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
ms.openlocfilehash: e1cbdd156306d7cc2ee41fd85baadb1fa51cf1ac
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007893"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>Planowanie skanowania antywirusowego przy użyciu programu PowerShell

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

W tym artykule opisano sposób konfigurowania zaplanowanych skanów przy użyciu poleceń cmdlet programu PowerShell. Aby dowiedzieć się więcej o planowaniu skanów i typach skanowania, zobacz Konfigurowanie zaplanowanego szybkiego lub pełnego Program antywirusowy Microsoft Defender [skanowania](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Planowanie skanowania przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Aby uzyskać więcej informacji, zobacz Konfigurowanie i uruchamianie poleceń [cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) Program antywirusowy Microsoft Defender i programu [Defender Antivirus](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Polecenia cmdlet programu PowerShell do planowania skanów, gdy punkt końcowy nie jest w użyciu

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) do konfigurowania i uruchamiania Program antywirusowy Microsoft Defender i poleceń [cmdlet programu antywirusowego Defender](/powershell/module/defender/).

> [!NOTE]
> W przypadku planowania skanowania w czasie, gdy punkty końcowe nie są w użyciu, skany nie korzystają z konfiguracji ograniczania procesora i w pełni korzystają z dostępnych zasobów, aby wykonać skanowanie tak szybko, jak to możliwe.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>Polecenia cmdlet programu PowerShell do planowania skanów w celu ukończenia działań naprawczych

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Aby [uzyskać więcej informacji na](use-powershell-cmdlets-microsoft-defender-antivirus.md) temat używania programu PowerShell z programem PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń cm Program antywirusowy Microsoft Defender dlet programu PowerShell oraz poleceń [cmdlet programu Defender](/powershell/module/defender/) oraz Program antywirusowy Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>Polecenia cmdlet programu PowerShell do planowania codziennych skanów

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń [cmdlet](/powershell/module/defender/) programu PowerShell i programu Defender za pomocą poleceń [cm Program antywirusowy Microsoft Defender dlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md).
