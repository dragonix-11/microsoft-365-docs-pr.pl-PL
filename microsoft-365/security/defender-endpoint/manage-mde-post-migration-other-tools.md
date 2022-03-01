---
title: Zarządzanie programem Microsoft Defender dla punktu końcowego przy użyciu programu PowerShell, usługi WMI i MPCmdRun.exe
description: Dowiedz się, jak zarządzać usługą Microsoft Defender for Endpoint za pomocą programu PowerShell, usługi WMI i aplikacji MPCmdRun.exe
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, PowerShell, WMI, MPCmdRun.exe, Microsoft Defender for Endpoint, edr
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
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: b5794b978e35faa23df51528a077fe90444fdce1
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996815"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Zarządzanie programem Microsoft Defender for Endpoint za pomocą programu PowerShell, usługi WMI i MPCmdRun.exe

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Zalecamy używanie programu [Microsoft Endpoint Manager](/mem) do zarządzania funkcjami ochrony przed zagrożeniami organizacji dla urządzeń (nazywanymi również punktami końcowymi). Endpoint Manager obejmuje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction).
>
> - [Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview)
> - [Współ zarządzanie usługą Microsoft Defender for Endpoint na Windows 10 i Windows 11 za pomocą usługi Menedżer konfiguracji i Intune](manage-mde-post-migration-intune.md)
> - [Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune](manage-mde-post-migration-intune.md)

Niektórymi ustawieniami programu Program antywirusowy Microsoft Defender na urządzeniach można zarządzać za pomocą programu [PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell), [programu Windows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) i narzędzia [Microsoft Malware Protection Command Line Utility](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Na przykład możesz zarządzać niektórymi Program antywirusowy Microsoft Defender ustawieniami. Ponadto w niektórych przypadkach możesz dostosować reguły ograniczania powierzchni ataków i wykorzystać ustawienia ochrony.

> [!IMPORTANT]
> Funkcje ochrony przed zagrożeniami konfigurowane przy użyciu programu PowerShell, MCPmdRun.exe WMI lub MCPmdRun.exe można za pomocą ustawień konfiguracji wdrożonych w usłudze Intune lub programie Menedżer konfiguracji.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego za pomocą programu PowerShell

Za pomocą programu PowerShell można zarządzać regułami Program antywirusowy Microsoft Defender, wykorzystywania ochrony i zmniejszania powierzchni ataków.<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zarządzanie Program antywirusowy Microsoft Defender** <br/><br/> Wyświetl stan ochrony przed złośliwym oprogramowaniem, skonfiguruj preferencje skanowania antywirusowego & aktualizacji i wprowadzaj inne zmiany w ochronie antywirusowej.*|[Konfigurowanie poleceń cmdlet programu PowerShell i zarządzanie nimi Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Włączanie ochrony w chmurze za pomocą poleceń cmdlet programu PowerShell](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Konfigurowanie ochrony przed zagrożeniami** na urządzeniach organizacji w celu ich zmniejszenia <br/><br/> *Zalecamy, aby na początku korzystać z ochrony [przed użyciem luk w](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) trybie inspekcji. Dzięki temu można zobaczyć, jak ochrona przed użyciem luk w zabezpieczeniach wpłynie na aplikacje, z których korzysta Twoja organizacja.*|[Dostosowywanie ochrony przed lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Polecenia cmdlet programu PowerShell do ochrony przed exploitami](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**Konfigurowanie reguł zmniejszania powierzchni ataków za** pomocą programu PowerShell <br/><br/> *Za pomocą programu PowerShell możesz wykluczyć pliki i foldery z reguł ograniczania powierzchni ataków.*|[Dostosowywanie reguł zmniejszania powierzchni ataków: Użyj programu PowerShell, aby wykluczyć pliki & foldery](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-powershell-to-exclude-files-and-folders) <br/><br/> Zobacz też [Graficzne narzędzie interfejsu użytkownika użytkownika António Vasconcelo](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI), które umożliwia ustawienie reguł zmniejszania powierzchni ataków za pomocą programu PowerShell.|
|**Włączanie ochrony sieci za** pomocą programu PowerShell <br/><br/> *Za pomocą programu PowerShell możesz włączyć ochronę sieci.*|[Włączanie ochrony sieci za pomocą programu PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Konfigurowanie kontrolowanego dostępu do folderu w** celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *[Kontrolowany dostęp do folderu](/microsoft-365/security/defender-endpoint/controlled-folders) jest również określany jako ochrona antyransomware.*|[Włączanie kontrolowanego dostępu do folderu za pomocą programu PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Skonfiguruj Zaporę Microsoft Defender,** aby blokować nieautoryzowany ruch sieciowy wychodzący do urządzeń organizacji lub wychodzący z nich|[Zapora Microsoft Defender z zaawansowaną administracją zabezpieczeń przy Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Skonfiguruj szyfrowanie i funkcję BitLocker**, aby chronić informacje na urządzeniach w Twojej organizacji, na których działa Windows|[Przewodnik po programie PowerShell dla funkcji BitLocker](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego za Windows Management Instrumentation (WMI)

WMI to interfejs skryptów umożliwiający pobieranie, modyfikowanie i aktualizowanie ustawień. Aby dowiedzieć się więcej, zobacz [Korzystanie z usługi WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Włączanie ochrony w chmurze** na urządzeniu|[Włączanie Windows ochrony w chmurze za pomocą instrukcji zarządzania danymi (WMI)](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Pobieranie, modyfikowanie i aktualizowanie ustawień Program antywirusowy Microsoft Defender**|[Użyj usługi WMI, aby skonfigurować usługę Program antywirusowy Microsoft Defender i zarządzać nimi](/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Przejrzyj listę dostępnych klas i skryptów przykładowych aplikacji WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Zobacz też [zarchiwizowane informacje Windows Defender informacji o dostawcy WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego za pomocą programu Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe)

Na poszczególnych urządzeniach możesz uruchomić skanowanie, uruchomić śledzenie diagnostyczne, sprawdzać aktualizacje analizy zabezpieczeń i nie tylko, używając narzędzia wiersza mpcmdrun.exe. Narzędzie można znaleźć w programie `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Uruchom ją z wiersza polecenia.

Aby dowiedzieć się więcej, zobacz [Konfigurowanie usługi Program antywirusowy Microsoft Defender zarządzanie mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender sieciOwego

Jeśli jeszcze tego nie zrobiono, skonfiguruj w portalu usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> wyświetlanie alertów, konfigurowanie funkcji ochrony przed zagrożeniami i wyświetlanie szczegółowych informacji o ogólnym stanie zabezpieczeń Twojej organizacji.

Możesz także skonfigurować, czy i jakie funkcje będą dostępne dla użytkowników końcowych w Centrum zabezpieczeń usługi Microsoft Defender.

- [Omówienie Centrum zabezpieczeń usługi Microsoft Defender](/microsoft-365/security/defender-endpoint/use)

- [Ochrona punktu końcowego: Centrum zabezpieczeń usługi Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie funkcji Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Odwiedź pulpit nawigacyjny Centrum zabezpieczeń usługi Microsoft Defender zabezpieczeń](/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune](manage-mde-post-migration-intune.md)
