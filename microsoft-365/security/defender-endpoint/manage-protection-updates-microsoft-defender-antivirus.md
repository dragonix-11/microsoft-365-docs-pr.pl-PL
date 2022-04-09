---
title: Zarządzanie sposobem i miejscem, w którym Program antywirusowy Microsoft Defender odbiera aktualizacje
description: Zarządzaj kolejnością rezerwy, aby dowiedzieć się, jak Program antywirusowy Microsoft Defender odbiera aktualizacje ochrony.
keywords: updates, security baselines, protection, fallback order, ADL, MMPC, UNC, file path, share, wsus
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
ms.openlocfilehash: 04cedfa951387274261c3a7a064cf11a4b97db62
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731466"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Zarządzaj źródłami aktualizacji programu antywirusowego Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Aktualizowanie ochrony antywirusowej ma kluczowe znaczenie. Istnieją dwa składniki do zarządzania aktualizacjami ochrony dla Program antywirusowy Microsoft Defender:

- *Skąd* są pobierane aktualizacje; I
- *Po* pobraniu i zastosowaniu aktualizacji.

W tym artykule opisano sposób określania miejsca pobierania aktualizacji (jest to również określane jako kolejność rezerwowa). Zobacz [Temat Manage Program antywirusowy Microsoft Defender updates and apply baselines (Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)), aby zapoznać się z omówieniem sposobu działania aktualizacji oraz sposobu konfigurowania innych aspektów aktualizacji (takich jak planowanie aktualizacji).

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender aktualizacje analizy zabezpieczeń i aktualizacje platformy są dostarczane za pośrednictwem Windows Update i od poniedziałku, 21 października 2019 r., wszystkie aktualizacje analizy zabezpieczeń będą podpisane wyłącznie przez algorytm SHA-2. Aby zaktualizować analizę zabezpieczeń, urządzenia muszą zostać zaktualizowane w celu obsługi algorytmu SHA-2. Aby dowiedzieć się więcej, zobacz [2019 SHA-2 Code Signing Support requirement for Windows and WSUS (Wymagania dotyczące obsługi podpisywania kodu SHA-2 w wersji 2019 dla Windows i WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus)).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Kolejność rezerwowa

Zazwyczaj punkty końcowe są konfigurowane w celu indywidualnego pobierania aktualizacji ze źródła podstawowego, a następnie innych źródeł w kolejności priorytetu na podstawie konfiguracji sieci. Aktualizacje są uzyskiwane ze źródeł w określonej kolejności. Jeśli aktualizacje z bieżącego źródła są nieaktualne, następne źródło na liście zostanie użyte natychmiast.

Po opublikowaniu aktualizacji stosowana jest pewna logika w celu zminimalizowania rozmiaru aktualizacji. W większości przypadków pobierane i stosowane są tylko różnice między najnowszą aktualizacją a aktualnie zainstalowaną aktualizacją (nazywaną różnicą) na urządzeniu. Jednak rozmiar różnicy zależy od dwóch głównych czynników:

- Wiek ostatniej aktualizacji na urządzeniu; I
- Źródło używane do pobierania i stosowania aktualizacji.

Tym starsze aktualizacje w punkcie końcowym, tym większe będzie pobieranie. Należy jednak również rozważyć częstotliwość pobierania. Częstsze aktualizowanie harmonogramu może spowodować większe użycie sieci, podczas gdy rzadziej spotykany harmonogram może powodować większe rozmiary plików na pobranie.

