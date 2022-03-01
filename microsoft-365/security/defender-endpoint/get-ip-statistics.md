---
title: Interfejs API statystyk ADRESÓW IP
description: Uzyskaj najnowsze statystyki dla adresu IP za pomocą programu Microsoft Defender dla punktu końcowego.
keywords: apis, api Graph, obsługiwane api, get, ip, statistics, cycer
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
ms.openlocfilehash: a98b78e85956d49c3b7d7e389882e017dcede3a4
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996877"
---
# <a name="get-ip-statistics-api"></a>Interfejs API statystyk ADRESÓW IP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API
Pobiera statystykę dla danego adresu IP.

## <a name="limitations"></a>Ograniczenia
1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.
2. Maksymalna wartość dla godzin przedoferowych wynosi 720 godzin(30 dni).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Ip.Read.All|"Odczyt profilów adresów IP"
Delegowane (konto służbowe)|Ip.Read.All|"Odczyt profilów adresów IP"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/ips/{ip}/stats
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-uri-parameters"></a>Żądanie parametrów URI

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
lookBackHours|Int32|Definiuje godziny, które są przeszukiwane w celu uzyskania statystyk. Wartość domyślna to 30 dni. **Opcjonalne**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli adres IP się powiedzie, a istnieje — 200 OK z danymi statystycznymi w treści. Adres IP jest prawidłowy, ale nie istnieje — organizacjaPrevalence 0, adres IP jest nieprawidłowy — HTTP 400.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/stats?lookBackHours=48
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgIPStats",
    "ipAddress": "10.209.67.177",
    "organizationPrevalence": 63515,
    "orgFirstSeen": "2017-07-30T13:36:06Z",
    "orgLastSeen": "2017-08-29T13:32:59Z"
}
```

|Name (Nazwa)|Opis|
|---|---|
|Organizacja w achr.|odrębną liczbę urządzeń, które otworzyły połączenie sieciowe z tym adresem IP.|
|Org first seen|pierwsze połączenie dla tego adresu IP w organizacji.|
|Ostatnio widziane w organizacji|ostatniego połączenia dla tego adresu IP w organizacji.|

> [!NOTE]
> Te informacje statystyczne są oparte na danych z ostatnich 30 dni.
