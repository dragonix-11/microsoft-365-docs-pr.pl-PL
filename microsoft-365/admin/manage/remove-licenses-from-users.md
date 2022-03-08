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
description: Metoda, za pomocą która służy do nieprzypisania licencji produktu, zależy od tego, czy licencje są nieprzypisane określonym użytkownikom, czy z konkretnego produktu.
ms.date: 09/16/2021
ms.openlocfilehash: 7308888c54a30cdd11618cb07a233f8bd55f27c2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321211"
---
# <a name="unassign-licenses-from-users"></a>Odbieranie licencji użytkownikom

Możesz nieprzypisać licencje użytkownikom na stronie Aktywni użytkownicy  lub **na stronie Licencje**. Metoda, której używasz, zależy od tego, czy chcesz usunąć licencje na produkty od konkretnych użytkowników, czy też usunąć przypisanie licencji użytkowników z określonego produktu.

> [!NOTE]
> 
> - Jako administrator nie możesz przypisywać ani anulować przypisania licencji na subskrypcję zakupu samoobsługowego zakupową zakupioną przez użytkownika w Organizacji. Możesz [przejąć subskrypcję zakupu samoobsługowego, a](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) następnie przypisać lub anulować przypisanie licencji.
> 
> - W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli okno anulowania już minęło, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej zakończenia.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby nieprzypisać licencje, musisz być administratorem globalnym, licencją i administratorem użytkownika. Aby uzyskać więcej informacji, zobacz [Informacje Microsoft 365 administratorów](../add-users/about-admin-roles.md).
- Możesz [usuwać licencje z kont użytkowników przy użyciu programu Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Możesz również usunąć [konta użytkowników](../add-users/delete-a-user.md) , do których przypisano licencję, aby udostępnić tę licencję innym użytkownikom. Po usunięciu konta użytkownika jego licencja jest od razu dostępna do przypisania innej osobie.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Używanie strony Licencje do nieprzypisywania licencji

Gdy używasz strony **Licencje** , aby nieprzypisać licencje, możesz nieprzypisać licencje dla konkretnego produktu dla maksymalnie 20 użytkowników.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

2. Wybierz produkt, dla którego chcesz usunąć przypisanie licencji.

3. Wybierz użytkowników, dla których chcesz usunąć przypisanie licencji.

4. Wybierz **pozycję Co umożliwia nieprzypis licencji**.

5. W **polu Nieprzypisaj licencje** wybierz pozycję **Nieprzypisz**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Używanie strony Aktywni użytkownicy do nieprzypisywania licencji

Gdy używasz strony **Aktywni użytkownicy** , aby nieprzypisać licencje, licencje produktu są nieprzypisane użytkownikom.

### <a name="unassign-licenses-from-one-user"></a>Cossign licenses from one user

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Zaznacz wiersz użytkownika, dla którego chcesz usunąć przypisanie licencji.

3. W okienku po prawej stronie wybierz pozycję **Licencje i aplikacje**.

4. Rozwiń **sekcję Licencje** , wyczyść pola licencji, które chcesz usunąć, a następnie wybierz pozycję **Zapisz zmiany**.

### <a name="unassign-licenses-from-multiple-users"></a>Co umożliwia nieprzypisane licencje wielu użytkowników

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz kółka obok nazw użytkowników, dla których chcesz usunąć licencje.

3. U góry wybierz pozycję **Zarządzaj licencjami produktów**.

4. W **okienku Zarządzanie licencjami produktów** wybierz pozycję **Cognuj przypisanie** **wszystkichZapisuj** >  zmiany.

5. U dołu okienka wybierz pozycję **Gotowe**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Co się dzieje z danymi użytkownika po usunięciu jego licencji?

- Po usunięciu licencji użytkownikowi wszystkie Exchange online skojarzone z tym kontem są przechowywane przez 30 dni. Po upływie 30-dniowego okresu prolongaty dane są usuwane i nie można ich odzyskać.
- Pliki zapisane w OneDrive dla Firm nie są usuwane, chyba że użytkownik zostanie usunięty z centrum administracyjne platformy Microsoft 365 synchronizacji z usługą Active Directory. Aby uzyskać więcej informacji, [zobacz OneDrive i usuwanie](/onedrive/retention-and-deletion).
- Po usunięciu licencji nie będzie już można wyszukiwać skrzynki pocztowej użytkownika za pomocą narzędzia zbierania elektronicznych materiałów dowodowych, takiego jak Przeszukiwanie zawartości Advanced eDiscovery. Aby uzyskać więcej informacji, zobacz "Wyszukiwanie odłączonych lub odłączonych skrzynek pocztowych" w te sposób: [Wyszukiwanie zawartości w programie Microsoft 365](../../compliance/content-search.md).
- Jeśli masz subskrypcję usługi Enterprise, na przykład Office 365 Enterprise E3, program Exchange Online umożliwia zachowanie danych skrzynki pocztowej usuniętego konta użytkownika przy użyciu nieaktywnych [skrzynek pocztowych](../../compliance/inactive-mailboxes-in-office-365.md). Aby uzyskać więcej informacji, zobacz [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi w programie Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Aby dowiedzieć się, jak zablokować użytkownikowi dostęp do danych Microsoft 365 po usunięciu jego licencji i jak później uzyskać dostęp do tych danych, zobacz Usuwanie [byłego pracownika](../add-users/remove-former-employee.md).
- Jeśli usuniesz licencję użytkownika i nadal będzie mieć zainstalowane aplikacje pakietu Office, zobaczą oni błędy "Produkt bez licencji" i błędy aktywacji w aplikacji [Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380), gdy korzystają oni Office aplikacji.

## <a name="next-steps"></a>Następne kroki

Jeśli nie zamierzasz ponownie ponownie nieprzypisać nieużywanych licencji innym użytkownikom[, rozważ](../../managed-desktop/get-started/assign-licenses.md) usunięcie licencji z [](../../commerce/licenses/buy-licenses.md) subskrypcji, aby nie płacić za więcej licencji, niż potrzebujesz.

## <a name="related-content"></a>Zawartość pokrewna

[Usuwanie licencji z subskrypcji](../../commerce/licenses/buy-licenses.md) (artykuł)\
[Przypisywanie licencji użytkownikom](assign-licenses-to-users.md) (artykuł)\
[Opis subskrypcji i licencji w programie Microsoft 365 dla firm](../../commerce/licenses/subscriptions-and-licenses.md) (artykuł)
