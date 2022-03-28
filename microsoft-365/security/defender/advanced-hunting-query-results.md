---
title: Praca z zaawansowanymi wynikami wyszukiwania w programie Microsoft 365 Defender
description: W większości przypadków wyniki zapytania są zwracane przez zaawansowane szukanie w Microsoft 365 Defender
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, wizualizacja, wykres, filtry, przechodzenie do szczegółów
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
ms.openlocfilehash: 41427760a0a02f0dafbb9685da457a473698207c
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755009"
---
# <a name="work-with-advanced-hunting-query-results"></a>Praca z zaawansowanymi wynikami zapytania wyszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Możesz konstruować [zaawansowane zapytania](advanced-hunting-overview.md) myśliwskie, aby zwrócić precyzyjne informacje, ale możesz również pracować z wynikami zapytania, aby uzyskać bardziej szczegółowe informacje oraz zbadać określone działania i wskaźniki. W wynikach zapytania można podjąć następujące działania:

- Wyświetlanie wyników w widoku tabeli lub wykresu
- Eksportowanie tabel i wykresów
- Przechodzenie do szczegółów szczegółowych informacji o encji
- Poprawianie zapytań bezpośrednio z wyników lub stosowanie filtrów

## <a name="view-query-results-as-a-table-or-chart"></a>Wyświetlanie wyników zapytania jako tabeli lub wykresu
Domyślnie funkcja wyszukiwania zaawansowanego wyświetla wyniki zapytania jako dane tabelarowe. Możesz również wyświetlić te same dane co wykres. Zaawansowane wyszukiwanie obsługuje następujące widoki:

| Typ widoku | Opis |
|--|--|
| **Tabela** | Wyświetla wyniki zapytania w formacie tabelarykim. |
| **Wykres kolumnowy** | Renderowanie serii unikatowych elementów na osi x jako pionowych słupków, których wysokości reprezentują wartości liczbowe z innego pola |
| **Skumulowany wykres kolumnowy** | Renderuje serię unikatowych elementów na osi x jako skumulowane słupki pionowe, których wysokości reprezentują wartości liczbowe z innych pól. |
| **Wykres kołowy** | Renderuje pies sekcji z unikatowymi elementami. Rozmiar każdego koła odpowiada wartościom liczbowym z innego pola. |
| **Wykres pierścieniowy** | Renderuje łuki sekcji reprezentujące unikatowe elementy. Długość każdego łuku odpowiada wartościom liczbowym z innego pola. |
| **Wykres liniowy** | Kreśl wartości liczbowe dla serii unikatowych elementów i łączy wartości kreślone. |
| **Wykres punktowy** | Kreśl wartości liczbowe dla serii unikatowych elementów. |
| **Wykres obszarowy** | Kreśli wartości liczbowe dla serii unikatowych elementów i wypełnia sekcje poniżej kreślonych wartości. |

### <a name="construct-queries-for-effective-charts"></a>Konstruowanie zapytań w celu efektywnego tworzenia wykresów
Podczas renderowania wykresów zaawansowane wyszukiwania automatycznie identyfikują interesujące kolumny i wartości liczbowe do agregowania. Aby uzyskać wykresy opisowe, konstruuj zapytania, aby zwracać określone wartości, które mają być widoczne jako wizualizowane. Oto kilka przykładowych zapytań i wykresów wynikowych.

#### <a name="alerts-by-severity"></a>Alerty według ważności
Użyj operatora `summarize` , aby uzyskać liczbę liczb wartości, które mają zostać na wykresie. Poniższe zapytanie używa operatora `summarize` w celu uzyskania liczby alertów według ważności.

```kusto
AlertInfo
| summarize Total = count() by Severity
```
Podczas renderowania wyników na wykresie kolumnowym są wyświetlane poszczególne wartości ważności w oddzielnej kolumnie:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Przykład wykresu, który przedstawia zaawansowane wyniki wyszukiwania w portalu Microsoft 365 Defender pracy" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Wyniki kwerend dotyczące alertów według ważności wyświetlane jako wykres kolumnowy*


