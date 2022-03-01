---
title: Krok 5. Nadaj innecie pracownika dostęp do OneDrive i Outlook danych
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Wykonaj czynności opisane w tym artykule, aby udzielić iniektowi dostępu do danych OneDrive i Outlook pracownika.
ms.openlocfilehash: 9c56e58de7a7bdbf1cec32ab3fc400c8b3b1b30c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011357"
---
# <a name="step-5---give-another-employee-access-to-onedrive-and-outlook-data"></a>Krok 5. Nadaj innecie pracownika dostęp do OneDrive i Outlook danych

Gdy pracownik odchodzi z organizacji, warto uzyskać dostęp do danych OneDrive i Outlook, wrócić do kopii zapasowej i zdecydować, czy przekazać ją inowi pracownikowi.
  
## <a name="access-a-former-users-onedrive-documents"></a>Uzyskiwanie dostępu do dokumentów OneDrive użytkownika

Jeśli usuniesz licencję użytkownika, ale nie usuniesz konta, możesz udzielić sobie dostępu do zawartości w treści OneDrive. Jeśli usuniesz konto użytkownika, domyślnie masz 30 dni na uzyskanie dostępu do danych OneDrive użytkownika. [Dowiedz się, jak ustawić przechowywanie OneDrive usuniętego użytkownika](/onedrive/set-retention). Jeśli konto użytkownika nie [zostanie w tym](/office365/admin/add-users/restore-user) czasie przywrócone, jego OneDrive zostanie usunięta.

Aby zachować pliki OneDrive użytkownika, najpierw nadaj mu dostęp OneDrive, a następnie przenieś pliki, które chcesz zachować.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  

2. Wybierz użytkownika.

3. Na stronie właściwości użytkownika wybierz pozycję **OneDrive**. W **obszarze Uzyskaj dostęp do plików** wybierz **pozycję Utwórz link do plików**.

4. Wybierz link, aby otworzyć lokalizację pliku. Pobierz pliki na komputer albo wybierz pozycję Przenieś do  lub Kopiuj,  aby przenieść lub skopiować je do własnej biblioteki OneDrive lub do biblioteki udostępnionej.

> [!NOTE]
> Możesz przenieść lub skopiować maksymalnie 500 MB plików i folderów jednocześnie.<br/>
> W przypadku przenoszenia lub kopiowania dokumentów z historią wersji jest przenoszony tylko najnowsza wersja.  

Możesz również udzielić dostępu inowi użytkownikowi, aby uzyskać dostęp do konta OneDrive.

1. Zaloguj się do centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">administracyjnego jako</a> administrator globalny lub administrator SharePoint administratorem.

    Jeśli zostanie wyświetlony komunikat informujący, że nie masz uprawnień dostępu do centrum administracyjnego, oznacza to, że nie masz uprawnień administratora w organizacji.

2. W okienku po lewej stronie wybierz **pozycję Centra administracyjne** \> **SharePoint**. (Może być konieczne wybranie pozycji **Pokaż wszystko** , aby wyświetlić listę centrów aadministracyjnym).

3. Jeśli pojawi się SharePoint centrum administracyjne, wybierz pozycję Otwórz teraz w  górnej części strony, aby otworzyć SharePoint administracyjnego.

4. W okienku po lewej stronie wybierz **pozycję Więcej funkcji**.

5. W **obszarze Profile użytkowników** wybierz pozycję **Otwórz**.

6. W **obszarze Osoby** wybierz pozycję **Zarządzaj profilami użytkowników**.

7. Wprowadź imię i nazwisko byłego pracownika, a następnie wybierz **pozycję Znajdź**.

8. Kliknij prawym przyciskiem myszy użytkownika, a następnie wybierz pozycję **Zarządzaj właścicielami zbioru witryn**.

9. Dodaj użytkownika do grupy **Administratorzy zbioru witryn i** wybierz przycisk **OK**.

10. Użytkownik będzie teraz mógł uzyskać dostęp do konta byłego pracownika OneDrive za pomocą adresu URL OneDrive URL. 

