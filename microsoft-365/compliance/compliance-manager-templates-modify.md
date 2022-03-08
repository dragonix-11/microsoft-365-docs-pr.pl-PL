---
title: Modyfikowanie szablonów ocen w Menedżerze zgodności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak modyfikować szablony ocen w Menedżerze zgodności firmy Microsoft.
ms.openlocfilehash: d409c21d31c909e7e6a59c308c7087e26ec78e24
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320567"
---
# <a name="modify-assessment-templates-in-microsoft-compliance-manager"></a>Modyfikowanie szablonów ocen w Menedżerze zgodności firmy Microsoft

Podczas pracy z ocenami w Menedżerze zgodności możesz zmodyfikować utworzony szablon oceny. Proces tworzenia szablonu jest podobny do [](compliance-manager-templates-create.md) procesu tworzenia szablonu w ten sposób, że przekażesz wraz z danymi szablonu Excel sformatowany plik szablonu.

Jednak podczas formatowania pliku ze zmianami danych istniejącego szablonu należy pamiętać o szczegółach. **Zalecamy dokładne zapoznanie się z tymi instrukcjami w celu zagwarantowania, że nie zastąpisz istniejących danych, które chcesz zachować.**

Aby dowiedzieć się więcej o formacie tego arkusza kalkulacyjnego, zobacz [Formatowanie danych szablonu za](compliance-manager-templates-format-excel.md) pomocą Excel.

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Formatowanie pliku Excel w celu zmodyfikowania istniejącego szablonu

Na stronie  **szablonów oceny**  wybierz szablon, który chcesz zmodyfikować, co spowoduje, że zostanie strona szczegółów tego szablonu. Następnie wybierz  **pozycjęEkportuj do Excel**. Zostanie Excel plik szablonu ze wszystkimi danymi szablonu. Zapisz plik na komputerze lokalnym.

Aby pracować z tym plikiem, przejdź do sekcji poniżej, aby szybko znaleźć potrzebne instrukcje:

