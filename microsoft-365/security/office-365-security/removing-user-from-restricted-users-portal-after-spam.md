---
title: Usuwanie zablokowanych użytkowników z portalu użytkowników z ograniczeniami
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.exch.eac.ActionCenter.Restricted.Users.RestrictedUsers
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak usunąć użytkowników ze strony Użytkownicy z ograniczeniami w portalu Microsoft 365 Defender. Użytkownicy są dodawani do portalu użytkowników z ograniczeniami w celu wysyłania spamu wychodzącego, zazwyczaj w wyniku naruszenia zabezpieczeń konta.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 229dfbb7a0441f4a6cb6632432c0032f4ce4308e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130741"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>Usuwanie zablokowanych użytkowników z portalu użytkowników z ograniczeniami w Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli użytkownik przekroczy jeden z limitów wysyłania wychodzących określonych w [limitach usług](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) lub [w zasadach spamu wychodzącego](configure-the-outbound-spam-policy.md), użytkownik nie może wysyłać wiadomości e-mail, ale nadal może odbierać wiadomości e-mail.

Użytkownik jest dodawany do strony **Użytkownicy z ograniczeniami** w portalu Microsoft 365 Defender. Podczas próby wysłania wiadomości e-mail wiadomość jest zwracana w raporcie o braku dostarczenia (znanym również jako komunikat NDR lub bounce) z kodem błędu [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) i następującym tekstem:

> "Nie można dostarczyć wiadomości, ponieważ nie zostałeś rozpoznany jako prawidłowy nadawca. Najczęstszą przyczyną jest to, że twój adres e-mail jest podejrzany o wysyłanie spamu i nie może już wysyłać wiadomości e-mail.  Skontaktuj się z administratorem poczty e-mail, aby uzyskać pomoc. Serwer zdalny zwrócił komunikat "550 5.1.8 Odmowa dostępu, nieprawidłowy nadawca wychodzący".

Administratorzy mogą usuwać użytkowników ze strony **Użytkownicy z ograniczeniami** w Microsoft 365 Defender lub w programie Exchange Online Programu PowerShell.

## <a name="learn-more-on-restricted-entities"></a>Dowiedz się więcej na temat jednostek z ograniczeniami

Jednostka z ograniczeniami to jednostka, która nie mogła wysyłać wiadomości e-mail, ponieważ została potencjalnie naruszona lub przekroczyła limit wysyłania.

Istnieją 2 typy jednostek z ograniczeniami: 

- **Użytkownik z ograniczeniami**: dowiedz się, dlaczego użytkownik może być ograniczony i jak obsługiwać użytkowników z ograniczeniami (w tym artykule).  

