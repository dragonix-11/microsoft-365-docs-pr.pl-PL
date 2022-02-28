---
title: Tworzenie kolekcji roboczej
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Kolekcja robocza to wyszukiwanie w zbierania elektronicznych materiałów dowodowych źródeł danych, które nie są zaimkiwowe i niedobędne źródła danych w przypadku Advanced eDiscovery, które zwraca szacowaną wartość wyszukiwania, która jest taka, jak zapytanie wyszukiwania kolekcji. Możesz przeglądać statystyki wyszukiwania, wyświetlać podgląd próbki elementów oraz poprawiać i ponownie uruchomić kolekcję przed zatwierdzeniem wyników do zestawu recenzji.
ms.openlocfilehash: 5a65bc97f44b2b5bf32f57f52000e66d68dc428a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988346"
---
# <a name="create-a-draft-collection-in-advanced-ediscovery"></a>Tworzenie kolekcji roboczej w programie Advanced eDiscovery

Po zidentyfikowaniu zatrzymań i źródeł danych bez przechowywania danych dla sprawy możesz zidentyfikować i znaleźć odpowiedni zestaw dokumentów. Można to zrobić za pomocą narzędzia Kolekcje w celu wyszukiwania źródeł danych w celu wyszukania odpowiedniej zawartości. W tym celu należy utworzyć kolekcję, która przeszukuje określone źródła danych w poszukiwaniu zawartości, która jest spełniają kryteria wyszukiwania. Możesz utworzyć kolekcję roboczą *, która* stanowi szacowany zbiór znalezionych elementów, lub kolekcję, która automatycznie dodaje te elementy do zestawu recenzji. Podczas tworzenia kolekcji roboczej można uzyskać informacje o szacowanych wynikach, które pasują do zapytania wyszukiwania, takie jak całkowita liczba i rozmiar znalezionych elementów, różne źródła danych, w których zostały odnalezione, oraz statystyki dotyczące zapytania wyszukiwania. Możesz również wyświetlić podgląd przykładowych elementów zwróconych przez kolekcję. Za pomocą tych statystyk możesz zmienić zapytanie wyszukiwania i ponownie uruchomić kolekcję roboczą, aby zawęzić wyniki. Po zakończeniu zbierania danych możesz zatwierdzić kolekcję do zestawu recenzji. Po zatwierdzeniu wersji roboczej kolekcji elementy zwrócone przez kolekcję są dodawane do zestawu recenzji do przeglądania, analizy i eksportowania.

## <a name="before-you-create-a-draft-collection"></a>Przed utworzeniem kolekcji roboczej

- Przed utworzeniem zbioru roboczego dodaj do sprawy źródła danych, które nie są odimowywne. Jest to wymagane, aby można było wybrać źródła danych podczas tworzenia kolekcji roboczej. Więcej informacji można znaleźć w następujących artykułach:

  - [Dodawanie osób do sprawy](add-custodians-to-case.md)

  - [Dodawanie do sprawy niebędące niedobczasami źródeł danych](non-custodial-data-sources.md)

- Możesz wyszukać dodatkowe źródła danych (te, które nie zostały dodane do sprawy jako lokalizacje typu pobłędnie lub niebędące elementami, które nie są dostępne do danej sprawy) w wersji roboczej kolekcji w celu wyszukania zawartości, która może być istotny w danym przypadku. Te źródła danych mogą obejmować skrzynki pocztowe, SharePoint witryny i Teams. Jeśli taka sytuacja dotyczy Twojej sprawy, skompilowaj listę tych źródeł danych, aby można je było dodać do kolekcji.

## <a name="create-a-draft-collection"></a>Tworzenie kolekcji roboczej

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, a następnie wybierz **kartę** Kolekcje.

2. Na stronie **Kolekcje** wybierz pozycję **Nowa** **kolekcjaStandardowa** >  kolekcja.

3. Wpisz nazwę (wymaganą) i opis kolekcji (opcjonalnie). Po utworzeniu kolekcji nie można zmienić jej nazwy, ale można zmodyfikować opis.

