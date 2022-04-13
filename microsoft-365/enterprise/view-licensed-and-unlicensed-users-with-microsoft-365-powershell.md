---
title: Wyświetlanie licencjonowanych i nielicencjonowanych użytkowników Microsoft 365 przy użyciu programu PowerShell
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
description: W tym artykule wyjaśniono, jak używać programu PowerShell do wyświetlania licencjonowanych i nielicencjonowanych kont użytkowników Microsoft 365.
ms.openlocfilehash: 1be54b20d3b50985fea8eb665a1b6098a26aa703
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823636"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Wyświetlanie licencjonowanych i nielicencjonowanych użytkowników Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Konta użytkowników w organizacji Microsoft 365 mogą mieć przypisane niektóre, wszystkie lub żadne z dostępnych licencji z planów licencjonowania dostępnych w organizacji. Program PowerShell umożliwia Microsoft 365 szybkie znajdowanie licencjonowanych i nielicencjonowanych użytkowników w organizacji.

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Korzystanie z zestawu SDK programu PowerShell firmy Microsoft Graph

Najpierw [połącz się z dzierżawą Microsoft 365](/graph/powershell/get-started#authentication).

Odczytywanie właściwości użytkownika, w tym szczegółów licencji, wymaga zakresu uprawnień User.Read.All lub jednego z innych uprawnień wymienionych na [stronie odwołania interfejs Graph API "Pobierz użytkownika"](/graph/api/user-get).

Zakres uprawnień Organization.Read.All jest wymagany do odczytu licencji dostępnych w dzierżawie.

```powershell
Connect-Graph -Scopes User.Read.All, Organization.Read.All
```

Aby wyświetlić szczegóły licencji określonego konta użytkownika, uruchom następujące polecenie:
  
```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Przykład:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których nie przypisano żadnego z planów licencjonowania (nielicencjonowanych użytkowników), uruchom następujące polecenie:
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users."
```

Aby wyświetlić listę wszystkich kont użytkowników członkowskich (z wyłączeniem gości) w organizacji, do których nie przypisano żadnego z planów licencjonowania (nielicencjonowanych użytkowników), uruchom następujące polecenie:
  
```powershell
Get-MgUser -Filter "assignedLicenses/`$count eq 0 and userType eq 'Member'" -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users (excluding guests)."
```

Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których przypisano dowolne plany licencjonowania (licencjonowani użytkownicy), uruchom następujące polecenie:
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count ne 0' -ConsistencyLevel eventual -CountVariable licensedUserCount -All -Select UserPrincipalName,DisplayName,AssignedLicenses | Format-Table -Property UserPrincipalName,DisplayName,AssignedLicenses

Write-Host "Found $licensedUserCount licensed users."
```

Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których przypisano licencję E5, uruchom następujące polecenie:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

Get-MgUser -Filter "assignedLicenses/any(x:x/skuId eq $($e5sku.SkuId) )" -ConsistencyLevel eventual -CountVariable e5licensedUserCount -All

Write-Host "Found $e5licensedUserCount E5 licensed users."
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których nie przypisano żadnego z planów licencjonowania (nielicencjonowanych użytkowników), uruchom następujące polecenie:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Aby wyświetlić listę wszystkich kont użytkowników w organizacji, do których przypisano dowolne plany licencjonowania (licencjonowani użytkownicy), uruchom następujące polecenie:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Aby wyświetlić listę wszystkich użytkowników w subskrypcji, użyj `Get-AzureAdUser -All $true` polecenia .
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Aby wyświetlić listę wszystkich kont użytkowników i ich stan licencjonowania w organizacji, uruchom następujące polecenie w programie PowerShell:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
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

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
