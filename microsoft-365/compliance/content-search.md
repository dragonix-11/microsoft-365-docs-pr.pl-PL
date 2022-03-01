---
title: Tworzenie i uruchamianie wyszukiwania zawartości w Centrum zgodności platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Użyj narzędzia zbierania elektronicznych materiałów dowodowych przeszukiwania zawartości w Centrum zgodności, aby wyszukać zawartość w różnych Microsoft 365 usługach.
ms.openlocfilehash: 68270466625cc5f9b76359ae7697536956c727aa
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020733"
---
# <a name="create-a-content-search"></a>Tworzenie wyszukiwania zawartości

Za pomocą narzędzia Przeszukiwanie zawartości zbierania elektronicznych materiałów dowodowych w aplikacji Centrum zgodności platformy Microsoft 365 wyszukać zawartość w miejscu, taką jak wiadomości e-mail, dokumenty i konwersacje za pomocą wiadomości błyskawicznych w organizacji. To narzędzie umożliwia wyszukiwanie zawartości w tych opartych na Microsoft 365 źródłach danych:
  
- Exchange Online skrzynki pocztowe

- SharePoint witryny i konta OneDrive dla Firm online

- Microsoft Teams

- Microsoft 365 grupy

- Yammer grupy

Po uruchomieniu wyszukiwania na stronie wysuwu wyszukiwania jest wyświetlana liczba lokalizacji zawartości i szacowana liczba wyników wyszukiwania. Możesz szybko wyświetlać statystyki, takie jak lokalizacje zawartości, w których znajduje się najwięcej elementów, które pasują do zapytania wyszukiwania. Po uruchomieniu wyszukiwania można wyświetlić podgląd wyników lub wyeksportować je na komputer lokalny.

## <a name="before-you-run-a-search"></a>Przed uruchomieniem wyszukiwania

- Aby można było uzyskać dostęp do narzędzia przeszukiwania zawartości w aplikacji <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> (w celu uruchamiania wyszukiwań i wyświetlania podglądu wyników oraz eksportowania wyników), administrator, inspektor zgodności lub menedżer zbierania elektronicznych materiałów dowodowych musi być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w grupie Centrum zgodności platformy Microsoft 365. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- W Exchange hybrydowego nie można używać narzędzia Przeszukiwanie zawartości do wyszukiwania lokalnych skrzynek pocztowych. Za pomocą tego narzędzia można przeszukiwać wyłącznie skrzynki pocztowe w chmurze.

## <a name="create-and-run-a-search"></a>Tworzenie i uruchamianie wyszukiwania
  
1. Przejdź do <https://compliance.microsoft.com> odpowiedniego konta i zaloguj się przy użyciu poświadczeń odpowiedniego konta.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 pozycję **Wyszukiwanie zawartości**.

3. Na **stronie Wyszukiwanie zawartości** kliknij pozycję **Nowe wyszukiwanie**.

4. Wpisz nazwę wyszukiwania oraz opcjonalny opis, który ułatwia zidentyfikowanie wyszukiwania. Nazwa wyszukiwania musi być unikatowa w Twojej organizacji.

