---
title: Obsługa błędów podczas zaawansowanego wyszukiwania Microsoft 365 Defender
description: Opis błędów wyświetlanych podczas używania zaawansowanego wyszukiwania
keywords: zaawansowane szukanie, schłoń pod niebędący zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, schemat, kusto, limit czasu, zasoby, błędy, nieznany błąd, limity, przydział, parametr, alokacja
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
ms.openlocfilehash: 8bd7d4b5191ff88fe2bd958c87e930b91f64dd5e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989733"
---
# <a name="handle-advanced-hunting-errors"></a>Obsługa zaawansowanych błędów łęgowania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender


Zaawansowane wyszukiwanie wyświetla błędy powiadamiania o błędach składni i o każdym przypadku, gdy zapytania mają ustawione [wstępnie zdefiniowane przydziały i parametry użycia](advanced-hunting-limits.md). Skorzystaj z poniższej tabeli, aby uzyskać porady dotyczące sposobu rozwiązywania problemów i unikania ich.

| Typ błędu | Przyczyna | Rozwiązanie | Przykłady komunikatów o błędach |
|--|--|--|--|
| Błędy składni | Zapytanie zawiera nierozpoznane nazwy, w tym odwołania do brakowych operatorów, kolumn, funkcji lub tabel. | Upewnij się, że odwołania [do operatorów i funkcji Kusto](/azure/data-explorer/kusto/query/) są poprawne. Sprawdź [schemat, aby](advanced-hunting-schema-tables.md) sprawdzić, czy są odpowiednie zaawansowane kolumny, funkcje i tabele wyszukiwania zaawansowanego. Ciągi zmiennych są ujęte w cudzysłowy, aby były rozpoznawane. Podczas pisania zapytań użyj sugestii autouzupełniania z funkcji IntelliSense. | `A recognition error occurred.` |
| Błędy semantyczne | Podczas gdy zapytanie używa prawidłowego operatora, kolumny, funkcji lub nazw tabel, występują błędy w jego strukturze i logiki wynikowej. W niektórych przypadkach zaawansowane szukanie wskazuje określonego operatora, który spowodował błąd. | Sprawdź, czy nie występują błędy w strukturze zapytania. Aby uzyskać [wskazówki, zapoznaj się z dokumentacją firmy Kusto](/azure/data-explorer/kusto/query/) . Podczas pisania zapytań użyj sugestii autouzupełniania z funkcji IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Limity czasu | Kwerenda może zostać uruchamiana tylko w ograniczonym [okresie przed limitem czasu](advanced-hunting-limits.md). Ten błąd może wystąpić częściej podczas uruchamiania złożonych zapytań. | [Optymalizowanie zapytania](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| Ograniczanie procesora | Zapytania w tej samej dzierżawie przekroczyły zasoby [PROCESORA](advanced-hunting-limits.md) , które zostały przydzielone na podstawie rozmiaru dzierżawy. | Usługa sprawdza użycie zasobów procesora co 15 minut i codziennie oraz wyświetla ostrzeżenia po przekroczeniu 10% przydzielonego przydziału. Jeśli poziom użycia wynosi 100%, usługa blokuje zapytania do momentu kolejnego dziennego lub 15-minutowego cyklu. [Optymalizowanie zapytań w celu uniknięcia osiągnięcia przydziałów procesora](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Przekroczono limit rozmiaru wyników  | Maksymalny rozmiar został przekroczony w zagregowanym rozmiarze zestawu wyników zapytania. Ten błąd może wystąpić, jeśli zestaw wyników jest tak duży, że przycinanie w granicach limitu 10 000 rekordów nie może zmniejszyć go do dopuszczalnego rozmiaru. Ten błąd najprawdopodobniej wpłynie na wyniki, które zawierają wiele kolumn z rozmiarem zawartości. | [Optymalizowanie zapytania](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Nadmiarowe zużycie zasobów | Zapytanie zużyło nadmiarowe ilości zasobów i jego ukończenie zostało zatrzymane. W niektórych przypadkach zaawansowane szukanie wskazuje określony operator, który nie został zoptymalizowany. | [Optymalizowanie zapytania](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Nieznane błędy | Zapytanie nie powiodło się z powodu nieznanego powodu. | Spróbuj ponownie uruchomić zapytanie. Jeśli zapytania nadal zwracają nieznane błędy, skontaktuj się z firmą Microsoft za pośrednictwem portalu. | `An unexpected error occurred during query execution. Please try again in a few minutes.`



## <a name="related-topics"></a>Tematy pokrewne
- [Zaawansowane wskazówki dotyczące wyszukiwania](advanced-hunting-best-practices.md)
- [Przydziały i parametry użycia](advanced-hunting-limits.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Omówienie języka zapytań Kusto](/azure/data-explorer/kusto/query/)