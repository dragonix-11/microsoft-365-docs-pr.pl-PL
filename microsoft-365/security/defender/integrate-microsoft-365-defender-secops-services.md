---
title: Krok nr 3. Planowanie Microsoft 365 Defender integracji z katalogiem usług SOC
description: Podstawowe informacje na temat integrowania Microsoft 365 Defender z wykazem usług w ramach operacji zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, ataki, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki, zabezpieczenia, operacje zabezpieczeń, soc
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
ms.openlocfilehash: 45497f74db9c68959d4b23e013c6ea483e86378a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323965"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Krok nr 3. Planowanie Microsoft 365 Defender integracji z katalogiem usług SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Ustanowione Centrum operacji zabezpieczeń (SOC) powinno zawierać katalog usług, który może zawierać:

- Analiza & w celu analizy złośliwego oprogramowania
- Attribution & reverse engineering
- Ochrona przed zagrożeniami
- Analiza
- Badania  pracy myśliwskiej
- Forensics
- Reagowanie na incydenty 
- CsIRT (Computer Security Incident Response Team) (który może być oddzielony od SOC) 
- Testy zgodności
- Monitorowanie zagrożeń w & w niejawnym programie testów
- Monitorowanie zdarzeń & zabezpieczeń 
- Skanowanie w przypadku luk
- Rozszerzone wykrywanie i odpowiedź (XDR, Extended Detection and Response)/Security Poszukamy, Automatyzacja i Odpowiedź (SOAR)
- Wyłudzanie informacji
- Ochrona przed utratą danych
- Monitorowanie marki

Ponieważ Microsoft 365 Defender technologie obejmują różne funkcje, zespół soc będzie musiał określić, które role i obowiązki najlepiej nadają się do zarządzania każdym składnikiem programu Microsoft 365 Defender i dostosowania do funkcji usługi.

Składniki składowe Microsoft 365 Defender:

- **Microsoft Defender for Identity** (wcześniej Azure Advanced Threat Protection, znany także jako Azure ATP) to oparte na chmurze rozwiązanie zabezpieczeń, które używa sygnałów Usługi domenowe w usłudze Active Directory (AD DS) do identyfikowania, wykrywania i badanie zaawansowanych zagrożeń, naruszonych tożsamości i złośliwych działań w ramach niejawnego programu testów skierowanych do organizacji.

- **Program Microsoft Defender for Endpoint** to rozwiązanie bezpieczeństwa punktu końcowego w chmurze oparte na chmurze dla urządzeń, które zawiera oparte na ryzyko zarządzanie lukami w zabezpieczeniach i oceny, zmniejszenie powierzchni ataków, ochronę opartą na zachowaniu i opartą na chmurze ochronę następnej generacji. wykrywanie i reagowanie w punktach końcowych (EDR), automatyczne badanie i rozwiązywanie problemów, usługi chłoniaków zarządzanych, rozbudowane interfejsy API i ujednolicone zarządzanie zabezpieczeniami.

 - **Microsoft Defender for Office 365** to oparta na chmurze usługa filtrowania poczty e-mail, która pomaga chronić organizacje przed nieznanym złośliwym oprogramowaniem i wirusami, zapewniając niezawodną, bezdniową ochronę i udostępnia funkcje chroniące organizacje przed niebezpiecznymi linkami w czasie rzeczywistym. Oferuje również szeroki zakres badań, badań, reakcji i środków zaradczych, informacji i szkoleń oraz funkcji bezpiecznego postępowania.

- **Program Microsoft Defender for Cloud Apps** to broker zabezpieczeń dostępu w chmurze (CASB), który obsługuje różne tryby wdrażania, w tym zbieranie dzienników, łączniki interfejsu API i odwrotny serwer proxy. Zapewnia on zaawansowaną widoczność, kontrolę nad podróżami danych oraz zaawansowane analizy w celu identyfikowania i zwalczania cyberataków we wszystkich usługach firmy Microsoft i innych firm w chmurze.

Ponieważ Microsoft 365 Defender składniki i technologie obejmują różne funkcje, Twój zespół soc będzie musiał określić, które role i obowiązki najlepiej nadają się do zarządzania każdym składnikiem programu Microsoft 365 Defender i dostosowania do funkcji usługi.

Aby zintegrować możliwości Microsoft 365 Defender, musisz uściślić usługi SOC. Aby uzyskać więcej informacji na temat możliwości Microsoft 365 Defender, zobacz następujące artykuły:

- [Co to jest program Microsoft Defender for Endpoint?](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Co to jest program Microsoft Defender for Identity?](/defender-for-identity/what-is)
- [Co to jest defender dla Office 365?](/office-365-security/defender-for-office-365)
- [Co to jest program Microsoft Defender dla aplikacji w chmurze?](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Następny krok

[Krok 4. Definiowanie Microsoft 365 Defender, obowiązków i nadzór](integrate-microsoft-365-defender-secops-roles.md)
