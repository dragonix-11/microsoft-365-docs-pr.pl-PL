---
title: Modyfikowanie szablonów oceny w programie Microsoft Purview Compliance Manager
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
description: Dowiedz się, jak modyfikować szablony oceny w programie Microsoft Purview Compliance Manager.
ms.openlocfilehash: f21ff61f6bb06f00d1db8381e3760e7c4b5343aa
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630416"
---
# <a name="modify-assessment-templates-in-microsoft-purview-compliance-manager"></a>Modyfikowanie szablonów oceny w programie Microsoft Purview Compliance Manager

Podczas pracy z ocenami w Menedżerze zgodności możesz zmodyfikować utworzony szablon oceny. Proces jest podobny do procesu [tworzenia szablonu](compliance-manager-templates-create.md) , ponieważ przekażesz sformatowany plik programu Excel z danymi szablonu.

Istnieją jednak szczegóły, o których należy pamiętać podczas formatowania pliku ze zmianami istniejących danych szablonu. **Zalecamy dokładne przejrzenie tych instrukcji, aby upewnić się, że nie zastąpisz żadnych istniejących danych, które chcesz zachować.**

Aby dowiedzieć się więcej na temat formatu tego arkusza kalkulacyjnego, zobacz [Formatowanie danych szablonu za pomocą programu Excel](compliance-manager-templates-format-excel.md).

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Formatowanie pliku programu Excel w celu zmodyfikowania istniejącego szablonu

Na stronie **szablonów oceny** wybierz szablon, który chcesz zmodyfikować, aby wyświetlić jego stronę szczegółów. Następnie wybierz pozycję **Eksportuj do programu Excel**. Plik programu Excel ze wszystkimi danymi szablonu zostanie pobrany. Zapisz plik na komputerze lokalnym.

Aby pracować z tym plikiem, przejdź do poniższej sekcji, aby szybko znaleźć potrzebne instrukcje:

