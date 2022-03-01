---
title: DeviceTvmSoftwareVulnerabilitiesKB w zaawansowanym schemacie wyszukiwania
description: Informacje o luki w zabezpieczeniach oprogramowania śledzone przez funkcje zarządzania & zagrożeniami w tabeli DeviceTvmSoftwareVulnerabilitiesKB zaawansowanego schematu wyszukiwania.
keywords: zaawansowane szukanie, schłolenie przed zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, schemat, reference, kusto, tabela, kolumna, typ danych, opis, zagrożenie & zarządzanie lukami w zabezpieczeniach, TVM, zarządzanie urządzeniami, oprogramowanie, zapasy, luki w zabezpieczeniach, identyfikator CVE, CVSS, DeviceTvmSoftwareVulnerabilitiesKB
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
ms.openlocfilehash: 545e2a3ba12924d364facda14a7a564ead212f30
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017892"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftwareVulnerabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



Tabela `DeviceTvmSoftwareVulnerabilitiesKB` w zaawansowanym schemacie chłoń zawiera listę luk w zabezpieczeniach, które mogą & w przypadku zarządzania lukami w zabezpieczeniach.[](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `CveId` | `string` | Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu CVE (Common Vulnerabilities and Exposures) |
| `CvssScore` | `string` | Wynik ważności przypisany do luki w zabezpieczeniach na mocy tego systemu oceniania luk (CVSS) |
| `IsExploitAvailable` | `boolean` | Wskazuje, czy kod wykorzystania luki w zabezpieczeniach jest publicznie dostępny. |
| `VulnerabilitySeverityLevel` | `string` | Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń |
| `LastModifiedTime` | `datetime` | Data i godzina ostatniej modyfikacji elementu lub powiązanych metadanych |
| `PublishedDate` | `datetime` | Lukę w zabezpieczeniach przed datą ujawniane |
| `VulnerabilityDescription` | `string` | Opis luki w zabezpieczeniach i związanych z nim czynników ryzyka |
| `AffectedSoftware` | `string` | Lista wszystkich produktów oprogramowania, których dotyczy luka |

## <a name="related-topics"></a>Tematy pokrewne

- [Aktywne poszukiwania zagrożeń](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Omówienie zarządzania & zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)