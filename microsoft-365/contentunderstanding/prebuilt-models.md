---
title: Wyodrębnij informacje z faktur lub pokwitowania za pomocą modelu wbudowanego w aplikacji Microsoft SharePoint Syntex
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
description: Dowiedz się, jak tworzyć i konfigurować wstępnie utworzony model w SharePoint Syntex.
ms.openlocfilehash: cf87eab6158ae6dff3053dbddaee7f2fedcd87a5
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013893"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-sharepoint-syntex"></a>Wyodrębnij informacje z faktur lub pokwitowania za pomocą modelu wbudowanego w aplikacji Microsoft SharePoint Syntex

Wbudowane modele są wstępnie przeszkolone w zakresie rozpoznawania dokumentów i strukturalnych informacji w dokumentach. Zamiast tworzyć nowy model niestandardowy od podstaw, możesz dodać do istniejącego wstępnie przeszkolonego modelu określone pola, które będą dopasowane do potrzeb Twojej organizacji. 

Obecnie dostępne są dwa wbudowane modele: faktura i potwierdzenie.

- Model *wstępnego zakupu faktury analizuje* i wyodrębnia kluczowe informacje z faktur sprzedaży. Interfejs API analizuje faktury w różnych formatach i [wyodrębnia](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) kluczowe informacje o fakturze, takie jak nazwa klienta, adres na fakturze, termin i należna kwota.

- Wbudowany *model pokwitowania analizuje* i wyodrębnia kluczowe informacje z pokwitowania sprzedaży. Interfejs API analizuje drukowane i napisane odręcznie potwierdzenia oraz [wyodrębnia](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) informacje dotyczące kluczy pokwitowania, takie jak nazwa dostawcy, numer telefonu handlowego, data transakcji, podatek i suma transakcji.

Dodatkowe wbudowane modele będą dostępne w przyszłych wersjach.

## <a name="create-a-prebuilt-model"></a>Tworzenie modelu wstępnego

Wykonaj poniższe czynności, aby utworzyć wstępny model klasyfikowania dokumentów w SharePoint Syntex.

1. Na stronie **Modele** wybierz pozycję **Utwórz model**.

    ![Zrzut ekranu przedstawiający stronę Modele z przyciskiem Utwórz model.](../media/content-understanding/prebuilt-create-model-button.png) 

2. W **panelu Tworzenie** modelu w polu **Nazwa** wpisz nazwę modelu.

    ![Zrzut ekranu przedstawiający panel Opis nowego dokumentu przedstawiający dostępne typy modeli.](../media/content-understanding/prebuilt-create-panel.png) 

3. W **sekcji Typ modelu** wybierz jeden ze wstępnie utworzonych modeli:
   - **Wstępne przetwarzanie faktury**
   - **Wstępne przetwarzanie pokwitowania**

   Jeśli chcesz utworzyć tradycyjny, niewyszkolony model rozumienia dokumentu zamiast wstępnie utworzonego modelu, wybierz pozycję Opis **dokumentu niestandardowego**.

4. Jeśli chcesz zmienić typ zawartości lub dodać etykietę przechowywania, wybierz pozycję **Ustawienia zaawansowane**.

    > [!NOTE]
    > Obecnie etykiety wrażliwości nie są dostępne dla wstępnie utworzonych modeli.

5. Wybierz pozycję **Utwórz**. Model zostanie zapisany w **bibliotece Modele** .

## <a name="add-a-file-to-analyze"></a>Dodawanie pliku do analizy

