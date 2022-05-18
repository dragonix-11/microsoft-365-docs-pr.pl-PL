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
description: 'Dowiedz się, jak przekonwertować prywatną skrzynkę pocztową na udostępnioną skrzynkę pocztową, do której może uzyskać dostęp kilka osób, a nie tylko jedna osoba. '
ms.openlocfilehash: 07b36e5c8b2cb7b2e88dfedd80b31353cb8f7e32
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466223"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową

Podczas konwertowania skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową wszystkie istniejące wiadomości e-mail i kalendarz są zachowywane. Dopiero teraz jest w udostępnionej skrzynce pocztowej, w której kilka osób będzie mogło uzyskać do niej dostęp zamiast jednej osoby. W późniejszym terminie można przekonwertować udostępnioną skrzynkę pocztową z powrotem na skrzynkę pocztową użytkownika (prywatną).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

**Oto kilka naprawdę ważnych rzeczy, które musisz wiedzieć**:

- Skrzynka pocztowa użytkownika musi mieć przypisaną licencję, zanim przekonwertujesz ją na udostępnioną skrzynkę pocztową. W przeciwnym razie nie będzie widoczna opcja konwertowania skrzynki pocztowej. Jeśli licencja została usunięta, dodaj ją z powrotem, aby można było przekonwertować skrzynkę pocztową. Po przekonwertowaniu skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową możesz usunąć licencję z konta użytkownika.

- Bez licencji udostępnione skrzynki pocztowe są ograniczone do 50 GB. Może być konieczne usunięcie wielu dużych wiadomości (np. wiadomości z załącznikami) ze udostępnionej skrzynki pocztowej, aby zmniejszyć ją, aby można było usunąć licencję.

  Aby zwiększyć limit rozmiaru do 100 GB, przypisz licencję Exchange Online Plan 2 do udostępnionej skrzynki pocztowej.

  Jeśli przypiszesz licencję Exchange Online Plan 1 i licencję Exchange Online — archiwum dodatku do udostępnionej skrzynki pocztowej, możesz włączyć automatyczne rozszerzanie archiwizacji w celu zwiększenia pojemności magazynu archiwum.

