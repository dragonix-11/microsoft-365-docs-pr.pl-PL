---
title: Omówienie — zaawansowane wyszukiwanie zagrożeń
description: Dowiedz się więcej o zaawansowanych zapytaniach dotyczących wyszukiwania zagrożeń w Microsoft 365 i sposobie ich używania do aktywnego znajdowania zagrożeń i słabych stron w sieci
keywords: zaawansowane wyszukiwanie zagrożeń, polowanie na zagrożenia, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wykrywanie zagrożeń cybernetycznych, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto
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
ms.openlocfilehash: 1ee8d8fbd3b1a56f83106ffaf6be937fa984c272
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731444"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Proaktywne wyszukiwanie zagrożeń dzięki zaawansowanym polowaniom w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Zaawansowane wyszukiwanie zagrożeń to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia eksplorowanie nieprzetworzonych danych przez maksymalnie 30 dni. Możesz proaktywnie sprawdzać zdarzenia w sieci, aby zlokalizować wskaźniki zagrożeń i jednostki. Elastyczny dostęp do danych umożliwia nieograniczone wyszukiwanie zagrożeń zarówno znanych, jak i potencjalnych.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Możesz użyć tych samych zapytań wyszukiwania zagrożeń, aby utworzyć niestandardowe reguły wykrywania. Te reguły są uruchamiane automatycznie w celu sprawdzania, a następnie reagowania na podejrzenie naruszenia zabezpieczeń, nieprawidłowo skonfigurowane maszyny i inne ustalenia.

Ta funkcja jest podobna do [zaawansowanego wyszukiwania zagrożeń w Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) i obsługuje zapytania, które sprawdzają szerszy zestaw danych z:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Ochrona usługi Office 365 w usłudze Microsoft Defender
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

Aby użyć zaawansowanego wyszukiwania zagrożeń, [włącz Microsoft 365 Defender](m365d-enable.md).

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania zagrożeń w Microsoft Defender for Cloud Apps danych, zobacz [wideo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>Wprowadzenie z zaawansowanym wyszukiwaniem zagrożeń

Zalecamy wykonanie kilku kroków, aby szybko rozpocząć zaawansowane wyszukiwanie zagrożeń.

| cel Edukacja | Opis | Zasób |
|--|--|--|
| **Nauka języka** | Zaawansowane wyszukiwanie zagrożeń opiera się na [języku zapytań Kusto](/azure/kusto/query/) obsługujących tę samą składnię i operatory. Rozpocznij naukę języka zapytań, uruchamiając pierwsze zapytanie. | [Omówienie języka zapytań](advanced-hunting-query-language.md) |
| **Dowiedz się, jak używać wyników zapytania** | Dowiedz się więcej o wykresach i różnych sposobach wyświetlania lub eksportowania wyników. Dowiedz się, jak szybko dostosować zapytania, przejść do szczegółów, aby uzyskać bogatsze informacje i podjąć akcje odpowiedzi. | - [Praca z wynikami zapytania](advanced-hunting-query-results.md)<br /> - [Wykonywanie akcji w wynikach zapytania](advanced-hunting-take-action.md) |
| **Analiza schematu** | Uzyskaj dobrą, ogólną wiedzę na temat tabel w schemacie i ich kolumnach. Dowiedz się, gdzie szukać danych podczas konstruowania zapytań. | - [Dokumentacja schematu](advanced-hunting-schema-tables.md) <br />- [Przejście z Ochrona punktu końcowego w usłudze Microsoft Defender](advanced-hunting-migrate-from-mde.md) |
| **Uzyskiwanie porad i przykładów ekspertów** | Trenowanie bezpłatnie za pomocą przewodników od ekspertów firmy Microsoft. Eksploruj kolekcje wstępnie zdefiniowanych zapytań obejmujących różne scenariusze wyszukiwania zagrożeń. | - [Uzyskiwanie szkoleń ekspertów](advanced-hunting-expert-training.md) <br />- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md) <br />- [Go hunt](advanced-hunting-go-hunt.md) <br />- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md) |
| **Optymalizowanie zapytań i obsługa błędów** | Dowiedz się, jak tworzyć wydajne i wolne od błędów zapytania. | - [Najlepsze rozwiązania dotyczące zapytań](advanced-hunting-best-practices.md)<br />- [Obsługa błędów](advanced-hunting-errors.md) |
| **Tworzenie niestandardowych reguł wykrywania** | Dowiedz się, jak za pomocą zaawansowanych zapytań wyszukiwania zagrożeń wyzwalać alerty i automatycznie podejmować akcje reagowania. | - [Omówienie wykrywania niestandardowego](custom-detections-overview.md) <br />- [Niestandardowe reguły wykrywania](custom-detection-rules.md) |

## <a name="get-access"></a>Uzyskiwanie dostępu
Aby korzystać z zaawansowanych możliwości wyszukiwania zagrożeń lub innych [Microsoft 365 Defender](microsoft-365-defender.md), potrzebna jest odpowiednia rola w Azure Active Directory. [Przeczytaj o wymaganych rolach i uprawnieniach do zaawansowanego wyszukiwania zagrożeń](custom-roles.md).

Ponadto dostęp do danych punktu końcowego jest określany przez ustawienia kontroli dostępu opartej na rolach (RBAC) w Ochrona punktu końcowego w usłudze Microsoft Defender. [Przeczytaj o zarządzaniu dostępem do Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Częstotliwość odświeżenia i aktualizacji danych
Zaawansowane dane wyszukiwania zagrożeń można podzielić na dwa różne typy, z których każdy jest konsolidowany inaczej.

- **Dane zdarzeń lub działań** — wypełnia tabele dotyczące alertów, zdarzeń zabezpieczeń, zdarzeń systemowych i rutynowych ocen. Zaawansowane wyszukiwanie zagrożeń odbiera te dane niemal natychmiast po tym, jak czujniki, które je pomyślnie zbierają, przekazują je do odpowiednich usług w chmurze. Na przykład można wysyłać zapytania dotyczące danych zdarzeń z czujników w dobrej kondycji na stacjach roboczych lub kontrolerach domeny niemal natychmiast po ich udostępnieniu w Ochrona punktu końcowego w usłudze Microsoft Defender i Microsoft Defender for Identity.
- **Dane jednostki** — wypełnia tabele informacjami o użytkownikach i urządzeniach. Te dane pochodzą zarówno ze względnie statycznych źródeł danych, jak i źródeł dynamicznych, takich jak wpisy usługi Active Directory i dzienniki zdarzeń. Aby zapewnić świeże dane, tabele są aktualizowane przy użyciu nowych informacji co 15 minut, dodając wiersze, które mogą nie być w pełni wypełnione. Co 24 godziny dane są konsolidowane w celu wstawiania rekordu zawierającego najnowszy, najbardziej kompleksowy zestaw danych o każdej jednostce.

## <a name="time-zone"></a>Strefa czasowa
Informacje o czasie w zaawansowanym polowaniu znajdują się w strefie czasowej UTC.

## <a name="related-topics"></a>Tematy pokrewne
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Uczestniczenie w szkoleniu dla ekspertów](advanced-hunting-expert-training.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)
