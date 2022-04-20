---
title: Analiza istotności testu w zakresie zbierania elektronicznych materiałów dowodowych (Premium)
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
description: Dowiedz się, jak używać karty Test po obliczeniu usługi Batch w usłudze eDiscovery (Premium) do testowania, porównywania i weryfikowania ogólnej jakości przetwarzania.
ms.openlocfilehash: 7e4541aa2309b6209537931160bf351d22ee8eb7
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935505"
---
# <a name="test-relevance-analysis-in-ediscovery-premium"></a>Analiza istotności testu w zakresie zbierania elektronicznych materiałów dowodowych (Premium)
  
Karta Test w usłudze Microsoft Purview eDiscovery (Premium) umożliwia testowanie, porównywanie i weryfikowanie ogólnej jakości przetwarzania. Te testy są wykonywane po obliczeniu usługi Batch. Oznaczając pliki w kolekcji, ekspert dokonuje ostatecznego osądu, czy każdy otagowany plik ma znaczenie dla sprawy.
  
W scenariuszach z pojedynczym i wieloma problemami testy są zwykle wykonywane dla każdego problemu. Wyniki można wyświetlić po każdym teście, a wyniki testu można ponownie wykonać za pomocą określonych przykładowych plików testowych.
  
## <a name="testing-the-rest"></a>Testowanie reszty

Test "Przetestuj resztę" służy do weryfikowania decyzji dotyczących uboju, na przykład do przeglądania tylko plików powyżej określonego wyniku odcięcia istotności na podstawie końcowych wyników zbierania elektronicznych materiałów dowodowych (Premium). Ekspert przegląda próbkę plików pod wybranym wynikiem odcięcia, aby ocenić liczbę odpowiednich plików w tym zestawie.
  
Ten test zawiera statystyki i porównanie zestawu przeglądów i populacji Testowanie reszty. Wyniki zestawu przeglądów są obliczane przez wartość Istotność podczas trenowania. Wyniki obejmują obliczenia na podstawie ustawień i parametrów wejściowych, takich jak:
  
- Przetestuj przykładowe statystyki liczby plików w przykładzie i zidentyfikowano odpowiednie pliki.

- Tabelaryczne porównanie parametrów Populacji zestawu przeglądów i reszty, na przykład liczby plików, szacowanej liczby odpowiednich plików, szacowanego bogactwa i średniego kosztu znalezienia innego odpowiedniego pliku. Ustawienia parametru kosztu mogą być ustawiane przez administratora.

Aby uruchomić test "Przetestuj resztę":

1. Otwórz kartę **Test istotności\>**.

2. Na karcie **Test** kliknij pozycję **Nowy test**. Zostanie wyświetlone okno dialogowe **Tworzenie testu** , jak pokazano w poniższym przykładzie.

    ![Relevance Test the Rest results (Testowanie istotności wyników rest).](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. W **obszarze Nazwa testu** i **Opis** wpisz nazwę i opis.

4. Na liście **Typ testu** wybierz pozycję **Przetestuj resztę**

5. Na liście **Problem/kategoria** wybierz nazwę problemu.

6. Na liście **Załaduj** wybierz obciążenie. 

7. W **obszarze Odczyt %** zaakceptuj wartość domyślną lub wybierz wartość dla wyniku istotności limitu. 

8. W **obszarze Ustaw rozmiar** lub zaakceptuj wartość domyślną. Ikony przywracania przywrócą wartości domyślne.

9. Kliknij **przycisk Rozpocznij tagowanie**. Generowany jest przykład testowy.

10. Przejrzyj i otaguj każdy z plików na karcie **Tag istotności\>**, a po zakończeniu kliknij pozycję **Oblicz**.

11. Na karcie Test możesz kliknąć pozycję **Wyświetl wyniki** , aby wyświetlić wyniki testu. Przykład przedstawiono na poniższym zrzucie ekranu.

    ![Przetestuj wyniki pozostałych.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
Na poprzednim zrzucie ekranu sekcja **Przykładowe parametry** tabeli zawiera szczegółowe informacje o liczbie plików w przykładzie oznaczonym przez eksperta oraz liczbie odpowiednich plików znalezionych w tym przykładzie.
  
Sekcja **Parametry populacji** tabeli zawiera wyniki testów, w tym populację zestawu przeglądów plików z wynikiem poniżej wybranego odcięcia i populację plików "The Rest" z wynikiem powyżej wybranego odcięcia. Dla każdej populacji są wyświetlane następujące wyniki:
  
- Zawiera pliki z procentem odczytu — deklarowane odcięcie

- Całkowita liczba plików

- Szacowana liczba odpowiednich plików

- Szacowane bogactwo

- Średni koszt przeglądu znalezienia innego odpowiedniego pliku

## <a name="testing-the-slice"></a>Testowanie wycinka

Test "Testowanie wycinka" wykonuje test podobny do testu "Przetestuj resztę", ale do segmentu pliku ustawionego zgodnie z wartością Relevance Read %.

Aby uruchomić test "Testowanie wycinka":
  
1. Otwórz kartę **Test istotności\>**.

2. Na karcie **Test** kliknij pozycję **Nowy test**. Zostanie wyświetlone okno dialogowe **Tworzenie testu** .

3. W **obszarze Nazwa testu** i **Opis** wpisz informacje.

4. Na liście **Typ testu** wybierz pozycję **Przetestuj wycinek**.

5. Na liście **Problem** wybierz nazwę problemu.

6. Na liście **Załaduj** wybierz obciążenie.

7. W **obszarze Procent odczytu między** zaakceptuj domyślne wartości niskiego i wysokiego zakresu lub wybierz wartości dla oceny istotności limitu.

8. W **obszarze Ustaw rozmiar** wybierz wartość lub zaakceptuj wartość domyślną.

    Ikony przywracania przywrócą wartość domyślną.

9. Kliknij **przycisk Rozpocznij tagowanie**. Generowany jest przykład testowy.

10. Przejrzyj i otaguj każdy z plików na karcie **Tag istotności\>**, a po zakończeniu kliknij pozycję **Oblicz**.

11. Na karcie Test możesz kliknąć pozycję **Wyświetl wyniki** , aby wyświetlić wyniki testu.
