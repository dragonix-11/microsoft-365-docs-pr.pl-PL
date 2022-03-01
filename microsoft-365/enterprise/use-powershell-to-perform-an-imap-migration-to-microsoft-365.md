---
title: Przeprowadzanie migracji poczty IMAP do programu PowerShell w Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: Dowiedz się, jak za pomocą programu PowerShell przeprowadzić migrację protokołu IMAP (Internet Mail Access Protocol) w celu przeprowadzenia Microsoft 365.
ms.openlocfilehash: 0c546782e81a399f092c8c7878b52c419adee799
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017779"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Przeprowadzanie migracji poczty IMAP do programu PowerShell w Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W ramach procesu wdrażania programu Microsoft 365 możesz przeprowadzić migrację zawartości skrzynek pocztowych użytkowników z usługi poczty e-mail IMAP (Internet Mail Access Protocol) do programu Microsoft 365. Ten artykuł zawiera informacje o zadaniach związanych z migracją poczty e-mail IMAP przy użyciu programu Exchange Online PowerShell.

> [!NOTE]
> Migrację IMAP <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange również</a> wykonać za pomocą centrum administracyjnego. Zobacz [Migrowanie skrzynek pocztowych IMAP](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Szacowany czas wykonania tego zadania: 2–5 minut na utworzenie partii migracji. Po zakończeniu partii migracji czas trwania migracji zależy od liczby skrzynek pocztowych w partii, rozmiaru poszczególnych skrzynek pocztowych i dostępnej pojemności sieci. Aby uzyskać informacje o innych czynnikach, które wpływają na czas migracji skrzynek pocztowych do Microsoft 365, zobacz [Wydajność migracji](/Exchange/mailbox-migration/office-365-migration-best-practices).

Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby sprawdzić, jakich uprawnień potrzebujesz, zobacz wpis "Migracja" w tabeli w temacie [Uprawnienia adresatów](/exchange/recipients-permissions-exchange-2013-help) .

Aby używać poleceń cmdlet programu Exchange Online PowerShell, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell programu PowerShell. [Instrukcje Połączenie dotyczące Exchange Online pracy ze zdalnym programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

Migracje IMAP mają zastosowanie do następujących ograniczeń:

- Migrować można tylko elementy ze skrzynki odbiorczej lub innych folderów poczty użytkownika. Nie można migrować kontaktów, elementów kalendarza ani zadań.

- Ze skrzynki pocztowej użytkownika można migrować maksymalnie 500 000 elementów.

- Maksymalny rozmiar wiadomości, który można migrować, to 35 MB.

## <a name="migration-steps"></a>Kroki migracji

### <a name="step-1-prepare-for-an-imap-migration"></a>Krok 1. Przygotowywanie do migracji IMAP
<a name="BK_Step1"> </a>

- **Jeśli masz domenę dla swojej organizacji IMAP, dodaj ją jako zaakceptowaną domenę organizacji Microsoft 365 organizacji.** Jeśli chcesz używać tej samej domeny, która jest już posiadana dla swoich skrzynek pocztowych usługi Microsoft 365, musisz dodać ją jako zaakceptowaną domenę do usługi Microsoft 365. Po dodaniu użytkowników możesz je utworzyć w programie Microsoft 365. Aby uzyskać więcej informacji, [zobacz Uweryfikuj swoją domenę](../admin/setup/add-domain.md).

- **Dodaj każdego użytkownika do Microsoft 365, aby każdy miał skrzynkę pocztową.** Aby uzyskać instrukcje, [zobaczDaduj użytkowników do Microsoft 365 dla firm](../admin/add-users/add-users.md).

- **Uzyskaj fQDN serwera IMAP**. Należy podać w pełni kwalifikowaną nazwę domeny (FQDN) (nazywaną również pełną nazwą komputera) serwera IMAP, z których będą migrowane dane skrzynek pocztowych podczas tworzenia punktu końcowego migracji IMAP. Użyj klienta IMAP lub polecenia PING, aby sprawdzić, czy ta nazwa FQDN umożliwia komunikację z serwerem IMAP przez Internet.

- **Skonfiguruj zaporę, aby zezwalała na połączenia IMAP**. Może być konieczne otwarcie portów w zaporze organizacji hostującej serwer IMAP, aby ruch sieciowy pochodzący z centrum danych firmy Microsoft podczas migracji mógł wejść do organizacji hostującej serwer IMAP. Aby uzyskać listę adresów IP używanych przez centra danych firmy Microsoft, zobacz adresy URL Exchange Online [i zakresy adresów IP](./urls-and-ip-address-ranges.md).

- **Przypisz uprawnienia konta administratora do uzyskiwania dostępu do skrzynek pocztowych w organizacji IMAP**. Jeśli użyjesz poświadczeń administratora w pliku CSV, konto, z którego korzystasz, musi mieć uprawnienia niezbędne do uzyskania dostępu do wszystkich lokalnych skrzynek pocztowych. Uprawnienia wymagane do uzyskiwania dostępu do skrzynek pocztowych użytkowników są określane przez określony serwer IMAP.

- **Aby użyć poleceń cmdlet programu Exchange Online PowerShell**, musisz zalogować się i zaimportować te polecenia cmdlet do lokalnej sesji Windows PowerShell programu PowerShell. [Instrukcje Połączenie dotyczące Exchange Online pracy ze zdalnym programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

    Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

- **Sprawdź, czy możesz połączyć się z serwerem IMAP**. Uruchom następujące polecenie w programie Exchange Online PowerShell, aby przetestować ustawienia połączenia z serwerem IMAP.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    Dla wartości parametru **Port** typowe jest użycie wartości 143 dla połączeń nieszyfrowanych lub połączeń TLS (Transport Layer Security) oraz 993 dla połączeń SSL.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Krok 2. Tworzenie pliku CSV dla partii migracji IMAP

Zidentyfikuj grupę użytkowników, których skrzynki pocztowe mają zostać zmigrowane w partii migracji IMAP. Każdy wiersz w pliku CSV zawiera informacje niezbędne do nawiązania połączenia ze skrzynką pocztową w systemie obsługi wiadomości IMAP.

Opisano tutaj wymagane atrybuty dla poszczególnych użytkowników:

- **EmailAddress** określa identyfikator użytkownika dla skrzynki Microsoft 365 pocztowej.

- **UserName** — określa nazwę logowania dla konta, za pomocą których ma ono uzyskać dostęp do skrzynki pocztowej na serwerze IMAP.

- **Hasło** określa hasło dla konta w kolumnie **UserName** .

Poniżej przedstawiono przykładowy format pliku CSV. W tym przykładzie migrowane są trzy skrzynki pocztowe:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

Dla **atrybutu UserName** (Nazwa użytkownika) oprócz nazwy użytkownika możesz użyć poświadczeń konta, do których przypisano uprawnienia niezbędne do uzyskiwania dostępu do skrzynek pocztowych na serwerze IMAP, poniżej przedstawiono niektóre z konkretnych formatów używanych dla niektórych serwerów IMAP:

 **Microsoft Exchange:**

Jeśli poczta e-mail jest migrowana z implementacji serwera IMAP dla programu Microsoft Exchange, należy w pliku CSV użyć dla atrybutu **UserName** formatu **Domain/Admin_UserName/User_UserName**. Można na przykład założyć, że z programu Exchange migrowana jest poczta e-mail użytkowników Terry Adams, Ann Beebe i Paul Cannon. Masz konto administratora poczty e-mail, którego nazwa użytkownika to **mailadmin**, a hasło **ma nazwę Pssw0rd\@**. Plik CSV będzie wyglądał następująco:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

W przypadku serwerów IMAP, które obsługują interfejs SASL (Simple Authentication and Security Layer), takich jak serwer IMAP Dovecot, użyj formatu **User_UserName*Admin_UserName**, w którym gwiazdka ( * ) jest konfigurowalnym znakiem separatora. Załóżmy, że poczta e-mail tych samych użytkowników jest migrowa z serwera IMAP Dovecot przy użyciu poświadczeń administratora **mailadmin** i **Pssw0rd\@**. Plik CSV będzie wyglądał następująco:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

Jeśli migrujesz pocztę e-mail z serwera wiadomości Mirapoint, użyj dla poświadczeń **administratora formatu #user\@ domain#Admin_UserName** #. Aby przeprowadzić migrację poczty e-mail z serwera Mirapoint przy użyciu poświadczeń administratora **mailadmin** i **Pssw0rd\@**, plik CSV będzie wyglądał tak:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

Niektóre źródłowe systemy poczty e-mail, takie jak Courier IMAP, nie obsługują migracji skrzynek pocztowych do kont e-mail za pomocą poświadczeń administratora skrzynek pocztowych Microsoft 365. Możesz jednak skonfigurować źródłowy system poczty e-mail tak, aby korzystał z wirtualnych folderów udostępnionych. Za pomocą wirtualnych folderów udostępnionych można używać poświadczeń administratora skrzynek pocztowych w celu uzyskiwania dostępu do skrzynek pocztowych użytkowników w źródłowym systemie poczty e-mail. Aby uzyskać więcej informacji na temat sposobu konfigurowania wirtualnych folderów udostępnionych w systemie Courier IMAP, zobacz [Foldery udostępnione](https://go.microsoft.com/fwlink/p/?LinkId=398870).

Aby przeprowadzić migrację skrzynek pocztowych po skonfigurowaniu wirtualnych folderów udostępnionych w źródłowym systemie poczty e-mail, wprowadź w pliku migracji opcjonalny atrybut **UserRoot** (katalog główny). Ten atrybut określa lokalizację skrzynek pocztowych poszczególnych użytkowników w strukturze wirtualnych folderów udostępnionych w źródłowym systemie poczty e-mail. Na przykład ścieżka do skrzynki pocztowej Użytkownika Terry to /users/terry.adams.

Poniżej przedstawiono przykładowy plik CSV zawierający atrybut **UserRoot**:

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Krok 3. Tworzenie punktu końcowego migracji IMAP

Aby pomyślnie przeprowadzić migrację poczty e-mail, Microsoft 365 się ze źródłowym systemem poczty e-mail i komunikować się z nim. W tym celu program Microsoft 365 punkt końcowy migracji. Punkt końcowy migracji definiuje również liczbę skrzynek pocztowych do jednoczesnej migracji oraz liczbę skrzynek pocztowych do jednoczesnej synchronizacji podczas synchronizacji przyrostowej, która występuje raz na 24 godziny. Aby utworzyć punkt końcowy migracji IMAP[, najpierw połącz](/powershell/exchange/connect-to-exchange-online-powershell) się z Exchange Online.

Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

Aby utworzyć punkt końcowy migracji IMAP o nazwie "IMAPEndpoint" w programie Exchange Online PowerShell, uruchom następujące polecenie:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Możesz również dodać parametry, aby określić współbieżne migracje, równoczesne migracje przyrostowe i port do użycia. Poniższe Exchange Online programu PowerShell tworzy punkt końcowy migracji IMAP o nazwie "IMAPEndpoint", który obsługuje 50 współbieżnych migracji i maksymalnie 25 współbieżnych synchronizacji przyrostowych. Ponadto konfiguruje punkt końcowy do używania portu 143 do szyfrowania TLS.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **New-MigrationEndpoint** , [zobaczNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić informacje o programie "IMAPEndpoint":

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Krok 4. Tworzenie i uruchamianie partii migracji IMAP

Możesz użyć polecenia cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) , aby utworzyć partię migracji na użytek migracji IMAP. Partię migracji można utworzyć i uruchomić automatycznie, uwzględniając _parametr Autostart_ . Ewentualnie możesz utworzyć partię migracji, a następnie uruchomić ją później przy użyciu polecenia [cmdletStart-MigrationBatch](/powershell/module/exchange/start-migrationbatch) .

Następujące Exchange Online programu PowerShell automatycznie uruchamia partię migracji o nazwie "IMAPBatch1" przy użyciu punktu końcowego IMAP o nazwie "IMAPEndpoint":

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Uruchom polecenie [cmdlet Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) , aby wyświetlić informacje o "IMAPBatch1":

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Możesz również sprawdzić, czy partia została uruchomiona, uruchamiając następujące polecenie:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Krok 5. Rozsyłanie wiadomości e-mail do Microsoft 365

Systemy poczty e-mail ustalają lokalizację, do której należy dostarczać wiadomości e-mail, na podstawie rekordu DNS nazywanego rekordem MX. W trakcie procesu migracji poczty e-mail rekord MX wskazywał źródłowy system poczty e-mail. Po zakończeniu migracji poczty e-Microsoft 365 e-mail należy wskazać rekordowi MX, aby był Microsoft 365. Dzięki temu wiadomości e-mail będą na pewno dostarczane do twoich Microsoft 365 pocztowych. Przenosząc rekord MX, możesz również wyłączyć stary system poczty e-mail, gdy wszystko będzie już gotowe.

W przypadku wielu dostawców hostingu DNS dostępne są szczegółowe instrukcje dotyczące zmieniania rekordu MX. Jeśli Twojego dostawcy hostingu DNS nie ma na liście lub jeśli chcesz zapoznać się z ogólnymi wskazówkami, dostępne są również [ogólne instrukcje dotyczące rekordów MX](https://go.microsoft.com/fwlink/?LinkId=397449).

Rozpoznanie zmienionego rekordu MX przez systemy poczty e-mail Twoich klientów i partnerów może potrwać do 72 godzin. Przed rozpoczęciem kolejnego zadania poczekaj co najmniej 72 godziny: Krok 6. Usuwanie partii migracji IMAP.

### <a name="step-6-delete-imap-migration-batch"></a>Krok 6. Usuwanie partii migracji IMAP

Po zmianie rekordu MX i sprawdzeniu, czy wszystkie wiadomości e-mail są kierowane do Microsoft 365 pocztowych, powiadom użytkowników, że ich poczta trafia do Microsoft 365. Następnie możesz usunąć partię migracji IMAP. Przed usunięciem partii migracji sprawdź, czy są spełnione poniższe wymagania.

- Wszyscy użytkownicy Microsoft 365 skrzynki pocztowe. Po usunięciu partii poczta wysyłana do skrzynek pocztowych na lokalnym Exchange Server nie jest kopiowana do odpowiadających im Microsoft 365 pocztowych.

- Microsoft 365 zostały zsynchronizowane co najmniej raz po zakończeniu przesyłania poczty bezpośrednio do tych skrzynek. W tym celu upewnij się, że wartość w polu Godzina ostatniej synchronizacji w partii migracji jest najnowsza niż wartość, gdy poczta rozpoczyna się bezpośrednio do Microsoft 365 pocztowych.

Aby usunąć partię migracji "IMAPBatch1" z programu Exchange Online PowerShell, uruchom następujące polecenie:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **Remove-MigrationBatch** , [zobaczRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić informacje o "IMAPBatch1":

```powershell
Get-MigrationBatch IMAPBatch1"
```

Polecenie zwróci partię migracji ze stanem Usuwanie lub zwróci błąd informujący, że partii migracji nie można odnaleźć, co oznacza, że partia została usunięta.

Aby uzyskać więcej informacji na temat **polecenia cmdlet Get-MigrationBatch** , [zobaczGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Zobacz też

[Narzędzie do rozwiązywania problemów z migracją IMAP](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)