---
title: Oznaczanie dokumentów w zestawie recenzji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Otagowanie dokumentów w zestawie recenzji pomaga usunąć niepotrzebną zawartość i zidentyfikować odpowiednią zawartość w Advanced eDiscovery przypadku.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 43b0bf42bcd94f0bc3ade169ee5b41ee33dcbc5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984947"
---
# <a name="tag-documents-in-a-review-set-in-advanced-ediscovery"></a>Oznaczanie dokumentów w zestawie recenzji w programie Advanced eDiscovery

Organizowanie zawartości w zestawie recenzji jest ważne do ukończenia różnych przepływów pracy w procesie zbierania elektronicznych materiałów dowodowych. Obejmuje to:

- Obliczanie niepotrzebnej zawartości

- Identyfikowanie odpowiedniej zawartości

- Identyfikowanie zawartości, która musi zostać przejmowana przez eksperta lub pełnomocnika

Gdy eksperci, prawnicy lub inni użytkownicy przeglądają zawartość zestawu recenzji, ich opinie dotyczące tej zawartości można chwycić za pomocą znaczników. Jeśli na przykład celem jest zmierzowanie niepotrzebnej zawartości, użytkownik może otagować dokumenty za pomocą tagu, takiego jak "nie odpowiada". Po przejrzeniu i oznaczeniu zawartości można utworzyć wyszukiwanie zestawu recenzji w celu wykluczenia z witryny wszelkiej zawartości oznaczonej jako nieaktywna. Ten proces eliminuje nie odpowiadanie zawartości z kolejnych kroków przepływu pracy zbierania elektronicznych materiałów dowodowych. Panel otagowania w zestawie recenzji można dostosować do każdej sprawy, tak aby tagi obsługiły przepływ pracy przeglądu zamierzony w przypadku sprawy.

> [!NOTE]
> Zakres tagów jest Advanced eDiscovery przypadku. Oznacza to, że w przypadku sprawy może być tylko jeden zestaw tagów, za pomocą których recenzentzy mogą oznaczać dokumenty zestawu recenzji. W tym samym przypadku nie można skonfigurować innego zestawu tagów do używania w różnych zestawach recenzji.

## <a name="tag-types"></a>Typy tagów

Advanced eDiscovery udostępnia dwa typy tagów:

- **Tagi wyboru pojedynczego**: Ogranicza recenzentów do wybierania pojedynczego tagu w grupie. Te typy tagów mogą być przydatne w celu zagwarantowania, że recenzentzy nie wybierają tagów powodującego konflikt, takich jak "czas odpowiedzi" i "nie odpowiada". Tagi wyboru pojedynczego są wyświetlane jako przyciski radiowe.

- **Tagi wyboru wielokrotnego** wyboru: Zezwalaj na zaznaczanie wielu tagów w grupie przez recenzowanie. Tagi tego typu są wyświetlane jako pola wyboru.

## <a name="tag-structure"></a>Struktura znaczników

Oprócz typów tagów można zmienić strukturę zorganizowania tagów w panelu tagów, aby tagi są bardziej intuicyjne. Tagi są pogrupowane według sekcji. Wyszukiwanie zestawu recenzji umożliwia wyszukiwanie według tagu i sekcji tagów. Oznacza to, że możesz utworzyć wyszukiwanie zestawu recenzji w celu pobrania dokumentów oznaczonych dowolnym tagiem w sekcji.

![Oznacz sekcje w panelu znaczników.](../media/TagTypes.png)

Tagi można dodatkowo organizować, zagnieżdżając je w sekcji. Jeśli na przykład celem jest zidentyfikowanie zawartości z uprawnieniami i tagowanie jej, można użyć zagnieżdżania, aby było jasne, że recenzent może otagować dokument jako "Uprawnienia", a następnie wybrać typ uprawnień, sprawdzając odpowiedni tag zagnieżdżony.

