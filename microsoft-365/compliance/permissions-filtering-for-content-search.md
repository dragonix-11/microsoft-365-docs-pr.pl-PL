---
title: Konfigurowanie filtrowania uprawnień dla zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.openlocfilehash: 4ebd42882c7b914fe661df589382482d9f0595bc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625022"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>Konfigurowanie filtrowania uprawnień dla zbierania elektronicznych materiałów dowodowych

Filtrowanie uprawnień wyszukiwania umożliwia menedżerowi zbierania elektronicznych materiałów dowodowych wyszukiwanie tylko podzestawu skrzynek pocztowych i witryn w organizacji. Możesz również użyć filtrowania uprawnień, aby umożliwić temu sameemu menedżerowi zbierania elektronicznych materiałów dowodowych wyszukiwanie tylko zawartości skrzynki pocztowej lub witryny spełniającej określone kryteria wyszukiwania. Na przykład możesz zezwolić menedżerowi zbierania elektronicznych materiałów dowodowych na wyszukiwanie tylko skrzynek pocztowych użytkowników w określonej lokalizacji lub dziale. Można to zrobić, tworząc filtr, który używa obsługiwanego filtru adresatów, aby ograniczyć skrzynki pocztowe, które mogą być wyszukiwane przez określonego użytkownika lub grupę użytkowników. Możesz również utworzyć filtr określający zawartość skrzynki pocztowej, której może wyszukać użytkownik. Odbywa się to przez utworzenie filtru, który używa właściwości komunikatu z możliwością wyszukiwania. Podobnie można zezwolić menedżerowi zbierania elektronicznych materiałów dowodowych na wyszukiwanie tylko określonych witryn programu SharePoint w organizacji. Można to zrobić, tworząc filtr, który ogranicza, która witryna może być przeszukiwana. Można również utworzyć filtr określający zawartość witryny, którą można przeszukiwać. Odbywa się to przez utworzenie filtru, który używa właściwości witryny z możliwością wyszukiwania.

Filtry uprawnień wyszukiwania są stosowane podczas wyszukiwania zawartości przy użyciu wyszukiwania zawartości, Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (standardowa) i Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview ( Premium) w portal zgodności Microsoft Purview. Gdy filtr uprawnień wyszukiwania jest stosowany do określonego użytkownika, ten użytkownik może wykonać następujące akcje związane z wyszukiwaniem:

- Szukaj zawartości

- Podgląd wyników wyszukiwania

- Eksportuj wyniki wyszukiwania

- Przeczyszczanie elementów zwracanych przez wyszukiwanie

Możesz również użyć filtrowania uprawnień wyszukiwania, aby utworzyć granice logiczne (nazywane *granicami zgodności*) w organizacji kontrolującej lokalizacje zawartości użytkownika (takie jak skrzynki pocztowe, witryny programu SharePoint i konta usługi OneDrive), które mogą wyszukiwać określone menedżerowie zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych](set-up-compliance-boundaries.md).
  
Następujące cztery polecenia cmdlet w programie PowerShell security & Compliance umożliwiają konfigurowanie filtrów uprawnień wyszukiwania i zarządzanie nimi:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>Wymagania dotyczące konfigurowania filtrowania uprawnień

- Aby uruchomić polecenia cmdlet filtru zabezpieczeń zgodności, musisz być członkiem grupy ról Zarządzanie organizacją w portalu zgodności. Aby uzyskać więcej informacji, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Aby użyć poleceń cmdlet filtru zabezpieczeń zgodności, musisz nawiązać połączenie z programem PowerShell Exchange Online i security & Compliance. Jest to konieczne, ponieważ te polecenia cmdlet wymagają dostępu do właściwości skrzynki pocztowej, dlatego należy nawiązać połączenie z programem Exchange Online programu PowerShell. Zobacz kroki opisane w następnej sekcji.

