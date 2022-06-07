---
title: Zasady zarządzania ryzykiem wewnętrznym
description: Dowiedz się więcej o zasadach zarządzania ryzykiem wewnętrznym w usłudze Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: 4b61043af9c66f43701f34381f12aaafdca8cabe
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922202"
---
# <a name="insider-risk-management-policies"></a>Zasady zarządzania ryzykiem wewnętrznym

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Zasady zarządzania ryzykiem wewnętrznym określają, którzy użytkownicy są w zakresie i jakie typy wskaźników ryzyka są skonfigurowane dla alertów. Można szybko utworzyć zasady, które mają zastosowanie do wszystkich użytkowników w organizacji lub zdefiniować poszczególnych użytkowników lub grupy do zarządzania w zasadach. Zasady obsługują priorytety zawartości, aby skoncentrować warunki zasad na wielu lub określonych aplikacjach Microsoft Teams, witrynach programu SharePoint, typach poufności danych i etykietach danych. Za pomocą szablonów można wybrać określone wskaźniki ryzyka i dostosować progi zdarzeń dla wskaźników zasad, skutecznie dostosowując wyniki ryzyka oraz poziom i częstotliwość alertów. Ponadto dopalacze oceny ryzyka i wykrywanie anomalii pomagają zidentyfikować aktywność użytkownika, która ma większe znaczenie lub jest bardziej nietypowa. Okna zasad umożliwiają zdefiniowanie przedziału czasowego stosowania zasad do działań alertów i służą do określania czasu trwania zasad po aktywowaniu.

