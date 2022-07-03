---
title: Dodawanie użytkowników i przypisywanie licencji na platformie Microsoft 365
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- MET150
description: Dowiedz się, jak nadać każdemu członkowi zespołu konto użytkownika, aby mógł mieć licencje platformy Microsoft 365, poświadczenia logowania i skrzynki e-mail na platformie Microsoft 365.
ms.date: 07/01/2020
ms.openlocfilehash: b9662263711bb08063a9c2ff9f70767bb3ea7ce4
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601999"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Dodawanie użytkowników i jednoczesne przypisywanie licencji

Zapoznaj się z [Pomoc techniczna platformy Microsoft 365 dla małego biznesu](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

Aby osoby z Twojego zespołu mogły zalogować się i uzyskać dostęp do platformy [Microsoft 365 dla firm](https://www.microsoft.com/microsoft-365/business), każda z nich potrzebuje konta użytkownika. Najłatwiejszym sposobem dodawania kont użytkowników jest dodawanie ich pojedynczo w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnym platformy Microsoft 365</a>. Na końcu tego procesu użytkownicy będą mieli licencje platformy Microsoft 365, poświadczenia logowania oraz skrzynki pocztowe na platformie Microsoft 365.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą firmy Microsoft ds. małych firm](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dodawać użytkowników i przypisywać licencje, musisz być administratorem globalnym, administratorem licencji lub użytkowników. W celu uzyskania więcej informacji zobacz [Informacje o rolach administratora](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>Obejrzyj: Dodawanie użytkowników w widoku pulpitu nawigacyjnego

Obejrzyj ten klip wideo i inne na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198205).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Kroki przedstawione w wideo pokazują inny punkt początkowy dodawania użytkowników, ale pozostałe kroki są takie same jak poniższa procedura.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Dodawanie użytkowników pojedynczo w widoku pulpitu nawigacyjnego

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Wycinek ekranu: widok pulpitu nawigacyjnego centrum administracyjnego":::

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w witrynie <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Przejdź do obszaru **Użytkownicy** > **Aktywni użytkownicy**, a następnie wybierz pozycję **Dodaj użytkownika**.
3. W okienku **Konfigurowanie ustawień podstawowych** wypełnij podstawowe informacje o użytkowniku, a następnie wybierz pozycję **Dalej**.
    - **Nazwa** Podaj imię i nazwisko, nazwę wyświetlaną i nazwę użytkownika.
    - **Domena** Wybierz domenę dla konta użytkownika. Na przykład jeśli nazwa użytkownika to Jakub, a domena to contoso.com, ta osoba będzie logować się wpisując ciąg jakub@contoso.com.
    - **Ustawienia hasła** Wybierz opcję użycia automatycznie wygenerowanego hasła lub utworzenia własnego silnego hasła dla użytkownika.
    - Użytkownik musi zmienić hasło po upływie 90 dni. Możesz też wybrać opcję **Wymagaj od tego użytkownika zmiany hasła, gdy zaloguje się po raz pierwszy**.
    - Określ, czy chcesz wysłać hasło w wiadomości e-mail po dodaniu użytkownika.
4. W okienku **Przypisywanie licencji produktu** wybierz lokalizację i odpowiednią licencję dla użytkownika. Jeśli nie masz dostępnych żadnych licencji, nadal możesz dodać użytkownika i kupić dodatkowe licencje. Rozwiń obszar **Aplikacje** i wybierz lub usuń zaznaczenie aplikacji, aby ograniczyć liczbę aplikacji, na które użytkownik ma licencję. Wybierz pozycję **Dalej**.
5. W okienku **Ustawienia opcjonalne** rozwiń obszar **Role**, aby przypisać temu użytkownikowi rolę administratora. Rozwiń obszar **Informacje o profilu**, aby dodać dodatkowe informacje o użytkowniku.
6. Wybierz pozycję **Dalej**, przejrzyj ustawienia nowego użytkownika, wprowadź odpowiednie zmiany, a następnie wybierz pozycję **Zakończ dodawanie** i **Zamknij**.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Dodawanie użytkownika w widoku uproszczonym administratora

Jeśli widzisz tę stronę w centrum administracyjnym, korzystasz z **uproszczonego widoku administratora**. Wykonaj poniższe kroki, aby dodać użytkownika.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Wycinek ekranu: uproszczony widok centrum administracyjnego":::

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w witrynie <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Wybierz pozycję **Utwórz konto dla innej osoby**.
3. Na stronie **Dodawanie konta użytkownika** podaj imię i nazwisko, nazwę wyświetlaną i nazwę użytkownika, która będzie używana do logowania.
4. Dodaj adres e-mail użytkownika w polu tekstowym **Wprowadź maksymalnie 5 adresów e-mail...**. Dzięki temu nowy użytkownik otrzyma informacje potrzebne do zalogowania się do usług platformy Microsoft 365.
5. Wybierz pozycję **Dodaj użytkownika**, a następnie pozycję **Pobierz informacje logowania**, jeśli chcesz zapisać te informacje.

## <a name="add-multiple-users-at-the-same-time"></a>Dodawanie kilku użytkowników jednocześnie

Aby dodać wielu użytkowników jednocześnie, można użyć jednej z następujących metod:

- **Aby zbiorczo dodać użytkowników, możesz użyć arkusza kalkulacyjnego.** Zobacz: [Dodawanie kilku użytkowników jednocześnie](../../enterprise/add-several-users-at-the-same-time.md).
- **Zautomatyzuj dodawanie kont i przypisywanie licencji.** Zobacz: [Tworzenie kont użytkowników przy użyciu programu PowerShell na platformie Microsoft 365](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Wybierz tę metodę, jeśli wiesz już, jak używać poleceń cmdlet programu Windows PowerShell.
- **Używasz usługi Active Directory?** [Skonfiguruj synchronizację katalogów dla platformy Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Za pomocą narzędzia Azure AD Connect zreplikuj konta użytkowników usługi Active Directory (i inne obiekty usługi Active Directory) na platformie Microsoft 365. Synchronizacja powoduje tylko dodanie kont użytkowników. Musisz przypisać licencje do synchronizowanych użytkowników, aby mogli oni korzystać z poczty e-mail i innych aplikacji pakietu Office.
- **Migrujesz z programu Exchange?** Zobacz: [Sposoby migrowania wielu kont e-mail do usługi Office 365](/Exchange/mailbox-migration/mailbox-migration). Podczas migrowania wielu skrzynek pocztowych na platformę Microsoft 365 za pomocą metody jednorazowej, etapowej lub hybrydowej programu Exchange użytkownicy są dodawani automatycznie w ramach migracji. Migracja powoduje tylko dodanie kont użytkowników. Musisz przypisać licencje do użytkowników, aby mogli oni korzystać z poczty e-mail i innych aplikacji pakietu Office. W przypadku nieprzypisania licencji do użytkownika skrzynka pocztowa zostanie wyłączona po upływie 30-dniowego okresu prolongaty. Dowiedz się, jak [przypisywać licencje do użytkowników](../manage/assign-licenses-to-users.md) w centrum administracyjnym platformy Microsoft 365.

## <a name="next-steps"></a>Następne kroki

Po dodaniu użytkownika otrzymasz wiadomość e-mail z powiadomieniem od firmy Microsoft. Ta wiadomość zawiera identyfikator użytkownika i hasło umożliwiające logowanie się do platformy Microsoft 365. Skorzystaj ze swojego zwykłego procesu przekazywania nowych haseł. Udostępnij [Przewodnik Szybki start dla pracowników](../setup/employee-quick-setup.md) nowym użytkownikom w celu skonfigurowania elementów, takich jak [pobieranie i instalowanie aplikacji pakietu Office na komputerach PC i komputerach Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) oraz [konfigurowanie aplikacji pakietu Office i poczty e-mail na urządzeniu przenośnym](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Zawartość pokrewna

[Dodawanie nowego pracownika do platformy Microsoft 365](add-new-employee.md) (artykuł)\
[Dodawanie kilku użytkowników jednocześnie do platformy Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md)
[Przywracanie użytkownika na platformie Microsoft 365](restore-user.md) (artykuł)\
[Przypisywanie licencji do użytkowników](../manage/assign-licenses-to-users.md) (artykuł)\
[Usuwanie użytkownika z własnej organizacji](delete-a-user.md) (artykuł)
