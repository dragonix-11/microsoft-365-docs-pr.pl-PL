---
title: Praca z zaawansowanymi wynikami zapytania wyszukiwania zagrożeń w Microsoft 365 Defender
description: Jak najlepiej wykorzystać wyniki zapytania zwracane przez zaawansowane wyszukiwanie zagrożeń w Microsoft 365 Defender
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wykrywanie zagrożeń cybernetycznych, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, wizualizacja, wykres, filtry, przechodzenie do szczegółów
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
ms.openlocfilehash: cb17e2a3624471031eb4f72199705d6b8fe06979
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092872"
---
# <a name="work-with-advanced-hunting-query-results"></a>Praca z zaawansowanymi wynikami zapytania wyszukiwania zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Chociaż możesz utworzyć zaawansowane zapytania [wyszukiwania zagrożeń](advanced-hunting-overview.md) w celu zwrócenia dokładnych informacji, możesz również pracować z wynikami zapytania, aby uzyskać dalszy wgląd i zbadać konkretne działania i wskaźniki. Możesz wykonać następujące akcje w wynikach zapytania:

- Wyświetlanie wyników jako tabeli lub wykresu
- Eksportowanie tabel i wykresów
- Przechodzenie do szczegółów szczegółowych informacji o jednostce
- Dostosowywanie zapytań bezpośrednio z wyników

## <a name="view-query-results-as-a-table-or-chart"></a>Wyświetlanie wyników zapytania jako tabeli lub wykresu

Domyślnie zaawansowane wyszukiwanie zagrożeń wyświetla wyniki zapytania jako dane tabelaryczne. Możesz również wyświetlić te same dane co wykres. Zaawansowane wyszukiwanie zagrożeń obsługuje następujące widoki:

| Typ widoku | Opis |
|--|--|
| **Tabeli** | Wyświetla wyniki zapytania w formacie tabelarycznym |
| **Wykres kolumnowy** | Renderuje serię unikatowych elementów na osi x jako pionowe słupki, których wysokość reprezentuje wartości liczbowe z innego pola |
| **Wykres kołowy** | Renderuje fragmenty reprezentujące unikatowe elementy. Rozmiar każdego tortu reprezentuje wartości liczbowe z innego pola. |
| **Wykres liniowy** | Wykreśla wartości liczbowe dla serii unikatowych elementów i łączy wykreślone wartości |
| **Wykres punktowy** | Wykreśla wartości liczbowe dla serii unikatowych elementów |
| **Wykres warstwowy** | Kreśli wartości liczbowe dla serii unikatowych elementów i wypełnia sekcje poniżej wykreślonych wartości |
| **Skumulowany wykres warstwowy** | Kreśli wartości liczbowe dla serii unikatowych elementów i umieszcza wypełnione sekcje poniżej wykreślonych wartości  |
| **Wykres czasowe** | Kreśla wartości według liczby w liniowej skali czasu |

### <a name="construct-queries-for-effective-charts"></a>Konstruowanie zapytań dla efektywnych wykresów

Podczas renderowania wykresów zaawansowane wyszukiwanie zagrożeń automatycznie identyfikuje interesujące kolumny i wartości liczbowe do zagregowania. Aby uzyskać istotne wykresy, skonstruuj zapytania, aby zwracać określone wartości, które chcesz wyświetlić, zwizualizowane. Oto kilka przykładowych zapytań i wykresów wynikowych.

#### <a name="alerts-by-severity"></a>Alerty według ważności

Użyj operatora, `summarize` aby uzyskać liczbę liczbową wartości, które chcesz utworzyć na wykresie. Poniższe zapytanie używa `summarize` operatora w celu uzyskania liczby alertów według ważności.

```kusto
AlertInfo
| summarize Total = count() by Severity
```

Podczas renderowania wyników wykres kolumnowy wyświetla każdą wartość ważności jako oddzielną kolumnę:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Przykład wykresu, który wyświetla zaawansowane wyniki wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Wyniki zapytań dla alertów według ważności wyświetlanych jako wykres kolumnowy*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Wyłudzanie informacji o wiadomościach e-mail w dziesięciu najważniejszych domenach nadawcy

