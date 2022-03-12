---
title: Zmienianie nazwy modelu w aplikacji Microsoft SharePoint Syntex
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
description: Dowiedz się, jak i dlaczego należy zmienić nazwę modelu rozumienia dokumentu w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: b1ced765d7a69fdf8b9fe9eb44d6716a840bf8a0
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450300"
---
# <a name="rename-a-model-in-microsoft-sharepoint-syntex"></a>Zmienianie nazwy modelu w aplikacji Microsoft SharePoint Syntex

W pewnym momencie możesz zechcieć zmienić nazwę modelu rozumienia dokumentu. Przykładem typowego przykładu jest utworzenie początkowej wersji roboczej modelu, która może nie przemyślać ostatecznej nazwy (na przykład można ją nazwać "AlexWilburModel1"). Gdy zbliżysz się do sfinalizowania modelu i wprowadzenia go do użycia, uświadomisz sobie, że bardziej odpowiednia nazwa to "Odnowienie umowy", i chcesz zmienić jego nazwę.  

Innym przykładem jest decyzja organizacji, aby odwołać się do procesu lub typu dokumentu pod inną nazwą. Na przykład po utworzeniu modelu i przygotowaniu się do jego zastosowania organizacja może złożyć na użytkownika upoważnienie do formalnego wykluczeniu wszystkich "umów". W razie potrzeby możesz zmienić nazwę modelu z "Odnowienie kontraktu" na "Odnowienie umowy".

> [!IMPORTANT]
> Nazwę modelu rozumienia dokumentu można zmienić tylko wtedy, gdy nie został on zastosowany do biblioteki dokumentów. 

Zmiana nazwy modelu również [zmienia nazwę typu](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) zawartości skojarzonego z modelem.

## <a name="rename-a-model"></a>Zmienianie nazwy modelu

Wykonaj poniższe czynności, aby zmienić nazwę modelu rozumienia dokumentu.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.

2. Na stronie **Modele** wybierz model, którego nazwę chcesz zmienić.

3. Używając wstążki lub przycisku **Pokaż akcje** (obok nazwy modelu), wybierz pozycję **Zmień nazwę**. </br>

    ![Zrzut ekranu przedstawiający stronę Modele z wyróżnionymi opcjami Zmień nazwę wybranego modelu.](../media/content-understanding/select-model-rename-both.png) </br>

4. W **panelu Zmień nazwę** modelu:

   a. W **obszarze Nowa** nazwa wprowadź nową nazwę modelu, którego nazwę chcesz zmienić.</br>

    ![Zrzut ekranu przedstawiający panel Zmień nazwę modelu.](../media/content-understanding/rename-model-panel.png) </br>

   b. (Opcjonalnie) W **obszarze Ustawienia zaawansowane** określ, czy chcesz skojarzyć istniejący [typ zawartości](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview). Jeśli wybierzesz **pozycję Użyj istniejącego typu zawartości**, nazwa modelu zostanie zmieniona, aby dopasować go do wybranego typu zawartości.

5. Wybierz **pozycję Zmień nazwę**.

## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Zmienianie nazwy wyodrębnianego](rename-an-extractor.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Typy objaśnień](explanation-types-overview.md)

[Stosowanie modelu](apply-a-model.md) 
