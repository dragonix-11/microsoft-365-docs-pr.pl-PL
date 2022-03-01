---
title: Omówienie zaawansowanego wyszukiwania w programie Microsoft Defender dla punktu końcowego
description: Korzystaj z możliwości wyszukiwania zagrożeń w programie Microsoft Defender dla punktu końcowego, aby tworzyć zapytania, które znajdują zagrożenia i niechęć w Twojej sieci
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, mdatp, microsoft defender atp, microsoft defender for endpoint, wdatp, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, strefa czasowa, UTC
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2e1b6a5bb77dc757861a5d7f56d8a4380c6fc6c1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997414"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting"></a>Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Zaawansowane szukanie to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni nieprzetworzone dane. Możesz proaktywnie przeprowadzać inspekcje zdarzeń w sieci, aby zlokalizować wskaźniki zagrożeń i jednostki. Elastyczny dostęp do danych umożliwia niewyszkolone czasy, w których są poszukiwane zarówno znane, jak i potencjalne zagrożenia.

Obejrzyj ten klip wideo, aby szybko rozpocząć pracę, a także obejrzyj krótki samouczek, który pomoże Ci szybko rozpocząć pracę.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqo]

Za pomocą tych samych zapytań wyszukiwania zagrożeń możesz tworzyć niestandardowe reguły wykrywania. Reguły te są uruchamiane automatycznie w celu sprawdzenia, czy są wykrywane i reagować na podejrzewane naruszenie, błędnie skonfigurowane komputery i inne ustalenia.

> [!TIP]
> Użyj [zaawansowanego](/microsoft-365/security/defender/advanced-hunting-overview) wyszukiwania w Microsoft 365 Defender, aby poszukać zagrożeń za pomocą danych z usługi Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender dla aplikacji w chmurze i Microsoft Defender for Identity. [Włącz Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

Aby dowiedzieć się więcej na temat przenoszenia zaawansowanych przepływów pracy wyszukiwania z programu Microsoft Defender for Endpoint do Microsoft 365 Defender zobacz Migrowanie zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="get-started-with-advanced-hunting"></a>Początek zaawansowanego chłoniania

Aby rozszerz swoją zaawansowaną wiedzę na temat wyszukiwania, przejdź przez poniższe kroki.

Zalecamy skorzystanie z kilku kroków, aby szybko rozpocząć łętwtwo zaawansowane.

<br>

****

|Edukacja celu|Opis|Zasób|
|---|---|---|
|**Nauka języka**|Zaawansowane wyszukiwanie jest oparte na języku [zapytań Kusto](/azure/kusto/query/), które obsługuje tę samą składnię i operatory. Rozpocznij naukę języka zapytań, uruchamiając pierwsze zapytanie.|[Omówienie języka zapytań](advanced-hunting-query-language.md)|
|**Dowiedz się, jak używać wyników zapytania**|Informacje o wykresach i różnych sposobach wyświetlania i eksportowania wyników. Poznaj sposób szybkiego poprawiania zapytań i przechodzenia do szczegółów w celu uzyskania bardziej rozbudowanych informacji.|[Praca z wynikami zapytania](advanced-hunting-query-results.md)|
|**Opis schematu**|Uzyskaj dobry, wysoki poziom zrozumienia tabel w schemacie i ich kolumn. Dowiedz się, gdzie szukać danych podczas konstruowania zapytań.|[Informacje o schemacie](advanced-hunting-schema-reference.md)|
|**Używanie wstępnie zdefiniowanych zapytań**|Eksplorowanie zbiorów wstępnie zdefiniowanych zapytań dotyczących różnych scenariuszy wyszukiwania zagrożeń.|[Zapytania udostępnione](advanced-hunting-shared-queries.md)|
|**Optymalizowanie zapytań i obsługa błędów**|Dowiedz się, jak tworzyć wydajne i wolne od błędów zapytania.|[Najlepsze rozwiązania dotyczące zapytań](advanced-hunting-best-practices.md) <p> [Obsługa błędów](advanced-hunting-errors.md)|
|**Uzyskiwanie najpełniejszego zakresu**|Użyj ustawień inspekcji, aby zapewnić lepszy zakres danych dla organizacji.|[Rozszerzanie zaawansowanego zakresu wyszukiwania](advanced-hunting-extend-data.md)|
|**Uruchamianie szybkiego badania**|Szybko uruchom zaawansowane zapytanie wyszukiwania w celu zbadania podejrzanych działań.|[Szybkie poszukiwania informacji o encji lub zdarzeniach za pomocą *ponagowego poszukiwania*](advanced-hunting-go-hunt.md)|
|**Zawieraj zagrożenia i wyeksymilij naruszenia**|Reagowanie na ataki ze względu na nieoczekiwane pliki, ograniczanie wykonywania aplikacji i innych akcji|[Weź udział w zaawansowanych wyszukiwaniach wyników kwerendy](advanced-hunting-take-action.md)|
|**Tworzenie reguł wykrywania niestandardowego**|Dowiedz się, jak możesz używać zaawansowanych zapytań myśliwnych w celu wyzwalania alertów i automatycznego reagowania.|[Wykrywanie niestandardowe — omówienie](overview-custom-detections.md) <p> [Niestandardowe reguły wykrywania](custom-detection-rules.md)|
|

## <a name="data-freshness-and-update-frequency"></a>Data freshness and update frequency

Zaawansowane dane wyszukiwania można podzielić na dwie osobne typy, z których każda skonsolidowana jest w inny sposób.

- **Dane zdarzeń lub aktywności**: Wypełnia tabele dotyczące alertów, zdarzeń zabezpieczeń, zdarzeń systemu i rutynowych testów. Szukanie zaawansowane otrzymuje te dane niemal natychmiast po czujniku, który je zbiera, aby pomyślnie przesłać je do usługi Defender for Endpoint.
- **Dane encja**: Wypełnia tabele skonsolidowanymi informacjami o użytkownikach i urządzeniach. Te dane pochodzą zarówno ze względnie statycznych źródeł danych, jak i źródeł dynamicznych, takich jak wpisy usługi Active Directory i dzienniki zdarzeń. Aby udostępnić nowe dane, tabele są aktualizowane tak, aby co 15 minut zawierały nowe informacje, co dodaje wiersze, które mogą nie być w pełni wypełnione. Konsolidowane są dane co 24 godziny w celu wstawienia rekordu zawierającego najnowszy i najbardziej kompleksowy zestaw danych dotyczących każdej jednostki.

## <a name="time-zone"></a>Strefa czasowa

Informacje o czasie podczas zaawansowanego wyszukiwania są obecnie w strefie czasowej UTC.

## <a name="related-topics"></a>Tematy pokrewne

- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytania](advanced-hunting-query-results.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Opis schematu](advanced-hunting-schema-reference.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](overview-custom-detections.md)
- [Omówienie Storage konta](/azure/storage/common/storage-account-overview)
- [Azure Event Hubs — platforma do przesyłania strumieniowego dużych danych i usługa ingestion zdarzeń](/azure/event-hubs/event-hubs-about)
