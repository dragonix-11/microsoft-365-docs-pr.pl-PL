---
title: Wyświetlanie Microsoft 365 licencji konta i usługi za pomocą programu PowerShell
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
description: W tym artykule wyjaśniono, jak za pomocą programu PowerShell Microsoft 365 usługi, które zostały przypisane do użytkowników.
ms.openlocfilehash: c02d3ffe2fff330f46adfc6b6dd49e553f69ad86
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988395"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>Wyświetlanie Microsoft 365 licencji konta i usługi za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W Microsoft 365 licencje z planów licencjonowania (nazywanych również jednostkami SKU lub planami Microsoft 365) zapewniają użytkownikom dostęp do usług Microsoft 365 zdefiniowanych dla tych planów. Użytkownik może jednak nie mieć dostępu do wszystkich usług dostępnych w obecnie przypisanej licencji. Za pomocą programu PowerShell Microsoft 365 wyświetlać stan usług na kontach użytkowników. 

Aby uzyskać więcej informacji na temat planów licencjonowania, licencji i usług, zobacz Wyświetlanie licencji [i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Następnie, za pomocą tego polecenia, wywszukaj listę planów licencji dla dzierżawy.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Użyj tych poleceń, aby wyświetlić listę usług dostępnych w poszczególnych planach licencjonowania.

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

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Następnie uruchom to polecenie, aby wyświetlić listę planów licencjonowania dostępnych w Twojej organizacji. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

Następnie uruchom to polecenie, aby wyświetlić listę usług dostępnych w poszczególnych planach licencjonowania oraz kolejność ich list (numer indeksu).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
To polecenie pozwala wyświetlić listę licencji przypisanych do użytkownika oraz kolejność ich numeracji (numer indeksu).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Aby wyświetlić usługi dla konta użytkownika

Aby wyświetlić wszystkie usługi Microsoft 365, do których użytkownik ma dostęp, użyj następującej składni:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

W tym przykładzie pokazano usługi, do których użytkownik BelindaN@litwareinc.com ma dostęp. To pokazuje usługi skojarzone ze wszystkimi licencjami przypisanymi do jej konta.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

W tym przykładzie pokazano usługi BelindaN@litwareinc.com do których użytkownik ma dostęp z pierwszej licencji przypisanej do jej konta (numer indeksu wynosi 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Aby wyświetlić wszystkie usługi dla użytkownika, który ma przypisanych *wiele* licencji, użyj następującej składni:

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

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
