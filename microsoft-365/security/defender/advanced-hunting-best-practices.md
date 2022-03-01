---
title: Zaawansowane wskazówki dotyczące wyszukiwania w programie Microsoft 365 Defender
description: Dowiedz się, jak szybko konstruować, wydajnie i bezbłędnie wyglądające na zagrożenia zapytania z zaawansowanymi wyszukiwaniami
keywords: zaawansowane wyszukiwania, chłonianie pod kątem zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, schemat, kusto, unikanie limitów czasu, wierszy poleceń, id procesu, optymalizowanie, najlepsze rozwiązanie, analizowanie, dołączanie, podsumowuje
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
ms.openlocfilehash: d797fb8843bdf5d29e9af43cac152461eb379e5f
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996834"
---
# <a name="advanced-hunting-query-best-practices"></a>Zaawansowane wskazówki dotyczące wyszukiwania podczas wyszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Zastosować te zalecenia, aby szybciej uzyskać wyniki i uniknąć limitów czasu podczas uruchamiania złożonych zapytań. Aby uzyskać więcej wskazówek na temat poprawy wydajności zapytań, zobacz [Najlepsze rozwiązania dotyczące zapytań Kusto](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>Opis przydziałów zasobów procesora
W zależności od jego rozmiaru każda dzierżawa ma dostęp do poszczególnych zasobów PROCESORA przydzielonych do uruchamiania zaawansowanych zapytań łowiecki. Aby uzyskać szczegółowe informacje na temat różnych parametrów użycia, [przeczytaj o zaawansowanych przydziałach pracy i parametrach użycia](advanced-hunting-limits.md).

Po uruchomieniu zapytania można sprawdzić czas wykonywania i użycie zasobów (niskie, średnie, wysokie). Wysoka oznacza, że zapytanie zajęło więcej zasobów do uruchomienia i można je ulepszyć, aby wydajniej zwracać wyniki.

:::image type="content" source="../../media/resource-usage.png" alt-text="Szczegóły zapytania na karcie **Results** w portalu Microsoft 365 Defender projektu" lightbox="../../media/resource-usage.png":::

Klienci, którzy regularnie uruchamiają wiele zapytań, powinni śledzić użycie i stosować wskazówki dotyczące optymalizacji w tym artykule, aby zminimalizować zakłócenia wynikające z przekroczenia przydziałów lub parametrów użycia.

## <a name="general-optimization-tips"></a>Ogólne porady dotyczące optymalizacji

