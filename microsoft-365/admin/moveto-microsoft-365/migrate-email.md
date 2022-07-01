---
title: Migrowanie służbowych wiadomości e-mail i kalendarza z obszaru roboczego Google
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
description: Dowiedz się, jak przeprowadzić migrację poczty e-mail, kontaktów i kalendarza z obszaru roboczego Google do platformy Microsoft 365 dla firm.
ms.openlocfilehash: be7637816f80ecba3c56db644114d5ddb00caeb7
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602043"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Migrowanie służbowych wiadomości e-mail i kalendarza z obszaru roboczego Google

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

## <a name="watch-migrate-business-email-and-calendar-from-google-workspace"></a>Obejrzyj: Migrowanie służbowych wiadomości e-mail i kalendarza z obszaru roboczego Google

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198034).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Migracja uruchomiona przez administratora umożliwia Exchange Online z obszaru roboczego Google. Możesz przeprowadzić migrację wiadomości e-mail jednocześnie lub etapami. Poniższe kroki pokazują, jak przeprowadzić migrację danych poczty e-mail jednocześnie. Aby uzyskać więcej informacji, zobacz [Przeprowadzanie migracji do pakietu G Suite](/exchange/mailbox-migration/perform-g-suite-migration).

Proces migracji wykonuje kilka kroków i może potrwać od kilku godzin do kilku dni w zależności od ilości migrowanych danych.

### <a name="create-a-google-service-account"></a>Tworzenie konta usługi Google

