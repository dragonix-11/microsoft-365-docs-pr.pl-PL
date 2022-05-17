---
title: Wykonaj akcje odpowiedzi na urządzeniu w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Wykonaj akcje reagowania na urządzeniu, takie jak izolowanie urządzeń, zbieranie pakietu badania, zarządzanie tagami, uruchamianie skanowania av i ograniczanie wykonywania aplikacji.
keywords: odpowiadanie, izolowanie, izolowanie urządzenia, zbieranie pakietu badania, centrum akcji, ograniczanie, zarządzanie tagami, skanowanie av, ograniczanie aplikacji
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f290af2808db1aa56f39593ec4f9fac68c0f76d8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438822"
---
# <a name="take-response-actions-on-a-device"></a>Wykonaj akcje odpowiedzi na urządzeniu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [plany Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](defender-endpoint-plan-1-2.md)
- [Microsoft Defender dla Firm](/microsoft-365/security/defender-business/mdb-overview)

Szybkie reagowanie na wykryte ataki przez izolowanie urządzeń lub zbieranie pakietu badania. Po wykonaniu akcji na urządzeniach możesz sprawdzić szczegóły działania w Centrum akcji.

Akcje odpowiedzi są uruchamiane w górnej części określonej strony urządzenia i obejmują:

- Zarządzaj tagami
- Inicjowanie zautomatyzowanego badania
- Inicjowanie sesji odpowiedzi na żywo
- Zbieraj pakiet badań
- Uruchomiono skanowanie antywirusowe
- Ogranicz wykonanie aplikacji
- Izolowanie urządzenia
- Konsultuj się z ekspertem ds. zagrożeń
- Centrum akcji

