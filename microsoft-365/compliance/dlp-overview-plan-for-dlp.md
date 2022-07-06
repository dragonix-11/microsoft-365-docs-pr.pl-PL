---
title: Zaplanuj ochronę przed utratą danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Omówienie procesu planowania zapobiegania utracie danych
ms.openlocfilehash: afda017b2cc627876134888a83f70e9464aba2c8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634450"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Planowanie zapobiegania utracie danych (DLP)

Każda organizacja będzie inaczej planować i implementować zapobieganie utracie danych, ponieważ potrzeby biznesowe, cele, zasoby i sytuacja każdej organizacji są dla nich unikatowe. Istnieją jednak elementy, które są wspólne dla wszystkich pomyślnych implementacji DLP. W tym artykule przedstawiono najlepsze rozwiązania, które są używane przez organizacje w planowaniu DLP.

## <a name="multiple-starting-points"></a>Wiele punktów początkowych

Wiele organizacji decyduje się na wdrożenie DLP w celu zachowania zgodności z różnymi przepisami rządowymi lub branżowymi. Na przykład ogólne rozporządzenie o ochronie danych (RODO) Unii Europejskiej lub ustawę o przenośności i odpowiedzialności ubezpieczeń zdrowotnych (HIPAA) lub kalifornijską ustawę o ochronie prywatności konsumentów (CCPA). Wdrażają również ochronę przed utratą danych, aby chronić swoją własność intelektualną. Ale miejsce początkowe i ostateczny cel podróży DLP różnią się. 

Organizacje mogą rozpocząć swoją podróż DLP:

- z poziomu platformy, na przykład chcesz chronić informacje w wiadomościach na czacie i kanale w usłudze Teams lub na urządzeniach Windows 10
- znajomość informacji poufnych, które chcą nadać priorytet ochronie, na przykład dokumentacji służby zdrowia, i przejście bezpośrednio do definiowania zasad ich ochrony
- nie wiedząc, czym są ich poufne informacje, gdzie to jest i kto robi to, co z nim zrobić, aby zacząć od odkrycia i kategoryzacji i przyjąć bardziej metodyczne podejście
- nie wiedząc, czym są ich poufne informacje, gdzie są lub kto z nimi robi, ale przejdą od razu do definiowania zasad i wykorzystywania tych wyników jako miejsca początkowego, a następnie uściślają swoją politykę stamtąd
- wiedząc, że muszą wdrożyć pełny stos Microsoft Purview Information Protection i dlatego zamierzają przyjąć długoterminowe, metodyczne podejście

To tylko kilka przykładów sposobu, w jaki klienci mogą podejść do DLP i nie ma znaczenia, od czego zaczynasz, DLP jest wystarczająco elastyczna, aby pomieścić różne rodzaje podróży ochrony informacji od początku do w pełni zrealizowanej strategii zapobiegania utracie danych. 

## <a name="overview-of-planning-process"></a>Omówienie procesu planowania

