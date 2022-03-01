---
title: Tworzenie powiadomień o dokładnie tych działaniach dotyczących dopasowania danych
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
description: Dowiedz się, jak tworzyć powiadomienia dotyczące dokładnie tych działań.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e5f7c2a2d724a66aea1ce55658ff84e6e0da4738
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010412"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Tworzenie powiadomień o dokładnie tych działaniach dotyczących dopasowania danych

W przypadku [tworzenia niestandardowych typów informacji poufnych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) z dokładnym dopasowaniem danych (EDM) w dzienniku inspekcji jest tworzona [szereg działań](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log). Za pomocą polecenia cmdlet [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) programu PowerShell możesz tworzyć powiadomienia o tych działaniach:

- CreateSchema
- EditSchema
- RemoveSchema
- UploadDataFailed
- UploadDataCompleted

> [!NOTE]
 Możliwość tworzenia powiadomień dotyczących działań w ramach zarządzania EDM jest dostępna tylko w całym świecie i tylko GCC chmurach.

## <a name="pre-requisites"></a>Wymagania wstępne

Konto, z których korzystasz, musi być jednym z następujących:

- Administrator globalny
- Administrator zgodności
- Exchange Online administratora

Aby dowiedzieć się więcej o uprawnieniach DLP, zobacz [Uprawnienia](data-loss-prevention-policies.md#permissions).

Klasyfikacja oparta na programie EDM jest zawarta w tych subskrypcjach:

- Office 365 E5
- Microsoft 365 E5
- Zgodność platformy Microsoft 365 E5
- Ochrona informacji i zarządzanie informacjami na platformie Microsoft E5/A5

Aby dowiedzieć się więcej o licencjonowaniu DLP, zobacz [Microsoft 365 licencjonowania w celu zapewnienia & zgodnością](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>Konfigurowanie powiadomień dotyczących działań w ramach usługi EDM

1. Połączenie się z Centrum [& zgodności w programie PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom polecenie `New-ProtectionAlert` cmdlet, używając działania, dla którego chcesz utworzyć powiadomienie.  Jeśli na przykład chcesz uzyskać powiadomienie o akcji **PrzekażDanychUzupełniane** , uruchom:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    Dla pliku **UploadDataFailed** możesz uruchomić:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>Artykuły pokrewne

- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)