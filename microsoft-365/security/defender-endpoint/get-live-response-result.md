---
title: Uzyskiwanie wyników odpowiedzi na żywo
description: Dowiedz się, jak pobrać określony wynik polecenia na żywo na skutek indeksu.
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
ms.openlocfilehash: bd8b3c997a8efceb2791eca4de0b0e42d47513f8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314409"
---
# <a name="get-live-response-results"></a>Uzyskiwanie wyników odpowiedzi na żywo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera określony wynik polecenia odpowiedzi na żywo na skutek indeksu.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

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
Aplikacja|Machine.Read.All|''Czytaj wszystkie profile maszyn''
Aplikacja|"Machine.ReadWrite.All|"Czytanie i pisanie wszystkich informacji o komputerze"
|Delegowane (konto służbowe)|Machine.LiveResponse|Uruchamianie odpowiedzi na żywo na określonym komputerze|

## <a name="http-request"></a>Żądanie HTTP

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/{machine action
id}/GetLiveResponseResultDownloadLink(index={command-index})
```

## <a name="request-headers"></a>Żądaj nagłówków

|Name (Nazwa)|Wpisać|Opis|
|---|---|---|
|Autoryzacja|Ciąg|Użytkownik {token}. Wymagane.|

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200, kod odpowiedzi OK z obiektem, który zawiera link do wyniku polecenia we *właściwości wartość* . Ten link jest ważny przez 30 minut i powinien być natychmiast używany do pobrania pakietu do magazynu lokalnego. Wygasły link można utworzyć ponownie przez inne połączenie i nie trzeba ponownie uruchamiać odpowiedzi na żywo.

*Właściwości transkrypcji runscript:*

|Właściwość|Opis|
|---|---|
|script_name|Nazwa skryptu wykonywania|
|exit_code|Wykonywano kod wyjścia skryptu|
|script_output|Wykonanie standardowego wyniku skryptu|
|script_errors|Wynik błędu standardowego wykonywania skryptu|

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/GetLiveResponseResultDownloadLink(index=0)
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

HTTP/1.1 200 Ok

Typ zawartości: application/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Edm.String",
    "value": "https://core.windows.net/investigation-actions-data/ID/CustomPlaybookCommandOutput/4ed5e7807ad1fe59b00b664fe06a0f07?se=2021-02-04T16%3A13%3A50Z&sp=r&sv=2019-07-07&sr=b&sig=1dYGe9rPvUlXBPvYSmr6/OLXPY98m8qWqfIQCBbyZTY%3D"
}
```

*Zawartość pliku:*

```JSON
{
    "script_name": "minidump.ps1",
    "exit_code": 0,
    "script_output": "Transcript started, output file is C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Temp\\PSScriptOutputs\\PSScript_Transcript_{TRANSCRIPT_ID}.txt
C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip\n51 MB\n\u0000\u0000\u0000",
    "script_errors":""
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Uzyskiwanie interfejsu API akcji maszynowych](get-machineaction-object.md)
- [Anuluj akcję komputera](cancel-machine-action.md)
- [Uruchom odpowiedź na żywo](run-live-response.md) 
