---
title: Usuwanie elementów z folderu Elementy odzyskiwalne w chmurze skrzynki pocztowej w chmurze
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
search.appverid:
- MOE150
- MET150
ms.assetid: a85e1c87-a48e-4715-bfa9-d5275cde67b0
description: Dowiedz się, jak administratorzy mogą usuwać elementy z folderu Elementy do odzyskania użytkownika Exchange Online skrzynki pocztowej użytkownika, nawet jeśli ta skrzynka pocztowa została umieszczona w prawnych skrzynkach pocztowych.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: c349166477b610e48fd3a1b63c27d4dd4188012c
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015758"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Usuwanie elementów z folderu Elementy odzyskiwalne w chmurze skrzynek pocztowych w chmurze

Folder Elementy odzyskiwalne dla skrzynki Exchange Online pocztowej istnieje, aby chronić się przed przypadkowym lub złośliwym usunięciem. Ponadto służy do przechowywania elementów, które są zachowywane i dostępne przez funkcje zgodności, takie jak blokady i wyszukiwania zbierania elektronicznych materiałów dowodowych. Jednak w niektórych sytuacjach organizacje mogą mieć dane, które zostały nieumyślnie zachowane w folderze Elementy do odzyskania, które muszą usunąć. Na przykład użytkownik może nieświadomie wysłać lub przesłać dalej wiadomość e-mail zawierającą informacje poufne lub informacje, które mogą mieć poważne konsekwencje biznesowe. Nawet jeśli wiadomość zostanie trwale usunięta, może być przez nieograniczony czas zachowywana z powodu umieszczenia w skrzynce pocztowej statusu prawnych. Ten scenariusz jest nazywany *rozlaniem* danych, ponieważ dane zostały nieumyślnie rozlane *Office 365.* W takich sytuacjach możesz usunąć elementy ze skrzynki pocztowej programu Exchange Online użytkownika w folderze Elementy do odzyskania, nawet jeśli ta skrzynka pocztowa została umieszczona w posiadaniu jednej z funkcji przechowywania w programie Office 365. Do tych typów blokady należą blokady w związku z postępowaniem sądowym, In-Place, zbierania elektronicznych materiałów dowodowych i zasady przechowywania utworzone w centrum zabezpieczeń i zgodności w programie Office 365 lub Microsoft 365.

W tym artykule wyjaśniono, jak administratorzy mogą usuwać elementy z folderu Elementy do odzyskania dla chmurowych skrzynek pocztowych, które znajdują się w hold. Ta procedura obejmuje wyłączenie dostępu do skrzynki pocztowej, wyłączenie odzyskiwania jednego elementu, wyłączenie asystenta folderów zarządzanych z przetwarzania skrzynki pocztowej, tymczasowe usunięcie zawieszonych elementów, usunięcie elementów z folderu Elementy do odzyskania, a następnie przywrócenie poprzedniej konfiguracji skrzynki pocztowej. Oto ten proces:
  
