---
title: Raport o braku dostarczania na pulpicie nawigacyjnym przepływu poczty
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
description: Administratorzy mogą dowiedzieć się, jak używać raportu o braku dostarczania szczegółów na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi Security &, aby monitorować najczęściej spotykane kody błędów w raportach o braku dostarczania (nazywanych również żądaniami NDR lub komunikatami odbić) od nadawców w organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 663e145bcf9d6dc95f0f71b3b0b50a78419ed989
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973514"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Raport o braku dostarczania w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Raport o braku dostarczania** na [pulpicie nawigacyjnym przepływu poczty](mail-flow-insights-v2.md) w [Centrum zgodności usługi Security &](https://protection.office.com) pokazuje najbardziej napotkane kody błędów w raportach o braku dostarczania (znanych również jako żądania NDR lub komunikaty bounce) dla użytkowników w organizacji. Ten raport zawiera szczegółowe informacje o serwerach NDR, dzięki czemu można rozwiązywać problemy z dostarczaniem wiadomości e-mail.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="Widżet raportu o braku dostarczania na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>Widok raportu dla raportu o braku dostarczania

Kliknięcie widżetu **raportów o braku dostarczania** spowoduje, że przejdziesz do **raportu o braku dostarczania**.

Domyślnie wyświetlane jest działanie dla wszystkich kodów błędów. Jeśli klikniesz pozycję **Pokaż dane,** możesz wybrać określony kod błędu z listy rozwijanej.

Jeśli umieścisz kursor na określonym kolorze (kod błędu) w określonym dniu na wykresie, zobaczysz całkowitą liczbę komunikatów o błędzie.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="Widok Raport w raporcie nieakceptowano domeny" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>Widok tabeli szczegółów raportu o braku dostarczania

Jeśli klikniesz **pozycję Wyświetl tabelę szczegółów** w widoku raportu, wyświetlane są następujące informacje:

- **Data**
- **Kod raportu bez dostarczania**
- **Liczba**
- **Przykładowe komunikaty**: identyfikatory komunikatów przykładowych komunikatów, których dotyczy problem.

Jeśli klikniesz pozycję **Filtry** w widoku tabeli szczegółów, możesz określić zakres dat z **datą rozpoczęcia** i **datą zakończenia**.

Aby wysłać raport pocztą e-mail dla określonego zakresu dat do co najmniej jednego adresata, kliknij pozycję **Zażądaj pobrania**.

Po wybraniu wiersza w tabeli zostanie wyświetlone okno wysuwane z następującymi informacjami:

- **Data**
- **Kod raportu bez dostarczania**: możesz kliknąć link, aby znaleźć więcej informacji o przyczynach i rozwiązaniach dla określonego kodu błędu.
- **Liczba**
- **Przykładowe komunikaty**: możesz kliknąć pozycję **Wyświetl przykładowe komunikaty** , aby wyświetlić wyniki [śledzenia komunikatów](message-trace-scc.md) dla przykładu komunikatów, których dotyczy problem.

:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="Wysuwane szczegóły po wybraniu wiersza w widoku tabeli Szczegóły w raporcie o braku dostarczania" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać informacje o innych szczegółowych informacjach na pulpicie nawigacyjnym przepływu poczty, zobacz [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](mail-flow-insights-v2.md).
