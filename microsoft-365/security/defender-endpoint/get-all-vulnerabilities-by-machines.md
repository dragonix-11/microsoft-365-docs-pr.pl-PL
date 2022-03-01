---
title: Uzyskiwanie wszystkich luk w zabezpieczeniach komputera i oprogramowania
description: Pobiera listę wszystkich luk w zabezpieczeniach mających wpływ na organizację, które mogą wystąpić na komputerze i w oprogramowaniu.
keywords: apis, api Graph, obsługiwane api, get, vulnerability information, Microsoft Defender for Endpoint tvm api
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
ms.openlocfilehash: 45c29a70f97c681e6236f4327fed8e344d9dc8ac
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996338"
---
# <a name="list-vulnerabilities-by-machine-and-software"></a>Lista luk w zabezpieczeniach komputera i oprogramowania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera listę wszystkich luk w zabezpieczeniach mających wpływ na organizację na [komputer](machine.md) i [oprogramowanie](software.md).

- Jeśli luka w zabezpieczeniach ma naprawić KB, pojawi się ona w odpowiedzi.
- Obsługuje [zapytania OData w wersji 4](https://www.odata.org/documentation/).
- Zapytanie OData jest obsługiwane `$filter` dla: `id`, `cveId`, `machineId`, `fixingKbId`, `productName`, `productVersion`, `severity`i `productVendor` właściwości.
<br>```$stop``` z maksymalną wartością 10 000
<br>```$skip```

> [!TIP]
> Jest to doskonały interfejs API [na Power BI integracji](api-power-bi.md).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Vulnerability.Read.All|"Odczyt informacji o lukach w zabezpieczeniach i zarządzaniu zagrożeniami"
Delegowane (konto służbowe)|Vulnerability.Read|"Odczyt informacji o lukach w zabezpieczeniach i zarządzaniu zagrożeniami"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/vulnerabilities/machinesVulnerabilities
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, zostanie wyświetlona wartość 200 OK z listą luk w treści.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/vulnerabilities/machinesVulnerabilities
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicAssetVulnerabilityDto)",
    "value": [
        {
            "id": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21-_-CVE-2020-6494-_-microsoft-_-edge_chromium-based-_-81.0.416.77-_-",
            "cveId": "CVE-2020-6494",
            "machineId": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21",
            "fixingKbId": null,
            "productName": "edge_chromium-based",
            "productVendor": "microsoft",
            "productVersion": "81.0.416.77",
            "severity": "Low"
        },
        {
            "id": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283-_-CVE-2016-3348-_-microsoft-_-windows_server_2012_r2-_-6.3.9600.19728-_-3185911",
            "cveId": "CVE-2016-3348",
            "machineId": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283",
            "fixingKbId": "3185911",
            "productName": "windows_server_2012_r2",
            "productVendor": "microsoft",
            "productVersion": "6.3.9600.19728",
            "severity": "Low"
        },
        ...
    ]

}
```

## <a name="see-also"></a>Zobacz też

- [Ryzykowne Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Luki w zabezpieczeniach w organizacji](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
