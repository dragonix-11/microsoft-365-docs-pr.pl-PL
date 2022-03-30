---
title: Kolejność i pierwszeństwo ochrony poczty e-mail
keywords: zabezpieczenia, złośliwe oprogramowanie, Microsoft 365, M365, centrum zabezpieczeń, portal sieci Microsoft 365 Defender, program Microsoft Defender dla punktu końcowego, Microsoft Defender dla Office 365, Microsoft Defender for Identity
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
description: Administratorzy mogą dowiedzieć się więcej na temat kolejności aplikacji ochrony w u Exchange Online Protection (EOP) i jak wartość priorytetu w zasadach ochrony określa, które zasady są stosowane.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1debec0d2f8ca1498fd674f3d5a2d5a4681196eb
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679791"
---
# <a name="order-and-precedence-of-email-protection"></a>Kolejność i pierwszeństwo ochrony poczty e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online przychodzące wiadomości e-mail mogą być oflagowyane przez wiele rodzajów ochrony. Mogą Microsoft 365 przykład wbudowane zasady ochrony przed wyłudzaniem informacji w UOKI, które są dostępne dla wszystkich klientów usługi Microsoft 365, oraz bardziej zaawansowane zasady ochrony przed wyłudzaniem informacji, które są dostępne dla usługi Microsoft Defender dla Office 365 klientów. Wiadomości przechodzą również przez wiele wykrycia w poszukiwaniu złośliwego oprogramowania, spamu, wyłudzania informacji itp. Biorąc pod uwagę wszystkie te działania, mogą wystąpić pewne wątpliwości co do tego, które zasady są stosowane.

Ogólnie zasady stosowane do wiadomości są określone w nagłówku **X-Forefront-Antispam-Report** we właściwości **CAT (kategoria** ). Aby uzyskać więcej informacji, zobacz [Nagłówki wiadomości przed spamem](anti-spam-message-headers.md).

Istnieją dwa główne czynniki, które określają zasady stosowane do wiadomości:

- **Priorytet typu ochrony przed wiadomościami e-mail**: Tego zamówienia nie można konfigurować i jest opisane w poniższej tabeli:

  |Priority (Priorytet)|Ochrona poczty e-mail|Kategoria|Gdzie zarządzać|
  |---|---|---|---|
  |1|Złośliwe oprogramowanie|KOT:MALW|[Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w u usługi EOP](configure-anti-malware-policies.md)|
  |2|Wyłudzanie informacji|CAT:PHSH|[Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md)|
  |3|Duża pewność, że spam|CAT:HSPM|[Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md)|
  |4|Fałszowanie|CAT:SPOOF|[Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Personifikacja użytkownika (użytkownicy chronieni)|UIMP|[Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Personifikacja domeny (domeny chronione)|DIMP|[Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md)|
  |7|Spam|CAT:SPM|[Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md)|
  |8|Zbiorcze|KOT:ZBIORCZO|[Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md)|

  <sup>\*</sup>Te funkcje są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365.

- Priorytet **zasad: dla** każdego typu zasad (ochrony przed spamem, ochrony przed złośliwym oprogramowaniem, ochrony przed wyłudzaniem informacji itp.) obowiązują zasady domyślne dotyczące wszystkich użytkowników, ale można tworzyć zasady niestandardowe dotyczące konkretnych użytkowników. Każda zasada niestandardowa ma wartość priorytetu, która określa kolejność stosowania zasad. Zasady domyślne są zawsze stosowane na końcu.

  > [!IMPORTANT]
  > Jeśli użytkownik jest zdefiniowany w wielu zasadach tego samego typu, są do nich stosowane tylko zasady o najwyższym priorytecie. Wszelkie pozostałe zasady tego typu nie są obliczane dla użytkownika (w tym zasady domyślne).

Rozważ na przykład następujące zasady ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla systemu Office 365, które dotyczą tych samych **użytkowników, oraz** wiadomość, która jest identyfikowana zarówno jako personifikacja użytkownika, jak i spoofing:

|Nazwa zasad|Priority (Priorytet)|Personifikacja użytkownika|Ochrona przed fałszeringem|
|---|---|---|---|
|Zasady A|1|Wł.|Wyłączone|
|Zasady B|2|Wyłączone|Wł.|

1. Wiadomość jest oznaczona i traktowana jako fałsz, ponieważ fałszowanie ma wyższy priorytet (4) niż personifikacja użytkownika (5).
2. Zasady A są stosowane do użytkowników, ponieważ mają wyższy priorytet niż zasady B.
3. Na podstawie ustawień w zasadach A nie są podejmowane żadne akcje dotyczące wiadomości, ponieważ w tych zasadach jest wyłączona ochrona przed fałszowaniami.
4. Przetwarzanie zasad jest zatrzymane, więc zasady B nigdy nie są stosowane do użytkowników.

Ponieważ istnieje możliwość celowego lub niezamierzonego uwzględnionia tych samych użytkowników w wielu zasadach niestandardowych tego samego typu, należy użyć następujących wytycznych dotyczących projektowania zasad niestandardowych:

- Zasady, które mają zastosowanie do niewielkiej liczby użytkowników, mają wyższy priorytet, a zasady dotyczące dużej liczby użytkowników mają niższy priorytet. Pamiętaj, że zasady domyślne są zawsze stosowane jako ostatnie.
- Skonfiguruj zasady o wyższym priorytecie, aby ustawienia bardziej rygorystyczne lub bardziej specjalistyczne niż zasady o niższych priorytetach.
- Rozważ zastosowanie mniejszej liczby zasad niestandardowych (używaj zasad niestandardowych tylko w przypadku użytkowników wymagających bardziej rygorystycznych lub bardziej wyspecjalizowanych ustawień).
