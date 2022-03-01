---
title: Migrowanie starszych wyszukiwań i funkcji zbierania elektronicznych materiałów dowodowych do Centrum zgodności platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: fe3f65e2545b71f8cfbaea76dfd34fd2720a790f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017778"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-microsoft-365-compliance-center"></a>Migrowanie starszych wyszukiwań i funkcji zbierania elektronicznych materiałów dowodowych do Centrum zgodności platformy Microsoft 365

Program Centrum zgodności platformy Microsoft 365 zapewnia ulepszone środowisko zbierania elektronicznych materiałów dowodowych, w tym: większą niezawodność, lepszą wydajność i wiele funkcji dostosowanych do przepływów pracy zbierania elektronicznych materiałów dowodowych, w tym sprawy porządkowania zawartości według sprawy, przeglądanie zestawów w celu przejrzenia zawartości i analizy, aby pomóc w przejrzeniu danych, takich jak niemal zduplikowane grupowanie, wątkowanie wiadomości e-mail, analiza motywów i podpowidanie  kodowanie.

Aby ułatwić klientom skorzystanie z nowych i ulepszonych funkcji, w tym artykule przedstawiono podstawowe wskazówki dotyczące migrowania wyszukiwań i blokady zbierania elektronicznych materiałów dowodowych usługi In-Place z centrum administracyjnego programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> do centrum Centrum zgodności platformy Microsoft 365.

> [!NOTE]
> Ponieważ istnieje wiele różnych scenariuszy, ten artykuł zawiera ogólne wskazówki dotyczące przechodzenia wyszukiwania i blokady do podstawowej sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Korzystanie ze spraw zbierania elektronicznych materiałów dowodowych nie zawsze jest wymagane, ale dodają one dodatkową warstwę zabezpieczeń, pozwalając na przypisywanie uprawnień do kontrolowania, kto ma dostęp do spraw zbierania elektronicznych materiałów dowodowych w organizacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby uruchomić polecenia programu PowerShell opisane w tym artykule, musisz być członkiem grupy ról Menedżera zbierania elektronicznych materiałów dowodowych w grupie Centrum zgodności platformy Microsoft 365. Musisz również być członkiem grupy ról Zarządzanie odnajdowaniami w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>.

- Ten artykuł zawiera wskazówki dotyczące tworzenia zbierania elektronicznych materiałów dowodowych. Zasady przechowywania będą stosowane do skrzynek pocztowych za pośrednictwem asynchronicznego procesu. Podczas tworzenia zbierania elektronicznych materiałów dowodowych należy utworzyć zarówno element CaseHoldPolicy, jak i caseHoldRule. W przeciwnym razie nie zostanie utworzone hold i lokalizacje zawartości nie zostaną umieszczone w a hold.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-center-powershell"></a>Krok 1. Połączenie do Exchange Online programu PowerShell i centrum & zgodności programu PowerShell

Pierwszym krokiem jest połączenie się z programem PowerShell Exchange Online i centrum zabezpieczeń & w programie PowerShell. Możesz skopiować poniższy skrypt, wkleić go do okna programu PowerShell, a następnie go uruchomić. Zostanie wyświetlony monit o poświadczenia dla organizacji, z którą chcesz nawiązać połączenie. 

```powershell
$UserCredential = Get-Credential
$sccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $sccSession -DisableNameChecking
$exoSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $exoSession -AllowClobber -DisableNameChecking
```

Należy uruchomić polecenia w poniższych krokach tej sesji programu PowerShell.

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>Krok 2. Uzyskiwanie listy przeszukiwań zbierania In-Place eDiscovery przy użyciu funkcji Get-MailboxSearch

Po uwierzytelnieniu możesz uzyskać listę wyszukiwań zbierania elektronicznych materiałów dowodowych In-Place, uruchamiając polecenie cmdlet **Get-MailboxSearch** . Skopiuj i wklej następujące polecenie do programu PowerShell, a następnie uruchom go. Zostanie wyświetlona lista wyszukiwań wraz z ich nazwiskami i stanami wszystkich In-Place blokady.

```powershell
Get-MailboxSearch
```

Wynik polecenia cmdlet będzie podobny do następującego:

