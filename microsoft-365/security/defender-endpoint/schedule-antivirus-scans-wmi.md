---
title: Planowanie skanowania antywirusowego przy użyciu instrumentacji zarządzania Windows
description: Planowanie skanowania antywirusowego przy użyciu usługi WMI
keywords: szybkie skanowanie, pełne skanowanie, WMI, harmonogram, oprogramowanie antywirusowe
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
ms.openlocfilehash: 2b25876a43dea3b1598d4bdfa89cf4724c0fca14
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788925"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planowanie skanowania antywirusowego przy użyciu instrumentacji zarządzania Windows (WMI)

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

W tym artykule opisano sposób konfigurowania zaplanowanych skanów przy użyciu usługi WMI. Aby dowiedzieć się więcej na temat planowania skanowania i typów skanowania, zobacz [Konfigurowanie zaplanowanych szybkich lub pełnych skanów Program antywirusowy Microsoft Defender](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Planowanie skanowania przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz [Windows Defender Interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Usługa WMI do planowania skanowania, gdy punkt końcowy nie jest używany

Użyj [metody Set klasy MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
ScanOnlyIfIdleEnabled
```

Aby uzyskać więcej informacji na temat interfejsów API i dozwolonych parametrów, zobacz [Windows Defender Interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> Jeśli planujesz skanowanie w czasie, gdy punkty końcowe nie są używane, skany nie uwzględniają konfiguracji ograniczania przepustowości procesora CPU i w pełni wykorzystują dostępne zasoby, aby jak najszybciej ukończyć skanowanie.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>Usługa WMI do planowania skanowania w celu ukończenia korygowania

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz [Windows Defender Interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>Usługa WMI do planowania codziennych skanów

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
ScanScheduleQuickScanTime
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz [Windows Defender Interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)