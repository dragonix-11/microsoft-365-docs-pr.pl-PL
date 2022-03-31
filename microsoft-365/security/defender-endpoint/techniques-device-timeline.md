---
title: Techniki na osi czasu urządzenia
description: Opis osi czasu urządzenia w aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: Oś czasu urządzenia, punkt końcowy, MITRE, MITRE ATT&CK, techniki, taktyka
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
ms.openlocfilehash: d724b7663bd4484c630e97362eb5766490e1fa8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465910"
---
# <a name="techniques-in-the-device-timeline"></a>Techniki na osi czasu urządzenia

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Możesz uzyskać więcej informacji w analizie zdarzeń, które wydarzyły się na określonym urządzeniu. Najpierw wybierz interesujące urządzenie z [listy Urządzenia](machines-view-overview.md). Na stronie urządzenia możesz wybrać kartę Oś czasu, aby wyświetlić wszystkie zdarzenia, które wystąpiły na urządzeniu.

## <a name="understand-techniques-in-the-timeline"></a>Opis technik na osi czasu

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie dzierżawionych funkcji produktu w publicznej wersji zapoznawczej, która może zostać znacznie zmodyfikowana przed jej komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

W Ochrona punktu końcowego w usłudze Microsoft Defender **techniki to** dodatkowy typ danych na osi czasu zdarzenia. Techniki zapewniają więcej informacji na temat działań związanych z technikami [MITRE ATT&technikami CK](https://attack.mitre.org/) lub podsektami.

Ta funkcja upraszcza środowisko badania, pomagając analitykom w zrozumieniu działań obserwowanych na urządzeniu. Analitycy mogą następnie podjąć decyzję o dalszym zbadaniu.

W przypadku podglądu publicznego techniki są domyślnie dostępne i wyświetlane razem ze zdarzeniami, gdy jest wyświetlana oś czasu urządzenia.

:::image type="content" source="images/device-timeline-2.png" alt-text="Techniki na osi czasu urządzenia" lightbox="images/device-timeline-2.png":::

Techniki są wyróżniane pogrubionym tekstem i wyświetlane z niebieską ikoną po lewej stronie. Odpowiadająca mu nazwa&ATT MITRE jest wyświetlana jako tagi w obszarze Informacje dodatkowe.

Opcje wyszukiwania i eksportowania są również dostępne w przypadku technik.

## <a name="investigate-using-the-side-pane"></a>Badanie za pomocą okienka bocznego

Wybierz technikę, aby otworzyć odpowiednie okienko boczne. Tutaj możesz zobaczyć dodatkowe informacje i szczegółowe informacje, takie jak powiązane techniki ATT&CK, taktyki i opisy.

Wybierz określoną *technikę ataków,* aby otworzyć powiązaną technikę ATT&CK, gdzie możesz znaleźć więcej informacji na jej temat.

Możesz skopiować szczegóły encji, gdy zobaczysz niebieską ikonę po prawej stronie. Aby na przykład skopiować plik pokrewny SHA1, wybierz niebieską ikonę strony.

:::image type="content" source="images/techniques-side-pane-clickable.png" alt-text="Szczegóły jednostki do skopiowania" lightbox="images/techniques-side-pane-clickable.png":::

W przypadku wierszy poleceń można wykonać to samo.

:::image type="content" source="images/techniques-side-pane-command.png" alt-text="Opcja kopiowania wiersza polecenia" lightbox="images/techniques-side-pane-command.png":::

## <a name="investigate-related-events"></a>Badanie zdarzeń pokrewnych

Aby użyć [zaawansowanego wyszukiwania](advanced-hunting-overview.md) w celu znalezienia wydarzeń związanych z wybraną techniką, wybierz pozycję **Znajdź powiązane zdarzenia**. Prowadzi to do zaawansowanej strony wyszukiwania z zapytaniem w celu znalezienia wydarzeń związanych z techniką.

:::image type="content" source="images/techniques-hunt-for-related-events.png" alt-text="Opcja Hunt for related events (Zaszukaj powiązane zdarzenia)" lightbox="images/techniques-hunt-for-related-events.png":::

> [!NOTE]
> Zapytanie za pomocą **przycisku Wyszukiwania pokrewnych** zdarzeń z okienka bocznego Technika powoduje wyświetlenie wszystkich zdarzeń związanych z wskazaną techniką, ale nie uwzględnia samej techniki w wynikach zapytania.

## <a name="customize-your-device-timeline"></a>Dostosowywanie osi czasu urządzenia

W prawej górnej części osi czasu urządzenia możesz wybrać zakres dat, aby ograniczyć liczbę zdarzeń i technik na osi czasu.

Możesz określić, które kolumny mają być wyświetlane. Możesz również filtrować w celu wyszukiwania oflagowanych zdarzeń według typu danych lub grupy zdarzeń.

### <a name="choose-columns-to-expose"></a>Wybieranie kolumn do udostępnienia

Możesz wybrać kolumny do udostępnienia na osi czasu, wybierając **przycisk Wybierz kolumny** .

:::image type="content" source="images/filter-customize-columns.png" alt-text="Okienko, w którym można dostosowywać kolumny" lightbox="images/filter-customize-columns.png":::


W tym miejscu możesz wybrać, które informacje mają być zawarte.

### <a name="filter-to-view-techniques-or-events-only"></a>Filtrowanie w celu wyświetlenia tylko technik lub zdarzeń

Aby wyświetlić tylko zdarzenia lub techniki, wybierz **pozycję Filtry na** osi czasu urządzenia i wybierz preferowany typ danych do wyświetlenia.

:::image type="content" source="images/device-timeline-filters.png" alt-text="Okienko Filtry" lightbox="images/device-timeline-filters.png":::

## <a name="see-also"></a>Zobacz też

- [Wyświetlanie i organizowanie listy Urządzenia](machines-view-overview.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender flag zdarzeń osi czasu urządzenia](device-timeline-event-flag.md)