4. Na **stronieSzybkie źródła** danych wykonaj jedną z następujących czynności w celu zidentyfikowania tych źródeł danych, z których mają być zbierane:

   - Kliknij **pozycję Wybierz opiekunów** , aby przeszukać określone schłody, które zostały dodane do sprawy. W przypadku użycia tej opcji zostanie wyświetlona lista elementów elementów- Wybierz jeden lub więcej osób, które się w nich zatrzymają. Po wybraniu i dodaniu osób, które się od nich wybrzmią, można także wybrać określone źródła danych do wyszukania każdego z nich. Te wyświetlane źródła danych zostały określone podczas dobierania danych do sprawy przez osoby przechowacze.

   - Kliknij przełącznik **Zaznacz wszystko** , aby przeszukać wszystkie wyszukiwarki, które zostały dodane do sprawy. Po wybraniu tej opcji przeszukane zostaną wszystkie źródła danych dla wszystkich osób, które przechowywają dane.

5. Na stronie **Niebędące** źródłami danych wykonaj jedną z następujących czynności w celu zidentyfikowania źródeł danych, z których mają być zbierane dane, z których nie są one zbędne:

   - Kliknij **pozycję Wybierz niebędące jakością źródła** danych, aby wybrać określone, niebędące jakością źródła danych, które zostały dodane do sprawy. W przypadku użycia tej opcji zostanie wyświetlona lista źródeł danych. Zaznacz co najmniej jedno z tych źródeł danych.

   - Kliknij przełącznik **Zaznacz wszystko** , aby zaznaczyć wszystkie źródła danych bez przechowywania danych, które zostały dodane do sprawy.

6. Na stronie **Dodatkowe źródła** danych możesz wybrać inne skrzynki pocztowe i witryny do przeszukania w ramach kolekcji. Tego typu źródła danych nie zostały dodane w takim przypadku jako lokalizacje danych o niedobczasowych ani niedobczasowych. Podczas wyszukiwania dodatkowych źródeł danych dostępne są również dwie opcje:

   - Aby przeszukać wszystkie lokalizacje zawartości dla określonej usługi (skrzynek pocztowych usługi Exchange, witryn SharePoint i OneDrive lub Exchange folderów publicznych), kliknij odpowiedni przełącznik Zaznacz wszystko w kolumnie **Stan**. Ta opcja spowoduje przeszukanie wszystkich lokalizacji zawartości w wybranej usłudze.

   - Aby wyszukać konkretną lokalizację zawartości dla usługi, kliknij odpowiedni przełącznik  Zaznacz wszystko w kolumnie **Stan**, a następnie kliknij pozycję Użytkownicy **,** grupy lub zespoły (w przypadku skrzynek pocztowych programu Exchange) lub Wybierz  witryny dla (witryny usługi SharePoint i OneDrive), aby przeszukać konkretne lokalizacje zawartości.

7. Na stronie **Warunki** możesz utworzyć zapytanie wyszukiwania, które będzie używane do zbierania elementów ze źródeł danych zidentyfikowanych na poprzednich stronach kreatora. Możesz wyszukiwać słowa kluczowe, pary właściwość:wartość lub lista słów kluczowych. Możesz również dodać różne warunki wyszukiwania, aby zawęzić zakres kolekcji. Aby uzyskać więcej informacji, zobacz [Tworzenie zapytań wyszukiwania dla kolekcji](building-search-queries.md).

8. Na stronie **Zapisz jako wersje robocze lub Dodaj do recenzji wybierz** pozycję **Zapisz kolekcję jako wersja robocza**.

   > [!NOTE]
   > Druga opcja na tej stronie umożliwia zbieranie elementów i dodawanie ich bezpośrednio do zestawu recenzji. Zamiast tworzyć kolekcję roboczą, w przypadku których można przeglądać statystyki dotyczące przykładowych wyników kolekcji i wyświetlać ich podgląd, ta opcja pomija ten proces i automatycznie dodaje kolekcję do zestawu recenzji. Jeśli wybierzesz drugą opcję, aby dodać kolekcję do zestawu recenzji, będziesz mieć dodatkowe ustawienia do skonfigurowania, takie jak zbieranie całych wątków konwersacji czatu w programach Microsoft Teams i Yammer oraz zbieranie załączników w chmurze (nazywanych również nowoczesnych załącznikami *).* Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji](commit-draft-collection.md).