- Nie usuwaj konta starego użytkownika, ponieważ konto jest wymagane do zakotwiczenia udostępnionej skrzynki pocztowej. Jeśli konto użytkownika zostało już usunięte, zobacz [Konwertowanie skrzynki pocztowej usuniętego użytkownika](#convert-the-mailbox-of-a-deleted-user).

- Nie musisz resetować hasła konta skrzynki pocztowej użytkownika. Jeśli jednak nie zresetujesz hasła, **oryginalna nazwa użytkownika i hasło będą nadal działać w udostępnionej skrzynce pocztowej** po zakończeniu konwersji.

- Reguły skrzynki odbiorczej są zachowywane po przekonwertowania skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową.

- Aby wstrzymać In-Place lub wstrzymać postępowanie sądowe w udostępnionej skrzynce pocztowej, musisz przypisać licencję Exchange Online plan 2 *lub* licencję Exchange Online plan 1 i licencję dodatku Exchange Online — archiwum do udostępnionej skrzynki pocztowej.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Konwertowanie skrzynki pocztowej przy użyciu klasycznego centrum administracyjnego Exchange

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">klasycznego centrum administracyjnego Exchange</a>.

2. Wybierz pozycję **Skrzynki pocztowe adresatów**\>.

3. Wybierz skrzynkę pocztową użytkownika. W obszarze **Konwertuj na udostępnioną skrzynkę pocztową** wybierz pozycję **Konwertuj**.

4. Jeśli skrzynka pocztowa jest mniejsza niż 50 GB, możesz usunąć [licencję od użytkownika](../manage/remove-licenses-from-users.md) i przestać za nią płacić. Nie usuwaj konta użytkownika. Udostępniona skrzynka pocztowa potrzebuje jej jako kotwicy. W przypadku konwertowania skrzynki pocztowej pracownika, który opuszcza organizację, należy wykonać dodatkowe kroki, aby upewnić się, że nie może już się zalogować. Aby uzyskać więcej informacji, zobacz [Usuwanie byłego pracownika z Microsoft 365](../add-users/remove-former-employee.md).

Aby uzyskać informacje o udostępnionych skrzynkach pocztowych, zobacz [Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) i [Utwórz udostępnioną skrzynkę pocztową](create-a-shared-mailbox.md).

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Konwertowanie skrzynki pocztowej przy użyciu centrum administracyjnego New Exchange

1. Przejdź do <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> centrum administracyjnego Exchange</a>.

2. Wybierz pozycję **Skrzynki pocztowe adresatów**\>.

3. Wybierz skrzynkę pocztową użytkownika. Na karcie **Inne** wybierz pozycję **Konwertuj na udostępnioną skrzynkę pocztową**.

4. Jeśli skrzynka pocztowa jest mniejsza niż 50 GB, możesz usunąć [licencję od użytkownika](../manage/remove-licenses-from-users.md) i przestać za nią płacić. Nie usuwaj konta użytkownika. Udostępniona skrzynka pocztowa potrzebuje jej jako kotwicy. W przypadku konwertowania skrzynki pocztowej pracownika, który opuszcza organizację, należy wykonać dodatkowe kroki, aby upewnić się, że nie może on już się zalogować. Zobacz [Usuwanie byłego pracownika z Microsoft 365](../add-users/remove-former-employee.md).

Aby uzyskać informacje o udostępnionych skrzynkach pocztowych, zobacz [Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) i [Utwórz udostępnioną skrzynkę pocztową](create-a-shared-mailbox.md).

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Konwertowanie skrzynki pocztowej usuniętego użytkownika

Po usunięciu konta użytkownika wykonaj następujące kroki, aby przekonwertować starą skrzynkę pocztową na skrzynkę pocztową udziału:

1. [Przywróć konto użytkownika](../add-users/restore-user.md).

2. Upewnij się, że przypisano do niej licencję Microsoft 365.

3. Zresetuj hasło użytkownika.

4. Poczekaj 20–30 minut na ponowne utworzenie skrzynki pocztowej.

5. Po ponownym utworzeniu skrzynki pocztowej usuń licencję ze skrzynki pocztowej użytkownika. Nie usuwaj starej skrzynki pocztowej użytkownika. Udostępniona skrzynka pocztowa potrzebuje jej jako kotwicy.

6. Dodaj członków do udostępnionej skrzynki pocztowej.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Konwertowanie udostępnionej skrzynki pocztowej z powrotem na (prywatną) skrzynkę pocztową użytkownika

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centrum administracyjnego programu Exchange</a>.

2. Wybierz pozycję **Udostępnione adresaci**\>.

3. Wybierz udostępnioną skrzynkę pocztową. W obszarze **Konwertuj na zwykłą skrzynkę pocztową** wybierz pozycję **Konwertuj**.

4. Wstecz do centrum administracyjnego. W obszarze **Użytkownicy** wybierz konto użytkownika skojarzone ze starą udostępnioną skrzynką pocztową. Przypisz licencję do konta, a następnie zresetuj hasło.

   Konfiguracja skrzynki pocztowej potrwa kilka minut, ale po tym czasie osoba, która będzie korzystać z tego konta, jest gotowa do pracy. Po zalogowaniu zostaną wyświetlone elementy wiadomości e-mail i kalendarza, które były używane w udostępnionej skrzynce pocztowej.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Konwertowanie skrzynki pocztowej użytkownika w środowisku hybrydowym

Aby uzyskać więcej informacji na temat konwertowania skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową w Exchange środowisku hybrydowym, zobacz:

- [Polecenia cmdlet do tworzenia lub modyfikowania zdalnej udostępnionej skrzynki pocztowej w lokalnym środowisku Exchange](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
- [Udostępnione skrzynki pocztowe są nieoczekiwanie konwertowane na skrzynki pocztowe użytkowników po uruchomieniu synchronizacji katalogów w ramach wdrożenia hybrydowego Exchange](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)

> [!NOTE]
> Jeśli jesteś członkiem grupy ról Zarządzanie organizacją lub Zarządzanie adresatami, możesz użyć powłoki zarządzania Exchange, aby zmienić skrzynkę pocztową użytkownika na udostępnioną skrzynkę pocztową lokalnie. Na przykład `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
