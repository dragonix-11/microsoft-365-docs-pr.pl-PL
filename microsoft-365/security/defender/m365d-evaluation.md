---
title: Szacowanie Microsoft 365 Defender
description: Skonfiguruj laboratorium Microsoft 365 Defender próbne lub pilotażowe, aby wypróbować i wypróbować rozwiązanie zabezpieczające zaprojektowane do ochrony urządzeń, tożsamości, danych i aplikacji w organizacji.
keywords: Microsoft 365 Defender próbna, spróbuj Microsoft 365 Defender, oceń Microsoft 365 Defender, Microsoft 365 Defender laboratorium oceniania, Microsoft 365 Defender  pilot, zabezpieczenia cyberzabłędu, zaawansowane zagrożenia trwałe, zabezpieczenia przedsiębiorstwa, urządzenia, urządzenia, tożsamość, użytkownicy, dane, aplikacje, zdarzenia, zautomatyzowane badania i działania naprawcze, szukanie zaawansowane
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
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1c260588b80d8325567b74148a7a62586cfbc707
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959246"
---
# <a name="create-a-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Tworzenie laboratorium Microsoft 365 Defender próbnego lub środowiska pilotażowego 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender


Ten przewodnik ułatwia konfigurowanie środowiska laboratoryjnych z użytkownikami i grupami, a następnie przeprowadzi Cię przez konfigurację funkcji w programie Microsoft 365 Defender, aby można było naśladować ataki zagrożenia i uzyskać zrozumiały wynik próby. 

Celem utworzenia tego laboratorium próbnego lub środowiska pilotażowego jest zilustrowanie kompleksowych i zintegrowanych Microsoft 365 Defender pilotażowych. Poznaj sposób, w jaki to inteligentne rozwiązanie zabezpieczeń wykrywa, zapobiega, automatycznie bada i odpowiada na zaawansowane zagrożenia twojej organizacji. 


Zostaną Ci odpowiednie instrukcje, aby rozpocząć ocenę Microsoft 365 Defender na podstawie zalecanych ścieżek wdrażania. Celem jest pomoc w skonfigurowaniu rozwiązania zabezpieczającego w środowisku laboratoryjnym z kontem wersji próbnej lub w środowisku pilotażowym w środowisku produkcyjnym z pełną licencją. Przygotowanie laboratorium próbnego lub środowiska pilotażowego może ułatwić przedstawianie osób decyzyjnych w organizacji przypadków użycia zabezpieczeń. Po uruchomieniu symulowań ataków i ich zadowoleniu możesz w pełni wdrożyć i wdrożyć ją w organizacji, korzystając z pomocy specjalistów ds. sprzedaży firmy Microsoft lub ekspertów w Twojej organizacji. 

Ten przewodnik pomoże Ci:
- Konfigurowanie serwera laboratorium i komputerów
- Konfigurowanie usługi Active Directory z użytkownikami i grupami
- Konfigurowanie i konfigurowanie usługi Microsoft Defender dla tożsamości, programu Microsoft Defender dla systemu Office 365, programu Microsoft Defender dla punktu końcowego i Microsoft Cloud App Security
- Konfigurowanie zasad lokalnych dla serwera i komputerów
- Naśladowanie ataków na zagrożenia w celu wygenerowania zdarzenia testowego lub alertu w Microsoft 365 Defender

>[!IMPORTANT]
>Aby uzyskać optymalne wyniki, postępuj zgodnie z instrukcjami dotyczącymi konfiguracji laboratorium.


## <a name="deployment-phases"></a>Fazy wdrażania

Istnieją trzy fazy tworzenia Microsoft 365 Defender laboratorium próbnego.

![Fazy wdrażania: przygotowanie, konfiguracja, wdrożenie](../../media/evaluation-guide-phases.png)

