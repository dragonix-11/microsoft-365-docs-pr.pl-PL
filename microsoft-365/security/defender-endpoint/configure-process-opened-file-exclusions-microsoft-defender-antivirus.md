---
title: Konfigurowanie wykluczeń dla plików otwieranych w określonych procesach
description: Możesz wykluczyć pliki ze skanów, jeśli zostały otwarte w określonym procesie.
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
ms.openlocfilehash: 034ad1312497652554c9a59d51ba18f6bddc9d83
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996789"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>Konfigurowanie wykluczeń dla plików otwieranych przez procesy


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Możesz wykluczyć pliki otwarte przez określone procesy z Program antywirusowy Microsoft Defender skanów. Zobacz [Rekomendacje o definiowaniu wykluczeń](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) przed zdefiniowaniem list wykluczeń.

W tym artykule opisano, jak konfigurować listy wykluczeń.

## <a name="examples-of-exclusions"></a>Przykłady wykluczeń

<br/><br/>

|Wykluczenie|Przykład|
|---|---|
|Dowolny plik na komputerze otwierany w trakcie procesu z określoną nazwą pliku|Określenie oznaczałoby `test.exe` wykluczenie plików otwieranych przez: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Dowolny plik na komputerze otwierany w ramach procesu w określonym folderze|Określenie oznaczałoby `c:\test\sample\*` wykluczenie plików otwieranych przez: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Dowolny plik na komputerze otwierany w określonym procesie w określonym folderze|Określanie oznaczało `c:\test\process.exe` , że pliki będą otwierane tylko przez `c:\test\process.exe`|

