---
title: Uzyskiwanie brakującej kb/s przez identyfikator oprogramowania
description: Pobiera brakujące aktualizacje zabezpieczeń za pomocą identyfikatora oprogramowania
keywords: apis, api Graph, obsługiwane api, get, list, file, information, software id, threat & zarządzanie lukami w zabezpieczeniach api, Microsoft Defender for Endpoint tvm api
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
ms.openlocfilehash: 692d0ca44a46ef11bd7ab3e9bb32a0c98dd7e01a
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996304"
---
# <a name="get-missing-kbs-by-software-id"></a>Uzyskiwanie brakującej kb/s przez identyfikator oprogramowania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera brakujące kb/kb (aktualizacje zabezpieczeń) według identyfikatora oprogramowania

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Software.Read.All|"Odczyt informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Software.Read|"Odczyt informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/Software/{Id}/getmissingkbs
```

## <a name="request-header"></a>Nagłówek wniosku

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda zwróci wartość 200 OK, przy określonym oprogramowaniu brakujące dane KB w treści.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/getmissingkbs
```

### <a name="response"></a>Odpowiedź

Oto przykład odpowiedzi.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
         {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "edge"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 240,
            "cveAddressed": 14
         },
         ...
        ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie zagrożeniami opartymi na & i zagrożeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Wykaz & i luk w zabezpieczeniach](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
