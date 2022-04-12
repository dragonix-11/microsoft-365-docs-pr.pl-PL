---
title: Włączanie ochrony w chmurze w Program antywirusowy Microsoft Defender
description: Włącz ochronę w chmurze, aby korzystać z szybkich i zaawansowanych funkcji ochrony.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, chmura, blok od pierwszego wejrzenia
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 95269837e4ad26b4928a2ff82df65a259c707290
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790663"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Włączanie ochrony w chmurze w Program antywirusowy Microsoft Defender

**Dotyczy:**

- Program antywirusowy Microsoft Defender
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

**Platformy**
- System Windows

[Ochrona w chmurze w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) zapewnia dokładną, w czasie rzeczywistym i inteligentną ochronę. Ochrona w chmurze powinna być domyślnie włączona; Można jednak skonfigurować ochronę w chmurze zgodnie z potrzebami organizacji.

## <a name="methods-to-configure-cloud-protection"></a>Metody konfigurowania ochrony w chmurze

Ochronę Program antywirusowy Microsoft Defender w chmurze można włączyć lub wyłączyć przy użyciu jednej z kilku metod:

- Microsoft Endpoint Manager, w tym Microsoft Intune i Configuration Manager
- Zasady grupy
- Polecenia cmdlet programu PowerShell

Ochronę w chmurze można również włączyć lub wyłączyć w poszczególnych punktach końcowych przy użyciu aplikacji Zabezpieczenia Windows. 

