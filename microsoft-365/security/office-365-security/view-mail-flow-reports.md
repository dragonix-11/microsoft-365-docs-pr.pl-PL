---
title: Wyświetlanie raportów przepływu poczty e-mail na pulpicie nawigacyjnym Raporty
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się więcej o raportach przepływu poczty e-mail dostępnych na pulpicie nawigacyjnym Raporty w Centrum & zabezpieczeń.
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d1fc133a8e05541f402e35cf8d62ee9662af661b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476230"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Wyświetlanie raportów przepływu poczty e-mail na pulpicie nawigacyjnym Raporty w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Większość raportów w tym artykule jest również dostępna w portalu usługi Microsoft 365 Defender lub centrum administracyjnym usługi Exchange(EAC). Aby uzyskać więcej informacji, zobacz następujące tematy:
>
> - [Raporty przepływu poczty e-mail Exchange centrum administracyjnym](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [Wyświetlanie raportów zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender-mail](view-email-security-reports.md)

Oprócz raportów przepływu poczty e-mail dostępnych na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi & Security & na pulpicie nawigacyjnym Raporty są dostępne różne dodatkowe raporty przepływu poczty e-mail, które ułatwiają monitorowanie Microsoft 365 organizacji.[](mail-flow-insights-v2.md)

Jeśli masz [odpowiednie uprawnienia,](#what-permissions-are-needed-to-view-these-reports) możesz wyświetlić te raporty w Centrum zabezpieczeń & zgodności<https://protection.office.com>, przechodząc do **pulpitu nawigacyjnego Raporty**\>. Aby przejść bezpośrednio do pulpitu nawigacyjnego Raporty, otwórz .<https://protection.office.com/insightdashboard>

:::image type="content" source="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png" alt-text="Pulpit nawigacyjny Raporty w Centrum & zgodności" lightbox="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png":::

## <a name="connector-report"></a>Raport łącznika

> [!NOTE]
> Ten raport został zastąpiony raportem Wiadomości przychodzące **i** Wiadomości **wychodzące w** Aplikacji programu EAC. Aby uzyskać więcej informacji, zobacz Raporty wiadomości przychodzących i [wychodzących w nowej aplikacji EAC](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports).

## <a name="exchange-transport-rule-report"></a>Exchange reguł transportu

Raport **Exchange reguł transportu** pokazuje wpływ reguł przepływu poczty e-mail (nazywanych również regułami transportu) na wiadomości przychodzące i wychodzące w organizacji.

Aby wyświetlić raport, otwórz Centrum zabezpieczeń i zgodności & stronie <https://protection.office.com>,  \> przejdź do pulpitu nawigacyjnego Raporty i wybierz pozycję Exchange **Transport**. Aby przejść bezpośrednio do raportu, otwórz program <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/scc-transport-rule-report-widget.png" alt-text="Widżet Exchange reguły transportu na pulpicie nawigacyjnym Raporty" lightbox="../../media/scc-transport-rule-report-widget.png":::

> [!NOTE]
> Raport **Exchange transportu jest** teraz dostępny w EAC. Aby uzyskać więcej informacji, [Exchange raport reguł transportu w nowej Wiadomości e-mail](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

## <a name="forwarding-report"></a>Raport przesyłania dalej

> [!NOTE]
> Raport **przesyłanie dalej jest** teraz dostępny w EAC. Aby uzyskać więcej informacji, zobacz [Raport Autosyłki wiadomości przesyłanych dalej w nowej aplikacji EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Raport o stanie przepływu poczty

Raport **o stanie przepływu** poczty jest podobny do raportu Wysłane i odebrane wiadomości e-mail [z dodatkowymi](#sent-and-received-email-report) informacjami na temat dozwolonych lub zablokowanych wiadomości e-mail na krawędzi. Jest to jedyny raport, który zawiera informacje o ochronie brzegowej i pokazuje, ile wiadomości e-mail zostało zablokowanych, zanim zezwolisz na ich dostęp do usługi w celu oceny przez usługę Exchange Online Protection (EOP). Ważne jest, aby zrozumieć, że jeśli wiadomość zostanie wysłana do pięciu adresatów, jest ona liczna jako pięć różnych wiadomości, a nie jako jedna wiadomość.

Aby wyświetlić raport, otwórz Centrum zabezpieczeń i [&](https://protection.office.com) zgodności,  \> przejdź do pulpitu nawigacyjnego Raporty **i wybierz pozycję** **Raport o stanie przepływu poczty**. Aby przejść bezpośrednio do raportu **o stanie przepływu poczty e-mail**, otwórz program <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/scc-mail-flow-status-report-widget.png" alt-text="Widżet raportu o stanie przepływu poczty na pulpicie nawigacyjnym Raporty" lightbox="../../media/scc-mail-flow-status-report-widget.png":::

> [!NOTE]
> Kliknięcie widżetu dla tego raportu w Centrum & zgodności (protection.office.com) umożliwia teraz dostęp do pełnego raportu w portalu Microsoft 365 Defender (security.microsoft.com). Aby uzyskać szczegółowe informacje na temat raportu, zobacz [Raport o stanie przepływu poczty](view-email-security-reports.md#mailflow-status-report).

## <a name="sent-and-received-email-report"></a>Wysłano i odebrano raport wiadomości e-mail

> [!NOTE]
> Ten raport został zastąpiony raportem [o stanie przepływu poczty](#mailflow-status-report).

## <a name="top-senders-and-recipients-report"></a>Raport Najgorętsi nadawcy i adresaci

**Najgoręci** nadawcy i adresaci to najgoręci nadawcy w organizacji, a także najgoręci adresaci wiadomości wykrytych przez usługę EOP i Ochrona usługi Office 365 w usłudze Defender ochrony.

Aby wyświetlić raport, otwórz Centrum zabezpieczeń & zgodności <https://protection.office.com>w miejscu ,  \> przejdź do pulpitu nawigacyjnego Raporty i wybierz pozycję Najgoręci **nadawcy i adresaci**. Aby przejść bezpośrednio do raportu, otwórz jeden z następujących adresów URL:

- Ochrona usługi Office 365 w usłudze Defender:<https://protection.office.com/TopSenderRecipientsATP>
- EOP: <https://protection.office.com/TopSenderRecipients>

:::image type="content" source="../../media/scc-top-senders-and-recipients-widget.png" alt-text="Widżet Najgorętsi nadawcy i adresaci na pulpicie nawigacyjnym Raporty" lightbox="../../media/scc-top-senders-and-recipients-widget.png":::

> [!NOTE]
> Kliknięcie widżetu dla tego raportu w Centrum zgodności & security protection.office.com umożliwia jednak dostęp do strony protection.office.com, ale zawartość strony pochodzi z Microsoft 365 Defender sieci Web. Aby uzyskać szczegółowe informacje na temat raportu, zobacz Raport Najgorętsi [nadawcy i adresaci](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Jakie uprawnienia są potrzebne do wyświetlania tych raportów?

Aby móc wyświetlać raporty opisane w tym artykule i korzystać z nich, musisz być członkiem jednej z następujących grup ról w Centrum zabezpieczeń & zgodności:

- **Zarządzanie organizacją**
- **Administrator zabezpieczeń**
- **Czytnik zabezpieczeń**
- **Czytnik globalny**

Aby uzyskać więcej informacji, [zobacz Uprawnienia w Centrum & zgodności](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> Dodanie użytkowników do odpowiedniej roli Azure Active Directory w aplikacji Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w Centrum zgodności usługi & zabezpieczeń i uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

## <a name="related-topics"></a>Tematy pokrewne

[Inteligentne raporty i szczegółowe informacje w Centrum & zgodności](reports-and-insights-in-security-and-compliance.md)

[Szczegółowe informacje o przepływie poczty w Centrum & zgodności](mail-flow-insights-v2.md)

[Wyświetlanie raportów zabezpieczeń poczty e-mail w Centrum & zgodności](view-email-security-reports.md)

[Wyświetlanie raportów dla Ochrona usługi Office 365 w usłudze Microsoft Defender](view-reports-for-mdo.md)
