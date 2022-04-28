---
title: Usuwanie kont użytkowników Microsoft 365 przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2020
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
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Dowiedz się, jak używać różnych modułów w programie PowerShell do usuwania Microsoft 365 kont użytkowników.
ms.openlocfilehash: b3d273e6f2274b43018848e5439f431281a54df8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093443"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Usuwanie kont użytkowników Microsoft 365 przy użyciu programu PowerShell

Program PowerShell umożliwia Microsoft 365 usuwanie i przywracanie kont użytkowników.

>[!Note]
>Dowiedz się, jak [przywrócić konto użytkownika](../admin/add-users/restore-user.md) przy użyciu Centrum administracyjne platformy Microsoft 365.
>
>Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Po nawiązaniu połączenia użyj następującej składni, aby usunąć pojedyncze konto użytkownika:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

W tym przykładzie usunięto sieć *szkieletową\@* konta użytkownika litwareinc.com.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Parametr *-ObjectID* w poleceniu cmdlet **Remove-AzureADUser** akceptuje nazwę logowania konta, znaną również jako główna nazwa użytkownika lub identyfikator obiektu konta.
  
Aby wyświetlić nazwę konta na podstawie nazwy użytkownika, użyj następujących poleceń:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

W tym przykładzie jest wyświetlana nazwa konta użytkownika *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Aby usunąć konto na podstawie nazwy wyświetlanej użytkownika, użyj następujących poleceń:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Po usunięciu konta użytkownika za pośrednictwem modułu Microsoft Azure Active Directory dla Windows PowerShell konto nie zostanie trwale usunięte. Usunięte konto użytkownika można przywrócić w ciągu 30 dni.

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Aby usunąć konto użytkownika, użyj następującej składni:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
>

W tym przykładzie usunięto *BelindaN@litwareinc.com* konta użytkownika.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Aby przywrócić usunięte konto użytkownika w ciągu 30-dniowego okresu prolongaty, użyj następującej składni:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

W tym przykładzie przywrócono usunięte konto *BelindaN\@ litwareinc.com*.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

>[!Note]
> Aby wyświetlić listę usuniętych użytkowników, których można przywrócić, uruchom następujące polecenie:
>    
> ```powershell
> Get-MsolUser -All -ReturnDeletedUsers
> ```
>
> Jeśli oryginalna główna nazwa użytkownika konta użytkownika jest używana przez inne konto, użyj _parametru NewUserPrincipalName_ zamiast _UserPrincipalName_ , aby określić inną główną nazwę użytkownika podczas przywracania konta użytkownika.


## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)