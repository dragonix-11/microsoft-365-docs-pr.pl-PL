---
title: Uzyskiwanie alertów dotyczących informacji o użytkownikach
description: Dowiedz się, jak pobrać użytkownika związanego z alertem za pomocą interfejsu API informacji o użytkownikach związanych z alertami w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, alert, information, related, user
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
ms.openlocfilehash: bbf417139a1bfb64f528df97d4d8d0ce9cbb2045
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996234"
---
# <a name="get-alert-related-user-information-api"></a>Interfejs API alertów dotyczących informacji o użytkownikach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera użytkownika powiązanego z określonym alertem.

## <a name="limitations"></a>Ograniczenia

- Zapytania dotyczące alertów można aktualizować ostatnio zgodnie ze skonfigurowanym okresem przechowywania.
- Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|User.Read.All|"Czytanie profilów użytkowników"
Delegowane (konto służbowe)|User.Read.All|"Czytanie profilów użytkowników"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)
> - Zależnie od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia skojarzonego z alertem (aby uzyskać więcej informacji[](machine-groups.md), zobacz Tworzenie grup urządzeń i zarządzanie nimi).

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/alerts/{id}/user
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli to się powiedzie, a istnieje alert i użytkownik — 200 OK z użytkownikiem w treści. Jeśli alert lub nie można odnaleźć użytkownika — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład prośby.

```http
GET https://api.securitycenter.microsoft.com/api/alerts/636688558380765161_2136280442/user
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Users/$entity",
    "id": "contoso\\user1",
    "accountName": "user1",
    "accountDomain": "contoso",
    "accountSid": "S-1-5-21-72051607-1745760036-109187956-93922",
    "firstSeen": "2019-12-08T06:33:39Z",
    "lastSeen": "2020-01-05T06:58:34Z",
    "mostPrevalentMachineId": "0111b647235c26159bec3e5eb6c8c3a0cc3ab766",
    "leastPrevalentMachineId": "0111b647235c26159bec3e5eb6c8c3a0cc3ab766",
    "logonTypes": "Network",
    "logOnMachinesCount": 1,
    "isDomainAdmin": false,
    "isOnlyNetworkUser": false
}
```
