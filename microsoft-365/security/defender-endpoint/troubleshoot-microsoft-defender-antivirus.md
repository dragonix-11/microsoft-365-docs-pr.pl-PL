---
title: Program antywirusowy Microsoft Defender identyfikatory zdarzeń i kody błędów
description: Wyszukaj przyczyny i rozwiązania dotyczące identyfikatorów i błędów zdarzeń Program antywirusowy Microsoft Defender
keywords: zdarzenie, kod błędu, siem, rejestrowanie, rozwiązywanie problemów, wef, przekazywanie zdarzeń systemu Windows
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
ms.openlocfilehash: 9008fe0d6a4c46d544e4d806c3a15b24c53f2f10
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637999"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Przejrzyj dzienniki zdarzeń i kody błędów, aby rozwiązać problemy z programem antywirusowym Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Jeśli wystąpi problem z Program antywirusowy Microsoft Defender, możesz wyszukać tabele w tym temacie w celu znalezienia pasującego problemu i potencjalnego rozwiązania.

Lista tabel:

- [identyfikatory zdarzeń Program antywirusowy Microsoft Defender](#windows-defender-av-ids) (dotyczą one Windows 10, Windows 11 i Windows Server 2016)
- [kody błędów klienta Program antywirusowy Microsoft Defender](#error-codes)
- [Wewnętrzne kody błędów klienta Program antywirusowy Microsoft Defender (używane przez firmę Microsoft podczas opracowywania i testowania)](#internal-error-codes)

> [!TIP]
> Możesz również odwiedzić witrynę internetową Ochrona punktu końcowego w usłudze Microsoft Defender demo pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby potwierdzić, że działają następujące funkcje:
>
> - Ochrona dostarczana przez chmurę
> - Szybkie uczenie się (w tym Blok od pierwszego wejrzenia)
> - Potencjalnie niepożądane blokowanie aplikacji

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>identyfikatory zdarzeń Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender rejestruje identyfikatory zdarzeń w dzienniku zdarzeń Windows.

Możesz bezpośrednio wyświetlić dziennik zdarzeń lub jeśli masz narzędzie do zarządzania informacjami o zabezpieczeniach i zdarzeniami innych firm (SIEM), możesz również użyć [Program antywirusowy Microsoft Defender identyfikatorów zdarzeń klienta](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids), aby przejrzeć określone zdarzenia i błędy z punktów końcowych.

Tabela w tej sekcji zawiera listę głównych identyfikatorów zdarzeń Program antywirusowy Microsoft Defender i, jeśli to możliwe, zawiera sugerowane rozwiązania umożliwiające naprawienie lub rozwiązanie błędu.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Aby wyświetlić zdarzenie Program antywirusowy Microsoft Defender

1. Otwórz **Podgląd zdarzeń**.
2. W drzewie konsoli rozwiń węzeł **Dzienniki aplikacji i usług**, następnie **pozycję Microsoft**, a następnie **Windows**, a następnie **Windows Defender**.
3. Kliknij dwukrotnie pozycję **Operacje**.
4. W okienku szczegółów wyświetl listę poszczególnych zdarzeń, aby znaleźć zdarzenie.
5. Kliknij zdarzenie, aby wyświetlić szczegółowe informacje o zdarzeniu w dolnym okienku na kartach **Ogólne** i **Szczegóły** .

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
<b>Rozpoczęto skanowanie oprogramowania chroniącego przed złośliwym kodem. </b>
</td>
</tr>
<tr>
<td >
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikatora odpowiedniego skanowania.&gt;</dt>
<dt> Typ skanowania: &lt;typ&gt; skanowania, na przykład:<ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;skanuj parametry&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klienta</li>
</ul>
</dt>
<dt>Skanuj zasoby: &lt; Zasoby (takie jak pliki/katalogi/BHO), które zostały zeskanowane.&gt;</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; Użytkownika&gt;</dt>
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
<b>Skanowanie oprogramowania chroniącego przed złośliwym kodem zostało zakończone.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikatora odpowiedniego skanowania.&gt;</dt>
<dt> Typ skanowania: &lt;typ&gt; skanowania, na przykład:<ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;skanuj parametry&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klienta</li>
</ul>
</dt>
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserScan&gt;</dt> 
<dt>Time: &lt;czas trwania skanowania.&gt;</dt>
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
<b>Skanowanie oprogramowania chroniącego przed złośliwym kodem zostało zatrzymane przed jego zakończeniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikatora odpowiedniego skanowania.&gt;</dt>
<dt> Typ skanowania: &lt;typ&gt; skanowania, na przykład:<ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;skanuj parametry&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klienta</li>
</ul>
</dt>
<dt>Użytkownika: &lt; Domainlt&gt;&amp;; UserScan&gt;</dt> 
<dt>Time: &lt;czas trwania skanowania.&gt;</dt>
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
<b>Skanowanie oprogramowania chroniącego przed złośliwym kodem zostało wstrzymane. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikatora odpowiedniego skanowania.&gt;</dt>
<dt> Typ skanowania: &lt;typ&gt; skanowania, na przykład:<ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;skanuj parametry&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klienta</li>
</ul>
</dt>
<dt>Użytkownik: &lt;Domainlt&gt;\&; Użytkownika&gt;</dt>
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
<b>Wznowiono skanowanie oprogramowania chroniącego przed złośliwym kodem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikatora odpowiedniego skanowania.&gt;</dt>
<dt> Typ skanowania: &lt;typ&gt; skanowania, na przykład:<ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;skanuj parametry&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klienta</li>
</ul>
</dt>
<dt>Użytkownik: &lt;Domainlt&gt;\&; Użytkownika&gt;</dt>
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
<b>Skanowanie chroniące przed złośliwym kodem nie powiodło się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
<dl>
<dt>Identyfikator skanowania: &lt; Numer identyfikatora odpowiedniego skanowania.&gt;</dt>
<dt> Typ skanowania: &lt;typ&gt; skanowania, na przykład:<ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Parametry skanowania: &lt;skanuj parametry&gt;, na przykład:<ul>
<li>Pełne skanowanie</li>
<li>Szybkie skanowanie</li>
<li>Skanowanie klienta</li>
</ul>
</dt>
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Klient programu antywirusowego napotkał błąd, a bieżące skanowanie zostało zatrzymane. Skanowanie może zakończyć się niepowodzeniem z powodu problemu po stronie klienta. Ten rekord zdarzenia obejmuje identyfikator skanowania, typ skanowania (Program antywirusowy Microsoft Defender, oprogramowanie chroniące przed złośliwym kodem, oprogramowanie chroniące przed złośliwym kodem), parametry skanowania, użytkownika, który rozpoczął skanowanie, kod błędu i opis błędu.
Aby rozwiązać ten problem:
<ol>
<li>Uruchom ponownie skanowanie.</li>
<li>Jeśli nie powiedzie się w ten sam sposób, przejdź do <a href="https://go.microsoft.com/fwlink/?LinkId=215163">witryny pomoc techniczna firmy Microsoft</a>, wprowadź numer błędu w polu <b>Wyszukiwania</b>, aby wyszukać kod błędu.</li>
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
<b>Aparat ochrony przed złośliwym kodem znalazł złośliwe oprogramowanie lub inne potencjalnie niechciane oprogramowanie. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Wykrywanie źródła&gt;, na przykład:<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieci</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;typ&gt; wykrywania, na przykład:<ul>
<li>Heurystyki</li>
<li>Ogólny</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;źródło&gt; wykrywania na przykład:<ul>
<li>Użytkownik: zainicjowany przez użytkownika</li>
<li>System: zainicjowany przez system</li>
<li>W czasie rzeczywistym: inicjowany składnik czasu rzeczywistego</li>
<li>IOAV: Zainicjowano pobieranie i Outlook załączników usługi IE</li>
<li>NIS: System inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; Chroni to przed złośliwymi kontrolkami stron internetowych</li>
<li>Wczesna ochrona przed złośliwym kodem (ELAM). Obejmuje to złośliwe oprogramowanie wykryte przez sekwencję rozruchu</li>
<li>Zdalne zaświadczanie</li>
</ul>Interfejs skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI). Służy głównie do ochrony skryptów (PowerShell, VBS), choć może być wywoływany przez inne firmy, jak również.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
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
<b>Platforma ochrony przed złośliwym kodem wykonała akcję ochrony systemu przed złośliwym oprogramowaniem lub innym potencjalnie niepożądanym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender podjęła działania w celu ochrony tej maszyny przed złośliwym oprogramowaniem lub innym potencjalnie niepożądanym oprogramowaniem. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt>
<dt> Akcja: &lt;Akcja&gt;, na przykład:<ul>
<li>Czyszczenie: zasób został oczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł zostać wykonany/istnieje</li>
<li>Zdefiniowana przez użytkownika: akcja zdefiniowana przez użytkownika, która jest zwykle jedną z tej listy akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blokuj: wykonanie zasobu zostało zablokowane</li>
</ul>
</dt>
<dt>Stan: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
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
<b>Platforma ochrony przed złośliwym kodem próbowała wykonać akcję w celu ochrony systemu przed złośliwym oprogramowaniem lub innym potencjalnie niepożądanym oprogramowaniem, ale akcja nie powiodła się.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas podejmowania akcji dotyczących złośliwego oprogramowania lub innego potencjalnie niechcianego oprogramowania. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka&gt;</dt>
<dt> plikuAction: &lt;akcja&gt;, na przykład:<ul>
<li>Czyszczenie: zasób został oczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł zostać wykonany/istnieje</li>
<li>Zdefiniowana przez użytkownika: akcja zdefiniowana przez użytkownika, która jest zwykle jedną z tej listy akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blokuj: wykonanie zasobu zostało zablokowane</li>
</ul>
</dt>
<dt>Kod błędu: &lt; Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis&gt; błędu Opis błędu. </dt> 
<dt>Stan: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
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
<b>Platforma ochrony przed złośliwym kodem przywróciła element z kwarantanny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender przywrócił element z kwarantanny. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka&gt;</dt> 
<dt>plikuUżytk: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
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
<b>Platforma ochrony przed złośliwym kodem nie może przywrócić elementu z kwarantanny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby przywrócenia elementu z kwarantanny. Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka&gt;</dt> 
<dt>plikuUżytk: &lt;Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis&gt; błędu Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; &gt;Wersja</dt> 
<dt>definicjiInne wersja: &lt;wersja&gt; Antimalware Engine</dt>
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
<b>Platforma ochrony przed złośliwym kodem usunęła element z kwarantanny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender usunięto element z kwarantanny.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka&gt;</dt> 
<dt>plikuUżytk: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
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
<b>Platforma ochrony przed złośliwym kodem nie może usunąć elementu z kwarantanny.</b>
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
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; Ścieżka&gt;</dt> 
<dt>plikuUżytk: &lt;Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis&gt; błędu Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; &gt;Wersja</dt> 
<dt>definicjiInne wersja: &lt;wersja&gt; Antimalware Engine</dt>
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
<b>Platforma ochrony przed złośliwym kodem usunęła historię złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender usunięto historię złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
<dl>
<dt>Czas: czas wystąpienia zdarzenia, na przykład wtedy, gdy historia jest czyszczona. Ten parametr nie jest używany w zdarzeniach zagrożeń, więc nie ma żadnych pomyłek dotyczących tego, czy jest to czas korygowania, czy czas infekcji. W przypadku tych elementów nazywamy je w szczególności czasem akcji lub czasem wykrywania.</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; Użytkownika&gt;</dt>
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
Platforma ochrony przed złośliwym kodem nie może usunąć historii złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby usunięcia historii złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
<dl>
<dt>Czas: czas wystąpienia zdarzenia, na przykład wtedy, gdy historia jest czyszczona. Ten parametr nie jest używany w zdarzeniach zagrożeń, więc nie ma żadnych pomyłek dotyczących tego, czy jest to czas korygowania, czy czas infekcji. W przypadku tych elementów nazywamy je w szczególności czasem akcji lub czasem wykrywania.</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT. </dt>
<dt>Opis błędu: &lt;Opis&gt; błędu Opis błędu. </dt>
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
<b>Platforma ochrony przed złośliwym kodem wykryła podejrzane zachowanie.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wykryła podejrzane zachowanie.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Wykrywanie źródła&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieci</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;typ&gt; wykrywania, na przykład:<ul>
<li>Heurystyki</li>
<li>Ogólny</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;źródło&gt; wykrywania na przykład:<ul>
<li>Użytkownik: zainicjowany przez użytkownika</li>
<li>System: zainicjowany przez system</li>
<li>W czasie rzeczywistym: inicjowany składnik czasu rzeczywistego</li>
<li>IOAV: Zainicjowano pobieranie i Outlook załączników usługi IE</li>
<li>NIS: System inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; Chroni to przed złośliwymi kontrolkami stron internetowych</li>
<li>Wczesna ochrona przed złośliwym kodem (ELAM). Obejmuje to złośliwe oprogramowanie wykryte przez sekwencję rozruchu</li>
<li>Zdalne zaświadczanie</li>
</ul>Interfejs skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI). Służy głównie do ochrony skryptów (PowerShell, VBS), choć może być wywoływany przez inne firmy, jak również.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess Name: Process in the PIDSignature ID: Enumeration matching severity (Nazwa userprocess&gt;</dt>
<dt>: &lt;proces w identyfikatorze PIDSignature&gt;</dt>
<dt>: wyliczenie pasującej ważności).</dt> 
<dt>Wersja podpisu: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine versionFidelity&gt;</dt> 
<dt>Label:</dt>
<dt>Target File Name: &lt;Nazwa&gt; pliku.</dt>
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
<b>Platforma ochrony przed złośliwym kodem wykryła złośliwe oprogramowanie lub inne potencjalnie niechciane oprogramowanie. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wykryła złośliwe oprogramowanie lub inne potencjalnie niechciane oprogramowanie.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Wykrywanie źródła&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieci</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;typ&gt; wykrywania, na przykład:<ul>
<li>Heurystyki</li>
<li>Ogólny</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;źródło&gt; wykrywania na przykład:<ul>
<li>Użytkownik: zainicjowany przez użytkownika</li>
<li>System: zainicjowany przez system</li>
<li>W czasie rzeczywistym: inicjowany składnik czasu rzeczywistego</li>
<li>IOAV: Zainicjowano pobieranie i Outlook załączników usługi IE</li>
<li>NIS: System inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; Chroni to przed złośliwymi kontrolkami stron internetowych</li>
<li>Wczesna ochrona przed złośliwym kodem (ELAM). Obejmuje to złośliwe oprogramowanie wykryte przez sekwencję rozruchu</li>
<li>Zdalne zaświadczanie</li>
</ul>Interfejs skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI). Służy głównie do ochrony skryptów (PowerShell, VBS), choć może być wywoływany przez inne firmy, jak również.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Nie jest wymagana żadna akcja. Program antywirusowy Microsoft Defender może zawiesić i podjąć rutynowe działania w sprawie tego zagrożenia. Jeśli chcesz ręcznie usunąć zagrożenie, w interfejsie Program antywirusowy Microsoft Defender kliknij pozycję <b>Wyczyść komputer</b>.
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
<b>Platforma ochrony przed złośliwym kodem wykonała akcję ochrony systemu przed złośliwym oprogramowaniem lub innym potencjalnie niepożądanym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender podjęła działania w celu ochrony tej maszyny przed złośliwym oprogramowaniem lub innym potencjalnie niepożądanym oprogramowaniem.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Wykrywanie źródła&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieci</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;typ&gt; wykrywania, na przykład:<ul>
<li>Heurystyki</li>
<li>Ogólny</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;źródło&gt; wykrywania na przykład:<ul>
<li>Użytkownik: zainicjowany przez użytkownika</li>
<li>System: zainicjowany przez system</li>
<li>W czasie rzeczywistym: inicjowany składnik czasu rzeczywistego</li>
<li>IOAV: Zainicjowano pobieranie i Outlook załączników usługi IE</li>
<li>NIS: System inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; Chroni to przed złośliwymi kontrolkami stron internetowych</li>
<li>Wczesna ochrona przed złośliwym kodem (ELAM). Obejmuje to złośliwe oprogramowanie wykryte przez sekwencję rozruchu</li>
<li>Zdalne zaświadczanie</li>
</ul>Interfejs skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI). Służy głównie do ochrony skryptów (PowerShell, VBS), choć może być wywoływany przez inne firmy, jak również.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, na przykład:<ul>
<li>Czyszczenie: zasób został oczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł zostać wykonany/istnieje</li>
<li>Zdefiniowana przez użytkownika: akcja zdefiniowana przez użytkownika, która jest zwykle jedną z tej listy akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blokuj: wykonanie zasobu zostało zablokowane</li>
</ul>
</dt>
<dt>Stan akcji: &lt; Opis dodatkowych akcji&gt;</dt> 
<dt>Kod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; &gt;Wersja</dt> 
<dt>definicjiInne wersja: &lt;Antimalware Engine wersja&gt;</dt> UWAGA: Zawsze, gdy Program antywirusowy Microsoft Defender, Microsoft Security Essentials, Narzędzie do usuwania złośliwego oprogramowania lub System Center Endpoint Protection wykrywa złośliwe oprogramowanie, przywróci następujące ustawienia systemowe i usługi, które mogły ulec zmianie przez złośliwe oprogramowanie:<ul>
<li>Domyślne ustawienie programu Internet Explorer lub Microsoft Edge</li>
<li>Ustawienia Access Control użytkownika</li>
<li>Ustawienia przeglądarki Chrome</li>
<li>Dane kontrolki rozruchu</li>
<li>Ustawienia rejestru regedit i menedżera zadań</li>
<li>Windows Update, usługa inteligentnego transferu w tle i zdalne wywołanie procedury</li>
<li>pliki systemu operacyjnego Windows</li></ul>
Powyższy kontekst ma zastosowanie do następujących wersji klienta i serwera:
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
Windows Vista (z dodatkiem Service Pack 1 lub Dodatkiem Service Pack 2), Windows 7 lub nowszym
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
Żadna akcja nie jest konieczna. Program antywirusowy Microsoft Defender usunięte lub poddane kwarantannie zagrożenie.
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
<b>Platforma ochrony przed złośliwym kodem próbowała wykonać akcję w celu ochrony systemu przed złośliwym oprogramowaniem lub innym potencjalnie niepożądanym oprogramowaniem, ale akcja nie powiodła się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd niekrytyczny podczas podejmowania działań dotyczących złośliwego oprogramowania lub innego potencjalnie niechcianego oprogramowania.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Wykrywanie źródła&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieci</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;typ&gt; wykrywania, na przykład:<ul>
<li>Heurystyki</li>
<li>Ogólny</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;źródło&gt; wykrywania na przykład:<ul>
<li>Użytkownik: zainicjowany przez użytkownika</li>
<li>System: zainicjowany przez system</li>
<li>W czasie rzeczywistym: inicjowany składnik czasu rzeczywistego</li>
<li>IOAV: Zainicjowano pobieranie i Outlook załączników usługi IE</li>
<li>NIS: System inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; Chroni to przed złośliwymi kontrolkami stron internetowych</li>
<li>Wczesna ochrona przed złośliwym kodem (ELAM). Obejmuje to złośliwe oprogramowanie wykryte przez sekwencję rozruchu</li>
<li>Zdalne zaświadczanie</li>
</ul>Interfejs skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI). Służy głównie do ochrony skryptów (PowerShell, VBS), choć może być wywoływany przez inne firmy, jak również.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, na przykład:<ul>
<li>Czyszczenie: zasób został oczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł zostać wykonany/istnieje</li>
<li>Zdefiniowana przez użytkownika: akcja zdefiniowana przez użytkownika, która jest zwykle jedną z tej listy akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blokuj: wykonanie zasobu zostało zablokowane</li>
</ul>
</dt>
<dt>Stan akcji: &lt; Opis dodatkowych akcji&gt;</dt> 
<dt>Kod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; &gt;Wersja</dt> 
<dt>definicjiInnezyna wersja: &lt;wersja&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Żadna akcja nie jest konieczna. Program antywirusowy Microsoft Defender nie można wykonać zadania związanego z korygowanie złośliwego oprogramowania. Nie jest to błąd krytyczny.
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
<b>Platforma ochrony przed złośliwym kodem napotkała błąd krytyczny podczas próby podjęcia działań w sprawie złośliwego oprogramowania lub innego potencjalnie niechcianego oprogramowania. Komunikat o zdarzeniu zawiera więcej szczegółów.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd krytyczny podczas podejmowania działań dotyczących złośliwego oprogramowania lub innego potencjalnie niechcianego oprogramowania.<br/>Aby uzyskać więcej informacji, zobacz następujące artykuły:
<dl>
<dt>Nazwa: &lt; Nazwa&gt;</dt> 
<dt>zagrożeniaID: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Ważność&gt;, na przykład:<ul>
<li>Niskie</li>
<li>Umiarkowane</li>
<li>High (Wysoki)</li>
<li>Ciężkie</li>
</ul>
</dt>
<dt>Kategorii: &lt; Opis&gt; kategorii, na przykład dowolny typ zagrożenia lub złośliwego oprogramowania.</dt> 
<dt>Ścieżka: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Wykrywanie źródła&gt;, na przykład:
<ul>
<li>Unknown</li>
<li>Komputer lokalny</li>
<li>Udział sieci</li>
<li>Internet</li>
<li>Ruch przychodzący</li>
<li>Ruch wychodzący</li>
</ul>
</dt>
<dt>Typ wykrywania: &lt;typ&gt; wykrywania, na przykład:<ul>
<li>Heurystyki</li>
<li>Ogólny</li>
<li>Betonu</li>
<li>Podpis dynamiczny</li>
</ul>
</dt>
<dt>Źródło wykrywania: &lt;źródło&gt; wykrywania na przykład:<ul>
<li>Użytkownik: zainicjowany przez użytkownika</li>
<li>System: zainicjowany przez system</li>
<li>W czasie rzeczywistym: inicjowany składnik czasu rzeczywistego</li>
<li>IOAV: Zainicjowano pobieranie i Outlook załączników usługi IE</li>
<li>NIS: System inspekcji sieci</li>
<li>IEPROTECT: IE — IExtensionValidation; Chroni to przed złośliwymi kontrolkami stron internetowych</li>
<li>Wczesna ochrona przed złośliwym kodem (ELAM). Obejmuje to złośliwe oprogramowanie wykryte przez sekwencję rozruchu</li>
<li>Zdalne zaświadczanie</li>
</ul>Interfejs skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI). Służy głównie do ochrony skryptów (PowerShell, VBS), choć może być wywoływany przez inne firmy, jak również.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, na przykład:<ul>
<li>Czyszczenie: zasób został oczyszczony</li>
<li>Kwarantanna: zasób został poddany kwarantannie</li>
<li>Usuń: zasób został usunięty</li>
<li>Zezwalaj: zasób mógł zostać wykonany/istnieje</li>
<li>Zdefiniowana przez użytkownika: akcja zdefiniowana przez użytkownika, która jest zwykle jedną z tej listy akcji określonych przez użytkownika</li>
<li>Brak akcji: Brak akcji</li>
<li>Blokuj: wykonanie zasobu zostało zablokowane</li>
</ul>
</dt>
<dt>Stan akcji: &lt; Opis dodatkowych akcji&gt;</dt> 
<dt>Kod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; &gt;Wersja</dt> 
<dt>definicjiInnezyna wersja: &lt;wersja&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Klient Program antywirusowy Microsoft Defender napotkał ten błąd z powodu krytycznych problemów. Punkt końcowy może nie być chroniony. Przejrzyj opis błędu, a następnie wykonaj odpowiednie kroki <b>akcji użytkownika</b> poniżej.
<table>
<tr>
<th>Akcja</th>
<th>Akcja użytkownika</th>
</tr>
<tr>
<td>
<b>Usunąć</b>
</td>
<td>
Zaktualizuj definicje, a następnie sprawdź, czy usunięcie zakończyło się pomyślnie.
</td>
</tr>
<tr>
<td>
<b>Czyste</b>
</td>
<td>
Zaktualizuj definicje, a następnie sprawdź, czy korygowanie zakończyło się pomyślnie.
</td>
</tr>
<tr>
<td>
<b>Kwarantanny</b>
</td>
<td>
Zaktualizuj definicje i sprawdź, czy użytkownik ma uprawnienia dostępu do niezbędnych zasobów.
</td>
</tr>
<tr>
<td>
<b>Umożliwić swobodne otworzenie</b>
</td>
<td>
Sprawdź, czy użytkownik ma uprawnienia dostępu do niezbędnych zasobów.
</td>
</tr>
</table>

