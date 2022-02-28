---
title: Najważniejsze informacje o stanie przepływu poczty e-mail w domenie na pulpicie nawigacyjnym przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak za pomocą szczegółowych informacji o stanie przepływu poczty e-mail w panelu przepływu poczty e-mail w Centrum zabezpieczeń & zgodności rozwiązywać problemy z przepływem poczty e-mail związane z rekordami MX.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e4ed59e31cd21826eebf306e566610d54635f0c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984589"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Najważniejsze informacje o stanie przepływu poczty e-mail domeny w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Najważniejsze **informacje o stanie przepływu** poczty e-mail domeny na pulpicie [](https://protection.office.com) nawigacyjnym przepływu poczty w Centrum & zabezpieczeń i zgodności dają bieżący stan przepływu poczty dla organizacji.[](mail-flow-insights-v2.md)

Te informacje pomagają zidentyfikować domeny, w których występują problemy z przepływem ***poczty e-mail, i rozwiązywać je*** . Na przykład domena nie może odbierać zewnętrznych wiadomości e-mail, ponieważ domena wygasła lub domena ma niepoprawny rekord MX.

![Top domain flow status widget in the Mail flow dashboard in the Security & Compliance Center.](../../media/mfi-top-domain-mail-flow-status-widget.png)

Po kliknięciu w **widżecie** przycisku Wyświetl szczegóły zostanie wyświetlone **wysuwne** okno wysuwu stanu domeny z informacjami o stanie poszczególnych domen:

- **Domain (Domena)**
- **Poprzedni rekord MX**
- **Bieżący rekord MX**
- **Stan odbierania wiadomości e-mail**
- **Stan domeny**: zielony znacznik wyboru wskazuje bieżący rekord MX (w momencie kliknięcia widżetu) odpowiada wartości zapisanej w rekordzie, a domena otrzymała pocztę e-mail w ciągu ostatnich dwóch godzin.

  Czerwony znak X wskazuje, że rekord MX został zmieniony, a w ciągu ostatnich 6 godzin domena nie otrzymała żadnych wiadomości e-mail. Prawdopodobnie oznacza to, że domena wygasła lub że rekord MX został niepoprawnie zaktualizowany. Sprawdź u rejestratora twojej domeny lub w usłudze hostingu systemu DNS, czy domena wygasła, czy rekord MX domeny jest nieprawidłowy.

Możesz kliknąć pozycję **Wyświetl więcej,** aby wyświetlić te same informacje dla większej liczby domen.

![Wysuwu szczegóły w szczegółowych informacjach o stanie przepływu poczty w domenie najwyższej jakości.](../../media/mfi-top-domain-mail-flow-status-view-details.png)

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
