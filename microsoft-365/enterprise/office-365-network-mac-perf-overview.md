---
title: Łączność sieciowa w centrum Administracja Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Omówienie łączności sieciowej w centrum Administracja Microsoft 365
ms.openlocfilehash: 19aa6beaf299a80b76753357e4cbe4f8f0966362
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043870"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center"></a>Łączność sieciowa w centrum Administracja Microsoft 365

Centrum Administracja Microsoft 365 zawiera teraz zagregowane metryki łączności sieciowej zebrane z dzierżawy Microsoft 365 i dostępne do wyświetlania tylko przez użytkowników administracyjnych w dzierżawie.

> [!div class="mx-imgBorder"]
> ![Narzędzie do testowania łączności sieciowej.](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Oceny sieci** i **szczegółowe informacje o sieci** są wyświetlane w centrum Administracja Microsoft 365 w obszarze **Kondycja | Łączność sieciowa**.

> [!div class="mx-imgBorder"]
> ![Strona wydajności sieci.](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

> [!NOTE]
> Łączność sieciowa w Centrum administracyjnym obsługuje dzierżawy WW Commercial i Niemczech, ale nie GCC Moderate, GCC High, DoD lub China.

Po pierwszym przejściu na stronę wydajności sieci należy skonfigurować lokalizacje, aby wyświetlić mapę globalnej wydajności sieci, ocenę sieci w zakresie całej dzierżawy, odsetek użytkowników pracujących zdalnie a lokację oraz listę bieżących problemów do podjęcia działań i/lub dalszych badań. W okienku przeglądu możesz przejść do szczegółów, aby wyświetlić konkretne metryki wydajności sieci i problemy według lokalizacji. Aby uzyskać więcej informacji, zobacz [Omówienie wydajności sieci w centrum Administracja Microsoft 365](#network-connectivity-overview-in-the-microsoft-365-admin-center).

Aby uzyskać dostęp do strony łączności sieciowej, musisz być administratorem organizacji w ramach Microsoft 365. Rola administracyjna Czytelnik raportów będzie mieć dostęp do odczytu tych informacji. Aby skonfigurować lokalizacje i inne elementy łączności sieciowej, administrator musi mieć rolę administratora pomocy technicznej usługi.

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Wymagania wstępne dotyczące oceny łączności sieciowej mają być wyświetlane

Aby rozpocząć, włącz ustawienie zgody na lokalizację, aby automatycznie zbierać dane z urządzeń przy użyciu usług Windows Location Services, przejdź do listy Lokalizacje, aby dodać lub przekazać dane lokalizacji, lub uruchom test łączności sieciowej Microsoft 365 z lokalizacji w biurze. Poniżej przedstawiono te trzy opcje informacji o lokalizacji biura. Chociaż łączność sieciowa może być oceniana w całej organizacji, należy wprowadzić wszelkie ulepszenia projektu sieci dla określonych lokalizacji biurowych. Informacje o łączności sieciowej są udostępniane dla każdej lokalizacji biura po ustaleniu tych lokalizacji. Istnieją trzy opcje uzyskiwania ocen sieci z lokalizacji biurowych:

### <a name="1-enable-windows-location-services"></a>1. Włączanie usług lokalizacji Windows

W przypadku tej opcji w każdej lokalizacji biura muszą być uruchomione co najmniej dwa komputery, które obsługują wymagania wstępne. OneDrive dla wersji Windows musi być aktualna i zainstalowana na każdym komputerze. Aby uzyskać więcej informacji na temat wersji OneDrive, zobacz [informacje o wersji OneDrive](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0). Pomiary sieci mają zostać wkrótce dodane do innych Office 365 aplikacji klienckich.

Windows usługi lokalizacyjnej musi być wyrażana zgoda na maszynach. Możesz to przetestować, uruchamiając aplikację **Mapy** i lokalizując siebie. Można ją włączyć na jednej maszynie z **Ustawienia | | prywatności Lokalizacja**, w której należy włączyć ustawienie _Zezwalaj aplikacjom na dostęp do lokalizacji_. Windows zgodę usług lokalizacyjnych można wdrożyć na komputerach przy użyciu rozwiązania MDM lub zasady grupy z ustawieniem _LetAppsAccessLocation_.

Nie musisz dodawać lokalizacji w Centrum administracyjnym przy użyciu tej metody, ponieważ są one automatycznie identyfikowane w uchwałach miasta. W przypadku korzystania z usług Windows Location Services nie będzie wyświetlanych wiele lokalizacji biurowych w tym samym mieście. Informacje o lokalizacji są zaokrąglane do najbliższych 300 metrów na 300 metrów, aby nie uzyskiwać dostępu do bardziej precyzyjnych informacji o lokalizacji.

Maszyny powinny mieć Wi-Fi sieci, a nie kabel Ethernet. Maszyny z kablem Ethernet nie mają dokładnych informacji o lokalizacji.

Przykłady pomiarów i lokalizacje biura powinny zacząć pojawiać się 24 godziny po spełnieniu tych wymagań wstępnych.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Dodaj lokalizacje i podaj informacje o podsieci SIECI LAN

W przypadku tej opcji nie są wymagane ani usługi lokalizacji Windows, ani Wi-Fi. OneDrive dla wersji Windows musi być aktualny i zainstalowany na co najmniej jednym komputerze w lokalizacji.

Upewnij się, że dodano również lokalizacje na **stronie lokalizacji** lub zaimportowaliśmy je z pliku CSV. Dodane lokalizacje muszą zawierać informacje o podsieci sieci LAN biura. W oknie dialogowym dodawania lub edytowania lokalizacji można określić liczbę podsieci SIECI LAN i liczbę publicznych podsieci IP ruchu wychodzącego. Podsieci sieci LAN są wymagane, a jedna z nich musi być zgodna z atrybutem podsieci LAN w otrzymanej ocenie sieci, aby wyniki były wyświetlane. Super nets nie są obsługiwane, więc podsieć SIECI LAN musi być dokładnie zgodna.

Zazwyczaj podsieci SIECI LAN to zakresy prywatnych adresów IP zdefiniowane w dokumencie RFC1918, tak aby użycie publicznych adresów IP jako podsieci SIECI LAN było prawdopodobnie niepoprawne. W oknie dialogowym zostaną wyświetlone sugestie dotyczące podsieci SIECI LAN, które były widoczne w ostatnich testach oceny sieci dla twojej organizacji, aby można było wybrać tę opcję.

Jeśli dodasz publiczne adresy IP ruchu wychodzącego, są one używane jako pomocnicze różnicowniki i są przeznaczone dla wielu lokacji korzystających z tych samych zakresów adresów IP podsieci SIECI LAN. Aby upewnić się, że wyniki testu są wyświetlane, należy zacząć od pozostawienia pustych zakresów publicznych adresów IP wychodzących. Jeśli zostaną uwzględnione, wynik testu musi być zgodny zarówno z jednym z zakresów adresów IP podsieci SIECI LAN, jak i jednym z zakresów publicznych adresów IP ruchu wychodzącego.

Ta opcja umożliwia zdefiniowanie wielu biur w obrębie miasta.

Wszystkie pomiary testowe z maszyn klienckich zawierają informacje o podsieci SIECI LAN, które są skorelowane ze szczegółami lokalizacji biura, które zostały wprowadzone. Przykłady pomiarów i lokalizacje biura powinny zacząć pojawiać się 24 godziny po spełnieniu tych wymagań wstępnych.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Ręczne zbieranie raportów testowych za pomocą narzędzia do testowania łączności sieciowej Microsoft 365

W przypadku tej opcji należy zidentyfikować osobę w każdej lokalizacji. Poproś ich o przejście do [Microsoft 365 testu łączności sieciowej](https://connectivity.office.com) na maszynie Windows, na której mają uprawnienia administracyjne. W witrynie sieci Web muszą zalogować się do swojego konta Office 365 dla tej samej organizacji, w której chcesz wyświetlić wyniki. Następnie należy kliknąć pozycję **Uruchom test**. Podczas testu jest pobierany test łączności EXE. Muszą to otworzyć i wykonać. Po zakończeniu testów wynik testu jest przekazywany do Centrum administracyjnego.

Raporty testowe są połączone z lokalizacją, jeśli zostały dodane z informacjami o podsieci SIECI LAN, w przeciwnym razie są wyświetlane tylko w lokalizacji miasta.

Przykłady pomiarów i lokalizacje biura powinny zacząć pojawiać się 2–3 minuty po zakończeniu raportu testowego. Aby uzyskać więcej informacji, zobacz [Microsoft 365 test łączności sieciowej](office-365-network-mac-perf-onboarding-tool.md).

> [!NOTE]
> Obecnie podczas dodawania lokalizacji biurowych do Microsoft 365 łączności sieciowej w Centrum administracyjne platformy Microsoft 365 można podać tylko adresy IPv4 dla podsieci SIECI LAN. Egress adresy IP muszą używać protokołu IPv4.

## <a name="how-do-i-use-this-information"></a>Jak mogę użyć tych informacji?

**Szczegółowe informacje o sieci**, związane z nimi zalecenia dotyczące wydajności i oceny sieci mają pomóc w projektowaniu obwodów sieci dla lokalizacji biurowych. Każda analiza zawiera szczegółowe informacje o charakterystykach wydajności dla określonego wspólnego problemu z siecią dla każdej lokalizacji geograficznej, w której użytkownicy uzyskują dostęp do dzierżawy. **Zalecenia dotyczące wydajności** dla każdej analizy sieci oferują określone zmiany w projekcie architektury sieci, które można wprowadzić, aby poprawić środowisko użytkownika związane z łącznością sieciową Microsoft 365. Ocena sieci pokazuje, jak łączność sieciowa wpływa na środowisko użytkownika, co umożliwia porównanie różnych połączeń sieciowych lokalizacji użytkownika.

**Oceny sieci destylują** agregację wielu metryk wydajności sieci do migawki kondycji sieci przedsiębiorstwa reprezentowanej przez wartość punktów z zakresu od 0 do 100. Oceny sieci są ograniczone zarówno do całej dzierżawy, jak i dla każdej lokalizacji geograficznej, z której użytkownicy łączą się z dzierżawą, zapewniając administratorom Microsoft 365 łatwy sposób natychmiastowego zrozumienia kondycji sieci przedsiębiorstwa i szybkiego przechodzenia do szczegółowego raportu dla dowolnej globalnej lokalizacji biura.

Złożone przedsiębiorstwa z wieloma lokalizacjami biur i nietrywialnymi architekturami obwodowymi sieci mogą korzystać z tych informacji podczas początkowego dołączania do Microsoft 365 lub w celu skorygowania problemów z wydajnością sieci wykrytych podczas wzrostu użycia. Zwykle nie jest to konieczne w przypadku małych firm korzystających z Microsoft 365 lub przedsiębiorstw, które mają już prostą i bezpośrednią łączność sieciową. Oczekuje się, że przedsiębiorstwa z ponad 500 użytkownikami i wieloma lokalizacjami biur będą najbardziej korzystne.

## <a name="enterprise-network-connectivity-challenges"></a>Enterprise wyzwania związane z łącznością sieciową

> [!div class="mx-imgBorder"]
> ![Sieć klienta do chmury.](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Wiele przedsiębiorstw ma konfiguracje obwodowe sieci, które rosły w czasie i są przeznaczone przede wszystkim do obsługi dostępu pracowników do witryny internetowej, gdzie większość witryn internetowych nie są znane z wyprzedzeniem i są niezaufane. Nadrzędnym i koniecznym celem jest unikanie złośliwego oprogramowania i ataków phishingowych z tych nieznanych witryn internetowych. Ta strategia konfiguracji sieci, choć przydatna ze względów bezpieczeństwa, może prowadzić do obniżenia wydajności Microsoft 365 użytkownika i środowiska użytkownika.

## <a name="how-we-can-solve-these-challenges"></a>Jak możemy rozwiązać te problemy

Przedsiębiorstwa mogą poprawić ogólne środowisko użytkownika i zabezpieczyć swoje środowisko, stosując [zasady łączności Office 365](./microsoft-365-network-connectivity-principles.md) i korzystając z funkcji łączności sieciowej centrum Administracja Microsoft 365. W większości przypadków zastosowanie tych ogólnych zasad będzie miało znaczący pozytywny wpływ na opóźnienia użytkowników końcowych, niezawodność usługi i ogólną wydajność Microsoft 365.

Firma Microsoft jest czasami proszone o zbadanie problemów z wydajnością sieci w Microsoft 365 dla dużych klientów korporacyjnych, a te często mają główną przyczynę związaną z infrastrukturą obwodową sieci klienta. Po znalezieniu wspólnej głównej przyczyny problemu z obwodem sieci klienta staramy się zidentyfikować proste pomiary testowe. Test z progiem pomiaru, który identyfikuje konkretny problem, jest cenny, ponieważ możemy przetestować tę samą miarę w dowolnej lokalizacji, sprawdzić, czy ta główna przyczyna jest tam obecna, i udostępnić ją administratorowi jako wgląd w sieć.

Niektóre szczegółowe informacje o sieci wskazują jedynie problem, który wymaga dalszego zbadania. Analiza sieci, w której mamy wystarczająco dużo testów, aby pokazać określoną akcję korygowania w celu skorygowania głównej przyczyny, jest wymieniona jako **zalecana akcja**. Te zalecenia, oparte na metrykach na żywo, które ujawniają wartości, które wykraczają poza wstępnie określony próg, są znacznie cenniejsze niż ogólne porady dotyczące najlepszych rozwiązań, ponieważ są specyficzne dla danego środowiska i pokażą rzeczywistą poprawę po wprowadzeniu zalecanych zmian.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Omówienie łączności sieciowej w centrum Administracja Microsoft 365

Firma Microsoft ma istniejące pomiary sieci od kilku Office klientów stacjonarnych i internetowych, które obsługują działanie Microsoft 365. Te pomiary są teraz używane do dostarczania szczegółowych informacji na temat projektowania architektury sieci i oceny sieci, które są wyświetlane na stronie **Łączność sieciowa** w centrum Administracja Microsoft 365.

Domyślnie przybliżone informacje o lokalizacji skojarzone z pomiarami sieci identyfikują miasto, w którym znajdują się urządzenia klienckie. Ocena sieci w każdej lokalizacji jest wyświetlana z kolorem, a względna liczba użytkowników w każdej lokalizacji jest reprezentowana przez rozmiar okręgu.

> [!div class="mx-imgBorder"]
> ![Mapa przeglądu usługi Network Insights.](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

Na stronie przeglądu przedstawiono również ocenę sieci dla klienta jako średnią ważoną we wszystkich lokalizacjach biura.

> [!div class="mx-imgBorder"]
> ![Ocena sieci.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Możesz wyświetlić widok tabeli lokalizacji, w których można je filtrować, sortować i edytować na **karcie Lokalizacje** . Lokalizacje z określonymi zaleceniami mogą również obejmować szacowane potencjalne zwiększenie opóźnienia. Jest to obliczane przez pobranie mediany opóźnienia użytkowników organizacji w lokalizacji i odjęcie mediany opóźnienia dla wszystkich organizacji w tym samym mieście.

> [!div class="mx-imgBorder"]
> ![Lokalizacje szczegółowych informacji o sieci.](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Ocena zdalnego procesu roboczego i metryki połączeń użytkowników

Klasyfikujemy dzienniki ruchu sieciowego jako użytkowników zdalnych lub lokalnych i pokazujemy ich wartości procentowe w sekcji metryk połączeń użytkownika w okienku przeglądu. W przypadku miast, w których masz użytkowników zdalnych, po otwarciu strony tej lokalizacji znajdziesz ocenę oceny określonej lokalizacji dla sieci zdalnej. Lista lokalizacji będzie zawierać zarówno lokalizacje biurowe, jak i miasta pracowników zdalnych, które można filtrować i sortować. Zapewniamy ocenę oceny zdalnego procesu roboczego z podziałem punktów dla Exchange, SharePoint i Teams.

Szczegółowe informacje dotyczące sieci użytkowników domowych są agregowane i raportowane na poziomie miasta i ograniczone do miast z co najmniej 5 pracownikami zdalnymi. Nie identyfikujemy poszczególnych pracowników pracujących z domu.

Lokalizacje są automatycznie klasyfikowane jako lokalne lub zdalne, jednak możesz ręcznie wprowadzić wszystkie adresy IP ruchu wychodzącego w lokacji, aby zapewnić klasyfikację w 100%. Jeśli zdecydujesz się na tę trasę, po dodaniu wszystkich wychodzących adresów IP ruchu wychodzącego w lokalizacji w lokalizacji Ustawienia wysuwanej po dodaniu wszystkich adresów IP ruchu wychodzącego należy **zaznaczyć pole wyboru Wprowadź wszystkie adresy IP ruchu** wychodzącego. Po wykonaniu tej czynności wszystkie dzienniki ruchu sieciowego z wychodzących adresów IP, które zostały oznaczone jako lokalne, będą zawsze klasyfikowane jako biura, a każdy inny wychodzący adres IP zostanie sklasyfikowany jako zdalny.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Podsumowanie wydajności sieci lokalizacji biura i szczegółowe informacje

Wybranie lokalizacji biura powoduje otwarcie strony podsumowania specyficznej dla lokalizacji zawierającej szczegółowe informacje o ruchu wychodzącym sieci, który został zidentyfikowany na podstawie pomiarów dla tej lokalizacji biura.

> [!div class="mx-imgBorder"]
> ![Szczegółowe informacje o sieci według lokalizacji.](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Mapa sieci obwodowej dla użytkowników organizacji w lokalizacji jest wyświetlana z niektórymi lub wszystkimi następującymi elementami:

- **Office lokalizacji** — lokalizacja biura dla strony, na którą patrzysz
- **Obwód sieci** — lokalizacja źródłowego adresu IP dla połączeń z lokalizacji biura. Zależy to od dokładności baz danych lokalizacji geo-IP
- **Exchange optymalne drzwi wejściowe usługi** — jedna z zalecanych Exchange drzwi wejściowych usługi, z którymi użytkownicy w tej lokalizacji biura powinni się łączyć
- **Exchange nieoptymalne drzwi wejściowe** — brama frontowa usługi Exchange, z którą użytkownicy są połączeni, ale nie jest zalecana
- **SharePoint optymalne drzwi wejściowe usługi** — jeden z zalecanych drzwi frontowych usługi SharePoint, z którymi użytkownicy w tej lokalizacji biura powinni się połączyć
- **SharePoint nieoptymalne drzwi wejściowe usługi** — brama frontowa usługi SharePoint, z którą użytkownicy są połączeni, ale nie jest zalecana
- **Serwer rekursywnego rozpoznawania nazw DNS** — lokalizacja z bazy danych geograficznych adresów IP wykrytego rekursywnego rozpoznawania nazw DNS używanego do Exchange Online (jeśli jest dostępna)
- **Serwer proxy** — lokalizacja z bazy danych geograficznych adresów IP wykrytego serwera proxy (jeśli jest dostępna)

Na stronie podsumowania lokalizacji biura dodatkowo przedstawiono ocenę sieci lokalizacji, historię oceny sieci, porównanie oceny tej lokalizacji z innymi klientami w tym samym mieście oraz listę szczegółowych informacji i zaleceń, które można podjąć w celu zwiększenia wydajności i niezawodności sieci.

Porównania między klientami w tym samym mieście są oparte na oczekiwaniach, że wszyscy klienci mają równy dostęp do dostawców usług sieciowych, infrastruktury telekomunikacyjnej i pobliskich punktów sieciowych firmy Microsoft.

Nazwy lokalizacji można dostosować podczas dodawania nowej lokalizacji lub edytowania istniejącej lokalizacji w wysuwanej lokalizacji. Zapewnia to elastyczność dostosowywania nazw lokalizacji w dowolnym momencie. Ponadto podczas dodawania podsieci LAN bezpośrednio w wysuwanej lokalizacji wyświetlamy listę rozwijaną podsieci LAN dopasowanych nietrwale, z których można wybrać. Nazwy obwodów dla określonych adresów IP ruchu wychodzącego biura można również dodawać i edytować.

Karta szczegółów na stronie lokalizacji biura pokazuje konkretne wyniki pomiaru, które zostały użyte do wyświetlenia szczegółowych informacji, zaleceń i oceny sieci. Jest to możliwe, aby inżynierowie sieci mogli weryfikować zalecenia i uwzględniać wszelkie ograniczenia lub szczegóły w swoim środowisku. Szacowaną liczbę użytkowników zebranych próbek można również znaleźć w tych lokalizacjach biurowych, a także pracowników zdalnych w tym mieście.

> [!div class="mx-imgBorder"]
> ![Szczegóły specyficzne dla lokalizacji.](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="sharing-network-assessment-data-with-microsoft"></a>Udostępnianie danych oceny sieci firmie Microsoft

Domyślnie oceny sieci dla organizacji i szczegółowe informacje o sieci są udostępniane pracownikom firmy Microsoft. Nie obejmuje to żadnych danych osobowych pracowników, ale tylko określonych metryk oceny sieci i szczegółowych informacji o sieci wyświetlanych w centrum administracyjnym dla lokalizacji biura. Nie zawiera również nazw lokalizacji biura ani adresów ulic, więc musisz poinformować je o mieście i identyfikatorze pomocy technicznej biura, które chcesz omówić. Jeśli ta funkcja jest wyłączona, inżynierowie firmy Microsoft, z którą omawiasz łączność sieciową, nie mogą wyświetlić żadnej z tych informacji. Włączenie tego ustawienia powoduje udostępnienie tylko przyszłych danych, począwszy od dnia po ich włączeniu.

## <a name="csv-import-for-lan-subnet-office-locations"></a>Importowanie pliku CSV dla lokalizacji biura podsieci LAN

W przypadku identyfikacji biura podsieci SIECI LAN należy dodać każdą lokalizację z wyprzedzeniem. Zamiast dodawać poszczególne lokalizacje biura na **karcie Lokalizacje** , można je zaimportować z pliku CSV. Możesz uzyskać te dane z innych przechowywanych przez Ciebie miejsc, takich jak pulpit nawigacyjny jakości wywołań lub witryny i usługi Active Directory

W pliku CSV odnaleziona lokalizacja miasta jest wyświetlana w kolumnie userEntered jako pusta, a ręcznie dodana lokalizacja biura jest wyświetlana jako 1.

1. W głównym oknie _Łączność z Microsoft 365_ kliknij kartę **Lokalizacje**.

1. Kliknij przycisk **Importuj** tuż nad listą lokalizacji. Zostanie wyświetlone okno wysuwane **Importowanie lokalizacji biura** .

   > [!div class="mx-imgBorder"]
   > ![Komunikat importu CSV.](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Kliknij link **Pobierz bieżące lokalizacje biura (.csv** ), aby wyeksportować listę bieżących lokalizacji do pliku CSV i zapisać ją na lokalnym dysku twardym. Zapewni to poprawne formatowanie pliku CSV z nagłówkami kolumn, do których można dodawać lokalizacje. Istniejące wyeksportowane lokalizacje można pozostawić w miarę ich istnienia. Nie zostaną one zduplikowane podczas importowania zaktualizowanego pliku CSV. Jeśli chcesz zmienić adres istniejącej lokalizacji, zostanie on zaktualizowany podczas importowania pliku CSV. Nie można zmienić adresu odnalezionego miasta.

1. Otwórz plik CSV i dodaj lokalizacje, wypełniając następujące pola w nowym wierszu dla każdej lokalizacji, którą chcesz dodać. Pozostaw wszystkie pozostałe pola puste; wartości wprowadzone w innych polach zostaną zignorowane.

   1. **userEntered** (wymagane): musi mieć wartość 1 dla nowej lokalizacji biura podsieci SIECI LAN
   1. **Nazwa** (wymagana): nazwa lokalizacji biura
   1. **Adres** (wymagany): adres fizyczny biura
   1. **Szerokość geograficzna** (opcjonalnie): wypełnione z Bing mapuje wyszukiwanie adresu, jeśli jest puste
   1. **Długość geograficzna** (opcjonalnie): wypełnione z Bing mapuje wyszukiwanie adresu, jeśli jest puste
   1. **Egress zakresy adresów IP 1–5** (opcjonalnie): dla każdego zakresu wprowadź nazwę obwodu, a następnie rozdzielaną spacjami listę prawidłowych adresów CIDR IPv4. Te wartości służą do rozróżniania wielu lokalizacji biurowych, w których są używane te same adresy IP podsieci SIECI LAN. Egress zakresy adresów IP muszą mieć rozmiar sieci /24, a /24 nie jest uwzględniony w danych wejściowych.
   1. **LanIps** (wymagane): wyświetl listę zakresów podsieci SIECI LAN używanych w tej lokalizacji biura. Identyfikatory podsieci sieci LAN muszą mieć rozmiar sieci CIDR, w którym rozmiar sieci może wynosić od /8 do /29. Wiele zakresów podsieci SIECI LAN można rozdzielić przecinkami lub średnikami.

1. Po dodaniu lokalizacji biura i zapisaniu pliku kliknij przycisk **Przeglądaj** obok pola **Przekaż ukończone** i wybierz zapisany plik CSV.

1. Plik zostanie automatycznie zweryfikowany. Jeśli występują błędy walidacji, zostanie wyświetlony komunikat o błędzie: _W pliku importu występują błędy. Przejrzyj błędy, popraw plik importu, a następnie spróbuj ponownie._ Kliknij link **Otwórz szczegóły błędu** , aby uzyskać listę błędów walidacji określonych pól.

   > [!div class="mx-imgBorder"]
   > ![Komunikat o błędzie importu CSV.](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. Jeśli w pliku nie ma żadnych błędów, zostanie wyświetlony komunikat: _Raport jest gotowy. Znaleziono lokalizacje x do dodania i x lokalizacji do zaktualizowania._ Kliknij przycisk **Importuj** , aby przekazać plik CSV.

   > [!div class="mx-imgBorder"]
   > ![Gotowy komunikat dotyczący importowania pliku CSV.](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="cqd-tsv-import-for-lan-subnet-office-locations"></a>CQD TSV Import for LAN subnet office locations (Importowanie TSV CQD dla lokalizacji biura podsieci LAN)

Jeśli dane kompilowania zostały przekazane do pulpitu nawigacyjnego jakości połączeń, możesz dodać te lokalizacje tutaj, aby rozpocząć ocenę łączności sieciowej. Nie wpłynie to na istniejące lokalizacje.

[Przejdź do obszaru Przekazywanie danych dzierżawy](https://cqd.teams.microsoft.com/spd/#/TenantDataUpload) na pulpicie nawigacyjnym jakości wywołań. Jeśli przekazano dane budynku, zostanie wyświetlona opcja pobrania ich do pliku tsv. Pobierz plik tsv z pulpitu nawigacyjnego call quality, a następnie przekaż go w wysuwie CQD, wykonując poniższe kroki. Jeśli chcesz ręcznie utworzyć plik tsv, wyrównaj schemat do schematu w sekcji Przekazywanie pliku danych kompilacji lub spróbuj zamiast tego wypróbować lokalizacje biura csv import for LAN.

1. W głównym oknie Łączność z Microsoft 365 kliknij kartę **Lokalizacje**.

2. Kliknij przycisk **Zarządzaj wieloma lokalizacjami** tuż nad listą lokalizacji.

   > [!div class="mx-imgBorder"]
   > ![Menu Zarządzanie wieloma lokalizacjami.](../media/m365-mac-perf/m365-mac-perf-import-cqd-manage-multiple.png)

3. Kliknij pozycję **Dodaj lokalizacje z pulpitu nawigacyjnego jakości połączeń**. Zostanie wyświetlone okno wysuwane **Dodawanie lokalizacji z pulpitu nawigacyjnego jakości wywołań** .

   > [!div class="mx-imgBorder"]
   > ![Dodaj lokalizacje z wysuwanego pulpitu nawigacyjnego jakości wywołań.](../media/m365-mac-perf/m365-mac-perf-import-cqd-add-locations.png)

4. Kliknij przycisk **Przeglądaj** obok pola **Wybierz plik tsv do przekazania** i wybierz zapisany plik TSV. Upewnij się, że wartość w pliku jest oddzielona kartą.

5. Plik zostanie automatycznie zweryfikowany i przeanalizowany na liście lokalizacji biura. Jeśli występują błędy walidacji, zostanie wyświetlone okno wysuwane Nie **można przekazać pliku** , aby wyświetlić listę błędów.

   > [!div class="mx-imgBorder"]
   > ![Nie można przekazać wysuwanego pliku.](../media/m365-mac-perf/m365-mac-perf-import-cqd-couldnt-upload.png)

6. Jeśli w pliku nie ma żadnych błędów, zostanie wyświetlony komunikat: _Plik test.tsv został przekazany i gotowy. Wybierz pozycję Importuj, aby przekazać informacje._

   > [!div class="mx-imgBorder"]
   > ![Wybierz plik tsc do przekazania.](../media/m365-mac-perf/m365-mac-perf-import-cqd-select-tsv.png)

7. Kliknij przycisk **Przekaż** w dolnej części panelu, aby przekazać lokalizacje biura.

## <a name="faq"></a>Często zadawane pytania

### <a name="what-is-a-microsoft-365-service-front-door"></a>Co to jest brama Microsoft 365 usługi?

Brama frontowa usługi Microsoft 365 jest punktem wejścia w globalnej sieci firmy Microsoft, gdzie Office klienci i usługi przerywają połączenie sieciowe. W celu uzyskania optymalnego połączenia sieciowego z Microsoft 365 zaleca się zakończenie połączenia sieciowego w najbliższej Microsoft 365 drzwiach wejściowych.

> [!NOTE]
> Microsoft 365 usługa front door nie ma bezpośredniej relacji z produktem usługi Azure Front Door Service dostępnym na platformie Azure Marketplace.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>Co to jest optymalna Microsoft 365 usługi front door?

Optymalną Microsoft 365 usługą front door jest brama, która znajduje się najbliżej ruchu wychodzącego sieci, zazwyczaj w twoim mieście lub obszarze metra. Użyj [narzędzia do testowania łączności Microsoft 365](office-365-network-mac-perf-onboarding-tool.md), aby określić lokalizację używanej bramy frontowej usługi Microsoft 365 i optymalną usługę front door. Jeśli narzędzie ustali, że używana brama frontowa jest optymalna, optymalnie łączysz się z siecią globalną firmy Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Co to jest internetowa lokalizacja ruchu wychodzącego?

Lokalizacja ruchu wychodzącego z Internetu to lokalizacja, w której ruch sieciowy opuszcza sieć przedsiębiorstwa i łączy się z Internetem. Jest to również identyfikowane jako lokalizacja, w której masz urządzenie translatora adresów sieciowych (NAT) i zwykle w którym łączysz się z dostawcą usług internetowych. Jeśli widzisz dużą odległość między lokalizacją i lokalizacją internetowego ruchu wychodzącego, może to wskazywać na znaczący backhaul sieci WAN.

### <a name="what-license-is-needed-for-this-capability"></a>Jaka licencja jest potrzebna dla tej możliwości?

Wymagana jest licencja zapewniająca dostęp do Centrum administracyjne platformy Microsoft 365.

## <a name="related-topics"></a>Tematy pokrewne

[Microsoft 365 szczegółowych informacji o sieci](office-365-network-mac-perf-insights.md)

[ocena sieci Microsoft 365](office-365-network-mac-perf-score.md)

[narzędzie do testowania łączności Microsoft 365](office-365-network-mac-perf-onboarding-tool.md)

[usługi lokalizacji łączności sieciowej Microsoft 365](office-365-network-mac-location-services.md)
