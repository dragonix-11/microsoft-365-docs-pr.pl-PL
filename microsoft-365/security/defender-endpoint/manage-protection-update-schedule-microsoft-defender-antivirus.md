---
title: Planowanie aktualizacji ochrony antywirusowej w usłudze Microsoft Defender
description: Planowanie dnia, godziny i interwału pobierania aktualizacji ochrony
keywords: aktualizacje, punkty odniesienia zabezpieczeń, planowanie aktualizacji
ms.prod: m365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 35f9329756fde82a6ac0762d30041a3d30cd2c8b
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492474"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Zarządzaj harmonogramem pobierania i stosowania aktualizacji ochrony

> [!IMPORTANT]
> Klienci, którzy zastosowali aktualizację aparatu microsoft defender z marca 2022 r **. (1.1.19100.5**), mogli napotkać wysokie wykorzystanie zasobów (procesor CPU i/lub pamięć). Firma Microsoft wydała aktualizację (**1.1.19200.5**), która rozwiązuje błędy wprowadzone we wcześniejszej wersji. Zaleca się, aby klienci zaktualizowali tę nową kompilację aparatu antywirusowego (**1.1.19200.5**). Aby upewnić się, że wszystkie problemy z wydajnością są w pełni rozwiązane, zaleca się ponowne uruchomienie maszyn po zastosowaniu aktualizacji. Aby uzyskać więcej informacji, zobacz [Comiesięczne wersje platformy i aparatu](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender pozwala określić, kiedy powinien wyszukiwać i pobierać aktualizacje.

Aktualizacje punktów końcowych można zaplanować, wykonując następujące czynności:

- Określanie dnia tygodnia w celu sprawdzenia dostępności aktualizacji ochrony
- Określanie interwału sprawdzania dostępności aktualizacji ochrony
- Określanie czasu sprawdzania dostępności aktualizacji ochrony

Możesz również losowo określić czasy, w których każdy punkt końcowy sprawdza i pobiera aktualizacje ochrony. Aby uzyskać więcej informacji, zobacz temat [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) .

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu Configuration Manager

1. W konsoli Endpoint Manager firmy Microsoft otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (kliknij pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do pozycji **Przegląd** \> **zasad ochrony przed złośliwym kodem** **programu Endpoint Protection**\>)

2. Przejdź do sekcji **Aktualizacje analizy zabezpieczeń** .

3. Aby sprawdzić i pobrać aktualizacje w określonym czasie:
      1. Ustaw **opcję Sprawdź aktualizacje analizy zabezpieczeń programu Endpoint Protection w określonym interwale...** na **0**.
      2. Ustaw **opcję Sprawdź aktualizacje analizy zabezpieczeń programu Endpoint Protection codziennie o...** do czasu, kiedy aktualizacje powinny być sprawdzane.
      3
4. Aby sprawdzać i pobierać aktualizacje w ciągłym interwale, ustaw opcję **Sprawdź aktualizacje analizy zabezpieczeń programu Endpoint Protection w określonym interwale...** na liczbę godzin, które powinny wystąpić między aktualizacjami.

5. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu zasady grupy

> [!IMPORTANT]
> Domyślnie wartość "SignatureScheduleDay" jest ustawiona na wartość "8", a wartość "SignatureUpdateInterval" jest ustawiona na wartość "0", więc program antywirusowy Microsoft Defender nie planuje aktualizacji ochrony.
Włączenie tych ustawień spowoduje zastąpienie tego ustawienia domyślnego.

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo do **składników** \> systemu Windows **Program antywirusowy Windows Defender** \> **signature Aktualizacje** i skonfiguruj następujące ustawienia:

    1. Kliknij dwukrotnie ustawienie **Określ dzień tygodnia, aby sprawdzić, czy są dostępne aktualizacje analizy zabezpieczeń** , i ustaw opcję **Włączone**. Wprowadź dzień tygodnia, aby sprawdzić aktualizacje. Kliknij przycisk **OK**.

    2. Kliknij dwukrotnie ustawienie **Określ interwał, aby sprawdzić, czy są dostępne aktualizacje definicji** , i ustaw opcję **Włączone**. Wprowadź liczbę godzin między aktualizacjami. Kliknij przycisk **OK**.

    3. Kliknij dwukrotnie ustawienie **Określ czas sprawdzania dostępności aktualizacji definicji** i ustaw opcję **Włączone**. Wprowadź czas sprawdzania aktualizacji. Czas zależy od czasu lokalnego punktu końcowego. Kliknij przycisk **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania](use-powershell-cmdlets-microsoft-defender-antivirus.md) [poleceń cmdlet programu antywirusowego Microsoft Defender i programu antywirusowego Defender](/powershell/module/defender/) , aby uzyskać więcej informacji na temat używania programu PowerShell z programem antywirusowym Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu instrukcji zarządzania systemem Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujące informacje:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)

## <a name="related-articles"></a>Powiązane artykuły:

- [Wdrażanie programu antywirusowego Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami programu antywirusowego Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10 i 11](microsoft-defender-antivirus-in-windows-10.md)
