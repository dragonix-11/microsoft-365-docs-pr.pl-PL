---
title: Użyj wstępnie utworzonego modelu, aby wyodrębnić informacje z faktur lub paragonów w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak utworzyć i skonfigurować wstępnie utworzony model w SharePoint Syntex.
ms.openlocfilehash: f3b262ca94e0bfc6886a2ce84ae614569c584bf1
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738436"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-sharepoint-syntex"></a>Użyj wstępnie utworzonego modelu, aby wyodrębnić informacje z faktur lub paragonów w usłudze Microsoft SharePoint Syntex

Wstępnie utworzone modele są wstępnie wytrenowane do rozpoznawania dokumentów i informacji strukturalnych w dokumentach. Zamiast tworzyć nowy model niestandardowy od podstaw, można iterować na istniejącym wstępnie wytrenowanym modelu w celu dodania konkretnych pól odpowiadających potrzebom organizacji. 

Obecnie dostępne są dwa wstępnie utworzone modele: faktura i paragon.

- *Wstępnie utworzony model faktury* analizuje i wyodrębnia kluczowe informacje z faktur sprzedaży. Interfejs API analizuje faktury w różnych formatach i [wyodrębnia kluczowe informacje o fakturze](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) , takie jak nazwa klienta, adres rozliczeniowy, data ukończenia i należna kwota.

- *Wstępnie utworzony model paragonu* analizuje i wyodrębnia kluczowe informacje z paragonów sprzedaży. Interfejs API analizuje drukowane i odręczne potwierdzenia oraz [wyodrębnia informacje dotyczące paragonu klucza](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) , takie jak nazwa sprzedawcy, numer telefonu sprzedawcy, data transakcji, podatek i suma transakcji.

Dodatkowe wstępnie utworzone modele będą dostępne w przyszłych wersjach.

## <a name="create-a-prebuilt-model"></a>Tworzenie wstępnie utworzonego modelu

Wykonaj następujące kroki, aby utworzyć wstępnie utworzony model do klasyfikowania dokumentów w SharePoint Syntex.

1. Na stronie **Modele** wybierz **pozycję Utwórz model**.

    ![Zrzut ekranu przedstawiający stronę Modele z przyciskiem Utwórz model.](../media/content-understanding/prebuilt-create-model-button.png) 

2. Na panelu **Tworzenie modelu** w polu **Nazwa** wpisz nazwę modelu.

    ![Zrzut ekranu przedstawiający panel Nowy model zrozumienia dokumentu przedstawiający dostępne typy modeli.](../media/content-understanding/prebuilt-create-panel.png) 

3. W sekcji **Typ modelu** wybierz jeden ze wstępnie utworzonych modeli:
   - **Przetwarzanie faktury wstępnie skompilowane**
   - **Przetwarzanie paragonu wstępnie utworzone**

   Jeśli chcesz utworzyć tradycyjny, niewprawny model zrozumienia dokumentów zamiast wstępnie utworzonego modelu, wybierz pozycję **Niestandardowe omówienie dokumentów**.

4. Jeśli chcesz zmienić typ zawartości lub dodać etykietę przechowywania, wybierz pozycję **Ustawienia zaawansowane**.

    > [!NOTE]
    > Etykiety poufności nie są obecnie dostępne dla wstępnie utworzonych modeli.

5. Wybierz pozycję **Utwórz**. Model zostanie zapisany w **bibliotece Modele** .

## <a name="add-a-file-to-analyze"></a>Dodawanie pliku do analizy

