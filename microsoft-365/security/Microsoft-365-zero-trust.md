---
title: Plan wdrożenia platformy Microsoft 365 Zero Trust
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Dowiedz się, jak wdrażać zabezpieczenia Microsoft 365 Zero Trust w środowisku w celu ochrony przed zagrożeniami i ochrony poufnych danych.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: 4056310eb8e0d22a9758dfa2a572a473c83a0775
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669743"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Plan wdrożenia platformy Microsoft 365 Zero Trust

Ten artykuł zawiera plan wdrożenia na potrzeby tworzenia **zabezpieczeń Zero Trust** przy użyciu Microsoft 365. Zero Trust to nowy model zabezpieczeń, który zakłada naruszenie zabezpieczeń i weryfikuje każde żądanie tak, jakby pochodziło z niekontrolowanej sieci. Niezależnie od tego, skąd pochodzi żądanie i do jakiego zasobu uzyskuje dostęp, model Zero Trust uczy nas,aby "nigdy nie ufać, zawsze weryfikować".

Użyj tego artykułu razem z tym plakatem.

| Element | Opis |
|:-----|:-----|
|[![Ilustracja planu wdrożenia Microsoft 365 Zero Trust.](../media/solutions-architecture-center/m365-zero-trust-deployment-plan-thumb.png) ](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) <br/> [PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) \| [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx) <br/> Zaktualizowano marzec 2022 r. | **Powiązane przewodniki po rozwiązaniach** <br/> <ul><li>[Wdrażanie infrastruktury tożsamości dla Microsoft 365](/microsoft-365/enterprise/deploy-identity-solution-overview)</li><li>[Zalecane konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md)</li><li>[Zarządzanie urządzeniami przy użyciu Intune](../solutions/manage-devices-with-intune-overview.md)</li><li>[Ocena i pilotaż usługi Microsoft 365 Defender](../security/defender/eval-overview.md)</li><li>[Wdrażanie rozwiązania do ochrony informacji za pomocą Microsoft Purview](../compliance/information-protection-solution.md)</li><li>[Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365](../solutions/information-protection-deploy.md)</li></ul>

## <a name="zero-trust-security-architecture"></a>architektura zabezpieczeń Zero Trust

Podejście Zero Trust rozciąga się na całą infrastrukturę cyfrową i służy jako zintegrowana filozofia bezpieczeństwa i kompleksowa strategia.

Ta ilustracja przedstawia reprezentację podstawowych elementów, które współtworzą Zero Trust.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Architektura zabezpieczeń Zero Trust" lightbox="../media/zero-trust/zero-trust-architecture.png":::

Na ilustracji:

- Wymuszanie zasad zabezpieczeń znajduje się w centrum architektury Zero Trust. Obejmuje to uwierzytelnianie wieloskładnikowe z dostępem warunkowym, które uwzględnia ryzyko konta użytkownika, stan urządzenia oraz inne ustawione kryteria i zasady.
- Tożsamości, urządzenia, dane, aplikacje, sieć i inne składniki infrastruktury są skonfigurowane z odpowiednimi zabezpieczeniami. Zasady skonfigurowane dla każdego z tych składników są skoordynowane z ogólną strategią Zero Trust. Na przykład zasady urządzeń określają kryteria dla urządzeń w dobrej kondycji, a zasady dostępu warunkowego wymagają urządzeń w dobrej kondycji w celu uzyskania dostępu do określonych aplikacji i danych.
- Ochrona przed zagrożeniami i analiza monitoruje środowisko, zwiększa bieżące zagrożenia i podejmuje zautomatyzowane działania w celu skorygowania ataków.

Aby uzyskać więcej informacji na temat Zero Trust, zobacz [_**Centrum wskazówek Zero Trust**_](/security/zero-trust) firmy Microsoft.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype).
-->



## <a name="deploying-zero-trust-for-microsoft-365"></a>Wdrażanie Zero Trust dla Microsoft 365

Microsoft 365 jest celowo kompilowana z wieloma funkcjami zabezpieczeń i ochrony informacji, które ułatwiają tworzenie Zero Trust w środowisku. Wiele możliwości można rozszerzyć, aby chronić dostęp do innych aplikacji SaaS używanych przez organizację i danych w tych aplikacjach.

Ta ilustracja przedstawia pracę wdrażania Zero Trust możliwości. Ta praca jest podzielona na jednostki pracy, które można skonfigurować razem, zaczynając od dołu i pracując na górze, aby upewnić się, że praca wymagania wstępnego została ukończona.

:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Stos wdrażania Microsoft 365 Zero Trust" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Na tej ilustracji:

- Zero Trust zaczyna się od podstawy tożsamości i ochrony urządzeń.
- Możliwości ochrony przed zagrożeniami są oparte na tych podstawach, aby zapewnić monitorowanie i korygowanie zagrożeń bezpieczeństwa w czasie rzeczywistym.
- Ochrona informacji i ład zapewniają zaawansowane mechanizmy kontroli ukierunkowane na określone typy danych w celu ochrony najcenniejszych informacji i zapewnienia zgodności ze standardami zgodności, w tym ochrony danych osobowych.


W tym artykule przyjęto założenie, że masz już skonfigurowaną tożsamość w chmurze. Jeśli potrzebujesz wskazówek dotyczących tego celu, zobacz [**Wdrażanie infrastruktury tożsamości dla Microsoft 365**](/microsoft-365/enterprise/deploy-identity-solution-overview).

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Krok nr 1. Konfigurowanie Zero Trust tożsamości i ochrony dostępu do urządzeń — zasady punktu początkowego

Pierwszym krokiem jest utworzenie podstawy Zero Trust przez skonfigurowanie ochrony tożsamości i dostępu do urządzeń.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Proces konfigurowania tożsamości Zero Trust i ochrony dostępu do urządzeń" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::

Przejdź do [**_Zero Trust ochrony tożsamości i dostępu do urządzeń_**](office-365-security/microsoft-365-policies-configurations.md), aby uzyskać wskazówki nakazowe, aby to osiągnąć. W tej serii artykułów opisano zestaw konfiguracji wymagań wstępnych dotyczących tożsamości i dostępu do urządzeń oraz zestaw Azure Active Directory (Azure AD) dostępu warunkowego, Microsoft Intune i innych zasad w celu zabezpieczenia dostępu do Microsoft 365  dla aplikacji i usług w chmurze dla przedsiębiorstw, innych usług SaaS i aplikacji lokalnych opublikowanych za pomocą Azure AD serwer proxy aplikacji.

