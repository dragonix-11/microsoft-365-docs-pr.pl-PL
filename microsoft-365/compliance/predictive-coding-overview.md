---
title: Moduł predykcyjnego Advanced eDiscovery (wersja zapoznawcza)
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
description: Nowy moduł predykcyjnego kodowania w programie Advanced eDiscovery używa uczenia maszynowego do analizowania elementów w zestawie recenzji, aby podpowiądać, które elementy są istotne dla danej sprawy lub badania.
ms.openlocfilehash: 60f0fc2f53c8bfbde2a4a1d5cccb4eb678f7c33e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985105"
---
# <a name="learn-about-predictive-coding-in-advanced-ediscovery-preview"></a>Dowiedz się więcej na temat predykcyjnego Advanced eDiscovery (wersja zapoznawcza)

Moduł predykcyjnego kodowania Advanced eDiscovery korzysta z inteligentnych funkcji uczenia maszynowego, które ułatwiają zmniejszenie ilości zawartości do przejrzenia. Kodowanie podpowiedniowe pomaga zmniejszyć i pomylić duże ilości zawartości sprawy do odpowiedniego zestawu elementów, dla których można ustalić priorytety. Jest to możliwe dzięki utworzeniu i szkoleniu własnych modeli predykcyjnego kodowania, które ułatwiają określanie priorytetów przeglądu najbardziej istotnych elementów w zestawie recenzji.

Moduł predykcyjnego kodowania został zaprojektowany w celu usprawnienia złożoności zarządzania modelem w zestawie recenzji i oferuje iteracyjne podejście do szkolenia modelu, dzięki czemu można szybciej rozpocząć pracę z funkcjami uczenia maszynowego w programie Advanced eDiscovery. Aby rozpocząć, możesz utworzyć model i dodać etykietę do zaledwie 50 elementów jako odpowiednich lub nie istotnych. System używa tego szkolenia do stosowania wyników prognozowania do wszystkich elementów w zestawie recenzji. Umożliwia to filtrowanie elementów na podstawie wyników prognozy, dzięki którym można najpierw przejrzeć najbardziej istotne (lub nieistome) elementy. Jeśli chcesz przeszkolić modele z większą dokładnością i stawkami odwołania, możesz kontynuować znakowanie elementów podczas kolejnych szkoleń do momentu stabilizacji modelu.  

## <a name="the-predictive-coding-workflow"></a>Przepływ pracy predykcyjnego kodowania

Oto omówienie i opis przepływu pracy predykcyjnego kodowania kroków. Aby uzyskać bardziej szczegółowy opis pojęć i terminologii procesu predykcyjnego kodowania, zobacz [Predykcyjne informacje o kodowaniu](predictive-coding-reference.md).

![Predykcyjne kodowanie przepływu pracy.](..\media\PredictiveCodingWorkflow.png)

1. **Utwórz nowy model predykcyjnego kodowania w zestawie recenzji**. Pierwszym krokiem jest utworzenie nowego modelu predykcyjnego kodowania w zestawie recenzji. Aby utworzyć model, w zestawie recenzji musi być co najmniej 2000 elementów. Po utworzeniu modelu system określi liczbę elementów do użycia jako *zestawu kontrolek*. Zestaw kontrolek jest używany w trakcie procesu szkoleniowego do oceny wyników prognozy przypisywanych przez model elementom z etykietami, które wykonuje się podczas zaokrągleń szkoleń. Rozmiar zestawu kontrolek jest oparty na liczbie elementów w zestawie recenzji oraz poziomie ufności i marginesie wartości błędów ustawianych podczas tworzenia modelu. Elementy w zestawie kontrolek nigdy się nie zmieniają i nie są identyfikowalne do zidentyfikowania dla użytkowników.

   Aby uzyskać więcej informacji, zobacz [Tworzenie modelu predykcyjnego kodowania](predictive-coding-create-model.md).

