---
title: Aktualizowanie interfejsu API encji alertu
description: Dowiedz się, jak zaktualizować alert programu Microsoft Defender for Endpoint przy użyciu tego interfejsu API. Można aktualizować stan, wyznaczanie, klasyfikację i właściwości przypisane do.
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
ms.openlocfilehash: 4efe1460374350d054bbe6d19543c75454d7b5ce
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995859"
---
# <a name="update-alert"></a>Aktualizowanie alertu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API
Aktualizuje właściwości istniejącego [alertu](alerts.md).

Przesyłanie **komentarza** jest dostępne z aktualizacją właściwości lub bez niego.

Właściwości, które można ujednolić, to: `status`, `determination``classification`, i `assignedTo`.

## <a name="limitations"></a>Ograniczenia

1. Możesz aktualizować alerty dostępne w interfejsie API. Aby uzyskać więcej informacji, zobacz [Alerty listy](get-alerts.md).
2. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Alerts.ReadWrite.All|"Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe)|Alert.ReadWrite|"Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Badanie alertów" (Aby uzyskać więcej informacji, zobacz Tworzenie ról [i zarządzanie nimi](user-roles.md) )
> - Zależnie od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia skojarzonego z alertem (aby uzyskać więcej informacji, zobacz Tworzenie [grup urządzeń i zarządzanie nimi).](machine-groups.md)

## <a name="http-request"></a>Żądanie HTTP

```http
PATCH /api/alerts/{id}
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|Ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania podać wartości odpowiednich pól, które powinny zostać zaktualizowane.

Istniejące właściwości, które nie są uwzględnione w treści żądania, zachowają poprzednie wartości lub zostaną ponownie przeliczone na podstawie zmian innych wartości właściwości.

Aby uzyskać najlepszą wydajność, nie należy uwzględniać istniejących wartości, które nie zmieniły się.

Właściwość|Wpisać|Opis
:---|:---|:---
Stan|Ciąg|Określa bieżący stan alertu. Wartości właściwości to: "Nowy", "Ruch wychodzący" i "Rozpoznane".
assignedTo|Ciąg|Właściciel alertu
Klasyfikacja|Ciąg|Określa specyfikację alertu. Wartości właściwości to: "Nieznany", "FałszPozyty", "TruePositive".
Wyznaczanie|Ciąg|Określa określenie alertu. Wartości właściwości to: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
Komentowanie|Ciąg|Komentarz do dodania do alertu.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK i jednostkę [alertu](alerts.md) w treści odpowiedzi ze zaktualizowanymi właściwościami. Jeśli nie można odnaleźć alertu z określonym identyfikatorem — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład prośby.

```http
PATCH https://api.securitycenter.microsoft.com/api/alerts/121688558380765161_2136280442
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
