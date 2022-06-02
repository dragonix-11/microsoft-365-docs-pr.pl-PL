---
title: Pobierz rekomendacje dotyczące zabezpieczeń
description: Pobiera kolekcję zaleceń dotyczących zabezpieczeń związanych z danym identyfikatorem urządzenia.
keywords: apis, graph api, supported apis, get, list, file, information, security recommendation per device, threat & zarządzanie lukami w zabezpieczeniach api, Ochrona punktu końcowego w usłudze Microsoft Defender tvm api
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
ms.openlocfilehash: ebe07abd4e7f87e7abfe4d4a8ccd131e20dc4958
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839717"
---
# <a name="get-security-recommendations"></a>Pobierz rekomendacje dotyczące zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobiera kolekcję zaleceń dotyczących zabezpieczeń związanych z danym identyfikatorem urządzenia.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Korzystanie z interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|SecurityRecommendation.Read.All|"Przeczytaj informacje o zaleceniach dotyczących zabezpieczeń zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|SecurityRecommendation.Read|"Przeczytaj informacje o zaleceniach dotyczących zabezpieczeń zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{machineId}/recommendations
```

## <a name="request-headers"></a>Nagłówki żądań

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacji|Ciąg|Element nośny {token}. **Wymagane**.

## <a name="request-body"></a>Treść żądania

Pusty

## <a name="response"></a>Odpowiedzi

W przypadku powodzenia ta metoda zwraca wartość 200 OK z zaleceniami dotyczącymi zabezpieczeń w treści.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład żądania.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/recommendations
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-git-scm-_-git",
            "productName": "git",
            "recommendationName": "Update Git to version 2.24.1.2",
            "weaknesses": 3,
            "vendor": "git-scm",
            "recommendedVersion": "2.24.1.2",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": false,
            "activeAlert": false,
            "associatedThreats": [],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 0,
            "totalMachineCount": 0,
            "exposedMachinesCount": 1,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Git"
        },
...
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie lukami w zabezpieczeniach opartymi na ryzyku & zagrożeń](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Zalecenie dotyczące zabezpieczeń luk w zabezpieczeniach & zagrożeń](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
