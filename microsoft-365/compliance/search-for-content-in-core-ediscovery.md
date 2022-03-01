---
title: Wyszukiwanie zawartości w podstawowej sprawie zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Wyszukaj zawartość, która może dotyczyć podstawowej sprawy zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: 57ea95458df568de3687e1b0d38a70991b09a850
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020729"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>Wyszukiwanie zawartości w podstawowej sprawie zbierania elektronicznych materiałów dowodowych

Po utworzeniu podstawowej sprawy zbierania elektronicznych materiałów dowodowych i umieszczeniu odpowiednich osób w akacie można utworzyć i uruchomić jedno lub więcej wyszukiwań zawartości istotnych dla danej sprawy. Wyszukiwania skojarzone z podstawową sprawą zbierania elektronicznych materiałów dowodowych nie są wymienione na stronie **Przeszukiwanie** zawartości w Centrum zgodności platformy Microsoft 365. Te wyszukiwania są wymienione **na stronie Wyszukiwania** w przypadku podstawowej sprawy zbierania elektronicznych materiałów dowodowych, z które są skojarzone wyszukiwania. Oznacza to również, że dostęp do przeszukiwań związanych ze sprawą mogą uzyskiwać tylko członkowie sprawy.

Aby utworzyć podstawowe wyszukiwanie zbierania elektronicznych materiałów dowodowych:
  
1. Przejdź do <https://compliance.microsoft.com> i zaloguj się przy użyciu poświadczeń konta użytkownika, do których zostały przypisane odpowiednie uprawnienia zbierania elektronicznych materiałów dowodowych i który jest członkiem sprawy.

2. W lewym okienku nawigacji okienka Centrum zgodności platformy Microsoft 365 kliknij pozycję Pokaż **wszystko**, a następnie kliknij pozycję Zbierania elektronicznych materiałów dowodowych **> Core**.

3. Na stronie **Podstawowe sprawy zbierania** elektronicznych materiałów dowodowych wybierz sprawę, dla której chcesz utworzyć skojarzone wyszukiwanie, a następnie kliknij pozycję **Otwórz sprawę**.

4. Na stronie **głównej** dla sprawy **kliknij kartę** Wyszukiwania, a następnie kliknij pozycję **Nowe wyszukiwanie**.

   ![Kliknij pozycję Nowe wyszukiwanie, aby utworzyć podstawowe wyszukiwanie zbierania elektronicznych materiałów dowodowych.](../media/CoreeDiscoverySearch1.png)

5. W **kreatorze Nowe** wyszukiwanie wpisz nazwę wyszukiwania oraz opcjonalny opis, który ułatwia zidentyfikowanie wyszukiwania. Nazwa wyszukiwania musi być unikatowa w Twojej organizacji.