Jeśli to zdarzenie będzie się powtarzać:<ol>
<li>Uruchom ponownie skanowanie.</li>
<li>Jeśli nie powiedzie się w ten sam sposób, przejdź do <a href="https://go.microsoft.com/fwlink/?LinkId=215163">witryny pomoc techniczna firmy Microsoft</a>, wprowadź numer błędu w polu <b>Wyszukiwania</b>, aby wyszukać kod błędu.</li>
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
<b>Program antywirusowy Microsoft Defender wywnioskowała skróty dla zasobu zagrożenia.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender klient działa w dobrej kondycji.
<dl>
<dt>Bieżąca wersja platformy: &lt; Bieżąca wersja&gt; platformy</dt> 
<dt>Ścieżka zasobu: &lt;PathHashes&gt;</dt>
<dt>: &lt;skróty&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Uwaga: to zdarzenie zostanie zarejestrowane tylko wtedy, gdy zostaną ustawione następujące zasady: <b>ThreatFileHashLogging unsigned</b>.</div>
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
<b>Kontrolowany dostęp do folderów (CFA) zablokował niezaufanemu procesowi wprowadzanie zmian w pamięci. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Kontrolowany dostęp do folderów zablokował proces niezaufany przed potencjalnie modyfikowaniem sektorów dysków.
<br/> Aby uzyskać więcej informacji na temat rekordu zdarzenia, zobacz następujące informacje:
<dl>
<dt>Eventid: &lt; EventID&gt;, na przykład: 1127Wersja</dt>
<dt>: &lt;wersja&gt;, na przykład:</dt> 
<dt>0Poziom: &lt;Poziom&gt;, na przykład: win:</dt>
<dt>WarningTimeCreated: &lt;SystemTime&gt;, czas utworzenia</dt> 
<dt>zdarzeniaEventRecordID: &lt;EventRecordID&gt;, numer indeksu zdarzenia w dzienniku zdarzeń</dt> Identyfikator 
<dt>procesuexecution: &lt;Execution ProcessID&gt;, proces, który wygenerował zdarzenieChannel</dt>
<dt>: &lt;kanał&gt; zdarzeń, na przykład: Microsoft- Windows-Windows Defender/</dt>
<dt>OperationalComputer: &lt;Nazwa&gt;</dt> 
<dt>komputeraZabezpieczenia UserID: &lt;Nazwa produktu UserIDProduct&gt; zabezpieczeń</dt>
<dt>: &lt;nazwa&gt; produktu, na przykład: Program antywirusowy Microsoft Defender</dt> 
<dt>W wersji produktu: &lt;wersja&gt; produktu </dt>
<dt>Czas wykrywania: &lt;czas&gt; wykrywania, czas, kiedy cfa zablokował niezaufany</dt> 
<dt>procesUser: &lt;Domainlt&gt;\&; UserPath&gt;</dt>
<dt>: &lt;Nazwa&gt; urządzenia, nazwa urządzenia lub dysku, do którego uzyskano dostęp niezaufany proces w celu modyfikacjiNazwa</dt> 
<dt>procesu: &lt;ścieżka&gt; procesu, nazwa ścieżki procesu zablokowana przez usługę CFA w celu uzyskania dostępu do urządzenia lub dysku w celu modyfikacjiZabezpieczenia</dt> 
<dt>Intelligence Version: &lt;Security intelligence versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Użytkownik może dodać zablokowany proces do listy <i>Dozwolony proces</i> dla programu CFA przy użyciu programu PowerShell lub centrum Zabezpieczenia Windows.
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
<b>Jeśli platforma ochrony przed złośliwym kodem zgłasza stan do platformy monitorowania, to zdarzenie wskazuje, że platforma ochrony przed złośliwym kodem jest uruchomiona i jest w dobrej kondycji. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender klient działa w dobrej kondycji.
<dl>
<dt>Wersja platformy: &lt; Bieżąca wersja&gt;</dt> 
<dt>platformySignature Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Żadna akcja nie jest konieczna. Klient Program antywirusowy Microsoft Defender jest w dobrej kondycji. To zdarzenie jest zgłaszane co godzinę.
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
<b>Endpoint Protection raport kondycji klienta (czas w utc)</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Raport kondycji klienta programu antywirusowego.
<dl>
<dt>Wersja platformy: &lt; Bieżąca wersja&gt;</dt> 
<dt>platformyInformacje wersji: &lt;Antimalware Engine wersjaSieć&gt;</dt> 
<dt>aparatu inspekcji czasu rzeczywistegoSieć sieciowa &lt;wersja&gt; aparatu inspekcji w czasie rzeczywistym</dt> 
<dt>Wersja podpisu Programu antywirusowego: &lt;wersja sygnatury antywirusowej&gt;</dt> 
<dt>Wersja sygnatury oprogramowania antywirusowego: &lt;Wersja sygnatury antyszpiegowskiejSieć&gt; sygnatury</dt> czasu 
<dt>rzeczywistegoSieć sieciowa wersja podpisu inspekcji: &lt; Network Realtime Inspection signature versionRTP&gt;</dt> 
<dt>state: &lt;Realtime protection state&gt; (Enabled or Disabled)</dt>
<dt>OA state: &lt;On Access state&gt; (Enabled or Disabled)</dt>
<dt>IOAV state: &lt;IE Downloads and Outlook Express Attachments state&gt; (Enabled or Disabled)</dt>
<dt>BM state: &lt;Behavior Monitoring state&gt; (Enabled or Disabled)</dt>
<dt>Antivirus signature age: Antivirus signature age&gt; (&lt;Wiek podpisu antywirusowego)  (w dniach)</dt> 
<dt>Wiek podpisu oprogramowania chroniącego przed złośliwym oprogramowaniem: &lt; Wiek&gt; podpisu oprogramowania chroniącego przed złośliwym oprogramowaniem (w dniach)</dt>
<dt>Ostatni szybki wiek skanowania: &lt;Wiek ostatniego szybkiego skanowania&gt; (w dniach)</dt>
<dt>Ostatni pełny wiek skanowania: &lt;Ostatni pełny wiek&gt; skanowania (w dniach)</dt>
<dt>Czas tworzenia podpisu programu antywirusowego: ?&lt; Czas&gt; tworzenia sygnatury</dt> 
<dt>antywirusowejSygnatura oprogramowania antywirusowegoSygnatura oprogramowania antywirusowego: ?&lt; Czas tworzenia sygnatury oprogramowania chroniącego przed złośliwym oprogramowaniemSkład&gt;</dt> 
<dt>czasu rozpoczęcia szybkiego skanowania: ?&lt; Czas rozpoczęcia&gt; ostatniego szybkiego</dt> 
<dt>skanowaniaSkład czasu zakończenia szybkiego skanowania: ?&lt; Czas zakończenia&gt; ostatniego szybkiego</dt> 
<dt>skanowaniaSadowe źródło szybkiego skanowania: &lt;Ostatnie szybkie źródło&gt; skanowania (0 = skanowanie nie zostało uruchomione, 1 = zainicjowano użytkownika, 2 = zainicjowano system)</dt>
<dt>Czas ostatniego pełnego skanowania: ?&lt; Czas rozpoczęcia&gt; ostatniego pełnego</dt> 
<dt>skanowaniaSkład czasu zakończenia pełnego skanowania: ?&lt; Czas zakończenia&gt; ostatniego pełnego</dt> 
<dt>skanowaniaZdaj pełne źródło skanowania: &lt;Ostatnie pełne źródło&gt; skanowania (0 = skanowanie nie zostało uruchomione, 1 = zainicjowane przez użytkownika, 2 = zainicjowane przez system)</dt>
<dt>Stan produktu: Na potrzeby wewnętrznego rozwiązywania problemów
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
<b>Definicje ochrony przed złośliwym kodem zostały pomyślnie zaktualizowane. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Zaktualizowano wersję sygnatury programu antywirusowego.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja&gt;</dt> 
<dt>podpisuPrevious Signature Version: &lt;Poprzednie wersje&gt;</dt>
<dt> podpisuTyp podpisu: &lt;typ&gt; podpisu, na przykład: <ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Typ aktualizacji: &lt; Typ&gt; aktualizacji— pełny lub delta.</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Bieżąca wersja&gt;</dt> 
<dt>aparatuPrevious Engine Version: &lt;Poprzednia wersja&gt; aparatu</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Żadna akcja nie jest konieczna. Klient Program antywirusowy Microsoft Defender jest w dobrej kondycji. To zdarzenie jest zgłaszane, gdy podpisy są pomyślnie aktualizowane.
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
Program antywirusowy Microsoft Defender napotkał błąd podczas próby zaktualizowania sygnatur.
<dl>
<dt>Nowa wersja analizy zabezpieczeń: &lt; Nowy numer&gt;</dt> 
<dt>wersjiPrevious security intelligence version: &lt;Previous versionUpdate&gt;</dt>
<dt> Source: &lt;Update source&gt;, na przykład:
<ul>
<li>Folder aktualizacji analizy zabezpieczeń</li>
<li>Wewnętrzny serwer aktualizacji analizy zabezpieczeń</li>
<li>Microsoft Update Server</li>
<li>Udział plików</li>
<li>Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem (MMPC)</li>
</ul>
</dt>
<dt>Etap aktualizacji: &lt;etap&gt; aktualizacji, na przykład:
<ul>
<li>Szukaj</li>
<li>Pobierz</li>
<li>Instalowanie</li>
</ul>
</dt>
<dt>Ścieżka źródłowa: nazwa udziału plików dla uniwersalnej konwencji nazewnictwa (UNC), nazwa serwera dla Windows Server Update Services (WSUS)/Microsoft Update/ADL.</dt>
<dt> Typ podpisu: &lt;typ&gt; podpisu, na przykład: <ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Typ aktualizacji: &lt; Typ&gt; aktualizacji— pełny lub delta.</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> Engine Version: Previous engine versionError Code: Error code Result code associated with threat status (Wersja 
<dt>aparatu: &lt;Poprzednia wersja&gt; aparatu</dt> 
<dt>Kod: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia). Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Ten błąd występuje, gdy występuje problem z aktualizowaniem definicji.
Aby rozwiązać ten problem:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Zaktualizuj definicje</a> i wymuś ponowne skanowanie bezpośrednio w punkcie końcowym.</li>
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
<b>Aparat ochrony przed złośliwym kodem został pomyślnie zaktualizowany. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wersja aparatu została zaktualizowana.
<dl>
<dt>Bieżąca wersja aparatu: &lt; Bieżąca wersja aparatuPrevious Engine Version: Previous engine versionEngine Type: Engine type, or antimalware engine or Network Inspection System engine ( Bieżąca wersja&gt; aparatu</dt> aparatu
<dt>: &lt;Poprzednia wersja&gt; aparatu</dt>
<dt>: &lt;Typ&gt; aparatu, aparat ochrony przed złośliwym kodem lub aparat systemu inspekcji sieciowej).</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; Użytkownika&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Żadna akcja nie jest konieczna. Klient Program antywirusowy Microsoft Defender jest w dobrej kondycji. To zdarzenie jest zgłaszane po pomyślnej aktualizacji aparatu ochrony przed złośliwym kodem.
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
<b>Aktualizacja aparatu ochrony przed złośliwym kodem nie powiodła się. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby zaktualizowania aparatu.
<dl>
<dt>Nowa wersja aparatu:</dt>
<dt>Poprzednia wersja aparatu: &lt;Poprzednia wersja&gt; aparatuTyp aparatu</dt>
<dt>: &lt;typ&gt; aparatu, aparat ochrony przed złośliwym kodem lub aparat systemu inspekcji sieci.</dt> 
<dt>Użytkownika: &lt; Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Aktualizacja klienta Program antywirusowy Microsoft Defender nie powiodła się. To zdarzenie występuje, gdy klient nie może się zaktualizować. To zdarzenie jest zwykle spowodowane przerwą w łączności sieciowej podczas aktualizacji.
Aby rozwiązać ten problem:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Zaktualizuj definicje</a> i wymuś ponowne skanowanie bezpośrednio w punkcie końcowym.</li>
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
<b>Wystąpił problem podczas ładowania definicji oprogramowania chroniącego przed złośliwym kodem. Aparat ochrony przed złośliwym kodem podejmie próbę załadowania ostatniego znanego dobrego zestawu definicji.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby załadowania podpisów i spróbuje wrócić do znanego zestawu podpisów.
<dl>
<dt>Próbowano sygnatur:</dt>
<dt>Kod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt> 
<dt>Wersja podpisu: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Wersja&gt; aparatu ochrony przed złośliwym kodem</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Klient Program antywirusowy Microsoft Defender próbował pobrać i zainstalować najnowszy plik definicji i nie powiodło się. Ten błąd może wystąpić, gdy klient napotka błąd podczas próby załadowania definicji lub jeśli plik jest uszkodzony. Program antywirusowy Microsoft Defender spróbuje przywrócić znany zestaw definicji.
Aby rozwiązać ten problem:
<ol>
<li>Uruchom ponownie komputer i spróbuj ponownie.</li>
<li>Pobierz najnowsze definicje z <a href="https://aka.ms/wdsi">witryny Microsoft Security Intelligence</a>.
Uwaga: rozmiar pliku definicji pobranego z witryny może przekraczać 60 MB i nie powinien być używany jako długoterminowe rozwiązanie do aktualizowania definicji.
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
<b>Nie można załadować aparatu ochrony przed złośliwym kodem, ponieważ platforma ochrony przed złośliwym kodem jest nieaktualna. Platforma ochrony przed złośliwym kodem załaduje ostatni znany dobry aparat ochrony przed złośliwym kodem i podejmie próbę aktualizacji.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender nie można załadować aparatu ochrony przed złośliwym kodem, ponieważ bieżąca wersja platformy nie jest obsługiwana. Program antywirusowy Microsoft Defender powróci do ostatniego znanego dobrego aparatu i zostanie podjęta próba aktualizacji platformy.
<dl>
<dt>Bieżąca wersja platformy: &lt;bieżąca wersja platformy&gt;</dt>
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
<dt>Bieżąca wersja platformy: &lt; Bieżąca wersja&gt; platformy</dt> 
<dt>Kod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
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
<b>Platforma wkrótce będzie nieaktualna. Pobierz najnowszą platformę, aby zachować aktualną ochronę.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender wkrótce będzie wymagać nowszej wersji platformy do obsługi przyszłych wersji aparatu ochrony przed złośliwym kodem. Pobierz najnowszą platformę Program antywirusowy Microsoft Defender, aby zachować najlepszy dostępny poziom ochrony.
<dl>
<dt>Bieżąca wersja platformy: &lt;bieżąca wersja platformy&gt;</dt>
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
<b>Aparat ochrony przed złośliwym kodem użył usługi Dynamic Signature Service do uzyskania dodatkowych definicji. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender użyć <i>usługi podpisu dynamicznego</i> do pobrania dodatkowych podpisów w celu ochrony maszyny.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja&gt;</dt>
<dt> podpisuTyp podpisu: &lt;typ&gt; podpisu, na przykład: <ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Bieżąca wersja aparatu: &lt; Bieżąca wersja&gt;</dt>
<dt> aparatuTyp podpisu dynamicznego: &lt;typ&gt; podpisu dynamicznego, na przykład:
<ul>
<li>Wersja</li>
<li>Sygnatury czasowej</li>
<li>Brak limitu</li>
<li>Długość</li>
</ul>
</dt>
<dt>Ścieżka trwałości: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit type&gt;, na przykład:
<ul>
<li>Wersja maszyny wirtualnej</li>
<li>Sygnatury czasowej</li>
<li>Brak limitu</li>
</ul>
</dt>
<dt>Limit trwałości: limit trwałości podpisu fastpath.</dt>
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
<b>Usługa podpisu dynamicznego usunęła nieaktualne definicje dynamiczne. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender <i>używana usługa podpisu dynamicznego</i> do odrzucania przestarzałych podpisów.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja&gt;</dt>
<dt> podpisuTyp podpisu: &lt;typ&gt; podpisu, na przykład: <ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Bieżąca wersja aparatu: &lt; Bieżąca wersja&gt;</dt>
<dt> aparatuTyp podpisu dynamicznego: &lt;typ&gt; podpisu dynamicznego, na przykład:
<ul>
<li>Wersja</li>
<li>Sygnatury czasowej</li>
<li>Brak limitu</li>
<li>Długość</li>
</ul>
</dt>
<dt>Ścieżka trwałości: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Persistence Limit Type: &lt;Persistence limit type&gt;, na przykład:
<ul>
<li>Wersja maszyny wirtualnej</li>
<li>Sygnatury czasowej</li>
<li>Brak limitu</li>
</ul>
</dt>
<dt>Limit trwałości: limit trwałości podpisu fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Żadna akcja nie jest konieczna. Klient Program antywirusowy Microsoft Defender jest w dobrej kondycji. To zdarzenie jest zgłaszane, gdy usługa podpisu dynamicznego pomyślnie usuwa nieaktualne definicje dynamiczne.
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
<b>Aparat ochrony przed złośliwym kodem napotkał błąd podczas próby użycia usługi podpisu dynamicznego. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby użycia <i>usługi podpisu dynamicznego</i>.
<dl>
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja&gt;</dt>
<dt> podpisuTyp podpisu: &lt;typ&gt; podpisu, na przykład: <ul>
<li>Antivirus</li>
<li>Antyspyware</li>
<li>Antimalware</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Bieżąca wersja aparatu: &lt; Bieżąca wersja&gt;</dt> 
<dt>aparatuKod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
<dt> Typ podpisu dynamicznego: &lt;typ podpisu dynamicznego&gt;, na przykład:
<ul>
<li>Wersja</li>
<li>Sygnatury czasowej</li>
<li>Brak limitu</li>
<li>Długość</li>
</ul>
</dt>
<dt>Ścieżka trwałości: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit type&gt;, na przykład:
<ul>
<li>Wersja maszyny wirtualnej</li>
<li>Sygnatury czasowej</li>
<li>Brak limitu</li>
</ul>
</dt>
<dt>Limit trwałości: limit trwałości podpisu fastpath.</dt>
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
<b>Usługa podpisu dynamicznego usunęła wszystkie definicje dynamiczne. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender odrzucić wszystkie podpisy <i>usługi podpisu dynamicznego</i>.
<dl>
<dt>Bieżąca wersja podpisu: &lt;bieżąca wersja podpisu&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Identyfikator zdarzenia: 2020 r.</th>
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
<b>Aparat ochrony przed złośliwym kodem pobrał czysty plik. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender pobrany czysty plik.
<dl>
<dt>Pod nazwą: &lt; Nazwa&gt; pliku.</dt> 
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja&gt;</dt> 
<dt>sygnaturyBieżna wersja aparatu: &lt;bieżąca wersja&gt; aparatu</dt>
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
<b>Aparat ochrony przed złośliwym kodem nie może pobrać czystego pliku. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby pobrania czystego pliku.
<dl>
<dt>Pod nazwą: &lt; Nazwa&gt; pliku.</dt> 
<dt>Bieżąca wersja podpisu: &lt; Bieżąca wersja&gt;</dt> 
<dt>sygnaturyWersja aparatu współbieżnego: &lt;Bieżąca wersja&gt;</dt> 
<dt>aparatuKod błędu: &lt;kod&gt; błędu Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Sprawdź ustawienia łączności internetowej.
Klient Program antywirusowy Microsoft Defender napotkał błąd podczas korzystania z usługi podpisu dynamicznego w celu pobrania najnowszych definicji do określonego zagrożenia. Ten błąd jest prawdopodobnie spowodowany problemem z łącznością sieciową.
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
<b>Aparat ochrony przed złośliwym kodem został pobrany i jest skonfigurowany do uruchamiania w trybie offline po następnym ponownym uruchomieniu systemu.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender pobrany i skonfigurowany program antywirusowy w trybie offline do uruchomienia przy następnym ponownym uruchomieniu.
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
<b>Aparat ochrony przed złośliwym kodem nie może pobrać i skonfigurować skanowania w trybie offline.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender napotkał błąd podczas próby pobrania i skonfigurowania programu antywirusowego w trybie offline.
<dl>
<dt>Kod błędu: &lt; Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
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
<b>Obsługa ochrony przed złośliwym kodem dla tej wersji systemu operacyjnego wkrótce się zakończy. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Obsługa systemu operacyjnego wkrótce wygaśnie. Uruchamianie Program antywirusowy Microsoft Defender w systemie operacyjnym braku obsługi nie jest odpowiednim rozwiązaniem do ochrony przed zagrożeniami.
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
<b>Obsługa oprogramowania chroniącego przed złośliwym kodem dla tego systemu operacyjnego została zakończona. Aby zapewnić dalszą pomoc techniczną, należy uaktualnić system operacyjny. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Obsługa systemu operacyjnego wygasła. Uruchamianie Program antywirusowy Microsoft Defender w systemie operacyjnym braku obsługi nie jest odpowiednim rozwiązaniem do ochrony przed zagrożeniami.
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
<b>Aparat ochrony przed złośliwym kodem nie obsługuje już tego systemu operacyjnego i nie chroni już systemu przed złośliwym oprogramowaniem. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Obsługa systemu operacyjnego wygasła. Program antywirusowy Microsoft Defender nie jest już obsługiwana w systemie operacyjnym, przestała działać i nie chroni przed zagrożeniami złośliwym oprogramowaniem.
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
funkcja Program antywirusowy Microsoft Defender Real-Time Protection napotkała błąd i nie powiodła się.
<dl>
<dt>Funkcja: &lt;Funkcja&gt;, na przykład:
<ul>
<li>Przy dostępie</li>
<li>Pliki do pobrania programu Internet Explorer i załączniki microsoft Outlook Express</li>
<li>Monitorowanie zachowania</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Kod błędu: &lt; Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt> 
<dt>Przyczyna: przyczyna ponownego uruchomienia funkcji Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Należy ponownie uruchomić system, a następnie uruchomić pełne skanowanie, ponieważ możliwe, że system nie był chroniony przez pewien czas.
Funkcja ochrony klienta Program antywirusowy Microsoft Defender w czasie rzeczywistym napotkała błąd, ponieważ nie można uruchomić jednej z usług.
Jeśli po nim następuje identyfikator zdarzenia 3007, błąd był tymczasowy, a klient ochrony przed złośliwym kodem został odzyskany po awarii.
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
<b>Ochrona w czasie rzeczywistym odzyskana po awarii. Zalecamy przeprowadzenie pełnego skanowania systemu po wyświetleniu tego błędu. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender ochrona w czasie rzeczywistym ponownie uruchomiła funkcję. Zaleca się uruchomienie pełnego skanowania systemu w celu wykrycia wszelkich elementów, które mogły zostać pominięte, gdy ten agent nie działa.
<dl>
<dt>Funkcja: &lt;Funkcja&gt;, na przykład:
<ul>
<li>Przy dostępie</li>
<li>Pliki do pobrania IE i załączniki Outlook Express</li>
<li>Monitorowanie zachowania</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Przyczyna: przyczyna ponownego uruchomienia funkcji Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Funkcja ochrony w czasie rzeczywistym została ponownie uruchomiona. Jeśli to zdarzenie wystąpi ponownie, skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">pomocą techniczną firmy Microsoft</a>.
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
<b>Włączono ochronę w czasie rzeczywistym. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender włączono skanowanie ochrony w czasie rzeczywistym pod kątem złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania.
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
Program antywirusowy Microsoft Defender skanowanie ochrony w czasie rzeczywistym pod kątem złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania zostało wyłączone.
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
<b>Konfiguracja ochrony w czasie rzeczywistym została zmieniona. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender konfiguracja funkcji ochrony w czasie rzeczywistym została zmieniona.
<dl>
<dt>Funkcja: &lt;Funkcja&gt;, na przykład:
<ul>
<li>Przy dostępie</li>
<li>Pliki do pobrania IE i załączniki Outlook Express</li>
<li>Monitorowanie zachowania</li>
<li>System inspekcji sieci</li>
</ul>
</dt>
<dt>Konfiguracji: </dt>
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
<b>Konfiguracja platformy ochrony przed złośliwym kodem uległa zmianie.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender konfiguracja uległa zmianie. Jeśli jest to nieoczekiwane zdarzenie, należy przejrzeć ustawienia, ponieważ może to być wynikiem złośliwego oprogramowania.
<dl>
<dt>Stara wartość: &lt; Stary numer&gt; wartości Stara wartość konfiguracji programu antywirusowego.</dt> 
<dt>Nowa wartość: &lt; Nowy numer&gt; wartości Nowa wartość konfiguracji programu antywirusowego.</dt>
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
<b>Aparat ochrony przed złośliwym kodem napotkał błąd i uległ awarii.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender aparat został zakończony z powodu nieoczekiwanego błędu.
<dl>
<dt>Typ błędu: &lt; Typ&gt; błędu, na przykład: Crash lub</dt> 
<dt>HangException Code: &lt;Error codeResource&gt;</dt>
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
<li>W przypadku oprogramowania chroniącego przed złośliwym kodem, oprogramowania antywirusowego i programów szpiegujących w wierszu polecenia z podwyższonym poziomem uprawnień wpisz <b>net stop msmpsvc</b>, a następnie wpisz <b>net start msmpsvc</b> , aby ponownie uruchomić aparat ochrony przed złośliwym kodem.</li>
<li>W przypadku <i>systemu inspekcji sieci</i> w wierszu polecenia z podwyższonym poziomem uprawnień wpisz <b>net start nissrv</b>, a następnie wpisz <b>net start nissrv</b> , aby ponownie uruchomić aparat <i>systemu inspekcji sieci</i> przy użyciu pliku NiSSRV.exe.
</li>
</ul>
</li>
<li>Jeśli nie powiedzie się w ten sam sposób, wyszukaj kod błędu, uzyskując dostęp do <a href="https://go.microsoft.com/fwlink/?LinkId=215163">witryny pomoc techniczna firmy Microsoft</a> i wprowadzając numer błędu w polu <b>Wyszukaj</b>, a następnie skontaktuj się z <a href="https://go.microsoft.com/fwlink/?LinkId=215491">pomocą techniczną firmy Microsoft</a>.</li>
</ol>
</td>
</tr>
<tr>
<td>
Akcja użytkownika:
</td>
<td >
Aparat klienta Program antywirusowy Microsoft Defender został zatrzymany z powodu nieoczekiwanego błędu.
Aby rozwiązać ten problem:
<ol>
<li>Uruchom ponownie skanowanie.</li>
<li>Jeśli nie powiedzie się w ten sam sposób, przejdź do <a href="https://go.microsoft.com/fwlink/?LinkId=215163">witryny pomoc techniczna firmy Microsoft</a>, wprowadź numer błędu w polu <b>Wyszukiwania</b>, aby wyszukać kod błędu.</li>
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
<b>Skanowanie pod kątem złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania jest włączone. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender skanowanie pod kątem złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania zostało włączone.
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
<b>Skanowanie pod kątem złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania jest wyłączone.</b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender skanowanie pod kątem złośliwego oprogramowania i innego potencjalnie niechcianego oprogramowania jest wyłączone.
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
Program antywirusowy Microsoft Defender skanowanie w poszukiwaniu wirusów zostało włączone.
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
Jeśli ochrona przed naruszeniami jest włączona, każda próba zmiany dowolnego ustawienia usługi Defender, jeśli zostanie zablokowana, i zostanie wygenerowany identyfikator zdarzenia 5013, który określa, która zmiana ustawienia została zablokowana.
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
<b>Platforma ochrony przed złośliwym kodem wkrótce wygaśnie. </b>
</td>
</tr>
<tr>
<td>
Opis:
</td>
<td >
Program antywirusowy Microsoft Defender weszła w okres prolongaty i wkrótce wygaśnie. Po wygaśnięciu program wyłączy ochronę przed wirusami, programami szpiegującymi i innym potencjalnie niepożądanym oprogramowaniem.
<dl>
<dt>Przyczyna wygaśnięcia: przyczyna wygaśnięcia Program antywirusowy Microsoft Defender.</dt> 
<dt>Data wygaśnięcia: data wygaśnięcia Program antywirusowy Microsoft Defender.</dt>
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
<b>Platforma ochrony przed złośliwym kodem wygasła. </b>
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
<dt>Kod błędu: &lt;Kod błędu&gt; Kod wyniku skojarzony ze stanem zagrożenia. Standardowe wartości HRESULT.</dt> 
<dt>Opis błędu: &lt; Opis&gt; błędu Opis błędu. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Program antywirusowy Microsoft Defender kody błędów klienta Jeśli Program antywirusowy Microsoft Defender wystąpią jakiekolwiek problemy, zwykle będziesz dawać kod błędu ułatwiający rozwiązanie problemu. Najczęściej błąd oznacza, że wystąpił problem z zainstalowaniem aktualizacji.
Ta sekcja zawiera następujące informacje o błędach Program antywirusowy Microsoft Defender klienta.
- Kod - błędu Możliwa przyczyna błędu - Porady dotyczące tego, co należy teraz zrobić

