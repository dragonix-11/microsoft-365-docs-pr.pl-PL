---
title: Statystyki i raporty kolekcji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak uzyskiwać dostęp do statystyk i raportów dla kolekcji roboczych i kolekcji, które zostały zatwierdzone do zestawu przeglądów w usłudze Microsoft Purview eDiscovery (Premium).
ms.openlocfilehash: 12152e0b81df6c61732fda068c593a91578861ee
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940318"
---
# <a name="collection-statistics-and-reports-in-microsoft-purview-ediscovery-premium"></a>Zbieranie statystyk i raportów w usłudze Microsoft Purview eDiscovery (Premium)

Po utworzeniu kolekcji roboczej możesz wyświetlić statystyki dotyczące pobranych elementów, takich jak lokalizacje zawartości zawierające najwięcej elementów spełniających kryteria wyszukiwania i liczbę elementów zwróconych przez zapytanie wyszukiwania. Możesz również wyświetlić podgląd podzestawu wyników.

Po zidentyfikowaniu zestawu dokumentów, które chcesz dokładniej zbadać, możesz dodać wyniki wyszukiwania do zestawu przeglądów w celu zbierania i przetwarzania.

## <a name="statistics-and-reports-for-draft-collections"></a>Statystyki i raporty dla kolekcji roboczych

W tej sekcji opisano statystyki dostępne dla kolekcji roboczych. Te statystyki są dostępne na **karcie Statystyki wyszukiwania** na stronie wysuwanej kolekcji roboczej.

### <a name="collection-estimates"></a>Szacowanie kolekcji

W tej sekcji przedstawiono graficzne podsumowanie szacowanych elementów zwróconych przez kolekcję. Wskazuje to liczbę elementów zgodnych z kryteriami wyszukiwania kolekcji. Te informacje zawierają informacje o szacowanej liczbie elementów zwracanych przez kolekcję.

![Szacowanie kolekcji dla kolekcji roboczej.](../media/AeDCollectionEstimates.png)

- **Szacowane elementy według lokalizacji**: całkowita liczba szacowanych elementów zwróconych przez kolekcję. Wyświetlana jest również określona liczba elementów znajdujących się w skrzynkach pocztowych i znajdujących się w witrynach.

- **Szacowane lokalizacje z trafieniami**: całkowita liczba lokalizacji zawartości zawierających elementy zwrócone przez kolekcję. Zostanie również wyświetlona określona liczba lokalizacji skrzynki pocztowej i lokacji.

- **Wolumin danych według lokalizacji (w MB)**: całkowity rozmiar wszystkich szacowanych elementów zwróconych przez kolekcję. Zostanie również wyświetlony określony rozmiar elementów skrzynki pocztowej i elementów witryny.

### <a name="condition-report"></a>Raport warunku

W tej sekcji przedstawiono statystyki dotyczące zapytania wyszukiwania kolekcji oraz liczbę szacowanych elementów, które pasowały do różnych części zapytania wyszukiwania. Te statystyki umożliwiają analizowanie liczby elementów odpowiadających poszczególnym składnikom zapytania wyszukiwania. Może to pomóc uściślić kryteria wyszukiwania dla kolekcji i w razie potrzeby zawęzić zakres kolekcji.

- **Typ lokalizacji**: typ lokalizacji zawartości, do których mają zastosowanie statystyki zapytania. Wartość **Exchange** wskazuje lokalizację skrzynki pocztowej; wartość **SharePoint** wskazuje lokalizację witryny.

- **Część**: część zapytania wyszukiwania, do których mają zastosowanie statystyki. **Podstawowa** wskazuje całe zapytanie wyszukiwania. **Słowo kluczowe** wskazuje, że statystyki w wierszu dotyczą określonego słowa kluczowego. Jeśli używasz listy słów kluczowych w przypadku zapytania wyszukiwania w kolekcji, statystyki dla każdego składnika zapytania są uwzględniane w tej tabeli.

- **Warunek**: rzeczywisty składnik (słowo kluczowe lub warunek) zapytania wyszukiwania, które zostało uruchomione dla kolekcji roboczej, która zwróciła statystyki wyświetlane w odpowiednim wierszu.

- **Lokalizacje z trafieniami**: liczba lokalizacji zawartości (określonych w kolumnie **Typ lokalizacji** ), które zawierają elementy zgodne z zapytaniem podstawowym lub kluczowym wymienionym w kolumnie **Warunek** .

- **Elementy**: liczba elementów (z określonej lokalizacji zawartości), które są zgodne z zapytaniem wymienionym w kolumnie **Warunek** . Jak wyjaśniono wcześniej, jeśli element zawiera wiele wystąpień słowa kluczowego, które jest wyszukiwane, jest on liczony tylko raz w tej kolumnie.

