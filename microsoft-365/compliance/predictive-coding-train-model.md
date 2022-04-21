---
title: Trenowanie modelu kodowania predykcyjnego w usłudze eDiscovery (Premium)
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
ms.openlocfilehash: 3335e437a659eab984943adda31abdb344908c1c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997653"
---
# <a name="train-a-predictive-coding-model-preview"></a>Trenowanie modelu kodowania predykcyjnego (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po utworzeniu modelu kodowania predykcyjnego w usłudze Microsoft Purview eDiscovery (Premium) następnym krokiem jest przeprowadzenie pierwszej rundy trenowania w celu wytrenowania modelu na temat istotnej i nieistotnej zawartości w zestawie przeglądów. Po zakończeniu pierwszej rundy trenowania możesz wykonać kolejne rundy szkoleniowe, aby zwiększyć zdolność modelu do przewidywania odpowiedniej i nieistotnej zawartości.

Aby przejrzeć przepływ pracy kodowania predykcyjnego, zobacz [Learn about predictive coding in eDiscovery (Premium) (Informacje o kodowaniu predykcyjnym w usłudze eDiscovery (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Przed wytrenowania modelu

- Podczas rundy szkoleniowej oznacz elementy jako **istotne** lub **nieistotne** na podstawie istotności zawartości w dokumencie. Nie opieraj decyzji na wartościach w polach metadanych. Na przykład w przypadku wiadomości e-mail lub Teams konwersacji nie należy opierać decyzji o etykietowaniu na uczestnikach wiadomości.

## <a name="train-a-model-for-the-first-time"></a>Trenowanie modelu po raz pierwszy

1. W portalu zgodności usługi Microsoft Purview otwórz przypadek zbierania elektronicznych materiałów dowodowych (Premium), a następnie wybierz kartę **Zestawy przeglądów**.

2. Otwórz zestaw przeglądów, a następnie kliknij pozycję **AnalizaZarządzanie** >  **kodowaniem predykcyjnym (wersja zapoznawcza).**

3. Na stronie **Modele kodowania predykcyjnego (wersja zapoznawcza)** wybierz model, który chcesz wytrenować.

4. Na karcie **Przegląd** w obszarze **Runda 1** kliknij pozycję **Rozpocznij następną rundę treningową**.

   Zostanie wyświetlona karta **Trenowanie** zawierająca 50 elementów do etykiety.

5. Przejrzyj każdy dokument, a następnie wybierz przycisk **Odpowiednie** lub **Nieprawidłowe** w dolnej części okienka do czytania, aby go oznaczyć etykietą.

   ![Oznacz każdy dokument jako odpowiedni lub nieistotny.](..\media\TrainModel1.png)

6. Po oznaczeniu wszystkich 50 elementów kliknij przycisk **Zakończ**.

    Po kilku minutach system będzie "uczyć się" z etykietowania i aktualizować model. Po zakończeniu tego procesu stan **Gotowe** jest wyświetlany dla modelu na stronie **Predykcyjne modele kodowania (wersja zapoznawcza).**

## <a name="perform-additional-training-rounds"></a>Wykonywanie dodatkowych rund szkoleniowych

Po wykonaniu pierwszej rundy trenowania możesz wykonać kolejne rundy treningowe, wykonując kroki opisane w poprzedniej sekcji. Jedyną różnicą jest to, że liczba rundy trenowania zostanie zaktualizowana na karcie **Przegląd** modelu. Na przykład po wykonaniu pierwszej rundy treningowej możesz kliknąć przycisk **Rozpocznij następną rundę treningową** , aby rozpocząć drugą rundę trenowania. I tak dalej.

Każda runda trenowania (zarówno tych w toku, jak i tych, które są ukończone) jest wyświetlana na karcie **Trenowanie** dla modelu. Po wybraniu rundy szkoleniowej zostanie wyświetlona strona wysuwana z informacjami i metrykami dla rundy.

## <a name="what-happens-after-you-perform-a-training-round"></a>Co się stanie po zakończeniu rundy treningowej

Po wykonaniu pierwszej rundy trenowania uruchamiane jest zadanie, które wykonuje następujące czynności:

- W oparciu o sposób etykietowania 40 elementów w zestawie szkoleniowym model uczy się z etykietowania i samych aktualizacji, aby stać się bardziej dokładnym.

- Następnie model przetwarza każdy element w całym zestawie przeglądów i przypisuje wynik przewidywania z zakresu **od 0** (nieistotny) do **1** (odpowiedni).

- Model przypisuje wynik przewidywania do 10 elementów w zestawie sterowania oznaczonym podczas rundy trenowania. Model porównuje wynik przewidywania tych 10 elementów z rzeczywistą etykietą przypisaną do elementu podczas rundy szkoleniowej. Na podstawie tego porównania model identyfikuje następującą klasyfikację (nazywaną *macierzą pomyłek zestawu kontroli*), aby ocenić wydajność przewidywania modelu:

  <br>

  ****

  |Etykiety|Model przewiduje, że element jest odpowiedni|Model przewiduje, że element nie ma znaczenia|
  |---|---|---|
  |**Element etykiet recenzenta jako odpowiedni**|Prawdziwie dodatnie|Wynik fałszywie dodatni|
  |**Element etykiet recenzenta jako nieistotny**|Fałszywie ujemny|Wartość prawdziwie ujemna|
  |

  Na podstawie tych porównań model uzyskuje wartości dla metryk F-score, precision i recall oraz margines błędu dla każdego z nich. Wyniki dla tych metryk wydajności modelu są wyświetlane na stronie wysuwanej dla rundy trenowania. Opis tych metryk można znaleźć w temacie [Predictive coding reference (Dokumentacja kodowania predykcyjnego](predictive-coding-reference.md)).

- Na koniec model określa kolejne 50 elementów, które zostaną użyte do następnej rundy trenowania. Tym razem model może wybrać 20 elementów z zestawu kontrolek i 30 nowych elementów z zestawu przeglądów i wyznaczyć je jako zestaw szkoleniowy dla następnej rundy. Próbkowanie dla następnej rundy treningowej nie jest jednolicie próbki. Model zoptymalizuje wybór próbkowania elementów z zestawu przeglądów, aby wybrać elementy, w których przewidywanie jest niejednoznaczne, co oznacza, że wynik przewidywania znajduje się w zakresie 0,5. Ten proces jest nazywany *zaznaczeniem tendencyjnym*.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Co się stanie po wykonaniu kolejnych rund treningowych

Po wykonaniu kolejnych rund treningowych (po pierwszej rundzie trenowania) model wykonuje następujące czynności:

- Model jest aktualizowany na podstawie etykiet zastosowanych do zestawu trenowania w tej rundzie trenowania.

- System ocenia wynik przewidywania modelu dla elementów w zestawie sterowania i sprawdza, czy wynik jest zgodny ze sposobem etykietowania elementów w zestawie kontrolek. Ocena jest wykonywana dla wszystkich elementów oznaczonych etykietami z zestawu sterowania dla wszystkich rund szkoleniowych. Wyniki tej oceny są uwzględniane na pulpicie nawigacyjnym na karcie **Przegląd** modelu.

- Zaktualizowany model ponownie przetwarza każdy element w zestawie przeglądów i przypisuje każdemu elementowi zaktualizowany wynik przewidywania.

## <a name="next-steps"></a>Następne kroki

Po wykonaniu pierwszej rundy trenowania możesz wykonać więcej rund treningowych lub zastosować filtr wyników przewidywania modelu do zestawu przeglądów, aby wyświetlić elementy, które model przewidział jako odpowiednie lub nieistotne. Aby uzyskać więcej informacji, zobacz [Apply a prediction score filter to a review set (Stosowanie filtru wyniku przewidywania do zestawu przeglądów](predictive-coding-apply-prediction-filter.md)).
