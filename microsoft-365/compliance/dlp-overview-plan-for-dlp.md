---
title: Planowanie ochrony przed utratą danych
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
description: Omówienie procesu planowania w celu ochrony przed utratą danych
ms.openlocfilehash: c695a6a2a4bd21a147e5e81bc73fb65ab1378960
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005254"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Planowanie ochrony przed utratą danych (DLP)

Każda organizacja będzie zaplanować i wdrożyć zapobieganie utracie danych (DLP) w inny sposób, ponieważ potrzeby biznesowe, cele, zasoby i sytuacje każdej organizacji są unikatowe. Istnieją jednak elementy wspólne dla wszystkich skutecznych implementacji DLP. W tym artykule przedstawiliśmy najlepsze rozwiązania używane przez organizacje w planowaniu ochrony przed firmami.

## <a name="multiple-starting-points"></a>Wiele punktów początkowych

Wiele organizacji decyduje się na wdrożenie zasad DLP w celu zapewnienia zgodności z różnymi przepisami rządowymi lub branżowymi. Może to być na przykład Ogólne Rozporządzenie o Ochronie Danych (RODO) Unii Europejskiej, ustawa HIPAA (Health Insurance Portability and Accountability Act) albo california Consumer Privacy Act (HDMIA). Ponadto wdrażają zabezpieczenia przed utratą danych w celu ochrony swojej własności intelektualnej. Jednak miejsce rozpoczęcia i najlepsze miejsce docelowe podczas podróży w programie DLP różnią się. 

Organizacje mogą rozpocząć swoją podróż w celu lp:

- z fokusu platformy, np. gdy chcesz chronić informacje w wiadomościach Teams wiadomościach czatu i kanałach lub na Windows 10 urządzeniach
- wiedza o tym, jakie informacje poufne chcą określić priorytet ochrony, na przykład dokumentację opieki zdrowotnej, i od razu o definiowaniu zasad ochrony
- nie znając, co to są informacje poufne, gdzie to jest i kto co z tym robi, zaczyna od odnajdowania i kategoryzacji oraz bardziej metodycznego podejścia
- nie znając, co to są informacje poufne, czy gdzie to jest lub kto z tym coś robi, ale od razu przechodzi do definiowania zasad i używa ich jako punktu wyjścia, a następnie uściśli swoje zasady.
- wiedza o potrzebie wdrożenia pełnego zestawu danych Microsoft 365 Informacji i w związku z tym, że będą oni mieli bardziej długoterminowe, metodyczne podejście

To tylko kilka przykładów tego, jak klienci mogą korzystać z ochrony przed utratą danych i od którego zaczynasz, rozwiązanie Microsoft 365 DLP jest wystarczająco elastyczne, aby uwzględnić różnego rodzaju podróże w celu ochrony informacji od początku do w pełni zrealizowanej strategii ochrony przed utratą danych. 

## <a name="overview-of-planning-process"></a>Omówienie procesu planowania

