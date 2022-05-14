---
title: Konfigurowanie wykluczeń dla plików otwieranych przez określone procesy
description: Pliki ze skanowania można wykluczyć, jeśli zostały otwarte przez określony proces.
keywords: Program antywirusowy Microsoft Defender, proces, wykluczenie, pliki, skany
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 6faca5dde477908010f4426ff9009f383b63c58c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418615"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>Konfigurowanie wykluczeń dla plików otwieranych przez procesy


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows 

Pliki otwierane przez określone procesy można wykluczyć ze skanowania Program antywirusowy Microsoft Defender. Zobacz [Rekomendacje, aby zdefiniować wykluczenia](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) przed zdefiniowaniem list wykluczeń.

W tym artykule opisano sposób konfigurowania list wykluczeń.

## <a name="examples-of-exclusions"></a>Przykłady wykluczeń

<br/><br/>

|Wykluczenia|Przykład|
|---|---|
|Dowolny plik na komputerze, który jest otwierany przez dowolny proces o określonej nazwie pliku|Określenie spowoduje wykluczenie `test.exe` plików otwartych przez: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Dowolny plik na komputerze, który jest otwierany przez dowolny proces w określonym folderze|Określenie spowoduje wykluczenie `c:\test\sample\*` plików otwartych przez: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Dowolny plik na komputerze, który jest otwierany przez określony proces w określonym folderze|Określenie spowoduje wykluczenie `c:\test\process.exe` plików otwartych tylko przez `c:\test\process.exe`|

Po dodaniu procesu do listy wykluczeń procesu Program antywirusowy Microsoft Defender nie będzie skanować plików otwartych przez ten proces, niezależnie od tego, gdzie znajdują się pliki. Sam proces zostanie jednak przeskanowany, chyba że został on również dodany do [listy wykluczeń plików](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Wykluczenia mają zastosowanie tylko do [zawsze włączonej ochrony i monitorowania w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md). Nie mają one zastosowania do skanowania zaplanowanego lub na żądanie.

Zmiany wprowadzone za pomocą zasady grupy list wykluczeń **będą wyświetlane** na listach w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md). Jednak zmiany wprowadzone w aplikacji Zabezpieczenia Windows **nie będą wyświetlane** na listach zasady grupy.

Możesz dodawać, usuwać i przeglądać listy wykluczeń w zasady grupy, Microsoft Endpoint Configuration Manager, Microsoft Intune i za pomocą aplikacji Zabezpieczenia Windows, a także używać symboli wieloznacznych do dalszego dostosowywania list.

Możesz również użyć poleceń cmdlet programu PowerShell i usługi WMI, aby skonfigurować listy wykluczeń, w tym przejrzeć listy.

Domyślnie lokalne zmiany wprowadzone na listach (przez użytkowników z uprawnieniami administratora; zmiany wprowadzone za pomocą programu PowerShell i WMI) zostaną scalone z listami zgodnie z definicją (i wdrożonymi) przez zasady grupy, Configuration Manager lub Intune. Listy zasady grupy będą mieć pierwszeństwo w przypadku konfliktów.

