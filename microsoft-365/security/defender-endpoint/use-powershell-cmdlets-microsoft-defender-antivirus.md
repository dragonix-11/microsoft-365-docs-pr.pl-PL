---
title: Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender
description: W Windows 10 i Windows 11 można używać poleceń cmdlet programu PowerShell do uruchamiania skanów, aktualizowania analizy zabezpieczeń i zmieniania ustawień w Program antywirusowy Microsoft Defender.
keywords: skanowanie, wiersz polecenia, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 075a475ef3135769e90362f441077b1638192e99
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997263"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie poleceń cmdlet programu PowerShell i zarządzanie nimi Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Za pomocą programu PowerShell można wykonywać różne funkcje w programie Windows Defender. Program PowerShell, podobnie jak wiersz polecenia lub wiersz polecenia, jest opartym na zadaniu językiem wiersza polecenia i językiem skryptów przeznaczonym specjalnie do administrowania systemem. Więcej informacji na ten temat można znaleźć w centrum [programu PowerShell w witrynie MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

Aby uzyskać listę polecenia cmdlet i ich funkcji oraz dostępnych parametrów, zobacz temat Polecenia [cmdlet programu antywirusowego Defender](/powershell/module/defender) .

Polecenia cmdlet programu PowerShell są najbardziej przydatne w środowiskach programu Windows Server, które nie korzystają z graficznego interfejsu użytkownika do konfigurowania oprogramowania.

> [!NOTE]
> Poleceń cmdlet programu PowerShell nie należy używać jako zamiennika pełnej infrastruktury zarządzania zasadami sieci, takiej jak szablony [Microsoft Endpoint Configuration Manager](/configmgr), [zasady grupy Management Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) czy szablony [Program antywirusowy Microsoft Defender zasady grupy ADMX](https://www.microsoft.com/download/101445).

Zmiany wprowadzone za pomocą programu PowerShell mają wpływ na ustawienia lokalne w punkcie końcowym, w którym zmiany są wdrażane lub wdrażane. Oznacza to, że wdrożenia zasad z innymi zasady grupy, Microsoft Endpoint Configuration Manager lub innych Microsoft Intune mogą zastąpić zmiany wprowadzone za pomocą programu PowerShell.

Możesz określić [, które ustawienia można zastąpić lokalnie za pomocą zastępowania zasad lokalnych](configure-local-policy-overrides-microsoft-defender-antivirus.md).

Program PowerShell jest zazwyczaj instalowany w folderze `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Używanie Program antywirusowy Microsoft Defender cmdlet programu PowerShell

1. Na pasku Windows wpisz **powershell**.
2. Wybierz **Windows PowerShell** z wyników, aby otworzyć interfejs.
3. Wprowadź polecenie programu PowerShell i dowolne parametry.

> [!NOTE]
> Może być konieczne otwarcie programu PowerShell w trybie administratora. Kliknij prawym przyciskiem myszy element w menu Start, kliknij pozycję **Uruchom jako administrator** i kliknij pozycję **Tak w** wierszu uprawnień.

Aby otworzyć pomoc online dla dowolnego polecenia cmdlet, wpisz następujące polecenie:

```PowerShell
Get-Help <cmdlet> -Online
```

Pomiń parametr `-online` , aby uzyskać pomoc lokalnie w pamięci podręcznej.

## <a name="related-topics"></a>Tematy pokrewne

- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Program antywirusowy Microsoft Defender polecenia cmdlet](/powershell/module/defender)
