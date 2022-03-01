---
title: Uzyskiwanie interfejsu API komputerów powiązanych z użytkownikami
description: Dowiedz się, jak używać interfejsu API Get user-related machines w celu pobrania kolekcji urządzeń związanych z identyfikatorem użytkownika w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, user, user related alerts
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
ms.openlocfilehash: 5dd8cbd36fdac4aa3d0661a9b418a30ec2bae44f
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995819"
---
# <a name="get-user-related-machines-api"></a>Uzyskiwanie interfejsu API komputerów powiązanych z użytkownikami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API
Pobiera kolekcję urządzeń powiązanych z danym identyfikatorem użytkownika.

## <a name="limitations"></a>Ograniczenia

Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja |Machine.Read.All|"Czytaj wszystkie profile maszyn"
Aplikacja |Machine.ReadWrite.All |"Czytanie i pisanie wszystkich informacji o komputerze"
Delegowane (konto służbowe) | Machine.Read | "Odczytywanie informacji o komputerze"
Delegowane (konto służbowe) | Machine.ReadWrite | "Odczytywanie i pisanie informacji o komputerze"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych". Aby uzyskać więcej informacji, zobacz [Tworzenie ról i zarządzanie nimi.](user-roles.md)
> - Odpowiedź będzie obejmować tylko urządzenia, do których użytkownik może uzyskać dostęp, w zależności od ustawień grupy urządzeń. Aby uzyskać więcej informacji, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md).

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/users/{id}/machines
```

**Identyfikator nie jest pełną nazwą upn, ale tylko nazwą użytkownika. (Na przykład do pobierania komputerów do user1@contoso.com use /api/users/user1/machines)**

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i użytkownik istnieje — 200 OK z listą obiektów [maszynowych](machine.md) w treści. Jeśli użytkownik nie istnieje — 200 OK z pustym zestawem.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/machines
```
