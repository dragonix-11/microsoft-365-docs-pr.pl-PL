---
title: Konfigurowanie opcji skanowania dla Program antywirusowy Microsoft Defender
description: Program Microsoft Defender AV można skonfigurować do skanowania plików magazynu poczty e-mail, kopii zapasowej lub ponownego zarchiwizowania punktów, plików sieciowych i zarchiwizowane plików (na przykład .zip plików).
keywords: skanowanie zaawansowane, skanowanie, poczta e-mail, archiwum, zip, rar, archiwum, skanowanie ponowne
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
ms.openlocfilehash: 2527a558d474fecaab813963dc38a9e76aa89d5c
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2021
ms.locfileid: "62996397"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Konfigurowanie Program antywirusowy Microsoft Defender opcji skanowania

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Konfigurowanie Microsoft Intune skanowania za pomocą programu Microsoft Intune

Aby uzyskać więcej informacji, zobacz Konfigurowanie ustawień ograniczeń urządzeń w [programie Microsoft Intune](/intune/device-restrictions-configure) oraz Program antywirusowy Microsoft Defender ograniczeń urządzeń dla aplikacji Windows 10 [Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Konfigurowanie Microsoft Endpoint Manager skanowania za pomocą programu Microsoft Endpoint Manager

Aby uzyskać szczegółowe informacje na temat Microsoft Endpoint Manager (bieżąca gałąź), zobacz Jak tworzyć i wdrażać zasady ochrony przed [złośliwym kodem: ustawienia skanowania](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Konfigurowanie zasady grupy skanowania za pomocą programu Zasady grupy

> [!TIP]
> Pobierz arkusz zasady grupy kalkulacyjny, który zawiera listę ustawień zasad dla komputera i konfiguracji użytkowników, które są zawarte w plikach szablonów administracyjnych dostarczanych z usługą Windows. Podczas edytowania plików w oknie zasady grupy kalkulacyjnych można konfigurować zasady grupy arkusza kalkulacyjnego. <br/><br/> Oto najnowsze wersje:
> - [zasady grupy Ustawienia arkusza kalkulacyjnego z aktualizacją z Windows 10 maja 2020 r. (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [zasady grupy Ustawienia arkusza kalkulacyjnego z Windows z 11 października 2021 r. (21h2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera i** kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki** \> **Program antywirusowy Microsoft Defender**, a następnie wybierz lokalizację (zobacz Ustawienia [i](#settings-and-locations) lokalizacje w tym artykule).

5. Edytuj obiekt zasad.

6. Kliknij **przycisk OK** i powtórz te czynności dla innych ustawień.

### <a name="settings-and-locations"></a>Ustawienia i lokalizacje

|Element zasad i lokalizacja|Ustawienie domyślne (jeśli nie jest skonfigurowane)|Parametr programu PowerShell `Set-MpPreference` lub właściwość WMI klasy `MSFT_MpPreference`|
|---|---|---|
|Skanowanie wiadomości e-mail <p> **Skanowanie** \> **Włączanie skanowania wiadomości e-mail**<p>Zobacz [Ograniczenia dotyczące skanowania wiadomości e-mail](#email-scanning-limitations) (w tym artykule)|Wyłączone|`-DisableEmailScanning`|
| Skanowanie skryptów | Włączone  | To ustawienie zasad umożliwia skonfigurowanie skanowania skryptów. Jeśli to ustawienie zostanie włączone lub nie zostanie skonfigurowane, skanowanie skryptów zostanie włączone. <p>Zobacz [Defender/AllowScriptKanning](/windows/client-management/mdm/policy-csp-defender)  | 
|Skanowanie [różnych punktów](/windows/win32/fileio/reparse-points) <p> **Skanowanie** \> **Włączanie skanowania punktowego**|Wyłączone|Niedostępny <p>Zobacz [Ponowne rozsyłanie punktów](/windows/win32/fileio/reparse-points)|
|Skanowanie zamapowanych dysków sieciowych <p> **Skanowanie** \> **Uruchamianie pełnego skanowania na zamapowanych dyskach sieciowych**|Wyłączone|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Skanuj pliki archiwum (na przykład pliki .zip lub .rar). <p> **Skanowanie** \> **Skanowanie plików archiwum**|Włączone|`-DisableArchiveScanning` <p>Lista [wykluczeń rozszerzeń](configure-extension-file-exclusions-microsoft-defender-antivirus.md) będzie miała pierwszeństwo przed tym ustawieniem.|
|Skanowanie plików w sieci <p> **Skanowanie** \> **Skanowanie plików sieciowych**|Wyłączone|`-DisableScanningNetworkFiles`|
|Skanowanie spakowanych plików wykonywalnych <p> **Skanowanie** \> **Skanowanie spakowanych plików wykonywalnych**|Włączone|Niedostępne|
|Skanowanie tylko dysków wymiennych podczas pełnych skanów <p> **Skanowanie** \> **Skanowanie dysków wymiennych**|Wyłączone|`-DisableRemovableDriveScanning`|
|Określanie poziomu podfolderów w folderze archiwum do przeskanowania <p>**Skanowanie** \> **Określanie maksymalnej głębokości skanowania plików archiwum**|0|Niedostępny|
|Określ maksymalne obciążenie procesora (jako wartość procentową) podczas skanowania. <p> **Skanowanie** \> **Określanie maksymalnego procentu użycia procesora podczas skanowania**|50|`-ScanAvgCPULoadFactor` <p>**UWAGA**: Maksymalne obciążenie procesora nie jest trudnym limitem, ale zapewnia, że aparat skanujące nie może przekroczyć średniego maksimum. Ręczne uruchamianie skanów spowoduje zignorowanie tego ustawienia i uruchomienie bez ograniczeń procesora.|
|Określ maksymalny rozmiar (w kilobajtach) plików archiwum, które mają być skanowane. <p> **Skanowanie** \> **Określanie maksymalnego rozmiaru skanowanych plików archiwum**|Bez limitu|Niedostępne <p>Wartość domyślna 0 nie powoduje żadnego limitu|
|Konfigurowanie niskiego priorytetu procesora dla zaplanowanych skanów <p> **Skanowanie** \> **Konfigurowanie niskiego priorytetu procesora dla zaplanowanych skanów**|Wyłączone|Niedostępny|

> [!NOTE]
> Jeśli jest włączona ochrona w czasie rzeczywistym, pliki są skanowane, zanim będą dostępne i wykonane. Zakres skanowania obejmuje wszystkie pliki, w tym pliki na montowanych nośnikach wymiennych, takich jak dyski USB. Jeśli urządzenie wykonujące skanowanie ma włączona ochronę w czasie rzeczywistym lub ochronę przy dostępie, skanowanie będzie również obejmować udziały sieciowe.

## <a name="use-powershell-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu programu PowerShell

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz

- [Zarządzanie Program antywirusowy Microsoft Defender za pomocą poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender cmdlet](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Konfigurowanie opcji skanowania przy użyciu usługi WMI

Zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>Ograniczenia dotyczące skanowania wiadomości e-mail

Skanowanie wiadomości e-mail umożliwia skanowanie plików poczty e-mail używanych przez Outlook i innych klientów poczty podczas skanowania na żądanie i zaplanowane. Obiekty osadzone w wiadomościach e-mail (takie jak załączniki i zarchiwizowane pliki) również są skanowane. Można skanować i rekultywować następujące typy formatów plików:

- DBX
- MBX
- MIME

Pliki PST używane przez program Outlook 2003 lub starszy (jeśli typ archiwum jest ustawiony na format innego niż Unicode) również są skanowane, ale program Program antywirusowy Microsoft Defender nie może rozwiązać problemów związanych z zagrożeniami, które są wykrywane w plikach PST.

Jeśli Program antywirusowy Microsoft Defender w wiadomości e-mail wykryje zagrożenie, zostaną w nim podane następujące informacje, które mogą pomóc w zidentyfikowaniu naruszonej wiadomości e-mail, co pozwoli ręcznie rozwiązać ten błąd:

- Temat wiadomości e-mail
- Nazwa załącznika

## <a name="scanning-mapped-network-drives"></a>Skanowanie zamapowanych dysków sieciowych

W dowolnym systemie operacyjnym skanowane są tylko dyski sieciowe, które są mapowane na poziomie systemu. Mapowane dyski sieciowe na poziomie użytkownika nie są skanowane. Mapowane dyski sieciowe na poziomie użytkownika to te, które użytkownik ręcznie mapuje w swojej sesji i używa własnych poświadczeń.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie, inicjowanie i przeglądanie wyników skanów Program antywirusowy Microsoft Defender środków zaradczych](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Konfigurowanie i uruchamianie skanowania na żądanie Program antywirusowy Microsoft Defender skanowania](run-scan-microsoft-defender-antivirus.md)
- [Konfigurowanie zaplanowanych Program antywirusowy Microsoft Defender skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
