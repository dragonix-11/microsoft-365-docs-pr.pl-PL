---
title: Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Dowiedz się, jak przekonwertować prywatną skrzynkę pocztową na udostępnioną skrzynkę pocztową, do której dostęp może uzyskiwać kilka osób, a nie tylko jedna osoba. '
ms.openlocfilehash: a1b82d744cc43f8119e9819537467133f2bae17c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011415"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową

Po przekonwertowaniu skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową wszystkie istniejące wiadomości e-mail i kalendarz będą zachowywane. Tylko teraz znajduje się on w udostępnionej skrzynce pocztowej, gdzie kilka osób będzie mieć do niego dostęp zamiast jednej osoby. Później możesz przekonwertować udostępnioną skrzynkę pocztową z powrotem na skrzynkę pocztową użytkownika (prywatną).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="before-you-begin"></a>Przed rozpoczęciem

**Oto kilka naprawdę ważnych rzeczy, o których musisz wiedzieć:**

- Przekonwertowana skrzynka pocztowa użytkownika wymaga przypisanej do niego licencji, zanim zostanie przekonwertowana na udostępnioną skrzynkę pocztową. W przeciwnym razie nie zobaczysz opcji przekonwertowania skrzynki pocztowej. Po usunięciu licencji dodaj ją ponownie, aby można było przekonwertować skrzynkę pocztową. Po przekonwertowaniu skrzynki pocztowej na udostępnioną skrzynkę pocztową możesz usunąć licencję z konta użytkownika.

- Udostępnione skrzynki pocztowe mogą mieć maksymalnie 50 GB danych bez przypisanej do nich licencji. Aby przechować więcej danych, potrzebujesz przypisanej do niego licencji. Może być konieczne usunięcie wielu dużych wiadomości e-mail (na przykład z załącznikami) z udostępnionej skrzynki pocztowej w celu zmniejszenia jej w celu usunięcia licencji.

