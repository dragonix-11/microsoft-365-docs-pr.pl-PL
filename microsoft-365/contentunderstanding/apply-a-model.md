---
title: Stosowanie modelu rozumienia dokumentu w aplikacji Microsoft SharePoint Syntex
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
description: Dowiedz się, jak zastosować opublikowany model do biblioteki SharePoint dokumentów w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 0edb87faacc3518179b8bd1a4d41d7e3834394c3
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014882"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Stosowanie modelu rozumienia dokumentu w aplikacji Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Po opublikowaniu modelu rozumienia dokumentu można go zastosować do jednej lub SharePoint dokumentów w Microsoft 365 dzierżawie.

> [!NOTE]
> Model można stosować tylko do bibliotek dokumentów, do których masz dostęp.


## <a name="apply-your-model-to-a-document-library"></a>Stosowanie modelu do biblioteki dokumentów

Aby zastosować model do SharePoint dokumentów:

1. Na stronie głównej modelu na **kafelku Zastosuj model do bibliotek** wybierz pozycję **Zastosuj model**. Lub w sekcji **Gdzie został zastosowany model** wybierz pozycję **+Dodaj bibliotekę**.

    ![Zrzut ekranu przedstawiający sekcję Gdzie zastosowano model z wyróżniona opcją Dodaj bibliotekę.](../media/content-understanding/apply-to-library.png)

