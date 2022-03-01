---
title: Lista urządzeń według zaleceń
description: Pobiera listę urządzeń skojarzonych z zaleceniem zabezpieczeń.
keywords: apis, api Graph, obsługiwane api, get, security recommendation dla urządzeń wymagających ochrony, Zarządzanie zagrożeniami i lukami, Zarządzanie zagrożeniami i lukami api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: b30c558c2e202000145c89e9ab5a122d0dbe6283
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996307"
---
# <a name="list-devices-by-recommendation"></a>Lista urządzeń według zaleceń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobiera listę urządzeń skojarzonych z zaleceniem zabezpieczeń.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|SecurityRecommendation.Read.All|"Przeczytaj informacje o zaleceniach dotyczących bezpieczeństwa w zakresie zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|SecurityRecommendation.Read|"Przeczytaj informacje o zaleceniach dotyczących bezpieczeństwa w zakresie zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/recommendations/{id}/machineReferences
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK z listą urządzeń skojarzonych z zaleceniem zabezpieczeń.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations/va-_-google-_-chrome/machineReferences
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "e058770379bc199a9c179ce52a23e16fd44fd2ee",
            "computerDnsName": "niw_pc",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie zagrożeniami opartymi na & i zagrożeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Zalecenie & zabezpieczeń dotyczące zagrożeń i luk w zabezpieczeniach](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
