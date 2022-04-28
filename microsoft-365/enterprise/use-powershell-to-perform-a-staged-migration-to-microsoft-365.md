---
title: Używanie programu PowerShell do wykonywania migracji etapowej do platformy Microsoft 365
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Dowiedz się, jak za pomocą programu PowerShell przenosić zawartość ze źródłowego systemu poczty e-mail w czasie przy użyciu migracji etapowej do Microsoft 365.
ms.openlocfilehash: 872ae883728e1c20a6233e14e56bda804e757590
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091968"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Używanie programu PowerShell do wykonywania migracji etapowej do platformy Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Zawartość skrzynek pocztowych użytkowników można migrować ze źródłowego systemu poczty e-mail do Microsoft 365 w czasie przy użyciu migracji etapowej.

W tym artykule przedstawiono zadania związane z etapową migracją poczty e-mail przy użyciu programu Exchange Online programu PowerShell. Temat [Co musisz wiedzieć o etapowej migracji poczty e-mail](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration), zawiera omówienie procesu migracji. Po zapoznaniu się z powyższym artykułem możesz rozpocząć migrację skrzynek pocztowych między systemami poczty e-mail, korzystając z przedstawionych tu instrukcji.

> [!NOTE]
> Do przeprowadzania migracji etapowej można również użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a>. Zobacz [Przeprowadzanie migracji etapowej wiadomości e-mail do Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Szacowany czas wykonania tego zadania: 2–5 minut na utworzenie partii migracji. Po uruchomieniu partii migracji czas trwania migracji będzie się różnić w zależności od liczby skrzynek pocztowych w partii, rozmiaru każdej skrzynki pocztowej i dostępnej pojemności sieciowej. Aby uzyskać informacje o innych czynnikach wpływających na czas migrowania skrzynek pocztowych do Microsoft 365, zobacz [Wydajność migracji](/Exchange/mailbox-migration/office-365-migration-best-practices).

Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis "Migracja" w [temacie Uprawnienia adresatów](/exchange/recipients-permissions-exchange-2013-help) .

Aby użyć poleceń cmdlet programu PowerShell Exchange Online, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell. Aby uzyskać [instrukcje, zobacz Połączenie, aby Exchange Online za pomocą zdalnego programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

## <a name="migration-steps"></a>Kroki migracji

### <a name="step-1-prepare-for-a-staged-migration"></a>Krok 1. Przygotowanie do migracji etapowej

Przed migracją skrzynek pocztowych do Microsoft 365 przy użyciu migracji etapowej należy wprowadzić kilka zmian w środowisku Exchange.

 **Skonfiguruj Outlook Anywhere w lokalnym Exchange Server** Usługa migracji poczty e-mail używa Outlook Anywhere (znanej również jako RPC za pośrednictwem protokołu HTTP), aby nawiązać połączenie z lokalnym Exchange Server. Aby uzyskać informacje na temat konfigurowania Outlook Anywhere dla Exchange Server 2007 r. i Exchange 2003 r., zobacz następujące informacje:

- [Exchange 2007: jak włączyć funkcję Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Jak skonfigurować funkcję Outlook Anywhere w programie Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Do konfiguracji funkcji Outlook Anywhere należy użyć certyfikatu wystawionego przez zaufany urząd certyfikacji (UC). Funkcji Outlook Anywhere nie można skonfigurować z użyciem certyfikatu z podpisem własnym. Aby uzyskać więcej informacji, zobacz [Jak skonfigurować połączenie SSL dla funkcji Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **Opcjonalnie: sprawdź, czy możesz połączyć się ze swoją organizacją programu Exchange za pomocą funkcji Outlook Anywhere**. Możesz sprawdzić ustawienia połączenia, korzystając z jednej z następujących metod.

- Użyj programu Outlook poza siecią firmową, aby połączyć się ze swoją lokalną skrzynką pocztową programu Exchange.

- Użyj [analizatora łączności zdalnej firmy Microsoft](https://https://testconnectivity.microsoft.com/) , aby przetestować ustawienia połączenia. Użyj funkcji Outlook Anywhere (RPC przez HTTP) lub testów wykrywania automatycznego w programie Outlook.

- Uruchom następujące polecenia w programie Exchange Online programu PowerShell:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Ustawianie uprawnień** Lokalne konto użytkownika używane do nawiązywania połączenia z lokalną organizacją Exchange (nazywane również administratorem migracji) musi mieć uprawnienia niezbędne do uzyskiwania dostępu do lokalnych skrzynek pocztowych, które mają zostać zmigrowane do Microsoft 365. To konto użytkownika jest używane podczas nawiązywania połączenia z systemem poczty e-mail przez utworzenie punktu końcowego migracji w dalszej części tej procedury [Krok 3: Tworzenie punktu końcowego migracji](#step-3-create-a-migration-endpoint).

Aby przeprowadzić migrację skrzynek pocztowych, administrator musi uzyskać odpowiednie uprawnienia w jeden z następujących sposobów:

- Bądź członkiem grupy **Administratorzy domeny** w usłudze Active Directory w organizacji lokalnej.

    lub

- Należy przypisać **uprawnienie FullAccess** dla każdej lokalnej skrzynki pocztowej i uprawnienie **WriteProperty** do modyfikowania właściwości **TargetAddress** na kontach użytkowników lokalnych.

    lub

- Należy przypisać uprawnienie **Odbierz jako** w lokalnej bazie danych skrzynki pocztowej, która przechowuje skrzynki pocztowe użytkowników, oraz uprawnienie **WriteProperty** do modyfikowania właściwości **TargetAddress** na kontach użytkowników lokalnych.

Aby uzyskać instrukcje dotyczące ustawiania tych uprawnień, zobacz [Przypisywanie uprawnień do migrowania skrzynek pocztowych do Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Wyłącz ujednolicone komunikaty (UM)** Jeśli usługa UM jest włączona dla lokalnych skrzynek pocztowych, które migrujesz, wyłącz usługę UM przed migracją. Włącz usługę UM dla skrzynek pocztowych po zakończeniu migracji. Aby uzyskać instrukcje, [zobaczDisable unified messaging (Ujednolicone komunikaty](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80))).

 **Użyj synchronizacji katalogów, aby utworzyć nowych użytkowników w Microsoft 365.** Synchronizacja katalogów służy do tworzenia wszystkich użytkowników lokalnych w organizacji Microsoft 365.

Musisz licencji użytkowników po ich utworzeniu. Na dodanie licencji masz 30 dni od momentu utworzenia użytkowników. Aby uzyskać instrukcje dodawania licencji, zobacz [Krok 8: Wykonywanie zadań po migracji](#step-8-complete-post-migration-tasks).

 Aby zsynchronizować i utworzyć użytkowników lokalnych w Microsoft 365, możesz użyć narzędzia synchronizacji Microsoft Azure Active Directory (Azure AD) lub usług synchronizacji Microsoft Azure AD. Po migracji skrzynek pocztowych do Microsoft 365 zarządzasz kontami użytkowników w organizacji lokalnej i są one synchronizowane z organizacją Microsoft 365. Aby uzyskać więcej informacji, [zobaczDirectory Integration](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Krok 2. Tworzenie pliku CSV dla partii migracji etapowej

Po zidentyfikowaniu użytkowników, których lokalne skrzynki pocztowe mają zostać zmigrowane do Microsoft 365, należy użyć pliku wartości rozdzielanej przecinkami (CSV) do utworzenia partii migracji. Każdy wiersz w pliku CSV — używany przez Microsoft 365 do uruchomienia migracji — zawiera informacje o lokalnej skrzynce pocztowej.

> [!NOTE]
> Nie ma limitu liczby skrzynek pocztowych, które można migrować do Microsoft 365 przy użyciu migracji etapowej. Plik CSV używany do tworzenia partii migracji może zawierać maksymalnie 2000 wierszy. Aby przeprowadzić migrację więcej niż 2000 skrzynek pocztowych, utwórz dodatkowe pliki CSV, a następnie utwórz nowe partie migracji z użyciem poszczególnych plików.

 **Obsługiwane atrybuty**

Plik CSV używany podczas migracji etapowej obsługuje trzy atrybuty opisane poniżej. Każdy wiersz w pliku CSV odpowiada jednej skrzynce pocztowej i musi zawierać wartość każdego z tych atrybutów.

|**Atrybut**|**Opis**|**Wymagany?**|
|:-----|:-----|:-----|
|Emailaddress  <br/> |Określa podstawowy adres e-mail SMTP lokalnej skrzynki pocztowej, na przykład mariap@contoso.com.  <br/> Użyj podstawowego adresu SMTP dla lokalnych skrzynek pocztowych, a nie identyfikatorów użytkowników z Microsoft 365. Jeśli na przykład domena lokalna ma nazwę contoso.com ale Microsoft 365 domena poczty e-mail ma nazwę service.contoso.com, należy użyć nazwy domeny contoso.com adresów e-mail w pliku CSV.  <br/> |Wymagany  <br/> |
|Password (hasło)  <br/> |Hasło do ustawienia dla nowej skrzynki pocztowej Microsoft 365. Wszelkie ograniczenia haseł stosowane do organizacji Microsoft 365 mają również zastosowanie do haseł zawartych w pliku CSV.  <br/> |Opcjonalny  <br/> |
|Forcechangepassword  <br/> |Określa, czy użytkownik musi zmienić hasło przy pierwszym zalogowaniu się do nowej skrzynki pocztowej Microsoft 365. Dla tego parametru użyj wartości **True** (prawda) lub **False** (fałsz). <br/> > [!NOTE]> Jeśli zaimplementowano rozwiązanie logowania jednokrotnego przez wdrożenie Active Directory Federation Services (AD FS) lub nowszej w organizacji lokalnej, musisz użyć wartości **False** dla wartości atrybutu **ForceChangePassword**.          |Opcjonalny  <br/> |

 **Format pliku CSV**

Poniżej przedstawiono przykładowy format pliku CSV. W tym przykładzie trzy lokalne skrzynki pocztowe są migrowane do Microsoft 365.

Pierwszy wiersz w pliku CSV, czyli wiersz nagłówka, zawiera nazwy atrybutów, czyli pól, określonych w kolejnych wierszach. Poszczególne nazwy atrybutów są rozdzielone przecinkami.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

Każdy wiersz poniżej wiersza nagłówka odpowiada jednemu użytkownikowi i zawiera informacje używane do migrowania jego skrzynki pocztowej. Wartości atrybutów w każdym wierszu należy wprowadzić w takiej samej kolejności, w jakiej wprowadzono nazwy atrybutów w wierszu nagłówka.

Użyj dowolnego edytora tekstów lub aplikacji, takiej jak Excel , do utworzenia pliku CSV. Zapisz plik jako csv lub txt.

> [!NOTE]
> Jeśli plik CSV zawiera znaki specjalne lub niebędące znakami ASCII, zapisz go przy użyciu kodowania UTF-8 lub innego kodowania Unicode. W zależności od aplikacji zapisywanie pliku CSV z kodowaniem UTF-8 lub innym kodowaniem Unicode może być łatwiejsze, gdy ustawienia regionalne systemu komputera są zgodne z językiem używanym w pliku CSV.

### <a name="step-3-create-a-migration-endpoint"></a>Krok 3. Tworzenie punktu końcowego migracji

Aby pomyślnie przeprowadzić migrację poczty e-mail, Microsoft 365 musi nawiązać połączenie ze źródłowym systemem poczty e-mail i komunikować się z nimi. W tym celu Microsoft 365 używa punktu końcowego migracji. Aby utworzyć punkt końcowy migracji Outlook Anywhere przy użyciu programu PowerShell na potrzeby migracji etapowych, najpierw [połącz się z Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Przenoszenie i migracja poleceń cmdlet](/powershell/exchange/).

Aby utworzyć punkt końcowy migracji Outlook Anywhere o nazwie "StagedEndpoint" w programie Exchange Online programu PowerShell, uruchom następujące polecenia:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **New-MigrationEndpoint** , [zobaczNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> Polecenie cmdlet **New-MigrationEndpoint** może służyć do określania bazy danych dla usługi do użycia przy użyciu opcji **-TargetDatabase** . W przeciwnym razie baza danych jest losowo przypisywana z lokacji Active Directory Federation Services (AD FS) 2.0, w której znajduje się skrzynka pocztowa zarządzania.

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

W Exchange Online programu PowerShell uruchom następujące polecenie, aby wyświetlić informacje o punkcie końcowym migracji "StagedEndpoint":

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Krok 4. Tworzenie i uruchamianie partii migracji etapów

Aby utworzyć partię migracji na potrzeby migracji jednorazowej, możesz użyć polecenia cmdlet **New-MigrationBatch** w programie Exchange Online Programu PowerShell. Możesz utworzyć partię migracji i uruchomić ją automatycznie, dołączając parametr _AutoStart_ . Alternatywnie możesz utworzyć partię migracji, a następnie uruchomić ją ręcznie później przy użyciu polecenia cmdlet **Start-MigrationBatch** . W tym przykładzie utworzono partię migracji o nazwie "StagedBatch1" i użyto punktu końcowego migracji utworzonego w poprzednim kroku.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

W tym przykładzie utworzono również partię migracji o nazwie "StagedBatch1" i użyto punktu końcowego migracji utworzonego w poprzednim kroku. Ponieważ parametr  _AutoStart_ nie jest uwzględniony, partię migracji należy uruchomić ręcznie na pulpicie nawigacyjnym migracji lub za pomocą polecenia cmdlet **Start-MigrationBatch** . Jak wspomniano wcześniej, w danym momencie może istnieć tylko jedna partia migracji jednorazowej.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić informacje o "StagedBatch1":

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Możesz również sprawdzić, czy partia została uruchomiona, uruchamiając następujące polecenie:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **Get-MigrationBatch** , [zobaczGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Krok 5. Konwertowanie lokalnych skrzynek pocztowych na użytkowników obsługujących pocztę

Po pomyślnym przeprowadzeniu migracji partii skrzynek pocztowych potrzebny jest sposób na udostępnienie użytkownikom ich poczty. Użytkownik, którego skrzynka pocztowa została zmigrowana, ma teraz zarówno lokalną skrzynkę pocztową, jak i jedną w Microsoft 365. Użytkownicy, którzy mają skrzynkę pocztową w Microsoft 365, przestaną otrzymywać nową pocztę w lokalnej skrzynce pocztowej.

Ponieważ migracje nie zostały ukończone, nie możesz jeszcze skierować wszystkich użytkowników do Microsoft 365 ich wiadomości e-mail. Co więc należy zrobić w przypadku użytkowników mających oba rodzaje skrzynek? Można przekonwertować lokalne skrzynki pocztowe, których migrację już przeprowadzono, na użytkowników z włączoną obsługą poczty. Po zmianie ze skrzynki pocztowej na użytkownika z obsługą poczty możesz skierować użytkownika do Microsoft 365 wiadomości e-mail zamiast do lokalnej skrzynki pocztowej.

Innym ważnym powodem konwertowania lokalnych skrzynek pocztowych na użytkowników obsługujących pocztę jest zachowanie adresów proxy z Microsoft 365 skrzynek pocztowych przez skopiowanie adresów proxy do użytkowników obsługujących pocztę. W ten sposób możesz zarządzać użytkownikami w chmurze za pośrednictwem swojej organizacji lokalnej, korzystając z usługi Active Directory. Ponadto jeśli zdecydujesz się zlikwidować lokalną organizację Exchange Server po migracji wszystkich skrzynek pocztowych do Microsoft 365, adresy proxy skopiowane do użytkowników obsługujących pocztę pozostaną w lokalna usługa Active Directory.

### <a name="step-6-delete-a-staged-migration-batch"></a>Krok 6. Usuwanie partii migracji etapowej

 Po pomyślnym zmigrowanie wszystkich skrzynek pocztowych w partii migracji i przekonwertowanie lokalnych skrzynek pocztowych w partii na użytkowników obsługujących pocztę umożliwia usunięcie partii migracji etapowej. Upewnij się, że poczta jest przekazywana do Microsoft 365 skrzynek pocztowych w partii migracji. Po usunięciu partii migracji etapowej usługa migracji czyści wszelkie rekordy związane z partią migracji i usuwa partię migracji.

Aby usunąć partię migracji "StagedBatch1" w programie Exchange Online programu PowerShell, uruchom następujące polecenie.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **Remove-MigrationBatch** , [zobaczRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Sprawdź, czy to zadziałało

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić informacje o "IMAPBatch1":

```powershell
Get-MigrationBatch StagedBatch1
```

Polecenie zwróci partię migracji ze stanem **Usuwanie** lub zwróci błąd informujący, że nie można odnaleźć partii migracji, sprawdzając, czy partia została usunięta.

Aby uzyskać więcej informacji na temat polecenia cmdlet **Get-MigrationBatch** , [zobaczGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Krok 7. Przypisywanie licencji do użytkowników Microsoft 365

Aktywuj Microsoft 365 konta użytkowników dla zmigrowanych kont, przypisując licencje. W przypadku nieprzypisania licencji skrzynka pocztowa zostanie wyłączona po upływie okresu prolongaty (30 dni). Aby przypisać licencję w Centrum administracyjne platformy Microsoft 365, zobacz [Przypisywanie lub anulowanie przypisywania licencji](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Krok 8. Wykonywanie zadań po migracji

- **Utwórz rekord DNS wykrywania automatycznego, aby użytkownicy mogli łatwo uzyskać dostęp do swoich skrzynek pocztowych.** Po przeprowadzeniu migracji wszystkich lokalnych skrzynek pocztowych do Microsoft 365 można skonfigurować rekord DNS wykrywania automatycznego dla organizacji Microsoft 365, aby umożliwić użytkownikom łatwe łączenie się z nowymi skrzynkami pocztowymi Microsoft 365 przy użyciu Outlook i klientów mobilnych. Ten nowy rekord DNS wykrywania automatycznego musi używać tej samej przestrzeni nazw, której używasz dla organizacji Microsoft 365. Jeśli na przykład przestrzeń nazw w chmurze to cloud.contoso.com, należy utworzyć rekord DNS wykrywania automatycznego autodiscover.cloud.contoso.com.

    Microsoft 365 używa rekordu CNAME do implementowania usługi wykrywania automatycznego dla klientów Outlook i mobilnych. Rekord CNAME wykrywania automatycznego musi zawierać następujące informacje:

  - **Alias:** autodiscover

  - **Wartość docelowa:** autodiscover.outlook.com

    Aby uzyskać więcej informacji, zobacz [Dodawanie rekordów DNS w celu nawiązania połączenia z domeną](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Zlikwiduj lokalne serwery programu Exchange.** Po upewnieniu się, że wszystkie wiadomości e-mail są kierowane bezpośrednio do Microsoft 365 skrzynek pocztowych i nie musisz już utrzymywać lokalnej organizacji poczty e-mail ani nie planujesz implementowania rozwiązania logowania jednokrotnego, możesz odinstalować Exchange z serwerów i usunąć lokalną organizację Exchange.

    Aby uzyskać więcej informacji, zobacz następujące artykuły:

  - [Modyfikowanie lub usuwanie programu Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Jak usunąć organizację programu Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Jak odinstalować program Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
