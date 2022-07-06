---
title: Taguj dokumenty w zestawie do przeglądu
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Tagowanie dokumentów w zestawie przeglądów pomaga usunąć niepotrzebną zawartość i zidentyfikować odpowiednią zawartość w przypadku zbierania elektronicznych materiałów dowodowych (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 2cd1243f520be21cf27c810a5f2dc2e4a033a33f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623744"
---
# <a name="tag-documents-in-a-review-set-in-ediscovery-premium"></a>Tagowanie dokumentów w zestawie przeglądów w usłudze eDiscovery (Premium)

Organizowanie zawartości w zestawie przeglądów jest ważne, aby ukończyć różne przepływy pracy w procesie zbierania elektronicznych materiałów dowodowych. Obejmuje to:

- Ubój niepotrzebnej zawartości

- Identyfikowanie odpowiedniej zawartości

- Identyfikowanie zawartości, która musi zostać zweryfikowana przez eksperta lub adwokata

Gdy eksperci, adwokaci lub inni użytkownicy przeglądają zawartość w zestawie przeglądów, ich opinie dotyczące zawartości mogą być przechwytywane przy użyciu tagów. Jeśli na przykład celem jest usunięcie niepotrzebnej zawartości, użytkownik może oznaczyć dokumenty tagiem, takim jak "nie odpowiada". Po przejrzeniu i otagowaniu zawartości można utworzyć wyszukiwanie zestawu przeglądów, aby wykluczyć dowolną zawartość oznaczoną jako "niesponsywna". Ten proces eliminuje niesponsywną zawartość z następnych kroków w przepływie pracy zbierania elektronicznych materiałów dowodowych. Panel tagowania w zestawie przeglądów można dostosować dla każdego przypadku, aby tagi obsługiwały zamierzony przepływ pracy przeglądu dla danego przypadku.

> [!NOTE]
> Zakres tagów to przypadek zbierania elektronicznych materiałów dowodowych (Premium). Oznacza to, że przypadek może mieć tylko jeden zestaw tagów, których recenzenci mogą używać do tagowania dokumentów zestawu przeglądów. W tym samym przypadku nie można skonfigurować innego zestawu tagów do użycia w różnych zestawach przeglądów.

## <a name="tag-types"></a>Typy tagów

Funkcja zbierania elektronicznych materiałów dowodowych (Premium) udostępnia dwa typy tagów:

- **Tagi pojedynczego wyboru**: ogranicza recenzentów do wybierania pojedynczego tagu w grupie. Te typy tagów mogą być przydatne, aby upewnić się, że recenzenci nie wybierają tagów powodujących konflikt, takich jak "responsive" i "non-responsive". Tagi pojedynczego wyboru są wyświetlane jako przyciski radiowe.

- **Tagi wielokrotnego wyboru**: zezwalaj przeglądom na wybieranie wielu tagów w grupie. Te typy tagów są wyświetlane jako pola wyboru.

## <a name="tag-structure"></a>Struktura tagów

Oprócz typów tagów struktura sposobu organizowania tagów w panelu tagów może służyć do bardziej intuicyjnego tagowania dokumentów. Tagi są grupowane według sekcji. Wyszukiwanie zestawu przeglądów obsługuje możliwość wyszukiwania według tagów i według sekcji tagów. Oznacza to, że możesz utworzyć wyszukiwanie zestawu przeglądów w celu pobrania dokumentów oznaczonych dowolnym tagiem w sekcji.

![Sekcje tagów w panelu tagów.](../media/TagTypes.png)

Tagi można dodatkowo organizować, zagnieżdżając je w sekcji. Jeśli na przykład celem jest identyfikowanie i oznaczanie zawartości uprzywilejowanej, można użyć zagnieżdżenia, aby wyjaśnić, że recenzent może oznaczyć dokument jako "Uprzywilejowany" i wybrać typ uprawnień, sprawdzając odpowiedni zagnieżdżony tag.

![Zagnieżdżone tagi w sekcji tagów.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Tworzenie i stosowanie tagów

Tagowanie elementów w zestawach przeglądów jest procesem dwuetapowym. Pierwszym krokiem jest utworzenie tagów, które są następnie stosowane do przeglądania ustawionych elementów. Po utworzeniu tagów ty i inni recenzenci możesz zastosować je do elementów w zestawie przeglądów. Jak wyjaśniono wcześniej, przypadek zbierania elektronicznych materiałów dowodowych (Premium) może mieć tylko jeden zestaw tagów, których recenzenci mogą używać do tagowania elementów zestawu przeglądów.

### <a name="create-tags"></a>Tworzenie tagów

Przed zastosowaniem tagów do elementów w zestawie przeglądów należy utworzyć strukturę tagów.

1. Otwórz zestaw przeglądów, przejdź do paska poleceń i wybierz pozycję **Taguj pliki**.

2. Na stronie Wysuwane **pliki tagów** kliknij pozycję **Utwórz/edytuj tagi**.

   ![Kliknij pozycję Utwórz/edytuj tagi na stronie wysuwanej.](../media/CreateAeDTags1.png)

3. Na stronie **Tagi** wybierz pozycję **Dodaj sekcję**.

4. Wpisz tytuł grupy tagów i opcjonalny opis, a następnie kliknij przycisk **Zapisz**.

5. Wybierz menu rozwijane z potrójną kropką obok tytułu grupy tagów, a następnie kliknij **pozycję Dodaj pole wyboru** lub **przycisk Dodaj opcję**.

6. Wpisz nazwę i opis dla pola wyboru lub przycisku opcji.

7. Powtórz ten proces, aby utworzyć nowe sekcje tagów, opcje tagów i pola wyboru. Na przykład poniższy zrzut ekranu przedstawia grupę tagów o nazwie **Review**, która składa się z pól wyboru **Responsive** i **Not-responsive** .

   ![Skonfiguruj strukturę tagów.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Stosowanie tagów

Dzięki strukturze tagów recenzenci mogą stosować tagi do elementów w zestawie przeglądów, konfigurując ustawienia tagowania.

1. Na pasku poleceń zestawu przeglądów wybierz pozycję **Taguj pliki** , aby wyświetlić stronę wysuwaną **Pliki tagów** (nazywaną również *panelem tagowania*).

   ![Kliknij pozycję Taguj pliki na pasku poleceń, aby otworzyć panel tagowania.](../media/TagFilesFlyoutPage.png)

2. Na stronie Wysuwane **pliki tagów** można ustawić następujące opcje, aby skonfigurować sposób tagowania elementów wyświetlanych w zestawie przeglądów. Filtry lub zapytania filtrów stosowane obecnie do zestawu przeglądów określają, które elementy są wyświetlane, a zatem elementy, do których można zastosować tagi. Aby uzyskać więcej informacji, zobacz [Wykonywanie zapytań i filtrowanie zawartości w zestawie przeglądów](review-set-search.md).

   - **Wybierz opcję zaznaczenia**. Wybierz jedną z następujących opcji, aby określić zakres elementów do zastosowania tagów.

      - **Tagowanie wybranych elementów**: ta opcja stosuje tagi do wybranych elementów. Możesz wybrać elementy przed uruchomieniem panelu tagowania lub po jego uruchomieniu. Ta opcja wyświetla (w czasie rzeczywistym) liczbę wybranych elementów, które zostaną oznaczone tagiem.

      - **Otaguj wszystkie elementy na liście**: ta opcja stosuje tagi do wszystkich elementów wyświetlanych w zestawie przeglądów. Ta opcja wyświetla całkowitą liczbę elementów, które zostaną oznaczone tagiem.

   - **Rozwiń zaznaczenie**: Użyj następujących opcji, aby oznaczyć dodatkowe elementy powiązane z oznakowanymi elementami w zestawie przeglądów.

      - **Dołącz skojarzone elementy rodzinne**: ta opcja stosuje ten sam tag do skojarzonych elementów rodziny elementów, które są oznaczone tagiem.  *Elementy rodziny* to elementy, które mają tę samą wartość właściwości metadanych **FamilyId** . Na przykład dokument dołączony do wiadomości e-mail udostępnia ten sam identyfikator **FamilyId** co wiadomość e-mail. Jeśli więc ta opcja zostanie wybrana w tym przykładzie, wiadomość e-mail i dokument zostaną oznaczone tagiem, mimo że dokument może nie zostać uwzględniony na liście elementów zestawu przeglądów.

      - **Dołącz skojarzone elementy konwersacji**: ta opcja stosuje ten sam tag do wszystkich elementów, które znajdują się w tej samej konwersacji usługi Teams lub Yammer, co elementy oznaczone tagiem. *Elementy konwersacji* to elementy, które mają tę samą wartość właściwości metadanych **ConversationId** . Wszystkie komunikaty, wpisy i odpowiedni plik transkrypcji konwersacji mają ten sam **identyfikator Konwersacji**. Jeśli ta opcja jest zaznaczona, wszystkie elementy w tym samym pliku konwersacji (i pliku transkrypcji) są oznaczane tagiem, mimo że niektóre z tych elementów konwersacji mogą nie zostać uwzględnione na liście elementów zestawu przeglądów. Aby uzyskać więcej informacji na temat elementów konwersacji, zobacz sekcję "Grupowanie" w [przepływie pracy zbierania elektronicznych materiałów dowodowych (Premium) dla zawartości w usłudze Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#grouping).

      - **Brak**: ta opcja nie stosuje tagów do elementów rodziny ani elementów konwersacji. Stosuje tagi tylko do elementów, które są zaznaczone lub do wszystkich elementów na liście zestawów przeglądów.

   > [!NOTE]
   > Uwzględnienie skojarzonych elementów rodziny lub konwersacji nie spowoduje zmiany liczby elementów wyświetlanych w obszarze **Tagowanie wybranych elementów** ani **Tagowanie wszystkich elementów na liście** . Innymi słowy, liczba skojarzonych elementów, które zostaną oznaczone, nie jest wyświetlana.

   - **Przypisz tagi**: W tej sekcji są wyświetlane tagi (uporządkowane według grup tagów), które można zastosować do dokumentów. Można zastosować tylko jeden tag jednego wyboru (identyfikowany za pomocą przycisku radiowego) dla grupy tagów. Można jednak zastosować wiele tagów wielokrotnego wyboru (które są identyfikowane przez pole wyboru).

3. Kliknij **pozycję Zastosuj tagi** , aby zastosować tagi na podstawie ustawień.

   Komunikat **o stanie Stosowanie tagów** jest wyświetlany dla każdej grupy tagów na panelu tagowania, aby wskazać, że zadanie tagowania zostało uruchomione. Tagi dla każdej grupy **tagów w sekcji Przypisywanie tagów** są wyszarzone do momentu ukończenia zadania.

> [!TIP]
> Jeśli konfigurujesz ustawienia na panelu tagowania, ale chcesz zacząć od nowa, kliknij przycisk **Resetuj przypisanie tagu** , aby wyczyścić bieżące ustawienie. Ta kontrolka nie ma zastosowania do elementów, które zostały już oznakowane, i nie zmienia ani nie usuwa tagów z wcześniej oznakowanych elementów.  

#### <a name="monitor-tagging-jobs"></a>Monitorowanie zadań tagowania

Po otagowaniu dużej liczby elementów (lub wybraniu opcji **Taguj wszystkie elementy na liście**) zostanie utworzone zadanie **Tagowanie dokumentów** . Stan tego zadania można wyświetlić na karcie **Zadania** w przypadku. Ułatwia to śledzenie dużych zadań tagowania, które mogą zająć dużo czasu. W niektórych przypadkach zadanie tagowania może zostać ukończone, ale komunikat **o stanie Stosowanie tagów** na panelu tagowania jest nadal wyświetlany. Aby zaktualizować stan zadań tagowania, kliknij przycisk **Odśwież** na pasku poleceń zestawu przeglądów.

## <a name="removing-tags"></a>Usuwanie tagów

Tagi z elementów można usunąć w zestawie przeglądów. Nie można jednak usunąć tagu pojedynczego wyboru, który został zastosowany do elementu zestawu przeglądów. Tag pojedynczego wyboru można zmienić tylko na inny tag pojedynczego wyboru w tej samej grupie tagów.

Aby usunąć tag:

1. Wybierz elementy, z które chcesz usunąć tag.

2. Kliknij **pozycję Taguj pliki** , aby wyświetlić panel tagowania.

3. W obszarze **Przypisywanie tagów** usuń zaznaczenie tagu, a następnie kliknij pozycję **Zastosuj tagi**.

Możesz również użyć poprzedniej procedury, aby zmienić tag zastosowany do wybranych elementów. Po usunięciu zaznaczenia bieżącego tagu możesz wybrać inny.
