---
title: Praca z akcjami ulepszania w menedżerze zgodności Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak implementować i testować mechanizmy kontroli, pracując z akcjami ulepszania w programie Microsoft Purview Compliance Manager. Przypisywanie pracy, przechowywanie dokumentacji i eksportowanie raportów.
ms.openlocfilehash: 9dca4f3a742b82a2cf119ceb40b04241d1b5177f
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621784"
---
# <a name="working-with-improvement-actions-in-compliance-manager"></a>Praca z akcjami poprawy w Menedżerze zgodności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**W tym artykule:** W tym artykule wyjaśniono, jak **zarządzać przepływem pracy zgodności** za pomocą akcji poprawy. Dowiedz się, jak **przypisywać akcje poprawy** dotyczące implementacji i testowania, **zarządzać aktualizacjami** i eksportować **raporty**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Zarządzanie przepływami pracy zgodności za pomocą akcji poprawy

Akcje ulepszania scentralizują działania związane ze zgodnością. Każda akcja poprawy zapewnia szczegółowe wskazówki dotyczące implementacji, które pomogą Ci dostosować się do przepisów i standardów ochrony danych. Akcje mogą być przypisywane do użytkowników w organizacji w celu wykonywania zadań implementacji i testowania. W ramach akcji można również przechowywać dokumentację, notatki i aktualizacje stanu rekordów.

