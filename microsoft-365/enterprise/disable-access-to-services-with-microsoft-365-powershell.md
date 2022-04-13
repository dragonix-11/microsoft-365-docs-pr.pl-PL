---
title: Wyłączanie dostępu do usług Microsoft 365 przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: W tym artykule dowiesz się, jak wyłączyć dostęp do usług Microsoft 365 dla użytkowników za pomocą programu PowerShell.
ms.openlocfilehash: e0fc42f0c68b02824513f382228378bfd4ee2a8e
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824875"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Wyłączanie dostępu do usług Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Gdy konto Microsoft 365 ma przypisaną licencję z planu licencjonowania, Microsoft 365 usługi są udostępniane użytkownikowi z tej licencji. Można jednak kontrolować usługi Microsoft 365, do których użytkownik może uzyskać dostęp. Na przykład nawet jeśli licencja zezwala na dostęp do usługi SharePoint Online, możesz wyłączyć do niej dostęp. Program PowerShell umożliwia wyłączenie dostępu do dowolnej liczby usług dla określonego planu licencjonowania dla:

- Indywidualne konto.
- Grupa kont.
- Wszystkie konta w organizacji.

>[!Note]
>Istnieją Microsoft 365 zależności usług, które mogą uniemożliwić wyłączenie określonej usługi, gdy od niej zależą inne usługi.
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Korzystanie z zestawu SDK programu PowerShell firmy Microsoft Graph

