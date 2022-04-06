---
title: Domyślnie zabezpieczanie w Office 365
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
description: Dowiedz się więcej o domyślnym ustawieniu zabezpieczeń w Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 09395775cc5ecbd420dc7197664401c01c24d6c3
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664221"
---
# <a name="secure-by-default-in-office-365"></a>Domyślnie zabezpieczanie w Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

"Domyślnie bezpieczne" to termin używany do definiowania ustawień domyślnych, które są najbezpieczniejsze, jak to możliwe.

Jednak bezpieczeństwo musi być zrównoważone z wydajnością. Może to obejmować równoważenie między:

- **Użyteczność**: Ustawienia nie powinny stać na drodze do produktywności użytkowników.
- **Ryzyko**: Zabezpieczenia mogą blokować ważne działania.
- **Starsze ustawienia**: Niektóre konfiguracje starszych produktów i funkcji mogą wymagać konserwacji ze względów biznesowych, nawet jeśli nowe, nowoczesne ustawienia zostaną ulepszone.

Microsoft 365 organizacje ze skrzynkami pocztowymi w Exchange Online są chronione przez Exchange Online Protection (EOP). Ta ochrona obejmuje:

- Wiadomość e-mail z podejrzeniem złośliwego oprogramowania zostanie automatycznie poddana kwarantannie. To, czy adresaci są powiadamiani o komunikatach o złośliwym oprogramowaniu poddanym kwarantannie, jest kontrolowane przez zasady kwarantanny i ustawienia zasad ochrony przed złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach EOP](configure-anti-malware-policies.md).
- Wiadomość e-mail zidentyfikowana jako wyłudzająca informacje o wysokim poziomie zaufania będzie obsługiwana zgodnie z akcją zasad ochrony przed spamem. Zobacz [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).

Aby uzyskać więcej informacji na temat EOP, zobacz [omówienie Exchange Online Protection](exchange-online-protection-overview.md).

Ponieważ firma Microsoft chce domyślnie zapewnić bezpieczeństwo naszym klientom, niektóre przesłonięcia dzierżaw nie są stosowane w przypadku złośliwego oprogramowania ani wyłudzania informacji o wysokim poziomie zaufania. Te przesłonięcia obejmują:

- Listy dozwolonych nadawców lub listy dozwolonych domen (zasady ochrony przed spamem)
- nadawcy Outlook Sejf
- Lista dozwolonych adresów IP (filtrowanie połączeń)
- Exchange reguł przepływu poczty (znanej również jako reguły transportu)

Więcej informacji na temat tych przesłoń można znaleźć na [stronie Tworzenie list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md).

> [!NOTE]
> Wycofaliśmy akcję **Przenoszenie wiadomości do folderu Wiadomości-śmieci** dla werdyktu **wiadomości e-mail o wysokim poziomie ufności** w zasadach ochrony przed spamem w ramach EOP. Zasady ochrony przed spamem, które używają tej akcji do wyłudzania informacji o wysokim poziomie zaufania, zostaną przekonwertowane na **komunikaty kwarantanny**. Akcja **Przekierowanie wiadomości do adresu e-mail** w przypadku wiadomości wyłudzających informacje o wysokim poziomie ufności nie ma wpływu.

Ustawienie Bezpieczne domyślnie nie jest ustawieniem, które można włączyć lub wyłączyć, ale jest to sposób, w jaki nasze filtrowanie działa po wyczyszczeniu, aby zachować potencjalnie niebezpieczne lub niechciane wiadomości poza skrzynkami pocztowymi. Złośliwe oprogramowanie i wiadomości wyłudzające informacje o wysokim poziomie zaufania powinny zostać poddane kwarantannie. Domyślnie tylko administratorzy mogą zarządzać komunikatami, które zostały poddane kwarantannie jako złośliwe oprogramowanie lub wyłudzanie informacji o wysokim poziomie zaufania, a także mogą zgłaszać fałszywe alarmy firmie Microsoft stamtąd. Aby uzyskać więcej informacji, zobacz [Manage quarantined messages and files as an admin in EOP (Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w ramach EOP](manage-quarantined-messages-and-files.md)).

## <a name="more-on-why-were-doing-this"></a>Więcej informacji na temat tego, dlaczego to robimy

Domyślnym duchem bezpieczeństwa jest: podejmujemy tę samą akcję względem komunikatu, który należy wykonać, jeśli wiadomo, że komunikat jest złośliwy, nawet jeśli skonfigurowany wyjątek w przeciwnym razie zezwoli na dostarczenie komunikatu. Jest to takie samo podejście, które zawsze stosowaliśmy w przypadku złośliwego oprogramowania, a teraz rozszerzamy to samo zachowanie na wiadomości wyłudzające informacje o wysokim poziomie zaufania.

Nasze dane wskazują, że użytkownik jest 30 razy bardziej skłonny do kliknięcia złośliwego linku w wiadomościach w folderze Wiadomości-śmieci w porównaniu z kwarantanną. Nasze dane wskazują również, że wskaźnik fałszywie dodatni (dobre komunikaty oznaczone jako złe) dla wiadomości wyłudzających informacje o wysokim poziomie pewności jest bardzo niski, a administratorzy mogą rozpoznać wszelkie fałszywie dodatnie dane przy użyciu przesłanych przez administratorów.

Ustaliliśmy również, że dozwolony nadawca i listy dozwolonych domen w zasadach ochrony przed spamem i Sejf nadawców w Outlook są zbyt szerokie i wyrządzają więcej szkody niż pożytku.

Mówiąc inaczej: jako usługa zabezpieczeń działamy w Twoim imieniu, aby uniemożliwić użytkownikom naruszenie zabezpieczeń.

## <a name="exceptions"></a>Wyjątki

Należy rozważyć użycie przesłonięcia tylko w następujących scenariuszach:

- Symulacje wyłudzania informacji: symulowane ataki mogą pomóc w identyfikacji narażonych użytkowników, zanim rzeczywisty atak wpłynie na organizację. Aby zapobiec filtrowaniu komunikatów symulacji wyłudzania informacji, zobacz [Konfigurowanie symulacji wyłudzania informacji innych firm w zaawansowanych zasadach dostarczania](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).
- Skrzynki pocztowe zabezpieczeń/SecOps: dedykowane skrzynki pocztowe używane przez zespoły zabezpieczeń do pobierania niefiltrowanych wiadomości (zarówno dobrych, jak i złych). Teams następnie sprawdzić, czy zawierają złośliwą zawartość. Aby uzyskać więcej informacji, zobacz [Konfigurowanie skrzynek pocztowych SecOps w zaawansowanych zasadach dostarczania](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Filtry innych firm: Zabezpieczenia domyślnie mają zastosowanie tylko wtedy, gdy rekord MX dla domeny jest ustawiony na Exchange Online Protection (contoso.mail.protection.outlook.com). Jeśli jest ona ustawiona na inną usługę lub urządzenie, można domyślnie zastąpić funkcję Secure [regułą transportu](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) , aby pominąć wszystkie filtrowanie spamu. Gdy firma Microsoft wykryje komunikaty jako phish o wysokim poziomie ufności z tą regułą, nadal są dostarczane do skrzynki odbiorczej. 
- Wyniki fałszywie dodatnie: możesz tymczasowo zezwolić na niektóre komunikaty, które są nadal analizowane przez [firmę Microsoft za pośrednictwem przesyłania przez administratora](admin-submission.md). Podobnie jak w przypadku wszystkich przesłonięcia, zaleca się, aby były tymczasowe.
