---
title: Szczegółowe informacje o nowych domenach w wiadomościach e-mail przesyłanych dalej
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Administratorzy mogą dowiedzieć się, jak za pomocą szczegółowych informacji o nowych domenach przesyłanych dalej wiadomości e-mail na pulpicie nawigacyjnym przepływu poczty w Centrum zabezpieczeń & zgodności zbadać, kiedy ich użytkownicy przesyłają dalej wiadomości do domen zewnętrznych, które nigdy nie zostały przekazane dalej.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e23d63a519bf69f94ce4990d8851d673826dcb5c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475086"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Informacje o nowych domenach przesyłanych dalej w Centrum & zabezpieczeń i zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Istnieją ważne powody biznesowe, dla których wiadomości e-mail mogą być przesyłane dalej do adresatów zewnętrznych w określonych domenach. Jest to jednak podejrzane, gdy użytkownicy w Twojej organizacji nagle zaczną przesyłać dalej wiadomości do domeny, do której żadna z osób w organizacji nie przesyłała dalej wiadomości (do nowej domeny).

Ten warunek może wskazywać, że konta użytkowników zostały naruszone. Jeśli podejrzewasz, że konta zostały naruszone, zobacz Odpowiadanie na [naruszone konto e-mail](responding-to-a-compromised-email-account.md).

Szczegółowe **informacje o nowych domenach** w Centrum [&](https://protection.office.com) zabezpieczeń i zgodności powiadomią Cię, gdy użytkownicy w Twojej organizacji będą przesyłać dalej wiadomości do nowych domen.

Ta informacja jest widoczna tylko po wykryciu problemu i pojawia się na stronie [Raport przesyłany](view-mail-flow-reports.md#forwarding-report) dalej.

:::image type="content" source="../../media/mfi-new-domains-being-forwarded.png" alt-text="Szczegółowe informacje o nowych domenach w wiadomościach e-mail przesyłanych dalej" lightbox="../../media/mfi-new-domains-being-forwarded.png":::


Po kliknięciu widżetu zostanie wyświetlone wysuwne okno, w którym można znaleźć więcej szczegółowych informacji na temat wiadomości przesyłanych dalej, w tym link do raportu [przesyłania dalej](view-mail-flow-reports.md#forwarding-report).

:::image type="content" source="../../media/mfi-new-domains-being-forwarded-details.png" alt-text="Wysuw szczegółów wyświetlany po kliknięciu szczegółowych informacji o nowych domenach przesyłanych dalej wiadomości e-mail" lightbox="../../media/mfi-new-domains-being-forwarded-details.png":::

Możesz również przejść do tej strony szczegółów, gdy wybierzesz szczegółowe informacje po kliknięciu przycisku Wyświetl wszystkie w obszarze Najważniejsze informacje **& zalecenia** na (**Pulpit** \> nawigacyjny **Raporty** lub <https://protection.office.com/insightdashboard>).

Aby zapobiec automatycznemu przesyłaniu wiadomości do domen zewnętrznych, skonfiguruj domenę zdalną dla niektórych lub wszystkich domen zewnętrznych. Aby uzyskać więcej informacji, zobacz [Zarządzanie domenami zdalnymi w Exchange Online](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).