Informacje zawarte w tych tabelach ułatwiają rozwiązywanie problemów z kodami błędów Program antywirusowy Microsoft Defender.


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
Ten błąd wskazuje, że może zabraknąć pamięci.
</td>
</tr>
<tr>
<td>Rozwiązanie</td>
<td>
<ol>
<li>Sprawdź dostępną pamięć na urządzeniu.</li>
<li>Zamknij wszystkie nieużywane aplikacje, które są uruchomione w celu zwolnienia pamięci na urządzeniu.</li>
<li>Uruchom ponownie urządzenie i uruchom skanowanie ponownie.
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
Ten błąd wskazuje, że może wystąpić problem z produktem zabezpieczającym.
</td>
</tr><tr><td>Rozwiązanie</td><td>
<ol>
<li>Zaktualizuj definicje. Albo:<ol>
<li>Pobierz aktualizacje analizy zabezpieczeń w aplikacji Zabezpieczenia Windows. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Lub
</li>
<li>Pobierz najnowsze definicje z <a href="https://aka.ms/wdsi">witryny Microsoft Security Intelligence</a>.
Uwaga: rozmiar pliku definicji pobranego z witryny może przekraczać 60 MB i nie powinien być używany jako długoterminowe rozwiązanie do aktualizowania definicji.
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
Ten błąd wskazuje, że może wystąpić błąd konfiguracji aparatu; często jest to związane z danymi wejściowymi, które nie umożliwiają prawidłowego działania aparatu.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x805080211
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że Program antywirusowy Microsoft Defender nie można poddać kwarantannie zagrożenia.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508022
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że do ukończenia usuwania zagrożeń jest wymagany ponowny rozruch.
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
Ten błąd wskazuje, że zagrożenie może już nie być obecne na nośniku lub złośliwe oprogramowanie może uniemożliwić skanowanie urządzenia.
</tr><tr><td>Rozwiązanie
</td>
<td>
Uruchom <a href="https://www.microsoft.com/security/scanner/default.aspx">Skaner bezpieczeństwa Microsoft</a> następnie zaktualizuj oprogramowanie zabezpieczające i spróbuj ponownie.
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
Ten błąd wskazuje, że ręczne kroki są wymagane do ukończenia usuwania zagrożeń.
</td></tr><tr><td>Rozwiązanie</td><td>
Wykonaj kroki ręcznego korygowania opisane w <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">Encyklopedii ochrony przed złośliwym oprogramowaniem firmy Microsoft</a>. Link specyficzny dla zagrożenia można znaleźć w historii zdarzeń.<br/></td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508026
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że usunięcie wewnątrz typu kontenera może nie być obsługiwane.
</td></tr><tr><td>Rozwiązanie</td><td>
Program antywirusowy Microsoft Defender nie może korygować zagrożeń wykrytych w archiwum. Rozważ ręczne usunięcie wykrytych zasobów.
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
Ten błąd wskazuje, że wymagane jest ponowne skanowanie zagrożenia.
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
Uruchom Program antywirusowy Microsoft Defender offline. Informacje o tym, jak to zrobić, można przeczytać w <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">artykule Program antywirusowy Microsoft Defender offline</a>.
</td>
</tr>
<tr>
<th colspan="2">Kod błędu: 0x80508031
</th>
</tr><tr><td>Komunikat</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Możliwa przyczyna</td>
<td>
Ten błąd wskazuje, że Program antywirusowy Microsoft Defender nie obsługuje bieżącej wersji platformy i wymaga nowej wersji platformy.
</td></tr><tr><td>Rozwiązanie</td><td>
Można używać tylko Program antywirusowy Microsoft Defender w Windows 10 i Windows 11. W przypadku Windows 8, Windows 7 i Windows Vista można użyć <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">System Center Endpoint Protection</a>.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Podczas testowania wewnętrznego Program antywirusowy Microsoft Defender są używane następujące kody błędów.

Jeśli widzisz te błędy, możesz spróbować [zaktualizować definicje](manage-updates-baselines-microsoft-defender-antivirus.md) i wymusić ponowne skanowanie bezpośrednio w punkcie końcowym.


<table>
<tr>
<th colspan="3">Wewnętrzne kody błędów</th>
</tr>
<tr>
<th><b>Kod błędu</b></th>
<th>Wyświetlony komunikat</th>
<th>Możliwa przyczyna błędu i rozwiązania</th>
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
Jest to błąd wewnętrzny. Może on zostać wyzwolony, gdy usuwanie złośliwego oprogramowania nie powiedzie się.
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
Jest to błąd wewnętrzny. Mógł zostać wyzwolony, gdy skanowanie nie powiedzie się.
</td>
</tr>
</table>

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)


## <a name="related-topics"></a>Tematy pokrewne

- [Raport dotyczący ochrony Program antywirusowy Microsoft Defender](report-monitor-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
