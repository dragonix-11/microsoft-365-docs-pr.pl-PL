---
title: Konfigurowanie Microsoft 365 Business Standard przy użyciu nowej lub istniejącej domeny
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
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- BEA160
description: Podczas zakupu Microsoft 365 Business Standard masz możliwość korzystania z posiadanej domeny lub zakupu jej podczas rejestracji.
ms.openlocfilehash: d5504edaff4c9d406d218d8ab8333b6d50af406e
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573896"
---
# <a name="set-up-microsoft-365-business-standard-with-a-new-or-existing-domain"></a>Konfigurowanie Microsoft 365 Business Standard przy użyciu nowej lub istniejącej domeny

Podczas zakupu Microsoft 365 Business Standard możesz dodać posiadaną domenę lub kupić domenę. Zapoznaj się z [pozycją Zarejestruj się, aby uzyskać subskrypcję Microsoft 365 Business Standard](../simplified-signup/signup-business-standard.md).

W tym artykule przeprowadzimy Cię przez kroki dodawania istniejącej domeny, którą już posiadasz, lub zakupu nowej domeny. Jeśli nowa domena została zakupiona podczas tworzenia konta, twoja domena jest skonfigurowana i możesz przejść do [pozycji Dodaj użytkowników i przypisać licencje](#add-users-and-assign-licenses).

> [!Tip]
> Jeśli masz subskrypcję Microsoft 365 Business Premium, zobacz [Konfigurowanie Microsoft 365 Business Premium](../../business-premium/m365bp-setup.md).

## <a name="set-up-microsoft-365-for-business"></a>Konfigurowanie platformy Microsoft 365 dla firm

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ]

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dodawać, modyfikować lub usuwać domeny, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratora](../add-users/about-admin-roles.md).

> [!IMPORTANT]
> Osoba, która rejestruje się w usłudze Microsoft 365 dla firm (zazwyczaj właściciel firmy) automatycznie staje się administratorem technicznym organizacji. Możesz dodać inne osoby jako administratorów, jeśli chcesz uzyskać pomoc w zarządzaniu usługami platformy Microsoft 365. Aby uzyskać więcej informacji, zobacz [Przypisywanie ról administratora](../add-users/assign-admin-roles.md) .

## <a name="watch-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Obejrzyj: Dodawanie istniejącej domeny do subskrypcji Microsoft 365 Business Standard

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu]

## <a name="steps-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Kroki: Dodawanie istniejącej domeny do subskrypcji Microsoft 365 Business Standard

1. Na stronie **Jak się zalogujesz** na Microsoft 365 Business Standard rejestracji wybierz **pozycję Utwórz nowe biznesowe konto e-mail (zaawansowane).**

2. Na stronie **Instalowanie aplikacji pakietu Office** możesz opcjonalnie zainstalować aplikacje na własnym komputerze.

