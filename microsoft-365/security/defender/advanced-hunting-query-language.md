---
title: Poznaj zaawansowany język zapytań myśliwski w programie Microsoft 365 Defender
description: Utwórz pierwsze zapytanie dotyczące wyszukiwania zagrożeń i poznaj popularne operatory oraz inne aspekty zaawansowanego języka zapytań myśliwnych.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, język, nauka, pierwsze zapytanie, telemetria, zdarzenia, telemetria, niestandardowe wykrywanie, schemat, kusto, operatory, typy danych, pobieranie programu PowerShell, przykład kwerendy
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
ms.openlocfilehash: 7092b4ed30400fb559751d4d939801c1982407f8
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010671"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Poznaj zaawansowany język zapytań myśliwski

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Zaawansowane wyszukiwania są oparte na [języku zapytań Kusto](/azure/kusto/query/). Za pomocą operatorów i instrukcji Kusto można konstruować zapytania, które lokalizują informacje w wyspecjalizowanym [schemacie](advanced-hunting-schema-tables.md). 

Obejrzyj ten krótki klip wideo, aby poznać kilka przydatnych podstawowych informacji o języku zapytań Kusto.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Aby lepiej zrozumieć te pojęcia, uruchom pierwsze zapytanie.

## <a name="try-your-first-query"></a>Wypróbuj swoje pierwsze zapytanie

W portalu Microsoft 365 Defender przejdź do tematu **Wyszukiwania**, aby uruchomić pierwsze zapytanie. Użyj następującego przykładu: 

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

