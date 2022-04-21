---
title: Trenowanie tagowania i istotności w zakresie zbierania elektronicznych materiałów dowodowych (Premium)
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
ms.assetid: 8576cc86-d51b-4285-b54b-67184714cc62
ROBOTS: NOINDEX, NOFOLLOW
description: Zapoznaj się z krokami tagowania, a następnie pracuj z próbką szkoleniową zawierającą 40 plików na etapie trenowania istotności w usłudze eDiscovery (Premium).
ms.openlocfilehash: 9078bf36e1434cad0362c4584b5c61fd49e86c14
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996685"
---
# <a name="tagging-and-relevance-training-in-ediscovery-premium"></a>Trenowanie tagowania i istotności w zakresie zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
W tym artykule opisano procedurę pracy z modułem szkoleniowym Istotność w usłudze Microsoft Purview eDiscovery (Premium).
  
Po zakończeniu oceny w obszarze eDiscovery (Premium) i wprowadzeniu etapu trenowania istotności na karcie Tag na potrzeby tagowania jest wprowadzana próbka szkoleniowa zawierająca 40 plików.
  
## <a name="performing-relevance-training"></a>Przeprowadzanie trenowania istotności

1. Na karcie **Tag istotności \>** okienko Tagowanie jest wyświetlane domyślnie w okienku po lewej stronie, a przykładowe pliki są wyświetlane pojedynczo na potrzeby tagowania.

    ![Panel Tag istotności.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    Na karcie **Tag** jest wyświetlana nazwa wyświetlana pliku. Może to być ścieżka, temat wiadomości e-mail, tytuł lub nazwa zdefiniowana przez użytkownika. Identyfikator, ścieżka pliku lub ścieżka tekstowa można skopiować, klikając prawym przyciskiem myszy ścieżkę pliku.

    Statystyki tagowania na karcie **Tag** pokazują numer przykładu pliku (w górnej części okienka po lewej stronie), liczbę aktualnie wyświetlanego pliku z łącznej liczby plików w przykładzie (u dołu okienka po prawej stronie) oraz bieżącą całkowitą liczbę tagowanych plików w przykładzie (u dołu okienka po lewej stronie), która zmienia się w miarę tagowania plików. Dotyczy to wszelkich wykonanych tagów istotności, zarówno w obszarze Ocena, Szkolenie, Nadrabianie zaległości, czy Test.

    Ikony wskazujące istnienie komentarzy, tagów i plików rodzinnych są wyświetlane w widoku plików na pasku nad plikiem.

2. Określ istotność pliku w przypadku problemu i otaguj go przy użyciu przycisków ikony opcji tagowania lub skrótów klawiaturowych, jak pokazano w poniższej tabeli:

   |**Opcja tagowania**|**Opis**|**Skrót klawiatury**|**Zbiorcze tagowanie skrótu klawiaturowego (w przypadku wielu problemów)**|
   |-----|-----|-----|-----|
   |R  <br/> |Odpowiednich  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |Nie dotyczy  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Pominąć  <br/> |Pominąć  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Gdy istnieje wiele problemów z plikiem, po otagowaniu jednego problemu wybór przechodzi do następnego problemu (jeśli istnieje).  

   - Słowa kluczowe zdefiniowane przez administratora lub menedżera spraw podczas wyróżniania słów kluczowych (słowa kluczowe z wyróżnioną konfiguracją \> istotności) będą wyświetlane (w określonych kolorach), aby ułatwić identyfikację odpowiednich plików podczas tagowania. Jeśli słowo kluczowe ma podwójne podkreślenie, można je kliknąć, aby wyświetlić etykietkę narzędzia z opisem słowa kluczowego.

     Opcjonalnie na karcie **Tag** kliknij pozycję **Ustawienia tagów** , aby ustawić następujące opcje:

      ![Ustawienia tagu istotności.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Tag zbiorczy**: użyj tej opcji, aby przypisać wiele problemów dla pliku, wybierając pozycję **Wszystkie** , aby ustawić tag dla wybranego pliku dla wszystkich problemów (przesłonięcia już oznaczonych problemów) lub wybierając **pozycję Reszta** , aby zastosować tag do pozostałych nieoznaczonych problemów. Wybrana opcja pozostaje w mocy dla wszystkich przypadków tego użytkownika, dopóki nie zostanie zmieniona przez tego użytkownika (ustawienie dotyczy wszystkich przypadków użytkownika).

   - **Tag automatyczny**: zaznacz to pole wyboru, aby ustawić inne problemy dotyczące pliku jako nieistotne po pojedynczym tagowaniu odpowiednim.

   - **Automatyczne przechodzenie**: zaznacz to pole wyboru, aby przenieść wyświetlony wybór pliku do następnego pliku podczas tagowania ostatniego lub jedynego nieoznaczonego problemu.

    Pominięte pliki nie będą brane pod uwagę do celów trenowania istotności i oceniania istotności.

3. Komentarze z bezpłatnym tekstem, skojarzone z plikiem, można wyświetlać i edytować za pośrednictwem opcji **Komentarz** na liście rozwijanej okienka po lewej stronie. (opcjonalnie)

4. Wskazówki dotyczące tagowania można wyświetlić, wybierając opcję **Wskazówki dotyczące tagowania** na liście rozwijanej w okienku po lewej stronie.

5. Po zakończeniu tagowania wszystkich plików na liście i przygotowaniu do obliczenia wyników kliknij pozycję **Oblicz**. Zostanie wyświetlona karta **Śledzenie** .  

## <a name="working-with-the-sample-files-list"></a>Praca z listą przykładowych plików

Lista przykładowych plików umożliwia wyświetlenie listy plików w przykładzie szkoleniowym i wykonanie różnych akcji na co najmniej jednym pliku. Na karcie **Tag** **istotności** \> w lewym okienku **Przykładowe pliki** zostanie wyświetlona lista przykładowych plików do przetwarzania z procesami oceny, trenowania, nadrabiania zaległości i niespójności.
  
1. Na karcie **Tag istotności \>** wybierz listę rozwijaną Przykładowe pliki w okienku po lewej stronie. Przykładowe pliki są wyświetlane w okienku po lewej stronie.

    ![Lista plików przykładowych tagów istotności.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. Wybierz określony przykład lub numer pliku, wprowadzając lub wybierając jego numer w polach **Przykład** lub **Plik** .

   - Numer sekwencji plików znajduje się w lewej kolumnie wyświetlonej listy plików na karcie **Tag** . Klikając nagłówek, oryginalna wyświetlana kolejność plików powraca do oryginalnej kolejności.

   - Kliknięcie wiersza pliku powoduje wyświetlenie jego zawartości w okienku po prawej stronie.

   - Nawiguj między plikami w bieżącym przykładzie, używając opcji dolnego paska menu. Ponadto dostępne są skróty klawiaturowe nawigacji:
  
     - Aby przejść do pierwszego pliku w przykładzie: `Shift + Ctrl + <`

     - Aby przejść do poprzedniego pliku w przykładzie: `Shift + <`

     - Aby przejść do następnego pliku w przykładzie: `Shift + >`

     - Aby przejść do ostatniego pliku w przykładzie: `Shift + Ctrl + >`
