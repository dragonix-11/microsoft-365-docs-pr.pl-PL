---
title: Zaawansowane łowiectwo z podstawowymi funkcjami interfejsu API programu PowerShell
ms.reviewer: ''
description: Poznaj podstawy wykonywania zapytań w interfejsie API programu Microsoft Defender for Endpoint przy użyciu programu PowerShell.
keywords: api, obsługiwane api, zaawansowane wyszukiwania, zapytanie
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
ms.openlocfilehash: 5de8778f1da44f8a9453616dc1e3b6f2af948397
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996277"
---
# <a name="advanced-hunting-using-powershell"></a>Zaawansowane szukanie przy użyciu programu PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Aby uruchomić zapytania zaawansowane za pomocą programu PowerShell, zobacz [Zaawansowany interfejs API wyszukiwania](run-advanced-query-api.md).

W tej sekcji udostępniamy przykłady programu PowerShell, aby pobrać token i użyć go do uruchomienia zapytania.

## <a name="before-you-begin"></a>Przed rozpoczęciem
Najpierw musisz [utworzyć aplikację](apis-intro.md).

## <a name="preparation-instructions"></a>Instrukcje przygotowania

- Otwieranie okna programu PowerShell.

- Jeśli zasady nie zezwalają na uruchamianie poleceń programu PowerShell, możesz uruchomić następujące polecenie:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Aby uzyskać więcej informacji, zobacz Dokumentacja [programu PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Pobierz token

- Uruchom następujące czynności:

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

gdzie
- $tenantId: identyfikator dzierżawy, w imieniu której chcesz uruchomić zapytanie (oznacza to, że zapytanie zostanie uruchomione na danych tej dzierżawy)
- $appId: Identyfikator aplikacji Azure AD (aplikacja musi mieć uprawnienie "Uruchom zapytania zaawansowane" do usługi Defender dla punktu końcowego)
- $appSecret: Klucz tajny aplikacji usługi Azure AD

## <a name="run-query"></a>Uruchamianie zapytania

Uruchom następujące zapytanie:

```powershell
$query = 'RegistryEvents | limit 10' # Paste your own query here

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

- $results zawierają wyniki zapytania
- $schema zawiera schemat wyników zapytania

### <a name="complex-queries"></a>Złożone zapytania

Jeśli chcesz uruchamiać złożone zapytania (lub zapytania wielolinie), zapisz zapytanie w pliku i uruchom następujące polecenie zamiast pierwszego wiersza w powyższym przykładzie:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Praca z wynikami zapytania

Teraz możesz użyć wyników zapytania.

Aby wyprowadzić wyniki zapytania w formacie CSV w formacie file1.csv, uruchom następujące polecenie:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Aby wyprowadzić wyniki zapytania w formacie JSON w pliku file1.json, uruchom następujące polecenie:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>Temat pokrewny
- [Interfejsy API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
- [Zaawansowany interfejs API łowiectwo](run-advanced-query-api.md)
- [Zaawansowane szukanie w języku Python](run-advanced-query-sample-python.md)
