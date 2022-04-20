---
title: Wyświetlanie licencji Microsoft 365 konta i szczegółów usługi za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Objaśnienie sposobu używania programu PowerShell do określania usług Microsoft 365, które zostały przypisane do użytkowników.
ms.openlocfilehash: 7e5724acbff571825f1496db5d59e04e11ba3a67
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916000"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>Wyświetlanie licencji Microsoft 365 konta i szczegółów usługi za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W Microsoft 365 licencje z planów licencjonowania (nazywane również jednostkami SKU lub planami Microsoft 365) zapewniają użytkownikom dostęp do usług Microsoft 365 zdefiniowanych dla tych planów. Jednak użytkownik może nie mieć dostępu do wszystkich usług, które są dostępne w licencji, która jest obecnie do niego przypisana. Program PowerShell umożliwia Microsoft 365 wyświetlanie stanu usług na kontach użytkowników.

Aby uzyskać więcej informacji na temat planów licencjonowania, licencji i usług, zobacz [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Korzystanie z zestawu SDK programu PowerShell firmy Microsoft Graph

Najpierw [połącz się z dzierżawą Microsoft 365](/graph/powershell/get-started#authentication).

Odczytywanie właściwości użytkownika, w tym szczegółów licencji, wymaga zakresu uprawnień User.Read.All lub jednego z innych uprawnień wymienionych na [stronie odwołania interfejs Graph API "Pobierz użytkownika"](/graph/api/user-get).

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Następnie wyświetl listę planów licencji dla dzierżawy za pomocą tego polecenia.

```powershell
Get-MgSubscribedSku
```

Użyj tych poleceń, aby wyświetlić listę usług dostępnych w każdym planie licencjonowania.

```powershell

$allSKUs = Get-MgSubscribedSku -Property SkuPartNumber, ServicePlans 
$allSKUs | ForEach-Object {
    Write-Host "Service Plan:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

Użyj tych poleceń, aby wyświetlić listę licencji przypisanych do konta użytkownika.

```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Przykład:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

### <a name="to-view-services-for-a-user-account"></a>Aby wyświetlić usługi dla konta użytkownika

Aby wyświetlić wszystkie usługi Microsoft 365, do których użytkownik ma dostęp, użyj następującej składni:
  
```powershell
(Get-MgUserLicenseDetail -UserId <user account UPN> -Property ServicePlans)[<LicenseIndexNumber>].ServicePlans
```

W tym przykładzie przedstawiono usługi, do których użytkownik BelindaN@litwareinc.com ma dostęp. Spowoduje to wyświetlenie usług skojarzonych ze wszystkimi licencjami przypisanymi do jej konta.
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans).ServicePlans
```

W tym przykładzie pokazano usługi, do których użytkownik BelindaN@litwareinc.com ma dostęp z pierwszej licencji przypisanej do jej konta (numer indeksu to 0).
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans)[0].ServicePlans
```

Aby wyświetlić wszystkie usługi dla użytkownika, któremu przypisano *wiele licencji*, użyj następującej składni:

```powershell
$userUPN="<user account UPN>"
$allLicenses = Get-MgUserLicenseDetail -UserId $userUPN -Property SkuPartNumber, ServicePlans
$allLicenses | ForEach-Object {
    Write-Host "License:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Następnie wyświetl listę planów licencji dla dzierżawy za pomocą tego polecenia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Użyj tych poleceń, aby wyświetlić listę usług dostępnych w każdym planie licencjonowania.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Użyj tych poleceń, aby wyświetlić listę licencji przypisanych do konta użytkownika.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Następnie uruchom to polecenie, aby wyświetlić listę planów licencjonowania dostępnych w organizacji. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

Następnie uruchom to polecenie, aby wyświetlić listę usług dostępnych w każdym planie licencjonowania oraz kolejność ich wyświetlania (numer indeksu).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Użyj tego polecenia, aby wyświetlić listę licencji przypisanych do użytkownika oraz kolejność ich wyświetlania (numer indeksu).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Aby wyświetlić usługi dla konta użytkownika

Aby wyświetlić wszystkie usługi Microsoft 365, do których użytkownik ma dostęp, użyj następującej składni:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

W tym przykładzie przedstawiono usługi, do których użytkownik BelindaN@litwareinc.com ma dostęp. Spowoduje to wyświetlenie usług skojarzonych ze wszystkimi licencjami przypisanymi do jej konta.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

W tym przykładzie pokazano usługi, do których użytkownik BelindaN@litwareinc.com ma dostęp z pierwszej licencji przypisanej do jej konta (numer indeksu to 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Aby wyświetlić wszystkie usługi dla użytkownika, któremu przypisano *wiele licencji*, użyj następującej składni:

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