- **Łącznik z ograniczeniami**: Aby uzyskać więcej informacji o tym, dlaczego można ograniczyć łącznik i jak obsługiwać łączniki z ograniczeniami, zobacz [Usuwanie zablokowanych łączników z portalu jednostek z ograniczeniami](remove-blocked-connectors.md). 

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Użytkownicy z ograniczeniami** , użyj polecenia <https://security.microsoft.com/restrictedusers>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby usunąć użytkowników z portalu użytkowników z ograniczeniami, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do portalu użytkowników z ograniczeniami, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  >
  > - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Nadawca przekraczający limity wychodzącej poczty e-mail jest wskaźnikiem konta, które zostało naruszone. Przed usunięciem użytkownika z portalu Użytkownicy z ograniczeniami wykonaj wymagane kroki, aby odzyskać kontrolę nad swoim kontem. Aby uzyskać więcej informacji, zobacz [Odpowiadanie na naruszone konto e-mail w Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Usuwanie użytkownika z listy Użytkowników z ograniczeniami przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Poczta e-mail & współpracy** \> **Przejrzyj** \> **użytkowników z ograniczeniami**. Aby przejść bezpośrednio do strony **Użytkownicy z ograniczeniami** , użyj polecenia <https://security.microsoft.com/restrictedusers>.

2. Na stronie **Użytkownicy z ograniczeniami** znajdź i wybierz użytkownika, który chcesz odblokować, klikając użytkownika.

3. Kliknij wyświetloną akcję **Odblokuj** .

4. W wyświetlonym oknie wysuwnym **Odblokuj użytkownika** przeczytaj szczegóły dotyczące konta z ograniczeniami. Należy zapoznać się z zaleceniami, aby upewnić się, że podejmujesz odpowiednie akcje w przypadku naruszenia zabezpieczeń konta.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Następny ekran zawiera zalecenia, które pomogą zapobiec przyszłemu kompromisowi. Włączenie uwierzytelniania wieloskładnikowego (MFA) i zresetowanie hasła to dobra ochrona.

   Po zakończeniu kliknij pozycję **Prześlij**.

6. Kliknij przycisk **Tak** , aby potwierdzić zmianę.

   > [!NOTE]
   > Usunięcie wszystkich ograniczeń z użytkownika może potrwać do 1 godziny.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami

Domyślne zasady alertów o nazwie **Użytkownik z ograniczeniami wysyłania wiadomości e-mail** będą automatycznie powiadamiać administratorów, gdy użytkownicy będą blokować wysyłanie poczty wychodzącej. Możesz zweryfikować te ustawienia i dodać dodatkowych użytkowników do powiadomienia. Aby uzyskać więcej informacji na temat zasad alertów, zobacz [Zasady alertów w Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Aby alerty działały, należy włączyć wyszukiwanie dzienników inspekcji. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dziennika inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru Zasady **współpracy** \> & poczty e-mail **& reguły** \> **alertów**. Aby przejść bezpośrednio do strony **zasad alertów** , użyj polecenia <https://security.microsoft.com/alertpolicies>.

2. Na stronie **Zasady alertów** znajdź i wybierz alert o nazwie **Użytkownik ograniczony do wysyłania wiadomości e-mail**. Zasady można posortować według nazwy lub znaleźć zasady za pomocą pola **Wyszukaj** .

3. W wyświetlonym oknie wysuwu **wiadomości e-mail użytkownik nie może wysyłać wiadomości e-mail** , sprawdź lub skonfiguruj następujące ustawienia:
   - **Stan**: sprawdź, czy alert jest włączony ![Włączyć przełącznik.](../../media/scc-toggle-on.png)
   - **Adresaci wiadomości e-mail**: kliknij pozycję **Edytuj** i sprawdź lub skonfiguruj następujące ustawienia w wyświetlonym wysuwu **Edytuj adresatów** :
     - **Wysyłanie powiadomień e-mail**: sprawdź, czy wybrano tę **opcję (włączone**).
     - **Adresaci wiadomości e-mail**: wartość domyślna to **TenantAdmins** (czyli członkowie **administratora globalnego** ). Aby dodać więcej adresatów, kliknij pusty obszar pola. Zostanie wyświetlona lista adresatów i możesz zacząć wpisywać nazwę, aby filtrować i wybierać adresata. Możesz usunąć istniejącego adresata z pola, klikając pozycję Usuń ikonę ![.](../../media/m365-cc-sc-remove-selection-icon.png) obok ich nazwy.
     - **Dzienny limit powiadomień**: wartość domyślna **to Brak limitu** , ale możesz wybrać limit maksymalnej liczby powiadomień dziennie.

     Po zakończeniu kliknij przycisk **Zapisz**.

4. Wróć do obszaru **Użytkownik z ograniczeniami wysyłania wysuwanych wiadomości e-mail** , kliknij przycisk **Zamknij**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Wyświetlanie i usuwanie użytkowników z listy Użytkowników z ograniczeniami przy użyciu programu Exchange Online PowerShell

Aby wyświetlić tę listę użytkowników, którzy nie mogą wysyłać wiadomości e-mail, uruchom następujące polecenie:

```powershell
Get-BlockedSenderAddress
```

Aby wyświetlić szczegółowe informacje o określonym użytkowniku, zastąp \<emailaddress\> ciąg swoim adresem e-mail i uruchom następujące polecenie:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Aby usunąć użytkownika z listy Użytkownicy z ograniczeniami, zastąp \<emailaddress\> ciąg swoim adresem e-mail i uruchom następujące polecenie:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
