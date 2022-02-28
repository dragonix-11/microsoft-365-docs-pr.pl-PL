---
title: Wyłączanie dostępu do Microsoft 365 podczas przypisywania licencji użytkowników
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak przypisywać licencje do kont użytkowników i wyłączać określone plany usług jednocześnie przy użyciu programu PowerShell dla komputerów Microsoft 365.
ms.openlocfilehash: 5b7130930097970f5cfabc9a7599c211393b7c7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985088"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Wyłączanie dostępu do Microsoft 365 podczas przypisywania licencji użytkowników

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 subskrypcje mają plany usług dla poszczególnych usług. Microsoft 365 często muszą wyłączyć określone plany podczas przypisywania licencji do użytkowników. Zgodnie z instrukcjami w tym artykule możesz przypisać licencję usługi Microsoft 365 podczas wyłączania określonych planów usług przy użyciu programu PowerShell dla pojedynczego konta użytkownika lub wielu kont użytkowników.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Następnie, za pomocą tego polecenia, wywszukaj listę planów licencji dla dzierżawy.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie uzyskaj nazwę logowania dla konta, do którego chcesz dodać licencję, znaną również jako główna nazwa użytkownika (UPN).

Następnie skompilowaj listę usług, aby włączyć tę funkcję. Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), dołączone do nich plany usług i odpowiadające im przyjazne nazwy, zobacz Nazwy produktów i identyfikatory planów usług w celu [licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

W poniższym bloku poleceń wpisz główną nazwę użytkownika konta użytkownika, numer części jednostki SKU \< and > oraz listę planów usług w celu włączenia i usunięcia objaśnianego tekstu oraz znaków. Następnie uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.

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

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Następnie uruchom to polecenie, aby wyświetlić bieżące subskrypcje:

```powershell
Get-MsolAccountSku
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

Na ekranie polecenia  `Get-MsolAccountSku` :

- **AccountSkuId** to subskrypcja dla Twojej organizacji w formacie \<OrganizationName>:\<Subscription> . Jest \<OrganizationName> to wartość, która jest udzielana podczas zarejestrowania się w usłudze Microsoft 365 i jest unikatowa dla Twojej organizacji. Wartość \<Subscription> jest dla określonej subskrypcji. Na przykład w przypadku litwareinc:ENTERPRISEPACK nazwa organizacji to litwareinc, a nazwa subskrypcji to ENTERPRISEPACK (Office 365 Enterprise E3).

- **ActiveUnits** to liczba licencji, które kupiono dla subskrypcji.

- **OstrzeżenieUnits** to liczba licencji w subskrypcji, która nie została odnowiona i która wygaśnie po 30-dniowym okresie prolongaty.

- **ConsumedUnits** to liczba licencji przypisanych do użytkowników w ramach subskrypcji.

Zwróć uwagę na pole AccountSkuId Microsoft 365 subskrypcji zawierającej użytkowników, którym chcesz uzyskać licencję. Ponadto upewnij się, że jest wystarczająca ilość licencji do przypisania (odejmij **jednostki ConsumedUnits od** **jednostki ActiveUnits**).

Następnie uruchom to polecenie, aby wyświetlić szczegóły Microsoft 365 usług dostępnych we wszystkich subskrypcjach:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Na podstawie wyświetlania tego polecenia określ, które plany usług mają zostać wyłączone podczas przypisywania licencji do użytkowników.

Poniżej znajduje się częściowa lista planów usług i odpowiadających im Microsoft 365 usług.

W poniższej tabeli przedstawiono Microsoft 365 usług oraz ich przyjazne nazwy dla najczęściej oferowanych usług. Lista planów usług może się różnić.

|**Plan serwisowy**|**Opis**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Aplikacje Microsoft 365 dla przedsiębiorstw *(wcześniej Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype dla firm Online  <br/> |
| `SHAREPOINTWAC` <br/> |Pakiet Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |

Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), dołączone do nich plany usług i odpowiadające im przyjazne nazwy, zobacz Nazwy produktów i identyfikatory planów usług w celu [licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Teraz, gdy masz identyfikator AccountSkuId i plany usługi do wyłączenia, możesz przypisać licencje do pojedynczego użytkownika lub wielu użytkowników.

### <a name="for-a-single-user"></a>Dla jednego użytkownika

W przypadku jednego użytkownika wprowadź główną nazwę użytkownika konta użytkownika, identyfikator AccountSkuId \< and > oraz listę planów usługi do wyłączenia i usunięcia objaśnianego tekstu oraz znaków. Następnie uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

Oto przykładowy blok poleceń dla konta o nazwie belindan@contoso.com dla licencji contoso:ENTERPRISEPACK, a plany usług do wyłączenia to: RMS_S_ENTERPRISE, SWAY, INTUNE_O365 i YAMMER_ENTERPRISE:

```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>W przypadku wielu użytkowników

Aby wykonać to zadanie administracyjne dla wielu użytkowników, utwórz plik tekstowy wartości rozdzielanych przecinkami (CSV) zawierający pola UserPrincipalName i UsageLocation. Oto przykład:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Następnie wprowadź lokalizację wejściowych i wyjściowych plików CSV, identyfikator SKU konta i listę planów usług do wyłączenia, a następnie uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.

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

- Wyświetla główną nazwę każdego użytkownika.

- Przypisuje licencje niestandardowe do poszczególnych użytkowników.

- Tworzy plik CSV z wszystkimi użytkownikami, którzy zostali przetworzeni, i wyświetla ich stan licencji.

## <a name="see-also"></a>Zobacz też

[Wyłączanie dostępu do usług Microsoft 365 za pomocą programu PowerShell](disable-access-to-services-with-microsoft-365-powershell.md)

[Wyłączanie dostępu do aplikacji Sway za pomocą programu PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md)

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)