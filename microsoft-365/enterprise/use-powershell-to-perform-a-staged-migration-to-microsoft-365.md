---
title: Przeprowadzanie etapowej migracji do programu PowerShell Microsoft 365
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Dowiedz się, jak za pomocą programu PowerShell przenosić zawartość ze źródłowego systemu poczty e-mail w czasie podczas migracji etapowej do Microsoft 365.
ms.openlocfilehash: 562dcb8f32a0cd2b8452f2145dcb608dac353e2f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017807"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Przeprowadzanie etapowej migracji do programu PowerShell Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz przeprowadzić migrację zawartości skrzynek pocztowych użytkowników ze źródłowego systemu poczty e-mail do Microsoft 365 w czasie podczas migracji etapowej.

Ten artykuł zawiera informacje o zadaniach związanych z migracją etapową poczty e-mail przy Exchange Online PowerShell. Temat Co należy wiedzieć o etapowej migracji poczty [e-mail](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration) zawiera omówienie procesu migracji. Po zapoznaniu się z powyższym artykułem możesz rozpocząć migrację skrzynek pocztowych między systemami poczty e-mail, korzystając z przedstawionych tu instrukcji.

> [!NOTE]
> Do przeprowadzania migracji <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">etapowej Exchange użyć</a> centrum administracyjnego programu PowerPoint. Zobacz [Przeprowadzanie etapowej migracji poczty e-mail do Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Szacowany czas wykonania tego zadania: 2–5 minut na utworzenie partii migracji. Po zakończeniu partii migracji czas trwania migracji zależy od liczby skrzynek pocztowych w partii, rozmiaru poszczególnych skrzynek pocztowych i dostępnej pojemności sieci. Aby uzyskać informacje o innych czynnikach, które wpływają na czas migracji skrzynek pocztowych do Microsoft 365, zobacz [Wydajność migracji](/Exchange/mailbox-migration/office-365-migration-best-practices).

Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby sprawdzić, jakich uprawnień potrzebujesz, zobacz wpis "Migracja" w temacie [Uprawnienia adresatów](/exchange/recipients-permissions-exchange-2013-help) .

