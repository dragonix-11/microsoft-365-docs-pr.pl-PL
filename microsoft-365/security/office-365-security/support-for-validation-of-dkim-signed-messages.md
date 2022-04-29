---
title: Obsługa walidacji wiadomości z podpisem DKIM (Domain Keys Identified Mail)
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
description: Dowiedz się więcej o walidacji podpisanych komunikatów DKIM w Exchange Online Protection i Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dcdd251ba1266033671ac524426d1ac3d2f56a10
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130719"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>Obsługa weryfikacji podpisanych komunikatów DKIM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) i Exchange Online obsługują walidację przychodzącą wiadomości [DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt) (Domain Keys Identified Mail).

DKIM sprawdza, czy wiadomość e-mail nie została *sfałszowana* przez inną osobę i została wysłana z domeny, z którą *pochodzi* . Wiąże ona wiadomość e-mail z organizacją, która ją wysłała. Weryfikacja DKIM jest używana automatycznie dla wszystkich komunikatów wysyłanych przy użyciu protokołu IPv6. Microsoft 365 obsługuje również maszynę DKIM, gdy poczta jest wysyłana za pośrednictwem protokołu IPv4. (Aby uzyskać więcej informacji na temat obsługi protokołu IPv6, zobacz [Obsługa anonimowych przychodzących wiadomości e-mail za pośrednictwem protokołu IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md)).

Moduł DKIM weryfikuje cyfrowo podpisany komunikat, który pojawia się w nagłówku DKIM-Signature nagłówków wiadomości. Wyniki weryfikacji DKIM-Signature są ostemplowane w nagłówku Authentication-Results. Tekst nagłówka wiadomości jest podobny do następującego (gdzie contoso.com jest nadawcą):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Aby uzyskać więcej informacji na temat nagłówka Authentication-Results, zobacz RFC 7001 ([Pole nagłówka komunikatu wskazujące stan uwierzytelniania komunikatu](https://www.rfc-editor.org/rfc/rfc7001.txt)). Implementacja DKIM firmy Microsoft jest zgodna z tą usługą RFC.

Administratorzy mogą tworzyć [reguły przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Exchange (nazywane również regułami transportu) na podstawie wyników weryfikacji DKIM. Te reguły przepływu poczty umożliwiają administratorom filtrowanie lub kierowanie wiadomości w razie potrzeby.
