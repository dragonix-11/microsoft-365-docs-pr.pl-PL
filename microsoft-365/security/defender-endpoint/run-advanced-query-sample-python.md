---
title: Zaawansowane wyszukiwanie zagrożeń za pomocą interfejsu API języka Python
ms.reviewer: ''
description: Dowiedz się, jak wykonywać zapytania przy użyciu interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu języka Python z przykładami.
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
ms.openlocfilehash: 99fc848088725f7b28d91eebc78327c688059de8
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174784"
---
# <a name="advanced-hunting-using-python"></a>Zaawansowane wyszukiwanie zagrożeń przy użyciu języka Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Uruchom zaawansowane zapytania przy użyciu języka Python, zobacz [Advanced Hunting API (Zaawansowany interfejs API wyszukiwania zagrożeń](run-advanced-query-api.md)).

W tej sekcji udostępnimy przykłady języka Python, aby pobrać token i użyć go do uruchomienia zapytania.

> **Wymagania wstępne**: najpierw musisz [utworzyć aplikację](apis-intro.md).

## <a name="get-token"></a>Uzyskiwanie tokenu

- Uruchom następujące polecenia:

```python
import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.microsoftonline.com/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

Gdzie

- tenantId: identyfikator dzierżawy, w imieniu której chcesz uruchomić zapytanie (tj. zapytanie zostanie uruchomione na danych tej dzierżawy)
- appId: identyfikator aplikacji Azure AD (aplikacja musi mieć uprawnienie "Uruchamianie zaawansowanych zapytań" do Ochrona punktu końcowego w usłudze Microsoft Defender)
- appSecret: wpis tajny aplikacji Azure AD

## <a name="run-query"></a>Uruchamianie zapytania

 Uruchom następujące zapytanie:

```python
query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
headers = { 
    'Content-Type' : 'application/json',
    'Accept' : 'application/json',
    'Authorization' : "Bearer " + aadToken
}

data = json.dumps({ 'Query' : query }).encode("utf-8")

req = urllib.request.Request(url, data, headers)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
schema = jsonResponse["Schema"]
results = jsonResponse["Results"]
```

- schemat zawiera schemat wyników zapytania
- wyniki zawierają wyniki zapytania

### <a name="complex-queries"></a>Złożone zapytania

Jeśli chcesz uruchamiać złożone zapytania (lub zapytania wielowierszowe), zapisz zapytanie w pliku i zamiast pierwszego wiersza w powyższym przykładzie uruchom poniższe polecenie:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Praca z wynikami zapytań

Teraz możesz użyć wyników zapytania.

Aby wykonać iterację w wynikach, wykonaj poniższe czynności:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Aby wyświetlić wyniki zapytania w formacie CSV w pliku file1.csv wykonaj poniższe czynności:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Aby wyświetlić wyniki zapytania w formacie JSON w pliku file1.json, wykonaj poniższe czynności:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>Temat pokrewny

- [interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)
- [Interfejs API zaawansowanego wyszukiwania zagrożeń](run-advanced-query-api.md)
- [Zaawansowane wyszukiwanie zagrożeń przy użyciu programu PowerShell](run-advanced-query-sample-powershell.md)
