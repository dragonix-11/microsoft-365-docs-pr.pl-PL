---
title: Blokowanie pętli opinii
description: Blokowanie pętli sprzężenia zwrotnego, nazywane również szybką ochroną, jest częścią funkcji blokowania behawioralnego i powstrzymywania w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: blokowanie zachowań, szybka ochrona, blokowanie opinii, Ochrona punktu końcowego w usłudze Microsoft Defender
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: f68345b97d49adce2f55cffd837ca17e5b028953
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788001"
---
# <a name="feedback-loop-blocking"></a>Blokowanie pętli opinii

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

## <a name="overview"></a>Omówienie

Blokowanie pętli sprzężenia zwrotnego, nazywane również szybką ochroną, jest składnikiem [funkcji blokowania behawioralnego i hermetyzowania](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) w [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/). W przypadku blokowania pętli sprzężenia zwrotnego urządzenia w całej organizacji są lepiej chronione przed atakami. 

## <a name="how-feedback-loop-blocking-works"></a>Jak działa blokowanie pętli opinii

Po wykryciu podejrzanego zachowania lub pliku, na przykład przez [Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10), informacje o tym artefaktie są wysyłane do wielu klasyfikatorów. Aparat pętli szybkiej ochrony sprawdza i koreluje informacje z innymi sygnałami w celu podjęcia decyzji o zablokowaniu pliku. Sprawdzanie i klasyfikowanie artefaktów odbywa się szybko. Skutkuje to szybkim blokowaniem potwierdzonego złośliwego oprogramowania i zapewnia ochronę w całym ekosystemie. 

Dzięki szybkiej ochronie można zatrzymać atak na urządzeniu, innych urządzeniach w organizacji i urządzeniach w innych organizacjach, ponieważ atak próbuje poszerzyć jego przyczółek.


## <a name="configuring-feedback-loop-blocking"></a>Konfigurowanie blokowania pętli opinii

Jeśli Twoja organizacja używa usługi Defender for Endpoint, blokowanie pętli opinii jest domyślnie włączone. Jednak szybka ochrona odbywa się za pośrednictwem kombinacji funkcji usługi Defender for Endpoint, funkcji ochrony uczenia maszynowego i udostępniania sygnałów w usługach zabezpieczeń firmy Microsoft. Upewnij się, że następujące funkcje i możliwości usługi Defender for Endpoint są włączone i skonfigurowane:

- [Ochrona punktu końcowego w usłudze Microsoft Defender punktów odniesienia](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Urządzenia dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/onboard-configure)

- [Funkcja EDR w trybie blokowania](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Zmniejszanie obszaru podatnego na ataki](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Ochrona następnej generacji](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (program antywirusowy)

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

- [Blokowanie i ograniczanie behawioralne](behavioral-blocking-containment.md)

- [(Blog) Blokowanie i hermetyzowanie zachowań: przekształcanie optyki w ochronę](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Przydatne zasoby Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/helpful-resources)
