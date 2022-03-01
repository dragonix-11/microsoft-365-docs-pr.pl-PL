---
title: Dołączanie Windows 10 i Windows 11 urządzeń przy użyciu skryptu lokalnego
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
description: Użyj skryptu lokalnego, aby wdrożyć pakiet konfiguracji na urządzeniach, aby zostały one wdrożone w usłudze.
ms.openlocfilehash: 14412e782cffd597786a4d2c322fe2b8fc20e5ca
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2021
ms.locfileid: "62999371"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Dołączanie Windows 10 i Windows 11 urządzeń przy użyciu skryptu lokalnego

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Możesz także ręcznie włączyć poszczególne urządzenia, aby Microsoft 365. Warto to zrobić w pierwszej kolejności podczas testowania usługi przed zatwierdzeniem do korzystania ze wszystkich urządzeń w Twojej sieci.

> [!IMPORTANT]
> Ten skrypt został zoptymalizowany pod kątem używania na maksymalnie 10 urządzeniach.
>
> Aby wdrażać w skali, użyj [innych opcji wdrażania](device-onboarding-overview.md). Na przykład skrypt dołączania można wdrożyć na ponad 10 urządzeniach produkcyjnych, używając skryptu dostępnego na urządzeniach Windows 10 przy użyciu [zasady grupy](device-onboarding-gp.md).

## <a name="onboard-devices"></a>Urządzenia wyniesiene na urządzeniach w
 
1. Pobierz pakiet konfiguracyjnych .zip (*DeviceComplianceOnboardingPackage.zip*) z [Centrum zgodności firmy Microsoft](https://compliance.microsoft.com)

2. W okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> >  **Wniezienie urządzenia**.

3. W polu **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.
  
5. Wyodrębnij zawartość pakietu konfiguracyjne do lokalizacji na urządzeniu, które chcesz wdobyć (na przykład do pulpitu). Plik powinien mieć nazwę *DeviceOnboardingScript.cmd*.

6. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:

7. Przejdź do **przycisku Start** i wpisz **cmd**.

8. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

    ![Okno menu Start z punktem Uruchom jako administrator.](../media/dlp-run-as-admin.png)

9. Wpisz lokalizację pliku skryptu. Jeśli plik został skopiowany na pulpit, wpisz: *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. Naciśnij klawisz **Enter** lub kliknij przycisk **OK**.

Aby uzyskać informacje na temat ręcznego sprawdzania, czy urządzenie jest zgodne, i poprawnie raportuje dane czujnika, zobacz Rozwiązywanie problemów z dołączaniem do usługi [Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Urządzenia wye korzystające ze skryptu lokalnego

Ze względów bezpieczeństwa pakiet używany na urządzeniach offboardowych wygaśnie po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu wynegocjowego zostaniesz o nim powiadomiony(-a) o dacie wygaśnięcia pakietów, a także w nazwie pakietu.

> [!NOTE]
> Zasad wnoszeń i wynoszeń nie można wdrażać jednocześnie na tym samym urządzeniu, w przeciwnym razie spowoduje to nieprzewidywalne błędy.

1. Pobierz pakiet wywęszania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.

2. W okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> >  **Wyszczanie urządzenia**.

3. W polu **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

5. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której mogą uzyskiwać dostęp urządzenia. Plik powinien mieć nazwę *: DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:

7. Przejdź do **przycisku Start** i wpisz **cmd**.

8. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

    ![Okno menu Start z punktem Uruchom jako administrator.](../media/dlp-run-as-admin.png)

9. Wpisz lokalizację pliku skryptu. Jeśli plik został skopiowany na pulpit, wpisz: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. Naciśnij klawisz **Enter** lub kliknij przycisk **OK**.

> [!IMPORTANT]
> Wynosze powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu.

## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia

Aby sprawdzić, czy skrypt został pomyślnie ukończony i czy agent jest uruchomiony, możesz wykonać różne kroki weryfikacji opisane w te sposób: [Rozwiązywanie problemów z dołączaniem]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

Monitorowanie można również monitorować bezpośrednio w portalu lub przy użyciu różnych narzędzi wdrożeniowych.

### <a name="monitor-devices-using-the-portal"></a>Monitorowanie urządzeń za pomocą portalu

1. Przejdź do [Microsoft 365 zgodności](https://compliance.microsoft.com).

2. Wybierz **Ustawienia** >  **Device onboardingDevices** > .

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> >  **Device onboardingDevices** > .

1. Sprawdź, czy urządzenia są wyświetlane.

## <a name="related-topics"></a>Tematy pokrewne
- [Urządzenia Windows 10 i Windows 11 urządzeń korzystających z zasady grupy](device-onboarding-gp.md)
- [Urządzenia Windows 10 i Windows 11 urządzeń używających Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie Windows 10 i Windows 11 urządzeń za pomocą narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Uruchamianie testu wykrywania na nowo w urządzeniu z uruchomionym programem Microsoft Defender dla punktu końcowego](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Rozwiązywanie problemów z dołączaniem do zaawansowanej ochrony przed zagrożeniami w u programie Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)