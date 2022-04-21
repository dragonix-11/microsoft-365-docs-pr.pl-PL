---
title: Usuwanie elementów w folderze Elementy możliwe do odzyskania
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
description: Dowiedz się, jak administratorzy mogą usuwać elementy w folderze elementów możliwych do odzyskania użytkownika dla skrzynki pocztowej Exchange Online, nawet jeśli ta skrzynka pocztowa została wstrzymana ze względów prawnych.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: b421be087980c7878b79e3dbc03759ec45c546d8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001197"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Usuwanie elementów w folderze Elementy możliwe do odzyskania w magazynach chmurowych skrzynek pocztowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Folder Elementy do odzyskania dla skrzynki pocztowej Exchange Online istnieje w celu ochrony przed przypadkowymi lub złośliwymi usunięciami. Jest ona również używana do przechowywania elementów przechowywanych i uzyskiwanych przez funkcje zgodności, takie jak blokady i wyszukiwania zbierania elektronicznych materiałów dowodowych. Jednak w niektórych sytuacjach organizacje mogą mieć dane, które zostały przypadkowo zachowane w folderze Elementy możliwe do odzyskania, które muszą usunąć. Na przykład użytkownik może nieświadomie wysłać lub przesłać wiadomość e-mail zawierającą poufne informacje lub informacje, które mogą mieć poważne konsekwencje biznesowe. Nawet jeśli wiadomość zostanie trwale usunięta, może ona zostać zachowana przez czas nieokreślony, ponieważ w skrzynce pocztowej została umieszczona blokada prawna. Ten scenariusz jest znany jako *wyciek danych,* ponieważ dane zostały przypadkowo *rozlane* na Office 365. W takich sytuacjach można usunąć elementy w folderze Elementy do odzyskania użytkownika dla Exchange Online skrzynki pocztowej, nawet jeśli ta skrzynka pocztowa jest wstrzymana z jedną z różnych funkcji blokady w Office 365. Te typy blokad obejmują blokady sporów, blokady In-Place, blokady zbierania elektronicznych materiałów dowodowych i zasady przechowywania utworzone w centrum zabezpieczeń i zgodności w Office 365 lub Microsoft 365.

W tym artykule wyjaśniono, jak administratorzy mogą usuwać elementy z folderu Elementy do odzyskania dla przechowywanych w chmurze skrzynek pocztowych. Ta procedura obejmuje wyłączenie dostępu do skrzynki pocztowej i wyłączenie odzyskiwania pojedynczego elementu, wyłączenie asystenta folderu zarządzanego z przetwarzania skrzynki pocztowej, tymczasowe usunięcie blokady, usunięcie elementów z folderu Elementy możliwe do odzyskania, a następnie przywrócenie skrzynki pocztowej do poprzedniej konfiguracji. Oto proces:
  
