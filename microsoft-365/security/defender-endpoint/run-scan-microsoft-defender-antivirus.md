---
title: Uruchamianie i dostosowywanie skanów na żądanie w Program antywirusowy Microsoft Defender
description: Uruchamianie i konfigurowanie skanów na żądanie przy użyciu programu PowerShell, instrumentacji zarządzania Windows lub pojedynczo w punktach końcowych przy użyciu aplikacji Zabezpieczenia Windows
keywords: skanowanie, na żądanie, dokumentacja, usługa Intune, natychmiastowe skanowanie
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
ms.openlocfilehash: b22e59f5f54b556b32140640f1210e04389148cb
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415557"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Konfiguruj i uruchom skanowania programu antywirusowego Microsoft Defender na żądanie

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Skanowanie na żądanie można uruchomić w poszczególnych punktach końcowych. Te skany zostaną uruchomione natychmiast i można zdefiniować parametry skanowania, takie jak lokalizacja lub typ. Po uruchomieniu skanowania można wybrać spośród trzech typów: Szybkie skanowanie, pełne skanowanie i skanowanie niestandardowe. W większości przypadków użyj szybkiego skanowania. Szybkie skanowanie sprawdza wszystkie lokalizacje, w których może być zarejestrowane złośliwe oprogramowanie, aby rozpocząć pracę z systemem, takie jak klucze rejestru i znane Windows folderów startowych.

W połączeniu z zawsze włączoną ochroną w czasie rzeczywistym, która przegląda pliki po ich otwarciu i zamknięciu oraz za każdym razem, gdy użytkownik przechodzi do folderu, szybkie skanowanie pomaga zapewnić silną ochronę przed złośliwym oprogramowaniem rozpoczynającym się od złośliwego oprogramowania na poziomie systemu i jądra. W większości przypadków szybkie skanowanie jest wystarczające i jest zalecaną opcją skanowania zaplanowanego lub na żądanie. [Dowiedz się więcej o typach skanowania](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender działa w kontekście konta [LocalSystem](/windows/win32/services/localsystem-account) podczas skanowania lokalnego. W przypadku skanowania sieci używa kontekstu konta urządzenia. Jeśli konto urządzenia domeny nie ma odpowiednich uprawnień dostępu do udziału, skanowanie nie będzie działać. Upewnij się, że urządzenie ma uprawnienia dostępu do udziału sieciowego.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Uruchamianie skanowania przy użyciu Microsoft Endpoint Manager

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** zabezpieczeń \> **punktu końcowego**.

3. Na liście kart wybierz pozycję **Windows 10 punkty końcowe w złej kondycji** lub **Windows 11 punkty końcowe w złej kondycji**.

4. Z podanej listy akcji wybierz pozycję **Szybkie skanowanie** (zalecane) lub **Pełne skanowanie**.

   [![Opcje skanowania na karcie Windows 10 punktów końcowych w złej kondycji.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Aby uzyskać więcej informacji na temat używania Microsoft Endpoint Manager do uruchamiania skanowania, zobacz [Zadania ochrony przed złośliwym kodem i zapory: Jak przeprowadzić skanowanie na żądanie](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Uruchamianie skanowania przy użyciu narzędzia wiersza polecenia mpcmdrun.exe

Użyj następującego `-scan` parametru:

```console
mpcmdrun.exe -scan -scantype 1
```

Aby uzyskać więcej informacji na temat korzystania z narzędzia i dodatkowych parametrów, w tym uruchamiania pełnego skanowania lub definiowania ścieżek, zobacz [Konfigurowanie Program antywirusowy Microsoft Defender za pomocą narzędzia wiersza polecenia mpcmdrun.exe.](command-line-arguments-microsoft-defender-antivirus.md)

## <a name="use-microsoft-intune-to-run-a-scan"></a>Uruchamianie skanowania przy użyciu Microsoft Intune

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Na pasku bocznym wybierz pozycję **Urządzenia** \> **Wszystkie urządzenia** i wybierz urządzenie, które chcesz zeskanować.

3. Wybierz **pozycję ... Więcej**. Z opcji wybierz pozycję **Szybkie skanowanie** (zalecane) lub **Pełne skanowanie**.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Uruchamianie skanowania przy użyciu aplikacji Zabezpieczenia Windows

Aby uzyskać instrukcje dotyczące uruchamiania skanowania w poszczególnych punktach końcowych, zobacz [Uruchamianie skanowania w aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Uruchamianie skanowania przy użyciu poleceń cmdlet programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Start-MpScan
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu Program antywirusowy Microsoft Defender i programu antywirusowego Defender przy użyciu poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md).[](/powershell/module/defender/)

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Uruchamianie skanowania przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Start**](/previous-versions/windows/desktop/defender/start-msft-mpscan) klasy **MSFT_MpScan**.

Aby uzyskać więcej informacji na temat dozwolonych parametrów, zobacz [Windows Defender interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)