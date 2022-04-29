---
title: Szczegółowe informacje o wiadomościach przesyłanych automatycznie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Administratorzy mogą dowiedzieć się więcej o raporcie wiadomości przesyłanych automatycznie na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności & zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2f102f4fbea558f0972fbd4f3e8f4a4bea257bf4
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131047"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Szczegółowe informacje o komunikatach przesyłanych automatycznie w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Szczegółowe informacje o **automatycznym przekazywaniu wiadomości** na [pulpicie nawigacyjnym przepływu poczty](mail-flow-insights-v2.md) w [Centrum zgodności usługi Security &](https://protection.office.com) wyświetla informacje o komunikatach, które są automatycznie przekazywane z organizacji do adresatów w domenach zewnętrznych.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="Widżet, czyli komunikaty przesyłane automatycznie w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>Szczegóły komunikatów przesyłanych automatycznie

Po kliknięciu liczby komunikatów w widżecie zostanie wyświetlone okienko wysuwane, w którym zostaną wyświetlone dodatkowe informacje o komunikatach przesyłanych automatycznie:

- **Komunikaty przesyłane automatycznie przez metody przekazywania dalej**:

  - **Według reguł przepływu poczty**
  - **Według reguł skrzynki odbiorczej**
  - **Przekazywanie za pomocą protokołu SMTP**: ta metoda wskazuje automatyczne przekazywanie, które administratorzy mogą skonfigurować w skrzynce pocztowej zgodnie z [opisem w artykule Konfigurowanie przekazywania wiadomości e-mail dla skrzynki pocztowej](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - Link do [raportu przesyłania dalej](view-mail-flow-reports.md#forwarding-report) , aby uzyskać więcej szczegółów.

- **Komunikaty przesyłane automatycznie przez domeny i użytkowników**:

  - **5 najważniejszych domen przekazanych do**
  - **Nowe domeny (ostatni tydzień)**
  - **5 najlepszych użytkowników przekazujących**
  - **Nowi użytkownicy (ostatni tydzień)**
  - Link do [raportu modyfikacji przesyłania dalej](mfi-new-users-forwarding-email.md#forwarding-modifications-report) , aby uzyskać więcej szczegółów.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="Widżet komunikatów automatycznie przesyłanych dalej w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Szczegółowe informacje

Na podstawie danych raportu są generowane dwa szczegółowe informacje:

- [Nowi użytkownicy przekazujący wiadomości e-mail](mfi-new-users-forwarding-email.md)
- [Nowe domeny przesyłane dalej pocztą e-mail](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Zobacz też

Aby uzyskać informacje o innych szczegółowych informacjach na pulpicie nawigacyjnym przepływu poczty, zobacz [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](mail-flow-insights-v2.md).
