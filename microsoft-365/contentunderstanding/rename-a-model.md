---
title: Zmienianie nazwy modelu w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak i dlaczego zmienić nazwę modelu zrozumienia dokumentu w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: 0044b237705e6a716efb6133db392c68b82c7a25
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916144"
---
# <a name="rename-a-model-in-microsoft-sharepoint-syntex"></a>Zmienianie nazwy modelu w usłudze Microsoft SharePoint Syntex

W pewnym momencie możesz zmienić nazwę modelu zrozumienia dokumentu. Typowym przykładem jest utworzenie początkowej wersji roboczej modelu. Być może nie trzeba było myśleć o ostatecznej nazwie (na przykład nazwa została nazwana "AlexWilburModel1"). Gdy zbliżasz się do sfinalizowania modelu i wprowadzenia go do użycia, zdajesz sobie sprawę, że bardziej właściwą nazwą będą "Odnowienia kontraktów" i chcesz zmienić jego nazwę.  

Innym przykładem jest podjęcie przez organizację decyzji o odwołaniu się do typu procesu lub dokumentu pod inną nazwą. Na przykład po utworzeniu modelu i przygotowaniu go do jego zastosowania organizacja może nakazać, aby wszystkie "kontrakty" były teraz formalnie nazywane "umowami". W razie potrzeby możesz zmienić nazwę modelu z "Odnowienia kontraktu" na "Odnowienia umowy".

> [!IMPORTANT]
> Nazwę modelu interpretacji dokumentów można zmienić tylko wtedy, gdy nie został on zastosowany do biblioteki dokumentów. 

Zmiana nazwy modelu powoduje również zmianę [nazwy typu zawartości](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) skojarzonego z modelem.

## <a name="rename-a-model"></a>Zmienianie nazwy modelu

Wykonaj następujące kroki, aby zmienić nazwę modelu zrozumienia dokumentu.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.

2. Na stronie **Modele** wybierz model, który chcesz zmienić.

3. Za pomocą wstążki lub przycisku **Pokaż akcje** (obok nazwy modelu) wybierz pozycję **Zmień nazwę**. </br>

    ![Zrzut ekranu przedstawiający stronę Modele z wyróżnionymi opcjami Zmień nazwę wybranego modelu.](../media/content-understanding/select-model-rename-both.png) </br>

4. Na panelu **Zmień nazwę modelu** :

   a. W obszarze **Nowa nazwa** wprowadź nową nazwę modelu, którego nazwę chcesz zmienić.</br>

    ![Zrzut ekranu przedstawiający panel Zmienianie nazwy modelu.](../media/content-understanding/rename-model-panel.png) </br>

   b. (Opcjonalnie) W obszarze **Ustawienia zaawansowane** wybierz, czy chcesz skojarzyć istniejący [typ zawartości](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview). Jeśli **wybierzesz pozycję Użyj istniejącego typu zawartości**, nazwa modelu zostanie zmieniona tak, aby był zgodny z wybranym typem zawartości.

5. Wybierz pozycję **Zmień nazwę**.

## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Zmienianie nazwy wyodrębniacza](rename-an-extractor.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)

[Typy wyjaśnień](explanation-types-overview.md)

[Stosowanie modelu](apply-a-model.md) 
