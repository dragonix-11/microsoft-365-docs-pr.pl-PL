---
title: Zmienianie nazwy wyodrębniacza w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak i dlaczego zmienić nazwę ekstraktora w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: feba0d8850a534e7f5e5d985bf3424f931e0ceb0
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916166"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>Zmienianie nazwy wyodrębniacza w usłudze Microsoft SharePoint Syntex

W pewnym momencie może być konieczne zmianę nazwy ekstraktora, jeśli chcesz odwołać się do wyodrębnionych pól danych pod inną nazwą. Na przykład Twoja organizacja decyduje się na wprowadzenie zmian w dokumentach kontraktowych i w swoich dokumentach określa "klientów" jako "klientów". Jeśli wyodrębniono pole "Klient" w modelu, możesz zmienić jego nazwę na "Klient".

Podczas synchronizowania zaktualizowanego modelu z biblioteką dokumentów SharePoint w widoku biblioteki dokumentów zostanie wyświetlona nowa kolumna "Klient". Widok zachowa kolumnę "Klient" dla poprzednich działań, ale zaktualizuje nową kolumnę "Klient" dla wszystkich nowych dokumentów, które są przetwarzane przez model. 

> [!IMPORTANT]
>  Pamiętaj, aby zsynchronizować zaktualizowany model z bibliotekami dokumentów, w których wcześniej zastosowano go w celu wyświetlenia nowej nazwy kolumny. 

## <a name="rename-an-extractor"></a>Zmienianie nazwy wyodrębniacza

Wykonaj następujące kroki, aby zmienić nazwę wyodrębniacza jednostek.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.

2. Na stronie **Modele** w kolumnie **Nazwa** wybierz model, dla którego chcesz zmienić nazwę ekstraktora.

3. W obszarze **Wyodrębniarki jednostek** wybierz nazwę wyodrębniacza, którego nazwę chcesz zmienić, a następnie wybierz pozycję **Zmień nazwę**.

    ![Zrzut ekranu przedstawiający sekcję Wyodrębniacze jednostek przedstawiającą wybrany wyodrębniacz z wyróżnioną opcją Zmień nazwę.](../media/content-understanding/entity-extractor-rename.png) 

4. Na panelu **Wyodrębnianie jednostki Zmień nazwę** :

   a. W obszarze **Nowa nazwa** wprowadź nową nazwę wyodrębniacza.

    ![Zrzut ekranu przedstawiający panel wyodrębniacz jednostki.](../media/content-understanding/rename-entity-extractor-panel.png) 

   b. (Opcjonalnie) W obszarze **Ustawienia zaawansowane** wybierz, czy chcesz skojarzyć istniejącą kolumnę witryny.

5. Wybierz pozycję **Zmień nazwę**.

## <a name="see-also"></a>Zobacz też
[Tworzenie wyodrębniacza](create-an-extractor.md)

[Tworzenie klasyfikatora](create-a-classifier.md)

[Zmienianie nazwy modelu](rename-a-model.md)

[Typy wyjaśnień](explanation-types-overview.md)

[Korzystanie z taksonomii magazynu terminów podczas tworzenia ekstraktora](leverage-term-store-taxonomy.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)

[Stosowanie modelu](apply-a-model.md) 
