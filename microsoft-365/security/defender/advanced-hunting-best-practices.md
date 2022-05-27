---
title: Zaawansowane najlepsze rozwiązania dotyczące zapytań dotyczących wyszukiwania zagrożeń w Microsoft 365 Defender
description: Dowiedz się, jak tworzyć szybkie, wydajne i wolne od błędów zapytania dotyczące wyszukiwania zagrożeń za pomocą zaawansowanego wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagroże Microsoft 365 Defender ń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, schemat, kusto, unikanie limitu czasu, wiersze polecenia, identyfikator procesu, optymalizacja, najlepsze rozwiązanie, analizowanie, dołączanie, podsumowanie
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
ms.openlocfilehash: 505308bec005811e174b90cde9e872532ccacdfe
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739488"
---
# <a name="advanced-hunting-query-best-practices"></a>Zaawansowane najlepsze rozwiązania dotyczące zapytań dotyczących wyszukiwania zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Zastosuj te zalecenia, aby szybciej uzyskać wyniki i uniknąć przekroczenia limitu czasu podczas uruchamiania złożonych zapytań. Aby uzyskać więcej wskazówek dotyczących poprawy wydajności zapytań, przeczytaj [Kusto najlepsze rozwiązania dotyczące zapytań](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>Omówienie limitów przydziału zasobów procesora CPU
W zależności od rozmiaru każda dzierżawa ma dostęp do określonej ilości zasobów procesora CPU przydzielonych do uruchamiania zaawansowanych zapytań wyszukiwania zagrożeń. Aby uzyskać szczegółowe informacje o różnych parametrach użycia, [przeczytaj o zaawansowanych limitach przydziałów zagrożeń i parametrach użycia](advanced-hunting-limits.md).

Po uruchomieniu zapytania można zobaczyć czas wykonywania i jego użycie zasobów (niski, średni, wysoki). Wysoka wartość wskazuje, że zapytanie zajęło więcej zasobów do uruchomienia i można je ulepszyć w celu wydajniejszego zwracania wyników.

:::image type="content" source="../../media/resource-usage.png" alt-text="Szczegóły zapytania na karcie **Wyniki** w portalu Microsoft 365 Defender" lightbox="../../media/resource-usage.png":::

Klienci, którzy regularnie uruchamiają wiele zapytań, powinni śledzić użycie i stosować wskazówki dotyczące optymalizacji w tym artykule, aby zminimalizować zakłócenia wynikające z przekroczenia limitów przydziału lub parametrów użycia.

## <a name="general-optimization-tips"></a>Ogólne porady dotyczące optymalizacji

