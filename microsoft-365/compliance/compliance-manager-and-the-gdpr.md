---
title: Menedżer zgodności firmy Microsoft i RODO
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Menedżer zgodności firmy Microsoft to bezpłatne narzędzie do oceny ryzyka oparte na przepływach pracy dostępne w Portalu zaufania usług firmy Microsoft. Menedżer zgodności umożliwia śledzenie, przypisywanie i weryfikowanie działań związanych ze zgodnością z przepisami w zakresie usług firmy Microsoft w chmurze.
ms.openlocfilehash: b4a648c43fb20f557b85e24e9e67de036cc4f2e0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984011"
---
# <a name="microsoft-compliance-manager-and-the-gdpr"></a>Menedżer zgodności firmy Microsoft i RODO

Ogólne Rozporządzenie o Ochronie Danych (RODO) zawarte w Unii Europejskiej może mieć wpływ na Twoją strategię zgodności i upoważniać do określonych działań w celu zarządzania informacjami o użytkownikach i klientach używanymi w Menedżerze zgodności.

## <a name="user-privacy-settings"></a>Ustawienia prywatności użytkownika

Niektóre przepisy wymagają, aby organizacja mogła usuwać dane historii użytkowników. Menedżer zgodności udostępnia **funkcje prywatności Ustawienia**, które umożliwiają administratorom:
  
- [Wyszukiwanie użytkownika](#search-for-a-user)
- [Eksportowanie raportu historii danych konta](#export-a-report-of-account-data-history)
- [Usuwanie historii danych użytkownika](#delete-user-data-history)
  
## <a name="search-for-a-user"></a>Wyszukiwanie użytkownika

Aby wyszukać konto użytkownika:
  
1. Wprowadź alias e-mail użytkownika (informacje z lewej strony symbolu @) i wybierz nazwę domeny z listy sufiksów domen po prawej stronie. W przypadku organizacji z wieloma zarejestrowanymi domenami sprawdź dwukrotnie sufiks nazwy domeny, aby upewnić się, że jest poprawny.

2. Po prawidłowym wprowadzeniu nazwy użytkownika wybierz pozycję **Wyszukaj**.

3. W przypadku kont użytkowników, które nie zostały zwrócone, na stronie jest wyświetlany **komunikat Nie znaleziono użytkownika**. Sprawdź informacje o adresie e-mail użytkownika i w razie potrzeby wprowadzić korekty. Aby ponowić próbę, wybierz **pozycję Wyszukaj**.

4. W przypadku zwróconych kont użytkowników tekst przycisku zmieni się z **Wyszukaj na** **Wyczyść**. Oznacza to, że zwracane konto użytkownika jest kontekstem operacyjnym dla dodatkowych funkcji i że te funkcje mają zastosowanie do tego konta użytkownika.

5. Aby wyczyścić wyniki wyszukiwania i wyszukać innego użytkownika, wybierz pozycję **Wyczyść**.

## <a name="export-a-report-of-account-data-history"></a>Eksportowanie raportu historii danych konta

Dla każdego zidentyfikowanego konta użytkownika możesz wygenerować raport zależności połączonych z tym kontem. Te informacje umożliwiają ponowne przypisanie otwartych elementów akcji lub zapewnienie dostępu do przekazanych wcześniej dowodów.
  
 Aby wygenerować i wyeksportować raport:
  
1. Wybierz **pozycję Eksportuj** , aby wygenerować i pobrać raport czynności kontrolnych Menedżera zgodności aktualnie przypisanych do zwróconego konta użytkownika oraz listę dokumentów przekazanych przez tego użytkownika. Jeśli nie ma przypisanych akcji ani przekazanych dokumentów, zostanie wyświetlony komunikat o błędzie "Brak danych dla tego użytkownika".

2. Raport zostanie pobrany w tle aktywnego okna przeglądarki— jeśli nie widzisz wyskakującego okienka pobierania, które chcesz sprawdzić w historii pobierania przeglądarki.

3. Otwórz dokument, aby przejrzeć dane raportu.

> [!IMPORTANT]
> Dane raportu nie są historycznej listy, która zachowuje i wyświetla zmiany stanu w historii zadań czynności do wykonania. Wygenerowany raport jest migawką kontrolki Czynności do czynności przypisanych w momencie jego uruchamiania (sygnatura daty i czasu wpisana w raporcie). Na przykład kolejne ponowne przypisanie elementów akcji spowoduje, że dane raportu migawkowego będą inne, jeśli ten raport zostanie ponownie wygenerowany dla tego samego użytkownika.
  
## <a name="delete-user-data-history"></a>Usuwanie historii danych użytkownika

Ustawia dla wszystkich elementów akcji kontrolek przypisanych do zwracanych użytkowników ustawienie "nieprzypisane". Ustawia wartość **przekazane przez dla** wszystkich dokumentów przekazanych przez zwróconego użytkownika na "usunięto użytkownika".
  
Aby usunąć konto użytkownika Element akcji i historia przekazywania dokumentów:
  
1. Wybierz **pozycję Usuń**.

    Zostanie wyświetlone okno dialogowe potwierdzenia: "Spowoduje to usunięcie wszystkich przypisań czynności do wykonania i historii przekazywania *dokumentu dla wybranego użytkownika. Ta akcja jest trwała. Czy na pewno chcesz kontynuować?"*.

2. Aby kontynuować, wybierz **przycisk OK**, a w przeciwnym razie wybierz pozycję **Anuluj**.
