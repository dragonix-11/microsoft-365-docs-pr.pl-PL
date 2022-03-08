---
title: Anuluj interfejs API akcji komputera
description: Dowiedz się, jak anulować już uruchomiono akcję komputera
keywords: apis, graph api,
search.appverid: met150
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
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc4191043e19df7fea4f350d85acd78d2eca1551
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322915"
---
# <a name="cancel-machine-action-api"></a>Anuluj interfejs API akcji komputera

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Anulowanie uruchomionej już akcji komputera, która jeszcze nie znajduje się w końcowym stanie (ukończona, anulowana, nie powiodła się).

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).

|Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień|
|---|---|---|
|Aplikacja|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Zbieranie forensics <br>Wyizoluj komputer<br>Ograniczanie wykonywania kodu<br>  Skanowanie komputera<br>  Urządzenie wye startowe<br> Zatrzymaj i poddaj kwarantannie<br> Uruchamianie odpowiedzi na żywo na określonym komputerze|
|Delegowane (konto służbowe)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Zbieranie forensics<br> Wyizoluj komputer<br>  Ograniczanie wykonywania kodu<br> Skanowanie komputera<br>Urządzenie wye startowe<br> Zatrzymaj i poddaj kwarantannie<br> Uruchamianie odpowiedzi na żywo na określonym komputerze|

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>Żądaj nagłówków

|Name (Nazwa)|Wpisać|Opis|
|---|---|---|
|Autoryzacja|Ciąg|Użytkownik {token}. Wymagane.|
|Typ zawartości|ciąg|application/json. Wymagane.|

## <a name="request-body"></a>Treść wniosku

|Parametr|Wpisać|Opis|
|---|---|---|
|Komentowanie|Ciąg|Komentarz do skojarzenia z akcją anulowania.|

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200, kod odpowiedzi OK z jednostką Akcja komputera. Jeśli nie znaleziono jednostki akcji komputera o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```HTTP
POST
https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/cancel
```

```JSON
{
    "Comment": "Machine action was canceled by automation"
}
```

## <a name="related-topic"></a>Temat pokrewny

- [Uzyskiwanie interfejsu API akcji maszynowych](get-machineaction-object.md)
