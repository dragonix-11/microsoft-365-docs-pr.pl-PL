---
title: Obsługa sprawdzania poprawności wiadomości podpisanych przez DKIM (Domain Keys Identified Mail)
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- M365-security-compliance
description: Dowiedz się więcej o sprawdzaniu poprawności wiadomości podpisanych przez DKIM w Exchange Online Protection i Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5ea98add5ebe860f756d645909366a1f5502832
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988044"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>Obsługa sprawdzania poprawności wiadomości podpisanych przez DKIM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) i Exchange Online weryfikację ruchu przychodzącego wiadomości [DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt) (Domain Keys Identified Mail).

Aplikacja DKIM sprawdza, czy wiadomość e-mail nie  została sfałszowana przez inną osobę i została wysłana z domeny, z poziomu  tej domeny. Wiadomość e-mail jest owijana z organizacją, która ją wysłała. Weryfikacja DKIM jest używana automatycznie dla wszystkich wiadomości wysyłanych przy użyciu protokołu IPv6. Microsoft 365 obsługuje również funkcję DKIM, gdy poczta jest wysyłana za pośrednictwem protokołu IPv4. (Aby uzyskać więcej informacji na temat obsługi protokołu IPv6, zobacz Obsługa anonimowych przychodzących wiadomości e-mail za pośrednictwem [protokołu IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md)).

DKIM sprawdza poprawność podpisanej cyfrowo wiadomości wyświetlanej w DKIM-Signature nagłówkach wiadomości. Wyniki sprawdzania poprawności DKIM-Signature są stemplowane w nagłówku Authentication-Results pliku. Tekst nagłówka wiadomości jest podobny do następującego (gdzie contoso.com nadawcą):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Aby uzyskać więcej informacji na Authentication-Results wiadomości, zobacz RFC 7001 (Pole nagłówka wiadomości do oznaczania [stanu uwierzytelniania wiadomości](https://www.rfc-editor.org/rfc/rfc7001.txt)). Implementacja DKIM firmy Microsoft jest zgodna z tym standardem RFC.

Administratorzy mogą tworzyć Exchange [przepływu poczty e-mail](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (nazywane także regułami transportu) na temat wyników weryfikacji DKIM. Te reguły przepływu poczty e-mail umożliwiają administratorom filtrowanie lub rozsyłanie wiadomości zgodnie z potrzebami.