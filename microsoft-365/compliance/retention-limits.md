---
title: Limity dotyczące zasad przechowywania i zasad etykiet przechowywania
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
description: Opis maksymalnej liczby zasad i elementów na zasady dotyczące zasad przechowywania i zasad etykiet przechowywania
ms.openlocfilehash: f7b445ab8fd0afe5fb893933c3475385e09bc84e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011943"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Limity dotyczące zasad przechowywania i zasad etykiet przechowywania

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

W przypadku [używania zasad przechowywania i zasad etykiet](retention.md#retention-policies-and-retention-labels) przechowywania w celu automatycznego przechowywania lub usuwania danych dla organizacji należy pamiętać o kilku maksymalnych liczbach.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Maksymalna liczba etykiet przechowywania na dzierżawcę

Obsługiwane jest maksymalnie 1000 etykiet przechowywania na dzierżawcę.

## <a name="maximum-number-of-policies-per-tenant"></a>Maksymalna liczba zasad na dzierżawcę

Jedna dzierżawa może mieć maksymalnie 10 000 zasad (dowolna konfiguracja). Ta maksymalna liczba obejmuje różne zasady przechowywania i inne zasady dotyczące zgodności, takie jak zasady ochrony przed przepisami, bariery informacyjne, zbierania elektronicznych materiałów dowodowych, blokady w związku z postępowaniem sądowym, In-Place blokady i etykiety wrażliwości. Jednak ta maksymalna liczba z wyłączeniem:

- Zasady dotyczące etykiet SharePoint i OneDrive usuwać, zamiast zachowywać lub zachowywać, a następnie usuwać. Wyjątkiem jest automatyczne stosowanie zasad etykiet dla załączników w chmurze, które są zawsze uwzględniane w maksymalnej wartości 10 000.
- Exchange przechowywania z [zarządzania rekordami wiadomości](/exchange/security-and-compliance/messaging-records-management/messaging-records-management).

W ramach tego limitu 10 000 zasad istnieją również pewne limity maksymalnej liczby zasad przechowywania dla każdego obciążenia pracą:

- Exchange (dowolna konfiguracja): 1800
    - Na skrzynkę pocztową: 25 to zalecane maksimum, zanim będzie miało to wpływ na wydajność. Obsługiwany limit wynosi 50.
- SharePoint lub OneDrive: (wszystkie automatycznie dołączone witryny): 13
- SharePoint lub OneDrive (określone lokalizacje uwzględnione lub wykluczone): 2600

> [!NOTE]
> Te maksymalne liczby dla Exchange i SharePoint nie są wyłącznie do przechowywania, ale są udostępniane za pomocą innych typów zasad hold, takich jak blokady zbierania elektronicznych materiałów dowodowych, blokady w związku z postępowaniem sądowym i In-Place blokady.

Mimo że zasady przechowywania Microsoft Teams i Yammer przechowują dane w celu przechowywania danych w celach przechowywania, maksymalna liczba zasad dotyczących Exchange Online wykluczania zasad przechowywania dla klientów Teams i Yammer.

## <a name="maximums-for-adaptive-policy-scopes"></a>Maksymalna liczba zakresów adaptacyjnych zasad

Nie ma ograniczenia liczby adaptacyjnych zakresów [](retention.md#adaptive-or-static-policy-scopes-for-retention) zasad, które można dodać do zasad przechowywania, ale istnieją pewne maksymalne limity dla zapytania definiującego poszczególne adaptacyjne zakresy:

- Długość ciągu dla wartości atrybutów lub właściwości: 200
- Liczba atrybutów lub właściwości bez grupy lub w grupie: 10
- Liczba grup: 10
- Liczba znaków w zapytaniu zaawansowanym: 10 000

Grupowanie atrybutów lub właściwości w grupie nie jest obsługiwane. Oznacza to, że maksymalna liczba właściwości lub atrybutów obsługiwanych w pojedynczym zakresie adaptacyjnym wynosi 100.

## <a name="maximum-number-of-items-per-policy"></a>Maksymalna liczba elementów według zasad

> [!IMPORTANT]
> Ma zastosowanie tylko wtedy, gdy używasz [statycznych zakresów zasad, a nie adaptacyjnych zakresów zasad](retention.md#adaptive-or-static-policy-scopes-for-retention).

W przypadku użycia zakresów statycznych i opcjonalnej konfiguracji w celu dołączyć lub wykluczyć określonych użytkowników, Microsoft 365 grup użytkowników lub konkretnych witryn, istnieją pewne ograniczenia, o których należy pamiętać dla poszczególnych zasad. 

Maksymalna liczba elementów na zasady dla przechowywania w zakresach statycznych:

- Exchange skrzynek pocztowych: 1000
- Microsoft 365 grup: 1000
- Teams wiadomości w kanale: 1000
- Teams czatów: 1000
- Yammer wiadomości społeczności: 1000
- Yammer wiadomości od użytkowników: 1000
- SharePoint witryn: 100
- OneDrive konta: 100

Skype dla firm musi być określony dla konkretnych użytkowników, a maksymalna liczba obsługiwana przez zasady wynosi 1000.

Ponieważ te ograniczenia są określone dla zasad, jeśli musisz korzystać z określonych dołączeń lub wykluczeń, które skutkować przełoczeniem tych liczb, możesz utworzyć dodatkowe zasady, które mają takie same ustawienia przechowywania. Zobacz następną sekcję, aby uzyskać [przykładowe scenariusze i rozwiązania](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) , które z tego powodu korzystają z wielu zasad przechowywania.

Jednak wiele zasad skutkować większymi obciążeniami administracyjnymi. Rozważ korzystanie z adaptacyjnych zakresów zamiast tworzenia i utrzymywania wielu zasad z uwzględnieniem i wykluczeń.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Przykłady stosowania wielu zasad w celu uniknięcia przekroczenia maksymalnej liczby

Poniższe przykłady mają zastosowania statyczne zakresów i zapewniają pewne rozwiązania projektowe, gdy nie można określić tylko lokalizacji zasad przechowywania i musi uwzględniać maksymalną liczbę elementów udokumentowanych w poprzedniej sekcji.

Exchange przykład:

- **Wymaganie:** W organizacji, która ma ponad 40 000 skrzynek pocztowych użytkowników, większość użytkowników musi przechowywać swoją pocztę e-mail przez 7 lat, ale podzbiór zidentyfikowanych użytkowników (425) musi być zachowany przez tylko 5 lat.

- **Rozwiązanie**: Utwórz jedną zasady przechowywania dla Exchange e-mail z 7-letni okresem przechowywania i wykluczaj podzbiór użytkowników. Następnie utwórz drugie zasady przechowywania dla Exchange e-mail z 5-letni okresem przechowywania i uwzględnij podzbiór użytkowników. 
    
    W obu przypadkach liczba uwzględniana i wykluczona jest poniżej maksymalnej liczby określonych skrzynek pocztowych dla jednej zasady, a podzbiór użytkowników musi być jawnie wykluczany z pierwszej zasady, ponieważ [](retention.md#the-principles-of-retention-or-what-takes-precedence) ma dłuższy okres przechowywania niż w przypadku innych zasad. Jeśli podzbiór użytkowników wymagał dłuższych zasad przechowywania, nie trzeba wykluczać ich z pierwszej zasady.
     
    Dzięki temu rozwiązaniu, jeśli każda nowa kwota dołączy do organizacji, jej skrzynka pocztowa jest automatycznie uwzględniana w pierwszej zasadach przez 7 lat i nie ma wpływu na obsługiwane maksymalne liczby. Jednak nowi użytkownicy, którzy wymagają 5-letniego okresu przechowywania, dodają do liczb dołączanie i wykluczanie, a ten limit zostanie osiągnięty na poziomie 1000.

SharePoint przykład:

- **Wymaganie:** Organizacja ma kilka tysięcy witryn SharePoint, ale tylko 2000 witryn wymaga okresu przechowywania 10 lat, a 8000 witryn wymaga 4 lat przechowywania.

- Rozwiązanie **: Utwórz** 20 zasad przechowywania dla programu SharePoint z 10-letni okresem przechowywania, który obejmuje 100 konkretnych witryn, i utwórz 80 zasad przechowywania dla programu SharePoint z 4-letni okresem przechowywania, który obejmuje 100 konkretnych witryn.
    
    Ponieważ nie musisz zachowywać wszystkich witryn SharePoint, musisz utworzyć zasady przechowywania, które określają konkretne witryny. Ponieważ zasady przechowywania nie obsługują więcej niż 100 określonych witryn, należy utworzyć wiele zasad dla dwóch okresów przechowywania. Te zasady przechowywania mają maksymalną liczbę uwzględnionych witryn, więc następna nowa witryna, która wymaga zachowania, wymaga nowych zasad przechowywania niezależnie od okresu przechowywania.

## <a name="maximum-number-of-items-for-disposition"></a>Maksymalna liczba elementów do rozsyłania

W przypadku [zawartości zawartości](disposition.md) należy pamiętać o pewnych ograniczeniach:

- 1 000 000 elementów oczekujących na rozsyłanie na etap dla każdej etykiety przechowywania

- Dowód usuwania przez maksymalnie siedem lat po zrzucie produktu z ograniczeniem do 1000 000 pozycji na etykietę przechowywania dla tego okresu. 
    
Jeśli jest konieczne potwierdzenie ich rozsyłania większe niż ten limit 1 000 000 elementów oznaczonych jako rekordy, skontaktuj się z pomocą [techniczną firmy Microsoft](../admin/get-help-support.md).
