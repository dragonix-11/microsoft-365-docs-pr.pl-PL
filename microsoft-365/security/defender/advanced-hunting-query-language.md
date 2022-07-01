---
title: Poznaj zaawansowany język zapytań wyszukiwania zagrożeń w Microsoft 365 Defender
description: Tworzenie pierwszego zapytania dotyczącego wyszukiwania zagrożeń i poznawanie typowych operatorów i innych aspektów zaawansowanego języka zapytań wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń Microsoft 365 Defender, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie, nauka, pierwsze zapytanie, telemetria, zdarzenia, telemetria, wykrywanie niestandardowe, schemat, kusto, operatory, typy danych, pobieranie programu PowerShell, przykład zapytania
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 8c650e639d1a4629ed25bcc3a7f3a8c28df4b8e8
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603489"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Poznaj zaawansowany język zapytań wyszukiwania zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**

- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Zaawansowane wyszukiwanie zagrożeń jest oparte na [języku zapytań Kusto](/azure/kusto/query/). Operatory i instrukcje Kusto umożliwiają tworzenie zapytań, które lokalizują informacje w wyspecjalizowanym [schemacie](advanced-hunting-schema-tables.md). 

Obejrzyj ten krótki film wideo, aby poznać przydatne podstawy języka zapytań Kusto.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Aby lepiej zrozumieć te pojęcia, uruchom pierwsze zapytanie.

## <a name="try-your-first-query"></a>Wypróbuj pierwsze zapytanie

W portalu Microsoft 365 Defender przejdź do pozycji **Wyszukiwanie zagrożeń**, aby uruchomić pierwsze zapytanie. Skorzystaj z następującego przykładu: 

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

