---
title: Funkcja SeenBy() w zaawansowanym wyszukiwaniu Microsoft 365 Defender
description: Dowiedz się, jak za pomocą funkcji SeenBy() wyszukać, które dołączone urządzenia odnalazły określone urządzenie
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, dokumentacja schematu, kusto, SeenBy, odnajdywanie urządzeń, funkcja, wzbogacanie
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 4a17efeeaf62ddcf63988f055ca93b536e68c962
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65175013"
---
# <a name="seenby"></a>SeenBy()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Funkcja `SeenBy()` jest wywoływana w celu wyświetlenia listy dołączonych urządzeń, które widziały określone urządzenie za pomocą funkcji odnajdywania urządzeń.

Ta funkcja zwraca tabelę zawierającą następującą kolumnę:

| Kolumna | Typ danych | Opis |
|------------|---------------|-------------|
| `DeviceId` | `string` | Unikatowy identyfikator urządzenia w usłudze |


## <a name="syntax"></a>Składni

```kusto
invoke SeenBy(x)
```

- gdzie **x** jest identyfikatorem urządzenia, którego dotyczy

>[!TIP]
> Funkcje wzbogacania będą wyświetlać dodatkowe informacje tylko wtedy, gdy są dostępne. Dostępność informacji jest zróżnicowana i zależy od wielu czynników. Pamiętaj, aby wziąć to pod uwagę podczas korzystania z funkcji SeenBy() w zapytaniach lub podczas tworzenia wykrywania niestandardowego. Aby uzyskać najlepsze wyniki, zalecamy użycie funkcji SeenBy() z tabelą DeviceInfo.

### <a name="example-obtain-list-of-onboarded-devices-that-have-seen-a-device"></a>Przykład: uzyskiwanie listy dołączonych urządzeń, które widziały urządzenie

```kusto
DeviceInfo 
| where OnboardingStatus <> "Onboarded" 
| limit 100 | invoke SeenBy()
```

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Uzyskiwanie większej liczby przykładów zapytań](advanced-hunting-shared-queries.md)
