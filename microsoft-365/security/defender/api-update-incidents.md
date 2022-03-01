---
title: Aktualizowanie interfejsu API zdarzenia
description: Dowiedz się, jak aktualizować zdarzenia przy Microsoft 365 Defender API
keywords: aktualizacja, interfejs API, zdarzenie
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 447a4b5eb3f4eb521e7cc3bd2df23a42f16d2ef1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013389"
---
# <a name="update-incidents-api"></a>Interfejs API aktualizacji zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

## <a name="api-description"></a>Opis interfejsu API

Aktualizuje właściwości istniejącego zdarzenia. Właściwości, które można ujednolić, to: `status`, `determination``classification`, `assignedTo`, `tags`i `comments`.

### <a name="quotas-resource-allocation-and-other-constraints"></a>Przydziały, alokacja zasobów i inne ograniczenia

1. Zanim przekroczysz próg ograniczania, możesz wykonać do 50 połączeń na minutę lub 1500 połączeń na godzinę.
2. Właściwość można ustawić tylko `determination` wtedy, gdy jest `classification` ustawiona wartość TruePositive (Prawda).

Jeśli Twoje żądanie jest ograniczone, zwraca ono kod `429` odpowiedzi. Treść odpowiedzi będzie wskazywać, kiedy możesz zacząć dzwonić.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Uzyskiwanie dostępu do Microsoft 365 Defender [API](api-access.md).

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Incident.ReadWrite.All|Czytanie i pisanie wszystkich zdarzeń
Delegowane (konto służbowe)|Incident.ReadWrite|Zdarzenia przeczytania i pisania

> [!NOTE]
> Podczas uzyskiwania tokenu przy użyciu poświadczeń użytkownika użytkownik musi mieć uprawnienia do aktualizowania zdarzenia w portalu.

## <a name="http-request"></a>Żądanie HTTP

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
---|---|---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|Ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania podać wartości pól, które mają zostać zaktualizowane. Istniejące właściwości, które nie są uwzględnione w treści żądania, zachowają swoje wartości, chyba że muszą zostać ponownie obliczone ze względu na zmiany wartości pokrewnych. Aby uzyskać najlepszą wydajność, należy pominąć istniejące wartości, które nie zostały zmienione.

Właściwość|Wpisać|Opis
---|---|---
stan|Wyli roku|Określa bieżący stan zdarzenia. Dopuszczalne wartości to: `Active`, `Resolved`i `Redirected`.
assignedTo|ciąg|Właściciel zdarzenia.
klasyfikacja|Wyli roku|Specyfikacja zdarzenia. Dopuszczalne wartości: `Unknown`, `FalsePositive`, `TruePositive`.
wyznaczanie|Wyli roku|Określa określenie zdarzenia. Dopuszczalne wartości to: `NotAvailable`, `Apt`, `Malware`, `SecurityPersonnel``SecurityTesting`, `UnwantedSoftware`, . `Other`
tagi|ciąg Lista|Lista tagów zdarzeń.
komentarz|ciąg|Komentarz do dodania do zdarzenia.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość `200 OK`. Treść odpowiedzi będzie zawierać jednostkę zdarzenia ze zaktualizowanymi właściwościami. Jeśli nie zostanie znalezione zdarzenie o określonym identyfikatorze, metoda zwróci wartość `404 Not Found`.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład prośby.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

### <a name="response-example"></a>Przykład odpowiedzi

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"],
    "comments": [
          {
              "comment": "pen testing",
              "createdBy": "secop2@contoso.com",
              "createdTime": "2021-05-02T09:34:21.5519738Z"
          },
          {
              "comment": "valid incident",
              "createdBy": "secop2@contoso.comt",
              "createdTime": "2021-05-02T09:36:27.6652581Z"
          }
      ]
}
```

## <a name="related-articles"></a>Artykuły pokrewne

- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
- [Opis kodów błędów](api-error-codes.md)
- [Interfejsy API zdarzenia](api-incident.md)
- [Lista zdarzeń](api-list-incidents.md)
- [Omówienie zdarzeń](incidents-overview.md)
