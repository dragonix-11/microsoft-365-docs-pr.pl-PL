---
title: Migrowanie z reguł HIPS innych firm do reguł ASR
description: W tym artykule opisano, jak podejście do migracji z rozwiązania SYSTEMU HIPS (Host Intrusion Prevention System) innej firmy do reguł ASR.
keywords: Reguły zmniejszania powierzchni ataków, reguły asr, zasady asr, hips, host intrusion prevention system, reguły ochrony, ochrona przed wirusami, ochrona przed wirusami, wykorzystywanie, zapobieganie powstawaniu wirusów, program Microsoft Defender for Endpoint
ms.topic: article
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 2530f38bdcfdbb74bdd9a80c59c53c9e273e1449
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2021
ms.locfileid: "63018925"
---
# <a name="migrating-from-a-third-party-hips-to-asr-rules"></a>Migrowanie z reguł HIPS innych firm do reguł ASR

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ten artykuł ułatwia mapowanie typowych reguł na usługę Microsoft Defender for Endpoint.

## <a name="scenarios-when-migrating-from-a-third-party-hips-product-to-asr-rules"></a>Scenariusze migrowania z produktu HIPS innej firmy do reguł ASR

### <a name="block-creation-of-specific-files"></a>Blokowanie tworzenia określonych plików

- **Dotyczy wszystkich** procesów
- **Operation** — tworzenie plików
- Przykłady plików/folderów, kluczy rejestru **/wartości, procesów,** usług- *.zepto, *.odin, *.locky, *.jaff, *.lukitus, *.wnry, *.bangkok
- **Reguły zmniejszania powierzchni ataków —** reguły ASR blokują techniki ataków, a nie wskaźniki naruszenia (IOC, Indicators of Compromise). Zablokowanie określonego rozszerzenia pliku nie zawsze jest przydatne, ponieważ nie zapobiega utracie bezpieczeństwa urządzenia. Atak został tylko częściowo udaremniany do momentu utworzenia przez atakujących nowego typu rozszerzenia dla  payload.
- **Inne zalecane funkcje:** zdecydowanie zalecane jest posiadanie programu Microsoft Defender AV oraz funkcji ochrona w chmurze i analiza zachowania. Zalecamy korzystanie z innych środków zapobiegania, takich jak reguła ASR "Użyj zaawansowanej ochrony przed oprogramowaniem wymuszającym okup". Zapewnia to większy poziom ochrony przed atakami oprogramowania wymuszającego okup. Ponadto wiele z tych kluczy rejestru jest monitorowanych przez program Microsoft Defender for Endpoint, takich jak techniki ASEP, które powodują wyzwolenie określonych alertów. Używane klucze rejestru wymagają co najmniej uprawnień Administratora lokalnego lub Zaufanego instalatora. Zaleca się używanie zablokowanego środowiska z minimalnymi kontami administracyjnymi lub uprawnieniami. Inne konfiguracje systemu, w tym "Wyłączanie usługi SeDebug dla nie wymaganych ról", są częścią naszych szerszej rekomendacji dotyczących zabezpieczeń.

### <a name="block-creation-of-specific-registry-keys"></a>Blokowanie tworzenia określonych kluczy rejestru

