---
title: Tabela DeviceTvmSoftwareVulnerabilities w zaawansowanym schemacie wyszukiwania
description: Informacje na temat luk w zabezpieczeniach oprogramowania dostępnych na urządzeniach oraz listy dostępnych aktualizacji zabezpieczeń, które mają na celu ochronę przed każdą luką w zabezpieczeniach w tabeli DeviceTvmSoftwareVulnerabilities zaawansowanego schematu wyszukiwania.
keywords: zaawansowane szukanie, schłoń pod niebędący zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, zagrożenie & zarządzanie lukami w zabezpieczeniach, TVM, zarządzanie urządzeniami, oprogramowanie, zapasy, luki w zabezpieczeniach, identyfikator CVE, system operacyjny DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: a6588134ba2cdf166a465998cd0b1a4fd7134dbb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017918"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

>[!IMPORTANT]
> Niektóre informacje odnoszą się do produktu przed jego premierą, który może zostać znacząco zmodyfikowany przed jego premierą komercyjną. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Tabela `DeviceTvmSoftwareVulnerabilities` w zaawansowanym schemacie chłoń zawiera listę zagrożeń, [które](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) mogą & luk w zabezpieczeniach w zainstalowanych produktach oprogramowania. Ta tabela zawiera również informacje o systemie operacyjnym, identyfikatory CVE oraz informacje o ważności luk w zabezpieczeniach. Za pomocą tej tabeli można na przykład poszukać zdarzeń obejmujących urządzenia, które mają poważne luki w zabezpieczeniach związane z ich oprogramowaniem. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli.

>[!NOTE]
> Tabele `DeviceTvmSoftwareInventory` i `DeviceTvmSoftwareVulnerabilities` te zastąpiły tabelę `DeviceTvmSoftwareInventoryVulnerabilities` . Razem dwie pierwsze tabele zawierają więcej kolumn, które ułatwiają informowanie o twoich zarządzanie lukami w zabezpieczeniach lub poszukiwania narażonych urządzeń.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na komputerze. Wskazuje określone systemy operacyjne, w tym odmiany tej samej rodziny, takie jak Windows 11, Windows 10 i Windows 7. |
| `OSVersion` | `string` | Wersja systemu operacyjnego działającego na komputerze |
| `OSArchitecture` | `string` | Architektura systemu operacyjnego działającego na komputerze |
| `SoftwareVendor` | `string` | Nazwa wydawcy oprogramowania |
| `SoftwareName` | `string` | Nazwa produktu oprogramowania |
| `SoftwareVersion` | `string` | Numer wersji produktu oprogramowania |
| `CveId` | `string` | Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu CVE (Common Vulnerabilities and Exposures) |
| `VulnerabilitySeverityLevel` | `string` | Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń |
| `RecommendedSecurityUpdate` | `string` | Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez wydawcę oprogramowania w celu rozwiązania problemu z luką |
| `RecommendedSecurityUpdateId` | `string` | Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB) |



## <a name="related-topics"></a>Tematy pokrewne

- [Aktywne poszukiwania zagrożeń](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Omówienie zarządzania & zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)