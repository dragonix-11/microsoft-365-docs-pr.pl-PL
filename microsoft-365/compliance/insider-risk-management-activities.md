---
title: Badanie działań w zakresie zarządzania ryzykiem w niejawnym programie testów
description: Dowiedz się więcej o badaniach nad działaniami zarządzania ryzykiem w ramach niejawnego programu testów w programie Microsoft 365
keywords: Microsoft 365, ryzyko niejawnego programu testów, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: a34e876e1ea6f9be9004609daf8afeec97cc4fbb
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009762"
---
# <a name="investigate-insider-risk-management-activities"></a>Badanie działań w zakresie zarządzania ryzykiem w niejawnym programie testów

Badanie ryzykownych działań użytkowników to ważny pierwszy krok do zminimalizowania ryzyka w ramach niejawnego programu testów dla organizacji. Te czynniki ryzyka mogą być działaniami, które generują alerty z zasad zarządzania ryzykiem w ramach niejawnego programu testów lub ryzyka związane z działaniami wykrytymi przez zasady, ale nie tworzą od razu alertów dotyczących zarządzania ryzykiem w ramach niejawnego programu testów dla użytkowników. Te typy działań można badać za pomocą **raportów aktywności użytkowników (wersja zapoznawcza)** lub **pulpitu nawigacyjnego alertów**.

## <a name="user-activity-reports-preview"></a>Raporty aktywności użytkowników (wersja zapoznawcza)

Raporty aktywności użytkowników umożliwiają badanie działań określonych użytkowników przez określony czas bez konieczności tymczasowego lub jawnego przypisywania ich do zasad zarządzania ryzykiem w ramach niejawnego programu testów. W większości scenariuszy zarządzania ryzykiem w niejawnym programie testów użytkownicy są jawnie zdefiniowani w zasadach i mogą mieć alerty zasad (w zależności od wyzwalania zdarzeń) i wyniki ryzyka związane z działaniami. Jednak w niektórych scenariuszach możesz chcieć zbadać działania użytkowników, którzy nie są jawnie zdefiniowani w zasadach. Te działania mogą być dla użytkowników, którzy otrzymali poradę na temat użytkownika i potencjalnie ryzykownych działań, lub użytkowników, których zwykle nie trzeba przypisywać do zasad zarządzania ryzykiem w ramach niejawnego programu testów.

Po skonfigurowaniu wskaźników na stronie zarządzania ryzykiem w niejawnym programie testów **Ustawienia** aktywność użytkowników jest wykrywana w przypadku ryzykownych działań związanych z wybranymi wskaźnikami. Nie musisz konfigurować zasad dotyczących raportów aktywności użytkowników w celu wykrywania i zgłaszania ryzykownych działań użytkowników w organizacji. Działania zawarte w raportach aktywności użytkowników nie wymagają wyzwalania zdarzeń tych działań. Ta konfiguracja oznacza, że wszystkie wykryte działania użytkownika są dostępne do sprawdzenia bez względu na to, czy ma on zdarzenie wyzwalające lub czy tworzy alert. Raporty są tworzone dla każdego użytkownika i mogą zawierać wszystkie działania w niestandardowym 90-dniowym okresie. Wiele raportów dla tego samego użytkownika nie jest obsługiwanych.

Po analizie działań użytkownika jego uczestnicy mogą odrzucać poszczególne działania jako takie, które zostały w nim przypisane, udostępnić lub wysłać pocztą e-mail link do raportu innym chętniom albo zdecydować się na tymczasowe lub jawne przypisanie użytkownika do zasad zarządzania ryzykiem w ramach niejawnego programu testów. Użytkownicy muszą zostać przypisani *do grupy ról* Grupy ról Zarządzanie ryzykiem w niejawnym programie testów, aby wyświetlić **stronę Raporty aktywności** użytkowników.  

![Omówienie raportu aktywności użytkowników zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-user-activity-report-overview.png)

