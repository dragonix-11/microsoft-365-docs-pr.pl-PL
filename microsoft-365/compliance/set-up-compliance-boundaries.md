---
title: Konfigurowanie granic zgodności na potrzeby badań zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1b45c82f-26c8-44fb-9f3b-b45436fe2271
description: Dowiedz się, jak używać granic zgodności do tworzenia granic logicznych, które kontrolują lokalizacje zawartości użytkownika, które menedżer zbierania elektronicznych materiałów dowodowych może przeszukiwać w Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 52f4a66ffbab37109e7503181548b1de4ffac87a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128788"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>Konfigurowanie granic zgodności na potrzeby badań zbierania elektronicznych materiałów dowodowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Wskazówki zawarte w tym artykule można zastosować w przypadku korzystania z materiałów dowodowych usługi Microsoft Purview (Standard) lub Microsoft Purview eDiscovery (Premium) do zarządzania badaniami.

Granice zgodności tworzą granice logiczne w organizacji kontrolujące lokalizacje zawartości użytkownika (takie jak skrzynki pocztowe, konta OneDrive i witryny SharePoint), które mogą wyszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. Ponadto granice zgodności kontrolują, kto może uzyskiwać dostęp do przypadków zbierania elektronicznych materiałów dowodowych używanych do zarządzania badaniami prawnymi, ludzkimi lub innymi badaniami w organizacji. Potrzeba granic zgodności jest często niezbędna dla korporacji wielonarodowych, które muszą przestrzegać zarządców geograficznych i przepisów oraz dla rządów, które często są podzielone na różne agencje. W Microsoft 365 granice zgodności ułatwiają spełnienie tych wymagań podczas wyszukiwania zawartości i zarządzania badaniami w przypadkach zbierania elektronicznych materiałów dowodowych.
  
Użyjemy przykładu na poniższej ilustracji, aby wyjaśnić, jak działają granice zgodności.
  
