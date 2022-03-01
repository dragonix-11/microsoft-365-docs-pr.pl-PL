---
title: Jak działa ochrona przed zagrożeniami (DLP) & Centrum zgodności & Exchange administracyjnego
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
description: Dowiedz się, jak zasady DLP w Centrum & zabezpieczeń i zgodności są zgodne z regułami przepływu poczty (DLP) w centrum administracyjnym usługi Exchange i poczty.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 90706b3dad55ff84d274656673f9a60dbd71e35f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017796"
---
# <a name="how-dlp-works-between-the-microsoft-365-compliance-center-and-exchange-admin-center"></a>Jak działa zasady DLP między Centrum zgodności usługi Microsoft 365 a centrum Exchange administracyjnego

W Microsoft 365 możesz utworzyć zasady ochrony przed utratą danych (DLP) w dwóch różnych centrach aadministracyjnym:
  
- W Centrum **Microsoft 365 zgodności** możesz utworzyć jedną zasady DLP, aby chronić zawartość w urządzeniach SharePoint, OneDrive, Exchange, Teams, a teraz na urządzeniach końcowych. Zalecamy utworzenie tutaj zasad DLP. Aby uzyskać więcej informacji, zobacz [Informacje dotyczące ochrony przed utratą danych](data-loss-prevention-policies.md).
    
- W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a> możesz utworzyć zasady DLP, aby chronić zawartość tylko w Exchange. Te zasady mogą używać Exchange przepływu poczty e-mail (nazywane także regułami transportu), dzięki czemu mają więcej opcji specyficznych dla obsługi poczty e-mail. Aby uzyskać więcej informacji, zobacz [Temat zasad DLP w centrum Exchange administracyjnego](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
Zasady DLP utworzone w tych centrach aadministracyjnym działają obok siebie — w tym temacie wyjaśniono, jak to zrobić.
  
![Strony DLP w Centrum zabezpieczeń i zgodności Exchange centrum administracyjnym.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Jak zasady DLP w Centrum & zabezpieczeń i zgodności są zgodne z regułami DLP i przepływem poczty e-mail w centrum Exchange administracyjnego

Po utworzeniu zasad DLP w Centrum & zgodności zabezpieczeń zasady są wdrażane we wszystkich lokalizacjach zawartych w tych zasadach. Jeśli zasady obejmują Exchange Online, zostaną zsynchronizowane i wyegzekwowane dokładnie tak samo, jak zasady DLP utworzone w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange.</a> 
  
Jeśli zasady DLP zostały utworzone w centrum administracyjnym usługi Exchange, będą one nadal działać obok wszelkich zasad dotyczących wiadomości e-mail utworzonych w Centrum & zabezpieczeń i zgodności. Pamiętaj jednak, że reguły utworzone w centrum Exchange mają pierwszeństwo. Wszystkie Exchange przepływu poczty e-mail są najpierw przetwarzane, a następnie reguły DLP z Centrum zabezpieczeń & zgodności są przetwarzane.
  
Oznacza to, że:
  
- Wiadomości blokowane przez reguły przepływu Exchange nie będą skanowane przez reguły DLP utworzone w Centrum & zabezpieczeń i zgodności.

- Wiadomości poddane kwarantannie przez Exchange przepływu poczty e-mail lub inne filtry będą uruchamiane, zanim zasady DLP nie będą skanowane przez zasady DLP.
    
- Jeśli reguła przepływu poczty e-mail programu Exchange zmodyfikuje wiadomość w sposób, który powoduje dopasowanie jej do zasad DLP w Centrum zgodności usługi & — na przykład dodawania użytkowników zewnętrznych — reguły DLP wykryją to i wymuszą zasady zgodnie z potrzebami.
    
Pamiętaj także, że Exchange przepływu poczty e-mail, które używają akcji "zatrzymaj przetwarzanie", nie mają wpływu na przetwarzanie reguł ochrony przed zagrożeniami w Centrum zgodności usługi & — będą one nadal przetwarzane.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Porady dotyczące zasad w Centrum zabezpieczeń & zgodności a w centrum Exchange administracyjnego

Porady dotyczące zasad mogą działać zarówno z zasadami DLP, jak i regułami przepływu poczty e-mail utworzonymi w centrum administracyjnym programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> lub z zasadami DLP utworzonymi w Centrum zgodności usługi &, ale nie obu. Jest tak, ponieważ te zasady są przechowywane w różnych lokalizacjach, ale porady dotyczące zasad mogą rysować tylko z jednej lokalizacji.
  
Jeśli w centrum administracyjnym usługi Exchange skonfigurowano porady dotyczące zasad, porady dotyczące zasad skonfigurowane w Centrum zgodności usługi & nie będą wyświetlane użytkownikom w programach Outlook w sieci Web ani Outlook 2013 ani nowszych do momentu wyłączenia porad w centrum administracyjnym usługi Exchange. Dzięki temu twoje bieżące reguły przepływu Exchange będą nadal działać, dopóki nie zdecydujesz się na przełączenie do Centrum zabezpieczeń & zgodności.
  
Pamiętaj, że chociaż porady dotyczące zasad mogą rysować tylko z jednej lokalizacji, powiadomienia e-mail są zawsze wysyłane, nawet jeśli korzystasz z zasad DLP zarówno w Centrum zabezpieczeń & zgodności, jak i w centrum administracyjnym usługi Exchange.
