---
title: Mapa przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak za pomocą mapy przepływu poczty na pulpicie nawigacyjnym przepływu poczty e-mail w Centrum zgodności usługi & Security & wizualizować i śledzić przepływy poczty e-mail z organizacji przez łączniki i bez użycia łączników.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 725489dc92fc43edab13c291129ed78c3ca7915e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998952"
---
# <a name="mail-flow-map-in-the-security--compliance-center"></a>Mapa przepływu poczty e-mail w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Mapa **przepływu poczty na** pulpicie [nawigacyjnym](mail-flow-insights-v2.md) przepływu poczty w Centrum [&](https://protection.office.com) zabezpieczeń pozwala uzyskać szczegółowe informacje na temat przepływów poczty przez Twoją organizację. Za pomocą tych informacji można identyfikować wzorce, identyfikować anomalie i rozsyłać problemy w ich przypadku.

![Widżet mapy przepływu poczty e-mail na pulpicie nawigacyjnym przepływu poczty w Centrum & zgodności.](../../media/mfi-mail-flow-map-widget.png)

Domyślnie na wykresie nazywanym diagramem *Sankey* widżet pokazuje wzorzec przepływu poczty e-mail z poprzedniego dnia. Możesz użyć strzałki w lewo w ![lewo.](../../media/scc-left-arrow.png) i strzałka w prawo ![Strzałka w prawo](../../media/scc-right-arrow.png) , aby wyświetlić informacje z różnych dni. Każdy inny kolor reprezentuje przepływ poczty na innym łączniku ruchu przychodzącego lub wychodzącego (lub bez użycia łączników). Po umieszczeniu wskaźnika myszy na określonym kolorze zostanie wyświetlona liczba wiadomości dla tego typu łącznika.

## <a name="report-view-for-the-mail-flow-map"></a>Widok raportu dla mapy przepływu poczty

Kliknięcie widżetu **Mapa przepływu poczty** spowoduje kliknięcie raportu Mapy **przepływu poczty e-mail** .

W widoku raportu są dostępne następujące wykresy:

- **Pokaż dane dla: Omówienie**: to po prostu większy widok widżetu. Po umieszczeniu wskaźnika myszy na określonym kolorze zostanie wyświetlona liczba wiadomości dla tego typu łącznika.

  ![Widok Przegląd w raporcie Mapa przepływu poczty e-mail.](../../media/mfi-mail-flow-map-report-overview.png)

- **Pokaż dane dla: Szczegóły:** Ten widok zawiera szczegółowe informacje o łącznikach i domenach docelowych. Zostaną wyświetlone domeny nadawcy i adresata, a pozostałe zostaną wyświetlone w obszarze **Inne**. Po umieszczeniu wskaźnika myszy na określonym kolorze i sekcji zostanie wyświetlona liczba wiadomości.

  ![Widok szczegółowy w raporcie mapa przepływu poczty e-mail.](../../media/mfi-mail-flow-map-report-detail.png)

Jeśli klikniesz **pozycję Filtry** w widoku raportu, możesz określić zakres dat w **datach Rozpoczęcie** i **Data zakończenia**.

Aby wysłać raport pocztą e-mail z określonym zakresem dat do jednego lub większej liczby adresatów, kliknij pozycję **Poproś o pobranie**.

Powiązane informacje są wyświetlane poniżej mapy przepływu poczty e-mail, jeśli są dostępne (na przykład informacje Naprawianie możliwej pętli [poczty](mfi-mail-loop-insight.md).

## <a name="details-table-view-for-the-mail-flow-map"></a>Widok tabeli Szczegóły dla mapy przepływu poczty e-mail

Kliknięcie **przycisku Wyświetl tabelę szczegółów** w widoku raportu umożliwia wyświetlenie następujących informacji:

- **Data**
- **Kategoria**
- **Łącznik / Zewnętrzne usługodawca**
- **Domena nadawcy/adresata**
- **Liczba wiadomości**

Jeśli klikniesz **pozycję Filtry** w widoku tabeli szczegółów, możesz określić zakres dat z **datami rozpoczęcia** i **datami zakończenia**.

Jeśli zaznaczysz wiersz, podobne szczegóły zostaną wyświetlone w wysuwanych informacjach:

![Wysuw szczegółów z tabeli szczegółów na mapie przepływu poczty.](../../media/mfi-mail-flow-map-view-details-table-details.png)

Aby wysłać raport pocztą e-mail z określonym zakresem dat do jednego lub większej liczby adresatów, kliknij pozycję **Poproś o pobranie**.

Aby wrócić do widoku raportów, kliknij pozycję **Wyświetl raport**.

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
