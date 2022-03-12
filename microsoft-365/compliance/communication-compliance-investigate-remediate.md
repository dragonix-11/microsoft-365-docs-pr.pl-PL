---
title: Badanie i rozwiązywanie problemów z alertami zgodności komunikacji
description: Badanie i korygowanie alertów zgodności komunikacji w programie Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: c44d710b4067ec12b0234c88e02d2d89729819a6
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449684"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Badanie i rozwiązywanie problemów z alertami zgodności komunikacji

Po skonfigurowaniu zasad zgodności komunikacji zaczną być odbierane alerty w Centrum zgodności platformy Microsoft 365 dotyczące problemów z komunikatami, które są zgodne z warunkami zasad. Postępuj zgodnie z instrukcjami przepływu pracy, aby zbadać i rozwiązać problemy z alertami.

## <a name="investigate-alerts"></a>Badanie alertów

Pierwszym krokiem do zbadania problemów wykrytych przez zasady jest przejrzenie alertów zgodności komunikacji w Centrum zgodności platformy Microsoft 365. W obszarze rozwiązania do zgodności komunikacji istnieje kilka obszarów, które ułatwiają szybkie badanie alertów w zależności od preferowanego sposobu wyświetlania grupowania alertów:

- **Strona Zasady zgodności komunikacji**: Po zalogowaniu się do witryny [usługi Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń administratora konta administratora w Twojej organizacji usługi Microsoft 365 wybierz pozycję Zgodność komunikacji,  aby wyświetlić stronę Zasady **zgodności komunikacji.** Na tej stronie są wyświetlane zasady zgodności komunikacji skonfigurowane dla Microsoft 365 organizacji oraz linki do zalecanych szablonów zasad. Każda z wymienionych zasad obejmuje liczbę alertów do przejrzenia, liczbę eskalacji i rozwiązanych elementów, stan zasad oraz datę i godzina ostatniego skanowania zasad. Wybranie zasad powoduje wyświetlenie wszystkich oczekujących alertów dotyczących dopasowania do zasad, wybranie określonego alertu w celu uruchomienia strony szczegółów zasad i rozpoczęcie działań naprawczych.
- **Alerty**: Przejdź do **complianceAlerts**  >  komunikacji, aby wyświetlić alerty z ostatnich 30 dni pogrupowane według zgodności zasad. Ten widok pozwala szybko sprawdzić, które zasady zgodności komunikacji generują większość alertów uporządkowanych według ważności. Aby rozpocząć działania naprawcze, wybierz zasady skojarzone z alertem, aby uruchomić **stronę Szczegóły** zasad. Na stronie **Szczegóły zasad** możesz przejrzeć podsumowanie działań na stronie Przegląd, przejrzeć wiadomości  alertów i działać na nich na stronie Oczekujące lub  przejrzeć historię alertów zamkniętych na stronie Rozstrzygnięte.
- **Raporty**: Przejdź do **complianceReports**  >  komunikacji, aby wyświetlić widżety raportów zgodności komunikacji. Każdy widżet zawiera przegląd działań i stanu zgodności komunikacji, w tym dostęp do bardziej szczegółowych informacji o dopasowaniach zasad i działaniach naprawczych.

### <a name="using-filters"></a>Używanie filtrów

Następnym krokiem jest posortowanie wiadomości, aby ułatwić badanie alertów. Na stronie **Szczegóły zasad** zgodność komunikacji obsługuje filtrowanie wielopoziomowe dla kilku pól wiadomości, co pozwala szybko badać i przeglądać wiadomości ze zgodnością zasad. Filtrowanie jest dostępne dla elementów oczekujących i rozwiązanych dla poszczególnych skonfigurowanych zasad. Możesz skonfigurować zapytania filtru dla zasad lub skonfigurować i zapisać zapytania filtru niestandardowego i domyślnego do użycia w poszczególnych zasadach. Po skonfigurowaniu pól dla filtru pola filtru są wyświetlane w górnej części kolejki komunikatów alertów, w których można skonfigurować określone wartości filtru.

W przypadku filtru daty data i godzina zdarzeń są podane w uniwersalnym czasie koordynowanej (UTC). Podczas filtrowania wiadomości dla widoków lokalna data/godzina użytkownika żądającego określa wyniki na podstawie konwersji lokalnej daty/czasu użytkownika na czas UTC. Jeśli na przykład użytkownik w czasie pacyficznego czasu letniego (PDT) filtruje raport od 2021-08-30 do 2021-08-31 o 00:00, raport będzie zawierał wiadomości od 2021-08-30 07:00 czasu UTC do 2021-08-31 07:00. Jeśli ten sam użytkownik był w czasie wschodnioletniego (EDT) podczas filtrowania o godzinie 00:00, raport będzie zawierał wiadomości z dnia 2021-08-30 w godzinach 04:00 czasu UTC do godziny 2021-08-31 04:00 czasu UTC.

#### <a name="filter-details"></a>Szczegóły filtru

Filtry zgodności komunikacji umożliwiają filtrowanie i sortowanie komunikatów alertów w celu szybszego badania i działania naprawczego. Filtrowanie jest dostępne na kartach **Oczekujące** i **Rozwiązane** dla poszczególnych zasad. Aby zapisać filtr lub zestaw filtrów jako zapisane zapytanie filtru, co najmniej jedną wartość należy skonfigurować jako opcje filtrowania.

W poniższej tabeli przedstawiono szczegóły filtrowania:

|**Filtr**|**Szczegóły**|
|:-----|:-----|
| **Data** | Data wysłania lub odebrania wiadomości przez użytkownika w Twojej organizacji. Aby filtrować według jednego dnia, zaznacz zakres dat, który zaczyna się od dnia, dla którego chcesz uzyskać wyniki, i kończy się na następnym dniu. Jeśli na przykład chcesz filtrować wyniki dla 2020-09-20, wybierz zakres dat filtru: 2020-09-2020-21-20.|
| **Klasa pliku** | Klasa wiadomości na podstawie typu wiadomości, wiadomości *lub* *załącznika*. |
| **Ma załącznik** | Informacje o obecności załącznika w wiadomości. |
| **Klasa elementu** | Źródło wiadomości jest oparte na typie wiadomości, wiadomości e-mail, czacie zespołu Microsoft Team, kwiatmiecie itp. Aby uzyskać więcej informacji na temat typowych typów elementów i klas wiadomości, zobacz [Typy elementów i Klasy wiadomości](/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Domeny adresatów** | Domena, do której została wysłana wiadomość. Ta domena jest zwykle twoją Microsoft 365 domeną subskrypcji usługi. |
| **Adresat** | Użytkownik, do którego została wysłana wiadomość. |
| **Nadawca** | Osoba, która wysłała wiadomość. |
| **Domena nadawcy** | Domena, która wysłała wiadomość. |
| **Rozmiar** | Rozmiar wiadomości w KB. |
| **Temat/tytuł** | Temat wiadomości lub tytuł czatu. |
| **Tagi** | Tagi przypisane do wiadomości: może być *pytanie, zgodne* lub *niezgodne*.  |
| **Język** | Wykryty język tekstu w wiadomości. Wiadomości są klasyfikowane według języka większości tekstu wiadomości. Na przykład w przypadku wiadomości zawierającej tekst niemiecki i włoski, ale większość tekstu jest niemiecka, ta wiadomość jest klasyfikowana jako niemiecka (DE). Obsługiwane są następujące języki: chiński (uproszczony — ZH), angielski (EN), francuski (FR), niemiecki (DE), włoski (IT), japoński (JP), portugalski (PT) i hiszpański (ES). Aby na przykład filtrować wiadomości sklasyfikowane jako niemiecki i włoski, wprowadź wartość "DE,IT" (2-cyfrowy kod języka) w polu wyszukiwania filtru języka. Aby wyświetlić klasyfikację wykrytego języka wiadomości, zaznacz wiadomość, wybierz pozycję Wyświetl szczegóły wiadomości i przewiń do pola EmailDetectedLanguage. |
| **Eskalacji do** | Nazwa użytkownika osoby uwzględnionej w ramach akcji eskalacji wiadomości. |
| **Klasyfikatory** | Nazwa wbudowanych i niestandardowych klasyfikatorów, które dotyczą wiadomości. Oto *przykłady molestowania* kierowanego, *wulgarności*, *zagrożenia* i nie tylko.

#### <a name="to-configure-a-filter"></a>Aby skonfigurować filtr

1. Zaloguj się do [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w Twojej Microsoft 365 organizacji.

2. Na stronie Centrum zgodności platformy Microsoft 365 do tematu **Zgodność komunikacji**.

3. Wybierz **kartę Zasady** , a następnie wybierz zasady do badania i kliknij dwukrotnie, aby otworzyć **stronę** Zasady.

4. Na stronie **Zasady** wybierz kartę Oczekujące  lub Rozwiązane, aby wyświetlić elementy do filtrowania.

5. Wybierz **kontrolkę Filtry** , aby otworzyć stronę **szczegółów** Filtry.

6. Zaznacz co najmniej jedno pole wyboru, aby włączyć filtry dla tych alertów. Do wyboru są liczne filtry, takie jak *Data*, *Nadawca*, *Temat/Tytuł*, *Klasyfikatory*, *Język* i inne.

7. Jeśli chcesz zapisać filtr wybrany jako filtr domyślny, wybierz pozycję **Zapisz jako domyślny**. Jeśli chcesz użyć tego filtru jako zapisanego filtru, wybierz pozycję **Gotowe**.

8. Jeśli chcesz zapisać wybrane filtry jako zapytanie filtru, wybierz pozycję Zapisz kontrolkę zapytania  po skonfigurowaniu co najmniej jednej wartości filtru. Wprowadź nazwę zapytania filtru i wybierz pozycję **Zapisz**. Ten filtr jest dostępny tylko dla tych zasad i znajduje się na liście w sekcji  Zapisane zapytania filtru na **stronie Szczegóły** filtrów.

    ![Kontrolki szczegółów filtru zgodności komunikacji.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Używanie niemal i dokładnej analizy zduplikowanej

Zasady zgodności komunikacji automatycznie skanują i wstępnie grupują duplikaty wiadomości w pobliżu i dokładnie tak, aby nie wymagały żadnych dodatkowych kroków konfiguracji. Ten widok pozwala szybko działać na podobnych wiadomościach jeden po drugie lub w grupie, co zmniejsza obciążenie związane z badaniem wiadomości dla recenzentów. Po wykryciu duplikatów na pasku  narzędzi akcji rozwiązywania problemów są wyświetlane  kontrolki W pobliżu duplikatów i/lub Dokładne duplikaty. Ten widok nie jest dostępny, jeśli nie znaleziono niemal żadnych duplikatów lub dokładne ich duplikaty.

#### <a name="to-remediate-duplicates"></a>Aby rozwiązać problemów ze zduplikowanymi duplikatami

1. Zaloguj się do [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w Twojej Microsoft 365 organizacji.

2. Na stronie Centrum zgodności platformy Microsoft 365 do tematu **Zgodność komunikacji**.

3. Wybierz **kartę Zasady** , a następnie wybierz zasady do badania i kliknij dwukrotnie, aby otworzyć **stronę** Zasady.

4. Na stronie **Zasady** wybierz kartę Oczekujące  lub Rozwiązane, aby wyświetlić zduplikowane wiadomości.

5. Wybierz **kontrolki Near Duplicates** (Blisko duplikatów) lub **Exact Duplicates (Dokładne duplikaty** ), aby otworzyć stronę szczegółów duplikatów.

6. Zaznacz co najmniej jeden komunikat, aby kontrolki akcji rozwiązywania problemów dla tych wiadomości były wyświetlane.

7. Wybierz **pozycję Rozwiąż**, **Powiadom**, **Eskaluj** lub Pobierz, aby zastosować akcję do wybranych zduplikowanych wiadomości jako filtr domyślny.

8. Po **ukończeniu** działań zaradczych na wiadomościach wybierz pozycję Zamknij.

    ![Mechanizmy kontroli zgodności ze zgodnością.](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Alerty dotyczące rozwiązywania problemów

Niezależnie od tego, gdzie zaczną być przeglądane alerty i skonfigurowane filtrowanie, kolejnym krokiem jest podjęcia działań naprawczych alert. Na stronach Zasady lub Alerty rozpocznij rozwiązywanie alertów za  pomocą następującego przepływu **pracy.**

### <a name="step-1-examine-the-message-basics"></a>Krok 1. Badanie podstawowych czynności w wiadomości

 Czasami ze źródła lub tematu wynika, że wiadomość można natychmiast rozwiązać. Możliwe, że wiadomość jest nieodpowiednia lub niepoprawnie dopasowana do zasad i powinna zostać rozwiązana jako błędna klasyfikacja. Wybierz **kontrolkę Raport jako kontrolkę** z błędną klasyfikacją, aby udostępnić nieprawidłowo sklasyfikowaną zawartość firmie Microsoft, natychmiast rozwiąż alert i usuń go z kolejki oczekujących alertów. Z informacji o źródle lub nadawcy możesz już wiedzieć, w jaki sposób wiadomość powinna zostać przekierowyowana lub przejmowana w tych okolicznościach. Rozważ użycie kontrolek **Oznacz jako** lub **Eskaluj** w celu przypisania tagu do odpowiednich wiadomości lub wysyłania wiadomości do wyznaczonego recenzenta.

![Środki zaradcze w zakresie komunikacji.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>Krok 2. Sprawdź szczegóły wiadomości

Po przejrzeniu podstaw wiadomości należy otworzyć wiadomość, aby zbadać szczegóły i określić dalsze działania naprawcze. Wybierz wiadomość, aby wyświetlić pełne informacje nagłówka i treści wiadomości. Dostępnych jest kilka różnych opcji i widoków, które ułatwiają podjęcie odpowiednich działań:

- **Załączniki**: Ta opcja umożliwia badanie nowoczesnych załączników, które są zgodne z warunkami zasad. Zawartość nowoczesnych załączników jest wyodrębniona jako tekst i można jej wyświetlać na pulpicie nawigacyjnym Alerty oczekujące dla zasad. Aby uzyskać więcej informacji, zobacz [Informacje dotyczące funkcji zgodności komunikacji](/microsoft-365/compliance/communication-compliance-channels).
- **Źródło**: ten widok to standardowy widok wiadomości często spotykany na większości platform do obsługi wiadomości internetowych. Informacje nagłówka są formatowane w normalnym stylu, a treść wiadomości obsługujembeddowane pliki graficzne i tekst zawijany wyrazem. Jeśli dla zasad jest włączone optyczne rozpoznawanie znaków [(OCR](communication-compliance-policies.md#optical-character-recognition-ocr) ), w tym widoku obrazy zawierające drukowany lub pisany ręcznie tekst, które są zgodne z zasadami, są przeglądane jako element podrzędny skojarzonej wiadomości.
- **Zwykły tekst**: W widoku tekstu wyświetlany jest tylko tekstowy widok z wierszami wiadomości, a także wyróżnienia słów kluczowych w wiadomościach i załącznikach w przypadku terminów dotyczących typów informacji poufnych lub słów kluczowych zgodnych ze skojarzonymi zasadami zgodności komunikacji. Wyróżnianie słów kluczowych może ułatwić szybkie szybkie skanowanie długich wiadomości i załączników w poszukiwaniu interesującego obszaru. W niektórych przypadkach wyróżniony tekst może być tylko w załącznikach do wiadomości spełniających warunki zasad. Wyróżnianie słów kluczowych nie jest obsługiwane w przypadku terminów zidentyfikowanych przez wbudowane klasyfikatory przypisane do zasad. Osadzone pliki nie są wyświetlane, a numerowanie wiersza w tym widoku jest pomocne w przypadku odwoływania się do istotnych informacji między wieloma recenzentami.
- **Konwersacja (wersja zapoznawcza)**: Dostępny w Microsoft Teams wiadomościach czatu, w tym widoku jest wyświetlanych maksymalnie pięć wiadomości przed i po komunikacie alertu, aby ułatwić recenzentom przeglądanie aktywności w kontekście konwersacji. Ułatwia to recenzentom szybkie ocenianie wiadomości i podejmowanie bardziej świadomych decyzji dotyczących rozwiązywania problemów z wiadomościami. Wyświetlane są w czasie rzeczywistym dodatki do konwersacji, w tym wszystkie obrazy w tekście, emoji i naklejki dostępne w Teams. Obraz lub plik tekstowy załączników do wiadomości nie są wyświetlane. Powiadomienia są automatycznie wyświetlane w przypadku edytowanych wiadomości lub wiadomości usuniętych z okna konwersacji. Gdy wiadomość zostanie rozpoznana, skojarzone z nią wiadomości konwersacji nie są zachowywane wraz z nią. Wiadomości konwersacji są dostępne w ciągu 60 dni od zidentyfikowania komunikatu alertu.
- **Historia użytkowników: W** widoku historii użytkowników są wyświetlane wszystkie inne alerty wygenerowane przez wszelkie zasady zgodności komunikacji dla użytkownika wysyłającego wiadomość.
- **Powiadomienie wykryte w deseniu**: Wiele napastnych i nękających akcji z czasem i obejmuje powtarzające się wystąpienia tego samego zachowania przez użytkownika. Powiadomienie *wykryte deseń* jest wyświetlane w szczegółach alertu i zwraca uwagę na alert. Wykrywanie wzorców jest wykrywania wzorców na podstawie zasad i ocenia zachowanie z ostatnich 30 dni, gdy nadawca wysyła do tego samego adresata co najmniej dwie wiadomości. Wschowa i recenzentzy mogą używać tego powiadomienia do identyfikowania powtarzających się zachowań w celu oceny alertu w razie potrzeby.
- **Tłumaczenie**: Ten widok automatycznie konwertuje tekst wiadomości alertu na język skonfigurowany w ustawieniu Język  wyświetlany w subskrypcji usługi Microsoft 365 dla każdego recenzenta. Widok *tłumaczenia* ułatwia rozszerzenie obsługi badania w organizacjach z użytkownikami wielojęzycznymi i eliminuje konieczność tworzenia dodatkowych usług tłumaczenia poza procesem sprawdzania zgodności komunikacji. Za pomocą usług tłumaczenia firmy Microsoft  można w razie potrzeby włączać i wyłączać widok tłumaczenia oraz korzystać z wielu języków. Aby uzyskać pełną listę obsługiwanych języków, zobacz Microsoft Translator [języki](https://www.microsoft.com/translator/business/languages/). Języki wymienione na *liście Translator są* obsługiwane w *widoku* Tłumaczenie.

### <a name="step-3-decide-on-a-remediation-action"></a>Krok 3. Podjęcie decyzji o podjęciu działania naprawczego

Po przejrzeniu szczegółów komunikatu dla alertu możesz wybrać kilka działań naprawczych:

- **Rozwiąż**: Wybranie **kontrolki Rozwiąż** natychmiast usuwa wiadomość z kolejki **Alerty** oczekujące i nie można podjąć żadnych dalszych działań dotyczących wiadomości. Wybierając pozycję **Rozwiąż**, zasadniczo zamknięto alert bez dalszej klasyfikacji. Wszystkie rozpoznane wiadomości są wyświetlane na karcie **Rozpoznane** .
- **Zgłoś jako nieprawidłowo sklasyfikowane**: Zawsze możesz rozpoznać wiadomość jako błędną klasyfikację w dowolnym momencie przepływu pracy recenzji wiadomości. Błędna klasyfikacja oznacza, że alert nie może akcji lub że alert został nieprawidłowo wygenerowany przez proces alertowania i wszystkie przeszkolne klasyfikatory. Podczas rozpoznawania elementu jako nieprawidłowo sklasyfikowanej wysyła do firmy Microsoft zawartość wiadomości, załączniki i temat wiadomości (w tym metadane) w celu usprawnienia przeszkolinia klasyfikatorów. Dane wysyłane do firmy Microsoft nie zawierają informacji, które mogą być identyfikowane lub używane do identyfikowania użytkowników w organizacji. Nie można w tej wiadomości podjąć dalszych działań, a wszystkie błędnie sklasyfikowane wiadomości zostaną wyświetlone na **karcie Rozpoznane** .
- **Power Automate (wersja zapoznawcza)**: Użyj przepływu Power Automate, aby zautomatyzować zadania przetwarzania dla wiadomości alertu. Domyślnie zgodność komunikacji obejmuje menedżera powiadomień, gdy użytkownik ma szablon przepływu *alertu* zgodności komunikacji, za pomocą których recenzentzy mogą zautomatyzować proces powiadomień dla użytkowników za pomocą alertów o wiadomościach. Aby uzyskać więcej informacji na temat tworzenia przepływów Power Automate przepływów komunikacji i zarządzania nimi, zobacz sekcję Krok **5. Power Automate przepływów w** tym artykule.
- **Oznacz jako**: Oznacz wiadomość jako  zgodną *,* niedowiązywową lub jako podszytą jako podszytą w odniesieniu do zasad i standardów organizacji. Dodawanie tagów i komentarzy tagowania ułatwia mikrofiltrowanie alertów zasad dotyczących eskalacji lub w ramach innych wewnętrznych procesów przeglądu. Po zakończeniu tagowania możesz także rozpoznać wiadomość, aby przenieść ją poza kolejkę oczekujących recenzji.
- **Powiadom**: Możesz użyć kontrolki **Powiadom** , aby przypisać do alertu niestandardowy szablon powiadomienia oraz wysłać do użytkownika powiadomienie z ostrzeżeniem. Wybierz odpowiedni szablon powiadomienia skonfigurowany w obszarze Ustawienia zgodności  komunikacji i wybierz pozycję Wyślij,  aby wysłać przypomnienie do użytkownika, który wysłał wiadomość, i aby rozwiązać ten problem.
- **Eskalacji**: Za pomocą kontrolki **Eskaluj** możesz wybrać inne osoby w organizacji do przejrzenia wiadomości. Wybierz z listy recenzentów skonfigurowanych w zasadach zgodności komunikacji, aby wysłać wiadomość e-mail z powiadomieniem z prośbą o dodatkową recenzję alertu o wiadomości. Wybrany recenzent może użyć linku w powiadomieniu e-mail, aby przejść bezpośrednio do elementów, które zostały do nich eskalacji w celu przejrzenia.
- **Eskaluj do badania**:  Za pomocą kontrolki Eskaluj do badania możesz utworzyć nową Advanced eDiscovery [przypadku](overview-ediscovery-20.md) jednej lub wielu wiadomości. Po wypadku do użytkownika, który wysłał wiadomość pasującą do zasad, zostanie automatycznie przypisana nazwa i uwagi do nowej sprawy. Do zarządzania sprawą nie są potrzebne żadne dodatkowe uprawnienia. Utworzenie sprawy nie rozwiąże problemu ani nie utworzy nowego tagu dla wiadomości. Podczas tworzenia sprawy zaradczej można wybrać łącznie 100 wiadomości Advanced eDiscovery działania naprawczego. Obsługiwane są wiadomości ze wszystkich kanałów komunikacji monitorowanych przez zgodność komunikacji. Na przykład możesz wybrać 50 Microsoft Teams czatów, 25 Exchange Online e-mail i 25 Yammer wiadomości, gdy otworzysz nową Advanced eDiscovery przypadku dla użytkownika.
- **Usuwanie wiadomości z Teams**: Używając kontrolki Usuń wiadomość w aplikacji **Teams**, możesz blokować nieodpowiednie wiadomości i zawartość zidentyfikowane w alertach z kanałów Microsoft Teams oraz czatów grupowych i 1:1. Usunięte wiadomości i zawartość są zamieniane na poradę o zasadach z wyjaśnieniem, że wiadomość jest zablokowana, oraz zasady dotyczące usuwania wiadomości z widoku. Adresaci są dostępni do linku w poradach dotyczących zasad, aby dowiedzieć się więcej na temat obowiązujących zasad i procesu rezydowania. Nadawca otrzymuje poradę dotyczącą zasad dotyczącą zablokowanej wiadomości i zawartości, ale może przejrzeć szczegóły zablokowanej wiadomości i zawartości w kontekście usuwania.

    ![Usuwanie wiadomości z Microsoft Teams.](../media/communication-compliance-remove-teams-message.png)

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>Krok 4. Ustalanie, czy szczegóły wiadomości powinny być archiwizowane poza zgodnością z komunikacją

Szczegóły wiadomości można wyeksportować lub pobrać, jeśli konieczne jest ich zarchiwizowanie w osobnym rozwiązaniu do przechowywania. Wybranie **kontrolki Pobierz** powoduje automatyczne dodanie zaznaczonych wiadomości do .ZIP pliku, który można zapisać w pamięci poza Microsoft 365.

### <a name="step-5-consider-power-automate-flows"></a>Krok 5. Rozważenie Power Automate przepływów

[Microsoft Power Automate](/power-automate/getting-started) to usługa przepływu pracy, która automatyzuje akcje między aplikacjami i usługami. Korzystając z przepływów z szablonów lub utworzonych ręcznie, można zautomatyzować typowe zadania skojarzone z tymi aplikacjami i usługami. Po włączeniu przepływów Power Automate na celu zapewnienie zgodności komunikacji można zautomatyzować ważne zadania dla alertów i użytkowników. Możesz skonfigurować przepływy Power Automate do menedżerów, gdy użytkownicy mają alerty zgodności komunikacji i inne aplikacje.

Klienci z Microsoft 365 subskrypcjami, które zawierają zgodność z komunikacją, nie potrzebują dodatkowych licencji Power Automate, aby użyć zalecanego domyślnego szablonu zgodności Power Automate zgodności komunikacji. Domyślny szablon można dostosować tak, aby obsługiował Twoją organizację, i obejmować podstawowe scenariusze zgodności komunikacji. Jeśli zdecydujesz się na korzystanie z funkcji premium Power Automate w tych szablonach, utwórz szablon niestandardowy przy użyciu łącznika zgodności usługi Microsoft 365 lub użyj szablonów programu Power Automate dla innych obszarów zgodności w programie Microsoft 365, może być konieczne użycie dodatkowych Power Automate licencji.

> [!IMPORTANT]
> Czy podczas testowania przepływów testowania licencji jest wyświetlany Power Automate weryfikacji licencji? Być może Twoja organizacja jeszcze nie otrzymała aktualizacji usługi dla tej funkcji w wersji Preview. Obecnie wdrażane są aktualizacje i do 30 października 2020 r. wszystkie organizacje z subskrypcjami usługi Microsoft 365, które zawierają zgodność z przepisami komunikacji, powinny mieć obsługę licencji dla przepływów utworzonych na podstawie zalecanych szablonów programu Power Automate.

![Zgodność komunikacji Power Automate.](../media/communication-compliance-power-automate.png)

Następujący szablon Power Automate do klientów w celu obsługi automatyzacji procesu dla alertów zgodności komunikacji:

- **Powiadamianie menedżera, gdy użytkownik ma alert** zgodności komunikacji: W niektórych organizacjach może być konieczne natychmiastowe powiadomienie kierownictwa, gdy użytkownik ma alert zgodności komunikacji. Po skonfigurowaniu i wybraniu tego przepływu menedżer sprawy wysyła do użytkownika wiadomość e-mail z następującymi informacjami o wszystkich alertach:
  - Zasady obowiązujące dla alertu
  - Data/godzina alertu
  - Poziom ważności alertu

#### <a name="create-a-power-automate-flow"></a>Tworzenie przepływu Power Automate danych

Aby utworzyć przepływ Power Automate na podstawie zalecanego szablonu domyślnego, użyjesz opcji Zarządzaj przepływami Power Automate  z kontrolki Automatyzuj podczas pracy bezpośrednio w  alercie. Aby utworzyć przepływ Power Automate przepływów zgodności **Power Automate, musisz** być członkiem co najmniej jednej grupy ról zgodności komunikacji.

Wykonaj poniższe czynności, aby utworzyć przepływ Power Automate na podstawie szablonu domyślnego:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) **do zasad** >  zgodności komunikacji i wybierz zasady z alertem, który chcesz przejrzeć.
2. W zasadach wybierz kartę **Oczekujące** , a następnie wybierz oczekujący alert.
3. Wybierz **Power Automate** z menu akcji alertu.
4. Na **Power Automate strony** wybierz szablon domyślny **z sekcji Szablony** zgodności komunikacji.
5. Przepływ wyświetli listę osadzonych połączeń potrzebnych do przepływu i wyświetli je, jeśli stan połączenia jest dostępny. W razie potrzeby zaktualizuj wszystkie połączenia, które nie są wyświetlane jako dostępne. Wybierz **pozycję Kontynuuj**.
6. Domyślnie zalecane przepływy są wstępnie skonfigurowane z zalecanymi polami zgodności komunikacji i Microsoft 365 danych usługi wymaganymi do wykonania przydzielonego zadania w przepływie. W razie potrzeby dostosuj składniki przepływu, używając kontrolki Pokaż zaawansowane opcje i konfigurując dostępne właściwości składnika przepływu.
7. W razie potrzeby dodaj kolejne kroki do przepływu, wybierając **przycisk Nowy** krok. W większości przypadków ta zmiana nie powinna być potrzebna w przypadku zalecanych szablonów domyślnych.
8. Wybierz **pozycję Zapisz wersje** robocze, aby zapisać przepływ do dalszej konfiguracji później, lub pozycję Zapisz, aby ukończyć konfigurację przepływu.
9. Wybierz **pozycję Zamknij**, aby wrócić do Power Automate przepływu pracy. Nowy szablon zostanie wymieniony jako przepływ na karcie **Moje** przepływy i automatycznie dostępny z kontrolki Power Automate dla użytkownika, który utworzył przepływ podczas pracy z alertami zgodności komunikacji.

#### <a name="share-a-power-automate-flow"></a>Udostępnianie przepływu Power Automate przepływu pracy

Domyślnie przepływy Power Automate utworzone przez użytkownika są dostępne tylko dla tego użytkownika. Aby inni użytkownicy zgodności komunikacji mieli dostęp do przepływu i z niego korzystali, jego przepływ musi zostać udostępniony przez autora przepływu. Aby udostępnić przepływ, użyjesz kontrolki sterowania **Power Automate podczas pracy** bezpośrednio w alercie.

Aby udostępnić przepływ Power Automate, musisz być członkiem co najmniej jednej grupy ról zgodności komunikacji.
Wykonaj następujące czynności, aby udostępnić przepływ Power Automate przepływ pracy:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) **do zasad** >  zgodności komunikacji i wybierz zasady z alertem, który chcesz przejrzeć.
2. W zasadach wybierz kartę **Oczekujące** , a następnie wybierz oczekujący alert.
3. Wybierz **Power Automate** z menu akcji alertu.
4. Na stronie **Power Automate** wybierz **kartę Moje** przepływy lub **Przepływy** zespołu.
5. Wybierz przepływ, który chcesz udostępnić, a następnie wybierz **pozycję Udostępnij** z menu opcji przepływu.
6. Na stronie udostępniania przepływu wprowadź nazwę użytkownika lub grupy, którą chcesz dodać jako właściciela przepływu.
7. W **oknie dialogowym Używane** połączenie wybierz przycisk **OK** , aby potwierdzić, że dodany użytkownik lub grupa będzie mieć pełny dostęp do przepływu.

#### <a name="edit-a-power-automate-flow"></a>Edytowanie przepływu Power Automate danych

Jeśli musisz edytować przepływ, będziesz używać kontrolki sterowania przepływem Power Automate  podczas pracy bezpośrednio w alercie. Aby edytować przepływ Power Automate, musisz być członkiem co najmniej jednej grupy ról zgodności komunikacji.

Aby edytować przepływ pracy, wykonaj Power Automate czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) **do zasad** >  zgodności komunikacji i wybierz zasady z alertem, który chcesz przejrzeć.
2. W zasadach wybierz kartę **Oczekujące** , a następnie wybierz oczekujący alert.
3. Wybierz **Power Automate** z menu akcji alertu.
4. Na stronie **przepływów Power Automate** wybierz przepływ do edycji. Wybierz **pozycję Edytuj** w menu sterowania przepływem.
5. Wybierz **wielokropek** >  **Ustawienia** aby  >  zmienić ustawienie składnika przepływu lub wielokropekDelete, aby usunąć składnik przepływu.
6. Wybierz **pozycję Zapisz** , a następnie zamknij **,** aby zakończyć edytowanie przepływu.

#### <a name="delete-a-power-automate-flow"></a>Usuwanie przepływu Power Automate danych

Jeśli musisz usunąć przepływ, użyjesz kontrolki przepływu Power Automate podczas  pracy bezpośrednio w alercie. Aby usunąć przepływ Power Automate, musisz być członkiem co najmniej jednej grupy ról zgodności komunikacji.

Aby usunąć przepływ danych, wykonaj Power Automate czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) **do zasad** >  zgodności komunikacji i wybierz zasady z alertem, który chcesz przejrzeć.
2. W zasadach wybierz kartę **Oczekujące** , a następnie wybierz oczekujący alert.
3. Wybierz **Power Automate** z menu akcji alertu.
4. Na stronie **Power Automate przepływów** wybierz przepływ, który chcesz usunąć. Wybierz **polecenie Usuń** z menu sterowania przepływem.
5. W oknie dialogowym potwierdzenia usunięcia wybierz pozycję **Usuń** , aby usunąć przepływ, lub pozycję **Anuluj** , aby zamknąć akcję usunięcia.

### <a name="step-6-consider-creating-notice-templates"></a>Krok 6. Rozważ utworzenie szablonów z powiadomieniami

Jeśli chcesz wysłać użytkownikom powiadomienia z przypomnieniem e-mail o dopasowaniach zasad w ramach procesu rozwiązywania problemów, możesz utworzyć szablony z powiadomieniami. Powiadomienia można wysyłać tylko na adres e-mail użytkownika skojarzony z dopasowaniem zasad, które wygenerowali określony alert na temat rozwiązywania problemów. Po wybraniu szablonu powiadomienia do zastosowania w ramach przepływu pracy rozwiązywania problemów naruszenia zasad możesz zaakceptować wartości pól zdefiniowane w tym szablonie lub zastąpić pola w razie potrzeby.

Szablony powiadomienia to niestandardowe szablony wiadomości e-mail, w których można zdefiniować następujące pola wiadomości w obszarze **Ustawienia zgodności komunikacji** :

|**Pole**|**Wymagane**| **Szczegóły** |
|:-----|:-----|:-----|
|**Nazwa szablonu** | Tak | Przyjazna nazwa szablonu powiadomienia, który będzie wybierany w przepływie pracy powiadamiania podczas rozwiązywania problemów, obsługuje znaki tekstowe. |
| **Adres nadawcy** | Tak | Adres jednego lub większej liczby użytkowników albo grup, które wysyłają wiadomość do użytkownika z dopasowaniem zasad wybranym z usługi Active Directory dla Twojej subskrypcji. |
| **Adresy DW i UDW** | Nie | Opcjonalnie użytkownicy lub grupy, którzy mają zostać powiadomieni o dopasowanych zasadach, wybrani z usługi Active Directory dla Twojej subskrypcji. |
| **Temat** | Tak | Informacje wyświetlane w wierszu tematu wiadomości obsługują znaki tekstowe. |
| **Treść wiadomości** | Tak | Informacje wyświetlane w treści wiadomości obsługują tekst lub wartości HTML. |

### <a name="html-for-notices"></a>Html na uwagi

Jeśli chcesz utworzyć więcej niż zwykłą wiadomość e-mail opartą na tekście na powiadomieniach, możesz utworzyć bardziej szczegółową wiadomość, używając kodu HTML w polu treści wiadomości szablonu powiadomienia. W poniższym przykładzie przedstawiono format treści wiadomości dla podstawowego szablonu wiadomości e-mail opartego na języku HTML:

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

> [!NOTE]
> Implementacja atrybutu href HTML w szablonach powiadomień o zgodności komunikacji obsługuje obecnie tylko pojedynczy cudzysłów zamiast podwójnego cudzysłowu dla odwołań do adresów URL.

## <a name="unresolve-messages-preview"></a>Nierozpoznanie wiadomości (podgląd)

Gdy wiadomości są rozwiązywane, są one usuwane z widoku  karty Oczekujące i wyświetlane w **widoku karty Rozpoznane**. W widoku Rozpoznane wiadomości nie są dostępne akcje badania i *rozwiązywania* problemów. Mogą jednak wystąpić przypadki, w których trzeba podjąć dodatkowe działania dotyczące wiadomości, która została omyłnie rozwiązana lub która wymaga dalszego badania po rozpoznaniu początkowym. Można użyć funkcji nierozpoznania polecenia i przenieść jedną lub więcej wiadomości z widoku *Rozpoznano z powrotem* do *widoku Oczekujące* .

Aby nierozpoznać wiadomości, wykonaj następujące czynności:

1. Zaloguj [się do Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu po Microsoft 365 świadczeń użytkownika przypisanego do grup ról Analityk zgodności  komunikacji lub Zgodność komunikacji  w organizacji.
2. Na stronie Centrum zgodności platformy Microsoft 365 do tematu **Zgodność komunikacji**.
3. Wybierz **kartę Zasady** , a następnie wybierz zasady zawierające rozstrzygnięty komunikat alertu. Kliknij dwukrotnie, aby otworzyć **stronę** Zasady.
4. Na **stronie Zasady** wybierz kartę **Rozpoznane** .
5. Na karcie **Rozpoznane** zaznacz jedną lub więcej wiadomości, aby wrócić do listy *Oczekujące*.
6. Na pasku poleceń wybierz pozycję **Nierozpoznanie**.
7. W **okienku Nierozpoznanie** elementu dodaj wszelkie komentarze mające zastosowanie do akcji nierozwiązywana  i wybierz pozycję Zapisz, aby przenieść element z powrotem do pozycji *Oczekujące*.
8. Wybierz **kartę Oczekujące** , aby sprawdzić, czy zaznaczone elementy są wyświetlane.