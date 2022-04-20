---
title: Zmień czas trwania archiwizacji dla nieaktywnej skrzynki pocztowej
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
description: Po nieaktywności Office 365 skrzynki pocztowej zmień czas trwania zasad przechowywania lub Office 365 przypisanych do nieaktywnej skrzynki pocztowej.
ms.openlocfilehash: d959195731ee0bf4de9b533f85fa2e2356259c12
ms.sourcegitcommit: 1d972f15a45204e89e268c5ff257021aced5e775
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2022
ms.locfileid: "64911373"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Zmień czas trwania archiwizacji dla nieaktywnej skrzynki pocztowej

[Nieaktywna skrzynka pocztowa](inactive-mailboxes-in-office-365.md) to stan skrzynki pocztowej, który służy do przechowywania poczty e-mail byłego pracownika po opuszczeniu organizacji. Skrzynka pocztowa staje się nieaktywna, gdy zostanie do niej zastosowana odpowiednia blokada przed usunięciem Microsoft 365 obiektu użytkownika.  Następujące typy blokad zainicjują utworzenie nieaktywnej skrzynki pocztowej po usunięciu konta użytkownika:

- [Microsoft 365 zasad przechowywania i etykiet](retention.md) z ustawieniami zachowywania lub zachowywania i usuwania

- Blokada skojarzona ze sprawą zbierania [elektronicznych materiałów dowodowych](ediscovery.md)

- [Wstrzymanie postępowania sądowego](create-a-litigation-hold.md)

- Istniejący In-Place wstrzymany.

> [!IMPORTANT]
> Chociaż dowolna z powyższych blokad wymusi, że skrzynka pocztowa stanie się nieaktywna po usunięciu konta użytkownika Microsoft 365, zdecydowanie zaleca się użycie Microsoft 365 przechowywania podczas proaktywnego planowania korzystania z nieaktywnych skrzynek pocztowych.
>
> - Blokady zbierania elektronicznych materiałów dowodowych są przeznaczone dla konkretnych, czasowych spraw związanych z problemem prawnym. W pewnym momencie sprawa prawna prawdopodobnie zakończy się, a blokady związane ze sprawą zostaną usunięte, a sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta (lub usunięta). Jeśli blokada umieszczona w nieaktywnej skrzynce pocztowej jest skojarzona ze sprawą zbierania elektronicznych materiałów dowodowych, a blokada zostanie zwolniona lub sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta lub usunięta, nieaktywna skrzynka pocztowa zostanie trwale usunięta.
>
> - In-Place Blokady w centrum administracyjnym Exchange są teraz wycofywane. Od 1 lipca 2020 r. nie można utworzyć nowych blokad In-Place w Exchange Online. Od 1 października 2020 r. nie można już zmienić czasu trwania blokady miejscowej. Każdą nieaktywną skrzynkę pocztową z zastosowaną blokadą In-Place można usunąć tylko przez usunięcie blokady In-Place. Istniejące nieaktywne skrzynki pocztowe znajdujące się w In-Place Blokada będą nadal zachowywane do momentu usunięcia blokady. Aby uzyskać więcej informacji na temat wycofywania In-Place, zobacz [Wycofywanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).
>
> - [Blokada postępowania sądowego](create-a-litigation-hold.md) pozostaje obsługiwana jako alternatywna metoda przechowywania zawartości w skrzynce pocztowej i uniemożliwiania jej działania po usunięciu konta użytkownika. Jednak jako starsza technologia zalecamy użycie Microsoft 365 przechowywania.

Po nieaktywności zawartość skrzynki pocztowej, w tym [folderu Elementy możliwe do odzyskania, jest zachowywana](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) do momentu, gdy blokada umieszczona w skrzynce pocztowej przed jej nieaktywnym stanem nie będzie już stosowana.  

