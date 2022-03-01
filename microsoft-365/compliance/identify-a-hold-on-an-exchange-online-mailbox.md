---
title: Jak określić typ hold'a umieszczonego w skrzynce Exchange Online pocztowej
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6057daa8-6372-4e77-a636-7ea599a76128
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Dowiedz się, jak identyfikować różne typy trzymania, które można umieszczać w Exchange Online pocztowej w Microsoft 365.
ms.openlocfilehash: 0ad2a1a4479c2de667b23ee29ee321912e7d18e9
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013848"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Jak określić typ hold'a umieszczonego w skrzynce Exchange Online pocztowej

W tym artykule wyjaśniono, jak identyfikować blokady Exchange Online w skrzynkach pocztowych w Microsoft 365.

Microsoft 365 kilka sposobów, które organizacja może zapobiec trwałemu usunięciu zawartości skrzynki pocztowej. Umożliwia to organizacji zachowanie zawartości w celu spełnienia przepisów dotyczących zgodności z przepisami lub w trakcie postępowania sądowego i innego rodzaju badań. Poniżej znajduje się lista funkcji przechowywania (nazywanych także blokadymi *)* dostępnych w Office 365:

- **[Zawieszenie w procesów sądowych](create-a-litigation-hold.md):** Blokady stosowane do skrzynek pocztowych użytkowników w Exchange Online.

- **[Zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md):** Blokady skojarzone z podstawową sprawą zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń i zgodności. Zbierania elektronicznych materiałów dowodowych można stosować do skrzynek pocztowych użytkowników i do odpowiadających im skrzynek pocztowych na Microsoft 365 grupy i Microsoft Teams.

