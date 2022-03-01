---
title: Rozwiązywanie problemów z ochroną sieci
description: Zasoby i przykładowy kod do rozwiązywania problemów z ochroną sieci w programie Microsoft Defender for Endpoint.
keywords: troubleshoot, error, fix, windows defender eg, asr, rules, hips, troubleshoot, audit, exclusion, false positive, broken, blocking, Microsoft Defender for Endpoint
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 169a05fdde96ec780bf5e626d81846c9c2d37f26
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997807"
---
# <a name="troubleshoot-network-protection"></a>Rozwiązywanie problemów z ochroną sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów z [ochroną sieci](network-protection.md) w takich przypadkach, jak:

- Ochrona sieci blokuje bezpieczną witrynę sieci Web (wynik fałszywie dodatni)
- Ochrona sieci nie blokuje podejrzanej lub znanej złośliwej witryny internetowej (wynik fałszywie ujemny)

Rozwiązywanie tych problemów można rozwiązać w czterech krokach:

1. Potwierdź wymagania wstępne
2. Testowanie reguły przy użyciu trybu inspekcji
3. Dodawanie wykluczeń określonej reguły (dla wyników fałszywie dodatnich)
4. Przesyłanie dzienników pomocy technicznej

## <a name="confirm-prerequisites"></a>Potwierdź wymagania wstępne

Ochrona sieci będzie działać tylko na urządzeniach z następującymi warunkami:

> [!div class="checklist"]
>
> - Punkty końcowe są uruchomione Windows 10 Pro lub Enterprise, w wersji 1709 lub wyższej.
> - Punkty końcowe są używania Program antywirusowy Microsoft Defender jako jedynej aplikacji ochrony antywirusowej. [Zobacz, co się stanie, jeśli używasz rozwiązania antywirusowego firmy innych niż Microsoft](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).
> - [Jest włączona ochrona w](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) czasie rzeczywistym.
> - [Włączona jest ochrona w](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) chmurze.
> - Tryb inspekcji nie jest włączony. Użyj [zasady grupy](enable-network-protection.md#group-policy) , aby ustawić dla reguły wartość **Wyłączone** (wartość: **0**).

## <a name="use-audit-mode"></a>Korzystanie z trybu inspekcji

Możesz włączyć ochronę sieci w trybie inspekcji, a następnie odwiedzić utworzoną przez nas witrynę internetową, aby zobaczyć pokaz tej funkcji. Wszystkie połączenia witryny sieci Web będą dozwolone przez ochronę sieci, ale zostanie zarejestrowane zdarzenie wskazujące na każde połączenie, które zostałoby zablokowane, jeśli ochrona sieci została włączona.

1. Ustaw ochronę sieci na **wartość Tryb inspekcji**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Wykonaj działanie połączenia, które powoduje problem (na przykład spróbuj odwiedzić witrynę lub połączyć się z adresem IP, który chcesz lub których nie chcesz blokować).

3. [Przejrzyj dzienniki zdarzeń ochrony sieci,](network-protection.md#review-network-protection-events-in-windows-event-viewer) aby sprawdzić, czy funkcja nie zablokowałaby połączenia, jeśli zostałaby ustawiona na wartość **Włączone**.

   Jeśli ochrona sieci nie blokuje połączenia, którego oczekujesz, powinno zostać zablokowane, włącz tę funkcję.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Zgłaszanie wyników fałszywie dodatnich lub ujemnych

Jeśli funkcja została przetestowana w witrynie pokazowej i w trybie inspekcji, a ochrona sieci pracuje nad wstępnie skonfigurowanymi scenariuszami, ale nie działa zgodnie z oczekiwaniami w przypadku określonego połączenia, użyj formularza przesyłania opartego na sieci Web analizy zabezpieczeń usługi [Windows Defender](https://www.microsoft.com/wdsi/filesubmission), aby zgłosić wyniki fałszywie ujemne lub fałszywie dodatnie dla ochrony sieci. W przypadku subskrypcji E5 możesz także podać [link do dowolnego skojarzonego alertu](alerts-queue.md).

Zobacz [Adres dla wartości fałszywie dodatnich/ujemnych w programie Microsoft Defender, aby uzyskać informacje na temat punktu końcowego](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>Dodawanie wykluczeń
Bieżące opcje wykluczeń są następujące:

1.  Konfigurowanie niestandardowego wskaźnika zezwalania.
2.  Korzystanie z wykluczeń IP: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3.  Wykluczanie całego procesu. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender wykluczenia](configure-exclusions-microsoft-defender-antivirus.md). 


## <a name="collect-diagnostic-data-for-file-submissions"></a>Zbieranie danych diagnostycznych dla przesyłania plików

Podczas zgłaszania problemu z ochroną sieci jest proszony o zbieranie i przesyłanie danych diagnostycznych, które mogą być używane przez zespoły pomocy technicznej i inżynierów firmy Microsoft w celu rozwiązania problemów.

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i zmień go na Windows Defender wiersza:

   ```console
   cd c:\program files\windows defender
   ```

2. Uruchom to polecenie, aby wygenerować dzienniki diagnostyczne:

   ```console
   mpcmdrun -getfiles
   ```

3. Dołącz plik do formularza przesyłania. Domyślnie dzienniki diagnostyczne są zapisywane w `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Rozwiązywanie problemów z łącznością przy użyciu ochrony sieci (dla klientów usługi E5)

Ze względu na to, że w środowisku, w którym jest uruchomiona ochrona sieci, firma Microsoft nie może zobaczyć ustawień serwera proxy systemu operacyjnego. W niektórych przypadkach klienci ochrony sieci nie mogą uzyskać dostępu do usługi w chmurze. Aby rozwiązać problemy z łącznością przy użyciu ochrony sieci, skonfiguruj jeden z następujących kluczy rejestru, aby ochrona sieci wiedziała o konfiguracji serwera proxy:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Klucz rejestru można skonfigurować przy użyciu programu PowerShell, Microsoft Endpoint Manager lub zasady grupy. Oto kilka pomocnych zasobów:

- [Praca z kluczami rejestru](/powershell/scripting/samples/working-with-registry-keys)
- [Konfigurowanie niestandardowych ustawień klienta dla Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Zarządzanie zasady grupy za pomocą Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Zobacz też

- [Ochrona sieci](network-protection.md)
- [Ochrona sieci i trójkierunkowy uścisk dłoni protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Ocenianie ochrony sieci](evaluate-network-protection.md)
- [Włączanie ochrony sieci](enable-network-protection.md)
- [Adres dla wartości fałszywie dodatnich/ujemnych w programie Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md)
