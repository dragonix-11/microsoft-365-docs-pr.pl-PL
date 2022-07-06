---
title: Rozszerzanie szablonów oceny w programie Microsoft Purview Compliance Manager
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
description: Dowiedz się, jak rozszerzyć szablony oceny w programie Microsoft Purview Compliance Manager, aby dodawać i modyfikować kontrolki.
ms.openlocfilehash: b4cf642e7b5a9dac47cd513251c05a802f16b77b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630460"
---
# <a name="extend-assessment-templates-in-microsoft-purview-compliance-manager"></a>Rozszerzanie szablonów oceny w programie Microsoft Purview Compliance Manager

Menedżer zgodności oferuje opcję dodawania własnych kontrolek i akcji ulepszania do istniejącego szablonu. Ten proces jest nazywany rozszerzaniem szablonu.

Aby rozszerzyć szablon, należy użyć specjalnych instrukcji dotyczących modyfikowania danych szablonu w zależności od tego, czy rozszerzasz szablony oceny firmy Microsoft, czy szablony oceny uniwersalnej.

## <a name="extend-microsoft-assessment-templates"></a>Rozszerzanie szablonów oceny firmy Microsoft

Po rozszerzeniu szablonu firmy Microsoft, takiego jak utworzony do użycia z platformą Microsoft 365, nadal może on otrzymywać aktualizacje wydane przez firmę Microsoft. Aktualizacje może wystąpić w przypadku wprowadzenia zmian w powiązanym rozporządzeniu lub produkcie (zobacz [Akceptowanie aktualizacji ocen](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Przygotowywanie danych szablonu i tworzenie rozszerzenia

Aby się przygotować, należy utworzyć specjalnie sformatowany arkusz kalkulacyjny programu Excel w celu zaimportowania niezbędnych danych szablonu. Pliki programu Excel mają ten sam format opisany w [temacie Formatuj dane szablonu oceny w programie Excel](compliance-manager-templates-format-excel.md), ale istnieją specjalne wymagania dotyczące rozszerzeń. Zapoznaj się z tymi dodatkowymi punktami, aby zapobiec błędom:

- Arkusz kalkulacyjny powinien zawierać tylko akcje i kontrolki, które chcesz dodać do oceny.
- Arkusz kalkulacyjny nie może zawierać żadnych kontrolek ani akcji, które już istnieją w ocenie, którą chcesz zmodyfikować.
- Rozważ uwzględnienie "rozszerzenia" w tytule szablonu, na przykład "RODO — rozszerzenie [nazwa firmy]". Ułatwia to identyfikację na liście na stronie **szablonów oceny** w odróżnieniu od standardowego szablonu dostarczonego przez firmę Microsoft lub szablonu niestandardowego o podobnej nazwie.

Po sformatowaniu arkusza kalkulacyjnego wykonaj poniższe kroki.

1. Przejdź do strony **Szablony oceny** i wybierz pozycję **Utwórz nowy szablon**. Zostanie otwarty kreator tworzenia szablonu.

2. Wybierz typ szablonu, który chcesz utworzyć. W takim przypadku wybierz **pozycję Rozszerz szablon firmy Microsoft**, a następnie **wybierz pozycję Szablon firmy Microsoft**.

3. Po prawej stronie ekranu zostanie wyświetlone okienko wysuwane wyboru szablonu z listą wszystkich szablonów i ich stanem aktywnym lub nieaktywnym. Licznik **aktywowanych szablonów** pokazuje, ile szablonów jest obecnie używanych z łącznej liczby dostępnych do użycia. Jeśli przekraczasz limit, zostanie wyświetlone powiadomienie na pasku komunikatów.

4. Po prawej stronie ekranu zostanie wyświetlone okienko wysuwane wyboru szablonu. Użyj **funkcji Wyszukaj** , aby zastosować filtry do lokalizowania żądanego szablonu

5. Po zlokalizowaniu szablonu wybierz przycisk radiowy po lewej stronie jego nazwy, a następnie wybierz pozycję **Zapisz**.

6. Na następnym ekranie zostanie wyświetlony wybrany szablon. Jeśli jest to poprawne, wybierz przycisk **Dalej**. (Jeśli jest to niepoprawne, wybierz **pozycję Wybierz inny szablon** do wyboru ponownie).

7. Na ekranie **Przekazywanie pliku** wybierz pozycję **Przeglądaj** , aby znaleźć i przekazać sformatowany plik programu Excel zawierający wszystkie wymagane dane szablonu.

8. Jeśli nie ma żadnych problemów z plikiem, na następnym ekranie zostanie wyświetlona nazwa przekazanego pliku. Wybierz pozycję **Dalej** , aby kontynuować (jeśli chcesz zmienić plik, wybierz pozycję **Przekaż inny plik**).

    - Jeśli wystąpił problem z plikiem, u góry znajduje się komunikat o błędzie wyjaśniający, co jest nie tak. Musisz naprawić i ponownie przekazać plik. Błędy spowodują nieprawidłowe formatowanie arkusza kalkulacyjnego lub nieprawidłowe informacje w niektórych polach.

9. Na ekranie **Przeglądanie i zakończenie** jest wyświetlana liczba akcji i kontrolek poprawy oraz maksymalny wynik szablonu. Gdy wszystko będzie gotowe do zatwierdzenia, wybierz pozycję **Dalej**. (Jeśli musisz wprowadzić zmiany, wybierz pozycję **Przekaż inny plik**).

10. Ostatni ekran potwierdza, że został utworzony nowy szablon. Wybierz pozycję **Gotowe** , aby zamknąć kreatora.

11. Zobaczysz stronę szczegółów nowego szablonu. W tym miejscu możesz utworzyć ocenę, wybierając pozycję **Utwórz ocenę**. Aby uzyskać wskazówki, zobacz [Tworzenie ocen i zarządzanie nimi](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Rozszerzanie szablonów oceny uniwersalnej

Uniwersalne wersje szablonów można również rozszerzyć, aby dostosować oceny specyficzne dla produktu. Podczas tworzenia oceny przy użyciu szablonu uniwersalnego otrzymasz specjalny szablon rozszerzenia, a ocena ma unikatową kombinację produktów i certyfikacji. Ten plik można zmodyfikować w celu spełnienia twoich potrzeb. Aby uzyskać wskazówki dotyczące edytowania szablonu, zobacz instrukcje dotyczące [modyfikowania szablonu](compliance-manager-templates-modify.md).

Podczas edytowania szablonu uniwersalnego można zmienić całą zawartość szablonu, ale spowoduje to przerwanie dziedziczenia za pomocą szablonu nadrzędnego. Oznacza to, że nie będzie już automatycznie otrzymywać aktualizacji od firmy Microsoft, jeśli szablon nadrzędny zostanie odświeżony.
