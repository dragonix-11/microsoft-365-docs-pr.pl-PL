---
title: Pobierz interfejs API kolekcji stanów zabezpieczeń komputerów
description: Pobierz kolekcję stanów zabezpieczeń urządzeń za pomocą programu Microsoft Defender dla punktu końcowego.
keywords: apis, api Graph, obsługiwane api, get, device, security, state
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.custom: api
ms.openlocfilehash: 91df2aab70b2bb8edb46700feefdae59df4ac68b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998123"
---
# <a name="get-machines-security-states-collection-api"></a>Get Machines security states collection API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera kolekcję stanów zabezpieczeń urządzeń.

## <a name="permissions"></a>Uprawnienia

Użytkownik potrzebuje uprawnień do odczytu.

## <a name="http-request"></a>Żądanie HTTP

```http
GET /testwdatppreview/machinesecuritystates
```

## <a name="request-headers"></a>Żądaj nagłówków

Nagłówek|Value
:---|:---
Autoryzacja|Użytkownik {token}. **Wymagane**.
Typ zawartości|application/json

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli się powiedzie — 200 OK.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład prośby.

```http
GET https://graph.microsoft.com/testwdatppreview/machinesecuritystates
Content-type: application/json
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

Identyfikator *pola* zawiera identyfikator urządzenia i jest równy identyfikatorowi *pola** w informacjach o urządzeniach.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineSecurityStates",
    "@odata.count":444,
    "@odata.nextLink":"https://graph.microsoft.com/testwdatppreview/machinesecuritystates?$skiptoken=[continuation token]",
    "value":[
        {
            "id":"000050e1b4afeee3742489ede9ad7a3e16bbd9c4",
            "build":14393,
            "revision":2485,
            "architecture":"Amd64",
            "osVersion":"10.0.14393.2485.amd64fre.rs1_release.180827-1809",
            "propertiesRequireAttention":[
                "AntivirusNotReporting",
                "EdrImpairedCommunications"
            ]
        },
        ...
    ]
}
```
