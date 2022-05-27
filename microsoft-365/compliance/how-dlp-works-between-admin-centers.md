---
title: Jak działa usługa DLP z centrum administracyjnym & zgodności & zabezpieczeń & Exchange
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a7e4342a-a0a1-4b43-b166-3d7eecf5d2fd
description: Dowiedz się, jak usługa DLP w Centrum zgodności & zabezpieczeń współpracuje z regułami DLP i przepływem poczty (reguły transportu) w centrum administracyjnym Exchange.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 0c5c6288ed9e3c1f536e7a221a270bad9663cf6b
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753413"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>Jak działa DLP między Centrum zgodności a centrum administracyjnym Exchange

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W Microsoft Purview można utworzyć zasady ochrony przed utratą danych (DLP) w dwóch różnych centrach administracyjnych:
  
- W **portal zgodności Microsoft Purview** można utworzyć pojedyncze zasady DLP, aby chronić zawartość w SharePoint, OneDrive, Exchange, Teams, a teraz urządzeniach punktu końcowego. W tym miejscu zalecamy utworzenie zasad DLP. Aby uzyskać więcej informacji, zobacz [Dokumentacja ochrony przed utratą danych](data-loss-prevention-policies.md).
    
- W <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a> można utworzyć zasady DLP, aby chronić zawartość tylko w Exchange. Te zasady mogą używać Exchange reguł przepływu poczty (nazywanej również regułami transportu), więc mają bardziej szczegółowe opcje obsługi poczty e-mail. Aby uzyskać więcej informacji, zobacz [DLP w centrum administracyjnym Exchange](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
Zasady DLP utworzone w tych centrach administracyjnych działają obok siebie — w tym artykule wyjaśniono, jak to zrobić.
  
![Strony DLP w Centrum zabezpieczeń i zgodności oraz w centrum administracyjnym Exchange.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Jak usługa DLP w Centrum zgodności & zabezpieczeń współpracuje z regułami DLP i przepływem poczty w centrum administracyjnym Exchange

Po utworzeniu zasad DLP w Centrum zgodności & zabezpieczeń zasady są wdrażane we wszystkich lokalizacjach uwzględnionych w zasadach. Jeśli zasady obejmują Exchange Online, zasady są tam synchronizowane i wymuszane w dokładnie taki sam sposób jak zasady DLP utworzone w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. 
  
Jeśli zasady DLP zostały utworzone w centrum administracyjnym Exchange, zasady te będą nadal działać równolegle z wszelkimi zasadami dotyczącymi poczty e-mail utworzonej w Centrum zgodności & zabezpieczeń. Należy jednak pamiętać, że pierwszeństwo mają reguły utworzone w centrum administracyjnym Exchange. Wszystkie Exchange reguły przepływu poczty są najpierw przetwarzane, a następnie przetwarzane są reguły DLP z Centrum zgodności & zabezpieczeń.
  
Oznacza to:
  
- Wiadomości zablokowane przez reguły przepływu poczty Exchange nie będą skanowane według reguł DLP utworzonych w Centrum zgodności usługi Security &.
- Wiadomości poddane kwarantannie przez Exchange reguły przepływu poczty lub inne filtry uruchamiane przed skanowaniem DLP nie będą skanowane przez DLP. 
- Jeśli reguła przepływu poczty Exchange modyfikuje komunikat w taki sposób, aby był zgodny z zasadami DLP w Centrum zgodności & zabezpieczeń, takimi jak dodawanie użytkowników zewnętrznych, reguły DLP wykryje ją i wymuszą zasady zgodnie z potrzebami.
    
Należy również pamiętać, że Exchange reguł przepływu poczty, które używają akcji "zatrzymaj przetwarzanie", nie mają wpływu na przetwarzanie reguł DLP w Centrum zgodności & zabezpieczeń — nadal będą przetwarzane.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Porady dotyczące zasad w Centrum zgodności & zabezpieczeń a centrum administracyjnym Exchange

Porady dotyczące zasad mogą działać z zasadami DLP i regułami przepływu poczty utworzonymi w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a> lub z zasadami DLP utworzonymi w Centrum zgodności usługi Security &, ale nie w obu tych przypadkach. Wynika to z faktu, że te zasady są przechowywane w różnych lokalizacjach, ale wskazówki dotyczące zasad mogą być rysowane tylko z jednej lokalizacji.
  
Jeśli w centrum administracyjnym Exchange skonfigurowano wskazówki dotyczące zasad, żadne wskazówki dotyczące zasad skonfigurowane w Centrum zgodności & zabezpieczeń nie będą wyświetlane użytkownikom w Outlook w sieci Web i Outlook 2013 r. i nowszych, dopóki nie wyłączysz porad w centrum administracyjnym Exchange. Dzięki temu bieżące reguły przepływu poczty Exchange będą nadal działać do momentu przełączenia się do Centrum zgodności & zabezpieczeń.
  
>[!Note]
>Porady dotyczące zasad mogą być rysowane tylko z jednej lokalizacji, ale powiadomienia e-mail są zawsze wysyłane, nawet jeśli używasz zasad DLP zarówno w Centrum zgodności & zabezpieczeń, jak i w centrum administracyjnym Exchange.