![Przykład programu PowerShell: Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>Krok 3. Uzyskiwanie informacji na temat In-Place zbierania elektronicznych materiałów dowodowych i In-Place zbierania elektronicznych materiałów dowodowych, które chcesz zmigrować

Ponownie użyjsz polecenia cmdlet **Get-MailboxSearch** , ale tym razem do uzyskania właściwości wyszukiwania. Te właściwości można przechowywać w zmiennej do późniejszego użycia. W poniższym przykładzie wyniki polecenia cmdlet **Get-MailboxSearch są** przechowywane w zmiennej, a następnie są wyświetlane właściwości wyszukiwania.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | FL
```

Wynik tych dwóch poleceń będzie podobny do następującego:

![Przykład danych wyjściowych programu PowerShell z Get-MailboxSearch wyszukiwania indywidualnego.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> Czas trwania zawieszania In-Place w tym przykładzie jest nieograniczony (*ItemHoldPeriod: Unlimited*). Jest to typowe w przypadku zbierania elektronicznych materiałów dowodowych i dochodzenia prawnego. Jeśli czas trwania zawieszania jest inny niż czas nieograniczony, przyczyną jest prawdopodobnie przechowywanie zawartości w scenariuszu przechowywania. Zamiast korzystać z poleceń cmdlet zbierania elektronicznych materiałów dowodowych w programie PowerShell centrum zgodności & w celu przechowywania scenariuszy przechowywania, zalecamy zachowanie zawartości za pomocą poleceń [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) i [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) . Wynik korzystania z tych polecenia cmdlet będzie podobny do używania funkcji **New-CaseHoldPolicy** i **New-CaseHoldRule**, ale możesz określić okres przechowywania i akcję przechowywania, na przykład usunąć zawartość po wygaśnięciu okresu przechowywania. Ponadto korzystanie z polecenia cmdlet przechowywania nie wymaga kojarzenia przechowywania ze sprawą zbierania elektronicznych materiałów dowodowych.

## <a name="step-4-create-a-case-in-the-microsoft-365-compliance-center"></a>Krok 4. Tworzenie sprawy w centrum zgodności Microsoft 365 zgodności

Aby utworzyć hold zbierania elektronicznych materiałów dowodowych, musisz utworzyć sprawę zbierania elektronicznych materiałów dowodowych w celu skojarzenia jej z. Poniższy przykład tworzy sprawę zbierania elektronicznych materiałów dowodowych przy użyciu wybranej nazwy. Właściwości nowej sprawy będą przechowywane w zmiennej do późniejszego użycia. Te właściwości można wyświetlić, uruchamiając polecenie `$case | FL` po utworzeniu sprawy.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```
![Przykład uruchamiania New-ComplianceCase wiersza.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>Krok 5. Tworzenie zbierania elektronicznych materiałów dowodowych

Po utworzeniu sprawy możesz ją utworzyć i skojarzyć ze sprawą utworzoną w poprzednim kroku. Należy pamiętać, że należy utworzyć zarówno zasady dotyczące przechowywania liter, jak i regułę blokowania przypadków. Jeśli reguła przechowywania sprawy nie została utworzona po utworzeniu zasad przechowywania sprawy, nie zostanie utworzone hold zbierania elektronicznych materiałów dowodowych i nie zostanie umieszczona w tym miejscu.

Uruchom następujące polecenia, aby ponownie utworzyć hold zbierania elektronicznych materiałów dowodowych, który chcesz poddać migracji. W tych przykładach są In-Place właściwości z In-Place, które mają zostać zmigrowane z kroku 3. Pierwsze polecenie tworzy nowe zasady przechowywania przypadków i zapisuje właściwości zmiennej. Drugie polecenie tworzy odpowiednią regułę wstrzymywania liter.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![Przykład użycia polecenia cmdlet NewCaseHoldPolicy i NewCaseHoldRule.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>Krok 6. Sprawdzanie zbierania elektronicznych materiałów dowodowych

Aby upewnić się, że nie było problemów z utworzeniem wstrzymywania, warto sprawdzić, czy stan dystrybucji wstrzymania został pomyślnie zweryfikowany. Rozkład oznacza, że hold został zastosowany do wszystkich lokalizacji zawartości określonych w parametrze *ExchangeLocation* w poprzednim kroku. W tym celu możesz uruchomić polecenie cmdlet **Get-CaseHoldPolicy** . Ponieważ właściwości zapisane w zmiennej *$policy* utworzonej w poprzednim kroku nie są automatycznie aktualizowane w tej zmiennej, należy ponownie uruchomić polecenie cmdlet, aby sprawdzić, czy rozkład się powiodło. Pomyślne rozpowszechnianie zasad przechowywania sprawy może potrwać od 5 minut do 24 godzin.

Uruchom następujące polecenie, aby sprawdzić, czy pomyślnie rozpowszechniono hold zbierania elektronicznych materiałów dowodowych.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

Wartość **sukcesu dla** właściwości *DistributionStatus* wskazuje, że hold został pomyślnie umieszczony w lokalizacjach zawartości. Jeśli rozkład jeszcze nie został ukończony, zostanie wyświetlona wartość **Oczekiwanie** .

![Przykład Get-CaseHoldPolicy PowerShell.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>Krok 7. Tworzenie wyszukiwania

Ostatnim krokiem jest ponowne utworzenie wyszukiwania wskazanego w kroku 3 i skojarzenie go ze sprawą. Po utworzeniu wyszukiwania można je uruchomić za pomocą polecenia **cmdlet Start-ComplianceSearch** lub uruchomić w późniejszym czasie.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![Przykład New-ComplianceSearch PowerShell.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-microsoft-365-compliance-center"></a>Krok 8. Sprawdź sprawę, przytrzymaj i wyszukaj w Centrum zgodności platformy Microsoft 365

Aby upewnić się, że wszystko jest poprawnie skonfigurowane, [https://compliance.microsoft.com](https://compliance.microsoft.com)przejdź do Centrum zgodności platformy Microsoft 365 i kliknij pozycję zbierania elektronicznych materiałów dowodowych **> Core**.

![Microsoft 365 zbierania elektronicznych materiałów dowodowych w Centrum zgodności.](../media/MigrateLegacyeDiscovery7.png)

Sprawa utworzona w kroku 3 jest wymieniona na stronie **Podstawowe zbierania elektronicznych materiałów dowodowych** . Otwórz sprawę, a następnie zwróć uwagę na utworzoną w kroku 4 listę na karcie **Wstrzymaj** . Możesz wybrać pozycję wstrzymywania, aby wyświetlić szczegółowe informacje na stronie wysuwu, takie jak liczba skrzynek pocztowych, do których zastosowano hold, i stan dystrybucji.

![Zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.](../media/MigrateLegacyeDiscovery8.png)

Wyszukiwanie utworzone w kroku 7 zostanie wyświetlone na karcie Wyszukiwania w przypadku.

![Przeszukiwanie sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.](../media/MigrateLegacyeDiscovery9.png)

Jeśli przeprowadzasz migrację wyszukiwania zbierania elektronicznych materiałów dowodowych In-Place, ale nie skojarzysz jej ze sprawą zbierania elektronicznych materiałów dowodowych, będzie ona wymieniona na stronie Przeszukiwanie zawartości w Centrum zgodności platformy Microsoft 365.

## <a name="more-information"></a>Więcej informacji

- Aby uzyskać więcej informacji na In-Place zbierania elektronicznych materiałów dowodowych & <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">w centrum administracyjnym</a> usługi Exchange, zobacz:
  
  - [Zbierania elektronicznych materiałów dowodowych w miejscu](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [Zawieszenie w miejscu i zawieszenie w  postępowaniem sądowym](/exchange/security-and-compliance/in-place-and-litigation-holds)

- Aby uzyskać więcej informacji na temat poleceń cmdlet programu PowerShell używanych w tym artykule, zobacz:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)
  
  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)
  
  - [New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
  
  - [Wyszukiwanie nowych zgodności](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- Aby uzyskać więcej informacji na Centrum zgodności platformy Microsoft 365, zobacz [Omówienie](microsoft-365-compliance-center.md) Centrum zgodności platformy Microsoft 365.