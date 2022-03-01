---
title: Przeprowadzanie migracji Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak za pomocą programu PowerShell przenosić zawartość ze źródłowego systemu poczty e-mail naraz przez wykonanie migracji Microsoft 365.
ms.openlocfilehash: 65f48d95a73742a0ba4e5225361ecfb0fbf66c40
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017780"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Przeprowadzanie migracji Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz przeprowadzić migrację zawartości skrzynek pocztowych użytkowników ze źródłowego systemu poczty e-mail do Microsoft 365 w całej układzie, korzystając z migracji czasowej. Ten artykuł zawiera migrację dodatkową poczty e-mail za pomocą programu Exchange Online PowerShell.

Zapoznaj się z tematem Co należy wiedzieć o migracji Microsoft 365-mail[, aby](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration) zapoznać się z omówieniem procesu migracji. Po zapoznaniu się z powyższym artykułem możesz rozpocząć migrację skrzynek pocztowych między systemami poczty e-mail, korzystając z przedstawionych tu instrukcji.

> [!NOTE]
> Do przeprowadzenia migracji Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">może</a> także użyć centrum administracyjnego programu SharePoint. Zobacz [Przeprowadzanie migracji Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Szacowany czas wykonania tego zadania: 2–5 minut na utworzenie partii migracji. Po zakończeniu partii migracji czas trwania migracji zależy od liczby skrzynek pocztowych w partii, rozmiaru poszczególnych skrzynek pocztowych i dostępnej pojemności sieci. Aby uzyskać informacje o innych czynnikach, które wpływają na czas migracji skrzynek pocztowych do Microsoft 365, zobacz [Wydajność migracji](/Exchange/mailbox-migration/office-365-migration-best-practices).

Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby sprawdzić, jakich uprawnień potrzebujesz, zobacz wpis "Migracja" w tabeli w temacie [Uprawnienia adresatów](/exchange/recipients-permissions-exchange-2013-help) .

