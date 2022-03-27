---
title: Teams przepływu pracy w programie Advanced eDiscovery
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
description: Dowiedz się, jak zachowywać, zbierać, przeglądać i eksportować zawartość z witryny Microsoft Teams w programie Advanced eDiscovery.
ms.openlocfilehash: 68a255dda7aa9b879c9e608eb99c9575ba691c16
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716229"
---
# <a name="advanced-ediscovery-workflow-for-content-in-microsoft-teams"></a>Advanced eDiscovery przepływu pracy dla zawartości w programie Microsoft Teams

Ten artykuł zawiera obszerny zestaw procedur, wytycznych i najlepszych rozwiązań dotyczących używania aplikacji Advanced eDiscovery zachowywania, gromadzenia, przeglądania i eksportowania zawartości z usługi Microsoft Teams. Celem tego artykułu jest zoptymalizowanie przepływu pracy zbierania elektronicznych materiałów dowodowych pod kątem Teams zawartości.

Istnieje pięć kategorii zawartości Teams, które można zbierać i przetwarzać przy użyciu Advanced eDiscovery:

- **Teams czatach 1:1**. Wiadomości na czacie, wpisy i załączniki udostępniane w Teams konwersacji między dwiema osobami.  Teams czaty między 1:1 są również nazywane *konwersacjami*.

- **Teams czatów grupowych**. Czat z wiadomościami, wpisami i załącznikami udostępnionym Teams konwersacji między trzema lub większą ich liczby osobami. Nazywane również *czatami 1:N* lub *konwersacjami grupowych*.

- **Teams kanałów**. Czat z wiadomościami, wpisami, odpowiedziami i załącznikami udostępnianymi w standardowym Teams kanale.

- **Kanały prywatne**. Wpisy wiadomości, odpowiedzi i załączniki udostępnione w prywatnym Teams kanału.

- **Udostępnione kanały**. Wpisy wiadomości, odpowiedzi i załączniki udostępnione w udostępnionym Teams kanale.

## <a name="where-teams-content-is-stored"></a>Miejsce Teams zawartości

Wstępnie wymagane do zarządzania zawartością Teams w programie Advanced eDiscovery jest zrozumienie typu zawartości Teams, która może być zbierana, przetwarzana i przeglądana w programie Advanced eDiscovery oraz miejscu jej przechowywania w programie Microsoft 365. W poniższej tabeli po Teams typ zawartości i miejsce przechowywania każdej z nich.

||Lokalizacja wiadomości i wpisów na czacie  |Lokalizacja plików i załączników |
|:---------|:---------|:---------|
|Teams czatów 1:1     |Wiadomości w czatach 1:1 są przechowywane w Exchange Online skrzynki pocztowej wszystkich uczestników czatu. |Pliki udostępnione na czacie 1:1 są przechowywane OneDrive dla Firm konta osoby, która udostępniła plik. |
|Teams czatów grupowych     |Wiadomości w czatach grupowych są przechowywane Exchange Online skrzynce pocztowej wszystkich uczestników czatu. |Pliki udostępniane w czatach grupowych są przechowywane OneDrive dla Firm konta osoby, która udostępniła plik. |
|Teams kanałów     |Wszystkie wiadomości i wpisy w kanałach są przechowywane w Exchange Online skojarzonej z zespołem skrzynki pocztowej.|Pliki udostępniane w kanale są przechowywane w SharePoint Online skojarzonej z zespołem.           |
|Kanały prywatne     |Wiadomości wysłane w kanale prywatnym są przechowywane w Exchange Online pocztowych wszystkich członków kanału prywatnego.|Pliki udostępnione w kanale prywatnym są przechowywane w dedykowanej witrynie SharePoint online skojarzonej z kanałem prywatnym.|
|Kanały udostępnione     |Wiadomości wysłane w kanale udostępnionym są przechowywane w systemowej skrzynce pocztowej skojarzonej z kanałem udostępnionym. <sup>1</sup>|Pliki udostępniane w kanale udostępnionym są przechowywane w dedykowanej SharePoint Online skojarzonej z kanałem udostępnionym.|
||||

> [!NOTE]
> <sup>1</sup> Aby wyszukać (i zachować) wiadomości wysłane w kanale udostępnionym, musisz przeszukać lub określić skrzynkę pocztową Exchange Online dla nadrzędnego zespołu.

## <a name="create-a-case-for-teams-content"></a>Tworzenie sprawy na Teams zawartości

Pierwszym krokiem do zarządzania zawartością Teams w programie Advanced eDiscovery jest utworzenie sprawy w nowym formacie sprawy zoptymalizowanym pod kątem zarządzania Teams zawartości. Oto zalety korzystania z nowego formatu sprawy do Teams przypadku:

- Obsługa wątków konwersacji, w której dodatkowe wiadomości w tej samej konwersacji, które zawierają elementy odpowiedzi, są automatycznie zbierane i dodawane do recenzji zestawów.

