---
title: Interfejs API komputera od tablicy
description: Dowiedz się, jak za pomocą interfejsu API wyłączyć urządzenie z usługi Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, zbieranie pakietu badania
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
ms.openlocfilehash: 1279f7271abbd4086c946492e95daa52962dbae5
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013814"
---
# <a name="offboard-machine-api"></a>Interfejs API komputera od tablicy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Urządzenie odsuń od usługi Defender for Endpoint.

## <a name="limitations"></a>Ograniczenia

- Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Ten interfejs API jest obsługiwany na Windows 11, Windows 10, w wersji 1703 lub nowszej albo w Windows Server 2019 i nowszych wersjach.
>
> Ten interfejs API nie jest obsługiwany na urządzeniach z systemem MacOS ani Linux.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Korzystanie [z usługi Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Machine.Offboard|"Urządzenie do odsuń"
Delegowane (konto służbowe)|Machine.Offboard|"Urządzenie do odsuń"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć rolę AD "Administrator globalny"
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

Identyfikator komputera można znaleźć w adresie URL po wybraniu urządzenia. Ogólnie rzecz biorąc, jest to 40-cyfrowy numer alfanumeryczny, który można znaleźć w adresie URL.

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
---|---|---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt JSON o następujących parametrach:

Parametr|Wpisać|Opis
---|---|---
Komentowanie|Ciąg|Komentarz do skojarzenia z akcją. **Wymagane**.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 201 — utworzono kod odpowiedzi i [akcję maszynową](machineaction.md) w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
