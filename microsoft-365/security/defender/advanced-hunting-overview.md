---
title: Omówienie — wyszukiwanie zaawansowane
description: Dowiedz się więcej o zaawansowanych zapytaniach myśliwnych Microsoft 365, jak za ich pomocą proaktywnie odnajdować zagrożenia i wady sieci
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto
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
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 03f99f6b883a46e0a7c87d6cbdb2abb8f5552a31
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010654"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).
>

Zaawansowane szukanie to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni nieprzetworzonych danych. Możesz proaktywnie przeprowadzać inspekcje zdarzeń w sieci, aby zlokalizować wskaźniki zagrożeń i jednostki. Elastyczny dostęp do danych umożliwia niewyszkolone czasy, w których są poszukiwane zarówno znane, jak i potencjalne zagrożenia.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Za pomocą tych samych zapytań wyszukiwania zagrożeń możesz tworzyć niestandardowe reguły wykrywania. Reguły te są uruchamiane automatycznie w celu sprawdzenia, czy są wykrywane i reagować na podejrzewane naruszenie, błędnie skonfigurowane komputery i inne ustalenia.

Ta funkcja jest podobna do zaawansowanego wyszukiwania w programie [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) i obsługuje zapytania, które sprawdzają szersze zestawy danych z:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Usługa Microsoft Defender dla Office 365
- Usługa Microsoft Defender dla aplikacji w chmurze
- Microsoft Defender for Identity

Aby używać zaawansowanego wyszukiwania, [włącz tryb Microsoft 365 Defender](m365d-enable.md).

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania w usłudze Microsoft Defender dla aplikacji w chmurze, zobacz [klip wideo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>Początek zaawansowanego chłoniania

Zalecamy skorzystanie z kilku kroków, aby szybko rozpocząć zaawansowane szukanie.

| Edukacja celu | Opis | Zasób |
|--|--|--|
| **Nauka języka** | Zaawansowane wyszukiwanie jest oparte na języku [zapytań Kusto](/azure/kusto/query/), które obsługuje tę samą składnię i operatory. Rozpocznij naukę języka zapytań, uruchamiając pierwsze zapytanie. | [Omówienie języka zapytań](advanced-hunting-query-language.md) |
| **Dowiedz się, jak używać wyników zapytania** | Informacje o wykresach i różnych sposobach wyświetlania i eksportowania wyników. Poznaj sposób szybkiego poprawiania zapytań, przechodzenia do szczegółów w celu uzyskania bardziej rozbudowanych informacji i reagowania na odpowiedzi. | - [Praca z wynikami zapytania](advanced-hunting-query-results.md)<br /> - [Wykonywanie działań na wynikach zapytania](advanced-hunting-take-action.md) |
| **Opis schematu** | Uzyskaj dobry, wysoki poziom zrozumienia tabel w schemacie i ich kolumn. Dowiedz się, gdzie szukać danych podczas konstruowania zapytań. | - [Informacje o schemacie](advanced-hunting-schema-tables.md) <br />- [Przechodzenie z programu Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md) |
| **Uzyskaj porady ekspertów i przykłady** | Bezpłatne szkolenie z przewodnikami od ekspertów Microsoft. Eksplorowanie zbiorów wstępnie zdefiniowanych zapytań dotyczących różnych scenariuszy wyszukiwania zagrożeń. | - [Uzyskaj szkolenia ekspertów](advanced-hunting-expert-training.md) <br />- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md) <br />- [Przejdź do poszukiwania](advanced-hunting-go-hunt.md) <br />- [Poszukiwania zagrożeń na różnych urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md) |
| **Optymalizowanie zapytań i obsługa błędów** | Dowiedz się, jak tworzyć wydajne i wolne od błędów zapytania. | - [Najlepsze rozwiązania dotyczące zapytań](advanced-hunting-best-practices.md)<br />- [Obsługa błędów](advanced-hunting-errors.md) |
| **Tworzenie reguł wykrywania niestandardowego** | Dowiedz się, jak możesz używać zaawansowanych zapytań myśliwnych w celu wyzwalania alertów i automatycznego reagowania. | - [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md) <br />- [Niestandardowe reguły wykrywania](custom-detection-rules.md) |

## <a name="get-access"></a>Uzyskaj dostęp
Aby korzystać z zaawansowanych funkcji chłoniania [Microsoft 365 Defender](microsoft-365-defender.md), musisz mieć odpowiednią rolę w Azure Active Directory. [Przeczytaj o wymaganych rolach i uprawnieniach do zaawansowanego wyszukiwania](custom-roles.md).

Ponadto dostęp do danych punktu końcowego jest ustalany na podstawie ustawień kontroli dostępu opartej na rolach (RBAC, role based access control) w programie Microsoft Defender for Endpoint. [Przeczytaj o zarządzaniu dostępem do Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Data freshness and update frequency
Zaawansowane dane wyszukiwania można podzielić na dwie osobne typy, z których każda skonsolidowana jest w inny sposób.

- **Dane zdarzeń lub aktywności — wypełnia** tabele z alertami, zdarzeniami zabezpieczeń, zdarzeniami systemowymi i rutynowymi ocenami. Takie dane są odbierane prawie natychmiast po czujniku, który z nich pomyślnie przesłał do odpowiednich usług w chmurze. Możesz na przykład zapytanie danych zdarzeń z czujników dobrej kondycji na stacji roboczej lub kontrolerach domeny niemal natychmiast po ich dostępie w usługach Microsoft Defender for Endpoint i Microsoft Defender for Identity.
- **Dane encji** — wypełnia tabele informacjami o użytkownikach i urządzeniach. Te dane pochodzą zarówno ze względnie statycznych źródeł danych, jak i źródeł dynamicznych, takich jak wpisy usługi Active Directory i dzienniki zdarzeń. Aby udostępnić nowe dane, tabele są aktualizowane tak, aby co 15 minut zawierały nowe informacje, co dodaje wiersze, które mogą nie być w pełni wypełnione. Konsolidowane są dane co 24 godziny w celu wstawienia rekordu zawierającego najnowszy i najbardziej kompleksowy zestaw danych dotyczących każdej jednostki.

## <a name="time-zone"></a>Strefa czasowa
Informacje dotyczące czasu podczas zaawansowanego wyszukiwania są w strefie czasowej UTC.

## <a name="related-topics"></a>Tematy pokrewne
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Uzyskaj szkolenia ekspertów](advanced-hunting-expert-training.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)
