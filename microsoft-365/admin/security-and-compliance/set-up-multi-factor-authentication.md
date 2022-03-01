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
ms.openlocfilehash: 1279220ceb8de5c5fdb4361a258e2c2bfc1f7061
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63026595"
---
# <a name="set-up-multifactor-authentication"></a>Konfigurowanie uwierzytelniania wieloskładnikowego

Uwierzytelnianie wieloskładnikowe oznacza, że Ty i Twoi pracownicy musicie zapewnić więcej niż jeden sposób logowania Microsoft 365 to jeden z najłatwiejszych sposobów zabezpieczenia firmy. W zależności od zrozumienia uwierzytelniania wieloskładnikowego [(MFA)](multi-factor-authentication-microsoft-365.md) i jego obsługi w Microsoft 365 należy je skonfigurować i skonfigurować w twojej organizacji. 

> [!IMPORTANT]
> Jeśli subskrypcja lub wersja próbna została zakupiona po 21 października 2019 r., a podczas logowania jest wyświetlany monit o uwierzytelniania wieloskładnikowego [, dla](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) subskrypcji zostały automatycznie włączone ustawienia domyślne zabezpieczeń.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="watch-turn-on-multifactor-authentication"></a>Obejrzyj: Włączanie uwierzytelniania wieloskładnikowego

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. Przejdź do centrum administracyjne platformy Microsoft 365 stronie <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. Wybierz **pozycję Pokaż wszystko**, a następnie wybierz Azure Active Directory **administracyjne.**
1. Wybierz **Azure Active Directory** **Właściwości,** **Zarządzaj ustawieniami domyślnymi zabezpieczeń**.
1. W **obszarze Domyślne ustawienia włącz zabezpieczenia** wybierz pozycję **Tak,** a następnie pozycję **Zapisz**.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby zarządzać uwierzytelniania wieloskładnikowego, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../add-users/about-admin-roles.md).
- Jeśli włączona jest starsza wersja uwierzytelniania MFA dla uwierzytelniania wieloskładnikowego dla użytkownika, wyłącz starsze uwierzytelniania [MFA dla użytkownika](#turn-off-legacy-per-user-mfa).
- Jeśli masz klientów Office 2013 na Windows, włącz nowoczesne uwierzytelnianie dla klientów z systemem [Office 2013](./enable-modern-authentication.md).
- Zaawansowane: Jeśli masz usługi katalogowe innych firm z usługami federacyjną Active Directory (AD FS), skonfiguruj serwer uwierzytelniania wieloskładnikowego Azure. Aby [uzyskać więcej informacji, zobacz](/azure/active-directory/authentication/howto-mfaserver-nps-vpn) zaawansowane scenariusze z uwierzytelnianiem wieloskładnikowym usługi Azure AD i rozwiązaniami VPN innych firm.

### <a name="turn-off-legacy-per-user-mfa"></a>Wyłączanie starszych uwierzytelniania wieloskładnikowego dla uwierzytelniania wieloskładnikowego dla uwierzytelniania wieloskładnikowego dla uwierzytelniania wielo

Jeśli uwierzytelniania wieloskładnikowego dla  per użytkowników zostało wcześniej włączone, należy je wyłączyć przed włączeniem domyślnych ustawień zabezpieczeń.

1. W okienku centrum administracyjne platformy Microsoft 365 w lewym okienku narracji wybierz pozycję **Aktywni** \> **użytkownicy użytkownicy**.
1. Na stronie **Aktywni użytkownicy** wybierz pozycję **Uwierzytelnianie wieloskładnikowe**.
1. Na stronie uwierzytelnianie wieloskładnikowe zaznacz poszczególnych użytkowników i ustaw dla nich stan uwierzytelniania Wieloskładnikowego na wartość **Wyłączone**.

## <a name="turn-security-defaults-on-or-off"></a>Włączanie lub wyłączanie ustawień domyślnych zabezpieczeń

W większości organizacji ustawienia domyślne zabezpieczeń oferują wysoki poziom dodatkowych zabezpieczeń logowania. Aby uzyskać więcej informacji, zobacz [Co to są wartości domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Jeśli Twoja subskrypcja jest nowa, domyślne ustawienia zabezpieczeń mogą już być włączone automatycznie.

W okienku Właściwości usługi Azure AD można włączyć lub wyłączyć ustawienia domyślne zabezpieczeń w usłudze Azure Active Directory Azure Portal.

1. Zaloguj się [do centrum centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) pomocą poświadczeń administratora globalnego.
2. W lewym obszarzewersji wybierz **pozycję Pokaż wszystko** i w obszarze **Centra administracyjne** wybierz **pozycję Azure Active Directory**.
3. W centrum **Azure Active Directory wybierz** pozycję **Azure Active Directory** \> **Właściwości**.
4. W dolnej części strony wybierz pozycję **Zarządzanie wartościami domyślnymi zabezpieczeń**.
5. Wybierz **pozycję Tak** , aby włączyć ustawienia domyślne zabezpieczeń, lub pozycję **Nie** , aby wyłączyć ustawienia domyślne zabezpieczeń, a następnie wybierz pozycję **Zapisz**.

Jeśli korzystano z podstawowych zasad dostępu warunkowego [, przed](/azure/active-directory/conditional-access/concept-baseline-protection) przejściem do używania ustawień domyślnych zabezpieczeń zostanie wyświetlony monit o ich wyłączenie.

1. Przejdź do strony [Dostęp warunkowy — zasady](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. Wybierz dla każdej zasady planu bazowego wartość **Wł.** , a następnie ustaw **dla opcji Włącz zasady** wartość **Wyłączone**.
3. Przejdź do [strony Azure Active Directory — Właściwości](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. W dolnej części strony wybierz pozycję **Zarządzanie wartościami domyślnymi zabezpieczeń**.
5. Wybierz **pozycję Tak** , aby włączyć ustawienia domyślne zabezpieczeń, lub pozycję **Nie** , aby wyłączyć ustawienia domyślne zabezpieczeń, a następnie wybierz pozycję **Zapisz**.

## <a name="use-conditional-access-policies"></a>Używanie zasad dostępu warunkowego

Jeśli Twoja organizacja ma bardziej szczegółowe potrzeby w zakresie zabezpieczeń logowania, zasady dostępu warunkowego mogą zapewnić Ci większą kontrolę. Dostęp warunkowy umożliwia tworzenie i definiowanie zasad reagowania na zdarzenia logowania i żądania dodatkowych akcji przed udzielonym użytkownikowi dostępu do aplikacji lub usługi.

> [!IMPORTANT]
> Przed włączeniem zasad dostępu warunkowego wyłącz ustawienia domyślne uwierzytelniania wieloskładnikowego dla uwierzytelniania wieloskładnikowego i zabezpieczeń.

Dostęp warunkowy jest dostępny dla klientów, którzy kupili usługę Azure AD — wersja Premium P1, lub licencji, które zawierają tę usługę, na przykład Microsoft 365 Business Premium i Microsoft 365 E3. Aby uzyskać więcej informacji, [zobacz Tworzenie zasad dostępu warunkowego](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

Dostęp warunkowy oparty na czynniku ryzyka jest Azure AD — wersja Premium P2 za pośrednictwem licencji, które zawierają tę licencję, na przykład Microsoft 365 E5. Aby uzyskać więcej informacji, zobacz [Dostęp warunkowy oparty na czynniku ryzyka](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Aby uzyskać więcej informacji na temat usług Azure AD P1 i P2, zobacz ceny [Azure Active Directory usługi](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Włączanie nowoczesnego uwierzytelniania dla organizacji

W przypadku większości subskrypcji nowoczesne uwierzytelnianie jest automatycznie włączone, ale jeśli subskrypcję kupiono przed sierpniem 2017 r., prawdopodobnie konieczne będzie włączenie nowoczesnego uwierzytelniania, aby funkcje takie jak uwierzytelnianie wieloskładnikowe działały w klientach programu Windows, takich jak Outlook.


1. W lewym <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> wybierz pozycję Ustawienia organizacji w lewym **Ustawienia** \> **organizacji**.
2. Na karcie **Usługi** wybierz pozycję **Nowoczesne** uwierzytelnianie i w okienku **Nowoczesne** uwierzytelnianie upewnij się, że jest wybrana opcja **Włącz nowoczesne** uwierzytelnianie. Wybierz **pozycję Save changes (Zapisz zmiany**).


## <a name="next-steps"></a>Następne kroki

- [Jak zarejestrować się w celu zarejestrowania się w celu weryfikacji za pomocą dodatkowej metody weryfikacji](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Co to jest: Uwierzytelnianie wieloskładnikowe](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [Jak się zalogować po rejestracji](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Jak zmienić dodatkową metodę weryfikacji](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie uwierzytelniania wieloskładnikowego](set-up-multi-factor-authentication.md) (wideo)

[Włączanie uwierzytelniania wieloskładnikowego dla telefonu](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
