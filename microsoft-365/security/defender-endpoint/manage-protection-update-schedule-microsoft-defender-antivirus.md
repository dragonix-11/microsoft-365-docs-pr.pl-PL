---
title: Planowanie Program antywirusowy Microsoft Defender aktualizacji ochrony
description: Planowanie dnia, godzin i interwału pobierania aktualizacji ochrony
keywords: aktualizacje, plany bazowe zabezpieczeń, planowanie aktualizacji
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
ms.openlocfilehash: fa67ff12ecfc2fb97bbc50642a5d7db99df91819
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997223"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Zarządzanie harmonogramem pobierania i stosowania aktualizacji ochrony

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program antywirusowy Microsoft Defender pozwala określić, kiedy należy szukać i pobierać aktualizacje.

Możesz zaplanować aktualizacje dla punktów końcowych, korzystając z tych funkcji:

- Określanie dnia tygodnia, w który mają być sprawdzane aktualizacje dotyczące ochrony
- Określanie interwału sprawdzania aktualizacji ochrony
- Określanie czasu sprawdzania aktualizacji ochrony

Możesz także losowo określić czas, w którym poszczególne testy końcowe i aktualizacje ochrony przed pobraniem są przeprowadzane. Aby uzyskać [więcej informacji, zobacz temat Planowanie](scheduled-catch-up-scans-microsoft-defender-antivirus.md) skanowania.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Planowanie aktualizacji Menedżer konfiguracji za pomocą funkcji aktualizacji ochrony

1. Na konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym oprogramowaniem, które chcesz zmienić (kliknij pozycję Zasoby i zgodność  w okienku nawigacji po lewej stronie,  \> a następnie rozwiń drzewo do okna Omówienie **Endpoint Protection** \> zasady ochrony przed złośliwym **oprogramowaniem)**

2. Przejdź do sekcji **Aktualizacje analizy zabezpieczeń** .

3. Aby sprawdzić i pobrać aktualizacje o określonej godzinie:
      1. Ustaw **dla ustawienia Sprawdź Endpoint Protection aktualizacji analizy zabezpieczeń w określonym interwale...** wartość **0**.
      2. Ustaw **ustawienie Sprawdź Endpoint Protection aktualizacji analizy zabezpieczeń codziennie o godzinie,** kiedy aktualizacje powinny być sprawdzane.
      3
4. Aby sprawdzać i pobierać aktualizacje w ciągłym interwale, ustaw ustawienie Sprawdź aktualizacje analizy zabezpieczeń Endpoint Protection w określonym interwale **czasu na** liczbę godzin, która powinna nastąpić między aktualizacjami.

5. [Wdeksuj zaktualizowane zasady w zwykły sposób](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Planowanie aktualizacji zasady grupy za pomocą funkcji aktualizacji ochrony

> [!IMPORTANT]
> Domyślnie program Program antywirusowy Microsoft Defender sprawdza aktualizację 15 minut przed rozpoczęciem wszystkich zaplanowanych skanów. Włączenie tych ustawień spowoduje zastąpienie tego ustawienia domyślnego.

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **aktualizacje analizy podpisów** i skonfiguruj następujące ustawienia:

    1. Kliknij dwukrotnie ustawienie **Określ dzień** tygodnia, aby sprawdzić, czy są dostępne aktualizacje analizy zabezpieczeń, i ustaw dla tej opcji wartość **Włączone**. Wprowadź dzień tygodnia, aby sprawdzić aktualizacje. Kliknij przycisk **OK**.
    2. Kliknij dwukrotnie ustawienie **Określ interwał** sprawdzania, czy aktualizacje analizy zabezpieczeń mają być sprawdzane, i ustaw opcję **Włączone**. Wprowadź liczbę godzin między aktualizacjami. Kliknij przycisk **OK**.
    3. Kliknij dwukrotnie ustawienie **Określ czas sprawdzania aktualizacji analizy** zabezpieczeń i ustaw opcję **Włączone**. Wprowadź czas, na który powinny być sprawdzane aktualizacje. Czas jest oparty na lokalnym czasie punktu końcowego. Kliknij przycisk **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Planowanie aktualizacji ochrony za pomocą poleceń cmdlet programu PowerShell

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Aby [uzyskać więcej informacji na](use-powershell-cmdlets-microsoft-defender-antivirus.md) temat używania programu PowerShell z programem PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń cm Program antywirusowy Microsoft Defender dlet programu PowerShell oraz poleceń [cmdlet programu Defender](/powershell/module/defender/) oraz Program antywirusowy Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Planowanie aktualizacji Windows zarządzania zabezpieczeniami przy użyciu instrukcji zarządzania danymi (WMI)

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz następujące informacje:

- [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>Artykuły pokrewne

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
