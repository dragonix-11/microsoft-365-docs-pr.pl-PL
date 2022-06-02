---
title: Brakujące bazy danych według identyfikatora urządzenia
description: Pobiera brakujące aktualizacje zabezpieczeń według identyfikatora urządzenia
keywords: apis, graph api, supported apis, get, list, file, information, device id, threat & zarządzanie lukami w zabezpieczeniach api, Ochrona punktu końcowego w usłudze Microsoft Defender tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4a570851263b6a52193353e2c229e2df47b677e3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840326"
---
# <a name="get-missing-kbs-by-device-id"></a>Brakujące bazy danych według identyfikatora urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera brakujące bazy danych (aktualizacje zabezpieczeń) według identyfikatora urządzenia

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{machineId}/getmissingkbs
```
## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane następujące uprawnienie. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md).

Typ uprawnień | Uprawnienia | Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja | Software.Read.All | "Odczytywanie informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="request-header"></a>Nagłówek żądania

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacji | Ciąg | Element nośny {token}. **Wymagane**.

## <a name="request-body"></a>Treść żądania

Pusty

## <a name="response"></a>Odpowiedzi

Jeśli to się powiedzie, ta metoda zwróci wartość 200 OK, a na określonym urządzeniu brakuje danych kb w treści.

## <a name="example"></a>Przykład

### <a name="request"></a>Żądanie

Oto przykład żądania.

```http
GET https://api.securitycenter.microsoft.com/api/machines/2339ad14a01bd0299afb93dfa2550136057bff96/getmissingkbs 
```

### <a name="response"></a>Odpowiedzi

Oto przykład odpowiedzi.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
        {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "windows_10",
                "edge",
                "internet_explorer"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 1,
            "cveAddressed": 97
        }
        ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie lukami w zabezpieczeniach opartymi na ryzyku & zagrożeń](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Spis oprogramowania z lukami w zabezpieczeniach & zagrożeń](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
