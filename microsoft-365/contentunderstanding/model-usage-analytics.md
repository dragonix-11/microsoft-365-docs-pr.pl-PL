---
title: Analizowanie sposobu użycia modeli w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak znaleźć więcej informacji na temat sposobu działania modeli interpretacji dokumentów i przetwarzania formularzy.
ms.openlocfilehash: e9586bbbd8510611747b81424f1fbe494f212cc5
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916188"
---
# <a name="analyze-how-your-models-are-used-in-microsoft-sharepoint-syntex"></a>Analizowanie sposobu użycia modeli w usłudze Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


Centrum zawartości SharePoint Syntex udostępnia analizę użycia modelu, aby uzyskać więcej informacji na temat sposobu używania modeli opublikowanych w centrum zawartości. Sekcja <b>Jak działają modele w ciągu ostatnich 30 dni</b> w centrum zawartości zawiera 30-dniowe zestawienie danych analizy użycia podanych na następujących wykresach i listach:

- Klasyfikacja według modelu
- Klasyfikacja według biblioteki
- Użycie modelu 

 ![Analiza modelu.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Zestawienie danych użycia modelu w domyślnym centrum zawartości

W SharePoint Syntex domyślne centrum zawartości jest tworzone podczas instalacji. W razie potrzeby można również utworzyć dodatkowe centra zawartości. Na przykład działy mogą tworzyć własne centra zawartości w celu tworzenia modeli i zarządzania nimi. 

W odniesieniu do analizy użycia modelu należy pamiętać, że:

- Domyślne centrum zawartości wyświetli analizę użycia modelu dla wszystkich centrów zawartości i modeli w organizacji, w tym tych utworzonych w dodatkowych centrach zawartości. Dzięki temu menedżerowie zawartości i inni uczestnicy projektu mają scentralizowany portal do zarządzania centrami zawartości i modelami w całej firmie oraz nadzorowania ich.  
- Inne centra zawartości będą pokazywać analizę użycia modelu tylko dla modeli, które zostały w nich utworzone. Daje to menedżerom zawartości wgląd w dane użycia tylko dla modeli, których dotyczą.


## <a name="classification-by-model"></a>Klasyfikacja według modelu

   ![Całkowity procent modelu.](../media/content-understanding/total-model-percentage.png) </br>

Wykres kołowy **Klasyfikacja według modelu** zawiera modele, które sklasyfikowały najwięcej plików. Przedstawia on każdy opublikowany model jako procent wszystkich plików przetworzonych przez wszystkie opublikowane modele w centrum zawartości.

Każdy model pokazuje również **współczynnik kompletności** — procent przekazanych plików, które zostały pomyślnie przeanalizowane przez model. Niski współczynnik kompletności może oznaczać, że występują problemy z modelem lub analizowanymi plikami.

## <a name="classification-by-library"></a>Klasyfikacja według biblioteki

   ![Przetworzone pliki.](../media/content-understanding/files-processed-over-time.png) </br>

Wykres słupkowy **Klasyfikacja według biblioteki** pomaga określić skuteczność zrozumienia zawartości w organizacji.  Pokazuje nie tylko liczbę plików przetworzonych w czasie dla każdego modelu, ale przez wybranie kolumny na wykresie, ale także biblioteki dokumentów, do których został zastosowany model.


## <a name="model-usage"></a>Użycie modelu

Na liście Użycie modelu zostanie wyświetlona analiza użycia modeli utworzonych za pośrednictwem centrum zawartości.  

> [!NOTE]
> Jeśli jesteś w domyślnym centrum zawartości i masz dodatkowe centra zawartości w organizacji, lista użycia modelu zostanie pogrupowana według centrum zawartości.

Każdy model na liście użycia modelu będzie pokazywać dane użycia:

- Liczba sklasyfikowanych elementów: liczba plików przetworzonych przez model.
- Średni wynik ufności: średni wynik dokładności modelu podczas uruchamiania względem plików.
- Adres URL listy docelowej: biblioteka dokumentów SharePoint, do której jest stosowany model.



## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)  
