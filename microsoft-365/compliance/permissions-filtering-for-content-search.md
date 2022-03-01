---
title: Konfigurowanie filtrowania uprawnień dla zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
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
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: Filtrowanie uprawnień wyszukiwania umożliwia menedżerom zbierania elektronicznych materiałów dowodowych wyszukiwanie tylko podzestawu skrzynek pocztowych i witryn w organizacji.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6310334bdbfd1a94456d5e826daebb9f2945af14
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028084"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>Konfigurowanie filtrowania uprawnień dla zbierania elektronicznych materiałów dowodowych

Za pomocą filtrowania uprawnień wyszukiwania menedżer zbierania elektronicznych materiałów dowodowych może przeszukiwać tylko podzbiór skrzynek pocztowych i witryn w organizacji. Filtrowanie uprawnień umożliwia również temu menedżerowi zbierania elektronicznych materiałów dowodowych tylko wyszukiwanie zawartości skrzynki pocztowej lub witryny spełniającej określone kryteria wyszukiwania. Na przykład możesz pozwolić, aby menedżer zbierania elektronicznych materiałów dowodowych przeszukiwał tylko skrzynki pocztowe użytkowników w określonej lokalizacji lub dziale. W tym celu należy utworzyć filtr z obsługiwanym filtrem adresatów w celu ograniczenia możliwości wyszukiwania skrzynek pocztowych przez określonego użytkownika lub grupę użytkowników. Możesz również utworzyć filtr określający zawartość skrzynki pocztowej, która może być wyszukiwana przez użytkownika. Aby to zrobić, należy utworzyć filtr, który używa właściwości wiadomości, która może być przeszukiwana. Podobnie możesz pozwolić, aby menedżer zbierania elektronicznych materiałów dowodowych przeszukiwał tylko określone SharePoint witryn w organizacji. W tym celu należy utworzyć filtr, który ogranicza możliwość wyszukiwania witryn. Można również utworzyć filtr określający, jaka zawartość witryny może być przeszukiwana. W tym celu należy utworzyć filtr z właściwością witryny, która może być przeszukiwana.

Filtry uprawnień wyszukiwania są stosowane podczas wyszukiwania zawartości przy użyciu funkcji wyszukiwania zawartości, podstawowych zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery w Centrum zgodności platformy Microsoft 365. Po zastosowaniu filtru uprawnień wyszukiwania do określonego użytkownika ten użytkownik może wykonywać następujące akcje związane z wyszukiwaniem:

- Wyszukiwanie zawartości

- Podgląd wyników wyszukiwania

- Eksportowanie wyników wyszukiwania

- Przeczyszczanie elementów zwróconych przez wyszukiwanie

Za pomocą filtrowania uprawnień wyszukiwania można również tworzyć granice logiczne (nazywane granicami *zgodności) w* organizacji kontrolujące lokalizacje zawartości użytkowników (takie jak skrzynki pocztowe, witryny programu SharePoint i konta OneDrive), które mogą wyszukiwać określone menedżerowie zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, [zobacz Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych](set-up-compliance-boundaries.md).
  
Następujące cztery polecenia cmdlet w programie PowerShell & zabezpieczeń i zgodności umożliwiają konfigurowanie filtrów uprawnień wyszukiwania i zarządzanie nimi:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>Wymagania dotyczące konfigurowania filtrowania uprawnień

