---
title: Konfigurowanie ustawień ochrony przed utratą danych w punkcie końcowym
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Dowiedz się, jak skonfigurować ustawienia centralne ochrony przed utratą danych (DLP, Endpoint Data Loss Prevention).
ms.openlocfilehash: ebe995512769275999e7ec4837e16542ffce7100
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705690"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Konfigurowanie ustawień ochrony przed utratą danych w punkcie końcowym

Wiele aspektów zachowania ochrony przed utratą danych w punktach końcowych (DLP) jest kontrolowanych przez centralnie skonfigurowane ustawienia. Ustawienia są stosowane do wszystkich zasad DLP dla urządzeń.

![Ustawienia ochrony przed DLP punktu końcowego](../media/endpoint-dlp-1-using-dlp-settings.png)

Te ustawienia musisz skonfigurować, jeśli chcesz kontrolować:

- Ograniczenia ruchu wychodzącego w chmurze
- Różne typy restrykcyjnych działań na użytkownikach w poszczególnych aplikacjach.
- Wykluczenia ścieżek plików dla Windows i macOS.
- Ograniczenia przeglądarki i domeny.
- Jak biznesowe justowanie dla zastępowania zasad jest wyświetlane w poradach dotyczących zasad.
- Jeśli działania dotyczące plików Office, PDF i CSV są automatycznie insektowane.

## <a name="dlp-settings"></a>Ustawienia DLP

Przed rozpoczęciem należy skonfigurować ustawienia zasad DLP. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Ustawienia parametru DLP Windows 10/11 i systemu macOS

|Ustawienie |Windows 10, 1809 i nowsze, Windows 11  |system macOS Catalina 10.15 lub nowszy (wersja zapoznawcza)  |Uwagi  |
|---------|---------|---------|---------|
|Wykluczenia ścieżek plików     |Obsługiwane         |Obsługiwane         |System macOS zawiera listę zalecanych wykluczeń, która jest domyślnie włączona          |
|Aplikacje z ograniczeniami     |Obsługiwane         |Obsługiwane         |         |
|Grupy aplikacji z ograniczeniami |Obsługiwane |Nieobsługiwane
|Niedozwolone aplikacje Bluetooth aplikacji    |Obsługiwane         |Nieobsługiwane         |         |
|Ograniczenia przeglądarki i domeny dotyczące elementów poufnych      |Obsługiwane         |Obsługiwane         |         |
|Dodatkowe ustawienia dotyczące ochrony przed osią danych (DLP) dla punktu końcowego     |Obsługiwane         |Obsługiwane         |W przypadku urządzeń z systemem macOS są obsługiwane tylko domyślne justowania biznesowe         |
|Zawsze inspekcja działań na plikach dla urządzeń     |Obsługiwane         |Obsługiwane         |         |
|Automatyczne poddaj plikowi kwarantanny z aplikacji niezaszepowiednianych | Obsługiwane | Nieobsługiwane| |
|Klasyfikacja zaawansowana | Obsługiwane | Nieobsługiwane| |
|Uzasadnienie biznesowe w poradach dotyczących zasad | Obsługiwane | Obsługiwane| |

### <a name="advanced-classification-scanning-and-protection"></a>Zaawansowane skanowanie klasyfikacji i ochrona

