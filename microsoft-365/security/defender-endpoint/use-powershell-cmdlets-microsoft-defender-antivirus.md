---
title: Konfigurowanie i uruchamianie Program antywirusowy Microsoft Defender przy użyciu poleceń cmdlet programu PowerShell
description: W Windows 10 i Windows 11 można uruchamiać skanowania, aktualizować analizę zabezpieczeń i zmieniać ustawienia w Program antywirusowy Microsoft Defender za pomocą poleceń cmdlet programu PowerShell.
keywords: scan, wiersz polecenia, mpcmdrun, defender
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
ms.openlocfilehash: 7afde73e1e1c1e5ff35ee906331aa2756ba55a21
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419489"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi za pomocą poleceń cmdlet programu PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program PowerShell umożliwia wykonywanie różnych funkcji w Windows Defender. Podobnie jak w wierszu polecenia lub wierszu polecenia, program PowerShell jest powłoką wiersza polecenia opartą na zadaniach i językiem skryptów przeznaczonym specjalnie do administrowania systemem. Więcej informacji na ten temat można znaleźć w [centrum programu PowerShell w witrynie MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

Aby uzyskać listę poleceń cmdlet oraz ich funkcji i dostępnych parametrów, zobacz temat [Poleceń cmdlet programu antywirusowego Defender](/powershell/module/defender) .

Polecenia cmdlet programu PowerShell są najbardziej przydatne w środowiskach serwera Windows, które nie korzystają z graficznego interfejsu użytkownika (GUI) do konfigurowania oprogramowania.

> [!NOTE]
> Polecenia cmdlet programu PowerShell nie powinny być używane jako zamiennik pełnej infrastruktury zarządzania zasadami sieciowymi, takiej jak [Microsoft Endpoint Configuration Manager](/configmgr), [konsola zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) lub [ Program antywirusowy Microsoft Defender zasady grupy szablonów ADMX](https://www.microsoft.com/download/101445).

Zmiany wprowadzone za pomocą programu PowerShell będą miały wpływ na ustawienia lokalne w punkcie końcowym, w którym zmiany są wdrażane lub wprowadzane. Oznacza to, że wdrożenia zasad z zasady grupy, Microsoft Endpoint Configuration Manager lub Microsoft Intune mogą zastępować zmiany wprowadzone za pomocą programu PowerShell.

Można [skonfigurować ustawienia, które można zastąpić lokalnie za pomocą przesłonięcia zasad lokalnych](configure-local-policy-overrides-microsoft-defender-antivirus.md).

Program PowerShell jest zwykle instalowany w folderze `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Używanie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender

1. Na pasku wyszukiwania Windows wpisz **powershell**.
2. Wybierz **pozycję Windows PowerShell** z wyników, aby otworzyć interfejs.
3. Wprowadź polecenie programu PowerShell i wszystkie parametry.

> [!NOTE]
> Może być konieczne otwarcie programu PowerShell w trybie administratora. Kliknij prawym przyciskiem myszy element w menu Start, kliknij przycisk **Uruchom jako administrator** i kliknij przycisk **Tak** w wierszu polecenia uprawnień.

Aby otworzyć pomoc online dla dowolnego polecenia cmdlet, wpisz następujące polecenie:

```PowerShell
Get-Help <cmdlet> -Online
```

Pomiń parametr w `-online` celu uzyskania lokalnie buforowanej pomocy.

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
- [polecenia cmdlet Program antywirusowy Microsoft Defender](/powershell/module/defender)
