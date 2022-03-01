---
title: Obsługiwane Microsoft 365 Defender API
description: Obsługiwane Microsoft 365 Defender API
keywords: Microsoft 365 Defender, interfejsy API, interfejsy API
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1785186f778c489cb4a254fe39cc41921a4de86e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013372"
---
# <a name="supported-microsoft-365-defender-apis"></a>Obsługiwane Microsoft 365 Defender API 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

## <a name="list-of-available-apis"></a>Lista dostępnych interfejsów API

Artykuł | Opis
-|-
[Zaawansowany interfejs API łowiectwo](api-advanced-hunting.md) | Uruchom zaawansowane zapytania myśliwskie.
[Interfejsy API zdarzenia](api-incident.md) | Wymień i aktualizuj zdarzenia oraz inne praktyczne zadania.
[Interfejs API przesyłania strumieniowego](streaming-api.md) | Wysyłaj zdarzenia i alerty w czasie rzeczywistym w momencie ich wystąpienia w pojedynczym strumieniu danych.

### <a name="endpoint-uris"></a>URI punktu końcowego

Podstawowy URI dla obu głównych interfejsów API to: https://api.security.microsoft.com. Aby uzyskać lepszą wydajność, użyj serwera bliżej Twojej lokalizacji geograficznej:

- Stany Zjednoczone: api-us.security.microsoft.com
- Europa: api-eu.security.microsoft.com
- Zjednoczone Królestwo: api-uk.security.microsoft.com

Tokeny można nabyć, mając dostęp https://api.security.microsoft.comdo konta .

Wszystkie interfejsy API wzdłuż ścieżki `/api` używają protokołu [OData](/odata/overview) , na przykład https://api.security.microsoft.com/api/incidents.

## <a name="related-articles"></a>Artykuły pokrewne

- [Microsoft 365 Defender interfejsów API — omówienie](api-overview.md)
- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Interfejs API przesyłania strumieniowego](../defender-endpoint/raw-data-export.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
- [Opis kodów błędów](api-error-codes.md)
