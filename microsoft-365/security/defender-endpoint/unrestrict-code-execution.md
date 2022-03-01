---
title: Usuwanie interfejsu API ograniczeń aplikacji
description: Za pomocą tego interfejsu API możesz tworzyć wywołania związane z usuwaniem ograniczeń związanych z wykonywaniem przez aplikacje.
keywords: apis, api Graph, obsługiwane api, usuń urządzenie z izolacji
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: c2fe35d73cd9abf3483c32067bf59334c6ad016b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997291"
---
# <a name="remove-app-restriction-api"></a>Usuwanie interfejsu API ograniczeń aplikacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Włącz wykonywanie dowolnej aplikacji na urządzeniu.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Pełna izolacji jest dostępna dla urządzeń Windows 10 wersji 1703.
> - Izolacji selektywne jest dostępne dla urządzeń Windows 10 wersji 1709 lub nowszej.
> - W przypadku odizolowania urządzenia dozwolone są tylko niektóre procesy i miejsca docelowe. Dlatego urządzenia, które znajdują się za pełnym szyfrowaniem VPN, nie będą mogły uzyskać dostępu do usługi Microsoft Defender for Endpoint w chmurze, gdy urządzenie jest odizolowane. Zalecamy korzystanie z sieci VPN rozdzielaowej dla programu Microsoft Defender dla punktu końcowego i Program antywirusowy Microsoft Defender opartego na chmurze ruchu związanego z ochroną.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.RestrictExecution|"Ogranicz wykonywanie kodu"
Delegowane (konto służbowe)|Machine.RestrictExecution|"Ogranicz wykonywanie kodu"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia roli: "Aktywne akcje naprawcze" [(zobacz Tworzenie](user-roles.md) ról i zarządzanie nimi, aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/unrestrictCodeExecution
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

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 201 — utworzono kod odpowiedzi i [akcję maszynową](machineaction.md) w treści odpowiedzi.

W przypadku wysłania wielu wywołań interfejsu API w celu usunięcia ograniczeń aplikacji dla tego samego urządzenia zwracana jest "oczekująca akcja maszynowa" lub HTTP 400 z komunikatem "Akcja jest już w toku".

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```

Aby ograniczyć wykonywanie kodu na urządzeniu, zobacz [Ograniczanie wykonywania aplikacji](restrict-code-execution.md).
