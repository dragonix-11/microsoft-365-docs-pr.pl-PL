---
title: Uwierzytelnianie wieloskładnikowe dla Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 043807b2-21db-4d5c-b430-c8a6dee0e6ba
ROBOTS: NOINDEX, NOFOLLOW
description: Uwierzytelnianie wieloskładnikowe (MFA) używa zarówno hasła, które powinno być silne, jak i dodatkowej metody weryfikacji.
ms.openlocfilehash: f939b187fc81381dae4959fdf14280bc839dadb0
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739876"
---
# <a name="multifactor-authentication-for-microsoft-365"></a>Uwierzytelnianie wieloskładnikowe dla Microsoft 365

Hasła są najczęstszą metodą uwierzytelniania logowania na komputerze lub w usłudze online, ale są również najbardziej narażone. Użytkownicy mogą wybierać proste hasła i używać tych samych haseł do wielu logowań na różnych komputerach i usługach.

Aby zapewnić dodatkowy poziom zabezpieczeń dla logowań, należy użyć uwierzytelniania wieloskładnikowego (MFA), które używa zarówno hasła, które powinno być silne, jak i dodatkowej metody weryfikacji opartej na:

- Coś, co masz z tobą, które nie jest łatwo zduplikowane, takie jak smartfon.
- Coś, co masz unikatowo i biologicznie, takie jak odciski palców, twarz lub inny atrybut biometryczny.

Dodatkowa metoda weryfikacji jest stosowana dopiero po zweryfikowaniu hasła użytkownika. W przypadku uwierzytelniania wieloskładnikowego nawet w przypadku naruszenia silnego hasła użytkownika osoba atakująca nie ma telefonu inteligentnego ani odcisku palca, aby ukończyć logowanie.

## <a name="mfa-support-in-microsoft-365"></a>Obsługa uwierzytelniania wieloskładnikowego w Microsoft 365

Domyślnie zarówno Microsoft 365, jak i Office 365 obsługują uwierzytelnianie wieloskładnikowe dla kont użytkowników przy użyciu:

- Wiadomość SMS wysłana na telefon, która wymaga od użytkownika wpisania kodu weryfikacyjnego.
- Rozmowa telefoniczna.
- Aplikacja Microsoft Authenticator telefonu inteligentnego.

W obu przypadkach logowanie uwierzytelniania wieloskładnikowego używa metody "coś, co nie jest łatwo zduplikowane" na potrzeby dodatkowej weryfikacji. Istnieje wiele sposobów włączania uwierzytelniania wieloskładnikowego dla Microsoft 365 i Office 365:

- Z wartościami domyślnymi zabezpieczeń
- Z zasadami dostępu warunkowego
- Dla każdego konta użytkownika (niezalecane)

Te sposoby są oparte na planie Microsoft 365.

|Plan|Zalecenie|Typ klienta|
|---|---|---|
|Wszystkie plany Microsoft 365|Użyj wartości domyślnych zabezpieczeń, które wymagają uwierzytelniania wieloskładnikowego dla wszystkich kont użytkowników. <p> Uwierzytelnianie wieloskładnikowe dla poszczególnych użytkowników można również skonfigurować na poszczególnych kontach użytkowników, ale nie jest to zalecane.|Małe firmy|
|Microsoft 365 Business Premium <p> Microsoft 365 E3 <p> licencje Premium P1 Azure Active Directory (Azure AD)|Użyj [domyślnych zabezpieczeń lub zasad dostępu warunkowego](/microsoft-365/business-premium/m365bp-conditional-access) , aby wymagać uwierzytelniania wieloskładnikowego dla kont użytkowników na podstawie członkostwa w grupach, aplikacji lub innych kryteriów.|Małe firmy do przedsiębiorstwa|
|Microsoft 365 E5 <p> licencje Azure AD — wersja Premium P2|Użyj usługi Azure AD Identity Protection, aby wymagać uwierzytelniania wieloskładnikowego na podstawie kryteriów ryzyka logowania.|Enterprise|
||||

### <a name="security-defaults"></a>Ustawienia domyślne zabezpieczeń

Wartości domyślne zabezpieczeń to nowa funkcja dla subskrypcji Microsoft 365 i Office 365 płatnych lub próbnych utworzonych po 21 października 2019 r. Te subskrypcje mają włączone wartości domyślne zabezpieczeń, które:

