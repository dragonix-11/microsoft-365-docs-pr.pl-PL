---
title: Łączenie wyników zapytania z zdarzeniem
description: Łączenie wyników zapytania z zdarzeniem
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
ms.openlocfilehash: 8a1b8e11d16f0bf0d20739af8ff5699eb150c6f7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526694"
---
# <a name="link-query-results-to-an-incident"></a>Łączenie wyników zapytania z zdarzeniem

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Link do funkcji zdarzenia umożliwia dodanie zaawansowanych wyników zapytania wyszukiwania do nowego lub istniejącego zdarzenia w ramach badania. Ta funkcja ułatwia rejestrowanie rekordów z zaawansowanych działań łowiectwo, co pozwala utworzyć bogatszą oś czasu lub kontekst wydarzeń dotyczących zdarzenia. 

## <a name="link-results-to-new-or-existing-incidents"></a>Łączenie wyników z nowymi lub istniejącymi zdarzeniami

1. Na stronie zaawansowanego zapytania wyszukiwania wprowadź zapytanie w dostarczonym polu zapytania, a następnie wybierz pozycję **Uruchom zapytanie** , aby uzyskać wyniki.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Przykład strony **Query** w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/link-to-incident-1.png":::

2. Na stronie Wyniki wybierz zdarzenia lub rekordy związane z nowym lub bieżącym badaniem, nad które pracujesz, a następnie wybierz pozycję **Połącz z zdarzeniem**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Opcja **Link do zdarzenia** karty **Results** w portalu Microsoft 365 Defender w programie" lightbox="../../media/link-to-incident-1b.png":::

3. Znajdź **sekcję Szczegóły alertu** w okienku Łącze do zdarzenia, a  następnie wybierz pozycję Utwórz nowe zdarzenie, aby przekonwertować zdarzenia na alerty i zgrupować je na nowe zdarzenie:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Przykład sekcji **Szczegóły alertu** w okienku **Link do zdarzenia** w portalu Microsoft 365 Defender w programie" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Możesz też **wybrać pozycję Połącz z istniejącym zdarzeniem** , aby dodać wybrane rekordy do istniejącego zdarzenia. Wybierz powiązane zdarzenie z listy rozwijanej istniejących zdarzeń. Możesz również wprowadzić kilka pierwszych znaków nazwy zdarzenia lub identyfikatora, aby znaleźć istniejące zdarzenie. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Przykład sekcji **Szczegóły alertu** w okienku **Link do zdarzenia** w portalu Microsoft 365 Defender w programie":::

4. Aby wybrać jedną z tych opcji, podaj następujące szczegóły, a następnie wybierz pozycję **Dalej**:
      - **Tytuł alertu** — podaj opisowy tytuł wyników, które będą zrozumiałe dla osób odpowiadających na zdarzenia. Stanie się to tytułem alertu.
      - **Ważność** — wybierz ważność obowiązującą dla grupy alertów.
      - **Kategoria** — wybierz odpowiednią kategorię zagrożeń dla alertów.
      - **Opis** — przydaj się opis pogrupowanych alertów.
      - **Zalecane akcje** — zapewnij działania naprawcze.

5. W sekcji **Jednostki, których dotyczy problem** , wybierz główną jednostkę, na która ma wpływ problem. W tej sekcji są wyświetlane tylko odpowiednie jednostki oparte na wynikach zapytania. W naszym przykładzie za pomocą kwerendy można było znaleźć zdarzenia związane z ewentualnym incydentem związanym z wiadomością e-mail, dlatego nadawca jest jednostką, na która ma wpływ. Jeśli na przykład istnieje czterech różnych nadawców, są tworzone cztery alerty połączone z wybranym zdarzeniem.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Przykład podmiotu, u który ma wpływ na projekt w sekcji **Link do zdarzenia** w portalu Microsoft 365 Defender w programie" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. Wybierz pozycję **Dalej**.
1. Przejrzyj szczegóły podane w sekcji **Podsumowanie** .
     :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Przykład strony wyników w sekcji **Link do zdarzenia** w portalu Microsoft 365 Defender w sieci Web" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. Wybierz pozycję **Gotowe**.

## <a name="view-linked-records-in-the-incident"></a>Wyświetlanie połączonych rekordów w zdarzeniu

Możesz wybrać nazwę zdarzenia, aby wyświetlić zdarzenie, z które są połączone zdarzenia.
     :::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Przykład ekranu ze szczegółami zdarzenia na karcie **Summary** w portalu Microsoft 365 Defender główne" lightbox="../../media/link-to-incident-6-incident-pg.png":::

W naszym przykładzie cztery alerty reprezentujące cztery wybrane zdarzenia zostały pomyślnie połączone z nowym zdarzeniem. 

Pełne informacje o zdarzeniu lub zdarzeniach można znaleźć na każdej ze stron alertów w widoku osi czasu (jeśli jest dostępny) i w widoku wyników zapytania.
     :::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Przykład pełnych szczegółów zdarzenia na karcie **Timeline** w portalu Microsoft 365 Defender czasu" lightbox="../../media/link-to-incident-7-alert-story.png":::

Możesz także wybrać zdarzenie, aby otworzyć okienko **inspekcji** rekordu.
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="Przykład inspekcji szczegółów rekordu zdarzenia na karcie **Timeline** w portalu Microsoft 365 Defender czasu" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Filtr dla wydarzeń dodanych przy użyciu zaawansowanego wyszukiwania
Aby sprawdzić, które alerty zostały wygenerowane przez zaawansowane wyszukiwanie, filtruj kolejkę Zdarzenia i kolejkę **alertów według źródła** wykrywania ręcznego.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Przykład ręcznego filtrowania kolejki zdarzeń i alertów na stronie **Filters** w Microsoft 365 Defender sieci Web" lightbox="../../media/link-to-incident-8-filter.png":::
