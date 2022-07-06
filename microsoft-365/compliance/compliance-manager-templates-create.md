---
title: Tworzenie szablonów oceny w programie Microsoft Purview Compliance Manager
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
description: Dowiedz się, jak tworzyć szablony dla ocen w programie Microsoft Purview Compliance Manager. Tworzenie i modyfikowanie szablonów przy użyciu sformatowanego pliku programu Excel.
ms.openlocfilehash: f7198d9b7bb9c30d388924d9c1b16a79e86bb8ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638669"
---
# <a name="create-an-assessment-template-in-microsoft-purview-compliance-manager"></a>Tworzenie szablonu oceny w programie Microsoft Purview Compliance Manager

Aby utworzyć własny nowy szablon dla ocen niestandardowych w Menedżerze zgodności, użyjesz specjalnie sformatowanego arkusza kalkulacyjnego programu Excel do zmontowania niezbędnych danych kontrolnych. Po ukończeniu arkusza kalkulacyjnego zaimportujesz go do Menedżera zgodności.

Aby dowiedzieć się więcej na temat formatowania arkusza kalkulacyjnego, zobacz [Formatowanie danych szablonu oceny w programie Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>Wymagane role

Szablony mogą tworzyć i modyfikować tylko użytkownicy z rolą administratora globalnego lub administratora programu Compliance Manager. Dowiedz się więcej o [rolach i uprawnieniach](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>Tworzenie nowego szablonu w menedżerze zgodności

1. Przejdź do strony **szablonów oceny** w Menedżerze zgodności.
2. Wybierz pozycję **Utwórz nowy szablon**. Zostanie otwarty kreator tworzenia szablonu.
3. Wybierz typ szablonu, który chcesz utworzyć. W takim przypadku wybierz pozycję **Utwórz szablon niestandardowy**, a następnie wybierz pozycję **Dalej**.
4. Na ekranie **Przekazywanie pliku** wybierz pozycję **Przeglądaj** , aby znaleźć i przekazać sformatowany plik programu Excel zawierający wszystkie wymagane dane szablonu.
5. Jeśli nie ma żadnych problemów z plikiem, zostanie wyświetlona nazwa przekazanego pliku. Wybierz przycisk **Dalej**, aby kontynuować. (Jeśli musisz zmienić plik, wybierz pozycję **Przekaż inny plik**).
    - Jeśli wystąpił błąd z plikiem, u góry znajduje się komunikat o błędzie wyjaśniający, co jest nie tak. Musisz naprawić plik i przekazać go ponownie. Błędy spowodują nieprawidłowe formatowanie arkusza kalkulacyjnego lub nieprawidłowe informacje w niektórych polach.
6. Na ekranie **Przeglądanie i zakończenie** jest wyświetlana liczba akcji i kontrolek poprawy oraz maksymalny wynik szablonu. Gdy wszystko będzie gotowe do zatwierdzenia, wybierz pozycję **Utwórz szablon.** (Jeśli musisz wprowadzić zmiany, wybierz pozycję **Wstecz**).
7. Ostatni ekran potwierdza, że został utworzony nowy szablon. Wybierz pozycję **Gotowe** , aby zamknąć kreatora.
8. Zostanie wyświetlona strona szczegółów nowego szablonu, na której można [utworzyć ocenę](compliance-manager-assessments.md#create-assessments).
