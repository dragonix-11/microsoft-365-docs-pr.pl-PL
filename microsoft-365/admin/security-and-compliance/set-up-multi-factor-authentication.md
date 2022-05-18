---
title: Konfigurowanie uwierzytelniania wieloskładnikowego dla użytkowników
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: Dowiedz się, jak skonfigurować uwierzytelnianie wieloskładnikowe dla organizacji.
monikerRange: o365-worldwide
ms.openlocfilehash: c37e9126b7cf06929ca9c97533cddf19d1b71f6e
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468969"
---
# <a name="set-up-multifactor-authentication-for-microsoft-365"></a>Konfigurowanie uwierzytelniania wieloskładnikowego dla Microsoft 365

Uwierzytelnianie wieloskładnikowe oznacza, że Ty i Twoi pracownicy muszą zapewnić więcej niż jeden sposób logowania się do Microsoft 365 jest jednym z najprostszych sposobów zabezpieczenia firmy. Na podstawie zrozumienia [uwierzytelniania wieloskładnikowego (MFA) i jego obsługi w Microsoft 365](multi-factor-authentication-microsoft-365.md) nadszedł czas, aby go skonfigurować i wdrożyć w organizacji. 

> [!IMPORTANT]
> Jeśli subskrypcja lub wersja próbna została zakupiona po 21 października 2019 r., a po zalogowaniu zostanie wyświetlony monit o uwierzytelnianie [wieloskładnikowe, domyślne ustawienia zabezpieczeń](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) zostały automatycznie włączone dla Twojej subskrypcji.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy uzyskujecie całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm w miarę rozwoju firmy — od dołączania do codziennego użytku.

