---
title: Pule dostarczania połączeń wychodzących
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
ms.assetid: ac11edd9-2da3-462d-8ea3-bbf9dbc6f948
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak pule dostarczania są używane do ochrony reputacji serwerów poczty e-mail w Microsoft 365 centrach danych.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 273d105ca600face4d79d70fc1622dfce8bf9f5e
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403850"
---
# <a name="outbound-delivery-pools"></a>Pule dostarczania połączeń wychodzących

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Serwery poczty e-mail w Microsoft 365 danych mogą tymczasowo chcieć wysłać spam. Mogą to być na przykład złośliwe oprogramowanie lub złośliwy atak ze spamem w lokalnej organizacji poczty e-mail, który wysyła pocztę wychodzącą za pośrednictwem Microsoft 365 sieci Microsoft 365-mail. Atakujący próbują również unikać wykrywania przez przekazywanie wiadomości przez Microsoft 365 przekazywania dalej.

Takie scenariusze mogą spowodować, że adres IP Microsoft 365 serwera centrum danych wyświetlany na listach zablokowanych osób trzecich. Docelowe organizacje poczty e-mail, które korzystają z tych list zablokowanych, będą odrzucać wiadomości e-mail z tych Microsoft 365 wiadomości.

## <a name="high-risk-delivery-pool"></a>Pula dostarczania o wysokim poziomie ryzyka

Aby zapobiec blokowaniu naszych adresów IP, wszystkie wiadomości wychodzące z Microsoft 365 centrum danych, które są określone jako spam, są wysyłane przez pulę dostarczania _wysokiego ryzyka_.

Pula wiadomości wysokiego ryzyka to osobna pula adresów IP dla wychodzących wiadomości e-mail, która jest używana tylko do wysyłania wiadomości o niskiej jakości (na przykład spam i wiadomość typu [backscatter](backscatter-messages-and-eop.md)). Używanie puli wiadomości wysokiego ryzyka pomaga zapobiec wysyłaniu spamu przez zwykłego puli adresów IP dla wychodzących wiadomości e-mail. Normalna pula adresów IP dla wychodzących wiadomości e-mail utrzymuje reputację wysyłania wiadomości o "wysokiej jakości", co zmniejsza prawdopodobieństwo, że taki adres IP pojawi się na listach zablokowanych adresów IP.

Istnieje bardzo prawdopodobieństwo, że adresy IP w puli dostarczania o wysokim poziomie ryzyka zostaną umieszczone na listach zablokowanych adresów IP, ale jest to zaprojektowany. Dostarczanie do zamierzonych adresatów nie jest gwarantowane, ponieważ wiele organizacji poczty e-mail nie przyjmuje wiadomości z puli wiadomości wysokiego ryzyka.

Aby uzyskać więcej informacji, zobacz [Kontrolowanie spamu wychodzącego](outbound-spam-controls.md).

> [!NOTE]
> Wiadomości, w których źródłową domenę poczty e-mail nie ma rekordu A i nie zdefiniowano rekordu MX w publicznym systemie DNS, są zawsze kierowane przez pulę dostarczania wysokiego ryzyka, niezależnie od tego, czy mają adresy do spamu, czy wysyłania limitów.
>
> Wiadomości, które przekraczają następujące limity, są blokowane, więc nie są wysyłane przez pulę dostarczania wysokiego ryzyka:
>
> - [Limity wysyłania usługi](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).
> - [Zasady spamu wychodzącego](configure-the-outbound-spam-policy.md) , w przypadku których nadawcy mają ograniczone możliwości wysyłania poczty.

### <a name="bounce-messages"></a>Wiadomości podskakuje

Pula dostarczania połączeń wychodzących o wysokim poziomie ryzyka zarządza dostarczaniem dla wszystkich raportów o niedo dostarczenia (nazywanych również raportami o niedo dostarczenia, wiadomościami bounce, powiadomieniami o stanie dostarczenia lub powiadomieniami o stanie dostarczenia lub powiadomieniami o stanie dostarczenia).

