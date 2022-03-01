---
title: Stosowanie aktualizacji ochrony audio/wideo programu Microsoft Defender do aktualnych punktów końcowych
description: Zdefiniuj, kiedy i jak mają być stosowane aktualizacje dla punktów końcowych, które nie zostały zaktualizowane od jakego czasu.
keywords: aktualizacje, ochrona, nieaktualne, nieaktualne, stare, na bieżąco
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
ms.openlocfilehash: a708bf6ef34767b338c40cf8004e4c497658fc36
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997814"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Zarządzanie Program antywirusowy Microsoft Defender i skanowaniami w poszukiwaniu punktów końcowych, które są aktualne

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program antywirusowy Microsoft Defender pozwala zdefiniować, przez jaki czas może zostać pominięty lub przez jaki czas może zostać pominięty przez punkt końcowy w celu zaktualizowania i zeskanowania samego punktu końcowego. Jest to szczególnie przydatne w środowiskach, w których urządzenia nie są często połączone z siecią firmową lub zewnętrzną, lub urządzeń, które nie są używane codziennie.

Na przykład pracownik, który korzysta z określonego komputera, jest w przerwie przez trzy dni i w tym czasie nie loguje się na swoim komputerze.

Gdy użytkownik powróci do pracy i zaloguje się na swoim komputerze, Program antywirusowy Microsoft Defender natychmiast sprawdzi i pobierze najnowsze aktualizacje ochrony oraz rozpocznie skanowanie.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Konfigurowanie aktualizacji ochrony przez przyciąganie informacji dla punktów końcowych, które nie są aktualizowane przez jakiś czas

