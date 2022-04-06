---
title: Upload plików do biblioteki odpowiedzi na żywo
description: Dowiedz się, jak przekazać plik do biblioteki odpowiedzi na żywo.
keywords: apis, api Graph, obsługiwane api, przekazywanie do biblioteki
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
ms.openlocfilehash: 84ec7e361cccdc886650b0710f738a4315c4db8d
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705600"
---
#  <a name="upload-files-to-the-live-response-library"></a>Upload plików do biblioteki odpowiedzi na żywo  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Upload pliku do biblioteki odpowiedzi na żywo.

## <a name="limitations"></a>Ograniczenia

1.  Ograniczenie rozmiaru pliku o maksymalnym rozmiarze wynosi 20 MB.

2.  Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).


| Typ uprawnień                    | Uprawnienie     | Nazwa wyświetlana uprawnień        |
|------------------------------------|----------------|--------------------------------|
| Aplikacja                        | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |
| Delegowane (konto służbowe) | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |

## <a name="http-request"></a>Żądanie HTTP

Upload

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>Żądaj nagłówków

|  Name (Nazwa)   |    Wpisać    |       Opis                         |
|-----------------|--------|--------------------------------|
| Autoryzacja   | Ciąg | Nosiciel\<token>. Wymagane.      |
| Typ zawartości    | ciąg | multipart/form-data. Wymagane. |

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt form-data o następujących parametrach:

| Parametr         |     Wpisać         |       Opis                                        |
|-----------------------|--------------|------------------------------------------------------------|
| Plik                  | Zawartość pliku | Plik, który ma zostać przekazany do biblioteki odpowiedzi na żywo. Wymagane |
| Opis           | Ciąg       | Opis pliku.                                  |
| ParametersDescription | Ciąg       | (Opcjonalnie) Parametry wymagane do uruchomienia skryptu. Wartość domyślna jest ciągiem pustym.                |
| OverrideIfExists      | Wartość logiczna      | (Opcjonalnie) Czy zastąpić plik, jeśli już istnieje. Wartość domyślna jest ciągiem pustym.          |



## <a name="response"></a>Odpowiedź

-   Jeśli ta metoda powiedzie się, ta metoda zwróci wartość 200 — kod odpowiedzi OK i przekazany encję biblioteki odpowiedzi na żywo w treści odpowiedzi.

-   Jeśli nie uda się: ta metoda zwraca wartość 400 — złe żądanie.  
    Nieprawidłowe żądanie wskazuje zwykle niepoprawną treść.

## <a name="example"></a>Przykład

Zażądaj

Oto przykład żądania przy użyciu funkcji curl.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>Temat pokrewny

-  [Uruchom odpowiedź na żywo](run-live-response.md) 