Możliwe przyczyny wzrostu chwyt w pzp. dotyczące:

- Kampania spoofingowa, która dotyczy jednego z klientów korzystających z usługi.
- Ataki zbiorów katalogów.
- Atak ze spamem.
- A rogue email server.

Wszystkie te problemy mogą spowodować niespodziewanie zwiększenie liczby przetwarzanych przez usługę problemów. Wielokrotnie te powiadomienia o stanie realizacji wiadomości są spamem na innych serwerach i usługach _[e-mail (nazywanych także wiadomościami typu backscatter](backscatter-messages-and-eop.md)_).

### <a name="relay-pool"></a>Pula przekazywania

Wiadomości przesyłane dalej lub przekazywane za pośrednictwem programu Microsoft 365 w określonych scenariuszach będą wysyłane przy użyciu specjalnej puli przekazywania, ponieważ miejsce docelowe nie powinno uznać Microsoft 365 jako rzeczywistego nadawcy. Ważne jest odizolowanie tego ruchu poczty e-mail, ponieważ istnieją uzasadnione i nieprawidłowe scenariusze automatycznego przesyłania dalej lub przekazywania wiadomości e-mail z Microsoft 365. Podobnie jak w przypadku puli dostarczania o wysokim poziomie ryzyka do poczty przekazywanej jest używana osobna pula adresów IP. Ta pula adresów nie jest publikowana, ponieważ często się zmienia i nie jest częścią opublikowanego rekordu SPF dla Microsoft 365.

Microsoft 365 się, czy oryginalny nadawca jest legalny, aby można było pewnie dostarczyć wiadomość przesyłaną dalej.

Wiadomość przesyłana dalej lub przesyłana powinna spełniać jedno z następujących kryteriów, aby uniknąć korzystania z puli przekazywania:

- Nadawca ruchu wychodzącego znajduje się w [zaakceptowanym domenie](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- Spf passes when the message comes to Microsoft 365.
- DKIM w domenie nadawcy przechodzi po przyjściu wiadomości do Microsoft 365.

Można stwierdzić, że wiadomość została wysłana za pośrednictwem puli przekazywania, patrząc na adres IP serwera ruchu wychodzącego (pula przekazywania należy do zakresu 40.95.0.0/16) lub patrząc na nazwę serwera ruchu wychodzącego (będzie mieć nazwę "rly").

W przypadkach, gdy możemy uwierzytelnić nadawcę, używamy schematu ponownego redystrybowania nadawcy (SRS, Sender Rewriting Scheme), aby ułatwić systemowi poczty e-mail adresata powiadomienie, że wiadomość przesyłana dalej pochodzi z zaufanego źródła. Możesz przeczytać więcej o tym, jak to działa i co możesz zrobić, aby upewnić się, że wysyłająca domena przejdzie uwierzytelnianie w schemacie ponownego redytowania nadawców [(SRS, Sender Rewriting Scheme) w programie Office 365](/office365/troubleshoot/antispam/sender-rewriting-scheme).

Aby program DKIM działał, upewnij się, że włączyć funkcję DKIM dla wysyłania domeny. Na przykład fabrikam.com jest częścią contoso.com i jest zdefiniowany w zaakceptowanych domenach organizacji. Jeśli nadawca wiadomości jest sender@fabrikam.com, funkcja DKIM musi być włączona dla fabrikam.com. aby dowiedzieć się, jak włączyć tę funkcję, zobacz Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych [z domeny niestandardowej](use-dkim-to-validate-outbound-email.md).

Aby dodać domeny niestandardowe, wykonaj czynności opisane [w tece Dodawanie domeny do Microsoft 365](../../admin/setup/add-domain.md).

Jeśli rekord MX domeny wskazuje usługę innej firmy lub lokalnych serwerów poczty e-mail, należy użyć funkcji [rozszerzonego filtrowania dla łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors). Ulepszone filtrowanie zapewnia prawidłową weryfikację SPF dla poczty przychodzącej i pozwala uniknąć wysyłania wiadomości e-mail przez pulę przekazywania.
