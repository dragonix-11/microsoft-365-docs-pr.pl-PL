---
title: Uruchamianie projektu pilotażowego Microsoft 365 Defender projektu
description: Uruchomienie pilotażowego Microsoft 365 Defender produkcyjnego w celu skutecznego określenia korzyści i wdrożenia Microsoft 365 Defender.
keywords: Microsoft 365 Defender, uruchom projekt pilotażowy Microsoft 365 Defender, oceń Microsoft 365 Defender produkcji, Microsoft 365 Defender  projekt pilotażowy, zabezpieczenia cyberzabłędu, zaawansowane zagrożenia trwałe, zabezpieczenia przedsiębiorstwa, urządzenia, urządzenie, tożsamość, użytkownicy, dane, aplikacje, zdarzenia, zautomatyzowane badania i działania naprawcze, szukanie zaawansowane
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
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fd84ef93d679be6e1e42f823dcac1f2d5181f1e9
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959244"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>Uruchamianie projektu pilotażowego Microsoft 365 Defender projektu 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender


Ten przewodnik ułatwia prowadzenie projektu pilotażowego przez podanie wskaźników w celu zapewnienia, że masz dobrze ustrukturyzowany plan, prowadzenie przez korzystanie z funkcji symulacyjnej ataków, a na koniec zakończenie propozycji pilotażowej z kluczowymi krokami do zastanowienia się nad wynikami i dokumentowania wyników.

![Etapy uruchamiania Microsoft 365 Defender pilotażowego](../../media/pilotphases.png)


Uruchomienie pilotażu pomaga w efektywnej ustaleniu korzyści z przyjęcia Microsoft 365 Defender. Przed włączeniem Microsoft 365 Defender w środowisku produkcyjnym i uruchomieniem przypadków użycia najlepiej jest zaplanować zadania do wykonania w ramach projektu pilotażowego i ustawić kryteria sukcesu. 


## <a name="how-to-use-this-pilot-playbook"></a>Jak korzystać z tego podręcznika pilotażowego

Ten przewodnik zawiera omówienie Microsoft 365 Defender i instrukcji krok po kroku dotyczących sposobu skonfigurowania projektu pilotażowego. 

Microsoft 365 Defender to ujednolicony pakiet ochrony przed naruszeniem i po naruszeniu zabezpieczeń przedsiębiorstwa, który natywnie koordynuje ochronę, wykrywanie, zapobieganie, badanie i reakcję między punktami końcowymi, tożsamościami, pocztą e-mail i aplikacjami, aby zapewnić zintegrowaną ochronę przed zaawansowanymi atakami. Robi to przez połączenie i wymusanie następujących funkcji w jedno rozwiązanie zabezpieczeń:

- Microsoft Defender for Endpoint (endpoints)
- Program Microsoft Defender dla Office 365 (e-mail)
- Microsoft Defender for Identity (identity)
- Microsoft Cloud App Security (aplikacje)

![Obraz of_Microsoft rozwiązania Defender 365 dla użytkowników, usługi Microsoft Defender dla tożsamości dla punktów końcowych programu Microsoft Defender, dla aplikacji w chmurze, usług Microsoft Cloud App Security i danych program Microsoft Defender dla komputerów Office 365](../../media/mtp/m365pillars.png)

Dzięki zintegrowanemu rozwiązaniu Microsoft 365 Defender specjaliści bezpieczeństwa mogą jednocześnie chować się przed zagrożeniami, które mogą oznaczać, że usługa Microsoft Defender dla punktu końcowego, usługa Microsoft Defender dla systemów Office 365, Microsoft Defender for Identity i Microsoft Cloud App Security  odbieranie i określanie pełnego zakresu i wpływu zagrożeń, tego, jak wprowadzono je do środowiska, czego dotyczy i jak wpływa ono obecnie na organizację. Microsoft 365 Defender, które mają na celu zapobieganie atakom i samodzielnym dostępom między skrzynkami pocztowymi, punktami końcowymi i tożsamościami użytkowników, których to dotyczy. Aby uzyskać [szczegółowe Microsoft 365 Defender, zobacz](microsoft-365-defender.md) omówienie Microsoft 365 Defender.

Następująca przykładowa oś czasu różni się w zależności od posiadania odpowiednich zasobów w Twoim środowisku. Niektóre wykrywanie i przepływy pracy mogą wymagać więcej czasu uczenia się niż pozostałe.

![Przykładowa oś czasu w ramach uruchomienia Microsoft 365 Defender pilotażowego](../../media/phase-diagrams/pilot-phases.png)

> [!IMPORTANT]
> Aby uzyskać optymalne wyniki, postępuj zgodnie z instrukcjami pilotażowymi tak ściśle, jak to możliwe.

### <a name="pilot-playbook-phases"></a>Fazy podręcznika pilotażowego

Istnieją cztery fazy uruchomienia Microsoft 365 Defender pilotażowego:

|Faza | Opis |
|:-------|:-----|
| [Planowanie](m365d-pilot-plan.md)<br> ~ 1 dzień| Dowiedz się, co należy wziąć pod uwagę przed uruchomieniem Microsoft 365 Defender pilotażowego: <br><br>- Zakres <br> — Przypadki użycia <br>— Wymagania <br>— Plan testowy <br> — Kryteria sukcesu <br> - Karta wyników 
| [Przygotowanie](m365d-evaluation.md) <br>~2 dni|  Dostęp Microsoft 365 zabezpieczeń w celu skonfigurowania środowiska Microsoft 365 Defender pilotażowego. Otrzymasz przewodnik:<br><br>— Identyfikowanie uczestników projektu i szukanie rejestracji dla pilotażu <br> — Zagadnienia dotyczące środowiska <br>— Access <br>— Azure Active Directory konfiguracji <br> - Porządek konfiguracji <br> - Zarejestruj się w celu Microsoft 365 E5 próbnego <br> - Konfigurowanie domeny <br>— Przypisywanie Microsoft 365 E5 licencji <br> - Wykonaj zadania kreatora konfiguracji w portalu|
| [Symulacja ataków](m365d-pilot-simulate.md) <br>~2 dni| Aby symulować atak, otrzymasz  przewodnik:<br><br>— Sprawdź wymagania środowiska testowego <br>— Uruchamianie symulacyjnej <br>— Badanie zdarzenia <br>— rozstrzygnieć zdarzenie 
| [Zamknięcie i podsumowanie](m365d-pilot-close.md) <br>~ 1 dzień| Po zakończeniu tego procesu zostaną Ci przewodnik:<br><br>— przejdź przez końcowe dane wyjściowe<br>— Przedstawianie danych wyjściowych uczestnikom projektu <br>- Przekazać opinię <br>— Następne kroki 

## <a name="next-step"></a>Następny krok

|[Faza planowania](m365d-pilot-plan.md) | Planowanie Microsoft 365 Defender pilotażowego 
|:-------|:-----|
