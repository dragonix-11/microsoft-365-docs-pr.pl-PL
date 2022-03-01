---
title: Pilotaż programu Microsoft Defender dla aplikacji w chmurze za pomocą Microsoft 365 Defender
description: Skonfiguruj laboratorium próbne Microsoft 365 Defender pilotażowe, aby przetestować i przetestować rozwiązanie zabezpieczeń zaprojektowane do ochrony urządzeń, tożsamości, danych i aplikacji.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 484924d936f348fb29421b6bcc1789df4a44dc90
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010389"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Pilotaż programu Microsoft Defender dla aplikacji w chmurze za pomocą Microsoft 365 Defender


**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 3 z 3](eval-defender-mcas-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla aplikacji w chmurze. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-mcas-overview.md).

Aby skonfigurować i skonfigurować pilotaż programu Microsoft Defender dla aplikacji w chmurze, należy wykonać poniższe czynności.


![Procedura pilotażu programu Microsoft Defender dla aplikacji w chmurze.](../../media/defender/m365-defender-mcas-pilot-steps.png)

- Krok nr 1. [Tworzenie grupy pilotażowej — zakres wdrożenia pilotażowego dla określonych grup użytkowników](#step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups)
- [Krok 2. Konfigurowanie ochrony — kontrolka aplikacji dostępu warunkowego](#step-2-configure-protection--conditional-access-app-control)
- [Krok 3. Wypróbuj możliwości — omów samouczki dotyczące ochrony środowiska](#step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment) 


## <a name="step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups"></a>Krok nr 1. Tworzenie grupy pilotażowej — zakres wdrożenia pilotażowego dla określonych grup użytkowników

Program Microsoft Defender dla aplikacji w chmurze umożliwia zakres wdrożenia. Określanie zakresu umożliwia wybranie konkretnych grup użytkowników do monitorowania pod kątem aplikacji lub wykluczonych z monitorowania. Możesz uwzględnić lub wykluczyć grupy użytkowników. Aby zakres wdrożenia pilotażowego został ograniczony, zobacz [Wdrażanie z zakresem](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protection--conditional-access-app-control"></a>Krok nr 2. Konfigurowanie ochrony — kontrolka aplikacji dostępu warunkowego

Jedną z najbardziej zaawansowanych zabezpieczeń, które można skonfigurować, jest kontrola aplikacji dostępu warunkowego. Wymaga to integracji z usługą Azure Active Directory (Azure AD). Umożliwia stosowanie zasad dostępu warunkowego, w tym powiązanych zasad (takich jak wymaganie urządzeń o dobrej kondycji) do aplikacji w chmurze, które zostały przechowane. 

Pierwszym krokiem w zarządzaniu aplikacjami SaaS w usłudze Microsoft Defender for Cloud jest ich odnajdowanie, a następnie dodanie ich do dzierżawy usługi Azure AD. Jeśli potrzebujesz pomocy w odnajdowaniach, zobacz [Odnajdowanie aplikacji SaaS i zarządzanie nimi w swojej sieci](/cloud-app-security/tutorial-shadow-it). Po odnalezioniu aplikacji [dodaj je do dzierżawy usługi Azure AD](/azure/active-directory/manage-apps/add-application-portal).

Możesz zacząć zarządzać tymi procesami, wykonując następujące czynności:

- Najpierw w usłudze Azure AD utwórz nowe zasady dostępu warunkowego i skonfiguruj je tak, aby "Używanie kontrolki aplikacji dostępu warunkowego". To nastąpi przekierowanie żądania do usługi Defender dla aplikacji w chmurze. Możesz utworzyć jedną politykę i dodać do nich wszystkie aplikacje SaaS.
- Następnie w usłudze Defender dla aplikacji w chmurze utwórz zasady sesji. Utwórz jedną zasady dla każdej kontrolki, którą chcesz zastosować.

Aby uzyskać więcej informacji, w tym obsługiwanych aplikacji i klientów, zobacz Ochrona aplikacji za pomocą programu [Microsoft Defender dla aplikacji w](/cloud-app-security/proxy-intro-aad) chmurze Kontrola aplikacji dostępu warunkowego. 

Na przykład zasady, zobacz [Zalecane zasady programu Microsoft Defender dla aplikacji w chmurze dla aplikacji SaaS](../office-365-security/mcas-saas-access-policies.md). Te zasady opierają się na zestawie typowych zasad tożsamości i dostępu do [urządzeń, które](../office-365-security/microsoft-365-policies-configurations.md) są zalecane jako punkt wyjścia dla wszystkich klientów. 

## <a name="step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment"></a>Krok nr 3. Wypróbuj możliwości — omów samouczki dotyczące ochrony środowiska 

Dokumentacja programu Microsoft Defender dla aplikacji w chmurze zawiera serię samouczków pomocnych w odnajdywaniu ryzyka i ochronie środowiska. 

Wypróbuj samouczki dotyczące programu Defender dla aplikacji w chmurze:

- [Wykrywanie podejrzanych aktywności użytkowników](/cloud-app-security/tutorial-suspicious-activity)
- [Badanie ryzykownych użytkowników](/cloud-app-security/tutorial-ueba)
- [Badanie ryzykownych aplikacji protokołu OAuth](/cloud-app-security/investigate-risky-oauth)
- [Odnajdowanie i ochrona informacji poufnych](/cloud-app-security/tutorial-dlp)
- [Ochrona dowolnej aplikacji w organizacji w czasie rzeczywistym](/cloud-app-security/tutorial-proxy)
- [Blokowanie pobierania informacji poufnych](/cloud-app-security/use-case-proxy-block-session-aad)
- [Ochrona plików za pomocą kwarantanny administracyjnej](/cloud-app-security/use-case-admin-quarantine)
- [Wymagaj uwierzytelniania krok po ryzykownych działaniach](/cloud-app-security/tutorial-step-up-authentication)

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania w usłudze Microsoft Defender dla aplikacji w chmurze, zobacz [klip wideo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Następne kroki

[Badanie i odpowiadanie przy Microsoft 365 Defender w środowisku pilotażowym](eval-defender-investigate-respond.md)

Powrót do omówieniem Szacowanie [programu Microsoft Defender dla aplikacji w chmurze](eval-defender-mcas-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