[![Obraz akcji odpowiedzi.](images/response-actions.png)](images/response-actions.png#lightbox)

> [!IMPORTANT]
> [Usługa Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) i [Microsoft Defender dla Firm](../defender-business/mdb-overview.md) obejmują tylko następujące ręczne akcje odpowiedzi:
> - Uruchomiono skanowanie antywirusowe
> - Izolowanie urządzenia
> - Zatrzymywanie i kwarantanna pliku
> - Dodaj wskaźnik, aby zablokować lub zezwolić na plik Twoja subskrypcja musi zawierać usługę Defender for Endpoint Plan 2, aby wszystkie akcje odpowiedzi zostały opisane w tym artykule.

 Strony urządzeń można znaleźć w dowolnym z następujących widoków:

- **Pulpit nawigacyjny operacji zabezpieczeń** — wybierz nazwę urządzenia z karty Urządzenia zagrożone.
- **Kolejka alertów** - z kolejki alertów wybierz nazwę urządzenia obok ikony urządzenia.
- **Lista urządzeń** — wybierz nagłówek nazwy urządzenia z listy urządzeń.
- **Pole wyszukiwania** - wybierz pozycję Urządzenie z menu rozwijanego i wprowadź nazwę urządzenia.

> [!IMPORTANT]
> - Te akcje odpowiedzi są dostępne tylko dla urządzeń w Windows 10 w wersji 1703 lub nowszej, Windows 11, Windows Server 2019 i Windows Server 2022.
> - W przypadku platform innych niż Windows możliwości reagowania (takie jak izolacja urządzeń) są zależne od możliwości innych firm.
> - W przypadku agentów pierwszej firmy Microsoft zapoznaj się z linkiem "więcej informacji" w ramach każdej funkcji, aby uzyskać minimalne wymagania dotyczące systemu operacyjnego.

## <a name="manage-tags"></a>Zarządzaj tagami

Dodaj tagi lub zarządzaj nimi, aby utworzyć przynależność do grupy logicznej. Tagi urządzeń obsługują prawidłowe mapowanie sieci, pozwalając na dołączanie różnych tagów w celu przechwycenia kontekstu i umożliwienia dynamicznego tworzenia listy w ramach zdarzenia.

Aby uzyskać więcej informacji na temat tagowania urządzeń, zobacz [Tworzenie tagów urządzeń i zarządzanie nimi](machine-tags.md).

## <a name="initiate-automated-investigation"></a>Inicjowanie zautomatyzowanego badania

W razie potrzeby możesz rozpocząć nowe automatyczne badanie ogólnego przeznaczenia na urządzeniu. Gdy badanie jest uruchomione, wszelkie inne alerty wygenerowane na urządzeniu zostaną dodane do trwającego zautomatyzowanego badania do czasu zakończenia tego badania. Ponadto jeśli to samo zagrożenie jest widoczne na innych urządzeniach, te urządzenia zostaną dodane do badania.

Aby uzyskać więcej informacji na temat zautomatyzowanych badań, zobacz [Omówienie zautomatyzowanych dochodzeń](automated-investigations.md).

## <a name="initiate-live-response-session"></a>Inicjowanie sesji odpowiedzi na żywo

Odpowiedź na żywo to funkcja, która zapewnia natychmiastowy dostęp do urządzenia przy użyciu zdalnego połączenia powłoki. Daje to możliwość wykonywania szczegółowych działań dochodzeniowych i podejmowania natychmiastowych działań reagowania w celu szybkiego powstrzymania zidentyfikowanych zagrożeń w czasie rzeczywistym.

Reagowanie na żywo ma na celu usprawnienie badań dzięki umożliwieniu zbierania danych kryminalistycznych, uruchamiania skryptów, wysyłania podejrzanych jednostek do analizy, korygowania zagrożeń i proaktywnego wyszukiwania pojawiających się zagrożeń.

Aby uzyskać więcej informacji na temat odpowiedzi na żywo, zobacz [Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo](live-response.md).

## <a name="collect-investigation-package-from-devices"></a>Zbieranie pakietu badania z urządzeń

W ramach procesu badania lub odpowiedzi można zebrać pakiet badania z urządzenia. Zbierając pakiet badania, możesz zidentyfikować bieżący stan urządzenia i dokładniej zrozumieć narzędzia i techniki używane przez osobę atakującą.

> [!IMPORTANT]
>
>Te akcje nie są obecnie obsługiwane w przypadku macOS i Linux. Użyj odpowiedzi na żywo, aby uruchomić akcję. Aby uzyskać więcej informacji na temat odpowiedzi na żywo, zobacz [Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo](live-response.md)

Aby pobrać pakiet (plik Zip) i zbadać zdarzenia, które wystąpiły na urządzeniu

1. Wybierz pozycję **Zbierz pakiet badania** z wiersza akcji odpowiedzi w górnej części strony urządzenia.

2. W polu tekstowym określ, dlaczego chcesz wykonać tę akcję. Wybierz pozycję **Potwierdź**.

3. Plik zip zostanie pobrany

Alternatywny sposób:

1. Wybierz pozycję **Centrum akcji** w sekcji akcji odpowiedzi na stronie urządzenia.

   :::image type="content" source="images/action-center-package-collection.png" alt-text="Opcja Centrum akcji" lightbox="images/action-center-package-collection.png":::

2. W wysuwanym centrum akcji wybierz pozycję **Pakiet dostępny do** pobrania pliku zip.

   :::image type="content" source="images/collect-package.png" alt-text="Opcja pobierania pakietu" lightbox="images/collect-package.png":::

Pakiet zawiera następujące foldery:

|Folder|Opis|
|---|---|
|Autoruns|Zawiera zestaw plików, z których każdy reprezentuje zawartość rejestru znanego punktu wejścia automatycznego (ASEP), aby ułatwić identyfikację trwałości osoby atakującej na urządzeniu. <p> <div class="alert"><b>UWAGA:</b> Jeśli klucz rejestru nie zostanie znaleziony, plik będzie zawierać następujący komunikat: "BŁĄD: System nie mógł odnaleźć określonego klucza lub wartości rejestru".<div>|
|Zainstalowane programy|Ten plik .CSV zawiera listę zainstalowanych programów, które mogą pomóc w określeniu, co jest obecnie zainstalowane na urządzeniu. Aby uzyskać więcej informacji, zobacz [klasa Win32_Product](https://go.microsoft.com/fwlink/?linkid=841509).|
|Połączenia sieciowe|Ten folder zawiera zestaw punktów danych związanych z informacjami o łączności, które mogą pomóc w identyfikowaniu łączności z podejrzanymi adresami URL, infrastruktury poleceń i kontroli osoby atakującej (C&C), wszelkich ruchów bocznych lub połączeń zdalnych. <ul><li>ActiveNetConnections.txt: wyświetla statystyki protokołu i bieżące połączenia sieciowe TCP/IP. Umożliwia wyszukiwanie podejrzanych połączeń wykonanych przez proces.</li><li>Arp.txt: wyświetla bieżące tabele pamięci podręcznej protokołu rozpoznawania adresów (ARP) dla wszystkich interfejsów. Pamięć podręczna ARP może ujawnić inne hosty w sieci, które zostały naruszone lub podejrzane systemy w sieci, które mogły zostać użyte do uruchomienia ataku wewnętrznego.</il><li>DnsCache.txt: wyświetla zawartość pamięci podręcznej programu rozpoznawania nazw klienta DNS, która obejmuje zarówno wpisy wstępnie załadowane z lokalnego pliku hostów, jak i wszystkie ostatnio uzyskane rekordy zasobów dla zapytań nazw rozpoznawanych przez komputer. Może to pomóc w identyfikowaniu podejrzanych połączeń.</li><li>IpConfig.txt: wyświetla pełną konfigurację protokołu TCP/IP dla wszystkich kart. Karty mogą reprezentować interfejsy fizyczne, takie jak zainstalowane karty sieciowe lub interfejsy logiczne, takie jak połączenia telefoniczne.</li><li>FirewallExecutionLog.txt i pfirewall.log</li></ul><p><div class="alert"><b>UWAGA:</b> Plik pfirewall.log musi istnieć w pliku %windir%\system32\logfiles\firewall\pfirewall.log, więc zostanie uwzględniony w pakiecie badania. Aby uzyskać więcej informacji na temat tworzenia pliku dziennika zapory, zobacz [Konfigurowanie Zapora Windows Defender za pomocą zaawansowanego dziennika zabezpieczeń](/windows/security/threat-protection/windows-firewall/configure-the-windows-firewall-log)<div>|
|Pliki wstępne|Windows pliki wstępne zostały zaprojektowane w celu przyspieszenia procesu uruchamiania aplikacji. Może służyć do śledzenia wszystkich plików ostatnio używanych w systemie i znajdowania śladów dla aplikacji, które mogły zostać usunięte, ale nadal można je znaleźć na wstępnej liście plików. <ul><li>Folder prefetch: zawiera kopię plików prefetch z `%SystemRoot%\Prefetch`programu . UWAGA: Zaleca się pobranie podglądu plików wstępnych w celu wyświetlenia plików wstępnych.</li><li>PrefetchFilesList.txt: zawiera listę wszystkich skopiowanych plików, których można użyć do śledzenia, jeśli wystąpiły błędy kopiowania do folderu wstępnego.</li></ul>|
|Procesów|Zawiera plik .CSV zawierający listę uruchomionych procesów i umożliwia identyfikowanie bieżących procesów uruchomionych na urządzeniu. Może to być przydatne podczas identyfikowania podejrzanego procesu i jego stanu.|
|Zaplanowane zadania|Zawiera plik .CSV zawierający listę zaplanowanych zadań, które mogą służyć do identyfikowania procedur wykonywanych automatycznie na wybranym urządzeniu w celu wyszukiwania podejrzanego kodu, który został skonfigurowany do automatycznego uruchamiania.|
|Dziennik zdarzeń zabezpieczeń|Zawiera dziennik zdarzeń zabezpieczeń, który zawiera rekordy aktywności logowania lub wylogowania lub inne zdarzenia związane z zabezpieczeniami określone przez zasady inspekcji systemu. <p><div class="alert"><b>UWAGA:</b> Otwórz plik dziennika zdarzeń przy użyciu przeglądarki zdarzeń.</div>|
|Usług|Zawiera plik .CSV, który zawiera listę usług i ich stanów.|
|sesje bloku komunikatów serwera Windows (SMB)|Wyświetla udostępniony dostęp do plików, drukarek i portów szeregowych oraz różne komunikacje między węzłami w sieci. Może to pomóc w identyfikacji eksfiltracji danych lub przenoszenia bocznego. <p> Zawiera pliki dla SMBInboundSessions i SMBOutboundSession. <p> <div class="alert"><b>UWAGA:</b> Jeśli nie ma żadnych sesji (przychodzących lub wychodzących), otrzymasz plik tekstowy z informacją, że nie znaleziono żadnych sesji SMB.</div>|
|Informacje o systemie|Zawiera plik SystemInformation.txt zawierający informacje o systemie, takie jak wersja systemu operacyjnego i karty sieciowe.|
|Katalogi tymczasowe|Zawiera zestaw plików tekstowych zawierający listę plików znajdujących się w %Temp% dla każdego użytkownika w systemie. <p> Może to pomóc w śledzeniu podejrzanych plików, które osoba atakująca mogła porzucić w systemie. <p> <div class="alert"><b>UWAGA:</b> Jeśli plik zawiera następujący komunikat: "System nie może odnaleźć określonej ścieżki", oznacza to, że nie ma katalogu tymczasowego dla tego użytkownika i może to być spowodowane tym, że użytkownik nie zalogował się do systemu.</div>|
|Użytkownicy i grupy|Zawiera listę plików, z których każdy reprezentuje grupę i jej członków.|
|Dzienniki WdSupportLogs|Udostępnia MpCmdRunLog.txt i MPSupportFiles.cab  <p> <div class="alert"><b>UWAGA:</b> Ten folder zostanie utworzony tylko w Windows 10 w wersji 1709 lub nowszej z pakietem zbiorczym aktualizacji z lutego 2020 r. lub nowszym zainstalowanym: <ul><li>Kompilacja Win10 1709 (RS3) 16299.1717: [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)</li><li>Win10 1803 (RS4) Kompilacja 17134.1345: [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)</li><li>Kompilacja Win10 1809 (RS5) 17763.1075: [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)</li><li>Win10 1903/1909 (19h1/19h2) Kompilacje 18362.693 i 18363.693: [KB4535996](https://support.microsoft.com/help/4535996/windows-10-update-kb4535996)</li></ul> </div>|
|CollectionSummaryReport.xls|Ten plik jest podsumowaniem kolekcji pakietów badania, zawiera listę punktów danych, polecenie używane do wyodrębniania danych, stan wykonywania i kod błędu w przypadku niepowodzenia. Ten raport służy do śledzenia, czy pakiet zawiera wszystkie oczekiwane dane i określenia, czy wystąpiły błędy.|
|

## <a name="run-microsoft-defender-antivirus-scan-on-devices"></a>Uruchamianie skanowania Program antywirusowy Microsoft Defender na urządzeniach

W ramach procesu badania lub reagowania można zdalnie zainicjować skanowanie antywirusowe, aby ułatwić identyfikowanie i korygowanie złośliwego oprogramowania, które może znajdować się na urządzeniu, których zabezpieczenia zostały naruszone.

> [!IMPORTANT]
> - Ta akcja nie jest obecnie obsługiwana w przypadku macOS i Linux. Użyj odpowiedzi na żywo, aby uruchomić akcję. Aby uzyskać więcej informacji na temat odpowiedzi na żywo, zobacz [Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo](live-response.md)
> - Skanowanie Program antywirusowy Microsoft Defender (Microsoft Defender AV) może być uruchamiane wraz z innymi rozwiązaniami antywirusowymi, niezależnie od tego, czy usługa Microsoft Defender AV jest aktywnym rozwiązaniem antywirusowym, czy nie. Usługa Microsoft Defender AV może być w trybie pasywnym. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender zgodność](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

Wybierz opcję **Uruchom skanowanie antywirusowe**, wybierz typ skanowania, który chcesz uruchomić (szybkie lub pełne), a następnie dodaj komentarz przed potwierdzeniem skanowania.

:::image type="content" source="images/run-antivirus.png" alt-text="Powiadomienie umożliwiające wybranie szybkiego skanowania lub pełnego skanowania i dodanie komentarza" lightbox="images/run-antivirus.png":::

Centrum akcji wyświetli informacje o skanowaniu, a oś czasu urządzenia będzie zawierać nowe zdarzenie, co odzwierciedla, że akcja skanowania została przesłana na urządzeniu. Alerty usługi Microsoft Defender AV będą odzwierciedlać wszelkie wykrycia, które pojawiły się podczas skanowania.

> [!NOTE]
> Podczas wyzwalania skanowania przy użyciu akcji odpowiedzi usługi Defender for Endpoint wartość "ScanAvgCPULoadFactor" programu antywirusowego Microsoft Defender nadal ma zastosowanie i ogranicza wpływ skanowania na procesor CPU.
> Jeśli funkcja ScanAvgCPULoadFactor nie jest skonfigurowana, wartość domyślna to limit maksymalnego obciążenia procesora CPU wynoszący 50% podczas skanowania.
> Aby uzyskać więcej informacji, zobacz [configure-advanced-scan-types-microsoft-defender-antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-advanced-scan-types-microsoft-defender-antivirus).

## <a name="restrict-app-execution"></a>Ogranicz wykonanie aplikacji

Oprócz powstrzymania ataku przez zatrzymanie złośliwych procesów można również zablokować urządzenie i zapobiec kolejnym próbom uruchomienia potencjalnie złośliwych programów.

>[!IMPORTANT]
> - Ta akcja jest dostępna dla urządzeń w Windows 10, wersji 1709 lub nowszej, Windows 11 i Windows Server 2016. 
> - Ta funkcja jest dostępna, jeśli organizacja używa Program antywirusowy Microsoft Defender.
> - Ta akcja musi spełniać Windows Defender formaty zasad integralności kodu kontroli aplikacji i wymagania dotyczące podpisywania. Aby uzyskać więcej informacji, zobacz [Formaty zasad integralności kodu i podpisywanie](/windows/security/threat-protection/windows-defender-application-control/use-code-signing-to-simplify-application-control-for-classic-windows-applications)).

Aby ograniczyć uruchamianie aplikacji, stosowane są zasady integralności kodu, które zezwalają na uruchamianie plików tylko wtedy, gdy są podpisane przez certyfikat wystawiony przez firmę Microsoft. Ta metoda ograniczenia może pomóc uniemożliwić atakującemu kontrolowanie naruszeń urządzeń i wykonywanie dalszych złośliwych działań.

> [!NOTE]
> W dowolnym momencie będzie można odwrócić ograniczenie uruchamiania aplikacji. Przycisk na stronie urządzenia zmieni się na **Usuń ograniczenia aplikacji**, a następnie wykonasz te same kroki, co ograniczenie wykonywania aplikacji.

Po wybraniu pozycji **Ogranicz wykonywanie aplikacji** na stronie urządzenia wpisz komentarz i wybierz pozycję **Potwierdź**. Centrum akcji wyświetli informacje o skanowaniu, a oś czasu urządzenia będzie zawierać nowe zdarzenie.

:::image type="content" source="images/restrict-app-execution.png" alt-text="Powiadomienie o ograniczeniu aplikacji" lightbox="images/restrict-app-execution.png":::

### <a name="notification-on-device-user"></a>Powiadomienie użytkownika urządzenia

Gdy aplikacja jest ograniczona, zostanie wyświetlone następujące powiadomienie informujące użytkownika, że aplikacja jest ograniczona do uruchamiania:

:::image type="content" source="images/atp-app-restriction.png" alt-text="Komunikat o ograniczeniu aplikacji" lightbox="images/atp-app-restriction.png":::

>[!NOTE]
>Powiadomienie nie jest dostępne w Windows Server 2016 i Windows Server 2012 R2.

## <a name="isolate-devices-from-the-network"></a>Izoluj urządzenia z sieci

W zależności od ważności ataku i poufności urządzenia możesz chcieć odizolować urządzenie od sieci. Ta akcja może uniemożliwić atakującemu kontrolowanie urządzenia, które zostało naruszone, i wykonywanie dalszych działań, takich jak eksfiltracja danych i przenoszenie boczne.

> [!IMPORTANT]
> - Izolowanie urządzeń od sieci nie jest obecnie obsługiwane w przypadku macOS i Linux. Użyj odpowiedzi na żywo, aby uruchomić akcję. Aby uzyskać więcej informacji na temat odpowiedzi na żywo, zobacz [Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo](live-response.md).
> - Pełna izolacja jest dostępna dla urządzeń w Windows 10, wersji 1703, Windows 11, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 i Windows Server 2022.
> - Selektywna izolacja jest dostępna dla urządzeń w Windows 10, wersji 1709 lub nowszej i Windows 11.
> - Podczas izolowania urządzenia dozwolone są tylko niektóre procesy i miejsca docelowe. W związku z tym urządzenia, które znajdują się za pełnym tunelem SIECI VPN, nie będą mogły uzyskać dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender usługi w chmurze po odizolowaniu urządzenia. Zalecamy używanie sieci VPN z tunelowaniem podzielonym na Ochrona punktu końcowego w usłudze Microsoft Defender i Program antywirusowy Microsoft Defender ruchu związanego z ochroną opartą na chmurze.

Ta funkcja izolacji urządzenia odłącza urządzenie, którego zabezpieczenia zostały naruszone, z siecią, zachowując jednocześnie łączność z usługą Defender for Endpoint, która nadal monitoruje urządzenie.

W Windows 10 wersji 1709 lub nowszej będziesz mieć większą kontrolę nad poziomem izolacji sieci. Możesz również włączyć łączność Outlook, Microsoft Teams i Skype dla firm (np. "Izolacja selektywna").

> [!NOTE]
> W dowolnym momencie będzie można ponownie połączyć urządzenie z siecią. Przycisk na stronie urządzenia zmieni się na **Zwolnij z izolacji**, a następnie wykonasz te same kroki, co izolowanie urządzenia.

Po wybraniu pozycji **Wyizoluj urządzenie** na stronie urządzenia wpisz komentarz i wybierz pozycję **Potwierdź**. Centrum akcji wyświetli informacje o skanowaniu, a oś czasu urządzenia będzie zawierać nowe zdarzenie.

:::image type="content" source="images/isolate-device.png" alt-text="Strona szczegółów izolowanego urządzenia" lightbox="images/isolate-device.png":::

> [!NOTE]
> Urządzenie pozostanie połączone z usługą Defender for Endpoint, nawet jeśli jest odizolowane od sieci. Jeśli wybrano opcję włączenia komunikacji Outlook i Skype dla firm, będzie można komunikować się z użytkownikiem, gdy urządzenie jest izolowane.

### <a name="notification-on-device-user"></a>Powiadomienie użytkownika urządzenia

Gdy urządzenie jest izolowane, zostanie wyświetlone następujące powiadomienie informujące użytkownika, że urządzenie jest odizolowane od sieci:

:::image type="content" source="images/atp-notification-isolate.png" alt-text="Komunikat o braku połączenia sieciowego" lightbox="images/atp-notification-isolate.png":::

## <a name="consult-a-threat-expert"></a>Konsultuj się z ekspertem ds. zagrożeń

Możesz skontaktować się z ekspertem ds. zagrożeń firmy Microsoft, aby uzyskać więcej szczegółowych informacji na temat urządzenia, które zostało potencjalnie naruszone lub które zostało już naruszone. Microsoft Threat Experts można zaangażować bezpośrednio z poziomu Microsoft 365 Defender w celu terminowego i dokładnego reagowania. Eksperci udostępniają szczegółowe informacje nie tylko dotyczące potencjalnie zagrożonego urządzenia, ale także w celu lepszego zrozumienia złożonych zagrożeń, otrzymywanych powiadomień o ukierunkowanych atakach lub jeśli potrzebujesz więcej informacji na temat alertów lub kontekstu analizy zagrożeń widocznego na pulpicie nawigacyjnym portalu.

Szczegółowe informacje [można znaleźć w temacie Consult a Microsoft Threat Expert (Zapoznaj się z ekspertem ds. zagrożeń firmy Microsoft](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) ).

## <a name="check-activity-details-in-action-center"></a>Sprawdź szczegóły aktywności w Centrum akcji

**Centrum akcji** zawiera informacje o akcjach wykonywanych na urządzeniu lub pliku. Będzie można wyświetlić następujące szczegóły:

- Badanie kolekcji pakietów
- Skanowanie antywirusowe
- Ograniczenie aplikacji
- Izolacja urządzenia

Wyświetlane są również wszystkie inne powiązane szczegóły, na przykład data/godzina przesłania, przesyłanie użytkownika oraz czy akcja zakończyła się pomyślnie lub nie powiodła się.

:::image type="content" source="images/action-center-details.png" alt-text="Centrum akcji z informacjami" lightbox="images/action-center-details.png":::


## <a name="see-also"></a>Zobacz też

- [Wykonaj akcje odpowiedzi na pliku](respond-file-alerts.md)
- [Ręczne akcje reagowania w planie Ochrona punktu końcowego w usłudze Microsoft Defender 1](defender-endpoint-plan-1.md#manual-response-actions)
- [Niedokładność raportu](/microsoft-365/security/defender-endpoint/tvm-security-recommendation#report-inaccuracy)
