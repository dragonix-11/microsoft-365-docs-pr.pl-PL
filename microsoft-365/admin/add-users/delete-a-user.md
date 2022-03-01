---
title: Usuwanie użytkownika z własnej organizacji
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
- SPO_Content
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: Dowiedz się, jak usunąć konto użytkownika i co zrobić z pocztą e-mail i zawartością OneDrive użytkownika oraz czy zachować licencję produktu.
ms.openlocfilehash: 462e9bcec4dac7e9d708618777ea58fb5d182473
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995929"
---
# <a name="delete-a-user-from-your-organization"></a>Usuwanie użytkownika z własnej organizacji
  
**Szukasz sposobu usunięcia *własnego konta* Microsoft 365, którego używasz w pracy lub w szkole? Skontaktuj się z pomocą techniczną w miejscu pracy lub na uczelni, aby wykonać te czynności za Ciebie.**

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Tylko osoby, które [mają Microsoft 365 administratora globalnego](about-admin-roles.md) lub uprawnienia do zarządzania użytkownikami w firmie lub szkole, mogą usuwać konta użytkowników.
- Przed upływem 30 dni można [przywrócić](restore-user.md) konto  później dane użytkownika zostają trwale usunięte.
- Jeśli chcesz zachować dane usługi OneDrive użytkownika, przenieś je do innej lokalizacji. Możesz nawet przenieść dane do 30 dni po usunięciu konta. Zobacz [Uzyskiwanie dostępu do danych byłego użytkownika i tworzenie kopii zapasowej tych danych](get-access-to-and-back-up-a-former-user-s-data.md). Przenoszenie plików programu SharePoint nie jest konieczne, ponieważ zachowasz do nich dostęp.
- Jeśli chcesz zachować pocztę e-mail użytkownika, przenieś ją do innej lokalizacji **PRZED** usunięciem jego konta. Jeśli konto zostało już usunięte, przywróć je przed upływem 30 dni, przenieś dane poczty e-mail, a następnie ponownie usuń konto. Zobacz [Uzyskiwanie dostępu do danych byłego użytkownika i tworzenie kopii zapasowej tych danych](get-access-to-and-back-up-a-former-user-s-data.md).
- Jeśli masz subskrypcję usługi Enterprise, na przykład Office 365 Enterprise E3, możesz zachować dane skrzynki pocztowej usuniętego konta użytkownika, przekształcając ją w nieaktywną *skrzynkę pocztową*. Aby uzyskać więcej informacji, zobacz [Zarządzanie nieaktywnymi skrzynkami pocztowymi w usłudze Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Administrator globalny: Usuń użytkownika, przestań płacić za jego licencję i wybierz co zrobić z jego adresem e-mail i zawartością usługi OneDrive

Jeśli jesteś administratorem globalnym, po usunięciu użytkownika możesz również udostępnić dostęp do jego poczty e-mail innemu użytkownikowi i wybrać co zrobić z zawartością usługi OneDrive.

### <a name="things-to-consider"></a>Kwestie do rozważenia

Zanim rozpoczniesz, zastanów się, co chcesz zrobić z pocztą e-mail i zawartością usługi OneDrive danego użytkownika oraz czy chcesz zachować licencję lub przestać za nią płacić.
  
|Element | Opis |
|:-----|:-----|
|Licencje na produkty  <br/> |Możesz odebrać licencję użytkownikowi i usunąć go ze swojej subskrypcji, aby przestać płacić za tę licencję. Jeśli wybierzesz tę opcję, licencja zostanie automatycznie usunięta z subskrypcji.  <br/><br/> **Nie można usuwać licencji**, jeśli zakupiono ją za pośrednictwem partnera lub licencjonowania zbiorowego. Jeśli płacisz w planie rocznym lub jesteś w trakcie cyklu rozliczeniowego, nie możesz usunąć licencji z subskrypcji do momentu ukończenia zobowiązania.  <br/> |
|Zawartość usługi OneDrive  <br/> |Jeśli użytkownik zapisał pliki w usłudze OneDrive, możesz przekazać dostęp do nich innemu użytkownikowi.  <br/><br/> Musisz przenieść pliki, które chcesz zachować w trakcie okresu przechowywania ustawionego dla plików usługi OneDrive. **Domyślny okres przechowywania wynosi 30 dni.** Jeśli nie przeniesiesz plików w okresie przechowywania po usunięciu użytkownika, OneDrive usuniętego użytkownika jest przenoszony do Kosza zbioru witryn, w którym jest przechowywany przez 93 dni. W tym czasie użytkownicy nie będą już mogli uzyskać dostępu do żadnej zawartości udostępnionej w OneDrive. Aby przywrócić OneDrive, musisz użyć programu PowerShell. Aby uzyskać informacje, [zobacz Przywracanie usuniętego OneDrive](/onedrive/restore-deleted-onedrive).<br/><br/> Aby zwiększyć liczbę dni przechowywania plików usługi OneDrive dla usuniętego konta, zobacz [Ustawianie domyślnego okresu przechowywania w usłudze OneDrive dla usuniętych użytkowników](/onedrive/set-retention).  <br/><br/> **Ważne!** Jeśli w celu pobrania plików z programu SharePoint i OneDrive usunięty użytkownik użył komputera osobistego, nie ma sposobu na wyczyszczenie plików przechowywanych na jego komputerze. Nadal będzie mieć dostęp do wszystkich plików, które zostały zsynchronizowane z usługą OneDrive.           |
|Poczta e-mail  <br/> | Przyznanie innemu użytkownikowi dostępu do poczty e-mail usuniętego użytkownika zmieni ją w skrzynkę współużytkowaną. Nowy właściciel skrzynki pocztowej posiada wtedy do niej dostęp i może sprawdzać nowe wiadomości. Dostępne są również następujące opcje:  <br/>  <br/>Zmienianie nazwy wyświetlanej — zalecamy zmianę nazwy wyświetlanej, tak aby można było łatwo zidentyfikować udostępnioną skrzynkę pocztową na **liście Aktywni** użytkownicy.  <br/>  Włączenie odpowiedzi automatycznych  napisaliśmy dla Ciebie odpowiednią odpowiedź automatyczną. Możesz wysyłać różne odpowiedzi automatyczne do osób w Twojej organizacji i spoza organizacji.  <br/> <br/> Oczyszczanie aliasów — aliasy to dodatkowe adresy e-mail dla użytkowników. Niektóre organizacje z nich nie korzystają, więc jeśli nie masz żadnych innych, nie musisz w tym miejscu nic więcej robić. Jeśli użytkownik ma aliasy, zalecamy ich usunięcie, aby można było ponownie używać tych adresów e-mail. W przeciwnym razie nie możesz ponownie używać tych adresów e-mail, dopóki nie minął okres przechowywania usuniętych skrzynek pocztowych. Domyślnie usuniętą skrzynkę pocztową można odzyskać przez 30 dni. Aby uzyskać więcej informacji, zobacz [Usuwanie lub przywracanie skrzynek pocztowych użytkowników w aplikacji Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |Jeśli Twoja firma korzysta z usługi **Active Directory** synchronizowanej z usługą Azure Active Directory, konieczne będzie usunięcie tego konta użytkownika z usługi Active Directory. Nie można tego zrobić za pośrednictwem usługi Office 365. Aby uzyskać instrukcje, [zobacz Usuwanie konta użytkownika](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).  <br/> |

### <a name="get-started"></a>Wprowadzenie

Przewodnik krok po usunięciu użytkownika jest krok po jego usunięciu, dlatego poniżej opisano, jak rozpocząć pracę.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz użytkownika, którego chcesz usunąć, a następnie wybierz pozycję **Usuń użytkownika**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrator zarządzający użytkownikami: Usuwanie jednego lub kilku użytkowników z usługi Office 365

> [!IMPORTANT]
> Nie usuwaj konta użytkownika, jeśli przekonwertowano je na udostępnioną [](../email/convert-user-mailbox-to-shared-mailbox.md) skrzynkę pocztową lub dla konta ustawiono przesyłanie dalej poczty e-mail. Te funkcje nadal potrzebują konta. Udostępniona skrzynka pocztowa nie wymaga licencji. Jeśli przekonwertowano konto na udostępnioną skrzynkę pocztową, możesz przestać [płacić za licencję](#stop-paying-for-the-license). Jeśli na koncie jest już ustawione przesyłanie dalej poczty e-mail, nie można usunąć licencji. To spowoduje zatrzymanie przesyłania dalej poczty e-mail i dezaktywowanie skrzynki pocztowej.
  
::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Zaznacz nazwy użytkowników, których chcesz usunąć, zaznacz trzy kropki (więcej akcji), a następnie wybierz  **pozycję Usuń użytkownika**.

   Mimo usunięcia konta użytkownika nadal **płacisz za licencję**. Zobacz następną procedurę, aby przestać płacić za licencję.  Możesz też przypisać licencję do innego użytkownika. Nie zostanie ona przypisana do kogoś automatycznie.

### <a name="stop-paying-for-the-license"></a>Zablokowanie naliczania opłat za licencję

Zmniejszenie liczby licencji to osobny krok, który może wykonać tylko administrator globalny lub administrator rozliczeń.
  
::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">z produktami</a> .
::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">z produktami</a> .
::: moniker-end

2. Na **karcie Produkty** wybierz subskrypcję, dla której chcesz usunąć licencje.

3. Na stronie szczegółów subskrypcji wybierz pozycję **Usuń licencje**.

4. W **okienku Usuwanie licencji** w obszarze Nowa liczba w polu Łączna liczba  licencji wprowadź łączną liczbę licencji, które chcesz uzyskać dla tej subskrypcji. Jeśli na przykład masz 100 licencji i chcesz usunąć pięć z nich, wprowadź wartość 95.

5. Wybierz **Zapisz**.

Później, gdy dodasz kolejną osobę do swojej firmy, zostanie wyświetlony monit o zakup licencji w tym samym czasie, tylko o jeden krok!

## <a name="delete-many-users-at-the-same-time"></a>Usuwanie kilku użytkowników jednocześnie

Zobacz polecenie cmdlet programu PowerShell: [Remove-MsolUser](/powershell/module/msonline/remove-msoluser).

## <a name="fix-issues-with-deleting-a-user"></a>Rozwiązywanie problemów podczas usuwania użytkownika

Oto najczęstsze problemy napotykane przez osoby usuwające użytkownika:
  
- **Pojawia się komunikat o błędzie wraz z następującymi informacjami: „Nie można usunąć użytkownika. Spróbuj ponownie później".** Sprawdź dwukrotnie, czy dla konta nie zostało ustawione przesyłanie dalej poczty e-mail, czy konto nie zostało przekonwertowane na udostępnioną skrzynkę pocztową. W obu tych przypadkach zostanie zwrócony błąd. Nie usuwaj konta, dla którego skonfigurowano funkcję przesyłania dalej poczty e-mail, ani konta przekonwertowanego na udostępnioną skrzynkę pocztową.

- **Brak odpowiednich uprawnień do usunięcia użytkownika**. Tylko osoby, które [Microsoft 365 administratorami globalnymi lub administratorami zarządzającymi użytkownikami](about-admin-roles.md) mogą usuwać użytkowników. Zazwyczaj są to pracownicy pomocy technicznej w szkole lub w firmie.

- **Po usunięciu konta użytkownika jego nazwa nadal pojawia się w globalnej książce adresowej**. Taka sytuacja ma miejsce, gdy firma korzysta z usługi Active Directory. Należy usunąć konto użytkownika z usługi Active Directory. Aby uzyskać instrukcje, [zobacz Usuwanie konta użytkownika.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Czy chcesz usunąć pliki Microsoft 365 z komputera? Przejdź do [anulowanie subskrypcji](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-content"></a>Zawartość pokrewna

[Przywracanie użytkownika](restore-user.md) (artykuł)\
[Trwałe usuwanie skrzynki pocztowej](/exchange/permanently-delete-a-mailbox-exchange-2013-help) (artykuł)\
[Usuwanie byłego pracownika z Office 365](remove-former-employee.md) (artykuł)\
[Dodawanie nowego pracownika do Office 365](add-new-employee.md) (artykuł)\
[Usunąć konto użytkownika](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)). Skorzystaj z tych instrukcji, jeśli Twoja firma korzysta z usługi **Active Directory** synchronizowej z usługą Azure AD. Nie można tego zrobić za pośrednictwem usługi Office 365. (article)
