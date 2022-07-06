---
title: Jak zidentyfikować blokadę w skrzynce pocztowej Exchange Online
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Dowiedz się, jak zidentyfikować różne typy blokad, które można umieścić w Exchange Online skrzynce pocztowej na platformie Microsoft 365.
ms.openlocfilehash: d7a174d267897f37fa113a51e138ec68def65b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638306"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej Exchange Online

W tym artykule wyjaśniono, jak identyfikować blokady umieszczone w skrzynkach pocztowych Exchange Online w usłudze Microsoft 365.

Platforma Microsoft 365 oferuje kilka sposobów, dzięki czemu organizacja może uniemożliwić trwałe usunięcie zawartości skrzynki pocztowej. Dzięki temu organizacja może przechowywać zawartość zgodnie z przepisami dotyczącymi zgodności lub podczas prawnych i innych typów dochodzeń. Oto lista funkcji przechowywania (nazywanych również *blokadami*) w Office 365:

- **[Blokada postępowania sądowego](create-a-litigation-hold.md):** Blokady stosowane do skrzynek pocztowych użytkowników w Exchange Online.

- **[Blokada zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md):** Blokady skojarzone ze sprawą Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Standardowa) w centrum zabezpieczeń i zgodności. Blokady zbierania elektronicznych materiałów dowodowych można zastosować do skrzynek pocztowych użytkowników i odpowiedniej skrzynki pocztowej dla Grupy Microsoft 365 i usługi Microsoft Teams.

