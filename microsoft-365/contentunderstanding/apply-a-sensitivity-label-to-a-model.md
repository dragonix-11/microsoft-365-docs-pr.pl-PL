---
title: Stosowanie etykiet wrażliwości do modelu w aplikacji Microsoft SharePoint Syntex
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
description: Dowiedz się, jak zastosować etykietę wrażliwości do modelu w SharePoint Syntex.
ms.openlocfilehash: 189db9314e01a52618890daf6b0e5d4e81317de9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681705"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>Stosowanie etykiet wrażliwości do modelu w aplikacji Microsoft SharePoint Syntex

Możesz łatwo zastosować etykietę [wrażliwości, aby zrozumieć](../compliance/sensitivity-labels.md) modele w aplikacji Microsoft SharePoint Syntex. Ta funkcja nie jest jeszcze dostępna w przypadku modeli przetwarzania formularzy.

Etykiety wrażliwości umożliwiają zastosowanie szyfrowania do dokumentów identyfikowanych przez modele. Model ma na przykład zawierać nie tylko dokumenty finansowe zawierające numery kont bankowych lub numery kart kredytowych, które są przekazywane do biblioteki dokumentów, ale również etykietę wrażliwości skonfigurowanej przy użyciu ustawień szyfrowania w celu ograniczenia dostępu do tej zawartości i sposobu jej stosowania. SharePoint Syntex modelach są stosowane [reguły](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) kolejności etykiet, a także nie zastępują istniejącej etykiety, która została ręcznie zastosowana przez użytkownika do pliku. 

W ustawieniach modelu na stronie głównej modelu możesz zastosować istniejącą etykietę wrażliwości do modelu. Etykieta musi już zostać opublikowana, aby była dostępna do wyboru w ustawieniach modelu. Etykiety dotyczą Office plików programu Word (.docx), PowerPoint (.pptx) i Excel (.xlsx). 

> [!Important]
> Aby etykiety wrażliwości były dostępne do zastosowania w dokumencie w celu zrozumienia modeli, należy je utworzyć i opublikować w Centrum zgodności Microsoft 365 [zgodności](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>Dodawanie etykiety wrażliwości do modelu opisowego dokumentu

1. Na stronie głównej modelu wybierz **pozycję Ustawienia modelu**.

   ![Zrzut ekranu przedstawiający stronę Modele z wyróżniona opcją Ustawienia modelu.](../media/content-understanding/sensitivity-model-settings.png)

2. W **okienku Ustawienia** modelu w sekcji  Zgodność **wybierz menu** Etykieta wrażliwości, aby wyświetlić listę dostępnych etykiet wrażliwości, które możesz zastosować do modelu.

   ![Zrzut ekranu przedstawiający okienko Ustawienia modelu z menu etykiet wrażliwości.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. Wybierz etykietę wrażliwości, którą chcesz zastosować do modelu, a następnie wybierz pozycję **Zapisz**.

Po zastosowaniu etykiety wrażliwości do modelu możesz zastosować ją do:

- Nowa biblioteka dokumentów
- Biblioteka dokumentów, do której został już zastosowany model
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Stosowanie etykiety wrażliwości do biblioteki dokumentów, do której został już zastosowany model

Jeśli model rozumienia dokumentu został już zastosowany do biblioteki dokumentów, możesz wykonać następujące czynności w celu zsynchronizowania aktualizacji etykiet wrażliwości w celu zastosowania go do biblioteki dokumentów:

1. Na stronie głównej modelu w sekcji **Biblioteki z tym modelem** wybierz bibliotekę dokumentów, do której chcesz zastosować aktualizację etykiety wrażliwości.

2. Wybierz **pozycję Synchronizuj**.

   ![Zrzut ekranu przedstawiający biblioteki z sekcją tego modelu z wyróżniona synchronizować.](../media/content-understanding/sensitivity-libraries-sync.png)

Po zastosowaniu aktualizacji i zsynchronizowaniu jej z modelem możesz potwierdzić jej zastosowanie, wykonując następujące czynności:

1. W centrum zawartości w sekcji **Biblioteki z tym modelem** wybierz bibliotekę, do której zastosowano zaktualizowany model. 

2. W widoku biblioteki dokumentów wybierz ikonę informacji, aby sprawdzić właściwości modelu.

3. Na liście **Aktywne** modele wybierz zaktualizowany model.

4. W **sekcji Etykieta** wrażliwości zobaczysz nazwę zastosowanej etykiety wrażliwości.

Na stronie widoku modelu w bibliotece dokumentów zostanie wyświetlana **nowa kolumna** etykiety wrażliwości. Gdy model klasyfikuje pliki jako należące do swojego typu zawartości i wyświetla je w widoku biblioteki, w kolumnie Etykieta wrażliwości  będzie również wyświetlana nazwa etykiety wrażliwości, która została do niej zastosowana za pośrednictwem modelu.

Na przykład do wszystkich dokumentów finansowych, które identyfikuje Twój model, zastosowano do nich  etykietę wrażliwości Encryption, aby uniemożliwić dostęp do nich nieautoryzowanym osobom. Jeśli próbowano uzyskać dostęp do pliku z biblioteki dokumentów przez nieautoryzowaną osobę, zostanie wyświetlany komunikat o błędzie z informacją, że nie jest on dozwolony z powodu zastosowanej etykiety wrażliwości.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft 365 Compliance Center](../admin/security-and-compliance/set-up-compliance.md).

You can either apply a sensitivity label to a form processing model when you are creating a model, or apply it to an existing model.

### Add a sensitivity label when you create a form processing model

1. When you [create a new form processing model](create-a-form-processing-model.md), select **Advanced settings**.

2. In **Advanced settings**, in the **Sensitivity label** section, select the menu and then select the sensitivity label you want to apply to the model.

3.  After you've completed your remaining model settings, select **Create** to build your model.

### Add a sensitivity label to an existing form processing model

You can add a sensitivity label to an existing form processing model in different ways:

- Through the **Automate** menu in the document library
- Through the **Active model** settings in the document library 

#### Add a sensitivity label to an existing form processing model through the Automate menu

You can add a sensitivity label to an existing form processing model that you own through the **Automate** menu in the document library in which the model is applied.

1. In your document library to which the form processing model is applied, select the **Automate** menu, select **AI Builder**, and then select **View form processing model details**.

2. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

#### Add a sensitivity label to an existing form processing model in the active model settings

You can add a sensitivity label to an existing form processing model that you own through the **Active model** settings in the document library in which the model is applied.

1. In the SharePoint document library in which the model is applied, select the **View active models** icon, and then select **View active models**.

2. In **Active models**, select the form processing model to which you want to apply the sensitivity label.

3. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

   > [!NOTE]
   > You must be the model owner for the **Model settings** pane to be editable. 
--->

## <a name="see-also"></a>Zobacz też

[Stosowanie etykiety przechowywania](apply-a-retention-label-to-a-model.md)

[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)
