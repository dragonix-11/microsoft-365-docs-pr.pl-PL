---
title: Konfigurowanie ustawień udostępnionej skrzynki pocztowej
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Utwórz udostępnioną skrzynkę pocztową i skonfiguruj niektóre ustawienia dla użytkowników, takie jak przekazywanie wiadomości e-mail i odpowiedzi automatyczne.
ms.openlocfilehash: b3de51a8407c8f9786d6a1677137f2a564744ac0
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437156"
---
# <a name="configure-microsoft-365-shared-mailbox-settings"></a>Konfigurowanie Microsoft 365 ustawień udostępnionej skrzynki pocztowej

Po [utworzeniu udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) należy skonfigurować niektóre ustawienia dla użytkowników skrzynki pocztowej, takie jak przekazywanie wiadomości e-mail i odpowiedzi automatyczne. Później możesz zmienić inne ustawienia, takie jak nazwa skrzynki pocztowej, członkowie lub uprawnienia członka. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Zmień nazwę lub alias wiadomości e-mail udostępnionej skrzynki pocztowej lub zmień podstawowy adres e-mail

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Edytuj** obok **pozycji Nazwa, Adres e-mail, Aliasy poczty e-mail**.

3. Wprowadź nową nazwę lub dodaj inny alias. Jeśli chcesz zmienić podstawowy adres e-mail, skrzynka pocztowa musi mieć więcej niż jeden alias wiadomości e-mail.

4. Wybierz **Zapisz**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Przesyłanie dalej wiadomości e-mail wysłanych do udostępnionej skrzynki pocztowej

Nie musisz przypisywać licencji do udostępnionej skrzynki pocztowej, aby przesłać wiadomość e-mail, która zostanie do niej wysłana. Wiadomości można przekazywać dalej na dowolny prawidłowy adres e-mail lub listę dystrybucyjną.

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Edytuj** przekazywanie \> **wiadomości e-mail**.
    
3. Ustaw przełącznik **na Wł**., a następnie wprowadź jeden adres e-mail, na który chcesz przekazać wiadomości dalej. Może to być dowolny prawidłowy adres e-mail. Aby przesłać dalej do wielu adresów, należy [utworzyć grupę dystrybucyjną](/office365/admin/setup/create-distribution-lists) dla adresów, a następnie wprowadzić nazwę grupy w tym polu.
    
4. Wybierz **Zapisz**.

## <a name="send-automatic-replies-from-a-shared-mailbox"></a>Wysyłanie odpowiedzi automatycznych z udostępnionej skrzynki pocztowej

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Automatyczne odpowiedzi** **Edytuj**\>.
    
3. Ustaw przełącznik w pozycji **Włączone** i określ, czy odpowiedź ma być wysyłana do osób w organizacji, czy do osób spoza organizacji.

4. Wprowadź odpowiedź, którą chcesz wysłać do osób w organizacji. Nie można dodawać obrazów, tylko tekst.

5. Jeśli chcesz *również* wysłać odpowiedź do osób spoza organizacji, zaznacz to pole wyboru, komu chcesz uzyskać odpowiedź, i wpisz tekst. Nie można wysłać odpowiedzi tylko do osób spoza organizacji i nie wysłać jej do osób w organizacji.

6. Wybierz **Zapisz**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Zezwalanie wszystkim na wyświetlanie wysłanych wiadomości e-mail (odpowiedzi)

Domyślnie wiadomości wysłane z udostępnionej skrzynki pocztowej nie są zapisywane w folderze Elementy wysłane tej skrzynki. Zamiast tego są zapisywane w folderach Elementy wysłane osób, które je wysłały.

Jeśli chcesz zezwolić wszystkim na wyświetlanie wysłanej wiadomości e-mail, w centrum administracyjnym edytuj ustawienia udostępnionej skrzynki pocztowej i wybierz pozycję **Wysłane elementy** **Edytuj**\>.


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Wybierz aplikacje, których udostępniona skrzynka pocztowa może używać do uzyskiwania dostępu do poczty e-mail firmy Microsoft

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Edytuj** aplikacje \> **poczty e-mail**.

3. Ustaw przełącznik **na Wł.** dla wszystkich aplikacji, których członkowie mają mieć dostęp do udostępnionej skrzynki pocztowej. Ustaw przełącznik na **wartość Wyłączone** dla wszystkich aplikacji, których nie chcesz używać. 

4. Wybierz **Zapisz**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Wstrzymanie udostępnionej skrzynki pocztowej

Aby dowiedzieć się więcej na temat blokady sporów sądowych, zobacz [Tworzenie blokady postępowania sądowego](../../compliance/create-a-litigation-hold.md).

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Edytuj blokadę** \> sporów.

3. Ustaw przełącznik na **Wł**. 

4. Opcjonalnie wprowadź czas trwania, zanotuj blokadę i adres URL z większą ilością informacji.  

5. Wybierz **Zapisz**.


## <a name="add-or-remove-members"></a>Dodawanie lub usuwanie członków

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Członkowie Edytuj**\>.

3. Wykonaj jeden z następujących kroków:
   - Aby dodać członków, wybierz pozycję **Dodaj członków**, wyszukaj lub wybierz członka do dodania, a następnie wybierz pozycję **Zapisz**.
   - Aby usunąć członków, użyj pola Wyszukaj, aby w razie potrzeby wyszukać członka, wybierz znak **X** obok nazwy członka, a następnie wybierz pozycję **Zapisz**. 

4. Ponownie wybierz pozycję **Zapisz** .

## <a name="add-or-remove-permissions-of-members"></a>Dodawanie lub usuwanie uprawnień członków

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Członkowie** \> **Dostosuj uprawnienia**.

3. Wybierz pozycję **Edytuj** obok uprawnienia, które chcesz zmienić dla członka. 

4. Wykonaj jeden z następujących kroków:
   - Aby nadać to uprawnienie dodatkowemu członkowi, wybierz pozycję **Dodaj uprawnienia**, wyszukaj lub wybierz element członkowski do dodania, a następnie wybierz pozycję **Zapisz**.
   - Aby usunąć uprawnienie od członka, użyj pola Wyszukaj, aby wyszukać członka w razie potrzeby, wybierz znak **X** obok nazwy członka, a następnie wybierz pozycję **Zapisz**. 

4. Ponownie wybierz pozycję **Zapisz** .

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Pokaż lub ukryj udostępnioną skrzynkę pocztową na globalnej liście adresów

Jeśli nie chcesz pokazywać udostępnionej skrzynki pocztowej na globalnej liście adresów, skrzynka pocztowa nie będzie wyświetlana na liście adresów organizacji, ale nadal będzie otrzymywać wiadomości e-mail wysłane do niej. 

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Udostępnione skrzynki pocztowe</a> **grupy**\>.

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Pokaż na globalnej liście adresowej** \> **Edytuj**.

3. Ustaw przełącznik na **wartość Włączone**  lub **Wyłączone**. 

4. Wybierz **Zapisz**.

> [!NOTE]
> Ukrycie udostępnionej skrzynki pocztowej z listy adresowej uniemożliwi nowym członkom udostępnionej skrzynki pocztowej dodanie ukrytej skrzynki pocztowej do profilu Outlook, dopóki udostępniona skrzynka pocztowa nie zostanie ponownie wyświetlona na liście adresów. 

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)