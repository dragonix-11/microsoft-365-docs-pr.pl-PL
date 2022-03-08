---
title: Tworzenie zbierania elektronicznych materiałów dowodowych w przypadku podstawowej sprawy zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: W celu zachowania zawartości związanej z prowadzonym dochodzeniami sądowym lub sądowym możesz utworzyć Microsoft 365, która jest skojarzona z podstawową sprawą zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: 0d80197becdeb07c917602ff27a1ad9b2c882029
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322117"
---
# <a name="create-an-ediscovery-hold"></a>Tworzenie zbierania elektronicznych materiałów dowodowych

Przy użyciu podstawowej sprawy zbierania elektronicznych materiałów dowodowych możesz utworzyć blokady w celu zachowania zawartości, która może być istotny dla danej sprawy. Możesz umieścić w akwedycie skrzynki Exchange i konta OneDrive dla Firm osób, które badasz w tej sprawie. Możesz także umieścić w aarchiwowe skrzynki pocztowe i witryny skojarzone z witrynami Microsoft Teams, Office 365 i Yammer grupy. Po umieszczenie lokalizacji zawartości w hold, zawartość jest zachowywana do momentu usunięcia lokalizacji zawartości z zawieszonego miejsca lub do czasu jej usunięcia.

Po utworzeniu zbierania elektronicznych materiałów dowodowych może upłynieć do 24 godzin, aż zostanie ono zawieszone.

Po utworzeniu wstrzymywania dostępne są następujące opcje zakresu zawartości, która jest zachowywana w określonych lokalizacjach zawartości:
  
- Tworzenie nieograniczonej przestrzeni, w której cała zawartość w określonych lokalizacjach jest umieszczana w hold. Alternatywnie możesz utworzyć hold oparte na kwerendzie, w którym wstrzymywana jest tylko zawartość w określonych lokalizacjach, która jest odpowiada zapytaniu wyszukiwania.

- Określ zakres dat, aby zachować tylko zawartość, która została wysłana, odebrana lub utworzona w tym zakresie. Ewentualnie możesz przechowywać całą zawartość w określonych lokalizacjach, niezależnie od tego, kiedy została wysłana, odebrana lub utworzona.
  
## <a name="how-to-create-an-ediscovery-hold"></a>Jak utworzyć  hold zbierania elektronicznych materiałów dowodowych

Aby utworzyć hold zbierania elektronicznych materiałów dowodowych, który jest skojarzony z podstawową sprawą zbierania elektronicznych materiałów dowodowych:
  
1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu poświadczeń dla konta użytkownika, do których zostały przypisane odpowiednie uprawnienia zbierania elektronicznych materiałów dowodowych.

2. W lewym okienku nawigacji kliknij pozycję **Pokaż wszystko**, a następnie kliknij pozycję **zbierania elektronicznych materiałów dowodowych > Core**.

3. Na **stronie Podstawowe zbierania elektronicznych materiałów dowodowych** kliknij nazwę sprawy, w której chcesz utworzyć wstrzymanie.

4. Na stronie **głównej** sprawy kliknij kartę **Wstrzymaj** .
  
5. Na stronie **Wstrzymaj** kliknij pozycję **Utwórz**.

6. Na stronie **Kreatora nazywania** wstrzymywania nadaj ikonie wstrzymywania nazwę i dodaj opcjonalny opis, a następnie kliknij przycisk **Dalej**. Nazwa hold musi być unikatowa w Twojej organizacji.