9. Na **stronie Przeglądanie kolekcji** możesz przejrzeć i zaktualizować ustawienia kolekcji skonfigurowane na poprzednich stronach.

   - **Karta** Podsumowanie: Przejrzyj i zmodyfikuj nazwę i opis kolekcji, kryteria wyszukiwania kolekcji, dodatkowe lokalizacje danych oraz typ kolekcji.

   - **Karta** Źródła: przejrzyj i zmodyfikuj źródła danych, które nie są przechłodne dla zbioru.

10. Kliknij **przycisk Prześlij** , aby utworzyć kolekcję roboczą. Zostanie wyświetlona strona z potwierdzeniem utworzenia kolekcji.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Co się stanie po utworzeniu kolekcji roboczej

Po utworzeniu kolekcji roboczej jest ona wymieniona na  stronie Kolekcje w przypadku, a jej stan pokazuje, że jest w toku. Zostanie również **utworzone zadanie o nazwie Przygotowywanie podglądu wyszukiwania** i oszacowań, które w tym  przypadku będzie wyświetlane na stronie Zadania.

W trakcie procesu zbierania wersji Advanced eDiscovery przeprowadza szacowaną wartość wyszukiwania przy użyciu kryteriów wyszukiwania i źródeł danych określonych w zbiorze. Advanced eDiscovery również przygotowanie próbki elementów, których podgląd można wyświetlić. Po zakończeniu kolekcji zostaną zaktualizowane następujące kolumny i odpowiadające im wartości  na stronie Kolekcja:

![Stany dla kolekcji roboczej.](../media/DraftCollectionStatus.png)

- **Stan**. Wskazuje stan i typ kolekcji. Wartość **szacowana wskazuje** , że kolekcja robocza jest ukończona. Ta sama wartość wskazuje również, że kolekcja jest kolekcją roboczą i nie została dodana do zestawu recenzji. Wartość Projekt **zatwierdzone** w kolumnie **Stan** wskazuje, że kolekcja została dodana do zestawu recenzji.

- **Szacowany stan**: określa stan szacowanych wyników wyszukiwania oraz wskazuje, czy dane szacunkowe i statystyki wyszukiwania są gotowe do sprawdzenia. Wartość " **Pomyślnie"** wskazuje, że wyniki zbioru roboczego są gotowe do recenzji. Po przesłaniu najpierw kolekcji roboczej jest wyświetlana wartość W **toku** , która wskazuje, że kolekcja nadal działa

- **Stan podglądu**: określa stan elementów przykładowych, których podgląd można wyświetlić. Wartość "Pomyślnie **"** wskazuje, że elementy są gotowe do podglądu. Po przesłaniu najpierw kolekcji roboczej jest wyświetlana wartość  W toku, która wskazuje, że kolekcja jest nadal uruchomiona.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Następne kroki po ukończeniu wersji roboczej kolekcji

Po pomyślnym ukończeniu wersji roboczej kolekcji możesz wykonywać różne zadania. Aby wykonać większość z tych zadań, po prostu przejdź na **kartę** Kolekcje i kliknij nazwę kolekcji roboczej, aby wyświetlić stronę wysuwu.

![Wysuowana strona dla kolekcji roboczej.](../media/DraftCollectionFlyoutPage.png)

Oto lista czynności, które można robić na stronie wysuwu kolekcji:

- Wybierz **kartę Podsumowanie** , aby wyświetlić informacje podsumowujące kolekcję i szacowane wyniki wyszukiwania zwrócone przez tę kolekcję. Obejmuje to całkowitą liczbę elementów i rozmiar szacowanych wyników wyszukiwania, liczbę skrzynek pocztowych i witryn zawierających wyniki wyszukiwania oraz warunki wyszukiwania (jeśli są używane) używane do zawę gromadzenia.

- Wybierz **kartę Źródła** danych, aby wyświetlić listę elementów przechłodowanych i niebędące źródłem danych), które zostały przeszukane w kolekcji. Wszelkie dodatkowe lokalizacje zawartości, które były przeszukiwane, są wymienione w obszarze **Lokalizacje** na **karcie Podsumowanie** .

