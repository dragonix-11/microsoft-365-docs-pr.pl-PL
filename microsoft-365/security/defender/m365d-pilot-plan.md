---
title: Planowanie projektu Microsoft 365 Defender pilotażowego
description: Zaplanuj projekt pilotażowy Microsoft 365 Defender uczestnikami projektu, aby zarządzać oczekiwaniami i zapewnić pomyślne wyniki.
keywords: Microsoft 365 Defender pilotażowy, planowanie projektu Microsoft 365 Defender, ocenianie Microsoft 365 Defender produkcji, Microsoft 365 Defender  projekt pilotażowy, zabezpieczenia cyberzabłędu, zaawansowane zagrożenia trwałe, zabezpieczenia przedsiębiorstwa, urządzenia, urządzenie, tożsamość, użytkownicy, dane, aplikacje, zdarzenia, zautomatyzowane badania i działania naprawcze, szukanie zaawansowane
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6a52df8035ce6f84770a2d06c3b8c127e426622e
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959248"
---
# <a name="planning-your-pilot-microsoft-365-defender-project"></a>Planowanie projektu Microsoft 365 Defender pilotażowego 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

|![Planowanie](../../media/phase-diagrams/1-planning.png)<br/>Planowanie|[![Przygotowywanie](../../media/phase-diagrams/2-prepare.png)](prepare-m365d-eval.md)<br/>[Przygotowanie](prepare-m365d-eval.md) | [![Symulowanie ataków](../../media/phase-diagrams/3-simluate.png)](m365d-pilot-simulate.md)<br/>[Symulowanie ataków](m365d-pilot-simulate.md) | [![Zamykanie i podsumowywane](../../media/phase-diagrams/4-summary.png)](m365d-pilot-close.md)<br/>[Zamykanie i podsumowywane](m365d-pilot-close.md)|
|--|--|--|--|
|*Jesteś tutaj!*| | | |

Jesteś obecnie w fazie planowania.

Aby zapewnić sukces projektu pilotażowego, na początku należy dokładnie zaplanować projekt pilotażowy i uzyskać zatwierdzenia od uczestników projektu. Elementy planowania obejmują identyfikowanie zakresu, przypadków użycia, wymagań i kryteriów sukcesu.

W tym przewodniku opisano sposób planowania projektu pilotażowego. 

>[!IMPORTANT]
>Aby uzyskać optymalne wyniki, postępuj zgodnie z instrukcjami pilotażowymi tak ściśle, jak to możliwe.


## <a name="scope"></a>Zakres

Zakres pilotażu będzie określał zakres testowania na podstawie Twojego środowiska i akceptowalnych metod testowania. Oto kilka przykładowych zakresów do rozważenia:

- Środowisko projektowe lub testowe, które obejmuje punkty końcowe, serwery, kontrolery domen.
- Środowisko produkcyjne z usługami Microsoft 365, Azure, usługami Active Directory, punktami końcowymi i serwerami

