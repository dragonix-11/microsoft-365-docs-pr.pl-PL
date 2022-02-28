---
title: Przypisywanie Microsoft 365 do kont użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Z tego artykułu dowiesz się, jak za pomocą programu PowerShell przypisać licencję programu Microsoft 365 nielicencjonowani użytkownikom.
ms.openlocfilehash: b9f076e4856820d9f10e4cf92718dd6ddd3971c5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985300"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Przypisywanie Microsoft 365 do kont użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Użytkownicy nie mogą korzystać z żadnych Microsoft 365 licencji, dopóki ich konto nie zostanie przypisane w planie licencjonowania. Za pomocą programu PowerShell możesz szybko przypisywać licencje do nielicencjonowanych kont. 

Do kont użytkowników musi najpierw zostać przypisana lokalizacja. Określenie lokalizacji jest wymaganą częścią tworzenia nowego konta użytkownika w [centrum administracyjne platformy Microsoft 365.](../admin/add-users/add-users.md) 

Konta synchronizowane z lokalizacji Usługi domenowe w usłudze Active Directory nie mają domyślnie określonej lokalizacji. Lokalizację dla tych kont można skonfigurować w następującej lokalizacji:

- The centrum administracyjne platformy Microsoft 365
 - [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
 - Azure [Portal](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Active** **DirectoryUsers** >  > konta użytkownika > **ProfileKontakt** >  **infoCountry** >  **lub region**).

>[!Note]
>[Dowiedz się, jak przypisywać licencje do kont użytkowników przy](../admin/manage/assign-licenses-to-users.md) użyciu centrum administracyjne platformy Microsoft 365. Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Następnie, za pomocą tego polecenia, wywszukaj listę planów licencji dla dzierżawy.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie uzyskaj nazwę logowania dla konta, do którego chcesz dodać licencję, znaną także jako główna nazwa użytkownika (UPN).

Następnie upewnij się, że do konta użytkownika przypisano lokalizację użytkowania.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Jeśli lokalizacja użytkowania nie jest przypisana, możesz przypisać ją za pomocą tych poleceń:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Na koniec określ nazwę logowania użytkownika i nazwę planu licencji, a następnie uruchom te polecenia.

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

Pamiętaj, że zaczniemy wy przestać korzystać z tego modułu, gdy jego funkcje będą dostępne w nowszej wersji programu [Azure Active Directory PowerShell dla Graph](/powershell/azuread/v2/azureactivedirectory) moduł. Zalecamy klientom, którzy tworzą nowe skrypty programu PowerShell, korzystanie z nowszego modułu zamiast tego modułu.

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Uruchom to `Get-MsolAccountSku` polecenie, aby wyświetlić dostępne plany licencjonowania oraz liczbę dostępnych licencji w każdym planie w organizacji. Liczba dostępnych licencji w każdym planie to **ActiveUnitsWarningUnitsConsumedUnits** -  - . Aby uzyskać więcej informacji o planach licencjonowania, licencjach i usługach, zobacz Wyświetlanie licencji [i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

Aby znaleźć nielicencjonowane konta w organizacji, uruchom to polecenie.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Licencje można przypisywać tylko do kont użytkowników, dla których właściwość **UsageLocation** (Lokalizacja użytkowania) jest ustawiona na prawidłowy kod kraju ISO 3166-1 alfa-2. Na przykład STANY ZJEDNOCZONE, a FR dla Francji. Niektóre Microsoft 365 są niedostępne w niektórych krajach. Aby uzyskać więcej informacji, zobacz [Informacje o ograniczeniach licencyjnych](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Aby znaleźć konta, które nie mają wartości **Lokalizacja** użytkowania, uruchom to polecenie.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Aby ustawić **wartość UsageLocation (Lokalizacja** użytkowania) dla konta, uruchom to polecenie.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Przykład:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Jeśli używasz polecenia **cmdlet Get-MsolUser** bez użycia parametru **-All** , zwracanych jest tylko pierwszych 500 kont.

### <a name="assigning-licenses-to-user-accounts"></a>Przypisywanie licencji do kont użytkowników
    
Aby przypisać licencję do użytkownika, użyj następującego polecenia w programie PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

W tym przykładzie licencja z planu licencjonowania **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) jest przypisywana nielicencjonowaneowi użytkownikowi **Belindan\@ litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Aby przypisać licencję do wszystkich nielicencjonowanych użytkowników, uruchom to polecenie.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Nie można przypisać wielu licencji do użytkownika z tego samego planu licencjonowania. Jeśli nie masz wystarczającej ilości dostępnych licencji, licencje są przypisywane do użytkowników w kolejności zwracanych przez polecenie cmdlet **Get-MsolUser** , dopóki dostępne licencje nie wyczerują się.
>

W tym przykładzie licencje z planu licencjonowania **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) są przypisywane wszystkim nielicencjonowani użytkownikom:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

W tym przykładzie te same licencje są przypisywane do nielicencjonowanych użytkowników w dziale sprzedaży w Stanach Zjednoczonych:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Przenoszenie użytkownika do innej subskrypcji (planu licencji) za pomocą Azure Active Directory PowerShell dla Graph subskrypcji

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Następnie uzyskaj nazwę logowania do konta użytkownika, dla którego chcesz przełączyć subskrypcje, znaną również jako główna nazwa użytkownika (UPN).

Następnie wyeksskrybuj subskrypcje (plany licencji) dzierżawy za pomocą tego polecenia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie wynumeruj subskrypcje, które obecnie ma konto użytkownika z tymi poleceniami.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Określ subskrypcję posiadaną obecnie przez użytkownika (subskrypcję FROM) i subskrypcję, do której użytkownik jest przenoszący (subskrypcję TO).

Na koniec określ nazwy subskrypcji TO (TO) i FROM (numery części SKU) i uruchom te polecenia.

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

Za pomocą tych poleceń możesz sprawdzić zmianę w subskrypcji dla konta użytkownika.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie kontami użytkowników, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
