---
title: Dowiedz się więcej o barierach informacyjnych w Microsoft 365
description: Stosowanie barier informacyjnych w celu zapewnienia zgodności komunikacji przy Microsoft Teams w organizacji.
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
ms.openlocfilehash: fc3d961b8707ba07febd95022580091618086d7f
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2021
ms.locfileid: "63005229"
---
# <a name="learn-about-information-barriers-in-microsoft-365"></a>Dowiedz się więcej o barierach informacyjnych w Microsoft 365

Usługi firmy Microsoft w chmurze obejmują zaawansowane funkcje komunikacji i współpracy. Załóżmy jednak, że chcesz ograniczyć komunikację i współpracę między dwiema grupami, aby uniknąć konfliktu zainteresowań w Twojej organizacji. Być może chcesz ograniczyć komunikację i współpracę między określonymi osobami w organizacji w celu zabezpieczenia informacji wewnętrznych. Microsoft 365 komunikacji i współpracy między grupami i organizacjami, czy istnieje więc sposób ograniczenia komunikacji i współpracy między określonymi grupami użytkowników, jeśli jest to konieczne? Z barierami informacyjnymi możesz!

Microsoft Teams, SharePoint Online i OneDrive dla Firm i obsługują bariery informacyjne. Przy [założeniu,](#required-licenses-and-permissions) że Subskrypcja obejmuje bariery informacyjne, administrator zgodności lub administrator barier informacyjnych może zdefiniować zasady, które umożliwiają lub uniemożliwiają komunikację między grupami użytkowników w Microsoft Teams. Zasady barier informacyjnej mogą być stosowane w następujących sytuacjach:

- Użytkownik w grupie dni nie powinien się komunikować ani udostępniać plików zespołowi marketingoweowi
- Finanse personelu pracującego nad poufnymi informacjami firmowymi nie powinny udostępniać plików określonym grupom w organizacji
- Wewnętrzny zespół z materiałami o tajemnicy handlowej nie powinien dzwonić do osób z określonych grup w organizacji ani rozmawiać z nich w trybie online
- Zespół ds. badań powinien zadzwonić lub porozmawiać na czacie online tylko z zespołem ds. rozwoju produktu
- Witryna na dzień nie powinna być udostępniana ani uzyskiwać do niej dostępu osobom spoza grupy dni

> [!IMPORTANT]
> Bariery informacyjne***obsługuje** _ tylko ograniczenia dwukierunkowe. One way restrictions, such such marketing can communicate and collaborate with day traders, but day traders cannot communicate and collaborate with marketing _*_is not supported_**.

We wszystkich tych przykładowych scenariuszach (i nie tylko) można zdefiniować zasady bariery informacyjnej, aby uniemożliwić komunikację i współpracę w Microsoft Teams, SharePoint online i OneDrive. Takie zasady mogą uniemożliwiać użytkownikom rozmowy lub rozmowy z osobami, które nie powinny, lub umożliwiać komunikowanie się tylko z określonymi grupami w Microsoft Teams. Zasady barier informacyjnej będą obowiązywać, gdy użytkownicy objęci tymi zasadami będą próbować komunikować się i współpracować z innymi osobami w programach Microsoft Teams, SharePoint Online lub OneDrive, aby zapobiec (lub zezwolić) na komunikację i współpracę (zdefiniowane przez zasady bariery informacyjnej).

Aby dowiedzieć się więcej o doświadczeniu użytkownika z barierami informacyjnymi, zobacz:

- [Bariery informacyjne w programie Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Bariery informacyjne w SharePoint Online](/sharepoint/information-barriers)
- [Bariery informacyjne w programie OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> Obecnie bariery informacyjne nie dotyczą komunikacji za pośrednictwem poczty e-mail. Ponadto bariery informacyjne są niezależne od [granic zgodności](set-up-compliance-boundaries.md).<p> Przed zdefiniowaniem i zastosowaniem zasady informacyjnej upewnij się, że w Twojej organizacji nie [obowiązują Exchange książki adresowej](/exchange/address-books/address-book-policies/address-book-policies). (Bariery informacyjne są oparte na zasadach książki adresowej).

## <a name="what-happens-with-information-barriers"></a>Co się dzieje z barierami informacyjnymi

Gdy będą stosować zasady bariery informacyjnej, osoby, które nie powinny się komunikować ani udostępniać plików innym użytkownikom, nie będą mogły ich znaleźć, wybrać, rozmawiać ani do nich dzwonić. Ze względu na bariery informacyjne przeprowadza się testy, aby zapobiec nieautoryzowanej komunikacji i współpracy.

Bariery informacyjne dotyczą Microsoft Teams (czatów i kanałów), SharePoint Online i OneDrive. W Microsoft Teams informacji zasady zawarte w tym programie określają i zapobiegają nieautoryzowanej komunikacji następujących typów:

- Wyszukiwanie użytkownika
- Dodawanie członka do zespołu
- Rozpoczynanie sesji czatu z inną osobą
- Rozpoczynanie czatu grupowego
- Zapraszanie innej osoby do dołączenia do spotkania
- Udostępnianie ekranu
- Dzwonienie
- Udostępnianie pliku in inowi użytkownikowi
- Dostęp do pliku przy użyciu linku udostępniania

Jeśli zaangażowane osoby zostaną uwzględnione w zasadach bariery informacyjnej w celu uniemożliwienia tego działania, nie będą mogli kontynuować. Ponadto, potencjalnie, wszystkim osobom uwzględnionym w zasadach bariery informacyjnej można zablokować komunikację z innymi osobami w programie Microsoft Teams. Jeśli osoby, do których mają dostęp zasady bariery informacyjnej, są częścią tego samego czatu zespołowego lub grupowego, mogą one zostać usunięte z tych sesji czatu i nie zezwolić na dalszą komunikację z grupą.

Aby dowiedzieć się więcej na temat doświadczeń użytkowników z barierami informacyjnymi, zobacz bariery informacyjne [w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

W SharePoint online OneDrive i aplikacji zasady barier informacyjnej określają i zapobiegają następującym rodzajom nieautoryzowanych współpracy:

- Dodawanie członka do witryny
- Uzyskiwanie dostępu do witryny lub zawartości przez użytkownika
- Udostępnianie witryny lub zawartości in inowi użytkownikowi
- Wyszukiwanie w witrynie

Aby dowiedzieć się więcej o doświadczeniu użytkownika z barierami informacyjnymi, zobacz bariery informacyjne w u [SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Przed rozpoczęciem pracy z zarządzaniem ryzykiem w ramach niejawnego programu testów należy potwierdzić Microsoft 365 [subskrypcji](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszystkich dodatków. Aby uzyskać dostęp do barier informacyjnych i korzystać z nich, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- Microsoft 365 E5/A5 (płatna lub próbna)
- Office 365 E5/A5/A3/A1 (wersja płatna lub próbna)
- Office 365 Advanced Compliance (nie jest już dostępny dla nowych subskrypcji)
- Microsoft 365 E3/A3/A1 + Microsoft 365 E5 zgodności ze standardem Microsoft 365 E5/A5
- Microsoft 365 E3/A3/A1 + Microsoft 365 E5/A5 zarządzanie ryzykiem niejawnego programu testów

Aby uzyskać więcej informacji, [zobacz Microsoft 365 licencjonowania w celu zapewnienia zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Aby [zdefiniować lub edytować zasady bariery informacyjnej](information-barriers-policies.md), musisz mieć przypisaną jedną z następujących ról:

- Microsoft 365 administrator globalny
- Office 365 administrator globalny
- Administrator zgodności
- Zarządzanie zgodnością IB

(Aby dowiedzieć się więcej o rolach i uprawnieniach, zobacz Uprawnienia w [Centrum Office 365 zabezpieczeń &](../security/office-365-security/permissions-in-the-security-and-compliance-center.md) zgodności).

Aby definiować, weryfikować i edytować zasady barier informacyjnej, musisz znać polecenia cmdlet programu PowerShell. Chociaż w tym artykule z [how-to-how-to](information-barriers-policies.md) do nas podajemy kilka przykładów poleceń cmdlet programu PowerShell, musisz znać inne szczegóły, takie jak parametry, dla Twojej organizacji.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w programie OneDrive](/onedrive/information-barriers)
- [Zobacz atrybuty, których można użyć w celu ochrony przed barierą informacyjną](information-barriers-attributes.md)
- [Definiowanie zasad na barierach informacyjnych](information-barriers-policies.md)
- [Edytowanie (lub usuwanie) zasad bariery informacyjnej](information-barriers-edit-segments-policies.md)