|Zawiera|Wymagania wstępne|Nie obejmuje|
|---------|---------|---------|
|Zalecane zasady dostępu do tożsamości i urządzeń dla trzech warstw ochrony: <ul><li>Punkt początkowy</li><li>Enterprise (zalecane)</li><li>Specjalistyczne</li></ul> <br> Dodatkowe zalecenia dotyczące: <ul><li>Użytkownicy zewnętrzni (goście)</li><li>Microsoft Teams</li><li>SharePoint Online</li><li>Microsoft Defender for Cloud Apps</lu></ul>|Microsoft E3 lub E5 <br><br> Azure Active Directory w każdym z tych trybów: <ul><li>Tylko w chmurze</li><li>Uwierzytelnianie hybrydowe z uwierzytelnianiem synchronizacji skrótów haseł (PHS)</li><li>Hybrydowe z uwierzytelnianiem przekazywanym (PTA)</li><li>Federacyjnych</li></ul>|Rejestrowanie urządzeń dla zasad, które wymagają urządzeń zarządzanych. Zobacz [Krok 2. Zarządzanie punktami końcowymi przy użyciu Intune](#step-2-manage-endpoints-with-intune) do rejestrowania urządzeń|

Rozpocznij od zaimplementowania warstwy punktu początkowego. Te zasady nie wymagają rejestrowania urządzeń do zarządzania.

:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Zasady Zero Trust tożsamości i dostępu do urządzeń — warstwa punktu początkowego" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::

## <a name="step-2-manage-endpoints-with-intune"></a>Krok nr 2. Zarządzanie punktami końcowymi za pomocą Intune

Następnie zarejestruj urządzenia w systemie zarządzania i rozpocznij ich ochronę za pomocą bardziej zaawansowanych kontrolek.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Zarządzanie punktami końcowymi za pomocą elementu Intune" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::

Przejdź do obszaru [**_Zarządzanie urządzeniami za pomocą Intune_**](../solutions/manage-devices-with-intune-overview.md), aby uzyskać nakazowe wskazówki, aby to osiągnąć.

|Zawiera|Wymagania wstępne|Nie obejmuje|
|---------|---------|---------|
|Rejestrowanie urządzeń przy użyciu Intune: <ul><li>Urządzenia należące do firmy</li><li>Rozwiązanie Autopilot/zautomatyzowane</li><li>Rejestracji</li></ul> <br> Konfigurowanie zasad: <ul><li>Zasady ochrony aplikacji</li><li>Zasady zgodności</li><li>Zasady profilu urządzenia</li></ul>|Rejestrowanie punktów końcowych za pomocą Azure AD|Konfigurowanie możliwości ochrony informacji, w tym: <ul><li>Typy informacji poufnych</li><li>Etykiety</li><li>Zasady DLP</li></ul> <br> Aby uzyskać te możliwości, zobacz [Krok 5. Ochrona poufnych danych i zarządzanie nimi](#step-5-protect-and-govern-sensitive-data) (w dalszej części tego artykułu).|

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Krok nr 3. Dodawanie tożsamości Zero Trust i ochrony dostępu do urządzeń — zasady Enterprise

Dzięki urządzeniom zarejestrowanym w zarządzaniu można teraz zaimplementować pełny zestaw zalecanych Zero Trust zasad dotyczących tożsamości i dostępu do urządzeń, które wymagają zgodnych urządzeń.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Zasady Zero Trust tożsamości i dostępu za pomocą zarządzania urządzeniami" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

[**_Wróć do typowych zasad dostępu do tożsamości i urządzeń_**](office-365-security/identity-access-policies.md) i dodaj zasady w warstwie Enterprise.

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Zero Trust zasad tożsamości i dostępu — Enterprise (zalecane)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Krok nr 4. Ocena, pilotaż i wdrażanie Microsoft 365 Defender

Microsoft 365 Defender to rozszerzone rozwiązanie do wykrywania i reagowania (XDR), które automatycznie zbiera, koreluje i analizuje dane sygnału, zagrożeń i alertów z całego środowiska Microsoft 365, w tym punkty końcowe, pocztę e-mail, aplikacje i tożsamości.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Proces dodawania Microsoft 365 Defender do architektury Zero Trust" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Przejdź do [**_tematu Evaluate and pilot Microsoft 365 Defender (Ocena i pilotażowe Microsoft 365 Defender_**](defender/eval-overview.md)), aby zapoznać się z przewodnikiem metodycznym dotyczącym pilotażu i wdrażania składników Microsoft 365 Defender.

|Zawiera|Wymagania wstępne|Nie obejmuje|
|---------|---------|---------|
|Skonfiguruj środowisko ewaluacji i pilotażu dla wszystkich składników: <ul><li>Defender for Identity</li><li>Ochrona usługi Office 365 w usłudze Defender</li><li>Ochrona punktu końcowego w usłudze Microsoft Defender</li><li>Microsoft Defender for Cloud Apps</li></ul> <br> Ochrona przed zagrożeniami <br><br> Badanie zagrożeń i odpowiadanie na nie|Zapoznaj się ze wskazówkami, aby zapoznać się z wymaganiami dotyczącymi architektury dla każdego składnika Microsoft 365 Defender.| Azure AD usługa Identity Protection nie jest uwzględniona w tym przewodniku po rozwiązaniach. Jest on uwzględniony w [kroku 1. Skonfiguruj Zero Trust tożsamości i ochrony dostępu do urządzeń](#step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies).|

## <a name="step-5-protect-and-govern-sensitive-data"></a>Krok nr 5. Ochrona poufnych danych i zarządzanie nimi

Zaimplementuj Microsoft Purview Information Protection, aby ułatwić odnajdywanie, klasyfikowanie i ochronę poufnych informacji wszędzie tam, gdzie się znajdują lub podróżują.

Microsoft Purview Information Protection możliwości są dołączone do Microsoft Purview i udostępniają narzędzia do poznania danych, ochrony danych i zapobiegania utracie danych.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Funkcje ochrony informacji chroniące dane poprzez wymuszanie zasad" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Chociaż ta praca jest reprezentowana w górnej części stosu wdrażania zilustrowanego wcześniej w tym artykule, możesz rozpocząć tę pracę w dowolnym momencie.

Microsoft Purview Information Protection zapewnia strukturę, proces i możliwości, których można użyć do realizacji określonych celów biznesowych.

![Microsoft Purview Information Protection](../media/zero-trust/mip-solution-overview.png)

Aby uzyskać więcej informacji na temat planowania i wdrażania ochrony informacji, zobacz [**_Wdrażanie rozwiązania Microsoft Purview Information Protection_**](../compliance/information-protection-solution.md). 

Jeśli wdrażasz ochronę informacji dla przepisów dotyczących prywatności danych, ten przewodnik po rozwiązaniach zawiera zalecaną strukturę dla całego procesu: [**_Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365_**](../solutions/information-protection-deploy.md).
