---
title: Tworzenie i uruchamianie wyszukiwania zawartości w portal zgodności Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Użyj narzędzia Content search eDiscovery w centrum zgodności, aby wyszukać zawartość w różnych usługach Platformy Microsoft 365.
ms.openlocfilehash: 3c5e4191c34db9d31ce54494f2677e75f3cae3bf
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632624"
---
# <a name="create-a-content-search"></a>Tworzenie wyszukiwania zawartości

Za pomocą narzędzia Do zbierania elektronicznych materiałów dowodowych wyszukiwania zawartości w portal zgodności Microsoft Purview można wyszukiwać zawartość w miejscu, taką jak wiadomości e-mail, dokumenty i konwersacje dotyczące wiadomości błyskawicznych w organizacji. Użyj tego narzędzia, aby wyszukać zawartość w tych chmurowych źródłach danych platformy Microsoft 365:
  
- skrzynki pocztowe Exchange Online

- Witryny usługi SharePoint Online i konta OneDrive dla Firm

- Microsoft Teams

- Grupy Microsoft 365

- Grupy usługi Yammer

Po uruchomieniu wyszukiwania na stronie wysuwanej wyszukiwania zostanie wyświetlona liczba lokalizacji zawartości i szacowana liczba wyników wyszukiwania. Możesz szybko wyświetlić statystyki, takie jak lokalizacje zawartości, które mają najwięcej elementów zgodnych z zapytaniem wyszukiwania. Po uruchomieniu wyszukiwania można wyświetlić podgląd wyników lub wyeksportować je na komputer lokalny.

## <a name="before-you-run-a-search"></a>Przed uruchomieniem wyszukiwania

- Aby uzyskać dostęp do narzędzia do wyszukiwania zawartości w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a> (aby uruchamiać wyszukiwania i wyświetlać podgląd wyników i eksportować wyniki), administrator, oficer zgodności lub menedżer zbierania elektronicznych materiałów dowodowych musi być członkiem grupy ról Menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- We wdrożeniu hybrydowym programu Exchange nie można używać narzędzia do wyszukiwania zawartości do wyszukiwania wiadomości e-mail w lokalnych skrzynkach pocztowych. Za pomocą tego narzędzia można wyszukiwać tylko skrzynki pocztowe oparte na chmurze.

- We wdrożeniu hybrydowym programu Exchange możesz wyszukiwać dane czatu usługi Teams w lokalnych skrzynkach pocztowych. Aby uzyskać więcej informacji, zobacz [Dane czatu w usłudze Teams dla użytkowników lokalnych](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users).

## <a name="create-and-run-a-search"></a>Tworzenie i uruchamianie wyszukiwania
  
1. Przejdź do strony <https://compliance.microsoft.com> i zaloguj się przy użyciu poświadczeń konta, do których przypisano odpowiednie uprawnienia.

2. W okienku nawigacji po lewej stronie portalu zgodności kliknij pozycję **Wyszukiwanie zawartości**.

3. Na stronie **Wyszukiwanie zawartości** kliknij pozycję **Nowe wyszukiwanie**.

4. Wpisz nazwę wyszukiwania, opcjonalny opis, który pomaga zidentyfikować wyszukiwanie. Nazwa wyszukiwania musi być unikatowa w organizacji.

5. Na stronie **Lokalizacje** wybierz lokalizacje zawartości, które chcesz wyszukać. Możesz przeszukiwać skrzynki pocztowe, witryny i foldery publiczne.

    ![Wybierz lokalizacje zawartości, które mają zostać wstrzymane.](../media/ContentSearchLocations.png)
  
   1. **Skrzynki pocztowe programu Exchange**: ustaw przełącznik **na Włączone** , a następnie kliknij pozycję **Wybierz użytkowników, grupy lub zespoły,** aby określić skrzynki pocztowe, które mają zostać wstrzymane. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne. Możesz również wyszukać skrzynkę pocztową skojarzoną z zespołem firmy Microsoft (w poszukiwaniu wiadomości kanału), grupę Office 365 i grupę usługi Yammer. Aby uzyskać więcej informacji na temat danych aplikacji przechowywanych w skrzynkach pocztowych, zobacz [Zawartość przechowywana w skrzynkach pocztowych na potrzeby zbierania elektronicznych materiałów dowodowych](what-is-stored-in-exo-mailbox.md).

   2. **Witryny programu SharePoint**: ustaw przełącznik **na Wł.,** a następnie kliknij pozycję **Wybierz witryny** , aby określić witryny programu SharePoint i konta usługi OneDrive, które mają zostać wstrzymane. Wpisz adres URL każdej witryny, która ma zostać wstrzymana. Możesz również dodać adres URL witryny programu SharePoint dla zespołu firmy Microsoft, grupy Office 365 lub grupy usługi Yammer.
  
   3. **Foldery publiczne programu Exchange**: ustaw przełącznik **na Włączone**, aby wstrzymać wszystkie foldery publiczne w organizacji Exchange Online. Nie można wybrać określonych folderów publicznych do wstrzymania. Pozostaw przełącznik wyłączony, jeśli nie chcesz wstrzymać folderów publicznych.
  
   4. Zaznacz to pole wyboru, aby wyszukać zawartość usługi Teams dla użytkowników lokalnych. Jeśli na przykład przeszukasz wszystkie skrzynki pocztowe programu Exchange w organizacji i to pole wyboru zostanie zaznaczone, magazyn w chmurze używany do przechowywania danych czatu usługi Teams dla użytkowników lokalnych zostanie uwzględniony w zakresie wyszukiwania. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie danych czatu w usłudze Teams dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

