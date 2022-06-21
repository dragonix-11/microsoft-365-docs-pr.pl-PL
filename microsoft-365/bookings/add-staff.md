---
title: Dodaj pracowników do aplikacji Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Ta strona służy do tworzenia listy pracowników i zarządzania danymi pracowników, takimi jak imię i nazwisko, numer telefonu i adres e-mail.
ms.openlocfilehash: b9acf72e9026b230702ed4cad232a92842b51028
ms.sourcegitcommit: af2b570e76e074bbef98b665b5f9a731350eda58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185154"
---
# <a name="add-staff-to-bookings"></a>Dodaj pracowników do aplikacji Bookings

Strona Personel w obszarze Rezerwacje to miejsce, w którym tworzysz listę pracowników i zarządzasz danymi pracowników, takimi jak imię i nazwisko, numer telefonu i adres e-mail. W tym miejscu można również ustawić godziny pracy dla każdego pracownika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Chociaż rezerwacje są funkcją Microsoft 365, nie wszyscy pracownicy muszą mieć konto Microsoft 365. Wszyscy pracownicy muszą mieć prawidłowy adres e-mail, aby mogli otrzymywać rezerwacje i planować zmiany.

## <a name="watch-add-your-staff-to-bookings"></a>Obejrzyj: Dodaj pracowników do rezerwacji

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Kroki

1. Wybierz kalendarz na stronie głównej.

2. Przejdź do opcji personelu w lewym okienku i wybierz pozycję **Dodaj nowych pracowników**.

3. Podczas dodawania pracowników z organizacji wpisz ich imię i nazwisko w polu **Dodaj osoby** i wybierz je, gdy pojawią się w menu rozwijanym. Pozostałe pola zostaną automatycznie wypełnione.

    Po dodaniu pracownika możesz edytować nazwę wyświetlaną we wszystkich komunikatach Bookings, wybierając **znak x** obok jego nazwy i edytując pole **Dodaj osoby** . Może to być przydatne, jeśli chcesz, aby pracownicy mieli określony tytuł lub nazwę wyświetlaną dla klientów, na przykład wymieniając Adele Vance jako "Dr Vance, MD".

4. Aby dodać pracowników spoza organizacji, ręcznie wypełnij adres e-mail i inne informacje.

    > [!NOTE]
    > Pracownicy spoza twojej dzierżawy nie będą mogli udostępniać rezerwacjom bezpłatnych/zajętych informacji.

5. Dla każdego członka personelu wybierz rolę: Członek zespołu, Harmonogram, Przeglądarka lub Gość.
    - **Członek zespołu** może zarządzać rezerwacjami we własnym kalendarzu i ich dostępności w skrzynce pocztowej rezerwacji. Podczas dodawania lub edytowania rezerwacji w kalendarzu zostaną oni przypisani jako pracownicy.
    - **Harmonogram** może zarządzać rezerwacjami w kalendarzu i szczegółami klienta. Mają dostęp tylko do odczytu do ustawień, personelu i usług.
    - **Osoba przeglądająca** może zobaczyć wszystkie rezerwacje w kalendarzu, ale nie może ich modyfikować ani usuwać. Mają dostęp tylko do odczytu do ustawień.
    - **Gość** może zostać przypisany do rezerwacji, ale nie może otworzyć skrzynki pocztowej rezerwacji.

6. Wybierz pozycję **Powiadom wszystkich pracowników za pośrednictwem poczty e-mail, gdy zostanie utworzona lub zmieniona rezerwacja** , aby włączyć wiadomości e-mail pracowników. Poniżej znajduje się przykładowa wiadomość e-mail:

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Wiadomość e-mail z powiadomieniem z bookings.":::

7. Wybierz pozycję **Wydarzenia w Office 365 kalendarz wpływa na dostępność**, jeśli chcesz, aby bezpłatne/zajęte informacje z kalendarzy pracowników miały wpływ na dostępność usług rezerwacji za pośrednictwem rezerwacji.

    Jeśli na przykład członek personelu ma spotkanie zespołu lub spotkanie osobiste zaplanowane na godzinę 15:00 w środę, rezerwacje pokażą, że pracownik jest niedostępny do zarezerwowania w tym przedziale czasu. Ten czas będzie wyświetlany jako zajęty lub wstępny w widoku kalendarza Rezerwacje, jak pokazano w poniższym przykładzie.

    :::image type="content" source="media/bookings-busy-tentative-view-2.png" alt-text="Widok kalendarza Rezerwacje.":::

> [!IMPORTANT]
> Zdecydowanie zalecamy pozostawienie tego ustawienia włączone (jest domyślnie włączone), aby uniknąć podwójnych rezerwacji i zoptymalizować dostępność pracowników.

8. Wybierz pozycję **Użyj godzin pracy** , aby ustawić wszystkie godziny rezerwacji dla pracowników tylko w godzinach roboczych ustawionych w sekcji **Godziny pracy** na stronie Informacje biznesowe.

    Usuwając zaznaczenie tego pola, personel może otrzymać niestandardowe godziny, które dodatkowo ograniczają możliwość rezerwacji. Jest to przydatne w scenariuszach, w których pracownik może znajdować się tylko we wtorki i środy na miejscu lub poświęca poranki na jeden rodzaj spotkań i popołudnia dla innych typów.

    > [!NOTE]
    > Rezerwacje obsługują maksymalnie 100 pracowników w kalendarzu rezerwacji.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Ustaw użytkownika Bookings jako superużytkownika bez dodawania go jako personelu w rezerwacjach

Możesz dodać osobę do swojej listy pracowników w obszarze Rezerwacje bez udostępniania jej klientom lub klientom. Gdy staniesz się superużytkownikiem, zostanie administratorem skrzynki pocztowej rezerwacji. Bycie administratorem skrzynki pocztowej rezerwacji jest definiowane jako posiadające pełny dostęp i uprawnienia do wysyłania jako do skrzynki pocztowej rezerwacji.

> [!NOTE]
> Te kroki działają tylko wtedy, gdy dodawanemu użytkownikowi nie przypisano jeszcze roli **przeglądarki** w obszarze Rezerwacje.

1. [Połączenie do Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Za pomocą programu PowerShell przypisz pełny dostęp za pomocą następujących poleceń:

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Następnie uruchom to polecenie, aby przypisać uprawnienia typu send-as.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Oto przykładowe polecenie programu PowerShell, aby dodać Allie Bellew do skrzynki pocztowej rezerwacji przedszkola firmy Contoso.

1. Najpierw uruchom następujące polecenie:

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Następnie uruchom następujące polecenie:

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew** ma teraz dostęp administratora, ale nie pojawia się jako personel z możliwością rezerwacji.
