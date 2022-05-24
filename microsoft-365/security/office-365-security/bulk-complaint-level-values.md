---
title: Wartości poziomu skarg zbiorczych
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
description: Administratorzy mogą dowiedzieć się więcej o wartościach na poziomie skarg zbiorczych (BCL), które są używane w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 08e747b704faa18aa73110256624d70c79d0307b
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647386"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Poziom skarg zbiorczych (BCL) w ramach EOP

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, usługa EOP przypisuje poziom skarg zbiorczych (BCL) do wiadomości przychodzących z wiadomości zbiorczych. Lista BCL jest dodawana do wiadomości w nagłówku X i jest podobna do [poziomu ufności spamu (SCL),](spam-confidence-levels.md) który jest używany do identyfikowania wiadomości jako spamu. Wyższa lista BCL wskazuje, że komunikat zbiorczy jest bardziej skłonny do generowania skarg (i dlatego jest bardziej prawdopodobne, że jest spamem). Firma Microsoft używa źródeł wewnętrznych i innych firm do identyfikowania poczty zbiorczej i określania odpowiedniej listy BCL.

Nadawcy zbiorczi różnią się wzorcami wysyłania, tworzeniem zawartości i praktykami pozyskiwania adresatów. Dobre zbiorcze nadawcy wysyłają żądane wiadomości z odpowiednią zawartością do swoich subskrybentów. Te komunikaty generują kilka skarg od adresatów. Inne wiadomości zbiorcze wysyłają niechciane wiadomości, które bardzo przypominają spam i generują wiele skarg od adresatów. Wiadomości od nadawcy zbiorczego są nazywane pocztą zbiorczą lub szarą pocztą.

 Filtrowanie spamu oznacza wiadomości jako **zbiorczą wiadomość e-mail** na podstawie progu listy BCL (wartość domyślna lub określona wartość) i podejmuje określoną akcję w wiadomości (domyślną akcją jest dostarczenie wiadomości do folderu Wiadomości-śmieci odbiorcy). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md) i [Jaka jest różnica między wiadomościami-śmieciami a wiadomościami e-mail zbiorczymi?](what-s-the-difference-between-junk-email-and-bulk-email.md)

Progi listy BCL zostały opisane w poniższej tabeli.

|BCL|Opis|
|:---:|---|
|0|Wiadomość nie pochodzi od nadawcy zbiorczego.|
|1, 2, 3|Wiadomość pochodzi od nadawcy zbiorczego, który generuje kilka skarg.|
|4, 5, 6, 7<sup>\*</sup>|Wiadomość pochodzi od nadawcy zbiorczego, który generuje mieszaną liczbę skarg.|
|8, 9|Wiadomość pochodzi od nadawcy zbiorczego, który generuje dużą liczbę skarg.|

<sup>\*</sup> Jest to domyślna wartość progowa używana w zasadach ochrony przed spamem.
