---
title: Uruchom interfejs API badania
description: Użyj tego interfejsu API, aby rozpocząć badanie na urządzeniu.
keywords: apis, api Graph, obsługiwane api, badanie
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
ms.openlocfilehash: efffd6bdb0ab6db5b17a8d6beab09a0d84f5ff6c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012500"
---
# <a name="start-investigation-api"></a>Uruchom interfejs API badania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Rozpocznij zautomatyzowane badanie na urządzeniu.

Aby [uzyskać więcej informacji, zobacz Omówienie zautomatyzowanych](automated-investigations.md) badań.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 50 połączeń na godzinę.

## <a name="requirements-for-air"></a>Wymagania dotyczące środowiska AIR

Twoja organizacja musi mieć program Defender for Endpoint (zobacz [Minimalne wymagania programu Microsoft Defender dla punktu końcowego](minimum-requirements.md).

Obecnie program AIR obsługuje tylko następujące wersje systemu operacyjnego:

- Windows Server 2019
- Windows Server 2022
- Windows 10, wersja 1709 (kompilacja systemu operacyjnego 16299.1085 z [kb4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) lub nowsza
- Windows 10, wersja 1803 (kompilacja systemu operacyjnego 17134.704 z [kb4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) lub nowsza
- Windows 10, wersja [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) lub nowsza
- Windows 11

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Alert.ReadWrite.All|"Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe)|Alert.ReadWrite|"Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia roli: "Aktywne akcje naprawcze" [(zobacz Tworzenie](user-roles.md) ról i zarządzanie nimi, aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.security.microsoft.com/api/machines/{id}/startInvestigation
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
Komentowanie|Ciąg|Komentarz do skojarzenia z akcją. **Wymagane**.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 201 — Utworzono kod odpowiedzi i [badanie w treści](investigation.md) odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```https
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/startInvestigation
```

```json
{
  "Comment": "Test investigation"
}
```
