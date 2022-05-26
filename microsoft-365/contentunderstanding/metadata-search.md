---
title: Wyszukiwanie metadanych w bibliotekach dokumentów w usłudze Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: kkameth
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: high
description: Dowiedz się, jak używać zaawansowanego wyszukiwania metadanych i wyszukiwać kolumny witryny niestandardowej w celu znajdowania elementów w bibliotekach dokumentów SharePoint przy użyciu SharePoint Syntex.
ms.openlocfilehash: 50b9ef7ff6fe7942266ec59f8d5ad81e0dfbecd4
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679576"
---
# <a name="search-for-metadata-in-document-libraries-in-microsoft-sharepoint-syntex"></a>Wyszukiwanie metadanych w bibliotekach dokumentów w usłudze Microsoft SharePoint Syntex

Funkcja zaawansowanego wyszukiwania metadanych w SharePoint Syntex umożliwia wykonywanie określonych zapytań opartych na metadanych w bibliotekach dokumentów SharePoint. Można wykonywać szybsze i bardziej precyzyjne zapytania na podstawie określonych wartości kolumn metadanych, a nie tylko wyszukiwać słowa kluczowe.

Zaawansowane wyszukiwanie metadanych umożliwia użycie metadanych skojarzonych z dokumentem w celu znalezienia pliku w bibliotece dokumentów SharePoint. Ta funkcja jest szczególnie przydatna, gdy masz określoną informację, której chcesz wyszukać, na przykład kiedy dokument został ostatnio zmodyfikowany, określona osoba skojarzona z plikiem lub określony typ pliku.

> [!NOTE]
> Ta funkcja jest dostępna tylko dla użytkowników, którzy mają licencję na SharePoint Syntex. 

## <a name="to-use-advanced-metadata-search"></a>Aby użyć zaawansowanego wyszukiwania metadanych

1. W bibliotece dokumentów SharePoint w polu **Wyszukaj w tej bibliotece** wybierz ikonę wyszukiwania metadanych (![zrzut ekranu przedstawiający ikonę wyszukiwania metadanych).](../media/content-understanding/metadata-search-icon.png)

    ![Zrzut ekranu przedstawiający stronę biblioteki dokumentów pokazującą pole wyszukiwania z wyróżnioną ikoną wyszukiwania metadanych.](../media/content-understanding/metadata-search-box.png)

2. W okienku wyszukiwania metadanych wpisz tekst lub wybierz parametr, który chcesz znaleźć w co najmniej jednym polu wyszukiwania.

    ![Zrzut ekranu przedstawiający stronę biblioteki dokumentów z okienkiem wyszukiwania metadanych.](../media/content-understanding/metadata-search-pane.png)

   Następujące pola wyszukiwania metadanych są obecnie dostępne. Więcej pól zostanie dodanych w przyszłości.

   |Pole    |Użyj tego pola do  |
   |---------|---------|
   |Słowa kluczowe |Wyszukaj dopasowanie ciągu w metadanych lub w pełnym tekście dokumentu. |
   |Nazwa pliku     |Wyszukaj w kolumnie **Nazwa** w bibliotece.          |
   |Ludzi   |Wyszukaj dopasowanie dla osób w dowolnej kolumnie w bibliotece.   |
   |Data modyfikacji |Wyszukaj według wybranego zakresu dat w kolumnie **Zmodyfikowane** w bibliotece.         |
   |Typ pliku     |Wyszukaj według wybranego typu pliku (na przykład dokumentu programu Word lub pliku PDF).        |
   |Typ zawartości  |Wyszukaj według wybranego typu zawartości. Ta opcja będzie wyświetlana tylko wtedy, gdy do biblioteki jest zastosowany inny niż domyślny typ zawartości. Domyślne typy zawartości to *dokument* i *folder*.        |

3. Możesz również wyszukać niestandardowe kolumny witryny, które znajdują się w bieżącym widoku biblioteki. Jest to szczególnie przydatne w przypadku modelu uruchomionego w bibliotece, ponieważ wyodrębniarki metadanych automatycznie wypełniają informacje do kolumn lokacji.  

    Aby dodać kolumnę witryny niestandardowej do wyszukiwania, wybierz pozycję **Dodaj więcej opcji**, a następnie wybierz nazwę kolumny witryny.

    ![Zrzut ekranu przedstawiający menu Dodaj więcej opcji w okienku wyszukiwania metadanych.](../media/content-understanding/metadata-search-add-more-options.png)

4. Wybierz pozycję **Wyszukaj**. Dokumenty zgodne z wyszukiwaniem metadanych są wyświetlane na stronie wyników. 
