---
title: DeviceTvmSecureConfigurationAssessmentKB w zaawansowanym schemacie wyszukiwania
description: Poznaj różne bezpieczne konfiguracje oceniane przez zarządzanie & zagrożeniami w tabeli DeviceTvmSecureConfigurationAssessmentKB zaawansowanego schematu wyszukiwania.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, informacje o & zarządzanie lukami w zabezpieczeniach , TVM, zarządzanie urządzeniami, konfiguracja zabezpieczeń, MITRE ATT&CK Framework, baza wiedzy, KB, DeviceTvmSecureConfigurationAssessmentKB
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
ms.openlocfilehash: 81f03a665a0c825388335c925cb908f3b931a918
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017924"
---
# <a name="devicetvmsecureconfigurationassessmentkb"></a>DeviceTvmSecureConfigurationAssessmentKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender


Tabela `DeviceTvmSecureConfigurationAssessmentKB` w zaawansowanym schemacie chłoń zawiera informacje na temat różnych bezpiecznych konfiguracji sprawdzanych przez funkcje [zarządzania & zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Obejmuje on również informacje o ryzyku, powiązane punkty odniesienia branżowe i odpowiednie techniki MITRE ATT&technik i taktyk CK.

Ta tabela nie zwraca zdarzeń ani rekordów. Zalecamy dołączenie tej tabeli do tabeli [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) `ConfigurationId` przy użyciu tej tabeli w celu wyświetlenia informacji tekstowych o konfiguracjach zabezpieczeń w zwróconych ocenach.

Na przykład podczas wykonywania zapytań `DeviceTvmSecureConfigurationAssessment` `ConfigurationDescription` w tabeli możesz zechcieć wyświetlić konfiguracje zabezpieczeń, które są dostępne w wynikach testu. Możesz wyświetlić te informacje, dołączając tę tabelę do używania `DeviceTvmSecureConfigurationAssessment` i `ConfigurationId` używania programu Project `ConfigurationDescription`.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `ConfigurationId` | `string` | Unikatowy identyfikator określonej konfiguracji |
| `ConfigurationImpact` | `string` | Wpływ oceny konfiguracji na ogólny wynik konfiguracji (1–10) |
| `ConfigurationName` | `string` | Nazwa wyświetlana konfiguracji |
| `ConfigurationDescription` | `string` | Opis konfiguracji |
| `RiskDescription` | `string` | Opis skojarzonego ryzyka |
| `ConfigurationCategory` | `string` | Kategoria lub grupowanie, do których należy konfiguracja: Aplikacja, system operacyjny, sieć, konta, kontrolki zabezpieczeń|
| `ConfigurationSubcategory` | `string` |Podkategoria lub podgrupowanie, do którego należy konfiguracja. W wielu przypadkach opisano konkretne funkcje. |
| `ConfigurationBenchmarks` | `string` | Lista branżowych poziomów odniesienia zalecających taką samą lub podobną konfigurację |
| `Tags` | `string` | Etykiety reprezentujące różne atrybuty używane do identyfikowania lub kategoryzowania konfiguracji zabezpieczeń |
| `RemediationOptions` | `string` | Zalecane działania w celu zmniejszenia lub rozwiązania wszelkich związanych z tym czynników ryzyka |

Możesz wypróbować to przykładowe zapytanie, aby zwrócić odpowiednie metadane konfiguracji wraz z informacjami na urządzeniach z niezgodnymi konfiguracjami oprogramowania antywirusowego z `DeviceTvmSecureConfigurationAssessment` tabeli:

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