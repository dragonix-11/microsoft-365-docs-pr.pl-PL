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
description: Kolekcja robocza to wyszukiwanie zbierania elektronicznych materiałów dowodowych źródeł danych bez nadzoru w przypadku zbierania elektronicznych materiałów dowodowych (Premium), które zwraca oszacowanie wyszukiwania zgodne z zapytaniem wyszukiwania kolekcji. Możesz przejrzeć statystyki wyszukiwania, wyświetlić podgląd próbkowania elementów oraz poprawić i ponownie uruchomić kolekcję przed zatwierdzeniem wyników w zestawie przeglądów.
ms.openlocfilehash: 2178e836809a24edec6d3d184ef8b699bec87bb5
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997081"
---
# <a name="create-a-draft-collection-in-ediscovery-premium"></a>Tworzenie kolekcji roboczej w usłudze eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po zidentyfikowaniu opiekunów i wszelkich źródeł danych niebędących opiekunami w tej sprawie możesz zidentyfikować i zlokalizować odpowiedni zestaw dokumentów. Można to zrobić za pomocą narzędzia Kolekcje do wyszukiwania źródeł danych pod kątem odpowiedniej zawartości. Można to zrobić, tworząc kolekcję, która wyszukuje określone źródła danych pod kątem zawartości zgodnej z kryteriami wyszukiwania. Możesz utworzyć *kolekcję roboczą*, która jest oszacowaniem znalezionych elementów, lub możesz utworzyć kolekcję, która automatycznie dodaje elementy do zestawu przeglądów. Podczas tworzenia kolekcji roboczej można wyświetlać informacje o szacowanych wynikach dopasowanych do zapytania wyszukiwania, takie jak całkowita liczba i rozmiar znalezionych elementów, różne źródła danych, w których zostały znalezione, oraz statystyki dotyczące zapytania wyszukiwania. Możesz również wyświetlić podgląd przykładu elementów, które zostały zwrócone przez kolekcję. Korzystając z tych statystyk, możesz zmienić zapytanie wyszukiwania i ponownie uruchomić kolekcję roboczą, aby zawęzić wyniki. Gdy wyniki kolekcji będą zadowalające, możesz zatwierdzić kolekcję w zestawie przeglądów. Po zatwierdzeniu kolekcji roboczej elementy zwracane przez kolekcję są dodawane do zestawu przeglądów do przeglądania, analizy i eksportowania.

## <a name="before-you-create-a-draft-collection"></a>Przed utworzeniem kolekcji roboczej

- Przed utworzeniem kolekcji roboczej dodaj opiekunów i źródła danych bez opieki. Jest to wymagane, aby można było wybrać źródła danych podczas tworzenia kolekcji roboczej. Więcej informacji można znaleźć w następujących artykułach:

  - [Dodaj opiekunów do sprawy](add-custodians-to-case.md)

  - [Dodaj źródła danych bez opiekunów do sprawy](non-custodial-data-sources.md)

- Możesz przeszukać dodatkowe źródła danych (te, które nie zostały dodane do sprawy jako lokalizacje opieki lub bez opieki) w projekcie kolekcji pod kątem zawartości, która może być istotna dla sprawy. Te źródła danych mogą obejmować skrzynki pocztowe, witryny SharePoint i Teams. Jeśli ta sytuacja ma zastosowanie do Twojego przypadku, skompiluj listę tych źródeł danych, aby można było dodać je do kolekcji.

## <a name="create-a-draft-collection"></a>Tworzenie kolekcji roboczej

1. W portalu zgodności usługi Microsoft Purview otwórz przypadek zbierania elektronicznych materiałów dowodowych (Premium), a następnie wybierz kartę **Kolekcje**.

2. Na stronie **Kolekcje** wybierz pozycję **Nowa** **kolekcjaStandard** >  kolekcja.

3. Wpisz nazwę (wymagane) i opis (opcjonalnie) dla kolekcji. Po utworzeniu kolekcji nie można zmienić nazwy, ale można zmodyfikować opis.