- Aby uruchomić polecenia cmdlet filtru zabezpieczeń zgodności, musisz być członkiem grupy ról Zarządzanie organizacją w grupie Centrum zgodności platformy Microsoft 365. Aby uzyskać więcej informacji, [zobacz Uprawnienia w Centrum & zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Aby korzystać z poleceń cmdlet filtru zabezpieczeń zgodności, Exchange Online i Centrum zgodności & w programie PowerShell. Jest to konieczne, ponieważ te polecenia cmdlet wymagają dostępu do właściwości skrzynki pocztowej, dlatego musisz połączyć się z programem Exchange Online PowerShell. Zapoznaj się z instrukcjami w następnej sekcji.

- Dodatkowe informacje [o filtrach](#more-information) uprawnień wyszukiwania można znaleźć w sekcji Więcej informacji.

- Filtrowanie uprawnień wyszukiwania ma zastosowanie do nieaktywnych skrzynek pocztowych, co oznacza, że można używać filtrowania zawartości skrzynek pocztowych i skrzynek pocztowych w celu ograniczenia liczby osób, które mogą przeszukiwać nieaktywną skrzynkę pocztową. Dodatkowe informacje [na temat](#more-information) filtrowania uprawnień i nieaktywnych skrzynek pocztowych można znaleźć w sekcji Więcej informacji.

- Filtrowania uprawnień wyszukiwania nie można używać do ograniczania osób, które mogą przeszukiwać foldery publiczne w Exchange.

- Nie ma ograniczenia liczby filtrów uprawnień wyszukiwania, które można utworzyć w organizacji. Jednak zapytanie wyszukiwania może mieć maksymalnie 100 warunków. W tym przypadku warunek jest zdefiniowany jako wartość połączona z zapytaniem przez operator logiczny (taki jak **AND**, **OR** i **NEAR**). Limit liczby warunków obejmuje samą kwerendę wyszukiwania oraz wszystkie filtry uprawnień wyszukiwania stosowane do użytkownika, który uruchamia wyszukiwanie. Dlatego im więcej filtrów uprawnień wyszukiwania masz (zwłaszcza jeśli te filtry zostały zastosowane do tego samego użytkownika lub grupy użytkowników), tym większa jest prawdopodobieństwo przekroczenia maksymalnej liczby warunków wyszukiwania. Aby twoja organizacja nie dopuścić do osiągnięcia limitu warunków, ogranicz liczbę filtrów uprawnień wyszukiwania w organizacji do jak najbędszej liczby osób spełniających wymagania biznesowe. Aby uzyskać więcej informacji, [zobacz Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>Połączenie do Exchange Online i zabezpieczeń & w programie PowerShell w ramach jednej sesji

Zanim będzie można pomyślnie uruchomić skrypt w tej sekcji, musisz pobrać i zainstalować moduł Exchange Online PowerShell V2. Aby uzyskać informacje, [zobacz Informacje o module Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu **.ps1**. Na przykład możesz zapisać go w pliku o **nazwieConnectEXO-SCC.ps1**.

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. Na komputerze lokalnym otwórz Windows PowerShell, przejdź do folderu, w którym znajduje się skrypt utworzony w poprzednim kroku, a następnie uruchom skrypt, na przykład:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

Skąd wiadomo, czy to zadziałało? Po uruchomieniu skryptu polecenia cmdlet z programu Exchange Online Security & Compliance PowerShell zostaną zaimportowane do lokalnej Windows PowerShell pliku. Jeśli nie otrzymasz żadnych błędów, pomyślnie nałączono połączenie. Szybkim testem jest uruchomienie poleceń cmdlet programu PowerShell Exchange Online i centrum zabezpieczeń & w programie PowerShell. Na przykład możesz uruchomić i pobrać skrzynkę pocztową i **get-complianceSearch**.

Aby uzyskać informacje na temat rozwiązywania problemów z błędami połączenia programu PowerShell, zobacz:

- [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Połączenie do centrum & zabezpieczeń w programie PowerShell](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

Filtr **New-ComplianceSecurityFilter** służy do tworzenia filtru uprawnień wyszukiwania. Oto podstawowa składnia tego polecenia cmdlet:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

W poniższych sekcjach opisano parametry dla tego polecenia cmdlet. Wszystkie parametry są wymagane do utworzenia filtru uprawnień wyszukiwania.

### <a name="filtername"></a>*FilterName*

Parametr  _FilterName_ określa nazwę filtru uprawnień. Ta nazwa jest używana do tożsamości filtru podczas korzystania z polecenia **cmdlet Get-ComplianceSecurityFilter**, **Set-ComplianceSecurityFilter** i **Remove-ComplianceSecurityFilter** .

### <a name="filters"></a>*Filtry*

Parametr  _Filters_ określa kryteria wyszukiwania filtru zabezpieczeń zgodności. Można utworzyć trzy różne typy filtrów:  

- **Filtrowanie skrzynki OneDrive** lub skrzynki pocztowej: Ten typ filtru określa skrzynki pocztowe i konta OneDrive, które mogą wyszukiwać przypisane użytkowników (określone przez _parametr_ Użytkownicy). Ten typ filtru jest nazywany filtrem *lokalizacji* zawartości, ponieważ definiuje lokalizacje zawartości, które może wyszukiwać użytkownik. Składnią tego typu filtru jest Mailbox_  _MailboxPropertyName_, gdzie _MailboxPropertyName_ określa właściwość skrzynki pocztowej używaną do zakresu skrzynek pocztowych i kont OneDrive, które mogą być przeszukiwane. `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` Na przykład filtr skrzynki pocztowej pozwalał użytkownikowi przypisywać ten filtr do wyszukiwania tylko skrzynek pocztowych i kont usługi OneDrive, które mają wartość "OttawaUsers" we właściwości CustomAttribute10.

  Każda obsługiwana właściwość adresata z filtrowaniem może być używana dla właściwości _MailboxPropertyName_ w skrzynce pocztowej lub OneDrive filtru. W poniższej tabeli przedstawiono cztery często używane właściwości adresatów używane do tworzenia skrzynki pocztowej OneDrive filtru. W tabeli znajduje się również przykład użycia tej właściwości w filtrze.

  |Nazwa właściwości  |Przykład  |
  |---------|---------|
  |Alias    |`"Mailbox_Alias -like 'v-'"`         |
  |Company  |`"Mailbox_Company -eq 'Contoso'"`        |
  |KrajOrRegion |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Department |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Filtrowanie zawartości skrzynki pocztowej:** Ten typ filtru jest stosowany do zawartości, która może być przeszukiwana. Ten typ filtru jest *nazywany filtrem* zawartości, ponieważ określa zawartość skrzynki pocztowej lub właściwości poczty e-mail, które mogą być wyszukiwane przez przypisanych użytkowników. Składnia filtru tego typu to **MailboxContent_** _SearchablePropertyName gdzie właściwość  _SearchablePropertyName_ określa właściwość KQL (Keyword Query Language), która może zostać określona w wyszukiwaniu. Na przykład filtr zawartości skrzynki pocztowej `"MailboxContent_Recipients  -like 'contoso.com'"` pozwalał użytkownikowi przypisywać ten filtr tylko do wyszukiwania wiadomości wysyłanych do adresatów w contoso.com domenie. Aby uzyskać listę właściwości wiadomości e-mail, które można przeszukiwać, zobacz Zapytania słów kluczowych i warunki wyszukiwania dotyczące [zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > Pojedynczy filtr wyszukiwania nie może zawierać filtru skrzynki pocztowej ani filtru zawartości skrzynki pocztowej. Aby połączyć je w jeden filtr, musisz użyć [listy filtrów](#using-a-filters-list-to-combine-filter-types).  Filtr może jednak zawierać bardziej złożone zapytanie tego samego typu. Na przykład `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Filtrowanie zawartości witryny i witryny:** Istnieją dwa SharePoint- i OneDrive filtry, za pomocą których można określić, jaką witrynę lub zawartość witryny mogą wyszukiwać przypisani użytkownicy.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   Te dwa filtry są wymiennie. Na przykład zwracane `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"`  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` są te same wyniki. Aby uzyskać listę właściwości witryny, które można przeszukiwać[](keyword-queries-and-search-conditions.md#searchable-site-properties), zobacz Zapytania słów kluczowych i warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych Aby uzyskać pełniejszą listę, zobacz Omówienie właściwości przeszukanych i zarządzanych w [programie SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Właściwości oznaczone jako **Tak w** **kolumnie** Kwerenda mogą służyć do tworzenia filtru zawartości witryny lub witryny.  

  > [!IMPORTANT]
  > Skonfigurowanie filtru witryny przy użyciu jednej z obsługiwanych właściwości nie oznacza, że właściwość witryny w filtrze będzie propagowana do wszystkich dokumentów w tej witrynie. Oznacza to, że użytkownik nadal jest odpowiedzialny za wypełnienie określonych pól właściwości skojarzonych z dokumentami w tej witrynie, aby filtr witryny działał i przechwycił odpowiednią zawartość. Jeśli na przykład użytkownik ma zastosowany filtr zabezpieczeń "Site_RefineableString00 -eq 'abc'", a następnie uruchomi wyszukiwanie za pomocą zapytania słów kluczowych "xyz". Filtr zabezpieczeń zostanie dodany do zapytania, a rzeczywiste uruchomienie zapytania będzie mieć wartość "xyz **AND RefineableString0:'abc'**". Użytkownik musi zadbać o to, aby dokumenty w witrynie rzeczywiście zawierały wartości w polu RefineableString00 jako "abc". W innym przypadku zapytanie wyszukiwania nie zwróci żadnych wyników.

Podczas konfigurowania parametru *Filters* dla filtrów uprawnień wyszukiwania należy pamiętać o następujących kwestiach:

- W przeciwieństwie do skrzynek pocztowych nie istnieje filtr lokalizacji zawartości dla witryn, mimo *że filtr witryny* wygląda jak filtr lokalizacji. Wszystkie filtry dla pakietów SharePoint i OneDrive to filtry zawartości (dlatego filtry Site_ i *SiteContent_* są wymiennie), ponieważ właściwości związane z witryną, takie jak Ścieżka, są oznaczane bezpośrednio w dokumentach.  Dlaczego tak jest? Jest to wynik sposobu zaprojektowania SharePoint. Na SharePoint nie ma "obiektu witryny" z właściwościami, tak jak w przypadku Exchange pocztowych. Dlatego właściwość *Path* (Ścieżka) jest stemplowana w dokumencie i zawiera adres URL witryny, w której znajduje się dokument. Dlatego filtr witryny *jest uznawany* za filtr zawartości, a nie za filtr lokalizacji zawartości.

- Aby jawnie uniemożliwić użytkownikom przeszukiwanie lokalizacji zawartości w określonej usłudze (na przykład uniemożliwić użytkownikowi przeszukiwanie dowolnej skrzynki pocztowej usługi Exchange lub dowolnej witryny SharePoint, musisz utworzyć filtr uprawnień wyszukiwania). Innymi słowy, utworzenie filtru uprawnień wyszukiwania, który umożliwia użytkownikowi przeszukiwanie wszystkich witryn SharePoint w organizacji nie zapobiega przeszukiwaniu skrzynek pocztowych przez tego użytkownika. Aby na przykład zezwolić administratorom SharePoint przeszukiwać tylko witryny SharePoint, musisz utworzyć filtr uniemożliwiający im przeszukiwanie skrzynek pocztowych. Podobnie aby zezwolić administratorom Exchange przeszukiwać tylko skrzynki pocztowe, musisz utworzyć filtr uniemożliwiający im przeszukiwanie witryn.

### <a name="users"></a>*Użytkownicy*

Parametr  _Użytkownicy_ określa użytkowników, którzy mają zastosowany ten filtr do swoich wyszukiwań. Zidentyfikuj użytkowników według ich aliasu lub podstawowego adresu SMTP. Możesz określić wiele wartości rozdzielonych przecinkami lub przypisać filtr do wszystkich użytkowników, używając wartości **Wszystkie**.

Możesz także użyć _parametru Użytkownicy_, aby określić grupę Centrum zgodności platformy Microsoft 365 ról. Umożliwia to utworzenie niestandardowej grupy ról, a następnie przypisanie tej grupy ról do filtru uprawnień wyszukiwania. Załóżmy na przykład, że masz niestandardową grupę ról dla menedżerów zbierania elektronicznych materiałów dowodowych w amerykańskim przedstawicielsze wielonarodowej firmy. Za pomocą parametru  _Użytkownicy_ można określić tę grupę ról (używając właściwości Name grupy ról), a następnie użyć parametru  _Filter_ w celu umożliwienia wyszukiwania tylko skrzynek pocztowych w Stanach Zjednoczonych. Nie można określić grup dystrybucyjnych przy użyciu tego parametru.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Łączenie typów filtrów za pomocą listy filtrów

Lista *filtrów to* filtr, który zawiera filtr skrzynki pocztowej i filtr witryny oddzielony przecinkami. Ten przecinek działa również jako operator **LUB** . Używanie listy filtrów jest jedyną obsługiwaną metodą łączenia różnych typów filtrów. W poniższym przykładzie filtry skrzynki pocztowej i witryny oddziela  przecinek **:**

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

W przypadku przetwarzania w trakcie wyszukiwania filtru zawierającego listę filtrów na podstawie tej listy są tworzone dwa filtry uprawnień wyszukiwania: po jednym dla każdego filtru oddzielonego przecinkiem. W poprzednim przykładzie został utworzony jeden filtr uprawnień wyszukiwania w skrzynce pocztowej i jeden filtr uprawnień wyszukiwania w witrynie. Te filtry są połączone **operatorem LUB** .

Alternatywą dla używania listy filtrów jest utworzenie dwóch oddzielnych filtrów uprawnień wyszukiwania. W poprzednim przykładzie należy utworzyć jeden filtr dla atrybutu skrzynki pocztowej i jeden filtr dla atrybutu witryny. W obu przypadkach wyniki są takie same. Korzystanie z listy filtrów lub tworzenie oddzielnych filtrów uprawnień wyszukiwania wymaga preferencji.

Używając listy filtrów, pamiętaj o następujących kwestiach:

- Aby utworzyć filtr, który zawiera filtr Skrzynka pocztowa i filtr **Skrzynka pocztowaContent**, musisz użyć listy filtrów.

- Każdy składnik listy filtrów może zawierać złożoną składnię filtru. Na przykład filtry skrzynki pocztowej i witryny mogą zawierać wiele filtrów oddzielonych **operatorem -lub** :

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Przykłady tworzenia filtrów uprawnień wyszukiwania

Oto przykłady użycia polecenia cmdlet **New-ComplianceSecurityFilter** do utworzenia filtru uprawnień wyszukiwania.

W tym przykładzie członkowie grupy ról "Menedżerowie odnajdowania w Stanach Zjednoczonych" mogą przeszukiwać tylko skrzynki pocztowe i konta OneDrive w Stanach Zjednoczonych.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
W tym przykładzie użytkownik może annb@contoso.com wyszukiwania tylko dla skrzynek pocztowych i kont OneDrive w Kanadzie. Ten filtr zawiera trzycyfrowy kod kraju dla Kanady w formacie ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

W tym przykładzie użytkownicy donh i suzanf mogą przeszukiwać tylko skrzynki pocztowe i konta OneDrive, które mają wartość "Marketing" dla właściwości skrzynki pocztowej CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

W tym przykładzie członkowie grupy ról "Fourth Coffee eDiscovery Managers" mogą przeszukiwać tylko skrzynki pocztowe i konta usługi OneDrive, które mają wartość "FourthCoffee" dla właściwości skrzynki pocztowej Department. Filtr umożliwia również członkom grupy ról wyszukiwanie dokumentów w witrynie internetowej Fourth Coffee SharePoint.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> W poprzednim przykładzie należy dodać dodatkowy filtr zawartości witryny (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`), aby członkowie grupy ról mogą wyszukiwać dokumenty na OneDrive kontach. Jeśli ten filtr nie zostanie uwzględniony, ten filtr umożliwi tylko członkom grupy ról wyszukiwanie dokumentów znajdujących się w `https://contoso.sharepoint.com/sites/FourthCoffee`.

W tym przykładzie członkowie grupy ról Menedżer zbierania elektronicznych materiałów dowodowych mogą przeszukiwać tylko skrzynki pocztowe i konta OneDrive członków grupy dystrybucyjnej Użytkownicy Ottawa. Polecenie Get-DistributionGroup cmdlet w programie Exchange Online PowerShell służy do odnajdowania członków grupy Użytkownicy Ottawa.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

W tym przykładzie żaden użytkownik nie może wykonywać akcji wyszukiwania na skrzynkach pocztowych i OneDrive konta członków grupy dystrybucyjnej Zespołu kadry kierowniczej. Oznacza to, że użytkownicy mogą usuwać zawartość tych skrzynek pocztowych. Polecenie Get-DistributionGroup cmdlet w programie Exchange Online PowerShell służy do odnajdowania członków grupy grupę kadry kierowniczej.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

W tym przykładzie członkowie niestandardowej grupy ról menedżerów zbierania OneDrive zbierania elektronicznych materiałów dowodowych mogą wyszukiwać zawartość tylko w OneDrive kontach w organizacji.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
W tym przykładzie ograniczenie do wykonywania akcji wyszukiwania tylko w wiadomościach e-mail wysyłanych w roku kalendarzowym 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

Podobnie jak w poprzednim przykładzie, w tym przykładzie użytkownik może wykonywać akcje wyszukiwania tylko w przypadku dokumentów, które zostały ostatnio zmienione w roku kalendarzowym 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

W tym przykładzie członkowie grupy ról "menedżerowie odnajdowania OneDrive" nie mogą wykonywać akcji wyszukiwania dla dowolnej skrzynki pocztowej w organizacji.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

W tym przykładzie uniemożliwiono wszystkim osobom w organizacji wykonywanie akcji wyszukiwania w wiadomościach e-mail wysłanych lub otrzymywanych przez użytkownika Janets lub Ewa.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

W tym przykładzie zastosowano listę filtrów w celu połączenia filtrów skrzynki pocztowej i witryny. W tym przykładzie filtr skrzynki pocztowej jest filtrem lokalizacji zawartości, a filtr witryny jest filtrem zawartości.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

Filtr **Get-ComplianceSecurityFilter** służy do zwracania listy filtrów uprawnień wyszukiwania. Użyj  _parametru FilterName_ , aby zwrócić informacje dla określonego filtru wyszukiwania.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

Filtr **Set-ComplianceSecurityFilter** służy do modyfikowania istniejącego filtru uprawnień wyszukiwania. W poniższych sekcjach opisano parametry dla tego polecenia cmdlet. Jedynym wymaganym parametrem jest  _FilterName_.
  
### <a name="filtername"></a>*FilterName*

Parametr  _FilterName_ określa nazwę filtru uprawnień.

### <a name="users"></a>*Użytkownicy*

Parametr  _Użytkownicy_ określa użytkowników, którzy mają zastosowany ten filtr do swoich wyszukiwań. Ponieważ jest to właściwość wielowymiarowa, określająca użytkownika lub grupę użytkowników z tym parametrem zastąp istniejącą listę użytkowników. Zapoznaj się z poniższymi przykładami składni dodawania i usuwania wybranych użytkowników.

Możesz także użyć _parametru Użytkownicy_, aby określić grupę Centrum zgodności platformy Microsoft 365 ról. Umożliwia to utworzenie niestandardowej grupy ról, a następnie przypisanie tej grupy ról do filtru uprawnień wyszukiwania. Załóżmy na przykład, że masz niestandardową grupę ról dla menedżerów zbierania elektronicznych materiałów dowodowych w amerykańskim przedstawicielsze wielonarodowej firmy. Za pomocą parametru  _Użytkownicy_ można określić tę grupę ról (używając właściwości Name grupy ról), a następnie użyć parametru  _Filter_ w celu umożliwienia wyszukiwania tylko skrzynek pocztowych w Stanach Zjednoczonych. Nie można określić grup dystrybucyjnych za pomocą tego parametru.

### <a name="filters"></a>*Filtry*

Parametr  _Filters_ określa kryteria wyszukiwania filtru zabezpieczeń zgodności. Można utworzyć trzy różne typy filtrów:

- **Filtrowanie OneDrive** skrzynek pocztowych i skrzynek pocztowych: Ten typ filtru określa skrzynki pocztowe i konta OneDrive, które mogą wyszukiwać przypisanych użytkowników (określone przez _parametr_ Użytkownicy). Składnią tego typu filtru jest Mailbox_  _MailboxPropertyName_, gdzie _MailboxPropertyName_ określa właściwość skrzynki pocztowej używaną do zakresu skrzynek pocztowych, które mogą być przeszukiwane. Na przykład  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` filtr skrzynki pocztowej pozwalał użytkownikowi na przeszukanie tylko skrzynek pocztowych o wartości "OttawaUsers" we właściwości CustomAttribute10.  Każda obsługiwana właściwość adresata z filtrowaniem może być używana dla właściwości  _MailboxPropertyName_ . Aby uzyskać listę obsługiwanych właściwości, zobacz [Właściwości z filtrowaniem dla parametru -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **Filtrowanie zawartości skrzynki pocztowej:** Ten typ filtru jest stosowany do zawartości, która może być przeszukiwana. Określa zawartość skrzynki pocztowej, która może być wyszukiwana przez przypisanych użytkowników. Składnią tego typu filtru jest **MailboxContent_**_SearchablePropertyName_, gdzie właściwość  _SearchablePropertyName_ określa właściwość KQL (Keyword Query Language), która może zostać określona w wyszukiwaniu. Na przykład filtr zawartości skrzynki pocztowej `"MailboxContent_Recipients  -like 'contoso.com'"` pozwalał użytkownikowi przypisywać ten filtr tylko do wyszukiwania wiadomości wysyłanych do adresatów w contoso.com domenie.  Aby uzyskać listę właściwości wiadomości e-mail, które można przeszukiwać, zobacz Zapytania słów kluczowych i warunki wyszukiwania dotyczące [zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

- **Filtrowanie zawartości witryny i witryny:** Istnieją dwa filtry SharePoint i OneDrive dla Firm witryn, za pomocą których można określić, która witryna lub zawartość witryny mogą być przeszukiwane przez przypisanych użytkowników:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Te dwa filtry są wymiennie. Na przykład zwracane  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"`  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` są te same wyniki. Aby uzyskać listę właściwości witryny, które można przeszukiwać, zobacz Omówienie właściwości przeszukanych i zarządzanych [w programie SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Właściwości oznaczone jako **Tak w** **kolumnie** Kwerenda mogą służyć do tworzenia filtru zawartości witryny lub witryny.

### <a name="examples-of-changing-search-permissions-filters"></a>Przykłady zmieniania filtrów uprawnień wyszukiwania

W tych przykładach popisano sposób używania dodatku **cmdlet Get-ComplianceSecurityFilter** i **Set-ComplianceSecurityFilter** w celu dodania lub usunięcia użytkownika do istniejącej listy użytkowników, do których jest przypisany filtr. Po dodaniu lub usunięciu użytkowników z filtru określ użytkownika za pomocą jego adresu SMTP.
  
W tym przykładzie do filtru został dodanie użytkownika.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

W tym przykładzie użytkownik jest usuwany z filtru.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.remove("annb@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

## <a name="remove-compliancesecurityfilter"></a>Remove-ComplianceSecurityFilter

Filtr **Remove-ComplianceSecurityFilter** służy do usuwania filtru wyszukiwania. Użyj  _parametru FilterName_ , aby określić filtr, który chcesz usunąć.
  
## <a name="more-information"></a>Więcej informacji

- **Jak działa filtrowanie uprawnień wyszukiwania?** Filtr uprawnień zostanie dołączony do zapytania wyszukiwania po uruchomieniu wyszukiwania. Filtr uprawnień jest dołączany do zapytania wyszukiwania przez **operator AND** Boolean (ORAZ). Logika zapytania wyszukiwania i filtr uprawnień będą wyglądać tak:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Na przykład masz filtr uprawnień umożliwiający Tomaszowi wykonywanie wszystkich akcji wyszukiwania w skrzynkach pocztowych członków grupy dystrybucyjnej Pracownicy. Następnie Wojciech uruchamia wyszukiwanie we wszystkich skrzynkach pocztowych w organizacji za pomocą zapytania wyszukiwania  `sender:jerry@adatum.com`. Ponieważ filtr uprawnień i zapytanie wyszukiwania są logicznie łączone przez operator **AND** , wyszukiwanie zwraca wszystkie wiadomości wysłane przez jerry@adatum.com do dowolnego członka grupy dystrybucyjnej Pracownicy. 

- **Co się stanie, jeśli masz wiele filtrów uprawnień wyszukiwania?** W zapytaniu wyszukiwania wiele filtrów uprawnień jest łącznych za pomocą **operatorów LUB** logicznych. Jeśli którykolwiek z filtrów jest prawdziwy, zostaną zwrócone wyniki. Podczas wyszukiwania wszystkie filtry (połączone operatorami **OR** ) są następnie łączone z zapytaniem wyszukiwania przez operator **AND** .

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Przyjmijmy, że w poprzednim przykładzie filtr wyszukiwania umożliwia Wojciechowi przeszukiwanie tylko skrzynek pocztowych członków grupy dystrybucyjnej Pracownicy. Następnie tworzymy kolejny filtr, który uniemożliwia Tomaszowi przeszukiwanie skrzynki pocztowej Tomasza ("Mailbox_Alias -ne 'Michał'"). Załóżmy również, że Arter jest członkiem grupy Pracownicy. Gdy Wojciech uruchomi wyszukiwanie (z poprzedniego przykładu) we wszystkich skrzynkach pocztowych w organizacji, dla skrzynki pocztowej Tomasza są zwracane wyniki wyszukiwania, mimo że zastosowano filtr, aby zapobiec przeszukiwaniu skrzynki pocztowej Tomasza. Wynika to z tego, że pierwszy filtr, który umożliwia Tomaszowi przeszukiwanie grupy Pracownicy, jest prawdziwy. Ponieważ Tomasz jest członkiem grupy Pracownicy, może przeszukiwać skrzynkę pocztową Tomasza.

- **Czy filtrowanie uprawnień wyszukiwania działa w przypadku nieaktywnych skrzynek pocztowych?** Tak, możesz używać filtrów zawartości skrzynek pocztowych i skrzynek pocztowych, aby ograniczyć liczbę osób, które mogą przeszukiwać nieaktywne skrzynki pocztowe w Twojej organizacji. Podobnie jak w przypadku zwykłej skrzynki pocztowej nieaktywna skrzynka pocztowa musi zostać skonfigurowana przy użyciu właściwości adresata, która służy do tworzenia filtru uprawnień. W razie potrzeby możesz użyć polecenia **Get-Mailbox -InactiveMailboxOnly** w celu wyświetlenia właściwości nieaktywnych skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi](create-and-manage-inactive-mailboxes.md).
  
- **Czy filtrowanie uprawnień wyszukiwania działa w przypadku folderów publicznych?** L.p. Jak już wyjaśniono, filtrowania uprawnień wyszukiwania nie można używać do ograniczania osób, które mogą przeszukiwać foldery publiczne w Exchange. Na przykład za pomocą filtru uprawnień nie można wykluczyć elementów w lokalizacjach folderów publicznych z wyników wyszukiwania.

- **Czy zezwolenie użytkownikowi na przeszukiwanie wszystkich lokalizacji zawartości w określonej usłudze uniemożliwia mu również przeszukiwanie lokalizacji zawartości w innej usłudze?** L.p. Jak wyjaśniono wcześniej, należy utworzyć filtr uprawnień wyszukiwania, aby jawnie uniemożliwić użytkownikom przeszukiwanie lokalizacji zawartości w określonej usłudze (na przykład uniemożliwić użytkownikowi przeszukiwanie dowolnej skrzynki pocztowej usługi Exchange lub dowolnej witryny SharePoint). Innymi słowy, utworzenie filtru uprawnień wyszukiwania, który umożliwia użytkownikowi przeszukiwanie wszystkich witryn SharePoint w organizacji nie zapobiega przeszukiwaniu skrzynek pocztowych przez tego użytkownika. Aby na przykład zezwolić administratorom SharePoint przeszukiwać tylko witryny SharePoint, musisz utworzyć filtr uniemożliwiający im przeszukiwanie skrzynek pocztowych. Podobnie aby zezwolić administratorom Exchange przeszukiwać tylko skrzynki pocztowe, musisz utworzyć filtr uniemożliwiający im przeszukiwanie witryn.

- **Czy filtry uprawnień wyszukiwania są wliczane do limitów znaków zapytania wyszukiwania?** Tak. Filtry uprawnień wyszukiwania są wliczane do limitu znaków dla zapytań wyszukiwania. Aby uzyskać więcej informacji, zobacz [Limity w Advanced eDiscovery](limits-ediscovery20.md).

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