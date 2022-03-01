---
title: Program antywirusowy Microsoft Defender infrastruktury pulpitów wirtualnych
description: Dowiedz się, jak wdrożyć Program antywirusowy Microsoft Defender w środowisku pulpitu wirtualnego, aby uzyskać najlepszą równowagę między ochroną a wydajnością.
keywords: vdi, hyper-v, maszyny wirtualnej, windows defender, antivirus, av, pulpit wirtualny, rds, pulpit zdalny
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 02/11/2022
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 9ff523e55efa872002e53f74a631def4c65b9929
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014736"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Przewodnik po wdrażaniu Program antywirusowy Microsoft Defender w środowisku infrastruktury pulpitów wirtualnych (VDI, Virtual Desktop Infrastructure)

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Oprócz standardowych konfiguracji lokalnych lub sprzętowych można Program antywirusowy Microsoft Defender w środowisku pulpitu zdalnego (RDS) lub nietrwałych infrastruktury pulpitów wirtualnych (VDI, non-persistent virtual desktop infrastructure).

Aby uzyskać więcej informacji na Pulpit zdalny Microsoft usług wirtualnych i VDI, zobacz Dokumentacja pulpitu [wirtualnego platformy Azure](/azure/virtual-desktop).

W przypadku maszyn wirtualnych opartych na platformie Azure zobacz [Instalowanie Endpoint Protection w programie Microsoft Defender dla chmury](/azure/security-center/security-center-install-endpoint-protection).

Dzięki możliwości łatwego wdrażania aktualizacji dla maszyn wirtualnych uruchomionych w interfejsach VDI skróciliśmy ten przewodnik, aby skupić się na tym, jak można szybko i łatwo uzyskać aktualizacje na komputerach. Nie musisz już tworzyć i zaklejać złotych obrazów okresowo, ponieważ aktualizacje są rozszerzane na ich bity składników na serwerze hosta, a następnie pobierane bezpośrednio do maszyny wirtualnej po jej włączeniu.

W tym przewodniku opisano sposób konfigurowania maszyn wirtualnych w celu zapewnienia optymalnej ochrony i wydajności, w tym:

