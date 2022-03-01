---
title: Funkcja DeviceFromIP() podczas zaawansowanego wyszukiwania Microsoft 365 Defender
description: Dowiedz się, jak używać funkcji DeviceFromIP() w celu uzyskania urządzeń, do których przypisano określony adres IP
keywords: zaawansowane szukanie, skupowanie na zagrożenia, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, urządzenie, devicefromIP, funkcja, wzbogacenie
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 4a1f1198c247aefbcbb093d1a5f5105704255692
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017929"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


Użyj tej `DeviceFromIP()` funkcji [w zaawansowanych](advanced-hunting-overview.md) zapytaniach myśliwnych, aby szybko uzyskać listę urządzeń przypisanych do określonego adresu IP w określonym momencie. 

Ta funkcja zwraca tabelę z następującymi kolumnami:

| Kolumna | Typ danych | Opis |
|------------|-------------|-------------|
| `IP` | `string` | Adres IP  |
| `DeviceId` | `string` | Unikatowy identyfikator urządzenia w usłudze |


## <a name="syntax"></a>Składnia

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>Argumenty

Ta funkcja jest wywoływana jako część zapytania.

- **x** — pierwszy parametr to zazwyczaj kolumna w zapytaniu. W tym przypadku jest to kolumna `IP`o nazwie , adres IP, dla którego chcesz wyświetlić listę przypisanych do niego urządzeń. Powinien to być lokalny adres IP. Zewnętrzne adresy IP nie są obsługiwane.
- **y** — drugim parametrem opcjonalnym `Timestamp`jest parametr , który nakazuje funkcji uzyskanie najnowszych przypisanych urządzeń z określonego czasu. Jeśli nie zostanie określona, funkcja zwróci najnowsze dostępne rekordy.

## <a name="example"></a>Przykład


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>Uzyskiwanie najnowszych urządzeń, do których przypisano określone adresy IP

```kusto
DeviceNetworkEvents 
| limit 100 
| project IP = LocalIP 
| invoke DeviceFromIP()
```

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
