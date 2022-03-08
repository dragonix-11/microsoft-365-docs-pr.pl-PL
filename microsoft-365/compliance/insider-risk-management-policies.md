---
title: Zasady zarządzania ryzykiem w niejawnym programie testów
description: Informacje o zasadach zarządzania ryzykiem w niejawnym programie testów w programie Microsoft 365
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
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 86208efec649ad7fecc70ec1570a6e97ce28938c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330467"
---
# <a name="insider-risk-management-policies"></a>Zasady zarządzania ryzykiem w niejawnym programie testów

Zasady zarządzania ryzykiem w niejawnym programie testów określają, których użytkowników należy do określonych zakresów oraz jakie typy wskaźników ryzyka są skonfigurowane dla alertów. Możesz szybko utworzyć zasady dotyczące wszystkich użytkowników w organizacji lub zdefiniować poszczególnych użytkowników lub grupy do zarządzania w zasadach. Zasady obsługują priorytety zawartości w celu koncentracji warunków zasad na wielu lub Microsoft Teams, SharePoint, typach wrażliwości danych i etykietach danych. Korzystając z szablonów, możesz wybrać określone wskaźniki ryzyka i dostosować progi zdarzeń dla wskaźników zasad, w praktyce dostosowywając wyniki ryzyka oraz poziom i częstotliwość alertów. Ponadto wyniki oceny ryzyka i wykrywanie anomalii pomagają zidentyfikować działania użytkowników, które mają wyższą lub bardziej nietypową ważność. Okna zasad umożliwiają zdefiniowanie okresu stosowania zasad do działań alertów i służą do określania czasu trwania zasad po ich aktywowaniu.

