---
title: Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)
description: Wdeksuj pakiet konfiguracji na urządzeniu infrastruktury pulpitów wirtualnych (VDI), aby były one dołączane do usługi Programu Microsoft Defender dla punktu końcowego.
keywords: konfigurowanie urządzenia infrastruktury pulpitów wirtualnych (VDI), vdi, zarządzanie urządzeniami, konfigurowanie programu Microsoft Defender dla punktów końcowych, punktów końcowych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.date: 02/14/2022
ms.technology: mde
ms.openlocfilehash: 7342f368063c2c9024c4942c33a2e41f28eebd36
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449824"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure) w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Urządzenia infrastruktury pulpitów wirtualnych (VDI)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Trwałe sieci VDI** -  [Dołączanie trwałego komputera VDI](configure-endpoints.md) do programu Microsoft Defender for Endpoint jest obsługiwane tak samo, jak w przypadku komputera fizycznego, takiego jak komputer stacjonarny lub przenośny. Zasady grupy, Microsoft Endpoint Manager i inne metody mogą być używane do wschowania komputera trwałego. W portalu Microsoft 365 Defender w obszarzehttps://security.microsoft.com) dołączania wybierz preferowaną metodę dołączania i postępuj zgodnie z instrukcjami dla tego typu. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Wnoszenie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)

Program Defender for Endpoint obsługuje dołączanie nietrwałych sesji VDI.

Podczas dołączania interfejsów VDI mogą wiązać się ze swoimi wyzwaniami. Oto typowe wyzwania związane z tym scenariuszem:

- Szybkie wczesne dołączanie do krótkiej sesji, która musi zostać wproszona do usługi Defender for Endpoint przed rzeczywistym inicjowaniem obsługi administracyjnej.
- Nazwa urządzenia jest zwykle używana ponownie dla nowych sesji.

Urządzenia VDI mogą być wyświetlane w portalu programu Defender for Endpoint jako:

- Jedna pozycja dla każdego urządzenia.

  > [!NOTE]
  > W takim przypadku podczas tworzenia  sesji musi być skonfigurowana ta sama nazwa urządzenia, na przykład przy użyciu nienadzorowanych plików odpowiedzi.

- Wiele wpisów dla każdego urządzenia — po jednym dla każdej sesji.

Poniższe kroki poprowadzi Cię przez dołączanie urządzeń VDI i będą wyróżniać kroki dla 1 i wielu wpisów.

> [!WARNING]
> W środowiskach, w których występują niskie konfiguracje zasobów, procedura rozruchu VDI może spowolnić dołączanie czujnika punktu końcowego programu Defender.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>Na Windows 10, lub Windows 11 lub Windows Server 2012 R2 lub nowszy

> [!NOTE]
> Windows Server 2016 i Windows Server 2012 R2 muszą zostać przygotowane przez zastosowanie pakietu instalacyjnego najpierw, zgodnie z instrukcjami w Windows [Onboard,](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) aby ta funkcja działała.

1.  Otwórz pakiet konfiguracji VDI .zip (*WindowsDefenderATPOnboardingPackage.zip*), który został pobrany z Kreatora dołączania usługi. Możesz również pobrać pakiet z portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender witryny</a>:

    1. W okienku nawigacji wybierz pozycję **Ustawienia** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. Wybierz system operacyjny.

    1.  W polu **Metoda wdrażania** wybierz **pozycję Skrypty wdrażania VDI dla nietrwałych punktów końcowych**.

    1. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