2. Następnie możesz wybrać witrynę SharePoint zawierającą bibliotekę dokumentów, do której chcesz zastosować model. Jeśli witryna nie jest wyświetlona na liście, użyj pola wyszukiwania, aby ją znaleźć.

    ![Wybierz witrynę.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Musisz mieć uprawnienia *do zarządzania listą* lub *uprawnienia do* edytowania biblioteki dokumentów, do których chcesz zastosować model.

3. Po wybraniu witryny wybierz bibliotekę dokumentów, do której chcesz zastosować model. W przykładzie wybierz *bibliotekę dokumentów Dokumenty* w witrynie *Śledzenie przypadków Contoso* .

    ![Wybierz bibliotekę dokumentów.](../media/content-understanding/select-doc-library.png)

4. Model jest skojarzony z typem zawartości, dlatego po zastosowaniu go do biblioteki spowoduje dodanie typu zawartości i zaktualizowanie widoku domyślnego przy użyciu wyodrębnianych etykiet jako kolumn. Możesz jednak wybrać pozycję **Ustawienia** zaawansowane, aby opcjonalnie zdecydować się na zachowanie bieżącego widoku biblioteki lub użycie nowego widoku z informacjami o modelu i miniaturami plików. Jeśli zdecydujesz się zachować bieżący widok biblioteki, nowe widoki z informacjami o modelu będą nadal dostępne w menu widok biblioteki.

    ![Zrzut ekranu przedstawiający ustawienia zaawansowane z widokami biblioteki.](../media/content-understanding/library-view.png)

    Aby uzyskać więcej informacji, [zobacz Zmienianie widoku w bibliotece dokumentów](#change-the-view-in-a-document-library) w dalszej części tego artykułu.

5. Wybierz **pozycję Dodaj** , aby zastosować model do biblioteki.

6. Na stronie głównej modelu w sekcji Gdzie został zastosowany **model** powinna być SharePoint stronie.

7. Przejdź do biblioteki dokumentów i upewnij się, że jesteś w widoku biblioteki dokumentów modelu. Wybierz **pozycję AutomateView** >  **opis modeli dokumentu**.

8. Na **stronie Przeglądanie modeli i stosowanie nowych** wybierz kartę Zastosowane,  aby wyświetlić modele zastosowane do biblioteki dokumentów.

    ![Zrzut ekranu przedstawiający wybraną kartę Zastosowane i zastosowane modele.](../media/content-understanding/applied-models.png) 

9. Wybierz **pozycję Wyświetl szczegóły modelu** , aby wyświetlić informacje o modelu, takie jak opis modelu, kto go opublikował i czy w modelu są stosowane etykiety przechowywania lub wrażliwości do plików, które klasyfikuje.

Po zastosowaniu modelu do biblioteki dokumentów możesz rozpocząć przekazywanie dokumentów do witryny i wyświetlić wyniki.

Model identyfikuje wszystkie pliki i foldery przy użyciu skojarzonego z modelem typu zawartości i wyświetla je w widoku. Jeśli model zawiera jakiekolwiek wyodrębniacze, w widoku są wyświetlane kolumny danych wyodrębnianych z każdego pliku lub folderu.

> [!NOTE]
> Jeśli do tej samej biblioteki zastosowano co najmniej dwa modele opisowe dokumentów, przekazany plik zostanie sklasyfikowany przy użyciu modelu o największej średniej ufności. Wyodrębnione jednostki będą pochodzić tylko z zastosowanego modelu. <br><br>Jeśli do tej samej biblioteki zastosowano niestandardowy model przetwarzania formularza i model rozumienia dokumentu, plik zostanie sklasyfikowany przy użyciu modelu rozumienia dokumentu i dowolnych przeszkolonych wyodrębniaczy dla tego modelu. Jeśli istnieją puste kolumny zgodne z modelem przetwarzania formularzy, kolumny zostaną wypełnione przy użyciu tych wyodrębnianych wartości.

## <a name="sync-changes-to-one-or-more-libraries"></a>Synchronizowanie zmian w jednej lub większej liczby bibliotek

Podczas publikowania modelu w wielu bibliotekach dokumentów, a następnie aktualizowania modelu, na przykład dodawania lub usuwania wyodrębniaczy, musisz wypchnąć aktualizację do wszystkich bibliotek, które zastosowano do modelu.

Aby zsynchronizować zmiany ze wszystkimi zastosowanymi bibliotekami:

1. Na stronie głównej modelu w sekcji **Gdzie został zastosowany model** wybierz pozycję **Synchronizuj wszystko**.

    ![Zrzut ekranu przedstawiający sekcję Gdzie zastosowano model i wyróżniony przycisk Synchronizuj wszystko.](../media/content-understanding/sync-all-button.png) 

Aby zsynchronizować zmiany z jedną lub tylko wybranymi bibliotekami:

1. Na stronie głównej modelu w sekcji Gdzie **został zastosowany model** wybierz bibliotekę lub biblioteki, do których chcesz zastosować zmiany.

2. Wybierz **pozycję Synchronizuj**.

    ![Zrzut ekranu przedstawiający sekcję Gdzie zastosowano model i wyróżniony przycisk Synchronizuj.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Stosowanie modelu do plików i zawartości folderów już w bibliotece dokumentów

Podczas gdy zastosowany model przetwarza wszystkie pliki i foldery zawartości przekazanej do biblioteki dokumentów po jego zastosowaniu, możesz również wykonać następujące czynności, aby uruchomić model na plikach i folderach zawartości istniejących już w bibliotece dokumentów przed zastosowaniem modelu:

1. W bibliotece dokumentów zaznacz pliki i foldery, które mają być przetwarzane przez model.

2. Po wybraniu plików i folderów, **Klasyfikowanie i wyodrębnianie** pojawi się na wstążce biblioteki dokumentów. Wybierz **pozycję Klasyfikowanie i wyodrębnianie**.

      ![Zrzut ekranu przedstawiający opcję Klasyfikowanie i wyodrębnianie.](../media/content-understanding/extract-classify.png) 

3. Wybrane pliki i foldery zostaną dodane do kolejki do przetworzenia.

    > [!NOTE]
    > Zostanie wyświetlony komunikat z informacją, jak długo może potrwać klasyfikacja. Jeśli wybrano tylko pliki, klasyfikacja może potrwać do 30 minut. Jeśli wybrano co najmniej jeden folder, klasyfikacja może potrwać do 24 godzin.

### <a name="classification-date-field"></a>Pole Data klasyfikacji

W przypadku SharePoint Syntex dokumentu opisowego modelu (lub modelu przetwarzania formularza) do biblioteki dokumentów pole Data klasyfikacji jest  uwzględniane w schemacie biblioteki. Domyślnie to pole jest puste. Jednak podczas przetwarzania i klasyfikowania dokumentów za pomocą modelu to pole jest aktualizowane za pomocą sygnatury daty i czasu wykonania. 

   ![Zrzut ekranu przedstawiający bibliotekę dokumentów z kolumną Data klasyfikacji.](../media/content-understanding/class-date-column.png) 

Pole **Data klasyfikacji** jest używane przez wyzwalacz [](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) modelu rozumienia zawartości podczas klasyfikowania pliku w celu uruchomienia przepływu Power Automate po zakończeniu przetwarzania zawartości pliku lub folderu przez model i zaktualizowaniu pola Data klasyfikacji.

   ![Flow wyzwalacza.](../media/content-understanding/trigger.png)

Za **pomocą wyzwalacza modelu rozumienia** zawartości można następnie uruchomić przepływ, używając dowolnych wyodrębnianych informacji z pliku lub folderu, gdy plik jest klasyfikowany przez wyzwalacz modelu rozumienia zawartości.

Na przykład po oznaczaniu modelu sygnaturą z datą klasyfikacji możesz użyć funkcji Wyślij wiadomość e-mail po **tym, jak** program SharePoint Syntex przetwarza przepływ pliku w celu powiadomienia użytkowników, że nowy plik został przetworzony i sklasyfikowany przez model w bibliotece dokumentów usługi **SharePoint**.

Aby uruchomić przepływ:

1. Wybierz plik, a następnie **wybierz pozycję** Integracja  > **Power Automate** >  **Tworzenie przepływu**.

2. Na **panelu Tworzenie przepływu** wybierz pozycję Wyślij wiadomość e-mail, **SharePoint Syntex przetwarza plik**.

    ![Zrzut ekranu przedstawiający opcję Utwórz panel przepływu i przepływ.](../media/content-understanding/integrate-create-flow.png) 

## <a name="change-the-view-in-a-document-library"></a>Zmienianie widoku w bibliotece dokumentów

Istnieje wiele sposobów wyświetlania informacji w bibliotece SharePoint dokumentów. Możesz zmienić widok w bibliotece dokumentów, aby dopasować go do swoich potrzeb lub preferencji.

Aby zmienić widok na stronie biblioteki, wybierz menu rozwijane Widok, aby wyświetlić opcje, a następnie wybierz widok, którego chcesz użyć.

   ![Zrzut ekranu przedstawiający menu rozwijane widoków z opcjami widoku.](../media/content-understanding/document-library-view-menu.png) 

Jeśli na przykład **wybierzesz z** listy pozycję Kafelki, strona będzie wyświetlana w sposób pokazany.

   ![Zrzut ekranu przedstawiający bibliotekę dokumentów z widokiem Kafelki.](../media/content-understanding/document-library-tiles-view.png) 

W **widoku** Kafelki jest wyświetlanych maksymalnie osiem pól utworzonych przez użytkownika. Jeśli jest mniej niż osiem, wyświetlane są maksymalnie cztery pola wygenerowane przez system: Charakter (jeśli jest dostępny), Przechowywanie (jeśli jest dostępne), Typ zawartości, Data modyfikacji, Zmodyfikowane przez i Data klasyfikacji.

Aby edytować dowolny bieżący widok, z menu rozwijanego widoków wybierz pozycję **Edytuj bieżący widok**.

## <a name="see-also"></a>Zobacz też

[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)
