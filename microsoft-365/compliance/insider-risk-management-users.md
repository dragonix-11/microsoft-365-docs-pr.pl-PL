---
title: Pulpit nawigacyjny użytkownicy zarządzania ryzykiem wewnętrznym
description: Dowiedz się więcej o pulpicie nawigacyjnym użytkowników zarządzania ryzykiem wewnętrznym w usłudze Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: 05adeb86c5e4da5119a5aae184721ec667564b49
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629492"
---
# <a name="insider-risk-management-users-dashboard"></a>Pulpit nawigacyjny użytkownicy zarządzania ryzykiem wewnętrznym

**Pulpit nawigacyjny Użytkownicy** jest ważnym narzędziem w przepływie pracy zarządzania ryzykiem wewnętrznym i pomaga badaczom i analitykom lepiej zrozumieć działania związane z ryzykiem. Ten pulpit nawigacyjny oferuje widoki i funkcje zarządzania spełniające potrzeby administracyjne między tworzeniem zasad zarządzania ryzykiem wewnętrznym a zarządzaniem przypadkami zarządzania ryzykiem wewnętrznym.

Po dodaniu użytkowników do zasad zarządzania ryzykiem wewnętrznym procesy w tle automatycznie oceniają działania użytkowników pod kątem [wyzwalania wskaźników](insider-risk-management-settings.md#indicators). Po wyświetleniu wskaźników wyzwalania do działań użytkownika są przypisywane wyniki ryzyka. Niektóre z tych działań mogą powodować alert o ryzyku wewnętrznym, ale niektóre działania mogą nie spełniać minimalnego poziomu oceny ryzyka i alert o ryzyku wewnętrznym nie zostanie utworzony. **Pulpit nawigacyjny Użytkownicy** umożliwia wyświetlanie użytkowników z tego typu wskaźnikami i ocenami ryzyka, a także użytkowników, którzy mają aktywne alerty o ryzyku wewnętrznym.

Dowiedz się więcej na temat sposobu wyświetlania użytkowników na pulpicie nawigacyjnym Użytkownicy w następujących scenariuszach:

- Użytkownicy z aktywnymi alertami zasad ryzyka dotyczącego informacji poufnych
- Użytkownicy z wyzwalaczami zdarzeń
- Użytkownicy dodali tymczasowo do zasad

## <a name="users-with-active-insider-risk-policy-alerts"></a>Użytkownicy z aktywnymi alertami zasad ryzyka dotyczącego informacji poufnych

Pulpit **nawigacyjny Użytkownicy** automatycznie wyświetla wszystkich użytkowników z aktywnymi alertami zasad ryzyka wewnętrznego. Ci użytkownicy z alertami mają zarówno wskaźnik wyzwalania, jak i wynik ryzyka działania, który spełnia wymagania dotyczące tworzenia alertu o ryzyku wewnętrznym. Działania dla tych użytkowników są wyświetlane przez wybranie użytkownika na **pulpicie nawigacyjnym Użytkownicy** i przejście do karty **Aktywność użytkownika** .

## <a name="users-with-triggering-events"></a>Użytkownicy z wyzwalaczami zdarzeń

Pulpit **nawigacyjny Użytkownicy** automatycznie wyświetla wszystkich użytkowników z wyzwalaczami zdarzeń, ale nie ma wyniku ryzyka działania, który spowodowałby utworzenie alertu o ryzyku wewnętrznym. Na przykład zostanie wyświetlony użytkownik z zgłoszoną datą rezygnacji, ponieważ to działanie jest zdarzeniem wyzwalającym, ale nie jest działaniem, które ma ocenę ryzyka. Działania dla tych użytkowników są wyświetlane przez wybranie użytkownika na **pulpicie nawigacyjnym Użytkownicy** i przejście do karty **Aktywność użytkownika** .

## <a name="users-added-temporarily-to-policies"></a>Użytkownicy dodali tymczasowo do zasad

**Pulpit nawigacyjny Użytkownicy** zawiera użytkowników dodanych do zasad zarządzania ryzykiem wewnętrznym po nietypowym zdarzeniu poza przepływem pracy zarządzania ryzykiem wewnętrznym. Tymczasowe dodawanie użytkowników (z poziomu pulpitu nawigacyjnego Zasad) to również sposób na rozpoczęcie oceniania aktywności użytkowników dla zasad zarządzania ryzykiem wewnętrznym w celu przetestowania zasad, nawet jeśli wymagany łącznik nie jest skonfigurowany.

Gdy użytkownik zostanie ręcznie dodany do zasad, działania użytkownika z poprzednich 90 dni zostaną ocenione i dodane do osi czasu **aktywności użytkownika** . Na przykład użytkownik nie jest obecnie przypisany do oceny ryzyka dla zasad ryzyka wewnętrznego, a użytkownik ma działania związane z wyciekiem danych zgłoszone do działu prawnego w organizacji. Dział prawny zaleca skonfigurowanie nowych wymagań dotyczących monitorowania krótkoterminowego dla użytkownika. Możesz tymczasowo przypisać użytkownika do zasad *wycieków danych* przez określony czas (okno aktywacji). Wszyscy użytkownicy dodani tymczasowo są wyświetlani na **pulpicie nawigacyjnym Użytkownicy,** ponieważ wymagania dotyczące wyzwalania zdarzeń zostaną uchylone.

> [!NOTE]
> Pojawienie się nowych użytkowników dodanych ręcznie na **pulpicie nawigacyjnym Użytkownicy** może potrwać kilka godzin. Wyświetlenie działań z poprzednich 90 dni dla tych użytkowników może potrwać do 24 godzin. Aby wyświetlić działania dla użytkowników dodanych ręcznie, wybierz użytkownika na **pulpicie nawigacyjnym Użytkownicy** i otwórz kartę **Aktywność użytkownika** w okienku szczegółów.

Użytkownik jest automatycznie usuwany z **pulpitu nawigacyjnego Użytkownicy** , a ocenianie zostaje zatrzymane, gdy czas zdefiniowany w **oknie aktywacji** wygaśnie, jeśli:

- użytkownik nie ma żadnych dodatkowych zdarzeń wyzwalania ani alertów zasad ryzyka niejawnych informacji poufnych oraz
- jeśli czas trwania ręcznie zdefiniowanego **okna aktywacji** jest dłuższy niż czas trwania **okna aktywacji** zasad globalnych.

Ustawienie **okna Aktywacja** z najdłuższym czasem trwania zawsze zastępuje ustawienie **okna Aktywacja** z krótszym czasem trwania. Na przykład **okno Aktywacja** skonfigurowano na karcie globalne **ramy czasowe zasad** w ustawieniach globalnych zarządzania ryzykiem wewnętrznym przez 15 dni, które są automatycznie stosowane do wszystkich zasad ryzyka wewnętrznego.

Tymczasowo dodajesz użytkownika do zasad ryzyka *związanego z wyciekami danych* i definiujesz 30 dni jako **okno aktywacji** dla tego użytkownika. Ustawienie **okna aktywacji** globalnej wynoszące 15 dni jest zastępowane przez zdefiniowanie ustawienia **okna aktywacji** wynoszącego 30 dni dla tymczasowo dodanej użytkownika. Tymczasowo dodany użytkownik pozostanie na **pulpicie nawigacyjnym Użytkownicy** i będzie w zakresie zasad przez 30 dni.

W przeciwnym scenariuszu, w którym ustawienie **globalnego okna aktywacji** jest dłuższe niż ustawienie **okna aktywacji** zdefiniowane dla tymczasowo dodanej użytkownika, ustawienie **okna aktywacji** globalnej zastąpi ustawienie **okna Aktywacja** dla tymczasowo dodanej użytkownika. Tymczasowo dodany użytkownik pozostanie na **pulpicie nawigacyjnym Użytkownicy** i będzie w zakresie zasad dla liczby dni zdefiniowanej w ustawieniach globalnego **okna aktywacji** .

## <a name="view-user-information-on-the-users-dashboard"></a>Wyświetlanie informacji o użytkowniku na pulpicie nawigacyjnym Użytkownicy

Każdy użytkownik wyświetlany na **pulpicie nawigacyjnym Użytkownicy** ma następujące informacje:

- **Użytkownicy**: nazwa użytkownika. To pole jest anonimizowane, jeśli włączono globalne ustawienie anonimizacji dla zarządzania ryzykiem wewnętrznym.
- **Poziom ryzyka**: bieżący obliczony poziom ryzyka użytkownika. Ten wynik jest obliczany co 24 godziny i wykorzystuje wyniki ryzyka alertu ze wszystkich aktywnych alertów skojarzonych z użytkownikiem. W przypadku użytkowników, którzy mają tylko wskaźniki wyzwalające, poziom ryzyka wynosi zero.
- **Aktywne alerty**: liczba aktywnych alertów dla wszystkich zasad.
- **Potwierdzone naruszenia**: liczba spraw rozpoznawanych jako *potwierdzone naruszenie zasad* dla użytkownika.
- **Przypadek**: bieżący aktywny przypadek użytkownika.

Aby szybko zlokalizować określonego użytkownika, użyj pozycji **Wyszukaj** w prawym górnym rogu pulpitu nawigacyjnego Użytkownika. Podczas wyszukiwania użytkowników należy użyć głównej nazwy użytkownika (UPN). Na przykład podczas wyszukiwania użytkownika o nazwie "Tiara Hidayah", który ma nazwę UPN "thidayah" w organizacji, należy wprowadzić "thidayah" lub część nazwy UPN w **wyszukiwaniu**.

![Pulpit nawigacyjny użytkowników zarządzania ryzykiem wewnętrznym.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Liczba użytkowników wyświetlanych na **pulpicie nawigacyjnym Użytkownicy** może być ograniczona w niektórych wystąpieniach, w zależności od liczby aktywnych alertów i zgodnych zasad. Użytkownicy z aktywnymi alertami są wyświetlani na **pulpicie nawigacyjnym Użytkownicy** w miarę generowania alertów i mogą wystąpić rzadkie przypadki, gdy zostanie osiągnięta maksymalna liczba wyświetlanych użytkowników. W przypadku wystąpienia tego limitu użytkownicy z aktywnymi alertami, którzy nie są wyświetlani, zostaną dodani do **pulpitu nawigacyjnego Użytkownicy** , ponieważ istniejące alerty użytkowników są klasyfikowane.

## <a name="view-user-details"></a>Wyświetlanie szczegółów użytkownika

Aby wyświetlić więcej szczegółów dotyczących działań związanych z ryzykiem dla użytkownika, otwórz okienko szczegółów użytkownika, klikając dwukrotnie użytkownika na **pulpicie nawigacyjnym Użytkownicy**. W okienku szczegółów można wyświetlić następujące informacje:

- Karta **Profil użytkownika**
  - **Nazwa i tytuł**: nazwa i tytuł pozycji użytkownika z usługi Azure Active Directory. Te pola użytkownika zostaną zanonimizowane lub puste, jeśli zostanie włączone globalne ustawienie anonimizacji dla zarządzania ryzykiem wewnętrznym.
  - **Adres e-mail użytkownika**: adres e-mail użytkownika.
  - **Alias**: alias sieci dla użytkownika.
  - **Organizacja lub dział**: organizacja lub dział użytkownika.

- Karta **Aktywność użytkownika**
  - **Historia ostatnich działań użytkowników**: wyświetla zarówno wskaźniki wyzwalania, jak i wskaźniki ryzyka wewnętrznego dla działań użytkowników do ostatnich 180 dni. Oceniane są również wszystkie działania istotne dla wskaźników ryzyka wewnętrznego, chociaż działania te mogły lub nie wygenerowały alertu o ryzyku wewnętrznym. Przykłady wskaźników wyzwalania mogą być datą rezygnacji lub ostatnią zaplanowaną datą pracy użytkownika. Wskaźniki ryzyka wewnętrznego to działania określone jako mające element ryzyka i zdefiniowane w zasadach, w których użytkownik jest uwzględniony. Działania związane z zdarzeniami i ryzykiem są wyświetlane z najnowszym elementem wymienionym jako pierwsze.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Usuwanie użytkowników z przypisywania w zakresie do zasad

Mogą wystąpić scenariusze, w których należy przestać przypisywać wyniki ryzyka do działania użytkownika w zasadach zarządzania ryzykiem wewnętrznym. Użyj pozycji **Usuń użytkowników** na stronie **pulpitu nawigacyjnego Użytkownicy** , aby zatrzymać przypisywanie wyników ryzyka dla co najmniej jednego użytkownika ze wszystkich zasad zarządzania ryzykiem wewnętrznym, dla których są obecnie w zakresie. Ta akcja nie powoduje usunięcia użytkowników z ogólnego przypisania zasad (po dodaniu użytkowników lub grup do konfiguracji zasad), ale po prostu usuwa użytkowników z aktywnego przetwarzania przez zasady po bieżącym wyzwalaniu zdarzeń. Jeśli w przyszłości użytkownicy będą mieli inne zdarzenie wyzwalające, wyniki ryzyka z zasad automatycznie zaczną być ponownie przypisywane do użytkowników. Żadne istniejące alerty lub przypadki dla tego użytkownika nie zostaną usunięte.

> [!NOTE]
> Usunięcie użytkownika z zasad może potrwać kilka minut. Po zakończeniu użytkownik nie będzie już wyświetlany na stronie Użytkownicy. Jeśli usunięty użytkownik ma aktywne alerty lub przypadki, użytkownik pozostanie na stronie Użytkownicy, a szczegóły dotyczące użytkownika będą pokazywać, że nie są już w zakresie zasad.

Aby ręcznie usunąć użytkowników ze stanu w zakresie we wszystkich zasadach zarządzania ryzykiem wewnętrznym, wykonaj następujące kroki:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Użytkownicy**.
2. Na **pulpicie nawigacyjnym Użytkownicy** wybierz użytkownika lub użytkowników, którzy mają zostać usunięci z zakresu zasad zarządzania ryzykiem wewnętrznym.
3. Wybierz pozycję **Usuń użytkowników**.
4. W okienku **Usuń użytkownika** wybierz pozycję **Usuń** lub **Anuluj** , aby odrzucić zmiany i zamknąć okno dialogowe.
5. Wybierz pozycję **Usuń** w okienku potwierdzenia, aby usunąć użytkownika.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Uruchamianie zautomatyzowanych zadań za pomocą przepływów usługi Power Automate dla użytkownika

Korzystając z zalecanych przepływów usługi Power Automate, badacze ryzyka i analitycy mogą szybko podjąć działania w celu:

- Powiadamianie użytkowników o dodaniu ich do zasad ryzyka dotyczącego informacji poufnych

Aby uruchamiać przepływy usługi Power Automate, zarządzać nimi lub tworzyć dla użytkownika zarządzania ryzykiem wewnętrznym:

1. Wybierz pozycję **Automatyzuj** na pasku narzędzi akcji użytkownika.
2. Wybierz przepływ usługi Power Automate do uruchomienia, a następnie wybierz pozycję **Uruchom przepływ**.
3. Po zakończeniu przepływu wybierz pozycję **Gotowe**.

Aby dowiedzieć się więcej na temat przepływów usługi Power Automate na potrzeby zarządzania ryzykiem wewnętrznym, zobacz [Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#power-automate-flows-preview).
