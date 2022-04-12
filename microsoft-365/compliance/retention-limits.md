---
title: Limity zasad przechowywania i zasad etykiet przechowywania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
hideEdit: true
description: Informacje o maksymalnej liczbie zasad i elementów na zasady dotyczące zasad przechowywania i zasad etykiet przechowywania
ms.openlocfilehash: 260b99a4519937f962cc1c779a9beb9c6810e7e1
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782814"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Limity zasad przechowywania i zasad etykiet przechowywania

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Jeśli używasz [zasad przechowywania i zasad etykiet przechowywania](retention.md#retention-policies-and-retention-labels) do automatycznego przechowywania lub usuwania danych dla organizacji, należy pamiętać o pewnych maksymalnych liczbach.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Maksymalna liczba etykiet przechowywania na dzierżawę

Maksymalnie 1000 etykiet przechowywania jest obsługiwanych dla każdej dzierżawy.

## <a name="maximum-number-of-policies-per-tenant"></a>Maksymalna liczba zasad na dzierżawę

Jedna dzierżawa może mieć maksymalnie 10 000 zasad (dowolna konfiguracja). Ta maksymalna liczba obejmuje różne zasady przechowywania i inne zasady zgodności, takie jak zasady DLP, bariery informacyjne, blokady zbierania elektronicznych materiałów dowodowych, blokady sporów sądowych, blokady In-Place i etykiety poufności. Jednak ta maksymalna wartość wyklucza:

- Zasady automatycznego etykietowania dla SharePoint i OneDrive, chyba że są przeznaczone dla załączników w chmurze.
- Opublikowane zasady etykiet dla SharePoint i OneDrive, które są tylko do usuwania, a nie tylko do zachowania, lub zachowują, a następnie usuwają.
- Exchange zasady przechowywania z [zarządzania rekordami obsługi komunikatów (MRM).](/exchange/security-and-compliance/messaging-records-management/messaging-records-management)

W ramach tego limitu 10 000 zasad istnieją również pewne limity maksymalnej liczby zasad przechowywania na obciążenie:

- Exchange (dowolna konfiguracja): 1800
  - Na skrzynkę pocztową: 25 jest zalecaną wartością maksymalną, zanim będzie to miało wpływ na wydajność; 50 to obsługiwany limit.
- SharePoint lub OneDrive: (wszystkie witryny są automatycznie dołączone): 13
- SharePoint lub OneDrive (określone lokalizacje uwzględnione lub wykluczone): 2600

> [!NOTE]
> Te maksymalne liczby dla Exchange i SharePoint nie są wyłączne dla przechowywania, ale są współużytkowane z innymi typami zasad blokady, które obejmują blokady zbierania elektronicznych materiałów dowodowych, blokady sporów sądowych i blokady In-Place.

Mimo że zasady przechowywania dla Microsoft Teams i Yammer używają skrzynek pocztowych do przechowywania danych do celów przechowywania, maksymalna liczba zasad dla Exchange Online wyklucza zasady przechowywania dla Teams i Yammer.

## <a name="maximums-for-adaptive-policy-scopes"></a>Maksymalne wartości dla zakresów zasad adaptacyjnych

Nie ma limitu liczby [zakresów zasad adaptacyjnych](retention.md#adaptive-or-static-policy-scopes-for-retention) , które można dodać do zasad przechowywania, ale istnieją pewne maksymalne limity zapytania definiujące każdy zakres adaptacyjny:

- Długość ciągu dla wartości atrybutu lub właściwości: 200
- Liczba atrybutów lub właściwości bez grupy lub w grupie: 10
- Liczba grup: 10
- Liczba znaków w zapytaniu zaawansowanym: 10 000

Grupowanie atrybutów lub właściwości w grupie nie jest obsługiwane. Oznacza to, że maksymalna liczba właściwości lub atrybutów obsługiwanych w jednym zakresie adaptacyjnym wynosi 100.

## <a name="maximum-number-of-items-per-policy"></a>Maksymalna liczba elementów na zasady

> [!IMPORTANT]
> Dotyczy tylko wtedy, gdy używasz [zakresów zasad statycznych, a nie zakresów zasad adaptacyjnych](retention.md#adaptive-or-static-policy-scopes-for-retention).

Jeśli używasz zakresów statycznych i opcjonalnej konfiguracji do uwzględniania lub wykluczania określonych użytkowników, określonych grup Microsoft 365 lub określonych lokacji, istnieją pewne limity dla poszczególnych zasad, o których należy pamiętać.

Maksymalna liczba elementów na zasady przechowywania zakresów statycznych:

- Exchange skrzynki pocztowe: 1000
- Grupy Microsoft 365: 1000
- Teams komunikatów kanału: 1000
- Teams czaty: 1000
- Yammer komunikaty społeczności: 1000
- Yammer komunikaty użytkowników: 1000
- witryny SharePoint: 100
- konta OneDrive: 100

Skype dla firm musi być ograniczony do określonych użytkowników, a maksymalna liczba obsługiwanych zasad wynosi 1000.

Ponieważ te ograniczenia dotyczą zasad, jeśli musisz użyć określonych wkluczeń lub wykluczeń, które powodują przekroczenie tych liczb, możesz utworzyć dodatkowe zasady, które mają te same ustawienia przechowywania. Zapoznaj się z następną sekcją, aby zapoznać się z [przykładowymi scenariuszami i rozwiązaniami](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) , które z tego powodu korzystają z wielu zasad przechowywania.

Jednak wiele zasad powoduje wyższe koszty administracyjne. Rozważ użycie zakresów adaptacyjnych zamiast tworzenia i utrzymywania wielu zasad z uwzględnieniem i wykluczeniami.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Przykłady użycia wielu zasad w celu uniknięcia przekroczenia maksymalnej liczby

Poniższe przykłady dotyczą zakresów statycznych i zapewniają pewne rozwiązania projektowe, gdy nie można określić tylko lokalizacji dla zasad przechowywania i muszą uwzględniać maksymalną liczbę elementów udokumentowanych w poprzedniej sekcji.

Exchange przykład:

- **Wymaganie**: W organizacji, która ma ponad 40 000 skrzynek pocztowych użytkowników, większość użytkowników musi przechowywać pocztę e-mail przez 7 lat, ale podzestaw zidentyfikowanych użytkowników (425) musi przechowywać pocztę e-mail tylko przez 5 lat.

- **Rozwiązanie**: utwórz jedną zasadę przechowywania dla Exchange poczty e-mail z okresem przechowywania wynoszącym 7 lat i wykluczaj podzestaw użytkowników. Następnie utwórz drugie zasady przechowywania dla Exchange wiadomości e-mail z okresem przechowywania wynoszącym 5 lat i uwzględnij podzestaw użytkowników.

    W obu przypadkach liczba uwzględniona i wykluczona jest poniżej maksymalnej liczby określonych skrzynek pocztowych dla jednej zasady, a podzbiór użytkowników musi zostać jawnie wykluczony z pierwszych zasad, ponieważ ma [dłuższy okres przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) niż drugie zasady. Jeśli podzbiór użytkowników wymagał dłuższych zasad przechowywania, nie trzeba wykluczać ich z pierwszych zasad.

    Dzięki temu rozwiązaniu, jeśli ktoś nowy dołączy do organizacji, ich skrzynka pocztowa zostanie automatycznie uwzględniona w pierwszych zasadach od 7 lat i nie będzie mieć wpływu na maksymalną liczbę obsługiwanych numerów. Jednak nowi użytkownicy, którzy wymagają 5-letniego okresu przechowywania, dodają numery dołączania i wykluczania, a ten limit zostanie osiągnięty na poziomie 1000.

SharePoint przykład:

- **Wymaganie**: Organizacja ma kilka tysięcy witryn SharePoint, ale tylko 2000 witryn wymaga okresu przechowywania wynoszącego 10 lat, a 8000 witryn wymaga okresu przechowywania wynoszącego 4 lata.

- **Rozwiązanie**: Utwórz 20 zasad przechowywania dla SharePoint z okresem przechowywania wynoszącym 10 lat, który obejmuje 100 określonych lokacji, i utwórz 80 zasad przechowywania dla SharePoint z okresem przechowywania wynoszącym 4 lata, który obejmuje 100 określonych lokacji.

    Ponieważ nie musisz zachowywać wszystkich SharePoint witryn, musisz utworzyć zasady przechowywania określające określone lokacje. Ponieważ zasady przechowywania nie obsługują więcej niż 100 określonych lokacji, należy utworzyć wiele zasad dla dwóch okresów przechowywania. Te zasady przechowywania mają maksymalną liczbę uwzględnionych lokacji, więc następna nowa lokacja, która wymaga zachowania, wymagałaby nowych zasad przechowywania, niezależnie od okresu przechowywania.

## <a name="maximum-number-of-items-for-disposition"></a>Maksymalna liczba elementów do dyspozycji

W przypadku [rozporządzania zawartością](disposition.md) należy pamiętać o pewnych limitach:

- Maksymalna liczba na dzierżawę:
  - 16 000 000 elementów w jednym z następujących stanów przeglądu dyspozycji: oczekujące na dyspozycję lub zatwierdzone dyspozycje
  - 16 000 000 elementów oznaczonych jako rekordy automatycznie usuwane (bez przeglądu dyspozycji)

- Maksymalna liczba dla każdej etykiety przechowywania:
  - 1 000 000 elementów oczekujących na dyspozycję na etap dla każdej etykiety przechowywania
  - Dowód dyspozycji przez okres do siedmiu lat od usunięcia przedmiotu z limitem 1 000 000 elementów na etykietę przechowywania dla tego okresu.

    Jeśli potrzebujesz dowodu dyspozycji wyższego niż ten limit wynoszący 1 000 000 elementów oznaczonych jako rekordy, skontaktuj się z [pomoc techniczna firmy Microsoft](../admin/get-help-support.md).
