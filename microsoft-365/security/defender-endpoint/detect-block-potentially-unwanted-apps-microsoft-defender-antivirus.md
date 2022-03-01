---
title: Blokowanie potencjalnie niechcianych aplikacji za pomocą Program antywirusowy Microsoft Defender
description: Włącz potencjalnie niechcianą funkcję antywirusową (PUA), aby blokować niechciane oprogramowanie, takie jak np.
keywords: pua, enable, unwanted software, unwanted apps, google, browser toolbar, detect, block, Program antywirusowy Microsoft Defender
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
ms.date: 10/18/2021
ms.collection: m365-security-compliance
ms.openlocfilehash: b193279f9891badc78e639776a57a366a0fa8109
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014681"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>Wykrywanie i blokowanie potencjalnie niechcianych aplikacji

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)

Potencjalnie niechciane aplikacje (PUA) to kategoria oprogramowania, która może powodować powolne uruchamianie komputera, wyświetlanie nieoczekiwanych reklam lub w najgorszej sytuacji zainstalowanie innego oprogramowania, które może być nieoczekiwane lub niechciane. Ochrona pua nie jest traktowana jako wirus, złośliwe oprogramowanie ani inny rodzaj zagrożenia, ale może wykonywać akcje dotyczące punktów końcowych, które negatywnie wpływają na wydajność lub używanie punktów końcowych. Termin *"PUA* " może również odnosić się do aplikacji o słabej reputacji, jak ocenia program Microsoft Defender for Endpoint ze względu na określone rodzaje zachowań osób.

Oto kilka przykładów:

- **Oprogramowanie reklamowe** wyświetlace reklamy lub promocje, w tym oprogramowanie, które wstawia reklamy do stron internetowych.
- **Tworzenie pakietu oprogramowania udostępniacego** do instalowania innego oprogramowania, które nie jest podpisane cyfrowo przez tę samą jednostkę. Ponadto oprogramowanie udostępniające możliwość zainstalowania innego oprogramowania, które kwalifikuje się jako pakiet PUA.
- **Wsadowy** oprogramowania, które aktywnie próbuje wykrywać wykrycie przez produkty zabezpieczające, w tym oprogramowanie, które działa inaczej w obecności produktów zabezpieczających.

> [!TIP]
> Aby uzyskać więcej przykładów i omówienie kryteriów, za pomocą których oznaczamy aplikacje w celu zwrócenia specjalnej uwagi na funkcje zabezpieczeń, zobacz Jak firma Microsoft identyfikuje złośliwe oprogramowanie i [potencjalnie niechciane aplikacje](/windows/security/threat-protection/intelligence/criteria).

Potencjalnie niechciane aplikacje mogą zwiększyć ryzyko zainfekowania sieci rzeczywistym złośliwym oprogramowaniem, utrudnić identyfikację złośliwego oprogramowania lub zmarnować zasoby IT w oczyszczaniu. Ochrona za Windows 10 PUA jest obsługiwana w Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 i Windows Server 2016. W Windows 10 (w wersji 2004 i nowszej) program Program antywirusowy Microsoft Defender blokuje aplikacje, które są domyślnie traktowane jako tryb PUA dla urządzeń z systemem Enterprise (E5).

## <a name="microsoft-edge"></a>Microsoft Edge

