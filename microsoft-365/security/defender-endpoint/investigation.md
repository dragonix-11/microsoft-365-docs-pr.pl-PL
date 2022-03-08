---
title: Typ zasobu badania
description: Microsoft Defender for Endpoint Investigation entity.
keywords: apis, api Graph, obsługiwane api, get, alerts, investigations
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1749404942b42778ecde99417a8e3501c7c4f4cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327227"
---
# <a name="investigation-resource-type"></a>Typ zasobu badania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Reprezentowanie jednostki automatycznego badania w programie Defender dla punktu końcowego.

Aby uzyskać więcej informacji, zobacz [Omówienie zautomatyzowanych badań](automated-investigations.md).

## <a name="methods"></a>Metody

Metoda|Zwracany typ|Opis
:---|:---|:---
[Badania listy](get-investigation-collection.md)|Kolekcja badania|Pobierz kolekcję badania
[Pobierz jedno badanie](get-investigation-object.md)|Jednostka badania|Pobiera pojedynczą jednostkę badania.
[Rozpocznij badanie](initiate-autoir-investigation.md)|Jednostka badania|Uruchamia badanie na urządzeniu.

## <a name="properties"></a>Właściwości

Właściwość|Wpisać|Opis
:---|:---|:---
Identyfikator|Ciąg|Tożsamość jednostki badania. 
startTime|DateTime Nullable|Data i godzina utworzenia badania.
endTime (czas zakończenia)|DateTime Nullable|Data i godzina zakończenia badania.
cancelledBy|Ciąg|Identyfikator użytkownika/aplikacji, który anulował to badanie.
Stan|Wyli roku|Bieżący stan badania. Dopuszczalne wartości: "Nieznane", "Zakończone", "PomyślnieRemediated", "Szybki", "Zakończony niepowodzenie", "CzęściowoRemediated", "Uruchomiony", "OczekującyApproval", "OczekiwanieResource", "Częściowo Reinwestowane", "ZakończoneByUser", "TerminatedBySystem", "Queued", 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.
stanDetails|Ciąg|Dodatkowe informacje o stanie badania.
machineId|Ciąg|Identyfikator urządzenia, na którym wykonano badanie.
computerDnsName|Ciąg|Nazwa urządzenia, na którym wykonano badanie.
triggeringAlertId|Ciąg|Identyfikator alertu, który wyzwolił badanie.

## <a name="json-representation"></a>Reprezentacja Jsona

```json
{
    "id": "63004",
    "startTime": "2020-01-06T13:05:15Z",
    "endTime": null,
    "state": "Running",
    "cancelledBy": null,
    "statusDetails": null,
    "machineId": "e828a0624ed33f919db541065190d2f75e50a071",
    "computerDnsName": "desktop-test123",
    "triggeringAlertId": "da637139127150012465_1011995739"
}
```
