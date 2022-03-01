---
title: Lista wyników ekspozycji według grupy urządzeń
description: Pobiera listę wyników ekspozycji według grupy urządzeń.
keywords: apis, api Graph, obsługiwane api, get, exposure score, device group, device group exposure score
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: ba046d35b6cf93754fc1daf3d2b211d69e6c27d8
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996337"
---
# <a name="list-exposure-score-by-device-group"></a>Lista wyników ekspozycji według grupy urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobiera wynik ekspozycji dla każdej grupy na komputerze.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Score.Read.All|"Odczyt wyników zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Score.Read|"Odczyt wyników zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/exposureScore/ByMachineGroups
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
---|---|---
|Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda zwróci wartość 200 OK, z listą wyników ekspozycji dla każdego urządzenia w grupie danych w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="example-request"></a>Przykładowe żądanie

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/exposureScore/ByMachineGroups
```

### <a name="example-response"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ExposureScore",
    "value": [
        {
            "time": "2019-12-03T09:51:28.214338Z",
            "score": 41.38041766305988,
            "rbacGroupName": "GroupOne"
        },
        {
            "time": "2019-12-03T09:51:28.2143399Z",
            "score": 37.403726933165366,
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie zagrożeniami opartymi na & i zagrożeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Ocena & zagrożenia lub luki w zabezpieczeniach](/microsoft-365/security/defender-endpoint/tvm-exposure-score)
