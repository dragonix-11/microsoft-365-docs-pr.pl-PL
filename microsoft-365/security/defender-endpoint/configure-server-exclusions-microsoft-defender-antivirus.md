---
title: Konfigurowanie Program antywirusowy Microsoft Defender wykluczeń na Windows Server
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server uwzględnia automatyczne wykluczenia w zależności od roli serwera. Możesz również dodać wykluczenia niestandardowe.
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
ms.openlocfilehash: 442172afc9caf5dbd2af8c91cda531494fabd05d
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63015975"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Konfigurowanie Program antywirusowy Microsoft Defender wykluczeń na Windows Server


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender na Windows Server 2016 i Windows Server 2019 automatycznie zarejestruje Cię w określonych wykluczeniach, zdefiniowanych przez określoną rolę serwera. Te wykluczenia nie są wyświetlane na standardowych listach wykluczeń wyświetlanych w [Zabezpieczenia Windows aplikacji](microsoft-defender-security-center-antivirus.md).

Oprócz automatycznych wykluczeń zdefiniowanych przez rolę serwera można dodawać i usuwać wykluczenia niestandardowe. Aby to zrobić, zapoznaj się z tymi artykułami:
- [Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Kilka punktów do ominiania

Należy pamiętać o następujących ważnych kwestiach:

- Wykluczenia niestandardowe mają pierwszeństwo przed wykluczeniami automatycznymi.
- Wykluczenia automatyczne mają zastosowanie tylko w przypadku skanowania w czasie rzeczywistym. Wykluczenia automatyczne nie są szanuje podczas pełnego, szybkiego skanowania na żądanie.
- Wykluczenia niestandardowe i zduplikowane nie są powodujące konfliktu z automatycznymi wykluczeniami.
- Program antywirusowy Microsoft Defender informacji o rolach zainstalowanych na komputerze za pomocą narzędzi do obsługi i zarządzania obrazami wdrażania (DISM, Deployment Image Servicing and Management).
- Windows Server 2012 R2 nie ma Program antywirusowy Microsoft Defender jako funkcji instalowania. Po dojechiniu tych serwerów do usługi Defender for Endpoint zainstalujesz program Program antywirusowy Windows Defender i zostaną zastosowane domyślne wykluczenia dla plików systemu operacyjnego. Wyjątki dotyczące ról serwera (wskazane poniżej) nie są jednak stosowane automatycznie i należy odpowiednio skonfigurować te wykluczenia. Aby dowiedzieć się więcej, zobacz [Windows serwerach końcowych programu Microsoft Defender](configure-server-endpoints.md).

Ten artykuł zawiera omówienie wykluczeń w przypadku Program antywirusowy Microsoft Defender w Windows Server 2016 lub nowszym.

Ponieważ Program antywirusowy Microsoft Defender jest wbudowana w Windows Server 2016 i nowszych, wykluczenia dotyczące plików systemu operacyjnego i ról serwera są tworzone automatycznie. Można jednak zdefiniować wykluczenia niestandardowe. W razie potrzeby możesz również zrezygnować z automatycznego wyłączenia.

Ten artykuł zawiera następujące sekcje:

<br/><br/>

|Sekcja|Opis|
|---|---|
|[Automatyczne wykluczenia w Windows Server 2016 lub nowszym](#automatic-exclusions-on-windows-server-2016-or-later)|Opisuje dwa główne typy wykluczeń automatycznych i zawiera szczegółową listę wyłączeń automatycznych.|
|[Rezygnacja z automatycznego wyłączenia](#opting-out-of-automatic-exclusions)|Zawiera ważne zagadnienia i procedury opisujące sposób rezygnacji z automatycznych wykluczeń|
|[Definiowanie wykluczeń niestandardowych](#defining-custom-exclusions)|Linki do informacji, które można znaleźć w celu zdefiniowania niestandardowych wykluczeń|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Automatyczne wykluczenia w Windows Server 2016 lub nowszym

Na Windows Server 2016 lub nowszej nie należy definiować następujących wykluczeń:

- Pliki systemu operacyjnego
- Role serwera i wszystkie pliki dodawane za pośrednictwem ról serwera

Ponieważ Program antywirusowy Microsoft Defender jest wbudowana, nie wymaga ona wykluczeń dla plików systemu operacyjnego Windows Server 2016 i nowszych. Ponadto po uruchomieniu roli Windows Server 2016 lub nowszej, funkcja Program antywirusowy Microsoft Defender uwzględnia automatyczne wykluczenia roli serwera i wszystkich plików dodawanych podczas instalowania roli.

Wykluczenia systemów operacyjnych i wykluczenia ról serwera nie są wyświetlane na standardowych listach wykluczeń wyświetlanych w Zabezpieczenia Windows [aplikacji](microsoft-defender-security-center-antivirus.md).

> [!NOTE]
> Automatyczne wykluczenia dotyczące ról serwera i plików systemu operacyjnego nie mają zastosowania do Windows Server 2012. Automatyczne wykluczenia mogą obowiązywać, jeśli serwery z uruchomionym Windows Server 2012 R2 są wnoszone do usługi Defender for Endpoint. (Zobacz[: "Windows serwerach sieci Web do usługi Programu Microsoft Defender dla punktu końcowego](configure-server-endpoints.md).)


### <a name="the-list-of-automatic-exclusions"></a>Lista wyłączeń automatycznych

W poniższych sekcjach znajdują się wykluczenia, dla których są dostarczane ścieżki plików i typy plików z automatycznymi wykluczeniami.

#### <a name="default-exclusions-for-all-roles"></a>Domyślne wykluczenia dla wszystkich ról

W tej sekcji wymieniono domyślne wykluczenia dla wszystkich ról w programach Windows Server 2016, Windows Server 2019 i Windows Server 2022.

> [!NOTE]
> Lokalizacje domyślne mogą być inne niż wymienione w tym artykule.

##### <a name="windows-tempedb-files"></a>Windows "temp.edb"

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>Windows plików lub plików aktualizacji automatycznych

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>Zabezpieczenia Windows plików

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>zasady grupy plików

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

##### <a name="wins-files"></a>Pliki usługi WINS

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

##### <a name="file-replication-service-frs-exclusions"></a>Wykluczenia usługi replikacji plików (FRS)

- Pliki w folderze pracy Usługi replikacji plików (FRS, File Replication Service). Folder roboczy FRS jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- Pliki dziennika bazy danych FRS. Folder pliku dziennika bazy danych FRS jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- Folder tymczasowego frs. Folder tymczasowego jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- Folder preinstalacji FRS. Ten folder jest określony przez folder `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- Baza danych i foldery robocze replikacji systemu plików (DFSR, Distributed File System Replication). Te foldery są określone przez klucz rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > Aby uzyskać informacje o lokalizacjach niestandardowych, [zobacz Rezygnacja z automatycznych wykluczeń](#opting-out-of-automatic-exclusions).

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

##### <a name="process-exclusions"></a>Wykluczenia procesu

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Wykluczenia funkcji Hyper-V

W poniższej tabeli wymieniono wykluczenia typów plików, wykluczenia folderów i wykluczenia procesów, które są dostarczane automatycznie podczas instalowania roli hyper-V.

<br><br/>

|Typ wykluczenia|Szczegółowe informacje|
|---|---|
|Typy plików|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|Foldery|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|Procesy|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

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


#### <a name="active-directory-exclusions"></a>Wykluczenia z usługi Active Directory

W tej sekcji wymieniono wykluczenia, które są dostarczane automatycznie podczas instalowania Usługi domenowe w usłudze Active Directory (AD DS).

##### <a name="ntds-database-files"></a>Pliki baz danych NTDS

Pliki bazy danych są określone w kluczu rejestru `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>Pliki AD DS dziennika transakcji

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

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Wykluczenia procesów dla AD DS i AD DS pomocy technicznej związanych z obsługą klienta

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>WYKLUCZENIA SERWERÓW

W tej sekcji wymieniono wykluczenia dostarczane automatycznie podczas instalowania roli serwera PROXY. Lokalizacje plików serwera FTP są określone przez parametry *DatabasePath*, *LogFilePath* i *BackupDatabasePath* w kluczu rejestru. `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>Wykluczenia serwera DNS

Ta sekcja zawiera listę wykluczeń plików i folderów oraz wykluczeń procesów, które są dostarczane automatycznie po zainstalowaniu roli serwera DNS.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Wykluczenia plików i folderów dla roli serwera DNS

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>Wykluczenia procesu dla roli serwera DNS

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Wykluczenia usług Storage i plików

Ta sekcja zawiera listę wykluczeń plików i folderów, które są dostarczane automatycznie podczas instalowania roli Plik Storage Usługi. Wykluczenia wymienione poniżej nie obejmują wykluczeń roli klastrowania.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Wykluczenia z serwera wydruku

Ta sekcja zawiera listę wykluczeń typów plików, wykluczeń folderów i wykluczeń procesów, które są dostarczane automatycznie podczas instalowania roli serwera wydruku.

##### <a name="file-type-exclusions"></a>Wykluczenia typów plików

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Wykluczenia folderów

Ten folder jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>Wykluczenia procesu

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Wykluczenia serwerów sieci Web

Ta sekcja zawiera listę wykluczeń folderów i wykluczeń procesów, które są dostarczane automatycznie podczas instalowania roli serwera sieci Web.

##### <a name="folder-exclusions"></a>Wykluczenia folderów

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>Wykluczenia procesu

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>Wyłączanie skanowania plików w folderze Sysvol\Sysvol lub folderze SYSVOL_DFSR\Sysvol

Bieżąca lokalizacja folderu `Sysvol\Sysvol` lub `SYSVOL_DFSR\Sysvol` i wszystkich podfolderów to element docelowy ponownego rozparowania systemu plików katalogu głównego repliki zestawu. Foldery `Sysvol\Sysvol` `SYSVOL_DFSR\Sysvol` i korzystają domyślnie z następujących lokalizacji:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Do ścieżki aktualnie aktywnej `SYSVOL` odwołuje się udział NETLOGON i może zostać określona przez nazwę wartości sysVol w następującym podkluczu: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

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

#### <a name="windows-server-update-services-exclusions"></a>Windows Server Update Services wykluczenia

W tej sekcji wymieniono wykluczenia folderów, które są dostarczane automatycznie podczas instalowania roli programu Windows Server Update Services (WSUS). Folder WSUS jest określony w kluczu rejestru `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Rezygnacja z automatycznego wyłączenia

W Windows Server 2016 lub nowszych wstępnie zdefiniowane wykluczenia dostarczane przez aktualizacje analizy zabezpieczeń wykluczają tylko ścieżki domyślne dla roli lub funkcji. Jeśli zainstalowano rolę lub funkcję w ścieżce niestandardowej lub chcesz ręcznie sterować zestawem wykluczeń, wyłącz automatyczne wykluczenia dostarczane w aktualizacjach analizy zabezpieczeń. Należy jednak pamiętać, że dostarczane wykluczenia są automatycznie zoptymalizowane pod kątem Windows Server 2016 i nowszych. Zobacz [Rekomendacje o definiowaniu wykluczeń](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) przed zdefiniowaniem list wykluczeń.

> [!WARNING]
> Rezygnacja z automatycznego wyłączenia może negatywnie wpłynąć na wydajność lub powodować uszkodzenie danych. Dostarczone automatycznie wykluczenia są zoptymalizowane pod kątem ról Windows Server 2016, Windows Server 2019 i Windows Server 2022.

Ponieważ wstępnie zdefiniowane wykluczenia wykluczają tylko ścieżki **domyślne, przeniesienie** folderów NTDS i SYSVOL na inny dysk lub ścieżkę inną niż ścieżka pierwotna *, oznacza*, że należy ręcznie dodać wykluczenia. Zobacz [Konfigurowanie listy wykluczeń na podstawie nazwy folderu lub rozszerzenia pliku](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

Listy wykluczeń automatycznych można wyłączyć za zasady grupy cmdlet, poleceń cmdlet programu PowerShell i usługi WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Za zasady grupy wyłącz listę autowykluczeń w programach Windows Server 2016, Windows Server 2019 i Windows Server 2022

1. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera**, a następnie wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **wykluczeń**.

4. Kliknij dwukrotnie **pozycję Wyłącz automatyczne wykluczenia** i ustaw dla tej opcji wartość **Włączone**. Następnie wybierz przycisk **OK**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Wyłączanie listy autowykluczeń na serwerze programu PowerShell przy użyciu Windows Cmdlet programu PowerShell

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Za pomocą poleceń cmdlet programu PowerShell skonfiguruj i uruchom Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [Używanie programu PowerShell z Program antywirusowy Microsoft Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Aby Windows automatycznie wykluczeń na serwerze, użyj instrukcji zarządzania danymi (WMI, Windows Management Instruction)

Użyj metody **Set** klasy [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) , aby uzyskać następujące właściwości:

```WMI
DisableAutoExclusions
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz następujące informacje:

- [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Definiowanie wykluczeń niestandardowych

W razie potrzeby możesz dodać lub usunąć wykluczenia niestandardowe. W tym celu zapoznaj się z następującymi artykułami:

- [Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie i weryfikowanie wykluczeń Program antywirusowy Microsoft Defender skanowania](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Dostosowywanie, inicjowanie i przeglądanie wyników skanów Program antywirusowy Microsoft Defender środków zaradczych](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
