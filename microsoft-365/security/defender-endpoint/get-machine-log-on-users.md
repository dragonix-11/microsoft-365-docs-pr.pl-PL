---
title: Interfejs API użytkowników logowania maszynowego
description: Dowiedz się, jak pobrać kolekcję zalogowanych użytkowników na urządzeniu za pomocą interfejsu API Uzyskaj użytkowników logowania maszynowego w programie Microsoft Defender for Endpoint.
keywords: apis, graph api, obsługiwane api, get, device, log on, users
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
ms.openlocfilehash: 1c8635e7037f72830584d09d229891822a2e1f52
ms.sourcegitcommit: 2716cb48cc6127f6b851d177af23f276fb07bfc9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017816"
---
# <a name="get-machine-logon-users-api"></a>Interfejs API użytkowników logowania maszynowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Opis interfejsu API
Pobiera kolekcję zalogowanych użytkowników na określonym urządzeniu.

## <a name="limitations"></a>Ograniczenia
1. Zapytania dotyczące alertów można aktualizować ostatnio zgodnie ze skonfigurowanym okresem przechowywania.
2. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja |User.Read.All |"Czytanie profilów użytkowników"
Delegowane (konto służbowe) | User.Read.All | "Czytanie profilów użytkowników"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych". Aby uzyskać więcej informacji, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).
> - Odpowiedź będzie dotyczyć użytkowników tylko wtedy, gdy urządzenie jest widoczne dla użytkownika w zależności od ustawień grupy urządzeń. Aby uzyskać więcej informacji, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md).

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{id}/logonusers
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i urządzenie istnieje — 200 OK z listą jednostek użytkownika w treści.[](user.md) Jeśli nie znaleziono urządzenia — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/logonusers
```

### <a name="response"></a>Odpowiedź

Oto przykład odpowiedzi.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Users",
    "value": [
        {
            "id": "contoso\\user1",
            "accountName": "user1",
            "accountDomain": "contoso",
            "firstSeen": "2019-12-18T08:02:54Z",
            "lastSeen": "2020-01-06T08:01:48Z",
            "logonTypes": "Interactive",
            "isDomainAdmin": true,
            "isOnlyNetworkUser": false
        },
        ...
    ]
}
```
