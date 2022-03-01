---
title: Połączenie do wszystkich Microsoft 365 w jednym oknie programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/23/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Podsumowanie: Połączenie do wszystkich Microsoft 365 w jednym oknie programu PowerShell.'
ms.openlocfilehash: 4df9a16aba22587adbe289bca2d74e78a64db4ba
ms.sourcegitcommit: b51bfed24a9e3b7adf82d4918b76462cd40dffaf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007875"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Połączenie do wszystkich Microsoft 365 w jednym oknie programu PowerShell

Gdy zarządzasz sesjami za pomocą Microsoft 365 PowerShell, możesz jednocześnie otwierać wiele sesji programu PowerShell. Możesz mieć różne okna programu PowerShell do zarządzania kontami użytkowników, usługami SharePoint Online, Exchange Online, Skype dla firm Online, Microsoft Teams i Centrum &amp; zgodności zabezpieczeń.
  
Ten scenariusz nie jest optymalny w przypadku zarządzania Microsoft 365, ponieważ nie można wymieniać danych między tymi oknami w celu zarządzania między usługami. W tym artykule opisano, jak za pomocą jednego wystąpienia programu PowerShell zarządzać kontami usługi Microsoft 365, usługami Skype dla firm Online, Exchange Online, SharePoint Online, Microsoft Teams &amp; i Centrum zgodności zabezpieczeń.

>[!Note]
>Ten artykuł zawiera obecnie tylko polecenia nawiązywania połączenia z chmurą na całym świecie (+GCC). Notatki zawierają linki do artykułów dotyczących łączenia się z innymi Microsoft 365 chmurami.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem zarządzania wszystkimi plikami Microsoft 365 jednym wystąpieniem programu PowerShell należy wziąć pod uwagę następujące wymagania wstępne:
  
- Konto Microsoft 365 służbowe, z których korzystasz, musi być członkiem roli Microsoft 365 administratora. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../admin/add-users/about-admin-roles.md). Jest to wymagane w programie PowerShell dla Microsoft 365, ale nie musi to dotyczyć wszystkich Microsoft 365 usług.
    
- Możesz używać następujących 64-bitowych wersji Windows:
    
  - Windows 10
    
  - Windows 8.1 lub Windows 8
    
  - Windows Server 2019
    
  - System Windows Server 2016
    
  - Windows Server 2012 R2 lub Windows Server 2012
    
  - Windows 7 z dodatkiem Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 z dodatkiem SP1*
    
    \*Musisz zainstalować program Microsoft .NET Framework 4.5.*x*, a następnie Windows Management Framework 3.0 lub 4.0. Aby uzyskać więcej informacji, [zobacz Windows Management Framework](/powershell/scripting/windows-powershell/wmf/overview).
    
    Korzystanie z 64-bitowej wersji pakietu Windows jest spowodowane wymaganiami modułu Skype dla firm Online i jednego z modułów Microsoft 365 danych.
    
- Należy zainstalować moduły wymagane dla usług Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype dla firm Online i Teams:
    
  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint powłoki zarządzania online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Skype dla firm Online, Moduł programu PowerShell](/microsoftteams/teams-powershell-overview)
  - [Exchange Online w wersji 2 programu PowerShell](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Teams programu PowerShell — omówienie](/microsoftteams/teams-powershell-overview)
    
-  Program PowerShell musi być skonfigurowany do uruchamiania podpisanych skryptów dla usługi Skype dla firm Online i Centrum zgodności &amp; zabezpieczeń. Uruchom następujące polecenie w sesji programu PowerShell o podwyższonym poziomie uprawnień (sesji programu PowerShell uruchamianej **jako administrator**).
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Kroki połączenia w przypadku używania tylko hasła

Wykonaj poniższe czynności, aby połączyć się ze wszystkimi usługami w jednym oknie programu PowerShell, gdy używasz tylko hasła do logowania.
  
1. Otwórz Windows PowerShell.
    
