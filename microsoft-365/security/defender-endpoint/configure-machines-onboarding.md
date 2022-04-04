---
title: Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender
description: Śledź dołączanie urządzeń zarządzanych Intune, aby Ochrona punktu końcowego w usłudze Microsoft Defender zwiększyć szybkość dołączania.
keywords: onboard, Intune, Ochrona punktu końcowego w usłudze Microsoft Defender, Microsoft Defender, Windows Defender, zarządzanie konfiguracją
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
ms.openlocfilehash: 6caaddc208e6f73de0f49ff6d419c335848ae439
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466328"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Każde urządzenie włoowane dodaje dodatkowy wykrywanie i reagowanie w punktach końcowych (EDR) i zwiększa widoczność działań naruszenia bezpieczeństwa w Twojej sieci. Ponadto w trakcie wbierania urządzenia można sprawdzać, czy są na nie narażone składniki, a także czy nie są one związane z konfiguracją zabezpieczeń, a podczas ataków mogą być podejmowane krytyczne działania naprawcze.

Zanim będzie można śledzić dołączanie urządzeń i zarządzać nimi:

- [Rejestrowanie urządzeń w celu Intune zarządzania](configure-machines.md#enroll-devices-to-intune-management)
- [Upewnij się, że masz niezbędne uprawnienia](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>Odnajdowanie i śledzenie urządzeń niechronionych

Karta **wnoszona** udostępnia ogólne informacje o tempie dołączania do programu, porównując liczbę urządzeń Windows, które w rzeczywistości zostały podłączone do usługi Defender for Endpoint, z całkowitą liczbą urządzeń Intune zarządzanych Windows końcowych.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Karta dołączania do zarządzania konfiguracją urządzeń" lightbox="images/secconmgmt_onboarding_card.png":::

*Karta przedstawiająca urządzenia podłączone do urządzenia w porównaniu z całkowitą liczbą urządzeń Intune zarządzanych Windows urządzeniach*

> [!NOTE]
> W przypadku użycia Configuration Manager, skryptu dołączania lub innych metod dołączania, które nie korzystają z profilów Intune, może wystąpić rozbieżność danych. Aby rozwiązać te niezgodności, utwórz odpowiedni profil Intune konfiguracji programu Defender dla dołączania do punktu końcowego i przypisz ten profil do swoich urządzeń.

## <a name="onboard-more-devices-with-intune-profiles"></a>Więcej urządzeń z Intune profilami

Program Defender for Endpoint udostępnia kilka wygodnych opcji [dołączania Windows urządzeniach](onboard-configure.md). W Intune zarządzanych przez ciebie urządzeń możesz jednak wykorzystać profile usługi Intune, aby wygodnie wdrożyć czujnik Defender for Endpoint do wybierania urządzeń w celu efektywnego wdrażania tych urządzeń do usługi.

Na karcie **Dołączanie wybierz** pozycję Na **ekranie Więcej** urządzeń, aby utworzyć i przypisać profil na Intune. Link umożliwia dostęp do strony zgodności urządzenia w Intune, która przedstawia podobny przegląd stanu dołączania.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Strona Ochrona punktu końcowego w usłudze Microsoft Defender zgodności urządzeń w Intune zarządzania urządzeniami" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Ochrona punktu końcowego w usłudze Microsoft Defender stronie zgodności urządzeń na Intune zarządzanie urządzeniami*

> [!TIP]
> Możesz również przejść do strony zgodności przy dołączaniu do programu Defender for Endpoint w [portalu Microsoft Azure](https://portal.azure.com/) z witryny Wszystkie usługi **> Intune > Zgodność urządzenia > Microsoft Defender ATP**.

> [!NOTE]
> Jeśli chcesz wyświetlić najbardziej aktualne dane urządzenia, kliknij pozycję **Lista urządzeń bez czujnika ATP**.

Na stronie zgodności urządzenia utwórz profil konfiguracji przeznaczony specjalnie do wdrożenia czujnika Defender for Endpoint i przypisz ten profil do urządzeń, które chcesz dodać. W tym celu możesz wykonać jedną z tych:

- Wybierz **pozycję Utwórz profil konfiguracji urządzenia, aby skonfigurować czujnik ATP** , aby zaczynał się od wstępnie zdefiniowanego profilu konfiguracji urządzenia.
- Utwórz profil konfiguracji urządzenia od podstaw.

Aby uzyskać więcej informacji, [przeczytaj o używaniu profilów Intune konfiguracji urządzeń w celu korzystania z urządzeń w programie Defender for Endpoint](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Upewnij się, że urządzenia są poprawnie skonfigurowane](configure-machines.md)
- [Zwiększanie zgodności z planem bazowym zabezpieczeń programu Defender for Endpoint](configure-machines-security-baseline.md)
- [Optymalizowanie wdrażania reguł asr i wykrywanie](configure-machines-asr.md)
