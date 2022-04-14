---
title: przepływ pracy Teams w Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Dowiedz się, jak zachowywać, zbierać, przeglądać i eksportować zawartość z Microsoft Teams w Advanced eDiscovery.
ms.openlocfilehash: 90c3ece3f6e8218771da9dbbb88fe5c32d9d7d94
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847020"
---
# <a name="advanced-ediscovery-workflow-for-content-in-microsoft-teams"></a>przepływ pracy Advanced eDiscovery zawartości w Microsoft Teams

Ten artykuł zawiera kompleksowy zestaw procedur, wytycznych i najlepszych rozwiązań dotyczących używania Advanced eDiscovery do przechowywania, zbierania, przeglądania i eksportowania zawartości z Microsoft Teams. Celem tego artykułu jest pomoc w optymalizacji przepływu pracy zbierania elektronicznych materiałów dowodowych pod kątem zawartości Teams.

Istnieje pięć kategorii zawartości Teams, które można zbierać i przetwarzać przy użyciu Advanced eDiscovery:

- **Teams czaty 1:1**. Wiadomości czatu, wpisy i załączniki udostępnione w Teams konwersacji między dwiema osobami.  Teams 1:1 czaty są również *nazywane konwersacjami*.

- **Teams czaty grupowe**. Wiadomości czatu, wpisy i załączniki udostępnione w Teams konwersacji między co najmniej trzema osobami. Nazywane również czatami *1:N* lub *konwersacjami grupowymi*.

- **Teams kanałów**. Wiadomości czatu, wpisy, odpowiedzi i załączniki udostępnione w standardowym kanale Teams.

- **Kanały prywatne**. Wpisy wiadomości, odpowiedzi i załączniki udostępnione w prywatnym kanale Teams.

- **Kanały udostępnione**. Wpisy wiadomości, odpowiedzi i załączniki udostępnione w udostępnionym kanale Teams.

## <a name="where-teams-content-is-stored"></a>Gdzie jest przechowywana zawartość Teams

Warunkiem wstępnym zarządzania zawartością Teams w Advanced eDiscovery jest zrozumienie typu zawartości Teams, którą można zbierać, przetwarzać i przeglądać w Advanced eDiscovery oraz gdzie ta zawartość jest przechowywana w Microsoft 365. W poniższej tabeli wymieniono Teams typ zawartości i miejsce przechowywania poszczególnych elementów.

|&nbsp;|Lokalizacja wiadomości i wpisów czatu|Lokalizacja plików i załączników|
|---|---|---|
|czaty Teams 1:1|Wiadomości w czatach 1:1 są przechowywane w Exchange Online skrzynki pocztowej wszystkich uczestników czatu.|Pliki udostępnione podczas czatu 1:1 są przechowywane na koncie OneDrive dla Firm osoby, która udostępniła plik.|
|Teams czaty grupowe|Wiadomości w czatach grupowych są przechowywane w Exchange Online skrzynce pocztowej wszystkich uczestników czatu.|Pliki udostępnione w czatach grupowych są przechowywane na koncie OneDrive dla Firm osoby, która udostępniła plik.|
|kanały Teams|Wszystkie wiadomości i wpisy kanału są przechowywane w Exchange Online skrzynki pocztowej skojarzonej z zespołem.|Pliki udostępnione w kanale są przechowywane w witrynie SharePoint Online skojarzonej z zespołem.|
|Kanały prywatne|Wiadomości wysyłane w kanale prywatnym są przechowywane w Exchange Online skrzynkach pocztowych wszystkich członków kanału prywatnego.|Pliki udostępnione w kanale prywatnym są przechowywane w dedykowanej witrynie SharePoint Online skojarzonej z kanałem prywatnym.|
|Kanały udostępnione|Wiadomości wysyłane w kanale udostępnionym są przechowywane w systemowej skrzynce pocztowej skojarzonej z kanałem udostępnionym. <sup>1</sup>|Pliki udostępnione w kanale udostępnionym są przechowywane w dedykowanej witrynie SharePoint Online skojarzonej z kanałem udostępnionym.|

> [!NOTE]
> <sup>1</sup> Aby wyszukać (i zachować) wiadomości wysyłane w kanale udostępnionym, musisz wyszukać lub określić skrzynkę pocztową Exchange Online dla nadrzędnego zespołu.

## <a name="create-a-case-for-teams-content"></a>Tworzenie przypadku zawartości Teams

Pierwszym krokiem do zarządzania zawartością Teams w Advanced eDiscovery jest utworzenie sprawy przy użyciu nowego formatu przypadku zoptymalizowanego pod kątem zarządzania zawartością Teams. Oto zalety używania nowego formatu wielkości liter dla Teams zawartości:

- Obsługa wątków konwersacji, w których dodatkowe komunikaty w tej samej konwersacji, które zawierają elementy dynamiczne, są automatycznie zbierane i dodawane do zestawów przeglądów.

