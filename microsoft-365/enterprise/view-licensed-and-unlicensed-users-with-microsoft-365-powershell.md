---
title: Wyświetlanie licencjonowanych i nielicencjonowanych użytkowników Microsoft 365 programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: W tym artykule wyjaśniono, jak wyświetlać licencjonowane i nielicencjonowane konta Microsoft 365 użytkowników za pomocą programu PowerShell.
ms.openlocfilehash: 015cb63fd692131d77799fe30fc94c6214bb01d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988369"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Wyświetlanie licencjonowanych i nielicencjonowanych użytkowników Microsoft 365 programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Konta użytkowników w Microsoft 365 organizacji mogą mieć przypisane niektóre, wszystkie lub żadna z dostępnych licencji z planów licencjonowania dostępnych w Twojej organizacji. Za pomocą programu PowerShell Microsoft 365 szybko znaleźć licencjonowanych i nielicencjonowanych użytkowników w organizacji.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których NIE przypisano żadnych planów licencjonowania (nielicencjonowani użytkownicy), uruchom następujące polecenie:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których przypisano dowolne plany licencjonowania (licencjonowani użytkownicy), uruchom następujące polecenie:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Użyj tego polecenia, aby wyświetlić listę wszystkich użytkowników w subskrypcji `Get-AzureAdUser -All $true` .
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Aby wyświetlić listę wszystkich kont użytkowników i ich stan licencjonowania w organizacji, uruchom następujące polecenie w programie PowerShell:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

Aby wyświetlić listę wszystkich nielicencjonowanych kont użytkowników w organizacji, uruchom następujące polecenie:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Aby wyświetlić listę wszystkich licencjonowanych kont użytkowników w organizacji, uruchom następujące polecenie:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