Zapoznaj się z [wideo Konfiguracja zasad zarządzania ryzykiem wewnętrznym](https://www.youtube.com/watch?v=kudK5ajZTUo) , aby zapoznać się z omówieniem sposobu, w jaki zasady utworzone za pomocą wbudowanych szablonów zasad mogą pomóc w szybkim reagowaniu na potencjalne zagrożenia.

## <a name="policy-dashboard"></a>Pulpit nawigacyjny zasad

**Pulpit nawigacyjny zasad** umożliwia szybkie wyświetlanie zasad w organizacji, kondycję zasad, ręczne dodawanie użytkowników do zasad oraz wyświetlanie stanu alertów skojarzonych z poszczególnymi zasadami.

- **Nazwa zasad**: nazwa przypisana do zasad w kreatorze zasad.
- **Stan**: stan kondycji poszczególnych zasad. Wyświetla liczbę ostrzeżeń i zaleceń zasad lub stan *W dobrej kondycji* dla zasad bez problemów.  Możesz wybrać zasady, aby wyświetlić szczegóły stanu kondycji dla wszelkich ostrzeżeń lub zaleceń.
- **Aktywne alerty**: liczba aktywnych alertów dla poszczególnych zasad.
- **Potwierdzone alerty**: całkowita liczba alertów, które spowodowały przypadki z zasad w ciągu ostatnich 365 dni.
- **Akcje wykonywane w przypadku alertów**: całkowita liczba alertów, które zostały potwierdzone lub odrzucone w ciągu ostatnich 365 dni.
- **Skuteczność alertów zasad**: wartość procentowa określona przez łączną liczbę potwierdzonych alertów podzieloną przez łączną liczbę akcji wykonywanych w alertach (czyli sumę alertów, które zostały potwierdzone lub odrzucone w ciągu ostatniego roku).

![Pulpit nawigacyjny zasad zarządzania ryzykiem wewnętrznym.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics"></a>Zalecenia dotyczące zasad z analizy

Analiza ryzyka dotyczącego informacji poufnych umożliwia przeprowadzenie oceny potencjalnych zagrożeń wewnętrznych w organizacji bez konfigurowania żadnych zasad ryzyka związanego z wewnętrznymi informacjami. Ta ocena może pomóc twojej organizacji zidentyfikować potencjalne obszary o wyższym ryzyku użytkowników i pomóc w określeniu typu i zakresu zasad zarządzania ryzykiem wewnętrznym, które możesz rozważyć skonfigurowanie.

Aby dowiedzieć się więcej na temat analizy ryzyka wewnętrznego i zaleceń dotyczących zasad, zobacz [Ustawienia zarządzania ryzykiem wewnętrznym: Analiza](insider-risk-management-settings.md#analytics).

## <a name="policy-templates"></a>Szablony zasad

Szablony zarządzania ryzykiem wewnętrznym to wstępnie zdefiniowane warunki zasad definiujące typy wskaźników ryzyka i model oceniania ryzyka używany przez zasady. Przed utworzeniem zasad każda zasada musi mieć przypisany szablon w kreatorze tworzenia zasad. Zarządzanie ryzykiem wewnętrznym obsługuje maksymalnie pięć zasad dla każdego szablonu zasad. Podczas tworzenia nowych zasad ryzyka dotyczącego informacji poufnych za pomocą kreatora zasad wybierz jeden z następujących szablonów zasad:

### <a name="data-theft-by-departing-users"></a>Kradzież danych przez odchodzących użytkowników

Gdy użytkownicy opuszczają organizację, istnieją określone wskaźniki ryzyka zwykle związane z kradzieżą danych przez odchodzących użytkowników. Ten szablon zasad używa wskaźników eksfiltracji do oceniania ryzyka i koncentruje się na wykrywaniu i alertach w tym obszarze ryzyka. Kradzież danych dla odchodzących użytkowników może obejmować pobieranie plików z usługi SharePoint Online, drukowanie plików i kopiowanie danych do osobistych usług przesyłania komunikatów i magazynowania w chmurze w pobliżu ich rezygnacji z zatrudnienia i dat zakończenia. Korzystając z łącznika usługi Microsoft 365 HR lub opcji automatycznego monitorowania usunięcia konta użytkownika w usłudze Azure Active Directory dla organizacji, ten szablon rozpoczyna ocenianie wskaźników ryzyka związanych z tymi działaniami i ich korelowania ze stanem zatrudnienia użytkowników.

> [!IMPORTANT]
> W przypadku korzystania z tego szablonu można skonfigurować łącznik usługi Microsoft 365 HR, aby okresowo importować informacje o rezygnacji i dacie zakończenia dla użytkowników w organizacji. Zapoznaj się [z artykułem Importowanie danych za pomocą łącznika HR,](import-hr-data.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika usługi Microsoft 365 HR dla organizacji. Jeśli nie chcesz używać łącznika hr, musisz wybrać opcję Konto użytkownika usunięte z usługi Azure AD podczas konfigurowania zdarzeń wyzwalacza w kreatorze zasad.

### <a name="general-data-leaks"></a>Ogólne przecieki danych

Ochrona danych i zapobieganie wyciekom danych jest stałym wyzwaniem dla większości organizacji, szczególnie w przypadku szybkiego rozwoju nowych danych tworzonych przez użytkowników, urządzenia i usługi. Użytkownicy mogą tworzyć, przechowywać i udostępniać informacje między usługami i urządzeniami, które sprawiają, że zarządzanie wyciekami danych staje się coraz bardziej złożone i trudniejsze. Wycieki danych mogą obejmować przypadkowe nadmierne dzielenie informacji poza organizacją lub kradzież danych ze złośliwym zamiarem. Dzięki przypisanym zasadom ochrony przed utratą danych (DLP) firmy Microsoft Purview, wbudowanym lub dostosowywalnym zdarzeniom wyzwalającym ten szablon rozpoczyna ocenianie wykrywania podejrzanych danych usługi SharePoint Online w czasie rzeczywistym, udostępniania plików i folderów, drukowania plików oraz kopiowania danych do osobistych usług przesyłania komunikatów i magazynowania w chmurze.

W przypadku korzystania z szablonu *Wycieki danych* można przypisać zasady DLP w celu wyzwolenia wskaźników w zasadach ryzyka wewnętrznego dla alertów o wysokiej ważności w organizacji. Za każdym razem, gdy alert o wysokiej ważności jest generowany przez regułę zasad DLP, jest dodawany do dziennika inspekcji usługi Office 365, zasady ryzyka wewnętrznego utworzone za pomocą tego szablonu automatycznie sprawdzają alert DLP o wysokiej ważności. Jeśli alert zawiera użytkownika w zakresie zdefiniowanego w zasadach ryzyka niejawnego dostępu do informacji poufnych, alert jest przetwarzany przez zasady ryzyka informacji poufnych jako nowy alert i przypisano do niego ważność ryzyka wewnętrznego i ocenę ryzyka. Możesz również przypisać wybrane wskaźniki jako wyzwalające zdarzenia dla zasad. Ta elastyczność i dostosowywanie ułatwia określanie zakresu zasad tylko do działań objętych wskaźnikami. Te zasady umożliwiają ocenę tego alertu w kontekście innych działań uwzględnionych w tym przypadku.

#### <a name="data-leaks-policy-guidelines"></a>Wytyczne dotyczące zasad wycieków danych

Podczas tworzenia lub modyfikowania zasad DLP do użycia z zasadami zarządzania ryzykiem wewnętrznym należy wziąć pod uwagę następujące wytyczne:

- Określanie priorytetów zdarzeń eksfiltracji danych i selektywne podczas przypisywania ustawień **raportów o zdarzeniach** do *wartości Wysoki* podczas konfigurowania reguł w zasadach DLP. Na przykład wysyłanie poufnych dokumentów pocztą e-mail do znanego konkurenta powinno być zdarzeniem eksfiltracji *wysokiego* poziomu alertów. Nadmierne przypisywanie *wysokiego* poziomu w ustawieniach **raportów o zdarzeniach** w innych regułach zasad DLP może zwiększyć szum w przepływie pracy alertów zarządzania ryzykiem wewnętrznym i utrudnić badaczom danych i analitykom prawidłową ocenę tych alertów. Na przykład przypisanie *wysokich* poziomów alertów w celu uzyskania dostępu do działań odmowy w zasadach DLP utrudnia ocenę prawdziwie ryzykownych zachowań i działań użytkowników.
- W przypadku korzystania z zasad DLP jako zdarzenia wyzwalającego upewnij się, że rozumiesz i prawidłowo konfigurujesz użytkowników w zakresie zarówno w zasadach DLP, jak i zasadach zarządzania ryzykiem wewnętrznym. Tylko użytkownicy zdefiniowani jako w zakresie zasad zarządzania ryzykiem wewnętrznym przy użyciu szablonu **Wycieki danych** będą mieć przetworzone alerty zasad DLP o wysokiej ważności. Ponadto tylko użytkownicy zdefiniowani jako w zakresie w regule dla alertu DLP o wysokiej ważności zostaną przeanalizowani przez zasady zarządzania ryzykiem wewnętrznym do rozważenia. Ważne jest, aby nie nieświadomie konfigurować użytkowników w zakresie zarówno w zasadach DLP, jak i wewnętrznych zasad ryzyka w sposób powodujący konflikt.

     Jeśli na przykład reguły zasad DLP mają zakres tylko dla użytkowników w zespole ds. sprzedaży, a zasady ryzyka wewnętrznego utworzone na podstawie szablonu **Wycieki danych** zdefiniowały wszystkich użytkowników jako w zakresie, zasady ryzyka niejawnego dostępu do informacji poufnych będą przetwarzać tylko alerty DLP o wysokiej ważności dla użytkowników w zespole ds. sprzedaży. Zasady ryzyka wewnętrznego nie będą otrzymywać żadnych alertów DLP o wysokim priorytecie dla użytkowników do przetwarzania, które nie są zdefiniowane w regułach DLP w tym przykładzie. Z drugiej strony, jeśli zasady zarządzania ryzykiem wewnętrznym utworzone na podstawie **szablonów wycieków danych** są ograniczone tylko do użytkowników w zespole ds. sprzedaży, a przypisane zasady DLP są ograniczone do wszystkich użytkowników, zasady ryzyka wewnętrznego będą przetwarzać tylko alerty DLP o wysokiej ważności dla członków zespołu ds. sprzedaży. Zasady zarządzania ryzykiem wewnętrznym będą ignorować alerty DLP o wysokiej ważności dla wszystkich użytkowników, którzy nie są w zespole ds. sprzedaży.

- Upewnij się, że ustawienie **reguły Raporty zdarzeń** w zasadach DLP używanych dla tego szablonu zarządzania ryzykiem wewnętrznym jest skonfigurowane dla alertów o *wysokiej* ważności. *Wysoki poziom* ważności to wyzwalające zdarzenia, a alerty dotyczące zarządzania ryzykiem wewnętrznym nie będą generowane na podstawie reguł zasad DLP z polem **Raporty o zdarzeniach** ustawionym na *wartość Niska* lub *Średnia*.

    ![Ustawienie alertu zasad DLP.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Podczas tworzenia nowych zasad DLP przy użyciu wbudowanych szablonów należy wybrać opcję **Utwórz lub dostosuj zaawansowane reguły DLP** , aby skonfigurować ustawienie **Raporty zdarzeń** dla poziomu *o wysokiej* ważności.

Każda zasada zarządzania ryzykiem wewnętrznym utworzona na podstawie szablonu **Wycieki danych może mieć przypisane** tylko jedną zasadę DLP podczas korzystania z tej opcji wyzwalania zdarzenia. Rozważ utworzenie dedykowanych zasad DLP, które łączą różne działania, które chcesz wykrywać i działać jako wyzwalanie zdarzeń dla zasad ryzyka wewnętrznego korzystających z szablonu **Wycieki danych** .

Zapoznaj się z [artykułem Tworzenie, testowanie i dostrajanie zasad DLP,](create-test-tune-dlp-policy.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania zasad DLP dla organizacji.

### <a name="data-leaks-by-priority-users-preview"></a>Wycieki danych przez użytkowników o priorytecie (wersja zapoznawcza)

Ochrona danych i zapobieganie wyciekom danych dla użytkowników w organizacji może zależeć od ich pozycji, poziomu dostępu do informacji poufnych lub historii ryzyka. Wycieki danych mogą obejmować przypadkowe nadsyłanie wysoce poufnych informacji poza organizacją lub kradzież danych ze złośliwym zamiarem. Dzięki przypisanym zasadom ochrony przed utratą danych (DLP) jako opcją wyzwalania zdarzenia ten szablon rozpoczyna ocenianie wykrywania podejrzanych działań w czasie rzeczywistym i powoduje zwiększone prawdopodobieństwo alertów i alertów o podwyższonym ryzyku wewnętrznym. Użytkownicy o priorytecie są definiowane w [grupach użytkowników o priorytecie](insider-risk-management-settings.md#priority-user-groups-preview) skonfigurowanych w obszarze ustawień zarządzania ryzykiem wewnętrznym.

Podobnie jak w przypadku **szablonu Ogólne wycieki danych**, możesz wybrać zasady DLP, aby wyzwalać wskaźniki w zasadach ryzyka wewnętrznego dla alertów o wysokiej ważności w organizacji. Postępuj zgodnie z wytycznymi dotyczącymi zasad wycieków danych dla zasad DLP podczas tworzenia zasad z opcją DLP podczas korzystania z tego szablonu. Możesz również przypisać wybrane wskaźniki jako wyzwalające zdarzenia dla zasad. Ta elastyczność i dostosowywanie ułatwiają określanie zakresu zasad tylko do działań objętych wskaźnikami. Ponadto należy przypisać do zasad grupy użytkowników o priorytecie utworzone w **obszarze Ustawienia** >  **zarządzania** >  ryzykiem wewnętrznym **Grupy użytkowników o priorytecie**.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Wycieki danych przez niezadowolonych użytkowników (wersja zapoznawcza)

Gdy użytkownicy odczuwają stresory związane z zatrudnieniem, mogą stać się niezadowoleni, co może zwiększyć szanse na aktywność związaną z ryzykiem wewnętrznym. Ten szablon rozpoczyna ocenianie działania użytkownika po zidentyfikowaniu wskaźnika skojarzonego z niezadowoleniem. Przykłady obejmują powiadomienia o poprawie wydajności, słabe przeglądy wydajności lub zmiany stanu poziomu zadań. Przecieki danych dla niezadowolonych użytkowników mogą obejmować pobieranie plików z usługi SharePoint Online i kopiowanie danych do osobistych usług obsługi komunikatów i magazynowania w chmurze w pobliżu zdarzeń stresorów związanych z zatrudnieniem.

W przypadku korzystania z tego szablonu należy również skonfigurować łącznik usługi Microsoft 365 HR, aby okresowo importować powiadomienia o poprawie wydajności, stan przeglądu wydajności lub informacje o zmianie poziomu zadań dla użytkowników w organizacji. Zapoznaj się [z artykułem Importowanie danych za pomocą łącznika HR,](import-hr-data.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika usługi Microsoft 365 HR dla organizacji.

### <a name="general-security-policy-violations-preview"></a>Ogólne naruszenia zasad zabezpieczeń (wersja zapoznawcza)

W wielu organizacjach użytkownicy mają uprawnienia do instalowania oprogramowania na swoich urządzeniach lub modyfikowania ustawień urządzeń w celu ułatwienia wykonywania zadań. Przypadkowo lub ze złośliwym zamiarem użytkownicy mogą instalować złośliwe oprogramowanie lub wyłączać ważne funkcje zabezpieczeń, które ułatwiają ochronę informacji na urządzeniu lub w zasobach sieciowych. Ten szablon zasad używa alertów zabezpieczeń z usługi Microsoft Defender for Endpoint w celu rozpoczęcia oceniania tych działań oraz wykrywania fokusu i alertów w tym obszarze ryzyka. Ten szablon służy do udostępniania szczegółowych informacji na temat naruszeń zasad zabezpieczeń w scenariuszach, w których użytkownicy mogą mieć historię naruszeń zasad zabezpieczeń, które mogą być wskaźnikiem ryzyka związanego z poufnymi informacjami.

Musisz skonfigurować usługę Microsoft Defender for Endpoint w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem wewnętrznym w usłudze Defender Security Center, aby importować alerty naruszenia zabezpieczeń. Aby uzyskać więcej informacji na temat konfigurowania usługi Defender for Endpoint na potrzeby integracji z zarządzaniem ryzykiem wewnętrznym, zobacz [Konfigurowanie zaawansowanych funkcji w usłudze Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="general-patient-data-misuse-preview"></a>Ogólne nieprawidłowe wykorzystanie danych pacjentów (wersja zapoznawcza)

Ochrona danych rekordów opieki zdrowotnej i zapobieganie niewłaściwemu wykorzystywaniu danych osobowych pacjentów jest istotnym problemem dla organizacji w branży opieki zdrowotnej. To nadużycie może obejmować poufne wycieki danych do nieautoryzowanych osób, oszukańczą modyfikację dokumentacji pacjentów lub kradzież dokumentacji medycznej pacjentów. Zapobieganie temu niewłaściwemu wykorzystaniu danych pacjentów, albo z powodu braku świadomości, zaniedbania lub oszustw ze strony użytkowników, jest również kluczowym elementem spełniania wymogów prawnych ustawy o przenośności i odpowiedzialności ubezpieczeń zdrowotnych (HIPAA) oraz health information technology for Economic and Clinical Health (HITECH). Oba te akty ustanawiają wymagania dotyczące ochrony informacji zdrowotnych chronionych przez pacjenta (PHI).

Ten szablon zasad umożliwia ocenianie ryzyka dla użytkowników wewnętrznych, którzy wykrywają podejrzane działania związane z rekordami hostowanymi w istniejących systemach elektronicznej dokumentacji medycznej (EMR). Wykrywanie koncentruje się na nieautoryzowanym dostępie, wyświetlaniu, modyfikowaniu i eksportowaniu danych pacjentów. Należy skonfigurować łącznik [łącznika usługi Microsoft Healthcare](import-healthcare-data.md) lub [łącznika Epic](import-epic-data.md) w celu obsługi wykrywania działań związanych z dostępem, eksfiltracją lub zaciemnianiem w systemie EMR.

W przypadku korzystania z tego szablonu należy również skonfigurować łącznik usługi Microsoft 365 HR, aby okresowo importować dane profilu organizacji dla użytkowników w organizacji. Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika usługi Microsoft 365 HR dla organizacji, zobacz Artykuł [Konfigurowanie łącznika do importowania danych kadrowych](/microsoft-365/compliance/import-hr-data) .

### <a name="security-policy-violations-by-departing-users-preview"></a>Naruszenia zasad zabezpieczeń przez odchodzących użytkowników (wersja zapoznawcza)

Odchodzących użytkowników, bez względu na to, czy są pozostawieni na warunkach pozytywnych, czy negatywnych, może być większe ryzyko naruszeń zasad zabezpieczeń. Aby chronić przed niezamierzonymi lub złośliwymi naruszeniami zabezpieczeń dla odchodzących użytkowników, ten szablon zasad używa alertów usługi Defender for Endpoint w celu zapewnienia wglądu w działania związane z zabezpieczeniami. Działania te obejmują instalowanie złośliwego oprogramowania lub innych potencjalnie szkodliwych aplikacji oraz wyłączanie funkcji zabezpieczeń na swoich urządzeniach. Korzystając z [łącznika usługi Microsoft 365 HR](import-hr-data.md) lub opcji automatycznego monitorowania usunięcia konta użytkownika w usłudze Azure Active Directory dla organizacji, ten szablon rozpoczyna ocenianie wskaźników ryzyka związanych z tymi działaniami zabezpieczeń i sposobu ich korelowania ze stanem zatrudnienia użytkowników.

Musisz skonfigurować usługę Microsoft Defender for Endpoint w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem wewnętrznym w usłudze Defender Security Center, aby importować alerty naruszenia zabezpieczeń. Aby uzyskać więcej informacji na temat konfigurowania usługi Defender for Endpoint na potrzeby integracji z zarządzaniem ryzykiem wewnętrznym, zobacz [Konfigurowanie zaawansowanych funkcji w usłudze Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Naruszenia zasad zabezpieczeń przez użytkowników o priorytecie (wersja zapoznawcza)

Ochrona przed naruszeniami zabezpieczeń dla użytkowników w organizacji może zależeć od ich pozycji, poziomu dostępu do informacji poufnych lub historii ryzyka. Ponieważ naruszenia zabezpieczeń przez użytkowników o priorytecie mogą mieć znaczący wpływ na krytyczne obszary organizacji, ten szablon zasad rozpoczyna ocenianie tych wskaźników i używa alertów usługi Microsoft Defender for Endpoint w celu zapewnienia wglądu w działania związane z zabezpieczeniami dla tych użytkowników. Działania te mogą obejmować priorytetowe instalowanie złośliwego oprogramowania lub innych potencjalnie szkodliwych aplikacji oraz wyłączanie funkcji zabezpieczeń na swoich urządzeniach. Użytkownicy o priorytecie są definiowane w grupach użytkowników o priorytecie skonfigurowanych w obszarze ustawień zarządzania ryzykiem wewnętrznym.

Musisz skonfigurować usługę Microsoft Defender for Endpoint w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem wewnętrznym w usłudze Defender Security Center, aby importować alerty naruszenia zabezpieczeń. Aby uzyskać więcej informacji na temat konfigurowania usługi Defender for Endpoint na potrzeby integracji z zarządzaniem ryzykiem wewnętrznym, zobacz [Konfigurowanie zaawansowanych funkcji w usłudze Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). Ponadto należy przypisać do zasad grupy użytkowników o priorytecie utworzone w **obszarze Ustawienia** >  **zarządzania** >  ryzykiem wewnętrznym **Grupy użytkowników o priorytecie**.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników (wersja zapoznawcza)

Użytkownicy, którzy odczuwają stresory związane z zatrudnieniem, mogą być narażeni na większe ryzyko przypadkowego lub złośliwego naruszenia zasad zabezpieczeń. Te czynniki stresorowe mogą obejmować użytkownika, który został umieszczony w planie poprawy wydajności, niski stan przeglądu wydajności lub został zdegradowany z bieżącej pozycji. Ten szablon zasad uruchamia ocenianie ryzyka na podstawie tych wskaźników i działań skojarzonych z tymi zdarzeniami dla tych użytkowników.

W przypadku korzystania z tego szablonu należy również skonfigurować łącznik usługi Microsoft 365 HR, aby okresowo importować powiadomienia o poprawie wydajności, stan przeglądu wydajności lub informacje o zmianie poziomu zadań dla użytkowników w organizacji. Zapoznaj się [z artykułem Importowanie danych za pomocą łącznika HR,](import-hr-data.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika usługi Microsoft 365 HR dla organizacji.

Musisz również skonfigurować usługę Microsoft Defender for Endpoint w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem wewnętrznym w usłudze Defender Security Center, aby importować alerty naruszenia zabezpieczeń. Aby uzyskać więcej informacji na temat konfigurowania usługi Defender for Endpoint na potrzeby integracji z zarządzaniem ryzykiem wewnętrznym, zobacz [Konfigurowanie zaawansowanych funkcji w usłudze Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>Wymagania wstępne szablonu zasad i wyzwalanie zdarzeń

W zależności od szablonu wybranego dla zasad zarządzania ryzykiem wewnętrznym zdarzenia wyzwalania i wymagania wstępne zasad różnią się. Wyzwalanie zdarzeń to wymagania wstępne, które określają, czy użytkownik jest aktywny w przypadku zasad zarządzania ryzykiem wewnętrznym. Jeśli użytkownik zostanie dodany do zasad zarządzania ryzykiem wewnętrznym, ale nie ma zdarzenia wyzwalającego, działanie użytkownika nie zostanie ocenione przez zasady, chyba że zostanie on ręcznie dodany na pulpicie nawigacyjnym Użytkownicy. Wymagania wstępne zasad są wymaganymi elementami, dzięki czemu zasady odbierają sygnały lub działania niezbędne do oceny ryzyka.

W poniższej tabeli wymieniono zdarzenia wyzwalające i wymagania wstępne dotyczące zasad utworzonych na podstawie każdego szablonu zasad zarządzania ryzykiem wewnętrznym:

| **Szablon zasad** | **Wyzwalanie zdarzeń dla zasad** | **Wymagania wstępne** |
| :------------------ | :--------------------------------- | :---------------- |
| **Kradzież danych przez odchodzących użytkowników** | Wskaźnik daty rezygnacji lub zakończenia z łącznika HR lub usunięcia konta usługi Azure Active Directory | (opcjonalnie) Łącznik usługi Microsoft 365 HR skonfigurowany pod kątem wskaźników daty zakończenia i rezygnacji |
| **Ogólne przecieki danych** | Działanie zasad wycieku danych, które tworzy alert *o wysokiej ważności* lub wbudowane wyzwalacze zdarzeń eksfiltracji | Zasady DLP skonfigurowane dla alertów *o wysokiej ważności* <br><br> LUB <br><br> Dostosowane wskaźniki wyzwalania |
| **Wycieki danych według użytkowników o priorytecie** | Działanie zasad wycieku danych, które tworzy alert *o wysokiej ważności* lub wbudowane wyzwalacze zdarzeń eksfiltracji | Zasady DLP skonfigurowane dla alertów *o wysokiej ważności* <br><br> LUB <br><br> Dostosowane wskaźniki wyzwalania <br><br> Priorytetowe grupyużytkownikia |
| **Wycieki danych przez niezadowolonych użytkowników** | Wskaźnik poprawy wydajności, niskiej wydajności lub wskaźników zmiany poziomu zadań z łącznika HR | Łącznik usługi Microsoft 365 HR skonfigurowany pod kątem wskaźników niezadowolenia |
| **Ogólne naruszenia zasad zabezpieczeń** | Ochrona przed uchylaniem się od kontroli bezpieczeństwa lub niepożądanego oprogramowania wykrytego przez usługę Microsoft Defender dla punktu końcowego | Aktywna subskrypcja usługi Microsoft Defender dla punktu końcowego <br><br> Skonfigurowano integrację usługi Microsoft Defender for Endpoint z portalem zgodności usługi Microsoft Purview |
| **Ogólne nieprawidłowe wykorzystanie danych pacjentów** | Ochrona przed uchylaniem się od kontroli bezpieczeństwa z systemów EMR <br><br> Wskaźniki dopasowywania adresów użytkowników i pacjentów z systemów HR | Wskaźniki dostępu do opieki zdrowotnej wybrane w ustawieniach ryzyka dotyczącego zasad lub informacji poufnych <br><br> Łącznik usługi Microsoft 365 HR skonfigurowany do dopasowywania adresów <br><br> Skonfigurowano łącznik Microsoft Healthcare lub Epic |
| **Naruszenia zasad zabezpieczeń przez odchodzących użytkowników** | Wskaźniki daty rezygnacji lub zakończenia z łącznika HR lub usunięcia konta usługi Azure Active Directory | (opcjonalnie) Łącznik usługi Microsoft 365 HR skonfigurowany pod kątem wskaźników daty zakończenia i rezygnacji <br><br> Aktywna subskrypcja usługi Microsoft Defender dla punktu końcowego <br><br> Skonfigurowano integrację usługi Microsoft Defender for Endpoint z portalem zgodności usługi Microsoft Purview |
| **Naruszenia zasad zabezpieczeń przez użytkowników o priorytecie** | Ochrona przed uchylaniem się od kontroli bezpieczeństwa lub niepożądanego oprogramowania wykrytego przez usługę Microsoft Defender dla punktu końcowego | Aktywna subskrypcja usługi Microsoft Defender dla punktu końcowego <br><br> Skonfigurowano integrację usługi Microsoft Defender for Endpoint z portalem zgodności usługi Microsoft Purview <br><br> Priorytetowe grupyużytkownikia |
| **Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników** | Wskaźnik poprawy wydajności, niskiej wydajności lub wskaźników zmiany poziomu zadań z łącznika HR | Łącznik usługi Microsoft 365 HR skonfigurowany pod kątem wskaźników niezadowolenia <br><br> Aktywna subskrypcja usługi Microsoft Defender dla punktu końcowego <br><br> Skonfigurowano integrację usługi Microsoft Defender for Endpoint z portalem zgodności usługi Microsoft Purview |

## <a name="prioritize-content-in-policies"></a>Określanie priorytetów zawartości w zasadach

Zasady zarządzania ryzykiem wewnętrznym obsługują określanie wyższego priorytetu zawartości w zależności od tego, gdzie jest przechowywana, typ zawartości lub sposób jej klasyfikowania. Określenie zawartości jako priorytetu zwiększa ocenę ryzyka dla każdego skojarzonego działania, co z kolei zwiększa prawdopodobieństwo wygenerowania alertu o wysokiej ważności. Jednak niektóre działania w ogóle nie wygenerują alertu, chyba że powiązana zawartość zawiera wbudowane lub niestandardowe typy informacji poufnych lub została określona jako priorytet w zasadach.

Na przykład twoja organizacja ma dedykowaną witrynę programu SharePoint dla wysoce poufnego projektu. Wycieki danych dotyczące informacji w tej witrynie programu SharePoint mogą naruszyć projekt i mieć znaczący wpływ na jego powodzenie. Dzięki określaniu priorytetów tej witryny programu SharePoint w zasadach wycieków danych wyniki ryzyka dla kwalifikujących się działań są automatycznie zwiększane. Ta priorytetyzacja zwiększa prawdopodobieństwo, że te działania wygenerują alert o ryzyku wewnętrznym i podwyższą poziom ważności alertu.

Podczas tworzenia zasad zarządzania ryzykiem wewnętrznym w kreatorze zasad można wybrać spośród następujących priorytetów:

- **Witryny programu SharePoint**: wszystkie działania skojarzone ze wszystkimi typami plików w zdefiniowanych witrynach programu SharePoint mają wyższy wynik ryzyka. Użytkownicy konfigurujący zasady i wybierający priorytetowe witryny share point mogą wybrać witryny programu SharePoint, do których mają uprawnienia dostępu. Jeśli witryny programu SharePoint nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może wybrać witryny dla zasad później lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.
- **Typy informacji poufnych**: każde działanie skojarzone z zawartością zawierającą [typy informacji poufnych](sensitive-information-type-entity-definitions.md) ma wyższy wynik ryzyka.
- **Etykiety poufności**: każde działanie skojarzone z zawartością, do którego zastosowano określone [etykiety poufności](sensitivity-labels.md) , otrzymuje wyższy wynik ryzyka.
- **Rozszerzenia plików**: wszelkie działania skojarzone z zawartością, która ma określone rozszerzenia plików. Użytkownicy konfigurujący zasady kradzieży/wycieku danych, które wybierają **rozszerzenia plików do określenia priorytetów** w kreatorze zasad, mogą zdefiniować maksymalnie 50 rozszerzeń plików w celu określenia priorytetów w zasadach. Wprowadzone rozszerzenia mogą zawierać lub pomijać znak "". Jako pierwszy znak rozszerzenia o priorytetach.

## <a name="sequence-detection"></a>Wykrywanie sekwencji

Ryzykowne działania mogą nie występować jako zdarzenia izolowane. Te zagrożenia są często częścią większej sekwencji zdarzeń. Sekwencja to grupa co najmniej dwóch działań użytkownika wykonywanych jeden po drugim, co może sugerować podwyższone ryzyko. Zidentyfikowanie tych powiązanych działań jest ważną częścią oceny ogólnego ryzyka. Po włączeniu wykrywania sekwencji w przypadku zasad kradzieży danych lub wycieków danych szczegółowe informacje z działań związanych z informacjami sekwencji są wyświetlane na karcie **Działania użytkownika** w przypadku zarządzania ryzykiem wewnętrznym. Następujące szablony zasad obsługują wykrywanie sekwencji:

- Kradzież danych przez odchodzących użytkowników
- Ogólne przecieki danych
- Wycieki danych według użytkowników o priorytecie
- Wycieki danych przez niezadowolonych użytkowników

Te zasady zarządzania ryzykiem wewnętrznym mogą używać określonych wskaźników i kolejności wykrywania poszczególnych kroków w sekwencji ryzyka. Nazwy plików są używane podczas mapowania działań w sekwencji. Te zagrożenia są podzielone na cztery główne kategorie działań:

- **Kolekcja**: Te sygnały kategorii koncentrują się na działaniach pobierania przez użytkowników zasad w zakresie. Przykładowe działania w tej kategorii to pobieranie plików z witryn programu SharePoint lub przenoszenie plików do skompresowanego folderu.
- **Eksfiltracja**: Te sygnały kategorii koncentrują się na udostępnianiu lub wyodrębnianiu działań do źródeł wewnętrznych i zewnętrznych przez użytkowników zasad w zakresie. Przykładem działania w tej kategorii jest wysyłanie wiadomości e-mail z załącznikami z organizacji do adresatów zewnętrznych.
- **Zaciemnianie: te sygnały** kategorii koncentrują się na maskowaniu ryzykownych działań przez użytkowników zasad w zakresie. Niektóre przykładowe działania w tej kategorii to zmiana nazw plików na urządzeniu lub usunięcie lub obniżenie poziomu etykiet poufności w plikach programu SharePoint.
- **Oczyszczanie**: te sygnały kategorii koncentrują się na działaniach usuwania przez użytkowników zasad w zakresie. Przykładowym działaniem w tej kategorii byłoby usunięcie plików z urządzenia.

> [!NOTE]
> Wykrywanie sekwencji używa wskaźników, które są włączone w ustawieniach globalnych na potrzeby zarządzania ryzykiem wewnętrznym i wskaźników wybranych w zasadach. Jeśli nie zostaną wybrane odpowiednie wskaźniki, wykrywanie sekwencji nie będzie działać.

Po skonfigurowaniu w zasadach można dostosować ustawienia poszczególnych progów dla każdego typu wykrywania sekwencji. Te ustawienia progowe dostosowują alerty na podstawie ilości plików skojarzonych z sekwencją.

Aby dowiedzieć się więcej na temat zarządzania wykrywaniem sekwencji w widoku **Działania użytkownika** , zobacz [Przypadki zarządzania ryzykiem wewnętrznym: Aktywność użytkownika](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Zbiorcze wykrywanie eksfiltracji (wersja zapoznawcza)

Wskaźniki ryzyka wewnętrznego pomagają zidentyfikować nietypowe poziomy działań związanych z ryzykiem podczas codziennej oceny dla użytkowników, którzy są w zakresie zasad ryzyka wewnętrznego. Skumulowane wykrywanie eksfiltracji używa modeli uczenia maszynowego, aby ułatwić określenie, kiedy działania eksfiltracji wykonywane przez użytkownika w określonym czasie przekraczają normalną ilość wykonywaną przez użytkowników w organizacji w ciągu ostatnich 30 dni w wielu typach działań eksfiltracji. Jeśli na przykład użytkownik udostępnił więcej plików niż większość użytkowników w ciągu ostatniego miesiąca, to działanie zostanie wykryte i sklasyfikowane jako skumulowane działanie eksfiltracji.

Analitycy i badacze zarządzania ryzykiem wewnętrznym mogą używać zbiorczych szczegółowych informacji dotyczących wykrywania eksfiltracji, aby ułatwić identyfikację działań eksfiltracji, które zazwyczaj nie generują alertów, ale są wyższe niż typowe dla ich organizacji. Niektóre przykłady mogą spowodować, że odchodzących użytkowników powoli eksfiltrują dane w ciągu kilku dni lub gdy użytkownicy wielokrotnie udostępniają dane w wielu kanałach bardziej niż zwykle na potrzeby udostępniania danych w organizacji.  Wyższe wyniki ryzyka są przypisywane do skumulowanych działań eksfiltracji dla witryn programu SharePoint, typów informacji poufnych i zawartości z [etykietami poufności](/microsoft-365/compliance/sensitivity-labels#label-priority-order-matters) skonfigurowanymi jako zawartość priorytetowa w zasadach lub do działania obejmującego etykiety skonfigurowane jako wysoki priorytet w usłudze Microsoft Purview Information Protection.

Zbiorcze wykrywanie eksfiltracji jest domyślnie włączone w przypadku korzystania z następujących szablonów zasad:

- Kradzież danych przez odchodzących użytkowników
- Ogólne przecieki danych
- Wycieki danych według użytkowników o priorytecie
- Wycieki danych przez niezadowolonych użytkowników

> [!NOTE]
> Skumulowane wykrywanie eksfiltracji używa wskaźników eksfiltracji, które są włączone w ustawieniach globalnych na potrzeby zarządzania ryzykiem wewnętrznym i wskaźników eksfiltracji wybranych w zasadach. W związku z tym zbiorcze wykrywanie eksfiltracji jest oceniane tylko w przypadku wybranych niezbędnych wskaźników eksfiltracji. Skumulowane działania eksfiltracji [dla etykiet poufności](sensitivity-labels.md) skonfigurowanych w zawartości priorytetowej generują wyższe wyniki ryzyka.

Po włączeniu zbiorczego wykrywania eksfiltracji w przypadku zasad kradzieży danych lub wycieków danych szczegółowe informacje z skumulowanych działań eksfiltracji są wyświetlane na karcie **Działania użytkownika** w przypadku zarządzania ryzykiem wewnętrznym.

Aby dowiedzieć się więcej na temat zarządzania działaniami użytkowników, zobacz [Przypadki zarządzania ryzykiem wewnętrznym: działania użytkowników](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>Kondycja zasad

Stan kondycji zasad zapewnia wgląd w potencjalne problemy z zasadami zarządzania ryzykiem wewnętrznym. Kolumna **Stan** na karcie **Zasady** może ostrzegać o problemach z zasadami, które mogą uniemożliwić zgłaszanie aktywności użytkownika lub dlaczego liczba alertów dotyczących aktywności jest nietypowa. Stan kondycji zasad może również potwierdzić, że zasady są w dobrej kondycji i nie wymagają uwagi ani zmian konfiguracji.

Jeśli występują problemy z zasadami, stan kondycji zasad wyświetla ostrzeżenia i zalecenia dotyczące powiadomień ułatwiające podjęcie działań w celu rozwiązania problemów z zasadami. Te powiadomienia mogą pomóc w rozwiązaniu następujących problemów:

- **Zasady z niekompletną konfiguracją**. Te problemy mogą obejmować brakujących użytkowników lub grup w zasadach lub inne niekompletne kroki konfiguracji zasad.
- **Zasady z problemami z konfiguracją wskaźnika**. Wskaźniki są ważną częścią każdej polityki. Jeśli wskaźniki nie są skonfigurowane lub wybrano zbyt mało wskaźników, zasady mogą nie oceniać ryzykownych działań zgodnie z oczekiwaniami.
- **Wyzwalacze zasad nie działają lub wymagania dotyczące wyzwalacza zasad nie są prawidłowo skonfigurowane**. Funkcjonalność zasad może zależeć od innych usług lub wymagań konfiguracji, aby skutecznie wykrywać wyzwalające zdarzenia, aby aktywować przypisanie oceny ryzyka dla użytkowników w zasadach. Te zależności mogą obejmować problemy z konfiguracją łącznika, udostępnianiem alertów programu Microsoft Defender dla punktu końcowego lub ustawieniami konfiguracji zasad ochrony przed utratą danych.
- **Limity woluminów zbliżają się lub przekraczają limity**. Zasady zarządzania ryzykiem wewnętrznym używają wielu usług i punktów końcowych platformy Microsoft 365 do agregowania sygnałów dotyczących działań związanych z ryzykiem. W zależności od liczby użytkowników w zasadach limity woluminów mogą opóźniać identyfikację i raportowanie działań związanych z ryzykiem. Dowiedz się więcej o tych limitach w sekcji Limity szablonów zasad w tym artykule.

Aby szybko wyświetlić stan kondycji zasad, przejdź do karty **Zasady** i kolumny **Stan** . W tym miejscu zostaną wyświetlone następujące opcje stanu kondycji zasad dla poszczególnych zasad:

- *W dobrej kondycji*: nie zidentyfikowano żadnych problemów z zasadami.
- *Zalecenia*: Istnieją pewne problemy z zasadami, które mogą uniemożliwić działanie zasad zgodnie z oczekiwaniami.
- *Ostrzeżenia*: istnieją problemy z zasadami, które uniemożliwią identyfikację ryzykownych działań.

Aby uzyskać więcej informacji na temat wszelkich zaleceń lub ostrzeżeń, wybierz zasady na karcie **Zasady** , aby otworzyć kartę szczegółów zasad. Więcej informacji na temat zaleceń i ostrzeżeń, w tym wskazówek dotyczących rozwiązywania tych problemów, zostanie wyświetlonych w sekcji **Powiadomienia** na karcie szczegółów.

![Kondycja zasad zarządzania ryzykiem wewnętrznym.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Komunikaty powiadomień

Skorzystaj z poniższej tabeli, aby dowiedzieć się więcej na temat zaleceń, powiadomień ostrzegawczych i akcji, które należy podjąć w celu rozwiązania potencjalnych problemów.

|Komunikaty powiadomień|Szablony zasad|Przyczyny / Spróbuj rozwiązać tę akcję|
|---|---|---|
|Zasady nie przypisują wyników ryzyka do działania|Wszystkie szablony zasad|Możesz przejrzeć zakres zasad i wyzwolić konfigurację zdarzeń, aby zasady mogły przypisywać wyniki ryzyka do działań <br><br> 1. Przejrzyj użytkowników wybranych dla zasad. Jeśli wybrano kilku użytkowników, możesz wybrać dodatkowych użytkowników. <br> 2. Jeśli używasz łącznika HR, sprawdź, czy łącznik HR wysyła prawidłowe dane. <br> 3. Jeśli używasz zasad DLP jako zdarzenia wyzwalającego, sprawdź konfigurację zasad DLP, aby upewnić się, że zostały skonfigurowane do użycia w tych zasadach. <br> 4. W przypadku zasad naruszenia zabezpieczeń zapoznaj się ze stanem klasyfikacji alertów usługi Microsoft Defender for Endpoint wybranym w obszarze Ustawienia ryzyka niejawnych testów > wykrywania inteligentnego. Upewnij się, że filtr alertów nie jest zbyt wąski.|
|Zasady nie wygenerowały żadnych alertów|Wszystkie szablony zasad|Możesz przejrzeć konfigurację zasad, aby przeanalizować ocenianie działań, na których Ci zależy. <br><br> 1. Upewnij się, że wybrano wskaźniki, które chcesz ocenić. Tym więcej wybranych wskaźników, tym więcej działań ma przypisane wyniki ryzyka. <br> 2. Przejrzyj dostosowywanie progu dla zasad. Jeśli wybrane progi nie są zgodne z tolerancją ryzyka organizacji, dostosuj wybrane opcje tak, aby alerty były tworzone na podstawie preferowanych progów. <br> 3. Przejrzyj użytkowników i grupy wybrane dla zasad. Upewnij się, że wybrano wszystkich odpowiednich użytkowników i grupy. <br> 4. W przypadku zasad naruszenia zabezpieczeń potwierdź, że wybrano stan klasyfikacji alertów, który chcesz ocenić dla alertów punktu końcowego w usłudze Microsoft Defender w obszarze Inteligentne wykrywanie w ustawieniach.|
|W tych zasadach nie uwzględniono żadnych użytkowników ani grup|Wszystkie szablony zasad|Użytkownicy lub grupy nie są przypisani do zasad. <br><br> Edytuj zasady i wybierz użytkowników lub grupy dla zasad.|
|Nie wybrano żadnych wskaźników dla tych zasad|Wszystkie szablony zasad|Wskaźniki nie zostały wybrane dla zasad <br><br> Edytuj zasady i wybierz odpowiednie wskaźniki zasad dla zasad.|
|Żadne grupy użytkowników o priorytecie nie są uwzględniane w tych zasadach|— Wycieki danych według użytkowników o priorytecie <br> — Naruszenia zasad zabezpieczeń przez użytkowników o priorytecie|Grupy użytkowników o priorytecie nie są przypisane do zasad. <br><br> Skonfiguruj grupy użytkowników o priorytecie w ustawieniach zarządzania ryzykiem wewnętrznym i przypisz priorytetowe grupy użytkowników do zasad.|
|Dla tych zasad nie wybrano żadnego zdarzenia wyzwalającego|Wszystkie szablony zasad|Zdarzenie wyzwalające nie jest skonfigurowane dla zasad <br><br> Wyniki ryzyka nie będą przypisywane do działań użytkownika, dopóki nie zostaną edytowane zasady i nie wybierzesz zdarzenia wyzwalającego.|
|Łącznik hr nie jest skonfigurowany lub działa zgodnie z oczekiwaniami|— Kradzież danych przez odchodzącego użytkownika <br> — Naruszenia zasad zabezpieczeń przez odchodzącego użytkownika <br> — Wycieki danych przez niezadowolonych użytkowników <br> — Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników|Wystąpił problem z łącznikiem HR. <br><br> 1. Jeśli używasz łącznika hr, sprawdź, czy łącznik HR wysyła poprawne dane <br><br> LUB <br><br> 2. Wybierz zdarzenie wyzwalające usunięcie konta usługi Azure AD.|
|Żadne urządzenia nie są dołączone|— Kradzież danych przez odchodzących użytkowników <br> — Ogólne przecieki danych <br> — Wycieki danych przez niezadowolonych użytkowników <br> — Wycieki danych według użytkowników o priorytecie|Wskaźniki urządzenia są wybierane, ale nie ma żadnych urządzeń dołączonych do platformy Microsoft 365 <br><br> Sprawdź, czy urządzenia są dołączone i spełniają wymagania.|
|Łącznik hr nie przekazał ostatnio danych|— Kradzież danych przez odchodzącego użytkownika <br> — Naruszenia zasad zabezpieczeń przez odchodzącego użytkownika <br> — Wycieki danych przez niezadowolonych użytkowników <br> — Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników|Łącznik hr nie zaimportował danych od ponad 7 dni. <br><br> Sprawdź, czy łącznik hr jest poprawnie skonfigurowany i wysyła dane.|
|Nie możemy teraz sprawdzić stanu łącznika hr. Sprawdź ponownie później|— Kradzież danych przez odchodzącego użytkownika <br> — Naruszenia zasad zabezpieczeń przez odchodzącego użytkownika <br> — Wycieki danych przez niezadowolonych użytkowników <br> — Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników|Rozwiązanie do zarządzania ryzykiem wewnętrznym nie może sprawdzić stanu łącznika hr. <br><br> Sprawdź, czy łącznik hr jest poprawnie skonfigurowany i wysyła dane, lub wróć i sprawdź stan zasad.|
|Zasady DLP nie są wybierane jako zdarzenie wyzwalające|— Ogólne przecieki danych <br> — Wycieki danych według użytkowników o priorytecie|Zasady DLP nie zostały wybrane jako zdarzenie wyzwalające lub wybrane zasady DLP zostały usunięte. <br><br> Edytuj zasady i wybierz aktywne zasady DLP lub "Użytkownik wykonuje działanie eksfiltracji" jako zdarzenie wyzwalające w konfiguracji zasad.|
|Zasady DLP używane w tych zasadach są wyłączone|— Ogólne przecieki danych <br> — Wycieki danych według użytkowników o priorytecie|Zasady DLP używane w tych zasadach są wyłączone. <br><br> 1. Włącz zasady DLP przypisane do tych zasad. <br><br> LUB <br><br> 2. Edytuj te zasady i wybierz nowe zasady DLP lub "Użytkownik wykonuje działanie eksfiltracji" jako zdarzenie wyzwalające w konfiguracji zasad.|
|Zasady DLP nie spełniają wymagań|— Ogólne przecieki danych <br> — Wycieki danych według użytkowników o priorytecie|Zasady DLP używane jako wyzwalające zdarzenia muszą być skonfigurowane do generowania alertów o wysokiej ważności. <br><br>  1. Edytuj zasady DLP, aby przypisać odpowiednie alerty jako *o wysokiej ważności*. <br><br> LUB <br><br> 2. Edytuj te zasady i wybierz *pozycję Użytkownik wykonuje działanie eksfiltracji* jako zdarzenie wyzwalające.|
|Twoja organizacja nie ma subskrypcji usługi Microsoft Defender for Endpoint|— Ogólne naruszenia zasad zabezpieczeń <br> — Naruszenia zasad zabezpieczeń przez odchodzących użytkowników <br> — Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników <br> — Naruszenia zasad zabezpieczeń przez użytkowników o priorytecie|Aktywna subskrypcja usługi Microsoft Defender dla punktu końcowego nie została wykryta dla Twojej organizacji. <br><br> Dopóki nie zostanie dodana subskrypcja usługi Microsoft Defender dla punktu końcowego, te zasady nie przypisują wyników ryzyka do działań użytkowników.|
|Alerty usługi Microsoft Defender dla punktów końcowych nie są udostępniane portalowi zgodności|— Ogólne naruszenia zasad zabezpieczeń <br> — Naruszenia zasad zabezpieczeń przez odchodzących użytkowników <br> — Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników <br> — Naruszenia zasad zabezpieczeń przez użytkowników o priorytecie|Alerty programu Microsoft Defender dla punktów końcowych nie są udostępniane portalowi zgodności. <br><br> Konfigurowanie udostępniania alertów usługi Microsoft Defender dla punktów końcowych.|
|Zbliżasz się do maksymalnego limitu użytkowników aktywnie ocenianych dla tego szablonu zasad.|Wszystkie szablony zasad|Każdy szablon zasad ma maksymalną liczbę użytkowników w zakresie. Zobacz szczegóły sekcji limitu szablonu. <br><br> Przejrzyj użytkowników na karcie Użytkownicy i usuń wszystkich użytkowników, którzy nie muszą już być oceniani.|
|Wyzwalanie zdarzenia jest wielokrotnie występujące dla ponad 15% użytkowników w tych zasadach.|Wszystkie szablony zasad|Dostosuj zdarzenie wyzwalające, aby zmniejszyć częstotliwość wprowadzania użytkowników do zakresu zasad.|

## <a name="policy-template-limits"></a>Limity szablonów zasad

Szablony zasad zarządzania ryzykiem wewnętrznym używają limitów do zarządzania ilością i szybkością przetwarzania działań związanych z ryzykiem użytkownika w zakresie oraz sposobem integracji tego procesu z obsługą usług Platformy Microsoft 365. Każdy szablon zasad ma maksymalną liczbę użytkowników, którzy mogą być aktywnie przypisywani do oceny ryzyka dla zasad, które mogą obsługiwać i skutecznie przetwarzać i raportować działania związane z ryzykiem. Użytkownicy w zakresie to użytkownicy z wyzwalaniem zdarzeń dla zasad.

Limit dla poszczególnych zasad jest obliczany na podstawie łącznej liczby unikatowych użytkowników otrzymujących wyniki ryzyka na typ szablonu zasad. Jeśli liczba użytkowników dla typu szablonu zasad jest bliska lub przekracza limit użytkownika, wydajność zasad zostanie zmniejszona. Aby wyświetlić bieżącą liczbę użytkowników zasad, przejdź do karty Zasady i kolumny Użytkownicy w zakresie. Dla dowolnego szablonu zasad może być maksymalnie pięć zasad. Te maksymalne limity dotyczą użytkowników we wszystkich zasadach korzystających z danego szablonu zasad.

Użyj poniższej tabeli, aby określić maksymalną liczbę użytkowników w zakresie obsługiwanych dla każdego szablonu zasad:

|Szablon zasad|Bieżąca maksymalna liczba użytkowników w zakresie|
|---|---|
|Ogólny wyciek danych|15,000|
|Wyciek danych przez niezadowolonych użytkowników|7,500|
|Wyciek danych według priorytetowych użytkowników|1,000|
|Kradzież danych przez odchodzących użytkowników|20,000|
|Ogólne naruszenia zasad zabezpieczeń|1,000|
|Ogólne nieprawidłowe wykorzystanie danych pacjentów|5,000|
|Naruszenie zasad zabezpieczeń przez użytkowników priorytetowych|1,000|
|Naruszenia zasad zabezpieczeń przez odchodzących użytkowników|15,000|
|Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników|7,500|

## <a name="create-a-new-policy"></a>Tworzenie nowych zasad

Aby utworzyć nowe zasady zarządzania ryzykiem wewnętrznym, użyjesz kreatora zasad w rozwiązaniu **do zarządzania ryzykiem wewnętrznym** w portalu zgodności usługi Microsoft Purview.

Wykonaj następujące kroki, aby utworzyć nowe zasady:

1. W [portalu zgodności usługi Microsoft Purview przejdź do obszaru](https://compliance.microsoft.com) **Zarządzanie ryzykiem niejawnym** i wybierz kartę **Zasady** .
2. Wybierz pozycję **Utwórz zasady** , aby otworzyć kreatora zasad.
3. Na stronie **Szablon zasad** wybierz kategorię zasad, a następnie wybierz szablon dla nowych zasad. Te szablony składają się z warunków i wskaźników definiujących działania związane z ryzykiem, które chcesz wykryć i zbadać. Zapoznaj się z wymaganiami wstępnymi szablonu, wyzwalaniem zdarzeń i wykrytymi działaniami, aby potwierdzić, że ten szablon zasad spełnia Twoje potrzeby.

    > [!IMPORTANT]
    > Niektóre szablony zasad mają wymagania wstępne, które należy skonfigurować, aby zasady generowały odpowiednie alerty. Jeśli nie skonfigurowano odpowiednich wymagań wstępnych zasad, zobacz **Krok 4** powyżej.

4. Wybierz przycisk **Dalej**, aby kontynuować.
5. Na stronie **Nazwa i opis** wypełnij następujące pola:
    - **Nazwa (wymagana)**: wprowadź przyjazną nazwę zasad. Tej nazwy nie można zmienić po utworzeniu zasad.
    - **Opis (opcjonalnie)**: wprowadź opis zasad.

6. Wybierz przycisk **Dalej**, aby kontynuować.
7. Na stronie **Użytkownicy i grupy** wybierz pozycję **Dołącz wszystkich użytkowników i grupy** lub **Uwzględnij określonych użytkowników i grupy** , aby określić, którzy użytkownicy lub grupy są uwzględniane w zasadach, lub jeśli wybrano szablon oparty na priorytetach użytkowników; wybierz pozycję **Dodaj lub edytuj grupy użytkowników o priorytecie**. Wybranie pozycji **Uwzględnij wszystkich użytkowników i grupy** spowoduje wyszukanie wyzwalania zdarzeń dla wszystkich użytkowników i grup w organizacji w celu rozpoczęcia przypisywania wyników ryzyka dla zasad. Wybranie pozycji **Uwzględnij określonych użytkowników i grupy** umożliwia zdefiniowanie użytkowników i grup do przypisania do zasad. Konta użytkowników-gości nie są obsługiwane.
8. Wybierz przycisk **Dalej**, aby kontynuować.
9. Na stronie **Zawartość do określania priorytetów** można przypisać (w razie potrzeby) źródła do priorytetyzacji, co zwiększa prawdopodobieństwo wygenerowania alertu o wysokiej ważności dla tych źródeł. Wybierz jedną z następujących opcji:

    - **Chcę określić witryny programu SharePoint, etykiety poufności i/lub typy informacji poufnych jako zawartość priorytetu**. Wybranie tej opcji spowoduje włączenie stron szczegółów w kreatorze w celu skonfigurowania tych kanałów.
    - **Nie chcę teraz określać priorytetowej zawartości (będzie można to zrobić po utworzeniu zasad).** Wybranie tej opcji spowoduje pominięcie stron szczegółów kanału w kreatorze.

10. Wybierz przycisk **Dalej**, aby kontynuować.

11. Jeśli wybrano **opcję Chcę określić witryny programu SharePoint, etykiety poufności, typy informacji poufnych i/lub rozszerzenia plików jako zawartość priorytetu** w poprzednim kroku, zobaczysz strony szczegółów *witryn programu SharePoint*, *typy informacji poufnych*, *etykiety poufności* i *rozszerzenia plików*. Użyj tych stron szczegółów, aby zdefiniować program SharePoint, typy informacji poufnych i etykiety poufności w celu określenia priorytetów w zasadach.

    - **Witryny programu SharePoint**: wybierz pozycję **Dodaj witrynę programu SharePoint** i wybierz witryny programu SharePoint, do których masz dostęp, i chcesz określić priorytety. Na przykład *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Typ informacji poufnych**: wybierz pozycję **Dodaj typ informacji poufnych** i wybierz typy poufności, które chcesz nadać priorytet. Na przykład *"Numer konta bankowego w Stanach Zjednoczonych"* i *"Numer karty kredytowej"*.
    - **Etykiety poufności**: wybierz pozycję **Dodaj etykietę poufności** i wybierz etykiety, które chcesz nadać priorytet. Na przykład *"Poufne"* i *"Tajne"*.
    - **Rozszerzenia plików**: dodaj do 50 rozszerzeń plików. Możesz dołączyć lub pominąć "". z rozszerzeniem pliku. Na przykład plik *py* lub *py* określa priorytety plików języka Python.

    >[!NOTE]
    >Użytkownicy konfigurujący zasady i wybierający priorytetowe witryny share point mogą wybrać witryny programu SharePoint, do których mają uprawnienia dostępu. Jeśli witryny programu SharePoint nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może wybrać witryny dla zasad później lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.

12. Wybierz przycisk **Dalej**, aby kontynuować.
13. Jeśli wybrano *szablony Ogólne wycieki danych* lub *Wycieki danych według priorytetowych użytkowników* , na stronie **Wyzwalacze** dla tych zasad zostaną wyświetlone opcje niestandardowych zdarzeń wyzwalania i wskaźników zasad. Możesz wybrać zasady DLP lub wskaźniki wyzwalania zdarzeń, które umożliwiają użytkownikom przypisanym do zasad w zakresie oceniania działań. Jeśli **wybierzesz opcję User matches a data loss prevention (DLP) policy triggering event (User matches a data loss prevention( DLP),** musisz wybrać zasady DLP z listy rozwijanej zasad DLP, aby włączyć wyzwalanie wskaźników dla zasad DLP dla tych zasad zarządzania ryzykiem wewnętrznym. Jeśli **wybierzesz opcję User performs an exfiltration activity triggering event (Użytkownik wykonuje działanie eksfiltracji wyzwalające zdarzenie** ), musisz wybrać co najmniej jeden z wymienionych wskaźników dla zdarzenia wyzwalającego zasady.
    >[!IMPORTANT]
    >Jeśli nie możesz wybrać wymienionego wskaźnika, jest to spowodowane tym, że nie są one włączone dla Twojej organizacji. Aby udostępnić je do wybrania i przypisania do zasad, włącz wskaźniki w **obszarze Wskaźniki zasad** **zarządzania** >  >  **ryzykiem wewnętrznym**.

    Jeśli wybrano inne szablony zasad, niestandardowe zdarzenia wyzwalania nie są obsługiwane. Mają zastosowanie wbudowane zdarzenia wyzwalające zasady i przejdziesz do kroku 23 bez definiowania atrybutów zasad.

14. Wybierz przycisk **Dalej**, aby kontynuować.
15. Jeśli wybrano *szablony Ogólne wycieki danych* lub *Wycieki danych według priorytetowych użytkowników* i wybrano, że **użytkownik wykonuje działanie eksfiltracji i skojarzone wskaźniki**, możesz wybrać progi niestandardowe lub domyślne dla wybranych zdarzeń wyzwalających wskaźnik. Wybierz pozycję **Użyj progów domyślnych (zalecane)** lub **Użyj progów niestandardowych dla wyzwalających zdarzeń**.
16. Wybierz przycisk **Dalej**, aby kontynuować.
17. Jeśli wybrano pozycję **Użyj niestandardowych progów dla zdarzeń wyzwalających**, dla każdego wskaźnika zdarzenia wyzwalającego wybranego w kroku 13 wybierz odpowiedni poziom, aby wygenerować żądany poziom alertów dotyczących działań.
18. Wybierz przycisk **Dalej**, aby kontynuować.
19. Na stronie **Wskaźniki zasad** zostaną wyświetlone [wskaźniki](insider-risk-management-settings.md#indicators) zdefiniowane jako dostępne na stronie **Wskaźniki** ryzyka  > **niejawne**. Wybierz wskaźniki, które chcesz zastosować do zasad.

    > [!IMPORTANT]
    > Jeśli nie można wybrać wskaźników na tej stronie, musisz wybrać wskaźniki, które chcesz włączyć dla wszystkich zasad. Możesz użyć przycisku **Włącz wskaźniki** w kreatorze lub wybrać wskaźniki na stronie **Wskaźniki zasad** **zarządzania** >  >  **ryzykiem wewnętrznym**.

    Jeśli wybrano co najmniej jeden wskaźnik *pakietu Office* lub *urządzenia* , wybierz odpowiednio **dopalacze oceny ryzyka** . Dopalacze oceny ryzyka mają zastosowanie tylko w przypadku wybranych wskaźników.
    Jeśli wybrano szablon zasad *Kradzież danych* lub *Wycieki danych* , wybierz co najmniej jedną metodę **wykrywania sekwencji** i metodę **wykrywania zbiorczej eksfiltracji** , która ma zostać zastosowana do zasad.

20. Wybierz przycisk **Dalej**, aby kontynuować.
21. Na stronie **Zdecyduj, czy mają być używane domyślne, czy niestandardowe progi wskaźników** , wybierz progi niestandardowe lub domyślne dla wybranych wskaźników zasad. Wybierz pozycję **Użyj domyślnych progów dla wszystkich wskaźników** lub **Określ progi niestandardowe dla wybranych** wskaźników zasad. Jeśli wybrano pozycję Określ progi niestandardowe, wybierz odpowiedni poziom, aby wygenerować żądany poziom alertów aktywności dla każdego wskaźnika zasad.
22. Wybierz przycisk **Dalej**, aby kontynuować.
23. Na stronie **Przegląd** przejrzyj ustawienia wybrane dla zasad oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz pozycję **Edytuj** , aby zmienić dowolną z wartości zasad, lub wybierz pozycję **Prześlij** , aby utworzyć i aktywować zasady.

## <a name="update-a-policy"></a>Aktualizowanie zasad

Aby zaktualizować istniejące zasady zarządzania ryzykiem wewnętrznym, użyj kreatora zasad w rozwiązaniu **do zarządzania ryzykiem wewnętrznym** w portalu zgodności usługi Microsoft Purview.

Wykonaj następujące kroki, aby zarządzać istniejącymi zasadami:

1. W [portalu zgodności usługi Microsoft Purview przejdź do obszaru](https://compliance.microsoft.com) **Zarządzanie ryzykiem niejawnym** i wybierz kartę **Zasady** .
2. Na pulpicie nawigacyjnym zasad wybierz zasady, które chcesz zarządzać.
3. Na stronie szczegółów zasad wybierz pozycję **Edytuj zasady**
4. W kreatorze zasad nie można edytować następujących elementów:
    - **Szablon zasad**: szablon używany do definiowania typów wskaźników ryzyka monitorowanych przez zasady.
    - **Nazwa**: przyjazna nazwa zasad
5. Na stronie **Nazwa i opis** zaktualizuj opis zasad w polu **Opis** .
6. Wybierz przycisk **Dalej**, aby kontynuować.
7. Na stronie **Użytkownicy i grupy** wybierz pozycję **Dołącz wszystkich użytkowników i grupy** lub **Uwzględnij określonych użytkowników i grupy** , aby określić, którzy użytkownicy lub grupy są uwzględniane w zasadach, lub jeśli wybrano szablon oparty na priorytetach użytkowników; wybierz pozycję **Dodaj lub edytuj grupy użytkowników o priorytecie**. Wybranie pozycji **Uwzględnij wszystkich użytkowników i grupy** spowoduje wyszukanie wyzwalania zdarzeń dla wszystkich użytkowników i grup w organizacji w celu rozpoczęcia przypisywania wyników ryzyka dla zasad. Wybranie pozycji **Uwzględnij określonych użytkowników i grupy** umożliwia zdefiniowanie użytkowników i grup do przypisania do zasad. Konta użytkowników-gości nie są obsługiwane.
8. Wybierz przycisk **Dalej**, aby kontynuować.
9. Na stronie **Zawartość do określania priorytetów** można przypisać (w razie potrzeby) źródła do priorytetyzacji, co zwiększa prawdopodobieństwo wygenerowania alertu o wysokiej ważności dla tych źródeł. Wybierz jedną z następujących opcji:

    - **Chcę określić witryny programu SharePoint, etykiety poufności, typy informacji poufnych i/lub rozszerzenia plików jako zawartość priorytetu**. Wybranie tej opcji spowoduje włączenie stron szczegółów w kreatorze w celu skonfigurowania tych kanałów.
    - **Nie chcę teraz określać priorytetowej zawartości (będzie można to zrobić po utworzeniu zasad).** Wybranie tej opcji spowoduje pominięcie stron szczegółów kanału w kreatorze.

10. Wybierz przycisk **Dalej**, aby kontynuować.

11. Jeśli wybrano **opcję Chcę określić witryny programu SharePoint, etykiety poufności i/lub typy informacji poufnych jako zawartość priorytetu** w poprzednim kroku, zobaczysz strony szczegółów *witryn programu SharePoint*, *typy informacji poufnych* i *etykiety poufności*. Użyj tych stron szczegółów, aby zdefiniować program SharePoint, typy informacji poufnych i etykiety poufności w celu określenia priorytetów w zasadach.

    - **Witryny programu SharePoint**: wybierz pozycję **Dodaj witrynę programu SharePoint** i wybierz witryny programu SharePoint, do których masz dostęp, i chcesz określić priorytety. Na przykład *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Typ informacji poufnych**: wybierz pozycję **Dodaj typ informacji poufnych** i wybierz typy poufności, które chcesz nadać priorytet. Na przykład *"Numer konta bankowego w Stanach Zjednoczonych"* i *"Numer karty kredytowej"*.
    - **Etykiety poufności**: wybierz pozycję **Dodaj etykietę poufności** i wybierz etykiety, które chcesz nadać priorytet. Na przykład *"Poufne"* i *"Tajne"*.
    - **Rozszerzenia plików**: dodaj do 50 rozszerzeń plików. Możesz dołączyć lub pominąć "". z rozszerzeniem pliku. Na przykład plik *py* lub *py* określa priorytety plików języka Python.

    >[!NOTE]
    >Użytkownicy konfigurujący zasady i wybierający priorytetowe witryny share point mogą wybrać witryny programu SharePoint, do których mają uprawnienia dostępu. Jeśli witryny programu SharePoint nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może wybrać witryny dla zasad później lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.

12. Wybierz przycisk **Dalej**, aby kontynuować.
13. Jeśli wybrano *szablony Ogólne wycieki danych* lub *Wycieki danych według priorytetowych użytkowników* , na stronie **Wyzwalacze** dla tych zasad zostaną wyświetlone opcje niestandardowych zdarzeń wyzwalania i wskaźników zasad. Możesz wybrać zasady DLP lub wskaźniki wyzwalania zdarzeń, które umożliwiają użytkownikom przypisanym do zasad w zakresie oceniania działań. Jeśli **wybierzesz opcję User matches a data loss prevention (DLP) policy triggering event (User matches a data loss prevention( DLP),** musisz wybrać zasady DLP z listy rozwijanej zasad DLP, aby włączyć wyzwalanie wskaźników dla zasad DLP dla tych zasad zarządzania ryzykiem wewnętrznym. Jeśli **wybierzesz opcję User performs an exfiltration activity triggering event (Użytkownik wykonuje działanie eksfiltracji wyzwalające zdarzenie** ), musisz wybrać co najmniej jeden z wymienionych wskaźników dla zdarzenia wyzwalającego zasady.
    >[!IMPORTANT]
    >Jeśli nie możesz wybrać wymienionego wskaźnika, jest to spowodowane tym, że nie są one włączone dla Twojej organizacji. Aby udostępnić je do wybrania i przypisania do zasad, włącz wskaźniki w **obszarze Wskaźniki zasad** **zarządzania** >  >  **ryzykiem wewnętrznym**.

    Jeśli wybrano inne szablony zasad, niestandardowe zdarzenia wyzwalania nie są obsługiwane. Mają zastosowanie wbudowane zdarzenia wyzwalające zasady i przejdziesz do kroku 23 bez definiowania atrybutów zasad.

14. Wybierz przycisk **Dalej**, aby kontynuować.
15. Jeśli wybrano *szablony Ogólne wycieki danych* lub *Wycieki danych według priorytetowych użytkowników* i wybrano, że **użytkownik wykonuje działanie eksfiltracji i skojarzone wskaźniki**, możesz wybrać progi niestandardowe lub domyślne dla wybranych zdarzeń wyzwalających wskaźnik. Wybierz pozycję **Użyj progów domyślnych (zalecane)** lub **Użyj progów niestandardowych dla wyzwalających zdarzeń**.
16. Wybierz przycisk **Dalej**, aby kontynuować.
17. Jeśli wybrano pozycję **Użyj niestandardowych progów dla zdarzeń wyzwalających**, dla każdego wskaźnika zdarzenia wyzwalającego wybranego w kroku 13 wybierz odpowiedni poziom, aby wygenerować żądany poziom alertów dotyczących działań.
18. Wybierz przycisk **Dalej**, aby kontynuować.
19. Na stronie **Wskaźniki zasad** zostaną wyświetlone [wskaźniki](insider-risk-management-settings.md#indicators) zdefiniowane jako dostępne na stronie **Wskaźniki** ryzyka  > **niejawne**. Wybierz wskaźniki, które chcesz zastosować do zasad.

    > [!IMPORTANT]
    > Jeśli nie można wybrać wskaźników na tej stronie, musisz wybrać wskaźniki, które chcesz włączyć dla wszystkich zasad. Możesz użyć przycisku **Włącz wskaźniki** w kreatorze lub wybrać wskaźniki na stronie **Wskaźniki zasad** **zarządzania** >  >  **ryzykiem wewnętrznym**.

    Jeśli wybrano co najmniej jeden wskaźnik *pakietu Office* lub *urządzenia* , wybierz odpowiednio **dopalacze oceny ryzyka** . Dopalacze oceny ryzyka mają zastosowanie tylko w przypadku wybranych wskaźników.
    Jeśli wybrano szablon zasad *Kradzież danych* lub *Wycieki danych* , wybierz co najmniej jedną metodę **wykrywania sekwencji** i metodę **wykrywania zbiorczej eksfiltracji** , która ma zostać zastosowana do zasad.

20. Wybierz przycisk **Dalej**, aby kontynuować.
21. Na stronie **Zdecyduj, czy mają być używane domyślne, czy niestandardowe progi wskaźników** , wybierz progi niestandardowe lub domyślne dla wybranych wskaźników zasad. Wybierz pozycję **Użyj domyślnych progów dla wszystkich wskaźników** lub **Określ progi niestandardowe dla wybranych** wskaźników zasad. Jeśli wybrano pozycję Określ progi niestandardowe, wybierz odpowiedni poziom, aby wygenerować żądany poziom alertów aktywności dla każdego wskaźnika zasad.
22. Wybierz przycisk **Dalej**, aby kontynuować.
23. Na stronie **Przegląd** przejrzyj ustawienia wybrane dla zasad oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz pozycję **Edytuj** , aby zmienić dowolną z wartości zasad, lub wybierz pozycję **Prześlij** , aby utworzyć i aktywować zasady.

## <a name="copy-a-policy"></a>Kopiowanie zasad

Może być konieczne utworzenie nowych zasad, które są podobne do istniejących zasad, ale wymagają tylko kilku zmian konfiguracji. Zamiast tworzyć nowe zasady od podstaw, można skopiować istniejące zasady, a następnie zmodyfikować obszary, które należy zaktualizować w nowych zasadach.

Wykonaj następujące kroki, aby skopiować istniejące zasady:

1. W [portalu zgodności usługi Microsoft Purview przejdź do obszaru](https://compliance.microsoft.com) **Zarządzanie ryzykiem niejawnym** i wybierz kartę **Zasady** .
2. Na pulpicie nawigacyjnym zasad wybierz zasady, które chcesz skopiować.
3. Na stronie szczegółów zasad wybierz pozycję Kopiuj.
4. W kreatorze zasad nadaj nowe zasady nazwę i zaktualizuj konfigurację zasad zgodnie z potrzebami.

## <a name="immediately-start-scoring-user-activity"></a>Natychmiast rozpocznij ocenianie działania użytkownika

Mogą wystąpić scenariusze, w których należy natychmiast zacząć przypisywać wyniki ryzyka użytkownikom z zasadami ryzyka wewnętrznego poza przepływem pracy wyzwalającym zdarzenie zarządzania ryzykiem wewnętrznym. Użyj **opcji Rozpocznij ocenianie dla użytkowników** na karcie **Zasady** , aby ręcznie dodać użytkownika (lub użytkowników) do co najmniej jednej zasady ryzyka wewnętrznego przez określony czas, aby natychmiast rozpocząć przypisywanie wyników ryzyka do swojej aktywności i pominąć wymaganie, aby użytkownik miał wskaźnik wyzwalania (na przykład dopasowanie zasad DLP). Możesz również dodać przyczynę dodania użytkownika do zasad, która będzie wyświetlana na osi czasu aktywności użytkowników. Użytkownicy ręcznie dodani do zasad są wyświetlani na pulpicie nawigacyjnym **Użytkownicy** , a alerty są tworzone, jeśli działanie spełnia progi alertów zasad.

Niektóre scenariusze, w których można natychmiast rozpocząć ocenianie działań użytkowników:

- Gdy użytkownicy są identyfikowane z problemami dotyczącymi ryzyka i chcesz natychmiast zacząć przypisywać wyniki ryzyka do swojej aktywności dla co najmniej jednej zasady
- W przypadku wystąpienia incydentu, który może wymagać natychmiastowego rozpoczęcia przypisywania wyników ryzyka do działań związanych z użytkownikami dla co najmniej jednej zasady
- Jeśli łącznik hr nie został jeszcze skonfigurowany, ale chcesz zacząć przypisywać wyniki ryzyka do działań użytkowników dla zdarzeń kadr, przekazując plik .csv dla użytkowników

> [!NOTE]
> Pojawienie się nowych użytkowników dodanych ręcznie na pulpicie nawigacyjnym **Użytkownicy** może potrwać kilka godzin. Wyświetlenie działań z poprzednich 90 dni dla tych użytkowników może potrwać do 24 godzin. Aby wyświetlić działania dla użytkowników dodanych ręcznie, przejdź do karty **Użytkownicy** i wybierz użytkownika na pulpicie **nawigacyjnym Użytkownicy** i otwórz kartę **Aktywność użytkownika** w okienku szczegółów.

Aby ręcznie rozpocząć działanie oceniania dla użytkowników w co najmniej jednej polityce zarządzania ryzykiem wewnętrznym, wykonaj następujące kroki:

1. W [portalu zgodności usługi Microsoft Purview przejdź do obszaru](https://compliance.microsoft.com) **Zarządzanie ryzykiem niejawnym** i wybierz kartę **Zasady** .
2. Na pulpicie nawigacyjnym zasad wybierz zasady lub zasady, do które chcesz dodać użytkowników.
3. Wybierz pozycję **Rozpocznij działanie oceniania dla użytkowników**.
4. W **polu Przyczyna** w okienku **Dodawanie użytkowników do wielu zasad** dodaj przyczynę dodania użytkowników.
5. W polu **To powinno trwać (wybierz od 5 do 30 dni)** zdefiniuj liczbę dni, aby ocenić aktywność użytkownika dla zasad, do których zostały dodane
6. Aby wyszukać użytkowników w usłudze Active Directory, użyj pola **Wyszukaj użytkownika w celu dodania do zasad** . Wpisz nazwę użytkownika, którego chcesz dodać do zasad. Wybierz nazwę użytkownika i powtórz, aby przypisać dodatkowych użytkowników do zasad. Lista wybranych użytkowników zostanie wyświetlona w sekcji Użytkownicy w okienku Dodawanie użytkowników do wielu zasad.
7. Aby zaimportować listę użytkowników do dodania do zasad, wybierz pozycję **Importuj** , aby zaimportować plik .csv (wartości rozdzielone przecinkami). Plik musi mieć następujący format i musisz wyświetlić listę nazw głównych użytkowników w pliku:

    ```csv
    user principal name
    user1@domain.com
    user2@domain.com
    ```

8. Wybierz pozycję Dodaj użytkowników do zasad, aby zaakceptować zmiany i dodać użytkowników do zasad, lub wybierz pozycję Anuluj, aby odrzucić zmiany i zamknąć okno dialogowe.

## <a name="stop-scoring-users-in-a-policy"></a>Zatrzymywanie oceniania użytkowników w zasadach

Aby zatrzymać ocenianie użytkowników w zasadach, zobacz artykuł [Insider risk management users: Remove users from in-scope assignment to policies (Użytkownicy zarządzania ryzykiem wewnętrznym: usuwanie użytkowników z przypisywania w zakresie do zasad](insider-risk-management-users.md#remove-users-from-in-scope-assignment-to-policies) ).

## <a name="delete-a-policy"></a>Usuwanie zasad

> [!NOTE]
> Usunięcie zasad nie powoduje usunięcia aktywnych ani zarchiwizowanych alertów wygenerowanych na podstawie zasad.

Aby usunąć istniejące zasady zarządzania ryzykiem wewnętrznym, wykonaj następujące kroki:

1. W [portalu zgodności usługi Microsoft Purview przejdź do obszaru](https://compliance.microsoft.com) **Zarządzanie ryzykiem niejawnym** i wybierz kartę **Zasady** .
2. Na pulpicie nawigacyjnym zasad wybierz zasady, które chcesz usunąć.
3. Wybierz pozycję **Usuń** na pasku narzędzi pulpitu nawigacyjnego.
4. W oknie dialogowym **Usuwanie** wybierz pozycję **Tak** , aby usunąć zasady, lub wybierz pozycję **Anuluj** , aby zamknąć okno dialogowe.