## <a name="watch-turn-on-multifactor-authentication"></a>Obejrzyj: Włączanie uwierzytelniania wieloskładnikowego

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. Przejdź do Centrum administracyjne platformy Microsoft 365 pod adresem <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. Wybierz pozycję **Pokaż wszystko**, a następnie wybierz **centrum administracyjne Azure Active Directory**.
1. Wybierz **pozycję Azure Active Directory**, **Właściwości**, **Zarządzaj wartościami domyślnymi zabezpieczeń**.
1. W obszarze **Włącz ustawienia domyślne zabezpieczeń** wybierz pozycję **Tak** , a następnie **pozycję Zapisz**.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby zarządzać uwierzytelnianiem wieloskładnikowym, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../add-users/about-admin-roles.md).
- Jeśli masz włączoną starszą usługę MFA dla poszczególnych użytkowników, [wyłącz starszą uwierzytelnianie wieloskładnikowe dla poszczególnych użytkowników](#turn-off-legacy-per-user-mfa).
- Jeśli masz Office klientów 2013 na urządzeniach Windows, [włącz nowoczesne uwierzytelnianie dla klientów Office 2013](./enable-modern-authentication.md).
- Zaawansowane: jeśli masz usługi katalogowe innych firm z usługami Active Directory Federation Services (AD FS), skonfiguruj serwer usługi Azure MFA. Aby uzyskać więcej informacji, zobacz [zaawansowane scenariusze z uwierzytelnianiem wieloskładnikowym Azure AD i rozwiązaniami sieci VPN innych firm](/azure/active-directory/authentication/howto-mfaserver-nps-vpn).

### <a name="turn-off-legacy-per-user-mfa"></a>Wyłączanie starszej wersji uwierzytelniania wieloskładnikowego dla poszczególnych użytkowników

Jeśli usługa MFA dla poszczególnych użytkowników została wcześniej włączona, należy ją wyłączyć przed włączeniem ustawień domyślnych zabezpieczeń.

1. W Centrum administracyjne platformy Microsoft 365 w lewym pasku nawigacyjnym wybierz pozycję **Użytkownicy** \> **aktywni użytkownicy**.
1. Na stronie **Aktywni użytkownicy** wybierz pozycję **Uwierzytelnianie wieloskładnikowe**.
1. Na stronie uwierzytelniania wieloskładnikowego wybierz każdego użytkownika i ustaw jego stan uwierzytelniania wieloskładnikowego na **wartość Wyłączone**.

## <a name="turn-security-defaults-on-or-off"></a>Włączanie lub wyłączanie ustawień domyślnych zabezpieczeń

W przypadku większości organizacji ustawienia domyślne zabezpieczeń oferują dobry poziom dodatkowych zabezpieczeń logowania. Aby uzyskać więcej informacji, zobacz [Co to są wartości domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Jeśli twoja subskrypcja jest nowa, ustawienia domyślne zabezpieczeń mogą być już włączone automatycznie.

Ustawienia domyślne zabezpieczeń można włączyć lub wyłączyć w okienku **Właściwości** dla Azure Active Directory (Azure AD) w Azure Portal.

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń administratora globalnego.
2. W lewym okienku nawigacji wybierz pozycję **Pokaż wszystko** i w obszarze **Centra administracyjne** wybierz **pozycję Azure Active Directory**.
3. W **centrum administracyjnym Azure Active Directory** wybierz **pozycję właściwości Azure Active Directory**\>.
4. W dolnej części strony wybierz pozycję **Zarządzanie wartościami domyślnymi zabezpieczeń**.
5. Wybierz pozycję **Tak** , aby włączyć ustawienia domyślne zabezpieczeń lub **Nie** , aby wyłączyć wartości domyślne zabezpieczeń, a następnie wybierz pozycję **Zapisz**.

Jeśli używasz [podstawowych zasad dostępu warunkowego](/azure/active-directory/conditional-access/concept-baseline-protection), przed przejściem do korzystania z ustawień domyślnych zabezpieczeń zostanie wyświetlony monit o ich wyłączenie.

1. Przejdź do [strony Dostęp warunkowy — zasady](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. Wybierz każdą zasadę punktu odniesienia, która jest **włączona** , i ustaw opcję **Włącz zasady** na **Wartość Wyłączona**.
3. Przejdź do [strony Azure Active Directory — Właściwości](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. W dolnej części strony wybierz pozycję **Zarządzanie wartościami domyślnymi zabezpieczeń**.
5. Wybierz pozycję **Tak** , aby włączyć ustawienia domyślne zabezpieczeń i **Nie** , aby wyłączyć wartości domyślne zabezpieczeń, a następnie wybierz pozycję **Zapisz**.

## <a name="use-conditional-access-policies"></a>Korzystanie z zasad dostępu warunkowego

Jeśli Twoja organizacja ma bardziej szczegółowe potrzeby w zakresie zabezpieczeń logowania, zasady dostępu warunkowego mogą oferować większą kontrolę. Dostęp warunkowy umożliwia tworzenie i definiowanie zasad, które reagują na zdarzenia logowania i żądają dodatkowych akcji przed udzieleniem użytkownikowi dostępu do aplikacji lub usługi.

> [!IMPORTANT]
> Przed włączeniem zasad dostępu warunkowego wyłącz wartości domyślne uwierzytelniania wieloskładnikowego dla poszczególnych użytkowników i zabezpieczeń.

Dostęp warunkowy jest dostępny dla klientów, którzy zakupili Azure AD — wersja Premium P1 lub licencje, które obejmują ten dostęp, takie jak Microsoft 365 Business Premium i Microsoft 365 E3. Aby uzyskać więcej informacji, zobacz [tworzenie zasad dostępu warunkowego](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

Dostęp warunkowy oparty na ryzyku jest dostępny za pośrednictwem licencji Azure AD — wersja Premium P2 lub licencji, które to obejmują, takich jak Microsoft 365 E5. Aby uzyskać więcej informacji, zobacz [Dostęp warunkowy oparty na ryzyku](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Aby uzyskać więcej informacji na temat Azure AD P1 i P2, zobacz [cennik Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Włączanie nowoczesnego uwierzytelniania dla organizacji

W przypadku większości subskrypcji nowoczesne uwierzytelnianie jest automatycznie włączone, ale jeśli subskrypcja została zakupiona przed sierpniem 2017 r., prawdopodobnie trzeba będzie włączyć nowoczesne uwierzytelnianie, aby uzyskać funkcje, takie jak Uwierzytelnianie wieloskładnikowe, aby działały w Windows klientów, takich jak Outlook.


1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> w lewym pasku nawigacyjnym wybierz **pozycję Ustawienia** \> **Ustawienia organizacji**.
2. Na karcie **Usługi** wybierz pozycję **Nowoczesne uwierzytelnianie**, a następnie w okienku **Nowoczesne uwierzytelnianie** upewnij się, że wybrano pozycję **Włącz nowoczesne uwierzytelnianie** . Wybierz **pozycję Zapisz zmiany**.


## <a name="next-steps"></a>Następne kroki

- [Jak zarejestrować się, aby uzyskać dodatkową metodę weryfikacji](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Co to jest: Uwierzytelnianie wieloskładnikowe](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [Jak zalogować się po rejestracji](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Jak zmienić dodatkową metodę weryfikacji](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie uwierzytelniania wieloskładnikowego](set-up-multi-factor-authentication.md) (wideo)

[Włączanie uwierzytelniania wieloskładnikowego dla telefonu](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
