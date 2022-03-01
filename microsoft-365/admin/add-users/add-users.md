---
title: Dodawanie użytkowników i przypisywanie licencji
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
description: Każdy członek zespołu potrzebuje konta użytkownika, aby może zalogować się i uzyskać dostęp do Microsoft 365 dla firm. Dowiedz się, jak dodawać użytkowników i przypisywać licencje.
ms.date: 07/01/2020
ms.openlocfilehash: 90ef6506d10c0f4c106dd18816ccd2f11803a079
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011305"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Dodawanie użytkowników i przypisywanie licencji w tym samym czasie

Aby osoby z Twojego zespołu były w mogą logować się i korzystać z usługi Microsoft 365 [dla firm, każda z nich potrzebuje konta użytkownika](https://www.microsoft.com/microsoft-365/business). Najłatwiejszym sposobem dodawania kont użytkowników jest ich dodawanie po jednym na raz w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365.</a> Po zakończeniu tego kroku użytkownicy mają licencje Microsoft 365, poświadczenia logowania i Microsoft 365 skrzynki pocztowe.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dodawać użytkowników i przypisywać licencje, musisz być administratorem globalnym, licencją lub administratorem. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>Obejrzyj: Dodawanie użytkowników w widoku pulpitu nawigacyjnego

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Kroki użyte w klipie wideo pokazują inny punkt początkowy dodawania użytkowników, ale pozostałe kroki są takie same jak w poniższej procedurze.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Dodawanie użytkowników po jednym na raz w widoku pulpitu nawigacyjnego

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Zrzut ekranu: widok pulpitu nawigacyjnego w centrum administracyjnym":::

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w stronie <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Przejdź do **opcji** **UżytkownicyAktywowanie** >  użytkowników i wybierz **pozycję Dodaj użytkownika**.
3. W **okienku Konfigurowanie podstawowych informacji** wprowadź podstawowe informacje o użytkowniku, a następnie wybierz pozycję **Dalej**.
    - **Nazwa** Wprowadź imię i nazwisko, nazwę wyświetlaną i nazwę użytkownika.
    - **Domena** Wybierz domenę dla konta użytkownika. Jeśli na przykład nazwa użytkownika to Jakub, a domena jest contoso.com, będzie logować się przy użyciu konta jakob@contoso.com.
    - **Ustawienia haseł** Wybierz opcję użycia hasła wygenerowanego automatycznie lub utworzenia własnego silnego hasła dla użytkownika.
    - Użytkownik musi zmienić hasło po upływie 90 dni. Możesz też wybrać opcję **Wymagaj od tego użytkownika zmiany hasła, gdy zaloguje się po raz pierwszy**.
    - Określ, czy po dodaniu użytkownika chcesz wysłać hasło w wiadomości e-mail.
4. W **okienku Przypisywanie licencji produktu** wybierz lokalizację i odpowiednią licencję dla użytkownika. Jeśli nie masz dostępnych żadnych licencji, nadal możesz dodać użytkownika i kupić dodatkowe licencje. **Rozwiń pozycję** Aplikacje i zaznacz lub usuń zaznaczenie aplikacji, aby ograniczyć aplikacje, na które użytkownik ma licencję. Wybierz pozycję **Dalej**.
5. W **okienku Ustawienia opcjonalne** rozwiń pozycję **Role** , aby ten użytkownik był administratorem. **Rozwiń pozycję Informacje** o profilu, aby dodać dodatkowe informacje o użytkowniku.
6. Wybierz **pozycję** Dalej, przejrzyj ustawienia nowego użytkownika, wprowadzić dowolne zmiany, a następnie wybierz pozycję Zakończ **dodawanie**, a następnie **Zamknij**.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Dodawanie użytkownika w widoku uproszczonym administratora

Jeśli widzisz tę stronę w centrum administracyjnym, oznacza to, że jesteś administratorem **w widoku uproszczonym**. Aby dodać użytkownika, wykonaj poniższe czynności.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Zrzut ekranu: uproszczony widok centrum administracyjnego":::

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w stronie <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Wybierz **pozycję Utwórz konto dla innej osoby**.
3. Na **stronie Dodawanie konta użytkownika** wprowadź imię i nazwisko, nazwę wyświetlaną i nazwę użytkownika, przy użyciu których będą się logować.
4. Dodaj adres e-mail użytkownika w polu tekstowym **Do 5 adresów** e-mail. Dzięki temu nowy użytkownik otrzyma informacje potrzebne do zalogowania się do Microsoft 365 usług.
5. Wybierz **pozycję Dodaj użytkownika** **i Pobierz informacje logowania** , jeśli chcesz zapisać te informacje.

## <a name="add-multiple-users-at-the-same-time"></a>Dodawanie wielu użytkowników jednocześnie

Aby dodać wielu użytkowników jednocześnie, możesz użyć dowolnej z następujących metod:

- **Aby zbiorczo dodać użytkowników, możesz użyć arkusza kalkulacyjnego.** Zobacz [Dodawanie kilku użytkowników jednocześnie](../../enterprise/add-several-users-at-the-same-time.md).
- **Zautomatyzuj dodawanie kont i przypisywanie licencji.** Zobacz [Tworzenie kont użytkowników za pomocą programu Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Wybierz tę metodę, jeśli wiesz już, jak używać poleceń cmdlet programu Windows PowerShell.
- **Używasz usługi ActiveDirectory?** [Konfigurowanie synchronizacji katalogów dla Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Za pomocą narzędzia do Połączenie Active Directory zreplikuj konta użytkowników usługi Active Directory (i inne obiekty usługi Active Directory) w Microsoft 365. Synchronizacja powoduje tylko dodanie kont użytkowników. Musisz przypisać licencje do synchronizowanych użytkowników, aby użytkownicy mieli dostęp do poczty e-mail i innych Office aplikacji.
- **Migrowanie z Exchange?** Zobacz [Sposoby migrowania wielu kont e-mail do Office 365](/Exchange/mailbox-migration/mailbox-migration). Podczas migrowania wielu skrzynek pocztowych do usługi Microsoft 365 przy użyciu metody Exchange etapowej lub hybrydowej wersji programu Exchange są automatycznie dodawania użytkowników w ramach migracji. Migracja powoduje tylko dodanie kont użytkowników. Musisz przypisać licencje do użytkowników, abyli mogą korzystać z poczty e-mail i innych Office aplikacji. Jeśli użytkownikowi nie zostanie przypisana licencja, jego skrzynka pocztowa zostanie wyłączona po upływie 30-dniowego okresu prolongaty. Dowiedz się, [jak przypisywać licencje użytkownikom](../manage/assign-licenses-to-users.md) w centrum administracyjne platformy Microsoft 365.

## <a name="next-steps"></a>Następne kroki

Po dodaniu użytkownika otrzymasz powiadomienie e-mail od firmy Microsoft. Wiadomość e-mail zawiera identyfikator użytkownika i hasło, aby ta osoba Microsoft 365. Skorzystaj ze swojego zwykłego procesu przekazywania nowych haseł. Udostępnij przewodnik [Szybki start](../setup/employee-quick-setup.md) dla pracowników nowym użytkownikom, aby dowiedzieć się, jak pobrać i zainstalować aplikacje Office na komputerze [PC lub Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) oraz jak skonfigurować aplikacje Office i pocztę e-mail na urządzeniu [przenośnym](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Zawartość pokrewna

[Dodawanie nowego pracownika do Microsoft 365](add-new-employee.md) (artykuł)\
[Dodawanie kilku użytkowników jednocześnie do folderu Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (artykuł)\
[Przywracanie użytkownika w programie Microsoft 365](restore-user.md) (artykuł)\
[Przypisywanie licencji użytkownikom](../manage/assign-licenses-to-users.md) (artykuł)\
[Usuwanie użytkownika z organizacji](delete-a-user.md) (artykuł)