- Teams konwersacje czatu są automatycznie dodawane w celu przeglądania zestawów jako pliku transkrypcji HTML. Załączniki w chmurze, które są udostępniane w konwersacjach, są również dodawane do zestawu przeglądów. Pomaga to zapewnić kontekst konwersacji z elementami responsywnym i zmniejszyć całkowitą liczbę elementów generowanych przez zawartość opartą na czatach.

- Kolekcje o rozmiarze do 1 TB można dodać do zestawów przeglądów, które umożliwiają zbieranie i pobieranie dużych ilości Teams zawartości w jednym przypadku.

Aby uzyskać więcej informacji na temat zwiększonych limitów przypadków, zobacz [Używanie nowego formatu przypadku w Advanced eDiscovery](advanced-ediscovery-new-case-format.md).

Aby utworzyć przypadek:

1. Przejdź do i <https://compliance.microsoft.com> zaloguj się.

2. W okienku nawigacji po lewej stronie Centrum zgodności platformy Microsoft 365 kliknij pozycję **eDiscovery > Advanced**.

3. Na stronie **Advanced eDiscovery** kliknij kartę **Przypadki**, a następnie kliknij **pozycję Utwórz przypadek**.

   Zostanie wyświetlona strona Wysuwane **nowe przypadki zbierania elektronicznych** materiałów dowodowych. Sekcja **Format przypadku** zawiera opcję utworzenia sprawy przy użyciu nowego formatu wielkości liter.

   ![Opcja Duży przypadek na stronie Nowy przypadek zbierania elektronicznych materiałów dowodowych.](..\media\AeDNewCaseFormat1.png)

4. Po nazewnictwie sprawy wybierz opcję **Nowy** , a następnie kliknij przycisk **Zapisz** , aby utworzyć przypadek.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Dodawanie Teams źródeł danych opieki i zachowywanie zawartości Teams  

Następnym krokiem jest zidentyfikowanie użytkowników, którzy są opiekunami danych w badaniu, oraz dodanie ich i ich lokalizacji zawartości jako opiekunów do sprawy utworzonej w poprzedniej sekcji. Po dodaniu opiekunów możesz określić ich skrzynkę pocztową i konto OneDrive jako źródła danych opieki. Możesz również określić lokalizacje zawartości Teams jako źródła danych opiekunów, aby szybko wstrzymać te lokalizacje w celu zachowania zawartości podczas badania. Ułatwia również zbieranie zawartości i dodawanie jej do zestawu przeglądów.

Aby dodać opiekunów do sprawy i zachować źródła danych opieki:

1. Przejdź do Advanced eDiscovery przypadku utworzonego w poprzedniej sekcji, a następnie kliknij pozycję **Źródła danych**.

2. Na stronie **Źródła danych** kliknij pozycję **Dodaj źródło** >  **danychDodaj nowych opiekunów**.

3. W kreatorze **Nowy opiekun** dodaj do sprawy co najmniej jednego użytkownika jako opiekuna, wpisując pierwszą część nazwy lub aliasu użytkownika. Po znalezieniu właściwej osoby wybierz jej imię i nazwisko, aby dodać ją do listy.  

4. Rozwiń każdego opiekuna, aby wyświetlić podstawowe źródła danych, które zostały automatycznie skojarzone z opiekunem, oraz wybrać inne lokalizacje do skojarzenia z opiekunem.

   ![Kustosze źródeł danych.](..\media\TeamsCustodialDataLocations1.png)

5. Postępuj zgodnie z tymi wytycznymi, aby dodać źródła danych opieki dla Teams zawartości. Kliknij pozycję **Edytuj** , aby dodać lokalizację danych.

   - **Skrzynki pocztowe**. Skrzynka pocztowa opiekuna jest domyślnie zaznaczona. Zachowaj tę opcję, aby dodać (i zachować) czaty 1:1, czaty grupowe i czaty kanału prywatnego jako dane powiernicze.

   - **OneDrive.** Konto OneDrive opiekuna jest domyślnie wybrane. Zachowaj tę opcję, aby dodać (i zachować) pliki udostępnione w czatach 1:1 i czatach grupowych jako dane opieki.

   - **SharePoint**. Dodaj witrynę SharePoint skojarzoną z dowolnym kanałem prywatnym lub udostępnionym, do którego należy opiekun, aby dodać (i zachować) jako dane powiernicze plików udostępnionych w kanale. Kliknij pozycję **Edytuj**, a następnie dodaj adres URL witryny SharePoint skojarzonej z kanałem prywatnym lub udostępnionym. Aby dowiedzieć się, jak zlokalizować kanały prywatne i udostępnione, do które należy użytkownik, zobacz [eDiscovery of private and shared channels (Zbierania elektronicznych materiałów dowodowych kanałów prywatnych i udostępnionych](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels)).

   - **Teams**. Dodaj zespoły, do których należy opiekun, aby dodać (i zachować) jako dane powiernicze wszystkie komunikaty kanału i wszystkie pliki udostępnione kanałowi Teams. Obejmuje to dodanie skrzynki pocztowej dla zespołu nadrzędnego udostępnionego kanału, do który należy opiekun. Po kliknięciu przycisku **Edytuj** skrzynka pocztowa i witryna skojarzona z każdym zespołem, do których należy opiekun, są wyświetlane na liście. Wybierz zespoły, które chcesz skojarzyć z opiekunem. Musisz wybrać odpowiednią skrzynkę pocztową i witrynę dla każdego zespołu.

   > [!NOTE]
   > Możesz również dodać skrzynkę pocztową i witrynę Teams, których opiekunowie nie są członkami jako lokalizacja danych opiekuna. W tym celu kliknij pozycję **Edytuj** obok **pozycji Exchange** i **SharePoint**, a następnie dodając skrzynkę pocztową i witrynę skojarzoną z zespołem.

