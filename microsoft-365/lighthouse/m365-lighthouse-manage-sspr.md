---
title: Zarządzanie samodzielnego resetowania hasła
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się, jak zarządzać samodzielnego resetowania hasła.
ms.openlocfilehash: b8367d2ed2c088d56425b08c6da5dfd55fcd84b8
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2021
ms.locfileid: "63007058"
---
# <a name="manage-self-service-password-reset"></a>Zarządzanie samodzielnego resetowania hasła

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse umożliwia partnerom samodzielne Azure Active Directory (Azure AD) samodzielne resetowanie hasła (SSPR). Program SSPR umożliwia użytkownikom zmienianie lub resetowanie haseł bez angażowania pracowników pomocy technicznej. Jeśli konto użytkownika jest zablokowane lub zapomni hasło, może po wyświetleniu monitu odblokować użytkownika i wrócić do pracy. Ta możliwość zmniejsza liczbę rozmów przez pomoc do działu obsługi technicznej i utratę produktywności, gdy użytkownik nie może zalogować się na swoim urządzeniu lub w aplikacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dzierżawa pojawiła się na liście, muszą zostać spełnione następujące warunki:

- Dzierżawa klienta musi mieć licencję Azure AD — wersja Premium dla każdego użytkownika. Aby uzyskać więcej informacji o tym, które licencje obsługują usługę SSPR, zobacz Wymagania Azure Active Directory [samodzielnego resetowania hasła](/azure/active-directory/authentication/concept-sspr-licensing).

- Dzierżawa klienta musi być aktywna w latarni morskiej. Aby dowiedzieć się, jak ustalić, czy dzierżawa jest aktywna, zobacz omówienie [Microsoft 365 Lighthouse dzierżaw.](m365-lighthouse-tenants-page-overview.md)

## <a name="view-sspr-tenant-status"></a>Wyświetlanie stanu dzierżawy SSPR

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Użytkownicy**.

2. Wybierz **kartę Resetowanie** hasła.

Karta Resetowanie hasła zawiera omówienie dzierżaw, dla których włączono usługę SSPR, za pomocą zalecanych ustawień, liczby użytkowników, którzy nie zarejestrowały się w usługach SSPR, oraz szczegółowe zestawienie postępów wdrażania usług SSPR według dzierżawy w organizacjach, które zarządzasz.

## <a name="enable-sspr-for-a-tenant"></a>Włączanie usług SSPR dla dzierżawy

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Użytkownicy**.

2. Wybierz **kartę Resetowanie** hasła.

3. Z listy dzierżaw wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Wybierz **pozycję Edytuj ustawienia SSPR w programie Azure Active Directory**, aby przejść do usługi Azure Active Directory (Azure AD).

5. W usłudze Azure AD włącz usługę SSPR dla wszystkich lub wybranych użytkowników. Aby dowiedzieć się więcej, zobacz Samouczek: umożliwianie użytkownikom odblokowania konta lub resetowania haseł za [Azure Active Directory funkcji samodzielnego resetowania hasła](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Powiadamianie użytkowników o rejestracji WSPR

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Użytkownicy**.

2. Wybierz **kartę Resetowanie** hasła.

3. Z listy dzierżaw wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Wybierz użytkowników, których chcesz powiadomić.

5. Wybierz pozycję **Utwórz wiadomość e-mail**.

Lighthouse otwiera domyślnego klienta poczty e-mail i wstępnie zasypuje wiadomość e-mail instrukcjami, aby zarejestrować się w usługach SSPR. Wszyscy wybrani użytkownicy zostaną uwzględnioni w wierszu UDW. Jeśli wolisz wysyłać wiadomości e-mail do poszczególnych użytkowników, możesz wybrać ikonę wiadomości e-mail obok nazwy użytkownika.

Jeśli chcesz użyć innego konta e-mail, możesz wyeksportować listę użytkowników do pliku. Możesz również pobrać przykładowe szablony wiadomości e-mail, które możesz dostosować za pomocą  marki firmy.

## <a name="related-content"></a>Zawartość pokrewna

[Planowanie Azure Active Directory samodzielnego](/azure/active-directory/authentication/howto-sspr-deployment) resetowania hasła (artykuł)\
[Samouczek: umożliwianie użytkownikom odblokowywania konta i resetowania haseł za Azure Active Directory samodzielnego](/azure/active-directory/authentication/tutorial-enable-sspr) resetowania hasła (artykuł)\
[Jak włączyć i skonfigurować usługę SSPR w usłudze Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (klip wideo)\
[Zarządzanie uwierzytelnianiem wieloskładnikowym](m365-lighthouse-manage-mfa.md) (artykuł)
