---
title: Backscatter w usłudze EOP
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
description: W tym artykule dowiesz się więcej o usłudze Backscatter i Microsoft Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d132ed56c02989987da9e0ce32e7d4593e85e651
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648222"
---
# <a name="backscatter-in-eop"></a>Backscatter w usłudze EOP

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Backscatter to raporty* o braku dostarczania (nazywane również żądaniami NDR lub komunikatami odrzuceń), które są odbierane w przypadku wiadomości, które nie zostały wysłane. Backscatter jest spowodowane przez spamerów kucie (fałszowanie) z adresu (znany również jako `5322.From` adres lub P2) w swoich komunikatach. Spamerzy często używają prawdziwych adresów e-mail jako adresu Od, aby zwiększyć wiarygodność swoich wiadomości. Gdy spam jest wysyłany do nieistniejącego adresata, docelowy serwer poczty e-mail jest zasadniczo nakłaniany do zwrócenia niepożądanej wiadomości w NDR do sfałszowanego nadawcy w adresie Od.

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, EOP dokłada wszelkich starań, aby identyfikować i dyskretnie usuwać wiadomości z wątpliwych źródeł bez generowania protokołu NDR. Jednak w oparciu o samą ilość wiadomości e-mail przepływającej przez usługę, zawsze istnieje możliwość, że EOP przypadkowo wyśle zwrotne dane.

Backscatterer.org utrzymuje listę zablokowanych (nazywaną również listą blokową DNS lub DNSBL) serwerów poczty e-mail, które były odpowiedzialne za wysyłanie zaplecza, a serwery EOP mogą pojawić się na tej liście. Ale nie staramy się usunąć się z listy zablokowanych Backscatterer.org, ponieważ (według własnego uznania) ich lista nie jest listą spamerów.

> [!TIP]
> Witryna internetowa Backscatterer.org (<http://www.backscatterer.org/?target=usage>) zaleca korzystanie z usługi w trybie Sejf zamiast w trybie odrzucania, ponieważ duże usługi poczty e-mail prawie zawsze wysyłają pewne problemy.