- Aby uzyskać dodatkowe informacje na temat filtrów uprawnień wyszukiwania, zobacz sekcję [Więcej informacji](#more-information) .

- Filtrowanie uprawnień wyszukiwania ma zastosowanie do nieaktywnych skrzynek pocztowych, co oznacza, że możesz użyć filtrowania zawartości skrzynki pocztowej i skrzynki pocztowej, aby ograniczyć liczbę osób, które mogą przeszukiwać nieaktywną skrzynkę pocztową. Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać dodatkowe informacje na temat filtrowania uprawnień i nieaktywnych skrzynek pocztowych.

- Filtrowanie uprawnień wyszukiwania nie może służyć do ograniczania tego, kto może przeszukiwać foldery publiczne w programie Exchange.

- Nie ma limitu liczby filtrów uprawnień wyszukiwania, które można utworzyć w organizacji. Jednak zapytanie wyszukiwania może mieć maksymalnie 100 warunków. W takim przypadku warunek jest definiowany jako coś, co jest połączone z zapytaniem przez operator logiczny (na przykład **AND**, **OR** i **NEAR**). Limit liczby warunków obejmuje samo zapytanie wyszukiwania oraz wszystkie filtry uprawnień wyszukiwania, które są stosowane do użytkownika, który uruchamia wyszukiwanie. W związku z tym, tym więcej filtrów uprawnień wyszukiwania masz (zwłaszcza jeśli te filtry są stosowane do tego samego użytkownika lub grupy użytkowników), tym większe prawdopodobieństwo przekroczenia maksymalnej liczby warunków wyszukiwania. Aby uniemożliwić organizacji osiągnięcie limitu warunków, zachowaj maksymalną liczbę filtrów uprawnień do wyszukiwania w organizacji, aby spełnić wymagania biznesowe. Aby uzyskać więcej informacji, zobacz [Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-powershell-in-a-single-session"></a>Nawiązywanie połączenia z programem PowerShell Exchange Online i security & Compliance w jednej sesji

Przed pomyślnym uruchomieniem skryptu w tej sekcji należy pobrać i zainstalować moduł Exchange Online programu PowerShell w wersji 2. Aby uzyskać informacje, zobacz [Informacje o module Exchange Online programu PowerShell w wersji 2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku **.ps1**. Można na przykład zapisać go w pliku o nazwie **ConnectEXO-SCC.ps1**.

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

Skąd wiesz, czy to zadziałało? Po uruchomieniu skryptu dostępne są polecenia cmdlet programu Exchange Online programu PowerShell i programu PowerShell & zgodności zabezpieczeń. Jeśli nie otrzymasz żadnych błędów, połączenie zostało nawiązane pomyślnie. Szybki test polega na uruchomieniu Exchange Online poleceń cmdlet programu PowerShell i security & Compliance programu PowerShell. Można na przykład uruchamiać polecenia **Get-Mailbox** i **Get-ComplianceSearch**.

Aby rozwiązać problemy z błędami połączenia programu PowerShell, zobacz:

- [Połącz się z usługą Exchange Online w programie PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Nawiązywanie połączenia z programem PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

Filtr **New-ComplianceSecurityFilter** służy do tworzenia filtru uprawnień wyszukiwania. Oto podstawowa składnia tego polecenia cmdlet:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

W poniższych sekcjach opisano parametry tego polecenia cmdlet. Wszystkie parametry są wymagane do utworzenia filtru uprawnień wyszukiwania.

### <a name="filtername"></a>*Filtername*

Parametr  _FilterName_ określa nazwę filtru uprawnień. Ta nazwa jest używana do tożsamości filtru podczas korzystania z poleceń cmdlet **Get-ComplianceSecurityFilter**, **Set-ComplianceSecurityFilter** i **Remove-ComplianceSecurityFilter** .

### <a name="filters"></a>*Filtry*

Parametr  _Filtry_ określa kryteria wyszukiwania dla filtru zabezpieczeń zgodności. Można utworzyć trzy różne typy filtrów:  

- **Filtrowanie skrzynki pocztowej lub usługi OneDrive:** Ten typ filtru określa skrzynki pocztowe i konta usługi OneDrive, które mogą wyszukiwać przypisani użytkownicy (określona przez parametr  _Użytkownicy_ ). Ten typ filtru jest nazywany filtrem *lokalizacji zawartości* , ponieważ definiuje lokalizacje zawartości, które użytkownik może przeszukiwać. Składnia tego typu filtru to **Mailbox_** _MailboxPropertyName_, gdzie  _MailboxPropertyName_ określa właściwość skrzynki pocztowej używaną do określania zakresu skrzynek pocztowych i kont usługi OneDrive, które można przeszukiwać. Na przykład filtr  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` skrzynki pocztowej umożliwia użytkownikowi przypisanemu do tego filtru przeszukiwanie tylko skrzynek pocztowych i kont usługi OneDrive, które mają wartość "OttawaUsers" we właściwości CustomAttribute10.

  Dowolna obsługiwana właściwość adresata z możliwością filtrowania może być używana dla właściwości  _MailboxPropertyName_ w skrzynce pocztowej lub filtrze usługi OneDrive. W poniższej tabeli wymieniono cztery powszechnie używane właściwości adresatów używane do tworzenia skrzynki pocztowej lub filtru usługi OneDrive. Tabela zawiera również przykład użycia właściwości w filtrze.

  |Nazwa właściwości  |Przykład  |
  |---------|---------|
  |Alias    |`"Mailbox_Alias -like 'v-'"`         |
  |Company  |`"Mailbox_Company -eq 'Contoso'"`        |
  |CountryOrRegion |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Department |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Filtrowanie zawartości skrzynki pocztowej:** Ten typ filtru jest stosowany do zawartości, którą można przeszukiwać. Ten typ filtru jest nazywany *filtrem zawartości* , ponieważ określa zawartość skrzynki pocztowej lub właściwości poczty e-mail, które mogą wyszukiwać przypisani użytkownicy. Składnia tego typu filtru to **MailboxContent_** _SearchablePropertyName gdzie  _SearchablePropertyName_ określa właściwość KQL (Keyword Query Language), którą można określić w wyszukiwaniu. Na przykład filtr `"MailboxContent_Recipients  -like 'contoso.com'"` zawartości skrzynki pocztowej umożliwia użytkownikowi przypisanemu do tego filtru wyszukiwanie tylko wiadomości wysyłanych do adresatów w domenie contoso.com. Aby uzyskać listę właściwości wiadomości e-mail z możliwością wyszukiwania, zobacz [Zapytania dotyczące słów kluczowych i warunki wyszukiwania dla zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > Pojedynczy filtr wyszukiwania nie może zawierać filtru skrzynki pocztowej ani filtru zawartości skrzynki pocztowej. Aby połączyć je w jednym filtrze, należy użyć [listy filtrów](#using-a-filters-list-to-combine-filter-types).  Jednak filtr może zawierać bardziej złożone zapytanie tego samego typu. Na przykład `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Filtrowanie zawartości witryny i witryny:** Istnieją dwa filtry związane z programem SharePoint i OneDrive, których można użyć do określenia zawartości witryny lub witryny, którą mogą przeszukiwać przypisani użytkownicy.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   Te dwa filtry są wymienne. Na przykład `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` i  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` zwróć te same wyniki. Aby uzyskać listę właściwości witryny z możliwością wyszukiwania, zobacz [Zapytania dotyczące słów kluczowych i warunki wyszukiwania dla eDiscovery](keyword-queries-and-search-conditions.md#searchable-site-properties)  Aby uzyskać bardziej kompletną listę, zobacz [Omówienie przeszukanych i zarządzanych właściwości w programie SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Właściwości oznaczone wartością **Tak** w kolumnie **Queryable** mogą służyć do tworzenia filtru zawartości witryny lub witryny.  

  > [!IMPORTANT]
  > Skonfigurowanie filtru lokacji przy użyciu jednej z obsługiwanych właściwości nie oznacza, że właściwość lokacji w filtrze będzie propagowana do wszystkich dokumentów w tej witrynie. Oznacza to, że użytkownik nadal jest odpowiedzialny za wypełnianie określonych pól właściwości skojarzonych z dokumentami w tej witrynie, aby filtr witryny działał i przechwycił odpowiednią zawartość. Jeśli na przykład użytkownik ma zastosowany filtr zabezpieczeń "Site_RefineableString00 -eq 'abc'", a następnie użytkownik uruchamia wyszukiwanie przy użyciu zapytania kluczowego "xyz". Filtr zabezpieczeń jest dołączany do zapytania, a rzeczywiste uruchomione zapytanie to "xyz **AND RefineableString0:'abc'**". Użytkownik musi upewnić się, że dokumenty w witrynie rzeczywiście mają wartości w polu RefineableString00 jako "abc". Jeśli nie, zapytanie wyszukiwania nie zwróci żadnych wyników.

Podczas konfigurowania parametru *Filtry* dla filtrów uprawnień wyszukiwania należy pamiętać o następujących kwestiach:

- W przeciwieństwie do skrzynek pocztowych nie ma filtru lokalizacji zawartości dla witryn, mimo że filtr *witryny* wygląda jak filtr lokalizacji. Wszystkie filtry dla programów SharePoint i OneDrive są filtrami zawartości (dlatego *filtry Site_* i *SiteContent_* są wymienne), ponieważ właściwości związane z witryną, takie jak *Ścieżka* , są ostemplowane bezpośrednio w dokumentach. Dlaczego tak się dzieje? Jest to wynikiem sposobu projektowania programu SharePoint. W programie SharePoint nie ma "obiektu lokacji" z właściwościami, tak jak w przypadku skrzynek pocztowych programu Exchange. W związku z tym *właściwość Path* jest ostemplowana w dokumencie i zawiera adres URL witryny, w której znajduje się dokument. Dlatego filtr *witryny* jest uważany za filtr zawartości, a nie filtr lokalizacji zawartości.

- Musisz utworzyć filtr uprawnień wyszukiwania, aby jawnie uniemożliwić użytkownikom wyszukiwanie lokalizacji zawartości w określonej usłudze (na przykład uniemożliwienie użytkownikowi przeszukiwania dowolnej skrzynki pocztowej programu Exchange lub dowolnej witryny programu SharePoint). Innymi słowy, utworzenie filtru uprawnień wyszukiwania, który umożliwia użytkownikowi przeszukiwanie wszystkich witryn programu SharePoint w organizacji, nie uniemożliwia temu użytkownikowi przeszukiwania skrzynek pocztowych. Aby na przykład zezwolić administratorom programu SharePoint na wyszukiwanie tylko witryn programu SharePoint, należy utworzyć filtr uniemożliwiający im wyszukiwanie skrzynek pocztowych. Podobnie, aby umożliwić administratorom programu Exchange wyszukiwanie tylko skrzynek pocztowych, należy utworzyć filtr uniemożliwiający im wyszukiwanie witryn.

### <a name="users"></a>*Użytkownicy*

Parametr  _Użytkownicy_ określa użytkowników, którzy uzyskują ten filtr zastosowany do wyszukiwań. Identyfikowanie użytkowników według ich aliasu lub podstawowego adresu SMTP. Można określić wiele wartości rozdzielonych przecinkami lub przypisać filtr do wszystkich użytkowników przy użyciu wartości **Wszystkie**.

Możesz również użyć parametru  _Użytkownicy_ , aby określić grupę ról portalu zgodności. Dzięki temu można utworzyć niestandardową grupę ról, a następnie przypisać tej grupie ról filtr uprawnień wyszukiwania. Załóżmy na przykład, że masz niestandardową grupę ról dla menedżerów zbierania elektronicznych materiałów dowodowych dla amerykańskiej spółki zależnej wielonarodowej korporacji. Możesz użyć parametru  _Użytkownicy_ , aby określić tę grupę ról (przy użyciu właściwości Nazwa grupy ról), a następnie użyć parametru  _Filter_ , aby umożliwić wyszukiwanie tylko skrzynek pocztowych w Stanach Zjednoczonych. Nie można określić grup dystrybucji przy użyciu tego parametru.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Łączenie typów filtrów przy użyciu listy filtrów

*Lista filtrów* to filtr zawierający filtr skrzynki pocztowej i filtr witryny oddzielony przecinkami. Ten przecinek działa również jako operator **OR** . Użycie listy filtrów jest jedyną obsługiwaną metodą łączenia różnych typów filtrów. W poniższym przykładzie zwróć uwagę, że przecinek oddziela **filtry skrzynki pocztowej** i **witryny** :

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

Gdy filtr zawierający listę filtrów jest przetwarzany podczas uruchamiania wyszukiwania, na podstawie listy filtrów są tworzone dwa filtry uprawnień wyszukiwania: jeden dla każdego filtru rozdzielonego przecinkami. W poprzednim przykładzie zostanie utworzony jeden filtr uprawnień wyszukiwania skrzynki pocztowej i jeden filtr uprawnień wyszukiwania w witrynie. Te filtry są połączone przez operatora **OR** .

Alternatywą dla korzystania z listy filtrów byłoby utworzenie dwóch oddzielnych filtrów uprawnień wyszukiwania. W poprzednim przykładzie należy utworzyć jeden filtr atrybutu skrzynki pocztowej i jeden filtr atrybutu lokacji. W obu przypadkach wyniki są takie same. Korzystanie z listy filtrów lub tworzenie oddzielnych filtrów uprawnień wyszukiwania jest kwestią preferencji.

Należy pamiętać o używaniu listy filtrów:

- Aby utworzyć filtr zawierający filtr **skrzynki pocztowej** i filtr **MailboxContent** , należy użyć listy filtrów.

- Każdy składnik listy filtrów może zawierać złożoną składnię filtru. Na przykład filtry skrzynki pocztowej i witryny mogą zawierać wiele filtrów oddzielonych operatorem **-or** :

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Przykłady tworzenia filtrów uprawnień wyszukiwania

Poniżej przedstawiono przykłady użycia polecenia cmdlet **New-ComplianceSecurityFilter** do utworzenia filtru uprawnień wyszukiwania.

W tym przykładzie członkowie grupy ról "Us Discovery Managers" mogą przeszukiwać tylko skrzynki pocztowe i konta usługi OneDrive w Stany Zjednoczone.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
Ten przykład umożliwia użytkownikowi annb@contoso.com wykonywanie akcji wyszukiwania tylko dla skrzynek pocztowych i kont usługi OneDrive w Kanadzie. Ten filtr zawiera trzycyfrowy kod kraju liczbowego dla Kanady z iso 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

Ten przykład umożliwia użytkownikom donh i suzanf przeszukiwanie tylko skrzynek pocztowych i kont usługi OneDrive o wartości "Marketing" dla właściwości skrzynki pocztowej CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

W tym przykładzie członkowie grupy ról "Fourth Coffee eDiscovery Managers" mogą wyszukiwać tylko skrzynki pocztowe i konta usługi OneDrive o wartości "FourthCoffee" dla właściwości Skrzynka pocztowa działu. Filtr umożliwia również członkom grupy ról wyszukiwanie dokumentów w witrynie Czwarta kawa programu SharePoint.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> W poprzednim przykładzie należy uwzględnić dodatkowy filtr zawartości witryny (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`), aby członkowie grupy ról mogli wyszukiwać dokumenty na kontach usługi OneDrive. Jeśli ten filtr nie zostanie uwzględniony, filtr zezwoli tylko członkom grupy ról na wyszukiwanie dokumentów znajdujących się w `https://contoso.sharepoint.com/sites/FourthCoffee`programie .

W tym przykładzie członkowie grupy ról menedżera zbierania elektronicznych materiałów dowodowych mogą przeszukiwać tylko skrzynki pocztowe i konta usługi OneDrive członków grupy dystrybucyjnej Użytkownicy ottawy. Polecenie cmdlet Get-DistributionGroup w programie Exchange Online programu PowerShell służy do znajdowania członków grupy Użytkownicy Ottawy.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

Ten przykład uniemożliwia dowolnemu użytkownikowi wykonywanie akcji wyszukiwania na skrzynkach pocztowych i kontach usługi OneDrive członków grupy dystrybucyjnej zespołu wykonawczego. Oznacza to, że użytkownicy mogą usuwać zawartość z tych skrzynek pocztowych. Polecenie cmdlet Get-DistributionGroup w programie Exchange Online programu PowerShell służy do znajdowania członków grupy zespołu wykonawczego.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

W tym przykładzie członkowie niestandardowej grupy ról menedżerów zbierania elektronicznych materiałów dowodowych usługi OneDrive mogą wyszukiwać tylko zawartość na kontach usługi OneDrive w organizacji.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
Ten przykład ogranicza użytkownika do wykonywania akcji wyszukiwania tylko w wiadomościach e-mail wysłanych w roku kalendarzowy 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

Podobnie jak w poprzednim przykładzie, ten przykład ogranicza użytkownika do wykonywania akcji wyszukiwania tylko w dokumentach, które ostatnio zostały zmienione w roku kalendarzowym 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

Ten przykład uniemożliwia członkom grupy ról "Menedżerowie odnajdywania w usłudze OneDrive" wykonywanie akcji wyszukiwania w dowolnej skrzynce pocztowej w organizacji.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

Ten przykład uniemożliwia innym osobom w organizacji wykonywanie akcji wyszukiwania w wiadomościach e-mail, które zostały wysłane lub odebrane przez janets lub sarad.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

W tym przykładzie użyto listy filtrów do łączenia filtrów skrzynki pocztowej i witryny. W tym przykładzie filtr skrzynki pocztowej jest filtrem lokalizacji zawartości, a filtr witryny jest filtrem zawartości.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

Plik **Get-ComplianceSecurityFilter** służy do zwracania listy filtrów uprawnień wyszukiwania. Użyj parametru  _FilterName_ , aby zwrócić informacje dotyczące określonego filtru wyszukiwania.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Filtr Set-ComplianceSecurityFilter** służy do modyfikowania istniejącego filtru uprawnień wyszukiwania. W poniższych sekcjach opisano parametry tego polecenia cmdlet. Jedynym wymaganym parametrem jest  _FilterName_.
  
### <a name="filtername"></a>*Filtername*

Parametr  _FilterName_ określa nazwę filtru uprawnień.

### <a name="users"></a>*Użytkownicy*

Parametr  _Użytkownicy_ określa użytkowników, którzy uzyskują ten filtr zastosowany do wyszukiwań. Ponieważ jest to właściwość wielowartościowa, określenie użytkownika lub grupy użytkowników z tym parametrem zastępuje istniejącą listę użytkowników. Zobacz następujące przykłady składni, aby dodać i usunąć wybranych użytkowników.

Możesz również użyć parametru  _Użytkownicy_ , aby określić grupę ról portalu zgodności. Dzięki temu można utworzyć niestandardową grupę ról, a następnie przypisać tej grupie ról filtr uprawnień wyszukiwania. Załóżmy na przykład, że masz niestandardową grupę ról dla menedżerów zbierania elektronicznych materiałów dowodowych dla amerykańskiej spółki zależnej wielonarodowej korporacji. Możesz użyć parametru  _Użytkownicy_ , aby określić tę grupę ról (przy użyciu właściwości Nazwa grupy ról), a następnie użyć parametru  _Filter_ , aby umożliwić wyszukiwanie tylko skrzynek pocztowych w Stanach Zjednoczonych. Nie można określić grup dystrybucji przy użyciu tego parametru.

### <a name="filters"></a>*Filtry*

Parametr  _Filtry_ określa kryteria wyszukiwania dla filtru zabezpieczeń zgodności. Można utworzyć trzy różne typy filtrów:

- **Filtrowanie skrzynek pocztowych i usługi OneDrive:** Ten typ filtru określa skrzynki pocztowe i konta usługi OneDrive, które mogą wyszukiwać przypisani użytkownicy (określona przez parametr  _Użytkownicy_ ). Składnia tego typu filtru to **Mailbox_** _MailboxPropertyName_, gdzie  _MailboxPropertyName_ określa właściwość skrzynki pocztowej używaną do określania zakresu skrzynek pocztowych, które można przeszukiwać. Na przykład filtr  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` skrzynki pocztowej umożliwia użytkownikowi przypisanemu do tego filtru wyszukiwanie tylko skrzynek pocztowych o wartości "OttawaUsers" we właściwości CustomAttribute10.  Dla właściwości  _MailboxPropertyName_ można użyć dowolnej obsługiwanej właściwości adresata z możliwością filtrowania. Aby uzyskać listę obsługiwanych właściwości, zobacz [Właściwości możliwe do filtrowania dla parametru -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **Filtrowanie zawartości skrzynki pocztowej:** Ten typ filtru jest stosowany do zawartości, którą można przeszukiwać. Określa zawartość skrzynki pocztowej, która może być wyszukiwana przez przypisanych użytkowników. Składnia tego typu filtru to **MailboxContent_**_SearchablePropertyName_, gdzie  _searchablePropertyName_ określa właściwość KQL (Keyword Query Language), którą można określić w wyszukiwaniu. Na przykład filtr `"MailboxContent_Recipients  -like 'contoso.com'"` zawartości skrzynki pocztowej umożliwia użytkownikowi przypisanemu do tego filtru wyszukiwanie tylko wiadomości wysyłanych do adresatów w domenie contoso.com.  Aby uzyskać listę właściwości wiadomości e-mail z możliwością wyszukiwania, zobacz [Zapytania dotyczące słów kluczowych i warunki wyszukiwania dla zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

- **Filtrowanie zawartości witryny i witryny:** Istnieją dwa filtry związane z witryną programu SharePoint i OneDrive dla Firm, których można użyć do określenia zawartości witryny lub witryny, którą mogą przeszukiwać przypisani użytkownicy:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Te dwa filtry są wymienne. Na przykład  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` i  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` zwróć te same wyniki. Aby uzyskać listę właściwości witryny z możliwością wyszukiwania, zobacz [Omówienie właściwości przeszukanych i zarządzanych w programie SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Właściwości oznaczone wartością **Tak** w kolumnie **Queryable** mogą służyć do tworzenia filtru zawartości witryny lub witryny.

### <a name="examples-of-changing-search-permissions-filters"></a>Przykłady zmiany filtrów uprawnień wyszukiwania

W tych przykładach pokazano, jak za pomocą poleceń cmdlet **Get-ComplianceSecurityFilter** i **Set-ComplianceSecurityFilter** dodać lub usunąć użytkownika do istniejącej listy użytkowników, do których przypisano filtr. Po dodaniu lub usunięciu użytkowników z filtru określ użytkownika przy użyciu adresu SMTP.
  
Ten przykład dodaje użytkownika do filtru.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

W tym przykładzie użytkownik zostanie usunięty z filtru.

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

Filtr **Remove-ComplianceSecurityFilter** służy do usuwania filtru wyszukiwania. Użyj parametru  _FilterName_ , aby określić filtr, który chcesz usunąć.
  
## <a name="more-information"></a>Więcej informacji

- **Jak działa filtrowanie uprawnień wyszukiwania?** Filtr uprawnień jest dołączany do zapytania wyszukiwania po uruchomieniu wyszukiwania. Filtr uprawnień jest przyłączony do zapytania wyszukiwania przez operator logiczny **AND** . Logika zapytania wyszukiwania i filtr uprawnień będą wyglądać następująco:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Na przykład masz filtr uprawnień, który umożliwia Bobowi wykonywanie wszystkich akcji wyszukiwania w skrzynkach pocztowych członków grupy dystrybucyjnej Workers. Następnie Bob uruchamia wyszukiwanie we wszystkich skrzynkach pocztowych w organizacji przy użyciu zapytania  `sender:jerry@adatum.com`wyszukiwania . Ponieważ filtr uprawnień i zapytanie wyszukiwania są logicznie łączone przez operatora **AND** , wyszukiwanie zwraca dowolny komunikat wysłany przez jerry@adatum.com do dowolnego członka grupy dystrybucyjnej Workers. 

- **Co się stanie, jeśli masz wiele filtrów uprawnień wyszukiwania?** W zapytaniu wyszukiwania wiele filtrów uprawnień jest łączonych przez operatory logiczne **OR** . Dlatego wyniki zostaną zwrócone, jeśli którykolwiek z filtrów ma wartość true. W wyszukiwaniu wszystkie filtry (połączone przez operatory **OR** ) są następnie łączone z zapytaniem wyszukiwania przez operatora **AND** .

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Weźmy poprzedni przykład, w którym filtr wyszukiwania umożliwia Bobowi wyszukiwanie tylko skrzynek pocztowych członków grupy dystrybucyjnej Workers. Następnie utworzymy kolejny filtr, który uniemożliwia Bobowi przeszukiwanie skrzynki pocztowej Phila ("Mailbox_Alias -ne 'Phil'"). Załóżmy również, że Phil jest członkiem grupy Workers. Gdy Bob uruchamia wyszukiwanie (z poprzedniego przykładu) we wszystkich skrzynkach pocztowych w organizacji, wyniki wyszukiwania są zwracane dla skrzynki pocztowej Phila, nawet jeśli zastosowano filtr, aby uniemożliwić Bobowi przeszukiwanie skrzynki pocztowej Phila. Wynika to z faktu, że pierwszy filtr, który umożliwia Bobowi przeszukiwanie grupy Workers, ma wartość true. A ponieważ Phil jest członkiem grupy Workers, Bob może przeszukiwać skrzynkę pocztową Phila.

- **Czy filtrowanie uprawnień wyszukiwania działa w przypadku nieaktywnych skrzynek pocztowych?** Tak, możesz użyć filtrów zawartości skrzynki pocztowej i skrzynki pocztowej, aby ograniczyć liczbę osób, które mogą wyszukiwać nieaktywne skrzynki pocztowe w organizacji. Podobnie jak w przypadku zwykłej skrzynki pocztowej, nieaktywną skrzynkę pocztową należy skonfigurować przy użyciu właściwości adresata, która jest używana do tworzenia filtru uprawnień. W razie potrzeby możesz użyć polecenia **Get-Mailbox -InactiveMailboxOnly** , aby wyświetlić właściwości nieaktywnych skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi](create-and-manage-inactive-mailboxes.md).
  
- **Czy filtrowanie uprawnień wyszukiwania działa w przypadku folderów publicznych?** L.p. Jak wyjaśniono wcześniej, filtrowanie uprawnień wyszukiwania nie może służyć do ograniczania tego, kto może przeszukiwać foldery publiczne w programie Exchange. Na przykład elementów w lokalizacjach folderów publicznych nie można wykluczyć z wyników wyszukiwania za pomocą filtru uprawnień.

- **Czy zezwolenie użytkownikowi na przeszukiwanie wszystkich lokalizacji zawartości w określonej usłudze uniemożliwia również wyszukiwanie lokalizacji zawartości w innej usłudze?** L.p. Jak wyjaśniono wcześniej, należy utworzyć filtr uprawnień wyszukiwania, aby jawnie uniemożliwić użytkownikom wyszukiwanie lokalizacji zawartości w określonej usłudze (na przykład uniemożliwienie użytkownikom przeszukiwania dowolnej skrzynki pocztowej programu Exchange lub dowolnej witryny programu SharePoint). Innymi słowy, utworzenie filtru uprawnień wyszukiwania, który umożliwia użytkownikowi przeszukiwanie wszystkich witryn programu SharePoint w organizacji, nie uniemożliwia temu użytkownikowi przeszukiwania skrzynek pocztowych. Aby na przykład zezwolić administratorom programu SharePoint na wyszukiwanie tylko witryn programu SharePoint, należy utworzyć filtr uniemożliwiający im wyszukiwanie skrzynek pocztowych. Podobnie, aby umożliwić administratorom programu Exchange wyszukiwanie tylko skrzynek pocztowych, należy utworzyć filtr uniemożliwiający im wyszukiwanie witryn.

- **Czy filtry uprawnień wyszukiwania są liczone względem limitów znaków zapytania wyszukiwania?** Tak. Filtry uprawnień wyszukiwania są liczone względem limitu znaków dla zapytań wyszukiwania. Aby uzyskać więcej informacji, zobacz [Limity w funkcji zbierania elektronicznych materiałów dowodowych (Premium).](limits-ediscovery20.md)

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

Jest jeszcze jedna rzecz, o której należy pamiętać o limicie warunku. Liczba określonych witryn programu SharePoint uwzględnionych w filtrach zapytań wyszukiwania lub uprawnień wyszukiwania również jest liczona względem tego limitu. 

Aby uniemożliwić organizacji osiągnięcie limitu warunków, zachowaj maksymalną liczbę filtrów uprawnień do wyszukiwania w organizacji, aby spełnić wymagania biznesowe.