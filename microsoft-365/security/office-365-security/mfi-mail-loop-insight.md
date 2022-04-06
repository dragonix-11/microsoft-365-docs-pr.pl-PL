---
title: Naprawianie możliwych informacji o pętli poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: cb801985-3c89-4979-9c18-17829a4cb563
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak za pomocą informacji fix possible mail loop in the Mail flow dashboard in the Security & Compliance Center to identify and fix mail loops in their organization.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5a74e7cc623dffd6bae6451f7488d8f630b607b2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469146"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>Naprawianie ewentualnych informacji dotyczących pętli poczty w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pętle poczty są złe, ponieważ:

- Marnują one zasoby systemowe.
- Zużyje one przydział poczty e-mail Twojej organizacji.
- Wysyłają one do oryginalnych nadawców mylące raporty o niedo dostarczenia (nazywane też raportami o niedo dostarczenia lub wiadomościami odsuwanymi).

W **obszarze** Polecane dla Ciebie na pulpicie nawigacyjnym przepływu poczty [](mail-flow-insights-v2.md) w Centrum zabezpieczeń & zgodności [](https://protection.office.com) w Centrum zabezpieczeń i zgodności jest powiadamiany o wykryciu pętli poczty w organizacji.

Ta informacja pojawia się tylko po wykryciu warunku (jeśli nie masz żadnych pętli poczty, nie zobaczysz tej informacji).

:::image type="content" source="../../media/mfi-fix-possible-mail-loop.png" alt-text="Szczegółowe informacje na temat naprawiania wolnych reguł przepływu poczty e-mail w obszarze Polecane dla Ciebie na pulpicie nawigacyjnym przepływu poczty" lightbox="../../media/mfi-fix-possible-mail-loop.png":::

Po kliknięciu w **widżecie** przycisku Wyświetl szczegóły zostanie wyświetlone wysuwne okno z większej liczby informacji:

- **Domain (Domena)**
- **Liczba wiadomości**: Możesz kliknąć pozycję **Wyświetl** przykładowe wiadomości, aby wyświetlić [](message-trace-scc.md) wyniki śledzenia wiadomości dla przykładowych wiadomości, których dotyczyła pętla.
- **Typ domeny**" Na przykład Autorytatywny lub Nie autorytatywny.
- **Rekord MX**: wartości hosta (**serwera poczty**) i **priorytetu** rekordu MX domeny.
- **Loop przyczynę** **i jak to** naprawić: Zidentyfik będziemy identyfikować najbardziej typowe scenariusze pętli poczty i udostępnimy zalecane akcje naprawiania pętli.

:::image type="content" source="../../media/mfi-fix-possible-mail-loop-details.png" alt-text="Wysuw szczegółów wyświetlany po kliknięciu pozycji Wyświetl szczegóły w możliwych informacjach dotyczących pętli poczty" lightbox="../../media/mfi-fix-possible-mail-loop-details.png":::

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
