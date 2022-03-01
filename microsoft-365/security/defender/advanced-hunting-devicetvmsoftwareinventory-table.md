---
title: Tabela DeviceTvmSoftwareInventory w zaawansowanym schemacie wyszukiwania
description: Informacje o spisie oprogramowania na Twoich urządzeniach w tabeli DeviceTvmSoftwareInventory zaawansowanego schematu wyszukiwania.
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
ms.openlocfilehash: 10a184e6ce36129a84197cc02caae3b96625e39a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017888"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

>[!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.


Tabela `DeviceTvmSoftwareInventory` w zaawansowanym schemacie wyszukiwania zawiera spis narzędzi [](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) do zarządzania & lukami w zabezpieczeniach oprogramowania zainstalowanego obecnie na urządzeniach w Twojej sieci, łącznie z informacjami o zakończeniu pomocy technicznej. Możesz na przykład poszukać zdarzeń obejmujących urządzenia instalowane z obecnie podatną na zagrożenia wersją oprogramowania. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli.

>[!NOTE]
> Tabele `DeviceTvmSoftwareInventory` i `DeviceTvmSoftwareVulnerabilities` te zastąpiły tabelę `DeviceTvmSoftwareInventoryVulnerabilities` . Razem dwie pierwsze tabele zawierają więcej kolumn, które ułatwiają informowanie o działaniach w zakresie zarządzania zagrożeniami lub poszukiwania narażonych urządzeń.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na komputerze. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 11, Windows 10 i Windows 7. |
| `OSVersion` | `string` | Wersja systemu operacyjnego działającego na komputerze |
| `OSArchitecture` | `string` | Architektura systemu operacyjnego działającego na komputerze |
| `SoftwareVendor` | `string` | Nazwa dostawcy oprogramowania |
| `SoftwareName` | `string` | Nazwa produktu oprogramowania |
| `SoftwareVersion` | `string` | Numer wersji produktu oprogramowania |
| `EndOfSupportStatus` | `string` | Wskazuje etap cyklu życia produktu oprogramowania względem jego określonej daty zakończenia wsparcia technicznego (EOS) lub daty zakończenia użytkowania (EOL) |
| `EndOfSupportDate` | `string` | Data zakończenia pomocy technicznej (EOS) lub daty zakończenia użytkowania (EOL) produktu oprogramowania |



## <a name="related-topics"></a>Tematy pokrewne

- [Aktywne poszukiwania zagrożeń](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Omówienie zarządzania & zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)