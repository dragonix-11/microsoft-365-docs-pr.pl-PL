---
title: Ustawianie interfejsu API wartości urządzenia
description: Dowiedz się, jak określić wartość urządzenia przy użyciu interfejsu API programu Microsoft Defender dla punktu końcowego.
keywords: apis, api Graph, obsługiwane api, tagi, tagi maszynowe
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: b85e7e9fc96b447c6e2528249e516c45ea3e66d1
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996348"
---
# <a name="set-device-value-api"></a>Ustawianie interfejsu API wartości urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Ustaw wartość urządzenia określonego [komputera](machine.md).<br>
Aby [uzyskać więcej informacji, zobacz](tvm-assign-device-value.md) Przypisywanie wartości urządzeń.

## <a name="limitations"></a>Ograniczenia

1. Na urządzeniach możesz publikować ostatnio treści według skonfigurowanego okresu przechowywania.
2. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.ReadWrite.All|"Czytanie i pisanie wszystkich informacji o komputerze"
Delegowane (konto służbowe)|Machine.ReadWrite|"Odczytywanie i pisanie informacji o komputerze"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia roli: "Zarządzanie ustawieniem zabezpieczeń". Aby uzyskać więcej informacji ( [zobacz Tworzenie ról i zarządzanie nimi](user-roles.md) , aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do komputera w zależności od ustawień grupy komputera (zobacz Tworzenie grup [komputerowych](machine-groups.md) i zarządzanie nimi, aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{machineId}/setDeviceValue
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
DeviceValue|Wyli roku|Wartość urządzenia. Dozwolone wartości to: "Normalne", "Niskie" i "Wysokie". **Wymagane**.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 — Ok kod odpowiedzi i zaktualizowany komputer w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład żądania, które dodaje tag maszynowy.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/setDeviceValue
```

```json
{
  "DeviceValue" : "High"
}
```
