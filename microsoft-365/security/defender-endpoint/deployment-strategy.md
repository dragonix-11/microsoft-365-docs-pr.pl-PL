---
title: Planowanie wdrożenia programu Microsoft Defender dla punktu końcowego
description: Wybieranie najlepszej strategii wdrażania programu Microsoft Defender dla punktu końcowego dla Twojego środowiska
keywords: wdrażanie, plan, strategia wdrażania, natywny chmura, zarządzanie, na temat prem, evaluation, onboarding, local, group policy, gp, endpoint manager, mem
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
ms.openlocfilehash: cfdbb84cfcc2cda08572709adb3b13db83e319fa
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011401"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planowanie wdrożenia programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Zaplanuj wdrożenie programu Microsoft Defender for Endpoint, aby zmaksymalizować możliwości zabezpieczeń w ramach pakietu i lepiej chronić przedsiębiorstwa przed zagrożeniami cyberzagrożeniami.

To rozwiązanie zawiera wskazówki dotyczące identyfikowania architektury środowiska, wybierania typu narzędzia wdrażania najlepiej dopasowanego do Twoich potrzeb, a także wskazówki dotyczące konfigurowania możliwości.

![Obraz przepływu wdrażania.](images/deployment-guide-plan.png)

## <a name="step-1-identify-architecture"></a>Krok 1. Identyfikowanie architektury

Rozumiemy, że każde środowisko przedsiębiorstwa jest unikatowe, dlatego podaliśmy kilka opcji, aby zapewnić elastyczność w zakresie wyboru sposobu wdrażania usługi.

W zależności od środowiska niektóre narzędzia lepiej nadają się do określonych architektur.

Użyj następującego materiału, aby wybrać odpowiednią architekturę programu Defender for Endpoint, która najlepiej będzie odpowiedni dla Twojej organizacji.

| Element | Opis |
|:-----|:-----|
|[![Obraz kciuka dla strategii wdrażania programu Defender for Endpoint.](images/mde-deployment-strategy.png)](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Materiał architektoniczny ułatwia zaplanowanie wdrożenia z następującymi architekturami: <ul><li> Natywne w chmurze </li><li> Współzawłasnie </li><li> Lokalne</li><li>Oceny i lokalne dołączanie</li>

## <a name="step-2-select-deployment-method"></a>Krok 2. Wybieranie metody wdrażania

| Punkt końcowy     | Narzędzie wdrażania                       |
|--------------|------------------------------------------|
| **Windows**  |  [Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md) <br>  [zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Menedżer urządzeń przenośnych](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z usługą Microsoft Defender dla chmury](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Skrypt lokalny](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Jamf Pro](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami przenośnymi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Skrypt lokalny](linux-install-manually.md) <br> [Wytłaczenie](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

W poniższej tabeli wymieniono obsługiwane punkty końcowe i odpowiadające im narzędzie wdrażania, których można użyć, aby można było odpowiednio zaplanować wdrożenie.

|Punkt końcowy|Narzędzie wdrażania|
|---|---|
|**Windows**|[Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md) <br>  [zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Menedżer urządzeń przenośnych](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z usługą Microsoft Defender dla chmury](configure-server-endpoints.md#integration-with-azure-defender)|
|**macOS**|[Skrypt lokalny](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Jamf Pro](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami przenośnymi](mac-install-with-other-mdm.md)|
|**Linux Server**|[Skrypt lokalny](linux-install-manually.md) <br> [Wytłaczenie](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Oparte na aplikacji](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>Krok 3. Konfigurowanie funkcji

Po wstrzemieniu punktów końcowych skonfiguruj funkcje zabezpieczeń w programie Defender for Endpoint, aby zmaksymalizować niezawodną ochronę zabezpieczeń dostępną w pakiecie. Dostępne możliwości:

- Wykrywanie punktu końcowego i odpowiedź
- Ochrona następnej generacji
- Zmniejszenie powierzchni ataków

## <a name="related-topics"></a>Tematy pokrewne

- [Fazy wdrażania](deployment-phases.md)
