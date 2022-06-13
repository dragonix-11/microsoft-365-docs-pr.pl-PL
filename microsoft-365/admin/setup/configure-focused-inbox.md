---
title: Konfigurowanie priorytetowej skrzynki odbiorczej dla wszystkich osób w organizacji
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 613a845c-4b71-41de-b331-acdcf5b6625d
description: Jeśli jesteś odpowiedzialny za konfigurowanie ustawień poczty e-mail dla wszystkich osób w firmie, w tym artykule wyjaśniono, jak skonfigurować ukierunkowaną skrzynkę odbiorczą dla użytkowników.
ms.openlocfilehash: 9c3b17c632c2316f3c36a4f79362895d790b1c7b
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010217"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>Konfigurowanie priorytetowej skrzynki odbiorczej dla wszystkich osób w organizacji

Jeśli zakres Twojej odpowiedzialności obejmuje konfigurowanie sposobu działania poczty e-mail dla WSZYSTKICH UŻYTKOWNIKÓW w firmie, ten artykuł jest przeznaczony dla Ciebie. Wyjaśniono w nim, jak go dostosować lub wyłączyć dla swojej firmy, oraz odpowiedzi na [często zadawane pytania](#faq-for-focused-inbox).

Jeśli chcesz wyłączyć priorytetową skrzynkę odbiorczą tylko dla siebie, zobacz [Wyłączanie priorytetowej skrzynki odbiorczej](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2).  

Jeśli chcesz zagwarantować, że użytkownicy otrzymują firmowe wiadomości e-mail, na przykład z działu kadr lub płac, możesz skonfigurować priorytetową skrzynkę odbiorczą, aby te wiadomości pojawiały się w widoku Priorytetowe. Możesz także kontrolować, czy dla użytkowników w Twojej organizacji w skrzynce pocztowej jest widoczna priorytetowa skrzynka odbiorcza.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>Włączanie lub wyłączanie priorytetowej skrzynki odbiorczej w organizacji

Za pomocą programu PowerShell możesz włączyć lub wyłączyć priorytetową skrzynkę odbiorczą dla wszystkich użytkowników w Twojej organizacji. Czy chcesz to zrobić w Centrum administracyjne platformy Microsoft 365? Powiadom o tym nasz zespół inżynierów. **[Zagłosuj tutaj!](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**Aby wyłączyć priorytetową skrzynkę odbiorczą:**
  
W poniższym przykładzie polecenie programu PowerShell **wyłącza** priorytetową skrzynkę odbiorczą w organizacji. Nie zablokowano jednak w ten sposób dostępności tej funkcji dla użytkowników. W razie potrzeby użytkownicy mogą mimo to ponownie włączyć priorytetową skrzynkę odbiorczą na każdym ze swoich klientów. 
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis „Reguły transportu" w artykule [Uprawnienia dotyczące zasad obsługi wiadomości i zgodności](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Uruchom polecenie cmdlet **Get-OrganizationConfig**. 

    ```powershell
    Get-OrganizationConfig
    ```

4. Poszukaj parametru **FocusedInboxOn**, aby wyświetlić jego bieżące ustawienie: 

    ![Response from PowerShell on state of Focused Inbox.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Uruchom następujące polecenie cmdlet, aby wyłączyć priorytetową skrzynkę odbiorczą.

    ```powershell
    Set-OrganizationConfig -FocusedInboxOn $false
    ```

6. Uruchom ponownie polecenie cmdlet **Get-OrganizationConfig**, a zobaczysz, że parametr FocusedInboxOn jest ustawiony na wartość $false, co oznacza, że jest on wyłączony. 

**Aby włączyć priorytetową skrzynkę odbiorczą:**
  
- W kroku 5 powyżej uruchom następujące polecenie cmdlet, aby włączyć priorytetową skrzynkę odbiorczą.

  ```powershell
  Set-OrganizationConfig -FocusedInboxOn $true
  ```
    
## <a name="what-do-users-see-after-i-turn-on-focused-inbox"></a>Co będą widzieć użytkownicy po włączeniu priorytetowej skrzynki odbiorczej?

Widok Priorytetowe pojawi się u użytkowników dopiero po zamknięciu i ponownym uruchomieniu przez nich programu Outlook. Po ponownym uruchomieniu programu Outlook zobaczą oni poradę w interfejsie użytkownika programu Outlook, która zawiera opcję włączenia nowej priorytetowej skrzynki odbiorczej.
  
![An image of what Focused Inbox looks like when a user first opens Outlook on the web.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
Jeśli włączysz priorytetową skrzynkę odbiorczą zamiast funkcji oznaczania jako mało istotne, mogą oni włączyć tę funkcję („Wypróbuj") lub odrzucić ją. Jeśli dany użytkownik ma wielu (obsługiwanych) klientów, może włączyć/wyłączyć priorytetową skrzynkę odbiorczą osobno dla każdego z nich. Porada wygląda następująco:
  
![An image of what Focused Inbox looks like when it's rolled out to your users and Outlook is re-opened.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
Jeśli użytkownik postanowi zacząć korzystać z priorytetowej skrzynki odbiorczej, funkcja oznaczania jako mało istotne zostanie automatycznie wyłączona. Folder Mało istotne zostanie przekonwertowany na standardowy folder, dzięki czemu użytkownik będzie mógł zmienić jego nazwę lub usunąć go.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>Włączanie lub wyłączanie priorytetowej skrzynki odbiorczej dla określonych użytkowników

W tym przykładzie **wyłączono** priorytetową skrzynkę odbiorczą dla Dominika Michalskiego w organizacji Contoso. Nie zablokowano jednak w ten sposób dostępności tej funkcji dla niego. Jeśli chce, nadal może ponownie włączyć skoncentrowaną skrzynkę odbiorczą na każdym ze swoich klientów. 
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis „Reguły transportu" w temacie Uprawnienia dotyczące zasad obsługi wiadomości i zgodności.

3. Uruchom polecenie cmdlet **Get-FocusedInbox** , na przykład: 

    ```powershell
    Get-FocusedInbox -Identity <tim@contoso.com>
    ```

4. Poszukaj parametru FocusedInboxOn, aby wyświetlić jego bieżące ustawienie:

    ![Response from PowerShell on state of Focused Inbox.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Uruchom następujące polecenie cmdlet, aby wyłączyć skoncentrowaną skrzynkę odbiorczą:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $false
    ```

    LUB uruchom następujące polecenie cmdlet, aby ją włączyć:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $true
    ```

## <a name="use-the-ui-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Użyj interfejsu użytkownika, aby utworzyć regułę transportu kierującą wiadomości e-mail do widoku Priorytetowe u wszystkich użytkowników.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centrum administracyjnego programu Exchange</a>.

2. Przejdź do **pozycji Reguły** **przepływu** \> poczty. Wybierz pozycję ![EAC Dodaj ikonę.](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif) a następnie wybierz **pozycję Utwórz nową regułę...**. 

3. Po zakończeniu tworzenia nowej reguły wybierz pozycję **Zapisz** , aby uruchomić regułę.

    Na poniższej ilustracji przedstawiono przykład, w którym wszystkie komunikaty z "działu płac" mają być dostarczane do skrzynki odbiorczej skoncentrowanej.

    ![listy płac focusedinbox.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > Tekst wartości nagłówka wiadomości w tym przykładzie to **X-MS-Exchange-Organization-BypassFocusedInbox**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Użyj programu PowerShell, aby utworzyć regułę transportu kierującą wiadomości e-mail do widoku Priorytetowe u wszystkich użytkowników.

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis „Reguły transportu" w artykule [Uprawnienia dotyczące zasad obsługi wiadomości i zgodności](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Uruchom następujące polecenie, aby zezwolić na dostarczanie wszystkich komunikatów z "Działu płac", na przykład do ukierunkowanej skrzynki odbiorczej.

    ```powershell
    New-TransportRule -Name <name_of_the_rule> -From "Payroll Department" -SetHeaderName "X-MS-Exchange-Organization-BypassFocusedInbox" -SetHeaderValue "true"
    ```

> [!IMPORTANT]
> W tym przykładzie zarówno "X-MS-Exchange-Organization-BypassFocusedInbox", jak i "true" uwzględniają wielkość liter.
> Ponadto skoncentrowana skrzynka odbiorcza będzie uwzględniać nagłówek X, który pomija element Clutter, więc jeśli użyjesz tego ustawienia w obszarze Bałagan, będzie ono używane w skoncentrowanej skrzynce odbiorczej. Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Polecenie New-TransportRule](/powershell/module/exchange/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Możesz sprawdzić nagłówki wiadomości e-mail, aby ustalić, czy wiadomości e-mail trafiają do skrzynki odbiorczej dzięki pomijaniu reguły transportu priorytetowej skrzynki odbiorczej. Wybierz wiadomość e-mail ze skrzynki pocztowej w Twojej organizacji, w której jest stosowana reguła transportu priorytetowej skrzynki odbiorczej. Spójrz na nagłówki dołączone do wiadomości: powinien być widoczny nagłówek **X-MS-Exchange-Organization-BypassFocusedInbox: true**. Oznacza to, że pomijanie działa. Zapoznaj się z [artykułem Wyświetlanie informacji nagłówka internetu dla wiadomości e-mail](https://go.microsoft.com/fwlink/p/?LinkId=822530) , aby uzyskać informacje na temat znajdowania informacji nagłówka.

### <a name="what-will-the-user-see"></a>Co zobaczy użytkownik?

Jeśli reguła transportu jest w miejscu, zostanie wyświetlone powiadomienie dla przesłonięcia. Outlook w sieci Web spowoduje wyłączenie opcji "Always move to Other" i wyświetlenie etykietki narzędzia. Outlook klienci na pulpicie będą zezwalać na wybór opcji "Zawsze przenieś do innych" i wyskakują okno dialogowe.

## <a name="turn-onoff-clutter"></a>Włączanie/wyłączanie funkcji oznaczania jako mało istotne

Otrzymaliśmy zgłoszenia, że funkcja oznaczania jako mało istotne nagle przestała działać u niektórych użytkowników. W takim przypadku możesz ją ponownie włączyć dla konkretnych użytkowników. Zobacz [Konfigurowanie oznaczania jako mało istotne w organizacji](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>Często zadawane pytania dotyczące priorytetowej skrzynki odbiorczej

Poniżej przedstawiono odpowiedzi na często zadawane pytania dotyczące ukierunkowanej skrzynki odbiorczej.

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>Czy można kontrolować sposób wdrażania priorytetowej skrzynki odbiorczej w organizacji?

Tak. Można włączyć lub wyłączyć priorytetową skrzynkę odbiorczą dla całej organizacji lub dla określonych użytkowników. Zobacz wyżej.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>Czy funkcja priorytetowej skrzynki odbiorczej jest dostępna TYLKO dla klientów pakietu Office 2016?

Tak, tylko użytkownicy korzystający z pakietu Office 2016 mogą używać tej funkcji. Ta funkcja nie zostanie wdrożona w programie Outlook 2013 ani w jego wcześniejszych wersjach.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>Ile czasu potrzeba, aby wprowadzone zmiany dotyczące priorytetowej skrzynki odbiorczej zostały wprowadzone w programie Outlook?

Gdy włączysz lub wyłączysz priorytetową skrzynkę odbiorczą, ustawienia zaczną obowiązywać po zamknięciu i ponownym uruchomieniu programu Outlook przez Twoich użytkowników.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>Co się stanie z folderem Mało istotne po włączeniu priorytetowej skrzynki odbiorczej?

Po przełączeniu nie będziesz już otrzymywać mniej istotnych wiadomości e-mail w folderze Mało istotne. Zamiast tego poczta e-mail zostanie rozdzielona między karty Priorytetowe i Inne w skrzynce odbiorczej. Ten sam algorytm, który służył do przenoszenia wiadomości do folderu Mało istotne, jest teraz używany w priorytetowej skrzynce odbiorczej  oznacza to, że wszelkie wiadomości e-mail, które miały być przenoszone do folderu Mało istotne, będą teraz przenoszone do folderu Inne. Wszystkie wiadomości znajdujące się obecnie w folderze Mało istotne pozostaną w nim do czasu, aż zdecydujesz się je usunąć lub przenieść.
  
Zapoznaj się z tym wpisem autorstwa [Tony'ego Redmonda](https://www.petri.com/author/tony-redmond), specjalisty Microsoft MVP: [W jak sposób priorytetowa skrzynka odbiorcza zastępuje folder Mało istotne w usłudze Office 365](https://www.petri.com/focused-inbox-office-365).
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>Czy można zachować folder Mało istotne dla użytkowników? Jakie są zalecenia firmy Microsoft odnośnie do wyboru między folderem Mało istotne a priorytetową skrzynką odbiorczą?

Tak. Można zachować folder Mało istotne dla użytkowników i wyłączyć priorytetową skrzynkę odbiorczą. Ostatecznie folder Mało istotne zostanie jednak w pełni zastąpiony funkcją priorytetowej skrzynki odbiorczej, dlatego firma Microsoft zaleca przejście na priorytetową skrzynkę odbiorczą już teraz. Aby dowiedzieć się więcej o używaniu folderu Mało istotne w usłudze Exchange Online, zobacz następujący wpis w blogu: [Aktualizacja na temat priorytetowej skrzynki odbiorczej i nasze plany dla folderu Mało istotne](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>Czy należy wyłączyć folder Mało istotne dla użytkowników końcowych w przypadku planowanego przełączenia wszystkich użytkowników na korzystanie z priorytetowej skrzynki odbiorczej?

Nie. Można jawnie wyłączyć folder Mało istotne dla skrzynki pocztowej, uruchamiając polecenie cmdlet Set-Clutter. W przypadku wykonania tej czynności właściciel skrzynki pocztowej będzie jednak widział, że wiadomości, które wcześniej były przekierowywane do folderu Mało istotne, pozostają w skrzynce odbiorczej, i będzie musiał przetwarzać te wiadomości, dopóki jego klient nie zostanie uaktualniony do wersji obsługującej priorytetową skrzynkę odbiorczą. Dlatego najlepiej nie wyłączać folderu Mało istotne, dopóki nie zostaną udostępnieni uaktualnieni klienci.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>Dlaczego są dostępne dwa różne polecenia cmdlet do zarządzania priorytetową skrzynką odbiorczą?

Z priorytetową skrzynką odbiorczą są skojarzone dwa stany.
  
- **Poziom organizacji**: Stan priorytetowej skrzynki odbiorczej i skojarzona z nim sygnatura czasowa ostatniej aktualizacji.

- **Poziom skrzynki pocztowej**: Stan priorytetowej skrzynki odbiorczej i skojarzona z nim sygnatura czasowa ostatniej aktualizacji. 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>Jak program Outlook decyduje na podstawie tych dwóch stanów, czy wyświetlać folder priorytetowej skrzynki odbiorczej?

Program Outlook decyduje, czy wyświetlać ten folder, na podstawie stanu zwróconego przez polecenie cmdlet z najnowszą sygnaturą czasową. Domyślnie obie sygnatury czasowe mają wartość „null" i w takim przypadku opisywana funkcja jest włączona.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>Dlaczego polecenie cmdlet Get-FocusedInbox zwraca wartość „true" po wyłączeniu priorytetowej skrzynki odbiorczej w mojej organizacji?

Istnieją dwa polecenia cmdlet umożliwiające kontrolowanie priorytetowej skrzynki odbiorczej. Po uruchomieniu polecenia Get-FocusedInbox dla skrzynki pocztowej zwraca ono stan funkcji na poziomie skrzynki pocztowej. Środowisko w programie Outlook jest wybierane na podstawie tego, który stan zwrócony przez polecenie cmdlet został zmodyfikowany jako ostatni.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>Czy można uruchomić skrypt, aby zobaczyć, kto ma włączoną priorytetową skrzynkę odbiorczą?

Nie i jest to zamierzone. Włączenie skoncentrowanej skrzynki odbiorczej jest ustawieniem po stronie klienta, dlatego polecenie cmdlet może tylko poinformować, czy skrzynka pocztowa użytkownika kwalifikuje się do obsługi klienta. Ta funkcja może być włączona w niektórych klientach i jednocześnie wyłączona w innych, na przykład włączona w aplikacji Outlook i aplikacji mobilnej Outlook oraz wyłączona w aplikacji Outlook w sieci Web.

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie bałaganu dla organizacji](../email/configure-clutter.md) (artykuł)\
[Konfigurowanie ustawień udostępnionej skrzynki pocztowej](../email/configure-a-shared-mailbox.md) (artykuł)\
[Tworzenie podpisów i zrzeczenia się odpowiedzialności](create-signatures-and-disclaimers.md) (wideo)
