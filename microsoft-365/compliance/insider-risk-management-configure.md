---
title: Wprowadzenie do zarządzania ryzykiem wewnętrznym
description: Skonfiguruj zarządzanie ryzykiem wewnętrznym w organizacji.
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
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 8afb59606f4d13e96db5d4f03ffd8126c6ee9ba2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642574"
---
# <a name="get-started-with-insider-risk-management"></a>Wprowadzenie do zarządzania ryzykiem wewnętrznym

Użyj zasad zarządzania ryzykiem wewnętrznym, aby zidentyfikować ryzykowne działania i narzędzia do zarządzania, aby działać na alertach o podwyższonym ryzyku w organizacji. Wykonaj poniższe kroki, aby skonfigurować wymagania wstępne i skonfigurować zasady zarządzania ryzykiem wewnętrznym.

> [!IMPORTANT]
> Rozwiązanie do zarządzania ryzykiem wewnętrznym zapewnia opcję na poziomie dzierżawy, aby ułatwić klientom zarządzanie wewnętrzne na poziomie użytkownika. Administratorzy na poziomie dzierżawy mogą skonfigurować uprawnienia w celu zapewnienia dostępu do tego rozwiązania członkom organizacji i skonfigurować łączniki danych w portal zgodności Microsoft Purview w celu zaimportowania odpowiednich danych w celu obsługi identyfikacji na poziomie użytkownika potencjalnie ryzykownych działań. Klienci potwierdzają szczegółowe informacje dotyczące zachowania, charakteru lub wydajności poszczególnych użytkowników związane z zatrudnieniem, które mogą zostać obliczone przez administratora i udostępnione innym osobom w organizacji. Ponadto klienci przyznają, że muszą przeprowadzić własne pełne badanie dotyczące zachowania, charakteru lub wydajności poszczególnych użytkowników związane z zatrudnieniem, a nie tylko polegać na szczegółowych informacjach z usługi zarządzania ryzykiem wewnętrznym. Klienci są wyłącznie odpowiedzialni za korzystanie z usługi zarządzania ryzykiem wewnętrznym oraz wszelkich powiązanych funkcji lub usług zgodnie ze wszystkimi obowiązującymi przepisami, w tym przepisami dotyczącymi identyfikacji poszczególnych użytkowników i wszelkich działań korygujących.

