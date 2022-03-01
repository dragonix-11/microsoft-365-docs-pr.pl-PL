---
title: Interfejs API alertów dotyczących plików
description: Dowiedz się, jak za pomocą interfejsu API Alerty dotyczące pliku pobrać kolekcję alertów dotyczących danego skrótu pliku w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, file, hash
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
ms.openlocfilehash: b88fc9add77a790c21b3851e3e80f02681308195
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996878"
---
# <a name="get-file-related-alerts-api"></a>Interfejs API alertów dotyczących plików

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Pobiera kolekcję alertów dotyczących danego skrótu pliku.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.
2. Obsługiwana jest tylko funkcja skrótu SHA-1 (nie jest obsługiwana funkcja MD5 ani SHA-256).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Korzystanie [z usługi Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Alert.Read.All|"Czytaj wszystkie alerty"
Aplikacja|Alert.ReadWrite.All|"Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe)|Alert.Odczyt|"Alerty przeczytania"
Delegowane (konto służbowe)|Alert.ReadWrite|"Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienie roli: "Wyświetlanie danych" (zobacz Tworzenie ról i zarządzanie [nimi](user-roles.md) , aby uzyskać więcej informacji)
> - Odpowiedzi będą obejmować tylko alerty, skojarzone z urządzeniami, do których użytkownik ma dostęp, w zależności od ustawień grupy urządzeń ([](machine-groups.md)zobacz Tworzenie grup urządzeń i zarządzanie nimi, aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/files/{id}/alerts
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli wszystko się powiodło i plik istnieje — 200 OK z listą jednostek [alertu](alerts.md) w treści. Jeśli plik nie istnieje — 200 OK z pustym zestawem.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://api.securitycenter.microsoft.com/api/files/6532ec91d513acc05f43ee0aa3002599729fd3e1/alerts
```
