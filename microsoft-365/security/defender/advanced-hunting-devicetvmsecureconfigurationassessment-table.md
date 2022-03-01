---
title: DeviceTvmSecureConfigurationAssessment table in the advanced hunting schema
description: Informacje o zdarzeniach oceny zabezpieczeń w tabeli DeviceTvmSecureConfigurationAssessment zaawansowanego schematu wyszukiwania. Zdarzenia te zawierają informacje o urządzeniu, szczegóły konfiguracji zabezpieczeń, wpływ i informacje o zgodności.
keywords: zaawansowane szukanie, schłoń pod niebędące zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, zagrożenie & zarządzanie lukami w zabezpieczeniach, TVM, zarządzanie urządzeniami, konfiguracja zabezpieczeń, DeviceTvmSecureConfigurationAssessment
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
ms.openlocfilehash: 43f44458cde7d466d1097034e7bcc9d0e3072745
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017874"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender


Każdy wiersz tabeli zawiera `DeviceTvmSecureConfigurationAssessment` zdarzenie oceny określonej konfiguracji zabezpieczeń ze strony zarządzania zagrożeniami & [lukami w zabezpieczeniach](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Skorzystaj z tego odwołania, aby sprawdzić najnowsze wyniki testów i określić, czy urządzenia są zgodne.

Możesz połączyć tę tabelę z tabelą [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) `ConfigurationId` `ConfigurationDescription` `DeviceTvmSecureConfigurationAssessmentKB` przy użyciu, aby na przykład wyświetlić tekstowy opis konfiguracji z kolumny tabeli w wynikach oceny konfiguracji.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Unikatowy identyfikator urządzenia w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na urządzeniu. Wskazuje określone systemy operacyjne, w tym odmiany tej samej rodziny, takie jak Windows 11, Windows 10 i Windows 7.|
| `Timestamp` | `datetime` | Data i godzina wygenerowania rekordu |
| `ConfigurationId` | `string` | Unikatowy identyfikator określonej konfiguracji |
| `ConfigurationCategory` | `string` | Kategoria lub grupowanie, do których należy konfiguracja: Aplikacja, system operacyjny, sieć, konta, kontrolki zabezpieczeń |
| `ConfigurationSubcategory` | `string` | Podkategoria lub podgrupowanie, do którego należy konfiguracja. W wielu przypadkach ciąg opisuje konkretne funkcje lub możliwości. |
| `ConfigurationImpact` | `string` | Wpływ oceny konfiguracji na ogólny wynik konfiguracji (1–10) |
| `IsCompliant` | `boolean` | Wskazuje, czy konfiguracja lub zasady są poprawnie skonfigurowane. |
| `IsApplicable` | `boolean` | Wskazuje, czy konfiguracja lub zasady dotyczą urządzenia. |
| `Context` | `string` | Dodatkowe informacje kontekstowe dotyczące konfiguracji lub zasad |
| `IsExpectedUserImpact` | `boolean` | Wskazuje, czy zastosowanie konfiguracji lub zasad będzie miało wpływ na użytkowników |

Możesz wypróbować to przykładowe zapytanie, aby zwrócić informacje na urządzeniach z niezgodnymi konfiguracjami oprogramowania antywirusowego wraz z odpowiednimi metadanymi konfiguracji z `DeviceTvmSecureConfigurationAssessmentKB` tabeli:

```kusto
// Get information on devices with antivirus configurations issues
DeviceTvmSecureConfigurationAssessment
| where ConfigurationSubcategory == 'Antivirus' and IsApplicable == 1 and IsCompliant == 0
| join kind=leftouter (
    DeviceTvmSecureConfigurationAssessmentKB
    | project ConfigurationId, ConfigurationName, ConfigurationDescription, RiskDescription, Tags, ConfigurationImpact
) on ConfigurationId
| project DeviceName, OSPlatform, ConfigurationId, ConfigurationName, ConfigurationCategory, ConfigurationSubcategory, ConfigurationDescription, RiskDescription, ConfigurationImpact, Tags
```

## <a name="related-topics"></a>Tematy pokrewne

- [Aktywne poszukiwania zagrożeń](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Omówienie zarządzania & zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)