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
ms.date: 06/23/2022
ms.openlocfilehash: 87e62b8c39e5ba0a8f61caeea3560438a716881d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486181"
---
# <a name="unassign-microsoft-365-licenses-from-users"></a>Anulowanie przypisywania licencji platformy Microsoft 365 od użytkowników

Licencje od użytkowników można anulować na stronie **Aktywni użytkownicy** lub na stronie **Licencje** . Używana metoda zależy od tego, czy chcesz anulować przypisanie licencji produktów od określonych użytkowników, czy cofnąć przypisanie licencji użytkowników z określonego produktu.

> [!NOTE]
> 
> - Jako administrator nie możesz przypisywać ani anulować przypisywania licencji dla subskrypcji zakupu samoobsługowego zakupionej przez użytkownika w organizacji. Możesz [przejąć subskrypcję samoobsługowego zakupu](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), a następnie przypisać lub cofnąć przypisanie licencji.
> 
> - W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli termin anulowania już minął, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej trwania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Musisz być administratorem globalnym, licencją, administratorem użytkownika, aby anulować przypisanie licencji. Aby uzyskać więcej informacji, zobacz [About Microsoft 365 admin roles (Informacje o rolach administratora platformy Microsoft 365](../add-users/about-admin-roles.md)).
- Możesz [usuwać licencje z kont użytkowników przy użyciu programu Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Możesz również [usunąć konta użytkowników](../add-users/delete-a-user.md) , do których przypisano licencję, aby udostępnić ich licencję innym użytkownikom. Po usunięciu konta użytkownika jego licencja jest natychmiast dostępna do przypisania innej osobie.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Użyj strony Licencje, aby anulować przypisanie licencji

Strona **Licencje** umożliwia przypisywanie lub cofanie przypisania licencji dla maksymalnie 20 użytkowników jednocześnie. Na stronie przedstawiono posiadane produkty, liczbę dostępnych licencji dla każdego produktu oraz liczbę przypisanych licencji z łącznej liczby dostępnych licencji. Liczba licencji to łączna suma licencji dla wszystkich subskrypcji dla tej samej nazwy produktu.

Na przykład możesz mieć jedną subskrypcję dla Microsoft 365 Business Premium, która ma 5 licencji, i inną subskrypcję, która ma 8 licencji na ten sam produkt. Strona **Licencje** pokazuje, że masz łącznie 13 licencji na Microsoft 365 Business Premium we wszystkich subskrypcjach. Różni się to od tego, co widać na stronie **Twoje produkty** , która wyświetla wiersz dla każdej posiadanej subskrypcji, nawet jeśli są one dla tego samego produktu.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

1. Wybierz produkt.

2. Zaznacz pola wyboru użytkowników, dla których chcesz anulować przypisanie licencji.

3. Wybierz pozycję **Usuń przypisanie licencji**.

4. W polu **Cofanie przypisania licencji** wybierz pozycję **Usuń przypisanie**.

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

4. W okienku **Zarządzanie licencjami produktów** wybierz pozycję **Usuń przypisanie wszystkich zapisanych** > **zmian**.

5. W dolnej części okienka wybierz pozycję **Gotowe**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Co się stanie z danymi użytkownika po usunięciu licencji?

- Po usunięciu licencji z użytkownika Exchange Online dane skojarzone z tym kontem są przechowywane przez 30 dni. Po upływie 30-dniowego okresu prolongaty dane są usuwane i nie można ich odzyskać. Jest ona jednak połączona z zasadami przechowywania, a zawartość zgodna z etykietami przechowywania jest zachowywana na potrzeby odnajdywania.
- Pliki zapisane w OneDrive dla Firm nie są usuwane, chyba że użytkownik zostanie usunięty z Centrum administracyjne platformy Microsoft 365 lub zostanie usunięty w ramach synchronizacji usługi Active Directory. Aby uzyskać więcej informacji, zobacz [Przechowywanie i usuwanie usługi OneDrive](/onedrive/retention-and-deletion).
- Po usunięciu licencji skrzynka pocztowa użytkownika nie jest już przeszukiwana przy użyciu narzędzia zbierania elektronicznych materiałów dowodowych, takiego jak wyszukiwanie zawartości lub elektroniczne wykrywanie (Premium). Aby uzyskać więcej informacji, zobacz "Wyszukiwanie rozłączonych lub nielicenacjonowanych skrzynek pocztowych" w [usłudze Content Search na platformie Microsoft 365](../../compliance/content-search.md).
- Jeśli masz subskrypcję enterprise, taką jak Office 365 Enterprise E3, Exchange Online umożliwia zachowanie danych skrzynki pocztowej usuniętego konta użytkownika przy użyciu [nieaktywnych skrzynek pocztowych](../../compliance/inactive-mailboxes-in-office-365.md). Aby uzyskać więcej informacji, zobacz [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi w Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Aby dowiedzieć się, jak zablokować użytkownikowi dostęp do danych platformy Microsoft 365 po usunięciu licencji oraz jak uzyskać dostęp do danych, zobacz [Usuwanie byłego pracownika](../add-users/remove-former-employee.md).
- Jeśli usuniesz licencję użytkownika i nadal masz zainstalowane aplikacje pakietu Office, podczas korzystania z aplikacji pakietu Office będą widoczne [błędy nielicencjonowanego produktu i aktywacji w](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) pakiecie Office.

## <a name="next-steps"></a>Następne kroki

Jeśli nie zamierzasz [ponownie przypisywać nieużywanych licencji innym użytkownikom](../../managed-desktop/get-started/assign-licenses.md), rozważ [usunięcie licencji z subskrypcji](../../commerce/licenses/buy-licenses.md) , aby nie płacić za więcej licencji, niż potrzebujesz.

## <a name="related-content"></a>Zawartość pokrewna

[Usuwanie licencji z subskrypcji](../../commerce/licenses/buy-licenses.md) (artykuł)\
[Przypisywanie licencji do użytkowników](assign-licenses-to-users.md) (artykuł)\
[Omówienie subskrypcji i licencji w usłudze Microsoft 365 dla firm](../../commerce/licenses/subscriptions-and-licenses.md) (artykuł)
