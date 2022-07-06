---
title: Przypadki zarządzania ryzykiem wewnętrznym
description: Dowiedz się więcej o przypadkach zarządzania ryzykiem wewnętrznym w usłudze Microsoft Purview
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
ms.openlocfilehash: 678d500b5d523c2b656f4f30fa4ef4a4ed5015a7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628710"
---
# <a name="insider-risk-management-cases"></a>Przypadki zarządzania ryzykiem wewnętrznym

Przypadki są sednem zarządzania ryzykiem wewnętrznym i umożliwiają głębokie badanie i działanie w przypadku problemów generowanych przez wskaźniki ryzyka zdefiniowane w zasadach. Przypadki są tworzone ręcznie na podstawie alertów w sytuacjach, w których konieczne jest podjęcie dalszych działań w celu rozwiązania problemu związanego ze zgodnością dla użytkownika. Każdy przypadek jest ograniczony do pojedynczego użytkownika, a wiele alertów dla użytkownika można dodać do istniejącego przypadku lub do nowego przypadku.

Po zbadaniu szczegółów sprawy możesz podjąć działania, wykonując następujące czynności:

- wysyłanie użytkownikowi powiadomienia
- rozpoznawanie sprawy jako łagodnej
- udostępnianie sprawy wystąpieniu usługi ServiceNow lub adresatowi wiadomości e-mail
- eskalowanie sprawy dotyczącej dochodzenia zbierania elektronicznych materiałów dowodowych (Premium)

