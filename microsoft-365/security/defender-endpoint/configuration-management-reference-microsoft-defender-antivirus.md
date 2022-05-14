---
title: Zarządzanie Program antywirusowy Microsoft Defender w firmie
description: Dowiedz się, jak używać zasady grupy, Configuration Manager, programu PowerShell, usługi WMI, Intune i wiersza polecenia do zarządzania usługą Microsoft Defender AV
keywords: zasady grupy, gpo, config manager, sccm, scep, powershell, wmi, intune, defender, antivirus, antimalware, security, protection
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 760c3b7ca646b02813b5d14086f5d94fc9aec72c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418659"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Zarządzanie Program antywirusowy Microsoft Defender w firmie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Możesz zarządzać Program antywirusowy Microsoft Defender i konfigurować je przy użyciu następujących narzędzi:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (obecnie część Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (obecnie część Microsoft Endpoint Manager)
- [Zasady grupy](./use-group-policy-microsoft-defender-antivirus.md)
- [Polecenia cmdlet programu PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Instrumentacja zarządzania Windows (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- [Narzędzie wiersza polecenia ochrony przed złośliwym oprogramowaniem firmy Microsoft](./command-line-arguments-microsoft-defender-antivirus.md) (nazywane narzędziem *mpcmdrun.exe*

Poniższe artykuły zawierają dodatkowe informacje, linki i zasoby dotyczące używania tych narzędzi do zarządzania Program antywirusowy Microsoft Defender i konfigurowania ich.

|Artykułu|Opis|
|:---|:---|
|[Zarządzanie Program antywirusowy Microsoft Defender przy użyciu Microsoft Intune i Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Informacje o używaniu Intune i Configuration Manager do wdrażania Program antywirusowy Microsoft Defender, zarządzania nimi, raportowania i konfigurowania Program antywirusowy Microsoft Defender|
|[Zarządzanie Program antywirusowy Microsoft Defender przy użyciu ustawień zasady grupy](use-group-policy-microsoft-defender-antivirus.md)|Lista wszystkich ustawień zasady grupy znajdujących się w szablonach ADMX|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instrukcje dotyczące zarządzania Program antywirusowy Microsoft Defender za pomocą poleceń cmdlet programu PowerShell oraz linki do dokumentacji dla wszystkich poleceń cmdlet i dozwolonych parametrów|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą instrumentacji zarządzania Windows (WMI)](use-wmi-microsoft-defender-antivirus.md)|Instrukcje dotyczące zarządzania Program antywirusowy Microsoft Defender za pomocą usługi WMI oraz linki do dokumentacji interfejsów API WMIv2 (w tym wszystkich klas, metod i właściwości)|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą narzędzia wiersza polecenia MpCmdRun.exe](command-line-arguments-microsoft-defender-antivirus.md)|Instrukcje dotyczące używania dedykowanego narzędzia wiersza polecenia do zarządzania Program antywirusowy Microsoft Defender|

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)