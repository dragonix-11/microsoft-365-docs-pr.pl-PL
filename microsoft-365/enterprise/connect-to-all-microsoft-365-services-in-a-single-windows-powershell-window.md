---
title: Połączenie do wszystkich usług Microsoft 365 w jednym oknie programu PowerShell
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
description: 'Podsumowanie: Połączenie do wszystkich usług Microsoft 365 w jednym oknie programu PowerShell.'
ms.openlocfilehash: babb5c308310e1444a2ac20b6557f4f7a2050f79
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016905"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Połączenie do wszystkich usług Microsoft 365 w jednym oknie programu PowerShell

W przypadku zarządzania Microsoft 365 za pomocą programu PowerShell można jednocześnie otworzyć wiele sesji programu PowerShell. Mogą istnieć różne okna programu PowerShell do zarządzania kontami użytkowników, SharePoint Online, Exchange Online, Microsoft Teams, funkcji Ochrona usługi Office 365 w usłudze Microsoft Defender (zabezpieczenia) i zgodności usługi Microsoft Purview Funkcje.

Ten scenariusz nie jest optymalny do zarządzania Microsoft 365, ponieważ nie można wymieniać danych między tymi oknami na potrzeby zarządzania między usługami. W tym artykule opisano sposób używania jednego wystąpienia programu PowerShell do zarządzania kontami Microsoft 365, Exchange Online, SharePoint Online, Microsoft Teams i funkcjami w Ochrona usługi Office 365 w usłudze Defender  Zgodność z usługą Microsoft Purview.

>[!Note]
>Ten artykuł zawiera obecnie tylko polecenia umożliwiające nawiązanie połączenia z chmurą na całym świecie (+GCC). Uwagi zawierają linki do artykułów dotyczących nawiązywania połączenia z innymi chmurami Microsoft 365.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem zarządzania wszystkimi Microsoft 365 z jednego wystąpienia programu PowerShell należy wziąć pod uwagę następujące wymagania wstępne:

- Używane konto Microsoft 365 służbowe musi być członkiem roli administratora Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../admin/add-users/about-admin-roles.md). Jest to wymóg programu PowerShell dla Microsoft 365, ale niekoniecznie dla wszystkich innych usług Microsoft 365.

- Możesz użyć następujących 64-bitowych wersji Windows:
  - System Windows 11
  - Windows 10
  - Windows 8,1 lub Windows 8
  - Windows Server 2019
  - Windows Server 2016
  - Windows Server 2012 R2 lub Windows Server 2012
  - Windows 7 dodatku Service Pack 1 (SP1)*
  - Windows Server 2008 R2 SP1*

    \*Musisz zainstalować usługę Microsoft .NET Framework 4.5.*x*, a następnie Windows Management Framework 3.0 lub 4.0. Aby uzyskać więcej informacji, zobacz [Windows Management Framework](/powershell/scripting/windows-powershell/wmf/overview).

- Należy zainstalować moduły wymagane do Azure Active Directory (Azure AD), Exchange Online, Ochrona usługi Office 365 w usłudze Defender, zgodności usługi Microsoft Purview, SharePoint Online i Teams:

  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [powłoka zarządzania SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [moduł programu PowerShell Teams](/microsoftteams/teams-powershell-overview)
  - [Exchange Online programu PowerShell w wersji 2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Teams omówienie programu PowerShell](/microsoftteams/teams-powershell-overview)

- Program PowerShell musi być skonfigurowany do uruchamiania podpisanych skryptów dla zgodności Exchange Online, Ochrona usługi Office 365 w usłudze Defender i Microsoft Purview. Uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (sesji programu PowerShell **uruchamianej jako administrator**).

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Kroki połączenia podczas korzystania tylko z hasła

Wykonaj następujące kroki, aby połączyć się ze wszystkimi usługami w jednym oknie programu PowerShell, gdy używasz tylko hasła do logowania.

1. Otwórz Windows PowerShell.

2. Uruchom to polecenie i wprowadź poświadczenia konta służbowego Microsoft 365.

   ```powershell
   $credential = Get-Credential
   ```

3. Uruchom to polecenie, aby nawiązać połączenie z Azure AD przy użyciu modułu Azure Active Directory Programu PowerShell dla Graph.

   ```powershell
   Connect-AzureAD -Credential $credential
   ```

   Jeśli używasz modułu Microsoft Azure Active Directory dla modułu Windows PowerShell, uruchom to polecenie.

   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!NOTE]
   > Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. Należy uruchomić te polecenia cmdlet z programu PowerShell.