4. Na stronie **Źródła danych powierniczych** wykonaj jedną z następujących czynności, aby zidentyfikować źródła danych nadzoru w celu zbierania zawartości:

   - Kliknij **pozycję Wybierz opiekunów,** aby przeszukać określonych opiekunów, którzy zostali dodani do sprawy. Jeśli użyjesz tej opcji, zostanie wyświetlona lista opiekunów spraw. Wybierz co najmniej jednego opiekuna. Po wybraniu i dodaniu opiekunów możesz również wybrać określone źródła danych, aby wyszukać każdego opiekuna. Te wyświetlane źródła danych zostały określone podczas dodawania opiekuna do sprawy.

   - Kliknij przełącznik **Wybierz wszystkie** , aby wyszukać wszystkich opiekunów, którzy zostali dodani do sprawy. Po wybraniu tej opcji przeszukiwane są wszystkie źródła danych dla wszystkich opiekunów.

5. Na stronie **Źródła danych bez nadzoru** wykonaj jedną z następujących czynności, aby zidentyfikować źródła danych nienadzorowania w celu zbierania zawartości:

   - Kliknij **pozycję Wybierz źródła danych nienadzorujące,** aby wybrać określone źródła danych, które nie są chronione, które zostały dodane do sprawy. Jeśli używasz tej opcji, zostanie wyświetlona lista źródeł danych. Wybierz co najmniej jedno z tych źródeł danych.

   - Kliknij przełącznik **Wybierz wszystkie** , aby wybrać wszystkie źródła danych, które nie są chronione, które zostały dodane do sprawy.

6. Na stronie **Dodatkowe źródła danych** możesz wybrać inne skrzynki pocztowe i witryny do wyszukiwania w ramach kolekcji. Tego typu źródła danych nie zostały dodane jako lokalizacje danych bez nadzoru w tym przypadku. Dostępne są również dwie opcje wyszukiwania dodatkowych źródeł danych:

   - Aby wyszukać we wszystkich lokalizacjach zawartości określoną usługę (Exchange skrzynki pocztowe, witryny SharePoint i OneDrive lub Exchange foldery publiczne), kliknij odpowiedni przełącznik **Wybierz wszystko** w kolumnie **Stan**. Ta opcja spowoduje przeszukanie wszystkich lokalizacji zawartości w wybranej usłudze.

   - Aby wyszukać określoną lokalizację zawartości dla usługi, kliknij odpowiedni przełącznik **Wybierz wszystkie** w kolumnie **Stan**, a następnie kliknij pozycję **Użytkownicy, grupy lub zespoły** (dla Exchange skrzynek pocztowych) lub **Wybierz witryny** dla witryn (SharePoint i OneDrive witryn), aby wyszukać określone lokalizacje zawartości.

7. Na stronie **Warunki** możesz utworzyć zapytanie wyszukiwania służące do zbierania elementów ze źródeł danych zidentyfikowanych na poprzednich stronach kreatora. Możesz wyszukiwać słowa kluczowe, pary właściwości:wartości lub użyć listy słów kluczowych. Możesz również dodać różne warunki wyszukiwania, aby zawęzić zakres kolekcji. Aby uzyskać więcej informacji, zobacz [Tworzenie zapytań wyszukiwania dla kolekcji](building-search-queries.md).

8. Na stronie **Zapisz jako wersję roboczą lub dodaj do przeglądu zestawu** wybierz pozycję **Zapisz kolekcję jako wersję roboczą**.

   > [!NOTE]
   > Inna opcja na tej stronie umożliwia zbieranie elementów i dodawanie ich bezpośrednio do zestawu przeglądów. Zamiast tworzyć kolekcję roboczą, dla których można przeglądać statystyki i wyświetlać podgląd przykładowych wyników kolekcji, ta opcja pomija ten proces i automatycznie dodaje kolekcję do zestawu przeglądów. Jeśli wybierzesz drugą opcję dodawania kolekcji do zestawu przeglądów, masz dodatkowe ustawienia do skonfigurowania, takie jak zbieranie całych wątków konwersacji czatu w Microsoft Teams i Yammer oraz zbieranie załączników w chmurze (*nazywanych również nowoczesnymi załącznikami*). Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Zatwierdzanie kolekcji roboczej do zestawu przeglądów](commit-draft-collection.md).

