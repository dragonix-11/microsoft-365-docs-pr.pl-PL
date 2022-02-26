---
title: Analiza istotności testów w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1b092f7c-ea55-44f5-b419-63f3458fd7e0
ROBOTS: NOINDEX, NOFOLLOW
description: Dowiedz się, jak używać karty Test po obliczeniu wsadowym w programie Advanced eDiscovery do testowania, porównywania i sprawdzania ogólnej jakości przetwarzania.
ms.openlocfilehash: 0ea34ce101f6891670a0b646380c965a4391ea32
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973672"
---
# <a name="test-relevance-analysis-in-advanced-ediscovery"></a>Analiza istotności testów w programie Advanced eDiscovery
  
Karta Test w aplikacji Advanced eDiscovery umożliwia testowanie, porównywanie i sprawdzanie ogólnej jakości przetwarzania. Te testy są wykonywane po obliczeniu wsadu. Dzięki otagowaniu plików w kolekcji ekspert podejmuje ostateczną decyzję o tym, czy każdy z otagowanych plików jest istotny dla danej sprawy.
  
W scenariuszach z jednym i wieloma problemami zazwyczaj przeprowadzane są testy dla 1 problemu. Wyniki można wyświetlać po każdym teście, a wyniki testów można ponowniepracować z określonymi przykładami plików testowych.
  
## <a name="testing-the-rest"></a>Testowanie pozostałej części

Test "Testuj resztę" służy do sprawdzania poprawności decyzji dotyczących oceny, na przykład w celu przeglądania na podstawie ostatecznych wyników odciętych tylko plików powyżej określonego wyniku odciętych od istotności na podstawie ostatecznych Advanced eDiscovery wyników. Ekspert przegląda próbkę plików w wybranym wyniku odciętym, aby ocenić liczbę odpowiednich plików w tym zestawie.
  
Ten test udostępnia statystyki i porównanie zestawu recenzji z populacją Test populacji rest. Wyniki zestawu recenzji są obliczane na podstawie istotności podczas szkolenia. Wyniki obejmują obliczenia oparte na ustawieniach i parametrach wejściowych, takich jak:
  
- Przetestuj przykładową statystykę liczby plików w próbce i zidentyfikowanych odpowiednich plików.

- Tabelarycznie porównanie parametrów Population (Populacja) zestawu recenzji i reszty (na przykład liczba plików, szacowana liczba odpowiednich plików, szacowane dosyć rozbudowy i średni koszt znajdowania innego odpowiedniego pliku). Ustawienia parametru Koszt mogą zostać określone przez administratora.

Aby uruchomić test "Test rest":

1. Otwórz **kartę Test istotności\>**.

2. Na karcie **Test** kliknij pozycję **Nowy test**. Zostanie **wyświetlone okno dialogowe** Tworzenie testu, jak pokazano w poniższym przykładzie.

    ![Test istotności : wyniki spoczynku.](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. W **polach** Nazwa testu **i Opis** wpisz nazwę i opis.

4. Z listy **Typ testu** wybierz pozycję **Testuj resztę**

5. Na **liście Problem/kategoria** wybierz nazwę problemu.

6. Z **listy Załaduj** wybierz obciążenie. 

7. W **odczytu %** zaakceptuj wartość domyślną lub wybierz wartość dla wyniku odciętych istotności. 

8. W **ustawieniach** Ustaw rozmiar lub zaakceptuj wartość domyślną. Ikony przywracania przywrócą wartości domyślne.

9. Kliknij **pozycję Rozpocznij tagowanie**. Zostanie wygenerowana próbka testowa.

10. Przejrzyj i otaguj każdy z plików na karcie **\> Tag istotności**, a po jego kliknięciu kliknij przycisk **Oblicz**.

11. Na karcie Test możesz kliknąć pozycję **Wyświetl wyniki** , aby wyświetlić wyniki testu. Przykład przedstawiono na poniższym zrzucie ekranu.

    ![Przetestuj wyniki pozostałych.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
Na poprzednim zrzucie  ekranu sekcja Przykładowe parametry w tabeli zawiera szczegółowe informacje o liczbie plików w przykładzie oznaczonym przez eksperta oraz liczbie odpowiednich plików znalezionych w tej próbce.
  
Sekcja **Parametry populacji** w tabeli zawiera wyniki testów, w tym przeglądanie zestawu populacji plików z wynikami poniżej wybranego odciętych plików i populacji "Resztę" z wynikiem powyżej wybranego odciętych plików. Dla każdej populacji są wyświetlane następujące wyniki:
  
- Zawiera pliki z odczytaną wartością % — odcięty od wartości

- Całkowita liczba plików

- Szacowana liczba odpowiednich plików

- Szacowane richness

- Średni koszt przeglądu wyszukiwania innego odpowiedniego pliku

## <a name="testing-the-slice"></a>Testowanie wycinka

Test "Test the Slice" wykonuje testy podobne do testu "Testuj resztę", ale w przypadku segmentu pliku określonego za pomocą ustawienia Istotność odczytu %.

Aby uruchomić test "Testowanie wycinka":
  
1. Otwórz **kartę Test istotności\>**.

2. Na karcie **Test** kliknij pozycję **Nowy test**. Zostanie **wyświetlone okno dialogowe** Tworzenie testu.

3. W **polach Nazwa** testu **i Opis** wpisz informacje.

4. Z listy **Typ testu** wybierz pozycję **Testuj wycinek**.

5. Na liście **Problem** wybierz nazwę problemu.

6. Z **listy Załaduj** wybierz obciążenie.

7. W **pól Odczytuj %** między zaakceptuj domyślne wartości niskie i wysokiego zakresu lub wybierz wartości, aby uzyskać odcięty wynik istotności.

8. W **polecej** Ustaw rozmiar wybierz wartość lub zaakceptuj wartość domyślną.

    Ikony przywracania przywrócą wartość domyślną.

9. Kliknij **pozycję Rozpocznij tagowanie**. Zostanie wygenerowana próbka testowa.

10. Przejrzyj i otaguj każdy z plików na karcie **\> Tag istotności**, a po jego kliknięciu kliknij przycisk **Oblicz**.

11. Na karcie Test możesz kliknąć pozycję **Wyświetl wyniki** , aby wyświetlić wyniki testu.
