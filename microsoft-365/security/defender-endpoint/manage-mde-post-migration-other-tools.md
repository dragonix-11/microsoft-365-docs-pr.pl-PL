---
title: Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell, usługi WMI i MPCmdRun.exe
description: Dowiedz się, jak zarządzać Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell, usługi WMI i MPCmdRun.exe
keywords: po migracji, zarządzaniu, operacjach, konserwacji, wykorzystaniu, programie PowerShell, usłudze WMI, MPCmdRun.exe, Ochrona punktu końcowego w usłudze Microsoft Defender, edr
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 71b18f5e78301ac144faef9046420e817c65fa6b
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607372"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell, usługi WMI i MPCmdRun.exe

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Zalecamy używanie usługi [Microsoft Endpoint Manager](/mem) do zarządzania funkcjami ochrony przed zagrożeniami w organizacji dla urządzeń (nazywanych również punktami końcowymi). Endpoint Manager obejmuje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Configuration Manager punktu końcowego firmy Microsoft](/mem/configmgr/core/understand/introduction).
> - [Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview)
> - [Współzarządzaj Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach Windows 10 i Windows 11 przy użyciu Configuration Manager i Intune](manage-mde-post-migration-intune.md)
> - [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Intune](manage-mde-post-migration-intune.md)

Niektóre ustawienia programu antywirusowego Microsoft Defender można zarządzać na urządzeniach za pomocą [programu PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell),  [instrumentacji zarządzania systemem Windows](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) i [narzędzia wiersza polecenia ochrony przed złośliwym oprogramowaniem firmy Microsoft](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Można na przykład zarządzać niektórymi ustawieniami programu antywirusowego Microsoft Defender. W niektórych przypadkach można dostosować reguły zmniejszania obszaru ataków i wykorzystać ustawienia ochrony.

> [!IMPORTANT]
> Funkcje ochrony przed zagrożeniami konfigurowane przy użyciu programu PowerShell, WMI lub MCPmdRun.exe można zastąpić ustawieniami konfiguracji wdrożonymi za pomocą Intune lub Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell

Program PowerShell umożliwia zarządzanie programem antywirusowym Microsoft Defender, ochroną przed lukami w zabezpieczeniach i regułami zmniejszania obszaru ataków.

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zarządzanie programem antywirusowym Microsoft Defender** <br/><br/> Wyświetl stan ochrony przed złośliwym kodem, skonfiguruj preferencje skanowania antywirusowego & aktualizacji i wprowadź inne zmiany w ochronie antywirusowej.*|[Konfigurowanie programu antywirusowego Microsoft Defender i zarządzanie nim przy użyciu poleceń cmdlet programu PowerShell](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Używanie poleceń cmdlet programu PowerShell w celu włączenia ochrony dostarczanej w chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Konfigurowanie ochrony przed lukami w zabezpieczeniach** w celu wyeliminowania zagrożeń na urządzeniach organizacji <br/><br/> *Zalecamy używanie ochrony przed lukami w zabezpieczeniach w [trybie inspekcji](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) na początku. Dzięki temu możesz zobaczyć, jak ochrona przed lukami w zabezpieczeniach wpływa na aplikacje używane przez organizację.*|[Dostosuj ochronę przed wykorzystaniem](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Polecenia cmdlet programu PowerShell na potrzeby ochrony przed lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**Konfigurowanie reguł zmniejszania obszaru ataków** za pomocą programu PowerShell <br/><br/> *Program PowerShell umożliwia wykluczenie plików i folderów z reguł zmniejszania obszaru podatnego na ataki.*|[Dostosowywanie reguł zmniejszania obszaru ataków: wykluczanie plików & folderów przy użyciu programu PowerShell](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction) <br/><br/> Zobacz również [graficzne narzędzie interfejsu użytkownika António Vasconcelo do ustawiania reguł zmniejszania obszaru ataków za pomocą programu PowerShell](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI).|
|**Włączanie ochrony sieci** za pomocą programu PowerShell <br/><br/> *Program PowerShell umożliwia włączenie ochrony sieci.*|[Włączanie ochrony sieci za pomocą programu PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Konfigurowanie kontrolowanego dostępu do folderów** w celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *[Kontrolowany dostęp do folderów](/microsoft-365/security/defender-endpoint/controlled-folders) jest również określany jako ochrona przed złośliwym oprogramowaniem.*|[Włączanie kontrolowanego dostępu do folderów za pomocą programu PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Konfigurowanie Zapora Microsoft Defender** do blokowania nieautoryzowanego ruchu sieciowego przepływającego do lub z urządzeń organizacji|[Zapora Microsoft Defender z usługą Advanced Security Administration przy użyciu Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Konfigurowanie szyfrowania i BitLocker** w celu ochrony informacji na urządzeniach organizacji z systemem Windows|[przewodnik referencyjny BitLocker programu PowerShell](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą instrumentacji zarządzania windows (WMI)

WMI to interfejs skryptów, który umożliwia pobieranie, modyfikowanie i aktualizowanie ustawień. Aby dowiedzieć się więcej, zobacz [Korzystanie z usługi WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Włączanie ochrony dostarczanej przez chmurę** na urządzeniu|[Używanie instrukcji zarządzania systemem Windows (WMI) w celu włączenia ochrony dostarczanej w chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Pobieranie, modyfikowanie i aktualizowanie ustawień** programu antywirusowego Microsoft Defender|[Konfigurowanie programu antywirusowego Microsoft Defender i zarządzanie nimi za pomocą usługi WMI] (/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Przejrzyj listę dostępnych klas WMI i przykładowych skryptów](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Zobacz również zarchiwizowane [informacje referencyjne dostawcy Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą narzędzia Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe)

Na pojedynczym urządzeniu można uruchomić skanowanie, rozpocząć śledzenie diagnostyczne, sprawdzić aktualizacje analizy zabezpieczeń i nie tylko przy użyciu narzędzia wiersza polecenia mpcmdrun.exe. Narzędzie można znaleźć w pliku `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Uruchom go w wierszu polecenia.

Aby dowiedzieć się więcej, zobacz [Konfigurowanie programu antywirusowego Microsoft Defender i zarządzanie nimi przy użyciu mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender

Jeśli jeszcze tego nie zrobiono, skonfiguruj <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portal Microsoft 365 Defender</a>, aby wyświetlał alerty, konfigurował funkcje ochrony przed zagrożeniami i wyświetlał szczegółowe informacje o ogólnej kondycji zabezpieczeń organizacji.

Można również skonfigurować, czy i jakie funkcje użytkownicy końcowi mogą zobaczyć w Centrum zabezpieczeń usługi Microsoft Defender.

- [Omówienie Centrum zabezpieczeń usługi Microsoft Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Centrum zabezpieczeń usługi Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny operacji zabezpieczeń Centrum zabezpieczeń usługi Microsoft Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Intune](manage-mde-post-migration-intune.md)
