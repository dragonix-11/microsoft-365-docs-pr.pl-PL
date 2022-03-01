---
title: Dodawanie personelu do rezerwacji
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Na tej stronie możesz utworzyć listę personelu i zarządzać szczegółami członków personelu, takimi jak imię i nazwisko, numer telefonu i adres e-mail.
ms.openlocfilehash: 03ebf5c21e40d53e87067866e05fc37c2c255331
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015788"
---
# <a name="add-staff-to-bookings"></a>Dodawanie personelu do rezerwacji

Na stronie Personelu w aplikacji Bookings możesz utworzyć listę personelu i zarządzać szczegółami członków personelu, takimi jak imię i nazwisko, numer telefonu oraz adres e-mail. W tym miejscu możesz również ustawić godziny pracy dla każdego członka personelu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Mimo że bookings jest funkcją Microsoft 365, nie wszyscy członkowie personelu muszą mieć Microsoft 365 konta. Wszyscy członkowie personelu muszą mieć prawidłowy adres e-mail, aby otrzymać rezerwacje i zaplanować zmiany.

## <a name="watch-add-your-staff-to-bookings"></a>Obejrzyj: Dodawanie personelu do aplikacji Bookings

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Kroki

> [!NOTE]
> Te kroki nie są jeszcze dostępne w nowym środowisko obsługi rezerwacji.

1. Przejdź na stronę [Zarządzanie personelem i](https://outlook.office.com/bookings/staff) wybierz pozycję **Dodaj personel**

2. Wybierz przycisk **Dodaj personel** .

3. Podczas dodawania pracowników z organizacji wpisz ich nazwiska w polu Dodaj osoby  i zaznacz je, gdy pojawią się w menu rozwijaym. Pozostałe pola zostaną automatycznie wypełnione.

    Po dodaniu członka personelu możesz edytować nazwę wyświetlaną we wszystkich informacjach dotyczących usługi Bookings, wybierając **znak x** obok jego imienia i nazwiska oraz edytując pole **Dodaj** osoby. Może to być przydatne, jeśli chcesz, aby członkowie personelu mieli określone stanowisko lub imię i nazwisko wyświetlane dla klientów, na przykład imię i nazwisko Adele Vance jako "Dr. Vance, MD".

4. Aby dodać pracowników spoza organizacji, ręcznie wprowadź ich adresy e-mail i inne informacje.

    > [!NOTE]
    > Pracownicy spoza Twojej dzierżawy nie będą mogli udostępniać informacji o godzinie wolny/zajęty za pomocą usługi Bookings.

5. Dla każdego członka personelu wybierz rolę: Administrator, Przeglądarka lub Gość.
    - **Administratorzy** mogą edytować wszystkie ustawienia, dodawać i usuwać pracowników oraz tworzyć, edytować lub usuwać rezerwacje.
    - **Widzą** wszystkie rezerwacje w kalendarzu, ale nie mogą ich modyfikować ani usuwać. Mają dostęp tylko do odczytu do ustawień.
    - **Goście** mogą zostać przypisani do rezerwacji, ale nie mogą otworzyć skrzynki pocztowej rezerwacji.

6. Wybierz **pozycję Powiadom wszystkich pracowników pocztą e-mail** o utworzeniu lub zmianie rezerwacji, aby włączyć obsługę wiadomości e-mail personelu. Poniżej przedstawiono przykładowy adres e-mail:

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Wiadomość e-mail z powiadomieniem od usługi Bookings.":::

7. Wybierz **pozycję Zdarzenia Office 365** mają wpływ na dostępność, jeśli chcesz, aby informacje o wolnym/zajętym z kalendarzy członków personelu miały wpływ na dostępność usług rezerwacji za pośrednictwem aplikacji Bookings.

    Jeśli na przykład członek personelu ma spotkanie zespołu lub osobisty termin zaplanowany na 15:00 w środę, usługa Bookings pokaże, że członek personelu jest niedostępny w tym czasie. Ten czas będzie wyświetlany jako Zajęty lub Wstępna akceptacja w widoku kalendarza aplikacji Bookings, jak pokazano w poniższym przykładzie.

    :::image type="content" source="media/bookings-busy-tentative-view.jpg" alt-text="Widok kalendarza aplikacji Bookings.":::

> [!IMPORTANT]
> Zdecydowanie zalecamy pozostawienie tego ustawienia włączonego (domyślnie jest włączone) w celu uniknięcia podwójnej rezerwacji i zoptymalizowania dostępności członków personelu.

8. Wybierz **pozycję Użyj godzin** pracy, aby ustawić, że wszystkie godziny, w których można rezerwować, mają być dostępne dla członków personelu tylko  w godzinach pracy określonych w sekcji Godziny pracy na stronie Informacje służbowe.

    Usuwając zaznaczenie tego pola, pracownicy mogą mieć niestandardowe godziny, w przypadku których można dodatkowo ograniczyć możliwość rezerwacji. Jest to przydatne w sytuacjach, gdy członek personelu może być w miejscu tylko we wtorków i środach lub jeśli jego poranek jest poświęcany na jeden typ terminów, a po południu na inne typy.

    > [!NOTE]
    > W aplikacji Bookings można 100 członków personelu w kalendarzu aplikacji Bookings.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Nadaj użytkownikowi aplikacji Bookings uprawnienia użytkownika superzmiejscowego bez dodawania go jako personelu w aplikacji Bookings

Możesz chcieć dodać osobę do listy pracowników w aplikacji Bookings, nie dokonując jej dla klientów lub klientów. Gdy nadasz im uprawnienia administratora, zostanie administratorem skrzynki pocztowej rezerwacji. Uprawnienia administratora skrzynki pocztowej rezerwacji to uprawnienia pełnego dostępu i wysyłania do skrzynki pocztowej rezerwacji.

> [!NOTE]
> Te kroki działają tylko wtedy, gdy dodany użytkownik nie ma jeszcze przypisanej roli osoby  oglądającego w aplikacji Bookings.

1. [Połączenie do Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Przy użyciu programu PowerShell przypisz pełny dostęp za pomocą następujących poleceń:

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Następnie uruchom to polecenie, aby przypisać uprawnienia wysyłania jako.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Oto przykładowe polecenie programu PowerShell służące do dodawania Allie Bellew do skrzynki pocztowej rezerwowania dni firmy Contoso.

1. Pierwsze uruchomienie tego polecenia:

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Następnie uruchom to polecenie:

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew** ma teraz dostęp administratora, ale nie jest wyświetlana jako personel rezerwowalny w aplikacji Bookings.
