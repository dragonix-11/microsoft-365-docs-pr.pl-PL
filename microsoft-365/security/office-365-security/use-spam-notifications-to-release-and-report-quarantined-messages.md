---
title: Poddaj kwarantannie powiadomienia (powiadomienia użytkowników końcowych o spamie) w Microsoft 365
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
description: Administratorzy mogą dowiedzieć się więcej o powiadomieniach użytkowników końcowych o spamie dla wiadomości poddanych kwarantannie w u Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 706303e7bdab7297fbc1dd353238db3542c28177
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465844"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Używanie powiadomień kwarantanny do zwalniania i zgłaszania poddanych kwarantannie wiadomości

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online kwarantanna zawiera potencjalnie niebezpieczne lub niechciane wiadomości. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomości kwarantannie w uchęce EOP](quarantine-email-messages.md).

_Zasady kwarantanny_ określają, co użytkownicy mogą robić w kwarantannie wiadomości na podstawie tego, dlaczego ta wiadomość została poddana kwarantannie (dla obsługiwanych funkcji). Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md). Grupy kwarantanny kontrolują również, czy adresaci, których dotyczy problem (w tym  udostępnione skrzynki pocztowe), otrzymują okresowe powiadomienia kwarantanny dotyczące ich wiadomości poddanych kwarantannie. Powiadomienia kwarantanny zastępują powiadomienia użytkowników końcowych o spamie dla wszystkich obsługiwanych funkcji ochrony (nie tylko werdyktów zasad ochrony przed spamem).

Powiadomienia kwarantanny nie są włączone we wbudowanych powiadomieniach kwarantanny o nazwach AdminOnlyAccessPolicy lub DefaultFullAccessPolicy. Powiadomienia kwarantanny są włączone we wbudowanych zasadach kwarantanny o nazwie NotificationEnabledPolicy, [jeśli są dostępne w Twojej organizacji](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). W przeciwnym razie, aby włączyć powiadomienia kwarantanny w zasadach kwarantanny, musisz utworzyć [i skonfigurować nowe zasady kwarantanny](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

Ponadto, aby umożliwić poprawne działania opcji "Blokuj nadawcę" w powiadomieniach kwarantanny, użytkownicy muszą mieć włączoną obsługę zdalnej obsługi programu PowerShell. Aby uzyskać instrukcje, [zobacz Włączanie lub wyłączanie dostępu do Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

Administratorzy mogą także użyć ustawień globalnych w zasadach kwarantanny w celu dostosowania nazwy wyświetlanej nadawcy, tekstu zastrzeżenia w różnych językach oraz logo firmy używanego w powiadomieniach kwarantanny. Aby uzyskać instrukcje, [zobacz Konfigurowanie ustawień powiadomień globalnego kwarantanny](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

W przypadku udostępnionych skrzynek pocztowych powiadomienia kwarantanny są obsługiwane tylko dla użytkowników, którym udzielono uprawnień Pełny dostęp do udostępnionej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Edytowanie delegowania](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation) udostępnionej skrzynki pocztowej za pomocą programu EAC.

> [!NOTE]
> Domyślnie wiadomości poddane kwarantannie są nazywane próbami wyłudzania informacji o wysokiej pewności, złośliwym oprogramowaniem, regułami przepływu poczty e-mail (nazywanymi również regułami transportu) lub Sejf Zasady załączników w programie Ochrona usługi Office 365 w usłudze Defender są dostępne tylko dla administratorów (domyślnie są używane zasady kwarantanny AdminOnlyAccessPolicy). Aby uzyskać więcej informacji, zobacz [Zarządzanie poddatymi wiadomościami i plikami jako administrator w u usługi EOP](manage-quarantined-messages-and-files.md).
>
> Obecnie powiadomienia kwarantanny nie są obsługiwane dla grup ani wiadomości wyłudzających informacje o wysokiej pewności. 

Po otrzymaniu powiadomienia o kwarantannie dla każdej wiadomości poddanej kwarantannie są zawsze dostępne następujące informacje:

- **Nadawca**: nazwa i adres e-mail wysyłania wiadomości poddanej kwarantannie.
- **Temat**: tekst wiersza tematu wiadomości poddanej kwarantannie.
- **Data**: data i godzina (w czasie UTC), które poddano wiadomości kwarantannie.

Czynności dostępne w powiadomieniu kwarantanny zależą od tego, dlaczego wiadomość została poddana kwarantannie, oraz od uprawnień przypisanych przez skojarzone zasady kwarantanny. Aby uzyskać więcej informacji, zobacz [Szczegóły uprawnień do kwarantanny zasad](quarantine-policies.md#quarantine-policy-permission-details).

Domyślnie w powiadomieniu kwarantanny dla wiadomości poddanych kwarantannie jako spam, spam o dużej pewności lub zbiorczo są dostępne następujące akcje:

- **Zablokuj nadawcę**: Kliknij ten link, aby dodać nadawcę do listy Zablokowani nadawcy w _skrzynce pocztowej_ . Aby uzyskać więcej informacji, zobacz [Blokowanie nadawcy poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Wersja**: Możesz zwolnić wiadomość w tym miejscu bez konieczności przejść do kwarantanny **w Microsoft 365 Defender** portalu.
- **Recenzja**: Kliknij ten link, aby  przejść do kwarantanny w portalu usługi Microsoft 365 Defender, gdzie możesz (w zależności od tego, dlaczego wiadomość została poddana kwarantannie), zwolnić, usunąć lub zgłosić poddaną kwarantannie wiadomości. Aby uzyskać więcej informacji, zobacz Znajdowanie i zwalnianie poddanych [kwarantannie wiadomości jako użytkownik w u kontie EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="Przykład powiadomienia kwarantanny" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> Zablokowany nadawca nadal może ci wysyłać wiadomości. Wszystkie wiadomości od tego nadawcy, które przeniosą się do Twojej skrzynki pocztowej, zostaną natychmiast przeniesione do folderu Wiadomości-śmieci. Przyszłe wiadomości od tego nadawcy będą trafiać do folderu Wiadomości-śmieci lub do kwarantanny. Jeśli chcesz usunąć te wiadomości po nadejściu, zamiast kwartylować je, użyj reguł przepływu [poczty (](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) nazywanych również regułami transportu) w celu usunięcia wiadomości przy nadejściu.
