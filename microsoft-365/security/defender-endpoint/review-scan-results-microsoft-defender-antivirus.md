---
title: Przeglądanie wyników skanowania Program antywirusowy Microsoft Defender skanowania
description: Przeglądanie wyników skanów przy użyciu aplikacji Microsoft Endpoint Configuration Manager, Microsoft Intune lub Zabezpieczenia Windows skanowania
keywords: wyniki skanowania, działania naprawcze, pełne skanowanie, szybkie skanowanie
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
ms.openlocfilehash: 8727baa9bb1935a1186907ca5f3d9d4f82dad6d4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473656"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Przeglądanie Program antywirusowy Microsoft Defender wyników skanowania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Po Program antywirusowy Microsoft Defender skanowania na żądanie, niezależnie od [tego, czy](scheduled-catch-up-scans-microsoft-defender-antivirus.md) jest to [](run-scan-microsoft-defender-antivirus.md) skanowanie na żądanie, czy zaplanowane, wyniki są rejestrowane i można wyświetlić wyniki. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Przeglądanie Configuration Manager wyników skanowania za pomocą funkcji Skanowania

Zobacz [Jak monitorować Endpoint Protection stanu](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Przeglądanie wyników skanowania za pomocą poleceń cmdlet programu PowerShell

Następujące polecenie cmdlet zwróci każde wykrywanie w punkcie końcowym. Jeśli istnieje wiele wykrywanie tego samego zagrożenia, każde wykrywanie będzie wyświetlane oddzielnie w zależności od czasu każdego wykrywania:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="Polecenia cmdlet i dane wyjściowe programu PowerShell" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Możesz określić, `-ThreatID` czy dane wyjściowe mają być wyświetlane tylko w przypadku wykrycia określonego zagrożenia.

Jeśli chcesz wyświetlić listę wykrywania zagrożeń, ale połączyć wykrywanie tego samego zagrożenia w jeden element, możesz użyć następującego polecenia cmdlet:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="Kod programu PowerShell" lightbox="../../media/wdav-get-mpthreat.png":::

Aby [uzyskać więcej informacji na](use-powershell-cmdlets-microsoft-defender-antivirus.md) temat używania programu PowerShell z programem PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń cm Program antywirusowy Microsoft Defender dlet programu PowerShell oraz poleceń [cmdlet programu Defender](/powershell/module/defender/) oraz Program antywirusowy Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Przeglądanie wyników skanowania za pomocą Windows zarządzania danymi (WMI)

Użyj metody [**Get** (Pobierz) **MSFT_MpThreat** i **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) zajęć.


## <a name="related-articles"></a>Artykuły pokrewne

- [Dostosowywanie, inicjowanie i przeglądanie wyników skanów Program antywirusowy Microsoft Defender środków zaradczych](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
