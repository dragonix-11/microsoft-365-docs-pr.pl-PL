---
title: Publikowanie i odkrywanie modeli w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się, jak udostępnić przeszkolone modele innym osobom i jak stosować inne przeszkolone modele w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 9645b669c6fd419e8866d415cb5d2b0da56ab0e2
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2021
ms.locfileid: "63005235"
---
# <a name="publish-and-discover-models-in-microsoft-sharepoint-syntex"></a>Publikowanie i odkrywanie modeli w aplikacji Microsoft SharePoint Syntex

Przeszkolone dokumenty mogą udostępnić innym osobom do wyświetlania i używania modeli bezpośrednio z SharePoint dokumentów. 

Możesz również znaleźć i ocenić przeszkolone modele w innych centrach zawartości utworzonych przez inne osoby w organizacji. Wybierz model, który jest najbardziej przydatny do klasyfikowania plików lub wyodrębniania z nich określonych informacji. 

> [!NOTE]
> Ta funkcja nie jest jeszcze dostępna w przypadku modeli przetwarzania formularzy.

## <a name="make-your-model-discoverable-to-others"></a>Odkrywanie modelu innym osobom

Aby udostępnić przeszkolony model do użytku innym osobom:

1. Na stronie **Modele** dla Twojego modelu wybierz **pozycję Ustawienia modelu**.

2. W **panelu Ustawienia** modelu w sekcji **Witryny, w których ten model jest dostępny** wybierz pozycję **Edytuj**.

3. W tym momencie **panel Wybierz witryny** , w których jest dostępny ten model będzie różny w zależności od tego, czy jesteś administratorem. 

    Ten widok jest SharePoint administratorem witryny.

    ![Zrzut ekranu przedstawiający panel Wybierz witryny, w których jest dostępny ten model z opcjami miejsca, w którym model ma być dostępny dla innych osób.](../media/content-understanding/select-sites.png)

    - **Niedostępne w żadnych witrynach** — model nie będzie dostępny dla innych użytkowników.
    - **Wszystkie witryny** — model będzie dostępny do użytku w galerii typów zawartości dla innych użytkowników.
    - **Tylko wybrane witryny** — możesz wybrać witryny, w których model będzie dostępny. Kliknij w polu tekstowym, aby wyszukać i wybrać witryny, do których chcesz zastosować model. Będą tu dostępne tylko te witryny, do których masz dostęp.

    Ten widok *jest SharePoint* dla innych administratorów.

    ![Zrzut ekranu przedstawiający panel Wybierz witryny, w których ten model jest dostępny, przedstawiający opcje dla użytkowników końcowych z tylko kilkoma dostępnymi witrynami.](../media/content-understanding/select-site-user.png)

    Dostępność możesz dodawać lub usuwać tylko w konkretnych witrynach, do których już masz dostęp.

4. Wybierz witryny, w których chcesz, aby model był dostępny dla innych użytkowników, a następnie wybierz pozycję **Zapisz**.

## <a name="discover-other-trained-models"></a>Odkrywanie innych przeszkolonych modeli

Aby znaleźć przeszkolone modele, które mogą być odpowiednie dla Twojej zawartości:

1. W bibliotece dokumentów dla modelu wybierz pozycję **AutomateView** >  **opis modeli dokumentów**.

2. Na **stronie Przeglądanie modeli i stosowanie nowych** możesz przejrzeć zastosowane modele i te, które można zastosować do biblioteki dokumentów.

    ![Zrzut ekranu przedstawiający stronę Przeglądanie modeli i stosowanie nowych z kartami Zastosowane i Dostępne.](../media/content-understanding/review-models-apply-new-ones.png)

   - Na karcie **Zastosowane** zobacz modele, które zostały zastosowane do biblioteki. Wybierz **pozycję Wyświetl szczegóły modelu** , aby wyświetlić informacje o modelu, takie jak opis, wyodrębniacze i inne ustawienia.
   
   - Na **karcie Dostępne** zapoznaj się z przeszkolonymi modelami, które można zastosować do biblioteki.


