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
ms.date: 10/19/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: b5dc8832839c86fee98e9f27264b70e6a63f380c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790707"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Typowe błędy, których należy unikać podczas definiowania wykluczeń

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender 

**Platformy**
- System Windows
- macOS
- Linux

Możesz zdefiniować listę wykluczeń dla elementów, których nie chcesz skanować Program antywirusowy Microsoft Defender. Takie wykluczone elementy mogą zawierać zagrożenia, które sprawiają, że urządzenie jest narażone na zagrożenia. W tym artykule opisano niektóre typowe błędy, których należy unikać podczas definiowania wykluczeń.

Przed zdefiniowaniem list [wykluczeń zobacz Rekomendacje definiowania wykluczeń](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Wykluczanie niektórych zaufanych elementów

Niektórych plików, typów plików, folderów lub procesów nie należy wykluczać ze skanowania, nawet jeśli ufasz, że nie są złośliwe.

Nie należy definiować wykluczeń dla lokalizacji folderów, rozszerzeń plików i procesów wymienionych w następujących sekcjach:
- Lokalizacje folderów
- Rozszerzenia plików
- Procesów

### <a name="folder-locations"></a>Lokalizacje folderów

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących lokalizacji folderów:

`%systemdrive%`

`C:`

`C:\`

`C:\*`

`%ProgramFiles%\Java`

`C:\Program Files\Java`

`%ProgramFiles%\Contoso\`

`C:\Program Files\Contoso\`

`%ProgramFiles(x86)%\Contoso\`

`C:\Program Files (x86)\Contoso\`

`C:\Temp`

`C:\Temp\`

`C:\Temp\*`

`C:\Users\`

`C:\Users\*`

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**Zwróć uwagę na następujący wyjątek dla SharePoint**: Nie wykluczaj `C:\Users\ServiceAccount\AppData\Local\Temp` w przypadku korzystania z [ochrony antywirusowej na poziomie pliku w SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**Zwróć uwagę na następujący wyjątek dla SharePoint**: Nie wykluczaj `C:\Users\Default\AppData\Local\Temp` w przypadku korzystania z [ochrony antywirusowej na poziomie pliku w SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`%Windir%\Prefetch`

`C:\Windows\Prefetch`

`C:\Windows\Prefetch\`

`C:\Windows\Prefetch\*`

`%Windir%\System32\Spool`

`C:\Windows\System32\Spool`

`C:\Windows\System32\CatRoot2`
`%Windir%\Temp`

`C:\Windows\Temp`

`C:\Windows\Temp\`

`C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Platformy systemu Linux i macOS

`/`

`/bin`

`/sbin`

`/usr/lib`


### <a name="file-extensions"></a>Rozszerzenia plików

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących rozszerzeń plików:

`.7z`

`.bat`

`.bin`

`.cab`

`.cmd`

`.com`

`.cpl`

`.dll`

`.exe`

`.fla`

`.gif`

`.gz`

`.hta`

`.inf`

`.java`

`.jar`

`.job`

`.jpeg`

`.jpg`

`.js`

`.ko`

`.ko.gz`

`.msi`

`.ocx`

`.png`

`.ps1`

`.py`

`.rar`

`.reg`

`.scr`

`.sys`

`.tar`

`.tmp`

`.url`

`.vbe`

`.vbs`

`.wsf`

`.zip`

### <a name="processes"></a>Procesów

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla następujących procesów:

`AcroRd32.exe`

`bitsadmin.exe`

`excel.exe`

`iexplore.exe`

`java.exe`

`outlook.exe`

`psexec.exe`

`powerpnt.exe`

`powershell.exe`

`schtasks.exe`

`svchost.exe`

`wmic.exe`

`winword.exe`

`wuauclt.exe`

`addinprocess.exe`

`addinprocess32.exe`

`addinutil.exe`

`bash.exe`

`bginfo.exe`

`cdb.exe`

`csi.exe`

`dbghost.exe`

`dbgsvc.exe`

`dnx.exe`

`dotnet.exe`

`fsi.exe`

`fsiAnyCpu.exe`

`kd.exe`

`ntkd.exe`

`lxssmanager.dll`

`msbuild.exe`

`mshta.exe`

`ntsd.exe`

`rcsi.exe`

`system.management.automation.dll`

`windbg.exe`

#### <a name="linux-and-macos-platforms"></a>Platformy systemu Linux i macOS

`bash`

`sh`

`python` I `python3`

`java`

`zsh`

> [!NOTE]
> Można wykluczyć typy plików, takie jak `.gif`, `.jpg`, `.jpeg`lub `.png` jeśli środowisko ma nowoczesne, aktualne oprogramowanie z rygorystycznymi zasadami aktualizacji w celu obsługi wszelkich luk w zabezpieczeniach.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Używanie tylko nazwy pliku na liście wykluczeń

Złośliwe oprogramowanie może mieć taką samą nazwę jak plik, któremu ufasz i który chcesz wykluczyć ze skanowania. W związku z tym, aby uniknąć wykluczania potencjalnego złośliwego oprogramowania ze skanowania, użyj w pełni kwalifikowanej ścieżki do pliku, który chcesz wykluczyć, zamiast używać tylko nazwy pliku. Jeśli na przykład chcesz wykluczyć `Filename.exe` ze skanowania, użyj pełnej ścieżki do pliku, takiej jak `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Używanie pojedynczej listy wykluczeń dla wielu obciążeń serwera

Nie używaj jednej listy wykluczeń do definiowania wykluczeń dla wielu obciążeń serwera. Podziel wykluczenia dla różnych obciążeń aplikacji lub usług na wiele list wykluczeń. Na przykład lista wykluczeń dla obciążenia serwera usług IIS musi różnić się od listy wykluczeń dla obciążenia SQL Server.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Używanie nieprawidłowych zmiennych środowiskowych jako symboli wieloznacznych na liście wykluczeń nazwy pliku i folderu lub rozszerzenia

Program antywirusowy Microsoft Defender Usługa działa w kontekście systemu przy użyciu konta LocalSystem, co oznacza, że pobiera informacje ze zmiennej środowiskowej systemu, a nie ze zmiennej środowiskowej użytkownika. Używanie zmiennych środowiskowych jako symbolu wieloznacznego na listach wykluczeń jest ograniczone do zmiennych systemowych i tych mających zastosowanie do procesów działających jako konto NT AUTHORITY\SYSTEM. W związku z tym nie używaj zmiennych środowiskowych użytkownika jako symboli wieloznacznych podczas dodawania Program antywirusowy Microsoft Defender wykluczeń folderu i procesu. Zobacz tabelę w obszarze [Zmienne środowiskowe systemu](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) , aby uzyskać pełną listę systemowych zmiennych środowiskowych.

Aby uzyskać informacje na temat używania [symboli wieloznacznych na listach wykluczeń, zobacz Używanie symboli wieloznacznych na liście wykluczeń](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) .

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)
