---
title: Przypisywanie licencji Microsoft 365 do kont użytkowników przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: W tym artykule dowiesz się, jak przy użyciu programu PowerShell przypisać licencję Microsoft 365 do nielicencjonowanych użytkowników.
ms.openlocfilehash: 7f01ac335941c2f7b0ba425f5aff963056ce0da8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091440"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Przypisywanie licencji Microsoft 365 do kont użytkowników przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Użytkownicy nie mogą korzystać z żadnych usług Microsoft 365, dopóki ich konto nie zostanie przypisane licencji z planu licencjonowania. Program PowerShell umożliwia szybkie przypisywanie licencji do nielicencjonowanych kont. 

Konta użytkowników muszą najpierw mieć przypisaną lokalizację. Określanie lokalizacji jest wymaganą częścią tworzenia nowego konta użytkownika w [Centrum administracyjne platformy Microsoft 365](../admin/add-users/add-users.md). 

Konta zsynchronizowane z usługami lokalna usługa Active Directory Domain Services domyślnie nie mają określonej lokalizacji. Lokalizację dla tych kont można skonfigurować z następujących elementów:

- Centrum administracyjne platformy Microsoft 365
- [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
- [Azure Portal](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Active DirectoryUżytkownicy** >  > konto użytkownika > **ProfileKontakt** >  **infoCountry** >  lub region).

>[!Note]
>[Dowiedz się, jak przypisywać licencje do kont użytkowników](../admin/manage/assign-licenses-to-users.md) przy użyciu Centrum administracyjne platformy Microsoft 365. Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Korzystanie z zestawu SDK programu PowerShell firmy Microsoft Graph

Najpierw [połącz się z dzierżawą Microsoft 365](/graph/powershell/get-started#authentication).

Przypisywanie i usuwanie licencji dla użytkownika wymaga zakresu uprawnień User.ReadWrite.All lub jednego z innych uprawnień wymienionych na [stronie odwołania interfejs Graph API "Przypisywanie licencji"](/graph/api/user-assignlicense).

Zakres uprawnień Organization.Read.All jest wymagany do odczytu licencji dostępnych w dzierżawie.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Uruchom polecenie , `Get-MgSubscribedSku` aby wyświetlić dostępne plany licencjonowania i liczbę dostępnych licencji w każdym planie w organizacji. Liczba dostępnych licencji w każdym planie to ActiveUnitsWarningUnitsConsumedUnits -  - . Aby uzyskać więcej informacji na temat planów licencjonowania, licencji i usług, zobacz [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

Aby znaleźć nielicencjonowane konta w organizacji, uruchom to polecenie.

```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All
```

Licencje można przypisywać tylko do kont użytkowników, które mają właściwość **UsageLocation** ustawioną na prawidłowy kod kraju ISO 3166-1 alfa-2. Na przykład stany USA dla Stany Zjednoczone i FR dla Francji. Niektóre usługi Microsoft 365 nie są dostępne w niektórych krajach. Aby uzyskać więcej informacji, zobacz [About license restrictions (Informacje o ograniczeniach licencji](https://go.microsoft.com/fwlink/p/?LinkId=691730)).

Aby znaleźć konta, które nie mają wartości **UsageLocation** , uruchom to polecenie.

```powershell
Get-MgUser -Select Id,DisplayName,Mail,UserPrincipalName,UsageLocation,UserType | where { $_.UsageLocation -eq $null -and $_.UserType -eq 'Member' }
```

Aby ustawić wartość **UsageLocation** na koncie, uruchom to polecenie.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"

Update-MgUser -UserId $userUPN -UsageLocation $userLoc
```

Przykład:

```powershell
Update-MgUser -UserId "belindan@litwareinc.com" -UsageLocation US
```

Jeśli używasz polecenia cmdlet **Get-MgUser** bez użycia parametru **-All** , zwracanych jest tylko pierwsze 100 kont.

### <a name="assigning-licenses-to-user-accounts"></a>Przypisywanie licencji do kont użytkowników

Aby przypisać licencję do użytkownika, użyj następującego polecenia w programie PowerShell.
  
```powershell
Set-MgUserLicense -UserId $userUPN -AddLicenses @{SkuId = "<SkuId>"} -RemoveLicenses @()
```

W tym przykładzie przypisano licencję z planu licencjonowania **SPE_E5** (Microsoft 365 E5) do nielicencjonowanego użytkownika **belindan\@ litwareinc.com**:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Ten przykład przypisuje **SPE_E5** (Microsoft 365 E5) i **EMSPREMIUM** (ENTERPRISE MOBILITY + SECURITY E5) do użytkownika **belindan\@ litwareinc.com**:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$e5EmsSku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'EMSPREMIUM'
$addLicenses = @(
    @{SkuId = $e5Sku.SkuId},
    @{SkuId = $e5EmsSku.SkuId}
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

W tym przykładzie przypisano **SPE_E5** (Microsoft 365 E5) z wyłączonymi usługami **MICROSOFTBOOKINGS** (Microsoft Bookings) i **LOCKBOX_ENTERPRISE** (Customer Lockbox):
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

W tym przykładzie użytkownik jest aktualizowany przy użyciu **SPE_E5** (Microsoft 365 E5) i wyłącza plany usług Sway i Forms, pozostawiając istniejące wyłączone plany użytkownika w bieżącym stanie:
  
```powershell
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

### <a name="assign-licenses-to-a-user-by-copying-the-license-assignment-from-another-user"></a>Przypisywanie licencji do użytkownika przez skopiowanie przypisania licencji od innego użytkownika

W tym przykładzie przypisano **litwareinc.com jamesp\@** z tym samym planem licencjonowania, który został zastosowany do **aplikacji belindan\@ litwareinc.com**:

```powershell
$mgUser = Get-MgUser -UserId "belindan@litwareinc.com"
Set-MgUserLicense -UserId "jamesp@litwareinc.com" -AddLicenses $mgUser.AssignedLicenses -RemoveLicenses @()
```

### <a name="move-a-user-to-a-different-subscription-license-plan"></a>Przenoszenie użytkownika do innej subskrypcji (plan licencji)

W tym przykładzie uaktualnia użytkownika z planu licencjonowania **SPE_E3** (Microsoft 365 E3) do planu licencjonowania **SPE_E5** (Microsoft 365 E5):

```powershell
$e3Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E3'
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

# Unassign E3
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{} -RemoveLicenses @($e3Sku.SkuId)
# Assign E5
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Możesz zweryfikować zmianę subskrypcji dla konta użytkownika za pomocą tego polecenia.

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

>[!Note]
>Polecenie cmdlet Set-AzureADUserLicense ma zostać wycofane. Zmigruj skrypty do polecenia cmdlet Set-MgUserLicense zestawu Microsoft Graph SDK zgodnie z powyższym opisem. Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji w celu uzyskania dostępu do interfejsów API zarządzania licencjami z usługi Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Następnie wyświetl listę planów licencji dla dzierżawy za pomocą tego polecenia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie pobierz nazwę logowania konta, do którego chcesz dodać licencję, znaną również jako główna nazwa użytkownika (UPN).

Następnie upewnij się, że konto użytkownika ma przypisaną lokalizację użycia.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Jeśli nie przypisano lokalizacji użycia, możesz przypisać ją za pomocą następujących poleceń:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Na koniec określ nazwę logowania użytkownika i nazwę planu licencji i uruchom te polecenia.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

>[!Note]
>Polecenia cmdlet Set-MsolUserLicense i New-MsolUser (-LicenseAssignment) mają zostać wycofane. Zmigruj skrypty do polecenia cmdlet Set-MgUserLicense zestawu Microsoft Graph SDK zgodnie z powyższym opisem. Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji w celu uzyskania dostępu do interfejsów API zarządzania licencjami z usługi Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Uruchom polecenie , `Get-MsolAccountSku` aby wyświetlić dostępne plany licencjonowania i liczbę dostępnych licencji w każdym planie w organizacji. Liczba dostępnych licencji w każdym planie to ActiveUnitsWarningUnitsConsumedUnits -  - . Aby uzyskać więcej informacji na temat planów licencjonowania, licencji i usług, zobacz [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

Aby znaleźć nielicencjonowane konta w organizacji, uruchom to polecenie.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Licencje można przypisywać tylko do kont użytkowników, które mają właściwość **UsageLocation** ustawioną na prawidłowy kod kraju ISO 3166-1 alfa-2. Na przykład stany USA dla Stany Zjednoczone i FR dla Francji. Niektóre usługi Microsoft 365 nie są dostępne w niektórych krajach. Aby uzyskać więcej informacji, zobacz [About license restrictions (Informacje o ograniczeniach licencji](https://go.microsoft.com/fwlink/p/?LinkId=691730)).
    
Aby znaleźć konta, które nie mają wartości **UsageLocation** , uruchom to polecenie.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Aby ustawić wartość **UsageLocation** na koncie, uruchom to polecenie.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Przykład:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Jeśli używasz polecenia cmdlet **Get-MsolUser** bez użycia parametru **-All** , zwracanych jest tylko pierwsze 500 kont.

### <a name="assigning-licenses-to-user-accounts"></a>Przypisywanie licencji do kont użytkowników
    
Aby przypisać licencję do użytkownika, użyj następującego polecenia w programie PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

W tym przykładzie przypisano licencję z planu licencjonowania **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) do nielicencjonowanego użytkownika **belindan\@ litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Aby przypisać licencję wszystkim nielicencjonowanym użytkownikom, uruchom to polecenie.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Nie można przypisać wielu licencji do użytkownika z tego samego planu licencjonowania. Jeśli nie masz wystarczającej liczby dostępnych licencji, licencje są przypisywane do użytkowników w kolejności, w której są one zwracane przez polecenie cmdlet **Get-MsolUser** do momentu wygaśnięcia dostępnych licencji.
>

W tym przykładzie przypisano licencje z planu licencjonowania **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) wszystkim nielicencjonowanym użytkownikom:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

W tym przykładzie te same licencje są przypisywane do nielicencjonowanych użytkowników w dziale sprzedaży w Stany Zjednoczone:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Przenoszenie użytkownika do innej subskrypcji (planu licencji) za pomocą modułu Azure Active Directory Programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Następnie pobierz nazwę logowania konta użytkownika, dla którego chcesz przełączyć subskrypcje, znaną również jako główna nazwa użytkownika (UPN).

Następnie wyświetl listę subskrypcji (planów licencji) dzierżawy za pomocą tego polecenia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie wyświetl listę subskrypcji aktualnie posiadanych przez konto użytkownika za pomocą tych poleceń.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Zidentyfikuj subskrypcję aktualnie posiadanej przez użytkownika (subskrypcję FROM) i subskrypcję, do której przechodzi użytkownik (subskrypcja TO).

Na koniec określ nazwy subskrypcji TO i FROM (numery części jednostki SKU) i uruchom te polecenia.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Możesz zweryfikować zmianę subskrypcji konta użytkownika za pomocą tych poleceń.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