6. Na stronie **Definiowanie warunków wyszukiwania** wpisz zapytanie słowa kluczowego i w razie potrzeby dodaj warunki do zapytania wyszukiwania.

   ![Skonfiguruj zapytanie wyszukiwania.](../media/ContentSearchQuery.png)

   1. Określ słowa kluczowe, właściwości komunikatu, takie jak daty wysłania i odebrania, lub właściwości dokumentu, takie jak nazwy plików lub data ostatniej zmiany dokumentu. Możesz użyć bardziej złożonych zapytań, które używają operatora logicznego, takiego jak **AND**, **OR**, **NOT** i **NEAR**. Jeśli pole słowa kluczowego pozostanie puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości zostanie uwzględniona w wynikach wyszukiwania. Aby uzyskać więcej informacji, zobacz [Zapytania dotyczące słów kluczowych i warunki wyszukiwania dla zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

   2. Alternatywnie możesz kliknąć pole wyboru **Pokaż listę słów kluczowych** i wpisać słowo kluczowe w każdym wierszu. Jeśli to zrobisz, słowa kluczowe w każdym wierszu są połączone przez operator logiczny (**c:s**), który jest podobny do operatora **OR** w utworzonym zapytaniu wyszukiwania.

      Dlaczego warto używać listy słów kluczowych? Możesz uzyskać statystyki pokazujące, ile elementów pasuje do każdego słowa kluczowego. Może to pomóc w szybkim określeniu, które słowa kluczowe są najbardziej (i najmniej) skuteczne. Możesz również użyć frazy kluczowej (otoczonej nawiasami) w wierszu. Aby uzyskać więcej informacji na temat listy słów kluczowych i statystyk wyszukiwania, zobacz [Pobieranie statystyk słów kluczowych dla wyszukiwań](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Aby zmniejszyć problemy spowodowane przez duże listy słów kluczowych, możesz ograniczyć do maksymalnie 20 wierszy na liście słów kluczowych.

   3. Możesz dodać warunki wyszukiwania, aby zawęzić wyszukiwanie i zwrócić bardziej wyrafinowany zestaw wyników. Każdy warunek dodaje klauzulę do zapytania wyszukiwania, które jest tworzone i uruchamiane po rozpoczęciu wyszukiwania. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operator logiczny (**c:c**), który jest podobny pod względem funkcjonalności do operatora **AND** . Oznacza to, że elementy muszą spełniać zarówno zapytanie słowa kluczowego, jak i co najmniej jeden warunk, który ma zostać uwzględniony w wynikach. W ten sposób warunki pomagają zawęzić wyniki. Aby uzyskać listę i opis warunków, których można użyć w zapytaniu wyszukiwania, zobacz [Warunki wyszukiwania](keyword-queries-and-search-conditions.md#search-conditions).

7. Przejrzyj ustawienia wyszukiwania (i edytuj je w razie potrzeby), a następnie prześlij wyszukiwanie, aby je uruchomić.
  
Aby ponownie uzyskać dostęp do tego wyszukiwania zawartości lub uzyskać dostęp do innych wyszukiwań zawartości wymienionych na stronie **wyszukiwania zawartości** , wybierz wyszukiwanie, a następnie kliknij przycisk **Otwórz**.

## <a name="next-steps"></a>Następne kroki

Oto lista kolejnych kroków do wykonania po utworzeniu i uruchomieniu wyszukiwania zawartości.

- [Podgląd wyników wyszukiwania](preview-ediscovery-search-results.md)

- [Wyświetl statystyki wyników wyszukiwania](view-keyword-statistics-for-content-search.md)

- [Eksportuj wyniki wyszukiwania](export-search-results.md)

- [Eksportuj raport wyszukiwania](export-a-content-search-report.md)

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji na temat wyszukiwania zawartości, takich jak wyszukiwanie zawartości w różnych usługach Platformy Microsoft 365, zobacz [Dokumentacja funkcji wyszukiwania zawartości](content-search-reference.md).
