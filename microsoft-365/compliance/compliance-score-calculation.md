---
title: Obliczanie wskaźnika zgodności
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, w jaki sposób menedżer zgodności usługi Microsoft Purview oblicza spersonalizowany wynik na podstawie akcji podjętych w celu rozwiązania ryzyka i poprawy stanu zgodności.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 07a168bd32e73502380260db748fd145648c69ae
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971181"
---
# <a name="compliance-score-calculation"></a>Obliczanie wskaźnika zgodności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**W tym artykule:** Dowiedz się, jak Menedżer zgodności oblicza ocenę zgodności dla twojej organizacji. W tym artykule wyjaśniono, jak **interpretować wynik**, co obejmuje **ocena punktu odniesienia ochrony danych** , **ciągłe monitorowanie** oraz **jak różne typy akcji są zarządzane i oceniane**.

> [!IMPORTANT]
> Rekomendacje programu Compliance Manager nie powinny być interpretowane jako gwarancja zgodności. Do Ciebie należy ocena i weryfikowanie skuteczności kontroli klientów w danym środowisku regulacyjnym. Te usługi podlegają warunkom i postanowień [w Warunkach produktu](https://go.microsoft.com/fwlink/?linkid=2108910). Zobacz również [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zabezpieczeń i zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="how-to-read-your-compliance-score"></a>Jak odczytać wynik zgodności

Na pulpicie nawigacyjnym Programu Compliance Manager zostanie wyświetlony ogólny wynik zgodności. Ten wynik mierzy postęp w wykonywaniu zalecanych akcji poprawy w ramach kontrolek. Twój wynik może pomóc zrozumieć aktualną postawę zgodności. Może również pomóc w ustalaniu priorytetów akcji na podstawie ich potencjału w celu zmniejszenia ryzyka.

Wartość wyniku jest przypisywana na trzech poziomach:

1. **Ocena akcji poprawy**: każda akcja ma inny wpływ na wynik w zależności od potencjalnego ryzyka

2. **Wynik kontrolny**: ten wynik to suma punktów uzyskanych przez ukończenie akcji poprawy w ramach kontrolki. Ta suma jest stosowana w całości do ogólnego wyniku zgodności, gdy kontrolka spełnia oba następujące warunki:
    - **Stan implementacji** jest równy **zaimplementowanym** lub **alternatywnej implementacji** oraz
    - **Wynik testu** jest równy **wynikowi zakończonej** pomyślnie.

3. **Ocena**: ten wynik jest sumą wyników kontroli. Jest ona obliczana przy użyciu wyników akcji. Każda akcja firmy Microsoft i każda akcja poprawy zarządzana przez organizację są liczone raz, niezależnie od tego, jak często są przywoływane w kontrolce.

Ogólny wynik zgodności jest obliczany przy użyciu wyników akcji, gdzie każda akcja firmy Microsoft jest liczona raz, każda zarządzana akcja techniczna jest liczona raz, a każda akcja nietechnii, którą zarządzasz, jest liczona raz na grupę. Ta logika ma na celu zapewnienie najdokładniejszej analizy sposobu implementowania i testowania akcji w organizacji. Można zauważyć, że może to spowodować, że ogólny wynik zgodności będzie się różnić od średniej wyników oceny. Przeczytaj więcej poniżej na temat [sposobu oceniania akcji](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Wynik początkowy na podstawie punktu odniesienia ochrony danych Microsoft 365
  
Menedżer zgodności zapewnia wstępny wynik na podstawie punktu odniesienia Microsoft 365 ochrony danych. Ten punkt odniesienia to zestaw mechanizmów kontroli, które obejmują kluczowe przepisy i standardy dotyczące ochrony danych i ogólnego ładu danych. Ten punkt odniesienia czerpie przede wszystkim z NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) i ISO (Międzynarodowa Organizacja Standaryzacji), a także z FedRAMP (Federal Risk and Authorization Management Program) i RODO (ogólne rozporządzenie o ochronie danych Unii Europejskiej).

Początkowy wynik jest obliczany zgodnie z domyślną oceną punktu odniesienia ochrony danych udostępnioną wszystkim organizacjom. Podczas pierwszej wizyty Menedżer zgodności już zbiera sygnały z Microsoft 365 rozwiązań. Na pierwszy rzut oka zobaczysz, jak twoja organizacja działa w stosunku do kluczowych standardów i przepisów dotyczących ochrony danych, a także zobaczysz sugerowane działania ulepszeń do podjęcia.

Ponieważ każda organizacja ma określone potrzeby, menedżer zgodności polega na skonfigurowaniu ocen i zarządzaniu nimi, aby pomóc zminimalizować i ograniczyć ryzyko tak kompleksowo, jak to możliwe.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Jak Menedżer zgodności stale ocenia mechanizmy kontroli

Menedżer zgodności automatycznie identyfikuje ustawienia w środowisku Microsoft 365, które pomagają określić, kiedy niektóre konfiguracje spełniają wymagania implementacji akcji poprawy. Menedżer zgodności wykrywa sygnały z innych rozwiązań zgodności, które mogły zostać wdrożone, w tym zarządzania cyklem życia danych, ochrony informacji, zgodności z komunikacją i zarządzania ryzykiem wewnętrznym, a także wykorzystuje monitorowanie wskaźnika bezpieczeństwa firmy Microsoft w ramach uzupełniających akcji poprawy.

Stan akcji zostanie zaktualizowany na pulpicie nawigacyjnym w ciągu 24 godzin od zmiany. Po wykonaniu zalecenia w celu zaimplementowania kontrolki stan kontrolki będzie zwykle aktualizowany następnego dnia.

Jeśli na przykład włączysz uwierzytelnianie wieloskładnikowe (MFA) w portalu usługi Azure AD, menedżer zgodności wykryje to ustawienie i odzwierciedli je w szczegółach rozwiązania dostępu do kontroli. Z drugiej strony, jeśli nie włączono uwierzytelniania wieloskładnikowego, menedżer zgodności sygnalizuje to jako zalecaną akcję.

Dowiedz się więcej na temat [wskaźnika bezpieczeństwa i jego działania](../security/defender/microsoft-secure-score.md).
  
## <a name="action-types-and-points"></a>Typy i punkty akcji

Menedżer zgodności śledzi dwa typy akcji:

1. **Twoje akcje poprawy**: akcje zarządzane przez organizację.
2. **Akcje firmy Microsoft**: akcje zarządzane przez firmę Microsoft.

Oba typy akcji mają punkty, które są wliczane do ogólnego wyniku po zakończeniu.

### <a name="technical-and-non-technical-actions"></a>Działania techniczne i nietechnalne

Akcje są grupowane według tego, czy mają charakter techniczny, czy nietechnacyjny. Wpływ oceniania każdej akcji różni się w zależności od typu.

- **Akcje techniczne** są implementowane przez interakcję z technologią rozwiązania (na przykład zmianę konfiguracji). Punkty dla akcji technicznych są przyznawane raz na akcję, niezależnie od liczby grup, do których należy.

- **Akcje inne niż techniczne** są zarządzane przez organizację i implementowane w sposób inny niż praca z technologią rozwiązania. Istnieją dwa typy akcji nietechnacyjnych: **dokumentacja** i **operacje**. Punkty dla tych akcji są stosowane do oceny zgodności na poziomie grupy. Oznacza to, że jeśli akcja istnieje w wielu grupach, za każdym razem, gdy zaimplementujesz ją w grupie, otrzymasz wartość punktu akcji.

**Przykład akcji technicznych i nietechnacyjnych:**

Załóżmy, że masz akcję techniczną o wartości 3 punktów, która istnieje w 5 grupach i masz akcję nietechnii o wartości 3 punktów, która istnieje w tych samych 5 grupach.

Jeśli pomyślnie zaimplementujesz akcję techniczną, łączna liczba odebranych punktów wynosi 3. Dzieje się tak, ponieważ należy zaimplementować akcję tylko raz dla dzierżawy. Stan implementacji i testu dla akcji technicznej będzie taki sam we wszystkich wystąpieniach tej akcji, w każdej grupie, do której należy.

Jeśli pomyślnie zaimplementujesz akcję nietechnii w każdej z 5 grup, łączna liczba punktów, które otrzymasz, wynosi 15. Jest to spowodowane koniecznością zaimplementowania akcji w każdej grupie. Stan implementacji i testu dla akcji nietechnii będzie się różnić w różnych grupach, ponieważ akcja jest implementowana oddzielnie w każdej z jej grup.

Ta logika oceniania ma na celu zapewnienie najdokładniejszej analizy sposobu implementowania i testowania akcji w organizacji.

### <a name="how-score-values-are-determined"></a>Jak są określane wartości oceny

Akcjom przypisuje się wartość oceny na podstawie tego, czy są one obowiązkowe, czy uznaniowe oraz czy są zapobiegawcze, detektywistyczne czy naprawcze.

### <a name="mandatory-and-discretionary-actions"></a>Działania obowiązkowe i uznaniowe

- Nie można pominąć **obowiązkowych akcji**— celowo lub przypadkowo. Przykładem obowiązkowej akcji są centralnie zarządzane zasady haseł, które określają wymagania dotyczące długości hasła, złożoności i wygaśnięcia. Użytkownicy muszą spełniać te wymagania, aby uzyskać dostęp do systemu.
  
- **Akcje uznaniowe** polegają na użytkownikach, aby zrozumieć zasady i stosować się do nich. Na przykład zasady wymagające od użytkowników zablokowania komputera po jego opuszczeniu są akcją uznaniową, ponieważ są zależne od użytkownika.
  
### <a name="preventative-detective-and-corrective-actions"></a>Działania zapobiegawcze, detektywistyczne i naprawcze
  
- **Akcje zapobiegawcze** dotyczą określonych zagrożeń. Na przykład ochrona informacji magazynowanych przy użyciu szyfrowania jest działaniem zapobiegawczym w przypadku ataków i naruszeń. Rozdzielenie obowiązków jest działaniem zapobiegawczym w celu zarządzania konfliktem interesów i ochrony przed oszustwami.
  
- **Działania detektywistyczne** aktywnie monitorują systemy w celu identyfikowania nieregularnych warunków lub zachowań, które reprezentują ryzyko, lub które mogą służyć do wykrywania włamań lub naruszeń. Przykłady obejmują inspekcję dostępu do systemu i uprzywilejowane akcje administracyjne. Inspekcje zgodności z przepisami są rodzajem akcji detektywistycznej używanej do znajdowania problemów z procesami.
  
- **Działania naprawcze** starają się ograniczyć do minimum niekorzystne skutki zdarzenia zabezpieczeń, podjąć działania naprawcze w celu zmniejszenia natychmiastowego efektu i cofnąć szkody, jeśli to możliwe. Reagowanie na zdarzenia związane z prywatnością jest działaniem naprawczym mającym na celu ograniczenie uszkodzeń i przywrócenie systemów do stanu operacyjnego po naruszeniu.
  
Każda akcja ma przypisaną wartość w Menedżerze zgodności na podstawie ryzyka, które reprezentuje:

|**Type**|**Przypisany wynik**|
|:-----|:-----|
| Prewencyjne obowiązkowe | 27 |
| Profilaktyczne dyskrecjonalne | 9 |
| Detektyw obowiązkowy | 3 |
| Detektyw uznaniowy | 1 |
| Obowiązkowa korekta | 3 |
| Naprawczy dyskrecjonalny | 1 |
  
![Wartości punktu akcji programu Compliance Manager.](../media/compliance-score-action-scoring.png "Wartości punktu akcji programu Compliance Manager")
