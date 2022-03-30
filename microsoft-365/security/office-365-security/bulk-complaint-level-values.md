---
title: Zbiorcze wartości poziomu skarg
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
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się więcej o wartościach zbiorczych skarg (BCL, Bulk Complaint Level) używanych w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8c50ca25a355ca142e36c67d03fad42c3aa461a2
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679879"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Zbiorcza skarga (BCL) w uścisce EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online usługi EOP przypisywany jest poziom skarg zbiorczych do wiadomości przychodzących od poczty masowej. Wartość BCL jest dodawana do wiadomości w nagłówku X i przypomina poziom ufności filtru spamu [,](spam-confidence-levels.md) który służy do identyfikowania wiadomości jako spamu. Wyższa wartość BCL wskazuje, że wiadomość zbiorcza z większą prawdopodobieństwem generuje skargi (i dlatego jest bardziej prawdopodobna jako spam). Firma Microsoft używa zarówno źródeł wewnętrznych, jak i zewnętrznych do identyfikowania poczty masowej i ustalania odpowiedniej listy BCL.

Rozsyłanie zbiorcze różni się we wzorcach wysyłania, tworzeniu zawartości i pozyskiwaniu adresatów. Dobra masowa korespondencja pocztowa wysyła wymagane wiadomości z odpowiednią zawartością do swoich subskrybentów. Te wiadomości generują kilka skarg od adresatów. Inne osoby poczty masowej wysyłają niechciane wiadomości, które bardzo przypominają spam, i generują wiele skarg adresatów. Wiadomości od poczty masowej są nazywane pocztą masową lub szarymi wiadomościami.

 Filtrowanie spamu oznacza wiadomości  jako zbiorcze wiadomości e-mail na podstawie progu BCL (wartości domyślnej lub określonej przez Ciebie) i podejmuje określone działanie w określonej wiadomości (domyślną akcją jest dostarczenie wiadomości do folderu wiadomości-śmieci adresata). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md) oraz Jaka jest różnica między wiadomościami-śmieciami [a masową pocztą e-mail?](what-s-the-difference-between-junk-email-and-bulk-email.md)

Progi BCL opisano w poniższej tabeli.

|BCL|Opis|
|:---:|---|
|0|Wiadomość nie pochodzi od nadawcy zbiorczego.|
|1, 2, 3|Wiadomość pochodzi od nadawcy masowego, który wygeneruje kilka skarg.|
|4, 5, 6, 7<sup>\*</sup>|Wiadomość pochodzi od nadawcy masowego, który generuje różne skargi.|
|8, 9|Wiadomość pochodzi od nadawcy masowego, który generuje dużą liczbę skarg.|

<sup>\*</sup> Jest to domyślna wartość progowa używana w zasadach ochrony przed spamem.
