---
title: Aktualizowanie interfejsu API jednostki (Machine Entity API)
description: Dowiedz się, jak aktualizować tagi komputera przy użyciu tego interfejsu API. Możesz zaktualizować tagi i właściwości wartości urządzenia.
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
ms.openlocfilehash: 77876024faa7452ff284e30a587e72855068cc98
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996297"
---
# <a name="update-machine"></a>Aktualizuj komputer 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Aktualizuje właściwości istniejącego [komputera](machine.md).

Właściwości, które można ujednolić, to: `machineTags` i `deviceValue`.

## <a name="limitations"></a>Ograniczenia

1. Można aktualizować komputery dostępne w interfejsie API. 
2. Aktualizacja komputera dołącza tagi tylko do kolekcji tagów. Jeśli tagi istnieją, muszą być zawarte w kolekcji tagów w treści.
3. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.ReadWrite.All|"Odczytywanie i pisanie informacji o komputerze dla wszystkich komputerów"
Delegowane (konto służbowe)|Machine.ReadWrite|"Odczytywanie i pisanie informacji o komputerze"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Badanie alertów". Aby uzyskać więcej informacji, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).
> - W zależności od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia skojarzonego z alertem. Aby uzyskać więcej informacji, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md).

## <a name="http-request"></a>Żądanie HTTP

```http
PATCH /api/machines/{machineId}
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|Ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania podać wartości odpowiednich pól, które powinny zostać zaktualizowane.

Istniejące właściwości, które nie są uwzględnione w treści żądania, zachowają poprzednie wartości lub zostaną ponownie przeliczone na podstawie zmian w innych wartościach właściwości.

Aby uzyskać najlepszą wydajność, nie należy uwzględniać istniejących wartości, które nie zmieniły się.

Właściwość|Wpisać|Opis
:---|:---|:---
machineTags|Kolekcja ciągów|Zestaw [tagów maszynowych](machine.md) .
deviceValue|Wyliczność z wartością null|Wartość [urządzenia](tvm-assign-device-value.md). Dopuszczalne wartości: "Normalny", "Niski" i "Wysoki".

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK i jednostkę [komputera](machine.md) w treści odpowiedzi ze zaktualizowanymi właściwościami.

Jeśli kolekcja tagów maszynowych w treści nie zawiera istniejących tagów maszynowych, zastępuje wszystkie tagi tagami zawartymi w treści żądania.

Jeśli nie można odnaleźć komputera o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład prośby.

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10" "Windows11",
                     "Windows Insider - Fast"
    ]
}
```
