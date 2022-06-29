---
title: Zamknij konto
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
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
description: Po zamknięciu konta w firmie Microsoft wszystkie informacje związane z Twoim kontem zostaną usunięte, w tym licencje, użytkownicy i dane użytkowników.
ms.date: 04/02/2021
ms.openlocfilehash: a14dd1153d8030dd953c58404902a891aeefdaf9
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66491764"
---
# <a name="close-your-microsoft-account"></a>Zamykanie konta Microsoft

Po zamknięciu konta Microsoft usunięte zostaną wszystkie informacje dotyczące tego konta. Informacje te obejmują subskrypcje, licencje, metody płatności, użytkowników i ich dane.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem procedury zamykania konta utwórz kopię zapasową wszystkich danych, które chcesz zachować.

Musisz być administratorem globalnym lub administratorem ds. rozliczeń, aby wykonywać zadania opisane w tym artykule. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>Krok 1. Usuwanie użytkowników

Usuń wszystkich użytkowników z wyjątkiem jednego administratora globalnego. Administrator globalny wykonuje kroki, aby zamknąć konto. Aby można było usunąć katalog na końcu tego procesu, musisz usunąć wszystkich innych użytkowników.

Jeśli użytkownicy są synchronizowani ze środowiska lokalnego, najpierw wyłącz synchronizację, a następnie usuń użytkowników w katalogu w chmurze przy użyciu poleceń cmdlet Azure Portal lub Azure PowerShell.

Aby usunąć użytkowników, zobacz [Administrator zarządzania użytkownikami: Usuwanie co najmniej jednego użytkownika](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

Możesz również użyć polecenia cmdlet [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) programu PowerShell, aby zbiorczo usuwać użytkowników.

Jeśli Organizacja używa usługi Active Directory synchronizowanej z Microsoft Azure Active Directory (Azure AD), zamiast tego usuń konto użytkownika z usługi Active Directory. Aby uzyskać instrukcje, zobacz [Zbiorcze usuwanie użytkowników w usłudze Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>Krok 2. Anulowanie wszystkich aktywnych subskrypcji

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.
2. Na karcie **Produkty** znajdź aktywną subskrypcję. Wybierz pozycję z trzema kropkami (więcej akcji), a następnie wybierz pozycję **Anuluj subskrypcję**.
3. W okienku **Anulowanie subskrypcji** wybierz przyczynę anulowania. Opcjonalnie przekaż dowolną opinię.
4. Wybierz **Zapisz**.
5. Powtórz kroki od 1 do 4, aby anulować wszystkie aktywne subskrypcje.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Krok 3. Usuwanie wszystkich wyłączonych subskrypcji

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.
2. Na karcie **Produkty** wybierz wyłączoną subskrypcję.
3. Na stronie szczegółów subskrypcji w sekcji **Ustawienia subskrypcji i płatności** wybierz pozycję **Usuń subskrypcję**.
4. W okienku **Usuwanie subskrypcji** wybierz pozycję **Usuń subskrypcję**.
5. W oknie dialogowym **Usuwanie subskrypcji** wybierz pozycję **Tak**.
6. Dla każdej wyłączonej subskrypcji powtórz kroki od 3 do 5, aż wszystkie subskrypcje zostaną usunięte.

> [!NOTE]
> Jeśli nie możesz natychmiast usunąć wyłączonej subskrypcji, [skontaktuj się z pomocą techniczną](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>Krok 4. Wyłączanie uwierzytelniania wieloskładnikowego

1. Zaloguj się do centrum administracyjnego przy użyciu konta administrator globalny. Aby sprawdzić, jakie role masz, zobacz [Sprawdzanie ról administratorów w organizacji](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. Przejdź do strony **Użytkownicy** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">aktywni użytkownicy</a> .
3. Wybierz **pozycję Uwierzytelnianie wieloskładnikowe**.
4. Na stronie uwierzytelniania wieloskładnikowego wyłącz wszystkie konta z wyjątkiem aktualnie używanego konta administratora globalnego.

Program [PowerShell umożliwia również wyłączenie uwierzytelniania wieloskładnikowego dla wielu użytkowników](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Krok 5. Usuwanie katalogu w usłudze Azure Active Directory

1. Zaloguj się do <a href="https://aad.portal.azure.com/" target="_blank">centrum administracyjnego Azure AD</a> przy użyciu konta administrator globalny.
2. Wybierz pozycję **Azure Active Directory**.
3. Przejdź do organizacji, którą chcesz usunąć.
4. Wybierz pozycję **Usuń dzierżawę**.
5. Jeśli twoja organizacja zakończy się niepowodzeniem co najmniej jednej kontroli, zostanie wyświetlony link do dodatkowych informacji na temat sposobu przekazywania testów. Po przekazaniu wszystkich testów wybierz pozycję **Usuń** , aby ukończyć proces.

Po wykonaniu tego ostatniego kroku konto w firmie Microsoft zostanie zamknięte i usunięte.

## <a name="related-content"></a>Zawartość pokrewna 

[Opis rachunku lub faktury za platformę Microsoft 365 dla firm](./billing-and-payments/understand-your-invoice2.md) (artykuł)\
[Anulowanie subskrypcji](./subscriptions/cancel-your-subscription.md) (artykuł)

