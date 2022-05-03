---
title: Połączenie z platformą Microsoft 365 za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Połączenie do dzierżawy Microsoft 365 przy użyciu programu PowerShell, aby Microsoft 365 wykonywać zadania centrum administracyjnego z poziomu wiersza polecenia.
ms.openlocfilehash: a69fa6885e254e0c15cd65833a4f8368ec239c4f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174822"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>Połączenie z platformą Microsoft 365 za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Program PowerShell for Microsoft 365 umożliwia zarządzanie ustawieniami Microsoft 365 z poziomu wiersza polecenia. Aby nawiązać połączenie z programem PowerShell, zainstaluj wymagane oprogramowanie, a następnie połącz się z organizacją Microsoft 365.

Istnieją dwie wersje modułu programu PowerShell, których można użyć do nawiązywania połączenia z Microsoft 365 i administrowania kontami użytkowników, grupami i licencjami:

- Azure Active Directory programu PowerShell dla Graph, którego polecenia cmdlet zawierają nazwę *usługi AzureAD*
- Microsoft Azure Active Directory Module for Windows PowerShell, którego polecenia cmdlet zawierają nazwę *Msol*

Obecnie moduł Azure Active Directory programu PowerShell for Graph nie zastępuje całkowicie funkcji modułu Microsoft Azure Active Directory modułu Windows PowerShell na potrzeby administrowania użytkownikami, grupami i licencjami. W niektórych przypadkach należy użyć obu wersji. Obie wersje można bezpiecznie zainstalować na tym samym komputerze.

