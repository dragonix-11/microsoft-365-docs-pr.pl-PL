---
title: Predykcyjne informacje o kodowaniu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: ''
ms.openlocfilehash: ff681793a86d9953088c2c4da65553e1d2c54d22
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985635"
---
# <a name="predictive-coding-reference-preview"></a>Predykcyjne wskazówki kodowania (podgląd)

W tym artykule opisano kluczowe pojęcia i metryki narzędzia do predykcyjnego kodowania w programie Advanced eDiscovery. Sekcje w artykule są wyświetlane w kolejności alfabetycznej.

## <a name="confidence-level"></a>Poziom ufności

Poziom ufności jest zaawansowanym ustawieniem podczas tworzenia modelu predykcyjnego kodowania. Zdefiniowano w nim, że metryki wydajności modelu (na przykład rozbudowa, dokładność i odwołanie) należą do określonego zakresu (określonego dla modelu jako marginesu błędu), który jest reprezentatywny dla prawdziwych wartości wyników prognozy przypisywanych przez model elementom w zestawie recenzji. Wartości poziomu ufności i marginesu błędu ułatwiają również określenie, ile elementów znajduje się w zestawie kontrolek. Wartość domyślna poziomu ufności to 0,95 czyli 95%.

## <a name="control-set"></a>Zestaw kontrolek

Zestaw kontrolek jest używany w procesie szkolenia modelu predykcyjnego kodowania. Zestaw kontrolek umożliwia ocenę wyników prognozy przypisywanych przez model elementom z etykietami, które wykonuje się podczas zaokrągleń szkoleniowych. Rozmiar zestawu kontrolek jest oparty na liczbie elementów w zestawie recenzji oraz poziomie ufności i marginesie wartości błędów ustawianych podczas tworzenia modelu. Elementy w zestawie kontrolek nigdy się nie zmieniają i nie są identyfikowalne do zidentyfikowania dla użytkowników. Łączna liczba elementów w zestawie kontrolek jest wyświetlana na stronie wysuwana w celu zaokrąglenia szkolenia.

## <a name="control-set-confusion-matrix"></a>Macierz nieporozumień zestawu kontrolek

Po zakończeniu rundy szkolenia model przypisuje wynik prognozowania do 10 elementów w zestawie kontrolek oznaczonych podczas rundy szkolenia. Ten model porównuje wynik prognozowania tych 10 elementów z rzeczywistą etykietą przypisaną do elementu podczas rundy szkolenia. Na podstawie tego porównania w modelu są identyfikowane następujące klasyfikacje do oceny wydajności prognozowania modelu:

<br>

****

|Etykieta|Model przewiduje, że element jest istotny|Model przewiduje element nie jest odpowiedni|
|---|---|---|
|**Recenzent etykietuje element jako odpowiedni**|True positive|Wynik fałszywie dodatni|
|**Recenzent etykietuje element jako nieucztowy**|Wynik fałszywie ujemny|True negative|
|

Na podstawie tych porównań model pozysł wartości dla wyników F-score, dokładności i odwołania oraz marginesu błędu dla każdej z nich. Liczba typów nieporozumień w macierzy jest wyświetlana na stronie wysuwu w celu zaokrąglenia szkolenia.

## <a name="f-score"></a>Wynik F

Wynik F jest średnią ważoną wyników dla metryk dokładności i odwołania.  Zakres wyników dla tej metryki wynosi od **0** do **1**. Wynik bliższy **1** oznacza, że model dokładniej wykrywa odpowiednie elementy. Metryka wyniku F jest wyświetlana na pulpicie nawigacyjnym modelu oraz na wysuwanych stronie dla każdego rundy szkolenia.

## <a name="margin-of-error"></a>Margines błędu

Margines błędu jest zaawansowanym ustawieniem podczas tworzenia trybu predykcyjnego kodowania. Określa stopień błędu w metrykach wydajności (na przykład dokładność, dokładność i odwołanie) wynikających z losowej próbki elementów w zestawie kontrolek. Dolna marża błędu wymaga większego zestawu kontrolek w celu zapewnienia, że metryki wydajności modelu będą wchodzić w zakres mniejszego zakresu. Wartości marginesu błędu i poziomu ufności pomagają także określić, ile elementów jest zawartych w zestawie kontrolek. Wartość domyślna marginesu błędu wynosi 0,05 lub 5%.

## <a name="model-stability"></a>Stabilność modelu

Stabilność modelu wskazuje możliwość dokładnego przewidzenia, czy dokument w zestawie recenzji jest istotny, czy nie. Gdy model jest niestabilny, może być konieczne więcej rund szkoleniowych, aby uwzględnić stabilność modelu. Gdy model jest stabilny, może nie być konieczne więcej zaokrągleń szkoleniowych. Pulpit nawigacyjny modelu wskazuje bieżący stan stabilności modelu. Gdy model jest stabilny, metryki wydajności osiągną poziom, który odpowiada poziomowi ufności i marginesowi błędu.

