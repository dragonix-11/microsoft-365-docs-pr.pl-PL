---
title: Wiadomość backscatter w uchwale EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: W tym artykule dowiesz się więcej na temat zabezpieczeń Backscatter i Microsoft Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79a6dd1be6c33bdbfc3d87b834f231de7cd08a0c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986439"
---
# <a name="backscatter-in-eop"></a>Wiadomość backscatter w uchwale EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Wiadomość typu backscatter* to raporty o niedo dostarczenia (znane również jako raporty o niedo dostarczenia lub wiadomości przychodzące), które otrzymujesz za wiadomości, które nie wysłaliśmy. Backscatter jest powodowany przez spamerów podszywających się pod adres Od ( `5322.From` nazywany również adresami P2) w ich wiadomościach. Spamerzy często używają prawdziwych adresów e-mail jako adresu Od w celu wiarygodności swoich wiadomości. Gdy spam jest wysyłany do nieistniejącego adresata, docelowy serwer poczty e-mail w zasadzie musi zwrócić nie można dostarczyć wiadomości w wiadomości o niedostarczeniu do nadawcy, który został zafałszowany, w adresie Od.

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online program EOP podejmuje wszelkie starania w celu identyfikowania i dyskretnego upuszczania wiadomości z nazwanych źródeł bez generowania nDR. Jednak w zależności od tego, że przez usługę przepływa wiadomość e-mail z dużą głośnością, zawsze może się  to ając, że usługa EOP nieumyślnie wyśle wiadomość backscatter.

Backscatterer.org przechowuje listę zablokowanych serwerów poczty e-mail (znaną także jako lista zablokowanych adresów DNS lub DNSBL) serwerów poczty e-mail, które były odpowiedzialne za wysyłanie wiadomości backscatter, a serwery usługi EOP mogą być wyświetlane na tej liście. Jednak nie staramy się usuwać naszych Backscatterer.org z listy zablokowanych osób, ponieważ nie są to listy spamerów z ich listy (z powodu ich własnego niechciania).

> [!TIP]
> Witryna Backscatterer.org-mail (<http://www.backscatterer.org/?target=usage>) zaleca używanie ich usługi w trybie Sejf zamiast w trybie odrzuć, ponieważ duże usługi poczty e-mail prawie zawsze wysyłają niektóre wiadomości w trybie backscatter.