2. Uruchom to polecenie i wprowadź poświadczenia Microsoft 365 konta służbowego.
    
   ```powershell
   $credential = Get-Credential
   ```

3. Uruchom to polecenie, aby połączyć się z usługą Azure AD przy użyciu modułu Azure Active Directory PowerShell dla Graph usługi.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   Jeśli używasz modułu modułu Microsoft Azure Active Directory dla Windows PowerShell, uruchom to polecenie.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z *nazwą Msol*. Te polecenia cmdlet należy uruchomić z programu PowerShell.

4. Uruchom te polecenia, aby połączyć się z usługą SharePoint Online. Określ nazwę organizacji dla swojej domeny. Na przykład w przypadku "litwareinc\. onmicrosoft.com" wartość nazwy organizacji to "litwareinc".
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. Uruchom te polecenia, aby połączyć się z Exchange Online.
    
   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -ShowProgress $true
   ```

   > [!Note]
   > Aby uzyskać informacje na temat Exchange Online dla Microsoft 365 chmur innych niż na całym świecie, zobacz Połączenie [do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. Uruchom te polecenia, aby połączyć się z Centrum zgodności &amp; zabezpieczeń.
    
   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!Note]
   > Aby nawiązać połączenie z &amp; Centrum zgodności zabezpieczeń dla chmur Microsoft 365 innych niż na całym świecie, zobacz nawiązywanie połączenia Połączenie [z Centrum zabezpieczeń & w programie PowerShell](/powershell/exchange/connect-to-scc-powershell).

7. Uruchom te polecenia, aby nawiązać połączenie Teams PowerShell (i Skype dla firm Online).
    
   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams PowerShell. Jeśli używasz najnowszej wersji programu Teams PowerShell, nie musisz instalować do łącznika usługi Skype dla firm Online.
  
   > [!Note]
   > Aby nawiązać połączenie Microsoft Teams chmurami innymi niż na całym *świecie, zobacz* [Połączenie-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).
  


### <a name="azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory PowerShell dla Graph programu PowerShell

Oto polecenia dla wszystkich usług w jednym bloku podczas korzystania z programu PowerShell Azure Active Directory dla Graph moduł. Określ nazwę hosta domeny i nazwę UPN dla logowania, a następnie uruchom je wszystkie jednocześnie.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-AzureAD -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory moduł Windows PowerShell modułu

Oto polecenia dla wszystkich usług w jednym bloku podczas korzystania z modułu modułu Microsoft Azure Active Directory modułu Windows PowerShell moduł. Określ nazwę hosta domeny i nazwę UPN dla logowania, a następnie uruchom je wszystkie za jednym razem.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-MsolService -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Kroki połączenia podczas korzystania z uwierzytelniania wieloskładnikowego

### <a name="azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory PowerShell dla Graph programu PowerShell

Oto wszystkie polecenia w jednym bloku umożliwiające połączenie się z wieloma usługami Microsoft 365 w przypadku korzystania z uwierzytelniania wieloskładnikowego w programie Azure Active Directory PowerShell dla Graph moduł.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```
### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory moduł Windows PowerShell modułu

Poniżej znajdują się wszystkie polecenia w jednym bloku umożliwiające połączenie się z wieloma Microsoft 365 w przypadku korzystania z uwierzytelniania wieloskładnikowego za pomocą modułu Microsoft Azure Active Directory dla Windows PowerShell moduł.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

## <a name="close-the-powershell-window"></a>Zamykanie okna programu PowerShell

Aby zamknąć okno programu PowerShell, uruchom to polecenie w celu usunięcia aktywnych sesji w celu SharePoint Online i Teams:
  
```powershell
Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="see-also"></a>Zobacz też

- [Połączenie do Microsoft 365 za pomocą programu PowerShell](connect-to-microsoft-365-powershell.md)
- [Zarządzanie usługą SharePoint Online za pomocą programu PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
