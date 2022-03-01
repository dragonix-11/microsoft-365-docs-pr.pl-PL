---
title: Tabela DeviceTvmSoftwareEvidenceBeta w zaawansowanym schemacie wyszukiwania
description: Dowiedz się, jak używać tabeli DeviceTvmSoftwareEvidenceBeta w zaawansowanym schemacie wyszukiwania.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, informacje o & zarządzanie lukami w zabezpieczeniach , dowód, dowód oprogramowania, telewizja, zarządzanie urządzeniami, oprogramowanie, zapasy, luki w zabezpieczeniach, identyfikator CVE, urządzenie systemu operacyjnego DeviceTvmSoftwareEvidenceBeta
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
ms.openlocfilehash: 7fd064b906e4afe5e337df85d9dc6f174edc99cf
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020821"
---
# <a name="devicetvmsoftwareevidencebeta"></a>DeviceTvmSoftwareEvidenceBeta

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

> [!IMPORTANT]
> Tabela `DeviceTvmSoftwareEvidenceBeta` jest obecnie w wersji beta. Gdy tabela opuści wersję beta, zmieni się ostateczna nazwa tabeli, a nazwy kolumn również mogą się zmienić. Modyfikacje będą prawdopodobnie przerwać zapytania, które nadal mają poprzednie nazwy. Zaleca się, aby użytkownicy przeglądali i dostosowali swoje zapytania po zakończeniu tej tabeli. 


Tabela `DeviceTvmSoftwareEvidenceBeta` w zaawansowanym schemacie chłoniania zawiera dane z sekcji [& związanej](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) z zarządzaniem lukami w [zabezpieczeniach związanych z sekcją dowodów oprogramowania](/microsoft-365/security/defender-endpoint/tvm-software-inventory#software-evidence). Ta tabela pozwala na wyświetlenie dowodów na wykrycie określonego oprogramowania na urządzeniu. Za pomocą tej tabeli można na przykład zidentyfikować ścieżki plików określonego oprogramowania. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Unikatowy identyfikator urządzenia w usłudze |
| `SoftwareVendor` | `string` | Nazwa wydawcy oprogramowania |
| `SoftwareName` | `string` | Nazwa produktu oprogramowania |
| `SoftwareVersion` | `string` | Numer wersji produktu oprogramowania |
| `RegistryPaths` | `dynamic` | Ścieżki rejestru, w których wykryto dowody wskazujące na istnienie oprogramowania na urządzeniu |
| `DiskPaths` | `dynamic` | Ścieżki dysków, w których wykryto informacje na poziomie pliku wskazujące na istnienie oprogramowania na urządzeniu |
| `LastSeenTime` | `string` | Data i godzina ostatniego widzianego urządzenia w tej usłudze |




## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zarządzania & zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Aktywne poszukiwania zagrożeń](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
