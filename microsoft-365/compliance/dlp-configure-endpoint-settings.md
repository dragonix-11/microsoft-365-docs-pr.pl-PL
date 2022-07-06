---
title: Konfigurowanie ustawień DLP punktu końcowego
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
description: Dowiedz się, jak skonfigurować centralne ustawienia ochrony przed utratą danych punktu końcowego (DLP).
ms.openlocfilehash: 99598880515dd14bc453ebd61a633be7eb66a9fc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629954"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Konfigurowanie ustawień ochrony przed utratą danych punktu końcowego

Wiele aspektów zachowania ochrony przed utratą danych punktu końcowego (DLP) jest kontrolowanych przez centralnie skonfigurowane ustawienia. Ustawienia są stosowane do wszystkich zasad DLP dla urządzeń.

![Ustawienia DLP punktu końcowego](../media/endpoint-dlp-1-using-dlp-settings.png)

Te ustawienia należy skonfigurować, jeśli zamierzasz kontrolować:

- Ograniczenia ruchu wychodzącego w chmurze
- Różne typy restrykcyjnych akcji dotyczących działań użytkowników na aplikację.
- Wykluczenia ścieżki pliku dla urządzeń z systemem Windows i macOS.
- Ograniczenia przeglądarki i domeny.
- W jaki sposób uzasadnienia biznesowe dotyczące zastępowania zasad są wyświetlane w poradach dotyczących zasad.
- Jeśli działania w plikach Office, PDF i CSV są automatycznie poddawane inspekcji.

## <a name="dlp-settings"></a>Ustawienia DLP

Przed rozpoczęciem należy skonfigurować ustawienia DLP. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Ustawienia protokołu DLP punktu końcowego Windows 10/11 i systemu macOS

|Ustawienie |Windows 10, 1809 i nowsze, Windows 11  |macOS Catalina 10.15 lub nowszy |Uwagi  |
|---------|---------|---------|---------|
|Wykluczenia ścieżki pliku     |Obsługiwane         |Obsługiwane         |System macOS zawiera zalecaną listę wykluczeń, która jest domyślnie włączona          |
|Aplikacje z ograniczeniami     |Obsługiwane         |Obsługiwane         |         |
|Grupy aplikacji z ograniczeniami |Obsługiwane |Nieobsługiwane
|Niedozwolone aplikacje Bluetooth    |Obsługiwane         |Nieobsługiwane         |         |
|Ograniczenia przeglądarki i domeny dotyczące elementów poufnych      |Obsługiwane         |Obsługiwane         |         |
|Dodatkowe ustawienia protokołu DLP punktu końcowego     |Obsługiwane         |Obsługiwane         |Tylko domyślne uzasadnienia biznesowe są obsługiwane dla urządzeń z systemem macOS         |
|Zawsze przeprowadzaj inspekcję działania plików dla urządzeń     |Obsługiwane         |Obsługiwane         |         |
|Plik automatycznej kwarantanny z niezauważalnych aplikacji | Obsługiwane | Nieobsługiwane| |
|Klasyfikacja zaawansowana | Obsługiwane | Nieobsługiwane| |
|Uzasadnienie biznesowe w poradach dotyczących zasad | Obsługiwane | Obsługiwane| |

### <a name="advanced-classification-scanning-and-protection"></a>Zaawansowane skanowanie i ochrona klasyfikacji

Zaawansowane skanowanie i ochrona klasyfikacji umożliwiają bardziej zaawansowanej usłudze klasyfikacji danych opartej na chmurze microsoft Purview skanowanie elementów, klasyfikowanie ich i zwracanie wyników na komputerze lokalnym. Oznacza to, że możesz skorzystać z technik klasyfikacji, takich jak [dokładna klasyfikacja dopasowania danych](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) i [nazwane jednostki](named-entities-learn.md) w zasadach DLP.

Po włączeniu zaawansowanej klasyfikacji zawartość jest wysyłana z urządzenia lokalnego do usług w chmurze w celu skanowania i klasyfikacji. Jeśli wykorzystanie przepustowości jest problemem, możesz ustawić limit ilości, która może być używana w okresie 24-godzinnym. Limit jest skonfigurowany w ustawieniach DLP punktu końcowego i jest stosowany na urządzenie. Jeśli ustawisz limit wykorzystania przepustowości i zostanie przekroczony, usługa DLP przestanie wysyłać zawartość użytkownika do chmury. W tym momencie klasyfikacja danych jest kontynuowana lokalnie na urządzeniu, ale klasyfikacja przy użyciu dokładnego dopasowania danych, nazwanych jednostek i klasyfikatorów z możliwością trenowania nie jest dostępna. Gdy skumulowane wykorzystanie przepustowości spadnie poniżej limitu 24 godzin, komunikacja z usługami w chmurze zostanie wznowiona.

