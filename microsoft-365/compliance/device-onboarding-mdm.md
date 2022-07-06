---
title: Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Użyj narzędzi mobile Zarządzanie urządzeniami, aby wdrożyć pakiet konfiguracji na urządzeniach, aby były one dołączone do usługi.
ms.openlocfilehash: d5c03c80c9a38d34ab27f888084604372874a64a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624206"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)

Do konfigurowania urządzeń można używać rozwiązań do zarządzania urządzeniami przenośnymi (MDM). Ochrona informacji na platformie Microsoft 365 obsługuje rozwiązania MDM, udostępniając OMA-URIs do tworzenia zasad zarządzania urządzeniami.


## <a name="before-you-begin"></a>Przed rozpoczęciem
Jeśli używasz Microsoft Intune, musisz mieć zarejestrowane urządzenie MDM. W przeciwnym razie ustawienia nie zostaną zastosowane pomyślnie. 

Aby uzyskać więcej informacji na temat włączania zarządzania urządzeniami przenośnymi za pomocą Microsoft Intune, zobacz [Rejestrowanie urządzeń (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Dołączanie urządzeń przy użyciu Microsoft Intune

Postępuj zgodnie z instrukcjami z [Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - Zasady **Stan kondycji dołączonych urządzeń** używają właściwości tylko do odczytu i nie można ich skorygować.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Odłączanie i monitorowanie urządzeń przy użyciu narzędzi mobile Zarządzanie urządzeniami

Ze względów bezpieczeństwa pakiet używany do odłączenia urządzeń wygaśnie 30 dni po pobraniu. Wygasłe pakiety odłączania wysyłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu odłączania otrzymasz powiadomienie o dacie wygaśnięcia pakietów i zostanie on również uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasady dołączania i odłączania nie mogą być wdrażane na tym samym urządzeniu w tym samym czasie, w przeciwnym razie spowoduje to nieprzewidywalne kolizje.

1. Pobierz pakiet odłączania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>.

2. W okienku nawigacji wybierz pozycję **Ustawienia** > **Odłączanie dołączania** >  urządzenia.

3. W polu **Metoda wdrażania** wybierz pozycję **Mobile Zarządzanie urządzeniami/Microsoft Intune**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

5. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których mogą uzyskać dostęp administratorzy sieci, którzy wdrożą pakiet. Powinien istnieć plik o nazwie *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Użyj Microsoft Intune niestandardowych zasad konfiguracji, aby wdrożyć następujące obsługiwane ustawienia identyfikatora OMA-URI.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Jeśli Ochrona punktu końcowego w usłudze Microsoft Defender jest już skonfigurowany, możesz **włączyć dołączanie urządzenia**, a krok 6 nie jest już wymagany.

> [!NOTE]
> Zasady **Stan kondycji urządzeń odłączonych** używają właściwości tylko do odczytu i nie można ich skorygować.

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

## <a name="related-topics"></a>Tematy pokrewne
- [Dołączanie urządzeń Windows 10 przy użyciu zasady grupy](device-onboarding-gp.md)
- [Dołączanie urządzeń Windows 10 przy użyciu programu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie urządzeń Windows 10 przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](device-onboarding-vdi.md)
- [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