![Granice zgodności składają się z filtrów uprawnień wyszukiwania, które kontrolują dostęp do agencji i grup ról administratora, które kontrolują dostęp do przypadków zbierania elektronicznych materiałów dowodowych.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
W tym przykładzie firma Contoso LTD to organizacja składająca się z dwóch spółek zależnych: Fourth Coffee i Coho Winery. Firma wymaga, aby menedżerowie zbierania elektronicznych materiałów dowodowych i śledczy mogli przeszukiwać tylko skrzynki pocztowe Exchange, konta OneDrive i SharePoint witryny w swojej agencji. Ponadto menedżerowie i śledczy zbierania elektronicznych materiałów dowodowych mogą widzieć tylko przypadki zbierania elektronicznych materiałów dowodowych w swojej agencji i mogą uzyskiwać dostęp tylko do spraw, do których są członkami. Ponadto w tym scenariuszu badacze nie mogą wstrzymać lokalizacji zawartości ani wyeksportować zawartości ze sprawy. Poniżej przedstawiono sposób, w jaki granice zgodności spełniają te wymagania.
  
- Funkcja filtrowania uprawnień wyszukiwania dla zbierania elektronicznych materiałów dowodowych kontroluje lokalizacje zawartości, które mogą przeszukiwać menedżerowie i badacze zbierania elektronicznych materiałów dowodowych. Oznacza to, że menedżerowie zbierania elektronicznych materiałów dowodowych i śledczy w agencji Fourth Coffee mogą przeszukiwać tylko lokalizacje treści w filii Fourth Coffee. To samo ograniczenie dotyczy spółki zależnej Coho Winery.

- [Grupy ról](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) udostępniają następujące funkcje dla granic zgodności:

  - Kontrolowanie, kto może wyświetlać przypadki zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview. Oznacza to, że menedżerowie zbierania elektronicznych materiałów dowodowych i śledczy mogą widzieć tylko przypadki zbierania elektronicznych materiałów dowodowych w swojej agencji.

  - Kontrolowanie, kto może przypisywać członków do sprawy zbierania elektronicznych materiałów dowodowych. Oznacza to, że menedżerowie zbierania elektronicznych materiałów dowodowych i śledczy mogą przypisywać członków tylko do spraw, do których sami należą.

  - Kontroluj zadania związane zbierania elektronicznych materiałów dowodowych, które członkowie mogą wykonywać, dodając lub usuwając role, które przypisują określone uprawnienia.

- Gdy filtr uprawnień wyszukiwania jest stosowany do grupy ról, członkowie grupy ról mogą wykonywać następujące akcje związane z wyszukiwaniem, o ile uprawnienia do wykonania akcji są przypisane do grupy ról:

  - Szukaj zawartości

  - Podgląd wyników wyszukiwania

  - Eksportuj wyniki wyszukiwania

  - Przeczyszczanie elementów zwracanych przez wyszukiwanie

Oto proces konfigurowania granic zgodności:
  
[Krok 1. Identyfikowanie atrybutu użytkownika do definiowania agencji](#step-1-identify-a-user-attribute-to-define-your-agencies)

[Krok 2. Tworzenie grupy ról dla każdej agencji](#step-2-create-a-role-group-for-each-agency)

[Krok 3. Tworzenie filtru uprawnień wyszukiwania w celu wymuszenia granicy zgodności](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[Krok 4. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych na potrzeby dochodzenia wewnątrzagencyjnego](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Przed skonfigurowanie granic zgodności

- Użytkownikom należy przypisać licencję Exchange Online. Aby to sprawdzić, użyj polecenia cmdlet [Get-User](/powershell/module/exchange/get-user) w Exchange Online programu PowerShell.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>Krok 1. Identyfikowanie atrybutu użytkownika do definiowania agencji

Pierwszym krokiem jest wybranie atrybutu do użycia, który zdefiniuje agencje. Ten atrybut służy do tworzenia filtru uprawnień wyszukiwania, który ogranicza menedżera zbierania elektronicznych materiałów dowodowych do wyszukiwania tylko lokalizacji zawartości użytkowników, którzy mają przypisaną określoną wartość dla tego atrybutu. Załóżmy na przykład, że firma Contoso decyduje się na użycie atrybutu **Dział** . Wartość tego atrybutu dla użytkowników w jednostce zależnej Czwarta kawa będzie  `FourthCoffee`  i wartość dla użytkowników w coho winery spółki zależnej będzie `CohoWinery`. W kroku 3 użyjesz tej  `attribute:value`  pary (na przykład *Department:FourthCoffee*), aby ograniczyć lokalizacje zawartości użytkownika, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. 
  
Oto kilka przykładów atrybutów użytkownika, których można użyć na potrzeby granic zgodności:
  
- Company

- CustomAttribute1 — CustomAttribute15

- Department

- Pakiet Office

- CountryOrRegion (dwuliterowy kod kraju)

Aby uzyskać pełną listę, zobacz pełną listę obsługiwanych [filtrów skrzynki pocztowej](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties).

## <a name="step-2-create-a-role-group-for-each-agency"></a>Krok 2. Tworzenie grupy ról dla każdej agencji

Następnym krokiem jest utworzenie grup ról w portalu zgodności, które będą zgodne z agencjami. Zalecamy utworzenie grupy ról przez skopiowanie wbudowanej grupy menedżerów zbierania elektronicznych materiałów dowodowych, dodanie odpowiednich członków i usunięcie ról, które mogą nie mieć zastosowania do Twoich potrzeb. Aby uzyskać więcej informacji na temat ról związanych zbierania elektronicznych materiałów dowodowych, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).
  
Aby utworzyć grupy ról, przejdź do strony **Uprawnienia** w portalu zgodności i utwórz grupę ról dla każdego zespołu w każdej agencji, który będzie używać granic zgodności i przypadków zbierania elektronicznych materiałów dowodowych do zarządzania badaniami.
  
W scenariuszu granic zgodności firmy Contoso należy utworzyć cztery grupy ról i dodać do nich odpowiednie elementy członkowskie.
  
- Czwarta kawa eDiscovery Managers

- Czwarta kawa śledczych

- Coho Winery eDiscovery Managers

- Badacze winiarni coho
  
Aby spełnić wymagania scenariusza granic zgodności firmy Contoso, należy również usunąć role **Blokada** i **eksportowanie** z grup ról badaczy, aby uniemożliwić śledczym umieszczanie blokad w lokalizacjach zawartości i eksportowanie zawartości ze sprawy.

> [!IMPORTANT]
> Jeśli rola zostanie dodana lub usunięta z grupy ról, która została dodana jako członek sprawy, grupa ról zostanie automatycznie usunięta jako członek sprawy (lub w każdym przypadku grupa ról jest członkiem). Powodem jest ochrona organizacji przed nieumyślnym udzieleniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich przypadków, do które należała.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>Krok 3. Tworzenie filtru uprawnień wyszukiwania w celu wymuszenia granicy zgodności

Po utworzeniu grup ról dla każdej agencji następnym krokiem jest utworzenie filtrów uprawnień wyszukiwania, które kojarzą każdą grupę ról z określoną agencją i definiują samą granicę zgodności. Musisz utworzyć jeden filtr uprawnień wyszukiwania dla każdej agencji. Aby uzyskać więcej informacji na temat tworzenia filtrów uprawnień zabezpieczeń, zobacz [Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości](permissions-filtering-for-content-search.md).
  
Poniżej przedstawiono składnię używaną do tworzenia filtru uprawnień wyszukiwania używanego dla granic zgodności dla scenariusza w tym artykule.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Oto opis każdego parametru w poleceniu:
  
- `FilterName`: określa nazwę filtru. Użyj nazwy opisującej lub identyfikującej agencję, w której jest używany filtr.

- `Users`: określa użytkowników lub grupy, którzy uzyskują ten filtr zastosowany do wykonywanych akcji wyszukiwania. W przypadku granic zgodności ten parametr określa grupy ról (utworzone w kroku 3) w agencji, dla której tworzysz filtr. Należy pamiętać, że jest to parametr wielowartościowy, dzięki czemu można dołączyć co najmniej jedną grupę ról oddzieloną przecinkami.

- `Filters`: określa kryteria wyszukiwania dla filtru. W przypadku granic zgodności należy zdefiniować następujące filtry. Każdy z nich ma zastosowanie do różnych lokalizacji zawartości.

  - `Mailbox`: określa skrzynki pocztowe lub konta OneDrive, które mogą wyszukiwać grupy ról zdefiniowane w parametrze`Users`. Ten filtr umożliwia członkom grupy ról wyszukiwanie tylko skrzynek pocztowych lub kont OneDrive w określonej agencji, na przykład `"Mailbox_Department -eq 'FourthCoffee'"`.

  - `SiteContent`: Ten filtr zawiera dwa oddzielne filtry. Pierwszy `SiteContent_Path` określa lokacje SharePoint w agencji, które mogą wyszukiwać grupy ról zdefiniowane w parametrze`Users`. Na przykład `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. Drugi `SiteContent_Path` filtr (połączony z pierwszym `SiteContent_Path` filtrem `or` przez operatora) określa domenę OneDrive agencji (nazywaną również domeną *MySite*). Na przykład `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Możesz również użyć filtru `Site_Path` zamiast filtru `SiteContent` . Filtry `Site` i `SiteContent` są wymienne i nie mają wpływu na filtry uprawnień wyszukiwania opisane w tym artykule.

    > [!IMPORTANT]
    > `SiteContent` Dlaczego filtr OneDrive jest uwzględniony w poprzednim filtrze uprawnień wyszukiwania? `Mailbox` Mimo że filtr ma zastosowanie *zarówno* do skrzynek pocztowych, jak i kont OneDrive, dołączenie filtru SharePoint wykluczałoby konta OneDrive, jeśli filtr OneDrive `Site` również nie został dołączny. Jeśli filtr uprawnień wyszukiwania nie zawiera filtru SharePoint, nie trzeba będzie dołączać oddzielnego filtru OneDrive, ponieważ filtr Skrzynka pocztowa będzie zawierać konta OneDrive w zakresie granicy zgodności. Innymi słowy filtr uprawnień wyszukiwania z tylko filtrem `Mailbox` obejmowałby zarówno skrzynki pocztowe, jak i konta OneDrive.

Poniżej przedstawiono przykłady dwóch filtrów uprawnień wyszukiwania, które zostałyby utworzone w celu obsługi scenariusza granic zgodności firmy Contoso. Oba te przykłady obejmują listę filtrów rozdzielanych przecinkami, w której filtry skrzynki pocztowej i witryny są uwzględniane w tym samym filtrze uprawnień wyszukiwania i są oddzielone przecinkami.
  
### <a name="fourth-coffee"></a>Czwarta kawa

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Składnia `Filters` parametrów w poprzednich przykładach zawiera *listę filtrów*. Lista filtrów to filtr zawierający filtr skrzynki pocztowej i filtr ścieżki witryny oddzielony przecinkami. W poprzednim przykładzie zwróć uwagę, że przecinek oddziela i `SiteContent` filtruje`Mailbox`: `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. Gdy ten filtr jest przetwarzany podczas uruchamiania wyszukiwania zbierania elektronicznych materiałów dowodowych, z listy filtrów są tworzone dwa filtry uprawnień wyszukiwania: jeden filtr skrzynki pocztowej i jeden filtr SharePoint/OneDrive. Alternatywą dla korzystania z listy filtrów byłoby utworzenie dwóch oddzielnych filtrów uprawnień wyszukiwania dla każdej agencji: jeden filtr uprawnień wyszukiwania dla atrybutu skrzynki pocztowej i jeden filtr atrybutów SharePoint i OneDrive lokacji. W obu przypadkach wyniki będą takie same. Korzystanie z listy filtrów lub tworzenie oddzielnych filtrów uprawnień wyszukiwania jest kwestią preferencji.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Jak działają filtry uprawnień wyszukiwania w tym scenariuszu?

Poniżej przedstawiono sposób stosowania filtrów uprawnień wyszukiwania dla każdej agencji w tym scenariuszu.

1. Filtr `Mailbox` jest najpierw stosowany w celu zdefiniowania lokalizacji zawartości, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. W takim przypadku menedżerowie zbierania elektronicznych materiałów dowodowych coho Winery mogą przeszukiwać tylko skrzynki pocztowe i OneDrive konta użytkowników, których właściwość Skrzynka pocztowa *działu* ma wartość **FourthCoffee**; Menedżerowie zbierania elektronicznych materiałów dowodowych coho Winery mogą przeszukiwać tylko skrzynki pocztowe i OneDrive konta użytkowników, których właściwość skrzynki pocztowej *działu* ma wartość **CohoWinery**. Filtr `Mailbox` jest *filtrem lokalizacji zawartości*, ponieważ określa lokalizacje zawartości, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. W obu filtrach menedżerowie zbierania elektronicznych materiałów dowodowych mogą przeszukiwać tylko lokalizacje zawartości z określoną wartością właściwości skrzynki pocztowej.

2. Po zdefiniowaniu lokalizacji zawartości, które można przeszukiwać, następna część filtru definiuje zawartość, którą mogą wyszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. Pierwszy `SiteContent` filtr umożliwia menedżerom fourth coffee eDiscovery wyszukiwanie tylko dokumentów, które mają właściwość ścieżki witryny, która zawiera (lub zaczyna się od) `https://contoso.sharepoint.com/sites/FourthCoffee`; Menedżerowie zbierania elektronicznych materiałów dowodowych coho Winery mogą wyszukiwać tylko dokumenty, które mają właściwość ścieżki witryny zawierającą (lub zaczyna się od) `https://contoso.sharepoint.com/sites/CohoWinery`. W związku z tym dwa `SiteContent` filtry są *filtrami zawartości* , ponieważ definiują zawartość, która może być wyszukiwana. W obu filtrach menedżerowie zbierania elektronicznych materiałów dowodowych mogą wyszukiwać tylko dokumenty z określoną wartością właściwości dokumentu. Wszystkie filtry związane z SharePoint są filtrami zawartości, ponieważ właściwości witryny z możliwością wyszukiwania są ostemplowane we wszystkich dokumentach. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania uprawnień pod kątem zbierania elektronicznych materiałów dowodowych](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Chociaż scenariusz w tym artykule nie używa ich, możesz również użyć filtrów zawartości skrzynki pocztowej, aby określić zawartość, którą mogą wyszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. Składnia filtrów zawartości skrzynki pocztowej to `"MailboxContent_<property> -<comparison operator> '<value>'"`. Filtry zawartości można tworzyć na podstawie zakresów dat, adresatów i domen lub dowolnej właściwości poczty e-mail z możliwością wyszukiwania. Na przykład ten filtr umożliwia menedżerom zbierania elektronicznych materiałów dowodowych wyszukiwanie tylko elementów poczty wysłanych lub odebranych przez użytkowników w domenie contoso.com: `"MailboxContent_Participants -like 'contoso.com'"`. Aby uzyskać więcej informacji na temat filtrów zawartości skrzynki pocztowej, zobacz [Konfigurowanie filtrowania uprawnień wyszukiwania](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Filtr uprawnień wyszukiwania jest przyłączony do zapytania wyszukiwania przez operator logiczny **AND** . Oznacza to, że gdy menedżer zbierania elektronicznych materiałów dowodowych w jednej z agencji uruchamia wyszukiwanie zbierania elektronicznych materiałów dowodowych, elementy zwracane przez wyszukiwanie muszą być zgodne z zapytaniem wyszukiwania i warunkami zdefiniowanymi w filtrze uprawnień wyszukiwania.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>Krok 4. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych dla dochodzeń wewnątrzagencyjnych

Ostatnim krokiem jest utworzenie sprawy zbierania elektronicznych materiałów dowodowych (standardowa) lub sprawy zbierania elektronicznych materiałów dowodowych (Premium) w portalu zgodności, a następnie dodanie grupy ról utworzonej w kroku 2 jako element członkowski sprawy. Skutkuje to dwoma ważnymi cechami używania granic zgodności:
  
- Tylko członkowie grupy ról dodana do sprawy będą mogli wyświetlać przypadek i uzyskiwać do nich dostęp w portalu zgodności. Jeśli na przykład grupa ról Fourth Coffee Investigators jest jedynym członkiem sprawy, członkowie grupy ról Fourth Coffee eDiscovery Managers (lub członkowie jakiejkolwiek innej grupy ról) nie będą mogli zobaczyć sprawy ani uzyskać do niej dostępu.

- Gdy członek grupy ról przypisanej do sprawy uruchamia wyszukiwanie skojarzone ze sprawą, będzie mógł przeszukiwać tylko lokalizacje zawartości w ramach swojej agencji (która jest definiowana przez filtr uprawnień wyszukiwania utworzony w kroku 3).

Aby utworzyć przypadek i przypisać członków:

1. Przejdź do strony **eDiscovery (Standard)** lub **eDiscovery (Premium)** w portalu zgodności i utwórz przypadek.

2. Na liście przypadków kliknij nazwę utworzonego przypadku.

3. Dodaj grupy ról jako elementy członkowskie do sprawy. Aby uzyskać instrukcje, zobacz jeden z następujących artykułów:

   - [Dodawanie członków do sprawy zbierania elektronicznych materiałów dowodowych (standardowa)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

   - [Dodawanie członków do sprawy zbierania elektronicznych materiałów dowodowych (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Podczas dodawania grupy ról do sprawy można dodać tylko grupy ról, do których należysz.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Wyszukiwanie i eksportowanie zawartości w środowiskach z wieloma lokalizacjami geograficznymi

Filtry uprawnień wyszukiwania umożliwiają również kontrolowanie, gdzie zawartość jest kierowana do eksportu i które centrum danych można przeszukiwać podczas wyszukiwania lokalizacji zawartości w [środowisku SharePoint Multi-Geo](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).
  
- **Eksportuj wyniki wyszukiwania:** Wyniki wyszukiwania można wyeksportować ze skrzynek pocztowych Exchange, SharePoint witryn i kont OneDrive z określonego centrum danych. Oznacza to, że można określić lokalizację centrum danych, z których zostaną wyeksportowane wyniki wyszukiwania.

    Użyj parametru *Region* dla poleceń cmdlet **New-ComplianceSecurityFilter** lub **Set-ComplianceSecurityFilter** , aby utworzyć lub zmienić centrum danych, przez które eksport będzie kierowany.
  
    |**Wartość parametru**|**Lokalizacja centrum danych**|
    |:-----|:-----|
    |NAM  <br/> |Ameryka Północna (centra danych znajdują się w Stanach Zjednoczonych)  <br/> |
    |EUR  <br/> |Europie  <br/> |
    |APC  <br/> |Azja i Pacyfik  <br/> |
    |CNA <br/> |Kanada|
    |||

- **Kierowanie wyszukiwania zawartości:** Wyszukiwanie zawartości witryn SharePoint i kont OneDrive można kierować do satelitarnego centrum danych. Oznacza to, że można określić lokalizację centrum danych, w którym będą uruchamiane wyszukiwania.

    Użyj jednej z następujących wartości parametru *Region*, aby kontrolować lokalizację centrum danych, w ramach którego będą uruchamiane wyszukiwania podczas wyszukiwania SharePoint lokacji i kont OneDrive.
  
    |**Wartość parametru**|**Lokalizacje routingu centrum danych dla SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |NAS  <br/> |
    |EUR  <br/> |Europie  <br/> |
    |APC  <br/> |Azja i Pacyfik  <br/> |
    |CNA  <br/> |NAS  <br/> |
    |AUS  <br/> |Azja i Pacyfik  <br/> |
    |KOR  <br/> |Domyślne centrum danych organizacji  <br/> |
    |GBR  <br/> |Europie  <br/> |
    |JPN  <br/> |Azja i Pacyfik  <br/> |
    |KOMERCYJNY  <br/> |Azja i Pacyfik  <br/> |
    |LAM  <br/> |NAS  <br/> |
    |ANI  <br/> |Europie |
    |BIUSTONOSZ  <br/> |Północnoamerykańskie centra danych |
    |||

   Jeśli nie określisz parametru *Region* dla filtru uprawnień wyszukiwania, zostanie przeszukany podstawowy region SharePoint organizacji. Wyniki wyszukiwania są eksportowane do najbliższego centrum danych.

   Aby uprościć tę koncepcję, parametr *Region* steruje centrum danych używanym do wyszukiwania zawartości w SharePoint i OneDrive. Nie dotyczy to wyszukiwania zawartości w Exchange, ponieważ Exchange wyszukiwania zawartości nie są powiązane lokalizacją geograficzną centrów danych. Ponadto ta sama wartość parametru *Region* może również dyktować centrum danych, przez które eksporty są kierowane. Jest to często konieczne do kontrolowania przenoszenia danych między zarządcami geograficznym.

> [!NOTE]
> Jeśli używasz zbierania elektronicznych materiałów dowodowych (Premium), parametr *Region* nie kontroluje regionu, z którym są eksportowane dane. Dane są eksportowane z centralnej lokalizacji organizacji. Ponadto wyszukiwanie zawartości w SharePoint i OneDrive nie jest powiązane lokalizacją geograficzną centrów danych. Przeszukiwane są wszystkie centra danych. Aby uzyskać więcej informacji na temat zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Omówienie rozwiązania zbierania elektronicznych materiałów dowodowych (Premium) w Microsoft 365](overview-ediscovery-20.md).

Poniżej przedstawiono przykłady używania parametru *Region* podczas tworzenia filtrów uprawnień wyszukiwania dla granic zgodności. Zakłada to, że spółka zależna Fourth Coffee znajduje się w Ameryka Północna i że coho Winery znajduje się w Europie.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Podczas wyszukiwania i eksportowania zawartości w środowiskach z wieloma lokalizacjami geograficznymi należy pamiętać o następujących kwestiach.
  
- Parametr *Region* nie kontroluje wyszukiwań Exchange skrzynek pocztowych. Wszystkie centra danych będą przeszukiwane podczas wyszukiwania skrzynek pocztowych. Aby ograniczyć zakres wyszukiwania Exchange skrzynek pocztowych, użyj parametru *Filtry* podczas tworzenia lub zmieniania filtru uprawnień wyszukiwania.

- Jeśli menedżer zbierania elektronicznych materiałów dowodowych musi wyszukiwać w wielu regionach SharePoint, musisz utworzyć inne konto użytkownika dla tego menedżera zbierania elektronicznych materiałów dowodowych do użycia w filtrze uprawnień wyszukiwania w celu określenia regionu, w którym znajdują się witryny SharePoint lub konta OneDrive. Aby uzyskać więcej informacji na temat konfigurowania tej opcji, zobacz sekcję "Wyszukiwanie zawartości w środowisku SharePoint Multi-Geo" w [sekcji Wyszukiwanie zawartości](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment).

- Podczas wyszukiwania zawartości w SharePoint i OneDrive parametr *Region* kieruje wyszukiwania do lokalizacji podstawowej lub satelitarnej, w której menedżer zbierania elektronicznych materiałów dowodowych przeprowadzi badania zbierania elektronicznych materiałów dowodowych. Jeśli menedżer zbierania elektronicznych materiałów dowodowych wyszukuje witryny SharePoint i OneDrive poza regionem określonym w filtrze uprawnień wyszukiwania, wyniki wyszukiwania nie zostaną zwrócone.

- Podczas eksportowania wyników wyszukiwania z eDiscovery (Standard) zawartość ze wszystkich lokalizacji zawartości (w tym Exchange, Skype dla firm, SharePoint, OneDrive i innych usług, które można wyszukiwać za pomocą narzędzia wyszukiwania zawartości) jest przekazywana do lokalizacji usługi Azure Storage w centrum danych określonym przez *narzędzie wyszukiwania zawartości Parametr regionu*. Pomaga to organizacjom zachować zgodność, nie zezwalając na eksportowanie zawartości przez kontrolowane granice. Jeśli w filtrze uprawnień wyszukiwania nie określono żadnego regionu, zawartość jest przekazywana do podstawowego centrum danych organizacji.

  Podczas eksportowania zawartości z funkcji zbierania elektronicznych materiałów dowodowych (Premium) nie można kontrolować, gdzie zawartość jest przekazywana przy użyciu parametru *Region*. Zawartość jest przekazywana do lokalizacji usługi Azure Storage w centrum danych w centralnej lokalizacji organizacji. Aby uzyskać listę lokalizacji geograficznych opartych na centralnej lokalizacji, zobacz [Microsoft 365 Konfiguracja zbierania elektronicznych elektronicznych materiałów dowodowych w wielu obszarach geograficznych](../enterprise/multi-geo-ediscovery-configuration.md).

- Aby dodać lub zmienić region, możesz edytować istniejący filtr uprawnień wyszukiwania, uruchamiając następujące polecenie:

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Używanie granic zgodności dla lokacji centrum SharePoint

[SharePoint lokacje piasty](/sharepoint/dev/features/hub-site/hub-site-overview) często są zgodne z tymi samymi granicami geograficznymi lub granicami agencji, które są zgodne ze zgodnością zbierania elektronicznych materiałów dowodowych. Oznacza to, że możesz użyć właściwości identyfikatora lokacji centrum, aby utworzyć granicę zgodności. W tym celu użyj polecenia cmdlet [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) w programie SharePoint Online PowerShell, aby uzyskać identyfikator SiteId dla lokacji centrum, a następnie użyj tej wartości dla właściwości identyfikatora działu, aby utworzyć filtr uprawnień wyszukiwania.

Użyj następującej składni, aby utworzyć filtr uprawnień wyszukiwania dla witryny centrum SharePoint:

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Oto przykład tworzenia filtru uprawnień wyszukiwania dla witryny centrum dla agencji Coho Winery:

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Ograniczenia granic zgodności

Podczas zarządzania przypadkami zbierania elektronicznych materiałów dowodowych i badaniami, które korzystają z granic zgodności, należy pamiętać o następujących ograniczeniach.
  
- Podczas tworzenia i uruchamiania wyszukiwania można wybrać lokalizacje zawartości spoza agencji. Jednak ze względu na filtr uprawnień wyszukiwania zawartość z tych lokalizacji nie jest uwzględniana w wynikach wyszukiwania.

- Granice zgodności nie mają zastosowania do blokad w przypadkach zbierania elektronicznych materiałów dowodowych. Oznacza to, że menedżer zbierania elektronicznych materiałów dowodowych w jednej agencji może zawiesić użytkownika w innej agencji. Jednak granica zgodności zostanie wymuszona, jeśli menedżer zbierania elektronicznych materiałów dowodowych przeszukuje lokalizacje zawartości użytkownika, który został wstrzymany. Oznacza to, że menedżer zbierania elektronicznych elektronicznych materiałów dowodowych nie będzie mógł przeszukiwać lokalizacji zawartości użytkownika, nawet jeśli użytkownik mógł zostać wstrzymany.

- Jeśli masz przypisany filtr uprawnień wyszukiwania (skrzynkę pocztową lub filtr witryny) i spróbujesz wyeksportować niezainicjowane elementy do wyszukiwania obejmującego wszystkie witryny SharePoint w organizacji, zostanie wyświetlony następujący komunikat o błędzie: `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Jeśli masz przypisany filtr uprawnień wyszukiwania i chcesz wyeksportować niezaindeksowane elementy z SharePoint, musisz ponownie uruchomić wyszukiwanie i uwzględnić określone witryny SharePoint do wyszukiwania. W przeciwnym razie będzie można eksportować tylko indeksowane elementy z wyszukiwania obejmującego wszystkie SharePoint witryn. Aby uzyskać więcej informacji na temat opcji podczas eksportowania wyników wyszukiwania, zobacz [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md#step-1-prepare-search-results-for-export).

- Filtry uprawnień wyszukiwania nie są stosowane do Exchange folderów publicznych.

## <a name="more-information"></a>Więcej informacji

- Jeśli skrzynka pocztowa zostanie anulowana lub usunięta nietrwale, użytkownik nie będzie już brany pod uwagę w granicach zgodności. Jeśli blokada została umieszczona w skrzynce pocztowej po jej usunięciu, zawartość zachowana w skrzynce pocztowej nadal podlega filtrowi uprawnień zgodności lub uprawnień wyszukiwania.

- Jeśli dla użytkownika zostaną zaimplementowane filtry granic zgodności i uprawnień wyszukiwania, zalecamy, aby nie usuwać skrzynki pocztowej użytkownika, a nie jego konta OneDrive. Innymi słowy, jeśli usuniesz skrzynkę pocztową użytkownika, należy również usunąć konto OneDrive użytkownika, ponieważ mailbox_RecipientFilter służy do wymuszania filtru uprawnień wyszukiwania dla OneDrive.

- Filtry granic zgodności i uprawnień wyszukiwania zależą od atrybutów ostemplowanych na zawartości w Exchange, OneDrive i SharePoint oraz od późniejszego indeksowania tej sygnatury zawartości.

- Nie zalecamy używania filtrów wykluczeń (na przykład użycia `-not()` w filtrze uprawnień wyszukiwania) dla granicy zgodności opartej na zawartości. Użycie filtru wykluczeń może mieć nieoczekiwane wyniki, jeśli zawartość z ostatnio zaktualizowanymi atrybutami nie została zindeksowana.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**KtoTo można tworzyć filtry uprawnień wyszukiwania i zarządzać nimi (przy użyciu poleceń cmdlet New-ComplianceSecurityFilter i Set-ComplianceSecurityFilter)?**
  
Aby tworzyć, wyświetlać i modyfikować filtry uprawnień wyszukiwania, musisz być członkiem grupy ról Zarządzanie organizacją w portalu zgodności.
  
**Jeśli menedżer zbierania elektronicznych materiałów dowodowych jest przypisany do więcej niż jednej grupy ról obejmującej wiele agencji, jak wyszukiwać zawartość w jednej lub drugiej agencji?**
  
Menedżer zbierania elektronicznych materiałów dowodowych może dodać parametry do zapytania wyszukiwania, które ograniczają wyszukiwanie do określonej agencji. Jeśli na przykład organizacja określiła właściwość **CustomAttribute10** w celu odróżnienia agencji, może dołączyć następujące informacje do zapytania wyszukiwania, aby wyszukać skrzynki pocztowe i OneDrive konta w określonej agencji: `CustomAttribute10:<value>`.
  
**Co się stanie, jeśli wartość atrybutu używanego jako atrybut zgodności w filtrze uprawnień wyszukiwania zostanie zmieniona?**
  
Wymuszanie granicy zgodności przez filtr uprawnień wyszukiwania trwa do trzech dni, jeśli wartość atrybutu używanego w filtrze zostanie zmieniona. Na przykład w scenariuszu firmy Contoso załóżmy, że użytkownik w agencji Fourth Coffee jest przenoszony do agencji Coho Winery. W związku z tym wartość atrybutu **Department** obiektu użytkownika została zmieniona z *FourthCoffee* na *CohoWinery*. W tej sytuacji fourth coffee eDiscovery i inwestorzy otrzymają wyniki wyszukiwania dla tego użytkownika przez maksymalnie trzy dni po zmianie atrybutu. Podobnie, to trwa do trzech dni, zanim Coho Winery eDiscovery menedżerów i śledczych uzyskać wyniki wyszukiwania dla użytkownika.
  
**Czy menedżer zbierania elektronicznych materiałów dowodowych może wyświetlać zawartość z dwóch oddzielnych granic zgodności?**
  
Tak, można to zrobić podczas wyszukiwania Exchange skrzynek pocztowych przez dodanie menedżera zbierania elektronicznych materiałów dowodowych do grup ról, które mają wgląd w obie agencje. Jednak podczas wyszukiwania SharePoint witryn i kont OneDrive menedżer zbierania elektronicznych materiałów dowodowych może wyszukiwać zawartość w różnych granicach zgodności tylko wtedy, gdy agencje znajdują się w tym samym regionie lub lokalizacji geograficznej. **Uwaga:** To ograniczenie dla witryn nie ma zastosowania w przypadku zbierania elektronicznych materiałów dowodowych (Premium), ponieważ wyszukiwanie zawartości w SharePoint i OneDrive nie jest powiązane lokalizacją geograficzną.
  
**Czy filtry uprawnień wyszukiwania działają w przypadku blokad zbierania elektronicznych materiałów dowodowych, zasad przechowywania Microsoft 365 lub DLP?**
  
Nie, w tej chwili nie ma takiej wersji.
  
**Czy mogę nadal wyszukiwać SharePoint, jeśli określę region, w którym ma zostać wyeksportowana zawartość, ale nie mam organizacji SharePoint w tym regionie?**
  
Jeśli region określony w filtrze uprawnień wyszukiwania nie istnieje w organizacji, zostanie przeszukany region domyślny.
  
**Jaka jest maksymalna liczba filtrów uprawnień wyszukiwania, które można utworzyć w organizacji?**
  
Nie ma limitu liczby filtrów uprawnień wyszukiwania, które można utworzyć w organizacji. Jednak zapytanie wyszukiwania może mieć maksymalnie 100 warunków. W takim przypadku warunek jest definiowany jako coś, co jest połączone z zapytaniem przez operator logiczny (na przykład **AND**, **OR** i **NEAR**). Limit liczby warunków obejmuje samo zapytanie wyszukiwania oraz wszystkie filtry uprawnień wyszukiwania, które są stosowane do użytkownika, który uruchamia wyszukiwanie. W związku z tym, tym więcej filtrów uprawnień wyszukiwania masz (zwłaszcza jeśli te filtry są stosowane do tego samego użytkownika lub grupy użytkowników), tym większe prawdopodobieństwo przekroczenia maksymalnej liczby warunków wyszukiwania.

Aby zrozumieć, jak działa ten limit, musisz zrozumieć, że filtr uprawnień wyszukiwania jest dołączany do zapytania wyszukiwania po uruchomieniu wyszukiwania. Filtr uprawnień wyszukiwania jest przyłączony do zapytania wyszukiwania przez operator logiczny **AND** . Logika zapytania dla zapytania wyszukiwania i pojedynczy filtr uprawnień wyszukiwania będą wyglądać następująco:

```text
<SearchQuery> AND <PermissionsFilter>
```

Wiele filtrów uprawnień wyszukiwania jest łączonych ze sobą przez operator logiczny **OR** , a następnie te warunki są połączone z zapytaniem wyszukiwania przez operatora **AND** .

Logika zapytania dla zapytania wyszukiwania i wiele filtrów uprawnień wyszukiwania będzie wyglądać następująco:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Możliwe, że samo zapytanie wyszukiwania może składać się z wielu warunków połączonych przez operatory logiczne. Każdy warunek w zapytaniu wyszukiwania będzie również liczone względem limitu 100 warunków.

Ponadto liczba filtrów uprawnień wyszukiwania dołączonych do zapytania zależy od użytkownika, który uruchamia wyszukiwanie. Gdy określony użytkownik uruchamia wyszukiwanie, filtry uprawnień wyszukiwania, które są stosowane do użytkownika (który jest zdefiniowany przez parametr *Użytkownicy* w filtrze) są dołączane do zapytania. Organizacja może mieć setki filtrów uprawnień wyszukiwania, ale jeśli do tych samych użytkowników zostanie zastosowanych więcej niż 100 filtrów, prawdopodobnie limit 100 warunków zostanie przekroczony, gdy ci użytkownicy będą uruchamiać wyszukiwania.

Jest jeszcze jedna rzecz, o której należy pamiętać o limicie warunku. Liczba określonych witryn SharePoint uwzględnionych w filtrach zapytań wyszukiwania lub uprawnień wyszukiwania również jest liczona względem tego limitu. 

Aby uniemożliwić organizacji osiągnięcie limitu warunków, zachowaj maksymalną liczbę filtrów uprawnień do wyszukiwania w organizacji, aby spełnić wymagania biznesowe.
