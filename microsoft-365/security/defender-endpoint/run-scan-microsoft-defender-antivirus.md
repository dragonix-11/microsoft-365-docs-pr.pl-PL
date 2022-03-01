---
title: Uruchamianie i dostosowywanie skanów na żądanie w Program antywirusowy Microsoft Defender
description: Uruchamianie i konfigurowanie skanów na żądanie przy użyciu programu PowerShell, Windows Management Instrumentation lub indywidualnie na punktach końcowych za pomocą Zabezpieczenia Windows programu
keywords: skanowanie, na żądanie, zadania, intune, skanowanie błyskawiczne
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/22/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1f82fe410634ab92f7b403a30bcbcdf9a61634ba
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007896"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Konfigurowanie i uruchamianie skanowania na żądanie Program antywirusowy Microsoft Defender skanowania

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Możesz uruchomić skanowanie na żądanie dla poszczególnych punktów końcowych. Skany zaczną się od razu i można zdefiniować parametry skanowania, takie jak lokalizacja lub typ. Po uruchomieniu skanowania możesz wybrać jeden z trzech typów: szybkie skanowanie, pełne skanowanie i skanowanie niestandardowe. W większości przypadków użyj szybkiego skanowania. Szybkie skanowanie przeszukuje wszystkie lokalizacje, w których zarejestrowano złośliwe oprogramowanie, aby uruchomić system, takie jak klucze rejestru i znane Windows autostartu.

W połączeniu z zawsze włączona ochroną w czasie rzeczywistym, która sprawdza pliki po ich otwarciu i zamknięciu oraz zawsze, gdy użytkownik przechodzi do folderu, szybkie skanowanie pomaga zapewnić silną ochronę przed złośliwym oprogramowaniem, które zaczyna się od złośliwego oprogramowania na poziomie systemu i na poziomie kernel. W większości przypadków szybkie skanowanie jest wystarczające i jest zalecaną opcją skanowania według harmonogramu lub skanowania na żądanie. [Dowiedz się więcej o typach skanowania](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender działa w kontekście konta [LocalSystem](/windows/win32/services/localsystem-account) podczas skanowania lokalnego. W skanach sieci jest używany kontekst konta urządzenia. Jeśli konto urządzenia domeny nie ma odpowiednich uprawnień dostępu do udostępniania, skanowanie nie będzie działać. Upewnij się, że urządzenie ma uprawnienia do dostępu do udziału sieciowego.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Używanie Microsoft Endpoint Manager do uruchamiania skanowania

1. Przejdź do centrum Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Endpoint security Antivirus (Zabezpieczenia punktu końcowego**\>).

3. Na liście kart wybierz pozycję Windows 10 punktów  końcowych o złej kondycji lub Windows **11 punktów końcowych o złej kondycji**.

4. Z podanej listy akcji wybierz pozycję **Szybkie** skanowanie (zalecane) lub **Pełne skanowanie**.

   [![Opcje skanowania na karcie Windows 10 punktów końcowych o złej kondycji.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Aby uzyskać więcej informacji na temat Microsoft Endpoint Manager w celu przeprowadzenia skanowania, zobacz Zadania związane z zabezpieczeniami przed złośliwym kodem i zaporą: Jak przeprowadzić skanowanie [na żądanie](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Uruchamianie skanowania mpcmdrun.exe przy użyciu narzędzia wiersza polecenia

Użyj następującego parametru `-scan` :

```console
mpcmdrun.exe -scan -scantype 1
```

Aby uzyskać więcej informacji na temat używania narzędzia i dodatkowych parametrów, takich jak rozpoczynanie pełnego skanowania lub definiowanie ścieżek, zobacz Konfigurowanie ustawień i zarządzanie nimi za pomocą narzędzia wiersza [Program antywirusowy Microsoft Defender polecenia](command-line-arguments-microsoft-defender-antivirus.md) mpcmdrun.exe.

## <a name="use-microsoft-intune-to-run-a-scan"></a>Używanie Microsoft Intune do uruchamiania skanowania

1. Przejdź do centrum Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Na pasku bocznym wybierz **pozycję Urządzenia** \> **Wszystkie urządzenia** i wybierz urządzenie, które chcesz przeskanować.

3. Wybierz **pozycję ... Więcej**. Z menu opcji wybierz pozycję **Szybkie skanowanie** (zalecane) lub **Pełne skanowanie**.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Uruchamianie skanowania Zabezpieczenia Windows za pomocą aplikacji do skanowania

Zobacz [Uruchamianie skanowania w aplikacji Zabezpieczenia Windows,](microsoft-defender-security-center-antivirus.md) aby uzyskać instrukcje dotyczące uruchamiania skanowania dla poszczególnych punktów końcowych.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Uruchamianie skanowania za pomocą poleceń cmdlet programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Start-MpScan
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń [cm Program antywirusowy Microsoft Defender dlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) oraz programu Defender za pomocą poleceń [cmdlet programu](/powershell/module/defender/) PowerShell.

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Uruchamianie Windows przy użyciu instrukcji zarządzania danymi (WMI)

Użyj metody [**Start**](/previous-versions/windows/desktop/defender/start-msft-mpscan) **MSFT_MpScan zajęć**.

Aby uzyskać więcej informacji o dozwolonych parametrach, zobacz Windows Defender [interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)
