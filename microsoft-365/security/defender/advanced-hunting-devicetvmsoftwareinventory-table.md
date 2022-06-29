---
title: Tabela DeviceTvmSoftwareInventory w zaawansowanym schemacie wyszukiwania zagrożeń
description: Informacje na temat spisu oprogramowania na urządzeniach można znaleźć w tabeli DeviceTvmSoftwareInventory zaawansowanego schematu wyszukiwania zagrożeń.
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, telemetria, dokumentacja schematu, kusto, tabela, kolumna, typ danych, opis, zarządzanie lukami w zabezpieczeniach & zagrożeń, zarządzanie urządzeniami, oprogramowanie, spis, luki w zabezpieczeniach, identyfikator CVE, urządzenie systemu operacyjnegoTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: cecbf2078bff0143a5c14b8b0cffb636d4fa3454
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490802"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

>[!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.


Tabela `DeviceTvmSoftwareInventory` w zaawansowanym schemacie wyszukiwania zagrożeń zawiera spis [zarządzania lukami w zabezpieczeniach & zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) oprogramowania obecnie zainstalowanego na urządzeniach w sieci, w tym informacje o zakończeniu pomocy technicznej. Można na przykład wyszukiwać zdarzenia dotyczące urządzeń zainstalowanych z obecnie podatną na zagrożenia wersją oprogramowania. To odwołanie służy do konstruowania zapytań, które zwracają informacje z tabeli.

>[!NOTE]
> Tabele `DeviceTvmSoftwareInventory` i `DeviceTvmSoftwareVulnerabilities` zastąpiły tabelę `DeviceTvmSoftwareInventoryVulnerabilities` . Razem dwie pierwsze tabele zawierają więcej kolumn, których można użyć, aby ułatwić informowanie o działaniach związanych z zarządzaniem vulnerablity lub wyszukiwanie urządzeń podatnych na zagrożenia.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, zobacz [zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Unikatowy identyfikator maszyny w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) maszyny |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na maszynie. Wskazuje to określone systemy operacyjne, w tym odmiany w tej samej rodzinie, takie jak Windows 11, Windows 10 i Windows 7. |
| `OSVersion` | `string` | Wersja systemu operacyjnego uruchomionego na maszynie |
| `OSArchitecture` | `string` | Architektura systemu operacyjnego działającego na maszynie |
| `SoftwareVendor` | `string` | Nazwa dostawcy oprogramowania |
| `SoftwareName` | `string` | Nazwa produktu oprogramowania |
| `SoftwareVersion` | `string` | Numer wersji produktu oprogramowania |
| `EndOfSupportStatus` | `string` | Wskazuje etap cyklu życia produktu oprogramowania względem określonej daty zakończenia wsparcia (EOS) lub daty zakończenia okresu eksploatacji (EOL) |
| `EndOfSupportDate` | `string` | Data zakończenia wsparcia technicznego (EOS) lub data zakończenia okresu eksploatacji (EOL) produktu oprogramowania |
| `ProductCodeCpe` | `string` | cpe produktu oprogramowania lub "niedostępne", jeśli nie ma cpe |
| `CveTags` | `string` | Tablica tagów odpowiednich dla CVE. Obecnie obsługiwane tagi to "ZeroDay" i "NoSecurityUpdate".

## <a name="related-topics"></a>Tematy pokrewne

- [Proaktywne wyszukiwanie zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
- [Omówienie zarządzania lukami w zabezpieczeniach & zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)