[Krok 1. Zbieranie informacji o skrzynce pocztowej](#step-1-collect-information-about-the-mailbox)

[Krok 2. Przygotowywanie skrzynki pocztowej](#step-2-prepare-the-mailbox)

[Krok 3. Usuwanie wszystkich blokady ze skrzynki pocztowej](#step-3-remove-all-holds-from-the-mailbox)

[Krok 4. Usunięcie opóźnienia ze skrzynki pocztowej](#step-4-remove-the-delay-hold-from-the-mailbox)

[Krok 5. Usuwanie elementów z folderu Elementy do odzyskania](#step-5-delete-items-in-the-recoverable-items-folder)

[Krok 6. Przywracanie skrzynki pocztowej do poprzedniego stanu](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> Opisane w tym artykule procedury spowoduje trwałe usunięcie (usunięcie) danych ze skrzynki Exchange Online pocztowej. Oznacza to, że wiadomości usunięte z folderu Elementy do odzyskania nie mogą zostać odzyskane i nie będą dostępne na potrzeby odnajdowania prawnego lub innych celów dotyczących zgodności. Jeśli chcesz usunąć wiadomości ze skrzynki pocztowej, która jest umieszczana w stanie kontroli w związku z postępowaniem sądowym, In-Place Hold, Hold, eDiscovery hold lub zasady przechowywania utworzone w aplikacji Centrum zgodności platformy Microsoft 365, skontaktuj się z zarządzaniem rekordami lub działami prawnymi przed usunięciem umieszczenia w tym miejscu. Twoja organizacja może mieć zasady definiujące, czy skrzynka pocztowa w miejscu przechowywania lub zdarzenie rozlanie danych ma pierwszeństwo.
  
## <a name="before-you-delete-items"></a>Przed usunięciem elementów

- Aby utworzyć i uruchomić wyszukiwanie zawartości, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych lub mieć przypisaną rolę zarządzania wyszukiwaniem zgodności. Aby usuwać wiadomości, musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania Wyszukiwaniem i przeczyszczanie. Aby uzyskać informacje na temat dodawania użytkowników do grupy ról, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](./assign-ediscovery-permissions.md).

- Jeśli skrzynka pocztowa jest przypisana do zasad przechowywania w całej organizacji, musisz ją wykluczyć z zasad, zanim będzie można usunąć elementy z folderu Elementy do odzyskania. Synchronizowanie zmiany zasad i usuwanie skrzynki pocztowej z zasad może potrwać do 24 godzin. Aby uzyskać więcej informacji, zobacz sekcję "Zasady przechowywania dla całej [](#organization-wide-retention-policies) organizacji" w sekcji Usuwanie wszystkich blokady ze skrzynki pocztowej w tym artykule.

- Tej procedury nie można wykonać dla skrzynki pocztowej, do których przypisano ustawienia przechowywania przy użyciu zasad przechowywania zablokowanych przy użyciu blokady zachowywania. Jest tak, ponieważ ten kłódka uniemożliwia usunięcie lub wykluczenie skrzynki pocztowej z zasad i wyłączenie asystenta folderów zarządzanych w skrzynce pocztowej. Aby uzyskać więcej informacji na temat blokowania zasad przechowywania, zobacz Ograniczanie zmian zasad przechowywania i zasad etykiet przechowywania za pomocą blokady [zachowywania](retention-preservation-lock.md).

- Procedura opisana w tym artykule nie jest obsługiwana w przypadku nieaktywnych skrzynek pocztowych. Wynika to z tego, że po usunięciu nieaktywnej skrzynki pocztowej nie można jej ponownie przechowywać (czyli zasad przechowywania). Po usunięciu blokowania z nieaktywnej skrzynki pocztowej jest ona zmieniana w normalną, niechwytną skrzynkę pocztową i zostanie trwale usunięta z organizacji po przetworzeniu jej przez asystenta folderów zarządzanych.

- Jeśli skrzynka pocztowa nie została umieszczona w stanie przechowywania (lub nie włączono odzyskiwania pojedynczych elementów), możesz usunąć elementy z folderu Elementy do odzyskania. Aby uzyskać więcej informacji na ten temat, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail w organizacji](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>Krok 1. Zbieranie informacji o skrzynce pocztowej

Pierwszym krokiem jest zebranie wybranych właściwości z docelowej skrzynki pocztowej, które wpłyną na tę procedurę. Zapisz te ustawienia lub zapisz je w pliku tekstowym, ponieważ spowoduje to zmianę niektórych z tych właściwości, a następnie przywrócenie oryginalnych wartości w kroku 6 po usunięciu elementów z folderu Elementy do odzyskania. Oto lista właściwości skrzynki pocztowej, które należy zebrać.
  
- *SingleItemRecoveryEnabled*  *i RetainDeletedItemsFor*. W razie potrzeby wyłączysz funkcję pojedynczego odzyskiwania i zwiększysz okres przechowywania elementów usuniętych w kroku 3.

- *LitigationHoldEnabled*  *i InPlaceHolds*. Musisz zidentyfikować wszystkie blokady umieszczone w skrzynce pocztowej, aby można je było tymczasowo usunąć w kroku 3. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać porady dotyczące identyfikowania hold typu, które mogą być umieszczane w skrzynce pocztowej.

Ponadto musisz uzyskać ustawienia dostępu klienta skrzynki pocztowej, aby można było tymczasowo je wyłączyć, aby właściciel (lub inni użytkownicy) nie mogą uzyskać dostępu do skrzynki pocztowej w ramach tej procedury. Na koniec możesz uzyskać bieżący rozmiar i liczbę elementów w folderze Elementy do odzyskania. Po usunięciu elementów z folderu Elementy do odzyskania w kroku 5 użyjesz tych informacji, aby sprawdzić, czy elementy zostały usunięte.
  
1. [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pamiętaj, aby użyć nazwy użytkownika i hasła dla konta administratora, do których przypisano odpowiednie role zarządzania w programie Exchange Online.

2. Uruchom następujące polecenie, aby uzyskać informacje na temat odzyskiwania pojedynczych elementów i okresu przechowywania elementów usuniętych.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Jeśli funkcja odzyskiwania pojedynczych elementów jest włączona, musisz ją wyłączyć w kroku 2. Jeśli okres przechowywania elementów usuniętych nie jest ustawiony na 30 dni (wartość maksymalna w programie Exchange Online), możesz go zwiększyć w kroku 2.

3. Uruchom następujące polecenie, aby uzyskać ustawienia dostępu do skrzynki pocztowej.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   Wszystkie te metody dostępu wyłączysz w kroku 2.

4. Uruchom następujące polecenie, aby uzyskać informacje o blokady i zasadach przechowywania zastosowanych do skrzynki pocztowej.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > Jeśli właściwość  *InPlaceHolds*  ma zbyt wiele wartości i nie są wyświetlane wszystkie wartości,  `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` można uruchomić polecenie w celu wyświetlenia każdej wartości w osobnym wierszu.
  
5. Uruchom następujące polecenie, aby uzyskać informacje o zasadach przechowywania w całej organizacji. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Jeśli twoja organizacja ma zasady przechowywania dla całej organizacji, musisz wykluczyć skrzynkę pocztową z tych zasad w kroku 3. Replikowanie zmiany może potrwać do 24 godzin.

    > [!TIP]
    > Jeśli właściwość  *InPlaceHolds*  ma zbyt wiele wartości i nie są wyświetlane wszystkie wartości,  `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` można uruchomić polecenie w celu wyświetlenia każdej wartości w osobnym wierszu. 
  
6. Uruchom następujące polecenie, aby sprawdzić, czy do skrzynki pocztowej zastosowano opóźnienie.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   Jeśli wartość właściwości *DelayHoldApplied* lub *DelayReleaseHoldApplied* jest ustawiona na **True**, do skrzynki pocztowej jest stosowane opóźnienie i należy je usunąć. Aby uzyskać więcej informacji na temat opóźnień, zobacz [Krok 4. Usuwanie blokady opóźnienia ze skrzynki pocztowej](#step-4-remove-the-delay-hold-from-the-mailbox).

   Jeśli wartość jednej z tych właściwości jest ustawiona na **Fałsz**, do skrzynki pocztowej nie zostanie zastosowane opóźnienie i możesz pominąć krok 4.

7. Uruchom następujące polecenie, aby uzyskać bieżący rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Jeśli archiwalna skrzynka pocztowa użytkownika jest włączona, uruchom następujące polecenie, aby uzyskać rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy do odzyskania w jego archiwanej skrzynce pocztowej. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Podczas usuwania elementów w kroku 5 możesz zdecydować się na usunięcie elementów z folderu Elementy do odzyskania w podstawowej archiwaowej skrzynce pocztowej użytkownika. Jeśli dla skrzynki pocztowej włączono automatyczne rozszerzanie archiwizacji, elementy w archiwalnej skrzynce pocztowej nie zostaną usunięte.
  
## <a name="step-2-prepare-the-mailbox"></a>Krok 2. Przygotowywanie skrzynki pocztowej

Następnym krokiem po zgromadzeniu i zapisaniu informacji dotyczących skrzynki pocztowej jest przygotowanie skrzynki pocztowej przez wykonanie następujących zadań:
  
- **Wyłącz dostęp klienta do** skrzynki pocztowej, aby właściciel skrzynki pocztowej nie był w stanie uzyskać dostępu do swojej skrzynki pocztowej i nie wprowadzał żadnych zmian w danych skrzynki pocztowej w ramach tej procedury.

- **Zwiększ okres przechowywania** elementów usuniętych do 30 dni (wartość maksymalna w programie Exchange Online), aby elementy nie zostały usunięte z folderu Elementy do odzyskania, zanim będzie można je usunąć w kroku 5.

- **Wyłącz odzyskiwanie pojedynczych** elementów, aby elementy nie zostały zachowane (przez czas przechowywania elementów usuniętych) po ich usunięciu z folderu Elementy do odzyskania w kroku 5.

- **Wyłącz Asystenta folderów zarządzanych** , aby nie przetwarzał skrzynki pocztowej i zachowywał elementy usunięte w kroku 5.

Wykonaj poniższe czynności w programie Exchange Online PowerShell.
  
1. Uruchom następujące polecenie, aby wyłączyć wszystkim dostęp klienta do skrzynki pocztowej. W składni polecenia przyjęto założenie, że w skrzynce pocztowej włączono wszystkie metody dostępu klienta.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > Wyłączenie wszystkich metod dostępu klienta do skrzynki pocztowej może potrwać do 60 minut. Pamiętaj, że wyłączenie tych metod dostępu nie spowoduje rozłączenia właściciela skrzynki pocztowej, jeśli jest on obecnie zalogowany. Jeśli właściciel nie jest zalogowany, nie będzie mógł uzyskać dostępu do swojej skrzynki pocztowej po wyłączeniu tych metod dostępu.
  
2. Uruchom następujące polecenie, aby zwiększyć okres przechowywania elementów usuniętych maksymalnie o 30 dni. Założono, że bieżące ustawienie jest mniejsze niż 30 dni.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Uruchom następujące polecenie, aby wyłączyć odzyskiwanie pojedynczych elementów.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > Wyłączenie odzyskiwania jednego elementu może potrwać do 240 minut. Nie usuwaj elementów z folderu Elementy do odzyskania, dopóki nie upłynie ten okres.
  
4. Uruchom następujące polecenie, aby zapobiec przetwarzaniu skrzynki pocztowej przez asystenta folderów zarządzanych. Jak wyjaśniono wcześniej, asystenta folderów zarządzanych można wyłączyć tylko wtedy, gdy do skrzynki pocztowej nie zastosowano zasad przechowywania z blokadą zachowywania.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>Krok 3. Usuwanie wszystkich blokady ze skrzynki pocztowej

Ostatnim krokiem przed usunięciem elementów z folderu Elementy do odzyskania jest usunięcie wszystkich blokady (określonych w kroku 1) umieszczonych w skrzynce pocztowej. Wszystkie blokady muszą zostać usunięte, aby elementy nie zostały zachowane po usunięciu ich z folderu Elementy do odzyskania. Poniższe sekcje zawierają informacje na temat usuwania różnych typów blokady skrzynki pocztowej. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać porady dotyczące identyfikowania hold typu, które mogą być umieszczane w skrzynce pocztowej. Aby uzyskać więcej informacji, [zobacz Jak zidentyfikować typy blokowania umieszczonego w skrzynce Exchange Online pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md).
  
> [!CAUTION]
> Jak wspomniano wcześniej, przed usunięciem z skrzynki pocztowej należy sprawdzić to, czy rekordy są zarządzania rekordami lub działami prawnie.
  
### <a name="litigation-hold"></a>Zawieszenie w  postępowaniach sądowych
  
Uruchom następujące polecenie w programie Exchange Online PowerShell, aby usunąć ze skrzynki pocztowej zawieszenie w związku z postępowaniem sądowym.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> Podobnie jak w przypadku wyłączania odzyskiwania pojedynczych elementów usunięcie funkcji Zawieszenie w związku z postępowaniem sądowym może potrwać do 240 minut. Nie usuwaj elementów z folderu Elementy do odzyskania, dopóki nie upłynie ten okres.
  
### <a name="in-place-hold"></a>In-Place hold
  
Uruchom następujące polecenie w programie Exchange Online PowerShell, aby zidentyfikować In-Place, które jest umieszczone w skrzynce pocztowej. Użyj identyfikatora GUID dla In-Place, który został zidentyfikowany w kroku 1.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Po zidentyfikowaniu In-Place skrzynki pocztowej możesz usunąć skrzynkę pocztową z Exchange Centrum administracyjnego programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> lub programu Exchange Online PowerShell. Aby uzyskać więcej informacji, [zobacz Tworzenie lub usuwanie In-Place hold](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Zasady przechowywania stosowane do określonych skrzynek pocztowych
  
Uruchom następujące polecenie w [programie PowerShell & zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell) , aby zidentyfikować zasady przechowywania stosowane do skrzynki pocztowej. To polecenie zwróci również wszystkie zasady przechowywania Teams konwersacji zastosowane do skrzynki pocztowej. Identyfikator GUID (bez poprzedzania `mbx` lub prefiksu `skp` ) należy stosować do zasad przechowywania zidentyfikowanych w kroku 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Po zidentyfikowaniu  >  zasad przechowywania przejdź do strony Zarządzanie informacjami W programie Centrum zgodności platformy Microsoft 365, edytuj zasady przechowywania wskazane w poprzednim kroku i usuń skrzynkę pocztową z listy adresatów uwzględnionych w zasadach przechowywania.
  
### <a name="organization-wide-retention-policies"></a>Zasady przechowywania dla całej organizacji
  
Zasady przechowywania dotyczące całej Exchange, organizacji i Teams są stosowane do wszystkich skrzynek pocztowych w organizacji. Są one stosowane na poziomie organizacji (nie na poziomie skrzynki pocztowej) i są zwracane po uruchomieniu polecenia cmdlet **Get-OrganizationConfig** w kroku 1. Uruchom następujące polecenie w [programie PowerShell & w Centrum zabezpieczeń i](/powershell/exchange/exchange-online-powershell) zgodności, aby zidentyfikować zasady przechowywania dla całej organizacji. Identyfikator GUID (bez prefiksu  `mbx` ) należy stosować do zasad przechowywania dla całej organizacji, które zostały określone w kroku 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Po zidentyfikowaniu  >  zasad przechowywania dla całej organizacji przejdź do strony Zarządzanie informacjami W programie Centrum zgodności platformy Microsoft 365, edytuj poszczególne zasady przechowywania określone w poprzednim kroku dla całej organizacji i dodaj skrzynkę pocztową do listy wykluczonych adresatów. Spowoduje to usunięcie skrzynki pocztowej użytkownika z zasad przechowywania.

> [!IMPORTANT]
> Po wykluczeniu skrzynki pocztowej z zasad przechowywania dla całej organizacji zsynchronizowanie tej zmiany i usunięcie skrzynki pocztowej z zasad może potrwać do 24 godzin.

### <a name="retention-labels"></a>Etykiety przechowywania

Ilekroć użytkownik stosuje etykietę, która skonfigurowano tak, aby zachowywać lub zachowywać zawartość, a następnie usuwać ją do dowolnego folderu lub elementu w swojej skrzynce pocztowej, właściwość *ComplianceTagHoldApplied* skrzynki pocztowej ma ustawioną wartość **True**. W takim przypadku skrzynka pocztowa jest uznawana za wstrzymaną, tak jakby została umieszczona w związku z postępowaniem sądowym lub przypisana do zasad przechowywania.

Aby wyświetlić wartość właściwości *ComplianceTagHoldApplied*, uruchom następujące polecenie w programie Exchange Online PowerShell:

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Po zidentyfikowaniu, że skrzynka pocztowa znajduje się w stanie przechowywania, ponieważ etykieta przechowywania jest stosowana do folderu lub elementu, możesz użyć narzędzia Przeszukiwanie zawartości w programie Centrum zgodności platformy Microsoft 365, aby wyszukać elementy oznaczone etykietą przy użyciu warunku Etykieta **przechowywania.** Więcej informacji można znaleźć w następujących artykułach:

- Sekcja "Korzystanie z wyszukiwania zawartości w celu znalezienia całej zawartości z określoną etykietą przechowywania" w sekcji Informacje o zasadach przechowywania [i etykietach przechowywania](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)

- Sekcja "Warunki wyszukiwania" w sekcji [Zapytania słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md#conditions-for-common-properties).

Aby uzyskać więcej informacji na temat etykiet, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

### <a name="ediscovery-holds"></a>Zbierania elektronicznych materiałów dowodowych
  
Uruchom następujące polecenia w programie [PowerShell](/powershell/exchange/connect-to-scc-powershell) centrum zabezpieczeń & zgodności, aby zidentyfikować blokady skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych (nazywaną blokadymi zbierania elektronicznych materiałów dowodowych *), która* została zastosowana do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu  `UniH` ) dla zbierania elektronicznych materiałów dowodowych wskazanego w kroku 1. Drugie polecenie wyświetla nazwę sprawy zbierania elektronicznych materiałów dowodowych, z którym jest skojarzone hold. Trzecie polecenie wyświetla nazwę wstrzymywania.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

Po zidentyfikowaniu nazwy sprawy zbierania elektronicznych materiałów dowodowych i jej zbierania elektronicznych materiałów dowodowych przejdź do strony zbierania elektronicznych materiałów dowodowych w Centrum zgodności, otwórz sprawę i usuń skrzynkę pocztową z hold.  \> Aby uzyskać więcej informacji na temat identyfikowania zbierania elektronicznych materiałów dowodowych, zobacz sekcję "Zbierania elektronicznych materiałów dowodowych" w sekcji Jak zidentyfikować typ blokady umieszczonej w skrzynce [Exchange Online pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>Krok 4. Usunięcie opóźnienia ze skrzynki pocztowej

Po usunięciu dowolnego typu blokowania ze skrzynki pocztowej wartość właściwości *skrzynki pocztowej DelayHoldApplied* lub *DelayReleaseHoldApplied* jest ustawiana na **wartość True**. Dzieje się tak, gdy asystent folderów zarządzanych następnym razem przetwarza skrzynkę pocztową i wykrywa usunięcie awarii. Jest to nazywane opóźnieniem *i* oznacza, że rzeczywiste usunięcie opóźnienia jest opóźnione o 30 dni, aby zapobiec trwałemu usunięciu danych ze skrzynki pocztowej. Zadaniem opóźnienia jest nadanie administratorom możliwości wyszukania lub odzyskania elementów skrzynki pocztowej, które zostaną usunięte po usunięciu opóźnienia.  Po umieszczeniu opóźnienia w skrzynce pocztowej skrzynka pocztowa nadal jest uznawana za wstrzymaną przez nieograniczony czas, tak jakby skrzynka pocztowa była w związku z postępowaniem sądowym. Po 30 dniach opóźnienie wygasa i program Microsoft 365 automatycznie podejmie próbę usunięcia opóźnienia (ustawiając właściwość *DelayHoldApplied* lub *DelayReleaseHoldApplied* na **False**) w celu usunięcia opóźnienia. Aby uzyskać więcej informacji o opóźnieniu, zobacz sekcję "Zarządzanie skrzynkami pocztowymi podczas opóźnienia" w tece Jak zidentyfikować typ opóźnienia umieszczany w Exchange Online [pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

Jeśli wartość właściwości *DelayHoldApplied* lub *DelayReleaseHoldApplied* jest ustawiona na **True**, uruchom jedno z następujących poleceń w celu usunięcia opóźnienia:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Lub

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Do używania parametru *RemoveDelayHoldApplied* lub *RemoveDelayReleaseHoldApplied* w programie Exchange Online musi być przypisana rola funkcji Hold Prawne.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>Krok 5. Usuwanie elementów z folderu Elementy do odzyskania

Teraz możesz faktycznie usuwać elementy z folderu Elementy do odzyskania przy użyciu poleceń cmdlet [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) i [New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) w programie PowerShell w centrum zabezpieczeń & zgodności.

Aby wyszukać elementy, które znajdują się w folderze Elementy do odzyskania, zalecamy wykonanie docelowej *kolekcji*. Oznacza to, że zawęzisz zakres wyszukiwania tylko do elementów znajdujących się w folderze Elementy do odzyskania. Możesz to zrobić, uruchamiając skrypt z artykułu [Używanie wyszukiwania zawartości dla](use-content-search-for-targeted-collections.md) kolekcji docelowej. Ten skrypt zwraca wartość właściwości Identyfikator folderu dla wszystkich podfolderów w docelowym folderze Elementy do odzyskania. Następnie możesz użyć identyfikatora folderu w zapytaniu wyszukiwania, aby zwrócić elementy znajdujące się w tym folderze.

Oto omówienie procesu wyszukiwania i usuwania elementów w folderze Elementy do odzyskania użytkownika:

1. Uruchom skrypt docelowej kolekcji, który zwraca identyfikatory folderów dla wszystkich folderów w skrzynce pocztowej użytkownika docelowego. Skrypt łączy się z programem PowerShell Exchange Online i zabezpieczeniami programu PowerShell & w tej samej sesji programu PowerShell. Aby uzyskać więcej informacji, [zobacz Uruchamianie skryptu w celu uzyskania listy folderów skrzynki pocztowej](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Skopiuj identyfikatory folderów wszystkich podfolderów w folderze Elementy do odzyskania. Możesz również przekierować dane wyjściowe skryptu do pliku tekstowego.

   Oto lista i opis podfolderów w folderze Elementy do odzyskania, z których można wyszukiwać i usuwać elementy:

   - **Usunięcia**: zawiera elementy wygasnąć w przypadku elementów usuniętych, których okres przechowywania elementów usuniętych nie wygasł. Użytkownicy mogą odzyskać elementy programowo usunięte z tego podfolderu przy użyciu narzędzia Odzyskiwanie elementów usuniętych w programie Outlook.

   - **DiscoveryHolds**: Zawiera elementy trwale usunięte, które zostały zachowane przez przechowywanie zbierania elektronicznych materiałów dowodowych lub przez zasady przechowywania. Ten podfolder nie jest widoczny dla użytkowników końcowych.

   - **Holds**: Zawiera elementy usunięte z pliku Teams i innych aplikacji w chmurze, które zostały zachowane przez zasady przechowywania lub inny typ hold. Ten podfolder nie jest widoczny dla użytkowników końcowych.

3. Użyj polecenia cmdlet **New-ComplianceSearch** (w programie PowerShell w Centrum zgodności usługi Security &) lub utwórz wyszukiwanie zawartości za pomocą narzędzia przeszukiwania zawartości w Centrum zgodności, które zwraca elementy z folderu Elementy do odzyskania użytkownika docelowego. Możesz to zrobić, uwzględniając pole FolderId w zapytaniu wyszukiwania dla wszystkich podfolderów, które chcesz przeszukać. Na przykład poniższe zapytanie zwraca wszystkie wiadomości z podfolderów Deletions i eDiscoveryHolds:

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Aby uzyskać więcej informacji i przykładów dotyczących uruchamiania przeszukiwań zawartości, które używają właściwości Identyfikator folderu, zobacz Używanie identyfikatora folderu lub [wykonywanie docelowej kolekcji](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Jeśli używasz polecenia cmdlet **New-ComplianceSearch** do wyszukiwania w folderze Elementy do odzyskania, użyj polecenia cmdlet **Start-ComplianceSearch** , aby uruchomić wyszukiwanie.

4. Po utworzeniu wyszukiwania zawartości i walidacji, czy zwraca ona elementy, które mają zostać usunięte, `New-ComplianceSearchAction -Purge -PurgeType HardDelete` użyj polecenia (w programie PowerShell w Centrum zabezpieczeń & zgodności), aby trwale usunąć elementy zwrócone przez wyszukiwanie zawartości utworzone w poprzednim kroku. Na przykład można uruchomić polecenie podobne do następującego:

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Po uruchomieniu poprzedniego polecenia usuwanych jest maksymalnie 10 elementów na skrzynkę pocztową. Oznacza to, że `New-ComplianceSearchAction -Purge` być może trzeba będzie wielokrotnie uruchomić to polecenie, aby usunąć wszystkie elementy, które mają zostać usunięte w folderze Elementy do odzyskania. Aby usunąć dodatkowe elementy, najpierw musisz usunąć poprzednią akcję przeczyszczania wyszukiwania zgodności. Możesz to zrobić, uruchamiając `Remove-ComplianceSearchAction` polecenie cmdlet. Aby na przykład usunąć akcję przeczyszczania, która została uruchomione w poprzednim kroku, uruchom następujące polecenie:

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Gdy to zrobisz, możesz utworzyć nową akcję przeczyszczania wyszukiwania zgodności, aby usunąć więcej elementów. Przed utworzeniem nowej akcji należy usunąć każdą akcję przeczyszczania.

   Aby uzyskać listę akcji wyszukiwania dotyczących zgodności, możesz uruchomić `Get-ComplianceSearchAction` polecenie cmdlet. Akcje przeczyszczania są identyfikowane `_Purge` przez dołączenie ich do nazwy wyszukiwania.

### <a name="verify-that-items-were-deleted"></a>Sprawdzanie, czy elementy zostały usunięte

Aby sprawdzić, czy pomyślnie usunięto elementy z folderu Elementy do odzyskania w skrzynce pocztowej, użyj polecenia cmdlet **Get-MailboxFolderStatistics** w programie Exchange Online PowerShell, aby sprawdzić rozmiar i liczbę elementów w folderze Elementy do odzyskania. Możesz porównać te statystyki z tymi, które zostały zebrane w kroku 1.
  
Uruchom następujące polecenie, aby uzyskać bieżący rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Uruchom następujące polecenie, aby uzyskać rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy do odzyskania w archiwanej skrzynce pocztowej użytkownika.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>Krok 6. Przywracanie skrzynki pocztowej do poprzedniego stanu

Ostatnim krokiem jest przywrócenie poprzedniej konfiguracji skrzynki pocztowej. Oznacza to zresetowanie właściwości zmienionych w kroku 2 i ponownestosowanie blokady usuniętej w kroku 3. Obejmuje to:
  
- Okres przechowywania elementów usuniętych można zmienić z powrotem na poprzednią wartość. Alternatywnie możesz pozostawić ten zestaw na 30 dni, czyli maksymalną wartość w Exchange Online.

- Ponowne włączanie odzyskiwania pojedynczego elementu.

- Ponowne włączenie metod dostępu klienta w celu umożliwienia właścicielowi dostępu do jego skrzynki pocztowej.

- Ponownestosowanie usuniętych blokady i zasad przechowywania.

- Ponowne włączanie asystenta folderów zarządzanych w celu przetwarzania skrzynki pocztowej.

> [!IMPORTANT]
> Zalecamy odczekanie 24 godzin od ponownego zastosowania zasad przechowywania lub blokowania (i zweryfikowania ich stosowania) przed ponownego włączenia asystenta folderów zarządzanych w celu przetwarzania skrzynki pocztowej.
  
Wykonaj następujące czynności (w określonej kolejności) w programie Exchange Online PowerShell.
  
1. Uruchom następujące polecenie, aby zmienić okres przechowywania elementów usuniętych z powrotem na jego pierwotną wartość. Założono, że poprzednie ustawienie jest mniejsze niż 30 dni. na przykład 14 dni.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Uruchom następujące polecenie, aby ponownie włączyć odzyskiwanie pojedynczych elementów.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Uruchom następujące polecenie, aby ponownie włączyć wszystkie metody dostępu klienta do skrzynki pocztowej.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. Ponowniestosuj blokady usunięte w kroku 3. W zależności od typu hold'a skorzystaj z jednej z poniższych procedur.

    **Zawieszenie w  postępowaniach sądowych**

    Uruchom następujące polecenie, aby ponownie włączyć dla skrzynki pocztowej funkcję postępowania w związku z postępowaniem sądowym.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **In-Place Hold**

    Aby ponownie dodać skrzynkę pocztową do Exchange Online PowerShell, użyj SAC (lub programu Power In-Place Shell).

    **Zasady przechowywania stosowane do określonych skrzynek pocztowych**

    Użyj Centrum zgodności platformy Microsoft 365, aby ponownie dodać skrzynkę pocztową do zasad przechowywania. Przejdź do strony **Zarządzanie** informacjamiWczytanie  >  w Centrum zgodności, edytuj zasady przechowywania i dodaj skrzynkę pocztową z powrotem do listy adresatów, do których zastosowano zasady przechowywania.

    **Zasady przechowywania dla całej organizacji**

    Jeśli zasady przechowywania dla całej organizacji lub Exchange zostały usunięte przez ich wykluczenie z zasad, użyj przycisku Centrum zgodności platformy Microsoft 365, aby usunąć skrzynkę pocztową z listy wykluczonych użytkowników. Przejdź do strony **Zarządzanie** informacjamiWczytanie  >  w Centrum zgodności, edytuj zasady przechowywania dla całej organizacji i usuń skrzynkę pocztową z listy wykluczonych adresatów. Spowoduje to ponownestosowanie zasad przechowywania do skrzynki pocztowej użytkownika.

    **Zbierania elektronicznych materiałów dowodowych**

    Użyj Centrum zgodności platformy Microsoft 365, aby ponownie dodać skrzynkę pocztową do hold, która jest skojarzona ze sprawą zbierania elektronicznych materiałów dowodowych. Przejdź do strony **zbierania elektronicznych materiałów dowodowych** > , otwórz sprawę i dodaj skrzynkę pocztową z powrotem do hold. 

5. Uruchom następujące polecenie, aby umożliwić asystentowi folderów zarządzanych powtórz przetwarzanie skrzynki pocztowej. Jak wspomniano wcześniej, przed włączeniem asystenta folderów zarządzanych zalecamy odczekanie 24 godzin od ponownego włączenia asystenta folderów zarządzanych (i zweryfikowanie, że są one takie).

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Aby sprawdzić, czy skrzynka pocztowa została przywrócona do poprzedniej konfiguracji, możesz uruchomić następujące polecenia, a następnie porównać ustawienia z ustawieniami zebranymi w kroku 1.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Więcej informacji

W poniższej tabeli opisano sposób identyfikowania różnych typów blokady na podstawie wartości właściwości  *InPlaceHolds*  podczas uruchamiania polecenia cmdlet **Get-Mailbox** lub **Get-OrganizationConfig** . Aby uzyskać bardziej szczegółowe informacje, zobacz [Jak zidentyfikować typ blokowania umieszczany w skrzynce Exchange Online pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md).

Jak wyjaśniono wcześniej, przed pomyślnym usunięciem elementów z folderu Elementy do odzyskania należy usunąć wszystkie zasady przechowywania i blokady ze skrzynki pocztowej.
  
| Typ wstrzymywania | Wartość przykładowa | Jak zidentyfikować hold |
|:-----|:-----|:-----|
|Zawieszenie w  postępowaniach sądowych  <br/> | `True` <br/> |Właściwość  *LitigationHoldEnabled*  jest ustawiona na  `True`wartość .  <br/> |
|In-Place hold  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |Właściwość  *InPlaceHolds*  zawiera identyfikator GUID In-Place, który jest umieszczany w skrzynce pocztowej. Można stwierdzić, że jest In-Place, ponieważ identyfikator GUID nie zaczyna się od prefiksu.  <br/> Za pomocą polecenia w programie `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` Exchange Online PowerShell możesz uzyskać informacje o tym, In-Place wstrzymaj skrzynkę pocztową.  <br/> |
| Zasady przechowywania w p Centrum zgodności platformy Microsoft 365 do określonych skrzynek pocztowych  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> lub  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |Po uruchomieniu polecenia cmdlet **Get-Mailbox** właściwość  *InPlaceHolds*  zawiera również identyfikatory GUID zasad przechowywania zastosowanych do skrzynki pocztowej. Zasady przechowywania można określić, ponieważ identyfikator GUID zaczyna się od prefiksu  `mbx` . Jeśli identyfikator GUID zasad przechowywania zaczyna się od `skp` prefiksu, który wskazuje, że zasady przechowywania są stosowane do Skype dla firm konwersacji.  <br/> Aby tożsamości zasad przechowywania zastosowanych do skrzynki pocztowej, uruchom następujące polecenie w programie PowerShell centrum zabezpieczeń & zgodności: <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Pamiętaj o usunięciu prefiksu  `mbx` lub  `skp` po uruchomieniu tego polecenia.  <br/> |
|Zasady przechowywania dla całej organizacji w Centrum zgodności platformy Microsoft 365  <br/> |Brak wartości  <br/> lub  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (wskazuje, że skrzynka pocztowa jest wykluczona z zasad dla całej organizacji)  <br/> |Nawet jeśli właściwość  *InPlaceHolds*  jest pusta po uruchomieniu polecenia cmdlet **Get-Mailbox** , do skrzynki pocztowej nadal może być stosowana jedna lub więcej zasad przechowywania dla całej organizacji.  <br/> Aby to sprawdzić, możesz `Get-OrganizationConfig | FL InPlaceHolds` uruchomić polecenie w programie Exchange Online PowerShell, aby uzyskać listę identyfikatorów GUID dla zasad przechowywania dla całej organizacji. Identyfikator GUID zasad przechowywania stosowanych do skrzynek pocztowych Exchange organizacji zaczyna `mbx` się od prefiksu, na przykład `mbxa3056bb15562480fadb46ce523ff7b02`.  <br/> Aby tożsamość zasad przechowywania stosowanych do skrzynki pocztowej w całej organizacji było tożsamości, uruchom następujące polecenie w programie PowerShell w centrum zabezpieczeń & zgodności: <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Jeśli skrzynka pocztowa jest wykluczona z zasad przechowywania dla całej organizacji, po uruchomieniu polecenia cmdlet **Get-Mailbox** identyfikator GUID zasad przechowywania jest wyświetlany we właściwości *InPlaceHolds* skrzynki pocztowej użytkownika. jest identyfikowany za pomocą prefiksu `-mbx`, na przykład`-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|Wstrzymywanie sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |Właściwość *InPlaceHolds* zawiera również identyfikator GUID dowolnego miejsca przechowywania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365, które mogą zostać umieszczone w skrzynce pocztowej. Jak widać, jest to hold sprawy zbierania elektronicznych materiałów dowodowych, ponieważ identyfikator GUID zaczyna się od prefiksu  `UniH` .  <br/> Możesz użyć polecenia  `Get-CaseHoldPolicy` cmdlet w centrum zabezpieczeń & zgodności programu PowerShell, aby uzyskać informacje na temat sprawy zbierania elektronicznych materiałów dowodowych, z które jest skojarzone wstrzymanie skrzynki pocztowej. Można na przykład uruchomić  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` polecenie w celu wyświetlenia nazwy przechowywania sprawy w skrzynce pocztowej. Pamiętaj, aby po uruchomieniu  `UniH` tego polecenia usunąć prefiks.  <br/><br/> Aby tożsamości sprawy zbierania elektronicznych materiałów dowodowych, z tą skrzynką pocztową jest skojarzone, uruchom następujące polecenia:<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