1. Na stronie **Modele** w sekcji **Dodawanie** pliku do przeanalizowania wybierz pozycję **Dodaj plik**.

    ![Zrzut ekranu przedstawiający stronę nowych modeli z sekcją Dodaj plik do przeanalizowania.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. Na **stronie Pliki do przeanalizowania modelu** wybierz pozycję **Dodaj** , aby znaleźć plik, którego chcesz użyć.

    ![Zrzut ekranu przedstawiający stronę Pliki do przeanalizowania modelu z przyciskiem Dodaj.](../media/content-understanding/prebuilt-add-file-button.png) 

3. Na **stronie Dodaj plik ze strony biblioteki plików szkoleniowych** wybierz plik, a następnie wybierz pozycję **Dodaj**.

    ![Zrzut ekranu przedstawiający pozycję Dodaj plik ze strony biblioteki plików szkoleniowych.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. Na **stronie Pliki do przeanalizowania modelu** wybierz pozycję **Dalej**.

## <a name="select-extractors-for-your-model"></a>Wybieranie wyodrębniaczy do modelu

Na stronie szczegółów wyodrębniającego zobaczysz obszar dokumentu po prawej stronie, a po lewej stronie panel **Wyodrębniacze** . Panel **Wyodrębniacze** zawiera listę wyodrębniaczy zidentyfikowanych w dokumencie.

   ![Zrzut ekranu przedstawiający stronę szczegółów wyodrębniającego i panel Wyodrębniacz.](../media/content-understanding/prebuilt-extractor-details-page.png) 

Pola encji wyróżnione kolorem zielonym w obszarze dokumentu to elementy wykryte przez model podczas analizowania pliku. Gdy wybierzesz encję do wyodrębnienia, wyróżnione pole zmieni kolor na niebieski. Jeśli później zdecydujesz się nie uwzględniać encji, wyróżnione pole zmieni kolor na szary. Najważniejsze informacje ułatwiają wyświetlanie bieżącego stanu zaznaczonych wyodrębniaczy.

> [!TIP]
> Możesz użyć kółka przewijania myszy lub kontrolek w dolnej części obszaru dokumentu, aby powiększyć lub pomniejszyć widok zgodnie z potrzebami, aby odczytać pola encji.

### <a name="select-an-extractor-entity"></a>Wybieranie jednostki wyodrębniacej

Możesz wybrać wyodrębnianie z obszaru dokumentu lub z panelu **Extractors** , w zależności od preferencji.
 
- Aby wybrać wyodrębnianie z obszaru dokumentu, wybierz pole encji.

    ![Zrzut ekranu przedstawiający obszar dokumentu, w którym pokazano, jak wybrać pole encji.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- Aby wybrać wyodrębnianie z **panelu Wyodrębniacze** , zaznacz pole wyboru po prawej stronie nazwy jednostki.

    ![Zrzut ekranu przedstawiający panel Wyodrębniacze pokazujący, jak wybrać pole encji.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Po wybraniu wyodrębniatora w obszarze dokumentu jest wyświetlane pole **Select extractor? (Wybierz wyodrębniator** ?). Pole zawiera nazwę wyodrębnianego, oryginalną wartość i opcję wybrania jej jako wyodrębniaka. W przypadku niektórych typów danych, takich jak liczby lub daty, będzie również pokazywana wyodrębniona wartość.

   ![Zrzut ekranu przedstawiający pole Select extractor (Wybierz wyodrębniator) na stronie szczegółów wyodrębnianego fragmentatora.](../media/content-understanding/prebuilt-select-distractor-box.png) 

Oryginalna wartość jest faktycznie dosyć w dokumencie. Wyodrębniona wartość zostanie wpisana w kolumnie w programie SharePoint. Po zastosowaniu modelu do biblioteki możesz użyć formatowania kolumn, aby określić, jak ma wyglądać w dokumencie.

Kontynuuj wybieranie dodatkowych wyodrębniaczy, których chcesz użyć. Możesz również dodać inne pliki do przeanalizowania w przypadku tej konfiguracji modelu.

## <a name="rename-an-extractor"></a>Zmienianie nazwy wyodrębnianego

Możesz zmienić nazwę wyodrębniaczy z strony głównej modelu lub z **panelu Extractors** . Możesz rozważyć zmianę nazw wybranych wyodrębniaczy, ponieważ te nazwy będą używane jako nazwy kolumn po zastosowaniu modelu do biblioteki.

Aby zmienić nazwę wyodrębniaka ze strony głównej modelu:

1. W sekcji **Wyodrębniacze** wybierz wyodrębniator, którego nazwę chcesz zmienić, a następnie wybierz pozycję Zmień **nazwę**.

    ![Zrzut ekranu przedstawiający sekcję Wyodrębniacze z wyróżniona opcją Zmień nazwę.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. W **panelu Zmień nazwę wyodrębniającego** jednostki wprowadź nową nazwę wyodrębniającego, a następnie wybierz pozycję Zmień **nazwę**.

Aby zmienić nazwę wyodrębniaczy z **panelu Extractors** :

1. Wybierz wyodrębnianie, którego nazwę chcesz zmienić, a następnie wybierz pozycję Zmień **nazwę**.

    ![Zrzut ekranu przedstawiający panel Extractors pokazujący, jak zmienić nazwę wyodrębniaczy.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. W polu **Zmień nazwę wyodrębnianego** wprowadź nową nazwę wyodrębnianego, a następnie wybierz pozycję Zmień **nazwę**.

## <a name="apply-the-model"></a>Stosowanie modelu

- Aby zapisać zmiany i powrócić do strony głównej modelu, na panelu **Extractors** wybierz pozycję **Zapisz i zamknij**.

- Jeśli chcesz zastosować model do biblioteki, w obszarze dokumentu wybierz pozycję **Dalej**. W **panelu Dodaj** do biblioteki wybierz bibliotekę, do której chcesz dodać model, a następnie wybierz pozycję **Dodaj**.

## <a name="see-also"></a>Zobacz też

[Stosowanie modelu rozumienia dokumentu](apply-a-model.md)