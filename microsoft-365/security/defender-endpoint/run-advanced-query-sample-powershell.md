---
title: Zaawansowane wyszukiwanie zagrożeń za pomocą podstaw interfejsu API programu PowerShell
ms.reviewer: ''
description: Poznaj podstawy wykonywania zapytań dotyczących interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell.
keywords: interfejsy API, obsługiwane interfejsy API, zaawansowane wyszukiwanie zagrożeń, zapytania
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc0cae0ff8c45f4c32213130773e3c118d779ed6
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243145"
---
# <a name="advanced-hunting-using-powershell"></a>Zaawansowane wyszukiwanie zagrożeń przy użyciu programu PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Uruchom zaawansowane zapytania przy użyciu programu PowerShell, zobacz [Advanced Hunting API (Zaawansowany interfejs API wyszukiwania zagrożeń](run-advanced-query-api.md)).

W tej sekcji udostępniamy przykłady programu PowerShell w celu pobrania tokenu i użycia go do uruchomienia zapytania.

## <a name="before-you-begin"></a>Przed rozpoczęciem
Najpierw musisz [utworzyć aplikację](apis-intro.md).

## <a name="preparation-instructions"></a>Instrukcje przygotowywania

- Otwórz okno programu PowerShell.

- Jeśli zasady nie zezwalają na uruchamianie poleceń programu PowerShell, możesz uruchomić następujące polecenie:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Aby uzyskać więcej informacji, zobacz [dokumentację programu PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Uzyskiwanie tokenu

- Uruchom następujące polecenie:

```powershell
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$body = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$response = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $body -ErrorAction Stop
$aadToken = $response.access_token
```

Gdzie
- $tenantId: identyfikator dzierżawy, w imieniu której chcesz uruchomić zapytanie (oznacza to, że zapytanie zostanie uruchomione na danych tej dzierżawy)
- $appId: identyfikator aplikacji Azure AD (aplikacja musi mieć uprawnienie "Uruchamianie zaawansowanych zapytań" do usługi Defender for Endpoint)
- $appSecret: wpis tajny aplikacji Azure AD

## <a name="run-query"></a>Uruchamianie zapytania

Uruchom następujące zapytanie:

```powershell
$query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

$url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$body = ConvertTo-Json -InputObject @{ 'Query' = $query }
$webResponse = Invoke-WebRequest -Method Post -Uri $url -Headers $headers -Body $body -ErrorAction Stop
$response =  $webResponse | ConvertFrom-Json
$results = $response.Results
$schema = $response.Schema
```

- $results zawierać wyniki zapytania
- $schema zawiera schemat wyników zapytania

### <a name="complex-queries"></a>Złożone zapytania

Jeśli chcesz uruchamiać złożone zapytania (lub zapytania wielowierszowe), zapisz zapytanie w pliku i zamiast pierwszego wiersza w powyższym przykładzie uruchom następujące polecenie:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Praca z wynikami zapytań

Teraz możesz użyć wyników zapytania.

Aby wyświetlić wyniki zapytania w formacie CSV w pliku file1.csv, uruchom następujące polecenie:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Aby wyświetlić wyniki zapytania w formacie JSON w pliku file1.json, uruchom następujące polecenie:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>Temat pokrewny
- [interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)
- [Interfejs API zaawansowanego wyszukiwania zagrożeń](run-advanced-query-api.md)
- [Zaawansowane wyszukiwanie zagrożeń przy użyciu języka Python](run-advanced-query-sample-python.md)