|Faza | Opis | 
|:-------|:-----|
|[Etap 1. Przygotowywanie](prepare-m365d-eval.md)| Dowiedz się, co należy wziąć pod uwagę podczas wdrażania Microsoft 365 Defender w laboratorium próbnym lub w środowisku pilotażowym: <br><br>— Uczestnicy projektu i rejestracja <br> — Zagadnienia dotyczące środowiska <br>— Access <br>— Azure Active Directory konfiguracji <br> - Porządek konfiguracji
|[Etap 2. Konfigurowanie](setup-m365deval.md)|  Zrób początkowe kroki, aby uzyskać dostęp Microsoft 365 Security Center w celu skonfigurowania laboratorium Microsoft 365 Defender próbnego lub środowiska pilotażowego. Otrzymasz przewodnik:<br><br>- Zarejestruj się w celu Microsoft 365 E5 próbnego <br>  - Konfigurowanie domeny<br>- Przypisywanie Microsoft 365 E5 licencji<br>- Wykonaj zadania kreatora konfiguracji w portalu|
|[Etap 3. Konfigurowanie & Wniesienie](config-m365d-eval.md) | Skonfiguruj poszczególne Microsoft 365 Defender i punkty końcowe. Otrzymasz przewodnik:<br><br>- Konfigurowanie usługi Microsoft Defender dla Office 365<br>- Konfigurowanie Microsoft Cloud App Security<br>- Konfigurowanie usługi Microsoft Defender dla tożsamości<br>- Konfigurowanie programu Microsoft Defender dla punktu końcowego


Po ukończeniu tego przewodnika zidentyfikowalibyśmy uczestników projektu i wymagane zatwierdzenia, masz odpowiednie uprawnienia dostępu, założyły konto w celu wersji próbnej, skonfigurowano domeny i każdy ze słupków Microsoft 365 Defender, Microsoft 365 Defender punkty końcowe zostaną dołoowane do usługi.

## <a name="key-capabilities"></a>Najważniejsze funkcje

Chociaż Microsoft 365 Defender udostępnia wiele możliwości, głównym celem tego przewodnika po wdrażaniu jest wprowadzenie do pracy z urządzeniami przy wdrażaniu. Oprócz dodatku do pracy z usługą, z poniższych wskazówek możesz również rozpocząć pracę z następującymi możliwościami.


Funkcja | Opis 
:---|:---
Usługa Microsoft Defender dla Office 365 | Pomaga chronić cały swój Office 365 przed dzisiejszymi zagrożeniami
Microsoft Defender for Identity | Identyfikuje i wykrywa zagrożenia dla naruszonych tożsamości i złośliwych działań w ramach niejawnego programu testów.
Microsoft Cloud App Security | Zapewnia widoczność, kontrolowanie podróży danych i wykrywanie cyberataków w usługach w chmurze.
Ochrona punktu końcowego w usłudze Microsoft Defender | Zapobiega, wykrywa i udostępnia możliwości reagowania na zaawansowane zagrożenia przy użyciu kompleksowych zabezpieczeń punktów końcowych.


## <a name="in-scope"></a>W zakresie

W tym przewodniku mają zakres następujących zadań:
-   Konfigurowanie Azure Active Directory
-   Konfigurowanie Microsoft 365 Defender
    -   Zarejestruj się w celu Microsoft 365 E5 wersji próbnej lub użyj pełnej licencji, jeśli korzystasz z programu pilotażowego
    -   Konfigurowanie domeny
    -   Przypisywanie Microsoft 365 E5 licencji
    -   Kończenie pracy kreatora konfiguracji w portalu
-   Konfigurowanie wszystkich Microsoft 365 Defender na podstawie najlepszych rozwiązań
    -   Usługa Microsoft Defender dla Office 365
    -   Microsoft Defender for Identity
    -   Microsoft Cloud App Security
    -   Ochrona punktu końcowego w usłudze Microsoft Defender

## <a name="out-of-scope"></a>Poza zakresem

Następujące informacje nie znajdują się w tym przewodniku po wdrażaniu:

-   Konfiguracja rozwiązań innych firm, które mogą być zintegrowane z Microsoft 365 Defender
-   Testy penetracyjnych w środowisku produkcyjnym

## <a name="next-step"></a>Następny krok
[Etap 1. Przygotowywanie](prepare-m365d-eval.md) 
<br> Przygotowanie laboratorium Microsoft 365 Defender próbnego lub środowiska pilotażowego