Artykuł [Dowiedz się więcej o Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) wprowadza trzy różne aspekty [procesu planowania DLP](dlp-learn-about-dlp.md#plan-for-dlp). Więcej szczegółów znajdziesz tutaj na temat elementów, które są wspólne dla wszystkich planów DLP.

### <a name="identify-stakeholders"></a>Identyfikowanie uczestników projektu

Po zaimplementowaniu zasady DLP mogą być stosowane w dużych częściach organizacji. IT nie może samodzielnie opracować szerokiego planu bez negatywnych konsekwencji. Należy zidentyfikować osoby biorące udział w projekcie, które mogą:

- opisz przepisy, przepisy i standardy branżowe, których organizacja podlega
- kategorie elementów poufnych, które mają być chronione
- procesów biznesowych, w których są one używane
- ryzykowne zachowanie, które powinno być ograniczone
- priorytetyzowania, które dane powinny być chronione w pierwszej kolejności w oparciu o poufność elementów i związane z tym ryzyko
- opis procesu przeglądu i korygowania zdarzeń zgodności zasad DLP 
 
Ogólnie rzecz biorąc, te potrzeby zwykle obejmują 85% ochronę przepisów i zgodności oraz 15% ochronę własności intelektualnej. Poniżej przedstawiono kilka sugestii dotyczących ról do uwzględnienia w procesie planowania:

- Urzędnicy ds. przepisów i zgodności
- Dyrektor ds. ryzyka
- Urzędnicy prawni
- Funkcjonariusze ds. zabezpieczeń i zgodności
- Właściciele firm dla elementów danych
- Użytkownicy biznesowi
- IT

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Opis kategorii informacji poufnych w celu ochrony

Następnie uczestnicy projektu opisują kategorie poufnych informacji, które mają być chronione, oraz proces biznesowy, w którym są używane. Na przykład DLP definiuje następujące kategorie:

- Finansowych 
- Informacje medyczne i zdrowotne
- Prywatność
- Niestandardowe

Osoby biorące udział w projekcie mogą zidentyfikować poufne informacje jako "Jesteśmy podmiotem przetwarzającym dane, dlatego musimy wdrożyć ochronę prywatności w zakresie informacji o podmiotach danych i informacji finansowych".

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Ustawianie celów i strategii

Po zidentyfikowaniu uczestników projektu i określeniu, które poufne informacje wymagają ochrony i gdzie są używane, uczestnicy projektu mogą określić swoje cele w zakresie ochrony, a dział IT może opracować plan wdrożenia. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Ustawianie planu implementacji

Plan implementacji powinien obejmować:

- Mapowanie stanu początkowego i żądanego stanu końcowego oraz kroków, które należy wykonać z jednego do drugiego
- sposób rozwiązywania problemów z odnajdywaniem poufnych elementów
- planowania zasad i kolejności, w jakiej zostaną one zaimplementowane
- jak będziesz rozwiązywać wszelkie wymagania wstępne
- planowanie sposobu testowania zasad przed przejściem do wymuszania
- jak będziesz szkolić użytkowników końcowych
- jak będziesz testować i dostrajać zasady
- jak będziesz przeglądać i aktualizować strategię zapobiegania utracie danych w oparciu o zmieniające się wymagania prawne, prawne, branżowe lub ochrony własności intelektualnej i potrzeb biznesowych

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Mapowanie ścieżki od początku do żądanego stanu końcowego

Dokumentowanie sposobu, w jaki organizacja będzie przechodzić od stanu początkowego do żądanego stanu końcowego, jest niezbędne do komunikowania się z uczestnikami projektu i ustawiania zakresu projektu. Oto zestaw kroków, które są często używane do wdrażania DLP. Będziesz wymagać więcej szczegółów niż to, ale możesz użyć tej metody, aby określić ścieżkę wdrażania DLP.

![grafika przedstawiająca wspólną kolejność wdrażania DLP.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Odnajdywanie elementów poufnych

Istnieje wiele sposobów odnajdywania poszczególnych poufnych elementów i ich lokalizacji. Być może masz już wdrożone etykiety poufności lub być może podjęto decyzję o wdrożeniu szerokich zasad DLP we wszystkich lokalizacjach, które wykrywają i przeprowadzają inspekcję tylko elementów. Aby dowiedzieć się więcej, zobacz [Know your data (Poznaj swoje dane](information-protection.md#know-your-data)).

#### <a name="policy-planning"></a>Planowanie zasad

Po rozpoczęciu wdrażania DLP możesz użyć tych pytań, aby skoncentrować działania związane z projektowaniem i implementacją zasad.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Jakie przepisy, przepisy i standardy branżowe muszą być przestrzegane przez organizację?

Ponieważ wiele organizacji przychodzi do DLP w celu zapewnienia zgodności z przepisami, udzielenie odpowiedzi na to pytanie jest naturalnym miejscem rozpoczęcia planowania implementacji DLP. Jednak jako implementator IT prawdopodobnie nie jesteś w stanie odpowiedzieć na to pytanie. Na to pytanie musi odpowiedzieć twój zespół prawny i kierownictwo firmy. 
 
**Przykład** Twoja organizacja podlega Zjednoczonej Brytanii finansowych.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Jakie elementy poufne ma organizacja, które muszą być chronione przed wyciekami?

Gdy twoja organizacja wie, gdzie znajduje się pod względem wymagań w zakresie zgodności z przepisami, będziesz mieć pewne pojęcie o tym, jakie elementy poufne muszą być chronione przed wyciekami i jak chcesz nadać priorytet implementacji zasad, aby je chronić. Pomoże to wybrać najbardziej odpowiednie szablony zasad DLP. Usługa Microsoft Purview zawiera wstępnie skonfigurowane szablony DLP dla usług finansowych, medycznych i zdrowotnych, prywatność i możesz utworzyć własne przy użyciu szablonu niestandardowego. Podczas projektowania i tworzenia rzeczywistych zasad DLP znajomość odpowiedzi na to pytanie pomoże Ci również wybrać odpowiedni [typ informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

**Przykład** Aby szybko rozpocząć pracę`U.K. Financial Data`, wybierz szablon zasad, który zawiera `Credit Card Number`typy informacji poufnych , `EU Debit Card Number`i .`SWIFT Code` 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Gdzie są elementy poufne i w jakie procesy biznesowe są zaangażowane?

Elementy zawierające informacje poufne organizacji są używane codziennie w trakcie prowadzenia działalności. Musisz wiedzieć, gdzie mogą wystąpić wystąpienia tych poufnych informacji i w jakich procesach biznesowych są one używane. Ułatwi to wybranie odpowiednich lokalizacji do zastosowania zasad DLP. Zasady DLP są stosowane do lokalizacji:

- Poczta e-mail programu Exchange
- Witryny programu SharePoint
- Konta usługi OneDrive
- Wiadomości na czacie i kanale w usłudze Teams
- urządzenia Windows 10
- Microsoft Defender for Cloud Apps
- Repozytoria lokalne

**Przykład** Audytorzy wewnętrzni organizacji śledzą zestaw numerów kart kredytowych. Przechowują arkusz kalkulacyjny w bezpiecznej witrynie programu SharePoint. Kilku pracowników tworzy kopie i zapisuje je w swojej pracy OneDrive dla Firm lokacji, która jest synchronizowana z urządzeniem Windows 10. Jeden z nich wkleja listę 14 z nich w wiadomości e-mail i próbuje wysłać ją do zewnętrznych audytorów w celu przeglądu. Chcesz zastosować zasady do bezpiecznej witryny programu SharePoint, wszystkich audytorów wewnętrznych OneDrive dla Firm kont, ich urządzeń Windows 10 i poczty e-mail programu Exchange.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Jaka jest tolerancja organizacji na wycieki?

Różne grupy w organizacji mogą mieć różne poglądy na temat dopuszczalnego poziomu wycieków poufnych elementów, a co nie. Osiągnięcie perfekcji zerowego wycieku może mieć zbyt wysokie koszty dla firmy.

**Przykład** Grupa zabezpieczeń organizacji, wraz z zespołem prawnym, uważa, że nie powinno być udostępniania numerów kart kredytowych nikomu spoza organizacji i nalegać na zerowy wyciek. Jednak w ramach regularnego przeglądu działalności związanej z numerami kart kredytowych audytorzy wewnętrzni muszą udostępnić niektóre numery kart kredytowych audytorom innych firm. Jeśli zasady DLP zabraniają udostępniania wszystkich numerów kart kredytowych poza organizacją, nastąpi znaczne zakłócenie procesu biznesowego i dodatkowe koszty w celu złagodzenia zakłóceń, aby audytorzy wewnętrzni ukończyli śledzenie. Ten dodatkowy koszt jest nie do przyjęcia dla kierownictwa wykonawczego. Aby rozwiązać ten problem, musi istnieć wewnętrzna rozmowa, aby zdecydować o akceptowalnym poziomie wycieku. Po podjęciu decyzji zasady mogą zawierać wyjątki dla niektórych osób w celu udostępniania informacji lub mogą być stosowane tylko w trybie inspekcji.

#### <a name="planning-for-prerequisites"></a>Planowanie wymagań wstępnych

Aby można było monitorować niektóre lokalizacje DLP, należy spełnić wymagania wstępne. Zobacz sekcję **Przed rozpoczęciem** :

- [Wprowadzenie do lokalnego skanera zapobiegania utracie danych (wersja zapoznawcza)](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md#before-you-begin)
- [Wprowadzenie do rozszerzenia zgodności firmy Microsoft](dlp-chrome-get-started.md#before-you-begin)
- [Używanie zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż Microsoft (wersja zapoznawcza)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>Wdrażanie zasad

Podczas tworzenia zasad DLP należy rozważyć stopniowe wprowadzanie ich w celu oceny ich wpływu i przetestowania ich skuteczności przed ich pełnym egzekwowaniem. Na przykład nie chcesz, aby nowe zasady DLP nieumyślnie blokowały dostęp do tysięcy dokumentów lub przerywały istniejący proces biznesowy.
  
Jeśli tworzysz zasady DLP o dużym potencjalnym wpływie, zalecamy wykonanie następującej sekwencji:
  
1. **Rozpocznij w trybie testowym bez wskazówek dotyczących zasad** , a następnie użyj raportów DLP i wszelkich raportów o zdarzeniach, aby ocenić wpływ. Raporty DLP umożliwiają wyświetlanie liczby, lokalizacji, typu i ważności dopasowań zasad. Na podstawie wyników można dostosować zasady zgodnie z potrzebami. W trybie testowym zasady DLP nie będą miały wpływu na produktywność osób pracujących w organizacji. Ponadto użyj tego etapu, aby przetestować przepływ pracy na potrzeby przeglądu zdarzeń DLP i korygowania problemów.
    
2. **Przejdź do trybu testowego z powiadomieniami i wskazówkami dotyczącymi zasad** , aby zacząć uczyć użytkowników o zasadach zgodności i przygotowywać ich do stosowania zasad. Warto mieć link do strony zasad organizacji, który zawiera więcej szczegółów na temat zasad w poradę zasad. Na tym etapie można również poprosić użytkowników o zgłaszanie wyników fałszywie dodatnich, aby umożliwić dalsze uściślanie zasad. Przejdź do tego etapu, gdy masz pewność, że wyniki aplikacji zasad są zgodne z tym, co mają na myśli osoby biorące udział w projekcie. 
    
3. **Rozpocznij pełne wymuszanie zasad** , aby akcje w regułach były stosowane i zawartość była chroniona. Kontynuuj monitorowanie raportów DLP i wszelkich raportów lub powiadomień o zdarzeniach, aby upewnić się, że wyniki są tym, co zamierzasz. 

    ![Opcje korzystania z trybu testowego i włączania zasad.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    Zasady DLP można wyłączyć w dowolnym momencie, co ma wpływ na wszystkie reguły w zasadach. Jednak każdą regułę można również wyłączyć indywidualnie, przełączając jej stan w edytorze reguł.

    ![Opcje wyłączania reguły w zasadach.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Można również zmienić priorytet wielu reguł w zasadach. W tym celu otwórz zasady do edycji. W wierszu reguły wybierz wielokropek (**...**), a następnie wybierz opcję, taką jak **Przenieś w dół** lub **Przenieś do ostatniego**.

    ![Ustaw priorytet reguły.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Szkolenie użytkowników końcowych

Po wyzwoleniu zasad DLP można skonfigurować zasady do [wysyłania powiadomień e-mail i pokazywania wskazówek dotyczących zasad DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) administratorom i użytkownikom końcowym. Zasady są nadal w trybie testowym i zanim zostaną ustawione w celu wymuszenia akcji blokującej, porady dotyczące zasad są przydatnymi sposobami podnoszenia świadomości ryzykownych zachowań na poufnych elementach i trenowania użytkowników w celu uniknięcia tych zachowań w przyszłości.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>Przejrzyj wymagania DLP i strategię aktualizacji

Przepisy, przepisy i standardy branżowe, które mogą podlegać organizacji, zmienią się wraz z upływem czasu, a cele biznesowe dotyczące DLP również zostaną zmienione. Pamiętaj o regularnych przeglądach wszystkich tych obszarów, aby organizacja pozostała w zgodności, a implementacja DLP nadal spełnia twoje potrzeby biznesowe.

## <a name="approaches-to-deployment"></a>Podejścia do wdrożenia

|Opis potrzeb biznesowych klientów  | Podejście  |
|---------|---------|
|**Contoso Bank** jest w branży wysoce regulowanej i ma wiele różnych rodzajów poufnych elementów w wielu różnych lokalizacjach. </br> - wie, które typy informacji poufnych mają najwyższy priorytet. </br> — musi zminimalizować zakłócenia biznesowe w miarę wdrażania zasad. </br> — ma zasoby IT i może zatrudniać ekspertów, którzy mogą pomagać w planowaniu, projektowaniu </br> — ma umowę pomocy technicznej premier z firmą Microsoft| - Poświęć trochę czasu, aby zrozumieć, jakie przepisy muszą przestrzegać i w jaki sposób będą przestrzegane. </br> -Poświęć trochę czasu, aby zrozumieć lepszą wartość stosu Microsoft Purview Information Protection razem </br> - Opracowywanie schematu etykietowania poufności dla elementów o priorytetach i stosowanie </br> - Angażowanie właścicieli procesów biznesowych </br>- Projektowanie/kodowanie zasad, wdrażanie w trybie testowym, szkolenie użytkowników </br>- powtórz|
|**TailSpin Toys** nie wie, co ma i gdzie jest, i ma niewielką lub żadną głębokość zasobów. Intensywnie korzystają z usług Teams, OneDrive dla Firm i Exchange.     |— Zacznij od prostych zasad dotyczących lokalizacji o priorytetach. </br>- Monitorowanie tego, co zostanie zidentyfikowane </br>- Odpowiednio zastosuj etykiety poufności </br>— Uściślaj zasady, trenuj użytkowników       |
|**Fabrikam** to mały startup, który chce chronić swoją własność intelektualną i musi działać szybko. Są gotowi poświęcić niektóre zasoby, ale nie mogą sobie pozwolić na zatrudnianie zewnętrznych ekspertów. </br>— Elementy poufne znajdują się w usłudze Microsoft 365 OneDrive dla Firm/SharePoint </br>- Wdrażanie OneDrive dla Firm i SharePoint jest powolne, pracownicy / cień IT używać DropBox i dysk Google do udostępniania / przechowywania elementów </br>- Pracownicy cenią sobie szybkość pracy nad dziedziną ochrony danych </br>- Klient splurged i kupił wszystkich 18 pracowników nowych urządzeń Windows 10     |— Korzystanie z domyślnych zasad DLP w usłudze Teams </br>— Domyślnie używaj ustawień ograniczonych dla elementów programu SharePoint </br>— Wdrażanie zasad, które uniemożliwiają udostępnianie zewnętrzne </br>— Wdrażanie zasad w lokalizacjach o priorytetach </br>— Wdrażanie zasad na urządzeniach Windows 10 </br>— Blokuj przekazywanie do magazynu w chmurze bez OneDrive dla Firm      |

<!--

## Planning for workloads

### Exchange

### SharePoint

### OneDrive for Business

### Teams

### Windows 10 Devices

### Microsoft Cloud App Security (MCAS)

### On-premises Scanner
-->

## <a name="see-also"></a>Zobacz też
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
