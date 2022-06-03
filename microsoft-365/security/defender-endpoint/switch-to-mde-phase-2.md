---
title: Przełącz się do Ochrona punktu końcowego w usłudze Microsoft Defender — Konfiguracja
description: Przełącz się do usługi Defender dla punktu końcowego. Przejrzyj proces instalacji, który obejmuje instalowanie Program antywirusowy Microsoft Defender.
keywords: migracja, Ochrona punktu końcowego w usłudze Microsoft Defender, oprogramowanie antywirusowe, tryb pasywny, proces konfiguracji
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: article
ms.custom: migrationguides
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: fe789a8f4eaaee68fd18832b5d45125407525ccd
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873903"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Przełącz się do Ochrona punktu końcowego w usłudze Microsoft Defender — faza 2: konfiguracja

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Faza 1. Przygotowanie.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Faza 1. Przygotowanie](switch-to-mde-phase-1.md)|![Faza 2. Konfigurowanie.](images/phase-diagrams/setup.png#lightbox)<br/>Faza 2. Konfiguracja|[![Faza 3. Dołączanie3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Faza 3. Dołączenie](switch-to-mde-phase-3.md)|
|---|---|---|
||*Jesteś tutaj!*||

**Witamy w fazie konfiguracji [przełączania do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Ta faza obejmuje następujące kroki:

1. [Zainstaluj ponownie/włącz Program antywirusowy Microsoft Defender w punktach końcowych](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Skonfiguruj usługę Defender dla punktu końcowego](#configure-defender-for-endpoint).
3. [Dodaj usługę Defender for Endpoint do listy wykluczeń istniejącego rozwiązania](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Dodaj istniejące rozwiązanie do listy wykluczeń dla Program antywirusowy Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Skonfiguruj grupy urządzeń, kolekcje urządzeń i jednostki organizacyjne](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Ponowne instalowanie/włączanie Program antywirusowy Microsoft Defender w punktach końcowych

W przypadku niektórych wersji Windows Program antywirusowy Microsoft Defender prawdopodobnie została odinstalowana lub wyłączona, gdy zainstalowano oprogramowanie antywirusowe/chroniące przed złośliwym kodem. Gdy punkty końcowe z uruchomionymi Windows są dołączane do usługi Defender for Endpoint, Program antywirusowy Microsoft Defender mogą działać w trybie pasywnym wraz z rozwiązaniem antywirusowym innym niż Microsoft. Aby dowiedzieć się więcej, zobacz [Ochrona antywirusowa za pomocą usługi Defender for Endpoint](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Podczas przełączania do usługi Defender for Endpoint może być konieczne wykonanie pewnych kroków w celu ponownej instalacji lub włączenia Program antywirusowy Microsoft Defender. W poniższej tabeli opisano, co należy zrobić na Windows klientów i serwerów.

|Typ punktu końcowego|Co robić|
|---|---|
|Windows klientów (takich jak punkty końcowe z uruchomionymi Windows 10 i Windows 11)|Ogólnie rzecz biorąc, nie trzeba podejmować żadnych działań dla klientów Windows (chyba że Program antywirusowy Microsoft Defender został odinstalowany). Ogólnie rzecz biorąc, Program antywirusowy Microsoft Defender nadal powinny być zainstalowane, ale najprawdopodobniej są wyłączone w tym momencie procesu migracji. <br/><br/> Po zainstalowaniu rozwiązania antywirusowego/chroniącego przed złośliwym kodem firmy innej niż Microsoft, a klienci nie są jeszcze dołączane do usługi Defender for Endpoint, Program antywirusowy Microsoft Defender jest automatycznie wyłączona. Później, gdy punkty końcowe klienta zostaną dołączone do usługi Defender for Endpoint, jeśli te punkty końcowe korzystają z rozwiązania antywirusowego innego niż Microsoft, Program antywirusowy Microsoft Defender przechodzi w tryb pasywny. <br/><br/> Jeśli rozwiązanie antywirusowe inne niż Microsoft zostanie odinstalowane, Program antywirusowy Microsoft Defender automatycznie przejdzie w tryb aktywny.|
|serwery Windows|Na serwerze Windows należy ponownie zainstalować Program antywirusowy Microsoft Defender i ręcznie ustawić go na tryb pasywny. Na serwerach Windows, gdy jest zainstalowany program antywirusowy lub oprogramowanie chroniące przed złośliwym kodem firmy innej niż Microsoft, Program antywirusowy Microsoft Defender nie może działać razem z rozwiązaniem antywirusowym innym niż Microsoft. W takich przypadkach Program antywirusowy Microsoft Defender jest wyłączona lub odinstalowana ręcznie. <br/><br/> Aby ponownie zainstalować lub włączyć Program antywirusowy Microsoft Defender na serwerze Windows Server, wykonaj następujące zadania: <br/>- [Zainstaluj ponownie Program antywirusowy Microsoft Defender na Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [Ponowne instalowanie Program antywirusowy Microsoft Defender na serwerze Windows w wersji 1803 lub nowszej](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [Ustaw Program antywirusowy Microsoft Defender na tryb pasywny na serwerze Windows](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Jeśli wystąpią problemy z ponowną instalacją lub ponownym włączeniem Program antywirusowy Microsoft Defender na serwerze Windows Server, zobacz [Rozwiązywanie problemów: Program antywirusowy Microsoft Defender jest odinstalowywany na serwerze Windows](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Aby dowiedzieć się więcej na temat Program antywirusowy Microsoft Defender stanów z ochroną antywirusową inną niż Microsoft, zobacz [Program antywirusowy Microsoft Defender zgodność](microsoft-defender-antivirus-compatibility.md).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>Ponowne włączanie Program antywirusowy Microsoft Defender na Windows Server 2016

Za pomocą [narzędzia Command-Line ochrony przed złośliwym oprogramowaniem](command-line-arguments-microsoft-defender-antivirus.md) można ponownie włączyć Program antywirusowy Microsoft Defender na Windows Server 2016.

1. Jako administrator lokalny na serwerze otwórz wiersz polecenia.

2. Uruchom następujące polecenie: `MpCmdRun.exe -wdenable`

3. Uruchom urządzenie ponownie.

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>Ponowne włączanie Program antywirusowy Microsoft Defender na serwerze Windows Server w wersji 1803 lub nowszej

> [!IMPORTANT]
> Poniższa procedura dotyczy tylko punktów końcowych lub urządzeń z następującymi wersjami Windows:
> - Windows Server 2022
> - Windows Server 2019
> - Windows Server, wersja 1803 (tryb tylko dla rdzeni)

1. Jako administrator lokalny na serwerze otwórz Windows PowerShell.

2. Uruchom następujące polecenia cmdlet programu PowerShell:

   ```powershell
   # For Windows Server 2016
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Gui
   # For Windows Server 2019 and Windows Server 2022
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

   W przypadku korzystania z polecenia DISM w sekwencji zadań z uruchomionym programem PowerShell wymagana jest następująca ścieżka do cmd.exe.
   Przykład:

   ```powershell
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. Uruchom urządzenie ponownie.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Ustaw Program antywirusowy Microsoft Defender na tryb pasywny na serwerze Windows

> [!TIP]
> Teraz można uruchamiać Program antywirusowy Microsoft Defender w trybie pasywnym w Windows Server 2012 R2 i 2016. Aby uzyskać więcej informacji, zobacz [Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Otwórz Edytor rejestru, a następnie przejdź do obszaru `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Edytuj (lub utwórz) wpis DWORD o nazwie **ForceDefenderPassiveMode** i określ następujące ustawienia:

   - Ustaw wartość DWORD na **1**.

   - W obszarze **Baza** wybierz pozycję **Szesnastkowa**.

> [!NOTE]
> Po dołączeniu do usługi Defender for Endpoint może być konieczne ustawienie trybu pasywnego Program antywirusowy Microsoft Defender na serwerze Windows. Aby sprawdzić, czy tryb pasywny został ustawiony zgodnie z oczekiwaniami, wyszukaj *zdarzenie 5007* w dzienniku **operacyjnym Microsoft-Windows-Windows Defender** (znajdującym się w `C:\Windows\System32\winevt\Logs`), i upewnij się, że **klucze rejestru ForceDefenderPassiveMode** lub **PassiveMode** zostały ustawione na **0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Czy używasz Windows Server 2012 R2, czy Windows Server 2016?

Teraz można uruchamiać Program antywirusowy Microsoft Defender w trybie pasywnym w Windows Server 2012 R2 i 2016 przy użyciu powyższej metody. Aby uzyskać więcej informacji, zobacz [Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Konfigurowanie usługi Defender dla punktu końcowego

Ten krok procesu migracji obejmuje skonfigurowanie Program antywirusowy Microsoft Defender dla punktów końcowych. Zalecamy używanie Intune. Jednak można użyć dowolnej z metod wymienionych w poniższej tabeli:

|Metoda|Co robić|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **UWAGA**: Intune jest teraz częścią Microsoft Endpoint Manager.|1. Przejdź do [centrum administracyjnego Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) i zaloguj się.<br/><br/>2. Wybierz pozycję **Profile konfiguracji** **urządzeń**\>, a następnie wybierz typ profilu, który chcesz skonfigurować. Jeśli nie utworzono jeszcze typu profilu **ograniczenia urządzenia** lub chcesz utworzyć nowy, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure).<br/><br/>3. Wybierz pozycję **Właściwości**, a następnie wybierz pozycję **Ustawienia konfiguracji: Edytuj**<br/><br/>4. Rozwiń **Program antywirusowy Microsoft Defender**.<br/><br/>5. Włącz **ochronę dostarczaną przez chmurę**.<br/><br/>6. Na liście rozwijanej **Monituj użytkowników przed przesłaniem przykładu** wybierz pozycję **Wyślij wszystkie przykłady automatycznie**.<br/><br/>7. Na liście rozwijanej **Wykrywanie potencjalnie niechcianych aplikacji** wybierz pozycję **Włącz** lub **Przeprowadź inspekcję**.<br/><br/>8. Wybierz pozycję **Przejrzyj i zapisz**, a następnie wybierz pozycję **Zapisz**. <br/><br/> **PORADA**: Aby uzyskać więcej informacji na temat Intune profilów urządzeń, w tym sposobu tworzenia i konfigurowania ich ustawień, zobacz [Co to są Microsoft Intune profile urządzeń?](/intune/device-profiles).|
|Microsoft Endpoint Configuration Manager|Zobacz [Tworzenie i wdrażanie zasad ochrony przed złośliwym kodem dla Endpoint Protection w Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Podczas tworzenia i konfigurowania zasad ochrony przed złośliwym kodem należy zapoznać się z [ustawieniami ochrony w czasie rzeczywistym](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) i [włączyć blok od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|Panel sterowania w Windows|Postępuj zgodnie ze wskazówkami tutaj: [Włącz Program antywirusowy Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). (W niektórych wersjach Windows mogą być widoczne *Program antywirusowy Windows Defender* zamiast *Program antywirusowy Microsoft Defender*).|
|[Zaawansowane zarządzanie zasady grupy](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> lub <br/><br/> [Konsolę zarządzania zasadami grupy](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. Przejdź do pozycji **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows składniki** \> **Program antywirusowy Microsoft Defender**.<br/><br/>2. Poszukaj zasad o nazwie **Wyłącz Program antywirusowy Microsoft Defender**.<br/><br/>3. Wybierz pozycję **Edytuj ustawienie zasad** i upewnij się, że zasady są wyłączone. Ta akcja umożliwia Program antywirusowy Microsoft Defender. <br/>(W niektórych wersjach Windows mogą być widoczne *Program antywirusowy Windows Defender* zamiast *Program antywirusowy Microsoft Defender*).|

> [!TIP]
> Zasady można wdrożyć przed dołączeniem urządzeń organizacji.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń istniejącego rozwiązania

Ten krok procesu konfiguracji obejmuje dodanie usługi Defender for Endpoint do listy wykluczeń dla istniejącego rozwiązania ochrony punktu końcowego i innych produktów zabezpieczających używanych przez organizację.

> [!TIP]
> Aby uzyskać pomoc w konfigurowaniu wykluczeń, zapoznaj się z dokumentacją dostawcy rozwiązań.

Określone wykluczenia do skonfigurowania zależą od wersji Windows uruchomionych punktów końcowych lub urządzeń i są wymienione w poniższej tabeli.

| OS |Wykluczenia |
|:--|:--|
|System Windows 11 <br/><br/>Windows 10, [wersja 1803](/lifecycle/announcements/windows-server-1803-end-of-servicing) lub nowsza (zobacz [informacje o wersji Windows 10](/windows/release-health/release-information))<br/><br/>Windows 10, wersja 1703 lub 1709 z [zainstalowaną wersją KB4493441](https://support.microsoft.com/help/4493441) <br/><br/> Windows Server 2022<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server, wersja 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>Ponadto w Windows Server 2012 R2 i 2016 r., w których uruchomiono nowoczesne, ujednolicone rozwiązanie, po zaktualizowaniu składnika Sense EDR przy użyciu [kb5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) są wymagane następujące wykluczenia:<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe` |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 z dodatkiem SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**UWAGA**: Monitorowanie plików tymczasowych hosta 6\45 może być różnymi podfolderami numerowanymi.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Dodaj istniejące rozwiązanie do listy wykluczeń dla Program antywirusowy Microsoft Defender

W tym kroku procesu konfiguracji dodasz istniejące rozwiązanie do listy wykluczeń Program antywirusowy Microsoft Defender. Możesz wybrać jedną z kilku metod dodawania wykluczeń do Program antywirusowy Microsoft Defender, jak wymieniono w poniższej tabeli: 

|Metoda|Co robić|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **UWAGA**: Intune jest teraz częścią Microsoft Endpoint Manager.|1. Przejdź do [centrum administracyjnego Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) i zaloguj się.<br/><br/>2. Wybierz pozycję **Profile konfiguracji** **urządzeń**\>, a następnie wybierz profil, który chcesz skonfigurować.<br/><br/>3. W obszarze **Zarządzanie** wybierz pozycję **Właściwości**.<br/><br/>4. Wybierz pozycję **Ustawienia konfiguracji: Edytuj**.<br/><br/>5. Rozwiń **Program antywirusowy Microsoft Defender**, a następnie rozwiń węzeł **Program antywirusowy Microsoft Defender Wykluczenia**.<br/><br/>6. Określ pliki i foldery, rozszerzenia i procesy do wykluczenia ze skanowania Program antywirusowy Microsoft Defender. Aby uzyskać informacje, zobacz [Program antywirusowy Microsoft Defender wykluczenia](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. Wybierz pozycję **Przejrzyj i zapisz**, a następnie wybierz pozycję **Zapisz**.|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. Korzystając z [konsoli Configuration Manager](/mem/configmgr/core/servers/manage/admin-console), przejdź do pozycji **Zasoby i zgodność** \> **Endpoint Protection** \> **zasady ochrony przed złośliwym kodem**, a następnie wybierz zasady, które chcesz zmodyfikować.<br/><br/>2. Określ ustawienia wykluczeń dla plików i folderów, rozszerzeń i procesów do wykluczenia ze skanowania Program antywirusowy Microsoft Defender.|
|[Obiekt zasad grupy](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](https://technet.microsoft.com/library/cc731212.aspx), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.<br/><br/>2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.<br/><br/>3. Rozwiń drzewo, aby **Windows składniki \> Program antywirusowy Microsoft Defender \> Wykluczenia**. (W niektórych wersjach Windows mogą być widoczne *Program antywirusowy Windows Defender* zamiast *Program antywirusowy Microsoft Defender*).<br/><br/>4. Kliknij dwukrotnie ustawienie **Wykluczenia ścieżki** i dodaj wykluczenia.<br/><br/>5. Ustaw opcję **Włączone**.<br/><br/>6. W sekcji **Opcje** wybierz pozycję **Pokaż...**.<br/><br/>7. Określ każdy folder we własnym wierszu w kolumnie **Nazwa wartości** . Jeśli określisz plik, wprowadź w pełni kwalifikowaną ścieżkę do pliku, w tym literę dysku, ścieżkę folderu, nazwę pliku i rozszerzenie. Wprowadź **wartość 0** w kolumnie **Wartość** .<br/><br/>8. Wybierz przycisk **OK**.<br/><br/>9. Kliknij dwukrotnie ustawienie **Wykluczenia rozszerzeń** i dodaj wykluczenia.<br/><br/>10. Ustaw opcję **Włączone**.<br/><br/>11. W sekcji **Opcje** wybierz pozycję **Pokaż...**.<br/><br/>12. Wprowadź każde rozszerzenie pliku we własnym wierszu w kolumnie **Nazwa wartości** . Wprowadź **wartość 0** w kolumnie **Wartość** .<br/><br/>13. Wybierz przycisk **OK**.|
|Obiekt lokalnych zasad grupy|1. Na punkcie końcowym lub urządzeniu otwórz Edytor lokalnych zasady grupy.<br/><br/>2. Przejdź do pozycji **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **wykluczenia**. (W niektórych wersjach Windows mogą być widoczne *Program antywirusowy Windows Defender* zamiast *Program antywirusowy Microsoft Defender*).<br/><br/>3. Określ ścieżkę i wykluczenia procesów.|
|Klucz rejestru|1. Wyeksportuj następujący klucz rejestru: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Zaimportuj klucz rejestru. Oto dwa przykłady:<br/>- Ścieżka lokalna: `regedit.exe /s c:\temp\ MDAV_Exclusion.reg`<br/>- Udział sieciowy: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Należy pamiętać o następujących kwestiach dotyczących wykluczeń

Po dodaniu [wykluczeń do skanowania Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) należy dodać ścieżkę i wykluczenia procesów.

Należy pamiętać o następujących kwestiach:

- *Wykluczenia ścieżek* wykluczają określone pliki i dostęp do tych plików.
- *Wykluczenia procesów* wykluczają wszystkie elementy procesu, ale nie wykluczają samego procesu.
- Wyświetl listę wykluczeń procesu przy użyciu pełnej ścieżki, a nie tylko ich nazwy. (Metoda tylko do nazwy jest mniej bezpieczna).
- Jeśli wyświetlisz listę wszystkich plików wykonywalnych (.exe) jako wykluczenie ścieżki i wykluczenie procesu, proces i wszystkie elementy, których dotyczy, zostaną wykluczone.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Konfigurowanie grup urządzeń, kolekcji urządzeń i jednostek organizacyjnych

Grupy urządzeń, kolekcje urządzeń i jednostki organizacyjne umożliwiają zespołowi ds. zabezpieczeń wydajne i efektywne zarządzanie zasadami zabezpieczeń i przypisywanie ich. W poniższej tabeli opisano każdą z tych grup i sposób ich konfigurowania. Twoja organizacja może nie używać wszystkich trzech typów kolekcji.

|Typ kolekcji|Co robić|
|---|---|
|[Grupy urządzeń](/microsoft-365/security/defender-endpoint/machine-groups) (wcześniej nazywane *grupami maszyn*) umożliwiają zespołowi ds. operacji zabezpieczeń konfigurowanie możliwości zabezpieczeń, takich jak zautomatyzowane badanie i korygowanie. <br/><br/> Grupy urządzeń są również przydatne do przypisywania dostępu do tych urządzeń, dzięki czemu zespół ds. operacji zabezpieczeń może w razie potrzeby podjąć akcje korygowania. <br/><br/> Grupy urządzeń są tworzone w obszarze Podczas wykrywania i zatrzymywania ataku alerty, takie jak "alert dostępu początkowego", zostały wyzwolone i wyświetlone w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).|1. Przejdź do portalu Microsoft 365 Defender (<https://security.microsoft.com>).<br/><br/>2. W okienku nawigacji po lewej stronie wybierz **pozycję Ustawienia** \> Uprawnienia **punktów końcowych** \>  \> **Grupy urządzeń**.<br/><br/>3. Wybierz pozycję **+ Dodaj grupę urządzeń**.<br/><br/>4. Określ nazwę i opis grupy urządzeń.<br/><br/>5. Na liście **Poziom automatyzacji** wybierz opcję. (Zalecamy **ustawienie Pełne — automatyczne korygowanie zagrożeń**). Aby dowiedzieć się więcej na temat różnych poziomów automatyzacji, zobacz [Jak są korygowane zagrożenia](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. Określ warunki pasującej reguły, aby określić, które urządzenia należą do grupy urządzeń. Możesz na przykład wybrać domenę, wersje systemu operacyjnego, a nawet użyć [tagów urządzeń](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. Na karcie **Dostęp użytkownika** określ role, które powinny mieć dostęp do urządzeń uwzględnionych w grupie urządzeń.<br/><br/>8. Wybierz pozycję **Gotowe**.|
|[Kolekcje urządzeń](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) umożliwiają zespołowi ds. operacji zabezpieczeń zarządzanie aplikacjami, wdrażanie ustawień zgodności lub instalowanie aktualizacji oprogramowania na urządzeniach w organizacji. <br/><br/> Kolekcje urządzeń są tworzone przy użyciu [Configuration Manager](/mem/configmgr/).|Wykonaj kroki opisane w [temacie Tworzenie kolekcji](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[Jednostki organizacyjne](/azure/active-directory-domain-services/create-ou) umożliwiają logiczne grupowanie obiektów, takich jak konta użytkowników, konta usług lub konta komputerów. <br/><br/> Następnie można przypisać administratorów do określonych jednostek organizacyjnych i zastosować zasady grupy w celu wymuszenia docelowych ustawień konfiguracji. <br/><br/> Jednostki organizacyjne są definiowane w [usługach Azure Active Directory Domain Services](/azure/active-directory-domain-services).|Wykonaj kroki opisane w temacie [Tworzenie jednostki organizacyjnej w domenie zarządzanej usług Azure Active Directory Domain Services](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>Następny krok

**Gratulacje**! Ukończono fazę konfiguracji [przełączania do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Przejdź do fazy 3: dołączanie do usługi Defender dla punktu końcowego](switch-to-mde-phase-3.md)