Informacje [na temat ochrony przed utratą](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) danych przedstawią trzy różne aspekty procesu [planowania ochrony](dlp-learn-about-dlp.md#plan-for-dlp) przed utratą danych. W tym miejscu opisano szczegółowo elementy wspólne dla wszystkich planów DLP.

### <a name="identify-stakeholders"></a>Identyfikowanie uczestników projektu

Po zaimplementowaniu zasady DLP można stosować w dużej części organizacji. IT nie może samodzielnie opracować szerokiego planu bez negatywnych konsekwencji. Musisz zidentyfikować uczestników projektu, którzy mogą:

- opisać przepisy, przepisy i standardy branżowe, których podlega Twoja organizacja
- kategorie elementów poufnych, które mają być chronione
- procesów biznesowych, w których są używane
- ryzykowne zachowanie, które powinno być ograniczone
- określanie priorytetu, które dane powinny być najpierw chronione, na podstawie wrażliwości danych i ryzyka
- konspekt procesu przeglądu i rozwiązywania problemów zgodnego ze zdarzeniami zasad DLP 
 
Zazwyczaj wymaga to 85% ochrony zgodności z przepisami i zgodnością oraz 15% ochrony własności intelektualnej. Oto kilka sugestii dotyczących ról, które należy uwzględnić w procesie planowania:

- Insektnicy przepisami i zgodnością
- Główny dyrektor ds. ryzyka
- Prawnicy
- Służby ds. zabezpieczeń i zgodności
- Właściciele firmy dla elementów danych
- Użytkownicy biznesowi
- IT

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Opis kategorii informacji poufnych, które mają być chronine

Następnie uczestnicy projektu opisują kategorie informacji poufnych, które mają być chronione, oraz proces biznesowy, w których są używane. Na przykład zasady Microsoft 365 DLP określają następujące kategorie:

- Finanse 
- Informacje medyczne i informacje o stanie zdrowia
- Prywatność
- Niestandardowe

Udziałowcy mogą zidentyfikować informacje poufne jako "Jesteśmy przetwarzaniem danych, więc musimy zaimplementować ochronę prywatności w odniesieniu do informacji o podmiotach danych i informacji finansowych".

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Ustawianie celów i strategii

Po zidentyfikowaniu uczestników projektu i rozpoznaniu, które informacje poufne są potrzebne do ochrony i miejsca ich stosowania, uczestnicy projektu mogą określić cele ochrony i mogą opracować plan implementacji. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Ustawianie planu implementacji

Plan implementacji powinien zawierać:

- Mapowanie stanu początkowego i odpowiedniego stanu końcowego oraz czynności, które należy wykonać, aby nasyłać dane z jednego stanu początkowego do drugiego
- jak będzie dotyczyć odnajdowania elementów poufnych
- planowanie zasad i kolejność ich wdrożenia
- sposób rozwiązania wszelkich wymagań wstępnych
- Planowanie, jak zasady będą najpierw testowane przed przejściem do wymuszeń
- jak przeszkolisz użytkowników końcowych
- jak testować i dostrajać zasady
- jak przeglądasz i aktualizujesz strategię ochrony przed utratą danych opartą na zmianie wymogów prawnych, prawnych, branżowych lub ochrony własności intelektualnej oraz potrzeb biznesowych

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Mapowanie ścieżki od początku do odpowiedniego stanu końcowego

Dokumentowanie sposobu, w jaki Twoja organizacja będzie się rozpoczynać od stanu początkowego do odpowiedniego stanu końcowego, ma kluczowe znaczenie dla komunikowania się z uczestnikami projektu i ustawiania zakresu projektu. Poniżej znajduje się zestaw czynności, które są często używane do wdrażania zasad DLP. Będziesz chcieć uzyskać więcej szczegółów, ale możesz użyć ich do ramek ścieżki przyjęcia funkcji DLP.

![Grafika przedstawiająca kolejność wdrażania zasad DLP.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Odnajdowanie poufnych elementów

Istnieje wiele sposobów odnajdywania poszczególnych poufnych elementów i ich zlokalizowania. Być może etykiety wrażliwości są już wdrożone lub zdecydowano się na wdrożenie szerokich zasad DLP we wszystkich lokalizacjach, w których są wykrywane i przeprowadzane inspekcje tylko tych elementów. Aby dowiedzieć się więcej, zobacz [Znając swoje dane](information-protection.md#know-your-data).

#### <a name="policy-planning"></a>Planowanie zasad

Po rozpoczęciu wdrażania funkcji DLP możesz za pomocą tych pytań skoncentrować się na projektach zasad i działaniach wdrożeniowych.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Jakie przepisy, przepisy i standardy branżowe muszą być zgodne z przepisami Twojej organizacji?

Ponieważ wiele organizacji chce zapewnić zgodność z przepisami, odpowiedź na to pytanie jest naturalnym punktem wyjścia do planowania wdrożenia tej zasady. Jednak jako implementer IT, prawdopodobnie nie jesteś w stanie na nie odpowiedzieć. Na nie muszą odpowiedzieć członkowie twojego zespołu prawnego i  kierownictwa firmy. 
 
**Przykład** Twoja organizacja podlega Wielkiej Brytanii przepisów finansowych.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Jakie poufne elementy posiada Twoja organizacja, które muszą być chronione przed wyciekiem?

Gdy Twoja organizacja wie, gdzie należy się ona z punktu widzenia wymogów zgodności z przepisami, wiesz już, jakie poufne elementy muszą być chronione przed wyciekiem i jak chcesz określić priorytety implementacji zasad w celu ich ochrony. Pomoże Ci to w wybraniu najbardziej odpowiednich szablonów zasad DLP. Microsoft 365 zawiera wstępnie skonfigurowane szablony DLP do celów finansowych, medycznych i opieki zdrowotnej, prywatności, a także można utworzyć własne szablony przy użyciu szablonu Niestandardowe. Podczas projektowania i tworzenia rzeczywistych zasad DLP znajomość odpowiedzi na to pytanie pomoże także w wybraniu odpowiedniego typu [informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

**Przykład** Aby szybko rozpocząć pracę, wybierz `U.K. Financial Data` szablon zasad, który zawiera `Credit Card Number`typy informacji poufnych i , `EU Debit Card Number`.`SWIFT Code` 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Gdzie znajdują się elementy poufne i z jakim procesem biznesowym są one związane?

Elementy, które zawierają informacje poufne organizacji, są używane na co dzień w ramach prowadzenia działalności biznesowej. Musisz wiedzieć, gdzie mogą wystąpić wystąpienia tych informacji poufnych i w jakich procesach biznesowych są one używane. Pomoże ci to wybrać odpowiednie lokalizacje, do których mają być stosowane zasady DLP. Microsoft 365 DLP są stosowane do lokalizacji:

- Exchange-mail
- SharePoint witryn
- OneDrive konta
- Teams wiadomości czatu i kanałów
- Windows 10 urządzenia
- Usługa Microsoft Defender dla aplikacji w chmurze
- Repozytoria lokalne

**Przykład** Wewnętrzni audytorzy w Twojej organizacji śledzą zestaw numerów kart kredytowych. Przechowują one arkusz kalkulacyjny w bezpiecznym SharePoint sieci Web. Kilku pracowników kopiuje i zapisuje je w witrynie OneDrive dla Firm pracy, która jest synchronizowana z ich Windows 10 urządzeniami. Jeden z nich wkleja listę 14 z nich w wiadomości e-mail i próbuje przesłać ją do audytorów zewnętrznych w celu sprawdzenia. Możesz zastosować te zasady do bezpiecznej witryny usługi SharePoint, wszystkich audytorów wewnętrznych w OneDrive dla Firm, ich urządzeń Windows 10 i poczty Exchange e-mail.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Co to jest tolerancja organizacji do wycieku?

Różne grupy w organizacji mogą mieć różne widoki na temat możliwego do przyjęcia poziomu wycieku poufnych elementów, a co nie. Uzyskanie tych informacji o zerowej wycieku może okazać się zbyt wysokie dla firmy.

**Przykład** Członkowie grupy zabezpieczeń organizacji wraz z zespołem ds. prawnych uważają, że nie należy udostępniać numerów kart kredytowych osobom spoza organizacji i podlegać wyciekom. W ramach regularnego przeglądu działań na numerach kart kredytowych audytorzy wewnętrzni muszą jednak udostępnić niektóre numery kart kredytowych audytorom innych podmiotów. Jeśli Twoje zasady DLP zabraniają udostępniania numerów kart kredytowych poza firmę, zakłócenie i dodatkowe koszty w celu zminimalizowania przerw w pracy audytorów wewnętrznych mogą pomóc w ukończeniu śledzenia tych danych przez audytorów wewnętrznych. Ten dodatkowy koszt nie jest nieakceptowalny dla kierownictwa kierownictwa. Aby rozwiązać ten problem, należy podjąć wewnętrzną konwersację, aby określić akceptowalny poziom wycieku. Gdy to postanowisz, zasady mogą udostępnić określone osoby w wyjątkach lub mogą być stosowane tylko w trybie inspekcji.

#### <a name="planning-for-prerequisites"></a>Planowanie wymagań wstępnych

Zanim będzie można monitorować niektóre lokalizacje DLP, muszą zostać spełnione wymagania wstępne. Zobacz **sekcje Przed rozpoczęciem** :

- [Wprowadzenie do ochrony przed utratą danych w środowisku lokalnym (wersja Preview)](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Wprowadzenie do ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-getting-started.md#before-you-begin)
- [Wprowadzenie do rozszerzenia zgodności firmy Microsoft (wersja preview)](dlp-chrome-get-started.md#before-you-begin)
- [Korzystanie z zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż firmy Microsoft (wersja Preview)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>Wdrażanie zasad

Podczas tworzenia zasad DLP należy rozważyć ich stopniowe wdrażanie w celu oceny ich wpływu i przetestowania ich skuteczności przed ich pełnym wymuszaniem. Na przykład nie chcesz, aby nowe zasady DLP niezamierzonie blokowały dostęp do tysięcy dokumentów lub łamiły istniejący proces biznesowy.
  
Jeśli tworzysz zasady DLP o dużym potencjalnym wpływie, zalecamy następującą sekwencję:
  
1. **Rozpoczynanie pracy w trybie testowania** bez Wskazówki zasad, a następnie ocenianie wpływu za pomocą raportów ochrony przed incydentami i raportów zdarzeń. Raporty funkcji DLP mogą umożliwia wyświetlanie liczby, lokalizacji, typu i ważności dopasowania zasad. Na podstawie wyników możesz dostosować zasady zgodnie z potrzebami. W trybie testowania zasady DLP nie mają wpływu na produktywność osób pracujących w organizacji. Ten etap również pozwala przetestować przepływ pracy na wypadek przejrzenia zdarzenia DLP i rozwiązania problemu.
    
2. **Przejdź do trybu** testowania z powiadomieniami i Wskazówki zasad, aby rozpocząć omów z użytkownikami zasady zgodności i przygotować ich do stosowania zasad. Warto utworzyć link do strony zasad organizacji, który zawiera więcej szczegółowych informacji na temat zasad w poradach dotyczących zasad. Na tym etapie można również poprosić użytkowników o zgłaszanie wyników fałszywie dodatnich, aby można było jeszcze bardziej uściślić zasady. Przejdź do tego etapu, gdy masz pewność, że wyniki zastosowania zasad są zgodne z tym, co mieli na myśli uczestnicy projektu. 
    
3. **Rozpoczęcie pełnego wymuszania zasad** , dzięki czemu będą stosowane akcje w zasadach i zawartość będzie chroniona. W dalszym ciągu monitoruj raporty dotyczące zasad DLP oraz wszelkie raporty i powiadomienia o incydentach, aby upewnić się, że wyniki są dokładnie takie, jakie mają zanadto. 

    ![Opcje korzystania z trybu testowania i włączania zasad.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    Zasady DLP można wyłączyć w dowolnym momencie, co ma wpływ na wszystkie reguły w zasadach. Każdą regułę można jednak wyłączyć osobno, przełączanie jej stanu w edytorze reguł.

    ![Opcje wyłączania reguły w zasadach.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Można również zmienić priorytet wielu reguł w zasadach. W tym celu otwórz zasady do edycji. W wierszu reguły wybierz wielokropek (**...**), a następnie wybierz opcję, taką jak Przenieś w dół lub **Przesuń do ostatniego**.

    ![Ustawianie priorytetu reguły.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Szkolenia dla użytkowników końcowych

Po wyzwoleniu zasad DLP możesz skonfigurować zasady w taki sposób, aby wysyłać powiadomienia e-mail i wyświetlać porady dotyczące zasad [DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) administratorom i użytkownikom końcowych. Mimo że zasady są nadal w trybie testowania i zanim zostaną ustawione na wymuszanie blokowania, porady dotyczące zasad to przydatne sposoby podnoszenia wiedzy na temat ryzykownych zachowań dotyczących elementów poufnych i szkolenie użytkowników przed tymi zachowaniami w przyszłości.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>Przegląd wymagań dotyczących zasad DLP i strategii aktualizacji

Przepisy, przepisy i standardy branżowe, których podlega Twoja organizacja, będą z czasem zmieniać się, a także Twoje cele biznesowe dotyczące ochrony przed firmami. Pamiętaj o regularnym przeglądaniu wszystkich tych obszarów, aby Twoja organizacja pozostawała w zrównaniu z przepisami i Twoja implementacja zasad DLP nadal spełniała Twoje potrzeby biznesowe.

## <a name="approaches-to-deployment"></a>Metody wdrażania

|Opis potrzeb biznesowych klientów  | podejście  |
|---------|---------|
|**Contoso Bank** to dobrze uregulowana firma, która ma wiele różnych typów elementów poufnych w wielu różnych lokalizacjach. </br> — wie, które typy informacji poufnych mają najwyższy priorytet. </br> — musi zminimalizować zakłócenia w działaniu firmy w przypadku wywłasniania zasad. </br> — ma zasoby IT i może zatrudnić ekspertów do planowania, projektowania i wdrażania </br> — ma umowę na pomoc techniczną premier z firmą Microsoft| — Porozumiew się z czasem, jakie przepisy muszą przestrzegać i w jaki sposób będą one przestrzegane. </br> — Poeksymaj trochę czasu, aby razem zrozumieć, jaka jest wartość stosu Microsoft 365 Information Protection </br> - Opracowanie schematu etykiet wrażliwości dla elementów, dla których priorytetyzowane są, i stosowanie </br> - Angażowania właścicieli procesów biznesowych </br>- Zasady projektowania/kodów, wdrażanie w trybie testowania, szkolenie użytkowników </br>— powtórz|
|**TailSpin Toys** nie wie, co ma ani gdzie jest, i nie ma żadnej głębokości zasobów. Są one Teams, OneDrive dla Firm i Exchange mają wiele zastosowania.     |— Zacznij od prostych zasad dla lokalizacji, dla których priorytety są określone. </br>— Monitorowanie zidentyfikowanych danych </br>— Zastosuj odpowiednio etykiety wrażliwości </br>- Uściślij zasady, szkolenie użytkowników       |
|**Fabrikam** to mały start, który chce chronić swoją własność intelektualną i musi szybko przejść do programu. Są gotowi przeznaczyć na niektóre zasoby, ale nie mogą pozwolić sobie na zatrudnienie ekspertów zewnętrznych. </br>— Poufne elementy znajdują się w Microsoft 365 OneDrive dla Firm/SharePoint </br>- Wdrożenie usług OneDrive dla Firm i SharePoint jest powolne, pracownicy/indyjscy w tle używają usług DropBox i Google do udostępniania/przechowywania elementów </br>- Szybkość pracy pracowników nad dyscypliną ochrony danych </br>- Splurged customer and bought all 18 employees new Windows 10 devices     |— Skorzystaj z domyślnych zasad DLP w programie Teams </br>— Użyj domyślnie ograniczone dla SharePoint elementów </br>- Wdrażanie zasad uniemożliwiających udostępnianie zewnętrzne </br>- Wdrażanie zasad w celu ustalania priorytetów lokalizacji </br>- Wdrażanie zasad na Windows 10 urządzeniach </br>- Blokowanie przekazywania do magazynu w chmurze OneDrive dla Firm danych      |

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
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
