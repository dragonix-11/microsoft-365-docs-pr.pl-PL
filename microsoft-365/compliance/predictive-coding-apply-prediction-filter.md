---
title: Stosowanie filtru wyników prognozowania do elementów w zestawie recenzji
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
description: Użyj filtru wyników prognozowania, aby wyświetlać elementy, których model predykcyjnego kodowania jest przewidywany jako istotny lub nieumiejętny.
ms.openlocfilehash: 04d0881e36c28a70df58a1aa7b054c641dfeeb2a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987772"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Stosowanie filtru wyników prognozy do zestawu recenzji (podgląd)

Po utworzeniu modelu predykcyjnego kodowania w programie Advanced eDiscovery i przeszkolić go w punkcie, w którym jest stabilny, możesz zastosować filtr wyników prognozowania, aby wyświetlić elementy zestawu recenzji określone przez model są istotne (lub nie istotne). Podczas tworzenia modelu jest również tworzony odpowiedni filtr wyników prognozowania. Ten filtr umożliwia wyświetlanie elementów, do których przypisano wynik prognozowania w określonym zakresie. Ogólnie wyniki prognozowania z wartości **od 0** do **0,5** są przypisywane do elementów, które są przewidywane w modelu, nie są istotne. Elementy, do których przypisano wyniki prognozowania z **wartości od 0,5** do **1,0** , to elementy prognozowane przez model są istotne.

Oto dwa sposoby używania filtru wyników prognozy:

- Priorytetyzowanie przeglądu elementów w zestawie recenzji, który został prognozowany przez model, ma znaczenie.

- Elementy z zestawu recenzji, które zostały określone w modelu, nie są istotne. Alternatywnie można użyć filtru wyników prognozowania w celu odejmowania priorytetów przeglądu elementów nieistnieżnych.

## <a name="before-you-apply-a-prediction-score-filter"></a>Przed zastosowaniem filtru wyników prognozy

- Utwórz model predykcyjnego kodowania, aby utworzyć odpowiedni filtr wyników prognozowania.

- Możesz zastosować filtr wyników prognozy po dowolnym zaokrągleniu szkolenia. Przed użyciem filtru wyników prognozy warto jednak poczekać na wykonanie kilku zaokrągleń lub na stabilność modelu.

## <a name="apply-a-prediction-score-filter"></a>Stosowanie filtru wyników prognozowania

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, wybierz **kartę** Zestawy recenzji, a następnie otwórz zestaw recenzji.

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

  > [!TIP]
  > Aby wyświetlić rzeczywisty wynik prognozy przypisany do dokumentu, możesz kliknąć kartę **Metadane** w okienku odczytu. Wyniki prognozy dla wszystkich modeli w zestawie recenzji są wyświetlane we właściwości metadanych **IstotnośćScores** .

## <a name="more-information"></a>Więcej informacji

- Aby uzyskać więcej informacji o używaniu filtrów, zobacz Wykonywanie [zapytań i filtrowanie zawartości w zestawie recenzji](review-set-search.md).
