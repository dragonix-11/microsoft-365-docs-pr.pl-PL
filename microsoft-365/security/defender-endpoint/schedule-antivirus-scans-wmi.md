---
title: Planowanie skanów antywirusowych przy Windows zarządzania instrumentacjami zarządzania
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
ms.openlocfilehash: be22e59f6d2be30ead354099f2cc168868959752
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007878"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planowanie skanów antywirusowych przy Windows Zarządzania Instrumentacjami (WMI)

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

W tym artykule opisano sposób konfigurowania zaplanowanych skanów przy użyciu usługi WMI. Aby dowiedzieć się więcej o planowaniu skanów i typach skanowania, zobacz Konfigurowanie zaplanowanego szybkiego lub pełnego Program antywirusowy Microsoft Defender [skanowania](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Planowanie Windows za pomocą instrukcji zarządzania danymi (WMI, Management Instruction)

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz Windows Defender [interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Sieć WMI do planowania skanów, gdy punkt końcowy nie jest w użyciu

Użyj metody [Set klasy MSFT_MpPreference dla](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) następujących właściwości:

```WMI
ScanOnlyIfIdleEnabled
```

Aby uzyskać więcej informacji o interfejsach API i dozwolonych parametrach, [zobacz Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> W przypadku planowania skanowania w czasie, gdy punkty końcowe nie są w użyciu, skany nie korzystają z konfiguracji ograniczania procesora i w pełni korzystają z dostępnych zasobów, aby wykonać skanowanie tak szybko, jak to możliwe.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>Sieć WMI do planowania skanów w celu ukończenia działań naprawczych

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz Windows Defender [interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>Sieć WMI do planowania codziennych skanów

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
ScanScheduleQuickScanTime
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz Windows Defender [interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

