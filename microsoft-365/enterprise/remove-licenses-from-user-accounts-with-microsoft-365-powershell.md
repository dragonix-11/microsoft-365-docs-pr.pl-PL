---
title: Usuwanie Microsoft 365 z kont użytkowników za pomocą programu PowerShell
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: W tym artykule wyjaśniono, jak za pomocą programu PowerShell Microsoft 365 wcześniej przypisanych użytkownikom licencje.
ms.openlocfilehash: 4aa40b4405dda07eea34151bd2fddcde0030e8b8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988634"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>Usuwanie Microsoft 365 z kont użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

>[!Note]
>[Dowiedz się, jak usuwać licencje z kont użytkowników](../admin/manage/remove-licenses-from-users.md) za pomocą centrum administracyjne platformy Microsoft 365. Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Następnie, za pomocą tego polecenia, wywszukaj listę planów licencji dla dzierżawy.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie uzyskaj nazwę logowania dla konta, dla którego chcesz usunąć licencję, znaną także jako główna nazwa użytkownika (UPN).

Na koniec określ nazwy logowania użytkownika i planu licencji, usuń znaki "<" i ">" i uruchom te polecenia.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
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
            $Licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Aby wyświetlić informacje dotyczące planu licencjonowania (**AccountSkuID**) w organizacji, zobacz następujące tematy:
    
  - [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [Wyświetlanie szczegółów licencji konta i usługi za pomocą programu PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
Jeśli używasz polecenia **cmdlet Get-MsolUser** bez użycia parametru _-All_ , zwracanych jest tylko pierwszych 500 kont.
    
### <a name="removing-licenses-from-user-accounts"></a>Usuwanie licencji z kont użytkowników

Aby usunąć licencje z istniejącego konta użytkownika, użyj następującej składni:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

W tym przykładzie licencja **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) jest usuwana z konta użytkownika BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Za pomocą polecenia `Set-MsolUserLicense` cmdlet nie można anulować przypisania użytkowników z *anulowanych* licencji. Musisz to zrobić indywidualnie dla każdego konta użytkownika w centrum administracyjne platformy Microsoft 365.
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

W tym przykładzie wszystkie licencje są usuwane ze wszystkich kont użytkowników w dziale sprzedaży w Stanach Zjednoczonych.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Używanie listy określonych kont dla określonej licencji** W tym celu wykonaj następujące czynności:
    
1. Utwórz i zapisz plik tekstowy, który zawiera jedno konto w każdym wierszu w ten sposób:
    
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
W tym przykładzie licencja **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) jest usuwana z kont użytkowników zdefiniowanych w pliku tekstowym C:\Mój Documents\Accounts.txt.
    
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

Innym sposobem na to, aby uwolnić licencję, jest usunięcie konta użytkownika. Aby uzyskać więcej informacji, [zobacz Usuwanie i przywracanie kont użytkowników za pomocą programu PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)