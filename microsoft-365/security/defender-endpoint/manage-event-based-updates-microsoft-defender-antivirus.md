---
title: Stosowanie Program antywirusowy Microsoft Defender aktualizacji po określonych zdarzeniach
description: Zarządzanie zastosowaniem Program antywirusowy Microsoft Defender zabezpieczeń po uruchomieniu lub otrzymaniu raportów wykrywania w chmurze.
keywords: aktualizacje, ochrona, wymuszanie aktualizacji, zdarzenia, uruchamianie, sprawdzanie najnowszych, powiadomień
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/17/2018
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: c99e4e085de32ac4e7ec77a2155182f1a930d432
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997384"
---
# <a name="manage-event-based-forced-updates"></a>Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program antywirusowy Microsoft Defender pozwala określić, czy aktualizacje powinny (czy nie) nastąpić po pewnych zdarzeniach, takich jak uruchomienie lub odebranie określonych raportów z usługi ochrony w chmurze.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Sprawdzanie aktualizacji ochrony przed uruchomieniem skanowania

Możesz użyć poleceń Microsoft Endpoint Configuration Manager, zasady grupy, poleceń cmdlet programu PowerShell i usługi WMI, aby wymusić Program antywirusowy Microsoft Defender sprawdzanie i pobieranie aktualizacji ochrony przed uruchomieniem zaplanowanego skanowania.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Sprawdzanie aktualizacji ochrony Menedżer konfiguracji za pomocą funkcji skanowania przed uruchomieniem skanowania

1. Na konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym oprogramowaniem, które chcesz zmienić (kliknij pozycję Zasoby i zgodność  w okienku nawigacji po lewej stronie,  \> a następnie rozwiń drzewo do okna Omówienie **Endpoint Protection** \> zasady ochrony przed złośliwym **oprogramowaniem)**

2. Przejdź do sekcji **Zaplanowane skanowania i** przed uruchomieniem skanowania ustaw pozycję Sprawdź najnowsze aktualizacje analizy zabezpieczeń **na** wartość **Tak**.

3. Kliknij przycisk **OK**.

4. [Wdeksuj zaktualizowane zasady w zwykły sposób](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Sprawdzanie zasady grupy ochrony przed uruchomieniem skanowania za pomocą funkcji aktualizacji

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania przejdź** do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki Program antywirusowy Microsoft Defender** \>  \> **skanu**.

5. Kliknij dwukrotnie **pozycję Sprawdź najnowsze definicje wirusów i oprogramowania szpiegującego** przed uruchomieniem zaplanowanego skanowania i ustaw opcję **Włączone**.

6. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Sprawdzanie aktualizacji ochrony przed uruchomieniem skanowania za pomocą poleceń cmdlet programu PowerShell

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) do konfigurowania i uruchamiania Program antywirusowy Microsoft Defender i poleceń [cmdlet programu antywirusowego Defender](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Używanie Windows zarządzania zabezpieczeniami (WMI) w celu sprawdzenia, czy są dostępne aktualizacje ochrony przed uruchomieniem skanowania

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
CheckForSignaturesBeforeRunningScan
```

Aby uzyskać więcej informacji, zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Sprawdzanie aktualizacji ochrony podczas uruchamiania

Za pomocą przycisków zasady grupy wymusić Program antywirusowy Microsoft Defender sprawdzanie i pobieranie aktualizacji ochrony po uruchomionym komputerze.

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania przejdź** do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij dwukrotnie **pozycję Sprawdź, czy podczas uruchamiania są dostępne najnowsze definicje wirusów i oprogramowania szpiegującego**, i ustaw dla **opcji Włączone.**

6. Kliknij przycisk **OK**.

Za pomocą programu zasady grupy, PowerShell lub WMI można również skonfigurować Program antywirusowy Microsoft Defender, aby sprawdzać aktualizacje podczas uruchamiania, nawet jeśli nie jest uruchomione.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Użyj zasady grupy, aby pobrać aktualizacje, Program antywirusowy Microsoft Defender nie jest obecne

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania danymi** przejdź do **strony Konfiguracja komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij dwukrotnie pozycję **Zainicjuj aktualizację analizy zabezpieczeń przy uruchamianiu** i ustaw opcję **Włączone**.

6. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Używanie poleceń cmdlet programu PowerShell do pobierania aktualizacji, Program antywirusowy Microsoft Defender nie jest dostępne

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Aby uzyskać więcej informacji, zobacz Zarządzanie poleceniami [cmdlet programu PowerShell Program antywirusowy Microsoft Defender programem PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [poleceniami cmdlet programu Defender Antivirus](/powershell/module/defender/index), aby uzyskać więcej informacji na temat korzystania z programu PowerShell z programem Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Używanie Windows zarządzania (WMI) w celu pobierania aktualizacji, Program antywirusowy Microsoft Defender nie jest obecna

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Aby uzyskać więcej informacji, zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Zezwalanie na doraźne zmiany w ochronie opartej na ochronie w chmurze

Program Microsoft Defender AV może wprowadzać zmiany w zabezpieczeniach w chmurze. Zmiany te mogą wystąpić poza normalnymi lub planowanymi aktualizacjami ochrony.

Jeśli włączono ochronę w chmurze, program Microsoft Defender AV będzie wysyłać podejrzanych plików do Windows Defender danych. Jeśli usługa w chmurze zgłasza, że plik jest złośliwy, a plik został wykryty w ostatniej aktualizacji ochrony, możesz za pomocą programu zasady grupy skonfigurować program Microsoft Defender AV w celu automatycznego odbierania tej aktualizacji ochrony. Można również stosować inne ważne aktualizacje dotyczące ochrony.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Użyj zasady grupy, aby automatycznie pobierać najnowsze aktualizacje w oparciu o ochronę w chmurze

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania przejdź** do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij dwukrotnie pozycję **Zezwalaj na aktualizacje analizy zabezpieczeń w czasie rzeczywistym na podstawie** raportów dla usługi MAPY Microsoft i ustaw opcję **Włączone**. Następnie kliknij przycisk **OK**.

6. **Zezwalaj na wyłączanie raportów opartych na definicjach w aplikacji Microsoft MAPS** i ustawianie dla **opcji Włączone.** Następnie kliknij przycisk **OK**.

> [!NOTE]
> **Zezwalaj na wyłączanie powiadomień w raportach opartych** na definicjach, dzięki funkcji MAPY Microsoft mogą wyłączać te definicje, które mogą powodować raporty fałszywie dodatnie. Aby ta funkcja działała, musisz skonfigurować komputer tak, aby ta funkcja działała w aplikacji Microsoft MAPS.

## <a name="see-also"></a>Zobacz też

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie tym, kiedy mają być pobierane i stosowane aktualizacje ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
