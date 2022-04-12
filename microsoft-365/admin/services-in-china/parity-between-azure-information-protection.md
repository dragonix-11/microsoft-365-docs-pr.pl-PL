---
title: Obsługa Information Protection platformy Azure dla Office 365 obsługiwanych przez firmę 21Vianet
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
description: Dowiedz się więcej o usłudze Azure Information Protection (AIP) dla Office 365 obsługiwanych przez firmę 21Vianet oraz sposobie konfigurowania jej dla klientów w Chinach.
monikerRange: o365-21vianet
ms.openlocfilehash: 3b4906844c76293a1163d17d77b009528ef32f12
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782902"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>Obsługa Information Protection platformy Azure dla Office 365 obsługiwanych przez firmę 21Vianet

W tym artykule opisano różnice między obsługą usługi Azure Information Protection (AIP) dla Office 365 obsługiwanych przez usługę 21Vianet i ofertami komercyjnymi, a także konkretne instrukcje dotyczące konfigurowania usługi AIP dla klientów w Chinach&mdash;, w tym sposób instalowania lokalnego skanera usługi AIP i zarządzania zadaniami skanowania zawartości.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Różnice między usługą AIP dla Office 365 obsługiwanych przez firmę 21Vianet i ofertami komercyjnymi

Naszym celem jest dostarczenie klientom w Chinach wszystkich komercyjnych funkcji i funkcji za pomocą naszego rozwiązania AIP dla Office 365 obsługiwanych przez ofertę 21Vianet, ale brakuje niektórych funkcji, które chcielibyśmy wyróżnić.

Poniższa lista zawiera istniejące luki między usługą AIP dla Office 365 obsługiwanych przez firmę 21Vianet a naszą ofertą handlową od stycznia 2021 r.:

- szyfrowanie Usługi Active Directory Rights Management (AD RMS) jest obsługiwane tylko w Aplikacje Microsoft 365 dla przedsiębiorstw (kompilacja 11731.10000 lub nowsza). Office Professional Plus nie obsługuje usług AD RMS.

- Migracja z usług AD RMS do usługi AIP jest obecnie niedostępna.
  
- Udostępnianie chronionych wiadomości e-mail użytkownikom w chmurze komercyjnej jest obsługiwane.
  
- Udostępnianie dokumentów i załączników wiadomości e-mail użytkownikom w chmurze komercyjnej jest obecnie niedostępne. Obejmuje to Office 365 obsługiwanych przez użytkowników 21Vianet w chmurze komercyjnej, bez Office 365 obsługiwanych przez użytkowników 21Vianet w chmurze komercyjnej oraz użytkowników z licencją RMS for Individuals.
  
- Usługa IRM z SharePoint (witrynami i bibliotekami chronionymi przez usługę IRM) jest obecnie niedostępna.
  
- Rozszerzenie urządzenia przenośnego dla usług AD RMS jest obecnie niedostępne.

- [Przeglądarka mobilna](/azure/information-protection/rms-client/mobile-app-faq) nie jest obsługiwana przez usługę Azure China 21Vianet.

- Obszar AIP Azure Portal jest niedostępny dla klientów w Chinach. Użyj [poleceń programu PowerShell zamiast wykonywać akcje](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) w portalu, takie jak zarządzanie zadaniami skanowania zawartości i uruchamianie ich.

- Punkty końcowe usługi AIP w Office 365 obsługiwane przez firmę 21Vianet różnią się od punktów końcowych wymaganych dla innych usług w chmurze. Wymagana jest łączność sieciowa z klientów do następujących punktów końcowych:
    - Pobierz zasady etykiet i etykiet: `*.protection.partner.outlook.cn`
    - Usługa Azure Rights Management: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Konfigurowanie usługi AIP dla klientów w Chinach

