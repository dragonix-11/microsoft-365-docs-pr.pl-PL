---
title: Metody i właściwości wyników
description: Pobiera ocenę ekspozycji w organizacji, bezpieczną ocenę i ocenę ekspozycji w organizacji według grupy urządzeń.
keywords: apis, api Graph, obsługiwane api, wynik, wynik ekspozycji, bezpieczny wynik urządzenia, wynik ekspozycji według grupy urządzeń
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fe69b42c2d8bf80089b749cd41e59664cc2921e3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996287"
---
# <a name="score-resource-type"></a>Typ zasobu wyników

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Metody

Metoda|Zwracany typ|Opis
:---|:---|:---
[Uzyskaj wynik ekspozycji](get-exposure-score.md)|[Wynik](score.md)|Uzyskaj ocenę ekspozycji organizacyjnej.
[Uzyskiwanie wyniku bezpiecznego urządzenia](get-device-secure-score.md)|[Wynik](score.md)|Uzyskaj bezpieczny wynik dla urządzenia organizacyjnego.
[Lista wyników ekspozycji według grupy urządzeń](get-machine-group-exposure-score.md)|[Wynik](score.md)|Lista wyników według grupy urządzeń.

## <a name="properties"></a>Właściwości

Właściwość|Wpisać|Opis
:---|:---|:---
Wynik|Double|Bieżący wynik.
Czas|DateTime|Data i godzina, w której nadano wywołanie dla tego interfejsu API.
RbacGroupName|Ciąg|Nazwa grupy urządzeń.
RbacGroupId|Ciąg|Identyfikator grupy urządzeń.
