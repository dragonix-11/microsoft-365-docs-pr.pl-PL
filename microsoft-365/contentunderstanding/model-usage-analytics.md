---
title: Dokument opis analizy użycia modelu w aplikacji Microsoft SharePoint Syntex
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
description: Dowiedz się, jak znaleźć i używać analizy użycia w modelu zrozumienia dokumentu.
ms.openlocfilehash: 3dd77f760f70812045841ab56afbb13b02044d91
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987804"
---
# <a name="document-understanding-model-usage-analytics-in-microsoft-sharepoint-syntex"></a>Dokument opis analizy użycia modelu w aplikacji Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


Centrum SharePoint Syntex udostępnia analizę użycia modelu, aby uzyskać więcej informacji na temat używania modeli opublikowanych w centrum zawartości. Sekcja <b>Jak działa Twoje</b> modele w centrum zawartości z ostatnich 30 dni zawiera 30-dniowe zestawienia danych analizy użycia dostępne na następujących wykresach i listach:

- Klasyfikacja według modelu
- Klasyfikacja według biblioteki
- Użycie modelu 

 ![Analiza modelu.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Rzutowanie danych użycia modelu w domyślnym centrum zawartości

W SharePoint Syntex konfiguracyjną tworzona jest domyślna zawartość centrum zawartości. Można również utworzyć dodatkowe centra zawartości zgodnie z potrzebami. Na przykład działy mogą tworzyć własne centra zawartości, aby tworzyć modele i zarządzać nimi. 

W odniesieniu do analizy użycia modelu należy zwrócić uwagę, że:

- W domyślnym centrum zawartości będą wyświetlane analizy użycia modelu dla wszystkich centrów zawartości i modeli w organizacji, również tych utworzonych w dodatkowych centrach zawartości. Dzięki temu menedżerowie zawartości i inni uczestnicy projektu mogą scentralizowany portal zarządzać centrami zawartości i modelami w całej firmie i nadzorować je.  
- W innych centrach zawartości będą wyświetlane tylko analizy użycia modelu dla utworzonych w nich modeli. Dzięki temu menedżerowie zawartości mogą uzyskać szczegółowe informacje na temat danych dotyczących użycia tylko tych modeli, których dotyczą.


## <a name="classification-by-model"></a>Klasyfikacja według modelu

   ![Łączna wartość procentowa modelu.](../media/content-understanding/total-model-percentage.png) </br>

Na **wykresie kołowym** Klasyfikacja według modelu są wyświetlane modele, w których sklasyfikowano najwięcej plików. Przedstawia on każdy opublikowany model jako procent wszystkich plików przetwarzanych przez wszystkie modele opublikowane w centrum zawartości.

W każdym modelu jest też **pokazana szybkość kompletności**, czyli procent przekazanych plików, które zostały pomyślnie przeanalizowane przez model. Niska szybkość kompletności może oznaczać, że występują problemy z modelem lub plikami, które są analizowane.

## <a name="classification-by-library"></a>Klasyfikacja według biblioteki

   ![Pliki przetwarzane.](../media/content-understanding/files-processed-over-time.png) </br>

Wykres **słupkowy Klasyfikacja** według biblioteki pomaga w określeniu skuteczności zrozumienia zawartości w organizacji.  Pokazuje on nie tylko liczbę plików przetwarzanych w czasie dla każdego modelu, ale także przez wybranie kolumny na wykresie, co spowoduje również pokazanie bibliotek dokumentów, do których zastosowano model.


## <a name="model-usage"></a>Użycie modelu

Na liście Użycie modelu zostaną wyświetlona analiza użycia dla modeli utworzonych za pośrednictwem centrum zawartości.  

> [!NOTE]
> Jeśli korzystasz z domyślnego centrum zawartości i masz dodatkowe centra zawartości w organizacji, lista użycia modelu zostanie pogrupowana według centrum zawartości.

Na liście użycia każdego modelu będą wyświetlane dane użycia:

- Liczba sklasyfikowanych elementów: liczba plików przetwarzanych przez model.
- Średnia ocena ufności: Średnia dokładność modelu podczas uruchamiania na plikach.
- Adres URL listy docelowej: SharePoint biblioteki dokumentów, do której został zastosowany model.



## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)  