- **[Blokada](/Exchange/security-and-compliance/create-or-remove-in-place-holds) miejscowa:** blokady stosowane do skrzynek pocztowych użytkowników przy użyciu narzędzia In-Place eDiscovery & Hold w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a> w Exchange Online. 

   > [!NOTE]
   > In-Place Blokady zostały wycofane i nie można już tworzyć In-Place blokad ani stosować ich do skrzynek pocztowych. Jednak In-Place Blokady mogą być nadal stosowane do skrzynek pocztowych w organizacji, dlatego są one zawarte w tym artykule. Aby uzyskać więcej informacji, zobacz [Wycofywanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Zasady przechowywania platformy Microsoft 365](retention.md):** Można skonfigurować do przechowywania (lub zachowywania, a następnie usuwania) zawartości w skrzynkach pocztowych użytkowników w Exchange Online i w odpowiedniej skrzynce pocztowej dla Grupy Microsoft 365 i usługi Microsoft Teams. Można również utworzyć zasady przechowywania w celu zachowania Skype dla firm konwersacji, które są przechowywane w skrzynkach pocztowych użytkownika.

  Istnieją dwa typy zasad przechowywania platformy Microsoft 365, które można przypisać do skrzynek pocztowych.

    - **Określone zasady przechowywania lokalizacji:** Są to zasady przypisane do lokalizacji zawartości określonych użytkowników. Polecenie cmdlet **Get-Mailbox** w programie Exchange Online programu PowerShell umożliwia uzyskanie informacji o zasadach przechowywania przypisanych do określonych skrzynek pocztowych. Aby uzyskać więcej informacji na temat tego typu zasad przechowywania, zobacz [sekcję Zasady A z określonymi dołączeniami lub wykluczeniami](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) z dokumentacji zasad przechowywania.

    - **Zasady przechowywania w całej organizacji:** Są to zasady przypisane do wszystkich lokalizacji zawartości w organizacji. Aby uzyskać informacje o zasadach przechowywania w całej organizacji, użyj polecenia cmdlet **Get-OrganizationConfig** w programie Exchange Online programu PowerShell. Aby uzyskać więcej informacji na temat tego typu zasad przechowywania, zobacz sekcję [Zasady A, które mają zastosowanie do całych lokalizacji](retention-settings.md#a-policy-that-applies-to-entire-locations) z dokumentacji zasad przechowywania.

- **[Etykiety przechowywania platformy Microsoft 365](retention.md): jeśli użytkownik zastosuje** etykietę przechowywania platformy Microsoft 365 (taką, która jest skonfigurowana do przechowywania zawartości lub przechowywania, a następnie usuwania zawartości) do *dowolnego* folderu lub elementu w skrzynce pocztowej, w skrzynce pocztowej zostanie umieszczona blokada tak, jakby skrzynka pocztowa została wstrzymana lub przypisana do zasad przechowywania usługi Microsoft 365. Aby uzyskać więcej informacji, zobacz [sekcję Identyfikowanie skrzynek pocztowych wstrzymanych, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) w tym artykule.

Aby zarządzać skrzynkami pocztowymi w stanie wstrzymania, może być konieczne zidentyfikowanie typu blokady umieszczonego w skrzynce pocztowej, aby można było wykonywać zadania, takie jak zmiana czasu przechowywania, tymczasowe lub trwałe usunięcie blokady lub wykluczenie skrzynki pocztowej z zasad przechowywania usługi Microsoft 365. W takich przypadkach pierwszym krokiem jest zidentyfikowanie typu blokady umieszczonej w skrzynce pocztowej. A ponieważ wiele blokad (i różnych typów blokad) można umieścić w jednej skrzynce pocztowej, musisz zidentyfikować wszystkie blokady umieszczone w skrzynce pocztowej, jeśli chcesz usunąć lub zmienić blokadę.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>Krok 1. Uzyskiwanie identyfikatora GUID blokad umieszczonych w skrzynce pocztowej

W programie Exchange Online programu PowerShell można uruchomić następujące dwa polecenia cmdlet, aby uzyskać identyfikator GUID blokad umieszczonych w skrzynce pocztowej. Po uzyskaniu identyfikatora GUID należy go użyć do zidentyfikowania określonego blokady w kroku 2. Blokada postępowania sądowego nie jest identyfikowana przez identyfikator GUID. Blokady sporów są włączone lub wyłączone dla skrzynki pocztowej.

- **Get-Mailbox:** Użyj tego polecenia cmdlet, aby określić, czy blokada postępowania sądowego jest włączona dla skrzynki pocztowej, oraz aby uzyskać identyfikatory GUID blokad zbierania elektronicznych materiałów dowodowych, In-Place blokad i zasad przechowywania platformy Microsoft 365, które są specjalnie przypisane do skrzynki pocztowej. Dane wyjściowe tego polecenia cmdlet będą również wskazywać, czy skrzynka pocztowa została jawnie wykluczona z zasad przechowywania w całej organizacji.

- **Get-OrganizationConfig:** Użyj tego polecenia cmdlet, aby uzyskać identyfikatory GUID zasad przechowywania w całej organizacji.

Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Łączenie z programem PowerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Uruchom następujące polecenie, aby uzyskać informacje o blokadach i zasadach przechowywania platformy Microsoft 365 stosowanych do skrzynki pocztowej.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> Jeśli we właściwości InPlaceHolds jest zbyt wiele wartości, a nie wszystkie są wyświetlane, możesz uruchomić `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` polecenie , aby wyświetlić każdy identyfikator GUID w osobnym wierszu.

W poniższej tabeli opisano sposób identyfikowania różnych typów blokad na podstawie wartości we właściwości *InPlaceHolds podczas uruchamiania* polecenia cmdlet **Get-Mailbox** .

| Typ blokady                                                          | Przykładowa wartość                                                                                  | Jak zidentyfikować blokadę                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wstrzymanie postępowania sądowego                                                    | `True`                                                                                         | Blokada postępowania sądowego jest włączona dla skrzynki pocztowej, gdy właściwość *LitigationHoldEnabled* jest ustawiona na `True`.                                                                                                                                                                                                                                         |
| Blokada zbierania elektronicznych materiałów dowodowych                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | *Właściwość InPlaceHolds* zawiera identyfikator GUID dowolnego blokady skojarzonego z przypadkiem zbierania elektronicznych materiałów dowodowych w centrum zabezpieczeń i zgodności. Możesz powiedzieć, że jest to blokada zbierania elektronicznych materiałów dowodowych, ponieważ identyfikator GUID rozpoczyna się od prefiksu `UniH` (który oznacza ujednoliconą blokadę).                                                                                   |
| blokada In-Place                                                      | `c0ba3ce811b6432a8751430937152491` <br/> lub <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | Właściwość *InPlaceHolds* zawiera identyfikator GUID In-Place Hold umieszczony w skrzynce pocztowej. Możesz powiedzieć, że jest to In-Place Blokada, ponieważ identyfikator GUID nie zaczyna się od prefiksu lub zaczyna się od prefiksu `cld` .                                                                                                               |
| Zasady przechowywania usługi Microsoft 365 stosowane specjalnie do skrzynki pocztowej | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> lub <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | Właściwość InPlaceHolds zawiera identyfikatory GUID określonych zasad przechowywania lokalizacji, które są stosowane do skrzynki pocztowej. Można zidentyfikować zasady przechowywania, ponieważ identyfikator GUID rozpoczyna się od `mbx` prefiksu `skp` lub. Prefiks `skp` wskazuje, że zasady przechowywania są stosowane do Skype dla firm konwersacji w skrzynce pocztowej użytkownika. |
| Wykluczone z zasad przechowywania platformy Microsoft 365 w całej organizacji  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Jeśli skrzynka pocztowa jest wykluczona z zasad przechowywania platformy Microsoft 365 w całej organizacji, identyfikator GUID zasad przechowywania, z których jest wykluczona skrzynka pocztowa, jest wyświetlany we właściwości InPlaceHolds i jest identyfikowany przez `-mbx` prefiks.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
Jeśli właściwość *InPlaceHolds jest pusta podczas uruchamiania* polecenia cmdlet **Get-Mailbox** , do skrzynki pocztowej nadal może być stosowana co najmniej jedna ogólno organizacyjna zasady przechowywania usługi Microsoft 365. Uruchom następujące polecenie w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), aby uzyskać listę identyfikatorów GUID dla zasad przechowywania platformy Microsoft 365 w całej organizacji.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> Jeśli we właściwości InPlaceHolds jest zbyt wiele wartości, a nie wszystkie są wyświetlane, możesz uruchomić `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` polecenie , aby wyświetlić każdy identyfikator GUID w osobnym wierszu.

