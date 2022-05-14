---
title: Planowanie regularnych szybkich i pełnych skanów za pomocą Program antywirusowy Microsoft Defender
description: Konfigurowanie cyklicznych (zaplanowanych) skanów, w tym czasu ich uruchamiania i tego, czy są one uruchamiane jako pełne, czy szybkie skanowanie
keywords: szybkie skanowanie, pełne skanowanie, szybkie i pełne, planowanie skanowania, codziennie, co tydzień, czas, zaplanowane, cykliczne, regularne
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 02/22/2022
ms.reviewer: pauhijbr, ksarens, mkaminska
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: c0dac136b740ba9ff1ddccb5b121a2e2abb2334b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419621"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Konfigurowanie zaplanowanych szybkich lub pełnych skanów Program antywirusowy Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Oprócz zawsze włączonej ochrony w czasie rzeczywistym i skanowania [antywirusowego na żądanie](run-scan-microsoft-defender-antivirus.md) można skonfigurować regularne, zaplanowane skanowania antywirusowe. Można skonfigurować typ skanowania, kiedy powinno nastąpić skanowanie i czy skanowanie powinno nastąpić po [aktualizacji ochrony](manage-protection-updates-microsoft-defender-antivirus.md) lub gdy punkt końcowy nie jest używany. Możesz również skonfigurować specjalne skany, aby w razie potrzeby wykonać akcje korygowania.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Dowiedz się więcej na temat szybkich skanów, pełnych skanów i skanów niestandardowych](#quick-scan-full-scan-and-custom-scan)
- [Planowanie skanowania antywirusowego przy użyciu zasady grupy](schedule-antivirus-scans-group-policy.md)
- [Planowanie skanowania antywirusowego przy użyciu Windows PowerShell](schedule-antivirus-scans-powershell.md)
- [Planowanie skanowania antywirusowego przy użyciu instrumentacji zarządzania Windows](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Należy pamiętać o następujących kwestiach

- Domyślnie Program antywirusowy Microsoft Defender sprawdza dostępność aktualizacji na 15 minut przed rozpoczęciem zaplanowanego skanowania. Możesz [zarządzać harmonogramem pobierania i stosowania aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md) w celu zastąpienia tego ustawienia domyślnego.

- Jeśli urządzenie jest odłączone i uruchomione na baterii podczas zaplanowanego pełnego skanowania, zaplanowane skanowanie zostanie zatrzymane z zdarzeniem 1002, co oznacza, że skanowanie zostało zatrzymane przed zakończeniem. Program antywirusowy Microsoft Defender uruchomi pełne skanowanie w następnym zaplanowanym czasie.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Szybkie skanowanie, pełne skanowanie i skanowanie niestandardowe

Podczas konfigurowania zaplanowanych skanów można określić, czy skanowanie powinno być pełne, czy szybkie. W większości przypadków zalecane jest szybkie skanowanie.

<br/><br/>

|Szybkie skanowanie|Pełne skanowanie|Skanowanie niestandardowe|
|---|---|---|
|(Zalecane) Szybkie skanowanie sprawdza wszystkie lokalizacje, w których może być zarejestrowane złośliwe oprogramowanie, aby rozpocząć pracę z systemem, takie jak klucze rejestru i znane Windows folderów startowych. <br/><br/>W połączeniu z zawsze włączoną ochroną w czasie rzeczywistym, która przegląda pliki po ich otwarciu i zamknięciu oraz za każdym razem, gdy użytkownik przechodzi do folderu, szybkie skanowanie pomaga zapewnić silną ochronę przed złośliwym oprogramowaniem rozpoczynającym się od złośliwego oprogramowania na poziomie systemu i jądra.<br/><br/>W większości przypadków szybkie skanowanie jest wystarczające i jest zalecaną opcją dla zaplanowanych skanów.|Pełne skanowanie rozpoczyna się od uruchomienia szybkiego skanowania, a następnie kontynuuje sekwencyjne skanowanie plików wszystkich zainstalowanych dysków stałych i dysków wymiennych/sieciowych (jeśli skonfigurowano pełne skanowanie).<br/><br/>Pełne skanowanie może potrwać kilka godzin lub dni, w zależności od ilości i typu danych, które należy przeskanować.<br/><br/>Po zakończeniu pełnego skanowania jest dostępna nowa analiza zabezpieczeń, a następnie wymagane jest nowe skanowanie, aby upewnić się, że nie wykryto żadnych innych zagrożeń przy użyciu nowej analizy zabezpieczeń.<br/><br/>Ogólnie rzecz biorąc, ze względu na czas i zasoby związane z pełnym skanowaniem firma Microsoft nie zaleca planowania pełnych skanów.|Skanowanie niestandardowe jest uruchamiane w określonych plikach i folderach. Możesz na przykład wybrać skanowanie dysku USB lub określonego folderu na dysku lokalnym urządzenia.|

> [!NOTE]
> Domyślnie szybkie skanowanie jest uruchamiane na zainstalowanych urządzeniach wymiennych, takich jak dyski USB.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Jak mogę wiedzieć, który typ skanowania wybrać?

Użyj poniższej tabeli, aby wybrać typ skanowania.
<br/><br/>

|Scenariusz|Zalecany typ skanowania|
|---|---|
|Chcesz skonfigurować regularne, zaplanowane skanowanie|Szybkie skanowanie <p> Szybkie skanowanie sprawdza procesy, pamięć, profile i określone lokalizacje na urządzeniu. W połączeniu z [zawsze włączoną ochroną w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) szybkie skanowanie pomaga zapewnić silne pokrycie zarówno złośliwego oprogramowania, które rozpoczyna się od złośliwego oprogramowania na poziomie systemu, jak i złośliwego oprogramowania na poziomie jądra. Ochrona w czasie rzeczywistym przegląda pliki po ich otwarciu i zamknięciu oraz za każdym razem, gdy użytkownik przechodzi do folderu.|
|Zagrożenia, takie jak złośliwe oprogramowanie, są wykrywane na pojedynczym urządzeniu|Szybkie skanowanie <p> W większości przypadków szybkie skanowanie wychwytuje i oczyści wykryte złośliwe oprogramowanie.|
|Chcesz uruchomić [skanowanie na żądanie](run-scan-microsoft-defender-antivirus.md)|Szybkie skanowanie|
|Chcesz upewnić się, że urządzenie przenośne, takie jak dysk USB, nie zawiera złośliwego oprogramowania|Skanowanie niestandardowe <p> Skanowanie niestandardowe umożliwia wybranie określonych lokalizacji, folderów lub plików oraz szybkie skanowanie.|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Co jeszcze muszę wiedzieć o szybkich i pełnych skanowaniach?

- Złośliwe pliki mogą być przechowywane w lokalizacjach, które nie są uwzględnione w szybkim skanowaniu. Jednak zawsze włączona ochrona w czasie rzeczywistym przegląda wszystkie pliki, które są otwierane i zamykane, oraz wszystkie pliki znajdujące się w folderach, do których uzyskuje dostęp użytkownik. Kombinacja ochrony w czasie rzeczywistym i szybkiego skanowania pomaga zapewnić silną ochronę przed złośliwym oprogramowaniem.

- Ochrona przy dostępie przy użyciu [ochrony dostarczanej w chmurze](cloud-protection-microsoft-defender-antivirus.md) pomaga zapewnić, że wszystkie pliki dostępne w systemie są skanowane przy użyciu najnowszych modeli analizy zabezpieczeń i uczenia maszynowego w chmurze.

- Gdy ochrona w czasie rzeczywistym wykrywa złośliwe oprogramowanie, a zakres plików, których dotyczy problem, nie jest początkowo określany, Program antywirusowy Microsoft Defender inicjuje pełne skanowanie w ramach procesu korygowania.

- Pełne skanowanie może wykryć złośliwe pliki, które nie zostały wykryte przez inne skanowania, takie jak szybkie skanowanie. Jednak pełne skanowanie może trochę potrwać i wykorzystać cenne zasoby systemowe do ukończenia.

- Jeśli urządzenie jest w trybie offline przez dłuższy czas, pełne skanowanie może potrwać dłużej.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)