9. Na stronie **Przeglądanie kolekcji** możesz przejrzeć i zaktualizować ustawienia kolekcji skonfigurowane na poprzednich stronach.

   - Karta **Podsumowanie**: przejrzyj i zmodyfikuj nazwę i opis kolekcji, kryteria wyszukiwania kolekcji, dodatkowe lokalizacje danych i typ kolekcji.

   - Karta **Źródła**: przejrzyj i zmodyfikuj źródła danych dla kolekcji bez nadzoru.

10. Kliknij pozycję **Prześlij** , aby utworzyć kolekcję roboczą. Zostanie wyświetlona strona potwierdzająca, że kolekcja została utworzona.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Co się stanie po utworzeniu kolekcji roboczej

Po utworzeniu kolekcji roboczej jest ona wyświetlana na stronie **Kolekcje** w przypadku, a stan pokazuje, że jest w toku. Zadanie o nazwie **Przygotowywanie podglądu wyszukiwania i oszacowań** jest również tworzone i wyświetlane na stronie **Zadania** w tym przypadku.

Podczas procesu zbierania wersji roboczych funkcja eDiscovery (Premium) wykonuje szacowanie wyszukiwania przy użyciu kryteriów wyszukiwania i źródeł danych określonych w kolekcji. Funkcja zbierania elektronicznych materiałów dowodowych (Premium) przygotowuje również próbkowanie elementów, które można wyświetlić w wersji zapoznawczej. Po zakończeniu kolekcji zostaną zaktualizowane następujące kolumny i odpowiednie wartości na stronie **Kolekcja** :

![Stany stanu kolekcji roboczej.](../media/DraftCollectionStatus.png)

- **Stan**: wskazuje stan i typ kolekcji. Wartość **Szacowana** wskazuje, że kolekcja robocza została ukończona. Ta sama wartość wskazuje również, że kolekcja jest kolekcją roboczą i że nie została dodana do zestawu przeglądów. Wartość **Zatwierdzone** w kolumnie **Stan** wskazuje, że kolekcja została dodana do zestawu przeglądów.

- **Stan szacowania**: wskazuje stan szacowanych wyników wyszukiwania oraz to, czy oszacowania i statystyki wyszukiwania są gotowe do przeglądu. Wartość **Successful** wskazuje, że wyniki kolekcji roboczej są gotowe do przeglądu. Po pierwszym przesłaniu kolekcji roboczej jest wyświetlana wartość **W toku** , aby wskazać, że kolekcja jest nadal uruchomiona

- **Stan wersji zapoznawczej**: wskazuje stan przykładowych elementów, które można wyświetlić w wersji zapoznawczej. Wartość **Successful** wskazuje, że elementy są gotowe do wersji zapoznawczej. Po pierwszym przesłaniu kolekcji roboczej jest wyświetlana wartość **W toku** , aby wskazać, że kolekcja jest nadal uruchomiona.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Następne kroki po ukończeniu kolekcji roboczej

Po pomyślnym ukończeniu kolekcji roboczej można wykonywać różne zadania. Aby wykonać większość tych zadań, wystarczy przejść do karty **Kolekcje** i kliknąć nazwę kolekcji roboczej, aby wyświetlić stronę wysuwaną.

![Strona wysuwana dla kolekcji roboczej.](../media/DraftCollectionFlyoutPage.png)

Oto lista czynności, które można wykonać na stronie wysuwanej kolekcji:

- Wybierz kartę **Podsumowanie** , aby wyświetlić podsumowanie informacji o kolekcji i szacowanych wynikach wyszukiwania zwróconych przez kolekcję. Obejmuje to całkowitą liczbę elementów i rozmiar szacowanych wyników wyszukiwania, liczbę skrzynek pocztowych i witryn zawierających wyniki wyszukiwania oraz warunki wyszukiwania (jeśli są używane) używane do określania zakresu kolekcji.

- Wybierz kartę **Źródła danych** , aby wyświetlić listę opiekunów i źródeł danych bez nadzoru), które zostały przeszukane w kolekcji. Wszystkie dodatkowe lokalizacje zawartości, które były wyszukiwane, są wyświetlane w obszarze **Lokalizacje** na karcie **Podsumowanie** .

