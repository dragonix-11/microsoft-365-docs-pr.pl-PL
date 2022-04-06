---
title: Krok nr 1. Planowanie gotowości operacji Microsoft 365 Defender
description: Podstawy planowania gotowości operacji Microsoft 365 Defender podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
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
ms.openlocfilehash: 8c69e92390e6ed6515be6f399703124ece99cc39
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664023"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>Krok nr 1. Planowanie gotowości operacji Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Niezależnie od bieżącej dojrzałości operacji zabezpieczeń ważne jest, aby dopasować je do centrum operacji zabezpieczeń (SOC). Chociaż nie ma jednego modelu, który pasuje do każdej organizacji, istnieją pewne aspekty, które są bardziej powszechne niż inne.

W poniższych sekcjach opisano podstawowe funkcje soc.

## <a name="provide-situational-awareness-of-modern-threats"></a>Zapewnianie świadomości sytuacyjnej współczesnych zagrożeń

Zespół SOC przygotowuje się i poluje na nowe i przychodzące zagrożenia, dzięki czemu może współpracować z organizacją w celu ustanowienia środków zaradczych i odpowiedzi. Twój zespół SOC powinien mieć personel, który jest wysoko wyszkolony w nowoczesnych metodach i technikach ataków oraz zrozumieć aktorów zagrożeń. Współużytkowana analiza zagrożeń i struktury, takie jak [łańcuch Cyber Kill Lub](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) [struktura MITRE ATT&CK](https://attack.mitre.org/) , mogą zwiększyć możliwości personelu analityków zagrożeń i łowców zagrożeń.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>Zapewnianie odpowiedzi pierwszego, drugiego i potencjalnie trzeciego poziomu na zdarzenia i zdarzenia cybernetyczne

SOC jest pierwszą linią obrony przed zdarzeniami i incydentami bezpieczeństwa. Gdy zdarzenie, zagrożenie, atak, naruszenie zasad lub wyniki inspekcji wyzwalają alert lub wezwanie do działania, zespół SOC dokonuje oceny w celu klasyfikacji i powstrzymania go lub eskalacji w celu zbadania. W związku z tym ratownicy pierwszego wiersza SOC muszą posiadać szeroką wiedzę techniczną na temat zdarzeń i wskaźników bezpieczeństwa.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>Scentralizowanie monitorowania i rejestrowania źródeł zabezpieczeń organizacji

Zazwyczaj podstawową funkcją zespołu SOC jest upewnienie się, że wszystkie urządzenia zabezpieczeń, takie jak zapory, systemy zapobiegania włamaniom, systemy zapobiegania utracie danych, systemy Zarządzanie zagrożeniami i lukami i systemy tożsamości, działają prawidłowo i są monitorowane. Zespoły SOC będą współpracować z szerszymi operacjami sieciowymi, takimi jak tożsamość, DevOps, chmura, aplikacja, nauka o danych i inne zespoły biznesowe, aby zapewnić scentralizowanie i zabezpieczenie analizy informacji o zabezpieczeniach. Ponadto zespół SOC jest odpowiedzialny za utrzymywanie dzienników danych w formatach możliwych do użycia i czytelnych, co może obejmować analizowanie i normalizowanie różnych formatów.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>Ustal gotowość operacyjną zespołu Red, Blue i Purple

Każdy zespół SOC powinien przetestować swoją gotowość do reagowania na incydent cybernetyczny. Testowanie można wykonać za pomocą ćwiczeń szkoleniowych, takich jak table-topy i przebiegi treningowe z różnymi osobami w branży IT, zabezpieczeniach i na poziomie biznesowym. Poszczególne zespoły treningowe są tworzone na podstawie reprezentatywnych ról i odgrywają rolę obrońcy (Blue Team), atakującego (Red Team) lub jako obserwatorzy dążący do poprawy metod i technik zespołów Niebieski i Czerwony poprzez mocne i słabe strony, które są odkrywane podczas ćwiczenia (Purple Team).

## <a name="next-step"></a>Następny krok

[Krok 2. Przeprowadzanie oceny gotowości do integracji soc przy użyciu Zero Trust Framework](integrate-microsoft-365-defender-secops-readiness.md)
