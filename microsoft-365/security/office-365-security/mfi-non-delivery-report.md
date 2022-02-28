---
title: Raport o niedo dostarczenia na pulpicie nawigacyjnym przepływu poczty
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
description: Administratorzy mogą dowiedzieć się, jak za pomocą raportu Szczegóły niedo dostarczenia na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi & Security & monitorować najczęściej napotkane kody błędów w raportach o niedo dostarczeniu (nazywanych również raportami o niedo dostarczenia lub wiadomościach zwracanych) od nadawców w organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 00efa42dbe9f3ca119d407c74d3711d99d6c0d5c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983299"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Raport o niedo dostarczenia w Centrum & zgodności z zabezpieczeniami

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Raport o **niedo** dostarczenia na pulpicie [](mail-flow-insights-v2.md) nawigacyjnym przepływu poczty w Centrum zgodności usługi [&](https://protection.office.com) zabezpieczeń zawiera informacje o najczęściej występujących kodach błędów w raportach o niedo dostarczenia (nazywanych również raportami o niedo dostarczenia lub wiadomościach zwracanych) dla użytkowników w organizacji. Ten raport zawiera szczegółowe informacje o raportach o stanie dostarczenia, co umożliwia rozwiązywanie problemów z dostarczaniem wiadomości e-mail.

![Widżet raportu o niedo dostarczenia na pulpicie nawigacyjnym przepływu poczty w Centrum & zgodności.](../../media/mfi-non-delivery-report-widget.png)

## <a name="report-view-for-the-non-delivery-report"></a>Widok raportu o niedo dostarczenia

Kliknięcie **widżetu Raportu o niedo dostarczenia** spowoduje kliknięcie raportu **o niedo dostarczenia**.

Domyślnie jest wyświetlane działanie dla wszystkich kodów błędów. Jeśli klikniesz **pozycję Pokaż dane** dla, możesz wybrać określony kod błędu z listy rozwijanej.

Jeśli najedziesz kursorem na określony kolor (kod błędu) określonego dnia na wykresie, zobaczysz łączną liczbę komunikatów o błędzie.

![Widok raportu w raporcie o niedotrzymanych domenach.](../../media/mfi-non-delivery-report-overview-view.png)

## <a name="details-table-view-for-the-non-delivery-report"></a>Widok tabeli Szczegóły dla raportu o niedo dostarczenia

Kliknięcie **przycisku Wyświetl tabelę szczegółów** w widoku raportu umożliwia wyświetlenie następujących informacji:

- **Data**
- **Kod raportu o niedo dostarczenia**
- **Liczba**
- **Przykładowe wiadomości**: Identyfikatory wiadomości przykładowych wiadomości, których dotyczy problem.

Jeśli klikniesz **pozycję Filtry** w widoku tabeli szczegółów, możesz określić zakres dat z **datami rozpoczęcia** i **datami zakończenia**.

Aby wysłać raport pocztą e-mail z określonym zakresem dat do jednego lub większej liczby adresatów, kliknij pozycję **Poproś o pobranie**.

Po zaznaczeniu wiersza w tabeli zostanie wyświetlone wysuwne okno z następującymi informacjami:

- **Data**
- **Kod raportu o niedo dostarczenia**: Możesz kliknąć link, aby znaleźć więcej informacji o przyczynach i rozwiązaniach konkretnego kodu błędu.
- **Liczba**
- **Przykładowe wiadomości**: Możesz kliknąć pozycję **Wyświetl przykładowe wiadomości**, [](message-trace-scc.md) aby wyświetlić wyniki śledzenia wiadomości dla przykładowych wiadomości, których dotyczy problem.

![Wysuw szczegółów po wybraniu wiersza w widoku tabeli Szczegóły w raporcie O niedo dostarczenia.](../../media/mfi-non-delivery-report-details-flyout.png)

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
