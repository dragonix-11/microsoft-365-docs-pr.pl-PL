---
title: Dokumentacja dotycząca kodowania predykcyjnego
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
ms.openlocfilehash: 2f70039d3e55c429bf175d850db907eb7dc5b598
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942166"
---
# <a name="predictive-coding-reference-preview"></a>Dokumentacja kodowania predykcyjnego (wersja zapoznawcza)

W tym artykule opisano kluczowe pojęcia i metryki narzędzia do kodowania predykcyjnego w usłudze Microsoft Purview eDiscovery (Premium). Sekcje w artykule są wymienione w kolejności alfabetycznej.

## <a name="confidence-level"></a>Poziom ufności

Poziom ufności jest ustawieniem zaawansowanym podczas tworzenia modelu kodowania predykcyjnego. Definiuje ona, że metryki wydajności modelu (na przykład sformatowanie, precyzja i wycofanie) należą do określonego zakresu (który jest określany jako margines błędu zdefiniowany dla modelu), który jest reprezentatywny dla prawdziwych wartości wyników przewidywania przypisywanych przez model do elementów w zestawie przeglądów. Wartości poziomu ufności i marginesu błędu pomagają również określić, ile elementów jest uwzględnionych w zestawie kontrolek. Wartość domyślna poziomu ufności to 0,95 lub 95%.

## <a name="control-set"></a>Zestaw sterowania

Zestaw sterowania jest używany podczas procesu trenowania modelu kodowania predykcyjnego. Zestaw kontrolek ma na celu ocenę wyników przewidywania przypisywanych przez model do elementów z etykietami wykonywanymi podczas rund szkoleniowych. Rozmiar zestawu kontrolek jest oparty na liczbie elementów w zestawie przeglądów oraz poziomie ufności i marginesie wartości błędów ustawionych podczas tworzenia modelu. Elementy w zestawie kontrolek nigdy się nie zmieniają i nie są identyfikowalne dla użytkowników. Całkowita liczba elementów w zestawie sterowania jest wyświetlana na stronie wysuwanej dla rundy szkoleniowej.

## <a name="control-set-confusion-matrix"></a>Macierz pomyłek zestawu sterowania

Po zakończeniu rundy szkoleniowej model przypisuje wynik przewidywania do 10 elementów w zestawie sterowania oznaczonym podczas rundy szkoleniowej. Model porównuje wynik przewidywania tych 10 elementów z rzeczywistą etykietą przypisaną do elementu podczas rundy szkoleniowej. Na podstawie tego porównania model identyfikuje następujące klasyfikacje w celu oceny wydajności przewidywania modelu:

<br>

****

|Etykiety|Model przewiduje, że element jest odpowiedni|Model przewiduje, że element nie ma znaczenia|
|---|---|---|
|**Element etykiet recenzenta jako odpowiedni**|Prawdziwie dodatnie|Wynik fałszywie dodatni|
|**Element etykiet recenzenta jako nieistotny**|Fałszywie ujemny|Wartość prawdziwie ujemna|
|

Na podstawie tych porównań model uzyskuje wartości dla metryk F-score, precision i recall oraz margines błędu dla każdego z nich. Liczba typów pomyłek z macierzy jest wyświetlana na stronie wysuwanej dla rundy szkoleniowej.

## <a name="f-score"></a>Wynik F

Wynik F jest średnią ważoną wyników dla metryk precyzji i odwołania.  Zakres wyników dla tej metryki wynosi od **0** do **1**. Wynik bliżej **1** wskazuje, że model dokładniej wykrywa odpowiednie elementy. Metryka F-score jest wyświetlana na pulpicie nawigacyjnym modelu i na stronie wysuwanej dla każdej rundy trenowania.

## <a name="margin-of-error"></a>Margines błędu

Margines błędu jest ustawieniem zaawansowanym podczas tworzenia trybu kodowania predykcyjnego. Określa stopień błędu w metrykach wydajności (na przykład sformatowanie, precyzja i wycofanie), który jest uzyskiwany z losowego próbkowania elementów w zestawie sterowania. Niższy margines błędu wymaga większego zestawu kontroli, aby zapewnić, że metryki wydajności modelu mieszczą się w mniejszym zakresie. Wartości marginesu błędu i poziomu ufności pomagają również określić, ile elementów jest uwzględnionych w zestawie kontrolek. Wartość domyślna marginesu błędu to 0,05 lub 5%.

## <a name="model-stability"></a>Stabilność modelu

Stabilność modelu wskazuje zdolność modelu do dokładnego przewidywania, czy dokument w zestawie przeglądów jest istotny, czy nie. Jeśli model jest niestabilny, może być konieczne wykonanie większej liczby rund szkoleniowych w celu uwzględnienia stabilności modelu. Gdy model jest stabilny, nie trzeba będzie wykonywać więcej rund szkoleniowych. Pulpit nawigacyjny modelu wskazuje bieżący stan stabilności modelu. Gdy model jest stabilny, metryki wydajności osiągnęły poziom zgodny z ustawieniami poziomu ufności i marginesu błędu.

