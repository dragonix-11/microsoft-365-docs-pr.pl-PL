---
title: Typowe błędy, których należy unikać podczas definiowania wykluczeń
description: Unikaj typowych błędów podczas definiowania wykluczeń Program antywirusowy Microsoft Defender skanów.
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
ms.openlocfilehash: 73234fd929406da475455baf21fbbf463216c660
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996737"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Typowe błędy, których należy unikać podczas definiowania wykluczeń

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Listę wykluczeń można zdefiniować dla elementów, które mają być Program antywirusowy Microsoft Defender skanowane. Tego typu wykluczone elementy mogą zawierać zagrożenia, które mogą naraźć urządzenie na zagrożenia. W tym artykule opisano typowe błędy, których należy unikać podczas definiowania wykluczeń.

Przed zdefiniowaniem list wykluczeń zobacz [Rekomendacje o definiowaniu wykluczeń](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Wykluczanie pewnych zaufanych elementów

Niektóre pliki, typy plików, foldery lub procesy nie powinny być wykluczone z skanowania, nawet jeśli ufasz im, że nie są złośliwe.

Nie definiuj wykluczeń dla lokalizacji folderów, rozszerzeń plików i procesów wymienionych w następujących sekcjach:
- Lokalizacje folderów
- Rozszerzenia plików
- Procesy

### <a name="folder-locations"></a>Lokalizacje folderów

Ogólnie nie należy definiować wykluczeń dla następujących lokalizacji folderów:

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

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**Zwróć uwagę na następujący wyjątek SharePoint**: `C:\Users\ServiceAccount\AppData\Local\Temp` Nie wyklucz podczas używania ochrony antywirusowej na poziomie pliku w [programie SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**Zwróć uwagę na następujący wyjątek SharePoint**: `C:\Users\Default\AppData\Local\Temp` Nie wyklucz podczas używania ochrony antywirusowej na poziomie pliku w [programie SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

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

#### <a name="linux-and-macos-platforms"></a>Platformy Linux i macOS

`/`

`/bin`

`/sbin`

`/usr/lib`


### <a name="file-extensions"></a>Rozszerzenia plików

Ogólnie nie należy definiować wykluczeń następujących rozszerzeń plików:

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

### <a name="processes"></a>Procesy

Ogólnie nie należy definiować wykluczeń dla następujących procesów:

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

#### <a name="linux-and-macos-platforms"></a>Platformy Linux i macOS

`bash`

`sh`

`python` i `python3`

`java`

`zsh`

> [!NOTE]
> Możesz wykluczyć typy plików, `.gif`takie jak , `.jpg``.jpeg``.png` lub, jeśli w Twoim środowisku jest zainstalowane nowoczesne, aktualne oprogramowanie z rygorystycznymi zasadami aktualizacji, aby wykorzystać ewentualne luki w zabezpieczeniach.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Używanie tylko nazwy pliku na liście wykluczeń

Złośliwe oprogramowanie może mieć taką samą nazwę jak nazwa pliku, który jest zaufany i który chcesz wykluczyć z skanowania. Dlatego, aby zapobiec skanowaniu potencjalnego złośliwego oprogramowania, użyj w pełni kwalifikowanej ścieżki do pliku, który chcesz wykluczyć, zamiast używać tylko nazwy pliku. Jeśli na przykład chcesz wykluczyć z `Filename.exe` funkcji skanowania, użyj pełnej ścieżki do pliku, na przykład `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Korzystanie z jednej listy wykluczeń dla wielu obciążeń serwera

Nie należy używać jednej listy wykluczeń do definiowania wykluczeń dla wielu obciążeń serwerów. Podziel wykluczenia dla różnych obciążeń aplikacji lub usług na wiele list wykluczeń. Na przykład lista wykluczeń dla Twojego obciążenia serwera usług IIS musi różnić się od listy wykluczeń Twojego SQL Server obciążenia pracą.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Używanie nieprawidłowych zmiennych środowiskowych jako symboli wieloznacznych w nazwach plików i ścieżkach folderów lub na listach wykluczeń rozszerzenia

Program antywirusowy Microsoft Defender Service działa w kontekście systemowym przy użyciu konta LocalSystem, co oznacza, że pobiera informacje ze zmiennej środowiskowej systemu, a nie ze zmiennej środowiskowej użytkownika. Używanie zmiennych środowiskowych jako symboli wieloznacznych na listach wykluczeń jest ograniczone do zmiennych systemowych i mających zastosowanie do procesów uruchomionych jako konto NT AUTHORITY\SYSTEM. Dlatego nie należy używać zmiennych środowiska użytkownika jako symboli wieloznacznych podczas dodawania Program antywirusowy Microsoft Defender wykluczeń folderów i procesów. Pełną [listę zmiennych](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) środowiskowych systemowych można znaleźć w tabeli w obszarze Systemowe zmienne środowiska.

Aby [uzyskać informacje na](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) temat używania symboli wieloznacznych na listach wykluczeń, zobacz Używanie symboli wieloznacznych w nazwach plików i ścieżkach folderów lub na listach wykluczeń rozszerzenia.
