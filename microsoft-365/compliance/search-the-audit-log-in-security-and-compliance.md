---
title: Przeszukaj dziennik inspekcji w portal zgodności Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
description: Użyj portal zgodności Microsoft Purview, aby przeszukać ujednolicony dziennik inspekcji, aby wyświetlić aktywność użytkowników i administratorów w organizacji.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.openlocfilehash: 0e8ac4e3a8705960f307314717127c969a26c2f6
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078507"
---
# <a name="search-the-audit-log-in-the-compliance-portal"></a>Przeszukiwanie dziennika inspekcji w portalu zgodności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Czy chcesz sprawdzić, czy użytkownik wyświetlił określony dokument, czy oczyścił element ze swojej skrzynki pocztowej? Jeśli tak, możesz użyć narzędzia do wyszukiwania dzienników inspekcji w portal zgodności Microsoft Purview, aby przeszukać ujednolicony dziennik inspekcji, aby wyświetlić aktywność użytkowników i administratorów w organizacji. Tysiące operacji użytkowników i administratorów wykonywanych w dziesiątkach usług i rozwiązań Microsoft 365 są przechwytywane, rejestrowane i zachowywane w ujednoliconym dzienniku inspekcji organizacji. Użytkownicy w organizacji mogą używać narzędzia do wyszukiwania dzienników inspekcji, aby wyszukiwać, wyświetlać i eksportować (do pliku CSV) rekordy inspekcji dla tych operacji.

## <a name="microsoft-365-services-that-support-auditing"></a>usługi Microsoft 365 obsługujące inspekcję

Dlaczego ujednolicony dziennik inspekcji? Ponieważ można przeszukiwać dziennik inspekcji pod kątem działań wykonywanych w różnych usługach Microsoft 365. W poniższej tabeli wymieniono usługi i funkcje Microsoft 365 (w kolejności alfabetycznej), które są obsługiwane przez ujednolicony dziennik inspekcji.

| Microsoft 365 usługi lub funkcji | Typy rekordów|
|:---------|:---------|
| Azure Active Directory|AzureActiveDirectory, AzureActiveDirectoryAccountLogon, AzureActiveDirectoryStsLogon |
| Azure Information Protection|AipDiscover, AipSensitivityLabelAction, AipProtectionAction, AipFileDeleted, AipHeartBeat |
| Zgodność w komunikacji|ComplianceSuperVisionExchange|
| Eksplorator zawartości|LabelContentExplorer|
| Łączniki danych|ComplianceConnector|
| Ochrona przed utratą danych (DLP)|ComplianceDLPSharePoint, ComplianceDLPExchange, DLPEndpoint|
| Dynamics 365|CRM|
| Zbierania elektronicznych materiałów dowodowych|Odnajdywanie, AeD|
| Dokładne dopasowanie danych|MipExactDataMatch|
| Exchange Online|ExchangeAdmin, ExchangeItem, ExchangeItemAggregated |
| Formularzy|MicrosoftForms|
| Bariery informacyjne|InformationBarrierPolicyApplication|
| Microsoft 365 Defender|AirInvestigation, AirManualInvestigation, AirAdminActionInvestigation, MS365DCustomDetection|
| Microsoft Teams|MicrosoftTeams|
| MyAnalytics|MyAnalyticsSettings|
| OneDrive dla Firm|OneDrive|
| Power Apps|PowerAppsApp, PowerAppsPlan|
| Power Automate|MicrosoftFlow|
| Power BI|PowerBIAudit|
| Kwarantanna|Kwarantanna|
| Zasady przechowywania i etykiety przechowywania|MIPLabel, MipAutoLabelExchangeItem, MipAutoLabelSharePointItem, MipAutoLabelSharePointPolicyLocation|
| Typy informacji poufnych|DlpSensitiveInformationType|
| Etykiety wrażliwości|MIPLabel, SensitivityLabelAction, SensitivityLabeledFileAction, SensitivityLabelPolicyMatch|
| SharePoint Online|SharePoint, SharePointFileOperation,SharePointSharingOperation, SharePointListOperation, SharePointCommentOperation |
| Stream|MicrosoftStream|
| Analiza zagrożeń|ThreatIntelligence, ThreatIntelligenceUrl, ThreatFinder, ThreatIntelligenceAtpContent|
| Workplace Analytics|WorkplaceAnalytics|
| Yammer|Yammer|
| SystemSync| DataShareCreated, DataShareDeleted, GenerateCopyOfLakeData, DownloadCopyOfLakeData |

Aby uzyskać więcej informacji na temat operacji, które są poddawane inspekcji w każdej z usług wymienionych w poprzedniej tabeli, zobacz sekcję [Inspekcja działań](#audited-activities) w tym artykule.

W poprzedniej tabeli zidentyfikowano również wartość typu rekordu używaną do wyszukiwania w dzienniku inspekcji działań w odpowiedniej usłudze przy użyciu polecenia cmdlet **Search-UnifiedAuditLog** w programie Exchange Online programu PowerShell lub za pomocą skryptu programu PowerShell. Niektóre usługi mają wiele typów rekordów dla różnych typów działań w ramach tej samej usługi. Aby uzyskać bardziej kompletną listę typów rekordów inspekcji, zobacz [schemat interfejsu API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).

 Aby uzyskać więcej informacji na temat korzystania z programu PowerShell do przeszukiwania dziennika inspekcji, zobacz:

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)

- [Przeszukaj dziennik inspekcji za pomocą skryptu programu PowerShell](audit-log-search-script.md)

## <a name="before-you-search-the-audit-log"></a>Przed przeszukaniem dziennika inspekcji

Przed rozpoczęciem przeszukiwania dziennika inspekcji przeczytaj następujące elementy.

- Wyszukiwanie dzienników inspekcji jest domyślnie włączone dla organizacji Microsoft 365 i Office 365 przedsiębiorstw. Aby sprawdzić, czy wyszukiwanie dzienników inspekcji jest włączone, możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Wartość `True` właściwości *UnifiedAuditLogIngestionEnabled* wskazuje, że wyszukiwanie dziennika inspekcji jest włączone. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](turn-audit-log-search-on-or-off.md).

- Aby przeszukać dziennik inspekcji, musisz mieć przypisaną rolę dzienników inspekcji lub dzienników inspekcji View-Only w Exchange Online. Domyślnie te role są przypisywane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie **Uprawnienia** w centrum administracyjnym Exchange. Administratorzy globalni w Office 365 i Microsoft 365 są automatycznie dodawani jako członkowie grupy ról Zarządzanie organizacją w Exchange Online. Aby umożliwić użytkownikowi przeszukiwanie dziennika inspekcji z minimalnym poziomem uprawnień, możesz utworzyć niestandardową grupę ról w Exchange Online, dodać rolę View-Only Dzienniki inspekcji lub Dzienniki inspekcji, a następnie dodać użytkownika jako członka nowej grupy ról. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami ról w Exchange Online](/Exchange/permissions-exo/role-groups).

  > Jeśli przypiszesz użytkownikowi rolę dzienników inspekcji lub dzienników inspekcji View-Only na stronie **Uprawnienia** w portalu zgodności, nie będzie mógł przeszukiwać dziennika inspekcji. Musisz przypisać uprawnienia w Exchange Online. Dzieje się tak, ponieważ podstawowe polecenie cmdlet używane do przeszukiwania dziennika inspekcji jest Exchange Online poleceniem cmdlet.

