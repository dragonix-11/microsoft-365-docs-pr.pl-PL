---
title: Planuj regularne szybkie i pełne skanowania za pomocą Program antywirusowy Microsoft Defender
description: Konfigurowanie skanowania cyklicznego (zaplanowanego), w tym ich uruchamiania i tego, czy są one uruchamiane jako pełne, czy szybkie
keywords: szybkie skanowanie, pełne skanowanie, szybkie lub pełne, planowanie skanowania, codzienne, tygodniowe, czas, zaplanowane, cykliczne, normalne
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 91e3acee5fb3ab2542c2beed4681f07959e9fe05
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997299"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Konfigurowanie zaplanowanego szybkiego lub pełnego Program antywirusowy Microsoft Defender skanowania

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Oprócz zawsze wł. ochrony w czasie rzeczywistym i skanów [](run-scan-microsoft-defender-antivirus.md) antywirusowych na żądanie możesz skonfigurować regularne, zaplanowane skany antywirusowe. Możesz skonfigurować typ skanowania, czas jego wystąpienia oraz to, czy skanowanie powinno nastąpić po aktualizacji ochrony lub gdy punkt [](manage-protection-updates-microsoft-defender-antivirus.md) końcowy nie jest używany. W razie potrzeby możesz również skonfigurować specjalne skanowania w celu wykonania działań naprawczych.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Dowiedz się więcej o szybkich skanach, pełnych skanach i skanach niestandardowych](#quick-scan-full-scan-and-custom-scan)
- [Planowanie zasady grupy za pomocą programu antywirusowego](schedule-antivirus-scans-group-policy.md)
- [Planowanie Windows PowerShell antywirusowych za pomocą narzędzi do planowania skanów](schedule-antivirus-scans-powershell.md)
- [Planowanie skanów antywirusowych za pomocą narzędzi Windows Management Instrumentation](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Należy pamiętać o następujących kwestiach

- Domyślnie program Program antywirusowy Microsoft Defender na aktualizację 15 minut przed rozpoczęciem każdego zaplanowanego skanowania. Możesz [zarządzać harmonogramem pobierania](manage-protection-update-schedule-microsoft-defender-antivirus.md) i stosowania aktualizacji ochrony, aby zastąpić to ustawienie domyślne.

- Jeśli urządzenie jest odłączone i działa na baterii podczas zaplanowanego pełnego skanowania, zaplanowane skanowanie zostanie zatrzymane na zdarzeniu 1002, co oznacza, że skanowanie zostało zatrzymane przed ukończeniem. Program antywirusowy Microsoft Defender zostanie uruchomione pełne skanowanie w następnym zaplanowanym czasie.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Szybkie skanowanie, pełne skanowanie i skanowanie niestandardowe

Podczas set up scheduled scans, you can specify whether the scan should be a full or quick scan. W większości przypadków zalecane jest szybkie skanowanie.

<br>

****

|Szybkie skanowanie|Pełne skanowanie|Skanowanie niestandardowe|
|---|---|---|
|(Zalecane) Szybkie skanowanie przeszukuje wszystkie lokalizacje, w których zarejestrowano złośliwe oprogramowanie, aby uruchomić system, takie jak klucze rejestru i znane Windows autostartu. <p> W połączeniu z zawsze włączona ochroną w czasie rzeczywistym, która sprawdza pliki po ich otwarciu i zamknięciu oraz zawsze, gdy użytkownik przechodzi do folderu, szybkie skanowanie pomaga zapewnić silną ochronę przed złośliwym oprogramowaniem, które zaczyna się od złośliwego oprogramowania na poziomie systemu i na poziomie kernel. <p> W większości przypadków szybkie skanowanie jest wystarczające i jest zalecaną opcją w przypadku zaplanowanych skanów.|Pełne skanowanie zaczyna się od uruchomienia szybkiego skanowania, a następnie jest kontynuowane kolejne skanowanie pliku wszystkich montowanych dysków stacjonarnych i wymiennych/sieciowych (jeśli do tego jest skonfigurowane pełne skanowanie). <p> Pełne skanowanie może potrwać kilka godzin lub dni, w zależności od ilości i typu danych, które muszą zostać zeskanowane. <p> Po zakończeniu pełnego skanowania są dostępne nowe analizy zabezpieczeń, a następnie wymagane jest nowe skanowanie w celu upewninia się, że dzięki nowej analizie zabezpieczeń nie są wykrywane żadne inne zagrożenia. <p> Ze względu na czas i zasoby związane z pełnym skanowaniem firma Microsoft zasadniczo nie zaleca planowania pełnych skanów.|Skanowanie niestandardowe to szybkie skanowanie uruchamiane na plikach i folderach przez Ciebie określone. Możesz na przykład zdecydować się na zeskanowanie dysku USB lub określonego folderu na dysku lokalnym twojego urządzenia.|
|

> [!NOTE]
> Domyślnie szybkie skanowanie jest uruchamiane na montowanych urządzeniach wymiennych, takich jak dyski USB.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Jak sprawdzić typ skanowania do wyboru?

Użyj poniższej tabeli, aby wybrać typ skanowania.

<br>

****

|Scenariusz|Zalecany typ skanowania|
|---|---|
|Chcesz skonfigurować regularne, zaplanowane skanowania|Szybkie skanowanie <p> Szybkie skanowanie sprawdza procesy, pamięć, profile i niektóre lokalizacje na urządzeniu. W połączeniu [z zawsze włączona ochroną w](configure-real-time-protection-microsoft-defender-antivirus.md) czasie rzeczywistym szybkie skanowanie pomaga zapewnić silną ochronę zarówno przed złośliwym oprogramowaniem, które zaczyna się od systemu, jak i złośliwego oprogramowania na poziomie kernel. Ochrona w czasie rzeczywistym sprawdza pliki po ich otwarciu i zamknięciu oraz zawsze, gdy użytkownik przechodzi do folderu.|
|Zagrożenia, takie jak złośliwe oprogramowanie, są wykrywane na poszczególnych urządzeniach|Szybkie skanowanie <p> W większości przypadków szybkie skanowanie spowoduje wykrycie złośliwego oprogramowania i jego oczyszczenie.|
|Chcesz uruchomić skanowanie [na żądanie](run-scan-microsoft-defender-antivirus.md)|Szybkie skanowanie|
|Chcesz się upewnić, że urządzenie przenośne, takie jak dysk USB, nie zawiera złośliwego oprogramowania|Skanowanie niestandardowe <p> Skanowanie niestandardowe umożliwia wybranie konkretnych lokalizacji, folderów lub plików oraz szybkie skanowanie.|
|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Co jeszcze należy wiedzieć o szybkich i pełnych skanach?

- Złośliwe pliki mogą być przechowywane w lokalizacjach, które nie są uwzględnione w szybkim skanie. Jednak zawsze w on-time protection reviews all files that are opened and closed, and any files that are in folders that are accessed by a user. Połączenie ochrony w czasie rzeczywistym i szybkiego skanowania pomaga zapewnić silną ochronę przed złośliwym oprogramowaniem.

- Ochrona dostępu przy użyciu ochrony [](cloud-protection-microsoft-defender-antivirus.md) w chmurze pomaga zapewnić, że wszystkie pliki dostępne w systemie są skanowane za pomocą najnowszych analiz zabezpieczeń i modeli maszynowego uczenia w chmurze.

- Gdy ochrona w czasie rzeczywistym wykrywa złośliwe oprogramowanie i zakres plików, których dotyczy problem, nie jest wstępnie określony, program Program antywirusowy Microsoft Defender inicjuje pełne skanowanie w ramach procesu rozwiązywania problemów.

- Pełne skanowanie umożliwia wykrywanie złośliwych plików, które nie zostały wykryte w innych skanach, takich jak szybkie skanowanie. Jednak pełne skanowanie może trochę potrwać i warto skorzystać z cennych zasobów systemowych.

- Jeśli urządzenie jest w trybie offline przez dłuższy czas, pełne skanowanie może trwać dłużej.