- [Edytowanie atrybutów szablonu głównego](#edit-the-main-template-attributes)
- [Dodawanie akcji udoskonalania](#add-an-improvement-action)
- [Edytowanie informacji dotyczących akcji udoskonalania](#edit-an-improvement-actions-information)
- [Zmienianie nazwy akcji udoskonalania](#change-an-improvement-actions-name)
- [Usuwanie akcji udoskonalania](#remove-an-improvement-action)
- [Usuwanie kontrolki](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Edytowanie atrybutów szablonu głównego

Na karcie **Szablony** możesz edytować dowolne dane w kolumnie tytułu,  kolumnie **inScopeServices** i dowolnej innej kolumnie, która może zostać dodana. Nie można jednak edytować niczego w **kolumnach produktów ani** **certyfikacji** .

### <a name="add-an-improvement-action"></a>Dodawanie akcji udoskonalania

1. Przejdź do **karty Akcje** . Dodaj informacje w wymaganych polach w pierwszym pustym wierszu pod istniejącymi akcjami.
2. Przejdź do **karty ControlFamily** . Znajdź wiersz zawierający kontrolkę, na która jest mapowanie akcji udoskonalania. Dodaj nową akcję do kolumny **controlActionTitle** w tym wierszu (pamiętaj, aby oddzielić w tym polu wiele akcji dwoma średnikami, bez spacji między).
3. Zapisz arkusz kalkulacyjny.

### <a name="edit-an-improvement-actions-information"></a>Edytowanie informacji dotyczących akcji udoskonalania

Możesz zmienić dowolne informacje dotyczące akcji udoskonalania *, z wyjątkiem tytułu*. Każdą komórkę można edytować od kolumn B, a po zaimportowaniu pliku z powrotem do szablonu działania udoskonalania w tym szablonie będą teraz zawierać zaktualizowane dane.

Nie można edytować **tytułu akcji** (kolumna A), ponieważ w takim przypadku Menedżer zgodności uzna to za nowe działanie udoskonalania. Jeśli chcesz zmienić nazwę akcji udoskonalania, zapoznaj się z instrukcjami bezpośrednio poniżej.

### <a name="change-an-improvement-actions-name"></a>Zmienianie nazwy akcji udoskonalania

Jeśli chcesz zmienić nazwę akcji udoskonalania, musisz jawnie wskazać w arkuszu kalkulacyjnym, że chcesz zastąpić istniejącą nazwę nową nazwą. Wykonaj następujące czynności:

1. Na karcie **Akcje** arkusza kalkulacyjnego dodaj do arkusza kalkulacyjnego nową kolumnę za kolumną A.
2. W tej nowej kolumnie, która jest teraz kolumną B, umieść jako nagłówek w wierszu 1: **oldActionTitle**.
3. Skopiuj zawartość kolumny A i wklej ją do kolumny B. Dzięki temu istniejące tytuły akcji udoskonalania, które chcesz zmienić, zostaną wprowadzone w kolumnie B.
4. W kolumnie A **nazwa actionTitle** usuń starą nazwę i zamień ją na nową, aby usprawnić działanie.

Należy pamiętać, że tytuły akcji, zarówno dla akcji udoskonalania, jak i akcji firmy Microsoft, należy zapisywać w języku angielskim, aby były rozpoznawane w przypadku odwołania się w kontrolkach.

### <a name="remove-an-improvement-action"></a>Usuwanie akcji udoskonalania

Aby usunąć działanie udoskonalania z szablonu, musisz usunąć go z każdej kontrolki, która się do niego odwołuje. Wykonaj poniższe czynności, aby zmodyfikować arkusz kalkulacyjny:

1. Na **karcie ControlFamily** wyszukaj tytuł akcji udoskonalania, którą chcesz usunąć.
2. Usuń tytuł akcji udoskonalania w komórkach, w których jest wyświetlany. Jeśli akcja udoskonalania jest jedyną akcją w tym wierszu, usuń cały wiersz (co spowoduje usunięcie kontrolki).
3. Na **karcie Akcje** usuń wiersz zawierający akcję udoskonalania, która ma być usuwana.
4. Zapisz arkusz kalkulacyjny.

Po zaimportowaniu arkusza kalkulacyjnego z powrotem do szablonu działanie udoskonalania zostanie usunięte z szablonu.

Usunięcie działania udoskonalania z szablonu nie powoduje całkowitego usunięcia działania udoskonalania z Menedżera zgodności. Do tej akcji nadal może odwoływać się inny szablon.

### <a name="remove-a-control"></a>Usuwanie kontrolki

Aby usunąć kontrolkę, zmodyfikuj arkusz kalkulacyjny, korzystając z poniższych kroków, a następnie ponownie zaimportuj arkusz kalkulacyjny:

1. Na **karcie ControlFamily (** Nazwa Kontrolki) znajdź kontrolkę, którą chcesz usunąć, w kolumnie **ControlName (Nazwa kontrolki** ).
2. Usuń wiersz dla tej kontrolki.
    - Jeśli ta usunięta kontrolka zawiera akcje udoskonalania, do których nie odwołują się inne kontrolki, musisz usunąć te akcje udoskonalania z **karty Akcje** . W przeciwnym razie zostanie wyświetlony błąd sprawdzania poprawności.

3. Zapisz arkusz kalkulacyjny.

Po zaimportowaniu arkusza kalkulacyjnego z powrotem do szablonu kontrolka zostanie usunięta z szablonu.

## <a name="modify-template-info-in-compliance-manager"></a>Modyfikowanie informacji szablonu w Menedżerze zgodności

Po ukończeniu Excel zapisaniu pliku, wykonaj poniższe czynności.

1. Otwórz ponownie stronę szablonu oceniania i wybierz szablon. Na stronie szczegółów szablonu wybierz pozycję **Modyfikuj** szablon, aby zainicjować kreatora modyfikacji.
2. Na **ekranie Upload wybierz** **pozycję Przeglądaj**, aby znaleźć i przekazać Excel pliku.
3. Jeśli nie występują żadne problemy z plikiem, na następnym ekranie zostanie pokazana nazwa przekazanego pliku. Wybierz **pozycję** Dalej, aby kontynuować (jeśli chcesz zmienić plik, wybierz **Upload inny plik**).
    - Jeśli występuje problem z plikiem, u góry zostanie wyświetlony komunikat o błędzie informujący o tym, co się stało. Musisz naprawić plik i przekazać go ponownie. Błędy będą się pojawiać, jeśli arkusz kalkulacyjny został nieprawidłowo sformatowany lub w niektórych polach występują nieprawidłowe informacje.

4. Ekran **Recenzja i zakończenie** zawiera liczbę akcji udoskonalania i kontrolek oraz maksymalną liczbę wyników dla szablonu. Gdy wszystko będzie gotowe do zatwierdzenia, wybierz pozycję **Dalej**.
5. Ostatni ekran potwierdza, że szablon został zmodyfikowany. Wybierz **pozycję Gotowe** , aby zamknąć kreatora.

Twój szablon będzie teraz zawierać wprowadzone zmiany. W przypadku wszystkich ocen, które używają tego zmodyfikowanego szablonu, będą teraz wyświetlane oczekujące aktualizacje i konieczne będzie zaakceptowanie aktualizacji oceny, aby odzwierciedlić zmiany wprowadzone w szablonie. Dowiedz się więcej o [aktualizacjach oceniania](compliance-manager-assessments.md#accept-updates-to-assessments).

> [!NOTE]
> Jeśli korzystasz z Menedżera zgodności w języku innym niż angielski, część tekstu jest wyświetlana w języku angielskim podczas eksportowania szablonu do programu Excel. Tytuły akcji (zarówno działania udoskonalania, jak i, tam gdzie to ma zastosowanie, akcje firmy Microsoft) muszą być rozpoznawane przez kontrolki w języku angielskim. Jeśli wprowadzasz zmiany w tytule akcji, pamiętaj, aby zapisać go w języku angielskim, aby plik został poprawnie importny.