Najpierw [połącz się z dzierżawą Microsoft 365](/graph/powershell/get-started#authentication).

Przypisywanie i usuwanie licencji dla użytkownika wymaga zakresu uprawnień User.ReadWrite.All lub jednego z innych uprawnień wymienionych na [stronie odwołania interfejs Graph API "Przypisywanie licencji"](/graph/api/user-assignlicense).

Zakres uprawnień Organization.Read.All jest wymagany do odczytu licencji dostępnych w dzierżawie.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Następnie użyj tego polecenia, aby wyświetlić dostępne plany licencjonowania, znane również jako SkuPartNumber:

```powershell
Get-MgSubscribedSku | Select SkuId, SkuPartNumber, ServicePlans | Sort SkuPartNumber
```

Aby uzyskać więcej informacji, zobacz [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

Aby wyświetlić przed i po wynikach procedur w tym temacie, zobacz [Wyświetlanie licencji konta i szczegółów usługi za pomocą programu PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).

### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Wyłączanie określonych usług Microsoft 365 dla określonych użytkowników dla określonego planu licencjonowania
  
Aby wyłączyć określony zestaw usług Microsoft 365 dla użytkowników dla określonego planu licencjonowania, wykonaj następujące kroki:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Krok 1. Identyfikowanie niepożądanych usług w planie licencjonowania przy użyciu następującej składni:

Najpierw wyświetl listę planów licencjonowania dostępnych w dzierżawie przy użyciu następującego polecenia.

```powershell
Get-MgSubscribedSku | Select SkuPartNumber

SkuPartNumber
-------------
EMSPREMIUM
SPE_E5
RIGHTSMANAGEMENT_ADHOC

$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

Następnie użyj polecenia SkuPartNumber z powyższego polecenia, aby wyświetlić listę planów usług dostępnych dla danego planu licencji (SKU).

W poniższym przykładzie wymieniono wszystkie plany usług dostępne dla **SPE_E5** (Microsoft 365 E5).

```powershell
Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5' |  select -ExpandProperty ServicePlans
```

```text
AppliesTo ProvisioningStatus ServicePlanId                        ServicePlanName
--------- ------------------ -------------                        ---------------
User      Success            b21a6b06-1988-436e-a07b-51ec6d9f52ad PROJECT_O365_P3
User      Success            64bfac92-2b17-4482-b5e5-a0304429de3e MICROSOFTENDPOINTDLP
User      Success            199a5c09-e0ca-4e37-8f7c-b05d533e1ea2 MICROSOFTBOOKINGS
User      Success            6db1f1db-2b46-403f-be40-e39395f08dbb CUSTOMER_KEY
User      Success            4a51bca5-1eff-43f5-878c-177680f191af WHITEBOARD_PLAN3
User      Success            07699545-9485-468e-95b6-2fca3738be01 FLOW_O365_P3
User      Success            9c0dab89-a30c-4117-86e7-97bda240acd2 POWERAPPS_O365_P3
User      Success            e212cbc7-0961-4c40-9825-01117710dcb1 FORMS_PLAN_E5
User      Success            57ff2da0-773e-42df-b2af-ffb7a2317929 TEAMS1
User      Success            21b439ba-a0ca-424f-a6cc-52f954a5b111 WIN10_PRO_ENT_SUB
User      Success            eec0eb4f-6444-4f95-aba0-50c24d67f998 AAD_PREMIUM_P2
User      Success            c1ec4a95-1f05-45b3-a911-aa3fa01094f5 INTUNE_A
User      Success            7547a3fe-08ee-4ccb-b430-5077c5041653 YAMMER_ENTERPRISE
User      Success            a23b959c-7ce8-4e57-9140-b90eb88a9e97 SWAY
User      Success            e95bec33-7c88-4a70-8e19-b10bd9d0c014 SHAREPOINTWAC
User      Success            5dbe027f-2339-4123-9542-606e4d348a72 SHAREPOINTENTERPRISE
User      Success            b737dad2-2f6c-4c65-90e3-ca563267e8b9 PROJECTWORKMANAGEMENT
User      Success            43de0ff5-c92c-492b-9116-175376d08c38 OFFICESUBSCRIPTION
User      Success            0feaeb32-d00e-4d66-bd5a-43b5b83db82c MCOSTANDARD
User      Success            9f431833-0334-42de-a7dc-70aa40db46db LOCKBOX_ENTERPRISE
User      Success            efb87545-963c-4e0d-99df-69c6916d9eb0 EXCHANGE_S_ENTERPRISE
```

Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), ich dołączone plany usług i odpowiadające im przyjazne nazwy, zobacz [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference). (Wyszukaj przy użyciu identyfikatora ServicePlanId, aby wyszukać odpowiednią przyjazną nazwę planu usługi wyszukiwania).

Poniższy przykład przypisuje **SPE_E5** (Microsoft 365 E5) z wyłączonymi usługami **MICROSOFTBOOKINGS** (Microsoft Bookings) i **LOCKBOX_ENTERPRISE** (Customer LockBox):
  
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

Właściwość DisabledPlans parametru AddLicenses w Set-MgUserLicense zastąpi istniejącą wartość DisabledPlans użytkownika. Aby zachować stan istniejących planów usług, bieżący stan planów usług użytkownika musi zostać scalony z nowymi planami, które zostaną wyłączone.

Brak dołączenia istniejących planów DisabledPlans spowoduje włączenie wcześniej wyłączonego planu użytkownika.

Poniższy przykład aktualizuje użytkownika przy użyciu **SPE_E5** (Microsoft 365 E5) i wyłącza plany usług Sway i Forms, pozostawiając istniejące wyłączone plany użytkownika w bieżącym stanie:
  
```powershell
## Get the services that have already been disabled for the user.
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

## Get the new service plans that are going to be disabled
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

## Merge the new plans that are to be disabled with the user's current state of disabled plans
$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)
## Update user's license
Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Następnie użyj tego polecenia, aby wyświetlić dostępne plany licencjonowania, znane również jako AccountSkuIds:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

Aby uzyskać więcej informacji, zobacz [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Aby wyświetlić przed i po wynikach procedur w tym temacie, zobacz [Wyświetlanie licencji konta i szczegółów usługi za pomocą programu PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Dostępny jest skrypt programu PowerShell, który automatyzuje procedury opisane w tym temacie. W szczególności skrypt umożliwia wyświetlanie i wyłączanie usług w organizacji Microsoft 365, w tym Sway. Aby uzyskać więcej informacji, zobacz [Wyłączanie dostępu do Sway za pomocą programu PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Wyłączanie określonych usług Microsoft 365 dla określonych użytkowników dla określonego planu licencjonowania
  
Aby wyłączyć określony zestaw usług Microsoft 365 dla użytkowników dla określonego planu licencjonowania, wykonaj następujące kroki:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Krok 1. Identyfikowanie niepożądanych usług w planie licencjonowania przy użyciu następującej składni:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

Poniższy przykład tworzy obiekt **LicenseOptions**, który wyłącza usługi Office i SharePoint Online w planie licencjonowania o nazwie `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Krok 2. Użyj obiektu **LicenseOptions** z kroku 1 dla co najmniej jednego użytkownika.
    
Aby utworzyć nowe konto z wyłączonymi usługami, użyj następującej składni:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

Poniższy przykład tworzy nowe konto dla Allie Bellew, które przypisuje licencję i wyłącza usługi opisane w kroku 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Aby uzyskać więcej informacji na temat tworzenia kont użytkowników w programie PowerShell dla Microsoft 365, zobacz [Tworzenie kont użytkowników przy użyciu programu PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
Aby wyłączyć usługi dla istniejącego licencjonowanego użytkownika, użyj następującej składni:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

Ten przykład wyłącza usługi dla użytkownika BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Aby wyłączyć usługi opisane w kroku 1 dla wszystkich istniejących licencjonowanych użytkowników, określ nazwę planu Microsoft 365 z poziomu wyświetlania polecenia cmdlet **Get-MsolAccountSku** (na przykład **litwareinc:ENTERPRISEPACK**), a następnie uruchom następujące polecenia:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Jeśli używasz polecenia cmdlet **Get-MsolUser** bez użycia parametru _Wszystkie_ , zwracanych jest tylko pierwsze 500 kont użytkowników.

Aby wyłączyć usługi dla grupy istniejących użytkowników, użyj jednej z następujących metod, aby zidentyfikować użytkowników:
    
**Metoda 1. Filtrowanie kont na podstawie istniejącego atrybutu konta** 

W tym celu użyj następującej składni:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

Poniższy przykład wyłącza usługi dla użytkowników w dziale sprzedaży w Stany Zjednoczone.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Metoda 2. Używanie listy określonych kont** 

W tym celu wykonaj następujące kroki:
    
1. Utwórz plik tekstowy zawierający jedno konto w każdym wierszu w następujący sposób:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   W tym przykładzie plik tekstowy to C:\\My Documents\\Accounts.txt.
    
2. Uruchom następujące polecenie:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Jeśli chcesz wyłączyć dostęp do usług dla wielu planów licencjonowania, powtórz powyższe instrukcje dla każdego planu licencjonowania, zapewniając, że:

- Do kont użytkowników przypisano plan licencjonowania.
- Usługi do wyłączenia są dostępne w planie licencjonowania.

Aby wyłączyć usługi Microsoft 365 dla użytkowników podczas przypisywania ich do planu licencjonowania, zobacz [Wyłączanie dostępu do usług podczas przypisywania licencji użytkowników](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Przypisywanie wszystkich usług w planie licencjonowania do konta użytkownika

W przypadku kont użytkowników, dla których usługi zostały wyłączone, można włączyć wszystkie usługi dla określonego planu licencjonowania za pomocą następujących poleceń:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>Temat pokrewny

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
