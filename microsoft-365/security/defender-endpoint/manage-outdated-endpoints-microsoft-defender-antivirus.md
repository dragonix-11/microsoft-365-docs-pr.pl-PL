---
title: Stosowanie aktualizacji ochrony av usługi Microsoft Defender do nieaktualizowych punktów końcowych
description: Zdefiniuj, kiedy i w jaki sposób należy stosować aktualizacje dla punktów końcowych, które nie zostały zaktualizowane od jakiegoś czasu.
keywords: aktualizacje, ochrona, nieaktualne, nieaktualne, stare, nadrabianie zaległości
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 0f7f42662bf698f6e3a092539e58a8a9de529b24
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789475"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Zarządzaj aktualizacjami programu antywirusowego Microsoft Defender i skanuj w poszukiwaniu nieaktualnych punktów końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender pozwala określić, jak długo punkt końcowy może uniknąć aktualizacji lub ile skanów może zostać pominiętych, zanim będzie wymagane zaktualizowanie i skanowanie. Jest to szczególnie przydatne w środowiskach, w których urządzenia nie są często połączone z siecią firmową lub zewnętrzną lub urządzeniami, które nie są używane na co dzień.

Na przykład pracownik korzystający z określonego komputera jest w przerwach przez trzy dni i nie loguje się na komputerze w tym czasie.

Gdy użytkownik wróci do pracy i zaloguje się na komputerze, Program antywirusowy Microsoft Defender natychmiast sprawdzi i pobierze najnowsze aktualizacje ochrony i uruchomi skanowanie.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości dla punktów końcowych, które nie były aktualizowane od jakiegoś czasu

