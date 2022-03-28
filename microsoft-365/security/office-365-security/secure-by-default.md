---
title: Domyślnie bezpieczne w aplikacji Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 06/28/2021
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Dowiedz się więcej o domyślnym ustawieniu zabezpieczeń w u Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 59f29b0e923bdeb7481a64fb9ba1c3890e2b1369
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775505"
---
# <a name="secure-by-default-in-office-365"></a>Domyślnie bezpieczne w aplikacji Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

"Domyślnie bezpieczne" to termin używany do definiowania najbezpieczniejszych ustawień domyślnych.

Jednak zabezpieczenia muszą być zrównoważone pod względami produktywności. Może to obejmować równoważenie na różnych platformach:

- **Użyteczność**: Ustawienia nie powinny być schowek w sposób zwiększający produktywność użytkowników.
- **Ryzyko**: Zabezpieczenia mogą blokować ważne działania.
- **Starsze ustawienia**: Niektóre konfiguracje starszych produktów i funkcji mogą wymagać obsługi ze względów biznesowych, nawet jeśli nowe, nowoczesne ustawienia zostały ulepszone.

Microsoft 365, w których skrzynki pocztowe są Exchange Online, są chronione przez Exchange Online Protection (EOP). Ta ochrona obejmuje:

- Wiadomość e-mail z podejrzanym złośliwym oprogramowaniem zostanie automatycznie poddana kwarantannie. Informacja o tym, czy adresaci są powiadamiani o wiadomościach poddanych kwarantannie złośliwego oprogramowania, jest kontrolowana przez zasady kwarantanny i ustawienia w zasadach ochrony przed złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w uchcie EOP](configure-anti-malware-policies.md).
- Wiadomości e-mail zidentyfikowane jako próby wyłudzenia dużej pewności będą obsługiwane zgodnie z działaniem zasad ochrony przed spamem. Zobacz [Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

Aby uzyskać więcej informacji na temat programu EOP, Exchange Online Protection [omówienie](exchange-online-protection-overview.md).

Firma Microsoft chce, aby klienci domyślnie zapewniali bezpieczeństwo, dlatego niektóre zastąpień dzierżaw nie są stosowane do złośliwego oprogramowania ani do wyłudzania informacji o wysokiej pewności. Oto niektóre z tych zastąpień:

- Listy dozwolonych nadawców lub dozwolonych domen (zasady ochrony przed spamem)
- Outlook Sejf nadawców
- Lista zezwalań adresów IP (filtrowanie połączeń)
- Exchange przepływu poczty e-mail (nazywane także regułami transportu)

Więcej informacji na temat tych zastępować można znaleźć w artykule Tworzenie [list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md).

> [!NOTE]
> Akcja Przenieś wiadomość do folderu Wiadomości-śmieci została wycofana w przypadku werdyktu wiadomości e-mail służącej do wyłudzania informacji (High **confidence phishing email**) w zasadach ochrony przed spamem usługi EOP. Zasady ochrony przed spamem, które używają tej akcji do wyłudzania informacji o dużej pewności, zostaną przekonwertowane na wiadomości **kwarantanny**. Akcja **Przekieruj wiadomość na adres e-mail** w celu wyłudzania informacji o wysokiej pewności pozostaje nienaruszona.

Opcja Bezpieczne domyślnie nie jest ustawieniem, które można włączać i wyłączać, ale filtrowanie działa poza polem, aby zachować potencjalnie niebezpieczne lub niechciane wiadomości ze skrzynek pocztowych. Wiadomości służące do wyłudzania informacji o wysokim poziomie pewności i złośliwego oprogramowania należy poddać kwarantannie. Domyślnie tylko administratorzy mogą zarządzać wiadomościami poddanymi kwarantannie jako złośliwe oprogramowanie lub wyłudzaniem informacji o wysokiej pewności, a także mogą zgłaszać wynik fałszywie dodatni firmie Microsoft. Aby uzyskać więcej informacji, zobacz [Zarządzanie poddatymi wiadomościami i plikami jako administrator w u usługi EOP](manage-quarantined-messages-and-files.md).

## <a name="more-on-why-were-doing-this"></a>Więcej informacji o tym, dlaczego to robisz

Istotą bezpieczeństwa domyślnie jest: to samo dzieje się w przypadku wiadomości, która zostałaby zrobiona, jeśli wiadomość była złośliwa, nawet jeśli skonfigurowano wyjątek, który pozwala na dostarczyć wiadomość. Jest to takie samo podejście, które zawsze było używane w przypadku złośliwego oprogramowania i teraz rozszerzamy to samo zachowanie na wiadomości służące do wyłudzania informacji o wysokiej pewności.

Nasze dane wskazują, że użytkownik jest 30 razy bardziej prawdopodobny, aby kliknąć złośliwy link w wiadomościach w folderze Wiadomości-śmieci, a nie w kwarantannie. Nasze dane również wskazują, że wskaźnik fałszywie dodatni (oznaczane jako złe wiadomości) dla wiadomości wyłudzających informacje o wysokiej pewności jest bardzo niski, a administratorzy mogą rozstrzygnieć wszelkie wyniki fałszywie dodatnie przy użyciu przesyłania administratora.

Ustaliliśmy również, że listy dozwolonych nadawców i domen w zasadach ochrony przed spamem oraz listy dozwolonych nadawców Sejf w programie Outlook były zbyt szerokie i powodowały więcej uszkodzenia niż dobre.

Aby to zrobić w inny sposób: jako usługa zabezpieczeń pracujemy w Twoim imieniu, aby zapobiec naruszenia bezpieczeństwa Twoich użytkowników.

## <a name="exceptions"></a>Wyjątki

Zastępowanie należy rozważyć tylko w następujących scenariuszach:

- Symulacyjne próby wyłudzania informacji: Symulowane ataki mogą ułatwić zidentyfikowanie użytkowników, którzy mogą być podatni na ataki, zanim prawdziwe ataki będą mieć wpływ na organizację. Aby zapobiec filtrowaniu wiadomości symulacyjnych wyłudzania informacji, zobacz Konfigurowanie prób wyłudzania informacji z innych firm [w zaawansowanych zasadach dostarczania](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).
- Skrzynki pocztowe zabezpieczeń/usługi SecOps: dedykowane skrzynki pocztowe używane przez zespoły zabezpieczeń do odfiltrowywowanych wiadomości (zarówno tych dobrych, jak i złych). Teams następnie sprawdzić, czy zawierają one złośliwą zawartość. Aby uzyskać więcej informacji, [zobacz Konfigurowanie skrzynek pocztowych usługi SecOps w zaawansowanych zasadach dostarczania](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Filtry innych firm: Domyślnie bezpieczne ma zastosowanie tylko wtedy, gdy dla rekordu MX domeny jest ustawiona wartość Exchange Online Protection (contoso.mail.protection.outlook.com). Jeśli jest ustawiona na inną usługę lub urządzenie, można domyślnie zastąpić ustawienie Bezpieczne regułą transportu, aby [](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) pominąć wszelkie filtrowanie spamu. Po wykryciu przez firmę Microsoft wiadomości z regułą "wysoka ufność" i w miejscu te wiadomości nadal odbierają wiadomości w Skrzynce odbiorczej. 
- Wyniki fałszywie dodatnie: możesz zezwolić tymczasowo na niektóre wiadomości, które są nadal analizowane przez firmę Microsoft za pośrednictwem [przesyłania przez administratora](admin-submission.md). Tak jak w przypadku wszystkich zastępować, zaleca się ich tymczasowe zastępowanie.
