---
title: Zmienianie nazwy wyodrębnianego pliku w aplikacji Microsoft SharePoint Syntex
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
description: Dowiedz się, jak i dlaczego należy zmienić nazwę wyodrębnianego w programie Microsoft SharePoint Syntex.
ms.openlocfilehash: 0b5c52e00b287b6f4b41e7c8c3070261bccfda96
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986593"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>Zmienianie nazwy wyodrębnianego pliku w aplikacji Microsoft SharePoint Syntex

W pewnym momencie może być konieczne zmiana nazwy wyodrębnianego pola, jeśli chcesz odwołać się do wyodrębnionego pola danych pod inną nazwą. Na przykład twoja organizacja decyduje się wprowadzać zmiany w swoich dokumentach kontraktowych i określa w dokumentach klientów jako "klientów". Jeśli wyodrębniono w modelu pole "Klient", możesz zmienić jego nazwę na "Klient".

Po zsynchronizowaniu zaktualizowanego modelu z biblioteką SharePoint dokumentów zobaczysz nową kolumnę "Klient" w widoku biblioteki dokumentów. Widok zachowa kolumnę "Klient" dla działań w przeszłości, ale zaktualizuje nową kolumnę "Klient" dla wszystkich nowych dokumentów, które są przetwarzane przez Model. 

> [!IMPORTANT]
>  Pamiętaj o zsynchronizowaniu zaktualizowanego modelu z bibliotekami dokumentów w miejscach, w których został poprzednio zastosowany, aby była wyświetlana nazwa nowej kolumny. 

## <a name="rename-an-extractor"></a>Zmienianie nazwy wyodrębnianego

Wykonaj poniższe czynności, aby zmienić nazwę wyodrębniaka encji.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.

2. Na stronie **Modele** w kolumnie **Nazwa** wybierz model, którego nazwę chcesz zmienić.

3. W **obszarze Wyodrębniacze encja** wybierz nazwę wyodrębniaczy, którego nazwę chcesz zmienić, a następnie wybierz pozycję Zmień **nazwę**.</br>

    ![Zrzut ekranu przedstawiający sekcję Wyodrębniacze encja-wyodrębnianie z wyróżnionym wybranym wyodrębniaczem i opcją Zmień nazwę.](../media/content-understanding/entity-extractor-rename.png) </br>

4. Na **panelu Zmień nazwę jednostki wyodrębniającego** :

   a. W **obszarze Nowa** nazwa wprowadź nową nazwę wyodrębnianego.</br>

    ![Zrzut ekranu przedstawiający panel Wyodrębnianie jednostki.](../media/content-understanding/rename-entity-extractor-panel.png) </br>

   b. (Opcjonalnie) W **obszarze Ustawienia zaawansowane** określ, czy chcesz skojarzyć istniejącą kolumnę witryny.

5. Wybierz **pozycję Zmień nazwę**.

## <a name="see-also"></a>Zobacz też
[Tworzenie wyodrębnianego](create-an-extractor.md)

[Tworzenie klasyfikatora](create-a-classifier.md)

[Zmienianie nazwy modelu](rename-a-model.md)

[Typy objaśnień](explanation-types-overview.md)

[Korzystanie z taksonomii magazynu terminów podczas tworzenia wyodrębnianego](leverage-term-store-taxonomy.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Stosowanie modelu](apply-a-model.md) 