4. Uruchom te polecenia, aby nawiązać połączenie z usługą SharePoint Online. Określ nazwę organizacji dla domeny. Na przykład dla "litwareinc\.onmicrosoft.com" wartość nazwy organizacji to "litwareinc".

   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. Uruchom te polecenia, aby nawiązać połączenie z Exchange Online.

   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -ShowProgress $true
   ```

   > [!Note]
   > Aby nawiązać połączenie z Exchange Online dla chmur Microsoft 365 innych niż na całym świecie, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. Uruchom te polecenia, aby nawiązać połączenie z programem PowerShell security & Compliance.

   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!NOTE]
   > Aby nawiązać połączenie z programem PowerShell zgodności & zabezpieczeń dla chmur Microsoft 365 innych niż światowe, zobacz Połączenie do programu [PowerShell & Zgodności z zabezpieczeniami](/powershell/exchange/connect-to-scc-powershell).

7. Uruchom te polecenia, aby nawiązać połączenie z programem Teams programu PowerShell.

   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```

   > [!NOTE]
   > Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams programu PowerShell. Jeśli używasz najnowszej Teams publicznej wersji programu PowerShell, nie musisz instalować łącznika usługi Skype dla firm Online.
   >
   > Aby nawiązać połączenie z chmurami Microsoft Teams innymi niż *światowe*, zobacz [Połączenie-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).

### <a name="azure-active-directory-powershell-for-graph-module-when-using-just-a-password"></a>Azure Active Directory programu PowerShell dla modułu Graph podczas używania tylko hasła

Poniżej przedstawiono polecenia dla wszystkich usług w jednym bloku podczas korzystania z Azure Active Directory programu PowerShell dla modułu Graph. Określ nazwę hosta domeny i nazwę UPN dla logowania i uruchom je wszystkie w tym samym czasie.

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
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-just-a-password"></a>Microsoft Azure Active Directory Module for Windows PowerShell module when using just a password (Moduł Microsoft Azure Active Directory dla Windows PowerShell podczas używania tylko hasła)

Poniżej przedstawiono polecenia dla wszystkich usług w jednym bloku podczas korzystania z modułu Microsoft Azure Active Directory dla modułu Windows PowerShell. Określ nazwę hosta domeny i nazwę UPN dla logowania i uruchom je wszystkie jednocześnie.

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
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Kroki połączenia podczas korzystania z uwierzytelniania wieloskładnikowego

### <a name="azure-active-directory-powershell-for-graph-module-when-using-mfa"></a>Azure Active Directory programu PowerShell dla modułu Graph podczas korzystania z uwierzytelniania wieloskładnikowego

Poniżej przedstawiono wszystkie polecenia w jednym bloku umożliwiające nawiązanie połączenia z wieloma usługami Microsoft 365 w przypadku korzystania z uwierzytelniania wieloskładnikowego za pomocą Azure Active Directory programu PowerShell dla modułu Graph.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-mfa"></a>moduł Microsoft Azure Active Directory dla modułu Windows PowerShell podczas korzystania z uwierzytelniania wieloskładnikowego

Poniżej przedstawiono wszystkie polecenia w jednym bloku służące do nawiązywania połączenia z wieloma usługami Microsoft 365 podczas korzystania z uwierzytelniania wieloskładnikowego z modułem Microsoft Azure Active Directory dla modułu Windows PowerShell.

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

Aby zamknąć okno programu PowerShell, uruchom to polecenie, aby usunąć aktywne sesje w usłudze SharePoint Online, Teams, Ochrona usługi Office 365 w usłudze Defender i zgodności usługi Microsoft Purview:

```powershell
Disconnect-SPOService; Disconnect-MicrosoftTeams; Disconnect-ExchangeOnline
```

## <a name="see-also"></a>Zobacz też

- [Połączenie z platformą Microsoft 365 za pomocą programu PowerShell](connect-to-microsoft-365-powershell.md)
- [Zarządzanie SharePoint Online przy użyciu programu PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