- **[Blokady w miejscu](/Exchange/security-and-compliance/create-or-remove-in-place-holds):** Blokady stosowane do skrzynek pocztowych użytkowników za pomocą narzędzia In-Place eDiscovery & Hold w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange w</a> programie Exchange Online. 

   > [!NOTE]
   > In-Place zostały wycofane i nie można już tworzyć In-Place ani stosować ich do skrzynek pocztowych. Jednak In-Place mogą być nadal stosowane do skrzynek pocztowych w organizacji, dlatego zostały one uwzględnione w tym artykule. Aby uzyskać więcej informacji, zobacz [Wycofanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Microsoft 365](retention.md) przechowywania:** Można skonfigurować tak, aby zachowywać (lub zachowywać, a następnie usuwać) zawartość w skrzynkach pocztowych użytkowników w programie Exchange Online oraz w odpowiedniej skrzynce pocztowej dla grup i Microsoft 365 Microsoft Teams. Możesz również utworzyć zasady przechowywania, aby zachować konwersacje Skype dla firm, które są przechowywane w skrzynkach pocztowych użytkowników.

  Istnieją dwa typy zasad Microsoft 365 przechowywania, które można przypisywać do skrzynek pocztowych.

    - **Określone zasady przechowywania lokalizacji:** Są to zasady przypisane do lokalizacji zawartości określonych użytkowników. Polecenie cmdlet **Get-Mailbox** w programie Exchange Online PowerShell umożliwia uzyskiwanie informacji o zasadach przechowywania przypisanych do określonych skrzynek pocztowych. Aby uzyskać więcej informacji na temat tego typu zasad przechowywania, zobacz sekcję [Zasady](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) z określonymi dołączeniami lub wykluczeniami z dokumentacji zasad przechowywania.

    - **Zasady przechowywania dla całej organizacji:** Są to zasady przypisane do wszystkich lokalizacji zawartości w organizacji. Polecenie cmdlet **Get-OrganizationConfig** w programie Exchange Online PowerShell umożliwia uzyskiwanie informacji na temat zasad przechowywania w całej organizacji. Aby uzyskać więcej informacji na temat tego typu zasad przechowywania, zobacz sekcję [Zasady](retention-settings.md#a-policy-that-applies-to-entire-locations) dotyczące całych lokalizacji z dokumentacji zasad przechowywania.

- **[Microsoft 365 etykiety przechowywania](retention.md):** Jeśli użytkownik stosuje etykietę przechowywania programu Microsoft 365 (skonfigurowaną do zachowywania lub zachowywania lub zachowywania, a następnie usuwania zawartości) do dowolnego folderu  lub elementu w jego skrzynce pocztowej, do skrzynki pocztowej jest umieszczana informacja wie, jak gdyby skrzynka pocztowa została umieszczona w związku z postępowaniem sądowym lub przypisana do zasad przechowywania w programie Microsoft 365. Aby uzyskać więcej informacji, [zobacz sekcję](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) Identyfikowanie skrzynek pocztowych w wstrzymaniu, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu w tym artykule.

Aby zarządzać skrzynkami pocztowymi w miejscu, może być trzeba określić typ umieszczenia w skrzynce pocztowej, aby można było wykonywać zadania, takie jak zmienianie czasu trwania blokowania, tymczasowe lub trwałe usuwanie lub wykluczanie skrzynki pocztowej z zasad przechowywania usługi Microsoft 365. W takich przypadkach pierwszym krokiem jest określenie typu umieszczenia w skrzynce pocztowej. A ponieważ w jednej skrzynce pocztowej można umieszczać wiele blokady (i różne typy blokady), musisz zidentyfikować wszystkie blokady umieszczone w skrzynce pocztowej, jeśli chcesz usunąć lub zmienić blokady.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>Krok 1. Uzyskiwanie identyfikatora GUID dla blokady umieszczonej w skrzynce pocztowej

W programie Exchange Online PowerShell możesz uruchomić następujące dwa polecenia cmdlet, aby uzyskać identyfikator GUID przechowawek umieszczanych w skrzynce pocztowej. Po uzyskaniu identyfikatora GUID należy go użyć do zidentyfikowania określonego hold'a w kroku 2. W przypadku postępowania sądowego nie jest identyfikowany identyfikator GUID. Dla skrzynki pocztowej są włączone lub wyłączone blokady w procesów sądowych.

- **Get-Mailbox:** To polecenie cmdlet pozwala określić In-Place, czy dla skrzynki pocztowej włączono obsługę postępowań w związku z postępowaniem sądowym, oraz uzyskać identyfikatory GUID dla zbierania elektronicznych materiałów dowodowych, blokady blokady oraz zasady przechowywania Microsoft 365 przypisane do skrzynki pocztowej. Wynik tego polecenia cmdlet będzie również wskazywać, czy skrzynka pocztowa została jawnie wykluczona z zasad przechowywania dla całej organizacji.

- **Get-OrganizationConfig:** To polecenie cmdlet pozwala uzyskać identyfikatory GUID na podstawie zasad przechowywania w całej organizacji.

Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Uruchom następujące polecenie, aby uzyskać informacje o blokady i zasadach przechowywania Microsoft 365 stosowanych do skrzynki pocztowej.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> Jeśli właściwość InPlaceHolds ma zbyt wiele wartości i nie są wyświetlane wszystkie wartości, `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` można uruchomić to polecenie, aby wyświetlić każdy identyfikator GUID w osobnym wierszu.

W poniższej tabeli opisano sposób identyfikowania różnych typów blokady na podstawie wartości właściwości *InPlaceHolds* podczas uruchamiania polecenia cmdlet **Get-Mailbox** .

| Typ wstrzymywania                                                          | Wartość przykładowa                                                                                  | Jak zidentyfikować hold                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Zawieszenie w  postępowaniach sądowych                                                    | `True`                                                                                         | W przypadku właściwości *LitigationHoldEnabled właściwość LitigationHoldEnabled* jest włączona dla skrzynki pocztowej `True`.                                                                                                                                                                                                                                         |
| Zbierania elektronicznych materiałów dowodowych                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | Właściwość *InPlaceHolds zawiera* identyfikator GUID dowolnego miejsca przechowywania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w centrum zabezpieczeń i zgodności. Jak widać, jest to hold funkcji zbierania elektronicznych materiałów dowodowych, ponieważ identyfikator GUID `UniH` zaczyna się od prefiksu (co oznacza ujednolicone hold).                                                                                   |
| In-Place hold                                                      | `c0ba3ce811b6432a8751430937152491` <br/> lub <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | Właściwość *InPlaceHolds* zawiera identyfikator GUID In-Place, który jest umieszczany w skrzynce pocztowej. Możesz stwierdzić, że jest to In-Place, ponieważ identyfikator GUID nie zaczyna się od prefiksu lub zaczyna się od prefiksu `cld` .                                                                                                               |
| Microsoft 365 zasad przechowywania stosowanych specjalnie do skrzynki pocztowej | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> lub <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | Właściwość InPlaceHolds zawiera identyfikatory GUID dowolnych określonych zasad przechowywania lokalizacji zastosowanych do skrzynki pocztowej. Zasady przechowywania można określić, ponieważ identyfikator GUID zaczyna się od prefiksu `mbx` lub `skp` . Prefiks `skp` oznacza, że zasady przechowywania są stosowane Skype dla firm konwersacjach w skrzynce pocztowej użytkownika. |
| Wykluczane z zasad przechowywania i przechowywania Microsoft 365 całej organizacji  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Jeśli skrzynka pocztowa jest wykluczona z zasad przechowywania programu Microsoft 365 dla całej organizacji, identyfikator GUID zasad przechowywania, z których wykluczono skrzynkę pocztową, jest wyświetlany we właściwości InPlaceHolds `-mbx` i jest identyfikowany przez prefiks.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
Jeśli właściwość *InPlaceHolds* jest pusta po uruchomieniu polecenia cmdlet **Get-Mailbox**, nadal może być stosowana jedna lub więcej zasad przechowywania dla całej organizacji Microsoft 365 do skrzynki pocztowej. Uruchom następujące polecenie w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), aby uzyskać listę identyfikatorów GUID na Microsoft 365 przechowywania w całej organizacji.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> Jeśli właściwość InPlaceHolds ma zbyt wiele wartości i nie są wyświetlane wszystkie wartości, `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` można uruchomić to polecenie, aby wyświetlić każdy identyfikator GUID w osobnym wierszu.