Aby uzyskać więcej informacji na temat sposobu, w jaki zasady ryzyka wewnętrznego mogą pomóc w zarządzaniu ryzykiem w organizacji, zobacz [Informacje o zarządzaniu ryzykiem wewnętrznym](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Subskrypcje i licencjonowanie

Przed rozpoczęciem zarządzania ryzykiem wewnętrznym należy potwierdzić [subskrypcję platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszelkie dodatki. Aby uzyskać dostęp do zarządzania ryzykiem wewnętrznym i korzystać z niego, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- subskrypcja Microsoft 365 E5/A5/F5/G5 (wersja płatna lub próbna)
- subskrypcja Microsoft 365 E3/A3/F3/G3 + dodatek zgodności Microsoft 365 E5/A5/F5/G5
- subskrypcja Microsoft 365 E3/A3/F3/G3 + dodatek Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- subskrypcja Office 365 E3 + pakiet Enterprise Mobility and Security E3 + dodatek Zgodność platformy Microsoft 365 E5

Użytkownikom uwzględnionym w zasadach zarządzania ryzykiem wewnętrznym należy przypisać jedną z powyższych licencji.

> [!IMPORTANT]
> Zarządzanie ryzykiem wewnętrznym jest obecnie dostępne w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi platformy Azure. Aby sprawdzić, czy zarządzanie ryzykiem wewnętrznym jest obsługiwane w organizacji, zobacz [Dostępność zależności platformy Azure według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

Jeśli nie masz istniejącego planu Microsoft 365 Enterprise E5 i chcesz wypróbować zarządzanie ryzykiem wewnętrznym, możesz dodać platformę [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji lub [utworzyć konto próbne](https://www.microsoft.com/microsoft-365/enterprise) Microsoft 365 Enterprise E5.

## <a name="recommended-actions-preview"></a>Zalecane akcje (wersja zapoznawcza)

Zalecane akcje mogą pomóc organizacji szybko uzyskać dostęp do zarządzania ryzykiem wewnętrznym. Zalecane akcje zawarte na stronie **Przegląd** ułatwiają wykonanie kroków konfigurowania i wdrażania zasad.

![Zalecane akcje dotyczące zarządzania ryzykiem wewnętrznym.](../media/insider-risk-recommended-actions.png)

Dostępne są następujące zalecenia, które pomogą Ci rozpocząć pracę lub zmaksymalizować konfigurację zarządzania ryzykiem wewnętrznym:

- **Włącz inspekcję**: po włączeniu działania użytkownika i administratora w organizacji są rejestrowane w dzienniku inspekcji platformy Microsoft 365. Zasady ryzyka wewnętrznego i skanowania analiz używają tego dziennika do wykrywania działań związanych z ryzykiem.
- **Uzyskiwanie uprawnień do zarządzania ryzykiem użytkowników**: poziom dostępu do funkcji zarządzania ryzykiem wewnętrznym zależy od przypisanej grupy ról. Aby uzyskać dostęp do zalecanych akcji i skonfigurować je, użytkownicy muszą być przypisani do grup ról *Insider Risk Management* lub *Insider Risk Management Admins* .
- **Wybierz wskaźniki zasad**: Wskaźniki są zasadniczo działaniami użytkownika, które chcesz wykryć i zbadać. Możesz wybrać wskaźniki do śledzenia aktywności w kilku lokalizacjach i usługach platformy Microsoft 365.
- **Skanowanie pod kątem potencjalnych zagrożeń związanych z poufnymi informacjami**: uruchom skanowanie analityczne, aby wykryć potencjalne zagrożenia dla osób poufnych występujące w organizacji. Po ocenie wyników przejrzyj zalecane zasady do skonfigurowania.
- **Przypisywanie uprawnień innym** osobom: jeśli są dodatkowi członkowie zespołu, którzy będą odpowiedzialni za zarządzanie funkcjami ryzyka wewnętrznego, musisz przypisać ich do odpowiednich grup ról.
- **Tworzenie pierwszych zasad**: aby otrzymywać alerty dotyczące potencjalnie ryzykownych działań, należy skonfigurować zasady na podstawie wstępnie zdefiniowanych szablonów definiujących działania użytkownika, które chcesz wykryć i zbadać.

Każda zalecana akcja uwzględniona w tym środowisku ma cztery atrybuty:

- **Akcja**: nazwa i opis zalecanej akcji.
- **Stan**: stan zalecanej akcji. Wartości nie są *uruchamiane*, *W toku*, *Zapisane na później* lub *Ukończono*.
- **Wymagane lub opcjonalne**: czy zalecana akcja jest wymagana, czy opcjonalna, aby funkcje zarządzania ryzykiem wewnętrznym działały zgodnie z oczekiwaniami.
- **Szacowany czas ukończenia**: szacowany czas wykonania zalecanej akcji w minutach.

Wybierz zalecenie z listy, aby rozpocząć konfigurowanie zarządzania ryzykiem wewnętrznym. Każda zalecana akcja przeprowadzi Cię przez wymagane działania dla zalecenia, w tym wszelkie wymagania, oczekiwane wymagania i wpływ konfigurowania funkcji w organizacji.   Każda zalecana akcja jest automatycznie oznaczana jako ukończona po skonfigurowaniu lub należy ręcznie wybrać akcję jako ukończoną po skonfigurowaniu.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Krok 1 (wymagane): Włączanie uprawnień do zarządzania ryzykiem wewnętrznym

> [!IMPORTANT]
> Po skonfigurowaniu grup ról stosowanie uprawnień grupy ról do przypisanych użytkowników w całej organizacji może potrwać do 30 minut.

Istnieje sześć grup ról używanych do konfigurowania funkcji zarządzania ryzykiem wewnętrznym. Aby udostępnić zarządzanie **ryzykiem niejawnym** jako opcję menu w portal zgodności Microsoft Purview i kontynuować te kroki konfiguracji, musisz mieć przypisaną jedną z następujących ról lub grup ról:

- Rola [*administratora globalnego*](/azure/active-directory/roles/permissions-reference#global-administrator) usługi Azure Active Directory
- Rola [*administratora zgodności*](/azure/active-directory/roles/permissions-reference#compliance-administrator) usługi Azure Active Directory
- grupa ról [*zarządzania organizacją*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portal zgodności Microsoft Purview
- grupa ról [*administratora zgodności*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portal zgodności Microsoft Purview
- *Grupa ról zarządzania ryzykiem wewnętrznym*
- *Grupa ról Administracja zarządzania ryzykiem wewnętrznym*

W zależności od sposobu zarządzania zasadami i alertami dotyczącymi zarządzania ryzykiem wewnętrznym należy przypisać użytkowników do określonych grup ról, aby zarządzać różnymi zestawami funkcji zarządzania ryzykiem wewnętrznym. Istnieje możliwość przypisania użytkowników z różnymi obowiązkami zgodności do określonych grup ról w celu zarządzania różnymi obszarami funkcji zarządzania ryzykiem wewnętrznym. Możesz też zdecydować się na przypisanie wszystkich kont użytkowników wyznaczonym administratorom, analitykom, badaczom i widzom do grupy ról Insider Risk Management. Użyj jednej grupy ról lub wielu grup ról, aby najlepiej dopasować wymagania dotyczące zarządzania zgodnością.

Podczas pracy z zarządzaniem ryzykiem wewnętrznym wybierzesz spośród tych opcji grupy ról i akcji rozwiązania:

|Działania|Zarządzanie ryzykiem wewnętrznym|Administracja zarządzania ryzykiem wewnętrznym|Analitycy zarządzania ryzykiem wewnętrznym|Badacze zarządzania ryzykiem wewnętrznym|Audytorzy zarządzania ryzykiem wewnętrznym|
|---|---|---|---|---|---|
|Konfigurowanie zasad i ustawień|Tak|Tak|Nie|Nie|Nie|
|Uzyskiwanie dostępu do szczegółowych informacji analitycznych|Tak|Tak|Tak|Nie|Nie|
|& dostępu bada alerty|Tak|Nie|Tak|Tak|Nie|
|& dostępu bada przypadki|Tak|Nie|Tak|Tak|Nie|
|Uzyskiwanie dostępu & wyświetlenie Eksploratora zawartości|Tak|Nie|Nie|Tak|Nie|
|Konfigurowanie szablonów powiadomień|Tak|Nie|Tak|Tak|Nie|
|Wyświetlanie dzienników inspekcji eksportu &|Tak|Nie|Nie|Nie|Tak|

> [!IMPORTANT]
> Upewnij się, że zawsze masz co najmniej jednego użytkownika w grupach ról insider *risk management* lub *insider risk management Administracja* (w zależności od wybranej opcji), aby konfiguracja zarządzania ryzykiem wewnętrznym nie wchodziła do scenariusza "zero administratora", jeśli konkretni użytkownicy opuszczają organizację.

Członkowie następujących ról mogą przypisywać użytkowników do grup ról zarządzania ryzykiem wewnętrznym i mieć te same uprawnienia rozwiązania dołączone do grupy ról *Administracja zarządzania ryzykiem wewnętrznym*:

- *Administrator globalny* usługi Azure Active Directory
- *Administrator zgodności* usługi Azure Active Directory
- *zarządzanie organizacją* portal zgodności Microsoft Purview
- *administrator zgodności* portal zgodności Microsoft Purview

> [!NOTE]
> Te grupy ról nie są obecnie obsługiwane w Privileged Identity Management (PIM). Aby dowiedzieć się więcej na temat usługi PIM, zobacz [Przypisywanie ról Azure AD w Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Dodawanie użytkowników do grupy ról zarządzania ryzykiem wewnętrznym

Wykonaj następujące kroki, aby dodać użytkowników do grupy ról zarządzania ryzykiem wewnętrznym:

1. Zaloguj się [do portal zgodności Microsoft Purview](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji platformy Microsoft 365.

2. W Centrum zgodności zabezpieczeń &amp; przejdź do pozycji **Uprawnienia**. Wybierz link, aby wyświetlić role i zarządzać nimi w Office 365.

3. Wybierz grupę ról zarządzania ryzykiem wewnętrznym, do którą chcesz dodać użytkowników, a następnie wybierz pozycję **Edytuj grupę ról**.

4. Wybierz pozycję **Wybierz członków** w okienku nawigacji po lewej stronie, a następnie wybierz pozycję **Edytuj**.

5. Wybierz pozycję **Dodaj** , a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy chcesz dodać do grupy ról.

6. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Gotowe**.

7. Wybierz pozycję **Zapisz** , aby dodać użytkowników do grupy ról. Wybierz pozycję **Zamknij** , aby wykonać kroki.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>Krok 2 (wymagane): Włączanie dziennika inspekcji platformy Microsoft 365

Zarządzanie ryzykiem wewnętrznym używa dzienników inspekcji platformy Microsoft 365 do uzyskiwania szczegółowych informacji o użytkownikach i działań zidentyfikowanych w zasadach i analizach szczegółowych informacji. Dzienniki inspekcji platformy Microsoft 365 są podsumowaniem wszystkich działań w organizacji, a zasady zarządzania ryzykiem wewnętrznym mogą używać tych działań do generowania szczegółowych informacji o zasadach.

Inspekcja jest domyślnie włączona dla organizacji platformy Microsoft 365. Niektóre organizacje mogły wyłączyć inspekcję z określonych powodów. Jeśli inspekcja jest wyłączona dla Twojej organizacji, może to być spowodowane tym, że inny administrator wyłączył tę inspekcję. Zalecamy potwierdzenie, że podczas wykonywania tego kroku można ponownie włączyć inspekcję.

Aby uzyskać instrukcje krok po kroku dotyczące włączania inspekcji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](turn-audit-log-search-on-or-off.md). Po włączeniu inspekcji zostanie wyświetlony komunikat informujący, że dziennik inspekcji jest przygotowywany i że wyszukiwanie można uruchomić w ciągu kilku godzin po zakończeniu przygotowywania. Tę akcję trzeba wykonać tylko raz. Aby uzyskać więcej informacji na temat korzystania z dziennika inspekcji platformy Microsoft 365, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>Krok 3 (opcjonalnie): Włączanie i wyświetlanie szczegółowych informacji na temat analizy ryzyka poufnych informacji

Analiza zarządzania ryzykiem wewnętrznym umożliwia przeprowadzenie oceny potencjalnych zagrożeń wewnętrznych w organizacji bez konfigurowania żadnych zasad ryzyka wewnętrznego. Ta ocena może pomóc twojej organizacji zidentyfikować potencjalne obszary o wyższym ryzyku użytkowników i pomóc w określeniu typu i zakresu zasad zarządzania ryzykiem wewnętrznym, które możesz rozważyć skonfigurowanie. Ta ocena może również pomóc w określeniu potrzeb dotyczących dodatkowego licencjonowania lub przyszłej optymalizacji istniejących zasad. Wyniki skanowania analizy mogą potrwać do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przeglądu. Aby dowiedzieć się więcej na temat szczegółowych informacji analitycznych, zobacz [Ustawienia zarządzania ryzykiem wewnętrznym: Analiza](insider-risk-management-settings.md#analytics) i zapoznaj się z [wideo Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) , aby dowiedzieć się, w jaki sposób analiza może pomóc przyspieszyć identyfikację potencjalnych zagrożeń wewnętrznych i pomóc w szybkim podjęciu działań.

Aby włączyć analizę ryzyka wewnętrznego, musisz być członkiem grupy roli *Administrator globalny* firmy Microsoft 365, zarządzania *ryzykiem wewnętrznym*, *zarządzania ryzykiem wewnętrznym Administracja*.

Wykonaj następujące kroki, aby włączyć analizę ryzyka wewnętrznego:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym**.
2. Wybierz pozycję **Uruchom skanowanie** na **karcie Skanuj w poszukiwaniu zagrożeń wewnętrznych na** karcie Zarządzanie ryzykiem wewnętrznym na karcie **Omówienie** . Ta akcja włącza skanowanie analityczne dla twojej organizacji. Skanowanie można również włączyć w organizacji, przechodząc do **pozycji Ustawienia** >  ryzyka niejawnych testerów **Analiza** i włączając opcję **Skanuj aktywność użytkownika dzierżawy w celu zidentyfikowania potencjalnych zagrożeń związanych z wewnętrznymi informacjami**.
3. W okienku **Szczegóły analizy** wybierz pozycję **Uruchom skanowanie, aby rozpocząć skanowanie w organizacji**. Wyniki skanowania analizy mogą potrwać do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przeglądu.

Po przejrzeniu szczegółowych informacji analitycznych wybierz zasady ryzyka wewnętrznego i skonfiguruj skojarzone wymagania wstępne, które najlepiej spełniają strategię ograniczania ryzyka związanego z ryzykiem wewnętrznym organizacji.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>Krok 4 (zalecane): Konfigurowanie wymagań wstępnych dotyczących zasad

Większość zasad zarządzania ryzykiem wewnętrznym ma wymagania wstępne, które muszą być skonfigurowane pod kątem wskaźników zasad w celu generowania odpowiednich alertów dotyczących działań. Skonfiguruj odpowiednie wymagania wstępne w zależności od zasad, które planujesz skonfigurować dla organizacji.

### <a name="configure-microsoft-365-hr-connector"></a>Konfigurowanie łącznika usługi Microsoft 365 HR

Zarządzanie ryzykiem wewnętrznym obsługuje importowanie danych użytkowników i dzienników zaimportowanych z platform zarządzania ryzykiem i zasobów ludzkich innych firm. Łącznik danych zasobów ludzkich (HR) platformy Microsoft 365 umożliwia pobieranie danych zasobów ludzkich z plików CSV, w tym dat zakończenia pracy użytkownika, dat ostatniego zatrudnienia, powiadomień dotyczących planu poprawy wydajności, akcji przeglądu wydajności i stanu zmiany poziomu zadań. Te dane ułatwiają określanie wskaźników alertów w zasadach zarządzania ryzykiem wewnętrznym i są ważnym elementem konfigurowania pełnego zakresu zarządzania ryzykiem w organizacji. Jeśli skonfigurujesz więcej niż jeden łącznik hr dla swojej organizacji, zarządzanie ryzykiem wewnętrznym będzie automatycznie ściągać wskaźniki ze wszystkich łączników hr.

Łącznik usługi Microsoft 365 HR jest wymagany podczas korzystania z następujących szablonów zasad:

- Wycieki danych przez niezadowolonych użytkowników
- Kradzież danych odchodzących użytkowników
- Ogólne nieprawidłowe wykorzystanie danych pacjentów
- Naruszenia zasad zabezpieczeń przez odchodzących użytkowników
- Naruszenia zasad zabezpieczeń przez niezadowolonych użytkowników

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika usługi Microsoft 365 HR dla organizacji, zobacz Artykuł [Konfigurowanie łącznika do importowania danych kadrowych](import-hr-data.md) . Po skonfigurowaniu łącznika HR wróć do tych kroków konfiguracji.

### <a name="configure--a-healthcare-specific-data-connector"></a>Konfigurowanie łącznika danych specyficznego dla opieki zdrowotnej

Zarządzanie ryzykiem wewnętrznym obsługuje importowanie danych użytkowników i dzienników zaimportowanych od innych firm w istniejących systemach elektronicznej dokumentacji medycznej (EMR). Łączniki danych Microsoft Healthcare i Epic umożliwiają ściąganie danych aktywności z systemu EMR przy użyciu plików CSV, w tym niewłaściwego dostępu do rekordów pacjentów, podejrzanych działań związanych z woluminami oraz edytowania i eksportowania działań. Te dane ułatwiają określanie wskaźników alertów w zasadach zarządzania ryzykiem wewnętrznym i są ważnym elementem konfigurowania pełnego zakresu zarządzania ryzykiem w organizacji.

Jeśli skonfigurujesz więcej niż jeden łącznik usługi Healthcare lub Epic dla swojej organizacji, zarządzanie ryzykiem wewnętrznym automatycznie obsługuje sygnały zdarzeń i działań ze wszystkich łączników healthcare i Epic.
Łącznik Microsoft 365 Healthcare lub Epic jest wymagany podczas korzystania z następujących szablonów zasad:

- Ogólne nieprawidłowe wykorzystanie danych pacjentów

Zobacz [Artykuł Konfigurowanie łącznika w celu importowania danych opieki zdrowotnej](import-healthcare-data.md) lub [Konfigurowanie łącznika w celu importowania danych epic EHR, aby](import-epic-data.md) uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika specyficznego dla opieki zdrowotnej dla organizacji. Po skonfigurowaniu łącznika wróć do tych kroków konfiguracji.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Konfigurowanie zasad ochrony przed utratą danych (DLP)

Zarządzanie ryzykiem wewnętrznym obsługuje używanie zasad DLP w celu zidentyfikowania zamierzonego lub przypadkowego ujawnienia poufnych informacji niepożądanym stronom w przypadku alertów DLP wysokiego poziomu ważności. Podczas konfigurowania zasad zarządzania ryzykiem wewnętrznym za pomocą dowolnego szablonu **Wycieki danych** możesz przypisać określone zasady DLP do zasad dla tych typów alertów.

Zasady DLP pomagają zidentyfikować użytkowników w celu aktywowania oceny ryzyka w zarządzaniu ryzykiem wewnętrznym w przypadku alertów DLP o wysokiej ważności dla informacji poufnych i są ważnym elementem konfigurowania pełnego pokrycia zarządzania ryzykiem w organizacji. Aby uzyskać więcej informacji na temat zarządzania ryzykiem wewnętrznym i zagadnień związanych z integracją i planowaniem zasad DLP, zobacz [Zasady zarządzania ryzykiem wewnętrznym](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Upewnij się, że wykonano następujące czynności:
>
> - Rozumiesz i prawidłowo konfigurujesz użytkowników w zakresie zarówno w zasadach DLP, jak i zasadach zarządzania ryzykiem wewnętrznym, aby uzyskać oczekiwany zakres zasad.
> - Upewnij się, że ustawienie **Raporty o zdarzeniach** w zasadach DLP na potrzeby zarządzania ryzykiem wewnętrznym używanym z tymi szablonami jest skonfigurowane dla alertów o *wysokiej* ważności. Alerty dotyczące zarządzania ryzykiem wewnętrznym nie będą generowane na podstawie zasad DLP z polem **Raporty o zdarzeniach** ustawionym na *wartość Niska* lub *Średnia*.

Zasady DLP są opcjonalne w przypadku korzystania z następujących szablonów zasad:

- Ogólne przecieki danych
- Wycieki danych według użytkowników o priorytecie

Zapoznaj się z [artykułem Tworzenie, testowanie i dostrajanie zasad DLP,](create-test-tune-dlp-policy.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania zasad DLP dla organizacji. Po skonfigurowaniu zasad DLP wróć do tych kroków konfiguracji.

### <a name="configure-priority-user-groups"></a>Konfigurowanie grup użytkowników o priorytecie

Zarządzanie ryzykiem wewnętrznym obejmuje obsługę przypisywania priorytetowych grup użytkowników do zasad w celu ułatwienia tożsamości unikatowych działań związanych z ryzykiem dla użytkowników z krytycznymi pozycjami, wysokiego poziomu danych i dostępu do sieci lub poprzedniej historii zachowań związanych z ryzykiem. Tworzenie grupy użytkowników o priorytecie i przypisywanie użytkowników do grupy pomaga w określaniu zakresu zasad w unikatowych okolicznościach przedstawionych przez tych użytkowników.

W przypadku korzystania z następujących szablonów zasad wymagana jest priorytetowa grupa użytkowników:

- Naruszenia zasad zabezpieczeń przez użytkowników o priorytecie
- Wycieki danych według użytkowników o priorytecie

Zapoznaj [się z artykułem Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#priority-user-groups-preview) , aby uzyskać szczegółowe wskazówki dotyczące tworzenia priorytetowej grupy użytkowników. Po skonfigurowaniu grupy użytkowników o priorytecie wróć do tych kroków konfiguracji.

### <a name="configure-physical-badging-connector-optional"></a>Konfigurowanie łącznika fizycznego rozwiązywania problemów (opcjonalnie)

Zarządzanie ryzykiem wewnętrznym obsługuje importowanie danych użytkowników i dzienników z platform kontroli fizycznej i dostępu. Łącznik fizycznego rozwiązywania problemów umożliwia ściąganie danych dostępu z plików JSON, w tym identyfikatorów użytkowników, identyfikatorów punktów dostępu, czasu i dat dostępu oraz stanu dostępu. Te dane ułatwiają określanie wskaźników alertów w zasadach zarządzania ryzykiem wewnętrznym i są ważnym elementem konfigurowania pełnego zakresu zarządzania ryzykiem w organizacji. Jeśli skonfigurujesz więcej niż jeden łącznik fizycznego rozwiązywania problemów dla swojej organizacji, zarządzanie ryzykiem wewnętrznym automatycznie ściąga wskaźniki ze wszystkich łączników fizycznego rozwiązywania problemów. Informacje z fizycznego łącznika badging uzupełniają inne sygnały ryzyka wewnętrznego podczas korzystania ze wszystkich szablonów zasad ryzyka wewnętrznego.

> [!IMPORTANT]
> Aby zasady zarządzania ryzykiem wewnętrznym używały i korelowały dane sygnału związane z odchodzących i zakończonymi użytkownikami z danymi zdarzeń z platform kontroli fizycznej i dostępu, należy również skonfigurować łącznik usługi Microsoft 365 HR. Jeśli włączysz łącznik fizycznego rozwiązywania problemów bez włączania łącznika usługi Microsoft 365 HR, zasady zarządzania ryzykiem wewnętrznym będą przetwarzać zdarzenia tylko w celu uzyskania nieautoryzowanego dostępu fizycznego dla użytkowników w organizacji.

Zapoznaj [się z artykułem Konfigurowanie łącznika do importowania fizycznych danych powodujących](import-physical-badging-data.md) błędy w zabezpieczeniach, aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika fizycznego rozwiązywania problemów dla organizacji. Po skonfigurowaniu łącznika wróć do tych kroków konfiguracji.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender (opcjonalnie)

[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) to platforma zabezpieczeń punktów końcowych przedsiębiorstwa, która pomaga sieciom przedsiębiorstw w zapobieganiu zaawansowanym zagrożeniom, wykrywaniu i badaniu ich oraz reagowaniu na nie. Aby mieć lepszy wgląd w naruszenia zabezpieczeń w organizacji, możesz importować i filtrować alerty usługi Defender dla punktu końcowego pod kątem działań używanych w zasadach utworzonych na podstawie szablonów zasad naruszenia zabezpieczeń zarządzania ryzykiem wewnętrznym.

Jeśli tworzysz zasady naruszenia zabezpieczeń, musisz skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender w organizacji i włączyć usługę Defender for Endpoint na potrzeby integracji zarządzania ryzykiem wewnętrznym w usłudze Defender Security Center, aby importować alerty naruszenia zabezpieczeń. Aby uzyskać więcej informacji na temat wymagań, zobacz artykuł [Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements).

Zobacz [artykuł Konfigurowanie zaawansowanych funkcji w usłudze Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) , aby uzyskać szczegółowe wskazówki dotyczące konfigurowania usługi Defender for Endpoint na potrzeby integracji zarządzania ryzykiem wewnętrznym. Po skonfigurowaniu Ochrona punktu końcowego w usłudze Microsoft Defender wróć do tych kroków konfiguracji.

## <a name="step-5-required-configure-insider-risk-settings"></a>Krok 5 (wymagane): Konfigurowanie ustawień ryzyka dla niejawnych testerów

[Ustawienia ryzyka niejawnego](insider-risk-management-settings.md) dostępu do informacji poufnych mają zastosowanie do wszystkich zasad zarządzania ryzykiem wewnętrznym, niezależnie od szablonu wybranego podczas tworzenia zasad. Ustawienia są konfigurowane przy użyciu kontroli **ustawień ryzyka niejawnych testerów** znajdującej się w górnej części wszystkich kart zarządzania ryzykiem wewnętrznym. Te ustawienia kontrolują prywatność, wskaźniki, okna monitorowania i inteligentne wykrywanie.

Przed skonfigurowaniem zasad zdefiniuj następujące ustawienia ryzyka wewnętrznego:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz pozycję **Ustawienia ryzyka niejawnych testerów** w prawym górnym rogu dowolnej strony.
2. Na stronie **Prywatność** wybierz ustawienie prywatności do wyświetlania nazw użytkowników alertów zasad.
3. Na stronie **Wskaźniki** wybierz wskaźniki alertów, które chcesz zastosować do wszystkich zasad ryzyka dotyczącego informacji poufnych.

    > [!IMPORTANT]
    > Aby otrzymywać alerty dotyczące ryzykownych działań zdefiniowanych w zasadach, należy wybrać co najmniej jeden wskaźnik. Jeśli wskaźniki nie są skonfigurowane w obszarze Ustawienia, wskaźniki nie będą wybierane w zasadach ryzyka wewnętrznego.

4. Na stronie **Ramy czasowe zasad** wybierz [ramy czasowe zasad](insider-risk-management-settings.md#policy-timeframes) , które mają wejść w życie dla użytkownika po wyzwoleniu dopasowania zasad ryzyka niejawnego.
5. Na stronie **Wykrywanie inteligentne** skonfiguruj następujące ustawienia dla zasad ryzyka niejawnych informacji poufnych:
    - [Wykluczenia typu pliku](insider-risk-management-settings.md#file-type-exclusions)
    - [Minimalna liczba zdarzeń dziennie w celu zwiększenia oceny nietypowej aktywności](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Poziom woluminu alertu](insider-risk-management-settings.md#alert-volume)
    - [stan alertu Ochrona punktu końcowego w usłudze Microsoft Defender](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Ustawienia domeny](insider-risk-management-settings.md#domains)
6. Na stronie **Eksportowanie alertów** włącz eksport informacji o alertach o ryzyku wewnętrznym przy użyciu interfejsów API zarządzania Office 365 w razie potrzeby.
7. Na stronie **Grupy użytkowników o priorytecie** utwórz grupę użytkowników o priorytecie i dodaj użytkowników, jeśli nie zostały utworzone w **kroku 3**.
8. Na stronie **Przepływy usługi Power Automate** skonfiguruj przepływ z szablonów przepływu ryzyka niejawnego lub utwórz nowy przepływ. Zapoznaj [się z artykułem Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#power-automate-flows-preview) , aby uzyskać szczegółowe wskazówki.
9. Na **stronie Zasoby priorytetowe** skonfiguruj zasoby priorytetowe tak, aby używały danych z fizycznej platformy kontroli i dostępu zaimportowanych przez łącznik fizycznego rozwiązywania problemów. Zapoznaj [się z artykułem Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#priority-physical-assets-preview) , aby uzyskać szczegółowe wskazówki.
10. Na stronie **Microsoft Teams** włącz integrację usługi Microsoft Teams z funkcją zarządzania ryzykiem wewnętrznym, aby automatycznie utworzyć zespół na potrzeby współpracy przypadków lub użytkowników. Zapoznaj [się z artykułem Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#microsoft-teams-preview) , aby uzyskać szczegółowe wskazówki.
11. Wybierz pozycję **Zapisz** , aby włączyć te ustawienia zasad ryzyka niejawne.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>Krok 6 (wymagany): Tworzenie zasad zarządzania ryzykiem wewnętrznym

Zasady zarządzania ryzykiem wewnętrznym obejmują przypisanych użytkowników i określają, które typy wskaźników ryzyka są skonfigurowane dla alertów. Zanim działania będą mogły wyzwalać alerty, należy skonfigurować zasady. Użyj kreatora zasad, aby utworzyć nowe zasady zarządzania ryzykiem wewnętrznym.

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Zasady**.
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

    - **Chcę określić witryny programu SharePoint, etykiety poufności, typy informacji poufnych i/lub rozszerzenia plików jako zawartość priorytetu**. Wybranie tej opcji spowoduje włączenie stron szczegółów w kreatorze w celu skonfigurowania tych kanałów.
    - **Nie chcę teraz określać priorytetowej zawartości (będzie można to zrobić po utworzeniu zasad).** Wybranie tej opcji spowoduje pominięcie stron szczegółów kanału w kreatorze.

10. Wybierz przycisk **Dalej**, aby kontynuować.

11. Jeśli wybrano **opcję Chcę określić witryny programu SharePoint, etykiety poufności, typy informacji poufnych i/lub rozszerzenia plików jako zawartość priorytetu** w poprzednim kroku, zobaczysz strony szczegółów *witryn programu SharePoint*, *typy informacji poufnych*, *etykiety poufności* i *rozszerzenia plików*. Te strony szczegółów umożliwiają definiowanie programu SharePoint, typów informacji poufnych, etykiet poufności i rozszerzeń plików w celu określenia priorytetów w zasadach.

    - **Witryny programu SharePoint**: wybierz pozycję **Dodaj witrynę programu SharePoint** i wybierz witryny programu SharePoint, do których masz dostęp, i chcesz określić priorytety. Na przykład *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Typ informacji poufnych**: wybierz pozycję **Dodaj typ informacji poufnych** i wybierz typy poufności, które chcesz nadać priorytet. Na przykład *"Numer konta bankowego w Stanach Zjednoczonych"* i *"Numer karty kredytowej"*.
    - **Etykiety poufności**: wybierz pozycję **Dodaj etykietę poufności** i wybierz etykiety, które chcesz nadać priorytet. Na przykład *"Poufne"* i *"Tajne"*.
    - Rozszerzenia plików: dodaj do 50 rozszerzeń plików. Możesz dołączyć lub pominąć "". z rozszerzeniem pliku. Na przykład plik *py* lub *py* określa priorytety plików języka Python.

    > [!NOTE]
    > Użytkownicy konfigurujący zasady i wybierający priorytetowe witryny share point mogą wybrać witryny programu SharePoint, do których mają uprawnienia dostępu. Jeśli witryny programu SharePoint nie są dostępne do wyboru w zasadach przez bieżącego użytkownika, inny użytkownik z wymaganymi uprawnieniami może wybrać witryny dla zasad później lub bieżący użytkownik powinien mieć dostęp do wymaganych witryn.

12. Wybierz przycisk **Dalej**, aby kontynuować.
13. Jeśli wybrano *szablony Ogólne przecieki danych* lub *Wycieki danych według priorytetowych użytkowników* , na stronie **Wyzwalacze** dla tych zasad zostaną wyświetlone opcje niestandardowych zdarzeń wyzwalających i wskaźników zasad. Możesz wybrać zasady DLP lub wskaźniki wyzwalania zdarzeń, które umożliwiają użytkownikom przypisanym do zasad w zakresie oceniania działań. Jeśli **wybierzesz opcję User matches a data loss prevention (DLP) policy triggering event (User matches a data loss prevention( DLP),** musisz wybrać zasady DLP z listy rozwijanej zasad DLP, aby włączyć wyzwalanie wskaźników dla zasad DLP dla tych zasad zarządzania ryzykiem wewnętrznym. Jeśli **wybierzesz opcję User performs an exfiltration activity triggering event (Użytkownik wykonuje działanie eksfiltracji wyzwalające zdarzenie** ), musisz wybrać co najmniej jeden z wymienionych wskaźników dla zdarzenia wyzwalającego zasady.

    > [!IMPORTANT]
    > Jeśli nie możesz wybrać wymienionego wskaźnika, jest to spowodowane tym, że nie są one włączone dla Twojej organizacji. Aby udostępnić je do wybrania i przypisania do zasad, włącz wskaźniki w **obszarze Wskaźniki zasad** **zarządzania** >  >  **ryzykiem wewnętrznym**.

    Jeśli wybrano inne szablony zasad, niestandardowe zdarzenia wyzwalania nie są obsługiwane. Mają zastosowanie wbudowane zdarzenia wyzwalające zasady i przejdziesz do kroku 23 bez definiowania atrybutów zasad.

14. Wybierz przycisk **Dalej**, aby kontynuować.
15. Jeśli wybrano *szablony Ogólne wycieki danych* lub *Wycieki danych według priorytetowych użytkowników* i wybrano, że **użytkownik wykonuje działanie eksfiltracji i skojarzone wskaźniki**, możesz wybrać progi niestandardowe lub domyślne dla wybranych zdarzeń wyzwalających wskaźnik. Wybierz pozycję **Użyj progów domyślnych (zalecane)** lub **Użyj progów niestandardowych dla wyzwalających zdarzeń**.
16. Wybierz przycisk **Dalej**, aby kontynuować.
17. Jeśli wybrano pozycję **Użyj niestandardowych progów dla zdarzeń wyzwalających**, dla każdego wskaźnika zdarzenia wyzwalającego wybranego w kroku 13 wybierz odpowiedni poziom, aby wygenerować żądany poziom alertów dotyczących działań. Można użyć zalecanych progów, progów niestandardowych lub progów opartych na nietypowych działaniach (dla niektórych wskaźników) powyżej dziennej normy dla użytkowników.
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

## <a name="next-steps"></a>Następne kroki

Po wykonaniu tych kroków w celu utworzenia pierwszych zasad zarządzania ryzykiem wewnętrznym zaczniesz otrzymywać alerty ze wskaźników aktywności po około 24 godzinach. Skonfiguruj dodatkowe zasady zgodnie z potrzebami, korzystając ze wskazówek opisanych w kroku 4 tego artykułu lub krokach opisanych w [temacie Tworzenie nowych zasad ryzyka dotyczącego informacji poufnych](insider-risk-management-policies.md#create-a-new-policy).

Aby dowiedzieć się więcej na temat badania alertów o ryzyku wewnętrznym i **pulpitu nawigacyjnego alertów**, zobacz [Działania związane z zarządzaniem ryzykiem wewnętrznym](insider-risk-management-activities.md#alert-dashboard).
