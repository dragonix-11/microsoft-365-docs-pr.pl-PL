---
title: Ręczne Microsoft 365 dla firm
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
search.appverid: MET150
description: Możesz zmienić subskrypcję ręcznie, kupując nową subskrypcję i upewniając się, że obie subskrypcje są wymienione i aktywne.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: 12ff6bdec77e6407d1b854dc7a5fd78f0401c253
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012478"
---
# <a name="change-plans-manually"></a>Ręczne zmienianie planów

## <a name="step-1-decide-how-to-change-plans"></a>Krok 1. Podjęcie decyzji o tym, jak zmienić plany

Najlepszym sposobem na zmianę wszystkich użytkowników z jednego planu do drugiego jest użycie [karty Uaktualnianie](upgrade-to-different-plan.md). Czasami nie jest to możliwe. Zamiast tego zmień plany ręcznie:

- Jeśli karta **Uaktualnianie** wskazuje, że nie można uaktualnić bieżącego planu.

- Jeśli wybierzesz kartę **Uaktualnij** , odpowiedniego planu nie ma na liście.

- Jeśli nie chcesz uaktualniać wszystkich użytkowników w ten sam sposób. Niektóre firmy potrzebują różnych użytkowników z subskrypcją różnych planów. W tym celu należy użyć zmiany ręcznej.

Aby kontynuować ręczne zmienianie, przeczytaj [Krok 2. Kupowanie nowej subskrypcji w](#step-2-buy-a-new-subscription) tym temacie.

> [!IMPORTANT]
> Jeśli zmieniasz plan z mniejszą liczbą usług związanych z danymi niż bieżący plan (ocenianie), musisz ręcznie utworzyć kopię zapasową wszystkich danych, które chcesz zachować. Aby uzyskać więcej informacji, zobacz [Temat Kopii zapasowej danych przed zmianą planów](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>Krok 2. Kupowanie nowej subskrypcji

**Masz już kupione?** Jeśli masz już subskrypcję, do której chcesz przenieść użytkowników, pomiń ten krok i przejdź do kroku [3.](#step-3-check-your-new-subscription-and-licenses) Sprawdź nową subskrypcję i licencje w tym temacie.

LUB

**Kup nową subskrypcję i licencje:** Aby kupić [nową subskrypcję Microsoft 365 postępuj](../try-or-buy-microsoft-365.md) zgodnie z instrukcjami w tece Kupowanie innej subskrypcji dla firm.

Upewnij się, że kupisz subskrypcję dla tej samej organizacji, w których obecnie znajdują się użytkownicy. Na przykład sprawdź adresy e-mail użytkowników, których chcesz przenieść. Jeśli adresy e-mail \@contoso.com, musisz kupić nową subskrypcję usługi contoso.com.
Dołącz licencję dla każdego użytkownika, którego chcesz przenieść.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Krok 3. Sprawdzanie nowej subskrypcji i licencji

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">z produktami</a> .

2. **Sprawdzanie, czy obie subskrypcje są wymienione i aktywne** Subskrypcja, z których przenosisz użytkowników, i subskrypcja, do których przenosisz użytkowników, musi być wymieniona razem. Jeśli nowa subskrypcja nie zostanie wyewidencjonana podczas pierwszego sprawdzania, spróbuj ponownie później. Sprawdź, czy obie subskrypcje są aktywne. [Nowa subskrypcja nie jest wymieniona lub nie jest aktywna](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Sprawdzanie, czy masz wystarczającą ilość licencji dla każdego użytkownika** Każdy użytkownik potrzebuje licencji, która odpowiada jego subskrypcji. Jeśli chcesz przenieść dziesięciu użytkowników do Microsoft 365 Business Premium, musisz upewnić się, że jest dostępnych dziesięć licencji.

4. **Potrzebujesz większej liczby licencji na nową subskrypcję?**
   Przejdź do **strony Twoje produkty** i [kup więcej licencji](../licenses/buy-licenses.md).

> [Co ze starymi licencjami?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Nowa subskrypcja nie jest wymieniona lub nie jest aktywna

- **Jeśli zakupiono dwie subskrypcje** i nie wymieniono ich obu tutaj, być może zostały one kupione dla różnych organizacji (dla różnych domen). Subskrypcje nie mogą przekraczać granic organizacji.

- **Jeśli wiesz, że masz dodatkową subskrypcję** i nie ma jej na liście lub nie jest ona aktywna, zadzwoń do [pomocy technicznej firmy Microsoft](../../admin/get-help-support.md).

### <a name="what-about-the-old-licenses"></a>Co ze starymi licencjami?

Licencje dla bieżącej subskrypcji zostaną później usunięte. od tego czasu zapłacisz tylko za nowe licencje użytkowników.

## <a name="step-4-reassign-licenses"></a>Krok 4. Ponowne przypisanie licencji

W przypadku uaktualnienia z Office 365 do planu Microsoft 365 musisz zmienić przypisania licencji dla wszystkich użytkowników. Licencje nie są przypisywane automatycznie po ręcznej zmianie planów.

### <a name="reassign-a-license-for-one-user"></a>Ponowne przypisanie licencji dla jednego użytkownika

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Na **stronie Aktywni** użytkownicy wybierz użytkownika, do którego chcesz przypisać licencję.

3. Na karcie **Licencje i aplikacje** rozwiń pozycję **Licencje, zaznacz** pola licencji, które chcesz przypisać, a następnie wybierz **pozycję Zapisz zmiany**.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Ponowne przypisanie licencji dla wielu użytkowników jednocześnie

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Wybierz kółka obok nazw użytkowników, dla których chcesz zamienić istniejące licencje.

3. U góry wybierz trzy kropki (więcej akcji), a następnie wybierz pozycję **Zarządzaj licencjami produktów**.

4. Wybierz pozycję **Zastąp istniejące przypisania licencji produktów** \> **Dalej**.

5. Przestaw przełącznik na pozycję **Włącz** dla produktów, które chcesz przypisać do tych użytkowników.

    > [!TIP]
    > - Aby ograniczyć usługi dostępne dla użytkownika, przestaw przełączniki na pozycję Wyłączone dla usług,  które chcesz usunąć dla tego użytkownika. Jeśli na przykład chcesz, aby użytkownik miał dostęp do wszystkich dostępnych usług oprócz usługi Skype dla firm Online, możesz ustawić przełącznik dla usługi Skype dla firm Online na **pozycję Wyłączone.**
    > - Zostaną usunięte wszystkie poprzednie przypisania licencji dla wybranych użytkowników.

6. U dołu okienka **Zastąp istniejące produkty** wybierz pozycję **Zastąp** \> **Zamknij**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Krok 5. Anulowanie subskrypcji lub usuwanie licencji, które nie są już potrzebne (opcjonalnie)

Jeśli wszyscy użytkownicy zostali przeniesieni z jednej subskrypcji do innej i nie potrzebujesz już oryginalnej subskrypcji, możesz [anulować tę subskrypcję](cancel-your-subscription.md).

Jeśli do innej subskrypcji przeniesiono tylko niektórych użytkowników, usuń [licencje](../licenses/buy-licenses.md) , których już nie potrzebujesz.

## <a name="call-support-to-help-you-change-plans"></a>Zadzwoń do pomocy technicznej, aby pomóc Ci w zmianie planów

[Zadzwoń do pomocy technicznej firmy Microsoft](../../admin/get-help-support.md).
