---
title: Krok nr 1. Klasyfikowanie i analizowanie pierwszego incydentu
description: Jak sklasyfikować i rozpocząć analizę pierwszego incydentu w Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, adres e-mail, 365, microsoft, m365, reagowanie na zdarzenia, cyberatak
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: c58bc4eb30c819ae0cbc1654173e8d9dc4ecb7a7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664925"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Krok nr 1. Klasyfikowanie i analizowanie pierwszego incydentu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Ponieważ poświęcasz trochę czasu na ustanawianie, implementowanie i utrzymywanie środków bezpieczeństwa zgodnie ze standardami organizacji, możesz skonfigurować rozwiązania zabezpieczeń, aby ułatwić szybkie identyfikowanie zagrożeń i zagrożeń bezpieczeństwa. Microsoft 365 Defender umożliwia wykrywanie, klasyfikowanie i badanie zdarzeń za pomocą jednego okienka, w którym można znaleźć informacje potrzebne do podejmowania terminowych decyzji.

Po wykryciu zdarzenia zabezpieczeń Microsoft 365 Defender przedstawia szczegóły, które należy sklasyfikować lub ustalić priorytety zdarzenia lub zdarzeń w stosunku do innych. Po określeniu priorytetyzacji analitycy mogą skupić swoją energię na badaniu przypisanych im przypadków.

## <a name="detection-by-microsoft-365-defender"></a>Wykrywanie według Microsoft 365 Defender

Microsoft 365 Defender odbiera alerty i zdarzenia z wielu platform zabezpieczeń firmy Microsoft jako źródła wykrywania w celu utworzenia całościowego obrazu i kontekstu złośliwych działań. Możliwe źródła wykrywania to:

- [Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md) jest rozwiązaniem wykrywanie i reagowanie w punktach końcowych (EDR), które korzysta z programu antywirusowego Microsoft Defender i zaawansowanej ochrony przed zagrożeniami z obsługą chmury przy użyciu usługi Microsoft Security Graph. Defender for Endpoint to ujednolicona platforma do ochrony zapobiegawczej, wykrywania po naruszeniu zabezpieczeń, zautomatyzowanego badania i reagowania. Chroni punkty końcowe przed zagrożeniami cybernetycznymi, wykrywa zaawansowane ataki i naruszenia danych, automatyzuje zdarzenia bezpieczeństwa i poprawia stan bezpieczeństwa.
- [Microsoft Defender for Identity](/defender-for-identity/what-is) to oparte na chmurze rozwiązanie zabezpieczeń, które używa sygnałów usług lokalna usługa Active Directory Domain Services (AD DS) do identyfikowania, wykrywania i badania zaawansowanych zagrożeń, tożsamości z naruszeniem zabezpieczeń i złośliwych akcji wewnętrznych skierowanych do organizacji.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) pełni rolę strażnika dostępu brokera w czasie rzeczywistym między użytkownikami przedsiębiorstwa i używanymi przez nich zasobami w chmurze, niezależnie od tego, z którego urządzenia korzystają.
- [Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/overview.md) chroni organizację przed złośliwymi zagrożeniami w wiadomościach e-mail, linkach (adresach URL) i narzędziach do współpracy.
- [Azure Security Center](/azure/security-center/security-center-introduction) to ujednolicony system zarządzania zabezpieczeniami infrastruktury, który wzmacnia stan zabezpieczeń centrów danych i zapewnia zaawansowaną ochronę przed zagrożeniami w obciążeniach hybrydowych w chmurze i lokalnie.


W Microsoft 365 Defender [zdarzenia](incidents-overview.md) są identyfikowane przez skorelowanie alertów z tych różnych źródeł wykrywania. Zamiast wydawać zasoby na ciągi lub rozróżniać wiele alertów w odpowiednich zdarzeniach, możesz od razu rozpocząć kolejkę zdarzeń w Microsoft 365 Defender. Takie podejście umożliwia wydajne klasyfikowanie zdarzeń w punktach końcowych, tożsamościach, wiadomościach e-mail i aplikacjach oraz zmniejszanie szkód spowodowanych atakiem.

## <a name="triage-your-incidents"></a>Klasyfikowanie zdarzeń