1. Na stronie **Modele** w sekcji **Dodawanie pliku do analizy** wybierz pozycję **Dodaj plik**.

    ![Zrzut ekranu przedstawiający stronę nowych modeli z sekcją Dodawanie pliku do analizy.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. Na stronie **Pliki do analizowania modelu** wybierz pozycję **Dodaj** , aby znaleźć plik, którego chcesz użyć.

    ![Zrzut ekranu przedstawiający stronę Pliki do analizowania modelu z przyciskiem Dodaj.](../media/content-understanding/prebuilt-add-file-button.png) 

3. Na stronie **Dodawanie pliku z biblioteki plików szkoleniowych** wybierz plik, a następnie wybierz pozycję **Dodaj**.

    ![Zrzut ekranu przedstawiający stronę Dodawanie pliku ze strony biblioteki plików szkoleniowych.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. Na stronie **Pliki do analizowania modelu** wybierz pozycję **Dalej**.

## <a name="select-extractors-for-your-model"></a>Wybieranie wyodrębniaczy dla modelu

Na stronie szczegółów wyodrębniacza zobaczysz obszar dokumentu po prawej stronie i panel **Extractors** po lewej stronie. Na panelu **Extractors** jest wyświetlana lista wyodrębniaczy, które zostały zidentyfikowane w dokumencie.

   ![Zrzut ekranu przedstawiający stronę szczegółów ekstraktora i panel extractor.](../media/content-understanding/prebuilt-extractor-details-page.png) 

Pola jednostek wyróżnione na zielono w obszarze dokumentu to elementy, które zostały wykryte przez model podczas analizowania pliku. Po wybraniu jednostki do wyodrębnienia wyróżnione pole zmieni się na niebieskie. Jeśli później zdecydujesz się nie uwzględniać jednostki, wyróżnione pole zmieni się na szare. Wyróżnienia ułatwiają wyświetlanie bieżącego stanu wybranych wyodrębniaczy.

> [!TIP]
> Możesz użyć kółka przewijania myszy lub kontrolek w dolnej części obszaru dokumentu, aby powiększać lub pomniejszać, zgodnie z potrzebami, aby odczytać pola jednostki.

### <a name="select-an-extractor-entity"></a>Wybieranie jednostki wyodrębniacza

W zależności od preferencji możesz wybrać wyodrębniacz z obszaru dokumentu lub z panelu **Wyodrębniacze** .
 
- Aby wybrać wyodrębniacz z obszaru dokumentu, wybierz pole jednostki.

    ![Zrzut ekranu przedstawiający obszar dokumentu pokazujący sposób wybierania pola jednostki.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- Aby wybrać wyodrębniacz z panelu **Wyodrębniacze** , zaznacz pole wyboru po prawej stronie nazwy jednostki.

    ![Zrzut ekranu panelu Wyodrębniacze przedstawiający sposób wybierania pola jednostki.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Po wybraniu ekstraktora w obszarze dokumentu zostanie wyświetlone pole **Wybierz wyodrębniacz?** Pole zawiera nazwę wyodrębniacza, oryginalną wartość i opcję wybrania jej jako wyodrębniacza. W przypadku niektórych typów danych, takich jak liczby lub daty, zostanie również wyświetlona wyodrębniona wartość.

   ![Zrzut ekranu przedstawiający pole Wybierz wyodrębniacz na stronie szczegółów wyodrębniacza.](../media/content-understanding/prebuilt-select-distractor-box.png) 

Oryginalna wartość jest rzeczywiście w dokumencie. Wyodrębniona wartość zostanie zapisana w kolumnie w SharePoint. Gdy model jest stosowany do biblioteki, możesz użyć formatowania kolumn, aby określić, jak ma wyglądać w dokumencie.

Kontynuuj wybieranie dodatkowych wyodrębniaczy, których chcesz użyć. Możesz również dodać inne pliki do analizowania pod kątem tej konfiguracji modelu.

## <a name="rename-an-extractor"></a>Zmienianie nazwy wyodrębniacza

Możesz zmienić nazwę ekstraktora na stronie głównej modelu lub w panelu **Wyodrębniacze** . Możesz rozważyć zmianę nazw wybranych wyodrębniaczy, ponieważ te nazwy będą używane jako nazwy kolumn, gdy model zostanie zastosowany do biblioteki.

Aby zmienić nazwę ekstraktora ze strony głównej modelu:

1. W sekcji **Extractors (Wyodrębniacze** ) wybierz wyodrębniacz, który chcesz zmienić nazwę, a następnie wybierz pozycję **Zmień nazwę**.

    ![Zrzut ekranu przedstawiający sekcję Extractors (Wyodrębniacze) z wyróżnioną opcją Zmień nazwę.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. Na panelu **Wyodrębnianie jednostki Zmień nazwę** wprowadź nową nazwę ekstraktora, a następnie wybierz pozycję **Zmień nazwę**.

Aby zmienić nazwę ekstraktora z panelu **Extractors** :

1. Wybierz wyodrębniacz, który chcesz zmienić nazwę, a następnie wybierz pozycję **Zmień nazwę**.

    ![Zrzut ekranu panelu Extractors przedstawiający sposób zmiany nazwy wyodrębniacza.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. W polu **Zmienianie nazwy ekstraktora** wprowadź nową nazwę ekstraktora, a następnie wybierz pozycję **Zmień nazwę**.

## <a name="apply-the-model"></a>Stosowanie modelu

- Aby zapisać zmiany i wrócić do strony głównej modelu, na panelu **Extractors** wybierz pozycję **Zapisz i zakończ**.

- Jeśli wszystko jest gotowe do zastosowania modelu do biblioteki, w obszarze dokumentu wybierz pozycję **Dalej**. Na panelu **Dodaj do biblioteki** wybierz bibliotekę, do której chcesz dodać model, a następnie wybierz pozycję **Dodaj**.

## <a name="change-the-view-in-a-document-library"></a>Zmienianie widoku w bibliotece dokumentów

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

