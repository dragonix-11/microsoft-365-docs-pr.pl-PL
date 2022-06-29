---
title: Przypisywanie licencji użytkownikom w Centrum administracyjne platformy Microsoft 365
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
description: Przypisz licencje w zależności od tego, czy chcesz przypisać licencje produktów określonym użytkownikom, czy przypisać licencje użytkowników do określonego produktu.
ms.date: 06/23/2022
ms.openlocfilehash: ecca89deaadd55182875e8d3a5d8d74e2aec17eb
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487526"
---
# <a name="assign-microsoft-365-licenses-to-users"></a>Przypisywanie licencji platformy Microsoft 365 do użytkowników

Możesz przypisywać licencje do użytkowników na stronie **Aktywni użytkownicy** lub na stronie **Licencje**. Używana metoda zależy od tego, czy chcesz przypisać licencje produktów określonym użytkownikom, czy przypisać licencje użytkowników do określonego produktu.

> [!NOTE]
> 
> - Jako administrator nie możesz przypisywać ani anulować przypisywania licencji dla subskrypcji zakupu samoobsługowego zakupionej przez użytkownika w organizacji. Możesz [przejąć subskrypcję samoobsługowego zakupu](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), a następnie przypisać lub cofnąć przypisanie licencji.
> - W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli termin anulowania już minął, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej trwania.

