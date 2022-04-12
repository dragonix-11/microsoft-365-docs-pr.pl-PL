---
title: Planowanie skanowania antywirusowego przy użyciu programu PowerShell
description: Planowanie skanowania antywirusowego przy użyciu programu PowerShell
keywords: szybkie skanowanie, pełne skanowanie, oprogramowanie antywirusowe, harmonogram, program PowerShell
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 8961428acee5d166b0cdad4982aa5f9ed48020af
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788837"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>Planowanie skanowania antywirusowego przy użyciu programu PowerShell

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

W tym artykule opisano sposób konfigurowania zaplanowanych skanów przy użyciu poleceń cmdlet programu PowerShell. Aby dowiedzieć się więcej na temat planowania skanowania i typów skanowania, zobacz [Konfigurowanie zaplanowanych szybkich lub pełnych skanów Program antywirusowy Microsoft Defender](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Planowanie skanowania przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet programu antywirusowego Program antywirusowy Microsoft Defender i defendera](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Polecenia cmdlet programu PowerShell do planowania skanowania, gdy punkt końcowy nie jest używany

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet Program antywirusowy Microsoft Defender i defender antivirus](/powershell/module/defender/).

> [!NOTE]
> Jeśli planujesz skanowanie w czasie, gdy punkty końcowe nie są używane, skany nie uwzględniają konfiguracji ograniczania przepustowości procesora CPU i w pełni wykorzystują dostępne zasoby, aby jak najszybciej ukończyć skanowanie.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>Polecenia cmdlet programu PowerShell do planowania skanowania w celu ukończenia korygowania

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [poleceń cmdlet programu antywirusowego Defender](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>Polecenia cmdlet programu PowerShell do planowania codziennych skanów

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu](use-powershell-cmdlets-microsoft-defender-antivirus.md) Program antywirusowy Microsoft Defender i [programu antywirusowego Defender przy użyciu poleceń cmdlet](/powershell/module/defender/) programu PowerShell.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)