Jeśli wykorzystanie przepustowości nie jest problemem, wybierz pozycję **Bez limitu** , aby zezwolić na nieograniczone wykorzystanie przepustowości.

Te wersje systemu Windows obsługują zaawansowane skanowanie klasyfikacji i ochronę:

- Windows 10 wersje 20H1/20H2/21H1 (KB 5006738)
- Windows 10 wersje 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (KB 5006744)

> [!NOTE]
> Obsługa zaawansowanej klasyfikacji jest dostępna dla typów plików pakietu Office (Word, Excel, PowerPoint) i PDF.

> [!NOTE]
> Ocena zasad DLP zawsze odbywa się w chmurze, nawet jeśli zawartość użytkownika nie jest wysyłana.

### <a name="file-path-exclusions"></a>Wykluczenia ścieżki pliku

Otwórz [portal zgodności Microsoft Purview](https://compliance.microsoft.com) >  **Zastaw ustawienia****DLP** >  punktu końcowego zapobiegania  > **utracie danych Wykluczeń ścieżki pliku**.

Możesz wykluczyć niektóre ścieżki z monitorowania DLP, alertów DLP i wymuszania zasad DLP na urządzeniach, ponieważ są one zbyt hałaśliwe lub nie zawierają plików, które Cię interesują. Pliki w tych lokalizacjach nie będą poddawane inspekcji, a wszystkie pliki utworzone lub zmodyfikowane w tych lokalizacjach nie będą podlegać wymuszania zasad DLP. Wykluczenia ścieżek można skonfigurować w ustawieniach DLP.

#### <a name="windows-10-devices"></a>urządzenia Windows 10

Ta logika służy do tworzenia ścieżek wykluczeń dla urządzeń Windows 10:

- Prawidłowa ścieżka pliku kończąca się ciągiem `\`, co oznacza tylko pliki bezpośrednio w folderze. <br/>Przykład: `C:\Temp\`

- Prawidłowa ścieżka pliku, która kończy się ciągiem `\*`, co oznacza tylko pliki w podfolderach, oprócz plików bezpośrednio w folderze. <br/>Przykład: `C:\Temp\*`

- Prawidłowa ścieżka pliku, która kończy się bez `\` lub `\*`, co oznacza wszystkie pliki bezpośrednio w folderze i wszystkich podfolderach. <br/>Przykład: `C:\Temp`

- Ścieżka z symbolem wieloznacznym między poszczególnymi stronami `\` . <br/>Przykład: `C:\Users\*\Desktop\`

- Ścieżka z symbolem wieloznacznym między `\` z każdej strony i z `(number)` , aby podać dokładną liczbę podfolderów. <br/>Przykład: `C:\Users\*(1)\Downloads\`

- Ścieżka ze zmiennymi środowiskowymi SYSTEM. <br/>Przykład: `%SystemDrive%\Test\*`

- Mieszanka wszystkich powyższych. <br/>Przykład: `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices"></a>Urządzenia z systemem macOS

Podobnie jak w przypadku urządzeń z systemem Windows 10 można dodać własne wykluczenia dla urządzeń z systemem macOS.

- Definicje ścieżek plików nie uwzględniają wielkości liter, więc `User` są takie same jak `user`.

- Obsługiwane są wartości symboli wieloznacznych. Dlatego definicja ścieżki może zawierać `*` element w środku ścieżki lub na końcu ścieżki. Przykład: `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Zalecane wykluczenia ścieżki pliku (wersja zapoznawcza)

Ze względu na wydajność protokół DLP punktu końcowego zawiera listę zalecanych wykluczeń ścieżki pliku dla urządzeń z systemem macOS. Te wykluczenia są domyślnie włączone. Możesz je wyłączyć, jeśli chcesz, przełączając przełącznik **Dołącz zalecane wykluczenia ścieżki pliku dla komputerów Mac** . Lista zawiera następujące elementy:

- /Applications/*
- /System/*
- /usr/*
- /Biblioteka/*
- /private/*
- /opt/*
- /Users/*/Library/Application Support/Microsoft/Teams/*

### <a name="restricted-apps-and-app-groups"></a>Ograniczone aplikacje i grupy aplikacji

#### <a name="restricted-apps"></a>Aplikacje z ograniczeniami

**Aplikacje z ograniczeniami** (wcześniej nazywane **aplikacjami nieobsługiwanych**) to lista utworzonych aplikacji. Można skonfigurować akcje, które DLP będzie podejmować, gdy użytkownik korzysta z aplikacji na liście w celu **_uzyskania dostępu do_** pliku chronionego przez protokół DLP na urządzeniu. Jest ona dostępna dla urządzeń z systemem Windows 10 i macOS.

Gdy w zasadach wybrano opcję **Dostęp przez aplikacje z ograniczeniami** , a użytkownik używa aplikacji, która znajduje się na liście aplikacji z ograniczeniami, aby uzyskać dostęp do chronionego pliku, działanie będzie mieć `audited`wartość , `blocked`lub `blocked with override` w zależności od sposobu jego skonfigurowania. Dzieje się tak, chyba że ta sama aplikacja jest członkiem **grupy aplikacji z ograniczeniami**, a następnie akcje skonfigurowane dla działań w **grupie aplikacji z ograniczeniami** zastępują akcje skonfigurowane dla działania dostępu dla listy **Aplikacje z ograniczeniami** . Wszystkie działania są poddawane inspekcji i dostępne do przeglądania w Eksploratorze działań.

> [!IMPORTANT]
> Nie dołączaj ścieżki do pliku wykonywalnego, ale tylko nazwy wykonywalnej (takiej jak browser.exe).

> [!IMPORTANT]
> Akcja (`audit`, lub `block`) zdefiniowana dla aplikacji znajdujących się na liście aplikacji z ograniczeniami ma zastosowanie tylko wtedy, `block with override`gdy użytkownik próbuje ***uzyskać dostęp*** do chronionego elementu. 

#### <a name="file-activities-for-apps-in-restricted-app-groups"></a>Działania dotyczące plików dla aplikacji w grupach aplikacji z ograniczeniami

Grupy aplikacji z ograniczeniami to kolekcje aplikacji tworzone w ustawieniach DLP, a następnie dodawane do reguły w zasadach. Po dodaniu grupy aplikacji z ograniczeniami do zasad możesz wykonać akcje zdefiniowane w tej tabeli.

|Opcja Grupy aplikacji z ograniczeniami  |Co to pozwala zrobić  |
|---------|---------|
|Nie ograniczaj działania pliku     |Informuje DLP, aby zezwalała użytkownikom na dostęp do chronionych elementów DLP przy użyciu aplikacji w grupie aplikacji i nie podejmowała żadnych akcji, gdy użytkownik próbuje **skopiować do schowka**, **skopiować na dysk wymienny USB**, **skopiować na dysk sieciowy** i **wydrukować** z aplikacji.          |
|Stosowanie ograniczenia do wszystkich działań     |Informuje DLP do `Audit only`, `Block with override`lub `Block` gdy użytkownik próbuje uzyskać dostęp do chronionego elementu DLP przy użyciu aplikacji, która jest w tej grupie aplikacji         |
|Stosowanie ograniczeń do określonego działania     |To ustawienie umożliwia użytkownikowi dostęp do chronionego elementu DLP przy użyciu aplikacji, która znajduje się w grupie aplikacji i umożliwia wybranie domyślnej akcji (`Audit only``Block`lub `Block with override`) dla DLP, która ma zostać podjęta, gdy użytkownik **spróbuje skopiować do schowka**, **skopiować na dysk wymienny USB**, **skopiować na dysk sieciowy** i **wydrukować**.          |

> [!IMPORTANT]
> Ustawienia w grupie aplikacji z ograniczeniami przesłaniają wszelkie ograniczenia ustawione na liście aplikacji z ograniczeniami, gdy znajdują się w tej samej regule. Jeśli więc aplikacja znajduje się na liście aplikacji z ograniczeniami i jest członkiem grupy aplikacji z ograniczeniami, zostaną zastosowane ustawienia grupy aplikacji z ograniczeniami.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>Jak DLP stosuje ograniczenia do działań

Interakcje między **działaniami plików dla aplikacji w ograniczonych grupach aplikacji**, **działaniami plików dla wszystkich aplikacji** i listą **działań aplikacji z ograniczeniami** są ograniczone do tej samej reguły.

##### <a name="restricted-app-groups-overrides"></a>Przesłonięcia grup aplikacji z ograniczeniami

Konfiguracje zdefiniowane w **działaniach plików dla aplikacji w ograniczonych grupach aplikacji** zastępują konfiguracje na liście **Działań aplikacji z ograniczeniami** i **Działania plików dla wszystkich aplikacji** w tej samej regule.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Działania aplikacji z ograniczeniami i działania dotyczące plików dla wszystkich aplikacji

Konfiguracje **działań aplikacji z ograniczeniami** i **działania plików dla wszystkich aplikacji** działają w porozumieniu, jeśli akcja zdefiniowana dla **działań aplikacji z ograniczeniami** to `Audit only`, lub `Block with override` w tej samej regule. Dzieje się tak, ponieważ akcje zdefiniowane dla **działań aplikacji z ograniczeniami** mają zastosowanie tylko wtedy, gdy użytkownik uzyskuje dostęp do pliku przy użyciu aplikacji, która znajduje się na liście. Gdy użytkownik ma dostęp, mają zastosowanie akcje zdefiniowane dla działań w **obszarze Działania plików dla wszystkich aplikacji** . 

Oto przykład:

Jeśli Notepad.exe jest **dodawana do aplikacji z ograniczeniami** , a **działania plików dla wszystkich aplikacji** są skonfigurowane pod kątem **stosowania ograniczeń do określonych działań** i oba są konfigurowane w następujący sposób:

|Ustawienie w zasadach  |Nazwa aplikacji  |Aktywność użytkownika  |Akcja DLP do wykonania  |
|---------|---------|---------|---------|
|Działania aplikacji z ograniczeniami     |Notatnik        |Uzyskiwanie dostępu do chronionego elementu DLP         |Tylko inspekcja         |
|Działania dotyczące plików dla wszystkich aplikacji   |Wszystkie aplikacje        | Kopiuj do schowka        |Tylko inspekcja         |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Kopiowanie na urządzenie wymienne USB | Blokuj       |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Kopiowanie do udziału sieciowego         |Tylko inspekcja         |
|Działania dotyczące plików dla wszystkich aplikacji   |Wszystkie aplikacje         |Drukowania         |Blokuj         |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Kopiowanie lub przenoszenie przy użyciu niedozwolonej aplikacji Bluetooth         |Zablokowany         |
|Działania dotyczące plików dla wszystkich aplikacji     |Wszystkie aplikacje         |Usługi pulpitu zdalnego         |Blokuj z przesłonięciami         |

Użytkownik A otwiera chroniony plik DLP przy użyciu Notatnika. DLP zezwala na dostęp i przeprowadza inspekcję działania. Jeszcze w Notatniku użytkownik A próbuje skopiować do schowka z chronionego elementu, to działa i DLP przeprowadza inspekcję działania. Następnie użytkownik A próbuje wydrukować chroniony element z Notatnika, a działanie jest zablokowane.

> [!NOTE]
> Gdy akcja DLP do wykonania w **działaniach aplikacji z ograniczeniami** jest ustawiona na `block`wartość , cały dostęp jest blokowany, a użytkownik nie może wykonywać żadnych działań w pliku.
   
##### <a name="file-activities-for-all-apps-only"></a>Działania dotyczące plików tylko dla wszystkich aplikacji

Jeśli aplikacja nie znajduje się w **działaniach plików dla aplikacji w ograniczonych grupach aplikacji** lub nie znajduje się na liście **Działań aplikacji z ograniczeniami** lub znajduje się na liście **Działań aplikacji z ograniczeniami** z akcją `Audit only`, lub "Blokuj z przesłonięciami", wszelkie ograniczenia zdefiniowane w **działaniach plików dla wszystkich aplikacji** są stosowane w tej samej regule.  

#### <a name="macos-devices"></a>Urządzenia z systemem macOS

Podobnie jak na urządzeniach z systemem Windows, teraz możesz uniemożliwić aplikacjom systemu macOS dostęp do poufnych danych, definiując je na liście **działań aplikacji z ograniczeniami** . 

> [!NOTE]
> Należy pamiętać, że aplikacje międzyplatformowe muszą być wprowadzane z unikatowymi ścieżkami odpowiednimi dla systemu operacyjnego, na których są uruchomione.

Aby znaleźć pełną ścieżkę aplikacji dla komputerów Mac:

1. Na urządzeniu z systemem macOS otwórz **monitor aktywności**. Znajdź i kliknij dwukrotnie proces, który chcesz ograniczyć

2. Wybierz kartę **Otwórz pliki i porty** .
  
3. W przypadku aplikacji systemu macOS potrzebna jest pełna nazwa ścieżki, w tym nazwa aplikacji.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Ochrona poufnych danych przed aplikacjami synchronizacji w chmurze

Aby zapobiec synchronizacji poufnych elementów z chmurą przez aplikacje synchronizacji w chmurze, takie jak *onedrive.exe*, dodaj aplikację synchronizacji w chmurze do listy **Nieuprawialne aplikacje** . Gdy niedozwolona aplikacja synchronizacji w chmurze próbuje uzyskać dostęp do elementu chronionego przez blokujące zasady DLP, protokół DLP może generować powtarzające się powiadomienia. Możesz uniknąć tych powtarzających się powiadomień, włączając opcję **Automatyczna kwarantanna** w obszarze **Nie zezwalaj na aplikacje**.  

##### <a name="auto-quarantine-preview"></a>Automatyczna kwarantanna (wersja zapoznawcza)

> [!NOTE]
> Automatyczna kwarantanna jest obsługiwana tylko w Windows 10

Po włączeniu automatycznej kwarantanny rozpoczyna się, gdy niedozwolona aplikacja próbuje uzyskać dostęp do chronionego elementu poufnego DLP. Automatyczna kwarantanna przenosi poufny element do folderu skonfigurowanego przez administratora i może pozostawić symbol zastępczy **.txt** pliku zamiast oryginalnego. Tekst w pliku zastępczym można skonfigurować tak, aby informował użytkowników, dokąd został przeniesiony element, oraz inne istotne informacje.  

Możesz użyć automatycznej kwarantanny, aby zapobiec nieskończonemu łańcuchowi powiadomień DLP dla użytkowników i administratorów — zobacz [Scenariusz 4: Unikanie zapętlania powiadomień DLP z aplikacji synchronizacji w chmurze z automatyczną kwarantanną (wersja zapoznawcza).](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview)

### <a name="unallowed-bluetooth-apps"></a>Niedozwolone aplikacje Bluetooth

Uniemożliwiaj użytkownikom przesyłanie plików chronionych przez zasady za pośrednictwem określonych aplikacji Bluetooth.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Ograniczenia przeglądarki i domeny dotyczące danych poufnych

Ograniczanie udostępniania poufnych plików zgodnych z zasadami nieograniczonym domenom usług w chmurze.

#### <a name="unallowed-browsers"></a>Niedozwolone przeglądarki

W przypadku urządzeń z systemem Windows można dodać przeglądarki identyfikowane przez ich nazwy wykonywalne, które będą blokowane w przypadku plików zgodnych z warunkami wymuszonych zasad DLP, w których ograniczenie przekazywania do usług w chmurze jest ustawione na blokowanie lub blokowanie zastępowania. Gdy te przeglądarki nie będą mogły uzyskać dostępu do pliku, użytkownicy końcowi zobaczą wyskakujące powiadomienie z prośbą o otwarcie pliku za pośrednictwem przeglądarki Microsoft Edge.

W przypadku urządzeń z systemem macOS należy dodać pełną ścieżkę pliku. Aby znaleźć pełną ścieżkę aplikacji dla komputerów Mac:

1. Na urządzeniu z systemem macOS otwórz **monitor aktywności**. Znajdź i kliknij dwukrotnie proces, który chcesz ograniczyć

2. Wybierz kartę **Otwórz pliki i porty** .
  
3. W przypadku aplikacji systemu macOS potrzebna jest pełna nazwa ścieżki, w tym nazwa aplikacji.

#### <a name="service-domains"></a>Domeny usług

> [!NOTE]
> Ustawienie **Domeny usługi** dotyczy tylko plików przekazanych przy użyciu przeglądarki Microsoft Edge lub Google Chrome z [zainstalowanym rozszerzeniem Microsoft Purview](dlp-chrome-learn-about.md#learn-about-the-microsoft-purview-extension) .

Możesz kontrolować, czy pliki poufne chronione przez zasady mogą być przekazywane do określonych domen usług z przeglądarki Microsoft Edge.

Jeśli tryb listy jest ustawiony na **wartość Blokuj**, użytkownik nie będzie mógł przekazać poufnych elementów do tych domen. Gdy akcja przekazywania zostanie zablokowana, ponieważ element jest zgodny z zasadami DLP, DLP wygeneruje ostrzeżenie lub zablokuje przekazanie poufnego elementu.

Jeśli tryb listy jest ustawiony na **wartość Zezwalaj**, użytkownicy będą mogli przekazywać elementy poufne **_tylko_** do tych domen, a przekazywanie dostępu do wszystkich innych domen nie jest dozwolone.

> [!IMPORTANT]
> Jeśli tryb ograniczeń usługi jest ustawiony na wartość "Zezwalaj", musisz mieć skonfigurowaną co najmniej jedną domenę usługi, zanim ograniczenia zostaną wymuszone.

Użyj formatu FQDN domeny usługi bez zakończenia `.` 

Przykład:

 `www.contoso.com` 

Symbole wieloznaczne nie są obsługiwane.

### <a name="additional-settings-for-endpoint-dlp"></a>Dodatkowe ustawienia protokołu DLP punktu końcowego

#### <a name="business-justification-in-policy-tips"></a>Uzasadnienie biznesowe w poradach dotyczących zasad

Możesz kontrolować sposób interakcji użytkowników z opcją uzasadnienia biznesowego w powiadomieniach o poradach dotyczących zasad DLP. Ta opcja jest wyświetlana, gdy użytkownicy wykonują działanie chronione przez ustawienie **Blokuj z zastąpieniem** w zasadach DLP. Jest to ustawienie globalne. Możesz wybrać jedną z następujących opcji:

- **Pokaż opcje domyślne i niestandardowe pole tekstowe**: domyślnie użytkownicy mogą wybrać wbudowane uzasadnienie lub wprowadzić własny tekst.
- **Pokaż tylko opcje domyślne**: użytkownicy mogą wybrać tylko wbudowane uzasadnienie.
- **Pokaż tylko niestandardowe pole tekstowe**: użytkownicy mogą wprowadzać tylko własne uzasadnienie. W powiadomieniu o poradach dotyczących zasad użytkownika końcowego zostanie wyświetlone tylko pole tekstowe. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Dostosowywanie opcji w menu rozwijanym

Możesz utworzyć maksymalnie pięć dostosowanych opcji, które będą wyświetlane podczas interakcji użytkowników z poradą powiadomienia o zasadach, wybierając **menu rozwijane Dostosuj opcje**. 


|Opcja |Tekst domyślny  |
|---------|---------|
|opcja 1    | **Jest to część ustalonego biznesowego przepływu pracy**  lub można wprowadzić dostosowany tekst        |
|opcja 2  |**Mój menedżer zatwierdził tę akcję** lub możesz wprowadzić dostosowany tekst         |
|opcja 3   |**Wymagany jest pilny dostęp; Powiadomię mojego menedżera oddzielnie** lub możesz wprowadzić dostosowany tekst          |
|Pokaż opcję fałszywie dodatnią     |**Informacje w tych plikach nie są poufne** lub można wprowadzić dostosowany tekst          |
|opcja 5    |**Inny** lub możesz wprowadzić dostosowany tekst         |

### <a name="always-audit-file-activity-for-devices"></a>Zawsze przeprowadzaj inspekcję działania plików dla urządzeń

Domyślnie, gdy urządzenia są dołączone, działanie dla plików pakietu Office, PDF i CSV jest automatycznie poddawanych inspekcji i dostępne do przeglądu w Eksploratorze działań. Wyłącz tę funkcję, jeśli chcesz, aby to działanie było poddawane inspekcji tylko wtedy, gdy dołączone urządzenia są uwzględnione w aktywnych zasadach.

Działanie plików będzie zawsze poddawane inspekcji dla dołączonych urządzeń, niezależnie od tego, czy są one uwzględnione w aktywnych zasadach.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Dołączanie urządzeń Windows 10 i Windows 11 do usługi Microsoft Purview — omówienie](/microsoft-365/compliance/device-onboarding-overview)
- [Subskrypcja platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Przyłączone do usługi Azure Active Directory (AAD)](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nową przeglądarkę Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
