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
ms.openlocfilehash: e127f757b2aaa2865e8cb109699d76ed79f41cb6
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990278"
---
# <a name="work-with-advanced-hunting-query-results"></a>Praca z zaawansowanymi wynikami zapytania wyszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Mimo że możesz [konstruować zaawansowane](advanced-hunting-overview.md) zapytania myśliwskie, aby zwrócić bardzo precyzyjne informacje, możesz również pracować z wynikami zapytania, aby uzyskać bardziej szczegółowe informacje oraz zbadać określone działania i wskaźniki. W wynikach zapytania można podjąć następujące działania:

- Wyświetlanie wyników w widoku tabeli lub wykresu
- Eksportowanie tabel i wykresów
- Przechodzenie do szczegółów szczegółowych informacji o encji
- Poprawianie zapytań bezpośrednio z wyników lub stosowanie filtrów

## <a name="view-query-results-as-a-table-or-chart"></a>Wyświetlanie wyników zapytania jako tabeli lub wykresu
Domyślnie funkcja wyszukiwania zaawansowanego wyświetla wyniki zapytania jako dane tabelarowe. Możesz również wyświetlić te same dane co wykres. Zaawansowane wyszukiwanie obsługuje następujące widoki:

| Typ widoku | Opis |
| -- | -- |
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

![Obraz zaawansowanych wyników wyszukiwania wyszukiwania wyświetlanych jako wykres kolumnowy.](../../media/advanced-hunting-column-chart-new.png)
 *Wyniki kwerend dotyczące alertów według ważności wyświetlane jako wykres kolumnowy*


#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Wyłudzanie informacji e-mail w dziesięciu najlepszych domenach nadawców
Jeśli masz do czynienia z listą wartości, które nie są skończone, `Top` możesz użyć operatora do wykresu tylko wartości dla większości wystąpień. Aby na przykład uzyskać dziesięć najlepszych domen nadawców przy użyciu wiadomości e-mail, które najczęściej wyłudzają informacje, użyj poniższego zapytania:

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
Widok wykresu kołowego umożliwia efektywne pokazanie rozkładu między domenami o najwyższej jakości:

![Obraz zaawansowanych wyników wyszukiwania wyszukiwania wyświetlanych jako wykres kołowy.](../../media/advanced-hunting-pie-chart-new.png)
 *Wykres kołowy przedstawiający rozkład wiadomości e-mail wyłudzających informacje w domenach najlepszych nadawców*

#### <a name="file-activities-over-time"></a>Działania związane z plikami w czasie
Używając operatora `summarize` z funkcją `bin()` , możesz sprawdzić, czy zdarzenia dotyczące określonego wskaźnika są w czasie. Poniższe zapytanie zlicza zdarzenia dotyczące pliku w `invoice.doc` interwałach 30-minutowych w celu pokazania kolekcji aktywności związanych z tym plikiem:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
Na poniższym wykresie liniowym wyraźnie wyróżnione są okresy o większej aktywności obejmującej `invoice.doc`: 

![Obraz zaawansowanych wyników wyszukiwania wyszukiwania wyświetlanych jako wykres liniowy.](../../media/line-chart-a.png)
 *Wykres liniowy przedstawiający liczbę zdarzeń dotyczących pliku w czasie*


## <a name="export-tables-and-charts"></a>Eksportowanie tabel i wykresów
Po uruchomieniu zapytania wybierz pozycję **Eksportuj** , aby zapisać wyniki w pliku lokalnym. Wybrany widok określa sposób eksportowania wyników:

- **Widok tabeli** — wyniki zapytania są eksportowane w postaci tabelarowej jako Microsoft Excel skoroszycie
- **Dowolny wykres** — wyniki zapytania są eksportowane jako obraz JPEG renderowanego wykresu

## <a name="drill-down-from-query-results"></a>Przechodzenie do szczegółów w wynikach zapytania
Aby szybko sprawdzić rekord w wynikach zapytania, wybierz odpowiedni wiersz w celu otwarcia **panelu inspekcji** rekordów. Na podstawie wybranego rekordu panel udostępnia następujące informacje:

- **Składniki** majątku — podsumowanie głównych zasobów (skrzynek pocztowych, urządzeń i użytkowników) znalezionych w rekordzie, wzbogacanych o dostępne informacje, takie jak poziomy ryzyka i poziomu ekspozycji
- **Wszystkie szczegóły** — wszystkie wartości z kolumn w rekordzie  

![Obraz zaznaczonego rekordu z panelem inspekcji rekordu.](../../media/results-inspect-record.png)

Aby wyświetlić więcej informacji o określonej encji w wynikach zapytania, takiej jak komputer, plik, użytkownik, adres IP lub adres URL, wybierz identyfikator jednostki, aby otworzyć szczegółową stronę profilu dla tej jednostki.

## <a name="tweak-your-queries-from-the-results"></a>Poprawianie zapytań z wyników
Wybierz trzy kropki z prawej strony dowolnej kolumny w **panelu Inspekcja** rekordów. Za pomocą tych opcji można:

- Jawnie poszukaj wybranej wartości (`==`)
- Wykluczenie zaznaczonej wartości z zapytania (`!=`)
- Uzyskaj bardziej zaawansowane operatory do dodawania wartości do zapytania, takie jak `contains`, `starts with` i `ends with` 

![Obraz zaawansowanego zestawu wyników wyszukiwania.](../../media/work-with-query-tweak-query.png)



>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)
