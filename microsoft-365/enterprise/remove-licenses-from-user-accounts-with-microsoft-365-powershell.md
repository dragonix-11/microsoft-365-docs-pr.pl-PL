---
title: Usuwanie licencji Microsoft 365 z kont użytkowników przy użyciu programu PowerShell
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Objaśnienie sposobu używania programu PowerShell do usuwania licencji Microsoft 365, które zostały wcześniej przypisane do użytkowników.
ms.openlocfilehash: b036f58686ac179fc93c1a0605ed2b585ea89c30
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096331"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>Usuwanie licencji Microsoft 365 z kont użytkowników przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

>[!Note]
>[Dowiedz się, jak usunąć licencje z kont użytkowników](../admin/manage/remove-licenses-from-users.md) przy użyciu Centrum administracyjne platformy Microsoft 365. Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Korzystanie z zestawu SDK programu PowerShell firmy Microsoft Graph

Najpierw [połącz się z dzierżawą Microsoft 365](/graph/powershell/get-started#authentication).

Przypisywanie i usuwanie licencji dla użytkownika wymaga zakresu uprawnień User.ReadWrite.All lub jednego z innych uprawnień wymienionych na [stronie odwołania interfejs Graph API "Przypisywanie licencji"](/graph/api/user-assignlicense).

Zakres uprawnień Organization.Read.All jest wymagany do odczytu licencji dostępnych w dzierżawie.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Aby wyświetlić informacje o planie licencjonowania w organizacji, zobacz następujące tematy:

- [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)

- [Wyświetlanie szczegółów licencji konta i usługi za pomocą programu PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)

### <a name="removing-licenses-from-user-accounts"></a>Usuwanie licencji z kont użytkowników

Aby usunąć licencje z istniejącego konta użytkownika, użyj następującej składni:
  
```powershell
Set-MgUserLicense -UserId "<Account>" -RemoveLicenses @("<AccountSkuId1>") -AddLicenses @{}
```

W tym przykładzie usunięto plan licencjonowania **SPE_E5** (Microsoft 365 E5) z **BelindaN@litwareinc.com** użytkownika:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -RemoveLicenses @($e5Sku.SkuId) -AddLicenses @{}
```

Aby usunąć wszystkie licencje z grupy istniejących licencjonowanych użytkowników, użyj następującej składni:

```powershell
$licensedUsers = Get-MgUser -Filter 'assignedLicenses/$count ne 0' `
    -ConsistencyLevel eventual -CountVariable licensedUserCount -All `
    -Select UserPrincipalName,DisplayName,AssignedLicenses

foreach($user in $licensedUsers)
{
    $licencesToRemove = $user.AssignedLicenses | Select -ExpandProperty SkuId
    $user = Set-MgUserLicense -UserId $user.UserPrincipalName -RemoveLicenses $licencesToRemove -AddLicenses @{} 
}
```

Innym sposobem zwolnienia licencji jest usunięcie konta użytkownika. Aby uzyskać więcej informacji, zobacz [Usuwanie i przywracanie kont użytkowników za pomocą programu PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

>Polecenie cmdlet Set-AzureADUserLicense ma zostać wycofane. Zmigruj skrypty do polecenia cmdlet Set-MgUserLicense zestawu Microsoft Graph SDK zgodnie z powyższym opisem. Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji w celu uzyskania dostępu do interfejsów API zarządzania licencjami z usługi Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Następnie wyświetl listę planów licencji dla dzierżawy za pomocą tego polecenia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie pobierz nazwę logowania konta, dla którego chcesz usunąć licencję, znaną również jako główna nazwa użytkownika (UPN).

Na koniec określ nazwy logowania użytkownika i planu licencji, usuń znaki "<" i ">" i uruchom te polecenia.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

Aby usunąć wszystkie licencje dla określonego konta użytkownika, określ nazwę logowania użytkownika, usuń znaki "<" i ">" i uruchom te polecenia.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userList = Get-AzureADUser -ObjectID $userUPN
$Skus = $userList | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
    if($Skus -is [array])
    {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        for ($i=0; $i -lt $Skus.Count; $i++) {
            $licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

>[!Note]
>Polecenia cmdlet Set-MsolUserLicense i New-MsolUser (-LicenseAssignment) mają zostać wycofane. Zmigruj skrypty do polecenia cmdlet Set-MgUserLicense zestawu Microsoft Graph SDK zgodnie z powyższym opisem. Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji w celu uzyskania dostępu do interfejsów API zarządzania licencjami z usługi Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Aby wyświetlić informacje o planie licencjonowania (**AccountSkuID**) w organizacji, zobacz następujące tematy:
    
  - [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [Wyświetlanie szczegółów licencji konta i usługi za pomocą programu PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
Jeśli używasz polecenia cmdlet **Get-MsolUser** bez użycia parametru _-All_ , zwracanych jest tylko pierwsze 500 kont.
    
### <a name="removing-licenses-from-user-accounts"></a>Usuwanie licencji z kont użytkowników

Aby usunąć licencje z istniejącego konta użytkownika, użyj następującej składni:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

W tym przykładzie usunięto licencję **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) z konta użytkownika BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Nie można użyć `Set-MsolUserLicense` polecenia cmdlet, aby anulować przypisanie użytkowników z *anulowanych* licencji. Należy to zrobić indywidualnie dla każdego konta użytkownika w Centrum administracyjne platformy Microsoft 365.
>

Aby usunąć wszystkie licencje z grupy istniejących licencjonowanych użytkowników, użyj jednej z następujących metod:
  
- **Filtrowanie kont na podstawie istniejącego atrybutu konta** W tym celu użyj następującej składni:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

W tym przykładzie wszystkie licencje są usuwane ze wszystkich kont użytkowników w dziale sprzedaży w Stany Zjednoczone.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Używanie listy określonych kont dla określonej licencji** W tym celu wykonaj następujące kroki:
    
1. Utwórz i zapisz plik tekstowy zawierający jedno konto w każdym wierszu w następujący sposób:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Należy stosować następującą składnię:
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
W tym przykładzie **usunięto licencję litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) z kont użytkowników zdefiniowanych w pliku tekstowym C:\My Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Aby usunąć wszystkie licencje ze wszystkich istniejących kont użytkowników, użyj następującej składni:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Innym sposobem zwolnienia licencji jest usunięcie konta użytkownika. Aby uzyskać więcej informacji, zobacz [Usuwanie i przywracanie kont użytkowników za pomocą programu PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
