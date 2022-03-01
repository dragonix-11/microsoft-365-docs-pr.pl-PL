---
title: Konfigurowanie Program antywirusowy Microsoft Defender przy użyciu usługi WMI
description: Dowiedz się, jak konfigurować i zarządzać Program antywirusowy Microsoft Defender przy użyciu skryptów WMI w celu pobierania, modyfikowania i aktualizowania ustawień w programie Microsoft Defender for Endpoint.
keywords: wmi, scripts, windows management instrumentation, configuration
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
ms.openlocfilehash: c8057a971576d5511440ac009acd6eab55b302e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997368"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie Windows Program antywirusowy Microsoft Defender i zarządzanie nimi przy użyciu instrumentacji zarządzania Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Windows Management Instrumentation (WMI) to interfejs skryptów umożliwiający pobieranie, modyfikowanie i aktualizowanie ustawień.

Dowiedz się więcej o sieci WMI w bibliotece [Microsoft Developer Network System Administration](/windows/win32/wmisdk/wmi-start-page).

Program antywirusowy Microsoft Defender ma wiele określonych klas WMI, których można używać do wykonywania większości funkcji, takich jak program zasady grupy i inne narzędzia do zarządzania. Wiele klas jest analogicznych do poleceń [cmdlet programu PowerShell dla programu Defender w chmurze](use-powershell-cmdlets-microsoft-defender-antivirus.md).

Biblioteka [referencyjna dostawcy Windows Defender WMIv2 w witrynie MSDN](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) zawiera listę dostępnych klas usługi WMI dla Program antywirusowy Microsoft Defender oraz przykładowe skrypty.

Zmiany wprowadzone za pomocą usługi WMI mają wpływ na ustawienia lokalne w punkcie końcowym, w którym zmiany są wdrażane lub wdrażane. Oznacza to, że wdrożenia zasad z innymi zasady grupy, Microsoft Endpoint Configuration Manager lub innych Microsoft Intune mogą zastąpić zmiany wprowadzone przy użyciu usługi WMI. 

Możesz określić [, które ustawienia można zastąpić lokalnie za pomocą zastępowania zasad lokalnych](configure-local-policy-overrides-microsoft-defender-antivirus.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
