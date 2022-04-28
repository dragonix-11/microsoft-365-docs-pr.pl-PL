---
title: Ustawienia domyślne zabezpieczeń i dostęp warunkowy
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
ms.openlocfilehash: af9b19dcf33f1b79d4057662cf759ace27aec38f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095273"
---
# <a name="security-defaults-and-multi-factor-authentication"></a>Ustawienia domyślne zabezpieczeń i uwierzytelnianie wieloskładnikowe

Microsoft 365 Business Premium została zaprojektowana w celu ochrony kont użytkowników firmy przy użyciu wstępnie skonfigurowanych ustawień zabezpieczeń. Te ustawienia obejmują włączanie uwierzytelniania wieloskładnikowego dla wszystkich administratorów i kont użytkowników. W przypadku większości organizacji wartości domyślne zabezpieczeń zapewniają dobry poziom zabezpieczeń logowania.

Aby uzyskać więcej informacji na temat ustawień domyślnych zabezpieczeń i wymuszanych przez nie zasad, zobacz [Co to są wartości domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Ten artykuł zawiera informacje o:

- [Ustawienia domyślne zabezpieczeń](#security-defaults) (odpowiednie dla większości firm)
- [Dostęp warunkowy](#conditional-access) (dla firm z bardziej rygorystycznymi wymaganiami dotyczącymi zabezpieczeń)

> [!NOTE]
> Jeśli używasz zasad dostępu warunkowego, musisz je wyłączyć przed użyciem ustawień domyślnych zabezpieczeń. Możesz użyć domyślnych zabezpieczeń lub zasad dostępu warunkowego, ale nie możesz jednocześnie używać obu tych zasad.

## <a name="security-defaults"></a>Ustawienia domyślne zabezpieczeń

Ustawienia domyślne zabezpieczeń zostały zaprojektowane tak, aby ułatwić ochronę kont użytkowników firmy od samego początku. Po włączeniu ustawienia domyślne zabezpieczeń zapewniają bezpieczne ustawienia domyślne, które pomagają zapewnić bezpieczeństwo twojej firmy:

- Wymaganie od wszystkich użytkowników i administratorów zarejestrowania się na potrzeby uwierzytelniania wieloskładnikowego przy użyciu aplikacji Microsoft Authenticator.
- Wyzwanie dla użytkowników korzystających z uwierzytelniania wieloskładnikowego, głównie wtedy, gdy pojawiają się na nowym urządzeniu lub w aplikacji, ale częściej w przypadku ról i zadań krytycznych.
- Wyłączanie uwierzytelniania ze starszych klientów uwierzytelniania, którzy nie mogą wykonywać uwierzytelniania wieloskładnikowego.
- Ochrona administratorów przez wymaganie dodatkowego uwierzytelniania za każdym razem, gdy się logują.

Uwierzytelnianie wieloskładnikowe to ważny pierwszy krok w zabezpieczaniu firmy, a ustawienia domyślne zabezpieczeń ułatwiają implementowanie uwierzytelniania wieloskładnikowego. Jeśli subskrypcja została utworzona w dniu 22 października 2019 r. lub później, ustawienia domyślne zabezpieczeń mogły zostać automatycznie włączone, jeśli chcesz&mdash; sprawdzić ustawienia w celu potwierdzenia.

> [!TIP]
> Aby uzyskać więcej informacji na temat ustawień domyślnych zabezpieczeń i wymuszanych przez nie zasad, zobacz [Co to są wartości domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

### <a name="to-enable-security-defaults-or-confirm-theyre-already-enabled"></a>Aby włączyć wartości domyślne zabezpieczeń (lub potwierdzić, że są już włączone)

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> przy użyciu poświadczeń administratora zabezpieczeń, administratora dostępu warunkowego lub administratora globalnego.

2. W okienku po lewej stronie wybierz pozycję **Pokaż wszystko,** a następnie w obszarze **Centra administracyjne** wybierz pozycję **Azure Active Directory**.

3. W lewym okienku **centrum administracyjnego Azure Active Directory** wybierz pozycję **Azure Active Directory**.

4. W menu po lewej stronie pulpitu nawigacyjnego w sekcji **Zarządzanie** wybierz pozycję **Właściwości**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Zrzut ekranu centrum administracyjnego Azure Active Directory przedstawiający lokalizację elementu menu Właściwości.":::

5. W dolnej części strony **Właściwości** wybierz pozycję **Zarządzaj wartościami domyślnymi zabezpieczeń**.

6. W okienku po prawej stronie zostanie wyświetlone ustawienie **Włącz ustawienia domyślne zabezpieczeń** . Jeśli **wybrano** opcję Tak, wartości domyślne zabezpieczeń są już włączone i nie są wymagane żadne dalsze działania. Jeśli ustawienia domyślne zabezpieczeń nie są obecnie włączone, wybierz pozycję **Tak** , aby je włączyć, a następnie wybierz pozycję **Zapisz**.

## <a name="conditional-access"></a>Dostęp warunkowy

> [!NOTE]
> Jeśli używasz ustawień domyślnych zabezpieczeń, musisz je wyłączyć przed użyciem dostępu warunkowego. Możesz użyć domyślnych zabezpieczeń lub zasad dostępu warunkowego, ale nie możesz jednocześnie używać obu tych zasad.

Jeśli Twoja firma lub firma ma złożone wymagania dotyczące zabezpieczeń lub potrzebujesz bardziej szczegółowej kontroli nad zasadami zabezpieczeń, rozważ użycie dostępu warunkowego zamiast domyślnych zabezpieczeń, aby uzyskać podobną lub wyższą postawę zabezpieczeń.

Dostęp warunkowy umożliwia tworzenie i definiowanie zasad, które reagują na zdarzenia logowania i żądają dodatkowych akcji przed udzieleniem użytkownikowi dostępu do aplikacji lub usługi. Zasady dostępu warunkowego mogą być szczegółowe i specyficzne, dzięki czemu użytkownicy mogą pracować wydajnie wszędzie i wszędzie, ale także chronić organizację.

Ustawienia domyślne zabezpieczeń są dostępne dla wszystkich klientów, podczas gdy dostęp warunkowy wymaga jednego z następujących planów:

- Azure Active Directory — wersja Premium P1 lub P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 lub E5
- Enterprise Mobility & Security E3 lub E5

Jeśli chcesz skonfigurować zasady przy użyciu dostępu warunkowego, zapoznaj się z następującymi przewodnikami krok po kroku:

- [Wymagaj uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Wymaganie uwierzytelniania wieloskładnikowego na potrzeby zarządzania platformą Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Wymagaj rejestracji usługi Azure AD MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) — wymaga usługi Azure AD Identity Protection, która jest częścią Azure Active Directory — wersja Premium P2

Aby dowiedzieć się więcej na temat dostępu warunkowego, zobacz [Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) Aby uzyskać więcej informacji na temat tworzenia zasad dostępu warunkowego, zobacz [Tworzenie zasad dostępu warunkowego](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Jeśli masz plan lub licencję, która zapewnia dostęp warunkowy, ale nie utworzono jeszcze żadnych zasad dostępu warunkowego, możesz użyć wartości domyślnych zabezpieczeń. Jednak przed użyciem zasad dostępu warunkowego należy wyłączyć wartości domyślne zabezpieczeń.

## <a name="next-objective"></a>Następny cel

Skonfiguruj sposoby [ochrony przed złośliwym oprogramowaniem i innymi zagrożeniami](m365bp-increase-protection.md).

