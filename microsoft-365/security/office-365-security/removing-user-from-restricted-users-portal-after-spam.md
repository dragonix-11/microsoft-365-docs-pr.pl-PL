---
title: Usuwanie zablokowanych użytkowników z portalu Użytkownicy z ograniczeniami
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
description: Administratorzy mogą dowiedzieć się, jak usuwać użytkowników ze strony Użytkownicy z ograniczeniami w Microsoft 365 Defender sieci Web. Użytkownicy są dodawana do portalu użytkowników z ograniczeniami w celu wysyłania spamu wychodzącego, zazwyczaj w wyniku naruszenia bezpieczeństwa konta.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c375d77c3aa64d996a8d8d2f8dce538829eaa3b2
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568319"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>Usuwanie zablokowanych użytkowników z portalu Użytkownicy z ograniczeniami w programie Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli użytkownik przekroczy jedną z limitów wysyłania połączeń wychodzących określonych w [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) limitach usług lub zasadach spamu wychodzącego[, użytkownikowi](configure-the-outbound-spam-policy.md) zostanie ograniczone ograniczenie dotyczące wysyłania wiadomości e-mail, ale nadal może on odbierać wiadomości e-mail.

Użytkownik zostanie dodany do strony **Użytkownicy** z ograniczeniami w Microsoft 365 Defender sieci Web. Podczas próby wysłania wiadomości e-mail jest zwracana w raporcie o niedostarczeniu (nazywanym również raportem o niedostarczeniu lub wiadomości zwróconej) z kodem błędu [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) i następującym tekstem:

> "Nie można dostarczyć wiadomości, ponieważ nie rozpoznano Ciebie jako prawidłowego nadawcy. Najczęstszą przyczyną tego jest podejrzewanie, że Twój adres e-mail wysyła spam i nie może już wysyłać wiadomości e-mail.  Skontaktuj się z administratorem poczty e-mail, aby uzyskać pomoc. Serwer zdalny zwrócił "Odmowa dostępu 550 5.1.8, zły nadawca ruchu wychodzącego".