Aby uzyskać więcej informacji na temat określonych wymagań dotyczących łączności sieciowej, aby upewnić się, że punkty końcowe mogą łączyć się z usługą ochrony w chmurze, zobacz [Konfigurowanie i weryfikowanie połączeń sieciowych](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> W Windows 10 i Windows 11 nie ma różnicy między opcjami raportowania **podstawowego** i **zaawansowanego** opisanymi w tym artykule. Jest to starsze rozróżnienie, a wybranie dowolnego z tych ustawień spowoduje taki sam poziom ochrony w chmurze. Nie ma różnicy w typie ani ilości udostępnianych informacji. Aby uzyskać więcej informacji na temat tego, co zbieramy, zobacz [Zasady zachowania poufności informacji firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Włączanie ochrony w chmurze przy użyciu Intune

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. W okienku **Narzędzia** główne wybierz pozycję **Konfiguracja urządzenia > Profile**.

3. Wybierz typ profilu **Ograniczenia urządzenia** , który chcesz skonfigurować. Jeśli chcesz utworzyć nowy typ profilu **ograniczenia urządzenia**, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure).

4. Wybierz  pozycję **Ustawienia konfiguracji** właściwości\>: Edytuj \> **Program antywirusowy Microsoft Defender**.

5. Na przełączniku **ochrony dostarczanym przez chmurę** wybierz pozycję **Włącz**.

6. Na liście rozwijanej **Monituj użytkowników przed przesłaniem przykładu** wybierz pozycję **Wyślij wszystkie dane automatycznie**.

Aby uzyskać więcej informacji na temat Intune profilów urządzeń, w tym sposobu tworzenia i konfigurowania ustawień, zobacz [Co to są Microsoft Intune profili urządzeń?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Włączanie ochrony w chmurze przy użyciu Microsoft Endpoint Manager

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** zabezpieczeń \> **punktu końcowego**.

3. Wybierz profil antywirusowy. (Jeśli jeszcze go nie masz lub chcesz utworzyć nowy profil, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure).

4. Wybierz polecenie **Właściwości**. Następnie obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

5. Rozwiń węzeł **Ochrona w chmurze**, a następnie na liście **poziomów ochrony dostarczanej w chmurze** wybierz jedną z następujących opcji:
   - **Wysoki**: stosuje silny poziom wykrywania.
   - **Wysoki plus**: używa **wysokiego** poziomu i stosuje więcej środków ochrony (może mieć wpływ na wydajność klienta).
   - **Zero tolerancji**: blokuje wszystkie nieznane pliki wykonywalne.

6. Wybierz pozycję **Przejrzyj i zapisz**, a następnie wybierz pozycję **Zapisz**.

Aby uzyskać więcej informacji na temat konfigurowania Microsoft Endpoint Configuration Manager, zobacz [How to create and deploy antimalware policies: Cloud-protection service (Jak tworzyć i wdrażać zasady ochrony przed złośliwym kodem: usługa ochrony w chmurze](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Włączanie ochrony w chmurze przy użyciu zasady grupy

1. Na urządzeniu do zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Wybierz pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** >  **Program antywirusowy Microsoft Defender > MAPS**

    > [!NOTE]
    > Ustawienia USŁUGI MAPS są równe ochronie dostarczanej w chmurze.

5. Kliknij dwukrotnie **pozycję Dołącz do usługi Microsoft MAPS**. Upewnij się, że opcja jest włączona i ustawiona na **opcję Mapy podstawowe** lub **Mapy zaawansowane**. Wybierz przycisk **OK**.

    Możesz wysłać podstawowe lub dodatkowe informacje o wykrytym oprogramowaniu:

    - Podstawowe mapy: członkostwo w warstwie Podstawowa będzie wysyłać do firmy Microsoft podstawowe informacje o złośliwym oprogramowaniu i potencjalnie niepożądanym oprogramowaniu wykrytym na urządzeniu. Informacje obejmują lokalizację, z której pochodzi oprogramowanie (na przykład adresy URL i ścieżki częściowe), akcje podjęte w celu rozwiązania zagrożenia oraz to, czy akcje zakończyły się pomyślnie.

    - Mapy zaawansowane: oprócz podstawowych informacji zaawansowane członkostwo będzie wysyłać szczegółowe informacje o złośliwym oprogramowaniu i potencjalnie niepożądanym oprogramowaniu, w tym pełną ścieżkę do oprogramowania oraz szczegółowe informacje o tym, jak oprogramowanie wpłynęło na urządzenie.

6. Kliknij dwukrotnie **pozycję Wyślij przykłady plików, gdy wymagana jest dalsza analiza**. Upewnij się, że pierwsza opcja jest **ustawiona na Włączone** i że inne opcje są ustawione na jedną z następujących opcji:

   - **Wysyłanie bezpiecznych próbek** (1)
   - **Wyślij wszystkie przykłady** (3)

   >[!NOTE]
   > Opcja **Wyślij bezpieczne próbki** (1) oznacza, że większość próbek zostanie wysłana automatycznie. Pliki, które mogą zawierać dane osobowe, będą nadal monitować i wymagać dodatkowego potwierdzenia.
   > Ustawienie opcji **Always Prompt** (0) spowoduje obniżenie stanu ochrony urządzenia. Ustawienie opcji **Nigdy nie wysyłaj** (2) oznacza, że funkcja [Blokuj od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md) Ochrona punktu końcowego w usłudze Microsoft Defender nie będzie działać.

7. Wybierz przycisk **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Włączanie ochrony w chmurze przy użyciu poleceń cmdlet programu PowerShell

Następujące polecenia cmdlet mogą włączyć ochronę w chmurze:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender, zobacz [Konfigurowanie i uruchamianie Program antywirusowy Microsoft Defender i za pomocą poleceń cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) [ Program antywirusowy Microsoft Defender poleceń cmdlet](/powershell/module/defender/). [Dostawca CSP zasad — usługa Defender](/windows/client-management/mdm/policy-csp-defender) zawiera również więcej informacji dotyczących [elementu -SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Możesz ustawić wartość **-SubmitSamplesConsent** ( `SendSafeSamples` ustawienie domyślne, zalecane), `NeverSend`lub `AlwaysPrompt`. Ustawienie `SendSafeSamples` oznacza, że większość przykładów zostanie wysłana automatycznie. Pliki, które mogą zawierać dane osobowe, spowodują wyświetlenie monitu o kontynuowanie i będą wymagały potwierdzenia.
> Ustawienia `NeverSend` i `AlwaysPrompt` obniżają poziom ochrony urządzenia. Ponadto ustawienie oznacza, `NeverSend` że funkcja [Blokuj od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md) Ochrona punktu końcowego w usłudze Microsoft Defender nie będzie działać.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Korzystanie z instrukcji zarządzania Windows (WMI) w celu włączenia ochrony w chmurze

Użyj [metody **Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) dla następujących właściwości:

```WMI
MAPSReporting
SubmitSamplesConsent
```

Aby uzyskać więcej informacji na temat dozwolonych parametrów, zobacz [Windows Defender Interfejsy API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Włączanie ochrony w chmurze dla poszczególnych klientów przy użyciu aplikacji Zabezpieczenia Windows

> [!NOTE]
> Jeśli ustawienie **Konfiguruj ustawienie lokalne dla raportowania usługi Microsoft MAPS** zasady grupy jest ustawione na **Wartość Wyłączone**, ustawienie **ochrony opartej na chmurze** w Windows Ustawienia będzie wyszarzone i niedostępne. Zmiany wprowadzone za pośrednictwem obiektu zasady grupy należy najpierw wdrożyć w poszczególnych punktach końcowych, zanim ustawienie zostanie zaktualizowane w Windows Ustawienia.

1. Otwórz aplikację Zabezpieczenia Windows, wybierając ikonę osłony na pasku zadań lub wyszukując menu Start w poszukiwaniu **Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie), a następnie w obszarze **Zarządzanie ustawieniami** wybierz pozycję **Wirus & ustawienia ochrony przed zagrożeniami**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Ustawienia ochrony przed zagrożeniami & wirusów" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Upewnij się, że usługa **Cloud-based Protection** i **automatyczne przesyłanie przykładów** są przełączone na **włączone**.

   > [!NOTE]
   > Jeśli automatyczne przesyłanie przykładów zostało skonfigurowane przy użyciu zasady grupy, ustawienie będzie wyszarzone i niedostępne.

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

- [Korzystanie z ochrony w chmurze firmy Microsoft w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- [Jak tworzyć i wdrażać zasady ochrony przed złośliwym kodem: usługa ochrony w chmurze](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Za pomocą poleceń cmdlet programu PowerShell zarządzaj programem antywirusowym Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
