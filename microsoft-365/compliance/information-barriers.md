---
title: Dowiedz się więcej o barierach informacyjnych
description: Dowiedz się więcej o barierach informacyjnych w usłudze Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, zgodność, bariery informacyjne
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b302231d7dbdcc92ee2e8e2e0564cedb27a4218e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621122"
---
# <a name="learn-about-information-barriers"></a>Dowiedz się więcej o barierach informacyjnych

Microsoft Purview Information Barriers (IB) to rozwiązanie do zapewniania zgodności, które umożliwia ograniczenie dwukierunkowej komunikacji i współpracy między grupami i użytkownikami w usługach Microsoft Teams, SharePoint Online i OneDrive dla Firm. Często używane w wysoce regulowanych branżach, IB może pomóc uniknąć konfliktów interesów i chronić informacje wewnętrzne między użytkownikami a obszarami organizacyjnymi.

Po wprowadzeniu zasad IB użytkownicy, którzy nie powinni komunikować się ani udostępniać plików innym określonym użytkownikom, nie będą mogli znaleźć, wybrać, porozmawiać ani zadzwonić do tych użytkowników. Zasady IB automatycznie przeprowadzają kontrole w celu wykrywania i zapobiegania nieautoryzowanej komunikacji i współpracy między zdefiniowaną grupą i użytkownikami. Zasady IB są niezależne od [granic zgodności](/microsoft-365/compliance/set-up-compliance-boundaries) dla badań zbierania elektronicznych materiałów dowodowych, które kontrolują lokalizacje zawartości użytkowników, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych.

Zasady IB umożliwiają lub uniemożliwiają komunikację i współpracę między grupami i użytkownikami w następujących przykładowych scenariuszach:

- Użytkownicy w grupie *Day Trader* nie powinni komunikować się ani udostępniać plików *zespołowi ds. marketingu*
- Personel finansowy pracujący nad poufnymi informacjami firmy nie powinien komunikować się ani udostępniać plików określonym grupom w organizacji
- Wewnętrzny zespół z materiałami z tajemnicy handlowej nie powinien dzwonić ani rozmawiać online z osobami w niektórych grupach w swojej organizacji
- Zespół badawczy powinien dzwonić lub rozmawiać online tylko z zespołem deweloperów produktów
- Witryna programu SharePoint dla grupy *Day Trader* nie powinna być udostępniana ani dostępna dla osób spoza grupy *Day Trader*

> [!IMPORTANT]
> Bariery informacyjne **obsługują tylko dwukierunkowe** ograniczenia komunikacji i współpracy. Na przykład scenariusz, w którym marketing może komunikować się i współpracować z day traders, ale day traders nie może komunikować się i współpracować z **marketingiem, nie jest obsługiwany**.

## <a name="information-barriers-and-microsoft-teams"></a>Bariery informacyjne i microsoft teams

W usłudze Microsoft Teams zasady IB określają i zapobiegają następującym rodzajom nieautoryzowanej komunikacji i współpracy:

- Wyszukiwanie użytkownika
- Dodawanie członka do zespołu
- Rozpoczynanie sesji czatu z kimś
- Rozpoczynanie czatu grupowego
- Zapraszanie kogoś do dołączenia do spotkania
- Udostępnianie ekranu
- Nawiązywanie połączenia
- Udostępnianie pliku innemu użytkownikowi
- Dostęp do pliku za pośrednictwem udostępniania linku

Jeśli użytkownicy prowadzący te działania w usłudze Microsoft Teams zostaną uwzględnieni w zasadach IB, aby zapobiec działaniu, nie będą mogli kontynuować. Ponadto wszyscy użytkownicy uwzględnieni w zasadach IB mogą potencjalnie zablokować możliwość komunikowania się z innymi użytkownikami w usłudze Microsoft Teams. Gdy osoby objęte zasadami IB są częścią tego samego zespołu lub czatu grupowego, mogą zostać usunięte z tych sesji czatu, a dalsza komunikacja z grupą może nie być dozwolona.

Aby uzyskać więcej informacji, zobacz [bariery informacyjne w usłudze Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

## <a name="information-barriers-and-sharepoint-and-onedrive"></a>Bariery informacyjne i sharepoint i onedrive

W usługach SharePoint Online i OneDrive zasady IB wykrywają i zapobiegają następującym rodzajom nieautoryzowanej współpracy:

- Dodawanie członka do witryny
- Uzyskiwanie dostępu do witryny lub zawartości przez użytkownika
- Udostępnianie witryny lub zawartości innemu użytkownikowi
- Wyszukiwanie witryny

Aby uzyskać więcej informacji, zobacz [Bariery informacyjne w programie SharePoint](/sharepoint/information-barriers) i [bariery informacyjne w usłudze OneDrive](/onedrive/information-barriers).

## <a name="information-barriers-and-exchange-online"></a>Bariery informacyjne i Exchange Online

Zasady IB nie są dostępne w celu ograniczenia komunikacji i współpracy między grupami i użytkownikami w wiadomościach e-mail. Zasady IB są oparte na [zasadach książki adresowej Exchange Online (ABPs).](/exchange/address-books/address-book-policies/address-book-policies) Usługi ABP umożliwiają organizacjom wirtualne przypisywanie użytkowników do określonych grup w celu zapewnienia dostosowanych widoków globalnej książki adresowej (GAL) organizacji. Po utworzeniu zasad IB usługi ASP dla zasad są tworzone automatycznie. Po dodaniu zasad IB w organizacji struktura i zachowanie gal ulegnie zmianie w celu zachowania zgodności z zasadami IB.

Przed zdefiniowaniem i zastosowaniem zasad IB należy usunąć wszystkie istniejące zasady książki adresowej programu Exchange w organizacji. Zasady IB są oparte na zasadach książki adresowej, a istniejące zasady abp nie są zgodne z usługami ABP utworzonymi przez IB. Aby usunąć istniejące zasady książki adresowej, zobacz [Usuwanie zasad książki adresowej w Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). Po włączeniu zasad IB i w przypadku włączenia hierarchicznej książki adresowej wszyscy użytkownicy nieuwzględnienia segmentu IB zobaczą [hierarchiczną książkę adresową](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) w usłudze Exchange Online.

Tylko Exchange Online wdrożenia są obecnie obsługiwane w przypadku zasad IB. Jeśli Twoja organizacja musi definiować i kontrolować komunikację e-mail, rozważ użycie [reguł przepływu poczty programu Exchange](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

## <a name="ready-to-get-started"></a>Chcesz rozpocząć?

- [Wprowadzenie do barier informacyjnych](information-barriers-policies.md)
- [Zarządzanie zasadami IB](information-barriers-edit-segments-policies.md)
- [Zobacz atrybuty, które mogą być używane dla zasad IB](information-barriers-attributes.md)
