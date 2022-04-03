---
title: Krok nr 1. Przeszukaj i analizuj swoje pierwsze zdarzenie
description: Jak sprawdzić i rozpocząć analizę pierwszego zdarzenia w programie Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki
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
ms.openlocfilehash: 299cb7847e19e625bbae3122e16c56bb54e05c89
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499028"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Krok nr 1. Przeszukaj i analizuj swoje pierwsze zdarzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

W miarę jak poświęcisz trochę czasu na ustanowienie, wdrożenie i utrzymywanie zabezpieczeń zgodnie ze standardami organizacji, możesz skonfigurować rozwiązania zabezpieczeń, aby ułatwić szybkie identyfikowanie zagrożeń i zagrożeń bezpieczeństwa. Microsoft 365 Defender pozwala wykrywać, sprawdzać i badać zdarzenia za pomocą jednego okienka ze wszystkich okienek, w którym można znaleźć informacje potrzebne do podejmowania w terminie decyzji.

Po wykryciu zdarzenia zabezpieczeń użytkownik Microsoft 365 Defender szczegóły, które trzeba będzie poszedzonych ze zdarzeniami lub incydentami albo określić ich priorytetyzowanie nad innymi osobami. Po określeniu priorytetów analitycy mogą skoncentrować się na analizie przydzielonych im spraw.

## <a name="detection-by-microsoft-365-defender"></a>Wykrywanie za pomocą Microsoft 365 Defender

Microsoft 365 Defender odbiera alerty i zdarzenia z wielu platform zabezpieczeń firmy Microsoft jako źródła wykrywania w celu utworzenia obrazu i kontekstu złośliwych działań. Możliwe źródła wykrywania to:

- [Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md) to rozwiązanie wykrywanie i reagowanie w punktach końcowych (EDR), które korzysta z programu antywirusowego Microsoft Defender i zaawansowanej ochrony przed zagrożeniami w chmurze przy użyciu programu Microsoft Security Graph. Program Defender for Endpoint to ujednolicona platforma do zapobiegania wykrywaniu naruszenia, automatycznego badania i reagowania. Chroni ona punkty końcowe przed cyberatakami, wykrywa zaawansowane ataki i naruszenia danych, automatyzuje zdarzenia dotyczące zabezpieczeń i ulepsza zabezpieczenia.
- [Microsoft Defender for Identity](/defender-for-identity/what-is) to oparte na chmurze rozwiązanie zabezpieczeń, które używa sygnałów lokalna usługa Active Directory Domain Services (AD DS) do identyfikowania, wykrywania i badanie zaawansowanych zagrożeń, naruszonych tożsamości i złośliwych działań w ramach niejawnego programu testów skierowanych do organizacji.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) pełni rolę strażnika dostępu do usług brokera w czasie rzeczywistym między użytkownikami przedsiębiorstwa a zasobami w chmurze, z których korzystają, gdziekolwiek znajdują się Twoi użytkownicy i niezależnie od urządzenia, z którego korzystają.
- [Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/overview.md) chroni organizację przed złośliwymi zagrożeniami w wiadomościach e-mail, linkach (adresach URL) i narzędziach do współpracy.
- [Azure Security Center](/azure/security-center/security-center-introduction) to ujednolicony system zarządzania zabezpieczeniami infrastruktury, który jeszcze bardziej zwiększa bezpieczeństwo centrów danych i zapewnia zaawansowaną ochronę przed zagrożeniami we hybrydowych obciążeniach pracą w chmurze i lokalnie.


W Microsoft 365 Defender zdarzenia są identyfikowane [za](incidents-overview.md) pomocą skorelowania alertów z tych różnych źródeł wykrywania. Zamiast poświęcać zasoby związane ze sobą lub rozróżniać wiele alertów w poszczególnych zdarzeniach, możesz od razu zacząć od kolejki Microsoft 365 Defender zdarzenia. Ta metoda pozwala na wydajną ujedną pracę nad incydentami w punktach końcowych, tożsamościach, wiadomościach e-mail i aplikacjach, a także zmniejszanie szkód spowodowanych atakami.

## <a name="triage-your-incidents"></a>Ujednanie danych zdarzeń

Reagowanie na Microsoft 365 Defender rozpoczyna się po przechowanie listy zdarzeń przy użyciu zalecanej przez Twoją organizację metody priorytetyzowania. Określenie poziomu ważności lub pilności przypadku oznacza przypisanie do zdarzeń poziomu ważności lub pilności, a następnie określa kolejność, w jakiej będą one analizowane.

