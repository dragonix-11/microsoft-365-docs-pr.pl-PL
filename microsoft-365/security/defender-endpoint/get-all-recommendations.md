---
title: Wyeksymuj wszystkie zalecenia
description: Pobiera listę wszystkich zaleceń dotyczących zabezpieczeń mających wpływ na organizację.
keywords: apis, graph api, supported api, get, security recommendations, Microsoft Defender for Endpoint tvm api, Zarządzanie zagrożeniami i lukami, Zarządzanie zagrożeniami i lukami api
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
ms.openlocfilehash: 727b20e6784016aac423a74c6b564fa96d6f5733
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996354"
---
# <a name="list-all-recommendations"></a>Wyeksymuj wszystkie zalecenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobiera listę wszystkich zaleceń dotyczących zabezpieczeń mających wpływ na organizację.


## <a name="api-description"></a>Opis interfejsu API

Zwraca informacje na temat wszystkich zaleceń dotyczących zabezpieczeń mających wpływ na organizację.

*Adres URL:* GET:/api/recommendations
<br>Obsługuje [zapytania OData w wersji 4](https://www.odata.org/documentation/).
<br>Operatory obsługiwane przez usługę OData:
<br>```$filter```on, ```id``````productName```, ```vendor```, ```recommendedVersion```, ```recommendationCategory```, ```subCategory```, ```severityScore``````remediationType```, ```recommendedProgram```, , ```recommendedVendor```, i ```status``` properties.
<br>```$top``` z wartością maksymalną 10 000.
<br>```$skip```.
<br>Zobacz przykłady w [zapytaniach OData za pomocą programu Microsoft Defender for Endpoint](exposed-apis-odata-samples.md).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|SecurityRecommendation.Read.All|"Przeczytaj informacje o zaleceniach dotyczących bezpieczeństwa w zakresie zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|SecurityRecommendation.Read |"Przeczytaj informacje o zaleceniach dotyczących bezpieczeństwa w zakresie zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/recommendations
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK z listą zaleceń dotyczących zabezpieczeń w treści.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations
```

### <a name="response"></a>Odpowiedź

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11",
            "productName": "windows_10" "Windows_11",
            "recommendationName": "Update Windows 10" "Update Windows 11",
            "weaknesses": 397,
            "vendor": "microsoft",
            "recommendedVersion": "",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": true,
            "activeAlert": false,
            "associatedThreats": [
                "3098b8ef-23b1-46b3-aed4-499e1928f9ed",
                "40c189d5-0330-4654-a816-e48c2b7f9c4b",
                "4b0c9702-9b6c-4ca2-9d02-1556869f56f8",
                "e8fc2121-3cf3-4dd2-9ea0-87d7e1d2b29d",
                "94b6e94b-0c1d-4817-ac06-c3b8639be3ab"
            ],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 7.674418604651163,
            "totalMachineCount": 37,
            "exposedMachinesCount": 7,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Windows 10" "Windows 11"
        }
        ...
     ]
}
```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie zagrożeniami opartymi na & i zagrożeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Zalecenie & zabezpieczeń dotyczące zagrożeń i luk w zabezpieczeniach](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
