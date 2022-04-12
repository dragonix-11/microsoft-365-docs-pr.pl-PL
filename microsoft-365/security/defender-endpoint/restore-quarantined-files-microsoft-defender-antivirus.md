---
title: Przywróć pliki poddane kwarantannie w programie antywirusowym Microsoft Defender
description: Pliki i foldery, które zostały poddane kwarantannie przez Program antywirusowy Microsoft Defender, można przywrócić.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/19/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 14b6f6812e88a49220230e0e422d5c95f90fe187
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790597"
---
# <a name="restore-quarantined-files-in-microsoft-defender-antivirus"></a>Przywróć pliki poddane kwarantannie w programie antywirusowym Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Jeśli Program antywirusowy Microsoft Defender jest skonfigurowany do wykrywania i korygowania zagrożeń na urządzeniu, Program antywirusowy Microsoft Defender poddawane kwarantannie podejrzane pliki. Jeśli masz pewność, że plik poddany kwarantannie nie stanowi zagrożenia, możesz go przywrócić.

1. Otwórz **Zabezpieczenia Windows**.
2. Wybierz pozycję **Ochrona przed zagrożeniami & wirusami** , a następnie kliknij pozycję **Historia ochrony**.
3. Na liście wszystkich ostatnich elementów filtruj **elementy poddane kwarantannie**.
4. Wybierz element, który chcesz zachować, i wykonaj akcję, taką jak przywracanie.

> [!TIP]
> Przywracanie pliku z kwarantanny można również wykonać przy użyciu wiersza polecenia. Zobacz [Przywracanie pliku z kwarantanny](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts#restore-file-from-quarantine). 

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

- [Konfigurowanie korygowania na potrzeby skanowania](configure-remediation-microsoft-defender-antivirus.md)
- [Przeglądanie wyników skanowania](review-scan-results-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie i weryfikowanie wykluczeń dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie wykluczeń Program antywirusowy Microsoft Defender na serwerze Windows](configure-server-exclusions-microsoft-defender-antivirus.md)