---
title: Dołącz urządzenia z systemem Windows przy użyciu narzędzi do zarządzania urządzeniami przenośnymi
description: Użyj narzędzi mobilnych Zarządzanie urządzeniami do wdrażania pakietu konfiguracyjne na urządzeniach, aby były one dołączane do usługi Defender for Endpoint.
keywords: urządzenia onboard za pomocą usługi mdm, zarządzania urządzeniami, Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach Ochrona punktu końcowego w usłudze Microsoft Defender, mdm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f3b13df5b9368609e888b92cbba49a58a0db3008
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634762"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>Dołącz urządzenia z systemem Windows przy użyciu narzędzi do zarządzania urządzeniami przenośnymi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Za pomocą rozwiązań do zarządzania urządzeniami przenośnymi (MDM) możesz Windows 10 urządzenia. Program Defender for Endpoint obsługuje usługi MDM, zapewniając OMA-URIs tworzenia zasad zarządzania urządzeniami.


Aby uzyskać więcej informacji na temat korzystania z programu Defender for Endpoint CSP, zobacz Plik [DDF WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) i [WindowsAdvancedThreatProtection DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Jeśli korzystasz z usługi Microsoft Intune, musisz mieć zarejestrowane mdm urządzenia. W przeciwnym razie ustawienia nie zostaną zastosowane pomyślnie.

Aby uzyskać więcej informacji na temat włączania usługi MDM Microsoft Intune, zobacz [Rejestracja urządzenia (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Urządzenia w urządzeniach w urządzeniu Microsoft Intune

Zapoznaj się z [plikiem PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) aby zobaczyć różne ścieżki wdrożenia programu Defender dla punktu końcowego.

Postępuj zgodnie z instrukcjami [podanymi Intune](/mem/intune/protect/advanced-threat-protection-configure).

Aby uzyskać więcej informacji na temat korzystania z programu Defender for Endpoint CSP, zobacz Plik [DDF WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) i [WindowsAdvancedThreatProtection DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - W **zasadach Stan kondycji urządzeń wewnenych** używane są właściwości tylko do odczytu, których nie można rozwiązać.
> - Konfiguracja częstotliwości raportowania danych diagnostycznych jest dostępna tylko dla urządzeń w Windows 10 wersji 1703.


Zapoznaj się z [plikiem PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx), aby zobaczyć różne ścieżki wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania do uruchomienia
Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, [zobacz Uruchamianie testu](run-detection-test.md) wykrywania na nowo Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach.


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Urządzenia wyełowywne i monitorują je przy Zarządzanie urządzeniami urządzeniach przenośnych

Ze względów bezpieczeństwa pakiet używany na urządzeniach offboardowych wygaśnie po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane na urządzenie zostaną odrzucone. Podczas pobierania pakietu wynegocjowanego otrzymasz powiadomienie o dacie wygaśnięcia pakietów oraz zostanie on także uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasad wnoszeń i wynoszeń nie można wdrażać jednocześnie na tym samym urządzeniu, w przeciwnym razie spowoduje to nieprzewidywalne błędy.

1. Pobierz pakiet wynos ze <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>

   1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Zarządzanie urządzeniami** \> **(Wyczyszczycie**).

   1. Wybierz Windows 10 lub Windows 11 jako system operacyjny.

   1. W polu **Metoda wdrażania** wybierz pozycję **Zarządzanie urządzeniami / Microsoft Intune**.

   1. Kliknij **pozycję Pobierz** pakiet i zapisz .zip pliku.

2. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której dostęp mogą uzyskać administratorzy sieci, którzy wdrożyą pakiet. Plik powinien mieć nazwę *: WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. Skorzystaj z Microsoft Intune konfiguracji niestandardowej, aby wdrożyć następujące obsługiwane ustawienia OMA-URI.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Typ daty: Ciąg
   - Wartość: [Skopiuj i wklej wartość z zawartości pliku WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

Aby uzyskać więcej informacji Microsoft Intune dotyczących zasad, zobacz [Windows 10 ustawień zasad w Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> W **zasadach Stan kondycji urządzeń wynoszonych** używane są właściwości tylko do odczytu, których nie można rozwiązać.

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

## <a name="related-topics"></a>Tematy pokrewne
- [Dołącz urządzenia z systemem Windows przy użyciu zasad grupy](configure-endpoints-gp.md)
- [Dołącz urządzenia z systemem Windows przy użyciu menedżera konfiguracji punktu końcowego Microsoft](configure-endpoints-sccm.md)
- [Dołącz urządzenia z systemem Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](configure-endpoints-vdi.md)
- [Uruchamianie testu wykrywania na nowo włodowym Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia](run-detection-test.md)
- [Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender problemów z dołączaniem](troubleshoot-onboarding.md)
