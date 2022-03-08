---
title: Wprowadzenie do zarządzania ryzykiem w niejawnym programie testów
description: Skonfiguruj zarządzanie ryzykiem w niejawnym programie testów w organizacji.
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
ms.openlocfilehash: e21d2904ec2afdcd57b69267f99af6a0726dca56
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314633"
---
# <a name="get-started-with-insider-risk-management"></a>Wprowadzenie do zarządzania ryzykiem w niejawnym programie testów

Zasady zarządzania ryzykiem w niejawnym programie testów pozwalają identyfikować ryzykowne działania i narzędzia do zarządzania w celu działania na podstawie alertów o ryzyku w organizacji. Wykonaj poniższe czynności, aby skonfigurować wymagania wstępne i zasady zarządzania ryzykiem w niejawnym programie testów.

> [!IMPORTANT]
> Rozwiązanie Microsoft 365 zarządzania ryzykiem w niejawnym programie testów udostępnia opcję na poziomie dzierżawy ułatwianą klientom usprawnianie wewnętrznego zarządzania na poziomie użytkowników. Administratorzy na poziomie dzierżawy mogą skonfigurować uprawnienia w celu zapewnienia członkom organizacji dostępu do tego rozwiązania oraz skonfigurować łączniki danych w p Centrum zgodności platformy Microsoft 365 w celu importowania odpowiednich danych w celu obsługi identyfikacji na poziomie użytkownika potencjalnie ryzykownych działań. Klienci potwierdzają szczegółowe informacje związane z zachowaniem, znakiem lub wydajnością poszczególnych użytkowników w sposób materialny związany z zatrudnieniem. Mogą zostać obliczone przez administratora i udostępnione innym osobom w organizacji. Ponadto klienci wiedzą, że muszą przeprowadzić własne pełne badanie dotyczące zachowań, znaków lub wydajności poszczególnych użytkowników w sposób materialny związany z zatrudnieniem, a nie tylko opierać się na szczegółowych informacjach z usługi zarządzania ryzykiem w niejawnym programie testów. Klienci są wyłączną odpowiedzialnością za korzystanie z usługi Microsoft 365 zarządzania ryzykiem w ramach niejawnego programu testów oraz za wszelkie skojarzone funkcje lub usługi zgodnie ze wszystkimi obowiązującymi przepisami prawa, łącznie z przepisami prawnymi dotyczącymi identyfikacji użytkowników oraz działań naprawczych.

