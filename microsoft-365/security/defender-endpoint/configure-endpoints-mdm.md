---
title: Dołączanie urządzeń z systemem Windows do usługi Defender for Endpoint przy użyciu Intune
description: Użyj Microsoft Intune, aby wdrożyć pakiet konfiguracji na urządzeniach, tak aby były dołączane do usługi Defender for Endpoint.
keywords: dołączanie urządzeń przy użyciu zarządzania urządzeniami przenośnymi, zarządzania urządzeniami, dołączania Ochrona punktu końcowego w usłudze Microsoft Defender urządzeń, zarządzania urządzeniami przenośnymi
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
ms.openlocfilehash: 90c6ec688b19f328f89e2bcabe70b7955086e8da
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66531061"
---
# <a name="onboard-windows-devices-to-defender-for-endpoint-using-intune"></a>Dołączanie urządzeń z systemem Windows do usługi Defender for Endpoint przy użyciu Intune 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Rozwiązania do zarządzania urządzeniami przenośnymi (MDM) umożliwiają konfigurowanie Windows 10 urządzeń. Usługa Defender for Endpoint obsługuje rozwiązania MDM, udostępniając OMA-URIs do tworzenia zasad zarządzania urządzeniami.

Aby uzyskać więcej informacji na temat korzystania z dostawcy CSP usługi Defender for Endpoint, zobacz [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) i [WindowsAdvancedThreatProtection plik DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Urządzenia muszą być zarejestrowane w usłudze Intune jako rozwiązanie usługi Mobile Zarządzanie urządzeniami (MDM).

Aby uzyskać więcej informacji na temat włączania zarządzania urządzeniami przenośnymi za pomocą Microsoft Intune, zobacz [Rejestrowanie urządzeń (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Dołączanie urządzeń przy użyciu Microsoft Intune

Zapoznaj się z plikiem [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) lub [programem Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) , aby wyświetlić różne ścieżki wdrażania usługi Defender for Endpoint.

Postępuj zgodnie z instrukcjami z [Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).


Aby uzyskać więcej informacji na temat korzystania z dostawcy CSP usługi Defender for Endpoint, zobacz [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) i [WindowsAdvancedThreatProtection plik DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - Zasady **Stan kondycji dołączonych urządzeń** używają właściwości tylko do odczytu i nie można ich skorygować.
> - Konfiguracja częstotliwości raportowania danych diagnostycznych jest dostępna tylko dla urządzeń w Windows 10, wersja 1703.
> - Dołączanie do usługi Defender for Endpoint spowoduje dołączenie urządzenia do usługi [Data Loss Prevention (DLP),](../../compliance/endpoint-dlp-learn-about.md) która jest również częścią zgodności platformy Microsoft 365.


## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania dołączania
Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy urządzenie jest prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md).


## <a name="offboard-devices-using-mobile-device-management-tools"></a>Odłączanie urządzeń przy użyciu narzędzi mobile Zarządzanie urządzeniami

Ze względów bezpieczeństwa pakiet używany do odłączenia urządzeń wygaśnie 30 dni po pobraniu. Wygasłe pakiety odłączania wysyłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu odłączania otrzymasz powiadomienie o dacie wygaśnięcia pakietów i zostanie on również uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasady dołączania i odłączania nie mogą być wdrażane na tym samym urządzeniu w tym samym czasie, w przeciwnym razie spowoduje to nieprzewidywalne kolizje.

1. Pobierz pakiet odłączania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>:

   1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Odłączanie zarządzania urządzeniami**\>.

   1. Wybierz Windows 10 lub Windows 11 jako system operacyjny.

   1. W polu **Metoda wdrażania** wybierz pozycję **Mobile Zarządzanie urządzeniami/Microsoft Intune**.

   1. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

2. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których mogą uzyskać dostęp administratorzy sieci, którzy wdrożą pakiet. Powinien istnieć plik o nazwie *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. Użyj Microsoft Intune niestandardowych zasad konfiguracji, aby wdrożyć następujące obsługiwane ustawienia identyfikatora OMA-URI.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Typ daty: Ciąg
   - Wartość: [Skopiuj i wklej wartość z zawartości pliku WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

Aby uzyskać więcej informacji na temat ustawień zasad Microsoft Intune, zobacz [Windows 10 ustawienia zasad w Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> Zasady **Stan kondycji urządzeń odłączonych** używają właściwości tylko do odczytu i nie można ich skorygować.

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

## <a name="related-topics"></a>Tematy pokrewne
- [Dołącz urządzenia z systemem Windows przy użyciu zasad grupy](configure-endpoints-gp.md)
- [Dołącz urządzenia z systemem Windows przy użyciu menedżera konfiguracji punktu końcowego Microsoft](configure-endpoints-sccm.md)
- [Dołącz urządzenia z systemem Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](configure-endpoints-vdi.md)
- [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md)
- [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
