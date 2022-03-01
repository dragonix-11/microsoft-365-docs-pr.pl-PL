---
title: Omówienie kolekcji w aplikacji Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Kolekcje w Advanced eDiscovery w celu wyszukania i zbierania zawartości, która jest względna dla Twojej sprawy lub śledztwa.
ms.openlocfilehash: 8ccefb69463a2c518b0e0882a94bba81139e97eb
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014901"
---
# <a name="learn-about-collections-in-advanced-ediscovery"></a>Informacje o kolekcjach w aplikacji Advanced eDiscovery

W przypadku gdy organizacje mają do czynienia ze zbieraniem wiadomości i treści, które mogą być istotne w związku z prowadzonym śledztwem lub potencjalnym postępowaniem sądowym, w najlepszy razie mogą stawić przed nich istotne wyzwanie. We współczesnym miejscu pracy ilość, różnorodność i szybkość zawartości umożliwia innowację i pracę zdalną, a także rozszerza wymagania i proces zarządzania kolekcjami na potrzeby badań zbierania elektronicznych materiałów dowodowych.

Przepływ pracy kolekcji stwarza poważne problemy techniczne związane z wyodrębnianiem zawartości z natywnych lokalizacji i źródeł. Jest także krytycznym punktem oceny i strategii dla typowych scenariuszy sporu sądowego lub śledztwa. Gdy organizacje rozpoczynają ocenę badania, na początku zadawać pytania, kto był zaangażowany? Po zidentyfikowaniu ludzi, którzy się w to zaangażowali, można je szybko umieścić w a hold, aby zachować odpowiednią zawartość. Kolejne pytanie brzmi, co się stało? Aby odpowiedzieć na drugie podstawowe pytanie dotyczące dowolnego badania, menedżerowie muszą zwrócić się do danych. Aby szybko ocenić najbardziej trafną zawartość w pytaniu, jakie miało miejsce, menedżerowie zaczynają uściślić cel pytania, aby mieć pewność, że wyniki zbierania danych są wyczerpujące, nie są zbyt szerokie.

Kolekcje w Advanced eDiscovery ułatwiają menedżerom zbierania elektronicznych materiałów dowodowych szybkie wyszukiwanie zawartości w wiadomościach e-mail, dokumentach i innej zawartości w Microsoft 365. Kolekcje zapewniają kierownikom szacowaną zawartość, która może być istotny dla danej sprawy. Dzięki temu menedżerowie mogą szybko i przejmować decyzje dotyczące rozmiaru i zakresu zawartości związanej ze sprawą. Menedżerowie zbierania elektronicznych materiałów dowodowych mogą utworzyć kolekcję w celu przeszukiwania źródeł danych, takich jak skrzynki pocztowe i witryny usługi SharePoint, oraz przy użyciu określonych kryteriów wyszukiwania (takich jak słowa kluczowe i zakresy dat) w celu szybkiego zdefiniowania zakresu ich zbioru.

Po zdefiniowanym zbiorze menedżerowie zbierania elektronicznych materiałów dowodowych mogą zapisać kolekcję jako wersje robocze i uzyskać oszacowania, w tym oszacowania wielkości danych, lokalizacje zawartości zawierające wyniki i liczbę trafień dotyczących warunku zapytania wyszukiwania. Te szczegółowe informacje mogą pomóc w zawężaniu lub rozszerzaniu zakresu kolekcji przed przejściem do przeglądania i analizowania etapów przepływu pracy zbierania elektronicznych materiałów dowodowych.

Gdy kierownik jest zadowalacy zakresem kolekcji i szacowaną ilością zawartości, która może odpowiadać, może dodać lub zatwierdzić zawartość do zestawu  recenzji. Po zatwierdzeniu kolekcji do zestawu recenzji menedżer ma również opcje dołączania konwersacji na czacie, załączników w chmurze i wersji dokumentów. Zawartość w zbiorze również przechodzi przez inny poziom przetwarzania podczas pobierania do zestawu recenzji. a kolekcja zostanie zaktualizowana o końcowe podsumowanie kolekcji. Po dodaniu zawartości do zestawu recenzji menedżerowie zbierania elektronicznych materiałów dowodowych mogą nadal sprawdzać, grupować i uściślić zawartość, aby ułatwić jej minimization i przegląd. Ponadto kolekcja jest aktualizowana o informacje i statystyki dotyczące zawartości zatwierdzonej w zestawie recenzji. W ten sposób można odwoływać się do danych historycznych dotyczących zawartości kolekcji.

Wraz z wydaniem kolekcji w Advanced eDiscovery, nazwę karty Wyszukiwania  zmieniono na Kolekcje w Advanced eDiscovery przypadku  w Centrum zgodności platformy Microsoft 365. Kroki definiowania zakresu i rozmiaru kolekcji są zgodne z tym samym procesem co wyszukiwanie w celu zdefiniowania lokalizacji i warunków. Funkcja Zapisz jako wersję roboczą i uzyskaj oszacowania podglądu umożliwia szybką weryfikację kierowanego zakresu kolekcji przed zatwierdzeniem pełnego wyszukiwania i kolekcji do zestawu recenzji. Pozwala to ulepszyć zarządzanie zadaniami i kierowane iteracje w celu rozpoczęcia minimalizowania zawartości podczas procesu wyszukiwania i zbierania.