Aby uzyskać więcej informacji o tym, w jaki sposób zasady ryzyka niejawnego programu testów mogą ułatwić zarządzanie ryzykiem w organizacji, zobacz Zarządzanie ryzykiem w niejawnym [programie testów w programie Microsoft 365](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Subskrypcje i licencjonowanie

Przed rozpoczęciem pracy z zarządzaniem ryzykiem w ramach niejawnego programu testów należy potwierdzić Microsoft 365 [subskrypcji](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszystkich dodatków. Aby uzyskać dostęp do zarządzania ryzykiem w ramach niejawnego programu testów i korzystać z niego, Twoja organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- Microsoft 365 E5/A5/G5 (płatna lub próbna)
- Microsoft 365 E3/A3/G3 + Microsoft 365 E5 zgodności ze standardem Microsoft 365 E5/A5/G5
- Microsoft 365 E3/A3/G3 + Microsoft 365 E5/A5/G5 zarządzanie ryzykiem niejawnego programu testów
- Office 365 E3 + Enterprise Mobility and Security E3 + Zgodność platformy Microsoft 365 E5 pakietu

Użytkownikom uwzględnionym w zasadach zarządzania ryzykiem w niejawnym programie testów należy przypisać jedną z powyższych licencji.

> [!IMPORTANT]
> Zarządzanie ryzykiem w ramach niejawnego programu testów jest obecnie dostępne w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi Azure. Aby sprawdzić, czy zarządzanie ryzykiem niejawnego programu testów jest obsługiwane w Twojej organizacji, zobacz Dostępność platformy [Azure zależności według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

Jeśli nie masz jeszcze planu Microsoft 365 Enterprise E5 i chcesz wypróbować zarządzanie ryzykiem w ramach niejawnego programu testów, możesz dodać usługę [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji lub utworzyć konto w [](https://www.microsoft.com/microsoft-365/enterprise) celu wypróbowania usługi Microsoft 365 Enterprise E5.

## <a name="recommended-actions-preview"></a>Zalecane akcje (wersja zapoznawcza)

Zalecane działania mogą ułatwić Twojej organizacji szybkie rozpoczynanie pracy i wyeksymendować wszystkie możliwości w zakresie zarządzania ryzykiem w ramach niejawnego programu testów. Na stronie **Przegląd** zalecane akcje ułatwiają konfigurowanie i wdrażanie zasad oraz akcje badania dotyczące akcji użytkownika generujące alerty na podstawie dopasowania zasad.

![Zalecane działania w ramach zarządzania ryzykiem w ramach niejawnego programu testów.](../media/insider-risk-recommended-actions.png)

Dostępne są następujące zalecenia, które pomogą Ci rozpocząć pracę lub zmaksymalizować konfigurację zarządzania ryzykiem w niejawnym programie testów:

- **Włączanie inspekcji**: Gdy jest włączona, działania użytkowników i administratorów w organizacji są rejestrowane w Microsoft 365 inspekcji. Przy użyciu tego dziennika do wykrywania działań ryzyka są wykrywane zasady i skany analizy w ramach niejawnego programu testów.
- **Uzyskiwanie uprawnień do zarządzania ryzykiem użytkowników**: Poziom dostępu do funkcji zarządzania ryzykiem w niejawnym programie testów zależy od przypisanej do Ciebie grupy ról. Aby uzyskać dostęp do zalecanych akcji i je skonfigurować, należy przypisać użytkowników  do grup ról Zarządzanie ryzykiem niejawnego programu testów lub *Administratorów* zarządzania ryzykiem w ramach niejawnego programu testów.
- **Wybierz wskaźniki zasad**: Wskaźniki to zasadniczo działania użytkowników, które chcesz wykrywać i badać. Możesz wybrać wskaźniki do śledzenia aktywności w kilku Microsoft 365 lokalizacjach i usługach.
- **Skanuj w poszukiwaniu potencjalnych czynników** ryzyka w ramach niejawnego programu testów. Uruchom skanowanie analizy, aby wykryć potencjalne zagrożenia niejawnego programu testów w organizacji. Po dokonaniu oceny wyników przejrzyj zalecane zasady, które należy skonfigurować.
- **Przypisywanie uprawnień innym** osobom: Jeśli za zarządzanie funkcjami ryzyka niejawnego programu testów są odpowiedzialni dodatkowi członkowie zespołu, należy przypisać ich do odpowiednich grup ról.
- **Tworzenie pierwszej zasady**: Aby otrzymywać alerty o potencjalnie ryzykownych działaniach, musisz skonfigurować zasady na podstawie wstępnie zdefiniowanych szablonów definiujące działania użytkowników, które mają być wykrywane i analizowane.
- **Przeglądanie sprawdzanych** aktywności użytkowników: Pulpit nawigacyjny Użytkownicy  umożliwia wyświetlanie użytkowników, którym obecnie są przypisywane wyniki ryzyka, niezależnie od tego, czy to działanie spełnia próg wygenerowania alertu.
- **Przeglądanie alertów**: Po wyzwoleniu zdarzenia użytkownika zasady zaczynają przypisywać oceny ryzyka do wykrytych działań. Jeśli punkt ryzyka spełnia progi zasad, zostanie wyświetlony alert zawierający szczegółowy wykaz wyników wszystkich aktywności dla tego użytkownika.
- **Badanie sprawy**: Sprawy są tworzone ręcznie na podstawie alertów, gdy jest konieczne dalsze badanie w celu zidentyfikowania potencjalnych zagrożeń w niejawnym programie testów. Zakres każdej sprawy jest ograniczony do jednego użytkownika, a do istniejącej lub nowej sprawy można dodać wiele alertów dla użytkownika.

Każda zalecana akcja zawarta w tym doświadczeniu ma cztery atrybuty:

- **Akcja**: Nazwa i opis zalecanej akcji.
- **Stan**: stan zalecanej akcji. Wartości to *: Nie rozpoczęto*, *W toku*, *Zapisane na później* lub *Ukończone*.
- **Wymagane lub opcjonalne: czy** zalecane działanie jest wymagane, czy opcjonalne, aby funkcje zarządzania ryzykiem w niejawnym programie testów działały zgodnie z oczekiwaniami.
- **Szacowany czas wykonania**: Szacowany czas wykonania zalecanej akcji w minutach.

Wybierz z listy zalecenie, aby rozpocząć konfigurowanie zarządzania ryzykiem w niejawnym programie testów. Każda zalecana akcja przeprowadzi Cię przez działania wymagane do zalecenia, w tym wymagania, czego można oczekiwać i jaki wpływ ma skonfigurowanie tej funkcji w organizacji.   Każda zalecana akcja jest automatycznie oznaczana jako ukończona po skonfigurowaniu lub trzeba ręcznie wybrać akcję jako ukończoną podczas konfigurowania.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Krok 1 (wymagany): Włączanie uprawnień do zarządzania ryzykiem w niejawnym programie testów

> [!IMPORTANT]
> Po skonfigurowaniu grup ról może upłynąć do 30 minut, aby uprawnienia grupy ról dotyczyły przypisanych użytkowników w organizacji.

Do konfigurowania funkcji zarządzania ryzykiem w niejawnym programie testów jest używanych sześć grup ról. Aby **udostępnić** zarządzanie ryzykiem w niejawnym programie testów jako opcję menu w programie Centrum zgodności platformy Microsoft 365 i kontynuować te kroki konfiguracji, musisz mieć przypisaną jedną z następujących ról lub grup ról:

- Azure Active Directory [*administrator globalny*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*administratora*](/azure/active-directory/roles/permissions-reference#compliance-administrator) zgodności
- Centrum zgodności platformy Microsoft 365 [*ról Zarządzanie*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organizacją
- Centrum zgodności platformy Microsoft 365 [*ról Administrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) zgodności
- *Grupa ról Zarządzanie ryzykiem w niejawnym* programie testów
- *Grupa ról Administrator zarządzania ryzykiem w niejawnym programie* testów

W zależności od tego, jak chcesz zarządzać zasadami i alertami zarządzania ryzykiem w niejawnym programie testów, konieczne będzie przypisanie użytkowników do określonych grup ról w celu zarządzania różnymi zestawami funkcji zarządzania ryzykiem w niejawnym programie testów. Możesz przypisać użytkownikom różne obowiązki dotyczące zgodności z przepisami do określonych grup ról w celu zarządzania różnymi obszarami funkcji zarządzania ryzykiem w niejawnym programie testów. Możesz także przypisać wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, osób oglądających i osoby przeglądowe do grupy ról Zarządzanie ryzykiem w niejawnym programie testów. Korzystaj z jednej lub wielu grup ról, aby jak najlepiej dopasować się do wymagań zarządzania zgodnością.

Podczas pracy z zarządzaniem ryzykiem w ramach niejawnego programu testów będziesz wybierać spośród tych opcji grupy ról i akcji rozwiązania:

|**Akcje**|**Zarządzanie ryzykiem w niejawnym programie testów**|**Administrator zarządzania ryzykiem w niejawnym programie testów**|**Analitycy zarządzania ryzykiem wewnętrznym**|**Badacze zarządzania ryzykiem wewnętrznym**|**Audytorzy zarządzania ryzykiem w niejawnym programie testów**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Konfigurowanie zasad i ustawień | Tak | Tak | Nie | Nie | Nie |
| Szczegółowe informacje dotyczące analizy programu Access | Tak | Tak | Tak | Nie | Nie |
| Alerty & zbadać w programie Access | Tak | Nie | Tak | Tak | Nie |
| Uzyskiwanie dostępu & zbadania spraw | Tak | Nie | Tak | Tak | Nie |
| Uzyskiwanie & widoku Eksploratora zawartości | Tak | Nie | Nie | Tak | Nie |
| Konfigurowanie szablonów z powiadomieniami | Tak | Nie | Tak | Tak | Nie |
| Wyświetlanie & eksportowania dzienników inspekcji | Tak | Nie | Nie | Nie | Tak |

>[!IMPORTANT]
>Upewnij się, że w grupach ról Zarządzanie ryzykiem niejawnego programu testów  lub Administrator zarządzania ryzykiem w niejawnym programie testów (w zależności od wybranej opcji) zawsze jest co najmniej jeden użytkownik, aby konfiguracja zarządzania ryzykiem w niejawnym programie testów nie była dostępna w przypadku opuszczenia organizacji przez określonych użytkowników.

Członkowie poniższych ról mogą przypisywać użytkowników do grup ról zarządzania ryzykiem w niejawnym programie testów i mieć te same uprawnienia rozwiązania, które są zawarte w grupie ról Administrator zarządzania ryzykiem w niejawnym programie *testów* :

- Azure Active Directory *administrator globalny*
- Azure Active Directory *administratora zgodności*
- Centrum zgodności platformy Microsoft 365 *zarządzanie organizacją*
- Centrum zgodności platformy Microsoft 365 *zgodności*

> [!NOTE]
> Te grupy ról nie są obecnie obsługiwane Privileged Identity Management (PIM). Aby dowiedzieć się więcej o usłudze PIM, zobacz [Przypisywanie ról usługi Azure AD w usłudze Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Dodawanie użytkowników do grupy ról zarządzania ryzykiem w niejawnym programie testów

Wykonaj następujące czynności, aby dodać użytkowników do grupy ról zarządzania ryzykiem w niejawnym programie testów:

1. Zaloguj się [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w Twojej Microsoft 365 organizacji.

2. W Centrum zgodności &amp; zabezpieczeń przejdź **do uprawnień.** Wybierz link, aby wyświetlić role i zarządzać nimi w Office 365.

3. Wybierz grupę ról zarządzanie ryzykiem w niejawnym programie testów, do której chcesz dodać użytkowników, a następnie wybierz pozycję **Edytuj grupę ról**.

4. Wybierz **pozycję Wybierz członków** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytuj**.

5. Wybierz **pozycję** Dodaj, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz dodać do grupy ról.

6. Wybierz **pozycję Dodaj**, a następnie pozycję **Gotowe**.

7. Wybierz **pozycję Zapisz** , aby dodać użytkowników do grupy ról. Wybierz **pozycję Zamknij** , aby ukończyć procedurę.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>Krok 2 (wymagany): włączanie dziennika Microsoft 365 inspekcji

W zarządzaniu ryzykiem w ramach niejawnego programu testów Microsoft 365 dzienników inspekcji w celu analizy informacji użytkowników i działań zidentyfikowanych w zasadach i analizach. Dzienniki Microsoft 365 inspekcji to podsumowanie wszystkich działań w organizacji, a zasady zarządzania ryzykiem w niejawnym programie testów mogą używać tych działań do generowania szczegółowych informacji o zasadach.

Inspekcja jest domyślnie włączona Microsoft 365 organizacji. Niektóre organizacje mogą wyłączyć inspekcję z określonych powodów. Jeśli w Twojej organizacji inspekcja jest wyłączona, może to być spowodowane tym, że inny administrator wyłączył ją. Zalecamy potwierdzenie, że po wykonaniu tego kroku można ponownie włączyć inspekcję.

Aby uzyskać instrukcje krok po kroku dotyczące dotyczące włączanie inspekcji, zobacz Włączanie lub wyłączanie przeszukiwania [dziennika inspekcji](turn-audit-log-search-on-or-off.md). Po włączeniu inspekcji jest wyświetlany komunikat informujący, że dziennik inspekcji jest przygotowywany i że po upływie kilku godzin od zakończenia przygotowywania można uruchomić wyszukiwanie. Wystarczy wykonać tę czynność tylko raz. Aby uzyskać więcej informacji na temat korzystania z Microsoft 365 inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>Krok 3 (opcjonalnie): Włączanie i wyświetlanie szczegółowych informacji z analizy ryzyka w niejawnym programie testów

Analiza ryzyka w niejawnym programie testów umożliwia przeprowadzenie oceny potencjalnych czynników ryzyka niejawnego programu testów w organizacji bez konfigurowania żadnych zasad ryzyka niejawnego programu testów. Ocena ta może ułatwić organizacji zidentyfikowanie potencjalnych obszarów o wyższym poziomie ryzyka użytkownika oraz określenie typu i zakresu zasad zarządzania ryzykiem niejawnego programu testów, które można rozważyć podczas konfigurowania. Ocena ta może również pomóc w określeniu potrzeb w zakresie dodatkowego licencjonowania lub przyszłej optymalizacji istniejących zasad. Wyniki analizy mogą zająć do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przejrzenia. Aby dowiedzieć się więcej o szczegółowych informacjach dotyczących analiz, zobacz Ustawienia zarządzania ryzykiem w ramach niejawnego [](https://www.youtube.com/watch?v=5c0P5MCXNXk) programu testów[:](insider-risk-management-settings.md#analytics) analiza i obejrzyj klip wideo z analizą ryzyka w ramach niejawnego programu testów, aby ułatwić zrozumienie tego, jak analizy mogą pomóc przyspieszyć identyfikację potencjalnych czynników ryzyka w niejawnym programie testów i pomóc w szybkiej podjęciu działań.

Aby włączyć analizę ryzyka niejawnego programu testów, musisz być członkiem grupy ról Zarządzanie ryzykiem niejawnego programu testów *, administratora* zarządzania ryzykiem niejawnego programu testów *Microsoft 365 grupy* ról administratora globalnego.

Wykonaj poniższe czynności, aby włączyć analizę ryzyka niejawnego programu testów:

1. W centrum [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) do tematu Zarządzanie **ryzykiem w niejawnym programie testów**.
2. Wybierz **pozycję Uruchom skanowanie** na karcie Skanowanie w poszukiwaniu czynników ryzyka w niejawnym programie **testów** na karcie Przegląd zarządzania ryzykiem w niejawnym **programie** testów. Ta czynność włącza skanowanie analiz dla organizacji. Możesz również włączyć skanowanie  >  w organizacji, przechodząc do ustawień ryzyka niejawnego programu testówAnalytics i włączając skanowanie aktywności użytkowników w dzierżawie, aby zidentyfikować **potencjalne zagrożenia w niejawnym programie testów**.
3. W **okienku szczegółów analizy** wybierz pozycję **Uruchom skanowanie, aby rozpocząć skanowanie dla organizacji**. Wyniki analizy mogą zająć do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przejrzenia.

Po przejrzeniu szczegółowych informacji z analiz wybierz zasady ryzyka niejawnego programu testów i skonfiguruj skojarzone wymagania wstępne, które najlepiej spełniają strategię ograniczania ryzyka niejawnego programu testów Twojej organizacji.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>Krok 4 (zalecany): Konfigurowanie wymagań wstępnych zasad

Większość zasad zarządzania ryzykiem w niejawnym programie testów ma wymagania wstępne, które muszą zostać skonfigurowane pod warunkiem, że wskaźniki zasad będą generować alerty dotyczące odpowiednich działań. Skonfiguruj odpowiednie wymagania wstępne w zależności od zasad, które zamierzasz skonfigurować dla organizacji.

### <a name="configure-microsoft-365-hr-connector"></a>Konfigurowanie Microsoft 365 kadr

Zarządzanie ryzykiem w niejawnym programie testów umożliwia importowanie danych użytkowników i dzienników zaimportowanych z platform innych firm do zarządzania ryzykiem i kadr. Łącznik danych Microsoft 365 kadr umożliwia pobierania danych z zasobów ludzkich z plików CSV, takich jak daty zakończenia pracy użytkownika, daty ostatniego zatrudnienia, powiadomienia planu poprawy wydajności, działania w ramach przeglądu wydajności i stan zmiany stanowiska. Te dane pomagają chronić wskaźniki alertów w zasadach zarządzania ryzykiem w ramach niejawnego programu testów i są ważnym elementem konfigurowania pełnego zarządzania ryzykiem w organizacji. Jeśli skonfigurujesz dla organizacji więcej niż jeden łącznik kadr, zarządzanie ryzykiem niejawnego programu testów będzie automatycznie pobierać wskaźniki ze wszystkich łączników hr.

Łącznik Microsoft 365 kadr jest wymagany w przypadku korzystania z następujących szablonów zasad:

- Wycieki danych przez niezadowoniętych użytkowników
- Odchodzące kradzieże danych użytkowników
- Ogólne niewłaściwe użycie danych pacjenta
- Naruszenia zasad zabezpieczeń przez odchodzące użytkowników
- Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników

Zobacz artykuł [Konfigurowanie łącznika do](import-hr-data.md) importowania danych hr, aby uzyskać szczegółowe instrukcje dotyczące konfigurowania łącznika Microsoft 365 kadr dla organizacji. Po skonfigurowaniu łącznika kadr wróć do tych kroków konfiguracji.

### <a name="configure--a-healthcare-specific-data-connector"></a>Konfigurowanie łącznika danych specyficznego dla opieki zdrowotnej

Zarządzanie ryzykiem niejawnego programu testów umożliwia importowanie danych użytkowników i dzienników zaimportowanych od innych firm w istniejących systemach elektronicznej dokumentacji medycznej (EMR). Łączniki danych Microsoft Healthcare i Docx umożliwiają pobierania danych aktywności z systemu EMR za pomocą plików CSV, w tym nieprawidłowego dostępu do rejestrów pacjentów, podejrzanych działań w zakresie obrotu oraz edytowania i eksportowania działań. Te dane pomagają chronić wskaźniki alertów w zasadach zarządzania ryzykiem w ramach niejawnego programu testów i są ważnym elementem konfigurowania pełnego zarządzania ryzykiem w organizacji.

Jeśli skonfigurujesz dla organizacji więcej niż jeden łącznik opieki zdrowotnej lub łącznik Na tym łączniku, zarządzanie ryzykiem w ramach niejawnego programu testów automatycznie obsługuje sygnały dotyczące zdarzeń i działań ze wszystkich łączników opieki zdrowotnej i usług cyfrowych.
Łącznik Microsoft 365 Healthcare lub Na tym łączniku jest wymagany w przypadku korzystania z następujących szablonów zasad:

- Ogólne niewłaściwe użycie danych pacjenta

Zobacz artykuł [Konfigurowanie](import-healthcare-data.md) łącznika do importowania danych opieki zdrowotnej lub Konfigurowanie łącznika do importowania danych [OHR](import-epic-data.md) , aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika opieki zdrowotnej dla organizacji. Po skonfigurowaniu łącznika wróć do tych kroków konfiguracji.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Konfigurowanie zasad ochrony przed utratą danych (DLP, Data Loss Prevention)

Zarządzanie ryzykiem w niejawnym programie testów umożliwia stosowanie zasad DLP w celu zidentyfikowania celowego lub przypadkowego kontaktu z niepożądanymi podmiotami w przypadku alertów DLP o wysokim poziomie ważności. Konfigurując zasady zarządzania ryzykiem w niejawnym programie testów przy użyciu dowolnego szablonu wycieków danych, możesz przypisać do nich określone zasady DLP dla tych typów alertów.

Zasady DLP ułatwiają identyfikowanie użytkowników w celu aktywowania oceny ryzyka w zarządzaniu ryzykiem niejawnego programu testów dla alertów DLP o wysokim poziomie ważności dla informacji poufnych i są ważnym elementem konfigurowania pełnego zakresu zarządzania ryzykiem w organizacji. Aby uzyskać więcej informacji na temat zarządzania ryzykiem w niejawnym programie testów oraz kwestii integracji i planowania zasad DLP, zobacz [Zasady zarządzania ryzykiem w niejawnym programie testów](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Upewnij się, że zostały ukończone następujące czynności:
>
>- Rozumiesz i poprawnie konfigurujesz użytkowników w zakresie, zarówno w zasadach ochrony przed ryzykiem w niejawnym programie testów, jak i w celu uzyskania odpowiedniego zakresu zasad.
>- Upewnij się, **że ustawienie Raporty o incydentach** w zasadach DLP dotyczących zarządzania ryzykiem w niejawnym programie testów używanej z tymi szablonami jest skonfigurowane dla alertów o wysokim poziomie ważności. Alerty zarządzania ryzykiem w niejawnym programie testów nie będą generowane na podstawie  zasad DLP z polem Raporty o incydentach ustawionym na *wartość Niski* lub *Średni*.

Zasady DLP są opcjonalne w przypadku korzystania z następujących szablonów zasad:

- Ogólne wycieki danych
- Wycieki danych według priorytetowych użytkowników

Zobacz artykuł [Tworzenie, testowanie](create-test-tune-dlp-policy.md) i dostosowywanie zasad DLP, aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad DLP dla organizacji. Po skonfigurowaniu zasad DLP wróć do tych kroków konfiguracji.

### <a name="configure-priority-user-groups"></a>Konfigurowanie priorytetowych grup użytkowników

Zarządzanie ryzykiem w niejawnym programie testów obejmuje obsługę przypisywania priorytetowych grup użytkowników do zasad, aby ułatwić tożsamości unikatowych działań ryzyka dla użytkowników o krytycznych stanowiskach, wysokich poziomach danych i dostępu do sieci lub historii zachowań ryzyka w przeszłości. Utworzenie grupy użytkowników o priorytecie i przypisanie użytkowników do grupy zakresów pomocy grupy na unikatowe okoliczności przedstawione przez tych użytkowników.

W przypadku korzystania z następujących szablonów zasad wymagana jest grupa użytkowników o priorytecie:

- Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych
- Wycieki danych według priorytetowych użytkowników

Zobacz artykuł [Wprowadzenie do ustawień zarządzania](insider-risk-management-settings.md#priority-user-groups-preview) ryzykiem w niejawnym programie testów, aby uzyskać szczegółowe wskazówki dotyczące tworzenia grupy użytkowników o priorytecie. Po skonfigurowaniu grupy użytkowników o priorytecie wróć do tych kroków konfiguracji.

### <a name="configure-physical-badging-connector-optional"></a>Konfigurowanie łącznika z fizycznymi opcjami do wyboru (opcjonalnie)

Zarządzanie ryzykiem w niejawnym programie testów umożliwia importowanie danych użytkowników i dzienników z platform kontroli fizycznej i dostępu. Łącznik fizyczny umożliwiający uzyskiwanie dostępu do plików JSON, w tym identyfikatorów użytkowników, identyfikatorów punktów dostępu, godzin i dat dostępu oraz stanu dostępu. Te dane pomagają chronić wskaźniki alertów w zasadach zarządzania ryzykiem w ramach niejawnego programu testów i są ważnym elementem konfigurowania pełnego zarządzania ryzykiem w organizacji. Jeśli skonfigurujesz więcej niż jeden łącznik fizycznych do oszerowania w organizacji, zarządzanie ryzykiem w niejawnym programie testów automatycznie pobiera wskaźniki ze wszystkich łączników wybieranych fizycznie. Informacje z łącznika etykiet fizycznych uzupełnia inne sygnały ryzyka niejawnego programu testów podczas korzystania ze wszystkich szablonów zasad dotyczących ryzyka w niejawnym programie testów.

> [!IMPORTANT]
> Aby zasady zarządzania ryzykiem w niejawnym programie testów były wykorzystywane i skorelowane z danymi sygnału dotyczącymi odchodzijących i zakończonych użytkowników danymi zdarzeń z platformy kontroli fizycznej i dostępu, musisz również skonfigurować łącznik Microsoft 365 KADR. Jeśli włączysz łącznik fizyczny do zarządzania zabezpieczeniami bez włączania łącznika kadr w programie Microsoft 365, zasady zarządzania ryzykiem w niejawnym programie testów będą przetwarzać tylko zdarzenia nieautoryzowanego dostępu fizycznego dla użytkowników w organizacji.

Zobacz artykuł [Konfigurowanie łącznika do](import-physical-badging-data.md) importowania danych z fizycznymi zabezpieczeniami, aby uzyskać instrukcje krok po kroku dotyczące konfigurowania łącznika fizycznego do blokowania w organizacji. Po skonfigurowaniu łącznika wróć do tych kroków konfiguracji.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego (opcjonalnie)

[Program Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) to platforma zabezpieczeń punktów końcowych przedsiębiorstwa, która ma ułatwić sieciom przedsiębiorstwa zapobieganie zaawansowanym zagrożeniam, wykrywanie, badanie i reagowanie na nie. Aby poprawić widoczność naruszeń zabezpieczeń w organizacji, możesz zaimportować i odfiltrować usługę Defender, aby uzyskać alerty punktu końcowego w przypadku działań używanych w zasadach utworzonych na podstawie szablonów zasad naruszenia zabezpieczeń zarządzania ryzykiem w ramach niejawnego programu testów.

W przypadku tworzenia zasad naruszenia zabezpieczeń usługa Microsoft Defender for Endpoint musi być skonfigurowana w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem w niejawnym programie testów w Centrum zabezpieczeń Defender, aby importować alerty o naruszeniach zabezpieczeń. Aby uzyskać więcej informacji o wymaganiach, zobacz [artykuł Minimalne wymagania programu Microsoft Defender dla punktu końcowego](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) .

Zobacz artykuł [Konfigurowanie zaawansowanych funkcji w programie Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) , aby uzyskać szczegółowe instrukcje dotyczące konfigurowania programu Defender dla punktu końcowego na poziomie integracji zarządzania ryzykiem w niejawnym programie testów. Po skonfigurowaniu programu Microsoft Defender dla punktu końcowego wróć do tych kroków konfiguracji.

## <a name="step-5-required-configure-insider-risk-settings"></a>Krok 5 (wymagany): Konfigurowanie ustawień ryzyka niejawnego programu testów

[Ustawienia ryzyka niejawnego programu](insider-risk-management-settings.md) testów mają zastosowanie do wszystkich zasad zarządzania ryzykiem w niejawnym programie testów niezależnie od szablonu wybranego podczas tworzenia zasad. Ustawienia konfigurację przy **użyciu kontroli ustawień** ryzyka niejawnego programu testów znajdującej się u góry wszystkich kart zarządzania ryzykiem w niejawnym programie testów. Te ustawienia sterują prywatnością, wskaźnikami, monitorowaniem okien i inteligentnymi wykrywaniami.

Przed skonfigurowaniem zasad zdefiniuj następujące ustawienia ryzyka niejawnego programu testów:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie ryzykiem w niejawnym programie testów  i wybierz pozycję Ustawienia ryzyka niejawnego programu testów w prawym górnym rogu dowolnej strony.
2. Na stronie **Prywatność** wybierz ustawienie prywatności dotyczące wyświetlania nazw użytkowników dla alertów dotyczących zasad.
3. Na stronie **Wskaźniki** wybierz wskaźniki alertów, które chcesz zastosować do wszystkich zasad ryzyka w niejawnym programie testów.

    > [!IMPORTANT]
    > Aby otrzymywać alerty dotyczące ryzykownych działań zdefiniowanych w twoich zasadach, musisz wybrać jeden lub więcej wskaźników. Jeśli wskaźniki nie zostały skonfigurowane w programie Ustawienia, nie można ich wybrać w zasadach ryzyka w niejawnym programie testów.

4. Na **stronie Timeframes zasad** wybierz ramy czasowe zasad [](insider-risk-management-settings.md#policy-timeframes), które mają być stosowane dla użytkownika w przypadku wyzwalania dopasowania do zasad ryzyka niejawnego programu testów.
5. Na stronie **Inteligentne wykrywanie** skonfiguruj następujące ustawienia zasad ryzyka niejawnego programu testów:
    - [Wykluczenia typów plików](insider-risk-management-settings.md#file-type-exclusions)
    - [Minimalna liczba codziennych wydarzeń, aby zwiększyć liczbę wyników dla nietypowej aktywności](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Alert o poziomie głośności](insider-risk-management-settings.md#alert-volume)
    - [Stan alertu programu Microsoft Defender dla punktu końcowego](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Ustawienia domeny](insider-risk-management-settings.md#domains)
6. Na stronie **Eksportowanie alertów** włącz eksportowanie informacji alertów o ryzyku niejawnego programu testów przy użyciu Office 365 API zarządzania danymi.
7. Na stronie **Grupy użytkowników o priorytecie** utwórz grupę użytkowników o priorytecie i dodaj użytkowników, jeśli nie została utworzona w **kroku 3**.
8. Na stronie **Power Automate przepływów** skonfiguruj przepływ z szablonów przepływu ryzyka niejawnego programu testów lub utwórz nowy przepływ. Aby uzyskać szczegółowe instrukcje, zobacz artykuł Wprowadzenie do ustawień [zarządzania ryzykiem](insider-risk-management-settings.md#power-automate-flows-preview) w niejawnym programie testów.
9. Na stronie **Priority assets (Zasoby priorytetów**) skonfiguruj priorytetowe zasoby w celu używania danych z platformy kontroli fizycznej i dostępu zaimportowanych przez łącznik fizyczny do rezerwowania. Aby uzyskać szczegółowe instrukcje, zobacz artykuł Wprowadzenie do ustawień [zarządzania ryzykiem](insider-risk-management-settings.md#priority-physical-assets-preview) w niejawnym programie testów.
10. Na stronie **Microsoft Teams** włącz integrację programu Microsoft Teams z zarządzaniem ryzykiem w ramach niejawnego programu testów, aby automatycznie utworzyć zespół do współpracy nad sprawą lub z użytkownikiem. Aby uzyskać szczegółowe instrukcje, zobacz artykuł Wprowadzenie do ustawień [zarządzania ryzykiem](insider-risk-management-settings.md#microsoft-teams-preview) w niejawnym programie testów.
11. Wybierz **pozycję Zapisz** , aby włączyć te ustawienia dla zasad ryzyka niejawnego programu testów.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>Krok 6 (wymagany). Tworzenie zasad zarządzania ryzykiem w niejawnym programie testów

Zasady zarządzania ryzykiem w niejawnym programie testów obejmują przypisanych użytkowników i określają, jakie typy wskaźników ryzyka są konfigurowane dla alertów. Aby działania mogą wyzwalać alerty, należy skonfigurować zasady. Za pomocą kreatora zasad utwórz nowe zasady zarządzania ryzykiem w niejawnym programie testów.

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
13. Jeśli wybrano ogólne wycieki danych lub wycieki danych  według szablonów priorytetów użytkowników, na stronie Wyzwalacze tej zasady znajdziesz opcje dotyczące  niestandardowych zdarzeń i wskaźników zasad wyzwalania niestandardowego. Możesz wybrać zasady DLP lub wskaźniki służące do wyzwalania zdarzeń, które powodują przypisanie użytkowników do zakresu zasad oceniania aktywności. Jeśli wybierzesz opcję zdarzeń Zasady ochrony przed utratą danych **(DLP, Data Loss Prevention** ), wyzwalająco zdarzenie, musisz wybrać zasady DLP z listy rozwijanej zasad DLP, aby włączyć wskaźniki wyzwalania zasad DLP dla tych zasad zarządzania ryzykiem w niejawnym programie testów. Jeśli wybierzesz opcję **zdarzenia** wyzwolone przez użytkownika, należy wybrać jeden lub więcej ze wskaźników na liście dla zdarzenia wyzwalania zasad.
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

## <a name="next-steps"></a>Następne kroki

Po ukończeniu tych czynności w celu utworzenia pierwszych zasad zarządzania ryzykiem w niejawnym programie testów zaczniesz otrzymywać alerty ze wskaźników aktywności po upływie około 24 godzin. Skonfiguruj dodatkowe zasady zgodnie z potrzebami, używając wskazówek z kroku 4 tego artykułu lub kroków w artykule [Tworzenie nowych zasad ryzyka niejawnego programu testów](insider-risk-management-policies.md#create-a-new-policy).

Aby dowiedzieć się więcej o badaniach alertów o ryzyku niejawnego programu testów i **pulpitu nawigacyjnego alertów**, zobacz Działania związane z zarządzaniem [ryzykiem w niejawnym programie testów](insider-risk-management-activities.md#alert-dashboard).
