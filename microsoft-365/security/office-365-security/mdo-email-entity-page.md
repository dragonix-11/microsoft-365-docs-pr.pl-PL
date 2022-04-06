---
title: Strona Ochrona usługi Office 365 w usłudze Microsoft Defender e-mail
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 01/21/2021
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Ochrona usługi Office 365 w usłudze Microsoft Defender E5, P1 i P2 mogą teraz wyświetlać 360 stopni każda wiadomość e-mail ze stroną jednostki poczty e-mail.
ms.openlocfilehash: d75ebd9b54fc5e7919154a4f65e0d5fc0e77e117
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475460"
---
# <a name="the-email-entity-page"></a>Strona jednostki e-mail

**W tym artykule:**
- [Docieranie do strony jednostki poczty e-mail](#reach-the-email-entity-page)
- [Czytanie strony jednostki wiadomości e-mail](#read-the-email-entity-page)
- [Korzystanie z kart stron encji e-mail](#use-email-entity-page-tabs)
- [Nowa strona encji poczty e-mail](#new-to-the-email-entity-page)

Administratorzy usług Ochrona usługi Office 365 w usłudze Microsoft Defender E5 i Defender dla Office P1 i P2 mają widok poczty e-mail o 360 stopniach za pomocą strony jednostki **poczty e-mail**. Ta strona przechodnia do poczty e-mail została utworzona w celu ulepszania informacji dostarczanych w [wysuwanych szczegółach wiadomości e-mail](threat-explorer-views.md) w Eksploratorze zagrożeń.

## <a name="reach-the-email-entity-page"></a>Docieranie do strony jednostki poczty e-mail

Strona jednostki poczty e-mail jest dostępna w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com> **e-mail & Eksploratora** \> **współpracy**. Aby przejść bezpośrednio do strony **Eksploratora** , użyj przeglądarki <https://security.microsoft.com/threatexplorer>.

W **Eksploratorze** wybierz temat wiadomości e-mail, której badasz. U góry wysuwanych wiadomości e-mail zostanie wyświetlany złoty pasek. To zaproszenie do nowej strony zawiera informacje "Wypróbuj stronę nowej jednostki poczty e-mail z wzbogaceniem danych...". Wybierz pozycję , aby wyświetlić nową stronę.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Złoty transparent z wyrazami *Wypróbuj stronę nowej jednostki poczty e-mail z wzbogaceniem danych*, aby przejść do nowego programu" lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Grafika przedstawiająca stronę jednostki poczty e-mail skupiną na nagłówkach, które będą" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> Uprawnienia wymagane do wyświetlania i używania tej strony są takie same jak uprawnienia do wyświetlania **Eksploratora**. Administrator musi być członkiem grupy Administrator globalny lub czytelnik globalny albo Administrator zabezpieczeń lub Czytelnik zabezpieczeń. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

## <a name="read-the-email-entity-page"></a>Czytanie strony jednostki wiadomości e-mail

Struktura ma być łatwa do odczytania i nawigowania jednym rzutem oka. Różne karty w górnej części strony umożliwiają bardziej szczegółowe badanie. Układ działa w ten sposób:

1. Większość wymaganych pól jest po lewej stronie wysuwania. Te szczegóły są "przyklejone", co oznacza, że są zakotwiczone po lewej stronie niezależnie od karty, do których przechodzisz w pozostałej części wysuwu.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Grafika przedstawiająca stronę jednostki poczty e-mail z wyróżniona lewą stroną" lightbox="../../media/email-entities-3-left-panel.png":::

2. W prawym górnym rogu znajdują się akcje, które można podjąć w wiadomości e-mail. Wszystkie akcje, które można podjąć za pomocą **Eksploratora** , będą również dostępne za pośrednictwem strony jednostki poczty e-mail.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Grafika przedstawiająca stronę jednostki poczty e-mail z wyróżniona prawą stroną" lightbox="../../media/email-entities-5-preview.png":::

3. Bardziej dogłębną analizę można wykonać, sortując pozostałą część strony. Sprawdź szczegóły wykrywania wiadomości e-mail, stan uwierzytelniania wiadomości e-mail i nagłówek. W tym obszarze należy w zależności od sytuacji, ale informacje w tych kartach są dostępne dla każdej wiadomości e-mail.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Główny panel strony z nagłówkiem wiadomości e-mail i stanem uwierzytelniania" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="use-email-entity-page-tabs"></a>Korzystanie z kart stron encji e-mail

Karty w górnej części strony jednostki umożliwiają wydajne badanie wiadomości e-mail.

1. **Oś** czasu: Widok osi czasu wiadomości e-mail (na oś czasu w **Eksploratorze** ) zawiera oryginalne dostarczanie do zdarzeń po dostarczeniu, które mają miejsce w wiadomości e-mail. W przypadku wiadomości e-mail, które nie mają akcji po dostarczeniu, widok zawiera oryginalny wiersz dostarczenia w widoku osi czasu. Zdarzenia, takie jak: Automatyczne przeczyszczanie zerowej godziny (ZAP), Remediate, Kliknięcia adresów URL, et cetera, ze źródeł takich jak system, administrator i użytkownik, są wyświetlane tutaj w kolejności, w jakiej wystąpiły.
2. **Analiza**: Analiza przedstawia pola, które ułatwiają administratorom szczegółową analizę wiadomości e-mail. W przypadkach, gdy administratorzy muszą dowiedzieć się więcej na temat wykrywania, nadawcy/adresata oraz szczegółów uwierzytelniania wiadomości e-mail, powinni skorzystać z karty Analiza. Linki do załączników i adresów URL znajdują się również na tej stronie, w obszarze "Jednostki pokrewne". Tutaj poidentyfikowane są zarówno załączniki, jak i zidentyfikowane zagrożenia, a kliknięcie spowoduje proste kliknięcie spowoduje przekierowanie do stron Załączniki i Adres URL. Ta karta zawiera również opcję Wyświetl nagłówek, aby *wyświetlić nagłówek wiadomości e-mail*. Administratorzy mogą porównywać wszystkie szczegóły z nagłówków wiadomości e-mail obok siebie z informacjami w panelu głównym w celu zwiększenia przejrzystości.
3. **Załączniki**: Sprawdza załączniki znalezione w wiadomości e-mail wraz z innymi znalezionymi szczegółami załączników. Obecnie wyświetlana liczba załączników jest ograniczona do 10. Zwróć uwagę, że szczegóły detonacji załączników, które zostały znalezione jako złośliwe, również są tutaj widoczne.
4. **Adresy URL**: ta karta zawiera listę adresów URL znalezionych w wiadomości e-mail z innymi szczegółami na temat adresów URL. W tej chwili liczba adresów URL jest ograniczona do 10, ale najpierw trzeba wyświetlić te 10 adresów *URL*. Priorytetyzacja pozwala zaoszczędzić czas i przypuszczenia. W tym miejscu będą również pokazane adresy URL, które zostały znalezione jako złośliwe i detonowane.
5. **Podobne wiadomości e-mail**: Ta karta zawiera listę wszystkich wiadomości e-mail podobnych do kombinacji *identyfikator wiadomości sieciowej +* adresata specyficzna dla tej wiadomości e-mail. Podobieństwo zależy tylko *od treści* wiadomości. Określenie dokonane w wiadomościach e-mail w celu kategoryzowania ich jako "podobnych" nie obejmuje uwzględnienia *załączników*.

## <a name="new-to-the-email-entity-page"></a>Nowa strona encji poczty e-mail

Z tą stroną jednostki poczty e-mail są dostępne nowe funkcje. Oto lista.

### <a name="email-preview-for-cloud-mailboxes"></a>Podgląd wiadomości e-mail dla chmurowych skrzynek pocztowych

Administratorzy mogą wyświetlać podgląd wiadomości e-mail w skrzynkach pocztowych w ***chmurze, jeśli*** te wiadomości są nadal obecne w chmurze. W przypadku "miękkiego usunięcia" (przez administratora lub użytkownika) lub zap (do kwarantanny) wiadomości e-mail nie są już obecne w lokalizacji w chmurze. W takim przypadku administratorzy nie będą mogli wyświetlać podglądu tych konkretnych wiadomości e-mail. Wiadomości e-mail, które zostały porzucone lub których dostarczenie nie powiodło się, nigdy nie zostały wprowadzone do skrzynki pocztowej. Z tego powodu administratorzy również nie będą mogli wyświetlać podglądu tych wiadomości e-mail.

> [!WARNING]
> Wyświetlanie podglądu wiadomości e-mail wymaga specjalnej roli o nazwie **Podgląd**. Tę rolę możesz dodać w portalu Microsoft 365 Defender zgodnie z opisem w & e-mail w [portalu Microsoft 365 Defender współpraca](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal). W tym miejscu może być konieczne utworzenie  nowej grupy ról współpracy usługi poczty e-mail & i dodanie roli w wersji **Preview** do tej nowej grupy ról lub  dodanie roli w wersji Preview do grupy ról, która umożliwia administratorom w Twojej organizacji pracę w **Eksploratorze**.

### <a name="detonation-details"></a>Szczegóły detonacji

Te szczegóły są specyficzne dla załączników wiadomości e-mail i adresów URL. Użytkownicy mogą zobaczyć te szczegóły, przechodząc do Eksploratora i stosując  filtr technologii wykrywania ustawiony na detonację pliku lub detonację adresu URL. Wiadomości e-mail filtrowane w celu detonowania plików będą zawierać złośliwy plik ze szczegółami detonacji, a wiadomości odfiltrowane pod adresami URL zawierają złośliwy adres URL i szczegóły dotyczące jego detonacji.

Użytkownicy zobaczą wzbogacenie szczegółów detonacji dotyczących znanych złośliwych załączników lub adresów URL znalezionych w ich wiadomościach e-mail, które zostały zdetonowane dla określonej dzierżawy. Składa się ona z łańcucha detonacji, podsumowania detonacji, zrzutów ekranu i informacji obserwowanych zachowania, aby ułatwić klientom zrozumienie, dlaczego załącznik lub adres URL został uznany za złośliwy i detonowany.

1. *Łańcuch detonacji*. Jedno detonowanie pliku lub adresu URL może wyzwolić wiele dat. Łańcuch detonacji śledzi ścieżkę detonations, w tym oryginalny złośliwy plik lub adres URL, który spowodował werdykt, oraz wszystkie inne pliki lub adresy URL, na które wpływa detonacja. Te adresy URL lub dołączone pliki mogą nie być bezpośrednio obecne w wiadomości e-mail, ale uwzględniając analizę, ważne jest ustalenie, dlaczego plik lub adres URL został znaleziony jako złośliwy.  

    > [!NOTE]
    > Ten element może być pokazywany tylko element najwyższego poziomu, jeśli żaden z połączonych z nim jednostek nie został znaleziony jako problematyczny lub został zdetonowany.

1. Podsumowanie *detonacji* zawiera podstawowe podsumowanie dotyczące detonacji *, takie* jak czas analizy, czas detonacji, system operacyjny i aplikacja, system operacyjny i aplikacja, w których wystąpiło detonacja, rozmiar pliku i powód detonacji.
1. *Zrzuty ekranu* pokazują zrzuty ekranu zrobione podczas detonacji. Podczas detonacji może być wiele zrzutów ekranu. Zrzuty ekranu nie są przechwytywane dla
    - Pliki typu kontenera, takie .zip lub .rar.
    - Jeśli adres URL zostanie otwarty w linku, który bezpośrednio pobiera plik. Pobrany plik będzie jednak wyświetlony w łańcuchu detonacji.
1. Behavior *Details* (Szczegóły zachowania) to eksport, który przedstawia szczegóły dotyczące zachowania, takie jak dokładne zdarzenia, które miały miejsce podczas detonacji, oraz obserwowalne elementy, które zawierają adresy URL, adresy IP, domeny i pliki odnalezione podczas detonacji (i które mogą być problematyczne lub ciesze). Należy pamiętać, że szczegóły zachowania mogą nie obejmować:
    - Pliki kontenerów.zip na .rar, które są w posiadaniu innych plików.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="Podsumowanie detonacji pokazujące łańcuch, podsumowanie, szczegóły detonacji i zrzut ekranu pod nagłówkiem *Analiza głębokości*" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-innovations"></a>Inne innowacje

*Tagi*: Są to tagi stosowane do użytkowników. Jeśli użytkownik jest adresatem, administratorzy zobaczą tag *adresata* . Podobnie, jeśli użytkownik jest nadawcą, jest to *tag nadawcy* . Pojawi się on po lewej stronie strony jednostek poczty e-mail (w części, która jest opisana  jako przyklejona, i dlatego zakotwiczona na stronie).

*Najnowsza lokalizacja dostarczania*: Najnowsza lokalizacja dostarczania to lokalizacja, w której wiadomość e-mail trafiała po działaniach systemowych, takich jak ZAP, lub akcje administracyjne, takie jak Przenieś do elementów usuniętych, zakończ. Najnowsza lokalizacja dostarczania nie jest przeznaczona do informowania administratorów o bieżącej *lokalizacji* wiadomości. Jeśli na przykład użytkownik usunie wiadomość lub przeniesie ją do archiwum, lokalizacja dostarczania nie zostanie zaktualizowana. Jeśli jednak została wykonane działanie systemowe i zaktualizowano lokalizację (na przykład zap, co spowoduje przeniesienie wiadomości e-mail do kwarantanny), spowoduje to zaktualizowanie do kwarantanny najnowszej lokalizacji dostarczania.

*Szczegóły wiadomości e-mail*: Wymagane szczegółowe informacje w celu lepszego zrozumienia wiadomości e-mail dostępnych na *karcie* Analiza.

- *Exchange transportu (* nazywane także regułami przepływu poczty e-mail lub regułami ET): Te reguły są stosowane do wiadomości w warstwie transportu i mają pierwszeństwo przed wyłudami i spamem. Reguły przepływu poczty e-mail są tworzone i modyfikowane w centrum administracyjnym usługi Exchange <https://admin.exchange.microsoft.com/#/transportrules>na stronie , ale jeśli reguła przepływu poczty e-mail dotyczy wiadomości, nazwa reguły i identyfikator GUID będą wyświetlane w tym miejscu. Cenne informacje do celów śledzenia.

- *Zastępowanie systemu*: Oznacza to, że należy wypisać wyjątki od lokalizacji dostarczania wiadomości, zastępując lokalizację dostarczania podaną przez system (zgodnie z daniem technologii wykrywania i zagrożenia).

- *Poziom skarg zbiorczych*: zbiorczy poziom skarg (BCL, Bulk Complaint Level) wiadomości. Wyższa wartość BCL wskazuje, że wiadomość e-mail zbiorcza z większą prawdopodobieństwem generuje skargi (jest to naturalne, jeśli wiadomość e-mail prawdopodobnie jest spamem).

- *Poziom ufności filtru* spamu: poziom ufności filtru spamu wiadomości. Wyższa wartość oznacza, że wiadomość jest bardziej prawdopodobna jako spam.

- *Nazwa domeny*: jest nazwą domeny nadawcy.

- *Właściciel domeny*: określa właściciela domeny wysyłającej.

- *Lokalizacja domeny*: określa lokalizację domeny wysyłającej.

- *Data utworzenia domeny*: określa datę utworzenia domeny wysyłającej. Nowo utworzona domena jest działaniem, które możesz zachować, jeśli inne sygnały wskazują na podejrzane zachowanie.

*Uwierzytelnianie wiadomości* e-mail: Metody uwierzytelniania poczty e-mail używane przez Microsoft 365 SPF, DKIM i DMARC.

- Spf (Sender Policy **Framework): w** tym artykule opisano wyniki sprawdzania rekordu SPF wiadomości. Możliwe wartości mogą być:
  - Pass (IP address): Sprawdzanie SPF wiadomości przekazanych i zawiera adres IP nadawcy. Klient jest uprawniony do wysyłania lub przekazywania wiadomości e-mail w imieniu domeny nadawcy.
  - Niepowodzenie (adres IP): Sprawdzenie SPF wiadomości nie powiodło się i zawiera adres IP nadawcy. Jest to czasami nazywane trudnym niepowodzeniem.
  - Softfail (przyczyna): rekord SPF wyznaczył hosta jako nieudostępniany do wysyłania, ale jest w okresie przejścia.
  - Neutralny: rekord SPF wyraźnie stwierdza, że nie chowa, czy adres IP nie jest autoryzowany do wysyłania.
  - Brak: Domena nie ma rekordu SPF lub rekord SPF nie jest szacowany jako wynik.
  - Błąd: Wystąpił tymczasowy błąd. Na przykład błąd DNS. To samo sprawdzanie może się powieść w późniejszym czasie.
  - Błąd: Wystąpił błąd trwały. Na przykład domena ma rekord SPF o źle sformatowanym formacie.

- **DKIM** (DomainKeys Identified Mail):
  - Pass (Pomyślnie): wskazuje, czy wiadomość została pomyślnie przekazana przez DKIM.
  - Niepowodzenie (przyczyna): wskazuje, czy wiadomość nie powiodła się i dlaczego jest sprawdzana przez DKIM. Na przykład jeśli wiadomość nie została podpisana lub podpis nie został zweryfikowany.
  - Brak. Oznacza, że wiadomość nie została podpisana. Może to oznaczać, że domena ma rekord DKIM lub że rekord DKIM nie jest szacowany jako wynik, tylko że ta wiadomość nie została podpisana.

- **DMARC** (Domain-based Message Authentication, Reporting, and Conformance):
  - Pass (Pomyślnie): wskazuje, czy wiadomość została przekazana przez DMARC.
  - Niepowodzenie: oznacza, że sprawdzenie DMARC wiadomości nie powiodło się.
  - Bestguespass: Wskazuje, że dla domeny nie istnieje żaden rekord TXT DMARC, ale jeśli istniał, oznacza to, że pomyślnie by go sprawdzał DMARC.
  - Brak. Oznacza, że dla domeny wysyłającej w systemie DNS nie istnieje żaden rekord TXT DMARC.

*Uwierzytelnianie złożone*: Jest to wartość używana przez program Microsoft 365 do łączenia uwierzytelniania poczty e-mail, takiego jak SPF, DKIM i DMARC, w celu określenia, czy wiadomość jest autentyczna. Jako podstawy *oceny jest* używana domena Od: poczty.

### <a name="email-summary-panel"></a>Panel podsumowania wiadomości e-mail

Panel podsumowania wiadomości e-mail zawiera podsumowanie strony pełnej jednostki wiadomości e-mail. Zawiera ustowalizowane szczegóły dotyczące wiadomości e-mail (np. wykrywanie), a także informacje kontekstowe (np. w przypadku metadanych Kwarantanny lub Przesyłania). Panel podsumowania wiadomości e-mail zastępuje tradycyjne wysuwki wykrywania w czasie rzeczywistym, Eksploratora zagrożeń, przesyłania i raportowania.

> [!div class="mx-imgBorder"]
> ![Otwórz link do encji wiadomości e-mail.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Aby wyświetlić wszystkie składniki, kliknij link Otwórz jednostkę wiadomości **e-mail w** celu otwarcia pełnej strony jednostki wiadomości e-mail.  

Panel podsumowania wiadomości e-mail jest podzielony na następujące sekcje:  

- *Szczegóły dostarczenia*: Zawiera informacje o zagrożeniach i odpowiednim poziomie ufności, technologiach wykrywania oraz oryginalnej i najnowszej lokalizacji dostarczania.

- *Szczegóły wiadomości e-mail*: Zawiera informacje o właściwościach poczty e-mail, takich jak nazwa nadawcy, adres nadawcy, godzina otrzymania, szczegóły uwierzytelniania i inne kilka innych szczegółów.

- *Adresy URL*: Domyślnie zobaczysz 3 adresy URL i odpowiadające im zagrożenia. Zawsze możesz kliknąć pozycję **Wyświetl wszystkie adresy URL** , aby je rozwinąć, wyświetlić wszystkie adresy URL i je wyeksportować.  

- *Załączniki*: Domyślnie widać 3 załączniki. Zawsze możesz kliknąć pozycję **Wyświetl wszystkie załączniki,** aby rozwinąć i wyświetlić wszystkie załączniki. 

Oprócz powyższych sekcji będą również dostępne sekcje specyficzne dla niewielu funkcji, które są zintegrowane z panelem podsumowania: 

- Materiały: 

    - *Szczegóły przesłania*: zawiera informacje o konkretnych przesłaniach, takie jak:
        - Data przesłana
        - Temat
        - Typ przesłania
        - Powód przesłania
        - Identyfikator przesyłania
        - Przesłane przez

    - *Szczegóły wyniku*: Przesłane wiadomości są przeglądane. Możesz zobaczyć wynik przesłania oraz wszystkie zalecane następne kroki.

- Kwarantanna:  

    - *Szczegóły kwarantanny*: zawiera szczegóły specyficzne dla kwarantanny. Aby uzyskać więcej informacji, zobacz [Zarządzanie wiadomościami poddanymi kwarantannie](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Wygasa: Data/godzina, kiedy wiadomość zostanie automatycznie i trwale usunięta z kwarantanny.
        - Opublikowano dla: Wszystkie adresy e-mail (jeśli są), na które została wydana wiadomość.
        - Jeszcze nie opublikowano dla: Wszystkie adresy e-mail (jeśli są), na które wiadomość nie została jeszcze wydana.

    - *Akcje kwarantanny*: Aby uzyskać więcej informacji o różnych akcjach kwarantanny, zobacz [Zarządzanie wiadomościami poddanymi kwarantannie](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).