---
title: Pliki biblioteki list
description: Dowiedz się, jak wyświetlić listę plików bibliotek odpowiedzi na żywo.
keywords: apis, graph api, obsługiwane api, get, devices
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9c9bf11856cf518a1cd387b88a3b70dc4a34cc91
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705580"
---
#  <a name="list-library-files"></a>Pliki biblioteki list 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy: Program** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Lista plików bibliotek odpowiedzi na żywo.

## <a name="limitations"></a>Ograniczenia

1.  Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).

|Typ uprawnień                       |      Uprawnienie          |  Nazwa wyświetlana uprawnień | 
|-----------------|--------|---------------------------|  
| Aplikacja                        | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |
| Delegowane (konto służbowe) | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |

## <a name="http-request"></a>Żądanie HTTP

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>Żądaj nagłówków

| Name (Nazwa)         |      Wpisać                     | Opis
|-----------------|--------|---------------------------|
| Autoryzacja   | Ciąg | Użytkownik {token}. Wymagane. |

## <a name="request-body"></a>Treść wniosku
Puste

## <a name="response"></a>Odpowiedź 
Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 — kod odpowiedzi OK z kolekcją jednostek pliku biblioteki odpowiedzi na żywo.

## <a name="example"></a>Przykład

**Zażądaj**

Oto przykład żądania, które pobiera wszystkie pliki bibliotek odpowiedzi na żywo

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```JSON
HTTP/1.1 200 Ok
Content-type: application/json
{
"\@odata.context": "https://api.securitycenter.microsoft.com
/api/\$metadata\#LibraryFiles",
"value": [
    {
    "fileName": "script1.ps1",
    "sha256": "6e212a0db618507c44e4ec8ee7499dfef7e5767e5f8d31144df3b96fd1145caf",
    "description": null,
    "creationTime": "2019-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2019-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": true,
    "parametersDescription": "test"
    },
    {
    "fileName": "script.sh",
    "sha256": "d0f3e3b0641dbf88ee39c822516e81a909d1d06d22341dd9b1f12aa5e5c027a2",
    "description": null,
    "creationTime": "2018-10-24T11:15:35.3688259Z",
    "lastUpdatedTime": "2018-10-24T11:15:35.3688259Z",
    "createdBy": "username",
    "hasParameters": false
    },
    {
    "fileName": "memdump.exe",
    "sha256": "fa70b87730290c0d30fe255d1dfb65de82f96286ebfeeb1d88ed3cc831329825",
    "description": "Process memory dump",
    "creationTime": "2018-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2018-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": false
    }
]
}
```


## <a name="related-topic"></a>Temat pokrewny
- [Uruchom odpowiedź na żywo](run-live-response.md) 