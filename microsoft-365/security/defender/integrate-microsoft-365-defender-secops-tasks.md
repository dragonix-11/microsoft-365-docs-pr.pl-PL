---
title: Krok 6. Identyfikowanie zadań konserwacji SOC
description: Identyfikowanie zadań konserwacji SOC podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
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
ms.openlocfilehash: 6b1ee22f8176d6f682eb9e9f2134cc27db91affd
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783628"
---
# <a name="step-6-identify-soc-maintenance-tasks"></a>Krok 6. Identyfikowanie zadań konserwacji SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Poniżej przedstawiono okresowe lub wymagane zadania do obsługi soc dla Microsoft 365 Defender.

|Działanie|Opis|Rytm|Przypisany zespół|
|---|---|---|---|
|Współpraca administracji usługami z usługą SOC Teams|Administrowanie usługami peryferyjnymi, takimi jak śledzenie zasobów (CMDB), licencjonowanie aplikacji (nowe licencje SaaS), zakupy urządzeń (uaktualnianie lub odnawianie wdrożeń urządzeń) oraz inne Microsoft 365 zmiany w całej dzierżawie (Intune, Microsoft 365 i inne), które mogą mieć wpływ na wdrażanie produktów Microsoft 365 Defender .|Co tydzień i zgodnie z potrzebami|Inżynieria & SecOps|
|Aktualizowanie kampanii chroniących przed wyłudzaniem informacji i zapobieganiem utracie danych|Uwzględnij przypadek użycia SOC i wnioski wyciągnięte z rozszerzonej organizacji (kadra, prawa, szkolenia i inne).|Co miesiąc i w razie potrzeby|Nadzór SOC|
|W razie potrzeby wdrażaj skrypty i usługi automatyzacji|Pobierz i przetestuj skrypty automatyzacji oraz pliki konfiguracji z zatwierdzonych witryn firmy Microsoft, aby ulepszyć operacje Microsoft 365 Defender.|Co tydzień i zgodnie z potrzebami|Inżynieria i secops|
|Zarządzanie portalem lub licencjami|Sprawdź anonsy i centrum Wiadomości Microsoft dla portalu Microsoft 365 Defender lub wymagania dotyczące licencjonowania na podstawie aktualizacji i nowych funkcji firmy Microsoft.|Tygodniowy|Nadzór SOC|
|Aktualizowanie biletów eskalacji soc|Wszystkie zespoły SOC aktualizują przypisane bilety eskalacji (takie jak sentinel, bilety usługi ServiceNow).|Codziennie|Wszystkie zespoły SOC|
|Śledzenie działania korygowania luk w zabezpieczeniach Microsoft 365 Defender & zagrożeń|Wygeneruj działania korygowania wskaźnika bezpieczeństwa tvm i raportuj właścicielom zasobów za pośrednictwem portalu intranetowego.|Codziennie|Monitorowania|
|Generowanie raportu wskaźnika bezpieczeństwa|Zespół monitorujący śledzi i zgłasza ulepszenia bezpiecznego wyniku.|Tygodniowy soc|Monitorowania|
|Uruchamianie ćwiczenia tabeli środowiska IR|Testowanie podręczników zespołu SOC w ćwiczeniu tabletop.|W razie potrzeby|Wszystkie zespoły SOC|

Zintegruj te zadania z bieżącymi procesami SOC.

## <a name="next-steps"></a>Następne kroki

Należy przejrzeć przewodniki, o których mowa w tej zawartości i w [bibliotece Microsoft 365 Defender](/microsoft-365/security/defender), aby określić, w jaki sposób twoja implementacja Microsoft 365 Defender powinna być ustrukturyzowana i zintegrowana.
