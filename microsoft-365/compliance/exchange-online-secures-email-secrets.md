---
title: Jak Exchange Online sekrety poczty e-mail
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 07/01/2019
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 989ba10c-f73f-4efb-ad1b-af3322e5f376
ms.collection:
- M365-security-compliance
description: Oprócz Centrum zaufania usługi Office 365, które udostępnia informacje o zabezpieczeniach, prywatności i zgodności dla oprogramowania Microsoft 365, warto wiedzieć, w jaki sposób firma Microsoft pomaga chronić tajemnice przechowywane w jej centrach danych. Korzystamy z technologii o nazwie DKM (Distributed Key Manager).
ms.openlocfilehash: a1d939ebfc1ecba1e7cb8b97111f677f754894b1
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019342"
---
# <a name="how-exchange-online-secures-your-email-secrets"></a>Jak Exchange Online sekrety poczty e-mail

W tym artykule opisano, jak firma Microsoft zabezpiecza sekrety poczty e-mail w jej centrach danych.
  
## <a name="how-do-we-secure-secret-information-provided-by-you"></a>Jak zabezpieczamy poufne informacje dostarczone przez Ciebie?

Oprócz Centrum zaufania usługi Office 365, które udostępnia informacje o zabezpieczeniach, prywatności i zgodności dla usługi [Office 365](./get-started-with-service-trust-portal.md), warto wiedzieć, w jaki sposób firma Microsoft chroni tajemnice udostępniane przez Ciebie w swoich centrach danych. Korzystamy z technologii o nazwie DKM (Distributed Key Manager).
  
[DKM (Distributed Key Manager](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) ) to funkcja po stronie klienta, która używa zestawu tajnych kluczy do szyfrowania i odszyfrowywania informacji. Dostęp do tych kluczy mogą uzyskać tylko członkowie określonej grupy zabezpieczeń Usługi domenowe w usłudze Active Directory w celu odszyfrowania danych zaszyfrowanych przez DKM. W Exchange Online zabezpieczeń do tej grupy zabezpieczeń są Exchange tylko niektóre konta usług, w ramach których są uruchamiane te procesy. W ramach standardowej procedury operacyjnej w centrum danych nie są podano poświadczeń ludzkich, które są częścią tej grupy zabezpieczeń, dlatego nikt nie ma dostępu do kluczy, które mogą odszyfrowywać te tajemnice.
  
W celu debugowania, rozwiązywania problemów lub inspekcji administrator centrum danych musi zażądać podwyższonym poziom dostępu, aby uzyskać tymczasowe poświadczenia, które są częścią grupy zabezpieczeń. Ten proces wymaga zatwierdzenia przez wiele poziomów prawnych. W przypadku uzyskania dostępu wszystkie działania są rejestrowane i rejestrowane oraz rejestrowane w dzienniku inspekcji. Ponadto dostęp jest udzielany tylko dla ustawionego interwału, po którym automatycznie wygasa.
  
W celu dodatkowej ochrony technologia DKM obejmuje automatyczne wycofywanie i archiwizowanie kluczy. Dzięki temu nadal będzie można uzyskać dostęp do starszej zawartości bez konieczności polegania na tym samym kluczu w nieskończoność.
  
## <a name="where-does-exchange-online-make-use-of-dkm"></a>Gdzie Exchange Online korzystać z DKM?

Firma Microsoft używa [Menedżera kluczy rozłożonych](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) w celu szyfrowania twoich sekretów Exchange Online w centrach danych. Przykład:
  
- Poświadczenia konta e-mail dla połączonych kont. Połączone konta to konta innych firm, takie jak Hotmail, Gmail i Yahoo! mail.

- Klucz klienta. Jeśli używasz szyfrowania usługi [z kluczem klienta](customer-key-overview.md), użyjesz magazynu kluczy platformy [Azure](/azure/key-vault/key-vault-whatis) do zabezpieczenia swoich sekretów.

## <a name="related-topics"></a>Tematy pokrewne

[Szyfrowanie w Office 365](encryption.md)
  
[Informacje techniczne dotyczące szyfrowania](technical-reference-details-about-encryption.md)
  
[Zapewnianie ochrony usługi w Centrum &amp; zgodności zabezpieczeń](./service-assurance.md)
