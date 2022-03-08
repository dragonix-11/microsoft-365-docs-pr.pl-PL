---
title: Krok nr 4. Definiowanie Microsoft 365 Defender, obowiązków i nadzór
description: Podstawowe informacje o definiowaniu ról, obowiązków i nadzorowania podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, atak, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, Microsoft 365, reagowanie na incydenty, cyberataki, zabezpieczenia, operacje zabezpieczeń, soc
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
ms.openlocfilehash: 7562eca50b905bf70f17844cf8fe3079fbf3fc14
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314283"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Krok nr 4. Definiowanie Microsoft 365 Defender, obowiązków i nadzór

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Twoja organizacja musi ustalić własność i odpowiedzialność Microsoft 365 Defender licencji, konfiguracji i administrowania jako zadań początkowych, zanim będzie można określić role operacyjne. Zazwyczaj prawo własności do licencji, kosztów subskrypcji i administrowania usługami Microsoft 365 i Enterprise Security + Mobility (EMS), które mogą obejmować usługę Microsoft 365 Defender, nie wchodzi w zakres zespołów Centrum operacji zabezpieczeń (SOC). Zespoły SOC powinny współpracować z tymi osobami, aby zapewnić odpowiedni nadzór nad Microsoft 365 Defender. 

Wiele nowoczesnych społeczności zawodowej przydziela członków swojego zespołu do kategorii na podstawie ich umiejętności i funkcji. Przykład:

- Zespół analizy zagrożeń przypisany do zadań związanych z zarządzaniem cyklem życia funkcji zagrożeń i analizy.
- Zespół monitorowania składa się z analityków SOC odpowiedzialnych za utrzymywanie dzienników, alertów, zdarzeń i funkcji monitorowania.
- Zespół inżynierów & inżynierów przydzielonych do inżynierów i optymalizowania urządzeń zabezpieczających.

Role i obowiązki zespołu SOC Microsoft 365 Defender się z tymi zespołami w sposób naturalny.

W poniższej tabeli przedstawiono role i obowiązki każdego zespołu SOC oraz sposób integracji tych ról z Microsoft 365 Defender.

| Zespół SOC | Role i obowiązki | Microsoft 365 Defender zadań  |
|:-------|:-----|:-------|
| Nadzór SOC | <ul><li>Wykonuje zarządzanie soc</li><li>Ustanawianie dziennych, tygodniowych, miesięcznych procesów</li><li>Zapewnia szkolenia i świadomość</li><li>Pracownicy, uczestniczenie w grupach i spotkaniach równorzędnych</li><li>Conducts Blue, Red, Purple team exercises</ul>  | <ul><li>Microsoft 365 Defender dostępu do portalu</li><li>Prowadzi rejestr funkcji/adresu URL i aktualizacji licencjonowania</li><li>Zapewnia komunikację z uczestnikami projektu w zakresie it, prawnych, zgodności i prywatności</li><li>Bierze udział w spotkaniach kontrolnych nad zmianami w nowych Microsoft 365 projektach lub Microsoft Azure projektach</ul> |
| Analiza zagrożeń i & analizy zagrożeń  | <ul><li>Zarządzanie zagrożeniami w kanale firmy Intel</li><li>Przypisanie wirusów i złośliwego oprogramowania</li><li>Modelowanie zagrożeń & kategoryzacji zdarzeń zagrożenia</li><li>Opracowywanie atrybutów zagrożeń w niejawnym programie testów </li><li>Integracja firmy Intel z programem zarządzania ryzykiem</li><li>Integruje szczegółowe informacje o danych z analizami danych, analizą danych i analizą z różnych zespołów hr, prawnych, IT i zabezpieczeń.<ul> | <ul><li>Obsługuje modelowanie zagrożeń za pomocą usługi Microsoft Defender dla tożsamości</li><li>Zapewnia program Microsoft Defender Office 365 modelowania zagrożeń</li><li>Zapewnia modelowanie zagrożeń dla programu Microsoft Defender na punktu końcowego</ul> |
| Monitorowanie | <ul><li>Analitycy poziomu 1, 2 i 3</li><li>Konserwacja i inżynieria źródła dziennika</li><li>Wprowadzanie źródła danych </li><li>Analizowanie SIEM, alertowanie, korelacja, optymalizacja</li><li>Generowanie zdarzeń i alertów</li><li>Analiza zdarzeń i alertów</li><li>Raportowanie zdarzeń i alertów</li><li>Konserwacja systemu biletowego</ul> | Używane: <ul><li>Centrum & zabezpieczeń</li><li>Microsoft 365 Defender portalu</ul> |
| Funkcje & secOps | <ul><li>Zarządzanie lukami w zabezpieczeniach aplikacji, systemów i punktów końcowych</li><li>Automatyzacja XDR/SOAR</li><li>Testy zgodności</li><li>Wyłudzanie informacji i inżynieria DLP</li><li>Inżynieria</li><li>Kontrolka zmiany współrzędnych</li><li>Koordynowanie aktualizacji podręcznika</li><li>Testy penetracyjnych<ul> | <ul><li>Usługa Microsoft Defender dla aplikacji w chmurze</li><li>Defender for Endpoint</li><li>Defender for Identity</ul> |
| Zespół reagowania na incydenty zabezpieczeń komputera (CSIRT) | <ul><li>Badanie i reagowanie na incydenty cyberprzestępne</li><li>Wykonuje forensics</li><li>**Często może być odizolowany od soc**</ul> | Współpraca i obsługa podręczników Microsoft 365 Defender reagowania na incydenty |
||||


## <a name="next-step"></a>Następny krok

[Krok 5. Opracuj i testuj przypadki użycia](integrate-microsoft-365-defender-secops-use-cases.md)
