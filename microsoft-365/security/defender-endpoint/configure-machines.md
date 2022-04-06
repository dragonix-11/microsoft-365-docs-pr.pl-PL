---
title: Upewnij się, że urządzenia są poprawnie skonfigurowane
description: Prawidłowo skonfiguruj urządzenia, aby zwiększyć ogólną odporność na zagrożenia i ulepszyć swoją funkcję wykrywania ataków i reagowania na nie.
keywords: onboard, Intune, Ochrona punktu końcowego w usłudze Microsoft Defender, Microsoft Defender, Windows Defender, zmniejszenie obszarów ataków, asr, plan bazowy zabezpieczeń
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 47c3cb5d680899a28e6467b24ef398a428851a07
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476164"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Upewnij się, że urządzenia są poprawnie skonfigurowane

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Dzięki prawidłowo skonfigurowanym urządzeniem można zwiększyć ogólną odporność na zagrożenia i ulepszyć swoją możliwość wykrywania ataków i reagowania na nie. Zarządzanie konfiguracją zabezpieczeń pozwala zagwarantować, że Twoje urządzenia:

- Dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender
- Poznaj lub przekroczenie konfiguracji planu bazowego zabezpieczeń programu Defender for Endpoint
- Posiadaj środki zaradcze strategiczne na powierzchni ataków

Kliknij **pozycję Zarządzanie konfiguracją** w menu nawigacji, aby otworzyć stronę Zarządzanie konfiguracją urządzeń.

:::image type="content" source="images/secconmgmt_main.png" alt-text="Strona Zarządzanie konfiguracją zabezpieczeń" lightbox="images/secconmgmt_main.png":::

*Strona zarządzania konfiguracją urządzeń*

Możesz śledzić stan konfiguracji na poziomie organizacji i szybko podjąć działania w reakcji na słabe usługi dołączania, problemy ze zgodnością i niskie zoptymalizowane środki zaradcze powierzchni ataków za pośrednictwem bezpośrednich, bezpośrednich linków do stron zarządzania urządzeniami w sieci Microsoft Intune i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu</a> Microsoft 365 Defender.

W ten sposób skorzystasz z:

- Kompleksowy wgląd w wydarzenia na Twoich urządzeniach
- Zaawansowana inteligencja przed zagrożeniami i zaawansowane technologie nauki dotyczące urządzeń do przetwarzania nieprzetworzonych zdarzeń oraz identyfikowania działań naruszenia i wskaźników zagrożeń
- Pełen stos funkcji zabezpieczeń skonfigurowanych w taki sposób, aby skutecznie zatrzymywać instalację złośliwych plików, chwytując pliki i proces systemowy, eksstruowanie danych i inne działania związane z zagrożeniami
- Optymalne środki zaradcze dla powierzchni ataków, maksymalizowanie obron strategicznych przed zagrożeniami przy jednoczesnym zminimalizowaniu wpływu na wydajność

## <a name="enroll-devices-to-intune-management"></a>Zarejestruj urządzenia do Intune zarządzania

Zarządzanie konfiguracją urządzeń ściśle współpracuje Intune zarządzanie urządzeniami w celu ustalenia spisu urządzeń w organizacji i podstawowej konfiguracji zabezpieczeń. Będzie można śledzić problemy z konfiguracją i zarządzać nimi na Intune zarządzanych Windows urządzeniach.

Zanim będzie można upewnić się, że urządzenia są poprawnie skonfigurowane, zarejestruj je w celu Intune zarządzaniem nimi. Intune jest niezawodna i ma kilka opcji rejestracji na Windows urządzeniach. Aby uzyskać więcej informacji na Intune rejestracji, przeczytaj o [konfigurowaniu rejestracji dla Windows urządzeniach](/intune/windows-enroll).

> [!NOTE]
> Aby można było Windows urządzenia do Intune, administratorzy muszą mieć już przypisane licencje. [Przeczytaj o przypisywaniu licencji na rejestrację urządzenia](/intune/licenses-assign).

> [!TIP]
> Aby zoptymalizować zarządzanie urządzeniami za pośrednictwem Intune, [połącz Intune z usługą Defender for Endpoint](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>Uzyskiwanie wymaganych uprawnień

Domyślnie tylko użytkownicy z przypisaną rolą administratora globalnego lub administratora usługi Intune w usłudze Azure AD mogą zarządzać profilami konfiguracji urządzeń potrzebnymi do dołączania urządzeń i przypisywać je oraz wdrażać plan bazowy zabezpieczeń.

Jeśli masz inne role, upewnij się, że masz odpowiednie uprawnienia:

- Pełne uprawnienia do konfiguracji urządzeń
- Pełne uprawnienia do planu bazowego zabezpieczeń
- Odczytywanie uprawnień do zasad zgodności urządzeń
- Uprawnienia do odczytu dla organizacji

:::image type="content" source="images/secconmgmt_intune_permissions.png" alt-text="Wymagane uprawnienia w usłudze Intune" lightbox="images/secconmgmt_intune_permissions.png":::

*Uprawnienia konfiguracji urządzenia na Intune*

> [!TIP]
> Aby dowiedzieć się więcej o przypisywaniu uprawnień do Intune, [przeczytaj o tworzeniu ról niestandardowych](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>W tej sekcji

Temat|Opis
:---|:---
[Pobierz urządzenia do usługi Defender dla punktu końcowego](configure-machines-onboarding.md)|Śledź stan dołączania Intune zarządzanych urządzeń i wdowaj więcej urządzeń za pośrednictwem Intune. 
[Zwiększanie zgodności z planem bazowym zabezpieczeń programu Defender for Endpoint](configure-machines-security-baseline.md)|Śledzenie zgodności i niezgodność planu bazowego. Wdrożenie planu bazowego zabezpieczeń na większej Intune urządzeniach zarządzanych.
[Optymalizowanie wdrażania reguł asr i wykrywanie](configure-machines-asr.md)|Przejrzyj wdrożenie reguł i dostosuj wykrywanie przy użyciu narzędzi do analizy wpływu w Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sieci.</a>

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
