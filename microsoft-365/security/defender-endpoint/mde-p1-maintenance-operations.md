---
title: Zarządzanie planem Ochrona punktu końcowego w usłudze Microsoft Defender 1
description: Obsługa i aktualizowanie usługi Defender dla planu 1 punktu końcowego. Zarządzaj ustawieniami, pobieraj aktualizacje i usuwaj wyniki fałszywie dodatnie/ujemne.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 417dd33eed846e45453464e63ff403374ce224dc
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667411"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Zarządzanie planem Ochrona punktu końcowego w usłudze Microsoft Defender 1

**Dotyczy**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Podczas korzystania z usługi Defender for Endpoint Plan 1 w organizacji zespół ds. zabezpieczeń może podjąć pewne kroki w celu utrzymania rozwiązania zabezpieczeń. Ponieważ zespół ds. zabezpieczeń tworzy plan konserwacji i operacji, pamiętaj o uwzględnieniu co najmniej następujących działań:

- [Zarządzanie analizą zabezpieczeń i aktualizacjami produktów](#manage-security-intelligence-and-product-updates)
- [Dostosuj i dostosuj usługę Defender dla punktu końcowego](#fine-tune-and-adjust-defender-for-endpoint)
- [Adresowanie wyników fałszywie dodatnich/ujemnych](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Zarządzanie analizą zabezpieczeń i aktualizacjami produktów

Aktualizowanie Program antywirusowy Microsoft Defender ma kluczowe znaczenie dla ochrony przed nowym złośliwym oprogramowaniem i technikami ataku. Firma Microsoft udostępnia regularne aktualizacje dotyczące analizy zabezpieczeń, oprogramowania antywirusowego i ochrony przed złośliwym kodem. Aktualizacje są podzielone na dwie kategorie: 

- Aktualizacje analizy zabezpieczeń
- Aktualizacje produktów 

Aby zarządzać analizą zabezpieczeń i aktualizacjami produktów, zobacz [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Dostosuj i dostosuj usługę Defender dla punktu końcowego

Usługa Defender for Endpoint oferuje dużą elastyczność i opcje konfiguracji. Możesz dostosować i dostosować ustawienia zgodnie z potrzebami organizacji. Można na przykład użyć Microsoft Endpoint Manager, zasady grupy i innych metod do zarządzania ustawieniami zabezpieczeń punktu końcowego. 

Aby dowiedzieć się więcej, zobacz [Zarządzanie usługą Defender dla punktu końcowego](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Adresowanie wyników fałszywie dodatnich/ujemnych

Wynik fałszywie dodatni jest artefaktem, takim jak plik lub proces, który został wykryty jako złośliwy, mimo że w rzeczywistości nie stanowi zagrożenia. Wartość fałszywie ujemna to jednostka, która nie została wykryta jako zagrożenie, mimo że w rzeczywistości jest. Wyniki fałszywie dodatnie/ujemne mogą wystąpić w przypadku dowolnego rozwiązania ochrony punktu końcowego, w tym usługi Defender for Endpoint. Istnieją jednak kroki, które można wykonać, aby rozwiązać tego rodzaju problemy i dostosować rozwiązanie, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Omówienie procesu wyników fałszywie dodatnich i ujemnych" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

Jeśli widzisz wyniki fałszywie dodatnie/ujemne w usłudze Defender for Endpoint, zobacz [Address false positives/negatives in Ochrona punktu końcowego w usłudze Microsoft Defender (Adresowanie fałszywych alarmów/negatywów w Ochrona punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)).

## <a name="next-steps"></a>Następne kroki

- [Zobacz, co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender](whats-new-in-microsoft-defender-endpoint.md)