2. **Ukończ pierwszą rundę szkolenia, oznaczając elementy jako istotne lub nieumiejętne**. Następnym krokiem jest przeszkolenie modelu przez rozpoczęcie pierwszej rundy szkolenia. Po rozpoczęciu rundy szkolenia model losowo wybiera dodatkowe elementy z zestawu recenzji, który jest *nazywany zestawem szkoleniowym*. Te elementy (zarówno z zestawu kontrolek, jak i zestawu szkoleniowego) są przedstawiane, dzięki czemu możesz oznaczać każdy z nich jako "odpowiedni" lub "nie istotny". Istotność jest oparta na zawartości elementu, a nie na metadanych dokumentu. Po zakończeniu procesu oznaczania etykiet w trakcie rundy szkolenia model zostanie "uczony" na podstawie sposobu, w jaki oznaczono elementy w zestawie szkoleniowym. Na podstawie tego szkolenia model będzie przetwarzać elementy w zestawie recenzji i stosować do każdego z nich wynik prognozowania.

   Aby uzyskać więcej informacji, zobacz [Szkolenie modelu predykcyjnego kodowania](predictive-coding-train-model.md).

3. **Zastosuj filtr wyników prognozy do elementów w zestawie recenzji**. Kolejnym krokiem po zakończeniu poprzedniego kroku szkoleniowego jest zastosowanie filtru wyników prognozy do elementów przeglądanych w celu wyświetlenia elementów, które określono jako najbardziej istotne dla modelu (można również użyć filtru prognozowania w celu wyświetlania elementów, które są "nie istotne"). Po zastosowaniu filtru podpowiedzy określa się zakres wyników podpowiedni, który ma być filtrowany. Zakres wyników prognozy należy do przedziału od **0** do **1**, przy tym **0** jest "nieo znaczenia", a **1 jest** istotne. Ogólnie rzecz biorąc, elementy z wynikami prognozy między **0** a **0,5** są traktowane jako nie istotne, a elementy z wynikami prognozy między **0,5** a **1** są uznawane za istotne.

   Aby uzyskać więcej informacji, zobacz [Stosowanie filtru podpowiedzy do zestawu recenzji](predictive-coding-apply-prediction-filter.md).

4. **Wykonaj więcej szkoleń do momentu stabilizacji modelu**. Aby utworzyć model z większą dokładnością podpowiedni i zwiększyć wskaźniki odwołania, można wykonać dodatkowe rundy szkoleń. *Wskaźnik odwołania* mierzy proporcje przewidywanych elementów modelu między faktycznie odpowiednimi elementami (te, które zostały oznaczone jako istotne podczas szkolenia). Wynik odwołania wynosi od **0** do **1**. Wynik bliższy **1** oznacza, że model zidentyfikuje bardziej istotne elementy. Podczas nowego rundy szkolenia możesz o etykiecie dodatkowych elementów w nowym zestawie szkoleniowym. Po zakończeniu tego rundy szkolenia model jest aktualizowany na podstawie nowych informacji z najnowszej rundy z elementów oznaczonych etykietami w zestawie szkoleń. Model ponownie przetnie elementy w zestawie recenzji i zastosuje nowe wyniki prognozowania. Możesz kontynuować wykonywanie zaokrągleń szkoleń do momentu stabilizacji modelu. Model jest uznawany za stabilizację, gdy stopa zasobów po ostatniej rundy szkolenia jest mniejsza niż 5%. *Stopa churn* jest definiowana jako procent elementów w zestawie recenzji, gdzie wynik prognozowania zmienia się między zaokrąglami szkolenia. Na pulpicie nawigacyjnym kodu predykcyjnego są wyświetlane informacje i statystyki, które ułatwiają ocenę stabilności modelu.

5. **Stosowanie filtru wyników prognozy "końcowej" w celu przeglądania elementów, dla których ma być priorytetyzowane.** Po zakończeniu wszystkich szkoleń i stabilizacji modelu ostatnim krokiem jest zastosowanie ostatecznego wyniku prognozy do zestawu recenzji w celu priorytetyzowania przeglądu odpowiednich i nieistnieżnych elementów. To samo zadanie, które wykonano w kroku 3, ale na tym etapie model jest stabilny i nie planujesz kolejnych rund szkoleniowych.
