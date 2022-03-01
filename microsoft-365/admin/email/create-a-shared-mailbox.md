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
description: Utwórz udostępnioną skrzynkę pocztową, aby umożliwić wielu użytkownikom w firmie udostępnianie odpowiedzialności za czytanie i odpowiadanie na wiadomości e-mail wysyłane na jeden adres.
ms.openlocfilehash: f8a7f725e029021626bf408a3797ac6bfbb16215
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011329"
---
# <a name="create-a-shared-mailbox"></a>Tworzenie udostępnionej skrzynki pocztowej 

> [!NOTE]
> Jeśli Twoja organizacja korzysta z hybrydowego Exchange, do tworzenia udostępnionych skrzynek pocztowych i zarządzania nimi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a> należy używać Exchange administracyjnego lokalnego centrum administracyjnego. Zobacz [Tworzenie udostępnionych skrzynek pocztowych w centrum Exchange administracyjnego.](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Jeśli nie masz pewności, czy utworzyć udostępnioną skrzynkę pocztową, czy grupę Microsoft 365 dla usługi Outlook, zobacz Porównanie grup, aby uzyskać [](../create-groups/compare-groups.md) wskazówki. Pamiętaj, że obecnie nie jest możliwe migrowanie udostępnionej skrzynki pocztowej do Microsoft 365 grupy. Jeśli chcesz coś o tym wiedzieć, po prostu [przegłosuj tutaj](https://go.microsoft.com/fwlink/?linkid=871518).

Tworzenie udostępnionych skrzynek pocztowych jest łatwe. Dzięki nim grupa osób może monitorować wiadomości e-mail i wysyłać je ze wspólnego adresu e-mail, takiego jak info@contoso.com. Gdy osoba z grupy odpowie na wiadomość wysłaną do udostępnionej skrzynki pocztowej, utworzona przez nią wiadomość jest wysyłana z udostępnionej skrzynki pocztowej, a nie z indywidualnej skrzynki tej osoby.

Udostępnione skrzynki pocztowe zawierają kalendarz udostępniony. Wiele małych firm lubi używać kalendarza udostępnionego jako miejsca, w którym wszyscy mogą wprowadzać swoje terminy. Jeśli na przykład masz trzech pracowników, którzy spotykają się z klientami, mogą oni wprowadzać swoje terminy w kalendarzu udostępnionym. W ten prosty sposób wszyscy zostają poinformowani, gdzie kto jest.

Przed utworzeniem udostępnionej skrzynki pocztowej przeczytaj Informacje o udostępnionych skrzynkach [pocztowych](about-shared-mailboxes.md) , aby uzyskać więcej informacji.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="create-a-shared-mailbox-and-add-members"></a>Tworzenie udostępnionej skrzynki pocztowej i dodawanie członków
  
1. Zaloguj się przy użyciu konta administratora globalnego lub Exchange konta administratora. Jeśli zostanie wyświetlony komunikat "Nie masz uprawnień dostępu do tej strony lub wykonywania tej czynności", oznacza **to**, że nie jesteś administratorem. 

::: moniker range="o365-worldwide"

2. W centrum administracyjnym przejdź do strony skrzynki **Teams & udostępnione** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">skrzynki pocztowe grup</a>.

::: moniker-end

::: moniker range="o365-21vianet"

2. W centrum [administracyjnym](https://go.microsoft.com/fwlink/p/?linkid=850627) przejdź do strony Teams & **grupy Udostępnione** \> **skrzynki pocztowe**.

::: moniker-end
    
3. Na stronie **Udostępnione skrzynki pocztowe** wybierz pozycję **+ Dodaj udostępnioną skrzynkę pocztową**. Wprowadź nazwę udostępnionej skrzynki pocztowej. Wybiera adres e-mail, ale w razie potrzeby możesz go edytować.
    
    ![Name your shared mailbox.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Wybierz **pozycję Zapisz zmiany**. Może upłynąć kilka minut, zanim będzie możliwe dodanie członków.

5. W **obszarze Następne kroki** wybierz **pozycję Dodaj członków do tej skrzynki pocztowej**. Członkowie to osoby, które będą mogły wyświetlać pocztę przychodzącą do tej udostępnionej skrzynki pocztowej oraz wychodzące odpowiedzi.

   ![Wybierz pozycję Dodaj członków.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. Wybierz przycisk **+Dodaj** członków. Umieść znacznik wyboru obok osób, które mają korzystać z tej udostępnionej skrzynki pocztowej, a następnie wybierz pozycję **Zapisz**.

   ![Przypisz członków do udostępnionej skrzynki pocztowej.](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. Wybierz pozycję **Zamknij**.

Masz udostępnioną skrzynkę pocztową i zawiera ona kalendarz udostępniony. Przejdź do następnego kroku: [Blokowanie logowania dla konta udostępnionej skrzynki pocztowej](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Jakich uprawnień należy użyć?

Z udostępnioną skrzynką pocztową można używać następujących uprawnień:

- **Pełny dostęp**: Uprawnienia Pełny dostęp umożliwiają użytkownikowi otwieranie udostępnionej skrzynki pocztowej i działanie jako właściciel tej skrzynki pocztowej. Po uzyskiwaniu dostępu do udostępnionej skrzynki pocztowej użytkownik może tworzyć elementy kalendarza, czytać, wyświetlać, usuwać i zmieniać wiadomości e-mail oraz tworzyć zadania i kontakty kalendarza. Użytkownik z uprawnieniami Pełny dostęp nie może jednak wysyłać wiadomości e-mail z udostępnionej skrzynki pocztowej, chyba że ma również uprawnienia Wyślij jako lub Wyślij w imieniu.

- **Wyślij jako**: Uprawnienie Wyślij jako umożliwia użytkownikowi personifikowanie udostępnionej skrzynki pocztowej podczas wysyłania poczty. Jeśli na przykład Kateina zaloguje się do udostępnionej skrzynki pocztowej Dział marketingu i wyśle wiadomość e-mail, będzie ona wyglądać tak, jakby została wysłana przez dział marketingu.

- **Wyślij w imieniu**: Uprawnienie Wyślij w imieniu umożliwia użytkownikowi wysyłanie wiadomości e-mail w imieniu udostępnionej skrzynki pocztowej. Jeśli na przykład Jan zaloguje się do udostępnionej skrzynki pocztowej Recepcja budynku 32 i wyśle wiadomość e-mail, będzie ona wyglądać tak, jakby została wysłana przez użytkownika "Jan w imieniu recepcjonistki budynku 32". Za pomocą programu EAC nie można udzielać uprawnień Wyślij w imieniu. Należy użyć polecenia cmdlet **Set-Mailbox** z parametrem _GrantSendonBehalf_ .

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Edytowanie delegowania udostępnionej skrzynki pocztowej za pomocą Centrum administracyjnego programu Exchange

1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a> przejdź do **pozycji Adresaci udostępniani**\>. Wybierz udostępnioną skrzynkę pocztową, a następnie wybierz **pozycję Edytuj** ![ikonę Edytuj](../../media/ITPro-EAC-EditIcon.png).

2. Wybierz pozycję **Delegowanie skrzynki pocztowej**.

3. Aby przyznać lub usunąć uprawnienia Pełny dostęp i Wyślij jako, wybierz pozycję **Dodaj ikonę** ![Dodaj.](../../media/ITPro-EAC-AddIcon.png) lub **usuń** ![ikonę Usuń](../../media/ITPro-EAC-RemoveIcon.gif) , a następnie wybierz użytkowników, którym chcesz przyznać uprawnienia.

   > [!NOTE]
   > Uprawnienia Pełny dostęp umożliwiają użytkownikowi otwieranie skrzynki pocztowej, a także tworzenie i modyfikowanie zawartych w niej elementów. Uprawnienia Wyślij jako umożliwiają każdej osobie innej niż właściciel skrzynki pocztowej wysyłanie wiadomość e-mail z tej udostępnionej skrzynki pocztowej. Oba uprawnienia są wymagane do obsługi udostępnionej skrzynki pocztowej.

4. Wybierz **pozycję Zapisz** , aby zapisać zmiany.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Blokowanie logowania do konta udostępnionej skrzynki pocztowej

Każda udostępniona skrzynka pocztowa ma odpowiednie konto użytkownika. Zwróć uwagę, że podczas tworzenia udostępnionej skrzynki pocztowej nie poproszono Cię o podanie hasła? Konto ma hasło, ale jest generowane przez system (nieznany). Nie musisz logować się do udostępnionej skrzynki pocztowej przy użyciu tego konta.

Co jednak zrobić, jeśli administrator po prostu zresetuje hasło do konta użytkownika udostępnionej skrzynki pocztowej? A co w przypadku uzyskania przez atakującego dostępu do poświadczeń konta udostępnionej skrzynki pocztowej? Dzięki temu konto użytkownika może logować się do udostępnionej skrzynki pocztowej i wysyłać wiadomości e-mail. Aby temu zapobiec, musisz zablokować logowanie dla konta skojarzonego z udostępnioną skrzynką pocztową.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.
::: moniker-end

2. Na liście kont użytkowników znajdź konto dla udostępnionej skrzynki pocztowej (na przykład zmień filtr na **Nielicencjonowani użytkownicy**).

3. Wybierz użytkownika, aby otworzyć jego okienko właściwości, a  ![następnie wybierz ikonę Zablokuj tego użytkownika Zrzut ekranu: ikona Zablokuj tego użytkownika.](../../media/block-user-icon.png)

   > [!NOTE]
   > Jeśli konto jest już **zablokowane, u** góry zostanie wyświetlone menu Logowanie zablokowane, a na ikonie będzie wyświetlany odczyt **Odblokuj tego użytkownika**.

4. W **okienku Zablokować tego użytkownika?** **wybierz pozycję** Zablokuj logowanie się użytkownika, a następnie wybierz pozycję **Zapisz zmiany**.

Aby uzyskać instrukcje dotyczące blokowania logowania dla kont przy użyciu programu PowerShell usługi Azure AD (w tym wielu kont jednocześnie), zobacz Blokowanie kont użytkowników za [pomocą programu Office 365 PowerShell](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Dodawanie udostępnionej skrzynki pocztowej do programu Outlook

Jeśli w firmie włączono automatyczne mapowanie (domyślnie większość osób korzysta z tej funkcji), udostępniona skrzynka pocztowa pojawi się automatycznie w aplikacji usługi Outlook użytkownika po zamknięciu i ponownym uruchomieniu przez nich Outlook. 

Automatyczne mapowanie ustawia się dla skrzynki pocztowej użytkownika, nie dla udostępnionej skrzynki pocztowej. Oznacza to, że jeśli spróbujesz zarządzać tym, kto ma dostęp do udostępnionej skrzynki pocztowej, za pomocą grupy zabezpieczeń, automatyczne mapowanie nie będzie działać. Jeśli chcesz używać automatycznego mapowania, musisz jawnie przypisać uprawnienia. Automatyczne mapowanie jest domyślnie włączone. Aby dowiedzieć się, jak je wyłączyć, zobacz [Usuwanie automatycznego mapowania dla udostępnionej skrzynki pocztowej](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox).

Aby dowiedzieć się więcej o udostępnionych skrzynkach pocztowych w Outlook, zobacz:

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Otwieranie i używanie udostępnionej skrzynki pocztowej w programie Outlook</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Dodawanie udostępnionej skrzynki pocztowej do aplikacji Outlook w sieci Web</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Dodawanie udostępnionej skrzynki pocztowej do Outlook urządzenia przenośnego</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Otwieranie folderu udostępnionego lub skrzynki pocztowej w programie Outlook dla komputerów Mac</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Dodawanie reguł do udostępnionej skrzynki pocztowej</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Używanie udostępnionej skrzynki pocztowej na urządzeniu przenośnym (telefonie lub tablecie)

Udostępnioną skrzynkę pocztową można uzyskać na urządzeniu przenośnym na dwa sposoby:
- Dodaj udostępnioną skrzynkę pocztową <a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">w aplikacji Outlook dla systemu iOS</a> lub aplikacji mobilnej <a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">Outlook dla systemu Android</a>. 
    
    Aby uzyskać instrukcje, <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">zobacz Dodawanie udostępnionej skrzynki pocztowej do Outlook urządzenia przenośnego</a>.

- Otwórz przeglądarkę, zaloguj się, a następnie przejdź do Outlook w sieci Web. Z aplikacji Outlook w sieci Web można uzyskać dostęp do udostępnionej skrzynki pocztowej.

    Aby uzyskać instrukcje, <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">zobacz Dodawanie udostępnionej skrzynki pocztowej do Outlook w sieci Web</a>.
    
> [!NOTE]
> Udostępnioną skrzynkę pocztową można dodawać tylko do aplikacji Outlook dla systemu iOS lub aplikacji Outlook dla urządzeń przenośnych z systemem Android

## <a name="use-the-shared-calendar"></a>Korzystanie z kalendarza udostępnionego

Podczas tworzenia udostępnionej skrzynki pocztowej automatycznie utworzono kalendarz udostępniony. Wolimy kalendarz udostępnionej skrzynki pocztowej od kalendarza programu SharePoint do śledzenia terminów i tego, gdzie przebywają poszczególne osoby. Kalendarz udostępniony jest zintegrowany Outlook i jest znacznie łatwiejszy w użyciu niż kalendarz SharePoint kalendarzy.

1. W aplikacji Outlook przejdź do widoku kalendarza i wybierz udostępnioną skrzynkę pocztową.

2. Po wprowadzeniu terminów wszystkie osoby będące członkami udostępnionej skrzynki pocztowej będą je widzieć.

3. Każdy członek udostępnionej skrzynki pocztowej może tworzyć i wyświetlać terminy oraz zarządzać nimi w kalendarzu, tak jak w przypadku swoich osobistych terminów. Wszystkie osoby, które są członkami udostępnionej skrzynki pocztowej, mogą zobaczyć wprowadzone przez siebie zmiany w kalendarzu udostępnionym.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
