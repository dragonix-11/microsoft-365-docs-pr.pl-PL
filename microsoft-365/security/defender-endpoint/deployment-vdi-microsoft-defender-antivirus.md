---
title: przewodnik wdrażania infrastruktury pulpitu wirtualnego Program antywirusowy Microsoft Defender
description: Dowiedz się, jak wdrożyć Program antywirusowy Microsoft Defender w środowisku pulpitu wirtualnego, aby uzyskać najlepszą równowagę między ochroną a wydajnością.
keywords: vdi, hyper-v, vm, virtual machine, windows defender, antivirus, av, virtual desktop, rds, remote desktop
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: f788c72c9b437dba7528c59adedb3ced21539ada
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129124"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Przewodnik wdrożenia programu antywirusowego Microsoft Defender w środowisku infrastruktury pulpitu wirtualnego

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Oprócz standardowych konfiguracji lokalnych lub sprzętowych można używać Program antywirusowy Microsoft Defender w środowisku pulpitu zdalnego (RDS) lub nietrwałej infrastruktury pulpitu wirtualnego (VDI). Dzięki możliwości łatwego wdrażania aktualizacji maszyn wirtualnych działających w interfejsach VDI można szybko i łatwo uzyskiwać aktualizacje na maszynach. Nie trzeba już okresowo tworzyć i uszczelniać złotych obrazów, ponieważ aktualizacje są rozszerzane na ich bity składników na serwerze hosta, a następnie pobierane bezpośrednio na maszynę wirtualną po jej włączeniu.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w witrynie `demo.wd.microsoft.com` jest przestarzała i zostanie usunięta w przyszłości.

W tym przewodniku opisano sposób konfigurowania maszyn wirtualnych pod kątem optymalnej ochrony i wydajności, w tym:

- [Konfigurowanie dedykowanego udziału plików VDI na potrzeby aktualizacji analizy zabezpieczeń](#set-up-a-dedicated-vdi-file-share)
- [Losowe zaplanowanych skanów](#randomize-scheduled-scans)
- [Używanie szybkich skanów](#use-quick-scans)
- [Zapobieganie powiadomieniom](#prevent-notifications)
- [Wyłączanie skanowania po każdej aktualizacji](#disable-scans-after-an-update)
- [Skanuj nieaktualne maszyny lub maszyny, które od jakiegoś czasu są w trybie offline](#scan-vms-that-have-been-offline)
- [Stosowanie wykluczeń](#exclusions)

Możesz również pobrać oficjalny [dokument Program antywirusowy Microsoft Defender na temat infrastruktury pulpitu wirtualnego](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf), który analizuje nową funkcję aktualizacji analizy zabezpieczeń, a także testy wydajności i wskazówki dotyczące sposobu testowania wydajności oprogramowania antywirusowego na własnej infrastrukturze VDI.

Aby uzyskać więcej informacji na temat obsługi usług Pulpit zdalny Microsoft Services i VDI, zobacz [Dokumentacja usługi Azure Virtual Desktop](/azure/virtual-desktop).

W przypadku maszyn wirtualnych opartych na platformie Azure zobacz [Instalowanie Endpoint Protection w Microsoft Defender dla Chmury](/azure/defender-for-cloud/endpoint-protection-recommendations-technical).

> [!IMPORTANT]
> Mimo że interfejs VDI może być hostowany na Windows Server 2012 lub Windows Server 2016, maszyny wirtualne powinny działać Windows 10, co najmniej 1607, ze względu na zwiększone technologie ochrony i funkcje, które są niedostępne we wcześniejszych wersjach Windows.
> Istnieją ulepszenia wydajności i funkcji w sposobie, w jaki usługa Microsoft Defender AV działa na maszynach wirtualnych w Windows 10 Insider Preview, kompilacja 18323 (i nowsze). W tym przewodniku zidentyfikujemy, czy musisz używać kompilacji insider preview; Jeśli nie zostanie określony, minimalna wymagana wersja dla najlepszej ochrony i wydajności jest Windows 10 1607.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Konfigurowanie dedykowanego udziału plików VDI

W Windows 10, wersja 1903, wprowadziliśmy udostępnioną funkcję analizy zabezpieczeń, która odciąża rozpakowywanie pobranych aktualizacji analizy zabezpieczeń na maszynie hosta, oszczędzając w ten sposób poprzednie zasoby procesora CPU, dysku i pamięci na poszczególnych maszynach. Ta funkcja jest obsługiwana wstecznie i działa teraz w Windows 10 wersji 1703 lub nowszej. Tę funkcję można ustawić za pomocą zasady grupy lub programu PowerShell.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Użyj zasady grupy, aby włączyć funkcję współużytkowanej analizy zabezpieczeń:

1. Na komputerze zarządzania zasady grupy otwórz konsolę zarządzania zasady grupy, kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij dwukrotnie **pozycję Zdefiniuj lokalizację analizy zabezpieczeń dla klientów VDI**, a następnie ustaw opcję **Włączone**. Automatycznie zostanie wyświetlone pole.

6. Wprowadź `\\<sharedlocation\>\wdav-update` (aby uzyskać pomoc dotyczącą tej wartości, zobacz [Pobieranie i rozpakowywanie](#download-and-unpackage-the-latest-updates)).

7. Kliknij przycisk **OK**.

8. Wdróż obiekt zasad grupy na maszynach wirtualnych, które chcesz przetestować.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Używanie programu PowerShell do włączania funkcji analizy zabezpieczeń udostępnionych

Użyj następującego polecenia cmdlet, aby włączyć tę funkcję. Następnie należy wypchnąć tę opcję, ponieważ zwykle wypychasz zasady konfiguracji oparte na programie PowerShell na maszyny wirtualne:

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

Zobacz sekcję [Pobieranie i rozpakowywanie](#download-and-unpackage-the-latest-updates) , aby zapoznać się z tym, \<shared location\> co będzie.

## <a name="download-and-unpackage-the-latest-updates"></a>Pobieranie i rozpakowywanie najnowszych aktualizacji

Teraz możesz rozpocząć pobieranie i instalowanie nowych aktualizacji. Poniżej utworzono przykładowy skrypt programu PowerShell. Ten skrypt jest najprostszym sposobem pobierania nowych aktualizacji i przygotowania ich do użycia maszyn wirtualnych. Następnie należy ustawić skrypt do uruchomienia w określonym czasie na maszynie zarządzania przy użyciu zaplanowanego zadania (lub, jeśli znasz używanie skryptów programu PowerShell na platformie Azure, Intune lub SCCM, możesz również użyć tych skryptów).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd /d $vdmpath & mpam-fe.exe /x"
```

Zaplanowane zadanie można ustawić tak, aby było uruchamiane raz dziennie, tak aby po każdym pobraniu i rozpakowaniu pakietu maszyny wirtualne otrzymają nową aktualizację.
Zalecamy rozpoczęcie od raz dziennie, ale należy eksperymentować z zwiększaniem lub zmniejszaniem częstotliwości, aby zrozumieć wpływ.

Pakiety analizy zabezpieczeń są zwykle publikowane raz na trzy do czterech godzin. Nie zaleca się ustawiania częstotliwości krótszej niż cztery godziny, ponieważ bez korzyści zwiększy to obciążenie sieci na komputerze zarządzania.

Możesz również skonfigurować pojedynczy serwer lub maszynę, aby pobierać aktualizacje w imieniu maszyn wirtualnych w odstępach czasu i umieszczać je w udziale plików do użycia.
Jest to możliwe, gdy urządzenia mają uprawnienia do udziału i ntfs dostępu do odczytu do udziału, aby mogły pobrać aktualizacje. W tym celu:

 1. Utwórz udział plików SMB/CIFS. 
 
 2. Użyj poniższego przykładu, aby utworzyć udział plików z następującymi uprawnieniami udziału.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > Dodano uprawnienie NTFS dla **użytkowników uwierzytelnionych:Odczyt:**. 

    W tym przykładzie udział plików to:

    `\\fileserver.fqdn\mdatp$\wdav-update`

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>Ustawianie zaplanowanego zadania w celu uruchomienia skryptu programu PowerShell

1. Na maszynie zarządzania otwórz menu Start i wpisz **Harmonogram zadań**. Otwórz go i wybierz pozycję **Utwórz zadanie...** na panelu bocznym.

2. Wprowadź nazwę **unpacker analizy zabezpieczeń**. Przejdź do karty **Wyzwalacz** . Wybierz pozycję **Nowy...** \> **Codziennie** i wybierz przycisk **OK**.

3. Przejdź do karty **Akcje** . Wybierz pozycję **Nowy...** Wprowadź program **PowerShell** w polu **Program/Skrypt** . Wprowadź `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` wartość w polu **Dodaj argumenty** . Wybierz przycisk **OK**.

4. Jeśli chcesz, możesz skonfigurować dodatkowe ustawienia.

5. Wybierz przycisk **OK** , aby zapisać zaplanowane zadanie.

Aktualizację można zainicjować ręcznie, klikając prawym przyciskiem myszy zadanie i klikając pozycję **Uruchom**.

### <a name="download-and-unpackage-manually"></a>Ręczne pobieranie i rozpakowywanie

Jeśli wolisz zrobić wszystko ręcznie, oto, co należy zrobić, aby replikować zachowanie skryptu:

1. Utwórz nowy folder w katalogu głównym systemu o nazwie `wdav_update` do przechowywania aktualizacji analizy, na przykład utwórz folder `c:\wdav_update`.

2. Utwórz podfolder w *obszarze wdav_update* o nazwie GUID, na przykład `{00000000-0000-0000-0000-000000000000}`

   Oto przykład: `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > W skryptze ustawiliśmy go tak, aby ostatnie 12 cyfr identyfikatora GUID było rokiem, miesiącem, dniem i godziną pobrania pliku, tak aby za każdym razem był tworzony nowy folder. Można to zmienić, aby plik był pobierany do tego samego folderu za każdym razem.

3. Pobierz pakiet analizy zabezpieczeń z pliku [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  do folderu GUID. Plik powinien mieć nazwę `mpam-fe.exe`.

4. Otwórz okno wiersza polecenia cmd i przejdź do utworzonego folderu GUID. Użyj polecenia **wyodrębniania /X** , aby wyodrębnić pliki, na przykład `mpam-fe.exe /X`.

   > [!NOTE]
   > Maszyny wirtualne będą pobierać zaktualizowany pakiet za każdym razem, gdy zostanie utworzony nowy folder GUID z wyodrębnionym pakietem aktualizacji lub gdy istniejący folder zostanie zaktualizowany przy użyciu nowego wyodrębnionego pakietu.

## <a name="randomize-scheduled-scans"></a>Losowe zaplanowanych skanów

Zaplanowane skanowania są uruchamiane oprócz [ochrony i skanowania w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md).

Czas rozpoczęcia skanowania jest nadal oparty na zasadach zaplanowanego skanowania (**ScheduleDay**, **ScheduleTime** i **ScheduleQuickScanTime**). Randomizacja spowoduje, że Program antywirusowy Microsoft Defender rozpocznie skanowanie na każdej maszynie w ciągu czterech godzin od czasu ustawionego na zaplanowane skanowanie.

Zobacz [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) , aby uzyskać inne opcje konfiguracji dostępne dla zaplanowanych skanów.

## <a name="use-quick-scans"></a>Używanie szybkich skanów

Możesz określić typ skanowania, który ma zostać wykonany podczas zaplanowanego skanowania. Szybkie skanowanie to preferowane podejście, ponieważ są przeznaczone do wyszukiwania we wszystkich miejscach, w których złośliwe oprogramowanie musi znajdować się, aby być aktywnym. W poniższej procedurze opisano sposób konfigurowania szybkich skanów przy użyciu zasady grupy.

1. W edytorze zasady grupy przejdź do pozycji **Szablony** \> administracyjne **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **Skanuj**.

2. Wybierz **pozycję Określ typ skanowania do użycia podczas zaplanowanego skanowania** , a następnie zmodyfikuj ustawienie zasad.

3. Ustaw zasady na **Włączone**, a następnie w obszarze **Opcje** wybierz pozycję  **Szybkie skanowanie**.

4. Wybierz przycisk **OK**.

5. Wdróż obiekt zasady grupy tak jak zwykle.

## <a name="prevent-notifications"></a>Zapobieganie powiadomieniom

Czasami Program antywirusowy Microsoft Defender powiadomienia mogą być wysyłane do wielu sesji lub utrwalane w wielu sesjach. Aby zminimalizować ten problem, można zablokować Program antywirusowy Microsoft Defender interfejs użytkownika. W poniższej procedurze opisano sposób pomijania powiadomień przy użyciu zasady grupy.

1. W edytorze zasady grupy przejdź do **Windows składników** \> **Program antywirusowy Microsoft Defender** \> **interfejsu klienta**.

2. Wybierz pozycję **Pomiń wszystkie powiadomienia** , a następnie edytuj ustawienia zasad.

3. Ustaw zasady na **Włączone**, a następnie wybierz przycisk **OK**.

4. Wdróż obiekt zasady grupy tak jak zwykle.

Pomijanie powiadomień uniemożliwia wyświetlanie powiadomień z Program antywirusowy Microsoft Defender w Centrum akcji w Windows 10 po zakończeniu skanowania lub wykonaniu akcji korygowania. Jednak twój zespół ds. operacji zabezpieczeń zobaczy wyniki skanowania, gdy atak został wykryty i zatrzymany; alerty, takie jak "alert dostępu początkowego", są wyzwalane i wyświetlane w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Aby otworzyć Centrum akcji w Windows 10 lub Windows 11, wykonaj jedną z następujących czynności:
> - Na prawym końcu paska zadań wybierz ikonę Centrum akcji.
> - Naciśnij przycisk Windows logo + A.
> - Na urządzeniu z ekranem dotykowym szybko przesuń palcem od prawej krawędzi ekranu.

## <a name="disable-scans-after-an-update"></a>Wyłączanie skanowania po aktualizacji

Wyłączenie skanowania po aktualizacji uniemożliwi skanowanie po otrzymaniu aktualizacji. To ustawienie można zastosować podczas tworzenia obrazu podstawowego, jeśli uruchomiono również szybkie skanowanie. W ten sposób można uniemożliwić nowo zaktualizowanej maszynie wirtualnej ponowne przeprowadzenie skanowania (ponieważ został on już przeskanowany podczas tworzenia obrazu podstawowego).

> [!IMPORTANT]
> Uruchamianie skanowania po aktualizacji pomoże zapewnić ochronę maszyn wirtualnych przy użyciu najnowszych aktualizacji analizy zabezpieczeń. Wyłączenie tej opcji spowoduje zmniejszenie poziomu ochrony maszyn wirtualnych i powinno być używane tylko podczas pierwszego tworzenia lub wdrażania obrazu podstawowego.

1. W edytorze zasady grupy przejdź do **obszaru składniki Windows** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje analizy zabezpieczeń**.

2. Wybierz pozycję **Włącz skanowanie po aktualizacji analizy zabezpieczeń** , a następnie edytuj ustawienie zasad.

3. Ustaw zasady na **Wyłączone**.

4. Wybierz przycisk **OK**.

5. Wdróż obiekt zasady grupy tak jak zwykle.

Te zasady uniemożliwiają uruchamianie skanowania natychmiast po aktualizacji.

## <a name="disable-the-scanonlyifidle-option"></a>Wyłącz opcję `ScanOnlyIfIdle`

Użyj następującego polecenia cmdlet, aby zatrzymać szybkie lub zaplanowane skanowanie za każdym razem, gdy urządzenie będzie bezczynne, jeśli jest w trybie pasywnym.

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled $false
```

Można również wyłączyć opcję `ScanOnlyIfIdle` w Program antywirusowy Microsoft Defender przez konfigurację za pośrednictwem zasad grupy lokalnej lub domeny. Zapobiega to znacznej rywalizacji o procesor CPU w środowiskach o wysokiej gęstości.

Aby uzyskać więcej informacji, zobacz [Uruchamianie zaplanowanego skanowania tylko wtedy, gdy komputer jest włączony, ale nie jest używany](https://admx.help/?Category=SystemCenterEndpointProtection&Policy=Microsoft.Policies.Antimalware::scan_scanonlyifidle).

## <a name="scan-vms-that-have-been-offline"></a>Skanowanie maszyn wirtualnych, które były w trybie offline

1. W edytorze zasady grupy przejdź do **obszaru** \> składniki Windows **Program antywirusowy Microsoft Defender** \> **Scan**.

2. Wybierz pozycję **Włącz szybkie skanowanie w trybie catch-up** , a następnie edytuj ustawienie zasad.

3. Ustaw zasady na **Włączone**.

4. Wybierz przycisk **OK**.

5. Wdróż obiekt zasady grupy tak jak zwykle.

Te zasady wymuszają skanowanie, jeśli maszyna wirtualna nie ma co najmniej dwóch kolejnych zaplanowanych skanów.

## <a name="enable-headless-ui-mode"></a>Włączanie trybu bezgłowego interfejsu użytkownika

1. W edytorze zasady grupy przejdź do **Windows składników** \> **Program antywirusowy Microsoft Defender** \> **interfejsu klienta**.

2. Wybierz pozycję **Włącz tryb interfejsu użytkownika bez użycia głowy** i edytuj zasady.

3. Ustaw zasady na **Włączone**.

4. Kliknij przycisk **OK**.

5. Wdróż obiekt zasady grupy tak jak zwykle.

Te zasady ukrywają cały interfejs użytkownika Program antywirusowy Microsoft Defender przed użytkownikami końcowymi w organizacji.

## <a name="exclusions"></a>Wykluczenia

Wykluczenia można dodawać, usuwać lub dostosowywać zgodnie z potrzebami.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie wykluczeń Program antywirusowy Microsoft Defender na serwerze Windows.](configure-exclusions-microsoft-defender-antivirus.md)

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="additional-resources"></a>Dodatkowe materiały

- [Blog tech Community: konfigurowanie Program antywirusowy Microsoft Defender dla nietrwałych maszyn VDI](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [Fora TechNet dotyczące usług pulpitu zdalnego i interfejsu VDI](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [SignatureDownloadCustomTask — skrypt programu PowerShell](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