- [Edytowanie głównych atrybutów szablonu](#edit-the-main-template-attributes)
- [Dodawanie akcji poprawy](#add-an-improvement-action)
- [Edytowanie informacji dotyczących akcji poprawy](#edit-an-improvement-actions-information)
- [Zmienianie nazwy akcji poprawy](#change-an-improvement-actions-name)
- [Usuwanie akcji poprawy](#remove-an-improvement-action)
- [Usuwanie kontrolki](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Edytowanie głównych atrybutów szablonu

Na **karcie Szablony** możesz edytować dowolne elementy w kolumnie **tytułu** , **kolumnie inScopeServices** i w dowolnej innej kolumnie, która mogła zostać dodana. Nie można jednak edytować niczego w kolumnach **produktu** ani **certyfikacji** .

### <a name="add-an-improvement-action"></a>Dodawanie akcji poprawy

1. Przejdź do karty **Akcje** . Dodaj informacje w wymaganych polach w pierwszym pustym wierszu poniżej istniejących akcji.
2. Przejdź do karty **ControlFamily** . Znajdź wiersz zawierający kontrolkę, na która mapuje się akcja poprawy. Dodaj nową akcję do kolumny **controlActionTitle** w tym wierszu (pamiętaj, aby rozdzielić wiele akcji w tym polu dwoma średnikami, bez odstępu między nimi).
3. Zapisz arkusz kalkulacyjny.

### <a name="edit-an-improvement-actions-information"></a>Edytowanie informacji dotyczących akcji poprawy

Możesz zmienić informacje o dowolnej akcji poprawy *, z wyjątkiem jej tytułu*. Możesz edytować dowolną komórkę z kolumn B dalej, a po zaimportowaniu pliku z powrotem do szablonu akcje poprawy w tym szablonie będą teraz zawierać zaktualizowane dane.

Nie można edytować **elementu actionTitle** (kolumna A), ponieważ jeśli to zrobisz, Menedżer zgodności uzna to za nową akcję poprawy. Jeśli chcesz zmienić nazwę akcji poprawy, zapoznaj się z instrukcjami bezpośrednio poniżej.

### <a name="change-an-improvement-actions-name"></a>Zmienianie nazwy akcji poprawy

Jeśli chcesz zmienić nazwę akcji poprawy, musisz jawnie wyznaczyć w arkuszu kalkulacyjnym, że zastępujesz istniejącą nazwę nową nazwą. Wykonaj następujące czynności:

1. Na karcie **Akcje** arkusza kalkulacyjnego dodaj nową kolumnę do arkusza kalkulacyjnego po kolumnie A.
2. W tej nowej kolumnie, która jest teraz kolumną B, umieść jako nagłówek w wierszu 1: **oldActionTitle**.
3. Skopiuj zawartość kolumny A i wklej ją do kolumny B. Dzięki temu istniejące tytuły akcji poprawy, które chcesz zmienić, są umieszczane w kolumnie B.
4. W kolumnie A **, actionTitle** usuń starą nazwę i zastąp ją nową nazwą akcji poprawy.

Należy pamiętać, że tytuły akcji, zarówno dla akcji ulepszania, jak i dla akcji firmy Microsoft, muszą być napisane w języku angielskim, aby można je było rozpoznać, gdy są one przywoływane w kontrolkach.

### <a name="remove-an-improvement-action"></a>Usuwanie akcji poprawy

Aby usunąć akcję poprawy z szablonu, należy usunąć ją z każdej kontrolki, która do niej odwołuje się. Wykonaj poniższe kroki, aby zmodyfikować arkusz kalkulacyjny:

1. Na karcie **ControlFamily** wyszukaj tytuł akcji poprawy, którą chcesz usunąć.
2. Usuń tytuł akcji poprawy w komórkach, w których jest wyświetlana. Jeśli akcja poprawy jest jedyną akcją w tym wierszu, usuń cały wiersz (co usuwa kontrolkę).
3. Na karcie **Akcje** usuń wiersz zawierający akcję poprawy, którą usuwasz.
4. Zapisz arkusz kalkulacyjny.

Po zaimportowaniu arkusza kalkulacyjnego z powrotem do szablonu akcja poprawy zostanie usunięta z szablonu.

Usunięcie akcji poprawy z szablonu nie powoduje całkowitego usunięcia akcji poprawy z Menedżera zgodności. Do tej akcji może nadal odwoływać się inny szablon.

### <a name="remove-a-control"></a>Usuwanie kontrolki

Aby usunąć kontrolkę, zmodyfikuj arkusz kalkulacyjny, wykonując poniższe kroki, a następnie ponownie zaimportuj arkusz kalkulacyjny:

1. Na karcie **ControlFamily** znajdź kontrolkę, którą chcesz usunąć w kolumnie **controlName** .
2. Usuń wiersz dla tej kontrolki.
    - Jeśli ta usunięta kontrolka zawiera akcje poprawy, do których nie odwołuje się żadna inna kontrolka, należy usunąć te akcje poprawy z karty **Akcje** . W przeciwnym razie zostanie wyświetlony błąd weryfikacji.

3. Zapisz arkusz kalkulacyjny.

Po zaimportowaniu arkusza kalkulacyjnego z powrotem do szablonu kontrolka zostanie usunięta z szablonu.

## <a name="modify-template-info-in-compliance-manager"></a>Modyfikowanie informacji o szablonie w Menedżerze zgodności

Po zakończeniu i zapisaniu pliku programu Excel wykonaj następujące kroki.

1. Otwórz ponownie stronę szablonu oceny i wybierz szablon. Na stronie szczegółów szablonu wybierz pozycję **Modyfikuj szablon** , aby zainicjować kreatora modyfikacji.
2. Na ekranie **Przekazywanie pliku** wybierz pozycję **Przeglądaj** , aby znaleźć i przekazać plik programu Excel.
3. Jeśli nie ma żadnych problemów z plikiem, na następnym ekranie zostanie wyświetlona nazwa przekazanego pliku. Wybierz pozycję **Dalej** , aby kontynuować (jeśli chcesz zmienić plik, wybierz pozycję **Przekaż inny plik**).
    - Jeśli wystąpił problem z plikiem, u góry znajduje się komunikat o błędzie wyjaśniający, co jest nie tak. Musisz naprawić plik i przekazać go ponownie. Błędy spowodują nieprawidłowe formatowanie arkusza kalkulacyjnego lub nieprawidłowe informacje w niektórych polach.

4. Na ekranie **Przeglądanie i zakończenie** jest wyświetlana liczba akcji i kontrolek poprawy oraz maksymalny wynik szablonu. Gdy wszystko będzie gotowe do zatwierdzenia, wybierz pozycję **Dalej**.
5. Ostatni ekran potwierdza, że szablon został zmodyfikowany. Wybierz pozycję **Gotowe** , aby zamknąć kreatora.

Szablon będzie teraz zawierać wprowadzone zmiany. Wszystkie oceny korzystające z tego zmodyfikowanego szablonu będą teraz wyświetlać oczekujące aktualizacje i musisz zaakceptować aktualizacje ocen, aby odzwierciedlić zmiany wprowadzone w szablonie. Dowiedz się więcej o [aktualizacjach ocen](compliance-manager-assessments.md#accept-updates-to-assessments).

> [!NOTE]
> Jeśli używasz Menedżera zgodności w języku innym niż angielski, podczas eksportowania szablonu do programu Excel zostanie wyświetlony tekst w języku angielskim. Tytuły akcji (zarówno akcji poprawy, jak i, w stosownych przypadkach, akcji firmy Microsoft) muszą być rozpoznawane przez kontrolki w języku angielskim. Jeśli wprowadzisz zmiany w tytule akcji, pamiętaj o zapisaniu go w języku angielskim, aby plik został poprawnie zaimportowany.
