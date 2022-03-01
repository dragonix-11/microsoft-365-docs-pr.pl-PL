---
title: Krok 6. Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: Dowiedz się, jak połączyć Microsoft Intune usługą Defender dla punktu końcowego i monitorować ryzyko urządzenia jako warunek dostępu.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: f58611f555b022b69211e39f149effef925dde17
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015768"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>Krok 6. Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń

Po wdrożeniu programu Microsoft Defender dla punktu końcowego w organizacji można uzyskać więcej informacji i lepszą ochronę swoich urządzeń, integrując program Microsoft Intune usługą Defender for Endpoint. W przypadku urządzeń przenośnych obejmuje to możliwość monitorowania ryzyka urządzenia jako warunku dostępu. W Windows możesz monitorować zgodność tych urządzeń z planami bazowymi zabezpieczeń. 

![Ilustracja integracji programu Defender Microsoft Intune punktem końcowym i programem](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

Na poniższej ilustracji:
- Program Microsoft Defender for Endpoint znacznie zwiększa zaawansowaną ochronę przed zagrożeniami dla urządzeń. 
- Chociaż program Microsoft Intune umożliwia ustawianie zasad ochrony aplikacji i zarządzanie urządzeniami (w tym zmianami konfiguracji), program Defender for Endpoint nieustannie monitoruje urządzenia pod różnymi zagrożeniami i może podjąć zautomatyzowane działania w celu podjęcia działań naprawczych. 
- Za pomocą usługi Intune możesz dodać urządzenia do usługi Defender for Endpoint. W takim przypadku te urządzenia również mogą współpracować z zapobieganiem utracie danych w punkcie Microsoft 365 (Zapobieganie utracie danych w punkcie końcowym).

Ten artykuł zawiera następujące kroki:
- Połączenie Microsoft Intune do usługi Defender dla punktu końcowego
- Monitorowanie ryzyka związanego z urządzeniem
- Monitorowanie zgodności z planami bazowymi zabezpieczeń

Jeśli program Defender dla punktu końcowego nie został jeszcze skonfigurować, skonfiguruj środowisko oceny i pilotażu we współpracy z [administratorem ochrony przed zagrożeniami](../security/defender/eval-defender-endpoint-overview.md). Możesz pracować z grupą pilotażową, aby wypróbować funkcje z tego artykułu.

## <a name="connect-microsoft-intune-to-defender-for-endpoint"></a>Połączenie Microsoft Intune do usługi Defender dla punktu końcowego

Konfigurowanie integracji programu Microsoft Intune z programem Defender for Endpoint jest proste. Skorzystaj z tego artykułu: [Konfigurowanie programu Microsoft Defender dla punktu końcowego w usłudze Intune](/mem/intune/protect/advanced-threat-protection-configure). 

![Połączenie Intune do programu Microsoft Defender dla punktu końcowego](../media/devices/connect-intune-to-microsoft-defender.png#lightbox)

## <a name="monitor-device-risk-as-a-condition-for-access"></a>Monitorowanie ryzyka urządzenia jako warunku dostępu

Mając wdrożoną usługę Microsoft Defender for Endpoint, możesz korzystać z sygnałów zagrożeń. Umożliwia to zablokowanie dostępu do urządzeń na podstawie ich wyniku ryzyka. Firma Microsoft zaleca zezwolenie na dostęp do urządzeń o średniej lub średnich ocenach ryzyka.

W systemach Android i iOS i iPadOS sygnały zagrożeń mogą być używane w ramach zasad ochrony aplikacji (APP). Aby uzyskać informacje na temat konfigurowania tego ustawienia, zobacz Tworzenie i przypisywanie zasad ochrony [aplikacji w celu ustawienia poziomu ryzyka urządzenia](/mem/intune/protect/advanced-threat-protection-configure).

Dla wszystkich platform możesz ustawić poziom ryzyka w istniejących zasadach zgodności urządzeń. Zobacz [Tworzenie i przypisywanie zasad zgodności w celu ustawienia poziomu ryzyka urządzenia](/mem/intune/protect/advanced-threat-protection-configure).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>Wdrażanie planu bazowego zabezpieczeń i monitorowanie zgodności w tych ustawieniach

Dotyczy: Windows 10, Windows 11

Artykuł Krok [5. Wdrożenie profilów konfiguracji](manage-devices-with-intune-configuration-profiles.md) zaleca rozpoczęcie pracy z profilami konfiguracji przy użyciu planu bazowego zabezpieczeń dostępnego dla użytkowników Windows 10 i Windows 11. Program Microsoft Defender for Endpoint zawiera również linie bazowe zabezpieczeń, które zapewniają ustawienia optymalizujące wszystkie kontrolki zabezpieczeń w stosie programu Defender dla punktu końcowego, w tym ustawienia dla programu wykrywanie i reagowanie w punktach końcowych (EDR). Są one także wdrażane przy użyciu Microsoft Intune.

Najlepiej jest wtedy, gdy urządzenia wdrożone w usłudze Defender for Endpoint są wdrożone według planu bazowego: plan bazowy zabezpieczeń usługi Windows Intune, który wstępnie zabezpiecza program Windows, a następnie usługa Defender for Endpoint security baseline jest wdrożona w warstwie u góry w celu optymalnego skonfigurowania programu Defender pod względem zabezpieczeń punktu końcowego.

Aby korzystać z najnowszych danych na temat zagrożeń i czynników ryzyka oraz minimalizować konflikty w przypadku rozwoju planu bazowego, zawsze zastosuj najnowsze wersje linii bazowych we wszystkich produktach zaraz po ich ich zastosowaniu. 

Za pomocą usługi Defender for Endpoint możesz monitorować zgodność z tymi planami bazowymi. 

![Karta monitorowania zgodności z planami bazowymi zabezpieczeń](../media/devices/secconmgmt-baseline-card.png#lightbox)

Aby wdrożyć plan bazowy zabezpieczeń i monitorować zgodność z tymi ustawieniami, należy wykonać czynności opisane w poniższej tabeli.


|Krok  |Opis  |
|---------|---------|
|1     |Zapoznaj się z kluczowymi pojęciami i porównaj program Microsoft Defender dla punktu końcowego i podstawowe Windows zabezpieczeń usługi Intune. <br><br>Aby [uzyskać zalecenia, zobacz Zwiększanie zgodności z planem](../security/defender-endpoint/configure-machines-security-baseline.md) bazowym zabezpieczeń programu Microsoft Defender for Endpoint.<br><br>Zobacz [Używanie planu bazowego zabezpieczeń do konfigurowania Windows w ](/mem/intune/protect/security-baselines) usłudze Intune, aby zapoznać się z listą dostępnych baz bazowych zabezpieczeń i sposobu unikania konfliktów.         |
|2     |  Wd Windows ustawień planu bazowego zabezpieczeń dla usługi Intune. Możliwe, że zostało to już zrealizowane, jeśli zostały one już przez Ciebie obserwowane zgodnie z wskazówkami w [kroku 5. Wdrażanie profilów konfiguracji](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  Wdeksuj usługę Defender dla ustawień planu bazowego punktu końcowego dla usługi Intune. Zobacz [Zarządzanie profilami według planu bazowego](/mem/intune/protect/security-baselines-configure) Microsoft Intune w programie Microsoft Intune, aby utworzyć profil i wybrać wersję podstawową.<br><br>Możesz również wykonać instrukcje tutaj: [Przejrzyj i przypisz plan bazowy zabezpieczeń programu Microsoft Defender for Endpoint](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | W programie Defender for Endpoint zapoznaj się z [kartą planu bazowego zabezpieczeń na temat zarządzania konfiguracją urządzeń](../security/defender-endpoint/configure-machines.md).          |
| | |

## <a name="next-steps"></a>Następne kroki
Przejdź do [kroku 7. Wdrożenie funkcji DLP za pomocą funkcji ochrony informacji w punktach końcowych](manage-devices-with-intune-dlp-mip.md).