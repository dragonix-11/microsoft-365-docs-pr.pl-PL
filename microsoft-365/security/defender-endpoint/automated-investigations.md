---
title: Używanie zautomatyzowanych analiz w celu zbadania i rozwiązania problemów związanych z zagrożeniami
description: Zrozumienie zautomatyzowanego przepływu badania w programie Microsoft Defender for Endpoint.
keywords: zautomatyzowane, badania, wykrywanie, usługa Microsoft Defender dla punktu końcowego
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
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
ms.openlocfilehash: 547356fadc05c2359b4c6cd639bc22110bf8be93
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013832"
---
# <a name="overview-of-automated-investigations"></a>Omówienie zautomatyzowanych badań

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz zobaczyć, jak to działa? Obejrzyj poniższy klip wideo:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

Technologia w automatycznym śledztwie używa różnych algorytmów inspekcji i jest oparta na procesach, które są używane przez analityków zabezpieczeń. Funkcje AIR są przeznaczone do badania alertów i natychmiastowego podjęcia działań w celu rozwiązania problemów z naruszeniem zabezpieczeń. Funkcje AIR znacznie zmniejszają liczbę alertów, umożliwiając operacje zabezpieczeń koncentracji na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokiej wartości. Wszystkie akcje naprawcze, zarówno oczekujące, jak i zakończone, są śledzone w [Centrum akcji](auto-investigation-action-center.md). W Centrum akcji oczekujące akcje są zatwierdzane (lub odrzucane), a w razie potrzeby można cofnąć wykonane akcje.

Ten artykuł zawiera omówienie funkcji AIR oraz linki do następnych kroków i dodatkowych zasobów.

> [!TIP]
> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Jak rozpoczyna się automatyczne badanie

Zautomatyzowane badanie może się rozpocząć po wyzwoleniu alertu lub rozpoczęciu badania przez operatora zabezpieczeń.

<br>

****

|Sytuacja|Co się dzieje|
|---|---|
|Zostanie wyzwolony alert|Na ogół automatyczne badanie jest rozpoczynane po wyzwoleniu [alertu](review-alerts.md) i [utworzeniu](view-incidents-queue.md) zdarzenia. Załóżmy na przykład, że złośliwy plik znajduje się na urządzeniu. Po wykryciu tego pliku jest wyzwolony alert i jest tworzone zdarzenie. Na urządzeniu rozpoczyna się zautomatyzowany proces badania. W związku z tym, że inne alerty są generowane z powodu tego samego pliku na innych urządzeniach, są one dodawane do skojarzonego zdarzenia i do automatycznego badania.|
|Ręczne rozpoczynanie badania|Zespół operacyjny zabezpieczeń może uruchomić automatyczne badanie. Załóżmy na przykład, że operator zabezpieczeń przegląda listę urządzeń i zauważa, że urządzenie jest o wysokim poziomie ryzyka. Operator zabezpieczeń może wybrać urządzenie na liście, aby otworzyć jego wysunięcie, a następnie wybrać pozycję **Zainicjuj automatyczne badanie**.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Jak automatyczne badanie rozszerza zakres

Gdy jest uruchomione badanie, wszystkie inne alerty wygenerowane z urządzenia są dodawane do trwającego automatycznego badania do czasu jego ukończenia. Ponadto, jeśli to samo zagrożenie będzie widoczne na innych urządzeniach, zostaną one dodane do badania.

Jeśli podmiot incri pochłonie się na innym urządzeniu, proces automatycznego badania rozszerzy zakres, tak aby uwzględnić to urządzenie, a na tym urządzeniu zostanie uruchomiony ogólny podręcznik zabezpieczeń. Jeśli w ramach tego procesu rozszerzania tej samej jednostki znajduje się co najmniej 10 urządzeń, akcja rozszerzenia wymaga zatwierdzenia i jest widoczna na karcie **Oczekujące** akcje.

## <a name="how-threats-are-remediated"></a>Jak są korygowane zagrożenia

W związku z wyzwalanie alertów i uruchomieniem automatycznego badania jest generowany werdykt dla każdego dowodu, który został zbadany. Werdykty mogą być:

- *Złośliwy*;
- *Podejrzane*; lub
- *Nie znaleziono zagrożeń*.

Po osiągnięciu werdyktów zautomatyzowane badania mogą doprowadzić do co najmniej jednej akcji naprawczej. Przykłady działań naprawczych, takich jak wysłanie pliku do kwarantanny, zatrzymanie usługi, usunięcie zaplanowanego zadania i nie tylko. Aby dowiedzieć się więcej, zobacz [Działania naprawcze](manage-auto-investigation.md#remediation-actions).

W zależności od [poziomu zestawu automatyzacji](automation-levels.md) dla organizacji i innych ustawień zabezpieczeń działania naprawcze mogą być wykonywane automatycznie lub tylko po zatwierdzeniu ich przez zespół operacyjny zabezpieczeń. Dodatkowe ustawienia zabezpieczeń, które mogą mieć wpływ na automatyczne rozwiązywanie problemów, obejmują [ochronę przed potencjalnie niechcianymi aplikacjami](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) .

Wszystkie akcje naprawcze, zarówno oczekujące, jak i zakończone, są śledzone w [Centrum akcji](auto-investigation-action-center.md). W razie potrzeby zespół operacyjny zabezpieczeń może cofnąć działanie naprawcze. Aby dowiedzieć się więcej, zobacz [Przeglądanie i zatwierdzanie działań naprawczych prowadzonych w ramach automatycznego badania](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Zapoznaj się z nową, ujednoliconą stroną badania w portalu Microsoft 365 Defender użytkowników. Aby dowiedzieć się więcej, zobacz [(NOWY!) Ujednolicona strona badania](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>Wymagania dotyczące środowiska AIR

Twoja organizacja musi mieć program Defender for Endpoint (zobacz [Minimalne wymagania programu Microsoft Defender dla punktu końcowego](minimum-requirements.md).

Obecnie program AIR obsługuje tylko następujące wersje systemu operacyjnego:

- Windows Server 2012 R2 (wersja zapoznawcza)
- Windows Server 2016 (wersja zapoznawcza)
- Windows Server 2019
- Windows Server 2022
- Windows 10, wersja 1709 (kompilacja systemu operacyjnego 16299.1085 z [kb4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) lub nowsza
- Windows 10, wersja 1803 (kompilacja systemu operacyjnego 17134.704 z [kb4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) lub nowsza
- Windows 10, wersja [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) lub nowsza
- Windows 11

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o poziomach automatyzacji](automation-levels.md)
- [Zobacz interakcyjny przewodnik: Badanie i rozwiązywanie problemów związanych z zagrożeniami za pomocą programu Microsoft Defender for Endpoint](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Konfigurowanie funkcji automatycznego badania i rozwiązywania problemów w programie Microsoft Defender dla punktu końcowego](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Zobacz też

- [Ochrona pua](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Automatyczne badanie i reagowanie w programie Microsoft Defender dla Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
