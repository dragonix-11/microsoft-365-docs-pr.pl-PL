---
title: Program antywirusowy Microsoft Defender identyfikatorów zdarzeń i kodów błędów
description: Sprawdź przyczyny i rozwiązania problemów związanych z Program antywirusowy Microsoft Defender zdarzeniami i ich błędami
keywords: event, error code, siem, logging, troubleshooting, wef, windows event forwarding
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/27/2022
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: db4401e1215ab50e47425dee15a1337466e1e98a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014718"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Przejrzyj dzienniki zdarzeń i kody błędów, aby rozwiązać problemy z Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Jeśli wystąpi problem z Program antywirusowy Microsoft Defender, możesz przeszukać tabele w tym temacie, aby znaleźć pasujący problem i potencjalne rozwiązanie.

Lista tabel:

- [Program antywirusowy Microsoft Defender identyfikatorów zdarzeń](#windows-defender-av-ids) (dotyczą one Windows 10, Windows 11 i Windows Server 2016)
- [Program antywirusowy Microsoft Defender kodów błędów klienta](#error-codes)
- [Wewnętrzne Program antywirusowy Microsoft Defender błędów klienta (używane przez firmę Microsoft podczas opracowywania i testowania)](#internal-error-codes)

> [!TIP]
> Możesz również odwiedzić witrynę pokazu programu Microsoft Defender for Endpoint w witrynie [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) , aby sprawdzić, czy działają następujące funkcje:
>
> - Ochrona w chmurze
> - Szybkie uczenie się (w tym blokowanie od pierwszego rzutu)
> - Potencjalnie niechciane blokowanie aplikacji

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>Program antywirusowy Microsoft Defender identyfikatorów zdarzeń

Program antywirusowy Microsoft Defender identyfikatory zdarzeń w Windows zdarzeń.

Możesz bezpośrednio wyświetlić dziennik zdarzeń lub, jeśli masz narzędzie do zarządzania informacjami o zabezpieczeniach i zdarzeniami od innej firmy, możesz również użyć identyfikatorów zdarzeń klienta programu [Program antywirusowy Microsoft Defender](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) w celu przejrzenia określonych zdarzeń i błędów z punktów końcowych.

W tabeli w tej sekcji wymieniono główne identyfikatory zdarzeń Program antywirusowy Microsoft Defender oraz, o ile to możliwe, sugerowane rozwiązania problemu.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Aby wyświetlić Program antywirusowy Microsoft Defender zdarzenia

1. Otwórz **podgląd zdarzeń**.
2. W drzewie konsoli rozwiń **pozycję Dzienniki** aplikacji i usług, następnie pozycję **Microsoft**, a **następnie kliknij Windows** **i Windows Defender.**
3. Kliknij dwukrotnie **pozycję Operacyjne**.
4. W okienku szczegółów wyświetl listę poszczególnych zdarzeń, aby znaleźć zdarzenie.
5. Kliknij zdarzenie, aby wyświetlić szczegółowe informacje o zdarzeniu w dolnym okienku, na **kartach** **Ogólne** i Szczegóły.

<table>
<tr>
<th colspan="2" >Identyfikator zdarzenia: 1000</th>
</tr>
<tr>
<td>
Nazwa symboliczna:
</td>
<td>
<b>MALWAREPROTECTION_SCAN_STARTED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Rozpoczęto skanowanie w poszukiwaniu złośliwych kodów. </b>
</td>
</tr>
<tr>
<td >
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikacyjny odpowiedniego skanu.&gt;</dt>
<dt> Typ skanowania: &lt;typ skanowania&gt;, na przykład:<ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;parametry skanowania&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klientów</li>
</ul>
</dt>
<dt>Zasoby skanowania: &lt; Zeskanowane zasoby (takie jak pliki/katalogi/BHO).&gt;</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; Użytkownik&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1001</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_COMPLETED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Ukończono skanowanie w poszukiwaniu złośliwych kodów.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikacyjny odpowiedniego skanu.&gt;</dt>
<dt> Typ skanowania: &lt;typ skanowania&gt;, na przykład:<ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;parametry skanowania&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klientów</li>
</ul>
</dt>
<dt>Użytkownik: &lt; Domainlt&gt;\&; UserScan&gt;</dt> 
<dt>Time: &lt;Czas trwania skanowania.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1002</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_CANCELLED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu złośliwych kodów zostało zatrzymane przed jego zakończeniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikacyjny odpowiedniego skanu.&gt;</dt>
<dt> Typ skanowania: &lt;typ skanowania&gt;, na przykład:<ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;parametry skanowania&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klientów</li>
</ul>
</dt>
<dt>Użytkownik: &lt; Domainlt&gt;&amp;; UserScan&gt;</dt> 
<dt>Time: &lt;Czas trwania skanowania.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1003</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_PAUSED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu złośliwych kodów zostało wstrzymane. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikacyjny odpowiedniego skanu.&gt;</dt>
<dt> Typ skanowania: &lt;typ skanowania&gt;, na przykład:<ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;parametry skanowania&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klientów</li>
</ul>
</dt>
<dt>Użytkownik: &lt;Domainlt&gt;\&; Użytkownik&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1004</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_RESUMED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Wznowiono skanowanie w poszukiwaniu złośliwych kodów. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikacyjny odpowiedniego skanu.&gt;</dt>
<dt> Typ skanowania: &lt;typ skanowania&gt;, na przykład:<ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;parametry skanowania&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klientów</li>
</ul>
</dt>
<dt>Użytkownik: &lt;Domainlt&gt;\&; Użytkownik&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1005</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu złośliwych kodów nie powiodło się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikacyjny odpowiedniego skanu.&gt;</dt>
<dt> Typ skanowania: &lt;typ skanowania&gt;, na przykład:<ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;parametry skanowania&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klientów</li>
</ul>
</dt>
<dt>Użytkownik: &lt; Domainlt&gt;\&; Kod&gt;</dt> 
<dt>błędu użytkownika: Kod błędu &lt;&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Klient oprogramowania antywirusowego napotkał błąd i bieżące skanowanie zostało zatrzymane. Skanowanie może zakończyć się niepowodzeniem z powodu problemu po stronie klienta. Ten rekord zdarzenia zawiera identyfikator skanowania, typ skanowania (Program antywirusowy Microsoft Defender, ochrony przed złośliwym kodem, parametry skanowania, użytkownik, który uruchomił skanowanie, kod błędu i opis błędu.
Aby rozwiązać ten problem:
<ol>
<li>Uruchom ponownie skanowanie.</li>
<li>Jeśli błąd wystąpi w taki sam sposób, przejdź do witryny pomocy technicznej firmy <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a> i wprowadź numer błędu w <b></b> polu Wyszukaj, aby wyszukać kod błędu.</li>
<li>Skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Pomocą techniczną firmy Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1006</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_DETECTED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat chroniący przed złośliwym kodem znalazł złośliwe oprogramowanie lub inne potencjalnie niechciane oprogramowanie. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Pochodzenie pliku pathDetection&gt;</dt>
<dt>: Wykrywanie &lt;pochodzenia&gt;, na przykład:<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieciowy</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;Typ wykrywania&gt;, na przykład:<ul>
<li>Heuristics</li>
<li>Ogólne</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;Źródło wykrywania&gt; , na przykład:<ul>
<li>Użytkownik: inicjowany przez użytkownika</li>
<li>System: inicjowany system</li>
<li>W czasie rzeczywistym: inicjowany składnik w czasie rzeczywistym</li>
<li>IOAV: pobieranie i pobieranie w programie IE Outlook zainicjowanie załączników programu Express</li>
<li>NIS: system inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; zapewnia ochronę przed złośliwymi kontrolkami stron sieci Web</li>
<li>ELAM (Early Launch Antimalware). Dotyczy to złośliwego oprogramowania wykrytego przez sekwencję rozruchu</li>
<li>Zdalne poświadczenie</li>
</ul>Antimalware Scan Interface (AMSI). Głównie służy do ochrony skryptów (PowerShell, VBS), ale może być wywoływany również przez inne firmy.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; Nazwa&gt;</dt> 
<dt>przetwarzania użytkownika: &lt;Proces w wersji PIDSignature&gt;</dt>
<dt>: &lt;wersja definicjiAngine&gt;</dt> 
<dt>wersja: &lt;Antimalware Engine wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1007</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma chroniąca przed złośliwym kodem wykonała akcję mającą na celu ochronę systemu przed złośliwym oprogramowaniem lub innym potencjalnie niechcianym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender zostały podjęte działania w celu ochrony tego komputera przed złośliwym oprogramowaniem lub innym potencjalnie niechcianym oprogramowaniem. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Użytkownik: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt>
<dt> Akcja: &lt;na&gt; przykład:<ul>
<li>Oczyść: zasób został wyczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł wykonać/istnieje</li>
<li>Zdefiniowany przez użytkownika: akcja zdefiniowana przez użytkownika, która zwykle znajduje się na tej liście akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blok: Zasób został zablokowany do wykonania</li>
</ul>
</dt>
<dt>Stan: &lt; StanSignature&gt;</dt> 
<dt>Wersja: &lt;Wersja w definicjiJednoznakna&gt;</dt> 
<dt>wersja: Antimalware Engine &lt;wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1008</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma chroniąca przed złośliwym kodem próbowała wykonać akcję w celu ochrony systemu przed złośliwym oprogramowaniem lub innym potencjalnie niechcianym oprogramowaniem, ale działanie nie powiodło się.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas podejmowania działań na złośliwym oprogramowaniu lub innym potencjalnie niechcianym oprogramowaniu. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Użytkownik: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka plikuAction&gt;</dt>
<dt>: &lt;Na&gt; przykład akcja:<ul>
<li>Oczyść: zasób został wyczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł wykonać/istnieje</li>
<li>Zdefiniowany przez użytkownika: akcja zdefiniowana przez użytkownika, która zwykle znajduje się na tej liście akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blok: Zasób został zablokowany do wykonania</li>
</ul>
</dt>
<dt>Kod błędu: &lt; Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis błędu&gt; Opis błędu. </dt> 
<dt>Stan: &lt; StanSignature&gt;</dt> 
<dt>Wersja: &lt;Wersja w definicjiAngierzana&gt;</dt> 
<dt>wersja: &lt;Antimalware Engine wersja&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1009</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma zapobiegająca złośliwym oprogramowaniem przywróciła element z kwarantanny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender przywrócono element z kwarantanny. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka plikuUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1010</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platformy ochrony przed złośliwym oprogramowaniem nie można przywrócić elementu z kwarantanny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby przywrócenia elementu z kwarantanny. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka plikuUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; Kod&gt;</dt> 
<dt>błędu użytkownika: Kod błędu &lt;&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis błędu&gt; Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Wersja definicjaAngine&gt;</dt> 
<dt>wersja: Antimalware Engine &lt;wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1011</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma antyszybka usunęła element z kwarantanny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender usunięto element z kwarantanny.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka plikuUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1012</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma antyszybka nie mogła usunąć elementu z kwarantanny.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby usunięcia elementu z kwarantanny.
Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka plikuUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; Kod&gt;</dt> 
<dt>błędu użytkownika: Kod błędu &lt;&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis błędu&gt; Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Wersja definicjaAngine&gt;</dt> 
<dt>wersja: Antimalware Engine &lt;wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1013</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma chroniąca przed złośliwym kodem usunęła historię złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender usunięto historię złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
<dl>
<dt>Godzina: czas wystąpienia zdarzenia, na przykład gdy historia jest czyszczona. Ten parametr nie jest używany w przypadku zdarzeń zagrożeń, aby nie było żadnych wątpliwości co do tego, czy chodzi o czas rozwiązywania problemów, czy czas zagrożenia. W tym przypadku są to w szczególności czas akcji lub czas wykrywania.</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; Użytkownik&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1014</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
Na platformie chroniącej przed złośliwym kodem nie można usunąć historii złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas próby usunięcia historii złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
<dl>
<dt>Godzina: czas wystąpienia zdarzenia, na przykład gdy historia jest czyszczona. Ten parametr nie jest używany w przypadku zdarzeń zagrożeń, aby nie było żadnych wątpliwości co do tego, czy chodzi o czas rozwiązywania problemów, czy czas zagrożenia. W tym przypadku są to w szczególności czas akcji lub czas wykrywania.</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; Kod&gt;</dt> 
<dt>błędu użytkownika: Kod błędu &lt;&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1015</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_BEHAVIOR_DETECTED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma zapobiegająca złośliwym oprogramowaniem wykryła podejrzane zachowanie.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wykrył podejrzane zachowanie.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Pochodzenie pliku pathDetection&gt;</dt>
<dt>: Wykrywanie &lt;pochodzenia&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieciowy</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;Typ wykrywania&gt;, na przykład:<ul>
<li>Heuristics</li>
<li>Ogólne</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;Źródło wykrywania&gt; , na przykład:<ul>
<li>Użytkownik: inicjowany przez użytkownika</li>
<li>System: inicjowany system</li>
<li>W czasie rzeczywistym: inicjowany składnik w czasie rzeczywistym</li>
<li>IOAV: pobieranie i pobieranie w programie IE Outlook zainicjowanie załączników programu Express</li>
<li>NIS: system inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; zapewnia ochronę przed złośliwymi kontrolkami stron sieci Web</li>
<li>ELAM (Early Launch Antimalware). Dotyczy to złośliwego oprogramowania wykrytego przez sekwencję rozruchu</li>
<li>Zdalne poświadczenie</li>
</ul>Antimalware Scan Interface (AMSI). Głównie służy do ochrony skryptów (PowerShell, VBS), ale może być wywoływany również przez inne firmy.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>ID: Enumeration matching severity.</dt> 
<dt>Wersja podpisu: &lt; Wersja definicjiJednoszna&gt;</dt> 
<dt>wersja: &lt;Antimalware Engine Etykietafidelności&gt;</dt>
<dt>:</dt>Nazwa pliku docelowego
<dt>: &lt;&gt; Nazwa pliku.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1116</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_DETECTED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma chroniąca przed złośliwym oprogramowaniem wykryła złośliwe oprogramowanie lub inne potencjalnie niechciane oprogramowanie. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wykryło złośliwe oprogramowanie lub inne potencjalnie niechciane oprogramowanie.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Pochodzenie pliku pathDetection&gt;</dt>
<dt>: Wykrywanie &lt;pochodzenia&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieciowy</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;Typ wykrywania&gt;, na przykład:<ul>
<li>Heuristics</li>
<li>Ogólne</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;Źródło wykrywania&gt; , na przykład:<ul>
<li>Użytkownik: inicjowany przez użytkownika</li>
<li>System: inicjowany system</li>
<li>W czasie rzeczywistym: inicjowany składnik w czasie rzeczywistym</li>
<li>IOAV: pobieranie i pobieranie w programie IE Outlook zainicjowanie załączników programu Express</li>
<li>NIS: system inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; zapewnia ochronę przed złośliwymi kontrolkami stron sieci Web</li>
<li>ELAM (Early Launch Antimalware). Dotyczy to złośliwego oprogramowania wykrytego przez sekwencję rozruchu</li>
<li>Zdalne poświadczenie</li>
</ul>Antimalware Scan Interface (AMSI). Głównie służy do ochrony skryptów (PowerShell, VBS), ale może być wywoływany również przez inne firmy.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Nazwa&gt;</dt> 
<dt>przetwarzania użytkownika: &lt;proces w wersji PIDSignature&gt;</dt>
<dt>: &lt;wersja definicjiAngine&gt;</dt> 
<dt>wersja: &lt;Antimalware Engine wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie jest wymagane żadne działanie. Program antywirusowy Microsoft Defender zawiesić i podjąć rutynowe działania w związku z tym zagrożeniem. Jeśli chcesz ręcznie usunąć zagrożenie, w interfejsie Program antywirusowy Microsoft Defender kliknij pozycję <b>Oczyść komputer</b>.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1117</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma chroniąca przed złośliwym kodem wykonała akcję mającą na celu ochronę systemu przed złośliwym oprogramowaniem lub innym potencjalnie niechcianym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender zostały podjęte działania w celu ochrony tego komputera przed złośliwym oprogramowaniem lub innym potencjalnie niechcianym oprogramowaniem.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Pochodzenie pliku pathDetection&gt;</dt>
<dt>: Wykrywanie &lt;pochodzenia&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieciowy</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;Typ wykrywania&gt;, na przykład:<ul>
<li>Heuristics</li>
<li>Ogólne</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;Źródło wykrywania&gt; , na przykład:<ul>
<li>Użytkownik: inicjowany przez użytkownika</li>
<li>System: inicjowany system</li>
<li>W czasie rzeczywistym: inicjowany składnik w czasie rzeczywistym</li>
<li>IOAV: pobieranie i pobieranie w programie IE Outlook zainicjowanie załączników programu Express</li>
<li>NIS: system inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; zapewnia ochronę przed złośliwymi kontrolkami stron sieci Web</li>
<li>ELAM (Early Launch Antimalware). Dotyczy to złośliwego oprogramowania wykrytego przez sekwencję rozruchu</li>
<li>Zdalne poświadczenie</li>
</ul>Antimalware Scan Interface (AMSI). Głównie służy do ochrony skryptów (PowerShell, VBS), ale może być wywoływany również przez inne firmy.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Nazwaprocesu&gt;</dt> 
<dt>użytkownika: &lt;proces w akcji PID&gt;</dt>
<dt>:&lt;Akcja&gt;, na przykład:<ul>
<li>Oczyść: zasób został wyczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł wykonać/istnieje</li>
<li>Zdefiniowany przez użytkownika: akcja zdefiniowana przez użytkownika, która zwykle znajduje się na tej liście akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blok: Zasób został zablokowany do wykonania</li>
</ul>
</dt>
<dt>Stan akcji: &lt; Opis dodatkowych akcji Kod&gt;</dt> 
<dt>błędu: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Wersja definicjiJednoszna&gt;</dt> 
<dt>wersja: Antimalware Engine &lt;&gt;</dt> uwaga: Program antywirusowy Microsoft Defender, programu Microsoft Security Essentials, narzędzia do usuwania złośliwego oprogramowania lub System Center Endpoint Protection wykryje złośliwe oprogramowanie, przywróci następujące ustawienia systemowe i usługi, które mogły zostać zmienione przez złośliwe oprogramowanie:<ul>
<li>Domyślne ustawienie przeglądarki Internet Explorer Microsoft Edge inne</li>
<li>Ustawienia kontroli dostępu użytkownika</li>
<li>Ustawienia przeglądarki Chrome</li>
<li>Dane sterowania rozruchem</li>
<li>Ustawienia rejestru programu Regedit i Menedżera zadań</li>
<li>Windows, usługa inteligentnego transferu w tle i usługa zdalnego wywołania procedury</li>
<li>Windows plików systemu operacyjnego</li></ul>
Powyższy kontekst dotyczy następujących wersji klienta i serwera:
<table>
<tr>
<th>System operacyjny</th>
<th>Wersja systemu operacyjnego</th>
</tr>
<tr>
<td>
System operacyjny klienta
</td>
<td>
Windows Vista (z dodatkiem Service Pack 1 lub Service Pack 2) Windows 7 lub nowszym
</td>
</tr>
<tr>
<td>
System operacyjny serwera
</td>
<td>
Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 i Windows Server 2016
</td>
</tr>
</table>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie trzeba nic akcję. Program antywirusowy Microsoft Defender usunięto lub poddano kwarantannie zagrożenie.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1118</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma chroniąca przed złośliwym kodem próbowała wykonać akcję w celu ochrony systemu przed złośliwym oprogramowaniem lub innym potencjalnie niechcianym oprogramowaniem, ale działanie nie powiodło się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd, który nie jest krytyczny w przypadku podejmowania działań na złośliwym oprogramowaniu lub innym potencjalnie niechcianym oprogramowaniu.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Pochodzenie pliku pathDetection&gt;</dt>
<dt>: Wykrywanie &lt;pochodzenia&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieciowy</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;Typ wykrywania&gt;, na przykład:<ul>
<li>Heuristics</li>
<li>Ogólne</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;Źródło wykrywania&gt; , na przykład:<ul>
<li>Użytkownik: inicjowany przez użytkownika</li>
<li>System: inicjowany system</li>
<li>W czasie rzeczywistym: inicjowany składnik w czasie rzeczywistym</li>
<li>IOAV: pobieranie i pobieranie w programie IE Outlook zainicjowanie załączników programu Express</li>
<li>NIS: system inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; zapewnia ochronę przed złośliwymi kontrolkami stron sieci Web</li>
<li>ELAM (Early Launch Antimalware). Dotyczy to złośliwego oprogramowania wykrytego przez sekwencję rozruchu</li>
<li>Zdalne poświadczenie</li>
</ul>Antimalware Scan Interface (AMSI). Głównie służy do ochrony skryptów (PowerShell, VBS), ale może być wywoływany również przez inne firmy.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Nazwaprocesu&gt;</dt> 
<dt>użytkownika: &lt;proces w akcji PID&gt;</dt>
<dt>:&lt;Akcja&gt;, na przykład:<ul>
<li>Oczyść: zasób został wyczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł wykonać/istnieje</li>
<li>Zdefiniowany przez użytkownika: akcja zdefiniowana przez użytkownika, która zwykle znajduje się na tej liście akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blok: Zasób został zablokowany do wykonania</li>
</ul>
</dt>
<dt>Stan akcji: &lt; Opis dodatkowych akcji Kod&gt;</dt> 
<dt>błędu: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Wersja definicjaAngine&gt;</dt> 
<dt>wersja: Antimalware Engine &lt;wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie trzeba nic akcję. Program antywirusowy Microsoft Defender nie udało się wykonać zadania związanego z rozwiązywaniem problemów ze złośliwym oprogramowaniem. Nie jest to błąd krytyczny.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1119</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_CRITICALLY_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Podczas próby podjęcia działania na złośliwym oprogramowaniu lub innym potencjalnie niechcianym oprogramowaniu platforma chroniąca przed złośliwym kodem napotkała krytyczny błąd. Więcej szczegółów znajduje się w komunikacie o zdarzeniu.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd krytyczny podczas podejmowania działań na złośliwym oprogramowaniu lub innym potencjalnie niechcianym oprogramowaniu.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Identyfikator zagrożenia&gt;</dt>
<dt>: &lt;Identyfikator zagrożeniaSeverity&gt;</dt>
<dt>: &lt;Istotność&gt;, na przykład:<ul>
<li>Niska</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Poważny</li>
</ul>
</dt>
<dt>Kategoria: &lt; Opis kategorii&gt;, na przykład zagrożenia lub rodzaj złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Pochodzenie pliku pathDetection&gt;</dt>
<dt>: Wykrywanie &lt;pochodzenia&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieciowy</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;Typ wykrywania&gt;, na przykład:<ul>
<li>Heuristics</li>
<li>Ogólne</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;Źródło wykrywania&gt; , na przykład:<ul>
<li>Użytkownik: inicjowany przez użytkownika</li>
<li>System: inicjowany system</li>
<li>W czasie rzeczywistym: inicjowany składnik w czasie rzeczywistym</li>
<li>IOAV: pobieranie i pobieranie w programie IE Outlook zainicjowanie załączników programu Express</li>
<li>NIS: system inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; zapewnia ochronę przed złośliwymi kontrolkami stron sieci Web</li>
<li>ELAM (Early Launch Antimalware). Dotyczy to złośliwego oprogramowania wykrytego przez sekwencję rozruchu</li>
<li>Zdalne poświadczenie</li>
</ul>Antimalware Scan Interface (AMSI). Głównie służy do ochrony skryptów (PowerShell, VBS), ale może być wywoływany również przez inne firmy.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Nazwaprocesu&gt;</dt> 
<dt>użytkownika: &lt;proces w akcji PID&gt;</dt>
<dt>:&lt;Akcja&gt;, na przykład:<ul>
<li>Oczyść: zasób został wyczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł wykonać/istnieje</li>
<li>Zdefiniowany przez użytkownika: akcja zdefiniowana przez użytkownika, która zwykle znajduje się na tej liście akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blok: Zasób został zablokowany do wykonania</li>
</ul>
</dt>
<dt>Stan akcji: &lt; Opis dodatkowych akcji Kod&gt;</dt> 
<dt>błędu: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Wersja definicjaAngine&gt;</dt> 
<dt>wersja: Antimalware Engine &lt;wersji&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Klient Program antywirusowy Microsoft Defender napotkał ten błąd z powodu krytycznych problemów. Punkt końcowy może nie być chroniony. Zapoznaj się z opisem błędu, a następnie wykonaj odpowiednie <b>czynności czynności dla</b> użytkownika opisane poniżej.
<table>
<tr>
<th>Akcja</th>
<th>Akcja użytkownika</th>
</tr>
<tr>
<td>
<b>Usuń</b>
</td>
<td>
Zaktualizuj definicje, a następnie sprawdź, czy usuwanie się powiodło.
</td>
</tr>
<tr>
<td>
<b>Oczyść</b>
</td>
<td>
Zaktualizuj definicje, a następnie sprawdź, czy działania naprawcze się powiodło.
</td>
</tr>
<tr>
<td>
<b>Kwarantanna</b>
</td>
<td>
Zaktualizuj definicje i sprawdź, czy użytkownik ma uprawnienia dostępu do niezbędnych zasobów.
</td>
</tr>
<tr>
<td>
<b>Zezwalaj</b>
</td>
<td>
Sprawdź, czy użytkownik ma uprawnienia do uzyskiwania dostępu do niezbędnych zasobów.
</td>
</tr>
</table>

Jeśli to zdarzenie będzie nadal występowało:<ol>
<li>Uruchom ponownie skanowanie.</li>
<li>Jeśli błąd wystąpi w taki sam sposób, przejdź do witryny pomocy technicznej firmy <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a> i wprowadź numer błędu w <b></b> polu Wyszukaj, aby wyszukać kod błędu.</li>
<li>Skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Pomocą techniczną firmy Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1120</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_THREAT_HASH</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Program antywirusowy Microsoft Defender skróty dla zasobu zagrożeń.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender jest uruchomiony i działa w stanie dobrej kondycji.
<dl>
<dt>Bieżąca wersja platformy: &lt; Bieżąca wersja platformyTa&gt;</dt> 
<dt>ścieżka zasobów: &lt;PathHashes&gt;</dt>
<dt>: &lt;Hashes&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Uwaga: To zdarzenie zostanie zarejestrowane tylko w przypadku, gdy zostały ustawione następujące zasady: <b>ThreatFileHashLogging niepodpisane</b>.</div>
<div> </div>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1127</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_FOLDER_GUARD_SECTOR_BLOCK</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Kontrolowany dostęp do folderów(CFA) zablokował niezaufany proces przed wprowadzeniem zmian w pamięci. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Kontrolowany dostęp do folderu zablokował proces niezaufany przed potencjalnym modyfikowaniem procesów dyskowych.
<br/> Aby uzyskać więcej informacji na temat rekordu zdarzenia, zobacz następujące informacje:
<dl>
<dt>EventID: &lt; Na przykład: EventID&gt;: 1127Version</dt>
<dt>: &lt;Version&gt;,</dt> na przykład: 
<dt>0Level: &lt;Level&gt;, na przykład: win:</dt>
<dt>WarningTimeCreated: &lt;SystemTime&gt;,</dt> czas utworzenia 
<dt>zdarzeniaEventRecordID: &lt;EventRecordID&gt;,</dt> numer indeksu zdarzenia w dzienniku 
<dt>zdarzeńExecution ProcessID: &lt;Execution ProcessID&gt;, proces,</dt> który wygenerował 
<dt>zdarzenieChannel: &lt;kanał&gt; zdarzeń, na przykład: Microsoft- Windows-Windows Defender/</dt>
<dt>OperationalComputer: &lt;Nazwa&gt;</dt> 
<dt>komputeraBłęd użytkownikaBłędy zabezpieczeń: &lt;Nazwa produktu&gt;</dt>
<dt>: &lt;&gt;</dt> Nazwa produktu, na przykład: Program antywirusowy Microsoft Defender Produkt
<dt>: &lt;wersja&gt; produktu </dt>
<dt>Czas wykrywania: &lt;Czas wykrywania&gt;, czas, kiedy dyrektor ds. zaufania zablokował niezaufany procesUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserPath&gt;</dt>
<dt>: &lt;&gt;</dt> Nazwa urządzenia, nazwa urządzenia lub dysku, do którego uzyskano dostęp w przypadku niezaufanego procesu w celu 
<dt>modyfikacjiProcess Name: Process path, &lt;the process&gt; path name that CFA blocked to accessing</dt> the device or disk for 
<dt>modificationSecurity Intelligence Version: &lt;Antimalware Engine Security&gt; intelligence version</dt>
<dt>&lt;&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Użytkownik może dodać zablokowany proces do listy Dozwolony proces dla <i></i> funkcji CFA, używając programu PowerShell lub Zabezpieczenia Windows Center.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 1150</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTHY</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Jeśli Twoja platforma ochrony przed złośliwym kodem zgłasza stan platformy monitorowania, to zdarzenie wskazuje, że platforma antyszybka jest uruchomiona i znajduje się w stanie dobrej kondycji. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender jest uruchomiony i działa w stanie dobrej kondycji.
<dl>
<dt>Wersja platformy: &lt; Bieżąca wersja platformySignature&gt;</dt> 
<dt>Wersja: &lt;wersja w definicjiJednoznak&gt;</dt>
<dt>: &lt;Antimalware Engine wersja&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie trzeba nic akcję. Klient Program antywirusowy Microsoft Defender znajduje się w stanie dobrej kondycji. To zdarzenie jest zgłaszane co godzinę.
</td>
</tr>

<tr>
<th colspan="2">Identyfikator zdarzenia: 1151</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTH_REPORT</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Endpoint Protection kondycji klienta (czas utc)</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Raport kondycji klienta oprogramowania antywirusowego.
<dl>
<dt>Wersja platformy: &lt; &gt;</dt> Bieżąca wersja platformyAngiejna wersja
<dt>: &lt;Antimalware Engine&gt;</dt> Wersja aparatu inspekcji w czasie rzeczywistym: 
<dt>wersja aparatu inspekcji w czasie rzeczywistym Network Realtime &lt;&gt;</dt>
<dt>&gt;Wersja podpisu: Wersja podpisu antywirusowegoAntispyware wersja podpisu: wersja podpisu ochrony przed złośliwym oprogramowaniemNowy wersja podpisu w czasie rzeczywistym Wersja podpisu inspekcji w czasie rzeczywistym: &lt;</dt>
<dt>&lt;&gt;</dt>
<dt>&lt; &gt;</dt>
<dt>&lt;&gt;</dt> Stan podpisu inspekcji w czasie rzeczywistym w sieci Stan ochrony w czasie rzeczywistym Stan ochrony w czasie rzeczywistym (włączone lub wyłączone)Stan pakietu 
<dt>OA: &lt;W stanie programu Access&gt; (</dt>Włączone lub Wyłączone)Stan 
<dt>IOAV: &lt;Pliki do pobrania programu IE i stan załączników programu Outlook Express&gt; (</dt>włączone lub wyłączone)
<dt>&lt;&gt;</dt>Stan monitorowania zachowania (włączone lub wyłączone)Wiek podpisu oprogramowania antywirusowego
<dt>: &lt;wiek podpisu oprogramowania&gt; antywirusowego  (w dniach)</dt> 
<dt>Wiek podpisu ochrony przed złośliwym oprogramowaniem: &lt; Wiek podpisów ochrony&gt;</dt> przed złośliwym oprogramowaniem (w dniach)Wiek ostatniego szybkiego skanowania
<dt>: &lt;&gt;</dt> wiek ostatniego szybkiego skanowania (w dniach)Wiek ostatniego pełnego skanowania
<dt>: &lt;&gt;</dt> Wiek ostatniego pełnego skanu (w dniach)Czas tworzenia podpisu 
<dt>antywirusowego: ?&lt; Godzina utworzenia podpisu antywirusowegoAntispyware&gt;</dt> 
<dt>signature creation time: ?&lt; Czas tworzenia podpisu ochrony przed złośliwym oprogramowaniemOstatnia&gt;</dt> 
<dt>godzina szybkiego skanowania: ?&lt; Godzina ostatniego szybkiego skanowaniaostatnia&gt;</dt> 
<dt>godzina zakończenia szybkiego skanowania: ?&lt; &gt;Godzina</dt> zakończenia ostatniego szybkiego skanowaniaOstatnia szybkie źródło skanowania: 
<dt>&lt;&gt; Ostatnie źródło szybkiego skanowania (0 = skanowanie nie zostało uruchomione; 1 = zainicjowane przez użytkownika, 2 = zainicjowane przez system)</dt>Ostatni pełny czas rozpoczęcia skanowania
<dt>: ?&lt; Godzina rozpoczęcia ostatniego pełnego skanowaniaOstatnia&gt;</dt> 
<dt>pełny czas zakończenia skanowania: ?&lt; Ostatni czas&gt;</dt> zakończenia pełnego skanowaniaOstatnia pełne źródło skanowania
<dt>: &lt;&gt; Ostatnie pełne źródło skanowania (0 = skanowanie nie zostało uruchomione; 1 = zainicjowane przez użytkownika, 2 = zainicjowane przez system)</dt>
<dt>Stan produktu: Na potrzeby rozwiązywania problemów wewnętrznych
</dl>
</td>
</tr>

<tr>
<th colspan="2">Identyfikator zdarzenia: 2000</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Definicje ochrony przed złośliwym oprogramowaniem zostały pomyślnie zaktualizowane. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Zaktualizowano wersję podpisu antywirusowego.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja podpisuPrewersja&gt;</dt> 
<dt>podpisu Wersja: poprzednia &lt;&gt;</dt>
<dt>wersja podpisu Typ podpisu: &lt;Typ podpisu&gt;, na przykład: <ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Typ aktualizacji: &lt; Typ aktualizacji&gt;: Pełny lub Różnicowy.</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie trzeba nic akcję. Klient Program antywirusowy Microsoft Defender znajduje się w stanie dobrej kondycji. To zdarzenie jest zgłaszane po pomyślnej aktualizacji podpisów.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2001</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aktualizacja analizy zabezpieczeń nie powiodła się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby zaktualizowania podpisów.
<dl>
<dt>Nowa wersja analizy zabezpieczeń: &lt; Nowy numer wersjiPrewersja&gt;</dt> 
<dt>analizy zabezpieczeń: Poprzednia &lt;&gt;</dt>
<dt>wersjaUzyskaj źródło: &lt;Aktualizuj źródło&gt;, na przykład:
<ul>
<li>Folder aktualizacji analizy zabezpieczeń</li>
<li>Serwer aktualizacji wewnętrznej analizy zabezpieczeń</li>
<li>Microsoft Update Server</li>
<li>Udział plików</li>
<li>Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem (MMPC)</li>
</ul>
</dt>
<dt>Etap aktualizacji: &lt;Etap aktualizacji&gt;, na przykład:
<ul>
<li>Wyszukiwanie</li>
<li>Pobierz</li>
<li>Instalowanie</li>
</ul>
</dt>
<dt>Ścieżka źródłowa: nazwa udziału plików w uniwersalnej konwencji nazewnictwa (UNC), nazwa serwera programu Windows Server Update Services (WSUS)/Microsoft Update/ADL.</dt>
<dt> Typ podpisu: &lt;Typ podpisu&gt;, na przykład: <ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Typ aktualizacji: &lt; Typ aktualizacji&gt;: Pełny lub Różnicowy.</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine&gt;</dt> 
<dt>versionPrevious Engine Version: &lt;Previous engine versionError&gt;</dt> 
<dt>Code: &lt;Error&gt; code result code associated with threat status. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Ten błąd występuje, gdy występuje problem podczas aktualizowania definicji.
Aby rozwiązać ten problem:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Aktualizowanie definicji</a> i wymuszanie ponownego skanowania bezpośrednio w punkcie końcowym.</li>
<li>Przejrzyj wpisy w pliku %Windir%\WindowsUpdate.log, aby uzyskać więcej informacji na temat tego błędu.</li>
<li>Skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Pomocą techniczną firmy Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2002</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Pomyślnie zaktualizowano aparat ochrony przed złośliwym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wersji aparatu został zaktualizowany.
<dl>
<dt>Wersja bieżącego aparatu: &lt; Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine&gt;</dt> 
<dt>versionEngine Type: &lt;Engine type&gt;, either antimalware engine, or Network Inspection System engine.</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; Użytkownik&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie trzeba nic akcję. Klient Program antywirusowy Microsoft Defender znajduje się w stanie dobrej kondycji. To zdarzenie jest zgłaszane po pomyślnej aktualizacji aparatu ochrony przed złośliwym oprogramowaniem.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2003</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aktualizacja aparatu ochrony przed złośliwym oprogramowaniem nie powiodła się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas próby zaktualizowania aparatu.
<dl>
<dt>New Engine Version:</dt>
<dt>Previous Engine Version: &lt;Previous engine&gt;</dt> 
<dt>versionEngine Type: &lt;Engine type&gt;, either antimalware engine, or Network Inspection System engine.</dt> 
<dt>Użytkownik: &lt; Domainlt&gt;\&; Kod&gt;</dt> 
<dt>błędu użytkownika: Kod błędu &lt;&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Aktualizacja Program antywirusowy Microsoft Defender nie powiodła się. To zdarzenie występuje, gdy klient nie może zaktualizować się. To zdarzenie zwykle wynika z przerwy w łączności sieciowej podczas aktualizacji.
Aby rozwiązać ten problem:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Aktualizowanie definicji</a> i wymuszanie ponownego skanowania bezpośrednio w punkcie końcowym.</li>
<li>Skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Pomocą techniczną firmy Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2004</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_REVERSION</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Występuje problem podczas ładowania definicji ochrony przed złośliwym oprogramowaniem. Aparat ochrony przed złośliwym oprogramowaniem podejmie próbę załadowania ostatniego znanego dobrego zestawu definicji.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas próby załadowania podpisów i podejmie próbę przywrócenia znanego, dobrego zestawu podpisów.
<dl>
<dt>Podpisy próbna:</dt>
<dt>Kod błędu: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Wersja definicjiAnglinia&gt;</dt>
<dt>: &lt;wersja aparatu ochrony przed złośliwym oprogramowaniem&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Klient Program antywirusowy Microsoft Defender próbował pobrać i zainstalować najnowszy plik definicji i nie powiódł się. Ten błąd może wystąpić, gdy klient napotka błąd podczas próby załadowania definicji lub jeśli plik jest uszkodzony. Program antywirusowy Microsoft Defender spróbuje wrócić do znanego, dobrego zestawu definicji.
Aby rozwiązać ten problem:
<ol>
<li>Uruchom ponownie komputer i spróbuj ponownie.</li>
<li>Pobierz najnowsze definicje z <a href="https://aka.ms/wdsi">witryny Microsoft Security Intelligence sieci Web</a>.
Uwaga: Rozmiar pliku definicji pobranego z witryny może przekraczać 60 MB i nie powinien być używany jako długoterminowe rozwiązanie do aktualizowania definicji.
</li>
<li>Skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Pomocą techniczną firmy Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2005</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_PLATFORMOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Nie można załadować aparatu ochrony przed złośliwym oprogramowaniem, ponieważ platforma antyszybka jest przejadą. Platforma zapobiegająca złośliwym oprogramowaniem załaduje ostatnio znany dobry aparat ochrony przed złośliwym oprogramowaniem i podejmie próbę aktualizacji.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender ładowania aparatu ochrony przed złośliwym oprogramowaniem, ponieważ bieżąca wersja platformy nie jest obsługiwana. Program antywirusowy Microsoft Defender powrót do ostatniego znanego dobrego aparatu i zostanie podejmowana próba aktualizacji platformy.
<dl>
<dt>Bieżąca wersja platformy: &lt;wersja na bieżącą platformę&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2006</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aktualizacja platformy nie powiodła się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby zaktualizowania platformy.
<dl>
<dt>Bieżąca wersja platformy: &lt; Bieżąca wersja platformy&gt;</dt> 
<dt>Kod błędu: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2007</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_ALMOSTOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma niedługo będzie już niedługo będzie aktualny. Pobierz najnowszą platformę, aby zapewnić ochronę na bieżąco.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender będzie wkrótce wymagać nowszej wersji platformy do obsługi przyszłych wersji aparatu ochrony przed złośliwym oprogramowaniem. Pobierz najnowszą Program antywirusowy Microsoft Defender, aby zapewnić najlepszy dostępny poziom ochrony.
<dl>
<dt>Bieżąca wersja platformy: &lt;wersja na bieżącą platformę&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2010</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat ochrony przed złośliwym oprogramowaniem użył usługi podpisów dynamicznych do uzyskania dodatkowych definicji. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender <i>używanej usługi podpisów</i> dynamicznych do pobierania dodatkowych podpisów w celu ochrony Komputera.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja podpisu&gt;</dt>
<dt> Typ podpisu: &lt;Typ podpisu&gt;, na przykład: <ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Wersja bieżącego aparatu: &lt; Wersja bieżącego aparatuDynamic&gt;</dt>
<dt> Signature Type: &lt;Dynamiczny typ podpisu&gt;, na przykład:
<ul>
<li>Wersja</li>
<li>Timestamp</li>
<li>Bez limitu</li>
<li>Czas trwania</li>
</ul>
</dt>
<dt>Ścieżka utrwaloności: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> limit Type: &lt;Persistence limit type&gt;, example:
<ul>
<li>Wersja VDM</li>
<li>Timestamp</li>
<li>Bez limitu</li>
</ul>
</dt>
<dt>Limit czasu trwania: limit czasu trwania podpisu fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2011</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Usługa podpisów dynamicznych usunęła aktualne definicje dynamiczne. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender używana usługa <i>podpisów dynamicznych do</i> odrzucania przestarzałych podpisów.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja podpisu&gt;</dt>
<dt> Typ podpisu: &lt;Typ podpisu&gt;, na przykład: <ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Wersja bieżącego aparatu: &lt; Wersja bieżącego aparatuDynamic&gt;</dt>
<dt> Signature Type: &lt;Dynamiczny typ podpisu&gt;, na przykład:
<ul>
<li>Wersja</li>
<li>Timestamp</li>
<li>Bez limitu</li>
<li>Czas trwania</li>
</ul>
</dt>
<dt>Ścieżka utrwaloności: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Persistence Limit Type: &lt;Persistence limit&gt; type, example:
<ul>
<li>Wersja VDM</li>
<li>Timestamp</li>
<li>Bez limitu</li>
</ul>
</dt>
<dt>Limit czasu trwania: limit czasu trwania podpisu fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie trzeba nic akcję. Klient Program antywirusowy Microsoft Defender znajduje się w stanie dobrej kondycji. To zdarzenie jest zgłaszane, gdy usługa podpisu dynamicznego pomyślnie usuwa aktualne definicje dynamiczne.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2012</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Podczas próby korzystania z usługi podpisów dynamicznych aparat ochrony przed złośliwym kodem napotkał błąd. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas próby użycia usługi podpisu <i>dynamicznego</i>.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja podpisu&gt;</dt>
<dt> Typ podpisu: &lt;Typ podpisu&gt;, na przykład: <ul>
<li>Oprogramowanie antywirusowe</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>Ochrona przed złośliwym oprogramowaniem</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Wersja bieżącego aparatu: &lt; Current engine versionError&gt;</dt> 
<dt>Code: &lt;Error code&gt; Result code associated with threat status. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
<dt> Dynamiczny typ podpisu: &lt;dynamiczny typ podpisu&gt;, na przykład:
<ul>
<li>Wersja</li>
<li>Timestamp</li>
<li>Bez limitu</li>
<li>Czas trwania</li>
</ul>
</dt>
<dt>Ścieżka utrwaloności: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> limit Type: &lt;Persistence limit type&gt;, example:
<ul>
<li>Wersja VDM</li>
<li>Timestamp</li>
<li>Bez limitu</li>
</ul>
</dt>
<dt>Limit czasu trwania: limit czasu trwania podpisu fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Sprawdź ustawienia łączności internetowej.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2013</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED_ALL </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Usługa podpisów dynamicznych usunęła wszystkie dynamiczne definicje. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender odrzucone wszystkich <i>podpisów usługi podpisów dynamicznych</i>.
<dl>
<dt>Bieżąca wersja podpisu: bieżąca &lt;wersja podpisu&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2020</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOADED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat ochrony przed złośliwym oprogramowaniem pobrał czysty plik. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender pobrano czysty plik.
<dl>
<dt>Nazwa pliku: &lt; Nazwa pliku&gt; Nazwa pliku.</dt> 
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja podpisuCurrent&gt;</dt> 
<dt>Engine Wersja: &lt;wersja bieżącego aparatu&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2021</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOAD_FAILED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat ochrony przed złośliwym oprogramowaniem nie powiódł się do pobrania czystego pliku. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas próby pobrania czystego pliku.
<dl>
<dt>Nazwa pliku: &lt; Nazwa pliku&gt; Nazwa pliku.</dt> 
<dt>Bieżąca wersja podpisu: &lt; Current signature versionCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionError&gt;</dt> 
<dt>Code: &lt;Error code&gt; result code associated with threat status. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Sprawdź ustawienia łączności internetowej.
Klient Program antywirusowy Microsoft Defender napotkał błąd podczas korzystania z usługi podpisów dynamicznych w celu pobrania najnowszych definicji dla określonego zagrożenia. Ten błąd jest prawdopodobnie spowodowany problemem z łącznością sieciową.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2030</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALLED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Został pobrany aparat ochrony przed złośliwym oprogramowaniem skonfigurowany do uruchamiania w trybie offline przy następnym ponownym uruchomieniu systemu.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender pobrać i skonfigurować oprogramowanie antywirusowe w trybie offline do uruchamiania przy następnym ponownym uruchomieniu komputera.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2031</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALL_FAILED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat ochrony przed złośliwym kodem nie mógł pobrać i skonfigurować skanowania w trybie offline.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wystąpił błąd podczas próby pobrania i skonfigurowania oprogramowania antywirusowego w trybie offline.
<dl>
<dt>Kod błędu: &lt; Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2040</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_OS_EXPIRING </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Obsługa ochrony przed złośliwym oprogramowaniem dla tej wersji systemu operacyjnego wkrótce zakończy się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Pomoc techniczna dla Twojego systemu operacyjnego wkrótce wygaśnie. Uruchamianie Program antywirusowy Microsoft Defender nie jest odpowiednim rozwiązaniem w zakresie ochrony przed zagrożeniami.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2041</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_OS_EOL </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Wsparcie techniczne dotyczące ochrony przed złośliwym oprogramowaniem dla tego systemu operacyjnego zakończyło się. W celu dalszej pomocy technicznej należy uaktualnić system operacyjny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Pomoc techniczna dla Twojego systemu operacyjnego wygasła. Uruchamianie Program antywirusowy Microsoft Defender nie jest odpowiednim rozwiązaniem w zakresie ochrony przed zagrożeniami.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2042</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_PROTECTION_EOL </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat chroniący przed złośliwym kodem nie obsługuje już tego systemu operacyjnego i nie chroni systemu przed złośliwym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Pomoc techniczna dla Twojego systemu operacyjnego wygasła. Program antywirusowy Microsoft Defender nie jest już obsługiwane w systemie operacyjnym, przestało działać i nie chroni przed zagrożeniami złośliwym oprogramowaniem.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 3002</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_FAILURE </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Ochrona w czasie rzeczywistym napotkała błąd i nie powiodła się.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender Real-Time natrafiła na błąd i nie powiodła się.
<dl>
<dt>Funkcja: &lt;funkcja&gt;, na przykład:
<ul>
<li>W programie Access</li>
<li>Internet Explorer — pliki do pobrania i załączniki programu Microsoft Outlook Express</li>
<li>Monitorowanie zachowania</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Kod błędu: &lt; Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt> 
<dt>Przyczyna: Program antywirusowy Microsoft Defender funkcji ochrony w czasie rzeczywistym.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Należy ponownie uruchomić system, a następnie uruchomić pełne skanowanie, ponieważ być może przez pewien czas system nie był chroniony.
Funkcja Program antywirusowy Microsoft Defender klienta ochrony w czasie rzeczywistym napotkała błąd, ponieważ nie można uruchomić jednej z usług.
Jeśli po nim zostanie określony identyfikator zdarzenia 3007, błąd był tymczasowy, a po niepowodzeniu odzyskany klient ochrony przed złośliwym oprogramowaniem.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 3007</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_RECOVERED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Ochrona w czasie rzeczywistym odzyskana po awarii. Gdy zostanie wyświetlony ten błąd, zalecamy uruchomienie pełnego skanowania systemu. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender funkcja Ochrona w czasie rzeczywistym została ponownie uruchomiona. Zalecane jest uruchomienie pełnego skanowania systemu w celu wykrycia wszystkich elementów, które mogą zostać nieodebrane, gdy ten agent był u dołu.
<dl>
<dt>Funkcja: &lt;funkcja&gt;, na przykład:
<ul>
<li>W programie Access</li>
<li>Program IE pobiera i Outlook express</li>
<li>Monitorowanie zachowania</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Przyczyna: Program antywirusowy Microsoft Defender funkcji ochrony w czasie rzeczywistym.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Funkcja ochrony w czasie rzeczywistym została uruchomiona ponownie. Jeśli to zdarzenie nastąpi ponownie, skontaktuj się z pomocą <a href="https://go.microsoft.com/fwlink/?LinkId=215491">techniczną firmy Microsoft</a>.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5000</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_RTP_ENABLED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Jest włączona ochrona w czasie rzeczywistym. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym w poszukiwaniu złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5001</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_RTP_DISABLED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Ochrona w czasie rzeczywistym jest wyłączona. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym w poszukiwaniu złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania zostało wyłączone.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5004</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_CONFIGURED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Zmieniono konfigurację ochrony w czasie rzeczywistym. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender w czasie rzeczywistym zmieniła się konfiguracja funkcji ochrony w czasie rzeczywistym.
<dl>
<dt>Funkcja: &lt;funkcja&gt;, na przykład:
<ul>
<li>W programie Access</li>
<li>Program IE pobiera i Outlook express</li>
<li>Monitorowanie zachowania</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Konfiguracja: </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5007</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_CONFIG_CHANGED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Zmieniono konfigurację platformy ochrony przed złośliwym oprogramowaniem.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender się zmieniła. Jeśli jest to nieoczekiwane zdarzenie, należy przejrzeć ustawienia, ponieważ może to być wynikiem złośliwego oprogramowania.
<dl>
<dt>Stara wartość: &lt; Numer starej wartości&gt; Stara wartość konfiguracji oprogramowania antywirusowego.</dt> 
<dt>Nowa wartość: &lt; Nowa wartość Nowa&gt; wartość konfiguracji oprogramowania antywirusowego.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5008</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_FAILURE</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Aparat ochrony przed złośliwym kodem napotkał błąd i nie powiódł się.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender został zakończony z powodu nieoczekiwanego błędu.
<dl>
<dt>Typ błędu: &lt; Typ błędu&gt;, na przykład: Kod awarii</dt> lub 
<dt>HangException: &lt;Kod błęduResource&gt;</dt>
<dt>: &lt;Resource&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Aby rozwiązać ten problem:<ol>
<li>Spróbuj ponownie uruchomić usługę.<ul>
<li>W przypadku oprogramowania antywirusowego i oprogramowania szpiegującego w wierszu polecenia o podwyższonym poziomie uprawnień wpisz <b>net stop msmpsvc</b>, a następnie wpisz <b>net start msmpsvc</b> , aby uruchomić ponownie aparat ochrony przed złośliwym kodem.</li>
<li>W przypadku <i>systemu</i> inspekcji sieci w wierszu polecenia o podwyższonym poziomie uprawnień wpisz net <b>start nissrv</b>, a następnie wpisz <b>net start nissrv</b>, <i></i> aby uruchomić ponownie aparat systemu inspekcji sieciowej przy użyciu pliku NiSSRV.exe inspekcji.
</li>
</ul>
</li>
<li>Jeśli błąd wystąpi w taki sam sposób, wyszukaj kod błędu, uzyskujejąc dostęp do witryny pomocy technicznej firmy <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a> i wprowadzając numer błędu <b></b> w polu wyszukiwania, a następnie skontaktuj się z pomocą techniczną <a href="https://go.microsoft.com/fwlink/?LinkId=215491">firmy Microsoft</a>.</li>
</ol>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Aparat Program antywirusowy Microsoft Defender został zatrzymany z powodu nieoczekiwanego błędu.
Aby rozwiązać ten problem:
<ol>
<li>Uruchom ponownie skanowanie.</li>
<li>Jeśli błąd wystąpi w taki sam sposób, przejdź do witryny pomocy technicznej firmy <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a> i wprowadź numer błędu w <b></b> polu Wyszukaj, aby wyszukać kod błędu.</li>
<li>Skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Pomocą techniczną firmy Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5009</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_ENABLED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania jest włączone. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender w poszukiwaniu złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania zostało włączone.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5010</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_DISABLED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania jest wyłączone.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender skanowanie w poszukiwaniu złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania jest wyłączone.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5011</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_ENABLED</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu wirusów jest włączone.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender skanowanie w poszukiwaniu wirusów.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5012</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_DISABLED </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Skanowanie w poszukiwaniu wirusów jest wyłączone. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender skanowanie w poszukiwaniu wirusów jest wyłączone.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5013</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>
</b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Ochrona przed naruszeniami zablokowała zmianę Program antywirusowy Microsoft Defender.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Jeśli ochrona przed naruszeniami jest włączona, wszelkie próby zmiany ustawień usługi Defender, jeśli są zablokowane, i zostanie wygenerowany identyfikator zdarzenia 5013, który oznacza, że zmiana ustawień została zablokowana.
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5100</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_EXPIRATION_WARNING_STATE </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma zapobiegająca złośliwym oprogramowaniem wkrótce wygaśnie. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wprowadzono okres prolongaty i wkrótce wygaśnie. Po wygaśnięciu ten program wyłączy ochronę przed wirusami, programami szpiegującymi i innym potencjalnie niechcianym oprogramowaniem.
<dl>
<dt>Przyczyna wygaśnięcia: powód Program antywirusowy Microsoft Defender wygaśnie.</dt> 
<dt>Data wygaśnięcia: data Program antywirusowy Microsoft Defender wygaśnie.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 5101</th>
</tr>
<tr><td>
Nazwa symboliczna:
</td>
<td >
<b>MALWAREPROTECTION_DISABLED_EXPIRED_STATE </b>
</td>
</tr>
<tr>
<td>
Komunikat:
</td>
<td >
<b>Platforma zapobiegająca złośliwym oprogramowaniem wygasła. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender okres prolongaty wygasł. Ochrona przed wirusami, programami szpiegującymi i innym potencjalnie niepożądanym oprogramowaniem jest wyłączona.
<dl>
<dt>Przyczyna wygaśnięcia:</dt>
<dt>Data wygaśnięcia: </dt>
<dt>Kod błędu Kod &lt;&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis błędu&gt; Opis błędu. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Program antywirusowy Microsoft Defender kodów błędów klienta Jeśli Program antywirusowy Microsoft Defender wystąpią jakiekolwiek problemy, zazwyczaj jest wyświetlany kod błędu ułatwiający rozwiązanie tego problemu. Najczęściej oznacza to, że wystąpił problem podczas instalowania aktualizacji.
Ta sekcja zawiera następujące informacje dotyczące błędów Program antywirusowy Microsoft Defender klienta.
- Kod błędu - Możliwa przyczyna błędu - Porada co należy zrobić w tej chwili

Informacje zawarte w tych tabelach ułatwiają rozwiązywanie problemów z Program antywirusowy Microsoft Defender błędów.


<table>
<tr>
<th colspan="2">Kod błędu: 0x80508007</th>
</tr>
<tr>
<td>Komunikat</td>
<td>
<b>ERR_MP_NO_MEMORY </b>
</td>
</tr>
<tr>
<td>
Możliwa przyczyna
</td>
<td>
Ten błąd wskazuje, że może zabrakło pamięci.
</td>
</tr>
<tr>
<td>Rozwiązanie</td>
<td>
<ol>
<li>Sprawdź dostępną pamięć na urządzeniu.</li>
<li>Zamknij wszystkie nieużywane aplikacje, które działają, aby uwolnić pamięć na urządzeniu.</li>
<li>Uruchom ponownie urządzenie i ponownie uruchom skanowanie.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x8050800C</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_BAD_INPUT_DATA</b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że być może występuje problem z produktem zabezpieczającym.
</td>
</tr><tr><td>Rozwiązanie</td><td>
<ol>
<li>Aktualizuj definicje. Możesz:<ol>
<li>Kliknij przycisk <b>Aktualizuj definicje</b> na <b>karcie</b> Aktualizowanie w programie Program antywirusowy Microsoft Defender. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Lub,
</li>
<li>Pobierz najnowsze definicje z <a href="https://aka.ms/wdsi">witryny Microsoft Security Intelligence sieci Web</a>.
Uwaga: Rozmiar pliku definicji pobranego z witryny może przekraczać 60 MB i nie powinien być używany jako długoterminowe rozwiązanie do aktualizowania definicji.
</li>
</ol>
</li>
<li>Uruchom pełne skanowanie.
</li>
<li>Uruchom ponownie urządzenie i spróbuj ponownie.</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508020</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_BAD_CONFIGURATION </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że może wystąpić błąd konfiguracji aparatu. jest to związane z danymi wejściowymi, które nie pozwalają na poprawne działanie aparatu.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x805080211
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że Program antywirusowy Microsoft Defender kwarantannie zagrożenia.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508022
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że do usunięcia zagrożeń jest wymagane ponowne uruchomienie komputera.
</td>
</tr>
<tr>
<th colspan="2">
0x80508023
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_THREAT_NOT_FOUND </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że zagrożenie może już nie być obecne na multimediach lub złośliwe oprogramowanie może zatrzymać skanowanie urządzenia.
</tr><tr><td>Rozwiązanie
</td>
<td>
Uruchom <a href="https://www.microsoft.com/security/scanner/default.aspx">Skaner bezpieczeństwa Microsoft zaktualizuj</a> oprogramowanie zabezpieczające i spróbuj ponownie.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508024 </th></tr>
<tr>
<td>Komunikat</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że może być wymagane pełne skanowanie systemu.
</td></tr>
<tr>
<td>Rozwiązanie</td><td>
Uruchom pełne skanowanie systemu.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508025
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_MANUAL_STEPS_REQUIRED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że do usunięcia zagrożeń wymagane są ręczne kroki.
</td></tr><tr><td>Rozwiązanie</td><td>
Wykonaj czynności ręcznego rozwiązywania problemów opisane w witrynie <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">Encyclopedia dotyczącej ochrony przed złośliwym oprogramowaniem firmy Microsoft</a>. W historii zdarzeń możesz znaleźć link specyficzny dla zagrożeń.<br/></td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508026
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że usuwanie wewnątrz typu kontenera może nie być obsługiwane.
</td></tr><tr><td>Rozwiązanie</td><td>
Program antywirusowy Microsoft Defender nie może rozwiązać problemów ze zagrożeniami wykrytymi w archiwum. Rozważ ręczne usunięcie wykrytych zasobów.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508027
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_REMOVE_LOW_MEDIUM_DISABLED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że usunięcie niskich i średnich zagrożeń może zostać wyłączone.
</td></tr><tr><td>Rozwiązanie</td><td>
Sprawdź wykryte zagrożenia i rozwiąż je zgodnie z wymaganiami.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508029
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERROR_MP_RESCAN_REQUIRED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że konieczne jest ponowne zagrożenia.
</td></tr><tr><td>Rozwiązanie</td><td>
Uruchom pełne skanowanie systemu.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508030
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERROR_MP_CALLISTO_REQUIRED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że wymagane jest skanowanie w trybie offline.
</td></tr><tr><td>Rozwiązanie</td><td>
Uruchamianie aplikacji Program antywirusowy Microsoft Defender. Aby dowiedzieć się, jak to zrobić, przeczytaj artykuł Program antywirusowy Microsoft Defender <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">offline</a>.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508031
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, Program antywirusowy Microsoft Defender nie obsługuje bieżącej wersji platformy i wymaga nowej wersji platformy.
</td></tr><tr><td>Rozwiązanie</td><td>
Z tej funkcji można korzystać tylko Program antywirusowy Microsoft Defender w Windows 10 i Windows 11. Na Windows 8, Windows 7 i Windows Vista można <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">używać System Center Endpoint Protection.</a><br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Poniższe kody błędów są używane podczas wewnętrznych testów Program antywirusowy Microsoft Defender.

Jeśli widzisz te błędy, możesz spróbować zaktualizować [](manage-updates-baselines-microsoft-defender-antivirus.md) definicje i wymusić ponowne wypróbowanie bezpośrednio w punkcie końcowym.


<table>
<tr>
<th colspan="3">Wewnętrzne kody błędów</th>
</tr>
<tr>
<th><b>Kod błędu</b></th>
<th>Wyświetlana wiadomość</th>
<th>Możliwe przyczyny błędu i rozwiązania problemu</th>
</tr>
<tr>
<td>
0x80501004
</td>
<td>
<b>ERROR_MP_NO_INTERNET_CONN </b>
</td>
<td>
Sprawdź połączenie internetowe, a następnie ponownie uruchom skanowanie.
</td>
</tr>
<tr>
<td>
0x80501000
</td>
<td>
<b>ERROR_MP_UI_CONSOLIDATION_BAS</b> E
</td>
<td rowspan="34">
Jest to błąd wewnętrzny. Przyczyna nie jest jasno zdefiniowana.
</td>
<td rowspan="36">

</td>
</tr>
<tr>
<td>
0x80501001
</td>
<td>
<b>ERROR_MP_ACTIONS_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80501002
</td>
<td>
<b>ERROR_MP_NOENGINE</b>
</td>
</tr>
<tr>
<td>
0x80501003
</td>
<td>
<b>ERROR_MP_ACTIVE_THREATS</b>
</td>
</tr>
<tr>
<td>
0x805011011
</td>
<td>
<b>MP_ERROR_CODE_LUA_CANCELLED </b>
</td>
</tr>
<tr>
<td>
0x80501101
</td>
<td>
<b>ERROR_LUA_CANCELLATION </b>
</td>
</tr>
<tr>
<td>
0x80501102
</td>
<td>
<b>MP_ERROR_CODE_ALREADY_SHUTDOWN</b>
</td>
</tr>
<tr>
<td>
0x80501103
</td>
<td>
<b>MP_ERROR_CODE_RDEVICE_S_ASYNC_CALL_PENDING </b>
</td>
</tr>
<tr>
<td>
0x80501104
</td>
<td>
<b>MP_ERROR_CODE_CANCELLED</b>
</td>
</tr>
<tr>
<td>
0x80501105
</td>
<td>
<b>MP_ERROR_CODE_NO_TARGETOS</b>
</td>
</tr>
<tr>
<td>
0x80501106
</td>
<td>
<b>MP_ERROR_CODE_BAD_REGEXP</b>
</td>
</tr>
<tr>
<td>
0x80501107
</td>
<td>
<b>MP_ERROR_TEST_INDUCED_ERROR</b>
</td>
</tr>
<tr>
<td>
0x80501108
</td>
<td>
<b>MP_ERROR_SIG_BACKUP_DISABLED</b>
</td>
</tr>
<tr>
<td>
0x80508001
</td>
<td>
<b>ERR_MP_BAD_INIT_MODULES</b>
</td>
</tr>
<tr>
<td>
0x80508002
</td>
<td>
<b>ERR_MP_BAD_DATABASE</b>
</td>
</tr>
<tr>
<td>
0x80508004
</td>
<td>
<b>ERR_MP_BAD_UFS </b>
</td>
</tr>
<tr>
<td>
0x8050800C
</td>
<td>
<b>ERR_MP_BAD_INPUT_DATA</b>
</td>
</tr>
<tr>
<td>
0x8050800D
</td>
<td>
<b>ERR_MP_BAD_GLOBAL_STORAGE</b>
</td>
</tr>
<tr>
<td>
0x8050800E
</td>
<td>
<b>ERR_MP_OBSOLETE</b>
</td>
</tr>
<tr>
<td>
0x8050800F
</td>
<td>
<b>ERR_MP_NOT_SUPPORTED</b>
</td>
</tr>
<tr>
<td>
0x8050800F 0x80508010
</td>
<td>
<b>ERR_MP_NO_MORE_ITEMS </b>
</td>
</tr>
<tr>
<td>
0x80508011
</td>
<td>
<b>ERR_MP_DUPLICATE_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508012
</td>
<td>
<b>ERR_MP_BAD_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508013
</td>
<td>
<b>ERR_MP_BAD_USERDB_VERSION</b>
</td>
</tr>
<tr>
<td>
0x80508014
</td>
<td>
<b>ERR_MP_RESTORE_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80508016
</td>
<td>
<b>ERR_MP_BAD_ACTION</b>
</td>
</tr>
<tr>
<td>
0x80508019
</td>
<td>
<b>ERR_MP_NOT_FOUND</b>
</td>
</tr>
<tr>
<td>
0x80509001
</td>
<td>
<b>ERR_RELO_BAD_EHANDLE</b>
</td>
</tr>
<tr>
<td>
0x80509003
</td>
<td>
<b>ERR_RELO_KERNEL_NOT_LOADED</b>
</td>
</tr>
<tr>
<td>
0x8050A001
</td>
<td>
<b>ERR_MP_BADDB_OPEN</b>
</td>
</tr>
<tr>
<td>
0x8050A002
</td>
<td>
<b>ERR_MP_BADDB_HEADER</b>
</td>
</tr>
<tr>
<td>
0x8050A003
</td>
<td>
<b>ERR_MP_BADDB_OLDENGINE</b>
</td>
</tr>
<tr>
<td>
0x8050A004
</td>
<td>
<b>ERR_MP_BADDB_CONTENT </b>
</td>
</tr>
<tr>
<td>
0x8050A005
</td>
<td>
<b>ERR_MP_BADDB_NOTSIGNED</b>
</td>
</tr>
<tr>
<td>
0x8050801
</td>
<td>
<b>ERR_MP_REMOVE_FAILED</b>
</td>
<td>
Jest to błąd wewnętrzny. Usunięcie złośliwego oprogramowania może zostać wyzwolone, gdy usunięcie złośliwego oprogramowania nie powiedzie się.
</td>
</tr>
<tr>
<td>
0x80508018
</td>
<td>
<b>ERR_MP_SCAN_ABORTED </b>
</td>
<td>
Jest to błąd wewnętrzny. Mógł zostać wyzwolony, gdy skanowanie nie powiodło się.
</td>
</tr>
</table>

## <a name="related-topics"></a>Tematy pokrewne

- [Raporty dotyczące Program antywirusowy Microsoft Defender informacji](report-monitor-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
