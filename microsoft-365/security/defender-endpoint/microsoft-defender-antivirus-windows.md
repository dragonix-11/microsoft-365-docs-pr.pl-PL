---
title: Program antywirusowy Microsoft Defender w programie Windows
description: Dowiedz się, jak konfigurować i używać oprogramowania Program antywirusowy Microsoft Defender, wbudowanej ochrony przed złośliwym oprogramowaniem i oprogramowaniem antywirusowym.
keywords: Program antywirusowy Microsoft Defender, windows defender, antimalware, scep, system center endpoint protection, system center configuration manager, virus, malware, threat, detection, protection, security
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
ms.openlocfilehash: b6eabc3527742b6cc7f06d23207db813b827e5f5
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009557"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Program antywirusowy Microsoft Defender w programie Windows

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender jest dostępna w Windows 10 i Windows 11 oraz w wersjach programu Windows Server.

Program antywirusowy Microsoft Defender jest głównym elementem ochrony następnej generacji w programie Microsoft Defender for Endpoint. Ta ochrona łączy uczenie maszynowe, analizę dużych danych, szczegółowe badania odporność na zagrożenia oraz infrastrukturę chmury firmy Microsoft w celu ochrony urządzeń (lub punktów końcowych) w organizacji. Program antywirusowy Microsoft Defender jest wbudowany w usługę Windows i współpracuje z programem Microsoft Defender for Endpoint w celu zapewnienia ochrony na urządzeniu i w chmurze.

## <a name="compatibility-with-other-antivirus-products"></a>Zgodność z innymi produktami antywirusowymi

Jeśli używasz na urządzeniu produktu antywirusowego/ochrony przed złośliwym oprogramowaniem firmy Microsoft, możesz mieć możliwość uruchomienia programu Program antywirusowy Microsoft Defender w trybie pasywnym obok rozwiązania antywirusowego firmy innych niż Microsoft. Zależy to od używanego systemu operacyjnego i od tego, czy urządzenie jest w nim używane w programie Defender for Endpoint. Aby dowiedzieć się więcej, [zobacz Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Porównanie trybu aktywnego, pasywnego i wyłączonego

W poniższej tabeli opisano, czego można oczekiwać Program antywirusowy Microsoft Defender w trybie aktywnym, w trybie pasywnym lub w trybie wyłączonym.

<br/><br/>

| Tryb | Co się dzieje |
|---|---|
| Tryb aktywny | W trybie aktywnym Program antywirusowy Microsoft Defender jako podstawowa aplikacja antywirusowa na urządzeniu. Pliki są skanowane, są korygowane zagrożenia, a wykryte zagrożenia są wymienione w raportach zabezpieczeń organizacji oraz w Zabezpieczenia Windows sieci. |
| Tryb pasywny | W trybie pasywnym Program antywirusowy Microsoft Defender nie jest używana jako podstawowa aplikacja antywirusowa na urządzeniu. Pliki są skanowane i raportowane są wykryte zagrożenia, ale nie są one korygowane przez Program antywirusowy Microsoft Defender. <br/><br/> **WAŻNE**: Program antywirusowy Microsoft Defender działać w trybie pasywnym tylko w przypadku punktów końcowych, które są wnoszone do programu Microsoft Defender for Endpoint. Zobacz [Wymagania dotyczące Program antywirusowy Microsoft Defender w trybie pasywnym](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Wyłączone lub odinstalowane | Po wyłączeniu lub odinstalowaniu Program antywirusowy Microsoft Defender nie jest używana. Pliki nie są skanowane, a działania zagrożeń nie są korygowane. Ogólnie nie zalecamy wyłączania ani odinstalowywania Program antywirusowy Microsoft Defender. |

Aby dowiedzieć się więcej, [zobacz Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Sprawdzanie stanu Program antywirusowy Microsoft Defender na urządzeniu

Aby sprawdzić stan plików na Program antywirusowy Microsoft Defender, możesz użyć jednej z kilku metod, takich jak aplikacja Zabezpieczenia Windows lub Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Sprawdź stan Zabezpieczenia Windows za pomocą aplikacji Program antywirusowy Microsoft Defender

1. Na urządzeniu Windows wybierz przycisk i menu Start zacznij pisać `Security`. Następnie otwórz Zabezpieczenia Windows w wynikach.

2. Wybierz **pozycję Ochrona & przed zagrożeniami**.

3. W **obszarze & ochrony przed zagrożeniami** wybierz pozycję **Zarządzaj ustawieniami**.

Na stronie ustawień zobaczysz nazwę rozwiązania antywirusowego/ochrony przed złośliwym oprogramowaniem.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>Sprawdzanie stanu Program antywirusowy Microsoft Defender

1. Zaznacz menu Start i zacznij pisać `PowerShell`. Następnie otwórz Windows PowerShell w wynikach wyszukiwania.

2. Typ: `Get-MpComputerStatus`.

3. Na liście wyników spójrz na wiersz **AMRunningMode** .

   - **Normalne** oznacza Program antywirusowy Microsoft Defender że program działa w trybie aktywnym.

   - **Tryb pasywny** Program antywirusowy Microsoft Defender uruchomiony, ale nie jest podstawowym produktem antywirusowym/ochrony przed złośliwym kodem na Twoim urządzeniu. Tryb pasywny jest dostępny tylko dla urządzeń, które są podłączone do programu Microsoft Defender for Endpoint i spełniają określone wymagania. Aby dowiedzieć się więcej, [zobacz Wymagania dotyczące Program antywirusowy Microsoft Defender w trybie pasywnym](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **EDR tryb** blokowania oznacza Program antywirusowy Microsoft Defender że jest uruchomiony, a wykrywanie punktu końcowego i odpowiedź [(EDR)](edr-in-block-mode.md) w trybie blokowania jest włączona funkcja w programie Microsoft Defender dla punktu końcowego.

   - **Tryb pasywny SxS** oznacza Program antywirusowy Microsoft Defender jest uruchomiony obok innego produktu antywirusowego/ochrony przed złośliwym kodem i jest używane ograniczone [skanowanie okresowe](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Aby dowiedzieć się więcej o Get-MpComputerStatus cmdlet programu PowerShell, zobacz artykuł [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Uzyskiwanie aktualizacji platformy antywirusowej/ochrony przed złośliwym oprogramowaniem

Ważne jest, aby oprogramowanie Program antywirusowy Microsoft Defender lub dowolne rozwiązanie antywirusowe/zapobiegające złośliwym oprogramowaniem, było aktualne. Firma Microsoft wydaje regularne aktualizacje, aby upewnić się, że Twoje urządzenia mają najnowsze technologie ochrony przed nowym złośliwym oprogramowaniem i technikami ataków. Aby dowiedzieć się więcej, zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender zarządzanie i konfiguracja](configuration-management-reference-microsoft-defender-antivirus.md)
- [Ocenianie Program antywirusowy Microsoft Defender danych](evaluate-microsoft-defender-antivirus.md)
