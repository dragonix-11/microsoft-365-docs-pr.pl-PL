---
title: Podgląd i zarządzanie użytkownikami stwarzającymi zagrożenie
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak wyświetlać ryzykownych użytkowników i zarządzać nimi.
ms.openlocfilehash: 0b7567404b909927a80b69184299baae131f8eb7
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824273"
---
# <a name="view-and-manage-risky-users"></a>Podgląd i zarządzanie użytkownikami stwarzającymi zagrożenie

Firma Microsoft zbiera i analizuje biliony sygnałów logowania użytkowników każdego dnia. Te sygnały służą do tworzenia dobrych wzorców zachowania logowania użytkowników i identyfikowania potencjalnych ryzykownych prób logowania. Azure Active Directory (Azure AD) Identity Protection używa tych sygnałów do przeglądania prób logowania użytkowników i podejmowania działań w przypadku wystąpienia podejrzanych działań.

Microsoft 365 Lighthouse pomaga zarządzać ryzykiem wykrytym przez usługę Azure AD Identity Protection, zapewniając pojedynczy widok ryzykownych użytkowników we wszystkich zarządzanych dzierżawach. Możesz szybko zabezpieczyć ryzykownych użytkowników, resetując ich hasło lub blokując im logowanie się do konta Microsoft 365. Możesz również wyświetlić szczegółowe informacje, aby lepiej zrozumieć ryzyko użytkownika i określić kolejne kroki.

Usługa Azure AD Identity Protection identyfikuje zagrożenia wielu typów, w tym:

- Wyciek poświadczeń
- Użycie anonimowego adresu IP
- Nietypowe podróże
- Logowanie z zainfekowanych urządzeń
- Logowanie z adresów IP przy użyciu podejrzanych działań
- Logowanie z nieznanych lokalizacji

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby użytkownicy mogli pojawić się na liście ryzykownych użytkowników, należy spełnić następujące warunki:

- Dzierżawa klienta musi mieć licencję Azure AD — wersja Premium dla każdego użytkownika. Aby uzyskać więcej informacji o tym, które licencje obsługują usługę Azure AD Identity Protection, zobacz [Co to jest usługa Identity Protection?](/azure/active-directory/identity-protection/overview-identity-protection)

- Dzierżawa klienta musi być aktywna w Microsoft 365 Lighthouse. Aby ustalić, czy dzierżawa jest aktywna, zobacz [omówienie strony Microsoft 365 Lighthouse Dzierżawy](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Przejrzyj wykryte zagrożenia i podejmij działania

W usłudze Azure AD Identity Protection wykrywanie ryzyka obejmuje wszelkie zidentyfikowane podejrzane akcje związane z kontami użytkowników w usłudze Azure AD.

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Użytkownicy**.

2. Wybierz kartę **Ryzykowni użytkownicy** .

3. Przejrzyj użytkowników na liście ze stanem ryzyka **Zagrożony**.

4. Wybierz pozycję **Wyświetl wykrywanie ryzyka** , aby uzyskać szczegółowe informacje na temat zagrożeń wykrytych dla każdego użytkownika. Aby uzyskać więcej informacji na temat typów ryzyka i wykrywania, zobacz [Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. Dla każdego użytkownika oceń wykrycia ryzyka i wybierz jedną z następujących akcji, odpowiednio:

    - Resetowanie hasła — zmień lub zresetuj hasło użytkownika.

    - Blokuj logowanie — uniemożliwiaj użytkownikom logowanie się jako ten użytkownik.

    - Potwierdź naruszenie zabezpieczeń przez użytkownika — ustaw stan ryzyka na potwierdzoną naruszenie zabezpieczeń.

    - Odrzuć ryzyko użytkownika — ustaw stan ryzyka na odrzucony.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Jednoczesne podjęcie akcji na wielu kontach użytkowników

Aby jednocześnie podjąć działania wobec wielu użytkowników, których dotyczy problem:

1. Na karcie **Ryzykowni użytkownicy** wybierz zestaw użytkowników, dla którzy chcesz podjąć akcję.

2. Wybierz jedną z następujących akcji do wykonania:

    - Resetuj hasło

    - Blokuj logowanie

    - Potwierdzanie naruszenia zabezpieczeń przez użytkownika

    - Odrzucanie ryzyka użytkownika

> [!NOTE]
> Jeśli organizacja, którą zarządzasz, ma licencję Azure AD — wersja Premium P2, zaleca się włączenie zasad dostępu warunkowego opartego na ryzyku użytkownika. Aby uzyskać więcej informacji, zobacz [Dostęp warunkowy: Dostęp warunkowy oparty na ryzyku użytkownika](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Zawartość pokrewna
[Samouczek: używanie wykrywania ryzyka dla logowań użytkowników w celu wyzwolenia usługi Azure AD Multi-Factor Authentication lub zmian haseł](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) (artykuł)\
[Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (artykuł) \
[Korygowanie ryzyka i odblokowywanie użytkowników](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (artykuł)
