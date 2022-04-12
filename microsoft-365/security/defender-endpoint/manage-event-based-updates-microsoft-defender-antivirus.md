---
title: Stosowanie aktualizacji Program antywirusowy Microsoft Defender po określonych zdarzeniach
description: Zarządzanie sposobem, w jaki Program antywirusowy Microsoft Defender stosuje aktualizacje analizy zabezpieczeń po uruchomieniu lub otrzymaniu raportów wykrywania dostarczanych przez chmurę.
keywords: aktualizacje, ochrona, wymuszanie aktualizacji, zdarzenia, uruchamianie, sprawdzanie najnowszych, powiadomienia
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
ms.openlocfilehash: 8ad9a5c6cd1a79152640bb153f8a130ecdd29362
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789497"
---
# <a name="manage-event-based-forced-updates"></a>Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender pozwala określić, czy aktualizacje powinny (lub nie powinny) występować po określonych zdarzeniach, takich jak podczas uruchamiania lub po otrzymaniu określonych raportów z usługi ochrony dostarczanej w chmurze.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Sprawdzanie dostępności aktualizacji ochrony przed uruchomieniem skanowania

Możesz użyć poleceń cmdlet Microsoft Endpoint Configuration Manager, zasady grupy, PowerShell i WMI, aby wymusić Program antywirusowy Microsoft Defender sprawdzanie i pobieranie aktualizacji ochrony przed uruchomieniem zaplanowanego skanowania.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Użyj Configuration Manager, aby sprawdzić aktualizacje ochrony przed uruchomieniem skanowania

1. W konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (kliknij pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do **pozycji Przegląd** \> **Endpoint Protection** \> **Zasady ochrony przed złośliwym kodem**)

2. Przejdź do sekcji **Zaplanowane skanowania** i ustaw **pozycję Sprawdź najnowsze aktualizacje analizy zabezpieczeń przed uruchomieniem skanowania** na **wartość Tak**.

3. Kliknij przycisk **OK**.

4. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Użyj zasady grupy, aby sprawdzić aktualizacje ochrony przed uruchomieniem skanowania

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **Skanuj**.

5. Kliknij dwukrotnie **pozycję Sprawdź najnowsze definicje wirusów i programów szpiegujących przed uruchomieniem zaplanowanego skanowania** i ustaw opcję **Włączone**.

6. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Użyj poleceń cmdlet programu PowerShell, aby sprawdzić, czy nie ma aktualizacji ochrony przed uruchomieniem skanowania

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do konfigurowania i uruchamiania poleceń](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet Program antywirusowy Microsoft Defender i defender antivirus](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Użyj instrukcji zarządzania Windows (WMI), aby sprawdzić aktualizacje ochrony przed uruchomieniem skanowania

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
CheckForSignaturesBeforeRunningScan
```

Aby uzyskać więcej informacji, zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Sprawdzanie dostępności aktualizacji ochrony podczas uruchamiania

Możesz użyć zasady grupy, aby wymusić Program antywirusowy Microsoft Defender na sprawdzanie i pobieranie aktualizacji ochrony po uruchomieniu maszyny.

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij dwukrotnie **pozycję Sprawdź najnowsze definicje wirusów i programów szpiegujących podczas uruchamiania** i ustaw opcję **Włączone**.

6. Kliknij przycisk **OK**.

Możesz również użyć zasady grupy, programu PowerShell lub usługi WMI, aby skonfigurować Program antywirusowy Microsoft Defender w celu sprawdzania dostępności aktualizacji podczas uruchamiania, nawet jeśli nie jest uruchomiona.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Użyj zasady grupy, aby pobrać aktualizacje, gdy nie ma Program antywirusowy Microsoft Defender

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Korzystając z **edytora zarządzania zasady grupy**, przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij **dwukrotnie pozycję Inicjuj aktualizację analizy zabezpieczeń podczas uruchamiania** i ustaw opcję **Włączone**.

6. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Pobieranie aktualizacji przy braku Program antywirusowy Microsoft Defender przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Aby uzyskać więcej informacji, zobacz [Używanie poleceń cmdlet programu PowerShell do zarządzania poleceniami cmdlet programu antywirusowego Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [defender](/powershell/module/defender/index), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Użyj instrukcji zarządzania Windows (WMI), aby pobrać aktualizacje, gdy nie ma Program antywirusowy Microsoft Defender

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Aby uzyskać więcej informacji, zobacz [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Zezwalaj na zmiany ad hoc w ochronie w oparciu o ochronę dostarczaną przez chmurę

Usługa Microsoft Defender AV może wprowadzać zmiany w swojej ochronie w oparciu o ochronę dostarczaną przez chmurę. Takie zmiany mogą wystąpić poza normalnymi lub zaplanowanymi aktualizacjami ochrony.

Jeśli włączono ochronę dostarczaną przez chmurę, usługa Microsoft Defender AV wyśle podejrzane pliki do chmury Windows Defender. Jeśli usługa w chmurze zgłasza, że plik jest złośliwy, a plik zostanie wykryty w ostatniej aktualizacji ochrony, możesz użyć zasady grupy, aby skonfigurować usługę Microsoft Defender AV, aby automatycznie otrzymywać tę aktualizację ochrony. Można również zastosować inne ważne aktualizacje ochrony.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Użyj zasady grupy, aby automatycznie pobierać najnowsze aktualizacje w oparciu o ochronę dostarczaną przez chmurę

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje analizy zabezpieczeń**.

5. Kliknij **dwukrotnie pozycję Zezwalaj na aktualizacje analizy zabezpieczeń w czasie rzeczywistym na podstawie raportów w usłudze Microsoft MAPS** i ustaw opcję **Włączone**. Następnie kliknij przycisk **OK**.

6. **Zezwalaj na powiadomienia, aby wyłączyć raporty oparte na definicjach w usłudze Microsoft MAPS** i ustawić opcję **Włączone**. Następnie kliknij przycisk **OK**.

> [!NOTE]
> **Zezwalaj na powiadomienia w celu wyłączenia raportów opartych na definicjach** umożliwia usłudze Microsoft MAPS wyłączenie tych definicji, o których wiadomo, że powodują raporty fałszywie dodatnie. Aby ta funkcja działała, należy skonfigurować komputer do dołączania do usługi Microsoft MAPS.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