- Wybierz **kartę Statystyka** wyszukiwania, aby wyświetlić statystyki dotyczące kolekcji. Obejmuje to łączną liczbę i rozmiar elementów znalezionych w poszczególnych usługach (na przykład skrzynki pocztowe lub witryny programu Exchange SharePoint) oraz raport warunków, w którym są wyświetlane statystyki dotyczące liczby elementów zwracanych przez różne składniki zapytania wyszukiwania używanego przez tę kolekcję. Aby uzyskać więcej informacji, zobacz [Statystyki i raporty dotyczące zbierania danych](collection-statistics-reports.md).

- Kliknij **pozycję Przejrzyj przykład** (znajdującą się u dołu strony wysuwu), aby wyświetlić podgląd przykładowych elementów zwróconych przez kolekcję.

- Zatwierdzenie wersji roboczej kolekcji do zestawu recenzji (przez kliknięcie **pozycji ActionsEdit** >  **kolekcji**). Oznacza to, że ponownie uruchomić kolekcję (przy użyciu bieżących ustawień) i dodać elementy zwrócone przez kolekcję do zestawu recenzji. Jak wyjaśniono wcześniej, podczas dodawania kolekcji do zestawu recenzji można także skonfigurować dodatkowe ustawienia (takie jak wątki konwersacji i załączniki w chmurze). Aby uzyskać więcej informacji i instrukcje krok po kroku, zobacz [Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji](commit-draft-collection.md).

## <a name="manage-a-draft-collection"></a>Zarządzanie kolekcją roboczą

Za pomocą **opcji w menu** Akcje na wysuwanych stronie kolekcji wersji roboczej możesz wykonywać różne zadania zarządzania.

![Opcje w menu Akcje dla kolekcji roboczej.](../media/DraftCollectionActionsMenu.png)

Oto opisy opcji zarządzania.

- **Edytuj kolekcję**: zmienianie ustawień kolekcji roboczej. Po wymurzeniu zmian możesz ponownie uruchomić kolekcję i zaktualizować oszacowania wyszukiwania oraz statystyki. Jak wyjaśniono wcześniej, ta opcja umożliwia zatwierdzenie wersji roboczej kolekcji do zestawu recenzji.  

- **Usuwanie kolekcji**: Usuwanie kolekcji roboczej. Zwróć uwagę, że po zawęzieniu zbioru roboczego do zestawu recenzji nie można go usunąć.

- **Oszacowania odświeżania**: Ponownie uruchomić zapytanie (względem źródeł danych) określonych w wersji roboczej zbioru w celu zaktualizowania oszacowania i statystyki wyszukiwania.

- **Eksportuj jako raport**: eksportuje informacje o wersji roboczej kolekcji do pliku CSV, który można pobrać na komputer lokalny. Raport eksportu zawiera następujące informacje:

  - Tożsamość każdej lokalizacji zawartości zawierającej elementy zgodne z zapytaniem wyszukiwania w wersji roboczej kolekcji. Te lokalizacje to zazwyczaj skrzynki pocztowe lub witryny.
  
  - Całkowita liczba elementów w poszczególnych lokalizacjach zawartości.
  
  - Całkowity rozmiar (w bajtach) elementów w poszczególnych lokalizacjach zawartości.

  - Usługa (na przykład Exchange lub SharePoint), w której znajduje się lokalizacja zawartości.

- **Kopiowanie kolekcji**: utwórz nową kolekcję roboczą, kopiując ustawienia z istniejącej kolekcji. Należy użyć innej nazwy dla nowej kolekcji. Możesz również zmodyfikować ustawienia przed przesłaniem nowej kolekcji. Po przesłaniu zapytania wyszukiwania zostanie ono uruchomione i zostaną wygenerowane nowe oszacowania i statystyki. Jest to dobry sposób na szybkie utworzenie dodatkowej wersji roboczej kolekcji, a następnie zmodyfikowanie wybranych ustawień w razie potrzeby przy zachowaniu informacji w oryginalnej kolekcji. Pozwala to również łatwo porównać wyniki dwóch podobnych kolekcji.

> [!NOTE]
> Gdy wersja robocza kolekcji zostanie zatwierdzone do zestawu recenzji, można skopiować kolekcję i wyeksportować raport.