Jeśli odpowiedni blokada nie jest oparta na czasie, na przykład blokada skojarzona z zasadami przechowywania na czas nieokreślony Microsoft 365 zasadami przechowywania lub etykietą, sprawą zbierania elektronicznych materiałów dowodowych lub blokadą postępowania sądowego (bez skonfigurowanego```LitigationHoldDuration```), zawartość skrzynki pocztowej będzie przechowywana przez czas nieokreślony do momentu usunięcia blokady.  

Jeśli jednak blokada jest oparta na czasie, zawartość skrzynki pocztowej zostanie zachowana do czasu wygaśnięcia czasu przechowywania, w którym to momencie wszystkie elementy w folderze Elementy możliwe do odzyskania zostaną trwale usunięte (przeczyszczane) ze skrzynki pocztowej nieaktywnej.

> [!NOTE]
> W przypadku nieaktywnych skrzynek pocztowych zalecamy użycie ustawienia zachowywania i usuwania dla Microsoft 365 zasad przechowywania lub etykiet.  Jeśli wybierzesz ustawienie zachowaj tylko, folder Elementy możliwe do odzyskania zostanie przeczyszczony na końcu czasu trwania blokady, jednak wszystkie inne elementy, które nie zostaną usunięte, pozostaną w nieaktywnej skrzynce pocztowej przez czas nieokreślony.

W miarę rozwoju przepisów i zasad mogą wystąpić sytuacje, w których należy zmienić czas trwania blokady przypisanej do nieaktywnej skrzynki pocztowej.  W poniższych krokach opisano, jak to zrobić.

## <a name="connect-to-powershell"></a>Połączenie do programu PowerShell

