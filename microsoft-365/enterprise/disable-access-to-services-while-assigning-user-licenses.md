---
title: Wyłączanie dostępu do usług Microsoft 365 podczas przypisywania licencji użytkowników
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Dowiedz się, jak przypisywać licencje do kont użytkowników i wyłączać określone plany usług w tym samym czasie przy użyciu programu PowerShell dla Microsoft 365.
ms.openlocfilehash: 6c0c3a3860da8a1935152fcaefb29f2f355cfa49
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095735"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Wyłączanie dostępu do usług Microsoft 365 podczas przypisywania licencji użytkowników

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 subskrypcje są wyposażone w plany usług dla poszczególnych usług. Microsoft 365 administratorzy często muszą wyłączać niektóre plany podczas przypisywania licencji do użytkowników. Instrukcje przedstawione w tym artykule umożliwiają przypisanie licencji Microsoft 365 podczas wyłączania określonych planów usług przy użyciu programu PowerShell dla pojedynczego konta użytkownika lub wielu kont użytkowników.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Następnie wyświetl listę planów licencji dla dzierżawy za pomocą tego polecenia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie pobierz nazwę logowania konta, do którego chcesz dodać licencję, znaną również jako główna nazwa użytkownika (UPN).

Następnie skompiluj listę usług do włączenia. Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), ich dołączone plany usług i odpowiadające im przyjazne nazwy, zobacz [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

W poniższym bloku poleceń podaj główną nazwę użytkownika konta użytkownika, numer części jednostki SKU oraz listę planów usług umożliwiających włączenie i usunięcie tekstu objaśnienia oraz \< and > znaków. Następnie uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.

```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Następnie uruchom to polecenie, aby wyświetlić bieżące subskrypcje:

```powershell
Get-MsolAccountSku
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

Na ekranie  `Get-MsolAccountSku` polecenia:

- **AccountSkuId** to subskrypcja organizacji w \<OrganizationName>formacie :\<Subscription> Jest \<OrganizationName> to wartość podana podczas rejestracji w Microsoft 365 i jest unikatowa dla Twojej organizacji. Wartość \<Subscription> dotyczy określonej subskrypcji. Na przykład w przypadku oprogramowania litwareinc:ENTERPRISEPACK nazwa organizacji to litwareinc, a nazwa subskrypcji to ENTERPRISEPACK (Office 365 Enterprise E3).

- **ActiveUnits** to liczba licencji zakupionych dla subskrypcji.

- **WarningUnits** to liczba licencji w subskrypcji, która nie została odnowiona i wygaśnie po upływie 30-dniowego okresu prolongaty.

- **ConsumedUnits** to liczba licencji przypisanych do użytkowników subskrypcji.

Zanotuj identyfikator AccountSkuId dla subskrypcji Microsoft 365, która zawiera użytkowników, na których chcesz uzyskać licencję. Upewnij się również, że istnieje wystarczająca liczba licencji do przypisania (odejmowanie **jednostek ConsumedUnits** z **usługi ActiveUnits**).

Następnie uruchom to polecenie, aby wyświetlić szczegółowe informacje o planach usług Microsoft 365, które są dostępne we wszystkich subskrypcjach:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Na podstawie wyświetlania tego polecenia określ, które plany usług chcesz wyłączyć podczas przypisywania licencji do użytkowników.

Oto częściowa lista planów usług i odpowiadających im usług Microsoft 365.

W poniższej tabeli przedstawiono plany usług Microsoft 365 i ich przyjazne nazwy dla najpopularniejszych usług. Lista planów usług może być inna.

|**Plan usługi**|**Opis**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Aplikacje Microsoft 365 dla przedsiębiorstw *(wcześniej o nazwie Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype dla firm Online  <br/> |
| `SHAREPOINTWAC` <br/> |Pakiet Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online plan 2  <br/> |

Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), ich dołączone plany usług i odpowiadające im przyjazne nazwy, zobacz [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Teraz, gdy masz identyfikator AccountSkuId i plany usługi do wyłączenia, możesz przypisać licencje dla pojedynczego użytkownika lub wielu użytkowników.

### <a name="for-a-single-user"></a>Dla pojedynczego użytkownika

W przypadku pojedynczego użytkownika podaj główną nazwę użytkownika konta użytkownika, identyfikator AccountSkuId oraz listę planów usług, aby wyłączyć i usunąć tekst objaśnienia oraz \< and > znaki. Następnie uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

Oto przykładowy blok poleceń dla konta o nazwie belindan@contoso.com, licencji contoso:ENTERPRISEPACK, a plany usługi do wyłączenia to RMS_S_ENTERPRISE, SWAY, INTUNE_O365 i YAMMER_ENTERPRISE:

```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>Dla wielu użytkowników

Aby wykonać to zadanie administracyjne dla wielu użytkowników, utwórz plik tekstowy wartości rozdzielanej przecinkami (CSV), który zawiera pola UserPrincipalName i UsageLocation. Oto przykład:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Następnie wypełnij lokalizację wejściowych i wyjściowych plików CSV, identyfikator jednostki SKU konta oraz listę planów usług do wyłączenia, a następnie uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.

```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Ten blok poleceń programu PowerShell:

- Wyświetla główną nazwę użytkownika każdego użytkownika.

- Przypisuje dostosowane licencje do każdego użytkownika.

- Tworzy plik CSV ze wszystkimi użytkownikami, którzy zostali przetworzeni i pokazuje ich stan licencji.

## <a name="see-also"></a>Zobacz też

[Wyłączanie dostępu do usług Microsoft 365 przy użyciu programu PowerShell](disable-access-to-services-with-microsoft-365-powershell.md)

[Wyłączanie dostępu do Sway przy użyciu programu PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md)

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)