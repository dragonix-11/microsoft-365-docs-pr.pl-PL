---
title: Konfigurowanie przesyłania dalej poczty e-mail
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
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ab5eb117-0f22-4fa7-a662-3a6bdb0add74
description: Funkcja przesyłania dalej poczty e-mail umożliwia przesyłanie dalej wiadomości e-mail Microsoft 365 do innej skrzynki pocztowej użytkownika w organizacji lub poza nią.
ms.openlocfilehash: 5522d9202732ca54d1a395a83e99ae2442b68eb9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011409"
---
# <a name="configure-email-forwarding-in-microsoft-365"></a>Konfigurowanie przesyłania dalej poczty e-mail w aplikacji Microsoft 365

Jako administrator organizacji, możesz podlegać firmowe wymagania dotyczące skonfigurowania przesyłania dalej poczty e-mail dla skrzynki pocztowej użytkownika. Funkcja przesyłania dalej poczty e-mail umożliwia przesyłanie dalej wiadomości e-mail wysłanych do skrzynki pocztowej użytkownika do skrzynki pocztowej innego użytkownika w Twojej organizacji lub poza nią.

> [!IMPORTANT]
> Za pomocą zasad filtrowania spamu ruchu wychodzącego można sterować automatycznym przesyłaniem dalej do adresatów zewnętrznych. Aby uzyskać więcej informacji, zobacz [Sterowanie automatycznym zewnętrznym przesyłaniem dalej poczty e-mail w Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding#how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="configure-email-forwarding"></a>Konfigurowanie przesyłania dalej poczty e-mail

Przed skonfigurowaniem przesyłania dalej poczty e-mail warto zwrócić uwagę na następujące kwestie:

- Zezwalaj na automatyczne przesyłanie dalej wiadomości do osób w domenie zdalnej. Aby [uzyskać szczegółowe informacje, zobacz Zarządzanie domenami](/exchange/mail-flow-best-practices/remote-domains/manage-remote-domains) zdalnymi.

- Po skonfigurowaniu przesyłania dalej wiadomości e-mail  będą przesyłane dalej tylko nowe wiadomości e-mail wysyłane do *skrzynki* pocztowej.

- Przesyłanie dalej poczty e-mail wymaga, aby  *konto od*  było licencjonowane. Jeśli konwertujesz przesyłanie dalej poczty e-mail, ponieważ użytkownik odszedł z organizacji, innym rozwiązaniem jest przekonwertowanie jego skrzynki pocztowej na [udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md). Dzięki temu kilka osób może uzyskać do niego dostęp. Jednak rozmiar udostępnionej skrzynki pocztowej nie może przekraczać 50 GB.

Aby wykonać te Microsoft 365, musisz być administratorem Exchange lub administratorem globalnym. Aby uzyskać więcej informacji, zobacz temat Informacje [o rolach administratorów](../add-users/about-admin-roles.md).

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Aktywni** \> **[użytkownicy użytkownicy](https://go.microsoft.com/fwlink/p/?linkid=834822)** .

2. Wybierz nazwę użytkownika, którego adres e-mail chcesz przesyłać dalej, a następnie otwórz stronę właściwości.

3. Na karcie **Poczta** wybierz pozycję **Zarządzaj przesyłaniem dalej wiadomości e-mail**.

4. Na stronie Przesyłanie dalej wiadomości e-mail wybierz pozycję Przesyłaj dalej wszystkie wiadomości e-mail wysyłane do tej skrzynki **pocztowej, wprowadź** adres przesyłania dalej i określ, czy chcesz zachować kopię przesłanych dalej wiadomości e-mail. Jeśli nie widzisz tej opcji, upewnij się, że do konta użytkownika przypisano licencję. Wybierz **pozycję Zapisz zmiany**.

    **Aby przesyłać dalej na wiele adresów** e-mail, możesz poprosić użytkownika o skonfigurowanie reguły w programie Outlook przesyłania dalej na adresy. 
    
    1.  Otwieranie **okna reguł** **strona główna** >**programu** Outlook > > **Wybieranie opcji Zarządzaj regułami & alertów**  
    1. Wybierz **pozycję Nowa reguła** > **Wybierz pozycję Zastosuj regułę do otrzymuję** wiadomości znajdującej się w pobliżu dołu listy, a następnie kliknij przycisk **Dalej**.
    1. Gdy **zostanie** wyświetlony monit Ta reguła zostanie zastosowana do każdej obierania wiadomości, kliknij przycisk Tak. 
    1. Z następnej listy wybierz akcje **przekierowywania do osób lub** do grupy publicznej i **zaprzestań przetwarzania kolejnych reguł**
    1. Kliknij podkreśloną frazę **"osoby" lub "grupa publiczna** " w dolnej części okna.
    1. Wpisz adres **e-mail, na** który chcesz przesyłać pocztę dalej, w polu Do, a następnie kliknij przycisk **OK**.
    1. Wybierz **pozycję Zakończ.**
    

     Możesz też utworzyć grupę dystrybucyjną w centrum [administracyjnym, dodać](add-user-or-contact-to-distribution-list.md) adresy do takiej grupy, [a](../setup/create-distribution-lists.md) następnie skonfigurować przesyłanie dalej w celu wskazania listy dystrybucyjnej, korzystając z instrukcji podanych w tym artykule.

5. Nie usuwaj konta użytkownika, który wysyła dalej pocztę e-mail, ani nie usuwaj jego licencji.  Jeśli to zrobisz, przesyłanie dalej poczty e-mail zostanie zatrzymane.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Aktywni** \> **[użytkownicy użytkownicy](https://go.microsoft.com/fwlink/p/?linkid=850628)** .

2. Wybierz nazwę użytkownika, którego adres e-mail chcesz przesyłać dalej, aby otworzyć stronę właściwości.

3. **Rozwiń sekcję Ustawienia** poczty, a następnie w sekcji **Przesyłanie dalej** wiadomości e-mail wybierz pozycję **Edytuj**.

4. Na stronie przesyłania dalej poczty e-mail ustaw przełącznik w pozycję Wł **., wprowadź** adres przesyłania dalej i określ, czy chcesz zachować kopię wiadomości przesyłanych dalej. Jeśli nie widzisz tej opcji, upewnij się, że do konta użytkownika przypisano licencję. Wybierz **Zapisz**.

   **Aby przesyłać dalej na wiele adresów** e-mail, możesz poprosić użytkownika o skonfigurowanie reguły w programie Outlook przesyłania dalej na adresy. Aby dowiedzieć się więcej, zobacz [Automatyczne przesyłanie wiadomości dalej przy użyciu reguł](https://support.microsoft.com/office/45aa9664-4911-4f96-9663-ece42816d746).

   Możesz też utworzyć grupę dystrybucyjną w centrum [administracyjnym, dodać](add-user-or-contact-to-distribution-list.md) adresy do takiej grupy, [a](../setup/create-distribution-lists.md) następnie skonfigurować przesyłanie dalej w celu wskazania listy dystrybucyjnej, korzystając z instrukcji podanych w tym artykule.

5. Nie usuwaj konta użytkownika, który wysyła dalej pocztę e-mail, ani nie usuwaj jego licencji. Jeśli to zrobisz, przesyłanie dalej poczty e-mail zostanie zatrzymane.

::: moniker-end

## <a name="related-content"></a>Zawartość pokrewna 

[Tworzenie udostępnionej skrzynki pocztowej](../email/create-a-shared-mailbox.md) (artykuł)\
[Wysyłanie wiadomości e-mail z innego adresu](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (artykuł)\
[Zmienianie nazwy użytkownika i adresu e-mail](../add-users/change-a-user-name-and-email-address.md) (artykuł)\
[Control automatic external email forwarding in Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding) (article)


