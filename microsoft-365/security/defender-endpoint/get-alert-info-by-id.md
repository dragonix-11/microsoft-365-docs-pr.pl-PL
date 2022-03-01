---
title: Uzyskiwanie informacji alertów za pomocą interfejsu API identyfikatorów
description: Dowiedz się, jak pobrać określony alert za pomocą identyfikatora API alertu za pomocą identyfikatora w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, alert, information, id
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
ms.openlocfilehash: 09866afa2b965f8587114d49f92d8068c535a0c7
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997140"
---
# <a name="get-alert-information-by-id-api"></a>Uzyskiwanie informacji alertów za pomocą interfejsu API identyfikatorów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera określony [alert](alerts.md) na pomocą jego identyfikatora.

## <a name="limitations"></a>Ograniczenia

- Alerty można aktualizować po raz ostatni zgodnie ze skonfigurowanym okresem przechowywania.
- Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie programu [Microsoft Defender dla interfejsów API punktów końcowych](apis-intro.md).

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Alert.Read.All|"Czytaj wszystkie alerty"
Aplikacja|Alert.ReadWrite.All|"Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe)|Alert.Odczyt|"Alerty przeczytania"
Delegowane (konto służbowe)|Alert.ReadWrite|"Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)
> - Zależnie od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia skojarzonego z alertem (aby uzyskać więcej informacji[](machine-groups.md), zobacz Tworzenie grup urządzeń i zarządzanie nimi).

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/alerts/{id}
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK i [jednostkę alertu](alerts.md) w treści odpowiedzi. Jeśli alert o określonym identyfikatorze nie został znaleziony — 404 Nie znaleziono.