6. Na **stronie Lokalizacje** wybierz lokalizacje zawartości, które chcesz przeszukać. Możesz przeszukiwać skrzynki pocztowe, witryny i foldery publiczne.

    ![Wybierz lokalizacje zawartości, które mają być zawieszone.](../media/ContentSearchLocations.png)
  
   1. **Exchange skrzynki pocztowe**: Ustaw przełącznik w pozycję Wł., a następnie kliknij pozycję Wybierz użytkowników, grupy lub zespoły **,** aby określić skrzynki pocztowe do przechowywania. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne (aby umieścić je w miejscu przechowywania w skrzynkach pocztowych członków grupy), aby umieścić je w a hold. Możesz również przeszukać skrzynkę pocztową skojarzoną z zespołem Microsoft (w przypadku wiadomości na kanale), Office 365 grupy i Yammer grupy. Aby uzyskać więcej informacji na temat danych aplikacji przechowywanych w skrzynkach pocztowych, zobacz Zawartość przechowywana w skrzynkach pocztowych na [temat zbierania elektronicznych materiałów dowodowych](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint witryn**: Ustaw przełącznik w pozycję Wł.,  a następnie kliknij pozycję  Wybierz witryny, aby określić witryny SharePoint i konta OneDrive, które mają być zawieszone. Wpisz adres URL każdej witryny, którą chcesz umieścić w miejscu przechowywania. Możesz również dodać adres URL witryny SharePoint zespołu Microsoft, grupy Office 365 lub grupy Yammer grupy.
  
   3. **Exchange folderów publicznych**: Ustaw przełącznik na wartość Wł., aby umieścić wszystkie foldery publiczne w Exchange Online wstrzymywanie. Nie można wybrać konkretnych folderów publicznych, które mają zostać zawieszone. Jeśli nie chcesz przechowywać folderów publicznych, pozostaw przełącznik wyłączony.
  
   4. Zachowaj to pole wyboru zaznaczone, aby Teams zawartości dla użytkowników lokalnych. Jeśli na przykład przeszukasz wszystkie skrzynki pocztowe usługi Exchange w organizacji i to pole wyboru jest zaznaczone, zakres wyszukiwania będzie uwzględniany w opartym na chmurze magazynie używanym do przechowywania danych czatu Teams użytkowników lokalnych. Aby uzyskać więcej informacji, [zobacz Wyszukiwanie Teams danych czatu dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

7. Na stronie **Definiowanie warunków wyszukiwania** wpisz słowo kluczowe i w razie potrzeby dodaj warunki do zapytania wyszukiwania.

   ![Skonfiguruj zapytanie wyszukiwania.](../media/ContentSearchQuery.png)

   1. Określ słowa kluczowe, właściwości wiadomości, takie jak daty wysłania i odebrania, lub właściwości dokumentu, takie jak nazwy plików lub data ostatniej zmiany dokumentu. Można używać bardziej złożonych zapytań, które korzystają z operatorów logicznych, takich jak **ORAZ**, **LUB**, **NIE** i **NEAR**. Jeśli pozostawisz pole słowa kluczowego puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości zostanie uwzględniona w wynikach wyszukiwania. Aby uzyskać więcej informacji, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

   2. Ewentualnie możesz kliknąć pole wyboru **Pokaż** listę słów kluczowych i wpisać słowo kluczowe w każdym wierszu. W takim przypadku słowa kluczowe w każdym wierszu są połączone operatorem logicznym (**c:s**) podobnym do działania operatora **LUB** w utworzonym zapytaniu wyszukiwania.

      Dlaczego warto używać listy słów kluczowych? Możesz uzyskać statystykę, która pokazuje, ile elementów pasuje do poszczególnych słów kluczowych. Dzięki temu można szybko ustalić, które słowa kluczowe są najbardziej (i najmniej) skuteczne. Możesz również użyć frazy słowa kluczowego (otoczonej nawiasami) w wierszu. Aby uzyskać więcej informacji o liście słów kluczowych i statystykach wyszukiwania, zobacz [Uzyskiwanie statystyk dotyczących słów kluczowych dotyczących wyszukiwania](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Aby ograniczyć problemy powodowane przez duże listy słów kluczowych, możesz ograniczyć do maksymalnie 20 wierszy na liście słów kluczowych.

   3. Możesz dodać warunki wyszukiwania, aby zawęzić wyszukiwanie i zwrócić bardziej dopracowany zestaw wyników. Każdy warunek powoduje dodanie klauzuli do zapytania wyszukiwania, które jest tworzone i uruchamiane po rozpoczęciu wyszukiwania. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operator logiczny (**c:c**), który jest podobny do funkcji operatora **AND** . Oznacza to, że elementy muszą spełniać zarówno zapytanie słów kluczowych, jak i jeden lub więcej warunków, aby zostały uwzględnione w wynikach. W ten sposób warunki ułatwiają zawężenie wyników. Aby uzyskać listę i opis warunków, których można użyć w zapytaniu wyszukiwania, zobacz [Wyszukiwanie warunków](keyword-queries-and-search-conditions.md#search-conditions).

8. Przejrzyj ustawienia wyszukiwania (i w razie potrzeby edytuj), a następnie prześlij wyszukiwanie, aby je rozpocząć.

Po zakończeniu wyszukiwania możesz wyświetlić podgląd wyników wyszukiwania. W razie potrzeby kliknij **pozycję Odśwież** na **stronie Wyszukiwania** , aby wyświetlić utworzone wyszukiwanie.

## <a name="more-information-about-searching-content-locations"></a>Więcej informacji na temat wyszukiwania lokalizacji zawartości

- Gdy klikniesz **pozycję Wybierz użytkowników,** grupy lub zespoły w celu określenia skrzynek pocztowych do przeszukania, wyświetlony s wyboru skrzynki pocztowej jest pusty. Jest to zaprojektowany w celu zwiększenia wydajności. Aby dodać adresatów do tej listy, kliknij pozycję Wybierz użytkowników **,** grupy lub zespoły, wpisz nazwę (co najmniej trzy znaki) w polu wyszukiwania, zaznacz pole wyboru obok nazwy, a następnie kliknij pozycję **Wybierz.**

- Do listy skrzynek pocztowych do wyszukiwania można dodawać nieaktywne skrzynki pocztowe, grupy Microsoft Teams Yammer, grupy Office 365, grupy dystrybucyjne i grupy dystrybucyjne. Dynamiczne grupy dystrybucyjne nie są obsługiwane. Jeśli dodasz Microsoft Teams, Yammer grupy lub grupy Office 365, skrzynka pocztowa grupy lub zespołu zostanie przeszukana; skrzynki pocztowe członków grupy nie będą przeszukiwane.

- Aby dodać witryny do wyszukiwania, włącz przełącznik, a następnie kliknij pozycję **Wybierz witryny**. Wpisz adres URL każdej witryny, którą chcesz przeszukać. Możesz również dodać adres URL witryny SharePoint zespołu Microsoft, grupy Yammer lub grupy Office 365 grupy.
