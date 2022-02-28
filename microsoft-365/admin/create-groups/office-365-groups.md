---
title: Omówienie grup Microsoft 365 administratorów
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Dzięki Microsoft 365 możesz prowadzić pracę zespołową w różnych Microsoft 365, zapewniając grupie osób dostęp do zbioru udostępnionych zasobów.
ms.openlocfilehash: 5aaf7598f3591efb330618f0be98ea3376816eca
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983918"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Omówienie grup Microsoft 365 administratorów

Microsoft 365 Grupy to usługa członkostwa foundationowego, która kieruje całą pracą zespołową w Microsoft 365. Dzięki Microsoft 365 grupy możesz udzielić grupie osób dostępu do zbioru udostępnionych zasobów. Do tych zasobów należą:

- Udostępniona skrzynka Outlook odbiorcza
- Kalendarz udostępniony
- Biblioteka SharePoint dokumentów
- A Planner
- Notes OneNote
- Power BI
- Yammer (jeśli grupa została utworzona na podstawie Yammer)
- Zespół (jeśli grupa została utworzona na podstawie Teams)
- Przewodnik (jeśli masz Project dla sieci Web)
- Stream

W Microsoft 365 nie trzeba ręcznie przypisywać uprawnień do każdego z tych zasobów. Dodanie osób do grupy automatycznie nadaje im potrzebne uprawnienia.

Każdy użytkownik może utworzyć grupę, chyba że [ograniczysz możliwość tworzenia grup do określonego zestawu osób](../../solutions/manage-creation-of-groups.md). Jeśli ograniczysz tworzenie grup, użytkownicy, którzy nie mogą tworzyć grup, nie będą mogli tworzyć witryn programu SharePoint, aplikacji Planners, zespołów, kalendarzy grupy programu Outlook, grup strumieniowo, grup Yammer, bibliotek udostępnionych w programie OneDrive ani udostępnionych obszarów roboczych programu Power BI. Te usługi wymagają, aby osoby tworzące je mogły tworzyć grupę. Użytkownicy nadal mogą uczestniczyć w działaniach grupy, takich jak tworzenie zadań w aplikacji Planner Teams czatach, o ile są członkami grupy.

Grupy mają następujące role:

- **Właściciele** — właściciele grup mogą dodawać i usuwać członków oraz mają unikatowe uprawnienia, takie jak możliwość usuwania konwersacji z udostępnionej skrzynki odbiorczej lub zmieniania różnych ustawień dotyczących grupy. Właściciele grupy mogą zmienić nazwę grupy, zaktualizować opis lub obraz i nie tylko.
- **Członkowie** — członkowie mają dostęp do wszystkich elementów w grupie, ale nie mogą zmieniać ustawień grupy. Domyślnie członkowie grupy mogą zapraszać gości do dołączenia do grupy, ale możesz [kontrolować to ustawienie](manage-guest-access-in-groups.md).
- **Goście** — goście grupy to członkowie spoza Twojej organizacji.

Tylko administratorzy globalni, administratorzy użytkowników i administratorzy grup mogą tworzyć grupy na <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">centrum administracyjne platformy Microsoft 365.</a> Nie można użyć konta administratora delegowanego (na przykład w przypadku konsultanta, który jest administratorem w imieniu innego użytkownika).

Jako administrator możesz:

- [Określanie, kto może tworzyć grupy](../../solutions/manage-creation-of-groups.md)
- [Tworzenie zasad nazewnictwa dla grup w organizacji](../../solutions/groups-naming-policy.md)
- [Wybieranie domeny do użycia podczas tworzenia grupy](../../solutions/choose-domain-to-create-groups.md)
- [Zarządzanie dostępem gości do grup](manage-guest-access-in-groups.md)
- [Odzyskiwanie usuniętej grupy](restore-deleted-group.md) (w ciągu 30 dni od usunięcia)

Jeśli wolisz bardziej zautomatyzowany sposób zarządzania cyklem życia grup Microsoft 365, możesz użyć zasad wygasania, aby grupy wygasały w określonym przedziale czasu. Właściciele grupy otrzymają wiadomość e-mail na 30, 15 i 1 dzień przed wygaśnięciem grupy, co pozwoli im odnowić grupę, jeśli będzie ona nadal potrzebna. Zobacz: [Microsoft 365 wygasania grupy](../../solutions/microsoft-365-groups-expiration-policy.md).

Grupami można administrować z centrum administracyjne platformy Microsoft 365 [lub przy użyciu programu PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md).

Jeśli masz wielu użytkowników, na przykład w dużej firmie lub przedsiębiorstwie, możesz mieć wielu użytkowników, którzy tworzą grupy do różnych celów. Zdecydowanie zalecamy zapoznanie się z [planem zarządzania w Microsoft 365, aby](../../solutions/collaboration-governance-overview.md) zapoznać się z najlepszymi rozwiązaniami.

## <a name="group-limits"></a>Limity grupy

Następujące ograniczenia mają zastosowanie do Microsoft 365 grup:

|Maksimum...|Value|
|:---------|:----|
|Właściciele na grupę|100|
|Grupy, które może tworzyć użytkownik|250|
|Grupy, które może tworzyć administrator|Maksymalnie domyślny limit dzierżawy: 500 K|
|Liczba członków|Ponad 1000, chociaż tylko 1000 może jednocześnie uzyskać dostęp do konwersacji grupowych. <br>Użytkownicy mogą zauważyć opóźnienia podczas uzyskiwania dostępu do kalendarza i konwersacji w dużych grupach w Outlook.|
|Liczba grup, których użytkownik może być członkiem|7,000|
|Przechowywanie plików|1 TB + 10 GB na użytkownika z subskrypcją + wszelkie inne wykupione miejsce do magazynowania. Możesz kupić nieograniczoną ilość dodatkowego miejsca do magazynowania.|
|Rozmiar skrzynki pocztowej grupy|50 GB|

Domyślna maksymalna liczba Microsoft 365 organizacji może mieć 500 000. Aby przekroczyć limit domyślny, skontaktuj się z pomocą techniczną firmy Microsoft. Aby uzyskać więcej informacji na Microsoft 365 grupy, zobacz Grupy Microsoft 365 [— Pomoc dla administratorów](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

Zarządzanie grupami Microsoft 365 jest bardziej efektywne, gdy masz informacje z akcjami dotyczące użycia grup. Raport centrum administracyjne platformy Microsoft 365 narzędzie do raportowania, które umożliwia wyświetlanie informacji o użyciu magazynu, o tym, ile aktywnych grup jest aktywnych i jak użytkownicy korzystają z grup. Zobacz: [Microsoft 365 w centrum administracyjnym,](../activity-reports/office-365-groups.md) aby uzyskać więcej informacji.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

Możesz utworzyć etykiety wrażliwości, które mogą być ustawiane przez użytkowników podczas tworzenia Microsoft 365 grupy. Etykiety wrażliwości pozwala skonfigurować: 

- Prywatność (publiczna lub prywatna)
- Dostęp użytkowników zewnętrznych
- Niezamanektowany dostęp do urządzenia

Na przykład możesz utworzyć etykietę o nazwie Wysoce  poufne i określić, że dowolna grupa utworzona za pomocą tej etykiety będzie prywatna i nie zezwala na użytkowników zewnętrznych. Jeśli podczas tworzenia grupy użytkownicy w organizacji wybierzą tę etykietę, grupa będzie ustawiona na prywatną, a członkowie grupy nie będą mogli dodawać do grupy użytkowników zewnętrznych.

> [!IMPORTANT]
> Jeśli obecnie używasz etykiet klasyfikacji, nie będą one już dostępne dla użytkowników, którzy tworzą grupy po włączeniu etykiet wrażliwości. 

Aby uzyskać informacje na temat tworzenia etykiet wrażliwości, zarządzania nimi i używania ich, zobacz Chroninie zawartości w witrynach sieci [Microsoft Teams, Microsoft 365 i SharePoint tematu.](../../compliance/sensitivity-labels-teams-groups-sites.md)

## <a name="which-microsoft-365-plans-include-groups"></a>Które Microsoft 365 obejmują grupy?

Każda Microsoft 365, która ma subskrypcję usługi Exchange Online i SharePoint Online, będzie obsługiwać grupy. Obejmuje to plany usług Business Essentials i Business Premium oraz Enterprise E1, E3 i E5. Grupa przyjmuje licencję osoby, która tworzy grupę (ta grupa jest także znana jako "organizator" grupy). O ile organizator ma odpowiednią licencję na wszystkie funkcje, które ma mieć grupa, ta licencja przekaże grupie.

> [!NOTE]
> Aby uzyskać więcej szczegółowych informacji Microsoft 365 planów i rodzin usług, zobacz Microsoft 365 [opcje planu](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).

Jeśli masz plan tylko do Exchange, nadal możesz uzyskać funkcje udostępnionej skrzynki odbiorczej i kalendarza udostępnionego grup w programie Outlook, ale nie będziesz korzystać z biblioteki dokumentów, aplikacji Planner ani żadnych innych możliwości.

Microsoft 365 grupy pracują z innymi Azure Active Directory. Dostępne funkcje grup zależą od Azure Active Directory subskrypcji i licencji przypisanych do organizatora grupy.

> [!IMPORTANT]
> W przypadku wszystkich funkcji grup, jeśli masz subskrypcję usługi Azure AD — wersja Premium, użytkownicy mogą dołączyć do grupy niezależnie od tego, czy mają przypisaną licencję AAD P1. Licencjonowanie nie jest wymuszane.
> Okresowo będziemy generować raporty użycia informujące, którzy użytkownicy nie mają licencji, i muszą mieć przypisaną licencję, aby spełniała wymagania licencyjne. Załóżmy na przykład, że użytkownik nie ma licencji i jest dodawany do grupy, w której są wymuszane zasady nazewnictwa. W raporcie będzie oznaczana, że użytkownik potrzebuje licencji.

## <a name="related-content"></a>Zawartość pokrewna

[Więcej informacji Microsoft 365 grup](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2) (artykuł)\
[Uaktualnianie list dystrybucyjnych Microsoft 365 grup](../manage/upgrade-distribution-lists.md) (artykuł)\
[Zarządzanie Microsoft 365 grup za pomocą programu PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (artykuł)\
[SharePoint limity online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) (artykuł)\
[Organizowanie grup i kanałów w uwitrynie Microsoft Stream](/stream/groups-channels-organization) (artykuł)
