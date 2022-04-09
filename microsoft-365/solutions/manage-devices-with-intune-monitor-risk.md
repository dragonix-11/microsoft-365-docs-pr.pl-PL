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
description: Dowiedz się, jak połączyć Microsoft Intune z usługą Defender for Endpoint i monitorować ryzyko urządzenia jako warunek dostępu.
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
ms.openlocfilehash: 9000a56bb0bf4819f4fc2e9bf7553a19772efe66
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64730885"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>Krok 6. Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń

Po wdrożeniu Ochrona punktu końcowego w usłudze Microsoft Defender w organizacji możesz uzyskać lepszy wgląd i ochronę urządzeń, integrując Microsoft Intune z usługą Defender for Endpoint. W przypadku urządzeń przenośnych obejmuje to możliwość monitorowania ryzyka urządzenia jako warunku dostępu. W przypadku urządzeń Windows można monitorować zgodność tych urządzeń z punktami odniesienia zabezpieczeń. 

Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender obejmuje dołączanie punktów końcowych. Jeśli użyto Intune do dołączania punktów końcowych (zalecane), nawiązano już połączenie Microsoft Intune z usługą Defender for Endpoint. Jeśli do dołączania punktów końcowych do usługi Defender for Endpoint użyto innej metody, zobacz [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w Intune](/mem/intune/protect/advanced-threat-protection-configure), aby upewnić się, że skonfigurowano połączenie między usługami Intune i Ochrona punktu końcowego w usłudze Microsoft Defender. 