W poniższej tabeli opisano różne typy blokady dla całej organizacji oraz sposoby identyfikowania poszczególnych typów na podstawie identyfikatorów GUID zawartych we właściwości *InPlaceHolds* po uruchomieniu polecenia cmdlet **Get-OrganizationConfig** .

| Typ wstrzymywania                                                                                                | Wartość przykładowa                           | Opis                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft 365 przechowywania stosowane do Exchange skrzynek pocztowych, Exchange publicznych i czatów Teams czatach | `mbx7cfb30345d454ac0a989ab3041051209:2` | Zasady przechowywania stosowane do skrzynek Exchange, folderów Exchange i czatów 1xN w programie Microsoft Teams są identyfikowane przy użyciu identyfikatorów GUID`mbx`, które zaczynają się od prefiksu. Uwaga 1xN czaty są przechowywane w skrzynce pocztowej poszczególnych uczestników czatu.  |
| Microsoft 365 przechowywania stosowane do grup Microsoft 365 i wiadomości Teams kanałów                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | Zasady przechowywania stosowane w całej organizacji do grup Microsoft 365 wiadomości w kanałach Microsoft Teams są identyfikowane za pomocą identyfikatorów GUID, które zaczynają się od prefiksu`grp`. Wiadomości w kanałach nota są przechowywane w skrzynce pocztowej grupy skojarzonej z zespołem Microsoft Team. |

