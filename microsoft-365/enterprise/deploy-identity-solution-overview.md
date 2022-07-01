---
title: Wdrażanie infrastruktury tożsamości dla platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-overview
ms.custom:
- intro-overview
description: Wdrażanie infrastruktury tożsamości dla platformy Microsoft 365.
ms.openlocfilehash: 9f0956b0c131fb4cf90ce462fcfca0b9e124578e
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603687"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>Wdrażanie infrastruktury tożsamości dla platformy Microsoft 365

W usłudze Microsoft 365 dla przedsiębiorstw dobrze zaplanowana i wykonana infrastruktura tożsamości toruje drogę do zwiększenia bezpieczeństwa, w tym ograniczania dostępu do obciążeń produktywności i ich danych tylko uwierzytelnionym użytkownikom i urządzeniom. Zabezpieczenia tożsamości to kluczowy element wdrożenia Zero Trust, w którym wszystkie próby uzyskania dostępu do zasobów zarówno lokalnych, jak i w chmurze są uwierzytelniane i autoryzowane.

Aby uzyskać informacje na temat funkcji tożsamości każdej usługi Microsoft 365 dla przedsiębiorstw, roli usługi Azure Active Directory (Azure AD), składników lokalnych i chmurowych oraz najbardziej typowych konfiguracji uwierzytelniania, zobacz [plakat Infrastruktura tożsamości](../downloads/m365e-identity-infra.pdf).

