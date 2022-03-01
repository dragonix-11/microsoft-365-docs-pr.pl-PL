---
title: Interfejs API alertów związanych z użytkownikami
description: Pobieranie kolekcji alertów dotyczących danego identyfikatora użytkownika za pomocą programu Microsoft Defender dla punktu końcowego.
keywords: apis, api Graph, obsługiwane api, get, user, related, alerts
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
ms.openlocfilehash: 11811996ef369c7850030871abdb6a5082546de8
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996350"
---
# <a name="get-user-related-alerts-api"></a>Interfejs API alertów związanych z użytkownikami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera kolekcję alertów związanych z danym identyfikatorem użytkownika.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Alert.Read.All|"Czytaj wszystkie alerty"
Aplikacja|Alert.ReadWrite.All|"Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe) | Alert.Odczyt | "Alerty przeczytania"
Delegowane (konto służbowe) | Alert.ReadWrite | "Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych". Aby uzyskać więcej informacji, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).
> - Odpowiedzi będą obejmować tylko alerty, skojarzone z urządzeniami, do których użytkownik ma dostęp, w zależności od ustawień grupy urządzeń ([](machine-groups.md)zobacz Tworzenie grup urządzeń i zarządzanie nimi, aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/users/{id}/alerts
```

**Identyfikator nie jest pełną nazwą upn, ale tylko nazwą użytkownika. (Na przykład w celu pobrania alertów dla user1@contoso.com użyj instrukcji /api/users/user1/alerts)**

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i użytkownik istnieje — 200 OK. Jeśli użytkownik nie istnieje — 200 OK z pustym zestawem.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/alerts
```
