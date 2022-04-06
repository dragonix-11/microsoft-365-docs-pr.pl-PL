---
title: Zwiększanie zgodności z planem bazowym Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń
description: Podstawowa Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń określa mechanizmy kontroli zabezpieczeń w celu zapewnienia optymalnej ochrony.
keywords: Intune zarządzanie zabezpieczeniami, Ochrona punktu końcowego w usłudze Microsoft Defender, Program Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender asr, plan bazowy zabezpieczeń
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
ms.openlocfilehash: 1980567c93364f35923a9a7f2433733e05878e61
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467978"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Zwiększanie zgodności z planem bazowym Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Plan bazowy zabezpieczeń zapewnia, że funkcje zabezpieczeń są skonfigurowane zgodnie z wytycznymi ekspertów ds. zabezpieczeń i ekspertów Windows administratorów systemu. Po wdrożeniu program Defender for Endpoint security baseline ustawia program Defender dla kontroli zabezpieczeń punktu końcowego w celu zapewnienia optymalnej ochrony.

Aby poznać linie bazowe zabezpieczeń i sposób ich przypisywania Intune profilów konfiguracji, [przeczytaj te często zadawane pytania](/intune/security-baselines#q--a).

Zanim będzie można wdrożyć i śledzić zgodność z planami bazowymi zabezpieczeń:

- [Rejestrowanie urządzeń w celu Intune zarządzania](configure-machines.md#enroll-devices-to-intune-management)
- [Upewnij się, że masz niezbędne uprawnienia](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Porównanie Ochrona punktu końcowego w usłudze Microsoft Defender i podstawowych Windows Intune zabezpieczeń

Plan bazowy Windows Intune zabezpieczeń udostępnia kompleksowy zestaw zalecanych ustawień wymaganych do bezpiecznego konfigurowania urządzeń z systemem Windows, w tym ustawień przeglądarki, ustawień programu PowerShell i ustawień niektórych funkcji zabezpieczeń, takich jak Program antywirusowy Microsoft Defender. Natomiast plan bazowy usługi Defender dla punktu końcowego zawiera ustawienia, które optymalizują wszystkie kontrolki zabezpieczeń w stosie programu Defender dla punktu końcowego, w tym ustawienia dla programu wykrywanie i reagowanie w punktach końcowych (EDR), a także ustawienia w planie bazowym zabezpieczeń programu Windows Intune. Aby uzyskać więcej informacji o poszczególnych planach bazowych, zobacz:

- [Windows podstawowych ustawień zabezpieczeń dla Intune](/intune/security-baseline-settings-windows)
- [Ochrona punktu końcowego w usłudze Microsoft Defender planu bazowego dla Intune](/intune/security-baseline-settings-defender-atp)

Najlepiej jest wtedy, gdy urządzenia w programie Defender dla punktu końcowego są wdrożone według planu bazowego: planu bazowego zabezpieczeń programu Windows Intune, który wstępnie zabezpiecza program Windows, a następnie usługi Defender for Endpoint security baseline w warstwie u góry w celu optymalnego skonfigurowania programu Defender pod względem kontroli zabezpieczeń punktu końcowego. Aby korzystać z najnowszych danych na temat zagrożeń i czynników ryzyka oraz minimalizować konflikty w przypadku rozwoju planu bazowego, zawsze zastosuj najnowsze wersje linii bazowych we wszystkich produktach zaraz po ich ich zastosowaniu.

> [!NOTE]
> Plan bazowy zabezpieczeń programu Defender for Endpoint został zoptymalizowany pod kątem urządzeń fizycznych i nie jest obecnie zalecany do używania na wirtualnych maszyn wirtualnych (VM) ani w punktach końcowych VDI. Niektóre ustawienia planu bazowego mogą mieć wpływ na zdalne sesje interakcyjne w środowiskach zwirtualizowanych.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Monitorowanie zgodności z planem bazowym zabezpieczeń programu Defender for Endpoint

Karta **Planu bazowego zabezpieczeń** w [](configure-machines.md) zarządzaniu konfiguracją urządzenia zawiera przegląd zgodności na wszystkich Windows 10 i Windows 11, do których przypisano plan bazowy zabezpieczeń Programu Defender for Endpoint.

:::image type="content" source="images/secconmgmt_baseline_card.png" alt-text="Karta Planu bazowego zabezpieczeń" lightbox="images/secconmgmt_baseline_card.png":::

*Karta przedstawiająca zgodność z planem bazowym zabezpieczeń programu Defender for Endpoint*

Na każdym urządzeniu jest podawany jeden z następujących typów stanu:

- **Pasuje do planu** bazowego: Ustawienia urządzenia są zgodne ze wszystkimi ustawieniami na linii bazowej.
- **Nie jest zgodne z planem bazowym**: Co najmniej jedno ustawienie urządzenia nie jest zgodne z planem bazowym.
- **Nieprawidłowo skonfigurowane**: Co najmniej jedno ustawienie planu bazowego nie jest poprawnie skonfigurowane na urządzeniu i występuje konflikt, błąd lub stan oczekiwania.
- **Nie dotyczy**: Na urządzeniu nie ma zastosowania co najmniej jedno ustawienie linii bazowej.

Aby przejrzeć określone urządzenia, wybierz **pozycję Konfiguruj plan bazowy zabezpieczeń** na karcie. W ten sposób możesz Intune zarządzanie urządzeniami. W tym miejscu wybierz **pozycję Stan** urządzenia, aby sprawdzić nazwy i statusy urządzeń.

> [!NOTE]
> Rozbieżność danych zagregowanych może być wyświetlanych na stronie zarządzania konfiguracją urządzenia oraz na ekranach przeglądu w Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Przeglądanie i przypisywanie planu Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń

Zarządzanie konfiguracją urządzeń monitoruje podstawową zgodność tylko Windows 10 i Windows 11, które zostały specjalnie przypisane do Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń. Możesz wygodnie przeglądać plan bazowy i przypisywać go do urządzeń w Intune zarządzanie urządzeniami.

1. Wybierz **pozycję Konfiguruj plan bazowy zabezpieczeń** na **karcie Plan bazowy** zabezpieczeń, aby przejść Intune zarządzanie urządzeniami. Podobny przegląd zgodności bazowej jest wyświetlany.

   > [!TIP]
   > Możesz również przejść do planu bazowego zabezpieczeń programu Defender for Endpoint w portalu Microsoft Azure z poziomu strony Wszystkie usługi > Intune > Zabezpieczenia urządzeń **> Security baselines > Microsoft Defender ATP baseline**.

2. Utwórz nowy profil.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile1.png" alt-text="Karta Tworzenie profilu w przeglądzie planu bazowego Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń na karcie Intune" lightbox="images/secconmgmt_baseline_intuneprofile1.png":::<br>
   *Ochrona punktu końcowego w usłudze Microsoft Defender planu bazowego zabezpieczeń na Intune*

3. Podczas tworzenia profilu możesz przeglądać i dostosowywać określone ustawienia dla planu bazowego.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile2.png" alt-text="Opcje linii bazowej zabezpieczeń podczas tworzenia profilu w Intune" lightbox="images/secconmgmt_baseline_intuneprofile2.png":::<br>
   *Opcje planu bazowego zabezpieczeń podczas tworzenia profilu w Intune*

4. Przypisz profil do odpowiedniej grupy urządzeń.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile3.png" alt-text="Profile bazowe zabezpieczeń w u Intune" lightbox="images/secconmgmt_baseline_intuneprofile3.png":::<br>
   *Przypisywanie profilu planu bazowego zabezpieczeń na stronie Intune*

5. Utwórz profil, aby go zapisać i wdrożyć w przypisanej grupie urządzeń.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile4.png" alt-text="Przypisywanie planu bazowego zabezpieczeń na Intune" lightbox="images/secconmgmt_baseline_intuneprofile4.png":::<br>
   *Tworzenie profilu planu bazowego zabezpieczeń na Intune*

> [!TIP]
> Linie bazowe zabezpieczeń na Intune to wygodny sposób na pełne zabezpieczanie i ochronę urządzeń. [Dowiedz się więcej o planach bazowych zabezpieczeń na Intune](/intune/security-baselines).

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Upewnij się, że urządzenia są poprawnie skonfigurowane](configure-machines.md)
- [Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender](configure-machines-onboarding.md)
- [Optymalizowanie wdrażania reguł asr i wykrywanie](configure-machines-asr.md)
