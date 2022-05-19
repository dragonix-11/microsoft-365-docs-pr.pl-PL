---
title: Poziomy automatyzacji w zautomatyzowanym badaniu i korygowaniu
description: Omówienie poziomów automatyzacji i sposobu ich pracy w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: zautomatyzowane, badanie, poziom, Ochrona punktu końcowego w usłudze Microsoft Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: e36bcdd5851b64ec035eaf8e4e3961c14df5c535
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535829"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Poziomy automatyzacji w możliwościach zautomatyzowanego badania i korygowania

**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md)

Funkcje zautomatyzowanego badania i korygowania (AIR) w Microsoft Defender dla Firm są wstępnie skonfigurowane i nie można ich konfigurować. W Ochrona punktu końcowego w usłudze Microsoft Defender można skonfigurować funkcję AIR na jednym z kilku poziomów automatyzacji. Poziom automatyzacji ma wpływ na to, czy akcje korygowania po badaniach air są wykonywane automatycznie, czy tylko po zatwierdzeniu.

- *Pełna automatyzacja* (zalecane) oznacza, że akcje korygowania są wykonywane automatycznie na artefaktach uznanych za złośliwe. (*Pełna automatyzacja jest domyślnie ustawiana w usłudze Defender dla firm*).
- *Półautomatyczne* oznacza, że niektóre akcje korygowania są wykonywane automatycznie, ale inne akcje korygowania czekają na zatwierdzenie przed podjęciem. (Zobacz tabelę [w temacie Poziomy automatyzacji](#levels-of-automation)).
- Wszystkie akcje korygowania, oczekujące lub zakończone, są śledzone w Centrum akcji ([https://security.microsoft.com](https://security.microsoft.com)).

> [!TIP]
> Aby uzyskać najlepsze wyniki, zalecamy używanie pełnej automatyzacji podczas [konfigurowania środowiska AIR](configure-automated-investigations-remediation.md). Dane zebrane i przeanalizowane w ciągu ostatniego roku pokazują, że klienci korzystający z pełnej automatyzacji usunęli o 40% więcej próbek złośliwego oprogramowania o wysokim stopniu zaufania niż klienci korzystający z niższych poziomów automatyzacji. Pełna automatyzacja może pomóc zwolnić zasoby operacji zabezpieczeń, aby skupić się bardziej na strategicznych inicjatywach.

## <a name="levels-of-automation"></a>Poziomy automatyzacji

|Poziom automatyzacji|Opis|
|---|---|
|**Pełne — automatyczne korygowanie zagrożeń** <br> (nazywane również *pełną automatyzacją*)|W przypadku pełnej automatyzacji akcje korygowania są wykonywane automatycznie. Wszystkie podjęte akcje korygowania można wyświetlić w [Centrum akcji](auto-investigation-action-center.md) na karcie **Historia** . W razie potrzeby można cofnąć akcję korygowania. <p> **_Zalecana jest pełna automatyzacja_* i jest domyślnie wybierana dla dzierżaw z usługą Defender for Endpoint, które zostały utworzone 16 sierpnia 2020 r. lub później, bez zdefiniowanych jeszcze grup urządzeń.*<p>*Pełna automatyzacja jest domyślnie ustawiana w usłudze Defender dla firm.*|
|**Semi — wymaga zatwierdzenia dla wszelkich działań korygowania** <br> (nazywane również *półautomatycznym*)|Na tym poziomie automatyzacji półautomatycznej zatwierdzenie jest wymagane w *przypadku dowolnej* akcji korygowania. Takie oczekujące akcje można wyświetlić i zatwierdzić w [Centrum akcji](auto-investigation-action-center.md) na karcie **Oczekujące** . <p> *Ten poziom automatyzacji półautomatycznej jest domyślnie wybierany dla dzierżaw utworzonych przed 16 sierpnia 2020 r. z Ochrona punktu końcowego w usłudze Microsoft Defender bez zdefiniowanych grup urządzeń.*|
|**Semi — wymaga zatwierdzenia korygowania folderów podstawowych** <br> (również typ *pół automatyzacji*)|Na tym poziomie automatyzacji półautomatycznej zatwierdzenie jest wymagane w przypadku wszelkich akcji korygowania wymaganych w plikach lub plikach wykonywalnych znajdujących się w folderach podstawowych. Foldery podstawowe obejmują katalogi systemu operacyjnego, takie jak **Windows** (`\windows\*`). <p> Akcje korygowania mogą być wykonywane automatycznie w plikach lub plikach wykonywalnych znajdujących się w innych (nierdzeniowych) folderach. <p> Oczekujące akcje dla plików lub plików wykonywalnych w folderach podstawowych można wyświetlać i zatwierdzać w [Centrum akcji](auto-investigation-action-center.md) na karcie **Oczekujące** . <p> Akcje, które zostały wykonane w plikach lub plikach wykonywalnych w innych folderach, można wyświetlić w [Centrum akcji](auto-investigation-action-center.md) na karcie **Historia** .|
|**Semi — wymaga zatwierdzenia korygowania folderów innych niż temp** <br> (również typ *pół automatyzacji*)|W przypadku tego poziomu automatyzacji półautomatycznej zatwierdzenie jest wymagane w przypadku wszelkich akcji korygowania wymaganych w plikach lub plikach wykonywalnych, które *nie* znajdują się w folderach tymczasowych. <p> Foldery tymczasowe mogą zawierać następujące przykłady: <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Akcje korygowania mogą być wykonywane automatycznie w plikach lub plikach wykonywalnych znajdujących się w folderach tymczasowych. <p> Oczekujące akcje dla plików lub plików wykonywalnych, które nie znajdują się w folderach tymczasowych, można wyświetlić i zatwierdzić w [Centrum akcji](auto-investigation-action-center.md) na karcie **Oczekujące** . <p> Akcje wykonywane w plikach lub plikach wykonywalnych w folderach tymczasowych można wyświetlać i zatwierdzać w [Centrum akcji](auto-investigation-action-center.md) na karcie **Historia** .|
|**Brak automatycznej odpowiedzi** <br> (określane również jako *brak automatyzacji*)|Bez automatyzacji automatyczne badanie nie jest uruchamiane na urządzeniach organizacji. W związku z tym w wyniku zautomatyzowanego badania nie są podejmowane żadne akcje korygowania ani oczekujące na nie. Jednak inne funkcje ochrony przed zagrożeniami, takie jak [ochrona przed potencjalnie niepożądanymi aplikacjami](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus), mogą obowiązywać w zależności od sposobu konfigurowania programu antywirusowego i funkcji ochrony nowej generacji. <p> ***Korzystanie z opcji *brak automatyzacji* nie jest zalecane**, ponieważ zmniejsza stan zabezpieczeń urządzeń w organizacji. [Rozważ skonfigurowanie poziomu automatyzacji w celu pełnej automatyzacji (lub co najmniej częściowo automatyzacji).](/microsoft-365/security/defender-endpoint/machine-groups)|

## <a name="important-points-about-automation-levels"></a>Ważne punkty dotyczące poziomów automatyzacji

- Pełna automatyzacja okazała się niezawodna, wydajna i bezpieczna i jest zalecana dla wszystkich klientów. Pełna automatyzacja zwalnia krytyczne zasoby zabezpieczeń, dzięki czemu mogą bardziej skupić się na twoich strategicznych inicjatywach.

- Nowe dzierżawy (w tym dzierżawy utworzone 16 sierpnia 2020 r. lub później) w usłudze Defender for Endpoint są domyślnie ustawione na pełną automatyzację.

- [Usługa Defender dla firm](../defender-business/compare-mdb-m365-plans.md) domyślnie używa pełnej automatyzacji. Usługa Defender dla firm nie używa grup urządzeń w taki sam sposób jak usługa Defender dla firm. W związku z tym pełna automatyzacja jest włączana i stosowana do wszystkich urządzeń w usłudze Defender dla Firm.

- Jeśli zespół ds. zabezpieczeń zdefiniował grupy urządzeń z poziomem automatyzacji, te ustawienia nie zostaną zmienione przez nowe ustawienia domyślne, które są wdrażane.

- Możesz zachować domyślne ustawienia automatyzacji lub zmienić je zgodnie z potrzebami organizacji. Aby zmienić ustawienia, [ustaw poziom automatyzacji](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie możliwości zautomatyzowanego badania i korygowania w usłudze Defender for Endpoint](configure-automated-investigations-remediation.md)
- [Odwiedź Centrum akcji](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