- **Rozmiar nowych zapytań** — jeśli podejrzewasz, że zapytanie zwróci duży zestaw wyników, oceń je najpierw za pomocą [operatora liczenia](/azure/data-explorer/kusto/query/countoperator). Aby [uniknąć](/azure/data-explorer/kusto/query/limitoperator) dużych zestawów wyników, użyj `take` limitu lub jego synonimu.
- Wcześniejsze stosowanie filtrów — stosowanie filtrów czasu i innych filtrów w celu zmniejszenia zestawu danych, szczególnie przed użyciem funkcji przekształcania i analizowania, takich jak [podciąg()](/azure/data-explorer/kusto/query/substringfunction), [replace()](/azure/data-explorer/kusto/query/replacefunction), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction)lub [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). W poniższym przykładzie funkcja analizowania [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) jest używana po pomniejszeniu liczby rekordów przez operatory filtrowania.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Zawiera wyrazy beaty** — Aby uniknąć niepotrzebnie wyszukiwania podciągów w wyrazach, `has` użyj operatora zamiast `contains`. [Informacje o operatorach ciągu](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Wyszukiwanie w określonych kolumnach** — zamiast wyszukiwania pełnego tekstu we wszystkich kolumnach należy szukać w określonej kolumnie. Nie używaj do sprawdzania `*` wszystkich kolumn.
- **Szybkość wyszukiwania z określoną wielkością liter —** wyszukiwania z określoną wielkością liter są bardziej szczegółowe i na ogół bardziej performerują. Nazwy operatorów ciągu z wielkością [liter](/azure/data-explorer/kusto/query/datatypes-string-operators), takich jak `has_cs` i `contains_cs`, zwykle kończą się na `_cs`. Możesz również użyć operatora równania z wielkością liter, a nie `==` operatora `=~`.
- **Analizowanie nie** wyodrębniaj — jeśli to możliwe, użyj operatora analizy [](/azure/data-explorer/kusto/query/parseoperator) lub funkcji analizowania, [na przykład parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). Unikaj stosowania `matches regex` operatora ciągu lub [funkcji extract(),](/azure/data-explorer/kusto/query/extractfunction) przy czym w obu przypadkach jest to wyrażenie regularne. Użycie wyrażeń regularnych należy zarezerwować na bardziej złożone scenariusze. [Dowiedz się więcej o funkcjach analizowania](#parse-strings)
- **Filtrowanie tabel, a nie wyrażeń** — Nie filtruj według kolumny obliczeniowej, jeśli możesz filtrować według kolumny tabeli.
- **Brak trzech znaków —** unikaj porównywania lub filtrowania przy użyciu terminów z nie więcej niż trzema znakami. Te terminy nie są indeksowane, a ich dopasowanie będzie wymagało większej liczby zasobów.
- **Project selektywnie** — ułapnisz zrozumienie wyników, prognozując tylko potrzebne kolumny. Prognozowanie określonych kolumn przed uruchomieniem [sprzężenia](/azure/data-explorer/kusto/query/joinoperator) lub podobnych operacji również zwiększa wydajność.

## <a name="optimize-the-join-operator"></a>Optymalizowanie `join` operatora
Operator [sprzężenia scala](/azure/data-explorer/kusto/query/joinoperator) wiersze z dwóch tabel, dopasowując wartości w określonych kolumnach. Skorzystaj z tych porad, aby zoptymalizować zapytania, które używają tego operatora.

- **Mniejsza tabela po lewej** stronie — `join` operator dopasowuje rekordy w tabeli po lewej stronie instrukcji sprzężenia do rekordów po prawej stronie. Dzięki mniejszej tabeli po lewej stronie konieczne będzie dopasowanie mniejszej liczby rekordów, co przyspieszy zapytanie.

    W poniższej tabeli ograniczymy `DeviceLogonEvents` `IdentityLogonEvents` tabelę po lewej stronie, aby uwzględnić tylko trzy określone urządzenia przed dołączeniem ich za pomocą identyfikatorów SID kont.

    ```kusto
    DeviceLogonEvents
    | where DeviceName in ("device-1.domain.com", "device-2.domain.com", "device-3.domain.com")
    | where ActionType == "LogonFailed"
    | join
        (IdentityLogonEvents
        | where ActionType == "LogonFailed"
        | where Protocol == "Kerberos")
    on AccountSid
    ```

- **Użyj wewnętrznej** odmiany sprzężenia — domyślna odmiana sprzężenia lub [innerunique-join](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) deduplicates rows in the left table by the join key before returning a row for each match to the right table.[](/azure/data-explorer/kusto/query/joinoperator#join-flavors) Jeśli lewa tabela zawiera `join` wiele wierszy z taką samą wartością klucza, te wiersze zostaną deduplikowane w celu pozostawienia jednego losowego wiersza dla każdej unikatowej wartości.

    To zachowanie domyślne może pozostawić ważne informacje z lewej tabeli, które mogą dostarczyć przydatnych informacji. Na przykład poniższe zapytanie spowoduje wyświetlanie tylko jednej wiadomości e-mail zawierającej określony załącznik, nawet jeśli ten sam załącznik został wysłany przy użyciu wielu wiadomości e-mail:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    Aby rozwiązać to ograniczenie, zastosujemy odmianę [sprzężenia](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) `kind=inner` wewnętrznego, określając pokazywanie wszystkich wierszy w tabeli po lewej stronie z pasującymi wartościami po prawej stronie:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Dołączanie rekordów z okna czasowego** — podczas badania zdarzeń zabezpieczeń analitycy szukają powiązanych zdarzeń, które występują w tym samym czasie. Stosowanie tego samego podejścia w przypadku używania również `join` korzyści z wydajności przez zmniejszenie liczby rekordów do sprawdzenia.

    Poniższe zapytanie sprawdza zdarzenia logowania w ciągu 30 minut od odebrania złośliwego pliku:

    ```kusto
    EmailEvents
    | where Timestamp > ago(7d)
    | where ThreatTypes has "Malware"
    | project EmailReceivedTime = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0])
    | join (
    DeviceLogonEvents
    | where Timestamp > ago(7d)
    | project LogonTime = Timestamp, AccountName, DeviceName
    ) on AccountName
    | where (LogonTime - EmailReceivedTime) between (0min .. 30min)
    ```
- **Stosowanie filtrów czasu** po obu stronach — Nawet jeśli nie badasz określonego czasu, `join` zastosowanie filtrów czasu zarówno do lewej, jak i prawej tabeli może zmniejszyć liczbę rekordów w celu sprawdzenia i zwiększenia wydajności. Poniższe zapytanie dotyczy obu `Timestamp > ago(1h)` tabel i łączy tylko rekordy z poprzedniej godziny:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Używaj wskazówek dotyczących wydajności** — skorzystaj `join` ze wskazówek operatora, aby poinstruować zaplecza, aby rozpowszechniała obciążenie podczas wykonywania operacji wymagających dużej ilości zasobów. [Dowiedz się więcej o wskazówkach dotyczących dołączania do programu](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Na przykład wskazówka **[na temat](/azure/data-explorer/kusto/query/shufflequery)** losowej kolejności pomaga zwiększyć wydajność zapytania podczas łączenia tabel przy użyciu klucza o wysokiej kardynalności — klucza z wieloma unikatowymi wartościami, `AccountObjectId` na przykład w poniższym zapytaniu:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    Wskazówka **[dotyczące emisji pomaga](/azure/data-explorer/kusto/query/broadcastjoin)** , gdy tabela po lewej stronie jest niewielka (do 100 000 rekordów), a właściwa tabela jest bardzo duża. Na przykład poniższe zapytanie próbuje dołączyć do kilku wiadomości e-mail z określonymi tematami  ze wszystkimi wiadomościami zawierającymi linki w `EmailUrlInfo` tabeli:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>Optymalizowanie `summarize` operatora
Operator [podsumowania](/azure/data-explorer/kusto/query/summarizeoperator) agreguje zawartość tabeli. Skorzystaj z tych porad, aby zoptymalizować zapytania, które używają tego operatora.

- **Znajdowanie różnych wartości —** na ogół używaj `summarize` , aby znaleźć odrębne wartości, które mogą być powtarzające się. Nie trzeba go używać do agregowania kolumn, które nie mają powtarzających się wartości.

    Mimo że pojedyncza wiadomość e-mail może być częścią wielu zdarzeń,  `summarize` poniższy przykład nie jest skutecznym zastosowaniem, ponieważ identyfikator wiadomości sieciowej dla pojedynczej wiadomości e-mail zawsze ma unikatowy adres nadawcy.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    Operator `summarize` można łatwo zastąpić operatorem `project`, co daje potencjalnie takie same wyniki, gdy zużywa mniej zasobów:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    Poniższy przykład jest bardziej efektywnym `summarize` zastosowaniem, ponieważ istnieje wiele różnych wystąpień adresu nadawcy wysyłającego wiadomość e-mail na ten sam adres adresata. Takie kombinacje są mniej oddzielne i mogą mieć duplikaty.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Losowa kolejność**`summarize` zapytania — najlepiej jest używać jej w kolumnach z powtarzających się wartościami,  jednak te same kolumny mogą mieć również wysoką kardynalność lub dużą liczbę unikatowych wartości. Podobnie jak `join` operator, możesz również [](/azure/data-explorer/kusto/query/shufflequery) `summarize` zastosować wskazówkę losowo, aby rozłożyć obciążenie przetwarzania i potencjalnie zwiększyć wydajność podczas pracy na kolumnach o wysokiej kardynalności.

    Poniższe zapytanie używa do `summarize` zliczenia różnych adresów e-mail adresatów, które mogą być uruchamiane w setkach tysięcy w dużych organizacjach. W celu poprawienia wydajności zawiera on:`hint.shufflekey`

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

## <a name="query-scenarios"></a>Scenariusze kwerend

### <a name="identify-unique-processes-with-process-ids"></a>Identyfikowanie unikatowych procesów za pomocą identyfikatorów procesów

Identyfikatory procesów są odzyskiwane w Windows i używane ponownie dla nowych procesów. Samodzielnie nie mogą one służyć jako unikatowe identyfikatory dla określonych procesów.

Aby uzyskać identyfikator unikatowy dla procesu na określonym komputerze, wykorzystaj identyfikator procesu wraz z czasem utworzenia procesu. Podczas sprzężenia lub podsumowywanego danych wokół procesów uwzględnij kolumny identyfikatora komputera (`DeviceId``DeviceName`albo ), identyfikatora procesu (`ProcessId` lub `InitiatingProcessId`) i czasu utworzenia procesu (`ProcessCreationTime` lub `InitiatingProcessCreationTime`)

Poniższe przykładowe zapytanie umożliwia znalezienie procesów, które mają dostęp do ponad 10 adresów IP za pośrednictwem portu 445 (SMB), prawdopodobnie skanując w celu uzyskania udziałów plików.

Przykładowe zapytanie:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

Zapytanie podsumowuje dane według obu `InitiatingProcessId` `InitiatingProcessCreationTime` sposobów i tak, że przejmuje pojedynczy proces bez mieszania wielu procesów z tym samym identyfikatorem procesu.

### <a name="query-command-lines"></a>Wiersze poleceń zapytania
Istnieje wiele sposobów konstruowania wiersza polecenia w celu wykonania zadania. Na przykład atakujący może odwoływać się do pliku obrazu bez ścieżki, bez rozszerzenia pliku, przy użyciu zmiennych środowiskowych lub cudzysłowów. Atakujący może też zmienić kolejność parametrów lub dodać wiele cudzysłowów i spacji.

Aby utworzyć bardziej trwałe zapytania wokół wierszy poleceń, zastosuj następujące wskazówki:

- Zidentyfikuj znane ** procesy (takie jaknet.exelub *psexec.exe*), dopasowując pola nazwy pliku zamiast filtrowania w samym wierszu polecenia.
- Analizowanie sekcji wiersza polecenia przy użyciu [funkcji parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line)
- W przypadku wyszukiwania argumentów wiersza polecenia nie należy poszukać dokładnego dopasowania wielu niepowiązanych argumentów w określonej kolejności. Zamiast tego należy używać wyrażeń regularnych lub używać wielu osobnych operatorów.
- Użyj dopasowania bez uwzględniania liter. Na przykład użyj `=~`, `in~`, a `contains` zamiast `==`, `in`i `contains_cs`.
- Aby zminimalizować techniki zastępowania wiersza polecenia, rozważ usunięcie cudzysłowów, zamianę przecinków na spacje i zastąpienie wielu kolejnych spacji pojedynczymi odstępami. Istnieją bardziej złożone techniki zamiejscowe, które wymagają innych metod, ale te poprawki mogą pomóc w ich rozwiązaniach.

W poniższych przykładach podano różne sposoby konstruowania zapytania wyszuknet.exe ** w celu zatrzymania usługi zapory "MpsSvc":

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on file name, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc"

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc"
```

### <a name="ingest-data-from-external-sources"></a>Dane do zbierania danych z zewnętrznych źródeł
Aby uwzględnić długie listy lub duże tabele w zapytaniu, użyj [zewnętrznego operatora danych](/azure/data-explorer/kusto/query/externaldata-operator) w celu zbierania danych z określonego URI. Możesz pobrać dane z plików w formacie TXT, CSV, JSON [lub innym](/azure/data-explorer/ingestion-supported-formats). W poniższym przykładzie pokazano, jak użyć rozbudowanych list skrótów SHA-256 złośliwego oprogramowania dostarczonych przez firmę MalwareBazaar (abuse.ch) do sprawdzania załączników w wiadomościach e-mail:

```kusto
let abuse_sha256 = (externaldata(sha256_hash: string)
[@"https://bazaar.abuse.ch/export/txt/sha256/recent/"]
with (format="txt"))
| where sha256_hash !startswith "#"
| project sha256_hash;
abuse_sha256
| join (EmailAttachmentInfo
| where Timestamp > ago(1d)
) on $left.sha256_hash == $right.SHA256
| project Timestamp,SenderFromAddress,RecipientEmailAddress,FileName,FileType,
SHA256,ThreatTypes,DetectionMethods
```

### <a name="parse-strings"></a>Analizowanie ciągów
Istnieją różne funkcje, których można używać do efektywnego obsługi ciągów, które wymagają analizowania lub konwersji.

| Ciąg | Funkcja | Przykład użycia |
|--|--|--|
| Wiersze poleceń | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Wyodrębnianie polecenia i wszystkich argumentów. |
| Ścieżki | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Wyodrębnianie sekcji ścieżki pliku lub folderu. |
| Numery wersji | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Dekonstruuj numer wersji z maksymalnie czterema sekcjami i maksymalnie ośmioma znakami w sekcji. Porównywanie wieku wersji przy użyciu analizowanych danych. |
| Adresy IPv4 | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | Konwertuj adres IPv4 na długą liczbę całkowitą. Aby porównać adresy IPv4 bez ich konwertowania, użyj ipv4_compare [()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| Adresy IPv6 | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | Konwertowanie adresu IPv4 lub IPv6 na kanoniczny notację IPv6. Aby porównać adresy IPv6, użyj ipv6_compare [()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Aby uzyskać informacje na temat wszystkich obsługiwanych funkcji analizowania, [przeczytaj o funkcjach ciągów Kusto](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Dokumentacja języka kwerend Kusto](/azure/data-explorer/kusto/query/)
- [Przydziały i parametry użycia](advanced-hunting-limits.md)
- [Obsługa zaawansowanych błędów łęgowania](advanced-hunting-errors.md)
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)