- Wymaga, aby wszyscy użytkownicy korzystali z uwierzytelniania wieloskładnikowego z aplikacją Microsoft Authenticator.
- Blokuje starsze uwierzytelnianie.

Użytkownicy mają 14 dni na zarejestrowanie się w usłudze MFA przy użyciu aplikacji Microsoft Authenticator ze swoich smartfonów, co rozpoczyna się od pierwszego zalogowania się po włączeniu ustawień domyślnych zabezpieczeń. Po upływie 14 dni użytkownik nie będzie mógł się zalogować do momentu ukończenia rejestracji usługi MFA.

Ustawienia domyślne zabezpieczeń zapewniają, że wszystkie organizacje mają podstawowy poziom zabezpieczeń logowania użytkownika, który jest domyślnie włączony. Wartości domyślne zabezpieczeń można wyłączyć na korzyść uwierzytelniania wieloskładnikowego z zasadami dostępu warunkowego.

Ustawienia domyślne zabezpieczeń można włączyć lub wyłączyć w okienku **Właściwości** dla Azure AD w Azure Portal.

![Obraz przedstawiający stronę właściwości katalogu.](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Domyślnych zabezpieczeń można używać z dowolnym planem Microsoft 365.

Aby uzyskać więcej informacji, zobacz [omówienie ustawień domyślnych zabezpieczeń](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

Zasady dostępu warunkowego to zestaw reguł określających warunki, w których logowania są oceniane i dozwolone. Można na przykład utworzyć zasady dostępu warunkowego, które stanowią:

- Jeśli nazwa konta użytkownika jest członkiem grupy dla użytkowników, do których przypisano Exchange, użytkownik, hasło, zabezpieczenia, SharePoint lub role administratora globalnego, przed zezwoleniem na dostęp należy wymagać uwierzytelniania wieloskładnikowego.

Te zasady umożliwiają wymaganie uwierzytelniania wieloskładnikowego na podstawie członkostwa w grupie, zamiast próbować skonfigurować indywidualne konta użytkowników dla uwierzytelniania wieloskładnikowego, gdy są przypisane lub nieprzypisane z tych ról administratora.

Możesz również użyć zasad dostępu warunkowego, aby uzyskać bardziej zaawansowane możliwości, takie jak wymaganie uwierzytelniania wieloskładnikowego dla określonych aplikacji lub logowanie ze zgodnego urządzenia, takiego jak laptop z systemem Windows 10.

Zasady dostępu warunkowego można skonfigurować w okienku **Zabezpieczenia** dla Azure AD w Azure Portal.

![Obraz opcji menu dla dostępu warunkowego.](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Zasady dostępu warunkowego można używać z:

- Microsoft 365 Business Premium
- Microsoft 365 E3 i E5
- licencje Azure AD — wersja Premium P1 i Azure AD — wersja Premium P2

W przypadku małych firm z Microsoft 365 Business Premium można łatwo używać zasad dostępu warunkowego, wykonując następujące czynności:

1. Utwórz grupę zawierającą konta użytkowników, które wymagają uwierzytelniania wieloskładnikowego.
2. Włącz zasady **Wymagaj uwierzytelniania wieloskładnikowego dla administratorów globalnych** .
3. Utwórz zasady dostępu warunkowego opartego na grupach z następującymi ustawieniami:
    - Przypisania > Użytkownicy i grupy: nazwa grupy z kroku 1 powyżej.
    - Przypisania > aplikacje lub akcje w chmurze: wszystkie aplikacje w chmurze.
    - Mechanizmy kontroli dostępu > Udzielanie > Udzielanie dostępu > Wymagaj uwierzytelniania wieloskładnikowego.
4. Włącz zasady.
5. Dodaj konto użytkownika do grupy utworzonej w kroku 1 powyżej i przetestuj.
6. Aby wymagać uwierzytelniania wieloskładnikowego dla dodatkowych kont użytkowników, dodaj je do grupy utworzonej w kroku 1.

Te zasady dostępu warunkowego umożliwiają wdrażanie wymagań uwierzytelniania wieloskładnikowego dla użytkowników we własnym tempie.

Przedsiębiorstwa powinny używać [typowych zasad dostępu warunkowego](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) , aby skonfigurować następujące zasady:

- [Wymagaj uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Aby uzyskać więcej informacji, zobacz to [omówienie dostępu warunkowego](/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Ochrona tożsamości w usłudze Azure AD

Za pomocą usługi Azure AD Identity Protection można utworzyć dodatkowe zasady dostępu warunkowego, aby [wymagać uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest średnie lub wysokie](../../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk).

Usługi Azure AD Identity Protection i zasad dostępu warunkowego opartego na ryzyku można używać z następującymi elementami:

- Microsoft 365 E5
- licencje Azure AD — wersja Premium P2

Aby uzyskać więcej informacji, zobacz [omówienie usługi Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

### <a name="legacy-per-user-mfa-not-recommended"></a>Starsza wersja uwierzytelniania wieloskładnikowego dla użytkownika (niezalecana)

Należy używać domyślnych zabezpieczeń lub zasad dostępu warunkowego, aby wymagać uwierzytelniania wieloskładnikowego na potrzeby logowania do konta użytkownika. Jeśli jednak żadna z tych opcji nie może być używana, firma Microsoft zdecydowanie zaleca uwierzytelnianie wieloskładnikowe dla kont użytkowników, które mają role administratora, zwłaszcza rolę administratora globalnego, dla dowolnej subskrypcji rozmiaru.

Uwierzytelnianie wieloskładnikowe dla poszczególnych kont użytkowników jest włączane w okienku <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywni użytkownicy**</a> Centrum administracyjne platformy Microsoft 365.

![Obraz opcji Uwierzytelnianie wieloskładnikowe na stronie Aktywni użytkownicy.](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Po włączeniu przy następnym logowaniu użytkownika zostanie wyświetlony monit o zarejestrowanie się w usłudze MFA oraz wybranie i przetestowanie dodatkowej metody weryfikacji.

### <a name="using-these-methods-together"></a>Używanie tych metod razem

W tej tabeli przedstawiono wyniki włączania uwierzytelniania wieloskładnikowego z ustawieniami domyślnymi zabezpieczeń, zasadami dostępu warunkowego i ustawieniami konta poszczególnych użytkowników.

|*Element*|Włączone|Wyłączona|Pomocnicza metoda uwierzytelniania|
|---|---|---|---|
|**Ustawienia domyślne zabezpieczeń**|Nie można używać zasad dostępu warunkowego|Może używać zasad dostępu warunkowego|aplikacja Microsoft Authenticator|
|**Zasady dostępu warunkowego**|Jeśli są włączone, nie można włączyć wartości domyślnych zabezpieczeń|Jeśli wszystkie są wyłączone, można włączyć ustawienia domyślne zabezpieczeń|Określony przez użytkownika podczas rejestracji uwierzytelniania wieloskładnikowego|
|**Starsza wersja uwierzytelniania wieloskładnikowego dla użytkownika (niezalecana)**|Zastępuje wartości domyślne zabezpieczeń i zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego przy każdym logowaniu|Zastępowane przez wartości domyślne zabezpieczeń i zasady dostępu warunkowego|Określony przez użytkownika podczas rejestracji uwierzytelniania wieloskładnikowego|
||||

Jeśli ustawienia domyślne zabezpieczeń są włączone, podczas następnego logowania wszyscy nowi użytkownicy będą monitować o rejestrację usługi MFA i użycie aplikacji Microsoft Authenticator.

## <a name="ways-to-manage-mfa-settings"></a>Sposoby zarządzania ustawieniami uwierzytelniania wieloskładnikowego

Istnieją dwa sposoby zarządzania ustawieniami uwierzytelniania wieloskładnikowego.

W Azure Portal możesz:

- Włączanie i wyłączanie ustawień domyślnych zabezpieczeń
- Konfigurowanie zasad dostępu warunkowego

W Centrum administracyjne platformy Microsoft 365 można skonfigurować <a href="https://go.microsoft.com/fwlink/p/?linkid=2169174" target="_blank">ustawienia uwierzytelniania</a> wieloskładnikowego dla poszczególnych użytkowników i usługi.

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie uwierzytelniania wieloskładnikowego dla Microsoft 365](set-up-multi-factor-authentication.md)

## <a name="related-content"></a>Zawartość pokrewna

[Włącz uwierzytelnianie wieloskładnikowe](set-up-multi-factor-authentication.md) (wideo)\
[Włączanie uwierzytelniania wieloskładnikowego dla telefonu](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (wideo)