### <a name="apply-a-trained-model-to-your-library"></a>Stosowanie przeszkolonego modelu do biblioteki

Możesz ocenić przeszkolone modele na tle swojej zawartości, aby pomóc w odnalezieniu najbardziej odpowiedniego. Aby wybrać model, który chcesz zastosować do biblioteki:

1. Na stronie **Przeglądanie modeli i stosowanie nowych** wybierz kartę Dostępne,  aby przejrzeć modele na liście.

    ![Zrzut ekranu przedstawiający stronę Przeglądanie modeli i stosowanie nowych modeli na karcie Dostępne.](../media/content-understanding/available-models-to-apply.png)

2. Wybierz model, który według Ciebie pozwoli uzyskać najlepsze wyniki, wybierz pozycję **Wyświetl szczegóły modelu**, a następnie wybierz pozycję **Zastosuj do biblioteki**.

### <a name="get-a-recommendation-for-a-trained-model"></a>Uzyskaj zalecenia dla przeszkolonego modelu

Jeśli nie masz pewności, który model najlepiej pasuje do Twoich plików, możesz poprosić o zalecenia. Twoje zalecenie może zawierać maksymalnie 10 modeli.

1. Na **stronie Przeglądanie modeli i stosowanie nowych** wybierz **kartę** Dostępne.

2. Na pierwszym kafelku wybierz pozycję **Uzyskaj zalecenie**.

    ![Zrzut ekranu przedstawiający stronę Przeglądanie modeli i stosowanie nowych z opcją Uzyskaj zalecenia na karcie Dostępne.](../media/content-understanding/get-recommendation.png)

3. Na **stronie Wybierz jeden lub więcej** modeli do analizy wybierz modele, które mogą być najlepiej dopasowane, a następnie wybierz pozycję **Dalej**.

    ![Zrzut ekranu przedstawiający stronę Wybierz jeden lub więcej modeli z zaznaczonymi dwoma modelami.](../media/content-understanding/recommendation-results.png)

4. Na **stronie Wybierz plik do przeanalizowania** wybierz plik tego samego lub podobnego typu, który będzie przechowywany w bibliotece. Następnie wybierz **pozycję Wybierz**.

    ![Zrzut ekranu przedstawiający stronę Wybierz plik do przeanalizowania z zaznaczonymi plikami.](../media/content-understanding/file-to-analyze.png)

5. Na stronie **Przeglądanie wyników i wybierz model** w obszarze **Zalecane** przez Nas zobaczysz polecany plik. Nie musisz stosować zalecanego modelu. Jeśli uważasz, że lepiej pasuje, możesz zastosować inny model.

    ![Zrzut ekranu przedstawiający stronę Przeglądanie wyników i wybierz stronę modelu przedstawiającą zalecane modele.](../media/content-understanding/review-results.png)

6. Dla modelu, który uważasz, że uzyskaj najlepsze wyniki, wybierz pozycję **Wyświetl szczegóły modelu**, a następnie wybierz pozycję **Zastosuj do biblioteki**.

7. Jeśli nie ma zalecanych modeli na podstawie wybranego pliku, możesz wrócić i wybrać inny plik lub wybrać inne modele.

### <a name="remove-an-applied-model"></a>Usuwanie zastosowanego modelu

Aby usunąć model zastosowany z biblioteki dokumentów:

1. Na **stronie Przeglądanie modeli i stosowanie** nowych modeli na karcie Zastosowane zobacz  modele, które zostały zastosowane do biblioteki.

2. W modelu, który chcesz usunąć, wybierz pozycję **Wyświetl szczegóły modelu**, a następnie wybierz **pozycję Usuń z biblioteki**.


## <a name="see-also"></a>Zobacz też

[Stosowanie modelu rozumienia dokumentu](apply-a-model.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)
