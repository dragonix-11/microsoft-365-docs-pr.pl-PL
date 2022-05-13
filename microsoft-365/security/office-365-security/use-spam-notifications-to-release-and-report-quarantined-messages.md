---
title: Powiadomienia o kwarantannie (powiadomienia o spamie użytkowników końcowych) w Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o powiadomieniach o spamie użytkowników końcowych dotyczących komunikatów objętych kwarantanną w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c1688e4a56787c9593aae7006a05d52b16558647
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393485"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Używanie powiadomień kwarantanny do wydawania i zgłaszania komunikatów poddanych kwarantannie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych kwarantanna zawiera potencjalnie niebezpieczne lub niechciane wiadomości. Aby uzyskać więcej informacji, zobacz [Komunikaty poddane kwarantannie w ramach EOP](quarantine-email-messages.md).

_Zasady kwarantanny_ definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie w oparciu o przyczynę kwarantanny komunikatu (w przypadku obsługiwanych funkcji). Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md). Zasady kwarantanny kontrolują również, czy adresaci, których dotyczy problem (w tym udostępnione skrzynki pocztowe), otrzymują okresowe _powiadomienia o kwarantannie_ dotyczące wiadomości objętych kwarantanną. Powiadomienia o kwarantannie są zamiennikiem powiadomień o spamie użytkowników końcowych dla wszystkich obsługiwanych funkcji ochrony (nie tylko werdyktów dotyczących zasad ochrony przed spamem).

Powiadomienia kwarantanny nie są włączone we wbudowanych powiadomieniach kwarantanny o nazwie AdminOnlyAccessPolicy lub DefaultFullAccessPolicy. Powiadomienia o kwarantannie są włączone we wbudowanych zasadach kwarantanny o nazwie NotificationEnabledPolicy, [jeśli organizacja je ma](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). W przeciwnym razie, aby włączyć powiadomienia o kwarantannie w zasadach kwarantanny, należy [utworzyć i skonfigurować nowe zasady kwarantanny](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

Ponadto aby umożliwić poprawne działanie opcji "Blokuj nadawcę" w powiadomieniach o kwarantannie, użytkownicy muszą być włączeni dla zdalnego programu PowerShell. Aby uzyskać instrukcje, zobacz [Włączanie lub wyłączanie dostępu do Exchange Online programu PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

Administratorzy mogą również używać ustawień globalnych w zasadach kwarantanny, aby dostosować nazwę wyświetlaną nadawcy, tekst zastrzeżenia w różnych językach oraz logo firmy używane w powiadomieniach o kwarantannie. Aby uzyskać instrukcje, zobacz [Konfigurowanie ustawień powiadomień globalnej kwarantanny](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

W przypadku udostępnionych skrzynek pocztowych powiadomienia o kwarantannie są obsługiwane tylko dla użytkowników, którym przyznano uprawnienie FullAccess do udostępnionej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Używanie umowy EAC do edytowania delegowania udostępnionej skrzynki pocztowej](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Domyślnie wiadomości poddane kwarantannie jako wyłudzanie informacji o wysokim poziomie ufności, złośliwe oprogramowanie, reguły przepływu poczty (nazywane również regułami transportu) lub zasady załączników Sejf w Ochrona usługi Office 365 w usłudze Defender są dostępne tylko dla administratorów (domyślnie są używane zasady kwarantanny AdminOnlyAccessPolicy). Aby uzyskać więcej informacji, zobacz [Manage quarantined messages and files as an admin in EOP (Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w ramach EOP](manage-quarantined-messages-and-files.md)).
>
> Obecnie powiadomienia o kwarantannie nie są obsługiwane dla grup.

Po otrzymaniu powiadomienia o kwarantannie dla każdego komunikatu poddanej kwarantannie są zawsze dostępne następujące informacje:

- **Nadawca**: nazwa i adres e-mail wiadomości poddanej kwarantannie.
- **Temat**: tekst wiersza tematu komunikatu poddanej kwarantannie.
- **Data**: data i godzina (w utc), dla których komunikat został poddany kwarantannie.

Akcje dostępne w powiadomieniu o kwarantannie zależą od przyczyny kwarantanny komunikatu oraz uprawnień przypisanych przez skojarzone zasady kwarantanny. Aby uzyskać więcej informacji, zobacz [Szczegóły uprawnień zasad kwarantanny](quarantine-policies.md#quarantine-policy-permission-details).

Domyślnie w powiadomieniu o kwarantannie są dostępne następujące akcje dla wiadomości, które zostały poddane kwarantannie jako spam, spam o wysokim poziomie ufności lub zbiorczo:

- **Blokuj nadawcę**: kliknij ten link, aby dodać nadawcę do listy zablokowanych nadawców w _skrzynce_ pocztowej. Aby uzyskać więcej informacji, zobacz [Blokuj nadawcę poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Wydanie**: Komunikat można opublikować tutaj bez przechodzenia do **kwarantanny** w portalu Microsoft 365 Defender.
- **Przejrzyj**: kliknij ten link, aby przejść do **obszaru Kwarantanna** w portalu Microsoft 365 Defender, gdzie można (w zależności od tego, dlaczego komunikat został poddany kwarantannie) wyświetlać, zwalniać, usuwać lub zgłaszać komunikaty poddane kwarantannie. Aby uzyskać więcej informacji, zobacz [Znajdowanie i wydawanie komunikatów poddanych kwarantannie jako użytkownik w ramach EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="Przykład powiadomienia o kwarantannie" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> Zablokowany nadawca nadal może wysyłać Ci wiadomość e-mail. Wszystkie wiadomości od tego nadawcy, które trafią do Twojej skrzynki pocztowej, zostaną natychmiast przeniesione do folderu Wiadomości-śmieci. Przyszłe wiadomości od tego nadawcy zostaną przesłane do folderu Wiadomości-śmieci lub do kwarantanny. Jeśli chcesz usunąć te wiadomości po przyjeździe, zamiast ich unieważniać, użyj [reguł przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (znanych również jako reguły transportu), aby usunąć wiadomości po przyjeździe.
