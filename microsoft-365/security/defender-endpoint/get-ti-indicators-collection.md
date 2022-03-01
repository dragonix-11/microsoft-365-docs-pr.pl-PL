---
title: Interfejs API wskaźników listy
description: Dowiedz się, jak używać interfejsu API Wskaźników listy w celu pobrania kolekcji wszystkich aktywnych wskaźników w programie Microsoft Defender for Endpoint.
keywords: apis, public api, supported apis, Indicators collection
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: adc3cfecba10431a909b72f875442d80b6638f03
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996895"
---
# <a name="list-indicators-api"></a>Interfejs API wskaźników listy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera kolekcję wszystkich aktywnych [wskaźników](ti-indicator.md).

Obsługuje [zapytania OData w wersji 4](https://www.odata.org/documentation/).

Zapytanie OData jest obsługiwane `$filter` na: `application`, `createdByDisplayName`, `expirationTime`, `generateAlert`, `title`, `rbacGroupNames`, `rbacGroupIds``indicatorValue`, `indicatorType`, `creationTimeDateTimeUtc`, , `createdBy`, `action`i właściwości`severity`.
<br>```$stop``` z wartością maksymalną 10 000. 
<br>```$skip```.

Zobacz przykłady w [zapytaniach OData za pomocą programu Microsoft Defender dla punktu końcowego](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę. 

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Ti.ReadWrite|"Wskaźniki odczytu i zapisu"
Aplikacja|Ti.ReadWrite.All|"Odczyt i pisanie wszystkich wskaźników"
Delegowane (konto służbowe)|Ti.ReadWrite|"Wskaźniki odczytu i zapisu"

## <a name="http-request"></a>Żądanie HTTP

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200, kod odpowiedzi OK z kolekcją obiektów [Indicator](ti-indicator.md) .

> [!NOTE]
> Jeśli aplikacja ma uprawnienia "Ti.ReadWrite.All", zostanie ona ujawniona dla wszystkich wskaźników. W przeciwnym razie będzie ona dostępna tylko dla utworzonych przez niego wskaźników.

## <a name="example-1"></a>Przykład 1

### <a name="example-1-request"></a>Przykład 1 żądania

Oto przykład żądania, które pobiera wszystkie wskaźniki

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

### <a name="example-1-response"></a>Przykład 1. Odpowiedź

Oto przykład odpowiedzi.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "995",
            "indicatorValue": "12.13.14.15",
            "indicatorType": "IpAddress",
            "action": "Alert",
            "application": "demo-test",
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T11:15:35.3688259Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "test",
            "rbacGroupNames": []
        },
        {
            "id": "996",
            "indicatorValue": "220e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```

## <a name="example-2"></a>Przykład 2

### <a name="example-2-request"></a>Przykład 2. Żądanie

Oto przykład żądania, które pobiera wszystkie wskaźniki z akcją "AlertAndBlock" 

```http
GET https://api.securitycenter.microsoft.com/api/indicators?$filter=action+eq+'AlertAndBlock'
```

### <a name="example-2-response"></a>Przykład 2 odpowiedzi

Oto przykład odpowiedzi.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "997",
            "indicatorValue": "111e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```