- **Rozmiar nowych zapytań** — jeśli podejrzewasz, że zapytanie zwróci duży zestaw wyników, najpierw oceń je przy użyciu [operatora count](/azure/data-explorer/kusto/query/countoperator). Użyj [limitu](/azure/data-explorer/kusto/query/limitoperator) lub jego synonimu `take` , aby uniknąć dużych zestawów wyników.
- **Zastosuj filtry wcześnie** — zastosuj filtry czasu i inne filtry, aby zmniejszyć zestaw danych, zwłaszcza przed użyciem funkcji przekształcania i analizowania, takich jak [podciąg()](/azure/data-explorer/kusto/query/substringfunction), [replace()](/azure/data-explorer/kusto/query/replacefunction), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction)lub [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). W poniższym przykładzie funkcja analizowania [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) jest używana po zmniejszeniu liczby rekordów przez operatory filtrowania.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Zawiera bity** — aby uniknąć niepotrzebnego wyszukiwania podciągów w słowach, użyj `has` operatora zamiast `contains`. [Dowiedz się więcej o operatorach ciągów](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Wyszukiwanie w określonych kolumnach** — wyszukiwanie w określonej kolumnie zamiast wykonywania wyszukiwania pełnotekstowego we wszystkich kolumnach. Nie używaj do `*` sprawdzania wszystkich kolumn.
- **Wielkość liter dla szybkości** — wyszukiwania uwzględniające wielkość liter są bardziej szczegółowe i ogólnie bardziej wydajne. Nazwy [operatorów ciągów uwzględniających wielkość](/azure/data-explorer/kusto/query/datatypes-string-operators) liter, takich jak `has_cs` i `contains_cs`, zwykle kończą się ciągiem `_cs`. Można również użyć operatora `==` równości uwzględniania wielkości liter zamiast `=~`.
- **Analizuj, nie wyodrębniaj** — jeśli to możliwe, użyj [operatora analizy](/azure/data-explorer/kusto/query/parseoperator) lub funkcji analizy, takiej jak [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). `matches regex` Unikaj operatora ciągu lub [funkcji extract(),](/azure/data-explorer/kusto/query/extractfunction) które używają wyrażenia regularnego. Zarezerwuj użycie wyrażenia regularnego w bardziej złożonych scenariuszach. [Przeczytaj więcej na temat analizowania funkcji](#parse-strings)
- **Nie filtruj tabel —** nie filtruj kolumny obliczeniowej, jeśli możesz filtrować kolumnę tabeli.
- **Brak terminów trzyznakowych** — unikaj porównywania lub filtrowania przy użyciu terminów z trzema znakami lub mniejszą liczbą znaków. Te terminy nie są indeksowane, a ich dopasowanie będzie wymagało większej ilości zasobów.
- **Project selektywnie** — ułatwić zrozumienie wyników przez projekcję tylko potrzebnych kolumn. Projekcja określonych kolumn przed uruchomieniem [sprzężenia](/azure/data-explorer/kusto/query/joinoperator) lub podobnych operacji również pomaga zwiększyć wydajność.

## <a name="optimize-the-join-operator"></a>Optymalizowanie `join` operatora
[Operator sprzężenia](/azure/data-explorer/kusto/query/joinoperator) scala wiersze z dwóch tabel, dopasowując wartości w określonych kolumnach. Zastosuj te wskazówki, aby zoptymalizować zapytania korzystające z tego operatora.

- **Mniejsza tabela po lewej stronie** — `join` operator dopasowuje rekordy w tabeli po lewej stronie instrukcji join do rekordów po prawej stronie. Mając mniejszą tabelę po lewej stronie, należy dopasować mniej rekordów, przyspieszając w ten sposób zapytanie.

    W poniższej tabeli zmniejszymy tabelę `DeviceLogonEvents` po lewej stronie, aby objąć tylko trzy określone urządzenia przed dołączeniem `IdentityLogonEvents` jej do niej według identyfikatorów SID konta.

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

- **Użyj smaku sprzężenia wewnętrznego** — domyślny [smak sprzężenia](/azure/data-explorer/kusto/query/joinoperator#join-flavors) lub [innerunique-join](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) deduplikuje wiersze w lewej tabeli przy użyciu klucza sprzężenia przed zwróceniem wiersza dla każdego dopasowania do prawej tabeli. Jeśli tabela po lewej stronie zawiera wiele wierszy o tej samej wartości dla `join` klucza, te wiersze zostaną deduplikowane, aby pozostawić pojedynczy losowy wiersz dla każdej unikatowej wartości.

    To domyślne zachowanie może pominąć ważne informacje z lewej tabeli, które mogą dostarczyć przydatnych szczegółowych informacji. Na przykład poniższe zapytanie będzie zawierać tylko jedną wiadomość e-mail zawierającą określony załącznik, nawet jeśli ten sam załącznik został wysłany przy użyciu wielu wiadomości e-mail:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    Aby rozwiązać ten problem, stosujemy smak [sprzężenia wewnętrznego](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) , określając `kind=inner` , aby wyświetlić wszystkie wiersze w lewej tabeli z pasującymi wartościami po prawej stronie:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Dołączanie rekordów z przedziału czasu** — podczas badania zdarzeń zabezpieczeń analitycy poszukają powiązanych zdarzeń występujących w tym samym okresie. Zastosowanie tego samego podejścia w przypadku korzystania `join` z funkcji zapewnia również korzyści z wydajności dzięki zmniejszeniu liczby rekordów do sprawdzenia.

    Poniższe zapytanie sprawdza zdarzenia logowania w ciągu 30 minut od otrzymania złośliwego pliku:

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
- **Stosowanie filtrów czasu po obu stronach** — nawet jeśli nie badasz określonego przedziału czasu, zastosowanie filtrów czasu w tabelach po lewej i prawej stronie może zmniejszyć liczbę rekordów w celu sprawdzenia i zwiększenia `join` wydajności. Poniższe zapytanie dotyczy `Timestamp > ago(1h)` obu tabel, dzięki czemu łączy tylko rekordy z ostatniej godziny:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Użyj wskazówek dotyczących wydajności** — użyj wskazówek z operatorem, `join` aby poinstruować zaplecze o rozłożeniu obciążenia podczas wykonywania operacji intensywnie korzystających z zasobów. [Dowiedz się więcej o wskazówkach dotyczących dołączania](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Na przykład **[wskazówki dotyczące mieszania](/azure/data-explorer/kusto/query/shufflequery)** pomagają zwiększyć wydajność zapytań podczas łączenia tabel przy użyciu klucza o wysokiej kardynalności — klucza z wieloma unikatowymi wartościami, na przykład `AccountObjectId` w poniższym zapytaniu:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    **[Wskazówka dotycząca emisji](/azure/data-explorer/kusto/query/broadcastjoin)** pomaga, gdy tabela po lewej stronie jest mała (do 100 000 rekordów), a prawa tabela jest bardzo duża. Na przykład poniższe zapytanie próbuje dołączyć kilka wiadomości e-mail, które mają określone tematy ze _wszystkimi_ wiadomościami zawierającymi linki w `EmailUrlInfo` tabeli:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>Optymalizowanie `summarize` operatora
[Operator podsumowania](/azure/data-explorer/kusto/query/summarizeoperator) agreguje zawartość tabeli. Zastosuj te wskazówki, aby zoptymalizować zapytania korzystające z tego operatora.

- **Znajdowanie unikatowych wartości** — ogólnie rzecz biorąc, użyj polecenia `summarize` , aby znaleźć różne wartości, które mogą być powtarzalne. Użycie go do agregowania kolumn, które nie mają powtarzających się wartości, może być niepotrzebne.

    Chociaż pojedyncza wiadomość e-mail może być częścią wielu zdarzeń, poniższy przykład _nie_ jest efektywnym użyciem `summarize` , ponieważ identyfikator wiadomości sieciowej dla pojedynczej wiadomości e-mail zawsze jest dostarczany z unikatowym adresem nadawcy.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    Operator `summarize` można łatwo zastąpić elementem `project`, uzyskując potencjalnie te same wyniki, zużywając mniej zasobów:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    Poniższy przykład jest bardziej efektywnym zastosowaniem, `summarize` ponieważ może istnieć wiele różnych wystąpień adresu nadawcy wysyłającego wiadomość e-mail na ten sam adres adresata. Takie kombinacje są mniej odrębne i mogą mieć duplikaty.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Mieszanie zapytania** — chociaż `summarize` najlepiej jest używać w kolumnach z powtarzającymi się wartościami, te same kolumny mogą mieć również _wysoką kardynalność lub dużą_ liczbę unikatowych wartości. `join` Podobnie jak operator, możesz również zastosować [wskazówkę mieszania](/azure/data-explorer/kusto/query/shufflequery), `summarize` aby rozłożyć obciążenie przetwarzania i potencjalnie zwiększyć wydajność podczas pracy na kolumnach o wysokiej kardynalności.

    Poniższe zapytanie używa `summarize` do zliczania odrębnego adresu e-mail adresata, który może być uruchamiany w setkach tysięcy w dużych organizacjach. Aby zwiększyć wydajność, obejmuje `hint.shufflekey`ona:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

Obejrzyj ten [krótki film wideo](https://www.youtube.com/watch?v=ceYvRuPp5D8), aby dowiedzieć się, jak zoptymalizować język zapytań Kusto.  

## <a name="query-scenarios"></a>Scenariusze zapytań

### <a name="identify-unique-processes-with-process-ids"></a>Identyfikowanie unikatowych procesów przy użyciu identyfikatorów procesów

Identyfikatory procesów są poddawane recyklingowi w Windows i ponownie używane w nowych procesach. Same w sobie nie mogą służyć jako unikatowe identyfikatory dla określonych procesów.

Aby uzyskać unikatowy identyfikator procesu na określonej maszynie, użyj identyfikatora procesu wraz z czasem tworzenia procesu. Podczas dołączania lub podsumowywania danych dotyczących procesów dołącz kolumny identyfikatora maszyny ( `DeviceId` lub `DeviceName`), identyfikator procesu (`ProcessId` lub `InitiatingProcessId`), a czas tworzenia procesu (`ProcessCreationTime` lub `InitiatingProcessCreationTime`)

Poniższe przykładowe zapytanie znajduje procesy, które uzyskują dostęp do ponad 10 adresów IP za pośrednictwem portu 445 (SMB), prawdopodobnie skanując udziały plików.

Przykładowe zapytanie:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

Zapytanie jest podsumowywane zarówno `InitiatingProcessId` przez, jak i `InitiatingProcessCreationTime` w taki sposób, że analizuje jeden proces bez mieszania wielu procesów z tym samym identyfikatorem procesu.

### <a name="query-command-lines"></a>Wiersze poleceń zapytania
Istnieje wiele sposobów konstruowania wiersza polecenia w celu wykonania zadania. Na przykład osoba atakująca może odwoływać się do pliku obrazu bez ścieżki, bez rozszerzenia pliku, przy użyciu zmiennych środowiskowych lub z cudzysłowami. Osoba atakująca może również zmienić kolejność parametrów lub dodać wiele cudzysłowów i spacji.

Aby utworzyć bardziej trwałe zapytania wokół wierszy poleceń, zastosuj następujące rozwiązania:

- Zidentyfikuj znane procesy (takie jak *net.exe* lub *psexec.exe*), dopasowując je do pól nazw plików, zamiast filtrować w samym wierszu polecenia.
- Analizowanie sekcji wiersza polecenia przy użyciu [funkcji parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line)
- Podczas wykonywania zapytań o argumenty wiersza polecenia nie szukaj dokładnego dopasowania dla wielu niepowiązanych argumentów w określonej kolejności. Zamiast tego użyj wyrażeń regularnych lub użyj wielu oddzielnych operatorów zawiera.
- Używanie dopasowań bez uwzględniania wielkości liter. Na przykład użyj wartości `=~`, `in~`i `contains` zamiast `==`, `in`i `contains_cs`.
- Aby wyeliminować techniki zaciemniania wiersza polecenia, rozważ usunięcie cudzysłowów, zastąpienie przecinków spacjami i zastąpienie wielu kolejnych spacji pojedynczym spacji. Istnieją bardziej złożone techniki zaciemniania, które wymagają innych metod, ale te poprawki mogą pomóc w rozwiązaniu typowych z nich.

W poniższych przykładach przedstawiono różne sposoby konstruowania zapytania, które szuka pliku *net.exe* zatrzymania usługi zapory "MpsSvc":

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

### <a name="ingest-data-from-external-sources"></a>Pozyskiwanie danych ze źródeł zewnętrznych
Aby uwzględnić długie listy lub duże tabele w zapytaniu, użyj [operatora externaldata do pozyskiwania](/azure/data-explorer/kusto/query/externaldata-operator) danych z określonego identyfikatora URI. Dane z plików można pobierać w formatach TXT, CSV, JSON lub [innych.](/azure/data-explorer/ingestion-supported-formats) W poniższym przykładzie pokazano, jak można użyć obszernej listy skrótów sha-256 złośliwego oprogramowania dostarczonych przez malwareBazaar (abuse.ch) do sprawdzania załączników w wiadomościach e-mail:

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
Istnieją różne funkcje, których można użyć do wydajnego obsługi ciągów, które wymagają analizowania lub konwersji.

| Ciąg | Funkcja | Przykład użycia |
|--|--|--|
| Wiersze polecenia | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Wyodrębnij polecenie i wszystkie argumenty. |
| Ścieżki | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Wyodrębnij sekcje ścieżki pliku lub folderu. |
| Numery wersji | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Zdekonstruuj numer wersji z maksymalnie czterema sekcjami i maksymalnie ośmioma znakami na sekcję. Użyj przeanalizowanych danych, aby porównać wiek wersji. |
| Adresy IPv4 | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | Konwertuj adres IPv4 na długą liczbę całkowitą. Aby porównać adresy IPv4 bez ich konwertowania, użyj [ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| Adresy IPv6 | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | Przekonwertuj adres IPv4 lub IPv6 na kanoniczną notację IPv6. Aby porównać adresy IPv6, użyj [ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Aby dowiedzieć się więcej o wszystkich obsługiwanych funkcjach analizowania, [przeczytaj o funkcjach ciągu Kusto](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender. [Włącz Microsoft 365 Defender](m365d-enable.md), aby wyszukiwać zagrożenia przy użyciu większej liczby źródeł danych. Zaawansowane przepływy pracy wyszukiwania zagrożeń można przenieść z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender, wykonując kroki opisane w [temacie Migrowanie zaawansowanych zapytań wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [dokumentacja języka zapytań Kusto](/azure/data-explorer/kusto/query/)
- [Przydziały i parametry użycia](advanced-hunting-limits.md)
- [Obsługa zaawansowanych błędów wyszukiwania zagrożeń](advanced-hunting-errors.md)
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)