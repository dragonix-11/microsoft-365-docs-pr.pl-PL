---
title: Upewnij się, że urządzenia są poprawnie skonfigurowane
description: Prawidłowo skonfiguruj urządzenia, aby zwiększyć ogólną odporność na zagrożenia i ulepszyć swoją funkcję wykrywania ataków i reagowania na nie.
keywords: onboard, zarządzanie usługą Intune, program Microsoft Defender dla punktu końcowego, program Microsoft Defender, Windows Defender, zmniejszenie obszarów ataków, asr, plan bazowy zabezpieczeń
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
ms.openlocfilehash: 61b275e5e42a10743eee744ab44bce48a25fa2eb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998103"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Upewnij się, że urządzenia są poprawnie skonfigurowane

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Dzięki prawidłowo skonfigurowanym urządzeniem można zwiększyć ogólną odporność na zagrożenia i ulepszyć swoją możliwość wykrywania ataków i reagowania na nie. Zarządzanie konfiguracją zabezpieczeń pozwala zagwarantować, że Twoje urządzenia:

- Dołączanie do programu Microsoft Defender dla punktu końcowego
- Poznaj lub przekroczenie konfiguracji planu bazowego zabezpieczeń programu Defender for Endpoint
- Posiadaj środki zaradcze strategiczne na powierzchni ataków

Kliknij **pozycję Zarządzanie konfiguracją** w menu nawigacji, aby otworzyć stronę Zarządzanie konfiguracją urządzeń.

![Stronie zarządzania konfiguracją zabezpieczeń.](images/secconmgmt_main.png)

*Strona zarządzania konfiguracją urządzeń*

Możesz śledzić stan konfiguracji na poziomie organizacji i szybko podjąć działania w reakcji na słabe usługi dołączania, problemy ze zgodnością i niskie zoptymalizowane środki zaradcze powierzchni ataków za pośrednictwem bezpośrednich, bezpośrednich linków do stron zarządzania urządzeniami w sieci Microsoft Intune i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu</a> Microsoft 365 Defender.

W ten sposób skorzystasz z:

- Kompleksowy wgląd w wydarzenia na Twoich urządzeniach
- Zaawansowana inteligencja przed zagrożeniami i zaawansowane technologie nauki dotyczące urządzeń do przetwarzania nieprzetworzonych zdarzeń oraz identyfikowania działań naruszenia i wskaźników zagrożeń
- Pełen stos funkcji zabezpieczeń skonfigurowanych w taki sposób, aby skutecznie zatrzymywać instalację złośliwych plików, chwytując pliki i proces systemowy, eksstruowanie danych i inne działania związane z zagrożeniami
- Optymalne środki zaradcze dla powierzchni ataków, maksymalizowanie obron strategicznych przed zagrożeniami przy jednoczesnym zminimalizowaniu wpływu na wydajność

## <a name="enroll-devices-to-intune-management"></a>Rejestrowanie urządzeń do zarządzania usługą Intune

Zarządzanie konfiguracją urządzeń ściśle współpracuje z zarządzaniem urządzeniami w usłudze Intune w celu ustalenia spisu urządzeń w organizacji i podstawowej konfiguracji zabezpieczeń. Będzie można śledzić problemy z konfiguracją na urządzeniach zarządzanych w Windows Intune oraz zarządzać nimi.

Zanim będzie można upewnić się, że urządzenia są poprawnie skonfigurowane, zarejestruj je w usłudze zarządzania usługą Intune. Rejestracja w usłudze Intune jest niezawodna i ma kilka opcji rejestracji na Windows urządzenia. Aby uzyskać więcej informacji o opcjach rejestracji w usłudze Intune, przeczytaj o [konfigurowaniu rejestracji Windows urządzeniach](/intune/windows-enroll).

> [!NOTE]
> Aby można było Windows urządzenia w usłudze Intune, administratorzy muszą mieć już przypisane licencje. [Przeczytaj o przypisywaniu licencji na rejestrację urządzenia](/intune/licenses-assign).

> [!TIP]
> Aby zoptymalizować zarządzanie urządzeniami za pomocą usługi Intune, [połącz usługę Intune z usługą Defender for Endpoint](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>Uzyskiwanie wymaganych uprawnień

Domyślnie tylko użytkownicy z przypisaną rolą administratora globalnego lub administratora usługi Intune w usłudze Azure AD mogą zarządzać profilami konfiguracji urządzeń potrzebnymi do korzystania z tych urządzeń i wdrażać plan bazowy zabezpieczeń.

Jeśli masz inne role, upewnij się, że masz odpowiednie uprawnienia:

- Pełne uprawnienia do konfiguracji urządzeń
- Pełne uprawnienia do planu bazowego zabezpieczeń
- Odczytywanie uprawnień do zasad zgodności urządzeń
- Uprawnienia do odczytu dla organizacji

![Wymagane uprawnienia w usłudze Intune.](images/secconmgmt_intune_permissions.png)

*Uprawnienia do konfiguracji urządzenia w usłudze Intune*

> [!TIP]
> Aby dowiedzieć się więcej o przypisywaniu uprawnień w usłudze Intune, [przeczytaj o tworzeniu ról niestandardowych](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>W tej sekcji

Temat|Opis
:---|:---
[Pobierz urządzenia do usługi Defender dla punktu końcowego](configure-machines-onboarding.md)|Śledź stan dołączania urządzeń zarządzanych w usłudze Intune i większej liczby urządzeń za pośrednictwem usługi Intune. 
[Zwiększanie zgodności z planem bazowym zabezpieczeń programu Defender for Endpoint](configure-machines-security-baseline.md)|Śledzenie zgodności i niezgodność planu bazowego. Wdrażanie planu bazowego zabezpieczeń na większej liczby urządzeń zarządzanych w usłudze Intune.
[Optymalizowanie wdrażania reguł asr i wykrywanie](configure-machines-asr.md)|Przejrzyj wdrożenie reguł i dostosuj wykrywanie przy użyciu narzędzi do analizy wpływu w Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sieci.</a>

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