- Wybierz kartę **Statystyki wyszukiwania** , aby wyświetlić statystyki dotyczące kolekcji. Obejmuje to całkowitą liczbę i rozmiar elementów znalezionych w każdej usłudze (na przykład Exchange skrzynki pocztowe lub SharePoint lokacje) oraz raport warunków, który wyświetla statystyki dotyczące liczby elementów zwracanych przez różne składniki zapytania wyszukiwania używanego przez kolekcję. Aby uzyskać więcej informacji, zobacz [Statystyki kolekcji i raporty](collection-statistics-reports.md).

- Kliknij **pozycję Przejrzyj przykład** (znajdujący się w dolnej części strony wysuwanej), aby wyświetlić podgląd przykładu elementów zwróconych przez kolekcję.

- Zatwierdź kolekcję roboczą w zestawie przeglądów (klikając pozycję **ActionsEdit** >  collection). Oznacza to ponowne uruchomienie kolekcji (przy użyciu bieżących ustawień) i dodanie elementów zwróconych przez kolekcję do zestawu przeglądów. Jak wyjaśniono wcześniej, podczas dodawania kolekcji do zestawu przeglądów można również skonfigurować dodatkowe ustawienia (takie jak wątki konwersacji i załączniki oparte na chmurze). Aby uzyskać więcej informacji i instrukcje krok po kroku, zobacz [Zatwierdzanie kolekcji roboczej w zestawie przeglądów](commit-draft-collection.md).

## <a name="manage-a-draft-collection"></a>Zarządzanie kolekcją roboczą

Możesz użyć opcji w menu **Akcje** na stronie wysuwanej kolekcji roboczej, aby wykonywać różne zadania zarządzania.

![Opcje w menu Akcje dla kolekcji roboczej.](../media/DraftCollectionActionsMenu.png)

Poniżej przedstawiono opisy opcji zarządzania.

- **Edytuj kolekcję**: zmień ustawienia kolekcji roboczej. Po wprowadzeniu zmian możesz ponownie uruchomić kolekcję i zaktualizować oszacowania i statystyki wyszukiwania. Jak wyjaśniono wcześniej, ta opcja służy do zatwierdzania kolekcji roboczej do zestawu przeglądów.  

- **Usuń kolekcję**: usuń kolekcję roboczą. Pamiętaj, że po zatwierdzeniu kolekcji roboczej do zestawu przeglądów nie można go usunąć.

- **Szacowane odświeżanie**: uruchom ponownie zapytanie (względem źródeł danych) określone w kolekcji roboczej, aby zaktualizować oszacowania i statystyki wyszukiwania.

- **Eksportuj jako raport**: eksportuje informacje o kolekcji roboczej do pliku CSV, który można pobrać na komputer lokalny. Raport eksportu zawiera następujące informacje:

  - Tożsamość każdej lokalizacji zawartości zawierającej elementy zgodne z zapytaniem wyszukiwania w kolekcji roboczej. Te lokalizacje są zazwyczaj skrzynkami pocztowymi lub witrynami.
  
  - Całkowita liczba elementów w każdej lokalizacji zawartości.
  
  - Całkowity rozmiar (w bajtach) elementów w każdej lokalizacji zawartości.

  - Usługa (na przykład Exchange lub SharePoint), w której znajduje się lokalizacja zawartości.

- **Kopiowanie kolekcji**: utwórz nową kolekcję roboczą, kopiując ustawienia z istniejącej kolekcji. Musisz użyć innej nazwy dla nowej kolekcji. Masz również możliwość zmodyfikowania ustawień przed przesłaniem nowej kolekcji. Po przesłaniu zapytania wyszukiwania zostanie uruchomione i zostaną wygenerowane nowe oszacowania i statystyki. Jest to dobry sposób na szybkie utworzenie dodatkowej kolekcji roboczej, a następnie zmodyfikowanie wybranych ustawień w razie potrzeby przy zachowaniu informacji w oryginalnej kolekcji. Pozwala to również łatwo porównać wyniki dwóch podobnych kolekcji.

> [!NOTE]
> Po zatwierdzeniu kolekcji roboczej w zestawie przeglądów można skopiować tylko kolekcję i wyeksportować raport.