Jeśli Program antywirusowy Microsoft Defender nie pobierał aktualizacji ochrony przez określony czas, możesz skonfigurować go tak, aby automatycznie sprawdzał i pobierał najnowszą aktualizację przy następnym logu. Jest to przydatne, jeśli po uruchomieniu [globalnie wyłączono automatyczne pobieranie aktualizacji](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Konfigurowanie Menedżer konfiguracji w celu skonfigurowania aktualizacji ochrony przed przyciągania informacji

1. Na konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym oprogramowaniem, które chcesz zmienić (kliknij pozycję Zasoby i zgodność  w okienku nawigacji po lewej stronie,  \> a następnie rozwiń drzewo do okna Omówienie **Endpoint Protection** \> zasady ochrony przed złośliwym **oprogramowaniem)**

2. Przejdź do sekcji **Aktualizacje analizy zabezpieczeń i** skonfiguruj następujące ustawienia:

    1. Ustaw **opcję Wymuszaj aktualizację analizy zabezpieczeń, jeśli klient jest w trybie offline dla więcej niż dwóch następujących po sobie zaplanowanych aktualizacji na** **wartość Tak**.
    2. W przypadku ustawienia Menedżer konfiguracji źródło aktualizacji analizy zabezpieczeń  **...** określ godziny, przed którymi aktualizacje ochrony dostarczane przez program Menedżer konfiguracji powinny być traktowane jako aktualne. Spowoduje to, że będzie używana lokalizacja następnej aktualizacji na podstawie zdefiniowanej kolejności [źródłowej rezerwowej](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. Kliknij przycisk **OK**.

4. [Wdeksuj zaktualizowane zasady w zwykły sposób](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Korzystanie zasady grupy w celu włączenia i skonfigurowania funkcji aktualizacji pochwytliwej

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki > Program antywirusowy Microsoft Defender > aktualizacji podpisu**.

5. Kliknij dwukrotnie ustawienie **Definiuj liczbę** dni, po upływie której jest wymagana aktualizacja analizy zabezpieczeń pojętego, i ustaw dla opcji wartość **Włączone**. Wprowadź liczbę dni, po których program Microsoft Defender AV będzie sprawdzał i pobierał najnowszą aktualizację ochrony.

6. Kliknij przycisk **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji ochrony za pomocą poleceń cmdlet programu PowerShell

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Aby [uzyskać więcej informacji na](use-powershell-cmdlets-microsoft-defender-antivirus.md) temat używania programu PowerShell z programem PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń cm Program antywirusowy Microsoft Defender dlet programu PowerShell oraz poleceń [cmdlet programu Defender](/powershell/module/defender/) oraz Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Konfigurowanie aktualizacji Windows zarządzania za pomocą instrukcji zarządzania zabezpieczeniami (WMI)

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
SignatureUpdateCatchupInterval
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz następujące informacje:

- [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Ustawianie liczby dni przed raportem o ochronie jako aktualnej

Możesz także określić liczbę dni, po których Program antywirusowy Microsoft Defender będzie uznawana za starą lub zdaną. Po upływie określonej liczby dni klient będzie zgłaszać się jako aktualny i będzie wyświetlać komunikat o błędzie użytkownikowi komputera. Może to również spowodować, że program Program antywirusowy Microsoft Defender będzie próbował pobrać aktualizację z innych źródeł (na podstawie zdefiniowanej kolejności [źródłowej), na](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) przykład w przypadku użycia mmpc jako źródła pomocniczego po ustawieniu programu WSUS lub Microsoft Update jako pierwszego źródła.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Użyj zasady grupy, aby określić liczbę dni, po których ochrona będzie uznawana za datę

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki > Program antywirusowy Microsoft Defender > aktualizacje podpisu** i skonfiguruj następujące ustawienia:

    1. Kliknij dwukrotnie **pozycję Definiuj liczbę** dni, po których definicje oprogramowania szpiegującego zostaną uznane za aktualne, i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których program Microsoft Defender AV będzie uznać, że funkcje analizy zabezpieczeń programu szpiegującego są aktualne.

    2. Kliknij przycisk **OK**.

    3. Kliknij dwukrotnie **pozycję Definiuj liczbę dni** , po których definicje wirusów zostaną uznane za aktualne, i ustaw opcję **Włączone**. Wprowadź liczbę dni, po których program Microsoft Defender AV będzie uznać, że funkcje analizy wirusów są aktualne.

    4. Kliknij przycisk **OK**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Konfigurowanie skanowania w poszukiwaniu punktów końcowych, które nie były skanowane przez jakiś czas

Możesz ustawić liczbę następujących po sobie zaplanowanych skanów, które mogą zostać pominięte przed Program antywirusowy Microsoft Defender wymusnąć skan.

Proces włączania tej funkcji jest:

1. Skonfiguruj co najmniej jedno zaplanowane skanowanie (zobacz temat [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).
2. Włącz funkcję skanowania pogotowa.
3. Zdefiniuj liczbę skanów, które można pominąć przed rozpoczęciem skanowania pochwytowego.

Tę funkcję można włączyć zarówno w przypadku pełnego, jak i szybkiego skanowania.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Korzystanie zasady grupy w celu włączenia i skonfigurowania funkcji skanowania pochwytowego

1. Upewnij się, że zostało ustawione co najmniej jedno zaplanowane skanowanie.

2. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

3. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

4. Kliknij **pozycję Zasady** , **a następnie pozycję Szablony administracyjne**.

5. Rozwiń drzewo, **aby Windows składniki > Program antywirusowy Microsoft Defender > skanuj** i skonfiguruj następujące ustawienia:

    1. Jeśli masz ustawione zaplanowane szybkie skanowania, kliknij dwukrotnie ustawienie Włącz funkcję szybkiej  skanowania i ustaw dla tej opcji wartość **Włączone**.
    2. Jeśli masz ustawione zaplanowane pełne skanowania, kliknij dwukrotnie ustawienie **Włącz** pełne skanowanie po zakończeniu i ustaw dla tej opcji wartość **Włączone**. Kliknij przycisk **OK**.
    3. Kliknij dwukrotnie wartość **Określ** liczbę dni, po których trzeba wymusić skanowanie pochwytne, i ustaw dla opcji wartość **Włączone**.
    4. Wprowadź liczbę skanów, które mogą zostać nieodebrane przed rozpoczęciem skanowania, gdy użytkownik następnym razem zaloguje się na komputerze. Typ skanowania jest określany przez typ skanowania Określ typ skanowania do użycia w zaplanowanym skanie **(zobacz** temat [Planowanie skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). Kliknij przycisk **OK**.

> [!NOTE]
> Tytuł zasady grupy to liczba dni. Jednak to ustawienie jest stosowane do liczby skanów (nie dni), zanim zostanie uruchomione skanowanie pochwytne.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Konfigurowanie poleceń cmdlet programu PowerShell w celu konfigurowania skanów

Użyj następujących polecenia cmdlet:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Zobacz [Zarządzanie poleceniami cmdlet programu PowerShell i](use-powershell-cmdlets-microsoft-defender-antivirus.md) Program antywirusowy Microsoft Defender [programu Defender Antivirus](/powershell/module/defender/), aby uzyskać więcej informacji na temat korzystania z programu PowerShell z programem Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Konfigurowanie Windows przez zarządzanie nimi przy użyciu instrukcji zarządzania danymi (WMI, Catch-Up Instruction)

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uzyskać następujące właściwości:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Aby uzyskać więcej informacji i dozwolonych parametrów, zobacz następujące informacje:

- [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Konfigurowanie Menedżer konfiguracji za pomocą funkcji pochwytania

1. Na konsoli Microsoft Endpoint Manager otwórz zasady ochrony przed złośliwym oprogramowaniem, które chcesz zmienić (kliknij pozycję Zasoby i zgodność  w okienku nawigacji po lewej stronie,  \> a następnie rozwiń drzewo do okna Omówienie **Endpoint Protection** \> zasady ochrony przed złośliwym **oprogramowaniem)**

2. Przejdź do sekcji **Zaplanowane skanowania** i Wymusij skanowanie wybranego typu skanowania, jeśli klient jest w trybie **offline...** na pozycję **Tak**.

3. Kliknij przycisk **OK**.

4. [Wdeksuj zaktualizowane zasady w zwykły sposób](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="related-articles"></a>Artykuły pokrewne

- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Zarządzanie tym, kiedy mają być pobierane i stosowane aktualizacje ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