Aby uzyskać więcej informacji na temat zasad przechowywania stosowanych Microsoft Teams przechowywania, zobacz [Informacje o zasadach przechowywania dla Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Opis formatu wartości InPlaceHolds dla zasad przechowywania

Oprócz prefiksu (mbx, skp lub grp), który identyfikuje element we właściwości InPlaceHolds jako zasady przechowywania usługi Microsoft 365, wartość zawiera również sufiks określający typ akcji przechowywania skonfigurowanej dla zasad. Na przykład sufiks akcji jest wyróżniony pogrubioną czcionką w następujących przykładach:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

W poniższej tabeli zdefiniowano trzy możliwe akcje przechowywania:

| Value | Opis                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Wskazuje, że zasady przechowywania są skonfigurowane tak, aby usuwać elementy. Zasady nie zachowują elementów.                                  |
| **2** | Oznacza, że zasady przechowywania są skonfigurowane do przechowywania elementów. Zasady nie usuwają elementów po wygaśnięciu okresu przechowywania. |
| **3** | Wskazuje, że zasady przechowywania są skonfigurowane tak, aby przechowywać elementy, a następnie usuwać je po wygaśnięciu okresu przechowywania.             |

Aby uzyskać więcej informacji na temat akcji przechowywania, zobacz sekcję Zachowywanie zawartości przez [określony czas](retention-settings.md#retaining-content-for-a-specific-period-of-time) .
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>Krok 2. Identyfikowanie hold przy użyciu identyfikatora GUID

Po uzyskaniu identyfikatora GUID dla hold, który został zastosowany do skrzynki pocztowej, następnym krokiem jest zidentyfikowanie tego identyfikatora GUID. W poniższych sekcjach popisano, jak zidentyfikować nazwę hold (i inne informacje) przy użyciu identyfikatora GUID hold.

### <a name="ediscovery-holds"></a>Zbierania elektronicznych materiałów dowodowych

Uruchom następujące polecenia w programie PowerShell centrum zabezpieczeń & zgodności, aby zidentyfikować hold zbierania elektronicznych materiałów dowodowych, które zastosowano do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu UniH) do przechowywania zbierania elektronicznych materiałów dowodowych wskazanego w kroku 1. 

Aby nawiązać połączenie z programem PowerShell & zabezpieczeń lub zgodności, zobacz Połączenie się z centrum & [zabezpieczeń w programie PowerShell](/powershell/exchange/connect-to-scc-powershell).

Pierwsze polecenie tworzy zmienną zawierającą informacje o wstrzymywaniu. Ta zmienna jest używana w innych poleceniach. Drugie polecenie wyświetla nazwę sprawy zbierania elektronicznych materiałów dowodowych, z którym jest skojarzone hold. Trzecie polecenie wyświetla nazwę hold i listę skrzynek pocztowych, których dotyczy to okno.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>In-Place blokady

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby zidentyfikować In-Place, które zastosowano do skrzynki pocztowej. Użyj identyfikatora GUID dla In-Place, który został zidentyfikowany w kroku 1. To polecenie wyświetla nazwę hold i listę skrzynek pocztowych, do których ma zastosowanie to hold.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Jeśli identyfikator GUID dla rekordu In-Place `cld` zaczyna się od prefiksu, pamiętaj, aby dołączyć prefiks podczas uruchamiania poprzedniego polecenia.

> [!IMPORTANT]
> W związku z dalszymi inwestycjami w różne sposoby zachowywania zawartości skrzynek pocztowych zapowiadamy wycofanie blokady In-Place w centrum administracyjnym programu Exchange. Od 1 lipca 2020 r. nie będzie można tworzyć nowych In-Place miejsc w Exchange Online. Nadal jednak będzie można zarządzać rekordami In-Place w programie EAC lub przy użyciu polecenia cmdlet **Set-MailboxSearch** w programie Exchange Online PowerShell. Jednak od 1 października 2020 r. nie będzie można zarządzać rekordami In-Place. Usuniesz je tylko w Programie eAC lub przy użyciu polecenia cmdlet **Remove-MailboxSearch** . Aby uzyskać więcej informacji na temat wycofania In-Place, zobacz Wycofanie starszych narzędzi [zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Microsoft 365 zasad przechowywania

Połączenie do programu [PowerShell](/powershell/exchange/connect-to-scc-powershell) w Centrum zabezpieczeń & i uruchom następujące polecenie w celu tożsamości zasad przechowywania usługi Microsoft 365 (dla całej organizacji lub określonej lokalizacji), które zastosowano do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu mbx, skp, grp lub sufiksu akcji) zidentyfikowanego w kroku 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Identyfikowanie skrzynek pocztowych w stanie przechowywania, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu

Ilekroć użytkownik stosuje etykietę przechowywania, która skonfigurowano tak, aby  zachowywać lub zachowywać, a następnie usuwać zawartość do dowolnego folderu lub elementu w swojej skrzynce pocztowej, właściwość *ComplianceTagHoldApplied* skrzynki pocztowej ma ustawioną wartość **True**. W takiej sytuacji skrzynka pocztowa jest traktowana podobnie jak wtedy, gdy została umieszczona w stanie przechowywania, na przykład przypisana do zasad przechowywania usługi Microsoft 365 lub umieszczana w związku z postępowaniem sądowym, jednak z pewnymi zastrzeżeniami. Gdy właściwość *ComplianceTagHoldApplied* ma ustawioną wartość **True**, występują następujące zdarzenia:

- Jeśli skrzynka pocztowa lub konto Microsoft 365 użytkownika zostanie usunięte, stanie się ona [nieaktywną skrzynką pocztową](inactive-mailboxes-in-office-365.md).
- Nie można wyłączyć tej skrzynki pocztowej (podstawowej lub archiwaowej skrzynki pocztowej, jeśli jest włączona).
- Elementy, które zostały usunięte ze skrzynki pocztowej, będą podążać jedną z dwóch ścieżek w zależności od tego, czy zostały oznaczone etykietą:
    - **Elementy bez etykiety będą podążać** ścieżką, którą mają podążać elementy usunięte, gdy do skrzynki pocztowej nie mają zastosowania żadne blokady.  Czas trwałego usunięcia tych elementów zależy od konfiguracji przechowywania elementów usuniętych oraz od tego, [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) czy dla skrzynki pocztowej włączono odzyskiwanie pojedynczych elementów.[](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery)
    - **Elementy oznaczone etykietą** będą przechowywane w folderze elementów odzyskiwalnych w taki sam sposób jak elementy Microsoft 365, ale na poziomie poszczególnych elementów.[](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder)  Jeśli wiele elementów ma różne etykiety skonfigurowane w taki sposób, aby  zachowywać lub zachowywać, a następnie usuwać zawartość w różnych interwałach, każdy element zostanie zachowany na podstawie konfiguracji zastosowanej etykiety.
- Inne blokady, takie jak zasady przechowywania Microsoft 365, blokady zbierania elektronicznych materiałów dowodowych lub blokady w związku z postępowaniem sądowym mogą wydłużyć czas przechowywania elementów oznaczonych etykietą w zależności od zasad [przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence).

Aby wyświetlić wartość właściwości *ComplianceTagHoldApplied* dla jednej skrzynki pocztowej, uruchom następujące polecenie w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Aby uzyskać więcej informacji na temat etykiet przechowywania, zobacz [Etykiety przechowywania](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Zarządzanie skrzynkami pocztowymi w przypadku opóźnienia

Po usunięciu dowolnego typu opóźnienia ze skrzynki pocztowej *jest stosowany czas* opóźnienia. Oznacza to, że rzeczywiste usunięcie hold'a jest opóźnione o 30 dni, aby zapobiec trwałemu usunięciu danych (przeczyszczeniu) ze skrzynki pocztowej. Dzięki temu administratorzy mogą wyszukiwać lub odzyskiwać elementy skrzynki pocztowej, które zostaną usunięte po usunięciu trzymania. Opóźnienie umieszcza się w skrzynce pocztowej, gdy asystent folderów zarządzanych następnym razem przetwarza skrzynkę pocztową i wykrywa jej usunięcie. W szczególności do skrzynki pocztowej jest stosowane opóźnienie, gdy Asystent folderów zarządzanych ustawia jedną z następujących właściwości skrzynki pocztowej na **wartość True**:

- **DelayHoldApplied:** Ta właściwość dotyczy zawartości związanej z pocztą e-mail (generowanej przez osoby korzystające Outlook i Outlook w sieci Web) przechowywanej w skrzynce pocztowej użytkownika.

- **DelayReleaseHoldApplied:** Ta właściwość dotyczy zawartości opartej na chmurze (generowanej przez aplikacje inne niż Outlook, takie jak Microsoft Teams, Microsoft Forms i Microsoft Yammer), która jest przechowywana w skrzynce pocztowej użytkownika. Dane w chmurze wygenerowane przez aplikację firmy Microsoft są zwykle przechowywane w ukrytym folderze w skrzynce pocztowej użytkownika.

Po umieszczeniu w skrzynce pocztowej opóźnienia (jeśli dowolna z poprzednich właściwości jest ustawiona na **Prawda)** skrzynka pocztowa jest nadal uznawana za wstrzymaną przez nieograniczony czas trwania, tak jakby skrzynka pocztowa była w związku z postępowaniem sądowym. Po 30 dniach opóźnienie wygasa i program Microsoft 365 automatycznie podejmie próbę usunięcia opóźnienia (ustawiając dla właściwości DelayHoldApplied lub DelayReleaseHoldApplied wartość **False**), co spowoduje usunięcie opóźnienia. Gdy wartość jednej z tych właściwości zostanie ustawiona na Fałsz **, odpowiadające** im elementy oznaczone do usunięcia zostaną wyczyszczone podczas następnego przetwarzania skrzynki pocztowej przez asystenta folderów zarządzanych.

Aby wyświetlić wartości właściwości DelayHoldApplied i DelayReleaseHoldApplied skrzynki pocztowej, uruchom następujące polecenie w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Aby usunąć opóźnienie, zanim wygaśnie, możesz uruchomić jedno (lub oba) następujące polecenia w programie Exchange Online PowerShell, w zależności od właściwości, którą chcesz zmienić:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Lub

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Do używania parametrów *RemoveDelayHoldApplied* lub *RemoveDelayReleaseHoldApplied* w programie Exchange Online musi być przypisana rola funkcji Legal Hold. 

Aby usunąć opóźnienie w nieaktywnej skrzynce pocztowej, uruchom jedno z następujących poleceń w programie Exchange Online PowerShell:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Lub

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> Najlepszym sposobem na określenie nieaktywnej skrzynki pocztowej w poprzednim poleceniu jest użycie jej nazwy wyróżnianej lub Exchange GUID. Użycie jednej z tych wartości pomaga zapobiec przypadkowemu określeniu niewłaściwej skrzynki pocztowej. 

Aby uzyskać więcej informacji na temat używania tych parametrów do zarządzania opóźnieniami, zobacz [Ustawianie skrzynki pocztowej](/powershell/module/exchange/set-mailbox).

Podczas zarządzania skrzynką pocztową w przypadku opóźnienia należy pamiętać o następujących kwestiach:

- Jeśli właściwość DelayHoldApplied lub DelayReleaseHoldApplied ma ustawioną wartość **True** i skrzynka pocztowa (lub odpowiadające im konto użytkownika) zostanie usunięta, skrzynka pocztowa stanie się nieaktywną skrzynką pocztową. Jest tak dlatego, że skrzynka pocztowa jest uznawana za wstrzymaną, jeśli którakolwiek z tych właściwości ma ustawioną wartość **True** (Prawda), a usunięcie skrzynki pocztowej ze skrzynki pocztowej ze względu na jej wstrzymanie powoduje jej nieaktywność. Aby usunąć skrzynkę pocztową, co nie powoduje jej usunięcia, trzeba ustawić dla obu właściwości wartość **Fałsz**.

- Jak dano wcześniej, skrzynka pocztowa jest uznawana za wstrzymaną przez nieograniczony czas trwania, jeśli dla właściwości DelayHoldApplied lub DelayReleaseHoldApplied jest ustawiona wartość **True**. Nie oznacza to jednak, *że cała zawartość* skrzynki pocztowej jest zachowywana. Zależy to od wartości ustawionej dla każdej właściwości. Załóżmy na przykład, że obie właściwości mają ustawioną wartość **True (** Prawda), ponieważ blokady są usuwane ze skrzynki pocztowej. Następnie usuwasz tylko opóźnienie zastosowane do danych w chmurze innych niż Outlook (używając *parametru RemoveDelayReleaseHoldApplied*). Przy następnym przetwarzaniu skrzynki pocztowej przez asystenta folderów zarządzanych elementy nie Outlook oznaczone do usunięcia zostaną wyczyszczone. Żadne Outlook oznaczone do usunięcia nie zostaną wyczyszczone, ponieważ właściwość DelayHoldApplied jest nadal ustawiona na **wartość True**. Przeciwieństwem jest również wartość **True**: jeśli dla ustawienia DelayHoldApplied ustawiono wartość **False**, Outlook DelayReleaseHoldApplied zostałby przeczyszczony tylko elementy oznaczone do usunięcia.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Jak potwierdzić zastosowanie zasad przechowywania dla całej organizacji do skrzynki pocztowej

Po zastosowaniu lub usunięciu zasad przechowywania dla całej organizacji do skrzynki pocztowej wyeksportowanie dzienników diagnostyki skrzynki pocztowej może pomóc mieć pewność, że program Exchange Online faktycznie zastosować lub usunąć zasady przechowywania do skrzynki pocztowej. Aby wyświetlić te informacje, należy najpierw sprawdzić poprawność kilku czynności przy [użyciu Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Uzyskiwanie identyfikatorów GUID dla wszelkich zasad przechowywania jawnie stosowanych do skrzynki pocztowej

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Uzyskiwanie identyfikatorów GUID dla wszystkich zasad przechowywania stosowanych do skrzynek pocztowych w całej organizacji

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>Uzyskaj diagnostykę skrzynek pocztowych na potrzeby usługi HoldTracking

Dzienniki diagnostyki skrzynek pocztowych śledzenia blokady zachowywają historię blokady zastosowanych do skrzynki pocztowej użytkownika.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Przeglądanie wyników dzienników diagnostyki skrzynek pocztowych

Jeśli zbierzemy dane z poprzedniego kroku, wynikowe dane mogą wyglądać podobnie do tego:

> **ed**`  : 0001-01-01T00:00:00.0000000`
>  **hid**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **ht**`  : 4`
>  **lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **osd**` : 2020-03-23T18:24:37.1884606Z`

Skorzystaj z poniższej tabeli, aby ułatwić zrozumienie każdej z poprzednich wartości wymienionych w dzienniku diagnostyki.

| Value   | Opis |
|:------- |:----------- |
| **ed**  | Wskazuje datę zakończenia, czyli datę wyłączenia zasad przechowywania. MinValue oznacza, że zasady są nadal przypisane do skrzynki pocztowej. |
| **hid** | Identyfikator GUID zasad przechowywania. Ta wartość będzie skorelowana z zbieranymi identyfikatorami GUID dla jawnych zasad przechowywania przypisanych do skrzynki pocztowej lub dla całej organizacji.|
| **lsd** | Wskazuje datę ostatniego rozpoczęcia, czyli daty przypisania zasad przechowywania do skrzynki pocztowej.|
| **osd** | Wskazuje pierwotną datę rozpoczęcia, która zawiera Exchange informacji o zasadach przechowywania. |
|||

Gdy zasady przechowywania nie będą już stosowane do skrzynki pocztowej, tymczasowo opóźnimy zawieszenie dla użytkownika, aby zapobiec przeczyszczeniu zawartości. Wstrzymanie opóźnienia można wyłączyć, uruchamiając `Set-Mailbox -RemoveDelayHoldApplied` to polecenie.

## <a name="next-steps"></a>Następne kroki

Po zidentyfikowaniu blokady, które zostały zastosowane do skrzynki pocztowej, możesz wykonywać zadania, takie jak zmienianie czasu trwania blokady, tymczasowe lub trwałe usuwanie blokady albo wykluczanie nieaktywnej skrzynki pocztowej z zasad przechowywania Microsoft 365 przechowywania. Aby uzyskać więcej informacji na temat wykonywania zadań związanych z blokadymi, zobacz jeden z następujących tematów:

- Uruchom polecenie [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) w programie [PowerShell](/powershell/exchange/connect-to-scc-powershell) centrum zgodności zabezpieczeń &, aby wykluczyć skrzynkę pocztową z zasad przechowywania Microsoft 365 całej organizacji. To polecenie może być używane tylko w przypadku zasad przechowywania, gdy wartość właściwości *ExchangeLocation (Lokalizacja exchange)* jest równa `All`.

- [Zmienianie czasu trwania wstrzymywania nieaktywnej skrzynki pocztowej](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Usuwanie nieaktywnej skrzynki pocztowej](delete-an-inactive-mailbox.md)

- [Usuwanie elementów z folderu Elementy odzyskiwalne w chmurze skrzynek pocztowych w chmurze](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
