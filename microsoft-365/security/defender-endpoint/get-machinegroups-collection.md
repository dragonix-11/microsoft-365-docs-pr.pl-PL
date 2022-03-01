---
title: Pobieranie interfejsu API kolekcji grup komputerowych RBAC
description: Dowiedz się, jak pobrać kolekcję grup urządzeń RBAC w programie Microsoft Defender for Endpoint za pomocą interfejsu API kolekcji KB.
keywords: apis, api Graph, obsługiwane api, get, RBAC, grupa
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 10/07/2018
ms.custom: api
ms.openlocfilehash: 699a7e2738f1e0c89977bd152832f45935a06387
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997254"
---
# <a name="get-kb-collection-api"></a>Pobierz interfejs API kolekcji KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera kolekcję grup urządzeń RBAC.

## <a name="permissions"></a>Uprawnienia

Użytkownik potrzebuje uprawnień do odczytu.

## <a name="http-request"></a>Żądanie HTTP

```http
GET /testwdatppreview/machinegroups
```

## <a name="request-headers"></a>Żądaj nagłówków

Nagłówek|Value
:---|:---
Autoryzacja | Użytkownik {token}. **Wymagane**.
Typ zawartości | application/json

## <a name="request-body"></a>Treść wniosku

Puste

## <a name="response"></a>Odpowiedź

Jeśli się powiedzie — 200 OK.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.
Identyfikator pola zawiera identyfikator grupy **urządzeń i** jest równy polu **rbacGroupId w** informacjach o urządzeniach.
Pole **rozgrupowane ma** wartość prawda tylko dla jednej grupy dla wszystkich urządzeń, które nie zostały przypisane do żadnej grupy. Ta grupa ma zazwyczaj nazwę "UnassignedGroup".

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineGroups",
    "@odata.count":7,
    "value":[
        {
            "id":86,
            "name":"UnassignedGroup",
            "description":"",
            "ungrouped":true},
        ...
}
```