7. Na **stronie kreatora Wybieranie** lokalizacji wybierz lokalizacje zawartości, które mają zostać zawieszone. Możesz umieścić skrzynki pocztowe, witryny i foldery publiczne w miejscu przechowywania.

    ![Wybierz lokalizacje zawartości, które mają być zawieszone.](../media/eDiscoveryHoldLocations.png)
  
   1. **Exchange skrzynki pocztowe**: Ustaw przełącznik w pozycję Wł., a następnie kliknij pozycję Wybierz użytkowników, grupy lub zespoły **,** aby określić skrzynki pocztowe do przechowywania. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne (aby umieścić je w miejscu przechowywania w skrzynkach pocztowych członków grupy), aby umieścić je w a hold. Możesz także umieścić wstrzymaj skojarzoną skrzynkę pocztową dla zespołu Microsoft Team, grupy Office 365 i grupy Yammer grupy. Aby uzyskać więcej informacji o danych aplikacji, które są zachowywane po umieszczeniu skrzynki pocztowej w stanie przechowywania, zobacz Zawartość przechowywana w skrzynkach pocztowych na [celu zbierania elektronicznych materiałów dowodowych](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint witryn**: Ustaw przełącznik w pozycję Wł.,  a następnie kliknij pozycję  Wybierz witryny, aby określić witryny SharePoint i konta OneDrive, które mają być zawieszone. Wpisz adres URL każdej witryny, którą chcesz umieścić w miejscu przechowywania. Możesz również dodać adres URL witryny SharePoint zespołu Microsoft, grupy Office 365 lub grupy Yammer grupy.
  
   3. **Exchange folderów publicznych**: Ustaw przełącznik na wartość Wł., aby umieścić wszystkie foldery publiczne w Exchange Online wstrzymywanie. Nie można wybrać konkretnych folderów publicznych, które mają zostać zawieszone. Jeśli nie chcesz przechowywać folderów publicznych, pozostaw przełącznik wyłączony.

   > [!IMPORTANT]
   > Podczas dodawania Exchange pocztowych lub witryn SharePoint do hold, musisz jawnie dodać do hold co najmniej jedną lokalizację zawartości. Innymi słowy, jeśli ustawisz przełącznik w pozycję Wł. dla skrzynek pocztowych lub witryn, musisz wybrać określone skrzynki pocztowe lub witryny, które chcesz dodać do zawieszonego miejsca. W przeciwnym razie zostanie utworzone hold zbierania elektronicznych materiałów dowodowych, ale nie zostaną dodane żadne skrzynki pocztowe ani witryny, a statystyki będą pokazywać, że nie ma żadnych lokalizacji zawartości ani elementów w a hold.

8. Po dodaniu lokalizacji do zawieszonego miejsca kliknij przycisk **Dalej**.

9. Aby utworzyć hold oparte na kwerendzie przy użyciu słów kluczowych lub warunków, wykonaj następujące czynności. Aby zachować całą zawartość w określonych lokalizacjach zawartości, kliknij przycisk **Dalej**.

    ![Utwórz hold oparte na kwerendzie za pomocą słów kluczowych i warunków.](../media/eDiscoveryHoldQuery.png)
  
    1. W polu w obszarze **Słowa kluczowe** wpisz zapytanie, aby zachować tylko zawartość, która jest spełniają kryteria zapytania. Możesz określić słowa kluczowe, właściwości wiadomości e-mail lub właściwości witryny, takie jak nazwy plików. Można także używać bardziej złożonych zapytań, które używają operatora logicznych, takiego jak **AND**, **OR** lub **NOT**.

    2. Kliknij **pozycję Dodaj warunek** , aby dodać jeden lub więcej warunków w celu zawężenia zapytania w celu wstrzymywania. Każdy warunek powoduje dodanie klauzuli do zapytania wyszukiwania WKQL, które jest tworzone i uruchamiane podczas tworzenia holdu. Można na przykład określić zakres dat, aby wiadomości e-mail lub dokumenty witryny utworzone w zakresie dat były zachowywane. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym  w polu Słowa kluczowe) i innymi warunkami przez operator **AND**. Oznacza to, że elementy muszą spełniać zarówno zapytanie słów kluczowych, jak i warunek, który ma zostać zachowany.

    Aby uzyskać więcej informacji na temat tworzenia zapytania wyszukiwania i używania warunków, zobacz Zapytania słów kluczowych i warunki wyszukiwania [dotyczące zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

10. Po skonfigurowaniu hold'a opartego na kwerendzie kliknij przycisk **Dalej**.

11. Przejrzyj ustawienia (i w razie potrzeby je edytuj), a następnie kliknij przycisk **Prześlij**.

## <a name="query-based-holds-placed-on-sites"></a>Blokady oparte na zapytaniach umieszczane w witrynach

Podczas przechowywania SharePoint opartych na zapytaniach zbierania elektronicznych materiałów dowodowych należy pamiętać o następujących kwestiach:

- Wstrzymywanie oparte na kwerendach początkowo zachowuje wszystkie dokumenty w witrynie przez krótki czas po ich usunięciu. Oznacza to, że po usunięciu dokumentu zostanie on przeniesiony do biblioteki Zachowywanie, nawet jeśli nie jest on zgodne z kryteriami zawieszonego na podstawie zapytania. Jednak usunięte dokumenty, które nie są zgodne z holdm opartym na kwerendzie, zostaną usunięte przez zadanie czasomierza, które przetwarza bibliotekę Hold zachowania. Zadanie czasomierza jest uruchamiane okresowo i porównuje wszystkie dokumenty z biblioteki zbierania elektronicznych materiałów dowodowych oparte na kwerendach (oraz z innymi typami blokady i zasady przechowywania). Zadanie czasomierza usuwa dokumenty, które nie są zgodne z zapytaniem, i zachowuje te dokumenty.

- Blokady oparte na zapytaniach nie powinny być używane do zachowywania kierowanego, na przykład do zachowywania dokumentów w określonym folderze lub witrynie albo przy użyciu innych kryteriów przechowywania opartych na lokalizacji. Może to spowodować niezamierzone wyniki. Aby zachować dokumenty witryny, zalecamy używanie kryteriów przechowywania opartych na lokalizacji, takich jak słowa kluczowe, zakresy dat lub inne właściwości dokumentu.

## <a name="ediscovery-hold-statistics"></a>Statystyka zbierania elektronicznych materiałów dowodowych

Po utworzeniu blokady zbierania elektronicznych materiałów dowodowych na wysuwanych stronie dla wybranego zbierania elektronicznych materiałów dowodowych są wyświetlane informacje o nowym zarchiweniu. Te informacje obejmują liczbę skrzynek pocztowych i witryn umieszczonych w hold' oraz statystyki dotyczące zawartości, która została umieszczona w hold, na przykład całkowita liczba i rozmiar elementów umieszczonych w a holdie oraz czas ostatniego obliczania statystyki dotyczącej blokowania. Statystyki te ułatwiają zidentyfikowanie ilości zawartości związanej ze sprawą, która jest zachowywana.
  
![Statystyki wstrzymywania.](../media/eDiscoveryHoldStatistics.png)
  
W statystyce zbierania elektronicznych materiałów dowodowych należy pamiętać o następujących kwestiach:
  
- Całkowita liczba elementów wstrzymywanych wskazuje liczbę elementów ze wszystkich źródeł zawartości, które są umieszczone w hold. Jeśli utworzono hold oparte na kwerendzie, ta statystyka wskazuje liczbę elementów, które pasują do zapytania.

- Liczba elementów w hold obejmuje również elementy nieindeksowane odnalezione w lokalizacjach zawartości. Jeśli utworzysz hold oparte na kwerendzie, wszystkie elementy nieindeksowane w lokalizacjach zawartości zostaną umieszczone w hold. Dotyczy to elementów nieindeksowanych, które nie są zgodne z kryteriami wyszukiwania opartymi na kwerendzie i elementów nieindeksowanych, które mogą być spoza warunku zakresu dat. Jest to sytuacja inna niż przy uruchamianiu wyszukiwania, w którym elementy nieindeksowane, które nie są zgodne z zapytaniem wyszukiwania lub są wykluczane przez warunek zakresu dat, nie są uwzględniane w wynikach wyszukiwania. Aby uzyskać więcej informacji na temat elementów nieindeksowanych, zobacz [Elementy częściowo indeksowane](partially-indexed-items-in-content-search.md).

- Możesz uzyskać najnowsze statystyki dotyczące blokowania, klikając pozycję  Aktualizuj statystykę, aby ponownie uruchomić oszacowanie wyszukiwania, które oblicza bieżącą liczbę elementów w wstrzymaniu.

- Zazwyczaj liczba wstrzymanych elementów zwiększa się w czasie, ponieważ użytkownicy, których skrzynka pocztowa lub witryna znajdują się w stanie zawieszone, zazwyczaj wysyłają lub otrzymują nową wiadomość e-mail oraz tworzą nowe dokumenty w SharePoint i OneDrive.

- Jeśli skrzynka pocztowa usługi Exchange, witryna usługi SharePoint lub konto programu OneDrive zostanie przeniesione do innego regionu w środowisku z wieloma lokalizacjami geograficznymi, statystyki dotyczące tej witryny nie będą uwzględniane w statystykach zawieszonego miejsca. Jednak zawartość w tych lokalizacjach nadal zostanie zachowana. Ponadto jeśli skrzynka pocztowa lub witryna zostanie przeniesiona do innego regionu, adres SMTP lub adres URL wyświetlany w witrynie nie zostanie automatycznie zaktualizowany. Musisz edytować hold i zaktualizować adres URL lub SMTP, aby ponownie uwzględniono lokalizacje zawartości w statystyce hold

## <a name="search-locations-on-ediscovery-hold"></a>Lokalizacje wyszukiwania w zbierania elektronicznych materiałów dowodowych

Podczas wyszukiwania [zawartości](search-for-content-in-core-ediscovery.md) w podstawowej sprawie zbierania elektronicznych materiałów dowodowych można szybko skonfigurować wyszukiwanie tylko w lokalizacjach zawartości, które zostały umieszczone w zarchiwionym skojarzona ze sprawą.

Wybierz opcję **Lokalizacje w** wstrzymaniu, aby przeszukać wszystkie lokalizacje zawartości, które zostały umieszczone w wstrzymaniu. Jeśli sprawa zawiera wiele zbierania elektronicznych materiałów dowodowych, po wybraniu tej opcji przeszukane zostaną lokalizacje zawartości ze wszystkich zbierania elektronicznych materiałów dowodowych. Ponadto, jeśli lokalizację zawartości umieszczono w opartym na kwerendzie, po uruchomieniu wyszukiwania będą przeszukiwane tylko elementy, które pasują do zapytania wstrzymywania. Innymi słowy tylko zawartość, która odpowiada zarówno kryteriom wstrzymywania, jak i kryteriom wyszukiwania, jest zwracana wraz z wynikami wyszukiwania. Jeśli na przykład użytkownik został umieszczony w opartym na kwerendach z zachowaniem elementów wysłanych lub utworzonych przed określoną datą, przeszukiwane będą tylko te elementy. Można to zrobić przez połączenie zapytania przytrzymującego sprawę z zapytaniem wyszukiwania przez **operator AND** .

Oto kilka innych rzeczy, o których należy pamiętać podczas wyszukiwania lokalizacji w zbierania elektronicznych materiałów dowodowych:

- Jeśli lokalizacja zawartości jest częścią wielu zer w ramach tej samej sprawy, zapytania blokady są łączone za pomocą operatorów **LUB** podczas przeszukiwania tej lokalizacji zawartości przy użyciu opcji zawartości całej sprawy. Podobnie, jeśli lokalizacja zawartości jest częścią dwóch różnych zbędek, gdzie jedno jest oparte na kwerendach, a drugie to nieskończone hold (gdzie cała zawartość jest umieszczana w holdm), to cała zawartość jest przeszukiwana z powodu nieograniczonego zawieszonego miejsca.

- Jeśli w wyszukiwaniu skonfigurowano wyszukiwanie w miejscu, w którym jest ono skonfigurowane, a następnie zmienisz hold zbierania elektronicznych materiałów dowodowych (przez dodanie lub usunięcie lokalizacji lub zmianę zapytania wstrzymywania), konfiguracja wyszukiwania zostanie zaktualizowana wraz z tymi zmianami. Jednak aby zaktualizować wyniki wyszukiwania, trzeba ponownie uruchomić wyszukiwanie po zmianie wstrzymywania.

- Jeśli w jednej lokalizacji w ramach sprawy zbierania elektronicznych materiałów dowodowych znajduje się wiele zbierania elektronicznych materiałów dowodowych i wybierzesz lokalizacje wyszukiwania w miejscu, w którym zostanie wybrane wyszukiwanie w tym miejscu, maksymalna liczba słów kluczowych dla tego zapytania wyszukiwania wynosi 500. Wynika to z tego, że wyszukiwanie łączy wszystkie blokady oparte na zapytaniach przy użyciu **operatora OR** . Jeśli w połączonych zapytaniach hold i zapytaniu wyszukiwania znajduje się więcej niż 500 słów kluczowych, przeszukiwana jest cała zawartość skrzynki pocztowej, a nie tylko ta zawartość, która jest dołączona do przypadków opartych na kwerendach.

- Jeśli stan funkcji zbierania elektronicznych materiałów dowodowych ma stan Wł **. (** Oczekiwanie), nadal możesz wyszukiwać w lokalizacjach w miejscu, w którym jest włączona.

## <a name="preserve-content-in-microsoft-teams"></a>Zachowywanie zawartości w Microsoft Teams

Konwersacje w ramach kanału Microsoft Teams są przechowywane w skrzynce pocztowej skojarzonej z zespołem Microsoft. Podobnie pliki, które członkowie zespołu mają udział w kanale, są przechowywane w SharePoint zespołu. Dlatego należy umieścić skrzynkę pocztową zespołu i witrynę SharePoint zbierania elektronicznych materiałów dowodowych, aby zachować konwersacje i pliki w kanale.

Konwersacje, które są częścią listy czatów w programie Teams (nazywane czatami *1:1* lub *czatami grupowych 1:N*) są przechowywane w skrzynkach pocztowych użytkowników, którzy uczestniczą w czacie. Pliki, które użytkownicy mogą udostępniać w konwersacjach na czacie, są przechowywane OneDrive konta użytkownika, który udostępnia plik. Dlatego musisz dodać poszczególne skrzynki pocztowe użytkowników i konta OneDrive do zbierania elektronicznych materiałów dowodowych, aby zachować konwersacje i pliki na liście czatów. Oprócz umieszczenia skrzynki pocztowej zespołu i witryny w witrynie w witrynie, warto także umieścić w nich także skrzynkę pocztową zespołu i skrzynkę pocztową.

> [!NOTE]
> Jeśli Twoja organizacja ma wdrożenie hybrydowe programu Exchange (lub organizacja synchronizuje lokalną organizację programu Exchange z programem Office 365) i włączyła usługę Microsoft Teams, użytkownicy lokalni mogą korzystać z aplikacji czatu Teams i uczestniczyć w czatach indywidualnych i czatach grupowych 1:N. Te konwersacje są przechowywane w opartym na chmurze magazynie skojarzonym z użytkownikiem lokalnym. Jeśli użytkownik lokalnego zostanie umieszczony w zbierania elektronicznych materiałów dowodowych, zawartość czatu Teams w magazynie opartym na chmurze zostanie zachowana. Aby uzyskać więcej informacji, [zobacz Wyszukiwanie Teams danych czatu dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

Aby uzyskać więcej informacji na temat zachowywania Teams, zobacz Microsoft Teams lub zespół do [prawnie.](/MicrosoftTeams/legal-hold)

### <a name="preserve-card-content"></a>Zachowywanie zawartości karty

Podobnie zawartość kart generowana przez aplikacje w kanałach Teams, czatach grupowych 1:1 i czatach grupowych 1:N jest przechowywana w skrzynkach pocztowych i zachowywana, gdy skrzynka pocztowa zostanie umieszczona w zbierania elektronicznych materiałów dowodowych. Karta *to* kontener interfejsu użytkownika na krótkie fragmenty zawartości. Karty mogą mieć wiele właściwości i załączników oraz zawierać przyciski wyzwalające akcje karty. Aby uzyskać więcej informacji, zobacz [Karty](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Podobnie jak Teams, gdzie zawartość kart jest przechowywana na podstawie miejsca jej użytego. Zawartość kart używanych w kanale Teams jest przechowywana w skrzynce Teams pocztowej grupy. Zawartość kart do czatów 1:1 i 1xN jest przechowywana w skrzynkach pocztowych uczestników czatu.

### <a name="preserve-meeting-and-call-information"></a>Zachowywanie informacji o spotkaniu i rozmowę

Podsumowanie informacji dotyczących spotkań i połączeń w kanale Teams jest również przechowywane w skrzynkach pocztowych użytkowników, którzy nacięli się na spotkanie lub połączenie telefoniczne. Ta zawartość jest zachowywana również w przypadku umieszczenia w skrzynkach pocztowych użytkowników zbierania elektronicznych materiałów dowodowych.

### <a name="preserve-content-in-private-channels"></a>Zachowywanie zawartości w kanałach prywatnych

Od lutego 2020 r. włączona została również możliwość zachowywania zawartości w kanałach prywatnych. Ponieważ czaty w kanałach prywatnych są przechowywane w skrzynkach pocztowych uczestników czatu, umieszczenie skrzynki pocztowej użytkownika w zbierania elektronicznych materiałów dowodowych spowoduje zachowanie czatów w kanałach prywatnych. Ponadto jeśli skrzynka pocztowa użytkownika została umieszczona w zbierania elektronicznych materiałów dowodowych przed lutym 2020 r., teraz ta skrzynka będzie automatycznie miała zastosowanie do wiadomości w kanałach prywatnych przechowywanych w tej skrzynce pocztowej. Zachowywanie plików udostępnionych w kanałach prywatnych jest również obsługiwane.

### <a name="preserve-wiki-content"></a>Zachowywanie zawartości typu wiki

Każdy zespół lub kanał zespołu zawiera również stronę typu wiki do sporządzania notek i współpracy. Zawartość typu wiki jest automatycznie zapisywana w pliku w formacie mht. Ten plik jest przechowywany w bibliotece Teams danych typu wiki w witrynie zespołu SharePoint wiki. Zawartość witryny typu wiki można zachować, dodając witrynę zespołu do SharePoint zbierania elektronicznych materiałów dowodowych.

> [!NOTE]
> 22 czerwca 2017 r. opublikowano funkcję zachowywania zawartości typu wiki dla kanału zespołu lub zespołu (po SharePoint wstrzymywania witryny zespołu). Jeśli witryna zespołu znajduje się w wstrzymaniu, jej zawartość będzie zachowywana od tego dnia. Jeśli jednak witryna zespołu znajduje się w miejscu, a jej zawartość została usunięta przed 22 czerwca 2017 r., zawartość witryny typu wiki nie została zachowana.

### <a name="office-365-groups"></a>Grupy usługi Office 365

Teams są wbudowane w Office 365 grupy. Dlatego umieszczanie grup Office 365 w zbierania elektronicznych materiałów dowodowych jest podobne do umieszczania zawartości Teams w hold.

Przy umieszczaniu grup zbierania elektronicznych materiałów dowodowych Teams i Office 365 należy pamiętać o następujących kwestiach:

- Jak wyjaśniono wcześniej, aby umieścić zawartość w grupach Teams i Office 365 w miejscu, należy określić skrzynkę pocztową i witrynę SharePoint skojarzoną z grupą lub zespołem.

- Uruchom polecenie **cmdlet Get-UnifiedGroup** w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), aby wyświetlić właściwości Teams i Office 365 Grupy. Jest to dobry sposób na uzyskania adresu URL witryny skojarzonej z grupą użytkowników lub członków Office 365 grupy. Na przykład następujące polecenie wyświetla wybrane właściwości grupy kierownictwa Office 365 o nazwie Zespół kierownictwa wyższego:

    ```text
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl

    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Aby uruchomić polecenie **cmdlet Get-UnifiedGroup**, musisz mieć przypisaną rolę adresatów View-Only w programie Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only. 
  
- Podczas przeszukiwania skrzynki pocztowej użytkownika nie będą przeszukiwane żadne grupy zespołu Office 365 grupy, do których należy użytkownik. Podobnie, po umieszczeniu grupy zespołu lub grupy Office 365 w zbierania elektronicznych materiałów dowodowych wstrzymywana jest tylko skrzynka pocztowa grupy i witryna grupy. Skrzynki pocztowe i OneDrive dla Firm członków grupy nie są umieszczane w a hold, chyba że jawnie dodasz ich do hold usługi zbierania elektronicznych materiałów dowodowych. Jeśli z przyczyn prawnych trzeba chcieć umieścić grupę zespołu lub grupy Office 365, rozważ dodanie skrzynek pocztowych i kont OneDrive członków zespołu lub grupy w tym samym czacie.

- Aby uzyskać listę członków grupy zespołu lub grupy Office 365, możesz wyświetlić właściwości na stronie Grupy w centrum administracyjne platformy Microsoft 365.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> Możesz również uruchomić następujące polecenie w programie Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Aby uruchomić polecenie **cmdlet Get-UnifiedGroupLinks**, musisz mieć przypisaną rolę adresatów View-Only w programie Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only.

## <a name="preserve-content-in-onedrive-accounts"></a>Zachowywanie zawartości na OneDrive kontach

Aby zebrać listę adresów URL witryn usługi OneDrive dla Firm w organizacji w celu dodania ich do listy adresów URL lub wyszukiwania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych, zobacz Tworzenie listy wszystkich OneDrive lokalizacji w [organizacji.](/onedrive/list-onedrive-urls) Skrypt w tym artykule tworzy plik tekstowy zawierający listę wszystkich OneDrive witryny w organizacji. Aby uruchomić ten skrypt, musisz zainstalować powłokę zarządzania SharePoint online i używać jej. Pamiętaj, aby dołączyć adres URL domeny Moja witryna organizacji do każdej witryny OneDrive, którą chcesz przeszukać. Jest to domena zawierająca wszystkie twoje OneDrive, na przykład `https://contoso-my.sharepoint.com`. Oto przykładowy adres URL witryny sieci OneDrive użytkownika: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

> [!IMPORTANT]
> Adres URL konta użytkownika OneDrive zawiera jego główną nazwę użytkownika (GŁÓWNĄ nazwę użytkownika), na przykład `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). W rzadkich przypadkach, w której głównej nazwa sieci OneDrive głównej osoby, adres URL tej osoby również zostanie zmieniony, aby włączyć nową nazwę UPN. Jeśli konto użytkownika w programie OneDrive jest częścią przechowywania zbierania elektronicznych materiałów dowodowych, jego stara nazwa użytkownika i jego głównej nazwy użytkownika zostanie zmieniona, musisz zaktualizować to zawieszone konto, dodać nowy adres URL usługi OneDrive i usunąć stary. Aby uzyskać więcej informacji, zobacz [Jak zmiany głównej sieci użytkowników wpływają na OneDrive URL](/onedrive/upn-changes).

## <a name="removing-content-locations-from-an-ediscovery-hold"></a>Usuwanie lokalizacji zawartości z zawieszonego zbierania elektronicznych materiałów dowodowych

Po usunięciu skrzynki SharePoint skrzynki pocztowej, witryny OneDrive lub konta zbierania elektronicznych materiałów dowodowych stosowane jest opóźnienie. Oznacza to, że rzeczywiste usunięcie opóźnienia jest opóźnione o 30 dni, aby zapobiec trwałemu usunięciu danych (przeczyszczeniu) z lokalizacji zawartości. Dzięki temu administratorzy mogą wyszukiwać lub odzyskiwać zawartość, która zostanie przeczyszczona po usunięciu zbierania elektronicznych materiałów dowodowych. Szczegóły dotyczące sposobu działania opóźnienia w przypadku skrzynek pocztowych i witryn różnią się.

- **Skrzynki pocztowe:** Opóźnienie umieszcza się w skrzynce pocztowej, gdy asystent folderów zarządzanych następnym razem przetwarza skrzynkę pocztową i wykrywa usunięcie zbierania elektronicznych materiałów dowodowych. W szczególności do skrzynki pocztowej jest stosowane opóźnienie, gdy Asystent folderów zarządzanych ustawia jedną z następujących właściwości skrzynki pocztowej na **wartość True**:

   - **DelayHoldApplied:** Ta właściwość dotyczy zawartości związanej z pocztą e-mail (generowanej przez osoby korzystające Outlook i Outlook w sieci Web) przechowywanej w skrzynce pocztowej użytkownika.

   - **DelayReleaseHoldApplied:** Ta właściwość dotyczy zawartości opartej na chmurze (generowanej przez aplikacje inne niż Outlook, takie jak Microsoft Teams, Microsoft Forms i Microsoft Yammer), która jest przechowywana w skrzynce pocztowej użytkownika. Dane w chmurze wygenerowane przez aplikację firmy Microsoft są zwykle przechowywane w ukrytym folderze w skrzynce pocztowej użytkownika.

   Po umieszczeniu w skrzynce pocztowej opóźnienia (jeśli dowolna z poprzednich właściwości jest ustawiona na **Prawda)** skrzynka pocztowa jest nadal uznawana za wstrzymaną przez nieograniczony czas trwania, tak jakby skrzynka pocztowa była w związku z postępowaniem sądowym. Po 30 dniach opóźnienie wygasa i program Microsoft 365 automatycznie podejmie próbę usunięcia opóźnienia (ustawiając dla właściwości DelayHoldApplied lub DelayReleaseHoldApplied wartość **False**), co spowoduje usunięcie opóźnienia. Gdy wartość jednej z tych właściwości zostanie ustawiona na Fałsz **, odpowiadające** im elementy oznaczone do usunięcia zostaną wyczyszczone podczas następnego przetwarzania skrzynki pocztowej przez asystenta folderów zarządzanych.

   Aby uzyskać więcej informacji, zobacz [Zarządzanie skrzynkami pocztowymi w przypadku opóźnienia](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

- **SharePoint i OneDrive:** Zawartość usług SharePoint i OneDrive, która jest zachowywana w bibliotece zbierania elektronicznych materiałów dowodowych, nie jest usuwana w trakcie 30-dniowego okresu opóźnienia po usunięciu witryny z zawieszonego zbierania elektronicznych materiałów dowodowych. Przypomina to zachowanie po zwolnieniu witryny z zasad przechowywania. Ponadto nie można ręcznie usunąć tej zawartości z biblioteki Hold zachowywania w okresie opóźnienia 30 dni. 

   Aby uzyskać więcej informacji, [zobacz Zwalnianie zasad przechowywania](retention.md#releasing-a-policy-for-retention).

W przypadku zamykania podstawowej sprawy zbierania elektronicznych materiałów dowodowych blokady są również stosowane do lokalizacji zawartości w miejscu przechowywania zawartości, ponieważ w przypadku zamknięcia sprawy blokady są wyłączone. Aby uzyskać więcej informacji na temat zamykania sprawy, zobacz Zamykanie, ponowne otwieranie i usuwanie podstawowej sprawy [zbierania elektronicznych materiałów dowodowych](close-reopen-delete-core-ediscovery-cases.md).

## <a name="ediscovery-hold-limits"></a>Limity zbierania elektronicznych materiałów dowodowych

W poniższej tabeli wymieniono limity dotyczące spraw zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych.

  | Opis limitu | Limit |
  |:-----|:-----|
  |Maksymalna liczba spraw w organizacji.  <br/> |Bez limitu  <br/> |
  |Maksymalna liczba zasad zbierania elektronicznych materiałów dowodowych w organizacji. Limit ten obejmuje łączną liczbę zasad przechowywania w przypadku podstawowych zbierania elektronicznych materiałów dowodowych Advanced eDiscovery spraw.  <br/> |10 <sup>0001</sup>  <br/> |
  |Maksymalna liczba skrzynek pocztowych w pojedynczym zbierania elektronicznych materiałów dowodowych. Ten limit obejmuje łączną liczbę skrzynek pocztowych użytkowników oraz skrzynek pocztowych skojarzonych Microsoft 365, grup Microsoft Teams i Yammer grupy.  <br/> |1,000  <br/> |
  |Maksymalna liczba witryn w pojedynczym zbierania elektronicznych materiałów dowodowych. Ten limit obejmuje łączną liczbę OneDrive dla Firm, witryn SharePoint oraz witryn skojarzonych z grupami Microsoft 365, witrynami Microsoft Teams i Yammer grupy.  <br/> |100  <br/> |
  |Maksymalna liczba spraw wyświetlanych na stronie głównej zbierania elektronicznych materiałów dowodowych oraz maksymalna liczba elementów wyświetlanych na kartach Zarchiwnia, Wyszukiwania i Eksportowanie w ramach sprawy.  |10002<sup></sup>|
  |||

   > [!NOTE]
   > <sup>1</sup> Jeśli w ramach jednej zasady dotyczącej przechowywania wstrzymasz więcej niż 1000 skrzynek pocztowych lub 100 witryn, system automatycznie przeskaluje to hold. Oznacza to, że system automatycznie doda lokalizacje danych do zasad wielokrotnego blokowania, zamiast dodawać je do pojedynczych zasad przechowywania. Nadal jednak obowiązuje limit 10 000 zasad przechowywania przypadków na organizację.
   >
   > <sup>2</sup> Aby wyświetlić listę ponad 1000 spraw, blokady, wyszukiwania lub eksporty, można użyć odpowiedniego polecenia cmdlet programu PowerShell w & zabezpieczeń i zgodności:
   >
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)