Nowa [Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea), która jest oparta Chromium, blokuje potencjalnie niechciane pobieranie aplikacji i skojarzone adresy URL zasobów. Ta funkcja jest dostępna za [pośrednictwem Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Włączanie ochrony za Chromium pua w Microsoft Edge

Mimo że potencjalnie niechciana ochrona aplikacji w programie Microsoft Edge (opartym na systemie Chromium wersja 80.0.361.50) jest domyślnie wyłączona, można ją łatwo włączona z poziomu przeglądarki.

1. W przeglądarce Edge wybierz wielokropek, a następnie **wybierz pozycję Ustawienia**.

2. Wybierz **prywatność, wyszukiwanie i usługi**.

3. W sekcji **Zabezpieczenia** włącz opcję **Blokuj potencjalnie niechciane aplikacje**.

> [!TIP]
> Jeśli używasz programu Microsoft Edge (opartego na programie Chromium), możesz bezpiecznie korzystać z funkcji blokowania adresów URL funkcji ochrony za pomocą oprogramowania PUA, testując ją na jednej ze stron Microsoft Defender SmartScreen [pokazowych](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Blokowanie adresów URL przy użyciu Microsoft Defender SmartScreen

W Chromium Edge z włączonym zabezpieczeniem przed pua (PUA) Microsoft Defender SmartScreen przed adresami URL skojarzonymi z pua.

Administratorzy zabezpieczeń mogą [skonfigurować Microsoft Edge](/DeployEdge/configure-microsoft-edge) i Microsoft Defender SmartScreen, aby chronić grupy użytkowników przed adresami URL skojarzonymi z interfejsem PUA. Istnieje kilka ustawień [zasad grupy jawnie dotyczących](/DeployEdge/microsoft-edge-policies#smartscreen-settings) Microsoft Defender SmartScreen, w tym jedno [na blokowanie oprogramowania pua](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). Ponadto administratorzy mogą skonfigurować [Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) jako całość, używając ustawień zasad grupy w celu Microsoft Defender SmartScreen lub wyłączenia.

Chociaż program Microsoft Defender for Endpoint ma własną listę zablokowanych danych opartą na zestawie danych zarządzanych przez firmę Microsoft, możesz dostosować tę listę na podstawie swojej analizy zagrożeń. Jeśli [tworzysz wskaźniki i zarządzasz](manage-indicators.md) nimi w portalu programu Microsoft Defender for Endpoint, Microsoft Defender SmartScreen z nowymi ustawieniami.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>Program antywirusowy Microsoft Defender i ochrona przed pua

Potencjalnie niechciana funkcja ochrony aplikacji (PUA) w programie Program antywirusowy Microsoft Defender może wykrywać i blokować funkcję PUA na punktach końcowych w sieci.

> [!NOTE]
> Ta funkcja jest dostępna w Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 i Windows Server 2016.

Program antywirusowy Microsoft Defender plików pua i wszelkich prób ich pobrania, przeniesienia, uruchomienia lub zainstalowania. Zablokowane pliki pua są następnie przenoszone do kwarantanny. Po wykryciu pliku pua w punkcie końcowym program Program antywirusowy Microsoft Defender wysyła powiadomienie do [użytkownika (o](configure-notifications-microsoft-defender-antivirus.md) ile powiadomienia nie zostały wyłączone w tym samym formacie co inne wykrywanie zagrożeń. Powiadomienie jest poprzedzone wstępnie informacjami o `PUA:` jego zawartości.

Powiadomienie zostanie wyświetlone na zwykłej liście [kwarantanny w Zabezpieczenia Windows aplikacji](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Konfigurowanie ochrony za Program antywirusowy Microsoft Defender

Ochronę za pomocą funkcji PUA można włączyć [Microsoft Intune,](/mem/intune/protect/device-protect) [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection), [zasady grupy](/azure/active-directory-domain-services/manage-group-policy) lub za pomocą poleceń [cmdlet programu PowerShell](/powershell/module/defender/?preserve-view=true&view=win10-ps).

Możesz również użyć funkcji ochrony przed zagrożeniami dla użytkownika w trybie inspekcji, aby wykrywać potencjalnie niechciane aplikacje bez ich blokowania. Wykrywanie jest przechwytywane w dzienniku Windows zdarzeń.

> [!TIP]
> Odwiedź witrynę pokazową programu Microsoft Defender for Endpoint w witrynie [demo.wd.microsoft.com](https://demo.wd.microsoft.com/Page/UrlRep) , aby sprawdzić, czy ta funkcja działa, i zobaczyć ją w działaniu.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Ochrona oprogramowania PUA w trybie inspekcji jest przydatna, jeśli Twoja firma przeprowadza wewnętrzny test zgodności oprogramowania i chcesz uniknąć wyników fałszywie dodatnich.

### <a name="use-intune-to-configure-pua-protection"></a>Konfigurowanie ochrony za pomocą usługi Intune

Aby [uzyskać więcej szczegółowych](/intune/device-restrictions-configure) informacji, Microsoft Intune konfigurować ustawienia ograniczeń urządzeń Microsoft Intune i Program antywirusowy Microsoft Defender urządzenia dla aplikacji [Windows 10 Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### <a name="use-configuration-manager-to-configure-pua-protection"></a>Konfigurowanie ochrony Menedżer konfiguracji pua przy użyciu funkcji

Ochrona za pomocą funkcji PUA jest domyślnie włączona w Microsoft Endpoint Manager (Bieżąca gałąź).

Zobacz [Jak tworzyć i wdrażać](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) zasady ochrony przed złośliwym kodem: Ustawienia skanowania według harmonogramu są skanowane według harmonogramu, aby uzyskać szczegółowe informacje na temat Microsoft Endpoint Manager (Bieżąca gałąź).

Aby System Center 2012 Menedżer konfiguracji, zobacz Jak wdrożyć potencjalnie niechciane zasady ochrony aplikacji Endpoint Protection w [programie Menedżer konfiguracji](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> Zdarzenia puA blokowane przez użytkowników Program antywirusowy Microsoft Defender są raportowane w przeglądarce Windows zdarzeń, a nie w przeglądarce Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>Konfigurowanie ochrony zasady grupy pua za pomocą funkcji zabezpieczeń

1. Pobieranie i instalowanie [szablonów administracyjnych (admx) Windows 10 października 2020 r. (20H2)](https://www.microsoft.com/download/details.aspx?id=102157)

2. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. Zaznacz zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

4. W **edytorze zasady grupy zarządzaniem** przejdź do **strony Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

5. Rozwiń drzewo, **aby Windows składniki** \> **Program antywirusowy Microsoft Defender**.

6. Kliknij dwukrotnie pozycję **Konfiguruj wykrywanie dla potencjalnie niechcianych aplikacji**.

7. Wybierz **pozycję Włączone,** aby włączyć ochronę przed pua.

8. W **menu** Opcje wybierz pozycję **Blokuj,** aby zablokować potencjalnie niechciane aplikacje, lub wybierz pozycję Tryb inspekcji, aby sprawdzić działanie ustawienia w środowisku. Wybierz przycisk **OK**.

9. Wdeksuj zasady grupy obiekt tak jak zwykle.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>Konfigurowanie ochrony za pomocą poleceń cmdlet programu PowerShell

#### <a name="to-enable-pua-protection"></a>Aby włączyć ochronę przed pua

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Ustawienie wartości tego polecenia cmdlet w celu `Enabled` wyłączenia tej funkcji.

#### <a name="to-set-pua-protection-to-audit-mode"></a>Aby ustawić ochronę przed zabezpieczeniami pua w trybie inspekcji

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Ustawienie `AuditMode` wykrywa blokadę pua bez ich blokowania.

#### <a name="to-disable-pua-protection"></a>Aby wyłączyć ochronę przed pua

Zalecamy, aby włączona ochrona przed zabezpieczeniami po wyzysku (PUA). Można go jednak wyłączyć za pomocą następującego polecenia cmdlet:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

Ustawienie wartości tego polecenia cmdlet w celu `Disabled` wyłączenia tej funkcji, jeśli została ona włączona.

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) do konfigurowania i uruchamiania Program antywirusowy Microsoft Defender i poleceń [cmdlet programu antywirusowego Defender](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>Wyświetlanie zdarzeń interfejsu PUA przy użyciu programu PowerShell

Zdarzenia pua są zgłaszane w podglądzie Windows zdarzeń, ale nie są Microsoft Endpoint Manager ani w usłudze Intune. Za pomocą polecenia `Get-MpThreat` cmdlet można także wyświetlać zagrożenia, Program antywirusowy Microsoft Defender obsługiwane. Oto przykład:

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

## <a name="get-email-notifications-about-pua-detections"></a>Powiadomienia e-mail o wykryciu pua

Aby odbierać wiadomości e-mail z powiadomieniami o wykryciu pua, można włączyć powiadomienia e-mail.

Zobacz [Rozwiązywanie problemów z identyfikatorami zdarzeń](troubleshoot-microsoft-defender-antivirus.md), aby uzyskać szczegółowe informacje na temat Program antywirusowy Microsoft Defender zdarzeń. Zdarzenia pua są rejestrowane pod identyfikatorem **zdarzenia 1160**.

## <a name="view-pua-events-using-advanced-hunting"></a>Wyświetlanie wydarzeń pua przy użyciu zaawansowanego wyszukiwania

Jeśli korzystasz z programu [Microsoft Defender dla punktu końcowego](microsoft-defender-endpoint.md), możesz wyświetlać zdarzenia pua za pomocą zaawansowanego zapytania myśliwskiego. Oto przykładowe zapytanie:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Aby dowiedzieć się więcej na temat zaawansowanego wyszukiwania, zobacz [Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>Wykluczanie plików z ochrony przed pua

Czasami ochrona funkcji pua jest błędnie blokowana przez funkcję pua lub do wykonania zadania jest wymagana funkcja tego poziomu. W takich przypadkach plik można dodać do listy wykluczeń.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia pliku i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Zobacz też

- [Ochrona następnej generacji](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurowanie ochrony zachowanie, heuristic i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md)
