---
title: Interfejs API statystyk dotyczących domeny
description: Dowiedz się, jak używać interfejsu API statystyk dotyczących domeny w celu pobrania statystyk dotyczących danej domeny w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, domena, urządzenia powiązane z domenami
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
ms.openlocfilehash: 2e07b9545ef6bab0c7b93188edf65d43ae0378b2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996861"
---
# <a name="get-domain-statistics-api"></a>Interfejs API statystyk dotyczących domeny

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera statystykę dla danej domeny.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.
2. Maksymalna wartość to `lookbackhours` 720 godzin (30 dni).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|ADRES URL. Read.All|Przeczytane adresy URL
Delegowane (konto służbowe)|ADRES URL. Read.All|Przeczytane adresy URL

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/domains/{domain}/stats
```

## <a name="request-headers"></a>Żądaj nagłówków

Nagłówek|Value
:---|:---
Autoryzacja|Użytkownik {token}. **Wymagane**.

## <a name="request-uri-parameters"></a>Żądanie parametrów URI

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
lookBackHours|Int32|Definiuje godziny, które są przeszukiwane w celu uzyskania statystyk. Wartość domyślna to 30 dni. **Opcjonalne**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i domena istnieje — 200 OK, z obiektem statistics w treści odpowiedzi. Jeśli domena nie istnieje — 200 OK ze sednem ustawionym na 0.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/domains/example.com/stats?lookBackHours=48
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgDomainStats",
    "host": "example.com",
    "organizationPrevalence": 4070,
    "orgFirstSeen": "2017-07-30T13:23:48Z",
    "orgLastSeen": "2017-08-29T13:09:05Z"
}
```
