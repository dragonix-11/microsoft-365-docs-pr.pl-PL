---
title: Stosowanie etykiety przechowywania do modelu w SharePoint Syntex
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
description: Dowiedz się, jak zastosować etykietę przechowywania do modelu w SharePoint Syntex.
ms.openlocfilehash: 17bfc0121d18f30b03cc42585cb214b649597ff6
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882511"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>Stosowanie etykiety przechowywania do modelu w SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>


Etykietę [przechowywania](../compliance/retention.md) można łatwo zastosować do modelu w usłudze Microsoft SharePoint Syntex. Można to zrobić zarówno w przypadku modeli interpretacji dokumentów, jak i przetwarzania formularzy.

Etykiety przechowywania umożliwiają stosowanie ustawień przechowywania do dokumentów, które identyfikują modele.  Na przykład chcesz, aby model nie tylko identyfikował wszelkie dokumenty *z powiadomieniem o ubezpieczeniach* , które zostały przekazane do biblioteki dokumentów, ale także zastosował do nich tag przechowywania *firmy* , aby nie można było usunąć tych dokumentów z biblioteki dokumentów w określonym okresie (na przykład w ciągu najbliższych pięciu miesięcy).

Istniejącą etykietę przechowywania można zastosować do modelu za pomocą ustawień modelu na stronie głównej modelu. 