>[!NOTE]
>Jeśli nie masz jeszcze pełnych licencji, możesz uzyskać licencje wersji próbnej do oceny Microsoft 365 Defender — planowanie [](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , przygotowywanie, konfigurowanie, konfigurowanie i uruchamianie projektu pilotażowego. Udziałowcy będą odgrywać dużą rolę w ułatwianiu procesu od początku do końca.

Typy systemów operacyjnych, które mają być sprawdzane, powinny być również zdefiniowane na podstawie struktury organizacyjnej. Mogą to być następujące punkty końcowe: [punkty końcowe komputerów Mac](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements), serwery [Linux](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements), [Windows 10 punkty końcowe](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions), [Windows Server 2016](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions).

## <a name="use-cases"></a>Przypadki użycia

Przypadki użycia przedstawiają instrukcje dotyczące sposobu, w jaki testowane narzędzie ma być używane przez określonych użytkowników. Te informacje można formować jako historie użytkowników z punktu widzenia określonej osoby, na przykład analityka SOC. Przykład:

- Jako analityk SOC muszę wyświetlać, korelować, oceniać alerty i zdarzenia oraz zarządzać nimi na różnych urządzeniach, użytkownikach i w skrzynkach pocztowych w mojej sieci. [Zarządzanie zdarzeniami]
- Jako analityk SOC, muszę mieć narzędzie i proces, aby automatycznie badać złośliwe zdarzenia i odpowiadać na nie w mojej sieci. [Auto IR]
- Jako analityk SOC muszę przeszukiwać dane z mojego środowiska, aby znaleźć znane i potencjalne zagrożenia oraz podejrzane działania. [Zaawansowane szukanie]

Należy pamiętać, że takie przypadki użycia należy tworzyć w obrębie parametrów zdefiniowanego zakresu. Jeśli na przykład zakres testowania nie obejmuje oceny narzędzi, takich jak Microsoft Cloud App Security, nie należy tworzyć przypadków, które opierają się na tym jako źródło danych.

## <a name="requirements"></a>Wymagania

Z listy przypadków użycia możesz zacząć tworzyć wymagania. Wymagania obejmują funkcje, które muszą spełniać wymagania narzędzia w przypadku użycia. Te wymagania można podzielić na kategorie, takie jak konfiguracja i konserwacja, obsługa integracji i wymagania specyficzne dla funkcji, takie jak czas pracy myśliwskiej i możliwość tworzenia alertów niestandardowych.

## <a name="test-plan"></a>Plan testowania

W zależności od wymagań mogą być odpowiednie różne metody testowania. Jeśli na przykład jest wymagane oszacowanie automatycznie naprawień, plan testowania musi zawierać kroki w celu wygenerowania zachowań, które wyzwoliłyby automatyczne działania naprawcze w ramach Microsoft 365 Defender. Jeśli wymagane jest wykrycie określonego zachowania lub ataków, test może obejmować więcej kroków. Punktem wyjścia jest zaplanowanie dokładnego przetestowania pod względem wymagań.

## <a name="success-criteria"></a>Kryteria sukcesu

Kryteria sukcesu są ostatecznie słupkami ustawionymi do mierzenia w stosunku do testów. Niezależnie od tego, czy testuje się Microsoft 365 Defender (lub jakiejkolwiek innej technologii w tym zakresie) na innych narzędziach, czy też samodzielnie, musi być pewne kryteria ilościowe, aby określić wartość udostępnianą przez narzędzie. Kryteria sukcesu będą określać sposób testowania na podstawie zakresu, wymagań i planu testowania. Powinno to być mniej wynikowy lub nieudany, a w zależności od Potrzeb większa jest średnia ważona wyniki. Aby na przykład odnieść sukces, narzędzie może okazać się niezbędne do oceny powyżej 80% w określonych krytycznych obszarach.

## <a name="scorecard"></a>Karta wyników

Jednym ze sposobów zesłania wszystkich elementów planu jest utworzenie karty wyników. Zobacz przykładową kartę wyników poniżej:

| Przypadek użycia | Wymagania | Wymagania dotyczące konfiguracji | Plan testowania | Oczekiwany wynik | Stan testu | Wynik | Uwagi |
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|Zarządzanie zdarzeniami|— Microsoft 365 Defender </br></br>- Microsoft Defender for Identity </br></br>- Microsoft Defender for Endpoint </br></br>- Microsoft Cloud App Security (opcjonalnie)|Aby uzyskać [szczegółowe informacje](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , zobacz wymagania wstępne dotyczące przygotowania, konfiguracji i konfiguracji. |[Symulowanie ataków](m365d-pilot-simulate.md) <br></br>[Badanie zdarzenia](./m365d-pilot-simulate.md#investigate-an-incident) |Schowek może zrozumieć zakres i wpływ zdarzenia oraz zarządzać zdarzeniem.||||
|AutoIR|— Microsoft 365 Defender </br></br>- Microsoft Defender for Identity </br></br>- Microsoft Defender for Endpoint |Aby uzyskać [szczegółowe informacje](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , zobacz wymagania wstępne dotyczące przygotowania, konfiguracji i konfiguracji. <br>Włączanie funkcji AutoIR  |[Symulowanie ataków](m365d-pilot-simulate.md) <br></br>[Zautomatyzowane badanie](m365d-pilot-simulate.md#automated-investigation-and-remediation) |Alerty i zdarzenia są automatycznie korygowane przez Microsoft 365 Defender||||
|Zaawansowane łowy|— Microsoft 365 Defender </br></br>- Microsoft Defender for Endpoint </br></br>— Microsoft Defender dla Office 365 |Aby uzyskać [szczegółowe informacje](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , zobacz wymagania wstępne dotyczące przygotowania, konfiguracji i konfiguracji.|[Scenariusz zaawansowanego chłoniania](./m365d-pilot-simulate.md#advanced-hunting-scenario) |Wschowy mogą znaleźć dane podczas zaawansowanego wyszukiwania, przeskakiwania do jednostek, na które wpływa to zagrożenie, oraz przez tworzenie niestandardowych wykrywania.||||

## <a name="next-step"></a>Następny krok

|![Faza przygotowawowa](../../media/mtp/prep.png) <br>[Faza przygotowawowa](prepare-m365d-eval.md) | Przygotowanie środowiska Microsoft 365 Defender pilotażowego
|:-------|:-----|