#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Wyłudzanie informacji e-mail w dziesięciu najlepszych domenach nadawców
Jeśli masz do czynienia z listą wartości, które nie są skończone, `Top` możesz użyć operatora do wykresu tylko wartości dla większości wystąpień. Aby na przykład uzyskać 10 domen nadawców z najwięcej wiadomości e-mail wyłudzających informacje, użyj poniższego zapytania:

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
Widok wykresu kołowego umożliwia efektywne pokazanie rozkładu między domenami o najwyższej jakości:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Wykres kołowy, na którym są wyświetlane zaawansowane wyniki wyszukiwania w portalu Microsoft 365 Defender wyszukiwania" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*Wykres kołowy, na który widać rozkład wiadomości e-mail wyłudzających informacje w domenach najlepszych nadawców*

#### <a name="file-activities-over-time"></a>Działania związane z plikami w czasie
Używając operatora `summarize` z funkcją `bin()` , możesz sprawdzić, czy zdarzenia dotyczące określonego wskaźnika są w czasie. Poniższe zapytanie zlicza zdarzenia dotyczące pliku w `invoice.doc` 30-minutowych interwałach w celu pokazania kolekcji aktywności związanych z tym plikiem:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
Na poniższym wykresie liniowym wyraźnie wyróżnione są okresy o większej aktywności obejmującej `invoice.doc`: 

:::image type="content" source="../../media/line-chart-a.png" alt-text="Wykres liniowy, na którym są wyświetlane zaawansowane wyniki wyszukiwania w portalu Microsoft 365 Defender wyszukiwania" lightbox="../../media/line-chart-a.png":::
*Wykres liniowy przedstawiający liczbę zdarzeń dotyczących pliku w czasie*


## <a name="export-tables-and-charts"></a>Eksportowanie tabel i wykresów
Po uruchomieniu zapytania wybierz pozycję **Eksportuj** , aby zapisać wyniki w pliku lokalnym. Wybrany widok określa sposób eksportowania wyników:

- **Widok tabeli** — wyniki zapytania są eksportowane w postaci tabelarowej jako Microsoft Excel skoroszytu
- **Dowolny wykres** — wyniki zapytania są eksportowane jako obraz JPEG renderowanego wykresu

## <a name="drill-down-from-query-results"></a>Przechodzenie do szczegółów w wynikach zapytania
Aby szybko sprawdzić rekord w wynikach zapytania, wybierz odpowiedni wiersz w celu otwarcia **panelu inspekcji** rekordów. Na podstawie wybranego rekordu panel udostępnia następujące informacje:

- **Składniki** majątku — podsumowany widok głównych zasobów (skrzynek pocztowych, urządzeń i użytkowników) znalezionych w rekordzie, wzbogacany o dostępne informacje, takie jak poziomy ryzyka i poziomu ekspozycji
- **Wszystkie szczegóły** — wszystkie wartości z kolumn w rekordzie  

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Wybrany rekord z panelem do sprawdzania rekordu w portalu Microsoft 365 Defender danych" lightbox="../../media/results-inspect-record.png":::

Aby wyświetlić więcej informacji o określonej encji w wynikach zapytania, takiej jak komputer, plik, użytkownik, adres IP lub adres URL, wybierz identyfikator jednostki, aby otworzyć szczegółową stronę profilu dla tej jednostki.

## <a name="tweak-your-queries-from-the-results"></a>Poprawianie zapytań z wyników
Wybierz trzy kropki z prawej strony dowolnej kolumny w **panelu Inspekcja** rekordów. Za pomocą tych opcji można:

- Jawnie poszukaj wybranej wartości (`==`)
- Wykluczenie zaznaczonej wartości z zapytania (`!=`)
- Uzyskaj bardziej zaawansowane operatory do dodawania wartości do zapytania, `contains`takie jak , `starts with`czy `ends with` 

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Okienko Typ akcji na stronie Inspekcja rekordu w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/work-with-query-tweak-query.png":::



>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)
