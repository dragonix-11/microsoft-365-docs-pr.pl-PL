---
title: Usuń nieaktywną skrzynkę pocztową
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: f5caf497-5e8d-4b7a-bfff-d02942f38150
ms.custom:
- seo-marvel-apr2020
description: Jeśli nie musisz już zachowywać zawartości nieaktywnej skrzynki pocztowej platformy Microsoft 365, możesz trwale usunąć nieaktywną skrzynkę pocztową.
ms.openlocfilehash: a8bdd0cb98d744b6c64f651b7b7bb1754ff4f12e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634494"
---
# <a name="delete-an-inactive-mailbox"></a>Usuń nieaktywną skrzynkę pocztową

Nieaktywna skrzynka pocztowa służy do zachowania poczty e-mail byłego pracownika po opuszczeniu organizacji. Jeśli nie musisz już zachowywać zawartości nieaktywnej skrzynki pocztowej, możesz trwale usunąć nieaktywną skrzynkę pocztową, usuwając blokadę. Istnieje również możliwość umieszczenia wielu blokad w nieaktywnej skrzynce pocztowej. Na przykład nieaktywna skrzynka pocztowa może zostać umieszczona w blokadzie postępowania sądowego i na co najmniej jednej In-Place blokad. Ponadto przechowywanie usługi Microsoft 365 może być stosowane do nieaktywnej skrzynki pocztowej. Aby je usunąć, musisz usunąć wszystkie zasady przechowywania i przechowywania z nieaktywnej skrzynki pocztowej. Po usunięciu zasad przechowywania i przechowywania nieaktywna skrzynka pocztowa jest oznaczona do usunięcia i jest trwale usuwana po jej przetworzeniu.
  
> [!IMPORTANT]
> Ponieważ nadal inwestujemy w różne sposoby zachowania zawartości skrzynki pocztowej, ogłaszamy wycofanie In-Place Holds w centrum administracyjnym programu Exchange. Oznacza to, że należy użyć zasad archiwizacji i przechowywania sporów, aby utworzyć nieaktywną skrzynkę pocztową. Od 1 lipca 2020 r. nie będzie można tworzyć nowych blokad In-Place w Exchange Online. Nadal jednak będziesz mieć możliwość zmiany czasu przechowywania In-Place wstrzymania umieszczonego w nieaktywnej skrzynce pocztowej. Jednak od 1 października 2020 r. nie będzie można zmienić czasu trwania blokady. Usunięcie nieaktywnej skrzynki pocztowej będzie możliwe tylko przez usunięcie In-Place Blokada. Istniejące nieaktywne skrzynki pocztowe znajdujące się w In-Place Blokada będą nadal zachowywane do momentu usunięcia blokady. Aby uzyskać więcej informacji na temat wycofania In-Place Holds, zobacz [Wycofywanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).
  
Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać opis tego, co dzieje się po usunięciu blokad z nieaktywnej skrzynki pocztowej.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Przed usunięciem nieaktywnej skrzynki pocztowej

