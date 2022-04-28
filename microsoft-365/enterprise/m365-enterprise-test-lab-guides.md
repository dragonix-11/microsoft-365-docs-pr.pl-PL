---
title: Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/20/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Skorzystaj z tych przewodników po laboratorium testowym, aby skonfigurować środowiska demonstracyjne, weryfikację koncepcji lub środowiska deweloperskie/testowe dla Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 8c4444b599682ad40ebba88b37d83125fccd99f0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097431"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie

*Dotyczy to zarówno Microsoft 365 dla przedsiębiorstw, jak i Office 365 Enterprise.*

Przewodniki po laboratoriach testowych pomagają szybko poznać produkty firmy Microsoft. Zawierają one nakazowe instrukcje dotyczące konfigurowania uproszczonych, ale reprezentatywnych środowisk testowych. Tych środowisk można używać do demonstrowania, dostosowywania lub tworzenia złożonych dowodów koncepcji na czas trwania wersji próbnej lub płatnej subskrypcji.

Grupy TLG zostały zaprojektowane tak, aby były modułowe. Bazują one na sobie na tworzeniu wielu konfiguracji, które dokładniej odpowiadają potrzebom w zakresie konfiguracji uczenia się lub testowania. Praktyczne środowisko "I built it out it out and it works" pomaga zrozumieć wymagania dotyczące wdrażania nowego produktu lub scenariusza, dzięki czemu można lepiej zaplanować hosting w środowisku produkcyjnym.

Za pomocą grup czasu wygaśnięcia można również tworzyć reprezentatywne środowiska do tworzenia i testowania aplikacji, nazywanych również środowiskami deweloperskimi/testowymi.
  
![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

Aby uzyskać wizualną mapę na wszystkie artykuły w stosie Microsoft 365 for enterprise Test Lab Guide, rozwiń poniższą grafikę lub przejdź do [Microsoft 365 dla stosu przewodników laboratorium testowego w przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).

[![Stos przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>Konfiguracja podstawowa

Najpierw utwórz środowisko testowe dla [Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/). Można utworzyć dwa różne typy konfiguracji podstawowych:

- [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md) — ta opcja jest używana, gdy chcesz skonfigurować i zademonstrować Microsoft 365 dla funkcji i możliwości przedsiębiorstwa w środowisku tylko w chmurze, które nie obejmuje żadnych składników lokalnych.

- [Symulowana konfiguracja podstawowa przedsiębiorstwa](simulated-ent-base-configuration-microsoft-365-enterprise.md) — użyj tej funkcji, gdy chcesz skonfigurować i zademonstrować Microsoft 365 dla funkcji i możliwości przedsiębiorstwa w środowisku chmury hybrydowej, które używa składników lokalnych, takich jak domena Active Directory Domain Services (AD DS).

Można również tworzyć środowiska testowe dla Office 365 E5, nie dodając licencji Microsoft 365 E5 do środowiska testowego lub produkcyjnego.
    
## <a name="identity"></a>Tożsamości

Aby zademonstrować funkcje i możliwości związane z tożsamością, zobacz:

- [Synchronizacja skrótów haseł](password-hash-sync-m365-ent-test-environment.md)
  
   Włączanie i testowanie synchronizacji katalogu opartego na skrótach haseł z kontrolera domeny usług AD DS.

- [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md)
  
   Włączanie i testowanie uwierzytelniania przekazywanego do kontrolera domeny usług AD DS.

- [Uwierzytelnianie federacyjne](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   Włączanie i testowanie uwierzytelniania federacyjnego na kontrolerze domeny usług AD DS.

- [Bezproblemowe logowanie jednokrotne w usłudze Microsoft Azure Active Directory](single-sign-on-m365-ent-test-environment.md)
  
   Włączanie i testowanie bezproblemowego logowania jednokrotnego (Seamless SSO) usługi Azure AD za pomocą kontrolera domeny usług AD DS.

- [Uwierzytelnianie wieloskładnikowe](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Włączanie i testowanie uwierzytelniania wieloskładnikowego opartego na telefonie inteligentnym dla określonego konta użytkownika.

- [Ochrona kont administratorów globalnych](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   Zablokuj konta administratorów globalnych przy użyciu zasad dostępu warunkowego.

- [Zapisanie zwrotne haseł](password-writeback-m365-ent-test-environment.md)

   Użyj funkcji zapisywania zwrotnego haseł, aby zmienić hasło na koncie użytkownika usług AD DS z usługi Azure AD.

- [Resetowanie haseł](password-reset-m365-ent-test-environment.md)

   Użyj samoobsługowego resetowania hasła, aby zresetować hasło.

- [Automatyczne licencjonowanie i członkostwo w grupach](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Ułatwianie administrowania nowymi kontami za pomocą automatycznego licencjonowania i dynamicznego członkostwa w grupach.

- [Ochrona tożsamości w usłudze Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Przeskanuj bieżące konta użytkowników pod kątem luk w zabezpieczeniach.

- [Dostęp do tożsamość i urządzeń](identity-device-access-m365-test-environment.md)

   Utwórz środowisko do testowania zalecanych konfiguracji tożsamości i dostępu urządzeń oraz zasad dostępu warunkowego.

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi

Aby zademonstrować funkcje i możliwości związane z zarządzaniem urządzeniami przenośnymi, zobacz:

- [Zasady zgodności urządzeń](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Utwórz grupę użytkowników i zasady zgodności urządzeń dla urządzeń Windows 10.
    
- [Rejestrowanie urządzeń z systemem iOS i Android](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   Zarejestruj urządzenia z systemem iOS lub Android i zarządzaj nimi zdalnie.

## <a name="information-protection"></a>Ochrona informacji

Aby zademonstrować funkcje i możliwości związane z ochroną informacji, zobacz:

- [Zwiększone zabezpieczenia na platformie Microsoft 365](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Skonfiguruj ustawienia dla zwiększonych zabezpieczeń Microsoft 365 i zbadaj wbudowane narzędzia zabezpieczeń.
  
- [Klasyfikacja danych](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   Skonfiguruj i zastosuj etykiety do dokumentu w witrynie zespołu usługi SharePoint Online.
    
- [Privileged Access Management](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Skonfiguruj zarządzanie dostępem uprzywilejowanym na potrzeby dostępu just in time do zadań z podwyższonym poziomem uprawnień i uprzywilejowanych w organizacji.