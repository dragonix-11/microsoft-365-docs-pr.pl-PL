---
title: Uzyskiwanie interfejsu API zdarzenia
description: Dowiedz się, jak za pomocą interfejsu API uzyskaj informacje o zdarzeniach w celu uzyskania pojedynczego zdarzenia w aplikacji Microsoft 365 Defender.
keywords: apis, api Graph, obsługiwane api, get, file, hash
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 8861dc3752d2c4cc798bc83475f6a51f8245191a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983570"
---
# <a name="get-incident-information-api"></a>Interfejs API informacji o zdarzeniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera określone zdarzenie na pomocą jego identyfikatora.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Incident.Read.All|"Czytaj wszystkie zdarzenia"
Aplikacja|Incident.ReadWrite.All|"Czytanie i pisanie wszystkich zdarzeń"
Delegowane (konto służbowe)|Incident.Read|"Zdarzenia przeczytania"
Delegowane (konto służbowe)|Incident.ReadWrite|"Czytanie i pisanie zdarzeń"

> [!NOTE]
>
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych"
> - Odpowiedź będzie dotyczyć tylko zdarzeń, na które użytkownik jest

## <a name="http-request"></a>Żądanie HTTP

```console
GET .../api/incidents/{id}
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
---|---|---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK i jednostkę zdarzenia w treści odpowiedzi.
Jeśli nie znaleziono zdarzenia o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```