5. Na **stronie Lokalizacje** wybierz lokalizacje zawartości, które chcesz przeszukać. Możesz przeszukiwać skrzynki pocztowe, witryny i foldery publiczne.

    ![Wybierz lokalizacje zawartości, które mają być zawieszone.](../media/ContentSearchLocations.png)
  
   1. **Exchange skrzynki pocztowe**: Ustaw przełącznik w pozycję Wł., a następnie kliknij pozycję Wybierz użytkowników, grupy lub zespoły **,** aby określić skrzynki pocztowe do przechowywania. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne. Możesz również przeszukać skrzynkę pocztową skojarzoną z zespołem Microsoft (w przypadku wiadomości na kanale), Office 365 grupy i Yammer grupy. Aby uzyskać więcej informacji na temat danych aplikacji przechowywanych w skrzynkach pocztowych, zobacz Zawartość przechowywana w skrzynkach pocztowych na [temat zbierania elektronicznych materiałów dowodowych](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint witryn**: Ustaw przełącznik w pozycję Wł.,  a następnie kliknij pozycję  Wybierz witryny, aby określić witryny SharePoint i konta OneDrive, które mają być zawieszone. Wpisz adres URL każdej witryny, którą chcesz umieścić w miejscu przechowywania. Możesz również dodać adres URL witryny SharePoint zespołu Microsoft, grupy Office 365 lub grupy Yammer grupy.
  
   3. **Exchange folderów publicznych**: Ustaw przełącznik na wartość Wł., aby umieścić wszystkie foldery publiczne w Exchange Online wstrzymywanie. Nie można wybrać konkretnych folderów publicznych, które mają zostać zawieszone. Jeśli nie chcesz przechowywać folderów publicznych, pozostaw przełącznik wyłączony.
  
   4. Zachowaj to pole wyboru zaznaczone, aby Teams zawartości dla użytkowników lokalnych. Jeśli na przykład przeszukasz wszystkie skrzynki pocztowe usługi Exchange w organizacji i to pole wyboru jest zaznaczone, zakres wyszukiwania będzie uwzględniany w opartym na chmurze magazynie używanym do przechowywania danych czatu Teams użytkowników lokalnych. Aby uzyskać więcej informacji, [zobacz Wyszukiwanie Teams danych czatu dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

6. Na stronie **Definiowanie warunków wyszukiwania** wpisz słowo kluczowe i w razie potrzeby dodaj warunki do zapytania wyszukiwania.

   ![Skonfiguruj zapytanie wyszukiwania.](../media/ContentSearchQuery.png)

   1. Określ słowa kluczowe, właściwości wiadomości, takie jak daty wysłania i odebrania, lub właściwości dokumentu, takie jak nazwy plików lub data ostatniej zmiany dokumentu. Można używać bardziej złożonych zapytań, które korzystają z operatorów logicznych, takich jak **ORAZ**, **LUB**, **NIE** i **NEAR**. Jeśli pozostawisz pole słowa kluczowego puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości zostanie uwzględniona w wynikach wyszukiwania. Aby uzyskać więcej informacji, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

   2. Ewentualnie możesz kliknąć pole wyboru **Pokaż** listę słów kluczowych i wpisać słowo kluczowe w każdym wierszu. W takim przypadku słowa kluczowe w każdym wierszu są połączone operatorem logicznym (**c:s**) podobnym do działania operatora **LUB** w utworzonym zapytaniu wyszukiwania.

      Dlaczego warto używać listy słów kluczowych? Możesz uzyskać statystykę, która pokazuje, ile elementów pasuje do poszczególnych słów kluczowych. Dzięki temu można szybko ustalić, które słowa kluczowe są najbardziej (i najmniej) skuteczne. Możesz również użyć frazy słowa kluczowego (otoczonej nawiasami) w wierszu. Aby uzyskać więcej informacji o liście słów kluczowych i statystykach wyszukiwania, zobacz [Uzyskiwanie statystyk dotyczących słów kluczowych dotyczących wyszukiwania](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Aby ograniczyć problemy powodowane przez duże listy słów kluczowych, możesz ograniczyć do maksymalnie 20 wierszy na liście słów kluczowych.

   3. Możesz dodać warunki wyszukiwania, aby zawęzić wyszukiwanie i zwrócić bardziej dopracowany zestaw wyników. Każdy warunek powoduje dodanie klauzuli do zapytania wyszukiwania, które jest tworzone i uruchamiane po rozpoczęciu wyszukiwania. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operator logiczny (**c:c**), który jest podobny do funkcji operatora **AND** . Oznacza to, że elementy muszą spełniać zarówno zapytanie słów kluczowych, jak i jeden lub więcej warunków, aby zostały uwzględnione w wynikach. W ten sposób warunki ułatwiają zawężenie wyników. Aby uzyskać listę i opis warunków, których można użyć w zapytaniu wyszukiwania, zobacz [Wyszukiwanie warunków](keyword-queries-and-search-conditions.md#search-conditions).

7. Przejrzyj ustawienia wyszukiwania (i w razie potrzeby edytuj), a następnie prześlij wyszukiwanie, aby je rozpocząć.
  
Aby ponownie uzyskać dostęp do tego wyszukiwania zawartości lub uzyskać dostęp do innych wyszukiwań  zawartości wymienionych na stronie Wyszukiwanie zawartości, zaznacz to wyszukiwanie, a następnie kliknij pozycję **Otwórz**.

## <a name="next-steps"></a>Następne kroki

Oto lista następnych czynności, które należy wykonać po utworzeniu i uruchomieniu wyszukiwania zawartości.

- [Podgląd wyników wyszukiwania](preview-ediscovery-search-results.md)

- [Wyświetlanie statystyk wyników wyszukiwania](view-keyword-statistics-for-content-search.md)

- [Eksportowanie wyników wyszukiwania](export-search-results.md)

- [Eksportowanie raportu wyszukiwania](export-a-content-search-report.md)

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji o przeszukiwaniu zawartości, takich jak wyszukiwanie zawartości w różnych usługach Microsoft 365, zobacz Informacje o funkcjach [dotyczące wyszukiwania zawartości](content-search-reference.md).
