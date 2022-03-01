---
title: Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Dowiedz się, jak za pomocą granic zgodności tworzyć granice logiczne sterujące lokalizacjami zawartości użytkowników, które menedżer zbierania elektronicznych materiałów dowodowych może wyszukiwać w Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5fe023391823abbde2cb289926863bbcbb98dfb2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021332"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych

Wskazówki w tym artykule można stosować podczas korzystania z podstawowych funkcji zbierania elektronicznych materiałów dowodowych lub Advanced eDiscovery do zarządzania badaniami.

Granice zgodności tworzą logiczne granice w organizacji, które kontrolują lokalizacje zawartości użytkowników (takie jak skrzynki pocztowe, konta OneDrive i witryny SharePoint), które menedżerowie zbierania elektronicznych materiałów dowodowych mogą wyszukiwać. Ponadto granice zgodności kontrolują, kto może mieć dostęp do spraw zbierania elektronicznych materiałów dowodowych używanych do zarządzania sprawami prawnie, zasobami kadrami lub innymi badaniami w organizacji. Zgodność z przepisami jest często potrzebna w przypadku wielonarodowych firm, które muszą przestrzegać przepisów i zarządców geograficznych, a także dla instytucji rządowych, które często są podzielone na różne instytucje. W Microsoft 365 zgodności pomagają spełnić te wymagania podczas przeszukiwania zawartości i zarządzania badaniami za pomocą spraw zbierania elektronicznych materiałów dowodowych.
  
W przykładzie na poniższej ilustracji wyjaśniono, jak działają granice zgodności.
  