- Nie usuwaj starego konta użytkownika. Jest to wymagane do zakotwiczenia udostępnionej skrzynki pocztowej. Jeśli konto użytkownika zostało już usunięte, zobacz [Konwertowanie skrzynki pocztowej usuniętego użytkownika](#convert-the-mailbox-of-a-deleted-user).

- Reguły zostaną zachowane po przekonwertowaniu skrzynki pocztowej na udostępnioną skrzynkę pocztową.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Konwertowanie skrzynki Exchange klasycznej za pomocą klasycznego centrum administracyjnego
 
1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">klasycznego Exchange administracyjnego</a>.

2. Wybierz **pozycję Skrzynki pocztowe** \> **adresatów**.

3. Wybierz skrzynkę pocztową użytkownika. W **obszarze Konwertuj na udostępnioną skrzynkę pocztową** wybierz pozycję **Konwertuj**.

4. Jeśli skrzynka pocztowa jest mniejsza niż 50 GB, możesz usunąć licencję od [użytkownika i](../manage/remove-licenses-from-users.md) przestać za niego płacić. Nie usuwaj konta użytkownika. Udostępniona skrzynka pocztowa potrzebuje jej jako kotwicy. Jeśli konwertujesz skrzynkę pocztową pracownika, który odchodzi z Twojej organizacji, musisz wykonać dodatkowe czynności, aby upewnić się, że nie może on już się zalogować. Aby uzyskać więcej informacji, [zobacz Usuwanie byłego pracownika z Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Nie jest wymagane resetowanie hasła użytkownika podczas konwersji skrzynki pocztowej. Jeśli jednak hasło nie zostanie zresetowane **,** oryginalna nazwa użytkownika i hasło nadal będą działać po zakończeniu konwersji skrzynki pocztowej.

Aby poznać wszystkie inne informacje o udostępnionych skrzynkach pocztowych, zobacz Informacje o udostępnionych skrzynkach [pocztowych i](about-shared-mailboxes.md) [Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md).

> [!NOTE]
> Udostępnione skrzynki pocztowe nie wymagają osobnej licencji. Jeśli jednak chcesz włączyć archiwum programu In-Place In-Place lub umieścić w udostępnionej skrzynce pocztowej archiwizację w związku z postępowaniem sądowym albo archiwizację w związku z postępowaniem sądowym, musisz przypisać do skrzynki pocztowej licencję Exchange Online Plan 1 z usługą Exchange Online — archiwum lub Exchange Online Plan 2.

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Konwertowanie skrzynki Exchange przy użyciu strony Nowa skrzynka pocztowa

1. Przejdź do Exchange <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> administracyjnego</a>.

2. Wybierz **pozycję Skrzynki pocztowe** \> **adresatów**.

3. Wybierz skrzynkę pocztową użytkownika. Na karcie **Skrzynka** pocztowa w **obszarze Więcej akcji** wybierz pozycję **Konwertuj na udostępnioną skrzynkę pocztową**.

4. Jeśli skrzynka pocztowa jest mniejsza niż 50 GB, możesz usunąć licencję od [użytkownika i](../manage/remove-licenses-from-users.md) przestać za niego płacić. Nie usuwaj konta użytkownika. Udostępniona skrzynka pocztowa potrzebuje jej jako kotwicy. Jeśli konwertujesz skrzynkę pocztową pracownika, który odchodzi z Twojej organizacji, musisz wykonać dodatkowe czynności, aby upewnić się, że nie może się już zalogować. Zobacz [Usuwanie byłego pracownika z Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Nie jest wymagane resetowanie hasła użytkownika podczas konwersji skrzynki pocztowej. Jeśli jednak hasło nie zostanie zresetowane **,** oryginalna nazwa użytkownika i hasło nadal będą działać po zakończeniu konwersji skrzynki pocztowej.

Aby poznać wszystkie inne informacje o udostępnionych skrzynkach pocztowych, zobacz Informacje o udostępnionych skrzynkach [pocztowych i](about-shared-mailboxes.md) [Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md).

> [!NOTE]
> Udostępnione skrzynki pocztowe nie wymagają osobnej licencji. Jeśli jednak chcesz włączyć archiwum programu In-Place In-Place lub umieścić w udostępnionej skrzynce pocztowej archiwizację w związku z postępowaniem sądowym albo archiwizację w związku z postępowaniem sądowym, musisz przypisać do skrzynki pocztowej licencję Exchange Online Plan 1 z usługą Exchange Online — archiwum lub Exchange Online Plan 2.

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Konwertowanie skrzynki pocztowej usuniętego użytkownika

Po usunięciu konta użytkownika wykonaj następujące czynności, aby przekonwertować jego starą skrzynkę pocztową na skrzynkę pocztową udostępnianą:

1. [Przywróć konto użytkownika](../add-users/restore-user.md).

2. Upewnij się, Microsoft 365 do tej licencji jest przypisana licencja.

3. Zresetuj hasło użytkownika.
    
4. Poczekaj 20–30 minut na ponowne utworzenie skrzynki pocztowej.
      
6. Po utworzeniu skrzynki pocztowej usuń licencję ze skrzynki pocztowej użytkownika. Nie usuwaj starej skrzynki pocztowej użytkownika. Udostępniona skrzynka pocztowa potrzebuje jej jako kotwicy.
    
7. Dodaj członków do udostępnionej skrzynki pocztowej.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Konwertowanie udostępnionej skrzynki pocztowej z powrotem na (prywatną) skrzynkę pocztową użytkownika

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centrum administracyjnego programu Exchange</a>.
   
2. Wybierz **pozycję Udostępnili adresaci**\>.

3. Wybierz udostępnioną skrzynkę pocztową. W **obszarze Konwertuj na zwykłą skrzynkę pocztową** wybierz pozycję **Konwertuj**.

4. Wróć do centrum administracyjnego. W **obszarze** Użytkownicy wybierz konto użytkownika skojarzone ze starą udostępnioną skrzynką pocztową. Przypisz licencję do konta, a następnie zresetuj hasło.

   Skonfigurowanie skrzynki pocztowej zajmie kilka minut, ale później będzie ona gotowa do użycia przez osobę, która będzie korzystać z tego konta. Gdy się zaloguje, zobaczy wiadomości e-mail i elementy kalendarza, które kiedyś były w udostępnionej skrzynce pocztowej.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Konwertowanie skrzynki pocztowej użytkownika w środowisku hybrydowym

Aby uzyskać więcej informacji na temat konwertowania skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową w środowisku Exchange hybrydowego, zobacz:

 - [Polecenia cmdlet do tworzenia lub modyfikowania zdalnej udostępnionej skrzynki pocztowej w lokalnym Exchange lokalnym](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
 - [Udostępnione skrzynki pocztowe są nieoczekiwanie konwertowane na skrzynki pocztowe użytkowników po zakończeniu synchronizacji katalogów w Exchange hybrydowym](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)
 

> [!NOTE]
> Jeśli jesteś członkiem grupy ról Zarządzanie organizacją lub Zarządzanie adresatami, możesz za pomocą powłoki zarządzania programu Exchange zmienić skrzynkę pocztową użytkownika na udostępnioną skrzynkę pocztową lokalnie. Na przykład `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
