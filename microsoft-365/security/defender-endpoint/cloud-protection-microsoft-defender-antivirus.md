---
title: Ochrona i Program antywirusowy Microsoft Defender
description: Dowiedz się więcej o ochronie i Program antywirusowy Microsoft Defender
keywords: Program antywirusowy Microsoft Defender, technologie następnej generacji, audio/wideo nowej generacji, uczenie maszynowe, ochrona przed złośliwym kodem, zabezpieczenia, defender, chmura, ochrona w chmurze
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
ms.openlocfilehash: 013b189dca95fc63dc8d189d020fcf3f7727cf82
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996769"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>Ochrona i Program antywirusowy Microsoft Defender

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Technologie następnej generacji w Program antywirusowy Microsoft Defender natychmiastową, automatyczną ochronę przed nowymi i wyłaniających się zagrożeniami. Aby dynamicznie identyfikować nowe zagrożenia, technologie następnej generacji działają z dużymi zestawami połączonych danych w inteligentnych systemach zabezpieczeń firmy Microsoft Graph oraz zaawansowanych systemach sztucznej inteligencji sterowanej przez zaawansowane modele uczenia maszynowego. Ochrona chmury współpracuje z Program antywirusowy Microsoft Defender, aby zapewniać dokładną, inteligentną ochronę w czasie rzeczywistym. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Diagram przedstawiający współpracę ochrony chmury z siecią Program antywirusowy Microsoft Defender":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Zalecamy, aby ochrona chmury została włączona. Aby dowiedzieć się więcej, zobacz [Dlaczego ochrona chmury powinna być włączona dla Program antywirusowy Microsoft Defender](why-cloud-protection-should-be-on-mdav.md). 

## <a name="how-cloud-protection-works"></a>Jak działa ochrona chmury

Program antywirusowy Microsoft Defender bezproblemowo współpracuje z usługami firmy Microsoft w chmurze. Te usługi ochrony w chmurze, nazywane także usługą MICROSOFT Advanced Protection Service (MAPS), ulepszają standardową ochronę w czasie rzeczywistym. Dzięki ochronie w chmurze technologie następnej generacji zapewniają szybką identyfikację nowych zagrożeń, czasami nawet zanim jeden punkt końcowy zostanie zainfekowany. 

W poniższych wpisach w blogu pokazano, jak działa ochrona chmury:

- [Poznaj zaawansowane technologie w centrum ochrony następnej generacji programu Microsoft Defender for Endpoint](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [Dlaczego Program antywirusowy Microsoft Defender jest najbardziej wdrożony w przedsiębiorstwie](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [Monitorowanie zachowania w połączeniu z procesem uczenia maszynowego olbrzymią kampanią wyszukiwania monet](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [Jak sztuczna inteligencja zatrzymała epidemię "Emotet"](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [Detonowanie złej edukacji: Program antywirusowy Microsoft Defender i warstwowa obrona maszynowa do nauki](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [Program antywirusowy Microsoft Defender usługi ochrony w chmurze: Zaawansowana ochrona w czasie rzeczywistym przed nigdy niewiedzianym złośliwym oprogramowaniem](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> Usługa Program antywirusowy Microsoft Defender w chmurze to mechanizm dostarczania zaktualizowanej ochrony do Sieci i punktów końcowych. Jako usługa w chmurze nie jest po prostu ochroną plików przechowywanych w chmurze; Zamiast tego usługa w chmurze korzysta z zasobów rozłożonych i uczenia maszynowego w celu dostarczania ochrony do punktów końcowych w tempie znacznie szybszym niż tradycyjne aktualizacje analizy zabezpieczeń.

## <a name="how-to-get-cloud-protection"></a>Jak uzyskać ochronę chmury 

Ochrona chmury jest domyślnie włączona. Może być jednak konieczne ponowne włączenie tej funkcji, jeśli została wyłączona w ramach poprzednich zasad organizacji. Aby dowiedzieć się więcej, [zobacz Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md).

Jeśli Twoja subskrypcja obejmuje Windows 10 E5, możesz korzystać z aktualizacji analizy dynamicznej sytuacji awaryjnych, które zapewniają ochronę w czasie rzeczywistym przed pojawiającymi się zagrożeniami. Po włączeniu ochrony chmury rozwiązania problemów ze złośliwym oprogramowaniem mogą być dostarczane za pośrednictwem chmury w ciągu kilku minut, zamiast czekać na następną aktualizację. Zobacz [Konfigurowanie Program antywirusowy Microsoft Defender automatycznego otrzymywania nowych aktualizacji ochrony na podstawie raportów z naszej usługi w chmurze](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates).

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz już omówienie ochrony chmury w programie Program antywirusowy Microsoft Defender, poniżej przedstawiono kilka następnych kroków:

1. Zobacz [Dlaczego ochrona chmury powinna być włączona dla Program antywirusowy Microsoft Defender](why-cloud-protection-should-be-on-mdav.md).

2. Przejdź do [włączania ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)