Obejrzyj klip [wideo Konfiguracja](https://www.youtube.com/watch?v=kudK5ajZTUo) zasad zarządzania ryzykiem w niejawnym programie testów, aby uzyskać omówienie sposobu, w jaki zasady utworzone przy użyciu wbudowanych szablonów zasad mogą ułatwić szybkie działanie w przypadku potencjalnych zagrożeń.

## <a name="policy-dashboard"></a>Pulpit nawigacyjny zasad

Pulpit **nawigacyjny zasad** umożliwia szybkie wyświetlanie zasad w organizacji, kondycję zasad, ręczne dodawanie użytkowników do zasad oraz wyświetlanie stanu alertów skojarzonych z każdymi zasadami.

- **Nazwa zasad**: nazwa przypisana do zasad w kreatorze zasad.
- **Stan**: stan kondycji poszczególnych zasad. Wyświetla liczbę ostrzeżeń i zaleceń dotyczących zasad lub *stan "* Kondycja" w przypadku zasad bez problemów.  Możesz wybrać zasady, aby wyświetlić szczegółowe informacje o stanie kondycji dotyczące ostrzeżeń i zaleceń.
- **Aktywne alerty**: liczba aktywnych alertów dla poszczególnych zasad.
- **Potwierdzone alerty**: Całkowita liczba alertów dotyczących spraw wynikających z zasad w ciągu ostatnich 365 dni.
- **Akcje podejmowane w przypadku alertów**: Całkowita liczba alertów, które zostały potwierdzone lub odrzucone w ciągu ostatnich 365 dni.
- **Alert zasad :** wartość procentowa określona przez łączną liczbę potwierdzono alertów podzielona przez łączną liczbę akcji dotyczących alertów (czyli sumę alertów, które zostały potwierdzone lub odrzucone w ubiegłym roku).

![Pulpit nawigacyjny zasad zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics"></a>Zalecenia dotyczące zasad z analizy

Analiza ryzyka w niejawnym programie testów umożliwia przeprowadzenie oceny potencjalnych czynników ryzyka niejawnego programu testów w organizacji bez konfigurowania żadnych zasad ryzyka niejawnego programu testów. Ocena ta może ułatwić organizacji zidentyfikowanie potencjalnych obszarów o wyższym poziomie ryzyka użytkownika oraz określenie typu i zakresu zasad zarządzania ryzykiem niejawnego programu testów, które można rozważyć podczas konfigurowania.

Aby dowiedzieć się więcej o analizie ryzyka w niejawnym programie testów i zaleceniach dotyczących zasad, zobacz Ustawienia zarządzania ryzykiem w niejawnym programie [testów: Analiza](insider-risk-management-settings.md#analytics).

## <a name="policy-templates"></a>Szablony zasad

Szablony zarządzania ryzykiem w niejawnym programie testów to wstępnie zdefiniowane warunki zasad definiujące typy wskaźników ryzyka i modelu oceniania ryzyka stosowanego w zasadach. Przed utworzeniem zasad do każdej zasady musi być przypisany szablon w kreatorze tworzenia zasad. W przypadku każdego szablonu zasad zarządzanie ryzykiem w niejawnym programie testów obsługuje maksymalnie pięć zasad. Podczas tworzenia nowych zasad ryzyka niejawnego programu testów za pomocą kreatora zasad wybierz jeden z następujących szablonów zasad:

### <a name="data-theft-by-departing-users"></a>Kradzież danych przez odchodzące użytkowników

Gdy użytkownicy odchodzą z organizacji, istnieją określone wskaźniki ryzyka zwykle związane z kradzieżą danych przez odchodzące użytkowników. W tym szablonie zasad do oceniania ryzyka są używane wskaźniki wysokiego ryzyka, a w tym obszarze ryzyka skupiono się na wykrywaniu i alertach. Kradzież danych w przypadku odchodzącego użytkownika może obejmować pobieranie plików z usługi SharePoint Online, drukowanie plików oraz kopiowanie danych do wiadomości osobistych w chmurze i usług przechowywania w pobliżu ich dat zatrudnienia i zakończenia. Za pomocą łącznika Microsoft 365 HR lub opcji automatycznego monitorowania usuwania konta użytkownika w programie Azure Active Directory w organizacji ten szablon rozpoczyna ocenianie wskaźników ryzyka związanych z tymi działaniami i ich skorelowania ze statusem zatrudnienia użytkowników.

> [!IMPORTANT]
> W przypadku korzystania z tego szablonu można skonfigurować łącznik usługi Microsoft 365 HR w celu okresowego importowania informacji o dacie ponownego przypisania i zakończenia dla użytkowników w organizacji. Zobacz artykuł [Importowanie danych za pomocą łącznika](import-hr-data.md) kadr, aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 kadr dla organizacji. Jeśli nie chcesz używać łącznika kadr, musisz wybrać opcję Konto użytkownika usunięte z usługi Azure AD podczas konfigurowania zdarzeń wyzwalacza w kreatorze zasad.

### <a name="general-data-leaks"></a>Ogólne wycieki danych

Ochrona danych i zapobieganie wyciekom danych to stałe wyzwanie dla większości organizacji, zwłaszcza w przypadku szybkiego przyrostu nowych danych tworzona przez użytkowników, urządzenia i usługi. Użytkownicy mogą tworzyć, przechowywać i udostępniać informacje między usługami i urządzeniami, które sprawiają, że zarządzanie wyciekami danych jest coraz bardziej złożone i trudne. Wycieki danych mogą obejmować przypadkowe oversharowanie informacji poza organizację lub kradzież danych ze złośliwymi intencjami. Z przypisanymi zasadami ochrony przed utratą danych (DLP, Data Loss Prevention), wbudowanymi zdarzeniami wyzwalania, które można dostosowywać, ten szablon pozwala oceniać wykrywanie w czasie rzeczywistym podejrzanych plików SharePoint Pobieranie danych online, udostępnianie plików i folderów, drukowanie plików oraz kopiowanie danych do osobistych usług wiadomości i magazynu w chmurze.

Podczas korzystania z szablonu *wycieków* danych możesz przypisać zasady DLP do wyzwalania wskaźników w zasadach ryzyka niejawnego programu testów dla alertów o wysokim poziomie ważności w organizacji. Ilekroć do dziennika inspekcji programu Office 365 zostanie wygenerowany alert o wysokim poziomie ważności przez regułę zasad DLP, zasady ryzyka niejawnego programu testów utworzone za pomocą tego szablonu automatycznie zbadają alert o wysokim poziomie ważności zasad DLP. Jeśli alert zawiera użytkownika w zakresie zdefiniowany w zasadach ryzyka niejawnego programu testów, alert jest przetwarzany przez zasady ryzyka niejawnego programu testów jako nowy alert i przypisywany jest wynik oceny zagrożenia i zagrożenia niejawnego programu testów. Możesz także przypisać wybrane wskaźniki jako wyzwalające zdarzenia zasad. Taka elastyczność i dostosowywanie pomaga w zakresie zasad tylko do działań objętych wskaźnikami. Te zasady umożliwiają ocenianie tego alertu w kontekście z innymi działaniami uwzględnionmi w tym przypadku.

#### <a name="data-leaks-policy-guidelines"></a>Wytyczne dotyczące zasad wycieków danych

Tworząc lub modyfikując zasady ochrony przed zagrożeniami w celu ich używania z zasadami zarządzania ryzykiem w niejawnym programie testów, należy rozważyć następujące wytyczne:

- Podczas konfigurowania reguł w zasadach ochrony przed zdarzeniami DLP  należy określić priorytet zdarzeń  ex selektywnych i przypisywać ustawienia raportów zdarzeń do wartości Wysoka. Na przykład wiadomość e-mail z poufnymi dokumentami do znanego zawodnika powinna być zdarzeniem *wysokiego poziomu* alertu ex omówiące. Over-assigning the *High* level in the **Incident reports** settings in other DLP policy rules can increase the noise in the insider risk management workflow and make it it difficult for your data pochłonie and analysts to properly evaluate these alerts. Na przykład przypisywanie *wysokich poziomów* alertów do uzyskiwania dostępu do działań odmowę w zasadach DLP utrudnia ocenę bardziej ryzykownego zachowania użytkownika i działań.
- W przypadku używania zasad DLP jako zdarzenia wyzwalającego upewnij się, że rozumiesz i poprawnie konfigurujesz użytkowników w zakresie, zarówno w zasadach ochrony przed zagrożeniami, jak i w niejawnym programie testów. Tylko użytkownicy, którzy mają określone zasady zarządzania ryzykiem w niejawnym programie  testów przy użyciu szablonu Wycieki danych, będą mieć przetwarzane alerty zasad DLP o wysokim poziomie ważności. Ponadto tylko użytkownicy, których reguły mają określony zakres w związku z alertami DLP o wysokim poziomie ważności, będą rozważani przez zasady zarządzania ryzykiem w ramach niejawnego programu testów. Ważne jest, aby nieoznaczanie użytkowników w zakresie, zarówno w przypadku zasad DLP, jak i zasad ryzyka niejawnego programu testów, nie było możliwe w sposób kolidujący ze sobą.

     Jeśli na przykład reguły zasad DLP są objęte zakresem tylko do użytkowników w zespole sprzedaży, a zasady ryzyka niejawnego programu testów utworzone  na podstawie szablonu Wycieki danych zdefiniowały wszystkich użytkowników jako objęte zakresem, zasady ryzyka niejawnego programu testów będą w rzeczywistości przetwarzać tylko alerty DLP o wysokim poziomie ważności dla użytkowników w zespole sprzedaży. Zasady ryzyka niejawnego programu testów nie będą otrzymywać żadnych alertów DLP o wysokim priorytecie, aby użytkownicy przetwarzali dane, które nie zostały zdefiniowane w zasadach ochrony przed zagrożeniami w tym przykładzie. Jeśli natomiast zasady zarządzania ryzykiem niejawnego programu testów utworzone  na podstawie szablonów wycieków danych zostaną zawężona tylko do użytkowników w zespole sprzedaży, a przypisane zasady DLP zostaną przypisane do wszystkich użytkowników, zasady ryzyka niejawnego programu testów będą przetwarzać tylko alerty DLP o wysokim poziomie ważności dla członków zespołu sprzedaży. Zasady zarządzania ryzykiem w niejawnym programie testów będą ignorować alerty DLP o wysokim poziomie ważności dla wszystkich użytkowników, którzy nie są dostępni w zespole sprzedaży.

- Upewnij się, że ustawienie reguły **Raporty o** incydentach w zasadach DLP używanych dla tego szablonu zarządzania ryzykiem niejawnego programu testów jest *skonfigurowane dla* alertów o wysokim poziomie ważności. Poziom *Wysoki* poziom ważności to zdarzenia wyzwalające oraz alerty zarządzania ryzykiem w niejawnym programie testów nie zostaną wygenerowane na podstawie reguł w zasadach  DLP z polem  Raporty zdarzeń ustawionym na wartość Niski lub *Średni*.

    ![Ustawienie alertu zasad DLP.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Podczas tworzenia nowych zasad DLP przy użyciu wbudowanych szablonów musisz wybrać opcję Utwórz lub dostosuj zaawansowane reguły **DLP**, aby skonfigurować ustawienie Raporty o zdarzeniach na poziomie  Wysoka ważność.

Podczas korzystania z tej opcji wyzwalania zdarzeń  każda zasada zarządzania ryzykiem w niejawnym programie testów utworzona na podstawie szablonu Wycieki danych może mieć przypisane tylko jedną zasady DLP. Rozważ utworzenie dedykowanych zasad DLP łączących różne działania, które chcesz wykrywać i działać jako wyzwalanie zdarzeń dla zasad ryzyka niejawnego programu testów, które korzystają z **szablonu wycieków** danych.

Zobacz artykuł [Tworzenie, testowanie](create-test-tune-dlp-policy.md) i dostosowywanie zasad DLP, aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad DLP dla organizacji.

### <a name="data-leaks-by-priority-users-preview"></a>Wycieki danych według priorytetowych użytkowników (wersja zapoznawcza)

Ochrona danych i zapobieganie wyciekom danych u użytkowników w organizacji może zależeć od ich pozycji, poziomu dostępu do poufnych informacji lub historii ryzyka. Wycieki danych mogą obejmować przypadkowe oversharowanie wysoce poufnych informacji poza organizację lub kradzież danych ze złośliwymi intencjami. Gdy przypisano zasady ochrony przed utratą danych (DLP, Data Loss Prevention) jako opcję wyzwalania zdarzeń, ten szablon umożliwia rozpoczęcie oceniania w czasie rzeczywistym wykrywania podejrzanych działań i zwiększa prawdopodobieństwo wystąpienia alertów i alertów o poziomie zagrożenia niejawnego programu testów o wyższym poziomie ważności. Priorytet użytkowników określa się w [grupach użytkowników o priorytecie](insider-risk-management-settings.md#priority-user-groups-preview) skonfigurowanych w obszarze ustawień zarządzania ryzykiem w niejawnym programie testów.

Podobnie jak w przypadku szablonu **ogólne** wycieki danych, możesz wybrać zasady DLP w celu wyzwalania wskaźników w zasadach ryzyka niejawnego programu testów o wysokim poziomie ważności dla alertów o wysokim poziomie ważności w organizacji. Podczas korzystania z tego szablonu należy postępować zgodnie z wytycznymi dotyczącymi wycieków danych dotyczącymi zasad DLP podczas tworzenia zasad za pomocą opcji ochrony przed wyciekami danych. Możesz także przypisać wybrane wskaźniki jako wyzwalające zdarzenia zasad. Taka elastyczność i dostosowania ułatwiają zakres zasad tylko do działań objętych wskaźnikami. Ponadto musisz przypisać do  >  zasad grupy użytkowników o priorytecie utworzone w niejawnym programie testów zarządzania ryzykiem **Ustawienia** >  **Priority**.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Wycieki danych przez niezadowoniętych użytkowników (wersja Preview)

Gdy użytkownicy odczuwają streszków w zatrudnieniu, mogą być niechęci, co może zwiększyć prawdopodobieństwo aktywności niejawnego programu testów ryzyka. Ten szablon pozwala na rozpoczęcie oceniania aktywności użytkownika w przypadku zidentyfikowania wskaźnika skojarzonego z niedobraniem. Przykłady obejmują powiadomienia dotyczące poprawy wydajności, oceny niskiej wydajności lub zmiany stanu stanowiska. Wycieki danych niezadowolionych użytkowników mogą obejmować pobieranie plików z usługi SharePoint Online i kopiowanie danych do osobistych usług wiadomości i przechowywania danych w chmurze w pobliżu zdarzeń streszków zatrudnienia.

W przypadku używania tego szablonu musisz również skonfigurować łącznik kadr programu Microsoft 365, aby okresowo importować powiadomienia dotyczące poprawy wydajności, stan przeglądu niskiej wydajności lub informacje o zmianach na poziomie zadań dla użytkowników w organizacji. Zobacz artykuł [Importowanie danych za pomocą łącznika](import-hr-data.md) kadr, aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 kadr dla organizacji.

### <a name="general-security-policy-violations-preview"></a>Naruszenia ogólnych zasad zabezpieczeń (wersja zapoznawcza)

W wielu organizacjach użytkownicy mają uprawnienia do instalowania oprogramowania na swoich urządzeniach lub modyfikowania ustawień urządzeń w celu realizacji swoich zadań. Użytkownicy mogą zainstalować złośliwe oprogramowanie lub wyłączyć ważne funkcje zabezpieczeń, które pomagają chronić informacje na urządzeniach lub w zasobach sieciowych, przypadkowo lub ze złośliwą pomocą. Ten szablon zasad używa alertów zabezpieczeń z usługi Microsoft Defender for Endpoint, aby rozpocząć ocenianie tych działań, wykrywania koncentracji oraz alertów dotyczących tego obszaru ryzyka. Użyj tego szablonu, aby uzyskać szczegółowe informacje na temat naruszeń zasad zabezpieczeń w scenariuszach, gdy użytkownicy mogą mieć historię naruszeń zasad zabezpieczeń, która może być wskaźnikiem ryzyka w niejawnym programie testów.

Aby importować alerty o naruszeniach zabezpieczeń, musisz mieć program Microsoft Defender for Endpoint skonfigurowany w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem w Centrum zabezpieczeń Defender. Aby uzyskać więcej informacji na temat konfigurowania programu Defender for Endpoint na poziomie integracji zarządzania ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="general-patient-data-misuse-preview"></a>Ogólne błędne użycie danych pacjenta (wersja zapoznawcza)

Ochrona danych opieki zdrowotnej i zapobieganie niewłaściwemu użyciu danych osobowych pacjentów jest istotnym problemem dla organizacji w branży opieki zdrowotnej. To niewłaściwe użycie może obejmować poufne wycieki danych do nieautoryzowanych osób, nieuprawnione modyfikacje dokumentacji pacjentów lub kradzież dokumentacji opieki zdrowotnej pacjentów. Zapobieganie tego niewłaściwemu użyciu danych pacjentów przez brak wiedzy, zaniedbanie lub oszustwo przez użytkowników jest również kluczowym elementem w spełnianiu wymagań prawnych określonych w ustawie HIPAA (Health Insurance Portability and Accountability Act) oraz ustawie HITECH (Health Information Technology for Economic and Clinical Health). Obie te ustawy ustanawiają wymagania dotyczące zabezpieczania chronionych informacji o stanie zdrowia pacjentów (PHI, patient protected health information).

Ten szablon zasad umożliwia ocenianie ryzyka dla użytkowników wewnętrznych, którzy wykrywają podejrzane działania skojarzone z rekordami hostowaną w istniejących systemach elektronicznej dokumentacji medycznej (EMR). Wykrywanie dotyczy nieautoryzowanego dostępu, wyświetlania, modyfikowania i eksportowania danych pacjentów. Konieczne będzie skonfigurowanie łącznika (łącznika usługi [microsoft Healthcare](import-healthcare-data.md) lub łącznika [Dorysowanie](import-epic-data.md) w celu obsługi wykrywania dostępu, exekrowania lub udowadniania działań w systemie EMR).

W przypadku używania tego szablonu musisz również skonfigurować łącznik Microsoft 365 HR, aby okresowo importować dane profilu organizacji dla użytkowników w organizacji. Zobacz artykuł Importowanie danych za pomocą łącznika kadr, aby uzyskać instrukcje krok po kroku dotyczące konfigurowania łącznika Microsoft 365 kadr w organizacji.

### <a name="security-policy-violations-by-departing-users-preview"></a>Naruszenia zasad zabezpieczeń przez odchodzące użytkowników (wersja preview)

Odchodzący użytkownicy, niezależnie od tego, czy wychodzą na warunki dodatnie, czy ujemne, mogą być większe ryzyko związane z naruszeniem zasad zabezpieczeń. W celu ochrony przed przypadkowymi lub złośliwymi naruszeniami zabezpieczeń w przypadku odchodujących użytkowników ten szablon zasad używa alertów programu Defender dla punktu końcowego w celu zapewnienia szczegółowych informacji o działaniach związanych z zabezpieczeniami. Te działania obejmują instalowanie przez użytkownika złośliwego oprogramowania lub innych potencjalnie niebezpiecznych aplikacji oraz wyłączanie funkcji zabezpieczeń na swoich urządzeniach. Za pomocą łącznika [usługi Microsoft 365 HR](import-hr-data.md) lub opcji automatycznego monitorowania usuwania konta użytkownika w programie Azure Active Directory organizacji ten szablon rozpoczyna ocenianie wskaźników ryzyka związanych z tymi działaniami zabezpieczeń i ich skorelowania ze stanem zatrudnienia użytkowników.

Aby importować alerty o naruszeniach zabezpieczeń, musisz mieć program Microsoft Defender for Endpoint skonfigurowany w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem w Centrum zabezpieczeń Defender. Aby uzyskać więcej informacji na temat konfigurowania programu Defender for Endpoint na poziomie integracji zarządzania ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych (wersja Preview)

Ochrona przed naruszeniami zabezpieczeń u użytkowników w organizacji może być zależna od ich pozycji, poziomu dostępu do informacji poufnych lub historii ryzyka. Naruszenia zabezpieczeń według priorytetów użytkowników mogą mieć istotny wpływ na krytyczne obszary organizacji, dlatego ten szablon zasad zaczyna oceniać te wskaźniki i używa alertów programu Microsoft Defender dla punktów końcowych, aby zapewnić tym użytkownikom szczegółowe informacje na temat działań związanych z zabezpieczeniami. Te działania mogą obejmować priorytet instalowania przez użytkowników złośliwego oprogramowania lub innych potencjalnie niebezpiecznych aplikacji oraz wyłączania funkcji zabezpieczeń na swoich urządzeniach. Priorytet użytkowników określa się w grupach użytkowników o priorytecie skonfigurowanych w obszarze ustawień zarządzania ryzykiem w niejawnym programie testów.

Aby importować alerty o naruszeniach zabezpieczeń, musisz mieć program Microsoft Defender for Endpoint skonfigurowany w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem w Centrum zabezpieczeń Defender. Aby uzyskać więcej informacji na temat konfigurowania programu Defender for Endpoint na poziomie integracji zarządzania ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). Ponadto musisz przypisać do  >  zasad grupy użytkowników o priorytecie utworzone w niejawnym programie testów zarządzania ryzykiem **Ustawienia** >  **Priority**.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników (wersja Preview)

Użytkownicy, którzy odczuwają stres w zatrudnieniu, mogą stanowić większe ryzyko przypadkowego lub złośliwego naruszenia zasad zabezpieczeń. Te warunki mogą obejmować użytkowników, którzy mają plan poprawy wydajności, stan przeglądu niskiej wydajności lub są obniżani od ich bieżącej pozycji. Ten szablon zasad pozwala uruchamiać ocenianie ryzyka na podstawie tych wskaźników i działań skojarzonych z tymi zdarzeniami dla tych użytkowników.

W przypadku używania tego szablonu musisz również skonfigurować łącznik kadr programu Microsoft 365, aby okresowo importować powiadomienia dotyczące poprawy wydajności, stan przeglądu niskiej wydajności lub informacje o zmianach na poziomie zadań dla użytkowników w organizacji. Zobacz artykuł [Importowanie danych za pomocą łącznika](import-hr-data.md) kadr, aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 kadr dla organizacji.

Aby importować alerty o naruszeniach zabezpieczeń, musisz również skonfigurować program Microsoft Defender for Endpoint w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem w Centrum zabezpieczeń Defender. Aby uzyskać więcej informacji na temat konfigurowania programu Defender for Endpoint na poziomie integracji zarządzania ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>Wymagania wstępne szablonu zasad i wyzwalanie zdarzeń

W zależności od szablonu wybranego dla zasad zarządzania ryzykiem w niejawnym programie testów mogą być różne zdarzenia wyzwalające i wymagania wstępne zasad. Wyzwalanie zdarzeń to wymagania wstępne, które określają, czy użytkownik jest aktywny na podstawie zasad zarządzania ryzykiem w niejawnym programie testów. Jeśli użytkownik został dodany do zasad zarządzania ryzykiem w niejawnym programie testów, ale nie ma zdarzenia wyzwalania, działanie użytkownika nie jest obliczane przez te zasady, chyba że zostanie ręcznie dodany na pulpicie nawigacyjnym Użytkownicy. Wymagania wstępne zasad są elementami wymaganymi, aby zasady odbierały sygnały lub działania niezbędne do oceny ryzyka.

W poniższej tabeli wymieniono zdarzenia wyzwalające oraz wymagania wstępne dla zasad utworzonych na podstawie poszczególnych szablonów zasad zarządzania ryzykiem w niejawnym programie testów:

| **Szablon zasad** | **Wyzwalanie zdarzeń zasad** | **Wymagania wstępne** |
| :------------------ | :--------------------------------- | :---------------- |
| **Kradzież danych przez odchodzące użytkowników** | Wskaźnik daty ponownego przypisania lub zakończenia z łącznika kadr lub Azure Active Directory usunięcia konta | (opcjonalnie) Microsoft 365 hr skonfigurowany na wskaźniki daty zakończenia i ponownego przypisania |
| **Ogólne wycieki danych** | Działanie zasad wycieków danych, które tworzy alert *o* wysokim poziomie ważności lub wbudowane wyzwalacze zdarzeń ex przegnieć | Zasady DLP skonfigurowane dla *alertów o wysokim poziomie ważności* <br><br> LUB <br><br> Dostosowane wskaźniki wyzwalania |
| **Wycieki danych według priorytetowych użytkowników** | Działanie zasad wycieków danych, które tworzy alert *o* wysokim poziomie ważności lub wbudowane wyzwalacze zdarzeń ex przegnieć | Zasady DLP skonfigurowane dla *alertów o wysokim poziomie ważności* <br><br> LUB <br><br> Dostosowane wskaźniki wyzwalania <br><br> Grupy użytkowników o priorytecie skonfigurowane w ustawieniach ryzyka niejawnego programu testów |
| **Wycieki danych przez niezadowoniętych użytkowników** | Wskaźniki poprawy wydajności, niskiej wydajności lub zmiany poziomu zadań z łącznika kadr | Microsoft 365 hr skonfigurowany pod celu ujednowolenia wskaźników |
| **Naruszenia ogólnych zasad zabezpieczeń** | Obrona dzięki mechanizmom kontroli zabezpieczeń lub niechcianym oprogramowaniu wykrytym przez program Microsoft Defender for Endpoint | Aktywna subskrypcja usługi Microsoft Defender for Endpoint <br><br> Integracja programu Microsoft Defender for Endpoint ze Centrum zgodności platformy Microsoft 365 konfiguracją |
| **Ogólne niewłaściwe użycie danych pacjenta** | Obrona mechanizmów kontroli zabezpieczeń przed systemami EMR <br><br> Wskaźniki dopasowywania adresów dla użytkowników i pacjentów z systemów hr | Wskaźniki dostępu do opieki zdrowotnej wybrane w ustawieniach zasad lub w ustawieniach ryzyka niejawnego programu testów <br><br> Microsoft 365 hr skonfigurowany do dopasowywania adresów <br><br> Skonfigurowano łącznik Usługi opieki zdrowotnej firmy Microsoft lub Natłok |
| **Naruszenia zasad zabezpieczeń przez odchodzące użytkowników** | Wskaźniki daty ponownego przypisania lub zakończenia z łącznika kadr lub usuwania Azure Active Directory konta | (opcjonalnie) Microsoft 365 hr skonfigurowany na wskaźniki daty zakończenia i ponownego przypisania <br><br> Aktywna subskrypcja usługi Microsoft Defender for Endpoint <br><br> Integracja programu Microsoft Defender for Endpoint ze Centrum zgodności platformy Microsoft 365 konfiguracją |
| **Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych** | Obrona dzięki mechanizmom kontroli zabezpieczeń lub niechcianym oprogramowaniu wykrytym przez program Microsoft Defender for Endpoint | Aktywna subskrypcja usługi Microsoft Defender for Endpoint <br><br> Integracja programu Microsoft Defender for Endpoint ze Centrum zgodności platformy Microsoft 365 konfiguracją <br><br> Grupy użytkowników o priorytecie skonfigurowane w ustawieniach ryzyka niejawnego programu testów |
| **Naruszenia zasad zabezpieczeń przez niezadowoniętego użytkownika** | Wskaźniki poprawy wydajności, niskiej wydajności lub zmiany poziomu zadań z łącznika kadr | Microsoft 365 hr skonfigurowany pod celu ujednowolenia wskaźników <br><br> Aktywna subskrypcja usługi Microsoft Defender for Endpoint <br><br> Integracja programu Microsoft Defender for Endpoint ze Centrum zgodności platformy Microsoft 365 konfiguracją |

## <a name="prioritize-content-in-policies"></a>Określanie priorytetów zawartości w zasadach

Zasady zarządzania ryzykiem w niejawnym programie testów obsługują określanie wyższego priorytetu zawartości w zależności od tego, gdzie jest przechowywana lub jak jest klasyfikowana. Określenie zawartości jako priorytetu zwiększa ocenę ryzyka dla każdego skojarzonego działania, co z kolei zwiększa prawdopodobieństwo wygenerowania alertu o wysokim poziomie ważności. Jednak niektóre działania w ogóle nie wygenerują alertu, chyba że powiązana zawartość zawiera wbudowane lub niestandardowe typy informacji poufnych lub została określona jako priorytet w zasadach.

Na przykład organizacja ma dedykowaną witrynę SharePoint projektu o wysokim poufnej charakterze. Wycieki danych do informacji w tej SharePoint mogą stanowić zagrożenie dla projektu i mieć istotny wpływ na jego sukces. Dzięki ustalaniu priorytetu tej witryny SharePoint w zasadach wycieków danych oceny ryzyka dla kwalifikujących się działań są automatycznie zwiększane. Takie priorytetyzowanie zwiększa prawdopodobieństwo, że te działania wygenerują alert o ryzyku niejawnego programu testów i podwyższą poziom ważności tego alertu.

Po utworzeniu zasad zarządzania ryzykiem w niejawnym programie testów w kreatorze zasad można wybrać spośród następujących priorytetów:

- **SharePoint witryny:** Każde działanie skojarzone ze wszystkimi typami plików w zdefiniowanych witrynach sieci SharePoint ma przypisany wynik wyższego ryzyka. Użytkownicy konfigurujący zasady i wybierający priorytet witryn programu Share Point mogą SharePoint witryn, do których mają uprawnienia dostępu. Jeśli SharePoint witryny sieci Web nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może później wybrać witryny do tych zasad lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.
- **Typy informacji poufnych**: Każde działanie skojarzone z zawartością zawierającą [typy](sensitive-information-type-entity-definitions.md) informacji poufnych ma przypisany wynik wyższego ryzyka.
- **Etykiety wrażliwości**: Każde działanie skojarzone z zawartością, do [](sensitivity-labels.md) których zastosowano określone etykiety wrażliwości, ma przypisany wyższy poziom ryzyka.

## <a name="sequence-detection-preview"></a>Wykrywanie sekwencji (podgląd)

Ryzykowne działania mogą nie występować jako odizolowane zdarzenia. Te czynniki ryzyka są często częścią większej sekwencji zdarzeń. Sekwencja to grupa co najmniej dwóch działań użytkownika wykonana jedna za drugą, co może stanowić sugerowanie podwyższonego ryzyka. Identyfikowanie tych powiązanych działań jest ważną częścią oceny ogólnego ryzyka. Gdy funkcja wykrywania sekwencji jest włączona na podstawie zasad kradzieży danych lub wycieków danych, na karcie Aktywność użytkowników  w ramach sprawy zarządzania ryzykiem w ramach niejawnego programu testów są wyświetlane szczegółowe informacje z działań dotyczących informacji dotyczących sekwencji. Następujące szablony zasad obsługują wykrywanie sekwencji:

- Kradzież danych przez odchodzące użytkowników
- Ogólne wycieki danych
- Wycieki danych według priorytetowych użytkowników
- Wycieki danych przez niezadowoniętych użytkowników

Te zasady zarządzania ryzykiem w niejawnym programie testów mogą używać określonych wskaźników i kolejności wykrywania poszczególnych kroków w sekwencji ryzyka. Nazwy plików są używane podczas mapowania działań w sekwencji. Te czynniki ryzyka są podzielone na cztery główne kategorie działań:

- **Kolekcja**: Ta kategoria sygnalizuje koncentrację na działaniach pobierania przez użytkowników zasad w zakresie. Niektóre przykładowe działania w tej kategorii to pobieranie plików z witryn SharePoint lub przenoszenie plików do folderu skompresowanego.
- **Ex następnie:** Ta kategoria sygnalizuje koncentrację na działaniach udostępniania lub wyodrębniania dla źródeł wewnętrznych i zewnętrznych przez użytkowników zasad wewnątrz zakresu. Przykładowe działanie w tej kategorii dotyczy wysyłania wiadomości e-mail z załącznikami z Twojej organizacji do adresatów zewnętrznych.
- **Udowadnianie**: Te kategorie sygnalizują koncentrację na maskowania ryzykownych działań przez użytkowników zasad o zasięgu. Niektóre przykładowe działania w tej kategorii to zmiana nazw plików na urządzeniu lub usunięcie lub ocenianie etykiet wrażliwości na SharePoint plikach.
- **Oczyszczanie**: Te kategorie sygnalizuje, że użytkownicy zasad w zakresie skupiają się na działaniach usuwania. Przykładowe działanie w tej kategorii dotyczy usuwania plików z urządzenia.

> [!NOTE]
> Funkcja wykrywania sekwencji używa wskaźników włączonych w ustawieniach globalnych zarządzania ryzykiem w niejawnym programie testów oraz wskaźników wybranych w zasadach. Jeśli odpowiednie wskaźniki nie są zaznaczone, wykrywanie sekwencji nie będzie działać.

Poszczególne ustawienia progowe można dostosowywać dla każdego typu wykrywania sekwencji po skonfigurowaniu zasad. Te ustawienia progowe dostosują alerty na podstawie liczby plików skojarzonych z sekwencją.

Aby dowiedzieć się więcej o zarządzaniu wykrywaniem sekwencji w **widoku Aktywność** użytkowników, zobacz Przypadki zarządzania ryzykiem w niejawnym programie testów [: Działania użytkowników](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Skumulowane wykrywanie exfiltru (podgląd)

Wskaźniki ryzyka niejawnego programu testów pomagają zidentyfikować nietypowe poziomy aktywności ryzyka podczas codziennej oceny dla użytkowników, którzy znajdują się w zakresie zasad ryzyka niejawnego programu testów. W przypadku wykrywania skumulowanego exfiltrowania są używane modele uczenia maszynowego, które ułatwiają zidentyfikowanie działań wykrzykowania wykonywanych przez użytkownika w określonym czasie przekracza normalną ilość wykonywaną przez użytkowników w organizacji w ciągu ostatnich 30 dni w poprzednich 30 dniach w poprzednich przypadkach. Jeśli na przykład użytkownik udostępnił większą ilość plików niż większość użytkowników w ubiegłym miesiącu, to działanie zostanie wykryte i sklasyfikowane jako skumulowane działanie exfiltrowane.

Analitycy i testerzy zarządzania ryzykiem mogą korzystać z szczegółowych informacji dotyczących wykrywania ex exekrów w ramach niejawnego programu testów, które zwykle nie generują alertów, ale znajdują się powyżej tych typowych dla organizacji. Niektóre przykłady mogą odchodzić użytkowników, którzy powoli wychodzą z różnych dni lub gdy użytkownicy wielokrotnie udostępniają dane w wielu kanałach więcej niż zwykle w celu udostępniania danych w Organizacji.  Wyniki wyższych czynników ryzyka są przypisywane do skumulowanych działań ex rozsyłania dla witryn SharePoint, typów informacji [](/microsoft-365/compliance/sensitivity-labels#label-priority-order-matters) poufnych i zawartości z etykietami wrażliwości skonfigurowanymi jako priorytetowa zawartość zasad lub działań obejmujących etykiety o wysokim priorytecie w Microsoft Information Protection.

Funkcja wykrywania exfiltru skumulowanego jest domyślnie włączona w przypadku korzystania z następujących szablonów zasad:

- Kradzież danych przez odchodzące użytkowników
- Ogólne wycieki danych
- Wycieki danych według priorytetowych użytkowników
- Wycieki danych przez niezadowoniętych użytkowników

> [!NOTE]
> Funkcja wykrywania exfiltru skumulowanego korzysta ze wskaźników ex szomów, które są włączone w ustawieniach globalnych zarządzania ryzykiem w niejawnym programie testów i wskaźników ex przekłosów wybranych w zasadach. Dlatego wykrywanie ex ex ex  rozsyłki skumulowanej jest sprawdzane tylko pod celu wykrycia wybranych niezbędnych wskaźników ex przesłoń. Skumulowane działania ekseksywne dla [etykiet wrażliwości](sensitivity-labels.md) skonfigurowanych w zawartości o priorytecie generują oceny wysokiego ryzyka.

Gdy włączono funkcję wykrywania skumulowanego wykradzienia na podstawie zasad kradzieży danych lub wycieków danych, na karcie Aktywność  użytkowników w ramach sprawy zarządzania ryzykiem w ramach niejawnego programu testów są wyświetlane szczegółowe informacje na temat skumulowanych działań exeksorów.

Aby dowiedzieć się więcej o zarządzaniu aktywnością użytkowników, zobacz Przypadki zarządzania [ryzykiem w niejawnym programie testów: Działania użytkowników](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>Kondycja zasad

Stan kondycji zasad pozwala uzyskać szczegółowe informacje o potencjalnych problemach z zasadami zarządzania ryzykiem w niejawnym programie testów. Kolumna Stan na karcie Zasady może ostrzegać o problemach z zasadami, które mogą uniemożliwiać zgłaszane działania użytkowników lub przyczyny nietypowej liczby alertów dotyczących aktywności. Stan kondycji zasad może również potwierdzać, że zasady są dobrej kondycji i nie wymagają uwagi ani zmian w konfiguracji.

W przypadku problemów z zasadami stan kondycji zasad zawiera ostrzeżenia i zalecenia dotyczące powiadomień, które ułatwiają podjąć działania w celu rozwiązania problemów z zasadami. Te powiadomienia mogą pomóc w rozwiązaniu następujących problemów:

- Zasady nieukończonej konfiguracji. Te problemy mogą obejmować brak użytkowników lub grup w procedurach konfiguracji zasad lub inne niepełne kroki konfiguracji zasad.
- Zasady z problemami z konfiguracją wskaźnika. Wskaźniki są ważną częścią każdej zasady. Jeśli wskaźniki nie zostały skonfigurowane lub zaznaczono zbyt mało wskaźników, zasady mogą nie oceniać ryzykownych działań zgodnie z oczekiwaniami.
- Wyzwalacze zasad nie działają lub wymagania wyzwalacza zasad nie są poprawnie skonfigurowane. Funkcje zasad mogą być zależne od innych usług lub wymagań konfiguracyjnych w celu skutecznego wykrycia zdarzeń wyzwalających w celu aktywowania przypisania wyników ryzyka do użytkowników zasad. Te zależności mogą obejmować problemy z konfiguracją łączników, udostępnianiem alertów programu Microsoft Defender for Endpoint lub ustawieniami konfiguracji zasad ochrony przed utratą danych.
- Limity głośności są bliski limitom lub ich limitom. W zasadach zarządzania ryzykiem w niejawnym programie testów jest Microsoft 365 wiele usług i punktów końcowych do agregowania sygnałów aktywności ryzyka. W zależności od liczby użytkowników w zasadach limity pojemności mogą opóźnić identyfikowanie i raportowanie działań ryzyka. Więcej informacji o tych limitach zawiera sekcja Limity szablonów zasad w tym artykule.

Aby szybko wyświetlić stan kondycji zasad, przejdź do karty Zasady i kolumny Stan. Poniżej przedstawiono następujące opcje stanu kondycji zasad dla poszczególnych zasad:

- W dobrej kondycji: z zasadami nie zostały zidentyfikowane żadne problemy.
- Rekomendacje: Istnieją pewne problemy z zasadami, które mogą uniemożliwiać oczekiwany sposób działania zasad.
- Ostrzeżenia: Istnieją problemy z zasadami, które uniemożliwiają zidentyfikowanie ryzykownych działań.

Aby uzyskać więcej szczegółowych informacji na temat jakichkolwiek zaleceń lub ostrzeżeń, wybierz zasady na **karcie** Zasady, aby otworzyć kartę szczegółów zasad. Więcej informacji na temat zaleceń i ostrzeżeń, w tym wskazówki dotyczące sposobu rozwiązania tych problemów, zostaną wyświetlone w sekcji Powiadomienia na karcie szczegółów.

![Kondycja zasad zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Wiadomości z powiadomieniami

Skorzystaj z poniższej tabeli, aby dowiedzieć się więcej o zaleceniach i powiadomieniach ostrzegawczych oraz akcjach do podjęcia w celu rozwiązania potencjalnych problemów.

|**Wiadomości z powiadomieniami**|**Szablony zasad**|**Przyczyny/ Wypróbuj tę akcję, aby rozwiązać problem**|
|:------------------------|:-------------------|:---------------------------|
| Zasady nie przydzielają wyników ryzyka do działania | Wszystkie szablony zasad | Być może trzeba będzie przejrzeć zakres zasad i wyzwolić konfigurację zdarzenia, tak aby zasady mógły przypisywać oceny ryzyka do działań. <br><br> 1. Przejrzyj użytkowników wybranych dla zasad. Jeśli wybrano kilku użytkowników, możesz wybrać dodatkowych użytkowników. <br> 2. Jeśli używasz łącznika hr, sprawdź, czy łącznik kadr wysyła prawidłowe dane. <br> 3. Jeśli jako zdarzenia wyzwalania używasz zasad DLP, sprawdź konfigurację zasad DLP, aby się upewnić, że są one skonfigurowane do używania w tych zasadach. <br> 4. Aby zapoznać się z zasadami naruszenia zabezpieczeń, zapoznaj się z informacjami o stanie weryfikacji alertu programu Microsoft Defender for Endpoint wybranym w ustawieniach ryzyka niejawnego programu testów i > inteligentnych wykrywania. Upewnij się, że filtr alertu nie jest zbyt wąski. |
| W zasadach nie zostały wygenerowane żadne alerty | Wszystkie szablony zasad | Warto przejrzeć konfigurację zasad, aby przeanalizować wynik działania, dla którego zależy Twoje działanie. <br><br> 1. Upewnij się, że zostały wybrane wskaźniki, których wynik chcesz uzyskać. Im więcej wskaźników jest zaznaczonych, tym więcej działań jest przypisanych wyników ryzyka. <br> 2. Przejrzyj dostosowania progowe zasad. Jeśli wybrane progi nie są zgodne z tolerancją dla ryzyka organizacji, dostosuj ustawienia tak, aby alerty były tworzone na podstawie preferowanych progów. <br> 3. Przejrzyj użytkowników i grupy wybrane dla zasad. Upewnij się, że wybrano wszystkich odpowiednich użytkowników i grupy. <br> 4. W przypadku zasad naruszenia zabezpieczeń potwierdź, że wybrano stan alertu, który ma być punktem wyników dla alertów programu Microsoft Defender dla punktu końcowego w inteligentnych wykrywaniech w ustawieniach.|
| W tych zasadach nie są uwzględniani użytkownicy ani grupy | Wszystkie szablony zasad | Do zasad nie są przypisani użytkownicy ani grupy. <br><br> Edytuj zasady i wybierz użytkowników lub grupy zasad. |
| W przypadku tych zasad nie zaznaczono żadnych wskaźników | Wszystkie szablony zasad | Wskaźniki nie zostały wybrane dla zasad <br><br> Edytuj zasady i wybierz wskaźniki odpowiednich zasad. |
| W tych zasadach nie są uwzględniane żadne grupy użytkowników o priorytecie | - Wycieki danych według priorytetowych użytkowników <br> - Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych | Grupy użytkowników o priorytecie nie są przypisane do zasad. <br><br> Skonfiguruj priorytety grup użytkowników w ustawieniach zarządzania ryzykiem w niejawnym programie testów i przypisz do zasad grupy użytkowników o priorytecie. |
| Dla tych zasad nie zaznaczono zdarzenia wyzwalania | Wszystkie szablony zasad | Zdarzenie wyzwalające nie jest skonfigurowane dla zasad <br><br> Wyniki ryzyka nie zostaną przypisane do działań użytkownika, dopóki nie edytujesz zasad i nie wybierzesz zdarzenia wyzwalające. |
| Łącznik kadr nie jest skonfigurowany lub nie działa zgodnie z oczekiwaniami | - Kradzież danych przez odchodzącego użytkownika <br> - Naruszenia zasad zabezpieczeń przez odchodzącego użytkownika <br> - Wycieki danych przez niezadowoniętych użytkowników <br> - Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników | Występuje problem z łącznikiem kadr. <br><br> 1. Jeśli używasz łącznika hr, sprawdź, czy łącznik kadr wysyła prawidłowe dane <br><br> LUB <br><br> 2. Wybierz usunięte konto usługi Azure AD wyzwalające zdarzenie. |
| Nie są podłączone żadne urządzenia | - Kradzież danych przez odchodzące użytkowników <br> - Ogólne wycieki danych <br> - Wycieki danych przez niezadowoniętych użytkowników <br> - Wycieki danych według priorytetowych użytkowników | Wskaźniki urządzeń są zaznaczone, ale nie ma żadnych urządzeń podłączonych do Microsoft 365 <br><br> Sprawdź, czy urządzenia są podłączone i spełniają wymagania. |
| Łącznik kadr nie przesłał ostatnio danych | - Kradzież danych przez odchodzącego użytkownika <br> - Naruszenia zasad zabezpieczeń przez odchodzącego użytkownika <br> - Wycieki danych przez niezadowoniętych użytkowników <br> - Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników | Łącznik kadr nie zaimportował danych w ciągu ponad 7 dni. <br><br> Sprawdź, czy łącznik KADR jest prawidłowo skonfigurowany i wysyła dane. |
| Nie możemy w tej chwili sprawdzić stanu łącznika kadr. Sprawdź ponownie później | - Kradzież danych przez odchodzącego użytkownika <br> - Naruszenia zasad zabezpieczeń przez odchodzącego użytkownika <br> - Wycieki danych przez niezadowoniętych użytkowników <br> - Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników | Rozwiązanie do zarządzania ryzykiem w niejawnym programie testów nie może sprawdzać stanu łącznika kadr. <br><br> Sprawdź, czy łącznik kadr jest prawidłowo skonfigurowany i wysyła dane, lub wróć i sprawdź stan zasad.  |
| Zasady DLP nie są wybrane jako zdarzenie wyzwalające | - Ogólne wycieki danych <br> - Wycieki danych według priorytetowych użytkowników | Zasady DLP nie zostały wybrane jako zdarzenie wyzwalające lub wybrane zasady DLP zostały usunięte. <br><br> Przeedytuj zasady i wybierz aktywne zasady DLP lub "Użytkownik wykonuje działanie ekscytowania" jako zdarzenie wyzwalające w konfiguracji zasad. |
| Zasady DLP używane w tych zasadach są wyłączone | - Ogólne wycieki danych <br> - Wycieki danych według priorytetowych użytkowników | Zasady DLP używane w tych zasadach są wyłączone. <br><br> 1. Włącz zasady DLP przypisane do tych zasad. <br><br> LUB <br><br> 2. Edytuj te zasady, a następnie wybierz nowe zasady DLP lub "Użytkownik wykonuje działanie ex ex przeszłego" jako zdarzenie wyzwalające w konfiguracji zasad. |
| Zasady DLP nie spełniają wymagań | - Ogólne wycieki danych <br> - Wycieki danych według priorytetowych użytkowników | Zasady DLP używane jako wyzwalanie zdarzeń należy skonfigurować do generowania alertów o wysokim poziomie ważności. <br><br>  1. Edytuj zasady DLP, aby przypisać odpowiednie alerty jako *o wysokim poziomie ważności*. <br><br> LUB <br><br> 2. Edytuj te zasady, a następnie wybierz *pozycję Użytkownik wykonuje działanie ex ex przewłaszania* jako zdarzenie wyzwalające. |
| Twoja organizacja nie ma subskrypcji programu Microsoft Defender for Endpoint | - Naruszenia ogólnych zasad zabezpieczeń <br> - Naruszenia zasad zabezpieczeń przez odchodzące użytkowników <br> - Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników <br> - Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych | Nie wykryto aktywnej subskrypcji usługi Microsoft Defender for Endpoint w organizacji. <br><br> Do czasu dodania subskrypcji usługi Microsoft Defender for Endpoint te zasady nie będą przypisywać wyników ryzyka do aktywności użytkowników. |
| Alerty programu Microsoft Defender dla punktu końcowego nie są udostępniane centrum zgodności | - Naruszenia ogólnych zasad zabezpieczeń <br> - Naruszenia zasad zabezpieczeń przez odchodzące użytkowników <br> - Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników <br> - Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych | Alerty programu Microsoft Defender dla punktu końcowego nie są udostępniane centrum zgodności. <br><br> Konfigurowanie udostępniania alertów programu Microsoft Defender dla punktu końcowego. |
| Zbliżasz się do maksymalnego limitu liczby użytkowników aktywnie zdobywanych dla tego szablonu zasad. | Wszystkie szablony zasad | Każdy szablon zasad ma maksymalną liczbę użytkowników w zakresie. Zobacz szczegóły sekcji dotyczącej limitu szablonów. <br><br> Przejrzyj informacje o użytkownikach na karcie Użytkownicy i usuń wszystkich użytkowników, którzy nie muszą już być sprawdzani. |
| Wyzwalanie zdarzenia występuje wielokrotnie dla ponad 15% użytkowników tych zasad. | Wszystkie szablony zasad | Dostosuj zdarzenie wyzwalające, aby zmniejszyć liczbę osób uwzględnianych w zakresie zasad. |

## <a name="policy-template-limits"></a>Limity szablonów zasad

Szablony zasad zarządzania ryzykiem w niejawnym programie testów korzystają z limitów w celu zarządzania ilością i szybkością przetwarzania danych w ramach działań ryzyka użytkownika oraz o tym, jak ten proces jest zintegrowany z obsługą Microsoft 365 internetowych. Każdy szablon zasad zawiera maksymalną liczbę użytkowników, do których można aktywnie przypisywać oceny ryzyka związane z zasadami, które mogą wspierać oraz skutecznie przetwarzać i raportować działania związane z ryzykiem. Użytkownicy o zakresie to użytkownicy wyzwalający zdarzenia zasad.

Limit dla poszczególnych zasad jest obliczany na podstawie całkowitej liczby unikatowych użytkowników, którzy otrzymują wyniki ryzyka według typu szablonu zasad. Jeśli liczba użytkowników dla typu szablonu zasad jest niemal większa niż limit użytkowników, wydajność zasad zostanie zmniejszona. Aby wyświetlić bieżącą liczbę użytkowników zasad, przejdź do karty Zasady i kolumny Użytkownicy w zakresie. Dla każdego szablonu zasad może być maksymalnie pięć zasad. Te maksymalne limity mają zastosowanie do użytkowników we wszystkich zasadach korzystających z danego szablonu zasad.

Skorzystaj z poniższej tabeli, aby określić maksymalną liczbę użytkowników w zakresie obsługiwanych dla poszczególnych szablonów zasad:

|**Szablon zasad**|**Bieżąca maksymalna liczba użytkowników w zakresie**|
|:------------------|:--------------------------------|
| Ogólny wyciek danych | 15,000 |
| Wyciek danych przez niezadowoniętych użytkowników | 7,500 |
| Wyciek danych według priorytetowych użytkowników | 1,000 |
| Kradzież danych przez odchodzące użytkowników | 20,000 |
| Naruszenia ogólnych zasad zabezpieczeń | 1,000 |
| Ogólne niewłaściwe użycie danych pacjenta | 5,000 |
| Naruszenie zasad zabezpieczeń przez użytkowników priorytetowych | 1,000 |
| Naruszenia zasad zabezpieczeń przez odchodzące użytkowników | 15,000 |
| Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników | 7,500 |

## <a name="create-a-new-policy"></a>Tworzenie nowych zasad

Aby utworzyć nowe zasady zarządzania ryzykiem w niejawnym programie testów, użyj kreatora zasad  w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów w Centrum zgodności platformy Microsoft 365.

Wykonaj następujące czynności, aby utworzyć nowe zasady:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę** Zasady.
2. Wybierz **pozycję Utwórz zasady** , aby otworzyć kreatora zasad.
3. Na stronie **Szablon zasad** wybierz kategorię zasad, a następnie wybierz szablon nowych zasad. Te szablony składa się z warunków i wskaźników definiujące działania ryzyka, które mają zostać wykrywane i badane. Przejrzyj wymagania wstępne szablonu, wyzwalanie zdarzeń i wykrytych działań, aby potwierdzić, że ten szablon zasad spełnia Twoje wymagania.

    > [!IMPORTANT]
    > Niektóre szablony zasad mają wymagania wstępne, które muszą zostać skonfigurowane, aby zasady tworzyły odpowiednie alerty. Jeśli nie skonfigurowano wymagań wstępnych dotyczących odpowiednich zasad, zobacz **krok 4** powyżej.

4. Wybierz przycisk **Dalej**, aby kontynuować.
5. Na **stronie Nazwa i opis** wypełnij następujące pola:
    - **Nazwa (wymagany)**: Wprowadź przyjazną nazwę zasad. Po utworzeniu zasad nie można zmienić tej nazwy.
    - **Opis (opcjonalnie)**: Wprowadź opis zasad.

6. Wybierz przycisk **Dalej**, aby kontynuować.
7. Na stronie  Użytkownicy i grupy wybierz pozycję Uwzględnij wszystkich użytkowników i grupy lub  Uwzględnij konkretnych użytkowników i grupy, aby określić użytkowników lub grupy, które mają być uwzględnione w zasadach, lub jeśli został wybrany szablon priorytetowy oparty na użytkownikach. wybierz **pozycję Dodaj lub edytuj grupy użytkowników o priorytecie**. Wybranie **opcji Uwzględnij wszystkich użytkowników** i grupy spowoduje uruchomienie zdarzeń dla wszystkich użytkowników i grup w organizacji w celu rozpoczęcia przypisywania ocen ryzyka dla zasad. Wybranie **opcji Uwzględnij konkretnych użytkowników i** grupy umożliwia określenie użytkowników i grup, którym mają zostać przypisane zasady. Konta użytkowników gości nie są obsługiwane.
8. Wybierz przycisk **Dalej**, aby kontynuować.
9. Na **stronie Zawartość do priorytetyzowania** możesz (w razie potrzeby) przypisywać źródła do priorytetu, co zwiększa prawdopodobieństwo wygenerowania alertów o wysokim poziomie ważności dla tych źródeł. Wybierz jedną z następujących opcji:

    - **Jako priorytetową zawartość chcę SharePoint,** etykiety wrażliwości i/lub informacje poufne. Zaznaczenie tej opcji umożliwi skonfigurowanie tych kanałów na stronach szczegółów w kreatorze.
    - **Nie chcę teraz określać** priorytetu zawartości (będzie można to zrobić po utworzeniu zasad).. Zaznaczenie tej opcji spowoduje pominięcie stron szczegółów kanału w kreatorze.

10. Wybierz przycisk **Dalej**, aby kontynuować.

11. Jeśli w poprzednim kroku jako priorytet zostaną określone witryny programu **SharePoint,** etykiety wrażliwości i/lub typy informacji poufnych, zostaną wyświetlonych strony szczegółów witryn sieci *SharePoint**, typów* informacji poufnych i etykiet *wrażliwości.* Za pomocą tych stron szczegółów zdefiniuj SharePoint, poufne typy informacji i etykiety wrażliwości, aby określić priorytety zasad.

    - **SharePoint witryny**: Wybierz pozycję Dodaj witrynę SharePoint **,** a następnie SharePoint witryny, do których masz dostęp i chcesz określić priorytety. Na przykład *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Typ informacji poufnych**: Wybierz **pozycję Dodaj typ informacji poufnych** i wybierz typy wrażliwości, dla których chcesz określić priorytety. Na przykład *"Numer konta bankowego w Stanach Zjednoczonych"* i *"Numer karty kredytowej"*.
    - **Etykiety wrażliwości**: Wybierz **pozycję Dodaj etykietę wrażliwości** i wybierz etykiety, dla których chcesz określić priorytety. Na przykład *"Poufne"* i *"Tajna"*.

    >[!NOTE]
    >Użytkownicy konfigurujący zasady i wybierający priorytet witryn programu Share Point mogą SharePoint witryn, do których mają uprawnienia dostępu. Jeśli SharePoint witryny sieci Web nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może później wybrać witryny do tych zasad lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.

12. Wybierz przycisk **Dalej**, aby kontynuować.
13. Jeśli wybrano ogólne wycieki  danych lub wycieki danych  według szablonów priorytetów użytkowników, na stronie Wyzwalacze tej zasady znajdziesz opcje niestandardowego wyzwalania zdarzeń i wskaźników zasad. Możesz wybrać zasady DLP lub wskaźniki służące do wyzwalania zdarzeń, które powodują przypisanie użytkowników do zakresu zasad oceniania aktywności. Jeśli wybierzesz opcję zdarzeń Zasady ochrony przed utratą danych **(DLP, Data Loss Prevention** ), wyzwalająco zdarzenie, musisz wybrać zasady DLP z listy rozwijanej zasad DLP, aby włączyć wskaźniki wyzwalania zasad DLP dla tych zasad zarządzania ryzykiem w niejawnym programie testów. Jeśli wybierzesz opcję **zdarzenia** wyzwolone przez użytkownika, należy wybrać jeden lub więcej ze wskaźników na liście dla zdarzenia wyzwalania zasad.
    >[!IMPORTANT]
    >Jeśli nie możesz wybrać wskaźnika na liście, jest on włączony w Twojej organizacji. Aby udostępnić je w celu wybrania i przypisania do zasad,  >  włącz wskaźniki w zarządzaniu ryzykiem w niejawnym programie testów **Ustawienia** >  **Wskaźniki zasad**.

    Jeśli wybrano inne szablony zasad, niestandardowe zdarzenia wyzwalania nie są obsługiwane. Mają zastosowanie wbudowane zasady wyzwalające zdarzenia i przejdź do kroku 23 bez definiowania atrybutów zasad.

14. Wybierz przycisk **Dalej**, aby kontynuować.
15. Jeśli wybrano szablony Ogólne wycieki danych lub Wycieki  danych według szablonów priorytetów użytkowników i wybrano użytkownika, który wykonuje aktywność **exeksy** i skojarzone wskaźniki, możesz wybrać niestandardowe lub domyślne progi dla wskaźnika wyzwalania zdarzeń, które zostały wybrane. Wybierz pozycję **Użyj progów domyślnych (zalecane)** lub **Użyj niestandardowych progów zdarzeń wyzwalających**.
16. Wybierz przycisk **Dalej**, aby kontynuować.
17. Jeśli wybrano pozycję Użyj niestandardowych progów dla zdarzeń wyzwalających **, dla** każdego wskaźnika wyzwalania zdarzenia wybranego w kroku 13 wybierz odpowiedni poziom, aby wygenerować odpowiedni poziom alertów aktywności.
18. Wybierz przycisk **Dalej**, aby kontynuować.
19. Na **stronie Wskaźniki zasad** zobaczysz wskaźniki zdefiniowane  >  przez Ciebie jako dostępne na [](insider-risk-management-settings.md#indicators) stronie Ustawienia ryzyka niejawnego programu **testów.** Wybierz wskaźniki, które chcesz zastosować do zasad.

    > [!IMPORTANT]
    > Jeśli nie można wybrać wskaźników na tej stronie, musisz wybrać wskaźniki, które chcesz włączyć dla wszystkich zasad. Możesz użyć **przycisku Włącz**  >  wskaźniki w kreatorze lub wybrać wskaźniki na stronie Zarządzanie ryzykiem w niejawnym programie testów **Ustawienia** >  **Wskaźniki polityki**.

    Jeśli wybrano co najmniej jeden wskaźnik *Office* urządzenia, wybierz odpowiedni  **wynik ryzyka.** Wyniki ryzyka mają zastosowanie tylko do wybranych wskaźników.
    Jeśli wybrano szablon zasad Kradzież  danych lub Wycieki danych, wybierz jedną lub więcej metod wykrywania  sekwencji oraz skumulowaną metodę wykrywania **exeksymu**, aby zastosować ją do zasad.

20. Wybierz przycisk **Dalej**, aby kontynuować.
21. Na **stronie Zdecyduj, czy** chcesz używać domyślnych, czy niestandardowych progów wskaźników wybierz progi niestandardowe lub domyślne dla wybranych wskaźników zasad. Wybierz pozycję **Użyj progów domyślnych dla wszystkich wskaźników** lub Określ **progi niestandardowe** dla wskaźników wybranych zasad. Jeśli wybrano opcję Określ progi niestandardowe, wybierz odpowiedni poziom, aby wygenerować odpowiedni poziom alertów aktywności dla każdego wskaźnika zasad.
22. Wybierz przycisk **Dalej**, aby kontynuować.
23. Na **stronie Recenzja** sprawdź ustawienia wybrane dla zasad oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz **pozycję Edytuj** , aby zmienić dowolne wartości zasad, lub wybierz pozycję **Prześlij,** aby utworzyć i aktywować zasady.

## <a name="update-a-policy"></a>Aktualizowanie zasad

Aby zaktualizować istniejące zasady zarządzania ryzykiem w niejawnym programie testów, użyj kreatora  zasad w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów w Centrum zgodności platformy Microsoft 365.

Aby zarządzać istniejącymi zasadami, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę** Zasady.
2. Na pulpicie nawigacyjnym zasad wybierz zasady, które chcesz zarządzać.
3. Na stronie szczegółów zasad wybierz pozycję **Edytuj zasady**
4. W kreatorze zasad nie można edytować następujących plików:
    - **Szablon zasad**: Szablon służy do definiowania typów wskaźników ryzyka monitorowanych przez zasady.
    - **Nazwa**: przyjazna nazwa zasad
5. Na **stronie Nazwa i opis** zaktualizuj opis zasad **w polu Opis** .
6. Wybierz przycisk **Dalej**, aby kontynuować.
7. Na stronie  Użytkownicy i grupy wybierz pozycję Uwzględnij wszystkich użytkowników i grupy lub  Uwzględnij konkretnych użytkowników i grupy, aby określić użytkowników lub grupy, które mają być uwzględnione w zasadach, lub jeśli został wybrany szablon priorytetowy oparty na użytkownikach. wybierz **pozycję Dodaj lub edytuj grupy użytkowników o priorytecie**. Wybranie **opcji Uwzględnij wszystkich użytkowników** i grupy spowoduje uruchomienie zdarzeń dla wszystkich użytkowników i grup w organizacji w celu rozpoczęcia przypisywania ocen ryzyka dla zasad. Wybranie **opcji Uwzględnij konkretnych użytkowników i** grupy umożliwia określenie użytkowników i grup, którym mają zostać przypisane zasady. Konta użytkowników gości nie są obsługiwane.
8. Wybierz przycisk **Dalej**, aby kontynuować.
9. Na **stronie Zawartość do priorytetyzowania** możesz (w razie potrzeby) przypisywać źródła do priorytetu, co zwiększa prawdopodobieństwo wygenerowania alertów o wysokim poziomie ważności dla tych źródeł. Wybierz jedną z następujących opcji:

    - **Jako priorytetową zawartość chcę SharePoint,** etykiety wrażliwości i/lub informacje poufne. Zaznaczenie tej opcji umożliwi skonfigurowanie tych kanałów na stronach szczegółów w kreatorze.
    - **Nie chcę teraz określać** priorytetu zawartości (będzie można to zrobić po utworzeniu zasad).. Zaznaczenie tej opcji spowoduje pominięcie stron szczegółów kanału w kreatorze.

10. Wybierz przycisk **Dalej**, aby kontynuować.

11. Jeśli w poprzednim kroku jako priorytet zostaną określone witryny programu **SharePoint,** etykiety wrażliwości i/lub typy informacji poufnych, zostaną wyświetlonych strony szczegółów witryn sieci *SharePoint**, typów* informacji poufnych i etykiet *wrażliwości.* Za pomocą tych stron szczegółów zdefiniuj SharePoint, poufne typy informacji i etykiety wrażliwości, aby określić priorytety zasad.

    - **SharePoint witryny**: Wybierz pozycję Dodaj witrynę SharePoint **,** a następnie SharePoint witryny, do których masz dostęp i chcesz określić priorytety. Na przykład *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Typ informacji poufnych**: Wybierz **pozycję Dodaj typ informacji poufnych** i wybierz typy wrażliwości, dla których chcesz określić priorytety. Na przykład *"Numer konta bankowego w Stanach Zjednoczonych"* i *"Numer karty kredytowej"*.
    - **Etykiety wrażliwości**: Wybierz **pozycję Dodaj etykietę wrażliwości** i wybierz etykiety, dla których chcesz określić priorytety. Na przykład *"Poufne"* i *"Tajna"*.

    >[!NOTE]
    >Użytkownicy konfigurujący zasady i wybierający priorytet witryn programu Share Point mogą SharePoint witryn, do których mają uprawnienia dostępu. Jeśli SharePoint witryny sieci Web nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może później wybrać witryny do tych zasad lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.

12. Wybierz przycisk **Dalej**, aby kontynuować.
13. Jeśli wybrano ogólne wycieki  danych lub wycieki danych  według szablonów priorytetów użytkowników, na stronie Wyzwalacze tej zasady znajdziesz opcje niestandardowego wyzwalania zdarzeń i wskaźników zasad. Możesz wybrać zasady DLP lub wskaźniki służące do wyzwalania zdarzeń, które powodują przypisanie użytkowników do zakresu zasad oceniania aktywności. Jeśli wybierzesz opcję zdarzeń Zasady ochrony przed utratą danych **(DLP, Data Loss Prevention** ), wyzwalająco zdarzenie, musisz wybrać zasady DLP z listy rozwijanej zasad DLP, aby włączyć wskaźniki wyzwalania zasad DLP dla tych zasad zarządzania ryzykiem w niejawnym programie testów. Jeśli wybierzesz opcję **zdarzenia** wyzwolone przez użytkownika, należy wybrać jeden lub więcej ze wskaźników na liście dla zdarzenia wyzwalania zasad.
    >[!IMPORTANT]
    >Jeśli nie możesz wybrać wskaźnika na liście, jest on włączony w Twojej organizacji. Aby udostępnić je w celu wybrania i przypisania do zasad,  >  włącz wskaźniki w zarządzaniu ryzykiem w niejawnym programie testów **Ustawienia** >  **Wskaźniki zasad**.

    Jeśli wybrano inne szablony zasad, niestandardowe zdarzenia wyzwalania nie są obsługiwane. Mają zastosowanie wbudowane zasady wyzwalające zdarzenia i przejdź do kroku 23 bez definiowania atrybutów zasad.

14. Wybierz przycisk **Dalej**, aby kontynuować.
15. Jeśli wybrano szablony Ogólne wycieki danych lub Wycieki  danych według szablonów priorytetów użytkowników i wybrano użytkownika, który wykonuje aktywność **exeksy** i skojarzone wskaźniki, możesz wybrać niestandardowe lub domyślne progi dla wskaźnika wyzwalania zdarzeń, które zostały wybrane. Wybierz pozycję **Użyj progów domyślnych (zalecane)** lub **Użyj niestandardowych progów zdarzeń wyzwalających**.
16. Wybierz przycisk **Dalej**, aby kontynuować.
17. Jeśli wybrano pozycję Użyj niestandardowych progów dla zdarzeń wyzwalających **, dla** każdego wskaźnika wyzwalania zdarzenia wybranego w kroku 13 wybierz odpowiedni poziom, aby wygenerować odpowiedni poziom alertów aktywności.
18. Wybierz przycisk **Dalej**, aby kontynuować.
19. Na **stronie Wskaźniki zasad** zobaczysz wskaźniki zdefiniowane  >  przez Ciebie jako dostępne na [](insider-risk-management-settings.md#indicators) stronie Ustawienia ryzyka niejawnego programu **testów.** Wybierz wskaźniki, które chcesz zastosować do zasad.

    > [!IMPORTANT]
    > Jeśli nie można wybrać wskaźników na tej stronie, musisz wybrać wskaźniki, które chcesz włączyć dla wszystkich zasad. Możesz użyć **przycisku Włącz**  >  wskaźniki w kreatorze lub wybrać wskaźniki na stronie Zarządzanie ryzykiem w niejawnym programie testów **Ustawienia** >  **Wskaźniki polityki**.

    Jeśli wybrano co najmniej jeden wskaźnik *Office* urządzenia, wybierz odpowiedni  **wynik ryzyka.** Wyniki ryzyka mają zastosowanie tylko do wybranych wskaźników.
    Jeśli wybrano szablon zasad Kradzież  danych lub Wycieki danych, wybierz jedną lub więcej metod wykrywania  sekwencji oraz skumulowaną metodę wykrywania **exeksymu**, aby zastosować ją do zasad.

20. Wybierz przycisk **Dalej**, aby kontynuować.
21. Na **stronie Zdecyduj, czy** chcesz używać domyślnych, czy niestandardowych progów wskaźników wybierz progi niestandardowe lub domyślne dla wybranych wskaźników zasad. Wybierz pozycję **Użyj progów domyślnych dla wszystkich wskaźników** lub Określ **progi niestandardowe** dla wskaźników wybranych zasad. Jeśli wybrano opcję Określ progi niestandardowe, wybierz odpowiedni poziom, aby wygenerować odpowiedni poziom alertów aktywności dla każdego wskaźnika zasad.
22. Wybierz przycisk **Dalej**, aby kontynuować.
23. Na **stronie Recenzja** sprawdź ustawienia wybrane dla zasad oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz **pozycję Edytuj** , aby zmienić dowolne wartości zasad, lub wybierz pozycję **Prześlij,** aby utworzyć i aktywować zasady.

## <a name="copy-a-policy"></a>Kopiowanie zasad

Może być konieczne utworzenie nowych zasad, które będą podobne do istniejących, ale wymagają tylko kilku zmian w konfiguracji. Zamiast tworzyć nowe zasady od podstaw, możesz skopiować istniejące zasady, a następnie zmodyfikować obszary, które muszą zostać zaktualizowane w nowych zasadach.

Wykonaj następujące czynności, aby skopiować istniejące zasady:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę** Zasady.
2. Na pulpicie nawigacyjnym zasad wybierz zasady, które chcesz skopiować.
3. Na stronie szczegółów zasad wybierz pozycję Kopiuj.
4. W kreatorze zasad nazwij nowe zasady i zaktualizuj ich konfigurację zgodnie z potrzebami.

## <a name="immediately-start-scoring-user-activity"></a>Natychmiast rozpocznij ocenianie aktywności użytkownika

Mogą wystąpić sytuacje, w których trzeba od razu rozpocząć przypisywanie ocen ryzyka użytkownikom z zasadami ryzyka niejawnego programu testów, którzy nie muszą dzielić się informacjami o przepływie pracy zarządzania ryzykiem w niejawnym programie testów. Użyj  instrukcji Rozpocznij ocenianie wyników dla użytkowników  na karcie Zasady, aby ręcznie dodać użytkownika (lub użytkowników) do jednej lub kilku zasad ryzyka niejawnego programu testów przez określony czas, natychmiast rozpocząć przypisywanie wyników ryzyka do jego aktywności oraz pominąć wymaganie, aby użytkownik miał wskaźnik wyzwalania (taki jak dopasowanie zasad DLP). Możesz również dodać powód dodania użytkownika do zasad, które będą wyświetlane na osi czasu aktywności użytkowników. Użytkownicy dodani ręcznie do zasad są wyświetlani na pulpicie nawigacyjnym Użytkownicy, a alerty są tworzone w przypadku, gdy działanie spełnia progi alertów zasad.

Niektóre scenariusze, w których możesz chcieć od razu rozpocząć ocenianie działań użytkowników:

- Gdy użytkownicy zostaną zidentyfikowani w przypadku obaw o ryzyko i chcesz od razu rozpocząć przypisywanie wyników ryzyka do ich działań w przypadku jednej lub większej liczby zasad
- W przypadku zdarzenia, które może wymagać natychmiastowego rozpoczęcia przypisywania ocen ryzyka do działań związanych z użytkownikami w przypadku jednej lub większej liczby zasad
- Jeśli jeszcze nie skonfigurowano łącznika kadr, ale chcesz rozpocząć przypisywanie wyników ryzyka do działań użytkownika dla zdarzeń HR, przesyłając plik .csv dla użytkowników

> [!NOTE]
> Może mi potrwać kilka godzin, aby nowi ręcznie dodani użytkownicy pojawili się na **pulpicie nawigacyjnym** Użytkownicy. Wyświetlanie działań dla tych użytkowników w ciągu ostatnich 90 dni może potrwać do 24 godzin. Aby wyświetlić działania dotyczące ręcznie dodanych użytkowników, przejdź do karty  Użytkownicy i wybierz użytkownika na pulpicie nawigacyjnym Użytkownicy, a następnie  otwórz kartę Aktywność użytkownika w okienku szczegółów.

Aby ręcznie rozpocząć ocenianie aktywności użytkowników w co najmniej jednej zasadach zarządzania ryzykiem w niejawnym programie testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę** Zasady.
2. Na pulpicie nawigacyjnym zasad wybierz zasady, do których chcesz dodać użytkowników.
3. Wybierz **pozycję Rozpocznij aktywność oceniania dla użytkowników**.
4. W polu **Przyczyna** w **okienku Dodawanie** użytkowników do wielu zasad dodaj przyczynę dodawania użytkowników.
5. W polu **To powinno trwać (wybierz od 5 do 30 dni)** zdefiniuj liczbę dni na wynik aktywności użytkownika dla zasad, do których został dodany
6. Aby wyszukać użytkowników w usłudze Active Directory, użyj **pola Wyszukaj użytkownika w celu dodania do zasad** . Wpisz nazwę użytkownika, którego chcesz dodać do zasad. Wybierz nazwę użytkownika i powtórz tę czynność, aby przypisać dodatkowych użytkowników do zasad. Lista wybranych użytkowników pojawi się w sekcji użytkownicy okienka Dodawanie użytkowników do wielu zasad.
7. Aby zaimportować listę użytkowników w celu dodania ich do zasad, wybierz  pozycję Importuj w celu zaimportowania .csv pliku danych (wartości rozdzielanych przecinkami). Plik musi mieć następujący format i musi zawierać listę głównych nazw użytkowników w pliku:

    ```csv
    user principal name
    user1@domain.com
    user2@domain.com
    ```

8. Wybierz pozycję Dodaj użytkowników do zasad, aby zaakceptować zmiany i dodać użytkowników do zasad, lub pozycję Anuluj, aby odrzucić zmiany i zamknąć okno dialogowe.

## <a name="stop-scoring-users-in-a-policy"></a>Zatrzymywanie oceniania użytkowników w zasadach

Aby zatrzymać ocenianie użytkowników zgodnie z zasadami, zobacz artykuł Użytkownicy zarządzający niejawnym programem testów ryzyka: Usuwanie użytkowników z zakresu [przypisania do](insider-risk-management-users.md#remove-users-from-in-scope-assignment-to-policies) zasad.

## <a name="delete-a-policy"></a>Usuwanie zasad

> [!NOTE]
> Usunięcie zasad nie powoduje usunięcia aktywnych ani zarchiwizowane alertów wygenerowanych z zasad.

Aby usunąć istniejące zasady zarządzania ryzykiem w niejawnym programie testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę** Zasady.
2. Na pulpicie nawigacyjnym zasad wybierz zasady, które chcesz usunąć.
3. Wybierz **pozycję Usuń** na pasku narzędzi pulpitu nawigacyjnego.
4. W **oknie dialogowym** Usuwanie wybierz pozycję **Tak** , aby usunąć zasady, lub pozycję **Anuluj** , aby zamknąć okno dialogowe.
