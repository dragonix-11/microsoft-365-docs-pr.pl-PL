---
title: Połączenie do Microsoft 365 za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Połączenie dzierżawy usługi Microsoft 365, używając programu PowerShell Microsoft 365 do wykonywania zadań w centrum administracyjnym z wiersza polecenia.
ms.openlocfilehash: 67c3a596d1b0d7acec2925f39c2f6bd8025d7d4a
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013850"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>Połączenie do Microsoft 365 za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Program PowerShell Microsoft 365 umożliwia zarządzanie ustawieniami Microsoft 365 z wiersza polecenia. Aby nawiązać połączenie z programem PowerShell, zainstaluj wymagane oprogramowanie, a następnie połącz się ze swoją Microsoft 365 organizacją.

Istnieją dwie wersje modułu programu PowerShell, za pomocą których można łączyć się Microsoft 365 kontami użytkowników, grupami i licencjami oraz administrować tymi kontami:

- Azure Active Directory PowerShell dla programu Graph, którego polecenia cmdlet zawierają *w nazwie azureAD*
- Microsoft Azure Active Directory module for Windows PowerShell, którego polecenia cmdlet mają *w nazwie Msol*

Obecnie moduł Azure Active Directory PowerShell dla systemu Graph nie zastępuje całkowicie funkcji modułu Microsoft Azure Active Directory dla modułu Windows PowerShell dla użytkowników, grup i administracji licencją. W niektórych przypadkach trzeba używać obu wersji. Obie wersje możesz bezpiecznie zainstalować na tym samym komputerze.

