---
title: Przełączanie do Ochrona punktu końcowego w usłudze Microsoft Defender — Wboard
description: Przejdź na Ochrona punktu końcowego w usłudze Microsoft Defender. Na urządzeniach, a następnie odinstaluj rozwiązanie inne niż firmy Microsoft.
keywords: migracja, Ochrona punktu końcowego w usłudze Microsoft Defender, edr
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
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.topic: article
ms.date: 03/28/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 1397c34e8e4a7f1fcb20df192409bd57bc50f40b
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507126"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Przełączanie do Ochrona punktu końcowego w usłudze Microsoft Defender — etap 3. Etap: na wsch.

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Etap 1. Przygotowanie3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Etap 1. Przygotowywanie](switch-to-mde-phase-1.md) | [![Etap 2. Konfigurowanie](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Etap 2. Konfigurowanie](switch-to-mde-phase-2.md) | ![Etap 3. Wniesienie](images/phase-diagrams/onboard.png#lightbox)<br/>Etap 3. Wniesienie |
|--|--|--|
|| |*Jesteś tutaj!* |

**Witamy w etapie 3 [przełączania do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Ten etap migracji obejmuje następujące kroki:

1. [Urządzenia w programie Defender dla punktu końcowego](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [Uruchom test wykrywania](#run-a-detection-test).
3. [Upewnij się, Program antywirusowy Microsoft Defender jest w trybie pasywnym dla punktów końcowych](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints).
4. [Pobierz aktualizacje dla Program antywirusowy Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).
5. [Odinstaluj rozwiązanie inne niż firmy Microsoft](#uninstall-your-non-microsoft-solution).
6. [Upewnij się, że program Defender for Endpoint działa poprawnie](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Urządzenia, na których można Ochrona punktu końcowego w usłudze Microsoft Defender

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Wybierz **Ustawienia** \> **Do dołączania punktów** \> **końcowych** (w obszarze **Zarządzanie urządzeniami**).

3. Z listy **Wybierz system operacyjny, aby rozpocząć proces dołączania** wybierz system operacyjny.

4. W **obszarze Metoda wdrażania** wybierz opcję. Postępuj zgodnie z linkami i monitami, aby wychować urządzenia organizacji. Potrzebujesz pomocy? Zobacz [metody dołączania](#onboarding-methods) (w tym artykule).

> [!NOTE]
> Jeśli podczas dołączania coś poszło nie tak, zobacz [Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender dotyczących dołączania](troubleshoot-onboarding.md). W tym artykule opisano sposób rozwiązywania problemów z dołączaniem i typowych błędów dotyczących punktów końcowych.

### <a name="onboarding-methods"></a>Metody dołączania

> [!IMPORTANT]
> Jeśli używasz programu Microsoft Defender dla Chmury, zobacz [Integracja z usługą Microsoft Defender dla Chmury](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

Metody wdrażania różnią się w zależności od systemu operacyjnego i preferowanych metod. W poniższej tabeli wymieniono zasoby pomocne podczas pracy z programem Defender for Endpoint:

|Systemy operacyjne  |Metody  |
|---------|---------|
|Windows 10 lub nowszy<br/><br/>Windows Server 2019 lub nowszy<br/><br/>Windows Server w wersji 1803 lub nowszej<br/><br/>Windows Server 2012 R2 i 2016<sup>[[1](#fn1)]<sup>  |   [Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md)<br><br/>   [Zasady grupy](configure-endpoints-gp.md)<br/><br/>[Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)<br/><br/>[Microsoft Endpoint Manager/ Mobile Zarządzanie urządzeniami (Intune)](configure-endpoints-mdm.md)<br>    [Skrypty VDI](configure-endpoints-vdi.md) <br><br> **UWAGA**: Skrypt lokalny nadaje się do dowodu koncepcji, ale nie powinien być używany do wdrożenia produkcyjnego. W przypadku wdrożenia produkcyjnego zalecamy używanie aplikacji zasady grupy, Microsoft Endpoint Configuration Manager lub Intune. |
|Windows Server 2008 R2 z dodatkiem SP1 | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) [lub Microsoft Defender dla Chmury](/azure/security-center/security-center-wdatp) <br><br> **UWAGA**: Microsoft Monitoring Agent agentem usługi Azure Log Analytics. Aby dowiedzieć się więcej, zobacz Omówienie [agenta analizy dziennika](/azure/azure-monitor/platform/log-analytics-agent).  |
|Windows 8.1 Enterprise<br/><br/>Windows 8.1 Pro<br/><br/>Windows 7 z dodatkiem SP1 Pro<br/><br/>Windows 7 z dodatkiem SP1| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **UWAGA**: Microsoft Monitoring Agent agentem usługi Azure Log Analytics. Aby dowiedzieć się więcej, zobacz Omówienie [agenta analizy dziennika](/azure/azure-monitor/platform/log-analytics-agent).  
| macOS (zobacz [Wymagania systemowe](microsoft-defender-endpoint-mac.md) | [Skrypt lokalny](mac-install-manually.md)<br/><br/>[Microsoft Endpoint Manager](mac-install-with-intune.md)<br/><br/>[Jamf Pro](mac-install-with-jamf.md)<br/><br/>[Urządzenia Zarządzanie urządzeniami](mac-install-with-other-mdm.md)   |
| Linux (zobacz [Wymagania systemowe](microsoft-defender-endpoint-linux.md#system-requirements)) |  [Skrypt lokalny](linux-install-manually.md) <br><br/> [Wytłaczenie](linux-install-with-puppet.md) <br><br/> [Ansible](linux-install-with-ansible.md)|  
| iOS | [Microsoft Endpoint Manager](ios-install.md)     |
|Android  | [Microsoft Endpoint Manager](android-intune.md)  | 


(<a id="fn1">1</a>) Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone, korzystając z instrukcji podanych w te Windows[.](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016)


## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania

Aby sprawdzić, czy urządzenia zainstalowane na tych urządzeniach są poprawnie połączone z programem Defender for Endpoint, możesz uruchomić test wykrywania.

<br/><br/>

|System operacyjny|Wskazówki|
|---|---|
|Windows 10 lub nowszy<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server, wersja 1803 lub nowsza<br/><br/>System Windows Server 2016<br/><br/>Windows Server 2012 R2|Zobacz [Uruchamianie testu wykrywania](run-detection-test.md).<br/><br/>Odwiedź witrynę scenariuszy pokazu programu Defender for Endpoint (<https://demo.wd.microsoft.com>) i wypróbuj jeden lub więcej scenariuszy. Na przykład wypróbuj scenariusz **pokazu ochrona w** chmurze.|
|macOS (zobacz [Wymagania systemowe](microsoft-defender-endpoint-mac.md)|Pobierz aplikację DIY i korzystaj z jej podpowiedni <https://aka.ms/mdatpmacosdiy>. <br/><br/> Aby uzyskać więcej informacji, zobacz [Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md).|
|Linux (zobacz [Wymagania systemowe](microsoft-defender-endpoint-linux.md#system-requirements))|1. Uruchom następujące polecenie i poszukaj wyniku **1**: `mdatp health --field real_time_protection_enabled`.<br/><br/>2. Otwórz okno aplikacji Terminal i uruchom następujące polecenie: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. Uruchom następujące polecenie, aby wyświetlić listę wykrytych zagrożeń: `mdatp threat list`.<br/><br/>Aby uzyskać więcej informacji, zobacz [Program Defender dla punktu końcowego w systemie Linux](microsoft-defender-endpoint-linux.md).|

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>Potwierdzanie, Program antywirusowy Microsoft Defender jest w trybie pasywnym dla punktów końcowych

Po doprowadzeniu punktów końcowych do usługi Defender for Endpoint następnym krokiem jest upewninie się, że Program antywirusowy Microsoft Defender działa w trybie pasywnym. Możesz użyć jednej z kilku metod, zgodnie z opisem w poniższej tabeli:

<br/><br/>

|Metoda|Co należy zrobić|
|---|---|
|Wiersz polecenia|1. Na urządzeniu Windows otwórz wiersz polecenia.<br/><br/>2. Wpisz `sc query windefend`, a następnie naciśnij klawisz Enter.<br/><br/>3. Przejrzyj wyniki, aby sprawdzić, czy Program antywirusowy Microsoft Defender działa w trybie pasywnym.|
|PowerShell|1. Na Windows otwórz Windows PowerShell administratora.<br/><br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. Przejrzyj wyniki. Powinien być wyświetlony tryb **pasywny**.|
|Zabezpieczenia Windows aplikacji|1. Na Windows otwórz aplikację Zabezpieczenia Windows urządzenia.<br/><br/>2. Wybierz **pozycję Ochrona przed & zagrożeniami**.<br/><br/>3. **W KtoTo chroni mnie? wybierz** pozycję **Zarządzaj dostawcami**.<br/><br/>4. Na stronie **Dostawcy** zabezpieczeń w obszarze **Oprogramowanie antywirusowe** sprawdź, **czy Program antywirusowy Microsoft Defender jest włączona**.|
|Menedżer zadań|1. Na Windows otwórz aplikację Menedżer zadań.<br/><br/>2. Wybierz **kartę** Szczegóły. Poszukaj **MsMpEng.exe** na liście.|

> [!NOTE]
> W niektórych *Program antywirusowy Windows Defender* *plików może* Program antywirusowy Microsoft Defender być Windows.
> Aby dowiedzieć się więcej o trybie pasywnym i aktywnym, zobacz [Więcej informacji o Program antywirusowy Microsoft Defender stanach](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Ręczne Program antywirusowy Microsoft Defender ustawienia trybu Windows serwera na tryb pasywny

Aby ustawić Program antywirusowy Microsoft Defender na pasywny w Windows Server, wersji 1803 lub nowszej albo Windows Server 2019 lub Windows Server 2022, wykonaj następujące czynności:

1. Otwórz Edytor rejestru, a następnie przejdź do:

   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Edytuj (lub utwórz) wpis DWORD o nazwie **ForceDefenderPassiveMode** i określ następujące ustawienia:
   - Ustaw wartość dword na **1**.
   - W **obszarze Podstawa** wybierz **pozycję Szesnastkowy**.

> [!NOTE]
> Klucz rejestru można ustawić innymi metodami, takimi jak:
>
> - [zasady grupy preferencja](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [Local zasady grupy Object tool](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [Pakiet w programie Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Rozpoczynanie Program antywirusowy Microsoft Defender dnia Windows Server 2016

Jeśli korzystasz z Windows Server 2016, może być konieczne ręczne Program antywirusowy Microsoft Defender urządzenia. To zadanie można wykonać przy użyciu polecenia cmdlet `mpcmdrun.exe -wdenable` programu PowerShell na urządzeniu.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Pobierz aktualizacje dla Program antywirusowy Microsoft Defender

Zapewnienie Program antywirusowy Microsoft Defender na bieżąco jest niezbędne do zapewnienia, że Twoje urządzenia mają najnowsze technologie i funkcje potrzebne do ochrony przed nowym złośliwym oprogramowaniem i technikami ataków, nawet Program antywirusowy Microsoft Defender działa w trybie pasywnym. (Zobacz [Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md)).

Istnieją dwa typy aktualizacji związanych z Program antywirusowy Microsoft Defender aktualnymi aktualizacjami:

- Aktualizacje analizy zabezpieczeń
- Aktualizacje produktów

Aby pobrać aktualizacje, postępuj zgodnie ze wskazówkami w te [Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>Odinstaluj rozwiązanie inne niż firmy Microsoft

Jeśli na tym etapie masz:

- urządzenia organizacji do usługi Defender for Endpoint i
- Program antywirusowy Microsoft Defender jest zainstalowana i włączona,

Następnie następnym krokiem jest odinstalowanie rozwiązania antywirusowego, ochrony przed złośliwym oprogramowaniem i rozwiązania firmy Microsoft do ochrony przed złośliwym oprogramowaniem. Po odinstalowaniu rozwiązania firmy innym niż firma Microsoft tryb Program antywirusowy Microsoft Defender z trybu pasywnego do trybu aktywnego. W większości przypadków odbywa się to automatycznie. 

> [!IMPORTANT]
> Jeśli z jakiegoś powodu program Program antywirusowy Microsoft Defender nie przejść w tryb aktywny po odinstalowaniu rozwiązania niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft, zobacz wygląda na to, że program Program antywirusowy Microsoft Defender jest zablokowany w trybie [pasywnym](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

Aby uzyskać pomoc w odinstalowaniu rozwiązania firmy innych niż Microsoft, skontaktuj się z jego zespołem pomocy technicznej.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Upewnij się, że program Defender for Endpoint działa poprawnie

Po doinstalowaniu usługi Defender for Endpoint i odinstalowaniu rozwiązania, które było wcześniej inne niż firma Microsoft, następnym krokiem jest upewninie się, że program Defender for Endpoint działa poprawnie. Dobrym sposobem wykonania tego zadania jest odwiedzenie witryny scenariuszy pokazu programu Defender dla punktu końcowego ([https://demo.wd.microsoft.com](https://demo.wd.microsoft.com)). Wypróbuj jeden lub więcej scenariuszy pokazu na tej stronie, w tym co najmniej następujące:

- Ochrona w chmurze
- Potencjalnie niechciane aplikacje (PUA)
- Network Protection (NP)

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="next-steps"></a>Następne kroki

**Gratulacje**! Ukończono migrację [do usługi Defender dla punktu końcowego](switch-to-mde-overview.md#the-migration-process)!

- [Odwiedź pulpit nawigacyjny operacji zabezpieczeń](security-operations-dashboard.md) w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)).
- [Zarządzanie programem Defender dla punktu końcowego po migracji](manage-mde-post-migration.md).
