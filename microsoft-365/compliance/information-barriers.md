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
ms.openlocfilehash: 72a53580222b315f86fd397e391b026937b8035b
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287183"
---
# <a name="learn-about-information-barriers"></a>Dowiedz się więcej o barierach informacyjnych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Usługi w chmurze firmy Microsoft obejmują zaawansowane możliwości komunikacji i współpracy. Załóżmy jednak, że chcesz ograniczyć komunikację i współpracę między dwiema grupami, aby uniknąć konfliktu interesów w organizacji. Możesz też ograniczyć komunikację i współpracę między niektórymi osobami w organizacji, aby chronić informacje wewnętrzne. Microsoft 365 umożliwia komunikację i współpracę między grupami i organizacjami, więc czy istnieje sposób ograniczenia komunikacji i współpracy między określonymi grupami użytkowników w razie potrzeby? Dzięki usłudze Microsoft Purview Information Barriers (IB) możesz!

Microsoft Teams, SharePoint Online i OneDrive dla Firm obsługują bariery informacyjne. Zakładając, że [subskrypcja](#required-licenses-and-permissions) zawiera bariery informacyjne, administrator zgodności lub administrator barier informacyjnych może zdefiniować zasady umożliwiające lub uniemożliwiające komunikację między grupami użytkowników w Microsoft Teams. Zasady bariery informacyjnej mogą być używane w takich sytuacjach:

- Użytkownik w grupie przedsiębiorców dnia nie powinien komunikować się ani udostępniać plików zespołowi ds. marketingu
- Personel finansowy pracujący nad poufnymi informacjami firmy nie powinien komunikować się ani udostępniać plików określonym grupom w organizacji
- Wewnętrzny zespół z materiałami z tajemnicy handlowej nie powinien dzwonić ani rozmawiać online z osobami w niektórych grupach w swojej organizacji
- Zespół badawczy powinien dzwonić lub rozmawiać online tylko z zespołem deweloperów produktów
- Witryna dla dziennej grupy przedsiębiorców nie powinna być udostępniana ani dostępna dla osób spoza grupy przedsiębiorców dnia

> [!IMPORTANT]
> Bariery informacyjne ***obsługuje tylko** ograniczenia dwukierunkowe. Ograniczenia jednokierunkowe, takie jak marketing, mogą komunikować się z przedsiębiorcami dziennymi i współpracować z nimi, ale dzień, w którym inwestorzy nie mogą komunikować się i współpracować z marketingiem _*_, nie są obsługiwane_**.

We wszystkich tych przykładowych scenariuszach (i nie tylko) można zdefiniować zasady barier informacyjnych, aby zapobiegać lub zezwalać na komunikację i współpracę w Microsoft Teams, SharePoint Online i OneDrive. Takie zasady mogą uniemożliwić użytkownikom nawiązywanie połączeń lub rozmowy z tymi, których nie powinny, lub umożliwić użytkownikom komunikowanie się tylko z określonymi grupami w Microsoft Teams. W przypadku obowiązywania zasad barier informacyjnych zawsze, gdy użytkownicy objęci tymi zasadami próbują komunikować się i współpracować z innymi osobami w Microsoft Teams, SharePoint Online lub OneDrive kontrole są wykonywane w celu zapobiegania (lub zezwalania) na komunikację i współpracę (zgodnie z definicją w zasadach barier informacyjnych).

Aby dowiedzieć się więcej o środowisku użytkownika z barierami informacyjnymi, zobacz:

- [Bariery informacyjne w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Bariery informacyjne w usłudze SharePoint Online](/sharepoint/information-barriers)
- [Bariery informacyjne w OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> Obecnie bariery informacyjne nie mają zastosowania do komunikacji e-mail. Ponadto bariery informacyjne są niezależne od [granic zgodności](set-up-compliance-boundaries.md).<p> Przed zdefiniowaniem i zastosowaniem zasad barier informacyjnych upewnij się, że organizacja nie ma [Exchange zasad książki adresowej](/exchange/address-books/address-book-policies/address-book-policies). (Bariery informacyjne są oparte na zasadach książki adresowej).

## <a name="what-happens-with-information-barriers"></a>Co się dzieje z barierami informacyjnymi

Po wprowadzeniu zasad bariery informacyjnej osoby, które nie powinny komunikować się ani udostępniać plików innym określonym użytkownikom, nie będą mogły znaleźć, wybrać, porozmawiać ani zadzwonić do tych użytkowników. Dzięki barierom informacyjnym przeprowadza się kontrole, aby zapobiec nieautoryzowanej komunikacji i współpracy.

Bariery informacyjne mają zastosowanie do Microsoft Teams (czatów i kanałów), SharePoint Online i OneDrive. W Microsoft Teams zasady bariery informacyjnej określają i zapobiegają następującym rodzajom nieautoryzowanej komunikacji:

- Wyszukiwanie użytkownika
- Dodawanie członka do zespołu
- Rozpoczynanie sesji czatu z kimś
- Rozpoczynanie czatu grupowego
- Zapraszanie kogoś do dołączenia do spotkania
- Udostępnianie ekranu
- Nawiązywanie połączenia
- Udostępnianie pliku innemu użytkownikowi
- Dostęp do pliku za pośrednictwem linku udostępniania

Jeśli zaangażowane osoby zostaną uwzględnione w zasadach bariery informacyjnej, aby zapobiec działaniu, nie będą mogły kontynuować. Ponadto potencjalnie wszyscy, którzy są uwzględnieni w zasadach barier informacyjnych, mogą mieć możliwość komunikowania się z innymi osobami w Microsoft Teams. Gdy osoby, których dotyczą zasady bariery informacyjnej, należą do tego samego zespołu lub czatu grupowego, mogą zostać usunięte z tych sesji czatu, a dalsza komunikacja z grupą może nie być dozwolona.

Aby dowiedzieć się więcej o środowisku użytkownika z barierami informacyjnymi, zobacz [bariery informacyjne w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

W SharePoint Online i OneDrive zasady bariery informacyjnej określają i zapobiegają następującym rodzajom nieautoryzowanej współpracy:

- Dodawanie członka do witryny
- Uzyskiwanie dostępu do witryny lub zawartości przez użytkownika
- Udostępnianie witryny lub zawartości innemu użytkownikowi
- Wyszukiwanie witryny

Aby dowiedzieć się więcej o środowisku użytkownika z barierami informacyjnymi, zobacz [bariery informacyjne w usłudze SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Przed rozpoczęciem pracy z usługą IB należy potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszelkie dodatki. Aby uzyskać dostęp do usługi IB i korzystać z niej, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- subskrypcja Microsoft 365 E5/A5 (wersja płatna lub próbna)
- subskrypcja Office 365 E5/A5/A3/A1 (wersja płatna lub próbna)
- Office 365 Advanced Compliance dodatku (nie jest już dostępny dla nowych subskrypcji)
- subskrypcja Microsoft 365 E3/A3/A1 + dodatek zgodności Microsoft 365 E5/A5
- subskrypcja Microsoft 365 E3/A3/A1 + dodatek Microsoft 365 E5/A5 Insider Risk Management

Aby uzyskać więcej informacji, zobacz [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Aby [zdefiniować lub edytować zasady bariery informacji](information-barriers-policies.md), musisz mieć przypisaną jedną z następujących ról:

- administrator globalny Microsoft 365
- administrator globalny Office 365
- Administrator zgodności
- Zarządzanie zgodnością IB

(Aby dowiedzieć się więcej o rolach i uprawnieniach, zobacz [Uprawnienia w centrum Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)).

Aby zdefiniować, zweryfikować lub edytować zasady bariery informacji, musisz znać polecenia cmdlet programu PowerShell. Chociaż udostępniamy kilka przykładów poleceń cmdlet programu PowerShell w [artykule z instrukcjami](information-barriers-policies.md), musisz znać inne szczegóły, takie jak parametry, dla organizacji.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w usłudze SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w OneDrive](/onedrive/information-barriers)
- [Zobacz atrybuty, których można używać do zasad barier informacyjnych](information-barriers-attributes.md)
- [Definiowanie zasad dla barier informacyjnych](information-barriers-policies.md)
- [Edytowanie (lub usuwanie) zasad barier informacyjnych](information-barriers-edit-segments-policies.md)
