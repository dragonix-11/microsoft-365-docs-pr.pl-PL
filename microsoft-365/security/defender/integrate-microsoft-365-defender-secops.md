---
title: Integrowanie Microsoft 365 Defender z operacjami zabezpieczeń
description: Podstawowe informacje na temat integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
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
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 6bfec4b38d3451d25d65c63ce46fb8df74cd6d0e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013667"
---
# <a name="integrating-microsoft-365-defender-into-your-security-operations"></a>Integrowanie Microsoft 365 Defender z operacjami zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Nowoczesne Centrum operacji zabezpieczeń (SOC, Security Operations Center) to oparty na analizie, adaptacyjna organizacja, która pochłonie strategię ochrony przed zagrożeniami, czyli przeniesienie procesów zabezpieczeń wcześniej w procesie wdrażania, aby zapewnić wbudowane zabezpieczenia. Oznacza to, że tradycyjne przypisywanie odizolowanych technologii i procesów pojedynczym analitykom zabezpieczeń nie obsługuje już znacznej ilości danych pochodzących z wielu źródeł. Analitycy i inżynierowie zabezpieczeń są proszeni o bardziej szczegółowe podejście i korzystanie z wspólnych informacji na różnych platformach i w celu efektywnego działania.

Z tego powodu wdrażanie i implementacja platformy Microsoft 365 Defender będzie wymagać starannego planowania wraz z zespołem SOC w celu zoptymalizowania codziennie wykonywanych operacji i zarządzania cyklem życia samej Microsoft 365 Defender firmy. W tej zawartości opisano kilka pojęć dotyczących operacyjności i integracji programu Microsoft 365 Defender z nowymi lub istniejącymi osobami, procesami i technologiami, które stanowią podstawę nowoczesnych operacji zabezpieczeń.

Jeśli nie znasz już Microsoft 365 Defender, zobacz następujące artykuły:

- [Wprowadzenie do Microsoft 365 Defender](get-started.md)
- [Włączanie Microsoft 365 Defender](m365d-enable.md)

Jeśli Twoja organizacja wdrożyła już niektóre aspekty Microsoft 365 Defender, mogą potwierdzić lub ulepszyć istniejącą architekturę i procesy.

>[!Note]
>Jako partner firmy Microsoft protiviti współtwoował ten artykuł i przekazał istotne opinie na jego temat.
>

## <a name="target-audience"></a>Docelowa grupa odbiorców

Ta zawartość jest przeznaczona do następujących czynności:

- DevOps i operacji zabezpieczeń (SecOps)
- Zespoły inżynierów ds. zabezpieczeń
- Zespoły IT
- CisOs i CTO
- Kolor czerwony, niebieski i Teams
- CsIRT dla & forensic teams
- Microsoft 365 administratorów

## <a name="next-steps"></a>Następne kroki

Aby zintegrować Microsoft 365 Defender z soc, należy wykonać poniższe czynności.

- [Krok 1. Planowanie na Microsoft 365 Defender operacji](integrate-microsoft-365-defender-secops-plan.md)
- [Krok 2. Przeprowadzanie oceny gotowości integracji soc przy użyciu struktury zerowego zaufania](integrate-microsoft-365-defender-secops-readiness.md)
- [Krok 3. Planowanie Microsoft 365 Defender integracji z katalogiem usług SOC](integrate-microsoft-365-defender-secops-services.md)
- [Krok 4. Definiowanie Microsoft 365 Defender, obowiązków i nadzór](integrate-microsoft-365-defender-secops-roles.md)
- [Krok 5. Opracuj i testuj przypadki użycia](integrate-microsoft-365-defender-secops-use-cases.md)
- [Krok 6. Identyfikowanie zadań konserwacji soc](integrate-microsoft-365-defender-secops-tasks.md)



