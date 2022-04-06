---
title: Raport nie zaakceptowanych domen na pulpicie nawigacyjnym przepływu poczty e-mail
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak używać raportu Nie zaakceptowane domeny na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi Security & w celu monitorowania wiadomości od lokalnej organizacji, w której domena nadawcy nie została skonfigurowana w programie Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 25a8b1adb882aa83861e936d48534fc0a5f826e4
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679681"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Raport o nie zaakceptowanych domenach w Centrum & zabezpieczeń i zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Raport Nie** zaakceptowane domeny na pulpicie [](mail-flow-insights-v2.md) nawigacyjnym przepływu poczty w Centrum zgodności zabezpieczeń [&](https://protection.office.com) wyświetla informacje o wiadomościach od lokalnej organizacji poczty e-mail, w przypadku których domena nadawcy nie jest skonfigurowana jako zaakceptowana domena w Twojej Microsoft 365 organizacji.

Microsoft 365 tych wiadomości mogą zostać ograniczone, jeśli mamy dane, które udowadniają, że celem tych wiadomości jest złośliwy. Dlatego ważne jest zrozumienie, co się dzieje, i rozwiązanie problemu.

![Nie zaakceptowany widżet domeny na pulpicie nawigacyjnym przepływu poczty w Centrum & zgodności.](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a>Widok raportu dla raportu o niedo zaakceptowanych domenach

Kliknięcie wykresu na **widżecie Nie zaakceptowana** domena spowoduje kliknięcie raportu **o niedo zaakceptowanych domenach** .

Domyślnie jest wyświetlana aktywność dla wszystkich łączników, których dotyczy problem. Jeśli klikniesz **pozycję Pokaż dane** dla, możesz wybrać konkretny łącznik z listy rozwijanej.

Umieszczenie wskaźnika myszy nad punktem danych (dniem) na wykresie pozwala wyświetlić łączną liczbę wiadomości łącznika.

![Widok raportu w raporcie o niedotrzymanych domenach.](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Widok tabeli Szczegóły raportu o niedo zaakceptowanych domenach

Kliknięcie **przycisku Wyświetl tabelę szczegółów** w widoku raportu umożliwia wyświetlenie następujących informacji:

- **Data**
- **Nazwa łącznika ruchu przychodzącego**
- **Domena nadawcy**
- **Liczba wiadomości**
- **Przykładowe wiadomości**: Identyfikatory wiadomości przykładowych wiadomości, których dotyczy problem.

Jeśli klikniesz **pozycję Filtry** w widoku tabeli szczegółów, możesz określić zakres dat z **datami rozpoczęcia** i **datami zakończenia**.

Aby wysłać raport pocztą e-mail z określonym zakresem dat do jednego lub większej liczby adresatów, kliknij pozycję **Poproś o pobranie**.

Po zaznaczeniu wiersza w tabeli zostanie wyświetlone wysuwne okno z następującymi informacjami:

- **Data**
- **Nazwa łącznika ruchu przychodzącego**
- **Domena nadawcy**
- **Liczba wiadomości**
- **Przykładowe wiadomości**: Możesz kliknąć pozycję **Wyświetl przykładowe wiadomości**, [](message-trace-scc.md) aby wyświetlić wyniki śledzenia wiadomości dla przykładowych wiadomości, których dotyczy problem.

![Wysuw szczegółów po zaznaczeniu wiersza w widoku tabeli Szczegóły w raporcie Nie zaakceptowana domena.](../../media/mfi-non-accepted-domain-report-details-flyout.png)

Aby wrócić do widoku raportów, kliknij pozycję **Wyświetl raport**.

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
