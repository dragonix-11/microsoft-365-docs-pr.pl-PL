---
title: Typowe błędy, których należy unikać podczas definiowania wykluczeń
description: Unikaj typowych błędów podczas definiowania wykluczeń dla skanowania Program antywirusowy Microsoft Defender.
keywords: wykluczenia, pliki, rozszerzenie, typ pliku, nazwa folderu, nazwa pliku, skany
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 06/16/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 99d59c2027d3b34ad5c9c19444a51dd08cc22276
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128663"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Typowe błędy, których należy unikać podczas definiowania wykluczeń

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)
- Program antywirusowy Microsoft Defender 

**Platformy**

- System Windows
- macOS
- Linux

> [!IMPORTANT]
> **Ostrożnie dodaj wykluczenia**. Wykluczenia skanowania Program antywirusowy Microsoft Defender zmniejszają poziom ochrony urządzeń.

Możesz zdefiniować listę wykluczeń dla elementów, których nie chcesz skanować Program antywirusowy Microsoft Defender. Jednak wykluczone elementy mogą zawierać zagrożenia, które sprawiają, że urządzenie jest narażone na zagrożenia. W tym artykule opisano niektóre typowe błędy, których należy unikać podczas definiowania wykluczeń.

Przed zdefiniowaniem list [wykluczeń zobacz Rekomendacje definiowania wykluczeń](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Wykluczanie niektórych zaufanych elementów

Niektórych plików, typów plików, folderów lub procesów nie należy wykluczać ze skanowania, nawet jeśli ufasz, że nie są złośliwe.

Nie zdefiniuj wykluczeń dla lokalizacji folderów, rozszerzeń plików i procesów wymienionych w następujących sekcjach:

- [Lokalizacje folderów](#folder-locations)
- [Rozszerzenia plików](#file-extensions)
- [Procesów](#processes)

### <a name="folder-locations"></a>Lokalizacje folderów

> [!IMPORTANT]
> Niektórych folderów nie należy wykluczać ze skanowania, ponieważ są to foldery, w których można porzucić złośliwe pliki.

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących lokalizacji folderów:

- `%systemdrive%`
- `C:`, , `C:\`lub `C:\*`
- `%ProgramFiles%\Java` Lub `C:\Program Files\Java`
- `%ProgramFiles%\Contoso\`, , `C:\Program Files\Contoso\``%ProgramFiles(x86)%\Contoso\`, lub`C:\Program Files (x86)\Contoso\`
- `C:\Temp`, , `C:\Temp\`lub `C:\Temp\*`
- `C:\Users\` Lub `C:\Users\*`
- `C:\Users\<UserProfileName>\AppData\Local\Temp\` lub `C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`. **Zwróć uwagę na następujące ważne wyjątki dla SharePoint**: **Czy wykluczyć** `C:\Users\ServiceAccount\AppData\Local\Temp` lub `C:\Users\Default\AppData\Local\Temp` gdy używasz [ochrony antywirusowej na poziomie pliku w SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).
- `%Windir%\Prefetch`, , `C:\Windows\Prefetch``C:\Windows\Prefetch\`, lub`C:\Windows\Prefetch\*`
- `%Windir%\System32\Spool` Lub `C:\Windows\System32\Spool`
- `C:\Windows\System32\CatRoot2`
- `%Windir%\Temp`, , `C:\Windows\Temp``C:\Windows\Temp\`, lub`C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Platformy systemu Linux i macOS

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących lokalizacji folderów:

- `/`
- `/bin` Lub `/sbin`
- `/usr/lib`

### <a name="file-extensions"></a>Rozszerzenia plików

> [!IMPORTANT]
> Niektórych rozszerzeń plików nie należy wykluczać, ponieważ mogą to być typy plików używane w ataku.

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących rozszerzeń plików:

- `.7z`
- `.bat`
- `.bin`
- `.cab`
- `.cmd`
- `.com`
- `.cpl`
- `.dll`
- `.exe`
- `.fla`
- `.gif`
- `.gz`
- `.hta`
- `.inf`
- `.java`
- `.jar`
- `.job`
- `.jpeg`
- `.jpg`
- `.js`
- `.ko` Lub `.ko.gz`
- `.msi`
- `.ocx`
- `.png`
- `.ps1`
- `.py`
- `.rar`
- `.reg`
- `.scr`
- `.sys`
- `.tar`
- `.tmp`
- `.url`
- `.vbe`
- `.vbs`
- `.wsf`
- `.zip`

### <a name="processes"></a>Procesów

> [!IMPORTANT]
> Niektórych procesów nie należy wykluczać, ponieważ są używane podczas ataków.

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących procesów:

- `AcroRd32.exe`
- `addinprocess.exe`
- `addinprocess32.exe`
- `addinutil.exe`
- `bash.exe`
- `bginfo.exe`
- `bitsadmin.exe`
- `cdb.exe`
- `csi.exe`
- `dbghost.exe`
- `dbgsvc.exe`
- `dnx.exe`
- `dotnet.exe`
- `excel.exe`
- `fsi.exe`
- `fsiAnyCpu.exe`
- `iexplore.exe`
- `java.exe`
- `kd.exe`
- `lxssmanager.dll`
- `msbuild.exe`
- `mshta.exe`
- `ntkd.exe`
- `ntsd.exe`
- `outlook.exe`
- `psexec.exe`
- `powerpnt.exe`
- `powershell.exe`
- `rcsi.exe`
- `svchost.exe`
- `schtasks.exe`
- `system.management.automation.dll`
- `windbg.exe`
- `winword.exe`
- `wmic.exe`
- `wuauclt.exe`

> [!NOTE]
> Można wykluczyć typy plików, takie jak `.gif`, `.jpg`, `.jpeg`lub `.png` jeśli środowisko ma nowoczesne, aktualne oprogramowanie z rygorystycznymi zasadami aktualizacji w celu obsługi wszelkich luk w zabezpieczeniach.

#### <a name="linux-and-macos-platforms"></a>Platformy systemu Linux i macOS

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących procesów:

- `bash`
- `java`
- `python` I `python3`
- `sh`
- `zsh`

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Używanie tylko nazwy pliku na liście wykluczeń

Złośliwe oprogramowanie może mieć taką samą nazwę jak plik, któremu ufasz i który chcesz wykluczyć ze skanowania. W związku z tym, aby uniknąć wykluczania potencjalnego złośliwego oprogramowania ze skanowania, użyj w pełni kwalifikowanej ścieżki do pliku, który chcesz wykluczyć, zamiast używać tylko nazwy pliku. Jeśli na przykład chcesz wykluczyć `Filename.exe` ze skanowania, użyj pełnej ścieżki do pliku, takiej jak `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Używanie pojedynczej listy wykluczeń dla wielu obciążeń serwera

Nie używaj jednej listy wykluczeń do definiowania wykluczeń dla wielu obciążeń serwera. Podziel wykluczenia dla różnych obciążeń aplikacji lub usług na wiele list wykluczeń. Na przykład lista wykluczeń dla obciążenia serwera usług IIS musi różnić się od listy wykluczeń dla obciążenia SQL Server.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Używanie nieprawidłowych zmiennych środowiskowych jako symboli wieloznacznych na liście wykluczeń nazwy pliku i folderu lub rozszerzenia

Program antywirusowy Microsoft Defender Usługa działa w kontekście systemu przy użyciu konta LocalSystem, co oznacza, że pobiera informacje ze zmiennej środowiskowej systemu, a nie ze zmiennej środowiskowej użytkownika. Używanie zmiennych środowiskowych jako symbolu wieloznacznego na listach wykluczeń jest ograniczone do zmiennych systemowych i tych mających zastosowanie do procesów działających jako konto NT AUTHORITY\SYSTEM. W związku z tym nie używaj zmiennych środowiskowych użytkownika jako symboli wieloznacznych podczas dodawania Program antywirusowy Microsoft Defender folderów i wykluczeń procesów. Zobacz tabelę w obszarze [Zmienne środowiskowe systemu](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) , aby uzyskać pełną listę systemowych zmiennych środowiskowych.

Aby uzyskać informacje na temat używania [symboli wieloznacznych na listach wykluczeń, zobacz Używanie symboli wieloznacznych na liście wykluczeń](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) .

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)
