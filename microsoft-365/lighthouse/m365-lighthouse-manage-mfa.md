---
title: Zarządzanie uwierzytelnianiem wieloskładnikowym
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się, jak zarządzać uwierzytelnianiem wieloskładnikowym.
ms.openlocfilehash: 5ab430e464fb2d20f9a911818f9fd6cb077d849e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326135"
---
# <a name="manage-multifactor-authentication"></a>Zarządzanie uwierzytelnianiem wieloskładnikowym

Azure Active Directory (Azure AD) uwierzytelnianie wieloskładnikowe (MFA) pomaga chronić dostęp do danych i aplikacji, zapewniając kolejną warstwę zabezpieczeń przy użyciu drugiej formy uwierzytelniania. Karta Uwierzytelnianie wieloskładnikowe zawiera szczegółowe informacje o stanie włączania uwierzytelniania wieloskładnikowego w dzierżawach. Wybierz dowolną dzierżawę na liście, aby wyświetlić więcej szczegółów dotyczących tej dzierżawy, w tym zasady dostępu warunkowego wymagające uwierzytelniania MFA, które użytkownicy nie zarejestrowali się jeszcze w celu uwierzytelniania MFA.

W przypadku klientów o małych i średnich firmach (SMB) firma Microsoft zaleca co najmniej włączenie [](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) ustawień domyślnych zabezpieczeń. W bardziej złożonych scenariuszach możesz użyć dostępu [warunkowego w](/azure/active-directory/conditional-access/overview) celu skonfigurowania określonych zasad.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dzierżawa pojawiła się na liście, muszą zostać spełnione następujące warunki:

- Dzierżawa klienta musi mieć licencję Azure AD — wersja Premium dla każdego użytkownika. Aby uzyskać więcej informacji o tym, które licencje obsługują uwierzytelnianie wieloskładnikowe, zobacz Funkcje i [licencje usługi Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-licensing).

- Dzierżawa klienta musi być aktywna w Microsoft 365 Lighthouse. Aby dowiedzieć się, jak ustalić, czy dzierżawa jest aktywna, zobacz Microsoft 365 Lighthouse [omówienie listy dzierżaw](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Włączanie uwierzytelniania wieloskładnikowego dla dzierżawy

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Użytkownicy**.

2. Wybierz **kartę Uwierzytelnianie wieloskładnikowe** .

3. Z listy dzierżaw wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Na karcie **Włączanie uwierzytelniania wieloskładnikowego** w obszarze **Uwierzytelniania wieloskładnikowego** z ustawieniami domyślnymi zabezpieczeń wybierz **pozycję Włącz domyślne ustawienia zabezpieczeń**.

5. Wybierz **pozycję Zapisz zmiany**.

Aby włączyć uwierzytelnianie wieloskładnikowe za pośrednictwem dostępu warunkowego, zobacz [Samouczek: zabezpieczanie zdarzeń logowania użytkownika za pomocą usługi Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>Powiadamianie użytkowników, którzy nie są zarejestrowani w ramach uwierzytelniania MFA

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Użytkownicy**.

2. Wybierz **kartę Uwierzytelnianie wieloskładnikowe** .

3. Z listy dzierżaw wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Na karcie **Użytkownik, który nie został zarejestrowany w celu uwierzytelniania MFA** wybierz użytkowników, których chcesz powiadomić.

5. Wybierz pozycję **Utwórz wiadomość e-mail**.

Lighthouse otwiera domyślnego klienta poczty e-mail i wstępnie zasypuje wiadomość e-mail instrukcjami dotyczącymi zarejestrowania się w celu uwierzytelniania wieloskładnikowego. Wszyscy wybrani użytkownicy zostaną uwzględnioni w wierszu UDW. Jeśli wolisz wysyłać wiadomości e-mail do poszczególnych użytkowników, możesz wybrać ikonę wiadomości e-mail obok nazwy użytkownika.

Jeśli chcesz użyć innego konta e-mail, możesz wyeksportować listę użytkowników do pliku. Możesz również pobrać przykładowe szablony wiadomości e-mail, które możesz dostosować za pomocą  marki firmy.

## <a name="next-steps"></a>Następne kroki

Po włączeniu uwierzytelniania wieloskładnikowego możesz włączyć funkcję samodzielnego Azure Active Directory (Azure AD). Ta funkcja umożliwia użytkownikom zmienianie lub resetowanie haseł bez angażowania pracowników pomocy technicznej. Aby uzyskać więcej informacji, zobacz [Zarządzanie samodzielnego resetowania hasła](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>Zawartość pokrewna

[Planowanie Azure Active Directory usługi Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-getstarted) (artykuł)\
[Co to są ustawienia domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (artykuł)\
[Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) (artykuł)\
[Dowiedz się, jak przekonwertować użytkowników z uwierzytelniania MFA na](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) dostęp warunkowy (artykuł)
