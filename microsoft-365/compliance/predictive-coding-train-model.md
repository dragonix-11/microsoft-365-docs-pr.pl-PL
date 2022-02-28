---
title: Szkolenie modelu predykcyjnego kodowania w programie Advanced eDiscovery
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
ms.openlocfilehash: b5f1a958696dad84ac2bedec8f1ab7d23dfa6428
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988049"
---
# <a name="train-a-predictive-coding-model-preview"></a>Szkolenie modelu predykcyjnego kodowania (podgląd)

Kolejnym krokiem po utworzeniu modelu predykcyjnego kodowania w programie Advanced eDiscovery jest wykonanie pierwszego rundy szkolenia w celu przeszkolenia modelu w zakresie tego, co jest istotne i nieistniejący zawartości w zestawie recenzji. Po ukończeniu pierwszej rundy szkolenia można przeprowadzić kolejne rundy szkoleniowe, aby ulepszyć możliwości modelu przewidywania istotnej i nieistnieowej zawartości.

Aby zapoznać się z przepływem pracy predykcyjnego kodowania, zobacz [Informacje na temat predykcyjnego kodowania w programie Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Zanim wyszkolisz model

- W trakcie rundy szkolenia oznacz elementy jako **istotne lub nieo** znaczenia na podstawie istotności zawartości dokumentu. Nie należy opierać się na wartościach w polach metadanych. Na przykład w przypadku wiadomości e-mail Teams konwersacji nie należy opierać się na decyzji dotyczącej etykiet dla uczestników wiadomości.

## <a name="train-a-model-for-the-first-time"></a>Szkolenie modelu po raz pierwszy

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, a następnie wybierz **kartę Zestawy** recenzji.

2. Otwórz zestaw recenzji, a następnie kliknij pozycję **AnalizaSzybki kodowanie predykcyjne (wersja zapoznawcza)**. > 

3. Na stronie **Predykcyjne modele kodowania (wersja zapoznawcza)** wybierz model, który chcesz przeszkolić.

4. Na karcie **Omówienie** w obszarze **1. kliknij** pozycję **Rozpocznij następne szkolenie**.

   Zostanie **wyświetlona** karta Szkolenie zawierająca 50 elementów do o etykiecie.

5. Przejrzyj każdy dokument, a następnie **wybierz przycisk Istotne** lub Nie istotne u dołu okienka odczytu, aby go o etykiecie.

   ![Oznaczaj każdy dokument jako odpowiedni lub nieumiejętny.](..\media\TrainModel1.png)

6. Po oznaczeniu etykietą wszystkich 50 elementów kliknij przycisk **Zakończ**.

    "Nauka" na etykietach i zaktualizowanie modelu zajmie kilka minut. Po zakończeniu tego procesu dla modelu jest wyświetlany stan **Ready** (Gotowe) na stronie **Predykcyjne modele kodowania (podgląd** ).

## <a name="perform-additional-training-rounds"></a>Wykonywanie dodatkowych zaokrągleń szkoleń

Po zakończeniu pierwszej rundy szkolenia można wykonać kolejne zaokrągli szkoleniowe, korzystając z procedury opisanej w poprzedniej sekcji. Jedyna różnica polega na tym, że na karcie Przegląd modelu zostanie zaktualizowana liczba  rundy szkolenia. Na przykład po przeprowadzeniu pierwszej rundy szkolenia możesz kliknąć pozycję Rozpocznij następne  szkolenie, aby rozpocząć drugą rundę szkolenia. I tak dalej.

Każda runda szkolenia (zarówno w toku, jak i ukończone) jest wyświetlana na **karcie Szkolenie dla** modelu. Po wybraniu rundy szkolenia zostanie wyświetlona wysuuwana strona z informacjami i metrykami dla rundy.

## <a name="what-happens-after-you-perform-a-training-round"></a>Co się dzieje po zakończeniu rundy szkolenia

Po pierwszym zaokrągleniu szkolenia jest rozpoczynane zadanie, które wykonuje następujące czynności:

- Na podstawie sposobu, w jaki oznaczono 40 elementów w zestawie szkoleniowym, sam model uczy się na podstawie etykiet i aktualizacji, aby uzyskać większą dokładność.

- Następnie model przetwarza każdy element w całym zestawie recenzji i przypisuje wynik prognozy między **0** (nie istotne) a **1** (odpowiedni).

- Model przypisuje wynik prognozy dla 10 elementów w zestawie kontrolek oznaczonych podczas rundy szkolenia. Ten model porównuje wynik prognozowania tych 10 elementów z rzeczywistą etykietą przypisaną do elementu podczas rundy szkolenia. Na podstawie tego porównania model identyfikuje następującą klasyfikację (nazywaną macierzą nieporozumień zestawu kontrolek *) do* oceny wydajności prognozowania modelu:

  <br>

  ****

  |Etykieta|Model przewiduje, że element jest istotny|Model przewiduje element nie jest odpowiedni|
  |---|---|---|
  |**Recenzent etykietuje element jako odpowiedni**|True positive|Wynik fałszywie dodatni|
  |**Recenzent etykietuje element jako nieucztowy**|Wynik fałszywie ujemny|True negative|
  |

  Na podstawie tych porównań model pozysł wartości dla wyników F-score, dokładności i odwołania oraz marginesu błędu dla każdej z nich. Wyniki dla tych metryk wydajności modelu są wyświetlane na wysuwanych stronie rundy szkolenia. Aby uzyskać opis tych metryk, zobacz [Predykcyjne wskazówki dotyczące kodowania](predictive-coding-reference.md).

- Na koniec model określa kolejne 50 elementów, które zostaną użyte w następnym szkoleniu. Tym razem model może wybrać 20 elementów z zestawu kontrolek i 30 nowych elementów z zestawu recenzji i wyznaczyć je jako zestaw szkoleniowy na następną rundę. Próbkowanie do następnego rundy nie jest próbkowane równomiernie. Model optymalizuje wybór próbkowania elementów z zestawu recenzji w celu wybrania elementów, dla których prognoza jest niejednoznaczna, co oznacza, że wynik prognozowania należy do zakresu 0,5. Ten proces jest nazywany *wybórm zniechęceniem*.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Co się stanie po kolejnych rundach szkolenia

Po zakończeniu kolejnych zaokrągleń szkoleniowych (po pierwszym zaokrągleniu szkolenia) model wykonuje następujące czynności:

- Model zostanie zaktualizowany na podstawie etykiet zastosowanych do zestawu szkoleniowego w tej rundy szkolenia.

- System ocenia wynik prognozowania modelu dla elementów w zestawie kontrolek i sprawdza, czy wynik jest wyrównany do sposobu, w jaki oznaczono elementy w zestawie kontrolek. Ocena jest wykonywana na wszystkich elementach oznaczonych etykietą z zestawu kontrolek dla wszystkich zaokrągleń szkoleniowych. Wyniki tej oceny są uwzględnione na pulpicie nawigacyjnym na karcie **Przegląd** modelu.

- Zaktualizowany model ponownie przetwarza każdy element w zestawie recenzji i przypisuje każdemu elementowi zaktualizowany wynik prognozowania.

## <a name="next-steps"></a>Następne kroki

Po zakończeniu pierwszej rundy szkoleniowej możesz wykonać więcej zaokrągleń szkoleniowych lub zastosować filtr wyników prognozy modelu do zestawu recenzji, aby wyświetlić elementy, które model przewidział, jako odpowiednie lub nieocene. Aby uzyskać więcej informacji, zobacz [Stosowanie filtru wyników prognozy do zestawu recenzji](predictive-coding-apply-prediction-filter.md).
