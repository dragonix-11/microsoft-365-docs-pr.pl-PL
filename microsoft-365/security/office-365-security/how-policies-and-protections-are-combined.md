---
title: Kolejność i pierwszeństwo ochrony poczty e-mail
keywords: zabezpieczenia, złośliwe oprogramowanie, Microsoft 365, M365, Security Center, portal Microsoft 365 Defender, Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Microsoft Defender for Identity
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o kolejności ochrony aplikacji w Exchange Online Protection (EOP) oraz o tym, jak wartość priorytetu w zasadach ochrony określa, które zasady są stosowane.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8b7bf48de0939ec913982feb399b38dc2c540157
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417759"
---
# <a name="order-and-precedence-of-email-protection"></a>Kolejność i pierwszeństwo ochrony poczty e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych przychodzące wiadomości e-mail mogą być oflagowane przez wiele form ochrony. Na przykład wbudowane zasady ochrony przed wyłudzaniem informacji dostępne dla wszystkich Microsoft 365 klientów oraz bardziej niezawodne zasady ochrony przed wyłudzaniem informacji, które są dostępne dla Ochrona usługi Office 365 w usłudze Microsoft Defender klientów. Komunikaty przechodzą również przez wiele skanów wykrywania złośliwego oprogramowania, spamu, wyłudzania informacji itp. Biorąc pod uwagę wszystkie te działania, może wystąpić pewne nieporozumienie co do tego, które zasady są stosowane.

Ogólnie rzecz biorąc, zasady stosowane do komunikatu są identyfikowane w nagłówku **X-Forefront-Antispam-Report** we właściwości **CAT (Kategoria** ). Aby uzyskać więcej informacji, zobacz [Nagłówki wiadomości antyspamowych](anti-spam-message-headers.md).

Istnieją dwa główne czynniki, które określają, które zasady są stosowane do komunikatu:

- **Kolejność przetwarzania dla typu ochrony poczty e-mail**: to zamówienie nie jest konfigurowalne i jest opisane w poniższej tabeli:

  |Zamówienia|Ochrona poczty e-mail|Kategoria|Gdzie zarządzać|
  |:---:|---|---|---|
  |1|Złośliwego oprogramowania|CAT:MALW|[Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach operacji EOP](configure-anti-malware-policies.md)|
  |2|Wyłudzanie informacji|CAT:PHSH|[Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md)|
  |3|Spam o wysokim poziomie ufności|CAT:HSPM|[Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md)|
  |4|Fałszowanie|CAT:SPOOF|[Fałszowanie szczegółowych informacji wywiadowczych w ramach EOP](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Personifikacja użytkownika (użytkownicy chronieni)|UIMP|[Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Personifikacja domeny (domeny chronione)|DIMP|[Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md)|
  |7|Spam|CAT:SPM|[Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md)|
  |8|Zbiorczego|CAT:BULK|[Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md)|

  <sup>\*</sup>Te funkcje są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender.

- **Priorytet zasad**: dla każdego typu zasad (antyspamowych, chroniących przed złośliwym oprogramowaniem, chroniących przed wyłudzaniem informacji itp.) istnieją zasady domyślne, które mają zastosowanie do wszystkich użytkowników, ale można utworzyć niestandardowe zasady, które mają zastosowanie do określonych użytkowników (adresatów). Każda zasada niestandardowa ma wartość priorytetu, która określa kolejność stosowania zasad. Domyślne zasady są zawsze stosowane jako ostatnie.

  > [!IMPORTANT]
  > Jeśli adresat jest zdefiniowany w wielu zasadach tego samego typu (anty-spam, ochrona przed wyłudzaniem informacji itp.), tylko zasady o najwyższym priorytecie są stosowane do adresata. Wszystkie pozostałe zasady tego typu nie są oceniane dla odbiorcy (w tym zasady domyślne).

Rozważmy na przykład następujące **zasady ochrony przed wyłudzaniem informacji** w Ochrona usługi Office 365 w usłudze Microsoft Defender **, które mają zastosowanie do tych samych użytkowników**, oraz komunikat, który jest identyfikowany jako **personifikacja i fałszowanie użytkowników**:

|Nazwa zasad|Priority (Priorytet)|Personifikacja użytkownika|Ochrona przed fałszowaniem|
|---|:---:|:---:|:---:|
|Zasady A|1|Na|Wył.|
|Zasady B|2|Wył.|Na|

1. Komunikat jest identyfikowany jako fałszowanie, ponieważ fałszowanie (4) jest oceniane przed personifikacją użytkownika (5).
2. Zasady A są stosowane jako pierwsze, ponieważ mają wyższy priorytet niż zasady B.
3. Na podstawie ustawień w zasadach A nie jest podejmowana żadna akcja dotycząca komunikatu, ponieważ funkcja ochrony przed fałszowaniem jest wyłączona.
4. Przetwarzanie zasad ochrony przed wyłudzaniem informacji zatrzymuje się dla wszystkich uwzględnionych adresatów, dlatego zasady B nigdy nie są stosowane do adresatów, którzy również znajdują się w zasadach A.

Ponieważ ci sami użytkownicy mogą być celowo lub przypadkowo uwzględnieni w wielu zasadach tego samego typu, skorzystaj z następujących wytycznych dotyczących projektowania zasad niestandardowych:

- Przypisz wyższy priorytet do zasad, które mają zastosowanie do niewielkiej liczby użytkowników, i niższy priorytet zasad, które mają zastosowanie do dużej liczby użytkowników. Pamiętaj, że domyślne zasady są zawsze stosowane jako ostatnie.
- Skonfiguruj zasady o wyższym priorytecie, aby miały bardziej rygorystyczne lub bardziej wyspecjalizowane ustawienia niż zasady o niższym priorytecie.
- Rozważ użycie mniejszej liczby zasad niestandardowych (używaj tylko zasad niestandardowych dla użytkowników, którzy wymagają bardziej rygorystycznych lub bardziej wyspecjalizowanych ustawień).
