---
title: Metody i właściwości oprogramowania
description: Pobiera najnowsze alerty na początku.
keywords: apis, api Graph, obsługiwane api, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6b08b7c4ebb0a818dec5bdf799c3114d91764259
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996346"
---
# <a name="software-resource-type"></a>Typ zasobu oprogramowania

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

<br>

****

|Metoda|Zwracany typ|Opis|
|---|---|---|
|[Oprogramowanie listy](get-software.md)|Kolekcja oprogramowania|Lista spisu oprogramowania organizacji|
|[Uzyskiwanie oprogramowania według identyfikatora](get-software-by-id.md)|Oprogramowanie|Uzyskiwanie określonego oprogramowania za pomocą identyfikatora oprogramowania|
|[Rozpowszechnianie wersji oprogramowania na liście](get-software-ver-distribution.md)|Zbiór dystrybucyjny|Rozsyłanie wersji oprogramowania według identyfikatora oprogramowania|
|[Lista komputerów według oprogramowania](get-machines-by-software.md)|Kolekcja MachineRef|Pobieranie listy urządzeń skojarzonych z identyfikatorem oprogramowania|
|[Lista luk w zabezpieczeniach oprogramowania](get-vuln-by-software.md)|[Kolekcja luk](vulnerability.md)|Pobieranie listy luk w zabezpieczeniach związanych z identyfikatorem oprogramowania|
|[Brakujące KB](get-missing-kbs-software.md)|Kolekcja KB|Uzyskiwanie listy brakujących kb/kb skojarzonych z identyfikatorem oprogramowania|
|

## <a name="properties"></a>Właściwości

<br>

****

|Właściwość|Wpisać|Opis|
|---|---|---|
|identyfikator|Ciąg|Identyfikator oprogramowania|
|Name (Nazwa)|Ciąg|Nazwa oprogramowania|
|Dostawca|Ciąg|Nazwa wydawcy oprogramowania|
|Braki|Długa|Liczba wykrytych luk|
|publicExploit|Wartość logiczna|W przypadku niektórych luk istnieje publiczna luka|
|activeAlert|Wartość logiczna|Z tym oprogramowaniem jest skojarzony aktywny alert|
|exposedMachines|Długa|Liczba ujawnionych urządzeń|
|impactScore|Double|Wpływ tego oprogramowania na wyniki ekspozycji|
|
