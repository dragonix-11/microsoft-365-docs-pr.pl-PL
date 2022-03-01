---
title: Hunt for exposed devices
description: Dowiedz się Zarządzanie zagrożeniami i lukami w jaki sposób mogą być używane w celu pomocy administratorom zabezpieczeń, administratorom IT i administratorom usługi SecOps współpracę.
keywords: Program Microsoft Defender for Endpoint-tvm scenarios, Microsoft Defender for Endpoint, tvm, tvm scenarios, reduce threat & vulnerability exposure, reduce threat and vulnerability, improve security configuration, increase Microsoft Secure Score for Devices, increase threat & vulnerability Microsoft Secure Score for Devices, Microsoft Secure Score for Devices, exposure score, security controls
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 40544ab3879acd026d7f327e63d02bdb79d00d83
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997297"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>Hunt for exposed devices - Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>Użyj zaawansowanego wyszukiwania, aby znaleźć urządzenia z lukami w zabezpieczeniach

Zaawansowane szukanie to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni nieprzetworzone dane. Możesz proaktywnie przeprowadzać inspekcje zdarzeń w sieci, aby zlokalizować wskaźniki zagrożeń i jednostki. Elastyczny dostęp do danych umożliwia niewyszkolone czasy, w których są poszukiwane zarówno znane, jak i potencjalne zagrożenia. [Dowiedz się więcej o zaawansowanym chłonie](advanced-hunting-overview.md)

### <a name="schema-tables"></a>Tabele schematów

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) — spis oprogramowania zainstalowanych na urządzeniach, w tym informacje o wersji i stanie zakończenia pomocy technicznej.

- [DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) — luki w oprogramowaniu na urządzeniach oraz lista dostępnych aktualizacji zabezpieczeń, które mogą wykorzystać luki w zabezpieczeniach.

- [DeviceTvmSoftwareVulnerabilitiesKB —](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) baza wiedzy na temat dostępnych publicznie luk w zabezpieczeniach, w tym tego, czy kod wykorzystujący lukę jest publicznie dostępny.

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) — zagrożenia i zdarzenia zarządzanie lukami w zabezpieczeniach, oznaczające stan różnych konfiguracji zabezpieczeń na urządzeniach.

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) — baza wiedzy o różnych konfiguracjach zabezpieczeń używanych przez funkcje zarządzania zagrożeniami i & do oceny urządzeń; obejmuje mapowania na różne standardy i punkty odniesienia

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>Sprawdzanie, na których urządzeniach obowiązują alerty o wysokim poziomie ważności

1. Przejdź do **tematu Szukanie** \> **zaawansowanego** wyszukiwania w okienku nawigacji po lewej stronie Microsoft 365 Defender portalu.

2. Przewiń w dół do zaawansowanych schematów wyszukiwania w programie TVM, aby zapoznać się z nazwami kolumn.

3. Wprowadź następujące zapytania:

    ```kusto
    // Search for devices with High active alerts or Critical CVE public exploit
    let DeviceWithHighAlerts = AlertInfo
    | where Severity == "High"
    | project Timestamp, AlertId, Title, ServiceSource, Severity
    | join kind=inner (AlertEvidence | where EntityType == "Machine" | project AlertId, DeviceId, DeviceName) on AlertId
    | summarize HighSevAlerts = dcount(AlertId) by DeviceId;
    let DeviceWithCriticalCve = DeviceTvmSoftwareVulnerabilities
    | join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
    | where IsExploitAvailable == 1 and CvssScore >= 7
    | summarize NumOfVulnerabilities=dcount(CveId),
    DeviceName=any(DeviceName) by DeviceId;
    DeviceWithCriticalCve
    | join kind=inner DeviceWithHighAlerts on DeviceId
    | project DeviceId, DeviceName, NumOfVulnerabilities, HighSevAlerts
    ```

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)
- [Interfejsy API](next-gen-threat-and-vuln-mgt.md#apis)
- [Konfigurowanie dostępu do danych dla Zarządzanie zagrożeniami i lukami użytkowników](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [Omówienie zaawansowanego wyszukiwania](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Wszystkie zaawansowane narzędzia do łowiectwo](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)