![Ilustracja integracji usługi Defender for Endpoint i Microsoft Intune](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

Na tej ilustracji:
- Ochrona punktu końcowego w usłudze Microsoft Defender znacznie zwiększa wyrafinowanie ochrony przed zagrożeniami dla urządzeń. 
- Chociaż Microsoft Intune umożliwia ustawianie zasad ochrony aplikacji i zarządzanie urządzeniami (w tym zmianami konfiguracji), usługa Defender for Endpoint stale monitoruje urządzenia pod kątem zagrożeń i może podejmować zautomatyzowane działania w celu skorygowania ataków. 
- Możesz połączyć Microsoft Intune z usługą Defender for Endpoint, aby monitorować ryzyko urządzenia i zgodność z punktami odniesienia zabezpieczeń.

Ten artykuł zawiera następujące kroki:
- Monitorowanie ryzyka urządzenia
- Monitorowanie zgodności z punktami odniesienia zabezpieczeń

Jeśli usługa Defender for Endpoint nie została jeszcze skonfigurowana, skontaktuj się z administratorem ochrony przed zagrożeniami, aby [skonfigurować środowisko ewaluacji i pilotażowe](../security/defender/eval-defender-endpoint-overview.md). Możesz pracować z grupą pilotażową, aby wypróbować możliwości w tym artykule.

## <a name="monitor-device-risk-as-a-condition-for-access"></a>Monitorowanie ryzyka urządzenia jako warunku dostępu

Dzięki Ochrona punktu końcowego w usłudze Microsoft Defender wdrożonym można korzystać z sygnałów ryzyka zagrożenia. Dzięki temu można zablokować dostęp do urządzeń na podstawie ich oceny ryzyka. Firma Microsoft zaleca zezwolenie na dostęp do urządzeń z wynikiem ryzyka średnim lub niższym.

W przypadku systemów Android i iOS/iPadOS sygnały zagrożeń mogą być używane w ramach zasad ochrony aplikacji (APP). Aby uzyskać informacje na temat konfigurowania tej funkcji, zobacz [Tworzenie i przypisywanie zasad ochrony aplikacji w celu ustawienia poziomu ryzyka urządzenia](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level).

Dla wszystkich platform można ustawić poziom ryzyka w istniejących zasadach zgodności urządzeń. Zobacz [Tworzenie zasad dostępu warunkowego](/mem/intune/protect/advanced-threat-protection-configure#create-a-conditional-access-policy).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>Wdrażanie punktów odniesienia zabezpieczeń i monitorowanie zgodności w tych ustawieniach

Dotyczy: Windows 10, Windows 11

Artykuł [Krok 5. Wdrażanie profilów konfiguracji](manage-devices-with-intune-configuration-profiles.md) zaleca wprowadzenie do profilów konfiguracji przy użyciu punktów odniesienia zabezpieczeń dostępnych dla Windows 10 i Windows 11. Ochrona punktu końcowego w usłudze Microsoft Defender zawiera również punkty odniesienia zabezpieczeń, które zapewniają ustawienia optymalizujące wszystkie mechanizmy kontroli zabezpieczeń w stosie usługi Defender for Endpoint, w tym ustawienia wykrywanie i reagowanie w punktach końcowych (EDR) . Są one również wdrażane przy użyciu Microsoft Intune.

W idealnym przypadku urządzenia dołączone do usługi Defender for Endpoint są wdrażane w obu punktach odniesienia: Windows Intune punkt odniesienia zabezpieczeń w celu wstępnego zabezpieczenia Windows, a następnie punkt odniesienia zabezpieczeń usługi Defender for Endpoint ułożony warstwowo, aby optymalnie skonfigurować mechanizmy kontroli zabezpieczeń usługi Defender for Endpoint.

Aby korzystać z najnowszych danych dotyczących zagrożeń i zagrożeń oraz zminimalizować konflikty w miarę rozwoju linii bazowych, zawsze stosuj najnowsze wersje punktów odniesienia we wszystkich produktach natychmiast po ich wydaniu. 

Za pomocą usługi Defender for Endpoint można monitorować zgodność z tymi punktami odniesienia. 

![Karta do monitorowania zgodności z punktami odniesienia zabezpieczeń](../media/devices/secconmgmt-baseline-card.png#lightbox)

Aby wdrożyć punkty odniesienia zabezpieczeń i monitorować zgodność z tymi ustawieniami, wykonaj kroki opisane w tej tabeli.


|Krok  |Opis  |
|---------|---------|
|1     |Przejrzyj kluczowe pojęcia i porównaj Ochrona punktu końcowego w usłudze Microsoft Defender i Windows Intune punktów odniesienia zabezpieczeń. <br><br>Zobacz [Zwiększanie zgodności z punktem odniesienia zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender](../security/defender-endpoint/configure-machines-security-baseline.md), aby poznać zalecenia.<br><br>Zobacz [Używanie punktów odniesienia zabezpieczeń do konfigurowania urządzeń Windows w Intune](/mem/intune/protect/security-baselines), aby przejrzeć listę dostępnych punktów odniesienia zabezpieczeń i jak uniknąć konfliktów.         |
|2     |  Wdróż Windows ustawienia punktu odniesienia zabezpieczeń dla Intune. Być może udało Ci się to już osiągnąć, jeśli zostały wykonane wskazówki opisane w [kroku 5. Wdrażanie profilów konfiguracji](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  Wdróż ustawienia punktu odniesienia usługi Defender dla punktu końcowego dla Intune. Zobacz [Zarządzanie profilami punktów odniesienia zabezpieczeń w Microsoft Intune](/mem/intune/protect/security-baselines-configure), aby utworzyć profil i wybrać wersję punktu odniesienia.<br><br>Możesz również postępować zgodnie z instrukcjami w tym miejscu: [Przejrzyj i przypisz punkt odniesienia zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | W usłudze Defender for Endpoint przejrzyj [kartę Punkt odniesienia zabezpieczeń w zarządzaniu konfiguracją urządzenia](../security/defender-endpoint/configure-machines.md).          |


## <a name="next-steps"></a>Następne kroki
Przejdź do [kroku 7. Zaimplementuj DLP z funkcjami ochrony informacji w punktach końcowych](manage-devices-with-intune-dlp-mip.md).