![Zagnieżdżone tagi w sekcji tagów.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Tworzenie i stosowanie tagów

Oznaczanie elementów w zestawach recenzji jest procesem dwuetapowym. Pierwszym krokiem jest utworzenie tagów, które zostaną następnie zastosowane w celu przejrzenia zestawu elementów. Po utworzeniu tagów ty i inni recenzentzy możecie zastosować je do elementów w zestawie recenzji. Jak już wyjaśniono, Advanced eDiscovery przypadku może mieć tylko jeden zestaw tagów, których recenzentzy mogą używać do oznaczania elementów zestawu recenzji.

### <a name="create-tags"></a>Tworzenie tagów

Przed zastosowaniem tagów do elementów w zestawie recenzji musisz utworzyć strukturę tagów.

1. Otwórz zestaw recenzji, przejdź do paska poleceń i wybierz pozycję **Oznakuj pliki**.

2. Na **wysuwana strona Pliki** znaczników kliknij pozycję **Utwórz/edytuj tagi**.

   ![Na wysuwanych stronie kliknij pozycję Utwórz/edytuj tagi.](../media/CreateAeDTags1.png)

3. Na stronie **Tagi** wybierz pozycję **Dodaj sekcję**.

4. Wpisz tytuł grupy tagów i opcjonalny opis, a następnie kliknij **pozycjęZapis**.

5. Wybierz menu rozwijane z trzema kropkami obok tytułu grupy tagów i kliknij pole wyboru **Dodaj** lub **przycisk Dodaj opcję**.

6. Wpisz nazwę i opis pola wyboru lub przycisku opcji.

7. Powtórz tę procedurę, aby utworzyć nowe sekcje tagów, opcje znaczników i pola wyboru. Poniższy zrzut ekranu przedstawia na przykład grupę tagów o nazwie **Recenzja**, która zawiera  pola wyboru Odpowiadanie **i Nie** odpowiadanie.

   ![Konfigurowanie struktury tagów.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Stosowanie tagów

Po skonfigurowaniu struktury tagów recenzentzy mogą stosować tagi do elementów w zestawie recenzji, konfigurując ustawienia tagów.

1. Na pasku poleceń zestawu recenzji wybierz pozycję **Otaguj** pliki, aby wyświetlić wysuwaną stronę Tagowanie plików (nazywaną również  *panelem tagowania*).

   ![Kliknij pozycję Otaguj pliki na pasku poleceń, aby otworzyć panel tagowania.](../media/TagFilesFlyoutPage.png)

2. Na stronie **wysuwu** Pliki znaczników możesz ustawić następujące opcje w celu skonfigurowania sposobu tagowania elementów wyświetlanych w zestawie recenzji. Filtry lub zapytania filtru stosowane obecnie do zestawu recenzji określają, które elementy są wyświetlane, a zatem elementy, do których można stosować tagi. Aby uzyskać więcej informacji, zobacz [Wykonywanie zapytań i filtrowanie zawartości w zestawie recenzji](review-set-search.md).

   - **Wybierz zaznaczenie**. Wybierz jedną z następujących opcji, aby określić zakres elementów, do których mają być stosowane tagi.

      - **Oznacz zaznaczone elementy**: ta opcja powoduje zastosowanie tagów do wybranych elementów. Możesz wybrać elementy przed uruchomieniem panelu otagowania lub po nim. Ta opcja powoduje wyświetlenie (w czasie rzeczywistym) liczby zaznaczonych elementów, które zostaną otagowane.

      - **Oznacz wszystkie elementy na liście**: ta opcja powoduje zastosowanie tagów do wszystkich elementów wyświetlanych w zestawie recenzji. Ta opcja wyświetla łączną liczbę elementów, które będą otagowane.

   - **Rozszerzanie zaznaczenia**: Za pomocą następujących opcji można oznaczać dodatkowe elementy, które są powiązane z elementami oznakowanych w zestawie recenzji.

      - **Uwzględnij skojarzone elementy rodziny**: ta opcja powoduje zastosowanie tego samego tagu do skojarzonych elementów rodzinnych otagowanych elementów.  *Elementy rodziny* to elementy, które mają taką samą wartość właściwości metadanych **FamilyId** . Na przykład dokument dołączony do wiadomości e-mail ma ten sam adres **FamilyId** co wiadomość e-mail. Jeśli w tym przykładzie jest zaznaczona ta opcja, wiadomość e-mail i dokument są otagowane, mimo że dokument może nie zostać uwzględniony na liście elementów zestawu recenzji.

      - **Uwzględnij skojarzone elementy** konwersacji: ta opcja powoduje zastosowanie tego samego tagu do wszystkich elementów, które znajdują się w tym samym Teams lub Yammer co otagowane elementy. *Elementy konwersacji* to elementy, które mają taką samą wartość właściwości metadanych **ConversationId** . Wszystkie wiadomości, wpisy i odpowiedni plik transkrypcji konwersacji mają ten **samid konwersacji**. Jeśli ta opcja jest zaznaczona, oznacza to, że wszystkie elementy tej samej konwersacji (i plik transkrypcji) są tagowane, mimo że niektóre z tych elementów konwersacji mogą nie być uwzględnione na liście elementów zestawu recenzji. Aby uzyskać więcej informacji na temat elementów konwersacji, zobacz sekcję "Grupowanie" w te Advanced eDiscovery [przepływu pracy dla zawartości w programie Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#grouping).

      - **Brak**: ta opcja nie powoduje zastosowania tagów do elementów rodzinnych ani do konwersacji. Powoduje ono zastosowanie tagów tylko do zaznaczonych elementów lub do wszystkich elementów na liście zestawu recenzji.

   > [!NOTE]
   > Uwzględnienie skojarzonych elementów rodziny lub konwersacji nie spowoduje zmiany liczby elementów wyświetlanych w opcjach **Oznacz zaznaczone** elementy lub **Oznacz wszystkie elementy w opcjach** listy. Oznacza to, że liczba skojarzonych elementów, które zostaną otagowane, nie jest wyświetlana.

   - **Przypisz tagi**: w tej sekcji są wyświetlane tagi (uporządkowane według grup tagów), które można stosować do dokumentów. W jednej grupie tagów można zastosować tylko jeden tag wyboru pojedynczego (oznaczony za pomocą przycisku radiowego). Można jednak zastosować wiele tagów wielokrotnego wyboru (które są oznaczone polem wyboru).

3. Kliknij **pozycję Zastosuj tagi** , aby zastosować tagi w zależności od ustawień.

   Dla **każdej grupy** tagów w panelu tagów zostanie wyświetlony komunikat o stanie Stosowania znaczników wskazujący, że zadanie tagowania zostało uruchomione. Tagi dla każdej grupy tagów w sekcji **Przypisywanie tagów** są wyszańne do czasu ukończenia zadania.

> [!TIP]
> Jeśli jesteś w trakcie konfigurowania ustawień w panelu tagów, ale chcesz zacząć od początku, kliknij pozycję **Resetuj** przypisanie tagu, aby wyczyścić bieżące ustawienie. Ta kontrolka nie dotyczy elementów, które są już oznakowane, ani nie zmienia ani nie usuwa tagów z wcześniej otagowanych elementów.  

#### <a name="monitor-tagging-jobs"></a>Monitorowanie zadań otagowania

Po oznaczeniu dużej liczby elementów (lub wybraniu opcji **Oznacz** wszystkie elementy na liście) jest tworzone zadanie Otagowanie dokumentów. Stan tego zadania można wyświetlić **na karcie Zadania** w tym przypadku. Ułatwia to śledzenie dużych zadań tagowania, których ukończenie może zająć dużo czasu. W niektórych przypadkach zadanie tagowania może być ukończone, ale w panelu otagowania nadal jest wyświetlany komunikat o stanie stosowania tagów. Aby zaktualizować stan otagowania zadań, kliknij pozycję **Odśwież** na pasku poleceń zestawu recenzji.

## <a name="removing-tags"></a>Usuwanie tagów

Możesz usuwać tagi z elementów w zestawie recenzji. Nie można jednak usunąć tagu jednorazowego wyboru, który został zastosowany do elementu zestawu recenzji. Tag z pojedynczym wyborem można zmienić tylko na inny tag z pojedynczym wyborem w obrębie tej samej grupy tagów.

Aby usunąć tag:

1. Zaznacz elementy, z których chcesz usunąć tag.

2. Kliknij **pozycję Otaguj** pliki, aby wyświetlić panel tagów.

3. W **obszarze Przypisywanie** tagów usuń jego zaznaczenie, a następnie kliknij pozycję **Zastosuj tagi**.

Możesz również użyć poprzedniej procedury, aby zmienić tag zastosowany do wybranych elementów. Po odznaczeniu bieżącego tagu możesz wybrać inny.