3. W kroku **Dodawanie domeny** wprowadź nazwę domeny, która ma być używana (na przykład contoso.com).

    > [!IMPORTANT]
    > Jeśli domena została zakupiona podczas tworzenia konta, nie zobaczysz tutaj kroku **Dodawanie domeny** . Zamiast tego przejdź do [pozycji Dodaj użytkowników](#add-users-and-assign-licenses) .

4. Wykonaj kroki tworzenia [rekordów DNS u dowolnego dostawcy hostingu DNS dla Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), który weryfikuje, czy jesteś właścicielem domeny. Jeśli znasz hosta domeny, zobacz również [Dodawanie domeny do platformy Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Jeśli dostawca hostingu to GoDaddy lub inny host z włączoną obsługą [połączenia z domeną](/office365/admin/get-help-with-domains/domain-connect), proces jest łatwy i zostanie automatycznie poproszony o zalogowanie się i umożliwienie firmie Microsoft uwierzytelniania w Twoim imieniu.

    ![Na stronie GoDaddy Confirm Access (Potwierdź dostęp) wybierz pozycję Autoryzuj.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Dodawanie użytkowników i przypisywanie licencji

Możesz teraz dodawać użytkowników, ale możesz również [dodać użytkowników w dalszej](../add-users/add-users.md) części centrum administracyjnego.

Wszyscy dodaeni użytkownicy otrzymują automatycznie przypisaną licencję Microsoft 365 Business Standard.

1. Jeśli twoja subskrypcja Microsoft 365 Business Standard ma istniejących użytkowników, możesz teraz przypisać do nich licencje. Możesz dodać licencje dla tych użytkowników.

2. Po dodaniu użytkowników otrzymasz również opcję udostępniania poświadczeń nowym dodanym użytkownikom. Możesz wydrukować te informacje, wysłać je pocztą e-mail lub pobrać.

## <a name="connect-your-domain"></a>Łączenie domeny
  
Aby skonfigurować usługi, musisz zaktualizować rekordy u hosta DNS lub rejestratora domeny.
  
1. Kreator konfiguracji zwykle wykrywa rejestratora i udostępnia linki do instrukcji krok po kroku dotyczących aktualizowania rekordów serwera nazw w witrynie internetowej rejestratora. Jeśli tak się nie stanie, [zmień serwery nazw, aby skonfigurować Office 365 z dowolnym rejestratorem domeny](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md).

    - Jeśli masz istniejące rekordy DNS, na przykład istniejącą witrynę internetową, ale host DNS jest włączony na potrzeby [nawiązywania połączenia z domeną](/office365/admin/get-help-with-domains/domain-connect), wybierz pozycję **Dodaj rekordy dla mnie**. Na stronie **Wybierz Usługi online** zaakceptuj wszystkie wartości domyślne, a następnie wybierz pozycję **Dalej**, a następnie wybierz pozycję **Autoryzuj** na stronie hosta DNS.
    - Jeśli masz istniejące rekordy DNS z innymi hostami DNS (nie włączono połączenia z domeną), chcesz zarządzać własnymi rekordami DNS, aby upewnić się, że istniejące usługi pozostają połączone. Aby uzyskać więcej informacji [, zobacz podstawy domeny](/office365/admin/get-help-with-domains/dns-basics) .

2. Wykonaj kroki opisane w kreatorze, a adres e-mail i inne usługi zostaną skonfigurowane dla Ciebie.

    Po zakończeniu procesu rejestracji nastąpi przekierowanie do centrum administracyjnego, w którym będziesz postępować zgodnie z instrukcjami kreatora, aby zainstalować aplikacje pakietu Office, dodać domenę, dodać użytkowników i przypisać licencje. Po zakończeniu początkowej konfiguracji możesz użyć strony **Konfiguracja** w centrum administracyjnym, aby kontynuować konfigurowanie i konfigurowanie usług, które pochodzą z subskrypcji.

    Aby uzyskać więcej informacji na temat kreatora konfiguracji i strony **Konfiguracja** centrum administracyjnego, zobacz [Różnica między kreatorem instalacji a stroną Instalatora](o365-setup-wizard-and-setup-page.md).

## <a name="watch-set-up-business-email-with-a-new-domain"></a>Obejrzyj: Konfigurowanie firmowej poczty e-mail przy użyciu nowej domeny

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>Kroki: Konfigurowanie firmowej poczty e-mail przy użyciu nowej domeny

1. Na stronie **Jak się zalogujesz** na Microsoft 365 Business Standard rejestracji wybierz **pozycję Utwórz nowe biznesowe konto e-mail (zaawansowane).**

2. Wykonaj kroki zakupu nowej domeny i wprowadź nazwę domeny, która ma być używana (na przykład contoso.com). Po zakończeniu zakupu domeny możesz [dodać użytkowników i licencje](../add-users/add-users.md) oraz zainstalować aplikacje pakietu Office w centrum administracyjnym.

## <a name="finish-setting-up"></a>Zakończ konfigurowanie

Wykonaj poniższe kroki, aby skonfigurować aplikacje Outlook, Teams, OneDrive i witrynę internetową.

### <a name="step-set-up-outlook-for-email"></a>Krok: Konfigurowanie programu Outlook na potrzeby poczty e-mail

1. W menu Start systemu Windows wyszukaj pozycję Outlook i wybierz ją.

    (Jeśli używasz komputera Mac, otwórz program Outlook na pasku narzędzi lub znajdź go przy użyciu narzędzia Finder).

    Jeśli właśnie zainstalowano program Outlook, na stronie Powitalnej wybierz pozycję **Dalej**.

2. Wybierz pozycję **Informacje o** \> **pliku** \> **Dodaj konto**.

3. Wprowadź swój adres e-mail firmy Microsoft i wybierz pozycję **Połącz**.

## <a name="watch-set-up-outlook-for-email"></a>Obejrzyj: Konfigurowanie programu Outlook na potrzeby poczty e-mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
Więcej informacji można [znaleźć w tematach Konfigurowanie programu Outlook na potrzeby poczty e-mail](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>Importowanie wiadomości e-mail

Jeśli używasz programu Outlook z innym kontem e-mail, możesz zaimportować poprzednią wiadomość e-mail, kalendarz i kontakty do nowego konta Microsoft.
  
1. **Eksportowanie starej wiadomości e-mail**

    In Outlook, choose **File** \> **Open &amp; Export** \> **Import/Export**.

    Wybierz **pozycję Eksportuj do pliku,** a następnie wykonaj kroki, aby wyeksportować plik danych programu Outlook (pst) i wszystkie podfoldery.

2. **Importowanie starej wiadomości e-mail**

    W programie Outlook ponownie wybierz pozycję **Otwórz &amp;** **plik** \> Eksportuj \> **import/eksport**.

    Tym razem wybierz pozycję **Importuj z innego programu lub pliku** i wykonaj kroki importowania pliku kopii zapasowej utworzonego podczas eksportowania starej wiadomości e-mail.

## <a name="watch-import-and-redirect-email"></a>Obejrzyj: Importowanie i przekierowywanie wiadomości e-mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Więcej informacji można [znaleźć w tematach Importowanie poczty e-mail za pomocą programu Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Możesz również zaimportować wiadomości e-mail wszystkich użytkowników za pomocą <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego programu Exchange</a> . Aby uzyskać więcej informacji, zobacz [migrowanie wielu kont e-mail](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>Konfigurowanie usług Microsoft Teams i OneDrive dla firm

Wybierz ikonę chmury usługi OneDrive na pasku zadań i wykonaj kroki, aby przenieść pliki do nowego folderu OneDrive dla Firm. Wybierz pozycję **Dalej** , aby skonfigurować usługę Microsoft Teams.

1. Otwórz aplikację Microsoft Teams, wybierz ikonę profilu, a następnie **dodaj konto służbowe**. Wykonaj kroki, aby dodać nowe konto do aplikacji Teams.

## <a name="use-a-public-website"></a>Korzystanie z publicznej witryny internetowej

Platforma Microsoft 365 nie zawiera publicznej witryny internetowej dla Twojej firmy. Jeśli chcesz go skonfigurować, rozważ użycie partnera firmy Microsoft, takiego jak GoDaddy lub WIX.
  
1. W centrum administracyjnym przejdź do pozycji **Zasoby**, a następnie wybierz pozycję **Publiczna witryna internetowa**.

2. Wybierz pozycję **Dowiedz się więcej** w ramach jednej z opcji, a następnie utwórz konto u partnera witryny internetowej i użyj jego narzędzi do skonfigurowania i zaprojektowania witryny.

## <a name="watch-create-your-business-website"></a>Obejrzyj: Tworzenie witryny internetowej firmy

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>Zapraszanie użytkowników do dołączenia do subskrypcji i organizacji

Po skonfigurowaniu organizacji możesz zaprosić innych użytkowników do dołączenia do subskrypcji biznesowej platformy Microsoft 365. Uzyskają dostęp do wszystkich funkcji subskrypcji.

[Zapraszanie użytkowników do mojej subskrypcji](../simplified-signup/admin-invite-business-standard.md)

Poinformuj użytkowników, że mogą wykonać kroki opisane w poniższych artykułach, aby dołączyć do Twojej organizacji i subskrypcji.

- [Akceptowanie zaproszenia e-mail](../simplified-signup/user-invite-business-standard.md)

- [Akceptowanie zaproszenia e-mail przy użyciu programu Outlook, Yahoo, Gmail lub innego konta (użytkownik)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>Tematy pokrewne

[Migruj dane do mojej subskrypcji Microsoft 365 dla Firm w warstwie Standard](../simplified-signup/migrate-data-business-standard.md)