> [!Important]
> Aby etykiety przechowywania były dostępne do zastosowania w modelach interpretacji dokumentów, należy [je utworzyć](../compliance/file-plan-manager.md#create-retention-labels) i [opublikować](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) w Centrum zgodności platformy Microsoft 365.

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Aby dodać etykietę przechowywania do modelu zrozumienia dokumentu

1. Na stronie głównej modelu wybierz pozycję **Ustawienia modelu**.</br>
2. W **obszarze Ustawienia modelu** w sekcji **Zabezpieczenia i zgodność** wybierz menu **Etykieta przechowywania** , aby wyświetlić listę etykiet przechowywania dostępnych do zastosowania do modelu.</br>
 ![Menu etykiet przechowywania.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Wybierz etykietę przechowywania, którą chcesz zastosować do modelu, a następnie wybierz pozycję **Zapisz**.</br>

Po zastosowaniu etykiety przechowywania do modelu można zastosować ją do:
- Nowa biblioteka dokumentów
- Biblioteka dokumentów, do której model jest już zastosowany
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Stosowanie etykiety przechowywania do biblioteki dokumentów, do której model jest już zastosowany

Jeśli model interpretacji dokumentów został już zastosowany do biblioteki dokumentów, możesz wykonać następujące czynności, aby zsynchronizować aktualizację etykiety przechowywania, aby zastosować ją do biblioteki dokumentów:</br>

1. Na stronie głównej modelu w sekcji **Biblioteki z tym modelem** wybierz bibliotekę dokumentów, do której chcesz zastosować aktualizację etykiety przechowywania. </br> 
2. Wybierz pozycję **Synchronizuj**. </br>
 ![Model synchronizacji.](../media/content-understanding/sync-model.png)</br> 


Po zastosowaniu aktualizacji i zsynchronizowaniu jej z modelem możesz potwierdzić, że została ona zastosowana, wykonując następujące czynności:

1. W centrum zawartości w sekcji **Biblioteki z tym modelem** kliknij bibliotekę, do której został zastosowany zaktualizowany model. </br>
2. W widoku biblioteki dokumentów wybierz ikonę informacji, aby sprawdzić właściwości modelu.</br>  
3. Na liście **Aktywne modele** wybierz zaktualizowany model.</br>
4. W sekcji **Etykieta przechowywania** zostanie wyświetlona nazwa zastosowanej etykiety przechowywania.</br>


Na stronie widoku modelu w bibliotece dokumentów zostanie wyświetlona nowa kolumna **Etykieta przechowywania** .  Ponieważ model klasyfikuje pliki, które identyfikuje jako należące do typu zawartości, i wyświetla je w widoku biblioteki, kolumna Etykieta przechowywania będzie również wyświetlać nazwę etykiety przechowywania, która została do niej zastosowana za pośrednictwem modelu.


Na przykład wszystkie dokumenty *z powiadomieniem o ubezpieczeniach* , które identyfikuje model, będą miały również zastosowany etykietę Przechowywania *firmy* , co uniemożliwi ich usunięcie z biblioteki dokumentów na pięć miesięcy. Jeśli zostanie podjęta próba usunięcia pliku z biblioteki dokumentów, zostanie wyświetlony błąd informujący, że jest on niedozwolony ze względu na zastosowaną etykietę przechowywania.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Aby dodać etykietę przechowywania do modelu przetwarzania formularzy

> [!Important]
> Aby etykiety przechowywania były dostępne do zastosowania do modelu przetwarzania formularzy, należy [je utworzyć](../compliance/file-plan-manager.md#create-retention-labels) i [opublikować](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) w Centrum zgodności platformy Microsoft 365.

Podczas tworzenia modelu można zastosować etykietę przechowywania do modelu przetwarzania formularzy lub zastosować ją do istniejącego modelu.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Aby dodać etykietę przechowywania podczas tworzenia modelu przetwarzania formularzy

1. Podczas [tworzenia nowego modelu przetwarzania formularzy](./create-a-form-processing-model.md) wybierz pozycję <b>Ustawienia zaawansowane.</b>
2. W <b>obszarze Ustawienia zaawansowane</b> w sekcji <b>Etykieta przechowywania</b> wybierz menu, a następnie wybierz etykietę przechowywania, którą chcesz zastosować do modelu.</b>

 
     ![Dodaj do nowego modelu przetwarzania formularzy.](../media/content-understanding/retention-label-forms.png)</br>

3.  Po zakończeniu pozostałych ustawień modelu wybierz pozycję <b>Utwórz</b> , aby skompilować model.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Aby dodać etykietę przechowywania do istniejącego modelu przetwarzania formularzy

Etykietę przechowywania można dodać do istniejącego modelu przetwarzania formularzy na różne sposoby:
- Za pomocą menu Automate w bibliotece dokumentów
- Za pośrednictwem ustawień modelu aktywnego w bibliotece dokumentów 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Aby dodać etykietę przechowywania do istniejącego modelu przetwarzania formularzy za pomocą menu Automate

Etykietę przechowywania można dodać do istniejącego modelu przetwarzania formularzy, którego jesteś właścicielem, za pośrednictwem menu Automate w bibliotece dokumentów, w której jest stosowany model.


1. W bibliotece dokumentów, do której jest stosowany model przetwarzania formularzy, wybierz menu <b>Automate</b> , wybierz pozycję <b>AI Builder</b>, a następnie wybierz pozycję <b>Wyświetl szczegóły modelu przetwarzania formularzy</b>.

   ![Menu Automatyzowanie.](../media/content-understanding/automate-menu.png)</br>

2. W szczegółach modelu w sekcji <b>Etykieta przechowywania</b> wybierz etykietę przechowywania, którą chcesz zastosować.  Następnie wybierz pozycję <b>Zapisz</b>.

     ![Dodaj do istniejącego modelu przetwarzania formularzy.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Aby dodać etykietę przechowywania do istniejącego modelu przetwarzania formularzy w ustawieniach aktywnego modelu

Etykietę przechowywania można dodać do istniejącego modelu przetwarzania formularzy, którego jesteś właścicielem, za pośrednictwem ustawień modelu aktywnego w bibliotece dokumentów, w której jest stosowany model.

1. W bibliotece dokumentów SharePoint, w której jest stosowany model, wybierz ikonę <b>Wyświetl aktywne modele</b>, a następnie wybierz pozycję <b>Wyświetl aktywne modele</b>.</b>

   ![Wyświetlanie aktywnych modeli.](../media/content-understanding/info-du.png)</br> 

2. W <b>obszarze Modele aktywne</b> wybierz model przetwarzania formularzy, do którego chcesz zastosować etykietę przechowywania.

     ![Szczegóły modelu.](../media/content-understanding/retention-label-model-details.png)</br> 


3. W szczegółach modelu w sekcji <b>Etykieta przechowywania</b> wybierz etykietę przechowywania, którą chcesz zastosować.  Następnie wybierz pozycję <b>Zapisz</b>.

> [!NOTE]
> Aby można było edytować okienko ustawień modelu, musisz być właścicielem modelu. 


## <a name="see-also"></a>Zobacz też

[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)