## <a name="overturn-rate"></a>Szybkość przewrócenia

Stopa przewrócenia to procent pozycji w zestawie recenzji, w którym wynik prognozowania zmienia się między zaokrągleniami szkolenia. Model jest stabilny, gdy szybkość przekręcenia wynosi poniżej 5%. Metryka szybkości przewrócenia jest wyświetlana na pulpicie nawigacyjnym modelu oraz na wysuwanych stronie dla każdego rundy szkolenia. Szybkość przewrócenia w pierwszej zaokrąglonym szkoleniu wynosi zero, ponieważ nie ma poprzedniego wyniku prognozy przewracenia.

## <a name="precision"></a>Dokładność

Metryka precyzji mierzy proporcje elementów, które w rzeczywistości są istotne między elementami prognozowany model, były istotne. Oznacza to, że elementy w kontrolce, w których etykieta będzie odpowiedni dla recenzenta i przewidywana jako mająca znaczenie dla modelu. Zakres wyników dla tej metryki wynosi od **0** do **1**. Wynik bliższy **1** oznacza, że model zidentyfikuje mniej elementów nieistnieżnych. Metryka dokładności jest wyświetlana na pulpicie nawigacyjnym modelu oraz na wysuwanych stronie dla każdego rundy szkolenia.

## <a name="prediction-score"></a>Wynik prognozowania

Jest to wynik przypisywany przez model każdemu dokumentowi w zestawie recenzji. Wynik jest oparty na istotności dokumentu w porównaniu z wynikami rundy szkoleń opartymi na modelu. Ogólnie rzecz biorąc, elementy z wynikami prognozy między **0** a **0,5** są traktowane jako nie istotne, a elementy z wynikami prognozy między **0,5** a **1** są uznawane za istotne. Wynik prognozy znajduje się w polu metadanych dokumentu. Możesz użyć filtru podpowiedniowego, aby wyświetlić elementy w zestawie recenzji, które należą do określonego zakresu podpowiedni.

## <a name="recall"></a>Odwołaj

Metryka odwołania mierzy proporcje przewidywanego modelu między faktycznie odpowiednimi elementami. Oznacza to, że elementy w zestawie kontrolek, w przypadku których przewidywano zastosowanie modelu, były również oznaczone jako istotne przez recenzenta. Zakres wyników dla tej metryki wynosi od **0** do **1**. Wynik bliższy **1** oznacza, że model zidentyfikuje większą część odpowiednich elementów. Metryka odwołania jest wyświetlana na pulpicie nawigacyjnym modelu oraz na wysuwanej stronie dla każdego rundy szkolenia.

## <a name="review-set"></a>Zestaw recenzji

Zestaw recenzji zawiera zakres modelu predykcyjnego kodowania. Podczas tworzenia nowego modelu dla zestawu recenzji elementy zestawu kontrolek i zestawów szkoleniowych są wybierane z zestawu recenzji. Gdy model przypisuje wyniki prognozowania, przypisuje te wyniki elementom w recenzji. Przed utworzeniem modelu predykcyjnego kodowania należy dodać wszystkie elementy do zestawu recenzji. W przypadku dodania elementów po utworzeniu modelu nie zostaną one przypisane do wyników prognozy.

## <a name="richness"></a>Rwęczność

Metryka rozbudowy mierzy procent przeglądanych elementów zestawu elementów, które model przewiduje jako istotne. Zakres wyników dla tej metryki wynosi od **0** do **1**. Metryka rozbudowy jest wyświetlana na pulpicie nawigacyjnym modelu.

## <a name="sampled-items"></a>Przykładowe elementy

Termin " *próbkowane* elementy" jest odwołaniem do losowych próbek elementów w zestawie recenzji (zawierających tekst), które są wybrane i skojarzone z zestawem kontrolek podczas tworzenia modelu predykcyjnego kodowania. Dla każdego rundy szkolenia jest również wybrana losowa próbka elementów. Elementy wybrane dla zestawu kontrolek modelu nie są uwzględniane w zestawie szkoleniowym dla tego samego modelu. Jest też odwrotnie: elementy zestawu szkoleń nie są nigdy uwzględniane w zestawie kontrolek.

## <a name="training-set"></a>Zestaw szkoleniowy

Model losowo wybiera elementy z zestawu recenzji i dodaje je do zestawu szkoleniowego. Podczas rundy szkolenia przedstawiane są elementy z zestawu szkoleniowego (oprócz elementów z zestawu kontrolek), dzięki czemu można oznaczać każdy z nich jako "odpowiedni" lub "nie istotny". Ten proces oznaczania etykietami lub "szkolenia" ułatwia modelowi sprawdzenie, jak można przewidywać, które elementy recenzji są istotne, czy nie. Za każdym razem, gdy przeprowadzasz rundę szkolenia, model wybiera więcej elementów z recenzji i dodaje je do zestawu szkoleniowego dla tego rundy. Elementy z zestawu kontrolek nie są nigdy wybierane dla zestawu szkoleniowego.
