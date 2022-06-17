---
title: Używanie programu PowerShell do wykonywania migracji IMAP do platformy Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak za pomocą programu PowerShell przeprowadzić migrację protokołu IMAP (Internet Mail Access Protocol) do Microsoft 365.
ms.openlocfilehash: e3375af79ce4332ebf8f44e88181d7d8dc0e430f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128794"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Używanie programu PowerShell do wykonywania migracji IMAP do platformy Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W ramach procesu wdrażania Microsoft 365 można migrować zawartość skrzynek pocztowych użytkowników z usługi poczty e-mail protokołu IMAP (Internet Mail Access Protocol) do Microsoft 365. W tym artykule przedstawiono zadania migracji protokołu IMAP w wiadomości e-mail przy użyciu Exchange Online programu PowerShell.

> [!NOTE]
> Możesz również użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a>, aby przeprowadzić migrację IMAP. Zobacz [Migrowanie skrzynek pocztowych IMAP](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Szacowany czas wykonania tego zadania: 2–5 minut na utworzenie partii migracji. Po uruchomieniu partii migracji czas trwania migracji będzie się różnić w zależności od liczby skrzynek pocztowych w partii, rozmiaru każdej skrzynki pocztowej i dostępnej pojemności sieciowej. Aby uzyskać informacje o innych czynnikach wpływających na czas migrowania skrzynek pocztowych do Microsoft 365, zobacz [Wydajność migracji](/Exchange/mailbox-migration/office-365-migration-best-practices).

Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis "Migracja" w tabeli w [temacie Uprawnienia adresatów](/exchange/recipients-permissions-exchange-2013-help) .

Aby użyć poleceń cmdlet programu PowerShell Exchange Online, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie, aby Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

Migracje IMAP mają zastosowanie do następujących ograniczeń:

- Można migrować tylko elementy w skrzynce odbiorczej użytkownika lub w innych folderach poczty. Nie można migrować kontaktów, elementów kalendarza ani zadań.

- Z poziomu skrzynki pocztowej użytkownika można migrować maksymalnie 500 000 elementów.

- Maksymalny rozmiar komunikatu, który można zmigrować, wynosi 35 MB.

## <a name="migration-steps"></a>Kroki migracji

### <a name="step-1-prepare-for-an-imap-migration"></a>Krok 1. Przygotowanie do migracji IMAP
<a name="BK_Step1"> </a>

- **Jeśli masz domenę dla swojej organizacji IMAP, dodaj ją jako akceptowaną domenę organizacji Microsoft 365.** Jeśli chcesz użyć tej samej domeny, którą już posiadasz dla Microsoft 365 skrzynek pocztowych, musisz najpierw dodać ją jako akceptowaną domenę, aby Microsoft 365. Po dodaniu można utworzyć użytkowników w Microsoft 365. Aby uzyskać więcej informacji, zobacz[Weryfikowanie domeny](../admin/setup/add-domain.md).

- **Dodaj każdego użytkownika do Microsoft 365, aby miał skrzynkę pocztową.** Aby uzyskać instrukcje, zobacz[Dodawanie użytkowników do Microsoft 365 dla firm](../admin/add-users/add-users.md).

- **Uzyskaj nazwę FQDN serwera IMAP**. Musisz podać w pełni kwalifikowaną nazwę domeny (FQDN) (nazywaną również pełną nazwą komputera) serwera IMAP, z którego będą migrowane dane skrzynki pocztowej podczas tworzenia punktu końcowego migracji IMAP. Użyj klienta IMAP lub polecenia PING, aby sprawdzić, czy ta nazwa FQDN umożliwia komunikację z serwerem IMAP przez Internet.

- **Skonfiguruj zaporę tak, aby zezwalała na połączenia IMAP**. Może być konieczne otwarcie portów w zaporze organizacji hostującej serwer IMAP, aby ruch sieciowy pochodzący z centrum danych firmy Microsoft podczas migracji mógł wejść do organizacji hostującej serwer IMAP. Aby uzyskać listę adresów IP używanych przez centra danych firmy Microsoft, zobacz [Exchange Online adresów URL i zakresów adresów IP](./urls-and-ip-address-ranges.md).

- **Przypisz uprawnienia konta administratora do uzyskiwania dostępu do skrzynek pocztowych w organizacji IMAP**. Jeśli użyjesz poświadczeń administratora w pliku CSV, konto, z którego korzystasz, musi mieć uprawnienia niezbędne do uzyskania dostępu do wszystkich lokalnych skrzynek pocztowych. Uprawnienia wymagane do uzyskiwania dostępu do skrzynek pocztowych użytkowników są określane przez konkretny serwer IMAP.

- **Aby użyć Exchange Online poleceń cmdlet programu PowerShell**, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie, aby Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

    Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

- **Sprawdź, czy możesz nawiązać połączenie z serwerem IMAP**. Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby przetestować ustawienia połączenia z serwerem IMAP.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    W przypadku wartości parametru **Port** typowe jest użycie wartości 143 dla połączeń nieszyfrowanych lub TLS (Transport Layer Security) oraz użycie wartości 993 dla połączeń SSL.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Krok 2. Tworzenie pliku CSV dla partii migracji IMAP

Zidentyfikuj grupę użytkowników, których skrzynki pocztowe mają być migrowane w partii migracji IMAP. Każdy wiersz w pliku CSV zawiera informacje niezbędne do nawiązania połączenia ze skrzynką pocztową w systemie komunikatów IMAP.

Opisano tutaj wymagane atrybuty dla poszczególnych użytkowników:

- **EmailAddress** określa identyfikator użytkownika dla skrzynki pocztowej Microsoft 365 użytkownika.

- **UserName** określa nazwę logowania dla konta do użycia w celu uzyskania dostępu do skrzynki pocztowej na serwerze IMAP.

- **Hasło** określa hasło dla konta w kolumnie **UserName** .

Poniżej przedstawiono przykładowy format pliku CSV. W tym przykładzie migrowane są trzy skrzynki pocztowe:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

W przypadku atrybutu **UserName** oprócz nazwy użytkownika można użyć poświadczeń konta, do którego przypisano uprawnienia niezbędne do uzyskiwania dostępu do skrzynek pocztowych na serwerze IMAP, poniżej przedstawiono niektóre z określonych formatów używanych dla niektórych serwerów IMAP:

 **Microsoft Exchange:**

Jeśli poczta e-mail jest migrowana z implementacji serwera IMAP dla programu Microsoft Exchange, należy w pliku CSV użyć dla atrybutu **UserName** formatu **Domain/Admin_UserName/User_UserName**. Można na przykład założyć, że z programu Exchange migrowana jest poczta e-mail użytkowników Terry Adams, Ann Beebe i Paul Cannon. Masz konto administratora poczty, gdzie nazwa użytkownika to **mailadmin** , a hasło to **P\@ssw0rd**. Plik CSV będzie wyglądał następująco:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

W przypadku serwerów IMAP, które obsługują uwierzytelnianie proste i warstwę zabezpieczeń (SASL), takich jak serwer IMAP aplikacji Dovecot, użyj formatu **User_UserName*Admin_UserName**, gdzie gwiazdka ( * ) jest konfigurowalnym znakiem separatora. Załóżmy, że migrujesz wiadomości e-mail tych samych użytkowników z serwera IMAP aplikacji Dovecot przy użyciu poświadczeń **administratora mailadmin** i **P\@ssw0rd**. Plik CSV będzie wyglądał następująco:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

Jeśli migrujesz wiadomość e-mail z serwera komunikatów Mirapoint, użyj formatu **#user\@domain#Admin_UserName#** dla poświadczeń administratora. Aby przeprowadzić migrację wiadomości e-mail z programu Mirapoint przy użyciu poświadczeń **administratora mailadmin** i **P\@ssw0rd**, plik CSV będzie wyglądać następująco:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

Niektóre źródłowe systemy poczty e-mail, takie jak Courier IMAP, nie obsługują korzystania z poświadczeń administratora skrzynki pocztowej w celu migrowania skrzynek pocztowych do Microsoft 365. Możesz jednak skonfigurować źródłowy system poczty e-mail tak, aby korzystał z wirtualnych folderów udostępnionych. Korzystając z wirtualnych folderów udostępnionych, możesz użyć poświadczeń administratora skrzynki pocztowej, aby uzyskać dostęp do skrzynek pocztowych użytkowników w źródłowym systemie poczty e-mail. Aby uzyskać więcej informacji na temat sposobu konfigurowania wirtualnych folderów udostępnionych w systemie Courier IMAP, zobacz [Foldery udostępnione](https://go.microsoft.com/fwlink/p/?LinkId=398870).

Aby przeprowadzić migrację skrzynek pocztowych po skonfigurowaniu wirtualnych folderów udostępnionych w źródłowym systemie poczty e-mail, wprowadź w pliku migracji opcjonalny atrybut **UserRoot** (katalog główny). Ten atrybut określa lokalizację skrzynek pocztowych poszczególnych użytkowników w strukturze wirtualnych folderów udostępnionych w źródłowym systemie poczty e-mail. Na przykład ścieżka do skrzynki pocztowej Terry'ego to /users/terry.adams.

Poniżej przedstawiono przykładowy plik CSV zawierający atrybut **UserRoot**:

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Krok 3. Tworzenie punktu końcowego migracji IMAP

Aby pomyślnie przeprowadzić migrację poczty e-mail, Microsoft 365 musi nawiązać połączenie ze źródłowym systemem poczty e-mail i komunikować się z nimi. W tym celu Microsoft 365 używa punktu końcowego migracji. Punkt końcowy migracji definiuje również liczbę skrzynek pocztowych do jednoczesnej migracji oraz liczbę skrzynek pocztowych do jednoczesnej synchronizacji podczas synchronizacji przyrostowej, która występuje raz na 24 godziny. Aby utworzyć punkt końcowy migracji dla migracji IMAP, najpierw [połącz się z Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

Aby utworzyć punkt końcowy migracji IMAP o nazwie "IMAPEndpoint" w programie Exchange Online programu PowerShell, uruchom następujące polecenie:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Można również dodać parametry określające migracje współbieżne, współbieżne migracje przyrostowe i port do użycia. Następujące polecenie Exchange Online programu PowerShell tworzy punkt końcowy migracji IMAP o nazwie "IMAPEndpoint", który obsługuje 50 równoczesnych migracji i maksymalnie 25 współbieżnych synchronizacji przyrostowych. Konfiguruje również punkt końcowy do używania portu 143 na potrzeby szyfrowania TLS.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **New-MigrationEndpoint** , zobacz [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić informacje o "IMAPEndpoint":

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Krok 4. Tworzenie i uruchamianie partii migracji IMAP

Aby utworzyć partię migracji dla migracji IMAP, można użyć polecenia cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) . Możesz utworzyć partię migracji i uruchomić ją automatycznie, dołączając parametr _AutoStart_ . Alternatywnie możesz utworzyć partię migracji, a następnie uruchomić ją później za pomocą polecenia cmdlet[Start-MigrationBatch](/powershell/module/exchange/start-migrationbatch) .

Następujące polecenie Exchange Online programu PowerShell automatycznie uruchomi partię migracji o nazwie "IMAPBatch1" przy użyciu punktu końcowego IMAP o nazwie "IMAPEndpoint":

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Uruchom polecenie cmdlet [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) , aby wyświetlić informacje o "IMAPBatch1":

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Możesz również sprawdzić, czy partia została uruchomiona, uruchamiając następujące polecenie:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Krok 5. Kierowanie wiadomości e-mail do Microsoft 365

Systemy poczty e-mail ustalają lokalizację, do której należy dostarczać wiadomości e-mail, na podstawie rekordu DNS nazywanego rekordem MX. W trakcie procesu migracji poczty e-mail rekord MX wskazywał źródłowy system poczty e-mail. Po zakończeniu migracji wiadomości e-mail do Microsoft 365 nadszedł czas, aby wskazać rekord MX na Microsoft 365. Pomaga to upewnić się, że wiadomość e-mail jest dostarczana do skrzynek pocztowych Microsoft 365. Przenosząc rekord MX, możesz również wyłączyć stary system poczty e-mail, gdy wszystko będzie gotowe.

W przypadku wielu dostawców hostingu DNS dostępne są szczegółowe instrukcje dotyczące zmieniania rekordu MX. Jeśli Twojego dostawcy hostingu DNS nie ma na liście lub jeśli chcesz zapoznać się z ogólnymi wskazówkami, dostępne są również [ogólne instrukcje dotyczące rekordów MX](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide#add-an-mx-record-for-email-outlook-exchange-online).

Rozpoznanie zmienionego rekordu MX przez systemy poczty e-mail Twoich klientów i partnerów może potrwać do 72 godzin. Poczekaj co najmniej 72 godziny, zanim przejdziesz do następnego zadania: Krok 6. Usuwanie partii migracji IMAP.

### <a name="step-6-delete-imap-migration-batch"></a>Krok 6. Usuwanie partii migracji IMAP

Po zmianie rekordu MX i sprawdzeniu, czy wszystkie wiadomości e-mail są kierowane do Microsoft 365 skrzynek pocztowych, powiadom użytkowników, że ich poczta będzie Microsoft 365. Następnie możesz usunąć partię migracji IMAP. Przed usunięciem partii migracji sprawdź, czy są spełnione poniższe wymagania.

- Wszyscy użytkownicy używają Microsoft 365 skrzynek pocztowych. Po usunięciu partii poczta wysłana do skrzynek pocztowych w lokalnym Exchange Server nie jest kopiowana do odpowiednich Microsoft 365 skrzynek pocztowych.

- Microsoft 365 skrzynki pocztowe zostały zsynchronizowane co najmniej raz po rozpoczęciu wysyłania wiadomości e-mail bezpośrednio do nich. W tym celu upewnij się, że wartość w polu Czas ostatniej synchronizacji dla partii migracji jest nowsza niż wtedy, gdy poczta zaczęła być kierowana bezpośrednio do Microsoft 365 skrzynek pocztowych.

Aby usunąć partię migracji "IMAPBatch1" z programu Exchange Online programu PowerShell, uruchom następujące polecenie:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **Remove-MigrationBatch** , zobacz [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić informacje o "IMAPBatch1":

```powershell
Get-MigrationBatch IMAPBatch1"
```

Polecenie zwróci partię migracji ze stanem **Usuwanie** lub zwróci błąd informujący, że nie można odnaleźć partii migracji, sprawdzając, czy partia została usunięta.

Aby uzyskać więcej informacji na temat polecenia cmdlet **Get-MigrationBatch** , zobacz [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Zobacz też

[Narzędzie do rozwiązywania problemów z migracją IMAP](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)
