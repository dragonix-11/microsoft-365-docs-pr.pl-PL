---
title: Wdrażanie infrastruktury tożsamości na Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-scenario
- m365solution-overview
ms.custom:
- intro-overview
description: Wdaj swoją infrastrukturę tożsamości na Microsoft 365.
ms.openlocfilehash: 77dbb7c5c38e2ecd8d8ef5ae71044565c2ae6b20
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016035"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>Wdrażanie infrastruktury tożsamości na Microsoft 365

W Microsoft 365 dla przedsiębiorstw dobrze zaplanowana i wykonana infrastruktura tożsamości zapewnia silniejsze zabezpieczenia, w tym ograniczanie dostępu do obciążeń pracą biurową i ich danych tylko uwierzytelnionym użytkownikom i urządzeniu. Zabezpieczenia tożsamości to kluczowy element wdrożenia zerowego zaufania, w którym wszystkie próby uzyskania dostępu do zasobów zarówno lokalnych, jak i w chmurze są uwierzytelniane i autoryzowane.

Aby uzyskać informacje na temat funkcji tożsamości poszczególnych usług Microsoft 365 dla przedsiębiorstw, roli usługi Azure Active Directory (Azure AD), składników lokalnych i opartych na chmurze oraz najpopularniejszych konfiguracji uwierzytelniania, zobacz plakat Infrastruktura [tożsamości.](../downloads/m365e-identity-infra.pdf)