Użyteczny przykładowy przewodnik dotyczący określania zdarzenia, które ma być priorytetyzowane w programie Microsoft 365 Defender można podsumować za pomocą formuły: Ważność *+ Wpływ = Priorytet*.

- **Ważność** to poziom wyznaczony przez Microsoft 365 Defender i jego zintegrowane składniki zabezpieczeń.
- **Wpływ** jest ustalany przez organizację i ogólnie obejmuje próg liczby użytkowników, urządzeń, usług, których to dotyczy (lub ich połączenia), a nawet typów alertów, ale nie tylko.

Następnie analitycy inicjują badania na podstawie **kryteriów Priorytet** określonych przez organizację.

Priorytety zdarzeń mogą się różnić w zależności od organizacji. Funkcja NIST zaleca również uwzględnianie wpływu na funkcje i informacje zdarzenia oraz możliwość ich odzyskania.

Poniżej opisano jedno podejście do ujednania:

1. Przejdź do strony [zdarzeń, aby](incidents-overview.md) zainicjować proces wyszukiwania. Tutaj możesz zobaczyć listę zdarzeń mających wpływ na organizację. Domyślnie są one rozmieszczone od najnowszego do najstarszego zdarzenia. W tym miejscu możesz również wyświetlić różne kolumny dla każdego zdarzenia przedstawiające ich ważność, kategorię, liczbę aktywnych alertów i jednostki, na które ma wpływ, między innymi. Możesz dostosować zestaw kolumn i posortować kolejkę zdarzeń według niektórych z tych kolumn, wybierając nazwę kolumny. Można również filtrować kolejkę zdarzeń zgodnie z potrzebami. Aby uzyskać pełną listę dostępnych filtrów, zobacz [Określanie priorytetów zdarzeń](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Zdarzenia w portalu Microsoft 365 zabezpieczeń" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    Przykładem tego, jak można przeprowadzić triage dla tego zestawu zdarzeń, jest priorytetyzowanie zdarzeń, które dotyczyły większej liczby użytkowników i urządzeń. W tym przykładzie możesz określić priorytet identyfikatora zdarzenia 6769, ponieważ dotyczy on największej liczby jednostek: siedmiu urządzeń, sześciu użytkowników i dwóch skrzynek pocztowych. Ponadto wygląda na to, że zdarzenie zawiera alerty z Microsoft Defender for Identity, które wskazują alert oparty na tożsamości i możliwe kradzieże poświadczeń.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Strona Zdarzenia** przedstawiająca przykładowy wywłaszowy incydent w portalu zabezpieczeń Microsoft 365 sieci Web" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. Wybierz kółko obok nazwy zdarzenia, aby przejrzeć szczegóły. Po prawej stronie zostanie wyświetlone okienko boczne z dodatkowymi informacjami, które mogą pomóc w dalszej pracy z informacjami.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Strona Zdarzenia z przykładem okienka bocznego zdarzenia w Microsoft 365 zabezpieczeń" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   Można na przykład ustalić, która taktyka [atT&CK](https://attack.mitre.org/) została użyta przez atakującego na podstawie kategorii incydentu, można ustalić priorytety tego zdarzenia, ponieważ atakujący użyli skradzionych poświadczeń, ustalili polecenia i kontroli, wykonali ruchy boczne i przeszlili niektóre dane. Te działania sugerują, że atakujący poszli już w głąb sieci i potencjalnie ukradzili poufne informacje.

   Ponadto, jeśli Twoja organizacja wdrożyła platformę Zero Trust, należy rozważyć dostęp poświadczeń jako ważne naruszenie zabezpieczeń, na które warto zwrócić uwagę.

   Przewijając w dół okienko boczne, zobaczysz konkretne jednostki, na które wpływa ta wpływ, takie jak użytkownicy, urządzenia i skrzynki pocztowe. Możesz sprawdzić poziom ekspozycji na poszczególne urządzenia i właścicieli skrzynek pocztowych, których dotyczy problem.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Szczegóły okienka bocznego zdarzenia" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. W dalszej części okienka bocznego znajdują się skojarzone alerty. Microsoft 365 Defender już korelacji tych alertów w przypadku jednego zdarzenia, co pozwala zaoszczędzić czas i zasoby, które lepiej spędzone na rozwiązywaniu ataków. Alerty są podejrzane, a zatem mogą być złośliwymi zdarzeniami systemowym sugerującymi obecność atakującego w sieci.

   W tym przykładzie 87 pojedynczych alertów zostało określonych jako część jednego zdarzenia związanego z zabezpieczeniami. Możesz wyświetlić wszystkie alerty, aby szybko sprawdzić sposób odtwarzania ataków.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Alerty w okienku po stronie zdarzenia w Microsoft 365 zabezpieczeń" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>Analizowanie pierwszego zdarzenia

Równie ważna jest znajomość kontekstu otaczającego alerty. Często alert nie jest pojedynczym zdarzeniem niezależnym. Istnieje łańcuch procesów utworzonych, poleceń i akcji, które mogą nie wystąpić w tym samym czasie. Dlatego analityk musi poszukać pierwszego i ostatniego działania podejrzanej jednostki na osiach czasu urządzeń, aby zrozumieć kontekst alertów.

Istnieje wiele sposobów odczytywania i analizowania danych przy użyciu aplikacji Microsoft 365 Defender jednak celem analityków jest jak najszybciej reagowanie na incydenty. Chociaż Microsoft 365 Defender może znacznie skrócić średni czas rozwiązywania problemów [(MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) za pomocą wiodącej w branży funkcji [](m365d-autoir.md) automatycznego badania i reagowania, zawsze są przypadki wymagające analizy ręcznej.

Oto przykład:

1. Po  ustalić priorytetu triage analityk rozpoczyna szczegółową analizę, wybierając nazwę zdarzenia. Na tej stronie jest **wyświetlane podsumowanie zdarzeń** , na którym dane są wyświetlane na kartach w celu pomocy podczas analizy. Na karcie **Alerty** są wyświetlane typy alertów. Analitycy mogą klikać poszczególne alerty, aby przejść do szczegółów w odpowiednim źródle wykrywania.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Karta Podsumowanie zdarzenia" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    Aby uzyskać krótki przewodnik dotyczący domeny, którą obejmuje każde źródło wykrywania, zapoznaj się z sekcją [Wykrywanie](#detection-by-microsoft-365-defender) w tym artykule.

2. Z karty **Alerty** możesz przejść do źródła wykrywania, aby przeprowadzić bardziej szczegółową analizę i analizy. Na przykład wybranie opcji Wykrywanie złośliwego oprogramowania Microsoft Defender for Cloud Apps źródłem wykrywania przenosi analityka do odpowiedniej strony alertu.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Strona Zdarzenia z przykładem wybrania alertu o zdarzeniu." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Odpowiednia strona w Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. Aby dokładniej zbadać przykład, przewiń do dołu strony w celu wyświetlenia **danych użytkowników, których dotyczy problem**. Aby zobaczyć aktywność i kontekst związane z wykrywaniem złośliwego oprogramowania, wybierz stronę użytkownika An anety Hill.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Strona użytkownika" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. Na stronie użytkownika są wymieniane zdarzenia chronologicznie, zaczynając od ryzykownych logowania z alertu *adresu IP sieci TOR* . Mimo że podejrzaność działania zależy od rodzaju prowadzenia działalności przez organizację, w większości przypadków użycie routera Onion (TOR), sieci, która umożliwia użytkownikom anonimowe przeglądanie sieci Web, w środowisku przedsiębiorstwa może być traktowane jako mało prawdopodobne i niepotrzebne w przypadku zwykłych operacji online.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Chronologiczna lista zdarzeń dla użytkownika" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. Każdy alert można wybrać, aby uzyskać więcej informacji na temat działania. Na przykład wybranie działania z alertu **Adres IP** Tora prowadzi do strony tego alertu. An również jest administratorem usługi Office 365, który wskazuje na podwyższony poziom uprawnień i że zdarzenie źródłowe mogło wymagać dostępu do informacji poufnych.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Szczegóły alertów dla Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. Wybierając inne alerty, możesz uzyskać pełny obraz ataków.

## <a name="next-step"></a>Następny krok

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="Opcja Remediate (Rozwiązywanie problemów) na stronie Odpowiadanie na pierwsze zdarzenie" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

Dowiedz się, [jak rozwiązać zdarzenia](first-incident-remediate.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
