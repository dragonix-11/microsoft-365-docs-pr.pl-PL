---
title: Usuwanie nieaktywnej skrzynki pocztowej
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
description: Jeśli nie potrzebujesz już zachowywać zawartości nieaktywnej skrzynki Microsoft 365, możesz trwale usunąć nieaktywną skrzynkę pocztową.
ms.openlocfilehash: 71223c0b5f53e03d51797e32f249f24146e96dee
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009551"
---
# <a name="delete-an-inactive-mailbox"></a>Usuwanie nieaktywnej skrzynki pocztowej

Nieaktywna skrzynka pocztowa służy do zachowywania wiadomości e-mail byłego pracownika po opuszczeniu organizacji. Jeśli nie potrzebujesz już zachowywać zawartości nieaktywnej skrzynki pocztowej, możesz trwale usunąć nieaktywną skrzynkę pocztową, usuwając jej hold. Ponadto może się okazać, że w nieaktywnej skrzynce pocztowej może być umieszczanych wiele blokady. Na przykład nieaktywna skrzynka pocztowa może być umieszczana w związku z postępowaniem sądowym i na co najmniej jednej In-Place blokady. Ponadto do nieaktywnej skrzynki pocztowej mogą zostać zastosowane zasady przechowywania (utworzone w Centrum zabezpieczeń i zgodności w programie Office 365 lub Microsoft 365). Aby je usunąć, musisz usunąć wszystkie zasady przechowywania i blokady ze nieaktywnej skrzynki pocztowej. Po usunięciu zdjęć blokady i zasady przechowywania nieaktywna skrzynka pocztowa zostanie oznaczona do usunięcia i trwale usunięta po jej przetworzeniu.
  
> [!IMPORTANT]
> W związku z dalszymi inwestycjami w różne sposoby zachowywania zawartości skrzynek pocztowych zapowiadamy wycofanie blokady In-Place w centrum administracyjnym firmy Exchange. Oznacza to, że w celu utworzenia nieaktywnej skrzynki pocztowej należy używać funkcji blokady w procesów sądowych i zasad przechowywania. Od 1 lipca 2020 r. nie będzie można tworzyć nowych In-Place miejsc w Exchange Online. Nadal jednak będzie można zmienić czas trwania blokowania wiadomości In-Place w nieaktywnej skrzynce pocztowej. Jednak od 1 października 2020 r. nie będzie można zmienić czasu trwania blokowania. Nieaktywną skrzynkę pocztową można usunąć tylko przez usunięcie In-Place hold. Istniejące nieaktywne skrzynki pocztowe, In-Place wstrzymają, będą zachowywane do momentu usunięcia go. Aby uzyskać więcej informacji na temat wycofania In-Place, zobacz Wycofanie starszych narzędzi [zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).
  
Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać opis tego, co dzieje się po usunięciu blokady z nieaktywnej skrzynki pocztowej.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Przed usunięciem nieaktywnej skrzynki pocztowej

- Aby usunąć z nieaktywnej skrzynki Exchange Online w programie PowerShell, należy użyć programu PowerShell. Nie możesz korzystać z centrum administracyjnego usługi Exchange(EAC). Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Możesz skopiować zawartość nieaktywnej skrzynki pocztowej do innej skrzynki pocztowej przed usunięciem tej skrzynki przez jej usunięciem. Aby uzyskać szczegółowe informacje, [zobacz Przywracanie nieaktywnej skrzynki pocztowej w Office 365](restore-an-inactive-mailbox.md).

