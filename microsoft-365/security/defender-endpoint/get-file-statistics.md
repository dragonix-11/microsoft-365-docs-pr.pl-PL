---
title: Interfejs API statystyk plików
description: Dowiedz się, jak pobrać statystykę dla danego pliku za pomocą interfejsu API Uzyskaj statystykę plików w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, file, statistics
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
ms.openlocfilehash: 83901799d6dc5e8f6aa81ad57580e64167bfa134
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996224"
---
# <a name="get-file-statistics-api"></a>Interfejs API statystyk plików

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera statystykę dla danego pliku.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.
2. Maksymalna wartość to `lookbackhours` 720 godzin(30 dni).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|File.Read.All|"Odczyt profilów plików"
Delegowane (konto służbowe)|File.Read.All|"Odczyt profilów plików"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/files/{id}/stats
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-uri-parameters"></a>Żądanie parametrów URI

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
lookBackHours|Int32|Definiuje godziny, które są przeszukiwane w celu uzyskania statystyk. Wartość domyślna to 30 dni. **Opcjonalne**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli plik się powiedzie i istnieje — 200 OK z danymi statystycznymi w treści. Jeśli plik nie istnieje — nie można odnaleźć 404.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/files/0991a395da64e1c5fbe8732ed11e6be064081d9f/stats?lookBackHours=48
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgFileStats",
    "sha1": "0991a395da64e1c5fbe8732ed11e6be064081d9f",
    "organizationPrevalence": 14850,
    "orgFirstSeen": "2019-12-07T13:44:16Z",
    "orgLastSeen": "2020-01-06T13:39:36Z",
    "globallyPrevalence": 705012,
    "globalFirstObserved": "2015-03-19T12:20:07.3432441Z",
    "globalLastObserved": "2020-01-06T13:39:36Z",
    "topFileNames": [
        "MREC.exe"
    ]
}
```
