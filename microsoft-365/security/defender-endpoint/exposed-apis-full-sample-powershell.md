---
title: Przewodnik zaawansowanego wyszukiwania przy użyciu interfejsu API programu PowerShell
ms.reviewer: ''
description: Skorzystaj z tych przykładów kodów i przeszukaj kilka interfejsów API programu Microsoft Defender dla punktów końcowych.
keywords: api, obsługiwane api, zaawansowane wyszukiwania, zapytanie
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
ms.date: 09/24/2018
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6b1f501b942512500c11c7f9fe1e9308d67706e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997848"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>Interfejsy API programu Microsoft Defender dla punktów końcowych przy użyciu programu PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Pełny scenariusz z użyciem wielu interfejsów API z programu Microsoft Defender dla punktu końcowego.

W tej sekcji udostępniamy przykłady programu PowerShell 
- Pobieranie tokenu 
- Pobieranie najnowszych alertów w programie Microsoft Defender dla punktu końcowego za pomocą tokenu
- Dla każdego alertu, jeśli alert ma średni lub wysoki priorytet i jest nadal w toku, sprawdź, ile razy urządzenie jest połączone z podejrzanym adresem URL.

**Wymagania** wstępne: najpierw należy [utworzyć aplikację](apis-intro.md).

## <a name="preparation-instructions"></a>Instrukcje przygotowania

- Otwieranie okna programu PowerShell.
- Jeśli zasady nie umożliwiają uruchamiania poleceń programu PowerShell, możesz uruchomić poniższe polecenie:
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Aby uzyskać więcej informacji, zobacz Dokumentacja [programu PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Pobierz token

Uruchom poniższe czynności:

- $tenantId: identyfikator dzierżawy, w imieniu której chcesz uruchomić zapytanie (tj. zapytanie zostanie uruchomione na danych tej dzierżawy)
- $appId: Identyfikator aplikacji AAD (aplikacja musi mieć uprawnienie "Uruchom zapytania zaawansowane" do usługi Defender dla punktu końcowego)
- $appSecret: Klucz tajny aplikacji usługi Azure AD

- $suspiciousUrl: Adres URL


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
- [Interfejsy API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
- [Zaawansowany interfejs API łowiectwo](run-advanced-query-api.md)
- [Zaawansowane szukanie w języku Python](run-advanced-query-sample-python.md)
