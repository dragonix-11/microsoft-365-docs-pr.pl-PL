---
title: Tabela AlertInfo w zaawansowanym schemacie wyszukiwania
description: Informacje o zdarzeniach związanych z generowanie alertów w tabeli AlertInfo zaawansowanego schematu wyszukiwania
keywords: zaawansowane wyszukiwania, chłonianie pod zagrożeniami, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, AlertInfo, alert, ważność, kategoria, MITRE, ATT&CK, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Cloud App Security, MCAS i Microsoft Defender for Identity
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
ms.openlocfilehash: 0298b4f83ac748048215af4f5b1f8261a2a8c67c
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017885"
---
# <a name="alertinfo"></a>AlertInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender



Tabela `AlertInfo` w zaawansowanym schemacie chłoń zawiera informacje o alertach z programu Microsoft Defender for Endpoint, programu Microsoft Defender for Office 365, programu Microsoft Defender dla aplikacji w chmurze i programu Microsoft Defender dla tożsamości.[](advanced-hunting-overview.md) To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `AlertId` | `string` | Unikatowy identyfikator alertu |
| `Title` | `string` | Tytuł alertu |
| `Category` | `string` | Typ wskaźnika zagrożenia lub działania w przypadku naruszenia zabezpieczeń wskazanego przez alert |
| `Severity` | `string` | Wskazuje potencjalny wpływ (wysoki, średni lub niski) wskaźnika zagrożenia lub działania na naruszenie określone przez alert |
| `ServiceSource` | `string` | Produkt lub usługa, która podała informacje o alertach |
| `DetectionSource` | `string` | Technologia wykrywania lub czujnik, który zidentyfikował notowalny składnik lub działanie |
| `AttackTechniques` | `string` | MiTRE ATT&technik CK skojarzonych z działaniem, które wyzwoliło alert |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