- Gdy inspekcja działania jest wykonywana przez użytkownika lub administratora, rekord inspekcji jest generowany i przechowywany w dzienniku inspekcji organizacji. Czas, przez który rekord inspekcji jest przechowywany (i można go przeszukiwać w dzienniku inspekcji) zależy od twojej subskrypcji Office 365 lub Microsoft 365 Enterprise, a w szczególności od typu licencji przypisanej do określonych użytkowników.

  - W przypadku użytkowników, którzy mają przypisaną licencję Office 365 E5 lub Microsoft 365 E5 (lub użytkowników z licencją Zgodność platformy Microsoft 365 E5 lub Microsoft 365 E5 zbierania elektronicznych materiałów dowodowych i licencji dodatku Inspekcja), należy przeprowadzać inspekcję rekordów dla Działania Azure Active Directory, Exchange i SharePoint są domyślnie zachowywane przez jeden rok. Organizacje mogą również tworzyć zasady przechowywania dzienników inspekcji, aby zachować rekordy inspekcji dla działań w innych usługach przez okres do jednego roku. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasadami przechowywania dzienników inspekcji](audit-log-retention-policies.md).

    > [!NOTE]
    > Jeśli Twoja organizacja uczestniczyła w programie prywatnej wersji zapoznawczej na potrzeby rocznego przechowywania rekordów inspekcji, czas przechowywania rekordów inspekcji wygenerowanych przed ogólną datą wdrożenia dostępności nie zostanie zresetowany.

  - W przypadku użytkowników, do których przypisano dowolną inną licencję Office 365 lub Microsoft 365 E5, rekordy inspekcji są przechowywane przez 90 dni. Aby uzyskać listę subskrypcji Office 365 i Microsoft 365 obsługujących ujednolicone rejestrowanie inspekcji, zobacz [opis usługi portalu zabezpieczeń i zgodności](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

    > [!NOTE]
    > Nawet jeśli domyślnie włączono inspekcję skrzynek pocztowych, można zauważyć, że zdarzenia inspekcji skrzynki pocztowej dla niektórych użytkowników nie są odnalezione podczas przeszukiwania dzienników inspekcji w portalu zgodności lub za pośrednictwem interfejsu API działania zarządzania Office 365. Aby uzyskać więcej informacji, zobacz [Więcej informacji na temat rejestrowania inspekcji skrzynki pocztowej](enable-mailbox-auditing.md#more-information).

- Jeśli chcesz wyłączyć wyszukiwanie dzienników inspekcji w organizacji, możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Aby ponownie włączyć wyszukiwanie inspekcji, możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Aby uzyskać więcej informacji, zobacz [Wyłączanie wyszukiwania dzienników inspekcji](turn-audit-log-search-on-or-off.md).

- Jak wspomniano wcześniej, podstawowym poleceniem cmdlet używanym do przeszukiwania dziennika inspekcji jest polecenie cmdlet Exchange Online, czyli **Search-UnifiedAuditLog**. Oznacza to, że można użyć tego polecenia cmdlet do przeszukiwania dziennika inspekcji zamiast używania narzędzia wyszukiwania na stronie **Inspekcja** w portalu zgodności. To polecenie cmdlet należy uruchomić w programie Exchange Online programie PowerShell. Aby uzyskać więcej informacji, zobacz [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

  Aby uzyskać informacje na temat eksportowania wyników wyszukiwania zwróconych przez polecenie cmdlet **Search-UnifiedAuditLog** do pliku CSV, zobacz sekcję "Wskazówki eksportowania i wyświetlania dziennika inspekcji" w temacie [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Jeśli chcesz programowo pobierać dane z dziennika inspekcji, zalecamy użycie interfejsu API działania zarządzania Office 365 zamiast skryptu programu PowerShell. Interfejs API działania zarządzania Office 365 to usługa internetowa REST, która umożliwia opracowywanie rozwiązań do monitorowania operacji, zabezpieczeń i zgodności dla organizacji. Aby uzyskać więcej informacji, zobacz [dokumentację interfejsu API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

- Azure Active Directory (Azure AD) jest usługą katalogową dla Microsoft 365. Ujednolicony dziennik inspekcji zawiera działania użytkownika, grupy, aplikacji, domeny i katalogu wykonywane w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> lub w portalu zarządzania platformy Azure. Aby uzyskać pełną listę zdarzeń Azure AD, zobacz [Azure Active Directory Zdarzenia raportu inspekcji](/azure/active-directory/reports-monitoring/concept-audit-logs).

- Firma Microsoft nie gwarantuje określonego czasu po wystąpieniu zdarzenia, aby odpowiedni rekord inspekcji został zwrócony w wynikach wyszukiwania dziennika inspekcji. W przypadku usług podstawowych (takich jak Exchange, SharePoint, OneDrive i Teams) dostępność rekordów inspekcji zwykle wynosi od 60 do 90 minut po wystąpieniu zdarzenia. W przypadku innych usług dostępność rekordów inspekcji może być dłuższa. Jednak niektóre problemy, które są nieuniknione (takie jak awaria serwera) mogą wystąpić poza usługą inspekcji, która opóźnia dostępność rekordów inspekcji. Z tego powodu firma Microsoft nie zobowiązuje się do określonego czasu.

- Rejestrowanie inspekcji dla Power BI nie jest domyślnie włączone. Aby wyszukać działania Power BI w dzienniku inspekcji, musisz włączyć inspekcję w portalu administracyjnym Power BI. Aby uzyskać instrukcje, zobacz sekcję "Dzienniki inspekcji" w [portalu administracyjnym Power BI](/power-bi/service-admin-portal#audit-logs).

## <a name="search-the-audit-log"></a>Przeszukaj dziennik inspekcji

Oto proces przeszukiwania dziennika inspekcji w Microsoft 365.

[Krok 1. Uruchamianie wyszukiwania dziennika inspekcji](#step-1-run-an-audit-log-search)

[Krok 2. Wyświetlanie wyników wyszukiwania](#step-2-view-the-search-results)

[Krok 3. Eksportowanie wyników wyszukiwania do pliku](#step-3-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>Krok 1. Uruchamianie wyszukiwania dziennika inspekcji

1. Przejdź do i <https://compliance.microsoft.com> zaloguj się.

    > [!TIP]
    > Użyj prywatnej sesji przeglądania (nie zwykłej sesji), aby uzyskać dostęp do portalu zgodności, ponieważ uniemożliwi to użycie poświadczeń, za pomocą których aktualnie zalogowano się. Naciśnij **klawisze CTRL+SHIFT+N**, aby otworzyć sesję przeglądania InPrivate w Microsoft Edge lub sesję przeglądania prywatnego w przeglądarce Google Chrome (nazywaną oknem incognito).

2. W lewym okienku portalu zgodności kliknij pozycję **Inspekcja**.

    Zostanie wyświetlona strona **Inspekcja** .

    ![Skonfiguruj kryteria, a następnie kliknij pozycję Wyszukaj, aby uruchomić raport.](../media/AuditLogSearchPage1.png)

    > [!NOTE]
    > Jeśli zostanie wyświetlony link **Rozpocznij rejestrowanie użytkownika i działania administratora** , kliknij go, aby włączyć inspekcję. Jeśli nie widzisz tego linku, inspekcja jest włączona dla Twojej organizacji.

3. Na karcie **Wyszukiwanie** skonfiguruj następujące kryteria wyszukiwania:

   1. **Data rozpoczęcia** i **data zakończenia**: domyślnie wybrano ostatnie siedem dni. Wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie. Data i godzina są prezentowane w godzinach lokalnych. Maksymalny zakres dat, który można określić, wynosi 90 dni. Jeśli wybrany zakres dat jest większy niż 90 dni, zostanie wyświetlony błąd.

    > [!TIP]
    > Jeśli używasz maksymalnego zakresu dat wynoszącego 90 dni, wybierz bieżącą godzinę **dla daty rozpoczęcia**. W przeciwnym razie zostanie wyświetlony błąd informujący o tym, że data rozpoczęcia jest wcześniejsza niż data zakończenia. Jeśli inspekcja została włączona w ciągu ostatnich 90 dni, maksymalny zakres dat nie może rozpocząć się przed datą włączenia inspekcji.

   2. **Działania**: kliknij listę rozwijaną, aby wyświetlić działania, których można wyszukać. Działania użytkownika i administratora są zorganizowane w grupy powiązanych działań. Możesz wybrać określone działania lub kliknąć nazwę grupy działań, aby wybrać wszystkie działania w grupie. Możesz również kliknąć wybrane działanie, aby wyczyścić zaznaczenie. Po uruchomieniu wyszukiwania zostaną wyświetlone tylko wpisy dziennika inspekcji dla wybranych działań. Wybranie pozycji **Pokaż wyniki dla wszystkich działań** powoduje wyświetlenie wyników dla wszystkich działań wykonywanych przez wybranego użytkownika lub grupę użytkowników.<br/><br/>W dzienniku inspekcji jest zalogowanych ponad 100 działań użytkownika i administratora. Kliknij kartę **Inspekcja działań** w temacie tego artykułu, aby wyświetlić opisy każdego działania w każdej z różnych usług.

   3. **Użytkownicy**: kliknij to pole, a następnie wybierz co najmniej jednego użytkownika, aby wyświetlić wyniki wyszukiwania. Wpisy dziennika inspekcji dla wybranego działania wykonane przez użytkowników wybranych w tym polu są wyświetlane na liście wyników. Pozostaw to pole puste, aby zwrócić wpisy dla wszystkich użytkowników (i kont usług) w organizacji.

   4. **Plik, folder lub lokacja**: wpisz część lub wszystkie nazwy pliku lub folderu, aby wyszukać działanie związane z plikiem folderu zawierającym określone słowo kluczowe. Możesz również określić adres URL pliku lub folderu. Jeśli używasz adresu URL, upewnij się, że wpisz pełną ścieżkę adresu URL lub jeśli wpiszesz część adresu URL, nie dołącz żadnych znaków specjalnych ani spacji (jednak użycie symbolu wieloznacznego (\*) jest obsługiwane).<br/><br/>Pozostaw to pole puste, aby zwrócić wpisy dla wszystkich plików i folderów w organizacji.

    > [!TIP]
    >
    > - Jeśli szukasz wszystkich działań związanych z **witryną**, dodaj symbol wieloznaczny (\*) po adresie URL, aby zwrócić wszystkie wpisy dla tej witryny, `"https://contoso-my.sharepoint.com/personal*"`na przykład .
    >
    > - Jeśli szukasz wszystkich działań związanych z **plikiem**, dodaj symbol wieloznaczny (\*) przed nazwą pliku, aby zwrócić wszystkie wpisy dla tego pliku, `"*Customer_Profitability_Sample.csv"`na przykład .

4. Kliknij pozycję **Wyszukaj** , aby uruchomić wyszukiwanie przy użyciu kryteriów wyszukiwania.

   Wyniki wyszukiwania są ładowane i po kilku chwilach są wyświetlane na nowej stronie. Po zakończeniu wyszukiwania zostanie wyświetlona liczba znalezionych wyników. Maksymalnie 50 000 zdarzeń będzie wyświetlanych w przyrostach 150 zdarzeń. Jeśli więcej niż 50 000 zdarzeń spełnia kryteria wyszukiwania, zostanie wyświetlonych tylko 50 000 niesortowanych zdarzeń.

   ![Liczba wyników jest wyświetlana po zakończeniu wyszukiwania.](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>Wskazówki przeszukiwania dziennika inspekcji

- Możesz wybrać określone działania do wyszukania, klikając nazwę działania. Możesz też wyszukać wszystkie działania w grupie (takie jak **działania plików i folderów**), klikając nazwę grupy. Jeśli wybrano działanie, możesz je kliknąć, aby anulować wybór. Możesz również użyć pola wyszukiwania, aby wyświetlić działania zawierające wpisane słowo kluczowe.

  ![Kliknij nazwę grupy działań, aby wybrać wszystkie działania.](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Musisz wybrać pozycję **Pokaż wyniki dla wszystkich działań na** liście **Działania**, aby wyświetlić zdarzenia z dziennika inspekcji Exchange administratora. Zdarzenia z tego dziennika inspekcji wyświetlają nazwę polecenia cmdlet (na przykład **Set-Mailbox**) w kolumnie **Działanie** w wynikach. Aby uzyskać więcej informacji, kliknij kartę **Inspekcja działań** w tym temacie, a następnie kliknij pozycję **Exchange działania administratora**.

  Podobnie istnieją pewne działania inspekcji, które nie mają odpowiedniego elementu na liście **Działania** . Jeśli znasz nazwę operacji dla tych działań, możesz wyszukać wszystkie działania, a następnie filtrować operacje po wyeksportowaniu wyników wyszukiwania do pliku CSV.

- Kliknij przycisk **Wyczyść** , aby wyczyścić bieżące kryteria wyszukiwania. Zakres dat powraca do wartości domyślnej z ostatnich siedmiu dni. Możesz również kliknąć pozycję **Wyczyść wszystko, aby wyświetlić wyniki dla wszystkich działań** , aby anulować wszystkie wybrane działania.

- Jeśli zostanie znalezionych 50 000 wyników, prawdopodobnie można założyć, że istnieje ponad 50 000 zdarzeń spełniających kryteria wyszukiwania. Możesz uściślić kryteria wyszukiwania i ponownie uruchomić wyszukiwanie w celu zwrócenia mniejszej liczby wyników lub wyeksportować wszystkie wyniki wyszukiwania, wybierając pozycję **Eksportuj wyniki** \> **Pobierz wszystkie wyniki**.

### <a name="step-2-view-the-search-results"></a>Krok 2. Wyświetlanie wyników wyszukiwania

Wyniki wyszukiwania dziennika inspekcji są wyświetlane w obszarze **Wyniki** na stronie **wyszukiwania dziennika inspekcji** . Jak wspomniano wcześniej, maksymalnie 50 000 (najnowszych) zdarzeń jest wyświetlanych w przyrostach 150 zdarzeń. Użyj paska przewijania lub naciśnij **klawisze Shift + End** , aby wyświetlić następne 150 zdarzeń.

Wyniki zawierają następujące informacje o każdym zdarzeniu zwracanym przez wyszukiwanie:

- **Data**: data i godzina (w czasie lokalnym) wystąpienia zdarzenia.

- **Adres IP**: adres IP urządzenia, które było używane podczas rejestrowania działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.

   > [!NOTE]
  > W przypadku niektórych usług wartością wyświetlaną w tym polu może być adres IP zaufanej aplikacji (na przykład Office w sieci Web aplikacji) wywołujący do usługi w imieniu użytkownika, a nie adres IP urządzenia używanego przez osobę, która wykonała działanie. Ponadto w przypadku działań administratora (lub działań wykonywanych przez konto systemowe) dla zdarzeń związanych z Azure Active Directory adres IP nie jest rejestrowany, a wartość wyświetlana w tym polu to `null`.

- **Użytkownik**: użytkownik (lub konto usługi), który wykonał akcję, która wyzwoliła zdarzenie.

- **Działanie**: działanie wykonywane przez użytkownika. Ta wartość odpowiada działaniom wybranym na liście rozwijanej **Działania** . W przypadku zdarzenia z dziennika inspekcji administratora Exchange wartość w tej kolumnie jest Exchange polecenia cmdlet.

- **Element**: obiekt, który został utworzony lub zmodyfikowany w wyniku odpowiedniego działania. Na przykład plik, który został wyświetlony lub zmodyfikowany, lub zaktualizowane konto użytkownika. Nie wszystkie działania mają wartość w tej kolumnie.

- **Szczegóły**: dodatkowe informacje o działaniu. Ponownie nie wszystkie działania mają wartość.

> [!TIP]
> Kliknij nagłówek kolumny w obszarze **Wyniki** , aby posortować wyniki. Wyniki można sortować od A do Z lub Z do A. Kliknij nagłówek **Data** , aby posortować wyniki od najstarszych do najnowszych lub od najnowszych do najstarszych.

#### <a name="view-the-details-for-a-specific-event"></a>Wyświetlanie szczegółów określonego zdarzenia

Aby wyświetlić więcej szczegółów dotyczących zdarzenia, kliknij rekord zdarzenia na liście wyników wyszukiwania. Zostanie wyświetlona strona wysuwana zawierająca szczegółowe właściwości rekordu zdarzenia. Wyświetlane właściwości zależą od usługi, w której występuje zdarzenie. 

### <a name="step-3-export-the-search-results-to-a-file"></a>Krok 3. Eksportowanie wyników wyszukiwania do pliku

Wyniki wyszukiwania dziennika inspekcji można wyeksportować do pliku wartości rozdzielanej przecinkami (CSV) na komputerze lokalnym. Możesz otworzyć ten plik w Microsoft Excel i użyć funkcji, takich jak wyszukiwanie, sortowanie, filtrowanie i dzielenie pojedynczej kolumny (zawierającej wiele właściwości) na wiele kolumn.

1. Uruchom wyszukiwanie w dzienniku inspekcji, a następnie popraw kryteria wyszukiwania do momentu uzyskania żądanych wyników.

2. Na stronie wyników wyszukiwania kliknij pozycję **Eksportuj** > **Pobierz wszystkie wyniki**.

   Wszystkie wpisy z dziennika inspekcji spełniające kryteria wyszukiwania są eksportowane do pliku CSV. Nieprzetworzone dane z dziennika inspekcji są zapisywane w pliku CSV. Dodatkowe informacje z wpisu dziennika inspekcji są zawarte w kolumnie o nazwie **AuditData** w pliku CSV.

     > [!IMPORTANT]
     > Możesz pobrać maksymalnie 50 000 wpisów do pliku CSV z pojedynczego przeszukiwania dziennika inspekcji. Jeśli do pliku CSV zostanie pobranych 50 000 wpisów, można założyć, że istnieje ponad 50 000 zdarzeń spełniających kryteria wyszukiwania. Aby wyeksportować więcej niż ten limit, spróbuj użyć zakresu dat, aby zmniejszyć liczbę wpisów dziennika inspekcji. Może być konieczne uruchomienie wielu wyszukiwań z mniejszymi zakresami dat, aby wyeksportować ponad 50 000 wpisów.

3. Po zakończeniu procesu eksportowania w górnej części okna zostanie wyświetlony komunikat z monitem o otwarcie pliku CSV i zapisanie go na komputerze lokalnym. Możesz również uzyskać dostęp do pliku CSV w folderze Pliki do pobrania.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Więcej informacji na temat eksportowania i wyświetlania wyników wyszukiwania dzienników inspekcji

- Po pobraniu wszystkich wyników wyszukiwania plik CSV zawiera kolumny **CreationDate**, **UserIds**, **Operations** i **AuditData**. **Kolumna AuditData** zawiera dodatkowe informacje o każdym zdarzeniu (podobnie jak szczegółowe informacje wyświetlane na stronie wysuwanej podczas wyświetlania wyników wyszukiwania w portalu zgodności). Dane w tej kolumnie składają się z obiektu JSON, który zawiera wiele właściwości z rekordu dziennika inspekcji. Każda para *właściwości:value* w obiekcie JSON jest oddzielona przecinkami. Narzędzie przekształcania JSON w Edytor Power Query w Excel umożliwia podzielenie kolumny **AuditData** na wiele kolumn, dzięki czemu każda właściwość obiektu JSON ma własną kolumnę. Umożliwia to sortowanie i filtrowanie co najmniej jednej z tych właściwości. Aby uzyskać instrukcje krok po kroku dotyczące przekształcania obiektu JSON przy użyciu Edytor Power Query, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

  Po podzieleniu kolumny **AuditData** można filtrować kolumnę **Operacje** , aby wyświetlić szczegółowe właściwości określonego typu działania.

- Po pobraniu wszystkich wyników z zapytania wyszukiwania zawierającego zdarzenia z różnych usług **kolumna AuditData** w pliku CSV zawiera różne właściwości w zależności od usługi, w której wykonano akcję. Na przykład wpisy z dzienników inspekcji Exchange i Azure AD obejmują właściwość o nazwie **ResultStatus**, która wskazuje, czy akcja zakończyła się pomyślnie, czy nie. Ta właściwość nie jest uwzględniana w przypadku zdarzeń w SharePoint. Podobnie SharePoint zdarzenia mają właściwość identyfikującą adres URL witryny dla działań związanych z plikami i folderami. Aby wyeliminować to zachowanie, rozważ użycie różnych wyszukiwań w celu wyeksportowania wyników działań z jednej usługi.

  Aby zapoznać się z opisem wielu właściwości wymienionych w kolumnie **AuditData** w pliku CSV podczas pobierania wszystkich wyników, a każda z nich ma zastosowanie, zobacz [Szczegółowe właściwości w dzienniku inspekcji](detailed-properties-in-the-office-365-audit-log.md).

## <a name="audited-activities"></a>Działania poddane inspekcji

W tabelach w tej sekcji opisano działania, które są poddawane inspekcji w Microsoft 365. Te zdarzenia można wyszukać, wyszukując dziennik inspekcji w portalu zabezpieczeń i zgodności.

Te tabele grupują powiązane działania lub działania z określonej usługi. Tabele zawierają przyjazną nazwę wyświetlaną na liście rozwijanej **Działania** oraz nazwę odpowiedniej operacji, która jest wyświetlana w szczegółowych informacjach rekordu inspekcji i w pliku CSV podczas eksportowania wyników wyszukiwania. Aby uzyskać opisy szczegółowych informacji, zobacz [Szczegółowe właściwości w dzienniku inspekcji](detailed-properties-in-the-office-365-audit-log.md).

Kliknij jeden z poniższych linków, aby przejść do określonej tabeli.

:::row:::
    :::column:::
        [Działania dotyczące plików i stron](#file-and-page-activities)
    :::column-end:::
    :::column:::
        [Działania folderów](#folder-activities)
    :::column-end:::
    :::column:::
        [działania listy SharePoint](#sharepoint-list-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania dotyczące udostępniania i uzyskiwania dostępu do żądań](#sharing-and-access-request-activities)
    :::column-end:::
    :::column:::
        [Działania synchronizacji](#synchronization-activities)
    :::column-end:::
    :::column:::
        [Działania dotyczące uprawnień witryny](#site-permissions-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania administracji lokacji](#site-administration-activities)
    :::column-end:::
    :::column:::
        [działania Exchange skrzynki pocztowej](#exchange-mailbox-activities)
    :::column-end:::
    :::column:::
        [Działania administracyjne użytkowników](#user-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Azure AD działań administracyjnych grupy](#azure-ad-group-administration-activities)
    :::column-end:::
    :::column:::
        [Działania administracji aplikacjami](#application-administration-activities)
    :::column-end:::
    :::column:::
        [Działania administrowania rolami](#role-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania administracji katalogowej](#directory-administration-activities)
    :::column-end:::
    :::column:::
        [Działania zbierania elektronicznych materiałów dowodowych](#ediscovery-activities)
    :::column-end:::
    :::column:::
        [Działania zbierania elektronicznych materiałów dowodowych (Premium)](#ediscovery-premium-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [działania Power BI](#power-bi-activities)
    :::column-end:::
    :::column:::
        [Microsoft Workplace Analytics](#workplace-analytics-activities)
    :::column-end:::
    :::column:::
        [działania Microsoft Teams](#microsoft-teams-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Microsoft Teams działania w zakresie opieki zdrowotnej](#microsoft-teams-healthcare-activities)
    :::column-end:::
    :::column:::
        [działania Microsoft Teams Shifts](#microsoft-teams-shifts-activities)
    :::column-end:::
    :::column:::
        [działania Yammer](#yammer-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania firmy Microsoft Power Automate](#microsoft-power-automate-activities)
    :::column-end:::
    :::column:::
        [Działania firmy Microsoft Power Apps](#microsoft-power-apps-activities)
    :::column-end:::
    :::column:::
        [działania Microsoft Stream](#microsoft-stream-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania Eksploratora zawartości](#content-explorer-activities)
    :::column-end:::
    :::column:::
        [Działania kwarantanny](#quarantine-activities)
    :::column-end:::
    :::column:::
        [działania Microsoft Forms](#microsoft-forms-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania związane z etykietami poufności](#sensitivity-label-activities)
    :::column-end:::
    :::column:::
        [Działania dotyczące zasad przechowywania i etykiet przechowywania](#retention-policy-and-retention-label-activities)
    :::column-end:::
    :::column:::
        [Działania dotyczące wiadomości e-mail z briefingu](#briefing-email-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania myAnalytics](#myanalytics-activities)
    :::column-end:::
    :::column:::
        [Działania związane z barierami informacyjnymi](#information-barriers-activities)
    :::column-end:::
    :::column:::
        [Działania przeglądu dyspozycji](#disposition-review-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania dotyczące zgodności komunikacji](#communication-compliance-activities)
    :::column-end:::
    :::column:::
        [Działania raportu](#report-activities)
    :::column-end:::
    :::column:::
        [działania administratora Exchange](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Działania zaszyfrowanego portalu wiadomości](#encrypted-message-portal-activities)
    :::column-end:::
    :::column:::
        [Działania narzędzia SystemSync] (działania #systemsync)
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Działania dotyczące plików i stron

W poniższej tabeli opisano działania dotyczące plików i stron w usłudze SharePoint Online i OneDrive dla Firm.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dostęp do pliku|FileAccessed|Użytkownik lub konto systemowe uzyskuje dostęp do pliku. Gdy użytkownik uzyskuje dostęp do pliku, zdarzenie FileAccessed nie jest ponownie rejestrowane dla tego samego użytkownika dla tego samego pliku przez następne pięć minut.|
|(brak)|FileAccessedExtended|Jest to związane z działaniem "Dostęp do pliku" (FileAccessed). Zdarzenie FileAccessedExtended jest rejestrowane, gdy ta sama osoba stale uzyskuje dostęp do pliku przez dłuższy czas (do 3 godzin). <br/><br/> Celem rejestrowania zdarzeń FileAccessedExtended jest zmniejszenie liczby zdarzeń FileAccessed, które są rejestrowane podczas ciągłego uzyskiwania dostępu do pliku. Pomaga to zmniejszyć szum wielu rekordów FileAccessed dla tego, co jest zasadniczo tym samym działaniem użytkownika, i pozwala skupić się na początkowym (i ważniejszym) zdarzeniu FileAccessed.|
|Zmieniono etykietę przechowywania pliku|ComplianceSettingChanged|Etykieta przechowywania została zastosowana do dokumentu lub usunięta z dokumentu. To zdarzenie jest wyzwalane, gdy etykieta przechowywania jest ręcznie lub automatycznie stosowana do komunikatu.|
|Zmieniono stan rekordu na zablokowany|LockRecord|Stan rekordu etykiety przechowywania, która klasyfikuje dokument jako rekord, został zablokowany. Oznacza to, że nie można modyfikować ani usuwać dokumentu. Tylko użytkownicy przypisani co najmniej uprawnienie współautora witryny mogą zmienić stan rekordu dokumentu.|
|Zmieniono stan rekordu na odblokowany|UnlockRecord|Stan rekordu etykiety przechowywania, która klasyfikuje dokument jako rekord został odblokowany. Oznacza to, że dokument można modyfikować lub usuwać. Tylko użytkownicy przypisani co najmniej uprawnienie współautora witryny mogą zmienić stan rekordu dokumentu.|
|Zaewidencjonowany plik|FileCheckedIn|Użytkownik zaewidencjonuje dokument wyewidencjonowany z biblioteki dokumentów.|
|Wyewidencjonowany plik|FileCheckedOut|Użytkownik wyewidencjonuje dokument znajdujący się w bibliotece dokumentów. Użytkownicy mogą wyewidencjonować i wprowadzić zmiany w dokumentach, które zostały im udostępnione.|
|Skopiowany plik|Plik skopiowany|Użytkownik kopiuje dokument z witryny. Skopiowany plik można zapisać w innym folderze w witrynie.|
|Usunięty plik|FileDeleted|Użytkownik usuwa dokument z witryny.|
|Usunięty plik z kosza|FileDeletedFirstStageRecycleBin|Użytkownik usuwa plik z kosza witryny.|
|Usunięty plik z kosza drugiego etapu|FileDeletedSecondStageRecycleBin|Użytkownik usuwa plik z kosza drugiego etapu lokacji.|
|Usunięty plik oznaczony jako rekord|RecordDelete|Usunięto dokument lub wiadomość e-mail oznaczoną jako rekord. Element jest uważany za rekord, gdy etykieta przechowywania, która oznacza elementy jako rekord, jest stosowana do zawartości.|
|Wykryta niezgodność poufności dokumentu|DocumentSensitivityMismatchDetected|Użytkownik przekazuje dokument do witryny chronionej etykietą poufności, a dokument ma etykietę poufności o wyższym priorytecie niż etykieta poufności zastosowana do witryny. Na przykład dokument z etykietą Poufne jest przekazywany do witryny z etykietą Ogólne. <br/><br/> To zdarzenie nie jest wyzwalane, jeśli dokument ma etykietę poufności o niższym priorytecie niż etykieta poufności zastosowana do witryny. Na przykład dokument z etykietą Ogólne jest przekazywany do witryny z etykietą Poufne. Aby uzyskać więcej informacji na temat priorytetu etykiet poufności, zobacz [Priorytet etykiety (kolejność ma znaczenie)](sensitivity-labels.md#label-priority-order-matters).|
|Wykryto złośliwe oprogramowanie w pliku|FileMalwareDetected|SharePoint aparat antywirusowy wykrywa złośliwe oprogramowanie w pliku.|
|Odrzucone wyewidencjonowania pliku|FileCheckOutDiscarded|Użytkownik odrzuca (lub cofa) wyewidencjonowany plik. Oznacza to, że wszelkie zmiany wprowadzone w pliku podczas wyewidencjonowania są odrzucane i nie są zapisywane w wersji dokumentu w bibliotece dokumentów.|
|Pobrany plik|FileDownloaded|Użytkownik pobiera dokument z witryny.|
|Zmodyfikowany plik|FileModified|Konto użytkownika lub konta systemowego modyfikuje zawartość lub właściwości dokumentu w witrynie. System czeka pięć minut, zanim zarejestruje inne zdarzenie FileModified, gdy ten sam użytkownik modyfikuje zawartość lub właściwości tego samego dokumentu.|
|(brak)|FileModifiedExtended|Jest to związane z działaniem "Zmodyfikowany plik" (FileModified). Zdarzenie FileModifiedExtended jest rejestrowane, gdy ta sama osoba stale modyfikuje plik przez dłuższy czas (do 3 godzin). <br/><br/> Celem rejestrowania zdarzeń FileModifiedExtended jest zmniejszenie liczby zdarzeń FileModified, które są rejestrowane, gdy plik jest stale modyfikowany. Pomaga to zmniejszyć szum wielu rekordów FileModified dla tego, co jest zasadniczo tym samym działaniem użytkownika, i pozwala skupić się na początkowym (i ważniejszym) zdarzeniu FileModified.|
|Przeniesiony plik|Plikprzesuwany|Użytkownik przenosi dokument z bieżącej lokalizacji w lokacji do nowej lokalizacji.|
|(brak)|PlikPrzegląd|Użytkownik wyświetla podgląd plików w witrynie SharePoint lub OneDrive dla Firm. Te zdarzenia zwykle występują w dużych ilościach na podstawie jednego działania, takiego jak wyświetlanie galerii obrazów.|
|Wykonane zapytanie wyszukiwania|SearchQueryPerformed|Konto użytkownika lub systemu wykonuje wyszukiwanie w SharePoint lub OneDrive dla Firm. Niektóre typowe scenariusze, w których konto usługi wykonuje zapytanie wyszukiwania, obejmują stosowanie zasad przechowywania zbierania elektronicznych materiałów dowodowych i przechowywania do witryn i kont OneDrive oraz automatyczne stosowanie etykiet przechowywania lub poufności do zawartości witryny.|
|Odtwarzanie pliku | FileRecycled | Użytkownik przenosi plik do kosza SharePoint. |
|Odtwarzanie folderu | FolderRecycled | Użytkownik przenosi folder do kosza SharePoint. |
|Odtworzono wszystkie wersje pomocnicze pliku|FileVersionsAllMinorsRecycled|Użytkownik usuwa wszystkie wersje pomocnicze z historii wersji pliku. Usunięte wersje są przenoszone do kosza witryny.|
|Odtworzono wszystkie wersje pliku|FileVersionsAllRecycled|Użytkownik usuwa wszystkie wersje z historii wersji pliku. Usunięte wersje są przenoszone do kosza witryny.|
|Odtworzona wersja pliku|FileVersionRecycled|Użytkownik usuwa wersję z historii wersji pliku. Usunięta wersja zostanie przeniesiona do kosza witryny.|
|Zmieniono nazwę pliku|FileRenamed|Użytkownik zmienia nazwę dokumentu.|
|Przywrócony plik|FileRestored|Użytkownik przywraca dokument z kosza witryny.|
|Przekazany plik|FileUploaded|Użytkownik przekazuje dokument do folderu w witrynie.|
|Wyświetlona strona|PageViewed|Użytkownik wyświetla stronę w witrynie. Nie obejmuje to używania przeglądarki sieci Web do wyświetlania plików znajdujących się w bibliotece dokumentów. Gdy użytkownik wyświetli stronę, zdarzenie PageViewed nie zostanie ponownie zarejestrowane dla tego samego użytkownika dla tej samej strony przez następne pięć minut.|
|(brak)|PageViewedExtended|Jest to związane z działaniem "Wyświetlona strona" (PageViewed). Zdarzenie PageViewedExtended jest rejestrowane, gdy ta sama osoba stale wyświetla stronę internetową przez dłuższy czas (do 3 godzin). <br/><br/> Celem rejestrowania zdarzeń PageViewedExtended jest zmniejszenie liczby zdarzeń PageViewed, które są rejestrowane, gdy strona jest stale wyświetlana. Pomaga to zmniejszyć szum wielu rekordów PageViewed dla tego, co jest zasadniczo tym samym działaniem użytkownika, i pozwala skupić się na początkowym (i ważniejszym) zdarzeniu PageViewed.|
|Widok sygnalizowany przez klienta|ClientViewSignaled|Klient użytkownika (taki jak witryna internetowa lub aplikacja mobilna) zasygnalizował, że wskazana strona została wyświetlona przez użytkownika. To działanie jest często rejestrowane po zdarzeniu PagePrefetched dla strony. <br/><br/>**UWAGA**: Ponieważ zdarzenia ClientViewSignaled są sygnalizowane przez klienta, a nie przez serwer, możliwe, że zdarzenie nie zostanie zarejestrowane przez serwer i w związku z tym może nie pojawić się w dzienniku inspekcji. Istnieje również możliwość, że informacje w rekordzie inspekcji mogą nie być wiarygodne. Jednak ponieważ tożsamość użytkownika jest weryfikowana przez token użyty do utworzenia sygnału, tożsamość użytkownika wymieniona w odpowiednim rekordzie inspekcji jest dokładna. System czeka pięć minut, zanim zarejestruje to samo zdarzenie, gdy klient tego samego użytkownika sygnalizuje, że strona została ponownie wyświetlona przez użytkownika.|
|(brak)|PagePrefetched|Klient użytkownika (taki jak witryna internetowa lub aplikacja mobilna) zażądał wskazanej strony, aby zwiększyć wydajność, jeśli użytkownik przegląda tę stronę. To zdarzenie jest rejestrowane, aby wskazać, że zawartość strony została udostępniona klientowi użytkownika. To zdarzenie nie jest ostatecznym wskazaniem, że użytkownik przeszedł do strony. <br/><br/> Gdy zawartość strony jest renderowana przez klienta (zgodnie z żądaniem użytkownika), powinno zostać wygenerowane zdarzenie ClientViewSignaled. Nie wszyscy klienci obsługują elementy wskazujące wstępne pobieranie, dlatego niektóre wstępnie pobrane działania mogą zostać zarejestrowane jako zdarzenia PageViewed.|

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>Często zadawane pytania dotyczące zdarzeń FileAccessed i FilePreviewed

**Czy jakiekolwiek działania inne niż użytkownika mogą wyzwalać rekordy inspekcji FilePreviewed zawierające agenta użytkownika, takiego jak "OneDriveMpc-Transform_Thumbnail"?**

Nie znamy scenariuszy, w których akcje inne niż użytkownika generują zdarzenia takie jak te. Akcje użytkownika, takie jak otwieranie karty profilu użytkownika (przez kliknięcie nazwy lub adresu e-mail w wiadomości w Outlook w sieci Web) wygenerują podobne zdarzenia.

**Czy wywołania OneDriveMpc-Transform_Thumbnail są zawsze celowo wyzwalane przez użytkownika?**

Nie. Jednak podobne zdarzenia można rejestrować w wyniku wstępnego pobrania przeglądarki.

**Jeśli zobaczymy zdarzenie FilePreviewed pochodzące z adresu IP zarejestrowanego przez firmę Microsoft, czy oznacza to, że podgląd został wyświetlony na ekranie urządzenia użytkownika?**

Nie. Zdarzenie mogło zostać zarejestrowane w wyniku wstępnego pobrania przeglądarki.

**Czy istnieją scenariusze, w których użytkownik wyświetlający podgląd dokumentu generuje zdarzenia FileAccessed?**

Zdarzenia FilePreviewed i FileAccessed wskazują, że wywołanie użytkownika doprowadziło do odczytu pliku (lub odczytu renderowania miniatury pliku). Chociaż te zdarzenia mają być zgodne z intencją podglądu i dostępu, rozróżnienie zdarzeń nie jest gwarancją intencji użytkownika.

#### <a name="the-appsharepoint-user-in-audit-records"></a>Użytkownik programu SharePoint aplikacji\@w rekordach inspekcji

W rekordach inspekcji niektórych działań dotyczących plików (i innych działań związanych z SharePoint) można zauważyć, że użytkownik, który wykonał działanie (zidentyfikowane w polach Użytkownik i UserId) jest app@sharepoint. Oznacza to, że "użytkownik", który wykonał działanie, był aplikacją. W takim przypadku aplikacji udzielono uprawnień w SharePoint do wykonywania akcji w całej organizacji (takich jak przeszukiwanie witryny SharePoint lub konta OneDrive) w imieniu użytkownika, administratora lub usługi. Ten proces udzielania uprawnień aplikacji jest nazywany *SharePoint dostępu tylko do aplikacji*. Oznacza to, że uwierzytelnianie przedstawione SharePoint w celu wykonania akcji zostało wykonane przez aplikację, a nie przez użytkownika. Dlatego app@sharepoint użytkownik jest identyfikowany w niektórych rekordach inspekcji. Aby uzyskać więcej informacji, zobacz [Udzielanie dostępu przy użyciu SharePoint App-Only](/sharepoint/dev/solution-guidance/security-apponly-azureacs).

Na przykład app@sharepoint jest często identyfikowany jako użytkownik zdarzeń "Wykonywane zapytanie wyszukiwania" i "Dostęp do pliku". Dzieje się tak dlatego, że aplikacja z dostępem SharePoint App-Only w organizacji wykonuje zapytania wyszukiwania i uzyskuje dostęp do plików podczas stosowania zasad przechowywania do witryn i kont OneDrive.

Poniżej przedstawiono kilka innych scenariuszy, w których app@sharepoint można zidentyfikować w rekordzie inspekcji jako użytkownik, który wykonał działanie:

- Grupy Microsoft 365. Gdy użytkownik lub administrator tworzy nową grupę, są generowane rekordy inspekcji na potrzeby tworzenia zbioru witryn, aktualizowania list i dodawania członków do grupy SharePoint. Te zadania są wykonywane w imieniu użytkownika, który utworzył grupę.

- Microsoft Teams. Podobnie jak Grupy Microsoft 365, rekordy inspekcji są generowane na potrzeby tworzenia zbioru witryn, aktualizowania list i dodawania członków do grupy SharePoint podczas tworzenia zespołu.

- Funkcje zgodności. Gdy administrator implementuje funkcje zgodności, takie jak zasady przechowywania, blokady zbierania elektronicznych materiałów dowodowych i automatyczne stosowanie etykiet poufności.

W tych i innych scenariuszach zauważysz również, że wiele rekordów inspekcji z app@sharepoint, ponieważ określony użytkownik został utworzony w krótkim czasie, często w ciągu kilku sekund od siebie. Oznacza to również, że prawdopodobnie zostały one wyzwolone przez to samo zadanie zainicjowane przez użytkownika. Ponadto pola ApplicationDisplayName i EventData w rekordzie inspekcji mogą pomóc w zidentyfikowaniu scenariusza lub aplikacji, która wyzwoliła zdarzenie.

### <a name="folder-activities"></a>Działania folderów

W poniższej tabeli opisano działania folderów w usłudze SharePoint Online i OneDrive dla Firm. Jak wyjaśniono wcześniej, rekordy inspekcji dla niektórych działań SharePoint wskazują, app@sharepoint użytkownik wykonał działanie w imieniu użytkownika lub administratora, który zainicjował akcję. Aby uzyskać więcej informacji, zobacz [Temat Użytkownik programu SharePoint aplikacji\@w rekordach inspekcji](#the-appsharepoint-user-in-audit-records).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Skopiowany folder|Folder skopiowany|Użytkownik kopiuje folder z witryny do innej lokalizacji w SharePoint lub OneDrive dla Firm.|
|Utworzony folder|FolderUtwórz|Użytkownik tworzy folder w witrynie.|
|Usunięty folder|FolderDeleted|Użytkownik usuwa folder z witryny.|
|Usunięty folder z kosza|FolderDeletedFirstStageRecycleBin|Użytkownik usuwa folder z kosza w witrynie.|
|Usunięty folder z kosza drugiego etapu|FolderDeletedSecondStageRecycleBin|Użytkownik usuwa folder z kosza drugiego etapu w lokacji.|
|Folder zmodyfikowany|FolderModyfikowany|Użytkownik modyfikuje folder w witrynie. Obejmuje to zmianę metadanych folderu, takich jak zmiana tagów i właściwości.|
|Folder przeniesiony|FolderMoved|Użytkownik przenosi folder do innej lokalizacji w witrynie.|
|Zmieniono nazwę folderu|FolderRenamed|Użytkownik zmienia nazwę folderu w witrynie.|
|Przywrócony folder|FolderRestored|Użytkownik przywraca usunięty folder z kosza w witrynie.|

### <a name="sharepoint-list-activities"></a>działania listy SharePoint

W poniższej tabeli opisano działania związane z interakcją użytkowników z listami i elementami listy w usłudze SharePoint Online. Jak wyjaśniono wcześniej, rekordy inspekcji dla niektórych działań SharePoint wskazują, app@sharepoint użytkownik wykonał działanie w imieniu użytkownika lub administratora, który zainicjował akcję. Aby uzyskać więcej informacji, zobacz [Temat Użytkownik programu SharePoint aplikacji\@w rekordach inspekcji](#the-appsharepoint-user-in-audit-records).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Utworzona lista|ListCreated|Użytkownik utworzył listę SharePoint.|
|Utworzona kolumna listy|ListColumnCreated|Użytkownik utworzył kolumnę listy SharePoint. Kolumna listy to kolumna dołączona do co najmniej jednej listy SharePoint.|
|Utworzony typ zawartości listy|ListContentTypeCreated|Użytkownik utworzył typ zawartości listy. Typ zawartości listy to typ zawartości dołączony do co najmniej jednej listy SharePoint.|
|Utworzony element listy|ListItemCreated|Użytkownik utworzył element na istniejącej liście SharePoint.|
|Utworzona kolumna witryny|SiteColumnCreated|Użytkownik utworzył kolumnę witryny SharePoint. Kolumna witryny to kolumna, która nie jest dołączona do listy. Kolumna witryny to również struktura metadanych, która może być używana przez dowolną listę w danej sieci Web.|
|Typ zawartości utworzonej witryny|Utworzony typ zawartości witryny|Użytkownik utworzył typ zawartości witryny. Typ zawartości witryny to typ zawartości dołączony do witryny nadrzędnej.|
|Usunięta lista|ListDeleted|Użytkownik usunął listę SharePoint.|
|Usunięta kolumna listy|Usunięto kolumnę listy|Użytkownik usunął kolumnę listy SharePoint.|
|Usunięty typ zawartości listy|ListContentTypeDeleted|Użytkownik usunął typ zawartości listy.|
|Usunięty element listy|Usunięto element listy|Użytkownik usunął element listy SharePoint.|
|Usunięta kolumna witryny|SiteColumnDeleted|Użytkownik usunął kolumnę witryny SharePoint.|
|Typ zawartości usuniętej witryny|SiteContentTypeDeleted|Użytkownik usunął typ zawartości witryny.|
|Element listy z recyklingu|ListItemRecycled|Użytkownik przeniósł element listy SharePoint do Kosza.|
|Przywrócona lista|ListRestored|Użytkownik przywrócił listę SharePoint z Kosza.|
|Przywrócony element listy|ListItemRestored|Użytkownik przywrócił element listy SharePoint z Kosza.|
|Zaktualizowana lista|ListUpdated|Użytkownik zaktualizował listę SharePoint, modyfikując co najmniej jedną właściwość.|
|Zaktualizowana kolumna listy|ListColumnUpdated|Użytkownik zaktualizował kolumnę listy SharePoint, modyfikując co najmniej jedną właściwość.|
|Zaktualizowany typ zawartości listy|ListContentTypeUpdated|Użytkownik zaktualizował typ zawartości listy, modyfikując co najmniej jedną właściwość.|
|Zaktualizowany element listy|ListItemUpdated|Użytkownik zaktualizował element listy SharePoint, modyfikując co najmniej jedną właściwość.|
|Zaktualizowana kolumna witryny|SiteColumnUpdated|Użytkownik zaktualizował kolumnę witryny SharePoint, modyfikując co najmniej jedną właściwość.|
|Zaktualizowany typ zawartości witryny|SiteContentTypeUpdated|Użytkownik zaktualizował typ zawartości witryny, modyfikując co najmniej jedną właściwość.|

### <a name="sharing-and-access-request-activities"></a>Działania dotyczące udostępniania i uzyskiwania dostępu do żądań

W poniższej tabeli opisano działania związane z udostępnianiem i uzyskiwaniem dostępu użytkowników w usłudze SharePoint Online i OneDrive dla Firm. W przypadku udostępniania zdarzeń kolumna **Szczegóły** w obszarze **Wyniki** identyfikuje nazwę użytkownika lub grupy, którym element został udostępniony, oraz to, czy ten użytkownik lub grupa jest członkiem lub gościem w organizacji. Aby uzyskać więcej informacji, zobacz [Używanie inspekcji udostępniania w dzienniku inspekcji](use-sharing-auditing.md).

> [!NOTE]
> Użytkownicy mogą być  *członkami*  lub  *gośćmi*  na podstawie właściwości UserType obiektu użytkownika. Członek jest zwykle pracownikiem, a gość jest zwykle współpracownikiem spoza organizacji. Gdy użytkownik zaakceptuje zaproszenie do udostępniania (i nie jest jeszcze częścią organizacji), konto gościa zostanie utworzone dla niego w katalogu organizacji. Gdy użytkownik-gość ma konto w katalogu, zasoby mogą być udostępniane mu bezpośrednio (bez konieczności zaproszenia).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano poziom uprawnień do zbioru witryn|PermissionLevelAdded|Poziom uprawnień został dodany do zbioru witryn.|
|Akceptowane żądanie dostępu|AccessRequestAccepted|Żądanie dostępu do witryny, folderu lub dokumentu zostało zaakceptowane i użytkownikowi żądającemu udzielono dostępu.|
|Zaakceptowane zaproszenie do udostępniania|SharingInvitationAccepted|Użytkownik (członek lub gość) zaakceptował zaproszenie do udostępniania i otrzymał dostęp do zasobu. To zdarzenie zawiera informacje o zaproszonym użytkowniku oraz adres e-mail, który został użyty do zaakceptowania zaproszenia (mogą być inne). Temu działaniu często towarzyszy drugie zdarzenie opisujące sposób udzielenia użytkownikowi dostępu do zasobu, na przykład dodanie użytkownika do grupy, która ma dostęp do zasobu.|
|Zaproszenie do udostępniania zablokowane|SharingInvitationBlocked|Zaproszenie do udostępniania wysyłane przez użytkownika w organizacji jest blokowane z powodu zasad udostępniania zewnętrznego, które zezwalają na udostępnianie zewnętrzne lub odmawiają go w oparciu o domenę użytkownika docelowego. W takim przypadku zaproszenie do udostępniania zostało zablokowane, ponieważ: <br/> Domena użytkownika docelowego nie znajduje się na liście dozwolonych domen. <br/> Lub <br/> Domena użytkownika docelowego znajduje się na liście zablokowanych domen. <br/> Aby uzyskać więcej informacji na temat zezwalania na udostępnianie zewnętrzne lub blokowania go w oparciu o domeny, zobacz [Udostępnianie domen z ograniczeniami w usłudze SharePoint Online i OneDrive dla Firm](/sharepoint/restricted-domains-sharing).|
|Utworzone żądanie dostępu|AccessRequestCreated|Użytkownik żąda dostępu do witryny, folderu lub dokumentu, do których nie ma uprawnień dostępu.|
|Tworzenie linku do udostępniania firmy|CompanyLinkCreated|Użytkownik utworzył link do zasobu dla całej firmy. Linki dla całej firmy mogą być używane tylko przez członków w organizacji. Goście nie mogą ich używać.|
|Utworzono link anonimowy|AnonymousLinkCreated|Użytkownik utworzył anonimowy link do zasobu. Każdy, kto ma ten link, może uzyskać dostęp do zasobu bez konieczności uwierzytelniania.|
|Utworzono bezpieczny link|SecureLinkCreated|Do tego elementu utworzono link bezpiecznego udostępniania.|
|Zaproszenie do udostępniania utworzone|SharingInvitationCreated|Użytkownik udostępnił zasób w usłudze SharePoint Online lub OneDrive dla Firm użytkownikowi, który nie znajduje się w katalogu organizacji.|
|Usunięto bezpieczny link|SecureLinkDeleted|Usunięto link bezpiecznego udostępniania.|
|Żądanie odmowy dostępu|AccessRequestDenied|Żądanie dostępu do witryny, folderu lub dokumentu zostało odrzucone.|
|Usunięto link do udostępniania firmy|CompanyLinkRemoved|Użytkownik usunął link do zasobu dla całej firmy. Link nie może już służyć do uzyskiwania dostępu do zasobu.|
|Usunięto link anonimowy|AnonymousLinkRemoved|Użytkownik usunął anonimowy link do zasobu. Link nie może już służyć do uzyskiwania dostępu do zasobu.|
|Udostępniony plik, folder lub witryna|Zestaw udostępniania|Użytkownik (członek lub gość) udostępnił plik, folder lub witrynę w SharePoint lub OneDrive dla Firm użytkownikowi w katalogu organizacji. Wartość w kolumnie **Szczegóły** dla tego działania określa nazwę użytkownika, któremu został udostępniony zasób, oraz to, czy ten użytkownik jest członkiem, czy gościem. <br/><br/> Temu działaniu często towarzyszy drugie zdarzenie opisujące sposób udzielenia użytkownikowi dostępu do zasobu. Na przykład dodanie użytkownika do grupy, która ma dostęp do zasobu.|
|Zaktualizowane żądanie dostępu|AccessRequestUpdated|Zaktualizowano żądanie dostępu do elementu.|
|Zaktualizowano link anonimowy|AnonymousLinkUpdated|Użytkownik zaktualizował anonimowy link do zasobu. Zaktualizowane pole jest uwzględniane we właściwości EventData podczas eksportowania wyników wyszukiwania.|
|Zaktualizowane zaproszenie do udostępniania|SharingInvitationUpdated|Zaproszenie do udostępniania zewnętrznego zostało zaktualizowane.|
|Użyto linku anonimowego|AnonymousLinkUsed|Anonimowy użytkownik uzyskiwał dostęp do zasobu za pomocą linku anonimowego. Tożsamość użytkownika może być nieznana, ale można uzyskać inne szczegóły, takie jak adres IP użytkownika.|
|Plik, folder lub witryna nieudostępniona|SharingRevoked|Użytkownik (członek lub gość) anulował udostępnianie pliku, folderu lub witryny, która została wcześniej udostępniona innemu użytkownikowi.|
|Używany link do udostępniania firmy|CompanyLinkUsed|Użytkownik uzyskiwał dostęp do zasobu przy użyciu linku dla całej firmy.|
|Używany bezpieczny link|SecureLinkUsed|Użytkownik użył bezpiecznego linku.|
|Użytkownik dodany do bezpiecznego linku|DodanoToSecureLink|Użytkownik został dodany do listy jednostek, które mogą korzystać z linku bezpiecznego udostępniania.|
|Użytkownik usunięty z bezpiecznego linku|RemovedFromSecureLink|Użytkownik został usunięty z listy jednostek, które mogą korzystać z linku bezpiecznego udostępniania.|
|Wycofane zaproszenie do udostępniania|SharingInvitationRevoked|Użytkownik wycofał zaproszenie do udostępniania zasobu.|

### <a name="synchronization-activities"></a>Działania synchronizacji

W poniższej tabeli wymieniono działania synchronizacji plików w usłudze SharePoint Online i OneDrive dla Firm.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Zezwalanie komputerowi na synchronizowanie plików|ManagedSyncClientAllowed|Użytkownik pomyślnie ustanawia relację synchronizacji z witryną. Relacja synchronizacji powiodła się, ponieważ komputer użytkownika jest członkiem domeny, która została dodana do listy domen (nazywanych *listą bezpiecznych adresatów*), które mogą uzyskiwać dostęp do bibliotek dokumentów w organizacji. <br/><br/> Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Używanie poleceń cmdlet programu PowerShell do włączania synchronizacja usługi OneDrive dla domen znajdujących się na liście bezpiecznych adresatów](/powershell/module/sharepoint-online/).|
|Zablokowane synchronizowanie plików przez komputer|UnmanagedSyncClientBlocked|Użytkownik próbuje ustanowić relację synchronizacji z lokacją z komputera, który nie jest członkiem domeny organizacji lub jest członkiem domeny, która nie została dodana do listy domen (nazywanych  *listą bezpiecznych adresatów),*  która może uzyskiwać dostęp do bibliotek dokumentów w organizacji. Relacja synchronizacji jest niedozwolona, a komputer użytkownika nie może synchronizować, pobierać ani przekazywać plików w bibliotece dokumentów. <br/><br/> Aby uzyskać informacje o tej funkcji, zobacz [Używanie poleceń cmdlet programu PowerShell do włączania synchronizacja usługi OneDrive dla domen znajdujących się na liście bezpiecznych adresatów](/powershell/module/sharepoint-online/).|
|Pobrane pliki na komputer|FileSyncDownloadedFull|Użytkownik pobiera plik na swój komputer z biblioteki dokumentów SharePoint lub OneDrive dla Firm przy użyciu aplikacji synchronizacja usługi OneDrive (OneDrive.exe).|
|Pobrane zmiany pliku na komputerze|FileSyncDownloadedPartial|To zdarzenie zostało przestarzałe wraz ze starą aplikacją synchronizacji OneDrive dla Firm (Groove.exe).|
|Przekazane pliki do biblioteki dokumentów|FileSyncUploadedFull|Użytkownik przekazuje nowy plik lub zmiany do pliku w bibliotece dokumentów SharePoint lub OneDrive dla Firm przy użyciu aplikacji synchronizacja usługi OneDrive (OneDrive.exe).|
|Przekazane zmiany pliku do biblioteki dokumentów|FileSyncUploadedPartial|To zdarzenie zostało przestarzałe wraz ze starą aplikacją synchronizacji OneDrive dla Firm (Groove.exe).|

### <a name="site-permissions-activities"></a>Działania dotyczące uprawnień witryny

W poniższej tabeli wymieniono zdarzenia związane z przypisywaniem uprawnień w SharePoint i używaniem grup do udzielania (i odwoływania) dostępu do witryn. Jak wyjaśniono wcześniej, rekordy inspekcji dla niektórych działań SharePoint wskazują, app@sharepoint użytkownik wykonał działanie w imieniu użytkownika lub administratora, który zainicjował akcję. Aby uzyskać więcej informacji, zobacz [Temat Użytkownik programu SharePoint aplikacji\@w rekordach inspekcji](#the-appsharepoint-user-in-audit-records).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano administratora zbioru witryn|SiteCollectionAdminAdded|Administrator lub właściciel zbioru witryn dodaje osobę jako administratora zbioru witryn dla witryny. Administratorzy zbioru witryn mają uprawnienia pełnej kontroli dla zbioru witryn i wszystkich podwitryn. To działanie jest również rejestrowane, gdy administrator zapewnia sobie dostęp do konta OneDrive użytkownika (edytując profil użytkownika w centrum administracyjnym SharePoint lub [za pomocą Centrum administracyjne platformy Microsoft 365](/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data)).|
|Dodano użytkownika lub grupę do grupy SharePoint|AddedToGroup|Użytkownik dodał członka lub gościa do grupy SharePoint. Mogło to być zamierzone działanie lub wynik innego działania, takiego jak zdarzenie udostępniania.|
|Przerwane dziedziczenie poziomu uprawnień|PermissionLevelsInheritanceBroken|Element został zmieniony tak, aby nie dziedziczył już poziomów uprawnień po elemencie nadrzędnym.|
|Podział dziedziczenia udostępniania|SharingInheritanceBroken|Element został zmieniony tak, aby nie dziedziczył już uprawnień do udostępniania po jego elemencie nadrzędnym.|
|Utworzona grupa|GroupAdded|Administrator lub właściciel witryny tworzy grupę dla witryny lub wykonuje zadanie, które powoduje utworzenie grupy. Na przykład przy pierwszym utworzeniu linku do udostępniania pliku grupa systemowa jest dodawana do OneDrive dla Firm lokacji użytkownika. To zdarzenie może być również wynikiem utworzenia przez użytkownika linku z uprawnieniami do edycji do udostępnionego pliku.|
|Usunięto grupę|GrupaRemoved|Użytkownik usuwa grupę z witryny.|
|Zmodyfikowane ustawienie żądania dostępu|WebRequestAccessModified|Ustawienia żądania dostępu zostały zmodyfikowane w witrynie.|
|Zmodyfikowane ustawienie "Członkowie mogą udostępniać"|WebMembersCanShareModified|Ustawienie **Członkowie mogą udostępnić** została zmodyfikowana w witrynie.|
|Zmodyfikowany poziom uprawnień w zbiorze witryn|PermissionLevelModified|Poziom uprawnień został zmieniony w zbiorze witryn.|
|Zmodyfikowane uprawnienia witryny|SitePermissionsModified|Administrator witryny lub właściciel (lub konto systemowe) zmienia poziom uprawnień przypisany do grupy w witrynie. To działanie jest również rejestrowane, jeśli wszystkie uprawnienia zostaną usunięte z grupy. <br/><br/> **UWAGA**: Ta operacja została wycofana w usłudze SharePoint Online. Aby znaleźć powiązane zdarzenia, możesz wyszukać inne działania związane z uprawnieniami, takie jak **Dodano administratora zbioru witryn**, **Dodano użytkownika lub grupę do grupy SharePoint**, **Zezwalaj użytkownikowi na tworzenie grup**, **Utworzono grupę** i **Usunięto grupę.**|
|Usunięto poziom uprawnień z zbioru witryn|PermissionLevelRemoved|Poziom uprawnień został usunięty z zbioru witryn.|
|Usunięto administratora zbioru witryn|SiteCollectionAdminRemoved|Administrator lub właściciel zbioru witryn usuwa osobę jako administratora zbioru witryn dla witryny. To działanie jest również rejestrowane, gdy administrator usunie się z listy administratorów zbioru witryn dla konta OneDrive użytkownika (edytując profil użytkownika w centrum administracyjnym SharePoint).  Aby zwrócić to działanie w wynikach wyszukiwania dziennika inspekcji, należy wyszukać wszystkie działania.|
|Usunięto użytkownika lub grupę z grupy SharePoint|RemovedFromGroup|Użytkownik usunął członka lub gościa z grupy SharePoint. Mogło to być zamierzone działanie lub wynik innego działania, takiego jak zdarzenie bez udostępniania.|
|Żądane uprawnienia administratora witryny|SiteAdminChangeRequest|Użytkownik żąda dodania jako administrator zbioru witryn dla zbioru witryn. Administratorzy zbioru witryn mają uprawnienia pełnej kontroli dla zbioru witryn i wszystkich podwitryn.|
|Przywrócone dziedziczenie udostępniania|SharingInheritanceReset|Wprowadzono zmianę, dzięki czemu element dziedziczy uprawnienia do udostępniania po jego elemencie nadrzędnym.|
|Zaktualizowana grupa|GroupUpdated|Administrator lub właściciel witryny zmienia ustawienia grupy dla witryny. Może to obejmować zmianę nazwy grupy, osób, które mogą wyświetlać lub edytować członkostwo w grupie oraz sposobu obsługi żądań członkostwa.|

### <a name="site-administration-activities"></a>Działania administracji lokacji

W poniższej tabeli wymieniono zdarzenia wynikające z zadań administracji lokacji w usłudze SharePoint Online. Jak wyjaśniono wcześniej, rekordy inspekcji dla niektórych działań SharePoint wskazują, app@sharepoint użytkownik wykonał działanie w imieniu użytkownika lub administratora, który zainicjował akcję. Aby uzyskać więcej informacji, zobacz [Temat Użytkownik programu SharePoint aplikacji\@w rekordach inspekcji](#the-appsharepoint-user-in-audit-records).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano dozwoloną lokalizację danych|AllowedDataLocationAdded|Administrator SharePoint lub administrator globalny dodał dozwoloną lokalizację danych w środowisku z wieloma lokalizacjami geograficznymi.|
|Dodano zwolnionego agenta użytkownika|ExemptUserAgentSet|Administrator SharePoint lub administrator globalny dodał agenta użytkownika do listy zwolnionych agentów użytkowników w centrum administracyjnym SharePoint.|
|Dodano administratora lokalizacji geograficznej|GeoAdminAdded|Administrator SharePoint lub administrator globalny dodał użytkownika jako administratora geograficznego lokalizacji.|
|Zezwalanie użytkownikowi na tworzenie grup|AllowGroupCreationSet|Administrator lub właściciel witryny dodaje do witryny poziom uprawnień, który umożliwia użytkownikowi przypisanemu do tej lokacji utworzenie grupy dla tej witryny.|
|Anulowane przenoszenie geograficzne lokacji|SiteGeoMoveCancelled|Administrator SharePoint lub administrator globalny pomyślnie anuluje przenoszenie geograficzne lokacji SharePoint lub OneDrive. Funkcja Multi-Geo umożliwia organizacji obejmującą wiele obszarów geograficznych centrum danych firmy Microsoft, które są nazywane obszarami geograficznymi. Aby uzyskać więcej informacji, zobacz [Multi-Geo Capabilities in OneDrive and SharePoint Online (Możliwości wielu obszarów geograficznych w OneDrive i SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)).|
|Zmieniono zasady udostępniania|SharingPolicyChanged|Administrator SharePoint lub administrator globalny zmienił zasady udostępniania SharePoint przy użyciu Centrum administracyjne platformy Microsoft 365, centrum administracyjnego SharePoint lub powłoki zarządzania usługi SharePoint Online. Wszelkie zmiany ustawień w zasadach udostępniania w organizacji zostaną zarejestrowane. Zmienione zasady są identyfikowane w polu **ModifiedProperties** we szczegółowych właściwościach rekordu zdarzenia.|
|Zmienione zasady dostępu do urządzeń|DeviceAccessPolicyChanged|Administrator SharePoint lub administrator globalny zmienił zasady dotyczące urządzeń niezarządzanych w organizacji. Te zasady kontrolują dostęp do SharePoint, OneDrive i Microsoft 365 z urządzeń, które nie są przyłączone do organizacji. Skonfigurowanie tych zasad wymaga subskrypcji Enterprise Mobility + Security. Aby uzyskać więcej informacji, zobacz artykuł[Sterowanie dostępem z urządzeń niezarządzanych](/sharepoint/control-access-from-unmanaged-devices).|
|Zmieniono zwolnionych agentów użytkowników|CustomizeExemptUsers|Administrator SharePoint lub administrator globalny dostosował listę zwolnionych agentów użytkowników w centrum administracyjnym SharePoint. Możesz określić agentów użytkowników, którzy mają zostać wykluczeni z otrzymywania całej strony internetowej do indeksowania. Oznacza to, że gdy agent użytkownika określony jako wykluczony napotka formularz programu InfoPath, formularz zostanie zwrócony jako plik XML, a nie cała strona internetowa. Dzięki temu indeksowanie formularzy programu InfoPath jest szybsze.|
|Zmienione zasady dostępu do sieci|NetworkAccessPolicyChanged|Administrator SharePoint lub administrator globalny zmienił zasady dostępu oparte na lokalizacji (nazywane również granicą zaufanej sieci) w centrum administracyjnym SharePoint lub przy użyciu programu PowerShell SharePoint Online. Ten typ zasad kontroluje, kto może uzyskiwać dostęp do SharePoint i OneDrive zasobów w organizacji na podstawie określonych przez Ciebie zakresów autoryzowanych adresów IP. Aby uzyskać więcej informacji, zobacz [Kontrolowanie dostępu do SharePoint Online i OneDrive danych na podstawie lokalizacji sieciowej](/sharepoint/control-access-based-on-network-location).|
|Ukończono przenoszenie geograficzne lokacji|SiteGeoMoveCompleted|Pomyślnie ukończono przenoszenie geograficzne witryny zaplanowane przez administratora globalnego w organizacji. Funkcja Multi-Geo umożliwia organizacji obejmującą wiele obszarów geograficznych centrum danych firmy Microsoft, które są nazywane obszarami geograficznymi. Aby uzyskać więcej informacji, zobacz [Multi-Geo Capabilities in OneDrive and SharePoint Online (Możliwości wielu obszarów geograficznych w OneDrive i SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)).|
|Utworzono połączenie wysłane do|SendToConnectionAdded|Administrator SharePoint lub administrator globalny tworzy nowe połączenie Wyślij do na stronie zarządzania rekordami w centrum administracyjnym SharePoint. Połączenie Wyślij do określa ustawienia repozytorium dokumentów lub centrum rekordów. Podczas tworzenia połączenia Wyślij do organizator zawartości może przesyłać dokumenty do określonej lokalizacji.|
|Utworzony zbiór witryn|SiteCollectionCreated|Administrator SharePoint lub administrator globalny tworzy zbiór witryn w organizacji SharePoint Online lub użytkownik aprowizuje swoją witrynę OneDrive dla Firm.|
|Usunięto oddzieloną witrynę centrum|HubSiteOrphanHubDeleted|Administrator SharePoint lub administrator globalny usunął lokację centrum sierocego, czyli lokację centrum, która nie ma żadnych skojarzonych z nią witryn. Oddzielone centrum jest prawdopodobnie spowodowane usunięciem oryginalnej lokacji centrum.|
|Usunięto połączenie wysłane do|SendToConnectionRemoved|Administrator SharePoint lub administrator globalny usuwa połączenie Wyślij do na stronie zarządzania rekordami w centrum administracyjnym SharePoint.|
|Usunięta witryna|SiteDeleted|Administrator witryny usuwa witrynę.|
|Włączona wersja zapoznawcza dokumentu|PreviewModeEnabledSet|Administrator witryny włącza podgląd dokumentów dla witryny.|
|Włączony starszy przepływ pracy|LegacyWorkflowEnabledSet|Administrator lub właściciel witryny dodaje typ zawartości zadania przepływu pracy SharePoint 2013 do witryny. Administratorzy globalni mogą również włączyć przepływy pracy dla całej organizacji w centrum administracyjnym SharePoint.|
|Włączone Office na żądanie|Zestaw OfficeOnDemand|Administrator witryny umożliwia Office na żądanie, co umożliwia użytkownikom dostęp do najnowszej wersji aplikacji klasycznych Office. Office na żądanie jest włączona w centrum administracyjnym SharePoint i wymaga subskrypcji Microsoft 365 zawierającej pełne, zainstalowane aplikacje Office.|
|Włączone źródło wyników wyszukiwania osób|PeopleResultsScopeSet|Administrator witryny tworzy źródło wyników dla osób wyszukuje witrynę.|
|Włączone kanały informacyjne RSS|NewsFeedEnabledSet|Administrator lub właściciel witryny włącza kanały informacyjne RSS dla witryny. Administratorzy globalni mogą włączyć kanały informacyjne RSS dla całej organizacji w centrum administracyjnym SharePoint.|
|Przyłączona lokacja do lokacji centrum|HubSiteJoined|Właściciel witryny kojarzy swoją witrynę z lokacją centrum.|
|Zmodyfikowany limit przydziału zbioru witryn|SiteCollectionQuotaModified|Administrator witryny modyfikuje przydział zbioru witryn.|
|Zarejestrowana witryna centrum|HubSiteRegistered|Administrator SharePoint lub administrator globalny tworzy witrynę centrum. Wyniki są takie, że witryna jest zarejestrowana jako lokacja centrum.|
|Usunięto dozwoloną lokalizację danych|AllowedDataLocationDeleted|Administrator SharePoint lub administrator globalny usunął dozwoloną lokalizację danych w środowisku z wieloma lokalizacjami geograficznymi.|
|Usunięto administratora lokalizacji geograficznej|GeoAdminDeleted|Administrator SharePoint lub administrator globalny usunął użytkownika jako administratora geograficznego lokalizacji.|
|Zmieniono nazwę witryny|SiteRenamed|Administrator witryny lub właściciel zmienia nazwę witryny|
|Zaplanowane przenoszenie geograficzne lokacji|SiteGeoMoveScheduled|Administrator SharePoint lub administrator globalny pomyślnie planuje przeniesienie geograficzne SharePoint lub OneDrive lokacji. Funkcja Multi-Geo umożliwia organizacji obejmującą wiele obszarów geograficznych centrum danych firmy Microsoft, które są nazywane obszarami geograficznymi. Aby uzyskać więcej informacji, zobacz [Multi-Geo Capabilities in OneDrive and SharePoint Online (Możliwości wielu obszarów geograficznych w OneDrive i SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)).|
|Ustawianie witryny hosta|HostSiteSet|Administrator SharePoint lub administrator globalny zmienia wyznaczoną witrynę w celu hostowania witryn osobistych lub OneDrive dla Firm.|
|Ustawianie limitu przydziału magazynu dla lokalizacji geograficznej|GeoQuotaAllocated|Administrator SharePoint lub administrator globalny skonfigurował przydział magazynu dla lokalizacji geograficznej w środowisku z wieloma obszarami geograficznymi.|
|Witryna połączona z witryny centrum|HubSiteUnjoined|Właściciel witryny odłącza swoją witrynę od lokacji centrum.|
|Niezarejestrowana lokacja centrum|HubSiteUnregistered|Administrator SharePoint lub administrator globalny wyrejestruje lokację jako lokację centrum. Gdy lokacja koncentratora jest wyrejestrowana, nie działa już jako lokacja centrum.|

### <a name="exchange-mailbox-activities"></a>działania Exchange skrzynki pocztowej

W poniższej tabeli wymieniono działania, które mogą być rejestrowane przez rejestrowanie inspekcji skrzynki pocztowej. Działania skrzynki pocztowej wykonywane przez właściciela skrzynki pocztowej, delegowanego użytkownika lub administratora są automatycznie rejestrowane w dzienniku inspekcji przez maksymalnie 90 dni. Administrator może wyłączyć rejestrowanie inspekcji skrzynki pocztowej dla wszystkich użytkowników w organizacji. W takim przypadku żadne akcje skrzynki pocztowej dla żadnego użytkownika nie są rejestrowane. Aby uzyskać więcej informacji, zobacz [Zarządzanie inspekcją skrzynek pocztowych](enable-mailbox-auditing.md).

 Działania skrzynki pocztowej można również wyszukiwać za pomocą polecenia cmdlet [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Elementy skrzynki pocztowej z dostępem|MailItemsAccessed|Wiadomości były odczytywane lub uzyskiwane w skrzynce pocztowej. Rekordy inspekcji dla tego działania są wyzwalane na jeden z dwóch sposobów: gdy klient poczty (na przykład Outlook) wykonuje operację powiązania na komunikatach lub gdy protokoły poczty (takie jak Exchange ActiveSync lub IMAP) synchronizują elementy w folderze poczty. To działanie jest rejestrowane tylko dla użytkowników z licencją Office 365 lub Microsoft 365 E5. Analizowanie rekordów inspekcji dla tego działania jest przydatne podczas badania naruszonego konta e-mail. Aby uzyskać więcej informacji, zobacz sekcję "Inspekcja (Premium) zdarzeń" w sekcji [Inspekcja (Premium)](advanced-audit.md#audit-premium-events). |
|Dodano uprawnienia delegowanych skrzynek pocztowych|Add-MailboxPermission|Administrator przypisył uprawnienie do skrzynki pocztowej funkcji FullAccess użytkownikowi (znanemu jako pełnomocnik) do skrzynki pocztowej innej osoby. Uprawnienie FullAccess umożliwia pełnomocnikowi otwieranie skrzynki pocztowej innej osoby oraz odczytywanie zawartości skrzynki pocztowej i zarządzanie nią. Rekord inspekcji dla tego działania jest również generowany, gdy konto systemowe w usłudze Microsoft 365 okresowo wykonuje zadania konserwacji w imieniu organizacji. Typowym zadaniem wykonywanym przez konto systemowe jest aktualizowanie uprawnień dla systemowych skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [Konta systemowe w rekordach inspekcji Exchange skrzynki pocztowej](#system-accounts-in-exchange-mailbox-audit-records).|
|Dodano lub usunięto użytkownika z delegowaniem dostępu do folderu kalendarza|UpdateCalendarDelegation|Użytkownik został dodany lub usunięty jako pełnomocnik do kalendarza skrzynki pocztowej innego użytkownika. Delegowanie kalendarza daje innej osobie w tej samej organizacji uprawnienia do zarządzania kalendarzem właściciela skrzynki pocztowej.|
|Dodano uprawnienia do folderu|DodajfolderPermissions|Dodano uprawnienie folderu. Uprawnienia folderu określają, którzy użytkownicy w organizacji mogą uzyskiwać dostęp do folderów w skrzynce pocztowej i wiadomości znajdujących się w tych folderach.|
|Skopiowano komunikaty do innego folderu|Kopii|Wiadomość została skopiowana do innego folderu.|
|Utworzony element skrzynki pocztowej|Tworzenie|Element jest tworzony w folderze Kalendarz, Kontakty, Notatki lub Zadania w skrzynce pocztowej. Na przykład zostanie utworzone nowe żądanie spotkania. Tworzenie, wysyłanie lub odbieranie komunikatu nie jest poddawane inspekcji. Ponadto tworzenie folderu skrzynki pocztowej nie jest poddawane inspekcji.|
|Utworzono nową regułę skrzynki odbiorczej w Outlook aplikacji internetowej|New-InboxRule|Właściciel skrzynki pocztowej lub inny użytkownik z dostępem do skrzynki pocztowej utworzył regułę skrzynki odbiorczej w aplikacji internetowej Outlook.|
|Usunięte komunikaty z folderu Elementy usunięte|SoftDelete|Komunikat został trwale usunięty lub usunięty z folderu Elementy usunięte. Te elementy są przenoszone do folderu Elementy możliwe do odzyskania. Komunikaty są również przenoszone do folderu Elementy możliwe do odzyskania po wybraniu go przez użytkownika i naciśnięciu klawiszy **Shift+Delete**.|
|Komunikat oznaczony etykietą jako rekord|ApplyRecordLabel|Wiadomość została sklasyfikowana jako rekord. Dzieje się tak, gdy etykieta przechowywania, która klasyfikuje zawartość jako rekord, jest ręcznie lub automatycznie stosowana do komunikatu.|
|Przeniesiono komunikaty do innego folderu|Przenieść|Wiadomość została przeniesiona do innego folderu.|
|Przeniesione komunikaty do folderu Elementy usunięte|MoveToDeletedItems|Komunikat został usunięty i przeniesiony do folderu Elementy usunięte.|
|Zmodyfikowane uprawnienie folderu|UpdateFolderPermissions|Zmieniono uprawnienie folderu. Uprawnienia folderu określają, którzy użytkownicy w organizacji mogą uzyskiwać dostęp do folderów skrzynki pocztowej i wiadomości w folderze.|
|Zmodyfikowana reguła skrzynki odbiorczej z Outlook aplikacji internetowej|Set-InboxRule|Właściciel skrzynki pocztowej lub inny użytkownik z dostępem do skrzynki pocztowej zmodyfikował regułę skrzynki odbiorczej przy użyciu aplikacji internetowej Outlook.|
|Przeczyszczane wiadomości ze skrzynki pocztowej|HardDelete|Wiadomość została usunięta z folderu Elementy możliwe do odzyskania (trwale usunięta ze skrzynki pocztowej).|
|Usunięto uprawnienia delegowanych skrzynek pocztowych|Remove-MailboxPermission|Administrator usunął uprawnienie FullAccess (przypisane do pełnomocnika) ze skrzynki pocztowej danej osoby. Po usunięciu uprawnienia FullAccess pełnomocnik nie może otworzyć skrzynki pocztowej innej osoby ani uzyskać do niej dostępu.|
|Usunięto uprawnienia z folderu|RemoveFolderPermissions|Usunięto uprawnienie folderu. Uprawnienia folderu określają, którzy użytkownicy w organizacji mogą uzyskiwać dostęp do folderów w skrzynce pocztowej i wiadomości znajdujących się w tych folderach.|
|Wysłana wiadomość|Wyślij|Wiadomość została wysłana, przekazana lub przekazana dalej. To działanie jest rejestrowane tylko dla użytkowników z licencją Office 365 lub Microsoft 365 E5. Aby uzyskać więcej informacji, zobacz sekcję "Inspekcja (Premium) zdarzeń" w sekcji [Inspekcja (Premium)](advanced-audit.md#audit-premium-events).|
|Wysłano wiadomość przy użyciu uprawnień Wyślij jako|SendAs|Wiadomość została wysłana przy użyciu uprawnienia SendAs. Oznacza to, że inny użytkownik wysłał wiadomość tak, jakby pochodziła od właściciela skrzynki pocztowej.|
|Wysłano wiadomość przy użyciu uprawnień Wyślij w imieniu|SendOnBehalf|Wiadomość została wysłana przy użyciu uprawnienia SendOnBehalf. Oznacza to, że inny użytkownik wysłał wiadomość w imieniu właściciela skrzynki pocztowej. Wiadomość wskazuje adresatowi, któremu wiadomość została wysłana w imieniu użytkownika i który faktycznie wysłał wiadomość.|
|Zaktualizowano reguły skrzynki odbiorczej z klienta Outlook|UpdateInboxRules|Właściciel skrzynki pocztowej lub inny użytkownik z dostępem do skrzynki pocztowej utworzonej, zmodyfikowanej lub usuniętej reguły skrzynki odbiorczej przy użyciu klienta Outlook.|
|Zaktualizowano komunikat|Aktualizacja|Komunikat lub jego właściwości zostały zmienione.|
|Użytkownik zalogowany do skrzynki pocztowej|MailboxLogin|Użytkownik zalogował się do swojej skrzynki pocztowej.|
|Etykieta komunikatu jako rekordu||Użytkownik zastosował etykietę przechowywania do wiadomości e-mail i ta etykieta jest skonfigurowana do oznaczania elementu jako rekordu. |

#### <a name="system-accounts-in-exchange-mailbox-audit-records"></a>Konta systemowe w rekordach inspekcji Exchange skrzynki pocztowej

W rekordach inspekcji dla niektórych działań skrzynki pocztowej (zwłaszcza **Add-MailboxPermissions**) można zauważyć, że użytkownik, który wykonał działanie (i jest identyfikowany w polach Użytkownik i UserId) jest NT AUTHORITY\SYSTEM lub NT AUTHORITY\SYSTEM(Microsoft.Exchange. Servicehost). Oznacza to, że "użytkownik", który wykonał działanie, był kontem systemowym w usłudze Exchange w chmurze firmy Microsoft. To konto systemowe często wykonuje zadania konserwacji zaplanowanej w imieniu organizacji. Na przykład typowe inspekcji działania wykonywane przez NT AUTHORITY\SYSTEM (Microsoft.Exchange. Konto ServiceHost) ma zaktualizować uprawnienia do skrzynki pocztowej DiscoverySearchMailbox, która jest systemową skrzynką pocztową. Celem tej aktualizacji jest sprawdzenie, czy uprawnienie FullAccess (które jest domyślne) jest przypisane do grupy ról Zarządzania odnajdywaniem dla usługi DiscoverySearchMailbox.The purpose of this update is to verify that the FullAccess permission (czyli default) issigned to the Discovery Management role group for the DiscoverySearchMailbox. Dzięki temu administratorzy zbierania elektronicznych materiałów dowodowych mogą wykonywać niezbędne zadania w swojej organizacji.

Inne konto użytkownika systemu, które może zostać zidentyfikowane w rekordzie inspekcji **add-mailboxPermission** jest Administrator@apcprd03.prod.outlook.com. To konto usługi jest również zawarte w rekordach inspekcji skrzynki pocztowej związanych z weryfikowaniem i aktualizowaniem uprawnienia FullAccess jest przypisywane do grupy ról Zarządzanie odnajdywaniem dla skrzynki pocztowej systemu DiscoverySearchMailbox. W szczególności rekordy inspekcji identyfikujące konto Administrator@apcprd03.prod.outlook.com są zwykle wyzwalane, gdy personel pomocy technicznej firmy Microsoft uruchamia narzędzie diagnostyczne roli RBAC w imieniu organizacji.

### <a name="user-administration-activities"></a>Działania administracyjne użytkowników

Poniższa tabela zawiera listę działań administracyjnych użytkowników, które są rejestrowane, gdy administrator dodaje lub zmienia konto użytkownika przy użyciu [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) lub portalu zarządzania platformy Azure.

> [!NOTE]
> Nazwy operacji wymienione w kolumnie **Operacja** w poniższej tabeli zawierają kropkę ( `.` ). Okres należy uwzględnić w nazwie operacji, jeśli określisz operację w poleceniu programu PowerShell podczas przeszukiwania dziennika inspekcji, tworzenia zasad przechowywania inspekcji, tworzenia zasad alertów lub tworzenia alertów aktywności. Pamiętaj również, aby użyć podwójnego cudzysłowu (`" "`), aby zawierać nazwę operacji.

|Działanie|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano użytkownika|Dodaj użytkownika.|Utworzono konto użytkownika.|
|Zmieniono licencję użytkownika|Zmień licencję użytkownika.|Licencja przypisana do użytkownika, co się zmieniło. Aby zobaczyć, jakie licencje zostały wprowadzone, zobacz odpowiednie **zaktualizowane działanie użytkownika** .|
|Zmieniono hasło użytkownika|Zmień hasło użytkownika.|Użytkownik zmienia swoje hasło. Samoobsługowe resetowanie hasła musi być włączone (dla wszystkich lub wybranych użytkowników) w organizacji, aby umożliwić użytkownikom resetowanie hasła. Aktywność samoobsługowego resetowania haseł można również śledzić w Azure Active Directory. Aby uzyskać więcej informacji, zobacz [Opcje raportowania dotyczące zarządzania hasłami Azure AD](/azure/active-directory/authentication/howto-sspr-reporting).
|Usunięty użytkownik|Usuń użytkownika.|Konto użytkownika zostało usunięte.|
|Resetowanie hasła użytkownika|Resetowanie hasła użytkownika.|Administrator resetuje hasło użytkownika.|
|Ustaw właściwość, która wymusza zmianę hasła przez użytkownika|Ustaw wymuszanie zmiany hasła użytkownika.|Administrator ustawi właściwość, która wymusza zmianę hasła przy następnym logowaniu użytkownika do Microsoft 365.|
|Ustawianie właściwości licencji|Ustaw właściwości licencji.|Administrator modyfikuje właściwości licencji przypisanej do użytkownika.|
|Zaktualizowany użytkownik|Zaktualizuj użytkownika.|Administrator zmienia co najmniej jedną właściwości konta użytkownika. Aby uzyskać listę właściwości użytkownika, które można zaktualizować, zobacz sekcję "Aktualizowanie atrybutów użytkownika" w [Azure Active Directory Inspekcja zdarzeń raportu](/azure/active-directory/reports-monitoring/concept-audit-logs).|

### <a name="azure-ad-group-administration-activities"></a>Azure AD działań administracyjnych grupy

Poniższa tabela zawiera listę działań administracyjnych grupy, które są rejestrowane, gdy administrator lub użytkownik tworzy lub zmienia grupę Microsoft 365 lub gdy administrator tworzy grupę zabezpieczeń przy użyciu [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) lub portalu zarządzania platformy Azure. Aby uzyskać więcej informacji na temat grup w Microsoft 365, zobacz [Wyświetlanie, tworzenie i usuwanie grup w Centrum administracyjne platformy Microsoft 365](../admin/create-groups/create-groups.md).

> [!NOTE]
> Nazwy operacji wymienione w kolumnie **Operacja** w poniższej tabeli zawierają kropkę ( `.` ). Okres należy uwzględnić w nazwie operacji, jeśli określisz operację w poleceniu programu PowerShell podczas przeszukiwania dziennika inspekcji, tworzenia zasad przechowywania inspekcji, tworzenia zasad alertów lub tworzenia alertów aktywności. Pamiętaj również, aby użyć podwójnego cudzysłowu (`" "`), aby zawierać nazwę operacji.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano grupę|Dodaj grupę.|Utworzono grupę.|
|Dodano członka do grupy|Dodaj członka do grupy.|Element członkowski został dodany do grupy.|
|Usunięto grupę|Usuń grupę.|Grupa została usunięta.|
|Usunięto członka z grupy|Usuń członka z grupy.|Element członkowski został usunięty z grupy.|
|Zaktualizowana grupa|Zaktualizuj grupę.|Zmieniono właściwość grupy.|

### <a name="application-administration-activities"></a>Działania administracji aplikacjami

Poniższa tabela zawiera listę działań administratora aplikacji, które są rejestrowane, gdy administrator dodaje lub zmienia aplikację zarejestrowaną w Azure AD. Każda aplikacja, która korzysta z Azure AD uwierzytelniania, musi zostać zarejestrowana w katalogu.

> [!NOTE]
> Nazwy operacji wymienione w kolumnie **Operacja** w poniższej tabeli zawierają kropkę ( `.` ). Okres należy uwzględnić w nazwie operacji, jeśli określisz operację w poleceniu programu PowerShell podczas przeszukiwania dziennika inspekcji, tworzenia zasad przechowywania inspekcji, tworzenia zasad alertów lub tworzenia alertów aktywności. Pamiętaj również, aby użyć podwójnego cudzysłowu (`" "`), aby zawierać nazwę operacji.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano wpis delegowania|Dodaj wpis delegowania.|Utworzono/udzielono uprawnienia uwierzytelniania aplikacji w Azure AD.|
|Dodano jednostkę usługi|Dodaj jednostkę usługi.|Aplikacja została zarejestrowana w Azure AD. Aplikacja jest reprezentowana przez jednostkę usługi w katalogu.|
|Dodano poświadczenia do jednostki usługi|Dodaj poświadczenia jednostki usługi.|Poświadczenia zostały dodane do jednostki usługi w Azure AD. Zasada usługi reprezentuje aplikację w katalogu.|
|Usunięto wpis delegowania|Usuń wpis delegowania.|Uprawnienie uwierzytelniania zostało usunięte z aplikacji w Azure AD.|
|Usunięto jednostkę usługi z katalogu|Usuń jednostkę usługi.|Aplikacja została usunięta/wyrejestrowana z Azure AD. Aplikacja jest reprezentowana przez jednostkę usługi w katalogu.|
|Usunięto poświadczenia z jednostki usługi|Usuń poświadczenia jednostki usługi.|Poświadczenia zostały usunięte z jednostki usługi w Azure AD. Zasada usługi reprezentuje aplikację w katalogu.|
|Ustawianie wpisu delegowania|Ustaw wpis delegowania.|Zaktualizowano uprawnienie uwierzytelniania dla aplikacji w Azure AD.|

### <a name="role-administration-activities"></a>Działania administrowania rolami

W poniższej tabeli wymieniono Azure AD działań administracyjnych ról, które są rejestrowane, gdy administrator zarządza rolami administratora w [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) lub w portalu zarządzania platformy Azure.

> [!NOTE]
> Nazwy operacji wymienione w kolumnie **Operacja** w poniższej tabeli zawierają kropkę ( `.` ). Okres należy uwzględnić w nazwie operacji, jeśli określisz operację w poleceniu programu PowerShell podczas przeszukiwania dziennika inspekcji, tworzenia zasad przechowywania inspekcji, tworzenia zasad alertów lub tworzenia alertów aktywności. Pamiętaj również, aby użyć podwójnego cudzysłowu (`" "`), aby zawierać nazwę operacji.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodawanie elementu członkowskiego do roli|Dodaj element członkowski do roli.|Dodano użytkownika do roli administratora w Microsoft 365.|
|Usunięto użytkownika z roli katalogu|Usuń członka z roli.|Usunięto użytkownika z roli administratora w Microsoft 365.|
|Ustawianie informacji kontaktowych firmy|Ustaw informacje kontaktowe firmy.|Zaktualizowano preferencje kontaktów na poziomie firmy dla organizacji. Obejmuje to adresy e-mail związane z subskrypcją wysyłane przez Microsoft 365 oraz powiadomienia techniczne dotyczące usług.|

### <a name="directory-administration-activities"></a>Działania administracji katalogowej

W poniższej tabeli wymieniono Azure AD działania związane z katalogiem i domeną, które są rejestrowane, gdy administrator zarządza organizacją w [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) lub w portalu zarządzania platformy Azure.

> [!NOTE]
> Nazwy operacji wymienione w kolumnie **Operacja** w poniższej tabeli zawierają kropkę ( `.` ). Okres należy uwzględnić w nazwie operacji, jeśli określisz operację w poleceniu programu PowerShell podczas przeszukiwania dziennika inspekcji, tworzenia zasad przechowywania inspekcji, tworzenia zasad alertów lub tworzenia alertów aktywności. Pamiętaj również, aby użyć podwójnego cudzysłowu (`" "`), aby zawierać nazwę operacji.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dodano domenę do firmy|Dodaj domenę do firmy.|Dodano domenę do organizacji.|
|Dodano partnera do katalogu|Dodaj partnera do firmy.|Dodano partnera (administratora delegowanego) do organizacji.|
|Usunięto domenę z firmy|Usuń domenę z firmy.|Usunięto domenę z organizacji.|
|Usunięto partnera z katalogu|Usuń partnera z firmy.|Usunięto partnera (administratora delegowanego) z organizacji.|
|Ustawianie informacji o firmie|Ustaw informacje o firmie.|Zaktualizowano informacje o firmie dla organizacji. Obejmuje to adresy e-mail związane z subskrypcją wysyłane przez Microsoft 365 oraz powiadomienia techniczne dotyczące usług Microsoft 365.|
|Ustawianie uwierzytelniania domeny|Ustaw uwierzytelnianie domeny.|Zmieniono ustawienie uwierzytelniania domeny dla organizacji.|
|Zaktualizowano ustawienia federacji dla domeny|Ustaw ustawienia federacji w domenie.|Zmieniono ustawienia federacji (udostępniania zewnętrznego) dla organizacji.|
|Ustawianie zasad haseł|Ustaw zasady haseł.|Zmieniono ograniczenia długości i znaków haseł użytkowników w organizacji.|
|Włączono synchronizację Azure AD|Ustaw flagę DirSyncEnabled.|Ustaw właściwość, która włącza katalog dla Azure AD Sync.|
|Zaktualizowana domena|Zaktualizuj domenę.|Zaktualizowano ustawienia domeny w organizacji.|
|Zweryfikowana domena|Sprawdź domenę.|Sprawdź, czy Twoja organizacja jest właścicielem domeny.|
|Zweryfikowana domena zweryfikowana pocztą e-mail|Sprawdź domenę zweryfikowaną pocztą e-mail.|Używana weryfikacja poczty e-mail w celu sprawdzenia, czy Organizacja jest właścicielem domeny.|

### <a name="ediscovery-activities"></a>Działania zbierania elektronicznych materiałów dowodowych

W dzienniku inspekcji są rejestrowane działania związane z wyszukiwaniem zawartości i zbierania elektronicznych materiałów dowodowych, które są wykonywane w portalu zabezpieczeń i zgodności lub przy użyciu odpowiednich poleceń cmdlet programu PowerShell. Obejmuje to następujące działania:

- Tworzenie przypadków zbierania elektronicznych materiałów dowodowych i zarządzanie nimi

- Tworzenie, uruchamianie i edytowanie wyszukiwania zawartości

- Wykonywanie akcji wyszukiwania zawartości, takich jak wyświetlanie podglądu, eksportowanie i usuwanie wyników wyszukiwania

- Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości

- Zarządzanie rolą administratora zbierania elektronicznych materiałów dowodowych

Aby uzyskać listę i szczegółowy opis zarejestrowanych działań zbierania elektronicznych materiałów dowodowych, zobacz [Wyszukiwanie działań zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> Wyświetlenie w wynikach wyszukiwania zdarzeń wynikających z działań wymienionych w obszarze Działania zbierania **elektronicznych** materiałów dowodowych i **działań zbierania elektronicznych materiałów dowodowych (Premium)** na liście rozwijanej **Działania**. Z drugiej strony wyświetlenie odpowiednich zdarzeń z działań poleceń cmdlet zbierania elektronicznych materiałów dowodowych trwa do 24 godzin.

### <a name="ediscovery-premium-activities"></a>Działania zbierania elektronicznych materiałów dowodowych (Premium)

Możesz również wyszukać w dzienniku inspekcji działania w Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium). Opis tych działań można znaleźć w sekcji "Działania zbierania elektronicznych materiałów dowodowych (Premium) w [temacie Wyszukiwanie działań zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-premium-activities).

### <a name="power-bi-activities"></a>działania Power BI

W dzienniku inspekcji można wyszukiwać działania w Power BI. Aby uzyskać informacje o działaniach Power BI, zobacz sekcję "Działania poddane inspekcji przez Power BI" w [temacie Korzystanie z inspekcji w organizacji](/power-bi/service-admin-auditing#activities-audited-by-power-bi).

Rejestrowanie inspekcji dla Power BI nie jest domyślnie włączone. Aby wyszukać działania Power BI w dzienniku inspekcji, musisz włączyć inspekcję w portalu administracyjnym Power BI. Aby uzyskać instrukcje, zobacz sekcję "Dzienniki inspekcji" w [portalu administracyjnym Power BI](/power-bi/service-admin-portal#audit-logs).

### <a name="workplace-analytics-activities"></a>Działania związane z analizą miejsca pracy

Usługa Workplace Analytics zapewnia wgląd w sposób współpracy grup w całej organizacji. W poniższej tabeli wymieniono działania wykonywane przez użytkowników, którzy mają przypisaną rolę administratora lub role analityka w usłudze Workplace Analytics. Użytkownicy przypisani do roli analityka mają pełny dostęp do wszystkich funkcji usługi i używają produktu do analizy. Użytkownicy przypisani do roli Administrator mogą konfigurować ustawienia prywatności i ustawienia domyślne systemu oraz przygotowywać, przekazywać i weryfikować dane organizacyjne w usłudze Workplace Analytics. Aby uzyskać więcej informacji, zobacz [Workplace Analytics](/workplace-analytics/index-orig).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Dostęp do linku OData|AccessedOdataLink|Analityk uzyskiwał dostęp do linku OData dla zapytania.|
|Anulowane zapytanie|CanceledQuery|Analityk anulował uruchomione zapytanie.|
|Utworzono wykluczenie spotkania|MeetingExclusionCreated|Analityk utworzył regułę wykluczenia spotkania.|
|Usunięty wynik|DeletedResult|Analityk usunął wynik zapytania.|
|Pobrany raport|Pobranyraport|Analityk pobrał plik wyników zapytania.|
|Wykonane zapytanie|ExecutedQuery|Analityk uruchomił zapytanie.|
|Zaktualizowane ustawienie dostępu do danych|UpdatedDataAccessSetting|Administracja zaktualizowane ustawienia dostępu do danych.|
|Zaktualizowane ustawienie prywatności|AktualizacjaPrivacySetting|Administracja zaktualizowane ustawienia prywatności, na przykład minimalny rozmiar grupy.|
|Przekazane dane organizacji|UploadedOrgData|Administracja przekazany plik danych organizacji.|
|Zalogowany użytkownik<sup>*</sup>| UserLoggedIn |Użytkownik zalogował się do swojego konta użytkownika Microsoft 365.|
|Użytkownik wylogowany<sup>*</sup>| UserLoggedOff |Użytkownik wylogowył się ze swojego konta użytkownika Microsoft 365.
|Wyświetlone eksplorowanie|ViewedExplore|Wizualizacje przeglądane przez analityków na co najmniej jednej karcie Eksploruj stronę.|

> [!NOTE]
> <sup>*</sup>Są to Azure Active Directory działania logowania i logowania. Te działania są rejestrowane, nawet jeśli nie masz włączonej usługi Workplace Analytics w organizacji. Aby uzyskać więcej informacji na temat działań związanych z logowaniem [użytkowników, zobacz Logowanie w Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins).

### <a name="microsoft-teams-activities"></a>działania Microsoft Teams

Dziennik inspekcji można przeszukiwać pod kątem działań użytkowników i administratorów w Microsoft Teams. Teams jest obszarem roboczym wyśrodkowanym na czacie w Microsoft 365. Łączy rozmowy, spotkania, pliki i notatki zespołu w jednym miejscu. Aby uzyskać opisy działań Teams, które są poddawane inspekcji, zobacz [Wyszukiwanie w dzienniku inspekcji zdarzeń w Microsoft Teams](/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Microsoft Teams działania w zakresie opieki zdrowotnej

Jeśli Twoja organizacja używa [aplikacji Pacjenci](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) w Microsoft Teams, możesz wyszukać w dzienniku inspekcji działania związane z aplikacją Pacjenci. Jeśli środowisko jest skonfigurowane do obsługi aplikacji Pacjenci, dodatkowa grupa działań dla tych działań jest dostępna na liście selektora **Działania** .

![Microsoft Teams działań opieki zdrowotnej na liście selektorów działań.](../media/TeamsHealthcareAuditActivities.png)

Aby uzyskać opis działań aplikacji Pacjenci, zobacz [Dzienniki inspekcji dla aplikacji Pacjenci](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>działania Microsoft Teams Shifts

Jeśli Twoja organizacja korzysta z aplikacji Shifts w Microsoft Teams, możesz wyszukać w dzienniku inspekcji działania związane z aplikacją Shifts. Jeśli środowisko jest skonfigurowane do obsługi aplikacji Shifts, dodatkowa grupa działań dla tych działań jest dostępna na liście **selektora działania** .

Aby uzyskać opis działań aplikacji Shifts, zobacz [Wyszukiwanie w dzienniku inspekcji zdarzeń w Microsoft Teams](/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>działania Yammer

W poniższej tabeli wymieniono działania użytkownika i administratora w Yammer, które są rejestrowane w dzienniku inspekcji. Aby zwrócić działania związane z Yammer z dziennika inspekcji, musisz wybrać pozycję **Pokaż wyniki dla wszystkich działań** na liście **Działania**. Użyj pól zakresu dat i listy **Użytkownicy** , aby zawęzić wyniki wyszukiwania.

> [!NOTE]
> Niektóre działania inspekcji Yammer są dostępne tylko w obszarze Inspekcja (Premium). Oznacza to, że użytkownicy muszą mieć przypisaną odpowiednią licencję, zanim te działania zostaną zarejestrowane w dzienniku inspekcji. Aby uzyskać więcej informacji o działaniach dostępnych tylko w obszarze Inspekcja (Premium), zobacz [Audit (Premium) in Microsoft 365 (Inspekcja (Premium) w Microsoft 365](advanced-audit.md#audit-premium-events). Aby zapoznać się z wymaganiami dotyczącymi licencjonowania inspekcji (Premium), zobacz [Auditing solutions in Microsoft 365 (Rozwiązania inspekcji w Microsoft 365](auditing-solutions-overview.md#licensing-requirements)). <br/><br/>W poniższej tabeli działania inspekcji (Premium) są wyróżnione gwiazdką (*).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Zmienione zasady przechowywania danych|SoftDeleteSettingsUpdated|Zweryfikowany administrator aktualizuje ustawienie zasad przechowywania danych sieciowych do usunięcia twardego lub nietrwałego. Tę operację mogą wykonać tylko zweryfikowali administratorzy.|
|Zmieniono konfigurację sieci|NetworkConfigurationUpdated|Sieć lub zweryfikowany administrator zmienia konfigurację sieci Yammer. Obejmuje to ustawienie interwału eksportowania danych i włączania czatu.|
|Zmieniono ustawienia profilu sieciowego|ProcessProfileFields|Sieć lub zweryfikowany administrator zmienia informacje wyświetlane w profilach elementów członkowskich dla sieci użytkowników sieci.|
|Zmieniono tryb zawartości prywatnej|NadzorcaAdminToggled|Zweryfikowany administrator włącza lub wyłącza  *tryb zawartości prywatnej*  . Ten tryb umożliwia administratorowi wyświetlanie wpisów w grupach prywatnych i wyświetlanie prywatnych wiadomości między poszczególnymi użytkownikami (lub grupami użytkowników). Tylko zweryfikowane administratorzy mogą wykonać tę operację.|
|Zmieniono konfigurację zabezpieczeń|NetworkSecurityConfigurationUpdated|Zweryfikowany administrator aktualizuje konfigurację zabezpieczeń sieci Yammer. Obejmuje to ustawienie zasad wygasania haseł i ograniczeń dotyczących adresów IP. Tę operację mogą wykonać tylko zweryfikowali administratorzy.|
|Utworzony plik|FileCreated|Użytkownik przekazuje plik.|
|Utworzona grupa|GroupCreation (Tworzenie grupy)|Użytkownik tworzy grupę.|
|Utworzono komunikat<sup>*</sup>|MessageCreated|Użytkownik tworzy komunikat.|
|Usunięto grupę|GroupDeletion|Grupa jest usuwana z Yammer.|
|Usunięto komunikat|MessageDeleted|Użytkownik usuwa komunikat.|
|Pobrany plik|FileDownloaded|Użytkownik pobiera plik.|
|Wyeksportowane dane|DataExport|Zweryfikowany administrator eksportuje Yammer danych sieciowych. Tę operację mogą wykonać tylko zweryfikowali administratorzy.|
|Nie można uzyskać dostępu do społeczności<sup>*</sup>|CommunityAccessFailure|Użytkownik nie mógł uzyskać dostępu do społeczności.|
|Nie można uzyskać dostępu do pliku<sup>*</sup>|FileAccessFailure|Użytkownik nie może uzyskać dostępu do pliku.|
|Nie można uzyskać dostępu do komunikatu<sup>*</sup>|MessageAccessFailure|Użytkownik nie może uzyskać dostępu do komunikatu.|
|Plik udostępniony|FileShared|Użytkownik udostępnia plik innemu użytkownikowi.|
|Zawieszony użytkownik sieci|NetworkUserSuspended|Sieć lub zweryfikowany administrator wstrzymuje (dezaktywuje) użytkownika z Yammer.|
|Zawieszony użytkownik|UserSuspension|Konto użytkownika jest zawieszone (dezaktywowane).|
|Zaktualizowany opis pliku|FileUpdateDescription|Użytkownik zmienia opis pliku.|
|Zaktualizowana nazwa pliku|FileUpdateName|Użytkownik zmienia nazwę pliku.|
|Zaktualizowano komunikat<sup>*</sup>|MessageUpdated|Użytkownik aktualizuje komunikat.|
|Wyświetlony plik|FileVisited|Użytkownik wyświetla plik.|
|Wyświetlony komunikat<sup>*</sup>|MessageViewed|Użytkownik wyświetla komunikat.|

### <a name="microsoft-power-automate-activities"></a>Działania firmy Microsoft Power Automate

W dzienniku inspekcji można wyszukiwać działania w Power Automate (dawniej nazywanych Microsoft Flow). Działania te obejmują tworzenie, edytowanie i usuwanie przepływów oraz zmienianie uprawnień przepływu. Aby uzyskać informacje na temat inspekcji działań Power Automate, zobacz blog [Power Automate zdarzenia inspekcji dostępne teraz w portalu zgodności](https://flow.microsoft.com/blog/security-and-compliance-center).

### <a name="microsoft-power-apps-activities"></a>Działania firmy Microsoft Power Apps

Dziennik inspekcji można przeszukiwać pod kątem działań związanych z aplikacją w Power Apps. Te działania obejmują tworzenie, uruchamianie i publikowanie aplikacji. Przypisywanie uprawnień do aplikacji jest również poddawane inspekcji. Aby uzyskać opis wszystkich działań Power Apps, zobacz [Rejestrowanie aktywności dla Power Apps](/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>działania Microsoft Stream

W dzienniku inspekcji można wyszukiwać działania w Microsoft Stream. Działania te obejmują działania wideo wykonywane przez użytkowników, działania kanału grupy i działania administratora, takie jak zarządzanie użytkownikami, zarządzanie ustawieniami organizacji i eksportowanie raportów. Opis tych działań można znaleźć w sekcji "Akcje zarejestrowane w usłudze Stream" w [temacie Dzienniki inspekcji w Microsoft Stream](/stream/audit-logs#actions-logged-in-stream).

### <a name="content-explorer-activities"></a>Działania Eksploratora zawartości

W poniższej tabeli wymieniono działania w Eksploratorze zawartości, które są rejestrowane w dzienniku inspekcji. Eksplorator zawartości dostępny w narzędziu klasyfikacji danych w portalu zgodności. Aby uzyskać więcej informacji, zobacz [Korzystanie z eksploratora zawartości klasyfikacji danych](data-classification-content-explorer.md).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Element, do który uzyskano dostęp|LabelContentExplorerAccessedItem|Administrator (lub użytkownik należący do grupy ról Podgląd zawartości Eksploratora zawartości) używa Eksploratora zawartości do wyświetlania wiadomości e-mail lub SharePoint/OneDrive dokumentu.|

### <a name="quarantine-activities"></a>Działania kwarantanny

W poniższej tabeli wymieniono działania kwarantanny, które można wyszukać w dzienniku inspekcji. Aby uzyskać więcej informacji na temat kwarantanny, zobacz [Kwarantanna wiadomości e-mail](../security/office-365-security/quarantine-email-messages.md).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Usunięto komunikat kwarantanny|KwarantannaDelete|Użytkownik usunął wiadomość e-mail, która została uznana za szkodliwą.|
|Wyeksportowany komunikat kwarantanny|QuarantineExport|Użytkownik wyeksportował wiadomość e-mail, która została uznana za szkodliwą.|
|Podgląd komunikatu kwarantanny|KwarantannaPrzegląd|Użytkownik wyświetlił podgląd wiadomości e-mail, która została uznana za szkodliwą.|
|Komunikat dotyczący wydanej kwarantanny|QuarantineRelease|Użytkownik opublikował wiadomość e-mail z kwarantanny, która została uznana za szkodliwą.|
|Wyświetlony nagłówek komunikatu kwarantanny|QuarantineViewHeader|Użytkownik wyświetlił nagłówek wiadomości e-mail, która została uznana za szkodliwą.|

### <a name="microsoft-forms-activities"></a>działania Microsoft Forms

Tabele w tej sekcji dotyczące działań użytkownika i administratora w Microsoft Forms, które są rejestrowane w dzienniku inspekcji. Microsoft Forms jest narzędziem formularzy/testów/ankiet używanych do zbierania danych do analizy. W przypadku zanotowania poniżej w opisach niektóre operacje zawierają dodatkowe parametry działania.

Jeśli działanie formularzy jest wykonywane przez współautora lub anonimowego użytkownika odpowiadającego, zostanie ono zarejestrowane nieco inaczej. Aby uzyskać więcej informacji, zobacz sekcję [Forms activities performed by coauthors and anonymous responders (Działania formularzy wykonywane przez współautorów i osoby odpowiadające anonimowe](#forms-activities-performed-by-coauthors-and-anonymous-responders) ).

> [!NOTE]
> Niektóre działania inspekcji formularzy są dostępne tylko w obszarze Inspekcja (Premium). Oznacza to, że użytkownicy muszą mieć przypisaną odpowiednią licencję, zanim te działania zostaną zarejestrowane w dzienniku inspekcji. Aby uzyskać więcej informacji o działaniach dostępnych tylko w obszarze Inspekcja (Premium), zobacz [Audit (Premium) in Microsoft 365 (Inspekcja (Premium) w Microsoft 365](advanced-audit.md#audit-premium-events). Aby zapoznać się z wymaganiami dotyczącymi licencjonowania inspekcji (Premium), zobacz [Auditing solutions in Microsoft 365 (Rozwiązania inspekcji w Microsoft 365](auditing-solutions-overview.md#licensing-requirements)). <br/><br/>W poniższej tabeli działania inspekcji (Premium) są wyróżnione gwiazdką (*).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Utworzony komentarz|CreateComment|Właściciel formularza dodaje komentarz lub ocenę do quizu.|
|Utworzony formularz|CreateForm|Właściciel formularza tworzy nowy formularz. <br><br>Właściwość DataMode:string wskazuje, że bieżący formularz jest ustawiony na synchronizację z nowym lub istniejącym skoroszytem Excel, jeśli wartość właściwości jest równa DataSync. Właściwość ExcelWorkbookLink:string wskazuje skojarzony identyfikator skoroszytu Excel bieżącego formularza.|
|Edytowany formularz|EditForm|Właściciel formularza edytuje formularz, taki jak tworzenie, usuwanie lub edytowanie pytania. Właściwość *EditOperation:string* wskazuje nazwę operacji edycji. Możliwe operacje to:<br/>- CreateQuestion<br/>- CreateQuestionChoice <br/>- DeleteQuestion <br/>- DeleteQuestionChoice <br/>- DeleteFormImage <br/>- DeleteQuestionImage <br/>- UpdateQuestion <br/>- UpdateQuestionChoice <br/>— UploadFormImage/Bing/Onedrive <br/>— UploadQuestionImage <br/>- ChangeTheme <br><br>FormImage zawiera dowolne miejsce w formularzach, które użytkownik może przekazać obraz, na przykład w zapytaniu lub jako motyw w tle.|
|Formularz przeniesiony|MoveForm|Właściciel formularza przenosi formularz. <br><br>Właściwość DestinationUserId:string wskazuje identyfikator użytkownika osoby, która przeniosła formularz. Właściwość NewFormId:string to nowy identyfikator nowo skopiowanego formularza. Właściwość IsDelegateAccess:boolean wskazuje, że bieżąca akcja przenoszenia formularza jest wykonywana za pośrednictwem strony delegata administratora.|
|Usunięty formularz|DeleteForm|Właściciel formularza usuwa formularz. Obejmuje to softdelete (opcja usuwania używana i formularz przeniesiony do kosza) i HardDelete (Kosz jest opróżniany).|
|Wyświetlony formularz (czas projektowania)|ViewForm|Właściciel formularza otwiera istniejący formularz do edycji. <br><br>Właściwość AccessDenied:boolean wskazuje, że dostęp do bieżącego formularza został odrzucony z powodu sprawdzania uprawnień. Właściwość FromSummaryLink:boolean wskazuje, że bieżące żądanie pochodzi ze strony linku podsumowania.|
|Formularz w wersji zapoznawczej|Wersja zapoznawcza|Właściciel formularza wyświetla podgląd formularza przy użyciu funkcji Preview.|
|Wyeksportowany formularz|ExportForm|Właściciel formularza eksportuje wyniki do Excel. <br><br>Właściwość ExportFormat:string wskazuje, czy plik Excel to Pobierz, czy Online.|
|Formularz dozwolonego udziału do kopiowania|AllowShareFormForCopy|Właściciel formularza tworzy link szablonu do udostępniania formularza innym użytkownikom. To zdarzenie jest rejestrowane, gdy właściciel formularza kliknie, aby wygenerować adres URL szablonu.|
|Niedozwolony formularz udziału do kopiowania|DisallowShareFormForCopy|Właściciel formularza usuwa link szablonu.|
|Dodano współautora formularza|AddFormCoauthor|Użytkownik używa linku do współpracy, aby ułatwić projektowanie/wyświetlanie odpowiedzi. To zdarzenie jest rejestrowane, gdy użytkownik używa adresu URL kolabu (a nie po pierwszym wygenerowaniu adresu URL collab).|
|Usunięto współautora formularza|RemoveFormCoauthor|Właściciel formularza usuwa link do współpracy.|
|Wyświetlona strona odpowiedzi|ViewRuntimeForm|Użytkownik otworzył stronę odpowiedzi do wyświetlenia. To zdarzenie jest rejestrowane niezależnie od tego, czy użytkownik przesyła odpowiedź, czy nie.|
|Utworzona odpowiedź|CreateResponse|Podobnie jak w przypadku otrzymywania nowej odpowiedzi.  Użytkownik przesłał odpowiedź do formularza. <br><br>Właściwość ResponseId:string i Właściwość ResponderId:string wskazuje, który wynik jest wyświetlany. <br><br>W przypadku odpowiedzi anonimowej właściwość ResponderId będzie mieć wartość null.|
|Zaktualizowana odpowiedź|UpdateResponse|Właściciel formularza zaktualizował komentarz lub wynik testu. <br><br>Właściwość ResponseId:string i Właściwość ResponderId:string wskazuje, który wynik jest wyświetlany. <br><br>W przypadku odpowiedzi anonimowej właściwość ResponderId będzie mieć wartość null.|
|Usunięto wszystkie odpowiedzi|DeleteAllResponses|Właściciel formularza usuwa wszystkie dane odpowiedzi.|
|Usunięta odpowiedź|DeleteResponse|Właściciel formularza usuwa jedną odpowiedź. <br><br>Właściwość ResponseId:string wskazuje, że odpowiedź jest usuwana.|
|Wyświetlone odpowiedzi|ViewResponses|Właściciel formularza wyświetla zagregowaną listę odpowiedzi. <br><br>ViewType:string właściwości wskazuje, czy właściciel formularza wyświetla szczegóły, czy agreguje|
|Wyświetlona odpowiedź|ViewResponse|Właściciel formularza wyświetla określoną odpowiedź. <br><br>Właściwość ResponseId:string i Właściwość ResponderId:string wskazuje, który wynik jest wyświetlany. <br><br>W przypadku odpowiedzi anonimowej właściwość ResponderId będzie mieć wartość null.|
|Link do podsumowania utworzonego|GetSummaryLink|Właściciel formularza tworzy link do wyników podsumowania w celu udostępniania wyników.|
|Link do usuniętego podsumowania|DeleteSummaryLink|Właściciel formularza usuwa link wyników podsumowania.|
|Zaktualizowany stan wyłudzania informacji o formularzu|UpdatePhishingStatus|To zdarzenie jest rejestrowane za każdym razem, gdy została zmieniona szczegółowa wartość stanu zabezpieczeń wewnętrznych, niezależnie od tego, czy zmieniono ostateczny stan zabezpieczeń (na przykład formularz jest teraz zamknięty, czy otwarty). Oznacza to, że mogą zostać wyświetlone zduplikowane zdarzenia bez ostatecznej zmiany stanu zabezpieczeń. Możliwe wartości stanu dla tego zdarzenia to:<br/>- Zdjąć <br/>- Take Down by Administracja <br/>- odblokowane Administracja <br/>— Automatyczne blokowanie <br/>— Automatyczne odblokowywanie <br/>- Zgłoszone przez klienta <br/>- Resetowanie zgłoszonego klienta|
|Zaktualizowany stan wyłudzania informacji przez użytkownika|UpdateUserPhishingStatus|To zdarzenie jest rejestrowane za każdym razem, gdy wartość stanu zabezpieczeń użytkownika została zmieniona. Wartość stanu użytkownika w rekordzie inspekcji jest **potwierdzona jako Phisher** , gdy użytkownik utworzył formularz wyłudzania informacji, który został zdjęty przez zespół ds. bezpieczeństwa usługi Microsoft Online. Jeśli administrator odblokuje użytkownika, wartość stanu użytkownika jest ustawiona na **wartość Resetuj jako normalny użytkownik**.|
|Wysłane formularze Pro zaproszenia|ProInvitation|Użytkownik klika, aby aktywować Pro wersji próbnej.|
|Zaktualizowane ustawienie formularza<sup>*</sup> |UpdateFormSetting|Właściciel formularza aktualizuje jedno lub wiele ustawień formularza. <br><br>Właściwość FormSettingName:string wskazuje zaktualizowaną nazwę ustawień poufnych. Właściwość NewFormSettings:string wskazuje nazwę zaktualizowanych ustawień i nową wartość. Właściwość thankYouMessageContainsLink:boolean wskazuje zaktualizowany komunikat podziękowania zawiera link url.|
|Zaktualizowane ustawienie użytkownika|UpdateUserSetting|Właściciel formularza aktualizuje ustawienie użytkownika. <br><br>Właściwość UserSettingName:string wskazuje nazwę ustawienia i nową wartość|
|Formularze wymienione<sup>*</sup>|ListForms|Właściciel formularza wyświetla listę formularzy. <br><br>Właściwość ViewType:string wskazuje, na który widok patrzy właściciel formularza: Wszystkie formularze, Udostępnione mi lub Formularze grupy|
|Przesłana odpowiedź|SubmitResponse|Użytkownik przesyła odpowiedź do formularza. <br><br>Właściwość IsInternalForm:boolean wskazuje, czy osoba odpowiadająca znajduje się w tej samej organizacji co właściciel formularza.|
|Włączone ustawienie odpowiedzi dla każdej osoby<sup>*</sup>|AllowAnonymousResponse|Właściciel formularza włącza ustawienie umożliwiające dowolnemu użytkownikowi odpowiadanie na formularz.|
|Wyłączona osoba może odpowiedzieć na ustawienie<sup>*</sup>|DisallowAnonymousResponse|Właściciel formularza wyłącza ustawienie umożliwiające dowolnemu użytkownikowi odpowiadanie na formularz.|
|Włączone określone osoby mogą odpowiadać na ustawienie<sup>*</sup>|EnableSpecificResponse|Właściciel formularza włącza ustawienie zezwalające tylko określonym osobom lub określonym grupom w bieżącej organizacji na odpowiadanie na formularz.|
|Wyłączone określone osoby mogą odpowiadać na ustawienie<sup>*</sup>|DisableSpecificResponse|Właściciel formularza wyłącza ustawienie zezwalające tylko określonym osobom lub określonym grupom w bieżącej organizacji na odpowiadanie na formularz.|
|Dodano określoną odpowiedź<sup>*</sup>|AddSpecificResponder|Właściciel formularza dodaje nowego użytkownika lub grupę do listy określonych odpowiedzi.|
|Usunięto określoną odpowiedź<sup>*</sup>|RemoveSpecificResponder|Właściciel formularza usuwa użytkownika lub grupę z listy określonych odpowiedzi.|
|Wyłączona współpraca<sup>*</sup>|DisableCollaboration|Właściciel formularza wyłącza ustawienie współpracy w formularzu.|
|Włączono współpracę Office 365 kontem służbowym<sup>*</sup>|EnableWorkOrSchoolCollaboration|Właściciel formularza włącza ustawienie umożliwiające użytkownikom z kontem Microsoft 365 służbowym wyświetlanie i edytowanie formularza.|
|Włączone osoby we współpracy w mojej organizacji<sup>*</sup>|EnableSameOrgCollaboration|Właściciel formularza włącza ustawienie umożliwiające użytkownikom w bieżącej organizacji wyświetlanie i edytowanie formularza.|
|Włączono współpracę konkretnych osób<sup>*</sup>|EnableSpecificCollaboaration|Właściciel formularza włącza ustawienie zezwalające tylko określonym osobom lub określonym grupom w bieżącej organizacji na wyświetlanie i edytowanie formularza.|
|Połączony ze skoroszytem Excel<sup>*</sup>|ConnectToExcelWorkbook|Formularz został połączony ze skoroszytem Excel. <br><br>Właściwość ExcelWorkbookLink:string wskazuje skojarzony identyfikator skoroszytu Excel bieżącego formularza.|
|Tworzenie kolekcji|KolekcjaUtwórz|Właściciel formularza utworzył kolekcję.|
|Zaktualizowano kolekcję|CollectionUpdated|Właściciel formularza zaktualizował właściwość kolekcji.|
|Usunięto kolekcję z Kosza|CollectionHardDeleted|Właściciel formularza na stałe usunął kolekcję z Kosza.|
|Przeniesiono kolekcję do Kosza|CollectionSoftDeleted|Właściciel formularza przeniósł kolekcję do Kosza.|
|Zmieniono nazwę kolekcji|CollectionRenamed|Właściciel formularza zmienił nazwę kolekcji.|
|Przeniesiono formularz do kolekcji|MovedFormIntoCollection|Właściciel formularza przeniósł formularz do kolekcji.|
|Przeniesiono formularz z kolekcji|MovedFormOutofCollection|Właściciel formularza przeniósł formularz z kolekcji.|

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Formularze działań wykonywanych przez współautorów i osoby odpowiadające anonimowo

Formularze obsługują współpracę podczas projektowania formularzy i analizowania odpowiedzi. Współpracownik formularza jest znany jako *współautor*. Współautorzy mogą robić wszystko, co może zrobić właściciel formularza, z wyjątkiem usuwania lub przenoszenia formularza. Formularze umożliwiają również utworzenie formularza, na który można odpowiadać anonimowo. Oznacza to, że osoba odpowiadająca nie musi być zalogowana do organizacji, aby odpowiedzieć na formularz.

W poniższej tabeli opisano działania inspekcji i informacje w rekordzie inspekcji dotyczące działań wykonywanych przez współautorów i osoby odpowiadające anonimowo.

|Typ działania|Użytkownik wewnętrzny lub zewnętrzny|Zarejestrowany identyfikator użytkownika|Organizacja zalogowana do|Typ użytkownika formularzy|
|:-----|:-----|:-----|:-----|:-----|
|działania Współautorstwo|Wewnętrznego|UPN|Organizacja właściciela formularza|Współautor|
|działania Współautorstwo|Zewnętrznych|UPN<br>|Organizacja współautora<br>|Współautor|
|działania Współautorstwo|Zewnętrznych|`urn:forms:coauthor#a0b1c2d3@forms.office.com`<br>(Druga część identyfikatora to skrót, który będzie się różnić w przypadku różnych użytkowników)|Organizacja właściciela formularza<br>|Współautor|
|Działania odpowiedzi|Zewnętrznych|UPN<br>|Organizacja odpowiadającego<br>|Obiektu odpowiadającego|
|Działania odpowiedzi|Zewnętrznych|`urn:forms:external#a0b1c2d3@forms.office.com`<br>(Druga część identyfikatora użytkownika to skrót, który będzie się różnić w przypadku różnych użytkowników)|Organizacja właściciela formularza|Obiektu odpowiadającego|
|Działania odpowiedzi|Anonimowy|`urn:forms:anonymous#a0b1c2d3@forms.office.com`<br>(Druga część identyfikatora użytkownika to skrót, który będzie się różnić w przypadku różnych użytkowników)|Organizacja właściciela formularza|Obiektu odpowiadającego|

### <a name="sensitivity-label-activities"></a>Działania związane z etykietami poufności

W poniższej tabeli wymieniono zdarzenia wynikające z [używania etykiet poufności](sensitivity-labels.md).

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
|Zastosowana etykieta poufności do witryny|SensitivityLabelApplied|Etykieta poufności została zastosowana do witryny SharePoint lub Teams.|
|Usunięto etykietę poufności z witryny|SensitivityLabelRemoved|Etykieta poufności została usunięta z witryny SharePoint lub Teams.|
|Zastosowana etykieta poufności do pliku|FileSensitivityLabelApplied|Etykieta poufności została zastosowana do dokumentu przy użyciu aplikacji Microsoft 365, Office w sieci Web. lub zasady automatycznego etykietowania.|
|Zmieniono etykietę poufności stosowaną do pliku|FileSensitivityLabelChanged<br /><br>SensitivityLabelUpdated|Do dokumentu została zastosowana inna etykieta poufności. <br /><br>Operacje dla tego działania różnią się w zależności od sposobu zmiany etykiety:<br /> - Office w sieci Web lub zasady automatycznego etykietowania (FileSensitivityLabelChanged) <br /> — aplikacje Microsoft 365 (SensitivityLabelUpdated)|
|Zmieniono etykietę poufności w witrynie|SensitivityLabelChanged|Inna etykieta poufności została zastosowana do witryny SharePoint lub Teams.|
|Usunięto etykietę poufności z pliku|FileSensitivityLabelRemoved|Etykieta poufności została usunięta z dokumentu przy użyciu Microsoft 365 aplikacji, Office w sieci Web, zasad automatycznego etykietowania lub polecenia cmdlet [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile).|

### <a name="retention-policy-and-retention-label-activities"></a>Działania dotyczące zasad przechowywania i etykiet przechowywania

W poniższej tabeli opisano działania konfiguracji [zasad przechowywania i etykiet przechowywania](retention.md) podczas ich tworzenia, ponownego konfigurowania lub usuwania.

|Przyjazna nazwa|Operacja|Opis|
|:-----|:-----|:-----|
| Zmieniono członkostwo w zakresie adaptacyjnym |ApplicableAdaptiveScopeChange |Użytkownicy, witryny lub grupy zostały dodane do zakresu adaptacyjnego lub usunięte z tego zakresu. Te zmiany są wynikiem uruchomienia zapytania zakresu. Ponieważ zmiany są inicjowane przez system, zgłoszony użytkownik jest wyświetlany jako identyfikator GUID, a nie konto użytkownika.|
| Skonfigurowane ustawienia zasad przechowywania |NewRetentionComplianceRule |Administrator skonfigurował ustawienia przechowywania dla nowych zasad przechowywania. Ustawienia przechowywania obejmują czas przechowywania elementów oraz to, co dzieje się z elementami po upływie okresu przechowywania (na przykład usuwanie elementów, zachowywanie lub zachowywanie, a następnie ich usuwanie). To działanie odpowiada również uruchomieniu polecenia cmdlet [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) .|
| Utworzono zakres adaptacyjny |NewAdaptiveScope |Administrator utworzył zakres adaptacyjny.|
| Utworzona etykieta przechowywania |NewComplianceTag |Administrator utworzył nową etykietę przechowywania.|
| Utworzone zasady przechowywania |NewRetentionCompliancePolicy|Administrator utworzył nowe zasady przechowywania.|
| Usunięto zakres adaptacyjny | RemoveAdaptiveScope| Administrator usunął zakres adaptacyjny.|
| Usunięte ustawienia z zasad przechowywania| RemoveRetentionComplianceRule<br/>| Administrator usunął ustawienia konfiguracji zasad przechowywania. Najprawdopodobniej to działanie jest rejestrowane, gdy administrator usunie zasady przechowywania lub uruchomi polecenie cmdlet [Remove-RetentionComplianceRule](/powershell/module/exchange/Remove-RetentionComplianceRule) .|
| Usunięta etykieta przechowywania |RemoveComplianceTag | Administrator usunął etykietę przechowywania.|
| Usunięte zasady przechowywania |RemoveRetentionCompliancePolicy<br/> |Administrator usunął zasady przechowywania. |
| Włączono opcję rekordu regulacyjnego dla etykiet przechowywania<br/> |SetRestrictiveRetentionUI |Administrator uruchomił polecenie cmdlet [Set-RegulatoryComplianceUI](/powershell/module/exchange/set-regulatorycomplianceui) , aby administrator mógł wybrać opcję konfiguracji interfejsu użytkownika dla etykiety przechowywania, aby oznaczyć zawartość jako rekord regulacyjny.|
| Zaktualizowany zakres adaptacyjny | SetAdaptiveScope | Administrator zmienił opis lub zapytanie dotyczące istniejącego zakresu adaptacyjnego. |
| Zaktualizowano ustawienia zasad przechowywania | SetRetentionComplianceRule | Administrator zmienił ustawienia przechowywania istniejących zasad przechowywania. Ustawienia przechowywania obejmują czas przechowywania elementów oraz to, co dzieje się z elementami po upływie okresu przechowywania (na przykład usuwanie elementów, zachowywanie lub zachowywanie, a następnie ich usuwanie). To działanie odpowiada również uruchamianiu polecenia cmdlet [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) . |
| Zaktualizowana etykieta przechowywania |SetComplianceTag  | Administrator zaktualizował istniejącą etykietę przechowywania.|
| Zaktualizowane zasady przechowywania |SetRetentionCompliancePolicy |Administrator zaktualizował istniejące zasady przechowywania. Aktualizacje wyzwalające to zdarzenie obejmują dodawanie lub wykluczanie lokalizacji zawartości, do których są stosowane zasady przechowywania.|

### <a name="briefing-email-activities"></a>Działania dotyczące wiadomości e-mail z briefingu

W poniższej tabeli wymieniono działania w wiadomości e-mail z informacją, które są rejestrowane w dzienniku inspekcji Microsoft 365. Aby uzyskać więcej informacji na temat wiadomości e-mail z informacjami o briefingu, zobacz:

- [Omówienie wiadomości e-mail z briefingu](/Briefing/be-overview)

- [Konfigurowanie wiadomości e-mail z briefingu](/Briefing/be-admin)

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:----|:-----|:-----|
|Zaktualizowane ustawienia prywatności organizacji|UpdatedOrganizationBriefingSettings|Administracja aktualizuje ustawienia prywatności organizacji dla wiadomości e-mail z briefingiem. |
|Zaktualizowane ustawienia prywatności użytkowników|UpdatedUserBriefingSettings|Administracja aktualizuje ustawienia prywatności użytkownika dla wiadomości e-mail z briefingiem.

### <a name="myanalytics-activities"></a>Działania myAnalytics

W poniższej tabeli wymieniono działania w usłudze MyAnalytics, które są rejestrowane w dzienniku inspekcji Microsoft 365. Aby uzyskać więcej informacji na temat usługi MyAnalytics, zobacz [MyAnalytics for admins (MyAnalytics for admins](/workplace-analytics/myanalytics/overview/mya-for-admins)).

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|Zaktualizowano ustawienia myanalytics organizacji|UpdatedOrganizationMyAnalyticsSettings|Administracja aktualizuje ustawienia na poziomie organizacji dla usługi MyAnalytics. |
|Zaktualizowano ustawienia myanalytics użytkownika|UpdatedUserMyAnalyticsSettings|Administracja aktualizuje ustawienia użytkownika dla usługi MyAnalytics.|

### <a name="information-barriers-activities"></a>Działania związane z barierami informacyjnymi

W poniższej tabeli wymieniono działania w barierach informacyjnych, które są rejestrowane w dzienniku inspekcji Microsoft 365. Aby uzyskać więcej informacji na temat barier informacyjnych, zobacz [Dowiedz się więcej o barierach informacyjnych w Microsoft 365](information-barriers.md).

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:----------------|:------------|:--------------|
| Dodano segmenty do witryny | SegmentyAdded | Administrator SharePoint, administrator globalny lub właściciel witryny dodał co najmniej jeden segment barier informacyjnych do witryny. |
| Zmieniono segmenty witryny | SegmentsChanged | Administrator SharePoint lub administrator globalny zmienił co najmniej jeden segment barier informacyjnych dla witryny. |
| Usunięto segmenty z witryny | SegmentyRemoved | Administrator SharePoint lub administrator globalny usunął co najmniej jeden segment barier informacyjnych z witryny. |

### <a name="disposition-review-activities"></a>Działania przeglądu dyspozycji

W poniższej tabeli wymieniono działania wykonywane przez recenzenta dyspozycji, gdy element osiągnął koniec skonfigurowanego okresu przechowywania. Aby uzyskać więcej informacji, zobacz [Wyświetlanie i usuwanie zawartości](disposition.md#viewing-and-disposing-of-content).

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|Zatwierdzona utylizacja|ApproveDisposal|Recenzent dyspozycji zatwierdził dyspozycję elementu w celu przeniesienia go do następnego etapu dyspozycji. Jeśli element znajdował się w jedynym lub ostatnim etapie przeglądu dyspozycji, zatwierdzenie rozporządzania oznaczyło element jako kwalifikujący się do trwałego usunięcia.|
|Dłuższy okres przechowywania|ExtendRetention|Recenzent dyspozycji przedłużył okres przechowywania elementu.|
|Ponownie oznakowany element|RelabelItem|Recenzent dyspozycji ponownie oznaczył etykietę przechowywania.|
|Dodano recenzentów|AddReviewer|Recenzent dyspozycji dodał co najmniej jednego innego użytkownika do bieżącego etapu przeglądu dyspozycji.|

### <a name="communication-compliance-activities"></a>Działania dotyczące zgodności komunikacji

Poniższa tabela zawiera listę działań zgodności komunikacji, które są rejestrowane w dzienniku inspekcji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o zgodności komunikacji w Microsoft 365](communication-compliance.md).

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|Aktualizacja zasad|SupervisionPolicyCreated, SupervisionPolicyUpdated, SupervisionPolicyDeleted|Administrator zgodności komunikacji przeprowadził aktualizację zasad.|
|Dopasowanie zasad|NadzórRuleMatch|Użytkownik wysłał komunikat zgodny z warunkiem zasad.|
|Tag zastosowany do komunikatów|SupervisoryReviewTag|Tagi są stosowane do komunikatów lub komunikatów są rozwiązywane.|

### <a name="report-activities"></a>Działania raportu

W poniższej tabeli wymieniono działania dotyczące raportów użycia, które są rejestrowane w dzienniku inspekcji Microsoft 365.

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|Zaktualizowane ustawienia prywatności raportu użycia|UpdateUsageReportsPrivacySetting|Administracja zaktualizowane ustawienia prywatności dla raportów użycia. |

### <a name="exchange-admin-audit-log"></a>dziennik inspekcji administratora Exchange

Exchange rejestrowanie inspekcji administratora (domyślnie włączone w Microsoft 365) rejestruje zdarzenie w dzienniku inspekcji, gdy administrator (lub użytkownik, któremu przypisano uprawnienia administracyjne) wprowadza zmianę w organizacji Exchange Online. Zmiany wprowadzone przy użyciu centrum administracyjnego Exchange lub przez uruchomienie polecenia cmdlet w programie Exchange Online programu PowerShell są rejestrowane w dzienniku inspekcji administratora Exchange. Polecenia cmdlet rozpoczynające się czasownikami **Get-**, **Search-lub** **Test nie** są rejestrowane w dzienniku inspekcji. Aby uzyskać bardziej szczegółowe informacje na temat rejestrowania inspekcji administratora w Exchange, zobacz [Rejestrowanie inspekcji administratora](/exchange/administrator-audit-logging-exchange-2013-help).

> [!IMPORTANT]
> Niektóre Exchange Online poleceń cmdlet, które nie są rejestrowane w dzienniku inspekcji Exchange administratora (lub w dzienniku inspekcji). Wiele z tych poleceń cmdlet jest związanych z utrzymaniem usługi Exchange Online i jest uruchamianych przez personel centrum danych firmy Microsoft lub konta usług. Te polecenia cmdlet nie są rejestrowane, ponieważ powodują dużą liczbę "hałaśliwych" zdarzeń inspekcji. Jeśli istnieje polecenie cmdlet Exchange Online, które nie jest poddawane inspekcji, prześlij żądanie zmiany projektu (DCR) do pomoc techniczna firmy Microsoft.

Poniżej przedstawiono kilka wskazówek dotyczących wyszukiwania działań administratora Exchange podczas przeszukiwania dziennika inspekcji:

- Aby zwrócić wpisy z dziennika inspekcji Exchange administratora, musisz wybrać pozycję **Pokaż wyniki dla wszystkich działań na** liście **Działania**. Użyj pól zakresu dat i listy **Użytkownicy**, aby zawęzić wyniki wyszukiwania poleceń cmdlet uruchamianych przez określonego administratora Exchange w określonym zakresie dat.

- Aby wyświetlić zdarzenia z dziennika inspekcji Exchange administratora, kliknij kolumnę **Działanie**, aby posortować nazwy poleceń cmdlet w kolejności alfabetycznej.

- Aby uzyskać informacje o tym, jakie polecenie cmdlet zostało uruchomione, które parametry i wartości parametrów zostały użyte oraz jakie obiekty zostały naruszone, możesz wyeksportować wyniki wyszukiwania, wybierając opcję **Pobierz wszystkie wyniki** . Aby uzyskać więcej informacji, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

- Możesz również użyć `Search-UnifiedAuditLog -RecordType ExchangeAdmin` polecenia w programie Exchange Online programu PowerShell, aby zwrócić tylko rekordy inspekcji z dziennika inspekcji Exchange administratora. Może upłynąć do 30 minut po uruchomieniu polecenia cmdlet Exchange, aby odpowiedni wpis dziennika inspekcji został zwrócony w wynikach wyszukiwania. Aby uzyskać więcej informacji, zobacz [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog). Aby uzyskać informacje na temat eksportowania wyników wyszukiwania zwróconych przez polecenie cmdlet **Search-UnifiedAuditLog** do pliku CSV, zobacz sekcję "Wskazówki eksportowania i wyświetlania dziennika inspekcji" w temacie [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Zdarzenia można również wyświetlać w dzienniku inspekcji administratora Exchange przy użyciu centrum administracyjnego Exchange lub uruchamiając dziennik **Search-AdminAuditLog** w programie Exchange Online programu PowerShell. Jest to dobry sposób na wyszukiwanie działań wykonywanych przez administratorów Exchange Online. Aby uzyskać instrukcje, zobacz:

  - [Wyświetlanie dziennika inspekcji administratora](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)

  - [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog)

   Należy pamiętać, że te same działania administratora Exchange są rejestrowane zarówno w dzienniku inspekcji Exchange administratora, jak i w dzienniku inspekcji.

### <a name="encrypted-message-portal-activities"></a>Działania zaszyfrowanego portalu wiadomości

Dzienniki dostępu są dostępne dla zaszyfrowanych komunikatów za pośrednictwem zaszyfrowanego portalu wiadomości, który pozwala organizacji określić, kiedy wiadomości są odczytywane i przekazywane dalej przez adresatów zewnętrznych. Aby uzyskać więcej informacji na temat włączania i używania zaszyfrowanych dzienników aktywności portalu komunikatów, zobacz [Encrypted message portal activity log (Dziennik aktywności zaszyfrowanego portalu wiadomości](ome-message-access-logs.md)).

Każdy wpis inspekcji dla śledzonego komunikatu będzie zawierać następujące pola:

- MessageID — zawiera identyfikator śledzonego komunikatu. Jest to identyfikator klucza używany do śledzenia komunikatu za pośrednictwem systemu.
- Adresat — lista wszystkich adresów e-mail adresatów.
- Nadawca — źródłowy adres e-mail.
- AuthenticationMethod — opisuje metodę uwierzytelniania na potrzeby uzyskiwania dostępu do komunikatu, na przykład OTP, Yahoo, Gmail lub Microsoft.
- AuthenticationStatus — zawiera wartość wskazującą, że uwierzytelnianie zakończyło się pomyślnie lub zakończyło się niepowodzeniem.
- OperationStatus — wskazuje, czy wskazana operacja zakończyła się powodzeniem, czy niepowodzeniem.
- AttachmentName — nazwa załącznika.
- OperationProperties — lista opcjonalnych właściwości, na przykład liczba wysłanych kodów dostępu OTP lub temat wiadomości e-mail.

### <a name="systemsync-activities"></a>Działania narzędzia SystemSync

W poniższej tabeli wymieniono działania programu SystemSync, które są rejestrowane w dzienniku inspekcji Microsoft 365.

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|utworzono Data Share|DataShareCreated|Po utworzeniu eksportu danych przez użytkownika.|
|Data Share usunięto|DataShareDeleted|Gdy eksport danych zostanie usunięty przez użytkownika.|
|Generowanie kopii danych usługi Lake|GenerateCopyOfLakeData|Po wygenerowaniu kopii danych usługi Lake Data.|
|Pobieranie kopii danych usługi Lake|DownloadCopyOfLakeData|Po pobraniu kopii usługi Lake Data.|


## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Czym różnią się usługi Microsoft 365, które są obecnie poddawane inspekcji?**

Najczęściej używane usługi, takie jak Exchange Online, SharePoint Online, OneDrive dla Firm, Azure Active Directory, Microsoft Teams, Dynamics 365, Ochrona usługi Office 365 w usłudze Defender i Power BI są poddawane inspekcji. Zobacz [początek tego artykułu](search-the-audit-log-in-security-and-compliance.md) , aby uzyskać listę usług, które są poddawane inspekcji.

**Jakie działania są poddawane inspekcji przez usługę inspekcji w Microsoft 365?**

Zobacz sekcję [Inspekcja działań](#audited-activities) w tym artykule, aby zapoznać się z listą i opisem działań, które są poddawane inspekcji.

**Jak długo trwa udostępnienie rekordu inspekcji po wystąpieniu zdarzenia?**

Większość danych inspekcji jest dostępna w ciągu 30 minut, ale wyświetlenie odpowiedniego wpisu dziennika inspekcji w wynikach wyszukiwania może potrwać do 24 godzin. Zobacz tabelę w sekcji [Przed przeszukaniem dziennika inspekcji](#before-you-search-the-audit-log) w tym artykule, która pokazuje czas potrzebny na udostępnienie zdarzeń w różnych usługach.

**Jak długo są przechowywane rekordy inspekcji?**

Jak wyjaśniono wcześniej, rekordy inspekcji działań wykonywanych przez użytkowników z przypisaną licencją Office 365 E5 lub Microsoft E5 (lub użytkowników z licencją dodatku Microsoft 365 E5) są przechowywane przez jeden rok. W przypadku wszystkich innych subskrypcji obsługujących ujednolicone rejestrowanie inspekcji rekordy inspekcji są przechowywane przez 90 dni.

**Czy mogę programowo uzyskiwać dostęp do danych inspekcji?**

Tak. Interfejs API działania zarządzania Office 365 służy do programowego pobierania dzienników inspekcji.  Aby rozpocząć, zobacz [Wprowadzenie z interfejsami API zarządzania Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

**Czy istnieją inne sposoby uzyskiwania dzienników inspekcji innych niż korzystanie z portalu zabezpieczeń i zgodności lub interfejsu API działania zarządzania Office 365?**

Tak, dzienniki inspekcji można pobrać przy użyciu następujących metod:

- [Interfejs API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

- [Narzędzie do wyszukiwania dzienników inspekcji](search-the-audit-log-in-security-and-compliance.md) w portal zgodności Microsoft Purview.

- Polecenie cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online programu PowerShell.

**Czy muszę indywidualnie włączyć inspekcję w każdej usłudze, dla której chcę przechwycić dzienniki inspekcji?**

W większości usług inspekcja jest domyślnie włączona po początkowym włączeniu inspekcji dla organizacji (zgodnie z [opisem w sekcji Przed przeszukaniem dziennika inspekcji](#before-you-search-the-audit-log) w tym artykule).

**Czy usługa inspekcji obsługuje cofanie duplikowania rekordów?**

Nie. Potok usługi inspekcji znajduje się niemal w czasie rzeczywistym i w związku z tym nie może obsługiwać cofania duplikowania.

**Gdzie są przechowywane dane inspekcji?**

Obecnie przeprowadzamy inspekcję wdrożeń potoków w regionach NA (Ameryka Północna), EMEA (Europa, Bliski Wschód i Afryka) oraz APAC (Azja i Pacyfik). Dzierżawy znajdujące się w tych regionach będą przechowywać dane inspekcji w regionie. W przypadku dzierżaw z wieloma lokalizacjami geograficznymi dane inspekcji zebrane ze wszystkich regionów dzierżawy będą przechowywane tylko w regionie macierzystym dzierżawy. Możemy jednak przesyłać dane między tymi regionami w celu równoważenia obciążenia i tylko podczas problemów z lokacją na żywo. Gdy wykonujemy te działania, przesyłane dane są szyfrowane. 

**Czy inspekcja danych jest szyfrowana?**

Dane inspekcji są przechowywane w Exchange skrzynkach pocztowych (danych magazynowanych) w tym samym regionie, w którym wdrożono ujednolicony potok inspekcji. Dane skrzynki pocztowej magazynowane nie są szyfrowane przez Exchange. Jednak szyfrowanie na poziomie usługi szyfruje wszystkie dane skrzynki pocztowej, ponieważ serwery Exchange w centrach danych firmy Microsoft są szyfrowane za pośrednictwem BitLocker. Aby uzyskać więcej informacji, zobacz [szyfrowanie Microsoft 365 dla Skype dla firm, OneDrive dla Firm, SharePoint Online i Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services).

Przesyłane dane poczty są zawsze szyfrowane.
