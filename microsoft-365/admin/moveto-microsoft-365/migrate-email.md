---
title: Migrowanie firmowej poczty e-mail i kalendarza z usługi Google Workspace
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Dowiedz się, jak przeprowadzić migrację poczty e-mail, kontaktów i kalendarza z usługi Google Workspace do usługi Microsoft 365 dla firm.
ms.openlocfilehash: a5ceccfde47b5084326aae9346b1c645cef7114a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014779"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Migrowanie firmowej poczty e-mail i kalendarza z usługi Google Workspace

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Możesz użyć migracji z uruchomiono przez administratora, aby Exchange Online z usługi Google Workspace. Możesz przeprowadzić migrację poczty e-mail jednocześnie lub etapowo. W poniższych krokach popisano, jak przeprowadzić migrację danych poczty e-mail jednocześnie. Aby uzyskać więcej informacji, [zobacz Przeprowadzanie migracji do usługi G Suite](/exchange/mailbox-migration/perform-g-suite-migration).

Proces migracji wymaga kilku etapów, które mogą potrwać od kilku godzin do kilku dni w zależności od ilości migrowania danych.

## <a name="try-it"></a>Spróbuj!

### <a name="create-a-google-service-account"></a>Tworzenie konta usługi Google

1. Za pomocą przeglądarki Chrome zaloguj się do konsoli administracyjnej programu Google [Workspace w admin.google.com](https://admin.google.com). 
1. W nowym oknie lub na nowej karcie przejdź do strony [Konta](https://console.developers.google.com/iam-admin/serviceaccounts) usług. 
1. Wybierz **pozycję Utwórz projekt**, nadaj projektowi nazwę, a następnie wybierz pozycję **Utwórz**. 
1. Wybierz **pozycję Utwórz konto usługi**, wprowadź nazwę, wybierz **pozycję Utwórz,** a następnie **Gotowe**. 
1. Otwórz menu **Akcje** , wybierz **pozycję Edytuj** i zanotuj unikatowy identyfikator. Ten identyfikator będzie potrzebny w dalszej części tego procesu. 
1. Otwórz **sekcję Pokazywanie delegowania dla całej** domeny. 
1. Wybierz **pozycję Włącz delegowanie dla całej domeny usługi G Suite**, wprowadź nazwę produktu na ekranie zgody i wybierz pozycję **Zapisz**. 

    > [!NOTE]
    > Nazwa produktu nie jest używana w procesie migracji, ale musi być zapisywana w oknie dialogowym.     

1. Ponownie otwórz menu **Akcje** i wybierz **pozycję Utwórz klucz**. 
1. Wybierz **pozycję JSON**, a następnie **pozycję Utwórz**. 

     Klucz prywatny zostanie zapisany w folderze pobierania na Twoim urządzeniu.
 
1. Wybierz pozycję **Zamknij**. 

### <a name="enable-api-usage-for-the-project"></a>Włączanie użycia interfejsu API dla projektu

1. Przejdź do strony [interfejsów API](https://console.developers.google.com/apis/library). 
1. Na pasku wyszukiwania wprowadź tekst **Interfejs API usługi Gmail**.
1. Zaznacz go, a następnie wybierz pozycję **Włącz**.
1. Powtórz ten proces dla interfejsu API Kalendarza Google, interfejsu Api Osób i interfejsu API kontaktów. 

### <a name="grant-access-to-the-service-account"></a>Udzielanie dostępu do konta usługi

1. Wróć do konsoli administracyjnej programu Google Workspace. 
1. Wybierz **pozycję Zabezpieczenia**, przewiń w dół i otwórz **kontrolki API**. 
1. Przewiń w dół i wybierz **pozycję Zarządzaj delegowaniem dla całej domeny**.
1. Wybierz **pozycję Dodaj nowy** i wprowadź wcześniej zanotny identyfikator klienta.
1. Następnie wprowadź zakresy protokołu OAuth dla interfejsów API usługi Google. Są one dostępne na [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) kroku 5 i są następujące:

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. Wybierz **pozycję Authorize (Autoryzuj**). 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Tworzenie poddomeny dla poczty przechodzącej do usługi Microsoft 365

1. Wróć do konsoli **administracyjnej programu Google Workspace** .
1. Wybierz **pozycję Domeny**, **Zarządzaj domenami**, **a następnie Dodaj alias domeny**. 
1. Wprowadź alias domeny, taki jak `m365.contoso.com`.
1. Następnie wybierz pozycję **Kontynuuj i zweryfikuj własność domeny**. 

    Weryfikacja domeny trwa zwykle tylko kilka minut, ale może potrwać do 48 godzin.

1. Przejdź do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com).
1. W lewym okienku centrum administracyjne platformy Microsoft 365 wybierz pozycję **Pokaż** >  wszystkie **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>, a następnie **dodaj domenę**. 
1. Wprowadź wcześniej utworzoną poddomenę, a następnie wybierz **pozycję Użyj tej domeny**. 
1. Aby połączyć domenę, wybierz pozycję **Kontynuuj**. 
1. Przewiń w dół i zanotuj rekordy MX, rekordy CNAME oraz rekordy TXT. 
1. Wróć do **konsoli administracyjnej usługi Google**.
1. Wybierz **pozycję Domeny**, wybierz **pozycję Zarządzaj domenami**, **pozycję Zweryfikuj szczegóły** , a następnie pozycję **Zarządzaj domeną**. 
1. W lewym okienku narracji wybierz pozycję **DNS** i przewiń w dół do **opcji Niestandardowe rekordy zasobów**. 
1. Otwórz menu rozwijane typu rekordu i wybierz pozycję **MX**, wprowadź lub skopiuj i wklej wcześniej zanot określone informacje o rekordzie MX, a następnie wybierz pozycję **Dodaj**. 
1. Powtórz tę procedurę dla rekordu CNAME i rekordu TXT. 

    Może mi trochę potrwać, aby te zmiany obowiązywały.  

1. Wróć do miejsca, w którym zostało centrum administracyjne platformy Microsoft 365 i wybierz pozycję **Kontynuuj**. 

Domena jest teraz ustawiona.  

### <a name="create-email-aliases-in-microsoft-365"></a>Tworzenie aliasów e-mail w programie Microsoft 365

Zanim będzie można rozpocząć migrację, musisz utworzyć aliasy e-mail dla użytkowników z nową poddomeną. 

1. Aby rozpocząć następny krok, **w kreatorze** dodawanie domen w centrum administracyjne platformy Microsoft 365 wybierz pozycję **Przejdź do aktywnych użytkowników**. 
1. Wybierz użytkownika, a następnie pozycję **Zarządzaj nazwą użytkownika i pocztą e-mail**. 
1. Z listy **rozwijanej** Domains (Domeny) wybierz utworzoną wcześniej poddomenę. 
1. Wprowadź nazwę użytkownika, **wybierz pozycję Dodaj**, **Zapisz zmiany** i zamknij okno. 

    Powtórz tę procedurę dla każdego użytkownika. 

### <a name="start-the-migration-process"></a>Rozpoczynanie procesu migracji

Po zakończeniu migracji możesz rozpocząć migrację. 

1. W lewym okienku na <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">ekranie centrum administracyjne platformy Microsoft 365</a> w dół do **pozycji Centra** administracyjne i wybierz pozycję **Exchange**. 
1. W **obszarze Adresaci** wybierz pozycję **migracja**, wybierz pozycję **Nowy,** **Exchange Online** do usługi migracji, wybierz pozycję **Migracja usługi G Suite**, a następnie pozycję **Dalej**. 
1. Utwórz plik CSV zawierający listę skrzynek pocztowych, które chcesz poddać migracji. Upewnij się, że plik jest w tym formacie: 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Aby uzyskać szczegółowe [informacje, aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. Wybierz **pozycję Wybierz plik**, przejdź do pliku CSV, wybierz go, wybierz pozycję **Otwórz**, a następnie pozycję **Dalej**. 
1. Sprawdź adres e-mail administratora, którego chcesz użyć do testowania. 
1. Wybierz **pozycję Wybierz plik**, przejdź do utworzonego wcześniej pliku JSON (zwykle w folderze Pobrane na komputerze), wybierz go, wybierz pozycję **Otwórz**, a następnie **pozycję Dalej**. 
1. Wprowadź nazwę w polu **Nazwa nowej partii migracji**.
1. Wprowadź poddomenę utworzoną w polu **Docelowa domena dostarczania** , wybierz pozycję **Dalej**, a następnie **Nowy**. 
1. Po zapisaniu informacji wybierz przycisk **OK**. 

    Możesz teraz wyświetlić stan migracji. 

1. Po upływie pewnego czasu, w zależności od tego, ilu użytkowników migruje, wybierz pozycję **Odśwież**. 
1. Gdy stan zmieni się na **Zsynchronizowano**, wybierz **pozycję Ukończ tę partię migracji, a** następnie pozycję **Tak**. 
1. Po zakończeniu procesu Twój status zmieni się na **Ukończono**. 
1. Jeśli chcesz, możesz wybrać pozycję **Wyświetl szczegóły,** aby uzyskać więcej informacji na temat migracji. 
1. Wybierz pozycję **Zamknij**. 
1. Otwórz Outlook, aby sprawdzić, czy wszystkie wiadomości e-mail z usługi Google Workspace zostały pomyślnie zmigrowane.
Możesz powtórzyć te czynności także w przypadku elementów kalendarza i kontaktów.
