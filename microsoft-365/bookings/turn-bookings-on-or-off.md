---
title: Włącz lub wyłącz aplikację Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Dowiedz się, jak uzyskać dostęp do Microsoft Bookings w Microsoft 365.
ms.openlocfilehash: a2ab25b3b187ba45dfe460991b91e77d70a2bb70
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715280"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Włącz lub wyłącz aplikację Microsoft Bookings

> [!NOTE]
> Ten artykuł ułatwia interakcję z najnowszą wersją Microsoft Bookings. Poprzednie wersje zostaną wycofane w najbliższych miesiącach.

Ten artykuł jest przeznaczony dla administratorów. 

Bookings można włączyć lub wyłączyć dla całej organizacji lub dla określonych użytkowników. Po włączeniu Bookings dla użytkowników mogą oni utworzyć stronę Bookings, utworzyć kalendarz i zezwolić innym osobom na zarezerwowanie z nimi czasu.

> [!NOTE]
> Kontrolki administratora opisane w tych sekcjach nie są dostępne dla klientów Office 365 obsługiwanych przez klientów 21Vianet (Chiny).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Włączanie lub wyłączanie Bookings dla organizacji przy użyciu Centrum administracyjne platformy Microsoft 365

1. Zaloguj się do Centrum administracyjne platformy Microsoft 365 jako administrator globalny.

2. W centrum administracyjnym przejdź do Ustawienia <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**ustawienia organizacji**</a> **** \>.

3. Zaznacz pole wyboru **Zezwalaj organizacji na używanie Bookings** do włączania lub wyłączania Bookings dla organizacji.

   > [!NOTE]
   > Wyłączenie Bookings spowoduje wyłączenie całego dostępu do usługi, w tym tworzenia stron Bookings i zarządzania nimi.

4. Wybierz opcję **Zapisz zmiany**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Włączanie lub wyłączanie Bookings dla organizacji przy użyciu programu PowerShell

Aby włączyć lub wyłączyć Bookings dla organizacji przy użyciu polecenia cmdlet Programu PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [Połączenie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i uruchomić następujące polecenie:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="granular-controls"></a>Kontrolki szczegółowe

Użyj poniższych ustawień, aby kontrolować, kto może korzystać z Bookings, zdecydować, jakie Bookings informacje są udostępniane i czy pracownicy potrzebują zatwierdzenia przed dodaniem ich do kalendarza rezerwacji.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Zrzut ekranu: Ustawienia, które umożliwiają kontrolowanie, kto może korzystać z Bookings, decydowanie o tym, jakie informacje Bookings są udostępniane, i zatwierdzanie przez personel":::

### <a name="block-bookings-from-outside-your-organization"></a>Blokowanie rezerwacji spoza organizacji

Możesz skonfigurować Bookings, aby tylko osoby w organizacji mogły rezerwować terminy. Tylko użytkownicy w organizacji, którzy się zalogowali i są uwierzytelnieni, mogą rezerwować terminy.

### <a name="block-social-sharing-options"></a>Blokuj opcje udostępniania społecznościowego

Możesz kontrolować sposób udostępniania stron rezerwacji w sieciach społecznościowych. To ustawienie jest dostępne w Centrum administracyjne platformy Microsoft 365 w obszarze **ustawień** ->  **Ustawienia** ->  Org **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Blokuj udostępnianie szczegółów personelu klientom

Dane personelu, takie jak informacje kontaktowe, nigdy nie zostaną wysłane do klientów za pośrednictwem poczty e-mail lub innej komunikacji.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Wymagaj zatwierdzeń personelu przed udostępnieniem informacji wolnych/zajętych

Możesz wymagać od pracowników w organizacji, aby wyrazili zgodę przed udostępnieniem informacji o dostępności za pośrednictwem Bookings i zanim będą mogli dokonać rezerwacji za pośrednictwem strony rezerwacji.

Po włączeniu tego ustawienia osoby dodane jako pracownicy kalendarzy rezerwacji otrzymają wiadomość e-mail z linkiem do **strony Zatwierdzanie/odrzucanie** żądania.

## <a name="restrict-collection-of-customer-data"></a>Ograniczanie zbierania danych klientów

Ze względu na zgodność możesz nie chcieć zbierać niektórych informacji o kliencie. Jeśli zaznaczysz pole wyboru dla żadnej z tych opcji, te pola nie zostaną uwzględnione w formularzach wyświetlanych klientom ani klientom.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Zrzut ekranu: zaznacz pola wyboru, aby uniemożliwić klientom udostępnianie Ci poufnych danych":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Włączanie lub wyłączanie Bookings dla poszczególnych użytkowników

Możesz wyłączyć Bookings dla poszczególnych użytkowników.

1. Przejdź do Centrum administracyjne platformy Microsoft 365, a następnie wybierz pozycję **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**aktywni użytkownicy**</a>.

1. Wybierz żądanego użytkownika, a następnie wybierz pozycję **Licencje i aplikacje**.

1. Rozwiń pozycję **Aplikacje** i wyczyść pole wyboru Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Zezwalaj tylko wybranym użytkownikom na tworzenie kalendarzy Bookings

Korzystając z ograniczeń zasad, można ograniczyć licencjonowanym użytkownikom możliwość tworzenia Bookings kalendarzy. Najpierw należy włączyć Bookings dla całej organizacji. Wszyscy użytkownicy w organizacji będą mieć licencje Bookings, ale tylko ci, którzy są uwzględnieni w zasadach, mogą tworzyć kalendarze Bookings i mieć pełną kontrolę nad tym, kto może uzyskiwać dostęp do utworzonych kalendarzy.

Użytkownicy, którzy są uwzględnieni w tych zasadach, mogą tworzyć nowe kalendarze Bookings i mogą być dodawani jako pracownicy w dowolnej pojemności (w tym roli administratora) do istniejących kalendarzy Bookings. Użytkownicy, którzy nie są uwzględnieni w tych zasadach, nie będą mogli tworzyć nowych kalendarzy Bookings i otrzymają komunikat o błędzie, jeśli spróbują to zrobić.

Należy uruchomić następujące polecenia przy użyciu Exchange Online programu PowerShell. Aby uzyskać więcej informacji na temat uruchamiania poleceń cmdlet Exchange Online, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> W poniższych krokach założono, że żadne inne zasady skrzynki pocztowej Outlook Web App (OWA) nie zostały utworzone w organizacji.

1. Utwórz nowe zasady skrzynki pocztowej dla użytkowników, którzy powinni mieć możliwość tworzenia kalendarzy Bookings. (Bookings tworzenie kalendarza jest domyślnie dozwolone przez nowe zasady skrzynki pocztowej).

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Aby uzyskać więcej informacji, zobacz [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Przypisz te zasady do odpowiednich użytkowników, uruchamiając to polecenie dla każdego użytkownika, który chcesz udzielić uprawnień do tworzenia kalendarzy Bookings.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Aby uzyskać więcej informacji, zobacz [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Opcjonalnie: uruchom to polecenie, jeśli chcesz wyłączyć Bookings dla wszystkich innych użytkowników w organizacji.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Aby uzyskać więcej informacji, zobacz [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Aby uzyskać więcej informacji na temat zasad skrzynki pocztowej OWA, zapoznaj się z następującymi tematami:

- [Tworzenie zasad skrzynki pocztowej Outlook w sieci Web w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Stosowanie lub usuwanie zasad skrzynki pocztowej Outlook w sieci Web w skrzynce pocztowej w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
