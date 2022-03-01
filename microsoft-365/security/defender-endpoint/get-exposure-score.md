---
title: Uzyskaj wynik ekspozycji
description: Pobiera ocenę ekspozycji organizacyjnej.
keywords: apis, api Graph, obsługiwane api, get, exposure score, organizational exposure score
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
ms.openlocfilehash: 478f109d1f519e8d931716ce90bdcc979fed4b33
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996368"
---
# <a name="get-exposure-score"></a>Uzyskaj wynik ekspozycji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobiera ocenę ekspozycji organizacyjnej.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Score.Read.All|"Odczyt wyników zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Score.Read|"Odczyt wyników zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/exposureScore
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
---|---|---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda zwróci wartość 200 OK, z danymi na temat ekspozycji w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/exposureScore
```

### <a name="response"></a>Odpowiedź

Oto przykład odpowiedzi.

> [!NOTE]
> Wyświetlana tutaj lista odpowiedzi może zostać obcięta w celu zwięzłego wypowiedzeń.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ExposureScore/$entity",
    "time": "2019-12-03T07:23:53.280499Z",
    "score": 33.491554051195706
}
```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie zagrożeniami opartymi na & i zagrożeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Ocena & zagrożenia lub luki w zabezpieczeniach](/microsoft-365/security/defender-endpoint/tvm-exposure-score)
