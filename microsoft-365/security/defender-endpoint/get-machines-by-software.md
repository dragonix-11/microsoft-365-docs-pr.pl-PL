---
title: Lista urządzeń według oprogramowania
description: Pobierz listę urządzeń, na których jest zainstalowane to oprogramowanie.
keywords: apis, api Graph, obsługiwane api, get, lista urządzeń, lista urządzeń, urządzenia listy urządzeń według oprogramowania, Microsoft Defender for Endpoint tvm api
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
ms.openlocfilehash: 32dd0531d0919613621d656f7f3b9aef3e4bec0d
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996334"
---
# <a name="list-devices-by-software"></a>Lista urządzeń według oprogramowania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobierz listę odwołań do urządzeń, na których jest zainstalowane to oprogramowanie.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Software.Read.All|"Odczyt informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Software.Read|"Odczyt informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/Software/{Id}/machineReferences 
```

## <a name="request-headers"></a>Żądaj nagłówków

|Name (Nazwa)|Wpisać|Opis
|---|---|---|
|Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda zwróci wartość 200 OK i listę urządzeń z zainstalowanym oprogramowaniem w treści. 

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/machineReferences
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json

{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "7c7e1896fa39efb0a32a2cf421d837af1b9bf762",
            "computerDnsName": "dave_desktop",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        },
        {
            "id": "7d5cc2e7c305e4a0a290392abf6707f9888fda0d",
            "computerDnsName": "jane_PC",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie zagrożeniami opartymi na & i zagrożeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Wykaz & i luk w zabezpieczeniach](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
