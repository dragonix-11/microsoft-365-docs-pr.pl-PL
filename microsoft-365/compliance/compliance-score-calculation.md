---
title: Obliczanie wyniku zgodności
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Zrozumienie sposobu, w jaki Menedżer zgodności firmy Microsoft oblicza spersonalizowany wynik na podstawie działań podejmowane w celu rozwiązania zagrożeń i poprawy oceny zgodności.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b3b250391d04a8bf7388c761bcb00fe7cf99a4a5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983425"
---
# <a name="compliance-score-calculation"></a>Obliczanie wyniku zgodności

**W tym artykule:** Dowiedz się, jak Menedżer zgodności oblicza wynik zgodności dla organizacji. W tym artykule wyjaśniono, jak **interpretować** wyniki, co obejmuje ocena planu bazowego **ochrony** danych, ciągłe **monitorowanie** oraz jak zarządzane i oceniane są różne typy **akcji**.

> [!IMPORTANT]
> Rekomendacje Menedżera zgodności nie należy interpretować jako gwarancji zgodności. Ocena i weryfikacja skuteczności kontroli klienta w środowisku wymogów prawnych należy do Użytkownika. Te usługi podlegają regulaminom i regulaminom usług [online](https://go.microsoft.com/fwlink/?linkid=2108910). Zobacz też [Microsoft 365 licencjonowania w zakresie zabezpieczeń i zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="how-to-read-your-compliance-score"></a>Jak odczytać wynik zgodności

Na pulpicie nawigacyjnym Menedżer zgodności jest wyświetlany ogólny wynik zgodności. Ten wynik jest miarą postępów w ukończeniu zalecanych działań udoskonalania w obrębie kontrolek. Twój wynik może ułatwić zrozumienie bieżącej sytuacji dotyczącej zgodności z przepisami. Może także ułatwić priorytetyzowanie akcji na podstawie ich potencjału w celu zmniejszenia ryzyka.

Wartość wyniku jest przypisywana na trzech poziomach:

1. **Wynik akcji udoskonalania**: każda akcja ma inny wpływ na wynik w zależności od potencjalnego ryzyka

2. **Wynik kontroli**: ten wynik jest sumą punktów zdobytych w wyniku wykonania akcji udoskonalania w kontrolce. Ta suma jest stosowana do ogólnego wyniku zgodności, gdy kontrolka spełnia oba następujące warunki:
    - **Stan implementacji** jest równy **zaimplementowaniu** lub **alternatywnej implementacji**, oraz
    - **Wynik testu równa** się **Passed**.

3. **Wynik oceny**: ten wynik jest sumą twoich wyników kontroli. Jest on obliczany na podstawie wyników akcji. Każde działanie firmy Microsoft i każde działanie udoskonalania zarządzane przez Twoją organizację jest liczone raz, niezależnie od tego, jak często do nich występuje w kontrolce.

Ogólna ocena zgodności jest obliczana na podstawie wyników akcji, gdzie każde działanie firmy Microsoft jest liczone raz, każde działanie techniczne, którym zarządzasz, jest liczone raz, a każda akcja nie technicalna, której zarządzasz, jest zliczane raz na grupę. Ta logika ma na celu zapewnienie najdokładniejszego księgowego sposobu implementowania i  testowania akcji w organizacji. Możesz zauważyć, że może to powodować różnice w ogólnym wyniku zgodności od średniej wyników oceniania. Dowiedz się więcej poniżej o [tym, jak są odczytywane akcje](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Początkowa ocena na podstawie Microsoft 365 danych podstawowych
  
Menedżer zgodności daje początkową ocenę na podstawie planu bazowego Microsoft 365 ochrony danych. Ten plan bazowy jest zestawem kontroli, który zawiera najważniejsze przepisy i standardy w zakresie ochrony danych i ogólnego zarządzania danymi. Ten plan bazowy rysuje elementy przede wszystkim z NIST CSF (National Institute of Standards and Technology Nacjonalizacja) i ISO (Międzynarodowa Organizacja Normalizacji), a także fedRAMP (Federal Risk and Authorization Management Program) i RODO (Ogólne Rozporządzenie o Ochronie Danych Unii Europejskiej).

Twój początkowy wynik jest obliczany zgodnie z domyślną oceną planu bazowego ochrony danych dostępną dla wszystkich organizacji. Podczas pierwszej wizyty Menedżer zgodności zbiera już sygnały z Twoich Microsoft 365 rozwiązania. Zobaczysz w skrócie, jak Twoja organizacja działa w odniesieniu do kluczowych standardów i przepisów dotyczących ochrony danych, oraz zobaczysz sugerowane działania ulepszeń do podjęcia.

Ponieważ każda organizacja ma określone potrzeby, Menedżer zgodności polega na tym, aby skonfigurować testy i zarządzać nimi w celu jak najbardziej kompleksowego zminimalizowania i minimalizowania ryzyka.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Sposób ciągłego oceniania kontroli przez Menedżera zgodności

Menedżer zgodności automatycznie skanuje dane w środowisku Microsoft 365 i wykrywa ustawienia systemu, stale i automatycznie aktualizując stan działań technicznych. Program Microsoft Secure Score jest aparatem źródłowym, który wykonuje monitorowanie.

Stan akcji jest aktualizowany na pulpicie nawigacyjnym co 24 godziny. Gdy będziesz postępować zgodnie z zaleceniem, aby zaimplementować kontrolkę, stan kontrolki będzie zazwyczaj aktualizowany następnego dnia.

Jeśli na przykład włączysz uwierzytelnianie wieloskładnikowe (MFA) w portalu usługi Azure AD, Menedżer zgodności wykryje to ustawienie i odzwierciedli je w szczegółach rozwiązania dostępu kontrolki. Jeśli nie włączyć uwierzytelniania wieloskładnikowego, Menedżer zgodności oznaczy flagą akcję zalecaną do podjęcia.

Dowiedz się więcej o [bezpiecznym wyniku i o tym, jak to działa](../security/defender/microsoft-secure-score.md).
  
## <a name="action-types-and-points"></a>Typy i punkty akcji

Menedżer zgodności śledzi dwa typy akcji:

1. **Działania ulepszeń**: akcje, które są zarządzane przez Twoją organizację.
2. **Akcje firmy Microsoft**: akcje, które zarządza firma Microsoft.

Oba typy akcji mają punkty, które liczą się w ogólnym wyniku po ukończeniu.

### <a name="technical-and-non-technical-actions"></a>Działania techniczne i inne niż techniczne

Akcje są grupowane według ich charakteru technicznego lub nie technicalowego. Skutki oceniania poszczególnych akcji różnią się w zależności od typu.

- **Działania techniczne** są wdrażane przez interakcję z technologią rozwiązania (na przykład przez zmianę konfiguracji). Punkty za akcje techniczne są udzielane raz na akcję, niezależnie od tego, do ilu grup należy.

- **Akcje nie technicalne** są zarządzane przez Twoją organizację i implementowane w sposób inny niż praca z technologią rozwiązania. Istnieją dwa typy działań nietechnowych: dokumentacja **i** **działania operacyjne**. Punkty za te akcje są stosowane do wyniku zgodności na poziomie grupy. Oznacza to, że jeśli akcja istnieje w wielu grupach, wartość punktowa akcji będzie odbierana za każdym razem, gdy zostanie zaimplementowana w grupie.

**Przykład, w jaki sposób są analizne działania techniczne i niezwiązywne z technicznego:**

Załóżmy, że masz akcja techniczną, o wartości 3 punktów, która istnieje w 5 grupach, i masz nie technicalną wartość 3 punkty, która istnieje w tych samych 5 grupach.

Jeśli pomyślnie wdrożysz działanie techniczne, łączna liczba obierania punktów wynosi 3. Jest tak, ponieważ wystarczy zaimplementować akcję tylko raz dla dzierżawy. Implementacja i stan testowania akcji technicznej będą wyświetlane tak samo we wszystkich wystąpieniach tej akcji, we wszystkich grupach, do których należy.

Jeśli pomyślnie wdrożysz działanie nie technicalne w każdej z 5 grup, łączna liczba obierania punktów wynosi 15. Jest to spowodowane tym, że należy zaimplementować akcję w każdej grupie. Implementacja i stan testowania akcji nietechnicznych będą się różnić w zależności od grupy, ponieważ akcja jest zaimplementowana oddzielnie w obrębie każdej z jej grup.

Ta logika wyników ma na celu zapewnienie najdokładniejszego księgowego sposobu implementowania i  testowania akcji w organizacji.

### <a name="how-score-values-are-determined"></a>Jak są określane wartości wyników
 
Akcji przypisywana jest wartość wyniku na podstawie tego, czy są one obowiązkowe, czy dyskrecjonalne, oraz od tego, czy mają one charakter zapobiegający, detekwacyjny czy zawłaszający.

### <a name="mandatory-and-discretionary-actions"></a>Działania obowiązkowe i dyskrecjonalne

 - **Czynności obowiązkowych** nie można pominąć celowo ani przypadkowo. Przykładem obowiązkowej akcji jest centralnie zarządzane zasady dotyczące haseł, które ustawiają wymagania dotyczące długości, złożoności i wygasania hasła. Użytkownicy muszą spełniać te wymagania, aby uzyskać dostęp do systemu.
  
 - **Działania dyskrecjonalne** polegają na tym, że użytkownicy rozumieją zasady i ich przestrzegają. Przykładem może być zasada wymagająca od użytkowników zablokowania komputera w przypadku opuszczenia jej przez użytkownika, ponieważ zależy ona od użytkownika.
  
### <a name="preventative-detective-and-corrective-actions"></a>Akcje zapobiegające, wykrywające i korygające
  
 - **Działania zapobiegające odniesieniu** do określonego ryzyka. Na przykład ochrona informacji w miejscu przy użyciu szyfrowania jest akcją zapobiegawczą atakom i naruszeniem bezpieczeństwa. Rozdzielenie obowiązków jest działaniem zapobiegającym zarządzaniu konfliktem zainteresowań i zabezpieczeniu się przed oszustwami.
  
 - **Akcje wykrywające** aktywnie monitorują systemy w celu identyfikowania nieregularnych warunków lub zachowań reprezentujących ryzyko albo takich, które mogą być używane do wykrywania łamania praw lub naruszeń. Przykłady obejmują inspekcję dostępu systemu i akcje administracyjne o uprzywilejowanych uprawnieniach. Inspekcje zgodności z przepisami to rodzaj akcji dekcyjnej służącej do wykrywania problemów z procesami.
  
- **Działania naprawcze próbują** ograniczyć do minimum negatywne skutki zdarzenia związanego z zabezpieczeniami, podjąć działania naprawcze w celu zmniejszenia efektu natychmiastowego i, jeśli to możliwe, odwrócić szkody. Reagowanie na incydenty dotyczące prywatności jest działaniem naprawczym w celu ograniczenia uszkodzeń i przywracania systemów do stanu operacyjnego w przypadku naruszenia.
  
Każda akcja ma przypisaną wartość w Menedżerze zgodności na podstawie ryzyka, które reprezentuje:

|**Type**|**Przydzielony wynik**|
|:-----|:-----|
| Obowiązkowa obowiązkowa | 27 |
| Zapobieganie dyskrecji | 9 |
| Detective mandatory | 3 |
| Wykryj dyskrecję | 1 |
| Poprawianie obowiązkowych | 3 |
| Właściwa dyskrecja | 1 |
  
![Wartości punktów akcji Menedżera zgodności.](../media/compliance-score-action-scoring.png "Wartości punktów akcji Menedżera zgodności")