---
title: Zarządzanie uwierzytelnianiem wieloskładnikowym w Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak zarządzać uwierzytelnianiem wieloskładnikowym.
ms.openlocfilehash: 6db13adbce775ea276352b715cf25f0da7324b87
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017725"
---
# <a name="manage-multifactor-authentication-in-microsoft-365-lighthouse"></a>Zarządzanie uwierzytelnianiem wieloskładnikowym w Microsoft 365 Lighthouse

Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA) pomaga chronić dostęp do danych i aplikacji, zapewniając kolejną warstwę zabezpieczeń przy użyciu drugiej formy uwierzytelniania. Karta Uwierzytelnianie wieloskładnikowe zawiera szczegółowe informacje na temat stanu włączania uwierzytelniania wieloskładnikowego w dzierżawach. Wybierz dowolną dzierżawę na liście, aby wyświetlić więcej szczegółów dotyczących tej dzierżawy, w tym jakie zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego zostały już skonfigurowane i którzy użytkownicy nie zarejestrowali się jeszcze w usłudze MFA.

W przypadku klientów małych i średnich firm (SMB) firma Microsoft zaleca włączenie [domyślnych ustawień zabezpieczeń](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) co najmniej. W przypadku bardziej złożonych scenariuszy można skonfigurować określone zasady przy użyciu [dostępu warunkowego](/azure/active-directory/conditional-access/overview) .

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dzierżawa pojawiła się na liście, należy spełnić następujące warunki:

- Dzierżawa klienta musi mieć licencję Azure AD — wersja Premium dla każdego użytkownika. Aby uzyskać więcej informacji o tym, które licencje obsługują uwierzytelnianie wieloskładnikowe, zobacz [Funkcje i licencje dla Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-licensing).

- Dzierżawa klienta musi być aktywna w Microsoft 365 Lighthouse. Aby dowiedzieć się, jak określić, czy dzierżawa jest aktywna, zobacz [Microsoft 365 Lighthouse omówienie listy dzierżaw](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Włączanie uwierzytelniania wieloskładnikowego dla dzierżawy

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Użytkownicy**.

2. Wybierz kartę **Uwierzytelnianie wieloskładnikowe** .

3. Z listy dzierżawy wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Na karcie **Włączanie uwierzytelniania wieloskładnikowego** w obszarze **Uwierzytelnianie wieloskładnikowe z wartościami domyślnymi zabezpieczeń** wybierz pozycję **Włącz wartości domyślne zabezpieczeń**.

5. Wybierz pozycję **Zapisz zmiany**.

Aby włączyć uwierzytelnianie wieloskładnikowe za pośrednictwem dostępu warunkowego, zobacz [Samouczek: zabezpieczanie zdarzeń logowania użytkownika za pomocą Azure AD multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>Powiadamianie użytkowników, którzy nie są zarejestrowani w usłudze MFA

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Użytkownicy**.

2. Wybierz kartę **Uwierzytelnianie wieloskładnikowe** .

3. Z listy dzierżawy wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Na karcie **Użytkownik niezarejestrowany dla uwierzytelniania** wieloskładnikowego wybierz użytkowników, których chcesz powiadomić.

5. Wybierz pozycję **Utwórz wiadomość e-mail**.

Usługa Lighthouse otwiera domyślnego klienta poczty e-mail i wstępnie wypełnia wiadomość e-mail z instrukcjami dotyczącymi rejestracji w usłudze MFA. Wszyscy wybrani użytkownicy zostaną uwzględnieni w wierszu BCC. Jeśli wolisz indywidualnie wysyłać wiadomości e-mail do użytkowników, możesz wybrać ikonę wiadomości e-mail obok nazwy użytkownika.

Jeśli chcesz użyć innego konta e-mail, możesz wyeksportować listę użytkowników do pliku. Możesz również pobrać przykładowe szablony wiadomości e-mail, które można dostosować przy użyciu znakowania firmowego.

## <a name="next-steps"></a>Następne kroki

Po włączeniu uwierzytelniania wieloskładnikowego możesz włączyć samoobsługowe resetowanie haseł Azure Active Directory (Azure AD). Ta funkcja zapewnia użytkownikom możliwość zmiany lub zresetowania hasła bez udziału administratora ani pomocy technicznej. Aby uzyskać więcej informacji, zobacz [Zarządzanie samoobsługowym resetowaniem haseł w Microsoft 365 Lighthouse](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>Zawartość pokrewna

[Planowanie wdrożenia usługi Multi-Factor Authentication Azure Active Directory](/azure/active-directory/authentication/howto-mfa-getstarted) (artykuł)\
[Co to są wartości domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (artykuł)\
[Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) (artykuł)\
[Dowiedz się, jak konwertować użytkowników z uwierzytelniania wieloskładnikowego na użytkownika na dostęp warunkowy](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (artykuł)