Możesz rozpocząć pracę, wybierając pozycję **Zarządzaj raportami** w sekcji **Badanie** aktywności użytkowników na stronie Przegląd zarządzania ryzykiem w niejawnym **programie** testów. Aby wyświetlić działania użytkownika, najpierw wybierz pozycję **Utwórz** raport aktywności użytkowników i wypełnij następujące pola w **okienku Nowy raport aktywności** użytkowników:

- **Użytkownik**: wyszukiwanie użytkownika według nazwy lub adresu e-mail
- **Data rozpoczęcia**: użyj kontrolki kalendarza, aby wybrać datę rozpoczęcia działań użytkownika.
- **Data zakończenia**. Użyj kontrolki kalendarza, aby wybrać datę końcową działań użytkownika. Wybrana data zakończenia musi być większa niż dwa dni po wybranej dacie rozpoczęcia i nie większa niż 90 dni od wybranej daty rozpoczęcia.
Nowe raporty zwykle trzeba przygotować do przeglądu w ciągu 10 godzin. Gdy raport będzie gotowy, w kolumnie **Stan** na stronie  Raport aktywności użytkowników zobaczysz kolumnę Raport gotowy. Wybierz użytkownika, aby wyświetlić szczegółowy raport:

![Raport aktywności użytkowników zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-user-activity-report.png)

Raport **Aktywność użytkownika dla** wybranego użytkownika zawiera karty **Aktywność** użytkowników i **Eksplorator aktywności** :

- **Działania użytkowników**: Ten widok wykresu umożliwia badanie działań i wyświetlanie potencjalnych działań, które występują w sekwencjach. Ta karta ma strukturę, która umożliwia szybki przegląd sprawy, w tym za pomocą historycznej osi czasu wszystkich działań, szczegółów działań, bieżącej oceny ryzyka dla użytkownika w przypadku sprawy, sekwencji zdarzeń ryzyka i kontrolek filtrowania w celu pomocy w badaniach.
- **Eksplorator aktywności**: Karta **Eksplorator aktywności** udostępnia schłodnikom ryzyka kompleksowe narzędzie analityczne udostępniace szczegółowe informacje o działaniach. Za pomocą Eksploratora aktywności recenzentzy mogą szybko przeglądać oś czasu wykrytych ryzykownych działań oraz identyfikować i filtrować wszystkie działania ryzyka skojarzone z alertami. Aby dowiedzieć się więcej o oknie Eksplorator aktywności, zobacz *sekcję Eksplorator aktywności* w dalszej części tego artykułu.

## <a name="alert-dashboard"></a>Pulpit nawigacyjny alertów

