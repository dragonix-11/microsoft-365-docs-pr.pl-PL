---
title: Uzyskiwanie komputera za pomocą interfejsu API identyfikatorów
description: Dowiedz się, jak pobrać komputer za pomocą interfejsu API Get machine by ID, aby pobrać komputer na przykład za pomocą identyfikatora urządzenia lub nazwy komputera w programie Microsoft Defender for Endpoint.
keywords: api, api Graph, obsługiwane api, get, devices, entity, id
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
ms.openlocfilehash: 14b00e936111c54cd100e847a9ec18f921e34880
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996876"
---
# <a name="get-machine-by-id-api"></a>Uzyskiwanie komputera za pomocą interfejsu API identyfikatorów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API
Pobiera określony [komputer](machine.md) według jego identyfikatora urządzenia lub nazwy komputera.

## <a name="limitations"></a>Ograniczenia

1. Urządzenia możesz ostatnio zobaczyć zgodnie ze skonfigurowanymi zasadami przechowywania.
2. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.Read.All|"Czytaj wszystkie profile maszyn"
Aplikacja|Machine.ReadWrite.All|"Czytanie i pisanie wszystkich informacji o komputerze"
Delegowane (konto służbowe) | Machine.Read | "Odczytywanie informacji o komputerze"
Delegowane (konto służbowe) | Machine.ReadWrite | "Odczytywanie i pisanie informacji o komputerze"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{id}
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i urządzenie istnieje — 200 OK z jednostką [komputera](machine.md) w treści.
Jeśli nie można odnaleźć komputera o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Machine",
    "id": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "computerDnsName": "mymachine1.contoso.com",
    "firstSeen": "2018-08-02T14:55:03.7791856Z",
    "lastSeen": "2018-08-02T14:55:03.7791856Z",
    "osPlatform": "Windows10" "Windows11",
    "version": "1709",
    "osProcessor": "x64",
    "lastIpAddress": "172.17.230.209",
    "lastExternalIpAddress": "167.220.196.71",
    "osBuild": 18209,
    "healthStatus": "Active",
    "rbacGroupId": 140,
    "rbacGroupName": "The-A-Team",
    "riskScore": "Low",
    "exposureLevel": "Medium",
    "isAadJoined": true,
    "aadDeviceId": "80fe8ff8-2624-418e-9591-41f0491218f9",
    "machineTags": [ "test tag 1", "test tag 2" ]
}
```
