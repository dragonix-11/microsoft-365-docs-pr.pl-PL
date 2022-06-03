---
title: Tworzenie udostępnionej skrzynki pocztowej
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 871a246d-3acd-4bba-948e-5de8be0544c9
description: Utwórz udostępnioną skrzynkę pocztową, aby umożliwić wielu użytkownikom w firmie dzielenie się odpowiedzialnością za odczytywanie i odpowiadanie na wiadomości e-mail wysyłane na jeden adres.
ms.openlocfilehash: 444be08a2083bf184d61ee206dfaa8ab53657b0b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864567"
---
# <a name="create-a-shared-mailbox"></a>Tworzenie udostępnionej skrzynki pocztowej 

> [!NOTE]
> Jeśli Organizacja korzysta ze środowiska Exchange hybrydowego, do tworzenia udostępnionych skrzynek pocztowych i zarządzania nimi należy użyć lokalnego <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a>. Zobacz [Tworzenie udostępnionych skrzynek pocztowych w centrum administracyjnym Exchange](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Jeśli nie masz pewności, czy chcesz utworzyć udostępnioną skrzynkę pocztową, czy grupę Microsoft 365 dla Outlook, zobacz [Porównanie grup](../create-groups/compare-groups.md), aby uzyskać wskazówki. Należy pamiętać, że obecnie nie można migrować udostępnionej skrzynki pocztowej do grupy Microsoft 365. Jeśli jest to coś, czego chcesz, daj nam znać, [głosując tutaj](https://go.microsoft.com/fwlink/?linkid=871518).

Tworzenie udostępnionych skrzynek pocztowych jest łatwe. Dzięki nim grupa osób może monitorować wiadomości e-mail i wysyłać je ze wspólnego adresu e-mail, takiego jak info@contoso.com. Gdy osoba z grupy odpowie na wiadomość wysłaną do udostępnionej skrzynki pocztowej, utworzona przez nią wiadomość jest wysyłana z udostępnionej skrzynki pocztowej, a nie z indywidualnej skrzynki tej osoby.

Udostępnione skrzynki pocztowe zawierają kalendarz udostępniony. Wiele małych firm lubi używać kalendarza udostępnionego jako miejsca, w którym wszyscy mogą wprowadzać swoje terminy. Jeśli na przykład masz trzech pracowników, którzy spotykają się z klientami, mogą oni wprowadzać swoje terminy w kalendarzu udostępnionym. W ten prosty sposób wszyscy zostają poinformowani, gdzie kto jest.

Przed utworzeniem udostępnionej skrzynki pocztowej przeczytaj [informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) , aby uzyskać więcej informacji.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą firmy Microsoft ds. małych firm](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="create-a-shared-mailbox-and-add-members"></a>Tworzenie udostępnionej skrzynki pocztowej i dodawanie członków
  
1. Zaloguj się przy użyciu konta administratora globalnego lub konta administratora Exchange. Jeśli zostanie wyświetlony komunikat "**Nie masz uprawnień dostępu do tej strony lub wykonasz tę akcję**", nie jesteś administratorem. 

::: moniker range="o365-worldwide"

2. W centrum administracyjnym przejdź do strony udostępnione <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">skrzynki pocztowe</a> **Teams & Grupy**\>.

::: moniker-end

::: moniker range="o365-21vianet"

2. W [centrum administracyjnym](https://go.microsoft.com/fwlink/p/?linkid=850627) przejdź do strony udostępnione **skrzynki pocztowe** **grup** \> Teams &.

::: moniker-end
    
3. Na stronie **Udostępnione skrzynki pocztowe** wybierz pozycję **+ Dodaj udostępnioną skrzynkę pocztową**. Wprowadź nazwę udostępnionej skrzynki pocztowej. Spowoduje to wybranie adresu e-mail, ale w razie potrzeby można go edytować.
    
    ![Name your shared mailbox.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Wybierz pozycję **Zapisz zmiany**. Może upłynąć kilka minut, zanim będzie możliwe dodanie członków.

5. W obszarze **Następne kroki** wybierz pozycję **Dodaj członków do tej skrzynki pocztowej**. Członkowie to osoby, które będą mogły wyświetlać pocztę przychodzącą do tej udostępnionej skrzynki pocztowej oraz wychodzące odpowiedzi.

   ![Wybierz pozycję Dodaj członków.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. Wybierz przycisk **+Dodaj członków** . Umieść znacznik wyboru obok osób, które mają korzystać z tej udostępnionej skrzynki pocztowej, a następnie wybierz pozycję **Zapisz**.

   ![Przypisz członków do udostępnionej skrzynki pocztowej.](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. Wybierz pozycję **Zamknij**.

Masz udostępnioną skrzynkę pocztową i zawiera ona kalendarz udostępniony. Przejdź do następnego kroku: [Blokuj logowanie do udostępnionego konta skrzynki pocztowej](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Jakich uprawnień należy użyć?

Możesz użyć następujących uprawnień w udostępnionej skrzynce pocztowej:

- **Pełny dostęp**: uprawnienie Pełny dostęp umożliwia użytkownikowi otwarcie udostępnionej skrzynki pocztowej i pełnienie roli właściciela tej skrzynki pocztowej. Po uzyskaniu dostępu do udostępnionej skrzynki pocztowej użytkownik może tworzyć elementy kalendarza, odczytywać, wyświetlać, usuwać i zmieniać wiadomości e-mail oraz tworzyć zadania i kontakty kalendarza. Użytkownik z uprawnieniami Pełny dostęp nie może jednak wysyłać wiadomości e-mail z udostępnionej skrzynki pocztowej, chyba że ma również uprawnienia Wyślij jako lub Wyślij w imieniu.

- **Wyślij jako**: uprawnienie Wyślij jako umożliwia użytkownikowi personifikowanie udostępnionej skrzynki pocztowej podczas wysyłania wiadomości e-mail. Jeśli na przykład Katerina zaloguje się do działu marketingu udostępnionej skrzynki pocztowej i wyśle wiadomość e-mail, będzie ona wyglądać tak, jakby dział marketingu wysłał wiadomość e-mail.

- **Wyślij w imieniu**: uprawnienie Wyślij w imieniu umożliwia użytkownikowi wysyłanie wiadomości e-mail w imieniu udostępnionej skrzynki pocztowej. Jeśli na przykład Jan zaloguje się do udostępnionego budynku recepcji skrzynki pocztowej 32 i wyśle wiadomość e-mail, będzie to wyglądać tak, jakby wiadomość została wysłana przez "Jana w imieniu budynku recepcji 32". Nie można użyć EAC do udzielenia uprawnień Wyślij w imieniu. Należy użyć polecenia cmdlet **Set-Mailbox** z parametrem _GrantSendonBehalf_ .

> [!NOTE]
> Uprawnienia **Wyślij jako** i **Wyślij w imieniu** nie działają w kliencie stacjonarnym Outlook z *parametrem HiddenFromAddressListsEnabled* w skrzynce pocztowej ustawionej na **wartość True**, ponieważ wymagają one, aby skrzynka pocztowa była widoczna w Outlook za pośrednictwem globalnej listy adresów.

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Edytowanie delegowania udostępnionej skrzynki pocztowej za pomocą Centrum administracyjnego programu Exchange

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a> przejdź do **obszaru Skrzynki pocztowe** **adresatów**\>. Wybierz udostępnioną skrzynkę pocztową, a następnie wybierz pozycję **Edytuj** ![ikonę Edycja.](../../media/ITPro-EAC-EditIcon.png)

2. W obszarze **Uprawnienia skrzynki pocztowej** wybierz pozycję **Zarządzaj delegowaniem skrzynki pocztowej**.

3. Aby udzielić lub usunąć uprawnienia Pełny dostęp i Wyślij jako, wybierz pozycję **Dodaj** ![ikonę.](../../media/ITPro-EAC-AddIcon.png) lub **Usuń** ![ikonę](../../media/ITPro-EAC-RemoveIcon.gif) Usuń, a następnie wybierz użytkowników, do których chcesz udzielić uprawnień.

   > [!NOTE]
   > Uprawnienia Pełny dostęp umożliwiają użytkownikowi otwieranie skrzynki pocztowej, a także tworzenie i modyfikowanie zawartych w niej elementów. Uprawnienia Wyślij jako umożliwiają każdej osobie innej niż właściciel skrzynki pocztowej wysyłanie wiadomość e-mail z tej udostępnionej skrzynki pocztowej. Oba uprawnienia są wymagane do obsługi udostępnionej skrzynki pocztowej.

4. Wybierz pozycję **Zapisz** , aby zapisać zmiany.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Blokuj logowanie do udostępnionego konta skrzynki pocztowej

Każda udostępniona skrzynka pocztowa ma odpowiednie konto użytkownika. Zwróć uwagę, że podczas tworzenia udostępnionej skrzynki pocztowej nie poproszono Cię o podanie hasła? Konto ma hasło, ale jest generowane przez system (nieznane). Nie należy używać konta do logowania się do udostępnionej skrzynki pocztowej.

Ale co zrobić, jeśli administrator po prostu zresetował hasło udostępnionego konta użytkownika skrzynki pocztowej? A co, jeśli osoba atakująca uzyska dostęp do udostępnionych poświadczeń konta skrzynki pocztowej? Pozwoliłoby to kontu użytkownika zalogować się do udostępnionej skrzynki pocztowej i wysłać wiadomość e-mail. Aby temu zapobiec, musisz zablokować logowanie do konta skojarzonego z udostępnioną skrzynką pocztową.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.
::: moniker-end

2. Na liście kont użytkowników znajdź konto udostępnionej skrzynki pocztowej (na przykład zmień filtr na **Nielicencjonowani użytkownicy**).

3. Wybierz użytkownika, aby otworzyć okienko właściwości, a następnie wybierz ikonę ![**Blokuj tego użytkownika** Zrzut ekranu przedstawiający ikonę Blokuj tego użytkownika.](../../media/block-user-icon.png)

   > [!NOTE]
   > Jeśli konto jest już zablokowane, **zablokowane logowanie zostanie wyświetlone** u góry, a ikona będzie odczytywać polecenie **Odblokuj tego użytkownika**.

4. W okienku **Blokuj tego użytkownika?** wybierz pozycję **Blokuj logowanie użytkownika**, a następnie wybierz pozycję **Zapisz zmiany**.

Aby uzyskać instrukcje dotyczące blokowania logowania dla kont przy użyciu Azure AD programu PowerShell (w tym wielu kont w tym samym czasie), zobacz [Blokowanie kont użytkowników za pomocą programu Office 365 programu PowerShell](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Dodawanie udostępnionej skrzynki pocztowej do programu Outlook

Jeśli w twojej firmie włączono automatyczne aplikacje (domyślnie większość osób to robi), udostępniona skrzynka pocztowa zostanie automatycznie wyświetlona w aplikacji Outlook użytkownika po zamknięciu i ponownym uruchomieniu Outlook. 

Automatyczne mapowanie ustawia się dla skrzynki pocztowej użytkownika, nie dla udostępnionej skrzynki pocztowej. Oznacza to, że jeśli spróbujesz zarządzać tym, kto ma dostęp do udostępnionej skrzynki pocztowej, za pomocą grupy zabezpieczeń, automatyczne mapowanie nie będzie działać. Jeśli chcesz używać automatycznego mapowania, musisz jawnie przypisać uprawnienia. Automatyczne aplikacje są domyślnie włączone. Aby dowiedzieć się, jak go wyłączyć, zobacz [Remove automapping for a shared mailbox (Usuwanie automappingu dla udostępnionej skrzynki pocztowej](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox)).

Aby dowiedzieć się więcej o udostępnionych skrzynkach pocztowych w Outlook, zobacz:

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Otwieranie i używanie udostępnionej skrzynki pocztowej w programie Outlook</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Dodawanie udostępnionej skrzynki pocztowej do aplikacji Outlook w sieci Web</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Dodawanie udostępnionej skrzynki pocztowej do Outlook mobile</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Otwieranie folderu udostępnionego lub skrzynki pocztowej w programie Outlook dla komputerów Mac</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Dodawanie reguł do udostępnionej skrzynki pocztowej</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Używanie udostępnionej skrzynki pocztowej na urządzeniu przenośnym (telefonie lub tablecie)

Dostęp do udostępnionej skrzynki pocztowej na urządzeniu przenośnym można uzyskać na dwa sposoby:
- Dodaj udostępnioną skrzynkę pocztową w <a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">Outlook dla aplikacji iOS</a> lub <a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">Outlook dla aplikacji mobilnej Android</a>. 
    
    Aby uzyskać instrukcje, zobacz <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Dodawanie udostępnionej skrzynki pocztowej do Outlook urządzenia przenośnego</a>.

- Otwórz przeglądarkę, zaloguj się, a następnie przejdź do Outlook w sieci Web. Z aplikacji Outlook w sieci Web można uzyskać dostęp do udostępnionej skrzynki pocztowej.

    Aby uzyskać instrukcje, zobacz <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Dodawanie udostępnionej skrzynki pocztowej do Outlook w sieci Web</a>.
    
> [!NOTE]
> Udostępnioną skrzynkę pocztową można dodać tylko do Outlook dla aplikacji iOS lub Outlook dla aplikacji mobilnej Android

## <a name="use-the-shared-calendar"></a>Korzystanie z kalendarza udostępnionego

Po utworzeniu udostępnionej skrzynki pocztowej automatycznie utworzono kalendarz udostępniony. Wolimy kalendarz udostępnionej skrzynki pocztowej od kalendarza programu SharePoint do śledzenia terminów i tego, gdzie przebywają poszczególne osoby. Kalendarz udostępniony jest zintegrowany z Outlook i jest znacznie łatwiejszy w użyciu niż kalendarz SharePoint.

1. W aplikacji Outlook przejdź do widoku kalendarza i wybierz udostępnioną skrzynkę pocztową.

2. Po wprowadzeniu terminów wszystkie osoby będące członkami udostępnionej skrzynki pocztowej będą je widzieć.

3. Każdy członek udostępnionej skrzynki pocztowej może tworzyć i wyświetlać terminy w kalendarzu oraz zarządzać nimi, tak jak w przypadku spotkań osobistych. Każdy, kto jest członkiem udostępnionej skrzynki pocztowej, może zobaczyć zmiany w kalendarzu udostępnionym.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
