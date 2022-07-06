---
title: Jak działa protokół DLP z Centrum zgodności usługi Security & & Exchange
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
description: Dowiedz się, jak usługa DLP w Centrum zgodności & zabezpieczeń współpracuje z regułami DLP i przepływem poczty (reguły transportu) w centrum administracyjnym programu Exchange.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: fa77bf84ff8ef2b4f194f45b9a29b49f6b662a70
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641411"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>Jak działa DLP między Centrum zgodności i Centrum administracyjnym programu Exchange

W usłudze Microsoft Purview można utworzyć zasady ochrony przed utratą danych (DLP) w dwóch różnych centrach administracyjnych:
  
- W **portal zgodności Microsoft Purview** można utworzyć pojedyncze zasady DLP, aby chronić zawartość w programach SharePoint, OneDrive, Exchange, Teams, a teraz urządzeniach punktu końcowego. W tym miejscu zalecamy utworzenie zasad DLP. Aby uzyskać więcej informacji, zobacz [Dokumentacja ochrony przed utratą danych](data-loss-prevention-policies.md).
    
- W <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a> można utworzyć zasady DLP, aby chronić zawartość tylko w programie Exchange. Te zasady mogą używać reguł przepływu poczty programu Exchange (nazywanych również regułami transportu), więc mają bardziej szczegółowe opcje obsługi poczty e-mail. Aby uzyskać więcej informacji, zobacz [DLP w centrum administracyjnym programu Exchange](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
Zasady DLP utworzone w tych centrach administracyjnych działają obok siebie — w tym artykule wyjaśniono, jak to zrobić.
 
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Jak usługa DLP w Centrum zgodności & zabezpieczeń współpracuje z regułami DLP i przepływem poczty w centrum administracyjnym programu Exchange

Po utworzeniu zasad DLP w Centrum zgodności & zabezpieczeń zasady są wdrażane we wszystkich lokalizacjach uwzględnionych w zasadach. Jeśli zasady obejmują Exchange Online, zasady są tam synchronizowane i wymuszane w dokładnie taki sam sposób jak zasady DLP utworzone w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a>. 
  
Jeśli zasady DLP zostały utworzone w centrum administracyjnym programu Exchange, te zasady będą nadal działać równolegle z wszelkimi zasadami dotyczącymi poczty e-mail utworzonej w Centrum zgodności & zabezpieczeń. Należy jednak pamiętać, że pierwszeństwo mają reguły utworzone w centrum administracyjnym programu Exchange. Najpierw przetwarzane są wszystkie reguły przepływu poczty programu Exchange, a następnie przetwarzane są reguły DLP z Centrum zgodności & zabezpieczeń.
  
Oznacza to:
  
- Wiadomości zablokowane przez reguły przepływu poczty programu Exchange nie będą skanowane według reguł DLP utworzonych w Centrum zgodności & zabezpieczeń.
- Wiadomości poddane kwarantannie przez reguły przepływu poczty programu Exchange lub inne filtry są uruchamiane przed skanowaniem DLP. 
- Jeśli reguła przepływu poczty programu Exchange modyfikuje komunikat w sposób, który powoduje dopasowanie go do zasad DLP w Centrum zgodności & zabezpieczeń, takich jak dodawanie użytkowników zewnętrznych, reguły DLP wykryje ją i wymuszą zasady zgodnie z potrzebami.
    
Należy również pamiętać, że reguły przepływu poczty programu Exchange korzystające z akcji "zatrzymaj przetwarzanie" nie mają wpływu na przetwarzanie reguł DLP w Centrum zgodności & zabezpieczeń — nadal będą przetwarzane.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Porady dotyczące zasad w Centrum zgodności & zabezpieczeń a centrum administracyjnym programu Exchange

Porady dotyczące zasad mogą współpracować z zasadami DLP i regułami przepływu poczty utworzonymi w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a> lub z zasadami DLP utworzonymi w Centrum zgodności usługi Security &, ale nie w obu tych przypadkach. Wynika to z faktu, że te zasady są przechowywane w różnych lokalizacjach, ale wskazówki dotyczące zasad mogą być rysowane tylko z jednej lokalizacji.
  
Jeśli w centrum administracyjnym programu Exchange skonfigurowano porady dotyczące zasad, żadne wskazówki dotyczące zasad skonfigurowane w Centrum zgodności & zabezpieczeń nie będą wyświetlane użytkownikom w programach Outlook w sieci Web i Outlook 2013 i nowszych, dopóki nie wyłączysz porad w centrum administracyjnym programu Exchange. Dzięki temu bieżące reguły przepływu poczty programu Exchange będą nadal działać do momentu przełączenia się do Centrum zgodności & zabezpieczeń.
  
>[!Note]
>Porady dotyczące zasad mogą być rysowane tylko z jednej lokalizacji, ale powiadomienia e-mail są zawsze wysyłane, nawet jeśli używasz zasad DLP zarówno w Centrum zgodności usługi Security &, jak i w Centrum administracyjnym programu Exchange.
