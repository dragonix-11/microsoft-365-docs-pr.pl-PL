---
title: Poziom ufności spamu
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
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o poziomie ufności spamu (SCL) stosowanym do wiadomości w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8febc1d0e0c4fd98b33fb0016beee89a30802241
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647914"
---
# <a name="spam-confidence-level-scl-in-eop"></a>Poziom ufności spamu (SCL) w funkcji EOP

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, wiadomości przychodzące przechodzą przez filtrowanie spamu w ramach EOP i otrzymują ocenę spamu. Ten wynik jest mapowany na indywidualny poziom ufności spamu (SCL), który jest dodawany do wiadomości w nagłówku X. Wyższa lista SCL wskazuje, że komunikat jest bardziej prawdopodobny jako spam. EOP podejmuje akcję na podstawie komunikatu na podstawie listy SCL.

Co oznacza lista SCL i domyślne akcje podejmowane w komunikatach, opisano w poniższej tabeli. Aby uzyskać więcej informacji na temat akcji, które można podjąć w przypadku wiadomości opartych na werdykcie filtrowania spamu, zobacz [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).

|SCL|Definicja|Akcja domyślna|
|:---:|---|---|
|-1|Komunikat pominął filtrowanie spamu. Na przykład wiadomość pochodzi od bezpiecznego nadawcy, została wysłana do bezpiecznego adresata lub pochodzi z serwera źródłowego poczty e-mail na liście dozwolonych adresów IP. Aby uzyskać więcej informacji, zobacz [Tworzenie list bezpiecznych nadawców w ramach EOP](create-safe-sender-lists-in-office-365.md).|Dostarczenie wiadomości do skrzynki odbiorczej adresatów.|
|0, 1|Filtrowanie spamu ustaliło, że wiadomość nie była spamem.|Dostarczenie wiadomości do skrzynki odbiorczej adresatów.|
|5, 6|Filtrowanie spamu oznacza wiadomość jako **spam**|Dostarczenie wiadomości do folderu wiadomości-śmieci adresatów.|
|9|Filtrowanie spamu oznacza wiadomość jako **spam o wysokim poziomie ufności**|Dostarczenie wiadomości do folderu wiadomości-śmieci adresatów.|

Zauważysz, że lista SCL 2, 3, 4, 7 i 8 nie jest używana przez filtrowanie spamu.

Reguły przepływu poczty (znane również jako reguły transportu) umożliwiają ostemplowanie listy SCL w wiadomościach. Jeśli używasz reguły przepływu poczty do ustawienia listy SCL, wartości 5 lub 6 wyzwalają akcję filtrowania spamu dla **spamu**, a wartości 7, 8 lub 9 wyzwalają akcję filtrowania spamu dla **spamu o wysokim poziomie ufności**. Aby uzyskać więcej informacji, zobacz [Używanie reguł przepływu poczty do ustawiania poziomu ufności spamu (SCL) w wiadomościach](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Podobnie jak w przypadku listy SCL, poziom skarg zbiorczych (BCL) identyfikuje nieprawidłową zbiorczą wiadomość e-mail (znaną również jako _szara poczta_). Wyższa lista BCL wskazuje, że wiadomość e-mail zbiorcza jest bardziej skłonna do generowania skarg (i dlatego jest bardziej prawdopodobna jako spam). Próg listy BCL można skonfigurować w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w EOP](configure-your-spam-filter-policies.md), [Poziom skarg zbiorczych (BCL) w EOP)](bulk-complaint-level-values.md) i [Jaka jest różnica między wiadomościami-śmieciami a wiadomościami e-mail zbiorczymi?](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![Ikona skrótu do usługi LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Nowość w Microsoft 365?** Odkryj bezpłatne kursy wideo dla **administratorów Microsoft 365 i specjalistów IT**, które zostały ci przywiezione przez Edukacja LinkedIn.
