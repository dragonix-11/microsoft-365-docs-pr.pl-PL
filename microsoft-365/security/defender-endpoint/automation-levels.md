---
title: Poziomy automatyzacji w automatycznym śledztwie i rozwiązywaniu problemów
description: Omówienie poziomów automatyzacji i ich działania w programie Microsoft Defender for Endpoint
keywords: automated, investigation, level, Microsoft Defender for Endpoint
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 10/22/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: e440675a46a4340e2f659b23a31b19dbab33d2c0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328165"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Poziomy automatyzacji w możliwościach automatycznego badania i rozwiązywania problemów

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Funkcje automatycznego badania i rozwiązywania problemów (AIR) w programie Microsoft Defender for Endpoint można skonfigurować na jednym z kilku poziomów automatyzacji. Poziom automatyzacji ma wpływ na to, czy działania naprawcze po badaniach air są podejmowane automatycznie, czy tylko po zatwierdzeniu.

- *Pełna automatyzacja* (zalecana) oznacza, że działania naprawcze są podejmowane automatycznie na artefaktach określonych jako złośliwe.
- *Automatyczna automatyzacja* oznacza, że niektóre akcje naprawcze są podejmowane automatycznie, ale inne działania naprawcze oczekują na zatwierdzenie przed podjęciem. (Zobacz tabelę w [tece Poziomy automatyzacji](#levels-of-automation)).
- Wszystkie akcje naprawcze, zarówno oczekujące, jak i zakończone, są śledzone w Centrum akcji ([https://security.microsoft.com](https://security.microsoft.com)).

> [!TIP]
> Aby uzyskać najlepsze wyniki, zalecamy stosowanie pełnej automatyzacji podczas [konfigurowania funkcji AIR](configure-automated-investigations-remediation.md). Dane zbierane i analizowane w ubiegłym roku pokazują, że klienci korzystający z pełnej automatyzacji usunęli o 40% bardziej ufne próbki złośliwego oprogramowania niż klienci, którzy stosujący niższe poziomy automatyzacji. Pełna automatyzacja może ułatwić zasoby związane z operacjami zabezpieczeń w celu skoncentrowania się w sposób bardziej strategiczny na inicjatywach.

## <a name="levels-of-automation"></a>Poziomy automatyzacji

W poniższej tabeli opisano poszczególne poziom automatyzacji i sposób jej działania.

<br>

****

|Poziom automatyzacji|Opis|
|---|---|
|**Pełne — automatyczne korygowanie zagrożeń** <br> (nazywana również pełną *automatyzacją*)|Ze pełną automatyzacją działania naprawcze są wykonywane automatycznie. Wszystkie wykonane działania naprawcze można wyświetlić w Centrum [akcji na](auto-investigation-action-center.md) **karcie** Historia. W razie potrzeby działania naprawcze można cofnąć. <p> **_Pełna automatyzacja_* jest zalecana i jest domyślnie wybrana dla dzierżaw utworzonych 16 sierpnia 2020 r. przy użyciu programu Microsoft Defender for Endpoint, ale nie zdefiniowano jeszcze grup urządzeń.*|
|**Pół - wymagaj zatwierdzenia wszelkich działań naprawczych** <br> (nazywana również *półautomatyzmem*)|W przypadku tego poziomu półautomazyjnych działań naprawczych jest wymagane zatwierdzenie. Takie oczekujące akcje można wyświetlać i zatwierdzać w [Centrum akcji](auto-investigation-action-center.md) na karcie **Oczekujące** . <p> *Ten poziom pół automatyzacji jest domyślnie wybierany dla dzierżaw utworzonych przed 16 sierpnia 2020 r. przy użyciu programu Microsoft Defender dla punktu końcowego, bez zdefiniowanych grup urządzeń.*|
|**Pół - wymaganie zatwierdzenia rozwiązywania problemów z folderami podstawowymi** <br> (również typ *pół automatyzacji*)|W przypadku tego poziomu półautomazy jest wymagane zatwierdzanie wszelkich działań naprawczych niezbędnych dla plików lub plików wykonywalnych z folderów podstawowych. Foldery podstawowe obejmują katalogi systemu operacyjnego, takie **jak Windows** (`\windows\*`). <p> Akcje naprawcze mogą być wykonywane automatycznie na plikach lub plikach wykonywalnych, które znajdują się w innych (nierdzeniowych) folderach. <p> Oczekujące akcje dotyczące plików lub plików wykonywalnych w folderach podstawowych można wyświetlać i zatwierdzać w Centrum [akcji na](auto-investigation-action-center.md) **karcie Oczekujące** . <p> Akcje wykonane na plikach lub plikach wykonywalnych w innych folderach można wyświetlać w Centrum [akcji na](auto-investigation-action-center.md) **karcie** Historia.|
|**Pół - wymaganie zatwierdzenia działań naprawczych folderów nie temp** <br> (również typ *pół automatyzacji*)|W przypadku tego poziomu półautomazy jest wymagane zatwierdzanie wszelkich działań naprawczych wymaganych dla plików lub plików wykonywalnych, które nie znajdują *się w* folderach tymczasowych. <p> Foldery tymczasowe mogą zawierać następujące przykłady: <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Akcje naprawcze mogą być wykonywane automatycznie na plikach lub plikach wykonywalnych w folderach tymczasowych. <p> Oczekujące akcje dotyczące plików lub plików wykonywalnych, które nie znajdują się w folderach tymczasowych [, można](auto-investigation-action-center.md) wyświetlać i zatwierdzać w Centrum akcji na **karcie Oczekiwanie** . <p> Akcje wykonane na plikach lub plikach wykonywalnych w folderach tymczasowych można wyświetlać i zatwierdzać w Centrum [akcji na](auto-investigation-action-center.md) **karcie** Historia.|
|**Brak automatycznej odpowiedzi** <br> (ta automatyzacja jest również *nazywana bez automatyzacji*)|Bez automatyzacji automatyczne badanie nie jest uruchamiane na urządzeniach organizacji. W wyniku tego w wyniku zautomatyzowanego badania nie są podejmowane ani oczekujące akcje naprawcze. Jednak inne funkcje ochrony przed zagrożeniami, takie jak ochrona przed [potencjalnie](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) niechcianymi aplikacjami, mogą obowiązywać w zależności od konfiguracji oprogramowania antywirusowego i funkcji ochrony następnej generacji. <p> ***Korzystanie z *opcji bez* automatyzacji** nie jest zalecane, ponieważ zmniejsza bezpieczeństwo urządzeń w Twojej organizacji. [Rozważ skonfigurowanie poziomu automatyzacji do pełnej automatyzacji (lub co najmniej pół automatyzacji).](/microsoft-365/security/defender-endpoint/machine-groups)|
|

## <a name="important-points-about-automation-levels"></a>Ważne kwestie dotyczące poziomów automatyzacji

- Pełna automatyzacja udowodniła, że jest niezawodna, wydajna i bezpieczna, i jest zalecana dla wszystkich klientów. Pełna automatyzacja uwolni krytyczne zasoby zabezpieczeń, dzięki czemu mogą bardziej skoncentrować się na strategicznych inicjatywach.

- Nowe dzierżawy (które zawierają dzierżawy utworzone 16 sierpnia 2020 r. lub później) z usługą Microsoft Defender for Endpoint są domyślnie ustawione na pełną automatyzację.

- Jeśli zespół zabezpieczeń zdefiniował grupy urządzeń z poziomem automatyzacji, te ustawienia nie zostaną zmienione przez nowe ustawienia domyślne, które są obecnie publikowane.

- Możesz zachować domyślne ustawienia automatyzacji lub zmienić je odpowiednio do potrzeb organizacji. Aby zmienić ustawienia, [ustaw poziom automatyzacji](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie funkcji automatycznego badania i rozwiązywania problemów w programie Microsoft Defender dla punktu końcowego](configure-automated-investigations-remediation.md)
- [Odwiedź Centrum akcji](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
