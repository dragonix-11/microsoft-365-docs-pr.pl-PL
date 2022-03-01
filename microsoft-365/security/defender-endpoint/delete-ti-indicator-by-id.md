---
title: Interfejs API wskaźnika usuwania.
description: Dowiedz się, jak za pomocą interfejsu API Delete Indicator usunąć jednostkę Indicator według identyfikatora w programie Microsoft Defender for Endpoint.
keywords: api, publiczny interfejs API, obsługiwane api, delete, ti indicator, entity, id
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
ms.openlocfilehash: 6122c50018bb44f0e5812263339a7644868fd0d2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996217"
---
# <a name="delete-indicator-api"></a>Interfejs API usuwania wskaźnika

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Opis interfejsu API

Usuwa [jednostkę Wskaźnik](ti-indicator.md) według identyfikatora.

## <a name="limitations"></a>Ograniczenia

Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja | Ti.ReadWrite | "Odczyt i pisanie wskaźników TI"
Aplikacja | Ti.ReadWrite.All | "Wskaźniki odczytu i zapisu"

## <a name="http-request"></a>Żądanie HTTP

```http
Delete https://api.securitycenter.microsoft.com/api/indicators/{id}
```

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wskaźnik istnieje i zostanie pomyślnie usunięty — 204 ok bez zawartości.

Jeśli nie znaleziono wskaźnika o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
DELETE https://api.securitycenter.microsoft.com/api/indicators/995
```