Aby skonfigurować usługę AIP dla klientów w Chinach:
1. [Włącz usługę Rights Management dla dzierżawy](#step-1-enable-rights-management-for-the-tenant).

1. [Dodaj jednostkę usługi Microsoft Information Protection Sync Service](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [Konfigurowanie szyfrowania DNS](#step-3-configure-dns-encryption).

1. [Zainstaluj i skonfiguruj klienta ujednoliconego etykietowania usługi AIP](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Konfigurowanie aplikacji usługi AIP na Windows](#step-5-configure-aip-apps-on-windows).

1. [Zainstaluj lokalny skaner usługi AIP i zarządzaj zadaniami skanowania zawartości](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>Krok 1. Włączanie usługi Rights Management dla dzierżawy

Aby szyfrowanie działało poprawnie, usługa RMS musi być włączona dla dzierżawy.

1. Sprawdź, czy usługa RMS jest włączona:

    1. Uruchom program PowerShell jako administrator.
    2. Jeśli moduł AIPService nie jest zainstalowany, uruchom polecenie `Install-Module AipService`.
    3. Zaimportuj moduł przy użyciu polecenia `Import-Module AipService`.
    4. Połączenie do usługi przy użyciu polecenia `Connect-AipService -environmentname azurechinacloud`.
    5. Uruchom `(Get-AipServiceConfiguration).FunctionalState` polecenie i sprawdź, czy stan to `Enabled`.

2. Jeśli stan funkcjonalny to `Disabled`, uruchom polecenie `Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>Krok 2. Dodawanie jednostki usługi Microsoft Information Protection Sync Service

Jednostka usługi **Microsoft Information Protection Sync Service** nie jest domyślnie dostępna w dzierżawach usługi Azure China i jest wymagana dla usługi Azure Information Protection. Utwórz tę jednostkę usługi ręcznie za pośrednictwem modułu Azure Az PowerShell.

1. Jeśli nie masz zainstalowanego modułu Azure Az, zainstaluj go lub użyj zasobu, w którym moduł Azure Az jest wstępnie zainstalowany, na przykład [Azure Cloud Shell](/azure/cloud-shell/overview). Aby uzyskać więcej informacji, zobacz [Instalowanie modułu Azure Az PowerShell](/powershell/azure/install-az-ps).

1. Połączenie do usługi przy użyciu polecenia cmdlet [Połączenie-AzAccount](/powershell/module/az.accounts/Connect-AzAccount) i nazwy `azurechinacloud` środowiska:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. Ręcznie utwórz **jednostkę usługi synchronizacji Microsoft Information Protection** przy użyciu polecenia cmdlet [New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) i `870c4f2e-85b6-4d43-bdda-6ed9a579b725` identyfikatora aplikacji dla usługi Microsoft Information Protection Sync Service:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Po dodaniu jednostki usługi dodaj odpowiednie uprawnienia wymagane do usługi.

### <a name="step-3-configure-dns-encryption"></a>Krok 3. Konfigurowanie szyfrowania DNS

Aby szyfrowanie działało poprawnie, Office aplikacje klienckie muszą łączyć się z wystąpieniem usługi w Chinach i stamtąd uruchamiać. Aby przekierowywać aplikacje klienckie do odpowiedniego wystąpienia usługi, administrator dzierżawy musi skonfigurować rekord SRV DNS z informacjami o adresie URL usługi Azure RMS. Bez rekordu SRV DNS aplikacja kliencka spróbuje połączyć się domyślnie z wystąpieniem chmury publicznej i zakończy się niepowodzeniem.

Ponadto przyjęto założenie, że użytkownicy będą logować się przy użyciu nazwy użytkownika na podstawie domeny należącej do dzierżawy (na przykład `joe@contoso.cn`), a nie `onmschina` nazwy użytkownika (na przykład `joe@contoso.onmschina.cn`). Nazwa domeny z nazwy użytkownika jest używana do przekierowania DNS do poprawnego wystąpienia usługi.

#### <a name="configure-dns-encryption---windows"></a>Konfigurowanie szyfrowania DNS — Windows

1. Pobierz identyfikator usługi RMS:

    1. Uruchom program PowerShell jako administrator.
    2. Jeśli moduł AIPService nie jest zainstalowany, uruchom polecenie `Install-Module AipService`.
    3. Połączenie do usługi przy użyciu polecenia `Connect-AipService -environmentname azurechinacloud`.
    4. Uruchom polecenie `(Get-AipServiceConfiguration).RightsManagementServiceId` , aby uzyskać identyfikator usługi RMS.

2. Zaloguj się do dostawcy DNS, przejdź do ustawień DNS dla domeny, a następnie dodaj nowy rekord SRV.

    - Usługa = `_rmsredir`
    - Protokół = `_http`
    - Nazwa = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (gdzie identyfikator GUID jest identyfikatorem usługi RMS)
    - Priority, Weight, Seconds, TTL = default values (Priorytet, Waga, Sekundy, Czas wygaśnięcia = wartości domyślne)

3. Skojarz domenę niestandardową z dzierżawą w [Azure Portal](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Spowoduje to dodanie wpisu w systemie DNS, co może potrwać kilka minut po dodaniu wartości do ustawień DNS.

4. Zaloguj się do Centrum administracyjne platformy Microsoft 365 przy użyciu odpowiednich poświadczeń administratora globalnego i dodaj domenę (na przykład `contoso.cn`) w celu utworzenia użytkownika. W procesie weryfikacji mogą być wymagane dodatkowe zmiany dns. Po zakończeniu weryfikacji można utworzyć użytkowników.

#### <a name="configure-dns-encryption---mac-ios-android"></a>Konfigurowanie szyfrowania DNS — Mac, iOS, Android

Zaloguj się do dostawcy DNS, przejdź do ustawień DNS dla domeny, a następnie dodaj nowy rekord SRV.

- Usługa = `_rmsdisco`
- Protokół = `_http`
- Nazwa = `_tcp`
- Wartość docelowa = `api.aadrm.cn`
- Port = `80`
- Priority, Weight, Seconds, TTL = default values (Priorytet, Waga, Sekundy, Czas wygaśnięcia = wartości domyślne)


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>Krok 4. Instalowanie i konfigurowanie klienta ujednoliconego etykietowania usługi AIP

Pobierz i zainstaluj klienta ujednoliconego etykietowania usługi AIP z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

Więcej informacji można znaleźć w następujących artykułach:

- [Dokumentacja usługi AIP](/azure/information-protection/)
- [Historia wersji usługi AIP i zasady pomocy technicznej](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Wymagania systemowe usługi AIP](/azure/information-protection/requirements)
- [Szybki start usługi AIP: wdrażanie klienta usługi AIP](/azure/information-protection/quickstart-deploy-client)
- [Przewodnik administratora usługi AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [Przewodnik użytkownika usługi AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [Dowiedz się więcej o etykietach poufności Microsoft 365](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>Krok 5. Konfigurowanie aplikacji usługi AIP na Windows

Aplikacje usługi AIP na Windows potrzebują następującego klucza rejestru, aby wskazać im poprawną suwerenną chmurę dla platformy Azure w Chinach:

- Węzeł rejestru = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Nazwa = `CloudEnvType`
- Wartość = `6` (wartość domyślna = 0)
- Typ = `REG_DWORD`

> [!IMPORTANT]
> Upewnij się, że klucz rejestru nie jest usuwany po odinstalowaniu. Jeśli klucz jest pusty, niepoprawny lub nieistniejący, funkcja będzie zachowywać się jako wartość domyślna (wartość domyślna = 0 dla chmury komercyjnej). Jeśli klucz jest pusty lub niepoprawny, do dziennika jest również dodawany błąd drukowania.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>Krok 6. Instalowanie lokalnego skanera usługi AIP i zarządzanie zadaniami skanowania zawartości

Zainstaluj lokalny skaner usługi AIP, aby przeskanować udziały sieci i zawartości pod kątem poufnych danych oraz zastosować etykiety klasyfikacji i ochrony zgodnie z konfiguracją w zasadach organizacji.

Podczas konfigurowania zadań skanowania zawartości i zarządzania nimi należy użyć poniższej procedury zamiast [interfejsu Azure Portal](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) używanego przez oferty komercyjne.

Aby uzyskać więcej informacji, zobacz [Co to jest skaner ujednoliconego etykietowania usługi Azure Information Protection?](/azure/information-protection/deploy-aip-scanner) i [Manage your content scan jobs using PowerShell only (Zarządzanie zadaniami skanowania zawartości tylko przy użyciu programu PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer)).

**Aby zainstalować i skonfigurować skaner**:

1. Zaloguj się na komputerze Windows Server, na który zostanie uruchomiony skaner. Użyj konta z uprawnieniami administratora lokalnego, które ma uprawnienia do zapisu w bazie danych SQL Server master.

1. Zacznij od zamknięcia programu PowerShell. Jeśli wcześniej zainstalowano klienta i skaner usługi AIP, upewnij się, że usługa **AIPScanner** została zatrzymana.

1. Otwórz sesję Windows PowerShell z **opcją Uruchom jako administrator**.

1. Uruchom polecenie cmdlet [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner), określając wystąpienie SQL Server, na którym ma zostać utworzona baza danych dla skanera usługi Azure Information Protection, oraz opisową nazwę klastra skanera.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Możesz użyć tej samej nazwy klastra w poleceniu [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) , aby skojarzyć wiele węzłów skanera z tym samym klastrem. Użycie tego samego klastra dla wielu węzłów skanera umożliwia współdziałanie wielu skanerów w celu wykonania skanowania.
    > 

1. Sprawdź, czy usługa jest teraz zainstalowana przy użyciu **narzędzi** >  **administracyjnychUsługi**.

    Zainstalowana usługa ma nazwę **Azure Information Protection Scanner** i jest skonfigurowana do uruchamiania przy użyciu utworzonego konta usługi skanera.

1. Pobierz token platformy Azure do użycia ze skanerem. Token usługi Azure AD umożliwia skanerowi uwierzytelnianie w usłudze Azure Information Protection, dzięki czemu skaner może działać nieinterakcyjnie. 

    1. Otwórz Azure Portal i utwórz aplikację usługi Azure AD, aby określić token dostępu do uwierzytelniania. Aby uzyskać więcej informacji, zobacz [How to label files non-interactively for Azure Information Protection (Jak etykietować pliki nieinterakcyjnie dla usługi Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)).
    
        > [!TIP]
        > Podczas tworzenia i konfigurowania aplikacji usługi Azure AD dla polecenia [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) okienko **Uprawnienia interfejsu API żądania** pokazuje kartę **Interfejsy API używane przez moją organizację** zamiast karty **Interfejsy API firmy Microsoft** . Wybierz **interfejsy API używane przez moją organizację** , aby następnie wybrać pozycję **Azure Rights Management Services**. 
        >

    1. Jeśli konto usługi skanera zostało **przydzielone lokalnie** bezpośrednio do instalacji na komputerze z serwerem Windows, zaloguj się przy użyciu tego konta i rozpocznij sesję programu PowerShell. 
    
        Jeśli kontu usługi skanera nie można udzielić **lokalnego** logowania do instalacji, użyj parametru *OnBehalfOf* z [poleceniem Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), zgodnie z opisem w [temacie How to label files non-interactively for Azure Information Protection (Jak etykietować pliki nieinterakcyjnie dla usługi Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)).

    1. Uruchom [polecenie Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), określając wartości skopiowane z aplikacji usługi Azure AD:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Przykład:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Skaner ma teraz token do uwierzytelniania w usłudze Azure AD. Ten token jest ważny przez jeden rok, dwa lata lub nigdy, zgodnie z konfiguracją **wpisu tajnego klienta aplikacji internetowej /interfejsu API** w usłudze Azure AD. Po wygaśnięciu tokenu należy powtórzyć tę procedurę.

1. Uruchom polecenie cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) , aby ustawić skaner do działania w trybie offline. Uruchomić:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Uruchom polecenie cmdlet [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) , aby utworzyć domyślne zadanie skanowania zawartości.

    Jedynym wymaganym parametrem w poleceniu cmdlet **Set-AIPScannerContentScanJob** jest **wymuszanie**. W tej chwili możesz jednak zdefiniować inne ustawienia zadania skanowania zawartości. Przykład:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    Powyższa składnia konfiguruje następujące ustawienia podczas kontynuowania konfiguracji:

    - Umożliwia ręczne uruchamianie harmonogramu uruchamiania *skanera*
    - Ustawia typy informacji do odnalezienia na podstawie zasad etykietowania poufności
    - *Nie* wymusza zasad etykietowania poufności
    - Automatyczne etykietowanie plików na podstawie zawartości przy użyciu etykiety domyślnej zdefiniowanej dla zasad etykietowania poufności
    - *Nie* zezwala na ponowne etykietowanie plików
    - Zachowuje szczegóły pliku podczas skanowania i automatycznego etykietowania, w tym *datę modyfikacji*, *ostatniej modyfikacji* i *modyfikacji według* wartości
    - Ustawia skaner do wykluczania plików msg i tmp podczas uruchamiania
    - Ustawia domyślnego właściciela na konto, którego chcesz użyć podczas uruchamiania skanera

1. Użyj polecenia cmdlet [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) , aby zdefiniować repozytoria, które chcesz skanować w zadaniu skanowania zawartości. Na przykład uruchom polecenie:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Użyj jednej z następujących składni, w zależności od typu dodanego repozytorium:

    - W przypadku udziału sieciowego użyj polecenia `\\Server\Folder`.
    - W przypadku biblioteki SharePoint użyj polecenia `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - W przypadku ścieżki lokalnej: `C:\Folder`
    - W przypadku ścieżki UNC: `\\Server\Folder`

    > [!NOTE]
    > Symbole wieloznaczne nie są obsługiwane, a lokalizacje WebDav nie są obsługiwane.
    >
    > Aby później zmodyfikować repozytorium, użyj polecenia cmdlet [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) . 


W razie potrzeby wykonaj następujące kroki:

- [Uruchamianie cyklu odnajdywania i wyświetlanie raportów dla skanera](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Konfigurowanie skanera w celu zastosowania klasyfikacji i ochrony przy użyciu programu PowerShell](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Konfigurowanie zasad DLP przy użyciu programu PowerShell przy użyciu skanera](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

W poniższej tabeli wymieniono polecenia cmdlet programu PowerShell, które są istotne dla instalowania skanera i zarządzania zadaniami skanowania zawartości:

| Polecenie cmdlet | Opis |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Dodaje nowe repozytorium do zadania skanowania zawartości. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Zwraca szczegółowe informacje o klastrze. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Pobiera szczegółowe informacje o zadaniu skanowania zawartości. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Pobiera szczegółowe informacje o repozytoriach zdefiniowanych dla zadania skanowania zawartości. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Usuwa zadanie skanowania zawartości. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Usuwa repozytorium z zadania skanowania zawartości. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Definiuje ustawienia zadania skanowania zawartości. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Definiuje ustawienia istniejącego repozytorium w zadaniu skanowania zawartości. |
| | |

Więcej informacji można znaleźć w następujących artykułach:

- [Co to jest skaner ujednoliconego etykietowania usługi Azure Information Protection?](/azure/information-protection/deploy-aip-scanner)
- [Konfigurowanie i instalowanie skanera ujednoliconego etykietowania usługi Azure Information Protection (AIP)](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [Zarządzaj zadaniami skanowania zawartości tylko przy użyciu programu PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
