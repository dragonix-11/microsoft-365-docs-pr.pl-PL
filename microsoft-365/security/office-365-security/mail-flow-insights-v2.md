---
title: Szczegółowe informacje o przepływie poczty na pulpicie nawigacyjnym przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: Administratorzy mogą poznać szczegółowe informacje i raporty dostępne na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi Security &.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: eef35eedd5a7f182160b9a6a8b27a59cf9cdd9c0
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129183"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Szczegółowe informacje o przepływie poczty e-mail w Centrum zabezpieczeń i zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorzy mogą używać pulpitu nawigacyjnego przepływu poczty w Centrum zgodności usługi Security &, aby odnajdywać trendy, szczegółowe informacje i podejmować działania w celu rozwiązania problemów związanych z przepływem poczty w organizacji.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="Pulpit nawigacyjny przepływu poczty w Centrum zgodności & zabezpieczeń" lightbox="../../media/mail-flow-dashboard-v2.png":::

Dostępne szczegółowe informacje to:

- [Szczegółowe informacje o wiadomościach przesyłanych automatycznie](mfi-auto-forwarded-messages-report.md)

- [Rozwiązywanie problemów z możliwą analizą pętli poczty1](mfi-mail-loop-insight.md)<sup></sup>

- [Rozwiązywanie problemów z powolnym przepływem poczty — szczegółowe informacje1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [Mapa przepływu poczty e-mail](mfi-mail-flow-map-report.md)

- [Nowe domeny przesyłane dalej — szczegółowe informacje e-mail2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [Nowi użytkownicy przekazujący szczegółowe informacje e-mail2](mfi-new-users-forwarding-email.md)<sup></sup>

- [Raport o nie zaakceptowanej domenie](mfi-non-accepted-domain-report.md)

- [Raport o niedostarczeniu](mfi-non-delivery-report.md)

- [Szczegółowe informacje o przepływie poczty wychodzącej i przychodzącej](mfi-outbound-and-inbound-mail-flow.md)

- [Szczegółowe informacje o kolejkach](mfi-queue-alerts-and-queues.md)

- [Szczegółowe informacje i raport klientów uwierzytelniania SMTP](mfi-smtp-auth-clients-report.md)

- [Szczegółowe informacje o stanie przepływu poczty e-mail w domenie](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Ten wgląd jest wyświetlany w obszarze **Zalecane dla Ciebie** na pulpicie nawigacyjnym przepływu poczty dopiero po wykryciu problemu. W przeciwnym razie go nie zobaczysz.

<sup>2</sup> Ta analiza nie jest wyświetlana na pulpicie nawigacyjnym przepływu poczty, ale jest widoczna na stronie [raportów przesyłania dalej](view-mail-flow-reports.md#forwarding-report) po wykryciu problemu. W przeciwnym razie go nie zobaczysz.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Uprawnienia wymagane do wyświetlania pulpitu nawigacyjnego przepływu poczty

Pulpit nawigacyjny przepływu poczty jest dostępny dla członków następujących grup ról:

- **Zarządzanie organizacją** w Centrum zgodności & zabezpieczeń (administratorzy globalni).

- **[administrator Exchange](/azure/active-directory/roles/permissions-reference#exchange-administrator)** w Azure Active Directory.

- **Administrator usługi MailFlow** w Centrum zgodności & zabezpieczeń. Jeśli konto nie jest również członkiem grup ról Zarządzanie organizacją lub administrator Exchange, rozważ następujące problemy:
  - Użytkownik musi zalogować się do Centrum zgodności & zabezpieczeń bezpośrednio pod adresem <https://protection.office.com>.
  - Użytkownik będzie miał uprawnienia tylko do odczytu do pulpitu nawigacyjnego przepływu poczty.
  - Użytkownik nie będzie miał dostępu do Centrum administracyjne platformy Microsoft 365.

Aby uzyskać więcej informacji na temat uprawnień, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](permissions-in-the-security-and-compliance-center.md) i [Przyznaj użytkownikom dostęp do Centrum zgodności & zabezpieczeń](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Gdzie znaleźć pulpit nawigacyjny przepływu poczty

Otwórz Centrum zgodności & zabezpieczeń pod adresem <https://protection.office.com>, rozwiń węzeł **Przepływ poczty**, a następnie wybierz pozycję **Pulpit nawigacyjny**.

Aby przejść bezpośrednio do pulpitu nawigacyjnego przepływu poczty, otwórz pozycję <https://protection.office.com/mailflow/dashboard>.
