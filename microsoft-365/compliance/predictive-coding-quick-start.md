---
title: Kodowanie predykcyjne w usłudze eDiscovery (Premium) — szybki start
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
description: Dowiedz się, jak rozpocząć korzystanie z modułu kodowania predykcyjnego w usłudze eDiscovery (Premium). W tym artykule przedstawiono kompleksowy proces używania kodowania predykcyjnego do identyfikowania zawartości w zestawie przeglądów, który jest najbardziej odpowiedni dla badania.
ms.openlocfilehash: ddf1762545765424891108f50cceea17999f0920
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625088"
---
# <a name="quick-start-predictive-coding-in-ediscovery-premium-preview"></a>Szybki start: kodowanie predykcyjne w usłudze eDiscovery (Premium) (wersja zapoznawcza)

W tym artykule przedstawiono przewodnik Szybki start dotyczący korzystania z kodowania predykcyjnego w Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium). Moduł kodowania predykcyjnego korzysta z inteligentnych możliwości uczenia maszynowego, które ułatwiają wykreślenie dużych ilości zawartości przypadków, która nie jest istotna dla badania. Można to osiągnąć, tworząc i szkoląc własne modele kodowania predykcyjnego, które ułatwiają określanie priorytetów najbardziej odpowiednich elementów do przeglądu.

Oto krótkie omówienie procesu kodowania predykcyjnego:

![Szybki start — proces kodowania przewidywania.](..\media\PredictiveCodingQuickStartProcess.png)

Aby rozpocząć, należy utworzyć model, oznaczać etykietą tylko 50 elementów jako odpowiednich lub nieistotnych. Następnie system używa tego szkolenia do stosowania wyników przewidywania do każdego elementu w zestawie przeglądów. Umożliwia to filtrowanie elementów na podstawie wyniku przewidywania, co pozwala najpierw przejrzeć najbardziej odpowiednie (lub nieistotne) elementy. Jeśli chcesz trenować modele z wyższymi wskaźnikami akustyków i współczynników wycofywania, możesz kontynuować etykietowanie elementów w kolejnych rundach szkoleniowych, dopóki model się nie ustabilizuje. Po ustabilizowaniu modelu można zastosować ostateczny filtr przewidywania, aby określić priorytety elementów do przejrzenia.

Szczegółowe omówienie kodowania predykcyjnego można znaleźć [w temacie Learn about predictive coding in eDiscovery (Premium) (Informacje o kodowaniu predykcyjnym w usłudze eDiscovery (Premium).](predictive-coding-overview.md)

## <a name="step-1-create-a-new-predictive-coding-model"></a>Krok 1. Tworzenie nowego modelu kodowania predykcyjnego

Pierwszym krokiem jest utworzenie nowego modelu kodowania predykcyjnego w zestawie przeglądów

1. W portal zgodności Microsoft Purview otwórz przypadek zbierania elektronicznych materiałów dowodowych (Premium), a następnie wybierz kartę **Zestawy przeglądów**.

2. Otwórz zestaw przeglądów, a następnie kliknij pozycję **Analiza** > **Zarządzaj kodowaniem predykcyjnym (wersja zapoznawcza).**

   ![Kliknij menu rozwijane Analizuj w zestawie przeglądów, aby przejść do strony Kodowanie predykcyjne.](..\media\ManagePredictiveCoding.png)

3. Na stronie **Modele kodowania predykcyjnego (wersja zapoznawcza)** kliknij pozycję **Nowy model**.

4. Na stronie wysuwanej wpisz nazwę modelu i opcjonalny opis.

5. Kliknij przycisk **Zapisz** , aby utworzyć model.

   Przygotowanie modelu przez system potrwa kilka minut. Gdy wszystko będzie gotowe, możesz wykonać pierwszą rundę trenowania.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Tworzenie modelu kodowania predykcyjnego](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>Krok 2. Wykonanie pierwszej rundy treningowej

Po utworzeniu modelu następnym krokiem jest ukończenie pierwszej rundy trenowania przez oznaczenie elementów jako odpowiednich lub nieistotnych.

1. Otwórz zestaw przeglądów, a następnie kliknij pozycję **Analiza** > **Zarządzaj kodowaniem predykcyjnym (wersja zapoznawcza).**

2. Na stronie **Modele kodowania predykcyjnego (wersja zapoznawcza)** wybierz model, który chcesz wytrenować.

3. Na karcie **Przegląd** w obszarze **Runda 1** kliknij pozycję **Rozpocznij następną rundę treningową**.

   Zostanie wyświetlona karta **Trenowanie** zawierająca 50 elementów do etykiety.

4. Przejrzyj każdy dokument, a następnie wybierz przycisk **Odpowiednie** lub **Nieprawidłowe** w dolnej części okienka do czytania, aby go oznaczyć etykietą.

   ![Oznacz każdy dokument jako odpowiedni lub nieistotny.](..\media\TrainModel1.png)

5. Po oznaczeniu wszystkich 50 elementów kliknij przycisk **Zakończ**.

    Po kilku minutach system będzie "uczyć się" z etykietowania i aktualizować model. Po zakończeniu tego procesu stan **Gotowe** jest wyświetlany dla modelu na stronie **Predykcyjne modele kodowania (wersja zapoznawcza).**

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Train a predictive coding model (Trenowanie modelu kodowania predykcyjnego](predictive-coding-train-model.md)).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>Krok 3. Stosowanie filtru wyniku przewidywania do elementów w zestawie przeglądów

Po wykonaniu w dzierżawie jednej rundy treningowej można zastosować filtr wyniku przewidywania do elementów w zestawie przeglądów. Dzięki temu można przejrzeć elementy, które model przewidział jako istotne lub nieistotne.   

1. Otwórz zestaw przeglądów.

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

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Stosowanie filtru przewidywania do zestawu przeglądów](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>Krok 4. Wykonywanie większej liczby rund treningowych

Bardziej niż prawdopodobne jest wykonanie większej liczby rund szkoleniowych w celu wytrenowania modułu w celu lepszego przewidywania odpowiednich i nieistotnych elementów w zestawie przeglądów. Ogólnie rzecz biorąc, wytrenujesz model wystarczająco dużo razy, dopóki nie ustabilizuje się na tyle, aby spełniał wymagania.

Aby uzyskać więcej informacji, zobacz [Wykonywanie dodatkowych rund szkoleniowych](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>Krok 5. Stosowanie filtru wyniku przewidywania końcowego w celu określenia priorytetów przeglądu

Powtórz instrukcje w kroku 3, aby zastosować końcowy wynik przewidywania do zestawu przeglądów, aby ustalić priorytet przeglądu odpowiednich i nieistotnych elementów po zakończeniu wszystkich rund szkoleniowych i ustabilizowaniu modelu.