Alerty zarządzania ryzykiem w niejawnym programie testów są generowane automatycznie na podstawie wskaźników ryzyka zdefiniowanych w zasadach zarządzania ryzykiem w niejawnym programie testów. Alerty te zapewniają analitykom zgodności i chłoną bieżący stan ryzyka, a także umożliwiają organizacji ocenianie i działanie w celu odkrycia ryzyka. Domyślnie zasady generują niektóre alerty o niskim, średnim i wysokim poziomie ważności, ale w zależności od potrzeb możesz zwiększyć lub zmniejszyć liczbę [alertów](insider-risk-management-settings.md#alert-volume) . Dodatkowo można skonfigurować próg [alertów](insider-risk-management-settings.md#indicator-level-settings-preview) dla wskaźników zasad podczas tworzenia nowych zasad za pomocą narzędzia do tworzenia zasad.

Obejrzyj klip wideo [](https://www.youtube.com/watch?v=KgmpxBLJLPI) z informacjami o doświadczeniu w zakresie zarządzania ryzykiem w ramach niejawnego programu testów, aby dowiedzieć się, jak alerty zawierają szczegóły, kontekst i zawartość powiązaną dla ryzykownych działań oraz jak sprawić, aby proces analizy był bardziej efektywny.

Pulpit nawigacyjny **alertów o ryzyku niejawnego** programu testów umożliwia wyświetlanie alertów wygenerowanych na podstawie zasad dotyczących ryzyka niejawnego programu testów i działanie w związku z nimi. Każdy widżet raportu zawiera informacje z ostatnich 30 dni.

- **Całkowita liczba alertów**, które wymagają przejrzenia: na liście wymieniono łączną liczbę alertów wymagających przeglądu i weryfikacji, w tym podział według ważności alertów.
- **Alerty** otwarte w ciągu ostatnich 30 dni: Całkowita liczba alertów utworzonych przez zasady jest odpowiadania w ciągu ostatnich 30 dni, sortowanych według poziomów ważności alertów najwyższych, średnich i niskich.
- **Średni czas rozwiązywania problemów z alertami**: podsumowanie przydatnych statystyk alertów:
  - Średni czas rozwiązywania alertów o wysokim poziomie ważności, wymienionych w godzinach, dniach lub miesiącach.
  - Średni czas rozwiązywania problemów z alertami o średniej ważności, które są wyświetlane w godzinach, dniach lub miesiącach.
  - Średni czas rozwiązywania problemów z alertami o niskim poziomie ważności, które są wyświetlane w godzinach, dniach lub miesiącach.

![Pulpit nawigacyjny alertów o zarządzaniu ryzykiem w niejawnym programie testów.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> W zarządzaniu ryzykiem w niejawnym programie testów są używane wbudowane ograniczanie alertów w celu ochrony i optymalizowania środowiska analizy ryzyka i przeglądu. To ograniczenie chroni przed problemami, które mogą powodować przeciążenie alertów zasad, takimi jak nieprawidłowo skonfigurowane łączniki danych lub zasady DLP. W wyniku tego może wystąpić opóźnienie w wyświetlaniu nowych alertów dla użytkownika.

## <a name="alert-status-and-severity"></a>Stan i ważność alertu

Alerty można po trzynascie chcieć określić w jednym z następujących stanów:

- **Potwierdzone**: alert potwierdzono i przypisano do nowej lub istniejącej sprawy.
- **Odrzucone**: alert odrzucony jako odrzucony w procesie sprawdzania.
- **Przegląd potrzeb**: Nowy alert, w którym nie zostały jeszcze wykonane akcje służące do oceniania.
- **Rozwiązano**: alert, który jest częścią zamkniętej i rozpoznanej sprawy.

Wyniki ryzyka alertu są automatycznie obliczane na podstawie kilku wskaźników aktywności ryzyka. Wskaźniki te obejmują typ działania ryzyka, liczbę i częstotliwość występowania aktywności, historię działań ryzyka użytkownika oraz dodawanie czynników ryzyka, które mogą poważnie zwiększyć poważne działanie. Wynik alertu poziomu ryzyka zwiększa programowy przydział poziomu ważności ryzyka dla każdego alertu i nie można go dostosować. Jeśli alerty pozostaną odblokowane, a działania związane z ryzykiem będą nadal narosły w alercie, poziom zagrożenia może wzrosnąć. Analitycy i schłońcy ryzyka mogą stosować alerty o ważności, aby ułatwić ich ocenianie zgodnie z zasadami i standardami organizacji.

Poziom zagrożenia zagrożenia to:

- **Wysoka ważność**: Działania i wskaźniki dla alertu stanowią istotne ryzyko. Skojarzone działania ryzyka są poważne, powtarzające się i wyważają wszystkie istotne czynniki ryzyka.
- **Średnia ważność**: Działania i wskaźniki dla alertu stanowią umiarkowane ryzyko. Skojarzone działania związane z ryzykiem są umiarkowane, częste i mają pewne korelacje z innymi czynnikami ryzyka.
- **Niska ważność**: Działania i wskaźniki dla alertu stanowią niewielkie ryzyko. Skojarzone działania związane z ryzykiem są niepełnoletnie, mniej często sięgają i nie są zmniejszane z innymi istotnymi czynnikami ryzyka.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrowanie alertów na pulpicie nawigacyjnym alertów

W zależności od liczby i typu aktywnych zasad zarządzania ryzykiem niejawnego programu testów w organizacji przeglądanie dużej kolejki alertów może być trudne. Filtry alertów ułatwiają analitykom i chętnym sortowanie alertów według kilku atrybutów. Aby filtrować alerty na **pulpicie nawigacyjnym Alerty**, wybierz **kontrolkę Filtruj** . Alerty można filtrować według jednego lub większej liczby atrybutów:

- **Stan**: Wybierz co najmniej jedną wartość stanu, aby przefiltrować listę alertów. Opcje to *Potwierdzono*, *Odrzucone*, *Wymaga recenzji* i *Rozwiązano*.
- **Ważność**: Wybierz co najmniej jeden poziom zagrożenia zagrożenia, aby przefiltrować listę alertów. Dostępne opcje to *Wysoki*, *Średni* i *Niski*.
- **Wykryty czas**: Wybierz daty rozpoczęcia i zakończenia dla czasu utworzenia alertu. Ten filtr wyszukuje alerty od godziny 00:00 czasu UTC w dniu rozpoczęcia do godziny 00:00 w dniu zakończenia. Aby filtrować alerty dla określonego dnia, wprowadź datę dnia w polu Data  rozpoczęcia i datę następnego dnia w polu **Data zakończenia**.
- **Zasady**. Wybierz jedną lub więcej zasad, aby filtrować alerty wygenerowane przez wybrane zasady.

## <a name="search-alerts-on-the-alert-dashboard"></a>Alerty wyszukiwania na pulpicie nawigacyjnym alertów

Aby wyszukać określony wyraz w nazwie alertu, zaznacz **kontrolkę Wyszukaj** i wpisz wyraz do wyszukania. W wynikach wyszukiwania są wyświetlane alerty dotyczące zasad zawierające wyraz zdefiniowany w wyszukiwaniu.

## <a name="dismiss-multiple-alerts-preview"></a>Odrzucanie wielu alertów (podgląd)

Może to ułatwić analitykom i współpracownikom zaoszczędź czas na natychmiastowe odrzucenie wielu alertów jednocześnie. Opcja **Odrzuć** alerty na pasku poleceń pozwala wybrać jeden lub więcej alertów ze  stanem przeglądu Wymaga na pulpicie nawigacyjnym i szybko odrzucić te alerty jako odpowiednie w procesie sprawdzania. Możesz wybrać maksymalnie 400 alertów do odrzuć jednocześnie.

Aby odrzucić alert o ryzyku niejawnego programu testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę Alerty**.
2. Na **pulpicie nawigacyjnym** Alerty wybierz alert (lub alerty)  z stanem przeglądu Wymaga, który chcesz odrzucić.
3. Na pasku poleceń Alerty wybierz pozycję **Odrzuć alerty**.
4. W **okienku szczegółów Odrzuć** alerty możesz przejrzeć szczegóły użytkownika i zasad skojarzone z wybranymi alertami.
5. Wybierz **pozycję Odrzuć alerty** , aby alerty rozstrzygnieć jako takie, które chcesz anulować, lub pozycję **Anuluj** , aby zamknąć okienko szczegółów bez zamykania alertów.

## <a name="triage-alerts"></a>Alerty dotyczące triage

Aby zweryfikować alert o ryzyku niejawnego programu testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę Alerty**.
2. Na **pulpicie nawigacyjnym** Alerty wybierz alert, który chcesz poszelić.
3. Na **stronie szczegółów** alertu możesz przejrzeć informacje dotyczące alertu, potwierdzić alert i utworzyć nową sprawę, potwierdzić alert i dodać go do istniejącej sprawy lub odrzucić alert. Ta strona zawiera również bieżący stan alertu i poziom ważności alertu (na liście Jako wysoki, Średni lub Niski). Poziom ważności może rosnąć lub zmniejszać się z czasem, jeśli alert nie został poszepny.

    Karty na stronie szczegółów **alertu** zawierają więcej informacji dotyczących alertu:
    - **Podsumowanie**: ta karta zawiera ogólne informacje o alercie.
        - **Co to było zdarzenie wyzwalające?**: Wyświetla najnowsze zdarzenie wyzwalające, które monituje zasady o rozpoczęcie przypisywania wyników ryzyka do działania użytkownika.
        - **Działanie, które wygenerował ten alert**: Wyświetla najwyższy czynnik ryzyka oraz dopasowanie zasad w okresie oceny aktywności, który spowodował wygenerowanie alertu.
        - **Analiza ryzyka dla działania w tym alertze**: Wyświetla liczbę wszystkich szczegółowych informacji o ryzyku dla alertu. Niektóre przykłady są takie, jak gdy alert zawiera działania sekwencji, skumulowane ryzyko aktywności ex  rozsyłania, działanie zawierające zdarzenia z odblokowanych domen, działanie zawierające zdarzenia z treścią priorytetową lub działania, które są nietypowe dla użytkownika.
        - **Szczegóły użytkownika**: wyświetla ogólne informacje o użytkowniku przypisanym do alertu. Jeśli jest włączona anonimizacja, pola nazwy użytkownika, adresu e-mail, aliasu i organizacji są anonimizowane.
        - **Szczegóły alertu**: uwzględnia czas trwania od wygenerowania alertu, zasady, które wygenerowały alert, a także wymieniono sprawę wygenerowaną z tego alertu. W przypadku nowych alertów w **polu Sprawa** jest wyświetlana nazwa Brak.
        - **Wykryta zawartość**: uwzględnia zawartość związaną z działaniami ryzyka związanych z alertem i podsumowuje zdarzenia związane z aktywnością według kluczowych obszarów. Wybranie linku aktywności spowoduje otwarcie Eksploratora aktywności i wyświetlenie szczegółowych informacji o aktywności.
    - **Eksplorator aktywności**: Ta karta powoduje otwarcie **Eksploratora aktywności**. Aby uzyskać więcej informacji, zobacz następną sekcję tego artykułu.

## <a name="retention-and-item-limits"></a>Limity przechowywania i elementów

Gdy zarządzanie ryzykiem w niejawnym programie testów informuje o wieku, ich wartość w celu zminimalizowania ryzykownej aktywności zmniejsza się w przypadku większości organizacji. Z kolei aktywne sprawy i skojarzone artefakty (alerty, szczegółowe informacje, działania) są zawsze przydatne dla organizacji i nie powinny mieć automatycznej daty wygaśnięcia. Dotyczy to wszystkich przyszłych alertów i artefaktów w aktywnym stanie dla każdego użytkownika skojarzonego z aktywną sprawą.

Aby zminimalizować liczbę starszych elementów, które zapewniają ograniczoną bieżącą wartość, w przypadku alertów dotyczących zarządzania ryzykiem w niejawnym programie testów, spraw i raportów aktywności użytkowników mają zastosowanie następujące limity i alerty dotyczące zarządzania ryzykiem w ramach niejawnego programu testów:

|**Element**|**Przechowywanie/limit**|
|:-------|:------------------|
| Alerty ze stanem przeglądu potrzeb | 120 dni od utworzenia alertu, a następnie automatycznie usunięte |
| Aktywne sprawy (i skojarzone artefakty) | Bezterminowe przechowywanie nigdy nie wygasa |
| Rozwiązane sprawy (i skojarzone artefakty) | 120 dni od rozwiązania problemu, a następnie automatycznie usunięte |
| Maksymalna liczba aktywnych spraw | 100 |
| Raporty aktywności użytkowników | 120 dni od wykrywania aktywności, a następnie automatycznie usunięte |

## <a name="activity-explorer"></a>Eksplorator aktywności

> [!NOTE]
> Eksplorator aktywności jest dostępny w obszarze zarządzania alertami dla użytkowników wyzwalających zdarzenia po tym, jak ta funkcja jest dostępna w Twojej organizacji.

Eksplorator aktywności udostępnia analitykom i schłodnikom ryzyko kompleksowe narzędzie analityczne, które udostępnia szczegółowe informacje o alertach. Za pomocą Eksploratora aktywności recenzentzy mogą szybko przeglądać oś czasu wykrytych ryzykownych działań oraz identyfikować i filtrować wszystkie działania ryzyka skojarzone z alertami. 

Aby filtrować alerty w Eksploratorze aktywności, aby uzyskać informacje o kolumnie, wybierz kontrolkę Filtr. Alerty można filtrować według jednego lub większej liczby atrybutów wymienionych w okienku szczegółów alertu. Eksplorator aktywności obsługuje również dostosowywalne kolumny, aby ułatwić analitykom i analitykom skoncentrowanie się na najważniejszych informacjach.

Za pomocą filtrów Zakres aktywności i Analiza ryzyka możesz wyświetlać i sortować działania i wnioski dotyczące następujących obszarów.

- **Filtry zakresu aktywności**: Filtruje wszystkie działania ponagniane dla użytkownika.
    - Wszystkie wynikowe działania dla tego użytkownika
    - Tylko wynikowe działania w tym alertie

- **Filtry analizy ryzyka**: Filtry aktywności mające zastosowanie do wszystkich zasad przypisywania wyników ryzyka.
    - Skumulowane działania ekscytacji
    - Uwzględnia zdarzenie z treścią priorytetową
    - Uwzględnia zdarzenie z domeną niedozwolonej
    - Sekwencja działań
    - Nietypowe działania

![Przegląd Eksploratora aktywności zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-activity-explorer.png)

Aby skorzystać z **Eksploratora aktywności**, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę Alerty**.
2. Na **pulpicie nawigacyjnym** Alerty wybierz alert, który chcesz poszelić.
3. W **okienku szczegółów Alerty** wybierz **pozycję Otwórz widok rozwinięty**.
4. Na stronie dla wybranego alertu wybierz **kartę Eksplorator** aktywności.

Podczas przeglądania działań w Eksploratorze aktywności osoby i analitycy mogą wybrać określone działanie i otworzyć okienko szczegółów aktywności. W okienku są wyświetlane szczegółowe informacje na temat aktywności, z których mogą korzystać analitycy i osoby chłonące podczas procesu sprawdzania alertu. Szczegółowe informacje mogą dostarczyć kontekst alertu i pomóc w zidentyfikowaniu pełnego zakresu działania ryzyka, które wyzwoliło alert.

Podczas wybierania zdarzeń działania na osi czasu aktywności liczba działań wyświetlana w Eksploratorze może nie być dopasowana do liczby zdarzeń aktywności wyświetlanych na osi czasu. Przykłady tego, dlaczego może wystąpić ta różnica:

- **Wykrywanie skumulowane exfiltrowania**: Wykrywanie rozsyłania skumulowanego analizuje dzienniki zdarzeń, ale stosuje model, który zawiera odduplikowanie podobnych działań w celu obliczenia skumulowanego ryzyka wykrzykowania. Ponadto może być też różnica w liczbie działań wyświetlanych w Eksploratorze aktywności, jeśli zostały wprowadzone zmiany w istniejących zasadach lub ustawieniach. Jeśli na przykład zmodyfikujesz dozwolone/zabronione domeny lub dodasz nowe wykluczenia typów plików po utworzeniu zasad i dopasowaniach działań, działania wykrywania ex przechyłki będą inne niż wyniki przed zmianami zasad lub ustawień. Skumulowane sumy aktywności wykrywania ex zmysłowego są oparte na konfiguracji zasad i ustawień w czasie obliczeń i nie zawierają działań przed zmianami zasad i ustawień
- **Wiadomości e-mail** do adresatów zewnętrznych: Działanie w przypadku wiadomości e-mail wysyłanych do adresatów zewnętrznych otrzymuje ocenę ryzyka na podstawie liczby wysłanych wiadomości e-mail, która może być dopasowana do dzienników zdarzeń aktywności.

![Szczegóły eksploratora aktywności w zakresie zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Tworzenie sprawy dla alertu

W przypadku przeglądania i oceniania alertów możesz utworzyć nową sprawę w celu dalszego zbadania działania ryzyka. Aby utworzyć sprawę dla alertu, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie** testów i wybierz **kartę Alerty**.
2. Na **pulpicie nawigacyjnym** Alerty wybierz alert, dla którego chcesz potwierdzić i utworzyć nową sprawę.
3. W **okienku Szczegółów alertów wybierz** pozycję **AkcjeKonfirmuj** >  **alerty & tworzenia sprawy**.
4. W **oknie dialogowym Potwierdzanie alertu** i tworzenie sprawy związanej z ryzykiem w niejawnym programie testów wprowadź nazwę sprawy, wybierz użytkowników, których chcesz dodać jako współautorów, i dodaj odpowiednie komentarze. Komentarze są automatycznie dodawane do sprawy jako notatka sprawy.
5. Wybierz **pozycję Utwórz sprawę** , aby utworzyć nową sprawę, lub pozycję **Anuluj** , aby zamknąć okno dialogowe bez tworzenia sprawy.

Po utworzeniu sprawy wiało i analitycy mogą zarządzać sprawą i działać w jej sprawie. Aby uzyskać więcej informacji, zobacz artykuł o przypadku [zarządzania ryzykiem w niejawnym programie](insider-risk-management-cases.md) testów.

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Uzyskiwanie pomocy dotyczącej zarządzania kolejką alertów o ryzyku niejawnego programu testów

Przeglądanie, badanie i działania w związku z alertami o ryzyku w niejawnym programie testów to ważne elementy minimalizowania czynników ryzyka w niejawnym programie testów w organizacji. Szybkie podejmowanie działań w celu zminimalizowania wpływu tych czynników może potencjalnie zaoszczędzić czas, pieniądze oraz konsekwencje prawne lub prawne dla organizacji. W tym procesie rozwiązywania problemów pierwszy krok przeglądania alertów może wydawać się trudnym zadaniem dla wielu analityków i osób wiaty. W zależności od sytuacji podczas korzystania z alertów o ryzyku w niejawnym programie testów mogą wystąpić pewne niewielkie przeszkody. Zapoznaj się z poniższymi zaleceniami i dowiedz się, jak zoptymalizować proces przeglądu alertów.

### <a name="too-many-alerts-to-review"></a>Zbyt wiele alertów do przejrzenia

Liczba alertów, które są publikowane przez Twoje zasady zarządzania ryzykiem w niejawnym programie testów, może być frustrująca. Liczba alertów można szybko rozwiązać za pomocą prostych kroków, w zależności od typów odbieranych alertów. Może być odbieranych zbyt wiele prawidłowych alertów lub zbyt wiele przestarzałych alertów o niskim poziomie ryzyka. Rozważ następujące działania:

- **Dostosowywanie zasad ryzyka w niejawnym programie** testów. Wybieranie i konfigurowanie właściwych zasad dotyczących ryzyka niejawnego programu testów jest podstawową metodą korygowania typu i liczby alertów. Rozpoczynając od odpowiedniego [szablonu zasad,](insider-risk-management-policies.md#policy-templates) możesz skoncentrować się na typach działań ryzyka i alertach. Inne czynniki, które mogą mieć wpływ na głośność alertów, to rozmiar użytkowników i grup, których zakres obejmuje, oraz zawartości i kanałów, dla których mają [określone priorytety](insider-risk-management-policies.md#prioritize-content-in-policies). Rozważ dostosowanie zasad, aby dostosować te obszary do tego, co jest najważniejsze dla Twojej organizacji.
- **Modyfikowanie ustawień ryzyka niejawnego programu** testów: Ustawienia ryzyka niejawnego programu testów zawierają różne opcje konfiguracji, które mogą mieć wpływ na ilość i typy ostrzeżeń, które otrzymasz. Należą do nich ustawienia [wskaźników zasad](insider-risk-management-settings.md#indicators), [progów wskaźników](insider-risk-management-settings.md#indicator-level-settings-preview) i [ram czasowych zasad](insider-risk-management-settings.md#policy-timeframes). Rozważ skonfigurowanie opcji [inteligentnych](insider-risk-management-settings.md#intelligent-detections) wykrywania w celu wykluczenia określonych typów plików, zdefiniowanie minimalnych progów przed raportem alertów aktywności przez zasady oraz zmianę ustawień głośności alertów na niższe.
- **Zbiorcze usuwanie alertów tam, gdzie to** możliwe: może ułatwić analitykom i współpracownikom zaoszczędzyć czas na natychmiastowe odrzucenie wielu [alertów](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) jednocześnie. Możesz wybrać maksymalnie 400 alertów do odrzuć jednocześnie.

### <a name="not-familiar-with-the-alert-triage-process"></a>Nie znasz procesu sprawdzania alertów

Badanie i działanie alertów w zarządzaniu ryzykiem w niejawnym programie testów jest proste:

1. **Na [pulpicie nawigacyjnym alertów](insider-risk-management-activities.md#alert-dashboard) są sprawdzane alerty ze stanem przeglądów potrzeb**. [W razie](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) potrzeby *filtruj według stanu* alertu, aby zlokalizować alerty tego typu.
2. **Zacznij od alertów o najwyższym poziomie ważności**. [Jeśli jest](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) to konieczne *, przefiltruj* je według alertów o ważności, aby zlokalizować te typy alertów.
3. **Wybierz alert, aby odnaleźć więcej informacji i przejrzeć szczegóły alertu**. W razie potrzeby za pomocą [Eksploratora](insider-risk-management-activities.md#activity-explorer) aktywności przejrzyj oś czasu skojarzonego z ryzykownym zachowaniem i zidentyfikuj wszystkie działania związane z ryzykiem dla alertu.
4. **Działanie w przypadku alertu**. Możesz potwierdzić i [utworzyć sprawę dla](insider-risk-management-activities.md#create-a-case-for-an-alert) alertu lub odrzucić i rozwiązać alert.

### <a name="resource-constraints-in-my-organization"></a>Ograniczenia zasobów w mojej organizacji

Użytkownicy nowoczesnego miejsca pracy często mają różne zakresy obowiązków i wymagania dotyczące czasu pracy. Istnieje kilka działań, które można podjąć, aby rozwiązać ograniczenia dotyczące zasobów:

- **Najpierw skoncentruj się na pracy analityka i pracy nad alertami o najwyższym poziomie ryzyka**. W zależności od zasad możesz przechwytywać działania i generować alerty o różnych stopniach potencjalnego wpływu na Twoje wysiłki na ograniczenie ryzyka. [Filtruj alerty](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) według ważności i priorytetów *Alerty o wysokim poziomie ważności* .
- **Przypisywanie użytkowników jako analityków i osób chętnych**. Przypisanie odpowiedniego użytkownika do odpowiednich ról jest ważną częścią procesu sprawdzania alertu o ryzyku w niejawnym programie testów. Upewnij się, że przypisano odpowiednich użytkowników do grup ról Analitycy zarządzających ryzykiem w niejawnym programie testów i grupy ról Zarządzanie ryzykiem *w niejawnym* programie testów.  
- **Skorzystaj z automatycznych funkcji ryzyka niejawnego programu testów, aby ułatwić odnajdowanie działań o najwyższym poziomie ryzyka**. Funkcje wykrywania [sekwencji zdarzeń zarządzania ryzykiem](insider-risk-management-policies.md#sequence-detection-preview) w niejawnym programie testów i wykrywania rozsyłania skumulowanego mogą ułatwić szybkie odnajdowanie zagrożeń w organizacji.[](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) Rozważ dostosowanie wyników [ryzyka](insider-risk-management-settings.md#indicators)[,](insider-risk-management-settings.md#file-type-exclusions) wykluczeń typów plików, [domen](insider-risk-management-settings.md#domains) i [ustawień minimalnego](insider-risk-management-settings.md#indicator-level-settings-preview) progu wskaźnika dla Twoich zasad.
