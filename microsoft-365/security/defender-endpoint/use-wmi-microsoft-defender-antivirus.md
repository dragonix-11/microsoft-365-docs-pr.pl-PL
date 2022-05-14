---
title: Konfigurowanie Program antywirusowy Microsoft Defender za pomocą usługi WMI
description: Dowiedz się, jak skonfigurować Program antywirusowy Microsoft Defender i zarządzać nimi przy użyciu skryptów WMI do pobierania, modyfikowania i aktualizowania ustawień w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: wmi, skrypty, instrumentacja zarządzania windows, konfiguracja
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 8ef8355afe3019c2a179f59d83faddac4aa5792a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419007"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi za pomocą instrumentacji zarządzania Windows (WMI)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Windows Management Instrumentation (WMI) to interfejs skryptów, który umożliwia pobieranie, modyfikowanie i aktualizowanie ustawień.

Więcej informacji na temat usługi WMI można znaleźć w [bibliotece administracji systemu sieci deweloperów firmy Microsoft](/windows/win32/wmisdk/wmi-start-page).

Program antywirusowy Microsoft Defender ma wiele określonych klas WMI, których można użyć do wykonywania większości tych samych funkcji co zasady grupy i innych narzędzi do zarządzania. Wiele klas jest analogicznych do [Defender dla Chmury poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md).

[Biblioteka referencyjna dostawcy msdn Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) zawiera listę dostępnych klas WMI dla Program antywirusowy Microsoft Defender i zawiera przykładowe skrypty.

Zmiany wprowadzone za pomocą usługi WMI będą miały wpływ na ustawienia lokalne w punkcie końcowym, w którym zmiany są wdrażane lub wprowadzane. Oznacza to, że wdrożenia zasad z zasady grupy, Microsoft Endpoint Configuration Manager lub Microsoft Intune mogą zastępować zmiany wprowadzone za pomocą usługi WMI. 

Można [skonfigurować ustawienia, które można zastąpić lokalnie za pomocą przesłonięcia zasad lokalnych](configure-local-policy-overrides-microsoft-defender-antivirus.md).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-topics"></a>Tematy pokrewne

- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