- Aby usunąć blokady z nieaktywnej skrzynki pocztowej, należy użyć Exchange Online programu PowerShell. Nie można użyć centrum administracyjnego programu Exchange (EAC) ani portal zgodności Microsoft Purview dla tych procedur. Aby uzyskać instrukcje krok po kroku dotyczące korzystania z programu Exchange Online programu PowerShell, zobacz [Nawiązywanie połączenia z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Zawartość nieaktywnej skrzynki pocztowej można skopiować do innej skrzynki pocztowej przed usunięciem blokady i usunięciem nieaktywnej skrzynki pocztowej. Aby uzyskać szczegółowe informacje, zobacz [Przywracanie nieaktywnej skrzynki pocztowej w Office 365](restore-an-inactive-mailbox.md).

- Jeśli usuniesz zasady przechowywania lub przechowywania z nieaktywnej skrzynki pocztowej i nietrwale usunięty okres przechowywania skrzynki pocztowej wygasł, skrzynka pocztowa zostanie trwale usunięta po upływie 183-dniowego okresu przechowywania nietrwałej skrzynki pocztowej. Aby uzyskać więcej informacji na temat okresu przechowywania nietrwałej skrzynki pocztowej, zobacz sekcję [Więcej informacji](#more-information) w tym artykule. Po trwałym usunięciu nieaktywnej skrzynki pocztowej nie można jej odzyskać. Przed usunięciem blokady upewnij się, że zawartość w skrzynce pocztowej nie jest już potrzebna. Jeśli chcesz ponownie uaktywnić nieaktywną skrzynkę pocztową, możesz ją odzyskać. Aby uzyskać szczegółowe informacje, zobacz [Odzyskiwanie nieaktywnej skrzynki pocztowej w Office 365](recover-an-inactive-mailbox.md).

- Aby uzyskać więcej informacji na temat nieaktywnych skrzynek pocztowych, zobacz [Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Krok 1. Identyfikowanie blokad w nieaktywnej skrzynce pocztowej

Jak wspomniano wcześniej, zasady wstrzymania postępowania sądowego, In-Place blokady lub przechowywania mogą być umieszczane w nieaktywnej skrzynce pocztowej. Pierwszym krokiem jest zidentyfikowanie blokad w nieaktywnej skrzynce pocztowej.
  
[Połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), a następnie uruchom następujące polecenie, aby wyświetlić informacje o blokadzie dla wszystkich nieaktywnych skrzynek pocztowych w organizacji.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

Wartość **True** właściwości **LitigationHoldEnabled** wskazuje, że nieaktywna skrzynka pocztowa znajduje się w blokadzie postępowania sądowego. Jeśli blokada In-Place zostanie umieszczona w nieaktywnej skrzynce pocztowej, identyfikator GUID blokady zostanie wyświetlony jako wartość właściwości **InPlaceHolds** . Na przykład poniższe wyniki dla dwóch nieaktywnych skrzynek pocztowych pokazują, że blokada postępowania sądowego jest umieszczana na Ann Beebe i że zasady przechowywania i przechowywania In-Place są umieszczane w usłudze Pilar Pinilla.
  
```text
DisplayName           : Ann Beebe
Name                  : annb
IsInactiveMailbox     : True
LitigationHoldEnabled : True
InPlaceHolds          : {}
...
DisplayName           : Pilar Pinilla
Name                  : pilarp
IsInactiveMailbox     : True
LitigationHoldEnabled : False
InPlaceHolds          : {c0ba3ce811b6432a8751430937152491, mbxba6f4ba25b62490aaaa253eea27426ab}
```

> [!TIP]
> Jeśli wiele In-Place blokad lub zasad przechowywania zostanie umieszczonych w nieaktywnej skrzynce pocztowej, nie zostaną wyświetlone wszystkie identyfikatory GUID blokady In-Place. Możesz uruchomić następujące polecenie, aby wyświetlić wszystkie identyfikatory GUID we właściwości InPlaceHolds:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Aby uzyskać więcej informacji na temat identyfikowania blokad, zobacz [How to identify the type of hold placed on a mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md)).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>Krok 2. Usuwanie blokady z nieaktywnej skrzynki pocztowej

Po ustaleniu, jakiego typu blokada jest umieszczana w nieaktywnej skrzynce pocztowej (i czy istnieje wiele blokad), następnym krokiem jest usunięcie blokady w skrzynce pocztowej. Jak wspomniano wcześniej, należy usunąć wszystkie blokady, aby trwale usunąć nieaktywną skrzynkę pocztową.
  
### <a name="remove-a-litigation-hold"></a>Usuwanie blokady postępowania sądowego

Uruchom następujące polecenie programu PowerShell, aby usunąć blokadę postępowania sądowego.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> Najlepszym sposobem identyfikacji nieaktywnej skrzynki pocztowej jest użycie jej wartości Distinguished Name lub Exchange GUID. Użycie jednej z tych wartości pomaga zapobiec przypadkowemu określeniu niewłaściwej skrzynki pocztowej. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Usuwanie nieaktywnej skrzynki pocztowej z zasad przechowywania

Procedura usuwania nieaktywnej skrzynki pocztowej z zasad przechowywania platformy Microsoft 365 zależy od tego, czy zasady przechowywania przypisane do nieaktywnej skrzynki pocztowej są jawne w całej organizacji:

- Zasady przechowywania w całej organizacji przypisane do wszystkich skrzynek pocztowych w organizacji. Użyj polecenia cmdlet **Get-OrganizationConfig** w programie Exchange Online programu PowerShell, aby uzyskać informacje o zasadach przechowywania w całej organizacji.

- Określone zasady przechowywania lokalizacji przypisane do określonych skrzynek pocztowych. Są to zasady przypisane do lokalizacji zawartości określonych użytkowników. Użyj polecenia cmdlet **Get-Mailbox -IncludeInactiveMailbox** w programie Exchange Online programu PowerShell, aby uzyskać informacje o zasadach przechowywania przypisanych do określonych nieaktywnych skrzynek pocztowych.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Usuwanie nieaktywnej skrzynki pocztowej z zasad przechowywania w całej organizacji

Uruchom następujące polecenie programu PowerShell, aby wykluczyć nieaktywną skrzynkę pocztową z zasad przechowywania w całej organizacji.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Aby uzyskać więcej informacji na temat identyfikowania zasad przechowywania w całej organizacji stosowanych do nieaktywnej skrzynki pocztowej i uzyskiwania identyfikatora GUID dla zasad przechowywania, zobacz sekcję "Get-OrganizationConfig" w temacie [How to identify the type of hold placed on a mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig)).

Alternatywnie możesz uruchomić następujące polecenie programu PowerShell, aby usunąć nieaktywną skrzynkę pocztową ze wszystkich zasad w całej organizacji:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Usuwanie nieaktywnej skrzynki pocztowej z określonych zasad przechowywania lokalizacji

Użyj [programu PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell) , aby usunąć nieaktywną skrzynkę pocztową z jawnych zasad przechowywania:

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -RemoveExchangeLocation <identity of inactive mailbox>
```

Aby uzyskać więcej informacji na temat identyfikowania określonych zasad przechowywania lokalizacji, które są stosowane do nieaktywnej skrzynki pocztowej, oraz uzyskiwania identyfikatora GUID dla zasad przechowywania, zobacz sekcję "Get-Mailbox" w temacie [How to identify the type of hold placed on a mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox)).

### <a name="remove-in-place-holds"></a>Usuwanie blokad In-Place

 Istnieją dwa sposoby usuwania blokady In-Place z nieaktywnej skrzynki pocztowej:
  
- **Usuń obiekt In-Place Hold**. Jeśli nieaktywna skrzynka pocztowa, którą chcesz trwale usunąć, jest jedyną źródłową skrzynką pocztową dla In-Place Hold, możesz po prostu usunąć obiekt In-Place Hold. 

    > [!NOTE]
    > Aby można było usunąć obiekt In-Place Hold, należy wyłączyć blokadę. Jeśli spróbujesz usunąć obiekt In-Place Hold z włączoną blokadą, zostanie wyświetlony komunikat o błędzie. 
  
- **Usuń nieaktywną skrzynkę pocztową jako źródłową skrzynkę pocztową In-Place Hold**. Jeśli chcesz zachować inne źródłowe skrzynki pocztowe dla In-Place Hold, możesz usunąć nieaktywną skrzynkę pocztową z listy źródłowych skrzynek pocztowych i zachować obiekt In-Place Hold.

#### <a name="delete-an-in-place-hold"></a>Usuwanie blokady In-Place

1. Utwórz zmienną zawierającą właściwości In-Place Hold, które chcesz usunąć. Użyj identyfikatora GUID In-Place Hold uzyskanego w [kroku 1. Identyfikowanie blokad w nieaktywnej skrzynce pocztowej](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. Wyłącz blokadę blokady In-Place Hold.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. Usuń blokadę In-Place.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Usuwanie nieaktywnej skrzynki pocztowej z blokady In-Place

Jeśli blokada In-Place zawiera dużą liczbę źródłowych skrzynek pocztowych, możliwe, że nieaktywna skrzynka pocztowa nie zostanie wyświetlona na stronie **Źródła** w usłudze EAC. Do 3000 skrzynek pocztowych jest wyświetlanych na stronie **Źródła** podczas edytowania blokady In-Place. Jeśli nieaktywnej skrzynki pocztowej nie ma na liście na stronie **Źródła**, możesz użyć programu Exchange Online programu PowerShell, aby usunąć ją z In-Place Hold. 
  
1. Utwórz zmienną zawierającą właściwości In-Place Hold umieszczone w nieaktywnej skrzynce pocztowej. Użyj identyfikatora GUID In-Place Hold uzyskanego w [kroku 1. Identyfikowanie blokad w nieaktywnej skrzynce pocztowej](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Sprawdź, czy nieaktywna skrzynka pocztowa jest wyświetlana jako źródłowa skrzynka pocztowa dla In-Place Hold. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > Właściwość *Sources* blokady In-Place identyfikuje źródłowe skrzynki pocztowe za pomocą ich właściwości *LegacyExchangeDN* . Ponieważ ta właściwość jednoznacznie identyfikuje nieaktywne skrzynki pocztowe, użycie właściwości *Sources* z In-Place Hold pomaga zapobiec usunięciu niewłaściwej skrzynki pocztowej. Pomaga to również uniknąć problemów, jeśli dwie skrzynki pocztowe mają ten sam alias lub adres SMTP. 

3. Usuń nieaktywną skrzynkę pocztową z listy źródłowych skrzynek pocztowych w zmiennej. Pamiętaj, aby użyć nazwy **LegacyExchangeDN** nieaktywnej skrzynki pocztowej zwróconej przez polecenie w poprzednim kroku. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Na przykład następujące polecenie usuwa nieaktywną skrzynkę pocztową dla pilar Pinilla.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Sprawdź, czy nieaktywna skrzynka pocztowa została usunięta z listy źródłowych skrzynek pocztowych w zmiennej.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Zmodyfikuj In-Place Hold przy użyciu zaktualizowanej listy źródłowych skrzynek pocztowych, które nie zawierają nieaktywnej skrzynki pocztowej.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Sprawdź, czy nieaktywna skrzynka pocztowa została usunięta z listy źródłowych skrzynek pocztowych dla In-Place Hold.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Więcej informacji

- **Nieaktywna skrzynka pocztowa jest typem nietrwale usuniętej skrzynki pocztowej.** W Exchange Online nietrwale usunięta skrzynka pocztowa jest skrzynką pocztową, która została usunięta, ale może zostać odzyskana w określonym okresie przechowywania. W przypadku nietrwałych skrzynek pocztowych, które nie są wstrzymane, można odzyskać skrzynkę pocztową w ciągu 30 dni. Nieaktywna skrzynka pocztowa (skrzynka pocztowa wstrzymana przed jej usunięciem) pozostanie w stanie nietrwałym, dopóki blokada nie zostanie usunięta. Po usunięciu blokady ze nieaktywnej skrzynki pocztowej skrzynka pocztowa nie będzie już w stanie nieaktywnym. Zamiast tego zostanie on usunięty nietrwale i pozostanie w Exchange Online przez 183 dni od dnia usunięcia blokady i możliwości odzyskania w tym czasie. Po 183 dniach nietrwale usunięta skrzynka pocztowa jest oznaczona do trwałego usunięcia i nie można jej odzyskać.

- **Co się stanie po usunięciu blokady nieaktywnej skrzynki pocztowej?** Skrzynka pocztowa jest traktowana jak inne nietrwale usunięte skrzynki pocztowe i jest oznaczona do trwałego usunięcia po upływie 183-dniowego okresu przechowywania nietrwałej skrzynki pocztowej. Ten okres przechowywania rozpoczyna się od daty usunięcia blokady ze nieaktywnej skrzynki pocztowej. Właściwość *InactiveMailboxRetireTime* jest ustawiana, gdy skrzynka pocztowa przechodzi z nieaktywnej (usuniętej nietrwale w stanie wstrzymania) na nieaktywną (nietrwale usuniętą bez blokady). W tym momencie właściwość *InactiveMailboxRetireTime* jest ustawiona na bieżącą datę przejścia. Jest uruchomiony asystent (nazywany asystentem *MailboxLifeCycle* ), który szuka skrzynek pocztowych z ustawioną właściwością *InactiveMailboxRetireTime* . Jeśli wartość "InactiveMailboxRetireTime + 183 days" jest mniejsza niż bieżąca data, spowoduje to przeczyszczenie skrzynki pocztowej.

- **Czy nieaktywna skrzynka pocztowa jest trwale usuwana natychmiast po usunięciu blokady?** Wcześniej nieaktywna skrzynka pocztowa będzie dostępna w stanie usunięcia nietrwałego przez 183 dni. Po 183 dniach skrzynka pocztowa zostanie oznaczona do trwałego usunięcia.

- **Jak wyświetlić informacje o nieaktywnej skrzynce pocztowej po usunięciu blokady?** Po usunięciu blokady i przywróceniu nieaktywnej skrzynki pocztowej do nietrwale usuniętej skrzynki pocztowej nie zostanie ona zwrócona przy użyciu parametru  *InactiveMailboxOnly*  z poleceniem cmdlet **Get-Mailbox** . Można jednak wyświetlić informacje o skrzynce pocztowej za pomocą polecenia **Get-Mailbox -SoftDeletedMailbox** . Przykład:

  ```text
  Get-Mailbox -SoftDeletedMailbox -Identity pilarp | FL Name,Identity,LitigationHoldEnabled,In
  Placeholds,WhenSoftDeleted,IsInactiveMailbox,WasInactiveMailbox,InactiveMailboxRetireTime
  Name                   : pilarp
  Identity               : Soft Deleted Objects\pilarp
  LitigationHoldEnabled  : False
  InPlaceHolds           : {}
  WhenSoftDeleted        : 6/16/2020 1:19:04 AM
  IsInactiveMailbox      : False
  WasInactiveMailbox     : True
  InactiveMailboxRetireTime : 9/30/2020 11:16:23 PM
  ```

  W powyższym przykładzie właściwość *WhenSoftDeleted* identyfikuje datę usunięcia nietrwałego, która w tym przykładzie to 16 czerwca 2020 r. Właściwość *WasInactiveMailbox* jest wyświetlana jako `True` , ponieważ wcześniej była nieaktywną skrzynką pocztową. Skrzynka pocztowa zostanie trwale usunięta 183 dni po 30 września 2020 r.
