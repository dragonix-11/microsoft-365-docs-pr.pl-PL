---
title: Tworzenie szablonów ocen w Menedżerze zgodności firmy Microsoft
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
description: Dowiedz się, jak tworzyć szablony dla ocen w Menedżerze zgodności firmy Microsoft. Tworzenie i modyfikowanie szablonów przy użyciu Excel pliku.
ms.openlocfilehash: 1c7ccbe01d3411ace40cfe6ccdbe4fcb4d90480b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316187"
---
# <a name="create-an-assessment-template-in-microsoft-compliance-manager"></a>Tworzenie szablonu oceny w Menedżerze zgodności firmy Microsoft

Aby utworzyć własny nowy szablon na potrzeby niestandardowych ocen w Menedżerze zgodności, użyj specjalnie sformatowanych arkuszy Excel kalkulacyjnych do zbierania niezbędnych danych kontrolnych. Po zakończeniu pracy z arkuszem kalkulacyjnym zaimportujesz go do Menedżera zgodności.

Aby uzyskać informacje na temat formatowania arkusza kalkulacyjnego, zobacz Formatowanie danych [szablonu oceny za pomocą Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>Wymagane role

Tylko użytkownicy, którzy mają rolę administratora globalnego lub administratora zgodności, mogą tworzyć i modyfikować szablony. Dowiedz się więcej o [rolach i uprawnieniach](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>Tworzenie nowego szablonu w Menedżerze zgodności

1. Przejdź do strony **szablonów oceniania** w Menedżerze zgodności.
2. Wybierz **pozycję Utwórz nowy szablon**. Zostanie otwarty kreator tworzenia szablonów.
3. Wybierz typ szablonu, który chcesz utworzyć. W tym przypadku wybierz pozycję **Utwórz szablon niestandardowy, a** następnie wybierz pozycję **Dalej**.
4. Na **ekranie Upload** pliku wybierz pozycję Przeglądaj, aby  znaleźć i przekazać sformatowany plik Excel zawierający wszystkie wymagane dane szablonu.
5. Jeśli nie będzie żadnych problemów z plikiem, zostanie wyświetlona nazwa przekazanego pliku. Wybierz przycisk **Dalej**, aby kontynuować. (Jeśli chcesz zmienić plik, wybierz **Upload inny plik**).
    - W przypadku wystąpienia błędu w pliku u góry zostanie wyświetlony komunikat o błędzie informujący o tym, co się stało. Musisz naprawić plik i przekazać go ponownie. Błędy będą się pojawiać, jeśli arkusz kalkulacyjny został nieprawidłowo sformatowany lub w niektórych polach występują nieprawidłowe informacje.
6. Ekran **Recenzja i zakończenie** zawiera liczbę akcji udoskonalania i kontrolek oraz maksymalną liczbę wyników dla szablonu. Gdy wszystko będzie gotowe do zatwierdzenia, wybierz **pozycję Utwórz szablon.** (Jeśli chcesz wprowadzić zmiany, wybierz pozycję **Wstecz**).
7. Ostatni ekran potwierdza, że został utworzony nowy szablon. Wybierz **pozycję Gotowe** , aby zamknąć kreatora.
8. Zostanie do Ciebie przyjedzie strona ze szczegółami nowego szablonu, na której możesz [utworzyć ocenę](compliance-manager-assessments.md#create-assessments).
