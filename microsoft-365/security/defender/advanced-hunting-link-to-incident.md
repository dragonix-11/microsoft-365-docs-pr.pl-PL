---
title: Łączenie wyników zapytań ze zdarzeniami
description: Łączenie wyników zapytań ze zdarzeniami
keywords: zaawansowane wyszukiwania, zdarzenia, przestaw, jednostki, idź szukać, odpowiednie wydarzenia, szukanie zagrożeń, szukanie przed cyberzagrożeniami, wyszukiwanie, zapytanie, telemetria, Microsoft 365, Microsoft 365 Defender
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
ms.openlocfilehash: c81b0b0850686242c675629cf99fa2c4b3a18496
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755487"
---
# <a name="link-query-results-to-an-incident"></a>Łączenie wyników zapytań ze zdarzeniami

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Możesz użyć linku do funkcji zdarzenia, aby dodać zaawansowane wyniki zapytania wyszukiwania do nowego lub istniejącego zdarzenia, które jest w trakcie badania. Ta funkcja ułatwia rejestrowanie rekordów z zaawansowanych działań chowania, co pozwala na utworzenie bogatszej osi czasu lub kontekstu wydarzeń dotyczących zdarzenia. 

## <a name="link-results-to-new-or-existing-incidents"></a>Łączenie wyników z nowymi lub istniejącymi zdarzeniami

1. Na stronie zaawansowanego zapytania wyszukiwania wprowadź zapytanie w dostarczonym polu zapytania, a następnie wybierz pozycję **Uruchom zapytanie** , aby uzyskać wyniki.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Strona Zapytanie w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/link-to-incident-1.png":::

2. Na stronie Wyniki wybierz zdarzenia lub rekordy związane z nowym lub bieżącym badaniem, nad które pracujesz, a następnie wybierz pozycję **Połącz z zdarzeniem**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Opcja Połącz z incydentem na karcie Wyniki w portalu Microsoft 365 Defender wer." lightbox="../../media/link-to-incident-1b.png":::

3. Znajdź **sekcję Szczegóły alertu** w okienku Łącze do zdarzenia, a  następnie wybierz pozycję Utwórz nowe zdarzenie, aby przekonwertować zdarzenia na alerty i zgrupować je na nowe zdarzenie:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Sekcja Szczegóły alertu w okienku Łącze do zdarzenia w portalu Microsoft 365 Defender wieści" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Możesz też **wybrać pozycję Połącz z istniejącym zdarzeniem** , aby dodać wybrane rekordy do istniejącego zdarzenia. Wybierz powiązane zdarzenie z listy rozwijanej istniejących zdarzeń. Możesz również wprowadzić kilka pierwszych znaków nazwy zdarzenia lub identyfikatora, aby znaleźć istniejące zdarzenie. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Sekcja Szczegóły alertu w portalu Microsoft 365 Defender alertów" lightbox="../../media/link-to-incident-3-link-to-existing.png":::

4. Aby wybrać jedną z tych opcji, podaj następujące szczegóły, a następnie wybierz pozycję **Dalej**:
      - **Tytuł alertu** — podaj opisowy tytuł wyników, które będą zrozumiałe dla osób odpowiadających na zdarzenia. Ten opisowy tytuł stanie się tytułem alertu.
      - **Ważność** — wybierz ważność obowiązującą dla grupy alertów.
      - **Kategoria** — wybierz odpowiednią kategorię zagrożeń dla alertów.
      - **Opis** — przydaj się opis pogrupowanych alertów.
      - **Zalecane akcje** — zapewnij działania naprawcze.

5. W sekcji **Jednostki, których dotyczy problem** , wybierz główną jednostkę, na która ma wpływ problem. W tej sekcji są wyświetlane tylko odpowiednie jednostki oparte na wynikach zapytania. W naszym przykładzie za pomocą kwerendy można było znaleźć zdarzenia związane z ewentualnym incydentem związanym z wiadomością e-mail, dlatego nadawca jest jednostką, na która ma wpływ. Jeśli na przykład istnieje czterech różnych nadawców, są tworzone cztery alerty połączone z wybranym zdarzeniem.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Encja, u związku z która ma wpływ, w sekcji Łącze do zdarzenia w portalu Microsoft 365 Defender wyw." lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. Wybierz pozycję **Dalej**.
1. Przejrzyj szczegóły podane w sekcji **Podsumowanie** .
   :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Strona wyników w sekcji Link do zdarzenia w portalu Microsoft 365 Defender w sieci Web" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. Wybierz pozycję **Gotowe**.

## <a name="view-linked-records-in-the-incident"></a>Wyświetlanie połączonych rekordów w zdarzeniu

Możesz wybrać nazwę zdarzenia, aby wyświetlić zdarzenie, z które są połączone zdarzenia.
:::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Ekran szczegółów zdarzenia na karcie Podsumowanie w portalu z podsumowaniem Microsoft 365 Defender projektu" lightbox="../../media/link-to-incident-6-incident-pg.png":::

W naszym przykładzie cztery alerty reprezentujące cztery wybrane zdarzenia zostały pomyślnie połączone z nowym zdarzeniem. 

Pełne informacje o zdarzeniu lub zdarzeniach można znaleźć na każdej ze stron alertów w widoku osi czasu (jeśli jest dostępny) i w widoku wyników zapytania.
:::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Szczegółowe informacje o zdarzeniu na karcie Oś czasu w portalu Microsoft 365 Defender osi czasu" lightbox="../../media/link-to-incident-7-alert-story.png":::

Możesz także wybrać zdarzenie, aby otworzyć okienko **inspekcji** rekordu.
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="The inspect record details of an event in the Timeline tab in the Microsoft 365 Defender portal" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Filtr dla wydarzeń dodanych przy użyciu zaawansowanego wyszukiwania
Aby sprawdzić, które alerty zostały wygenerowane przez zaawansowane wyszukiwanie, filtruj kolejkę Zdarzenia i kolejkę **alertów według źródła** wykrywania ręcznego.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Ręczne filtrowanie kolejki Zdarzenia i Alerty na stronie Filtry w Microsoft 365 Defender sieci Web" lightbox="../../media/link-to-incident-8-filter.png":::
