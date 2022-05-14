---
title: Planowanie aktualizacji ochrony Program antywirusowy Microsoft Defender
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
ms.openlocfilehash: 5ffa9d623b89bc19c7c3ec8817f2df6bc174384b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419841"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Zarządzaj harmonogramem pobierania i stosowania aktualizacji ochrony

> [!IMPORTANT]
> Klienci, którzy zastosowali aktualizację aparatu microsoft defender z marca 2022 r **. (1.1.19100.5**), mogli napotkać wysokie wykorzystanie zasobów (procesor CPU i/lub pamięć). Firma Microsoft wydała aktualizację (**1.1.19200.5**), która rozwiązuje błędy wprowadzone we wcześniejszej wersji. Zaleca się, aby klienci zaktualizowali tę nową kompilację aparatu antywirusowego (**1.1.19200.5**). Aby upewnić się, że wszystkie problemy z wydajnością są w pełni rozwiązane, zaleca się ponowne uruchomienie maszyn po zastosowaniu aktualizacji. Aby uzyskać więcej informacji, zobacz [Comiesięczne wersje platformy i aparatu](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender pozwala określić, kiedy należy szukać i pobierać aktualizacje.

Aktualizacje punktów końcowych można zaplanować, wykonując następujące czynności:

- Określanie dnia tygodnia w celu sprawdzenia dostępności aktualizacji ochrony
- Określanie interwału sprawdzania dostępności aktualizacji ochrony
- Określanie czasu sprawdzania dostępności aktualizacji ochrony

Możesz również losowo określić czasy, w których każdy punkt końcowy sprawdza i pobiera aktualizacje ochrony. Aby uzyskać więcej informacji, zobacz temat [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) .

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu Configuration Manager

1. W konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (kliknij pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do **pozycji Przegląd** \> **Endpoint Protection** \> **Zasady ochrony przed złośliwym kodem**)

2. Przejdź do sekcji **Aktualizacje analizy zabezpieczeń** .

3. Aby sprawdzić i pobrać aktualizacje w określonym czasie:
      1. Ustaw **opcję Sprawdź, czy Endpoint Protection aktualizacje analizy zabezpieczeń w określonym interwale...** na **0**.
      2. Ustaw **opcję Sprawdź, czy Endpoint Protection aktualizacje analizy zabezpieczeń codziennie o...** do czasu, kiedy aktualizacje powinny być sprawdzane.
      3
4. Aby sprawdzać i pobierać aktualizacje w ciągłym interwale, ustaw opcję **Sprawdź, czy Endpoint Protection aktualizacje analizy zabezpieczeń w określonym interwale...** na liczbę godzin, które powinny wystąpić między aktualizacjami.

5. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu zasady grupy

> [!IMPORTANT]
> Domyślnie wartość "SignatureScheduleDay" jest ustawiona na wartość "8", a wartość "SignatureUpdateInterval" jest ustawiona na wartość "0", więc Program antywirusowy Microsoft Defender nie będzie planować aktualizacji ochrony.
Włączenie tych ustawień spowoduje zastąpienie tego ustawienia domyślnego.

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje analizy podpisów** i skonfiguruj następujące ustawienia:

    1. Kliknij dwukrotnie ustawienie **Określ dzień tygodnia, aby sprawdzić, czy są dostępne aktualizacje analizy zabezpieczeń** , i ustaw opcję **Włączone**. Wprowadź dzień tygodnia, aby sprawdzić aktualizacje. Kliknij przycisk **OK**.
    2. Kliknij dwukrotnie ustawienie **Określ interwał w celu sprawdzenia dostępności aktualizacji analizy zabezpieczeń** i ustaw opcję **Włączone**. Wprowadź liczbę godzin między aktualizacjami. Kliknij przycisk **OK**.
    3. Kliknij dwukrotnie ustawienie **Określ czas sprawdzania dostępności aktualizacji analizy zabezpieczeń** i ustaw opcję **Włączone**. Wprowadź czas sprawdzania aktualizacji. Czas zależy od czasu lokalnego punktu końcowego. Kliknij przycisk **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [poleceń cmdlet programu antywirusowego Defender](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujące informacje:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
