---
title: Wyszukiwanie zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: Użyj narzędzia zbierania elektronicznych materiałów dowodowych przeszukiwania zawartości w programie Centrum zgodności platformy Microsoft 365, aby szybko znaleźć wiadomości e-mail w skrzynkach pocztowych programu Exchange, dokumentach w witrynach SharePoint i lokalizacjach OneDrive oraz w konwersacjach za pomocą wiadomości błyskawicznych w Skype dla firm.
ms.openlocfilehash: 21e07f09c21bbf0196b6ba113b82ec3030aada32
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028082"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Wyszukiwanie zawartości za pomocą narzędzia Wyszukiwanie zawartości

Za pomocą narzędzia Przeszukiwanie zawartości w aplikacji Centrum zgodności platformy Microsoft 365 możesz szybko znaleźć wiadomości e-mail w skrzynkach pocztowych programu Exchange, dokumentach w witrynach SharePoint i lokalizacjach usługi OneDrive oraz w konwersacjach za pomocą wiadomości błyskawicznych w Skype dla firm. Za pomocą narzędzia do wyszukiwania zawartości możesz wyszukiwać wiadomości e-mail, dokumenty i konwersacje za pomocą wiadomości błyskawicznych w narzędziach do współpracy, takich Microsoft Teams i Microsoft 365 Grupy.
  
## <a name="search-for-content"></a>Wyszukiwanie zawartości

Pierwszym krokiem jest rozpoczęcie korzystania z narzędzia Przeszukiwanie zawartości w celu wybrania lokalizacji zawartości w celu wyszukiwania i skonfigurowania zapytania słów kluczowych w celu wyszukania określonych elementów. Możesz też pozostawić zapytanie puste i zwrócić wszystkie elementy w lokalizacjach docelowych.
  
- [Tworzenie i uruchamianie](content-search.md) wyszukiwania zawartości

- [Tworzenie zapytań wyszukiwania i używanie warunków do](keyword-queries-and-search-conditions.md) zawężania wyszukiwania

- [Informacje o funkcjach](content-search-reference.md) dotyczące wyszukiwania zawartości

- [Konfigurowanie filtrowania uprawnień wyszukiwania,](permissions-filtering-for-content-search.md) aby menedżer zbierania elektronicznych materiałów dowodowych może przeszukiwać tylko podzbiór skrzynek pocztowych lub witryn w organizacji

- [Wyszukiwanie lokalnych użytkowników w skrzynkach](search-cloud-based-mailboxes-for-on-premises-users.md) pocztowych w chmurze w programie Microsoft 365

- [Wyświetlanie statystyk słów](view-keyword-statistics-for-content-search.md) kluczowych dotyczących wyników wyszukiwania, a następnie w razie potrzeby uściślij zapytanie

- [Wyszukaj dane innych firm](use-content-search-to-search-third-party-data-that-was-imported.md), które Twoja organizacja zaimportowała do Microsoft 365

- [Zachowywanie adresatów z pola UDW](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) w celu ich wyszukiwania

## <a name="perform-actions-on-content-you-find"></a>Wykonywanie akcji na odnajdej zawartości

Po uruchomieniu wyszukiwania i w razie potrzeby jego uściślieniu należy wykonać czynności, których wyniki zostaną zwrócone przez wyszukiwanie. Możesz wyeksportować i pobrać wyniki na komputer lokalny lub w przypadku ataku poczty e-mail na organizację, możesz usunąć wyniki wyszukiwania ze skrzynek pocztowych użytkowników.
  
- [Eksportowanie wyników wyszukiwania zawartości i](export-search-results.md) pobieranie ich na komputer lokalny

- [Wyszukiwanie i usuwanie wiadomości e-mail](search-for-and-delete-messages-in-your-organization.md), takich jak wiadomości z wirusami, niebezpieczne załączniki lub wiadomości wyłudzące informacje

- [Eksportowanie raportu](export-a-content-search-report.md) o wynikach przeszukiwania zawartości bez eksportowania rzeczywistych wyników

## <a name="learn-more-about-content-search"></a>Dowiedz się więcej o wyszukiwaniu zawartości

Przeszukiwanie zawartości jest łatwe w użyciu, ale jest także bardzo wydajnym narzędziem. W tle dzieje się wiele rzeczy. Im więcej będziesz wiedzieć o tym problemie i zrozumieć jego zachowanie oraz ograniczenia, tym lepiej będziesz go używać na potrzeby organizacji w zakresie wyszukiwania i badania. Dowiedz się więcej o:
  
- [Limity wyszukiwania](limits-for-content-search.md) zawartości, takie jak maksymalna liczba wyszukiwań, które można uruchomić jednocześnie, oraz maksymalna liczba lokalizacji zawartości, które można uwzględnić w jednym wyszukiwaniu

- [Szacowane i rzeczywiste wyniki](differences-between-estimated-and-actual-ediscovery-search-results.md) wyszukiwania oraz przyczyny różnic między nimi podczas eksportowania i pobierania wyników wyszukiwania

- [Elementy częściowo indeksowane w programach Exchange i SharePoint](partially-indexed-items-in-content-search.md) oraz dołączanie i wykluczanie ich podczas eksportowania i pobierania wyników wyszukiwania

- [Badanie elementów częściowo indeksowanych](investigating-partially-indexed-items-in-ediscovery.md) i określanie ich ekspozycji w organizacji

- [Duplikowanie w wynikach wyszukiwania,](de-duplication-in-ediscovery-search-results.md) które można włączyć podczas eksportowania wiadomości e-mail, które są wynikami wyszukiwania

## <a name="use-scripts-for-advanced-scenarios"></a>Używanie skryptów w zaawansowanych scenariuszach

Czasami trzeba wykonać bardziej zaawansowane, złożone i powtarzające się zadania przeszukiwania zawartości. W takich przypadkach łatwiej i szybciej jest używać poleceń w programie PowerShell centrum zabezpieczeń & zgodności. Aby ułatwić to zadanie, tworzona jest szereg skryptów programu PowerShell centrum zabezpieczeń &, które ułatwiają wykonywanie złożonych zadań związanych z wyszukiwaniem zawartości.

- [Wyszukiwanie określonych folderów skrzynki pocztowej](use-content-search-for-targeted-collections.md) i witryny (nazywanej kolekcją  *docelową* ), jeśli masz pewność, że elementy reagujące na dane sprawy znajdują się w tym folderze.

- [Wyszukiwanie listy użytkowników w OneDrive](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) i lokalizacji skrzynki pocztowej

- [Tworzenie, zgłaszanie i usuwanie wielu wyszukiwań](create-report-on-and-delete-multiple-content-searches.md) w celu szybkiego i wydajnego identyfikowania i poprawiania danych wyszukiwania

- [Sklonowanie wyszukiwania zawartości i](clone-a-content-search.md) szybkie porównywanie wyników różnych zapytań wyszukiwania słów kluczowych uruchamianych w tych samych lokalizacjach zawartości. można też użyć skryptu, aby zaoszczędzić czas, bez konieczności ponownego wprowadzania wielu lokalizacji zawartości podczas tworzenia nowego wyszukiwania.