Zaawansowane skanowanie klasyfikacji i ochrony umożliwia im bardziej zaawansowane Microsoft 365 klasyfikacji danych w chmurze, może skanować, klasyfikować je i zwracać wyniki na komputer lokalny. Oznacza to, że możesz korzystać z technik klasyfikacji[](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md), takich jak dokładna klasyfikacja dopasowania danych, nazwane jednostki [(wersja zapoznawcza)](named-entities-learn.md#learn-about-named-entities-preview) i przeszkolne klasyfikatory w twoich zasadach ochrony przed zasadami DLP.[](classifier-learn-about.md#learn-about-trainable-classifiers)

Gdy jest włączona zaawansowana klasyfikacja, zawartość jest wysyłana z urządzenia lokalnego do usług w chmurze w celu skanowania i klasyfikacji. Jeśli wykorzystanie przepustowości jest problemem, możesz ustawić limit wykorzystania w okresie 24 godzin. Limit jest konfigurowany w ustawieniach ochrony przed dlp punktami końcowymi i jest stosowany na urządzenie. Jeśli ustawisz limit użycia przepustowości i zostanie on przekroczony, rozwiązanie DLP przestanie wysyłać zawartość użytkownika do chmury. Na tym etapie klasyfikacja danych jest kontynuowana lokalnie na urządzeniu, ale klasyfikacja z zastosowaniem dokładnego dopasowania danych, nazwanych jednostek (wersja Zapoznawcza) i klasyfikatorów przeszkolnych nie są dostępne. Gdy skumulowane użycie przepustowości spadnie poniżej 24-godzinnego limitu, zostanie wznowiona komunikacja z usługami w chmurze.

Jeśli użycie przepustowości nie jest problemem, wybierz pozycję **Bez limitu** , aby zezwolić na nieograniczone wykorzystanie przepustowości.

Te Windows obsługują zaawansowane skanowanie klasyfikacji i ochrony:

- Windows 10 20H1/20H2/21H1 (KB 5006738)
- Windows 10 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (kb 5006744)

> [!NOTE]
> Obsługa klasyfikacji zaawansowanej jest dostępna dla Office plików (Word, Excel, PowerPoint) i plików PDF.

> [!NOTE]
> Ocena zasad DLP zawsze odbywa się w chmurze, nawet jeśli zawartość użytkownika nie jest wysyłana.

### <a name="file-path-exclusions"></a>Wykluczenia ścieżek plików

Otwórz [Centrum zgodności](https://compliance.microsoft.com) >  **Zapobieganie utraciedanychUzyszania** >  **danychUkluczenia ścieżek plików w** >  programie **DLP**.

Możesz zechcieć wykluczyć określone ścieżki z monitorowania DLP, alertów DLP i wymuszania zasad DLP na twoich urządzeniach, ponieważ są one zbyt głośne lub nie zawierają plików, które Cię interesują. Pliki w tych lokalizacjach nie będą objęte inspekcją, a żadne pliki, które zostały utworzone lub zmodyfikowane w tych lokalizacjach, nie będą podlegać wymuszaniom zasad DLP. W ustawieniach DLP można konfigurować wykluczenia ścieżek.

#### <a name="windows-10-devices"></a>Windows 10 urządzenia

Za pomocą tej logiki można utworzyć ścieżki wykluczeń dla Windows 10 urządzeniach:

- Prawidłowa ścieżka pliku, która kończy się na `\`, co oznacza tylko pliki bezpośrednio pod folderem. <br/>Na przykład: `C:\Temp\`

- Prawidłowa ścieżka pliku, która kończy się na `\*`, co oznacza tylko pliki w podfolderach, oprócz plików bezpośrednio pod folderem. <br/>Na przykład: `C:\Temp\*`

- Prawidłowa ścieżka pliku, która kończy się bez `\` `\*`lub , co oznacza, że wszystkie pliki są bezpośrednio pod folderem i wszystkimi podfolderami. <br/>Na przykład: `C:\Temp`

- Ścieżka z symbolami wieloznacznymi między `\` poszczególnymi bokami. <br/>Na przykład: `C:\Users\*\Desktop\`

- Ścieżka z symbolami wieloznacznymi `\` między poszczególnymi stronami i z `(number)` , aby zapewnić dokładną liczbę podfolderów. <br/>Na przykład: `C:\Users\*(1)\Downloads\`

- Ścieżka ze zmiennymi środowiskowym SYSTEM. <br/>Na przykład: `%SystemDrive%\Test\*`

- Połączenie wszystkich powyższych danych. <br/>Na przykład: `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices-preview"></a>Urządzenia z systemem macOS (wersja zapoznawcza)

Podobnie jak w Windows 10 możesz dodać własne wykluczenia dla urządzeń macOS.

- Definicje ścieżki pliku nie są bez uwzględniania liter, `User` więc są takie same jak `user`w przypadku plików .

- Obsługiwane są wartości symboli wieloznacznych. Definicja ścieżki może zatem zawierać środek `*` ścieżki lub na jej końcu. Na przykład: `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Zalecane wykluczenia ścieżek plików (wersja Zapoznawcza)

Ze względów wydajności ochrona przed punktami końcowymi zawiera listę zalecanych wykluczeń ścieżki pliku dla urządzeń z systemem macOS. Te wykluczenia są domyślnie włączone. Możesz je wyłączyć, przełączaąc przełącznik Uwzględnij zalecane wykluczenia ścieżek plików dla komputerów **Mac** . Lista zawiera:

- /Programy/*
- /System/*
- /usr/*
- /Library/*
- /private/*
- /opt/*
- /Użytkownicy/*/Biblioteki/Application Support/Microsoft/Teams/*

### <a name="restricted-apps-and-app-groups"></a>Ograniczone aplikacje i grupy aplikacji

#### <a name="restricted-apps"></a>Aplikacje z ograniczeniami

**Aplikacje z** ograniczeniami (wcześniej nazywane **aplikacjami niedozwolone**) to lista tworzyć aplikacje. Konfigurowanie akcji, jakie będzie podejmowane przez działanie ochrony przed działaniem, gdy użytkownik korzysta z aplikacji **** na liście w celu uzyskania dostępu do pliku chronionego DLP na urządzeniu. Jest dostępna dla urządzeń z systemem Windows 10 i macOS (wersja zapoznawcza).

Jeśli **w** zasadach wybrano opcję Dostęp przez aplikacje z ograniczeniami i użytkownik korzysta z aplikacji, która znajduje się na liście aplikacji z ograniczeniami, aby uzyskać dostęp do pliku chronionego, `audited``blocked``blocked with override` działanie to , lub, w zależności od tego, jak je skonfigurowano. Jeśli ta sama aplikacja nie jest członkiem grupy aplikacji z ograniczeniami **, akcje** skonfigurowane dla działań w grupie Aplikacja z ograniczeniami  zastępują akcje skonfigurowane dla działania dostępu dla listy Aplikacje z **ograniczeniami.** Wszystkie działania są sprawdzane i można je przejrzeć w Eksploratorze aktywności.

> [!IMPORTANT]
> Nie dołączaj ścieżki do pliku wykonywalnego, ale tylko nazwy pliku wykonywalnego (na przykład browser.exe).

> [!IMPORTANT]
> Akcja (`audit`, lub `block`) zdefiniowana dla aplikacji, które znajdują się na liście aplikacji z ograniczeniami, ma zastosowanie tylko wtedy, `block with override`gdy użytkownik próbuje ***uzyskać dostęp do*** chronionego elementu. 

#### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Działania związane z plikami aplikacji w grupach aplikacji z ograniczeniami (wersja Preview)

Grupy aplikacji z ograniczeniami to kolekcje aplikacji, które tworzysz w ustawieniach ochrony przed prywatnością, a następnie dodajesz do reguły w zasadach. Po dodaniu grupy aplikacji z ograniczeniami do zasad można używać akcji zdefiniowanych w tej tabeli.

|Opcja grupy aplikacji z ograniczeniami  |Co to umożliwia  |
|---------|---------|
|Nie ograniczaj aktywności na plikach     |Dzięki funkcji DLP użytkownicy mogą uzyskać dostęp do elementów chronionych za pomocą funkcji DLP przy użyciu aplikacji w grupie aplikacji i nie podejmowali żadnych działań, gdy użytkownik próbuje skopiować do schowka **, skopiować** do schowka, skopiować na dysk wymienny **USB****, skopiować** na dysk sieciowy i wydrukować z aplikacji.          |
|Stosowanie ograniczenia do wszystkich działań     |Informuje o próbie `Audit only``Block with override`uzyskania `Block` przez użytkownika dostępu do elementu chronionego DLP przy użyciu aplikacji, która jest w tej grupie aplikacji, lub gdy użytkownik próbuje uzyskać dostęp do elementu chronionego przez DLP.         |
|Stosowanie ograniczeń do określonego działania     |To ustawienie umożliwia użytkownikowi uzyskiwanie dostępu do elementu chronionego przez działanie funkcji DLP przy użyciu aplikacji, która znajduje się w grupie aplikacji, `Block``Block with override`i pozwala wybrać domyślną akcję (`Audit only`lub) ochrony przed dlp, która ma być podejmowana, gdy użytkownik próbuje skopiować do schowka **, pozycję** Kopiuj na dysk wymienny **USB****, pozycję** Kopiuj na dysk sieciowy i pozycję **Drukuj**.          |

> [!IMPORTANT]
> Ustawienia w grupie aplikacji z ograniczeniami zastępują wszelkie ograniczenia określone na liście aplikacji z ograniczeniami, gdy znajdują się w tej samej  regułach. Zatem jeśli aplikacja znajduje się na liście aplikacji z ograniczeniami i należy do grupy aplikacji z ograniczeniami, zostaną zastosowane ustawienia grupy aplikacji z ograniczeniami.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>Jak zasady DLP stosuje ograniczenia dotyczące działań

Interakcje **między działaniami pliku dla aplikacji w grupach** aplikacji z ograniczeniami (wersja Preview)**, Działania** dotyczące plików we wszystkich aplikacjach i lista Działania aplikacji z ograniczeniami są ograniczone do tej samej reguły.

##### <a name="restricted-app-groups-overrides"></a>Ograniczone zastępowanie grup aplikacji

Konfiguracje zdefiniowane w **działaniach na** plikach dla aplikacji w grupach aplikacji z ograniczeniami (wersja Preview) zastępują konfiguracje na liście Działania aplikacji z ograniczeniami oraz Działania na plikach dla wszystkich **aplikacji w tej** samej regułach.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Ograniczone działania aplikacji i Działania na plikach dla wszystkich aplikacji

Konfiguracje działań **aplikacji**   `Audit only``Block with override` z ograniczeniami i Działania dotyczące plików dla wszystkich aplikacji działają zgodnie z działaniem, jeśli akcja zdefiniowana dla działań aplikacji z ograniczeniami jest albo w tej samej regułie. Dzieje się tak, ponieważ akcje  zdefiniowane dla działań w aplikacjach z ograniczeniami są stosowane tylko wtedy, gdy użytkownik uzyskuje dostęp do pliku przy użyciu aplikacji, która znajduje się na liście. Gdy użytkownik ma dostęp, mają zastosowanie akcje zdefiniowane dla działań w **działaniach na plikach we wszystkich aplikacjach** . 

Oto przykład:

Jeśli Notepad.exe dodano do ustawień Aplikacje z ograniczeniami i Działania  na plikach dla wszystkich aplikacji skonfigurowano stosowanie  ograniczeń do określonej aktywności, a obie te aplikacje są skonfigurowane w ten sposób:

|Ustawienie w zasadach  |Nazwa aplikacji  |Aktywność użytkowników  |Akcja zasad DLP do podjęcia  |
|---------|---------|---------|---------|
|Działania aplikacji z ograniczeniami     |Notatnik        |Uzyskiwanie dostępu do elementu chronionego DLP         |Tylko inspekcja         |
|Działania dotyczące plików dla wszystkich aplikacji   |Wszystkie aplikacje        | Kopiuj do schowka        |Tylko inspekcja         |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Kopiowanie na urządzenie, które można usunąć przez USB | Blokuj       |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Kopiowanie do udziału sieciowego         |Tylko inspekcja         |
|Działania dotyczące plików dla wszystkich aplikacji   |Wszystkie aplikacje         |Drukowanie         |Blokuj         |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Kopiowanie lub przenoszenie przy użyciu niedozwolonej Bluetooth aplikacji         |Zablokowane         |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Usługi pulpitu zdalnego         |Blokuj z zastępowaniem         |

Użytkownik A otwiera plik chroniony DLP przy użyciu Notatnik. Funkcja DLP umożliwia dostęp do działań i inspekcje. Gdy użytkownik A Notatnik w trybie Notatnik następnie próbuje skopiować do Schowka z chronionego elementu, takie działanie działa i inspekcje DLP. Użytkownik A spróbuje następnie wydrukować chroniony element z Notatnik i działanie zostanie zablokowane.

> [!NOTE]
> Jeśli akcja DLP  `block`, która ma być podjęcia w działaniach aplikacji z ograniczeniami jest ustawiona na , dostęp jest zablokowany i użytkownik nie może wykonywać żadnych działań na pliku.
   
##### <a name="file-activities-for-all-apps-only"></a>Działania dotyczące plików tylko dla wszystkich aplikacji

Jeśli aplikacja nie ma działań na plikach dla aplikacji w grupach aplikacji z ograniczeniami **(wersja Preview)** `Audit only`lub nie znajduje się na liście Działania aplikacji z  ograniczeniami albo znajduje się na liście Działania aplikacji z ograniczeniem z akcją albo "Blokuj  z zastępowaniem", wszelkie ograniczenia określone w działaniach dotyczących plików dla wszystkich aplikacji są stosowane w tej samej regułzie.  

#### <a name="macos-devices-preview"></a>Urządzenia z systemem macOS (wersja zapoznawcza)

Podobnie jak na Windows, teraz będzie można zablokować aplikacjom macOS dostęp do poufnych danych, definiując je na liście **Działań aplikacji z ograniczeniami**. 

> [!NOTE]
> Zwróć uwagę, że aplikacje międzyplatformowe należy wprowadzać przy użyciu ich unikatowych ścieżek odpowiednich do systemu operacyjnego, na który są uruchomione.

Aby znaleźć pełną ścieżkę aplikacji dla komputerów Mac:

1. Na urządzeniu z systemem macOS otwórz **program Monitor aktywności**. Znajdź i kliknij dwukrotnie proces, który chcesz ograniczyć

2. Wybierz **kartę Otwórz pliki i** porty.
  
3. W przypadku aplikacji macOS potrzebna jest pełna nazwa ścieżki, łącznie z nazwą aplikacji.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Ochrona poufnych danych przed aplikacjami do synchronizacji z chmurą

Aby uniemożliwić synchronizowanie poufnych elementów z chmurą przez aplikacje do synchronizacji w chmurze, takie jak *onedrive.exe*, dodaj aplikację do synchronizacji chmury do listy aplikacji Niezaszepłane. Jeśli aplikacja do synchronizacji w chmurze zablokowana przez aplikację do synchronizacji w chmurze spróbuje uzyskać dostęp do elementu chronionego przez blokującą zasady DLP, rozwiązanie DLP może generować powtarzające się powiadomienia. Możesz uniknąć tych powtarzających się powiadomień, włączając opcję **Autopoddaj** kwarantannę w obszarze **Aplikacje niedozwolone**.  

##### <a name="auto-quarantine-preview"></a>Automatyczne poddaj kwarantannie (podgląd)

> [!NOTE]
> Automatyczna kwarantanna jest obsługiwana tylko Windows 10 w programie

Jeśli ta funkcja jest włączona, auto kwarantanna jest włączana, gdy aplikacja, która nie została włączona, próbuje uzyskać dostęp do poufnego elementu chronionego przez funkcję DLP. Automatyczna kwarantanna powoduje przeniesienie poufnego elementu do skonfigurowanego folderu administratora i pozostawienie **.txtzastępczego** pliku w miejscu oryginału. Tekst w pliku zastępczym można skonfigurować w taki sposób, aby poinformować użytkowników o miejscu, do którego został przeniesiony element, oraz o innych istotnych informacjach.  

Za pomocą automatycznego kwarantanny możesz zapobiec nieskończonemu łańcuchowi powiadomień DLP dla użytkowników i administratorów — zobacz Scenariusz 4. Unikanie w pętli powiadomień [DLP](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview) z aplikacji do synchronizacji chmury za pomocą automatycznego kwarantanny (wersja zapoznawcza).

### <a name="unallowed-bluetooth-apps"></a>Niedozwolone aplikacje Bluetooth aplikacji

Uniemożliwiaj innym osobom przesyłanie plików chronionych przez Twoje zasady za pośrednictwem Bluetooth aplikacji.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Ograniczenia przeglądarki i domeny dotyczące danych poufnych

Ograniczanie plików poufnych, które są zgodne z zasadami, od ich współużytkowania z nieograniczonej domenami usługi w chmurze.

#### <a name="unallowed-browsers"></a>Niedozwolone przeglądarki

W przypadku Windows dodajesz przeglądarki określone przez ich wykonywalne nazwy, które będą blokowane do uzyskiwania dostępu do plików, które są zgodne z warunkami wymuszonych zasad DLP, gdzie ograniczenie przekazywania do usług w chmurze jest ustawione na blokowanie lub blokowanie zastępowania. Gdy te przeglądarki będą zablokowane przez te przeglądarki, użytkownicy końcowi zobaczą wyskakujące powiadomienie z prośbą o otwarcie pliku za pośrednictwem Microsoft Edge.

W przypadku urządzeń z systemem macOS należy dodać pełną ścieżkę pliku. Aby znaleźć pełną ścieżkę aplikacji dla komputerów Mac:

1. Na urządzeniu z systemem macOS otwórz **program Monitor aktywności**. Znajdź i kliknij dwukrotnie proces, który chcesz ograniczyć

2. Wybierz **kartę Otwórz pliki i** porty.
  
3. W przypadku aplikacji macOS potrzebna jest pełna nazwa ścieżki, łącznie z nazwą aplikacji.

#### <a name="service-domains"></a>Domeny usługi

> [!NOTE]
> Ustawienie **Domeny usługi dotyczy** tylko plików przekazanych za pomocą programu Microsoft Edge lub Google Chrome z zainstalowanym rozszerzeniem zgodności [firmy Microsoft](dlp-chrome-learn-about.md#learn-about-the-microsoft-compliance-extension).

Możesz kontrolować, czy poufne pliki chronione przez zasady mogą być przekazywane z usługi do określonych domen Microsoft Edge.

Jeśli tryb listy jest **ustawiony na Blokowanie**, użytkownik nie będzie mógł przekazywać do tych domen poufnych elementów. Jeśli akcja przekazywania zostanie zablokowana, ponieważ element jestowy pasowany do zasad DLP, zasady DLP wygenerują ostrzeżenie lub zablokują przekazywanie poufnego elementu.

Jeśli tryb listy jest ustawiony na Zezwalaj **, użytkownicy** będą mogli przekazywać poufne elementy tylko do tych **** domen, a przekazywanie dostępu do wszystkich innych domen jest niedozwolone.

> [!IMPORTANT]
> Gdy dla trybu ograniczeń usługi jest ustawiona wartość "Zezwalaj", przed wymuszeniami ograniczeń musisz mieć skonfigurowaną co najmniej jedną domenę usługi.

Używanie formatu FQDN domeny usługi bez zakończenia `.` 

Przykład:

 `www.contoso.com` 

Symbole wieloznaczne nie są obsługiwane.

### <a name="additional-settings-for-endpoint-dlp"></a>Dodatkowe ustawienia dotyczące ochrony przed dlp punktu końcowego

#### <a name="business-justification-in-policy-tips"></a>Uzasadnienie biznesowe w poradach dotyczących zasad

Możesz kontrolować sposób interakcji użytkowników z opcją justowania firmy w powiadomieniach porad dotyczących zasad DLP. Ta opcja jest wyświetlana, gdy użytkownicy wykonują działania chronione przez ustawienie **Blokuj z zastępowaniem** w zasadach DLP. To ustawienie globalne. Możesz wybrać jedną z następujących opcji:

- **Pokaż opcje domyślne i niestandardowe** pole tekstowe: Domyślnie użytkownicy mogą wybrać wbudowane justowanie lub wprowadzić własny tekst.
- **Pokaż tylko opcje domyślne**: Użytkownicy mogą wybrać tylko wbudowane justowanie.
- **Pokaż tylko niestandardowe pole tekstowe**: Użytkownicy mogą wprowadzać tylko własne justowanie. W powiadomieniu z poradami o zasadach użytkownika końcowego zostanie wyświetlone tylko pole tekstowe. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Dostosowywanie opcji w menu rozwijaym

Możesz utworzyć maksymalnie pięć dostosowanych opcji, które będą wyświetlane, gdy użytkownicy będą wchodzić w interakcje z poradą z powiadomieniami o zasadach, wybierając **menu rozwijane Dostosuj opcje**. 


|Opcja |Tekst domyślny  |
|---------|---------|
|opcja 1    | **Jest to część ustanowionego przepływu pracy biznesowej**  lub można wprowadzić tekst niestandardowy        |
|opcja 2  |**Mój kierownik zatwierdził tę akcję** lub możesz wprowadzić tekst niestandardowy         |
|opcja 3   |**Wymagany pilny dostęp; Powiadomię kierownika oddzielnie** lub będzie można wprowadzić tekst niestandardowy          |
|Pokaż opcję wyników fałszywie dodatnich     |**Informacje w tych plikach nie są poufne lub** możesz wprowadzić tekst niestandardowy          |
|opcja 5    |**Inny** tekst lub możesz wprowadzić tekst niestandardowy         |

### <a name="always-audit-file-activity-for-devices"></a>Zawsze inspekcja działań na plikach dla urządzeń

Domyślnie, gdy urządzenia są włączone, działania dotyczące plików Office, PDF i CSV są automatycznie sprawdzane i dostępne do przeglądu w Eksploratorze aktywności. Wyłącz tę funkcję, jeśli chcesz, aby to działanie było objęte inspekcją tylko wtedy, gdy włączone urządzenia są uwzględnione w aktywnych zasadach.

Aktywność w plikach będzie zawsze podsyłana w przypadku urządzeń włączonych do pracy, niezależnie od tego, czy są one uwzględnione w aktywnych zasadach.

## <a name="see-also"></a>Zobacz też

- [Informacje na temat ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-getting-started.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Omówienie dołączania Windows 10 i Windows 11 Microsoft 365 urządzeniach](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365 subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD)](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nowy Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