Jak wspomniano wcześniej, wiele różnych typów blokad może wyzwolić utworzenie nieaktywnej skrzynki pocztowej.  Z tego powodu, aby zmienić czas przechowywania zastosowany do nieaktywnej skrzynki pocztowej, należy najpierw określić, jakiego typu blokady mają na nią wpływ.  W tym celu należy użyć programu Exchange Online programu PowerShell do identyfikowania typów blokad, a jeśli nieaktywna skrzynka pocztowa ma wpływ na zasady lub etykiety przechowywania Microsoft 365, musisz również użyć programu PowerShell Centrum zabezpieczeń i zgodności, aby zidentyfikować określone zasady.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell lub programem PowerShell & Security & Compliance Center, zobacz jeden z następujących tematów:

  - [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Krok 1. Identyfikowanie blokad w nieaktywnej skrzynce pocztowej

Ponieważ różne typy blokad lub co najmniej jedna Microsoft 365 zasady przechowywania mogą być umieszczane w nieaktywnej skrzynce pocztowej, pierwszym krokiem jest zidentyfikowanie blokad w nieaktywnej skrzynce pocztowej.
  
Uruchom następujące polecenie w programie Exchange Online Programu PowerShell, aby wyświetlić informacje o blokadzie dla określonej nieaktywnej skrzynki pocztowej w organizacji.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Jeśli musisz zidentyfikować typ blokady dla wielu nieaktywnych skrzynek pocztowych, a twoja organizacja ma ich dużą liczbę, wyświetlanie przy użyciu programu PowerShell może stać się niezarządzane. W takim przypadku można wyeksportować wszystkie odpowiednie informacje do pliku CSV przy użyciu następującego polecenia i zmodyfikować ```Path``` je zgodnie z potrzebami środowiska:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

Na potrzeby tego przykładu poniżej przedstawiono wyniki dla sześciu nieaktywnych skrzynek pocztowych o różnych możliwych typach blokad.

> [!NOTE]
> Wiele blokad, w tym wiele typów blokad, może mieć zastosowanie do jednej nieaktywnej skrzynki pocztowej.
  
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

W poniższej tabeli zidentyfikowano sześć różnych typów blokad, które zostały użyte do nieaktywnego działania każdej skrzynki pocztowej z powyższego przykładu.
  
|**Nieaktywna skrzynka pocztowa**|**Typ blokady**|**Jak zidentyfikować blokadę w nieaktywnej skrzynce pocztowej**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Wstrzymanie postępowania sądowego  <br/> | Właściwość jest ustawiona  `LitigationHoldEnabled`  na  `True` wskazującą, że skrzynka pocztowa znajduje się w blokadzie postępowania sądowego. <br/><br/> Ponadto parametr ma wartość `365.00:00:00` wskazującą, `LitigationHoldDuration` że elementy skrzynki pocztowej nie będą już podlegać postępowaniu sądowemu po upływie 365 dni od daty ich utworzenia (wysłane/odebrane).  <br/><br/> Wskazuje `LitigationHoldDate` datę włączenia elementu LitigationHold i `LitigationHoldOwner` identyfikuje osobę, która wszczęła postępowanie sądowe. <br/> |
|Carol Olson  <br/> |Microsoft 365 zasad przechowywania z Centrum zgodności platformy Microsoft 365, które są stosowane do określonych skrzynek pocztowych  <br/> |Właściwość `InPlaceHolds` zawiera identyfikator GUID zasad przechowywania Microsoft 365 stosowanych do nieaktywnej skrzynki pocztowej. Można powiedzieć, że są to zasady przechowywania stosowane do określonych skrzynek pocztowych, ponieważ identyfikator GUID zaczyna się od prefiksu `mbx` i kończy się znakiem `:2` lub `:3`. <br/><br/> Aby uzyskać więcej informacji, zobacz [Opis formatu wartości InPlaceHolds dla zasad przechowywania](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Megan Bowen <br/> | Microsoft 365 etykieta przechowywania z akcją zachowywania lub zachowywania i usuwania jest stosowana do co najmniej jednego elementu w skrzynce pocztowej  <br/> |Właściwość `ComplianceTagHoldApplied` `True` wskazuje, że element został oznaczony etykietą zachowywania lub zachowywania i usuwania.  <br/><br/> Ponadto właściwość `InPlaceHolds` zawiera identyfikator GUID zasad etykiety przechowywania Microsoft 365 zastosowanych do nieaktywnej skrzynki pocztowej.  <br/><br/> Aby uzyskać więcej informacji, zobacz [Identyfikowanie zablokowanych skrzynek pocztowych, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Zasady przechowywania Microsoft 365 w całej organizacji z Centrum zgodności platformy Microsoft 365  <br/> |Właściwość jest pusta  `InPlaceHolds`  , `LitigationHoldEnabled` jest `False` i `ComplianceTagHoldApplied` jest `False`. Oznacza to, że co najmniej jedna cała lokalizacja (Exchange) Microsoft 365 zasad przechowywania stosowanych do organizacji, którą dziedziczy nieaktywna skrzynka pocztowa. <br/><br/> Aby uzyskać więcej informacji, zobacz [How to confirm that an organization-wide retention policy is applied to a mailbox (Jak potwierdzić, że zasady przechowywania w całej organizacji są stosowane do skrzynki pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox)) <br/> |
|Abraham McMahon  <br/> |Sprawa zbierania elektronicznych materiałów dowodowych jest przechowywana w Centrum zgodności platformy Microsoft 365  <br/> |Właściwość  `InPlaceHolds`  zawiera identyfikator GUID blokady sprawy zbierania elektronicznych materiałów dowodowych umieszczony w nieaktywnej skrzynce pocztowej. Możesz powiedzieć, że jest to blokada sprawy zbierania elektronicznych materiałów dowodowych, ponieważ identyfikator GUID rozpoczyna się od prefiksu  `UniH` .  <br/><br/> Aby uzyskać więcej informacji, zobacz [Blokady zbierania elektronicznych materiałów dowodowych](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |blokada In-Place  <br/> |Właściwość  `InPlaceHolds`  zawiera identyfikator GUID blokady In-Place umieszczony w nieaktywnej skrzynce pocztowej. Możesz powiedzieć, że jest to In-Place Hold, ponieważ identyfikator GUID nie zaczyna się od prefiksu.  <br/><br/> **UWAGA**: Od 1 października 2020 r. czas trwania blokady miejscowej nie może już ulec zmianie. Możesz usunąć tylko In-Place Hold, co spowoduje usunięcie nieaktywnej skrzynki pocztowej. <br/><br/> Aby uzyskać więcej informacji, zobacz [Wycofywanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Krok 2. Zmiana czasu przechowywania nieaktywnej skrzynki pocztowej

Po zidentyfikowaniu typu blokady w nieaktywnej skrzynce pocztowej (i tego, czy istnieje wiele blokad), następnym krokiem jest zmiana czasu trwania blokady.  Proces różni się w zależności od typu blokady.

- [Zmienianie czasu trwania zasad przechowywania Microsoft 365](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Zmienianie czasu trwania etykiety przechowywania Microsoft 365](#change-the-duration-for-a-microsoft-365-retention-label)

- [Zmienianie czasu trwania blokady zbierania elektronicznych materiałów dowodowych](#change-the-duration-for-an-ediscovery-hold)

- [Zmienianie czasu trwania blokady postępowania sądowego](#change-the-duration-for-a-litigation-hold)

- [Zmienianie czasu trwania blokady In-Place](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Zmienianie czasu trwania zasad przechowywania Microsoft 365

Aby zmodyfikować czas przechowywania dla zasad przechowywania Microsoft 365, należy najpierw zidentyfikować zasady wpływające na nieaktywną skrzynkę pocztową, uruchamiając z `Get-RetentionCompliancePolicy` skojarzonym identyfikatorem GUID z `InPlaceHolds` właściwości w skrzynce pocztowej w programie PowerShell Centrum zabezpieczeń i zgodności.

Pamiętaj, aby usunąć prefiks i sufiks z identyfikatora GUID podczas uruchamiania tego polecenia.  Na przykład, korzystając z przykładowych informacji z powyższych `mbxcdbbb86ce60342489bff371876e7f224:3` informacji, należy wziąć `InPlaceHolds` wartość, a następnie usunąć `mbx` i `:3` spowodować identyfikator GUID zasad .`cdbbb86ce60342489bff371876e7f224`  W tym przykładzie należy uruchomić następujące polecenie:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

Gdy znasz nazwę zasad, możesz po prostu zmodyfikować zasady przechowywania w centrum zgodności Microsoft 365.  Należy pamiętać, że zasady przechowywania są zwykle stosowane do więcej niż jednej lokalizacji, więc modyfikowanie zasad będzie miało wpływ na wszystkie zastosowane lokalizacje — zarówno nieaktywne, jak i aktywne, które mogą również obejmować lokalizacje inne niż Exchange.  Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md).  

> [!IMPORTANT]
> Zasady przechowywania z włączoną [blokadą zachowywania](retention-preservation-lock.md) mogą mieć przedłużony okres przechowywania, ale nie są zmniejszane ani usuwane.

Jeśli celem jest zmodyfikowanie okresu przechowywania tylko dla nieaktywnych skrzynek pocztowych lub tylko określonych nieaktywnych skrzynek pocztowych, możesz rozważyć wdrożenie [adaptacyjnych zakresów zasad](retention.md#adaptive-or-static-policy-scopes-for-retention), które mogą służyć do indywidualnego określania konkretnych skrzynek pocztowych lub typów skrzynek pocztowych, takich jak nieaktywne skrzynki pocztowe , przy użyciu usługi Azure AD i Exchange atrybutów i właściwości.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Zmienianie czasu trwania etykiety przechowywania Microsoft 365

Podobnie jak w przypadku zasad przechowywania, podczas modyfikowania czasu przechowywania etykiety przechowywania Microsoft 365 należy najpierw zidentyfikować zasady, które publikują etykietę wpływającą na zawartość w nieaktywnej skrzynce pocztowej, uruchamiając `Get-RetentionCompliancePolicy` skojarzony identyfikator GUID z `InPlaceHolds` właściwości w skrzynce pocztowej w programie PowerShell Centrum zabezpieczeń i zgodności.

Pamiętaj, aby usunąć prefiks i sufiks z identyfikatora GUID podczas uruchamiania tego polecenia.  Na przykład, korzystając z przykładowych informacji z powyższych `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` informacji, należy wziąć `InPlaceHolds` wartość, a następnie usunąć `mbx` i `:1` spowodować identyfikator GUID zasad .`6fe063689d404a5bb9940eed0f0bf5d2`  W tym przykładzie należy uruchomić następujące polecenie:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

Po zidentyfikowaniu zasad będziesz wiedzieć, które etykiety zostały opublikowane i jakie są ich ustawienia.  Ponieważ etykiety mają zastosowanie do poszczególnych elementów, w zależności od liczby etykiet opublikowanych przy użyciu zasad i ich ustawień, możesz nie być w stanie bezpośrednio określić, która etykieta ma wpływ na zawartość.  

Jedną z metod, za pomocą których można zidentyfikować zawartość, do których stosuje się każdą etykietę, jest użycie [wyszukiwania zawartości](content-search.md).  Na przykład korzystając z powyższych przykładowych informacji, załóżmy, że zasady publikują kilka etykiet, z których jedna nosi nazwę "HR-Content".  Przy [prawidłowych uprawnieniach](microsoft-365-compliance-center-permissions.md) można uruchomić wyszukiwanie zawartości za pomocą [polecenia New-ComplianceSearch programu PowerShell](/powershell/module/exchange/new-compliancesearch), określając podstawowy adres SMTP nieaktywnej skrzynki pocztowej, wstępnie z kropką (`.`) i `-AllowNotFoundExchangeLocationsEnabled $true` parametrem pomijającym walidację:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Po utworzeniu wyszukiwania rozpoczniesz wyszukiwanie przy użyciu następującego polecenia:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

Korzystając z tej metody, możesz określić, które etykiety z zidentyfikowanych zasad etykiet mają zastosowanie do zawartości w nieaktywnej skrzynce pocztowej, aby można było modyfikować ich okresy przechowywania. Należy pamiętać, że etykiety przechowywania są zwykle stosowane do więcej niż jednej lokalizacji, dlatego modyfikowanie etykiety będzie miało wpływ na wszystkie zastosowane lokalizacje i zawartość z etykietami, które mogą również obejmować lokalizacje i zawartość inną niż Exchange. Aby uzyskać więcej informacji, zobacz [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md).

> [!NOTE]
> Nie można modyfikować wszystkich typów etykiet przechowywania.  W przypadku niektórych etykiet może być możliwe tylko wydłużenie czasu przechowywania, a w przypadku innych może nie być możliwe zmodyfikowanie okresu przechowywania w ogóle.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>Zmienianie czasu trwania blokady zbierania elektronicznych materiałów dowodowych

Blokady skojarzone ze sprawami zbierania elektronicznych materiałów dowodowych są przechowywane na czas nieokreślony, co oznacza, że nie ma czasu przechowywania, który można zmienić. Elementy są przechowywane na zawsze lub do momentu [usunięcia blokady](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) lub zamknięcia sprawy.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Zmienianie czasu trwania blokady postępowania sądowego

Należy użyć Exchange Online programu PowerShell, aby zmienić czas przechowywania blokady postępowania sądowego umieszczonego w nieaktywnej skrzynce pocztowej. Nie można użyć umowy EAC. Uruchom następujące polecenie, aby zmienić czas przechowywania. W tym przykładzie czas trwania blokady jest zmieniany na nieograniczony okres czasu:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

W rezultacie elementy w nieaktywnej skrzynce pocztowej są przechowywane przez czas nieokreślony lub do momentu usunięcia blokady lub zmiany czasu przechowywania na inną wartość.
  
> [!TIP]
> Najlepszym sposobem identyfikacji nieaktywnej skrzynki pocztowej jest użycie jej **wartości Identyfikator GUID lub nazwa wyróżniająca** lub **Exchange**. Użycie jednej z tych wartości pomaga zapobiec przypadkowemu określeniu niewłaściwej skrzynki pocztowej.

### <a name="change-the-duration-for-an-in-place-hold"></a>Zmienianie czasu trwania blokady In-Place

In-Place Blokady zostały wycofane i nie można ich już modyfikować. Jeśli nieaktywna skrzynka pocztowa ma zastosowany In-Place Hold, nie można zmienić czasu przechowywania. Można usunąć tylko In-Place Hold, co spowoduje usunięcie nieaktywnej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Usuwanie nieaktywnej skrzynki pocztowej](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Więcej informacji

- **Jak jest obliczany czas przechowywania dla elementu w nieaktywnej skrzynce pocztowej?** Czas trwania jest obliczany na podstawie oryginalnej daty odebrania lub utworzenia elementu skrzynki pocztowej.
    
- **Co się stanie, gdy czas trwania blokady wygaśnie?** Gdy czas przechowywania wygaśnie dla elementu skrzynki pocztowej w folderze Elementy możliwe do odzyskania, element zostanie trwale usunięty (przeczyszczany) ze nieaktywnej skrzynki pocztowej. Jeśli dla blokady umieszczonej w nieaktywnej skrzynce pocztowej nie określono czasu trwania, elementy w folderze Elementy możliwe do odzyskania nigdy nie zostaną wyczyszczone (chyba że czas przechowywania nieaktywnej skrzynki pocztowej zostanie zmieniony). 
    
- **Czy zasady Exchange MRM są nadal przetwarzane w nieaktywnych skrzynkach pocztowych?**  Jeśli zasady przechowywania MRM zostały zastosowane do skrzynki pocztowej przed jej nieaktywnym działaniem, wszelkie zasady usuwania (tagi przechowywania MRM skonfigurowane za pomocą akcji **Usuń** ) będą nadal przetwarzane w nieaktywnej skrzynce pocztowej. Oznacza to, że elementy oznaczone zasadami usuwania mrm zostaną przeniesione do folderu Elementy możliwe do odzyskania po upływie okresu przechowywania. Te elementy są usuwane z nieaktywnej skrzynki pocztowej po wygaśnięciu czasu przechowywania. Jeśli czas przechowywania nie zostanie określony dla nieaktywnej skrzynki pocztowej, elementy w folderze Odzyskiwanie elementów zostaną zachowane przez czas nieokreślony.

    Z drugiej strony wszystkie zasady archiwum (tagi przechowywania mrm skonfigurowane za pomocą akcji **MoveToArchive** ), które są uwzględnione w zasadach przechowywania mrm przypisanych do nieaktywnej skrzynki pocztowej, są ignorowane. Oznacza to, że elementy w nieaktywnej skrzynce pocztowej oznaczone zasadami archiwum pozostają w podstawowej skrzynce pocztowej po upływie okresu przechowywania. Nie są one przenoszone do skrzynki pocztowej archiwum ani do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum. Zostaną one zachowane na czas nieokreślony.
    > [!NOTE]
    > Zastosowanie zasad przechowywania Exchange (funkcja Zarządzanie rekordami obsługi komunikatów lub MRM w Exchange Online) nie powoduje utworzenia nieaktywnej skrzynki pocztowej po usunięciu konta użytkownika.

- **Podobnie jak w przypadku zwykłych skrzynek pocztowych, asystent folderów zarządzanych (MFA) przetwarza również nieaktywne skrzynki pocztowe.** W Exchange Online uwierzytelnianie wieloskładnikowe przetwarza skrzynki pocztowe około raz na siedem dni. Po zmianie czasu przechowywania nieaktywnej skrzynki pocztowej możesz użyć polecenia cmdlet **Start-ManagedFolderAssistant** , aby natychmiast rozpocząć przetwarzanie nowego czasu przechowywania nieaktywnej skrzynki pocztowej. Uruchom następujące polecenie: 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Jeśli wiele z nich `InPlaceHolds` zostanie umieszczonych w nieaktywnej skrzynce pocztowej, nie zostaną wyświetlone wszystkie identyfikatory GUID blokady.** Możesz uruchomić następujące polecenie, aby wyświetlić identyfikatory GUID dla wszystkich `InPlaceHolds` elementów umieszczonych w nieaktywnej skrzynce pocztowej.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
