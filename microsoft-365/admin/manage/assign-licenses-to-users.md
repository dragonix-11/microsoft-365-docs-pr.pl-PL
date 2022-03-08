---
title: Przypisywanie licencji do użytkowników
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- TopSMBIssues
- SaRA
- business_assist
- okr_SMB
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Przypisywanie licencji zależy od tego, czy chcesz przypisać licencje produktu określonym użytkownikom, czy licencje użytkowników do określonego produktu.
ms.date: 09/16/2021
ms.openlocfilehash: dd0469288ce53ac59663e119022a204130bad3ef
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316705"
---
# <a name="assign-licenses-to-users"></a>Przypisywanie licencji do użytkowników

Możesz przypisywać licencje do użytkowników na stronie **Aktywni użytkownicy** lub na stronie **Licencje**. Metoda, której używasz, zależy od tego, czy chcesz przypisać licencje produktu określonym użytkownikom, czy licencje użytkowników do określonego produktu.

> [!NOTE]
> 
> - Jako administrator nie możesz przypisywać ani anulować przypisania licencji na subskrypcję zakupu samoobsługowego zakupową zakupioną przez użytkownika w Organizacji. Możesz [przejąć subskrypcję zakupu samoobsługowego, a](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) następnie przypisać lub anulować przypisanie licencji.
> - W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli okno anulowania już minęło, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej zakończenia.