Aby używać poleceń cmdlet programu Exchange Online PowerShell, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell programu PowerShell. [Instrukcje Połączenie dotyczące Exchange Online pracy ze zdalnym programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

## <a name="migration-steps"></a>Kroki migracji

### <a name="step-1-prepare-for-a-cutover-migration"></a>Krok 1. Przygotowywanie do migracji etapowej
<a name="BK_Step1"> </a>

- **Dodaj lokalną organizację Exchange jako zaakceptowaną domenę organizacji Microsoft 365 organizacji.** Usługa migracji tworzy identyfikator użytkownika i adres e-mail nowych skrzynek pocztowych w witrynie Microsoft Online Microsoft 365 Services za pomocą adresu SMTP lokalnych skrzynek pocztowych. Migracja nie powiedzie się, Exchange nie jest zaakceptowaną domeną ani domeną podstawową organizacji Microsoft 365 organizacji. Aby uzyskać więcej informacji, zobacz [Weryfikowanie domeny](../admin/setup/add-domain.md).

- **Skonfiguruj Outlook Anywhere na lokalnym Exchange serwera.** Usługa migracji poczty e-mail łączy się z lokalnym Exchange RPC przez HTTP lub Outlook Anywhere. Aby uzyskać informacje o tym, jak skonfigurować Outlook Anywhere dla użytkowników Exchange 2010, Exchange 2007 i Exchange 2003, zobacz następujące informacje:

  - [Exchange 2010: włączanie funkcji Outlook Anywhere](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: jak włączyć funkcję Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: Scenariusze wdrażania pakietu RPC przez HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [Jak skonfigurować usługę Outlook Anywhere za Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > Konfiguracja Outlook Anywhere musi być skonfigurowana przy użyciu certyfikatu wystawionego przez zaufany urząd certyfikacji. Nie można go skonfigurować przy użyciu certyfikatu z podpisem własnym. Aby uzyskać więcej informacji, zobacz [Jak skonfigurować protokół SSL dla Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

- **Sprawdź, czy możesz połączyć się ze swoją organizacją Exchange przy użyciu usługi Outlook Anywhere.** Wypróbuj jedną z tych metod, aby przetestować ustawienia połączenia:

  - Użyj programu Microsoft Outlook spoza sieci firmowej, aby połączyć się z lokalną skrzynką Exchange pocztowej.

  - Użyj narzędzia Microsoft [Exchange Remote Connectivity Analyzer,](https://www.testexchangeconnectivity.com/) aby przetestować ustawienia połączenia. Użyj funkcji Outlook Anywhere (RPC przez HTTP) lub testów wykrywania automatycznego w programie Outlook.

  - Uruchom następujące polecenia w programie Exchange Online PowerShell.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Przypisz lokalne konto użytkownika odpowiednie uprawnienia, aby uzyskać dostęp do skrzynek pocztowych w Twojej Exchange organizacji.** Lokalne konto użytkownika, którego używasz do łączenia się ze swoją lokalną organizacją programu Exchange (nazywane również administratorem migracji), musi mieć niezbędne uprawnienia dostępu do lokalnych skrzynek pocztowych, które chcesz zmigrować do usługi Microsoft 365. To konto użytkownika służy do tworzenia punktu końcowego migracji dla organizacji lokalnej.

    Na poniższej liście przedstawiono uprawnienia administracyjne wymagane do migrowania skrzynek pocztowych w celu przeprowadzenia migracji cutover. Dostępne są trzy opcje.

  - Administrator migracji musi być członkiem grupy **Administratorzy** domeny w usłudze Active Directory w organizacji lokalnej.

    Lub

  - Administrator migracji musi mieć przypisane uprawnienie **FullAccess** dla każdej lokalnej skrzynki pocztowej.

    Lub

  - Administrator migracji musi mieć przypisane uprawnienie **Receive As** do bazy danych lokalnych skrzynek pocztowych, w których są przechowywane skrzynki pocztowe użytkowników.

- **Wyłącz funkcję Unified Messaging.** Jeśli dla lokalnych skrzynek pocztowych, które będą migrowane, włączono funkcję Unified Messaging (UM), należy wyłączyć w nich funkcję UM przed rozpoczęciem migracji. Następnie możesz włączyć funkcję UM dla skrzynek pocztowych po zakończeniu migracji.

- **Grupy zabezpieczeń i pełnomocni** Usługa migracji poczty e-mail nie może wykryć, czy lokalne grupy usługi Active Directory są grupami zabezpieczeń, dlatego nie może ona zapewniać obsługi administracyjnej żadnych migrowanych grup jako grup zabezpieczeń w Microsoft 365. Aby mieć grupy zabezpieczeń w dzierżawie usługi Microsoft 365, przed rozpoczęciem migracji Microsoft 365 należy wykonać obsługę pustą grupę zabezpieczeń z obsługą poczty w dzierżawie usługi Microsoft 365. Ponadto ta metoda migracji tylko przenosi skrzynki pocztowe, użytkowników poczty, kontakty poczty i grupy z obsługą poczty. Jeśli jakikolwiek inny obiekt usługi Active Directory, na przykład użytkownik, który nie jest migrowany do programu Microsoft 365, zostanie przypisany jako menedżer lub pełnomocnik do migrego obiektu, musi on zostać usunięty z tego obiektu przed przeprowadzeniem migracji.

### <a name="step-2-create-a-migration-endpoint"></a>Krok 2. Tworzenie punktu końcowego migracji
<a name="BK_Step2"> </a>

Aby pomyślnie przeprowadzić migrację poczty e Microsoft 365 się ze źródłowym systemem poczty e-mail i komunikować się z nim. W tym celu program Microsoft 365 punkt końcowy migracji. Aby utworzyć punkt końcowy Outlook Anywhere w celu migracji etapowej, najpierw połącz się z [programem Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

Uruchom następujące polecenia w programie Exchange Online PowerShell:

```powershell
$Credentials = Get-Credential
```

W tym przykładzie użyto polecenia cmdlet [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) w celu uzyskania i przetestowania ustawień połączenia z lokalnym serwerem Exchange, a następnie za ich podstawie utworzysz punkt końcowy migracji o nazwie "CutoverEndpoint".

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> Polecenie **cmdlet New-MigrationEndpoint** umożliwia określenie bazy danych dla usługi za pomocą opcji **-TargetDatabase** . W przeciwnym razie baza danych jest losowo przypisywana z witryny usług federowanych Active Directory (AD FS) 2.0, w której znajduje się skrzynka pocztowa zarządzania.

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

W Exchange Online programu PowerShell uruchom następujące polecenie, aby wyświetlić informacje o punkcie końcowym migracji "CutoverEndpoint":

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Krok 3. Tworzenie partii migracji jednorazowej
<a name="BK_Step3"> </a>

Możesz użyć polecenia cmdlet **New-MigrationBatch** w programie Exchange Online PowerShell, aby utworzyć partię migracji do migracji cutover. Partię migracji można utworzyć i uruchomić automatycznie, uwzględniając _parametr Autostart_ . Ewentualnie możesz utworzyć partię migracji, a następnie uruchomić ją ręcznie później przy użyciu polecenia **cmdlet Start-MigrationBatch** . W tym przykładzie jest tworzona partia migracji o nazwie "CutoverBatch" i korzysta z punktu końcowego migracji utworzonego w poprzednim kroku.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

W tym przykładzie jest również tworzona partia migracji o nazwie "CutoverBatch" i używa punktu końcowego migracji utworzonego w poprzednim kroku. Ponieważ parametr  _Autostart_ nie jest uwzględniony, partia migracji musi zostać uruchomiona ręcznie na pulpicie nawigacyjnym migracji lub przy użyciu polecenia cmdlet **Start-MigrationBatch** . Jak wspomniano wcześniej, jednocześnie może istnieć tylko jedna partia migracji.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Aby sprawdzić, czy partia migracji została pomyślnie utworzona na podstawie migracji, uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić informacje o nowej partii migracji:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Krok 4. Uruchamianie partii migracji jednorazowej

Aby uruchomić partię migracji w programie Exchange Online PowerShell, uruchom następujące polecenie. Spowoduje to utworzenie partii migracji o nazwie "CutoverBatch".

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Jeśli partia migracji zostanie pomyślnie uruchomiona, jej stan na pulpicie nawigacyjnym migracji zostanie określony jako Synchronizowanie. Aby sprawdzić, czy partia migracji została pomyślnie uruchomiona przy użyciu programu Exchange Online PowerShell, uruchom następujące polecenie:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Krok 5. Rozsyłanie wiadomości e-mail do Microsoft 365

Systemy poczty e-mail ustalają lokalizację, do której należy dostarczać wiadomości e-mail, na podstawie rekordu DNS nazywanego rekordem MX. W trakcie procesu migracji poczty e-mail rekord MX wskazywał źródłowy system poczty e-mail. Po zakończeniu migracji poczty e-Microsoft 365 e-mail należy wskazać rekordowi MX, aby był Microsoft 365. Dzięki temu wiadomości e-mail będą na pewno dostarczane do twoich Microsoft 365 pocztowych. Przenosząc rekord MX, możesz też wyłączyć stary system poczty e-mail, gdy wszystko będzie już gotowe.

W przypadku wielu dostawców hostingu DNS dostępne są szczegółowe instrukcje dotyczące zmieniania rekordu MX. Jeśli Twojego dostawcy hostingu DNS nie ma na liście lub jeśli chcesz zapoznać się z ogólnymi wskazówkami, dostępne są również [ogólne instrukcje dotyczące rekordów MX](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx).

Rozpoznanie zmienionego rekordu MX przez systemy poczty e-mail Twoich klientów i partnerów może potrwać do 72 godzin. Przed rozpoczęciem kolejnego zadania poczekaj co najmniej 72 godziny: [Krok 6. Usuwanie partii migracji etapowej](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>Krok 6. Usuwanie partii migracji jednorazowej

Po zmianie rekordu MX i sprawdzeniu, czy wszystkie wiadomości e-mail są kierowane do Microsoft 365 pocztowych, powiadom użytkowników, że ich poczta trafia do Microsoft 365. Następnie możesz usunąć partię migracji cutover. Przed usunięciem partii migracji sprawdź, czy są spełnione poniższe wymagania.

- Wszyscy użytkownicy Microsoft 365 skrzynki pocztowe. Po usunięciu partii poczta wysyłana do skrzynek pocztowych na lokalnym Exchange Server nie jest kopiowana do odpowiadających im Microsoft 365 pocztowych.

- Microsoft 365 zostały zsynchronizowane co najmniej raz po zakończeniu przesyłania poczty bezpośrednio do tych skrzynek. W tym celu upewnij się, że wartość w polu Godzina ostatniej synchronizacji w partii migracji jest najnowsza niż wartość, gdy poczta rozpoczyna się bezpośrednio do Microsoft 365 pocztowych.

Aby usunąć partię migracji "CutoverBatch" w programie Exchange Online PowerShell, uruchom następujące polecenie:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Sekcja 7. Przypisywanie licencji użytkowników

 **Aktywuj Microsoft 365 użytkowników dla kont poddanych migracji, przypisując licencje.** W przypadku nieprzypisania licencji skrzynka pocztowa zostanie wyłączona po upływie okresu prolongaty (30 dni). Aby przypisać licencję w centrum administracyjne platformy Microsoft 365, zobacz [Przypisywanie lub nieprzypisywanie licencji](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Krok 8. Wykonywanie zadań po migracji

- **Utwórz rekord DNS wykrywania automatycznego, aby użytkownicy mogli łatwo uzyskać dostęp do swoich skrzynek pocztowych.** Po zakończeniu migracji wszystkich lokalnych skrzynek pocztowych do usługi Microsoft 365 możesz skonfigurować rekord DNS wykrywania automatycznego dla swojej organizacji usługi Microsoft 365, aby umożliwić użytkownikom łatwe łączenie się ze swoimi nowymi skrzynkami pocztowymi usługi Microsoft 365 za pomocą usługi Outlook i klientów przenośnych. Ten nowy rekord DNS wykrywania automatycznego musi korzystać z tej samej przestrzeni nazw, która jest Microsoft 365 organizacji. Jeśli na przykład przestrzeń nazw w chmurze to cloud.contoso.com, należy utworzyć rekord DNS wykrywania automatycznego autodiscover.cloud.contoso.com.

    Jeśli zachować Exchange Server, upewnij się też, że po zakończeniu migracji rekord CNAME DNS wykrywania automatycznego musi wskazać usługę Microsoft 365 zarówno w wewnętrznym, jak i zewnętrznym systemie DNS, tak aby klient usługi Outlook łączył się z właściwą skrzynką pocztową.

    > [!NOTE]
    >  W Exchange 2007, Exchange 2010 i Exchange 2013 także należy `Set-ClientAccessServer AutodiscoverInternalConnectionURI` ustawić wartość `Null`.

    Microsoft 365 używa rekordu CNAME do wdrożenia usługi wykrywania automatycznego dla klientów Outlook przenośnych. Rekord CNAME wykrywania automatycznego musi zawierać następujące informacje:

  - **Alias:** autodiscover

  - **Wartość docelowa:** autodiscover.outlook.com

    Aby uzyskać więcej informacji, zobacz [Dodawanie rekordów DNS w celu połączenia domeny](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Zlikwiduj lokalne serwery programu Exchange.** Po sprawdzeniu, że wszystkie wiadomości e-mail są kierowane bezpośrednio do skrzynek pocztowych usługi Microsoft 365, i gdy nie musisz zachowywać lokalnej organizacji poczty e-mail ani nie planujesz zaimplementowania rozwiązania logowania jednokrotnego (SSO), możesz odinstalować program Exchange z serwerów i usunąć lokalną organizację programu Exchange.

    Aby uzyskać więcej informacji, zobacz następujące artykuły:

  - [Modyfikowanie lub usuwanie programu Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Jak usunąć organizację programu Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Jak odinstalować program Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))