[Dowiedz się, jak dodać użytkownika i jednocześnie przypisać licencję](../add-users/add-users.md).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą firmy Microsoft ds. małych firm](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby przypisać licencje, musisz być administratorem globalnym, licencji lub użytkownika. Aby uzyskać więcej informacji, zobacz [About Microsoft 365 admin roles (Informacje o rolach administratora platformy Microsoft 365](../add-users/about-admin-roles.md)).
- Licencje [platformy Microsoft 365 można przypisać do kont użytkowników przy użyciu programu PowerShell](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Aby korzystać z licencjonowania opartego na [grupach, zobacz Przypisywanie licencji do użytkowników według członkostwa w grupie w usłudze Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Niektóre usługi, takie jak Sway, są automatycznie przypisywane do użytkowników i nie trzeba ich przypisywać pojedynczo.


## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Przypisywanie licencji użytkownikom przy użyciu strony Licencje

Strona **Licencje** umożliwia przypisywanie lub cofanie przypisania licencji dla maksymalnie 20 użytkowników jednocześnie. Na stronie przedstawiono posiadane produkty, liczbę dostępnych licencji dla każdego produktu oraz liczbę przypisanych licencji z łącznej liczby dostępnych licencji. Liczba licencji to łączna suma licencji dla wszystkich subskrypcji dla tej samej nazwy produktu.

Na przykład możesz mieć jedną subskrypcję dla Microsoft 365 Business Premium, która ma 5 licencji, i inną subskrypcję, która ma 8 licencji na ten sam produkt. Strona **Licencje** pokazuje, że masz łącznie 13 licencji na Microsoft 365 Business Premium we wszystkich subskrypcjach. Różni się to od tego, co widać na stronie **Twoje produkty** , która wyświetla wiersz dla każdej posiadanej subskrypcji, nawet jeśli są one dla tego samego produktu.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Wybierz produkt.

3. Na stronie szczegółów produktu wybierz pozycję **Przypisz licencje**.

4. W okienku **Przypisz licencje użytkownikom** zacznij wpisywać imię, a następnie wybierz użytkownika z wyników, aby dodać go do listy. Możesz dodać maksymalnie 20 użytkowników jednocześnie.

4. Wybierz pozycję **Włączanie i wyłączanie aplikacji oraz usług**, aby przypisać lub odebrać uprawnienia dostępu do określonych elementów.

6. Po zakończeniu wybierz pozycję **Przypisz**, a następnie zamknij okienko po prawej stronie.

Jeśli występuje konflikt, zostanie wyświetlony komunikat informujący o tym, czym jest problem i jak go rozwiązać. Na przykład w przypadku wybrania licencji, które zawierają kolidujące ze sobą usługi, wyświetli się komunikat o błędzie z poleceniem sprawdzeniem, jakie usługi są dostępne w poszczególnych licencjach, i prośbą, aby spróbować ponownie.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Zmienianie aplikacji i usług, do które użytkownik ma dostęp

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Na stronie **Licencje** wybierz wiersz dla określonego użytkownika.

3. W okienku po prawej stronie zaznacz aplikacje i usługi, do których chcesz przydzielić użytkownikowi dostęp, lub usuń zaznaczenie obok tych, do których użytkownik ma stracić dostęp.

4. Gdy skończysz, wybierz pozycję **Zapisz**, a następnie **Zamknij**.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Przypisywanie licencji przy użyciu strony Aktywni użytkownicy

W przypadku przypisywania licencji przy użyciu strony **Aktywni użytkownicy** należy przypisać licencje użytkowników do produktów.

### <a name="assign-licenses-to-multiple-users"></a>Przypisywanie licencji do wielu użytkowników

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz okręgi obok nazw użytkowników, do których chcesz przypisać licencje.

3. U góry wybierz pozycję **Zarządzaj licencjami produktów**.

4. W okienku **Zarządzanie licencjami produktów** wybierz pozycję **Przypisz więcej: Zachowaj istniejące licencje i przypisz więcej** \> **dalej**.

5. W obszarze **Licencje** wybierz pole licencji, które mają mieć wybrani użytkownicy.\
    Domyślnie do użytkownika są automatycznie przypisywane wszystkie usługi skojarzone z tymi licencjami. Możesz ograniczyć liczbę usług dostępnych dla użytkowników. Usuń zaznaczenie pól dla usług, które nie mają być dostępne dla użytkowników.

6. W dolnej części okienka wybierz pozycję **Zapisz zmiany**.  
    Jeśli nie masz wystarczającej liczby licencji dla wszystkich, może być konieczne zakup dodatkowych licencji.

> [!NOTE]
> Jeśli chcesz przypisać licencje dla dużej liczby użytkowników, użyj polecenia [Przypisz licencje do użytkowników według członkostwa w grupie w usłudze Azure Active Directory](/azure/active-directory/enterprise-users/licensing-groups-assign)

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

## <a name="assign-a-license-to-a-guest-user"></a>Przypisywanie licencji do użytkownika-gościa

Możesz zaprosić użytkowników-gości do współpracy z organizacją w centrum administracyjnym usługi Azure Active Directory. Aby dowiedzieć się więcej o użytkownikach-gościach, zobacz [Co to jest dostęp użytkowników-gości w usłudze Azure Active Directory B2B?](/azure/active-directory/external-identities/what-is-b2b). Jeśli nie masz żadnych użytkowników-gości, zobacz [Szybki start: Dodawanie użytkowników-gości do katalogu w Azure Portal](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Aby wykonać te kroki, musisz być administratorem globalnym.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">centrum administracyjnego usługi Azure Active Directory</a>.

2. W okienku nawigacji wybierz pozycję **Użytkownicy**.

3. Na **| Użytkownicy Strona Wszyscy użytkownicy (wersja zapoznawcza)** wybierz pozycję **Dodaj filtry**.

4. W menu **Wybierz pole wybierz pozycję** **Typ użytkownika**, a następnie wybierz pozycję **Zastosuj**.

5. W następnym menu wybierz pozycję **Gość**.

6. Na liście wyników wybierz użytkownika, który potrzebuje licencji.

7. W obszarze **Zarządzanie** wybierz pozycję **Licencje**.

8. Wybierz pozycję **Przypisania**.

9. Na stronie **Aktualizowanie przypisań licencji** wybierz produkt, dla który chcesz przypisać licencję.

10. Po prawej stronie wyczyść pola wyboru dla wszystkich usług, do których nie chcesz, aby użytkownik-gość miał dostęp.

11. Wybierz **Zapisz**.

## <a name="next-steps"></a>Następne kroki

Jeśli użytkownicy nie mają jeszcze zainstalowanych aplikacji pakietu Office, możesz udostępnić użytkownikom [przewodnik Szybki start dla](../setup/employee-quick-setup.md) pracowników, aby skonfigurować elementy, takie [jak pobieranie i instalowanie platformy Microsoft 365 lub Office 2019 na komputerze PC lub Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) oraz [konfigurowanie aplikacji pakietu Office i poczty e-mail na urządzeniu przenośnym](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie subskrypcji i licencji](../../commerce/licenses/subscriptions-and-licenses.md) (artykuł)\
[Anulowanie przypisywania licencji od użytkowników](remove-licenses-from-users.md) (artykuł)\
[Kupowanie lub usuwanie licencji dla subskrypcji](../../commerce/licenses/buy-licenses.md) (artykuł)
