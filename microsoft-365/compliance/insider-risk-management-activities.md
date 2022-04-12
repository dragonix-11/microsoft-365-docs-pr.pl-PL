---
title: Badanie działań związanych z zarządzaniem ryzykiem wewnętrznym
description: Dowiedz się więcej o badaniu działań związanych z zarządzaniem ryzykiem wewnętrznym w Microsoft 365
keywords: Microsoft 365, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: b53b67433bea08e20b082f555c26d41edce55daa
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783342"
---
# <a name="investigate-insider-risk-management-activities"></a>Badanie działań związanych z zarządzaniem ryzykiem wewnętrznym

Badanie ryzykownych działań użytkowników jest ważnym pierwszym krokiem minimalizowania ryzyka związanego z informacjami poufnymi w organizacji. Mogą to być działania generujące alerty na podstawie zasad zarządzania ryzykiem wewnętrznym lub ryzyka związane z działaniami wykrytymi przez zasady, ale nie od razu tworzące alert dotyczący zarządzania ryzykiem wewnętrznym dla użytkowników. Tego typu działania można zbadać przy użyciu **raportów aktywności użytkowników (wersja zapoznawcza)** lub **pulpitu nawigacyjnego alertów**.

## <a name="user-activity-reports-preview"></a>Raporty aktywności użytkowników (wersja zapoznawcza)

Raporty aktywności użytkowników umożliwiają badanie działań dla określonych użytkowników w określonym okresie bez konieczności tymczasowego lub jawnego przypisywania ich do zasad zarządzania ryzykiem wewnętrznym. W większości scenariuszy zarządzania ryzykiem wewnętrznym użytkownicy są jawnie definiowani w zasadach i mogą mieć alerty zasad (w zależności od wyzwalania zdarzeń) i wyniki ryzyka skojarzone z działaniami. Jednak w niektórych scenariuszach warto zbadać działania użytkowników, które nie są jawnie zdefiniowane w zasadach. Te działania mogą dotyczyć użytkowników, którzy otrzymali poradę dotyczącą użytkownika i potencjalnie ryzykownych działań, lub użytkowników, którzy zazwyczaj nie muszą być przypisani do zasad zarządzania ryzykiem wewnętrznym.

Po skonfigurowaniu wskaźników na stronie **Ustawienia** zarządzania ryzykiem wewnętrznym aktywność użytkownika jest wykrywana pod kątem ryzykownych działań skojarzonych z wybranymi wskaźnikami. Nie musisz konfigurować zasad dla raportów aktywności użytkowników w celu wykrywania i zgłaszania ryzykownych działań użytkowników w organizacji. Działania zawarte w raportach aktywności użytkowników nie wymagają wyzwalania zdarzeń, aby działania były wyświetlane. Ta konfiguracja oznacza, że wszystkie wykryte działania użytkownika są dostępne do przeglądu, niezależnie od tego, czy ma zdarzenie wyzwalające lub czy tworzy alert. Raporty są tworzone dla poszczególnych użytkowników i mogą obejmować wszystkie działania w niestandardowym okresie 90 dni. Wiele raportów dla tego samego użytkownika nie jest obsługiwanych.

Po zbadaniu działań dla użytkownika badacze mogą odrzucić poszczególne działania jako łagodne, udostępnić lub wysłać link do raportu e-mail z innymi badaczami lub zdecydować się na tymczasowe lub jawne przypisanie użytkownika do zasad zarządzania ryzykiem wewnętrznym. Użytkownicy muszą zostać przypisani do grupy ról *Badacze zarządzania ryzykiem wewnętrznym* , aby wyświetlić stronę **Raporty aktywności użytkowników** .  

![Omówienie raportu aktywności użytkownika dotyczącego zarządzania ryzykiem wewnętrznym.](../media/insider-risk-user-activity-report-overview.png)

Możesz rozpocząć pracę, wybierając pozycję **Zarządzaj raportami** w sekcji **Badanie aktywności użytkownika** na stronie **Omówienie** zarządzania ryzykiem wewnętrznym. Aby wyświetlić działania użytkownika, najpierw wybierz pozycję **Utwórz raport aktywności użytkownika** i wypełnij następujące pola w okienku **Raport aktywności nowego użytkownika** :

- **Użytkownik**: wyszukaj użytkownika według nazwy lub adresu e-mail
- **Data rozpoczęcia**: użyj kontrolki kalendarza, aby wybrać datę rozpoczęcia działań użytkownika.
- **Data zakończenia**: użyj kontrolki kalendarza, aby wybrać datę zakończenia działań użytkownika. Wybrana data zakończenia musi być większa niż dwa dni po wybranej dacie rozpoczęcia i nie większa niż 90 dni od wybranej daty rozpoczęcia.
Nowe raporty zwykle trwają do 10 godzin, zanim będą gotowe do przeglądu. Gdy raport będzie gotowy, zobaczysz pozycję *Raport gotowy* w kolumnie **Stan** na stronie Raport aktywności użytkownika. Wybierz użytkownika, aby wyświetlić szczegółowy raport:

![Raport aktywności użytkownika dotyczący zarządzania ryzykiem wewnętrznym.](../media/insider-risk-user-activity-report.png)

**Raport aktywności użytkownika** dla wybranego użytkownika zawiera karty **Aktywność użytkownika** i **Eksplorator działań**:

- **Aktywność użytkownika**: użyj tego widoku wykresu, aby zbadać działania i wyświetlić potencjalne działania występujące w sekwencjach. Ta karta ma strukturę umożliwiającą szybkie przeglądanie sprawy, w tym historyczną oś czasu wszystkich działań, szczegóły działania, bieżący wynik ryzyka dla użytkownika w przypadku, sekwencję zdarzeń o podwyższonym ryzyku i mechanizmy filtrowania ułatwiające wykonywanie działań dochodzeniowych.
- **Eksplorator działań**: karta **Eksplorator działań** udostępnia badaczom ryzyka kompleksowe narzędzie analityczne, które zawiera szczegółowe informacje o działaniach. W Eksploratorze działań recenzenci mogą szybko przejrzeć oś czasu wykrytych ryzykownych działań oraz zidentyfikować i odfiltrować wszystkie działania związane z ryzykiem skojarzone z alertami. Aby dowiedzieć się więcej na temat korzystania z Eksploratora działań, zobacz sekcję *Eksplorator działań w dalszej* części tego artykułu.

## <a name="alert-dashboard"></a>Pulpit nawigacyjny alertów