Zapoznaj się z [filmem Dotyczącym badania i eskalacji w ramach zarządzania ryzykiem wewnętrznym](https://www.youtube.com/watch?v=UONUSmkRC8s) , aby zapoznać się z omówieniem sposobu badania przypadków i zarządzania nimi w ramach zarządzania ryzykiem wewnętrznym.

## <a name="cases-dashboard"></a>Pulpit nawigacyjny przypadków

**Pulpit nawigacyjny Przypadków** zarządzania ryzykiem wewnętrznym umożliwia wyświetlanie i działanie w sprawach. Każdy widżet raportu na pulpicie nawigacyjnym wyświetla informacje z ostatnich 30 dni.

- **Aktywne sprawy**: całkowita liczba aktywnych spraw objętych dochodzeniem.
- **Przypadki w ciągu ostatnich 30 dni**: całkowita liczba utworzonych przypadków posortowanych według stanu *Aktywne* i *Zamknięte* .
- **Statystyki**: średni czas aktywnych przypadków, wymieniony w godzinach, dniach lub miesiącach.

Kolejka przypadków zawiera listę wszystkich aktywnych i zamkniętych spraw dla twojej organizacji, oprócz bieżącego stanu następujących atrybutów przypadku:

- **Nazwa przypadku**: nazwa sprawy, zdefiniowana po potwierdzeniu alertu i utworzeniu sprawy.  
- **Stan**: stan sprawy *Aktywny* lub *Zamknięty*.
- **Użytkownik**: użytkownik w tym przypadku. Jeśli włączono anonimizację nazw użytkowników, są wyświetlane zanonimizowane informacje.
- **Sprawa czasowa otwarta**: czas, który minął od czasu otwarcia sprawy.
- **Łączna liczba alertów zasad**: liczba dopasowań zasad uwzględnionych w tym przypadku. Ta liczba może wzrosnąć, jeśli do sprawy zostaną dodane nowe alerty.
- **Przypadek ostatniej aktualizacji**: czas, który minął od momentu dodania noty sprawy lub zmiany stanu sprawy.
- **Ostatnia aktualizacja**: nazwa analityka lub badacza zarządzania ryzykiem wewnętrznym, który ostatnio zaktualizował sprawę.

![Pulpit nawigacyjny Przypadków zarządzania ryzykiem wewnętrznym.](../media/insider-risk-cases-dashboard.png)

Użyj **kontrolki Wyszukiwania** , aby wyszukać nazwy przypadków dla określonego tekstu i użyć filtru przypadku do sortowania przypadków według następujących atrybutów:

- Stan
- Przypadek godziny otwarcia, data rozpoczęcia i data zakończenia
- Ostatnia aktualizacja, data rozpoczęcia i data zakończenia

## <a name="filter-cases"></a>Przypadki filtrowania

W zależności od liczby i typu aktywnych zasad zarządzania ryzykiem wewnętrznym w organizacji przejrzenie dużej kolejki przypadków może być trudne. Użycie filtrów przypadków może pomóc analitykom i badaczom sortować przypadki według kilku atrybutów. Aby filtrować alerty na **pulpicie nawigacyjnym Przypadki**, wybierz kontrolkę **Filtruj** . Przypadki można filtrować według co najmniej jednego atrybutu:

- **Stan**: wybierz co najmniej jedną wartość stanu, aby odfiltrować listę przypadków. Opcje to *Aktywne* i *Zamknięte*.
- **Sprawa czasowa otwarta**: wybierz daty rozpoczęcia i zakończenia, kiedy sprawa została otwarta.
- **Ostatnia aktualizacja**: wybierz daty rozpoczęcia i zakończenia, kiedy sprawa została zaktualizowana.

## <a name="investigate-a-case"></a>Badanie sprawy

Dokładniejsze badanie alertów dotyczących zarządzania ryzykiem wewnętrznym ma kluczowe znaczenie dla podejmowania odpowiednich działań naprawczych. Przypadki zarządzania ryzykiem wewnętrznym to centralne narzędzie do zarządzania, które umożliwia dokładniejsze zapoznanie się z historią działań związanych z ryzykiem użytkownika, szczegółami alertów, sekwencją zdarzeń o podwyższonym ryzyku oraz badaniem zawartości i komunikatów narażonych na ryzyko. Analitycy ryzyka i badacze używają również przypadków do scentralizowania opinii i notatek przeglądowych oraz do rozpatrywania spraw.

Wybranie sprawy otwiera narzędzia do zarządzania przypadkami i umożliwia analitykom i śledczym analizowanie szczegółów spraw.

### <a name="case-overview"></a>Omówienie sprawy

Karta **Przegląd sprawy** zawiera podsumowanie szczegółów sprawy dla analityków ryzyka i badaczy. Zawiera ona następujące informacje w obszarze **Informacje o tym przypadku**

- **Stan**: bieżący stan sprawy, Aktywny lub Zamknięty.
- **Przypadek utworzony w dniu**: data i godzina utworzenia sprawy.
- **Ocena ryzyka użytkownika**: bieżący obliczony poziom ryzyka użytkownika dla przypadku. Ten wynik jest obliczany co 24 godziny i używa wyników ryzyka alertów ze wszystkich aktywnych alertów skojarzonych z użytkownikiem.
- **Wiadomość e-mail**: alias wiadomości e-mail użytkownika dla sprawy.
- **Organizacja lub dział**: organizacja lub dział, do których przypisano użytkownika.
- **Nazwa menedżera**: nazwa menedżera użytkownika.
- **Wiadomość e-mail menedżera**: alias wiadomości e-mail menedżera użytkownika.

![Szczegóły sprawy dotyczącej zarządzania ryzykiem wewnętrznym.](../media/insider-risk-case-details.png)

Karta **Przegląd przypadku** zawiera również sekcję **Alerty** , która zawiera następujące informacje dotyczące alertów dopasowania zasad skojarzonych ze sprawą:

- **Dopasowania zasad**: nazwa zasad zarządzania ryzykiem wewnętrznym skojarzonych z alertami dopasowania dla działania użytkownika.
- **Stan**: stan alertu.
- **Ważność**: ważność alertu.
- **Wykryto czas**: czas, który minął od czasu wygenerowania alertu.

### <a name="alerts"></a>Alerty

Karta **Alerty** zawiera podsumowanie bieżących alertów uwzględnionych w tym przypadku. Nowe alerty mogą zostać dodane do istniejącego przypadku i zostaną dodane do kolejki **alertów** w miarę ich przypisywania. Kolejka zawiera następujące atrybuty alertów:

- Stan
- Waga
- Wykryto czas

Wybierz alert z kolejki, aby wyświetlić stronę **szczegółów alertu** .

Użyj kontrolki wyszukiwania, aby wyszukać nazwy alertów pod kątem określonego tekstu, a następnie użyj filtru alertów do sortowania przypadków według następujących atrybutów:

- Stan
- Waga
- Wykryto godzinę, datę rozpoczęcia i datę zakończenia

Użyj kontrolki filtru, aby filtrować alerty według kilku atrybutów, w tym:

- **Stan**: wybierz co najmniej jedną wartość stanu, aby odfiltrować listę alertów. Opcje to *Potwierdzone*, *Odrzucone*, *Przegląd potrzeb* i *Rozwiązane*.
- **Ważność**: wybierz co najmniej jeden poziom ważności alertu, aby odfiltrować listę alertów. Opcje są *wysokie*, *średnie* i *niskie*.
- **Wykryto czas**: wybierz daty rozpoczęcia i zakończenia utworzenia alertu.
- **Zasady**: wybierz co najmniej jedną zasadę, aby filtrować alerty generowane przez wybrane zasady.

### <a name="user-activity"></a>Aktywność użytkownika

Karta **Aktywność użytkownika** umożliwia analitykom ryzyka i badaczom przeglądanie szczegółów działania i używanie wizualnej reprezentacji wszystkich działań związanych z alertami i przypadkami ryzyka. Na przykład w ramach procesu klasyfikacji alertów analitycy mogą wymagać przejrzenia wszystkich działań związanych z ryzykiem związanych ze sprawą, aby uzyskać więcej szczegółów. W takich przypadkach badacze ryzyka mogą przeglądać szczegóły aktywności użytkownika i wykres bąbelkowy, aby ułatwić zrozumienie ogólnego zakresu działań związanych ze sprawą. Aby uzyskać więcej informacji na temat wykresu aktywności użytkowników, zobacz artykuł [Insider risk management activities (Działania związane z zarządzaniem ryzykiem wewnętrznym](insider-risk-management-activities.md#user-activity) ).

### <a name="activity-explorer-preview"></a>Eksplorator działań (wersja zapoznawcza)

Karta **Eksplorator działań** umożliwia analitykom ryzyka i badaczom przeglądanie szczegółów działań skojarzonych z alertami o ryzyku. Na przykład w ramach działań związanych z zarządzaniem sprawami śledczy i analitycy mogą wymagać przejrzenia wszystkich działań związanych z ryzykiem związanych ze sprawą, aby uzyskać więcej szczegółów. W **Eksploratorze działań** recenzenci mogą szybko przejrzeć oś czasu wykrytych ryzykownych działań oraz zidentyfikować i odfiltrować wszystkie działania związane z ryzykiem skojarzone z alertami.

Aby uzyskać więcej informacji na temat Eksploratora działań, zobacz artykuł [Insider risk management activities (Działania związane z zarządzaniem ryzykiem wewnętrznym](insider-risk-management-activities.md#activity-explorer) ).

### <a name="content-explorer"></a>Eksplorator zawartości

Karta **Eksplorator zawartości** umożliwia badaczom ryzyka przeglądanie kopii wszystkich pojedynczych plików i wiadomości e-mail skojarzonych z alertami o podwyższonym ryzyku. Jeśli na przykład alert zostanie utworzony, gdy użytkownik pobierze setki plików z usługi SharePoint Online, a działanie wyzwoli alert zasad, wszystkie pobrane pliki alertu zostaną przechwycone i skopiowane do przypadku zarządzania ryzykiem wewnętrznym z oryginalnych źródeł magazynu.

Eksplorator zawartości to zaawansowane narzędzie z podstawowymi i zaawansowanymi funkcjami wyszukiwania i filtrowania. Aby dowiedzieć się więcej na temat korzystania z Eksploratora zawartości, zobacz [Insider risk management Content explorer (Eksplorator zawartości zarządzania ryzykiem wewnętrznym](insider-risk-management-content-explorer.md)).

![Przypadek zarządzania ryzykiem wewnętrznym Eksplorator zawartości.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Uwagi dotyczące sprawy

Na karcie **Notatki** o przypadku w tym przypadku analitycy ryzyka i badacze dzielą się komentarzami, opiniami i szczegółowymi informacjami na temat swojej pracy w tej sprawie. Notatki są trwałymi dodatkami do sprawy i nie można ich edytować ani usuwać po zapisaniu notatki. Gdy przypadek jest tworzony na podstawie alertu, komentarze wprowadzone w oknie dialogowym **Potwierdzanie alertu i tworzenie przypadku ryzyka dla niejawnych testerów** są automatycznie dodawane jako uwaga dotycząca przypadku.

Na pulpicie nawigacyjnym notatek o przypadku są wyświetlane notatki użytkownika, który utworzył notatkę, oraz czas, który minął od momentu zapisania notatki. Aby wyszukać w polu tekstowym case note dla określonego słowa kluczowego, użyj przycisku **Wyszukaj** na pulpicie nawigacyjnym przypadku i wprowadź określone słowo kluczowe.

Aby dodać notatkę do sprawy:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Przypadki**.
2. Wybierz przypadek, a następnie wybierz kartę **Notatki o sprawie** .
3. Wybierz pozycję **Dodaj notatkę o wielkości liter**.
4. W oknie dialogowym **Dodawanie notatek przypadku** wpisz notatkę dla sprawy. Wybierz pozycję **Zapisz** , aby dodać notatkę do sprawy lub wybierz pozycję **Anuluj** zamknięcie bez zapisywania notatki w sprawie.

### <a name="contributors"></a>Współpracowników

Na **karcie Współautorzy** w tym przypadku analitycy ryzyka i badacze mogą dodawać innych recenzentów do sprawy. Domyślnie wszyscy użytkownicy przypisani do ról **Insider Risk Management Analysts** i **Insider Risk Management Investigators** są wymienieni jako współautorzy każdego aktywnego i zamkniętego przypadku. Tylko użytkownicy przypisani do roli **Badacze zarządzania ryzykiem wewnętrznym** mają uprawnienia do wyświetlania plików i komunikatów w Eksploratorze zawartości.

Tymczasowy dostęp do sprawy można udzielić, dodając użytkownika jako współautora. Współautorzy mają kontrolę nad zarządzaniem wszystkimi przypadkami w konkretnym przypadku, z wyjątkiem:

- Uprawnienie do potwierdzania lub odrzucania alertów
- Uprawnienie do edytowania współautorów w przypadku przypadków
- Uprawnienie do wyświetlania plików i komunikatów w Eksploratorze zawartości

Aby dodać współautora do sprawy:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Przypadki**.
2. Wybierz przypadek, a następnie wybierz kartę **Współautorzy** .
3. Wybierz pozycję **Dodaj współautora**.
4. W oknie dialogowym **Dodawanie współautora** zacznij wpisywać nazwę użytkownika, którego chcesz dodać, a następnie wybierz użytkownika z listy sugerowanych użytkowników. Ta lista jest generowana na podstawie usługi Azure Active Directory subskrypcji dzierżawy.
5. Wybierz pozycję **Dodaj** , aby dodać użytkownika jako współautora, lub wybierz pozycję **Anuluj** , aby zamknąć okno dialogowe bez dodawania użytkownika jako współautora.

## <a name="case-actions"></a>Akcje sprawy

Badacze ryzyka mogą podjąć działania w sprawie w jednej z kilku metod, w zależności od ważności sprawy, historii ryzyka użytkownika i wytycznych dotyczących ryzyka organizacji. W niektórych sytuacjach może być konieczne eskalowanie sprawy do użytkownika lub badania danych w celu współpracy z innymi obszarami organizacji i dokładniejszego poznania działań związanych z ryzykiem. Zarządzanie ryzykiem wewnętrznym jest ściśle zintegrowane z innymi rozwiązaniami usługi Microsoft Purview, które ułatwiają kompleksowe zarządzanie rozwiązaniami.

### <a name="send-email-notice"></a>Wysyłanie powiadomienia e-mail

W większości przypadków akcje użytkownika, które tworzą alerty o ryzyku wewnętrznym, są przypadkowe lub przypadkowe. Wysyłanie powiadomienia o przypomnieniu do użytkownika za pośrednictwem poczty e-mail jest skuteczną metodą dokumentowania przeglądu i akcji sprawy oraz jest metodą przypominającą użytkownikom o zasadach firmowych lub wskazującą im szkolenie odświeżania. Powiadomienia są generowane na podstawie [szablonów powiadomień tworzonych](insider-risk-management-notices.md) dla infrastruktury zarządzania ryzykiem wewnętrznym.

Należy pamiętać, że wysłanie powiadomienia e-mail do użytkownika ***nie** rozwiązuje sprawy jako _Closed*. W niektórych przypadkach możesz pozostawić sprawę otwartą po wysłaniu powiadomienia do użytkownika, aby wyszukać więcej działań związanych z ryzykiem bez otwierania nowego przypadku. Jeśli chcesz rozwiązać problem po wysłaniu powiadomienia, po wysłaniu powiadomienia musisz wybrać rozwiązanie **sprawy** jako kolejny krok.

Aby wysłać powiadomienie do użytkownika przypisanego do sprawy:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Przypadki**.
2. Wybierz przypadek, a następnie wybierz przycisk **Wyślij powiadomienie e-mail** na pasku narzędzi akcji sprawy.
3. W oknie dialogowym **Wysyłanie powiadomienia e-mail** wybierz kontrolkę listy rozwijanej **Wybierz szablon powiadomienia** , aby wybrać szablon powiadomienia dla powiadomienia. To zaznaczenie wstępnie wypełnia inne pola w zawiadomieniu.
4. Przejrzyj pola powiadomień i zaktualizuj je odpowiednio. Wprowadzone tutaj wartości zastąpią wartości szablonu.
5. Wybierz pozycję **Wyślij** , aby wysłać powiadomienie do użytkownika lub wybierz pozycję **Anuluj** , aby zamknąć okno dialogowe bez wysyłania powiadomienia do użytkownika. Wszystkie wysłane powiadomienia są dodawane do kolejki notatek o przypadku na pulpicie nawigacyjnym **Notatek sprawy** .

### <a name="escalate-for-investigation"></a>Eskalowanie w celu zbadania

Eskaluj sprawę do badania użytkownika w sytuacjach, w których wymagana jest dodatkowa kontrola prawna dla działania użytkownika związanego z ryzykiem. Ta eskalacja otwiera nową sprawę Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) w organizacji platformy Microsoft 365. Funkcja zbierania elektronicznych materiałów dowodowych (Premium) udostępnia kompleksowy przepływ pracy umożliwiający zachowanie, zbieranie, przeglądanie, analizowanie i eksportowanie zawartości, która odpowiada na wewnętrzne i zewnętrzne badania prawne organizacji. Umożliwia również zespołowi prawnemu zarządzanie całym przepływem pracy powiadomień o blokadzie prawnej w celu komunikowania się z opiekunami zaangażowanymi w sprawę. Eskalowanie do sprawy zbierania elektronicznych materiałów dowodowych (Premium) z przypadku zarządzania ryzykiem wewnętrznym pomaga zespołowi prawnemu podjąć odpowiednie działania i zarządzać zachowaniem zawartości. Aby dowiedzieć się więcej na temat przypadków zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Omówienie Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium)](overview-ediscovery-20.md).

Aby eskalować sprawę do badania użytkownika:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Przypadki**.
2. Wybierz przypadek, a następnie wybierz przycisk **Eskaluj do zbadania** na pasku narzędzi akcji sprawy.
3. W oknie dialogowym **Eskaluj do badania** wprowadź nazwę nowego badania użytkownika. W razie potrzeby wprowadź uwagi dotyczące sprawy i wybierz pozycję **Eskaluj**.
4. Przejrzyj pola powiadomień i zaktualizuj je odpowiednio. Wprowadzone tutaj wartości zastąpią wartości szablonu.
5. Wybierz pozycję **Potwierdź** , aby utworzyć przypadek badania użytkownika, lub wybierz pozycję **Anuluj** , aby zamknąć okno dialogowe bez tworzenia nowego przypadku badania użytkownika.

Po eskalacji przypadku zarządzania ryzykiem wewnętrznym do nowego przypadku badania użytkownika możesz przejrzeć nowy przypadek w obszarze **eDiscovery** > **Advanced** w portal zgodności Microsoft Purview.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Uruchamianie zautomatyzowanych zadań za pomocą przepływów usługi Power Automate w tym przypadku

Korzystając z zalecanych przepływów usługi Power Automate, badacze ryzyka i analitycy mogą szybko podjąć działania w celu:

- Żądanie informacji od działu kadr lub firmy na temat użytkownika w przypadku ryzyka związanego z wewnętrznym dostępem
- Powiadamianie menedżera, gdy użytkownik ma alert o ryzyku wewnętrznym
- Tworzenie rekordu w przypadku zarządzania ryzykiem wewnętrznym w usłudze ServiceNow
- Powiadamianie użytkowników o dodaniu ich do zasad ryzyka dotyczącego informacji poufnych

Aby uruchamiać przepływy usługi Power Automate lub zarządzać nimi w przypadku zarządzania ryzykiem wewnętrznym:

1. Wybierz pozycję **Automatyzuj** na pasku narzędzi akcji sprawy. 
2. Wybierz przepływ usługi Power Automate do uruchomienia, a następnie wybierz pozycję **Uruchom przepływ**. 
3. Po zakończeniu przepływu wybierz pozycję **Gotowe**.

Aby dowiedzieć się więcej na temat przepływów usługi Power Automate na potrzeby zarządzania ryzykiem wewnętrznym, zobacz [Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#power-automate-flows-preview).

### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Wyświetlanie lub tworzenie zespołu usługi Microsoft Teams w tej sprawie

Po włączeniu integracji usługi Microsoft Teams w celu zarządzania ryzykiem wewnętrznym w ustawieniach zespół usługi Microsoft Teams jest tworzony automatycznie za każdym razem, gdy alert zostanie potwierdzony i zostanie utworzony przypadek. Badacze ryzyka i analitycy mogą szybko otworzyć usługę Microsoft Teams i przejść bezpośrednio do zespołu w celu zgłoszenia sprawy, wybierając pozycję **Wyświetl zespół usługi Microsoft Teams** na pasku narzędzi akcji sprawy.

W przypadku spraw otwartych przed włączeniem integracji z zespołem firmy Microsoft badacze ryzyka i analitycy mogą utworzyć nowy zespół usługi Microsoft Teams dla danego przypadku, wybierając pozycję **Utwórz zespół usługi Microsoft Teams** na pasku narzędzi do akcji sprawy.

Po rozwiązaniu sprawy skojarzony zespół firmy Microsoft zostanie automatycznie zarchiwizowany (ukryty i przekształcony w tryb tylko do odczytu).

Aby dowiedzieć się więcej o usłudze Microsoft Teams na potrzeby zarządzania ryzykiem wewnętrznym, zobacz [Wprowadzenie do ustawień zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md#microsoft-teams-preview).

### <a name="resolve-the-case"></a>Rozwiązywanie problemu

Po zakończeniu przeglądu i zbadania przez analityków ryzyka i śledczych można rozwiązać sprawę, aby działać na wszystkich alertach obecnie uwzględnionych w tej sprawie. Rozwiązanie problemu powoduje dodanie klasyfikacji rozwiązania, zmianę stanu sprawy na *Zamknięte*, a przyczyny akcji rozwiązywania problemów są automatycznie dodawane do kolejki notatek o przypadku na pulpicie nawigacyjnym **Notatek** sprawy. Sprawy są rozwiązywane jako:

- **Niegroźne**: klasyfikacja przypadków, w których alerty dopasowania zasad są oceniane jako alerty o niskim ryzyku, inne niż poważne lub fałszywie dodatnie.
- **Potwierdzone naruszenie zasad**: klasyfikacja przypadków, w których alerty dopasowania zasad są oceniane jako ryzykowne, poważne lub w wyniku złośliwego zamiaru.

Aby rozwiązać problem:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Przypadki**.
2. Wybierz przypadek, a następnie wybierz przycisk **Rozwiąż sprawę** na pasku narzędzi akcji sprawy.
3. W oknie dialogowym **Rozwiązywanie sprawy** wybierz kontrolkę **rozwiąż jako** listę rozwijaną, aby wybrać klasyfikację rozpoznawania sprawy. Opcje to **łagodne** lub **potwierdzone naruszenie zasad**.
4. W oknie dialogowym **Rozwiązywanie sprawy** wprowadź przyczyny klasyfikacji rozwiązania w polu tekstowym **Akcja podjęta** .
5. Wybierz pozycję **Rozwiąż** , aby zamknąć sprawę, lub wybierz pozycję **Anuluj** zamknij okno dialogowe bez rozwiązywania sprawy.
