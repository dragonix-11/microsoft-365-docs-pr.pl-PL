---
title: Twórz powiadomienia dla działań dokładnego dopasowania danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak tworzyć powiadomienia dotyczące dokładnych działań dopasowania danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1a9c629e5258efd096ce1412a7a42bc7bc672008
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641345"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Twórz powiadomienia dla działań dokładnego dopasowania danych

Podczas [tworzenia niestandardowych typów informacji poufnych z dokładnym dopasowaniem danych (EDM)](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) w [dzienniku inspekcji](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log) jest tworzonych wiele działań. Polecenie cmdlet [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) programu PowerShell umożliwia tworzenie powiadomień informujących o następujących działaniach:

- CreateSchema
- EditSchema
- RemoveSchema
- UploadDataFailed
- UploadDataCompleted

> [!NOTE]
 Możliwość tworzenia powiadomień dotyczących działań EDM jest dostępna tylko dla chmur world wide i GCC.

## <a name="pre-requisites"></a>Wymagania wstępne

Używane konto musi być jednym z następujących:

- Administrator globalny
- Administrator zgodności
- administrator Exchange Online

Aby dowiedzieć się więcej o uprawnieniach DLP, zobacz [Uprawnienia](data-loss-prevention-policies.md#permissions).

Klasyfikacja oparta na programie EDM jest uwzględniona w następujących subskrypcjach:

- Office 365 E5
- Microsoft 365 E5
- Zgodność platformy Microsoft 365 E5
- Microsoft E5/A5 Information Protection i ład

Aby dowiedzieć się więcej na temat licencjonowania DLP, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>Konfigurowanie powiadomień dotyczących działań EDM

1. Połącz się z programem [PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

2. `New-ProtectionAlert` Uruchom polecenie cmdlet przy użyciu działania, dla których chcesz utworzyć powiadomienie.  Jeśli na przykład chcesz otrzymać powiadomienie o wystąpieniu akcji **UploadDataCompleted** , uruchom polecenie:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    W przypadku **polecenia UploadDataFailed** można uruchomić następujące polecenie:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>Powiązane artykuły:

- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)
