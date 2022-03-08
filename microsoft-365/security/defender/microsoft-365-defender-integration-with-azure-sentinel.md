---
title: Microsoft 365 Defender integracji z programem Microsoft Sentinel
description: Użyj programu Microsoft Sentinel jako SIEM do Microsoft 365 Defender zdarzeń i zdarzeń.
keywords: zdarzenia, alerty, badanie, analizowanie, odpowiedź, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: d0add9fe000966cdeb2ffc5ce23e4ba0690bbadb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320287"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>Microsoft 365 Defender integracji z programem Microsoft Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Łącznik Microsoft 365 Defender dla programu Microsoft Sentinel (wersja Preview) wysyła wszystkie Microsoft 365 Defender dotyczące zdarzeń i alertów do programu Microsoft Sentinel i synchronizuje te incydenty. 

Po dodaniu łącznika mogą Microsoft 365 Defender&mdash; która zawiera wszystkie skojarzone alerty, jednostki i odpowiednie informacje otrzymywane z usługi Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender dla usługi Office 365 i Programu Microsoft Defender dla&mdash; aplikacji w chmurze są przesyłane strumieniowo do kanału Microsoft Sentinel jako dane zarządzania zdarzeniami i informacjami o zabezpieczeniach, co zapewnia kontekst do przeprowadzania triage i reagowania na incydenty w programie Microsoft Sentinel. 

Po w programie Microsoft Sentinel zdarzenia są synchronizowane dwukierunkowo z programem Microsoft 365 Defender, co pozwala na korzystanie z zalet portalu Microsoft 365 Defender i programu Microsoft Sentinel w Portalu Azure na temat badania i reagowania na incydenty.

Obejrzyj to krótkie omówienie integracji programu Microsoft Sentinel z usługą Microsoft 365 Defender (4 minuty).

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Oto, jak to działa.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Przepływ i udostępnianie danych dotyczących zdarzeń między programem Microsoft 365 Defender i programem Microsoft Sentinel.":::

## <a name="next-steps"></a>Następne kroki

1. Uzyskaj głębszą wiedzę na [temat Microsoft 365 Defender z programem Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).
2. [Połączenie dane z programu Microsoft 365 Defender do programu Microsoft Sentinel](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń w programie Microsoft 365 Defender](incidents-overview.md)
- [Badanie zdarzeń za pomocą programu Microsoft Sentinel](/azure/sentinel/tutorial-investigate-cases)
