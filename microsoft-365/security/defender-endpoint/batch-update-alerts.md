---
title: Interfejs API jednostek alertu aktualizacji partii
description: Dowiedz się, jak zaktualizować alerty programu Microsoft Defender dla punktu końcowego w partii przy użyciu tego interfejsu API. Można aktualizować stan, wyznaczanie, klasyfikację i właściwości przypisane do.
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: a2d695a2b406d4850f0e9896af3ec3b2aede8870
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996891"
---
# <a name="batch-update-alerts"></a>Alerty aktualizacji wsadowej

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Opis interfejsu API

Aktualizuje właściwości partii istniejących [alertów](alerts.md).

Przesyłanie **komentarza** jest dostępne z aktualizacją właściwości lub bez niego.

Właściwości, które można ujednolić, to: `status`, `determination`i `classification` `assignedTo`.

## <a name="limitations"></a>Ograniczenia

1. Możesz aktualizować alerty, które są dostępne w interfejsie API. Aby [uzyskać więcej informacji,](get-alerts.md) zobacz Alerty listy.
2. Ograniczenia stawek dla tego interfejsu API to 10 połączeń na minutę i 500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja | Alert.ReadWrite.All | "Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe) | Alert.ReadWrite | "Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Badanie alertów" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)
> - Zależnie od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia skojarzonego z alertem (aby uzyskać więcej informacji[](machine-groups.md), zobacz Tworzenie grup urządzeń i zarządzanie nimi).

## <a name="http-request"></a>Żądanie HTTP

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.
Typ zawartości | Ciąg | application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania podać identyfikatory alertów, które mają zostać zaktualizowane, oraz wartości odpowiednich pól, które mają zostać zaktualizowane dla tych alertów.

Istniejące właściwości, które nie są uwzględnione w treści żądania, zachowają poprzednie wartości lub zostaną ponownie przeliczone na podstawie zmian w innych wartościach właściwości.

Aby uzyskać najlepszą wydajność, nie należy uwzględniać istniejących wartości, które nie zostały zmienione.

Właściwość | Wpisać | Opis
:---|:---|:---
alertIds | ListString&lt;&gt;| Lista identyfikatorów alertów, które mają zostać zaktualizowane. **Wymagane**
stan | Ciąg | Określa stan aktualizacji określonych alertów. Wartości właściwości to: "Nowy", "Ruch wychodzący" i "Rozpoznane".
assignedTo | Ciąg | Właściciel określonych alertów
klasyfikacja | Ciąg | Określa specyfikację określonych alertów. Wartości właściwości to: "Nieznany", "FałszPozyty", "TruePositive". 
wyznaczanie | Ciąg | Określa określenie określonych alertów. Wartości właściwości to: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
komentarz | Ciąg | Komentarz do dodania do określonych alertów.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda przebiegnie pomyślnie, funkcja zwróci wartość 200 OK z pustą treścią odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
