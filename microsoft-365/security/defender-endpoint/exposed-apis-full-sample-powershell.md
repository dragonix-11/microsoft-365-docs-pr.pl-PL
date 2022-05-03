---
title: Zaawansowane wyszukiwanie zagrożeń za pomocą interfejsu API programu PowerShell — przewodnik
ms.reviewer: ''
description: Użyj tych przykładów kodu, wykonując zapytania dotyczące kilku Ochrona punktu końcowego w usłudze Microsoft Defender interfejsów API.
keywords: interfejsy API, obsługiwane interfejsy API, zaawansowane wyszukiwanie zagrożeń, zapytania
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 04/27/2022
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c23bf15a188527b2b4c24270fbc1312537da4154
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174880"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>Ochrona punktu końcowego w usłudze Microsoft Defender interfejsów API przy użyciu programu PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/index.yml)

> [!IMPORTANT]
> Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w usłudze Defender dla firm. Zobacz [Porównanie Microsoft Defender dla Firm z planami Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Pełny scenariusz z użyciem wielu interfejsów API z Ochrona punktu końcowego w usłudze Microsoft Defender.

W tej sekcji udostępnimy przykłady programu PowerShell 
- Pobieranie tokenu 
- Użyj tokenu, aby pobrać najnowsze alerty w Ochrona punktu końcowego w usłudze Microsoft Defender
- Jeśli alert ma średni lub wysoki priorytet i jest nadal w toku, sprawdź, ile razy urządzenie połączyło się z podejrzanym adresem URL.

**Wymagania wstępne**: najpierw musisz [utworzyć aplikację](apis-intro.md).

## <a name="preparation-instructions"></a>Instrukcje przygotowywania

- Otwórz okno programu PowerShell.
- Jeśli zasady nie zezwalają na uruchamianie poleceń programu PowerShell, możesz uruchomić poniższe polecenie:
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Aby uzyskać więcej informacji, zobacz [dokumentację programu PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Uzyskiwanie tokenu

Uruchom poniższe polecenie:

- $tenantId: identyfikator dzierżawy, w imieniu której chcesz uruchomić zapytanie (tj. zapytanie zostanie uruchomione na danych tej dzierżawy)
- $appId: identyfikator aplikacji AAD (aplikacja musi mieć uprawnienie "Uruchamianie zaawansowanych zapytań" do usługi Defender for Endpoint)
- $appSecret: wpis tajny aplikacji Azure AD

- $suspiciousUrl: adres URL


```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://securitycenter.onmicrosoft.com/windowsatpservice'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token


#Get latest alert
$alertUrl = "https://api.securitycenter.microsoft.com/api/alerts?`$top=10"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```


## <a name="see-also"></a>Zobacz też
- [interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)
- [Interfejs API zaawansowanego wyszukiwania zagrożeń](run-advanced-query-api.md)
- [Zaawansowane wyszukiwanie zagrożeń przy użyciu języka Python](run-advanced-query-sample-python.md)
