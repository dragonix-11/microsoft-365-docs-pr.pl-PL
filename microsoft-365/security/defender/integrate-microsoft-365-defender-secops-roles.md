---
title: Krok nr 4. Definiowanie Microsoft 365 Defender ról, obowiązków i nadzoru
description: Podstawy definiowania ról, obowiązków i nadzoru podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, atak, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, adres e-mail, 365, microsoft, Microsoft 365, reagowanie na zdarzenia, cyberatak, secops, operacje zabezpieczeń, soc
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
ms.openlocfilehash: 5410db413ece81a39453070985e6c744e8b684a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664067"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Krok nr 4. Definiowanie Microsoft 365 Defender ról, obowiązków i nadzoru

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Twoja organizacja musi ustanowić własność i odpowiedzialność Microsoft 365 Defender licencji, konfiguracji i administracji jako początkowe zadania, zanim będzie można zdefiniować jakiekolwiek role operacyjne. Zazwyczaj własność licencji, kosztów subskrypcji i administrowania usługami Microsoft 365 i Enterprise Security + Mobility (EMS) (które mogą obejmować Microsoft 365 Defender) wykracza poza zespoły usługi Security Operations Center (SOC). Zespoły SOC powinny współpracować z tymi osobami, aby zapewnić odpowiedni nadzór nad Microsoft 365 Defender. 

Wiele nowoczesnych soc przypisać członków zespołu do kategorii na podstawie ich zestawów umiejętności i funkcji. Przykład:

- Zespół analizy zagrożeń przypisany do zadań związanych z zarządzaniem cyklem życia funkcji analizy i zagrożeń.
- Zespół monitorujący składający się z analityków SOC odpowiedzialnych za obsługę dzienników, alertów, zdarzeń i funkcji monitorowania.
- Zespół ds. operacji & inżynierów przypisany do inżyniera i optymalizowania urządzeń zabezpieczeń.

Role zespołu SOC i obowiązki dotyczące Microsoft 365 Defender naturalnie integrują się z tymi zespołami.

W poniższej tabeli przedstawiono role i obowiązki każdego zespołu SOC oraz sposób integracji ich ról z Microsoft 365 Defender.

| Zespół SOC | Role i obowiązki | zadania Microsoft 365 Defender  |
|:-------|:-----|:-------|
| Nadzór SOC | <ul><li>Wykonuje ład SOC</li><li>Ustanawia procesy codziennie, co tydzień i co miesiąc</li><li>Zapewnia szkolenia i świadomość</li><li>Zatrudnia pracowników, uczestniczy w grupach równorzędnych i spotkaniach</li><li>Prowadzi ćwiczenia zespołowe Blue, Red, Purple</ul>  | <ul><li>Microsoft 365 Defender kontrolki dostępu do portalu</li><li>Utrzymuje funkcję/adres URL i rejestr aktualizacji licencjonowania</li><li>Utrzymuje komunikację z osobami biorącymi udział w projekcie it, prawnym, zgodności i prywatności</li><li>Uczestniczy w spotkaniach kontroli zmian dla nowych inicjatyw Microsoft 365 lub Microsoft Azure</ul> |
| Analiza zagrożeń & Analytics  | <ul><li>Zarządzanie źródłami danych intel zagrożeń</li><li>Przypisywanie wirusów i złośliwego oprogramowania</li><li>Modelowanie zagrożeń & kategoryzacji zdarzeń zagrożeń</li><li>Opracowywanie atrybutów zagrożeń wewnętrznych </li><li>Integracja rozwiązania Threat Intel z programem zarządzania ryzykiem</li><li>Integruje szczegółowe informacje o danych z analizą danych, analizą biznesową i analizą w zespołach ds. kadr, prawnych, IT i zabezpieczeń<ul> | <ul><li>Utrzymuje modelowanie zagrożeń Microsoft Defender for Identity</li><li>Utrzymuje modelowanie zagrożeń Ochrona usługi Office 365 w usłudze Microsoft Defender</li><li>Utrzymuje modelowanie zagrożeń Ochrona punktu końcowego w usłudze Microsoft Defender</ul> |
| Monitorowania | <ul><li>Warstwa 1, 2, 3 analitycy</li><li>Konserwacja i inżynieria źródła dzienników</li><li>Pozyskiwanie źródła danych </li><li>Analiza SIEM, alerty, korelacja, optymalizacja</li><li>Generowanie zdarzeń i alertów</li><li>Analiza zdarzeń i alertów</li><li>Raportowanie zdarzeń i alertów</li><li>Konserwacja systemu biletów</ul> | Używa: <ul><li>Centrum zgodności & zabezpieczeń</li><li>portal Microsoft 365 Defender</ul> |
| Inżynieria & SecOps | <ul><li>Zarządzanie lukami w zabezpieczeniach dla aplikacji, systemów i punktów końcowych</li><li>Automatyzacja XDR/SOAR</li><li>Testowanie zgodności</li><li>Wyłudzanie informacji i inżynieria DLP</li><li>Inżynierii</li><li>Kontrolka zmian współrzędnych</li><li>Współrzędne aktualizacji elementu Runbook</li><li>Testy penetracyjne<ul> | <ul><li>Microsoft Defender for Cloud Apps</li><li>Ochrona punktu końcowego w usłudze Microsoft Defender</li><li>Defender for Identity</ul> |
| Zespół reagowania na zdarzenia zabezpieczeń komputera (CSIRT) | <ul><li>Badanie zdarzeń cybernetycznych i reagowanie na nie</li><li>Wykonuje badania kryminalistyczne</li><li>**Często mogą być odizolowane od soc**</ul> | Współpraca i obsługa podręczników Microsoft 365 Defender reagowania na zdarzenia |
||||


## <a name="next-step"></a>Następny krok

[Krok 5. Opracowywanie i testowanie przypadków użycia](integrate-microsoft-365-defender-secops-use-cases.md)
