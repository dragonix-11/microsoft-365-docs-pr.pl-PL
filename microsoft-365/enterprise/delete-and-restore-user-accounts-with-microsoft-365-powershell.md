---
title: Usuwanie Microsoft 365 użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak używać różnych modułów w programie PowerShell w celu Microsoft 365 kont użytkowników.
ms.openlocfilehash: dc1e5c53f2d356f0585da5a0a5285b9af28dc8f0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985455"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Usuwanie Microsoft 365 użytkowników za pomocą programu PowerShell

Za pomocą programu PowerShell Microsoft 365 usuwać i przywracać konta użytkowników.

>[!Note]
>Dowiedz się[, jak przywrócić konto użytkownika](../admin/add-users/restore-user.md) przy użyciu centrum administracyjne platformy Microsoft 365.
>
>Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Po nawiązania połączenia usuń konto indywidualnego użytkownika przy użyciu następującej składni:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

W tym przykładzie usuwa się z konta *użytkownika fabricec\@ litwareinc.com*.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Parametr *-ObjectID* w poleceniach cmdlet **Remove-AzureADUser** przyjmuje nazwę logowania konta, znaną także jako główna nazwa użytkownika lub identyfikator obiektu konta.
  
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

W przypadku usunięcia konta użytkownika za pośrednictwem modułu Microsoft Azure Active Directory dla systemu Windows PowerShell konto nie zostanie trwale usunięte. Usunięte konto użytkownika możesz przywrócić w ciągu 30 dni.

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Aby usunąć konto użytkownika, użyj następującej składni:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z *nazwą Msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
>

W tym przykładzie konto użytkownika jest *BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Aby przywrócić usunięte konto użytkownika w 30-dniowym okresie prolongaty, użyj następującej składni:
  
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
> Jeśli oryginalna główna nazwa konta użytkownika jest używana przez inne konto, podczas przywracania konta użytkownika użyj parametru _NewUserPrincipalName_ zamiast nazwy _UserPrincipalName_ .


## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)