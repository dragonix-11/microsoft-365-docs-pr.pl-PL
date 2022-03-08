---
title: Uruchamianie poleceń odpowiedzi na żywo na urządzeniu
description: Dowiedz się, jak uruchomić sekwencję poleceń odpowiedzi na żywo na urządzeniu.
keywords: apis, api Graph, obsługiwane api, przekazywanie do biblioteki
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: e81c235105a7c7479a917c7cb7cc404e2553f2f1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323521"
---
# <a name="run-live-response-commands-on-a-device"></a>Uruchamianie poleceń odpowiedzi na żywo na urządzeniu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Uruchamia sekwencję poleceń odpowiedzi na żywo na urządzeniu.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 10 połączeń na minutę (odpowiedzi na dodatkowe żądania są odbierane przy użyciu protokołu HTTP 429).

2. 25 jednoczesnych sesji (żądania przekraczające limit ograniczania otrzymają odpowiedź "429 — Zbyt wiele żądań").

3. Jeśli komputer nie jest dostępny, sesja zostanie w kolejce przez maksymalnie 3 dni.

4. Limity czasu poleceń RunScript po 10 minutach.

5. Poleceń odpowiedzi na żywo nie można wsuń w kolejce i można je wykonać tylko raz na raz.

6. Jeśli komputer, na który próbujesz uruchomić to wywołanie interfejsu API, znajduje się w grupie urządzeń RBAC, do których nie jest przypisany automatyczny poziom rozwiązywania problemów, musisz przynajmniej włączyć minimalny poziom rozwiązywania problemów dla danej grupy urządzeń.

7. W jednym wywołaniu interfejsu API można uruchomić wiele poleceń odpowiedzi na żywo. Jednak jeśli polecenie odpowiedzi na żywo zakończy się niepowodzeniem, nie zostaną wykonane wszystkie kolejne akcje.

## <a name="minimum-requirements"></a>Wymagania minimalne

Zanim zainicjujesz sesję na urządzeniu, upewnij się, że spełniasz następujące wymagania:

- **Sprawdź, czy używasz obsługiwanej wersji pakietu Windows**.

  Na urządzeniach musi być uruchomiona jedna z następujących wersji Windows

  - **Windows 11**
  
  - **Windows 10**
    - [Wersja 1909 lub](/windows/whats-new/whats-new-windows-10-version-1909) nowsza
    - [Wersja 1903](/windows/whats-new/whats-new-windows-10-version-1903) z [kb4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Wersja 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) z [kb4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Wersja 1803 (RS 4) z](/windows/whats-new/whats-new-windows-10-version-1803) [kb4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Wersja 1709 (RS 3) z](/windows/whats-new/whats-new-windows-10-version-1709) [kb4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **Windows Server 2019 — dotyczy tylko wersji Public Preview**
    - Wersja 1903 lub (z [kb4515384) później](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - Wersja 1809 (z [kb4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).

|Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień|
|---|---|---|
|Aplikacja|Machine.LiveResponse|Uruchamianie odpowiedzi na żywo na określonym komputerze|
|Delegowane (konto służbowe)|Machine.LiveResponse|Uruchamianie odpowiedzi na żywo na określonym komputerze|

## <a name="http-request"></a>Żądanie HTTP

```HTTP
POST https://api.securitycenter.microsoft.com/API/machines/{machine_id}/runliveresponse
```

## <a name="request-headers"></a>Żądaj nagłówków

|Name (Nazwa)|Wpisać|Opis|
|---|---|---|
|Autoryzacja|Ciąg|Bearer\<token>\. Wymagane.|
|Typ zawartości|ciąg|application/json. Wymagane.|

## <a name="request-body"></a>Treść wniosku

|Parametr|Wpisać|Opis|
|---|---|---|
|Komentowanie|Ciąg|Komentarz do skojarzenia z akcją.|
|Polecenia|Tablica|Polecenia do uruchomienia. Dozwolone wartości to PutFile, RunScript, GetFile.|

## <a name="commands"></a>Polecenia

|Typ polecenia|Parametry|Opis|
|---|---|---|
|PutFile|Klucz: Nazwa_pliku <p> Wartość: \<file name\>|Umieszcza plik z biblioteki na urządzeniu. Pliki są zapisywane w folderze roboczym i są usuwane po domyślnym ponownym uruchomieniu urządzenia.
|RunScript|Klucz: ScriptName <br> Wartość: \<Script from library\> <p> Klucz: Args <br> Wartość: \<Script arguments\>|Uruchamia skrypt z biblioteki na urządzeniu. <p>  Parametr Args jest przekazywany do skryptu. <p> Limity czasu po 10 minutach.|
|GetFile|Klucz: Ścieżka <br> Wartość: \<File path\>|Zbieranie plików z urządzenia. UWAGA: Należy uniknąć ukośników odwrotnych w ścieżce.|

## <a name="response"></a>Odpowiedź

- Jeśli ta metoda się powiedzie, funkcja zwróci wartość 201 Utworzono.

  Jednostka akcji. Jeśli nie można odnaleźć komputera o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```HTTP
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runliveresponse

```JSON
{
   "Commands":[
      {
         "type":"RunScript",
         "params":[
            {
               "key":"ScriptName",
               "value":"minidump.ps1"
            },
            {
               "key":"Args",
               "value":"OfficeClickToRun"
            }

         ]
      },
      {
         "type":"GetFile",
         "params":[
            {
               "key":"Path",
               "value":"C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
            }
         ]
      }
   ],
   "Comment":"Testing Live Response API"
}
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```HTTP
HTTP/1.1 200 Ok
```

Typ zawartości: application/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "{machine_action_id}",
    "type": "LiveResponse",
    "requestor": "analyst@microsoft.com",
    "requestorComment": "Testing Live Response API",
    "status": "Pending",
    "machineId": "{machine_id}",
    "computerDnsName": "hostname",
    "creationDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "lastUpdateDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "errorHResult": 0,
    "commands": [
        {
            "index": 0,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "RunScript",
                "params": [
                    {
                        "key": "ScriptName",
                        "value": "minidump.ps1"
                    },{
                        "key": "Args",
                        "value": "OfficeClickToRun"
                    }
                ]
            }
        }, {
            "index": 1,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "GetFile",
                "params": [{
                        "key": "Path", "value": "C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
                    }
                ]
            }
        }
    ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Uzyskiwanie interfejsu API akcji maszynowych](get-machineaction-object.md)
- [Uzyskiwanie odpowiedzi na żywo](get-live-response-result.md)
- [Anuluj akcję komputera](cancel-machine-action.md)
