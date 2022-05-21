---
title: Stosowanie aktualizacji ochrony Program antywirusowy Microsoft Defender do nieaktualnych punktów końcowych
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
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: fcf13258b8012bfd2a5875b52b8d844040aee73e
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623496"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Zarządzaj aktualizacjami programu antywirusowego Microsoft Defender i skanuj w poszukiwaniu nieaktualnych punktów końcowych

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**

- System Windows

Dzięki Program antywirusowy Microsoft Defender twój zespół ds. zabezpieczeń może określić, jak długo punkt końcowy może uniknąć aktualizacji lub ile skanów może przegapić, zanim będzie wymagany do odebrania aktualizacji i uruchomienia skanowania. Ta funkcja jest szczególnie przydatna w środowiskach, w których urządzenia nie są często połączone z siecią firmową lub zewnętrzną albo w przypadku urządzeń, które nie są używane na co dzień.

Na przykład pracownik korzystający z określonego komputera ma trzy dni wolnego od pracy i nie loguje się na komputerze w tym czasie. Gdy pracownik wróci do pracy i zaloguje się do swojego komputera, Program antywirusowy Microsoft Defender natychmiast sprawdzi i pobierze najnowsze aktualizacje ochrony, a następnie uruchomi skanowanie.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości dla punktów końcowych, które nie były aktualizowane od jakiegoś czasu

Jeśli Program antywirusowy Microsoft Defender nie pobrano aktualizacji ochrony przez określony okres, możesz skonfigurować ją tak, aby automatycznie sprawdzała i pobierała najnowszą aktualizację przy następnym logowaniu się do punktu końcowego. Ta konfiguracja jest przydatna w przypadku [globalnego wyłączenia automatycznego pobierania aktualizacji podczas uruchamiania](manage-event-based-updates-microsoft-defender-antivirus.md).

Aby skonfigurować aktualizacje ochrony nadrabiania zaległości, można użyć jednej z kilku metod:

- [Menedżer konfiguracji](#use-configuration-manager-to-configure-catch-up-protection-updates)
- [Zasady grupy](#use-group-policy-to-enable-and-configure-the-catch-up-update-feature)
- [Polecenia cmdlet programu PowerShell](#use-powershell-cmdlets-to-configure-catch-up-protection-updates)
- [instrukcja zarządzania Windows (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates)

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości przy użyciu Configuration Manager

1. W konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (wybierz pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do pozycji **Przegląd** \> **Endpoint Protection** \> **zasady ochrony przed złośliwym kodem**)

2. Przejdź do sekcji **Aktualizacje analizy zabezpieczeń** i skonfiguruj następujące ustawienia:

    - Ustaw **opcję Wymuś aktualizację analizy zabezpieczeń, jeśli komputer kliencki jest w trybie offline dla więcej niż dwóch kolejnych zaplanowanych aktualizacji** na **wartość Tak**.
    - W polu **Jeśli Configuration Manager jest używany jako źródło aktualizacji analizy zabezpieczeń...**, określ godziny, przed którymi aktualizacje ochrony dostarczane przez Configuration Manager powinny być uważane za nieaktualne. To ustawienie powoduje użycie następnej lokalizacji aktualizacji na podstawie zdefiniowanego [rezerwowego zamówienia źródłowego](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. Wybierz przycisk **OK**.

4. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Użyj zasady grupy, aby włączyć i skonfigurować funkcję aktualizacji catch-up

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Wybierz pozycję **Zasady** , a następnie **szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > aktualizacje podpisów**.

5. Kliknij dwukrotnie ustawienie **Zdefiniuj liczbę dni, po których wymagana jest aktualizacja analizy zabezpieczeń catch-up** , i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których Program antywirusowy Microsoft Defender sprawdzić i pobrać najnowszą aktualizację ochrony.

6. Wybierz przycisk **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości przy użyciu poleceń cmdlet programu PowerShell

Użyj następującego polecenia cmdlet:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Aby uzyskać więcej informacji na temat korzystania z programu PowerShell z Program antywirusowy Microsoft Defender, zobacz następujące artykuły:

- [Konfigurowanie i uruchamianie Program antywirusowy Microsoft Defender przy użyciu poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Polecenia cmdlet programu antywirusowego Defender](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony nadrabiania zaległości za pomocą instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
SignatureUpdateCatchupInterval
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujący artykuł:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Ustaw liczbę dni, po których ochrona zostanie zgłoszona jako nieaktualna

Możesz również określić liczbę dni, po których ochrona Program antywirusowy Microsoft Defender jest uznawana za starą lub nieaktualna. Po określonej liczbie dni klient zgłosi się jako "nieaktualny" i wyświetli błąd użytkownikowi punktu końcowego. Gdy punkt końcowy jest uznawany za nieaktualny, Program antywirusowy Microsoft Defender może próbować pobrać aktualizację z innych źródeł (na podstawie zdefiniowanego [rezerwowego zamówienia źródłowego](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)).

Możesz użyć zasady grupy, aby określić liczbę dni, po których ochrona punktu końcowego jest uważana za nieaktualna.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Użyj zasady grupy, aby określić liczbę dni, po których ochrona zostanie uznana za nieaktualna

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Wybierz pozycję **Zasady** , a następnie **szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > aktualizacje podpisu** i skonfiguruj następujące ustawienia:

    1. Kliknij dwukrotnie **pozycję Zdefiniuj liczbę dni, po których definicje programów szpiegujących zostaną uznane za nieaktualne** , i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których chcesz, aby Program antywirusowy Microsoft Defender uznać analizę zabezpieczeń programów szpiegujących za nieaktualna.

    2. Wybierz przycisk **OK**.

    3. Kliknij dwukrotnie **pozycję Zdefiniuj liczbę dni, po których definicje wirusów zostaną uznane za nieaktualne** , i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których chcesz, aby Program antywirusowy Microsoft Defender uznać analizę zabezpieczeń przed wirusami za nieaktualna.

    4. Wybierz przycisk **OK**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Konfigurowanie skanowania nadrabiania zaległości dla punktów końcowych, które nie były skanowane od jakiegoś czasu

Możesz ustawić liczbę kolejnych zaplanowanych skanów, które mogą zostać pominięte, zanim Program antywirusowy Microsoft Defender wymusi skanowanie.

Proces włączania tej funkcji to:

1. Skonfiguruj co najmniej jedno zaplanowane skanowanie (zobacz artykuł [Zaplanowane skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).

2. Włącz funkcję skanowania nadrabiania zaległości.

3. Zdefiniuj liczbę skanów, które można pominąć przed zakończeniem skanowania catch-up.

Tę funkcję można włączyć zarówno w przypadku pełnego, jak i szybkiego skanowania. 

> [!TIP]
> Zalecamy używanie szybkich skanów w większości sytuacji. Aby dowiedzieć się więcej, zobacz [Szybkie skanowanie, pełne skanowanie i skanowanie niestandardowe](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan). 

Do konfigurowania skanowania uzupełniającego można użyć jednej z kilku metod:

- [Zasady grupy](#use-group-policy-to-enable-and-configure-the-catch-up-scan-feature)
- [Konfigurowanie skanowania nadrabiania zaległości przy użyciu poleceń cmdlet programu PowerShell](#use-powershell-cmdlets-to-configure-catch-up-scans)
- [instrukcja zarządzania Windows (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-scans)
- [Menedżer konfiguracji](#use-configuration-manager-to-configure-catch-up-scans)

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Użyj zasady grupy, aby włączyć i skonfigurować funkcję skanowania nadrabiania zaległości

1. Upewnij się, że skonfigurowano co najmniej jedno zaplanowane skanowanie.

2. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

4. Wybierz pozycję **Zasady** , a następnie **szablony administracyjne**.

5. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > Skanuj** i skonfiguruj następujące ustawienia:

    - Jeśli skonfigurowano zaplanowane szybkie skanowanie, kliknij dwukrotnie ustawienie **Włącz szybkie skanowanie catch-up** i ustaw opcję **Włączone**.
    - Jeśli skonfigurowano zaplanowane pełne skanowanie, kliknij dwukrotnie ustawienie **Włącz pełne skanowanie catch-up** i ustaw opcję **Włączone**. Wybierz przycisk **OK**.
    - Kliknij dwukrotnie ustawienie **Zdefiniuj liczbę dni, po których skanowanie uzupełniające jest wymuszone** , i ustaw opcję **Włączone**.
    - Wprowadź liczbę skanów, które mogą zostać pominięte, zanim skanowanie zostanie automatycznie uruchomione po następnym zalogowaniu się użytkownika w punkcie końcowym. Typ uruchomionego skanowania jest określany przez opcję **Określ typ skanowania do użycia podczas zaplanowanego skanowania** (zobacz artykuł [Harmonogram skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). Wybierz przycisk **OK**.

> [!NOTE]
> Tytuł ustawienia zasady grupy odnosi się do liczby dni. Ustawienie jest jednak stosowane do liczby skanów (a nie dni) przed uruchomieniem skanowania nadrabiania zaległości.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Konfigurowanie skanowania nadrabiania zaległości przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Aby uzyskać więcej informacji na temat korzystania z programu PowerShell z Program antywirusowy Microsoft Defender, zobacz następujące artykuły:

- [Za pomocą poleceń cmdlet programu PowerShell zarządzaj programem antywirusowym Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) 
- [Polecenia cmdlet programu antywirusowego Defender](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Konfigurowanie skanowania nadrabiania zaległości przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) dla następujących właściwości:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Aby uzyskać więcej informacji i dozwolone parametry, zobacz następujący artykuł:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Konfigurowanie skanowania nadrabiania zaległości przy użyciu Configuration Manager

1. W konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym kodem, które chcesz zmienić (wybierz pozycję **Zasoby i zgodność** w okienku nawigacji po lewej stronie, a następnie rozwiń drzewo do pozycji **Przegląd** \> **Endpoint Protection** \> **zasady ochrony przed złośliwym kodem**)

2. Przejdź do sekcji Zaplanowane skanowania i **wymuś skanowanie wybranego typu skanowania, jeśli komputer kliencki jest w trybie offline...** na **wartość Tak**.

3. Wybierz przycisk **OK**.

4. [Wdróż zaktualizowane zasady jak zwykle](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Powiązane artykuły:

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
