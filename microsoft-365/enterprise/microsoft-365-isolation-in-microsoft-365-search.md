---
title: Isolation dzierżawy w Microsoft 365 wyszukiwania
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: W tym artykule wyjaśnij, jak działa izolacji dzierżawy w celu oddzielenia danych dzierżawy w Microsoft 365 wyszukiwania.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3416afdeceaa7000b516ec89b4a2a1e59d8708d0
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959260"
---
# <a name="tenant-isolation-in-microsoft-365-search"></a>Isolation dzierżawy w Microsoft 365 wyszukiwania

SharePoint online korzysta z modelu wyciągów barwnych dzierżawy, który równoważy wydajność udostępnionych struktur danych z ochroną przed wyciekiem informacji między dzierżawami. W przypadku tego modelu zapobiegniemy możliwościom wyszukiwania:

- Zwracanie wyników zapytania zawierających dokumenty z innych dzierżaw
- Ujawnianie wystarczających informacji w wynikach zapytania, że uzdolnieny użytkownik może wywrzeć informacje o innych dzierżawach
- Wyświetlanie schematu lub ustawień z innej dzierżawy
- Mieszanie informacji dotyczących przetwarzania analiz między dzierżawami lub przechowywaniem wyników w niewłaściwej dzierżawie
- Używanie wpisów słownika z innej dzierżawy

Dla każdego typu danych dzierżawy używamy co najmniej jednej warstwy ochrony w kodzie, aby zapobiec przypadkowemu wyciekowi informacji. Najważniejsze dane mają większość warstw ochrony, aby zapewnić, że pojedyncza wada nie spowoduje rzeczywistego lub postrzeganego wycieku informacji.

## <a name="tenant-separation-for-the-search-index"></a>Wyciągi barwne dzierżawy dla indeksu wyszukiwania

Indeks wyszukiwania jest przechowywany na dysku na serwerach hostowanych składniki indeksu, a dzierżawy współużytają pliki indeksu. Dokumenty indeksowane dzierżawy są widoczne tylko dla zapytań dla tej dzierżawy. Trzy niezależne mechanizmy zapobiegające wyciekowi informacji:

- Filtrowanie identyfikatora dzierżawy
- Prefiksy okresów identyfikatorów dzierżawy
- Testy ACL

Wszystkie trzy mechanizmy w celu zwrócenia dokumentów do niewłaściwej dzierżawy przy pomocy funkcji wyszukiwania muszą się nie powieść.

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a>Filtrowanie identyfikatora dzierżawy i prefiksy okresów identyfikatorów dzierżawy

Wyszukiwanie ma prefiks przed każdym terminem indeksowany w indeksie pełnoektowym z identyfikatorem dzierżawy. Na przykład gdy termin "*foo*" jest indeksowany dla dzierżawy o identyfikatorze "*123*", wpis w indeksie pełnoektowym to "*123foo"*.

Każde zapytanie jest konwertowane tak, aby uwzględniało identyfikator dzierżawy w procesie nazywanym filtrowaniem identyfikatorów dzierżawy. Na przykład zapytanie "*foo*" jest konwertowane na "<*guid*>. *foo* AND *tenantID*:<*guid*>", gdzie <*guid*> reprezentuje dzierżawę wykonującą zapytanie. Konwersja tego zapytania występuje w każdym węźle indeksu i ani zapytanie, ani przetwarzanie zawartości nie może mieć na to wpływu. Ponieważ identyfikator dzierżawy jest dodawany do każdego zapytania, częstotliwość występowania terminu w innych dzierżawach nie można wywątać na przykład przez klasyfikację najlepszego dopasowania w jednej dzierżawie.

Prefiksy okresów identyfikatorów dzierżawy występują tylko w indeksie pełnoektowym. Pola wyszukiwania, takie jak "*title:foo*", przejdź do indeksu wyszukiwania wyszukanych bez prefiksu z identyfikatorem dzierżawy. Zamiast tego wyszukiwania po polu są poprzedzone nazwą pola. Na przykład zapytanie "tytuł *:foo*" jest konwertowane na "*fields.title:foo AND fields.tenantID*:<*guid*>". Ponieważ częstotliwość występowania terminu nie ma wpływu na klasyfikację trafień w wyszukiwanej indeksie wyszukiwania, nie ma potrzeby wyciągania dzierżawy przez prefiksy terminów. W przypadku wyszukiwania polu, takiego jak "*tytuł:foo*", wyciągi zawartości dzierżawy zależą od filtrowania identyfikatora dzierżawy przez konwersję zapytania.

## <a name="document-access-control-list-checks"></a>Testy listy kontroli dostępu do dokumentów

Wyszukiwanie umożliwia sterowanie dostępem do dokumentów za pomocą acl, które są zapisywane w indeksie wyszukiwania. Każdy element jest indeksowany za pomocą zestawu terminów w specjalnym polu ACL. Pole ACL zawiera jeden termin dla grupy lub użytkownika, który może wyświetlać dokument. Każde zapytanie jest rozszerzane o listę terminów kontroli dostępu (ACE, Access Control Entry), po jednym dla każdej grupy, do której należy uwierzytelniony użytkownik.

Na przykład zapytanie takie jak "<*guid*>. *foo AND tenantID*:<*guid*>" stanie się: "<*guid*>. *foo AND tenantID*:<*guidAND* >  (*docACL:*<*ace1OR*>  *docACL*:<*ace2OR*>  *docACL*:<*ace3*> *...*)"

Identyfikatory użytkowników i grup, a przez to identyfikatory ACES są unikatowe, zapewnia to dodatkowy poziom zabezpieczeń między dzierżawami w przypadku dokumentów, które są widoczne tylko dla niektórych użytkowników. Tak samo jest w przypadku specjalnego bazy danych "Wszyscy oprócz użytkowników zewnętrznych", który udziela dostępu zwykłym użytkownikom w dzierżawie. Jednak ponieważ sieci ACEs dla "Wszyscy" są takie same dla wszystkich dzierżaw, wyciągi dzierżawy dla dokumentów publicznych zależą od filtrowania identyfikatorów dzierżawy. Obsługiwane są również odrzucanie aces. Ulepszenie zapytania powoduje dodanie klauzuli, która usuwa dokument z wyniku, gdy istnieje dopasowanie z odmową ace.

W Exchange Online wyszukiwania indeks jest podzielony na identyfikator skrzynki pocztowej poszczególnych użytkowników zamiast identyfikatora dzierżawy (identyfikatora subskrypcji), jak w SharePoint Online. Mechanizm partycjonowania jest taki sam jak w SharePoint Online, ale nie ma filtrowania ACL.
