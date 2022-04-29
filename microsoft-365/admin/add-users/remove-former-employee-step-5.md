---
title: Krok 5. Udzielanie innym pracownikom dostępu do danych OneDrive i Outlook
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
description: Wykonaj kroki opisane w tym artykule, aby udzielić innemu pracownikowi dostępu do danych OneDrive i Outlook byłego pracownika.
ms.openlocfilehash: c710826d0403c6935127f14dade3dfe30a8b5c13
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129205"
---
# <a name="step-5---give-another-employee-access-to-onedrive-and-outlook-data"></a>Krok 5. Udzielanie innym pracownikom dostępu do danych OneDrive i Outlook

Gdy pracownik opuści organizację, będziesz chciał uzyskać dostęp do OneDrive i Outlook danych, utworzyć ich kopię zapasową i wybrać, czy przekazać je innemu pracownikowi.
  
## <a name="access-a-former-users-onedrive-documents"></a>Uzyskiwanie dostępu do dokumentów OneDrive byłego użytkownika

Jeśli usuniesz licencję użytkownika, ale nie usuniesz konta, możesz udzielić sobie dostępu do zawartości w OneDrive użytkownika. Jeśli usuniesz konto użytkownika, domyślnie masz 30 dni na dostęp do danych OneDrive byłego użytkownika. [Dowiedz się, jak ustawić przechowywanie OneDrive dla usuniętych użytkowników](/onedrive/set-retention). Jeśli w tym czasie nie [przywrócisz konta użytkownika](/office365/admin/add-users/restore-user), jego zawartość OneDrive zostanie usunięta.

Aby zachować pliki OneDrive byłego użytkownika, najpierw przyznaj sobie dostęp do OneDrive, a następnie przenieś pliki, które chcesz zachować.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  

2. Wybierz użytkownika.

3. Na stronie właściwości użytkownika wybierz pozycję **OneDrive**. W obszarze **Uzyskiwanie dostępu do plików** wybierz pozycję **Utwórz link do plików**.

4. Wybierz link, aby otworzyć lokalizację pliku. Pobierz pliki na komputer lub wybierz pozycję **Przenieś do** lub **Kopiuj, aby** przenieść lub skopiować je do własnej OneDrive lub do biblioteki udostępnionej.

> [!NOTE]
> Możesz przenieść lub skopiować do 500 MB plików i folderów jednocześnie.<br/>
> Podczas przenoszenia lub kopiowania dokumentów z historią wersji jest przenoszona tylko najnowsza wersja.  

Możesz również udzielić dostępu innemu użytkownikowi w celu uzyskania dostępu do OneDrive byłego pracownika.

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnego</a> jako administrator globalny lub administrator SharePoint.

    Jeśli zostanie wyświetlony komunikat, że nie masz uprawnień dostępu do centrum administracyjnego, nie masz uprawnień administratora w organizacji.

2. W okienku po lewej stronie wybierz pozycję **Centra** \> administracyjne **SharePoint**. (Może być konieczne wybranie pozycji **Pokaż wszystko** , aby wyświetlić listę centrów administracyjnych).

3. Jeśli zostanie wyświetlone klasyczne centrum administracyjne SharePoint, wybierz pozycję **Otwórz teraz** w górnej części strony, aby otworzyć centrum administracyjne SharePoint.

4. W okienku po lewej stronie wybierz pozycję **Więcej funkcji**.

5. W obszarze **Profile użytkowników** wybierz pozycję **Otwórz**.

6. W obszarze **Osoby** wybierz pozycję **Zarządzaj profilami użytkowników**.

7. Wprowadź imię i nazwisko byłego pracownika i wybierz pozycję **Znajdź**.

8. Kliknij prawym przyciskiem myszy użytkownika, a następnie wybierz pozycję **Zarządzaj właścicielami zbioru witryn**.

9. Dodaj użytkownika do **administratorów zbioru witryn** i wybierz przycisk **OK**.