- Teams konwersacji na czacie są automatycznie dodawane do przeglądania zestawów jako plik transkrypcji HTML. Załączniki w chmurze udostępniane w konwersacjach są również dodawane do zestawu recenzji. Ułatwia to zapewnianie kontekstu do konwersacji za pomocą elementów odpowiadania i zmniejszanie całkowitej liczby elementów powiąnych przez zawartość opartą na czacie.

- Kolekcje o rozmiarze do 1 TB można dodać do recenzji zestawów, co pozwala zbierać duże ilości zawartości Teams ilości zawartości w przypadku.

Aby uzyskać więcej informacji o zwiększonych limitach liter, zobacz [Używanie nowego formatu liter w programie Advanced eDiscovery](advanced-ediscovery-new-case-format.md).

Aby utworzyć sprawę:

1. Przejdź do i <https://compliance.microsoft.com> zaloguj się.

2. W okienku nawigacji po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **zbierania elektronicznych materiałów** dowodowych > zaawansowane.

3. Na stronie **Advanced eDiscovery** kliknij kartę **Sprawy**, a następnie kliknij pozycję **Utwórz sprawę**.

   Zostanie **wyświetlona strona wysuwana** Nowa sprawa zbierania elektronicznych materiałów dowodowych. Sekcja **Format sprawy** umożliwia utworzenie sprawy przy użyciu nowego formatu sprawy.

   ![Opcja Dużych liter na stronie Nowa sprawa zbierania elektronicznych materiałów dowodowych.](..\media\AeDNewCaseFormat1.png)

4. Po nazewnictwie sprawy wybierz opcję **Nowy** , a następnie kliknij przycisk **Zapisz** , aby utworzyć sprawę.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Dodawanie Teams danych i zachowywanie zawartości Teams danych  

Następnym krokiem jest zidentyfikowanie użytkowników, którzy są osobami przechowywania danych podczas badania, i dodanie ich i lokalizacji zawartości jako osób przechoczyczy do sprawy utworzonej w poprzedniej sekcji. Podczas dodawania zawartości odbiorczej można określić ich skrzynki pocztowe i konta OneDrive jako źródła danych. Możesz także określić Teams jako źródła danych przechwycące, aby szybko umieścić te lokalizacje w zbędnych prawach w celu zachowania zawartości podczas badania. Ułatwia również zbieranie zawartości i dodawanie jej do zestawu recenzji.

Aby dodać do sprawy przechowywania i zachować źródła danych:

1. Przejdź do Advanced eDiscovery przypadku utworzonego w poprzedniej sekcji, a następnie kliknij **pozycję Źródła danych**.

2. Na stronie **Źródła danych** kliknij pozycję **Dodaj źródło danychDowiej** >  **nowe pliki przechowywania**.

3. W **kreatorze Nowy woło7** dodaj jednego lub więcej użytkowników jako osoby, które przechowają dane w przypadku sprawy, wpisując pierwszą część nazwy lub aliasu użytkownika. Po odnalezieniu odpowiedniej osoby wybierz jej nazwisko, aby dodać ją do listy.  

4. Rozwiń każdego opiekuna, aby wyświetlić podstawowe źródła danych, które zostały automatycznie skojarzone z tym opiekunem, oraz wybierz inne lokalizacje do skojarzenia z tym opiekunem.

   ![Źródła danych Wiad.](..\media\TeamsCustodialDataLocations1.png)

