---
title: Blokowanie pętli opinii
description: Blokowanie pętli opinii, nazywane także szybką ochroną, jest częścią funkcji blokowania i blokowania zachowań w programie Microsoft Defender for Endpoint
keywords: blokowanie zachowań, szybka ochrona, blokowanie opinii, usługa Microsoft Defender dla punktu końcowego
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
ms.openlocfilehash: 82d5fb32a9535a5b341bca8e5bee989d88ad8232
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997239"
---
# <a name="feedback-loop-blocking"></a>Blokowanie pętli opinii

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

## <a name="overview"></a>Omówienie

Blokowanie pętli opinii, nazywane także szybką ochroną, jest składnikiem funkcji blokowania zachowań i blokowania [](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) w programie [Microsoft Defender for Endpoint](/windows/security/threat-protection/). Dzięki blokowaniu pętli opinii urządzenia w twojej organizacji są lepiej chronione przed atakami. 

## <a name="how-feedback-loop-blocking-works"></a>Jak działa blokowanie pętli opinii

W przypadku wykrycia podejrzanego zachowania lub pliku, na przykład ze [Program antywirusowy Microsoft Defender, informacje](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) o tym artefaktie są wysyłane do wielu klasyfikatorów. System szybkiej pętli ochrony przeprowadza inspekcje i koreluje informacje z innymi sygnałami, aby podjąć decyzję, czy zablokować plik. Sprawdzanie i klasyfikowanie artefaktów odbywa się szybko. Powoduje to szybkie zablokowanie potwierdzonego złośliwego oprogramowania i ochrony dysków w całym ekosystemie. 

Dzięki szybkiej ochronie w miejscu ataki mogą być zatrzymywane na urządzeniu, innych urządzeniach w organizacji i urządzeniach w innych organizacjach, co ma na celu rozszerzenie jego stopki.


## <a name="configuring-feedback-loop-blocking"></a>Konfigurowanie blokowania pętli opinii

Jeśli Twoja organizacja używa programu Defender for Endpoint, blokowanie pętli opinii jest domyślnie włączone. Jednak szybka ochrona jest zapewniana przez połączenie funkcji programu Defender dla punktów końcowych, funkcji ochrony maszynowej i udostępniania sygnału w różnych usługach zabezpieczeń firmy Microsoft. Upewnij się, że włączono i skonfigurowano następujące funkcje i możliwości usługi Defender for Endpoint:

- [Microsoft Defender for Endpoint baselines](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Urządzenia podłączone do programu Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/onboard-configure)

- [EDR w trybie blokowania](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Zmniejszenie powierzchni ataków](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Ochrona następnej generacji](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (oprogramowanie antywirusowe)

## <a name="related-articles"></a>Artykuły pokrewne

- [Blokowanie i blokowanie zachowań](behavioral-blocking-containment.md)

- [(Blog) Blokowanie i zasłanianie zachowania: przekształcanie światłowodów w ochronę](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Przydatne zasoby dotyczące programu Microsoft Defender dla punktów końcowych](/microsoft-365/security/defender-endpoint/helpful-resources)
