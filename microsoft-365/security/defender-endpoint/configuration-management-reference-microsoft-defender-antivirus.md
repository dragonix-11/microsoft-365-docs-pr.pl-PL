---
title: Zarządzanie Program antywirusowy Microsoft Defender w firmie
description: Dowiedz się, jak używać funkcji zasady grupy, Menedżer konfiguracji, PowerShell, WMI, Intune i wiersza polecenia do zarządzania programem Microsoft Defender AV
keywords: zasady grupy, gpo, menedżer konfiguracji, sccm, scep, powershell, wmi, intune, defender, antivirus, antimalware, zabezpieczenia, ochrona
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
ms.openlocfilehash: 4c73936bd32381988a03ad527a83847497eab71d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997361"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Zarządzanie Program antywirusowy Microsoft Defender w firmie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

Za pomocą następujących narzędzi Program antywirusowy Microsoft Defender zarządzać danymi i je konfigurować:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (obecnie jest częścią Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (obecnie jest częścią Microsoft Endpoint Manager)
- [zasady grupy](./use-group-policy-microsoft-defender-antivirus.md)
- [Polecenia cmdlet programu PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows instrumentacja zarządzania (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- Narzędzie [Wiersza polecenia ochrony przed złośliwym oprogramowaniem firmy Microsoft](./command-line-arguments-microsoft-defender-antivirus.md) (określane *mianem* narzędziampcmdrun.exezłośliwego oprogramowania)

Dalsze informacje, linki i zasoby można znaleźć w poniższych artykułach dotyczących używania tych narzędzi do zarządzania Program antywirusowy Microsoft Defender.

|Artykuł|Opis|
|:---|:---|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą Microsoft Intune i Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Informacje o wdrażaniu i Menedżer konfiguracji Intune oraz zarządzaniu raportami i konfigurowaniu aplikacji Program antywirusowy Microsoft Defender|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą zasady grupy danych](use-group-policy-microsoft-defender-antivirus.md)|Lista wszystkich ustawień zasady grupy w szablonach ADMX|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instrukcje dotyczące korzystania z poleceń cmdlet programu PowerShell do zarządzania Program antywirusowy Microsoft Defender oraz linki do dokumentacji dotyczące wszystkich poleceń cmdlet i dozwolonych parametrów|
|[Zarządzanie Program antywirusowy Microsoft Defender za pomocą Windows Management Instrumentation (WMI)](use-wmi-microsoft-defender-antivirus.md)|Instrukcje dotyczące zarządzania usługą WMI Program antywirusowy Microsoft Defender oraz linki do dokumentacji interfejsów API WMIv2 (w tym wszystkich klas, metod i właściwości)|
|[Zarządzanie Program antywirusowy Microsoft Defender za MpCmdRun.exe wiersza polecenia](command-line-arguments-microsoft-defender-antivirus.md)|Instrukcje dotyczące używania dedykowanego narzędzia wiersza polecenia do zarządzania Program antywirusowy Microsoft Defender|
