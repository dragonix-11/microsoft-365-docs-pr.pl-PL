---
title: Program antywirusowy Microsoft Defender w systemie Windows
description: Dowiedz się, jak zarządzać programem Microsoft Defender Antivirus, wbudowanej ochrony przed złośliwym oprogramowaniem i wirusami oraz jak go konfigurować i używać.
keywords: Program antywirusowy Microsoft Defender, windows defender, oprogramowanie chroniące przed złośliwym oprogramowaniem, scep, system center endpoint protection, system center configuration manager, wirus, złośliwe oprogramowanie, zagrożenie, wykrywanie, ochrona, zabezpieczenia
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e344c98fd136569015a032bcc83569bc38e06621
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438800"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Program antywirusowy Microsoft Defender w systemie Windows

**Dotyczy:**

- Ochrona punktu końcowego w usłudze Microsoft Defender – plan 1 i 2
- Microsoft Defender dla Firm
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows 

Program antywirusowy Microsoft Defender jest dostępny w systemach Windows 10 i Windows 11 oraz w wersjach systemu Windows Server.

Program antywirusowy Microsoft Defender jest głównym składnikiem ochrony nowej generacji w ochronie punktu końcowego w usłudze Microsoft Defender. Ta ochrona łączy uczenie maszynowe, analizę danych big data, szczegółowe badania odporności na zagrożenia oraz infrastrukturę chmury firmy Microsoft, aby chronić urządzenia (lub punkty końcowe) w organizacji. Program antywirusowy Microsoft Defender jest wbudowany w system Windows i współpracuje z ochroną punktu końcowego w usłudze Microsoft Defender dla zapewnienia ochrony na urządzeniu i w chmurze.

## <a name="compatibility-with-other-antivirus-products"></a>Zgodność z innymi produktami antywirusowymi

Jeśli korzystasz z produktu antywirusowego/chroniącego przed złośliwym oprogramowaniem firmy innej niż Microsoft na urządzeniu, możesz uruchomić program antywirusowy Microsoft Defender w trybie pasywnym obok rozwiązania antywirusowego firmy innej niż Microsoft. Zależy to od używanego systemu operacyjnego i od tego, czy urządzenie zostało dołączone do usługi ochrony punktu końcowego w usłudze Microsoft Defender. Aby dowiedzieć się więcej, zobacz [Zgodność programu antywirusowego Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Porównywanie trybu aktywnego, pasywnego i wyłączonego

W poniższej tabeli opisano, czego można oczekiwać, gdy program antywirusowy Microsoft Defender jest w trybie aktywnym, pasywnym lub wyłączonym.

<br/><br/>

| Tryb | Efekt |
|---|---|
| Tryb aktywny | W trybie aktywnym program antywirusowy Microsoft Defender jest używany jako podstawowa aplikacja antywirusowa na urządzeniu. Pliki są skanowane, zagrożenia są usuwane, a wykryte zagrożenia są wyświetlane w raportach zabezpieczeń organizacji i w Twojej aplikacji Zabezpieczenia Windows. |
| Tryb pasywny | W trybie pasywnym program antywirusowy Microsoft Defender nie jest używany jako podstawowa aplikacja antywirusowa na urządzeniu. Pliki są skanowane i raportowane są wykryte zagrożenia, ale program antywirusowy Microsoft Defender nie usuwa zagrożeń. <br/><br/> **WAŻNE**: Program antywirusowy Microsoft Defender może działać w trybie pasywnym tylko w punktach końcowych dołączonych do ochrony punktu końcowego w usłudze Microsoft Defender. Zobacz [Wymagania, aby program antywirusowy Microsoft Defender działał w trybie pasywnym](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Wyłączone lub odinstalowane | Po wyłączeniu lub odinstalowaniu program antywirusowy Microsoft Defender nie jest używany. Pliki nie są skanowane, a zagrożenia nie są usuwane. Zasadniczo nie zalecamy wyłączania ani odinstalowywania programu antywirusowego Microsoft Defender. |

Aby dowiedzieć się więcej, zobacz [Zgodność programu antywirusowego Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Sprawdź stan programu antywirusowego Microsoft Defender na urządzeniu

Jeśli chcesz sprawdzić stan programu antywirusowego Microsoft Defender na urządzeniu, możesz użyć jednej z kilku metod, takich jak aplikacja Zabezpieczenia Windows lub program Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Sprawdzanie stanu programu antywirusowego Microsoft Defender za pomocą aplikacji Zabezpieczenia Windows

1. Na urządzeniu z systemem Windows wybierz menu Start i zacznij pisać `Security`. Następnie otwórz aplikację Zabezpieczenia Windows w wynikach.

2. Wybierz pozycję **Ochrona przed wirusami i zagrożeniami**.

3. W obszarze **Ustawienia ochrony przed wirusami i zagrożeniami** wybierz opcję **Zarządzaj ustawieniami**.

Nazwa rozwiązania antywirusowego/chroniącego przed złośliwym oprogramowaniem zostanie wyświetlona na stronie ustawień.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>Sprawdzanie stanu programu antywirusowego Microsoft Defender za pomocą programu PowerShell

1. Wybierz menu Start i zacznij wpisywać `PowerShell`. Następnie otwórz program Windows PowerShell w wynikach.

2. Typ: `Get-MpComputerStatus`.

3. Na liście wyników przyjrzyj się wierszowi **AMRunningMode**.

   - **Normalny** oznacza, że program antywirusowy Microsoft Defender działa w trybie aktywnym.

   - **Tryb pasywny** oznacza, że program antywirusowy Microsoft Defender działa, ale nie jest podstawowym produktem antywirusowym/chroniącym przed złośliwym oprogramowaniem na urządzeniu. Tryb pasywny jest dostępny tylko dla urządzeń dołączonych do ochrony punktu końcowego w usłudze Microsoft Defender. Aby dowiedzieć się więcej, zobacz [Wymagania dotyczące uruchamiania programu antywirusowego Microsoft Defender w trybie pasywnym](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **EDR w trybie blokowania** oznacza, że program antywirusowy Microsoft Defender jest uruchomiony i [Wykrycie i odpowiedź punktu końcowego (EDR) w trybie blokowania](edr-in-block-mode.md), funkcja ochrony punktu końcowego w usłudze Microsoft Defender, jest włączona.

   - **Tryb pasywny SxS** oznacza, że program antywirusowy Microsoft Defender działa obok innego produktu antywirusowego/chroniącego przed złośliwym oprogramowaniem i [ używane jest okresowe skanowanie](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Aby dowiedzieć się więcej o poleceniu cmdlet Get-MpComputerStatus programu PowerShell, zobacz artykuł referencyjny [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Pobierz aktualizacje platformy antywirusowej/chroniącej przed złośliwym oprogramowaniem

Ważne jest, aby program antywirusowy Microsoft Defender lub dowolne rozwiązanie antywirusowe/chroniące przed złośliwym oprogramowaniem były aktualne. Firma Microsoft udostępnia regularne aktualizacje, aby zapewnić, że twoje urządzenia mają najnowszą technologię chroniącą przed nowym złośliwym oprogramowaniem i technikami ataków. Aby dowiedzieć się więcej, zobacz [Zarządzanie aktualizacji programu antywirusowego Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md).

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender — zarządzanie i konfiguracja](configuration-management-reference-microsoft-defender-antivirus.md)
- [Oceń ochronę programu antywirusowego Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