[Dowiedz się, jak dodać użytkownika i jednocześnie przypisać mu licencję](../add-users/add-users.md).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby przypisywać licencje, musisz być globalnym, licencjonowanym lub administratorem użytkownika. Aby uzyskać więcej informacji, zobacz [Informacje Microsoft 365 administratorów](../add-users/about-admin-roles.md).
- Możesz [przypisywać Microsoft 365 do kont użytkowników za pomocą programu PowerShell](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Aby skorzystać z licencjonowania opartego na grupach, zobacz Przypisywanie licencji użytkownikom według [członkostwa w grupie w programie Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Niektóre usługi, takie jak Sway, są automatycznie przypisywane do użytkowników i nie trzeba ich przypisywać pojedynczo.


## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Używanie strony Licencje do przypisywania licencji do użytkowników

Na stronie **Licencje** możesz przypisać licencje na określony produkt maksymalnie 20 użytkownikom. Na **stronie Licencje** jest wyświetlona lista wszystkich produktów, dla których masz subskrypcje. Jest też dostępna łączna liczba licencji dla każdego produktu, liczba przypisanych licencji i liczba dostępnych licencji.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

2. Wybierz produkt.

3. Na stronie szczegółów produktu wybierz pozycję **Przypisz licencje**.

4. W okienku **Przypisz licencje użytkownikom** zacznij wpisywać imię, a następnie wybierz użytkownika z wyników, aby dodać go do listy. Możesz dodać maksymalnie 20 użytkowników jednocześnie.

4. Wybierz pozycję **Włączanie i wyłączanie aplikacji oraz usług**, aby przypisać lub odebrać uprawnienia dostępu do określonych elementów.

6. Po zakończeniu wybierz przypisz **, a** następnie wybierz pozycję **Zamknij**.

W przypadku konfliktu zostanie wyświetlony komunikat informujący o tym, czym jest problem, oraz sposób jego rozwiązania. Na przykład w przypadku wybrania licencji, które zawierają kolidujące ze sobą usługi, wyświetli się komunikat o błędzie z poleceniem sprawdzeniem, jakie usługi są dostępne w poszczególnych licencjach, i prośbą, aby spróbować ponownie.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Zmienianie aplikacji i usług, do których użytkownik ma dostęp

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

2. Na **stronie Licencje** zaznacz wiersz dla określonego użytkownika.

3. W okienku po prawej stronie zaznacz aplikacje i usługi, do których chcesz przydzielić użytkownikowi dostęp, lub usuń zaznaczenie obok tych, do których użytkownik ma stracić dostęp.

4. Gdy skończysz, wybierz pozycję **Zapisz**, a następnie **Zamknij**.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Przypisywanie licencji za pomocą strony Aktywni użytkownicy

Gdy używasz strony **Aktywni użytkownicy** do przypisywania licencji, przypisuj licencje użytkowników do produktów.

### <a name="assign-licenses-to-multiple-users"></a>Przypisywanie licencji do wielu użytkowników

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz kółka obok nazw użytkowników, którym chcesz przypisać licencje.

3. U góry wybierz pozycję **Zarządzaj licencjami produktów**.

4. W **okienku Zarządzanie licencjami produktu** wybierz pozycję **Przypisz więcej: Zachowaj istniejące licencje i przypisz więcej dalej**\>.

5. W **obszarze Licencje** zaznacz pola licencji, które mają mieć wybrani użytkownicy.\
    Domyślnie do użytkownika są automatycznie przypisywane wszystkie usługi skojarzone z tymi licencjami. Możesz ograniczyć liczbę usług dostępnych dla użytkowników. Usuń zaznaczenie pól dla usług, których nie chcesz mieć dla użytkowników.

6. U dołu okienka wybierz pozycję **Zapisz zmiany**.  
    Jeśli nie masz wystarczającej ilości licencji dla wszystkich, może być konieczne zakupienie dodatkowych licencji.

> [!NOTE]
> Jeśli chcesz przypisać licencje dużej liczbie użytkowników, użyj funkcji Przypisywanie licencji użytkownikom według członkostwa [w](/azure/active-directory/enterprise-users/licensing-groups-assign) grupach w Azure Active Directory

### <a name="assign-licenses-to-one-user"></a>Przypisywanie licencji do jednego użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz wierz z użytkownikiem, któremu chcesz przypisać licencję.

3. W okienku po prawej stronie wybierz pozycję **Licencje i aplikacje**.

4. Rozwiń sekcję **Licencje**, zaznacz pola obok licencji, które chcesz przypisać, a następnie wybierz pozycję **Zapisz zmiany**.

## <a name="assign-a-license-to-a-guest-user"></a>Przypisywanie licencji użytkownikowi gościowi

Możesz zaprosić użytkowników-gości do współpracy z Twoją organizacją w centrum Azure Active Directory administracyjnego. Aby dowiedzieć się więcej o użytkownikach gości, zobacz Co to jest dostęp użytkownika gościa w Azure Active Directory [B2B?](/azure/active-directory/external-identities/what-is-b2b). Jeśli nie masz żadnych użytkowników-gości, zobacz Szybki start: dodawanie użytkowników gości do katalogu w [portalu Azure Portal](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Aby wykonać te czynności, musisz być administratorem globalnym.

1. Przejdź do Azure Active Directory <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">administracyjnego</a>.

2. W okienku nawigacji wybierz pozycję **Użytkownicy**.

3. Na **stronie | Wszyscy użytkownicy (wersja zapoznawcza)** wybierz pozycję **Dodaj filtry**.

4. W menu **Wybierz pole** wybierz pozycję **Typ użytkownika**, a następnie wybierz pozycję **Zastosuj**.

5. W następnym menu wybierz pozycję **Gość**.

6. Z listy wyników wybierz użytkownika, który potrzebuje licencji.

7. W **obszarze Zarządzanie** wybierz **pozycję Licencje**.

8. Wybierz **pozycję Zadania**.

9. Na **stronie Aktualizowanie przypisań licencji** wybierz produkt, do którego chcesz przypisać licencję.

10. Po prawej stronie wyczyść pola wyboru obok wszystkich usług, do których nie chcesz, aby gość miał dostęp.

11. Wybierz **Zapisz**.

## <a name="next-steps"></a>Następne kroki

Jeśli użytkownicy nie mają jeszcze zainstalowanych aplikacji Office, możesz udostępnić użytkownikom przewodnik Szybki start dla [](../setup/employee-quick-setup.md) pracowników, aby skonfigurować różne ustawienia, takie jak pobieranie i instalowanie programu [Microsoft 365 lub Office 2019](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) na komputerze PC lub Mac oraz konfigurowanie aplikacji [pakietu Office](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f) i poczty e-mail na urządzeniu przenośnym.

## <a name="related-content"></a>Zawartość pokrewna

[Opis subskrypcji i licencji](../../commerce/licenses/subscriptions-and-licenses.md) (artykuł)\
[Odsyłanie licencji użytkownikom](remove-licenses-from-users.md) (artykuł)\
[Kupowanie lub usuwanie licencji dla subskrypcji](../../commerce/licenses/buy-licenses.md) (artykuł)
