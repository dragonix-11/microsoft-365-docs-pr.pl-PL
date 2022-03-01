---
title: Krok nr 2. Przeprowadzanie oceny gotowości integracji soc przy użyciu struktury zerowego zaufania
description: Podstawowe informacje na temat przeprowadzania oceny gotowości integracji SOC przy użyciu struktury zerowego zaufania podczas integrowania programu Microsoft 365 Defender z operacjami zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, ataki, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki, zabezpieczenia, operacje zabezpieczeń, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: ca58d56e9caf6aa8a359a0776fc160cca04fec8a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013384"
---
# <a name="step-2-perform-a-soc-integration-readiness-assessment-using-the-zero-trust-framework"></a>Krok nr 2. Przeprowadzanie oceny gotowości integracji soc przy użyciu struktury zerowego zaufania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Po zakończeniu definicji podstawowych funkcji zespołu Centrum operacji zabezpieczeń (SOC, Security Operations Center) następnym krokiem dla organizacji jest przygotowanie się na wdrożenie programu Microsoft 365 Defender w ramach podejścia bez [zaufania.](/security/zero-trust/) Wdrażanie może ułatwić ustalenie wymagań wymaganych do wdrożenia programu Microsoft 365 Defender z zastosowaniem nowoczesnych najlepszych w branży rozwiązań, oceniając możliwości firmy Microsoft 365 Defender w środowisku.

Takie podejście opiera się na silnych podstawach ochrony i obejmuje kluczowe obszary, takie jak tożsamość, punkty końcowe (urządzenia), dane, aplikacje, infrastruktura i sieci. Zespół oceniania gotowości określi obszary, w których nie zostały jeszcze spełnione wymagania Microsoft 365 Defender i będzie potrzebować środków zaradczych.

Poniżej przedstawiono niektóre elementy, które trzeba będzie rozwiązać, aby soc w pełni zoptymalizował procesy w soc:

- **Tożsamość:** Starsze domeny lokalne (Usługi domenowe w usłudze Active Directory (AD DS), bez planu uwierzytelniania wieloskładnikowego, bez spisu kont uprzywilejowanych i innych.
- **Punkty końcowe (urządzenia):** Duża liczba starszych systemów operacyjnych, ograniczony spis urządzeń i inne.
- **Dane i aplikacje:**  Brak standardów zarządzania danymi, brak spisu niestandardowych aplikacji, które nie będą zintegrowane.
- **Infrastruktura:** Duża liczba niezwiązanych licencji SaaS, bez zabezpieczeń kontenerów i innych.
- **Sieci:** Problemy z wydajnością wynikające z niskiej przepustowości, płaskiej sieci, problemów z zabezpieczeniami bezprzewodowymi i innymi.

Organizacje powinny również postępować zgodnie z [artykułem](m365d-enable.md) Microsoft 365 Defender w celu przechwycenia podstawowego zestawu wymagań konfiguracyjnych. Te kroki będą z kolei określać działania naprawcze, które zespoły SOC będą musiały wykonać w celu skutecznego opracowywania przypadków użycia. 

Procedury przyjęcia i tworzenie przypadków użycia opisano w krokach 3 i 4.

## <a name="next-step"></a>Następny krok

[Krok 3. Planowanie Microsoft 365 Defender integracji z katalogiem usług SOC](integrate-microsoft-365-defender-secops-services.md)
