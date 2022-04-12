---
title: Planowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender
description: Wybierz najlepszą strategię wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender dla swojego środowiska
keywords: deploy, plan, deployment strategy, cloud native, management, on prem, evaluation, onboarding, local, group policy, gp, endpoint manager, mem
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 63996aa4d046ac719e0e6b98ed4c5980e0d979be
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783870"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Zaplanuj wdrożenie Ochrona punktu końcowego w usłudze Microsoft Defender, aby zmaksymalizować możliwości zabezpieczeń w pakiecie i lepiej chronić przedsiębiorstwo przed zagrożeniami cybernetycznymi.

To rozwiązanie zawiera wskazówki dotyczące identyfikowania architektury środowiska, wybierania typu narzędzia wdrażania, które najlepiej odpowiada Twoim potrzebom, oraz wskazówki dotyczące sposobu konfigurowania możliwości.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="Przepływ wdrażania" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>Krok 1. Identyfikowanie architektury

Rozumiemy, że każde środowisko przedsiębiorstwa jest unikatowe, dlatego udostępniliśmy kilka opcji zapewniających elastyczność wyboru sposobu wdrażania usługi.

W zależności od środowiska niektóre narzędzia są lepiej dostosowane do niektórych architektur.

Użyj poniższego materiału, aby wybrać odpowiednią architekturę usługi Defender for Endpoint, która najlepiej odpowiada Twojej organizacji.

| Element | Opis |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Strategia wdrażania usługi Defender for Endpoint" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Materiał architektoniczny pomaga zaplanować wdrożenie dla następujących architektur: <ul><li> Natywny dla chmury </li><li> Współzarządzanie </li><li> Lokalnie</li><li>Ocena i dołączanie lokalne</li>

## <a name="step-2-select-deployment-method"></a>Krok 2. Wybieranie metody wdrażania

| Punkt końcowy     | Narzędzie do wdrażania                       |
|--------------|------------------------------------------|
| **Windows**  |  [Skrypt lokalny (maksymalnie 10 urządzeń)](configure-endpoints-script.md) <br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile Menedżer urządzeń](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z Microsoft Defender dla Chmury](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **macOS**    | [Skrypt lokalny](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Pro JAMF](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami mobilne](mac-install-with-other-mdm.md) |
| **Serwer z systemem Linux** | [Skrypt lokalny](linux-install-manually.md) <br> [Lalek](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

W poniższej tabeli wymieniono obsługiwane punkty końcowe i odpowiednie narzędzie wdrażania, którego można użyć, aby można było odpowiednio zaplanować wdrożenie.

|Punkt końcowy|Narzędzie do wdrażania|
|---|---|
|**Windows**|[Skrypt lokalny (maksymalnie 10 urządzeń)](configure-endpoints-script.md) <br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile Menedżer urządzeń](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z Microsoft Defender dla Chmury](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**macOS**|[Skrypt lokalny](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Pro JAMF](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami mobilne](mac-install-with-other-mdm.md)|
|**Serwer z systemem Linux**|[Skrypt lokalny](linux-install-manually.md) <br> [Lalek](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Oparte na aplikacji](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>Krok 3. Konfigurowanie możliwości

Po dołączeniu punktów końcowych skonfiguruj możliwości zabezpieczeń w usłudze Defender for Endpoint, aby zmaksymalizować niezawodną ochronę zabezpieczeń dostępną w pakiecie. Możliwości obejmują:

- Wykrywanie i reagowanie dotyczące punktów końcowych
- Ochrona nowej generacji
- Zmniejszanie obszaru podatnego na ataki

## <a name="related-topics"></a>Tematy pokrewne

- [Fazy wdrażania](deployment-phases.md)