Administratorzy mogą usuwać użytkowników ze strony **Użytkownicy z ograniczeniami** w programie Microsoft 365 Defender lub Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Użytkownicy z ograniczeniami**, użyj .<https://security.microsoft.com/restrictedusers>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby usunąć użytkowników z portalu Użytkownicy z ograniczeniami, musisz być członkiem grup ról Zarządzanie  organizacją lub **Administrator** zabezpieczeń.
  - Aby uzyskać dostęp tylko do odczytu do portalu użytkowników z ograniczeniami, musisz być członkiem grup ról  Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w aplikacji  Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  >
  > - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Nadawca, który przekroczył limity wychodzącej poczty e-mail, jest wskaźnikiem naruszonego konta. Zanim usuniesz użytkownika z portalu Użytkownicy z ograniczeniami, wykonaj wymagane czynności, aby odzyskać kontrolę nad jego kontem. Aby uzyskać więcej informacji, [zobacz Odpowiadanie na naruszone konto e-mail w programie Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Usuwanie użytkownika Microsoft 365 Defender z listy Użytkownicy z ograniczeniami przy użyciu portalu Microsoft 365 Defender użytkowników

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do tematu Współpraca **za & e-mail** \> **Przejrzyj ograniczone** \> **użytkownicy**. Aby przejść bezpośrednio do strony **Użytkownicy z ograniczeniami**, użyj .<https://security.microsoft.com/restrictedusers>

2. Na stronie **Użytkownicy z ograniczeniami** znajdź i wybierz użytkownika, którego chcesz odblokować, klikając tego użytkownika.

3. Kliknij **wyświetloną akcję** Odblokuj.

4. W **wyświetlonym wysuwaniu Odblokuj** użytkownika przeczytaj szczegóły dotyczące konta z ograniczeniami. Należy przejść przez zalecenia, aby upewnić się, że w razie naruszenia bezpieczeństwa konta są podejmowane odpowiednie działania.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na następnym ekranie po zaleceniach dotyczących bezpieczeństwa w przyszłości. Włączenie uwierzytelniania wieloskładnikowego (MFA) i resetowanie hasła to dobra metoda.

   Po zakończeniu kliknij pozycję **Prześlij**.

6. Kliknij **przycisk Tak** , aby potwierdzić zmianę.

   > [!NOTE]
   > Usunięcie wszystkich ograniczeń od użytkownika może potrwać do 1 godziny.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Sprawdzanie ustawień alertów dla użytkowników z ograniczeniami

Domyślne zasady alertów o nazwie **Użytkownik z ograniczonymi możliwościami** wysyłania wiadomości e-mail będą automatycznie powiadamiać administratorów, jeśli użytkownicy mają zablokowaną opcję wysyłania poczty wychodzącej. Możesz zweryfikować te ustawienia i dodać kolejnych użytkowników do powiadomienia. Aby uzyskać więcej informacji na temat zasad alertów, zobacz [Zasady alertów w programie Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Aby alerty działały, należy włączona jest przeszukiwanie dziennika inspekcji. Aby uzyskać więcej informacji, zobacz Włączanie lub wyłączanie [przeszukiwania dziennika inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do tematu Zasady **& e-mail** \> **& Zasady** \> **alertów**. Aby przejść bezpośrednio do strony **zasady alertu**, użyj .<https://security.microsoft.com/alertpolicies>

2. Na stronie **Zasady alertów** znajdź i wybierz alert o nazwie Użytkownik ograniczony do wysyłania **wiadomości e-mail**. Zasady można sortować według nazw lub wyszukiwać je za  pomocą pola wyszukiwania.

3. W **wyświetlonym czacie** z ograniczeniami do wysyłania wiadomości e-mail sprawdź lub skonfiguruj następujące ustawienia:
   - **Stan**: sprawdź, czy alert jest włączony![.](../../media/scc-toggle-on.png)
   - **Adresaci wiadomości e-mail**: Kliknij pozycję **Edytuj** i sprawdź lub skonfiguruj następujące ustawienia **w wyświetlonym** wysuwanych oknie Edytowanie adresatów:
     - **Wysyłanie powiadomień e-mail**: Sprawdź, czy ta opcja jest **zaznaczona (Wł.**).
     - **Adresaci poczty e-mail**: wartość domyślna to **TenantAdmins** (co oznacza, **członkowie administratora globalnego** ). Aby dodać więcej adresatów, kliknij pusty obszar w polu. Zostanie wyświetlona lista adresatów, w przypadku których możesz rozpocząć wpisywanie nazwy w celu filtrowania i wybrania adresata. Możesz usunąć istniejącego adresata z pola, klikając ikonę ![Usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok jej imienia i nazwiska.
     - **Dzienny limit powiadomień**: Wartość domyślna to Bez **limitu** , ale możesz wybrać limit maksymalnej liczby powiadomień dziennie.

     Po zakończeniu kliknij przycisk **Zapisz**.

4. Na **wysuwanych wiadomościach z ograniczeniami do wysyłania wiadomości e-mail** przez użytkownika kliknij przycisk **Zamknij**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Wyświetlanie Exchange Online i usuwanie użytkowników z listy Użytkowników z ograniczeniami przy użyciu programu PowerShell

Aby wyświetlić tę listę użytkowników, którzy nie mogą wysyłać wiadomości e-mail, uruchom następujące polecenie:

```powershell
Get-BlockedSenderAddress
```

Aby wyświetlić szczegółowe informacje o określonym użytkowniku, zamień go \<emailaddress\> na jego adres e-mail i uruchom następujące polecenie:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-BlockedSenderAddress(Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress)).

Aby usunąć użytkownika z listy Użytkownicy z ograniczeniami, zamień \<emailaddress\> go na jego adres e-mail i uruchom następujące polecenie:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
