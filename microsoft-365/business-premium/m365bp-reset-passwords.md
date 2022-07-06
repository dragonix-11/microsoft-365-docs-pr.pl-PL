---
title: Resetowanie haseł
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
description: Resetowanie haseł dla użytkowników w Microsoft 365 Business Premium.
ms.openlocfilehash: baa83c54eafbee5f53ac59c9769b802e11485af3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633209"
---
# <a name="reset-passwords-in-microsoft-365-business-premium"></a>Resetowanie haseł w Microsoft 365 Business Premium

Dowiedz się, jak resetować hasła dla siebie i swoich użytkowników w razie potrzeby. Jako administrator możesz zresetować hasło użytkownika, jeśli o nim zapomnisz.

## <a name="user-initiated-password-reset"></a>Resetowanie hasła inicjowane przez użytkownika

Gdy użytkownik zażąda nowego hasła, żądanie resetowania hasła jest wysyłane za pośrednictwem poczty e-mail.

1. Aby zresetować hasło, otwórz program uruchamiania aplikacji i wybierz **pozycję Administracja** i zaloguj się przy użyciu poświadczeń.

2. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Użytkownicy**, <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywni użytkownicy**</a>, a następnie wybierz ikonę klucza obok użytkownika, który zażądał zresetowania.

3. Wybierz pozycję **Automatycznie wygeneruj hasło** , aby automatycznie utworzyć losowe hasło.

4. Wybierz pozycję **Resetuj**.

## <a name="admin-initiated-password-reset"></a>resetowanie hasła inicjowane przez Administracja

Zdarza się, że administrator może chcieć wymusić resetowanie hasła na kontach.

1. W centrum Administracja przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">aktywni użytkownicy</a>.

2. Na stronie **Aktywni użytkownicy** wybierz określonego użytkownika do zresetowania, a następnie wybierz pozycję **Resetuj hasło**.

3. Postępuj zgodnie z instrukcjami na stronie **Resetowanie hasła** , aby automatycznie wygenerować nowe hasło dla użytkownika lub utworzyć je dla niego, a następnie wybierz pozycję **Resetuj**.  

4. Wprowadź adres e-mail, na który użytkownik może uzyskać dostęp, aby otrzymać nowe hasło, i postępuj zgodnie z nimi, aby upewnić się, że je otrzymał.

## <a name="let-users-reset-their-own-passwords"></a>Zezwalanie użytkownikom na resetowanie swoich haseł

Zdecydowanie zalecamy skonfigurowanie samoobsługowego resetowania hasła. Dzięki temu nie będzie konieczne ręczne resetowanie haseł użytkowników. Aby dowiedzieć się, jak to zrobić, zobacz [Zezwalanie użytkownikom na resetowanie swoich haseł w usłudze Office 365](/admin/add-users/let-users-reset-passwords.md).

## <a name="reset-my-admin-password"></a>Resetowanie hasła administratora

Wykonaj następujące kroki, jeśli nie pamiętasz hasła, ale możesz zalogować się na platformie Microsoft 365, ponieważ na przykład hasło jest zapisywane w przeglądarce:

1. Wybierz swoją nazwę (ikonę) w prawym górnym rogu > **Moje dane****osobowe** konta > .

2. W obszarze **Szczegóły kontaktu** sprawdź dokładnie, czy **alternatywna wiadomość e-mail** jest dokładna i czy podano numer telefonu komórkowego. W przeciwnym razie zmień je teraz.

3. Wyloguj się: wybierz swoje imię i nazwisko w prawym górnym rogu \> **Wyloguj.**

4. Teraz zaloguj się ponownie: wpisz nazwę \> użytkownika **Dalej**\>, a następnie wybierz pozycję **Nie pamiętam hasła**.

5. Postępuj zgodnie z instrukcjami kreatora, aby zresetować hasło. Korzystając z alternatywnych informacji kontaktowych, kreator sprawdzi, czy jesteś właściwą osobą do resetowania Twojego hasła.

Jeśli nie pamiętasz hasła i nie możesz się zalogować:

- Poproś innego administratora globalnego w Twojej firmie, aby zresetował hasło za Ciebie.

- Upewnij się, że podano alternatywne informacje kontaktowe, w tym numer telefonu komórkowego.

## <a name="reset-all-business-passwords-for-everyone-at-the-same-time"></a>Resetuj wszystkie hasła biznesowe dla wszystkich jednocześnie

<a name="bkmk_forgot"> </a>

Ta procedura dotyczy firm z dziesiątkami użytkowników. Jeśli masz setki lub tysiące użytkowników, zobacz następną sekcję dotyczącą zbiorczego resetowania haseł (maksymalnie 40 użytkowników jednocześnie).
  
1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Wybierz opcję obok pozycji **Nazwa wyświetlana,** aby wybrać wszystkich w firmie. Następnie usuń zaznaczenie siebie. Nie możesz zresetować swojego hasła w tym samym czasie, w którym resetujesz hasła wszystkich innych osób.

3. Wybierz pozycję **Resetuj hasło**.

4. Postępuj zgodnie z instrukcjami na stronie **Resetowanie hasła** i wybierz pozycję **Resetuj**.  Jeśli zdecydujesz się na automatyczne generowanie haseł, zostaną wyświetlone nowe hasła tymczasowe.

5. Wprowadź adres e-mail, na którym można odbierać hasła tymczasowe. Musisz powiadomić użytkowników, jakie są ich tymczasowe hasła.
  
## <a name="reset-business-passwords-in-bulk"></a>Zbiorcze resetowanie haseł biznesowych

<a name="bkmk_forgot"> </a>

Aby zresetować hasła dla wielu kont, użyj programu PowerShell. Zapoznaj się z tym wpisem autorstwa Eyal Doron: [Zarządzanie hasłami za pomocą programu PowerShell](https://go.microsoft.com/fwlink/?linkid=853696).

Aby uzyskać informacje o przeglądzie, zobacz [Manage Microsoft 365 with PowerShell (Zarządzanie platformą Microsoft 365 przy użyciu programu PowerShell](../enterprise/manage-microsoft-365-with-microsoft-365-powershell.md)).
  
## <a name="related-content"></a>Zawartość pokrewna
  
[Zezwalaj użytkownikom na resetowanie własnych haseł](../admin/add-users/let-users-reset-passwords.md)
 [Resetowanie haseł w usłudze Microsoft 365 dla firm](../admin/add-users/reset-passwords.md)
 [Ustawianie hasła pojedynczego użytkownika tak, aby nigdy nie wygasało](../admin/add-users/set-password-to-never-expire.md) 
 [Ustawianie zasad wygasania haseł dla organizacji](../admin/manage/set-password-expiration-policy.md)