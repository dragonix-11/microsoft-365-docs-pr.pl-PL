---
title: Ochrona w chmurze i program antywirusowy Microsoft Defender
description: Dowiedz się więcej o ochronie chmury i Program antywirusowy Microsoft Defender
keywords: Program antywirusowy Microsoft Defender, technologie nowej generacji, av nowej generacji, uczenie maszynowe, oprogramowanie chroniące przed złośliwym kodem, zabezpieczenia, defender, chmura, ochrona w chmurze
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 0cba725ed27d652366e681adccdec8dbefa68ecd
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788089"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>Ochrona w chmurze i program antywirusowy Microsoft Defender

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Technologie nowej generacji w Program antywirusowy Microsoft Defender zapewniają niemal natychmiastową, zautomatyzowaną ochronę przed nowymi i pojawiającym się zagrożeniami. Aby dynamicznie identyfikować nowe zagrożenia, technologie nowej generacji współpracują z dużymi zestawami połączonych ze sobą danych w systemach microsoft Intelligent Security Graph i zaawansowanych systemach sztucznej inteligencji (AI) opartych na zaawansowanych modelach uczenia maszynowego. Ochrona w chmurze współdziała z Program antywirusowy Microsoft Defender w celu zapewnienia dokładnej, w czasie rzeczywistym i inteligentnej ochrony. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Diagram przedstawiający sposób współdziałania ochrony chmury z Program antywirusowy Microsoft Defender" lightbox="images/mde-cloud-protection.png":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Zalecamy włączenie ochrony w chmurze. Aby dowiedzieć się więcej, zobacz [Dlaczego ochrona w chmurze powinna być włączona dla Program antywirusowy Microsoft Defender](why-cloud-protection-should-be-on-mdav.md). 

## <a name="how-cloud-protection-works"></a>Jak działa ochrona w chmurze

Program antywirusowy Microsoft Defender bezproblemowo współpracuje z usługami firmy Microsoft w chmurze. Te usługi ochrony w chmurze, nazywane również usługą Microsoft Advanced Protection Service (MAPS), zwiększają standardową ochronę w czasie rzeczywistym. Dzięki ochronie w chmurze technologie nowej generacji zapewniają szybką identyfikację nowych zagrożeń, czasami nawet przed zainfekowaniem pojedynczego punktu końcowego. 

Poniższe wpisy w blogu ilustrują działanie ochrony w chmurze:

- [Poznaj zaawansowane technologie, które są podstawą Ochrona punktu końcowego w usłudze Microsoft Defender ochrony nowej generacji](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [Dlaczego Program antywirusowy Microsoft Defender jest najczęściej wdrażana w przedsiębiorstwie](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [Monitorowanie zachowania w połączeniu z uczeniem maszynowym psuje ogromną kampanię wydobycia monet](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [Jak sztuczna inteligencja zatrzymała epidemię "Emotet"](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [Detonacja złego królika: Program antywirusowy Microsoft Defender i warstwowe mechanizmy obronne uczenia maszynowego](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [Program antywirusowy Microsoft Defender usługi ochrony w chmurze: zaawansowana ochrona w czasie rzeczywistym przed nigdy wcześniej nie widzianym złośliwym oprogramowaniem](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> Usługa w chmurze Program antywirusowy Microsoft Defender to mechanizm zapewniający zaktualizowaną ochronę sieci i punktów końcowych. Jako usługa w chmurze nie jest to po prostu ochrona plików przechowywanych w chmurze; Zamiast tego usługa w chmurze korzysta z zasobów rozproszonych i uczenia maszynowego, aby zapewnić ochronę punktów końcowych w tempie znacznie szybszym niż tradycyjne aktualizacje analizy zabezpieczeń.

## <a name="how-to-get-cloud-protection"></a>Jak uzyskać ochronę w chmurze 

Ochrona w chmurze jest domyślnie włączona. Jednak może być konieczne ponowne włączenie go, jeśli zostało wyłączone w ramach poprzednich zasad organizacyjnych. Aby dowiedzieć się więcej, zobacz [Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md).

Jeśli Twoja subskrypcja obejmuje Windows 10 E5, możesz skorzystać z awaryjnych aktualizacji analizy dynamicznej, które zapewniają niemal w czasie rzeczywistym ochronę przed pojawiającym się zagrożeniami. Po włączeniu ochrony w chmurze poprawki problemów ze złośliwym oprogramowaniem można dostarczyć za pośrednictwem chmury w ciągu kilku minut, zamiast czekać na następną aktualizację. Zobacz [Konfigurowanie Program antywirusowy Microsoft Defender, aby automatycznie otrzymywać nowe aktualizacje ochrony na podstawie raportów z naszej usługi w chmurze](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates).

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz omówienie ochrony w chmurze w Program antywirusowy Microsoft Defender, oto kilka następnych kroków:

1. Zobacz [Dlaczego ochrona w chmurze powinna być włączona dla Program antywirusowy Microsoft Defender](why-cloud-protection-should-be-on-mdav.md).

2. Przejdź do [sekcji Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)