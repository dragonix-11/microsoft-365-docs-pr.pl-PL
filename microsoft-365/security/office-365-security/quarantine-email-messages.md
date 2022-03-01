---
title: Poddaj kwarantannie wiadomości e-mail
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 4c234874-015e-4768-8495-98fcccfc639b
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą uzyskać informacje na temat kwarantanny Exchange Online Protection (EOP), która zawiera potencjalnie niebezpieczne lub niechciane wiadomości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 509e093d1618cf17d8f5f880aa82a2c54e8204bf
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996222"
---
# <a name="quarantined-email-messages-in-eop-and-defender-for-office-365"></a>Poddaj kwarantannie wiadomości e-mail w usługach EOP i Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub organizacji autonomicznych usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online dostęp do kwarantanny może zawierać potencjalnie niebezpieczne lub niechciane wiadomości.

Zasady ochrony przed złośliwym oprogramowaniem automatycznie poddaj wiadomości *kwarantannie,* jeśli załącznik zawiera złośliwe oprogramowanie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w uchcie EOP](configure-anti-malware-policies.md).

Domyślnie policy antyspamowe poddają wiadomości służące do wyłudzania informacji o dużej pewności, a także wysyłają spam, spam o dużej pewności i zbiorcze wiadomości e-mail do folderu wiadomości-śmieci użytkownika. Możesz jednak również tworzyć i dostosowywać zasady ochrony przed spamem w celu kwarantanny spamu, spamu o dużej pewności i zbiorczej poczty e-mail. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

Z wiadomościami poddanymi kwarantannie mogą pracować zarówno użytkownicy, jak i administratorzy:

- _Zasady kwarantanny_ określają, co użytkownicy mogą, a czego nie mogą robić w kwarantannie wiadomości w zależności od tego, dlaczego wiadomość została poddana kwarantannie (dla obsługiwanych funkcji). Domyślne zasady kwarantanny wymuszają funkcje historyczne zgodnie z poniższym opisem. Administratorzy mogą tworzyć i stosować niestandardowe zasady kwarantanny, które definiują mniej restrykcyjne lub bardziej restrykcyjne funkcje dla użytkowników, a także włączać powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

- Administratorzy mogą pracować ze wszystkimi typami wiadomości poddanych kwarantannie dla wszystkich użytkowników. Domyślnie tylko administratorzy mogą pracować z wiadomościami poddanymi kwarantannie jako złośliwe oprogramowanie, wyłudzaniem dużej pewności lub ze względu na reguły przepływu poczty (nazywane także regułami transportu). Aby uzyskać więcej informacji, zobacz [Zarządzanie poddatymi wiadomościami i plikami jako administrator w u usługi EOP](manage-quarantined-messages-and-files.md).

- Domyślnie użytkownicy mogą pracować z wiadomościami poddanymi kwarantannie, do których są adresatami, a wiadomość została poddana kwarantannie jako spam, zbiorcza poczta e-mail lub wyłudzanie informacji (bez wysokiej pewności, wyłudzanie informacji). Aby uzyskać więcej informacji, zobacz Znajdowanie i zwalnianie poddanych [kwarantannie wiadomości jako użytkownik w u kontie EOP](find-and-release-quarantined-messages-as-a-user.md).

  Aby uniemożliwić użytkownikom zarządzanie własnymi wiadomościami wyłudzających informacje poddanymi kwarantannie, administratorzy mogą przypisać zasady kwarantanny, które  uniemożliwiają dostęp do kwarantanny wiadomości z werdyktu filtrowania wiadomości wyłudzających informacje w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Przypisywanie zasad kwarantanny w zasadach ochrony przed](quarantine-policies.md#anti-spam-policies) spamemKranowe [zasady](quarantine-policies.md).

- Administratorzy i użytkownicy mogą raportować wyniki fałszywie dodatnie firmie Microsoft w kwarantannie.

- Czas, przez jaki wiadomości poddane kwarantannie są przechowywane w kwarantannie, zanim wygaśnie, zależy od tego, dlaczego wiadomość została poddana kwarantannie. Funkcje kwarantanny wiadomości i odpowiadające im okresy przechowywania są opisane w poniższej tabeli:

  <br>

  ****

  |Powód kwarantanny|Domyślny okres przechowywania|Możliwość dostosowania?|Komentarze|
  |---|---|:---:|---|
  |Wiadomości poddane kwarantannie według zasad ochrony przed spamem: spam, spam o dużej pewności, wyłudzanie informacji, próby wyłudzenia dużej pewności lub zbiorcze.|15 dni: <ul><li>W domyślnych zasadach ochrony przed spamem.</li><li>W zasadach ochrony przed spamem tworzyć w programie PowerShell.</li></ul> <p> 30 dni w zasadach ochrony przed spamem tworzyć w portalu Microsoft 365 Defender wiadomości.|Tak|Tę wartość można skonfigurować w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz ustawienie Zachowaj **spam** w kwarantannie przez tę wiele dni (_QuarantineRetentionPeriod_) w tece Konfigurowanie zasad ochrony [przed spamem](configure-your-spam-filter-policies.md).|
  |Wiadomości poddanych kwarantannie przez zasady ochrony przed wyłudzaniem informacji: fałszerska ochrona przed fałszerami w uciekowoniu EOP; personifikacja użytkownika, personifikacja domeny lub inteligencja skrzynek pocztowych w uchcie Defender dla Office 365.|30 dni|Tak|Ten okres przechowywania jest również kontrolowany przez ustawienie Zachowaj **spam** w kwarantannie przez tę wiele dni (_QuarantineRetentionPeriod_) w zasadach ochrony **przed spamem** . Używany okres przechowywania to wartość z pierwszej zdefiniowanej przez adresata zasady ochrony przed **spamem** .|
  |Wiadomości poddane kwarantannie przez zasady ochrony przed złośliwym oprogramowaniem (wiadomości złośliwego oprogramowania).|15 dni|Nie||
  |Wiadomości poddane kwarantannie przez Sejf Zasady załączników w programie Defender Office 365 wiadomości (wiadomości złośliwego oprogramowania).|15 dni|Nie||
  |Wiadomości poddane kwarantannie według reguł przepływu poczty: akcja to Dostarczanie wiadomości do **hostowanej** kwarantanny (_Kwarantanna_).|30 dni|Nie||
  |Pliki poddane kwarantannie przez Sejf załączników do SharePoint, OneDrive i Microsoft Teams (plików złośliwego oprogramowania).|15 dni|Nie||
  |

  Gdy wiadomość wygaśnie z kwarantanny, nie można jej odzyskać.

Aby uzyskać więcej informacji na temat kwarantanny, zobacz [Kwarantanna — często zadawane pytania](quarantine-faq.yml).
