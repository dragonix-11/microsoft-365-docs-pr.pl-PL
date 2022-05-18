---
title: Blokuj potencjalnie niechciane aplikacje za pomocą Program antywirusowy Microsoft Defender
description: Włącz funkcję ochrony antywirusowej potencjalnie niechcianej aplikacji (PUA), aby blokować niepożądane oprogramowanie, takie jak adware.
keywords: pua, enable, unwanted software, unwanted apps, adware, browser toolbar, detect, block, Program antywirusowy Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: detect
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
audience: ITPro
ms.reviewer: mimilone, julih
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: d93587867a2fea0921a1ac9711eed0f8c1b1beec
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468311"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>Wykryj i blokuj potencjalnie niechciane aplikacje

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Potencjalnie niechciane aplikacje (PUA) to kategoria oprogramowania, która może powodować powolne uruchamianie maszyny, wyświetlanie nieoczekiwanych reklam lub w najgorszym przypadku instalowanie innego oprogramowania, które może być nieoczekiwane lub niepożądane. Usługa PUA nie jest uważana za wirus, złośliwe oprogramowanie ani inny typ zagrożenia, ale może wykonywać akcje w punktach końcowych, które niekorzystnie wpływają na wydajność lub użycie punktu końcowego. Termin *PUA* może również odnosić się do aplikacji, która ma słabą reputację, ocenianą przez Ochrona punktu końcowego w usłudze Microsoft Defender, ze względu na pewne rodzaje niepożądanego zachowania.

Oto kilka przykładów:

- **Oprogramowanie reklamowe** , które wyświetla reklamy lub promocje, w tym oprogramowanie, które wstawia reklamy do stron internetowych.
- **Łączenie oprogramowania** , które oferuje instalację innego oprogramowania, które nie jest podpisane cyfrowo przez tę samą jednostkę. Ponadto oprogramowanie, które oferuje instalację innego oprogramowania, które kwalifikuje się jako PUA.
- **Oprogramowanie do unikania opodatkowania** , które aktywnie próbuje uniknąć wykrycia przez produkty zabezpieczające, w tym oprogramowanie, które zachowuje się inaczej w obecności produktów zabezpieczających.

> [!TIP]
> Aby uzyskać więcej przykładów i omówić kryteria, których używamy do etykietowania aplikacji w celu zwrócenia szczególnej uwagi z funkcji zabezpieczeń, zobacz [Jak firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje](/windows/security/threat-protection/intelligence/criteria).

Potencjalnie niechciane aplikacje mogą zwiększyć ryzyko zainfekowania sieci rzeczywistym złośliwym oprogramowaniem, utrudnić identyfikację infekcji złośliwym oprogramowaniem lub zmarnować zasoby IT podczas ich czyszczenia. Ochrona pua jest obsługiwana na Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 i Windows Server 2016. W Windows 10 (wersja 2004 lub nowsza) Program antywirusowy Microsoft Defender domyślnie blokuje aplikacje uznawane za pua dla urządzeń Enterprise (E5).

## <a name="microsoft-edge"></a>Microsoft Edge

