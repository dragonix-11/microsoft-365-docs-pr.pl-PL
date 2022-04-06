---
title: Wyświetlanie ryzykownych użytkowników i zarządzanie nimi
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
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse dowiedz się, jak wyświetlać ryzykownych użytkowników i zarządzać nimi.
ms.openlocfilehash: 708fc0576c85d9b8511ac6b31ed0398fae1b20d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704920"
---
# <a name="view-and-manage-risky-users"></a>Wyświetlanie ryzykownych użytkowników i zarządzanie nimi

Firma Microsoft zbiera i analizuje informacje o sygnałach logowania użytkownika każdego dnia. Sygnały te są używane do tworzenia dobrych wzorców logowania użytkownika i identyfikowania potencjalnych ryzykownych prób logowania. Azure Active Directory (Azure AD) Identity Protection używa tych sygnałów do przeglądania prób logowania użytkownika i podejmować działania w przypadku podejrzanych aktywności.

Microsoft 365 Lighthouse pomaga zarządzać ryzykiem wykrytym przez usługę Azure AD Identity Protection, udostępniając jeden widok ryzykownych użytkowników we wszystkich dzierżawach zarządzanych. Możesz szybko zabezpieczyć ryzykownych użytkowników, resetując ich hasła lub blokując ich możliwość logowania się do ich Microsoft 365 konta. Możesz także wyświetlać szczegółowe informacje, aby lepiej zrozumieć ryzyko użytkownika i określić kolejne kroki.

W usłudze Azure AD Identity Protection są identyfikowane czynniki ryzyka związane z wieloma typami, między innymi:

- Wyciekły poświadczenia
- Anonimowe użycie adresu IP
- Podróżtypowa
- Logowanie się na zainfekowanych urządzeniach
- Logowanie się z adresów IP z podejrzanymi działaniami
- Logowanie się z nieznanych lokalizacji

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby użytkownicy znajdowali się na liście ryzykownych użytkowników, muszą zostać spełnione następujące warunki:

- Dzierżawa klienta musi mieć licencję Azure AD — wersja Premium dla każdego użytkownika. Aby uzyskać więcej informacji na temat licencji, które obsługują usługę Azure AD Identity Protection, zobacz [Co to jest ochrona tożsamości?](/azure/active-directory/identity-protection/overview-identity-protection)

- Dzierżawa klienta musi być aktywna w Microsoft 365 Lighthouse. Aby sprawdzić, czy dzierżawa jest aktywna, zobacz [omówienie Microsoft 365 Lighthouse dzierżaw.](m365-lighthouse-tenant-list-overview.md)

## <a name="review-detected-risks-and-take-action"></a>Przeglądanie wykrytych zagrożeń i działania

W usłudze Azure AD Identity Protection wykrywanie ryzyka obejmuje wszelkie zidentyfikowane podejrzane działania związane z kontami użytkowników w usłudze Azure AD.

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Użytkownicy**.

2. Wybierz **kartę Ryzykowni** użytkownicy.

3. Przejrzyj listę użytkowników w przypadku **zagrożenia.**

4. Wybierz **pozycję Wyświetl wykrywanie ryzyka,** aby uzyskać szczegółowe informacje o ryzyku wykrytym dla każdego użytkownika. Aby uzyskać więcej informacji na temat typów ryzyka i wykrywania, zobacz [Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. Dla każdego użytkownika oceń wykrywanie ryzyka i wybierz jedną z następujących akcji, odpowiednio do potrzeb:

    - Resetowanie hasła — zmienianie lub resetowanie hasła użytkownika.

    - Blokowanie logowania — uniemożliwia innym użytkownikom logowanie się jako ten użytkownik.

    - Potwierdź naruszonego użytkownika — ustaw stan ryzyka na naruszony.

    - Odrzuć ryzyko użytkownika — ustaw stan ryzyka jako odrzucony.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Działanie na wielu kontach użytkowników jednocześnie

Aby podjąć działania dotyczące wielu użytkowników jednocześnie:

1. Na karcie **Ryzykowni** użytkownicy wybierz zestaw użytkowników, dla których chcesz podjąć działanie.

2. Wybierz jedną z następujących akcji do wykonania:

    - Resetuj hasło

    - Blokowanie logowania

    - Potwierdź użytkownikom, których bezpieczeństwo zostało naruszone

    - Odrzucenie ryzyka użytkownika

> [!NOTE]
> Jeśli zarządzana organizacja ma licencję Azure AD — wersja Premium P2, zalecamy włączenie zasad dostępu warunkowego opartych na czynniku ryzyka użytkownika. Aby uzyskać więcej informacji, zobacz [Dostęp warunkowy: Dostęp warunkowy oparty na czynniku ryzyka użytkownika](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Zawartość pokrewna
[Samouczek: Używanie wykrywania ryzyka w przypadku logowania](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) użytkowników do wyzwalania uwierzytelniania wieloskładnikowego usługi Azure AD lub zmian haseł (artykuł)\
[Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (article) \
[Rozwiązywanie problemów związanych z zagrożeniami i odblokowywanie użytkowników](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (artykuł)
