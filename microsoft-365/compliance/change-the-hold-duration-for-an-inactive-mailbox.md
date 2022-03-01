---
title: Zmienianie czasu trwania wstrzymywania nieaktywnej skrzynki pocztowej
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: 8/29/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: bdee24ed-b8cf-4dd0-92ae-b86ec4661e6b
ms.custom:
- seo-marvel-apr2020
description: Gdy skrzynka Office 365 zostanie nieaktywna, zmień czas trwania stosowania lub zasad przechowywania Office 365 przypisanych do nieaktywnej skrzynki pocztowej.
ms.openlocfilehash: bf1131aa0d14222bec7ab1c94983925cfe39e673
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010650"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Zmienianie czasu trwania wstrzymywania nieaktywnej skrzynki pocztowej

[Nieaktywna skrzynka](inactive-mailboxes-in-office-365.md) pocztowa to stan skrzynki pocztowej używany do zachowywania wiadomości e-mail byłego pracownika po opuszczeniu organizacji. Skrzynka pocztowa staje się nieaktywna, gdy do skrzynki pocztowej jest stosowana stosowana Microsoft 365 usunięcia obiektu użytkownika.  Następujące typy blokady zapoczynują tworzenie nieaktywnych skrzynek pocztowych po usunięciu konta użytkownika:

- [Microsoft 365 przechowywania i etykiet z zachowaniem](retention.md) lub zachowaniem i usunięciem ustawień

- A hold associated with [an eDiscovery](ediscovery.md) case

- [Zawieszenie w  postępowaniach sądowych](create-a-litigation-hold.md)

- Istniejące In-Place wstrzymaj.

> [!IMPORTANT]
> Jakiekolwiek z powyższych blokady wymuszają nieaktywność skrzynki pocztowej po usunięciu konta użytkownika, Microsoft 365 zdecydowanie zaleca się korzystanie z przechowywania w programie Microsoft 365, gdy aktywnie planujesz korzystać z nieaktywnych skrzynek pocztowych.
>
> - Zbierania elektronicznych materiałów dowodowych są przeznaczone do konkretnych spraw związanych z problemami prawnie powiązanymi z określonymi terminami. W pewnym momencie sprawa prawdopodobnie zakończy się, a blokady skojarzone z tą sprawą zostaną usunięte, a sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta (lub usunięta). Jeśli z sprawę zbierania elektronicznych materiałów dowodowych zostanie skojarzona nieaktywna skrzynka pocztowa umieszczona w zbierania elektronicznych materiałów dowodowych i sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta lub usunięta, nieaktywna skrzynka pocztowa zostanie trwale usunięta.
>
> - In-Place w centrum administracyjnym usługi Exchange zostały wycofane. Od 1 lipca 2020 r. nie można utworzyć nowych In-Place w programie Exchange Online. Od 1 października 2020 r. nie można już zmieniać czasu trwania blokady w miejscu. Nieaktywną skrzynkę pocztową, do In-Place wstrzymywanie wiadomości, można usunąć tylko przez usunięcie In-Place wiadomości. Istniejące nieaktywne skrzynki pocztowe, In-Place wstrzymają, będą zachowywane do momentu usunięcia go. Aby uzyskać więcej informacji na In-Place wycofanie, zobacz Wycofanie starszych narzędzi [zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).
>
> - [Zawieszenie w procesów](create-a-litigation-hold.md) sądowych jest obsługiwane jako metoda alternatywna w celu przechowywania zawartości w skrzynce pocztowej i jej nieaktywności po usunięciu konta użytkownika. Jednak w przypadku starszej technologii zalecamy używanie przechowywania Microsoft 365 przechowywania.

Po tym, jak skrzynka pocztowa została już nieaktywna, zawartość skrzynki pocztowej wraz z [folderem](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) Elementy do odzyskania jest zachowywana do momentu jej umieszczenia w skrzynce pocztowej przed jej zmianą.  

Jeśli obowiązujące przechowywanie nie jest oparte na czasie, na przykład z zachowaniem przez czas nieograniczony zasad lub etykiety przechowywania aplikacji Microsoft 365, sprawy zbierania elektronicznych materiałów dowodowych lub postępowania w związku z postępowaniem sądowym (```LitigationHoldDuration```bez skonfigurowanego), zawartość skrzynki pocztowej będzie przez czas nieograniczony zachowywana przez czas nieograniczony do chwili usunięcia zawieszania.  

