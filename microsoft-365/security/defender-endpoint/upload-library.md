---
title: Przekazywanie plików do biblioteki odpowiedzi na żywo
description: Dowiedz się, jak przekazać plik do biblioteki odpowiedzi na żywo.
keywords: apis, graph api, obsługiwane interfejsy API, przekazywanie do biblioteki
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
ms.openlocfilehash: 8e0bc9ca78a7e0baad7c07e73790215618aff9ab
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873744"
---
#  <a name="upload-files-to-the-live-response-library"></a>Przekazywanie plików do biblioteki odpowiedzi na żywo  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Przekaż plik do biblioteki odpowiedzi na żywo.

## <a name="limitations"></a>Ograniczenia

1.  Ograniczenie maksymalnego rozmiaru pliku wynosi 20 MB.

2.  Ograniczenia szybkości dla tego interfejsu API to 100 wywołań na minutę i 1500 wywołań na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).


| Typ uprawnień                    | Uprawnienia     | Nazwa wyświetlana uprawnień        |
|------------------------------------|----------------|--------------------------------|
| Aplikacja                        | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |
| Delegowane (konto służbowe) | Library.Manage | Zarządzanie biblioteką odpowiedzi na żywo |

## <a name="http-request"></a>Żądanie HTTP

Przesłać

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>Nagłówki żądań

|  Name (Nazwa)   |    Wpisać    |       Opis                         |
|-----------------|--------|--------------------------------|
| Autoryzacji   | Ciąg | Nośnik\<token>. Wymagane.      |
| Typ zawartości    | Ciąg | multipart/form-data. Wymagane. |

## <a name="request-body"></a>Treść żądania

W treści żądania podaj obiekt form-data z następującymi parametrami:

| Parametr         |     Wpisać         |       Opis                                        |
|-----------------------|--------------|------------------------------------------------------------|
| Plik                  | Zawartość pliku | Plik, który ma zostać przekazany do biblioteki odpowiedzi na żywo. Wymagane |
| Opis           | Ciąg       | Opis pliku.                                  |
| ParametersDescription | Ciąg       | (Opcjonalnie) Parametry wymagane do uruchomienia skryptu. Wartość domyślna to pusty ciąg.                |
| OverrideIfExists      | Wartość logiczna      | (Opcjonalnie) Czy zastąpić plik, jeśli już istnieje. Wartość domyślna to pusty ciąg.          |



## <a name="response"></a>Odpowiedzi

-   W przypadku powodzenia ta metoda zwraca kod odpowiedzi 200 — OK i przekazaną jednostkę biblioteki odpowiedzi na żywo w treści odpowiedzi.

-   Jeśli nie powiedzie się: ta metoda zwraca wartość 400 — nieprawidłowe żądanie.  
    Nieprawidłowe żądanie zwykle wskazuje nieprawidłową treść.

## <a name="example"></a>Przykład

Żądanie

Oto przykład żądania przy użyciu narzędzia curl.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>Temat pokrewny

-  [Uruchom reagowanie w czasie rzeczywistym](run-live-response.md) 