Alerty dotyczące zarządzania ryzykiem wewnętrznym są automatycznie generowane przez wskaźniki ryzyka zdefiniowane w zasadach zarządzania ryzykiem wewnętrznym. Te alerty zapewniają analitykom zgodności i badaczom szczegółowy widok bieżącego stanu ryzyka i umożliwiają organizacji klasyfikację i podjęcie działań w przypadku wykrytego ryzyka. Domyślnie zasady generują pewną liczbę alertów o niskiej, średniej i wysokiej ważności, ale możesz [zwiększyć lub zmniejszyć liczbę alertów](insider-risk-management-settings.md#alert-volume) zgodnie z potrzebami. Ponadto można skonfigurować [próg alertu dla wskaźników zasad](insider-risk-management-settings.md#indicator-level-settings-preview) podczas tworzenia nowych zasad przy użyciu narzędzia do tworzenia zasad.

Zapoznaj się z [filmem przedstawiającym środowisko klasyfikacji alertów zarządzania ryzykiem wewnętrznym](https://www.youtube.com/watch?v=KgmpxBLJLPI) , aby zapoznać się z omówieniem sposobu, w jaki alerty zawierają szczegółowe informacje, kontekst i powiązaną zawartość ryzykownych działań oraz jak sprawić, by proces badania był bardziej skuteczny.

**Pulpit nawigacyjny alertów o** ryzyku wewnętrznym umożliwia wyświetlanie alertów generowanych przez zasady ryzyka związanego z wewnętrznym dostępem i działanie na ich podstawie. Każdy widżet raportu wyświetla informacje z ostatnich 30 dni.

- **Łączna liczba alertów, które wymagają przeglądu**: wyświetlana jest całkowita liczba alertów wymagających przeglądu i klasyfikacji, w tym podział według ważności alertu.
- **Otwórz alerty w ciągu ostatnich 30 dni**: całkowita liczba alertów utworzonych przez zasady jest zgodna z zasadami w ciągu ostatnich 30 dni, posortowana według wysokich, średnich i niskich poziomów ważności alertów.
- **Średni czas rozwiązywania alertów**: podsumowanie przydatnych statystyk alertów:
  - Średni czas rozwiązywania alertów o wysokiej ważności wymienionych w godzinach, dniach lub miesiącach.
  - Średni czas rozwiązywania alertów o średniej ważności wymienionych w godzinach, dniach lub miesiącach.
  - Średni czas rozwiązywania alertów o niskiej ważności wymienionych w godzinach, dniach lub miesiącach.

![Pulpit nawigacyjny alertu dotyczącego zarządzania ryzykiem wewnętrznym.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> Zarządzanie ryzykiem wewnętrznym korzysta z wbudowanego ograniczania alertów, aby chronić i optymalizować badanie ryzyka i środowisko przeglądu. To ograniczanie zabezpieczeń chroni przed problemami, które mogą spowodować przeciążenie alertów zasad, takich jak błędnie skonfigurowane łączniki danych lub zasady DLP. W związku z tym może wystąpić opóźnienie wyświetlania nowych alertów dla użytkownika.

## <a name="alert-status-and-severity"></a>Stan i ważność alertu

Alerty można klasyfikować do jednego z następujących stanów:

- **Potwierdzone**: alert został potwierdzony i przypisany do nowego lub istniejącego przypadku.
- **Odrzucone**: alert odrzucony jako łagodny w procesie klasyfikacji. Możesz podać przyczynę zwolnienia alertu i uwzględnić notatki, które są dostępne w historii alertów użytkownika, aby zapewnić dodatkowy kontekst dla przyszłego odwołania lub dla innych recenzentów. Przyczyny te mogą się wahać od oczekiwanych działań, zdarzeń niewpływających, po prostu zmniejszenia liczby działań alertów dla użytkownika lub przyczyny związanej z informacjami o alertach. Opcje klasyfikacji przyczyn obejmują *działanie oczekiwane dla tego użytkownika*, *działanie jest wystarczająco ważne, abym mógł dokładniej zbadać*, a *alerty dla tego użytkownika zawierają zbyt wiele działań*.
- **Przegląd potrzeb**: nowy alert, w którym akcje klasyfikacji nie zostały jeszcze wykonane.
- **Rozwiązano**: alert będący częścią zamkniętego i rozwiązanego przypadku.

Wyniki ryzyka alertów są automatycznie obliczane na podstawie kilku wskaźników aktywności ryzyka. Wskaźniki te obejmują rodzaj działania związanego z ryzykiem, liczbę i częstotliwość występowania działania, historię aktywności związaną z ryzykiem użytkownika oraz dodanie ryzyka związanego z działaniami, które może zwiększyć powagę działania. Ocena ryzyka alertu powoduje programowe przypisanie poziomu ważności ryzyka dla każdego alertu i nie można go dostosować. Jeśli alerty pozostaną niezarządzane, a działania związane z ryzykiem będą nadal naliczane do alertu, poziom ważności ryzyka może wzrosnąć. Analitycy ryzyka i badacze mogą używać ważności ryzyka alertów, aby ułatwić klasyfikację alertów zgodnie z zasadami i standardami ryzyka organizacji.

Poziomy ważności ryzyka alertu to:

- **Wysoka ważność**: działania i wskaźniki alertu stanowią znaczne ryzyko. Związane z tym działania związane z ryzykiem są poważne, powtarzalne i silnie skorelują się z innymi istotnymi czynnikami ryzyka.
- **Średnia ważność**: działania i wskaźniki alertu stanowią umiarkowane ryzyko. Skojarzone działania związane z ryzykiem są umiarkowane, częste i mają pewną korelację z innymi czynnikami ryzyka.
- **Niska ważność**: działania i wskaźniki alertu stanowią niewielkie ryzyko. Skojarzone działania związane z ryzykiem są niewielkie, bardziej rzadkie i nie są powiązane z innymi istotnymi czynnikami ryzyka.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrowanie alertów na pulpicie nawigacyjnym alertów

W zależności od liczby i typu aktywnych zasad zarządzania ryzykiem wewnętrznym w organizacji przejrzenie dużej kolejki alertów może być trudne. Użycie filtrów alertów może pomóc analitykom i badaczom sortować alerty według kilku atrybutów. Aby filtrować alerty na **pulpicie nawigacyjnym Alerty**, wybierz kontrolkę **Filtr** . Alerty można filtrować według co najmniej jednego atrybutu:

- **Stan**: wybierz co najmniej jedną wartość stanu, aby odfiltrować listę alertów. Opcje to *Potwierdzone*, *Odrzucone*, *Przegląd potrzeb* i *Rozwiązane*.
- **Ważność**: wybierz co najmniej jeden poziom ważności alertu, aby odfiltrować listę alertów. Opcje są *wysokie*, *średnie* i *niskie*.
- **Wykryto czas**: wybierz daty rozpoczęcia i zakończenia utworzenia alertu. Ten filtr wyszukuje alerty między godziną UTC 00:00 w dniu rozpoczęcia a godziną UTC 00:00 w dniu końcowym. Aby filtrować alerty dla określonego dnia, wprowadź datę dnia w polu **Data rozpoczęcia** i datę następnego dnia w polu **Data zakończenia** .
- **Zasady**: wybierz co najmniej jedną zasadę, aby filtrować alerty generowane przez wybrane zasady.
- **Czynniki ryzyka**: wybierz jeden z dodatkowych czynników ryzyka, aby odfiltrować listę alertów. Opcje to *skumulowane działania eksfiltracji*, *działania obejmują zawartość priorytetową*, *działania sekwencji* i *działania obejmują niedozwolone domeny*.

## <a name="search-alerts-on-the-alert-dashboard"></a>Wyszukiwanie alertów na pulpicie nawigacyjnym alertów

Aby wyszukać nazwę alertu dla określonego wyrazu, wybierz kontrolkę **Wyszukaj** i wpisz wyraz do wyszukania. Wyniki wyszukiwania zawierają wszystkie alerty zasad zawierające słowo zdefiniowane w wyszukiwaniu.

## <a name="dismiss-multiple-alerts-preview"></a>Odrzucanie wielu alertów (wersja zapoznawcza)

Może to pomóc zaoszczędzić czas klasyfikacji dla analityków i badaczy, aby natychmiast odrzucić wiele alertów jednocześnie. Opcja **Odrzuć alerty** na pasku poleceń umożliwia wybranie co najmniej jednego alertu ze stanem *Przeglądu potrzeb* na pulpicie nawigacyjnym i szybkie odrzucenie tych alertów jako niegroźnych odpowiednio w procesie klasyfikacji. Możesz wybrać maksymalnie 400 alertów do odrzucenia jednocześnie.

Aby odrzucić alert o ryzyku wewnętrznym, wykonaj następujące kroki:

1. W [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Alerty**.
2. Na **pulpicie nawigacyjnym Alerty** wybierz alert (lub alerty) ze stanem *Przegląd potrzeb* , który chcesz odrzucić.
3. Na pasku poleceń Alerty wybierz pozycję **Odrzuć alerty**.
4. W okienku Szczegół **odrzuć alerty** możesz przejrzeć szczegóły użytkownika i zasad skojarzone z wybranymi alertami.
5. Wybierz pozycję **Odrzuć alerty** , aby rozpoznać alerty jako niegroźne, lub wybierz pozycję **Anuluj** , aby zamknąć okienko szczegółów bez odrzucania alertów.

## <a name="triage-alerts"></a>Klasyfikacja alertów

Aby sklasyfikować alert o ryzyku wewnętrznym, wykonaj następujące kroki:

1. W [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Alerty**.
2. Na **pulpicie nawigacyjnym Alerty** wybierz alert, który chcesz sklasyfikować.
3. Na stronie **Szczegóły alertu** możesz przejrzeć informacje o alertie. Możesz potwierdzić alert i utworzyć nowy przypadek, potwierdzić alert i dodać go do istniejącego przypadku lub odrzucić alert. Ta strona zawiera również bieżący stan alertu i poziom ważności zagrożenia alertu, wymieniony jako Wysoki, Średni lub Niski. Jeśli alert nie jest klasyfikowany, poziom ważności może się zwiększać lub zmniejszać w miarę upływu czasu.

Aby uzyskać więcej informacji na temat alertu, skorzystaj z następujących sekcji i kart na stronie szczegółów alertu:

### <a name="headersummary-section"></a>Sekcja nagłówka/podsumowania

Ta sekcja zawiera ogólne informacje o użytkowniku i alertie. Te informacje są dostępne dla kontekstu podczas przeglądania szczegółowych informacji o wykrytych działaniach uwzględnionych w alercie dla użytkownika:

- **Działanie, które wygenerowało ten alert**: wyświetla działanie o najwyższym ryzyku i dopasowanie zasad w okresie oceny działania, które doprowadziło do wygenerowania alertu.
- **Zdarzenie wyzwalające**: wyświetla najnowsze zdarzenie wyzwalające, które skłoniło zasady do rozpoczęcia przypisywania wyników ryzyka do działania użytkownika.
- **Profil użytkownika**: wyświetla ogólne informacje o użytkowniku przypisanym do alertu. Jeśli anonimizacja jest włączona, pola nazwy użytkownika, adresu e-mail, aliasu i organizacji zostaną zanonimizowane.
- **Historia alertów użytkownika**: wyświetla listę alertów dla użytkownika z ostatnich 30 dni. Zawiera link umożliwiający wyświetlenie pełnej historii alertów dla użytkownika.

### <a name="all-risk-factors"></a>Wszystkie czynniki ryzyka

Ta karta otwiera podsumowanie czynników ryzyka dla działania alertu użytkownika. Czynniki ryzyka mogą pomóc w określeniu, jak ryzykowne jest działanie tego użytkownika podczas przeglądu. Czynniki ryzyka obejmują podsumowania dla:

- **Najważniejsze działania eksfiltracji**: wyświetla działania eksfiltracji z największą liczbą lub zdarzeniami dla alertu.
- **Skumulowane działania eksfiltracji**: wyświetla zdarzenia skojarzone z skumulowanymi działaniami eksfiltracji.
- **Sekwencje działań**: wyświetla wykryte działania skojarzone z sekwencjami ryzyka.
- **Nietypowe działanie dla tego użytkownika**: wyświetla działania dla użytkownika, które są uważane za nietypowe, i odejście od ich zwykłych działań.
- **Zawartość priorytetowa**: wyświetla działania skojarzone z zawartością priorytetu.
- **Niezamówiene domeny**: wyświetla działania dla zdarzeń skojarzonych z niedozwolonymi domenami.
- **Dostęp do rekordu** kondycji: wyświetla działania dla zdarzeń skojarzonych z uzyskiwaniem dostępu do rekordów kondycji.

W przypadku tych filtrów będą widoczne tylko alerty z tymi czynnikami ryzyka, ale działanie, które wygenerowało alert, może nie należeć do żadnej z tych kategorii. Na przykład alert zawierający działania sekwencji mógł zostać wygenerowany tylko dlatego, że użytkownik skopiował plik na urządzenie USB.

### <a name="content-detected"></a>Wykryto zawartość

Sekcja na karcie **Wszystkie czynniki ryzyka** zawiera zawartość skojarzoną z działaniami ryzyka dla alertu i podsumowuje zdarzenia działania według kluczowych obszarów. Wybranie linku działania powoduje otwarcie Eksploratora działań i wyświetlenie dodatkowych szczegółów dotyczących działania.

### <a name="activity-explorer"></a>Eksplorator działań

Ta karta otwiera Eksploratora działań. Aby uzyskać więcej informacji, zobacz sekcję Eksplorator działań w tym artykule.

### <a name="user-activity"></a>Aktywność użytkownika

Wykres **aktywności użytkowników** jest jednym z najbardziej zaawansowanych narzędzi do wewnętrznej analizy ryzyka i badania alertów i przypadków w rozwiązaniu do zarządzania ryzykiem wewnętrznym. Ta karta ma strukturę umożliwiającą szybkie przeglądanie wszystkich działań użytkownika, w tym historycznej osi czasu wszystkich alertów, szczegółów alertów, bieżącej oceny ryzyka dla użytkownika i sekwencji zdarzeń o podwyższonym ryzyku.  

![Działania użytkowników związane z zarządzaniem ryzykiem wewnętrznym.](../media/insider-risk-user-activities.png)

1. **Filtry czasu**: domyślnie ostatnie trzy miesiące działań wyświetlanych na wykresie aktywności użytkowników. Widok wykresu można łatwo filtrować, wybierając karty *6 miesięcy*, *3 miesięcy* lub *1 miesiąca* na wykresie bąbelkowym.
2. **Działanie alertu o ryzyku i szczegóły**: działania związane z ryzykiem są wizualnie wyświetlane jako kolorowe bąbelki na wykresie aktywności użytkownika. Bąbelki są tworzone dla różnych kategorii ryzyka i. Wybierz bąbelek, aby wyświetlić szczegóły poszczególnych działań związanych z ryzykiem. Szczegóły obejmują:
    - **Data** działania związanego z ryzykiem.
    - **Kategoria działania związanego z ryzykiem**. Na przykład *wiadomości e-mail z załącznikami wysłanymi poza organizację* lub *pliki pobrane z usługi SharePoint Online*.
    - **Ocena ryzyka** dla alertu. Ten wynik jest liczbowym wynikiem dla poziomu ważności ryzyka alertu.
    - Liczba zdarzeń skojarzonych z alertem. Dostępne są również linki do każdego pliku lub wiadomości e-mail skojarzonych z działaniem ryzyka.
3. **Filtry i sortowanie (wersja zapoznawcza):**
    - **Kategoria ryzyka**: Filtruj działania według następujących kategorii ryzyka: *Działania z wynikami ryzyka > 15 (chyba że w sekwencji)* i *Działania sekwencji*.
    - **Typ działania**: filtruj działania według następujących typów: *Dostęp*, *Usuwanie*, *Kolekcja*, *Eksfiltracja*, *Infiltracja*, *Zaciemnianie* i *Zabezpieczenia*.
    - **Sortuj według**: wyświetl listę działań osi czasu według *daty lub* *oceny ryzyka*.
4. **Sekwencja ryzyka (wersja zapoznawcza)**: kolejność chronologiczna ryzykownych działań jest ważnym aspektem badania ryzyka, a zidentyfikowanie tych powiązanych działań jest ważnym elementem oceny ogólnego ryzyka dla organizacji. Powiązane działania alertów są wyświetlane z wierszami łączącymi, aby podkreślić, że te działania są skojarzone z większym obszarem ryzyka. Ten widok działań może pomóc śledczym dosłownie "połączyć kropki" dla działań związanych z ryzykiem, które mogły być postrzegane jako zdarzenia izolowane lub jednorazowe. Wybierz dowolny bąbelek w sekwencji, aby wyświetlić szczegóły wszystkich skojarzonych działań związanych z ryzykiem. Szczegóły obejmują:

    - **Nazwa** sekwencji.
    - **Zakres daty** lub **daty** sekwencji.
    - **Ocena ryzyka** dla sekwencji. Ten wynik jest liczbowym wynikiem dla sekwencji połączonych poziomów ważności ryzyka alertu dla każdego powiązanego działania w sekwencji.
    - **Liczba zdarzeń skojarzonych z każdym alertem w sekwencji**. Dostępne są również linki do każdego pliku lub wiadomości e-mail skojarzonych z każdym działaniem ryzyka.
    - **Pokaż działania w sekwencji**. Wyświetla sekwencję jako linię wyróżniania na wykresie bąbelkowym i rozszerza szczegóły alertu, aby wyświetlić wszystkie powiązane alerty w sekwencji.

5. **Legenda aktywności związanej z ryzykiem**: w dolnej części wykresu aktywności użytkownika legenda z kolorami pomaga szybko określić kategorię ryzyka dla każdego alertu.
6. **Chronologia działań związanych z ryzykiem**: wyświetlana jest pełna chronologia wszystkich alertów dotyczących ryzyka związanych ze sprawą, w tym wszystkie szczegóły dostępne w odpowiednim bąbelku alertów.
7. **Akcje sprawy**: opcje rozwiązywania sprawy znajdują się na pasku narzędzi akcji sprawy. Podczas wyświetlania w danym przypadku możesz rozwiązać problem, wysłać powiadomienie e-mail do użytkownika lub eskalować sprawę dotyczącą badania danych lub użytkownika.

## <a name="activity-explorer"></a>Eksplorator działań

> [!NOTE]
> Eksplorator działań jest dostępny w obszarze zarządzania alertami dla użytkowników z wyzwalaniem zdarzeń po udostępnieniu tej funkcji w organizacji.

Eksplorator działań udostępnia badaczom ryzyka i analitykom kompleksowe narzędzie analityczne, które udostępnia szczegółowe informacje o alertach. W Eksploratorze działań recenzenci mogą szybko przejrzeć oś czasu wykrytych ryzykownych działań oraz zidentyfikować i odfiltrować wszystkie działania związane z ryzykiem skojarzone z alertami. 

Aby filtrować alerty w Eksploratorze działań pod kątem informacji o kolumnie, wybierz kontrolkę Filtr. Alerty można filtrować według co najmniej jednego atrybutu wymienionego w okienku szczegółów alertu. Eksplorator działań obsługuje również dostosowywalne kolumny, aby ułatwić badaczom i analitykom skoncentrowanie pulpitu nawigacyjnego na najważniejszych dla nich informacjach.

Użyj filtrów Zakres działania i Analiza ryzyka, aby wyświetlać i sortować działania i szczegółowe informacje dla następujących obszarów.

- **Filtry zakresu działania**: filtruje wszystkie ocenione działania dla użytkownika.
  - Wszystkie ocenione działania dla tego użytkownika
  - Tylko ocenione działanie w tym alercie

- **Filtry czynników ryzyka**: filtry aktywności czynnika ryzyka stosowane dla wszystkich zasad przypisujących wyniki ryzyka Obejmuje to wszystkie działania dla wszystkich zasad dla użytkowników w zakresie.
  - Nietypowe działanie
  - Zawiera zdarzenia z zawartością priorytetu
  - Obejmuje zdarzenia z niedozwoloną domeną
  - Działania sekwencji
  - Skumulowane działania eksfiltracji
  - Działania dotyczące dostępu do rekordów kondycji

![Omówienie eksploratora działań zarządzania ryzykiem wewnętrznym.](../media/insider-risk-activity-explorer.png)

Aby użyć **Eksploratora działań**, wykonaj następujące kroki:

1. W [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Alerty**.
2. Na **pulpicie nawigacyjnym Alerty** wybierz alert, który chcesz sklasyfikować.
3. W **okienku Szczegóły alertów** wybierz pozycję **Otwórz rozwinięty widok**.
4. Na stronie wybranego alertu wybierz kartę **Eksplorator działań** .

Podczas przeglądania działań w Eksploratorze działań badacze i analitycy mogą wybrać określone działanie i otworzyć okienko szczegółów działania. W okienku zostaną wyświetlone szczegółowe informacje o działaniach, których mogą używać badacze i analitycy podczas procesu klasyfikacji alertów. Szczegółowe informacje mogą stanowić kontekst alertu i pomóc w zidentyfikowaniu pełnego zakresu działania ryzyka, które wyzwoliło alert.

Podczas wybierania z osi czasu działania zdarzeń działania liczba działań wyświetlanych w eksploratorze może nie być zgodna z liczbą zdarzeń działania wymienionych na osi czasu. Przykłady przyczyn występowania tej różnicy:

- **Skumulowane wykrywanie eksfiltracji**: skumulowane wykrywanie eksfiltracji analizuje dzienniki zdarzeń, ale stosuje model, który obejmuje de-duplikowanie podobnych działań do obliczeniowego skumulowanego ryzyka eksfiltracji. Ponadto może wystąpić różnica w liczbie działań wyświetlanych w Eksploratorze działań, jeśli wprowadzono zmiany w istniejących zasadach lub ustawieniach. Jeśli na przykład zmodyfikujesz dozwolone/niedozwolone domeny lub dodasz nowe wykluczenia typu pliku po utworzeniu zasad i wystąpieniu dopasowań działań, skumulowane działania wykrywania eksfiltracji będą się różnić od wyników przed zmianą zasad lub ustawień. Łączne sumy działań wykrywania eksfiltracji są oparte na konfiguracji zasad i ustawień w czasie obliczeń i nie obejmują działań przed zmianami zasad i ustawień
- **Wiadomości e-mail do zewnętrznych adresatów**: aktywność wiadomości e-mail wysyłanych do adresatów zewnętrznych jest przypisywana do oceny ryzyka na podstawie liczby wysłanych wiadomości e-mail, które mogą nie być zgodne z dziennikami zdarzeń aktywności.

![Szczegóły eksploratora działań zarządzania ryzykiem wewnętrznym.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Tworzenie przypadku alertu

Ponieważ alert jest przeglądany i klasyfikowany, możesz utworzyć nowy przypadek, aby dokładniej zbadać działanie związane z ryzykiem. Aby utworzyć przypadek dla alertu, wykonaj następujące kroki:

1. W [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Alerty**.
2. Na **pulpicie nawigacyjnym Alerty** wybierz alert, który chcesz potwierdzić, i utwórz nowy przypadek.
3. W **okienku Szczegóły alertów** wybierz pozycję **AkcjeKonfirmuj alerty & utwórz przypadek**. > 
4. W oknie dialogowym **Potwierdzanie alertu i tworzenie przypadku ryzyka związanego z ryzykiem wewnętrznym** wprowadź nazwę sprawy, wybierz użytkowników, którzy mają zostać dodani jako współautorzy, i dodaj komentarze zgodnie z wymaganiami. Komentarze są automatycznie dodawane do sprawy jako notatka o przypadku.
5. Wybierz pozycję **Utwórz przypadek** , aby utworzyć nowy przypadek, lub wybierz pozycję **Anuluj** , aby zamknąć okno dialogowe bez tworzenia sprawy.

Po utworzeniu sprawy śledczy i analitycy mogą zarządzać sprawą i działać w tej sprawie. Aby uzyskać więcej informacji, zobacz artykuł Dotyczący [przypadków zarządzania ryzykiem wewnętrznym](insider-risk-management-cases.md) .

## <a name="retention-and-item-limits"></a>Limity przechowywania i elementów

Wraz ze starzeniem się alertów dotyczących zarządzania ryzykiem wewnętrznym ich wartość minimalizująca ryzykowną aktywność zmniejsza się w większości organizacji. Z drugiej strony aktywne przypadki i skojarzone artefakty (alerty, szczegółowe informacje, działania) są zawsze cenne dla organizacji i nie powinny mieć automatycznej daty wygaśnięcia. Obejmuje to wszystkie przyszłe alerty i artefakty w stanie aktywnym dla każdego użytkownika skojarzonego z aktywnym przypadkiem.

Aby zminimalizować liczbę starszych elementów, które zapewniają ograniczoną bieżącą wartość, następujące okresy przechowywania i limity mają zastosowanie w przypadku alertów, przypadków i raportów aktywności użytkowników dotyczących zarządzania ryzykiem wewnętrznym:

|Element|Przechowywanie/limit|
|---|---|
|Alerty ze stanem przeglądu potrzeb|120 dni od utworzenia alertu, a następnie automatyczne usunięcie|
|Aktywne przypadki (i skojarzone artefakty)|Przechowywanie na czas nieokreślony, nigdy nie wygasa|
|Rozwiązane przypadki (i skojarzone artefakty)|120 dni od rozwiązania sprawy, a następnie automatycznie usunięte|
|Maksymalna liczba aktywnych przypadków|100|
|Raporty działań użytkowników|120 dni od wykrycia aktywności, a następnie automatyczne usunięcie|

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Uzyskiwanie pomocy dotyczącej zarządzania kolejką alertów o ryzyku wewnętrznym

Przeglądanie, badanie i działanie w przypadku alertów o ryzyku wewnętrznym to ważne elementy minimalizowania ryzyka związanego z informacjami poufnymi w organizacji. Szybkie podejmowanie działań w celu zminimalizowania wpływu tych zagrożeń może potencjalnie zaoszczędzić czas, pieniądze oraz konsekwencje prawne lub prawne dla organizacji. W tym procesie korygowania pierwszy krok przeglądania alertów może wydawać się najtrudniejszym zadaniem dla wielu analityków i badaczy. W zależności od okoliczności może wystąpić kilka drobnych przeszkód podczas działania na podstawie alertów o ryzyku wewnętrznym. Zapoznaj się z poniższymi zaleceniami i dowiedz się, jak zoptymalizować proces przeglądu alertów.

### <a name="too-many-alerts-to-review"></a>Zbyt wiele alertów do przejrzenia

Przeciążanie się liczbą alertów generowanych przez zasady zarządzania ryzykiem wewnętrznym może być frustrujące. Liczba alertów można szybko rozwiązać za pomocą prostych kroków, w zależności od typów otrzymywanych woluminów alertów. Być może otrzymujesz zbyt wiele prawidłowych alertów lub masz zbyt wiele nieaktualnych alertów niskiego ryzyka. Rozważ podjęcie następujących akcji:

- **Dostosuj zasady ryzyka wewnętrznego**: wybranie i skonfigurowanie prawidłowych zasad ryzyka wewnętrznego jest najbardziej podstawową metodą rozwiązywania problemów z typem i ilością alertów. Począwszy od odpowiedniego [szablonu zasad](insider-risk-management-policies.md#policy-templates) , można skoncentrować typy działań i alertów dotyczących ryzyka, które zobaczysz. Inne czynniki, które mogą mieć wpływ na wolumin alertów, to rozmiar użytkownika i grup w zakresie oraz [priorytetyzowana](insider-risk-management-policies.md#prioritize-content-in-policies) zawartość i kanały. Rozważ dostosowanie zasad w celu dostosowania tych obszarów do tego, co jest najważniejsze dla Twojej organizacji.
- **Zmodyfikuj ustawienia ryzyka związanego z informacjami poufnymi**: ustawienia ryzyka dla niejawnych testerów obejmują szeroką gamę opcji konfiguracji, które mogą mieć wpływ na ilość i typy otrzymywanych alertów. Obejmują one ustawienia [wskaźników zasad](insider-risk-management-settings.md#indicators), [progów wskaźników](insider-risk-management-settings.md#indicator-level-settings-preview) i [ram czasowych zasad](insider-risk-management-settings.md#policy-timeframes). Rozważ skonfigurowanie [inteligentnych opcji wykrywania w celu wykluczenia](insider-risk-management-settings.md#intelligent-detections) określonych typów plików, zdefiniowanie minimalnych progów przed zgłoszeniem alertów aktywności przez zasady i zmianę konfiguracji woluminu alertów na niższe.
- **Zbiorcze usuwanie alertów, jeśli ma to zastosowanie**: może pomóc zaoszczędzić czas klasyfikacji dla analityków i badaczy, aby natychmiast [odrzucić wiele alertów](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) jednocześnie. Możesz wybrać maksymalnie 400 alertów do odrzucenia jednocześnie.

### <a name="not-familiar-with-the-alert-triage-process"></a>Nie znasz procesu klasyfikacji alertów

Badanie i działanie w oparciu o alerty w zakresie zarządzania ryzykiem wewnętrznym jest proste:

1. **Przejrzyj [pulpit nawigacyjny alertów](insider-risk-management-activities.md#alert-dashboard) , aby uzyskać alerty ze stanem Przegląd potrzeb**. [Filtruj](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) według *stanu* alertu, jeśli jest to konieczne, aby ułatwić lokalizowanie tego typu alertów.
2. **Zacznij od alertów o najwyższej ważności**. [Filtruj](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) według *ważności* alertu, jeśli jest to konieczne, aby ułatwić lokalizowanie tego typu alertów.
3. **Wybierz alert, aby dowiedzieć się więcej informacji i przejrzeć szczegóły alertu**. W razie potrzeby użyj [Eksploratora działań](insider-risk-management-activities.md#activity-explorer) , aby przejrzeć oś czasu skojarzonego ryzykownego zachowania i zidentyfikować wszystkie działania związane z ryzykiem dla alertu.
4. **Działaj zgodnie z alertem**. Możesz potwierdzić i [utworzyć przypadek](insider-risk-management-activities.md#create-a-case-for-an-alert) dla alertu lub odrzucić i rozwiązać alert.

### <a name="resource-constraints-in-my-organization"></a>Ograniczenia zasobów w mojej organizacji

Współcześni użytkownicy w miejscu pracy często mają wiele różnych obowiązków i wymagań dotyczących swojego czasu. Istnieje kilka akcji, które można wykonać, aby rozwiązać problem z ograniczeniami zasobów:

- **Najpierw skoncentruj działania analityków i badaczy na alertach o najwyższym ryzyku**. W zależności od zasad możesz przechwytywać działania i generować alerty o różnym stopniu potencjalnego wpływu na działania związane z ograniczaniem ryzyka. [Filtrowanie alertów](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) według ważności i określanie priorytetów alertów *o wysokiej ważności* .
- **Przypisz użytkowników jako analityków i badaczy**. Przypisanie odpowiedniego użytkownika do odpowiednich ról jest ważną częścią procesu przeglądu alertów o ryzyku wewnętrznym. Upewnij się, że przypisano odpowiednich użytkowników do grup ról *Insider Risk Management Analysts* i *Insider Risk Management Investigators* .  
- **Użyj zautomatyzowanych funkcji ryzyka wewnętrznych, aby ułatwić odnajdywanie działań o najwyższym ryzyku**. [Funkcje wykrywania sekwencji zarządzania](insider-risk-management-policies.md#sequence-detection-preview) ryzykiem wewnętrznym i [zbiorczego wykrywania eksfiltracji](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) mogą pomóc w szybkim odnalezieniu zagrożeń w organizacji. Rozważ dostrojenie [dopalaczy oceny ryzyka](insider-risk-management-settings.md#indicators), [wykluczeń typów plików](insider-risk-management-settings.md#file-type-exclusions), [domen](insider-risk-management-settings.md#domains) i [ustawień minimalnego progu wskaźnika](insider-risk-management-settings.md#indicator-level-settings-preview) dla zasad.