- **Rozmiar (MB)**: całkowity rozmiar wszystkich znalezionych elementów (w określonej lokalizacji zawartości), które są zgodne z zapytaniem wyszukiwania w kolumnie **Warunek** .

### <a name="top-locations"></a>Najważniejsze lokalizacje

W tej sekcji przedstawiono statystyki dotyczące określonych lokalizacji zawartości z największą większością elementów zwracanych przez kolekcję.

- Nazwa lokalizacji (adres e-mail skrzynek pocztowych i adres URL witryn).

- Typ lokalizacji (skrzynka pocztowa lub witryna).

- Szacowana liczba elementów w lokalizacji zawartości zwracanych przez kolekcję.

- Całkowity rozmiar szacowanych elementów w każdej lokalizacji zawartości.

## <a name="statistics-and-reports-for-committed-collections"></a>Statystyki i raporty dotyczące zatwierdzonych kolekcji

W tej sekcji opisano statystyki dostępne po zatwierdzeniu kolekcji w zestawie przeglądów, w tym rzeczywistą liczbę elementów dodanych do zestawu przeglądów. Te statystyki (oprócz ładowania informacji zestawu) zawierają historyczne informacje o zawartości dodanej do sprawy.

Po zatwierdzeniu kolekcji w zestawie przeglądów na stronie wysuwanej zatwierdzonego połączenia są wyświetlane następujące karty. Każda z tych kart zawiera różne typy informacji o kolekcji.

