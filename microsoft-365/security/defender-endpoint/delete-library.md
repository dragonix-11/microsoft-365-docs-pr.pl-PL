---
title: Usuwanie pliku z biblioteki odpowiedzi na żywo
description: Dowiedz się, jak usunąć plik z biblioteki odpowiedzi na żywo.
keywords: apis, graph api, obsługiwane interfejsy API, usuwanie z biblioteki
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
ms.openlocfilehash: 97a2a2152a60ff542cb946c4283fe3f26c4b9c8e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874135"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Usuwanie pliku z biblioteki odpowiedzi na żywo  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Usuń plik z biblioteki odpowiedzi na żywo.

## <a name="limitations"></a>Ograniczenia

1.  Ograniczenia szybkości dla tego interfejsu API to 100 wywołań na minutę i 1500 wywołań na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).

| Typ uprawnień                    | Uprawnienia     | Nazwa wyświetlana uprawnień        |
|------------------------------------|----------------|--------------------------------|
| Aplikacja                        | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |
| Delegowane (konto służbowe) | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |

## <a name="http-request"></a>Żądanie HTTP

USUNĄĆ https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>Nagłówki żądań

| Name (Nazwa)            | Wpisać   | Opis               |
|-----------------|--------|---------------------------|
| Autoryzacji   | Ciąg | Okaziciela\<token>\. Wymagane. |

## <a name="request-body"></a>Treść żądania

Pusty

## <a name="response"></a>Odpowiedzi

-   Jeśli plik istnieje w bibliotece i został pomyślnie usunięty 204 Brak zawartości.

-   Jeśli nie odnaleziono określonej nazwy pliku 404 Nie znaleziono.

## <a name="example"></a>Przykład

Żądanie

Oto przykład żądania.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>Temat pokrewny
- [Uruchom reagowanie w czasie rzeczywistym](run-live-response.md) 