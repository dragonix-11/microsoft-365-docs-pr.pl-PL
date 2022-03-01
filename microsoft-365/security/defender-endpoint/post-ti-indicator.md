---
title: Interfejs API przesyłania lub aktualizowania wskaźnika
description: Dowiedz się, jak za pomocą interfejsu API przesyłania lub aktualizowania wskaźnika przesyłać lub aktualizować nową jednostkę Indicator w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, submit, ti, indicator, update
ms.prod: m365-security
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
ms.openlocfilehash: a3fc1a0ce2f7d02ad8ed6804b99621f78fb859d3
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010452"
---
# <a name="submit-or-update-indicator-api"></a>Interfejs API przesyłania lub aktualizowania wskaźnika

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Przesyła lub aktualizuje nową [jednostkę Wskaźnik](ti-indicator.md) .

Notacja CIDR dla ip nie jest obsługiwana.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.
2. Istnieje limit 15 000 aktywnych wskaźników na dzierżawcę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Ti.ReadWrite|"Wskaźniki odczytu i zapisu"
Aplikacja|Ti.ReadWrite.All|"Odczyt i pisanie wszystkich wskaźników"
Delegowane (konto służbowe)|Ti.ReadWrite|"Wskaźniki odczytu i zapisu"

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators
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
indicatorValue|Ciąg|Tożsamość [encji Wskaźnik](ti-indicator.md) . **Wymagane**
indicatorType (Typ wskaźnika)|Wyli roku|Typ wskaźnika. Dopuszczalne wartości: "FileSha1", "FileMd5", "CertificateThumbprint", "FileSha256", "IpAddress", "DomainName" i "Url". **Wymagane**
akcja|Wyli roku|Akcja, która zostanie podjęta, jeśli wskaźnik zostanie wykryty w organizacji. Dopuszczalne wartości to: "Alert", "Ostrzeżenie", "Blok", "Inspekcja, "BlokujAndRemediate", "AlertAndBlock" i "Dozwolone". **Wymagane**. Parametr "GenerateAlert" musi mieć ustawioną wartość "TRUE" podczas tworzenia akcji o wartości "Inspekcja".
aplikacja|Ciąg|Aplikacja skojarzona ze wskaźnikiem. To pole działa tylko w przypadku nowych wskaźników. Nie zaktualizuje on wartości na istniejącym wskaźniku. **Opcjonalne**
tytuł|Ciąg|Tytuł alertu wskaźnika. **Wymagane**
opis|Ciąg|Opis wskaźnika. **Wymagane**
expirationTime|DateTimeOffset|Czas wygaśnięcia wskaźnika. **Opcjonalne**
ważność|Wyli roku|Ważność wskaźnika. Dopuszczalne wartości to: "Informacyjne", "Niskie", "Średnie" i "Wysokie". **Opcjonalne**
zalecaneActions|Ciąg|Alert wskaźnika TI: zalecane działania. **Opcjonalne**
rbacGroupNames|Ciąg|Rozdzielana przecinkami lista nazw grup RBAC, do których zostanie zastosowany wskaźnik. **Opcjonalne**
generateAlert|Wyli roku|**Ma wartość True** (Prawda), jeśli wymagane jest generowanie alertu, **fałsz** , jeśli ten wskaźnik nie powinien generować alertu.
## <a name="response"></a>Odpowiedź

- Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 — OK kodu odpowiedzi i utworzoną /zaktualizowaną jednostkę [Wskaźnik](ti-indicator.md) w treści odpowiedzi.
- Jeśli się nie powiedzie: ta metoda zwróci 400 — złe żądanie. Nieprawidłowe żądanie wskazuje zwykle niepoprawną treść.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

```json
{
    "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
    "indicatorType": "FileSha1",
    "title": "test",
    "application": "demo-test",
    "expirationTime": "2020-12-12T00:00:00Z",
    "action": "AlertAndBlock",
    "severity": "Informational",
    "description": "test",
    "recommendedActions": "nothing",
    "rbacGroupNames": ["group1", "group2"]
}
```

## <a name="related-topic"></a>Temat pokrewny

- [Zarządzanie wskaźnikami](manage-indicators.md)
