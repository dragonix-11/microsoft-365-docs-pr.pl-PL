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
description: Dowiedz się, jak usunąć konto użytkownika oraz co zrobić z wiadomością e-mail użytkownika i zawartością OneDrive oraz jak zachować licencję produktu.
ms.openlocfilehash: 894bcef6cc273c067b3d9b622f244d361ed24d96
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090712"
---
# <a name="delete-a-user-from-your-organization"></a>Usuwanie użytkownika z własnej organizacji
  
**Szukasz sposobu usunięcia *własnego* konta użytkownika Microsoft 365, którego używasz w pracy lub szkole? Skontaktuj się z pomocą techniczną w swojej pracy lub na uniwersytecie, aby wykonać te kroki za Ciebie.**

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Tylko osoby, które mają [Microsoft 365 uprawnienia administratora globalnego](about-admin-roles.md) lub zarządzania użytkownikami dla firmy lub szkoły, mogą usuwać konta użytkowników.
- Przed upływem 30 dni można [przywrócić](restore-user.md) konto  później dane użytkownika zostają trwale usunięte.
- Jeśli chcesz zachować dane usługi OneDrive użytkownika, przenieś je do innej lokalizacji. Możesz nawet przenieść dane do 30 dni po usunięciu konta. Zobacz [Uzyskiwanie dostępu do danych byłego użytkownika i tworzenie kopii zapasowej tych danych](get-access-to-and-back-up-a-former-user-s-data.md). Przenoszenie plików programu SharePoint nie jest konieczne, ponieważ zachowasz do nich dostęp.
- Jeśli chcesz zachować pocztę e-mail użytkownika, przenieś ją do innej lokalizacji **PRZED** usunięciem jego konta. Jeśli konto zostało już usunięte, przywróć je przed upływem 30 dni, przenieś dane poczty e-mail, a następnie ponownie usuń konto. Zobacz [Uzyskiwanie dostępu do danych byłego użytkownika i tworzenie kopii zapasowej tych danych](get-access-to-and-back-up-a-former-user-s-data.md).
- Jeśli masz subskrypcję Enterprise, taką jak Office 365 Enterprise E3, możesz zachować dane skrzynki pocztowej usuniętego konta użytkownika, przekształcając je *w nieaktywną skrzynkę pocztową*. Aby uzyskać więcej informacji, zobacz [Zarządzanie nieaktywnymi skrzynkami pocztowymi w usłudze Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Administrator globalny: Usuń użytkownika, przestań płacić za jego licencję i wybierz co zrobić z jego adresem e-mail i zawartością usługi OneDrive

Jeśli jesteś administratorem globalnym, po usunięciu użytkownika możesz również udostępnić dostęp do jego poczty e-mail innemu użytkownikowi i wybrać co zrobić z zawartością usługi OneDrive.

### <a name="things-to-consider"></a>Kwestie do rozważenia

Zanim rozpoczniesz, zastanów się, co chcesz zrobić z pocztą e-mail i zawartością usługi OneDrive danego użytkownika oraz czy chcesz zachować licencję lub przestać za nią płacić.
  
|Element | Opis |
|:-----|:-----|
|Licencje na produkty  <br/> |Możesz odebrać licencję użytkownikowi i usunąć go ze swojej subskrypcji, aby przestać płacić za tę licencję. Jeśli wybierzesz tę opcję, licencja zostanie automatycznie usunięta z subskrypcji.  <br/><br/> **Nie można usuwać licencji**, jeśli zakupiono ją za pośrednictwem partnera lub licencjonowania zbiorowego. Jeśli płacisz za plan roczny lub jesteś w trakcie cyklu rozliczeniowego, nie będziesz w stanie usunąć licencji z subskrypcji do czasu zakończenia zobowiązania.  <br/> |
|Zawartość usługi OneDrive  <br/> |Jeśli użytkownik zapisał pliki w usłudze OneDrive, możesz przekazać dostęp do nich innemu użytkownikowi.  <br/><br/> Musisz przenieść pliki, które chcesz zachować w trakcie okresu przechowywania ustawionego dla plików usługi OneDrive. **Domyślny okres przechowywania wynosi 30 dni.** Jeśli nie przeniesiesz plików w okresie przechowywania po usunięciu użytkownika, OneDrive dla usuniętego użytkownika zostanie przeniesiony do kosza zbioru witryn, gdzie jest przechowywany przez 93 dni. W tym czasie użytkownicy nie będą już mogli uzyskiwać dostępu do żadnej udostępnionej zawartości w OneDrive. Aby przywrócić OneDrive, należy użyć programu PowerShell. Aby uzyskać informacje, zobacz [Przywracanie usuniętego OneDrive](/onedrive/restore-deleted-onedrive).<br/><br/> Aby zwiększyć liczbę dni przechowywania plików usługi OneDrive dla usuniętego konta, zobacz [Ustawianie domyślnego okresu przechowywania w usłudze OneDrive dla usuniętych użytkowników](/onedrive/set-retention).  <br/><br/> **Ważne!** Jeśli usunięty użytkownik używał komputera osobistego do pobierania plików z SharePoint i OneDrive, nie ma możliwości wyczyszczenia tych plików przechowywanych na komputerze. Nadal będzie mieć dostęp do wszystkich plików, które zostały zsynchronizowane z usługą OneDrive.           |
|Poczta e-mail  <br/> | Przyznanie innemu użytkownikowi dostępu do poczty e-mail usuniętego użytkownika zmieni ją w skrzynkę współużytkowaną. Nowy właściciel skrzynki pocztowej posiada wtedy do niej dostęp i może sprawdzać nowe wiadomości. Dostępne są również następujące opcje:  <br/>  <br/>Zmień nazwę wyświetlaną — zalecamy zmianę nazwy wyświetlanej tak, aby łatwo było zidentyfikować udostępnioną skrzynkę pocztową na liście **Aktywni użytkownicy** .  <br/>  <br/>  Włączenie odpowiedzi automatycznych  napisaliśmy dla Ciebie odpowiednią odpowiedź automatyczną. Możesz wysyłać różne odpowiedzi automatyczne do osób w organizacji i osób spoza organizacji. <br/> <br/> [Usuń wszystkie istniejące uprawnienia kalendarza](/powershell/module/exchange/remove-mailboxfolderpermission?view=exchange-ps) przy użyciu programu PowerShell. <br/> <br/> Czyszczenie aliasów — aliasy to dodatkowe adresy e-mail dla użytkowników. Niektóre organizacje ich nie używają, więc jeśli nie masz żadnych, nie musisz robić nic innego tutaj. Jeśli użytkownik ma aliasy, zalecamy ich usunięcie, aby można było ponownie użyć tych adresów e-mail. W przeciwnym razie nie można ponownie używać tych adresów e-mail, dopóki nie minie okres przechowywania usuniętych skrzynek pocztowych. Domyślnie usuniętą skrzynkę pocztową można odzyskać przez 30 dni. Aby uzyskać więcej informacji, zobacz [Usuwanie lub przywracanie skrzynek pocztowych użytkowników w Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |Jeśli Twoja firma korzysta z usługi **Active Directory** synchronizowanej z usługą Azure Active Directory, konieczne będzie usunięcie tego konta użytkownika z usługi Active Directory. Nie można tego zrobić za pośrednictwem usługi Office 365. Aby uzyskać instrukcje, zobacz [Usuwanie konta użytkownika](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).  <br/> |

### <a name="get-started"></a>Wprowadzenie

Ponieważ środowisko z przewodnikiem przechodzi przez kroki usuwania użytkownika, oto jak rozpocząć pracę.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz użytkownika, który chcesz usunąć, a następnie wybierz pozycję **Usuń użytkownika**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrator zarządzający użytkownikami: Usuwanie jednego lub kilku użytkowników z usługi Office 365

> [!IMPORTANT]
> Nie usuwaj konta użytkownika, jeśli [zostało ono przekonwertowane na udostępnioną skrzynkę pocztową](../email/convert-user-mailbox-to-shared-mailbox.md) lub skonfigurowano przekazywanie wiadomości e-mail na koncie. Te funkcje nadal potrzebują konta. Udostępniona skrzynka pocztowa nie wymaga licencji. Jeśli konto zostało przekonwertowane na udostępnioną skrzynkę pocztową, możesz [przestać płacić za licencję](#stop-paying-for-the-license). Jeśli skonfigurowano przekazywanie wiadomości e-mail na koncie, nie możesz usunąć licencji. Spowoduje to zatrzymanie przekazywania wiadomości e-mail i dezaktywowanie skrzynki pocztowej.
  
::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Wybierz nazwy użytkowników, których chcesz usunąć, wybierz trzy kropki (więcej akcji), a następnie wybierz pozycję  **Usuń użytkownika**.

   Mimo że usunięto konto użytkownika, **nadal płacisz za licencję**. Zapoznaj się z następną procedurą, aby zatrzymać płacenie za licencję.  Możesz też przypisać licencję innemu użytkownikowi. Nie zostanie on automatycznie przypisany do kogoś.

### <a name="stop-paying-for-the-license"></a>Zablokowanie naliczania opłat za licencję

Zmniejszenie liczby licencji jest oddzielnym krokiem, który może wykonać tylko administrator globalny lub administrator rozliczeń.
  
::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.
::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Twoje produkty</a>.
::: moniker-end

2. Na karcie **Produkty** wybierz subskrypcję, dla którą chcesz usunąć licencje.

3. Na stronie szczegółów subskrypcji wybierz pozycję **Usuń licencje**.

4. W okienku **Usuń licencje** w obszarze **Nowa ilość** w polu **Łączna liczba licencji** wprowadź całkowitą liczbę licencji, które mają być przeznaczone dla tej subskrypcji. Jeśli na przykład masz 100 licencji i chcesz usunąć pięć z nich, wprowadź 95.

5. Wybierz **Zapisz**.

Później, gdy przejdziesz przez kroki dodawania innej osoby do swojej firmy, zostanie wyświetlony monit o zakup licencji w tym samym czasie, z zaledwie jednym krokiem!

## <a name="delete-many-users-at-the-same-time"></a>Usuwanie kilku użytkowników jednocześnie

Zobacz polecenie cmdlet programu PowerShell: [Remove-MsolUser](/powershell/module/msonline/remove-msoluser).

## <a name="fix-issues-with-deleting-a-user"></a>Rozwiązywanie problemów podczas usuwania użytkownika

Poniżej przedstawiono najczęstsze problemy napotykane przez użytkowników podczas usuwania użytkownika:
  
- **Pojawia się komunikat o błędzie wraz z następującymi informacjami: „Nie można usunąć użytkownika. Spróbuj ponownie później".** Sprawdź dokładnie, czy konto ma skonfigurowane przekazywanie wiadomości e-mail, czy zostało przekonwertowane na udostępnioną skrzynkę pocztową. W obu tych przypadkach zostanie zwrócony błąd. Nie usuwaj konta, dla którego skonfigurowano funkcję przesyłania dalej poczty e-mail, ani konta przekonwertowanego na udostępnioną skrzynkę pocztową.

- **Brak odpowiednich uprawnień do usunięcia użytkownika**. Tylko osoby [Microsoft 365 administratorów globalnych lub administratorów zarządzania użytkownikami](about-admin-roles.md) mogą usuwać użytkowników. Zazwyczaj są to pracownicy pomocy technicznej w szkole lub w firmie.

- **Po usunięciu konta użytkownika jego nazwa nadal pojawia się w globalnej książce adresowej**. Taka sytuacja ma miejsce, gdy firma korzysta z usługi Active Directory. Musisz usunąć konto użytkowników z usługi Active Directory. Aby uzyskać instrukcje, zobacz [Usuwanie konta użytkownika.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Czy chcesz usunąć Microsoft 365 z komputera? Przejdź do [pozycji Anuluj subskrypcję](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-content"></a>Zawartość pokrewna

[Przywracanie użytkownika](restore-user.md) (artykuł)\
[Trwale usuń skrzynkę pocztową](/exchange/permanently-delete-a-mailbox-exchange-2013-help) (artykuł)\
[Usuwanie byłego pracownika z Office 365](remove-former-employee.md) (artykuł)\
[Dodawanie nowego pracownika do Office 365](add-new-employee.md) (artykuł)\
[Usuń konto użytkownika](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)): skorzystaj z tych instrukcji, jeśli Twoja firma korzysta z **usługi Active Directory** synchronizowanej z usługą Azure AD. Nie można tego zrobić za pośrednictwem usługi Office 365. (artykuł)
