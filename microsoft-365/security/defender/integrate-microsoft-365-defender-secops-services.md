---
title: Krok nr 3. Planowanie integracji Microsoft 365 Defender z katalogiem usług SOC
description: Podstawy integracji Microsoft 365 Defender z katalogiem usług operacji zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, atak, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, adres e-mail, 365, microsoft, m365, reagowanie na zdarzenia, cyberatak, secops, operacje zabezpieczeń, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: f6cab6be7d41f1d71a6ccf69fbedfa616694ee78
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438493"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Krok nr 3. Planowanie integracji Microsoft 365 Defender z katalogiem usług SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Ustanowione centrum operacji zabezpieczeń (SOC) powinno mieć wykaz usług, które mogą obejmować:

- Analiza złośliwego oprogramowania & włamań
- Atrybucja & inżynierii odwrotnej
- Analiza zagrożeń
- Analytics
- Badanie zagrożeń
- Forensics
- Reagowanie na zdarzenia 
- Computer Security Incident Response Team (CSIRT) (które mogą być oddzielone od SOC) 
- Testowanie zgodności
- Monitorowanie oszustw & zagrożeń wewnętrznych
- Monitorowanie zdarzenia & zdarzenia zabezpieczeń 
- Skanowanie luk w zabezpieczeniach
- Rozszerzone wykrywanie i reagowanie (XDR)/Orkiestracja zabezpieczeń, automatyzacja i reagowanie (SOAR)
- Wyłudzanie informacji
- Zapobieganie utracie danych
- Monitorowanie marki

Ponieważ technologie Microsoft 365 Defender obejmują różne funkcje, zespół SOC będzie musiał określić, które role i obowiązki najlepiej nadają się do zarządzania każdym składnikiem Microsoft 365 Defender i dopasowania do funkcji usługi.

Składniki Microsoft 365 Defender to:

- **Microsoft Defender for Identity** (dawniej Azure Advanced Threat Protection, znana również jako Azure ATP) to oparte na chmurze rozwiązanie zabezpieczeń, które używa sygnałów Active Directory Domain Services (AD DS) do identyfikowania, wykrywania i badania zaawansowanych zagrożeń, tożsamości z naruszeniem zabezpieczeń i złośliwych akcji wewnętrznych skierowanych do Organizacji.

- **Ochrona punktu końcowego w usłudze Microsoft Defender** to całościowe rozwiązanie zabezpieczeń punktów końcowych dostarczane w chmurze dla urządzeń, które obejmuje zarządzanie lukami w zabezpieczeniach i ocenę opartą na ryzyku, redukcję obszaru ataków, opartą na zachowaniu i opartą na chmurze nową generację ochrona, wykrywanie i reagowanie w punktach końcowych (EDR), automatyczne badanie i korygowanie, zarządzane usługi wyszukiwania zagrożeń, zaawansowane interfejsy API i ujednolicone zarządzanie zabezpieczeniami.

 - **Ochrona usługi Office 365 w usłudze Microsoft Defender** to oparta na chmurze usługa filtrowania poczty e-mail, która pomaga chronić organizacje przed nieznanym złośliwym oprogramowaniem i wirusami, zapewniając niezawodną ochronę zerodniową i udostępnia funkcje chroniące organizacje przed szkodliwymi linkami w czasie rzeczywistym. Oferuje również kompleksową listę badań i zagrożeń, reagowania i korygowania, świadomości i szkolenia oraz bezpiecznych funkcji postawy.

- **Microsoft Defender for Cloud Apps** jest brokerem zabezpieczeń dostępu do chmury (CASB), który obsługuje różne tryby wdrażania, w tym zbieranie dzienników, łączniki interfejsu API i zwrotny serwer proxy. Zapewnia ona bogaty wgląd, kontrolę nad przenoszeniem danych i zaawansowane analizy umożliwiające identyfikowanie i zwalczanie cyberoszertw we wszystkich usługach firmy Microsoft i innych firm w chmurze.

Ponieważ Microsoft 365 Defender składniki i technologie obejmują różne funkcje, zespół SOC będzie musiał określić, które role i obowiązki najlepiej nadają się do zarządzania każdym składnikiem Microsoft 365 Defender i dopasowania do funkcji usługi.

Aby zintegrować możliwości Microsoft 365 Defender, należy uściślić usługi SOC. Aby uzyskać więcej informacji na temat możliwości Microsoft 365 Defender, zobacz następujące artykuły:

- [Co to jest Ochrona punktu końcowego w usłudze Microsoft Defender?](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Co to jest usługa Microsoft Defender for Identity?](/defender-for-identity/what-is)
- [Co to jest Ochrona usługi Office 365 w usłudze Defender?](/microsoft-365/security/defender/microsoft-365-defender)
- [Co to jest usługa Microsoft Defender for Cloud Apps?](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Następny krok

[Krok 4. Definiowanie Microsoft 365 Defender ról, obowiązków i nadzoru](integrate-microsoft-365-defender-secops-roles.md)