[Krok 1. Zbieranie informacji o skrzynce pocztowej](#step-1-collect-information-about-the-mailbox)

[Krok 2. Przygotowanie skrzynki pocztowej](#step-2-prepare-the-mailbox)

[Krok 3. Usuwanie wszystkich blokad ze skrzynki pocztowej](#step-3-remove-all-holds-from-the-mailbox)

[Krok 4. Usuwanie blokady opóźnienia ze skrzynki pocztowej](#step-4-remove-the-delay-hold-from-the-mailbox)

[Krok 5. Usuwanie elementów w folderze Elementy możliwe do odzyskania](#step-5-delete-items-in-the-recoverable-items-folder)

[Krok 6. Przywrócenie poprzedniego stanu skrzynki pocztowej](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> Procedury opisane w tym artykule spowodują trwałe usunięcie danych (przeczyszczanie) ze skrzynki pocztowej Exchange Online. Oznacza to, że nie można odzyskać komunikatów usuniętych z folderu Elementy możliwe do odzyskania i nie będą dostępne do celów legalnego odnajdywania lub innych celów zgodności. Jeśli chcesz usunąć wiadomości ze skrzynki pocztowej, która została wstrzymana w ramach blokady postępowania sądowego, In-Place blokady, blokady zbierania elektronicznych materiałów dowodowych lub zasad przechowywania utworzonych w portalu zgodności usługi Microsoft Purview, przed usunięciem blokady skontaktuj się z działami zarządzania rekordami lub działami prawnymi. Organizacja może mieć zasady określające, czy skrzynka pocztowa jest wstrzymana, czy zdarzenie wycieku danych ma priorytet.
  
## <a name="before-you-delete-items"></a>Przed usunięciem elementów

- Aby utworzyć i uruchomić wyszukiwanie zawartości, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych lub mieć przypisaną rolę zarządzania wyszukiwaniem zgodności. Aby usunąć komunikaty, musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania wyszukiwaniem i przeczyszczaniem. Aby uzyskać informacje na temat dodawania użytkowników do grupy ról, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](./assign-ediscovery-permissions.md).

- Jeśli skrzynka pocztowa jest przypisana do zasad przechowywania w całej organizacji, przed usunięciem elementów z folderu Elementy możliwe do odzyskania należy wykluczyć skrzynkę pocztową z zasad. Synchronizowanie zmiany zasad i usunięcie skrzynki pocztowej z zasad może potrwać do 24 godzin. Aby uzyskać więcej informacji, zobacz "Zasady przechowywania w całej organizacji" w sekcji [Usuwanie wszystkich blokad ze skrzynki pocztowej](#organization-wide-retention-policies) w tym artykule.

- Nie można wykonać tej procedury dla skrzynki pocztowej, która została przypisana do ustawień przechowywania z zasadami przechowywania zablokowanymi przy użyciu blokady zachowania. Dzieje się tak, ponieważ ta blokada uniemożliwia usunięcie lub wykluczenie skrzynki pocztowej z zasad oraz wyłączenie asystenta folderów zarządzanych w skrzynce pocztowej. Aby uzyskać więcej informacji na temat zasad blokowania na potrzeby przechowywania, zobacz [Używanie blokady zachowania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania](retention-preservation-lock.md).

- Procedura opisana w tym artykule nie jest obsługiwana w przypadku nieaktywnych skrzynek pocztowych. Dzieje się tak, ponieważ nie można ponownie zastosować blokady (lub zasad przechowywania) do nieaktywnej skrzynki pocztowej po jej usunięciu. Po usunięciu blokady z nieaktywnej skrzynki pocztowej zostanie ona zmieniona na normalną nietrwałą skrzynkę pocztową i zostanie trwale usunięta z organizacji po przetworzeniu jej przez Asystenta folderów zarządzanych.

- Jeśli skrzynka pocztowa nie jest wstrzymana (lub nie ma włączonego odzyskiwania pojedynczego elementu), możesz usunąć elementy z folderu Elementy możliwe do odzyskania. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail w organizacji](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>Krok 1. Zbieranie informacji o skrzynce pocztowej

Pierwszym krokiem jest zebranie wybranych właściwości z docelowej skrzynki pocztowej, która będzie miała wpływ na tę procedurę. Pamiętaj, aby zapisać te ustawienia lub zapisać je w pliku tekstowym, ponieważ niektóre z tych właściwości zostaną zmienione, a następnie przywrócisz oryginalne wartości w kroku 6 po usunięciu elementów z folderu Elementy możliwe do odzyskania. Oto lista właściwości skrzynki pocztowej, które należy zebrać.
  
- *SingleItemRecoveryEnabled*  i  *RetainDeletedItemsFor*. W razie potrzeby wyłączysz pojedyncze odzyskiwanie i zwiększ okres przechowywania usuniętych elementów w kroku 3.

- *LitigationHoldEnabled*  i  *InPlaceHolds*. Musisz zidentyfikować wszystkie blokady umieszczone w skrzynce pocztowej, aby można było je tymczasowo usunąć w kroku 3. Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać wskazówki dotyczące identyfikowania blokady typów, która może zostać umieszczona w skrzynce pocztowej.

Ponadto należy uzyskać ustawienia dostępu klienta skrzynki pocztowej, aby można było je tymczasowo wyłączyć, aby właściciel (lub inni użytkownicy) nie mogli uzyskać dostępu do skrzynki pocztowej podczas tej procedury. Na koniec możesz uzyskać bieżący rozmiar i liczbę elementów w folderze Elementy do odzyskania. Po usunięciu elementów w folderze Elementy możliwe do odzyskania w kroku 5 użyjesz tych informacji, aby sprawdzić, czy elementy zostały usunięte.
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pamiętaj, aby użyć nazwy użytkownika i hasła dla konta administratora, do którego przypisano odpowiednie role zarządzania w Exchange Online.

2. Uruchom następujące polecenie, aby uzyskać informacje o odzyskiwaniu pojedynczego elementu i okresie przechowywania usuniętego elementu.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Jeśli odzyskiwanie pojedynczego elementu jest włączone, musisz go wyłączyć w kroku 2. Jeśli okres przechowywania usuniętego elementu nie jest ustawiony na 30 dni (maksymalna wartość w Exchange Online), możesz go zwiększyć w kroku 2.

3. Uruchom następujące polecenie, aby uzyskać ustawienia dostępu do skrzynki pocztowej dla skrzynki pocztowej.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   Wszystkie te metody dostępu zostaną wyłączone w kroku 2.

4. Uruchom następujące polecenie, aby uzyskać informacje o zasadach przechowywania i przechowywania stosowanych do skrzynki pocztowej.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > Jeśli we właściwości  *InPlaceHolds*  jest zbyt wiele wartości, a nie wszystkie są wyświetlane, możesz uruchomić  `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` polecenie , aby wyświetlić każdą wartość w osobnym wierszu.
  
5. Uruchom następujące polecenie, aby uzyskać informacje o zasadach przechowywania w całej organizacji. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Jeśli Twoja organizacja ma jakiekolwiek zasady przechowywania w całej organizacji, musisz wykluczyć skrzynkę pocztową z tych zasad w kroku 3. Replikowanie zmiany może potrwać do 24 godzin.

    > [!TIP]
    > Jeśli we właściwości  *InPlaceHolds*  jest zbyt wiele wartości, a nie wszystkie są wyświetlane, możesz uruchomić  `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` polecenie , aby wyświetlić każdą wartość w osobnym wierszu. 
  
6. Uruchom następujące polecenie, aby ustalić, czy do skrzynki pocztowej zastosowano blokadę opóźnienia.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   Jeśli wartość właściwości *DelayHoldApplied* lub *DelayReleaseHoldApplied jest ustawiona* na **wartość True**, do skrzynki pocztowej jest stosowane wstrzymanie opóźnienia i należy je usunąć. Aby uzyskać więcej informacji na temat blokad opóźnień, zobacz [Krok 4: Usuwanie blokady opóźnienia ze skrzynki pocztowej](#step-4-remove-the-delay-hold-from-the-mailbox).

   Jeśli wartość dowolnej właściwości jest ustawiona na **wartość False**, do skrzynki pocztowej nie jest stosowane blokada opóźnienia i możesz pominąć krok 4.

7. Uruchom następujące polecenie, aby uzyskać bieżący rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy możliwe do odzyskania w podstawowej skrzynce pocztowej użytkownika.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Jeśli skrzynka pocztowa archiwum użytkownika jest włączona, uruchom następujące polecenie, aby uzyskać rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy możliwe do odzyskania w skrzynce pocztowej archiwum. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Po usunięciu elementów w kroku 5 można usunąć lub nie usuwać elementów w folderze Elementy możliwe do odzyskania w podstawowej skrzynce pocztowej archiwum użytkownika. Jeśli automatyczne rozszerzanie archiwizacji jest włączone dla skrzynki pocztowej, elementy w pomocniczej skrzynce pocztowej archiwum nie zostaną usunięte.
  
## <a name="step-2-prepare-the-mailbox"></a>Krok 2. Przygotowanie skrzynki pocztowej

Po zebraniu i zapisaniu informacji o skrzynce pocztowej następnym krokiem jest przygotowanie skrzynki pocztowej przez wykonanie następujących zadań:
  
- **Wyłącz dostęp klienta do skrzynki pocztowej, aby** właściciel skrzynki pocztowej nie mógł uzyskać dostępu do swojej skrzynki pocztowej i wprowadzić żadnych zmian w danych skrzynki pocztowej podczas tej procedury.

- **Zwiększ okres przechowywania usuniętych elementów** do 30 dni (maksymalna wartość w Exchange Online), aby nie usuwać elementów z folderu Elementy możliwe do odzyskania przed usunięciem ich w kroku 5.

- **Wyłącz odzyskiwanie pojedynczego elementu** , aby elementy nie były zachowywane (na czas trwania okresu przechowywania usuniętego elementu) po usunięciu ich z folderu Elementy możliwe do odzyskania w kroku 5.

- **Wyłącz Asystenta folderów zarządzanych** , aby nie przetwarzał skrzynki pocztowej i nie zachował elementów usuniętych w kroku 5.

Wykonaj następujące kroki w programie Exchange Online programu PowerShell.
  
1. Uruchom następujące polecenie, aby wyłączyć cały dostęp klienta do skrzynki pocztowej. W składni polecenia przyjęto założenie, że wszystkie metody dostępu klienta zostały włączone w skrzynce pocztowej.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > Wyłączenie wszystkich metod dostępu klienta do skrzynki pocztowej może potrwać do 60 minut. Należy pamiętać, że wyłączenie tych metod dostępu nie spowoduje rozłączenia właściciela skrzynki pocztowej, jeśli są one obecnie zalogowane. Jeśli właściciel nie jest zalogowany, nie będzie mógł uzyskać dostępu do swojej skrzynki pocztowej po wyłączeniu tych metod dostępu.
  
2. Uruchom następujące polecenie, aby zwiększyć okres przechowywania usuniętego elementu maksymalnie o 30 dni. Przyjęto założenie, że bieżące ustawienie jest mniejsze niż 30 dni.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Uruchom następujące polecenie, aby wyłączyć odzyskiwanie pojedynczego elementu.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > Wyłączenie odzyskiwania pojedynczego elementu może potrwać do 240 minut. Nie usuwaj elementów w folderze Elementy możliwe do odzyskania, dopóki ten okres nie upłynął.
  
4. Uruchom następujące polecenie, aby uniemożliwić asystentowi folderów zarządzanych przetwarzanie skrzynki pocztowej. Jak wyjaśniono wcześniej, asystenta folderów zarządzanych można wyłączyć tylko wtedy, gdy zasady przechowywania z blokadą zachowania nie zostaną zastosowane do skrzynki pocztowej.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>Krok 3. Usuwanie wszystkich blokad ze skrzynki pocztowej

Ostatnim krokiem przed usunięciem elementów z folderu Elementy do odzyskania jest usunięcie wszystkich blokad (zidentyfikowanych w kroku 1) umieszczonych w skrzynce pocztowej. Wszystkie blokady muszą zostać usunięte, aby elementy nie były zachowywane po usunięciu ich z folderu Elementy możliwe do odzyskania. Poniższe sekcje zawierają informacje o usuwaniu różnych typów blokad w skrzynce pocztowej. Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać wskazówki dotyczące identyfikowania blokady typów, która może zostać umieszczona w skrzynce pocztowej. Aby uzyskać więcej informacji, zobacz [How to identify the type of hold placed on an Exchange Online mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md)).
  
> [!CAUTION]
> Jak wspomniano wcześniej, przed usunięciem blokady ze skrzynki pocztowej skontaktuj się z działami zarządzania rekordami lub działami prawnymi.
  
### <a name="litigation-hold"></a>Wstrzymanie postępowania sądowego
  
Uruchom następujące polecenie w programie Exchange Online Programu PowerShell, aby usunąć blokadę postępowania sądowego ze skrzynki pocztowej.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> Podobnie jak w przypadku wyłączania odzyskiwania pojedynczego elementu usunięcie blokady postępowania sądowego może potrwać do 240 minut. Nie usuwaj elementów z folderu Elementy możliwe do odzyskania, dopóki ten okres nie upłynął.
  
### <a name="in-place-hold"></a>blokada In-Place
  
Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby zidentyfikować In-Place Blokada umieszczoną w skrzynce pocztowej. Użyj identyfikatora GUID dla In-Place Hold, który został zidentyfikowany w kroku 1.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Po zidentyfikowaniu blokady In-Place można usunąć skrzynkę pocztową z blokady za pomocą <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange (EAC)</a> lub Exchange Online programu PowerShell. Aby uzyskać więcej informacji, zobacz [Tworzenie lub usuwanie blokady In-Place](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Zasady przechowywania stosowane do określonych skrzynek pocztowych
  
Uruchom następujące polecenie w programie [PowerShell Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell) , aby zidentyfikować zasady przechowywania stosowane do skrzynki pocztowej. To polecenie zwróci również wszelkie zasady przechowywania konwersacji Teams stosowane do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu `mbx` lub `skp` ) dla zasad przechowywania zidentyfikowanych w kroku 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Po zidentyfikowaniu zasad przechowywania przejdź do strony **Zarządzanie** >  **informacjamiRetention** w portalu zgodności, edytuj zasady przechowywania zidentyfikowane w poprzednim kroku i usuń skrzynkę pocztową z listy adresatów uwzględnionych w zasadach przechowywania.
  
### <a name="organization-wide-retention-policies"></a>Zasady przechowywania w całej organizacji
  
Zasady przechowywania dla całej organizacji, Exchange i Teams są stosowane do każdej skrzynki pocztowej w organizacji. Są one stosowane na poziomie organizacji (nie na poziomie skrzynki pocztowej) i są zwracane po uruchomieniu polecenia cmdlet **Get-OrganizationConfig** w kroku 1. Uruchom następujące polecenie w programie [PowerShell Security & Compliance Center](/powershell/exchange/exchange-online-powershell) , aby zidentyfikować zasady przechowywania w całej organizacji. Użyj identyfikatora GUID (bez prefiksu  `mbx` ) dla zasad przechowywania dla całej organizacji, które zostały zidentyfikowane w kroku 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Po zidentyfikowaniu zasad przechowywania w całej organizacji przejdź do strony **Zarządzanie** >  **informacjamiRetention** w portalu zgodności, edytuj wszystkie zasady przechowywania w całej organizacji zidentyfikowane w poprzednim kroku i dodaj skrzynkę pocztową do listy wykluczonych adresatów. Spowoduje to usunięcie skrzynki pocztowej użytkownika z zasad przechowywania.

> [!IMPORTANT]
> Po wykluczeniu skrzynki pocztowej z zasad przechowywania w całej organizacji synchronizacja tej zmiany i usunięcie skrzynki pocztowej z zasad może potrwać do 24 godzin.

### <a name="retention-labels"></a>Etykiety przechowywania

Za każdym razem, gdy użytkownik stosuje etykietę skonfigurowaną do przechowywania zawartości lub przechowywania, a następnie usuwania zawartości do dowolnego folderu lub elementu w skrzynce pocztowej, właściwość *ComplianceTagHoldApplied* jest ustawiona na **wartość True**. W takim przypadku skrzynka pocztowa jest uznawana za wstrzymaną, tak jakby została umieszczona w blokadzie postępowania sądowego lub przypisana do zasad przechowywania.

Aby wyświetlić wartość właściwości *ComplianceTagHoldApplied*, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Po zidentyfikowaniu, że skrzynka pocztowa jest wstrzymana, ponieważ etykieta przechowywania jest stosowana do folderu lub elementu, możesz użyć narzędzia do wyszukiwania zawartości w portalu zgodności, aby wyszukać elementy oznaczone etykietami przy użyciu warunku **etykiety Przechowywania** . Więcej informacji można znaleźć w następujących artykułach:

- Sekcja "Używanie wyszukiwania zawartości do znajdowania całej zawartości z określoną etykietą przechowywania" w temacie [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)

- Sekcja "Warunki wyszukiwania" w [zapytaniach słów kluczowych i warunkach wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md#conditions-for-common-properties).

Aby uzyskać więcej informacji na temat etykiet, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

### <a name="ediscovery-holds"></a>Blokady zbierania elektronicznych materiałów dowodowych
  
Uruchom następujące polecenia w programie [PowerShell Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell) , aby zidentyfikować blokadę skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych (o nazwie *eDiscovery holds*), która jest stosowana do skrzynki pocztowej. Użyj identyfikatora GUID (bez prefiksu  `UniH` ) dla blokady zbierania elektronicznych materiałów dowodowych, która została zidentyfikowana w kroku 1. Drugie polecenie wyświetla nazwę przypadku zbierania elektronicznych materiałów dowodowych, z którego jest skojarzona blokada; w trzecim poleceniu jest wyświetlana nazwa blokady.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

Po zidentyfikowaniu nazwy sprawy zbierania elektronicznych materiałów dowodowych i blokady przejdź do strony **eDiscovery** \> **eDiscovery** w centrum zgodności, otwórz sprawę i usuń skrzynkę pocztową z blokady. Aby uzyskać więcej informacji na temat identyfikowania blokad zbierania elektronicznych materiałów dowodowych, zobacz sekcję "Blokady zbierania elektronicznych materiałów dowodowych" w temacie [How to identify the type of hold placed on an Exchange Online mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds)).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>Krok 4. Usuwanie blokady opóźnienia ze skrzynki pocztowej

Po usunięciu dowolnego typu blokady ze skrzynki pocztowej wartość właściwości *DelayHoldApplied* lub *DelayReleaseHoldApplied jest ustawiona* na **wartość True**. Dzieje się tak przy następnym procesie, gdy Asystent folderów zarządzanych przetworzy skrzynkę pocztową i wykryje, że blokada została usunięta. Jest to nazywane *wstrzymaniem opóźnienia* i oznacza, że rzeczywiste usunięcie blokady jest opóźnione o 30 dni, aby zapobiec trwałemu usunięciu danych ze skrzynki pocztowej. (Celem blokady opóźnienia jest zapewnienie administratorom możliwości wyszukiwania lub odzyskiwania elementów skrzynki pocztowej, które zostaną usunięte po usunięciu blokady).  Po umieszczeniu blokady opóźnienia na skrzynce pocztowej skrzynka pocztowa jest nadal uważana za wstrzymaną przez nieograniczony czas, tak jakby skrzynka pocztowa znajdowała się w blokadzie postępowania sądowego. Po upływie 30 dni wstrzymanie opóźnienia wygaśnie, a Microsoft 365 automatycznie spróbuje usunąć blokadę opóźnienia (ustawiając właściwość *DelayHoldApplied* lub *DelayReleaseHoldApplied* na **wartość False**), aby blokada została usunięta. Aby uzyskać więcej informacji na temat blokady opóźnienia, zobacz sekcję "Zarządzanie skrzynkami pocztowymi z opóźnieniem" w temacie [How to identify the type of hold placed on an Exchange Online mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold)).

Jeśli wartość właściwości *DelayHoldApplied* lub *DelayReleaseHoldApplied* ma wartość **True**, uruchom jedno z następujących poleceń, aby usunąć blokadę opóźnienia:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Lub

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Musisz mieć przypisaną rolę Archiwum prawne w Exchange Online, aby użyć parametru *RemoveDelayHoldApplied* lub *RemoveDelayReleaseHoldApplied*.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>Krok 5. Usuwanie elementów w folderze Elementy możliwe do odzyskania

Teraz możesz przystąpić do faktycznego usuwania elementów w folderze Elementy do odzyskania przy użyciu poleceń cmdlet [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) i [New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) w programie PowerShell Security & Compliance Center.

Aby wyszukać elementy znajdujące się w folderze Elementy możliwe do odzyskania, zalecamy wykonanie *kolekcji docelowej*. Oznacza to, że zakres wyszukiwania można zawęzić tylko do elementów znajdujących się w folderze Elementy możliwe do odzyskania. Możesz to zrobić, uruchamiając skrypt w artykule [Use Content Search for targeted collections (Używanie wyszukiwania zawartości dla kolekcji docelowych](use-content-search-for-targeted-collections.md) ). Ten skrypt zwraca wartość właściwości identyfikatora folderu dla wszystkich podfolderów w docelowym folderze Elementy możliwe do odzyskania. Następnie użyjesz identyfikatora folderu w zapytaniu wyszukiwania, aby zwrócić elementy znajdujące się w tym folderze.

Oto omówienie procesu wyszukiwania i usuwania elementów w folderze Elementy możliwe do odzyskania użytkownika:

1. Uruchom skrypt kolekcji docelowej, który zwraca identyfikatory folderów dla wszystkich folderów w skrzynce pocztowej użytkownika docelowego. Skrypt nawiązuje połączenie z programem Exchange Online programu PowerShell i programem PowerShell & Zgodności zabezpieczeń w tej samej sesji programu PowerShell. Aby uzyskać więcej informacji, zobacz [Uruchamianie skryptu w celu uzyskania listy folderów dla skrzynki pocztowej](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Skopiuj identyfikatory folderów dla wszystkich podfolderów w folderze Elementy możliwe do odzyskania. Alternatywnie można przekierować dane wyjściowe skryptu do pliku tekstowego.

   Oto lista i opis podfolderów w folderze Elementy możliwe do odzyskania, z których można wyszukiwać i usuwać elementy:

   - **Usunięcia**: zawiera nietrwale usunięte elementy, których okres przechowywania usuniętych elementów nie wygasł. Użytkownicy mogą odzyskać elementy usunięte nietrwale z tego podfolderu przy użyciu narzędzia Odzyskaj usunięte elementy w Outlook.

   - **DiscoveryHolds**: zawiera mocno usunięte elementy, które zostały zachowane przez blokadę zbierania elektronicznych materiałów dowodowych lub zasady przechowywania. Ten podfolder nie jest widoczny dla użytkowników końcowych.

   - **SubstrateHolds**: zawiera usunięte elementy z Teams i innych aplikacji opartych na chmurze, które zostały zachowane przez zasady przechowywania lub inny typ blokady. Ten podfolder nie jest widoczny dla użytkowników końcowych.

3. Użyj polecenia cmdlet **New-ComplianceSearch** (w programie PowerShell Security & Compliance Center) lub użyj narzędzia wyszukiwania zawartości w centrum zgodności, aby utworzyć wyszukiwanie zawartości, które zwraca elementy z folderu Elementy możliwe do odzyskania użytkownika docelowego. Można to zrobić, dołączając identyfikator FolderId w zapytaniu wyszukiwania dla wszystkich podfolderów, które chcesz wyszukać. Na przykład następujące zapytanie zwraca wszystkie komunikaty w podfolderach Deletions i eDiscoveryHolds:

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Aby uzyskać więcej informacji i przykładów dotyczących uruchamiania wyszukiwań zawartości korzystających z właściwości identyfikatora folderu, zobacz [Używanie identyfikatora folderu lub wykonywanie kolekcji docelowej](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Jeśli używasz polecenia cmdlet **New-ComplianceSearch** do przeszukiwania folderu Elementy możliwe do odzyskania, użyj polecenia cmdlet **Start-ComplianceSearch** , aby uruchomić wyszukiwanie.

4. Po utworzeniu wyszukiwania zawartości i sprawdzeniu, czy zwraca ono elementy, które chcesz usunąć, użyj `New-ComplianceSearchAction -Purge -PurgeType HardDelete` polecenia (w programie PowerShell Security & Compliance Center), aby trwale usunąć elementy zwrócone przez wyszukiwanie zawartości utworzone w poprzednim kroku. Na przykład można uruchomić polecenie podobne do następującego polecenia:

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Po uruchomieniu poprzedniego polecenia zostanie usuniętych maksymalnie 10 elementów na skrzynkę pocztową. Oznacza to, że może być konieczne wielokrotne uruchomienie `New-ComplianceSearchAction -Purge` polecenia, aby usunąć wszystkie elementy, które chcesz usunąć w folderze Elementy możliwe do odzyskania. Aby usunąć dodatkowe elementy, należy najpierw usunąć poprzednią akcję przeczyszczania wyszukiwania zgodności. Można to zrobić, uruchamiając `Remove-ComplianceSearchAction` polecenie cmdlet. Aby na przykład usunąć akcję przeczyszczania, która została uruchomiona w poprzednim kroku, uruchom następujące polecenie:

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Po wykonaniu tej czynności możesz utworzyć nową akcję przeczyszczania w celu usunięcia większej liczby elementów. Przed utworzeniem nowej akcji przeczyszczania musisz usunąć każdą akcję przeczyszczania.

   Aby uzyskać listę akcji wyszukiwania zgodności, można uruchomić `Get-ComplianceSearchAction` polecenie cmdlet. Akcje przeczyszczania są identyfikowane przez `_Purge` dołączenie do nazwy wyszukiwania.

### <a name="verify-that-items-were-deleted"></a>Sprawdź, czy elementy zostały usunięte

Aby sprawdzić, czy elementy z folderu Elementy możliwe do odzyskania zostały pomyślnie usunięte ze skrzynki pocztowej, użyj polecenia cmdlet **Get-MailboxFolderStatistics** w programie Exchange Online programu PowerShell, aby sprawdzić rozmiar i liczbę elementów w folderze Elementy do odzyskania. Możesz porównać te statystyki z tymi, które zostały zebrane w kroku 1.
  
Uruchom następujące polecenie w programie , aby uzyskać bieżący rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy możliwe do odzyskania w podstawowej skrzynce pocztowej użytkownika.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Uruchom następujące polecenie, aby uzyskać rozmiar i łączną liczbę elementów w folderach i podfolderach w folderze Elementy możliwe do odzyskania w skrzynce pocztowej archiwum użytkownika.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>Krok 6. Przywrócenie poprzedniego stanu skrzynki pocztowej

Ostatnim krokiem jest przywrócenie poprzedniej konfiguracji skrzynki pocztowej. Oznacza to zresetowanie właściwości zmienionych w kroku 2 i ponowne zastosowane blokady usunięte w kroku 3. Obejmuje to:
  
- Zmiana okresu przechowywania usuniętego elementu z powrotem na poprzednią wartość. Alternatywnie możesz pozostawić ten zestaw na 30 dni, czyli maksymalną wartość w Exchange Online.

- Ponowne włączanie odzyskiwania pojedynczego elementu.

- Ponowne włączenie metod dostępu klienta, aby właściciel mógł uzyskać dostęp do swojej skrzynki pocztowej.

- Ponowne aplikowanie usuniętych zasad przechowywania i przechowywania.

- Ponowne włączenie asystenta folderów zarządzanych w celu przetworzenia skrzynki pocztowej.

> [!IMPORTANT]
> Zalecamy odczekanie 24 godzin od ponownego zastosowania zasad przechowywania lub przechowywania (i sprawdzenie, czy zostały one wprowadzone) przed ponownym włączeniem asystenta folderów zarządzanych w celu przetworzenia skrzynki pocztowej.
  
Wykonaj następujące kroki (w określonej sekwencji) w programie Exchange Online programu PowerShell.
  
1. Uruchom następujące polecenie, aby zmienić okres przechowywania usuniętego elementu z powrotem na jego oryginalną wartość. Zakłada to, że poprzednie ustawienie jest mniejsze niż 30 dni; na przykład 14 dni.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Uruchom następujące polecenie, aby ponownie włączyć odzyskiwanie pojedynczego elementu.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Uruchom następujące polecenie, aby ponownie włączyć wszystkie metody dostępu klienta do skrzynki pocztowej.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. Ponownie zastosować blokady usunięte w kroku 3. W zależności od typu blokady użyj jednej z poniższych procedur.

    **Wstrzymanie postępowania sądowego**

    Uruchom następujące polecenie, aby ponownie włączyć blokadę postępowania sądowego dla skrzynki pocztowej.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **Blokada miejscowa**

    Użyj eac (lub Exchange Online programu PowerShell), aby dodać skrzynkę pocztową z powrotem do In-Place Hold.

    **Zasady przechowywania stosowane do określonych skrzynek pocztowych**

    Użyj portalu zgodności, aby dodać skrzynkę pocztową z powrotem do zasad przechowywania. Przejdź do strony **Zarządzanie** >  **informacjamiRetention** w centrum zgodności, edytuj zasady przechowywania i dodaj skrzynkę pocztową z powrotem do listy adresatów, do których są stosowane zasady przechowywania.

    **Zasady przechowywania w całej organizacji**

    Jeśli usunięto zasady przechowywania w całej organizacji lub w całej Exchange, wykluczając je z zasad, użyj portalu zgodności, aby usunąć skrzynkę pocztową z listy wykluczonych użytkowników. Przejdź do strony **Zarządzanie** >  **informacjamiRetention** w centrum zgodności, edytuj zasady przechowywania w całej organizacji i usuń skrzynkę pocztową z listy wykluczonych adresatów. Spowoduje to ponowne zastosowanie zasad przechowywania do skrzynki pocztowej użytkownika.

    **Sprawa zbierania elektronicznych materiałów dowodowych jest przechowywana**

    Użyj portalu zgodności, aby dodać skrzynkę pocztową z powrotem do blokady skojarzonej ze sprawą zbierania elektronicznych materiałów dowodowych. Przejdź do strony **eDiscoveryCore** > , otwórz sprawę i dodaj skrzynkę pocztową z powrotem do blokady. 

5. Uruchom następujące polecenie, aby umożliwić asystentowi folderów zarządzanych ponowne przetworzenie skrzynki pocztowej. Zgodnie z wcześniejszymi instrukcjami zalecamy odczekanie 24 godzin od ponownego zastosowania zasad wstrzymania lub przechowywania (i sprawdzenie, czy zostały one wprowadzone) przed ponownym włączeniem Asystenta folderów zarządzanych.

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

Poniżej przedstawiono tabelę opisującą sposób identyfikowania różnych typów blokad na podstawie wartości we właściwości  *InPlaceHolds podczas uruchamiania*  poleceń cmdlet **Get-Mailbox** lub **Get-OrganizationConfig** . Aby uzyskać bardziej szczegółowe informacje, zobacz [How to identify the type of hold placed on an Exchange Online mailbox (Jak zidentyfikować typ blokady umieszczonej w Exchange Online skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md)).

Jak wyjaśniono wcześniej, przed pomyślnym usunięciem elementów w folderze Elementy możliwe do odzyskania należy usunąć wszystkie zasady przechowywania i przechowywania ze skrzynki pocztowej.
  
| Typ blokady | Przykładowa wartość | Jak zidentyfikować blokadę |
|:-----|:-----|:-----|
|Wstrzymanie postępowania sądowego  <br/> | `True` <br/> |*Właściwość LitigationHoldEnabled* jest ustawiona na `True`.  <br/> |
|blokada In-Place  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |Właściwość  *InPlaceHolds*  zawiera identyfikator GUID In-Place Hold umieszczony w skrzynce pocztowej. Możesz powiedzieć, że jest to In-Place Hold, ponieważ identyfikator GUID nie zaczyna się od prefiksu.  <br/> Możesz użyć polecenia w programie `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` Exchange Online Programu PowerShell, aby uzyskać informacje o In-Place Wstrzymaj w skrzynce pocztowej.  <br/> |
| Zasady przechowywania w portalu zgodności stosowane do określonych skrzynek pocztowych  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> lub  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |Po uruchomieniu polecenia cmdlet **Get-Mailbox** właściwość  *InPlaceHolds*  zawiera również identyfikatory GUID zasad przechowywania stosowane do skrzynki pocztowej. Można zidentyfikować zasady przechowywania, ponieważ identyfikator GUID rozpoczyna się od prefiksu  `mbx` . Jeśli identyfikator GUID zasad przechowywania rozpoczyna się od prefiksu`skp`, oznacza to, że zasady przechowywania są stosowane do Skype dla firm konwersacji.  <br/> Aby tożsamości zasad przechowywania, które są stosowane do skrzynki pocztowej, uruchom następujące polecenie w Security & Compliance Center PowerShell: <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Pamiętaj, aby usunąć  `mbx` prefiks lub  `skp` podczas uruchamiania tego polecenia.  <br/> |
|Zasady przechowywania w całej organizacji w portalu zgodności  <br/> |Brak wartości  <br/> lub  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (wskazuje, że skrzynka pocztowa jest wykluczona z zasad dla całej organizacji)  <br/> |Nawet jeśli właściwość  *InPlaceHolds jest pusta podczas uruchamiania*  polecenia cmdlet **Get-Mailbox** , do skrzynki pocztowej nadal mogą być stosowane co najmniej jedna zasady przechowywania w całej organizacji.  <br/> Aby to sprawdzić, możesz uruchomić `Get-OrganizationConfig | FL InPlaceHolds` polecenie w programie Exchange Online programie PowerShell, aby uzyskać listę identyfikatorów GUID dla zasad przechowywania w całej organizacji. Identyfikator GUID dla zasad przechowywania w całej organizacji stosowany do Exchange skrzynek pocztowych zaczyna się od prefiksu`mbx`, `mbxa3056bb15562480fadb46ce523ff7b02`na przykład .  <br/> Aby utworzyć tożsamość zasad przechowywania w całej organizacji, które są stosowane do skrzynki pocztowej, uruchom następujące polecenie w programie PowerShell Security & Compliance Center: <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Jeśli skrzynka pocztowa jest wykluczona z zasad przechowywania w całej organizacji, identyfikator GUID zasad przechowywania jest wyświetlany we właściwości  *InPlaceHolds*  skrzynki pocztowej użytkownika podczas uruchamiania polecenia cmdlet **Get-Mailbox** ; jest on identyfikowany przez prefiks  `-mbx`; na przykład  `-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|Blokada sprawy zbierania elektronicznych materiałów dowodowych w portalu zgodności  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |Właściwość  *InPlaceHolds*  zawiera również identyfikator GUID dowolnego blokady skojarzonego z przypadkiem zbierania elektronicznych materiałów dowodowych w portalu zgodności, który może zostać umieszczony w skrzynce pocztowej. Możesz powiedzieć, że jest to blokada sprawy zbierania elektronicznych materiałów dowodowych, ponieważ identyfikator GUID rozpoczyna się od prefiksu  `UniH` .  <br/> Możesz użyć  `Get-CaseHoldPolicy` polecenia cmdlet w programie PowerShell Security & Compliance Center, aby uzyskać informacje o przypadku zbierania elektronicznych materiałów dowodowych, z którą jest skojarzona blokada w skrzynce pocztowej. Na przykład możesz uruchomić polecenie  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` , aby wyświetlić nazwę blokady sprawy, która jest w skrzynce pocztowej. Pamiętaj, aby usunąć  `UniH` prefiks podczas uruchamiania tego polecenia.  <br/><br/> Aby tożsamość przypadku zbierania elektronicznych materiałów dowodowych, z którą jest skojarzona blokada skrzynki pocztowej, uruchom następujące polecenia:<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
