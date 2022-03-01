---
title: Interfejs API wskaźników importu
description: Dowiedz się, jak używać partii importowania interfejsu API wskaźnika w programie Microsoft Defender for Endpoint.
keywords: api, obsługiwane api, submit, ti, indicator, update
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
ms.custom: api
ms.openlocfilehash: 7306489e537e583055e037ce9d8ce04add248844
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996894"
---
# <a name="import-indicators-api"></a>Interfejs API wskaźników importu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Przesyła lub aktualizuje partię [jednostek](ti-indicator.md) wskaźników.

Notacja CIDR dla ip nie jest obsługiwana.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 30 połączeń na minutę.
2. Istnieje limit 15 000 aktywnych [wskaźników na](ti-indicator.md) dzierżawcę.
3. Maksymalny rozmiar partii dla jednego wywołania interfejsu API wynosi 500.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Ti.ReadWrite|"Wskaźniki odczytu i zapisu"
Aplikacja|Ti.ReadWrite.All|"Odczyt i pisanie wszystkich wskaźników"
Delegowane (konto służbowe)|Ti.ReadWrite|"Wskaźniki odczytu i zapisu"

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt JSON o następujących parametrach:

Parametr|Wpisać|Opis
:---|:---|:---
Wskaźniki|Wskaźnik<[listy](ti-indicator.md)>|Lista [wskaźników](ti-indicator.md). **Wymagane**

## <a name="response"></a>Odpowiedź

- Jeśli ta metoda zwróci wartość 200 — kod odpowiedzi OK z listą wyników importu według wskaźnika, zobacz przykład poniżej.
- Jeśli się nie powiedzie: ta metoda zwróci 400 — złe żądanie. Nieprawidłowe żądanie wskazuje zwykle niepoprawną treść.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

```json
{
    "Indicators":
    [
        {
            "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "demo",
            "application": "demo-test",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Informational",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": ["group1", "group2"]
        },
        {
            "indicatorValue": "2233223322332233223322332233223322332233223322332233223322332222",
            "indicatorType": "FileSha256",
            "title": "demo2",
            "application": "demo-test2",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Medium",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": []
        }
    ]
}
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "value": [
        {
            "id": "2841",
            "indicator": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "isFailed": false,
            "failureReason": null
        },
        {
            "id": "2842",
            "indicator": "2233223322332233223322332233223322332233223322332233223322332222",
            "isFailed": false,
            "failureReason": null
        }
    ]
}
```

## <a name="related-topic"></a>Temat pokrewny

- [Zarządzanie wskaźnikami](manage-indicators.md)