1. W przeglądarce Chrome zaloguj się do konsoli administracyjnej obszaru roboczego Google w [admin.google.com](https://admin.google.com). 
1. W nowej karcie lub oknie przejdź do strony [Konta usług](https://console.developers.google.com/iam-admin/serviceaccounts) . 
1. Wybierz pozycję **Utwórz projekt**, nadaj projektowi nazwę, a następnie wybierz pozycję **Utwórz**. 
1. Wybierz pozycję **Utwórz konto usługi**, wprowadź nazwę, wybierz pozycję **Utwórz** , a następnie **pozycję Gotowe**. 
1. Otwórz menu **Akcje** , wybierz pozycję **Edytuj** i zanotuj unikatowy identyfikator. Ten identyfikator będzie potrzebny w dalszej części procesu. 
1. Otwórz sekcję **Pokaż delegowanie dla całej domeny** . 
1. Wybierz pozycję **Włącz delegowanie całej domeny pakietu G Suite**, wprowadź nazwę produktu na ekranie zgody, a następnie wybierz pozycję **Zapisz**. 

    > [!NOTE]
    > Nazwa produktu nie jest używana przez proces migracji, ale jest potrzebna do zapisania w oknie dialogowym.     

1. Otwórz ponownie menu **Akcje** i wybierz pozycję **Utwórz klucz**. 
1. Wybierz **pozycję JSON**, a następnie **pozycję Utwórz**. 

     Klucz prywatny jest zapisywany w folderze pobierania na urządzeniu.
 
1. Wybierz pozycję **Zamknij**. 

### <a name="enable-api-usage-for-the-project"></a>Włączanie użycia interfejsu API dla projektu

1. Przejdź do [strony interfejsów API](https://console.developers.google.com/apis/library). 
1. Na pasku wyszukiwania wprowadź **interfejs API gmaila**.
1. Wybierz go, a następnie wybierz pozycję **Włącz**.
1. Powtórz ten proces dla interfejsu API kalendarza Google, interfejsu API osób i interfejsu API kontaktów. 

### <a name="grant-access-to-the-service-account"></a>Udzielanie dostępu do konta usługi

1. Wróć do konsoli administracyjnej obszaru roboczego Google. 
1. Wybierz pozycję **Zabezpieczenia**, przewiń w dół i otwórz **kontrolki interfejsu API**. 
1. Przewiń w dół i wybierz pozycję **Zarządzaj delegowaniem w całej domenie**.
1. Wybierz pozycję **Dodaj nową** i wprowadź wcześniej zanotiony identyfikator klienta.
1. Następnie wprowadź zakresy uwierzytelniania OAuth dla interfejsów API Google. Są one dostępne w [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) w kroku 5 i są następujące:

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. Wybierz pozycję **Autoryzuj**. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Tworzenie domeny podrzędnej dla poczty przechodzącej do platformy Microsoft 365

1. Wróć do konsoli **administracyjnej obszaru roboczego Google** .
1. Wybierz pozycję **Domeny**, **Zarządzaj domenami**, a następnie **dodaj alias domeny**. 
1. Wprowadź alias domeny, taki jak `m365.contoso.com`.
1. Następnie wybierz pozycję **Kontynuuj i sprawdź własność domeny**. 

    Weryfikacja domeny zwykle trwa zaledwie kilka minut, ale może potrwać do 48 godzin.

1. Przejdź do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com).
1. W Centrum administracyjne platformy Microsoft 365 w lewym pasku nawigacyjnym wybierz pozycję **Pokaż wszystkie** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domeny ustawień**</a> > , a następnie **pozycję Dodaj domenę**. 
1. Wprowadź wcześniej utworzoną poddomenę, a następnie wybierz pozycję **Użyj tej domeny**. 
1. Aby połączyć domenę, wybierz pozycję **Kontynuuj**. 
1. Przewiń w dół i zanotuj rekordy MX, rekordy CNAME i rekordy TXT. 
1. Wróć do **konsoli administracyjnej Google**.
1. Wybierz pozycję **Domeny**, wybierz pozycję **Zarządzaj domenami**, **Sprawdź szczegóły** , a następnie **pozycję Zarządzaj domeną**. 
1. W lewym okienku nawigacji wybierz pozycję **DNS** i przewiń w dół do pozycji **Niestandardowe rekordy zasobów**. 
1. Otwórz listę rozwijaną typu rekordu i wybierz pozycję **MX**, wprowadź lub skopiuj i wklej wcześniej zanotowane informacje o rekordzie MX, a następnie wybierz pozycję **Dodaj**. 
1. Powtórz proces dla rekordu CNAME i rekordu TXT. 

    Może upłynąć trochę czasu, aby te zmiany zaczęły obowiązywać.  

1. Wróć do miejsca, w którym zostało przerwane Centrum administracyjne platformy Microsoft 365, a następnie wybierz pozycję **Kontynuuj**. 

Domena jest teraz skonfigurowana.  

### <a name="create-email-aliases-in-microsoft-365"></a>Tworzenie aliasów wiadomości e-mail na platformie Microsoft 365

Przed rozpoczęciem migracji należy utworzyć aliasy poczty e-mail dla użytkowników z nową poddomeną. 

1. Aby rozpocząć następny krok, w kreatorze **Dodawanie domen** w Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Przejdź do aktywnych użytkowników**. 
1. Wybierz użytkownika, a następnie **pozycję Zarządzaj nazwą użytkownika i wiadomością e-mail**. 
1. Z listy rozwijanej **Domeny** wybierz wcześniej utworzoną poddomenę. 
1. Wprowadź nazwę użytkownika, wybierz pozycję **Dodaj**, **Zapisz zmiany** i zamknij okno. 

    Powtórz ten proces dla każdego użytkownika. 

### <a name="start-the-migration-process"></a>Uruchamianie procesu migracji

Po zakończeniu możesz przystąpić do migracji. 

1. W lewym pasku nawigacyjnym <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> przewiń w dół do **Administracja centrów** i wybierz pozycję **Exchange**. 
1. W obszarze **Adresaci** wybierz **pozycję Migracja**, wybierz pozycję **Nowy**, **Migruj do Exchange Online**, wybierz pozycję **Migracja g suite**, a następnie **dalej**. 
1. Utwórz plik CSV z listą skrzynek pocztowych, które chcesz migrować. Upewnij się, że plik ma następujący format: 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Aby uzyskać szczegółowe informacje [, zobacz aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. Wybierz **pozycję Wybierz plik**, przejdź do pliku CSV, wybierz go, wybierz pozycję **Otwórz**, a następnie **dalej**. 
1. Sprawdź adres e-mail administratora, którego chcesz użyć do testowania. 
1. Wybierz **pozycję Wybierz plik**, przejdź do utworzonego wcześniej pliku JSON (zwykle w folderze Pliki do pobrania na komputerze), wybierz go, wybierz pozycję **Otwórz**, a następnie **dalej**. 
1. Wprowadź nazwę w **polu Nowa nazwa partii migracji**.
1. Wprowadź poddomenę utworzoną w polu **Docelowa domena dostarczania** , wybierz pozycję **Dalej**, a następnie pozycję **Nowy**. 
1. Po zapisaniu informacji wybierz przycisk **OK**. 

    Teraz możesz wyświetlić stan migracji. 

1. Po pewnym czasie, w zależności od liczby migrowanych użytkowników, wybierz pozycję **Odśwież**. 
1. Po zmianie stanu na **Synchronizowane** wybierz pozycję **Zakończ tę partię migracji**, a następnie **pozycję Tak**. 
1. Po zakończeniu procesu stan zmieni się na **Ukończono**. 
1. Jeśli chcesz, możesz wybrać pozycję **Wyświetl szczegóły** , aby uzyskać więcej informacji na temat migracji. 
1. Wybierz pozycję **Zamknij**. 
1. Otwórz program Outlook, aby sprawdzić, czy wszystkie wiadomości e-mail z obszaru roboczego Google zostały pomyślnie zmigrowane.
Można to powtórzyć również w przypadku elementów kalendarza i kontaktów.