>[!Note]
>Możesz również nawiązać połączenie z [usługą Azure Cloud Shell](#connect-with-the-azure-cloud-shell) z poziomu Centrum administracyjne platformy Microsoft 365.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?


**System operacyjny**

Musisz użyć 64-bitowej wersji Windows. Obsługa 32-bitowej wersji modułu Microsoft Azure Active Directory dla Windows PowerShell zakończyła się w 2014 roku.

Możesz użyć następujących wersji Windows:
    
  - Windows 10, Windows 8.1, Windows 8 lub Windows 7 z dodatkiem Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2 SP1

>[!Note]
>W przypadku Windows 8.1, Windows 8, Windows 7 z dodatkiem Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2 z dodatkiem SP1 pobierz i zainstaluj [ Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- W przypadku modułu Azure Active Directory programu PowerShell dla Graph należy użyć programu PowerShell w wersji 5.1.

- W przypadku modułu Microsoft Azure Active Directory dla Windows PowerShell modułu należy użyć programu PowerShell w wersji 5.1 lub nowszej, aż do programu PowerShell w wersji 6. Nie można użyć programu PowerShell w wersji 7.
       
>[!Note]
>Te procedury są przeznaczone dla użytkowników, którzy są członkami roli administratora Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Połączenie za pomocą modułu Azure Active Directory Programu PowerShell dla Graph

Polecenia w module Azure Active Directory programu PowerShell dla Graph mają nazwę polecenia cmdlet *usługi AzureAD*. Możesz zainstalować Azure Active Directory program [PowerShell dla modułu Graph](/powershell/azure/active-directory/install-adv2) lub [Azure PowerShell](/powershell/azure/install-az-ps).

W przypadku procedur, które wymagają nowych poleceń cmdlet w module Azure Active Directory Programu PowerShell dla Graph, wykonaj następujące kroki, aby zainstalować moduł i nawiązać połączenie z subskrypcją Microsoft 365.

> [!Note]
> Aby uzyskać informacje o obsłudze różnych wersji Windows, zobacz [Azure Active Directory programu PowerShell dla modułu Graph](/powershell/azure/active-directory/install-adv2) .

### <a name="step-1-install-the-required-software"></a>Krok 1. Instalowanie wymaganego oprogramowania

Te kroki są wymagane tylko raz na komputerze. Jednak prawdopodobnie będzie konieczne okresowe aktualizowanie oprogramowania.
  
1. Otwórz okno wiersza polecenia Windows PowerShell z podwyższonym poziomem uprawnień (uruchom Windows PowerShell jako administrator).
    
2. Uruchom następujące polecenie:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  Domyślnie Galeria programu PowerShell (PSGallery) nie jest skonfigurowany jako zaufane repozytorium dla **programu PowerShellGet**. Przy pierwszym użyciu galerii PSGallery zostanie wyświetlony następujący komunikat:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Odpowiedz **tak** lub **tak na wszystkie, aby** kontynuować instalację.

3.  Uruchom to polecenie, aby zaimportować moduł:
    
    ```powershell
    Import-Module  AzureAD
    ```
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Krok 2. Połączenie do Azure AD subskrypcji Microsoft 365

Aby nawiązać połączenie z Azure Active Directory (Azure AD) dla subskrypcji Microsoft 365 przy użyciu nazwy konta i hasła lub przy użyciu uwierzytelniania wieloskładnikowego, uruchom jedno z tych poleceń w wierszu polecenia Windows PowerShell. (Nie musi być podwyższony poziom.)

| chmura Office 365 | Polecenia |
|:-------|:-----|
| Office 365 Worldwide (+GCC) | `Connect-AzureAD` |
| Office 365 obsługiwane przez 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Niemcy | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 Us Government DoD i Office 365 Us Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

W oknie dialogowym **Logowanie się do konta** wpisz nazwę użytkownika i hasło Microsoft 365 konta służbowego, a następnie wybierz przycisk **OK**.

Jeśli używasz uwierzytelniania wieloskładnikowego, postępuj zgodnie z instrukcjami, aby podać dodatkowe informacje o uwierzytelnianiu, takie jak kod weryfikacyjny.

Po nawiązaniu połączenia możesz użyć poleceń cmdlet Azure Active Directory [programu PowerShell dla modułu Graph](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Połączenie z modułem Microsoft Azure Active Directory dla Windows PowerShell

>[!Note]
>Polecenia cmdlet w module Microsoft Azure Active Directory dla Windows PowerShell mają nazwę *Msol*.

Program PowerShell w wersji 7 lub nowszej nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. W przypadku programu PowerShell w wersji 7 lub nowszej należy użyć zestawu SDK programu PowerShell firmy Microsoft Graph.

Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>Krok 1. Instalowanie wymaganego oprogramowania

Te kroki są wymagane tylko raz na komputerze. Jednak prawdopodobnie będzie konieczne okresowe aktualizowanie oprogramowania.
  
1.  Jeśli nie używasz Windows 10, zainstaluj 32-bitową wersję asystenta logowania usług online firmy Microsoft: [Asystent logowania usług online firmy Microsoft dla specjalistów IT RTW](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi).
    
2. Wykonaj następujące kroki, aby zainstalować moduł Microsoft Azure Active Directory dla Windows PowerShell:
    
   1. Otwórz wiersz polecenia Windows PowerShell z podwyższonym poziomem uprawnień (uruchom polecenie Windows PowerShell jako administrator).
   1.  Uruchom polecenie **MsOnline Install-Module** .
   1. Jeśli zostanie wyświetlony monit o zainstalowanie dostawcy NuGet, wpisz **Y** i naciśnij klawisz Enter.
   1. Jeśli zostanie wyświetlony monit o zainstalowanie modułu z galerii PSGallery, wpisz **Y** i naciśnij klawisz Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Krok 2. Połączenie do Azure AD subskrypcji Microsoft 365

Aby nawiązać połączenie z Azure AD dla subskrypcji Microsoft 365 przy użyciu nazwy konta i hasła lub uwierzytelniania wieloskładnikowego, uruchom jedno z tych poleceń w wierszu polecenia Windows PowerShell. (Nie musi być podwyższony poziom.)

| chmura Office 365 | Polecenia |
|:-------|:-----|
| Office 365 Worldwide (+GCC) | `Connect-MsolService` |
| Office 365 obsługiwane przez 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Niemcy | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 Us Government DoD i Office 365 Us Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

W oknie dialogowym **Logowanie się do konta** wpisz nazwę użytkownika i hasło Microsoft 365 konta służbowego, a następnie wybierz przycisk **OK**.

Jeśli używasz uwierzytelniania wieloskładnikowego, postępuj zgodnie z instrukcjami, aby podać dodatkowe informacje o uwierzytelnianiu, takie jak kod weryfikacyjny.

### <a name="how-do-you-know-it-worked"></a>Skąd wiesz, że to zadziałało?

Jeśli nie zostanie wyświetlony komunikat o błędzie, połączenie zostało nawiązane pomyślnie. Aby uzyskać szybki test, uruchom polecenie cmdlet Microsoft 365, takie jak **Get-MsolUser**, i zobacz wyniki.
  
Jeśli zostanie wyświetlony komunikat o błędzie, sprawdź następujące problemy:
  
- **Typowym problemem jest nieprawidłowe hasło**. Uruchom ponownie [krok 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) i zwróć szczególną uwagę na nazwę użytkownika i hasło, które wprowadzasz.
    
- **Moduł Microsoft Azure Active Directory dla Windows PowerShell wymaga, aby firma Microsoft .NET Framework 3.5.* X* jest włączony na komputerze**. Prawdopodobnie komputer ma zainstalowaną nowszą wersję (na przykład 4 lub 4.5.* x*). Jednak zgodność z poprzednimi wersjami .NET Framework można włączyć lub wyłączyć. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:
    
  - Aby uzyskać Windows Server 2012 lub Windows Server 2012 R2, zobacz [Włączanie .NET Framework 3.5 przy użyciu Kreatora dodawania ról i funkcji](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)).
    
  - Aby uzyskać Windows 7 lub Windows Server 2008 R2, zobacz [Nie można otworzyć modułu Azure Active Directory dla Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - Aby uzyskać Windows 10, Windows 8.1 i Windows 8, zobacz [Instalowanie .NET Framework 3.5 na Windows 10, Windows 8.1 i Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **Twoja wersja modułu Microsoft Azure Active Directory dla Windows PowerShell może być nieaktualna.** Aby to sprawdzić, uruchom następujące polecenie w programie PowerShell dla Microsoft 365 lub Microsoft Azure Active Directory Module for Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Jeśli zwrócony numer wersji jest niższy niż *1.0.8070.2*, odinstaluj moduł Microsoft Azure Active Directory dla Windows PowerShell i zainstaluj go z [kroku 1](#step-1-install-the-required-software) powyżej.

- **Jeśli zostanie wyświetlony komunikat o błędzie połączenia**, zobacz [błąd "Połączenie-MsolService: Wyjątek typu został zgłoszony"](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception).
    
- **Jeśli zostanie wyświetlony komunikat o błędzie "Get-Item: Cannot find path",** uruchom następujące polecenie:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>Połączenie z usługą Azure Cloud Shell

Aby nawiązać połączenie z usługą Azure Cloud Shell i korzystać z niej z Centrum administracyjne platformy Microsoft 365, wybierz ikonę okna programu PowerShell w prawym górnym rogu paska zadań. W okienku **Witamy w usłudze Azure Cloud Shell** wybierz pozycję **PowerShell**.

Będziesz potrzebować aktywnej subskrypcji platformy Azure dla organizacji powiązanej z subskrypcją Microsoft 365. Jeśli jeszcze go nie masz, możesz go utworzyć. Po utworzeniu subskrypcji platformy Azure zostanie otwarte okno programu PowerShell, z którego można uruchamiać polecenia i skrypty programu PowerShell.

Aby uzyskać więcej informacji, zobacz [Azure Cloud Shell](/azure/cloud-shell/overview).


## <a name="get-started-with-the-microsoft-graph-powershell-sdk"></a>Wprowadzenie z zestawem SDK programu PowerShell firmy Microsoft Graph

Możesz użyć zestawu SDK programu PowerShell firmy Microsoft Graph, aby uzyskać dostęp do wszystkich interfejsów API Graph firmy Microsoft.

Aby uzyskać więcej informacji, zobacz [Wprowadzenie z zestawem Microsoft Graph PowerShell SDK](/powershell/microsoftgraph/get-started?view=graph-powershell-beta)

## <a name="see-also"></a>Zobacz też

- [Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [Połączenie ze wszystkimi usługami Microsoft 365 w pojedynczym oknie programu PowerShell](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
