---
title: Konfigurowanie Microsoft 365 Business Standard nowej lub istniejącej domeny
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
description: Podczas zakupu Microsoft 365 Business Standard masz możliwość używania domeny, która należy do Ciebie, lub kupowania jej podczas rejestracji.
ms.openlocfilehash: 51f88847a1e0ca04e216044172dbacf572fb82e3
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012525"
---
# <a name="set-up-microsoft-365-business-standard-with-a-new-or-existing-domain"></a>Konfigurowanie Microsoft 365 Business Standard nowej lub istniejącej domeny

Podczas zakupu Microsoft 365 Business Standard masz możliwość dodania własnej domeny lub zakupu. Zobacz Logowanie [się w celu Microsoft 365 Business Standard subskrypcji usługi](../simplified-signup/signup-business-standard.md).

W tym artykule o krokach dodawania istniejącej domeny i kupowania nowej domeny już istniejącej. Jeśli podczas rejestracji w domenie kupiono nową domenę, to jest ona w ogóle ustawiona. Możesz przejść do dodawania użytkowników i [przypisywania licencji](#add-users-and-assign-licenses).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dodawać, modyfikować lub usuwać domeny, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz [Role administratora informacje](../add-users/about-admin-roles.md).

> [!IMPORTANT]
> Osoba, która tworzy konto w Microsoft 365 dla firm (zwykle jest to właściciel firmy) automatycznie staje się administratorem technicznym organizacji. Jeśli chcesz uzyskać pomoc przy zarządzaniu usługami firmy Microsoft, możesz dodać inne osoby Microsoft 365 administratorów. Aby uzyskać [więcej informacji, zobacz Przypisywanie ról](../add-users/assign-admin-roles.md) administratora.

## <a name="watch-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Obejrzyj: Dodawanie istniejącej domeny do subskrypcji Microsoft 365 Business Standard domeny

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu]

## <a name="steps-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Kroki: Dodawanie istniejącej domeny do subskrypcji Microsoft 365 Business Standard domeny

1. Na stronie **Jak się logować** na stronie Microsoft 365 Business Standard utwórz konto wybierz pozycję Utwórz nowe biznesowe konto e-mail **(zaawansowane)**.

2. Na **stronie Instalowanie Office aplikacji** możesz opcjonalnie zainstalować te aplikacje na swoim komputerze.

