---
title: Zarządzanie tym, jak i gdzie Program antywirusowy Microsoft Defender otrzymuje aktualizacje
description: Zarządzaj kolejnością rezerwową, aby dowiedzieć się, Program antywirusowy Microsoft Defender otrzymywać aktualizacje ochrony.
keywords: aktualizacje, linie bazowe zabezpieczeń, ochrona, kolejność rezerwowa, ADL, MMPC, UNC, ścieżka pliku, udostępnianie, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 69c211e02b5bea12431e17bf2256405f96977b53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467428"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Zarządzanie źródłami aktualizacji Program antywirusowy Microsoft Defender ochrony

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Zapewnienie aktualnej ochrony antywirusowej jest bardzo ważne. Istnieją dwa składniki do zarządzania aktualizacjami ochrony dla Program antywirusowy Microsoft Defender:

- *Miejsce* pobierania aktualizacji; i
- *Podczas* pobierania i stosowania aktualizacji.

W tym artykule opisano sposób określania miejsca, z którego mają być pobierane aktualizacje (ta kolejność jest również określana jako kolejność rezerwowa). Zobacz [temat Program antywirusowy Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md) i stosowanie planu bazowego, aby uzyskać omówienie sposobu działania aktualizacji i sposobu konfigurowania innych aspektów aktualizacji (na przykład planowania aktualizacji).

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender aktualizacje analizy zabezpieczeń są dostarczane za pośrednictwem systemu Windows Update, a począwszy od poniedziałku 21 października 2019 r., wszystkie aktualizacje analizy zabezpieczeń będą podpisane wyłącznie przez sha-2. Aby zaktualizować analizy zabezpieczeń, należy zaktualizować urządzenia, aby obsługiły sha-2. Aby dowiedzieć się więcej, zobacz [Wymaganie obsługi podpisywania kodu SHA-2 2 dla programu Windows i programu WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Kolejność rezerwowa

Zazwyczaj konfigurowane są punkty końcowe tak, aby poszczególne aktualizacje z podstawowego źródła, po których następuje inne źródła, w kolejności priorytetu, na podstawie konfiguracji sieci. Aktualizacje są uzyskiwane ze źródeł w  sposób określony przez użytkownika. Jeśli aktualizacje z bieżącego źródła są aktualne, natychmiast zostanie użyte następne źródło z listy.

Po opublikowaniu aktualizacji stosowana jest logika w celu zminimalizowania rozmiaru aktualizacji. W większości przypadków pobierane i stosowane są tylko różnice między najnowszą aktualizacją a aktualizacją, która jest obecnie zainstalowana (jest to nazywane różnicą). Jednak rozmiar różnicy zależy od dwóch głównych czynników:

- Wiek ostatniej aktualizacji na urządzeniu; i
- Źródło używane do pobierania i stosowania aktualizacji.

Im starsze aktualizacje dla punktu końcowego, tym większe będą dostępne pliki do pobrania. Należy jednak również rozważyć częstotliwość pobierania. Częstszy harmonogram aktualizacji może powodować większe użycie sieci, natomiast rzadziej ten harmonogram może skutkować większymi rozmiarami plików podczas pobierania.

Istnieje pięć lokalizacji, w których można określić, gdzie punkt końcowy ma uzyskiwać aktualizacje:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows aktualizacji serwera](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [Sieciowy udział plików](#unc-share)
- [Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innego złośliwego oprogramowania](https://www.microsoft.com/wdsi/defenderupdates) <sup>firmy Microsoft [[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune Internal Definition Update Server — jeśli korzystasz z usług SCCM/SUP w celu uzyskiwania aktualizacji definicji dla usługi Program antywirusowy Microsoft Defender i potrzebujesz dostępu do usługi Windows Update na urządzeniach klienckich zablokowanych, możesz przejść do współzawładowania i odładować obciążenie pracą ochrony punktu końcowego do Intune. W zasadach ochrony przed złośliwym oprogramowaniem skonfigurowanych w programie Intune dostępna jest opcja "wewnętrzny serwer aktualizacji definicji", który można skonfigurować do używania lokalnego programu WSUS jako źródła aktualizacji. Pozwala to kontrolować, które aktualizacje z oficjalnego serwera organizacji WU zostały zatwierdzone do przedsiębiorstwa, a także pomóc serwerowi proxy i zapisać ruch sieciowy w oficjalnej sieci Windows UPdates.

(<a id="fn1">2</a>) Zasady i rejestr mogą mieć na liście zabezpieczenia Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem (MMPC) lub wcześniejszą nazwę.

W celu zapewnienia jak najlepszego poziomu ochrony usługa Microsoft Update umożliwia szybkie wersje, co oznacza częste mniejsze pliki do pobrania. Źródła Windows aktualizacji serwera oraz Microsoft Endpoint Configuration Manager i analizy zabezpieczeń firmy Microsoft dostarczają rzadziej aktualizowane aktualizacje. Różnica może być zatem większa, co spowoduje pobranie większej ilości danych.

> [!IMPORTANT]
> Jeśli ustawiono aktualizacje strony analizy zabezpieczeń firmy [Microsoft](https://www.microsoft.com/security/portal/definitions/adl.aspx) jako źródło rezerwowe po zaktualizowaniu usługi Windows Server Update lub usługi Microsoft Update, aktualizacje są pobierane z aktualizacji analizy zabezpieczeń tylko wtedy, gdy bieżąca aktualizacja jest uznawana za aktualną. Domyślnie jest to siedem kolejnych dni bez możliwości stosowania aktualizacji z usługi Windows Server Update lub usług Microsoft Update.
> Można jednak ustawić liczbę dni, po których ochrona będzie [zgłaszana jako "aktualny"](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> Począwszy od poniedziałku 21 października 2019 r., aktualizacje analizy zabezpieczeń będą podpisane wyłącznie przez sha-2. Aby uzyskać najnowsze aktualizacje analizy zabezpieczeń, należy zaktualizować urządzenia, aby obsługiły technologię SHA-2. Aby dowiedzieć się więcej, zobacz [Wymaganie obsługi podpisywania kodu SHA-2 2 dla programu Windows i programu WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Każde źródło ma typowe scenariusze, które zależą od konfiguracji sieci, a także to, jak często publikują aktualizacje, jak opisano w poniższej tabeli:

<br/><br/>

|Lokalizacja|Przykładowy scenariusz|
|---|---|
|Windows aktualizacji serwera|Do zarządzania aktualizacjami Windows używasz usługi aktualizacji serwera.|
|Microsoft Update|Chcesz, aby punkty końcowe łączyły się bezpośrednio z usługą Microsoft Update. Może to być przydatne w przypadku punktów końcowych, które nieregularnie łączą się z siecią przedsiębiorstwa, lub jeśli nie zarządza się aktualizacjami za pomocą usługi Windows Server Update Service.|
|Udział plików|Masz urządzenia inne niż połączone z Internetem (takie jak maszyny wirtualne). Aktualizacje udziału sieciowego można pobrać za pomocą podłączonego do Internetu hosta maszyny wirtualnej, z którego maszyny wirtualne mogą uzyskać aktualizacje. Zobacz przewodnik [wdrażania VDI](deployment-vdi-microsoft-defender-antivirus.md) , aby dowiedzieć się, jak można używać udziałów plików w środowiskach infrastruktury pulpitów wirtualnych (VDI).|
|Microsoft Endpoint Manager|Używasz programu Microsoft Endpoint Manager do aktualizowania punktów końcowych.|
|Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innego złośliwego oprogramowania firmy Microsoft (wcześniej nazywanego MMPC)|[Upewnij się, że urządzenia zostały zaktualizowane, aby obsługiły sha-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Program antywirusowy Microsoft Defender aktualizacje analizy zabezpieczeń są dostarczane za pośrednictwem firmy Windows Update, a od poniedziałku 21 października 2019 r. aktualizacje analizy zabezpieczeń sha-2 będą podpisane wyłącznie przez sha-2. <br/>Pobierz najnowsze aktualizacje ochrony z powodu ostatniej infekcji lub aby pomóc w zapewnianiu silnego, podstawowego obrazu wdrożenia [VDI](deployment-vdi-microsoft-defender-antivirus.md). Tej opcji na ogół należy używać tylko jako ostatecznego źródła zwrotnego, a nie jako źródła podstawowego. Będzie on używany tylko w przypadku, gdy nie można pobierać aktualizacji Windows usługi aktualizacji serwera lub usługi Microsoft Update przez określoną [liczbę dni](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

Możesz zarządzać kolejnością, w jakiej źródła aktualizacji są używane z zasady grupy, Microsoft Endpoint Configuration Manager cmdlet programu PowerShell i WMI.

> [!IMPORTANT]
> Jeśli ustawisz Windows aktualizacji serwera jako lokalizację pobierania, musisz zatwierdzić aktualizacje bez względu na narzędzie zarządzania, za pomocą których korzystasz do określania lokalizacji. Możesz skonfigurować regułę automatycznego zatwierdzania za pomocą usługi Windows Server Update Service, która może być przydatna, gdy aktualizacje są aktualizowane co najmniej raz dziennie. Aby dowiedzieć się więcej, [zobacz Synchronizowanie aktualizacji ochrony punktu końcowego w autonomicznej Windows aktualizacji serwera](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Procedury w tym artykule najpierw opisują sposób ustawienia kolejności, a następnie sposób skonfigurowania opcji Udziału plików, jeśli  została ona włączona.

## <a name="use-group-policy-to-manage-the-update-location"></a>Zarządzanie lokalizacją zasady grupy za pomocą programu Zasady grupy

1. Na zasady grupy zarządzania komputerami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracja komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Windows Defender** \>  \> **aktualizacji podpisu** i skonfiguruj następujące ustawienia:

   1. Kliknij dwukrotnie ustawienie **Definiuj kolejność źródeł aktualizacji** analizy zabezpieczeń i ustaw opcję **Włączone**.

   2. Wprowadź kolejność źródeł oddzielonych pojedynczą rurą, na przykład: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`, jak pokazano na poniższym zrzucie ekranu.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="Ustawienie zasad grupy z listą źródeł" lightbox="../../media/wdav-order-update-sources.png":::

   3. Wybierz przycisk **OK**. Zostanie ustawiona kolejność źródeł aktualizacji ochrony.

   4. Kliknij dwukrotnie ustawienie **Definiuj udziały plików na celu pobierania aktualizacji analizy** zabezpieczeń i ustaw opcję **Włączone**.

   5. Określ źródło udziału plików. Jeśli masz wiele źródeł, wprowadź poszczególne źródła w kolejności, w których powinny być używane, rozdzielając je pojedynczą rurą. Użyj [standardowej notacji UNC](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) do oznaczania ścieżki, na przykład: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Jeśli nie wprowadźsz żadnych ścieżek, to źródło zostanie pominięte po pobraniu aktualizacji przez maszyny wirtualne.

   6. Kliknij przycisk **OK**. Kolejność udziałów plików, do których odwołuje się to źródło, zostanie ustawiona w ustawieniu Definiuj kolejność źródeł **zasad grupy.**

> [!NOTE]
> W Windows 10, od wersji 1703 do 1809 włącznie ścieżka zasad to **Windows Składniki > Program antywirusowy Microsoft Defender > Aktualizacje** podpisu Dla systemu Windows 10 w wersji 1903 ścieżka zasad to Windows **Składniki > Program antywirusowy Microsoft Defender > aktualizacji analizy zabezpieczeń**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Zarządzanie Configuration Manager za pomocą programu Windows

Zobacz [Konfigurowanie aktualizacji analizy zabezpieczeń dla programu Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates), aby uzyskać szczegółowe informacje na temat Microsoft Endpoint Manager (bieżąca gałąź).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji przy użyciu poleceń cmdlet programu PowerShell

Aby ustawić kolejność aktualizacji, użyj następujących poleceń cmdlet programu PowerShell.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Aby uzyskać więcej informacji, zobacz następujące artykuły:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Polecenia cmdlet programu antywirusowego Defender](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Zarządzanie Windows lokalizacją aktualizacji przy użyciu instrukcji zarządzania danymi (WMI)

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Aby uzyskać więcej informacji, zobacz następujące artykuły:

- [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji Zarządzanie urządzeniami funkcji Zarządzanie urządzeniami przenośnymi (MDM)

Aby [uzyskać szczegółowe informacje na temat konfigurowania usługi MDM, zobacz CSP zasad — Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) .

## <a name="what-if-were-using-a-third-party-vendor"></a>Co zrobić, jeśli korzystamy z usług dostawcy z innej firmy?

W tym artykule opisano sposób konfigurowania aktualizacji aplikacji i zarządzania Program antywirusowy Microsoft Defender. Jednak do wykonywania tych zadań można użyć innych dostawców.

Załóżmy na przykład, że firma Contoso zatrudniła firmę Fabrikam do zarządzania swoim rozwiązaniem zabezpieczeń, które obejmuje Program antywirusowy Microsoft Defender. Firma Fabrikam zwykle używa Windows o instrumentacji [zarządzania, poleceń](./use-wmi-microsoft-defender-antivirus.md) [cmdlet programu PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md) Windows wiersza [](./command-line-arguments-microsoft-defender-antivirus.md) polecenia do wdrażania poprawek i aktualizacji.

> [!NOTE]
> Firma Microsoft nie testuje rozwiązań innych firm do zarządzania Program antywirusowy Microsoft Defender.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-updates"></a>Tworzenie udziału UNC na aktualizacje analizy zabezpieczeń

Skonfiguruj sieciowy udział plików (UNC/mapowany dysk), aby pobierać aktualizacje analizy zabezpieczeń z witryny MMPC przy użyciu zaplanowanego zadania.

1. W systemie, w którym chcesz aprowizować udostępnianie i pobrać aktualizacje, utwórz folder, w którym chcesz zapisać skrypt.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. Utwórz folder, w którym chcesz zapisać aktualizacje podpisu.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Pobierz skrypt programu PowerShell z [www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. Kliknij **pozycję Pobieranie ręczne**.

5. Kliknij **pozycję Pobierz nieprzetworzone pliki nupkg**.

6. Wyodrębnij plik.

7. Skopiuj plik SignatureDownloadCustomTask.ps1 do poprzednio utworzonego folderu . `C:\Tool\PS-Scripts\`

8. Konfigurowanie zaplanowanego zadania przy użyciu wiersza polecenia.

   > [!NOTE]
   > Istnieją dwa typy aktualizacji: pełne i różnicowe.

   - Dla różnicy x64:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - W przypadku wersji x64 pełnej:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Dla różnicy x86:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Wersja x86 pełna:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > Zaplanowane zadania można znaleźć w harmonogramie zadań w obszarze `Microsoft\Windows\Windows Defender`.

9. Uruchom każde zadanie ręcznie i sprawdź, czy masz dane (`mpam-d.exe`, `mpam-fe.exe`, i `nis_full.exe`) w następujących folderach (być może wybrano inne lokalizacje):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   Jeśli zaplanowane zadanie zakończy się niepowodzeniem, uruchom następujące polecenia:

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > Problemy mogą być również spowodowane zasadami wykonywania.

10. Tworzenie udziału z punktami `C:\Temp\TempSigs` (np. `\\server\updates`).

    > [!NOTE]
    > Uwierzytelnieni użytkownicy muszą mieć co najmniej dostęp do odczytu. To wymaganie dotyczy również komputerów z domeną, udziału i systemu plików NTFS (security).

11. Ustaw lokalizację udostępniania w zasadach na udostępnianie.

    > [!NOTE]
    > Nie dodawaj folderu x64 (lub x86) w ścieżce. Proces mpcmdrun.exe jest automatycznie do niego dodano.

## <a name="related-articles"></a>Artykuły pokrewne

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
