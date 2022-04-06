---
title: Przełączanie do Ochrona punktu końcowego w usłudze Microsoft Defender — Konfiguracja
description: Przejdź do usługi Defender dla punktu końcowego. Zapoznaj się z procesem konfiguracji, który obejmuje instalowanie Program antywirusowy Microsoft Defender.
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
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 5dd5c78c366a708104b4662be86d71056d6a726a
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632716"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Przełączanie do Ochrona punktu końcowego w usłudze Microsoft Defender — etap 2. Konfigurowanie

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Etap 1. Przygotowanie.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Faza 1. Przygotowanie](switch-to-mde-phase-1.md)|![Etap 2. Konfigurowanie.](images/phase-diagrams/setup.png#lightbox)<br/>Faza 2. Konfiguracja|[![Etap 3. Etap 3. Etap 3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Faza 3. Dołączenie](switch-to-mde-phase-3.md)|
|---|---|---|
||*Jesteś tutaj!*||

**Witamy w fazie konfiguracji przełączania [do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Ten etap obejmuje następujące kroki:

1. [Ponownie zainstaluj/włącz Program antywirusowy Microsoft Defender punktu końcowego](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Skonfiguruj usługę Defender dla punktu końcowego](#configure-defender-for-endpoint).
3. [Dodaj program Defender for Endpoint do listy wykluczeń istniejącego rozwiązania](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Dodaj istniejące rozwiązanie do listy wykluczeń dla Program antywirusowy Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Skonfiguruj grupy urządzeń, kolekcje urządzeń i jednostki organizacyjne](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Ponowne instalowanie/włączanie Program antywirusowy Microsoft Defender dla punktów końcowych

W niektórych wersjach pakietu Windows program Program antywirusowy Microsoft Defender został prawdopodobnie odinstalowany lub wyłączony podczas instalowania rozwiązania innego niż firmy Microsoft lub ochrony przed złośliwym oprogramowaniem. Gdy punkty końcowe uruchomione przez Windows są wnoszone do usługi Defender for Endpoint, Program antywirusowy Microsoft Defender działać w trybie pasywnym obok rozwiązania antywirusowego firmy microsoft. Aby dowiedzieć się więcej, zobacz [Ochrona antywirusowa za pomocą programu Defender dla punktu końcowego](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Podczas przełączania się do usługi Defender dla punktu końcowego może być konieczne wykonanie pewnych czynności w celu ponownej instalacji lub włączenia Program antywirusowy Microsoft Defender. W poniższej tabeli opisano, co należy zrobić na Windows klientach i serwerach.

|Typ punktu końcowego|Co należy zrobić|
|---|---|
|Windows klientów (na przykład punkty końcowe uruchomione Windows 10 i Windows 11)|Na ogół nie trzeba nic robić w przypadku klientów Windows (chyba że Program antywirusowy Microsoft Defender zostały odinstalowane). Na ogół Program antywirusowy Microsoft Defender być nadal instalowane, ale najprawdopodobniej są wyłączone na tym etapie procesu migracji. <br/><br/> Po zainstalowaniu rozwiązania niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft i do programu Defender for Endpoint klienci nie są jeszcze dostępni, program Program antywirusowy Microsoft Defender jest automatycznie wyłączony. Później, gdy punkty końcowe klienta są dołączane do usługi Defender for Endpoint, jeśli te punkty końcowe działają w rozwiązaniu antywirusowym innym niż firmy Microsoft, Program antywirusowy Microsoft Defender przechodzi w tryb pasywny. <br/><br/> Jeśli odinstalowane zostanie rozwiązanie antywirusowe inne niż firmy Microsoft, Program antywirusowy Microsoft Defender automatycznie przejdzie w tryb aktywny.|
|Windows serwerach|Na Windows serwera konieczne będzie ponowne zainstalowanie Program antywirusowy Microsoft Defender i ręczne ustawienie trybu pasywnego. Na Windows w przypadku zainstalowania oprogramowania antywirusowego/ochrony przed złośliwym oprogramowaniem Program antywirusowy Microsoft Defender firmy Microsoft nie można używać razem z rozwiązaniem antywirusowym innym niż firmy Microsoft. W takich przypadkach Program antywirusowy Microsoft Defender została wyłączona lub odinstalowana ręcznie. <br/><br/> Aby ponownie zainstalować lub włączyć Program antywirusowy Microsoft Defender na Windows Server, wykonaj następujące zadania: <br/>- [Ponowne Program antywirusowy Microsoft Defender na Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [Ponowne Program antywirusowy Microsoft Defender na Windows Server w wersji 1803 lub nowszej](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [Ustawianie Program antywirusowy Microsoft Defender na tryb pasywny na Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Jeśli podczas ponownego instalowania lub ponownego włączania programu Program antywirusowy Microsoft Defender w programie Windows Server na tym serwerze będą się Program antywirusowy Microsoft Defender problemy, zobacz Rozwiązywanie problemów: odinstalowywanie programu [Windows Server](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Aby dowiedzieć się więcej Program antywirusowy Microsoft Defender o stanach z ochroną antywirusową innych niż firma Microsoft, zobacz [Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>Ponowne włączanie Program antywirusowy Microsoft Defender w Windows Server 2016

Możesz użyć narzędzia [Malware Protection Command-Line Utility,](command-line-arguments-microsoft-defender-antivirus.md) aby ponownie włączyć Program antywirusowy Microsoft Defender na Windows Server 2016.

1. Jako administrator lokalny na serwerze otwórz wiersz polecenia.

2. Uruchom następujące polecenie: `MpCmdRun.exe -wdenable`

3. Uruchom urządzenie ponownie.

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>Ponowne włączanie Program antywirusowy Microsoft Defender w Windows Server w wersji 1803 lub nowszej

> [!IMPORTANT]
> Następująca procedura dotyczy tylko punktów końcowych lub urządzeń z następującymi wersjami programu Windows:
> - Windows Server 2022
> - Windows Server 2019
> - Windows Server, wersja 1803 (tryb tylko podstawowy)

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

   W przypadku używania polecenia ROZM w sekwencji zadań z uruchomionym programem PowerShell wymagana jest następująca cmd.exe rozsyłania.
   Przykład:

   ```powershell
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. Uruchom urządzenie ponownie.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Ustawianie Program antywirusowy Microsoft Defender na tryb pasywny na Windows Server

> [!TIP]
> Teraz można uruchamiać Program antywirusowy Microsoft Defender pasywnego na Windows Server 2012 R2 i 2016. Aby uzyskać więcej informacji, [zobacz Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Otwórz Edytor rejestru, a następnie przejdź do .`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

2. Edytuj (lub utwórz) wpis DWORD o nazwie **ForceDefenderPassiveMode** i określ następujące ustawienia:

   - Ustaw wartość dword na **1**.

   - W **obszarze Podstawa** wybierz **pozycję Szesnastkowy**.

> [!NOTE]
> Po dojechi do usługi Defender dla punktu końcowego może być konieczne ustawienie trybu Program antywirusowy Microsoft Defender pasywnego na Windows serwera. Aby sprawdzić, czy tryb pasywny został ustawiony zgodnie z oczekiwaniami, wyszukaj zdarzenie *5007* w dzienniku operacyjnym firmy **Microsoft-Windows-Windows Defender** (`C:\Windows\System32\winevt\Logs`w miejscu ), i upewnij się, że dla klucza rejestru **ForceDefenderPassiveMode** lub **PassiveMode** ustawiono wartość **0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Używasz programu Windows Server 2012 R2 lub Windows Server 2016?

Teraz można uruchamiać Program antywirusowy Microsoft Defender pasywnego na Windows Server 2012 R2 i 2016, używając powyższej metody. Aby uzyskać więcej informacji, [zobacz Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Konfigurowanie usługi Defender dla punktu końcowego

Ten krok procesu migracji obejmuje skonfigurowanie Program antywirusowy Microsoft Defender punktów końcowych. Zalecamy używanie Intune jednak możesz użyć dowolnej z metod wymienionych w poniższej tabeli:

|Metoda|Co należy zrobić|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **UWAGA**: Intune jest teraz częścią Microsoft Endpoint Manager.|1. Przejdź do centrum [Microsoft Endpoint Manager i](https://go.microsoft.com/fwlink/?linkid=2109431) zaloguj się.<br/><br/>2. Wybierz **pozycję Urządzenia** \> **Profile konfiguracji**, a następnie wybierz typ profilu, który chcesz skonfigurować. Jeśli typ profilu Ograniczenia dotyczące urządzeń nie został  jeszcze utworzony lub chcesz utworzyć nowy, zobacz Konfigurowanie ustawień ograniczeń urządzeń w aplikacji [Microsoft Intune](/intune/device-restrictions-configure).<br/><br/>3. Wybierz **pozycję Właściwości**, a następnie pozycję **Ustawienia konfiguracji: Edytuj**<br/><br/>4. **Rozwiń Program antywirusowy Microsoft Defender**.<br/><br/>5. Włączanie **ochrony w chmurze**.<br/><br/>6. Na liście **rozwijanej Monituj użytkowników przed przykładowym** przesłaniem wybierz **pozycję Automatycznie wyślij wszystkie próbki**.<br/><br/>7. Z listy **rozwijanej Wykryj potencjalnie niechciane aplikacje** wybierz pozycję **Włącz lub** **Inspekcja**.<br/><br/>8. Wybierz **pozycję Recenzja + zapisywanie**, a następnie wybierz pozycję **Zapisz**. <br/><br/> **PORADA**: Aby uzyskać więcej informacji na temat Intune profilów urządzeń, w tym dotyczących tworzenia i konfigurowania ich ustawień, zobacz Co to są Microsoft Intune [profilów urządzeń?](/intune/device-profiles).|
|Microsoft Endpoint Configuration Manager|Zobacz [Tworzenie i wdrażanie zasad ochrony przed złośliwym oprogramowaniem dla Endpoint Protection w programie Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Podczas tworzenia i konfigurowania zasad ochrony przed złośliwym oprogramowaniem należy zapoznać się z ustawieniami ochrony w czasie rzeczywistym i od początku [włączyć blokowanie](configure-block-at-first-sight-microsoft-defender-antivirus.md).[](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings)
|Panel sterowania w programie Windows|Postępuj zgodnie z wskazówkami tutaj: [Włącz Program antywirusowy Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). W niektórych wersjach programu *Program antywirusowy Windows Defender* może być Program antywirusowy Microsoft Defender zamiast  Windows).|
|[Zaawansowane zasady grupy zaawansowane](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> lub <br/><br/> [zasady grupy zarządzania](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. Przejdź do konfiguracja **komputera Szablony** \> **administracyjne** \> **Windows składników Program antywirusowy Microsoft Defender**\>.<br/><br/>2. Poszukaj zasad o nazwie **Wyłączanie Program antywirusowy Microsoft Defender**.<br/><br/>3. Wybierz **pozycję Edytuj ustawienie zasad** i upewnij się, że zasady są wyłączone. Ta akcja umożliwia Program antywirusowy Microsoft Defender. <br/>W niektórych wersjach programu *Program antywirusowy Windows Defender* może być Program antywirusowy Microsoft Defender zamiast  Windows).|

> [!TIP]
> Możesz wdrożyć zasady przed dołozeniem urządzeń organizacji.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Dodaj Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń istniejącego rozwiązania

Ten krok procesu konfiguracji obejmuje dodanie usługi Defender for Endpoint do listy wykluczeń istniejącego rozwiązania ochrony punktu końcowego i wszystkich innych produktów zabezpieczeń, z których korzysta Twoja organizacja.

> [!TIP]
> Aby uzyskać pomoc dotyczącą konfigurowania wykluczeń, zapoznaj się z dokumentacją dostawcy rozwiązań.

Konkretne wykluczenia do skonfigurowania zależą od tego, Windows które punkty końcowe lub urządzenia są uruchomione, i są wymienione w poniższej tabeli.
<br/><br/>

| System operacyjny |Wykluczenia |
|:--|:--|
|Windows 11 <br/><br/>Windows 10, [wersja 1803](/windows/release-health/status-windows-10-1803) lub nowsza (zobacz [Windows 10 informacje o wersji](/windows/release-health/release-information))<br/><br/>Windows 10 wersji 1703 lub 1709 z zainstalowaną [kb4493441](https://support.microsoft.com/help/4493441) <br/><br/> Windows Server 2022<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server, wersja 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>Ponadto na Windows Server 2012 R2 i 2016 z zastosowaniem nowoczesnego, ujednoliconego rozwiązania po zaktualizowaniu składnika Sense EDR przy użyciu aktualizacji [KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) są wymagane następujące wykluczenia:<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe` |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 z dodatkiem SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**UWAGA**: Pliki tymczasowe hosta monitorowania 6\45 mogą być różnymi pogrupowanych podfolderami.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Dodaj istniejące rozwiązanie do listy wykluczeń dla Program antywirusowy Microsoft Defender

W tym kroku procesu konfiguracji dodasz istniejące rozwiązanie do Program antywirusowy Microsoft Defender wykluczeń. Możesz wybrać jedną z kilku metod dodawania wykluczeń Program antywirusowy Microsoft Defender, jak podano w poniższej tabeli: 

|Metoda|Co należy zrobić|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **UWAGA**: Intune jest teraz częścią Microsoft Endpoint Manager.|1. Przejdź do centrum [Microsoft Endpoint Manager i](https://go.microsoft.com/fwlink/?linkid=2109431) zaloguj się.<br/><br/>2. Wybierz **pozycję Profile** \> **konfiguracji** urządzeń, a następnie wybierz profil, który chcesz skonfigurować.<br/><br/>3. W **obszarze Zarządzanie** wybierz pozycję **Właściwości**.<br/><br/>4. Wybierz **pozycję Ustawienia konfiguracji: Edytuj**.<br/><br/>5. **Rozwiń Program antywirusowy Microsoft Defender**, a następnie rozwiń Program antywirusowy Microsoft Defender **wykluczeń**.<br/><br/>6. Określ pliki, foldery, rozszerzenia i procesy, które mają być wykluczone Program antywirusowy Microsoft Defender skanów. Aby uzyskać informacje referencyjne, [Program antywirusowy Microsoft Defender wykluczenia](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. Wybierz **pozycję Recenzja + zapisywanie**, a następnie wybierz pozycję **Zapisz**.|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. Za pomocą konsoli [Configuration Manager](/mem/configmgr/core/servers/manage/admin-console) \> przejdź do tematu Zasoby i zgodność **z** \> Endpoint Protection zasadami ochrony przed **złośliwym** kodem, a następnie wybierz zasady, które chcesz zmodyfikować.<br/><br/>2. Określ ustawienia wykluczeń plików, folderów, rozszerzeń i procesów, które mają być wykluczone Program antywirusowy Microsoft Defender skanów.|
|[Obiekt zasad grupy](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. Na komputerze zasady grupy zarządzania danymi otwórz konsolę zarządzania usługami [zasady grupy, kliknij](https://technet.microsoft.com/library/cc731212.aspx) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.<br/><br/>2. W zasady grupy **zarządzania przejdź** do **konfiguracja** komputera i wybierz pozycję **Szablony administracyjne**.<br/><br/>3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender \> \> wykluczeń**. W niektórych wersjach programu *Program antywirusowy Windows Defender* może być Program antywirusowy Microsoft Defender zamiast  Windows).<br/><br/>4. Kliknij dwukrotnie ustawienie **Wyjątki ścieżki** i dodaj wykluczenia.<br/><br/>5. Ustaw dla opcji wartość **Włączone**.<br/><br/>6. W sekcji **Opcje** wybierz pozycję **Pokaż....**<br/><br/>7. Określ każdy folder w swoim wierszu pod **kolumną Nazwa** wartości. W przypadku określenia pliku wprowadź w pełni kwalifikowaną ścieżkę do pliku, w tym literę dysku, ścieżkę folderu, nazwę pliku i rozszerzenie. Wprowadź **wartość 0** w **kolumnie** Wartość.<br/><br/>8. Wybierz **przycisk OK**.<br/><br/>9. Kliknij dwukrotnie ustawienie **Wykluczenia rozszerzeń** i dodaj wykluczenia.<br/><br/>10. Ustaw dla opcji wartość **Włączone**.<br/><br/>11. W sekcji **Opcje** wybierz pozycję **Pokaż...**.<br/><br/>12. Wprowadź poszczególne rozszerzenia plików w wierszu poniżej **kolumny Nazwa** wartości. Wprowadź **wartość 0** w **kolumnie** Wartość.<br/><br/>13. Wybierz przycisk **OK**.|
|Obiekt lokalnych zasad grupy|1. Na punkcie końcowym lub urządzeniu otwórz Edytor zasady grupy sieci Web.<br/><br/>2. Przejdź do **szablonu administracyjnego** \>  \> konfiguracji **komputera i Windows składników** \> **Program antywirusowy Microsoft Defender** \> **wykluczeń**. W niektórych wersjach programu *Program antywirusowy Windows Defender* może być Program antywirusowy Microsoft Defender zamiast  Windows).<br/><br/>3. Określ ścieżkę i wykluczenia procesów.|
|Klucz rejestru|1. Wyeksportuj następujący klucz rejestru: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Zaimportuj klucz rejestru. Oto dwa przykłady:<br/>— Ścieżka lokalna: `regedit.exe /s c:\temp\ MDAV_Exclusion.reg`<br/>— Udział sieciowy: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Pamiętaj o następujących kwestiach dotyczących wykluczeń

Po dodaniu [wykluczeń do Program antywirusowy Microsoft Defender należy](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) dodać wykluczenia dotyczące ścieżki i procesu.

Należy pamiętać o następujących kwestiach:

- *Wykluczenia ścieżek nie obejmują* określonych plików ani dostępu do nich.

- *Wykluczenia procesów nie* wykluczają z jakiegokolwiek procesu, ale nie wykluczają samego procesu.

- Wyklucz proces, używając ich pełnej ścieżki, a nie tylko nazwy użytkownika. Metoda dostępna tylko w przypadku nazw jest mniej bezpieczna.

- Jeśli każdy plik wykonywalny (.exe) zostanie na liście jako wykluczona ścieżka i wykluczenie procesu, proces i wszelkie jego dane zostaną wykluczone.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Konfigurowanie grup urządzeń, kolekcji urządzeń i jednostek organizacyjnych

Grupy urządzeń, kolekcje urządzeń i jednostki organizacyjne umożliwiają Twoje zespołowi zabezpieczeń wydajne i efektywne zarządzanie zasadami zabezpieczeń oraz przypisywanie ich. W poniższej tabeli opisano każdą z tych grup i sposób ich konfigurowania. Twoja organizacja może nie używać wszystkich trzech typów kolekcji.

|Typ kolekcji|Co należy zrobić|
|---|---|
|[Grupy urządzeń](/microsoft-365/security/defender-endpoint/machine-groups) (nazywane wcześniej grupami *maszynowymi*) umożliwiają Twojemu zespołowi ds. bezpieczeństwa konfigurowanie funkcji zabezpieczeń, takich jak zautomatyzowane badanie i rozwiązywanie problemów. <br/><br/> Grupy urządzeń przydają się również do przypisywania dostępu do tych urządzeń, dzięki czemu zespół operacyjny zabezpieczeń może w razie potrzeby podjąć działania naprawcze. <br/><br/> Grupy urządzeń są tworzone w trakcie wykrycia i zatrzymania ataków, alerty, takie jak "alert dostępu początkowego", zostały wyzwolone i pojawiły się w portalu Microsoft 365 Defender [urządzenia](/microsoft-365/security/defender/microsoft-365-defender).|1. Przejdź do portalu Microsoft 365 Defender (<https://security.microsoft.com>).<br/><br/>2. W okienku nawigacji po lewej stronie **wybierz pozycję** \> Ustawienia **grupy Urządzenia z** \> **uprawnieniami** \> **do punktów końcowych**.<br/><br/>3. Wybierz **pozycję + Dodaj grupę urządzeń**.<br/><br/>4. Określ nazwę i opis grupy urządzeń.<br/><br/>5. Wybierz opcję z  listy Poziom automatyzacji. (Zalecamy pełne **— automatyczne korygowanie zagrożeń**). Aby dowiedzieć się więcej o różnych poziomach automatyzacji, zobacz [Jak są korygowane zagrożenia](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. Określ warunki dla reguły dopasowywania, aby określić, które urządzenia należą do grupy urządzeń. Na przykład możesz wybrać domenę, wersje systemu operacyjnego, a nawet używać [tagów urządzeń](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. Na karcie **Dostęp użytkowników** określ role, które powinny mieć dostęp do urządzeń zawartych w grupie urządzeń.<br/><br/>8. Wybierz pozycję **Gotowe**.|
|[Kolekcje urządzeń](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) umożliwiają zespołowi ds. zabezpieczeń zarządzanie aplikacjami, wdrażanie ustawień zgodności lub instalowanie aktualizacji oprogramowania na urządzeniach w organizacji. <br/><br/> Kolekcje urządzeń są tworzone przy użyciu [Configuration Manager](/mem/configmgr/).|Postępuj zgodnie z instrukcjami [w tece Tworzenie kolekcji](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[Jednostki](/azure/active-directory-domain-services/create-ou) organizacyjne umożliwiają logiczne grupowanie obiektów, takich jak konta użytkowników, konta usług lub konta komputerów. <br/><br/> Następnie możesz przypisywać administratorów do konkretnych jednostek organizacyjnych i stosować zasady grupy, aby wymuszać kierowane ustawienia konfiguracji. <br/><br/> Jednostki organizacyjne są definiowane [w Azure Active Directory domenowych](/azure/active-directory-domain-services).|Postępuj zgodnie z instrukcjami [w tece Tworzenie jednostki organizacyjnej w domenie zarządzanej Azure Active Directory domen usług domenowych](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>Następny krok

**Gratulacje**! Ukończono etap konfiguracji przełączania [do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Przejdź do fazy 3. Dołączanie do programu Defender dla punktu końcowego](switch-to-mde-phase-3.md)
