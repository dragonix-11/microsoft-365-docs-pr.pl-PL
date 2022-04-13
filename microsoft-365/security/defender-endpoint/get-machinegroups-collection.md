---
title: Uzyskiwanie interfejsu API zbierania grup maszyn RBAC
description: Dowiedz się, jak za pomocą interfejsu API pobierania kolekcji KB pobrać kolekcję grup urządzeń RBAC w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: apis, graph api, supported apis, get, RBAC, group
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
ms.openlocfilehash: 528b80b3c40fd7df853190788abb347ed90a82e4
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825173"
---
# <a name="get-kb-collection-api"></a>Uzyskiwanie interfejsu API kolekcji KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Pobiera kolekcję grup urządzeń RBAC.

## <a name="permissions"></a>Uprawnienia

Użytkownik musi mieć uprawnienia do odczytu.

## <a name="http-request"></a>Żądanie HTTP

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
```

## <a name="request-headers"></a>Nagłówki żądań

Nagłówek|Value
:---|:---
Autoryzacji | Element nośny {token}. **Wymagane**.
Typ zawartości | application/json

## <a name="request-body"></a>Treść żądania

Pusty

## <a name="response"></a>Odpowiedzi

Jeśli się powiedzie — 200 OK.

## <a name="example"></a>Przykład

### <a name="request"></a>Żądanie

Oto przykład żądania.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.
Identyfikator pola zawiera **identyfikator** grupy urządzeń i jest równy **identyfikatorowi rbacGroupId** pola w informacjach o urządzeniach.
Pole **niezgrupowane** jest prawdziwe tylko dla jednej grupy dla wszystkich urządzeń, które nie zostały przypisane do żadnej grupy. Ta grupa jak zwykle ma nazwę "UnassignedGroup".

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