5. Postępuj zgodnie z tymi wskazówkami, aby dodać przykładowe źródła danych Teams zawartości. Kliknij **pozycję Edytuj** , aby dodać lokalizację danych.

   - **Skrzynki pocztowe**. Skrzynka pocztowa użytkownika korzystającego z tej skrzynki jest domyślnie zaznaczona. Zachowaj tę wybraną opcję, aby dodać (i zachować) czaty 1:1, czaty grupowe i czaty prywatnego kanału jako dane przechowujące.

   - **OneDrive.** Konto OneDrive jest domyślnie zaznaczone. Zachowaj tę wybraną opcję, aby dodać (i zachować) pliki udostępnione w czatach prywatnych i czatach grupowych jako dane chroniące.

   - **SharePoint**. Dodaj witrynę SharePoint skojarzoną z dowolnym kanałem prywatnym lub udostępnionym, do których należy administrator, aby dodać (i zachować) jako dane grupy treści udostępnione w kanale. Kliknij **pozycję Edytuj**, a następnie dodaj adres URL SharePoint skojarzonej z kanałem prywatnym lub udostępnionym. Aby dowiedzieć się, jak znaleźć kanały prywatne i udostępnione, do których należy użytkownik, zobacz Zbierania elektronicznych materiałów dowodowych w kanałach [prywatnych i udostępnionych](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

   - **Teams**. Dodaj zespoły, do których należy administrator, aby dodać (i zachować) jako dane dostępowe do wszystkich wiadomości kanału i wszystkich plików udostępnionych w kanale Teams kanału. Obejmuje to dodanie skrzynki pocztowej dla zespołu nadrzędnego kanału udostępnionego, do którym należy ten element. Po kliknięciu **przycisku Edytuj** na liście zostanie wyświetlona skrzynka pocztowa i witryna skojarzona z każdym zespołem, do którym należy ten zespół. Wybierz zespoły, które chcesz skojarzyć z opiekunem. Musisz wybrać zarówno odpowiednią skrzynkę pocztową, jak i witrynę dla każdego zespołu.

   > [!NOTE]
   > Można również dodać skrzynkę pocztową i witrynę Teams, które nie są członkami jako lokalizacja danych przechoczy. Możesz to zrobić, klikając pozycję **Edytuj** Exchange  grupy i **SharePoint a następnie** dodając skrzynkę pocztową i witrynę skojarzoną z zespołem.

6. Po dodaniu osób do przechowywania i skonfigurowaniu źródeł danych wieńczych **kliknij przycisk Dalej** , aby wyświetlić stronę **Ustawień blokowania** .

   Zostanie wyświetlona lista elementów przechowywania i domyślnie zaznaczone pole wyboru w kolumnie Wstrzymaj. Oznaczało to, że na źródłach danych skojarzonych z każdym powiązanym z nimi źródłami danych zostanie umieszczona hold. Pozostaw te pola wyboru zaznaczone, aby zachować te dane.

7. Na stronie **Ustawienia wstrzymywania** kliknij przycisk **Dalej** , aby przejrzeć ustawienia przechowywania. Kliknij **przycisk Submit** (Prześlij), aby dodać opiekunów do sprawy.

Aby uzyskać więcej informacji na temat dodawania i zachowywania źródeł danych w Advanced eDiscovery przypadku, zobacz:

- [Dodawanie elementów do Advanced eDiscovery przypadku](add-custodians-to-case.md)

- [Dodawanie niepowiązywnych źródeł danych do sprawy Advanced eDiscovery przypadku](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Zbieranie Teams zawartości i dodawanie do zestawu recenzji

Po dodaniu osób do sprawy i zachowaniu zawartości w źródłach danych, które są przechowywanie Teams m, następnym krokiem przepływu pracy jest wyszukanie zawartości istotnej dla prowadzonego badania i dodanie jej do zestawu recenzji w celu dalszego przejrzenia i analizy. Chociaż typowym zbieraniem zawartości usługi Teams razem z zawartością innych usług Microsoft 365, takich jak wiadomości e-mail w programie Exchange i dokumenty w programie SharePoint, ta sekcja dotyczy konkretnie zbierania zawartości Teams w kolekcji. Możesz utworzyć dodatkowe kolekcje, które zbierają Teams zawartości do dodania do zestawu recenzji.

Gdy zbierasz Teams dla sprawy, istnieją dwa kroki przepływu pracy:

1. **Utwórz kolekcję roboczą**.  Pierwszym krokiem jest utworzenie wersji *roboczej kolekcji*, która stanowi szacowaną wartość elementów spełniającą kryteria wyszukiwania. Możesz wyświetlić informacje o wynikach zapytania wyszukiwania, takie jak łączna liczba i rozmiar znalezionych elementów, różne źródła danych, w których zostały znalezione, oraz statystyki dotyczące zapytania wyszukiwania. Możesz również wyświetlić podgląd przykładowych elementów zwróconych przez kolekcję. Korzystając z tych statystyk, możesz zmienić zapytanie wyszukiwania i ponownie uruchomić kolekcję roboczą tyle razy, ile jest to konieczne, aby zawęzić wyniki, dopóki nie zawęzisz zbierania treści istotnych dla danej sprawy.

2. **Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji**. Po zadoweraniu wyników kolekcji roboczej możesz zatwierdzić kolekcję do zestawu recenzji. Po zatwierdzeniu wersji roboczej kolekcji elementy zwrócone przez kolekcję są dodawane do zestawu recenzji do przeglądania, analizy i eksportowania.

Możesz również nie uruchamiać kolekcji roboczej i dodawać wyniki kolekcji bezpośrednio do zestawu recenzji podczas tworzenia i uruchamiania kolekcji.

Aby utworzyć kolekcję Teams zawartości:

1. Przejdź do sprawy Advanced eDiscovery do poprzedniej sekcji, do których dodano części przechowacze, a następnie kliknij pozycję **Kolekcje**.

2. Na stronie **Kolekcje** wybierz pozycję **Nowa** **kolekcjaStandardowa** >  kolekcja.

3. Wpisz nazwę (wymaganą) i opis kolekcji (opcjonalnie).

4. Na stronie **Źródła danych Wiązywne** kliknij pozycję **Wybierz przechowywania** , aby wybrać przechowywania, które zostały dodane do sprawy.

   Lista elementów przechowawczych sprawy jest wyświetlana na **stronie wysuwu Wybierz selektorów** .

5. Zaznacz jeden lub więcej określników, a następnie kliknij przycisk **Dodaj**.

   Po dodaniu określonych elementów przechowywania do kolekcji zostanie wyświetlona lista określonych źródeł danych dla każdego źródła przechowywania. Są to źródła danych skonfigurowane po dodaniu do sprawy urządzenia do przechowywania. Domyślnie są zaznaczone wszystkie źródła danych, które są w nich wyeksjonowane. Dotyczy to wszelkich Teams lub kanałów powiązanych z opiekunem.

   Podczas zbierania zawartości w programie Teams zalecamy wykonanie następujących czynności:

   - Usuń konta elementów OneDrive z zakresu kolekcji (usuwając zaznaczenie pola wyboru w kolumnie OneDrive poszczególnych elementów dojściowych). Zapobiega to kolekcji zduplikowanych plików dołączonych do czatów jeden na jeden i czatów grupowych. Załączniki w chmurze są automatycznie zbierane z każdej konwersacji znalezionej w kolekcji po zatwierdzeniu kolekcji roboczej do zestawu recenzji. Przy użyciu tej metody (zamiast wyszukiwania kont OneDrive w ramach kolekcji) pliki dołączone do czatów grupowych i 1:1 są grupowane w konwersacji, w których zostały udostępnione.

   - Usuń zaznaczenie pola wyboru w kolumnie Dodatkowa witryna, aby usunąć SharePoint zawierających pliki udostępnione w kanałach prywatnych lub udostępnionych. Eliminuje to gromadzenie zduplikowanych plików dołączonych do konwersacji w kanale prywatnym lub udostępnionym, ponieważ te załączniki w chmurze są automatycznie dodawane do zestawu recenzji po zatwierdzeniu wersji roboczej kolekcji i zgrupowaniu w konwersacjach, w których zostały udostępnione.

6. Jeśli wcześniej wspomniano o dodaniu zawartości do Teams jako źródeł danych, można pominąć ten krok i wybrać przycisk **Dalej**. W przeciwnym razie na  stronie Kreatora niebędące danymi można wybrać źródła danych, które nie mają elementów Teams zawartości dodanej do sprawy w celu przeszukania w kolekcji.

7. Jeśli wcześniej wspomniano o dodaniu zawartości do Teams jako źródeł danych, można pominąć ten krok i wybrać przycisk **Dalej**. W przeciwnym razie na **stronie Kreator dodatkowych** lokalizacji możesz dodać inne źródła danych do wyszukiwania w kolekcji. Możesz na przykład dodać skrzynkę pocztową i witrynę zespołu, który nie został dodany jako źródło danych o niedobczasowym lub niedobczasowym źródle danych. W przeciwnym razie **wybierz przycisk Dalej** i pomiń ten krok.

8. Na stronie **kreatora** Warunki skonfiguruj zapytanie wyszukiwania w celu zbierania Teams zawartości ze źródeł danych określonych na poprzednich stronach kreatora. Zawęzić zakres kolekcji za pomocą różnych słów kluczowych i warunków wyszukiwania. Aby uzyskać więcej informacji, zobacz [Tworzenie zapytań wyszukiwania dla kolekcji](building-search-queries.md).

   Aby zapewnić najbardziej kompleksowy zbiór konwersacji za pomocą Teams czatów (w tym czatów 1:1, czatów grupowych i kanałów) użyj warunku  Typ i wybierz opcję **Wiadomości błyskawiczne**. Zalecamy również zastosowanie zakresu dat lub kilku słów kluczowych w celu zawężenia zakresu kolekcji do elementów istotnych dla twojego badania. Oto zrzut ekranu przedstawiający przykładowe zapytanie korzystające z **opcji Typ** **i** Data:

   ![Kwerenda zbiera Teams zawartości.](..\media\TeamsConditionsQueryType.png)

9. Na stronie **Zapisywanie wersji roboczej lub zbierania** kreatora wykonaj jedną z następujących czynności w zależności od tego, czy chcesz utworzyć kolekcję roboczą, czy zatwierdzić kolekcję do zestawu recenzji.

   ![Zapisywanie wersji roboczej kolekcji lub zatwierdzanie kolekcji.](..\media\TeamsDraftCommitCollection.png)

   1. **Zapisywanie kolekcji jako wersji roboczej**. Wybierz tę opcję, aby utworzyć kolekcję roboczą. Jak już wyjaśniono, wersja robocza kolekcji nie dodaje wyników kolekcji do zestawu recenzji. Zwraca ona szacowaną wartość wyników wyszukiwania, które są zgodne z zapytaniem wyszukiwania źródeł danych w zakresie kolekcji. Umożliwia to wyświetlenie [statystyk kolekcji i raportów[(collection-statistics-reports.md)] oraz edytowanie i ponowne uruchomić tę roboczą kolekcję. Jeśli wynik wersji roboczej kolekcji ci się podoba, możesz go zatwierdzić do zestawu recenzji. Aby uzyskać więcej informacji, [zobacz Tworzenie kolekcji roboczej](create-draft-collection.md).

   2. **Zbieranie elementów i dodawanie ich do zestawu recenzji**. Wybierz tę opcję, aby uruchomić kolekcję, a następnie dodać wyniki do zestawu recenzji. Kolekcję można dodać do nowego lub istniejącego zestawu recenzji. Opcje zbierania wiadomości Teams konwersacji (nazywanej także wątkiem *konwersacji*) i zbierania załączników w chmurze są domyślnie zaznaczone i nie można ich wybrać. Te opcje są automatycznie stosowane ze względu na nowy format sprawy użyty podczas tworzenia sprawy na Teams sprawy. Aby uzyskać więcej informacji na temat zatwierdzania kolekcji do zestawu recenzji, zobacz [Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji](commit-draft-collection.md).

10. Po zakończeniu konfigurowania kolekcji prześlij kolekcję, aby utworzyć kolekcję roboczą lub zebrać elementy i dodać je do zestawu recenzji.

   Po zakończeniu procesu dodawania kolekcji do zestawu recenzji wartość stanu kolekcji na karcie Kolekcje ma  wartość **Zatwierdzone**.

## <a name="review-teams-content-in-a-review-set"></a>Przeglądanie Teams zawartości w zestawie recenzji

Po dodaniu kolekcji Teams do zestawu recenzji następnym krokiem jest przejrzenie zawartości pod celu sprawdzenia jej istotności dla badania i w razie potrzeby jego pomylinie. Ważnym wymaganiem wstępnym przeglądania zawartości Teams jest zrozumienie, jak Advanced eDiscovery przetwarza Teams konwersacji na czacie i załączników podczas dodawania ich do zestawu recenzji. Takie przetwarzanie Teams powoduje następujące trzy rzeczy:

- **[Grupowanie](#grouping)**. Sposób grupowania wiadomości, wpisów i odpowiedzi Teams konwersacji i prezentowania ich w zestawie recenzji. Obejmuje to również załączniki w konwersacjach na czacie, które są wyodrębnione i grupowane w konwersacji.

- **[Transkrypcja wątków konwersacji](#transcript-conversation-threading)**. Sposób Advanced eDiscovery zawartości z konwersacji, która ma być zbierana w celu zapewnienia kontekstu wokół elementów, które spełniają kryteria kolekcji.

- **[Deduplication](#deduplication-of-teams-content)**. Jak Advanced eDiscovery zduplikowaną Teams zawartości.

- **[Metadane](#metadata-for-teams-content)**. Właściwości metadanych, Advanced eDiscovery dodawane Teams zawartości po jej zbierzeniu i dodaniu do zestawu recenzji.

Informacje na temat grupowania, wątków konwersacji, deduplikacji i Teams pomagają zoptymalizować przeglądanie i analizę Teams zawartości. Ta sekcja zawiera również [porady dotyczące wyświetlania Teams w zestawie recenzji](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Grupowanie

Po dodaniu zawartości Teams konwersacji na czacie do zestawu recenzji wiadomości, wpisy i odpowiedzi z konwersacji są agregowane w plikach transkrypcji HTML. Jedna konwersacja na czacie może mieć wiele plików transkrypcji. Ważną funkcją tych plików transkrypcji jest przedstawianie zawartości Teams jako ciągłej konwersacji, a nie jako osobnej (lub osobnej) wiadomości. Zapewnia to kontekst dla elementów, które pasują do kryteriów wyszukiwania kolekcji w poprzednim kroku, i zmniejsza liczbę elementów zebranych do zestawu recenzji. Transkrypcje i skojarzone elementy mogą być grupowane według *rodziny lub* *konwersacji*. Elementy w tej samej rodzinie będą mieć tę samą wartość dla właściwości metadanych **FamilyId** . Elementy w tej samej konwersacji będą mieć tę samą wartość dla właściwości metadanych **ConversationId** .

W poniższej tabeli opisano, jak różne typy wiadomości Teams są grupowane według rodziny i konwersacji.

| Teams typ zawartości|Grupowanie według rodziny  |Grupowanie według konwersacji  |
|:---------|:---------|:---------|
|Teams czatach grupowych i 1:1   | Transkrypcja i wszystkie jej załączniki oraz wyodrębnione elementy mają ten sam **element FamilyId**. Każda transkrypcja ma unikatowy **identyfikator FamilyId**. |Wszystkie pliki transkrypcji i ich elementy rodzinne w tej samej konwersacji mają ten sam **conversationId**. Obejmuje to następujące elementy:<br/><br/>  — Wszystkie wyodrębnione elementy i załączniki ze wszystkich transkrypcji, które mają ten sam **element ConversationId**. <br/> - Wszystkie transkrypcje dla tej samej konwersacji na czacie<br/> - Wszystkie kopie kopi poszczególnych transkrypcji<br/> - Transkrypcje z kolejnych kolekcji z tej samej konwersacji na czacie <br/><br/>  W Teams czatach grupowych i 1:1 konwersacjach grupowych możesz mieć wiele plików transkrypcji, z których każdy odpowiada różnym ramom czasowym w konwersacji. Ponieważ te pliki transkrypcji są z tej samej konwersacji z tymi samymi uczestnikami, mają ten **samid konwersacji**.|
|Standardowe, prywatne i udostępnione czaty na kanale    | Każdy wpis oraz wszystkie odpowiedzi i załączniki są zapisywane we własnej transkrypcie. Ten transkrypcja i wszystkie jej załączniki oraz wyodrębnione elementy mają ten sam **element FamilyId**.         |Każdy wpis, jego załączniki i wyodrębnione elementy mają unikatowy identyfikator **ConversationId**. Jeśli istnieją kolejne kolekcje lub nowe odpowiedzi z tego samego wpisu, transkrypcje różnicowe wynikające z tych kolekcji również będą mieć ten sam **conversationId**.|
||||

Kontrolka **Grupuj** na pasku poleceń zestawu recenzji umożliwia wyświetlanie Teams grupowanych według rodziny lub konwersacji.

![Kontrolka grupowania na pasku poleceń.](..\media\TeamsGroupControl.png)

- Wybierz **pozycję Grupuj załączniki** rodziny, aby Teams zawartość pogrupowane według rodziny. Każdy plik transkrypcji jest wyświetlany w wierszu na liście elementów zestawu recenzji. Załączniki są zagnieżdżone pod tym elementem.

- Wybierz **pozycję Grupuj Teams lub Yammer konwersacje**, aby Teams zawartość pogrupowane według konwersacji. Każda konwersacja jest wyświetlana w wierszu na liście elementów zestawu recenzji. Transkrypcje plików i załączników są zagnieżdżone w konwersacji najwyższego poziomu.

> [!NOTE]
> Załączniki w chmurze są grupowane z konwersacjami, w których się znajdują. To grupowanie jest realizowane przez przypisanie tej samej wartości **FamilyId** co plik transkrypcji wiadomości, do która go dołączono, i tego  samego samegoidu konwersacji, w których pojawiła się wiadomość. Oznacza to, że do zestawu recenzji można dodać wiele kopii załączników w chmurze, jeśli zostały dołączone do różnych konwersacji.

#### <a name="viewing-transcript-files-for-conversations"></a>Wyświetlanie plików transkrypcji dla konwersacji

Podczas wyświetlania plików transkrypcji w zestawie recenzji niektóre wiadomości są wyróżnione kolorem fioletowym. Wyróżnione wiadomości zależą od tego, którą kopię transkrypcyjną transkrypcji wyświetlasz. Na przykład na czacie 1:1 między użytkownikami User4 i User2 wiadomości opublikowane przez użytkownika User4 są wyróżniane kolorem fioletowym podczas wyświetlania transkrypcji zebranej ze skrzynki pocztowej użytkownika User4. Gdy wyświetlasz transkrypcję tej samej konwersacji użytkownika User2, wiadomości opublikowane przez użytkownika User2 są wyróżniane kolorem fioletowym. To wyróżnienie jest oparte na tym samym Teams klienta, gdzie wpisy użytkownika są wyróżniane kolorem fioletowym w kliencie Teams klienta.

Na poniższych zrzutach ekranu pokazano przykładową konwersację w kliencie Teams oraz plik transkrypcji tej samej konwersacji w zestawie recenzji. Purpurowe wyróżnienie w pliku transkrypcji wskazuje, że transkrypcja została zebrana ze skrzynki pocztowej użytkownika User2.

##### <a name="conversation-in-teams-client"></a>Konwersacja w Teams klienta

![Konwersacja pokazana w pliku transkrypcji w zestawie recenzji.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Konwersacja w pliku transkrypcji

![Ta sama konwersacja wyświetlana w Teams klienta.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Transkrypcja wątku konwersacji

Funkcja wątków konwersacji w nowym formacie sprawy w programie Advanced eDiscovery ułatwia identyfikowanie zawartości kontekstowej związanej z elementami, które mogą być istotne dla prowadzonego badania. Ta funkcja tworzy oddzielne widoki konwersacji, które obejmują wiadomości czatu poprzedzające i następujące po nich, są zgodne z zapytaniem wyszukiwania podczas kolekcji. Ta funkcja umożliwia wydajne i szybkie przeglądanie ukończonych konwersacji na czacie (nazywanych konwersacjami w wątkach *) w* Microsoft Teams. Jak wyjaśniono wcześniej, konwersacje na czacie są odtworzyć w plikach transkrypcji HTML, Advanced eDiscovery dodaje Teams do zestawu recenzji.

Oto logika używana przez program Advanced eDiscovery do dołączania dodatkowych wiadomości i plików transkrypcji odpowiedzi, które zapewniają kontekst wokół elementów odpowiada zapytaniu kolekcji (nazywanego elementami *odpowiedzi), które* było używane podczas gromadzenia Teams zawartości. Różne zachowania w wątkach są oparte na typach czatów i kwerendzie wyszukiwania używanej do zbierania elementów odpowiedzi. Istnieją dwa typowe scenariusze zbierania:

- Zapytania, które używają parametrów wyszukiwania, takich jak słowa kluczowe i pary właściwość:wartość

- Zapytania, które używają tylko zakresów dat

| Teams typ zawartości|Zapytania z parametrami wyszukiwania  |Zapytania z zakresami dat  |
|:---------|:---------|:---------|
|Teams czatach grupowych i 1:1   |Wiadomości opublikowane 12 godzin przed i 12 godzin po odpowiedziach są grupowane z elementem odpowiedzi w pojedynczym pliku transkrypcji.   |Wiadomości w oknie 24-godzinnym są grupowane w jednym pliku transkrypcji.|
|Standardowe, prywatne i udostępnione Teams kanałów    |Każdy wpis zawierający elementy odpowiedzi i wszystkie odpowiadające im odpowiedzi są grupowane w jednym pliku transkrypcji. |Każdy wpis zawierający elementy odpowiedzi i wszystkie odpowiadające im odpowiedzi są grupowane w jednym pliku transkrypcji.|
||||

### <a name="deduplication-of-teams-content"></a>Deduplication Teams zawartości

Na poniższej liście opisano działanie deduplikacji (i duplikacji) podczas gromadzenia Teams w zestawie recenzji.

- Każdy plik transkrypcji dodany do zestawu recenzji powinien być mapowaniem jeden-do-jednego na zawartość przechowywaną w lokalizacjach danych. Oznacza to Advanced eDiscovery nie są zbierane żadne Teams, które już zostały dodane do zestawu recenzji. Jeśli wiadomość czatu jest już zebrana w zestawie recenzji, Advanced eDiscovery nie dodaje tej samej wiadomości z tej samej lokalizacji danych do zestawu recenzji w kolejnych kolekcjach.

- W rozmowach grupowych (1:1) kopie wiadomości są przechowywane w skrzynce pocztowej każdego uczestnika konwersacji. Kopie tej samej konwersacji, które znajdują się w skrzynkach pocztowych różnych uczestników, są zbierane z różnymi metadanymi. W wyniku tego każde wystąpienie konwersacji jest traktowane jako unikatowe i jest przenoszone do zestawu recenzji w osobnych plikach transkrypcji. Jeśli zatem wszyscy uczestnicy czatu grupowego lub 1:1 zostaną dodani jako osoby do sprawy i zostaną uwzględnione w zakresie kolekcji, kopie każdej transkrypcji (w przypadku tej samej konwersacji) zostaną dodane do zestawu recenzji i pogrupowane razem z tym samym polem **konwersacji**. Każda z tych kopii jest skojarzona z odpowiadającym mu opiekunem. **Porada**: kolumna **Pośręce** na liście zestawu recenzji identyfikuje element do obsługi odpowiedniego pliku transkrypcji.

- W kolejnych kolekcjach elementów z tej samej konwersacji do zestawu recenzji jest dodawana i grupowana tylko zawartość różnicowa, która wcześniej nie była zbierana, z wcześniej zebranymi transkrypcjami z tej samej konwersacji. Oto przykład takiego zachowania:

   1. Kolekcja A zbiera wiadomości w konwersacji między użytkownikami Użytkownik1 i Użytkownik2 oraz dodaje zestaw recenzji.

   2. Kolekcja B zbiera wiadomości z tej samej konwersacji, ale od czasu uruchomienia kolekcji A istnieją nowe wiadomości między użytkownikami User1 i User2.

   3. Do zestawu recenzji są dodawane tylko nowe wiadomości z kolekcji B. Te wiadomości są dodawane do osobnego pliku transkrypcji, ale nowa transkrypcja jest grupowana z transkrypcjami z kolekcji A według tego samego **indeksu konwersacji**.

   To zachowanie dotyczy wszystkich typów Teams czatów.

### <a name="metadata-for-teams-content"></a>Metadane dla Teams zawartości

W dużych zestawach recenzji z tysiącami lub milionami elementów może być trudne zawężenie zakresu recenzji w celu Teams zawartości. Aby ułatwić skoncentrowanie się na zawartości Teams, istnieją właściwości metadanych specyficzne dla Teams zawartości. Za pomocą tych właściwości można organizować kolumny na liście recenzji oraz konfigurować [](review-set-search.md) filtry i kwerendy w celu zoptymalizowania przeglądania Teams zawartości. Te właściwości metadanych są również uwzględniane podczas eksportowania zawartości Teams z usługi Advanced eDiscovery, co ma ułatwić organizowanie i wyświetlanie zawartości po eksportowaniu lub za pomocą narzędzi zbierania elektronicznych materiałów dowodowych innych firm.

W poniższej tabeli opisano właściwości metadanych dla Teams zawartości.

|Właściwość Metadane  |Opis  |
|:---------|:---------|
|ContainsEditedMessage      | Wskazuje, czy plik transkrypcji zawiera edytowaną wiadomość. Edytowane wiadomości są identyfikowane podczas wyświetlania pliku transkrypcji.|
|ConversationId|Identyfikator GUID identyfikujący konwersację, z która jest skojarzona z elementem. Transkrypcje plików i załączników z tej samej konwersacji mają tę samą wartość dla tej właściwości.|
|Nazwa konwersacji     | Nazwa konwersacji, z która jest skojarzony plik transkrypcji lub załącznik. W Teams czatach grupowych i 1:1 wartość tej właściwości to upn wszystkich uczestników konwersacji. Na przykład `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams kanału (standardowy, prywatny i udostępniony) mają nazwę konwersacji w następującym formacie: `<Team name>,<Channel name>`.Na przykład `eDiscovery vNext, General`.          |
|ConversationType     | Wskazuje typ czatu zespołu. W Teams czatach grupowych i 1:1 wartość tej właściwości `Group`wynosi . W przypadku standardowych, prywatnych i udostępnionych czatów na kanale wartość to `Channel`.|
|Data | Sygnatura czasowa pierwszej wiadomości w pliku transkrypcji.|
|FamilyId|Identyfikator GUID identyfikujący plik transkrypcji dla konwersacji na czacie. Załączniki będą mieć tę samą wartość dla tej właściwości, co plik transkrypcji zawierający wiadomość, do których plik został dołączony.|
|FileClass     |Wskazuje ten typ zawartości. Elementy z Teams mają wartość `Conversation`. Natomiast Exchange e-mail mają wartość `Email`.|          |
|MessageKind     | Właściwość typu wiadomości. Teams zawartość ma wartość `microsoftteams , im`. |
|Adresaci     | Lista wszystkich użytkowników, którzy otrzymali wiadomość w ramach transkrypcji.|
|TeamsChannelName     | Nazwa Teams transkrypcji w kanale.|
|||

Aby uzyskać opisy Advanced eDiscovery właściwości metadanych dokumentu, zobacz [Pola metadanych](document-metadata-fields-in-Advanced-eDiscovery.md) dokumentu Advanced eDiscovery.

## <a name="export-teams-content"></a>Eksportowanie Teams zawartości

Po przejrzeniu i obliczaniu zawartości Teams w zestawie recenzji możesz wyeksportować pliki transkrypcji zawierające zawartość, która odpowiada analizie. Nie ma żadnych określonych ustawień eksportu dla Teams zawartości. Każdy plik transkrypcji jest eksportowany jako plik wiadomości HTML. Ten plik zawiera również ukryte tagi CDATA ze wszystkimi metadanymi dla poszczególnych wiadomości czatu. Podczas eksportowania zawartości metadanych są uwzględniane właściwości Teams poprzedniej sekcji.  

Do każdego pliku transkrypcji odwołuje się plik ładowania i może on być umieszczony przy użyciu ścieżki względnej w polu Export_native_path pliku ładowania. Transkrypcje plików znajdują się w folderze Konwersacje w głównym folderze eksportu.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Wskazówki przeglądania Teams w zestawie recenzji

Poniżej znajdują się porady i najlepsze rozwiązania dotyczące wyświetlania Teams w zestawie recenzji.

- Użyj **kontrolki Dostosuj kolumny** na pasku poleceń, aby dodać i uporządkować kolumny w celu zoptymalizowania przeglądania Teams zawartości.

  ![Strona wysuwana Edytuj kolumnę umożliwia dodawanie, usuwanie i organizowanie kolumn.](..\media\EditReviewSetColumns.png)

   Możesz dodawać i usuwać kolumny, które są przydatne Teams zawartości. Kolejność kolumn można także zmieniać, przeciągając je i upuszczając na **wysuwaną** stronę Edytowania kolumny. Można też sortować według kolumn w celu grupowania Teams zawartości z podobnymi wartościami w sortowanej kolumnie.

- Przydatne kolumny, które ułatwiają przeglądanie Teams to **: Szybki****,** Adresaci, **Typ pliku** **lub Rodzaj wiadomości**.

- Aby [szybko](review-set-search.md) wyświetlić Teams zawartości, użyj filtrów Teams właściwości związanych Teams zawartości. Istnieją filtry dla większości właściwości metadanych opisanych w poprzedniej sekcji.

## <a name="reference-guide"></a>Przewodnik

Oto krótki przewodnik dotyczący korzystania z programu Advanced eDiscovery dla Microsoft Teams. Ten przewodnik zawiera podsumowanie kluczy używania aplikacji Advanced eDiscovery zachowywania, zbierania, przeglądania i eksportowania zawartości z usługi Microsoft Teams.

![Miniatura przewodnika do reference for using Advanced eDiscovery for Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[Pobierz jako plik PDF](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
