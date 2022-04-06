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
description: Administratorzy mogą dowiedzieć się więcej o raporcie Wiadomości automatycznie przekazywane na pulpicie nawigacyjnym przepływu poczty w Centrum & zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 4603e7d895c847513a41dc52764070f970a50d15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476384"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Szczegółowe informacje o wiadomościach przesyłanych automatycznie w Centrum & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Szczegółowe **informacje o** automatycznie przesyłanych wiadomościach na [](mail-flow-insights-v2.md) pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi [& Security & zawierają](https://protection.office.com) informacje o wiadomościach, które są automatycznie przekazywane z organizacji do adresatów w domenach zewnętrznych.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="Widżet, który w Centrum zgodności programu & jest & wiadomości przesyłanych dalej" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>Szczegóły wiadomości przesyłanych automatycznie

Po kliknięciu liczby wiadomości w widżecie zostanie wyświetlone okienko wysuwu, które zawiera więcej informacji o wiadomościach automatycznie przesyłanych dalej:

- **Automatyczne przesyłanie dalej wiadomości przy pomocą metod przesyłania dalej**:

  - **Według reguł przepływu poczty e-mail**
  - **Według reguł skrzynki odbiorczej**
  - **Przez przesyłanie dalej SMTP**: Ta metoda oznacza automatyczne przesyłanie dalej, które administratorzy mogą skonfigurować w skrzynce pocztowej zgodnie z opisem w tece Konfigurowanie przesyłania dalej poczty [e-mail dla skrzynki pocztowej](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - Link do raportu [przesyłania dalej, aby](view-mail-flow-reports.md#forwarding-report) uzyskać więcej szczegółowych informacji.

- **Automatyczne przesyłanie dalej wiadomości według domen i użytkowników**:

  - **5 najlepszych domen jest przesyłanych dalej do**
  - **Nowe domeny (w zeszłym tygodniu)**
  - **5 najlepszych użytkowników przesyłających dalej**
  - **Nowi użytkownicy (w zeszłym tygodniu)**
  - Link do raportu [do przesyłania dalej modyfikacji,](mfi-new-users-forwarding-email.md#forwarding-modifications-report) aby uzyskać więcej szczegółowych informacji.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="Widżet wiadomości automatycznie przesyłanych dalej w Centrum & zabezpieczeń" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Szczegółowe informacje

Na podstawie danych raportu są generowane dwie szczegółowe informacje:

- [Nowi użytkownicy przesyłają dalej pocztę e-mail](mfi-new-users-forwarding-email.md)
- [Nowe domeny w wiadomościach e-mail przesyłanych dalej](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).