---
title: Stosowanie filtru wyniku przewidywania do zestawu przeglądów
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Użyj filtru oceny przewidywania, aby wyświetlić elementy, które model kodowania predykcyjnego są przewidywane jako odpowiednie lub nieistotne.
ms.openlocfilehash: 64abac8b9f53baa9afb869d77296089544919fea
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096617"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Stosowanie filtru wyniku przewidywania do zestawu przeglądów (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po utworzeniu modelu kodowania predykcyjnego w usłudze Microsoft Purview eDiscovery (Premium) i wytrenowaniu go do punktu, w którym jest on stabilny, można zastosować filtr oceny przewidywania, aby wyświetlić elementy zestawu przeglądów, które został określony przez model, są istotne (lub nieistotne). Podczas tworzenia modelu tworzony jest również odpowiedni filtr wyników przewidywania. Ten filtr umożliwia wyświetlanie elementów, do których przypisano wynik przewidywania w określonym zakresie. Ogólnie rzecz biorąc, wyniki przewidywania od **0** do **0,5** są przypisywane do elementów, które model przewidział, nie są istotne. Elementy przypisane do wyników przewidywania z **zakresu od .5** do **1.0** są elementami, które model przewidział, są istotne.

Poniżej przedstawiono dwa sposoby użycia filtru wyniku przewidywania:

- Określanie priorytetów przeglądu elementów w zestawie przeglądów, który przewidział model, jest istotne.

- Elementy uśmiercenia z zestawu przeglądów, które przewidział model, nie są istotne. Alternatywnie możesz użyć filtru oceny przewidywania, aby anulować priorytety przeglądu elementów, które nie są istotne.

## <a name="before-you-apply-a-prediction-score-filter"></a>Przed zastosowaniem filtru wyników przewidywania

- Utwórz model kodowania predykcyjnego, aby utworzyć odpowiedni filtr wyników przewidywania.

- Filtr wyniku przewidywania można zastosować po dowolnej z rund treningowych. Warto jednak poczekać po wykonaniu kilku rund lub do momentu, aż model będzie stabilny przed użyciem filtru wyniku przewidywania.

## <a name="apply-a-prediction-score-filter"></a>Stosowanie filtru wyniku przewidywania

1. W portalu zgodności usługi Microsoft Purview otwórz przypadek zbierania elektronicznych materiałów dowodowych (Premium), wybierz kartę **Zestawy przeglądów**, a następnie otwórz zestaw przeglądów.

   ![Kliknij pozycję Filtry, aby wyświetlić stronę wysuwaną Filtry.](..\media\PredictionScoreFilter0.png)   

   Wstępnie załadowane filtry domyślne są wyświetlane w górnej części strony zestawu przeglądów. Możesz pozostawić te ustawienia na **Dowolne**.

2. Kliknij pozycję **Filtry** , aby wyświetlić stronę wysuwaną **Filtry** .

3. Rozwiń sekcję **Analiza & kodowania predykcyjnego** , aby wyświetlić zestaw filtrów.

      ![Filtr wskaźnika przewidywania w sekcji Analiza & kodowania predykcyjnego.](..\media\PredictionScoreFilter1.png)

   Konwencją nazewnictwa dla filtrów wyników przewidywania jest **wynik przewidywania (nazwa modelu).** Na przykład nazwa filtru wyniku przewidywania dla modelu o nazwie **Model A** to **Wynik przewidywania (Model A)**.

4. Wybierz filtr wyniku przewidywania, którego chcesz użyć, a następnie kliknij przycisk **Gotowe**.

5. Na stronie zestawu przeglądów kliknij listę rozwijaną filtru wyników przewidywania i wpisz wartości minimalne i maksymalne dla zakresu wyników przewidywania. Na przykład poniższy zrzut ekranu przedstawia zakres wyników przewidywania z zakresu od **.5** do **1.0**.

   ![Wartości minimalne i maksymalne dla filtru wyniku przewidywania.](..\media\PredictionScoreFilter2.png)

6. Kliknij poza filtrem, aby automatycznie zastosować filtr do zestawu przeglądów.

  Lista dokumentów z wynikiem przewidywania w określonym zakresie jest wyświetlana na stronie zestawu przeglądów. 

  > [!TIP]
  > Aby wyświetlić rzeczywisty wynik przewidywania przypisany do dokumentu, możesz kliknąć kartę **Metadane** w okienku odczytu. Wyniki przewidywania dla wszystkich modeli w zestawie przeglądów są wyświetlane we właściwości **metadanych RelevanceScores** .

## <a name="more-information"></a>Więcej informacji

- Aby uzyskać więcej informacji na temat korzystania z filtrów, zobacz [Wykonywanie zapytań i filtrowanie zawartości w zestawie przeglądów](review-set-search.md).
