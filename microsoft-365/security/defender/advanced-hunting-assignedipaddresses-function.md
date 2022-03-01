---
title: Przypisano funkcjęIPAddresses() w zaawansowanym szukaniu Microsoft 365 Defender
description: Dowiedz się, jak używać funkcji AssignedIPAddresses() w celu uzyskania najnowszych adresów IP przypisanych do urządzenia
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, FileProfile, profil pliku, funkcja, wzbogacenie
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
ms.openlocfilehash: b82a079a476ee6ed3d5465b52bca381cd49746b5
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017891"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Użyj tej `AssignedIPAddresses()` funkcji w zaawansowanych zapytaniach [myśliwnych](advanced-hunting-overview.md) , aby szybko uzyskać najnowsze adresy IP, które zostały przypisane do urządzenia. Jeśli określisz argument sygnatury czasowej, ta funkcja uzyska najnowsze adresy IP w określonym czasie. 

Ta funkcja zwraca tabelę z następującymi kolumnami:

| Kolumna | Typ danych | Opis |
|------------|-------------|-------------|
| `Timestamp` | `datetime` | Godzina ostatniego obserwowania urządzenia przy użyciu adresu IP |
| `IPAddress` | `string` | Adres IP używany przez urządzenie |
| `IPType` | `string` | Wskazuje, czy adres IP jest adresem publicznym, czy prywatnym. |
| `NetworkAdapterType` | `int` | Typ karty sieciowej używany przez urządzenie, do których przypisano adres IP. Aby uzyskać możliwe wartości, zapoznaj się z [tym wyliczeniem.](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | `int` | Sieci, do których jest podłączona karta z przypisanym adresem IP. Każda tablica JSON zawiera nazwę sieciową, kategorię (publiczną, prywatną lub domenę), opis i flagę wskazującą, czy jest publicznie połączona z Internetem |

## <a name="syntax"></a>Składnia

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>Argumenty

- **x** —`DeviceId` lub `DeviceName` wartość identyfikująca urządzenie
- **y** —`Timestamp` (data/godzina) instruowanie funkcji, aby uzyskać najnowsze przypisane adresy IP z określonego czasu. Jeśli nie zostanie określona, funkcja zwróci najnowsze adresy IP.

## <a name="examples"></a>Przykłady

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>Uzyskiwanie listy adresów IP używanych przez urządzenie 24 godziny temu

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>Uzyskiwanie adresów IP używanych przez urządzenie i znajdowanie urządzeń do komunikowania się z nim
To zapytanie używa tej funkcji `AssignedIPAddresses()` do uzyskania przypisanych adresów IP urządzenia () w określonym dniu lub`example-device-name` wcześniej (`example-date`). Następnie używa adresów IP w celu znalezienia połączeń z urządzeniem inicjowanych przez inne urządzenia. 

```kusto
let Date = datetime(example-date);
let DeviceName = "example-device-name";
// List IP addresses used on or before the specified date
AssignedIPAddresses(DeviceName, Date)
| project DeviceName, IPAddress, AssignedTime = Timestamp 
// Get all network events on devices with the assigned IP addresses as the destination addresses
| join kind=inner DeviceNetworkEvents on $left.IPAddress == $right.RemoteIP
// Get only network events around the time the IP address was assigned
| where Timestamp between ((AssignedTime - 1h) .. (AssignedTime + 1h))
```

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Opis schematu](advanced-hunting-schema-tables.md)