Istnieje pięć lokalizacji, w których można określić, gdzie punkt końcowy powinien uzyskać aktualizacje:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Server Update Service](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [Udział plików sieciowych](#unc-share)
- [Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innych programów chroniących przed złośliwym oprogramowaniem](https://www.microsoft.com/wdsi/defenderupdates) <sup>firmy Microsoft [[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune wewnętrzny serwer aktualizacji definicji — jeśli używasz programu SCCM/SUP do pobierania aktualizacji definicji dla Program antywirusowy Microsoft Defender i potrzebujesz dostępu do Windows Update na zablokowanych urządzeniach klienckich, możesz przejść do współzarządzania i odciążyć obciążenie ochrony punktu końcowego do Intune. W zasadach ochrony przed złośliwym oprogramowaniem skonfigurowanych w Intune istnieje opcja "wewnętrznego serwera aktualizacji definicji", którą można skonfigurować do używania lokalnego programu WSUS jako źródła aktualizacji. Ułatwia to kontrolowanie, które aktualizacje z oficjalnego serwera WU są zatwierdzane dla przedsiębiorstwa, a także pomaga serwerowi proxy i zapisywaniu ruchu sieciowego w oficjalnej sieci Windows UPdates.

(<a id="fn1">2</a>) Zasady i rejestr mogą zawierać te informacje jako Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem analizy zabezpieczeń (MMPC), jej poprzednia nazwa.

Aby zapewnić najlepszy poziom ochrony, usługa Microsoft Update umożliwia szybkie wersje, co oznacza częste pobieranie mniejszych plików. Źródła Windows Server Update Service, Microsoft Endpoint Configuration Manager, aktualizacje analizy zabezpieczeń firmy Microsoft i źródła aktualizacji platformy zapewniają rzadsze aktualizacje. W związku z tym delta może być większa, co powoduje większe pliki do pobrania.

> [!NOTE]
> Aktualizacje analizy zabezpieczeń zawierają aktualizacje aparatu i są wydawane co miesiąc.
Aktualizacje analizy zabezpieczeń są również dostarczane wiele razy dziennie, ale ten pakiet nie zawiera aparatu.


> [!IMPORTANT]
> Jeśli aktualizacje [strony analizy zabezpieczeń firmy Microsoft](https://www.microsoft.com/security/portal/definitions/adl.aspx) zostały ustawione jako źródło rezerwowe po Windows Server Update Service lub Microsoft Update, aktualizacje są pobierane z aktualizacji analizy zabezpieczeń i aktualizacji platformy tylko wtedy, gdy bieżąca aktualizacja jest uważana za nieaktualną. (Domyślnie jest to siedem kolejnych dni, w których nie można zastosować aktualizacji z usługi Windows Server Update Lub usług Microsoft Update).
> Można jednak [ustawić liczbę dni, po których ochrona zostanie zgłoszona jako nieaktualna](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> Od poniedziałku, 21 października 2019 r. aktualizacje analizy zabezpieczeń i aktualizacje platformy będą podpisane wyłącznie przez algorytm SHA-2. Aby uzyskać najnowsze aktualizacje analizy zabezpieczeń i aktualizacje platformy, należy zaktualizować urządzenia w celu obsługi algorytmu SHA-2. Aby dowiedzieć się więcej, zobacz [2019 SHA-2 Code Signing Support requirement for Windows and WSUS (Wymagania dotyczące obsługi podpisywania kodu SHA-2 w wersji 2019 dla Windows i WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus)).

Każde źródło ma typowe scenariusze, które zależą od sposobu konfigurowania sieci oprócz tego, jak często publikują aktualizacje, zgodnie z opisem w poniższej tabeli:

<br/><br/>

|Lokalizacja|Przykładowy scenariusz|
|---|---|
|usługa aktualizacji serwera Windows|Do zarządzania aktualizacjami sieci używasz usługi aktualizacji serwera Windows.|
|Microsoft Update|Punkty końcowe mają łączyć się bezpośrednio z usługą Microsoft Update. Może to być przydatne w przypadku punktów końcowych, które nieregularnie łączą się z siecią przedsiębiorstwa lub jeśli nie używasz usługi aktualizacji serwera Windows do zarządzania aktualizacjami.|
|Udział plików|Masz urządzenia bez połączenia z Internetem (takie jak maszyny wirtualne). Host maszyny wirtualnej połączonej z Internetem umożliwia pobranie aktualizacji do udziału sieciowego, z którego maszyny wirtualne mogą uzyskać aktualizacje. Zobacz [przewodnik wdrażania interfejsu VDI](deployment-vdi-microsoft-defender-antivirus.md) , aby dowiedzieć się, jak można używać udziałów plików w środowiskach infrastruktury pulpitu wirtualnego (VDI).|
|Microsoft Endpoint Manager|Używasz Microsoft Endpoint Manager do aktualizowania punktów końcowych.|
|Aktualizacje analizy zabezpieczeń i aktualizacje platformy dla Program antywirusowy Microsoft Defender i innych programów ochrony przed złośliwym oprogramowaniem firmy Microsoft (wcześniej nazywanych MMPC)|[Upewnij się, że urządzenia zostały zaktualizowane w celu obsługi algorytmu SHA-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Program antywirusowy Microsoft Defender Aktualizacje analizy zabezpieczeń i platformy są dostarczane za pośrednictwem Windows Update, a od poniedziałku 21 października 2019 r. aktualizacje analizy zabezpieczeń i aktualizacje platformy będą podpisane wyłącznie przez ALGORYTM SHA-2. <br/>Pobierz najnowsze aktualizacje ochrony z powodu niedawnej infekcji lub aby ułatwić aprowizowanie silnego obrazu podstawowego dla [wdrożenia interfejsu VDI](deployment-vdi-microsoft-defender-antivirus.md). Ta opcja powinna być zwykle używana tylko jako ostateczne źródło rezerwowe, a nie źródło podstawowe. Będzie on używany tylko wtedy, gdy aktualizacje nie mogą być pobierane z usługi Windows Server Update Lub Microsoft Update przez [określoną liczbę dni](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

Możesz zarządzać kolejnością, w jakiej źródła aktualizacji są używane z zasady grupy, Microsoft Endpoint Configuration Manager, poleceniami cmdlet programu PowerShell i usługą WMI.

> [!IMPORTANT]
> Jeśli ustawisz usługę Windows Server Update Service jako lokalizację pobierania, musisz zatwierdzić aktualizacje, niezależnie od narzędzia do zarządzania używanego do określania lokalizacji. Regułę automatycznego zatwierdzania można skonfigurować za pomocą usługi Windows Server Update Service, która może być przydatna, ponieważ aktualizacje pojawiają się co najmniej raz dziennie. Aby dowiedzieć się więcej, zobacz [synchronizowanie aktualizacji programu Endpoint Protection w autonomicznej usłudze Windows Server Update Service](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Procedury opisane w tym artykule najpierw opisują sposób ustawiania kolejności, a następnie konfigurowanie opcji **Udział plików** , jeśli została włączona.

## <a name="use-group-policy-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji przy użyciu zasady grupy

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Windows Defender** \> **aktualizacje podpisu** i skonfiguruj następujące ustawienia:

   1. Kliknij dwukrotnie ustawienie **Zdefiniuj kolejność źródeł pobierania aktualizacji analizy zabezpieczeń** i ustaw opcję **Włączone**.

   2. Wprowadź kolejność źródeł rozdzielonych pojedynczym potokiem, na przykład: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`, jak pokazano na poniższym zrzucie ekranu.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="Ustawienie zasad grupy z listą kolejności źródeł" lightbox="../../media/wdav-order-update-sources.png":::

   3. Wybierz przycisk **OK**. Spowoduje to ustawienie kolejności źródeł aktualizacji ochrony.

   4. Kliknij dwukrotnie ustawienie **Zdefiniuj udziały plików do pobierania aktualizacji analizy zabezpieczeń** i ustaw opcję **Włączone**.

   5. Określ źródło udziału plików. Jeśli masz wiele źródeł, wprowadź każde źródło w kolejności, w jakiej powinny być używane, oddzielone pojedynczym potokiem. Użyj [standardowej notacji UNC](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) do oznaczania ścieżki, na przykład: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Jeśli nie wprowadzisz żadnych ścieżek, to źródło zostanie pominięte, gdy maszyna wirtualna pobierze aktualizacje.

   6. Kliknij przycisk **OK**. Spowoduje to ustawienie kolejności udziałów plików, gdy do tego źródła odwołuje się ustawienie zasad **Zdefiniuj kolejność źródeł...** grupy.

> [!NOTE]
> W przypadku Windows 10 w wersji 1703 do 1809 włącznie ścieżka zasad to **Windows Components > Program antywirusowy Microsoft Defender > Signature Updates** For Windows 10, wersja 1903, ścieżka zasad to **Windows Components > aktualizacje analizy zabezpieczeń Program antywirusowy Microsoft Defender >**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji przy użyciu Configuration Manager

Aby uzyskać szczegółowe informacje na temat konfigurowania Microsoft Endpoint Manager (bieżącej gałęzi), zobacz [Konfigurowanie aktualizacji analizy zabezpieczeń dla Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet programu PowerShell, aby ustawić kolejność aktualizacji.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Aby uzyskać więcej informacji, zobacz następujące artykuły:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Konfigurowanie i uruchamianie Program antywirusowy Microsoft Defender przy użyciu poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Polecenia cmdlet programu antywirusowego Defender](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Aby uzyskać więcej informacji, zobacz następujące artykuły:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Zarządzanie lokalizacją aktualizacji przy użyciu usługi Mobile Zarządzanie urządzeniami (MDM)

Aby uzyskać szczegółowe informacje na temat konfigurowania zarządzania urządzeniami przenośnymi [, zobacz Zasady CSP — Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) .

## <a name="what-if-were-using-a-third-party-vendor"></a>Co zrobić, jeśli używamy dostawcy innej firmy?

W tym artykule opisano sposób konfigurowania aktualizacji dla Program antywirusowy Microsoft Defender i zarządzania nimi. Jednak do wykonywania tych zadań mogą służyć dostawcy innych firm.

Załóżmy na przykład, że firma Contoso zatrudniła usługę Fabrikam do zarządzania swoim rozwiązaniem zabezpieczeń, które obejmuje Program antywirusowy Microsoft Defender. Firma Fabrikam zwykle używa [instrumentacji zarządzania Windows](./use-wmi-microsoft-defender-antivirus.md), [poleceń cmdlet programu PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md) lub [Windows wiersza polecenia](./command-line-arguments-microsoft-defender-antivirus.md) do wdrażania poprawek i aktualizacji.

> [!NOTE]
> Firma Microsoft nie testuje rozwiązań innych firm do zarządzania Program antywirusowy Microsoft Defender.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-and-platform-updates"></a>Tworzenie udziału UNC na potrzeby analizy zabezpieczeń i aktualizacji platformy

Skonfiguruj udział plików sieciowych (dysk UNC/mapowany), aby pobierać analizę zabezpieczeń i aktualizacje platformy z lokacji PROGRAMU MMPC przy użyciu zaplanowanego zadania.

1. W systemie, w którym chcesz aprowizować udział i pobrać aktualizacje, utwórz folder, w którym zapiszesz skrypt.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. Utwórz folder, w którym zostaną zapisane aktualizacje podpisu.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Pobierz skrypt programu PowerShell z [www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. Kliknij pozycję **Pobierz ręcznie**.

5. Kliknij **pozycję Pobierz nieprzetworzony plik nupkg**.

6. Wyodrębnij plik.

7. Skopiuj plik SignatureDownloadCustomTask.ps1 do utworzonego `C:\Tool\PS-Scripts\` wcześniej folderu .

8. Użyj wiersza polecenia, aby skonfigurować zaplanowane zadanie.

   > [!NOTE]
   > Istnieją dwa typy aktualizacji: pełne i różnicowe.

   - W przypadku różnicy x64:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Dla x64 full:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - W przypadku różnicy x86:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Dla x86 full:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > Po utworzeniu zaplanowanych zadań można je znaleźć w harmonogramie zadań w obszarze `Microsoft\Windows\Windows Defender`.

9. Uruchom każde zadanie ręcznie i sprawdź, czy masz dane (`mpam-d.exe`, `mpam-fe.exe`i `nis_full.exe`) w następujących folderach (być może wybrano różne lokalizacje):

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

10. Utwórz udział wskazujący na `C:\Temp\TempSigs` (np. `\\server\updates`).

    > [!NOTE]
    > Co najmniej uwierzytelnieni użytkownicy muszą mieć dostęp do odczytu. To wymaganie dotyczy również komputerów domeny, udziału i systemu plików NTFS (zabezpieczenia).

11. Ustaw lokalizację udziału w zasadach na udział.

    > [!NOTE]
    > Nie należy dodawać folderu x64 (lub x86) w ścieżce. Proces mpcmdrun.exe dodaje go automatycznie.

## <a name="related-articles"></a>Artykuły pokrewne

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
