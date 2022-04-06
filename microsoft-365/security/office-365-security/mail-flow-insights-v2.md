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
description: Administratorzy mogą dowiedzieć się więcej o szczegółowych informacjach i raportach dostępnych na pulpicie nawigacyjnym przepływu poczty e-mail w Centrum & zabezpieczeń i zgodności.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 176681b5fe780f0aeb4a0c8502b3e919e7ebcadc
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682532"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Szczegółowe informacje o przepływie poczty w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorzy mogą za pomocą pulpitu nawigacyjnego przepływu poczty e-mail w Centrum & zgodności usługi Security & odnajdować trendy i szczegółowe informacje oraz podjąć działania w celu rozwiązania problemów związanych z przepływem poczty e-mail w organizacji.

![Pulpit nawigacyjny przepływu poczty w Centrum & zgodności.](../../media/mail-flow-dashboard-v2.png)

Dostępne informacje:

- [Szczegółowe informacje o wiadomościach przesyłanych automatycznie](mfi-auto-forwarded-messages-report.md)

- [Naprawianie możliwej pętli poczty szczegółowe1](mfi-mail-loop-insight.md)<sup></sup>

- [Rozwiązywanie problemów dotyczących wolnych reguł przepływu poczty e-mail (szczegółowe1](mfi-slow-mail-flow-rules-insight.md)<sup>)</sup>

- [Mapa przepływu poczty](mfi-mail-flow-map-report.md)

- [Informacje o nowych domenach przesyłanych dalej w wiadomościach e-mail2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [Nowi użytkownicy przesyłający dalej informacje o wiadomościach e-mail2](mfi-new-users-forwarding-email.md)<sup></sup>

- [Raport o niedo zaakceptowanych domenach](mfi-non-accepted-domain-report.md)

- [Raport o niedo dostarczenia](mfi-non-delivery-report.md)

- [Szczegółowe informacje o przepływie poczty wychodzącej i przychodzącej](mfi-outbound-and-inbound-mail-flow.md)

- [Szczegółowe informacje o kolejkach](mfi-queue-alerts-and-queues.md)

- [Szczegółowe informacje o klientach i raportach protokołu SMTP Auth](mfi-smtp-auth-clients-report.md)

- [Najważniejsze informacje o stanie przepływu poczty e-mail domeny](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Ta informacja pojawia się w obszarze **Polecane** dla Ciebie na pulpicie nawigacyjnym przepływu poczty tylko po wykryciu problemu. W przeciwnym razie nie będzie on wyświetlony.

<sup>2</sup> Ta informacja nie jest widoczna na pulpicie nawigacyjnym przepływu poczty, ale jest widoczna na stronie Raport przesyłany dalej po wykryciu problemu.[](view-mail-flow-reports.md#forwarding-report) W przeciwnym razie nie będzie on wyświetlony.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Uprawnienia wymagane do wyświetlania pulpitu nawigacyjnego przepływu poczty e-mail

Pulpit nawigacyjny przepływu poczty e-mail jest dostępny dla członków następujących grup ról:

- **Zarządzanie organizacją** w Centrum zabezpieczeń & zgodności (administratorzy globalni).

- **[Exchange administratorem w](/azure/active-directory/roles/permissions-reference#exchange-administrator)** Azure Active Directory.

- **MailFlow Administrator w** Centrum & zgodności. Jeśli to konto nie jest także członkiem grupy ról Zarządzanie organizacją lub administrator Exchange, rozważ następujące problemy:
  - Użytkownik musi zalogować się do Centrum zabezpieczeń & zgodności bezpośrednio na stronie <https://protection.office.com>.
  - Użytkownik będzie miał uprawnienia tylko do odczytu do pulpitu nawigacyjnego przepływu poczty.
  - Użytkownik nie będzie miał dostępu do centrum administracyjne platformy Microsoft 365.

Aby uzyskać więcej informacji o uprawnieniach, zobacz Uprawnienia w [Centrum zabezpieczeń & zgodności](permissions-in-the-security-and-compliance-center.md) i Zapewnianie użytkownikom dostępu do Centrum zabezpieczeń & [zgodności](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Gdzie można znaleźć pulpit nawigacyjny przepływu poczty

Otwórz Centrum zabezpieczeń & zgodności w miejscu <https://protection.office.com>, rozwiń przepływ **poczty e-mail**, a następnie wybierz pozycję Pulpit **nawigacyjny**.

Aby przejść bezpośrednio do pulpitu nawigacyjnego przepływu poczty e-mail, otwórz program <https://protection.office.com/mailflow/dashboard>.