---
title: Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu skryptu lokalnego
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
description: Użyj skryptu lokalnego, aby wdrożyć pakiet konfiguracji na urządzeniach, aby były one dołączane do usługi.
ms.openlocfilehash: 840573794b447162f917fed162bb1f869585286e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634428"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu skryptu lokalnego

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)

Możesz również ręcznie dołączyć poszczególne urządzenia do platformy Microsoft 365. Możesz to zrobić najpierw podczas testowania usługi przed zatwierdzeniem dołączenia wszystkich urządzeń w sieci.

> [!IMPORTANT]
> Ten skrypt został zoptymalizowany pod kątem użycia na maksymalnie 10 urządzeniach.
>
> Aby wdrożyć na dużą skalę, użyj [innych opcji wdrażania](device-onboarding-overview.md). Na przykład skrypt dołączania można wdrożyć na ponad 10 urządzeniach w środowisku produkcyjnym przy użyciu skryptu dostępnego w obszarze [Dołączanie urządzeń Windows 10 przy użyciu zasady grupy](device-onboarding-gp.md).

## <a name="onboard-devices"></a>Dołączanie urządzeń
 
1. Pobieranie pakietu konfiguracji .zip pakietu (*DeviceComplianceOnboardingPackage.zip*) z [portal zgodności Microsoft Purview](https://compliance.microsoft.com)

2. W okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> > **Dołączanie urządzenia**.

3. W polu **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.
  
5. Wyodrębnij zawartość pakietu konfiguracji do lokalizacji na urządzeniu, które chcesz dołączyć (na przykład Pulpit). Powinien istnieć plik o nazwie *DeviceOnboardingScript.cmd*.

6. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:

7. Przejdź do **pozycji Start** i wpisz **cmd**.

8. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

    ![Menu Start okna wskazujące polecenie Uruchom jako administrator.](../media/dlp-run-as-admin.png)

9. Wpisz lokalizację pliku skryptu. Jeśli plik został skopiowany do pulpitu, wpisz: *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. Naciśnij klawisz **Enter** lub kliknij przycisk **OK**.

Aby uzyskać informacje na temat ręcznego sprawdzania zgodności urządzenia i prawidłowego raportowania danych czujników, zobacz [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) w usłudze Microsoft Defender.

## <a name="offboard-devices-using-a-local-script"></a>Odłączanie urządzeń przy użyciu skryptu lokalnego

Ze względów bezpieczeństwa pakiet używany do odłączenia urządzeń wygaśnie 30 dni po pobraniu. Wygasłe pakiety odłączania wysyłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu odłączania otrzymasz powiadomienie o dacie wygaśnięcia pakietów i zostanie on również uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasady dołączania i odłączania nie mogą być wdrażane na tym samym urządzeniu w tym samym czasie, w przeciwnym razie spowoduje to nieprzewidywalne kolizje.

1. Pobierz pakiet odłączania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>.

2. W okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> > **Odłączanie urządzenia**.

3. W polu **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

5. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których mogą uzyskiwać dostęp urządzenia. Powinien istnieć plik o nazwie *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:

7. Przejdź do **pozycji Start** i wpisz **cmd**.

8. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

    ![Menu Start okna wskazujące polecenie Uruchom jako administrator.](../media/dlp-run-as-admin.png)

9. Wpisz lokalizację pliku skryptu. Jeśli plik został skopiowany na pulpit, wpisz: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. Naciśnij klawisz **Enter** lub kliknij przycisk **OK**.

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu.

## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia

Możesz wykonać różne kroki weryfikacji w sekcji [Rozwiązywanie problemów z dołączaniem]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding), aby sprawdzić, czy skrypt został ukończony pomyślnie, a agent jest uruchomiony.

Monitorowanie można również przeprowadzić bezpośrednio w portalu lub przy użyciu różnych narzędzi wdrażania.

### <a name="monitor-devices-using-the-portal"></a>Monitorowanie urządzeń przy użyciu portalu

1. Przejdź do [portal zgodności Microsoft Purview](https://compliance.microsoft.com).

2. Wybierz pozycję **Ustawienia** > **Urządzenia dołączania** > **urządzeń**.

1. Przejdź do portal zgodności Microsoft Purview i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> > **Urządzenia dołączające** > **urządzenia**.

1. Sprawdź, czy urządzenia są wyświetlane.

## <a name="related-topics"></a>Tematy pokrewne
- [Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu zasady grupy](device-onboarding-gp.md)
- [Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu programu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](device-onboarding-vdi.md)
- [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
