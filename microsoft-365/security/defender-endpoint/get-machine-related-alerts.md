---
title: Interfejs API alertów związanych z komputerami
description: Dowiedz się, jak używać interfejsu API alertów związanych z komputerami. Ten interfejs API umożliwia pobieranie wszystkich alertów, które są powiązane z określonym urządzeniem w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, devices, related, alerts
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
ms.openlocfilehash: 49cc0fca3ae7617b86ab079daace92eb3790db94
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996885"
---
# <a name="get-machine-related-alerts--api"></a>Interfejs API alertów związanych z komputerami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera wszystkie [alerty](alerts.md) związane z określonym urządzeniem.

## <a name="limitations"></a>Ograniczenia

1. Zapytania na urządzeniach można aktualizować po raz ostatni zgodnie ze skonfigurowanym okresem przechowywania.
2. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Alert.Read.All|"Czytaj wszystkie alerty"
Aplikacja|Alert.ReadWrite.All|"Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe) | Alert.Odczyt | "Alerty przeczytania"
Delegowane (konto służbowe) | Alert.ReadWrite | "Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych". Aby uzyskać więcej informacji o uprawnieniach, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).
> - W zależności od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia. Aby uzyskać więcej informacji o ustawieniach grupy urządzeń, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md).

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{id}/alerts
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i istnieje urządzenie: 200 OK z listą jednostek [alertu](alerts.md) w treści. Jeśli nie znaleziono urządzenia: 404 Nie znaleziono.
