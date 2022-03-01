---
title: Zwiększanie zgodności z planem bazowym zabezpieczeń programu Microsoft Defender for Endpoint
description: Plan bazowy zabezpieczeń programu Microsoft Defender for Endpoint określa mechanizmy kontroli zabezpieczeń w celu zapewnienia optymalnej ochrony.
keywords: Zarządzanie usługą Intune, usługa Microsoft Defender for Endpoint, Microsoft Defender, Microsoft Defender for Endpoint ASR, plan bazowy zabezpieczeń
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
ms.openlocfilehash: 95790626461d7db02f3837321e0d9075e0597515
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998102"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Zwiększanie zgodności z planem bazowym zabezpieczeń programu Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Plan bazowy zabezpieczeń zapewnia, że funkcje zabezpieczeń są skonfigurowane zgodnie z wytycznymi ekspertów ds. zabezpieczeń i ekspertów Windows administratorów systemu. Po wdrożeniu program Defender for Endpoint security baseline ustawia program Defender dla kontroli zabezpieczeń punktu końcowego w celu zapewnienia optymalnej ochrony.

Aby poznać linie bazowe zabezpieczeń i sposób ich przypisywania w usłudze Intune przy użyciu profilów konfiguracji, [przeczytaj te często zadawane pytania](/intune/security-baselines#q--a).

Zanim będzie można wdrożyć i śledzić zgodność z planami bazowymi zabezpieczeń:

- [Rejestrowanie urządzeń w zarządzaniu usługą Intune](configure-machines.md#enroll-devices-to-intune-management)
- [Upewnij się, że masz niezbędne uprawnienia](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Porównanie programu Microsoft Defender dla punktu końcowego i podstawowych Windows zabezpieczeń usługi Intune

Plan bazowy usługi Windows Intune zapewnia kompleksowy zestaw zalecanych ustawień wymaganych do bezpiecznego skonfigurowania urządzeń z systemem Windows, w tym ustawień przeglądarki, ustawień programu PowerShell i ustawień niektórych funkcji zabezpieczeń, takich jak Program antywirusowy Microsoft Defender. Natomiast plan bazowy usługi Defender for Endpoint zawiera ustawienia, które optymalizują wszystkie kontrolki zabezpieczeń w usłudze Defender pod kątem stosu punktów końcowych, w tym ustawienia dla programu wykrywanie i reagowanie w punktach końcowych (EDR), a także ustawienia w planie bazowym zabezpieczeń usługi Windows Intune. Aby uzyskać więcej informacji o poszczególnych planach bazowych, zobacz:

- [Windows podstawowych ustawień zabezpieczeń dla usługi Intune](/intune/security-baseline-settings-windows)
- [Ustawienia linii bazowej programu Microsoft Defender dla punktu końcowego dla usługi Intune](/intune/security-baseline-settings-defender-atp)

Najlepiej jest wtedy, gdy urządzenia wdrożone w usłudze Defender for Endpoint są wdrożone według planu bazowego: plan bazowy zabezpieczeń usługi Windows Intune, który wstępnie zabezpiecza program Windows, a następnie usługa Defender for Endpoint security baseline jest wdrożona w warstwie u góry w celu optymalnego skonfigurowania programu Defender pod względem zabezpieczeń punktu końcowego. Aby korzystać z najnowszych danych na temat zagrożeń i czynników ryzyka oraz minimalizować konflikty w przypadku rozwoju planu bazowego, zawsze zastosuj najnowsze wersje linii bazowych we wszystkich produktach zaraz po ich ich zastosowaniu.

> [!NOTE]
> Plan bazowy zabezpieczeń programu Defender for Endpoint został zoptymalizowany pod kątem urządzeń fizycznych i nie jest obecnie zalecany do używania na wirtualnych maszyn wirtualnych (VM) ani w punktach końcowych VDI. Niektóre ustawienia planu bazowego mogą mieć wpływ na zdalne sesje interakcyjne w środowiskach zwirtualizowanych.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Monitorowanie zgodności z planem bazowym zabezpieczeń programu Defender for Endpoint

Karta **Plan bazowy** zabezpieczeń w [](configure-machines.md) zarządzaniu konfiguracją urządzenia zawiera przegląd zgodności na wszystkich Windows 10 i Windows 11 urządzeń, do których przypisano plan bazowy zabezpieczeń Defender for Endpoint.

![Karta planu bazowego zabezpieczeń.](images/secconmgmt_baseline_card.png)

*Karta przedstawiająca zgodność z planem bazowym zabezpieczeń programu Defender for Endpoint*

Na każdym urządzeniu jest podawany jeden z następujących typów stanu:

- **Pasuje do planu** bazowego: Ustawienia urządzenia są zgodne ze wszystkimi ustawieniami na linii bazowej.
- **Nie jest zgodne z planem bazowym**: Co najmniej jedno ustawienie urządzenia nie jest zgodne z planem bazowym.
- **Nieprawidłowo skonfigurowane**: Co najmniej jedno ustawienie planu bazowego nie jest poprawnie skonfigurowane na urządzeniu i występuje konflikt, błąd lub stan oczekiwania.
- **Nie dotyczy**: Na urządzeniu nie ma zastosowania co najmniej jedno ustawienie linii bazowej.

Aby przejrzeć określone urządzenia, wybierz **pozycję Konfiguruj plan bazowy zabezpieczeń** na karcie. Umożliwia to zarządzanie urządzeniami w usłudze Intune. W tym miejscu wybierz **pozycję Stan** urządzenia, aby sprawdzić nazwy i statusy urządzeń.

> [!NOTE]
> Rozbieżność może wystąpić w przypadku zagregowanych danych wyświetlanych na stronie zarządzania konfiguracją urządzenia oraz na ekranach przeglądu w usłudze Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Przeglądanie i przypisywanie planu bazowego zabezpieczeń programu Microsoft Defender for Endpoint

Zarządzanie konfiguracją urządzeń monitoruje podstawową zgodność tylko Windows 10 i Windows 11 urządzeń, do których przypisano plan bazowy zabezpieczeń programu Microsoft Defender for Endpoint. Możesz w wygodny sposób przejrzeć plan bazowy i przypisać go do urządzeń w usłudze Zarządzania urządzeniami w usłudze Intune.

1. Wybierz **pozycję Konfiguruj plan bazowy zabezpieczeń** na **karcie Plan bazowy zabezpieczeń** , aby przejść do opcji Zarządzanie urządzeniami w usłudze Intune. Podobny przegląd zgodności bazowej jest wyświetlany.

   > [!TIP]
   > Możesz również przejść do planu bazowego zabezpieczeń programu Defender for Endpoint w portalu usługi Microsoft Azure z witryny Wszystkie usługi **> Intune > Zabezpieczenia urządzeń >** Plan bazowy zabezpieczeń > Plan bazowy programu Microsoft Defender ATP.

2. Utwórz nowy profil.

   ![Omówienie planu bazowego zabezpieczeń programu Microsoft Defender for Endpoint w usłudze Intune.](images/secconmgmt_baseline_intuneprofile1.png)<br>
   *Omówienie planu bazowego zabezpieczeń programu Microsoft Defender for Endpoint w usłudze Intune*

3. Podczas tworzenia profilu możesz przeglądać i dostosowywać określone ustawienia dla planu bazowego.

   ![Opcje planu bazowego zabezpieczeń podczas tworzenia profilu w usłudze Intune.](images/secconmgmt_baseline_intuneprofile2.png)<br>
   *Opcje planu bazowego zabezpieczeń podczas tworzenia profilu w usłudze Intune*

4. Przypisz profil do odpowiedniej grupy urządzeń.

   ![Profile bazowe zabezpieczeń w usłudze Intune.](images/secconmgmt_baseline_intuneprofile3.png)<br>
   *Przypisywanie profilu planu bazowego zabezpieczeń w usłudze Intune*

5. Utwórz profil, aby go zapisać i wdrożyć w przypisanej grupie urządzeń.

   ![Przypisywanie planu bazowego zabezpieczeń w usłudze Intune.](images/secconmgmt_baseline_intuneprofile4.png)<br>
   *Tworzenie profilu planu bazowego zabezpieczeń w usłudze Intune*

> [!TIP]
> Linie bazowe zabezpieczeń w usłudze Intune zapewniają wygodny sposób bezpiecznego i bezpiecznego korzystania z urządzeń. [Dowiedz się więcej o planach bazowych zabezpieczeń w usłudze Intune](/intune/security-baselines).

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Upewnij się, że urządzenia są poprawnie skonfigurowane](configure-machines.md)
- [Uzyskiwanie urządzeń podłączonych do programu Microsoft Defender dla punktu końcowego](configure-machines-onboarding.md)
- [Optymalizowanie wdrażania reguł asr i wykrywanie](configure-machines-asr.md)