W poniższej tabeli opisano różne typy blokad w całej organizacji oraz sposób identyfikowania poszczególnych typów na podstawie identyfikatorów GUID zawartych we właściwości *InPlaceHolds podczas uruchamiania* polecenia cmdlet **Get-OrganizationConfig** .

| Typ blokady                                                                                                | Przykładowa wartość                           | Opis                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Zasady przechowywania platformy Microsoft 365 stosowane do skrzynek pocztowych programu Exchange, folderów publicznych programu Exchange i czatów usługi Teams | `mbx7cfb30345d454ac0a989ab3041051209:2` | Zasady przechowywania w całej organizacji stosowane do skrzynek pocztowych programu Exchange, folderów publicznych programu Exchange i czatów 1xN w usłudze Microsoft Teams są identyfikowane przez identyfikatory GUID rozpoczynające się od prefiksu `mbx` . Uwaga: czaty 1xN są przechowywane w skrzynce pocztowej poszczególnych uczestników czatu.  |
| Zasady przechowywania usługi Microsoft 365 stosowane do komunikatów kanałów Grupy Microsoft 365 i Teams                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | Zasady przechowywania w całej organizacji stosowane do grup platformy Microsoft 365 i komunikatów kanałów w usłudze Microsoft Teams są identyfikowane za pomocą identyfikatorów GUID rozpoczynających się od prefiksu `grp` . Wiadomości kanału notatek są przechowywane w skrzynce pocztowej grupy skojarzonej z zespołem firmy Microsoft. |

