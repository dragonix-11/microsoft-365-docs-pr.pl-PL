---
title: Krok nr 3. Ochrona tożsamości
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: oprogramowanie wymuszające okup, oprogramowanie wymuszające okup obsługiwane przez człowieka, oprogramowanie wymuszające okup przez człowieka, humor, ataki wymuszające okup, ataki oprogramowania wymuszającego okup, szyfrowanie, kryptografia, zerowe zaufanie
description: Korzystaj z bezpiecznych logowania i dostępu warunkowego, aby chronić zasoby Microsoft 365 przed atakami oprogramowania wymuszającego okup.
ms.openlocfilehash: 548e0649d7180ef39f693049210a91c1e0dce312
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320231"
---
# <a name="step-3-protect-identities"></a>Krok nr 3. Ochrona tożsamości

Poniższe sekcje chronią organizację przed naruszeniami zabezpieczeń poświadczeń, który zazwyczaj jest pierwszym etapem większego ataku oprogramowania wymuszającego okup.

## <a name="increase-sign-in-security"></a>Zwiększanie zabezpieczeń logowania

[Uwierzytelnianie bez użycia hasła](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) dla kont użytkowników w usłudze Azure Active Directory (Azure AD).

W przypadku kont użytkowników, które nadal korzystają z tych kont, podczas przechodzenia na uwierzytelnianie bez uwierzytelnianie hasłem:

- Blokuj znane słabe i niestandardowe hasła za pomocą [usługi Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad).
- Rozszerzenie blokowania znanych słabych i niestandardowych haseł na twoje lokalne hasła [Usługi domenowe w usłudze Active Directory (AD DS) za pomocą usługi Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).
- Zezwalaj użytkownikom na zmienianie swoich haseł za pomocą samodzielnego resetowania hasła [(SSPR).](/azure/active-directory/authentication/concept-sspr-howitworks)

Następnie implementuj [zasady wspólnej tożsamości i dostępu do urządzeń](/microsoft-365/security/office-365-security/identity-access-policies). Te zasady zapewniają wyższy poziom bezpieczeństwa dostępu do Microsoft 365 usług w chmurze. 

W przypadku logowania użytkowników są następujące zasady:

- Wymaganie uwierzytelniania wieloskładnikowego (MFA) dla kont [priorytetowych (](/microsoft-365/admin/setup/priority-accounts) natychmiast) i ostatecznie wszystkich kont użytkowników.
- Korzystanie z uwierzytelniania wieloskładnikowego wymaga logowania wysokiego ryzyka.
- Zmienianie haseł przez użytkowników o wysokim poziomie ryzyka z logowaniem o wysokim poziomie ryzyka.

## <a name="prevent-privilege-escalation"></a>Zapobieganie eskalacji uprawnień

Skorzystaj z tych najlepszych rozwiązań:

- Implementuj zasadę [](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) najmniejszych uprawnień i używaj ochrony hasłem zgodnie [](#increase-sign-in-security) z opisem w zwiększanie zabezpieczeń logowania dla tych kont użytkowników, które nadal używają haseł do ich logowania. 
- Unikaj korzystania z kont usług na poziomie administratora w całej domenie. 
- Ograniczanie lokalnych uprawnień administracyjnych w celu ograniczenia instalowania trojańskich sieci trojańskich (RAT) i innych niepożądanych aplikacji.
- Użyj dostępu warunkowego usługi Azure AD, aby jawnie zweryfikować zaufanie użytkowników i stacji roboczych przed zezwoleniem na dostęp do portali administracyjnych. Zobacz [ten przykład dla](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management) portalu Azure Portal.
- Włącz zarządzanie hasłami administratora lokalnego.
- Określ, gdzie są logowania i ujawniane poświadczenia dla kont o wysokim poziomie uprawnień. Konta o wysokim poziomie uprawnień nie powinny być obecne na stanowiskach roboczych.
- Wyłącz lokalny magazyn haseł i poświadczeń.

## <a name="impact-on-users-and-change-management"></a>Wpływ na użytkowników i zarządzanie zmianami

Należy upewnić się, że użytkownicy w organizacji wiedzą o:

- Nowe wymagania dotyczące silniejszego hasła.
- Zmiany w procesach logowania, na przykład wymagane użycie uwierzytelniania wieloskładnikowego i rejestracja pomocniczej metody uwierzytelniania MFA.
- Korzystanie z konserwacji haseł z programem SSPR. Na przykład koniec z telefonami pomocy technicznej w celu zresetowania hasła.
- Monit o wymaganie uwierzytelniania MFA lub zmiany hasła dla logowania, które są określone jako ryzykowne.

## <a name="resulting-configuration"></a>Wynikowa konfiguracja

Oto ochrona przed oprogramowaniem wymuszającym okup dla Twojej dzierżawy w krokach od 1 do 3.

![Ochrona przed oprogramowaniem wymuszającym okup dla Microsoft 365 dzierżawy po kroku 3](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step3.png)

## <a name="next-step"></a>Następny krok

[![Krok 4 ochrony przed oprogramowaniem wymuszającym okup przy użyciu Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step4.png)](ransomware-protection-microsoft-365-devices.md)

Przejdź do [kroku 4,](ransomware-protection-microsoft-365-devices.md) aby chronić urządzenia (punkty końcowe) w Microsoft 365 dzierżawie. 
