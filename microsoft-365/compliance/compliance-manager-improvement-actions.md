---
title: Przypisywanie i ukończenie działań udoskonalania w Menedżerze zgodności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Dowiedz się, jak przeprowadzić implementację i testowanie kontrolek w Menedżerze zgodności firmy Microsoft. Przypisz raporty służbowe, przechowuj dokumentację i eksportuj.
ms.openlocfilehash: e0f1faa6ede05358eeafa8740fcf3cd79613b39c
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2021
ms.locfileid: "62988657"
---
# <a name="assign-and-complete-improvement-actions-in-compliance-manager"></a>Przypisywanie i ukończenie działań udoskonalania w Menedżerze zgodności

**W tym artykule:** W tym artykule wyjaśniono, jak **zarządzać przepływem pracy zgodności** za pomocą akcji udoskonalania. Dowiedz się, jak **przypisywać akcje udoskonalania** dotyczące implementacji i testowania, **zarządzania aktualizacjami** i **eksportowania raportów**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Zarządzanie przepływami pracy zgodności z działaniami udoskonalania

Akcje usprawniania scentralizują działania związane ze zgodnością. Każde działanie udoskonalania udostępnia szczegółowe wskazówki implementacji, które ułatwiają dostosowanie do przepisów i standardów ochrony danych. Do użytkowników w Twojej organizacji można przypisywać akcje służące do wykonywania prac implementacji i testowania. W ramach akcji można również przechowywać dokumentację, notatki i aktualizacje stanu rekordów.