### <a name="revoke-admin-access-to-a-users-onedrive"></a>Odwoływanie uprawnień administratora do uprawnień dostępu użytkownika OneDrive

Możesz samodzielnie uzyskać dostęp do zawartości w profilu OneDrive, ale możesz chcieć usunąć dostęp, gdy nie jest już potrzebny.

1. Zaloguj się do centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">administracyjnego jako</a> administrator globalny lub administrator SharePoint administratorem.

    Jeśli zostanie wyświetlony komunikat informujący, że nie masz uprawnień dostępu do centrum administracyjnego, oznacza to, że nie masz uprawnień administratora w organizacji.

2. W okienku po lewej stronie wybierz **pozycję Centra administracyjne** \> **SharePoint**. (Może być konieczne wybranie pozycji **Pokaż wszystko** , aby wyświetlić listę centrów aadministracyjnym).

3. Jeśli pojawi się SharePoint centrum administracyjne, wybierz pozycję Otwórz teraz w  górnej części strony, aby otworzyć SharePoint administracyjnego.

4. W okienku po lewej stronie wybierz **pozycję Więcej funkcji**.

5. W **obszarze Profile użytkowników** wybierz pozycję **Otwórz**.

6. W **obszarze Osoby** wybierz pozycję **Zarządzaj profilami użytkowników**.

7. Wprowadź nazwę użytkownika i wybierz pozycję **Znajdź**.

8. Kliknij prawym przyciskiem myszy użytkownika, a następnie wybierz pozycję **Zarządzaj właścicielami zbioru witryn**.

9. Usuń osobę, która nie potrzebuje już dostępu do danych użytkownika, a następnie wybierz przycisk **OK**.

## <a name="access-the-outlook-data-of-a-former-user"></a>Uzyskiwanie dostępu Outlook danych byłego użytkownika

Aby zapisać wiadomości e-mail, kalendarz, zadania i kontakty byłego pracownika, wyeksportuj informacje do pliku Outlook danych (pst).
  
1. [Dodaj do wiadomości e-mail byłego](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b) pracownika Outlook. (Jeśli [zresetowasz hasło](reset-passwords.md) użytkownika, możesz je ustawić na coś, o czym tylko wiesz).

