---
title: Usuwanie pliku z biblioteki odpowiedzi na żywo
description: Dowiedz się, jak usunąć plik z biblioteki odpowiedzi na żywo.
keywords: apis, api Graph, obsługiwane api, usuwanie z biblioteki
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
ms.openlocfilehash: 23625c8b7160d604df5f3a8b1b1387fc31027acf
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705560"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Usuwanie pliku z biblioteki odpowiedzi na żywo  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Usuwanie pliku z biblioteki odpowiedzi na żywo.

## <a name="limitations"></a>Ograniczenia

1.  Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).

| Typ uprawnień                    | Uprawnienie     | Nazwa wyświetlana uprawnień        |
|------------------------------------|----------------|--------------------------------|
| Aplikacja                        | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |
| Delegowane (konto służbowe) | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |

## <a name="http-request"></a>Żądanie HTTP

DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>Żądaj nagłówków

| Name (Nazwa)            | Wpisać   | Opis               |
|-----------------|--------|---------------------------|
| Autoryzacja   | Ciąg | Bearer\<token>\. Wymagane. |

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

-   Jeśli plik istnieje w bibliotece i pomyślnie usunięto 204 Brak zawartości.

-   Jeśli nie można odnaleźć 404 nie znaleziono określonej nazwy pliku.

## <a name="example"></a>Przykład

Zażądaj

Oto przykład wniosku.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>Temat pokrewny
- [Uruchom odpowiedź na żywo](run-live-response.md) 