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
ms.openlocfilehash: 09fba96265bc3d2b67db9152f0c6020e10183314
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634806"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Włącz lub wyłącz aplikację Microsoft Bookings

Bookings włączona lub wyłączona dla całej organizacji lub określonych użytkowników. Gdy włączysz Bookings dla użytkowników, będą oni mieli możliwość utworzenia strony Bookings kalendarza, utworzenia kalendarza i umożliwienia innym osobom zarezerwowania czasu.

> [!NOTE]
> Kontrolki administratora opisane w tych sekcjach nie są dostępne dla klientów usługi Office 365 obsługiwanej przez firmę 21Vianet (Chiny).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Włączanie Bookings lub wyłączanie funkcji dla organizacji przy użyciu aplikacji Centrum administracyjne platformy Microsoft 365

1. Zaloguj się do centrum Centrum administracyjne platformy Microsoft 365 jako administrator globalny.

2. W centrum administracyjnym przejdź do pozycji  **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**ustawienia organizacji**</a>.

3. Zaznacz pole wyboru **Zezwalaj** organizacji na używanie aplikacji Bookings lub wyłączanie jej w Bookings organizacji.

   > [!NOTE]
   > Wyłączenie Bookings spowoduje wyłączenie całego dostępu do usługi, łącznie z tworzeniem stron Bookings stron i zarządzaniem nimi.

4. Wybierz opcję **Zapisz zmiany**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Włączanie Bookings lub wyłączanie funkcji dla organizacji przy użyciu programu PowerShell

Aby włączyć Bookings lub wyłączyć dla organizacji przy użyciu polecenia cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) programu PowerShell, Połączenie w celu Exchange Online [programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i uruchom następujące polecenie:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

Za pomocą poniższych ustawień możesz kontrolować, kto Bookings może korzystać z kalendarza, decydować o tym, Bookings mają być udostępniane informacje i czy pracownicy potrzebują zatwierdzenia, zanim będzie go można dodać do kalendarza rezerwacji.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Zrzut ekranu: Ustawienia, które umożliwiają kontrolowanie, kto może Bookings, decydowanie, Bookings udostępniana i zatwierdzanie personelu":::

### <a name="block-bookings-from-outside-your-organization"></a>Blokowanie rezerwacji spoza organizacji

Spotkania możesz skonfigurować Bookings aby tylko osoby w Twojej organizacji mogą rezerwować terminy. Tylko użytkownicy w Twojej organizacji, którzy się zalogowali i są uwierzytelnieni, mogą rezerwować terminy.

### <a name="block-social-sharing-options"></a>Blokowanie opcji udostępniania sieci społecznościowych

Możesz kontrolować sposób współużytkowania stron rezerwacji w sieciach społecznościowych. To ustawienie jest dostępne na Centrum administracyjne platformy Microsoft 365 w **Ustawienia** ->  **Org** ->  **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Blokowanie udostępniania szczegółowych informacji dotyczących personelu klientom

Dane pracowników, takie jak informacje kontaktowe, nigdy nie będą wysyłane do klientów pocztą e-mail ani żadnymi innymi informacjami.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Wymaganie zatwierdzenia personelu przed udostępnieniem informacji o wolnym/zajętym

Możesz wymagać od pracowników w twojej organizacji zgody na zgodę na to, aby ich informacje o dostępności były udostępniane za pośrednictwem usługi Bookings i aby można było ich było zarezerwować za pośrednictwem strony rezerwacji.

Gdy to ustawienie jest włączone, osoby dodane jako personel w kalendarzach rezerwacji otrzymają wiadomość e-mail z linkiem do zatwierdzania **/** odrzucania żądania.

## <a name="restrict-collection-of-customer-data"></a>Ograniczanie zbierania danych klientów

Ze względu na zgodność ze standardami możesz nie chcieć zbierać niektórych informacji o klientach. Jeśli zaznaczysz pole wyboru dla dowolnej z tych opcji, te pola nie będą uwzględniane w formularzach wyświetlanych Twoim klientom ani klientom.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Zrzut ekranu: zaznacz pola wyboru, aby uniemożliwić klientom udostępnianie Ci poufnych danych":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Włączanie Bookings lub wyłączanie dla poszczególnych użytkowników

Możesz wyłączyć funkcję Bookings użytkowników.

1. Przejdź do Centrum administracyjne platformy Microsoft 365, a następnie wybierz **pozycję Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**użytkownicy**</a> użytkownicy.

1. Wybierz odpowiedniego użytkownika, a następnie wybierz **pozycję Licencje i aplikacje**.

1. **Rozwiń aplikacje** i wyczyść pole wyboru dla Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Zezwalaj tylko wybranym użytkownikom na tworzenie Bookings kalendarzy

Stosując ograniczenia zasad, można ograniczyć licencjonowanym użytkownikom możliwość tworzenia Bookings kalendarzy. Najpierw należy włączyć Bookings dla całej organizacji. Wszyscy użytkownicy w organizacji mają licencje Bookings, ale tylko użytkownicy uwzględnioni w zasadach mogą tworzyć kalendarze programu Bookings i mieć pełną kontrolę nad tym, kto ma dostęp do tworzyć kalendarze.

Użytkownicy uwzględnieni w tych zasadach mogą tworzyć nowe kalendarze Bookings i mogą być do nich dodawana jako personel z dowolną wydajnością (wraz z rolą administratora) do istniejących Bookings kalendarzy. Użytkownicy, którzy nie są uwzględnioni w tych zasadach, nie będą mogli tworzyć nowych kalendarzy programu Bookings i w razie próby ich wystąpienia otrzymają komunikat o błędzie.

Poniższe polecenia należy uruchomić przy użyciu programu Exchange Online PowerShell. Aby uzyskać więcej informacji na temat Exchange Online poleceń cmdlet, zobacz Połączenie [aby Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> W poniższej czynności założono, że Outlook Web App nie zostały utworzone żadne inne zasady skrzynek pocztowych aplikacji (OWA).

1. Utwórz nowe zasady skrzynki pocztowej dla użytkowników, którzy powinni mieć możliwość Bookings kalendarzy. (Bookings tworzenia kalendarza jest domyślnie dozwolone przez nowe zasady skrzynki pocztowej.

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Aby uzyskać więcej informacji, [zobacz New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Przypisz te zasady do odpowiednich użytkowników, uruchamiając to polecenie dla każdego użytkownika, którego chcesz udzielić uprawnień do Bookings kalendarzy.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Aby uzyskać więcej informacji, [zobacz Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Opcjonalnie: Uruchom to polecenie, jeśli chcesz wyłączyć funkcję Bookings dla wszystkich innych użytkowników w organizacji.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Aby uzyskać więcej informacji, [zobacz Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Aby uzyskać więcej informacji na temat zasad skrzynek pocztowych aplikacji OWA, zobacz następujące tematy:

- [Tworzenie zasad skrzynki Outlook w sieci Web pocztowej w aplikacji Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Stosowanie lub usuwanie zasad skrzynki Outlook w sieci Web do skrzynki pocztowej w programie Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