Reagowanie na zdarzenia w Microsoft 365 Defender rozpoczyna się po sklasyfikowaniu listy zdarzeń przy użyciu zalecanej metody priorytetyzacji organizacji. Klasyfikacja oznacza przypisanie do incydentów poziomu ważności lub pilności, który następnie określa kolejność, w jakiej będą one badane.

Przydatny przykładowy przewodnik określający, które zdarzenie ma być priorytetem w Microsoft 365 Defender, można podsumować za pomocą formuły: *Ważność i wpływ = Priorytet*.

- **Ważność** to poziom wyznaczony przez Microsoft 365 Defender i jej zintegrowane składniki zabezpieczeń.
- **Wpływ** jest określany przez organizację i zwykle obejmuje, ale nie tylko, próg liczby użytkowników, urządzeń, usług, których dotyczy problem (lub ich kombinacji), a nawet typ alertu.

Następnie analitycy inicjują badania na podstawie kryteriów **priorytetu** określonych przez organizację.

Priorytetyzacja incydentów może się różnić w zależności od organizacji. NIST zaleca również rozważenie funkcjonalnego i informacyjnego wpływu zdarzenia oraz możliwości odzyskiwania.

Poniżej opisano jedno podejście do klasyfikacji:

1. Przejdź do strony [zdarzeń](incidents-overview.md) , aby zainicjować klasyfikację. W tym miejscu można wyświetlić listę zdarzeń mających wpływ na organizację. Domyślnie są one rozmieszczone od ostatniego do najstarszego incydentu. W tym miejscu można również zobaczyć różne kolumny dla każdego zdarzenia pokazujące ich ważność, kategorię, liczbę aktywnych alertów i jednostki, których dotyczy problem, między innymi. Możesz dostosować zestaw kolumn i posortować kolejkę zdarzeń według niektórych z tych kolumn, wybierając nazwę kolumny. Możesz również filtrować kolejkę zdarzeń zgodnie z potrzebami. Aby uzyskać pełną listę dostępnych filtrów, zobacz [Określanie priorytetów zdarzeń](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Zdarzenia w portalu zabezpieczeń Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    Jednym z przykładów wykonywania klasyfikacji dla tego zestawu zdarzeń jest określenie priorytetów zdarzeń, które dotknęły więcej użytkowników i urządzeń. W tym przykładzie można określić priorytet zdarzenia o identyfikatorze 6769, ponieważ miało to wpływ na największą liczbę jednostek: siedem urządzeń, sześciu użytkowników i dwie skrzynki pocztowe. Ponadto zdarzenie wydaje się zawierać alerty z Microsoft Defender for Identity, które wskazują alert oparty na tożsamości i możliwą kradzież poświadczeń.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Strona Zdarzenia** przedstawiająca przykład zdarzenia o dużym wpływie w portalu zabezpieczeń Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. Wybierz okrąg obok nazwy zdarzenia, aby przejrzeć szczegóły. Po prawej stronie zostanie wyświetlone okienko boczne zawierające dodatkowe informacje, które mogą pomóc w dalszej klasyfikacji.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Strona Zdarzenia przedstawiająca przykład okienka po stronie zdarzenia w portalu zabezpieczeń Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   Na przykład, sprawdzając, które metody [MITRE ATT&](https://attack.mitre.org/) taktykę CK używaną przez osobę atakującą na podstawie kategorii incydentu, możesz określić priorytet tego incydentu, ponieważ osoba atakująca użyła skradzionych poświadczeń, ustanowiła polecenie i kontrolę, wykonała ruch boczny i eksfiltrował niektóre dane. Te akcje sugerują, że osoba atakująca trafiła już głęboko do sieci i prawdopodobnie ukradła poufne informacje.

   Ponadto jeśli organizacja zaimplementowała strukturę Zero Trust, należy rozważyć dostęp do poświadczeń jako ważne naruszenie zabezpieczeń, które warto nadać priorytet.

   Przewijając w dół okienko boczne, zobaczysz konkretne jednostki, na które ma to wpływ, takie jak użytkownicy, urządzenia i skrzynki pocztowe. Możesz sprawdzić poziom narażenia każdego urządzenia i właścicieli skrzynek pocztowych, których dotyczy problem.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Szczegóły okienka po stronie zdarzenia" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. W dalszej części okienka bocznego można znaleźć skojarzone alerty. Microsoft 365 Defender wykonał już korelację tych alertów w jednym zdarzeniu, oszczędzając czas i zasoby lepiej poświęcone na korygowanie ataku. Alerty są podejrzane i w związku z tym mogą być złośliwymi zdarzeniami systemowymi, które sugerują obecność osoby atakującej w sieci.

   W tym przykładzie określono, że 87 pojedynczych alertów jest częścią jednego zdarzenia zabezpieczeń. Możesz wyświetlić wszystkie alerty, aby uzyskać szybki wgląd w to, jak atak się rozegrał.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Alerty w okienku po stronie zdarzenia w portalu zabezpieczeń Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>Analizowanie pierwszego incydentu

Zrozumienie kontekstu otaczającego alerty jest równie ważne. Często alert nie jest pojedynczym niezależnym zdarzeniem. Istnieje łańcuch utworzonych procesów, poleceń i akcji, które mogły nie wystąpić w tym samym czasie. W związku z tym analityk musi wyszukać pierwsze i ostatnie działania podejrzanej jednostki na osiach czasu urządzenia, aby zrozumieć kontekst alertów.

Istnieje wiele sposobów odczytywania i analizowania danych przy użyciu Microsoft 365 Defender ale celem końcowym analityków jest jak najszybsze reagowanie na zdarzenia. Chociaż Microsoft 365 Defender może znacznie [skrócić średni czas korygowania (MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) dzięki wiodącej w branży funkcji [zautomatyzowanego badania i reagowania](m365d-autoir.md), zawsze istnieją przypadki, które wymagają ręcznej analizy.

Oto przykład:

1. Po określeniu priorytetu klasyfikacji analityk rozpoczyna szczegółową analizę, wybierając nazwę zdarzenia. Ta strona zawiera **podsumowanie zdarzeń** , w którym dane są wyświetlane na kartach, aby ułatwić analizę. Na **karcie Alerty** są wyświetlane typy alertów. Analitycy mogą kliknąć każdy alert, aby przejść do szczegółów odpowiedniego źródła wykrywania.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Karta Podsumowanie zdarzenia" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    Aby uzyskać szybki przewodnik dotyczący domeny, którą obejmuje każde źródło wykrywania, zapoznaj się z sekcją [Wykryj](#detection-by-microsoft-365-defender) w tym artykule.

2. Na **karcie Alerty** możesz przełączyć się do źródła wykrywania, aby przeprowadzić bardziej szczegółowe badanie i analizę. Na przykład wybranie opcji Wykrywanie złośliwego oprogramowania z Microsoft Defender for Cloud Apps jako źródła wykrywania powoduje przejście analityka do odpowiedniej strony alertu.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Strona Zdarzenia przedstawiająca przykład wybierania alertu o zdarzeniu." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Odpowiednia strona w Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. Aby dokładniej zbadać nasz przykład, przewiń do dołu strony, aby wyświetlić **użytkowników, których dotyczy problem**. Aby wyświetlić działanie i kontekst wykrywania złośliwego oprogramowania, wybierz stronę użytkownika Annette Hill.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Strona użytkownika" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. Na stronie użytkownika są wyświetlane zdarzenia chronologicznie, począwszy od *ryzykownego logowania z alertu adresu IP sieci TOR* . Chociaż podejrzaność działania zależy od charakteru sposobu, w jaki organizacja prowadzi swoją działalność, w większości przypadków użycie routera onionowego (TOR), sieci, która umożliwia użytkownikom anonimowe przeglądanie Internetu, w środowisku przedsiębiorstwa może być uważane za bardzo mało prawdopodobne i niepotrzebne w przypadku regularnych operacji online.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Chronologiczna lista zdarzeń dla użytkownika" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. Każdy alert można wybrać, aby uzyskać więcej informacji na temat działania. Na przykład wybranie pozycji **Działanie z alertu adresu IP Tora** prowadzi do własnej strony tego alertu. Annette jest administratorem Office 365, co wskazuje na podwyższone uprawnienia i że zdarzenie źródłowe mogło doprowadzić do uzyskania dostępu do informacji poufnych.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Szczegóły alertów dla Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. Wybierając inne alerty, możesz uzyskać pełny obraz ataku.

## <a name="next-step"></a>Następny krok

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="Opcja Koryguj na stronie Reagowanie na pierwsze zdarzenie" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

Dowiedz się, jak [korygować zdarzenia](first-incident-remediate.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
