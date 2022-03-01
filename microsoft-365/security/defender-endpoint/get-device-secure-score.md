---
title: Uzyskiwanie wyniku bezpiecznego urządzenia
description: Pobiera bezpieczny wynik dla urządzenia organizacyjnego.
keywords: apis, api Graph, obsługiwane api, get, alerts, recent
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
ms.openlocfilehash: 69385a5a1da4b9e91084b4fc524334956c2d8403
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996249"
---
# <a name="get-device-secure-score"></a>Uzyskiwanie wyniku bezpiecznego urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera wynik [bezpiecznego połączenia firmy Microsoft dla urządzeń](tvm-microsoft-secure-score-devices.md). Wyższy wynik bezpiecznego punktu końcowego firmy Microsoft dla urządzeń oznacza, że punkty końcowe są bardziej odporne na ataki zagrożenia bezpieczeństwa bezpieczeństwa.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Score.Read.All|"Odczyt wyników zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Score.Read|"Odczyt wyników zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/configurationScore
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK, przy użyciu danych dotyczących bezpiecznego wyniku urządzenia w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/configurationScore
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

> [!NOTE]
> Wyświetlana tutaj lista odpowiedzi może zostać obcięta w celu zwięzłego wypowiedzeń.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ConfigurationScore/$entity",
    "time": "2019-12-03T09:15:58.1665846Z",
    "score": 340
}
```

## <a name="see-also"></a>Zobacz też

- [Zapytania OData za pomocą programu Microsoft Defender dla punktu końcowego](exposed-apis-odata-samples.md)
