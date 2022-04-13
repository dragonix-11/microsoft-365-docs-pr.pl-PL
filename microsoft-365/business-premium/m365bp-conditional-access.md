---
title: Włączanie ustawień domyślnych zabezpieczeń dla Microsoft 365 Business Premium
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
description: Dowiedz się, jak ustawienia domyślne zabezpieczeń mogą pomóc chronić organizację przed atakami związanymi z tożsamością, udostępniając wstępnie skonfigurowane ustawienia zabezpieczeń dla Microsoft 365 Business Premium.
ms.openlocfilehash: 58477da3d44844c763dff95d35fc71753afc7ce2
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824515"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>Włączanie ustawień domyślnych zabezpieczeń dla Microsoft 365 Business Premium

Ustawienia domyślne zabezpieczeń pomagają chronić organizację przed atakami związanymi z tożsamością, udostępniając wstępnie skonfigurowane ustawienia zabezpieczeń zarządzane przez firmę Microsoft w imieniu organizacji. Te ustawienia obejmują włączanie uwierzytelniania wieloskładnikowego dla wszystkich administratorów i kont użytkowników. W przypadku większości organizacji wartości domyślne zabezpieczeń oferują dobry poziom dodatkowych zabezpieczeń logowania.

Aby uzyskać więcej informacji na temat ustawień domyślnych zabezpieczeń i wymuszanych przez nie zasad, zobacz [Co to są wartości domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Jeśli subskrypcja została utworzona w dniu 22 października 2019 r. lub później, ustawienia domyślne zabezpieczeń mogły zostać automatycznie włączone, jeśli chcesz&mdash; sprawdzić ustawienia w celu potwierdzenia.

Aby włączyć wartości domyślne zabezpieczeń w Azure Active Directory (Azure AD) lub sprawdzić, czy są już włączone:

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> przy użyciu poświadczeń administratora zabezpieczeń, administratora dostępu warunkowego lub administratora globalnego.

2. W okienku po lewej stronie wybierz pozycję **Pokaż wszystko,** a następnie w obszarze **Centra administracyjne** wybierz pozycję **Azure Active Directory**.

3. W lewym okienku **centrum administracyjnego Azure Active Directory** wybierz pozycję **Azure Active Directory**.

4. W menu po lewej stronie pulpitu nawigacyjnego w sekcji **Zarządzanie** wybierz pozycję **Właściwości**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Zrzut ekranu centrum administracyjnego Azure Active Directory przedstawiający lokalizację elementu menu Właściwości.":::

5. W dolnej części strony **Właściwości** wybierz pozycję **Zarządzaj wartościami domyślnymi zabezpieczeń**.

6. W okienku po prawej stronie zostanie wyświetlone ustawienie **Włącz ustawienia domyślne zabezpieczeń** . Jeśli **wybrano** opcję Tak, wartości domyślne zabezpieczeń są już włączone i nie są wymagane żadne dalsze działania. Jeśli ustawienia domyślne zabezpieczeń nie są obecnie włączone, wybierz pozycję **Tak** , aby je włączyć, a następnie wybierz pozycję **Zapisz**.

> [!NOTE]
> Jeśli używasz zasad dostępu warunkowego, musisz je wyłączyć przed użyciem ustawień domyślnych zabezpieczeń.
>
> Możesz użyć domyślnych zabezpieczeń lub zasad dostępu warunkowego, ale nie możesz jednocześnie używać obu tych zasad.

## <a name="consider-using-conditional-access"></a>Rozważ użycie dostępu warunkowego

Jeśli Twoja organizacja ma złożone wymagania dotyczące zabezpieczeń lub potrzebujesz bardziej szczegółowej kontroli nad zasadami zabezpieczeń, rozważ użycie dostępu warunkowego zamiast ustawień domyślnych zabezpieczeń, aby uzyskać podobną lub wyższą postawę zabezpieczeń. 

Dostęp warunkowy umożliwia tworzenie i definiowanie zasad, które reagują na zdarzenia logowania i żądają dodatkowych akcji przed udzieleniem użytkownikowi dostępu do aplikacji lub usługi. Zasady dostępu warunkowego mogą być szczegółowe i specyficzne, dzięki czemu użytkownicy mogą pracować wydajnie wszędzie i wszędzie, ale także chronić organizację.

Ustawienia domyślne zabezpieczeń są dostępne dla wszystkich klientów, podczas gdy dostęp warunkowy wymaga licencji dla jednego z następujących planów:

- Azure Active Directory — wersja Premium P1 lub P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 lub E5
- Enterprise Mobility & Security E3 lub E5

Jeśli chcesz użyć dostępu warunkowego do konfigurowania zasad równoważnych zasadom włączonym domyślnie przez zabezpieczenia, zapoznaj się z następującymi przewodnikami krok po kroku:

- [Wymagaj uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)

- [Wymaganie uwierzytelniania wieloskładnikowego na potrzeby zarządzania platformą Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)

- [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

- [Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)

- [Wymagaj rejestracji usługi Azure AD MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) — wymaga usługi Azure AD Identity Protection, która jest częścią Azure Active Directory — wersja Premium P2

Aby dowiedzieć się więcej na temat dostępu warunkowego, zobacz [Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) Aby uzyskać więcej informacji na temat tworzenia zasad dostępu warunkowego, zobacz [Tworzenie zasad dostępu warunkowego](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Jeśli masz plan lub licencję, która zapewnia dostęp warunkowy, ale nie utworzono jeszcze żadnych zasad dostępu warunkowego, możesz użyć wartości domyślnych zabezpieczeń. Jednak przed użyciem zasad dostępu warunkowego należy wyłączyć wartości domyślne zabezpieczeń.
