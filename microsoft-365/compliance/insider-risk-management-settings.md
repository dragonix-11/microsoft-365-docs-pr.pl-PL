---
title: Ustawienia zarządzania ryzykiem w niejawnym programie testów
description: Informacje o ustawieniach zarządzania ryzykiem w niejawnym programie testów w programie Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem w niejawnym programie testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 4b14f2def771294bdfa05109d6060242736f26d5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754717"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Wprowadzenie do ustawień zarządzania ryzykiem w niejawnym programie testów

Ustawienia zarządzania ryzykiem w niejawnym programie testów mają zastosowanie do wszystkich zasad zarządzania ryzykiem w niejawnym programie testów niezależnie od szablonu, który wybierzesz podczas tworzenia zasad. Ustawienia są konfigurowane przy **użyciu kontroli ustawień** niejawnego programu testów ryzyka znajdującej się u góry wszystkich stron zarządzania ryzykiem w niejawnym programie testów. Te ustawienia sterują składnikami zasad dla następujących obszarów:

- Prywatność
- Wskaźniki
- Osie czasu zasad
- Inteligentne wykrywanie
- Eksportowanie alertów
- Grupy użytkowników o priorytecie (wersja Preview)
- Priorytet fizycznych środków trwałych (wersja zapoznawcza)
- przepływy Power Automate (wersja zapoznawcza)
- Microsoft Teams (wersja zapoznawcza)
- Analiza
- Powiadomienia administratora

Przed rozpoczęciem i utworzeniem zasad zarządzania ryzykiem w niejawnym programie testów należy zrozumieć te ustawienia i wybrać poziomy ustawień najlepiej zgodne z potrzebami organizacji w zakresie zgodności.

## <a name="privacy"></a>Prywatność

Ochrona prywatności użytkowników, którzy mają dopasowania do zasad, jest ważna i może ułatwić promowanie obiektowości w przeglądach analizy i analizy danych w przypadku alertów o ryzyku w niejawnym programie testów. W przypadku użytkowników z dopasowaniem zasad ryzyka niejawnego programu testów możesz wybrać jedno z następujących ustawień:

- **Pokaż anonimizowane** wersje nazw użytkowników: Nazwy użytkowników są anonimizowane, aby uniemożliwić administratorom, wybranym skojarzeńom danych i recenzentom sprawdzenie, kto jest skojarzony z alertami zasad. Na przykład użytkownik Grace Taylor pojawiał się z przypadkowym pseudonimem, takim jak "AnonIS8-988" we wszystkich obszarach doświadczenia w zarządzaniu ryzykiem w niejawnym programie testów. Wybranie tego ustawienia powoduje, że wszyscy użytkownicy mają aktualne i przeszłe dopasowania oraz mają zastosowanie do wszystkich zasad. Po wybranej opcji informacje o profilu użytkownika w alertach o ryzyku niejawnego programu testów i szczegóły przypadku nie będą dostępne. Nazwy użytkowników są jednak wyświetlane podczas dodawania nowych użytkowników do istniejących zasad lub przypisywania użytkowników do nowych zasad. Jeśli wyłączysz to ustawienie, nazwy użytkowników będą wyświetlane dla wszystkich użytkowników, którzy mają dopasowania do bieżących lub wcześniejszych zasad.

    >[!IMPORTANT]
    >Aby zachować więzy integralności dla użytkowników korzystających z alertów lub spraw dotyczących ryzyka w programie Microsoft 365 lub innych systemach, anonimizacja nazw użytkowników nie jest zachowywana dla wyeksportowanych alertów. Wyeksportowane alerty będą wyświetlać nazwy użytkowników poszczególnych alertów.

- **Nie pokazuj anonimizowanych wersji** nazw użytkowników: Nazwy użytkowników są wyświetlane dla wszystkich bieżących i przeszłych spotkań dotyczących zasad dla alertów i spraw. Informacje o profilu użytkownika (imię i nazwisko, stanowisko, alias oraz organizacja lub dział) są wyświetlane użytkownikowi we wszystkich przypadkach i alertach dotyczących zarządzania ryzykiem w niejawnym programie testów.

