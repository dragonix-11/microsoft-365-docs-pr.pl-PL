---
title: Stosowanie etykiety przechowywania do modelu w programie SharePoint Syntex
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
description: Dowiedz się, jak zastosować etykietę przechowywania do modelu w programie SharePoint Syntex.
ms.openlocfilehash: 112b48af5e07d09faab61bd656c5629b449d9a1c
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010665"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>Stosowanie etykiety przechowywania do modelu w programie SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>


Etykietę przechowywania można łatwo [zastosować](../compliance/retention.md) do modelu w aplikacji Microsoft SharePoint Syntex. Możesz to zrobić zarówno w przypadku zrozumienia dokumentu, jak i modeli przetwarzania formularzy.

Etykiety przechowywania umożliwiają stosowanie ustawień przechowywania do dokumentów identyfikowanych przez modele.  Model ma na przykład nie tylko identyfikować wszystkie dokumenty  z informacjami o ubezpieczeniach, które są przekazywane do biblioteki dokumentów, ale  także stosować do nich tag przechowywania danych biznesowych, aby nie można było ich usuwać z biblioteki dokumentów w określonym przedziale czasu (na przykład przez następne pięć miesięcy).

Możesz zastosować istniejącą etykietę przechowywania do modelu za pomocą ustawień modelu na stronie głównej modelu. 

