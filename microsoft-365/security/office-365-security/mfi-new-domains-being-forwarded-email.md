---
title: Szczegółowe informacje o nowych domenach przesyłanych dalej pocztą e-mail
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Administratorzy mogą dowiedzieć się, jak używać szczegółowych informacji o wiadomościach e-mail przesyłanych dalej przez nowe domeny na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności & zabezpieczeń w celu zbadania, kiedy ich użytkownicy przekazują wiadomości do domen zewnętrznych, do których nigdy nie przekazano dalej.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 1dbcf83d234611af1d209d83191cee24f5bee579
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974350"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Nowe domeny przesyłane dalej za pomocą wiadomości e-mail w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Istnieją ważne powody biznesowe, aby przekazywać wiadomości e-mail do adresatów zewnętrznych w określonych domenach. Jest to jednak podejrzane, gdy użytkownicy w organizacji nagle zaczynają przekazywać komunikaty do domeny, do której nikt w organizacji nigdy nie przekazywał komunikatów do (nowej domeny).

Ten warunek może wskazywać, że konta użytkowników zostały naruszone. Jeśli podejrzewasz, że konta zostały naruszone, zobacz [Odpowiadanie na naruszone konto e-mail](responding-to-a-compromised-email-account.md).

Usługa **New domains being forwarded email** insight in the [Security & Compliance Center](https://protection.office.com) powiadamia, gdy użytkownicy w organizacji przekazują komunikaty do nowych domen.

Ta analiza jest wyświetlana tylko wtedy, gdy problem zostanie wykryty i zostanie wyświetlony na stronie [raportu przesyłania dalej](view-mail-flow-reports.md#forwarding-report) .

:::image type="content" source="../../media/mfi-new-domains-being-forwarded.png" alt-text="Nowe domeny przesyłane dalej — szczegółowe informacje o wiadomościach e-mail" lightbox="../../media/mfi-new-domains-being-forwarded.png":::

Po kliknięciu widżetu zostanie wyświetlone okno wysuwane, w którym można znaleźć więcej szczegółów na temat przekazywanych komunikatów, w tym link z powrotem do [raportu przesyłania dalej](view-mail-flow-reports.md#forwarding-report).

:::image type="content" source="../../media/mfi-new-domains-being-forwarded-details.png" alt-text="Okno wysuwane Szczegóły, które zostanie wyświetlone po kliknięciu pozycji Nowe domeny, do których jest przekazywana wiadomość e-mail" lightbox="../../media/mfi-new-domains-being-forwarded-details.png":::

Możesz również przejść do tej strony szczegółów po wybraniu szczegółowych informacji po kliknięciu pozycji **Wyświetl wszystko** w obszarze **Najważniejsze szczegółowe informacje & rekomendacji** na stronie (**Pulpit nawigacyjny raportów** \> lub  <https://protection.office.com/insightdashboard>).

Aby zapobiec automatycznemu przekazywaniu komunikatów do domen zewnętrznych, skonfiguruj domenę zdalną dla niektórych lub wszystkich domen zewnętrznych. Aby uzyskać więcej informacji, zobacz [Zarządzanie domenami zdalnymi w Exchange Online](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać informacje o innych szczegółowych informacjach na pulpicie nawigacyjnym przepływu poczty, zobacz [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](mail-flow-insights-v2.md).
