---
title: Odbieranie licencji użytkownikom
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_smb
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Metoda używana do cofania przypisania licencji produktów zależy od tego, czy nie przypisano licencji od określonych użytkowników, czy od określonego produktu.
ms.date: 09/16/2021
ms.openlocfilehash: 8d0fd6f89802111bdb2afbc2586392251d393e4e
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971088"
---
# <a name="unassign-licenses-from-users"></a>Odbieranie licencji użytkownikom

Licencje od użytkowników można anulować na stronie **Aktywni użytkownicy** lub na stronie **Licencje** . Używana metoda zależy od tego, czy chcesz anulować przypisanie licencji produktów od określonych użytkowników, czy cofnąć przypisanie licencji użytkowników z określonego produktu.

> [!NOTE]
> 
> - Jako administrator nie możesz przypisywać ani anulować przypisywania licencji dla subskrypcji zakupu samoobsługowego zakupionej przez użytkownika w organizacji. Możesz [przejąć subskrypcję samoobsługowego zakupu](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), a następnie przypisać lub cofnąć przypisanie licencji.
> 
> - W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli termin anulowania już minął, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej trwania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Musisz być administratorem globalnym, licencją, administratorem użytkownika, aby anulować przypisanie licencji. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratora Microsoft 365](../add-users/about-admin-roles.md).
- Możesz [usuwać licencje z kont użytkowników przy użyciu programu Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Możesz również [usunąć konta użytkowników](../add-users/delete-a-user.md) , do których przypisano licencję, aby udostępnić ich licencję innym użytkownikom. Po usunięciu konta użytkownika jego licencja jest natychmiast dostępna do przypisania innej osobie.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Użyj strony Licencje, aby anulować przypisanie licencji

W przypadku korzystania ze strony **Licencje** do cofania przypisania licencji można anulować przypisanie licencji dla określonego produktu dla maksymalnie 20 użytkowników.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Wybierz produkt, dla którego chcesz anulować przypisanie licencji.

3. Wybierz użytkowników, dla których chcesz anulować przypisanie licencji.

4. Wybierz pozycję **Usuń przypisanie licencji**.

5. W polu **Cofanie przypisania licencji** wybierz pozycję **Usuń przypisanie**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Anulowanie przypisania licencji przy użyciu strony Aktywni użytkownicy

W przypadku korzystania ze strony **Aktywni użytkownicy** do cofania przypisania licencji można anulować przypisanie licencji produktów od użytkowników.

### <a name="unassign-licenses-from-one-user"></a>Anulowanie przypisania licencji od jednego użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz wiersz użytkownika, dla który chcesz anulować przypisanie licencji.

3. W okienku po prawej stronie wybierz pozycję **Licencje i aplikacje**.

4. Rozwiń sekcję **Licencje, wyczyść** pola licencji, które chcesz anulować, a następnie wybierz pozycję **Zapisz zmiany**.

### <a name="unassign-licenses-from-multiple-users"></a>Anulowanie przypisania licencji od wielu użytkowników

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz okręgi obok nazw użytkowników, dla których chcesz anulować przypisanie licencji.

3. U góry wybierz pozycję **Zarządzaj licencjami produktów**.

4. W okienku **Zarządzanie licencjami produktów** wybierz pozycję **Usuń przypisanie** **wszystkichZapisz** >  zmiany.

5. W dolnej części okienka wybierz pozycję **Gotowe**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Co się stanie z danymi użytkownika po usunięciu licencji?

- Gdy licencja zostanie usunięta z użytkownika, Exchange dane online skojarzone z tym kontem są przechowywane przez 30 dni. Po upływie 30-dniowego okresu prolongaty dane są usuwane i nie można ich odzyskać.
- Pliki zapisane w OneDrive dla Firm nie są usuwane, chyba że użytkownik zostanie usunięty z Centrum administracyjne platformy Microsoft 365 lub zostanie usunięty w ramach synchronizacji usługi Active Directory. Aby uzyskać więcej informacji, zobacz [przechowywanie i usuwanie OneDrive](/onedrive/retention-and-deletion).
- Gdy licencja zostanie usunięta, skrzynka pocztowa użytkownika nie będzie już przeszukiwana przy użyciu narzędzia zbierania elektronicznych materiałów dowodowych, takiego jak wyszukiwanie zawartości lub zbierania elektronicznych materiałów dowodowych (Premium). Aby uzyskać więcej informacji, zobacz "Wyszukiwanie rozłączonych lub nielicenacjonowanych skrzynek pocztowych" w [wyszukiwaniu zawartości w Microsoft 365](../../compliance/content-search.md).
- Jeśli masz subskrypcję Enterprise, taką jak Office 365 Enterprise E3, Exchange Online umożliwia zachowanie danych skrzynki pocztowej usuniętego konta użytkownika przy użyciu [nieaktywnych skrzynek pocztowych](../../compliance/inactive-mailboxes-in-office-365.md). Aby uzyskać więcej informacji, zobacz [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi w Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Aby dowiedzieć się, jak zablokować użytkownikowi dostęp do danych Microsoft 365 po usunięciu licencji oraz jak uzyskać dostęp do danych później, zobacz [Usuwanie byłego pracownika](../add-users/remove-former-employee.md).
- Jeśli usuniesz licencję użytkownika i nadal masz zainstalowane aplikacje Office, podczas korzystania z aplikacji Office będą widoczne [błędy nielicencjonowanego produktu i aktywacji w Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

## <a name="next-steps"></a>Następne kroki

Jeśli nie zamierzasz [ponownie przypisywać nieużywanych licencji innym użytkownikom](../../managed-desktop/get-started/assign-licenses.md), rozważ [usunięcie licencji z subskrypcji](../../commerce/licenses/buy-licenses.md) , aby nie płacić za więcej licencji, niż potrzebujesz.

## <a name="related-content"></a>Zawartość pokrewna

[Usuwanie licencji z subskrypcji](../../commerce/licenses/buy-licenses.md) (artykuł)\
[Przypisywanie licencji do użytkowników](assign-licenses-to-users.md) (artykuł)\
[Omówienie subskrypcji i licencji w usłudze Microsoft 365 dla firm](../../commerce/licenses/subscriptions-and-licenses.md) (artykuł)
