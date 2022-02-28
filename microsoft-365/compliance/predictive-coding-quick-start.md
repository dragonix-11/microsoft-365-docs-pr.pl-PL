---
title: Predykcyjne kodowanie Advanced eDiscovery — Szybki start
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
description: Dowiedz się, jak rozpocząć korzystanie z modułu predykcyjnego kodowania w programie Advanced eDiscovery. Ten artykuł zawiera omów wszystkie procedury używania predykcyjnego kodowania do identyfikowania zawartości w zestawie recenzji, który jest najbardziej odpowiedni do analizy.
ms.openlocfilehash: 38607459057ff06a2ce74364b752130467deaddd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986653"
---
# <a name="quick-start-predictive-coding-in-advanced-ediscovery-preview"></a>Szybki start: predykcyjne kodowanie w Advanced eDiscovery (wersja zapoznawcza)

Ten artykuł zawiera informacje na temat szybkiego rozpoczynania korzystania z predykcyjnego kodowania w programie Advanced eDiscovery. Moduł predykcyjnego kodowania w programie Advanced eDiscovery korzysta z inteligentnych funkcji uczenia maszynowego w programie Advanced eDiscovery, które ułatwiają zmniejszenie ilości zawartości do przejrzenia. Kodowanie podpowiedniowe pomaga zmniejszyć i pomylić duże ilości zawartości sprawy do odpowiedniego zestawu elementów, dla których można ustalić priorytety. Jest to możliwe dzięki utworzeniu i szkoleniu własnych modeli predykcyjnego kodowania, które ułatwiają określanie priorytetów przeglądu najbardziej istotnych elementów w zestawie recenzji.

Oto krótki przegląd procesu predykcyjnego kodowania:

![Proces Szybki start podpowidania kodu.](..\media\PredictiveCodingQuickStartProcess.png)

Aby rozpocząć, utwórz model i oznacz etykietą aż 50 elementów jako odpowiednie lub nie istotne. Następnie system używa tego szkolenia do stosowania wyników prognozy dla każdego elementu w zestawie recenzji. Umożliwia to filtrowanie elementów na podstawie wyników prognozy, dzięki którym można najpierw przejrzeć najbardziej istotne (lub nieistome) elementy. Jeśli chcesz przeszkolić modele z większą dokładnością i stawkami odwołania, możesz kontynuować znakowanie elementów podczas kolejnych szkoleń do momentu stabilizacji modelu. Po stabilizacji modelu możesz zastosować końcowy filtr prognozowania, aby określić priorytety elementów do przejrzenia.

Aby uzyskać szczegółowe omówienie predykcyjnego kodowania, zobacz [Informacje na temat predykcyjnego kodowania w programie Advanced eDiscovery](predictive-coding-overview.md).

## <a name="step-1-create-a-new-predictive-coding-model"></a>Krok 1. Tworzenie nowego modelu predykcyjnego kodowania

Pierwszym krokiem jest utworzenie nowego modelu predykcyjnego kodowania w zestawie recenzji

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, a następnie wybierz **kartę Zestawy** recenzji.

2. Otwórz zestaw recenzji, a następnie kliknij pozycję **AnalizaSzybki kodowanie predykcyjne (wersja zapoznawcza)**. > 

   ![Kliknij menu rozwijane Analiza w recenzji, aby przejść do strony Predykcyjne kodowanie.](..\media\ManagePredictiveCoding.png)

3. Na stronie **Predykcyjne modele kodowania (podgląd)** kliknij pozycję **Nowy model**.

4. Na stronie wysuwu wpisz nazwę modelu i opcjonalny opis.

