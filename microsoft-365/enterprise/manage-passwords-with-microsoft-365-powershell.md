---
title: Zarządzanie hasłami za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
description: Dowiedz się, jak zarządzać hasłami przy użyciu programu PowerShell.
ms.openlocfilehash: 64c46f774db2ae2153ea336b8afb1f1aa7536d94
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959564"
---
# <a name="manage-passwords-with-powershell"></a>Zarządzanie hasłami za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Programu PowerShell dla Microsoft 365 można używać jako alternatywy dla centrum administracyjne platformy Microsoft 365 zarządzania hasłami w Microsoft 365. 

Jeśli blok poleceń w tym artykule wymaga określenia wartości zmiennych, należy wykonać poniższe czynności.

1. Skopiuj blok polecenia do schowka i wklej go do Notatnik lub środowiska PowerShell Integrated Script Environment (ISE).
2. Wypełnij wartości zmiennych i usuń znaki "<" i ">".
3. Uruchom polecenia w oknie programu PowerShell lub w oknie programu PowerShell ISE.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="set-a-password"></a>Ustawianie hasła

Użyj tych poleceń, aby określić hasło dla konta użytkownika.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword
```
### <a name="force-a-user-to-change-their-password"></a>Wymuszanie zmiany hasła przez użytkownika

Użyj tych poleceń, aby ustawić hasło i wymusić zmianę nowego hasła przez użytkownika.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -EnforceChangePasswordPolicy $true
```

Użyj tych poleceń, aby ustawić hasło i wymusić zmianę nowego hasła przez użytkownika, gdy zaloguje się następnym razem.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -ForceChangePasswordNextLogin $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="set-a-password"></a>Ustawianie hasła

Użyj tych poleceń, aby określić hasło dla konta użytkownika.

```powershell
$userUPN="<user account sign in name>"
$newPassword="<new password>"
Set-MsolUserPassword -UserPrincipalName $userUPN -NewPassword $newPassword
```

### <a name="force-a-user-to-change-their-password"></a>Wymuszanie zmiany hasła przez użytkownika

Użyj tych poleceń, aby wymusić zmianę hasła przez użytkownika.

```powershell
$userUPN="<user account sign in name>"
Set-MsolUserPassword -UserPrincipalName $userUPN -ForceChangePassword $true
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)

