---
title: Tabela DeviceNetworkInfo w zaawansowanym schemacie chłoniania
description: Informacje o konfiguracji sieci można znaleźć w tabeli DeviceNetworkInfo zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, schłonienie pod niebędący zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, machinenetworkinfo, DeviceNetworkInfo, urządzenie, komputer, mac, ip, adapter, dns, dns, brama, klienta
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
ms.openlocfilehash: 86c087c8a8cdfa80904612625c08ec37ca6813ca
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017893"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



Tabela `DeviceNetworkInfo` w zaawansowanym schemacie [chwyć](advanced-hunting-overview.md) zawiera informacje o konfiguracji sieciowej komputerów, w tym o kartach sieciowych, adresach IP i MAC oraz połączonych sieciach i domenach. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `NetworkAdapterName` | `string` | Nazwa karty sieciowej |
| `MacAddress` | `string` | Adres MAC karty sieciowej |
| `NetworkAdapterType` | `string` | Typ karty sieciowej. Aby uzyskać możliwe wartości, zapoznaj się z [tym wyliczeniem.](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | `string` | Stan operacyjny karty sieciowej. Aby uzyskać możliwe wartości, zapoznaj się z [tym wyliczeniem.](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | `string` | Protokół sieciowego, jeśli do tego celu jest używany interfejs, na przykład 6to4, Teredo, ISATAP, PPTP, SSTP i SSH |
| `ConnectedNetworks` | `string` | Sieci, do których jest podłączona karta. Każda tablica JSON zawiera nazwę sieciową, kategorię (publiczną, prywatną lub domenę), opis i flagę wskazującą, czy jest publicznie połączona z Internetem |
| `DnsAddresses` | `string` | Adresy serwerów DNS w formacie tablicy JSON |
| `IPv4Dhcp` | `string` | Adres IPv4 serwera FTP |
| `IPv6Dhcp` | `string` | Adres IPv6 serwera FTP |
| `DefaultGateways` | `string` | Domyślne adresy bram w formacie tablicowym JSON |
| `IPAddresses` | `string` | Tablica JSON zawierająca wszystkie adresy IP przypisane do karty wraz z odpowiednim prefiksem podsieci i przestrzenią adresów IP, taką jak publiczny, prywatny lub link-local |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)