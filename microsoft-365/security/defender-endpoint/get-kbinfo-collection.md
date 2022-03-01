---
title: Pobierz interfejs API kolekcji KB
description: Pobierz zbiór baz wiedzy (KB) i szczegóły bazy wiedzy za pomocą programu Microsoft Defender for Endpoint.
keywords: apis, graph api, obsługiwane api, get, kb
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ROBOTS: NOINDEX
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 31edd825a20e1f466b2ace4ea3030a10dcdeb3cd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997309"
---
# <a name="get-kb-collection-api"></a>Pobierz interfejs API kolekcji KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera kolekcję szczegółów KB i KB.

## <a name="permissions"></a>Uprawnienia

Użytkownik potrzebuje uprawnień do odczytu.

## <a name="http-request"></a>Żądanie HTTP

```http
GET /testwdatppreview/kbinfo
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

Oto przykład wniosku.

```http
GET https://graph.microsoft.com/testwdatppreview/KbInfo
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://graph.microsoft.com/testwdatppreview/$metadata#KbInfo",
    "@odata.count": 271,
    "value":[
        {
            "id": "KB3097617 (10240.16549) Amd64",
            "release": "KB3097617 (10240.16549)",
            "publishingDate": "2015-10-16T21:00:00Z",
            "version": "10.0.10240.16549",
            "architecture": "Amd64"
        },
        ...
}
```
