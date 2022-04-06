---
title: Ochrona punktu końcowego w usłudze Microsoft Defender flag zdarzeń osi czasu urządzenia
description: Użyj Ochrona punktu końcowego w usłudze Microsoft Defender flag zdarzeń osi czasu urządzenia do
keywords: Oś czasu urządzenia programu Defender dla punktu końcowego, flagi zdarzeń
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 44292893249872c1c4b8dc3b4f66d10085fb0a2b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471192"
---
# <a name="microsoft-defender-for-endpoint-device-timeline-event-flags"></a>Ochrona punktu końcowego w usłudze Microsoft Defender flag zdarzeń osi czasu urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Flagi zdarzeń na osi czasu aplikacji Defender for Endpoint ułatwiają filtrowanie i organizowanie określonych zdarzeń podczas zbadania potencjalnych ataków.

Oś czasu urządzenia programu Defender dla punktu końcowego zapewnia chronologiczny widok zdarzeń i skojarzonych z nimi alertów obserwowanych na urządzeniu. Ta lista zdarzeń zapewnia pełną widoczność wszystkich zdarzeń, plików i adresów IP obserwowanych na urządzeniu. Lista może czasami być długość. Flagi zdarzeń osi czasu urządzenia ułatwiają śledzenie zdarzeń, które mogą być powiązane.

Po przebyeniu osi czasu urządzenia możesz sortować, filtrować i eksportować określone oflagowane zdarzenia.

Podczas poruszania się po osi czasu urządzenia możesz wyszukiwać i filtrować konkretne zdarzenia. Flagi zdarzeń można ustawić przez:

- Wyróżnianie najważniejszych zdarzeń
- Oznaczanie wydarzeń, które wymagają dogłębnego zejdowania
- Tworzenie czystej osi czasu naruszenia

## <a name="flag-an-event"></a>Oznaczanie zdarzenia flagą

1. Znajdowanie zdarzenia, które chcesz oflagować

2. Kliknij ikonę flagi w kolumnie Flaga. 

:::image type="content" source="images/device-flags.png" alt-text="Flaga osi czasu urządzenia" lightbox="images/device-flags.png":::

## <a name="view-flagged-events"></a>Wyświetlanie oflagowanych zdarzeń

1. W sekcji Filtry **osi czasu** włącz **opcję Oflagowane zdarzenia**.
2. Kliknij przycisk **Zastosuj**. Wyświetlane są tylko oflagowane zdarzenia.

Możesz zastosować dodatkowe filtry, klikając pasek czasu. Spowoduje to pokazanie tylko zdarzeń przed oflagowanym zdarzeniem.  

:::image type="content" source="images/device-flag-filter.png" alt-text="Flaga osi czasu urządzenia z włączonym filtrem" lightbox="images/device-flag-filter.png":::