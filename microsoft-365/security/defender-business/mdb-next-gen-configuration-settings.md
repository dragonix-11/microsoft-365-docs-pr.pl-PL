---
title: Opis ustawień konfiguracji ochrony następnej generacji w programie Microsoft Defender dla firm
description: Opis ustawień konfiguracji ochrony następnej generacji w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a71ca8294660a98d13e72a3316b5512f1647f4f7
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450650"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>Opis ustawień konfiguracji następnej generacji w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Ochrona następnej generacji w programie Defender dla firm obejmuje niezawodność ochrony przed złośliwym oprogramowaniem i oprogramowaniem antywirusowym. Twoje domyślne zasady mają na celu ochronę Twoich urządzeń i użytkowników bez zakłócania produktywności. można jednak dostosować zasady do swoich potrzeb biznesowych. Jeśli korzystasz z usługi Microsoft Endpoint Manager, możesz użyć jej do zarządzania zasadami zabezpieczeń.

**W tym artykule opisano**:

- [Ustawienia i opcje ochrony następnej generacji](#next-generation-protection-settings-and-options)

- [Inne wstępnie skonfigurowane ustawienia w programie Defender dla firm](#other-preconfigured-settings-in-defender-for-business) 

- [Domyślne ustawienia i ustawienia usługi Defender dla firm Microsoft Endpoint Manager](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>Ustawienia i opcje ochrony następnej generacji

W poniższej tabeli wymieniono ustawienia i opcje:<br/><br/>

| Ustawienie | Opis |
|:---|:---|
| **Ochrona w czasie rzeczywistym**  |  |
| **Włączanie ochrony w czasie rzeczywistym** | Domyślnie włączona ochrona w czasie rzeczywistym znajduje i zatrzymuje uruchamianie złośliwego oprogramowania na urządzeniach. *Zalecamy zachowywanie włączonej ochrony w czasie rzeczywistym.*<br/><br/>Gdy jest włączona ochrona w czasie rzeczywistym, konfiguruje ona następujące ustawienia:<br/>- Monitorowanie zachowania jest włączone ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>— Wszystkie pobrane pliki i załączniki są skanowane ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>— Skrypty używane w przeglądarkach firmy Microsoft są skanowane ([AllowScript Scannning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **Blokuj na pierwszy rzut oka** | Domyślnie funkcja blokowania na pierwszy rzut oka blokuje złośliwe oprogramowanie w ciągu kilku sekund wykrywania, zwiększa czas przesyłania przykładowych plików do analizy (w sekundach), a także ustawia poziom wykrywania na Wysoki. *Zalecamy zachowywanie włączonego blokowania na pierwszy rzut oka.*<br/><br/>Po włączeniu blokowania na pierwszy rzut oka konfiguruje on następujące ustawienia dla następujących Program antywirusowy Microsoft Defender: <br/>- Blokowanie i skanowanie podejrzanych plików jest ustawione na wysoki poziom blokowania ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>— Liczba sekund blokowania i sprawdzenia pliku to 50 sekund ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**WAŻNE**: Zablokowanie na pierwszy rzut oka jest wyłączone, ma to wpływ `CloudBlockLevel` na `CloudExtendedTimeout` Program antywirusowy Microsoft Defender.  |
| **Włączanie ochrony sieci** | Po włączeniu ochrona sieci pomaga chronić przed wyłudzaniem informacji, witrynami typu exploit-hosting oraz złośliwą zawartością w Internecie. Ponadto zapobiega wyłączeniu ochrony sieci przez użytkowników.<br/><br/>Ochronę sieci można ustawić na jeden z następujących trybów:<br/>- **Tryb blokowania** (to ustawienie jest ustawieniem domyślnym), który uniemożliwia użytkownikom odwiedzanie witryn uznanych za niebezpieczne. *Zalecamy, aby ochrona sieci była ustawiona na tryb blokowania.*<br/>- **Tryb inspekcji**, który umożliwia użytkownikom odwiedzanie witryn, które mogą być niebezpieczne, oraz śledzenie aktywności sieciowej w takich witrynach <br/>- **Tryb wyłączony**, który blokuje użytkownikom odwiedzanie witryn, które mogą być niebezpieczne, ani śledzenie aktywności sieciowej z takich witryn |
| **Działania naprawcze**  |  |
| **Działanie w celu podjęcia działań w związku z potencjalnie niechcianymi aplikacjami (PUA)** | Pakiet PUA może zawierać oprogramowanie reklamowe, oprogramowanie do instalowania innych, niepodpisanych oprogramowania i oprogramowania, które próbuje omijać funkcje zabezpieczeń. Mimo że oprogramowanie pua nie może być oprogramowaniem antywirusowym, złośliwym oprogramowaniem ani innymi zagrożeniami, może to wpłynąć na wydajność urządzenia.<br/><br/>Ochrona pua blokuje elementy wykrywane jako obiekt pua. Ochronę przed kodem PUA można ustawić na jedno z następujących ustawień: <br/>- **Włączone** (to ustawienie jest ustawieniem domyślnym), które blokuje elementy wykryte jako tryb PUA na urządzeniach. *Zalecamy, aby włączyć ochronę przed pua.*<br/>- **Tryb inspekcji**, w którym nie są podejmuje żadnych działań na elementach wykrytych jako obiekt pua <br/>- **Wyłączona**, która nie wykrywa ani nie podejmie działań na elementach, które mogą być w stanie pua |
| **Skanowanie**   |  |
| **Typ skanowania według harmonogramu** | Rozważ uruchomienie cotygodniowego skanowania antywirusowego na urządzeniach. Dostępne są następujące opcje typu skanowania: <br/>- **Quickkan** sprawdza lokalizacje, takie jak klucze rejestru i foldery uruchamiania, w których można zarejestrować złośliwe oprogramowanie, aby uruchomić urządzenie. *Zalecamy użycie opcji quickkan.* <br/>- **Fullkan** sprawdza wszystkie pliki i foldery na urządzeniu <br/>- **Wyłączone** oznacza, że nie będą odbywać się żadne zaplanowane skanowania. Użytkownicy nadal mogą uruchamiać skany na swoich urządzeniach. (Na ogół nie zalecamy wyłączania zaplanowanych skanów). <br/><br/> [Dowiedz się więcej o typach skanowania](../defender-endpoint/schedule-antivirus-scans.md). |
| **Dzień tygodnia do uruchomienia zaplanowanego skanowania** | Wybierz dzień, w który mają być uruchamiane zwykłe, cotygodniowe skanowania antywirusowe. |
| **Godzina uruchomienia zaplanowanego skanowania** | Wybierz czas uruchamiania regularnie planowanych skanów antywirusowych do uruchomienia. |
| **Stosowanie niskiej wydajności** | To ustawienie jest domyślnie wyłączone. *Zalecamy, aby to ustawienie było wyłączone.* Możesz jednak włączyć to ustawienie, aby ograniczyć ilość pamięci urządzenia i zasobów używanych podczas zaplanowanych skanów. <br/><br/>**WAŻNE** Jeśli **włączysz pozycję Użyj niskiej** wydajności, skonfiguruje ona następujące ustawienia Program antywirusowy Microsoft Defender: <br/>- Pliki archiwum nie są skanowane ([AllowArchive Scannning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>— skanom jest przypisywany niski priorytet procesora ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Jeśli nie zostanie nieodebrane pełne skanowanie antywirusowe, nie zostanie uruchomione żadne skanowanie w trybie pochwytujące ([DisableCatchupFullKan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Jeśli nie zostanie nieodebrane szybkie skanowanie antywirusowe, nie zostanie uruchomione żadne skanowanie w trybie catch-up ([DisableCatchupQuickKan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- Zmniejsza średni współczynnik obciążenia procesora podczas skanowania antywirusowego z 50% do 20% ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Środowisko użytkownika**   |  |
| **Zezwalaj użytkownikom na dostęp do Zabezpieczenia Windows aplikacji** | Włącz to ustawienie, aby umożliwić użytkownikom otwieranie aplikacji Zabezpieczenia Windows na ich urządzeniach. Użytkownicy nie będą mogli zastępować ustawień skonfigurowanych w programie Microsoft Defender dla firm, ale w razie potrzeby mogą szybko przeglądać lub wyświetlać wykryte zagrożenia. |
| **Wykluczenia dotyczące oprogramowania antywirusowego** | Wykluczenia to procesy, pliki lub foldery, które są pomijane przez Program antywirusowy Microsoft Defender skanowania. *Ogólnie nie należy definiować wykluczeń.* Program antywirusowy Microsoft Defender uwzględnia wiele automatycznych wykluczeń, które są oparte na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania.<br/><br/>[Dowiedz się więcej o wykluczeniach](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **Wykluczenia procesu** | Wykluczenia procesu uniemożliwiają skanowanie plików otwieranych przez określone procesy przez Program antywirusowy Microsoft Defender. <br/><br/>[Dowiedz się więcej o wykluczeniach procesów](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Wykluczenia rozszerzeń plików** | Wykluczenia rozszerzeń plików uniemożliwiają skanowanie plików z określonymi rozszerzeniami przez Program antywirusowy Microsoft Defender.<br/><br/>[Dowiedz się więcej o wykluczeniach rozszerzeń plików](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Wykluczenia plików i folderów** | Wykluczenia plików i folderów uniemożliwiają skanowanie plików w określonych folderach przez Program antywirusowy Microsoft Defender. <br/><br/>[Dowiedz się więcej o wykluczeniach plików i folderów](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Inne wstępnie skonfigurowane ustawienia w programie Defender dla firm

Następujące ustawienia zabezpieczeń są wstępnie skonfigurowane w programie Defender dla firm:

- Jest włączone skanowanie dysków wymiennych ([AllowFull ScannRemovableDriveŚwietlanie](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))

- Codzienne szybkie skanowania nie mają wstępnie ustawionego czasu ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))

- Aktualizacje analizy zabezpieczeń są sprawdzane przed rozpoczęciem skanowania antywirusowego ([CheckForSignaturesBeforeRunningKanning)](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan)

- Testy analizy zabezpieczeń są przeprowadzane co cztery godziny ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>Domyślne ustawienia i ustawienia usługi Defender dla firm Microsoft Endpoint Manager

W poniższej tabeli opisano ustawienia wstępnie skonfigurowane dla usługi Defender dla firm oraz sposób, w jaki te ustawienia odpowiadają tym, co można zobaczyć w programie Microsoft Endpoint Manager (lub Microsoft Intune). Jeśli korzystasz z uproszczonego [procesu](mdb-simplified-configuration.md) konfiguracji w programie Defender dla firm (wersja Preview), nie musisz edytować tych ustawień.
<br/><br/>

| Ustawienie  | Opis  |
|---------|---------|
| [Ochrona chmury](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Czasami, określane jako ochrona w chmurze lub usługa MICROSOFT Advanced Protection Service (MAPS), ochrona w chmurze współpracuje z programem Program antywirusowy Microsoft Defender i chmurą firmy Microsoft w celu identyfikowania nowych zagrożeń, czasami nawet zanim zostanie wpływane na jedno urządzenie. Domyślnie opcja [AllowCloudProtection jest](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) włączona. <br/><br/>[Dowiedz się więcej o ochronie chmury](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Monitorowanie plików przychodzących i wychodzących](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | Aby monitorować pliki przychodzące i wychodzące, [dla pliku RealTimeKanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) jest ustawione monitorowanie wszystkich plików.         |
| [Skanowanie plików sieciowych](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Domyślnie ustawienie [AllowKanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) nie jest włączone, a pliki sieciowe nie są skanowane. |
| [Skanowanie wiadomości e-mail](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Domyślnie [AllowEmailKanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) nie jest włączony i wiadomości e-mail nie są skanowane. |
| [Liczba dni (0–90) na utrzymanie pod kwarantanną złośliwego oprogramowania](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Domyślnie wartość [ustawienia DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) jest równa zero (0) dni. Artifacts, które są poddawane kwarantannie, nie są usuwane automatycznie.  |
| [Przesyłanie zgody na próbki](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | Domyślnie [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) is et to send safe samples automatically. Przykładami bezpiecznych próbek `.bat`są : , `.scr``.dll`i pliki`.exe`, które nie zawierają danych umożliwiających identyfikację użytkownika (PII). Jeśli plik zawiera identyfikatory PII, użytkownik otrzymuje żądanie umożliwienia kontynuowania przykładowego żądania przesłania.<br/><br/>[Dowiedz się więcej o ochronie chmury i przykładowym przesyłaniem](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Skanowanie dysków wymiennych](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | Domyślnie [AllowFull ScannRemovableDriveŚwietlanie](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) jest skonfigurowane do skanowania dysków wymiennych, takich jak dyski USB usb na urządzeniach.<br/><br/>[Dowiedz się więcej o ustawieniach zasad ochrony przed złośliwym oprogramowaniem](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Uruchom dzienny czas szybkiego skanowania](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Domyślnie ustawienie [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) jest ustawione na wartość 2:00 AM.<br/><br/>[Dowiedz się więcej o ustawieniach skanowania](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Sprawdzanie aktualizacji podpisów przed uruchomieniem skanowania](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Domyślnie narzędzie [CheckForSignaturesBeforeRunningKanning Może](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) być skonfigurowane do sprawdzania aktualizacji analizy zabezpieczeń przed uruchomieniem skanów oprogramowania antywirusowego/ochrony przed złośliwym kodem.<br/><br/>[Dowiedz się więcej o ustawieniach skanowania i](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [aktualizacjach analizy zabezpieczeń](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Jak często (od 0 do 24 godzin) sprawdzane są aktualizacje analizy zabezpieczeń](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | Domyślnie [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) jest skonfigurowany do sprawdzania aktualizacji analizy zabezpieczeń co cztery godziny.<br/><br/>[Dowiedz się więcej o ustawieniach skanowania i](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [aktualizacjach analizy zabezpieczeń](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Zobacz też

- [Odwiedź Microsoft 365 Defender witryny](mdb-get-started.md)

- [Zarządzanie ustawieniami zapory w programie Microsoft Defender dla firm](mdb-custom-rules-firewall.md)

- [CSP zasad — Defender](/windows/client-management/mdm/policy-csp-defender)