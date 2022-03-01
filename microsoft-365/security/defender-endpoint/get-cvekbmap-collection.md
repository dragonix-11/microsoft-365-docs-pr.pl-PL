---
title: Uzyskiwanie interfejsu API mapy CVE-KB
description: Dowiedz się, jak za pomocą interfejsu API mapy CVE-KB pobrać mapę cves do kb/kb i szczegółów CVE w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, cve, kb
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
ms.openlocfilehash: d0672804d0d2a8221480fe76e4237114a88f4cfb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997311"
---
# <a name="get-cve-kb-map-api"></a>Uzyskiwanie interfejsu API mapy CVE-KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera mapę cves do szczegółów KB i CVE.

## <a name="permissions"></a>Uprawnienia

Użytkownik potrzebuje uprawnień do odczytu.

## <a name="http-request"></a>Żądanie HTTP

```http
GET /testwdatppreview/cvekbmap
```

## <a name="request-headers"></a>Żądaj nagłówków

Nagłówek|Value
:---|:---
Autoryzacja|Użytkownik {token}. **Wymagane**.
Typ zawartości|application/json

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiedzie i mapowanie już istnieje — 200 OK.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład prośby:

```http
GET https://graph.microsoft.com/testwdatppreview/CveKbMap
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi:

```json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#CveKbMap",
    "@odata.count": 4168,
    "value": [
        {
            "cveKbId": "CVE-2015-2482-3097617",
            "cveId": "CVE-2015-2482",
            "kbId":"3097617",
            "title": "Cumulative Security Update for Internet Explorer",
            "severity": "Critical"
        },
    ...
}
```
