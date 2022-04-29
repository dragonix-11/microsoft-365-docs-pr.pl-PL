---
title: Naprawianie szczegółowych informacji o regułach powolnego przepływu poczty e-mail
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
description: Administratorzy mogą dowiedzieć się, jak używać szczegółowych informacji na temat rozwiązywania problemów z regułami powolnych przepływów poczty w Centrum zgodności & zabezpieczeń w celu identyfikowania i naprawiania nieefektywnych lub uszkodzonych reguł przepływu poczty (nazywanych również regułami transportu) w organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 650389529f2a5d811f71b7c3f755d93e7e734d81
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128745"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Rozwiązywanie problemów ze szczegółowymi informacjami o regułach przepływu poczty w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Nieefektywne reguły przepływu poczty (nazywane również regułami transportu) mogą prowadzić do opóźnień przepływu poczty w organizacji. Ten wgląd w szczegółowe informacje zgłasza reguły przepływu poczty, które mają wpływ na przepływ poczty w organizacji. Przykłady tych typów reguł obejmują:

- Warunki, które używają **elementu Jest członkiem** dla dużych grup.
- Warunki, które używają dopasowywania wzorców złożonych wyrażeń regularnych (regex).
- Warunki, które używają ewidencjonowania zawartości w załącznikach.

Szczegółowe informacje na temat **rozwiązywania problemów z regułami powolnego przepływu poczty** w obszarze **Zalecane dla Ciebie** [na pulpicie nawigacyjnym przepływu poczty](mail-flow-insights-v2.md) w [Centrum zgodności & zabezpieczeń](https://protection.office.com) powiadamia użytkownika, gdy ukończenie reguły przepływu poczty trwa zbyt długo.

Ta analiza jest wyświetlana dopiero po wykryciu warunku (jeśli nie masz żadnych pętli poczty, nie zobaczysz szczegółowych informacji).

To powiadomienie ułatwia identyfikowanie i dostosowywanie reguł przepływu poczty w celu zmniejszenia opóźnień w przepływie poczty.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules.png" alt-text="Szczegółowe informacje na temat rozwiązywania problemów z regułami powolnych przepływów poczty w obszarze Zalecane dla Ciebie na pulpicie nawigacyjnym przepływu poczty" lightbox="../../media/mfi-fix-slow-mail-flow-rules.png":::

Po kliknięciu pozycji **Wyświetl szczegóły** w widżetu zostanie wyświetlone okno wysuwane z większą ilością informacji:

- **Reguła**: możesz zatrzymać kursor na podsumowaniu, aby wyświetlić wszystkie warunki, wyjątki i akcje reguły. Możesz kliknąć podsumowanie, aby edytować regułę w centrum administracyjnym Exchange (EAC) pod adresem <https://admin.exchange.microsoft.com/#/transportrules>.
- **Liczba ocenianych komunikatów**: możesz kliknąć pozycję **Wyświetl przykładowe komunikaty** , aby wyświetlić wyniki [śledzenia komunikatów](message-trace-scc.md) dla przykładu komunikatów, których dotyczy reguła.
- **Średni czas spędzony na każdym komunikacie**
- **Mediana czasu poświęconego na komunikat**: wartość środkowa, która oddziela górną połowę od dolnej połowy danych czasu.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules-details.png" alt-text="Okno wysuwane Szczegóły wyświetlane po kliknięciu pozycji Wyświetl szczegóły w szczegółowych informacjach na temat rozwiązywania problemów z regułami powolnych przepływów poczty" lightbox="../../media/mfi-fix-slow-mail-flow-rules-details.png":::

Aby uzyskać więcej informacji na temat warunków i wyjątków w regułach przepływu poczty, zobacz [Warunki reguły przepływu poczty i wyjątki (predykaty) w Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>Zobacz też

Aby uzyskać informacje o innych szczegółowych informacjach na pulpicie nawigacyjnym przepływu poczty, zobacz [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](mail-flow-insights-v2.md).