Aby używać poleceń cmdlet programu Exchange Online PowerShell, musisz zalogować się i zaimportować polecenia cmdlet do lokalnej sesji Windows PowerShell programu PowerShell. [Instrukcje Połączenie dotyczące Exchange Online pracy ze zdalnym programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

## <a name="migration-steps"></a>Kroki migracji

### <a name="step-1-prepare-for-a-staged-migration"></a>Krok 1. Przygotowywanie do migracji etapowej

Przed przeprowadzeniem migracji etapowej Microsoft 365 skrzynek pocztowych do programu w celu przeprowadzenia migracji etapowej należy wprowadzić kilka zmian w środowisku programu Exchange.

 Skonfiguruj usługę **Outlook Anywhere** w lokalnej usłudze Exchange Server Usługa migracji poczty e-mail używa programu Outlook Anywhere (nazywanego także RPC przez HTTP) do nawiązania połączenia z lokalnym Exchange Server. Aby uzyskać informacje o tym, jak skonfigurować Outlook Anywhere Exchange Server 2007 i Exchange 2003, zobacz następujące informacje:

- [Exchange 2007: jak włączyć funkcję Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Jak skonfigurować funkcję Outlook Anywhere w programie Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Do konfiguracji funkcji Outlook Anywhere należy użyć certyfikatu wystawionego przez zaufany urząd certyfikacji (UC). Funkcji Outlook Anywhere nie można skonfigurować z użyciem certyfikatu z podpisem własnym. Aby uzyskać więcej informacji, zobacz [Jak skonfigurować połączenie SSL dla funkcji Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **Opcjonalnie: sprawdź, czy możesz połączyć się ze swoją organizacją programu Exchange za pomocą funkcji Outlook Anywhere**. Możesz sprawdzić ustawienia połączenia, korzystając z jednej z następujących metod.

- Użyj programu Outlook poza siecią firmową, aby połączyć się ze swoją lokalną skrzynką pocztową programu Exchange.

- Użyj [Analizatora łączności zdalnej firmy Microsoft](https://https://testconnectivity.microsoft.com/) , aby przetestować ustawienia połączenia. Użyj funkcji Outlook Anywhere (RPC przez HTTP) lub testów wykrywania automatycznego w programie Outlook.

- Uruchom następujące polecenia w programie Exchange Online PowerShell:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Ustawianie uprawnień** Lokalne konto użytkownika, którego używasz do łączenia się ze swoją lokalną organizacją programu Exchange (nazywane również administratorem migracji), musi mieć niezbędne uprawnienia dostępu do lokalnych skrzynek pocztowych, które chcesz zmigrować do usługi Microsoft 365. To konto użytkownika jest używane do nawiązywania połączenia z systemem poczty e-mail przez utworzenie punktu końcowego migracji w dalszej części tej procedury Krok [3. Tworzenie punktu końcowego migracji](#step-3-create-a-migration-endpoint).

Aby przeprowadzić migrację skrzynek pocztowych, administrator musi uzyskać odpowiednie uprawnienia w jeden z następujących sposobów:

- Być członkiem grupy **Administratorzy domeny** w usłudze Active Directory w organizacji lokalnej.

    lub

- Mieć przypisane uprawnienie **FullAccess** do każdej lokalnej skrzynki pocztowej i uprawnienie **WriteProperty** do **modyfikowania właściwości TargetAddress** lokalnych kont użytkowników.

    lub

- Otrzymać uprawnienie **Receive As** w bazie danych lokalnych skrzynek pocztowych, w których są przechowywane skrzynki pocztowe użytkowników, oraz uprawnienie **WriteProperty** do modyfikowania właściwości **TargetAddress** lokalnych kont użytkowników.

Aby uzyskać instrukcje dotyczące sposobu ustawienia tych uprawnień, zobacz [Przypisywanie](/Exchange/mailbox-migration/assign-permissions-for-migration) uprawnień do migrowania skrzynek pocztowych do Microsoft 365.

 **Wyłączanie funkcji Unified Messaging (UM)** Jeśli dla lokalnych skrzynek pocztowych, które będą podlegać migracji, jest włączona, wyłącz usługę UM przed rozpoczęciem migracji. Włącz UM dla skrzynek pocztowych po zakończeniu migracji. Aby uzyskać instrukcje, zobacz [Nie można uzyskać informacji o funkcji Unified Messaging](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Użyj synchronizacji katalogów, aby utworzyć nowych użytkowników w Microsoft 365.** Za pomocą synchronizacji katalogów można utworzyć wszystkich użytkowników lokalnych w Microsoft 365 organizacji.

Po utworzeniu użytkowników należy uzyskać na nich licencję. Na dodanie licencji masz 30 dni od momentu utworzenia użytkowników. Aby uzyskać instrukcje dodawania licencji, zobacz [Krok 8. Zadania wykonywane po migracji](#step-8-complete-post-migration-tasks).

 Do synchronizowania i tworzenia użytkowników lokalnych w usłudze Microsoft Azure Active Directory możesz użyć narzędzia do synchronizacji usług Microsoft Azure Active Directory Microsoft 365 (Azure AD) lub usług synchronizacji usługi Microsoft Azure AD. Po migracji skrzynek pocztowych do usługi Microsoft 365 zarządzasz kontami użytkowników w organizacji lokalnej i synchronizowane z Twoją organizacją Microsoft 365 organizacji. Aby uzyskać więcej informacji, zobacz [Integracja z usługądirectory](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Krok 2. Tworzenie pliku CSV dla partii migracji etapowej

Po zidentyfikowaniu użytkowników, których lokalne skrzynki pocztowe mają zostać zmigrowane do programu Microsoft 365, utwórz partię migracji za pomocą pliku wartości rozdzielonych przecinkami (CSV). Każdy wiersz w pliku CSV — używanym Microsoft 365 do uruchomienia migracji — zawiera informacje o lokalnej skrzynce pocztowej.

> [!NOTE]
> Liczba skrzynek pocztowych, które można migrować do usługi Microsoft 365 etapowa, jest bez ograniczeń. Plik CSV używany do tworzenia partii migracji może zawierać maksymalnie 2000 wierszy. Aby przeprowadzić migrację więcej niż 2000 skrzynek pocztowych, utwórz dodatkowe pliki CSV, a następnie utwórz nowe partie migracji z użyciem poszczególnych plików.

 **Obsługiwane atrybuty**

Plik CSV używany podczas migracji etapowej obsługuje trzy atrybuty opisane poniżej. Każdy wiersz w pliku CSV odpowiada jednej skrzynce pocztowej i musi zawierać wartość każdego z tych atrybutów.

|**Atrybut**|**Opis**|**Wymagany?**|
|:-----|:-----|:-----|
|EmailAddress (Adres e-mail)  <br/> |Określa podstawowy adres e-mail SMTP lokalnej skrzynki pocztowej, na przykład mariap@contoso.com.  <br/> Użyj podstawowego adresu SMTP lokalnych skrzynek pocztowych, a nie identyfikatorów użytkowników z Microsoft 365. Jeśli na przykład domena lokalna nosi nazwę contoso.com, Microsoft 365 domena poczty e-mail Microsoft 365 nosi nazwę service.contoso.com, w pliku CSV należy użyć nazwy domeny contoso.com dla adresów e-mail.  <br/> |Wymagany  <br/> |
|Password (hasło)  <br/> |Hasło, które zostanie ustawione dla nowej skrzynki Microsoft 365 pocztowej. Wszelkie ograniczenia dotyczące haseł stosowane w Twojej organizacji Microsoft 365 mają zastosowanie również do haseł zawartych w pliku CSV.  <br/> |Opcjonalny  <br/> |
|ForceChangePassword (ForceChangePassword)  <br/> |Określa, czy użytkownik będzie musiał zmienić hasło po pierwszym zalogowaniu do nowej skrzynki Microsoft 365 pocztowej. Dla tego parametru użyj wartości **True** (prawda) lub **False** (fałsz). <br/> > [!NOTE]> Jeśli zaimplementowano rozwiązanie do logowania jednokrotnego (SSO), wdrażając w organizacji lokalnej usługi federujące Active Directory (AD FS) lub więcej, należy użyć wartości **False** dla atrybutu **ForceChangePassword** .          |Opcjonalny  <br/> |

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

Do utworzenia pliku CSV możesz użyć dowolnego edytora Excel tekstu lub aplikacji, na przykład Excel. Zapisz plik jako csv lub txt.

> [!NOTE]
> Jeśli plik CSV zawiera znaki specjalne lub niebędące znakami ASCII, zapisz go przy użyciu kodowania UTF-8 lub innego kodowania Unicode. W zależności od aplikacji zapisywanie pliku CSV przy użyciu kodowania UTF-8 lub innego kodowania Unicode może być łatwiejsze, gdy język używany w pliku CSV jest zgodne z ustawieniami lokalnymi systemu.

### <a name="step-3-create-a-migration-endpoint"></a>Krok 3. Tworzenie punktu końcowego migracji

Aby pomyślnie przeprowadzić migrację poczty e Microsoft 365 się ze źródłowym systemem poczty e-mail i komunikować się z nim. W tym celu program Microsoft 365 punkt końcowy migracji. Aby utworzyć punkt końcowy Outlook Anywhere przy użyciu programu PowerShell, na przykład w celu migracji etapowej połącz się z [programem Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Aby uzyskać pełną listę poleceń migracji, zobacz [Polecenia cmdlet przenoszenia i migracji](/powershell/exchange/).

Aby utworzyć punkt końcowy Outlook Anywhere o nazwie "StagedEndpoint" w programie Exchange Online PowerShell, uruchom następujące polecenia:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **New-MigrationEndpoint** , [zobaczNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> Polecenie **cmdlet New-MigrationEndpoint** umożliwia określenie bazy danych dla usługi za pomocą opcji **-TargetDatabase** . W przeciwnym razie baza danych jest losowo przypisywana z witryny usług federowanych Active Directory (AD FS) 2.0, w której znajduje się skrzynka pocztowa zarządzania.

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

W Exchange Online programu PowerShell uruchom następujące polecenie, aby wyświetlić informacje o punkcie końcowym migracji "StagedEndpoint":

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Krok 4. Tworzenie i uruchamianie partii migracji etapowej

Możesz użyć polecenia cmdlet **New-MigrationBatch** w programie Exchange Online PowerShell, aby utworzyć partię migracji do migracji cutover. Partię migracji można utworzyć i uruchomić automatycznie, uwzględniając _parametr Autostart_ . Ewentualnie możesz utworzyć partię migracji, a następnie uruchomić ją ręcznie później przy użyciu polecenia **cmdlet Start-MigrationBatch** . W tym przykładzie jest tworzona partia migracji o nazwie "StagedBatch1" i korzysta z punktu końcowego migracji utworzonego w poprzednim kroku.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

W tym przykładzie jest również tworzona partia migracji o nazwie "StagedBatch1" i korzysta z punktu końcowego migracji utworzonego w poprzednim kroku. Ponieważ parametr  _Autostart_ nie jest uwzględniony, partia migracji musi zostać uruchomiona ręcznie na pulpicie nawigacyjnym migracji lub przy użyciu polecenia cmdlet **Start-MigrationBatch** . Jak wspomniano wcześniej, jednocześnie może istnieć tylko jedna partia migracji.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić informacje o "StagedBatch1":

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Możesz również sprawdzić, czy partia została uruchomiona, uruchamiając następujące polecenie:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Aby uzyskać więcej informacji na temat **polecenia cmdlet Get-MigrationBatch** , [zobaczGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Krok 5. Konwertowanie lokalnych skrzynek pocztowych na użytkowników z włączoną obsługą poczty

Po pomyślnym przeprowadzeniu migracji partii skrzynek pocztowych potrzebny jest sposób na udostępnienie użytkownikom ich poczty. Użytkownik, którego skrzynka pocztowa została już zmigrowana, ma teraz zarówno lokalną skrzynkę pocztową, jak i skrzynkę pocztową w Microsoft 365. Użytkownicy, którzy mają skrzynkę pocztową Microsoft 365 nie będą już otrzymywać nowej poczty do swoich lokalnych skrzynek pocztowych.

Ponieważ migracje nie zostały jeszcze wykonane, nie można jeszcze skierować wszystkich użytkowników do Microsoft 365 e-mail. Co więc należy zrobić w przypadku użytkowników mających oba rodzaje skrzynek? Można przekonwertować lokalne skrzynki pocztowe, których migrację już przeprowadzono, na użytkowników z włączoną obsługą poczty. Po zmianie skrzynki pocztowej na użytkownika z włączoną obsługą poczty możesz skierować użytkownika do skrzynki Microsoft 365 e-mail zamiast do lokalnej skrzynki pocztowej.

Innym ważnym powodem konwertowania lokalnych skrzynek pocztowych na użytkowników z włączoną obsługą poczty jest zachowanie adresów serwera proxy ze skrzynek pocztowych programu Microsoft 365 przez skopiowanie adresów serwera proxy do użytkowników z włączoną obsługą poczty. W ten sposób możesz zarządzać użytkownikami w chmurze za pośrednictwem swojej organizacji lokalnej, korzystając z usługi Active Directory. Ponadto jeśli zdecydujesz się likwidować lokalną organizację programu Exchange Server po migracji wszystkich skrzynek pocztowych do programu Microsoft 365, adresy serwerów proxy skopiowane do użytkowników z włączoną obsługą poczty pozostaną w lokalnej usłudze Active Directory.

### <a name="step-6-delete-a-staged-migration-batch"></a>Krok 6. Usuwanie partii migracji etapowej

 Po pomyślnym zmigreniu wszystkich skrzynek pocztowych w partii migracji i przekonwertowaniu lokalnych skrzynek pocztowych w partii na użytkowników z włączoną obsługą poczty możesz usunąć partię migracji etapowej. Upewnij się, że poczta jest przesyłana dalej do Microsoft 365 pocztowych w partii migracji. Podczas usuwania partii migracji etapowej usługa migracji wyczyści wszystkie związane z nią rekordy, a następnie usunie partię migracji.

Aby usunąć partię migracji "StagedBatch1" w programie Exchange Online PowerShell, uruchom następujące polecenie.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Aby uzyskać więcej informacji na temat polecenia cmdlet **Remove-MigrationBatch** , [zobaczRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Sprawdzanie, czy wszystko działa

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić informacje o "IMAPBatch1":

```powershell
Get-MigrationBatch StagedBatch1
```

Polecenie zwróci partię migracji ze stanem Usuwanie lub zwróci błąd informujący, że partii migracji nie można odnaleźć, co oznacza, że partia została usunięta.

Aby uzyskać więcej informacji na temat **polecenia cmdlet Get-MigrationBatch** , [zobaczGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Krok 7. Przypisywanie licencji do Microsoft 365 użytkowników

Aktywuj Microsoft 365 użytkowników dla kont poddanych migracji, przypisując licencje. W przypadku nieprzypisania licencji skrzynka pocztowa zostanie wyłączona po upływie okresu prolongaty (30 dni). Aby przypisać licencję w centrum administracyjne platformy Microsoft 365, zobacz [Przypisywanie lub nieprzypisywanie licencji](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Krok 8. Wykonywanie zadań po migracji

- **Utwórz rekord DNS wykrywania automatycznego, aby użytkownicy mogli łatwo uzyskać dostęp do swoich skrzynek pocztowych.** Po zakończeniu migracji wszystkich lokalnych skrzynek pocztowych do usługi Microsoft 365 możesz skonfigurować rekord DNS wykrywania automatycznego dla swojej organizacji usługi Microsoft 365, aby umożliwić użytkownikom łatwe łączenie się ze swoimi nowymi skrzynkami pocztowymi usługi Microsoft 365 za pomocą usługi Outlook i klientów przenośnych. Ten nowy rekord DNS wykrywania automatycznego musi korzystać z tej samej przestrzeni nazw, która jest Microsoft 365 organizacji. Jeśli na przykład przestrzeń nazw w chmurze to cloud.contoso.com, należy utworzyć rekord DNS wykrywania automatycznego autodiscover.cloud.contoso.com.

    Microsoft 365 używa rekordu CNAME do wdrożenia usługi wykrywania automatycznego dla klientów Outlook przenośnych. Rekord CNAME wykrywania automatycznego musi zawierać następujące informacje:

  - **Alias:** autodiscover

  - **Wartość docelowa:** autodiscover.outlook.com

    Aby uzyskać więcej informacji, zobacz [Dodawanie rekordów DNS w celu połączenia domeny](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Zlikwiduj lokalne serwery programu Exchange.** Po sprawdzeniu, że wszystkie wiadomości e-mail są kierowane bezpośrednio do skrzynek pocztowych usługi Microsoft 365, i gdy nie musisz zachowywać lokalnej organizacji poczty e-mail ani nie planujesz zaimplementowania rozwiązania logowania jednokrotnego, możesz odinstalować program Exchange z serwerów i usunąć lokalną organizację Exchange.

    Aby uzyskać więcej informacji, zobacz następujące artykuły:

  - [Modyfikowanie lub usuwanie programu Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Jak usunąć organizację programu Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Jak odinstalować program Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
