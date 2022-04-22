---
title: Zarządzanie samoobsługowym resetowaniem haseł w Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak zarządzać samoobsługowym resetowaniem haseł.
ms.openlocfilehash: 4d618eb80dfd4a37ad5548de997b3d551bcbbf85
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022366"
---
# <a name="manage-self-service-password-reset-in-microsoft-365-lighthouse"></a>Zarządzanie samoobsługowym resetowaniem haseł w Microsoft 365 Lighthouse

Microsoft 365 Lighthouse umożliwia partnerom zarządzanie samoobsługowym resetowaniem haseł Azure Active Directory (Azure AD). Samoobsługowe resetowanie hasła daje użytkownikom możliwość zmiany lub zresetowania hasła bez udziału administratora ani pomocy technicznej. Jeśli konto użytkownika jest zablokowane lub nie pamięta hasła, może postępować zgodnie z monitami, aby się odblokować i wrócić do pracy. Ta możliwość zmniejsza liczbę wywołań pomocy technicznej i utratę produktywności, gdy użytkownik nie może zalogować się do swojego urządzenia lub aplikacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dzierżawa pojawiła się na liście, należy spełnić następujące warunki:

- Dzierżawa klienta musi mieć licencję Azure AD — wersja Premium dla każdego użytkownika. Aby uzyskać więcej informacji o tym, które licencje obsługują [samoobsługowe resetowanie hasła, zobacz Wymagania licencyjne dotyczące Azure Active Directory samoobsługowego resetowania haseł](/azure/active-directory/authentication/concept-sspr-licensing).

- Dzierżawa klienta musi być aktywna w aplikacji Lighthouse. Aby dowiedzieć się, jak określić, czy dzierżawa jest aktywna, zobacz [Omówienie strony Windows 365 (komputery w chmurze) w Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>Wyświetlanie stanu dzierżawy samoobsługowego resetowania hasła

1. W okienku nawigacji po lewej stronie aplikacji Lighthouse wybierz pozycję **Użytkownicy**.

2. Wybierz kartę **Resetowanie hasła** .

Karta Resetowanie hasła zawiera omówienie dzierżaw, które włączyły samoobsługowe resetowanie hasła za pomocą zalecanych ustawień, liczbę użytkowników, którzy nie zarejestrowali się na potrzeby samoobsługowego resetowania hasła, oraz szczegółowy podział według dzierżawy postępu wdrażania samoobsługowego resetowania haseł w zarządzanych organizacjach.

## <a name="enable-sspr-for-a-tenant"></a>Włączanie samoobsługowego resetowania hasła dla dzierżawy

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Użytkownicy**.

2. Wybierz kartę **Resetowanie hasła** .

3. Z listy dzierżaw wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Wybierz pozycję **Edytuj ustawienia samoobsługowego resetowania hasła w Azure Active Directory**, aby przejść do Azure Active Directory (Azure AD).

5. W usłudze Azure AD włącz samoobsługowe resetowanie hasła dla wszystkich lub wybranych użytkowników. Aby dowiedzieć się więcej, zobacz [Samouczek: włączanie użytkownikom odblokowywania konta lub resetowania haseł przy użyciu Azure Active Directory samoobsługowego resetowania haseł](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Powiadamianie użytkowników o zarejestrowaniu się na potrzeby samoobsługowego resetowania hasła

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Użytkownicy**.

2. Wybierz kartę **Resetowanie hasła** .

3. Z listy dzierżaw wybierz dzierżawę, aby otworzyć okienko szczegółów.

4. Wybierz użytkowników, których chcesz powiadomić.

5. Wybierz pozycję **Utwórz wiadomość e-mail**.

Usługa Lighthouse otwiera domyślnego klienta poczty e-mail i wstępnie wypełnia wiadomość e-mail z instrukcjami rejestracji na potrzeby samoobsługowego resetowania hasła. Wszyscy wybrani użytkownicy zostaną uwzględnieni w wierszu BCC. Jeśli wolisz indywidualnie wysyłać wiadomości e-mail do użytkowników, możesz wybrać ikonę wiadomości e-mail obok nazwy użytkownika.

Jeśli chcesz użyć innego konta e-mail, możesz wyeksportować listę użytkowników do pliku. Możesz również pobrać przykładowe szablony wiadomości e-mail, które można dostosować przy użyciu znakowania firmowego.

## <a name="related-content"></a>Zawartość pokrewna

[Planowanie wdrożenia samoobsługowego resetowania haseł Azure Active Directory](/azure/active-directory/authentication/howto-sspr-deployment) (artykuł)\
[Samouczek: umożliwianie użytkownikom odblokowywania konta lub resetowania haseł przy użyciu Azure Active Directory samoobsługowego resetowania haseł](/azure/active-directory/authentication/tutorial-enable-sspr) (artykuł)\
[Jak włączyć i skonfigurować samoobsługowe resetowanie hasła w usłudze Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (wideo)\
[Zarządzanie uwierzytelnianiem wieloskładnikowym w Microsoft 365 Lighthouse](m365-lighthouse-manage-mfa.md) (artykuł)
