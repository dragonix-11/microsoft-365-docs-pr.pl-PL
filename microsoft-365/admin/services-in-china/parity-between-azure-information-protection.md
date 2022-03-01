---
title: Obsługa usługi Azure Information Protection Office 365 obsługiwanej przez firmę 21Vianet
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEU150
- GEA150
description: Dowiedz się więcej o usłudze Azure Information Protection (AIP) dla usługi Office 365 obsługiwanej przez firmę 21Vianet i jak skonfigurować ją dla klientów w Chinach.
monikerRange: o365-21vianet
ms.openlocfilehash: 44681286bce5e16a08f7400a2dbb083288a6f3b7
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009815"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>Obsługa usługi Azure Information Protection Office 365 obsługiwanej przez firmę 21Vianet

W tym artykule opisano różnice między obsługą usługi Azure Information Protection (AIP) dla usługi Office 365 obsługiwanej przez firmę 21Vianet i oferty komercyjne, a także szczegółowe instrukcje dotyczące konfigurowania programu AIP&mdash; dla klientów w Chinach, w tym instrukcje dotyczące instalowania lokalnego skanera programu AIP i zarządzania zadaniami skanowania zawartości.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Różnice między usługą AIP dla Office 365 obsługiwanej przez firmę 21Vianet a ofertą komercyjną

Chociaż naszym celem jest dostarczenie wszystkich komercyjnych funkcji klientom w Chinach za pomocą programu AIP dla usługi Office 365 obsługiwanej przez firmę 21Vianet, brakuje niektórych funkcji, które chcemy wyróżnić.

Na poniższej liście przedstawiono istniejące odstępy między usługą AIP dla usług Office 365 obsługiwanej przez firmę 21Vianet a naszymi ofertami komercyjnymi od stycznia 2021 r.:

- Usługi Active Directory Rights Management (AD RMS) jest obsługiwane tylko w Aplikacje Microsoft 365 dla przedsiębiorstw (kompilacja 11731.10000 lub nowszy). Office Professional Plus nie obsługuje usług AD RMS.

- Migracja z usług AD RMS do usługi AIP nie jest obecnie dostępna.
  
- Obsługiwane jest udostępnianie chronionych wiadomości e-mail użytkownikom w chmurze komercyjnej.
  
- Udostępnianie dokumentów i załączników wiadomości e-mail użytkownikom w komercyjnej chmurze nie jest obecnie dostępne. Dotyczy Office 365 usług firmy Office 365 obsługiwanych przez użytkowników 21Vianet w chmurze komercyjnej , usług innych niż Office 365 obsługiwanych przez użytkowników 21Vianet w chmurze komercyjnej oraz użytkowników z licencją RMS dla użytkowników indywidualnych.
  
- Usługi IRM SharePoint (biblioteki i witryny chronione za pomocą usługi IRM) nie są obecnie dostępne.
  
- Rozszerzenie urządzenia przenośnego dla usług AD RMS nie jest obecnie dostępne.

- Usługa [Mobile Viewer](/azure/information-protection/rms-client/mobile-app-faq) nie jest obsługiwana przez usługę Azure China 21Vianet.

- Obszar AIP portalu Azure portal jest niedostępny dla klientów w Chinach. Zamiast [wykonywać w portalu](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) akcje, takie jak zarządzanie zadaniami skanowania zawartości i uruchamianie ich, użyj poleceń programu PowerShell.

- Punkty końcowe usługi AIP Office 365 obsługiwane przez firmę 21Vianet różnią się od punktów końcowych wymaganych dla innych usług w chmurze. Wymagana jest łączność sieciowa z klientami do następujących punktów końcowych:
    - Pobierz zasady dotyczące etykiet i etykiet: `*.protection.partner.outlook.cn`
    - Usługa Azure Rights Management: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Konfigurowanie usługi AIP dla klientów w Chinach

