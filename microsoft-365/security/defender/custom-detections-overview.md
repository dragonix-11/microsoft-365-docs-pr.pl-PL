---
title: Omówienie niestandardowych wykrywania w Microsoft 365 Defender
description: Dowiedz się, jak korzystać z zaawansowanego wyszukiwania w celu tworzenia niestandardowych wykrywania i generowania alertów
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 0ad75d2cf67360c04597f56816e22755fae3388b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988382"
---
# <a name="custom-detections-overview"></a>Wykrywanie niestandardowe — omówienie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Dzięki niestandardowym wykryciom możesz aktywnie monitorować różne zdarzenia i stany systemowe, w tym podejrzewane naruszenie i nieprawidłowo skonfigurowane punkty końcowe, oraz reagować na nie. Jest to możliwe dzięki dostosowywalnym regułom wykrywania, które automatycznie wyzwalają alerty, a także akcje odpowiedzi.

Wykrywanie niestandardowe umożliwia zaawansowane [wyszukiwanie, które](advanced-hunting-overview.md) zapewnia zaawansowany, elastyczny język zapytań, który obejmuje szeroki zestaw informacji o wydarzeniach i systemie z Twojej sieci. Można je tak skonfigurować, aby były uruchamiane w regularnych interwałach, generując alerty i uruchamiając akcje reagowania, gdy tylko zostaną one zes względu na dopasowania.

Wykrywanie niestandardowe zapewnia:
- Alerty dotyczące wykrywania opartych na regułach oparte na zaawansowanych zapytaniach myśliwnych
- Akcje odpowiedzi automatycznych

## <a name="see-also"></a>Zobacz też
- [Tworzenie reguł wykrywania niestandardowego i zarządzanie nimi](custom-detection-rules.md)
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Migrowanie zaawansowanych zapytań myśliwnych z programu Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md)