>[!Note]
>Możesz również połączyć się z powłoką [platformy Azure Cloud Shell](#connect-with-the-azure-cloud-shell) z centrum administracyjne platformy Microsoft 365.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?


**System operacyjny**

Musisz używać 64-bitowej wersji pakietu Windows. Obsługa 32-bitowej wersji modułu Microsoft Azure Active Directory dla Windows PowerShell zakończyła się w 2014 roku.

Można używać następujących wersji programu Windows:
    
  - Windows 10, Windows 8.1, Windows 8 lub Windows 7 z dodatkiem Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2 z dodatkiem SP1

>[!Note]
>W przypadku Windows 8.1, Windows 8, Windows 7 z dodatkiem Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2 z dodatkiem SP1 pobierz [i zainstaluj Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- Aby uzyskać Azure Active Directory PowerShell dla Graph, musisz użyć programu PowerShell w wersji 5.1.

- W przypadku Microsoft Azure Active Directory modułu Windows PowerShell należy użyć programu PowerShell w wersji 5.1 lub nowszej, do wersji 6 programu PowerShell. Nie można używać programu PowerShell w wersji 7.
       
>[!Note]
>Te procedury są przeznaczone dla użytkowników, którzy są członkami Microsoft 365 roli administratora. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Połączenie modułem Azure Active Directory PowerShell dla Graph programu PowerShell

Polecenia w programie Azure Active Directory PowerShell dla programu Graph mają nazwę polecenia cmdlet *AzureAD*. Możesz zainstalować moduł [Azure Active Directory PowerShell dla Graph](/powershell/azure/active-directory/install-adv2) lub [Azure PowerShell](/powershell/azure/install-az-ps).

W przypadku procedur wymagających nowych poleceń cmdlet w module Azure Active Directory PowerShell dla programu Graph wykonaj poniższe czynności, aby zainstalować moduł i połączyć się z subskrypcją usługi Microsoft 365.

> [!Note]
> Aby uzyskać informacje na temat obsługi różnych wersji programu Windows, zobacz Azure Active Directory [PowerShell dla Graph programu](/powershell/azure/active-directory/install-adv2) .

### <a name="step-1-install-the-required-software"></a>Krok 1. Instalowanie wymaganego oprogramowania

Te kroki są wymagane tylko raz na komputerze. Prawdopodobnie konieczne będzie jednak okresowe aktualizowanie oprogramowania.
  
1. Otwórz okno wiersza Windows PowerShell z podwyższonym poziomem uprawnień (uruchom Windows PowerShell jako administrator).
    
2. Uruchom następujące polecenie:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  Galeria programu PowerShell (PSGallery) nie jest domyślnie skonfigurowana jako zaufane repozytorium programu **PowerShellGet**. Podczas pierwszego użyciagalera PSGallery zostanie wyświetlony następujący komunikat:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Odpowiedz **Tak** lub **Tak na pozycję Wszystkie** , aby kontynuować instalację.

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Krok 2. Połączenie do usługi Azure AD dla swojej Microsoft 365 subskrypcji usługi

Aby nawiązać połączenie z usługą Azure Active Directory (Azure AD) dla subskrypcji usługi Microsoft 365 za pomocą nazwy konta i hasła lub za pomocą uwierzytelniania wieloskładnikowego, uruchom jedno z tych poleceń z wiersza Windows PowerShell polecenia. Nie trzeba go podwyższonym poziomem uprawnień.

| Office 365 chmurze | Polecenie |
|:-------|:-----|
| Office 365 Worldwide (+GCC) | `Connect-AzureAD` |
| Office 365 obsługiwana przez firmę 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 Rząd Stanów Zjednoczonych doD i Office 365 Rząd Stanów Zjednoczonych GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

W **oknie dialogowym** Logowanie do konta wpisz swoją Microsoft 365 użytkownika i hasło konta służbowego, a następnie wybierz przycisk **OK**.

Jeśli używasz uwierzytelniania wieloskładnikowego, postępuj zgodnie z instrukcjami, aby podać dodatkowe informacje uwierzytelnienia, takie jak kod weryfikacyjny.

Po nawiązania połączenia możesz używać poleceń cmdlet dla programu [Azure Active Directory PowerShell dla Graph moduł.](/powershell/module/azuread)

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Połączenie moduł Microsoft Azure Active Directory dla Windows PowerShell

>[!Note]
>Polecenia cmdlet w module Microsoft Azure Active Directory dla Windows PowerShell mają *nazwę Msol*.

Program PowerShell w wersji 7 i nowszej nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet *z Msol* w nazwie. W przypadku programu PowerShell w wersji 7 i nowszej należy użyć zestawu SDK programu Microsoft Graph PowerShell.

Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z *nazwą Msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>Krok 1. Instalowanie wymaganego oprogramowania

Te kroki są wymagane tylko raz na komputerze. Prawdopodobnie konieczne będzie jednak okresowe aktualizowanie oprogramowania.
  
1.  Jeśli nie używasz programu Windows 10, zainstaluj 32-bitową wersję Asystenta logowania w witrynie Microsoft Online Services: Asystent logowania w witrynie [Microsoft Online Services dla informatyków RTW](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi).
    
2. Wykonaj poniższe czynności, aby zainstalować moduł Microsoft Azure Active Directory dla Windows PowerShell:
    
   1. Otwórz wiersz polecenia Windows PowerShell z podwyższonym poziomem uprawnień (uruchom Windows PowerShell jako administrator).
   1.  Uruchom polecenie **Install-Module MSOnline** .
   1. Jeśli zostanie wyświetlony monit o zainstalowanie dostawcy NuGet, wpisz **Y** i naciśnij klawisz Enter.
   1. Jeśli zostanie wyświetlony monit o zainstalowanie modułu z psGallery, wpisz **Y** i naciśnij klawisz Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Krok 2. Połączenie do usługi Azure AD dla swojej Microsoft 365 subskrypcji usługi

Aby połączyć się z usługą Azure AD dla subskrypcji usługi Microsoft 365 za pomocą nazwy konta i hasła lub przy użyciu uwierzytelniania wieloskładnikowego, uruchom jedno z tych poleceń z wiersza Windows PowerShell polecenia. Nie trzeba go podwyższonym poziomem uprawnień.

| Office 365 chmurze | Polecenie |
|:-------|:-----|
| Office 365 Worldwide (+GCC) | `Connect-MsolService` |
| Office 365 obsługiwana przez firmę 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 Rząd Stanów Zjednoczonych doD i Office 365 Rząd Stanów Zjednoczonych GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

W **oknie dialogowym** Logowanie do konta wpisz swoją Microsoft 365 użytkownika i hasło konta służbowego, a następnie wybierz przycisk **OK**.

Jeśli używasz uwierzytelniania wieloskładnikowego, postępuj zgodnie z instrukcjami, aby podać dodatkowe informacje uwierzytelnienia, takie jak kod weryfikacyjny.

### <a name="how-do-you-know-it-worked"></a>Skąd wiadomo, że to zadziałało?

Jeśli nie zostanie wyświetlony komunikat o błędzie, pomyślnie nałączono połączenie. Aby uzyskać szybki test, uruchom polecenie cmdlet Microsoft 365, takie jak **Get-MsolUser**, i wyświetl wyniki.
  
Jeśli zostanie wyświetlony komunikat o błędzie, sprawdź następujące problemy:
  
- **Częstym problemem jest niepoprawne hasło**. Ponownie [uruchom krok 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) i zwróć szczególną uwagę na wprowadzeniu nazwy użytkownika i hasła.
    
- **Moduł Microsoft Azure Active Directory dla Windows PowerShell wymaga, aby firma Microsoft .NET Framework 3.5.* x* jest włączone na komputerze**. Prawdopodobnie na komputerze jest* zainstalowana nowsza wersja (na przykład 4 lub 4.5. x*). Jednak zgodność z poprzednimi wersjami pakietu .NET Framework można włączyć lub wyłączyć. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:
    
  - Aby Windows Server 2012 lub Windows Server 2012 R2, zobacz [Włączanie .NET Framework 3.5](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)) za pomocą Kreatora dodawania ról i funkcji.
    
  - Aby Windows 7 lub Windows Server 2008 R2, zobacz Nie można otworzyć modułu Azure Active Directory [dla systemu Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - Aby uzyskać Windows 10, Windows 8.1 i Windows 8, zobacz Instalowanie pakietu [.NET Framework 3.5 na Windows 10, Windows 8.1 i Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **Twoja wersja modułu Microsoft Azure Active Directory dla systemu Windows PowerShell może być nie aktualny.** Aby to sprawdzić, uruchom następujące polecenie w programie PowerShell dla programu Microsoft 365 lub moduł Microsoft Azure Active Directory dla Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Jeśli zwrócony numer wersji jest niższy niż *1.0.8070.2*, odinstaluj moduł Microsoft Azure Active Directory dla systemu Windows PowerShell i zainstaluj go z kroku [1](#step-1-install-the-required-software) powyżej.

- **Jeśli zostanie wyświetlony komunikat o błędzie połączenia**, zobacz [błąd "Połączenie-MsolService: Wyjątek typu został wygenerowany"](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception).
    
- **Jeśli zostanie wyświetlony komunikat o błędzie "Get-Item: Nie można odnaleźć ścieżki"**, uruchom to polecenie:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>Połączenie przy użyciu powłoki chmury platformy Azure

Aby nawiązać połączenie z powłoką Azure Cloud Shell z centrum administracyjne platformy Microsoft 365, wybierz ikonę okna programu PowerShell w prawym górnym rogu paska zadań. W **okienku Witamy w usłudze Azure Cloud Shell** wybierz pozycję **PowerShell**.

Potrzebujesz aktywnej subskrypcji platformy Azure dla Twojej organizacji powiązanej z Twoją subskrypcją usługi Microsoft 365 Azure. Jeśli jeszcze jej nie masz, możesz ją utworzyć. Po wykupie subskrypcji platformy Azure zostanie otwarte okno programu PowerShell, w którym można uruchamiać polecenia i skrypty programu PowerShell.

Aby uzyskać więcej informacji, zobacz [Powłoka platformy Azure Cloud Shell](/azure/cloud-shell/overview).

## <a name="see-also"></a>Zobacz też

- [Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [Połączenie do wszystkich Microsoft 365 w jednym Windows PowerShell okna](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