**[Uruchom to zapytanie podczas zaawansowanego wyszukiwania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Opis kwerendy i określanie tabel do przeszukania
Na początku zapytania został dodany krótki komentarz opisujący, do czego ono jest służące. Ten komentarz jest pomocny, jeśli później zdecydujesz się zapisać zapytanie i udostępnić je innym osobom w organizacji. 

```kusto
// Finds PowerShell execution events that could involve a download
```

Samo zapytanie zwykle zaczyna się od nazwy tabeli, po której następuje kilka elementów, które rozpoczynają się od potoku (`|`). W tym przykładzie zaczynamy od  `DeviceProcessEvents` `DeviceNetworkEvents`utworzenia unii dwóch tabel i dodawania elementów potokowych zgodnie z potrzebami.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>Ustawianie zakresu czasu
Pierwszym elementem potokowym jest filtr czasu ograniczony do ostatnich siedmiu dni. Ograniczenie zakresu czasu pomaga zagwarantować, że zapytania będą działać dobrze, będą zwracać wyniki, które można zarządzać, i nie przekrocz limitu czasu.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Sprawdzanie określonych procesów
Po zakresie czasu następuje wyszukiwanie nazw plików procesów reprezentujących aplikację PowerShell.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Wyszukiwanie określonych ciągów poleceń
Później zapytanie wyszukuje ciągi w wierszach poleceń, które są zwykle używane do pobierania plików za pomocą programu PowerShell.

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

### <a name="customize-result-columns-and-length"></a>Dostosowywanie kolumn i długości wyników 
Teraz, gdy zapytanie wyraźnie identyfikuje dane, które chcesz znaleźć, możesz zdefiniować wygląd wyników. `project` zwraca określone kolumny i `top` ogranicza liczbę wyników. Operatory te zapewniają, że wyniki są odpowiednio sformatowane, mają dość duży i łatwy w przetwarzaniu.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Wybierz **pozycję Uruchom zapytanie,** aby wyświetlić wyniki.

>[!TIP]
>Możesz wyświetlać wyniki zapytania jako wykresy i szybko dostosowywać filtry. Aby uzyskać wskazówki, [przeczytaj o pracy z wynikami zapytania.](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators"></a>Informacje o typowych operatorach zapytań

Właśnie zostało uruchomione pierwsze zapytanie i masz ogólny pomysł na jego składniki. Czas nieco wywrócić do śledzenia i poznać podstawowe informacje. Język zapytań Kusto używany podczas wyszukiwania zaawansowanego obsługuje szereg operatorów, w tym następujące typowe operatory.

| Operator | Opis i użycie |
|--|--|
| `where` | Umożliwia filtrowanie tabeli podzestawu wierszy spełniających predykat. |
| `summarize` | Tworzenie tabeli, która agreguje zawartość tabeli wejściowej. |
| `join` | Scal wiersze dwóch tabel, aby tworzyć nową tabelę, dopasowując wartości z określonych kolumn z każdej tabeli. |
| `count` | Zwraca liczbę rekordów w zestawie rekordów wejściowych. |
| `top` | Zwraca pierwsze N rekordów posortowane według określonych kolumn. |
| `limit` | Zwraca aż do określonej liczby wierszy. |
| `project` | Zaznacz kolumny, które chcesz uwzględnić, zmień nazwę lub upuść i wstaw nowe kolumny obliczeniowe. |
| `extend` | Utwórz kolumny obliczeniowe i dołącz je do zestawu wyników. |
| `makeset` |  Zwraca tablicę dynamiczną (JSON) zestawu różnych wartości, które Wyr. przyjmuje w grupie. |
| `find` | Znajdowanie wierszy o predykatach w zestawie tabel. |

Aby zobaczyć przykład na żywo tych operatorów, uruchom je z sekcji **Wprowadzenie** w chłonie zaawansowanej pracy.

## <a name="understand-data-types"></a>Opis typów danych

Zaawansowane wyszukiwania obsługują typy danych Kusto, między innymi następujące typy:

| Typ danych | Opis i opis opisów zapytań |
|--|--|
| `datetime` | Dane i informacje o czasie zwykle reprezentują sygnatury czasowe wydarzeń. [Zobacz obsługiwane formaty daty/godziny](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | Ciąg znaków ujęty w cudzysłów pojedynczy () lub podwójny (`'`) ujęty w cudzysłów (`"`UTF-8). [Przeczytaj więcej o ciągach](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Ten typ danych obsługuje `true` lub stany `false` . [Zobacz obsługiwane literały i operatory](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32-bitowa liczba całkowita  |
| `long` | 64-bitowa liczba całkowita |

Aby dowiedzieć się więcej o tych typach danych, [przeczytaj o skalarnych typach danych Kusto](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Uzyskiwanie pomocy podczas pisania zapytań
Skorzystaj z następujących funkcji, aby szybciej pisać zapytania:
- **Autosuggest** — podczas pisania zapytań zaawansowane wyszukiwanie zapewnia sugestie z listy IntelliSense. 
- **Drzewo schematu** — reprezentacja schematu, która zawiera listę tabel i ich kolumn, jest wyświetlane obok obszaru roboczego. Aby uzyskać więcej informacji, umieść wskaźnik myszy na pozycji. Kliknij dwukrotnie element, aby wstawić go do edytora zapytań.
- **[Odwołanie do schematu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** — odwołanie w portalu z opisami tabel i kolumn, a także obsługiwane typy zdarzeń (`ActionType` wartości) i przykładowe zapytania

## <a name="work-with-multiple-queries-in-the-editor"></a>Praca z wieloma zapytaniami w edytorze
Za pomocą edytora zapytań można eksperymentować z wieloma zapytaniami. Aby użyć wielu zapytań:

- Poszczególne zapytania należy oddzielić pustym wierszem.
- Umieść kursor w dowolnej części zapytania, aby zaznaczyć to zapytanie przed jego uruchomieniem. Spowoduje to uruchomienie tylko wybranego zapytania. Aby uruchomić kolejne zapytanie, przenieś odpowiednio kursor i wybierz pozycję **Uruchom zapytanie**.

:::image type="content" source="../../media/learn-work-with-multiple.png" alt-text="Przykład wykonywania wielu zapytań na stronie **Nowe zapytanie** w portalu Microsoft 365 Defender zapytania" lightbox="../../media/learn-work-with-multiple.png":::

## <a name="use-sample-queries"></a>Używanie przykładowych zapytań

Sekcja **Wprowadzenie zawiera** kilka prostych zapytań, w których są używane często używane operatory. Spróbuj uruchomić te zapytania i z niewielkimi zmianami je w nich edytować.

:::image type="content" source="../../media/get-started-section.png" alt-text="Sekcja **Wprowadzenie** na stronie **Zaawansowane szukanie** w portalu Microsoft 365 Defender zaawansowane" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Oprócz podstawowych przykładów zapytań można również uzyskać dostęp do [](advanced-hunting-shared-queries.md) zapytań udostępnionych w przypadku określonych scenariuszy wyszukiwania zagrożeń. Przejrzyj zapytania udostępnione w lewej części strony lub [repozytorium GitHub zapytań](https://aka.ms/hunting-queries).

## <a name="access-query-language-documentation"></a>Dokumentacja języka zapytań programu Access

Aby uzyskać więcej informacji na temat języka zapytań Kusto i obsługiwanych operatorów, zobacz dokumentację języka zapytań [Kusto](/azure/kusto/query/).

>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Praca z wynikami zapytania](advanced-hunting-query-results.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)