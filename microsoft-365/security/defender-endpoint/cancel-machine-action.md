---
title: Anuluj interfejs API akcji maszyny
description: Dowiedz się, jak anulować już uruchomioną akcję maszyny
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
ms.openlocfilehash: 08f302a541e60cb2844dc6ef2b91509556f03330
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873759"
---
# <a name="cancel-machine-action-api"></a>Anuluj interfejs API akcji maszyny

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/defender-endpoint)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Anuluj już uruchomioną akcję maszyny, która nie jest jeszcze w stanie końcowym (ukończona, anulowana, nieudana).

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia szybkości dla tego interfejsu API to 100 wywołań na minutę i 1500 wywołań na godzinę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Wprowadzenie](apis-intro.md).

|Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień|
|---|---|---|
|Aplikacja|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Zbieranie kryminalistyki <br>Izoluj komputer<br>Ograniczanie wykonywania kodu<br>  Skanuj maszynę<br>  Odłącz komputer<br> Zatrzymywanie i kwarantanna<br> Uruchamianie odpowiedzi na żywo na określonej maszynie|
|Delegowane (konto służbowe)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Zbieranie kryminalistyki<br> Izoluj komputer<br>  Ograniczanie wykonywania kodu<br> Skanuj maszynę<br>Odłącz komputer<br> Zatrzymywanie i kwarantanna<br> Uruchamianie odpowiedzi na żywo na określonej maszynie|

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>Nagłówki żądań

|Name (Nazwa)|Wpisać|Opis|
|---|---|---|
|Autoryzacji|Ciąg|Element nośny {token}. Wymagane.|
|Typ zawartości|Ciąg|application/json. Wymagane.|

## <a name="request-body"></a>Treść żądania

|Parametr|Wpisać|Opis|
|---|---|---|
|Komentowanie|Ciąg|Komentarz do skojarzenia z akcją anulowania.|

## <a name="response"></a>Odpowiedzi

Jeśli to się powiedzie, ta metoda zwraca kod odpowiedzi 200, OK z jednostką Machine Action. Jeśli nie odnaleziono jednostki akcji komputera o określonym identyfikatorze — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Żądanie

Oto przykład żądania.

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

- [Uzyskiwanie interfejsu API akcji maszyny](get-machineaction-object.md)
