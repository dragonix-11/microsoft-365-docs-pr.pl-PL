---
title: Konfigurowanie wykluczeń Program antywirusowy Microsoft Defender na serwerze Windows
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server zawiera automatyczne wykluczenia oparte na roli serwera. Można również dodać wykluczenia niestandardowe.
keywords: wykluczenia, serwer, automatyczne wykluczenia, automatyczne, niestandardowe, skany, Program antywirusowy Microsoft Defender
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
ms.date: 02/04/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 487c253adc422d69be5ce011ffef1fc1a014474b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789783"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Konfigurowanie wykluczeń Program antywirusowy Microsoft Defender na serwerze Windows


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender na Windows Server 2016 i Windows Server 2019 automatycznie rejestruje Cię w niektórych wykluczeń, zgodnie z definicją określonej roli serwera. Te wykluczenia nie są wyświetlane na standardowych listach wykluczeń, które są wyświetlane w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

Oprócz automatycznych wykluczeń zdefiniowanych przez rolę serwera można dodawać lub usuwać wykluczenia niestandardowe. Aby to zrobić, zapoznaj się z następującymi artykułami:
- [Konfigurowanie i weryfikowanie wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Należy pamiętać o kilku kwestiach

Należy pamiętać o następujących ważnych kwestiach:

- Wykluczenia niestandardowe mają pierwszeństwo przed automatycznymi wykluczeniami.
- Automatyczne wykluczenia mają zastosowanie tylko do skanowania ochrony w czasie rzeczywistym (RTP). Automatyczne wykluczenia nie są uwzględniane podczas pełnego, szybkiego lub na żądanie skanowania.
- Wykluczenia niestandardowe i zduplikowane nie powodują konfliktu z automatycznymi wykluczeniami.
- Program antywirusowy Microsoft Defender używa narzędzi do obsługi i zarządzania obrazami wdrożenia (DISM) w celu określenia, które role są zainstalowane na komputerze.
- Windows Server 2012 R2 nie ma Program antywirusowy Microsoft Defender jako funkcji instalowania. Po dołączeniu tych serwerów do usługi Defender for Endpoint zainstalujesz Program antywirusowy Windows Defender i zostaną zastosowane domyślne wykluczenia dla plików systemu operacyjnego. Jednak wykluczenia dla ról serwera (jak określono poniżej) nie są stosowane automatycznie i należy odpowiednio skonfigurować te wykluczenia. Aby dowiedzieć się więcej, zobacz [Dołączanie serwerów Windows do usługi Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md).

Ten artykuł zawiera omówienie wykluczeń dla Program antywirusowy Microsoft Defender Windows Server 2016 lub nowszych.

Ponieważ Program antywirusowy Microsoft Defender jest wbudowana w Windows Server 2016 i później, wykluczenia plików systemu operacyjnego i ról serwera są automatycznie wykonywane. Można jednak zdefiniować wykluczenia niestandardowe. W razie potrzeby możesz również zrezygnować z automatycznych wykluczeń.

Ten artykuł zawiera następujące sekcje:

<br/><br/>

|Sekcji|Opis|
|---|---|
|[Automatyczne wykluczenia w Windows Server 2016 lub nowszych](#automatic-exclusions-on-windows-server-2016-or-later)|Opisuje dwa główne typy automatycznych wykluczeń i zawiera szczegółową listę automatycznych wykluczeń|
|[Rezygnacja z automatycznych wykluczeń](#opting-out-of-automatic-exclusions)|Zawiera ważne zagadnienia i procedury opisujące sposób rezygnacji z automatycznych wykluczeń|
|[Definiowanie wykluczeń niestandardowych](#defining-custom-exclusions)|Zawiera linki do informacji z instrukcjami dotyczącymi definiowania wykluczeń niestandardowych|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Automatyczne wykluczenia w Windows Server 2016 lub nowszych

W Windows Server 2016 lub nowszym nie należy definiować następujących wykluczeń:

- Pliki systemu operacyjnego
- Role serwera i wszystkie pliki dodawane za pośrednictwem ról serwera

Ponieważ Program antywirusowy Microsoft Defender jest wbudowana, nie wymaga wykluczeń dla plików systemu operacyjnego na Windows Server 2016 lub nowszych. Ponadto po uruchomieniu Windows Server 2016 lub nowszym i zainstalowaniu roli Program antywirusowy Microsoft Defender obejmuje automatyczne wykluczenia roli serwera i wszystkich plików dodanych podczas instalowania roli.

Wykluczenia systemu operacyjnego i wykluczenia roli serwera nie są wyświetlane na standardowych listach wykluczeń, które są wyświetlane w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

> [!NOTE]
> Automatyczne wykluczenia dla ról serwera i plików systemu operacyjnego nie mają zastosowania do Windows Server 2012. Automatyczne wykluczenia mogą mieć zastosowanie, jeśli serwery z systemem Windows Server 2012 R2 są dołączane do usługi Defender for Endpoint. (Zobacz [Dołączanie serwerów Windows do usługi Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md)).


### <a name="the-list-of-automatic-exclusions"></a>Lista automatycznych wykluczeń

Poniższe sekcje zawierają wykluczenia dostarczane ze ścieżkami plików i typami plików automatycznych wykluczeń.

#### <a name="default-exclusions-for-all-roles"></a>Domyślne wykluczenia dla wszystkich ról

Ta sekcja zawiera listę domyślnych wykluczeń dla wszystkich ról w Windows Server 2016, Windows Server 2019 i Windows Server 2022.

> [!NOTE]
> Lokalizacje domyślne mogą być inne niż wymienione w tym artykule.

##### <a name="windows-tempedb-files"></a>Windows plików "temp.edb"

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>pliki Windows Update lub pliki aktualizacji automatycznej

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>pliki Zabezpieczenia Windows

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>pliki zasady grupy

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

##### <a name="wins-files"></a>Pliki WINS

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

##### <a name="file-replication-service-frs-exclusions"></a>Wykluczenia usługi replikacji plików (FRS)

- Pliki w folderze roboczym usługi replikacji plików (FRS). Folder roboczy usługi FRS jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- Pliki dziennika bazy danych USŁUGI FRS. Folder pliku dziennika bazy danych usługi FRS jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- Folder przejściowy usługi FRS. Folder przejściowy jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- Preinstaluj folder FRS. Ten folder jest określony przez folder `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- Baza danych i foldery robocze replikacji rozproszonego systemu plików (DFSR). Te foldery są określane przez klucz rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > W przypadku lokalizacji niestandardowych zobacz [Rezygnacja z automatycznych wykluczeń](#opting-out-of-automatic-exclusions).

  - `%systemdrive%\System Volume Information\DFSR\$db_normal$`
  - `%systemdrive%\System Volume Information\DFSR\FileIDTable_*`
  - `%systemdrive%\System Volume Information\DFSR\SimilarityTable_*`
  - `%systemdrive%\System Volume Information\DFSR\*.XML`
  - `%systemdrive%\System Volume Information\DFSR\$db_dirty$`
  - `%systemdrive%\System Volume Information\DFSR\$db_clean$`
  - `%systemdrive%\System Volume Information\DFSR\$db_lostl$`
  - `%systemdrive%\System Volume Information\DFSR\Dfsr.db`
  - `%systemdrive%\System Volume Information\DFSR\*.frx`
  - `%systemdrive%\System Volume Information\DFSR\*.log`
  - `%systemdrive%\System Volume Information\DFSR\Fsr*.jrs`
  - `%systemdrive%\System Volume Information\DFSR\Tmp.edb`

##### <a name="process-exclusions"></a>Wykluczenia procesów

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Wykluczenia funkcji Hyper-V

Poniższa tabela zawiera listę wykluczeń typów plików, wykluczeń folderów i wykluczeń procesów, które są dostarczane automatycznie podczas instalowania roli funkcji Hyper-V.

<br><br/>

|Typ wykluczenia|Specyfiki|
|---|---|
|Typy plików|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|Foldery|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|Procesów|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

##### <a name="sysvol-files"></a>Pliki SYSVOL

- `%systemroot%\Sysvol\Domain\*.adm`
- `%systemroot%\Sysvol\Domain\*.admx`
- `%systemroot%\Sysvol\Domain\*.adml`
- `%systemroot%\Sysvol\Domain\Registry.pol`
- `%systemroot%\Sysvol\Domain\*.aas`
- `%systemroot%\Sysvol\Domain\*.inf`
- `%systemroot%\Sysvol\Domain\*Scripts.ini`
- `%systemroot%\Sysvol\Domain\*.ins`
- `%systemroot%\Sysvol\Domain\Oscfilter.ini`


#### <a name="active-directory-exclusions"></a>Wykluczenia usługi Active Directory

Ta sekcja zawiera listę wykluczeń, które są dostarczane automatycznie podczas instalowania Active Directory Domain Services (AD DS).

##### <a name="ntds-database-files"></a>Pliki bazy danych NTDS

Pliki bazy danych są określone w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>Pliki dziennika transakcji usług AD DS

Pliki dziennika transakcji są określone w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

##### <a name="the-ntds-working-folder"></a>Folder roboczy NTDS

Ten folder jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Wykluczenia procesów dla plików pomocy technicznej związanych z usługami AD DS i AD DS

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>Wykluczenia serwera DHCP

Ta sekcja zawiera listę wykluczeń, które są dostarczane automatycznie podczas instalowania roli serwera DHCP. Lokalizacje plików serwera DHCP są określane przez parametry *DatabasePath*, *DhcpLogFilePath* i *BackupDatabasePath* w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>Wykluczenia serwera DNS

Ta sekcja zawiera listę wykluczeń plików i folderów oraz wykluczeń procesu, które są dostarczane automatycznie podczas instalowania roli serwera DNS.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Wykluczenia plików i folderów dla roli serwera DNS

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>Wykluczenia procesów dla roli serwera DNS

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Wykluczenia usług plików i Storage

Ta sekcja zawiera listę wykluczeń plików i folderów, które są dostarczane automatycznie podczas instalowania roli Plik i usługi Storage. Wykluczenia wymienione poniżej nie obejmują wykluczeń dla roli Klastrowanie.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Wykluczenia serwera wydruku

Ta sekcja zawiera listę wykluczeń typów plików, wykluczeń folderów i wykluczeń procesu, które są dostarczane automatycznie podczas instalowania roli serwera wydruku.

##### <a name="file-type-exclusions"></a>Wykluczenia typu pliku

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Wykluczenia folderów

Ten folder jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>Wykluczenia procesów

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Wykluczenia serwera sieci Web

Ta sekcja zawiera listę wykluczeń folderów i wykluczeń procesu, które są dostarczane automatycznie podczas instalowania roli serwera sieci Web.

##### <a name="folder-exclusions"></a>Wykluczenia folderów

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>Wykluczenia procesów

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>Wyłączanie skanowania plików w folderze Sysvol\Sysvol lub folderze SYSVOL_DFSR\Sysvol

Bieżąca lokalizacja folderu `Sysvol\Sysvol` lub `SYSVOL_DFSR\Sysvol` i wszystkich podfolderów jest miejscem docelowym ponownej analizy systemu plików w katalogu głównym zestawu replik. Foldery `Sysvol\Sysvol` i `SYSVOL_DFSR\Sysvol` domyślnie używają następujących lokalizacji:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Ścieżka do aktualnie aktywnego `SYSVOL` obiektu jest przywoływane przez udział NETLOGON i może być określana przez nazwę wartości SysVol w następującym podkluczu: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

Wyklucz następujące pliki z tego folderu i wszystkich jego podfolderów:

- `*.adm`
- `*.admx`
- `*.adml`
- `Registry.pol`
- `Registry.tmp`
- `*.aas`
- `*.inf`
- `Scripts.ini`
- `*.ins`
- `Oscfilter.ini`

#### <a name="windows-server-update-services-exclusions"></a>wykluczenia Windows Server Update Services

Ta sekcja zawiera listę wykluczeń folderów, które są dostarczane automatycznie podczas instalowania roli Windows Server Update Services (WSUS). Folder WSUS jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Rezygnacja z automatycznych wykluczeń

W Windows Server 2016 i nowszych wstępnie zdefiniowane wykluczenia dostarczane przez aktualizacje analizy zabezpieczeń wykluczają tylko domyślne ścieżki dla roli lub funkcji. Jeśli zainstalowano rolę lub funkcję w ścieżce niestandardowej lub chcesz ręcznie kontrolować zestaw wykluczeń, pamiętaj, aby zrezygnować z automatycznych wykluczeń dostarczanych w aktualizacjach analizy zabezpieczeń. Należy jednak pamiętać, że wykluczenia dostarczane automatycznie są zoptymalizowane pod kątem Windows Server 2016 i nowszych. Zobacz [Rekomendacje, aby zdefiniować wykluczenia](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) przed zdefiniowaniem list wykluczeń.

> [!WARNING]
> Rezygnacja z automatycznych wykluczeń może niekorzystnie wpłynąć na wydajność lub spowodować uszkodzenie danych. Wykluczenia dostarczane automatycznie są zoptymalizowane pod kątem ról Windows Server 2016, Windows Server 2019 i Windows Server 2022.

Ponieważ wstępnie zdefiniowane wykluczenia wykluczają tylko **ścieżki domyślne**, w przypadku przeniesienia folderów NTDS i SYSVOL na inny dysk lub ścieżkę *inną niż oryginalna ścieżka* należy dodać wykluczenia ręcznie. Zobacz [Konfigurowanie listy wykluczeń na podstawie nazwy folderu lub rozszerzenia pliku](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

Listy wykluczeń automatycznych można wyłączyć za pomocą zasady grupy, poleceń cmdlet programu PowerShell i usługi WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Użyj zasady grupy, aby wyłączyć listę wykluczeń automatycznych na Windows Server 2016, Windows Server 2019 i Windows Server 2022

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**, a następnie wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **Wykluczenia**.

4. Kliknij dwukrotnie **pozycję Wyłącz automatyczne wykluczenia** i ustaw opcję **Włączone**. Następnie wybierz przycisk **OK**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Użyj poleceń cmdlet programu PowerShell, aby wyłączyć listę automatycznych wykluczeń na serwerze Windows

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Użyj poleceń cmdlet programu PowerShell, aby skonfigurować i uruchomić Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [Użyj programu PowerShell z Program antywirusowy Microsoft Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Użyj instrukcji zarządzania Windows (WMI), aby wyłączyć listę wykluczeń automatycznych na serwerze Windows

Użyj metody **Set** klasy [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) dla następujących właściwości:

```WMI
DisableAutoExclusions
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujące informacje:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Definiowanie wykluczeń niestandardowych

W razie potrzeby można dodawać lub usuwać wykluczenia niestandardowe. Aby to zrobić, zobacz następujące artykuły:

- [Konfigurowanie i weryfikowanie wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie i weryfikowanie wykluczeń dla skanowania Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Dostosowywanie, inicjowanie i przeglądanie wyników skanowania i korygowania Program antywirusowy Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