> [!Important]
> Aby etykiety przechowywania były dostępne w celu zastosowania do dokumentu opisowego modeli, należy je utworzyć [](../compliance/file-plan-manager.md#create-retention-labels) i [opublikować](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) w Centrum zgodności platformy Microsoft 365.

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Aby dodać etykietę przechowywania do modelu opisowego dokumentu

1. Na stronie głównej modelu wybierz **pozycję Ustawienia modelu**.</br>
2. W **sekcji Ustawienia** modelu **w sekcji Zabezpieczenia** i zgodność **wybierz menu** Etykieta przechowywania, aby wyświetlić listę dostępnych etykiet przechowywania, które możesz zastosować do modelu.</br>
 ![Menu Etykieta przechowywania.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Wybierz etykietę przechowywania, którą chcesz zastosować do modelu, a następnie wybierz pozycję **Zapisz**.</br>

Po zastosowaniu etykiety przechowywania do modelu można zastosować ją do:
- Nowa biblioteka dokumentów
- Biblioteka dokumentów, do której został już zastosowany model
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Stosowanie etykiety przechowywania do biblioteki dokumentów, do której już zastosowano model

Jeśli model rozumienia dokumentu został już zastosowany do biblioteki dokumentów, możesz wykonać następujące czynności w celu zsynchronizowania aktualizacji etykiet przechowywania w celu zastosowania go do biblioteki dokumentów:</br>

1. Na stronie głównej modelu w sekcji **Biblioteki z tym modelem** wybierz bibliotekę dokumentów, do której chcesz zastosować aktualizację etykiet przechowywania. </br> 
2. Wybierz **pozycję Synchronizuj**. </br>
 ![Model synchronizacji.](../media/content-understanding/sync-model.png)</br> 


Po zastosowaniu aktualizacji i zsynchronizowaniu jej z modelem możesz potwierdzić jej zastosowanie, wykonując następujące czynności:

1. W centrum zawartości w sekcji **Biblioteki z tym modelem** kliknij bibliotekę, do której zastosowano zaktualizowany model. </br>
2. W widoku biblioteki dokumentów wybierz ikonę informacji, aby sprawdzić właściwości modelu.</br>  
3. Na liście **Aktywne** modele wybierz zaktualizowany model.</br>
4. W sekcji **Etykieta** przechowywania zobaczysz nazwę zastosowanej etykiety przechowywania.</br>


Na stronie widoku modelu w bibliotece dokumentów zostanie wyświetlana **nowa kolumna** Etykieta przechowywania.  Podczas gdy model klasyfikuje pliki jako należące do jego typu zawartości i wyświetla je w widoku biblioteki, w kolumnie Etykieta przechowywania będzie również wyświetlana nazwa etykiety przechowywania, która została do niej zastosowana za pośrednictwem modelu.


Na przykład *do wszystkich dokumentów* z powiadomieniami o ubezpieczeniach, które są identyfikowane  przez Twój model, będą również stosowane etykiety przechowywania Biznesowe, uniemożliwiając ich usunięcie z biblioteki dokumentów przez pięć miesięcy. Jeśli zostanie wykonana próba usunięcia pliku z biblioteki dokumentów, zostanie wyświetlany komunikat o błędzie z informacją, że nie jest on dozwolony ze względu na zastosowaną etykietę przechowywania.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Aby dodać etykietę przechowywania do modelu przetwarzania formularzy

> [!Important]
> Aby etykiety przechowywania były dostępne do zastosowania w modelu przetwarzania formularzy, należy je utworzyć [](../compliance/file-plan-manager.md#create-retention-labels) i [opublikować](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) w Centrum zgodności platformy Microsoft 365.

Etykietę przechowywania można zastosować do modelu przetwarzania formularzy podczas tworzenia modelu lub zastosować do istniejącego modelu.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Aby dodać etykietę przechowywania podczas tworzenia modelu przetwarzania formularzy

1. Podczas tworzenia [nowego modelu przetwarzania formularzy](./create-a-form-processing-model.md) wybierz pozycję <b>Ustawienia zaawansowane.</b>
2. W <b>sekcji Ustawienia</b> zaawansowane w sekcji <b>Etykieta przechowywania</b> wybierz menu, a następnie wybierz etykietę przechowywania, którą chcesz zastosować do modelu.</b>

 
     ![Dodaj do nowego modelu przetwarzania formularzy.](../media/content-understanding/retention-label-forms.png)</br>

3.  Po zakończeniu pozostałych ustawień modelu wybierz pozycję <b>Utwórz</b> , aby utworzyć model.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Aby dodać etykietę przechowywania do istniejącego modelu przetwarzania formularzy

Etykietę przechowywania można dodać do istniejącego modelu przetwarzania formularzy na różne sposoby:
- Za pośrednictwem menu Automatyzuj w bibliotece dokumentów
- Za pośrednictwem ustawień aktywnego modelu w bibliotece dokumentów 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Aby dodać etykietę przechowywania do istniejącego modelu przetwarzania formularzy za pomocą menu Automate

Etykietę przechowywania można dodać do istniejącego modelu przetwarzania formularzy, którego jesteś właścicielem, za pomocą menu Automate w bibliotece dokumentów, w której został zastosowany model.


1. W bibliotece dokumentów, do której zastosowano model przetwarzania formularzy, wybierz menu <b>Automatyzuj</b> , wybierz pozycję <b>Konstruktor AI, a</b> następnie wybierz pozycję <b>Wyświetl szczegóły modelu przetwarzania formularzy</b>.

   ![Menu Automatyzuj.](../media/content-understanding/automate-menu.png)</br>

2. W szczegółach modelu w sekcji <b>Etykieta przechowywania</b> wybierz etykietę przechowywania, którą chcesz zastosować.  Następnie wybierz <b>pozycję Zapisz</b>.

     ![Dodawanie do istniejącego modelu przetwarzania formularzy.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Aby dodać etykietę przechowywania do istniejącego modelu przetwarzania formularzy w aktywnych ustawieniach modelu

Etykietę przechowywania można dodać do istniejącego modelu przetwarzania formularzy, którego jesteś właścicielem, za pomocą ustawień aktywnego modelu w bibliotece dokumentów, w której został zastosowany model.

1. W bibliotece SharePoint dokumentów, w której został zastosowany model, wybierz ikonę Wyświetl <b>aktywne</b> modele, a następnie wybierz pozycję <b>Wyświetl aktywne modele</b>.</b>

   ![Wyświetlanie aktywnych modeli.](../media/content-understanding/info-du.png)</br> 

2. W <b>przypadku aktywnych modeli</b> wybierz model przetwarzania formularzy, do którego chcesz zastosować etykietę przechowywania.

     ![Szczegóły modelu.](../media/content-understanding/retention-label-model-details.png)</br> 


3. W szczegółach modelu w sekcji <b>Etykieta przechowywania</b> wybierz etykietę przechowywania, którą chcesz zastosować.  Następnie wybierz <b>pozycję Zapisz</b>.

> [!NOTE]
> Aby można było edytować okienko ustawień modelu, musisz być właścicielem modelu. 


## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)
