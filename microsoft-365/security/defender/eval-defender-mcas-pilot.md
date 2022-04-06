---
title: Pilot Microsoft Defender for Cloud Apps z Microsoft 365 Defender
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
ms.openlocfilehash: 73601660fc4b7ee2f58748d7e59a10aa53157745
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570134"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Pilot Microsoft Defender for Cloud Apps z Microsoft 365 Defender


**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 3 z 3](eval-defender-mcas-overview.md) w procesie konfigurowania środowiska oceny dla Microsoft Defender for Cloud Apps. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-mcas-overview.md).

Aby skonfigurować i skonfigurować pilotaż dla programu Microsoft Defender for Cloud Apps, należy wykonać poniższe Microsoft Defender for Cloud Apps.


:::image type="content" source="../../media/defender/m365-defender-mcas-pilot-steps.png" alt-text="Procedura pilotażowa Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-pilot-steps.png":::
- [Krok 1. Tworzenie grupy pilotażowej — zakres wdrożenia pilotażowego dla określonych grup użytkowników](#step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups)
- [Krok 2. Konfigurowanie ochrony — kontrolka aplikacji dostępu warunkowego](#step-2-configure-protectionconditional-access-app-control)
- [Krok 3. Wypróbuj możliwości — omów samouczki dotyczące ochrony środowiska](#step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment) 

## <a name="step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups"></a>Krok nr 1. Tworzenie grupy pilotażowej — zakres wdrożenia pilotażowego dla określonych grup użytkowników

Microsoft Defender for Cloud Apps umożliwia zakres wdrożenia. Określanie zakresu umożliwia wybranie konkretnych grup użytkowników do monitorowania pod kątem aplikacji lub wykluczonych z monitorowania. Możesz uwzględnić lub wykluczyć grupy użytkowników. Aby zakres wdrożenia pilotażowego został ograniczony, zobacz [Wdrażanie z zakresem](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protectionconditional-access-app-control"></a>Krok nr 2. Konfigurowanie ochrony — kontrolka aplikacji dostępu warunkowego

Jedną z najbardziej zaawansowanych zabezpieczeń, które można skonfigurować, jest kontrola aplikacji dostępu warunkowego. Ta ochrona wymaga integracji z usługą Azure Active Directory (Azure AD). Umożliwia stosowanie zasad dostępu warunkowego, w tym powiązanych zasad (takich jak wymaganie urządzeń o dobrej kondycji) do aplikacji w chmurze, które zostały przechowane. 

Pierwszym krokiem podczas korzystania Microsoft Defender for Cloud Apps do zarządzania aplikacjami SaaS jest odnajdowanie tych aplikacji, a następnie dodawanie ich do dzierżawy usługi Azure AD. Jeśli potrzebujesz pomocy w odnajdowaniach, zobacz [Odnajdowanie aplikacji SaaS i zarządzanie nimi w swojej sieci](/cloud-app-security/tutorial-shadow-it). Po wykryeniu aplikacji dodaj [je do dzierżawy usługi Azure AD](/azure/active-directory/manage-apps/add-application-portal).

Możesz zacząć zarządzać tymi aplikacjami, wykonując następujące zadania:

- Najpierw w usłudze Azure AD utwórz nowe zasady dostępu warunkowego i skonfiguruj je tak, aby "Używanie kontrolki aplikacji dostępu warunkowego". Ta konfiguracja ułatwia przekierowanie żądania do usługi Defender dla Chmury Apps. Możesz utworzyć jedną politykę i dodać do nich wszystkie aplikacje SaaS.
- Następnie na stronie Defender dla Chmury utwórz zasady sesji. Utwórz jedną zasady dla każdej kontrolki, którą chcesz zastosować.

Aby uzyskać więcej informacji, w tym obsługiwanych aplikacji i klientów, zobacz [Chroninie aplikacji za Microsoft Defender for Cloud Apps kontrolek aplikacji dostępu warunkowego](/cloud-app-security/proxy-intro-aad). 

Na przykład zasady można znaleźć w [Microsoft Defender for Cloud Apps polecanych zasad saas](../office-365-security/mcas-saas-access-policies.md). Te zasady opierają się na zestawie typowych zasad tożsamości i dostępu do [urządzeń, które](../office-365-security/microsoft-365-policies-configurations.md) są zalecane jako punkt wyjścia dla wszystkich klientów. 

## <a name="step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment"></a>Krok nr 3. Wypróbuj możliwości — omów samouczki dotyczące ochrony środowiska 

Dokumentacja Microsoft Defender for Cloud Apps zawiera serię samouczków pomocnych w odnajdowanie ryzyka i ochrony środowiska. 

Wypróbuj samouczki Defender dla Chmury aplikacji:

- [Wykrywanie podejrzanych aktywności użytkowników](/cloud-app-security/tutorial-suspicious-activity)
- [Badanie ryzykownych użytkowników](/cloud-app-security/tutorial-ueba)
- [Badanie ryzykownych aplikacji protokołu OAuth](/cloud-app-security/investigate-risky-oauth)
- [Odnajdowanie i ochrona informacji poufnych](/cloud-app-security/tutorial-dlp)
- [Ochrona dowolnej aplikacji w organizacji w czasie rzeczywistym](/cloud-app-security/tutorial-proxy)
- [Blokowanie pobierania informacji poufnych](/cloud-app-security/use-case-proxy-block-session-aad)
- [Ochrona plików za pomocą kwarantanny administracyjnej](/cloud-app-security/use-case-admin-quarantine)
- [Wymagaj uwierzytelniania krok po ryzykownych działaniach](/cloud-app-security/tutorial-step-up-authentication)

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania Microsoft Defender for Cloud Apps danych, zobacz [klip wideo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Następne kroki

[Badanie i odpowiadanie przy Microsoft 365 Defender w środowisku pilotażowym](eval-defender-investigate-respond.md)

Powrót do omówieniem [funkcji Szacowanie Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