![Karty na stronie wysuwanej zatwierdzonej kolekcji.](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Zawartość kolekcji

Ta sekcja karty **Podsumowanie** zawiera statystyki i inne informacje o elementach, które zostały zebrane ze źródeł danych w kolekcji i dodane do zestawu przeglądów.

- **Łączna liczba wyodrębnionych elementów**. Całkowita liczba elementów dodanych do zestawu przeglądów. Ta liczba wskazuje sumę elementów nadrzędnych i elementów podrzędnych dodanych do zestawu przeglądów.

  > [!TIP]
  > Umieść kursor na paskach elementów nadrzędnych lub podrzędnych, aby wyświetlić całkowitą liczbę elementów nadrzędnych lub podrzędnych.

- **Elementy nadrzędne**. Liczba elementów zwróconych przez kolekcję, która została użyta do zbierania elementów, które zostały dodane do zestawu przeglądów. Ta liczba odpowiada (i jest równa) szacowanej liczbie elementów wyświetlanych w sekcji **Parametry kolekcji** . Liczba elementów nadrzędnych, które zbiera informacje, które zostały użyte do zbierania elementów, które zostały dodane do zestawu przeglądów.
 
   Element nadrzędny może zawierać wiele elementów podrzędnych. Na przykład wiadomość e-mail jest elementem nadrzędnym, jeśli zawiera dołączony plik lub załącznik w chmurze. W takim przypadku dołączony plik lub plik docelowy załącznika w chmurze jest uważany za element podrzędny. Po zatwierdzeniu kolekcji elementy nadrzędne i wszystkie odpowiednie elementy podrzędne (takie jak dołączone pliki i załączniki w chmurze) są dodawane do zestawu przeglądów jako pojedyncze elementy lub pliki.

- **Elementy podrzędne**. Liczba elementów podrzędnych dodanych do zestawu przeglądów. Tylko elementy podrzędne, które są załącznikami plików i załącznikami w chmurze, są dodawane do zestawu przeglądów jako pojedyncze pliki. Inne typy elementów podrzędnych, takie jak podpisy poczty e-mail i obrazy, są wyodrębniane z elementu nadrzędnego, a następnie przetwarzane przez optyczne rozpoznawanie znaków (OCR) w celu wyodrębnienia dowolnego tekstu z elementu podrzędnego. Tekst wyodrębniony z tych typów elementów podrzędnych jest następnie dodawany do elementu nadrzędnego, dzięki czemu można go wyświetlić w zestawie przeglądów. Nie dodając elementów podrzędnych do zestawu przeglądów jako oddzielnego pliku, funkcja zbierania elektronicznych materiałów dowodowych (Premium) pomaga usprawnić proces przeglądu, ograniczając liczbę potencjalnie nieistotnych elementów w zestawie przeglądów.

- **Unikatowe elementy**. Liczba unikatowych elementów dodanych do zestawu przeglądów. Unikatowe elementy są unikatowe dla zestawu przeglądów. Wszystkie elementy są unikatowe, gdy pierwsza kolekcja zostanie dodana do nowego zestawu przeglądów, ponieważ w zestawie przeglądów nie było żadnych poprzednich elementów.

- **Zidentyfikowane zduplikowane elementy**. Liczba elementów z kolekcji, które nie zostały dodane do zestawu przeglądów, ponieważ ten sam element już istnieje w zestawie przeglądów. Statystyki dotyczące zduplikowanych elementów mogą pomóc w wyjaśnieniu różnic między liczbą szacowanych elementów z kolekcji roboczej a rzeczywistą liczbą elementów dodanych do zestawu przeglądów.

### <a name="indexing"></a>Indeksowania

Sekcja **Indeksowanie** na karcie **Podsumowanie** zatwierdzonego zestawu przeglądów zawiera informacje indeksowania dotyczące elementów dodanych do zestawu przeglądów.

**Nowe indeksowane elementy**. Liczba elementów, które zostały nowo zindeksowane przed dodaniem ich do zestawu przeglądów. Przykładami nowo indeksowanego elementu są elementy podrzędne wyodrębnione z elementu nadrzędnego, a następnie indeksowane przed dodaniem ich do zestawu przeglądów. Ponadto elementy, które nie znajdują się w źródłach danych będących osobami nadzoru i nienadzorowanych lokalizacjach zawartości wymienionych na karcie **Źródła danych** w przypadku, są indeksowane przed dodaniem ich do przeglądu. Na przykład nowo indeksowane elementy będą zawierać elementy zebrane z dodatkowych lokalizacji.

**Zaktualizowano indeksowane elementy**. Liczba częściowo indeksowanych elementów, które zostały pomyślnie zindeksowane i dodane do zestawu przeglądów. Ta statystyka wskazuje częściowo zaindeksowane elementy z lokalizacjizawartościej i nienadzorowanych lokalizacji zawartości Karta **Źródła danych** , które zostały pomyślnie zindeksowane, gdy kolekcja została zatwierdzona do zestawu przeglądów.

**Błędy indeksowania**. Liczba częściowo indeksowanych elementów, których nie można było zindeksować przed dodaniem ich do zestawu przeglądów. Te elementy mogą wymagać korygowania błędów.

### <a name="collection-parameters"></a>Parametry kolekcji

W tej sekcji są wyświetlane informacje o kolekcji, które zostały użyte do zbierania elementów, które zostały dodane do zestawu przeglądów. Na tej karcie są wyświetlane informacje podobne do informacji na **karcie Statystyki wyszukiwania** . Ta sekcja zawiera szybkie ujęcie zapytania wyszukiwania używanego przez kolekcję, wyszukiwane lokalizacje zawartości i szacowane wyniki kolekcji. Jak wyjaśniono wcześniej, liczba szacowanych elementów w tej sekcji będzie równa liczbie elementów nadrzędnych wyświetlanych w sekcji **Zawartość kolekcji** .

### <a name="search-statistics-tab"></a>Karta Statystyki wyszukiwania

Statystyki wyświetlane na karcie **Statystyki wyszukiwania** to te same statystyki z ostatniego uruchomienia kolekcji roboczej. Obejmuje to szacowanie kolekcji, raport warunków i najważniejsze lokalizacje. Te informacje są zachowywane z kolekcji roboczej na potrzeby odwołania historycznego i można je porównać z rzeczywistą kolekcją, która została zatwierdzona w zestawie przeglądów.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Różnice między szacowanymi wersjami roboczymi kolekcji a rzeczywistą zatwierdzoną kolekcją

Po uruchomieniu kolekcji roboczej oszacowanie liczby elementów (i ich całkowitego rozmiaru) spełniających kryteria kolekcji jest wyświetlane na karcie **Podsumowanie** i w sekcji **Szacowane kolekcje** na **karcie Statystyki wyszukiwania** . Po zatwierdzeniu kolekcji roboczej do zestawu przeglądów rzeczywista liczba elementów (i ich całkowity rozmiar) dodano zestaw przeglądów, które często różnią się od szacowanych. W większości przypadków do zestawu przeglądów jest dodawanych więcej elementów niż oszacowano w wersji roboczej kolekcji. Na poniższej liście opisano najczęstsze przyczyny tych różnic i wskazówki dotyczące ich identyfikacji:

- **Elementy podrzędne**. Elementy podrzędne (takie jak załączniki plików i załączniki w chmurze), które są wyodrębniane z elementów nadrzędnych i dodawane jako pojedyncze pliki. Liczba elementów podrzędnych może zwiększyć liczbę elementów faktycznie dodanych do zestawu przeglądów. Ogólnie rzecz biorąc, liczba elementów nadrzędnych zidentyfikowanych w sekcji **Zawartość kolekcji** na karcie **Podsumowanie** zatwierdzonej kolekcji powinna być równa liczbie szacowanych elementów z kolekcji roboczej.

- **Zduplikowane elementy**. Elementy z kolekcji roboczej, które zostały już dodane do zestawu przeglądów w poprzedniej kolekcji, nie zostaną dodane. Jak wyjaśniono wcześniej, liczba zduplikowanych elementów w kolekcji jest wyświetlana w sekcji **Zawartość kolekcji** na karcie **Podsumowanie** .

- **Opcje konfiguracji kolekcji**. Po zatwierdzeniu kolekcji roboczej do zestawu przeglądów należy uwzględnić wątki konwersacji, załączniki w chmurze i wersje dokumentów. Żaden z tych elementów dodanych do zestawu przeglądów nie jest uwzględniony w oszacowaniach kolekcji roboczej. Są one identyfikowane i zbierane tylko podczas zatwierdzania kolekcji. Wybranie tych opcji najprawdopodobniej zwiększy liczbę elementów dodanych do zestawu przeglądów. 

    Na przykład wiele wersji dokumentów SharePoint nie jest uwzględnionych w szacowaniu dla kolekcji roboczej. Jeśli jednak wybierzesz opcję uwzględnienia wszystkich wersji dokumentu podczas zatwierdzania kolekcji roboczej, rzeczywista liczba (i całkowity rozmiar) elementów dodanych do zestawu przeglądów wzrośnie.

    Aby uzyskać więcej informacji na temat tych opcji, zobacz [Commit a draft collection to a review set (Zatwierdzanie kolekcji roboczej do zestawu przeglądów](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-ediscovery-premium)).

Poniżej przedstawiono inne powody, dla których szacowane wyniki kolekcji roboczej mogą różnić się od rzeczywistych zatwierdzonych wyników.

- **Sposób szacowania wyników dla kolekcji roboczych**. Oszacowanie wyników wyszukiwania zwracanych przez kolekcję roboczą to tylko oszacowanie (a nie rzeczywista liczba) elementów spełniających kryteria zapytania kolekcji. Aby skompilować oszacowanie elementów wiadomości e-mail, z bazy danych Exchange jest wymagana lista identyfikatorów wiadomości spełniających kryteria wyszukiwania. Jednak po zatwierdzeniu kolekcji do zestawu przeglądów kolekcja jest uruchamiana ponownie, a rzeczywiste komunikaty są pobierane z bazy danych Exchange. Różnice mogą więc wynikać ze sposobu określania szacowanej liczby elementów i rzeczywistej liczby elementów.

- **Zmiany zachodzą między godziną szacowania i zatwierdzania kolekcji roboczych**. Po zatwierdzeniu kolekcji roboczej do zestawu przeglądów wyszukiwanie jest uruchamiane ponownie w celu zebrania najnowszych elementów w indeksie wyszukiwania spełniających kryteria wyszukiwania. Możliwe, że dodatkowe elementy zostały utworzone, wysłane lub usunięte, które spełniają kryteria wyszukiwania w czasie między ostatnim uruchomieniem kolekcji roboczej a zobowiązaniem kolekcji roboczej do zestawu przeglądów. Istnieje również możliwość, że elementy, które znajdowały się w indeksie wyszukiwania podczas szacowania wyników kolekcji roboczej, nie są już dostępne, ponieważ zostały usunięte ze źródła danych przed zatwierdzeniem kolekcji. Jednym ze sposobów rozwiązania tego problemu jest określenie zakresu dat dla kolekcji. Innym sposobem jest wstrzymanie lokalizacji zawartości, aby elementy były zachowywane i nie mogły być czyszczone.

- **Elementy bez certyfikatu**. Jeśli kolekcja robocza zawierała przeszukiwanie wszystkich Exchange skrzynek pocztowych lub wszystkich witryn SharePoint, do zestawu przeglądów zostaną dodane tylko niezadeksowane elementy z lokalizacji zawartości, które zawierają elementy zgodne z kryteriami kolekcji. Innymi słowy, jeśli w skrzynce pocztowej lub witrynie nie zostaną znalezione żadne wyniki, żadne niezainicjowane elementy w tej skrzynce pocztowej lub witrynie nie zostaną dodane do zestawu przeglądów. Jednak niezainicjowane elementy ze wszystkich lokalizacji zawartości (nawet te, które nie zawierają elementów zgodnych z zapytaniem kolekcji) zostaną uwzględnione w szacowanych wynikach kolekcji.

    Alternatywnie, jeśli wersja robocza kolekcji zawierała określone lokalizacje zawartości (co oznacza, że określone skrzynki pocztowe lub witryny określone na stronie **Dodatkowe lokalizacje** w kreatorze kolekcji roboczej), nieweksportowane elementy (które nie są wykluczone przez kryteria zbierania) z lokalizacji zawartości określonych w wyszukiwaniu zostaną wyeksportowane. W tym przypadku szacowana liczba nieweksportowanych elementów i liczba nieweksportowanych elementów dodawanych do zestawu przeglądów powinna być taka sama.