Jeśli jednak zawartość skrzynki pocztowej jest oparta na czasie, zawartość skrzynki pocztowej będzie zachowywana do czasu jej wygaśnięcia — wówczas wszystkie elementy w folderze Elementy do odzyskania zostaną trwale usunięte (usunięte) z nieaktywnej skrzynki pocztowej.

> [!NOTE]
> W przypadku nieaktywnych skrzynek pocztowych zalecamy zachowanie i usunięcie ustawień przechowywania Microsoft 365 przechowywania lub etykiet.  Jeśli wybierzesz ustawienie zachowaj tylko, folder Elementy do odzyskania zostanie trwale usunięty na koniec okresu przechowywania, jednak wszelkie inne elementy, które nie zostały usunięte, pozostaną w nieaktywnej skrzynce pocztowej przez nieograniczony czas.

W związku z rozwojem przepisów i zasad może się okazać, że trzeba zmienić czas trwania stosowania holdu przydzielonego do nieaktywnej skrzynki pocztowej.  Poniżej przedstawiono kroki, które należy wykonać w tym celu.

## <a name="connect-to-powershell"></a>Połączenie do programu PowerShell

Jak wspomniano wcześniej, tworzenie nieaktywnej skrzynki pocztowej może być wyzwalane przez wiele różnych typów blokady.  Z tego powodu, aby zmienić czas trwania blokady stosowany do nieaktywnej skrzynki pocztowej, musisz najpierw określić, jaki typ blokady ma wpływ na tę skrzynkę.  W tym celu należy użyć programu Exchange Online PowerShell do identyfikowania typów blokady, Microsoft 365 także, jeśli na nieaktywną skrzynkę pocztową mają wpływ zasady przechowywania lub etykiety, należy również użyć programu PowerShell w Centrum zabezpieczeń i zgodności w celu zidentyfikowania konkretnych zasad.