2. Skopiuj pliki z folderu WindowsDefenderATPOnboardingPackage wyodrębniony z pliku .zip do złotego/wzorcowego obrazu pod ścieżką `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Jeśli implementujesz wiele wpisów dla każdego urządzenia — po jednym dla każdej sesji, skopiuj kod WindowsDefenderATPOnboardingScript.cmd.
    2. Jeśli implementujesz pojedynczą pozycję dla każdego urządzenia, skopiuj zarówno Onboard-NonPersistentMachine.ps1 WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Jeśli nie widzisz folderu, może `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` to być ukryte. Musisz wybrać opcję Pokaż ukryte **pliki i** foldery w Eksploratorze plików.

3. Otwórz okno Edytora zasady grupy komputera i przejdź do **strony Konfiguracja** \> **komputera Windows Ustawienia** \> **uruchamianie skryptów**\>.

   > [!NOTE]
   > Domeny zasady grupy być także używane do wnoszania nietrwałych urządzeń VDI.

4. W zależności od metody, która ma być zaimplementowana, wykonaj odpowiednie czynności:
    - Dla poszczególnych urządzeń:

         Wybierz **kartę Skrypty programu PowerShell**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator zostanie otwarty bezpośrednio w ścieżce, do której wcześniej skopiowano skrypt dołączania). Przejdź do skryptu dołączania programu PowerShell `Onboard-NonPersistentMachine.ps1`. Nie trzeba określać drugiego pliku, ponieważ zostanie on wyzwolony automatycznie.

    - W przypadku wielu wpisów dla każdego urządzenia:

         Wybierz **kartę Skrypty**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator zostanie otwarty bezpośrednio w ścieżce, do której wcześniej skopiowano skrypt dołączania). Przejdź do skryptu bash wniesienie `WindowsDefenderATPOnboardingScript.cmd`.

5. Przetestuj swoje rozwiązanie:
   1. Utwórz pulę przy użyciu jednego urządzenia.
   2. Zaloguj się na urządzeniu.
   3. Wyloguj się z urządzenia.
   4. Zaloguj się na urządzeniu z innym użytkownikiem.
   5. W zależności od metody, która ma być zaimplementowana, wykonaj odpowiednie czynności:
      - W przypadku wpisu pojedynczego dla każdego urządzenia: Sprawdź tylko jedną pozycję w Microsoft 365 Defender blogu.
      - W przypadku wielu wpisów dla każdego urządzenia: Sprawdź wiele wpisów w Microsoft 365 Defender sieci.

6. Kliknij **listę Urządzenia w** okienku nawigacji.

7. Użyj funkcji wyszukiwania, wprowadzając nazwę urządzenia i wybierz **pozycję Urządzenie** jako typ wyszukiwania.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>Dla skośnych jednostki SKU (Windows Server 2008 R2)

> [!NOTE]
> Poniższe instrukcje dotyczące innych Windows serwera mają zastosowanie również w przypadku, gdy jest uruchomiona poprzednia wersja programu Microsoft Defender for Endpoint dla systemu Windows Server 2016 i Windows Server 2012 R2 wymagająca oprogramowania MMA. Instrukcje migrowania do nowego, ujednoliconego rozwiązania znajdują się w scenariuszach migracji [serwera w programie Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Poniższy rejestr jest istotny tylko wtedy, gdy celem jest uzyskanie "jednej propozycji dla każdego urządzenia".

1. Ustaw wartość rejestru na:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    lub przy użyciu wiersza polecenia:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. Postępuj zgodnie [z procesem dołączania do serwera](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Aktualizowanie nietrwałych obrazów infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)

Jako najlepsze rozwiązanie zalecamy używanie narzędzi obsługi w trybie offline do poprawiania obrazów złotych/wzorcowych.

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

1. Po uruchomieniu wzorca w celu obsługi lub poprawiania poprawek w trybie online uruchom skrypt wybiegania, aby wyłączyć czujnik programu Defender for Endpoint. Aby uzyskać więcej informacji, zobacz [Urządzenia przenośne korzystające ze skryptu lokalnego](configure-endpoints-script.md#offboard-devices-using-a-local-script).

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
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. W zwykły sposób ponownie wytłuchaj obraz złotego/wzorcowego.

## <a name="related-topics"></a>Tematy pokrewne
- [Na urządzeniach Windows przy użyciu aplikacji zasady grupy](configure-endpoints-gp.md)
- [Na urządzeniach Windows urządzeniach przy użyciu Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Na urządzeniach Windows urządzeniach przenośnych za pomocą narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md)
- [Dołączanie Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
