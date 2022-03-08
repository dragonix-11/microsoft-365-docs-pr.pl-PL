---
title: Rozszerzanie szablonów ocen w Menedżerze zgodności firmy Microsoft
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
description: Dowiedz się, jak rozszerzyć szablony ocen w Menedżerze zgodności firmy Microsoft, aby dodawać i modyfikować kontrolki.
ms.openlocfilehash: 4c9e4543a046e09733711500ae6162a547e3602b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316214"
---
# <a name="extend-assessment-templates-in-microsoft-compliance-manager"></a>Rozszerzanie szablonów ocen w Menedżerze zgodności firmy Microsoft

Menedżer zgodności umożliwia dodanie własnych kontrolek i działań udoskonalania do istniejącego szablonu. Ten proces nosi nazwę rozszerzania szablonu.

Aby rozszerzyć szablon, należy użyć specjalnych instrukcji dotyczących modyfikowania danych szablonów w zależności od tego, czy rozszerzasz szablony oceniań firmy Microsoft, czy uniwersalne szablony oceniań.

## <a name="extend-microsoft-assessment-templates"></a>Rozszerzanie szablonów ocen firmy Microsoft

Rozszerzenie szablonu firmy Microsoft, na przykład utworzonego do użytku z platformą Microsoft 365, nadal może otrzymywać aktualizacje wydane przez firmę Microsoft. Aktualizacje mogą się pojawiać w przypadku zmiany związanego z przepisami lub produktu (zobacz [Akceptowanie aktualizacji ocen](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Przygotowywanie danych szablonu i tworzenie rozszerzenia

Aby się przygotować, musisz zebrać specjalnie sformatowany arkusz kalkulacyjny programu Excel, aby zaimportować niezbędne dane szablonów. Pliki programu Excel są zgodne z tym samym formatem opisanym w temacie Formatowanie danych szablonu oceny w programie [Excel](compliance-manager-templates-format-excel.md), ale istnieją specjalne wymagania dotyczące rozszerzeń. Zapoznaj się z tymi dodatkowymi tematami, aby uzyskać pomoc w zapobieganiu błędom:

- Arkusz kalkulacyjny powinien zawierać tylko akcje i kontrolki, które chcesz dodać do oceny.
- Arkusz kalkulacyjny nie może zawierać żadnych kontrolek ani akcji istniejących już w ramach oceny, którą chcesz zmodyfikować.
- Rozważ nadenie tytułu szablonu tytułu "rozszerzenie", na przykład "RODO — [nazwa Twojej firmy] rozszerzenia". Ułatwia to identyfikację na liście na stronie szablonów formularzy  oceniania w odróżnieniu od standardowego szablonu dostarczonego przez firmę Microsoft lub szablonu niestandardowego o podobnej nazwie.

Po sformatowaniu arkusza kalkulacyjnego wykonaj poniższe czynności.

1. Przejdź na stronę **szablonów oceniania** i wybierz **pozycję Utwórz nowy szablon**. Zostanie otwarty kreator tworzenia szablonów.

2. Wybierz typ szablonu, który chcesz utworzyć. W tym przypadku wybierz pozycję **Rozszerz szablon firmy Microsoft, a** następnie **wybierz pozycję Szablon firmy Microsoft**.

3. Po prawej stronie ekranu zostanie wyświetlone okienko wysuwu wyboru szablonu z listą wszystkich szablonów oraz ich statusami aktywnymi lub nieaktywnymi. Licznik **aktywowanych szablonów** wskazuje, ile szablonów jest obecnie w użyciu, poza całkowitą liczbą dostępnych do użycia. W przypadku przekroenia limitu zostanie wyświetlony pasek komunikatów z powiadomieniem.

4. Po prawej stronie ekranu pojawi się okienko wysuwu wyboru szablonu. Stosowanie **filtrów** w celu zlokalizowania szablonu przy użyciu funkcji wyszukiwania

5. Po odnalezieniu szablonu wybierz przycisk radiowy z lewej strony jego nazwy, a następnie wybierz pozycję **Zapisz**.

6. Na następnym ekranie zostanie wybrany szablon. Jeśli ten wybór jest poprawny, wybierz przycisk **Dalej**. (Jeśli jest nieprawidłowy, **wybierz pozycję Wybierz inny szablon** do wyboru ponownie).

7. Na **ekranie Przekazywanie pliku** **wybierz pozycję Przeglądaj** , aby znaleźć i przekazać sformatowany plik programu Excel zawierający wszystkie wymagane dane szablonu.

8. Jeśli nie występują żadne problemy z plikiem, na następnym ekranie zostanie pokazana nazwa przekazanego pliku. Wybierz **pozycję** Dalej, aby kontynuować (jeśli chcesz zmienić plik, wybierz pozycję **Przekaż inny plik**).

    - Jeśli występuje problem z plikiem, u góry zostanie wyświetlony komunikat o błędzie informujący o tym, co się stało. Musisz naprawić i ponownie przekazać plik. Błędy będą się pojawiać, jeśli arkusz kalkulacyjny został nieprawidłowo sformatowany lub w niektórych polach występują nieprawidłowe informacje.

9. Ekran **Recenzja i zakończenie** zawiera liczbę akcji udoskonalania i kontrolek oraz maksymalną liczbę wyników dla szablonu. Gdy wszystko będzie gotowe do zatwierdzenia, wybierz pozycję **Dalej**. (Jeśli chcesz wprowadzić zmiany, wybierz **pozycję Przekaż inny plik**).

10. Ostatni ekran potwierdza, że został utworzony nowy szablon. Wybierz **pozycję Gotowe** , aby zamknąć kreatora.

11. Otrzymasz stronę szczegółów nowego szablonu. W tym miejscu możesz utworzyć swój ocenianie, wybierając **pozycję Utwórz ocena**. Aby uzyskać wskazówki, zobacz [Tworzenie ocen i zarządzanie nimi](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Rozszerzanie uniwersalnych szablonów oceniania

Wersje uniwersalne szablonów można również rozszerzyć, aby dostosować oceny dla poszczególnych produktów. Podczas tworzenia oceny przy użyciu szablonu uniwersalnego otrzymasz specjalny szablon rozszerzenia, a ocena ma unikatowy produkt i kombinację certyfikatów. Ten plik można zmodyfikować odpowiednio do potrzeb. Aby uzyskać wskazówki dotyczące edytowania szablonu, zobacz instrukcje dotyczące [modyfikowania szablonu](compliance-manager-templates-modify.md).

Podczas edytowania szablonu uniwersalnego cała zawartość szablonu może być zmieniana, ale spowoduje to przerwę w dziedziczeniu przy użyciu szablonu nadrzędnego. Oznacza to, że nie będzie już automatycznie otrzymywać aktualizacji od firmy Microsoft, jeśli szablon nadrzędny zostanie odświeżony.
