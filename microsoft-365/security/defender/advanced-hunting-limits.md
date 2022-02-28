---
title: Zaawansowane informacje o przydziałach wyszukiwania i parametrach użycia w programie Microsoft 365 Defender
description: Opis różnych przydziałów i parametrów użycia (limitów usług), które chronią zaawansowaną służbę chłonianą
keywords: zaawansowane szukanie, schłoń pod niebędący zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, schemat, kusto, limit procesora, limit zapytań, zasoby, maksymalne wyniki, przydział, parametry, alokacja
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
ms.openlocfilehash: fe0ad42ac0ebfc7f6816e412ab6ffb0ac9291b44
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989107"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Zaawansowane informacje o przydziałach wyszukiwania i parametrach użycia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

W celu utrzymania szybkości i szybkości usługi zaawansowane ustawienia terminów wyszukiwania są różnego rodzaju przydziałów i parametrów użycia (nazywanych również "limitami usług"). Te przydziały i parametry mają zastosowanie osobno do kwerend uruchamianych ręcznie, a zapytania są uruchamiane przy użyciu niestandardowych [reguł wykrywania](custom-detection-rules.md). Klienci, którzy regularnie uruchamiają wiele zapytań, powinni pamiętać o tych limitach i stosować najlepsze rozwiązania optymalizacji [,](advanced-hunting-best-practices.md) aby zminimalizować zakłócenia w pracy.

Skorzystaj z poniższej tabeli, aby poznać istniejące przydziały i parametry użycia.

| Przydział lub parametr | Rozmiar | Cykl odświeżania | Opis |
|--|--|--|--|
| Zakres danych | 30 dni | Każde zapytanie | Każde zapytanie może szukać danych z ostatnich 30 dni. |
| Zestaw wyników | 10 000 wierszy | Każde zapytanie | Każde zapytanie może zwrócić do 10 000 rekordów. |
| Limit czasu | 10 minut | Każde zapytanie | Każde zapytanie można uruchomić przez maksymalnie 10 minut. Jeśli nie zostanie ono ukończone w ciągu 10 minut, usługa wyświetli komunikat o błędzie.
| Zasoby procesora | W zależności od rozmiaru dzierżawy | Co 15 minut | W [portalu jest wyświetlany błąd](advanced-hunting-errors.md) przy każdym uruchamianiu zapytania, a dzierżawa zużyła ponad 10% przydzielonych zasobów. Zapytania są blokowane, jeśli dzierżawa osiągnęła 100% do czasu kolejnego 15-minutowego cyklu. |

>[!NOTE] 
>Oddzielny zestaw przydziałów i parametrów dotyczy zaawansowanych zapytań wyszukiwania wykonywanych za pomocą interfejsu API. [Przeczytaj o zaawansowanych interfejsach API wyszukiwania](./api-advanced-hunting.md)

## <a name="related-topics"></a>Tematy pokrewne

- [Zaawansowane wskazówki dotyczące wyszukiwania](advanced-hunting-best-practices.md)
- [Obsługa zaawansowanych błędów łęgowania](advanced-hunting-errors.md)
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)