- Jeśli usuniesz zasady przechowywania lub przechowywania ze nieaktywnej skrzynki pocztowej i wygaśnie okres przechowywania "miękkiego usunięcia" skrzynki pocztowej dla skrzynki pocztowej, skrzynka pocztowa zostanie trwale usunięta po upływie 183-dniowego okresu "miękkiego usunięcia" skrzynki pocztowej. Aby uzyskać więcej informacji na temat okresu przechowywania "miękkiego usunięcia skrzynki pocztowej", zobacz [sekcję Więcej](#more-information) informacji w tym artykule. Po trwałym usunięciu nieaktywnej skrzynki pocztowej nie można jej odzyskać. Zanim usuniesz hold, upewnij się, że nie potrzebujesz już zawartości skrzynki pocztowej. Jeśli chcesz ponownie aktywować nieaktywną skrzynkę pocztową, możesz ją odzyskać. Aby uzyskać szczegółowe informacje, [zobacz Odzyskiwanie nieaktywnej skrzynki pocztowej w Office 365](recover-an-inactive-mailbox.md).

- Aby uzyskać więcej informacji o nieaktywnych skrzynkach pocztowych, zobacz [Informacje o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Krok 1. Identyfikowanie blokady nieaktywnej skrzynki pocztowej

Jak wspomniano wcześniej, zasady przechowywania lub In-Place w związku z postępowaniem sądowym mogą być umieszczane w nieaktywnej skrzynce pocztowej. Pierwszym krokiem jest zidentyfikowanie blokady nieaktywnej skrzynki pocztowej.
  
Uruchom następujące polecenie, aby wyświetlić informacje o hold dla wszystkich nieaktywnych skrzynek pocztowych w organizacji.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

Wartość wartości True **dla** właściwości **LitigationHoldEnabled** oznacza, że nieaktywna skrzynka pocztowa jest w przypadku postępowania w sądach. Jeśli do In-Place do nieaktywnej skrzynki pocztowej zostanie umieszczona wartość GUID dla tej skrzynki, będzie ona wyświetlana jako wartość właściwości **InPlaceHolds** . Na przykład poniższe wyniki dla dwóch nieaktywnych skrzynek pocztowych wskazują, że w przypadku konta Ann Beebe jest umieszczone zawieszenie w związku z postępowaniem sądowym, a zasady przechowywania i przechowywania aplikacji In-Place są umieszczane na pilarze Pinilla.
  
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
> Jeśli w nieaktywnej skrzynce pocztowej jest umieszczanych wiele In-Place lub zasad przechowywania, nie są wyświetlane wszystkie identyfikatory GUID In-Place. Aby wyświetlić wszystkie identyfikatory GUID we właściwości InPlaceHolds, możesz uruchomić następujące polecenie:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Aby uzyskać więcej informacji na temat identyfikowania blokady, zobacz Jak zidentyfikować typy blokady [umieszczonej w skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>Krok 2. Usuwanie wstrzymywania nieaktywnej skrzynki pocztowej

Po zidentyfikowaniu, jaki typ blokady jest umieszczany w nieaktywnej skrzynce pocztowej (i czy jest ich wiele), następnym krokiem jest usunięcie blokady skrzynki pocztowej. Jak wspomniano wcześniej, aby trwale usunąć nieaktywną skrzynkę pocztową, należy usunąć wszystkie blokady.
  
### <a name="remove-a-litigation-hold"></a>Usuwanie postępowania sądowego

Jak wspomniano wcześniej, należy użyć funkcji Windows PowerShell usunąć zawieszenie w związku z postępowaniem sądowym z nieaktywnej skrzynki pocztowej. Nie można korzystać z programu EAC. Uruchom następujące polecenie, aby usunąć zawieszenie w związku z postępowaniem sądowym.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> Najlepszym sposobem na zidentyfikowanie nieaktywnej skrzynki pocztowej jest użycie jej nazwy wyróżnianej lub wartości Exchange GUID. Użycie jednej z tych wartości pomaga zapobiec przypadkowemu określeniu niewłaściwej skrzynki pocztowej. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Usuwanie nieaktywnej skrzynki pocztowej z zasad przechowywania

Procedura usuwania nieaktywnej skrzynki pocztowej z zasad przechowywania usługi Microsoft 365 zależy od tego, czy zasady przechowywania przypisane do nieaktywnej skrzynki pocztowej są jawne lub dla całej organizacji. na typie zasad przechowywania przypisanych do nieaktywnej skrzynki pocztowej.

- Zasady przechowywania przypisane do wszystkich skrzynek pocztowych w organizacji dla całej organizacji. Użyj polecenia **cmdlet Get-OrganizationConfig** w programie Exchange Online PowerShell, aby uzyskać informacje na temat zasad przechowywania w całej organizacji.

- Określone zasady przechowywania lokalizacji przypisane do określonych skrzynek pocztowych. Są to zasady przypisane do lokalizacji zawartości określonych użytkowników. Aby uzyskać informacje o zasadach przechowywania przypisanych do określonych nieaktywnych skrzynek pocztowych, użyj polecenia cmdlet **Get-Mailbox -IncludeInactiveMailbox** w programie Exchange Online PowerShell.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Usuwanie nieaktywnej skrzynki pocztowej z zasad przechowywania w całej organizacji

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wykluczyć nieaktywną skrzynkę pocztową z zasad przechowywania w całej organizacji.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Aby uzyskać więcej informacji na temat zasad przechowywania stosowanych do nieaktywnej skrzynki pocztowej w całej organizacji i uzyskiwania identyfikatora GUID dla zasad przechowywania, zobacz sekcję "Get-OrganizationConfig" w sekcji Jak zidentyfikować typ holdu umieszczonego w skrzynce [pocztowej.](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig)

Możesz również uruchomić następujące polecenie, aby usunąć nieaktywną skrzynkę pocztową ze wszystkich zasad dla całej organizacji:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Usuwanie nieaktywnej skrzynki pocztowej z określonych zasad przechowywania lokalizacji

Uruchom następujące polecenie w [programie PowerShell & zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell) , aby usunąć nieaktywną skrzynkę pocztową z jawnych zasad przechowywania.

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -AddExchangeLocationException <identity of inactive mailbox>
```

Aby uzyskać więcej informacji na temat konkretnych zasad przechowywania lokalizacji zastosowanych do nieaktywnej skrzynki pocztowej i uzyskiwania identyfikatora GUID dla zasad przechowywania, zobacz sekcję "Get-Mailbox" w sekcji Jak zidentyfikować typ przechowywania umieszczany w skrzynce [pocztowej.](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox)

### <a name="remove-in-place-holds"></a>Usuwanie In-Place blokady

 Istnieją dwa sposoby usuwania wstrzymywania wiadomości In-Place nieaktywnej skrzynki pocztowej:
  
- **Usuń In-Place Przytrzymaj.** Jeśli nieaktywna skrzynka pocztowa, którą chcesz trwale usunąć, jest jedyną źródłową skrzynką pocztową dla In-Place skrzynki pocztowej, możesz po prostu usunąć In-Place Przytrzymaj. 

    > [!NOTE]
    > Aby usunąć obiekt z wstrzymywania, należy In-Place hold. Jeśli spróbujesz usunąć obiekt In-Place z włączonym hold'em, zostanie wyświetlony komunikat o błędzie. 
  
- **Usuń nieaktywną skrzynkę pocztową jako źródłową skrzynkę pocztową In-Place Hold**. Jeśli chcesz zachować inne źródłowe skrzynki pocztowe na In-Place, możesz usunąć nieaktywną skrzynkę pocztową z listy źródłowych skrzynek pocztowych i zachować obiekt In-Place Hold.

#### <a name="delete-an-in-place-hold"></a>Usuwanie In-Place wiadomości

1. Utwórz zmienną zawierającą właściwości In-Place, którą chcesz usunąć. Użyj identyfikatora GUID In-Place, który uzyskano w [kroku 1: Identyfikowanie blokady nieaktywnej skrzynki pocztowej](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. Wyłącz hold on the In-Place Hold.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. Usuń In-Place przytrzymaj.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Usuwanie nieaktywnej skrzynki pocztowej z In-Place hold

Jeśli In-Place zawiera dużą liczbę źródłowych skrzynek pocztowych, możliwe, że nieaktywna skrzynka pocztowa nie będzie wymieniona na stronie Źródła  w Programie wiadomości e-mail. Podczas edytowania In-Place pocztowej na stronie Źródła jest wyświetlanych maksymalnie 3000 skrzynek pocztowych. Jeśli nieaktywnej skrzynki pocztowej nie ma  na stronie Źródła, możesz ją usunąć z Exchange Online PowerShell In-Place Hold. 
  
1. Utwórz zmienną zawierającą właściwości skrzynki pocztowej, która In-Place nieaktywnej skrzynki pocztowej. Użyj identyfikatora GUID In-Place, który uzyskano w [kroku 1: Identyfikowanie blokady nieaktywnej skrzynki pocztowej](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Upewnij się, że nieaktywna skrzynka pocztowa jest wymieniona jako źródłowa skrzynka pocztowa dla In-Place hold. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > Właściwość *Źródła* trzymania In-Place identyfikuje źródłowe skrzynki pocztowe na pomocą ich *właściwości LegacyExchangeDN* . Ponieważ ta właściwość jednoznacznie identyfikuje nieaktywne skrzynki pocztowe, użycie właściwości *Źródła* z In-Place zapobiega usunięciu niewłaściwej skrzynki pocztowej. Pomaga to również uniknąć problemów, jeśli dwie skrzynki pocztowe mają taki sam alias lub adres SMTP. 

3. Usuń nieaktywną skrzynkę pocztową z listy źródłowych skrzynek pocztowych zmiennej. Pamiętaj, aby użyć **LegacyExchangeDN** nieaktywnej skrzynki pocztowej zwróconej przez polecenie z poprzedniego kroku. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Na przykład poniższe polecenie usuwa nieaktywną skrzynkę pocztową dla pilara Pinilla.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Upewnij się, że nieaktywna skrzynka pocztowa została usunięta ze zmiennej ze źródłowej listy skrzynek pocztowych.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Zmodyfikuj In-Place przy użyciu zaktualizowanej listy źródłowych skrzynek pocztowych, która nie obejmuje nieaktywnej skrzynki pocztowej.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Upewnij się, że nieaktywna skrzynka pocztowa została usunięta z listy źródłowych skrzynek pocztowych na In-Place.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Więcej informacji

- **Nieaktywna skrzynka pocztowa to rodzaj "miękkiego usunięcia" skrzynki pocztowej.** Na Exchange Online "miękkie usunięcie" skrzynka pocztowa to skrzynka pocztowa, która została usunięta, ale można ją odzyskać w określonym okresie przechowywania. W przypadku skrzynek pocztowych, które nie są w stanie "miękkiego" usunięcia, można je odzyskać w ciągu 30 dni. Nieaktywna skrzynka pocztowa (skrzynka pocztowa, która przed usunięciem została usunięta) pozostaje w stanie "miękkiego usunięcia", dopóki nie zostanie usunięta. Po usunięciu go z nieaktywnej skrzynki pocztowej nie będzie ona już w stanie nieaktywnym. Zamiast tego stanie się ona "miękko usunięta" i pozostanie Exchange Online przez 183 dni od dnia usunięcia i odzyskania w tym czasie. Po 183 dniach trwale usunięta skrzynka pocztowa jest oznaczana jako "miękko usunięta" i nie można jej odzyskać.

- **Co się dzieje po usunięciu wstrzymywania nieaktywnej skrzynki pocztowej?** Skrzynka pocztowa jest traktowana jak inne niechtywne skrzynki pocztowe i jest oznaczana do trwałego usunięcia po upływie 183-dniowego okresu "miękkiego usunięcia" skrzynki pocztowej. Ten okres przechowywania zaczyna się od daty usunięcia trzymania ze nieaktywnej skrzynki pocztowej. Właściwość *InactiveMailboxRetireTime* jest ustawiana, gdy skrzynka pocztowa przechodzi z nieaktywnej (programowo usuniętej) na nieaktywną (miękko usuniętą bez blokady). W tym momencie właściwość *InactiveMailboxRetireTime* jest ustawiana na bieżącą datę przejścia. Istnieje asystent, który uruchamia (nazywany asystentem *MailboxLifeCycle* ), który wyszukuje skrzynki pocztowe, dla których ustawiono właściwość *InactiveMailboxRetireTime* . Jeśli "InactiveMailboxRetireTime + 183 dni" jest mniejsze niż bieżąca data, skrzynka pocztowa zostanie przeczyszczta.

- **Czy nieaktywna skrzynka pocztowa jest trwale usuwana natychmiast po usunięciu zawieszonego miejsca?** Skrzynka pocztowa, która wcześniej była nieaktywna, będzie dostępna w stanie "miękkiego usunięcia" przez 183 dni. Po 183 dniach skrzynka pocztowa zostanie oznaczona do trwałego usunięcia.

- **Jak wyświetlić informacje o nieaktywnej skrzynce pocztowej po usunięciu go?** Po usunięciu wstrzymywania i przywróceniu nieaktywnej skrzynki pocztowej do "miękkiego usunięcia" skrzynki pocztowej nie zostanie ona zwrócona za pomocą parametru  *InactiveMailboxOnly*  z poleceniem cmdlet **Get-Mailbox** . Możesz jednak wyświetlić informacje o skrzynce pocztowej za pomocą polecenia **Get-Mailbox -SoftDeletedMailbox** . Przykład:

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

  W powyższym przykładzie właściwość *WhenSoftDeleted* określa datę "miękkiego usunięcia", która w tym przykładzie to 16 czerwca 2020 r. Właściwość *WasInactiveMailbox jest wymieniona* jako nieaktywna `True` skrzynka pocztowa. Skrzynka pocztowa zostanie trwale usunięta 183 dni po 30 września 2020 r.