[Nowa Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea) oparta na Chromium blokuje potencjalnie niepożądane pliki do pobrania aplikacji i skojarzone adresy URL zasobów. Ta funkcja jest udostępniana za pośrednictwem [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Włączanie ochrony pua w Microsoft Edge opartym na Chromium

Mimo że potencjalnie niepożądana ochrona aplikacji w Microsoft Edge (oparta na Chromium wersji 80.0.361.50) jest domyślnie wyłączona, można ją łatwo włączyć z poziomu przeglądarki.

1. W przeglądarce Edge wybierz wielokropek, a następnie wybierz **pozycję Ustawienia**.

2. Wybierz pozycję **Prywatność, wyszukiwanie i usługi**.

3. W sekcji **Zabezpieczenia** włącz opcję **Blokuj potencjalnie niechciane aplikacje**.

> [!TIP]
> Jeśli korzystasz z Microsoft Edge (opartej na Chromium), możesz bezpiecznie zapoznać się z funkcją blokowania adresów URL ochrony pua, testując ją na jednej z naszych [Microsoft Defender SmartScreen stron demonstracyjnych](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Blokuj adresy URL przy użyciu Microsoft Defender SmartScreen

W Chromium edge z włączoną ochroną pua Microsoft Defender SmartScreen chroni przed adresami URL skojarzonymi z pua.

Administratorzy zabezpieczeń mogą [skonfigurować](/DeployEdge/configure-microsoft-edge) sposób współpracy Microsoft Edge i Microsoft Defender SmartScreen w celu ochrony grup użytkowników przed adresami URL skojarzonymi z pua. Istnieje kilka [ustawień zasad grupy](/DeployEdge/microsoft-edge-policies#smartscreen-settings) jawnie dla Microsoft Defender SmartScreen dostępne, w tym [jeden do blokowania PUA](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). Ponadto administratorzy mogą [skonfigurować Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) jako całość przy użyciu ustawień zasad grupy, aby włączyć lub wyłączyć Microsoft Defender SmartScreen.

Mimo że Ochrona punktu końcowego w usłudze Microsoft Defender ma własną listę blokową opartą na zestawie danych zarządzanym przez firmę Microsoft, możesz dostosować tę listę na podstawie własnej analizy zagrożeń. Jeśli [tworzysz wskaźniki i zarządzasz nimi](manage-indicators.md) w portalu Ochrona punktu końcowego w usłudze Microsoft Defender, Microsoft Defender SmartScreen przestrzega nowych ustawień.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>ochrona Program antywirusowy Microsoft Defender i pua

Funkcja ochrony potencjalnie niechcianej aplikacji (PUA) w Program antywirusowy Microsoft Defender może wykrywać i blokować pua w punktach końcowych w sieci.

> [!NOTE]
> Ta funkcja jest dostępna w Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 i Windows Server 2016.

Program antywirusowy Microsoft Defender bloki wykryły pliki PUA oraz wszelkie próby ich pobrania, przeniesienia, uruchomienia lub zainstalowania. Zablokowane pliki PUA są następnie przenoszone do kwarantanny. Po wykryciu pliku PUA w punkcie końcowym Program antywirusowy Microsoft Defender wysyła powiadomienie do użytkownika ([chyba że powiadomienia zostały wyłączone](configure-notifications-microsoft-defender-antivirus.md) w tym samym formacie co inne wykrycia zagrożeń. Powiadomienie jestpoprzee `PUA:` , aby wskazać jego zawartość.

Powiadomienie zostanie wyświetlone na [zwykłej liście kwarantanny w aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Konfigurowanie ochrony pua w Program antywirusowy Microsoft Defender

Ochronę pua można włączyć za pomocą [Microsoft Intune](/mem/intune/protect/device-protect), [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection), [zasady grupy](/azure/active-directory-domain-services/manage-group-policy) lub za pomocą [poleceń cmdlet programu PowerShell](/powershell/module/defender/?preserve-view=true&view=win10-ps).

Można również użyć ochrony pua w trybie inspekcji do wykrywania potencjalnie niechcianych aplikacji bez blokowania ich. Wykrycia są przechwytywane w dzienniku zdarzeń Windows.

> [!TIP]
> Odwiedź witrynę internetową Ochrona punktu końcowego w usłudze Microsoft Defender demo pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com/Page/UrlRep), aby potwierdzić, że funkcja działa i zobaczyć ją w akcji.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Ochrona pua w trybie inspekcji jest przydatna, jeśli firma przeprowadza wewnętrzną kontrolę zgodności z zabezpieczeniami oprogramowania i chcesz uniknąć wyników fałszywie dodatnich.

### <a name="use-intune-to-configure-pua-protection"></a>Konfigurowanie ochrony pua przy użyciu Intune

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w ustawieniach](/intune/device-restrictions-configure) ograniczeń urządzeń Microsoft Intune i [Program antywirusowy Microsoft Defender dla Windows 10 w Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### <a name="use-configuration-manager-to-configure-pua-protection"></a>Konfigurowanie ochrony pua przy użyciu Configuration Manager

Ochrona pua jest domyślnie włączona w Microsoft Endpoint Manager (Current Branch).

Zobacz [Jak utworzyć i wdrożyć zasady ochrony przed złośliwym kodem: zaplanowane skanowanie ustawień](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings), aby uzyskać szczegółowe informacje na temat konfigurowania Microsoft Endpoint Manager (Current Branch).

Aby uzyskać System Center 2012 Configuration Manager, zobacz [How to Deploy Potentially Unwanted Application Protection Policy for Endpoint Protection in Configuration Manager (Jak wdrożyć potencjalnie niepożądane zasady ochrony aplikacji dla Endpoint Protection w Configuration Manager](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA)).

> [!NOTE]
> Zdarzenia pua zablokowane przez Program antywirusowy Microsoft Defender są zgłaszane w Windows Podgląd zdarzeń, a nie w Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>Konfigurowanie ochrony pua przy użyciu zasady grupy

1. Pobierz i zainstaluj [szablony administracyjne (.admx) dla Windows 11 aktualizacji z października 2021 r. (21H2)](https://www.microsoft.com/download/details.aspx?id=103507)

2. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. Wybierz obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

4. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

5. Rozwiń drzewo, aby **Program antywirusowy Microsoft Defender składniki** \> **Windows**.

6. Kliknij **dwukrotnie pozycję Konfiguruj wykrywanie potencjalnie niechcianych aplikacji**.

7. Wybierz pozycję **Włączone** , aby włączyć ochronę pua.

8. W **obszarze Opcje** wybierz pozycję **Blokuj** , aby zablokować potencjalnie niepożądane aplikacje, lub wybierz pozycję **Tryb inspekcji** , aby przetestować działanie tego ustawienia w środowisku. Wybierz przycisk **OK**.

9. Wdróż obiekt zasady grupy tak jak zwykle.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>Konfigurowanie ochrony pua przy użyciu poleceń cmdlet programu PowerShell

#### <a name="to-enable-pua-protection"></a>Aby włączyć ochronę pua

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Ustawienie wartości dla tego polecenia cmdlet `Enabled` powoduje włączenie funkcji, jeśli została wyłączona.

#### <a name="to-set-pua-protection-to-audit-mode"></a>Aby ustawić ochronę pua na tryb inspekcji

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Ustawienie `AuditMode` wykrywa puas bez blokowania ich.

#### <a name="to-disable-pua-protection"></a>Aby wyłączyć ochronę pua

Zalecamy włączenie ochrony pua. Można go jednak wyłączyć przy użyciu następującego polecenia cmdlet:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

Ustawienie wartości dla tego polecenia cmdlet `Disabled` powoduje wyłączenie funkcji, jeśli została włączona.

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet Program antywirusowy Microsoft Defender i defender antivirus](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>Wyświetlanie zdarzeń pua przy użyciu programu PowerShell

Zdarzenia pua są zgłaszane w Windows Podgląd zdarzeń, ale nie w Microsoft Endpoint Manager lub w Intune. Możesz również użyć `Get-MpThreat` polecenia cmdlet, aby wyświetlić zagrożenia, które Program antywirusowy Microsoft Defender obsługiwane. Oto przykład:

```console
CategoryID       : 27
DidThreatExecute : False
IsActive         : False
Resources        : {webfile:_q:\Builds\Dalton_Download_Manager_3223905758.exe|http://d18yzm5yb8map8.cloudfront.net/
                    fo4yue@kxqdw/Dalton_Download_Manager.exe|pid:14196,ProcessStart:132378130057195714}
RollupStatus     : 33
SchemaVersion    : 1.0.0.0
SeverityID       : 1
ThreatID         : 213927
ThreatName       : PUA:Win32/InstallCore
TypeID           : 0
PSComputerName   :
```

## <a name="get-email-notifications-about-pua-detections"></a>Pobieranie powiadomień e-mail dotyczących wykrywania pua

Możesz włączyć powiadomienia e-mail, aby otrzymywać wiadomości e-mail dotyczące wykrywania pua.

Aby uzyskać szczegółowe informacje na temat wyświetlania zdarzeń Program antywirusowy Microsoft Defender, zobacz [Rozwiązywanie problemów z identyfikatorami zdarzeń](troubleshoot-microsoft-defender-antivirus.md). Zdarzenia PUA są rejestrowane pod identyfikatorem zdarzenia **1160**.

## <a name="view-pua-events-using-advanced-hunting"></a>Wyświetlanie zdarzeń PUA przy użyciu zaawansowanego wyszukiwania zagrożeń

Jeśli używasz [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md), możesz użyć zaawansowanego zapytania wyszukiwania zagrożeń, aby wyświetlić zdarzenia PUA. Oto przykładowe zapytanie:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Aby dowiedzieć się więcej na temat zaawansowanego wyszukiwania zagrożeń, zobacz [Proaktywne wyszukiwanie zagrożeń przy użyciu zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>Wykluczanie plików z ochrony pua

Czasami plik jest błędnie blokowany przez ochronę pua lub funkcja pua jest wymagana do wykonania zadania. W takich przypadkach plik można dodać do listy wykluczeń.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia pliku i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Ochrona nowej generacji](microsoft-defender-antivirus-in-windows-10.md)
- [Konfiguruj ochronę behawioralną, heurystyczną i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md)