Aby skonfigurować program AIP dla klientów w Chinach:
1. [Włącz zarządzanie prawami dla dzierżawy](#step-1-enable-rights-management-for-the-tenant).

1. [Dodaj podmiot Microsoft Information Protection usługi synchronizacji](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [Skonfiguruj szyfrowanie DNS](#step-3-configure-dns-encryption).

1. [Zainstaluj i skonfiguruj klienta ujednoliconego etykiet programu AIP](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Skonfiguruj aplikacje AIP na Windows](#step-5-configure-aip-apps-on-windows).

1. [Zainstaluj skaner lokalnym programu AIP i zarządzaj zadaniami skanowania zawartości](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>Krok 1. Włączanie zarządzania prawami dla dzierżawy

Aby szyfrowanie działało poprawnie, dla dzierżawy musi być włączona funkcja RMS.

1. Sprawdź, czy jest włączone usługi RMS:

    1. Uruchom program PowerShell jako administrator.
    2. Jeśli moduł AIPService nie jest zainstalowany, uruchom program `Install-Module AipService`.
    3. Zaimportuj moduł za pomocą `Import-Module AipService`.
    4. Połączenie się z usługą za pomocą .`Connect-AipService -environmentname azurechinacloud`
    5. Uruchom `(Get-AipServiceConfiguration).FunctionalState` i sprawdź, czy stan to `Enabled`.

2. Jeśli stan funkcjonalny to `Disabled`, uruchom `Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>Krok 2. Dodawanie podmiotu zabezpieczeń Microsoft Information Protection usługi synchronizacji

Podmiot **Microsoft Information Protection usługi synchronizacji** nie jest domyślnie dostępny w dzierżawach platformy Azure w Chinach i jest wymagany dla usługi Azure Information Protection. Utwórz ten podmiot zabezpieczeń usługi ręcznie za pośrednictwem modułu Azure Az PowerShell.

1. Jeśli nie masz zainstalowanego modułu Azure Az, zainstaluj go lub użyj zasobu, w którym jest preinstalowany moduł Azure Az, na przykład powłoki [platformy Azure Cloud Shell](/azure/cloud-shell/overview). Aby uzyskać więcej informacji, [zobacz Instalowanie modułu Azure Az PowerShell](/powershell/azure/install-az-ps).

1. Połączenie do usługi przy użyciu [polecenia cmdlet](/powershell/module/az.accounts/Connect-AzAccount) `azurechinacloud` Połączenie-AzAccount i nazwy środowiska:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. Utwórz ręcznie **Microsoft Information Protection usługi** synchronizacji, używając polecenia cmdlet `870c4f2e-85b6-4d43-bdda-6ed9a579b725` [New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) i identyfikatora aplikacji dla usługi Microsoft Information Protection Synchronizacji:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Po dodaniu podmiotu zabezpieczeń usługi dodaj odpowiednie uprawnienia wymagane do usługi.

### <a name="step-3-configure-dns-encryption"></a>Krok 3. Konfigurowanie szyfrowania DNS

Aby szyfrowanie działało poprawnie, Office muszą połączyć się z wystąpieniem usługi w Chinach i bootstrap z tego wystąpienia. Aby przekierować aplikacje klienckie do odpowiedniego wystąpienia usługi, administrator dzierżawy musi skonfigurować rekord DNS SRV z informacjami o adresie URL usługi Azure RMS. Bez rekordu DNS SRV aplikacja kliencza domyślnie podejmie próbę nawiązania połączenia z wystąpieniem chmury publicznej i nie powiedzie się.

Ponadto zakłada się, że użytkownicy logują się przy użyciu nazwy użytkownika w oparciu o domenę należącą do dzierżawy ( `joe@contoso.cn`na przykład ) `onmschina` a nie za pomocą nazwy użytkownika (na przykład `joe@contoso.onmschina.cn`). Nazwa domeny z nazwy użytkownika jest używana do przekierowywania dns do odpowiedniego wystąpienia usługi.

#### <a name="configure-dns-encryption---windows"></a>Konfigurowanie szyfrowania DNS — Windows

1. Uzyskaj identyfikator RMS:

    1. Uruchom program PowerShell jako administrator.
    2. Jeśli moduł AIPService nie jest zainstalowany, uruchom program `Install-Module AipService`.
    3. Połączenie się z usługą za pomocą .`Connect-AipService -environmentname azurechinacloud`
    4. Uruchom, `(Get-AipServiceConfiguration).RightsManagementServiceId` aby uzyskać identyfikator RMS.

2. Zaloguj się do swojego dostawcy hostingu DNS, przejdź do ustawień DNS domeny, a następnie dodaj nowy rekord SRV.

    - Service = (Usługa = ) `_rmsredir`
    - Protocol = (Protokół) = `_http`
    - Nazwa = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (gdzie identyfikator GUID to identyfikator RMS)
    - Priority (Priorytet), Weight (Waga), Seconds(Sekundy), TTL (Czas wygaśnięcia) = wartości domyślne

3. Skojarz domenę niestandardową z dzierżawą w [portalu Azure Portal](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Spowoduje to dodanie wpisu w systemie DNS, co może potrwać kilka minut na weryfikację po dodaniu wartości do ustawień DNS.

4. Zaloguj się do centrum administracyjne platformy Microsoft 365 przy użyciu odpowiednich poświadczeń administratora globalnego i dodaj domenę (`contoso.cn`na przykład) do utworzenia użytkowników. W procesie weryfikacji mogą być wymagane dodatkowe zmiany w systemie DNS. Po zakończeniu weryfikacji można utworzyć użytkowników.

#### <a name="configure-dns-encryption---mac-ios-android"></a>Konfigurowanie szyfrowania DNS na komputerach Mac, urządzeniach z systemem iOS i Android

Zaloguj się do swojego dostawcy hostingu DNS, przejdź do ustawień DNS domeny, a następnie dodaj nowy rekord SRV.

- Service = (Usługa = ) `_rmsdisco`
- Protocol = (Protokół) = `_http`
- Nazwa = `_tcp`
- Target = (Wartość docelowa) `api.aadrm.cn`
- Port = `80`
- Priority (Priorytet), Weight (Waga), Seconds(Sekundy), TTL (Czas wygaśnięcia) = wartości domyślne


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>Krok 4. Instalowanie i konfigurowanie klienta ujednoliconego etykiet programu AIP

Pobierz i zainstaluj klienta ujednoliconego etykiet AIP z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

Więcej informacji można znaleźć w następujących artykułach:

- [Dokumentacja AIP](/azure/information-protection/)
- [Historia wersji i zasady pomocy technicznej dotyczące programu AIP](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Wymagania systemowe programu AIP](/azure/information-protection/requirements)
- [Szybki start w programie AIP: wdrażanie klienta AIP](/azure/information-protection/quickstart-deploy-client)
- [Przewodnik administratora programu AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [Podręcznik użytkownika programu AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [Dowiedz się więcej Microsoft 365 etykiet wrażliwości](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>Krok 5. Konfigurowanie aplikacji AIP na Windows

Aplikacje AIP na Windows muszą mieć następujący klucz rejestru, aby wskazać prawidłową suwerenną chmurę dla platformy Azure w Chinach:

- Węzeł rejestru = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Nazwa = `CloudEnvType`
- Wartość = `6` (domyślnie = 0)
- Wpisz = `REG_DWORD`

> [!IMPORTANT]
> Upewnij się, że klucz rejestru nie został usunięty po odinstalowaniu. Jeśli klucz jest pusty, niepoprawny lub nie istnieje, funkcja będzie działać jako wartość domyślna (wartość domyślna = 0 w przypadku chmury komercyjnej). Jeśli klucz jest pusty lub niepoprawny, do dziennika jest również dodawany błąd wydruku.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>Krok 6. Instalowanie lokalnego skanera programu AIP i zarządzanie zadaniami skanowania zawartości

Zainstaluj skaner lokalnym programu AIP, aby przeskanować sieć i udziały zawartości w poszukiwaniu poufnych danych i zastosować etykiety klasyfikacji i ochrony skonfigurowane w zasadach organizacji.

Podczas konfigurowania zadań skanowania zawartości i zarządzania nimi skorzystaj z poniższej procedury zamiast interfejsu [portalu Azure Portal](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) używanego w ofertach komercyjnych.

Aby uzyskać więcej informacji, zobacz Co to jest ujednolicony skaner etykiet usługi [Azure Information Protection?](/azure/information-protection/deploy-aip-scanner) i Zarządzanie zadaniami skanowania zawartości tylko [za pomocą programu PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**Aby zainstalować i skonfigurować skaner**:

1. Zaloguj się do komputera Windows Server, na którym zostanie uruchomiony skaner. Użyj konta, które ma prawa administratora lokalnego i które ma uprawnienia do zapisu w SQL Server głównej bazy danych.

1. Zacznij od zamknięcia programu PowerShell. Jeśli wcześniej zainstalowano klienta i skaner AIP, upewnij się, że usługa **AIPScanner** została zatrzymana.

1. Otwórz sesję Windows PowerShell za pomocą **opcji Uruchom jako administrator**.

1. Uruchom polecenie cmdlet [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner), określając wystąpienie programu SQL Server, w którym chcesz utworzyć bazę danych dla skanera usługi Azure Information Protection, oraz opisową nazwę twojego skanera.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Możesz użyć tej samej nazwy klastrów w [poleceniu Install-AIPKanner](/powershell/module/azureinformationprotection/install-aipscanner) , aby skojarzyć wiele węzłów skanera z tym samym klastrem. Korzystanie z tego samego klastru dla wielu węzłów skanera umożliwia współpracę wielu skanerów podczas skanowania.
    > 

1. Sprawdź, czy usługa jest teraz zainstalowana za pomocą **narzędzi administracyjnychServices** > .

    Zainstalowana usługa nosi nazwę **Azure Information Protection Scanner** i jest skonfigurowana do uruchamiania przy użyciu utworzonego konta usługi skanera.

1. Uzyskaj token Azure do użycia ze swoim skanerem. Token usługi Azure AD umożliwia skanerowi uwierzytelnienie się w usłudze Azure Information Protection, co umożliwia uruchamianie skanera w sposób nieinterakcyjny. 

    1. Otwórz Portal Azure i utwórz aplikację usługi Azure AD, aby określić token dostępu do uwierzytelniania. Aby uzyskać więcej informacji, zobacz Jak oznaczać pliki w sposób interakcyjny [dla usługi Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > Podczas tworzenia i konfigurowania aplikacji Usługi Azure AD dla polecenia [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) w okienku Żądanie uprawnień interfejsów API  jest pokazana karta Interfejsy **API** używane przez moją organizację zamiast karty **Interfejsy API firmy Microsoft**. Wybierz **interfejsy API, z których korzysta moja organizacja**, a następnie wybierz pozycję **Usługi Azure Rights Management**. 
        >

    1. Jeśli na Windows Server Twoje konto usługi skanera otrzymało konto usługi logowania lokalnego bezpośrednio do  instalacji, zaloguj się przy użyciu tego konta i uruchom sesję programu PowerShell. 
    
        Jeśli twoje konto usługi skanera nie może zostać  przyznane w celu obsługi logowania lokalnego bezpośrednio do instalacji, użyj parametru *W* imieniu z ustawieniem [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), zgodnie z opisem w tece Jak oznaczać pliki bez interakcyjnego oznaczania plików dla usługi [Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

    1. Uruchom [uwierzytelnianie Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), określając wartości skopiowane z aplikacji usługi Azure AD:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Przykład:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Skaner ma teraz token do uwierzytelnienia w usłudze Azure AD. Ten token jest ważny przez rok, dwa lata lub nigdy, zgodnie z konfiguracją klienta aplikacji sieci **Web /interfejsu API** tajnego w usłudze Azure AD. Po wygaśnięciu tokenu musisz powtórzyć tę procedurę.

1. Uruchom [polecenie cmdlet Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) , aby ustawić skaner do działania w trybie offline. Uruchamianie:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Uruchom [polecenie cmdlet Set-AIPScantentContentKanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) , aby utworzyć domyślne zadanie skanowania zawartości.

    Jedynym parametrem wymaganym w poleceniach cmdlet **Set-AIPScantentContentKanJob** jest **polecenie Enforce**. W tym momencie możesz jednak zdefiniować inne ustawienia zadania skanowania zawartości. Przykład:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    W trakcie kontynuowania konfiguracji składnia w powyższej składni jest konfigurowana zgodnie z następującymi ustawieniami:

    - Ręczne planowanie dla *skanera*
    - Ustawia typy informacji, które mają zostać odnalezione, na podstawie zasad wrażliwości
    - Zasady *wrażliwości* nie są wymuszane
    - Automatyczne oznaczanie plików na podstawie zawartości przy użyciu etykiety domyślnej zdefiniowanej dla zasad wrażliwości
    - Nie *umożliwia* ponownego na etykietowania plików
    - Zachowuje szczegóły pliku podczas skanowania i automatycznego oznaczania, w tym *daty modyfikacji*, ostatniej *modyfikacji* *i modyfikacji przez* wartości.
    - Ustawia skaner tak, aby wykluczał pliki msg i tmp podczas uruchamiania
    - Ustawia domyślne konto właściciela, którego chcesz używać podczas uruchamiania skanera.

1. Użyj polecenia [cmdlet Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) , aby zdefiniować repozytoria, które chcesz przeskanować w zadaniu skanowania zawartości. Na przykład uruchom:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Użyj jednej z następujących składni, w zależności od typu dodawania repozytorium:

    - W przypadku udziału sieciowego użyj .`\\Server\Folder`
    - W przypadku biblioteki SharePoint użyj .`http://sharepoint.contoso.com/Shared%20Documents/Folder`
    - W przypadku ścieżki lokalnej: `C:\Folder`
    - W przypadku ścieżki UNC: `\\Server\Folder`

    > [!NOTE]
    > Symbole wieloznaczne nie są obsługiwane, a lokalizacje WebDav nie są obsługiwane.
    >
    > Aby później zmodyfikować repozytorium, użyj zamiast tego polecenia cmdlet [Set-AIPKannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) . 


W razie potrzeby kontynuuj następujące czynności:

- [Uruchamianie cyklu odnajdowania i wyświetlanie raportów dla skanera](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Używanie programu PowerShell do konfigurowania skanera w celu stosowania klasyfikacji i ochrony](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Konfigurowanie zasad DLP za pomocą skanera przy użyciu programu PowerShell](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

W poniższej tabeli wymieniono polecenia cmdlet programu PowerShell związane z instalowaniem skanera i zarządzaniem zadaniami skanowania zawartości:

| Polecenie cmdlet | Opis |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Dodaje nowe repozytorium do zadania skanowania zawartości. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Zwraca szczegółowe informacje o klastrze. |
| [Get-AIPScannerContentKanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Otrzymuje szczegółowe informacje na temat zadania skanowania zawartości. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Pobiera szczegółowe informacje o repozytoriach zdefiniowanych dla zadania skanowania zawartości. |
| [Remove-AIPScannerContentKanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Usuwa zadanie skanowania zawartości. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Usuwa repozytorium z zadania skanowania zawartości. |
| [Set-AIPScannerContentKanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Określa ustawienia zadania skanowania zawartości. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Definiuje ustawienia istniejącego repozytorium w zadaniu skanowania zawartości. |
| | |

Więcej informacji można znaleźć w następujących artykułach:

- [Co to jest ujednolicony skaner etykiet usługi Azure Information Protection?](/azure/information-protection/deploy-aip-scanner)
- [Konfigurowanie i instalowanie ujednoliconego skanera etykiet usługi Azure Information Protection (AIP)](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [Zarządzaj zadaniami skanowania zawartości tylko za pomocą programu PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
