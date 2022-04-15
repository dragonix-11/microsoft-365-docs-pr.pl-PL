---
title: Duplikowanie modelu w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak i dlaczego zduplikować model zrozumienia dokumentów w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: 56e05389cad4ad9010324a3efd48bf679700be76
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882247"
---
# <a name="duplicate-a-model-in-microsoft-sharepoint-syntex"></a>Duplikowanie modelu w usłudze Microsoft SharePoint Syntex

Duplikowanie modelu zrozumienia dokumentów może zaoszczędzić czas i nakład pracy, jeśli trzeba utworzyć nowy model, i wiedzieć, że istniejący model jest bardzo podobny do tego, czego potrzebujesz.

Na przykład istniejący model o nazwie "Contracts" klasyfikuje te same pliki, z których musisz pracować. Nowy model wyodrębni niektóre z istniejących danych, ale będzie musiał zostać zaktualizowany w celu wyodrębnienia dodatkowych danych. Zamiast tworzyć i trenować nowy model od podstaw, można użyć funkcji zduplikowanego modelu, aby utworzyć kopię modelu Contracts, który będzie również kopiować wszystkie skojarzone elementy trenowania, takie jak przykładowe pliki i wyodrębniacze jednostek.

Po zduplikowaniu modelu po zmianie jego nazwy (na przykład na wartość "Odnowienia kontraktu") możesz wprowadzić do niego aktualizacje. Możesz na przykład usunąć niektóre z istniejących pól wyodrębnionych, które nie są potrzebne, a następnie wytrenować model w celu wyodrębnienia nowego (na przykład "Data odnowienia").

## <a name="duplicate-a-model"></a>Duplikowanie modelu

Wykonaj następujące kroki, aby zduplikować model zrozumienia dokumentu.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.

2. Na stronie **Modele** wybierz model, który chcesz zduplikować.

3. Używając wstążki lub przycisku **Pokaż akcje** (obok nazwy modelu), wybierz pozycję **Duplikuj**.</br>

    ![Zrzut ekranu przedstawiający stronę Modele przedstawiającą wybrany model z wyróżnionymi opcjami Duplikuj.](../media/content-understanding/select-model-duplicate-both.png) </br>

4. Na panelu **Duplikuj model** :

   a. W obszarze **Nazwa** wprowadź nową nazwę modelu, który chcesz zduplikować.</br>

    ![Zrzut ekranu przedstawiający panel Duplikuj model.](../media/content-understanding/duplicate-model-panel.png) </br>

   b. W obszarze **Opis** dodaj opis nowego modelu.

   c. (Opcjonalnie) W obszarze **Ustawienia zaawansowane** wybierz, czy chcesz skojarzyć istniejący [typ zawartości](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview).

5. Wybierz pozycję **Duplikuj**.

## <a name="see-also"></a>Zobacz też

[Tworzenie klasyfikatora](create-a-classifier.md)

[Zmienianie nazwy modelu](rename-a-model.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)

[Typy wyjaśnień](explanation-types-overview.md)

[Stosowanie modelu](apply-a-model.md) 

[tryb ułatwień dostępu SharePoint Syntex](accessibility-mode.md)