---
title: Pobierz wykryte luki w zabezpieczeniach
description: Pobiera kolekcję wykrytych luk w zabezpieczeniach związanych z danym identyfikatorem urządzenia.
keywords: apis, graph api, supported apis, get, list, file, information, discovered vulnerabilities, threat & zarządzanie lukami w zabezpieczeniach api, Ochrona punktu końcowego w usłudze Microsoft Defender tvm api
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
ms.openlocfilehash: 6b3271637b1b275fe26d07975d0592bf1e7ae672
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840480"
---
# <a name="get-discovered-vulnerabilities"></a>Pobierz wykryte luki w zabezpieczeniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API
Pobiera kolekcję wykrytych luk w zabezpieczeniach związanych z danym identyfikatorem urządzenia.

## <a name="limitations"></a>Ograniczenia
1. Ograniczenia szybkości dla tego interfejsu API to 50 wywołań na minutę i 1500 wywołań na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Korzystanie z interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)

Typ uprawnień | Uprawnienia | Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja |Vulnerability.Read.All | "Odczytywanie informacji o lukach w zabezpieczeniach dotyczących zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe) | Luka w zabezpieczeniach.Odczyt | "Odczytywanie informacji o lukach w zabezpieczeniach dotyczących zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{machineId}/vulnerabilities
```

## <a name="request-headers"></a>Nagłówki żądań

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacji | Ciąg | Element nośny {token}. **Wymagane**.

## <a name="request-body"></a>Treść żądania

Pusty

## <a name="response"></a>Odpowiedzi

W przypadku powodzenia ta metoda zwraca wartość 200 OK z informacjami o wykrytej lukie w zabezpieczeniach w treści.

## <a name="example"></a>Przykład

### <a name="request"></a>Żądanie

Oto przykład żądania.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/vulnerabilities
```

### <a name="response"></a>Odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
        {
            "id": "CVE-2019-1348",
            "name": "CVE-2019-1348",
            "description": "Git could allow a remote attacker to bypass security restrictions, caused by a flaw in the --export-marks option of git fast-import. By persuading a victim to import specially-crafted content, an attacker could exploit this vulnerability to overwrite arbitrary paths.",
            "severity": "Medium",
            "cvssV3": 4.3,
            "exposedMachines": 1,
            "publishedOn": "2019-12-13T00:00:00Z",
            "updatedOn": "2019-12-13T00:00:00Z",
            "publicExploit": false,
            "exploitVerified": false,
            "exploitInKit": false,
            "exploitTypes": [],
            "exploitUris": []
        }
    ]
}
```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie lukami w zabezpieczeniach opartymi na ryzyku & zagrożeń](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Luki w zabezpieczeniach w organizacji](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
