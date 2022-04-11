---
title: Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)
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
description: Wdróż pakiet konfiguracji na urządzeniu infrastruktury pulpitu wirtualnego (VDI), aby był dołączany do usługi zapobiegania utracie danych punktu końcowego Microsoft 365.
ms.openlocfilehash: 6bfb0f69198afbcc9d2949d583e151631cc7953b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760630"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Dołączanie nietrwałych urządzeń infrastruktury pulpitu wirtualnego

**Dotyczy:**

- [Microsoft 365 ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

- Urządzenia infrastruktury pulpitu wirtualnego (VDI)

> [!WARNING]
> Microsoft 365 obsługa zapobiegania utracie danych punktu końcowego dla usługi Windows Virtual Desktop obsługuje scenariusze pojedynczej sesji. Scenariusze z wieloma sesjami w Windows Virtual Desktop nie są obecnie obsługiwane.

## <a name="onboard-vdi-devices"></a>Dołączanie urządzeń VDI

Microsoft 365 obsługuje dołączanie nietrwałej infrastruktury pulpitu wirtualnego (VDI).

> [!NOTE]
> Aby dołączyć nietrwałe sesje VDI, urządzenia VDI muszą znajdować się w Windows 10 1809 lub nowszym.

Podczas dołączania interfejsów VDI mogą wystąpić problemy. Poniżej przedstawiono typowe wyzwania dla tego scenariusza:

- Natychmiastowe wczesne dołączanie krótkotrwałych sesji, które muszą zostać dołączone do Microsoft 365 przed rzeczywistą aprowizowaniem.
- Nazwa urządzenia jest zwykle ponownie używana dla nowych sesji.

Urządzenia VDI mogą być wyświetlane w centrum zgodności Microsoft 365 jako:

- Pojedynczy wpis dla każdego urządzenia.
Należy pamiętać, że w tym przypadku podczas tworzenia sesji należy skonfigurować *tę samą* nazwę urządzenia, na przykład przy użyciu nienadzorowanego pliku odpowiedzi.
- Wiele wpisów dla każdego urządzenia — po jednym dla każdej sesji.

Poniższe kroki przeprowadzą Cię przez dołączanie urządzeń VDI i wyróżnią kroki dla pojedynczych i wielu wpisów.

> [!WARNING]
> W środowiskach, w których konfiguracje zasobów są niskie, procedura rozruchu interfejsu VDI może spowolnić proces dołączania urządzenia.

1. Pobierz pakiet konfiguracji interfejsu VDI .zip plik (*DeviceCompliancePackage.zip*) z [Centrum zgodności firmy Microsoft](https://compliance.microsoft.com).

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Device onboardingOnboarding** > .

3. W polu **Metoda wdrażania** wybierz pozycję **VDI onboarding scripts for non-persistent endpoints (Skrypty dołączania interfejsu VDI dla nietrwałych punktów końcowych**).

4. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

5. Skopiuj pliki z folderu DeviceCompliancePackage wyodrębnione z pliku .zip do `golden` obrazu w ścieżce `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. Jeśli nie implementujesz pojedynczego wpisu dla każdego urządzenia, skopiuj plik DeviceComplianceOnboardingScript.cmd.

7. Jeśli implementujesz pojedynczy wpis dla każdego urządzenia, skopiuj zarówno Onboard-NonPersistentMachine.ps1, jak i DeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > Jeśli nie widzisz folderu `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , może on być ukryty. Musisz wybrać opcję **Pokaż ukryte pliki i foldery** z Eksplorator plików.

8. Otwórz okno Edytor lokalnych zasady grupy i przejdź do pozycji **Konfiguracja** >  komputera **Windows Ustawienia** >  **ScriptsStartup** > .

   > [!NOTE]
   > Zasady grupy domeny mogą być również używane do dołączania nietrwałych urządzeń VDI.

9. W zależności od metody, którą chcesz zaimplementować, wykonaj odpowiednie kroki:

   **Dla pojedynczego wpisu dla każdego urządzenia**

   Wybierz kartę **Skrypty programu PowerShell**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator otworzy się bezpośrednio w ścieżce, w której wcześniej skopiowano skrypt dołączania). Przejdź do dołączania skryptu `Onboard-NonPersistentMachine.ps1`programu PowerShell.

   **W przypadku wielu wpisów dla każdego urządzenia**:

   Wybierz kartę **Skrypty**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator otworzy się bezpośrednio w ścieżce, w której wcześniej skopiowano skrypt dołączania). Przejdź do skryptu `DeviceComplianceOnboardingScript.cmd`powłoki bash dołączania.

10. Przetestuj rozwiązanie:
    1. Utwórz pulę przy użyciu jednego urządzenia.
    1. Zaloguj się na urządzeniu.
    1. Wyloguj się z urządzenia.
    1. Zaloguj się na urządzeniu przy użyciu innego użytkownika.
    1. **Dla pojedynczego wpisu dla każdego urządzenia**: sprawdź tylko jeden wpis w Centrum zabezpieczeń usługi Microsoft Defender.
       **Dla wielu wpisów dla każdego urządzenia**: sprawdź wiele wpisów w Centrum zabezpieczeń usługi Microsoft Defender.

11. Kliknij **listę Urządzenia** w okienku Nawigacji.

12. Użyj funkcji wyszukiwania, wprowadzając nazwę urządzenia i wybierając pozycję **Urządzenie** jako typ wyszukiwania.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Aktualizowanie nietrwałych obrazów infrastruktury pulpitu wirtualnego (VDI)

Najlepszym rozwiązaniem jest użycie narzędzi do obsługi offline w celu stosowania poprawek do złotych obrazów.

Na przykład możesz użyć poniższych poleceń, aby zainstalować aktualizację, gdy obraz pozostaje w trybie offline:

```DOS
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Aby uzyskać więcej informacji na temat poleceń DISM i obsługi w trybie offline, zapoznaj się z poniższymi artykułami:

- [Modyfikowanie obrazu Windows przy użyciu narzędzia DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Opcje Command-Line zarządzania obrazami DISM](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Zmniejsz rozmiar magazynu składników w obrazie Windows offline](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Jeśli obsługa w trybie offline nie jest realną opcją dla nietrwałego środowiska VDI, należy wykonać następujące kroki w celu zapewnienia spójności i kondycji czujnika:

1. Po uruchomieniu złotego obrazu do obsługi lub stosowania poprawek w trybie online uruchom skrypt odłączania, aby wyłączyć czujnik monitorowania urządzenia Microsoft 365. Aby uzyskać więcej informacji, zobacz [Artykuł Offboard devices using a local script (Odłącz urządzenia przy użyciu skryptu lokalnego](device-onboarding-script.md#offboard-devices-using-a-local-script)).

2. Upewnij się, że czujnik został zatrzymany, uruchamiając poniższe polecenie w oknie cmd:

   ```DOS
   sc query sense
   ```

3. Obsługuj obraz zgodnie z potrzebami.

4. Uruchom poniższe polecenia przy użyciu PsExec.exe (z https://download.sysinternals.com/files/PSTools.zip) którego można pobrać zawartość folderu cybernetycznego, którą czujnik mógł zgromadzić od czasu rozruchu:

    ```DOS
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Ponownie przypieczętuj złoty obraz tak, jak zwykle.

## <a name="related-topics"></a>Tematy pokrewne

- [Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu zasady grupy](device-onboarding-gp.md)
- [Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