![Ustawienia prywatności związane z zarządzaniem ryzykiem w niejawnym programie testów.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Wskaźniki

Szablony zasad ryzyka w ramach niejawnego programu testów określają typ działań ryzyka, które mają być wykrywane i badane. Każdy szablon zasad jest oparty na określonych wskaźnikach odpowiadających określonym wyzwalaczom i aktywnościom ryzyka. Wszystkie wskaźniki są domyślnie wyłączone i musisz wybrać jeden lub więcej wskaźników zasad przed skonfigurowaniem zasad zarządzania ryzykiem w niejawnym programie testów.

Alerty są wyzwalane przez zasady, gdy użytkownicy wykonują działania związane ze wskaźnikami zasad, które spełniają wymagany próg. W zarządzaniu ryzykiem w niejawnym programie testów używane są dwa typy wskaźników:

- **Wyzwalanie zdarzeń**: Zdarzenia, które określają, czy użytkownik jest aktywny w zasadach zarządzania ryzykiem w niejawnym programie testów. Jeśli użytkownik zostanie dodany do zasad zarządzania ryzykiem w niejawnym programie testów, nie powoduje wyzwolenia zdarzenia, działanie użytkownika nie jest oceniane przez te zasady. Na przykład do zasad utworzonych na podstawie szablonu zasad Kradzież danych przez  wymykanie szablonu zasad użytkowników jest dodawany użytkownik A, a łącznik kadr Microsoft 365 prawidłowo skonfigurowany. Do czasu, gdy użytkownik A nie poda daty zakończenia zgłoszonych przez łącznik kadr, działania użytkownika A nie są oceniane przez te zasady zarządzania ryzykiem w niejawnym programie testów pod pod koniec stosunku ryzyka. Innym przykładem zdarzenia wyzwalania jest to, jeśli użytkownik ma alert zasad  DLP o wysokim poziomie ważności podczas używania zasad *wycieków* danych.
- **Wskaźniki zasad**: Wskaźniki zawarte w zasadach zarządzania ryzykiem w ramach niejawnego programu testów używane do określania wyniku ryzyka dla użytkownika w zakresie. Te wskaźniki zasad są aktywowane tylko po wystąpieniu zdarzenia wyzwalania dla użytkownika. Przykładami wskaźników zasad jest skopiowanie przez użytkownika danych do osobistych usług przechowywania danych w chmurze lub przenośnych urządzeń magazynujących, usunięcie konta użytkownika z programu Azure Active Directory lub jeśli użytkownik udostępnia pliki i foldery wewnętrzne nieautoryzowanym podmiotom zewnętrznym.

Niektóre wskaźniki zasad mogą być także używane do dostosowywania zdarzeń wyzwalania dla określonych szablonów zasad. Po skonfigurowaniu w kreatorze zasad na podstawie  ogólnych wycieków danych lub  wycieków danych przez szablony priorytetów użytkowników wskaźniki te zapewniają większą elastyczność i możliwość dostosowania zasad oraz sytuacji, w których użytkownicy mają zakres zasad. Ponadto można zdefiniować poszczególne progi działań dla tych wskaźników wyzwalających w celu bardziej precyzyjnej kontroli w zasadach.

Wskaźniki zasad są podzielone na następujące obszary. Możesz wybrać wskaźniki, aby aktywować i dostosować limity zdarzeń wskaźników dla poszczególnych poziomu wskaźników podczas tworzenia zasad ryzyka w ramach niejawnego programu testów:

- **Office wskaźników** zasad: należą do nich wskaźniki zasad dla witryn sieci SharePoint, witryn sieci Microsoft Teams i wiadomości e-mail.
- **Wskaźniki urządzeń**: Obejmują one wskaźniki zasad dotyczące działań, takich jak udostępnianie plików w sieci lub za pomocą urządzeń. Wskaźniki obejmują działania obejmujące wszystkie typy plików, z wyjątkiem wykonywalnej (.exe) i dynamicznej biblioteki linków (.dll) działania na plikach. Jeśli wybierzesz *wskaźniki* urządzeń, aktywność jest przetwarzana dla urządzeń z Windows 10 kompilacja 1809 lub nowszym oraz urządzeń z systemem macOS (Catalina 10.15 lub nowszym). Zarówno w Windows jak i macOS, musisz najpierw wboardować urządzenia do Centrum zgodności. Wskaźniki urządzeń zawierają również wykrywanie sygnału przeglądarki, które pomagają Twojej organizacji wykrywać i działać na sygnałach exdrukowanego dla plików nie wykonywalnych, które były przeglądane, kopiowane, udostępniane lub drukowane w programach Microsoft Edge i Google Chrome. Aby uzyskać więcej informacji na temat konfigurowania urządzeń Windows na rzecz integracji z ryzykiem w niejawnym programie testów, zobacz następującą sekcję Włączanie wskaźników urządzeń i Windows [urządzeniach w](insider-risk-management-settings.md#OnboardDevices) tym artykule. Aby uzyskać więcej informacji na temat konfigurowania urządzeń z systemem macOS na celu integrację z ryzykiem w niejawnym programie testów, zobacz następującą sekcję Włączanie wskaźników urządzeń i dołączanie urządzeń z systemem macOS w tym artykule. Aby uzyskać więcej informacji na temat wykrywania sygnału przeglądarki, zobacz [Informacje na temat wykrywania](insider-risk-management-browser-support.md) sygnału w niejawnym programie testów i konfiguracji wykrywania sygnału przeglądarki zarządzania ryzykiem.
- **Wskaźnik naruszenia zasad zabezpieczeń (wersja Preview)**: Należą do nich wskaźniki programu Microsoft Defender for Endpoint dotyczące niestosowanych lub złośliwych instalacji oprogramowania lub pomijania kontroli zabezpieczeń. Aby otrzymywać alerty w zarządzaniu ryzykiem w niejawnym programie testów, musisz mieć aktywną licencję usługi Defender for Endpoint i integrację ryzyka niejawnego programu testów. Aby uzyskać więcej informacji na temat konfigurowania programu Defender for Endpoint na poziomie integracji zarządzania ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Wskaźniki dostępu do dokumentacji zdrowia (wersja zapoznawcza)**: Obejmują one wskaźniki zasad dostępu do dokumentacji medycznej pacjenta. Na przykład próby uzyskania dostępu do dokumentacji medycznej pacjentów w dziennikach systemu elektronicznej dokumentacji medycznej (EMR) mogą być udostępniane zasadom opieki zdrowotnej w zakresie zarządzania ryzykiem w niejawnym programie testów. Aby otrzymywać alerty tego typu w zarządzaniu ryzykiem w niejawnym programie testów, musisz mieć skonfigurowany łącznik danych dla opieki zdrowotnej i łącznik danych kadr.
- **Wskaźniki dostępu fizycznego (wersja Preview)**: Obejmują one wskaźniki zasad fizycznego dostępu do poufnych zasobów. Na przykład próby uzyskania dostępu do obszaru z ograniczeniami w fizycznych dziennikach systemowych z informacjami mogą być udostępniane przy użyciu zasad zarządzania ryzykiem w niejawnym programie testów. Aby otrzymywać alerty tego typu w zarządzaniu ryzykiem w niejawnym programie testów, musisz mieć włączone priorytetowe zasoby fizyczne w [](import-physical-badging-data.md) zarządzaniu ryzykiem w niejawnym programie testów i skonfigurowany łącznik danych fizycznie do zarządzania danymi o typie majątku. Aby dowiedzieć się więcej o konfigurowaniu dostępu fizycznego, zobacz [sekcję Priorytet dostępu fizycznego w](#priority-physical-assets-preview) tym artykule.
- **Wskaźniki programu Microsoft Defender dla aplikacji w chmurze (wersja Preview)**: Należą do nich wskaźniki zasad z alertów udostępnionych z usługi Defender dla aplikacji w chmurze. Funkcja automatycznego wykrywania anomalii w usłudze Defender dla aplikacji w chmurze natychmiast rozpoczyna wykrywanie i sortowanie wyników, skierowana na liczne anomalii zachowania na komputerach i urządzeniach połączonych z Twoją siecią. Aby uwzględnić te działania w alertach dotyczących zasad zarządzania ryzykiem w niejawnym programie testów, wybierz jeden lub więcej wskaźników w tej sekcji. Aby dowiedzieć się więcej o analizie usługi Defender dla aplikacji w chmurze i wykrywaniu [anomalii, zobacz Uzyskiwanie analizy zachowania i wykrywania anomalii](/cloud-app-security/anomaly-detection-policy).
- **Ocena ryzyka:** obejmuje to zwiększenie wyniku ryzyka dla działania, które jest powyżej zwykłego działania użytkownika w ciągu jednego dnia lub dla użytkowników, których poprzednie sprawy rozwiązano jako naruszenie zasad. Włączenie oceny ryzyka zwiększa wyniki ryzyka i prawdopodobieństwo wystąpienia alertów dotyczących tego typu działań. W przypadku aktywności, która przekracza zazwyczaj aktywność użytkownika w ciągu dnia, wyniki są zwiększane, jeśli wykryte działanie odbiega od typowego zachowania użytkownika. W przypadku użytkowników, których poprzednie sprawy zostały rozwiązane jako naruszenie zasad, wyniki są zwiększane, jeśli użytkownik miał wcześniej więcej niż jedną sprawę rozpoznaną jako potwierdzone naruszenie zasad. Ocenę ryzyka można wybrać tylko w przypadku, gdy jest wybrany co najmniej jeden wskaźnik.

W niektórych przypadkach możesz chcieć ograniczyć wskaźniki zasad niejawnego programu testów ryzyka stosowane do zasad ryzyka niejawnego programu testów w organizacji. Możesz wyłączyć wskaźniki zasad dla określonych obszarów, wyłączając je ze wszystkich zasad ryzyka w niejawnym programie testów. Wyzwalanie zdarzeń można modyfikować tylko w przypadku zasad utworzonych na *podstawie ogólnych* wycieków danych lub wycieków danych przez *szablony priorytetowych użytkowników* . Zasady utworzone na podstawie wszystkich pozostałych szablonów nie mają dostosowywalnych wskaźników wyzwalania ani zdarzeń.

Aby zdefiniować wskaźniki zasad ryzyka niejawnego programu testów, które są włączone we wszystkich zasadach ryzyka niejawnego programu testów,  >  przejdź do ustawień ryzyka niejawnego programu testówIndicatorzy i wybierz jeden lub więcej wskaźników zasad. Wskaźników zaznaczonych na stronie Ustawienia wskaźników nie można konfigurować pojedynczo podczas tworzenia lub edytowania zasad ryzyka niejawnego programu testów w kreatorze zasad.

> [!NOTE]
> Może mi potrwać kilka godzin, aby nowi ręcznie dodani użytkownicy pojawili się na **pulpicie nawigacyjnym Użytkownicy**. Wyświetlanie działań dla tych użytkowników w ciągu ostatnich 90 dni może potrwać do 24 godzin. Aby wyświetlić działania dotyczące ręcznie dodanych użytkowników, wybierz użytkownika na pulpicie  nawigacyjnym Użytkownicy i otwórz  kartę Aktywność użytkowników w okienku szczegółów.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Włączanie wskaźników urządzeń i Windows urządzenia
<a name="OnboardDevices"> </a>

Aby umożliwić monitorowanie działań ryzyka na urządzeniach Windows i uwzględnić wskaźniki zasad dla tych działań, urządzenia z systemem Windows muszą spełniać następujące wymagania i należy wykonać następujące kroki dołączania.

#### <a name="step-1-prepare-your-endpoints"></a>Krok 1. Przygotowywanie punktów końcowych

Upewnij się, że urządzenia Windows 10, które planujesz na potrzeby raportowania w zarządzaniu ryzykiem w niejawnym programie testów, spełniają te wymagania.

1. Musi być uruchomiona Windows 10 x64 kompilacja 1809 lub nowszy i musi być zainstalowana aktualizacja [systemu Windows 10 (kompilacja systemu operacyjnego 17763.1075)](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) z 20 lutego 2020 r.
2. Konto użytkownika używane do logowania się do aplikacji Windows 10 musi być aktywnym kontem Azure Active Directory (AAD). Urządzenie Windows 10 [być przyłączone](/azure/active-directory/devices/concept-azure-ad-join) do AAD, hybrydowe AAD, do usługi Active Directory lub AAD zarejestrowane.
3. Zainstaluj przeglądarkę Microsoft Edge na urządzeniu końcowym, aby monitorować akcje dotyczące działania przekazywania w chmurze. Zobacz [Pobieranie nowej aplikacji Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>Krok 2. Urządzenia dołączające
<a name="OnboardStep2"> </a>

Aby monitorować działania związane z zarządzaniem ryzykiem w niejawnym programie testów na urządzeniu, musisz włączyć monitorowanie urządzeń i włączyć punkty końcowe. Obie czynności są podejmowane w portalu Microsoft 365 zgodności.

Jeśli chcesz wboardować urządzenia, które nie zostały jeszcze wdrożone, pobierzesz odpowiedni skrypt i wdrożysz go zgodnie z poniższymi krokami.

Jeśli masz już urządzenia, które są już włożyone do programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/), będą one już widoczne na liście urządzeń zarządzanych. Wykonaj [krok 3. Jeśli masz urządzenia podłączone do programu Microsoft Defender for Endpoint](insider-risk-management-settings.md#OnboardStep3) w następnej sekcji.

W tym scenariuszu wdrażania będziesz na urządzeniach, które nie zostały jeszcze wnoszone, i chcesz tylko monitorować działania związane z ryzykiem w niejawnym programie testów na Windows 10 urządzeniach.

1. Otwórz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com).
2. Otwórz stronę ustawień Centrum zgodności i wybierz pozycję **Urządzenia w układzie .**

   > [!NOTE]
   > Włączanie dołączania do urządzenia trwa zwykle około 60 sekund, ale skontaktuj się z pomocą techniczną firmy Microsoft na maksymalnie 30 minut przed jej rozpoczęciem.

3. Wybierz **pozycję Zarządzanie urządzeniami** , aby otworzyć **listę** Urządzenia. Lista będzie pusta, dopóki nie najedziesz na urządzenia.
4. Wybierz **pozycję Dołączanie** , aby rozpocząć proces dołączania.
5. Z listy Metody wdrażania wybierz sposób wdrażania na tych większej liczby  urządzeń, a następnie **pobierz pakiet**.
6. Postępuj zgodnie z odpowiednimi procedurami w narzędziach i metodach dołączania [dla komputerów Windows 10 komputerów](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ten link przenosi Cię do strony docelowej, na której możesz uzyskać dostęp do procedur programu Microsoft Defender dla punktów końcowych, które są zgodne z pakietem wdrożenia wybranym w kroku 5:
    - Komputery Windows 10 przy użyciu zasady grupy
    - Komputery Windows przy użyciu Microsoft Endpoint Configuration Manager
    - Komputery Windows 10 urządzenia przenośne korzystające z narzędzi do zarządzania urządzeniami przenośnymi
    - Na Windows 10 komputerów przy użyciu skryptu lokalnego
    - Wyloguj nietrwałych komputerów z infrastrukturą pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure).

Po zakończeniu i dodaniem punktu końcowego powinien on być widoczny na liście urządzeń, a punkt końcowy rozpocznie raportowanie dzienników działań inspekcji do zarządzania ryzykiem w niejawnym programie testów.

> [!NOTE]
> To środowisko podlega wymuszania licencji. Bez wymaganej licencji dane nie będą widoczne ani dostępne.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>Krok 3. Jeśli masz urządzenia podłączone do programu Microsoft Defender for Endpoint
<a name="OnboardStep3"> </a>

Jeśli usługa Microsoft Defender for Endpoint jest już wdrożona i istnieją punkty końcowe raportowania, wszystkie te punkty końcowe zostaną wyświetlone na liście urządzeń zarządzanych. Możesz nadal dołączać nowe urządzenia do zarządzania ryzykiem w niejawnym programie testów, aby rozszerzyć zasięg, korzystając z sekcji Krok [2:](insider-risk-management-settings.md#OnboardStep2) Urządzenia do dołączania.

1. Otwórz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com).
2. Otwórz stronę ustawień Centrum zgodności i wybierz pozycję **Włącz monitorowanie urządzeń**.
3. Wybierz **pozycję Zarządzanie urządzeniami** , aby otworzyć **listę** Urządzenia. Powinna zostać wyświetlona lista urządzeń, które już zgłaszają się do programu Microsoft Defender for Endpoint.
4. Wybierz **pozycję Dołączanie** , jeśli musisz wychować więcej urządzeń.
5. Z listy Metody wdrażania wybierz sposób wdrażania na tych większej liczby  urządzeń, a następnie wybierz **pozycję Pobierz pakiet**.
6. Postępuj zgodnie z odpowiednimi procedurami w narzędziach i metodach dołączania [dla komputerów Windows 10 komputerów](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ten link przenosi Cię do strony docelowej, na której możesz uzyskać dostęp do procedur programu Microsoft Defender dla punktów końcowych, które są zgodne z pakietem wdrożenia wybranym w kroku 5:
    - Komputery Windows 10 przy użyciu zasady grupy
    - Komputery Windows przy użyciu Microsoft Endpoint Configuration Manager
    - Komputery Windows 10 urządzenia przenośne korzystające z narzędzi do zarządzania urządzeniami przenośnymi
    - Na Windows 10 komputerów przy użyciu skryptu lokalnego
    - Wyloguj nietrwałych komputerów z infrastrukturą pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure).

Po zakończeniu i rozpoczęciu punktu końcowego powinien on być widoczny w tabeli  Urządzenia, a punkt końcowy rozpocznie raportowanie dzienników działań inspekcji do zarządzania ryzykiem w niejawnym programie testów.

> [!NOTE]
>To środowisko podlega wymuszania licencji. Bez wymaganej licencji dane nie będą widoczne ani dostępne.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Włączanie wskaźników urządzeń i dołączanie urządzeń z systemem macOS

Urządzenia z systemem macOS (Catalina 10.15 lub nowszym) mogą być dołączane do programu Microsoft 365 w celu obsługi zasad zarządzania ryzykiem w niejawnym programie testów przy użyciu usługi Intune lub usługi JAMF Pro. Aby uzyskać więcej informacji i wskazówki dotyczące konfiguracji, zobacz [Dołączanie urządzeń z systemem macOS do Microsoft 365 (wersja zapoznawcza)](device-onboarding-macos-overview.md).

### <a name="indicator-level-settings-preview"></a>Ustawienia poziomu wskaźnika (podgląd)

Podczas tworzenia zasad w kreatorze zasad można skonfigurować wpływ dziennej liczby zdarzeń ryzyka na ocenę ryzyka dla alertów o czynnikach ryzyka w niejawnym programie testów. Te ustawienia wskaźnika ułatwiają kontrolowanie, jak liczba wystąpień zdarzeń ryzyka w organizacji powinna wpłynąć na wynik ryzyka, a zatem skojarzoną ważność alertów dla tych zdarzeń. Jeśli wolisz, możesz również wybrać zachowanie domyślnych poziomów progów zdarzeń zalecanych przez firmę Microsoft dla wszystkich włączonych wskaźników.

Na przykład możesz włączyć wskaźniki SharePoint w ustawieniach zasad ryzyka niejawnego programu testów i ustawić niestandardowe progi dla zdarzeń programu SharePoint podczas konfigurowania wskaźników dla nowych zasad wycieków danych ryzyka niejawnego programu *testów.* W kreatorze zasad dotyczących ryzyka niejawnego programu testów konfigurujesz trzy różne poziomy zdarzeń dziennych dla każdego SharePoint wskaźników ryzyka, aby wpłynąć na ocenę ryzyka dla alertów skojarzonych z tymi zdarzeniami.

![Ustawienia niestandardowych wskaźników zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-custom-indicators.png)

Dla pierwszego dziennego poziomu wydarzenia ustawia się próg *na 10* lub więcej zdarzeń dziennie, aby uzyskać niższy wpływ na ocenę ryzyka zdarzeń, *20* lub więcej zdarzeń dziennie, aby uzyskać średni wpływ na ocenę ryzyka zdarzeń, oraz *30* lub więcej zdarzeń dziennie, co ma wyższy wpływ na ocenę ryzyka zdarzeń. Te ustawienia oznaczają w praktyce:

- Jeśli po wyzwoleniu zdarzenia ma miejsce 1–SharePoint 9 zdarzeń, które mają miejsce po wyzwoleniu zdarzenia, wyniki ryzyka mają minimalny wpływ i zwykle nie generują alertu.
- Jeśli po wyzwalaniu zdarzenia ma miejsce 10–1 SharePoint 9 zdarzeń, które mają miejsce po wyzwoleniu zdarzenia, ocena ryzyka jest z natury niższy, a poziomy ważności alertów zwykle znajdują się na niskim poziomie.
- Jeśli po wyzwalaczu występują zdarzenia SharePoint 20–29, ocena ryzyka jest z natury wyższa, a poziomy ważności alertów zwykle znajdują się na poziomie średnim.
- Jeśli istnieje co najmniej 30 SharePoint zdarzeń, które mają miejsce po wyzwalaczu, ocena ryzyka jest z natury wyższa, a poziomy ważności alertów zwykle znajdują się na wysokim poziomie.

## <a name="policy-timeframes"></a>Ramy czasowe zasad

Ramy czasowe zasad umożliwiają definiowanie przeszłych i przyszłych okresów przeglądu wyzwalanych po dopasowaniach zasad na podstawie zdarzeń i działań w szablonach zasad zarządzania ryzykiem w ramach niejawnego programu testów. W zależności od wybranego szablonu zasad dostępne są następujące ramy czasowe zasad:

- **Okno aktywacji**: Dostępne dla wszystkich szablonów zasad Okno aktywacji  to zdefiniowana liczba dni aktywowana przez okno po zdarzeniu  wyzwalające. Okno aktywuje się od 1 do 30 dni po wystąpieniu zdarzenia wyzwalania dla każdego użytkownika przypisanego do zasad. Na przykład skonfigurowano zasady zarządzania ryzykiem w niejawnym programie testów i ustawiono wartość Okna *aktywacji* na 30 dni. Od skonfigurowania zasad minęło kilka miesięcy i występuje zdarzenie wyzwalające dla jednego z użytkowników uwzględnionych w zasadach. Zdarzenie wyzwalające aktywuje okno *Aktywacja* i zasady są aktywne dla tego użytkownika przez 30 dni od wystąpienia zdarzenia wyzwalającego.
- **Wykrywanie działań w przeszłości**: Dostępne dla wszystkich szablonów zasad Wykrywanie  działań w przeszłości to zdefiniowana liczba dni aktywowana przez okno przed wyzwoleniem zdarzenia. Okno aktywuje się na 0 do 90 dni przed zdarzeniem wyzwalania dla dowolnego użytkownika przypisanego do zasad. Na przykład skonfigurowano zasady zarządzania ryzykiem w niejawnym programie testów i ustawiono wartość Wykrywanie działań w przeszłości na 90 dni. Od skonfigurowania zasad minęło kilka miesięcy i występuje zdarzenie wyzwalające dla jednego z użytkowników uwzględnionych w zasadach. Zdarzenie wyzwalające aktywuje wykrywanie działań  w przeszłości, a zasady zbierają działania historyczne dla tego użytkownika na 90 dni przed zdarzeniem wyzwalającym.

![Ustawienia czasowe zarządzania ryzykiem w ramach niejawnego programu testów.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Inteligentne wykrywanie

Ustawienia inteligentnego wykrywania pomagają uściślić sposób przetwarzania wykrywania ryzykownych działań na alerty. W niektórych okolicznościach może być konieczne zdefiniowanie typów plików do ignorowania lub wymuszanie poziomu wykrywania dla dziennych zdarzeń w celu zwiększenia wyników ryzyka dla użytkowników. Za pomocą tych ustawień można sterować wykluczeniami typów plików, aby sterować ocenami ryzyka dla nietypowej aktywności i limitami liczby plików.

### <a name="file-type-exclusions"></a>Wykluczenia typów plików

Aby wykluczyć określone typy plików ze wszystkich zasad zarządzania ryzykiem w niejawnym programie testów, wprowadź rozszerzenia typu plików oddzielone przecinkami. Aby na przykład wykluczyć określone typy plików muzycznych z zasad, możesz wprowadzić *wartości aac,mp3,wav,wma* w polu **Wykluczeń typu** pliku. Pliki z tymi rozszerzeniami są ignorowane przez wszystkie zasady zarządzania ryzykiem w niejawnym programie testów.

### <a name="minimum-number-of-daily-events-to-boost-score-for-unusual-activity"></a>Minimalna liczba codziennych wydarzeń, aby zwiększyć liczbę wyników dla nietypowej aktywności

To ustawienie pozwala określić, ile codziennych zdarzeń wymaga, aby zwiększyć ocenę ryzyka dla działania uznawanego za nietypowe dla użytkownika. Załóżmy na przykład, że wprowadzasz wartość 25 dla tego ryzyka. Jeśli w ciągu ostatnich 30 dni użytkownik średnio pobrał 10 plików, ale zasady wykryje, że pobrał 20 plików w ciągu jednego dnia, wyniki dla tej aktywności nie zostaną zwiększone, mimo że jest to nietypowe dla tego użytkownika, ponieważ liczba pobieranych plików tego dnia była mniejsza niż wartość wprowadzona dla tego ryzyka.

### <a name="alert-volume"></a>Głośność alertu

W działaniach użytkowników wykrytych przez zasady ryzyka niejawnego programu testów przypisywany jest określony wynik ryzyka, który z kolei określa stopień zagrożenia (niski, średni i wysoki). Domyślnie zostanie wygenerowana duża liczba alertów o niskim, średnim i wysokim poziomie ważności, ale możesz odpowiednio zwiększyć lub zmniejszyć liczbę alertów. Aby dostosować ilość alertów dotyczących wszystkich zasad zarządzania ryzykiem w niejawnym programie testów, wybierz jedno z następujących ustawień:

- **Mniej alertów**: Zobaczysz wszystkie alerty o wysokim poziomie ważności, mniej alertów o średnim poziomie ważności i nie tylko alerty o niskim poziomie ważności. Ten poziom ustawień oznacza, że możesz przeoczyć niektóre prawdziwe pozytywy.
- **Głośność domyślna**: Zobaczysz wszystkie alerty o wysokim poziomie ważności oraz zrównoważonej ilości alertów o średniej i niskiej ważności.
- **Więcej alertów**: Zobaczysz wszystkie alerty o średnim i wysokim poziomie ważności oraz alerty o najbardziej niskim poziomie ważności. Ten poziom ustawień może spowodować więcej wyników fałszywie dodatnich.

### <a name="microsoft-defender-for-endpoint-preview"></a>Microsoft Defender for Endpoint (preview)

[Program Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) to platforma zabezpieczeń punktów końcowych przedsiębiorstwa, która ma ułatwić sieciom przedsiębiorstwa zapobieganie zaawansowanym zagrożeniam, wykrywanie, badanie i reagowanie na nie. Aby poprawić widoczność naruszeń zabezpieczeń w organizacji, możesz zaimportować i odfiltrować usługę Defender, aby uzyskać alerty punktu końcowego w przypadku działań używanych w zasadach utworzonych na podstawie szablonów zasad naruszenia zabezpieczeń zarządzania ryzykiem w ramach niejawnego programu testów.

W zależności od typów sygnałów, które Cię interesują, możesz wybrać importowanie alertów do zarządzania ryzykiem w niejawnym programie testów na podstawie stanu triage alertu programu Defender dla punktu końcowego. W ustawieniach globalnych można zdefiniować co najmniej jeden z następujących stanów alertów do określenia w celu zaimportowania:

- Unknown
- Nowy
- W toku
- Rozpoznane

Alerty z usługi Defender dla punktu końcowego są importowane codziennie. W zależności od wybranego stanu triage dla tego samego alertu może być wyświetlonych wiele działań użytkownika, co zmiana stanu triage w programie Defender for Endpoint.

Jeśli na przykład wybierzesz dla tego ustawienia pozycję *Nowy, W* toku i Rozwiązano, gdy zostanie wygenerowany alert programu Microsoft Defender dla punktu końcowego i ma on stan  *Nowy, dla* użytkownika o ryzyku niejawnego programu testów zostanie zaimportowane początkowe działanie alertu. Gdy stan triage usługi Defender for Endpoint zmieni się na W *toku, drugie* działanie dla tego alertu zostanie zaimportowane dla użytkownika o ryzyku niejawnego programu testów. Po ustawianiu końcowego stanu niejawnego programu testów usługi Defender for Endpoint rozpoznanego użytkownika jest importowane trzecie działanie dla tego alertu dla użytkownika o ryzyku niejawnego programu testów. Ta funkcja umożliwia schłodom obserwowanie postępu alertów programu Defender dla punktu końcowego i wybranie poziomu widoczności wymaganego dla ich badania.

> [!IMPORTANT]
> Aby importować alerty o naruszeniach zabezpieczeń, musisz mieć program Microsoft Defender for Endpoint skonfigurowany w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem w Centrum zabezpieczeń Defender. Aby uzyskać więcej informacji na temat konfigurowania programu Defender for Endpoint na poziomie integracji zarządzania ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Domeny

Ustawienia domeny ułatwiają definiowanie poziomów ryzyka dla działań w określonych domenach. Działania te obejmują udostępnianie plików, wysyłanie wiadomości e-mail, pobieranie lub przekazywanie zawartości. Określenie domen w tych ustawieniach pozwala zwiększyć lub zmniejszyć wyniki oceny ryzyka dla działań z tymi domenami.

Za pomocą przycisku Dodaj domenę zdefiniuj domenę dla każdego z ustawień domeny. Ponadto możesz używać symboli wieloznacznych, aby dopasować odmiany domen głównych lub poddomen. Aby na przykład określić typy sales.wingtiptoys.com i support.wingtiptoys.com, użyj symbolu wieloznacznego "*.wingtiptoys.com" w celu dopasowania tych poddomen (i dowolnej innej poddomeny na tym samym poziomie). Aby określić wielopoziomowe poddomeny dla domeny głównej, musisz zaznaczyć pole wyboru **Uwzględnij poddomeny** wielopoziomowe.

Dla każdego z poniższych ustawień domeny możesz wprowadzić maksymalnie 500 domen:

- **Niedozwolone domeny:** Określenie domen, które są niedozwolone, spowoduje, że aktywność w tych domenach będzie miała *wyższe* wyniki ryzyka. Niektóre przykłady to działania obejmujące udostępnianie zawartości innej osobie (na przykład wysyłanie wiadomości e-mail do osoby z adresem gmail.com) oraz pobieranie zawartości na urządzenie z jednej z tych domen, które są niedozwolone.
- **Dozwolone domeny:** Określone działania związane z dozwolonymi domenami będą ignorowane przez Twoje zasady i nie będą generować alertów. Są to między innymi następujące działania:

    - Wiadomości e-mail wysyłane do domen zewnętrznych
    - Pliki, foldery, witryny udostępnione domenom zewnętrznym
    - Pliki przekazane do domen zewnętrznych (przy Microsoft Edge przeglądarce)

    Określając dozwolone domeny w ustawieniach, to działanie w tych domenach jest traktowane podobnie jak aktywność wewnętrzna organizacji. Na przykład domeny dodane w tym miejscu są mapowanie na działania mogą obejmować udostępnianie zawartości osobie spoza organizacji (na przykład wysyłanie wiadomości e-mail do osoby gmail.com adres).

- **Domeny innych firm:** Jeśli Twoja organizacja korzysta z domen innych firm do celów biznesowych (takich jak magazyn w chmurze), uwzględnij je tutaj, aby otrzymywać alerty dotyczące działań związanych ze wskaźnikiem urządzenia Pobieranie zawartości z witryny innej firmy za pomocą *przeglądarki*.

## <a name="export-alerts"></a>Eksportowanie alertów

Informacje alertów dotyczących zarządzania ryzykiem w niejawnym programie testów można eksportować do rozwiązań do zarządzania informacjami o zabezpieczeniach i zdarzeniach oraz do rozwiązań soar (Security Management Automated Response) przy użyciu schematu [interfejsu API](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema) działań zarządzania Office 365. Za pomocą interfejsów API działań zarządzania Office 365 możesz wyeksportować informacje alertów do innych aplikacji, za pomocą których Twoja organizacja może zarządzać informacjami o czynnikach ryzyka w niejawnym programie testów lub agregować je. Informacje alertów są eksportowane i dostępne co 60 minut za pośrednictwem Office 365 interfejsów API działań zarządzania alertami.

Jeśli Twoja organizacja korzysta z programu Microsoft Sentinel, możesz również zaimportować informacje alertów o ryzyku niejawnego programu testów do programu Sentinel za pomocą owego łącznika danych zarządzania ryzykiem w niejawnym programie testów. Aby uzyskać więcej informacji, zobacz Microsoft 365 zarządzanie ryzykiem w niejawnym programie testów [(IRM, Insider Risk Management) (wersja Preview)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) w artykule programu Microsoft Sentinel.

>[!IMPORTANT]
>Aby zachować więzy integralności dla użytkowników korzystających z alertów lub spraw dotyczących ryzyka w programie Microsoft 365 lub innych systemach, anonimizacja nazw użytkowników nie jest zachowywana dla wyeksportowanych alertów. Wyeksportowane alerty będą wyświetlać nazwy użytkowników poszczególnych alertów.

Aby za pomocą interfejsów API przeglądać informacje alertów o ryzyku w niejawnym programie testów:

1. Włącz Office 365 interfejsu API działań **zarządzania w zarządzaniu** ryzykiem w niejawnym  >  programie **testów Ustawienia** >  **Alerty dotycząceportów**. Domyślnie to ustawienie jest wyłączone dla Twojej Microsoft 365 organizacji.
2. Filtrowanie typowych działań Office 365 przez *securitycomplianceAlerts*.
3. *Filtruj ustawienia SecurityComplianceAlerts* według *kategorii InsiderRiskManagement*.

![Ustawienia alertów eksportu zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-settings-export.png)

Informacje alertów zawierają informacje ze schematu alertów zabezpieczeń i zgodności oraz wspólnego Office 365 API działań zarządzania.

Następujące pola i wartości są eksportowane dla alertów zarządzania ryzykiem w niejawnym programie testów dla schematu alertów zabezpieczeń i & zgodności:

| **Parametr alertu** | **Opis** |
|:------------------|:----------------|
| AlertType (Typ alertu) | Typ alertu to *Niestandardowe*.  |
| AlertId | Identyfikator GUID alertu. Alerty dotyczące zarządzania ryzykiem w niejawnym programie testów są wyciszone. W przypadku zmiany stanu alertu zostanie wygenerowany nowy dziennik o tym samymidie alertu. Ten alertID może być używany do korelowania aktualizacji alertu. |
| Kategoria | Kategorią alertu jest *InsiderRiskManagement*. Za pomocą tej kategorii można odróżnić te alerty od innych alertów zabezpieczeń & zabezpieczeń i zgodności. |
| Komentarze | Komentarze domyślne alertu. Wartości to *Nowy alert* (rejestrowany po utworzeniu alertu) i *Zaktualizowano alert* (rejestrowane w przypadku aktualizacji alertu). Za pomocą funkcji AlertID koreluj aktualizacje alertu. |
| Data (Dane) | Dane alertu zawierają unikatowy identyfikator użytkownika, główną nazwę użytkownika oraz datę i czas (UTC) po wyzwoleniu użytkownika do zasad. |
| Name (Nazwa) | Nazwa zasad dla zasad zarządzania ryzykiem w niejawnym programie testów, które wygenerowała alert. |
| PolicyId | Identyfikator GUID zasad zarządzania ryzykiem w niejawnym programie testów, które wyzwoliły alert. |
| Ważność | Ważność alertu. Wartości to *Wysoki*, *Średni* lub *Niski*. |
| Źródło | Źródło alertu. Wartość ta to *Office 365 zabezpieczeń & zgodności*. |
| Stan | Stan alertu. Wartości to *: Aktywny* (*przegląd potrzeb* w zakresie ryzyka w niejawnym programie testów *), Badanie* *(potwierdzone* ryzykiem niejawnego programu testów *),* Rozwiązane *(* rozwiązane w przypadku ryzyka niejawnego programu testów *),* Odrzucone *(* odrzucone przy ryzyku niejawnego programu testów). |
| Wersja | Wersja schematu alertów zabezpieczeń i zgodności. |

Następujące pola i wartości są eksportowane dla alertów dotyczących zarządzania ryzykiem w niejawnym programie testów dla [wspólnego Office 365 API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema).

- UserId
- Identyfikator
- RecordType (Typ rekordu)
- CreationTime
- Operacja
- OrganizationId
- UserType (Typ użytkownika)
- UserKey (Klucz użytkownika)

## <a name="priority-user-groups-preview"></a>Grupy użytkowników o priorytecie (wersja Preview)

Użytkownicy w Twojej organizacji mogą mieć różne poziomy ryzyka w zależności od ich pozycji, poziomu dostępu do informacji poufnych lub historii ryzyka. Ustalanie priorytetu insekcji i oceniania działań tych użytkowników może ułatwić ostrzeganie o potencjalnych zagrożeniach, które mogą mieć większe konsekwencje dla organizacji. Grupy użytkowników o wysokim priorytecie w zarządzaniu ryzykiem w niejawnym programie testów ułatwiają definiowanie użytkowników w organizacji, którzy muszą być dokładniejsi i dokładniej oceniać ryzyko. W połączeniu z *naruszeniami* zasad zabezpieczeń przez użytkowników o wysokim  priorytecie i wyciekami danych przez szablony zasad priorytetu użytkowników użytkownicy dodani do grupy użytkowników priorytetowych mają zwiększone prawdopodobieństwo wystąpienia alertów i alertów o poziomie zagrożenia niejawnego programu testów o wyższym poziomie ważności.

![Ustawienia grupy użytkowników o priorytecie zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-settings-priority-users.png)

Zamiast być otwarta do przeglądania przez wszystkich analityków i osoby wschłodowe, grupy użytkowników priorytetowych mogą również ograniczać działania re przeglądu do konkretnych użytkowników lub grup ról ryzyka niejawnego programu testów. Możesz przypisywać poszczególnych użytkowników i grupy ról do przeglądania użytkowników, alertów, spraw i raportów dla poszczególnych grup użytkowników o priorytecie. Grupy użytkowników o priorytecie mogą mieć uprawnienia do przeglądania przypisane do wbudowanych grup ról Zarządzanie ryzykiem w niejawnym programie  testów *,* Analityków zarządzania ryzykiem niejawnego programu testów i Grupy ról zarządzania ryzykiem w niejawnym programie testów, co najmniej jednej z tych grup ról, bądź do niestandardowego wyboru użytkowników.

Na przykład musisz chronić się przed wyciekami danych w przypadku wysoce poufnego projektu, w którym użytkownicy mają dostęp do poufnych informacji. Możesz utworzyć grupę *Priorytet Project* *użytkowników* dla użytkowników w twojej organizacji, którzy pracują nad tym projektem. Ponadto ta grupa użytkowników o priorytecie nie powinna mieć użytkowników, alertów, spraw i raportów skojarzonych z grupą, które są widoczne dla wszystkich domyślnych administratorów zarządzających ryzykiem w niejawnym programie testów, analityków i wcięć. W **Ustawienia** grupy Użytkownicy priorytetowi mają Project  i przypisano dwóch użytkowników jako recenzentów, którzy mogą wyświetlać dane powiązane z grupami. Za pomocą kreatora zasad *i szablonu zasad* Wycieki danych według priorytetów użytkowników możesz utworzyć nowe zasady i przypisać do zasad poufne Project *priorytet* użytkowników. Działania sprawdzane przez zasady dla członków grupy użytkowników o wyższym priorytecie Project Priorytet użytkownicy są bardziej poufne na ryzyko, *a* działania tych użytkowników będą bardziej prawdopodobne do wygenerowania alertu i alertów o wyższym poziomie ważności.

### <a name="create-a-priority-user-group"></a>Tworzenie grupy użytkowników o priorytecie

Aby utworzyć nową grupę użytkowników o nowym priorytecie, użyj kontrolek  ustawień w rozwiązaniu do zarządzania ryzykiem niejawnego programu testów w grupie Centrum zgodności platformy Microsoft 365. Aby utworzyć grupę użytkowników o priorytecie, musisz być członkiem  grupy ról Zarządzanie ryzykiem w niejawnym programie testów lub Administrator *zarządzania ryzykiem w* niejawnym programie testów.

Wykonaj następujące czynności, aby utworzyć grupę użytkowników o priorytecie:

1. W centrum [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) do tematu Zarządzanie ryzykiem **w niejawnym programie** testów i wybierz pozycję **Ustawienia ryzyka niejawnego programu testów**.
2. Wybierz stronę **Priorytetowe grupy użytkowników (wersja zapoznawcza** ).
3. Na stronie **Priorytetowe grupy użytkowników (wersja zapoznawcza)** wybierz pozycję **Utwórz** grupę użytkowników o priorytecie, aby uruchomić kreatora tworzenia grup.
4. Na **stronie Nazwa i opisz** wypełnij następujące pola:
    - **Nazwa (wymagany)**: Wprowadź przyjazną nazwę grupy użytkowników o priorytecie. Po zakończeniu działania kreatora nie można zmienić nazwy grupy użytkowników o priorytecie.
    - **Opis (opcjonalnie)**: Wprowadź opis grupy użytkowników o priorytecie.
5. Wybierz przycisk **Dalej**, aby kontynuować.
6. Na **stronie Wybieranie** członków wybierz pozycję Wybierz  członków do przeszukania i wybierz konta użytkowników z włączoną obsługą poczty, które mają zostać uwzględnione  w grupie, lub zaznacz pole wyboru Zaznacz wszystkie, aby dodać do grupy wszystkich użytkowników w organizacji. Wybierz **pozycję Dodaj** , aby kontynuować, lub pozycję **Anuluj** , aby zamknąć bez dodawania użytkowników do grupy.
7. Wybierz przycisk **Dalej**, aby kontynuować.
8. Na stronie **Wybierz, kto** może wyświetlać tę grupę musisz określić, kto może przeglądać użytkowników, alerty, sprawy i raporty dla grupy użytkowników o priorytecie. Należy przypisać co najmniej jedną grupę ról do zarządzania ryzykiem w niejawnym programie testów lub użytkownika. Wybierz **pozycję Wybierz użytkowników i grupy ról** , a następnie wybierz użytkowników lub grupy ról zarządzania ryzykiem niejawnego programu testów, które chcesz przypisać do grupy użytkowników priorytetowych. Wybierz **pozycję Dodaj** , aby przypisać wybranych użytkowników lub grupy ról do grupy.
9. Wybierz przycisk Dalej, aby kontynuować.
10. Na stronie **Recenzja** przejrzyj ustawienia wybrane dla grupy użytkowników o priorytecie. Wybierz link **Edytuj** , aby zmienić dowolną wartość grupy, lub wybierz pozycję **Prześlij,** aby utworzyć i aktywować grupę użytkowników o priorytecie.
11. Na stronie potwierdzenia **wybierz pozycję Gotowe** , aby zamknąć kreatora.

### <a name="update-a-priority-user-group"></a>Aktualizowanie grupy użytkowników o priorytecie

Aby zaktualizować istniejącą grupę użytkowników o priorytecie, użyj kontrolek  ustawień w rozwiązaniu do zarządzania ryzykiem niejawnego programu testów w grupie Centrum zgodności platformy Microsoft 365. Aby zaktualizować grupę użytkowników o priorytecie, musisz być członkiem grupy ról Zarządzanie ryzykiem niejawnego programu testów lub Administrator *zarządzania ryzykiem w* niejawnym programie testów.

Aby edytować grupę użytkowników o priorytecie, wykonaj następujące czynności:

1. W centrum [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) do tematu Zarządzanie ryzykiem **w niejawnym programie** testów i wybierz pozycję **Ustawienia ryzyka niejawnego programu testów**.
2. Wybierz stronę **Priorytetowe grupy użytkowników (wersja zapoznawcza** ).
3. Wybierz grupę użytkowników o priorytecie, którą chcesz edytować, a następnie wybierz **pozycję Edytuj grupę**.
4. Na **stronie Nazwa i opisz** w razie potrzeby zaktualizuj pole Opis. Nie można zaktualizować nazwy grupy użytkowników o priorytecie. Wybierz przycisk **Dalej**, aby kontynuować.
5. Na stronie **Wybieranie członków** dodaj nowych członków do grupy przy użyciu **kontrolki Wybierz** członków. Aby usunąć użytkownika z grupy, wybierz znak "X" obok użytkownika, który chcesz usunąć. Wybierz przycisk **Dalej**, aby kontynuować.
6. Na stronie **Wybierz, kto** może wyświetlać tę grupę możesz dodawać lub usuwać użytkowników lub grupy ról, które mogą przeglądać użytkowników, alerty, sprawy i raporty dla grupy użytkowników o priorytecie.
7. Wybierz przycisk **Dalej**, aby kontynuować.
8. Na stronie **Recenzja** przejrzyj ustawienia aktualizacji wybrane dla grupy użytkowników o priorytecie. Wybierz link **Edytuj** , aby zmienić dowolną wartość grupy, lub wybierz pozycję **Prześlij,** aby zaktualizować grupę użytkowników o priorytecie.
9. Na stronie potwierdzenia **wybierz pozycję Gotowe** , aby zamknąć kreatora.

### <a name="delete-a-priority-user-group"></a>Usuwanie grupy użytkowników o priorytecie

Aby usunąć istniejącą grupę użytkowników o priorytecie, użyj kontrolek ustawień  w rozwiązaniu do zarządzania ryzykiem niejawnego programu testów w grupie Centrum zgodności platformy Microsoft 365. Aby usunąć grupę użytkowników o priorytecie, musisz być członkiem  grupy ról Zarządzanie ryzykiem niejawnego programu testów lub Administrator zarządzania *ryzykiem w* niejawnym programie testów.

> [!IMPORTANT]
> Usunięcie grupy użytkowników o priorytecie spowoduje usunięcie jej z wszystkich aktywnych zasad, do których jest przypisana. Jeśli usuniesz grupę użytkowników o priorytecie przypisaną do aktywnych zasad, zasady nie będą zawierać żadnych użytkowników w zakresie i będą w praktyce bezczynne i nie będą tworzyć alertów.

Wykonaj następujące czynności, aby usunąć grupę użytkowników o priorytecie:

1. W centrum [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) do tematu Zarządzanie ryzykiem **w niejawnym programie** testów i wybierz pozycję **Ustawienia ryzyka niejawnego programu testów**.
2. Wybierz stronę **Priorytetowe grupy użytkowników (wersja zapoznawcza** ).
3. Wybierz grupę użytkowników o priorytecie, którą chcesz edytować, a następnie wybierz **pozycję Usuń** z menu pulpitu nawigacyjnego.
4. W **oknie dialogowym Usuwanie** wybierz pozycję **Tak** , aby usunąć grupę użytkowników o priorytecie, lub pozycję **Anuluj** , aby powrócić do pulpitu nawigacyjnego.

## <a name="priority-physical-assets-preview"></a>Priorytet fizycznych środków trwałych (wersja zapoznawcza)

Identyfikowanie dostępu do priorytetów fizycznych środków trwałych i skorelowanie aktywności dostępu ze zdarzeniami użytkownika jest ważnym elementem infrastruktury zgodności. Te zasoby fizyczne reprezentują priorytetowe lokalizacje w organizacji, takie jak budynki firmy, centra danych lub pomieszczenia serwerowe. Działania niejawnego programu testów mogą być skojarzone z użytkownikami pracującymi w nietypowych godzinach, próbami uzyskania dostępu do tych nieautoryzowanych poufnych lub bezpiecznych obszarów oraz żądaniami dostępu do obszarów wysokiego poziomu bez uzasadnionego potrzeby.

Dzięki włączonej opcji priorytetu fizycznych [](import-physical-badging-data.md) środków trwałych i skonfigurowanego łącznika danych fizycznego zarządzania zabezpieczeniami niejawny program testów integruje sygnały z fizycznych systemów kontroli i dostępu do nich z innymi działaniami ryzyka użytkownika. Analizując wzorce zachowania w systemach dostępu fizycznego i skorelując te działania z innymi zdarzeniami ryzyka niejawnego programu testów, zarządzanie ryzykiem niejawnego programu testów może ułatwić analitykom i analitykom podejmowanie bardziej świadomych decyzji dotyczących reakcji dotyczących alertów. Uzyskiwanie dostępu do priorytetowych fizycznych środków trwałych jest punktowane i identyfikowane w szczegółowych informacjach w inny sposób niż dostęp do zasobów o innych priorytetach.

Na przykład organizacja ma system zarządzania zabezpieczeniami dla użytkowników, którzy monitoruje i zatwierdzają dostęp fizyczny do normalnych obszarów roboczych i poufnych projektów. Kilku użytkowników pracuje nad poufnym projektem i po zakończeniu projektu powróci on do innych obszarów organizacji. Gdy poufny projekt zbliża się do ukończenia, chcesz mieć pewność, że praca nad projektem pozostanie poufna i że dostęp do obszarów projektu będzie ściśle kontrolowany.

Użytkownik zdecyduje się włączyć łącznik fizycznych danych umożliwiających określanie wartości nieruchomości w programie Microsoft 365 w celu importowania informacji o dostępie z fizycznego systemu oceny i określania priorytetów fizycznych środków trwałych w zarządzaniu ryzykiem w niejawnym programie testów. Importując informacje z systemu oceny i skorelując informacje z dostępem fizycznym z innymi działaniami ryzyka zidentyfikowanymi w zarządzaniu ryzykiem w ramach niejawnego programu testów, jeden z użytkowników projektu uzyskuje dostęp do biur projektów po normalnych godzinach pracy, a także eksportuje duże ilości danych do osobistej usługi magazynu w chmurze z ich normalnego obszaru roboczego. Ta aktywność fizyczna dostępu skojarzona z aktywnością w trybie online może prowadzić do możliwej kradzieży danych i skojarzeń ze zgodnością, a analitycy mogą podjąć odpowiednie działania, zgodnie z podjęciem odpowiednich działań w ypadku dla tego użytkownika.

![Bezpieczeństwo aktywów fizycznych w zarządzaniu ryzykiem w niejawnym programie testów.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Konfigurowanie priorytetów fizycznych środków trwałych

Aby skonfigurować priorytet fizycznych środków trwałych, należy skonfigurować łącznik fizyczny do zarządzania zabezpieczeniami i użyć kontrolek ustawień  w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów w p Centrum zgodności platformy Microsoft 365. Aby skonfigurować priorytet fizycznych środków trwałych, musisz być członkiem grupy ról  Zarządzanie ryzykiem w niejawnym programie testów lub Administrator zarządzania *ryzykiem w niejawnym programie testów*.

Wykonaj następujące czynności, aby skonfigurować priorytet fizycznych zasobów:

1. Postępuj zgodnie z instrukcjami konfiguracyjnymi w celu zarządzania ryzykiem w niejawnym programie testów w artykule Wprowadzenie [do zarządzania ryzykiem w niejawnym programie](insider-risk-management-configure.md) testów. W kroku 3 upewnij się, że skonfigurowano łącznik z fizycznymi zabezpieczeniami.

    > [!IMPORTANT]
    > Aby zasady zarządzania ryzykiem w niejawnym programie testów były wykorzystywane i skorelowane z danymi sygnału dotyczącymi odchodzijących i zakończonych użytkowników danymi zdarzeń z platformy kontroli fizycznej i dostępu, musisz również skonfigurować łącznik Microsoft 365 KADR. Jeśli włączysz łącznik fizyczny do zarządzania zabezpieczeniami bez włączania łącznika kadr w programie Microsoft 365, zasady zarządzania ryzykiem w niejawnym programie testów będą przetwarzać zdarzenia tylko w przypadku działań fizycznego dostępu dla użytkowników w organizacji.

2. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do **strony Zarządzanie ryzykiem** w niejawnym programie testów i **wybierz pozycję** >  Ustawienia ryzyka niejawnego programu testówPriorność **fizycznych środków trwałych**.
3. Na stronie  Priorytet fizycznych środków trwałych możesz ręcznie dodać identyfikatory fizyczne środków trwałych, które mają być monitorowane pod względem zdarzeń środków trwałych zaimportowanych przez łącznik Opcji fizycznych lub zaimportować plik .csv wszystkich identyfikatorów fizycznych środków trwałych zaimportowanych za pomocą łącznika aktywów fizycznych: a) Aby ręcznie dodać identyfikatory fizycznych środków trwałych, wybierz pozycję Dodaj priorytetowe **zasoby fizyczne**.  wprowadź identyfikator fizycznych środków trwałych, a następnie wybierz **pozycję Dodaj**. Wprowadź inne identyfikatory fizycznych środków trwałych, a następnie wybierz pozycję **Dodaj priorytetowe zasoby fizyczne** , aby zapisać wszystkie wprowadzone środki trwałe.
    b) Aby dodać listę identyfikatorów fizycznych środków trwałych z pliku danych.csv wybierz pozycję **Importuj priorytetowe zasoby fizyczne**. W oknie dialogowym Eksploratora plików wybierz plik, .csv chcesz zaimportować, a następnie wybierz pozycję **Otwórz**. Identyfikatory fizycznych elementów zawartości z .csv zostaną dodane do listy.
4. Przejdź do **strony Wskaźniki zasad** w **programie Ustawienia**.
5. Na stronie **Wskaźniki zasad** przejdź do sekcji Wskaźniki dostępu fizycznego i zaznacz pole wyboru Dostęp fizyczny po zakończeniu lub nieudany dostęp do **poufnego zasobu**.
6. Wybierz **pozycję Zapisz,** aby skonfigurować i zakończyć działanie.

### <a name="delete-a-priority-physical-asset"></a>Usuwanie zasobu fizycznego priorytetu

Aby usunąć istniejący priorytet zasobu fizycznego, użyj kontrolek ustawień w rozwiązaniu do zarządzania ryzykiem niejawnego programu testów w p Centrum zgodności platformy Microsoft 365. Aby usunąć priorytet zasobu fizycznego, musisz być członkiem grupy ról Zarządzanie ryzykiem w niejawnym programie testów lub Administrator zarządzania ryzykiem w niejawnym programie testów.

> [!IMPORTANT]
> Usunięcie priorytetu fizycznego zasobu usuwa go z pamięci przez wszystkie aktywne zasady, do których został poprzednio dołączony. Alerty generowane przez działania skojarzone z zasobem fizycznym o priorytecie nie są usuwane.

Wykonaj następujące czynności, aby usunąć priorytet zasobu fizycznego:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do **strony Zarządzanie ryzykiem** w niejawnym programie testów i **wybierz pozycję** >  Ustawienia ryzyka niejawnego programu testówPriorność **fizycznych środków trwałych**.
2. Na stronie **Priorytet fizycznych środków** trwałych wybierz składnik majątku, który chcesz usunąć.
3. Wybierz **polecenie Usuń** w menu akcji, aby usunąć element zawartości.

## <a name="power-automate-flows-preview"></a>przepływy Power Automate (wersja zapoznawcza)

[Microsoft Power Automate](/power-automate/getting-started) to usługa przepływu pracy, która automatyzuje akcje między aplikacjami i usługami. Korzystając z przepływów z szablonów lub utworzonych ręcznie, można zautomatyzować typowe zadania skojarzone z tymi aplikacjami i usługami. Po włączeniu przepływów Power Automate do zarządzania ryzykiem w niejawnym programie testów można zautomatyzować ważne zadania dotyczące spraw i użytkowników. Możesz skonfigurować przepływy Power Automate pobierania informacji o użytkownikach, alertach i przypadku oraz udostępniania tych informacji uczestnikom projektu i innym aplikacjom, a także automatyzować działania w ramach zarządzania ryzykiem w ramach niejawnego programu testów, takie jak publikowanie notatek dotyczących sprawy. Power Automate przepływów mają zastosowanie do spraw i każdego użytkownika mającego zastosowanie do zasad.

Klienci z Microsoft 365 subskrypcji, które zawierają zarządzanie ryzykiem w niejawnym programie testów, nie potrzebują dodatkowych licencji Power Automate, aby korzystać z zalecanych szablonów zarządzania ryzykiem w ramach Power Automate niejawnego programu testów. Te szablony można dostosować, aby wspierały twoją organizację i zawierały podstawowe scenariusze zarządzania ryzykiem w niejawnym programie testów. Jeśli zdecydujesz się na korzystanie z funkcji premium Power Automate w tych szablonach, utwórz szablon niestandardowy przy użyciu łącznika zgodności usługi Microsoft 365 lub użyj szablonów programu Power Automate dla innych obszarów zgodności w programie Microsoft 365, może być Power Automate więcej licencji.

Następujące szablony Power Automate klientów w celu obsługi automatyzacji procesów w przypadku użytkowników i spraw zarządzania ryzykiem w niejawnym programie testów:

- Powiadamianie użytkowników o dodaniu do zasad ryzyka niejawnego programu testów **: Ten** szablon jest dla organizacji, które mają wewnętrzne zasady, prywatność lub wymagania prawne, o których użytkownicy muszą być powiadamiani, gdy podlegają zasadom zarządzania ryzykiem w ramach niejawnego programu testów. Po skonfigurowaniu i wybraniu tego przepływu dla użytkownika na stronie Użytkownicy  użytkownicy i ich menedżerowie są wysyłani wiadomości e-mail, gdy ten użytkownik zostanie dodany do zasad zarządzania ryzykiem w niejawnym programie testów. Ten szablon obsługuje również aktualizowanie listy wiadomości SharePoint hostowanej w witrynie usługi SharePoint w celu śledzenia komunikat z powiadomieniem takich jak data/godzina i adresat wiadomości. Jeśli wybrano anonimizacji użytkowników w ustawieniach **prywatności,** przepływy utworzone za pomocą tego szablonu nie będą działać zgodnie z zamierzonymi zasadami zachowania prywatności użytkowników. Power Automate korzystających z tego szablonu są dostępne na **pulpicie nawigacyjnym Użytkownicy**.
- Żądanie od **kadry** lub firmy informacji o użytkowniku w przypadku ryzyka w ramach niejawnego programu testów: Podczas prowadzenia działań w związku ze sprawą analitycy i osoby w związku z ryzykiem w ramach niejawnego programu testów mogą musieć skonsultować się z kadrą lub innymi uczestnikami projektu w celu zrozumienia kontekstu działań dotyczących sprawy. Gdy ten przepływ zostanie skonfigurowany i wybrany do przypadku, analitycy i osoby w jego przypadku wysyłają wiadomości e-mail do kadr i biznesowych uczestników projektu skonfigurowanych dla tego przepływu. Do każdego adresata jest wysyłana wiadomość ze wstępnie skonfigurowanymi lub dostosowywalnymi opcjami odpowiedzi. Gdy adresaci wybierzą opcję odpowiedzi, odpowiedź jest rejestrowana jako notatka sprawy i zawiera informacje o adresacie oraz dacie/godzinie. Jeśli wybrano anonimizacji użytkowników w ustawieniach **prywatności,** przepływy utworzone za pomocą tego szablonu nie będą działać zgodnie z zamierzonymi zasadami zachowania prywatności użytkowników. Power Automate korzystających z tego szablonu są dostępne na pulpicie **nawigacyjnym Sprawy**.
- **Powiadamianie menedżera, gdy użytkownik ma alert o czynniku ryzyka** w niejawnym programie testów: W niektórych organizacjach może być konieczne powiadomienie o natychmiastowym zarządzaniu, gdy użytkownik ma alert o zarządzaniu ryzykiem w niejawnym programie testów. Po skonfigurowaniu i wybraniu tego przepływu menedżer sprawy wysyła do użytkownika wiadomość e-mail z następującymi informacjami o wszystkich alertach dotyczących sprawy:
    - Zasady obowiązujące dla alertu
    - Data/godzina alertu
    - Poziom ważności alertu

    Przepływ automatycznie aktualizuje notatki dotyczące sprawy, że wiadomość została wysłana i że przepływ został aktywowany. Jeśli wybrano anonimizacji użytkowników w ustawieniach **prywatności,** przepływy utworzone za pomocą tego szablonu nie będą działać zgodnie z zamierzonymi zasadami zachowania prywatności użytkowników. Power Automate korzystających z tego szablonu są dostępne na pulpicie **nawigacyjnym Sprawy**.
- **Tworzenie rekordu dla przypadku ryzyka niejawnego programu testów w serwisie ServiceNow**: Ten szablon jest dla organizacji, które chcą używać swojego rozwiązania ServiceNow do śledzenia spraw zarządzania ryzykiem w niejawnym programie testów.  W takim przypadku analitycy i testerzy ryzyka w niejawnym programie testów mogą utworzyć rekord dla sprawy w serwisie ServiceNow. Ten szablon można dostosować w celu wypełnienia wybranych pól w polu ServiceNow zgodnie z wymaganiami Twojej organizacji. Power Automate korzystających z tego szablonu są dostępne na pulpicie **nawigacyjnym Sprawy**. Aby uzyskać więcej informacji na temat dostępnych pól ServiceNow, zobacz artykuł informacyjny do [łącznika ServiceNow](/connectors/service-now/) .

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Tworzenie przepływu Power Automate szablonu zarządzania ryzykiem w niejawnym programie testów

Aby utworzyć przepływ Power Automate na podstawie zalecanego szablonu zarządzania ryzykiem w niejawnym programie testów, użyj kontrolek ustawień w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów w  programie Centrum zgodności platformy Microsoft 365 lub opcji Zarządzaj przepływami  Power Automate z automatyzowania   podczas pracy bezpośrednio na pulpitach **nawigacyjnych Sprawy** lub **Użytkownicy**.

Aby utworzyć przepływ Power Automate w obszarze ustawień, musisz być członkiem grupy ról Zarządzanie ryzykiem w niejawnym programie testów lub Administratorem zarządzania ryzykiem w niejawnym *programie testów*. Aby utworzyć przepływ Power Automate **przy użyciu opcji** Zarządzaj przepływami Power Automate, musisz być członkiem co najmniej jednej grupy ról zarządzania ryzykiem w niejawnym programie testów.

Wykonaj poniższe czynności, aby utworzyć przepływ Power Automate na podstawie zalecanego szablonu zarządzania ryzykiem w niejawnym programie testów:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do **strony Zarządzanie ryzykiem** w niejawnym programie testów i **wybierz pozycję** >  Ustawienia ryzyka niejawnego programu testów **Power Automate przepływy**. Dostęp do stron spraw lub pulpitów nawigacyjnych użytkownicy można również uzyskać, wybierając opcję  **AutomateManage** >  **Power Automate przepływów**.
2. Na stronie **Power Automate** wybierz zalecany szablon z sekcji Szablony zarządzania ryzykiem w niejawnym programie testów, które mogą Ci się spodobać.
3. Przepływ zawiera listę osadzonych połączeń wymaganych dla przepływu i zanotuje, czy stan połączenia jest dostępny. W razie potrzeby zaktualizuj wszystkie połączenia, które nie są wyświetlane jako dostępne. Wybierz **pozycję Kontynuuj**.
4. Domyślnie zalecane przepływy są wstępnie skonfigurowane z zalecanym zarządzaniem ryzykiem niejawnego programu testów i polami danych usług Microsoft 365 wymaganymi do wykonania przydzielonego zadania w przepływie. W razie potrzeby dostosuj składniki przepływu, używając kontrolki Pokaż zaawansowane opcje i konfigurując dostępne właściwości składnika przepływu.
5. W razie potrzeby dodaj inne kroki do przepływu, wybierając **przycisk Nowy** krok. W większości przypadków nie powinno to być potrzebne w przypadku zalecanych szablonów domyślnych.
6. Wybierz **pozycję Zapisz wersje** robocze, aby zapisać przepływ do dalszej  konfiguracji, lub pozycję Zapisz, aby ukończyć konfigurację przepływu.
7. Wybierz **pozycję Zamknij**, aby wrócić **do Power Automate przepływu** pracy. Nowy szablon będzie wymieniony jako przepływ na kartach Moje  przepływy i automatycznie dostępny z kontrolki listy rozwijanej **Automate** podczas pracy ze sprawami zarządzania ryzykiem w niejawnym programie testów dla użytkownika tworzącego przepływ.

> [!IMPORTANT]
> Jeśli inni użytkownicy w organizacji potrzebują dostępu do przepływu, przepływ musi być udostępniony.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Tworzenie niestandardowego przepływu Power Automate zarządzania ryzykiem w niejawnym programie testów

Niektóre procesy i przepływy pracy w Organizacji mogą być spoza zalecanych szablonów przepływów zarządzania ryzykiem niejawnego programu testów i może być konieczne utworzenie niestandardowych przepływów Power Automate dla obszarów zarządzania ryzykiem w niejawnym programie testów. Power Automate są elastyczne i obsługują rozbudowane dostosowania, ale istnieją czynności, które należy podjąć, aby zintegrować je z funkcjami zarządzania ryzykiem w niejawnym programie testów.

Wykonaj poniższe czynności, aby utworzyć niestandardowy szablon Power Automate do zarządzania ryzykiem w niejawnym programie testów:

1. **Sprawdź swoją Power Automate** przepływu pracy: aby utworzyć niestandardowe przepływy Power Automate, które korzystają z wyzwalaczy zarządzania ryzykiem w niejawnym programie testów, potrzebujesz licencji Power Automate grupy. Szablony przepływu zalecanego przepływu zarządzania ryzykiem w niejawnym programie testów nie wymagają dodatkowego licencjonowania i są uwzględnione w ramach licencji na zarządzanie ryzykiem w niejawnym programie testów.
2. **Tworzenie zautomatyzowanego przepływu**: utwórz przepływ, który wykona jedno lub więcej zadań po jego wyzwoleniu przez zdarzenie zarządzania ryzykiem w niejawnym programie testów. Aby uzyskać szczegółowe informacje na temat tworzenia zautomatyzowanego przepływu, zobacz Tworzenie [przepływu w Power Automate](/power-automate/get-started-logic-flow).
3. **Wybierz łącznik Microsoft 365 zgodności**: Wyszukaj i wybierz łącznik zgodności Microsoft 365 zgodności. Ten łącznik umożliwia wyzwalanie i akcje zarządzania ryzykiem w ramach niejawnego programu testów. Aby uzyskać więcej informacji o łącznikach, zobacz artykuł z omówieniem [odwoływać się do łączników](/connectors/connector-reference/) .
4. **Wybierz wyzwalacze zarządzania ryzykiem niejawnego** programu testów dla swojego przepływu: Zarządzanie ryzykiem niejawnego programu testów ma dwa wyzwalacze dostępne dla niestandardowych przepływów Power Automate informacji:
    - **W przypadku wybranego przypadku zarządzania ryzykiem w niejawnym programie testów**: Przepływy z tym wyzwalaczem można wybrać na stronie pulpitu nawigacyjnego przypadki zarządzania ryzykiem w niejawnym programie testów.
    - **Dla wybranego użytkownika do zarządzania ryzykiem w niejawnym programie** testów: Przepływy z tym wyzwalaczem można wybrać na stronie pulpitu nawigacyjnego Użytkowników zarządzania ryzykiem w niejawnym programie testów.
5. Wybierz dla swojego przepływu działania związane z zarządzaniem ryzykiem w ramach niejawnego programu testów: Możesz wybrać spośród kilku akcji zarządzania ryzykiem w ramach niejawnego programu testów, które będą obejmować Twój niestandardowy przepływ:
    - Otrzymuj alerty dotyczące zarządzania ryzykiem w niejawnym programie testów
    - Uzyskiwanie sprawy związanej z zarządzaniem ryzykiem w niejawnym programie testów
    - Pobierz użytkownika do zarządzania ryzykiem w niejawnym programie testów
    - Uzyskiwanie alertów dotyczących zarządzania ryzykiem w niejawnym programie testów dotyczących sprawy
    - Dodawanie notatki dotyczącej sprawy związanej z zarządzaniem ryzykiem w niejawnym programie testów

### <a name="share-a-power-automate-flow"></a>Udostępnianie przepływu Power Automate przepływu pracy

Domyślnie przepływy Power Automate utworzone przez użytkownika są dostępne tylko dla tego użytkownika. Aby inni użytkownicy zarządzający ryzykiem w niejawnym programie testów mieli dostęp do przepływu i korzystali z niego, jego przepływ musi zostać udostępniony przez twórcę przepływu. Aby udostępnić przepływ, użyj kontrolek ustawień w rozwiązaniu do zarządzania  ryzykiem niejawnego programu testów w programie Centrum zgodności platformy Microsoft 365 lub opcji Zarządzaj przepływami Power Automate z kontrolki Automatyzuj podczas pracy bezpośrednio na stronach pulpitu nawigacyjnego Sprawy  lub Użytkownicy.  Po udostępnieniu przepływu wszystkie osoby, którym został on udostępniony, mogą uzyskać dostęp do przepływu na liście rozwijanej kontrolki **Automate** w pulpitach nawigacyjnych **sprawy i użytkowników**.

Aby udostępnić przepływ Power Automate w obszarze ustawień, musisz być członkiem grupy ról Zarządzanie ryzykiem w niejawnym  programie testów lub Administratorem *zarządzania ryzykiem w* niejawnym programie testów. Aby udostępnić przepływ Power Automate **przy użyciu opcji** Zarządzaj przepływami Power Automate, musisz być członkiem co najmniej jednej grupy ról zarządzania ryzykiem w niejawnym programie testów.

Wykonaj następujące czynności, aby udostępnić przepływ Power Automate przepływ pracy:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do **strony Zarządzanie ryzykiem** w niejawnym programie testów i **wybierz pozycję** >  Ustawienia ryzyka niejawnego programu testów **Power Automate przepływy**. Dostęp do stron spraw lub pulpitów nawigacyjnych użytkownicy można również uzyskać, wybierając opcję  **AutomateManage** >  **Power Automate przepływów**.
2. Na stronie **Power Automate** wybierz **kartę Moje** przepływy lub **Przepływy** zespołu.
3. Wybierz przepływ, który chcesz udostępnić, a następnie wybierz **pozycję Udostępnij** z menu opcji przepływu.
4. Na stronie udostępniania przepływu wprowadź nazwę użytkownika lub grupy, którą chcesz dodać jako właściciela przepływu.
5. W **oknie dialogowym Używane** połączenie wybierz przycisk **OK** , aby potwierdzić, że dodany użytkownik lub grupa będzie mieć pełny dostęp do przepływu.

### <a name="edit-a-power-automate-flow"></a>Edytowanie przepływu Power Automate danych

Aby edytować przepływ, użyj kontrolek ustawień w rozwiązaniu do zarządzania ryzykiem  niejawnego programu testów w programie Centrum zgodności platformy Microsoft 365 lub opcji Zarządzaj przepływami **Power Automate** z kontrolki Automatyzuj podczas pracy bezpośrednio na pulpitach nawigacyjnych  Sprawy lub **Użytkownicy.**

Aby edytować przepływ Power Automate w obszarze ustawień, musisz być członkiem grupy ról Zarządzanie ryzykiem w niejawnym programie testów lub Administratorem zarządzania *ryzykiem w niejawnym* programie testów. Aby edytować przepływ Power Automate za pomocą opcji Zarządzaj przepływami  Power Automate, musisz być członkiem co najmniej jednej grupy ról zarządzania ryzykiem w niejawnym programie testów.

Aby edytować przepływ pracy, wykonaj Power Automate czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do **strony Zarządzanie ryzykiem** w niejawnym programie testów i **wybierz pozycję** >  Ustawienia ryzyka niejawnego programu testów **Power Automate przepływy**. Dostęp do stron spraw lub pulpitów nawigacyjnych użytkownicy można również uzyskać, wybierając opcję  **AutomateManage** >  **Power Automate przepływów**.
2. Na stronie **Power Automate** przepływów wybierz przepływ do edycji, a następnie wybierz pozycję **Edytuj** z menu sterowania przepływem.
3. Wybierz **wielokropek** >  **Ustawienia** aby  >  zmienić ustawienie składnika przepływu lub wielokropekDelete, aby usunąć składnik przepływu.
4. Wybierz **pozycję Zapisz** , a następnie zamknij **,** aby zakończyć edytowanie przepływu.

### <a name="delete-a-power-automate-flow"></a>Usuwanie przepływu Power Automate danych

Aby usunąć przepływ, użyj kontrolek ustawień w rozwiązaniu do zarządzania ryzykiem  niejawnego programu testów w programie Centrum zgodności platformy Microsoft 365 lub opcji Zarządzaj przepływami **Power Automate** z kontrolki Automatyzuj podczas pracy bezpośrednio na pulpitach nawigacyjnych  Sprawy lub **Użytkownicy.** Usunięcie przepływu powoduje usunięcie go jako opcji dla wszystkich użytkowników.

Aby usunąć przepływ Power Automate w obszarze ustawień, musisz być członkiem grupy ról Zarządzanie ryzykiem niejawnego programu testów lub Administrator zarządzania *ryzykiem w* niejawnym programie testów. Aby usunąć przepływ Power Automate **przy użyciu opcji** Zarządzaj przepływami Power Automate, musisz być członkiem co najmniej jednej grupy ról zarządzania ryzykiem w niejawnym programie testów.

Aby usunąć przepływ danych, wykonaj Power Automate czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do **strony Zarządzanie ryzykiem** w niejawnym programie testów i **wybierz pozycję** >  Ustawienia ryzyka niejawnego programu testów **Power Automate przepływy**. Dostęp do stron spraw lub pulpitów nawigacyjnych użytkownicy można również uzyskać, wybierając opcję  **AutomateManage** >  **Power Automate przepływów**.
2. Na stronie **Power Automate** przepływów wybierz przepływ do usunięcia, a następnie wybierz pozycję **Usuń** z menu sterowania przepływem.
3. W oknie dialogowym potwierdzenia usunięcia wybierz pozycję **Usuń** , aby usunąć przepływ, lub pozycję **Anuluj** , aby zamknąć akcję usunięcia.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (wersja zapoznawcza)

Analitycy zgodności i osoby wiadące mogą łatwo Microsoft Teams do współpracy nad sprawami zarządzania ryzykiem w ramach niejawnego programu testów. Mogą one koordynować działania innych uczestników projektu i komunikować się z Microsoft Teams w celu:

- Koordynowanie i przeglądanie działań w zakresie odpowiedzi w przypadku spraw w Teams kanałach
- Bezpieczne udostępnianie i przechowywanie plików i dowodów związanych z poszczególnymi sprawami
- Śledzenie i przeglądanie działań reakcji analityków i użytkowników

Po Microsoft Teams włączono zarządzanie ryzykiem w niejawnym programie testów, za każdym Microsoft Teams po potwierdzeniu alertu i utworzeniu sprawy jest tworzony dedykowany zespół ds. ryzyka. Domyślnie zespół automatycznie obejmuje wszystkich członków grup ról Zarządzanie ryzykiem niejawnego programu testów *,* Analityków zarządzania ryzykiem w niejawnym programie testów i Członków grupy ról zarządzanie ryzykiem w niejawnym programie testów (do 100 początkowych użytkowników). Kolejnych współautorów organizacji można dodać do zespołu po jego utworzeniu i, w razie potrzeby. W przypadku istniejących spraw utworzonych przed Microsoft Teams, analitycy i osoby chłonące mogą zdecydować się na utworzenie nowego zespołu Microsoft Teams w razie potrzeby podczas pracy nad sprawami.  Po rozwiązaniu skojarzonej sprawy w zarządzaniu ryzykiem w niejawnym programie testów zespół jest automatycznie archiwizowany (przenoszony do ukrytego i tylko do odczytu).

Aby uzyskać więcej informacji na temat korzystania z zespołów i Microsoft Teams w aplikacji Microsoft Teams, zobacz Omówienie [zespołów](/MicrosoftTeams/teams-channels-overview) i kanałów w Microsoft Teams.

Włączanie Microsoft Teams spraw jest szybkie i łatwe w konfiguracji. Aby włączyć Microsoft Teams do zarządzania ryzykiem w niejawnym programie testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie ryzykiem w niejawnym **programie** >  **testówU** ds. ryzyka.
2. Wybierz **Microsoft Teams strony**.
3. Włącz Microsoft Teams na rzecz zarządzania ryzykiem w niejawnym programie testów.
4. Wybierz **pozycję Zapisz,** aby skonfigurować i zakończyć działanie.

![Zarządzanie ryzykiem w niejawnym programie testów Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Tworzenie zespołu Microsoft Teams istniejących spraw

Jeśli włączysz Microsoft Teams do zarządzania ryzykiem w ramach niejawnego programu testów po istniejących przypadkach, w razie potrzeby musisz ręcznie utworzyć zespół dla każdej sprawy. Po włączeniu Microsoft Teams technicznej w ustawieniach zarządzania ryzykiem w niejawnym programie testów nowe przypadki będą automatycznie tworzyły nowy Microsoft Teams zespołu.

Użytkownicy muszą mieć uprawnienia do tworzenia Microsoft 365 w organizacji, aby utworzyć nowy Microsoft Teams zespołu w danej sprawie. Aby uzyskać więcej informacji na temat zarządzania uprawnieniami do grup Microsoft 365, zobacz Zarządzanie tym, kto może [tworzyć Microsoft 365 grupy](../solutions/manage-creation-of-groups.md).

Aby utworzyć zespół dla sprawy, użyj kontrolki Utwórz zespół Microsoft podczas pracy bezpośrednio w istniejącej sprawie. Wykonaj następujące czynności, aby utworzyć nowy zespół:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do tematu Zarządzanie ryzykiem w ramach niejawnego **programu** >  testówDaty i wybierz istniejącą sprawę.
2. W menu akcji sprawy wybierz polecenie **Utwórz zespół Microsoft**.
3. W **polu Nazwa** zespołu wprowadź nazwę nowego Microsoft Teams zespołu.
4. Wybierz **pozycję Utwórz zespół Microsoft,** a następnie wybierz **pozycję Zamknij**.

W zależności od liczby użytkowników przypisanych do grup ról zarządzania ryzykiem w niejawnym programie testów może potrwać 15 minut, a dodanie wszystkich członków zespołu analityków i analityków do zespołu Microsoft Teams ds. sprawy może potrwać 15 minut.

## <a name="analytics"></a>Analiza

Analiza ryzyka w niejawnym programie testów umożliwia przeprowadzenie oceny potencjalnych czynników ryzyka niejawnego programu testów w organizacji bez konfigurowania żadnych zasad ryzyka niejawnego programu testów. Ocena ta może ułatwić organizacji zidentyfikowanie potencjalnych obszarów o wyższym poziomie ryzyka użytkownika oraz określenie typu i zakresu zasad zarządzania ryzykiem niejawnego programu testów, które można rozważyć podczas konfigurowania. Skanowania analizy mają następujące zalety dla twojej organizacji:

- Łatwa konfiguracja: Aby rozpocząć pracę ze skanami analizy, możesz wybrać pozycję Uruchom skanowanie po  >  wyświetleniu monitu z zaleceniem do analizy lub przejść do ustawień ryzyka niejawnego programu testówAnalytics i włączyć analizę.
- Prywatność według projektu: Wyniki skanowania i szczegółowe informacje są zwracane jako zagregowane i zanonimizowane działania użytkowników, a poszczególne nazwy użytkowników nie są identyfikowalne przez recenzentów.
- Zrozumienie potencjalnych czynników ryzyka dzięki skonsolidowanym analizom: wyniki skanowania mogą ułatwić szybkie zidentyfikowanie obszarów potencjalnego ryzyka dla użytkowników oraz zasady, które najlepiej byłoby zminimalizować te zagrożenia.

Obejrzyj klip [wideo z analizą ryzyka](https://www.youtube.com/watch?v=5c0P5MCXNXk) w ramach niejawnego programu testów, aby dowiedzieć się, jak analiza może przyspieszyć identyfikację potencjalnych czynników ryzyka w niejawnym programie testów i pomóc w szybkich działaniach.

Analizy pod poszukiwaniu zdarzeń aktywności ryzyka z kilku źródeł ułatwiają zidentyfikowanie potencjalnych obszarów ryzyka. W zależności od bieżącej konfiguracji analiza wyszukuje działania o kwalifikowanym ryzyku w następujących obszarach:

- **Microsoft 365 dziennikach inspekcji**: Są one uwzględniane we wszystkich skanach i są podstawowym źródłem identyfikacji większości potencjalnie ryzykownych działań.
- **Exchange Online**: Uwzględniane we wszystkich skanach aktywność Exchange Online pomaga identyfikować działania, w przypadku których dane w załącznikach są e-mailowane do zewnętrznych kontaktów lub usług.
- **Azure Active Directory**: Uwzględniane we wszystkich skanach historia Azure Active Directory pomaga identyfikować ryzykowne działania związane z użytkownikami z usuniętymi kontami użytkowników.
- **Microsoft 365 danych HR**: Jeśli łącznik kadr jest skonfigurowany, zdarzenia łącznika kadr pomagają identyfikować ryzykowne działania skojarzone z użytkownikami, którzy mają ponowne przypisanie lub zbliżające się daty zakończenia.

Analizy analiz na podstawie skanów są oparte na takich samych sygnałach aktywności ryzyka, jakie zostały użyte przez zasady zarządzania ryzykiem w ramach niejawnego programu testów i raportują wyniki na podstawie zarówno pojedynczych, jak i sekwencji działań użytkownika. Jednak wyniki oceniania ryzyka dla analiz są oparte na maksymalnie 10-dniowej aktywności, natomiast zasady ryzyka niejawnego programu testów korzystają z codziennej aktywności na podstawie szczegółowych informacji. Po włączeniu i uruchomieniu analizy w organizacji po raz pierwszy zobaczysz wyniki skanowania dla jednego dnia. Jeśli pozostawisz włączoną analizę, zobaczysz wyniki każdego dziennego skanowania dodane do raportów szczegółowych dla maksymalnego zakresu działań z poprzednich 10 dni.

### <a name="enable-analytics-and-start-your-scan"></a>Włączanie analizy i rozpoczynanie skanowania

Aby włączyć analizę ryzyka niejawnego programu testów, musisz być członkiem grupy ról Zarządzanie ryzykiem niejawnego programu testów *, administratora* zarządzania ryzykiem w niejawnym programie testów *Microsoft 365* grupy ról administratora globalnego.
Wykonaj poniższe czynności, aby włączyć analizę ryzyka niejawnego programu testów:

1. W centrum [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) do tematu Zarządzanie **ryzykiem w niejawnym programie testów**.
2. Wybierz **pozycję Uruchom skanowanie** na karcie Skanowanie w poszukiwaniu czynników ryzyka w niejawnym programie **testów** na karcie Przegląd zarządzania ryzykiem w niejawnym **programie** testów. Włączy to skanowanie analiz dla organizacji. Możesz również włączyć skanowanie  >  w organizacji, przechodząc do ustawień ryzyka niejawnego programu testówAnalytics i włączając skanowanie aktywności użytkowników w dzierżawie, aby zidentyfikować **potencjalne zagrożenia w niejawnym programie testów**.
3. W **okienku szczegółów analizy** wybierz pozycję **Uruchom skanowanie** , aby rozpocząć skanowanie dla organizacji. Wyniki analizy mogą zająć do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przejrzenia.

![Ustawienia analizy ryzyka niejawnego programu testów.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Wyświetlanie szczegółowych informacji z analiz i tworzenie nowych zasad

Po zakończeniu pierwszego skanowania analizy dla organizacji członkowie grupy ról Administrator zarządzania ryzykiem  w ramach niejawnego programu testów będą automatycznie otrzymywać powiadomienia e-mail i mogą wyświetlać początkowe analizy i zalecenia dotyczące potencjalnie ryzykownych działań ze strony użytkowników. Codzienne skanowanie jest kontynuowane, chyba że wyłączysz analizę dla swojej organizacji. Powiadomienia e-mail dla administratorów są udostępniane dla każdej z trzech kategorii w zakresie na analizy (wycieki danych, kradzieże i exszybki) po pierwszym wystąpieniu aktywności w organizacji. Powiadomienia e-mail nie są wysyłane do administratorów w celu wykrywania działań następczych wynikających z codziennych skanów.  >  Jeśli analiza w zarządzaniu ryzykiem w ramach niejawnego programu testów **Ustawienia** >  **Analytics** zostanie wyłączona, a następnie ponownie włączona w organizacji, automatyczne powiadomienia e-mail zostaną zresetowane, a  wiadomości e-mail będą wysyłane do członków grupy ról Administrator zarządzania ryzykiem w ramach niejawnego programu testów, aby uzyskać nowe informacje dotyczące skanowania.

Aby wyświetlić potencjalne zagrożenia dla organizacji, przejdź do karty **Przegląd** i wybierz pozycję **Wyświetl** wyniki na karcie **Analiza** ryzyka niejawnego programu testów. Jeśli skanowanie w twojej organizacji nie jest ukończone, zostanie wyświetlony komunikat informujący, że skanowanie jest nadal aktywne.

![Karta gotowa do raportu analizy ryzyka niejawnego programu testów.](../media/insider-risk-analytics-ready-card.png)

W przypadku ukończonych skanów zobaczysz potencjalne ryzyko wykryte w Organizacji oraz szczegółowe informacje i zalecenia dotyczące rozwiązania tego ryzyka. Określone czynniki ryzyka i szczegółowe informacje są uwzględniane w raportach pogrupowanych według obszaru, łącznej liczbie użytkowników z określonymi zagrożeniami, procentach użytkowników z potencjalnie ryzykownym działaniami i zalecanych zasadach ryzyka w ramach niejawnego programu testów w celu zmniejszenia tego ryzyka. Raporty są następujące:

- **Wycieki danych:** Działania wszystkich użytkowników, które mogą obejmować przypadkowe oversharing informacji poza twoją organizację lub wycieki danych przez użytkowników ze złośliwą intencją.
- **Analiza kradzieży** danych: działania służące do odsuania użytkowników lub użytkowników z usuniętymi kontami usługi Azure Active Directory, które mogą obejmować ryzykowne udostępnianie informacji spoza organizacji lub kradzież danych przez użytkowników ze złośliwą intencją.
- **Najważniejsze szczegółowe informacje**: działania wszystkich użytkowników, którzy mogą obejmować udostępnianie danych spoza twojej organizacji.

![Raport przeglądu analizy ryzyka niejawnego programu testów.](../media/insider-risk-analytics-overview.png)

Aby wyświetlić więcej informacji na temat szczegółowej informacji, wybierz pozycję **Wyświetl szczegóły** , aby wyświetlić okienko szczegółów szczegółowych informacji. Okienko szczegółów zawiera pełne wyniki szczegółowej analizy, zalecenie dotyczące zasad ryzyka niejawnego programu testów i przycisk Utwórz zasady, który pozwala szybko utworzyć zalecane zasady. Wybranie przycisku Utwórz zasady spowoduje otworzynie kreatora zasad i automatyczne wybranie szablonu zalecanych zasad dotyczących danej szczegółowej informacji. Jeśli na przykład analiza ma na celu aktywność wycieków danych, szablon zasad  Ogólne wycieki danych zostanie wstępnie wybrany w kreatorze zasad.

![Raport szczegółów analizy ryzyka niejawnego programu testów.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Wyłączanie analizy

Aby wyłączyć analizę ryzyka w niejawnym programie testów, musisz być członkiem grupy ról Zarządzanie ryzykiem niejawnego programu testów *, administratora* zarządzania ryzykiem niejawnego programu testów Microsoft 365 *administratorem globalnym*. Po wyłączeniu analizy raporty szczegółowe analizy pozostaną statyczne i nie będą aktualizowane w przypadku nowych zagrożeń.

Wykonaj następujące czynności, aby wyłączyć analizę ryzyka niejawnego programu testów:

1. W centrum [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) do tematu Zarządzanie **ryzykiem w niejawnym programie testów**.
2. Wybierz **pozycję Ustawienia ryzyka niejawnego programu** **testówAnalytics** > .
3. Na stronie **Analiza** wyłącz skanowanie aktywności użytkowników dzierżawy, **aby zidentyfikować potencjalne zagrożenia w niejawnym programie testów**.

## <a name="admin-notifications"></a>Powiadomienia administratora

Powiadomienia administratora automatycznie wysyłają wiadomości e-mail z powiadomieniem do wybranych grup ról zarządzania ryzykiem w niejawnym programie testów. Możesz włączyć powiadomienia i przypisać grupy ról, które będą otrzymywać powiadomienia dla następujących scenariuszy:

- Wyślij powiadomienie e-mail po wygenerowaniu pierwszego alertu dla nowych zasad. W przypadku alertów i powiadomień o nowych terminach zasady są sprawdzane co 24 godziny, a powiadomienia dotyczące kolejnych alertów dotyczących zasad nie są wysyłane.
- Wysyłaj codzienną wiadomość e-mail, gdy są generowane nowe alerty o wysokim poziomie ważności. Zasady są sprawdzane dla alertów o wysokim poziomie ważności co 24 godziny.
- Wysyłanie cotygodniowych zasad podsumowania wiadomości e-mail, które mają nierozpoznane ostrzeżenia

Jeśli włączono analizę ryzyka w ramach niejawnego programu testów dla organizacji,  członkowie grupy ról Administrator zarządzania ryzykiem w ramach niejawnego programu testów automatycznie otrzymają powiadomienie e-mail o początkowych informacjach analitycznych dotyczących wycieków danych, kradzieży i działań kradzieży.

Jeśli wolisz wyłączyć powiadomienia administratora i analizy, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie ryzykiem w niejawnym **programie** >  **testówU** ds. ryzyka.
2. Wybierz stronę **Powiadomienia administratora** .
3. Wyczyść pole wyboru następujących opcji, jeśli mają zastosowanie:
    - **Wysyłanie powiadomienia e-mail po wygenerowaniu pierwszego alertu dla nowych zasad**
    - **Wysyłanie wiadomości e-mail z powiadomieniem, gdy w analizie są dostępne nowe szczegółowe informacje**
    - **Wysyłanie powiadomienia e-mail, gdy analiza jest wyłączona**

4. Wybierz **pozycję Zapisz,** aby skonfigurować i zakończyć działanie.