**[Uruchamianie tego zapytania w zaawansowanym wyszukiwaniu](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Opisz zapytanie i określ tabele do wyszukania

Na początku zapytania dodano krótki komentarz, aby opisać, do czego służy. Ten komentarz pomaga, jeśli później zdecydujesz się zapisać zapytanie i udostępnić je innym osobom w organizacji. 

```kusto
// Finds PowerShell execution events that could involve a download
```

Samo zapytanie zwykle rozpoczyna się od nazwy tabeli, po której następuje kilka elementów rozpoczynających się potokiem (`|`). W tym przykładzie zaczniemy od utworzenia unii dwóch tabel  `DeviceProcessEvents` i `DeviceNetworkEvents`, i w razie potrzeby dodamy elementy potokowe.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```

### <a name="set-the-time-range"></a>Ustawianie zakresu czasu

Pierwszy element potokowy to filtr czasu o zakresie do poprzednich siedmiu dni. Ograniczenie zakresu czasu pomaga zapewnić, że zapytania działają dobrze, zwracają możliwe do zarządzania wyniki i nie przekraczają limitu czasu.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Sprawdzanie określonych procesów

Po zakresie czasu natychmiast następuje wyszukiwanie nazw plików procesów reprezentujących aplikację programu PowerShell.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Wyszukiwanie określonych ciągów poleceń

Następnie zapytanie szuka ciągów w wierszach polecenia, które są zwykle używane do pobierania plików przy użyciu programu PowerShell.

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>Dostosowywanie kolumn wyników i długości 

Teraz, gdy zapytanie jasno identyfikuje dane, które chcesz zlokalizować, możesz zdefiniować, jak wyglądają wyniki. `project` zwraca określone kolumny i `top` ogranicza liczbę wyników. Te operatory pomagają zapewnić, że wyniki są dobrze sformatowane i dość duże i łatwe do przetworzenia.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Wybierz pozycję **Uruchom zapytanie** , aby wyświetlić wyniki.

>[!TIP]
>Możesz wyświetlać wyniki zapytań jako wykresy i szybko dostosowywać filtry. Aby uzyskać wskazówki, [przeczytaj o pracy z wynikami zapytania](advanced-hunting-query-results.md)



## <a name="learn-common-query-operators"></a>Poznaj typowe operatory zapytań

Właśnie uruchomiono pierwsze zapytanie i masz ogólne pojęcie o jego składnikach. Nadszedł czas, aby nieco wycofać się i poznać pewne podstawy. Język zapytań Kusto używany przez zaawansowane wyszukiwanie zagrożeń obsługuje szereg operatorów, w tym następujące typowe.

| Operator | Opis i użycie |
|--|--|
| `where` | Przefiltruj tabelę do podzestawu wierszy, które spełniają predykat. |
| `summarize` | Utwórz tabelę, która agreguje zawartość tabeli wejściowej. |
| `join` | Scal wiersze dwóch tabel, tworząc nową tabelę, dopasowując wartości określonych kolumn z każdej tabeli. Obejrzyj [artykuł Łączenie tabel w języku KQL](https://www.youtube.com/watch?v=8qZx7Pp5XgM) , aby dowiedzieć się, jak to zrobić.|
| `count` | Zwraca liczbę rekordów w zestawie rekordów wejściowych. |
| `top` | Zwróć pierwsze rekordy N posortowane według określonych kolumn. |
| `limit` | Wróć do określonej liczby wierszy. |
| `project` | Wybierz kolumny do uwzględnienia, zmień nazwę lub upuść, a następnie wstaw nowe kolumny obliczone. |
| `extend` | Utwórz kolumny obliczeniowe i dołącz je do zestawu wyników. |
| `makeset` |  Zwraca tablicę dynamiczną (JSON) zestawu unikatowych wartości, które wyrażenie przyjmuje w grupie. |
| `find` | Znajdź wiersze pasujące do predykatu w zestawie tabel. |

Aby wyświetlić dynamiczny przykład tych operatorów, uruchom je w sekcji **Wprowadzenie** w zaawansowanym polowaniu.

## <a name="understand-data-types"></a>Omówienie typów danych

Zaawansowane wyszukiwanie zagrożeń obsługuje typy danych Kusto, w tym następujące typowe typy:

| Typ danych | Implikacje dotyczące opisu i zapytania |
|--|--|
| `datetime` | Dane i informacje o czasie zwykle reprezentują znaczniki czasu zdarzenia. [Zobacz obsługiwane formaty daty/godziny](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | Ciąg znaków w formacie UTF-8 ujęty w cudzysłowy pojedyncze (`'`) lub cudzysłów (`"`). [Przeczytaj więcej o ciągach](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Ten typ danych obsługuje `true` lub `false` stany. [Zobacz obsługiwane literały i operatory](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32-bitowa liczba całkowita  |
| `long` | 64-bitowa liczba całkowita |

Aby dowiedzieć się więcej o tych typach danych, [przeczytaj o typach danych skalarnych Kusto](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Uzyskiwanie pomocy podczas pisania zapytań

Skorzystaj z następujących funkcji, aby szybciej pisać zapytania:
- **Automatyczne sugerowanie** — podczas pisania zapytań zaawansowane wyszukiwanie zagrożeń zapewnia sugestie z funkcji IntelliSense. 
- **Drzewo schematów** — obok obszaru roboczego znajduje się reprezentacja schematu zawierająca listę tabel i ich kolumn. Aby uzyskać więcej informacji, umieść kursor nad elementem. Kliknij dwukrotnie element, aby wstawić go do edytora zapytań.
- **[Dokumentacja schematu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** — dokumentacja w portalu z opisami tabel i kolumn, a także obsługiwanymi typami zdarzeń (`ActionType` wartościami) i przykładowymi zapytaniami

## <a name="work-with-multiple-queries-in-the-editor"></a>Praca z wieloma zapytaniami w edytorze

Edytor zapytań umożliwia eksperymentowanie z wieloma zapytaniami. Aby użyć wielu zapytań:

- Rozdziel każde zapytanie pustym wierszem.
- Umieść kursor na dowolnej części zapytania, aby wybrać to zapytanie przed jego uruchomieniem. Spowoduje to uruchomienie tylko wybranego zapytania. Aby uruchomić inne zapytanie, przesuń kursor odpowiednio i wybierz pozycję **Uruchom zapytanie**.

:::image type="content" source="../../media/multiple-queries.png" alt-text="Przykład wykonania wielu zapytań na stronie **Nowe zapytanie** w portalu Microsoft 365 Defender" lightbox="../../media/multiple-queries.png":::

Aby uzyskać bardziej wydajny obszar roboczy, możesz również użyć wielu kart na tej samej stronie wyszukiwania zagrożeń. Wybierz pozycję **Nowe zapytanie** , aby otworzyć kartę dla nowego zapytania.

:::image type="content" source="../../media/multitab.png" alt-text="Otwieranie nowej karty przez wybranie pozycji Utwórz nową w zaawansowanym polowaniu w portalu Microsoft 365 Defender" lightbox="../../media/multitab.png":::

Następnie można uruchamiać różne zapytania bez otwierania nowej karty przeglądarki. 

:::image type="content" source="../../media/multitab-examples.png" alt-text="Uruchamianie różnych zapytań bez opuszczania zaawansowanej strony wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="../../media/multitab-examples.png":::

>[!NOTE] 
> Użycie wielu kart przeglądarki z zaawansowanym wyszukiwaniem zagrożeń może spowodować utratę niezapisanych zapytań. Aby temu zapobiec, użyj funkcji tabulacji w ramach zaawansowanego wyszukiwania zagrożeń zamiast oddzielnych kart przeglądarki.

## <a name="use-sample-queries"></a>Używanie przykładowych zapytań

Sekcja **Wprowadzenie** zawiera kilka prostych zapytań przy użyciu powszechnie używanych operatorów. Spróbuj uruchomić te zapytania i wprowadzania w nich niewielkich modyfikacji.

:::image type="content" source="../../media/get-started-section.png" alt-text="Sekcja **Wprowadzenie** na stronie **Zaawansowane wyszukiwanie zagrożeń** w portalu Microsoft 365 Defender" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Oprócz podstawowych przykładów zapytań można również uzyskać dostęp do [udostępnionych zapytań](advanced-hunting-shared-queries.md) dla konkretnych scenariuszy wyszukiwania zagrożeń. Zapoznaj się z udostępnionymi zapytaniami po lewej stronie lub [repozytorium zapytań usługi GitHub](https://aka.ms/hunting-queries).

## <a name="access-query-language-documentation"></a>Dokumentacja języka zapytań dostępu

Aby uzyskać więcej informacji na temat języka zapytań Kusto i obsługiwanych operatorów, zobacz [dokumentację języka zapytań Kusto](/azure/kusto/query/).

>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender. [Włącz Microsoft 365 Defender](m365d-enable.md), aby wyszukiwać zagrożenia przy użyciu większej liczby źródeł danych. Zaawansowane przepływy pracy wyszukiwania zagrożeń można przenieść z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender, wykonując kroki opisane w [temacie Migrowanie zaawansowanych zapytań wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)