Jeśli masz do czynienia z listą wartości, które nie są skończone, możesz użyć `Top` operatora do wykresu tylko wartości z większością wystąpień. Aby na przykład uzyskać 10 najważniejszych domen nadawców z największą liczba wiadomości e-mail wyłudzających informacje, użyj poniższego zapytania:

```kusto
EmailEvents
| where ThreatTypes has "Phish"
| summarize Count = count() by SenderFromDomain
| top 10 by Count
```

Użyj widoku wykresu kołowego, aby skutecznie pokazać dystrybucję w najważniejszych domenach:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Wykres kołowy przedstawiający zaawansowane wyniki wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*Wykres kołowy przedstawiający dystrybucję wiadomości e-mail wyłudzających informacje w domenach nadawcy*

#### <a name="file-activities-over-time"></a>Działania dotyczące plików w czasie
`summarize` Za pomocą operatora z funkcją `bin()` można sprawdzić zdarzenia dotyczące określonego wskaźnika w czasie. Poniższe zapytanie zlicza zdarzenia dotyczące pliku `invoice.doc` w 30-minutowych interwałach, aby pokazać skoki aktywności związane z tym plikiem:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```

Poniższy wykres liniowy wyraźnie wyróżnia okresy z większą aktywnością obejmującą `invoice.doc`:

:::image type="content" source="../../media/line-chart-a.png" alt-text="Wykres liniowy przedstawiający zaawansowane wyniki wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="../../media/line-chart-a.png":::
*Wykres liniowy przedstawiający liczbę zdarzeń dotyczących pliku w czasie*

## <a name="export-tables-and-charts"></a>Eksportowanie tabel i wykresów

Po uruchomieniu zapytania wybierz pozycję **Eksportuj** , aby zapisać wyniki w pliku lokalnym. Wybrany widok określa sposób eksportowania wyników:

- **Widok tabeli** — wyniki zapytania są eksportowane w formie tabelarycznej jako skoroszyt Microsoft Excel
- **Dowolny wykres** — wyniki zapytania są eksportowane jako obraz JPEG renderowanego wykresu

## <a name="drill-down-from-query-results"></a>Przechodzenie do szczegółów z wyników zapytania

Aby szybko sprawdzić rekord w wynikach zapytania, wybierz odpowiedni wiersz, aby otworzyć panel **Inspekcja rekordów** . Panel zawiera następujące informacje na podstawie wybranego rekordu:

- **Zasoby** — podsumowany widok głównych zasobów (skrzynek pocztowych, urządzeń i użytkowników) znalezionych w rekordzie, wzbogacony o dostępne informacje, takie jak poziomy ryzyka i narażenia
- **Wszystkie szczegóły** — wszystkie wartości z kolumn w rekordzie

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Wybrany rekord z panelem do inspekcji rekordu w portalu Microsoft 365 Defender" lightbox="../../media/results-inspect-record.png":::

Aby wyświetlić więcej informacji o określonej jednostce w wynikach zapytania, takich jak maszyna, plik, użytkownik, adres IP lub adres URL, wybierz identyfikator jednostki, aby otworzyć szczegółową stronę profilu dla tej jednostki.

## <a name="tweak-your-queries-from-the-results"></a>Dostosowywanie zapytań na podstawie wyników

Wybierz trzy kropki po prawej stronie dowolnej kolumny w panelu **Inspekcja rekordu** . Możesz użyć opcji, aby:

- Jawne wyszukiwanie wybranej wartości (`==`)
- Wyklucz wybraną wartość z zapytania (`!=`)
- Uzyskiwanie bardziej zaawansowanych operatorów do dodawania wartości do zapytania, takich jak `contains`, `starts with`i `ends with`

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Okienko Typ akcji na stronie Inspekcja rekordu w portalu Microsoft 365 Defender" lightbox="../../media/work-with-query-tweak-query.png":::

> [!NOTE]
> Niektóre tabele w tym artykule mogą nie być dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender. [Włącz Microsoft 365 Defender](m365d-enable.md), aby wyszukiwać zagrożenia przy użyciu większej liczby źródeł danych. Zaawansowane przepływy pracy wyszukiwania zagrożeń można przenieść z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender, wykonując kroki opisane w [temacie Migrowanie zaawansowanych zapytań wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)