- [Konfigurowanie dedykowanego udziału plików VDI na aktualizacje analizy zabezpieczeń](#set-up-a-dedicated-vdi-file-share)
- [Randomizowanie zaplanowanych skanów](#randomize-scheduled-scans)
- [Korzystanie z szybkich skanów](#use-quick-scans)
- [Uniemożliwianie powiadomień](#prevent-notifications)
- [Wyłącz skany po każdej aktualizacji](#disable-scans-after-an-update)
- [Skanowanie aktualnych komputerów lub komputerów, które przez jakiś czas były w trybie offline](#scan-vms-that-have-been-offline)
- [Stosowanie wykluczeń](#exclusions)

Możesz również pobrać narzędzie do testowania oprogramowania [Program antywirusowy Microsoft Defender](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf) infrastruktury pulpitów wirtualnych, które wraz z testami wydajności i wskazówkami na temat testowania wydajności oprogramowania antywirusowego we własnej infrastrukturze pulpitu VDI przejrzysz nową funkcję udostępnionej analizy zabezpieczeń.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

> [!IMPORTANT]
> Mimo że VDI może być hostowane w programie Windows Server 2012 lub Windows Server 2016, maszyny wirtualne powinny być uruchomione co najmniej Windows 10 1607 ze względu na zwiększone technologie ochrony i funkcje, które są niedostępne we wcześniejszych wersjach programu Windows.
>
> Wprowadzono ulepszenia wydajności i funkcji w sposób, w jaki program Microsoft Defender AV działa na komputerach wirtualnych w programie Windows 10 Insider Preview, kompilacja 18323 (lub nowszy). Zidentyfikujemy to w tym przewodniku, jeśli musisz korzystać z kompilacji Insider Preview; jeśli nie zostanie określone, minimalna wymagana wersja dla najlepszej ochrony i wydajności wynosi Windows 10 1607.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Konfigurowanie dedykowanego udziału plików VDI

W Windows 10, w wersji 1903, wprowadzono funkcję udostępnionej analizy zabezpieczeń, która pobiera rozpakowywanie pobranych aktualizacji analizy zabezpieczeń na komputer-hosta, zapisując tym samym poprzedni procesor, dysk i zasoby pamięci na poszczególnych komputerach. Ta funkcja została wyeksportowana i działa Windows 10 wersja 1703 i nowsza. Tę funkcję można ustawić za pomocą programu zasady grupy lub PowerShell.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Użyj zasady grupy, aby włączyć funkcję udostępnionej analizy zabezpieczeń:

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami zasady grupy, kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Kliknij **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij dwukrotnie **pozycję Definiuj lokalizację analizy zabezpieczeń dla klientów VDI**, a następnie ustaw opcję **Włączone**. Pole zostanie automatycznie wyświetlone.

6. Wprowadź `\\<sharedlocation\>\wdav-update` wartość (aby uzyskać pomoc na temat tej wartości, [zobacz Pobieranie i rozpakowywanie](#download-and-unpackage-the-latest-updates)).

7. Kliknij przycisk **OK**.

8. Wdeksuj usługę zasad grupy na maszyny wirtualne, które chcesz przetestować.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Włączanie funkcji udostępnionej analizy zabezpieczeń przy użyciu programu PowerShell

Aby włączyć tę funkcję, użyj następującego polecenia cmdlet. Następnie należy wypchnąć tę normalnie normalnie zasady konfiguracji oparte na programie PowerShell do maszyn wirtualnych:

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

Zobacz [sekcję Pobieranie i rozpakowywanie](#download-and-unpackage-the-latest-updates) , aby uzyskać informacje na temat tego, co \<shared location\> będzie.

## <a name="download-and-unpackage-the-latest-updates"></a>Pobieranie i rozpakowywanie najnowszych aktualizacji

Teraz możesz rozpocząć pobieranie i instalowanie nowych aktualizacji. Poniżej został utworzony przykładowy skrypt programu PowerShell. Jest to najprostszy sposób pobierania nowych aktualizacji i przygotowania ich na maszyny wirtualne. Następnie należy skonfigurować skrypt do uruchamiania w określonym czasie na komputerze zarządzania przy użyciu zaplanowanego zadania (lub, jeśli wiesz, jak używać skryptów programu PowerShell w usłudze Azure, Intune lub SCCM, możesz również używać tych skryptów).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd $vdmpath & c: & mpam-fe.exe /x"
```

Zaplanowane zadanie można skonfigurować tak, aby było uruchamiane raz dziennie, dzięki czemu zawsze po pobraniu i rozpakowaniu pakietu maszyny wirtualne otrzymają nową aktualizację.
Zalecamy, aby zaczynać się raz dziennie, ale należy poeksperymentować ze zwiększeniem lub zmniejszeniem częstotliwości, aby zrozumieć wpływ tej zmian.

Pakiety analizy zabezpieczeń są zwykle publikowane co trzy do czterech godzin. Nie zaleca się ustawiania częstotliwości krótszych niż cztery godziny, ponieważ spowoduje to zwiększenie narzutu sieciowego na komputerze zarządzania bez dodatkowych korzyści.

Możesz również skonfigurować pojedynczy serwer lub komputer w celu pobierania aktualizacji w imieniu maszyn wirtualnych w interwale czasu i umieszczać je w udziałach plików do użycia.
Jest to możliwe, gdy urządzenia mają uprawnienia udostępniania i systemu plików NTFS do odczytu dla tego udziału, aby uzyskać dostęp do aktualizacji.

W tym celu:
 1. Tworzenie udziału plików SMB/CIFS. 
 
 2. Użyj poniższego przykładu, aby utworzyć udział plików z następującymi uprawnieniami udostępniania.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > Dodano uprawnienie NTFS dla **uwierzytelnionych użytkowników:Odczyt:**. 

    W tym przykładzie udział plików to:

    \\\fileserver.fqdn\mdatp$\wdav-update

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>Ustawianie zaplanowanego zadania w celu uruchomienia skryptu programu PowerShell

1. Na komputerze zarządzania otwórz menu Start i wpisz **Harmonogram zadań**. Otwórz go i **wybierz pozycję Utwórz zadanie...** na panelu bocznym.

2. Wprowadź nazwę jako **rozpakowywanie analizy zabezpieczeń**. Przejdź do karty **Wyzwalacz** . Wybierz **pozycję Nowy...** \> **Codziennie** i wybierz przycisk **OK**.

3. Przejdź do karty **Akcje** . Wybierz **pozycję Nowy...** Wprowadź **program PowerShell** **w polu Program/Skrypt** . Wprowadź `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` wartość w **polu Dodaj argumenty** . Wybierz przycisk **OK**.

4. Jeśli chcesz, możesz skonfigurować dodatkowe ustawienia.

5. Wybierz **przycisk OK** , aby zapisać zaplanowane zadanie.

Aktualizację możesz zainicjować ręcznie, klikając zadanie prawym przyciskiem myszy i klikając polecenie **Uruchom**.

### <a name="download-and-unpackage-manually"></a>Ręczne pobieranie i rozpakowywanie

Jeśli wolisz zrobić wszystko ręcznie, oto co należy zrobić, aby zreplikować zachowanie skryptu:

1. Utwórz w katalogu głównym systemu nowy `wdav_update` folder, na przykład w celu przechowywania aktualizacji analizy.`c:\wdav_update`

2. Tworzenie podfolderu w *obszarze wdav_update* z nazwą identyfikatora GUID, taką jak `{00000000-0000-0000-0000-000000000000}`

   Oto przykład: `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > W skrypcie ustawiliśmy go tak, aby ostatnich 12 cyfr identyfikatora GUID to rok, miesiąc, dzień i godzina pobrania pliku, aby za każdym razem został utworzony nowy folder. Możesz to zmienić, aby za każdym razem plik był pobierany do tego samego folderu.

3. Pobierz pakiet analizy zabezpieczeń z folderu [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  identyfikatorów GUID. Plik powinien mieć nazwę `mpam-fe.exe`.

4. Otwórz okno monitu polecenia cmd i przejdź do utworzonego folderu identyfikatora GUID. Za pomocą **polecenia wyodrębniania /X** wyodrębnij pliki, na przykład `mpam-fe.exe /X`.

   > [!NOTE]
   > Maszyny wirtualne przechowywają zaktualizowany pakiet za każdym razem, gdy zostanie utworzony nowy folder identyfikatora GUID z wyodrębniony pakietem aktualizacji lub za każdym razem, gdy istniejący folder zostanie zaktualizowany za pomocą nowego wyodrębniowanego pakietu.

## <a name="randomize-scheduled-scans"></a>Randomizowanie zaplanowanych skanów

Zaplanowane skanowania są uruchamiane poza ochroną [w czasie rzeczywistym i skanowaniem](configure-real-time-protection-microsoft-defender-antivirus.md).

Czas rozpoczęcia samego skanowania jest nadal oparty na zasadach zaplanowanego skanowania (**ScheduleDay**, **ScheduleTime** i **ScheduleQuickScanTime**). Randomizacja spowoduje, Program antywirusowy Microsoft Defender skanowanie na każdym komputerze w ciągu czterech godzin od czasu ustawionego na zaplanowane skanowanie.

Zobacz [Planowanie skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) , aby zobaczyć inne opcje konfiguracji dostępne dla zaplanowanych skanów.

## <a name="use-quick-scans"></a>Korzystanie z szybkich skanów

Można określić typ skanowania, który ma być wykonywany podczas zaplanowanego skanowania. Szybkie skanowanie to metoda preferowana, ponieważ została zaprojektowana tak, aby szukać we wszystkich miejscach, w których musi być aktywne złośliwe oprogramowanie. W poniższej procedurze opisano, jak skonfigurować szybkie skanowanie przy użyciu zasady grupy.

1. W Edytorze zasady grupy przejdź do **strony Szablony** \> administracyjne dla **Windows składników Program antywirusowy Microsoft Defender** \>  \> **Skanuj**.

2. Wybierz **pozycję Określ typ skanowania do użycia w zaplanowanym skanie, a** następnie edytuj ustawienie zasad.

3. Ustaw dla zasad wartość **Włączone**, a następnie w **obszarze Opcje** wybierz pozycję  **Szybkie skanowanie**.

4. Wybierz przycisk **OK**.

5. Wdeksuj zasady grupy obiekt tak jak zwykle.

## <a name="prevent-notifications"></a>Uniemożliwianie powiadomień

Czasami mogą Program antywirusowy Microsoft Defender lub zachowywać się w wielu sesjach. Aby zminimalizować ten problem, możesz zablokować Program antywirusowy Microsoft Defender interfejsu użytkownika. Poniżej opisano procedurę pomiń powiadomienia za pomocą zasady grupy.

1. W Edytorze zasady grupy przejdź do Windows **składników Program antywirusowy Microsoft Defender** \>  \> **Klienta**.

2. Wybierz **pozycję Pomiń wszystkie** powiadomienia, a następnie edytuj ustawienia zasad.

3. Ustaw dla zasad wartość **Włączone**, a następnie wybierz przycisk **OK**.

4. Wdeksuj zasady grupy obiekt tak jak zwykle.

Pomiń powiadomienia zapobiega wyświetlaniu Program antywirusowy Microsoft Defender w Centrum akcji na Windows 10 w przypadku skanowania lub działań naprawczych. Wyniki skanowania są jednak wyzwolone i zatrzymywane przez zespół operacyjny zabezpieczeń. Podczas wykrycia i zatrzymania ataków alerty, takie jak "alert dostępu początkowego", zostały wyzwolone i pojawiły się w portalu [Microsoft 365 Defender.](/microsoft-365/security/defender/microsoft-365-defender)

> [!TIP]
> Aby otworzyć Centrum akcji na Windows 10 lub Windows 11, zrób tak:
>
> - Na prawym końcu paska zadań wybierz ikonę Centrum akcji.
> - Naciśnij klawisz Windows klawisz logo + A.
> - Na urządzeniu z ekranem dotykowym szybko przesuń od prawej krawędzi ekranu.

## <a name="disable-scans-after-an-update"></a>Wyłączanie skanów po aktualizacji

Wyłączenie skanowania po aktualizacji zapobiegnie występowaniu skanu po otrzymaniu aktualizacji. To ustawienie można zastosować podczas tworzenia obrazu podstawowego, jeśli jest również uruchomione szybkie skanowanie. Dzięki temu możesz zapobiec wykonaniu skanowania przez nowo zaktualizowaną maszyny wirtualnej (tak jak skanowałeś ją już podczas tworzenia obrazu podstawowego).

> [!IMPORTANT]
> Uruchamiając skany po aktualizacji, można upewnić się, że maszyny wirtualne są chronione za pomocą najnowszych aktualizacji analizy zabezpieczeń. Wyłączenie tej opcji zmniejszy poziom ochrony maszyn wirtualnych i powinno być używane tylko podczas tworzenia lub wdrażania obrazu podstawowego.

1. W Edytorze zasady grupy przejdź do części Windows **i Program antywirusowy Microsoft Defender** \>  \> **aktualizacji analizy zabezpieczeń**.

2. Wybierz **pozycję Włącz skanowanie po aktualizacji analizy zabezpieczeń,** a następnie edytuj ustawienie zasad.

3. Ustaw dla zasad wartość **Wyłączone**.

4. Wybierz przycisk **OK**.

5. Wdeksuj zasady grupy obiekt tak jak zwykle.

Te zasady zapobiegają uruchamianiu skanowania natychmiast po aktualizacji.

## <a name="scan-vms-that-have-been-offline"></a>Skanowanie maszyn wirtualnych, które zostały w trybie offline

1. W Edytorze zasady grupy przejdź do części **Windows składników Program antywirusowy Microsoft Defender** \>  \> **Skanuj**.

2. Wybierz **pozycję Włącz szybkie skanowanie,** a następnie edytuj ustawienie zasad.

3. Ustaw dla zasad wartość **Włączone**.

4. Wybierz przycisk **OK**.

5. Wdeksuj obiekt zasady grupy tak jak zwykle.

Te zasady wymuszają skanowanie, jeśli maszyny wirtualnej pominięto dwa lub więcej następujących po sobie, zaplanowanych skanów.

## <a name="enable-headless-ui-mode"></a>Włączanie trybu bezgłowego interfejsu użytkownika

1. W Edytorze zasady grupy przejdź do Windows **składników Program antywirusowy Microsoft Defender** \>  \> **Klienta**.

2. Wybierz **opcję Włącz tryb interfejsu użytkownika** bez głowy i edytuj zasady.

3. Ustaw dla zasad wartość **Włączone**.

4. Kliknij przycisk **OK**.

5. Wdeksuj obiekt zasady grupy tak jak zwykle.

Te zasady ukrywają cały Program antywirusowy Microsoft Defender użytkownika przed użytkownikami końcowymi w organizacji.

## <a name="exclusions"></a>Wykluczenia

Wykluczenia można dodawać, usuwać lub dostosowywać do własnych potrzeb.

Aby uzyskać więcej informacji, [zobacz Konfigurowanie Program antywirusowy Microsoft Defender wykluczeń na Windows Server](configure-exclusions-microsoft-defender-antivirus.md).

## <a name="additional-resources"></a>Dodatkowe materiały

- [Blog Community tech: Konfigurowanie Program antywirusowy Microsoft Defender dla nietrwałych komputerów VDI](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [Fora TechNet dotyczące usług pulpitu zdalnego i VDI](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [SignatureDownloadCustomTask skrypt programu PowerShell](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