- **Dotyczy wszystkich** procesów
- **Procesy** — nie nasyć
- **Operacja** — modyfikacje rejestru
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów, usług**-  *\* Software,HKCU\Environment\UserInitMprLogonScript,HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs *\StartExe, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger, HKEY_CURRENT_USER\Software\Microsoft\HtmlHelp Author\location, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcess
- **Reguły zmniejszania powierzchni ataków —** reguły ASR blokują techniki ataków, a nie wskaźniki naruszenia (IOC, Indicators of Compromise). Zablokowanie określonego rozszerzenia pliku nie zawsze jest przydatne, ponieważ nie zapobiega utracie bezpieczeństwa urządzenia. Atak został tylko częściowo udaremniany do momentu utworzenia przez atakujących nowego typu rozszerzenia dla  payload.
- **Inne zalecane funkcje:** zdecydowanie zalecane jest posiadanie programu Microsoft Defender AV oraz funkcji ochrona w chmurze i analiza zachowania. Zalecamy korzystanie z dodatkowej ochrony, takiej jak reguła ASR "Użyj zaawansowanej ochrony przed oprogramowaniem wymuszającym okup". Zapewnia to większy poziom ochrony przed atakami oprogramowania wymuszającego okup. Ponadto kilka z tych kluczy rejestru jest monitorowanych przez program Microsoft Defender for Endpoint, takich jak techniki ASEP, które powodują wyzwolenie określonych alertów. Ponadto używane klucze rejestru wymagają co najmniej uprawnień Administratora lokalnego lub Zaufanego instalatora. Zaleca się używanie zablokowanego środowiska z minimalnymi kontami administracyjnymi lub uprawnieniami. Inne konfiguracje systemu, w tym "Wyłączanie usługi SeDebug dla nie wymaganych ról", są częścią naszych szerszej rekomendacji dotyczących zabezpieczeń.

### <a name="block-untrusted-programs-from-running-from-removable-drives"></a>Blokowanie uruchamiania niezaufanych programów z dysków wymiennych

- **Dotyczy niezaufanych** programów usb
- **Procesy**- *
- **Operacja** — wykonywanie procesu
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów, usług:-*
- Reguły zmniejszania powierzchni podczas ataków — reguły ASR mają wbudowaną regułę zapobiegającą uruchamianiu niezaufanych i niepodpisanych programów z dysków wymiennych: "Blokuj niezaufane i niepodpisane procesy uruchamiane przez USB", IDENTYFIKATOR GUID "b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4".
- **Inne zalecane funkcje**— zapoznaj się z dodatkowymi kontrolkami dla urządzeń USB i innych nośników wymiennych przy użyciu programu Microsoft Defender for Endpoint:Jak sterować urządzeniami USB i innymi nośnikami wymiennymi przy użyciu programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/device-control/control-usb-devices-using-intune).

### <a name="block-mshta-from-launching-certain-child-processes"></a>Blokowanie uruchamiania określonych procesów podrzędnych przez mshtę

- **Dotyczy:** - Mshta
- **Procesy** — mshta.exe
- **Operacja** — wykonywanie procesu
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów,** usług powershell.exe, cmd.exe, regsvr32.exe
- **Reguły ograniczania powierzchni** ataków — reguły ASR nie zawierają żadnej konkretnej reguły uniemożliwiającej procesom podrzędnym "mshta.exe". Ta kontrolka nie podlega prawu exploit protection ani Windows Defender kontroli aplikacji.
- **Inne zalecane funkcje** — włącz Windows Defender sterowania aplikacją, aby uniemożliwić mshta.exe całkowicie wykonywana. Jeśli organizacja wymaga "mshta.exe" dla aplikacji biznesowych, skonfiguruj określoną regułę Windows Defender Exploit Protection, aby uniemożliwić uruchamianie procesów mshta.exe podrzędnego.

### <a name="block-outlook-from-launching-child-processes"></a>Blokowanie Outlook z uruchamianiem procesów podrzędnych

- **Dotyczy-** Outlook
- **Procesy** — outlook.exe
- **Operacja** — wykonywanie procesu
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów, usług** i powershell.exe
- Reguły zmniejszania powierzchni w atakach — reguły asr mają wbudowaną regułę uniemożliwiającą aplikacjom do komunikacji programu Office (Outlook, Skype i Teams) uruchamianie procesów podrzędnych: Office "Blokowanie tworzenia procesów podrzędnych przez aplikację do komunikacji", IDENTYFIKATOR GUID "26190899-1602-49e8-8b27-eb1d0a1ce869".
- **Inne zalecane funkcje —** zalecamy włączenie trybu języka ograniczonego programu PowerShell w celu zminimalizowania ataków z programu PowerShell.

