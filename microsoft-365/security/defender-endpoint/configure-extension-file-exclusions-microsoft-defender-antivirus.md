---
title: Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia, nazwy lub lokalizacji
description: Wyklucz pliki z Program antywirusowy Microsoft Defender skanów na podstawie ich rozszerzenia pliku, nazwy pliku lub lokalizacji.
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
ms.date: 02/27/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: be22c80e51551b5de2a2aeed2f0dff0db9a8481f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323657"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie rozszerzenia pliku i lokalizacji folderu

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Można definiować wykluczenia dotyczące Program antywirusowy Microsoft Defender, które dotyczą zaplanowanych skanów[, skanów](schedule-antivirus-scans.md) na żądanie oraz zawsze wł. ochrony i monitorowania w czasie [rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md). [](run-scan-microsoft-defender-antivirus.md) **Ogólnie rzecz biorąc, nie należy stosować wykluczeń**. Jeśli chcesz zastosować wykluczenia, możesz wybrać jeden z kilku rodzajów:

- Wykluczenia oparte na rozszerzeniach plików i lokalizacjach folderów (opisane w tym artykule)
- [Wykluczenia dotyczące plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender wykluczenia nie mają zastosowania do innych funkcji programu Microsoft Defender dla punktu końcowego, takich jak wykrywanie i reagowanie w punktach końcowych [(EDR)](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response), zmniejszenie powierzchni ataków [(ASR, Attack Surface Reduction)](/microsoft-365/security/defender-endpoint/attack-surface-reduction) i kontrolowany dostęp do [folderu](/microsoft-365/security/defender-endpoint/controlled-folders) . Pliki wykluczone przy użyciu metod opisanych w tym artykule nadal mogą wyzwalać alerty EDR innych wykrycia.
> Aby ogólnie wykluczyć pliki, dodaj je do niestandardowych wskaźników programu Microsoft Defender [for Endpoint.](/microsoft-365/security/defender-endpoint/manage-indicators)

## <a name="before-you-begin"></a>Przed rozpoczęciem...

Zobacz [Rekomendacje o definiowaniu wykluczeń](configure-exclusions-microsoft-defender-antivirus.md) przed zdefiniowaniem list wykluczeń.

## <a name="exclusion-lists"></a>Listy wykluczeń

Aby wykluczyć określone pliki z Program antywirusowy Microsoft Defender, zmodyfikuj listy wykluczeń. Program antywirusowy Microsoft Defender uwzględnia wiele automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania, takich jak używane w zarządzaniu przedsiębiorstwem, zarządzaniu bazami danych i innych scenariuszach i sytuacjach przedsiębiorstwa.

> [!NOTE]
> Wykluczenia dotyczą również wykrywania potencjalnie niechcianych aplikacji (PUA).
>
> Wykluczenia automatyczne mają zastosowanie tylko Windows Server 2016 i nowszych. Te wykluczenia nie są widoczne w aplikacji Zabezpieczenia Windows ani w programie PowerShell.

W poniższej tabeli przedstawiono kilka przykładów wykluczeń opartych na rozszerzeniu pliku i lokalizacji folderu. 
<br/><br/>

|Wykluczenie|Przykłady|Lista wykluczeń|
|---|---|---|
|Dowolny plik z określonym rozszerzeniem|Wszystkie pliki o określonym rozszerzeniu, w dowolnym miejscu na komputerze. <p> Prawidłowa składnia: `.test` i `test`|Wykluczenia rozszerzeń|
|Dowolny plik w określonym folderze|Wszystkie pliki w folderze `c:\test\sample`|Wykluczenia plików i folderów|
|Określony plik w określonym folderze|`c:\sample\sample.test` Tylko plik|Wykluczenia plików i folderów|
|Określony proces|Plik wykonywalny `c:\test\process.exe`|Wykluczenia plików i folderów|

## <a name="characteristics-of-exclusion-lists"></a>Cechy list wykluczeń

- Wykluczenia folderów mają zastosowanie do wszystkich plików i folderów w tym folderze, o ile podfolder nie jest punktem ponownego rozdzielania. Podfoldery rozdzielane punktami należy wykluczać oddzielnie.
- Rozszerzenia plików mają zastosowanie do dowolnej nazwy pliku o zdefiniowanym rozszerzeniu, jeśli ścieżka lub folder nie jest zdefiniowany.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Ważne uwagi dotyczące wykluczeń opartych na rozszerzeniach plików i lokalizacjach folderów

- Zastosowanie symboli wieloznacznych, takich jak gwiazdka (\*), spowoduje zmianę sposobu interpretowania reguł wykluczeń. Ważne informacje [na](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) temat działania symboli wieloznacznych można znaleźć w sekcji Używanie symboli wieloznacznych w nazwach plików i ścieżkach folderów lub na listach wykluczeń rozszerzenia.

- Nie wykluczaj zamapowanych dysków sieciowych. Określ rzeczywistą ścieżkę sieciową.

- Foldery, które są różnych punktów utworzonych po Program antywirusowy Microsoft Defender usługi i które zostały dodane do listy wykluczeń, nie będą uwzględniane. Uruchom ponownie usługę (przez ponowne uruchomienie Windows), aby nowe punkty rozsyłania uznane za ważne miejsce docelowe wykluczeń.

- Wykluczenia mają zastosowanie do [zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md), skanów [na żądanie](run-scan-microsoft-defender-antivirus.md) i ochrony [w](configure-real-time-protection-microsoft-defender-antivirus.md) czasie rzeczywistym, ale nie w programie Defender for Endpoint. W celu zdefiniowania wykluczeń dla usługi Defender for Endpoint użyj [wskaźników niestandardowych](manage-indicators.md).

- Domyślnie lokalne zmiany wprowadzone na listach (przez użytkowników z uprawnieniami administratora, w tym zmiany wprowadzone za pomocą programu PowerShell i usługi WMI) będą scalane z listami zdefiniowanymi (i wdrożonym) przez usługi zasady grupy, Menedżer konfiguracji lub Intune. Listy zasady grupy mają pierwszeństwo w przypadku konfliktów. Ponadto zmiany na liście wykluczeń wprowadzone przy zasady grupy są widoczne w Zabezpieczenia Windows [aplikacji](microsoft-defender-security-center-antivirus.md).

- Aby zezwolić na zastępowanie ustawień wdrożenia zarządzanego przez zmiany lokalne, skonfiguruj scalanie list wykluczeń zdefiniowanych [lokalnie i globalnie](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Konfigurowanie listy wykluczeń na podstawie nazwy folderu lub rozszerzenia pliku

Możesz wybrać jedną z kilku metod definiowania wykluczeń dla Program antywirusowy Microsoft Defender.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie nazwy pliku, folderu lub wykluczeń rozszerzenia plików przy użyciu usługi Intune

Zobacz następujące artykuły:

- [Konfigurowanie ustawień ograniczeń urządzeń w aplikacji Microsoft Intune](/intune/device-restrictions-configure)
- [Program antywirusowy Microsoft Defender ograniczeń urządzenia dla aplikacji Windows 10 Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie Menedżer konfiguracji plików, folderów i wykluczeń rozszerzenia plików przy użyciu programu Menedżer konfiguracji plików

Zobacz [Jak tworzyć i wdrażać zasady ochrony przed złośliwym oprogramowaniem: Ustawienia wykluczeń](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings), aby uzyskać szczegółowe informacje na temat Microsoft Endpoint Manager (bieżąca gałąź).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Konfigurowanie wykluczeń folderów lub rozszerzeń plików przy użyciu programu zasady grupy plików

> [!NOTE]
> W przypadku określenia w pełni kwalifikowanej ścieżki do pliku zostanie wykluczony tylko ten plik. Jeśli wykluczono folder, wszystkie pliki i podkategorie w tym folderze są wykluczane.

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera i** wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **wykluczeń**.

4. Otwórz ustawienie **Wykluczeń ścieżki** do edycji i dodaj wykluczenia.
    1. Ustaw dla opcji wartość **Włączone**.
    2. W sekcji **Opcje** wybierz pozycję **Pokaż**.
    3. Określ każdy folder w swoim wierszu pod **kolumną Nazwa** wartości.
    4. Jeśli plik jest określony, wprowadź w pełni kwalifikowaną ścieżkę do pliku, w tym literę dysku, ścieżkę folderu, nazwę pliku i rozszerzenie. 
    5. Wprowadź **wartość 0** w **kolumnie** Wartość.

5. Wybierz pozycję **OK**.

6. Otwórz ustawienie **Wykluczenia rozszerzeń w celu** edytowania i dodaj wykluczenia.
    1. Ustaw dla opcji wartość **Włączone**.
    2. W sekcji **Opcje** wybierz pozycję **Pokaż**.
    3. Wprowadź poszczególne rozszerzenia plików w wierszu w **kolumnie Nazwa** wartości.
    4. Wprowadź **wartość 0** w **kolumnie** Wartość.

7. Wybierz pozycję **OK**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie nazw plików, folderów lub wykluczeń rozszerzenia plików przy użyciu poleceń cmdlet programu PowerShell

Dodanie lub usunięcie wykluczeń plików na podstawie rozszerzenia, lokalizacji lub nazwy pliku za pomocą programu PowerShell wymaga użycia kombinacji trzech poleceń cmdlet i odpowiedniego parametru listy wykluczeń. Wszystkie polecenia cmdlet znajdują się w [module Defender](/powershell/module/defender/).

Format dla tych cmdlet jest następujący:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

W poniższej tabeli wymieniono polecenia cmdlet, `<cmdlet>` których można używać w części polecenia cmdlet programu PowerShell:

<br/><br/>

|Akcja konfiguracji|Polecenie cmdlet programu PowerShell|
|:---|:---|
|Tworzenie lub zastępowanie listy|`Set-MpPreference`|
|Dodawanie do listy|`Add-MpPreference`|
|Usuwanie elementu z listy|`Remove-MpPreference`|

W poniższej tabeli wymieniono wartości, których można `<exclusion list>` użyć w części polecenia cmdlet programu PowerShell:

<br/><br/>

|Typ wykluczenia|Parametr programu PowerShell|
|---|---|
|Wszystkie pliki z określonym rozszerzeniem pliku|`-ExclusionExtension`|
|Wszystkie pliki w folderze (w tym pliki w podkierunkowych) lub określony plik|`-ExclusionPath`|

> [!IMPORTANT]
> Jeśli utworzono listę za pomocą polecenia `Set-MpPreference` `Add-MpPreference`cmdlet lub , `Set-MpPreference` użycie ponownie spowoduje zastąpienie istniejącej listy.

Na przykład poniższy fragment kodu może spowodować, Program antywirusowy Microsoft Defender skany wykluczą wszystkie pliki z rozszerzeniem `.test` pliku:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) do konfigurowania i uruchamiania Program antywirusowy Microsoft Defender i poleceń [cmdlet programu antywirusowego Defender](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie Windows nazw plików, folderów i wykluczeń rozszerzeń plików przy użyciu programu Windows Management Instrumentation (WMI)

Za pomocą [metod Set, Add i Remove](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) MSFT_MpPreference właściwości:

```WMI
ExclusionExtension
ExclusionPath
```

Polecenia **Ustaw**, **Dodaj** i **Usuń są** analogiczne do ich odpowiedników w programie PowerShell: `Set-MpPreference`, `Add-MpPreference`i `Remove-MpPreference`.

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Konfigurowanie nazwy Zabezpieczenia Windows, folderu lub wykluczeń rozszerzenia plików za pomocą aplikacji do konfigurowania plików

Aby [uzyskać instrukcje, zobacz Dodawanie Zabezpieczenia Windows w](microsoft-defender-security-center-antivirus.md) aplikacji mobilnej.

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Używanie symboli wieloznacznych w nazwach plików i ścieżkach folderów lub na listach wykluczeń rozszerzenia

Podczas definiowania `*`elementów na liście wykluczeń nazwy pliku lub ścieżki folderu możesz użyć gwiazdki, `?`znaku zapytania lub zmiennych środowiska ( `%ALLUSERSPROFILE%`takich jak ) jako symboli wieloznacznych. Sposób interpretowania tych symboli wieloznacznych różni się od ich zwykłego użycia w innych aplikacjach i językach. Koniecznie przeczytaj tę sekcję, aby poznać ich specyficzne ograniczenia.

> [!IMPORTANT]
> Istnieją kluczowe ograniczenia i scenariusze użycia tych symboli wieloznacznych:
>
> - Użycie zmiennych środowiskowych jest ograniczone do zmiennych komputerowych i mających zastosowanie do procesów uruchomionych jako konto NT AUTHORITY\SYSTEM.
> - W jednym wpisie można użyć maksymalnie sześciu symboli wieloznacznych.
> - Nie można użyć symbolu wieloznacznego w miejscu litery dysku.
> - Gwiazdka `*` w wykluczeniu folderu oznacza jeden folder. Wiele wystąpień tego folderu oznacza `\*\` wiele folderów zagnieżdżonych o nieokreślonych nazwach.
> - Obecnie Microsoft Endpoint Configuration Manager nie obsługuje symboli wieloznacznych (takich jak `*` lub `?`).
    
W poniższej tabeli opisano sposób, w jaki można używać symboli wieloznacznych, oraz po przedstawiono kilka przykładów.

<br/><br/>

|Symbol wieloznaczny|Przykłady|
|---|---|
|`*` (gwiazdka) <p> W **dołączeniach** nazwy pliku i rozszerzenia pliku gwiazdka zastępuje dowolną liczbę znaków i dotyczy tylko plików w ostatnim folderze zdefiniowanym w tym argumentie. <p> W **przypadku wykluczeń** folderów gwiazdka zastępuje jeden folder. Użyj wielu `*` ukośników folderów, aby `\` wskazać wiele folderów zagnieżdżonych. Po dopasowaniu liczby folderów z symbolami wieloznacznymi i nazwanymi zostaną również uwzględnione wszystkie podfoldery.|`C:\MyData\*.txt` zawiera `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` każdy plik w, jego `C:\somepath\Archives\Data` podfoldery i `C:\somepath\Authorized\Data` jego podfoldery <p> `C:\Serv\*\*\Backup` każdy plik w, jego `C:\Serv\Primary\Denied\Backup` podfoldery i `C:\Serv\Secondary\Allowed\Backup` jego podfoldery|
|`?` (znak zapytania)  <p> W **dołączeniach** nazwy pliku i rozszerzenia pliku znak zapytania zastępuje jeden znak i dotyczy tylko plików w ostatnim folderze zdefiniowanym w tym argumentze. <p> W **przypadku wykluczeń** folderów znak zapytania zastępuje jeden znak w nazwie folderu. Po dopasowaniu liczby folderów z symbolami wieloznacznymi i nazwanymi zostaną również uwzględnione wszystkie podfoldery.|`C:\MyData\my?.zip` zawiera `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` uwzględnia każdy plik w jego `C:\somepath\P\Data` podfolderach  <p> `C:\somepath\test0?\Data`każdy plik z jego podfolderów `C:\somepath\test01\Data`|
|Zmienne środowiskowe <p> Zdefiniowana zmienna jest wypełniana ścieżką podczas oceny wykluczenia.|`%ALLUSERSPROFILE%\CustomLogFiles` dołączyłaby `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Jeśli zmieszasz argument wykluczeń plików z argumentem wykluczeń folderów, reguły przestaną odpowiadać argumentowi plik w dopasowanej folderze i nie będą szukać dopasowań plików w żadnym podfolderze.
>
> Możesz na przykład wykluczyć wszystkie pliki, które zaczynają się od "daty" `c:\data\final\marked` `c:\data\review\marked` w folderach, i używając argumentu reguła `c:\data\*\marked\date*`.
>
> Ten argument nie będzie jednak taki jak żaden plik w podfolderach `c:\data\final\marked` w obszarze lub `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>Zmienne środowiska systemowego

W poniższej tabeli wymieniono i opisano zmienne środowiska konta systemowego.

<br/><br/>

|Ta zmienna środowiskowa systemu...|Przekierowuje do tego|
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

Elementy z listy wykluczeń można pobrać przy użyciu jednej z następujących metod:

- [Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- MpCmdRun
- PowerShell
- [Zabezpieczenia Windows aplikacji](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Zmiany listy wykluczeń wprowadzone przy zasady grupy **będą wyświetlane** na listach w [Zabezpieczenia Windows aplikacji](microsoft-defender-security-center-antivirus.md).
>
> Zmiany wprowadzone w aplikacji Zabezpieczenia Windows **nie będą wyświetlane** na zasady grupy listach.

Jeśli korzystasz z programu PowerShell, możesz pobrać listę na dwa sposoby:

- Pobieranie stanu wszystkich Program antywirusowy Microsoft Defender preferencji. Każda lista jest wyświetlana w osobnych wierszach, ale elementy na każdej liście są łączone w ten sam wiersz.
- Zapisz stan wszystkich preferencji dla zmiennej i za jej pomocą wywołaj tylko określoną listę, która Cię interesuje. Każde użycie jest `Add-MpPreference` zapisywane w nowym wierszu.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Sprawdzanie poprawności listy wykluczeń przy użyciu programu MpCmdRun

Aby sprawdzić wykluczenia przy użyciu dedykowanego narzędzia wiersza [mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md), użyj następującego polecenia:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Sprawdzanie wykluczeń w programie MpCmdRun wymaga Program antywirusowy Microsoft Defender PC w wersji 4.18.2111-5.0 (wydanej w grudniu 2021 r.) lub nowszej.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Przejrzyj listę wykluczeń obok wszystkich innych preferencji Program antywirusowy Microsoft Defender przy użyciu programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Get-MpPreference
```

W poniższym przykładzie wyróżnione `ExclusionExtension` są elementy znajdujące się na liście:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Dane wyjściowe programu PowerShell dla polecenia Get-MpPreference.":::

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) do konfigurowania i uruchamiania Program antywirusowy Microsoft Defender i poleceń [cmdlet programu antywirusowego Defender](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Pobieranie określonej listy wykluczeń przy użyciu programu PowerShell

Użyj następującego fragmentu kodu (wprowadź każdy wiersz jako oddzielne polecenie); **Zamień pola WDAVprefs na** etykiety, którym chcesz nazwać zmienną:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

W poniższym przykładzie lista jest dzielona na nowe wiersze dla każdego użycia polecenia `Add-MpPreference` cmdlet:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Dane wyjściowe programu PowerShell pokazujące tylko wpisy na liście wykluczeń.":::

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) do konfigurowania i uruchamiania Program antywirusowy Microsoft Defender i poleceń [cmdlet programu antywirusowego Defender](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Sprawdzanie poprawności list wykluczeń przy użyciu pliku testowego EICAR

Możesz sprawdzić, czy listy wykluczeń działają, używając programu PowerShell `Invoke-WebRequest` z poleceniem cmdlet lub klasą .NET WebClient do pobrania pliku testowego.

W poniższym fragmencie programu PowerShell zastąp `test.txt` plik zgodny z regułami wykluczeń. Na przykład jeśli wykluczono rozszerzenie `.testing` , zamień je na `test.txt` `test.testing`. Jeśli testujesz ścieżkę, upewnij się, że uruchamiasz polecenie cmdlet w tej ścieżce.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Jeśli Program antywirusowy Microsoft Defender raport złośliwego oprogramowania, reguła nie działa. Jeśli nie ma żadnego raportu o złośliwym oprogramowaniu, a pobrany plik już istnieje, wówczas wykluczenie działa. Możesz otworzyć plik w celu potwierdzenia, że zawartość jest taka sama jak ta, co opisano w witrynie [internetowej pliku testowego EICAR](http://www.eicar.org/86-0-Intended-use.html).

Możesz również użyć następującego kodu programu PowerShell, który wywołuje klasę .NET WebClient w celu pobrania pliku testowego — `Invoke-WebRequest` tak jak w przypadku polecenia cmdlet; `c:\test.txt` zamień go na plik zgodny z regułą, która jest sprawdzania poprawności:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

Jeśli nie masz dostępu do Internetu, możesz utworzyć własny plik testowy EICAR, zapisuc ciąg znaków EICAR w nowym pliku tekstowym za pomocą następującego polecenia programu PowerShell:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Możesz również skopiować ciąg do pustego pliku tekstowego i spróbować zapisać go pod nazwą pliku lub w folderze, który próbujesz wykluczyć.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie i weryfikowanie wykluczeń w Program antywirusowy Microsoft Defender skanowaniach](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie Program antywirusowy Microsoft Defender wykluczeń na Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
