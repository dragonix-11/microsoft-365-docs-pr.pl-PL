---
title: Konfigurowanie opcji skanowania dla Program antywirusowy Microsoft Defender
description: Usługę Microsoft Defender AV można skonfigurować do skanowania plików magazynu poczty e-mail, kopii zapasowych lub punktów ponownej analizy, plików sieciowych i plików zarchiwizowanych (takich jak pliki .zip).
keywords: zaawansowane skanowanie, skanowanie, poczta e-mail, archiwum, zip, rar, archiwum, skanowanie ponownej analizy
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.date: 12/03/2021
ms.collection: M365-security-compliance
ms.topic: how-to
ms.openlocfilehash: 5060a05e485db18f8276ecd2ec592ea3873a83b2
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419929"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Konfiguruj opcje skanowania programu antywirusowego Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows 

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu Microsoft Intune

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure) i [Program antywirusowy Microsoft Defender ustawień ograniczeń urządzenia dla Windows 10 w Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu Microsoft Endpoint Manager

Aby uzyskać szczegółowe informacje na temat konfigurowania Microsoft Endpoint Manager (bieżąca gałąź), zobacz [Jak tworzyć i wdrażać zasady ochrony przed złośliwym kodem: Ustawienia skanowania](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu zasady grupy

> [!TIP]
> Pobierz arkusz kalkulacyjny dokumentacji zasady grupy, który zawiera listę ustawień zasad dla konfiguracji komputerów i użytkowników, które są zawarte w plikach szablonów administracyjnych dostarczonych dla Windows. Podczas edytowania zasady grupy Obiektów można skonfigurować odwołanie do arkusza kalkulacyjnego. <br/><br/> Oto najnowsze wersje:
> - [zasady grupy Ustawienia arkusz kalkulacyjny referencyjny dla aktualizacji Windows 10 maja 2020 r. (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [zasady grupy Ustawienia arkusz kalkulacyjny referencyjny dla Windows 11 aktualizacji z października 2021 r. (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender**, a następnie wybierz lokalizację (zapoznaj się [z Ustawienia i lokalizacjami](#settings-and-locations) w tym artykule).

5. Edytuj obiekt zasad.

6. Kliknij przycisk **OK** i powtórz dla innych ustawień.

### <a name="settings-and-locations"></a>Ustawienia i lokalizacje

|Element zasad i lokalizacja|Ustawienie domyślne (jeśli nie jest skonfigurowane)|Parametr programu PowerShell `Set-MpPreference` lub właściwość WMI dla `MSFT_MpPreference` klasy|
|---|---|---|
|Skanowanie poczty e-mail <p> **Skanowania** \> **Włączanie skanowania poczty e-mail**<p>Zobacz [Ograniczenia skanowania poczty e-mail](#email-scanning-limitations) (w tym artykule)|Wyłączona|`-DisableEmailScanning`|
| Skanowanie skryptów | Włączone  | To ustawienie zasad umożliwia skonfigurowanie skanowania skryptów. Jeśli to ustawienie zostanie włączone lub nie zostanie skonfigurowane, skanowanie skryptów zostanie włączone. <p>Zobacz [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|Skanowanie [punktów ponownej analizy](/windows/win32/fileio/reparse-points) <p> **Skanowania** \> **Włączanie skanowania punktów ponownej analizy**|Wyłączona|Niedostępny <p>Zobacz [Punkty ponownej analizy](/windows/win32/fileio/reparse-points)|
|Skanowanie zamapowanych dysków sieciowych <p> **Skanowania** \> **Uruchamianie pełnego skanowania na zamapowanych dyskach sieciowych**|Wyłączona|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Skanuj pliki archiwum (takie jak pliki .zip lub .rar). <p> **Skanowania** \> **Skanowanie plików archiwum**|Włączone|`-DisableArchiveScanning` <p>[Lista wykluczeń rozszerzeń](configure-extension-file-exclusions-microsoft-defender-antivirus.md) będzie mieć pierwszeństwo przed tym ustawieniem.|
|Skanowanie plików w sieci <p> **Skanowania** \> **Skanowanie plików sieciowych**|Wyłączona|`-DisableScanningNetworkFiles`|
|Skanowanie spakowanych plików wykonywalnych <p> **Skanowania** \> **Skanowanie spakowanych plików wykonywalnych**|Włączone|Niedostępny|
|Skanuj dyski wymienne tylko podczas pełnego skanowania <p> **Skanowania** \> **Skanowanie dysków wymiennych**|Wyłączona|`-DisableRemovableDriveScanning`|
|Określanie poziomu podfolderów w folderze archiwum do skanowania <p>**Skanowania** \> **Określ maksymalną głębokość skanowania plików archiwum**|0|Niedostępny|
|Określ maksymalne obciążenie procesora CPU (jako wartość procentową) podczas skanowania. <p> **Skanowania** \> **Określanie maksymalnego procentu wykorzystania procesora CPU podczas skanowania**|50|`-ScanAvgCPULoadFactor` <p>**UWAGA**: Maksymalne obciążenie procesora CPU nie jest twardym limitem, ale jest wskazówką dla aparatu skanowania, aby nie przekraczać średniej maksymalnej. Ręczne uruchamianie skanowania spowoduje zignorowanie tego ustawienia i uruchomienie go bez żadnych limitów procesora CPU.|
|Określ maksymalny rozmiar (w kilobajtach) plików archiwum, które mają być skanowane. <p> **Skanowania** \> **Określanie maksymalnego rozmiaru plików archiwum do skanowania**|Brak limitu|Niedostępny <p>Wartość domyślna 0 nie ma żadnego limitu|
|Konfigurowanie niskiego priorytetu procesora CPU dla zaplanowanych skanów <p> **Skanowania** \> **Konfigurowanie niskiego priorytetu procesora CPU dla zaplanowanych skanów**|Wyłączona|Niedostępny|

> [!NOTE]
> Jeśli ochrona w czasie rzeczywistym jest włączona, pliki są skanowane przed uzyskaniem dostępu i wykonaniem. Zakres skanowania obejmuje wszystkie pliki, w tym pliki na zainstalowanych nośnikach wymiennych, takich jak dyski USB. Jeśli urządzenie wykonujące skanowanie ma włączoną ochronę w czasie rzeczywistym lub ochronę dostępu, skanowanie będzie również obejmować udziały sieciowe.

## <a name="use-powershell-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu programu PowerShell

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz

- [Zarządzanie Program antywirusowy Microsoft Defender za pomocą poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [polecenia cmdlet Program antywirusowy Microsoft Defender](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu usługi WMI

Zobacz [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>Ograniczenia skanowania poczty e-mail

Skanowanie poczty e-mail umożliwia skanowanie plików poczty e-mail używanych przez Outlook i innych klientów poczty podczas skanowania na żądanie i zaplanowanego skanowania. Skanowane są również obiekty osadzone w wiadomości e-mail (takie jak załączniki i zarchiwizowane pliki). Następujące typy formatów plików można skanować i korygować:

- DBX
- MBX
- MIME

Skanowane są również pliki PST używane przez Outlook 2003 lub starsze (gdzie typ archiwum jest ustawiony na nie-unicode), ale Program antywirusowy Microsoft Defender nie może korygować zagrożeń wykrytych wewnątrz plików PST.

Jeśli Program antywirusowy Microsoft Defender wykryje zagrożenie wewnątrz wiadomości e-mail, zostaną wyświetlone następujące informacje ułatwiające zidentyfikowanie wiadomości e-mail, której zabezpieczenia zostały naruszone, dzięki czemu można ręcznie skorygować zagrożenie:

- Temat wiadomości e-mail
- Nazwa załącznika

## <a name="scanning-mapped-network-drives"></a>Skanowanie zamapowanych dysków sieciowych

W dowolnym systemie operacyjnym skanowane są tylko dyski sieciowe zamapowane na poziomie systemu. Dyski sieciowe mapowane na poziomie użytkownika nie są skanowane. Zamapowane dyski sieciowe na poziomie użytkownika to dyski, które użytkownik mapuje w swojej sesji ręcznie i używając własnych poświadczeń.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie, inicjowanie i przeglądanie wyników skanowania i korygowania Program antywirusowy Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Konfiguruj i uruchom skanowania programu antywirusowego Microsoft Defender na żądanie](run-scan-microsoft-defender-antivirus.md)
- [Konfigurowanie zaplanowanych skanów Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