5. Kliknij **przycisk Zapisz** , aby utworzyć model.

   Przygotowanie modelu przez system zajmie kilka minut. Gdy wszystko będzie gotowe, możesz przeprowadzić pierwszą rundę szkolenia.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Tworzenie modelu predykcyjnego kodowania](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>Krok 2. Wykonanie pierwszego rundy szkolenia

Kolejnym krokiem po utworzeniu modelu jest ukończenie pierwszego rundy szkolenia przez oznaczenie elementów jako istotnych lub nie istotnych.

1. Otwórz zestaw recenzji, a następnie kliknij pozycję **AnalizaSzybki kodowanie predykcyjne (wersja zapoznawcza)**. > 

2. Na stronie **Predykcyjne modele kodowania (wersja zapoznawcza)** wybierz model, który chcesz przeszkolić.

3. Na karcie **Omówienie** w obszarze **1. kliknij** pozycję **Rozpocznij następne szkolenie**.

   Zostanie **wyświetlona** karta Szkolenie zawierająca 50 elementów do o etykiecie.

4. Przejrzyj każdy dokument, a następnie **wybierz przycisk Istotne** lub Nie istotne u dołu okienka odczytu, aby go o etykiecie.

   ![Oznaczaj każdy dokument jako odpowiedni lub nieumiejętny.](..\media\TrainModel1.png)

5. Po oznaczeniu etykietą wszystkich 50 elementów kliknij przycisk **Zakończ**.

    "Nauka" na etykietach i zaktualizowanie modelu zajmie kilka minut. Po zakończeniu tego procesu dla modelu jest wyświetlany stan **Ready** (Gotowe) na stronie **Predykcyjne modele kodowania (podgląd** ).

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Szkolenie modelu predykcyjnego kodowania](predictive-coding-train-model.md).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>Krok 3. Stosowanie filtru wyników prognozy do elementów w zestawie recenzji

Po wydzierżawianiu jednej rundy szkolenia można zastosować filtr wyników prognozy do elementów w zestawie recenzji. Pozwala to przeglądać elementy, które model przewidział jako istotne lub nieumiejętne.   

1. Otwórz zestaw recenzji.

   ![Kliknij pozycję Filtry, aby wyświetlić stronę wysuwaną Filtry.](..\media\PredictionScoreFilter0.png)

   Wstępnie załadowane filtry domyślne są wyświetlane u góry strony zestawu recenzji. Możesz pozostawić te ustawienia ustawione jako **Dowolne**.

2. Kliknij **pozycję Filtry** , aby wyświetlić **stronę wysuwaną** Filtry.

3. Rozwiń **sekcję Analiza & kodu predykcyjnego** , aby wyświetlić zestaw filtrów.

      ![Prediction score filter in the Analytics & predictive coding section.](..\media\PredictionScoreFilter1.png)

   Konwencją nazewnictwa dla filtrów wyników prognozy jest **prognozowanie wyniku (nazwa modelu)**. Na przykład nazwa filtru wyników prognozowania dla modelu o nazwie **Model A** to **Wynik prognozy (model A)**.

4. Wybierz filtr wyników prognozy, którego chcesz użyć, a następnie kliknij przycisk **Gotowe**.

5. Na stronie zestawu recenzji kliknij listę rozwijaną filtru wyników prognozy i wpisz wartości minimalne i maksymalne dla zakresu wyników prognozy. Poniższy zrzut ekranu przedstawia na przykład zakres wyników prognozy dla przedziału od **0,5** do **1,0**.

   ![Wartości minimalne i maksymalne dla filtru wyników prognozy.](..\media\PredictionScoreFilter2.png)

6. Kliknij poza filtrem, aby automatycznie zastosować filtr do zestawu recenzji.

  Na stronie zestawu recenzji zostanie wyświetlona lista dokumentów z ocenami prognozowania w określonym zakresie.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Stosowanie filtru prognozowania do zestawu recenzji](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>Krok 4. Wykonywanie większej liczby rund szkoleniowych

Bardziej prawdopodobne jest, że trzeba będzie wykonać więcej zaokrągleń szkoleniowych w celu przeszkolenia modułu w celu lepszego przewidzenia istotnych i nieistniejnych elementów w zestawie recenzji. Ogólnie rzecz biorąc, będziesz ćwiczyć model wystarczającą ilość czasu do momentu jego stabilizacji, aby spełnić wymagania.

Aby uzyskać więcej informacji, zobacz [Wykonywanie dodatkowych zaokrągleń szkoleń.](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>Krok 5. Stosowanie filtru wyników prognozy końcowej w celu priorytetyzowania recenzji

Powtórz instrukcje z kroku 3, aby zastosować końcowy wynik prognozowania do zestawu recenzji w celu priorytetyzowania przeglądu odpowiednich i nieistniejących elementów po zakończeniu wszystkich zaokrągleń szkolenia i stabilizacji modelu.
