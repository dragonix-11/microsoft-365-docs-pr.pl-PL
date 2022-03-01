---
title: Pulpit nawigacyjny użytkowników zarządzania ryzykiem w niejawnym programie testów
description: Informacje na temat pulpitu nawigacyjnego zarządzania ryzykiem w programie Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem w niejawnym programie testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: a690f007b05709b094edd0c9d72417715875dfaf
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2021
ms.locfileid: "62996837"
---
# <a name="insider-risk-management-users-dashboard"></a>Pulpit nawigacyjny użytkowników zarządzania ryzykiem w niejawnym programie testów

Pulpit **nawigacyjny Użytkownicy to** ważne narzędzie w przepływie pracy do zarządzania ryzykiem w ramach niejawnego programu testów, które ułatwia wkłonie i analitykom pełniejszą wiedzę na temat działań ryzyka. Ten pulpit nawigacyjny zawiera widoki i funkcje zarządzania służące do zaspokojenia potrzeb administracyjnych między tworzeniem zasad zarządzania ryzykiem w niejawnym programie testów a zarządzaniem sprawami zarządzania ryzykiem w niejawnym programie testów.

Po dodaniu użytkowników do zasad zarządzania ryzykiem w ramach niejawnego programu testów procesy podstawowe automatycznie oceniają działania użytkowników [pod celu wyzwalania wskaźników](insider-risk-management-settings.md#indicators). Po wyzwoleniu wskaźników użytkownikom przypisywane są wyniki ryzyka. Niektóre z tych działań mogą powodować alerty o ryzyku niejawnego programu testów, ale niektóre działania mogą nie spełniać minimalnego poziomu wyników ryzyka i nie będzie tworzony alert o ryzyku niejawnego programu testów. Pulpit **nawigacyjny Użytkownicy** umożliwia wyświetlanie użytkowników z tymi typami wskaźników i ocen ryzyka, a także użytkowników, którzy mają aktywne alerty o ryzyku niejawnego programu testów.

Dowiedz się więcej o tym, jak pulpit nawigacyjny Użytkownicy wyświetla użytkowników w następujących scenariuszach:

- Użytkownicy z aktywnymi alertami o zasadach ryzyka niejawnego programu testów
- Użytkownicy wyzwalający zdarzenia
- Użytkownicy dodani tymczasowo do zasad

## <a name="users-with-active-insider-risk-policy-alerts"></a>Użytkownicy z aktywnymi alertami o zasadach ryzyka niejawnego programu testów

Na **pulpicie nawigacyjnym** Użytkownicy są automatycznie wyświetlane wszyscy użytkownicy z aktywnymi alertami o zasadach ryzyka niejawnego programu testów. Użytkownicy z alertami mają zarówno wskaźnik wyzwalający, jak i ocenę ryzyka aktywności, która spełnia wymagania dotyczące tworzenia alertu o ryzyku niejawnego programu testów. Działania dla tych użytkowników są przeglądane po wybraniu użytkownika na pulpicie  nawigacyjnym Użytkownicy i przejściu do karty **Aktywność** użytkownika.

## <a name="users-with-triggering-events"></a>Użytkownicy wyzwalający zdarzenia

Na **pulpicie nawigacyjnym** Użytkownicy są automatycznie wyświetlani wszyscy użytkownicy wyzwalający zdarzenia, ale którzy nie mają wyniku ryzyka związanego z aktywnością, który spowodowałby utworzenie alertu o ryzyku w niejawnym programie testów. Na przykład użytkownik, dla których zgłoszono datę ponownego przypisania, jest wyświetlany, ponieważ to działanie jest wyzwalające zdarzenie, ale nie jest działaniem, które ma ocenę ryzyka. Działania dla tych użytkowników są przeglądane po wybraniu użytkownika na pulpicie  nawigacyjnym Użytkownicy i przejściu do karty **Aktywność** użytkownika.

## <a name="users-added-temporarily-to-policies"></a>Użytkownicy dodani tymczasowo do zasad

Pulpit **nawigacyjny Użytkownicy zawiera** użytkowników dodanych do zasad zarządzania ryzykiem w niejawnym programie testów po nietypowym zdarzeniu, poza przepływem pracy zarządzaniem ryzykiem w niejawnym programie testów. Tymczasowe dodawanie użytkowników (z pulpitu nawigacyjnego Zasady) jest również sposobem na rozpoczęcie oceniania aktywności użytkowników dla zasad zarządzania ryzykiem w niejawnym programie testów na potrzeby testowania zasad, nawet jeśli wymagany łącznik nie został skonfigurowany.

Gdy użytkownik jest ręcznie dodawany do zasad, działania użytkownika z ostatnich 90 dni są zdobywane i dodawane do osi **czasu** Działania użytkowników. Na przykład użytkownik nie został aktualnie przypisany do oceny ryzyka dla zasad ryzyka niejawnego programu testów i ma działania związane z wyciekami danych zgłoszone do działu prawnego w organizacji. Dział prawny zaleca skonfigurowanie nowych wymagań w zakresie monitorowania krótkookresowego dla użytkownika. Możesz tymczasowo przypisać użytkownika do zasad wycieków danych  przez wyznaczony czas (okno aktywacji). Wszyscy dodani użytkownicy są tymczasowo wyświetlani na pulpicie nawigacyjnym Użytkownicy, ponieważ wyzwalanie wymagań dotyczących zdarzeń jest zrzeka się.

> [!NOTE]
> Może mi potrwać kilka godzin, aby nowi ręcznie dodani użytkownicy pojawili się na **pulpicie nawigacyjnym Użytkownicy**. Wyświetlanie działań dla tych użytkowników w ciągu ostatnich 90 dni może potrwać do 24 godzin. Aby wyświetlić działania dotyczące ręcznie dodanych użytkowników, wybierz użytkownika na pulpicie  nawigacyjnym Użytkownicy i otwórz  kartę Aktywność użytkowników w okienku szczegółów.

Użytkownik zostanie automatycznie usunięty z pulpitu **nawigacyjnego** Użytkownicy, a wyniki zostaną zatrzymane po wygaśnięciu czasu zdefiniowanego w **oknie aktywacji,** jeśli:

- użytkownik nie ma żadnych dodatkowych zdarzeń wyzwalających zdarzenia lub alerty zasad ryzyka niejawnego programu testów; oraz
- jeśli czas trwania okna **aktywacji** zdefiniowany ręcznie jest dłuższy niż czas trwania okna aktywacji **zasad globalnych** .

Ustawienie **okna Aktywacja** o najdłuższym czasie trwania zawsze zastępuje ustawienie  okna Aktywacja o krótszym czasie trwania. Na przykład okno Aktywacja na karcie Czas trwania  zasad globalnych w ustawieniach  globalnych zarządzania ryzykiem w ramach niejawnego programu testów ryzyka jest konfigurowane automatycznie przez 15 dni, które są automatycznie stosowane do wszystkich zasad ryzyka niejawnego programu testów.

Możesz tymczasowo dodać użytkownika do zasad ryzyka niejawnego programu testów danych i zdefiniować 30 dni jako okno **aktywacji dla tego** użytkownika. Ustawienie **globalnego okna aktywacji** na 15 dni zostanie zastąpione przez określenie dla użytkownika tymczasowo dodanego ustawienia Okno aktywacji na 30 dni. Tymczasowo dodany użytkownik pozostanie na pulpicie nawigacyjnym **Użytkownicy i** będzie mieć dostęp do zasad przez 30 dni.

W przeciwnym razie, w którym ustawienie  okna aktywacji globalnej jest dłuższe niż  ustawienie okna aktywacji zdefiniowane dla użytkownika tymczasowo dodanego, ustawienie okna aktywacji globalnej zastępuje ustawienie Okna aktywacji  dla użytkownika tymczasowo dodanego. Tymczasowo dodany użytkownik pozostanie na pulpicie nawigacyjnym  Użytkownicy i będzie miał zakres zasad określony przez liczbę dni zdefiniowaną w ustawieniach globalnego **okna aktywacji**.

## <a name="view-user-information-on-the-users-dashboard"></a>Wyświetlanie informacji o użytkowniku na pulpicie nawigacyjnym Użytkownicy

Każdy użytkownik wyświetlany na pulpicie **nawigacyjnym Użytkownicy** ma następujące informacje:

- **Użytkownicy**: nazwa użytkownika. To pole jest anonimizowane, jeśli włączono ustawienie anonimowości globalnej zarządzania ryzykiem w niejawnym programie testów.
- **Poziom ryzyka**: bieżący obliczony poziom ryzyka użytkownika. Ten wynik jest obliczany co 24 godziny i używa wyników alertów dotyczących ryzyka ze wszystkich aktywnych alertów skojarzonych z użytkownikiem. W przypadku użytkowników, którzy wyzwalają tylko wskaźniki, poziom ryzyka wynosi zero.
- **Aktywne alerty**: liczba aktywnych alertów dla wszystkich zasad.
- **Potwierdzone naruszenia**: liczba spraw rozwiązanych jako potwierdzone naruszenie *zasad* dla użytkownika.
- **Przypadek**: bieżąca aktywna sprawa dla użytkownika.

Aby szybko zlokalizować określonego użytkownika, użyj funkcji **wyszukiwania** w prawym górnym rogu pulpitu nawigacyjnego użytkownika. Podczas wyszukiwania użytkowników należy użyć głównej nazwy użytkownika (UPN). Na przykład podczas wyszukiwania użytkownika o nazwie "Tiara Hidayah", który ma nazwę UPN "thidayah" w organizacji, należy wprowadzić w wyszukiwaniu nazwę "thidayah" lub jej **część.**

![Pulpit nawigacyjny użytkowników zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Liczba użytkowników wyświetlanych na pulpicie  nawigacyjnym Użytkownicy może w niektórych przypadkach być ograniczona w zależności od liczby aktywnych alertów i zasad dopasowywania. W momencie generowania alertów użytkownicy z  aktywnymi alertami są wyświetlani na pulpicie nawigacyjnym użytkowników i w rzadkich przypadkach po osiągnięciu maksymalnej liczby wyświetlanych użytkowników. W przypadku tego limitu użytkownicy z aktywnymi alertami, które nie są wyświetlane, zostaną dodani  do pulpitu nawigacyjnego Użytkownicy, ponieważ istniejące alerty użytkownika są rozdzielone na grupy.

## <a name="view-user-details"></a>Wyświetl szczegóły użytkownika

Aby wyświetlić więcej szczegółowych informacji na temat aktywności związanej z ryzykiem dla użytkownika, otwórz okienko szczegółów użytkownika, klikając dwukrotnie użytkownika na **pulpicie nawigacyjnym Użytkownicy**. W okienku szczegółów możesz wyświetlić następujące informacje:

- **Karta Profil** użytkownika
  - **Nazwa i tytuł**: nazwa i tytuł pozycji użytkownika z Azure Active Directory. Te pola użytkowników będą anonimizowane lub puste, jeśli włączono ustawienie anonimowości globalnej zarządzania ryzykiem w niejawnym programie testów.
  - **Adres e-mail** użytkownika: adres e-mail użytkownika.
  - **Alias ( Alias** sieciowy): alias sieciowy użytkownika.
  - **Organizacja lub dział**: organizacja lub dział użytkownika.

- **Karta Aktywność** użytkowników
  - **Historia ostatnich działań użytkowników**: Wyświetla zarówno wskaźniki wyzwalania wskaźników, jak i wskaźniki ryzyka niejawnego programu testów dla działań użytkowników do ostatnich 180 dni. Wszystkie działania dotyczące wskaźników ryzyka niejawnego programu testów również są punktowane, chociaż działania te mogą, ale nie muszą, powodować wygenerowanie alertu o ryzyku niejawnego programu testów. Przykłady wskaźników wyzwalania mogą być datą ponownego przypisania lub ostatnią zaplanowaną datą pracy dla użytkownika. Wskaźniki ryzyka w niejawnym programie testów to działania określone jako elementy ryzyka definiowane w zasadach uwzględnianych przez użytkownika. Zdarzenia i działania związane z ryzykiem są wymienione z najnowszą  pozycji na liście jako pierwsza.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Usuwanie użytkowników z zakresu przypisywania do zasad

W niektórych sytuacjach konieczne może być zaprzestanie przypisywania ocen ryzyka do działań użytkowników w zasadach zarządzania ryzykiem w niejawnym programie testów. Użyj **funkcji Usuń użytkowników** na  stronie pulpitu nawigacyjnego Użytkownicy, aby zatrzymać przypisywanie ocen ryzyka dla jednego lub większej liczby użytkowników ze wszystkich zasad zarządzania ryzykiem w niejawnym programie testów, których obecnie używają. Ta akcja nie powoduje usunięcia użytkowników z ogólnego przypisywania zasad (podczas dodawania użytkowników lub grup do konfiguracji zasad), ale po prostu usuwa użytkowników z aktywnego przetwarzania przez zasady po bieżącym wyzwalaniu zdarzeń. Jeśli w przyszłości do użytkowników zostanie przypisane kolejne zdarzenie wyzwalające, wyniki dotyczące ryzyka związane z zasadami zaczną być ponownie przypisywane do użytkowników. Żadne istniejące alerty i przypadki dla tego użytkownika nie zostaną usunięte.

> [!NOTE]
> Usunięcie użytkownika z zasad może potrwać kilka minut. Po ukończeniu tej pracy użytkownik nie będzie już wymieniony na stronie Użytkownicy. Jeśli usunięty użytkownik ma aktywne alerty lub sprawy, pozostanie na stronie Użytkownicy, a szczegóły dotyczące użytkownika będą zawierały informacje, że nie ma już zakresu zasad.

Aby ręcznie usunąć użytkowników ze stanu "zakres", we wszystkich zasadach zarządzania ryzykiem w ramach niejawnego programu testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę** Użytkownicy.
2. Na **pulpicie nawigacyjnym** Użytkownicy wybierz użytkowników, których chcesz usunąć z zakresu zasad zarządzania ryzykiem w niejawnym programie testów.
3. Wybierz **pozycję Usuń użytkowników**.
4. W **okienku Usuń użytkownika** **wybierz pozycję Usuń** **lub Anuluj** , aby odrzucić zmiany i zamknąć okno dialogowe.
5. Wybierz **pozycję Usuń** w okienku potwierdzenia, aby usunąć użytkownika.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Uruchamianie zadań automatycznych z przepływami Power Automate użytkownika

Używając zalecanych Power Automate analizy ryzyka i analitycy mogą szybko podjąć działania w celu:

- Powiadamianie użytkowników o dodaniu ich do zasad ryzyka niejawnego programu testów

Aby uruchomić przepływy dla użytkownika do zarządzania ryzykiem w niejawnym programie testów, zarządzać nimi Power Automate tworzyć przepływy:

1. Wybierz **pozycję Automatyzuj** na pasku narzędzi akcji użytkownika.
2. Wybierz przepływ Power Automate przepływu pracy, a następnie wybierz pozycję **Uruchom przepływ**.
3. Po zakończeniu przepływu wybierz pozycję **Gotowe**.

Aby dowiedzieć się więcej o przepływach Power Automate do zarządzania ryzykiem w niejawnym programie testów, zobacz Wprowadzenie do ustawień zarządzania ryzykiem w niejawnym programie [testów](insider-risk-management-settings.md#power-automate-flows-preview).
