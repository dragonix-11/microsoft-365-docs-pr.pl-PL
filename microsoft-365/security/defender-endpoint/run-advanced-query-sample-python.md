---
title: Przewodnik zaawansowanego chłoniania w interfejsie API w języku Python
ms.reviewer: ''
description: Z przykładami dowiedz się, jak używać zapytania przy użyciu interfejsu API programu Microsoft Defender for Endpoint, używając języka Python.
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
ms.openlocfilehash: 73be2b3c2aa40bb88ac6ccff60eec5cb7f55338c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996276"
---
# <a name="advanced-hunting-using-python"></a>Zaawansowane szukanie w języku Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Uruchamianie zapytań zaawansowanych przy użyciu języka Python, zobacz [Zaawansowany interfejs API łowiectwo](run-advanced-query-api.md).

W tej sekcji udostępniamy przykłady w języku Python, aby pobrać token i użyć go do uruchomienia zapytania.

> **Wymagania** wstępne: najpierw należy [utworzyć aplikację](apis-intro.md).

## <a name="get-token"></a>Pobierz token

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

gdzie

- tenantId: identyfikator dzierżawy, w imieniu której chcesz uruchomić zapytanie (oznacza to, że zapytanie zostanie uruchomione na danych tej dzierżawy)
- appId: Identyfikator aplikacji Azure AD (aplikacja musi mieć uprawnienie "Uruchom zapytania zaawansowane" do programu Microsoft Defender dla punktu końcowego)
- appSecret: klucz tajny aplikacji usługi Azure AD

## <a name="run-query"></a>Uruchamianie zapytania

 Uruchom następujące zapytanie:

```python
query = 'RegistryEvents | limit 10' # Paste your own query here

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
- wyniki zawierają wyniki zapytania.

### <a name="complex-queries"></a>Złożone zapytania

Jeśli chcesz uruchamiać złożone zapytania (lub zapytania wieloliniętowe), zapisz zapytanie w pliku i uruchom poniższe polecenie zamiast pierwszego wiersza w powyższym przykładzie:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Praca z wynikami zapytania

Teraz możesz użyć wyników zapytania.

Aby iterować nad wynikami, wykonaj poniższe czynności:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Aby wyprowadzić wyniki zapytania w formacie CSV w file1.csv wykonaj poniższe czynności:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Aby wyprowadzić wyniki zapytania w formacie JSON w pliku file1.json, wykonaj poniższe czynności:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>Temat pokrewny

- [Interfejsy API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
- [Zaawansowany interfejs API łowiectwo](run-advanced-query-api.md)
- [Zaawansowane szukanie przy użyciu programu PowerShell](run-advanced-query-sample-powershell.md)
