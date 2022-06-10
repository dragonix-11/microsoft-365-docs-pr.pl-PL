---
title: Używanie programu PowerShell do wykonywania migracji jednorazowej do platformy Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Dowiedz się, jak za pomocą programu PowerShell przenieść zawartość ze źródłowego systemu poczty e-mail jednocześnie, przeprowadzając migrację jednorazową do Microsoft 365.
ms.openlocfilehash: d63b7250cd1c4c34d169521943c3973104b15837
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008402"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Używanie programu PowerShell do wykonywania migracji jednorazowej do platformy Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Zawartość skrzynek pocztowych użytkowników można migrować ze źródłowego systemu poczty e-mail, aby Microsoft 365 wszystko jednocześnie przy użyciu migracji jednorazowej. W tym artykule przedstawiono zadania migracji jednorazowej poczty e-mail przy użyciu Exchange Online programu PowerShell.

Przeglądając temat [Co musisz wiedzieć o migracji e-mail jednorazowej do Microsoft 365](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration), możesz zapoznać się z omówieniem procesu migracji. Po zapoznaniu się z powyższym artykułem możesz rozpocząć migrację skrzynek pocztowych między systemami poczty e-mail, korzystając z przedstawionych tu instrukcji.

> [!NOTE]
> Możesz również użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a>, aby przeprowadzić migrację jednorazową. Zobacz [Przeprowadzanie migracji jednorazowej wiadomości e-mail do Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Szacowany czas wykonania tego zadania: 2–5 minut na utworzenie partii migracji. Po uruchomieniu partii migracji czas trwania migracji będzie się różnić w zależności od liczby skrzynek pocztowych w partii, rozmiaru każdej skrzynki pocztowej i dostępnej pojemności sieciowej. Aby uzyskać informacje o innych czynnikach wpływających na czas migrowania skrzynek pocztowych do Microsoft 365, zobacz [Wydajność migracji](/Exchange/mailbox-migration/office-365-migration-best-practices).

Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis "Migracja" w tabeli w [temacie Uprawnienia adresatów](/exchange/recipients-permissions-exchange-2013-help) .

Aby użyć poleceń cmdlet programu PowerShell Exchange Online, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie, aby Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

## <a name="migration-steps"></a>Kroki migracji

### <a name="step-1-prepare-for-a-cutover-migration"></a>Krok 1. Przygotowanie do migracji jednorazowej
<a name="BK_Step1"> </a>

- **Dodaj lokalną organizację Exchange jako akceptowaną domenę organizacji Microsoft 365.** Usługa migracji używa adresu SMTP lokalnych skrzynek pocztowych do utworzenia identyfikatora użytkownika i adresu e-mail usługi Microsoft Online Services dla nowych skrzynek pocztowych Microsoft 365. Migracja zakończy się niepowodzeniem, jeśli domena Exchange nie jest akceptowaną domeną ani domeną podstawową organizacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Weryfikowanie domeny](../admin/setup/add-domain.md).

