---
title: Włączanie domyślnych ustawień zabezpieczeń dla Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Dowiedz się, jak domyślne ustawienia zabezpieczeń pomagają chronić twoją organizację przed atakami związanymi z tożsamością, udostępniając wstępnie skonfigurowane ustawienia zabezpieczeń dla Microsoft 365 Business Premium.
ms.openlocfilehash: dfd0d3edff541d828b70d383641aaf66c93826b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705140"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>Włączanie domyślnych ustawień zabezpieczeń dla Microsoft 365 Business Premium

Wartości domyślne zabezpieczeń pomagają chronić twoją organizację przed atakami związanymi z tożsamością, udostępniając wstępnie skonfigurowane ustawienia zabezpieczeń, które firma Microsoft zarządza w imieniu Twojej organizacji. Te ustawienia obejmują włączanie uwierzytelniania wieloskładnikowego (MFA) dla wszystkich administratorów i kont użytkowników. W większości organizacji ustawienia domyślne zabezpieczeń oferują wysoki poziom dodatkowych zabezpieczeń logowania.

Aby uzyskać więcej informacji o domyślnych ustawieniach zabezpieczeń i zasadach, które wymuszają, zobacz Co [to są domyślne ustawienia zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Jeśli Twoja subskrypcja została utworzona 22 października 2019 r. lub później,&mdash; być może automatycznie włączono dla Ciebie domyślne ustawienia zabezpieczeń.

Aby włączyć domyślne ustawienia zabezpieczeń w usłudze Azure Active Directory (Azure AD) lub sprawdzić, czy są już włączone:

1. Zaloguj się <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">do centrum centrum administracyjne platformy Microsoft 365</a> zabezpieczeń, administratorem dostępu warunkowego lub poświadczeń administratora globalnego.

2. W okienku po lewej stronie wybierz pozycję **Pokaż wszystko, a** następnie w obszarze **Centra** administracyjne wybierz pozycję **Azure Active Directory**.

3. W lewym okienku Azure Active Directory **administracyjnego wybierz** pozycję **Azure Active Directory**.

4. Z menu po lewej stronie pulpitu nawigacyjnego w sekcji **Zarządzanie** wybierz pozycję **Właściwości**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Zrzut ekranu przedstawiający Azure Active Directory administracyjnego z lokalizacją elementu menu Właściwości.":::

5. U dołu strony **Właściwości** wybierz pozycję **Zarządzaj ustawieniami domyślnymi zabezpieczeń**.

6. W prawym okienku zobaczysz ustawienie **domyślne Włącz zabezpieczenia** . Jeśli **wybrano** pozycję Tak, domyślne ustawienia zabezpieczeń są już włączone i nie są wymagane żadne dalsze działania. Jeśli domyślne ustawienia zabezpieczeń nie są obecnie włączone, wybierz pozycję **Tak** , aby je włączyć, a następnie wybierz pozycję **Zapisz**.

> [!NOTE]
> Jeśli korzystasz z zasad dostępu warunkowego, musisz je wyłączyć przed użyciem ustawień domyślnych zabezpieczeń.
>
> Można używać ustawień domyślnych zabezpieczeń lub zasad dostępu warunkowego, ale nie można używać ich jednocześnie.

## <a name="consider-using-conditional-access"></a>Rozważ użycie dostępu warunkowego

Jeśli Twoja organizacja ma złożone wymagania dotyczące zabezpieczeń lub potrzebujesz bardziej szczegółowej kontroli nad zasadami zabezpieczeń, rozważ korzystanie z dostępu warunkowego zamiast domyślnych ustawień zabezpieczeń, aby zapewnić podobną lub wyższą pozycję zabezpieczeń. 

Dostęp warunkowy pozwala tworzyć i definiować zasady reagowania na zdarzenia logowania i żądać dodatkowych działań przed udzielonym użytkownikowi dostępu do aplikacji lub usługi. Zasady dostępu warunkowego mogą być szczegółowe i szczegółowe, co umożliwia użytkownikom wydajną pracę w każdym miejscu i w dowolnym momencie, a także chronienie organizacji.

Ustawienia domyślne zabezpieczeń są dostępne dla wszystkich klientów, natomiast dostęp warunkowy wymaga licencji dla jednego z następujących planów:

- Azure Active Directory — wersja Premium P1 lub P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 lub E5
- Enterprise Mobility & Security E3 lub E5

Jeśli chcesz używać dostępu warunkowego do konfigurowania zasad podobnych do tych włączonych domyślnie przez zabezpieczenia, skorzystaj z następujących przewodników krok po kroku:

- [Wymaganie uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Wymaganie uwierzytelniania wieloskładnikowego do zarządzania platformą Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Wymaganie uwierzytelniania WIELOSKŁADNIKOWEGO dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Wymaganie rejestracji uwierzytelniania wieloskładnikowego usługi Azure AD —](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) wymaga usługi Azure AD Identity Protection, która jest częścią Azure Active Directory — wersja Premium P2

Aby dowiedzieć się więcej o dostępie warunkowym, zobacz [Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) Aby uzyskać więcej informacji na temat tworzenia zasad dostępu warunkowego, [zobacz Tworzenie zasad dostępu warunkowego](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Jeśli masz plan lub licencję, która zapewnia dostęp warunkowy, ale nie zostały jeszcze utworzone żadne zasady dostępu warunkowego, możesz korzystać z ustawień domyślnych zabezpieczeń. Zanim jednak będzie można używać zasad dostępu warunkowego, należy wyłączyć ustawienia domyślne zabezpieczeń.