6. Po dodaniu opiekunów i skonfigurowaniu źródeł danych nadzoru kliknij przycisk **Dalej** , aby wyświetlić stronę **Ustawienia blokady** .

   Zostanie wyświetlona lista opiekunów, a pole wyboru w kolumnie **Hold (Blokada** ) jest domyślnie zaznaczone. Oznacza to, że blokada zostanie umieszczona w źródłach danych skojarzonych z każdym opiekunem. Pozostaw zaznaczone pola wyboru, aby zachować te dane.

7. Na stronie **Ustawienia blokady** kliknij przycisk **Dalej** , aby przejrzeć ustawienia opiekunów. Kliknij pozycję **Prześlij** , aby dodać opiekunów do sprawy.

Aby uzyskać więcej informacji na temat dodawania i zachowywania źródeł danych w Advanced eDiscovery przypadku, zobacz:

- [Dodawanie opiekunów do sprawy Advanced eDiscovery](add-custodians-to-case.md)

- [Dodawanie źródeł danych bez opieki do sprawy Advanced eDiscovery](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Zbieranie zawartości Teams i dodawanie do zestawu przeglądów

Po dodaniu opiekunów do sprawy i zachowaniu zawartości w źródłach danych opiekunów następnym krokiem w przepływie pracy jest wyszukanie Teams zawartości, która jest istotna dla twojego badania, i dodanie jej do zestawu przeglądów w celu dalszego przeglądu i analizy. Chociaż typowe jest zbieranie zawartości Teams wraz z zawartością z innych usług Microsoft 365, takich jak poczta e-mail w Exchange i dokumenty w SharePoint, ta sekcja koncentruje się w szczególności na zbieraniu zawartości Teams w kolekcji. Możesz utworzyć dodatkowe kolekcje, które zbierają zawartość bez Teams, aby dodać ją do zestawu przeglądów.

Podczas zbierania Teams zawartości w przypadku przepływu pracy istnieją dwa kroki:

1. **Utwórz kolekcję roboczą**.  Pierwszym krokiem jest utworzenie *kolekcji roboczej*, która jest oszacowaniem elementów zgodnych z kryteriami wyszukiwania. Możesz wyświetlić informacje o wynikach dopasowanych do zapytania wyszukiwania, takie jak całkowita liczba i rozmiar znalezionych elementów, różne źródła danych, w których zostały znalezione, oraz statystyki dotyczące zapytania wyszukiwania. Możesz również wyświetlić podgląd przykładu elementów, które zostały zwrócone przez kolekcję. Korzystając z tych statystyk, możesz zmienić zapytanie wyszukiwania i ponownie uruchomić kolekcję roboczą tyle razy, ile jest to konieczne, aby zawęzić wyniki, dopóki nie będziesz zadowolony, że zbierasz zawartość odpowiednią dla Twojego przypadku.

2. **Zatwierdź kolekcję roboczą do zestawu przeglądów**. Gdy wyniki kolekcji roboczej będą zadowalające, możesz zatwierdzić kolekcję w zestawie przeglądów. Po zatwierdzeniu kolekcji roboczej elementy zwracane przez kolekcję są dodawane do zestawu przeglądów do przeglądania, analizy i eksportowania.

Istnieje również możliwość nie uruchamiania kolekcji roboczej i dodawania wyników kolekcji bezpośrednio do zestawu przeglądów podczas tworzenia i uruchamiania kolekcji.

Aby utworzyć kolekcję zawartości Teams:

1. Przejdź do Advanced eDiscovery przypadku, do których dodano opiekunów w poprzedniej sekcji, a następnie kliknij pozycję **Kolekcje**.

2. Na stronie **Kolekcje** wybierz pozycję **Nowa** **kolekcjaStandard** >  kolekcja.

3. Wpisz nazwę (wymagane) i opis (opcjonalnie) dla kolekcji.

4. Na stronie **Źródła danych opieki** kliknij pozycję **Wybierz opiekunów** , aby wybrać opiekunów dodanych do sprawy.

   Lista opiekunów sprawy jest wyświetlana na stronie wysuwanej **Wybieranie opiekunów** .

5. Wybierz co najmniej jednego opiekuna, a następnie kliknij przycisk **Dodaj**.

   Po dodaniu określonych opiekunów do kolekcji zostanie wyświetlona lista określonych źródeł danych dla każdego opiekuna. Są to źródła danych skonfigurowane podczas dodawania opiekuna do sprawy. Domyślnie wybierane są wszystkie źródła danych opiekuna. Obejmuje to wszystkie Teams lub kanały skojarzone z opiekunem.

   Zalecamy wykonanie następujących czynności podczas zbierania zawartości Teams:

   - Usuń konta OneDrive opiekunów z zakresu kolekcji (usuwając zaznaczenie pola wyboru w kolumnie **OneDrive opiekuna** dla każdego opiekuna). Uniemożliwia to zbieranie zduplikowanych plików dołączonych do czatów 1:1 i czatów grupowych. Załączniki w chmurze są automatycznie zbierane z każdej konwersacji znalezionej w kolekcji po zatwierdzeniu kolekcji roboczej do zestawu przeglądów. Korzystając z tej metody (zamiast przeszukiwać konta OneDrive w ramach kolekcji), pliki dołączone do wersji 1:1 i czaty grupowe są grupowane w konwersacji, w ramach których zostały udostępnione.

   - Usuń zaznaczenie pola wyboru w kolumnie **Dodatkowa witryna**, aby usunąć witryny SharePoint zawierające pliki udostępnione w kanałach prywatnych lub udostępnionych. Eliminuje to zbieranie zduplikowanych plików dołączonych do konwersacji w kanale prywatnym lub udostępnionym, ponieważ te załączniki w chmurze są automatycznie dodawane do zestawu przeglądów podczas zatwierdzania kolekcji roboczej i grupowania ich w konwersacjach, w których zostały udostępnione.

6. Jeśli wcześniej wykonaliśmy kroki dodawania zawartości Teams jako źródeł danych opiekuna, możesz pominąć ten krok i wybrać przycisk **Dalej**. W przeciwnym razie na stronie Kreatora **źródeł danych bez nadzoru** można wybrać źródła danych bez nadzoru zawierające Teams zawartości, które mogły zostać dodane do sprawy w celu wyszukania w kolekcji.

7. Jeśli wcześniej wykonaliśmy kroki dodawania zawartości Teams jako źródeł danych opiekuna, możesz pominąć ten krok i wybrać przycisk **Dalej**. W przeciwnym razie na stronie Kreator **dodatkowych lokalizacji** możesz dodać inne źródła danych do wyszukiwania w kolekcji. Możesz na przykład dodać skrzynkę pocztową i witrynę dla zespołu, który nie został dodany jako źródło danych bez nadzoru. W przeciwnym razie wybierz pozycję **Dalej** i pomiń ten krok.

8. Na stronie Kreator **warunków** skonfiguruj zapytanie wyszukiwania w celu zbierania Teams zawartości ze źródeł danych określonych na poprzednich stronach kreatora. Możesz użyć różnych słów kluczowych i warunków wyszukiwania, aby zawęzić zakres kolekcji. Aby uzyskać więcej informacji, zobacz [Tworzenie zapytań wyszukiwania dla kolekcji](building-search-queries.md).

   Aby zapewnić najbardziej kompleksową kolekcję Teams konwersacji na czacie (w tym 1:1, czatów grupowych i kanałowych), użyj warunku **Typ** i wybierz opcję **Wiadomości błyskawiczne**. Zalecamy również uwzględnienie zakresu dat lub kilku słów kluczowych, aby zawęzić zakres kolekcji do elementów związanych z badaniem. Oto zrzut ekranu przedstawiający przykładowe zapytanie korzystające z opcji **Typ** i **Data** :

   ![Zapytanie dotyczące zbierania zawartości Teams.](..\media\TeamsConditionsQueryType.png)

9. Na stronie **Kreator zapisywania wersji roboczej lub zbierania** wykonaj jedną z następujących czynności w zależności od tego, czy chcesz utworzyć kolekcję roboczą, czy zatwierdzić kolekcję w zestawie przeglądów.

   ![Zapisz kolekcję roboczą lub kolekcję zatwierdzeń.](..\media\TeamsDraftCommitCollection.png)

   1. **Zapisz kolekcję jako wersję roboczą**. Wybierz tę opcję, aby utworzyć kolekcję roboczą. Jak wyjaśniono wcześniej, kolekcja robocza nie dodaje wyników kolekcji do zestawu przeglądów. Zwraca oszacowanie wyników wyszukiwania zgodnych z zapytaniem wyszukiwania dla źródeł danych w zakresie kolekcji. Dzięki temu możesz wyświetlić [statystyki kolekcji i raporty[(collection-statistics-reports.md)] oraz edytować i ponownie uruchomić kolekcję roboczą. Jeśli wynik kolekcji roboczej jest zadowalający, możesz zatwierdzić ją w zestawie przeglądów. Aby uzyskać więcej informacji, zobacz [Tworzenie kolekcji roboczej](create-draft-collection.md).

   2. **Zbierz elementy i dodaj je do zestawu przeglądów**. Wybierz tę opcję, aby uruchomić kolekcję, a następnie dodaj wyniki do zestawu przeglądów. Kolekcję można dodać do nowego lub istniejącego zestawu przeglądów. Opcje zbierania kontekstowych Teams komunikatów konwersacji (nazywanych również *wątkami konwersacji*) i zbierania załączników w chmurze są domyślnie wybierane i nie można ich wybrać. Te opcje są stosowane automatycznie ze względu na nowy format przypadku, który był używany podczas początkowego tworzenia przypadku Teams zawartości. Aby uzyskać więcej informacji na temat zatwierdzania kolekcji w zestawie przeglądów, zobacz [Zatwierdzanie kolekcji roboczej do zestawu przeglądów](commit-draft-collection.md).

10. Po zakończeniu konfigurowania kolekcji prześlij kolekcję, aby utworzyć kolekcję roboczą lub zebrać elementy i dodać je do zestawu przeglądów.

   Po zakończeniu procesu dodawania kolekcji do zestawu przeglądów wartość stanu kolekcji na karcie **Kolekcje** jest ustawiona na **wartość Zatwierdzone**.

## <a name="review-teams-content-in-a-review-set"></a>Przeglądanie zawartości Teams w zestawie przeglądów

Po dodaniu kolekcji zawartości Teams do zestawu przeglądów następnym krokiem jest przejrzenie zawartości pod kątem jej istotności dla badania i usunięcie jej w razie potrzeby. Ważnym wymaganiem wstępnym przeglądania zawartości Teams jest zrozumienie, w jaki sposób Advanced eDiscovery przetwarza Teams konwersacje i załączniki rozmów podczas dodawania ich do zestawu przeglądów. To przetwarzanie zawartości Teams powoduje wykonanie następujących trzech czynności:

- **[Grupowanie](#grouping)**. Sposób grupowania wiadomości, wpisów i odpowiedzi Teams konwersacji i prezentowania ich w zestawie przeglądów. Obejmuje to również załączniki w konwersacjach rozmów są wyodrębniane i grupowane w konwersacji.

- **[Transkrypcja wątków konwersacji](#transcript-conversation-threading)**. Jak Advanced eDiscovery określa, jaka dodatkowa zawartość konwersacji ma być zbierana w celu zapewnienia kontekstu wokół elementów zgodnych z kryteriami kolekcji.

- **[Deduplikacja](#deduplication-of-teams-content)**. Jak Advanced eDiscovery obsługuje zduplikowaną zawartość Teams.

- **[Metadane](#metadata-for-teams-content)**. Właściwości metadanych, które Advanced eDiscovery dodawane do zawartości Teams po jej zebraniu i dodaniu do zestawu przeglądów.

Omówienie grupowania, wątków konwersacji, deduplikacji i metadanych Teams pomoże zoptymalizować przegląd i analizę zawartości Teams. Ta sekcja zawiera również [wskazówki dotyczące wyświetlania zawartości Teams w zestawie przeglądów](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Grupowanie

Gdy zawartość z Teams konwersacji czatu jest dodawana do zestawu przeglądów, wiadomości, wpisy i odpowiedzi z konwersacji są agregowane w plikach transkrypcji HTML. Konwersacja z jednym czatem może zawierać wiele plików transkrypcji. Ważną funkcją tych plików transkrypcji jest prezentowanie zawartości Teams jako ciągłych konwersacji, a nie jako pojedynczych (lub oddzielnych) komunikatów. Pomaga to zapewnić kontekst dla elementów spełniających kryteria wyszukiwania kolekcji w poprzednim kroku i zmniejszyć liczbę elementów zebranych do zestawu przeglądów. Transkrypcje i skojarzone elementy można grupować według *rodziny* lub *konwersacji*. Elementy w tej samej rodzinie będą miały taką samą wartość dla właściwości **FamilyId** metadata. Elementy w tej samej konwersacji będą miały taką samą wartość dla właściwości metadanych **ConversationId** .

W poniższej tabeli opisano sposób grupowania różnych typów Teams zawartości czatu według rodziny i konwersacji.

|typ zawartości Teams|Grupuj według rodziny|Grupuj według konwersacji|
|---|---|---|
|Teams 1:1 i czaty grupowe|Transkrypcja i wszystkie jej załączniki i wyodrębnione elementy mają ten sam **identyfikator FamilyId**. Każda transkrypcja ma unikatowy **identyfikator FamilyId**.|Wszystkie pliki transkrypcji i ich elementy rodzinne w ramach tej samej konwersacji mają ten sam **identyfikator Konwersacji**. Obejmuje to następujące elementy: <ul><li>Wszystkie wyodrębnione elementy i załączniki wszystkich transkrypcji, które mają ten sam **identyfikator Konwersacji**.</li><li>Wszystkie transkrypcje dla tej samej konwersacji na czacie</li><li>Wszystkie kopie każdego transkrypcji dla opiekunów</li><li>Transkrypcje z kolejnych kolekcji z tej samej konwersacji na czacie</li></ul> <br/> W przypadku Teams 1:1 i rozmów grupowych możesz mieć wiele plików transkrypcji, z których każdy odpowiada innym ramom czasowym w konwersacji. Ponieważ te pliki transkrypcji pochodzą z tej samej konwersacji z tymi samymi uczestnikami, mają ten sam **identyfikator ConversationId**.|
|Standardowe, prywatne i udostępnione czaty na kanale|Każdy wpis oraz wszystkie odpowiedzi i załączniki są zapisywane we własnej transkrypcji. Ta transkrypcja i wszystkie jej załączniki i wyodrębnione elementy mają ten sam **identyfikator FamilyId**.|Każdy wpis oraz jego załączniki i wyodrębnione elementy mają unikatowy **identyfikator Konwersacji**. Jeśli istnieją kolejne kolekcje lub nowe odpowiedzi z tego samego wpisu, transkrypcje różnicowe wynikające z tych kolekcji również będą miały ten sam **identyfikator ConversationId**.|

Użyj kontrolki **Grupa** na pasku poleceń zestawu przeglądów, aby wyświetlić Teams zawartości pogrupowane według rodziny lub konwersacji.

![Kontrolka grupy na pasku poleceń.](..\media\TeamsGroupControl.png)

- Wybierz pozycję **Grupuj załączniki rodziny**, aby wyświetlić Teams zawartość pogrupowana według rodziny. Każdy plik transkrypcji jest wyświetlany w wierszu na liście elementów zestawu przeglądów. Załączniki są zagnieżdżone pod elementem.

- Wybierz pozycję **Grupuj Teams lub Yammer konwersacje**, aby wyświetlić Teams zawartość pogrupowana według konwersacji. Każda konwersacja jest wyświetlana w wierszu na liście elementów zestawu przeglądów. Pliki transkrypcji i załączniki są zagnieżdżone w konwersacji najwyższego poziomu.

> [!NOTE]
> Załączniki w chmurze są grupowane z konwersacjami, w których się pojawiają. To grupowanie odbywa się przez przypisanie tego samego **identyfikatora FamilyId** co plik transkrypcji komunikatu, do który został dołączony plik, i ten sam **identyfikator Konwersacji co** konwersacja, w ramach która pojawiła się w komunikacie. Oznacza to, że wiele kopii załączników w chmurze może zostać dodanych do zestawu przeglądów, jeśli zostały dołączone do różnych konwersacji.

#### <a name="viewing-transcript-files-for-conversations"></a>Wyświetlanie plików transkrypcji dla konwersacji

Podczas wyświetlania plików transkrypcji w zestawie przeglądów niektóre komunikaty są wyróżnione w kolorze fioletowym. Wyróżnione komunikaty zależą od kopii wyświetlanej transkrypcji przez opiekuna. Na przykład podczas czatu 1:1 między użytkownikiem User4 i User2 wiadomości publikowane przez użytkownika User4 są wyróżnione w kolorze fioletowym podczas wyświetlania transkrypcji zebranej ze skrzynki pocztowej użytkownika User4. Podczas wyświetlania transkrypcji użytkownika User2 tej samej konwersacji komunikaty publikowane przez użytkownika User2 są wyróżnione w kolorze fioletowym. To zachowanie wyróżniania jest oparte na tym samym Teams środowisku klienta, w którym wpisy użytkownika są wyróżnione w kolorze fioletowym w kliencie Teams.

Poniższe zrzuty ekranu przedstawiają przykład konwersacji w kliencie Teams i plik transkrypcji tej samej konwersacji w zestawie przeglądów. Purpurowe wyróżnianie w pliku transkrypcji wskazuje, że transkrypcja została zebrana ze skrzynki pocztowej Użytkownika 2.

##### <a name="conversation-in-teams-client"></a>Konwersacja w kliencie Teams

![Konwersacja wyświetlana w pliku transkrypcji w zestawie przeglądów.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Konwersacja w pliku transkrypcji

![Ta sama konwersacja pokazana w kliencie Teams.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Transkrypcja wątków konwersacji

Funkcja wątków konwersacji w nowym formacie przypadku w Advanced eDiscovery ułatwia identyfikowanie zawartości kontekstowej związanej z elementami, które mogą być istotne dla badania. Ta funkcja tworzy różne widoki konwersacji, które zawierają komunikaty czatów poprzedzające elementy i zgodne z elementami zapytania wyszukiwania podczas zbierania. Ta funkcja umożliwia wydajne i szybkie przeglądanie pełnych konwersacji na czacie (*nazywanych konwersacjami wątkowymi*) w Microsoft Teams. Jak wyjaśniono wcześniej, konwersacje na czacie są rekonstruowane w plikach transkrypcji HTML, gdy Advanced eDiscovery dodaje zawartość Teams do zestawu przeglądów.

Oto logika używana przez Advanced eDiscovery do dołączania dodatkowych komunikatów i plików transkrypcji odpowiedzi, które zapewniają kontekst wokół elementów zgodnych z zapytaniem kolekcji (nazywanymi *elementami responsywnymi*) używanymi podczas zbierania Teams zawartości. Różne zachowania wątków są oparte na typach czatów i zapytaniu wyszukiwania używanym do zbierania elementów dynamicznych. Istnieją dwa typowe scenariusze zbierania danych:

- Zapytania używające parametrów wyszukiwania, takich jak słowa kluczowe i pary property:value

- Zapytania korzystające tylko z zakresów dat

|typ zawartości Teams|Zapytania z parametrami wyszukiwania|Zapytania z zakresami dat|
|---|---|---|
|Teams 1:1 i czaty grupowe|Komunikaty, które zostały opublikowane 12 godzin przed i 12 godzin po elementach responsywnych, są pogrupowane z elementem dynamicznym w pojedynczym pliku transkrypcji.|Komunikaty w oknie 24-godzinnym są grupowane w jednym pliku transkrypcji.|
|Standardowe, prywatne i udostępnione czaty kanałów Teams|Każdy wpis zawierający elementy dynamiczne i wszystkie odpowiadające im odpowiedzi są pogrupowane w pojedynczym pliku transkrypcji.|Każdy wpis zawierający elementy dynamiczne i wszystkie odpowiadające im odpowiedzi są pogrupowane w pojedynczym pliku transkrypcji.|

### <a name="deduplication-of-teams-content"></a>Deduplikacja zawartości Teams

Na poniższej liście opisano zachowanie deduplikacji (i duplikowania) podczas zbierania zawartości Teams do zestawu przeglądów.

- Każdy plik transkrypcji dodany do zestawu przeglądów powinien być mapowaniem jeden do jednego na zawartość przechowywaną w lokalizacjach danych. Oznacza to, że Advanced eDiscovery nie zbiera żadnych Teams zawartości, która została już dodana do zestawu przeglądów. Jeśli wiadomość czatu jest już zbierana w zestawie przeglądów, Advanced eDiscovery nie dodaje tego samego komunikatu z tej samej lokalizacji danych do zestawu przeglądów w kolejnych kolekcjach.

- W przypadku czatów grupowych i 1:1 kopie wiadomości są przechowywane w skrzynce pocztowej każdego uczestnika konwersacji. Kopie tej samej konwersacji, które istnieją w skrzynkach pocztowych różnych uczestników, są zbierane z różnymi metadanymi. W rezultacie każde wystąpienie konwersacji jest traktowane jako unikatowe i wprowadzane do zestawu przeglądów w oddzielnych plikach transkrypcji. Jeśli więc wszyscy uczestnicy czatu grupowego 1:1 lub zostaną dodani jako opiekunowie w danym przypadku i uwzględnieni w zakresie kolekcji, kopie każdej transkrypcji (dla tej samej ochrony) zostaną dodane do zestawu przeglądów i zostaną zgrupowane razem z tym samym **identyfikatorem ConversationId**. Każda z tych kopii jest skojarzona z odpowiednim opiekunem. **Porada**: Kolumna **Kustosz** na liście zestawu przeglądów identyfikuje opiekuna odpowiedniego pliku transkrypcji.

- W kolejnych kolekcjach elementów z tej samej konwersacji tylko zawartość delta, która nie została wcześniej zebrana, jest dodawana do zestawu przeglądów i grupowana (przez udostępnienie tego samego **identyfikatora Konwersacji**) z wcześniej zebranymi transkrypcjami z tej samej konwersacji. Oto przykład tego zachowania:

   1. Kolekcja A zbiera komunikaty w konwersacji między użytkownikami User1 i User2 i dodaje do zestawu przeglądów.

   2. Kolekcja B zbiera komunikaty z tej samej konwersacji, ale istnieją nowe komunikaty między użytkownikami User1 i User2 od momentu uruchomienia kolekcji A.

   3. Tylko nowe komunikaty w kolekcji B są dodawane do zestawu przeglądów. Te komunikaty są dodawane do oddzielnego pliku transkrypcji, ale nowa transkrypcja jest pogrupowana z transkrypcjami z kolekcji A według tego samego **identyfikatora Konwersacji**.

   To zachowanie ma zastosowanie do wszystkich typów czatów Teams.

### <a name="metadata-for-teams-content"></a>Metadane zawartości Teams

W dużych zestawach przeglądów z tysiącami lub milionami elementów może być trudno zawęzić zakres przeglądu, aby Teams zawartość. Aby ułatwić skoncentrowanie przeglądu na zawartości Teams, istnieją właściwości metadanych specyficzne dla Teams zawartości. Te właściwości umożliwiają organizowanie kolumn na liście [przeglądów oraz konfigurowanie filtrów i zapytań](review-set-search.md) w celu zoptymalizowania przeglądu zawartości Teams. Te właściwości metadanych są również uwzględniane podczas eksportowania zawartości Teams z Advanced eDiscovery, aby ułatwić organizowanie i wyświetlanie zawartości po wyeksportowaniu lub w narzędziach zbierania elektronicznych materiałów dowodowych innych firm.

W poniższej tabeli opisano właściwości metadanych Teams zawartości.

|Właściwość metadanych|Opis|
|---|---|
|ContainsEditedMessage|Wskazuje, czy plik transkrypcji zawiera edytowany komunikat. Edytowane komunikaty są identyfikowane podczas wyświetlania pliku transkrypcji.|
|ConversationId|Identyfikator GUID identyfikujący konwersację, z którą jest skojarzony element. Pliki transkrypcji i załączniki z tej samej konwersacji mają tę samą wartość dla tej właściwości.|
|Nazwa konwersacji|Nazwa konwersacji, z która jest skojarzony plik transkrypcji lub załącznik. W przypadku Teams 1:1 i czatów grupowych wartość tej właściwości to nazwa UPN wszystkich uczestników konwersacji. Na przykład `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams czatów w kanałach (standardowych, prywatnych i udostępnionych) użyj następującego formatu dla nazwy konwersacji: `<Team name>,<Channel name>`. Na przykład `eDiscovery vNext, General`.|
|Typ konwersacji|Wskazuje typ czatu zespołowego. W przypadku Teams 1:1 i czatów grupowych wartość tej właściwości to `Group`. W przypadku standardowych, prywatnych i udostępnionych czatów kanałowych wartość to `Channel`.|
|Data|Sygnatura czasowa pierwszej wiadomości w pliku transkrypcji.|
|Identyfikator rodziny|Identyfikator GUID identyfikujący plik transkrypcji konwersacji na czacie. Załączniki będą miały tę samą wartość dla tej właściwości co plik transkrypcji zawierający komunikat, do który został dołączony.|
|FileClass|Wskazuje ten typ zawartości. Elementy z czatów Teams mają wartość `Conversation`. Z kolei Exchange wiadomości e-mail mają wartość `Email`.|
|MessageKind|Właściwość rodzaju komunikatu. Teams zawartość ma wartość `microsoftteams , im`.|
|Adresatów|Lista wszystkich użytkowników, którzy otrzymali wiadomość w konwersacji transkrypcji.|
|TeamsChannelName|Nazwa kanału Teams transkrypcji.|

Opisy innych Advanced eDiscovery właściwości metadanych można znaleźć [w temacie Document metadata fields in Advanced eDiscovery (Pola metadanych dokumentu w Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md)).

## <a name="export-teams-content"></a>Eksportowanie zawartości Teams

Po przejrzeniu i usunięciu zawartości Teams w zestawie przeglądów można wyeksportować pliki transkrypcji zawierające zawartość reagującą na badanie. Nie ma żadnych konkretnych ustawień eksportu dla Teams zawartości. Każdy plik transkrypcji jest eksportowany jako plik komunikatu HTML. Ten plik zawiera również ukryte tagi CDATA ze wszystkimi metadanymi dla poszczególnych wiadomości czatu. Właściwości metadanych omówione w poprzedniej sekcji są uwzględniane podczas eksportowania Teams zawartości.  

Do każdego pliku transkrypcji odwołuje się plik ładowania i można go znaleźć przy użyciu ścieżki względnej w polu Export_native_path w pliku ładowania. Pliki transkrypcji znajdują się w folderze Konwersacje w głównym folderze eksportowania.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Wskazówki do wyświetlania zawartości Teams w zestawie przeglądów

Poniżej przedstawiono kilka wskazówek i najlepszych rozwiązań dotyczących wyświetlania zawartości Teams w zestawie przeglądów.

- Użyj kontrolki **Dostosuj kolumny** na pasku poleceń, aby dodawać i organizować kolumny, aby zoptymalizować przegląd zawartości Teams.

  ![Użyj strony wysuwanej kolumny Edytuj kolumnę, aby dodawać, usuwać i organizować kolumny.](..\media\EditReviewSetColumns.png)

   Możesz dodawać i usuwać kolumny, które są przydatne do Teams zawartości. Kolejność kolumn można również sekwencjonować, przeciągając i upuszczając je na stronie wysuwanej **kolumny Edytuj** . Możesz również sortować kolumny, aby grupować zawartość Teams z podobnymi wartościami dla kolumny, którą sortujesz.

- Przydatne kolumny ułatwiające przeglądanie zawartości Teams obejmują **opiekuna**, **adresatów** i **typ pliku** lub **rodzaj wiadomości**.

- Użyj [filtrów](review-set-search.md) dla właściwości związanych z Teams, aby szybko wyświetlić zawartość Teams. Istnieją filtry dla większości właściwości metadanych opisanych w poprzedniej sekcji.

## <a name="deleting-teams-chat-messages"></a>Usuwanie wiadomości Teams czatu

Za pomocą Advanced eDiscovery i Eksploratora Graph Firmy Microsoft można reagować na zdarzenia związane z wyciekiem danych, gdy zawartość zawierająca poufne lub złośliwe informacje jest udostępniana za pośrednictwem Teams wiadomości czatu. Administratorzy w organizacji mogą wyszukiwać i usuwać wiadomości czatów w Microsoft Teams. Może to pomóc w usunięciu poufnych informacji lub nieodpowiedniej zawartości w Teams wiadomościach czatu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i przeczyszczanie wiadomości czatu w Teams](search-and-delete-Teams-chat-messages.md).

## <a name="reference-guide"></a>Przewodnik referencyjny

Oto krótki przewodnik referencyjny dotyczący używania Advanced eDiscovery dla Microsoft Teams. Ten przewodnik zawiera podsumowanie punktów kluczy do używania Advanced eDiscovery do zachowywania, zbierania, przeglądania i eksportowania zawartości z Microsoft Teams.

![Miniatura przewodnika referencyjnego do używania Advanced eDiscovery dla Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[Pobieranie jako pliku PDF](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
