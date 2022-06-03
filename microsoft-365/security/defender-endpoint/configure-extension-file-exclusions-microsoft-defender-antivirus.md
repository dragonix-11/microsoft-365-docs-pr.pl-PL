---
title: Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia, nazwy lub lokalizacji
description: Wyklucz pliki ze skanowania Program antywirusowy Microsoft Defender na podstawie ich rozszerzenia pliku, nazwy pliku lub lokalizacji.
keywords: wykluczenia, pliki, rozszerzenie, typ pliku, nazwa folderu, nazwa pliku, skany
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 7b1614738b17d7f3cf78a6bfabb84f85196d42ff
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873253"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia pliku i lokalizacji folderu

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Można zdefiniować wykluczenia dla Program antywirusowy Microsoft Defender, które mają zastosowanie do [zaplanowanych skanów](schedule-antivirus-scans.md), [skanów na żądanie](run-scan-microsoft-defender-antivirus.md) oraz [zawsze włączonej ochrony i monitorowania w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md). **Ogólnie rzecz biorąc, nie należy stosować wykluczeń**. Jeśli musisz zastosować wykluczenia, możesz wybrać jeden z kilku różnych rodzajów:

- Wykluczenia oparte na rozszerzeniach plików i lokalizacjach folderów (opisane w tym artykule)
- [Wykluczenia dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender wykluczenia nie mają zastosowania do innych funkcji Ochrona punktu końcowego w usłudze Microsoft Defender, takich jak [reguły zmniejszania obszaru ataków (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction) i [kontrolowany dostęp do folderów](/microsoft-365/security/defender-endpoint/controlled-folders). Pliki wykluczone przy użyciu metod opisanych w tym artykule mogą nadal wyzwalać alerty EDR i inne wykrycia.
> Aby ogólnie wykluczyć pliki, dodaj je do Ochrona punktu końcowego w usłudze Microsoft Defender [niestandardowych wskaźników](/microsoft-365/security/defender-endpoint/manage-indicators).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zobacz [Rekomendacje, aby zdefiniować wykluczenia](configure-exclusions-microsoft-defender-antivirus.md) przed zdefiniowaniem list wykluczeń.

## <a name="exclusion-lists"></a>Listy wykluczeń

Aby wykluczyć niektóre pliki ze skanowania Program antywirusowy Microsoft Defender, należy zmodyfikować listy wykluczeń. Program antywirusowy Microsoft Defender obejmuje wiele automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania, takich jak te używane w zarządzaniu przedsiębiorstwem, zarządzaniu bazami danych i innych scenariuszach i sytuacjach przedsiębiorstwa.

> [!NOTE]
> Wykluczenia dotyczą również wykrywania potencjalnie niechcianych aplikacji (PUA).
>
> Automatyczne wykluczenia mają zastosowanie tylko do Windows Server 2016 i nowszych. Te wykluczenia nie są widoczne w aplikacji Zabezpieczenia Windows i w programie PowerShell.

Poniższa tabela zawiera kilka przykładów wykluczeń opartych na rozszerzeniu pliku i lokalizacji folderu.

|Wykluczenia|Przykłady|Lista wykluczeń|
|---|---|---|
|Dowolny plik z określonym rozszerzeniem|Wszystkie pliki z określonym rozszerzeniem w dowolnym miejscu na maszynie. <p> Prawidłowa składnia: `.test` i `test`|Wykluczenia rozszerzeń|
|Dowolny plik w określonym folderze|Wszystkie pliki w folderze `c:\test\sample`|Wykluczenia plików i folderów|
|Określony plik w określonym folderze|Tylko plik `c:\sample\sample.test`|Wykluczenia plików i folderów|
|Określony proces|Plik wykonywalny `c:\test\process.exe`|Wykluczenia plików i folderów|

## <a name="characteristics-of-exclusion-lists"></a>Charakterystyka list wykluczeń

- Wykluczenia folderów mają zastosowanie do wszystkich plików i folderów w tym folderze, chyba że podfolder jest punktem ponownej analizy. Podfoldery punktu ponownej analizy muszą być wykluczone oddzielnie.
- Rozszerzenia plików mają zastosowanie do dowolnej nazwy pliku ze zdefiniowanym rozszerzeniem, jeśli ścieżka lub folder nie jest zdefiniowany.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Ważne uwagi dotyczące wykluczeń opartych na rozszerzeniach plików i lokalizacjach folderów

- Użycie symboli wieloznacznych, takich jak gwiazdka (\*), spowoduje zmianę sposobu interpretacji reguł wykluczeń. Aby uzyskać ważne informacje o [sposobie działania symboli wieloznacznych, zobacz sekcję Używanie symboli wieloznacznych w ścieżce nazwy pliku i folderze lub listach wykluczeń rozszerzeń](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) .

- Nie wykluczaj zamapowanych dysków sieciowych. Określ rzeczywistą ścieżkę sieci.

- Foldery, które są punktami ponownej analizy utworzonymi po uruchomieniu usługi Program antywirusowy Microsoft Defender i które zostały dodane do listy wykluczeń, nie zostaną uwzględnione. Uruchom ponownie usługę (uruchamiając ponownie Windows), aby nowe punkty ponownej analizy zostały uznane za prawidłowy cel wykluczeń.

- Wykluczenia dotyczą [zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [skanów na żądanie](run-scan-microsoft-defender-antivirus.md) i ochrony w [czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md), ale nie w usłudze Defender for Endpoint. Aby zdefiniować wykluczenia w usłudze Defender for Endpoint, użyj [niestandardowych wskaźników](manage-indicators.md).

- Domyślnie lokalne zmiany wprowadzone na listach (przez użytkowników z uprawnieniami administratora, w tym zmiany wprowadzone za pomocą programu PowerShell i WMI) zostaną scalone z listami zdefiniowanymi (i wdrożonymi) przez zasady grupy, Configuration Manager lub Intune. Listy zasady grupy mają pierwszeństwo w przypadku konfliktów. Ponadto zmiany listy wykluczeń wprowadzone za pomocą zasady grupy są widoczne w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

- Aby zezwolić na lokalne zmiany w celu zastąpienia ustawień wdrożenia zarządzanego, [skonfiguruj sposób scalania list wykluczeń zdefiniowanych lokalnie i globalnie](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Konfigurowanie listy wykluczeń na podstawie nazwy folderu lub rozszerzenia pliku

Możesz wybrać jedną z kilku metod definiowania wykluczeń dla Program antywirusowy Microsoft Defender.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie wykluczeń nazwy pliku, folderu lub rozszerzenia pliku przy użyciu Intune

Zobacz następujące artykuły:

- [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure)
- [Program antywirusowy Microsoft Defender ustawienia ograniczeń urządzenia dla Windows 10 w Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie wykluczeń nazwy pliku, folderu lub rozszerzenia pliku za pomocą Configuration Manager

Zobacz [Jak tworzyć i wdrażać zasady ochrony przed złośliwym kodem: ustawienia wykluczeń, aby](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) uzyskać szczegółowe informacje na temat konfigurowania Microsoft Endpoint Manager (bieżącej gałęzi).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Konfigurowanie wykluczeń folderu lub rozszerzenia pliku za pomocą zasady grupy

> [!NOTE]
> Jeśli określisz w pełni kwalifikowaną ścieżkę do pliku, tylko ten plik zostanie wykluczony. Jeśli folder jest zdefiniowany w wykluczeniu, wszystkie pliki i podkatalogi w tym folderze zostaną wykluczone.

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **Edytorze zarządzania zasadami grupy** przejdź do **konfiguracji komputera** i wybierz **szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Windows Defender** \> **Wykluczenia**.

4. Otwórz ustawienie **Wykluczenia ścieżki** do edycji i dodaj wykluczenia.

    1. Ustaw opcję **Włączone**.
    2. W sekcji **Opcje** wybierz pozycję **Pokaż**.
    3. Określ każdy folder we własnym wierszu w kolumnie **Nazwa wartości** .
    4. Jeśli określasz plik, upewnij się, że wprowadź w pełni kwalifikowaną ścieżkę do pliku, w tym literę dysku, ścieżkę folderu, nazwę pliku i rozszerzenie.
    5. Wprowadź **wartość 0** w kolumnie **Wartość** .

5. Wybierz pozycję **OK**.

6. Otwórz ustawienie **Wykluczenia rozszerzeń** do edycji i dodaj wykluczenia.

    1. Ustaw opcję **Włączone**.
    2. W sekcji **Opcje** wybierz pozycję **Pokaż**.
    3. Wprowadź każde rozszerzenie pliku we własnym wierszu w kolumnie **Nazwa wartości** .
    4. Wprowadź **wartość 0** w kolumnie **Wartość** .

7. Wybierz pozycję **OK**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie wykluczeń nazwy pliku, folderu lub rozszerzenia pliku przy użyciu poleceń cmdlet programu PowerShell

Używanie programu PowerShell do dodawania lub usuwania wykluczeń dla plików na podstawie rozszerzenia, lokalizacji lub nazwy pliku wymaga użycia kombinacji trzech poleceń cmdlet i odpowiedniego parametru listy wykluczeń. Wszystkie polecenia cmdlet znajdują się w [module defender](/powershell/module/defender/).

Format poleceń cmdlet jest następujący:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

W poniższej tabeli wymieniono polecenia cmdlet, których można użyć w `<cmdlet>` części polecenia cmdlet programu PowerShell:

|Akcja konfiguracji|Polecenie cmdlet programu PowerShell|
|:---|:---|
|Tworzenie lub zastępowanie listy|`Set-MpPreference`|
|Dodaj do listy|`Add-MpPreference`|
|Usuwanie elementu z listy|`Remove-MpPreference`|

W poniższej tabeli wymieniono wartości, których można użyć w `<exclusion list>` części polecenia cmdlet programu PowerShell:

|Typ wykluczenia|Parametr programu PowerShell|
|---|---|
|Wszystkie pliki z określonym rozszerzeniem pliku|`-ExclusionExtension`|
|Wszystkie pliki w folderze (w tym pliki w podkatalogach) lub określony plik|`-ExclusionPath`|

> [!IMPORTANT]
> Jeśli utworzono listę za `Set-MpPreference` pomocą polecenia cmdlet lub `Add-MpPreference`, ponowne użycie `Set-MpPreference` polecenia cmdlet spowoduje zastąpienie istniejącej listy.

Na przykład poniższy fragment kodu może spowodować wykluczenie Program antywirusowy Microsoft Defender skanów z rozszerzeniem `.test` pliku:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet Program antywirusowy Microsoft Defender i defender antivirus](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Użyj instrumentacji zarządzania Windows (WMI), aby skonfigurować wykluczenia nazwy pliku, folderu lub rozszerzenia pliku

Użyj [metod Set, Add i Remove klasy MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
ExclusionExtension
ExclusionPath
```

Używanie **ustawień**, **dodawania** i **usuwania** jest analogiczne do ich odpowiedników w programie PowerShell: `Set-MpPreference`, `Add-MpPreference`i `Remove-MpPreference`.

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie wykluczeń nazwy pliku, folderu lub rozszerzenia pliku za pomocą aplikacji Zabezpieczenia Windows

Aby uzyskać [instrukcje, zobacz Dodawanie wykluczeń w aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Użyj symboli wieloznacznych na liście wykluczeń nazwy pliku i folderu lub rozszerzenia

Podczas definiowania elementów na liście wykluczeń nazwy pliku lub ścieżki folderu można użyć gwiazdki `*`, znaku `?`zapytania lub zmiennych środowiskowych (takich jak `%ALLUSERSPROFILE%`) jako symboli wieloznacznych. Sposób interpretacji tych symboli wieloznacznych różni się od ich zwykłego użycia w innych aplikacjach i językach. Zapoznaj się z tą sekcją, aby zrozumieć ich konkretne ograniczenia.

> [!IMPORTANT]
> Istnieją kluczowe ograniczenia i scenariusze użycia dla tych symboli wieloznacznych:
> - Użycie zmiennej środowiskowej jest ograniczone do zmiennych maszynowych i tych mających zastosowanie do procesów uruchomionych jako konto NT AUTHORITY\SYSTEM.
> - Można użyć maksymalnie sześciu symboli wieloznacznych na wpis.
> - Nie można użyć symbolu wieloznacznego zamiast litery dysku.
> - Gwiazdka `*` w wykluczeniu folderu jest w miejscu dla pojedynczego folderu. Użyj wielu wystąpień, `\*\` aby wskazać wiele zagnieżdżonych folderów o nieokreślonych nazwach.
> - Obecnie Microsoft Endpoint Configuration Manager nie obsługuje symboli wieloznaczowych (takich jak `*` lub `?`).
    
W poniższej tabeli opisano sposób użycia symboli wieloznacznych i przedstawiono kilka przykładów.

|Symbol wieloznaczny|Przykłady|
|---|---|
|`*` (gwiazdka) <p> W **dołączaniu nazwy pliku i rozszerzenia pliku** gwiazdka zastępuje dowolną liczbę znaków i dotyczy tylko plików w ostatnim folderze zdefiniowanym w argumencie. <p> W przypadku **wykluczeń folderów** gwiazdka zastępuje pojedynczy folder. Użyj wielu `*` z ukośnikami folderów `\` , aby wskazać wiele zagnieżdżonych folderów. Po dopasowaniu liczby folderów z symbolami wieloznacznymi i nazwanych uwzględniono również wszystkie podfoldery.|`C:\MyData\*.txt` Zawiera `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` zawiera dowolny plik i `C:\somepath\Archives\Data` jego podfoldery oraz `C:\somepath\Authorized\Data` jego podfoldery i jego podfoldery <p> `C:\Serv\*\*\Backup` zawiera wszystkie pliki i `C:\Serv\Primary\Denied\Backup` jego podfoldery oraz `C:\Serv\Secondary\Allowed\Backup` jego podfoldery i jego podfoldery|
|`?` (znak zapytania)  <p> W **dołączaniu nazwy pliku i rozszerzenia pliku** znak zapytania zastępuje pojedynczy znak i dotyczy tylko plików w ostatnim folderze zdefiniowanym w argumencie. <p> W przypadku **wykluczeń folderów** znak zapytania zastępuje pojedynczy znak w nazwie folderu. Po dopasowaniu liczby folderów z symbolami wieloznacznymi i nazwanych uwzględniono również wszystkie podfoldery.|`C:\MyData\my?.zip` Zawiera `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` zawiera dowolny plik i `C:\somepath\P\Data` jego podfoldery  <p> `C:\somepath\test0?\Data` plików i `C:\somepath\test01\Data` jego podfolderów|
|Zmienne środowiskowe <p> Zdefiniowana zmienna jest wypełniana jako ścieżka podczas obliczania wykluczenia.|`%ALLUSERSPROFILE%\CustomLogFiles` będzie obejmować `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> W przypadku mieszania argumentu wykluczenia pliku z argumentem wykluczenia folderu reguły zostaną zatrzymane w dopasowanym folderze i nie będą wyszukiwać dopasowań plików w żadnych podfolderach.
> Można na przykład wykluczyć wszystkie pliki rozpoczynające się od "date" w folderach `c:\data\final\marked` i `c:\data\review\marked` za pomocą argumentu `c:\data\*\marked\date*`reguły .
> Ten argument nie będzie jednak odpowiadał żadnym plikom w podfolderach w obszarze `c:\data\final\marked` lub `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>Systemowe zmienne środowiskowe

W poniższej tabeli wymieniono i opisano zmienne środowiskowe konta systemowego.

|Ta systemowa zmienna środowiskowa...|Przekierowuje do tego|
|---|---|
|`%APPDATA%`|`C:\Users\UserName.DomainName\AppData\Roaming`|
|`%APPDATA%\Microsoft\Internet Explorer\Quick Launch`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch`|
|`%APPDATA%\Microsoft\Windows\Start Menu`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu`|
|`%APPDATA%\Microsoft\Windows\Start Menu\Programs`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`|
|`%LOCALAPPDATA%`|`C:\Windows\System32\config\systemprofile\AppData\Local`|
|`%ProgramData%`|`C:\ProgramData`|
|`%ProgramFiles%`|`C:\Program Files`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles%\Windows Sidebar\Gadgets`|`C:\Program Files\Windows Sidebar\Gadgets`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles(x86)%`|`C:\Program Files (x86)`|
|`%ProgramFiles(x86)%\Common Files`|`C:\Program Files (x86)\Common Files`|
|`%SystemDrive%`|`C:`|
|`%SystemDrive%\Program Files`|`C:\Program Files`|
|`%SystemDrive%\Program Files (x86)`|`C:\Program Files (x86)`|
|`%SystemDrive%\Users`|`C:\Users`|
|`%SystemDrive%\Users\Public`|`C:\Users\Public`|
|`%SystemRoot%`|`C:\Windows`|
|`%windir%`|`C:\Windows`|
|`%windir%\Fonts`|`C:\Windows\Fonts`|
|`%windir%\Resources`|`C:\Windows\Resources`|
|`%windir%\resources\0409`|`C:\Windows\resources\0409`|
|`%windir%\system32`|`C:\Windows\System32`|
|`%ALLUSERSPROFILE%`|`C:\ProgramData`|
|`%ALLUSERSPROFILE%\Application Data`|`C:\ProgramData\Application Data`|
|`%ALLUSERSPROFILE%\Documents`|`C:\ProgramData\Documents`|
|`%ALLUSERSPROFILE%\Documents\My Music\Sample Music`|`C:\ProgramData\Documents\My Music\Sample Music`|
|`%ALLUSERSPROFILE%\Documents\My Music`|`C:\ProgramData\Documents\My Music`|
|`%ALLUSERSPROFILE%\Documents\My Pictures`|`C:\ProgramData\Documents\My Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Pictures\Sample Pictures`|`C:\ProgramData\Documents\My Pictures\Sample Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Videos`|`C:\ProgramData\Documents\My Videos`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\DeviceMetadataStore`|`C:\ProgramData\Microsoft\Windows\DeviceMetadataStore`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\GameExplorer`|`C:\ProgramData\Microsoft\Windows\GameExplorer`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Ringtones`|`C:\ProgramData\Microsoft\Windows\Ringtones`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu`|`C:\ProgramData\Microsoft\Windows\Start Menu`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\StartUp`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Templates`|`C:\ProgramData\Microsoft\Windows\Templates`|
|`%ALLUSERSPROFILE%\Start Menu`|`C:\ProgramData\Start Menu`|
|`%ALLUSERSPROFILE%\Start Menu\Programs`| `C:\ProgramData\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Templates`|`C:\ProgramData\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\ConnectedSearch\Templates`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\ConnectedSearch\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\History`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\History`|
|`%PUBLIC%`|`C:\Users\Public`|
|`%PUBLIC%\AccountPictures`|`C:\Users\Public\AccountPictures`|
|`%PUBLIC%\Desktop`|`C:\Users\Public\Desktop`|
|`%PUBLIC%\Documents`|`C:\Users\Public\Documents`|
|`%PUBLIC%\Downloads`|`C:\Users\Public\Downloads`|
|`%PUBLIC%\Music\Sample Music`|`C:\Users\Public\Music\Sample Music`|
|`%PUBLIC%\Music\Sample Playlists`|`C:\Users\Public\Music\Sample Playlists`|
|`%PUBLIC%\Pictures\Sample Pictures`|`C:\Users\Public\Pictures\Sample Pictures`|
|`%PUBLIC%\RecordedTV.library-ms`|`C:\Users\Public\RecordedTV.library-ms`|
|`%PUBLIC%\Videos`|`C:\Users\Public\Videos`|
|`%PUBLIC%\Videos\Sample Videos`|`C:\Users\Public\Videos\Sample Videos`|
|`%USERPROFILE%`|`C:\Users\UserName`|
|`%USERPROFILE%\AppData\Local`|`C:\Users\UserName\AppData\Local`|
|`%USERPROFILE%\AppData\LocalLow`|`C:\Users\UserName\AppData\LocalLow`|
|`%USERPROFILE%\AppData\Roaming`|`C:\Users\UserName\AppData\Roaming`|

## <a name="review-the-list-of-exclusions"></a>Przejrzyj listę wykluczeń

Elementy na liście wykluczeń można pobrać przy użyciu jednej z następujących metod:

- [Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- [MpCmdRun](command-line-arguments-microsoft-defender-antivirus.md)
- [PowerShell](/powershell/module/defender)
- [Aplikacja Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Zmiany listy wykluczeń wprowadzone za pomocą zasady grupy **będą wyświetlane** na listach w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).
> Zmiany wprowadzone w aplikacji Zabezpieczenia Windows **nie będą wyświetlane** na listach zasady grupy.

Jeśli używasz programu PowerShell, możesz pobrać listę na dwa sposoby:

- Pobierz stan wszystkich preferencji Program antywirusowy Microsoft Defender. Każda lista jest wyświetlana w oddzielnych wierszach, ale elementy na każdej liście są łączone w ten sam wiersz.
- Zapisz stan wszystkich preferencji w zmiennej i użyj tej zmiennej, aby wywołać tylko konkretną listę, która Cię interesuje. Każde użycie `Add-MpPreference` jest zapisywane w nowym wierszu.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Weryfikowanie listy wykluczeń przy użyciu polecenia MpCmdRun

Aby sprawdzić wykluczenia za pomocą dedykowanego [narzędzia wiersza polecenia mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md), użyj następującego polecenia:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Sprawdzanie wykluczeń przy użyciu narzędzia MpCmdRun wymaga Program antywirusowy Microsoft Defender CAMP w wersji 4.18.2111-5.0 (wydanej w grudniu 2021 r.) lub nowszej.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Przejrzyj listę wykluczeń wraz ze wszystkimi innymi preferencjami Program antywirusowy Microsoft Defender przy użyciu programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Get-MpPreference
```

W poniższym przykładzie wyróżniono elementy znajdujące się na `ExclusionExtension` liście:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Dane wyjściowe programu PowerShell dla polecenia Get-MpPreference" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet Program antywirusowy Microsoft Defender i defender antivirus](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Pobieranie określonej listy wykluczeń przy użyciu programu PowerShell

Użyj następującego fragmentu kodu (wprowadź każdy wiersz jako oddzielne polecenie); Zastąp **elementy WDAVprefs** dowolną etykietą, którą chcesz nazwać zmienną:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

W poniższym przykładzie lista jest podzielona na nowe wiersze dla każdego użycia `Add-MpPreference` polecenia cmdlet:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Dane wyjściowe programu PowerShell zawierające tylko wpisy na liście wykluczeń" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet Program antywirusowy Microsoft Defender i defender antivirus](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Weryfikowanie list wykluczeń przy użyciu pliku testowego EICAR

Możesz sprawdzić, czy listy wykluczeń `Invoke-WebRequest` działają, używając programu PowerShell z poleceniem cmdlet lub klasą WebClient platformy .NET w celu pobrania pliku testowego.

W poniższym fragmencie kodu programu PowerShell zastąp `test.txt` ciąg plikiem zgodnym z regułami wykluczeń. Jeśli na przykład wykluczono rozszerzenie, zastąp `.testing` ciąg `test.txt` `test.testing`. Jeśli testujesz ścieżkę, upewnij się, że uruchamiasz polecenie cmdlet w tej ścieżce.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Jeśli Program antywirusowy Microsoft Defender zgłasza złośliwe oprogramowanie, reguła nie działa. Jeśli nie ma raportu o złośliwym oprogramowaniu i pobrany plik istnieje, wykluczenie działa. Możesz otworzyć plik, aby potwierdzić, że zawartość jest taka sama jak opisana w [witrynie internetowej pliku testowego EICAR](http://www.eicar.org/86-0-Intended-use.html).

Możesz również użyć następującego kodu programu PowerShell, który wywołuje klasę WebClient platformy .NET w celu pobrania pliku testowego — podobnie jak w `Invoke-WebRequest` przypadku polecenia cmdlet; zastąp `c:\test.txt` ciąg plikiem zgodnym z weryfikowaną regułą:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

Jeśli nie masz dostępu do Internetu, możesz utworzyć własny plik testowy EICAR, zapisując ciąg EICAR w nowym pliku tekstowym za pomocą następującego polecenia programu PowerShell:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Możesz również skopiować ciąg do pustego pliku tekstowego i spróbować go zapisać przy użyciu nazwy pliku lub folderu, który próbujesz wykluczyć.

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie i weryfikowanie wykluczeń w skanowaniach Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie wykluczeń Program antywirusowy Microsoft Defender na serwerze Windows](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