## <a name="overturn-rate"></a>Współczynnik przewrócenia

Współczynnik przewrócenia to procent elementów w zestawie przeglądów, w którym wynik przewidywania zmienia się między rundami szkoleniowymi. Model jest uznawany za stabilny, gdy współczynnik wywrócenia jest mniejszy niż 5%. Metryka współczynnika przewrócenia jest wyświetlana na pulpicie nawigacyjnym modelu i na stronie wysuwanej dla każdej rundy trenowania. Współczynnik przewrócenia dla pierwszej rundy treningowej wynosi zero, ponieważ nie ma poprzedniego wyniku przewidywania do przewrócenia.

## <a name="precision"></a>Dokładność

Metryka precyzji mierzy proporcję elementów, które są faktycznie istotne wśród elementów przewidywanych przez model. Oznacza to, że elementy w zestawie kontrolek, w których etykieta jest odpowiednia dla recenzenta i przewidywane jako odpowiednie dla modelu. Zakres wyników dla tej metryki wynosi od **0** do **1**. Wynik bliżej **1** wskazuje, że model zidentyfikuje mniej nieistotnych elementów. Metryka precyzji jest wyświetlana na pulpicie nawigacyjnym modelu i na stronie wysuwanej dla każdej rundy trenowania.

## <a name="prediction-score"></a>Wynik przewidywania

Jest to wynik przypisywany przez model do każdego dokumentu w zestawie przeglądów. Wynik jest oparty na istotności dokumentu w porównaniu z uczeniem się modelu z rund szkoleniowych. Ogólnie rzecz biorąc, elementy z wynikami przewidywania z zakresu od **0** do **0,5** są uważane za nieistotne, a elementy z wynikami przewidywania z zakresu **od 0,5** do **1** są uważane za istotne. Wynik przewidywania jest zawarty w polu metadanych dokumentu. Możesz użyć filtru przewidywania, aby wyświetlić elementy w zestawie przeglądów, które mieszczą się w określonym zakresie przewidywania.

## <a name="recall"></a>Przypomnieć

Metryka wycofania mierzy proporcję elementów, które przewidywany model miał znaczenie wśród elementów, które są faktycznie istotne. Oznacza to, że elementy w zestawie kontrolek, które były odpowiednie dla przewidywanego modelu, również zostały oznaczone jako istotne przez recenzenta. Zakres wyników dla tej metryki wynosi od **0** do **1**. Wynik bliżej **1** wskazuje, że model zidentyfikuje większą część odpowiednich elementów. Metryka odwołania jest wyświetlana na pulpicie nawigacyjnym modelu i na stronie wysuwanej dla każdej rundy trenowania.

## <a name="review-set"></a>Zestaw przeglądów

Zestaw przeglądów zapewnia zakres modelu kodowania predykcyjnego. Podczas tworzenia nowego modelu dla zestawu przeglądów wybierane są elementy zestawu kontroli i zestawy szkoleniowe z zestawu przeglądów. Gdy model przypisuje wyniki przewidywania, przypisuje te wyniki do elementów w przeglądzie. Przed utworzeniem modelu kodowania predykcyjnego należy dodać wszystkie elementy do zestawu przeglądów. Jeśli dodasz elementy po utworzeniu modelu, te elementy nie zostaną przypisane do wyniku przewidywania.

## <a name="richness"></a>Bogactwo

Metryka bogactwa mierzy procent elementów zestawu przeglądów, które model przewiduje jako odpowiednie. Zakres wyników dla tej metryki wynosi od **0** do **1**. Metryka bogactwa jest wyświetlana na pulpicie nawigacyjnym modelu.

## <a name="sampled-items"></a>Przykładowe elementy

Termin *sampled items* to odwołanie do losowej próbki elementów w zestawie przeglądów (zawierającym tekst), które są zaznaczone i skojarzone z zestawem kontrolek podczas tworzenia modelu kodowania predykcyjnego. Losowa próbka elementów jest również wybrana dla każdej rundy trenowania. Elementy wybrane dla zestawu sterowania modelu nigdy nie są uwzględniane w zestawie szkoleniowym dla tego samego modelu. Odwrotna jest również prawda: elementy zestawu szkoleniowego nigdy nie są uwzględniane w zestawie kontrolek.

## <a name="training-set"></a>Zestaw treningowy

Model losowo wybiera elementy z zestawu przeglądów i dodaje je do zestawu treningowego. Podczas rundy szkoleniowej elementy z zestawu szkoleniowego (oprócz elementów z zestawu sterowania) są prezentowane, aby można było oznaczyć każdy z nich jako "odpowiedni" lub "nieistotny". Ten proces etykietowania lub "trenowania" pomaga modelowi dowiedzieć się, jak przewidzieć, które elementy w przeglądzie są istotne lub nieistotne. Za każdym razem, gdy przeprowadzasz rundę treningową, model wybiera więcej elementów z przeglądu i dodaje je do zestawu treningowego dla tej rundy szkoleniowej. Elementy z zestawu kontrolek nigdy nie są wybierane dla zestawu szkoleniowego.
