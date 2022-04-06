---
title: Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)
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
search.appverid:
- MET150
description: Wdeksuj pakiet konfiguracji na urządzeniu infrastruktury pulpitów wirtualnych (VDI), aby były one dołączane do usługi ochrony przed utratą danych Microsoft 365 punktów końcowych.
ms.openlocfilehash: 00804c93022f21715e3604eeb45c22caa4745f91
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682157"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

- Urządzenia infrastruktury pulpitów wirtualnych (VDI)

> [!WARNING]
> Microsoft 365 ochrony przed utratą danych w punkcie końcowym dla Windows Wirtualnego pulpitu obsługuje scenariusze z jedną sesją. Scenariusze z wieloma sesjami Windows pulpitu wirtualnego nie są obecnie obsługiwane.

## <a name="onboard-vdi-devices"></a>Urządzenia VDI na urządzeniach w urządzeniu

Microsoft 365 nietrwałych pulpitów wirtualnych (VDI, non-persistent virtual desktop infrastructure) podczas dołączania sesji.

> [!NOTE]
> Aby można było dołączać nietrwałych sesji VDI, urządzenia VDI muszą znajdować się na Windows 10 1809 lub więcej.

Podczas dołączania interfejsów VDI mogą wiązać się ze swoimi wyzwaniami. Oto typowe wyzwania związane z tym scenariuszem:

- Szybkie wczesne dołączanie do krótkich sesji, które muszą zostać Microsoft 365 przed rzeczywistym inicjowaniem obsługi administracyjnej.
- Nazwa urządzenia jest zwykle używana ponownie dla nowych sesji.

Urządzenia VDI mogą być wyświetlane w Centrum zgodności Microsoft 365 w następujący sposób:

- Jedna pozycja dla każdego urządzenia.
Pamiętaj, że w tym przypadku tę  samą nazwę urządzenia należy skonfigurować podczas tworzenia sesji, na przykład przy użyciu nienadzorowanych plików odpowiedzi.
- Wiele wpisów dla każdego urządzenia — po jednym dla każdej sesji.

Poniższe kroki poprowadzi Cię przez dołączanie urządzeń VDI i będą wyróżniać kroki dla 1 i wielu wpisów.

> [!WARNING]
> W środowiskach, w których występują niskie konfiguracje zasobów, procedura rozruchu VDI może spowalniać proces dołączania urządzenia.

1. Pobierz pakiet konfiguracji VDI z .zip (*DeviceCompliancePackage.zip*) z [Centrum zgodności firmy Microsoft](https://compliance.microsoft.com).

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Device onboardingOnboarding** > .

3. W polu **Metoda wdrażania** wybierz **pozycję Skrypty wdrażania VDI dla nietrwałych punktów końcowych**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

5. Skopiuj pliki z folderu DeviceCompliancePackage wyodrębniony z pliku .zip `golden` do obrazu pod ścieżką `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. Jeśli nie implementujesz pojedynczej pozycji dla każdego urządzenia, skopiuj kod DeviceComplianceOnboardingScript.cmd.

7. Jeśli implementujesz pojedynczą pozycję dla każdego urządzenia, skopiuj zarówno kod Onboard-NonPersistentMachine.ps1, jak i deviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > Jeśli nie widzisz folderu, może `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` to być ukryte. Musisz wybrać opcję Pokaż ukryte **pliki i** foldery w Eksploratorze plików.

8. Otwórz okno Edytor zasady grupy komputera i przejdź do **strony Konfiguracja komputera** >  **Windows Ustawienia** >  **ScriptsStartup** > .

   > [!NOTE]
   > Domeny zasady grupy być także używane do wnoszania nietrwałych urządzeń VDI.

9. W zależności od metody, która ma być zaimplementowana, wykonaj odpowiednie czynności:

   **Dla jednego wpisu dla każdego urządzenia**

   Wybierz **kartę Skrypty programu PowerShell**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator zostanie otwarty bezpośrednio w ścieżce, do której wcześniej skopiowano skrypt dołączania). Przejdź do skryptu dołączania programu PowerShell `Onboard-NonPersistentMachine.ps1`.

   **W przypadku wielu wpisów dla każdego urządzenia**:

   Wybierz **kartę Skrypty**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator zostanie otwarty bezpośrednio w ścieżce, do której wcześniej skopiowano skrypt dołączania). Przejdź do skryptu bash wniesienie `DeviceComplianceOnboardingScript.cmd`.

10. Przetestuj swoje rozwiązanie:
    1. Utwórz pulę przy użyciu jednego urządzenia.
    1. Zaloguj się na urządzeniu.
    1. Wyloguj się z urządzenia.
    1. Zaloguj się na urządzeniu z innym użytkownikiem.
    1. **W przypadku wpisu pojedynczego dla każdego urządzenia**: Sprawdź tylko jedną pozycję w Centrum zabezpieczeń usługi Microsoft Defender.
       **W przypadku wielu wpisów dla każdego urządzenia**: Sprawdź wiele wpisów w Centrum zabezpieczeń usługi Microsoft Defender.

11. Kliknij **listę Urządzenia w** okienku nawigacji.

12. Użyj funkcji wyszukiwania, wprowadzając nazwę urządzenia i wybierz **pozycję Urządzenie** jako typ wyszukiwania.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Aktualizowanie nietrwałych obrazów infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)

Jako najlepsze rozwiązanie zalecamy używanie narzędzi obsługi w trybie offline do poprawiania złotych obrazów.

Możesz na przykład użyć poniższych poleceń, aby zainstalować aktualizację, podczas gdy obraz pozostaje w trybie offline:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Aby uzyskać więcej informacji na temat poleceń ROZM i obsługi w trybie offline, zapoznaj się z poniższymi artykułami:

- [Modyfikowanie obrazu Windows przy użyciu funkcji ROZM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Opcje zarządzania obrazami Command-Line ROZM.](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Zmniejszanie rozmiaru magazynu składników w magazynie danych Windows offline](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Jeśli obsługa w trybie offline nie jest rentowną opcją dla nietrwałych środowisk VDI, należy podjąć następujące kroki w celu zapewnienia spójności i kondycji czujnika:

1. Po uruchomieniu złotego obrazu do obsługi lub poprawiania w trybie online uruchom skrypt wybiegania, aby wyłączyć czujnik monitorowania Microsoft 365 urządzenia. Aby uzyskać więcej informacji, zobacz [Urządzenia przenośne korzystające ze skryptu lokalnego](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. Upewnij się, że czujnik został zatrzymany, uruchamiając poniższe polecenie w oknie CMD:

   ```console
   sc query sense
   ```

3. Serwisuj obraz zgodnie z potrzebami.

4. Uruchom poniższe polecenia przy użyciu programu PsExec.exe ( https://download.sysinternals.com/files/PSTools.zip) który można pobrać w celu oczyszczenia zawartości cyber folderów, które czujnik mógł skumulować od momentu rozruchu:

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Ponownie zaklej złoty obraz tak jak zwykle.

## <a name="related-topics"></a>Tematy pokrewne

- [Urządzenia Windows 10 i Windows 11 urządzeń korzystających z zasady grupy](device-onboarding-gp.md)
- [Urządzenia Windows 10 i Windows 11 urządzeń używających Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie Windows 10 i Windows 11 urządzeń za pomocą narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie Windows 10 i Windows 11 urządzeń przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Rozwiązywanie problemów z dołączaniem do zaawansowanej ochrony przed zagrożeniami w u programie Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