Wszystkie akcje poprawy są wyświetlane na stronie akcji poprawy. Dowiedz się więcej na temat [wyświetlania akcji poprawy](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Strona szczegółów akcji ulepszania

Każda akcja poprawy zawiera stronę szczegółów przedstawiającą jej bieżący stan, powiązane standardy i wymagania prawne oraz zalecane wskazówki dotyczące implementacji. [Akcje techniczne](compliance-score-calculation.md#technical-and-non-technical-actions) obejmują link **Uruchom teraz** , który prowadzi do odpowiedniego rozwiązania do implementacji. Dokumentację implementacji i testowania można dołączyć bezpośrednio do strony szczegółów akcji poprawy.

Aby wyświetlić stronę szczegółów akcji poprawy:

1. Przejdź do strony akcji poprawy.
2. Wybierz wiersz zamierzonej akcji poprawy, która otwiera jego stronę szczegółów.

Możesz łatwo wyświetlić następną lub poprzednią akcję poprawy na liście, wybierając strzałkę w górę lub w dół w prawym górnym rogu ekranu. Jeśli lista została przefiltrowana na stronie akcji poprawy, przejście w górę lub w dół spowoduje przejście do następnego elementu na tej filtrowanej liście.

> [!TIP]
> Dowiedz się więcej o różnych [typach akcji poprawy oraz o tym, jak punkty są przyznawane](compliance-score-calculation.md#action-types-and-points) i uwzględniane w wyniku zgodności.

## <a name="assign-improvement-actions"></a>Przypisywanie akcji poprawy

Aby rozpocząć pracę nad implementacją akcji poprawy, możesz wykonać pracę samodzielnie lub przypisać ją do innego użytkownika. Przypisaną osobą może być:

- Właściciel zasad biznesowych
- Implementator IT
- Inny pracownik odpowiedzialny za wykonanie zadania

Po zidentyfikowaniu odpowiedniego przypisanego użytkownika upewnij się, że ma on wystarczającą [rolę Menedżera zgodności](compliance-manager-setup.md#set-user-permissions-and-assign-roles) , aby wykonać pracę. Następnie wykonaj poniższe kroki, aby przypisać akcję poprawy:

1. Na stronie szczegółów akcji poprawy wybierz pozycję **Przypisz akcję** po lewej stronie ekranu.

2. Okienko wysuwane **Przypisywanie do użytkownika** zawiera listę sugerowanych **osób** użytkowników. Możesz wybrać użytkownika z listy lub wpisać adres e-mail osoby, do której chcesz go przypisać.

3. Wybierz pozycję **Przypisz**. Przypisany użytkownik otrzyma wiadomość e-mail z wyjaśnieniem, że przypisano do niego akcję poprawy, z bezpośrednim linkiem do akcji poprawy.

> [!NOTE]
> Klienci Community (GCC) High i Department of Defense (DoD) nie otrzymają wiadomości e-mail po przypisaniu do nich akcji poprawy.

Przypisany użytkownik może następnie wykonać zalecane akcje.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Przypisywanie wielu akcji poprawy do jednego użytkownika

Do jednego użytkownika można przypisać wiele akcji poprawy, wykonując następujące kroki:

1. Przejdź do strony Akcje poprawy.
2. Wybierz obszar po lewej stronie nazwy akcji poprawy. Zostanie wyświetlona ikona sprawdzania okrągłego wskazująca, że wybrano tę akcję. Sprawdź wszystkie akcje, które chcesz przypisać.
3. Wybierz link **Przypisz do użytkownika** w górnej części tabeli akcji poprawy.
4. Zostanie wyświetlone okno podręczne. W polu **Przypisz do** zacznij wpisywać nazwę osoby, do której chcesz przypisać akcje. Możesz również wybrać z listy sugerowanych osób.
5. Po wypełnieniu pola **Przypisz do** nazwą przypisanego wybierz pozycję **Przypisz**.
6. Następnie zobaczysz stronę Akcji poprawy z nowym przypisanym elementem wymienionym dla przypisanych akcji.

## <a name="change-implementation-details"></a>Zmienianie szczegółów implementacji

Możesz zarejestrować stan i datę implementacji dla każdej akcji poprawy oraz dodać notatki do wewnętrznego odwołania. Te pola mogą być edytowane przez dowolnego użytkownika z uprawnieniami do edycji, a nie tylko przez przypisaną osobę.

Aby edytować stan akcji poprawy, wybierz pozycję **Edytuj szczegóły implementacji** na stronie szczegółów. Poniżej przedstawiono dostępne pola i opcje stanu:

- **Stan implementacji**
  - **Nie zaimplementowane**: akcja nie została jeszcze zaimplementowana
  - **Częściowo zaimplementowane**: w przypadku automatycznie testowanych akcji akcja jest częściowo implementowana (ani nie przechodzi, ani nie kończy się niepowodzeniem) i otrzymuje wynik częściowy
  - **Zaimplementowane**: zaimplementowana akcja
  - **Alternatywna implementacja**: wybierz tę opcję, jeśli używasz innych narzędzi innych firm lub podjąłeś inne działania, które nie zostały uwzględnione w zaleceniach firmy Microsoft
  - **Planowane**: planowane jest wykonanie akcji
  - **Poza zakresem**: akcja nie jest istotna dla Twojej organizacji i nie przyczynia się do oceny
- **Data implementacji**: dostępna do wybrania, kiedy stan implementacji jest "zaimplementowany" lub "implementacja alternatywna"
- **Uwagi dotyczące implementacji**: pole tekstowe do notatek dotyczących implementacji.

W polach notatek nie ma limitu znaków. Zalecamy przechowywanie krótkich notatek, aby można było je łatwo wyświetlać i edytować na stronie szczegółów akcji poprawy.

Typowe akcje synchronizują się między grupami. Gdy dwie różne oceny w tej samej grupie współużytkują akcje poprawy, które są zarządzane przez Ciebie, wszelkie aktualizacje dotyczące szczegółów lub stanu implementacji akcji zostaną automatycznie zsynchronizowane z tą samą akcją w każdej innej ocenie w grupie. Ta synchronizacja umożliwia zaimplementowanie jednej akcji poprawy i spełnienie kilku wymagań w wielu przepisach.

## <a name="change-test-status"></a>Zmienianie stanu testu

W sekcji **Testowanie** możesz wyświetlić stan testowania akcji poprawy, datę testowania i wszelkie uwagi. Użytkownik z uprawnieniami do edycji może wybrać pozycję  **Edytuj szczegóły testowania** , aby edytować zawartość na karcie **Testowanie** .

#### <a name="testing-status-fields"></a>Pola stanu testowania

**Stan testu**
 
Stan testu można edytować, gdy stan implementacji akcji poprawy jest "zaimplementowany" lub "implementacja alternatywna".

Stan testu dla [ręcznie przetestowanych akcji](#manual-testing-source):
  - **Brak**: nie rozpoczęto żadnej pracy nad akcją
  - **Nie oceniono**: działanie nie zostało przetestowane
  - **Przekazano**: implementacja została zweryfikowana przez asesora
  - **Niepowodzenie niskiego ryzyka**: testowanie nie powiodło się, niskie ryzyko
  - **Średnie ryzyko niepowodzenia**: testowanie nie powiodło się, średnie ryzyko
  - **Niepowodzenie wysokiego ryzyka**: testowanie nie powiodło się, wysokie ryzyko
  - **Poza zakresem**: akcja jest poza zakresem oceny i nie przyczynia się do oceny
  - **W toku**: testowanie w toku
  - **Skorygowano**: tbd

[Automatycznie przetestowane akcje](#automatic-testing-source) mogą również pokazywać jeden z następujących stanów w kolumnie **Stan testu** na stronie **Akcje poprawy** :
   - **Do wykrycia**: oczekiwanie na sygnały wskazujące stan testu
  - **Nie można wykryć**: nie można wykryć stanu testu; zostaną ponownie automatycznie sprawdzone
  - **Częściowo przetestowano**: akcja została częściowo przetestowana;  ani przechodzi, ani nie kończy się niepowodzeniem

> [!NOTE]
> Nie można edytować ręcznie informacji o stanie testu i testach dla automatycznie testowanych akcji poprawy. Menedżer zgodności aktualizuje te pola.

**Data testu**

Przełącz się przez wyskakujące okienko kalendarza, aby wybrać datę testowania.

**Uwagi dotyczące testowania** i **dodatkowe uwagi**

Wprowadź notatki dla własnego wewnętrznego odwołania w tych polach tekstu bezpłatnego.

**Historia testowania**

Historia testowania zawiera pobrany raport wszystkich zmian stanu testu dla akcji poprawy.

#### <a name="exporting-testing-history"></a>Eksportowanie historii testowania
Możesz wyeksportować raport, który wyświetli historię wszystkich zmian stanu testu dla akcji poprawy. Te raporty są szczególnie przydatne do monitorowania postępu [akcji, które są automatycznie testowane](#automatic-testing-source), ponieważ takie akcje są regularnie lub często aktualizowane na podstawie danych dzierżawy.

Na stronie szczegółów akcji poprawy wybierz kartę **Testowanie** . W obszarze **Historia testowania** wybierz przycisk **Eksportuj historię testowania** . Raport zostanie pobrany jako plik Excel.

## <a name="update-testing-source"></a>Aktualizowanie źródła testowania

Menedżer zgodności udostępnia opcje testowania akcji poprawy. W sekcji **Przegląd** każdej akcji poprawy obszar **Źródło testowania** zawiera menu rozwijane, z którego można wybrać sposób testowania akcji: **Ręczna**, **Automatyczna** i **Nadrzędna**. Dowiedz się więcej o każdej metodzie testowania poniżej.

#### <a name="manual-testing-source"></a>Źródło testowania ręcznego
Akcje poprawy ustawione na potrzeby testowania ręcznego to akcje, które można ręcznie przetestować i zaimplementować. Należy ustawić niezbędne stany implementacji i stanu testu oraz przekazać wszystkie pliki dowodów na karcie **Dokumenty** . W przypadku niektórych akcji jest to jedyna dostępna metoda testowania akcji poprawy.

#### <a name="automatic-testing-source"></a>Źródło automatycznego testowania
Jeśli akcja implementacji kwalifikuje się do automatycznego testowania przez Menedżera zgodności, zobaczysz opcję **Automatyczne** dla źródła testowania. Menedżer zgodności wykrywa sygnały z innych rozwiązań zgodności skonfigurowanych w środowisku Microsoft 365, a także wszelkie uzupełniające akcje monitorowane przez firmę Microsoft Secure Score. Pole **Logika testowania** na karcie **Testowanie** pokaże, jakiego rodzaju zasady lub konfiguracja są wymagane w innym rozwiązaniu, aby akcja przekazywała i zdobywała punkty w kierunku oceny zgodności.

Gdy sygnały wskazują, że akcja poprawy została pomyślnie zaimplementowana, automatycznie otrzymasz punkty kwalifikujące się do tej akcji, co będzie uwzględniać wyniki dla wszelkich powiązanych kontroli i ocen. Dowiedz się więcej o tym, jak [ciągła ocena wpływa na wynik zgodności](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

 Automatyczne testowanie jest domyślnie włączone dla wszystkich kwalifikujących się akcji poprawy. Możesz dostosować te ustawienia, aby automatycznie testować tylko niektóre akcje poprawy, lub wyłączyć automatyczne testowanie dla wszystkich akcji. Dowiedz się więcej o tym, jak działa testowanie automatyczne i jak dostosować ustawienia, zobacz [Konfigurowanie testowania automatycznego](compliance-manager-setup.md#manage-automated-testing-settings).

#### <a name="parent-testing-source"></a>Nadrzędne źródło testowania

Po wybraniu pozycji **Nadrzędny** jako źródła testowania dla akcji poprawy wybierz kolejną akcję, z którą zostanie połączona twoja akcja. Twoja akcja staje się "elementem podrzędnym" akcji wyznaczonej jako "nadrzędna". Gdy wyznaczysz obiekt nadrzędny do akcji poprawy, ta akcja będzie nieodłącznie związana z implementacją i testowaniem szczegółów akcji nadrzędnej. Za każdym razem, gdy stan akcji nadrzędnej zmieni się, stan dziecka odziedziczy te zmiany. Akcja podrzędna będzie również akceptować wszystkie **dowody** na karcie Dokumenty należące do akcji nadrzędnej, co może zastąpić wszystkie dane, które wcześniej istniały w **dokumentach** akcji podrzędnej.

> [!NOTE]
> Posiadanie źródła testowego **elementu nadrzędnego** nie musi oznaczać, że akcja jest automatycznie testowana przez Menedżera zgodności. Jeśli na przykład źródło testowania akcji nadrzędnej jest **ręczne**, akcja podrzędna będzie podejmować stan akcji nadrzędnej, która jest ręcznym testem i implementacją organizacji.

Aby skonfigurować nadrzędne źródło testowania, wykonaj poniższe kroki:

- Na stronie szczegółów akcji poprawy znajdź sekcję **Przegląd** .
- W nagłówku **Źródła testowania** wybierz pozycję **Nadrzędny** z menu rozwijanego.
- Wybierz pozycję **Przypisz element nadrzędny**.
- W okienku wysuwowym **Przypisywanie akcji poprawy nadrzędnej** znajdź akcję poprawy, którą chcesz przypisać jako element nadrzędny z listy, lub wprowadź nazwę akcji na pasku wyszukiwania w górnej części. Po zidentyfikowaniu zamierzonej akcji zaznacz pole wyboru wyświetlane po lewej stronie nazwy akcji po umieszczeniu wskaźnika myszy na niej, a następnie wybierz pozycję **Zapisz**.

Wrócisz do strony szczegółów akcji. W obszarze **Źródło testowania** w sekcji **Przegląd** nowa akcja wyznaczona jako element nadrzędny znajduje się w obszarze **Akcja nadrzędna**.

## <a name="review-standards-and-regulations"></a>Przegląd standardów i przepisów

Sekcja **standardy i przepisy** zawiera listę standardów i przepisów związanych z działaniami ulepszania, które można przeszukiwać i filtrować. Mogą być one przeglądane przez odpowiednią **kontrolę**, **identyfikator kontroli**, **rodzinę kontroli** i **związane z tym rozporządzenie** .

## <a name="perform-work-and-store-documentation"></a>Wykonywanie pracy i przechowywanie dokumentacji

Pliki i notatki związane z implementacją i testowaniem można przekazywać bezpośrednio do sekcji **Dokumenty** . To środowisko jest bezpiecznym, scentralizowanym repozytorium, które ułatwia zaprezentowanie satysfakcji z mechanizmów kontroli w celu spełnienia standardów i przepisów dotyczących zgodności. Każdy użytkownik z dostępem tylko do odczytu może odczytać zawartość w tej sekcji. Tylko użytkownicy z uprawnieniami do edycji mogą przekazywać i pobierać pliki.

#### <a name="uploaded-documents"></a>Przekazane dokumenty

- Wybierz pozycję **Zarządzaj dokumentami** , aby przekazać odpowiednie pliki.
- Po otwarciu okienka wysuwanego Zarządzaj dokumentami wybierz pozycję **Dodaj dokument**, a następnie wybierz plik z systemu. Akceptowane typy plików:
  - Dokumenty (.doc, .xls, .ppt, .txt, .pdf)
  - Obrazy (.jpg, .png)
  - Wideo (mkv)
  - Skompresowane pliki (.zip, .rar)
- Gdy plik zostanie rozpoznany w okienku, wybierz pozycję **Zamknij**, co automatycznie zapisze załącznik pliku. Następnie zobaczysz plik wymieniony poniżej pozycji **Przekazane dokumenty**.
- Aby pobrać lub usunąć dokument, wybierz pozycję **Zarządzaj dokumentami** poniżej listy dokumentów. W okienku wysuwanym wybierz wiersz dokumentu, aby go wyróżnić, a następnie wybierz pozycję **Pobierz** lub **Usuń**.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Przypisywanie akcji poprawy do oceny w celu ukończenia

Po zakończeniu pracy, przeprowadzeniu testów i przekazaniu dowodów następnym krokiem jest przypisanie akcji poprawy do oceny w celu weryfikacji. Oceniający weryfikuje pracę i analizuje dokumentację, a następnie wybiera odpowiedni stan testu.

**Jeśli stan testu jest ustawiony na wartość "Przekazano"**: akcja została ukończona, a uzyskane punkty pokazują maksymalną liczbę osiągniętych punktów. Punkty są następnie liczone do ogólnego wyniku zgodności.

**Jeśli stan testu jest ustawiony na wartość "Niepowodzenie"**: akcja nie spełnia wymagań, a osoba oceniająca może przypisać ją z powrotem do odpowiedniego użytkownika na potrzeby dodatkowej pracy.

## <a name="accepting-updates-to-improvement-actions"></a>Akceptowanie aktualizacji akcji ulepszania

Gdy aktualizacja jest dostępna dla akcji poprawy, obok jej nazwy zostanie wyświetlone powiadomienie. Możesz zaakceptować aktualizację lub odroczyć ją na później.

#### <a name="what-causes-an-update"></a>Co powoduje aktualizację

Aktualizacja występuje, gdy istnieją zmiany związane z ocenianiem, automatyzacją lub zakresem. Zmiany mogą obejmować nowe wskazówki dotyczące akcji poprawy w oparciu o zmiany regulacyjne lub mogą być spowodowane zmianami produktu. Tylko akcje poprawy zarządzane przez organizacje otrzymują powiadomienia o aktualizacji.

#### <a name="where-youll-see-assessment-update-notifications"></a>Gdzie zostaną wyświetlone powiadomienia o aktualizacji oceny

Po zaktualizowaniu akcji poprawy obok jej nazwy zobaczysz etykietę **Oczekujące na aktualizację** na stronie akcji poprawy oraz na stronie szczegółów powiązanych ocen.

Przejdź do strony szczegółów akcji poprawy i wybierz przycisk **Przejrzyj aktualizację** na górnym banerze, aby przejrzeć szczegóły dotyczące zmian i zaakceptować lub odroczyć aktualizację.

#### <a name="review-update-to-accept-or-defer"></a>Przejrzyj aktualizację, aby zaakceptować lub odroczyć

Po wybraniu pozycji **Przejrzyj aktualizację** na stronie szczegółów akcji poprawy po prawej stronie ekranu zostanie wyświetlone okienko wysuwane. Okienko wysuwane zawiera kluczowe szczegóły dotyczące aktualizacji, takie jak oceny, których dotyczy problem, oraz zmiany oceny i zakresu.

Wybierz pozycję **Zaakceptuj aktualizację** , aby zaakceptować wszystkie zmiany w akcji poprawy. **Zaakceptowane zmiany są trwałe**.

> [!NOTE]
> Po zaakceptowaniu aktualizacji akcji akceptujesz również aktualizacje innych wersji lub wystąpień tej akcji. Aktualizacje będą propagowane w całej dzierżawie w przypadku akcji technicznych i będą propagowane w całej grupie w przypadku akcji innych niż techniczne.

Jeśli wybierzesz opcję **Anuluj**, aktualizacja nie zostanie zastosowana do akcji poprawy. Będziesz jednak nadal widzieć powiadomienie **Oczekujące na aktualizację** do momentu zaakceptowania aktualizacji.

**Dlaczego zalecamy akceptowanie aktualizacji**

Akceptowanie aktualizacji pomaga zapewnić, że masz najbardziej zaktualizowane wskazówki dotyczące korzystania z rozwiązań i podejmowania odpowiednich działań ulepszeń, które pomogą Ci spełnić wymagania dotyczące certyfikacji.

**Dlaczego warto odroczyć aktualizację**

Jeśli jesteś w trakcie oceny, która obejmuje akcję poprawy, możesz upewnić się, że zakończono pracę nad nią przed zaakceptowaniem aktualizacji. Możesz odroczyć aktualizację na później, wybierając pozycję **Anuluj** w okienku wysuwanej aktualizacji przeglądu.

#### <a name="accept-all-updates-at-once"></a>Akceptowanie wszystkich aktualizacji jednocześnie

Jeśli masz wiele aktualizacji i chcesz je akceptować jednocześnie, wybierz link **Akceptuj wszystkie aktualizacje** w górnej części tabeli akcji poprawy. Zostanie wyświetlone okienko wysuwane z listą akcji do zaktualizowania. Wybierz przycisk **Akceptuj aktualizacje** , aby zastosować wszystkie aktualizacje.

Pamiętaj, że po powrocie do strony akcji poprawy w górnej części strony może zostać wyświetlony komunikat z prośbą o odświeżenie strony w celu ukończenia aktualizacji.

## <a name="set-up-alerts-for-improvement-action-changes"></a>Konfigurowanie alertów dotyczących zmian akcji poprawy

Możesz skonfigurować alerty, aby natychmiast powiadamiać o pewnych zmianach akcji poprawy, takich jak zmiana stanu implementacji lub testu albo zwiększenie lub spadek oceny. Szybkie powiadomienia o takich zmianach mogą pomóc Ci być na bieżąco z możliwymi zagrożeniami związanymi ze zgodnością. Odwiedź stronę [Alerty i zasady alertów programu Compliance Manager](compliance-manager-alert-policies.md) , aby dowiedzieć się, jak skonfigurować alerty.

## <a name="export-a-report"></a>Eksportowanie raportu

Wybierz pozycję **Eksportuj** w lewym górnym rogu ekranu, aby pobrać arkusz Excel zawierający wszystkie akcje poprawy oraz kategorie filtrów wyświetlane na stronie akcji poprawy.
