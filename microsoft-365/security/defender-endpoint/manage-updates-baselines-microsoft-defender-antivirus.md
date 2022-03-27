---
title: Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego
description: Zarządzaj tym, Program antywirusowy Microsoft Defender, jak otrzymujesz ochronę i aktualizacje produktów.
keywords: aktualizacje, plany bazowe zabezpieczeń, ochrona, planowanie aktualizacji, wymuszanie aktualizacji, aktualizacje dla urządzeń przenośnych, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.date: 03/22/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: c334a3829d28ad7b65f0f0db3bd9599570db8337
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716195"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego

**Dotyczy:**
- [Microsoft Defender for Endpoint Plans 1 and 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Zapewnienie Program antywirusowy Microsoft Defender na bieżąco jest niezbędne do zapewnienia, że Twoje urządzenia mają najnowsze technologie i funkcje potrzebne do ochrony przed nowym złośliwym oprogramowaniem i technikami ataków. Pamiętaj, aby zaktualizować ochronę antywirusową, nawet Program antywirusowy Microsoft Defender działa w [trybie pasywnym](microsoft-defender-antivirus-compatibility.md). Istnieją dwa typy aktualizacji związanych z Program antywirusowy Microsoft Defender aktualnymi aktualizacjami:

- Aktualizacje analizy zabezpieczeń
- Aktualizacje produktów

> [!TIP]
> Aby wyświetlić najbardziej aktualny aparat, platformę i datę podpisu, odwiedź aktualizacje analizy zabezpieczeń dla oprogramowania Program antywirusowy Microsoft Defender i innego oprogramowania firmy [Microsoft w celu ochrony przed złośliwym kodem.](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Aktualizacje analizy zabezpieczeń

Program antywirusowy Microsoft Defender korzysta z ochrony [w](cloud-protection-microsoft-defender-antivirus.md) chmurze (nazywanej również usługą Microsoft Advanced Protection Service lub MAP) i okresowo pobiera aktualizacje dynamicznej analizy zabezpieczeń w celu zapewnienia dodatkowej ochrony. Te aktualizacje dynamiczne nie są miejscem regularnego aktualizowania analizy zabezpieczeń za pośrednictwem aktualizacji analizy zabezpieczeń KB2267602.

> [!NOTE]
> Aktualizacje są wydane w ramach następujących kb/kb:
> - Program antywirusowy Microsoft Defender: KB2267602
> - System Center Endpoint Protection: KB2461484

Ochrona w chmurze jest zawsze waktywna i wymaga aktywnego połączenia z Internetem. Aktualizacje analizy zabezpieczeń występują w zaplanowanym harmonogramie (konfigurowalnym za pośrednictwem zasad). Aby uzyskać więcej informacji, [zobacz Korzystanie z ochrony przed chmurą przez firmę Microsoft w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

Aby uzyskać listę najnowszych aktualizacji analizy zabezpieczeń, zobacz Aktualizacje analizy zabezpieczeń dla oprogramowania [Program antywirusowy Microsoft Defender i innego oprogramowania firmy Microsoft w celu ochrony przed złośliwym kodem](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Aktualizacje aparatów są uwzględniane w aktualizacjach analizy zabezpieczeń i są wydane z miesięcznego należytego dnia.

## <a name="product-updates"></a>Aktualizacje produktów

Program antywirusowy Microsoft Defender aktualizacji [miesięcznych (KB4052623),](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) nazywanych *aktualizacjami platformy*.

Rozkładem aktualizacji można zarządzać za pomocą jednej z następujących metod:

- [Windows Server Update Service (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- Zazwyczaj stosowana metoda wdrażania firmy Microsoft i Windows do punktów końcowych w sieci.

Aby uzyskać więcej informacji, zobacz [Zarządzanie źródłami dla nowych Program antywirusowy Microsoft Defender ochrony](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Comiesięczne aktualizacje są zwalniane etapami, co spowoduje, że wiele pakietów będzie widocznych w [usługach Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).
> - Ten artykuł zawiera listę zmian dostępnych w kanale szerokiego kanału wydawniowego. [Zobacz najnowszą wersję dla szerokiego kanału tutaj](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Aby dowiedzieć się więcej o stopniowym uaktualnieniu i uzyskać więcej informacji na temat następnej wersji, zobacz Zarządzanie procesem stopniowego wdrażanie aktualizacji programu [Microsoft Defender](manage-gradual-rollout.md).
> - Aby dowiedzieć się więcej o aktualizacjach analizy zabezpieczeń, zobacz Aktualizacje analizy zabezpieczeń dla oprogramowania [Program antywirusowy Microsoft Defender i inne rozwiązania firmy Microsoft zapobiegające złośliwym kodom](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Jeśli szukasz listy procesów programu Microsoft Defender, pobierz skoroszyt **[mde-urls](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)**, a następnie wybierz arkusz **Procesy programu Microsoft Defender** . Skoroszyt mde-urls zawiera również usługi i skojarzone z nimi adresy URL, z których sieć musi mieć możliwość nawiązania połączenia, zgodnie z opisem w artykule Włączanie dostępu do adresów [URL usługi Microsoft Defender for Endpoint](configure-proxy-internet.md) na serwerze proxy.

## <a name="monthly-platform-and-engine-versions"></a>Miesięczne wersje platform i aparatów

Aby uzyskać informacje o tym, jak zaktualizować lub zainstalować aktualizację platformy, zobacz Aktualizacja dla Windows Defender [ochrony przed złośliwym oprogramowaniem](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Wszystkie nasze aktualizacje zawierają

- Ulepszenia wydajności
- Ulepszenia dotyczące możliwości serwisowania
- Ulepszenia integracji (chmura, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Luty 2022 r. (platforma: 4.18.2202.4 | Aparat: 1.1.19000.8)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.361.14.0**<br/>
&ensp;Opublikowano: **14 marca 2022 r**.<br/>
&ensp;Platforma: **4.18.2202.4**<br/>
&ensp;Aparat: **1.1.19000.8**<br/>
&ensp;Etap pomocy technicznej: **aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.19000.8 <br/>
Wersja aktualizacji analizy zabezpieczeń: 1.361.14.0 <br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenia logiki monitorowania wykrywania i zachowania
- Usunięto wykrywanie zmniejszenia powierzchni ataków po efektach fałszywie dodatnich
- Dodano poprawkę, która lepszą wierność EDR oraz alerty wykrywania zaawansowanego wyszukiwania
- Program Defender nie obsługuje już niestandardowych powiadomień o wyskakujących wyskakujące okienkach. Zmodyfikowano zasady GPO/Intune/SCCM i dokumenty w celu odzwierciedlenia tej zmiany.
- Ulepszenia przechwytywania informacji i kopii plików zapisanych w pamięci wymiennych. Aby dowiedzieć się więcej, zobacz [Program Microsoft Defender for Endpoint Device Control Wymienny Storage Access Control, nośnik wymienny pamięci masowej](device-control-removable-storage-access-control.md).
- Poprawiony ruch wyjściowy, gdy nie można jeszcze wyostrzać usługi SmartScreen 
- Ulepszenia łączności dla klientów korzystających z serwerów proxy z wymaganiami uwierzytelniania
- Usunięto błąd aktualizacji urządzeń VDI dla sieci FileShares 
- EDR w trybie blokowania obsługuje teraz szczegółowe targetowanie urządzeń za pomocą nowych csP. Zobacz [Wykrywanie punktu końcowego i odpowiedź (EDR) w trybie blokowania](edr-in-block-mode.md).

### <a name="known-issues"></a>Znane problemy

Nie ma żadnych znanych problemów

<br/><br/>
</details><details>
<summary>Styczeń 2022 r. (platforma: 4.18.2201.10 | Aparat: 1.1.18900.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.357.8.0**<br/>
&ensp;Opublikowano: **9 lutego 2022 r**.<br/>
&ensp;Platforma: **4.18.2201.10**<br/>
&ensp;Aparat: **1.1.18900.2**<br/>
&ensp;Etap pomocy technicznej: **aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.18900.2 <br/>
Wersja aktualizacji analizy zabezpieczeń: 1.357.8.0 <br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenia monitorowania zachowania w wydajności filtrowania
- Przechowanie do trustedInstaller
- Ulepszenia dotyczące ochrony przed naruszeniami
- Zastąpiony `ScanScheduleTime` nowym poleceniem `ScanScheduleOffest` cmdlet w [Set-MpPreference](/powershell/module/defender/set-mppreference). Te zasady konfigurują liczbę minut po północy na wykonanie zaplanowanego skanowania.
- Dodano `-ServiceHealthReportInterval` ustawienie [Set-MpPreference](/powershell/module/defender/set-mppreference). Te zasady konfigurują interwał (w minutach) na wykonanie zaplanowanego skanowania.
- Dodano `AllowSwitchToAsyncInspection` ustawienie [Set-MpPreference](/powershell/module/defender/set-mppreference). Te zasady umożliwiają optymalizację wydajności, która umożliwia synchroniczne sprawdzanie przepływów sieciowych, przełączanie się do inspekcji synchronizacji po ich sprawdzeniu i sprawdzeniu.
- Aktualizacje w wersji 2 Analizatora wydajności: Dodano zdalną obsługę programu PowerShell i programu PowerShell 7.x. Zobacz [Analizator wydajności, aby uzyskać Program antywirusowy Microsoft Defender](tune-performance-defender-antivirus.md).
- Usunięto potencjalną usterkę zduplikowanych pakietów Program antywirusowy Microsoft Defender sterownika systemu inspekcji sieci.

### <a name="known-issues"></a>Znane problemy

Nie ma żadnych znanych problemów

<br/><br/>
</details><details>
<summary>Listopad-2021 (platforma: 4.18.2111.5 | Aparat: 1.1.18800.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.355.2.0**<br/>
&ensp;Opublikowano: **9 grudnia 2021 r**.<br/>
&ensp;Platforma: **4.18.2111.5**<br/>
&ensp;Aparat: **1.1.18800.4**<br/>
&ensp;Etap pomocy technicznej: **aktualizacje zabezpieczeń i krytyczne**<br/>

Wersja aparatu: 1.1.18800.4 Wersja aktualizacji zabezpieczeń: 1.355.2.0

### <a name="whats-new"></a>Co nowego

- Poprawiono wydajność użycia procesora w przypadku określonych scenariuszy intensywnie Exchange serwerach
- Dodano nowe pola stanu sterowania urządzeniami w Get-MpComputerStatus module Defender PowerShell. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint Device Control Removable Storage Access Control](device-control-removable-storage-access-control.md).
- Usunięto usterkę, w `SharedSignatureRoot` której nie można usunąć wartości ustawionej za pomocą programu PowerShell
- Usunięto usterkę, [w której nie](prevent-changes-to-security-settings-with-tamper-protection.md) można włączyć ochrony przed naruszeniami, mimo że usługa Microsoft Defender dla punktu końcowego wskazywała, że ochrona przed naruszeniami została włączona
- Dodano możliwości obsługi i poprawki błędów do Analizatora wydajności Program antywirusowy Microsoft Defender narzędzia. Aby uzyskać więcej informacji, zobacz [Analizator wydajności Program antywirusowy Microsoft Defender](tune-performance-defender-antivirus.md).   
   - Dodano obsługę isE programu PowerShell dla programu `New-MpPerformanceRecording`
   - Usunięto błędy błędów dla `Get-MpPerformanceReport -TopFilesPerProcess`
   - Usunięto wyciek sesji nagrywania wydajności podczas używania w `New-MpPerformanceRecording` programie PowerShell 7.x, sesjach zdalnych i programie PowerShell ISE


### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Poprzednie aktualizacje wersji: tylko pomoc techniczna w zakresie uaktualniania

Po zwolnieniu nowej wersji pakietu pomoc techniczna dla dwóch poprzednich wersji zostanie ograniczona tylko do pomocy technicznej. Wersje starsze niż wymienione w tej sekcji i są dostępne tylko dla pomocy technicznej przy uaktualnieniu.<br/><br/>

<details>
<summary> Październik-2021 (platforma: 4.18.2110.6 | Aparat: 1.1.18700.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.353.3.0**<br/>
&ensp;Opublikowano: **28 października 2021 r**.<br/>
&ensp;Platforma: **4.18.2110.6**<br/>
&ensp;Aparat: **1.1.18700.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

Wersja aparatu: 1.1.18700.4 Wersja aktualizacji analizy zabezpieczeń: 1.353.3.0

### <a name="whats-new"></a>Co nowego

- Ulepszenia dotyczące zakresu ruchu sieciowego protokołu TRANSFERU PLIKÓW (FTP)
- Poprawka zmniejszająca użycie procesora Microsoft Defender w Exchange Server działa na Windows Server 2016
- Rozwiązanie problemu z przerwami w skanowaniu
- Poprawka dla alertów dotyczących zablokowanych prób modyfikacji, które nie są wyświetlane w Centrum zabezpieczeń
- Ulepszenia dotyczące odporności na naruszenia w usłudze Microsoft Defender

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Wrzesień-2021 (platforma: 4.18.2109.6 | Aparat: 1.1.18600.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.351.7.0**<br/>
&ensp;Opublikowano: **7 października 2021 r**.<br/>
&ensp;Platforma: **4.18.2109.6**<br/>
&ensp;Aparat: **1.1.18600.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

Wersja aparatu: 1.1.18600.4 Wersja aktualizacji analizy zabezpieczeń: 1.351.7.0

### <a name="whats-new"></a>Co nowego
- Nowy pierścień opóźnień Program antywirusowy Microsoft Defender aktualizacji aparatu i platformy. Urządzenia, które zdecydują się na ten pierścień, będą otrzymywać aktualizacje z 48-godzinnym opóźnieniem. Nowy pierścień opóźnień jest sugerowany tylko dla środowisk o krytycznym znaczeniu. Zobacz [Zarządzanie procesem stopniowego wdrażanie aktualizacji programu Microsoft Defender](manage-gradual-rollout.md).
- Ulepszenia procesu stopniowego wdrażanie aktualizacji programu Microsoft Defender

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Sierpień 2021 r. (platforma: 4.18.2108.7 | Aparat: 1.1.18500.10)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.349.22.0**<br/>
&ensp;Opublikowano: **2 września 2021 r**.<br/>
&ensp;Platforma: **4.18.2108.7**<br/>
&ensp;Aparat: **1.1.18500.10**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Ulepszenia aparatu monitorowania zachowania
- Opublikowano nowego [analizatora wydajności dla Program antywirusowy Microsoft Defender](tune-performance-defender-antivirus.md)
- Program antywirusowy Microsoft Defender ładowania złośliwych bibliotek DLL
- Program antywirusowy Microsoft Defender się przed obejściem trustedInstaller
- Rozszerzanie powiadomień o zmianach plików w celu większej liczby danych dla oprogramowania Human-Operated Ransomware (Humor)

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Lipiec-2021 (platforma: 4.18.2107.4 | Aparat: 1.1.18400.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.345.13.0**<br/>
&ensp;Opublikowano: **5 sierpnia 2021 r**.<br/>
&ensp;Platforma: **4.18.2107.4**<br/>
&ensp;Aparat: **1.1.18400.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Dodano obsługę sterowania urządzeniami dla Windows przenośnych
- Ochrona przed potencjalnie niechcianymi aplikacjami jest domyślnie włączona dla klientów indywidualnych (zobacz Domyślnie są blokowane potencjalnie [niechciane aplikacje](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- Zaplanowane skany zasady grupy systemów zarządzanych obiektami będą przestrzegać skonfigurowanego przez użytkownika czasu skanowania
- Ulepszenia aparatu monitorowania zachowania

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów

<br/>
</details><details>
<summary> Czerwiec-2021 (platforma: 4.18.2106.5 | Aparat: 1.1.18300.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.343.17.0**<br/>
&ensp;Wydano: **28 czerwca 2021 r**.<br/>
&ensp;Platforma: **4.18.2106.5**<br/>
&ensp;Aparat: **1.1.18300.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Nowe kontrolki służące do zarządzania procesem stopniowego wdrażanie aktualizacji programu Microsoft Defender. Zobacz [Zarządzanie procesem stopniowego wdrażanie aktualizacji programu Microsoft Defender](manage-gradual-rollout.md).
- Ulepszenie aparatu monitorowania zachowania
- Ulepszenia dotyczące wycofywania definicji ochrony przed złośliwym oprogramowaniem
- Inspekcje zdarzeń sieci rozszerzonej krawędzi

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Maj-2021 (platforma: 4.18.2105.4 | Aparat: 1.1.18200.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.341.8.0**<br/>
&ensp;Opublikowano: **3 czerwca 2021 r**.<br/>
&ensp;Platforma: **4.18.2105.4**<br/>
&ensp;Aparat: **1.1.18200.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Ulepszenia monitorowania [zachowania](client-behavioral-blocking.md)
- Naprawiono [funkcję filtrowania powiadomień](network-protection.md) o ochronie sieci

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Kwiecień 2021 r. (platforma: 4.18.2104.14 | Aparat: 1.1.18100.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.337.2.0**<br/>
&ensp;Opublikowano: **26 kwietnia 2021**  r. (aparat: 1.1.18100.6 wydany 5 maja 2021 r.)<br/>
&ensp;Platforma: **4.18.2104.14**<br/>
&ensp;Aparat: **1.1.18100.5**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Więcej logiki monitorowania zachowania
- Ulepszono wykrywanie klucza trybu kernelowego
- Dodano nowe kontrolki do zarządzania procesem stopniowego wdrażanie aktualizacji [programu Microsoft Defender](manage-gradual-rollout.md)


### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Marzec 2021 r. (platforma: 4.18.2103.7 | Aparat: 1.1.18000.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.335.36.0**<br/>
&ensp;Opublikowano: **2 kwietnia 2021 r**.<br/>
&ensp;Platforma: **4.18.2103.7**<br/>
&ensp;Aparat: **1.1.18000.5**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenie aparatu monitorowania zachowania
- Środki zaradcze dla rozszerzonej sieci wymuszania ataków
- Więcej nieudanych prób naruszenia, gdy [jest włączona ochrona przed](prevent-changes-to-security-settings-with-tamper-protection.md) naruszeniami

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Luty 2021 r. (platforma: 4.18.2102.3 | Aparat: 1.1.17900.7)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.333.7.0**<br/>
&ensp;Opublikowano: **9 marca 2021 r**.<br/>
&ensp;Platforma: **4.18.2102.3**<br/>
&ensp;Aparat: **1.1.17900.7**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszone odzyskiwanie usługi dzięki ochronie [przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md)
- Rozszerzenie zakresu ochrony przed naruszeniami

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Styczeń 2021 r. (platforma: 4.18.2101.9 | Aparat: 1.1.17800.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.327.1854.0**<br/>
&ensp;Wydano: **2 lutego 2021 r**.<br/>
&ensp;Platforma: **4.18.2101.9**<br/>
&ensp;Aparat: **1.1.17800.5**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszenia wykrywania wykorzystania kodu powłoki
- Lepsza widoczność w przypadku prób kradzieży poświadczeń
- Ulepszenia funkcji ochrony przed sygnaturami w Program antywirusowy Microsoft Defender usługach
- Ulepszona obsługa emulacji ARM x64
- Poprawka: EDR powiadomienia o zablokowaniu pozostają w historii zagrożeń po wykonaniu początkowego wykrywania w ochronie w czasie rzeczywistym

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Listopad-2020 (platforma: 4.18.2011.6 | Aparat: 1.1.17700.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.327.1854.0**<br/>
&ensp;Opublikowano: **3 grudnia 2020 r**.<br/>
&ensp;Platforma: **4.18.2011.6**<br/>
&ensp;Aparat: **1.1.17700.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- [Ulepszona obsługa rejestrowania stanu filtru SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Październik-2020 (platforma: 4.18.2010.7 | Aparat: 1.1.17600.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.327.7.0**<br/>
&ensp;Opublikowano: **29 października 2020 r**.<br/>
&ensp;Platforma: **4.18.2010.7**<br/>
&ensp;Aparat: **1.1.17600.5**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Nowe opisy specjalnych kategorii zagrożeń
- Ulepszone możliwości emulacji
- Ulepszone możliwości zezwalania/blokowania adresów hosta
- Nowa opcja w programie Defender CSP na ignorowanie scalania wykluczeń użytkownika lokalnego

### <a name="known-issues"></a>Znane problemy

Nie ma żadnych znanych problemów
<br/>
</details><details>
<summary> Wrzesień-2020 (platforma: 4.18.2009.7 | Aparat: 1.1.17500.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.325.10.0**<br/>
&ensp;Opublikowano: **1 października 2020 r**.<br/>
&ensp;Platforma: **4.18.2009.7**<br/>
&ensp;Aparat: **1.1.17500.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Do przywracania plików w kwarantannie są wymagane uprawnienia administratora
- Obsługiwane są teraz zdarzenia w formacie XML
- Obsługa programu CSP ignorowania scaleń wykluczeń
- Nowe interfejsy zarządzania dla:
   - Inspekcja UDP
   - Ochrona sieci w serwerze 2019
   - Wykluczenia adresów IP w celu ochrony sieci
- Lepsza widoczność w pomiarach TPM
- Ulepszone Office modułu VBA

### <a name="known-issues"></a>Znane problemy

Nie ma żadnych znanych problemów
<br/>
</details>
<details>
<summary> Sierpień 2020 r. (platforma: 4.18.2008.9 | Aparat: 1.1.17400.5)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.323.9.0**<br/>
&ensp;Opublikowano: **27 sierpnia 2020 r**.<br/>
&ensp;Platforma: **4.18.2008.9**<br/>
&ensp;Aparat: **1.1.17400.5**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Dodawanie większej liczby zdarzeń telemetrycznych
- Ulepszona telemetria zdarzeń skanowania
- Ulepszone monitorowanie zachowania w skanach pamięci
- Ulepszone skanowanie strumieni makr
- Dodano `AMRunningMode` do Get-MpComputerStatus cmdlet programu PowerShell
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) jest ignorowana. Program antywirusowy Microsoft Defender automatycznie wyłącza się po wykryciu innego programu antywirusowego.


### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>

<details>
<summary> Lipiec–2020 (platforma: 4.18.2007.8 | Aparat: 1.1.17300.4)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.321.30.0**<br/>
&ensp;Opublikowano: **28 lipca 2020 r**.<br/>
&ensp;Platforma: **4.18.2007.8**<br/>
&ensp;Aparat: **1.1.17300.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszona telemetria dla usługi BITS
- Ulepszono sprawdzanie poprawności certyfikatu podpisywania kodu authenticode

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>

<details>
<summary> Czerwiec 2020 r. (platforma: 4.18.2006.10 | Aparat: 1.1.17200.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.319.20.0**<br/>
&ensp;Wydano: **22 czerwca 2020 r**.<br/>
&ensp;Platforma: **4.18.2006.10**<br/>
&ensp;Aparat: **1.1.17200.2**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Możliwość określenia [lokalizacji dzienników pomocy technicznej](./collect-diagnostic-data.md)
- Pomijanie agresywnego skanowania w trybie pasywnym.
- Zezwalaj u defenderowi na aktualizowanie połączeń taryfowej
- Poprawione dostosowywanie wydajności, gdy buforowanie jest wyłączone
- Poprawione zapytanie rejestru
- Naprawiono losowanie czasu skanowania w admx

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>

<details>
<summary> Maj-2020 (platforma: 4.18.2005.4 | Aparat: 1.1.17100.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.317.20.0**<br/>
&ensp;Opublikowano: **26 maja 2020 r**.<br/>
&ensp;Platforma: **4.18.2005.4**<br/>
&ensp;Aparat: **1.1.17100.2**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Ulepszona rejestrowanie zdarzeń skanowania
- Ulepszona obsługa awarii w trybie użytkownika.
- Dodano śledzenie zdarzeń w celu ochrony przed naruszeniami
- Poprawiono przesyłanie próbki AMSI
- Rozwiązano problem z blokowaniem chmury AMSI
- Dziennik instalacji naprawiliśmy aktualizację zabezpieczeń

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>

<details>
<summary> Kwiecień 2020 r. (platforma: 4.18.2004.6 | Aparat: 1.1.17000.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.315.12.0**<br/>
&ensp;Wydano: **30 kwietnia 2020 r**.<br/>
&ensp;Platforma: **4.18.2004.6**<br/>
&ensp;Aparat: **1.1.17000.2**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego
- Ulepszenia w filtrze WDfilter
- Dodaj więcej danych zdarzeń z akcjami, aby atakować zdarzenia wykrywania zmniejszenia powierzchni
- Naprawiono informacje o wersji w danych diagnostycznych i w aplikacji WMI
- Poprawiono niepoprawną wersję platformy w interfejsie użytkownika po aktualizacji platformy
- Dynamiczny adres URL firmy Intel do ochrony przed zagrożeniami bez plików
- Możliwości skanowania UEFI
- Rozszerzanie rejestrowania dla aktualizacji

### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>

<details>
<summary> Marzec 2020 r. (platforma: 4.18.2003.8 | Aparat: 1.1.16900.2)</summary>

&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.313.8.0**<br/>
&ensp;Opublikowano: **24 marca 2020 r**.<br/>
&ensp;Platforma: **4.18.2003.8**<br/>
&ensp;Aparat: **1.1.16900.4**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Opcja ograniczania procesora dodana do [mpCmdRun](./command-line-arguments-microsoft-defender-antivirus.md)
- Ulepszanie funkcji diagnostycznych
- zmniejszanie limitu czasu analizy zabezpieczeń (5 min)
- Rozszerzanie wewnętrznej funkcji dziennika aparatu AMSI
- Ulepszanie powiadomień o blokowaniu procesów

### <a name="known-issues"></a>Znane problemy
[**Naprawione**] Program antywirusowy Microsoft Defender pomija pliki podczas uruchamiania skanowania.

<br/>
</details>

<details>

<summary> Luty 2020 r. (platforma: — | Aparat: 1.1.16800.2)</summary>


&ensp;Wersja aktualizacji analizy zabezpieczeń: **1.311.4.0**<br/>
&ensp;Wydano: **25 lutego 2020 r**.<br/>
&ensp;Platforma/klient: **-**<br/>
&ensp;Aparat: **1.1.16800.2**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego


### <a name="known-issues"></a>Znane problemy
Nie ma żadnych znanych problemów
<br/>
</details>

<details>
<summary> Styczeń 2020 r. (platforma: 4.18.2001.10 | Aparat: 1.1.16700.2)</summary>


Wersja aktualizacji analizy zabezpieczeń: **1.309.32.0**<br/>
Wydano: **30 stycznia 2020 r**.<br/>
Platforma/klient: **4.18.2001.10**<br/>
Aparat: **1.1.16700.2**<br/>
&ensp;Etap pomocy technicznej: **pomoc techniczna w zakresie uaktualniania (tylko)**<br/>

### <a name="whats-new"></a>Co nowego

- Rozwiązano problem z BSOD w sieci WS2016 Exchange
- Aktualizacje platformy pomocy technicznej, gdy TMP jest przekierowywany do ścieżki sieciowej
- Wersje platformy i aparatu są dodawane do [systemu WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- rozszerzanie aktualizacji podpisu alarmowego na [tryb pasywny](./microsoft-defender-antivirus-compatibility.md)
- Poprawka 4.18.1911.3 zawiesza się

### <a name="known-issues"></a>Znane problemy

[**Naprawione**] urządzenia korzystające [z](/windows-hardware/design/device-experiences/modern-standby) nowoczesnego trybu gotowości mogą zawieszać się Windows Defender sterownika filtru, co powoduje przerwę w ochronie.  Klient wydaje się, że nie zaktualizował do najnowszej platformy ochrony przed złośliwym oprogramowaniem.
<br/>
> [!IMPORTANT]
> Ta aktualizacja jest:
> - wymagane przez urządzenia RS1 z niższą wersją platformy do obsługi SHA2;
> - ma flagę ponownego rozruchu dla systemów, które mają problemy z wysunięciem.
> - zostanie ponownie wydana w kwietniu 2020 r. i nie zostanie ona nowymi aktualizacjami, aby zachować ich dostępność w przyszłości.
> - jest skategoryzowana jako aktualizacja ze względu na wymaganie ponownego uruchomienia; i
> - jest oferowana tylko z [usługą Windows Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> Listopad-2019 (platforma: 4.18.1911.3 | Aparat: 1.1.16600.7)</summary>

Wersja aktualizacji analizy zabezpieczeń: **1.307.13.0**<br/>
Opublikowano: **7 grudnia 2019 r**.<br/>
Platforma: **4.18.1911.3**<br/>
Aparat: **1.1.17000.7**<br/>
Etap pomocy technicznej: **brak pomocy technicznej**<br/>

### <a name="whats-new"></a>Co nowego

- Poprawiono poziom śledzenia mpCmdRun
- Naprawione informacje o wersji filtru WDFilter
- Ulepszanie powiadomień (PUA)
- dodawanie dzienników MRT do plików pomocy technicznej

### <a name="known-issues"></a>Znane problemy
Po zainstalowaniu tej aktualizacji urządzenie potrzebuje pakietu jump 4.18.2001.10, aby móc zaktualizować go do najnowszej wersji na platformie.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>Program antywirusowy Microsoft Defender platformy

Aktualizacje platformy i aparatu są udostępniane z miesięczną aktualizacją. Aby być w pełni obsługiwanym, bądź na bieżąco z najnowszymi aktualizacjami platformy. Nasza struktura pomocy technicznej jest dynamiczna i rozwija się w dwóch fazach w zależności od dostępności najnowszej wersji platformy:

- **Faza obsługi aktualizacji zabezpieczeń** i aktualizacji krytycznych — podczas uruchamiania najnowszej wersji platformy będziesz kwalifikować się do otrzymywania aktualizacji zabezpieczeń i krytycznych dla platformy chroniącej przed złośliwym oprogramowaniem.

- **Etap pomocy technicznej (tylko)** — po zwolnieniu nowej wersji platformy obsługa starszych wersji (N-2) zostanie zmniejszona tylko do pomocy technicznej. Wersje platformy starsze niż N-2 nie będą już obsługiwane.*

\*Pomoc techniczna będzie nadal zapewniana w przypadku uaktualnień z wersji Windows 10 (zobacz Wersja platformy zawarta w Windows 10 wersjach[) do](#platform-version-included-with-windows-10-releases) najnowszej wersji platformy.

W okresie świadczenia pomocy technicznej (tylko) zdarzenia dotyczące pomocy technicznej uzasadnione komercyjnie będą udostępniane za pośrednictwem działu obsługi klienta firmy Microsoft & i zarządzanych ofert pomocy technicznej firmy Microsoft (takich jak pomoc techniczna Premier). Jeśli zdarzenie pomocy technicznej wymaga eskalacji do rozwoju w celu uzyskania dalszych wskazówek, wymaga aktualizacji niezwiązanej z zabezpieczeniami lub aktualizacji zabezpieczeń, klienci będą proszeni o uaktualnienie do najnowszej wersji platformy lub do aktualizacji pośredniej (*).

> [!NOTE]
> Jeśli wdrażasz ręcznie aktualizację platformy usługi Program antywirusowy Microsoft Defender lub jeśli do wdrożenia aktualizacji platformy firmy Program antywirusowy Microsoft Defender używasz skryptu lub produktu zarządzania firmy innego niż firma Microsoft, upewnij się, `4.18.2001.10` że ta wersja została zainstalowana z wykazu usługi [Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10).  zanim zostanie zainstalowana najnowsza wersja aktualizacji platformy (N-2).

### <a name="platform-version-included-with-windows-10-releases"></a>Wersja platformy dostępna w Windows 10 wersjach

W poniższej tabeli przedstawiono platformy Program antywirusowy Microsoft Defender wersje aparatów, które są dostarczane w najnowszych Windows 10 wersjach:<br/><br/>

|Windows 10 wersji  |Wersja platformy  |Wersja aparatu |Faza pomocy technicznej |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Pomoc techniczna w zakresie uaktualniania (tylko) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Pomoc techniczna w zakresie uaktualniania (tylko) |

Aby Windows 10 o wersji, zobacz Windows [arkusza informacji o cyklu życia firmy Microsoft](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Aktualizacje obsługi i zarządzania obrazami wdrażania (DISM)

Zalecamy zaktualizowanie obrazów instalacji systemu Windows 10 (wersje Enterprise, Pro i dla Użytkowników Domowych), Windows Server 2019, Windows Server 2022 i Windows Server 2016 OS za pomocą najnowszych aktualizacji antywirusowych i złośliwych. Utrzymywanie aktualnych obrazów instalacji systemu operacyjnego pomaga uniknąć przerwy w ochronie.

Aby uzyskać więcej informacji, zobacz [Aktualizacja programu Microsoft Defender w celu Windows obrazów instalacji systemu operacyjnego](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

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
- Rozwiązano problem dotyczący plików lokalizacji

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
&ensp;Wersja podpisu: **1.343.658.0**<br/>

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
- Odświeżone Program antywirusowy Microsoft Defender podpisy
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
- Dodano obsługę instalowania Windows 10 RS1 lub nowszego systemu operacyjnego.
<br/>
</details>

## <a name="more-resources"></a>Więcej zasobów

| Artykuł | Opis  |
|:---|:---|
|[Obrazy instalacji programu Microsoft Defender Windows systemu operacyjnego](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Przejrzyj pakiety aktualizacji ochrony przed złośliwym oprogramowaniem dla obrazów instalacji systemu operacyjnego (plików WIM i VHD). Uzyskiwanie Program antywirusowy Microsoft Defender aktualizacji dla Windows 10 (Enterprise, Pro i dla Użytkowników Domowych), Windows Server 2019, Windows Server 2022 oraz Windows Server 2016 obrazów instalacji.  |
|[Zarządzanie  pobraniem i zastosowaniem aktualizacji ochrony](manage-protection-updates-microsoft-defender-antivirus.md) | Aktualizacje ochrony mogą być dostarczane za pośrednictwem wielu źródeł. |
|[Zarządzanie tym, kiedy mają być pobierane i stosowane aktualizacje ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Możesz zaplanować, kiedy mają zostać pobrane aktualizacje ochrony. |
|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Jeśli punkt końcowy pominie aktualizację lub zaplanowane skanowanie, możesz wymusić aktualizację lub przeskanować, gdy użytkownik się następnym razem do nasyci. |
|[Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md) | Możesz ustawić aktualizacje ochrony, które mają być pobierane podczas uruchamiania lub po pewnych zdarzeniach ochrony w chmurze. |
|[Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Możesz określić ustawienia, takie jak to, czy aktualizacje powinny być ładowane na baterii, które są szczególnie przydatne w przypadku urządzeń przenośnych i maszyn wirtualnych. |
| [Aktualizacja punktu końcowego programu Microsoft Defender EDR czujnika ruchu](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | Możesz zaktualizować czujnik EDR (MsSense.exe) zawarty w nowym pakiecie rozwiązań ujednoliconego programu Microsoft Defender for Endpoint wydanym w 2021 r.   |