- Aby nawiązać połączenie Exchange Online z programem PowerShell lub centrum zabezpieczeń & w programie PowerShell, zobacz jeden z następujących tematów:

  - [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Połączenie do centrum & zabezpieczeń w programie PowerShell](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Krok 1. Identyfikowanie blokady nieaktywnej skrzynki pocztowej

Ponieważ w nieaktywnej skrzynce pocztowej mogą być Microsoft 365 różne typy blokady lub co najmniej jedna z tych zasad, pierwszym krokiem jest zidentyfikowanie blokady nieaktywnej skrzynki pocztowej.
  
Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić informacje o holdie dla określonej nieaktywnej skrzynki pocztowej w Twojej organizacji.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Jeśli musisz zidentyfikować typ blokowania wielu nieaktywnych skrzynek pocztowych i Twoja organizacja ma wiele z nich, wyświetlanie ich za pomocą programu PowerShell może stać się niewykonalne. W takim przypadku możesz wyeksportować wszystkie odpowiednie informacje do pliku CSV ```Path``` przy użyciu następującego polecenia i zmodyfikować odpowiednie informacje w środowisku:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

Na potrzeby tego przykładu pokazano wyniki dla 6 nieaktywnych skrzynek pocztowych z różnymi możliwymi typami blokowania.

> [!NOTE]
> Do jednej nieaktywnej skrzynki pocztowej można stosować wiele blokady w tym wiele typów blokady.
  
```text
DisplayName              : Ann Beebe
Name                     : annb
DistinguishedName        : CN=annb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 664ef44e-c1a0-47b0-9553-2ecdfc6ef840
IsInactiveMailbox        : True
LitigationHoldEnabled    : True
LitigationHoldDuration   : 365.00:00:00
LitigationHoldDate       : 10/25/2021 6:54:57 PM
LitigationHoldOwner      : admin@contoso.com
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Carol Olson
Name                     : carolo
DistinguishedName        : CN=carolo,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : e646a369-00bf-43d3-837a-8eae8b301d44
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbxcdbbb86ce60342489bff371876e7f224:3}
ComplianceTagHoldApplied : False
...
DisplayName              : Megan Bowen
Name                     : meganb
DistinguishedName        : CN=meganb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 36ec77cb-c524-468a-a8e8-bfb75e01a176
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbx6fe063689d404a5bb9940eed0f0bf5d2:1}
ComplianceTagHoldApplied : True
...
DisplayName              : Mario Necaise
Name                     : marion
DistinguishedName        : CN=marion,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 0579e039-a695-40d5-8f0a-0dc04f4b4c8f
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Abraham McMahon
Name                     : abrahamm
DistinguishedName        : CN=abrahamm,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 55ad8905-4e68-4c8d-940d-e068ec6b51fc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
ComplianceTagHoldApplied : False
...
DisplayName              : Pilar Pinilla
Name                     : pilarp
DistinguishedName        : CN=pilarp,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 8d7867d6-bb6d-4cd8-a51f-09d208f97fcc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {c0ba3ce811b6432a8751430937152491}
ComplianceTagHoldApplied : False
```

W poniższej tabeli przedstawiono sześć różnych typów holdów, które zostały użyte do oznaczania każdej skrzynki pocztowej jako nieaktywnej z powyższego przykładu.
  
|**Nieaktywna skrzynka pocztowa**|**Typ wstrzymywania**|**Jak zidentyfikować wstrzymaj nieaktywną skrzynkę pocztową**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Zawieszenie w  postępowaniach sądowych  <br/> | Właściwość  `LitigationHoldEnabled`  jest ustawiana tak, aby  `True` wskazywała, że skrzynka pocztowa jest w posiadaniu postępowaniem sądowym. <br/><br/> Ponadto ustawiono ustawienie wskazujące, `LitigationHoldDuration` `365.00:00:00` że elementy skrzynki pocztowej nie będą już objęte postępowaniem sądowym 365 dni od daty ich utworzenia (wysłane/odebrane).  <br/><br/> Wskazuje `LitigationHoldDate` datę włączonego sporu sądowego i `LitigationHoldOwner` identyfikuje osobę, która zainicjowała postępowanie sądowe. <br/> |
|Anna Olson  <br/> |Microsoft 365 przechowywania ze skrzynki Centrum zgodności platformy Microsoft 365, które są stosowane do określonych skrzynek pocztowych  <br/> |Ta `InPlaceHolds` właściwość zawiera identyfikator GUID Microsoft 365 przechowywania, które są stosowane do nieaktywnej skrzynki pocztowej. Jak widać, są to zasady przechowywania stosowane do określonych skrzynek pocztowych, ponieważ identyfikator GUID `mbx` zaczyna się od prefiksu i kończy na lub `:3``:2` . <br/><br/> Aby uzyskać więcej informacji, zobacz [Opis formatu wartości InPlaceHolds dla zasad przechowywania](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Megan Bowen <br/> | Microsoft 365 przechowywania z zachowaniem lub zachowaniem i usunięciem co najmniej jednego elementu w skrzynce pocztowej  <br/> |Właściwość `ComplianceTagHoldApplied` wskazuje, `True` że element został oznaczony etykietą z zachowaniem lub zachowaniem i usunięciem etykiety.  <br/><br/> Ponadto właściwość zawiera `InPlaceHolds` identyfikator GUID Microsoft 365 etykiet przechowywania, które są stosowane do nieaktywnej skrzynki pocztowej.  <br/><br/> Aby uzyskać więcej informacji, zobacz [Identyfikowanie skrzynek pocztowych w holdie, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Zasady przechowywania Microsoft 365 dla całej organizacji z Centrum zgodności platformy Microsoft 365  <br/> |Właściwość  `InPlaceHolds`  jest pusta, `LitigationHoldEnabled` jest `False` i `ComplianceTagHoldApplied` jest `False`. Oznacza to, że co najmniej jedna cała lokalizacja (Exchange) Microsoft 365 zasady przechowywania stosowane do organizacji, która dziedziczy nieaktywną skrzynkę pocztową. <br/><br/> Aby uzyskać więcej informacji, zobacz Jak potwierdzić zastosowanie zasad przechowywania w całej organizacji [do skrzynki pocztowej.](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Przedimek McMahon  <br/> |Wstrzymywanie sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365  <br/> |Ta  `InPlaceHolds`  właściwość zawiera identyfikator GUID przechowywania sprawy zbierania elektronicznych materiałów dowodowych, który jest umieszczany w nieaktywnej skrzynce pocztowej. Jak widać, jest to hold sprawy zbierania elektronicznych materiałów dowodowych, ponieważ identyfikator GUID zaczyna się od prefiksu  `UniH` .  <br/><br/> Aby uzyskać więcej informacji, zobacz [Zbierania elektronicznych materiałów dowodowych](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |In-Place hold  <br/> |Właściwość  `InPlaceHolds`  zawiera identyfikator GUID In-Place, który jest umieszczany w nieaktywnej skrzynce pocztowej. Można stwierdzić, że jest In-Place, ponieważ identyfikator GUID nie zaczyna się od prefiksu.  <br/><br/> **UWAGA**: Od 1 października 2020 r. nie można już zmieniać czasu trwania blokady w miejscu. Możesz usunąć tylko In-Place, co spowoduje usunięcie nieaktywnej skrzynki pocztowej. <br/><br/> Aby uzyskać więcej informacji, zobacz [Wycofanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Krok 2. Zmienianie czasu trwania wstrzymywania nieaktywnej skrzynki pocztowej

Po zidentyfikowaniu, jaki typ blokady jest umieszczany w nieaktywnej skrzynce pocztowej (i czy jest ich wiele), następnym krokiem jest zmiana czasu trwania blokady.  Ten proces różni się w zależności od typu zastosowanego wstrzymywania.

- [Zmienianie czasu trwania zasad Microsoft 365 przechowywania](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Zmienianie czasu trwania etykiety Microsoft 365 przechowywania](#change-the-duration-for-a-microsoft-365-retention-label)

- [Zmienianie czasu trwania zbierania elektronicznych materiałów dowodowych](#change-the-duration-for-an-ediscovery-hold)

- [Zmienianie czasu trwania sporu sądowego](#change-the-duration-for-a-litigation-hold)

- [Zmienianie czasu trwania In-Place Hold](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Zmienianie czasu trwania zasad Microsoft 365 przechowywania

Aby zmodyfikować czas trwania blokowania dla zasad przechowywania usługi Microsoft 365, należy najpierw zidentyfikować zasady wpływające na nieaktywną skrzynkę pocztową, `Get-RetentionCompliancePolicy` uruchamiając go ze skojarzonym identyfikatorem GUID `InPlaceHolds` z właściwości skrzynki pocztowej w programie PowerShell Centrum zabezpieczeń i zgodności.

Pamiętaj o usunięciu prefiksu i sufiksu z identyfikatora GUID podczas uruchamiania tego polecenia.  Na przykład, korzystając z powyższych przykładowych informacji, `InPlaceHolds` `:3` `mbxcdbbb86ce60342489bff371876e7f224:3` `mbx` należy użyć wartości usuń, a następnie w wyniku czego zostanie jej identyfikator GUID zasad o wartości .`cdbbb86ce60342489bff371876e7f224`  W tym przykładzie chcesz uruchomić:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

Gdy znasz nazwę zasad, możesz po prostu zmodyfikować zasady przechowywania w centrum Microsoft 365 zgodności.  Należy pamiętać, że zasady przechowywania są zazwyczaj stosowane do więcej niż jednej lokalizacji, więc modyfikowanie zasad ma wpływ na wszystkie zastosowane lokalizacje — zarówno nieaktywne, jak i aktywne, które mogą także obejmować lokalizacje inne niż Exchange.  Aby uzyskać więcej informacji, [zobacz Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md).  

> [!IMPORTANT]
> Zasady przechowywania z [włączonym blokowaniem](retention-preservation-lock.md) zachowywania mogą wydłużyć okres przechowywania, ale nie mogą zostać zmniejszone ani usunięte.

Jeśli zamierzasz zmodyfikować okres przechowywania tylko dla nieaktywnych skrzynek pocztowych lub tylko określonych nieaktywnych skrzynek pocztowych, możesz rozważyć wdrożenie adaptacyjnych zakresów [zasad, których](retention.md#adaptive-or-static-policy-scopes-for-retention) można używać do indywidualnego kierowania określonych skrzynek pocztowych — lub typów skrzynek pocztowych, takich jak nieaktywne skrzynki pocztowe — przy użyciu usługi Azure AD oraz atrybutów i właściwości usługi Exchange.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Zmienianie czasu trwania etykiety Microsoft 365 przechowywania

Podobnie jak w przypadku zasad przechowywania, podczas modyfikowania czasu trwania przechowywania etykiety przechowywania programu Microsoft 365 należy najpierw zidentyfikować zasady, `Get-RetentionCompliancePolicy` które publikują etykietę wpływającą na zawartość w nieaktywnej skrzynce pocztowej, uruchamiając skojarzony identyfikator GUID `InPlaceHolds` z właściwości skrzynki pocztowej w programie PowerShell Centrum zabezpieczeń i zgodności.

Pamiętaj o usunięciu prefiksu i sufiksu z identyfikatora GUID podczas uruchamiania tego polecenia.  Na przykład, korzystając z powyższych przykładowych informacji, `InPlaceHolds` `:1` `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` `mbx` należy użyć wartości usuń, a następnie w wyniku czego zostanie jej identyfikator GUID zasad o wartości .`6fe063689d404a5bb9940eed0f0bf5d2`  W tym przykładzie chcesz uruchomić:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

Po zidentyfikowaniu zasad będziesz wiedzieć, które etykiety zostały opublikowane i ich ustawienia.  Ponieważ etykiety dotyczą poszczególnych elementów, w zależności od liczby etykiet opublikowanych w związku z zasadami i ich ustawieniami, bezpośrednie zidentyfikowanie etykiet mających wpływ na zawartość może być nie możliwe.  

Jedną z metod identyfikowania zawartości, do których są stosowane poszczególne etykiety, jest korzystanie z [wyszukiwania zawartości](content-search.md).  Na przykład, korzystając z powyższych informacji przykładowych, założono, że zasady publikują kilka etykiet, z których jedna nosi nazwę "Zawartość-kadr".  Jeśli masz odpowiednie [uprawnienia,](microsoft-365-compliance-center-permissions.md) przeszukiwanie zawartości można uruchomić za pomocą polecenia [programu PowerShell New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch), określającego podstawowy adres SMTP nieaktywnej skrzynki pocztowej i wstępnie zapisanego z okresem (`.`) `-AllowNotFoundExchangeLocationsEnabled $true` oraz parametru, aby pominąć sprawdzanie poprawności:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Po utworzeniu wyszukiwania możesz rozpocząć wyszukiwanie, korzystając z następującego polecenia:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

Przy użyciu tej metody możesz następnie określić, które etykiety z zidentyfikowanych zasad etykiet mają zastosowanie do zawartości w nieaktywnej skrzynce pocztowej, aby zmodyfikować ich okresy przechowywania. Należy pamiętać, że etykiety przechowywania są zazwyczaj stosowane do więcej niż jednej lokalizacji, więc modyfikowanie etykiet ma wpływ na wszystkie zastosowane lokalizacje i zawartość oznaczoną etykietą, która może również zawierać lokalizacje i zawartość inną niż Exchange. Aby uzyskać więcej informacji, zobacz [Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md).

> [!NOTE]
> Nie wszystkie typy etykiet przechowywania można modyfikować.  W przypadku niektórych etykiet możesz tylko zwiększyć czas przechowywania, a w przypadku innych nie możesz w ogóle zmodyfikować okresu przechowywania.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>Zmienianie czasu trwania zbierania elektronicznych materiałów dowodowych

Blokady skojarzone ze sprawami zbierania elektronicznych materiałów dowodowych są nieokreślone, co oznacza, że nie ma czasu trwania blokady, który można zmienić. Elementy są przechowywane na zawsze lub do [](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) momentu usunięcia trzymania lub zamknięcia sprawy.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Zmienianie czasu trwania sporu sądowego

Za pomocą programu Exchange Online PowerShell można zmienić czas trwania stosowania funkcji zawieszenie w przypadku postępowania w sądach sądowych, która jest umieszczana w nieaktywnej skrzynce pocztowej. Nie można korzystać z programu EAC. Uruchom następujące polecenie, aby zmienić czas trwania blokowania. W tym przykładzie czas trwania zawieszonego połączenia jest zmieniany na nieograniczony czas:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

W efekcie elementy w nieaktywnej skrzynce pocztowej są zachowywane przez czas nieograniczony lub do czasu usunięcia zawieszania lub zmiany czasu trwania zawieszania na inną wartość.
  
> [!TIP]
> Najlepszym sposobem na zidentyfikowanie nieaktywnej skrzynki pocztowej jest użycie jej nazwy **wyróżnianej** lub **Exchange GUID**. Użycie jednej z tych wartości pomaga zapobiec przypadkowemu określeniu niewłaściwej skrzynki pocztowej.

### <a name="change-the-duration-for-an-in-place-hold"></a>Zmienianie czasu trwania In-Place Hold

In-Place zostały wycofane i nie można już ich modyfikować. Jeśli do nieaktywnej skrzynki In-Place do skrzynki pocztowej zastosowano wstrzymanie, nie można zmienić czasu trwania wstrzymywania. Możesz usunąć tylko In-Place, co spowoduje usunięcie nieaktywnej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Usuwanie nieaktywnej skrzynki pocztowej](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Więcej informacji

- **Jak jest obliczany czas trwania zawieszonego elementu w nieaktywnej skrzynce pocztowej?** Czas trwania jest obliczany na podstawie pierwotnej daty, gdy odebrano lub utworzono element skrzynki pocztowej.
    
- **Co się dzieje po wygaśnięciu czasu trwania zawieszonego?** Gdy czas trwania przechowywania dla elementu skrzynki pocztowej w folderze Elementy do odzyskania wygasa, ten element jest trwale usuwany (usuwany) z nieaktywnej skrzynki pocztowej. Jeśli nie określono czasu trwania dla umieszczenia w nieaktywnej skrzynce pocztowej, elementy w folderze Elementy do odzyskania nie są czyszowane (chyba że czas trwania przechowywania nieaktywnej skrzynki pocztowej zostanie zmieniony). 
    
- **Czy zasady Exchange MRM są nadal przetwarzane w nieaktywnych skrzynkach pocztowych?**  Jeśli zasady przechowywania MRM zostały zastosowane do skrzynki pocztowej przed jej nieaktywnym działaniem, wszelkie zasady usuwania (tagi przechowywania MRM  skonfigurowane przy użyciu akcji Usuń) będą nadal przetwarzane w nieaktywnej skrzynce pocztowej. Oznacza to, że elementy otagowane przy użyciu zasad usuwania mrm zostaną przeniesione do folderu Elementy do odzyskania po wygaśnięciu okresu przechowywania. Te elementy są czyszowane z nieaktywnej skrzynki pocztowej po wygaśnięciu czasu trwania blokowania. Jeśli nie określono czasu trwania zawieszania dla nieaktywnej skrzynki pocztowej, elementy w folderze Odzyskiwanie elementów będą zachowywane przez czas nieograniczony.

    Natomiast wszelkie zasady archiwizacji (tagi przechowywania MRM skonfigurowane za pomocą akcji **MoveToArchive** ) zawarte w zasadach przechowywania MRM przypisanych do nieaktywnej skrzynki pocztowej są ignorowane. Oznacza to, że elementy w nieaktywnej skrzynce pocztowej otagowane przy użyciu zasad archiwizacji pozostają w podstawowej skrzynce pocztowej po wygaśnięciu okresu przechowywania. Nie są one przenoszone do archiwaowej skrzynki pocztowej ani do folderu Elementy do odzyskania w archiwaowej skrzynce pocztowej. Będą one przechowywane przez czas nieograniczony.
    > [!NOTE]
    > Stosowanie zasad Exchange przechowywania (funkcji Zarządzanie rekordami wiadomości lub MRM w programie Exchange Online) nie powoduje utworzenia nieaktywnej skrzynki pocztowej po usunięciu konta użytkownika.

- **Podobnie jak w przypadku zwykłych skrzynek pocztowych asystent folderów zarządzanych (MFA) również przetwarza nieaktywne skrzynki pocztowe.** W Exchange Online uwierzytelniania wieloskładnikowego skrzynki pocztowe są przetwarzane mniej więcej raz na siedem dni. Po zmianie czasu trwania blokowania nieaktywnej skrzynki pocztowej możesz użyć polecenia **cmdlet Start-ManagedFolderAssistant** , aby natychmiast rozpocząć przetwarzanie nowego czasu trwania nowego blokowania dla nieaktywnej skrzynki pocztowej. Uruchom następujące polecenie: 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Jeśli wiele z `InPlaceHolds` nich znajduje się w nieaktywnej skrzynce pocztowej, nie są wyświetlane wszystkie identyfikatory GUID przechowywania.** Poniższe polecenie umożliwia wyświetlenie identyfikatorów GUID wszystkich `InPlaceHolds` osób umieszczonych w nieaktywnej skrzynce pocztowej.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