[![Plakat Infrastruktura tożsamości.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Przejrzyj ten dwustronicowy plakat, aby szybko zapoznać się z pojęciami i konfiguracjami tożsamości Microsoft 365 przedsiębiorstwa.

Możesz pobrać [ten plakat i](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) wydrukować go w formacie listu, prawego lub tabloidu (11 x 17).

To rozwiązanie jest pierwszym krokiem do rozbudowania stosu wdrażania programu Microsoft 365 zerowego zaufania.

![Stos Microsoft 365 zerowego zaufania](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

Aby uzyskać więcej informacji, zobacz Microsoft 365 [wdrażania bez zaufania](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>Co jest w tym rozwiązaniu

To rozwiązanie umożliwia wdrożenie infrastruktury tożsamości dla dzierżawy usługi Microsoft 365 w celu zapewnienia dostępu pracownikom i ochrony przed atakami opartymi na tożsamościach.

![Wdrażanie infrastruktury tożsamości na Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

W tym rozwiązaniu należy wykonać następujące czynności:

1. [Określanie modelu tożsamości.](deploy-identity-solution-identity-model.md)
2. [Ochrona Microsoft 365 użytkowników z uprawnieniami.](protect-your-global-administrator-accounts.md)
3. [Chroń swoje Microsoft 365 użytkowników.](microsoft-365-secure-sign-in.md)
4. [Wdeksuj swój model tożsamości.](cloud-only-identities.md)

To rozwiązanie obsługuje najważniejsze zasady zerowego [zaufania](https://www.microsoft.com/security/business/zero-trust/):

- **Jawne sprawdzanie:** Zawsze uwierzytelnianie i autoryzacja na podstawie wszystkich dostępnych punktów danych.
- **Użyj dostępu z najmniejszymi uprawnieniami:** Ogranicz dostęp użytkowników dzięki technologii Just-In-Time i Just-Enough-Access (JIT/JEA), adaptacyjnym zasadom opartym na ryzyko i ochronie danych.
- **Załóżmy naruszenie:** Minimalizowanie promieni rozdęć i dostępu segmentów. Weryfikuj zaawansowane szyfrowanie i korzystaj z analizy, aby uzyskać widoczność, usprawnić wykrywanie zagrożeń i usprawnić obronę.

W przeciwieństwie do konwencjonalnego dostępu do intranetu, który ufa wszystkomu, co znajduje się w zaporze organizacji, zaufanie zerowe traktuje każde logowanie i dostęp tak, jakby pochodziło z niepod kontrolowanych sieci, niezależnie od tego, czy znajduje się za zaporą organizacji, czy za Internetem. Zerowe zaufanie wymaga ochrony sieci, infrastruktury, tożsamości, punktów końcowych, aplikacji i danych.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 i funkcje

Usługa Azure AD zapewnia pełny zestaw funkcji zarządzania tożsamościami i zabezpieczeń dla Twojej Microsoft 365 dzierżawy.

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|[Uwierzytelnianie wieloskładnikowe](/azure/active-directory/authentication/concept-mfa-howitworks)|Uwierzytelniania wieloskładnikowego użytkownicy muszą zapewniać dwie formy weryfikacji, takie jak hasło użytkownika oraz powiadomienie z aplikacji Microsoft Authenticator lub połączenia telefonicznego. Uwierzytelniania wieloskładnikowego znacznie zmniejsza ryzyko, że w celu uzyskania dostępu do środowiska można użyć skradzionych poświadczeń. Microsoft 365 logowania oparte na uwierzytelniania wieloskładnikowego Azure AD.|Microsoft 365 E3 lub E5|
|[Dostęp warunkowy](/azure/active-directory/conditional-access/overview)|Usługa Azure AD ocenia warunki logowania użytkownika i ustala dozwolony dostęp za pomocą zasad dostępu warunkowego. W tych wskazówkach popisano na przykład, jak utworzyć zasady dostępu warunkowego w celu wymagania zgodności urządzenia w celu uzyskania dostępu do danych poufnych. Znacznie zmniejsza to ryzyko, że haker na własnych urządzeniach i skradzione poświadczenia będą mieć dostęp do Twoich danych poufnych. Chroni także poufne dane na urządzeniach, ponieważ muszą one spełniać określone wymagania dotyczące kondycji i zabezpieczeń.|Microsoft 365 E3 lub E5|
|[Grupy usługi Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups)|Zasady dostępu warunkowego, zarządzanie urządzeniami za pomocą usługi Intune, a nawet uprawnienia do plików i witryn w organizacji opierają się na przypisaniu ich do kont użytkowników lub grup usługi Azure AD. Zalecamy utworzenie grup usługi Azure AD, które odpowiadają wprowadzanych poziomach ochrony. Na przykład pracownicy kierownictwa są prawdopodobnie wyższymi wartościami dla hakerów. Dlatego warto dodać konta użytkowników tych pracowników do grupy usługi Azure AD i przypisać tę grupę do zasad dostępu warunkowego i innych zasad, które wymuszają wyższy poziom ochrony dostępu.|Microsoft 365 E3 lub E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Pozwala wykrywać potencjalne luki w zabezpieczeniach tożsamości organizacji i konfigurować automatyczne zasady rozwiązywania problemów do niskiego, średniego i wysokiego ryzyka związanego z logowaniem oraz ryzyka użytkownika. Te wskazówki są oparte na tej ocenie ryzyka w celu zastosowania zasad dostępu warunkowego w przypadku uwierzytelniania wieloskładnikowego. Wskazówki te obejmują również zasady dostępu warunkowego, które wymagają od użytkowników zmiany hasła w przypadku wykrycia dla konta aktywności o wysokim poziomie ryzyka.|Microsoft 365 E5 Microsoft 365 E3 E5 Security, EMS E5 lub licencji Azure AD — wersja Premium P2 E5|
|[Samodzielne resetowanie hasła (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Zezwalaj użytkownikom na bezpieczne i bez interwencji działu pomocy technicznej, zapewniając weryfikację wielu metod uwierzytelniania, które administrator może kontrolować.|Microsoft 365 E3 lub E5|
|[Ochrona hasłem w usłudze Azure AD](/azure/active-directory/authentication/concept-password-ban-bad)|Wykrywaj i blokuj znane słabe hasła i ich warianty oraz dodatkowe słaby terminy specyficzne dla Twojej organizacji. Domyślne globalne listy zablokowanych haseł są automatycznie stosowane do wszystkich użytkowników w dzierżawie usługi Azure AD. Możesz zdefiniować dodatkowe wpisy na niestandardowej liście zablokowanych haseł. Gdy użytkownicy zmieniają lub resetują swoje hasła, te listy zablokowanych haseł są sprawdzane, aby wymusić stosowanie silnych haseł.|Microsoft 365 E3 lub E5|
|

## <a name="next-steps"></a>Następne kroki

Skorzystaj z tej procedury, aby wdrożyć model tożsamości i infrastrukturę uwierzytelniania dla Microsoft 365 dzierżawy:

1. [Określanie modelu tożsamości w chmurze.](deploy-identity-solution-identity-model.md)
2. [Ochrona Microsoft 365 użytkowników z uprawnieniami.](protect-your-global-administrator-accounts.md)
3. [Chroń swoje Microsoft 365 użytkowników.](microsoft-365-secure-sign-in.md)
4. Wdaj swój model tożsamości w chmurze: [tylko w](cloud-only-identities.md) chmurze lub w [trybie hybrydowym](prepare-for-directory-synchronization.md).

[![Określanie modelu tożsamości, który ma być Microsoft 365 dzierżawy usługi](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Dodatkowe zasoby tożsamości w chmurze firmy Microsoft

### <a name="manage"></a>Zarządzanie

Aby zarządzać wdrożeniem tożsamości w chmurze firmy Microsoft, zobacz:

- [Konta użytkowników](manage-microsoft-365-accounts.md)
- [Licencje](assign-licenses-to-user-accounts.md)
- [Hasła](manage-microsoft-365-passwords.md)
- [Grupy](manage-microsoft-365-groups.md)
- [Nadzór](manage-microsoft-365-identity-governance.md)
- [Synchronizacja katalogów](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Jak firma Microsoft obsługuje tożsamość dla Microsoft 365

Dowiedz się, jak eksperci IT na stronie firmy Microsoft [zarządzają tożsamościami i zabezpieczają dostęp](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>Ten zasób IT Showcase jest dostępny tylko w języku angielskim.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Jak firma Contoso zrobiła tożsamość dla Microsoft 365

Aby uzyskać przykład tego, jak fikcyjna, ale reprezentująca organizację globalną organizacja wdrożyła hybrydową infrastrukturę tożsamości dla usług Microsoft 365 w chmurze, zobacz Tożsamość firmy [Contoso Corporation](contoso-identity.md).

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