### <a name="block-office-apps-from-launching-child-processes"></a>Blokowanie Office uruchamianie procesów podrzędnych przez aplikacje

- **Dotyczy:** Office
- **Procesy** — winword.exe, powerpnt.exe, excel.exe
- **Operacja** — wykonywanie procesu
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów,** usług powershell.exe, cmd.exe, wscript.exe, mshta.exe, EQNEDT32.EXE i regsrv32.exe
- Reguły zmniejszania powierzchni w atakach — reguły ASR mają wbudowaną regułę zapobiegającą uruchamianiu procesów podrzędnych przez aplikacje pakietu Office: "Blokuj wszystkie aplikacje pakietu Office z tworzenia procesów podrzędnych", GUID "d4f940ab-401b-4efc-aadc-ad5f3c50688a".
- **Inne zalecane funkcje —** Nie m.in.

### <a name="block-office-apps-from-creating-executable-content"></a>Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje

- **Dotyczy:** Office
- **Procesy** — winword.exe, powerpnt.exe, excel.exe
- **Operation** — tworzenie plików
- **Przykłady plików/folderów** Klucze rejestru/wartości, procesy, usługi — C:\Użytkownicy *\AppData **.exe, C:\ProgramData**.exe, C:\ProgramData**.com, C:\UsersAppData*\Local\**Temp.com, C:\Użytkownicy*\Pobrane**.exe, C:\Użytkownicy *\AppData.scf **, C:\ProgramData.scf**, C:\Użytkownicy\Public*.exe, C:\Użytkownicy*\Pulpit***.exe
- **Reguły ograniczania powierzchni ataków** — nie nasyć.

### <a name="block-wscript-from-reading-certain-types-of-files"></a>Blokowanie odczytywania określonych typów plików przez w języku Wscript

- **Dotyczy języka** Wscript
- **Procesy** — wscript.exe
- **Operacja —** odczyt pliku
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów,** usług — C:\Użytkownicy *\AppData**.js, C:\Użytkownicy*\Pobrane**.js
- **Reguły ograniczania powierzchni** w trakcie ataków — ze względu na problemy z niezawodnością i wydajnością reguły ASR nie mają możliwości uniemożliwiania konkretnego procesu odczytywania określonego typu pliku skryptu. Mamy regułę zapobiegającą wektorom ataków, które mogą pochodzić z tych scenariuszy. Nazwa reguły to "Blokowanie kodu JavaScript lub VBScript z uruchamiania pobranej zawartości wykonywalnego" (GUID "d3e037e1-3eb8-44c8-a917-57927947596) ") oraz "Blokowanie wykonywania potencjalnie obtapkowanych skryptów" (GUID " 5beb7efe-fd9a-4556-801d-275e5ffc04cc").
- Inne zalecane funkcje — Chociaż istnieją określone reguły asr, które kontrolują określone wektory ataków w tych scenariuszach, warto pamiętać, że funkcja audio/wideo może domyślnie przeprowadzać inspekcje skryptów (PowerShell, Windows Script Host, JavaScript, VBScript i innych) w czasie rzeczywistym za pośrednictwem interfejsu AMSI (Antimalware Scan Interface). Więcej informacji można uzyskać tutaj: [Interfejs skanowania przed złośliwym kodem (AMSI).](/windows/win32/amsi/antimalware-scan-interface-portal)

### <a name="block-launch-of-child-processes"></a>Blokowanie uruchamiania procesów podrzędnych

- **Dotyczy programu** Adobe Acrobat
- **Procesy** — AcroRd32.exe, Acrobat.exe
- **Operacja** — wykonywanie procesu
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów,** usług cmd.exe, powershell.exe, wscript.exe
- **Reguły ograniczania powierzchni w przypadku ataków** — reguły ASR umożliwiają blokowanie uruchamiania procesów podrzędnych przez program Adobe Reader. Nazwa reguły to "Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader", identyfikator GUID "7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c".
- **Inne zalecane funkcje —** Nie m.in.