- **Skonfiguruj Outlook Anywhere na lokalnym serwerze Exchange.** Usługa migracji poczty e-mail używa protokołu RPC za pośrednictwem protokołu HTTP lub Outlook Anywhere w celu nawiązania połączenia z lokalnym serwerem Exchange. Aby uzyskać informacje na temat konfigurowania Outlook Anywhere dla Exchange 2010 r., Exchange 2007 r. i Exchange 2003 r., zobacz następujące informacje:

  - [Exchange 2010: włączanie funkcji Outlook Anywhere](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: jak włączyć funkcję Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: Scenariusze wdrażania dla RPC za pośrednictwem protokołu HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [How to Configure Outlook Anywhere with Exchange 2003 (Jak skonfigurować Outlook Anywhere za pomocą programu Exchange 2003)](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > Konfiguracja Outlook Anywhere musi być skonfigurowana przy użyciu certyfikatu wystawionego przez zaufany urząd certyfikacji. Nie można go skonfigurować przy użyciu certyfikatu z podpisem własnym. Aby uzyskać więcej informacji, zobacz [How to Configure SSL for Outlook Anywhere (Jak skonfigurować protokół SSL dla Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80))).

- **Sprawdź, czy możesz nawiązać połączenie z organizacją Exchange przy użyciu Outlook Anywhere.** Wypróbuj jedną z tych metod, aby przetestować ustawienia połączenia:

  - Użyj usługi Microsoft Outlook spoza sieci firmowej, aby nawiązać połączenie z lokalną Exchange skrzynką pocztową.

  - Użyj [analizatora łączności zdalnej firmy Microsoft Exchange](https://www.testexchangeconnectivity.com/), aby przetestować ustawienia połączenia. Użyj funkcji Outlook Anywhere (RPC przez HTTP) lub testów wykrywania automatycznego w programie Outlook.

  - Uruchom następujące polecenia w programie Exchange Online programu PowerShell.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Przypisz lokalnemu kontu użytkownika uprawnienia niezbędne do uzyskiwania dostępu do skrzynek pocztowych w organizacji Exchange.** Lokalne konto użytkownika używane do nawiązywania połączenia z lokalną organizacją Exchange (nazywane również administratorem migracji) musi mieć uprawnienia niezbędne do uzyskiwania dostępu do lokalnych skrzynek pocztowych, które mają zostać zmigrowane do Microsoft 365. To konto użytkownika służy do tworzenia punktu końcowego migracji do organizacji lokalnej.

    Na poniższej liście przedstawiono uprawnienia administracyjne wymagane do migrowania skrzynek pocztowych przy użyciu migracji jednorazowej. Istnieją trzy możliwe opcje.

  - Administrator migracji musi być członkiem grupy **Administratorzy domeny** w usłudze Active Directory w organizacji lokalnej.

    Lub

  - Administrator migracji musi mieć przypisane uprawnienie **FullAccess** dla każdej lokalnej skrzynki pocztowej.

    Lub

  - Administrator migracji musi mieć przypisane uprawnienie **Odbierz jako** w lokalnej bazie danych skrzynki pocztowej, która przechowuje skrzynki pocztowe użytkownika.

- **Wyłącz funkcję Unified Messaging.** Jeśli lokalne skrzynki pocztowe, które migrujesz, są włączone dla usługi Unified Messaging (UM), należy wyłączyć usługę UM w skrzynkach pocztowych przed ich migracją. Następnie można włączyć UM w skrzynkach pocztowych po zakończeniu migracji.

- **Grupy zabezpieczeń i delegaci** Usługa migracji poczty e-mail nie może wykryć, czy grupy lokalna usługa Active Directory są grupami zabezpieczeń, więc nie może aprowizować żadnych zmigrowanych grup jako grup zabezpieczeń w Microsoft 365. Jeśli chcesz mieć grupy zabezpieczeń w dzierżawie Microsoft 365, musisz najpierw aprowizować pustą grupę zabezpieczeń obsługującą pocztę w dzierżawie Microsoft 365 przed rozpoczęciem migracji jednorazowej. Ponadto ta metoda migracji tylko przenosi skrzynki pocztowe, użytkowników poczty, kontakty poczty i grupy z obsługą poczty. Jeśli jakikolwiek inny obiekt usługi Active Directory, taki jak użytkownik, który nie został zmigrowany do Microsoft 365, zostanie przypisany jako menedżer lub pełnomocnik do migrowanego obiektu, musi zostać usunięty z obiektu przed migracją.

### <a name="step-2-create-a-migration-endpoint"></a>Krok 2. Tworzenie punktu końcowego migracji
<a name="BK_Step2"> </a>

Aby pomyślnie przeprowadzić migrację poczty e-mail, Microsoft 365 musi nawiązać połączenie ze źródłowym systemem poczty e-mail i komunikować się z nimi. W tym celu Microsoft 365 używa punktu końcowego migracji. Aby utworzyć punkt końcowy migracji Outlook Anywhere na potrzeby migracji jednorazowej, najpierw [połącz się z Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

Uruchom następujące polecenia w programie Exchange Online programu PowerShell:

```powershell
$Credentials = Get-Credential
```

W przykładzie użyto polecenia cmdlet [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) w celu uzyskania i przetestowania ustawień połączenia z lokalnym serwerem Exchange, a następnie użyje tych ustawień połączenia do utworzenia punktu końcowego migracji o nazwie "CutoverEndpoint".

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> Polecenie cmdlet **New-MigrationEndpoint** może służyć do określania bazy danych dla usługi do użycia przy użyciu opcji **-TargetDatabase** . W przeciwnym razie baza danych jest losowo przypisywana z lokacji Active Directory Federation Services (AD FS) 2.0, w której znajduje się skrzynka pocztowa zarządzania.

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

W Exchange Online programu PowerShell uruchom następujące polecenie, aby wyświetlić informacje o punkcie końcowym migracji "CutoverEndpoint":

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Krok 3. Tworzenie partii migracji jednorazowej
<a name="BK_Step3"> </a>

Aby utworzyć partię migracji na potrzeby migracji jednorazowej, możesz użyć polecenia cmdlet **New-MigrationBatch** w programie Exchange Online Programu PowerShell. Możesz utworzyć partię migracji i uruchomić ją automatycznie, dołączając parametr _AutoStart_ . Alternatywnie możesz utworzyć partię migracji, a następnie uruchomić ją ręcznie później przy użyciu polecenia cmdlet **Start-MigrationBatch** . W tym przykładzie utworzono partię migracji o nazwie "CutoverBatch" i użyto punktu końcowego migracji utworzonego w poprzednim kroku.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

W tym przykładzie utworzono również partię migracji o nazwie "CutoverBatch" i użyto punktu końcowego migracji utworzonego w poprzednim kroku. Ponieważ parametr  _AutoStart_ nie jest uwzględniony, partię migracji należy uruchomić ręcznie na pulpicie nawigacyjnym migracji lub za pomocą polecenia cmdlet **Start-MigrationBatch** . Jak wspomniano wcześniej, w danym momencie może istnieć tylko jedna partia migracji jednorazowej.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Aby sprawdzić, czy pomyślnie utworzono partię migracji na potrzeby migracji jednorazowej, uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić informacje o nowej partii migracji:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Krok 4. Uruchamianie partii migracji jednorazowej

Aby uruchomić partię migracji w programie Exchange Online programu PowerShell, uruchom następujące polecenie. Spowoduje to utworzenie partii migracji o nazwie "CutoverBatch".

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Jeśli partia migracji zostanie pomyślnie uruchomiona, jej stan na pulpicie nawigacyjnym migracji zostanie określony jako Synchronizowanie. Aby sprawdzić, czy pomyślnie uruchomiono partię migracji przy użyciu Exchange Online programu PowerShell, uruchom następujące polecenie:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Krok 5. Kierowanie wiadomości e-mail do Microsoft 365

Systemy poczty e-mail ustalają lokalizację, do której należy dostarczać wiadomości e-mail, na podstawie rekordu DNS nazywanego rekordem MX. W trakcie procesu migracji poczty e-mail rekord MX wskazywał źródłowy system poczty e-mail. Po zakończeniu migracji wiadomości e-mail do Microsoft 365 nadszedł czas, aby wskazać rekord MX na Microsoft 365. Pomaga to upewnić się, że wiadomość e-mail jest dostarczana do skrzynek pocztowych Microsoft 365. Przenosząc rekord MX, możesz również wyłączyć stary system poczty e-mail, gdy wszystko będzie gotowe.

W przypadku wielu dostawców hostingu DNS dostępne są szczegółowe instrukcje dotyczące zmieniania rekordu MX. Jeśli Twojego dostawcy hostingu DNS nie ma na liście lub jeśli chcesz zapoznać się z ogólnymi wskazówkami, dostępne są również [ogólne instrukcje dotyczące rekordów MX](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx).

Rozpoznanie zmienionego rekordu MX przez systemy poczty e-mail Twoich klientów i partnerów może potrwać do 72 godzin. Poczekaj co najmniej 72 godziny, zanim przejdziesz do następnego zadania: [Krok 6. Usuwanie partii migracji jednorazowej](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>Krok 6. Usuwanie partii migracji jednorazowej

Po zmianie rekordu MX i sprawdzeniu, czy wszystkie wiadomości e-mail są kierowane do Microsoft 365 skrzynek pocztowych, powiadom użytkowników, że ich poczta będzie Microsoft 365. Następnie możesz usunąć partię migracji jednorazowej. Przed usunięciem partii migracji sprawdź, czy są spełnione poniższe wymagania.

- Wszyscy użytkownicy używają Microsoft 365 skrzynek pocztowych. Po usunięciu partii poczta wysłana do skrzynek pocztowych w lokalnym Exchange Server nie jest kopiowana do odpowiednich Microsoft 365 skrzynek pocztowych.

- Microsoft 365 skrzynki pocztowe zostały zsynchronizowane co najmniej raz po rozpoczęciu wysyłania wiadomości e-mail bezpośrednio do nich. W tym celu upewnij się, że wartość w polu Czas ostatniej synchronizacji dla partii migracji jest nowsza niż wtedy, gdy poczta zaczęła być kierowana bezpośrednio do Microsoft 365 skrzynek pocztowych.

Aby usunąć partię migracji "CutoverBatch" w programie Exchange Online programu PowerShell, uruchom następujące polecenie:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Sekcja 7. Przypisywanie licencji użytkowników

 **Aktywuj Microsoft 365 konta użytkowników dla zmigrowanych kont, przypisując licencje.** W przypadku nieprzypisania licencji skrzynka pocztowa zostanie wyłączona po upływie okresu prolongaty (30 dni). Aby przypisać licencję w Centrum administracyjne platformy Microsoft 365, zobacz [Przypisywanie lub anulowanie przypisywania licencji](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Krok 8. Wykonywanie zadań po migracji

- **Utwórz rekord DNS wykrywania automatycznego, aby użytkownicy mogli łatwo uzyskać dostęp do swoich skrzynek pocztowych.** Po przeprowadzeniu migracji wszystkich lokalnych skrzynek pocztowych do Microsoft 365 można skonfigurować rekord DNS wykrywania automatycznego dla organizacji Microsoft 365, aby umożliwić użytkownikom łatwe łączenie się z nowymi skrzynkami pocztowymi Microsoft 365 przy użyciu Outlook i klientów mobilnych. Ten nowy rekord DNS wykrywania automatycznego musi używać tej samej przestrzeni nazw, której używasz dla organizacji Microsoft 365. Jeśli na przykład przestrzeń nazw w chmurze to cloud.contoso.com, należy utworzyć rekord DNS wykrywania automatycznego autodiscover.cloud.contoso.com.

    Jeśli zachowasz Exchange Server, upewnij się również, że rekord CNAME automatycznego wykrywania musi wskazywać Microsoft 365 w wewnętrznym i zewnętrznym systemie DNS po migracji, aby klient Outlook mógł nawiązać połączenie z poprawną skrzynką pocztową.

    > [!NOTE]
    >  W Exchange 2007 r. Exchange 2010 r. i Exchange 2013 r. należy również ustawić wartość `Set-ClientAccessServer AutodiscoverInternalConnectionURI` `Null`.

    Microsoft 365 używa rekordu CNAME do implementowania usługi wykrywania automatycznego dla klientów Outlook i mobilnych. Rekord CNAME wykrywania automatycznego musi zawierać następujące informacje:

  - **Alias:** autodiscover

  - **Wartość docelowa:** autodiscover.outlook.com

    Aby uzyskać więcej informacji, zobacz [Dodawanie rekordów DNS w celu nawiązania połączenia z domeną](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Zlikwiduj lokalne serwery programu Exchange.** Po upewnieniu się, że wszystkie wiadomości e-mail są kierowane bezpośrednio do Microsoft 365 skrzynek pocztowych i nie musisz już utrzymywać lokalnej organizacji poczty e-mail ani nie planujesz implementowania rozwiązania do logowania jednokrotnego, możesz odinstalować Exchange z serwerów i usunąć lokalne Exchange organizacji.

    Aby uzyskać więcej informacji, zobacz następujące artykuły:

  - [Modyfikowanie lub usuwanie programu Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Jak usunąć organizację programu Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Jak odinstalować program Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))