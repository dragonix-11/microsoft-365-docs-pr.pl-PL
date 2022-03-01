---
title: Typ zasobu użytkownika
description: Pobieranie ostatnich alertów programu Microsoft Defender dla punktu końcowego dotyczących użytkowników.
keywords: apis, api Graph, obsługiwane api, get, alerts, recent
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
ms.openlocfilehash: 01b7eb32415e431dce37935abb4a1a69776db0f9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996357"
---
# <a name="user-resource-type"></a>Typ zasobu użytkownika

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Metoda|Zwracany typ|Opis
---|---|---
[Lista Alerty dotyczące użytkowników](get-user-related-alerts.md)|[kolekcja alertów](alerts.md)|Lista wszystkich alertów skojarzonych z [użytkownikiem](user.md).
[Lista Urządzeń powiązanych z użytkownikami](get-user-related-machines.md)|[kolekcja maszyn](machine.md)|W tym celu należy wyświetlić listę wszystkich urządzeń zalogowanych przez [użytkownika](user.md).
