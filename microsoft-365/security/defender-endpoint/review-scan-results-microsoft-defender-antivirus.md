---
title: Przejrzyj wyniki skanowania Program antywirusowy Microsoft Defender
description: Przejrzyj wyniki skanowania przy użyciu Microsoft Endpoint Configuration Manager, Microsoft Intune lub aplikacji Zabezpieczenia Windows
keywords: wyniki skanowania, korygowanie, pełne skanowanie, szybkie skanowanie
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 3bbaa19401823eada5b1b9769c259e8296f75924
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417573"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Przeglądanie wyników skanowania Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Po zakończeniu skanowania Program antywirusowy Microsoft Defender, niezależnie od tego, czy jest to skanowanie [na żądanie](run-scan-microsoft-defender-antivirus.md), czy [zaplanowane](scheduled-catch-up-scans-microsoft-defender-antivirus.md), wyniki są rejestrowane i można wyświetlić wyniki. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Przeglądanie wyników skanowania przy użyciu Configuration Manager

Zobacz [Jak monitorować stan Endpoint Protection](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Przeglądanie wyników skanowania przy użyciu poleceń cmdlet programu PowerShell

Następujące polecenie cmdlet zwróci każde wykrycie w punkcie końcowym. Jeśli istnieje wiele wykrycia tego samego zagrożenia, każde wykrycie zostanie wyświetlone oddzielnie na podstawie czasu każdego wykrycia:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="Polecenia cmdlet i dane wyjściowe programu PowerShell" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Można określić `-ThreatID` , aby ograniczyć dane wyjściowe, aby pokazywać tylko wykrycia określonego zagrożenia.

Jeśli chcesz wyświetlić listę wykrywania zagrożeń, ale połączyć wykrywanie tego samego zagrożenia w jeden element, możesz użyć następującego polecenia cmdlet:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="Kod programu PowerShell" lightbox="../../media/wdav-get-mpthreat.png":::

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [poleceń cmdlet programu antywirusowego Defender](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Przeglądanie wyników skanowania przy użyciu instrukcji zarządzania Windows (WMI)

Użyj [metody **Get** klasy **MSFT_MpThreat** i **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

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

- [Dostosowywanie, inicjowanie i przeglądanie wyników skanowania i korygowania Program antywirusowy Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
