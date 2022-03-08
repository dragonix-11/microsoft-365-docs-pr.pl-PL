---
title: Zamykanie konta
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
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
- commerce_subscriptions
- AdminSurgePortfolio
- fwlink 2133922 to Delete subscription heading
- AdminTemplateSet
search.appverid: MET150
description: Po zamknięciu konta w firmie Microsoft wszystkie związane z nim informacje, w tym licencje, użytkownicy i dane użytkownika, zostaną usunięte.
ms.date: 04/02/2021
ms.openlocfilehash: b1ac828d047d2c2b9f39185a66ccc77976b8324b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317293"
---
# <a name="close-your-account"></a>Zamykanie konta

Po zamknięciu konta Microsoft usunięte zostaną wszystkie informacje dotyczące tego konta. Informacje te obejmują subskrypcje, licencje, metody płatności, użytkowników i ich dane.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem procedury zamykania konta utwórz kopię zapasową wszystkich danych, które chcesz zachować.

Aby wykonać zadania z tego artykułu, musisz być administratorem globalnym lub rozliczeniowym. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>Krok 1. Usuwanie użytkowników

Usuń wszystkich użytkowników z wyjątkiem jednego administratora globalnego. Administrator globalny dokończy procedurę zamykania konta. Przed usunięciem katalogu pod koniec tego procesu należy usunąć wszystkich innych użytkowników.

Jeśli użytkownicy są synchronizowane z lokalnego, najpierw wyłącz synchronizację, a następnie usuń użytkowników z katalogu w chmurze za pomocą portalu Azure portal lub Azure PowerShell cmdlet.

Aby usunąć użytkowników, zobacz [Administrator zarządzający użytkownikami: Usuwanie jednego lub większej liczby użytkowników](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

Możesz również użyć polecenia cmdlet [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell, aby zbiorczo usunąć użytkowników.

Jeśli organizacja korzysta z usługi Active Directory synchronizowej z usługą Microsoft Azure Active Directory (Azure AD), zamiast tego usuń konto użytkownika z usługi Active Directory. Aby uzyskać instrukcje, [zobacz Zbiorcze usuwanie użytkowników w programie Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>Krok 2. Anulowanie wszystkich aktywnych subskrypcji

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">RozliczeniaZgody</a>  >  produktów.
2. Na karcie **Produkty** znajdź aktywną subskrypcję. Wybierz trzy kropki (więcej akcji), a następnie wybierz anuluj **subskrypcję**.
3. W **okienku Anulowanie** subskrypcji wybierz powód anulowania. Opcjonalnie możesz przekazać opinię.
4. Wybierz **Zapisz**.
5. Powtórz kroki od 1 do 4, aby anulować wszystkie aktywne subskrypcje.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Krok 3. Usuwanie wszystkich wyłączonych subskrypcji

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">RozliczeniaZgody</a>  >  produktów.
2. Na karcie **Produkty** wybierz wyłączono subskrypcję.
3. Na stronie szczegółów subskrypcji w sekcji **Ustawienia subskrypcji i płatności** wybierz pozycję **Usuń subskrypcję**.
4. W **okienku Usuń subskrypcję** wybierz pozycję **Usuń subskrypcję**.
5. W **oknie dialogowym Usuwanie** subskrypcji wybierz pozycję **Tak**.
6. Dla każdej wyłączonej subskrypcji powtarzaj kroki od 3 do 5, aż wszystkie subskrypcje zostaną usunięte.

> [!NOTE]
> Jeśli nie możesz od razu usunąć wyłączonej subskrypcji, skontaktuj się [z pomocą techniczną](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>Krok 4. Wyłączanie uwierzytelniania wieloskładnikowego

1. Zaloguj się do centrum administracyjnego przy użyciu konta administratora globalnego. Aby sprawdzić, jakie masz role, zobacz [Sprawdzanie ról administratora w organizacji](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. Przejdź do **strony** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">UżytkownicyAktywowanie</a> >  użytkowników.
3. Wybierz **pozycję Uwierzytelnianie wieloskładnikowe**.
4. Na stronie uwierzytelnianie wieloskładnikowe wyłącz wszystkie konta z wyjątkiem konta administratora globalnego, z których obecnie korzystasz.

Za pomocą programu [PowerShell można również wyłączyć uwierzytelnianie wieloskładnikowe dla wielu użytkowników](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Krok 5. Usunięcie katalogu z Azure Active Directory

1. Zaloguj się do centrum <a href="https://aad.portal.azure.com/" target="_blank">administracyjnego usługi Azure AD</a> przy użyciu konta administratora globalnego.
2. Wybierz pozycję **Azure Active Directory**.
3. Przejdź do organizacji, którą chcesz usunąć.
4. Wybierz **pozycję Usuń dzierżawę**.
5. Jeśli Twoja organizacja nie sprawdzi się, zostanie wyświetlony link do dodatkowych informacji na temat sposobu przeprowadzania testów. Po ukończeniu wszystkich testów wybierz pozycję **Usuń** , aby ukończyć proces.

Po zakończeniu tego ostatniego kroku Twoje konto w firmie Microsoft zostanie zamknięte i usunięte.

## <a name="related-content"></a>Zawartość pokrewna 

[Opis rachunku lub faktury za Microsoft 365 dla firm](./billing-and-payments/understand-your-invoice2.md) (artykuł)\
[Anulowanie subskrypcji](./subscriptions/cancel-your-subscription.md) (artykuł)