3. W kroku **Dodaj domenę** wprowadź nazwę domeny, której chcesz użyć (na przykład contoso.com).

    > [!IMPORTANT]
    > Jeśli podczas rejestracji zakupiono domenę, nie zobaczysz tutaj kroku **Dodaj** domenę. Zamiast tego [przejdź do przycisku Dodaj użytkowników](#add-users-and-assign-licenses) .

4. Postępuj zgodnie z instrukcjami [w celu utworzenia rekordów DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) dla Office 365 w celu weryfikacji, że jesteś właścicielem domeny. Jeśli znasz hosta domeny, zobacz też [Dodawanie domeny do](/microsoft-365/admin/setup/add-domain) Microsoft 365.

    Jeśli Twój dostawca hostingu to Firma GoDaddy lub inny host z włączonym nawiązywaniem połączenia z domeną [, ten](/office365/admin/get-help-with-domains/domain-connect) proces jest łatwy i zostanie automatycznie poproszony o zalogowanie się i uwierzytelnienie firmy Microsoft w Twoim imieniu.

    ![Na stronie Potwierdzanie dostępu w daddy wybierz pozycję Autoryzuj.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Dodawanie użytkowników i przypisywanie licencji

Użytkowników możesz dodać teraz, ale możesz również dodać użytkowników [później](../add-users/add-users.md) w centrum administracyjnym.

Każdy użytkownik, który dodasz, automatycznie przypisze mu licencję Microsoft 365 Business Standard licencji.

1. Jeśli Twoja Microsoft 365 Business Standard ma już użytkowników, możesz teraz przypisać im licencje. Możesz dodać licencje dla tych użytkowników.

2. Po dodaniu użytkowników zostanie również dodana opcja udostępnienia poświadczeń nowym użytkownikom. Możesz wydrukować te informacje, wysłać je pocztą e-mail lub pobrać.

## <a name="connect-your-domain"></a>Łączenie domeny
  
Aby skonfigurować usługi, musisz zaktualizować rekordy u swojego hosta DNS lub rejestratora domen.
  
1. Kreator konfiguracji zwykle wykrywa rejestratora i udostępnia linki do instrukcji krok po kroku dotyczących aktualizowania rekordów serwera nazw w witrynie internetowej rejestratora. Jeśli tak się nie stanie, zmień serwery nazw, aby Office 365 [u dowolnego rejestratora domen](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md).

    - Jeśli masz istniejące rekordy DNS, na przykład istniejącą witrynę internetową, ale dla Twojego hosta DNS włączono łączenie [domen, wybierz](/office365/admin/get-help-with-domains/domain-connect) pozycję **Dodaj rekordy**. Na stronie **Wybierz usługi online** zaakceptuj wszystkie ustawienia domyślne, wybierz pozycję **Dalej, a** następnie wybierz pozycję **Autoryzuj** na stronie swojego hosta DNS.
    - Jeśli masz istniejące rekordy DNS z innymi hostami DNS (bez włączonego łączenia domen), chcieć zarządzać własnymi rekordami DNS, aby upewnić się, że istniejące usługi pozostają połączone. Aby [uzyskać więcej informacji, zobacz](/office365/admin/get-help-with-domains/dns-basics) Podstawowe informacje o domenie.

2. Postępuj zgodnie z instrukcjami kreatora, aby skonfigurować pocztę e-mail i inne usługi.

    Po zakończeniu procesu tworzenia konta zostaniesz przekierowywowany do centrum administracyjnego, w którym możesz wykonać kroki kreatora w celu zainstalowania aplikacji Office, dodania domeny, dodania użytkowników i przypisania licencji. Po ukończeniu konfiguracji początkowej możesz użyć strony Konfiguracja w centrum  administracyjnym, aby kontynuować konfigurowanie usług oferowanych w ramach subskrypcji.

    Aby uzyskać więcej informacji na temat kreatora konfiguracji i strony **Konfiguracja centrum** administracyjnego, zobacz Różnice między kreatorem [konfiguracji a stroną Konfiguracja](o365-setup-wizard-and-setup-page.md).

## <a name="watch-set-up-business-email-with-a-new-domain"></a>Obejrzyj: konfigurowanie firmowej poczty e-mail z nową domeną

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>Kroki: konfigurowanie firmowej poczty e-mail z nową domeną

1. Na stronie **Jak się logować** na stronie Microsoft 365 Business Standard utwórz konto wybierz pozycję Utwórz nowe biznesowe konto e-mail **(zaawansowane)**.

2. Postępuj zgodnie z instrukcjami, aby kupić nową domenę, a następnie wprowadź nazwę domeny, której chcesz użyć (na przykład contoso.com). Po zakupie domeny możesz dodać użytkowników i licencje oraz zainstalować aplikacje [](../add-users/add-users.md) pakietu Office w centrum administracyjnym.

## <a name="finish-setting-up"></a>Kończanie konfigurowania

Wykonaj poniższe czynności, aby skonfigurować Outlook, Teams, OneDrive i witrynę sieci Web.

### <a name="step-set-up-outlook-for-email"></a>Krok: konfigurowanie usługi Outlook-mail

1. W Windows menu Start wybierz pozycję Outlook i wybierz ją.

    (Jeśli korzystasz z komputera Mac, otwórz go Outlook na pasku narzędzi lub zlokalizuj go przy użyciu programu Finder).

    Jeśli właśnie zainstalowano aplikację Outlook, na stronie Powitanie wybierz pozycję **Dalej**.

2. Wybierz **pozycję Informacje** \> **o pliku** \> **, dodaj konto**.

3. Wprowadź swój adres e-mail firmy Microsoft i wybierz **Połączenie**.

## <a name="watch-set-up-outlook-for-email"></a>Obejrzyj: Konfigurowanie poczty e Outlook-mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
Więcej na [stronie Konfigurowanie poczty Outlook-mail](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>Importowanie poczty e-mail

Jeśli wcześniej używano programu Outlook-mail, możesz zaimportować poprzednie wiadomości e-mail, kalendarz i kontakty do nowego konta Microsoft.
  
1. **Eksportowanie starych wiadomości e-mail**

    In Outlook, choose **File** \> **Open &amp; Export** \> **Import/Export**.

    Wybierz **pozycję Eksportuj do pliku, a** następnie postępuj zgodnie z instrukcjami, aby wyeksportować plik Outlook danych (pst) i wszystkie podfoldery.

2. **Importowanie starych wiadomości e-mail**

    W Outlook wybierz ponownie **pozycję Otwórz** \> **plik &amp;** \> **eksportu Import/Export** plik.

    Tym razem wybierz pozycję **Importuj z innego programu** lub pliku i postępuj zgodnie z instrukcjami, aby zaimportować plik kopii zapasowej utworzony podczas eksportowania starych wiadomości e-mail.

## <a name="watch-import-and-redirect-email"></a>Obejrzyj: Importowanie i przekierowywanie poczty e-mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Więcej na stronie [Importowanie poczty e-mail za pomocą Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Możesz również zaimportować <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">pocztę e-Exchange e-mail</a> wszystkich osób przy użyciu centrum administracyjnego programu SharePoint. Aby uzyskać więcej informacji, zobacz [Migrowanie wielu kont e-mail](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>Konfigurowanie usługi Microsoft Teams i OneDrive dla firm

Wybierz ikonę OneDrive na pasku zadań i postępuj zgodnie z instrukcjami, aby przenieść pliki do nowego OneDrive dla Firm folderu. Wybierz **pozycję Dalej**, aby Microsoft Teams.

1. Otwórz Microsoft Teams, wybierz ikonę profilu, a następnie dodaj **konto służbowe**. Postępuj zgodnie z instrukcjami, aby dodać nowe konto do Teams.

## <a name="use-a-public-website"></a>Korzystanie z publicznej witryny sieci Web

Microsoft 365 nie obejmuje publicznej witryny internetowej Twojej firmy. Jeśli chcesz skonfigurować taki program, rozważ korzystanie z usług partnera firmy Microsoft, takiego jak GoDaddy lub WIX.
  
1. W centrum administracyjnym przejdź do pozycji **Zasoby**, a następnie wybierz pozycję **Publiczna witryna sieci Web**.

2. Wybierz **pozycję Dowiedz się** więcej w obszarze jednej z opcji, a następnie zarejestruj się u partnera witryny internetowej i użyj narzędzi, aby skonfigurować i zaprojektować witrynę.

## <a name="watch-create-your-business-website"></a>Obejrzyj: Tworzenie witryny internetowej Twojej firmy

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>Zapraszanie użytkowników do dołączenia do Twojej subskrypcji i organizacji

Po skonfigurowaniu organizacji możesz zaprosić innych użytkowników do dołączenia do Twojej subskrypcji usługi Microsoft 365 dla firm. Uzyskają dostęp do wszystkich funkcji subskrypcji.

[Zaproś użytkowników do mojej subskrypcji](../simplified-signup/admin-invite-business-standard.md)

Poukaj użytkownikom, że mogą oni wykonać czynności opisane w poniższych artykułach, aby dołączyć do Twojej organizacji i subskrypcji.

- [Akceptowanie zaproszenia pocztą e-mail](../simplified-signup/user-invite-business-standard.md)

- [Akceptowanie zaproszenia pocztą e-mail przy Outlook, Yahoo, Gmail lub innym koncie (użytkownik)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>Tematy pokrewne

[Migrowanie danych do mojej Microsoft 365 Business Standard subskrypcji usługi](../simplified-signup/migrate-data-business-standard.md)
