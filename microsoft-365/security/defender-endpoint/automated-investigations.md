---
title: Używanie zautomatyzowanych badań do badania i korygowania zagrożeń
description: Omówienie zautomatyzowanego przepływu badania w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: zautomatyzowane, badanie, wykrywanie, Ochrona punktu końcowego w usłudze Microsoft Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 11/24/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: eadf9fe7f6112d1219f085662686b2a930b3ff28
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789805"
---
# <a name="overview-of-automated-investigations"></a>Omówienie zautomatyzowanych badań

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Chcesz zobaczyć, jak to działa? Obejrzyj następujące wideo:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

Technologia zautomatyzowanego badania wykorzystuje różne algorytmy inspekcji i jest oparta na procesach używanych przez analityków zabezpieczeń. Możliwości AIR mają na celu zbadanie alertów i podjęcie natychmiastowych działań w celu rozwiązania problemów z naruszeniami. Możliwości AIR znacznie zmniejszają liczbę alertów, dzięki czemu operacje zabezpieczeń koncentrują się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokiej wartości. Wszystkie akcje korygowania, oczekujące lub ukończone, są śledzone w [centrum akcji](auto-investigation-action-center.md). W centrum akcji oczekujące akcje są zatwierdzane (lub odrzucane), a ukończone akcje można cofnąć w razie potrzeby.

Ten artykuł zawiera omówienie funkcji AIR i zawiera linki do następnych kroków i dodatkowych zasobów.

> [!TIP]
> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Jak rozpoczyna się zautomatyzowane badanie

Zautomatyzowane badanie może rozpocząć się po wyzwoleniu alertu lub zainicjowaniu badania przez operatora zabezpieczeń.

<br>

****

|Sytuacji|Efekt|
|---|---|
|Wyzwalany jest alert|Ogólnie rzecz biorąc, automatyczne badanie rozpoczyna się po wyzwoleniu [alertu](review-alerts.md) i utworzeniu [zdarzenia](view-incidents-queue.md) . Załóżmy na przykład, że na urządzeniu znajduje się złośliwy plik. Po wykryciu tego pliku zostanie wyzwolony alert i zostanie utworzone zdarzenie. Na urządzeniu rozpoczyna się zautomatyzowany proces badania. Ponieważ inne alerty są generowane z powodu tego samego pliku na innych urządzeniach, są one dodawane do skojarzonego zdarzenia i do zautomatyzowanego badania.|
|Badanie jest uruchamiane ręcznie|Zautomatyzowane badanie może zostać uruchomione ręcznie przez zespół ds. operacji zabezpieczeń. Załóżmy na przykład, że operator zabezpieczeń przegląda listę urządzeń i zauważa, że urządzenie ma wysoki poziom ryzyka. Operator zabezpieczeń może wybrać urządzenie na liście, aby otworzyć wysuwane urządzenie, a następnie wybrać pozycję **Inicjuj zautomatyzowane badanie**.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Jak zautomatyzowane badanie rozszerza jego zakres

Gdy badanie jest uruchomione, wszystkie inne alerty wygenerowane na urządzeniu są dodawane do trwającego zautomatyzowanego badania do czasu zakończenia tego badania. Ponadto jeśli to samo zagrożenie jest widoczne na innych urządzeniach, te urządzenia zostaną dodane do badania.

Jeśli na innym urządzeniu jest widoczna obciążana jednostka, zautomatyzowany proces badania rozszerza swój zakres w celu uwzględnienia tego urządzenia, a na tym urządzeniu zostanie uruchomiony ogólny podręcznik zabezpieczeń. Jeśli podczas tego procesu rozszerzania zostanie znalezionych co najmniej 10 urządzeń z tej samej jednostki, ta akcja rozszerzenia wymaga zatwierdzenia i jest widoczna na karcie **Oczekujące akcje** .

## <a name="how-threats-are-remediated"></a>Jak są korygowane zagrożenia

Po wyzwoleniu alertów i uruchomieniu zautomatyzowanego dochodzenia dla każdego badanego dowodu jest generowany werdykt. Werdykty mogą być:

- *Złośliwe*;
- *Podejrzane*; Lub
- *Nie znaleziono zagrożeń*.

Po osiągnięciu werdyktów zautomatyzowane badania mogą skutkować co najmniej jednym działaniem korygacyjnym. Przykłady akcji korygowania obejmują wysyłanie pliku do kwarantanny, zatrzymywanie usługi, usuwanie zaplanowanego zadania i nie tylko. Aby dowiedzieć się więcej, zobacz [Akcje korygowania](manage-auto-investigation.md#remediation-actions).

W zależności od [poziomu automatyzacji ustawionego](automation-levels.md) dla organizacji oraz innych ustawień zabezpieczeń akcje korygowania mogą być wykonywane automatycznie lub tylko po zatwierdzeniu przez zespół ds. operacji zabezpieczeń. Dodatkowe ustawienia zabezpieczeń, które mogą mieć wpływ na automatyczne korygowanie, obejmują [ochronę przed potencjalnie niechcianych aplikacji](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) (PUA).

Wszystkie akcje korygowania, oczekujące lub ukończone, są śledzone w [centrum akcji](auto-investigation-action-center.md). W razie potrzeby zespół ds. operacji zabezpieczeń może cofnąć akcję korygowania. Aby dowiedzieć się więcej, zobacz [Przeglądanie i zatwierdzanie akcji korygowania po zautomatyzowanym badaniu](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Zapoznaj się z nową, ujednoliconą stroną badania w portalu Microsoft 365 Defender. Aby dowiedzieć się więcej, zobacz [(NOWY!) Ujednolicona strona badania](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>Wymagania dotyczące air

Twoja organizacja musi mieć usługę Defender for Endpoint (zobacz [Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender](minimum-requirements.md)).

> [!NOTE]
> Zautomatyzowane badanie i reagowanie wymaga Program antywirusowy Microsoft Defender do uruchamiania w trybie pasywnym lub aktywnym. Jeśli Program antywirusowy Microsoft Defender zostanie wyłączona lub odinstalowana, automatyczne badanie i odpowiedź nie będą działać poprawnie.

Obecnie usługa AIR obsługuje tylko następujące wersje systemu operacyjnego:

- Windows Server 2012 R2 (wersja zapoznawcza)
- Windows Server 2016 (wersja zapoznawcza)
- Windows Server 2019
- Windows Server 2022
- Windows 10, wersja 1709 (kompilacja systemu operacyjnego 16299.1085 z [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) lub nowsza
- Windows 10, wersja 1803 (kompilacja systemu operacyjnego 17134.704 z [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) lub nowsza
- Windows 10, wersja [1803 lub nowsza](/windows/release-information/status-windows-10-1809-and-windows-server-2019)
- Windows 11

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o poziomach automatyzacji](automation-levels.md)
- [Zobacz interaktywny przewodnik: Badanie i korygowanie zagrożeń za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Konfigurowanie możliwości zautomatyzowanego badania i korygowania w Ochrona punktu końcowego w usłudze Microsoft Defender](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Zobacz też

- [Ochrona pua](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Zautomatyzowane badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security/office-365-air)
- [Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
