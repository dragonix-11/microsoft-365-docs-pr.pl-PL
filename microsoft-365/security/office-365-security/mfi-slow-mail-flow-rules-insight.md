---
title: Rozwiązywanie problemów dotyczących wolnych reguł przepływu poczty e-mail
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak znaleźć i naprawić nieefektywne lub uszkodzone reguły przepływu poczty (nazywane także regułami transportu) w Centrum zgodności usługi Security &, aby zidentyfikować i naprawić nieefektywne lub uszkodzone reguły przepływu poczty (nazywane także regułami transportu) w organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: af6d727f84cdaaed1b7f7558313ac7d080a13c93
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681529"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Rozwiązywanie problemów dotyczących wolnych reguł przepływu poczty e-mail w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Nieefektywne reguły przepływu poczty e-mail (nazywane także regułami transportu) mogą prowadzić do opóźnień przepływu poczty e-mail w organizacji. Ta szczegółowe informacje raportuje reguły przepływu poczty e-mail, które mają wpływ na przepływ poczty e-mail organizacji. Oto przykłady tych typów reguł:

- Warunki, dla **których jest on członkiem** w dużych grupach.
- Warunki, które używają złożonego dopasowania wzorca wyrażeń regularnych (regex).
- Warunki, które korzystają z funkcji sprawdzania zawartości załączników.

W **obszarze** Polecane dla Ciebie na pulpicie  nawigacyjnym przepływu poczty w [](mail-flow-insights-v2.md) Centrum zabezpieczeń & zgodności znajdziesz informacje o regułach wolnego przepływu poczty [e-mail](https://protection.office.com) z powiadomieniem o tym, że ich stosowanie trwa zbyt długo.

Ta informacja pojawia się tylko po wykryciu warunku (jeśli nie masz żadnych pętli poczty, nie zobaczysz tej informacji).

To powiadomienie może ułatwić identyfikowanie i dostosowywanie reguł przepływu poczty e-mail w celu zmniejszenia opóźnień przepływu poczty.

![Rozwiązywanie problemów dotyczących wolnych reguł przepływu poczty w obszarze Polecane dla Ciebie na pulpicie nawigacyjnym przepływu poczty.](../../media/mfi-fix-slow-mail-flow-rules.png)

Po kliknięciu w **widżecie** przycisku Wyświetl szczegóły zostanie wyświetlone wysuwne okno z większej liczby informacji:

- **Reguła**: Możesz zatrzymać wskaźnik myszy na podsumowaniu, aby wyświetlić wszystkie warunki, wyjątki i akcje reguły. Możesz kliknąć podsumowanie, aby edytować regułę w Centrum administracyjnym programu Exchange (EAC) w oknie <https://admin.exchange.microsoft.com/#/transportrules>.
- **Liczba wiadomości ocenionych** jako: Możesz kliknąć pozycję  Wyświetl przykładowe wiadomości, aby [](message-trace-scc.md) wyświetlić wyniki śledzenia wiadomości dla przykładowych wiadomości, na które wpływa reguła.
- **Średni czas spędzony na każdej wiadomości**
- **Mediana czasu spędzonego na wiadomości**: wartość środkowa, która oddziela górną połowę od dolnej połowy danych czasu.

![Wysuw szczegółów, który pojawia się po kliknięciu pozycji Wyświetl szczegóły w szczegółowych informacjach Rozwiązywanie problemów dotyczących wolnych reguł przepływu poczty.](../../media/mfi-fix-slow-mail-flow-rules-details.png)

Aby uzyskać więcej informacji na temat warunków i wyjątków w regułach przepływu poczty e-mail, zobacz Warunki i wyjątki reguły przepływu poczty [e-mail (predykaty) w Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).