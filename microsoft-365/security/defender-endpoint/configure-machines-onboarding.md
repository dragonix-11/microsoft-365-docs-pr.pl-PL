---
title: Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender
description: Śledzenie dołączania urządzeń zarządzanych przez Intune w celu Ochrona punktu końcowego w usłudze Microsoft Defender i zwiększenia szybkości dołączania.
keywords: dołączanie, zarządzanie Intune, Ochrona punktu końcowego w usłudze Microsoft Defender, Microsoft Defender, Windows Defender, zarządzanie konfiguracją
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1e77f404b70ee770bd4d5c441362739cc7b2f13c
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622952"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Każde dołączone urządzenie dodaje dodatkowy czujnik wykrywanie i reagowanie w punktach końcowych (EDR) i zwiększa widoczność działań polegających na naruszeniu zabezpieczeń w sieci. Dołączanie gwarantuje również, że urządzenie może być sprawdzane pod kątem składników narażonych na zagrożenia, a także problemów z konfiguracją zabezpieczeń i może odbierać krytyczne akcje korygowania podczas ataków.

Przed rozpoczęciem śledzenia dołączania urządzeń i zarządzania nimi:

- [Rejestrowanie urządzeń w celu zarządzania Intune](configure-machines.md#enroll-devices-to-intune-management)
- [Upewnij się, że masz niezbędne uprawnienia](configure-machines.md#obtain-required-permissions)

Obejrzyj ten film wideo, aby dowiedzieć się, jak łatwo dołączać klientów za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4bGqr?rel=0]

## <a name="discover-and-track-unprotected-devices"></a>Odnajdywanie i śledzenie niechronionych urządzeń

Karta **dołączania** zapewnia ogólny przegląd szybkości dołączania przez porównanie liczby urządzeń Windows, które zostały faktycznie dołączone do usługi Defender for Endpoint, z łączną liczbą urządzeń zarządzanych Intune Windows.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Karta Dołączanie zarządzania konfiguracją urządzenia" lightbox="images/secconmgmt_onboarding_card.png":::

*Karta przedstawiająca dołączone urządzenia w porównaniu z całkowitą liczbą urządzeń Windows zarządzanych przez Intune*

> [!NOTE]
> Jeśli użyto Configuration Manager, skryptu dołączania lub innych metod dołączania, które nie używają profilów Intune, mogą wystąpić rozbieżności danych. Aby rozwiązać te rozbieżności, utwórz odpowiedni profil konfiguracji Intune dla dołączania usługi Defender for Endpoint i przypisz ten profil do urządzeń.

## <a name="onboard-more-devices-with-intune-profiles"></a>Dołączanie większej liczby urządzeń z profilami Intune

Usługa Defender for Endpoint oferuje kilka wygodnych opcji [dołączania urządzeń Windows](onboard-configure.md). Jednak w przypadku urządzeń zarządzanych przez Intune można wykorzystać profile Intune, aby wygodnie wdrożyć czujnik punktu końcowego usługi Defender for Endpoint, aby wybrać urządzenia, skutecznie dołączając te urządzenia do usługi.

Na **karcie Dołączanie** wybierz pozycję **Dołącz więcej urządzeń**, aby utworzyć i przypisać profil na Intune. Link prowadzi do strony zgodności urządzenia w Intune, która zawiera podobne omówienie stanu dołączania.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Strona zgodności urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender w Intune zarządzania urządzeniami" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Ochrona punktu końcowego w usłudze Microsoft Defender stronę zgodności urządzeń w Intune zarządzania urządzeniami*

> [!TIP]
> Alternatywnie możesz przejść do strony zgodności dołączania punktu końcowego usługi Defender w [portalu Microsoft Azure](https://portal.azure.com/) z witryny **Wszystkie usługi > Intune > Zgodność urządzeń > microsoft Defender ATP**.

> [!NOTE]
> Jeśli chcesz wyświetlić najbardziej aktualne dane urządzenia, kliknij pozycję **Lista urządzeń bez czujnika ATP**.

Na stronie zgodności urządzenia utwórz profil konfiguracji przeznaczony specjalnie do wdrożenia czujnika defender for Endpoint i przypisz ten profil do urządzeń, które chcesz dołączyć. W tym celu możesz wykonać następujące czynności:

- Wybierz **pozycję Utwórz profil konfiguracji urządzenia, aby skonfigurować czujnik atp** , aby rozpocząć od wstępnie zdefiniowanego profilu konfiguracji urządzenia.
- Utwórz profil konfiguracji urządzenia od podstaw.

Aby uzyskać więcej informacji, [przeczytaj o używaniu Intune profilów konfiguracji urządzeń do dołączania urządzeń do usługi Defender for Endpoint](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Upewnij się, że urządzenia są prawidłowo skonfigurowane](configure-machines.md)
- [Zwiększanie zgodności z punktem odniesienia zabezpieczeń usługi Defender for Endpoint](configure-machines-security-baseline.md)
- [Optymalizowanie wdrażania i wykrywania reguł usługi ASR](configure-machines-asr.md)