### <a name="block-download-or-creation-of-executable-content"></a>Blokowanie pobierania lub tworzenia zawartości wykonywalnego

- **Dotyczy certyfikatu** CertUtil: Blokowanie pobierania lub tworzenia pliku wykonywalnego
- **Procesy** — certutil.exe
- **Operation** — tworzenie plików
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów,** usług — *.exe
- **Reguły ograniczania powierzchni** w przypadku ataków — reguły ASR nie obsługują tych scenariuszy, ponieważ są częścią Program antywirusowy Microsoft Defender ochrony.
- **Inne zalecane funkcje —** Program Microsoft Defender AV zapobiega tworzeniu lub pobieraniu pliku wykonywalnego przez firmę CertUtil.

### <a name="block-processes-from-stopping-critical-system-components"></a>Blokowanie procesów zatrzymania krytycznych składników systemu

- **Dotyczy wszystkich** procesów
- **Procesy**- *
- **Operacja —** zakończenie procesu
- Przykłady plików/folderów, kluczy rejestru **/wartości, procesów,** usług MsSense.exe, MsMpEng.exe, NisSrv.exe, svchost.exe*, services.exe, csrss.exe, smss.exe, wininit.exe i innych.
- **Reguły ograniczania obszarów** ataków — reguły ASR nie obsługują tych scenariuszy, ponieważ są one chronione Windows wbudowanymi zabezpieczeniami.
- **Inne zalecane funkcje**: ELAM (Early Launch AntiMalware), PPL (Protection Process Light), PPL AntiMalware Light i System Guard.

### <a name="block-specific-launch-process-attempt"></a>Blokowanie określonej próby uruchomienia

- **Dotyczy określonych** procesów
- **Procesy** — "Nadaj nazwę procesowi"
- **Operacja** — wykonywanie procesu
- **Przykłady plików/folderów, kluczy rejestru/wartości, procesów,** tor.exe, bittorrent.exe, cmd.exe, powershell.exe i nie tylko
- **Reguły zmniejszania powierzchni ataków** — ogólne reguły ASR nie są przeznaczone do działania jako menedżer aplikacji.
- **Inne zalecane funkcje —** aby uniemożliwić użytkownikom uruchamianie określonych procesów lub programów, zaleca się używanie kontrolki Windows Defender aplikacji. Wskaźników Programu Microsoft Defender for Endpoint File i Cert można używać w scenariuszu reagowania na incydenty (nie należy go oglądać jako mechanizmu kontroli aplikacji).

### <a name="block-unauthorized-changes-to-microsoft-defender-antivirus-configurations"></a>Blokowanie nieautoryzowanych zmian Program antywirusowy Microsoft Defender konfiguracji

- **Dotyczy wszystkich** procesów
- **Procesy**- *
- **Operacja** — modyfikacje rejestru
- Przykłady plików/folderów, kluczy rejestru **/wartości, procesów,** usług— HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware, HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowRealTimeMonitoring itp.
- **Reguły zmniejszania powierzchni** podczas ataków — reguły ASR nie obejmują tych scenariuszy, ponieważ są częścią wbudowanej ochrony programu Microsoft Defender for Endpoint.
- Inne zalecane funkcje — ochrona przed naruszeniami (opt-in, zarządzane z intune) zapobiega nieautoryzowanym zmianom kluczy rejestru DisableAntiWirus, DisableAntiSpyware, DisableRealtimeMonitoring, DisableOnAccessProtection, DisableBehaviorMonitoring i DisableIOAVProtection (i nie tylko).

Zobacz też

- [Zmniejszenie powierzchni ataków — często zadawane pytania](attack-surface-reduction-faq.yml)
- [Włączanie reguł ograniczania powierzchni ataków](enable-attack-surface-reduction.md)
- [Ocenianie reguł zmniejszania powierzchni ataków](evaluate-attack-surface-reduction.md)