2. W Outlook wybierz pozycję **Plik**.

    ![Tak wygląda wstążka w aplikacji Outlook 2016.](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. Wybierz **pozycję Otwórz &amp; okno** \> **Import/Export**.

    ![Import/Export w widoku Backstage.](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. Wybierz **pozycję Eksportuj do pliku, a** następnie wybierz przycisk **Dalej**.

    ![Opcja Eksportowanie do pliku w Kreatorze importu i eksportu.](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. Kliknij pozycję **Plik danych aplikacji Outlook (.pst)**, a następnie kliknij przycisk **Dalej**.

6. Wybierz konto, które chcesz wyeksportować, wybierając nazwę lub adres e-mail, na przykład Skrzynka pocztowa — Irena Weiler lub anne@contoso.com. Jeśli chcesz wyeksportować wszystkie dane na koncie (w tym pocztę, kalendarz, kontakty, zadania i notatki), upewnij się, że pole wyboru Uwzględnij **podfoldery** jest zaznaczone.

    > [!NOTE]
    > Możesz eksportować tylko jedno konto na raz. Jeśli chcesz wyeksportować wiele kont, po wyeksportowaniu jednego konta powtórz te czynności.
  
    ![Okno Outlook eksportowania pliku danych z zaznaczonym górnym folderem i zaznaczoną oknie uwzględnij podfoldery.](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. Wybierz pozycję **Dalej**.

8. Wybierz **pozycję Przeglądaj**, aby wybrać miejsce do zapisania Outlook danych (pst). Wpisz nazwę  *pliku, a* następnie wybierz przycisk **OK** , aby kontynuować.

    > [!NOTE]
    > Jeśli wcześniej był używany eksport, zostanie wyświetlony poprzednia lokalizacja folderu i nazwa pliku. Przed *wybraniem przycisku OK wpisz* inną nazwę **pliku**.
  
9. Jeśli miejscem docelowym eksportu danych jest istniejący plik danych programu Outlook (pst), w obszarze **Opcje** określ, co należy zrobić, jeśli eksportowane elementy już znajdują się w pliku.

10. Wybierz **Zakończ**.

Outlook rozpocznie się eksport od razu, chyba Outlook zostanie utworzony nowy plik danych programu Outlook (pst) lub zostanie użyty plik chroniony hasłem.
  
- Jeśli tworzysz plik danych programu Outlook (pst), możesz utworzyć opcjonalne hasło do ochrony pliku. Gdy zostanie **wyświetlone Outlook** Tworzenie pliku danych, wpisz hasło w polach Hasło i  Zweryfikuj  hasło, a następnie wybierz przycisk **OK**. W **oknie Outlook** hasło do pliku danych wpisz *hasło*, a następnie wybierz przycisk **OK**.

- Jeśli eksportujesz dane do istniejącego pliku danych programu Outlook (pst), który jest chroniony hasłem, w oknie dialogowym Hasło do pliku danych programu Outlook wpisz *hasło,* **a** następnie wybierz przycisk **OK**.

Zobacz, jak [eksportować lub](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) tworzyć kopie zapasowe wiadomości e-mail, kontaktów i kalendarza Outlook pliku pst w programie Outlook 2010.

  > [!NOTE]
  > Domyślnie poczta e-mail jest dostępna w trybie offline przez 12 miesięcy. Jeśli jest to wymagane, zobacz, jak [zwiększyć liczbę danych dostępnych w trybie offline](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized).

### <a name="give-another-user-access-to-a-former-users-email"></a>Umożliwianie iniu użytkownikowi dostępu do poczty e-mail byłego użytkownika

Aby udzielić dostępu do wiadomości e-mail, kalendarza, zadań i kontaktów byłego pracownika inowiemniom, zaimportuj informacje do Outlook odbiorczej innego pracownika.

> [!NOTE]
> Możesz również [przekonwertować skrzynkę](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) pocztową byłego użytkownika na udostępnioną skrzynkę pocztową lub przesyłać dalej wiadomości [e-mail byłego pracownika do innego pracownika](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox).

1. W Outlook przejdź do **menu Otwórz** \> **okno eksportowania &amp;** \> **plików i Import/Export**.

    Zostanie uruchomiony Kreator importu i eksportu.

2. Kliknij pozycję **Importuj z innego programu lub pliku**, a następnie kliknij przycisk **Dalej**.

    ![Kreator importu i eksportu.](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. Wybierz **Outlook pliku danych (pst)** i wybierz przycisk **Dalej**.

4. Przejdź do pliku pst, który chcesz zaimportować.

5. W obszarze **Opcje** wybierz, jak chcesz postępować z duplikatami.

6. Wybierz pozycję **Dalej**.

7. Jeśli do pliku danych programu Outlook (pst) przypisano hasło, wprowadź hasło, a następnie wybierz przycisk **OK**.

8. Ustaw opcje importowania elementów. Ustawień domyślnych zwykle nie trzeba zmieniać.

9. Wybierz **Zakończ**.

> [!NOTE]
> Czynności, które należy wykonać, aby uzyskać dostęp do danych poczty e-mail OneDrive użytkownika, pozostają bez zmian.

> [!TIP]
> Jeśli chcesz zaimportować lub przywrócić tylko kilka elementów z pliku danych programu Outlook (pst), możesz otworzyć Outlook pliku danych. Następnie w okienku nawigacji przeciągnij elementy z Outlook Plik danych do istniejących Outlook folderów.

## <a name="related-content"></a>Zawartość pokrewna

[Dodawanie i usuwanie administratorów na koncie OneDrive (](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive)artykuł)

[Przywracanie usuniętego OneDrive](/onedrive/restore-deleted-onedrive) (artykuł)

[OneDrive przechowywania i usuwania](/onedrive/retention-and-deletion) (artykuł)

[Udostępnianie OneDrive i folderów](https://support.microsoft.com/office/share-onedrive-files-and-folders-9fcc2f7d-de0c-4cec-93b0-a82024800c07)