10. Użytkownik będzie teraz mógł uzyskać dostęp do OneDrive byłego pracownika przy użyciu adresu URL OneDrive. Aby uzyskać więcej informacji, zobacz [Informacje o adresach URL OneDrive](/onedrive/list-onedrive-urls#about-onedrive-urls).

### <a name="revoke-admin-access-to-a-users-onedrive"></a>Odwoływanie dostępu administratora do OneDrive użytkownika

Możesz udzielić sobie dostępu do zawartości w OneDrive użytkownika, ale możesz chcieć usunąć dostęp, gdy nie będzie już potrzebny.

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnego</a> jako administrator globalny lub administrator SharePoint.

    Jeśli zostanie wyświetlony komunikat, że nie masz uprawnień dostępu do centrum administracyjnego, nie masz uprawnień administratora w organizacji.

2. W okienku po lewej stronie wybierz pozycję **Centra** \> administracyjne **SharePoint**. (Może być konieczne wybranie pozycji **Pokaż wszystko** , aby wyświetlić listę centrów administracyjnych).

3. Jeśli zostanie wyświetlone klasyczne centrum administracyjne SharePoint, wybierz pozycję **Otwórz teraz** w górnej części strony, aby otworzyć centrum administracyjne SharePoint.

4. W okienku po lewej stronie wybierz pozycję **Więcej funkcji**.

5. W obszarze **Profile użytkowników** wybierz pozycję **Otwórz**.

6. W obszarze **Osoby** wybierz pozycję **Zarządzaj profilami użytkowników**.

7. Wprowadź nazwę użytkownika i wybierz pozycję **Znajdź**.

8. Kliknij prawym przyciskiem myszy użytkownika, a następnie wybierz pozycję **Zarządzaj właścicielami zbioru witryn**.

9. Usuń osobę, która nie potrzebuje już dostępu do danych użytkownika, a następnie wybierz przycisk **OK**.

## <a name="access-the-outlook-data-of-a-former-user"></a>Uzyskiwanie dostępu do danych Outlook byłego użytkownika

Aby zapisać wiadomości e-mail, kalendarz, zadania i kontakty byłego pracownika, wyeksportuj informacje do pliku danych Outlook (pst).
  
1. [Dodaj wiadomość e-mail byłego pracownika](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b) do Outlook. (Jeśli [resetujesz hasło użytkownika](reset-passwords.md), możesz ustawić je na coś, co znasz).

2. W Outlook wybierz pozycję **Plik**.

    ![Tak wygląda wstążka w Outlook 2016.](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. Wybierz pozycję **Otwórz &amp; Import/Export eksportu**\>.

    ![Import/Export polecenie w widoku Backstage.](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. Wybierz **pozycję Eksportuj do pliku**, a następnie wybierz pozycję **Dalej**.

    ![Wyeksportuj do opcji pliku w Kreatorze importu i eksportu.](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. Kliknij pozycję **Plik danych aplikacji Outlook (.pst)**, a następnie kliknij przycisk **Dalej**.

6. Wybierz konto, które chcesz wyeksportować, wybierając nazwę lub adres e-mail, na przykład Skrzynka pocztowa — Anne Weiler lub anne@contoso.com. Jeśli chcesz wyeksportować wszystkie elementy na koncie, w tym pocztę, kalendarz, kontakty, zadania i notatki, upewnij się, że **zaznaczono pole wyboru Dołącz podfoldery** .

    > [!NOTE]
    > Możesz wyeksportować jedno konto jednocześnie. Jeśli chcesz wyeksportować wiele kont, po wyeksportowaniu jednego konta powtórz te kroki.
  
    ![Wyeksportuj plik danych Outlook okno dialogowe z wybranym górnym folderem i zaznaczone opcje Uwzględnij podfoldery.](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. Wybierz pozycję **Dalej**.

8. Wybierz pozycję **Przeglądaj**, aby wybrać, gdzie zapisać plik danych Outlook (pst). Wpisz  *nazwę pliku*, a następnie wybierz przycisk **OK** , aby kontynuować.

    > [!NOTE]
    > Jeśli wcześniej użyto eksportu, zostanie wyświetlona poprzednia lokalizacja folderu i nazwa pliku. Przed wybraniem przycisku **OK** wpisz *inną nazwę pliku*.
  
9. Jeśli miejscem docelowym eksportu danych jest istniejący plik danych programu Outlook (pst), w obszarze **Opcje** określ, co należy zrobić, jeśli eksportowane elementy już znajdują się w pliku.

10. Wybierz **Zakończ**.

Outlook rozpoczyna eksport natychmiast, chyba że zostanie utworzony nowy plik danych Outlook (pst) lub zostanie użyty plik chroniony hasłem.
  
- Jeśli tworzysz plik danych Outlook (pst), opcjonalne hasło może pomóc w ochronie pliku. Gdy zostanie wyświetlone okno dialogowe **Tworzenie pliku danych Outlook**, wpisz *hasło* w polach **Hasło** i **Sprawdź hasło**, a następnie wybierz przycisk **OK**. W oknie dialogowym **hasło pliku danych Outlook** wpisz *hasło*, a następnie wybierz przycisk **OK**.

- Jeśli eksportujesz do istniejącego pliku danych Outlook (pst), który jest chroniony hasłem, w oknie dialogowym **hasło pliku danych Outlook** wpisz *hasło*, a następnie wybierz przycisk **OK**.

Zobacz, jak [eksportować lub tworzyć kopie zapasowe wiadomości e-mail, kontaktów i kalendarza do pliku pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) w Outlook 2010 r.

  > [!NOTE]
  > Domyślnie wiadomość e-mail jest dostępna w trybie offline przez okres 12 miesięcy. W razie potrzeby zobacz, jak [zwiększyć dostępność danych w trybie offline](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized).

### <a name="give-another-user-access-to-a-former-users-email"></a>Udzielanie innemu użytkownikowi dostępu do poczty e-mail byłego użytkownika

Aby udzielić dostępu do wiadomości e-mail, kalendarza, zadań i kontaktów byłego pracownika innemu pracownikowi, zaimportuj informacje do skrzynki odbiorczej Outlook innego pracownika.

> [!NOTE]
> Możesz również [przekonwertować skrzynkę pocztową byłego użytkownika na udostępnioną skrzynkę pocztową](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) lub [przekazać wiadomość e-mail byłego pracownika do innego pracownika](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox).

1. W Outlook przejdź do pozycji **Otwórz &amp;** **plik** \> eksportu \> **Import/Export**.

    Spowoduje to uruchomienie Kreatora importu i eksportu.

2. Kliknij pozycję **Importuj z innego programu lub pliku**, a następnie kliknij przycisk **Dalej**.

    ![Kreator importu i eksportu.](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. Wybierz **pozycję Outlook Plik danych (pst),** a następnie wybierz pozycję **Dalej**.

4. Przejdź do pliku pst, który chcesz zaimportować.

5. W obszarze **Opcje** wybierz, jak chcesz postępować z duplikatami.

6. Wybierz pozycję **Dalej**.

7. Jeśli hasło zostało przypisane do pliku danych Outlook (pst), wprowadź hasło, a następnie wybierz przycisk **OK**.

8. Ustaw opcje importowania elementów. Ustawienia domyślne zwykle nie muszą być zmieniane.

9. Wybierz **Zakończ**.

> [!NOTE]
> Kroki pozostają takie same w przypadku uzyskiwania dostępu do danych OneDrive i poczty e-mail istniejącego użytkownika.

> [!TIP]
> Jeśli chcesz zaimportować lub przywrócić tylko kilka elementów z pliku danych Outlook (pst), możesz otworzyć plik danych Outlook. Następnie w okienku nawigacji przeciągnij elementy z folderów Outlook Data File do istniejących folderów Outlook.

## <a name="related-content"></a>Zawartość pokrewna

[Dodawanie i usuwanie administratorów na koncie OneDrive](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive) (artykuł)

[Przywracanie usuniętego OneDrive](/onedrive/restore-deleted-onedrive) (artykuł)

[OneDrive przechowywania i usuwania](/onedrive/retention-and-deletion) (artykuł)

[Udostępnianie plików i folderów OneDrive](https://support.microsoft.com/office/share-onedrive-files-and-folders-9fcc2f7d-de0c-4cec-93b0-a82024800c07)