Aby uzyskać więcej informacji na temat zasad przechowywania stosowanych do usługi Microsoft Teams, zobacz [Informacje o zasadach przechowywania dla usługi Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Informacje o formacie wartości InPlaceHolds dla zasad przechowywania

Oprócz prefiksu (mbx, skp lub grp), który identyfikuje element we właściwości InPlaceHolds jako zasady przechowywania platformy Microsoft 365, wartość zawiera również sufiks identyfikujący typ akcji przechowywania skonfigurowanej dla zasad. Na przykład sufiks akcji jest wyróżniony pogrubionym typem w następujących przykładach:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

W poniższej tabeli zdefiniowano trzy możliwe akcje przechowywania:

| Value | Opis                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Wskazuje, że zasady przechowywania są skonfigurowane do usuwania elementów. Zasady nie zachowują elementów.                                  |
| **2** | Wskazuje, że zasady przechowywania są skonfigurowane do przechowywania elementów. Zasady nie usuwają elementów po upływie okresu przechowywania. |
| **3** | Wskazuje, że zasady przechowywania są skonfigurowane do przechowywania elementów, a następnie usuwane po upływie okresu przechowywania.             |

Aby uzyskać więcej informacji na temat akcji przechowywania, zobacz [sekcję Zachowywanie zawartości dla określonego okresu czasu](retention-settings.md#retaining-content-for-a-specific-period-of-time) .
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>Krok 2. Identyfikowanie blokady przy użyciu identyfikatora GUID

Po uzyskaniu identyfikatora GUID blokady, który jest stosowany do skrzynki pocztowej, następnym krokiem jest użycie tego identyfikatora GUID do zidentyfikowania blokady. W poniższych sekcjach pokazano, jak zidentyfikować nazwę blokady (i inne informacje) przy użyciu identyfikatora GUID blokady.

### <a name="ediscovery-holds"></a>Blokady zbierania elektronicznych materiałów dowodowych

Uruchom następujące polecenia w programie PowerShell security & Compliance, aby zidentyfikować blokadę zbierania elektronicznych materiałów dowodowych, która jest stosowana do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu UniH) dla blokady zbierania elektronicznych materiałów dowodowych, która została zidentyfikowana w kroku 1. 

Aby nawiązać połączenie z programem PowerShell security & Compliance, zobacz [Connect to Security & Compliance PowerShell (Łączenie z programem PowerShell & zgodności z zabezpieczeniami](/powershell/exchange/connect-to-scc-powershell)).

Pierwsze polecenie tworzy zmienną zawierającą informacje o blokadzie. Ta zmienna jest używana w innych poleceniach. Drugie polecenie wyświetla nazwę przypadku zbierania elektronicznych materiałów dowodowych, z którego jest skojarzona blokada. Trzecie polecenie wyświetla nazwę blokady i listę skrzynek pocztowych, do których ma zastosowanie blokada.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>blokady In-Place

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby zidentyfikować In-Place Hold zastosowaną do skrzynki pocztowej. Użyj identyfikatora GUID dla In-Place Hold, który został zidentyfikowany w kroku 1. Polecenie wyświetla nazwę blokady i listę skrzynek pocztowych, do których ma zastosowanie blokada.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Jeśli identyfikator GUID blokady In-Place rozpoczyna się od prefiksu `cld` , pamiętaj o dodaniu prefiksu podczas uruchamiania poprzedniego polecenia.

> [!IMPORTANT]
> Ponieważ nadal inwestujemy w różne sposoby zachowania zawartości skrzynki pocztowej, ogłaszamy wycofanie In-Place Holds w Centrum administracyjnym programu Exchange (EAC). Od 1 lipca 2020 r. nie będzie można tworzyć nowych blokad In-Place w Exchange Online. Nadal jednak będziesz mieć możliwość zarządzania blokadami In-Place w usłudze EAC lub za pomocą polecenia cmdlet **Set-MailboxSearch** w programie Exchange Online programu PowerShell. Jednak od 1 października 2020 r. nie będzie można zarządzać In-Place Holds. Usuniesz je tylko w usłudze EAC lub za pomocą polecenia cmdlet **Remove-MailboxSearch** . Aby uzyskać więcej informacji na temat wycofania In-Place Holds, zobacz [Wycofywanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Zasady przechowywania usługi Microsoft 365

[Połącz się z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell) i uruchom następujące polecenie, aby tożsamości zasad przechowywania platformy Microsoft 365 (w całej organizacji lub określonej lokalizacji), które są stosowane do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu mbx, skp lub grp lub sufiksu akcji), który został zidentyfikowany w kroku 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Identyfikowanie skrzynek pocztowych wstrzymanych, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu

Za każdym razem, gdy użytkownik stosuje etykietę przechowywania skonfigurowaną do *przechowywania* lub *przechowywania, a następnie usuwa* zawartość do dowolnego folderu lub elementu w skrzynce pocztowej, właściwość *ComplianceTagHoldApplied* jest ustawiona na **wartość True**. W takim przypadku skrzynka pocztowa jest traktowana podobnie jak w przypadku, gdy została wstrzymana, na przykład po przypisaniu do zasad przechowywania platformy Microsoft 365 lub wstrzymaniu postępowania sądowego, jednak z pewnymi zastrzeżeniami. Gdy *właściwość ComplianceTagHoldApplied jest ustawiona* na **wartość True**, występują następujące elementy:

- Jeśli skrzynka pocztowa lub konto użytkownika platformy Microsoft 365 zostaną usunięte, skrzynka pocztowa stanie się [nieaktywną skrzynką pocztową](inactive-mailboxes-in-office-365.md).
- Nie można wyłączyć skrzynki pocztowej (podstawowej skrzynki pocztowej lub skrzynki pocztowej archiwum, jeśli jest włączona).
- Elementy, które zostały usunięte ze skrzynki pocztowej, będą podążać jedną z dwóch ścieżek w zależności od tego, czy są oznaczone etykietą, czy nie:
    - **Elementy bez etykiet** będą podążać tą samą ścieżką, którą usuwają elementy, gdy do skrzynki pocztowej nie zostaną zastosowane żadne blokady.  Czas trwałego usunięcia tych elementów zależy od konfiguracji [przechowywania usuniętych elementów](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) i tego, czy [odzyskiwanie pojedynczego elementu](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) jest włączone dla skrzynki pocztowej, czy nie.
    - **Elementy oznaczone etykietami** zostaną zachowane w [folderze elementów możliwych do odzyskania](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) w taki sam sposób, jak w przypadku zastosowania zasad przechowywania platformy Microsoft 365, ale na poziomie poszczególnych elementów.  Jeśli wiele elementów ma różne etykiety, które są skonfigurowane do *przechowywania* lub *przechowywania, a następnie usuwa* zawartość w różnych odstępach czasu, każdy element zostanie zachowany na podstawie konfiguracji zastosowanej etykiety.
- Inne blokady, takie jak zasady przechowywania platformy Microsoft 365, blokady zbierania elektronicznych materiałów dowodowych lub blokada sądowa, mogą przedłużyć czas przechowywania oznaczonych elementów na podstawie [zasad przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence).

Aby wyświetlić wartość właściwości *ComplianceTagHoldApplied* dla pojedynczej skrzynki pocztowej, uruchom następujące polecenie w [Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Aby uzyskać więcej informacji na temat etykiet przechowywania, zobacz [etykiety przechowywania](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Zarządzanie skrzynkami pocztowymi z opóźnieniem

Po usunięciu dowolnego typu blokady ze skrzynki pocztowej zastosowano *blokadę opóźnienia* . Oznacza to, że rzeczywiste usunięcie blokady jest opóźnione o 30 dni, aby zapobiec trwałemu usunięciu danych (przeczyszczaniu) ze skrzynki pocztowej. Daje to administratorom możliwość wyszukiwania lub odzyskiwania elementów skrzynki pocztowej, które zostaną usunięte po usunięciu blokady. Blokada opóźnienia jest umieszczana w skrzynce pocztowej przy następnym uruchomieniu asystenta folderów zarządzanych i wykryciu usunięcia blokady. W szczególności blokada opóźnienia jest stosowana do skrzynki pocztowej, gdy asystent folderów zarządzanych ustawia jedną z następujących właściwości skrzynki pocztowej na **wartość True**:

- **DelayHoldApplied:** Ta właściwość dotyczy zawartości związanej z pocztą e-mail (wygenerowanej przez osoby korzystające z programu Outlook i Outlook w sieci Web), która jest przechowywana w skrzynce pocztowej użytkownika.

- **DelayReleaseHoldApplied:** Ta właściwość dotyczy zawartości opartej na chmurze (generowanej przez aplikacje spoza programu Outlook, takie jak Microsoft Teams, Microsoft Forms i Microsoft Yammer), która jest przechowywana w skrzynce pocztowej użytkownika. Dane w chmurze generowane przez aplikację firmy Microsoft są zwykle przechowywane w ukrytym folderze w skrzynce pocztowej użytkownika.

Po umieszczeniu blokady opóźnienia w skrzynce pocztowej (gdy jedna z poprzednich właściwości jest ustawiona na **wartość True**), skrzynka pocztowa jest nadal uważana za wstrzymaną przez nieograniczony czas przechowywania, tak jakby skrzynka pocztowa była wstrzymana przez spory sądowe. Po upływie 30 dni wstrzymanie opóźnienia wygaśnie, a platforma Microsoft 365 automatycznie podejmie próbę usunięcia blokady opóźnienia (ustawiając właściwość DelayHoldApplied lub DelayReleaseHoldApplied na **wartość False**), aby blokada została usunięta. Po ustawieniu jednej z tych właściwości na **wartość False** odpowiednie elementy oznaczone do usunięcia zostaną wyczyszczone przy następnym przetworzeniu skrzynki pocztowej przez Asystenta folderów zarządzanych.

Aby wyświetlić wartości właściwości DelayHoldApplied i DelayReleaseHoldApplied dla skrzynki pocztowej, uruchom następujące polecenie w [Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Aby usunąć blokadę opóźnienia przed wygaśnięciem, możesz uruchomić jedno (lub oba) następujące polecenia w programie Exchange Online programie PowerShell, w zależności od właściwości, którą chcesz zmienić:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Lub

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Musisz mieć przypisaną rolę Archiwum prawne w Exchange Online, aby używać parametrów *RemoveDelayHoldApplied* lub *RemoveDelayReleaseHoldApplied*. 

Aby usunąć blokadę opóźnienia w nieaktywnej skrzynce pocztowej, uruchom jedno z następujących poleceń w programie Exchange Online programu PowerShell:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Lub

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> Najlepszym sposobem określenia nieaktywnej skrzynki pocztowej w poprzednim poleceniu jest użycie jej wartości Distinguished Name lub Identyfikator GUID programu Exchange. Użycie jednej z tych wartości pomaga zapobiec przypadkowemu określeniu niewłaściwej skrzynki pocztowej. 

Aby uzyskać więcej informacji na temat używania tych parametrów do zarządzania blokadami opóźnień, zobacz [Set-Mailbox(Ustawianie skrzynki pocztowej](/powershell/module/exchange/set-mailbox)).

Podczas zarządzania skrzynką pocztową z opóźnieniem należy pamiętać o następujących kwestiach:

- Jeśli właściwość DelayHoldApplied lub DelayReleaseHoldApplied ma wartość **True** i skrzynka pocztowa (lub odpowiednie konto użytkownika) zostanie usunięta, skrzynka pocztowa stanie się nieaktywną skrzynką pocztową. Dzieje się tak, ponieważ skrzynka pocztowa jest uważana za wstrzymaną, jeśli któraś z właściwości ma ustawioną wartość **True**, a usunięcie skrzynki pocztowej w stanie wstrzymania powoduje nieaktywną skrzynkę pocztową. Aby usunąć skrzynkę pocztową, a nie uczynić ją nieaktywną skrzynką pocztową, należy ustawić obie właściwości na **wartość False**.

- Jak wspomniano wcześniej, skrzynka pocztowa jest uznawana za wstrzymaną przez nieograniczony czas przechowywania, jeśli właściwość DelayHoldApplied lub DelayReleaseHoldApplied jest ustawiona na **wartość True**. Nie oznacza to jednak, że *cała* zawartość w skrzynce pocztowej jest zachowywana. Zależy to od wartości ustawionej dla każdej właściwości. Załóżmy na przykład, że obie właściwości są ustawione na **wartość True** , ponieważ blokady są usuwane ze skrzynki pocztowej. Następnie usuniesz tylko blokadę opóźnienia stosowaną do danych w chmurze spoza programu Outlook (przy użyciu parametru *RemoveDelayReleaseHoldApplied* ). Następnym razem, gdy Asystent folderów zarządzanych przetwarza skrzynkę pocztową, zostaną wyczyszczone elementy inne niż Outlook oznaczone do usunięcia. Wszystkie elementy programu Outlook oznaczone do usunięcia nie zostaną usunięte, ponieważ właściwość DelayHoldApplied jest nadal ustawiona na **wartość True**. Jest też odwrotnie: jeśli wartość DelayHoldApplied ma wartość **False** , a wartość DelayReleaseHoldApplied jest ustawiona na **wartość True**, tylko elementy programu Outlook oznaczone do usunięcia zostaną wyczyszczone.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Jak potwierdzić, że zasady przechowywania w całej organizacji są stosowane do skrzynki pocztowej

Jeśli zasady przechowywania w całej organizacji są stosowane lub usuwane do skrzynki pocztowej, eksportowanie dzienników diagnostycznych skrzynki pocztowej może pomóc w pewności, że Exchange Online faktycznie zastosowała lub usunęła zasady przechowywania do skrzynki pocztowej. Aby wyświetlić te informacje, należy najpierw zweryfikować kilka elementów przy użyciu [Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Uzyskiwanie identyfikatorów GUID dla wszystkich zasad przechowywania jawnie stosowanych do skrzynki pocztowej

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Uzyskiwanie identyfikatorów GUID dla wszystkich zasad przechowywania stosowanych w całej organizacji do skrzynek pocztowych

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>Pobieranie diagnostyki skrzynki pocztowej dla funkcji HoldTracking

Dzienniki diagnostyki skrzynki pocztowej śledzenia blokady przechowują historię blokad zastosowanych do skrzynki pocztowej użytkownika.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Przejrzyj wyniki dzienników diagnostyki skrzynki pocztowej

Jeśli zbierzesz dane z poprzedniego kroku, wynikowe dane mogą wyglądać mniej więcej tak:

> **Red**`  : 0001-01-01T00:00:00.0000000`
>  **Hid**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **Ht**`  : 4`
>  **Lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **Osd**` : 2020-03-23T18:24:37.1884606Z`

Poniższa tabela ułatwia zrozumienie każdej z poprzednich wartości wymienionych w dzienniku diagnostycznym.

| Value   | Opis |
|:------- |:----------- |
| **Red**  | Wskazuje datę zakończenia, czyli datę wyłączenia zasad przechowywania. MinValue oznacza, że zasady są nadal przypisane do skrzynki pocztowej. |
| **Hid** | Wskazuje identyfikator GUID zasad przechowywania. Ta wartość będzie skorelowana z identyfikatorami GUID zebranymi dla jawnych zasad przechowywania przypisanych do skrzynki pocztowej lub zasad przechowywania w całej organizacji.|
| **Lsd** | Wskazuje datę ostatniego rozpoczęcia, czyli datę przypisania zasad przechowywania do skrzynki pocztowej.|
| **Osd** | Wskazuje oryginalną datę rozpoczęcia, czyli datę, w której program Exchange po raz pierwszy zarejestrował informacje o zasadach przechowywania. |
|||

Gdy zasady przechowywania nie są już stosowane do skrzynki pocztowej, użytkownik zostanie tymczasowo wstrzymany, aby zapobiec przeczyszczaniu zawartości. Blokadę opóźnienia można wyłączyć, `Set-Mailbox -RemoveDelayHoldApplied` uruchamiając polecenie .

## <a name="next-steps"></a>Następne kroki

Po zidentyfikowaniu blokad zastosowanych do skrzynki pocztowej można wykonywać zadania, takie jak zmiana czasu trwania blokady, tymczasowe lub trwałe usunięcie blokady lub wykluczenie nieaktywnej skrzynki pocztowej z zasad przechowywania usługi Microsoft 365. Aby uzyskać więcej informacji na temat wykonywania zadań związanych z blokadami, zobacz jeden z następujących tematów:

- Uruchom polecenie [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) w programie [PowerShell Security & Compliance](/powershell/exchange/connect-to-scc-powershell) , aby wykluczyć skrzynkę pocztową z zasad przechowywania platformy Microsoft 365 w całej organizacji. To polecenie może być używane tylko w przypadku zasad przechowywania, w których wartość właściwości *ExchangeLocation* jest równa `All`.

- [Zmień czas trwania archiwizacji dla nieaktywnej skrzynki pocztowej](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Usuń nieaktywną skrzynkę pocztową](delete-an-inactive-mailbox.md)

- [Usuwanie elementów w folderze Elementy możliwe do odzyskania w magazynach chmurowych skrzynek pocztowych](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
