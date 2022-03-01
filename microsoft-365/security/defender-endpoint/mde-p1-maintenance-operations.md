---
title: Zarządzanie usługą Microsoft Defender dla punktu końcowego (plan 1)
description: Obsługa i aktualizowanie usługi Defender dla punktu końcowego (plan 1). Zarządzaj ustawieniami, otrzymuj aktualizacje i wyadresuj wartości fałszywie dodatnie/ujemne.
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
ms.openlocfilehash: 69e4df29817675918873e4d13b81bfe5b00b1219
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033768"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Zarządzanie usługą Microsoft Defender dla punktu końcowego (plan 1)

**Dotyczy**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Gdy używasz usługi Defender for Endpoint Plan 1 w organizacji, Twój zespół zabezpieczeń może podjąć pewne kroki w celu utrzymania rozwiązania zabezpieczającego. W ramach tego, jak Twój zespół zabezpieczeń łączy Twój plan konserwacji i operacji, pamiętaj, aby uwzględnić co najmniej następujące działania:

- [Zarządzanie analizą zabezpieczeń i aktualizacjami produktów](#manage-security-intelligence-and-product-updates)
- [Dostosowywanie i dostosowywanie usługi Defender dla punktu końcowego](#fine-tune-and-adjust-defender-for-endpoint)
- [Adres fałszywie dodatnie/ujemne](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Zarządzanie analizą zabezpieczeń i aktualizacjami produktów

Zapewnienie Program antywirusowy Microsoft Defender na bieżąco ma kluczowe znaczenie dla ochrony przed nowym złośliwym oprogramowaniem i technikami ataków. Firma Microsoft wydaje regularne aktualizacje dotyczące ochrony zabezpieczeń, oprogramowania antywirusowego i ochrony przed złośliwym kodem. Aktualizacje są podzielone na dwie kategorie: 

- Aktualizacje analizy zabezpieczeń
- Aktualizacje produktów 

Aby zarządzać analizą zabezpieczeń i aktualizacjami produktów, zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Dostosowywanie i dostosowywanie usługi Defender dla punktu końcowego

Program Defender for Endpoint oferuje większą elastyczność i opcje konfiguracji. Możesz dostosować i dostosować ustawienia do potrzeb swojej organizacji. Na przykład możesz zarządzać ustawieniami zabezpieczeń punktu końcowego Microsoft Endpoint Manager, zasady grupy i innymi metodami. 

Aby dowiedzieć się więcej, zobacz [Zarządzanie programem Defender dla punktu końcowego](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Adres fałszywie dodatnie/ujemne

Wyniki fałszywie dodatnie są artefaktem, na przykład plikiem lub procesem, który został wykryty jako złośliwy, mimo że w rzeczywistości nie jest to zagrożenie. Wartość fałszywa ujemna to podmiot, który nie został wykryty jako zagrożenie, mimo że w rzeczywistości jest nim. Wartości fałszywie dodatnie/ujemne mogą występować w przypadku dowolnego rozwiązania ochrony punktu końcowego, łącznie z programem Defender for Endpoint. Istnieje jednak kilka czynności, które możesz wykonać, aby rozwiązać te rodzaje problemów i dopracować swoje rozwiązanie, jak przedstawiono na poniższej ilustracji:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Omówienie procesu wyników fałszywie dodatnich i ujemnych":::

Jeśli w programie Defender for Endpoint wartości dodatnie/ujemne są fałszywie dodatnie, zobacz Adres wyników fałszywie dodatnich/ujemnych w programie [Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>Następne kroki

- [Zobacz, co nowego w programie Microsoft Defender dla punktu końcowego](whats-new-in-microsoft-defender-endpoint.md)