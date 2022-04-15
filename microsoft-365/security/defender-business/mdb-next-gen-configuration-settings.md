---
title: Omówienie ustawień konfiguracji ochrony nowej generacji w Microsoft Defender dla Firm
description: Omówienie ustawień konfiguracji ochrony nowej generacji w Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: eee272798be5396ad9ad15177fcd29a0180bc448
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862725"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>Omówienie ustawień konfiguracji nowej generacji w Microsoft Defender dla Firm

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

Ochrona nowej generacji w usłudze Defender for Business obejmuje niezawodny program antywirusowy i ochronę przed złośliwym kodem. Domyślne zasady mają na celu ochronę urządzeń i użytkowników bez ograniczania produktywności. Można jednak również dostosować zasady do własnych potrzeb biznesowych. A jeśli używasz Microsoft Endpoint Manager, możesz go użyć do zarządzania zasadami zabezpieczeń.

**W tym artykule opisano**:

- [Ustawienia i opcje ochrony następnej generacji](#next-generation-protection-settings-and-options)
- [Inne wstępnie skonfigurowane ustawienia w usłudze Defender dla Firm](#other-preconfigured-settings-in-defender-for-business) 
- [Ustawienia domyślne usługi Defender dla firm i Microsoft Endpoint Manager](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>Ustawienia i opcje ochrony następnej generacji

W poniższej tabeli wymieniono ustawienia i opcje:

| Ustawienie | Opis |
|:---|:---|
| **Ochrona w czasie rzeczywistym**  |  |
| **Włączanie ochrony w czasie rzeczywistym** | Domyślnie włączona ochrona w czasie rzeczywistym lokalizuje i uniemożliwia uruchamianie złośliwego oprogramowania na urządzeniach. *Zalecamy włączenie ochrony w czasie rzeczywistym.*<br/><br/>Po włączeniu ochrony w czasie rzeczywistym konfiguruje ona następujące ustawienia:<br/>- Monitorowanie zachowania jest włączone ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- Wszystkie pobrane pliki i załączniki są skanowane ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>— Skrypty używane w przeglądarkach firmy Microsoft są skanowane ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **Blokuj od pierwszego wejrzenia** | Domyślnie opcja blokuj od pierwszego wejrzenia blokuje złośliwe oprogramowanie w ciągu kilku sekund od wykrycia, wydłuża czas (w sekundach) na przesyłanie przykładowych plików do analizy i ustawia poziom wykrywania na wysoki. *Zalecamy włączenie blokady od pierwszego wejrzenia.*<br/><br/>Gdy blok od pierwszego wejrzenia jest włączony, konfiguruje następujące ustawienia dla Program antywirusowy Microsoft Defender: <br/>— Blokowanie i skanowanie podejrzanych plików jest ustawione na wysoki poziom blokowania ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>— Liczba sekund zablokowania i sprawdzenia pliku jest ustawiona na 50 sekund ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**WAŻNE**: Jeśli blok od pierwszego wejrzenia jest wyłączony, ma wpływ i `CloudBlockLevel` `CloudExtendedTimeout` na Program antywirusowy Microsoft Defender.  |
| **Wyłącz ochronę sieci** | Po włączeniu ochrona sieci pomaga chronić się przed wyłudzaniem informacji, witrynami hostu wykorzystującymi luki w zabezpieczeniach i złośliwą zawartością w Internecie. Zapobiega to również wyłączaniu ochrony sieci przez użytkowników.<br/><br/>Ochronę sieci można ustawić na jeden z następujących trybów:<br/>- **Tryb bloku** (to ustawienie jest domyślne), co uniemożliwia użytkownikom odwiedzanie witryn, które są uważane za niebezpieczne. *Zalecamy ustawienie ochrony sieci w trybie bloku.*<br/>- **Tryb inspekcji**, który umożliwia użytkownikom odwiedzanie witryn, które mogą być niebezpieczne, i śledzi aktywność sieci do/z takich witryn <br/>- **Tryb wyłączony**, który uniemożliwia użytkownikom odwiedzanie witryn, które mogą być niebezpieczne, ani śledzi aktywność sieci do/z takich witryn |
| **Korygowania**  |  |
| **Akcja do podjęcia w sprawie potencjalnie niechcianych aplikacji (PUA)** | Pua może obejmować oprogramowanie reklamowe, pakiet oprogramowania, które oferuje instalację innego, niepodpisanego oprogramowania i oprogramowania do unikania płacenia podatków, które próbuje uniknąć funkcji zabezpieczeń. Mimo że pua niekoniecznie jest wirusem, złośliwym oprogramowaniem lub innym typem zagrożeń, pua może mieć wpływ na wydajność urządzenia.<br/><br/>Ochrona pua blokuje elementy, które są wykrywane jako pua. Ochronę pua można ustawić na jedno z następujących ustawień: <br/>- **Włączone** (to ustawienie jest domyślne), które blokuje elementy wykryte jako pua na urządzeniach. *Zalecamy włączenie ochrony pua.*<br/>- **Tryb inspekcji**, który nie wykonuje żadnych akcji w przypadku elementów wykrytych jako pua <br/>- **Wyłączone**, które nie wykrywa ani nie podejmuje akcji na elementach, które mogą być pua |
| **Skanowania**   |  |
| **Typ zaplanowanego skanowania** | Rozważ uruchomienie cotygodniowego skanowania antywirusowego na urządzeniach. Możesz wybrać jedną z następujących opcji typu skanowania: <br/>- **Narzędzie Quickscan** sprawdza lokalizacje, takie jak klucze rejestru i foldery uruchamiania, w których można zarejestrować złośliwe oprogramowanie, aby rozpocząć pracę z urządzeniem. *Zalecamy użycie opcji Quickscan.* <br/>- **Usługa Fullscan** sprawdza wszystkie pliki i foldery na urządzeniu <br/>- **Wyłączone** oznacza, że zaplanowane skanowanie nie będzie odbywać się. Użytkownicy nadal mogą uruchamiać skanowania na własnych urządzeniach. (Ogólnie rzecz biorąc, nie zalecamy wyłączania zaplanowanych skanów). <br/><br/> [Dowiedz się więcej o typach skanowania](../defender-endpoint/schedule-antivirus-scans.md). |
| **Dzień tygodnia na uruchomienie zaplanowanego skanowania** | Wybierz dzień, w którym będą uruchamiane regularne, cotygodniowe skanowanie antywirusowe. |
| **Godzina uruchomienia zaplanowanego skanowania** | Wybierz czas uruchamiania regularnie zaplanowanych skanowania antywirusowego do uruchomienia. |
| **Korzystanie z niskiej wydajności** | To ustawienie jest domyślnie wyłączone. *Zalecamy wyłączenie tego ustawienia.* Można jednak włączyć to ustawienie, aby ograniczyć pamięć urządzenia i zasoby używane podczas zaplanowanych skanowania. <br/><br/>**WAŻNE** Jeśli włączysz opcję **Użyj niskiej wydajności**, skonfiguruje ona następujące ustawienia dla Program antywirusowy Microsoft Defender: <br/>- Pliki archiwum nie są skanowane ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>— Skanowanie ma niski priorytet procesora CPU ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- W przypadku pominięcia pełnego skanowania antywirusowego nie zostanie uruchomione żadne skanowanie catch-up ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Jeśli szybkie skanowanie antywirusowe zostanie pominięte, nie zostanie uruchomione żadne skanowanie catch-up ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>— Zmniejsza średni współczynnik obciążenia procesora CPU podczas skanowania antywirusowego z 50% do 20% ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Środowisko użytkownika**   |  |
| **Zezwalanie użytkownikom na dostęp do aplikacji Zabezpieczenia Windows** | Włącz to ustawienie, aby umożliwić użytkownikom otwieranie aplikacji Zabezpieczenia Windows na swoich urządzeniach. Użytkownicy nie będą mogli zastąpić ustawień skonfigurowanych w Microsoft Defender dla Firm, ale w razie potrzeby będą mogli uruchomić szybkie skanowanie lub wyświetlić wykryte zagrożenia. |
| **Wykluczenia programu antywirusowego** | Wykluczenia to procesy, pliki lub foldery pomijane przez skanowanie Program antywirusowy Microsoft Defender. *Ogólnie rzecz biorąc, nie należy definiować wykluczeń.* Program antywirusowy Microsoft Defender obejmuje wiele automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania.<br/><br/>[Dowiedz się więcej na temat wykluczeń](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **Wykluczenia procesów** | Wykluczenia procesów uniemożliwiają skanowanie plików otwieranych przez określone procesy za pomocą Program antywirusowy Microsoft Defender. <br/><br/>[Dowiedz się więcej na temat wykluczeń procesów](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Wykluczenia rozszerzenia pliku** | Wykluczenia rozszerzeń plików uniemożliwiają skanowanie plików z określonymi rozszerzeniami za pomocą Program antywirusowy Microsoft Defender.<br/><br/>[Dowiedz się więcej na temat wykluczeń rozszerzeń plików](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Wykluczenia plików i folderów** | Wykluczenia plików i folderów uniemożliwiają skanowanie plików znajdujących się w określonych folderach za pomocą Program antywirusowy Microsoft Defender. <br/><br/>[Dowiedz się więcej o wykluczeniach plików i folderów](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Inne wstępnie skonfigurowane ustawienia w usłudze Defender dla Firm

Następujące ustawienia zabezpieczeń są wstępnie skonfigurowane w usłudze Defender dla Firm:

- Skanowanie dysków wymiennych jest włączone ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))
- Codzienne szybkie skanowanie nie ma wstępnie ustawionego czasu ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))
- Aktualizacje analizy zabezpieczeń są sprawdzane przed uruchomieniem skanowania antywirusowego ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))
- Kontrole analizy zabezpieczeń są wykonywane co cztery godziny ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>Ustawienia domyślne usługi Defender dla firm i Microsoft Endpoint Manager

W poniższej tabeli opisano ustawienia wstępnie skonfigurowane dla usługi Defender dla firm oraz sposób, w jaki te ustawienia odpowiadają temu, co można zobaczyć w Microsoft Endpoint Manager (lub Microsoft Intune). Jeśli używasz [uproszczonego procesu konfiguracji w usłudze Defender dla Firm](mdb-simplified-configuration.md) (wersja zapoznawcza), nie musisz edytować tych ustawień.

| Ustawienie  | Opis  |
|---------|---------|
| [Ochrona w chmurze](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Czasami nazywana ochroną dostarczaną przez chmurę lub usługą Microsoft Advanced Protection Service (MAPS), ochrona w chmurze współpracuje z Program antywirusowy Microsoft Defender i chmurą firmy Microsoft w celu identyfikowania nowych zagrożeń, czasami nawet przed wystąpieniem jednego urządzenia. Domyślnie opcja [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) jest włączona. <br/><br/>[Dowiedz się więcej o ochronie chmury](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Monitorowanie plików przychodzących i wychodzących](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | Aby monitorować pliki przychodzące i wychodzące, właściwość [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) jest ustawiona na monitorowanie wszystkich plików.         |
| [Skanowanie plików sieciowych](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Domyślnie [pozycja AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) nie jest włączona, a pliki sieciowe nie są skanowane. |
| [Skanowanie wiadomości e-mail](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Domyślnie [funkcja AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) nie jest włączona i wiadomości e-mail nie są skanowane. |
| [Liczba dni (0–90) do przechowywania złośliwego oprogramowania poddanej kwarantannie](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Domyślnie [ustawienie DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) jest ustawione na zero (0) dni. Artifacts, że w kwarantannie nie są usuwane automatycznie.  |
| [Zgoda na przesyłanie przykładów](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | Domyślnie [właściwość SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) jest ustawiona na automatyczne wysyłanie bezpiecznych próbek. Przykłady bezpiecznych przykładów obejmują `.bat`pliki , `.scr`, `.dll`i `.exe` , które nie zawierają danych osobowych (PII). Jeśli plik zawiera identyfikator PII, użytkownik otrzymuje żądanie zezwalania na kontynuowanie przesyłania przykładowego.<br/><br/>[Dowiedz się więcej na temat ochrony w chmurze i przykładowego przesyłania](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Skanowanie dysków wymiennych](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | Domyślnie [funkcja AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) jest skonfigurowana do skanowania dysków wymiennych, takich jak dyski USB na urządzeniach.<br/><br/>[Dowiedz się więcej o ustawieniach zasad ochrony przed złośliwym kodem](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Uruchamianie dziennego czasu szybkiego skanowania](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Domyślnie [wartość ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) jest ustawiona na 2:00.<br/><br/>[Dowiedz się więcej o ustawieniach skanowania](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Sprawdzanie dostępności aktualizacji podpisu przed uruchomieniem skanowania](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Domyślnie [funkcja CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) jest skonfigurowana do sprawdzania dostępności aktualizacji analizy zabezpieczeń przed uruchomieniem skanowania antywirusowego/chroniącego przed złośliwym kodem.<br/><br/>[Dowiedz się więcej o ustawieniach skanowania](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) i [aktualizacjach analizy zabezpieczeń](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Jak często (0–24 godziny) sprawdzać aktualizacje analizy zabezpieczeń](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | Domyślnie [funkcja SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) jest skonfigurowana do sprawdzania dostępności aktualizacji analizy zabezpieczeń co cztery godziny.<br/><br/>[Dowiedz się więcej o ustawieniach skanowania](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) i [aktualizacjach analizy zabezpieczeń](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Zobacz też

- [Odwiedź portal Microsoft 365 Defender](mdb-get-started.md)
- [Zarządzanie ustawieniami zapory w Microsoft Defender dla Firm](mdb-custom-rules-firewall.md)
- [Dostawca CSP zasad — Defender](/windows/client-management/mdm/policy-csp-defender)
