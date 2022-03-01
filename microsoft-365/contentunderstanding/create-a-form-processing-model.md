---
title: Tworzenie modelu przetwarzania formularzy w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się, jak utworzyć model przetwarzania formularzy w aplikacji SharePoint Syntex.
ms.openlocfilehash: b6ccede1de62fbba0e111eb7d9d805b4998e9652
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015927"
---
# <a name="create-a-form-processing-model-in-microsoft-sharepoint-syntex"></a>Tworzenie modelu przetwarzania formularzy w aplikacji Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhN]  

</br>

Korzystanie [z aplikacji AI Builder](/ai-builder/overview) — funkcji w aplikacji Microsoft Power Apps — SharePoint Syntex użytkownicy mogą tworzyć [model](form-processing-overview.md) przetwarzania formularzy bezpośrednio z SharePoint dokumentów. 

Tworzenie modelu przetwarzania formularza obejmuje następujące kroki:

 - [Krok 1. Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md#step-1-create-a-form-processing-model)
 - [Krok 2. Dodawanie i analizowanie dokumentów](create-a-form-processing-model.md#step-2-add-and-analyze-documents)
 - [Krok 3. Oznaczanie pól i tabel](create-a-form-processing-model.md#step-3-tag-fields-and-tables)
 - [Krok 4. Szkolenie i publikowanie modelu](create-a-form-processing-model.md#step-4-train-and-publish-your-model)
 - [Krok 5. Używanie modelu](create-a-form-processing-model.md#step-5-use-your-model)

## <a name="requirements"></a>Wymagania

Model przetwarzania formularza można utworzyć tylko SharePoint bibliotekach dokumentów, dla których został włączony. Jeśli przetwarzanie formularzy jest włączone, można wyświetlić **konstruktora** automateAITworzenie  >  > **modelu** do przetwarzania formularzy w bibliotece dokumentów. Jeśli potrzebujesz włączonego przetwarzania w bibliotece dokumentów, musisz skontaktować się z administratorem SharePoint dokumentów.

 ![Zrzut ekranu przedstawiający model aplikacji AI Builder.](../media/content-understanding/create-ai-builder-model2.png)

## <a name="step-1-create-a-form-processing-model"></a>Krok 1. Tworzenie modelu przetwarzania formularzy

Pierwszym krokiem podczas tworzenia modelu przetwarzania formularzy jest nadanie modelowi nazwy, zdefiniowanie nowego typu zawartości i utworzenie dla niego nowego widoku biblioteki dokumentów.

1. W bibliotece dokumentów wybierz menu **Automatyzuj** , wybierz pozycję **Konstruktor AI**, a następnie wybierz pozycję **Utwórz model w celu przetwarzania formularzy**.

    ![Zrzut ekranu przedstawiający menu Automatyzuj i opcję Utwórz model do przetwarzania formularzy.](../media/content-understanding/create-ai-builder-model2.png)

2. W **panelu Tworzenie modelu do przetwarzania** formularzy w polu  Nazwa wpisz nazwę modelu (na przykład Zamówienia *zakupu*).

    ![Zrzut ekranu przedstawiający panel Tworzenie modelu do przetwarzania formularzy.](../media/content-understanding/new-form-model2.png) 

3. Teraz można automatycznie wyodrębniać i zapisywać informacje  z kolekcji plików strukturalnych o podobnym układzie — na przykład na fakturach lub dokumentach podatkowych — które znajdują się SharePoint bibliotece dokumentów. Pozwala to zredagować kilka modeli w jeden model i wyodrębnić informacje o określonych elementach tabeli.

   Nazwa kolekcji jest zapisywana w dedykowanej kolumnie w bibliotece dokumentów, w której jest stosowany model, co pozwala rozróżnić różne układy plików przetwarzane przez ten sam model.

   Ponadto wyodrębnione informacje o tabeli są zapisywane na określonej liście i skojarzone z przekazanym plikiem w celu łatwego przeglądania lub dodatkowego automatyzacji procesu biznesowego.

   Aby wyodrębnić informacje z tabeli do skojarzonej listy:<br><br>

     1. W sekcji **Wyodrębniaj informacje z tabel?** wybierz pozycję **Tak**.

      ![Zrzut ekranu przedstawiający sekcję Wyodrębnianie informacji z tabel na panelu Tworzenie modelu do przetwarzania formularzy.](../media/content-understanding/extract-info-from-tables.png) 

     2. W sekcji **Gdzie mamy zapisywać informacje o tabeli?**
 
        - Jeśli wybierzesz **opcję Nowa lista** (ustawienie domyślne), sugerowana nazwa zostanie automatycznie włączona w **polu Nowa nazwa** listy. Jeśli chcesz, możesz zmodyfikować nazwę. Jeśli chcesz wyświetlić listę w nawigacji witryny, zaznacz pole **wyboru Pokaż** w nawigacji witryny.

        - Jeśli **wybierzesz pozycję Istniejąca lista**, w **polu Wybrane listy** wybierz listę, której chcesz użyć.

4. Podczas tworzenia modelu przetwarzania formularzy jest tworzyć nowy SharePoint typu zawartości. Typ SharePoint reprezentuje kategorię dokumentów o wspólnych cechach i udostępnia kolekcję kolumn lub właściwości metadanych dla tej określonej zawartości. SharePoint zawartości są zarządzane za pośrednictwem centrum SharePoint administracyjnego.

   Aby zamapować ten model na istniejący typ zawartości w galerii typów SharePoint zawartości, wybierz pozycję **Ustawienia zaawansowane**.

    ![Zrzut ekranu przedstawiający ustawienia Zaawansowane w panelu Tworzenie modelu do przetwarzania formularzy.](../media/content-understanding/new-form-model-advanced-settings.png) 

   1. W **sekcji Typ zawartości** wybierz, czy chcesz utworzyć nowy typ zawartości, czy użyć istniejącego. 

   2. Aby użyć istniejącego typu zawartości, wybierz **pozycję Wybierz**, a następnie wybierz typ zawartości z listy.

   3. Model tworzy nowy widok dla wyodrębniowanych danych w bibliotece dokumentów. Jeśli nie chcesz, aby był to widok domyślny, w sekcji Widok biblioteki  dla tego modelu wyczyść pole wyboru Ustaw widok **jako** domyślny.

   4. Aby zastosować etykietę przechowywania do plików, **w sekcji** Etykieta przechowywania wybierz etykietę przechowywania, której chcesz użyć.

5. Wybierz pozycję **Utwórz**.

## <a name="step-2-add-and-analyze-documents"></a>Krok 2. Dodawanie i analizowanie dokumentów

Po utworzeniu nowego modelu przetwarzania formularzy przeglądarka otwiera nową stronę Power Apps przetwarzania formularzy aplikacji AI Builder. Na tej stronie możesz dodawać i analizować dokumenty przykładowe. 

> [!NOTE]
> Poszukasz przykładowych plików do użycia, zobacz wymagania dokumentu wejściowego [modelu przetwarzania formularza i porady dotyczące optymalizacji](/ai-builder/form-processing-model-requirements). 
 
1. Najpierw zdefiniuj pola i tabele, które chcesz wyodrębnić w modelu, na **stronie Wybieranie informacji do wyodrębnienia** . Aby uzyskać szczegółowy opis kroków, [zobacz Definiowanie pól i tabel do wyodrębnienia](/ai-builder/create-form-processing-model#define-fields-and-tables-to-extract). 

2.  Możesz utworzyć tyle kolekcji układów dokumentów, ile modelu chcesz przetworzyć. Aby uzyskać szczegółowy opis kroków, [zobacz Grupowanie dokumentów według kolekcji](/ai-builder/create-form-processing-model#group-documents-by-collections). 

3. Po utworzeniu kolekcji i dodaniu przykładowych plików do każdej z nich, AI Builder sprawdzi przekazane dokumenty w celu wykrycia pól i tabel. Zazwyczaj trwa to kilka minut. Po zakończeniu analizy możesz przystąpić do otagowania dokumentów.

## <a name="step-3-tag-fields-and-tables"></a>Krok 3. Oznaczanie pól i tabel

Musisz otagować dokumenty, aby nauczyć model rozumienia pól i danych tabel, które chcesz wyodrębnić. Aby uzyskać szczegółowy opis kroków, zobacz [Oznaczanie dokumentów](/ai-builder/create-form-processing-model#tag-documents).

## <a name="step-4-train-and-publish-your-model"></a>Krok 4. Szkolenie i publikowanie modelu

1. Po utworzeniu i przygotowaniu modelu możesz opublikować go i używać go w SharePoint. Aby uzyskać szczegółowe instrukcje, [zobacz Szkolenie i publikowanie modelu przetwarzania formularzy](/ai-builder/form-processing-train). 

2. Po opublikowaniu modelu wybierz pozycję **Użyj modelu**, a następnie wybierz pozycję **Utwórz przepływ**. Powoduje to utworzenie przepływu Power Automate który można uruchomić w bibliotece SharePoint dokumentów i wyodrębnia pola, które zostały zidentyfikowane w modelu.

    ![Zrzut ekranu przedstawiający konstruktora AI z panelem Tworzenie przepływu.](../media/content-understanding/ai-builder-create-a-flow.png)
 
3. Po ukończeniu zobaczysz komunikat: Przepływ *został utworzony pomyślnie*.

    ![Zrzut ekranu przedstawiający pomyślnie utworzony przepływ w aplikacji AI Builder.](../media/content-understanding/ai-builder-flow-created.png)

4. Wybierz przycisk **Przejdź SharePoint**, aby wyświetlić bibliotekę dokumentów zaktualizowaną o model.

## <a name="step-5-use-your-model"></a>Krok 5. Używanie modelu

1. W widoku modelu biblioteki dokumentów zaznaczone pola są teraz wyświetlane jako kolumny.

    ![Zastosowany model biblioteki dokumentów.](../media/content-understanding/doc-lib-view.png)

2. Zwróć uwagę, że link do informacji obok **notatek** Dokumenty oznacza, że do tej biblioteki dokumentów został zastosowany model przetwarzania formularzy.

    ![Przycisk Informacje.](../media/content-understanding/info-button.png)  

3. Upload plików do biblioteki dokumentów. Wszystkie pliki, które model identyfikuje jako typ zawartości, to pliki w widoku i wyodrębnione dane w kolumnach.

    ![Gotowe.](../media/content-understanding/doc-lib-done.png) 

> [!NOTE]
> Jeśli do tej samej biblioteki zastosowano niestandardowy model przetwarzania formularza i model rozumienia dokumentu, plik zostanie sklasyfikowany przy użyciu modelu rozumienia dokumentu i dowolnych przeszkolonych wyodrębniaczy dla tego modelu. Jeśli istnieją puste kolumny zgodne z modelem przetwarzania formularzy, kolumny zostaną wypełnione przy użyciu tych wyodrębnianych wartości.

### <a name="use-flows-to-extract-information"></a>Wyodrębnianie informacji za pomocą przepływów

Dostępne są dwa przepływy przetwarzania wybranego pliku lub partii plików w bibliotece, w której zastosowano model przetwarzania formularzy.

- **Wyodrębnianie informacji z obrazu lub pliku PDF** za pomocą modelu przetwarzania formularza — służy do wyodrębniania tekstu z wybranego obrazu lub pliku PDF przez uruchomienie modelu przetwarzania formularzy. Obsługuje pojedynczo wybrany plik i obsługuje tylko pliki PDF oraz pliki obrazów (PNG, JPG i JPEG). Aby uruchomić przepływ, wybierz plik, a następnie wybierz **pozycję AutomateExtract** >  **informacje**.

    ![Zrzut ekranu przedstawiający menu Automatyzuj z wyróżnionem poleceniem Wyodrębnij informacje.](../media/content-understanding/automate-extract-info.png)  

- **Wyodrębnianie informacji z plików za pomocą modelu przetwarzania formularzy** — służy do odczytywania i wyodrębniania informacji z partii plików za pomocą modeli przetwarzania formularzy. Przetwarza do 5000 SharePoint jednocześnie. Po uruchomieniu tego przepływu możesz ustawić pewne parametry. Można:

    - Określ, czy mają być dołączane wcześniej przetwarzane pliki (domyślnie nie są dołączane wcześniej przetwarzane pliki).
    - Wybierz liczbę plików, które chcesz przetworzyć (wartość domyślna to 100 plików).
    - Określ kolejność przetwarzania plików (dostępne opcje to identyfikator pliku, nazwa pliku, godzina utworzenia pliku lub godzina ostatniej modyfikacji).
    - Określ sposób sortowania kolejności (rosnąco lub malejąco).

    ![Zrzut ekranu przedstawiający panel Uruchom przepływ z wyróżniona opcjami parametrów.](../media/content-understanding/run-flow-panel.png)  

### <a name="classification-date-field"></a>Pole Data klasyfikacji

W przypadku SharePoint Syntex przetwarzania formularza (lub modelu rozumienia dokumentu) do biblioteki dokumentów pole Data klasyfikacji jest uwzględniane  w schemacie biblioteki. Domyślnie to pole jest puste. Jednak podczas przetwarzania i klasyfikowania dokumentów za pomocą modelu to pole jest aktualizowane za pomocą sygnatury daty i czasu wykonania. 

Gdy model jest opatrzony sygnaturą z datą klasyfikacji **, możesz** użyć funkcji Wyślij wiadomość **e-mail**, gdy program SharePoint Syntex przetwarza przepływ pliku w celu powiadomienia użytkowników, że nowy plik został przetworzony i sklasyfikowany przez model w bibliotece SharePoint dokumentów.

Aby uruchomić przepływ:

1. Wybierz plik, a następnie **wybierz pozycję** Integracja  > **Power Automate** >  **Tworzenie przepływu**.

2. Na **panelu Tworzenie przepływu** wybierz pozycję Wyślij wiadomość e-mail, **SharePoint Syntex przetwarza plik**.

    ![Zrzut ekranu przedstawiający opcję Utwórz panel przepływu i przepływ.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Zobacz też
  
[Power Automate dokumentacji](/power-automate/)

[Szkolenie: Ulepszanie wydajności biznesowej za pomocą aplikacji AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)