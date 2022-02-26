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
description: Utwórz udostępnioną skrzynkę pocztową i skonfiguruj dla jej użytkowników pewne ustawienia, takie jak przesyłanie dalej poczty e-mail i odpowiedzi automatyczne.
ms.openlocfilehash: 201291adddf588bde955cbba7e2c0075e5ca7c88
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973560"
---
# <a name="configure-shared-mailbox-settings"></a>Konfigurowanie ustawień udostępnionej skrzynki pocztowej

Po [utworzeniu udostępnionej](create-a-shared-mailbox.md) skrzynki pocztowej należy skonfigurować pewne ustawienia dla użytkowników skrzynki pocztowej, takie jak przesyłanie dalej poczty e-mail i odpowiedzi automatyczne. Później możesz zechcieć zmienić inne ustawienia, takie jak nazwa skrzynki pocztowej, członkowie lub uprawnienia członków. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Zmienianie nazwy lub aliasu e-mail udostępnionej skrzynki pocztowej oraz zmienianie podstawowego adresu e-mail

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Edytuj** obok nazwy **, adresu e-mail, aliasów e-mail**.

3. Wprowadź nową nazwę lub dodaj kolejny alias. Jeśli chcesz zmienić podstawowy adres e-mail, skrzynka pocztowa musi mieć więcej niż jeden alias e-mail.

4. Wybierz **Zapisz**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Przesyłanie dalej wiadomości e-mail wysłanych do udostępnionej skrzynki pocztowej

Nie musisz przypisywać licencji do udostępnionej skrzynki pocztowej, aby przesyłać dalej wiadomości e-mail wysyłane do tej skrzynki. Wiadomości można przesyłać dalej na dowolny prawidłowy adres e-mail lub listę dystrybucyjną.

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Przesyłanie dalej wiadomości e-mail Edytuj**\>.
    
3. Ustaw przełącznik w ustawieniach **Wł.** i wprowadź jeden adres e-mail, na który wiadomości będą przekazywane dalej. Może to być dowolny prawidłowy adres e-mail. Aby przesyłać dalej wiadomości na wiele adresów, należy utworzyć grupę dystrybucyjną dla tych adresów, [a](/office365/admin/setup/create-distribution-lists) następnie wprowadzić nazwę grupy w tym polu.
    
4. Wybierz **Zapisz**.

## <a name="send-automatic-replies-from-a-shared-mailbox"></a>Wysyłanie odpowiedzi automatycznych z udostępnionej skrzynki pocztowej

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz **pozycję Edytuj odpowiedzi automatyczne** \> **.**
    
3. Ustaw przełącznik w pozycji **Włączone** i określ, czy odpowiedź ma być wysyłana do osób w organizacji, czy do osób spoza organizacji.

4. Wprowadź odpowiedź, którą chcesz wysłać do osób w organizacji. Nie można dodawać obrazów, tylko tekst.

5. Jeśli chcesz *również wysłać* odpowiedź do osób spoza organizacji, zaznacz pole wyboru, kto ma otrzymać odpowiedź, i wpisz tekst. Nie można wysłać odpowiedzi tylko do osób spoza organizacji i nie wysłać jej do osób w organizacji.

6. Wybierz **Zapisz**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Zezwalanie wszystkim na wyświetlanie wysłanych wiadomości e-mail (odpowiedzi)

Domyślnie wiadomości wysłane z udostępnionej skrzynki pocztowej nie są zapisywane w folderze Elementy wysłane tej skrzynki. Zamiast tego są zapisywane w folderach Elementy wysłane osób, które je wysłały.

Jeśli chcesz zezwolić wszystkim na wyświetlanie wysłanych wiadomości e-mail, w centrum administracyjnym edytuj ustawienia udostępnionej skrzynki pocztowej, a następnie wybierz pozycję **Edytuj elementy wysłane** \> **.**


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Wybieranie aplikacji, za pomocą których udostępniona skrzynka pocztowa może uzyskać dostęp do poczty e-mail Microsoft

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję Edytuj w **aplikacjach poczty e-mail**\>.

3. Ustaw przełącznik wł **. dla** wszystkich aplikacji, których członkowie będą mogli używać w celu uzyskiwania dostępu do udostępnionej skrzynki pocztowej. Ustaw przełącznik w opcji **Wyłączone dla** wszystkich aplikacji, których nie chcesz używać. 

4. Wybierz **Zapisz**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Zawieszenie udostępnionej skrzynki pocztowej w przypadku sporu sądowego

Aby dowiedzieć się więcej na temat postępowania w związku z postępowaniem sądowym, zobacz [Tworzenie postępowania w związku z postępowaniem sądowym](../../compliance/create-a-litigation-hold.md).

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję Edycja w związku z postępowaniem **sądowym**\>.

3. Ustaw przełącznik w przycisku **Wł**. 

4. Opcjonalnie wprowadź czas trwania, uwagę na temat blokowania oraz adres URL z większej liczby informacji.  

5. Wybierz **Zapisz**.


## <a name="add-or-remove-members"></a>Dodawanie lub usuwanie członków

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Edycja członków**\>.

3. Wykonaj jeden z następujących kroków:
   - Aby dodać członków, wybierz **pozycję Dodaj członków**, wyszukaj lub wybierz członka do dodania, a następnie wybierz pozycję **Zapisz**.
   - Aby usunąć członków, w razie potrzeby użyj pola wyszukiwania, aby wyszukać członka, wybierz znak **X** obok jego nazwy, a następnie wybierz pozycję **Zapisz**. 

4. Ponownie **wybierz pozycję** Zapisz.

## <a name="add-or-remove-permissions-of-members"></a>Dodawanie lub usuwanie uprawnień członków

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz **pozycję Członkowie Dostosowywanie** \> **uprawnień**.

3. Wybierz **pozycję Edytuj** obok uprawnień, które chcesz zmienić dla członka. 

4. Wykonaj jeden z następujących kroków:
   - Aby nadać to uprawnienie dodatkoweowi członkowskiemu, wybierz pozycję **Dodaj** uprawnienia, wyszukaj lub wybierz członka do dodania, a następnie wybierz pozycję **Zapisz**.
   - Aby usunąć uprawnienie od członka, w razie potrzeby użyj pola wyszukiwania w celu wyszukania członka, wybierz znak **X** obok jego nazwy, a następnie wybierz pozycję **Zapisz**. 

4. Ponownie **wybierz pozycję** Zapisz.

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Pokazywanie lub ukrywanie udostępnionej skrzynki pocztowej na globalnej liście adresowej

Jeśli nie chcesz pokazywać udostępnionej skrzynki pocztowej na globalnej liście adresowej, nie będzie ona wyświetlana na liście adresów organizacji, ale nadal będzie otrzymywać wiadomości e-mail wysłane do tej skrzynki. 

1. W centrum administracyjnym przejdź do strony **Grupy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">udostępnione skrzynki pocztowe</a> .

2. Wybierz udostępnioną skrzynkę pocztową, którą chcesz edytować, a następnie wybierz pozycję **Pokaż na globalnej liście adresowej Edytuj**\>.

3. Ustaw przełącznik w opcji **Wł.**  lub **Wył**. 

4. Wybierz **Zapisz**.

> [!NOTE]
> Ukrycie udostępnionej skrzynki pocztowej na liście adresów uniemożliwi nowym członkom udostępnionej skrzynki pocztowej dodanie ukrytej skrzynki pocztowej do ich profilu Outlook, dopóki udostępniona skrzynka pocztowa nie zostanie ponownie wyświetlona na liście adresów. 

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)