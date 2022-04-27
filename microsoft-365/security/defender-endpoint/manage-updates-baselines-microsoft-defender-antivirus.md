---
title: Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych
description: Zarządzanie sposobem, w jaki Program antywirusowy Microsoft Defender odbiera ochronę i aktualizacje produktów.
keywords: updates, security baselines, protection, schedule updates, force updates, mobile updates, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 6822f736cae73d7d4654f8b4310e0e397cffa677
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077480"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych

> [!IMPORTANT]
> Klienci, którzy zastosowali aktualizację aparatu microsoft defender z marca 2022 r **. (1.1.19100.5**), mogli napotkać wysokie wykorzystanie zasobów (procesor CPU i/lub pamięć). Firma Microsoft wydała aktualizację (**1.1.19200.5**), która rozwiązuje błędy wprowadzone we wcześniejszej wersji. Zaleca się, aby klienci zaktualizowali tę nową kompilację aparatu antywirusowego (**1.1.19200.5**). Aby upewnić się, że wszystkie problemy z wydajnością są w pełni rozwiązane, zaleca się ponowne uruchomienie maszyn po zastosowaniu aktualizacji. Zobacz [Miesięczne wersje platformy i aparatu](#monthly-platform-and-engine-versions) (w tym artykule).

**Dotyczy:**
- [plany Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Aktualizowanie Program antywirusowy Microsoft Defender ma kluczowe znaczenie dla zapewnienia, że urządzenia mają najnowszą technologię i funkcje potrzebne do ochrony przed nowym złośliwym oprogramowaniem i technikami ataku. Pamiętaj, aby zaktualizować ochronę antywirusową, nawet jeśli Program antywirusowy Microsoft Defender działa w [trybie pasywnym](microsoft-defender-antivirus-compatibility.md). Istnieją dwa typy aktualizacji związane z aktualizowaniem Program antywirusowy Microsoft Defender:

- [Aktualizacje analizy zabezpieczeń](#security-intelligence-updates)
- [Aktualizacje produktów](#product-updates)

> [!TIP]
> Aby wyświetlić najbardziej aktualny aparat, platformę i datę podpisu, odwiedź [stronę Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innych programów chroniących przed złośliwym kodem firmy Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Aktualizacje analizy zabezpieczeń

Program antywirusowy Microsoft Defender korzysta z [ochrony dostarczanej w chmurze](cloud-protection-microsoft-defender-antivirus.md) (nazywanej również usługą Microsoft Advanced Protection Lub MAPS) i okresowo pobiera aktualizacje dynamicznej analizy zabezpieczeń w celu zapewnienia dodatkowej ochrony. Te aktualizacje dynamiczne nie są umieszczane w regularnych aktualizacjach analizy zabezpieczeń za pośrednictwem aktualizacji analizy zabezpieczeń KB2267602.

> [!NOTE]
> Aktualizacje są wydawane w następujących kb/s:
> - Program antywirusowy Microsoft Defender: KB2267602
> - System Center Endpoint Protection: KB2461484

Ochrona dostarczana w chmurze jest zawsze włączona i wymaga aktywnego połączenia z Internetem, aby działało. Aktualizacje analizy zabezpieczeń są wykonywane w zaplanowanym okresie (konfigurowalnym za pośrednictwem zasad). Aby uzyskać więcej informacji, zobacz [Korzystanie z ochrony firmy Microsoft w chmurze w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

Aby uzyskać listę najnowszych aktualizacji analizy zabezpieczeń, zobacz [Security intelligence updates for Program antywirusowy Microsoft Defender and other Microsoft antimalware (Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innych programów chroniących przed złośliwym kodem firmy Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates)).

Aktualizacje aparatu są dołączane do aktualizacji analizy zabezpieczeń i są wydawane co miesiąc.

## <a name="product-updates"></a>Aktualizacje produktów

Program antywirusowy Microsoft Defender wymaga [aktualizacji miesięcznych (KB4052623)](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) *znanych jako aktualizacje platformy*.

Dystrybucją aktualizacji można zarządzać za pomocą jednej z następujących metod:

- [Windows Server Update Service (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- Zwykle używana metoda wdrażania firmy Microsoft i Windows aktualizacji do punktów końcowych w sieci.

Aby uzyskać więcej informacji, zobacz [Zarządzanie źródłami aktualizacji Program antywirusowy Microsoft Defender ochrony](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Aktualizacje miesięczne są wydawane w fazach, co powoduje, że wiele pakietów jest widocznych w [usługach Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).
> - Ten artykuł zawiera listę zmian uwzględnionych w szerokim kanale wydań. [Zobacz najnowszą wersję szerokiego kanału tutaj](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Aby dowiedzieć się więcej na temat procesu stopniowego wdrażania i wyświetlić więcej informacji na temat następnej wersji, zobacz [Zarządzanie procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender](manage-gradual-rollout.md).
> - Aby dowiedzieć się więcej na temat aktualizacji analizy zabezpieczeń, zobacz [Security intelligence updates for Program antywirusowy Microsoft Defender and other Microsoft antimalware (Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innych programów chroniących przed złośliwym kodem firmy Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates)).
> - Jeśli szukasz listy procesów usługi Microsoft Defender, **[pobierz skoroszyt mde-urls](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)**, a następnie wybierz arkusz **Procesy usługi Microsoft Defender** . Skoroszyt mde-urls zawiera również listę usług i skojarzonych z nimi adresów URL, z którymi sieć musi być w stanie nawiązać połączenie, zgodnie z opisem w temacie [Enable access to Ochrona punktu końcowego w usłudze Microsoft Defender service URLLs in the proxy server (Włączanie dostępu do adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender na serwerze proxy](configure-proxy-internet.md)).

## <a name="monthly-platform-and-engine-versions"></a>Miesięczne wersje platformy i aparatu

Aby uzyskać informacje na temat aktualizowania lub instalowania aktualizacji platformy, zobacz [Update for Windows Defender antimalware platform (Aktualizacja dla platformy ochrony przed złośliwym kodem](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform)).

Wszystkie nasze aktualizacje zawierają

- Ulepszenia wydajności
- Ulepszenia obsługi
- Ulepszenia integracji (chmura, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>*AKTUALIZACJA* z marca 2022 r. (platforma: 4.18.2203.5 | Silnik: 1.1.19200.5)</summary>

*Klienci, którzy zastosowali aktualizację aparatu microsoft defender z marca 2022 r **. (1.1.19100.5**), mogli napotkać wysokie wykorzystanie zasobów (procesor CPU i/lub pamięć). Firma Microsoft wydała aktualizację (**1.1.19200.5**), która rozwiązuje błędy wprowadzone we wcześniejszej wersji. Zaleca się, aby klienci zaktualizowali tę nową kompilację aparatu antywirusowego (**1.1.19200.5**). Aby upewnić się, że wszystkie problemy z wydajnością są w pełni rozwiązane, zaleca się ponowne uruchomienie maszyn po zastosowaniu aktualizacji.*

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.363.817.0**<br/>
&ensp;Data wydania: **22 kwietnia 2022 r**.<br/>
&ensp;Platforma: **4.18.2203.5**<br/>
&ensp;Silnik: **1.1.19200.5**<br/>
&ensp;Faza pomocy technicznej: **Aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.19200.5 <br/>
Wersja aktualizacji analizy zabezpieczeń: 1.363.817.0<br/>

### <a name="whats-new"></a>Co nowego

- Rozwiązuje problemy z wysokim wykorzystaniem zasobów (procesorem CPU i/lub pamięcią) związane z wcześniejszą aktualizacją aparatu usługi Microsoft Defender z marca 2022 r. (1.1.19100.5)

### <a name="known-issues"></a>Znane problemy

Brak znanych problemów

<br/><br/>
</details><details>
<summary>Marzec-2022 (Platforma: 4.18.2203.5 | Silnik: 1.1.19100.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.361.1449.0**<br/>
&ensp;Data wydania: **7 kwietnia 2022 r**.<br/>
&ensp;Platforma: **4.18.2203.5**<br/>
&ensp;Silnik: **1.1.19100.5**<br/>
&ensp;Faza pomocy technicznej: **Aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.19100.5 <br/>
Wersja aktualizacji analizy zabezpieczeń: 1.361.1449.0<br/>

### <a name="whats-new"></a>Co nowego

- Dodano poprawkę [dla reguły zmniejszania obszaru ataków](attack-surface-reduction.md), która zablokowała dodatek Outlook 
- Dodano poprawkę dotyczącą problemu z [wydajnością monitorowania zachowania](configure-protection-features-microsoft-defender-antivirus.md) związanego z krótkimi procesami na żywo 
- Dodano poprawkę wykluczenia [amsi](/windows/win32/amsi/antimalware-scan-interface-portal) 
- Ulepszone możliwości [ochrony przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md) 
- Dodano poprawkę dotyczącą wyłączania [ochrony w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md) w niektórych przypadkach podczas korzystania z `SharedSignaturesPath` konfiguracji (Aby uzyskać więcej informacji o parametrze `SharedSignaturesPath` , zobacz [Set-MpPreference](/powershell/module/defender/set-mppreference))

### <a name="known-issues"></a>Znane problemy

Brak znanych problemów

<br/><br/>
</details><details>
<summary>Luty-2022 r. (platforma: 4.18.2202.4 | Silnik: 1.1.19000.8)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.361.14.0**<br/>
&ensp;Data wydania: **14 marca 2022 r**.<br/>
&ensp;Platforma: **4.18.2202.4**<br/>
&ensp;Silnik: **1.1.19000.8**<br/>
&ensp;Faza pomocy technicznej: **Aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.19000.8 <br/>
Wersja aktualizacji analizy zabezpieczeń: 1.361.14.0 <br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenia logiki monitorowania wykrywania i zachowania
- Naprawiono wykrywanie redukcji obszaru ataków wyzwalające fałszywie dodatnie
- Dodano poprawkę zapewniającą lepszą wierność alertów wykrywania EDR i zaawansowanego wyszukiwania zagrożeń
- Usługa Defender nie obsługuje już powiadomień niestandardowych w wyskakujących oknach podręcznych. Zmodyfikowano obiekt zasad grupy/Intune/SCCM i dokumentację, aby odzwierciedlić tę zmianę.
- Ulepszenia przechwytywania zarówno informacji, jak i kopii plików zapisywanych w magazynie wymiennym. Aby dowiedzieć się więcej, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender Device Control Removable Storage Access Control, wymienny nośnik magazynu](device-control-removable-storage-access-control.md).
- Ulepszone dane wyjściowe ruchu, gdy usługa SmartScreen jest nieosiągalna 
- Ulepszenia łączności dla klientów korzystających z serwerów proxy z wymaganiami dotyczącymi uwierzytelniania
- Naprawiono usterkę aktualizacji urządzenia VDI dla sieciowych akcji plików 
- EDR w trybie bloku obsługuje teraz szczegółowe określanie wartości docelowej urządzeń przy użyciu nowych dostawców CSP. Zobacz [Wykrywanie i reagowanie na punkty końcowe (EDR) w trybie bloku](edr-in-block-mode.md).

### <a name="known-issues"></a>Znane problemy

Brak znanych problemów

<br/><br/>
</details><details>
<summary>Styczeń-2022 r. (platforma: 4.18.2201.10 | Silnik: 1.1.18900.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.357.8.0**<br/>
&ensp;Data wydania: **9 lutego 2022 r**.<br/>
&ensp;Platforma: **4.18.2201.10**<br/>
&ensp;Silnik: **1.1.18900.2**<br/>
&ensp;Faza pomocy technicznej: **Aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.18900.2 <br/>
Wersja aktualizacji analizy zabezpieczeń: 1.357.8.0 <br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenia monitorowania zachowania w wydajności filtrowania
- Wzmacnianie zabezpieczeń na platformie TrustedInstaller
- Ulepszenia ochrony przed naruszeniami
- Zastąpione `ScanScheduleTime` nowym `ScanScheduleOffest` poleceniem cmdlet w [poleceniu Set-MpPreference](/powershell/module/defender/set-mppreference). Te zasady konfigurują liczbę minut po północy w celu przeprowadzenia zaplanowanego skanowania.
- `-ServiceHealthReportInterval` Dodano ustawienie [Set-MpPreference](/powershell/module/defender/set-mppreference). Te zasady konfigurują interwał czasu (w minutach) w celu przeprowadzenia zaplanowanego skanowania.
- `AllowSwitchToAsyncInspection` Dodano ustawienie [Set-MpPreference](/powershell/module/defender/set-mppreference). Te zasady umożliwiają optymalizację wydajności, która umożliwia synchronicznie kontrolowane przepływy sieciowe, przełączenie się do inspekcji asynchronicznej po sprawdzeniu i zweryfikowaniu.
- Analizator wydajności aktualizacje wersji 2: dodano zdalną obsługę programu PowerShell i programu PowerShell 7.x. Zobacz [Analizator wydajności, aby uzyskać Program antywirusowy Microsoft Defender](tune-performance-defender-antivirus.md).
- Usunięto potencjalne usterki zduplikowanych pakietów w sterowniku systemu inspekcji sieci Program antywirusowy Microsoft Defender.

### <a name="known-issues"></a>Znane problemy

Brak znanych problemów

<br/><br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Poprzednie aktualizacje wersji: tylko obsługa uaktualnień technicznych

Po wydaniu nowej wersji pakietu obsługa dwóch poprzednich wersji jest ograniczona tylko do pomocy technicznej. Wersje starsze niż wymienione w tej sekcji i są udostępniane tylko do obsługi uaktualnień technicznych.<br/><br/>

<details>
<summary>Listopad-2021 (Platforma: 4.18.2111.5 | Silnik: 1.1.18800.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.355.2.0**<br/>
&ensp;Data wydania: **9 grudnia 2021 r**.<br/>
&ensp;Platforma: **4.18.2111.5**<br/>
&ensp;Silnik: **1.1.18800.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

Wersja aparatu: 1.1.18800.4 Wersja aktualizacji analizy zabezpieczeń: 1.355.2.0

### <a name="whats-new"></a>Co nowego

- Zwiększona wydajność użycia procesora CPU w przypadku niektórych intensywnych scenariuszy na serwerach Exchange
- Dodano nowe pola stanu sterowania urządzeniami w obszarze Get-MpComputerStatus w module programu PowerShell usługi Defender. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender Device Control Removable Storage Access Control](device-control-removable-storage-access-control.md) .
- Usunięto usterkę polegającą na tym, że `SharedSignatureRoot` nie można było usunąć wartości po ustawieniu przy użyciu programu PowerShell
- Usunięto usterkę polegającą na tym, że nie można było włączyć [ochrony przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md), mimo że Ochrona punktu końcowego w usłudze Microsoft Defender wskazuje, że ochrona przed naruszeniami została włączona
- Dodano obsługę i poprawki błędów do analizatora wydajności dla narzędzia Program antywirusowy Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Analizator wydajności dla Program antywirusowy Microsoft Defender](tune-performance-defender-antivirus.md).   
   - Dodano obsługę środowiska ISE programu PowerShell dla `New-MpPerformanceRecording`
   - Naprawiono błędy błędów dla `Get-MpPerformanceReport -TopFilesPerProcess`
   - Naprawiono wyciek sesji rejestrowania wydajności podczas korzystania z programu `New-MpPerformanceRecording` PowerShell 7.x, sesji zdalnych i środowiska ISE programu PowerShell


### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Październik-2021 (Platforma: 4.18.2110.6 | Silnik: 1.1.18700.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.353.3.0**<br/>
&ensp;Data wydania: **28 października 2021 r**.<br/>
&ensp;Platforma: **4.18.2110.6**<br/>
&ensp;Silnik: **1.1.18700.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

Wersja aparatu: 1.1.18700.4 Wersja aktualizacji analizy zabezpieczeń: 1.353.3.0

### <a name="whats-new"></a>Co nowego

- Ulepszenia pokrycia ruchu sieciowego protokołu transferu plików (FTP)
- Poprawka umożliwiająca zmniejszenie użycia procesora CPU w usłudze Microsoft Defender w Exchange Server działających na Windows Server 2016
- Poprawka w przypadku przerw w skanowaniu
- Poprawka dotycząca alertów dotyczących zablokowanych prób naruszenia, które nie są wyświetlane w usłudze Security Center
- Ulepszenia odporności na naruszenia w usłudze Microsoft Defender

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Wrzesień 2021 r. (platforma: 4.18.2109.6 | Silnik: 1.1.18600.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.351.7.0**<br/>
&ensp;Data wydania: **7 października 2021 r**.<br/>
&ensp;Platforma: **4.18.2109.6**<br/>
&ensp;Silnik: **1.1.18600.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

Wersja aparatu: 1.1.18600.4 Wersja aktualizacji analizy zabezpieczeń: 1.351.7.0

### <a name="whats-new"></a>Co nowego
- Nowy pierścień opóźnienia dla aktualizacji aparatu Program antywirusowy Microsoft Defender i platformy. Urządzenia, które zdecydują się na ten pierścień, otrzymają aktualizacje z 48-godzinnym opóźnieniem. Nowy pierścień opóźnienia jest sugerowany tylko w środowiskach krytycznych. Zobacz [Zarządzanie procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender](manage-gradual-rollout.md).
- Ulepszenia procesu stopniowego wdrażania aktualizacji usługi Microsoft Defender

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Sierpień 2021 r. (platforma: 4.18.2108.7 | Silnik: 1.1.18500.10)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.349.22.0**<br/>
&ensp;Data wydania: **2 września 2021 r**.<br/>
&ensp;Platforma: **4.18.2108.7**<br/>
&ensp;Silnik: **1.1.18500.10**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Ulepszenia aparatu monitorowania zachowania
- Wydano nowy [analizator wydajności dla Program antywirusowy Microsoft Defender](tune-performance-defender-antivirus.md)
- Program antywirusowy Microsoft Defender wzmocnione przed ładowaniem złośliwych bibliotek DLL
- Program antywirusowy Microsoft Defender wzmocniona przed obejściem TrustedInstaller
- Rozszerzanie powiadomień o zmianie pliku w celu uwzględnienia większej ilości danych dla Human-Operated Ransomware (HumOR)

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Lipiec 2021 r. (platforma: 4.18.2107.4 | Silnik: 1.1.18400.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.345.13.0**<br/>
&ensp;Data wydania: **5 sierpnia 2021 r**.<br/>
&ensp;Platforma: **4.18.2107.4**<br/>
&ensp;Silnik: **1.1.18400.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Dodano obsługę sterowania urządzeniami przenośnymi Windows
- Ochrona potencjalnie niechcianych aplikacji (PUA) jest domyślnie włączona dla użytkowników (zobacz [Potencjalnie niechciane aplikacje będą domyślnie blokowane](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- Zaplanowane skanowania dla systemów zarządzanych zasady grupy Object będą zgodne z czasem skanowania skonfigurowanym przez użytkownika
- Ulepszenia aparatu monitorowania zachowania

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów

<br/>
</details><details>
<summary> Czerwiec 2021 (Platforma: 4.18.2106.5 | Silnik: 1.1.18300.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.343.17.0**<br/>
&ensp;Data wydania: **28 czerwca 2021 r**.<br/>
&ensp;Platforma: **4.18.2106.5**<br/>
&ensp;Silnik: **1.1.18300.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Nowe mechanizmy kontroli zarządzania procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender. Zobacz [Zarządzanie procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender](manage-gradual-rollout.md).
- Ulepszenie aparatu monitorowania zachowania
- Ulepszenia wprowadzania definicji oprogramowania chroniącego przed złośliwym kodem
- Rozszerzone inspekcje zdarzeń sieciowych usługi Edge

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Maj-2021 r. (platforma: 4.18.2105.4 | Silnik: 1.1.18200.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.341.8.0**<br/>
&ensp;Data wydania: **3 czerwca 2021 r**.<br/>
&ensp;Platforma: **4.18.2105.4**<br/>
&ensp;Silnik: **1.1.18200.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Ulepszenia [monitorowania zachowania](client-behavioral-blocking.md)
- Stała funkcja filtrowania powiadomień [ochrony sieci](network-protection.md)

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Kwiecień-2021 (Platforma: 4.18.2104.14 | Silnik: 1.1.18100.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.337.2.0**<br/>
&ensp;Wydano: **26 kwietnia 2021**  r. (silnik: 1.1.18100.6 wydany 5 maja 2021 r.)<br/>
&ensp;Platforma: **4.18.2104.14**<br/>
&ensp;Silnik: **1.1.18100.5**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Więcej logiki monitorowania zachowania
- Ulepszone wykrywanie rejestratora kluczy trybu jądra
- Dodano nowe kontrolki do zarządzania procesem stopniowego wdrażania [aktualizacji usługi Microsoft Defender](manage-gradual-rollout.md)


### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Marzec-2021 (Platforma: 4.18.2103.7 | Silnik: 1.1.18000.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.335.36.0**<br/>
&ensp;Data wydania: **2 kwietnia 2021 r**.<br/>
&ensp;Platforma: **4.18.2103.7**<br/>
&ensp;Silnik: **1.1.18000.5**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenie aparatu monitorowania zachowania
- Rozszerzone środki zaradcze ataków siłowych w sieci
- Więcej nieudanych prób naruszenia generowania zdarzeń po włączeniu [ochrony przed](prevent-changes-to-security-settings-with-tamper-protection.md) naruszeniami

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Luty-2021 r. (platforma: 4.18.2102.3 | Silnik: 1.1.17900.7)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.333.7.0**<br/>
&ensp;Data wydania: **9 marca 2021 r**.<br/>
&ensp;Platforma: **4.18.2102.3**<br/>
&ensp;Silnik: **1.1.17900.7**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszone odzyskiwanie usługi dzięki [ochronie przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md)
- Rozszerzanie zakresu ochrony przed naruszeniami

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Styczeń-2021 r. (platforma: 4.18.2101.9 | Silnik: 1.1.17800.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.327.1854.0**<br/>
&ensp;Data wydania: **2 lutego 2021 r**.<br/>
&ensp;Platforma: **4.18.2101.9**<br/>
&ensp;Silnik: **1.1.17800.5**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenia wykrywania luk w zabezpieczeniach programu Shellcode
- Zwiększona widoczność prób kradzieży poświadczeń
- Ulepszenia funkcji antytamperingu w usługach Program antywirusowy Microsoft Defender
- Ulepszona obsługa emulacji arm x64
- Poprawka: powiadomienie EDR Blokuj pozostaje w historii zagrożeń po początkowym wykryciu ochrony w czasie rzeczywistym

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Listopad-2020 r. (platforma: 4.18.2011.6 | Silnik: 1.1.17700.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.327.1854.0**<br/>
&ensp;Data wydania: **3 grudnia 2020 r**.<br/>
&ensp;Platforma: **4.18.2011.6**<br/>
&ensp;Silnik: **1.1.17700.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszone rejestrowanie stanu [filtru SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details><details>
<summary> Październik-2020 r. (platforma: 4.18.2010.7 | Silnik: 1.1.17600.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.327.7.0**<br/>
&ensp;Data wydania: **29 października 2020 r**.<br/>
&ensp;Platforma: **4.18.2010.7**<br/>
&ensp;Silnik: **1.1.17600.5**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Nowe opisy dla specjalnych kategorii zagrożeń
- Ulepszone możliwości emulacji
- Ulepszone możliwości zezwalania/blokowania adresów hostów
- Nowa opcja w programie Defender CSP do ignorowania scalania wykluczeń użytkowników lokalnych

### <a name="known-issues"></a>Znane problemy

Brak znanych problemów
<br/>
</details><details>
<summary> Wrzesień 2020 r. (platforma: 4.18.2009.7 | Silnik: 1.1.17500.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.325.10.0**<br/>
&ensp;Data wydania: **1 października 2020 r**.<br/>
&ensp;Platforma: **4.18.2009.7**<br/>
&ensp;Silnik: **1.1.17500.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Uprawnienia administratora są wymagane do przywracania plików w kwarantannie
- Zdarzenia w formacie XML są teraz obsługiwane
- Obsługa programu CSP w celu ignorowania scalania wykluczeń
- Nowe interfejsy zarządzania dla:
   - Inspekcja UDP
   - Ochrona sieci na serwerze 2019
   - Wykluczenia adresów IP dla ochrony sieci
- Lepszy wgląd w pomiary modułu TPM
- Ulepszone skanowanie modułów VBA Office

### <a name="known-issues"></a>Znane problemy

Brak znanych problemów
<br/>
</details>
<details>
<summary> Sierpień 2020 r. (platforma: 4.18.2008.9 | Silnik: 1.1.17400.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.323.9.0**<br/>
&ensp;Data wydania: **27 sierpnia 2020 r**.<br/>
&ensp;Platforma: **4.18.2008.9**<br/>
&ensp;Silnik: **1.1.17400.5**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Dodawanie większej liczby zdarzeń telemetrii
- Ulepszona telemetria zdarzeń skanowania
- Ulepszone monitorowanie zachowania skanowania pamięci
- Ulepszone skanowanie strumieni makr
- Dodano `AMRunningMode` polecenie cmdlet programu PowerShell do Get-MpComputerStatus
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) jest ignorowane. Program antywirusowy Microsoft Defender automatycznie wyłącza się po wykryciu innego programu antywirusowego.


### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details>

<details>
<summary> Lipiec 2020 r. (platforma: 4.18.2007.8 | Silnik: 1.1.17300.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.321.30.0**<br/>
&ensp;Data wydania: **28 lipca 2020 r**.<br/>
&ensp;Platforma: **4.18.2007.8**<br/>
&ensp;Silnik: **1.1.17300.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszona telemetria dla usługi BITS
- Ulepszona weryfikacja certyfikatu podpisywania kodu authenticode

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details>

<details>
<summary> Czerwiec 2020 r. (platforma: 4.18.2006.10 | Silnik: 1.1.17200.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.319.20.0**<br/>
&ensp;Data wydania: **22 czerwca 2020 r**.<br/>
&ensp;Platforma: **4.18.2006.10**<br/>
&ensp;Silnik: **1.1.17200.2**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Możliwość określenia [lokalizacji dzienników pomocy technicznej](./collect-diagnostic-data.md)
- Pomijanie agresywnego skanowania catchup w trybie pasywnym.
- Zezwalaj usłudze Defender na aktualizowanie połączeń taryfowych
- Naprawiono dostrajanie wydajności po wyłączeniu buforowania
- Naprawiono zapytanie rejestru
- Naprawiono randomizację czasu skanowania w programie ADMX

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details>

<details>
<summary> Maj-2020 r. (platforma: 4.18.2005.4 | Silnik: 1.1.17100.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.317.20.0**<br/>
&ensp;Data wydania: **26 maja 2020 r**.<br/>
&ensp;Platforma: **4.18.2005.4**<br/>
&ensp;Silnik: **1.1.17100.2**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszone rejestrowanie zdarzeń skanowania
- Ulepszona obsługa awarii trybu użytkownika.
- Dodano śledzenie zdarzeń w celu ochrony przed naruszeniami
- Naprawiono przesyłanie przykładów amsi
- Naprawiono blokowanie chmury AMSI
- Naprawiono dziennik instalacji aktualizacji zabezpieczeń

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details>

<details>
<summary> Kwiecień-2020 r. (platforma: 4.18.2004.6 | Silnik: 1.1.17000.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.315.12.0**<br/>
&ensp;Data wydania: **30 kwietnia 2020 r**.<br/>
&ensp;Platforma: **4.18.2004.6**<br/>
&ensp;Silnik: **1.1.17000.2**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Ulepszenia filtru WDfilter
- Dodawanie większej ilości danych zdarzeń z możliwością działania w celu zdarzeń wykrywania zmniejszania obszaru podatnego na ataki
- Naprawiono informacje o wersji w danych diagnostycznych i usłudze WMI
- Naprawiono nieprawidłową wersję platformy w interfejsie użytkownika po aktualizacji platformy
- Dynamiczny adres URL intel do ochrony przed zagrożeniami bez plików
- Funkcja skanowania UEFI
- Rozszerzanie rejestrowania dla aktualizacji

### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details>

<details>
<summary> Marzec 2020 r. (platforma: 4.18.2003.8 | Silnik: 1.1.16900.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.313.8.0**<br/>
&ensp;Data wydania: **24 marca 2020 r**.<br/>
&ensp;Platforma: **4.18.2003.8**<br/>
&ensp;Silnik: **1.1.16900.4**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Opcja ograniczania przepustowości procesora cpu dodana do [mpcmdrun](./command-line-arguments-microsoft-defender-antivirus.md)
- Ulepszanie możliwości diagnostycznych
- zmniejszenie limitu czasu analizy zabezpieczeń (5 minut)
- Rozszerzanie funkcji dziennika wewnętrznego aparatu AMSI
- Ulepszanie powiadomień dotyczących blokowania procesów

### <a name="known-issues"></a>Znane problemy
[**Naprawiono**] Program antywirusowy Microsoft Defender pomija pliki podczas skanowania.

<br/>
</details>

<details>

<summary> Luty-2020 (Platforma: - | Silnik: 1.1.16800.2)</summary>


&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.311.4.0**<br/>
&ensp;Data wydania: **25 lutego 2020 r**.<br/>
&ensp;Platforma/klient: **-**<br/>
&ensp;Silnik: **1.1.16800.2**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego


### <a name="known-issues"></a>Znane problemy
Brak znanych problemów
<br/>
</details>

<details>
<summary> Styczeń-2020 r. (platforma: 4.18.2001.10 | Silnik: 1.1.16700.2)</summary>


Wersja aktualizacji analizy zabezpieczeń: **1.309.32.0**<br/>
Data wydania: **30 stycznia 2020 r**.<br/>
Platforma/klient: **4.18.2001.10**<br/>
Silnik: **1.1.16700.2**<br/>
&ensp;Faza pomocy technicznej: **pomoc techniczna dotycząca uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Naprawiono BSOD w usłudze WS2016 z Exchange
- Aktualizacje platformy pomocy technicznej po przekierowaniu protokołu TMP do ścieżki sieciowej
- Wersje platformy i aparatu są dodawane do [usługi WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- rozszerzanie aktualizacji sygnatury [awaryjnej na tryb pasywny](./microsoft-defender-antivirus-compatibility.md)
- Naprawiono zawieszenie w wersji 4.18.1911.3

### <a name="known-issues"></a>Znane problemy

[**Naprawiono**] urządzenia korzystające z [nowoczesnego trybu wstrzymania](/windows-hardware/design/device-experiences/modern-standby) mogą napotkać zawieszenie ze sterownikiem filtru Windows Defender, co powoduje przerwę w ochronie.  Maszyny, których dotyczy problem, wydają się być wyświetlane klientowi jako nie zaktualizowane do najnowszej platformy ochrony przed złośliwym kodem.
<br/>
> [!IMPORTANT]
> Ta aktualizacja jest następująca:
> - wymagane przez urządzenia RS1 z niższą wersją platformy do obsługi algorytmu SHA2;
> - ma flagę ponownego uruchomienia dla systemów, które mają problemy z zawieszaniem się;
> - zostanie ponownie wydany w kwietniu 2020 r. i nie zostanie zastąpiony przez nowsze aktualizacje, aby zachować przyszłą dostępność;
> - jest skategoryzowany jako aktualizacja ze względu na wymaganie ponownego uruchomienia; I
> - jest oferowany tylko z [Windows Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> Listopad-2019 r. (platforma: 4.18.1911.3 | Silnik: 1.1.16600.7)</summary>

Wersja aktualizacji analizy zabezpieczeń: **1.307.13.0**<br/>
Data wydania: **7 grudnia 2019 r**.<br/>
Platforma: **4.18.1911.3**<br/>
Silnik: **1.1.17000.7**<br/>
Faza pomocy technicznej: **Brak pomocy technicznej**<br/>

### <a name="whats-new"></a>Co nowego

- Naprawiono poziom śledzenia MpCmdRun
- Naprawiono informacje o wersji narzędzia WDFilter
- Ulepszanie powiadomień (PUA)
- dodawanie dzienników MRT do obsługi plików

### <a name="known-issues"></a>Znane problemy
Po zainstalowaniu tej aktualizacji urządzenie musi mieć pakiet jump 4.18.2001.10, aby można było zaktualizować go do najnowszej wersji platformy.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>obsługa platformy Program antywirusowy Microsoft Defender

Aktualizacje platformy i aparatu są udostępniane w comiesięcznym okresie. Aby zapewnić pełną obsługę, bądź na bieżąco z najnowszymi aktualizacjami platformy. Nasza struktura pomocy technicznej jest dynamiczna i zmienia się w dwie fazy w zależności od dostępności najnowszej wersji platformy:

- **Faza obsługi aktualizacji zabezpieczeń i aktualizacji krytycznych** — podczas uruchamiania najnowszej wersji platformy będziesz mieć uprawnienia do otrzymywania zarówno aktualizacji zabezpieczeń, jak i aktualizacji krytycznych dla platformy chroniącej przed złośliwym oprogramowaniem.

- **Faza pomocy technicznej (tylko)** — po wydaniu nowej wersji platformy obsługa starszych wersji (N-2) zostanie zredukowana tylko do pomocy technicznej. Wersje platformy starsze niż N-2 nie będą już obsługiwane.*

\*Pomoc techniczna będzie nadal zapewniana w przypadku uaktualnień z wersji Windows 10 wersji (zobacz [Wersja platformy dołączona do wersji Windows 10](#platform-version-included-with-windows-10-releases)) do najnowszej wersji platformy.

W fazie pomocy technicznej (tylko) uzasadnione pod względem handlowym zdarzenia pomocy technicznej będą udostępniane za pośrednictwem działu obsługi klienta firmy Microsoft & Pomocy technicznej i zarządzanych ofert pomocy technicznej firmy Microsoft (takich jak pomoc techniczna Premier). Jeśli zdarzenie pomocy technicznej wymaga eskalacji w celu uzyskania dalszych wskazówek, wymaga aktualizacji niezwiązanej z zabezpieczeniami lub wymaga aktualizacji zabezpieczeń, klienci zostaną poproszeni o uaktualnienie do najnowszej wersji platformy lub aktualizacji pośredniej (*).

> [!NOTE]
> Jeśli ręcznie wdrażasz usługę Program antywirusowy Microsoft Defender Platform Update lub używasz skryptu lub produktu zarządzania innej firmy niż Microsoft do wdrażania Program antywirusowy Microsoft Defender Aktualizacji platformy, upewnij się, że wersja `4.18.2001.10` jest zainstalowana z [wykazu usługi Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10)  przed zainstalowaniem najnowszej wersji aktualizacji platformy (N-2).

### <a name="platform-version-included-with-windows-10-releases"></a>Wersja platformy dołączona do wersji Windows 10

Poniższa tabela zawiera wersje Program antywirusowy Microsoft Defender platformy i aparatu dostarczane z najnowszymi wersjami Windows 10:<br/><br/>

|wersja Windows 10  |Wersja platformy  |Wersja aparatu |Faza pomocy technicznej |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Pomoc techniczna dotycząca uaktualniania (tylko) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Pomoc techniczna dotycząca uaktualniania (tylko) |

Aby uzyskać Windows 10 informacje o wersji, zobacz [arkusz informacyjny Windows cyklu życia](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Aktualizacje dotyczące obsługi i zarządzania obrazami wdrożenia (DISM)

Zalecamy zaktualizowanie Windows 10 (wersje Enterprise, Pro i Home), Windows Server 2019, Windows Server 2022 i Windows Server 2016 obrazów instalacyjnych systemu operacyjnego przy użyciu najnowszych aktualizacji oprogramowania antywirusowego i ochrony przed złośliwym kodem. Aktualizowanie obrazów instalacyjnych systemu operacyjnego pomaga uniknąć luki w ochronie.

Aby uzyskać więcej informacji, zobacz [Microsoft Defender update for Windows operating system installation images (Aktualizacja usługi Microsoft Defender dla obrazów instalacyjnych systemu operacyjnego Windows](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)).

<details>
<summary>20220321.1</summary>

&ensp;Wersja pakietu: **20220321.1**<br/>
&ensp;Wersja platformy: **4.18.2202.4**<br/>
&ensp;Wersja aparatu: **1.1.19000.8**<br/>
&ensp;Wersja podpisu: **1.351.337.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak

<br/>
</details><details>
<summary>20220305.1</summary>

&ensp;Wersja pakietu: **20220305.1**<br/>
&ensp;Wersja platformy: **4.18.2201.10**<br/>
&ensp;Wersja aparatu: **1.1.18900.3**<br/>
&ensp;Wersja podpisu: **1.359.1405.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak

<br/>
</details><details>
<summary>20220203.1</summary>

&ensp;Wersja pakietu: **20220203.1**<br/>
&ensp;Wersja platformy: **4.18.2111.5**<br/>
&ensp;Wersja aparatu: **1.1.18900.2**<br/>
&ensp;Wersja podpisu: **1.357.32.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>20220105.1</summary>

&ensp;Wersja pakietu: **20220105.1**<br/>
&ensp;Wersja platformy: **4.18.2111.5**<br/>
&ensp;Wersja aparatu: **1.1.18800.4**<br/>
&ensp;Wersja podpisu: **1.355.1482.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2112.01</summary>

&ensp;Wersja pakietu: **1.1.2112.01**<br/>
&ensp;Wersja platformy: **4.18.2110.6**<br/>
&ensp;Wersja aparatu: **1.1.18700.4**<br/>
&ensp;Wersja podpisu: **1.353.2283.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2111.02</summary>

&ensp;Wersja pakietu: **1.1.2111.02**<br/>
&ensp;Wersja platformy: **4.18.2110.6**<br/>
&ensp;Wersja aparatu: **1.1.18700.4**<br/>
&ensp;Wersja podpisu: **1.353.613.0**<br/>

### <a name="fixes"></a>Poprawki
- Rozwiązano problem związany z plikami lokalizacji

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2110.01</summary>

&ensp;Wersja pakietu: **1.1.2110.01**<br/>
&ensp;Wersja platformy: **4.18.2109.6**<br/>
&ensp;Wersja aparatu: **1.1.18500.10**<br/>
&ensp;Wersja podpisu: **1.349.2103.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2109.01</summary>

&ensp;Wersja pakietu: **1.1.2109.01**<br/>
&ensp;Wersja platformy: **4.18.2107.4**<br/>
&ensp;Wersja aparatu: **1.1.18400.5**<br/>
&ensp;Wersja podpisu: **1.347.891.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2108.01</summary>

&ensp;Wersja pakietu: **1.1.2108.01**<br/>
&ensp;Wersja platformy: **4.18.2107.4**<br/>
&ensp;Wersja aparatu: **1.1.18300.4**<br/>
&ensp;Wersja podpisu: **1.343.2244.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2107.02</summary>

&ensp;Wersja pakietu: **1.1.2107.02**<br/>
&ensp;Wersja platformy: **4.18.2105.5**<br/>
&ensp;Wersja aparatu: **1.1.18300.4**<br/>
&ensp;Wersja **podpisu: 1.343.658.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2106.01</summary>

&ensp;Wersja pakietu: **1.1.2106.01**<br/>
&ensp;Wersja platformy: **4.18.2104.14**<br/>
&ensp;Wersja aparatu: **1.1.18100.6**<br/>
&ensp;Wersja podpisu: **1.339.1923.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2105.01</summary>

&ensp;Wersja pakietu: **1.1.2105.01**<br/>
&ensp;Wersja platformy: **4.18.2103.7**<br/>
&ensp;Wersja aparatu: **1.1.18100.6**<br/>
&ensp;Wersja podpisu: **1.339.42.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2104.01</summary>

&ensp;Wersja pakietu: **1.1.2104.01**<br/>
&ensp;Wersja platformy: **4.18.2102.4**<br/>
&ensp;Wersja aparatu: **1.1.18000.5**<br/>
&ensp;Wersja podpisu: **1.335.232.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2103.01</summary>

&ensp;Wersja pakietu: **1.1.2103.01**<br/>
&ensp;Wersja platformy: **4.18.2101.9**<br/>
&ensp;Wersja aparatu: **1.1.17800.5**<br/>
&ensp;Wersja podpisu: **1.331.2302.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2102.03</summary>

&ensp;Wersja pakietu: **1.1.2102.03**<br/>
&ensp;Wersja platformy: **4.18.2011.6**<br/>
&ensp;Wersja aparatu: **1.1.17800.5**<br/>
&ensp;Wersja podpisu: **1.331.174.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2101.02</summary>

&ensp;Wersja pakietu: **1.1.2101.02**<br/>
&ensp;Wersja platformy: **4.18.2011.6**<br/>
&ensp;Wersja aparatu: **1.1.17700.4**<br/>
&ensp;Wersja podpisu: **1.329.1796.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2012.01</summary>

&ensp;Wersja pakietu: **1.1.2012.01**<br/>
&ensp;Wersja platformy: **4.18.2010.7**<br/>
&ensp;Wersja aparatu: **1.1.17600.5**<br/>
&ensp;Wersja podpisu: **1.327.1991.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2011.02</summary>

&ensp;Wersja pakietu: **1.1.2011.02**<br/>
&ensp;Wersja platformy: **4.18.2010.7**<br/>
&ensp;Wersja aparatu: **1.1.17600.5**<br/>
&ensp;Wersja podpisu: **1.327.658.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Odświeżone sygnatury Program antywirusowy Microsoft Defender
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Wersja pakietu: **1.1.2011.01**<br/>
&ensp;Wersja platformy: **4.18.2009.7**<br/>
&ensp;Wersja aparatu: **1.1.17600.5**<br/>
&ensp;Wersja podpisu: **1.327.344.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Brak
<br/>
</details><details>
<summary>1.1.2009.10</summary>

&ensp;Wersja pakietu: **1.1.2011.01**<br/>
&ensp;Wersja platformy: **4.18.2008.9**<br/>
&ensp;Wersja aparatu: **1.1.17400.5**<br/>
&ensp;Wersja podpisu: **1.327.2216.0**<br/>

### <a name="fixes"></a>Poprawki
- Brak

### <a name="additional-information"></a>Informacje dodatkowe
- Dodano obsługę obrazów instalacji systemu operacyjnego Windows 10 RS1 lub nowszych.
<br/>
</details>

## <a name="more-resources"></a>Więcej zasobów

| Artykułu | Opis  |
|:---|:---|
|[Aktualizacja usługi Microsoft Defender dla obrazów instalacji systemu operacyjnego Windows](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Przejrzyj pakiety aktualizacji oprogramowania chroniącego przed złośliwym kodem dla obrazów instalacyjnych systemu operacyjnego (pliki WIM i VHD). Pobieranie aktualizacji Program antywirusowy Microsoft Defender dla Windows 10 (wersje Enterprise, Pro i Home), Windows Server 2019, Windows Server 2022 i Windows Server 2016 obrazów instalacyjnych.  |
|[Zarządzanie sposobem pobierania i stosowania aktualizacji ochrony](manage-protection-updates-microsoft-defender-antivirus.md) | Aktualizacje ochrony mogą być dostarczane za pośrednictwem wielu źródeł. |
|[Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Możesz zaplanować, kiedy należy pobrać aktualizacje ochrony. |
|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Jeśli punkt końcowy przegapi aktualizację lub zaplanowane skanowanie, możesz wymusić aktualizację lub skanować przy następnym zalogowaniu się użytkownika. |
|[Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md) | Aktualizacje ochrony można ustawić do pobrania podczas uruchamiania lub po niektórych zdarzeniach ochrony dostarczanych przez chmurę. |
|[Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Można określić ustawienia, takie jak to, czy aktualizacje powinny być wykonywane w przypadku zasilania baterii, które są szczególnie przydatne w przypadku urządzeń przenośnych i maszyn wirtualnych. |
| [aktualizacja Ochrona punktu końcowego w usłudze Microsoft Defender czujnika EDR](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | Możesz zaktualizować czujnik EDR (MsSense.exe), który jest dołączony do nowego pakietu ujednoliconego rozwiązania Ochrona punktu końcowego w usłudze Microsoft Defender wydanego w 2021 roku.   |

> [!TIP]
> Jeśli szukasz powiązanych informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)