Można [skonfigurować sposób scalania list wykluczeń zdefiniowanych lokalnie i globalnie](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) , aby umożliwić zmianę lokalną zastąpienia ustawień wdrożenia zarządzanego.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Konfigurowanie listy wykluczeń dla plików otwartych przez określone procesy

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj Microsoft Intune, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanowania

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w ustawieniach](/intune/device-restrictions-configure) ograniczeń urządzeń Microsoft Intune i [Program antywirusowy Microsoft Defender dla Windows 10 w Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj Microsoft Endpoint Manager, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanowania

Zobacz [Jak tworzyć i wdrażać zasady ochrony przed złośliwym kodem: ustawienia wykluczeń, aby](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) uzyskać szczegółowe informacje na temat konfigurowania Microsoft Endpoint Manager (bieżącej gałęzi).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj zasady grupy, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanowania

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki \> Program antywirusowy Microsoft Defender \> Wykluczenia**.

4. Kliknij **dwukrotnie pozycję Wykluczenia procesu** i dodaj wykluczenia:
    1. Ustaw opcję **Włączone**.
    2. W sekcji **Opcje** kliknij pozycję **Pokaż...**.
    3. Wprowadź każdy proces we własnym wierszu w kolumnie **Nazwa wartości** . Zapoznaj się z tabelą przykładów dla różnych typów wykluczeń procesów. Wprowadź **wartość 0** w kolumnie **Wartość** dla wszystkich procesów.

5. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj poleceń cmdlet programu PowerShell, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanowania

Używanie programu PowerShell do dodawania lub usuwania wykluczeń dla plików, które zostały otwarte przez procesy, wymaga użycia kombinacji trzech poleceń cmdlet z parametrem `-ExclusionProcess` . Wszystkie polecenia cmdlet znajdują się w [module defender](/powershell/module/defender/).

Format poleceń cmdlet to:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Następujące elementy są dozwolone jako \<cmdlet\>:

<br/><br/>

|Akcja konfiguracji|Polecenie cmdlet programu PowerShell|
|---|---|
|Tworzenie lub zastępowanie listy|`Set-MpPreference`|
|Dodaj do listy|`Add-MpPreference`|
|Usuwanie elementów z listy|`Remove-MpPreference`|

> [!IMPORTANT]
> Jeśli utworzono listę za `Set-MpPreference` pomocą polecenia cmdlet lub `Add-MpPreference`, ponowne użycie `Set-MpPreference` polecenia cmdlet spowoduje zastąpienie istniejącej listy.

Na przykład poniższy fragment kodu może spowodować wykluczenie wszystkich plików otwieranych przez określony proces w usłudze Microsoft Defender AV:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz Manage antivirus with PowerShell cmdlets and Program antywirusowy Microsoft Defender cmdlets (Zarządzanie oprogramowaniem antywirusowym przy użyciu poleceń cmdlet programu PowerShell i [poleceń cmdlet Program antywirusowy Microsoft Defender](/powershell/module/defender)).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj instrukcji zarządzania Windows (WMI), aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanowania

Użyj [metod **Set**, **Add** i **Remove** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
ExclusionProcess
```

Użycie poleceń **Set**, **Add** i **Remove** jest analogiczne do ich odpowiedników w programie PowerShell: `Set-MpPreference`, `Add-MpPreference`i `Remove-MpPreference`.

Aby uzyskać więcej informacji i dozwolone parametry, zobacz [Windows Defender Interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj aplikacji Zabezpieczenia Windows, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanowania

Aby uzyskać [instrukcje, zobacz Dodawanie wykluczeń w aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

## <a name="use-wildcards-in-the-process-exclusion-list"></a>Używanie symboli wieloznacznych na liście wykluczeń procesu

Użycie symboli wieloznacznych na liście wykluczeń procesu różni się od ich użycia na innych listach wykluczeń.

W szczególności nie można użyć symbolu wieloznacznego znaku zapytania (`?`), a symbol wieloznaczny gwiazdki (`*`) może być używany tylko na końcu pełnej ścieżki. Nadal można używać zmiennych środowiskowych (takich jak `%ALLUSERSPROFILE%`) jako symboli wieloznacznych podczas definiowania elementów na liście wykluczeń procesu.

W poniższej tabeli opisano sposób użycia symboli wieloznacznych na liście wykluczeń procesu:

<br/><br/>

|Symbol wieloznaczny|Przykładowe użycie|Przykładowe dopasowania|
|---|---|---|
|`*` (gwiazdka) <p> Zamienia dowolną liczbę znaków|`C:\MyData\*`|Dowolny plik otwarty przez `C:\MyData\file.exe`|
|Zmienne środowiskowe <p> Zdefiniowana zmienna jest wypełniana jako ścieżka podczas obliczania wykluczenia|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Dowolny plik otwarty przez `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Przejrzyj listę wykluczeń

Elementy na liście wykluczeń można pobrać za pomocą programu MpCmdRun, programu PowerShell, [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings), [Intune](/intune/device-restrictions-configure) lub [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

Jeśli używasz programu PowerShell, możesz pobrać listę na dwa sposoby:

- Pobierz stan wszystkich preferencji Program antywirusowy Microsoft Defender. Każda z list będzie wyświetlana w oddzielnych wierszach, ale elementy na każdej liście zostaną połączone w ten sam wiersz.
- Zapisz stan wszystkich preferencji w zmiennej i użyj tej zmiennej, aby wywołać tylko konkretną listę, która Cię interesuje. Każde użycie `Add-MpPreference` jest zapisywane w nowym wierszu.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Weryfikowanie listy wykluczeń przy użyciu polecenia MpCmdRun

Aby sprawdzić wykluczenia za pomocą dedykowanego [narzędzia wiersza polecenia mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options), użyj następującego polecenia:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Sprawdzanie wykluczeń przy użyciu narzędzia MpCmdRun wymaga Program antywirusowy Microsoft Defender CAMP w wersji 4.18.1812.3 (wydanej w grudniu 2018 r.) lub nowszej.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Przejrzyj listę wykluczeń wraz ze wszystkimi innymi preferencjami Program antywirusowy Microsoft Defender przy użyciu programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Get-MpPreference
```

Zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń cmdlet Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [Program antywirusowy Microsoft Defender](/powershell/module/defender), aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Pobieranie określonej listy wykluczeń przy użyciu programu PowerShell

Użyj następującego fragmentu kodu (wprowadź każdy wiersz jako oddzielne polecenie); Zastąp **elementy WDAVprefs** dowolną etykietą, którą chcesz nazwać zmienną:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

Zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń cmdlet Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [Program antywirusowy Microsoft Defender](/powershell/module/defender), aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie i weryfikowanie wykluczeń w skanowaniach Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie wykluczeń Program antywirusowy Microsoft Defender na serwerze Windows](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Dostosowywanie, inicjowanie i przeglądanie wyników skanowania i korygowania Program antywirusowy Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