[![Plakat Infrastruktura tożsamości.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Przejrzyj ten dwustronicowy plakat, aby szybko zapoznać się z koncepcjami i konfiguracjami tożsamości dla platformy Microsoft 365 dla przedsiębiorstw.

Możesz [pobrać ten plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) i wydrukować go w formacie literowym, prawnym lub tabloidowym (11 x 17).

To rozwiązanie jest pierwszym krokiem do utworzenia stosu wdrażania Zero Trust platformy Microsoft 365.

![Stos wdrażania Zero Trust platformy Microsoft 365](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

Aby uzyskać więcej informacji, zobacz [plan wdrożenia usługi Microsoft 365 Zero Trust](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>Co jest w tym rozwiązaniu

To rozwiązanie umożliwia wdrożenie infrastruktury tożsamości dla dzierżawy usługi Microsoft 365 w celu zapewnienia dostępu pracownikom i ochrony przed atakami opartymi na tożsamościach.

![Wdrażanie infrastruktury tożsamości dla platformy Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

Kroki opisane w tym rozwiązaniu są następujące:

1. [Określanie modelu tożsamości.](deploy-identity-solution-identity-model.md)
2. [Ochrona kont uprzywilejowanych platformy Microsoft 365.](protect-your-global-administrator-accounts.md)
3. [Ochrona kont użytkowników platformy Microsoft 365.](microsoft-365-secure-sign-in.md)
4. [Wdróż model tożsamości.](cloud-only-identities.md)

To rozwiązanie obsługuje kluczowe zasady [Zero Trust](https://www.microsoft.com/security/business/zero-trust/):

- **Weryfikuj jawnie:** Zawsze uwierzytelniaj się i autoryzuj na podstawie wszystkich dostępnych punktów danych.
- **Użyj dostępu z najniższymi uprawnieniami:** Ogranicz dostęp użytkowników za pomocą funkcji just in time i just-enough-access (JIT/JEA), zasad adaptacyjnych opartych na ryzyku i ochrony danych.
- **Załóżmy, że naruszenie:** Minimalizuj promień wybuchu i dostęp do segmentu. Zweryfikuj kompleksowe szyfrowanie i użyj analizy, aby uzyskać widoczność, zwiększyć wykrywanie zagrożeń i ulepszyć ochronę.

W przeciwieństwie do konwencjonalnego dostępu do intranetu, który ufa wszystkim za zaporą organizacji, Zero Trust traktuje każde logowanie i dostęp tak, jakby pochodziło z niekontrolowanej sieci, czy to za zaporą organizacji, czy z Internetu. Zero Trust wymaga ochrony sieci, infrastruktury, tożsamości, punktów końcowych, aplikacji i danych.

## <a name="microsoft-365-capabilities-and-features"></a>Możliwości i funkcje platformy Microsoft 365

Azure AD zapewnia pełny zestaw funkcji zarządzania tożsamościami i zabezpieczeń dla dzierżawy platformy Microsoft 365.

|Możliwość lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|[Uwierzytelnianie wieloskładnikowe (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|Uwierzytelnianie wieloskładnikowe wymaga od użytkowników podania dwóch form weryfikacji, takich jak hasło użytkownika oraz powiadomienie z aplikacji Microsoft Authenticator lub połączenie telefoniczne. Uwierzytelnianie wieloskładnikowe znacznie zmniejsza ryzyko użycia skradzionych poświadczeń w celu uzyskania dostępu do środowiska. Platforma Microsoft 365 używa usługi Azure AD Multi-Factor Authentication do logowania opartego na uwierzytelnianiu wieloskładnikowym.|Microsoft 365 E3 lub E5|
|[Dostęp warunkowy](/azure/active-directory/conditional-access/overview)|Azure AD ocenia warunki logowania użytkownika i używa zasad dostępu warunkowego do określenia dozwolonego dostępu. Na przykład w tych wskazówkach przedstawiono sposób tworzenia zasad dostępu warunkowego w celu wymagania zgodności urządzeń w celu uzyskania dostępu do poufnych danych. Znacznie zmniejsza to ryzyko, że haker z własnym urządzeniem i skradzionymi poświadczeniami będzie mógł uzyskać dostęp do poufnych danych. Chroni również poufne dane na urządzeniach, ponieważ urządzenia muszą spełniać określone wymagania dotyczące kondycji i zabezpieczeń.|Microsoft 365 E3 lub E5|
|[grupy Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups)|Zasady dostępu warunkowego, zarządzanie urządzeniami z Intune, a nawet uprawnienia do plików i witryn w organizacji zależą od przypisania do kont użytkowników lub grup Azure AD. Zalecamy utworzenie grup Azure AD, które odpowiadają zaimplementowaniu poziomów ochrony. Na przykład pracownicy kadry kierowniczej są prawdopodobnie celami o wyższej wartości dla hakerów. Dlatego warto dodać konta użytkowników tych pracowników do grupy Azure AD i przypisać tę grupę do zasad dostępu warunkowego i innych zasad, które wymuszają wyższy poziom ochrony dostępu.|Microsoft 365 E3 lub E5|
|[Ochrona tożsamości w usłudze Azure AD](/azure/active-directory/identity-protection/overview)|Umożliwia wykrywanie potencjalnych luk w zabezpieczeniach wpływających na tożsamości organizacji i konfigurowanie zasad zautomatyzowanego korygowania na potrzeby niskiego, średniego i wysokiego ryzyka logowania oraz ryzyka związanego z użytkownikiem. Te wskazówki opierają się na tej ocenie ryzyka w celu zastosowania zasad dostępu warunkowego na potrzeby uwierzytelniania wieloskładnikowego. Te wskazówki obejmują również zasady dostępu warunkowego, które wymagają od użytkowników zmiany hasła w przypadku wykrycia działania wysokiego ryzyka dla konta.|Microsoft 365 E5, Microsoft 365 E3 z dodatkiem E5 Security, licencjami EMS E5 lub Azure AD — wersja Premium P2|
|[Samodzielne resetowanie hasła (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Zezwalaj użytkownikom na bezpieczne resetowanie haseł i bez interwencji pomocy technicznej, zapewniając weryfikację wielu metod uwierzytelniania, które może kontrolować administrator.|Microsoft 365 E3 lub E5|
|[Azure AD ochrony hasłem](/azure/active-directory/authentication/concept-password-ban-bad)|Wykrywanie i blokowanie znanych słabych haseł oraz ich wariantów oraz dodatkowych słabych terminów specyficznych dla Organizacji. Domyślne globalne listy zakazanych haseł są automatycznie stosowane do wszystkich użytkowników w dzierżawie Azure AD. Dodatkowe wpisy można zdefiniować na niestandardowej liście zakazanych haseł. Gdy użytkownicy zmieniają lub resetują swoje hasła, te listy zakazanych haseł są sprawdzane w celu wymuszenia użycia silnych haseł.|Microsoft 365 E3 lub E5|
|

## <a name="next-steps"></a>Następne kroki

Wykonaj następujące kroki, aby wdrożyć model tożsamości i infrastrukturę uwierzytelniania dla dzierżawy platformy Microsoft 365:

1. [Określanie modelu tożsamości w chmurze.](deploy-identity-solution-identity-model.md)
2. [Ochrona kont uprzywilejowanych platformy Microsoft 365.](protect-your-global-administrator-accounts.md)
3. [Ochrona kont użytkowników platformy Microsoft 365.](microsoft-365-secure-sign-in.md)
4. Wdrażanie modelu tożsamości w chmurze: [tylko w chmurze](cloud-only-identities.md) lub [hybrydowo](prepare-for-directory-synchronization.md).

[![Określanie modelu tożsamości do użycia dla dzierżawy platformy Microsoft 365](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Dodatkowe zasoby tożsamości w chmurze firmy Microsoft

### <a name="manage"></a>Zarządzanie

Aby zarządzać wdrożeniem tożsamości w chmurze firmy Microsoft, zobacz:

- [Konta użytkowników](manage-microsoft-365-accounts.md)
- [Licencje](assign-licenses-to-user-accounts.md)
- [Hasła](manage-microsoft-365-passwords.md)
- [Grupy](manage-microsoft-365-groups.md)
- [Nadzór](manage-microsoft-365-identity-governance.md)
- [Synchronizacja katalogów](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Jak firma Microsoft robi tożsamość dla platformy Microsoft 365

Dowiedz się, jak eksperci IT w firmie Microsoft [zarządzają tożsamościami i bezpiecznym dostępem](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>Ten zasób IT Showcase jest dostępny tylko w języku angielskim.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Jak firma Contoso zrobiła tożsamość dla platformy Microsoft 365

Aby zapoznać się z przykładem sposobu, w jaki fikcyjna, ale reprezentatywna międzynarodowa organizacja wdrożyła infrastrukturę tożsamości hybrydowej dla usług w chmurze Platformy Microsoft 365, zobacz [Identity for the Contoso Corporation (Tożsamość dla firmy Contoso Corporation](contoso-identity.md)).

<!--

## Plan

To plan for your identity implementation:

- [Understand the different identity models](about-microsoft-365-identity.md)
- [Plan for hybrid identity and directory synchronization](plan-for-directory-synchronization.md)

## Deploy

To deploy your identity implementation:

- [Protect your global administrator accounts](protect-your-global-administrator-accounts.md)
- [Configure and use cloud-only identities](cloud-only-identities.md)
- [Configure and use hybrid identities](prepare-for-directory-synchronization.md)
- [Set up directory synchronization](set-up-directory-synchronization.md)
- If needed, deploy [hybrid identity scenarios](hybrid-solutions.md)

### Identity and device access recommendations

To help ensure a secure and productive workforce, Microsoft provides a set of recommendations for [identity and device access](../security/office-365-security/microsoft-365-policies-configurations.md). For identity, use the recommendations and settings in these articles:

- [Prerequisites](../security/office-365-security/identity-access-prerequisites.md)
- [Common identity and device access policies](../security/office-365-security/identity-access-policies.md)

--> 