Po dodaniu procesu do listy wykluczeń procesu Program antywirusowy Microsoft Defender nie będą skanowane pliki otwarte w tym procesie, niezależnie od tego, gdzie znajdują się te pliki. Jednak sam proces będzie skanowany, chyba że został również dodany do [listy wykluczeń plików](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Wykluczenia mają zastosowanie tylko do [zawsze stosowanej ochrony i monitorowania w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md). Nie dotyczą one skanowania zaplanowanego ani skanowania na żądanie.

Zmiany wprowadzone przy zasady grupy wykluczeń będą **wyświetlane** na listach w aplikacji Zabezpieczenia Windows [wykluczeń](microsoft-defender-security-center-antivirus.md). Jednak zmiany wprowadzone w aplikacji Zabezpieczenia Windows **nie będą wyświetlane** na zasady grupy listach.

Listy wykluczeń w programach zasady grupy, Microsoft Endpoint Configuration Manager, Microsoft Intune oraz w aplikacji Zabezpieczenia Windows można dodawać, usuwać i przeglądać, a także dostosowywać listy za pomocą symboli wieloznacznych.

Do konfigurowania list wykluczeń, na przykład przeglądania list, możesz również użyć poleceń cmdlet programu PowerShell i usługi WMI.

Domyślnie lokalne zmiany wprowadzone na listach (przez użytkowników z uprawnieniami administratora; zmiany wprowadzone przy użyciu programu PowerShell i usługi WMI) będą scalane z listami zdefiniowanymi (i wdrożonych) przez usługę zasady grupy, Menedżer konfiguracji lub Intune. Listy zasady grupy mają pierwszeństwo w przypadku konfliktów.

Możesz skonfigurować [scalanie list wykluczeń](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) lokalnych i globalnych, aby zezwolić na zastępowanie ustawień wdrożenia zarządzanego przez zmiany lokalne.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Konfigurowanie listy wykluczeń dla plików otwieranych przez określone procesy

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj Microsoft Intune, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanów

Aby [uzyskać więcej szczegółowych](/intune/device-restrictions-configure) informacji, Microsoft Intune konfigurować ustawienia ograniczeń urządzeń Microsoft Intune i Program antywirusowy Microsoft Defender urządzenia dla aplikacji [Windows 10 Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj Microsoft Endpoint Manager, aby wykluczyć pliki, które zostały otwarte przez określone procesy ze skanów

Zobacz [Jak tworzyć i wdrażać zasady ochrony przed złośliwym oprogramowaniem: Ustawienia wykluczeń](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings), aby uzyskać szczegółowe informacje na temat Microsoft Endpoint Manager (bieżąca gałąź).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Użyj zasady grupy, aby wykluczyć pliki otwarte przez określone procesy ze skanów

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera i** kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender \> \> wykluczeń**.

4. Kliknij dwukrotnie **pozycję Wykluczenia procesu** i dodaj wykluczenia:
    1. Ustaw dla opcji wartość **Włączone**.
    2. W sekcji **Opcje** kliknij pozycję **Pokaż....**
    3. Wprowadź każdy proces w własnym wierszu w **kolumnie Nazwa** wartości. W tabeli przykładowej można znaleźć informacje o różnych typach wykluczeń procesów. Wprowadź **wartość 0** w **kolumnie Wartość** dla wszystkich procesów.

5. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Używanie poleceń cmdlet programu PowerShell do wykluczania plików, które zostały otwarte przez określone procesy ze skanów

Dodanie lub usunięcie wykluczeń plików otwieranych przez procesy za pomocą programu PowerShell wymaga użycia kombinacji trzech poleceń cmdlet z parametrem `-ExclusionProcess` . Wszystkie polecenia cmdlet znajdują się w [module Defender](/powershell/module/defender/).

Format dla tych polecenia cmdlet jest:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Następujące elementy są dozwolone jako \<cmdlet\>:

<br/><br/>

|Akcja konfiguracji|Polecenie cmdlet programu PowerShell|
|---|---|
|Tworzenie lub zastępowanie listy|`Set-MpPreference`|
|Dodawanie do listy|`Add-MpPreference`|
|Usuwanie elementów z listy|`Remove-MpPreference`|

> [!IMPORTANT]
> Jeśli utworzono listę za pomocą polecenia `Set-MpPreference` `Add-MpPreference`cmdlet lub , `Set-MpPreference` użycie ponownie spowoduje zastąpienie istniejącej listy.

Na przykład poniższy fragment kodu spowoduje, że w skanach audio/wideo programu Microsoft Defender wykluczysz wszystkie pliki otwarte w określonym procesie:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Zarządzanie oprogramowaniem antywirusowym za pomocą poleceń cmdlet programu PowerShell i poleceń [cmdlet Program antywirusowy Microsoft Defender polecenia cmdlet](/powershell/module/defender).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Używanie Windows zarządzania (WMI) w celu wykluczenia plików, które zostały otwarte przez określone procesy ze skanów

Za pomocą [**metod Set**, **Add** i **Remove**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) MSFT_MpPreference właściwości:

```WMI
ExclusionProcess
```

Zestaw **, dodawanie** i usuwanie jest analogiczne  do ich odpowiedników w programie PowerShell: `Set-MpPreference`, `Add-MpPreference`i .`Remove-MpPreference`

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz Windows Defender [interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Za pomocą Zabezpieczenia Windows wyklucz plików, które zostały otwarte przez określone procesy ze skanów

Aby [uzyskać instrukcje, zobacz Dodawanie Zabezpieczenia Windows w](microsoft-defender-security-center-antivirus.md) aplikacji mobilnej.

## <a name="use-wildcards-in-the-process-exclusion-list"></a>Używanie symboli wieloznacznych na liście wykluczeń procesów

Użycie symboli wieloznacznych na liście wykluczeń procesów różni się od używania ich na innych listach wykluczeń.

W szczególności nie można używać symbolu wieloznacznego znaku zapytania (`?`), a symbolu gwiazdki (`*`) można używać tylko na końcu pełnej ścieżki. Podczas definiowania elementów na liście wykluczeń procesów można nadal używać zmiennych środowiskowych ( `%ALLUSERSPROFILE%`takich jak ) jako symboli wieloznacznych.

W poniższej tabeli opisano, jak można używać symboli wieloznacznych na liście wykluczeń procesów:

<br/><br/>

|Symbol wieloznaczny|Przykład użycia|Przykładowe dopasowania|
|---|---|---|
|`*` (gwiazdka) <p> Zastępuje dowolną liczbę znaków.|`C:\MyData\*`|Każdy plik otwarty przez `C:\MyData\file.exe`|
|Zmienne środowiskowe <p> Zdefiniowana zmienna jest wypełniana ścieżką podczas oceny wykluczenia|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Każdy plik otwarty przez `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Przejrzyj listę wykluczeń

Możesz pobrać elementy z listy wykluczeń za pomocą programu MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) [Intune lub](/intune/device-restrictions-configure) [aplikacji Zabezpieczenia Windows aplikacji](microsoft-defender-security-center-antivirus.md).

Jeśli korzystasz z programu PowerShell, możesz pobrać listę na dwa sposoby:

- Pobieranie stanu wszystkich Program antywirusowy Microsoft Defender preferencji. Każda z list będzie wyświetlana w osobnych wierszach, ale elementy na każdej liście zostaną połączone w ten sam wiersz.
- Zapisz stan wszystkich preferencji dla zmiennej i za jej pomocą wywołaj tylko określoną listę, która Cię interesuje. Każde użycie jest `Add-MpPreference` zapisywane w nowym wierszu.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Sprawdzanie poprawności listy wykluczeń przy użyciu programu MpCmdRun

Aby sprawdzić wykluczenia przy użyciu dedykowanego narzędzia wiersza [mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options), użyj następującego polecenia:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Sprawdzanie wykluczeń w programie MpCmdRun wymaga oprogramowania PROGRAM ANTYWIRUSOWY MICROSOFT DEFENDER WERSJI 4.18.1812.3 (wydanej w grudniu 2018 r.) lub nowszej.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Przejrzyj listę wykluczeń obok wszystkich innych preferencji Program antywirusowy Microsoft Defender przy użyciu programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Get-MpPreference
```

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [Program antywirusowy Microsoft Defender cmdlet](/powershell/module/defender), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Pobieranie określonej listy wykluczeń przy użyciu programu PowerShell

Użyj następującego fragmentu kodu (wprowadź każdy wiersz jako oddzielne polecenie); **Zamień pola WDAVprefs na** etykiety, którym chcesz nazwać zmienną:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [Program antywirusowy Microsoft Defender cmdlet](/powershell/module/defender), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie i weryfikowanie wykluczeń w Program antywirusowy Microsoft Defender skanowaniach](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie Program antywirusowy Microsoft Defender wykluczeń na Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Dostosowywanie, inicjowanie i przeglądanie wyników skanów Program antywirusowy Microsoft Defender środków zaradczych](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
