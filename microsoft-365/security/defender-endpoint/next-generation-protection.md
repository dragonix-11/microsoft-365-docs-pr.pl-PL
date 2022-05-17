---
title: Omówienie ochrony nowej generacji w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Zapoznaj się z omówieniem ochrony nowej generacji w Ochrona punktu końcowego w usłudze Microsoft Defender. Wzmacnianie obwodu zabezpieczeń sieci przy użyciu ochrony nowej generacji przeznaczonej do przechwytywania wszystkich typów pojawiających się zagrożeń.
keywords: Program antywirusowy Microsoft Defender, windows defender, ochrona przed złośliwym kodem, wirus, złośliwe oprogramowanie, zagrożenie, wykrywanie, ochrona, zabezpieczenia
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
ms.collection: M365-security-compliance
ms.openlocfilehash: 99790921d51bf6d7b5a7268c541b4f754e7b99c9
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438866"
---
# <a name="next-generation-protection-overview"></a>Omówienie ochrony nowej generacji

**Dotyczy**

- Program antywirusowy Microsoft Defender
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/index.yml)

**Platformy**
- System Windows

Ochrona punktu końcowego w usłudze Microsoft Defender obejmuje ochronę nowej generacji w celu wzmocnienia obwodu zabezpieczeń sieci. Ochrona nowej generacji została zaprojektowana w celu wychwytywania wszystkich rodzajów pojawiających się zagrożeń. Oprócz Program antywirusowy Microsoft Defender usługi ochrony nowej generacji obejmują następujące możliwości:

- [Ochrona antywirusowa oparta na zachowaniu, heurystycznym i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md), która obejmuje zawsze włączone skanowanie przy użyciu monitorowania zachowania plików i procesów oraz innych heurystycznych (znanych również jako *ochrona w czasie rzeczywistym*). Obejmuje ona również wykrywanie i blokowanie aplikacji, które są uważane za niebezpieczne, ale mogą nie zostać wykryte jako złośliwe oprogramowanie.
- [Ochrona dostarczana przez chmurę](cloud-protection-microsoft-defender-antivirus.md), która obejmuje niemal natychmiastowe wykrywanie i blokowanie nowych i pojawiających się zagrożeń.
- [Dedykowana ochrona i aktualizacje produktów](manage-updates-baselines-microsoft-defender-antivirus.md), które obejmują aktualizacje związane z aktualizowaniem Program antywirusowy Microsoft Defender.

> [!TIP]
> Ochrona nowej generacji jest uwzględniona zarówno w planie Ochrona punktu końcowego w usłudze Microsoft Defender 1, jak i planie 2. [Dowiedz się więcej o usłudze Defender for Endpoint Plan 1 i Plan 2](defender-endpoint-plan-1-2.md) Ochrona nowej generacji jest również uwzględniana w Microsoft Defender dla Firm i Microsoft 365 Business Premium. [Porównanie funkcji zabezpieczeń w planach Microsoft 365 dla małych i średnich firm](../defender-business/compare-mdb-m365-plans.md).

## <a name="try-a-demo"></a>Wypróbuj pokaz!

Odwiedź [witrynę internetową Ochrona punktu końcowego w usłudze Microsoft Defender demo](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby potwierdzić, że działają następujące funkcje ochrony, i zapoznaj się z nimi przy użyciu scenariuszy demonstracyjnych:

- Ochrona dostarczana przez chmurę
- Blokuj ochronę od pierwszego wejrzenia (BAFS)
- Ochrona potencjalnie niechcianych aplikacji (PUA)

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="configure-next-generation-protection-services"></a>Konfigurowanie usług ochrony nowej generacji

Aby uzyskać informacje na temat konfigurowania usług ochrony nowej generacji, zobacz [Konfigurowanie funkcji Program antywirusowy Microsoft Defender](configure-microsoft-defender-antivirus-features.md).

> [!NOTE]
> Konfiguracja i zarządzanie w Windows Server są w dużej mierze takie same jak w przypadku klientów Windows. Istnieją jednak pewne różnice. 

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