## <a name="collections-workflow"></a>Przepływ pracy Kolekcje

Aby rozpocząć korzystanie ze Advanced eDiscovery w aplikacji Advanced eDiscovery, oto podstawowy przepływ pracy i opisy poszczególnych kroków procesu.

![Przepływ pracy Kolekcje w Advanced eDiscovery.](../media/CollectionsWorkflow.png)

1. **Tworzenie i uruchamianie kolekcji roboczej**. Pierwszym krokiem jest utworzenie wersji roboczej kolekcji i zdefiniowanie tymczasowych i niebędące śmieciami źródeł danych do wyszukania. Możesz również przeszukiwać inne źródła danych, które nie zostały dodane do sprawy. Po dodaniu źródeł danych skonfigurujesz zapytanie wyszukiwania w celu wyszukiwania źródeł danych w poszukiwaniu zawartości związanej ze sprawą. Słowa kluczowe, właściwości i warunki możesz tworzyć zapytania wyszukiwania, które zwracają najbardziej odpowiednią zawartość w danym przypadku. Aby uzyskać więcej informacji, [zobacz Tworzenie kolekcji roboczej](create-draft-collection.md).

2. **Przeglądanie oszacowań i statystyk**. Kolejnym krokiem po utworzeniu i uruchomieniu kolekcji roboczej jest wyświetlenie statystyk kolekcji, które pomogą zweryfikować, czy znaleziona zawartość jest istotny, oraz lokalizacje zawartości z najbardziej trafieniami. Możesz także wyświetlić podgląd przykładowych wyników wyszukiwania, aby dodatkowo ustalić, czy zawartość należy do zakresu badania. Aby uzyskać więcej informacji, zobacz [Statystyki i raporty dotyczące kolekcji wersji roboczych](collection-statistics-reports.md#statistics-and-reports-for-draft-collections).

3. **Poprawianie i ponowne uruchomić kolekcję roboczą**. Na podstawie oszacowań i statystyk zwróconych przez kolekcję można edytować wersje robocze kolekcji, zmieniając przeszukane źródła danych i zapytanie wyszukiwania, aby rozszerzyć lub zawęzić kolekcję. Możesz aktualizować i ponownie uruchomić kolekcję wersji roboczej, dopóki nie masz pewności, że kolekcja zawiera najbardziej odpowiednią zawartość w danej sprawie.

4. **Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji**. Jeśli kolekcja zwróci zawartość typu odpowiednią dla danej sprawy, możesz zatwierdzić kolekcję w zestawie recenzji. Po zatwierdzeniu kolekcji możesz dodać do zestawu recenzji wątki konwersacji, załączniki w chmurze i wersje dokumentów, z których wszystkie mogą być związane ze sprawą.

   Po zatwierdzeniu kolekcji elementy podrzędne, takie jak podpisy e-mail i obrazy, są wyodrębnione z elementu nadrzędnego (takiego jak wiadomość e-mail, wiadomość czatu lub dokument), a następnie przetwarzane przez optyczne rozpoznawanie znaków (OCR, Optical Character Recognition) w celu wyodrębnienia dowolnego tekstu z elementu podrzędnego. Tekst wyodrębniony z elementów nadrzędnych jest następnie dodawany do jego elementu nadrzędnego, aby można go było wyświetlić w zestawie recenzji. Dzięki temu, że elementy podrzędne nie są dodawane do zestawu recenzji jako osobny plik, Advanced eDiscovery ograniczy liczbę potencjalnie nieistotnych elementów dodanych do zestawu recenzji. Aby uzyskać więcej informacji na temat sposobu obsługi elementów podrzędnych, zobacz [Statystyki i raporty dotyczące kolekcji](collection-statistics-reports.md#collection-contents).

   Aby uzyskać więcej informacji, [zobacz Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji](commit-draft-collection.md).

5. **Przeglądanie podsumowania kolekcji i statystyk**. Po zatwierdzeniu kolekcji do zestawu recenzji zostaną zachowane informacje o kolekcji, takie jak statystyki dotyczące wyodrębnianych elementów, indeksowanie szczegółowe, zapytanie wyszukiwania użyte dla kolekcji oraz lokalizacje zawartości, z których zostały zebrane elementy. Ponadto nie można edytować ani ponownie uruchomić kolekcji zatwierdzonej. Można je tylko kopiować lub usuwać. Zachowywanie kolekcji zawiera historyczny rekord zebranych elementów dodanych do zestawu recenzji. Aby uzyskać więcej informacji, zobacz [Statystyka i raporty dotyczące zatwierdzonej kolekcji](collection-statistics-reports.md#statistics-and-reports-for-committed-collections).