Jeśli Program antywirusowy Microsoft Defender nie pobierze aktualizacji ochrony przez określony okres, możesz skonfigurować ją tak, aby automatycznie sprawdzała i pobierała najnowszą aktualizację podczas następnego logowania. Jest to przydatne w przypadku [globalnego wyłączenia automatycznego pobierania aktualizacji podczas uruchamiania](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości przy użyciu Configuration Manager

1. W konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (kliknij pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do **pozycji Przegląd** \> **Endpoint Protection** \> **Zasady ochrony przed złośliwym kodem**)

2. Przejdź do sekcji **Aktualizacje analizy zabezpieczeń** i skonfiguruj następujące ustawienia:

    1. Ustaw **opcję Wymuś aktualizację analizy zabezpieczeń, jeśli komputer kliencki jest w trybie offline dla więcej niż dwóch kolejnych zaplanowanych aktualizacji** na **wartość Tak**.
    2. Jeśli **Configuration Manager jest używany jako źródło aktualizacji analizy zabezpieczeń...**, określ godziny, przed którymi aktualizacje ochrony dostarczane przez Configuration Manager powinny być uważane za nieaktualne. Spowoduje to użycie następnej lokalizacji aktualizacji na podstawie zdefiniowanego [rezerwowego zamówienia źródłowego](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. Kliknij przycisk **OK**.

4. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Użyj zasady grupy, aby włączyć i skonfigurować funkcję aktualizacji catch-up

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > aktualizacje podpisów**.

5. Kliknij dwukrotnie ustawienie **Zdefiniuj liczbę dni, po których wymagana jest aktualizacja analizy zabezpieczeń catch-up** , i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których usługa Microsoft Defender AV ma zostać sprawdzona i pobrana najnowsza aktualizacja ochrony.

6. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [poleceń cmdlet programu antywirusowego Defender](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości za pomocą instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
SignatureUpdateCatchupInterval
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujące informacje:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Ustaw liczbę dni, po których ochrona zostanie zgłoszona jako nieaktualna

Możesz również określić liczbę dni, po których ochrona Program antywirusowy Microsoft Defender jest uznawana za starą lub nieaktualną. Po określonej liczbie dni klient zgłosi się jako nieaktualny i wyświetli użytkownikowi komputera błąd. Może to również spowodować, że Program antywirusowy Microsoft Defender spróbuje pobrać aktualizację z innych źródeł (w oparciu o zdefiniowaną [rezerwową kolejność źródła](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)), na przykład podczas korzystania z programu MMPC jako źródła pomocniczego po ustawieniu programu WSUS lub Microsoft Update jako pierwszego źródła.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Użyj zasady grupy, aby określić liczbę dni, po których ochrona zostanie uznana za nieaktualną

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > aktualizacje podpisu** i skonfiguruj następujące ustawienia:

    1. Kliknij dwukrotnie **pozycję Zdefiniuj liczbę dni, po których definicje programów szpiegujących zostaną uznane za nieaktualne** , i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których usługa Microsoft Defender AV uzna analizę zabezpieczeń za nieaktualną.

    2. Kliknij przycisk **OK**.

    3. Kliknij dwukrotnie **pozycję Zdefiniuj liczbę dni, po których definicje wirusów zostaną uznane za nieaktualne** , i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których usługa Microsoft Defender AV uzna analizę zabezpieczeń za nieaktualną.

    4. Kliknij przycisk **OK**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Konfigurowanie skanowania nadrabiania zaległości dla punktów końcowych, które nie były skanowane od jakiegoś czasu

Możesz ustawić liczbę kolejnych zaplanowanych skanów, które mogą zostać pominięte, zanim Program antywirusowy Microsoft Defender wymusi skanowanie.

Proces włączania tej funkcji to:

1. Skonfiguruj co najmniej jedno zaplanowane skanowanie (zobacz temat [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).
2. Włącz funkcję skanowania nadrabiania zaległości.
3. Zdefiniuj liczbę skanów, które można pominąć przed zakończeniem skanowania catch-up.

Tę funkcję można włączyć zarówno w przypadku pełnego, jak i szybkiego skanowania.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Użyj zasady grupy, aby włączyć i skonfigurować funkcję skanowania nadrabiania zaległości

1. Upewnij się, że skonfigurowano co najmniej jedno zaplanowane skanowanie.

2. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

4. Kliknij pozycję **Zasady** , a następnie **pozycję Szablony administracyjne**.

5. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > Skanuj** i skonfiguruj następujące ustawienia:

    1. Jeśli skonfigurowano zaplanowane szybkie skanowanie, kliknij dwukrotnie ustawienie **Włącz szybkie skanowanie catch-up** i ustaw opcję **Włączone**.
    2. Jeśli skonfigurowano zaplanowane pełne skanowanie, kliknij dwukrotnie ustawienie **Włącz pełne skanowanie catch-up** i ustaw opcję **Włączone**. Kliknij przycisk **OK**.
    3. Kliknij dwukrotnie ustawienie **Zdefiniuj liczbę dni, po których skanowanie uzupełniające jest wymuszone** , i ustaw opcję **Włączone**.
    4. Wprowadź liczbę skanów, które można pominąć, zanim skanowanie zostanie automatycznie uruchomione, gdy użytkownik następnym razem zaloguje się na komputerze. Typ skanowania, które jest uruchamiane, jest określany przez **opcję Określ typ skanowania do użycia podczas zaplanowanego skanowania** (zobacz temat [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). Kliknij przycisk **OK**.

> [!NOTE]
> Tytuł ustawienia zasady grupy odnosi się do liczby dni. Ustawienie jest jednak stosowane do liczby skanów (a nie dni) przed uruchomieniem skanowania nadrabiania zaległości.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Konfigurowanie skanowania nadrabiania zaległości przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz [Używanie poleceń cmdlet programu PowerShell do zarządzania poleceniami](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet programu Program antywirusowy Microsoft Defender i programu Antywirusowego Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Konfigurowanie skanowania nadrabiania zaległości przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujące informacje:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Konfigurowanie skanowania nadrabiania zaległości przy użyciu Configuration Manager

1. W konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (kliknij pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do **pozycji Przegląd** \> **Endpoint Protection** \> **Zasady ochrony przed złośliwym kodem**)

2. Przejdź do sekcji Zaplanowane skanowania i **wymuś skanowanie wybranego typu skanowania, jeśli komputer kliencki jest w trybie offline...** na **wartość Tak**.

3. Kliknij przycisk **OK**.

4. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
