---
title: Rozwiązywanie problemów z ochroną sieci
description: Zasoby i przykładowy kod do rozwiązywania problemów z ochroną sieci w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: rozwiązywanie problemów, błąd, poprawka, windows defender np, asr, reguły, biodra, rozwiązywanie problemów, inspekcja, wykluczenie, fałszywie dodatnie, złamane, blokowanie, Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.openlocfilehash: fbb3a9e038dcd9f342065d538762b41c0673f7e6
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783166"
---
# <a name="troubleshoot-network-protection"></a>Rozwiązywanie problemów z ochroną sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów z [ochroną sieci](network-protection.md), na przykład:

- Ochrona sieci blokuje bezpieczną witrynę internetową (fałszywie dodatnią)
- Ochrona sieci nie blokuje podejrzanej lub znanej złośliwej witryny internetowej (fałszywie negatywnej)

Aby rozwiązać te problemy, należy wykonać cztery kroki:

1. Potwierdzanie wymagań wstępnych
2. Testowanie reguły przy użyciu trybu inspekcji
3. Dodawanie wykluczeń dla określonej reguły (dla wyników fałszywie dodatnich)
4. Przesyłanie dzienników pomocy technicznej

## <a name="confirm-prerequisites"></a>Potwierdzanie wymagań wstępnych

Ochrona sieci będzie działać tylko na urządzeniach z następującymi warunkami:

> [!div class="checklist"]
>
> - Punkty końcowe są uruchomione Windows 10 Pro lub Enterprise wersji 1709 lub nowszej.
> - Punkty końcowe używają Program antywirusowy Microsoft Defender jako jedynej aplikacji ochrony antywirusowej. [Zobacz, co się stanie, gdy korzystasz z rozwiązania antywirusowego](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility) innego niż Microsoft.
> - [Włączono ochronę w czasie rzeczywistym](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) .
> - [Włączono ochronę dostarczaną przez chmurę](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) .
> - Tryb inspekcji nie jest włączony. Użyj [zasady grupy](enable-network-protection.md#group-policy), aby ustawić regułę na **Wyłączone** (wartość: **0**).

## <a name="use-audit-mode"></a>Korzystanie z trybu inspekcji

Możesz włączyć ochronę sieci w trybie inspekcji, a następnie odwiedzić witrynę internetową utworzoną w celu zaprezentowania tej funkcji. Wszystkie połączenia z witryną internetową będą dozwolone przez ochronę sieci, ale zostanie zarejestrowane zdarzenie wskazujące każde połączenie, które zostałoby zablokowane, gdyby włączono ochronę sieci.

1. Ustaw ochronę sieci na **tryb inspekcji**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Wykonaj działanie połączenia, które powoduje problem (na przykład spróbuj odwiedzić witrynę lub połączyć się z adresem IP, który wykonujesz lub nie chcesz blokować).

3. [Przejrzyj dzienniki zdarzeń ochrony sieci,](network-protection.md#review-network-protection-events-in-windows-event-viewer) aby sprawdzić, czy funkcja zablokowałaby połączenie, gdyby została **ustawiona na wartość Włączone**.

   Jeśli ochrona sieci nie blokuje połączenia, które powinno zostać zablokowane, włącz tę funkcję.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Zgłoś wynik fałszywie dodatni lub fałszywie ujemny

Jeśli funkcja została przetestowana w lokacji demonstracyjnej i w trybie inspekcji, a ochrona sieci działa wstępnie skonfigurowanych scenariuszach, ale nie działa zgodnie z oczekiwaniami dla określonego połączenia, użyj [formularza przesyłania opartego na sieci Web analizy zabezpieczeń Windows Defender](https://www.microsoft.com/wdsi/filesubmission), aby zgłosić fałszywie ujemny lub fałszywie dodatni dla ochrony sieci. Za pomocą subskrypcji E5 możesz również [podać link do dowolnego skojarzonego alertu](alerts-queue.md).

Zobacz [Address false positives/negatives in Ochrona punktu końcowego w usłudze Microsoft Defender (Adresowanie fałszywych alarmów/negatywów w Ochrona punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)).

## <a name="add-exclusions"></a>Dodawanie wykluczeń

Bieżące opcje wykluczeń to:

1. Konfigurowanie niestandardowego wskaźnika zezwalania.
2. Korzystanie z wykluczeń adresów IP: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3. Z wyłączeniem całego procesu. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender wykluczenia](configure-exclusions-microsoft-defender-antivirus.md). 

## <a name="collect-diagnostic-data-for-file-submissions"></a>Zbieranie danych diagnostycznych na potrzeby przesyłania plików

Po zgłoszeniu problemu z ochroną sieci zostanie wyświetlony monit o zebranie i przesłanie danych diagnostycznych, które mogą być używane przez zespoły pomocy technicznej i inżynieryjnej firmy Microsoft w celu ułatwienia rozwiązywania problemów.

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i przejdź do katalogu Windows Defender:

   ```console
   cd c:\program files\windows defender
   ```

2. Uruchom to polecenie, aby wygenerować dzienniki diagnostyczne:

   ```console
   mpcmdrun -getfiles
   ```

3. Dołącz plik do formularza przesyłania. Domyślnie dzienniki diagnostyczne są zapisywane pod adresem `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Rozwiązywanie problemów z łącznością z ochroną sieci (dla klientów E5)

Ze względu na środowisko, w którym działa ochrona sieci, firma Microsoft nie może wyświetlić ustawień serwera proxy systemu operacyjnego. W niektórych przypadkach klienci ochrony sieci nie mogą uzyskać dostępu do usługi w chmurze. Aby rozwiązać problemy z łącznością związane z ochroną sieci, skonfiguruj jeden z następujących kluczy rejestru, aby ochrona sieci była świadoma konfiguracji serwera proxy:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Klucz rejestru można skonfigurować przy użyciu programu PowerShell, Microsoft Endpoint Manager lub zasady grupy. Oto kilka zasobów, które pomogą:

- [Praca z kluczami rejestru](/powershell/scripting/samples/working-with-registry-keys)
- [Konfigurowanie niestandardowych ustawień klienta dla Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Zarządzanie Endpoint Protection przy użyciu ustawień zasady grupy](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Zobacz też

- [Ochrona sieci](network-protection.md)
- [Ochrona sieci i trójstopnie uzgadnianie protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Oceń ochronę sieci](evaluate-network-protection.md)
- [Włączanie ochrony sieci](enable-network-protection.md)
- [Adresowanie wyników fałszywie dodatnich/ujemnych w usłudze Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