![Granice zgodności składają się z filtrów uprawnień wyszukiwania, które sterują dostępem do instytucji i grup ról administratorów, które kontrolują dostęp do spraw zbierania elektronicznych materiałów dowodowych.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
W tym przykładzie Contoso LTD to organizacja, która składa się z dwóch przedstawicielsze: Fourth Coffee i Coho Winery. Firma wymaga, aby menedżerowie zbierania elektronicznych materiałów dowodowych i osoby schłodne mogą przeszukiwać tylko skrzynki pocztowe usługi Exchange, konta OneDrive oraz witryny SharePoint w ich agencji. Ponadto menedżerowie zbierania elektronicznych materiałów dowodowych i jego kierownicy mogą widzieć tylko sprawy zbierania elektronicznych materiałów dowodowych w swoich agencji i mogą uzyskać dostęp tylko do spraw, których są członkami. Ponadto w tym scenariuszu chętni nie mogą umieszczać lokalizacji zawartości w hold czy eksportować zawartości ze sprawy. Poniżej opisano, w jaki sposób granice zgodności spełniają te wymagania.
  
- Funkcja filtrowania uprawnień wyszukiwania dla zbierania elektronicznych materiałów dowodowych steruje lokalizacjami zawartości, które mogą wyszukiwać menedżerowie i osoby zbierania elektronicznych materiałów dowodowych. Oznacza to, że menedżerowie zbierania elektronicznych materiałów dowodowych i kierownicy z przedstawicielstw Fourth Coffee mogą przeszukiwać tylko lokalizacje zawartości w przedstawicielstwie Fourth Coffee. To samo ograniczenie dotyczy przedstawicielstwo Coho Winery.

- [Grupy ról](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) zawierają następujące funkcje do zachowania zgodności:

  - Kontrolowanie, kto może widzieć sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Oznacza to, że kierownicy i słoje zbierania elektronicznych materiałów dowodowych mogą zobaczyć tylko sprawy zbierania elektronicznych materiałów dowodowych w ich agencji.

  - Kontrolowanie, kto może przypisywać członków do sprawy zbierania elektronicznych materiałów dowodowych. Oznacza to, że menedżerowie zbierania elektronicznych materiałów dowodowych i jego członkowie mogą przypisywać członków tylko do spraw, do których sami są członkami.

  - Kontroluj zadania związane z zbierania elektronicznych materiałów dowodowych, które mogą wykonywać członkowie, dodając lub usuwając role, które przypisują określone uprawnienia.

- Po zastosowaniu filtru uprawnień wyszukiwania do grupy ról członkowie tej grupy ról mogą wykonywać następujące akcje związane z wyszukiwaniem, o ile do grupy ról przypisano uprawnienia do wykonywania akcji:

  - Wyszukiwanie zawartości

  - Podgląd wyników wyszukiwania

  - Eksportowanie wyników wyszukiwania

  - Przeczyszczanie elementów zwróconych przez wyszukiwanie

Oto proces konfigurowania granic zgodności:
  
[Krok 1. Identyfikowanie atrybutu użytkownika w celu zdefiniowania agencji](#step-1-identify-a-user-attribute-to-define-your-agencies)

[Krok 2. Tworzenie grupy ról dla każdej agencji](#step-2-create-a-role-group-for-each-agency)

[Krok 3. Tworzenie filtru uprawnień wyszukiwania w celu wymuszenia granicy zgodności](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[Krok 4. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych dla badań wewnętrznej agencji](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Przed skonfigurowaniem granic zgodności

- Użytkownicy muszą mieć przypisaną licencję Exchange Online użytkowników. Aby to sprawdzić, użyj polecenia cmdlet [Get-User](/powershell/module/exchange/get-user) w programie Exchange Online PowerShell.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>Krok 1. Identyfikowanie atrybutu użytkownika w celu zdefiniowania agencji

Pierwszym krokiem jest wybranie atrybutu definiującego agencje. Ten atrybut służy do tworzenia filtru uprawnień wyszukiwania, który ogranicza menedżera zbierania elektronicznych materiałów dowodowych w celu wyszukiwania tylko lokalizacji zawartości użytkowników, którym przypisano określoną wartość tego atrybutu. Załóżmy na przykład, że contoso decyduje się na użycie **atrybutu Department** (Dział). Wartość tego atrybutu dla użytkowników w przedstawicielscy firmy Fourth Coffee `FourthCoffee` byłaby, a wartość dla użytkowników w przedstawicielsce Coho Winery byłaby .`CohoWinery` W kroku 3 tej pary (na przykład *Department:FourthCoffee*) możesz ograniczyć lokalizacje zawartości użytkowników, `attribute:value` które menedżerowie zbierania elektronicznych materiałów dowodowych mogą wyszukiwać. 
  
Oto kilka przykładów atrybutów użytkownika, których można używać do granic zgodności:
  
- Company

- CustomAttribute1 — CustomAttribute15

- Department

- Pakiet Office

- KrajOrRegion (dwulitowy kod kraju)

Aby uzyskać pełną listę, zobacz pełną listę obsługiwanych filtrów [skrzynek pocztowych](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties).

## <a name="step-2-create-a-role-group-for-each-agency"></a>Krok 2. Tworzenie grupy ról dla każdej agencji

Następnym krokiem jest utworzenie grup ról w grupie Centrum zgodności platformy Microsoft 365 z agencjami. Zalecamy utworzenie grupy ról przez skopiowanie wbudowanej grupy menedżerów zbierania elektronicznych materiałów dowodowych, dodanie odpowiednich członków i usunięcie ról, które mogą nie mieć zastosowania do Twoich potrzeb. Aby uzyskać więcej informacji na temat ról związanych z zbierania elektronicznych materiałów dowodowych, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).
  
Aby utworzyć grupy ról, przejdź do strony Uprawnienia  w programie Centrum zgodności platformy Microsoft 365 i utwórz grupę ról dla każdego zespołu w każdej agencji, która będzie zarządzać badaniami za pomocą granic zgodności i spraw zbierania elektronicznych materiałów dowodowych.
  
W scenariuszu z granicami zgodności firmy Contoso należy utworzyć cztery grupy ról i dodać odpowiednich członków do każdej z nich.
  
- Menedżerowie zbierania elektronicznych materiałów dowodowych Fourth Coffee

- Fourth Coffee Nasadki

- Menedżerowie zbierania elektronicznych materiałów dowodowych w Coho Winery

- Słoje Coho Winery
  
Aby spełnić wymagania scenariusza zgodności firmy Contoso, należy również usunąć role Wstrzymaj i  Eksportuj  z grupy ról, aby zapobiec umieszczaniu blokady w lokalizacjach zawartości i eksportowaniu zawartości ze sprawy.

> [!IMPORTANT]
> Jeśli rola zostanie dodana lub usunięta z grupy ról dodanej jako członek sprawy, grupa ról zostanie automatycznie usunięta jako członek sprawy (lub w dowolnym przypadku, do których należy grupa ról). Przyczyną tego jest ochrona organizacji przed nieumyślnie udostępnieniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich spraw, do których była członkiem.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>Krok 3. Tworzenie filtru uprawnień wyszukiwania w celu wymuszenia granicy zgodności

Kolejnym krokiem po utworzeniu grup ról dla każdej agencji jest utworzenie filtrów uprawnień wyszukiwania, które skojarzą każdą grupę ról z jej określoną agencją i definiują samą granicę zgodności. Musisz utworzyć jeden filtr uprawnień wyszukiwania dla każdej agencji. Aby uzyskać więcej informacji na temat tworzenia filtrów uprawnień zabezpieczeń, zobacz [Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości](permissions-filtering-for-content-search.md).
  
Oto składnia używana do tworzenia filtru uprawnień wyszukiwania używanego do tworzenia granic zgodności dla scenariusza w tym artykule.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Oto opis każdego parametru w poleceniu:
  
- `FilterName`: określa nazwę filtru. Użyj nazwy opisowej lub identyfikującej agencję, w których został użyty filtr.

- `Users`— określa użytkowników lub grupy, dla których ten filtr jest stosowany do akcji wyszukiwania, które wykonują. W przypadku granic zgodności ten parametr określa grupy ról (utworzone w kroku 3) w agencji, dla których jest tworzony filtr. Ten parametr ma wiele wartości, więc można dołączyć jedną lub więcej grup ról oddzielonych przecinkami.

- `Filters`— określa kryteria wyszukiwania filtru. W przypadku granic zgodności należy zdefiniować następujące filtry. Każda z nich ma zastosowanie do różnych lokalizacji zawartości.

  - `Mailbox`— określa skrzynki pocztowe lub OneDrive, które mogą wyszukiwać grupy ról zdefiniowane w `Users` parametrze. Ten filtr umożliwia członkom grupy ról przeszukiwanie tylko skrzynek pocztowych lub OneDrive w określonej agencji, na `"Mailbox_Department -eq 'FourthCoffee'"`przykład.

  - `SiteContent`: Ten filtr zawiera dwa oddzielne filtry. Pierwszy określa `SiteContent_Path` witrynę SharePoint w agencji, które grupy ról zdefiniowane `Users` w parametrze mogą wyszukiwać. Na przykład `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. Drugi filtr `SiteContent_Path` (połączony z `SiteContent_Path` `or` pierwszym filtrem przez operatora) określa domenę sieciową OneDrive agencji (nazywaną również domeną *Mojej* domeny). Na przykład `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Możesz także użyć filtru `Site_Path` w miejscu filtru `SiteContent` . Filtry `Site` i `SiteContent` filtry są zamiennie i nie mają wpływu na filtry uprawnień wyszukiwania opisane w tym artykule.

    > [!IMPORTANT]
    > Dlaczego filtr filtru `SiteContent` OneDrive został uwzględniony w poprzednim filtrze uprawnień wyszukiwania? Filtr dotyczy `Mailbox` zarówno skrzynek  pocztowych, jak i kont usługi OneDrive, jednak dołączenie filtru SharePoint `Site` wykluczałoby OneDrive kont, jeśli nie uwzględnisz filtru OneDrive. Jeśli filtr uprawnień wyszukiwania nie zawierał filtru SharePoint, nie trzeba uwzględniać oddzielnego filtru OneDrive, ponieważ filtr Skrzynka pocztowa uwzględniał konta programu OneDrive w zakresie granicy zgodności. Innymi słowy, filtr uprawnień wyszukiwania tylko z `Mailbox` filtrem uwzględnia zarówno skrzynki pocztowe, jak i OneDrive konta.

Poniżej przedstawiono przykłady dwóch filtrów uprawnień wyszukiwania, które zostałyby utworzone w celu obsługi scenariusza zgodności firmy Contoso. Oba te przykłady obejmują listę filtrów rozdzielanych przecinkami, na której filtry skrzynki pocztowej i witryny są uwzględnione w tym samym filtrze uprawnień wyszukiwania i są rozdzielone przecinkami.
  
### <a name="fourth-coffee"></a>Fourth Coffee

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Składnia parametrów z `Filters` poprzednich przykładów obejmuje listę *filtrów*. Lista filtrów to filtr, który zawiera filtr skrzynki pocztowej i filtr ścieżki witryny oddzielony przecinkami. W poprzednim przykładzie przecinek oddziela i `Mailbox` filtruje `SiteContent` : `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. Podczas przetwarzania tego filtru podczas uruchamiania wyszukiwania zbierania elektronicznych materiałów dowodowych na liście filtrów są tworzone dwa filtry uprawnień wyszukiwania: jeden filtr skrzynki pocztowej i jeden filtr SharePoint/OneDrive filtr. Alternatywą dla używania listy filtrów jest utworzenie dwóch oddzielnych filtrów uprawnień wyszukiwania dla każdej agencji: jednego filtru uprawnień wyszukiwania dla atrybutu skrzynki pocztowej i jednego filtru dla atrybutów witryny usługi SharePoint i OneDrive witryny. W obu przypadkach wyniki będą takie same. Korzystanie z listy filtrów lub tworzenie oddzielnych filtrów uprawnień wyszukiwania wymaga preferencji.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Jak działają w tym scenariuszu filtry uprawnień wyszukiwania?

Poniżej opisano, jak w tym scenariuszu zastosowano filtry uprawnień wyszukiwania dla każdej agencji.

1. Filtr `Mailbox` jest stosowany najpierw do definiowania lokalizacji zawartości, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. W tym przypadku menedżerowie zbierania elektronicznych materiałów dowodowych Coho Winery mogą przeszukiwać tylko skrzynki pocztowe i OneDrive użytkowników, których właściwość *skrzynki* pocztowej Department ma wartość **FourthCoffee**. Menedżerowie zbierania elektronicznych materiałów dowodowych Coho Winery mogą przeszukiwać tylko skrzynki pocztowe i konta OneDrive użytkowników, których właściwość *skrzynki* pocztowej Department ma wartość **CohoWinery**. Filtr `Mailbox` jest *filtrem lokalizacji zawartości*, ponieważ określa lokalizacje zawartości, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. W obu filtrach menedżerowie zbierania elektronicznych materiałów dowodowych mogą przeszukiwać tylko lokalizacje zawartości o określonej wartości właściwości skrzynki pocztowej.

2. Po zdefiniowaniu lokalizacji zawartości, które mogą być przeszukiwane, następna część filtru definiuje zawartość, która może być przeszukiwana przez menedżerów zbierania elektronicznych materiałów dowodowych. Pierwszy filtr `SiteContent` umożliwia menedżerom zbierania elektronicznych materiałów dowodowych Fourth Coffee wyszukiwanie tylko dokumentów, które mają właściwość ścieżki witryny, która zawiera (lub zaczyna się od) `https://contoso.sharepoint.com/sites/FourthCoffee`; Menedżerowie zbierania elektronicznych materiałów dowodowych Coho Winery mogą przeszukiwać tylko dokumenty, które mają właściwość ścieżki witryny, która zawiera (lub zaczyna się od) `https://contoso.sharepoint.com/sites/CohoWinery`. Dlatego oba filtry są `SiteContent` filtrami *zawartości* , ponieważ definiują one zawartość, która może być wyszukiwana. W obu filtrach menedżerowie zbierania elektronicznych materiałów dowodowych mogą wyszukiwać tylko dokumenty o określonej wartości właściwości dokumentu. Wszystkie SharePoint są filtrami zawartości, ponieważ właściwości witryny, które można przeszukiwać, są stemplowane we wszystkich dokumentach. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania uprawnień dla zbierania elektronicznych materiałów dowodowych](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Chociaż scenariusze w tym artykule ich nie używają, możesz również użyć filtrów zawartości skrzynki pocztowej, aby określić zawartość, która może być wyszukiwana przez menedżerów zbierania elektronicznych materiałów dowodowych. Składnia filtrów zawartości skrzynki pocztowej to `"MailboxContent_<property> -<comparison operator> '<value>'"`. Filtry zawartości można tworzyć na podstawie zakresów dat, adresatów i domen lub dowolnej właściwości poczty e-mail z możliwością wyszukiwania. Na przykład ten filtr umożliwia menedżerom zbierania elektronicznych materiałów dowodowych tylko wyszukiwanie elementów poczty wysłanych lub otrzymywanych przez użytkowników w domenie usługi contoso.com e: `"MailboxContent_Participants -like 'contoso.com'"`. Aby uzyskać więcej informacji o filtrach zawartości skrzynki pocztowej, zobacz [Konfigurowanie filtrowania uprawnień wyszukiwania](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Filtr uprawnień wyszukiwania jest dołączany do zapytania wyszukiwania przez **operator AND** Boolean (AND). Oznacza to, że gdy menedżer zbierania elektronicznych materiałów dowodowych w jednej z agencji prowadzi wyszukiwanie zbierania elektronicznych materiałów dowodowych, elementy zwracane przez to wyszukiwanie muszą być zgodne z zapytaniem wyszukiwania i warunkami zdefiniowanymi w filtrze uprawnień wyszukiwania.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>Krok 4. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych dla dochodzenia wewnątrz agencji

Ostatnim krokiem jest utworzenie podstawowej sprawy zbierania elektronicznych materiałów dowodowych lub Advanced eDiscovery sprawy w Centrum zgodności platformy Microsoft 365 a następnie dodanie grupy ról utworzonej w kroku 2 jako członka tej sprawy. Powoduje to dwie ważne cechy korzystania z granic zgodności:
  
- Tylko członkowie grupy ról dodani do sprawy będą mogli wyświetlić i uzyskać dostęp do sprawy w Centrum zgodności platformy Microsoft 365. Jeśli na przykład grupa ról "Fourth Coffee Nasyć" jest jedynym członkiem sprawy, członkowie grupy ról Fourth Coffee eDiscovery Managers (lub członkowie jakiejkolwiek innej grupy ról) nie będą mogli zobaczyć sprawy ani uzyskać do niego dostępu.

- Gdy członek grupy ról przypisanej do sprawy uruchomi wyszukiwanie skojarzone ze sprawą, będzie mógł przeszukiwać tylko lokalizacje zawartości w obrębie swojej agencji (która jest zdefiniowana przez filtr uprawnień wyszukiwania utworzony w kroku 3).

Aby utworzyć sprawę i przydzielić członków:

1. Przejdź do **strony Core eDiscovery** **lub Advanced eDiscovery** w Centrum zgodności platformy Microsoft 365 i utwórz sprawę.

2. Na liście spraw kliknij nazwę utworzonej sprawy.

3. Dodaj grupy ról jako członków do sprawy. Aby uzyskać instrukcje, zobacz jeden z następujących artykułów:

   - [Dodawanie członków do podstawowej sprawy zbierania elektronicznych materiałów dowodowych](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

   - [Dodawanie członków do sprawy Advanced eDiscovery sprawy](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Podczas dodawania grupy ról do sprawy możesz dodawać tylko te grupy ról, których jesteś członkiem.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Wyszukiwanie i eksportowanie zawartości w środowiskach z wieloma lokalizacjami geograficznymi

Filtry uprawnień wyszukiwania umożliwiają również kontrolowanie, gdzie zawartość jest rozsyłana w celu eksportu i które centrum danych można przeszukiwać podczas wyszukiwania w lokalizacjach zawartości w [SharePoint Multi-Geo środowisku.](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)
  
- **Eksportowanie wyników wyszukiwania:** Możesz wyeksportować wyniki wyszukiwania ze skrzynek Exchange, witryn SharePoint i OneDrive z określonego centrum danych. Oznacza to, że możesz określić lokalizację centrum danych, z których będą eksportowane wyniki wyszukiwania.

    Użyj *parametru Region* dla **polecenia cmdlet New-ComplianceSecurityFilter** lub **Set-ComplianceSecurityFilter** , aby utworzyć lub zmienić centrum danych, za pośrednictwem którego eksport zostanie rozsyłany.
  
    |**Wartość parametru**|**Lokalizacja centrum danych**|
    |:-----|:-----|
    |NAM  <br/> |Ameryka Północna (centra danych znajdują się w USA)  <br/> |
    |EUR  <br/> |Europa  <br/> |
    |APC  <br/> |Azja i Pacyfik  <br/> |
    |CAN <br/> |Kanada|
    |||

- **Rozsyłanie przeszukiwań zawartości:** Możesz rozsyłać wyszukiwania zawartości witryn SharePoint i OneDrive do satelitarnego centrum danych. Oznacza to, że możesz określić lokalizację centrum danych, w którym mają być uruchamiane wyszukiwania.

    Użyj jednej z następujących wartości dla parametru *Region*, aby sterować lokalizacją centrum danych, w którym będą uruchamiane wyszukiwania podczas wyszukiwania SharePoint witryn i OneDrive kont.
  
    |**Wartość parametru**|**Lokalizacje routingu w centrum danych dla SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |USA  <br/> |
    |EUR  <br/> |Europa  <br/> |
    |APC  <br/> |Azja i Pacyfik  <br/> |
    |CAN  <br/> |USA  <br/> |
    |AUS  <br/> |Azja i Pacyfik  <br/> |
    |KOR  <br/> |Domyślne centrum danych organizacji  <br/> |
    |GBR  <br/> |Europa  <br/> |
    |JPN  <br/> |Azja i Pacyfik  <br/> |
    |IND  <br/> |Azja i Pacyfik  <br/> |
    |LAM  <br/> |USA  <br/> |
    |NOR  <br/> |Europa |
    |BRA  <br/> |Centra danych w Ameryce Północnej |
    |||

   Jeśli nie określisz *parametru Region* dla filtru uprawnień wyszukiwania, będzie przeszukiwany podstawowy region SharePoint organizacji. Wyniki wyszukiwania są eksportowane do najbliższego centrum danych.

   Aby uprościć to pojęcie, *parametr Region* steruje centrum danych używanym do wyszukiwania zawartości w programie SharePoint i OneDrive. Nie dotyczy to wyszukiwania zawartości w programie Exchange ponieważ Exchange zawartości nie są powiązane z lokalizacją geograficzną centrów danych. Ponadto ta sama wartość *parametru Region* może również dyktować centrum danych, przez które są eksportowane eksportowane dane. Jest to często konieczne w celu kontrolowania ruchu danych między tablicami geograficznymi.

> [!NOTE]
> Jeśli używasz programu Advanced eDiscovery, *parametr Region* nie kontroluje regionu, z który są eksportowane dane. Dane są eksportowane z centralnej lokalizacji organizacji. Ponadto wyszukiwanie zawartości w SharePoint i OneDrive nie jest związane z lokalizacją geograficzną centrów danych. Przeszukiwane są wszystkie centra danych. Aby uzyskać więcej informacji Advanced eDiscovery na ten temat, zobacz Omówienie [Advanced eDiscovery rozwiązania w programie Microsoft 365](overview-ediscovery-20.md).

Oto przykłady użycia *parametru Region* podczas tworzenia filtrów uprawnień wyszukiwania dla granic zgodności. Założono, że przedstawicielstwo Fourth Coffee znajduje się w Ameryce Północnej, a coho Winery znajduje się w Europie.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Podczas wyszukiwania i eksportowania zawartości w środowiskach wielowymiarowych należy pamiętać o następujących kwestiach.
  
- Parametr *Region* nie kontroluje przeszukiwania skrzynek Exchange pocztowych. Podczas przeszukiwania skrzynek pocztowych będą przeszukiwane wszystkie centra danych. Aby ograniczyć zakres przeszukiwanych skrzynek Exchange, podczas tworzenia lub zmieniania filtru uprawnień wyszukiwania użyj parametru *Filters*.

- Jeśli menedżer zbierania elektronicznych materiałów dowodowych musi przeszukiwać wiele regionów usługi SharePoint, musisz utworzyć dla tego menedżera zbierania elektronicznych materiałów dowodowych inne konto użytkownika do użycia w filtrze uprawnień wyszukiwania w celu określenia regionu, w którym znajdują się witryny programu SharePoint lub konta programu OneDrive. Aby uzyskać więcej informacji na temat konfigurowania tej funkcji, zobacz sekcję "Wyszukiwanie zawartości w środowisku SharePoint Multi-Geo" w [przeszukiwaniu zawartości](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment).

- Podczas wyszukiwania zawartości w programach SharePoint i OneDrive parametr *Region* kieruje wyszukiwania do lokalizacji podstawowej lub satelitarnej, w której menedżer zbierania elektronicznych materiałów dowodowych będzie przeprowadzać badania dotyczące zbierania elektronicznych materiałów dowodowych. Jeśli menedżer zbierania elektronicznych materiałów dowodowych przeszukuje witryny SharePoint i OneDrive poza regionem określonym w filtrze uprawnień wyszukiwania, nie są zwracane żadne wyniki wyszukiwania.

- Podczas eksportowania wyników wyszukiwania z podstawowego zbierania elektronicznych materiałów dowodowych zawartość ze wszystkich lokalizacji zawartości (w tym Exchange, Skype dla firm, SharePoint, OneDrive i innych usług, które można wyszukiwać za pomocą narzędzia Wyszukiwanie zawartości) jest przekazywany do lokalizacji usługi Azure Storage *w centrum danych określonym przez Parametr* regionu. Ułatwia to organizacjom zachowanie zgodności, nie zezwalając na eksportowanie zawartości za pomocą kontrolowanych obramowań. Jeśli w filtrze uprawnień wyszukiwania nie określono żadnego regionu, zawartość jest przesyłana do podstawowego centrum danych organizacji.

  Podczas eksportowania zawartości Advanced eDiscovery nie można kontrolować, dokąd jest przesyłana zawartość, używając *parametru Region*. Zawartość jest przesyłana do centrum Storage Azure w centrum danych w centralnej lokalizacji organizacji. Aby uzyskać listę lokalizacji geograficznych opartych na Twojej lokalizacji centralnej, zobacz Microsoft 365 Konfiguracja zbierania elektronicznych materiałów dowodowych z wieloma [lokalizacjami geograficznymi](../enterprise/multi-geo-ediscovery-configuration.md).

- Aby dodać lub zmienić region, możesz edytować istniejący filtr uprawnień wyszukiwania, uruchamiając następujące polecenie:

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Używanie granic zgodności dla witryn SharePoint centrum

[SharePoint witryn centrum często](/sharepoint/dev/features/hub-site/hub-site-overview) są zgodne z tym samymi granicami geograficznymi lub agencji, które są zgodne z ograniczeniami zgodności zbierania elektronicznych materiałów dowodowych. Oznacza to, że można utworzyć granicę zgodności za pomocą właściwości identyfikatora witryny centrum. W tym celu użyj polecenia cmdlet [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) w programie PowerShell dla usługi SharePoint Online w celu uzyskania identyfikatora witryny centrum, a następnie użyj tej wartości dla właściwości identyfikatora działu w celu utworzenia filtru uprawnień wyszukiwania.

Użyj następującej składni, aby utworzyć filtr uprawnień wyszukiwania dla witryny centrum SharePoint centrum:

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Oto przykład tworzenia filtru uprawnień wyszukiwania dla witryny centrum dla agencji Coho Winery:

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Ograniczenia związane z zgodnością

Podczas zarządzania sprawami zbierania elektronicznych materiałów dowodowych i badaniami, które korzystają z ograniczeń zgodności, należy pamiętać o następujących ograniczeniach.
  
- Podczas tworzenia i uruchamiania wyszukiwania można wybrać lokalizacje zawartości spoza agencji. Jednak z powodu filtru uprawnień wyszukiwania zawartość z tych lokalizacji nie jest uwzględniana w wynikach wyszukiwania.

- Granice zgodności nie dotyczą blokady w przypadku zbierania elektronicznych materiałów dowodowych. Oznacza to, że menedżer zbierania elektronicznych materiałów dowodowych w jednej agencji może umieścić użytkownika w chmurze dla innego agencji. Jednak granica zgodności będzie wymuszana, jeśli menedżer zbierania elektronicznych materiałów dowodowych przeszukuje lokalizacje zawartości użytkownika, który został umieszczony w a holdie. Oznacza to, że menedżer zbierania elektronicznych materiałów dowodowych nie będzie mógł przeszukiwać lokalizacji zawartości użytkownika, mimo że mógł umieścić użytkownika w a holdie.

    Ponadto statystyki dotyczące blokowania będą stosowane tylko do lokalizacji zawartości w agencji.

- Jeśli masz przypisany filtr uprawnień wyszukiwania (skrzynkę pocztową lub filtr witryny) i spróbujesz wyeksportować elementy nieindeksowane do wyszukiwania, które obejmuje wszystkie witryny usługi SharePoint w organizacji, zostanie wyświetlony następujący komunikat o błędzie: `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Jeśli masz przypisany filtr uprawnień wyszukiwania i chcesz wyeksportować elementy nieindeksowane z usługi SharePoint, musisz ponownie uruchomić wyszukiwanie i dołączyć określone witryny SharePoint do przeszukania. W przeciwnym razie będzie można eksportować tylko elementy indeksowane z wyszukiwania, które obejmuje wszystkie SharePoint witryny. Aby uzyskać więcej informacji na temat opcji eksportowania wyników wyszukiwania, zobacz [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md#step-1-prepare-search-results-for-export).

- Filtry uprawnień wyszukiwania nie są stosowane do Exchange publicznych.

## <a name="more-information"></a>Więcej informacji

- Jeśli skrzynka pocztowa nie jest licencjonowana lub usunięta "miękko", użytkownik nie będzie już rozważany w granicach zgodności. Jeśli w momencie usunięcia skrzynki pocztowej został umieszczony w tym miejscu, zawartość zachowana w skrzynce pocztowej nadal podlega granicy zgodności lub filtrowi uprawnień wyszukiwania.

- Jeśli dla użytkownika zaimplementowano granice zgodności i filtry uprawnień wyszukiwania, zalecamy, aby nie usuwać skrzynki pocztowej użytkownika, a nie jego OneDrive konta. Innymi słowy, jeśli usuniesz skrzynkę pocztową użytkownika, należy również usunąć jego konto programu OneDrive, ponieważ filtr mailbox_RecipientFilter służy do wymuszania filtrowania uprawnień wyszukiwania dla OneDrive.

- Granice zgodności i filtry uprawnień wyszukiwania zależą od atrybutów, które są oznaczane sygnaturami zawartości w programach Exchange, OneDrive i SharePoint oraz od późniejszego indeksowania tej sygnatury zawartości.

- Nie zaleca się używania filtrów wykluczeń ( `-not()` takich jak używanie w filtrze uprawnień wyszukiwania) w celu zapewnienia granicy zgodności opartej na zawartości. Użycie filtru wykluczeń może mieć nieoczekiwane wyniki, jeśli zawartość z ostatnio zaktualizowanymi atrybutami nie została zaindeksowana.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**KtoTo tworzyć filtry uprawnień wyszukiwania i zarządzać nimi (za pomocą New-ComplianceSecurityFilter i Set-ComplianceSecurityFilter cmdlet)?**
  
Aby tworzyć, wyświetlać i modyfikować filtry uprawnień wyszukiwania, musisz być członkiem grupy ról Zarządzanie organizacją w grupie Centrum zgodności platformy Microsoft 365.
  
**Jeśli menedżer zbierania elektronicznych materiałów dowodowych jest przypisany do więcej niż jednej grupy ról obejmującej wiele agencji, jak wyszukiwać zawartość w jednej lub drugiej agencji?**
  
Menedżer zbierania elektronicznych materiałów dowodowych może dodawać do zapytania wyszukiwania parametry ograniczające wyszukiwanie do określonej agencji. Jeśli na przykład organizacja przypisała właściwość **CustomAttribute10** do odróżnienia instytucji, może ona dołączyć do zapytania wyszukiwania poniższe zapytanie w celu przeszukania skrzynek pocztowych i kont usługi OneDrive w określonej agencji: `CustomAttribute10:<value>`
  
**Co się stanie, jeśli wartość atrybutu używanego jako atrybut zgodności w filtrze uprawnień wyszukiwania zostanie zmieniona?**
  
W przypadku zmiany wartości atrybutu używanego w filtrze wymuszanie granicy zgodności przez filtr uprawnień wyszukiwania może potrwać do trzech dni. Na przykład w scenariuszu Contoso załóżmy, że użytkownik z agencji Fourth Coffee jest przenoszony do agencji Coho Winery. W wyniku tego wartość atrybutu **Department** w obiekcie użytkownika zostanie zmieniona z *FourthCoffee* na *CohoWinery*. W takiej sytuacji eDiscovery Fourth Coffee i inwestorzy otrzymają wyniki wyszukiwania dla tego użytkownika w ciągu trzech dni od zmiany atrybutu. Podobnie menedżerowie zbierania elektronicznych materiałów dowodowych Coho Winery i jego współpracownikami otrzymają wyniki wyszukiwania dla użytkownika.
  
**Czy menedżer zbierania elektronicznych materiałów dowodowych może zobaczyć zawartość z dwóch osobnych granic zgodności?**
  
Tak, można to zrobić podczas wyszukiwania w Exchange, dodając menedżera zbierania elektronicznych materiałów dowodowych do grup ról widocznych dla obu instytucji. Jednak podczas wyszukiwania witryn SharePoint i kont usługi OneDrive menedżer zbierania elektronicznych materiałów dowodowych może wyszukiwać zawartość w różnych granicach zgodności tylko wtedy, gdy agencje znajdują się w tym samym regionie lub lokalizacji geograficznej. **Uwaga:** To ograniczenie dotyczące witryn nie ma zastosowania w Advanced eDiscovery, ponieważ wyszukiwanie zawartości w SharePoint i OneDrive jest powiązane z lokalizacją geograficzną.
  
**Czy filtry uprawnień wyszukiwania działają w przypadku zbierania elektronicznych materiałów dowodowych, Microsoft 365 przechowywania lub zasad DLP?**
  
Nie, w tej chwili nie ma takiej wersji.
  
**Jeśli określę region, aby kontrolować, gdzie jest eksportowana zawartość, ale nie mam organizacji w SharePoint, czy mimo to mogę wyszukiwać w SharePoint?**
  
Jeśli region określony w filtrze uprawnień wyszukiwania nie istnieje w organizacji, będzie przeszukiwany region domyślny.
  
**Jaka jest maksymalna liczba filtrów uprawnień wyszukiwania, które można utworzyć w organizacji?**
  
Nie ma ograniczenia liczby filtrów uprawnień wyszukiwania, które można utworzyć w organizacji. Jednak zapytanie wyszukiwania może mieć maksymalnie 100 warunków. W tym przypadku warunek jest zdefiniowany jako wartość połączona z zapytaniem przez operator logiczny (taki jak **AND**, **OR** i **NEAR**). Limit liczby warunków obejmuje samo zapytanie wyszukiwania oraz wszystkie filtry uprawnień wyszukiwania stosowane do użytkownika, który uruchamia wyszukiwanie. Dlatego im więcej filtrów uprawnień wyszukiwania masz (zwłaszcza jeśli te filtry zostały zastosowane do tego samego użytkownika lub grupy użytkowników), tym większa jest prawdopodobieństwo przekroczenia maksymalnej liczby warunków wyszukiwania.

Aby zrozumieć, jak działa ten limit, musisz zrozumieć, że po uruchomieniu wyszukiwania do zapytania wyszukiwania jest dołączany filtr uprawnień wyszukiwania. Filtr uprawnień wyszukiwania jest dołączany do zapytania wyszukiwania przez **operator AND** Boolean (AND). Logika kwerendy dla zapytania wyszukiwania i pojedynczy filtr uprawnień wyszukiwania będą wyglądać tak:

```text
<SearchQuery> AND <PermissionsFilter>
```

Operator OR boolean (LUB) łączy  wiele filtrów uprawnień wyszukiwania, a następnie te warunki są połączone z zapytaniem wyszukiwania przez **operator AND**.

Logika kwerendy dla zapytania wyszukiwania i wielu filtrów uprawnień wyszukiwania będzie wyglądać tak:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Być może samo zapytanie wyszukiwania może zawierać wiele warunków połączonych operatorami Boolean. Każdy warunek w zapytaniu wyszukiwania będzie również wliczał się w limit 100-warunków.

Ponadto liczba filtrów uprawnień wyszukiwania dołączonych do zapytania zależy od użytkownika, który uruchamia wyszukiwanie. Gdy wyszukiwanie jest uruchamiane przez określonego użytkownika, do zapytania są dołączane filtry uprawnień wyszukiwania stosowane do użytkownika (zdefiniowane przez parametr *Użytkownicy* w filtrze). Organizacja może mieć setki filtrów uprawnień wyszukiwania, ale jeśli do tych samych użytkowników zastosowano więcej niż 100 filtrów, prawdopodobnie limit 100 warunków zostanie przekroczony, gdy użytkownicy będą uruchamiać wyszukiwanie.

Należy pamiętać o limitie warunków. Ten limit jest też uwzględniany w SharePoint witryn internetowych uwzględnionych w filtrach uprawnień wyszukiwania lub zapytania wyszukiwania. 

Aby twoja organizacja nie dopuścić do osiągnięcia limitu warunków, ogranicz liczbę filtrów uprawnień wyszukiwania w organizacji do jak najbędszej liczby osób spełniających wymagania biznesowe.