Wszystkie działania udoskonalania są wymienione na stronie akcji udoskonalania. Dowiedz się więcej [o wyświetlaniu działań udoskonalania](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Strona szczegółów akcji udoskonalania

Każde działanie udoskonalania zawiera stronę ze szczegółami pokazującymi jego bieżący stan, powiązane standardy i wymagania prawne oraz zalecane wskazówki implementacji. [W działaniach](compliance-score-calculation.md#technical-and-non-technical-actions) technicznych znajduje **się link Uruchom** teraz, za pomocą których możesz znaleźć odpowiednie rozwiązanie do wdrożenia. Możesz dołączyć dokumentację implementacji i testowania bezpośrednio do strony szczegółów akcji udoskonalania.

Aby wyświetlić stronę szczegółów akcji udoskonalania:

1. Przejdź na stronę działań udoskonalania.
2. Wybierz wiersz zamierzonego działania udoskonalania, co spowoduje otwarcie jego strony szczegółów.

Możesz łatwo wyświetlić na liście następną lub poprzednią akcję udoskonalania, wybierając strzałkę w górę lub w dół w prawym górnym rogu ekranu. Jeśli odfiltrowano listę na stronie akcji udoskonalania, przejście w górę lub w dół umożliwia przejście do następnej pozycji na tej liście filtrowanych.

## <a name="assign-improvement-actions"></a>Przypisywanie akcji udoskonalania

Aby rozpocząć prace implementacji nad akcją ulepszoną, możesz wykonać pracę samodzielnie lub przypisać ją in inowi użytkownikowi. Przypisana osoba może być:

- Właściciel zasad biznesowych
- Implementer IT
- Inny pracownik odpowiedzialny za wykonanie zadania

Po zidentyfikowaniu odpowiedniego osoby przydzielonej upewnij się, że ma oni odpowiednią rolę [Menedżera](compliance-manager-setup.md#set-user-permissions-and-assign-roles) zgodności, aby wykonać pracę. Następnie wykonaj poniższe czynności, aby przypisać akcję udoskonalania:

1. Na stronie szczegółów akcji udoskonalania wybierz pozycję **Edytuj stan** w pobliżu lewej górnej części ekranu.

2. W okienku wysuwanego stanu Edycja zaznacz pole **Przypisane** do, aby wyświetlić listę **Sugerowane** osoby użytkowników. Możesz wybrać użytkownika z listy lub wpisać adres e-mail osoby, do której chcesz go przypisać.

3. Wybierz **pozycję Zapisz i zamknij**. Przypisany użytkownik otrzyma wiadomość e-mail z wyjaśnieniem, że do użytkownika przydzielono akcję udoskonalania, z bezpośrednim linkiem do działania udoskonalania. 
> [!NOTE]
> Klienci działu Community (GCC) High and Department of Defense (DoD) nie otrzymają wiadomości e-mail po przypisaniu do nich akcji udoskonalania.

Przypisany użytkownik może następnie wykonać zalecane czynności.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Przypisywanie wielu akcji udoskonalania do jednego użytkownika

Możesz przypisać wiele akcji udoskonalania do jednego użytkownika, korzystając z następujących kroków:

1. Przejdź na stronę Akcje udoskonalania.
2. Zaznacz obszar po lewej stronie nazwy akcji udoskonalania. Zostanie wyświetlony okrągła ikona wyboru wskazująca, że ta akcja jest zaznaczona. Zaznacz wszystkie akcje, które chcesz przypisać.
3. Wybierz link **Przypisz do** użytkownika u góry tabeli akcji udoskonalania.
4. Zostanie wyświetlone okno podręczne. W **polu Przypisz** do zacznij wpisywać imię i nazwisko osoby, do której chcesz przypisać akcje. Możesz również wybrać pozycję z listy sugerowanych osób.
5. Po wypełnieniu pola **Przypisz** do imieniem i nazwiskiem osoby przydzielonej wybierz pozycję **Przypisz**.
6. Następnie zostanie wyświetlony strona Akcje udoskonalania z nowymi przypisanymi do Ciebie akcjami, które zostały właśnie przypisane.

## <a name="perform-work-and-store-documentation"></a>Wykonywanie dokumentacji służbowej i przechowywania

Pliki i notatki związane z implementacją i testowaniem można przekazywać bezpośrednio do sekcji **Uwagi i dokumentacja** . To środowisko to bezpieczne scentralizowane repozytorium, które pomoże Ci pokazać zadowolenie z kontroli w celu spełnienia standardów i przepisów dotyczących zgodności z przepisami. Każdy użytkownik z dostępem tylko do odczytu może odczytywać zawartość tej sekcji. Tylko użytkownicy z uprawnieniami do edytowania mogą przekazywać i pobierać pliki oraz wprowadzać i edytować notatki.

Sekcja **Notatki i dokumentacja** zawiera pola dla przekazanych dokumentów, notatek dotyczących implementacji, notatek dotyczących testów i dodatkowych notatek.

#### <a name="uploaded-documents"></a>Przekazane dokumenty

- Wybierz **pozycję Zarządzaj dokumentami** , aby przekazać odpowiednie pliki.
- Gdy zostanie otwarte okienko wysuwu zarządzanie dokumentami, wybierz pozycję **Dodaj dokument**, a następnie wybierz plik w systemie. Zaakceptowane typy plików:
    - Dokumenty (.doc, .xls, .ppt, .txt, .pdf)
    - Obrazy (.jpg, .png)
    - Klip wideo (mkv)
    - Pliki skompresowane (.zip, .rar)
- Gdy plik zostanie rozpoznany w okienku, wybierz pozycję **Zamknij**, co spowoduje automatyczne zapisanie załącznika pliku. Plik zostanie wyświetlony na liście poniżej Przekazane **dokumenty**.
- Aby pobrać lub usunąć dokument, wybierz pozycję Zarządzaj **dokumentami** poniżej listy dokumentów. W okienku wysuwany zaznacz wiersz dokumentu, aby go wyróżnić, a następnie wybierz pozycję **Pobierz** lub **Usuń**.

#### <a name="implementation-notes-test-notes-and-additional-notes"></a>Uwagi dotyczące implementacji, uwagi dotyczące testów i dodatkowe uwagi

- Aby dodać notatki w dowolnym z tych trzech pól, wybierz pozycję **Edytuj notatki implementacji** poniżej dowolnego z tych pól.
- Gdy zostanie otwarte okienko wysuwu, wprowadź notatki w polu tekstowym, a następnie wybierz pozycję **Zapisz i zamknij**.
- Aby edytować notatki, wybierz **pozycję Edytuj notatki implementacji**, dokonaj zmian, a następnie wybierz **pozycję Zapisz i zamknij**.

Limit znaków w polach notatek nie jest limitem znaków. Zalecamy, aby notatki były krótkie, aby można je było łatwo wyświetlać i edytować na stronie szczegółów akcji udoskonalania.

## <a name="change-improvement-action-status"></a>Zmienianie stanu akcji udoskonalania

Możesz zarejestrować stan i datę implementacji oraz stan i datę testu dla każdego działania udoskonalania. Pola **implementacji** **i stanu** testowania mogą być edytowane przez dowolnego użytkownika z uprawnieniami do edycji, nie tylko przez przypisaną osobę.

Aby edytować stan akcji udoskonalania, wybierz **pozycję Edytuj stan** w lewej górnej części strony szczegółów. Poniżej przedstawiono dostępne pola i opcje stanu:

- **Stan implementacji**
    - **Nie zaimplementowano** — akcja nie została jeszcze zaimplementowana
    - **Zaimplementowano** — wdrożono akcję
    - **Implementacja** alternatywna — wybierz tę opcję, jeśli używasz innych narzędzi innych firm lub zajęsz się innymi działaniami, które nie zostały uwzględnione w zaleceniach firmy Microsoft
    - **Planowane** — planowana jest akcja implementacji
    - **Poza zakresem** — działanie nie jest istotne dla Twojej organizacji i nie wpływa na wynik
- **Data wdrożenia**: dostępne do wyboru, kiedy stan implementacji jest "zaimplementowany" lub "implementacja alternatywna"
- **Stan testu**: dostępny do wyboru, kiedy stan implementacji jest "zaimplementowany" lub "implementacja alternatywna":
    - **Nie oceniono** — działanie nie zostało sprawdzone
    - **Pomyślnie** przekazane — implementacja została zweryfikowana przez oceniaka
    - **Niskie ryzyko,** których testowanie zakończyło się niepowodzeniem, niskie ryzyko
    - **Średnie ryzyko niepowodzenie —** testowanie zakończyło się niepowodzeniem, średnie ryzyko
    - **Niepowodzenie wysokiego ryzyka** — testowanie zakończyło się niepowodzeniem, wysokie ryzyko
    - **Poza zakresem** — nie ma możliwości zastosowania akcji w ramach oceny i nie wpływa na wynik
- **Data testowa**: przełączanie przez okno podręczne kalendarza w celu wybrania daty

Typowe akcje synchronizują się między grupami. Jeśli dwie różne oceny w tej samej grupie współużytkują działania udoskonalania, które zarządzasz, wszelkie aktualizacje szczegółów implementacji akcji lub stanu zostaną automatycznie zsynchronizowane z tym samym działaniem w innej ocenie w grupie. Ta synchronizacja umożliwia wdrożenie jednego działania ulepszeń i spełnienie kilku wymagań w ramach wielu przepisów.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Przypisywanie akcji udoskonalania, aby oceniać jego wykonanie

Kolejnym krokiem po ukończeniu pracy, testowaniu i przesłaniu dowodów jest przypisanie czynności udoskonalania do oceniania w celu weryfikacji. Oceniająco sprawdza pracę i sprawdza dokumentację, a następnie wybiera odpowiedni stan testu.

**Jeśli stan testu jest ustawiony na "Zakończone"**: akcja jest ukończona, a punkty, które udało się uzyskać, pokazują, ile maksymalnie punktów udało się osiągnąć. Punkty są następnie liczone w ogólnym wyniku zgodności.

**Jeśli stan testu ma wartość "** Nie powiodło się": akcja nie spełnia wymagań, a oceniacy może ją z powrotem przypisać do odpowiedniego użytkownika w celu dodatkowej pracy.

## <a name="accepting-updates-to-improvement-actions"></a>Akceptowanie aktualizacji w celu działań udoskonalania

Gdy będzie dostępna aktualizacja w celu działania usprawnień, obok jego nazwy zostanie wyświetlony komunikat. Możesz zaakceptować aktualizację lub odroczyć ją na później.

#### <a name="what-causes-an-update"></a>Co powoduje aktualizację

Aktualizacja występuje w przypadku zmian dotyczących oceniania, automatyzacji lub zakresu. Zmiany mogą obejmować nowe wskazówki dotyczące działań usprawnień opartych na zmianach przepisów prawnych lub mogą być spowodowane zmianami w produktach. Tylko działania udoskonalania zarządzane przez Twoją organizacje otrzymują powiadomienia o aktualizacjach.

#### <a name="where-youll-see-assessment-update-notifications"></a>Gdzie są wyświetlane powiadomienia o aktualizacjach oceny

Po zaktualizowaniu działania ulepszeń obok jego nazwy, na stronie  akcji udoskonalania i na stronie szczegółów powiązanych z nimi ocen, będzie dostępna etykieta Oczekująca aktualizacja.

Przejdź do strony szczegółów akcji udoskonalania i wybierz przycisk Sprawdź aktualizację  na górnym banerze, aby przejrzeć szczegóły zmian i zaakceptować lub odroczyć aktualizację.

#### <a name="review-update-to-accept-or-defer"></a>Przejrzyj aktualizację, aby zaakceptować lub odroczyć

Po wybraniu **przycisku Sprawdź** aktualizację na stronie szczegółów akcji udoskonalania po prawej stronie ekranu zostanie wyświetlone okienko wysuwu. Okienko wysuwu zawiera kluczowe informacje dotyczące aktualizacji, takie jak ocena, na które ma wpływ, oraz zmiany wyników i zakresu.

Wybierz **pozycję Zaakceptuj aktualizację** , aby zaakceptować wszystkie zmiany w działaniu udoskonalania. **Zaakceptowane zmiany są trwałe**.

> [!NOTE]
> Gdy zaakceptujesz aktualizację akcji, akceptujesz również aktualizacje wszystkich innych wersji lub wystąpień tej akcji. Aktualizacje będą propagowane w całej dzierżawie do działań technicznych i będą propagowane w całej grupie w przypadku działań innych niż techniczne.

Jeśli wybierzesz **pozycję Anuluj**, aktualizacja nie zostanie zastosowana do akcji udoskonalania. Jednak do czasu zaakceptowania aktualizacji nadal będziesz widzieć  powiadomienie o oczekującej aktualizacji.

**Dlaczego zalecamy akceptowanie aktualizacji**

Zaakceptowanie aktualizacji pomaga zapewnić, że masz najbardziej zaktualizowane wskazówki dotyczące korzystania z rozwiązań i podejmowania odpowiednich działań udoskonalania, aby pomóc Ci w spełnianiu wymagań certyfikacji.

**Dlaczego warto odroczyć aktualizację**

Jeśli jesteś w trakcie oceniania, który obejmuje działanie udoskonalania, warto upewnić się, że zakończono pracę nad tym, zanim zaakceptujesz aktualizację. Aktualizację można odroczyć na później, wybierając pozycję **Anuluj** w okienku wysuwanej aktualizacji recenzji.

#### <a name="accept-all-updates-at-once"></a>Akceptowanie wszystkich aktualizacji jednocześnie

Jeśli masz wiele aktualizacji i chcesz zaakceptować je wszystkie za jednym razem, **wybierz link Zaakceptuj** wszystkie aktualizacje u góry tabeli akcji udoskonalania. Zostanie wyświetlone okienko wysuane z liczbą akcji do zaktualizowania. Wybierz przycisk **Zaakceptuj aktualizacje** , aby zastosować wszystkie aktualizacje.

Zwróć uwagę, że po powrocie do strony akcji udoskonalania w górnej części strony może zostać wyświetlony komunikat z prośbą o odświeżenie strony w celu ukończenia aktualizacji.

## <a name="export-a-report"></a>Eksportowanie raportu

Wybierz **pozycję** Eksportuj w lewym górnym rogu ekranu, aby pobrać arkusz Excel zawierający wszystkie akcje udoskonalania i kategorie filtrowania przedstawione na stronie akcji udoskonalania.