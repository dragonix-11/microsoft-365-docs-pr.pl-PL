---
title: Ręczne zmienianie planów platformy Microsoft 365 dla firm
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: nalinkla, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid: MET150
description: Ręcznie zmień subskrypcje, kupując nową subskrypcję i upewniając się, że obie subskrypcje są wyświetlane i aktywne.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: 5e2d9e3da47c8d9c86e3e0b6d3d0b648c6016509
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493558"
---
# <a name="manually-change-microsoft-plans"></a>Ręczne zmienianie planów firmy Microsoft

## <a name="step-1-decide-how-to-change-plans"></a>Krok 1. Podejmowanie decyzji o zmianie planów

Najlepszym sposobem zmiany wszystkich użytkowników z jednego planu na inny jest [użycie karty Uaktualnij](upgrade-to-different-plan.md). Czasami nie jest to możliwe. Zamiast tego zmień plany ręcznie:

- Jeśli karta **Uaktualnij** wskazuje, że nie można uaktualnić bieżącego planu.

- Jeśli po wybraniu karty **Uaktualnianie** żądanego planu nie ma na liście.

- Jeśli nie chcesz uaktualniać wszystkich użytkowników w ten sam sposób. Niektóre firmy potrzebują różnych użytkowników subskrybowanych w różnych planach. W tym celu użyj ręcznej zmiany.

Aby kontynuować ręczną zmianę, przeczytaj [krok 2. Kupowanie nowej subskrypcji](#step-2-buy-a-new-subscription) w tym temacie.

> [!IMPORTANT]
> Jeśli zmieniasz plan z mniejszą liczbą usług związanych z danymi niż bieżący plan (obniżenie poziomu), musisz ręcznie utworzyć kopię zapasową wszystkich danych, które chcesz zachować. Aby uzyskać więcej informacji, zobacz [Tworzenie kopii zapasowej danych przed zmianą planów](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>Krok 2. Kupowanie nowej subskrypcji

**Masz już zakupione?** Jeśli masz już subskrypcję, do którą chcesz przenieść użytkowników, pomiń ten krok i przejdź do [kroku 3. Sprawdź nową subskrypcję i licencje w tym temacie](#step-3-check-your-new-subscription-and-licenses) .

LUB

**Kup nową subskrypcję i licencje:** Wykonaj kroki opisane w temacie [Kupowanie kolejnej subskrypcji platformy Microsoft 365 dla firm](../try-or-buy-microsoft-365.md) , aby kupić nową subskrypcję.

Upewnij się, że zakupiono subskrypcję dla tej samej organizacji, w którą obecnie znajdują się użytkownicy. Na przykład sprawdź adresy e-mail użytkowników, którzy mają zostać przeniesień. Jeśli ich adresy e-mail obejmują \@contoso.com, musisz kupić nową subskrypcję dla contoso.com.
Dołącz licencję dla każdego użytkownika, który chcesz przenieść.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Krok 3. Sprawdzanie nowej subskrypcji i licencji

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.

2. **Sprawdź, czy obie subskrypcje są wyświetlane i aktywne** Subskrypcja, z której przenosisz użytkowników, oraz subskrypcja, do której przenosisz użytkowników, muszą być wymienione razem. Jeśli podczas pierwszego sprawdzania nowej subskrypcji nie ma, spróbuj ponownie później. Sprawdź, czy obie subskrypcje są aktywne. [Nowa subskrypcja nie jest wyświetlana na liście lub nie jest aktywna](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Sprawdź, czy masz wystarczającą liczbę licencji dla każdego użytkownika** Każdy użytkownik musi mieć licencję zgodną ze swoją subskrypcją. Jeśli więc chcesz przenieść dziesięciu użytkowników do Microsoft 365 Business Premium, musisz upewnić się, że dostępnych jest dziesięć licencji.

4. **Potrzebujesz więcej licencji dla nowej subskrypcji?**
   Przejdź do strony **Twoje produkty** i [kup więcej licencji](../licenses/buy-licenses.md).

> [Co ze starymi licencjami?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Nowa subskrypcja nie jest wyświetlana na liście lub nie jest aktywna

- **Jeśli zakupiono dwie subskrypcje i nie są one wymienione w tym miejscu**, mogły zostać zakupione dla różnych organizacji (dla różnych domen). Subskrypcje nie mogą przekraczać granic organizacji.

- **Jeśli wiesz, że masz dodatkową subskrypcję** i nie jest ona wymieniona w tym miejscu lub nie jest aktywna, [zadzwoń do pomocy technicznej firmy Microsoft](../../admin/get-help-support.md).

### <a name="what-about-the-old-licenses"></a>Co ze starymi licencjami?

Licencje dla bieżącej subskrypcji zostaną usunięte później. Od tego czasu płacisz tylko za nowe licencje użytkowników.

## <a name="step-4-reassign-licenses"></a>Krok 4. Ponowne przypisywanie licencji

Podczas uaktualniania z planu Office 365 do planu platformy Microsoft 365 należy zmienić przypisania licencji dla wszystkich użytkowników. Licencje nie są przypisywane automatycznie podczas ręcznej zmiany planów.

### <a name="reassign-a-license-for-one-user"></a>Ponowne przypisywanie licencji dla jednego użytkownika

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Na stronie **Aktywni użytkownicy** wybierz użytkownika, któremu chcesz przypisać licencję.

3. Na **karcie Licencje i aplikacje** rozwiń węzeł **Licencje**, wybierz pola licencji, które chcesz przypisać, a następnie wybierz pozycję **Zapisz zmiany**.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Ponowne przypisywanie licencji dla wielu użytkowników jednocześnie

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Wybierz okręgi obok nazw użytkowników, dla których chcesz zastąpić istniejące licencje.

3. U góry wybierz trzy kropki (więcej akcji), a następnie wybierz pozycję **Zarządzaj licencjami produktów**.

4. Wybierz pozycję **Zastąp istniejące przypisania licencji produktów** \> **Dalej**.

5. Przełącz przełącznik na pozycję **Włączone** dla produktów, które chcesz przypisać do tych użytkowników.

    > [!TIP]
    > - Aby ograniczyć, które usługi są dostępne dla użytkownika, przełącz się do pozycji **Wyłączone** dla usług, które chcesz usunąć dla tego użytkownika. Jeśli na przykład chcesz, aby użytkownik miał dostęp do wszystkich dostępnych usług z wyjątkiem Skype dla firm Online, możesz przełączyć przełącznik dla usługi Skype dla firm Online na pozycję **Wyłączone**.
    > - Zostaną usunięte wszystkie poprzednie przypisania licencji dla wybranych użytkowników.

6. U dołu okienka **Zastąp istniejące produkty** wybierz pozycję **Zastąp** \> **Zamknij**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Krok 5. Anulowanie subskrypcji lub usunięcie niepotrzebnych licencji (opcjonalnie)

Jeśli wszyscy użytkownicy zostali przeniesieni z jednej subskrypcji do innej i nie potrzebujesz już oryginalnej subskrypcji, możesz [anulować tę subskrypcję](cancel-your-subscription.md).

Jeśli przeniesiono tylko niektórych użytkowników do innej subskrypcji, [usuń licencje](../licenses/buy-licenses.md) , których już nie potrzebujesz.

## <a name="call-support-to-help-you-change-plans"></a>Zadzwoń do pomocy technicznej, aby ułatwić zmianę planów

[Zadzwoń do pomocy technicznej firmy Microsoft](../../admin/get-help-support.md).
