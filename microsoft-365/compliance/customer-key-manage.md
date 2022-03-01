---
title: Zarządzanie kluczem klienta
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Po skonfigurowaniu klucza klienta dowiedz się, jak nim zarządzać, przywracając klucze AKV i zarządzając uprawnieniami oraz tworząc i przypisując zasady szyfrowania danych.
ms.openlocfilehash: 9dd333064c9fa121f8f1c99ffcd048f6b977dbf2
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998843"
---
# <a name="manage-customer-key"></a>Zarządzanie kluczem klienta

Po skonfigurowaniu klucza klienta dla Office 365 musisz utworzyć i przypisać jedną lub więcej zasad szyfrowania danych (DEP). Po przypisaniu sekcji DEP możesz zarządzać swoimi kluczami w sposób opisany w tym artykule. Więcej informacji o kluczu klienta można uzyskać w powiązanych tematach.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Tworzenie funkcji DEP do używania z wieloma obciążeniami pracą dla wszystkich użytkowników dzierżawy

Przed rozpoczęciem upewnij się, że ukończono zadania wymagane do skonfigurowania klienta. Aby uzyskać informacje, [zobacz Konfigurowanie klucza klienta](customer-key-set-up.md). Do utworzenia funkcji DEP są potrzebne  URS magazynu kluczy uzyskane podczas instalacji. Aby uzyskać informacje, [zobacz Uzyskiwanie URI dla każdego klucza magazynu kluczy platformy Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Aby utworzyć wielozadaniową dep, wykonaj następujące czynności:
  
1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Aby utworzyć polecenie cmdlet funkcji DEP, New-M365DataAtRestEncryptionPolicy polecenie cmdlet.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Gdzie:

   - *PolicyName* to nazwa, której chcesz użyć dla zasad. Nazwy nie mogą zawierać spacji. Na przykład: Contoso_Global.

   - *KeyVaultURI1* to URI pierwszego klucza zasad. Na przykład <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* to drugi klucz zasad, który jest URI. Na przykład <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. Dwie  URI należy oddzielić przecinkiem i spacją.

   - *Opis zasad* to przyjazny dla użytkownika opis zasad, ułatwiający zapamiętanie, do czego są one służące. Opis może zawierać spacje. Na przykład "Zasady główne dla wielu obciążeń dla wszystkich użytkowników w dzierżawie".

Przykład:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Przypisz zasady dotyczące wielu obciążeń pracą

Przypisz usługę DEP przy użyciu Set-M365DataAtRestEncryptionPolicyAssignment cmdlet. Po przypisaniu zasad szyfrowanie Microsoft 365 przy użyciu klucza wskazanego w funkcji DEP.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Gdzie *Nazwa_* zasad to nazwa zasad. Na przykład: Contoso_Global.

Przykład:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Tworzenie funkcji DEP do używania ze skrzynkami Exchange Online pocztowymi

Przed rozpoczęciem upewnij się, że ukończono zadania wymagane do skonfigurowania magazynu kluczy platformy Azure. Aby uzyskać informacje, [zobacz Konfigurowanie klucza klienta](customer-key-set-up.md). Te czynności można wykonać, łącząc się zdalnie z siecią Exchange Online pomocą Windows PowerShell.

Funkcja DEP jest skojarzona z zestawem kluczy przechowywanych w magazynie kluczy platformy Azure. Przypiszesz dep do skrzynki pocztowej w Microsoft 365. Microsoft 365 użyje kluczy wskazanych w zasadach do zaszyfrowania skrzynki pocztowej. Do utworzenia funkcji DEP są potrzebne  URS magazynu kluczy uzyskane podczas instalacji. Aby uzyskać informacje, [zobacz Uzyskiwanie URI dla każdego klucza magazynu kluczy platformy Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Pamiętaj! Podczas tworzenia funkcji DEP należy określić dwa klucze w dwóch różnych magazynach kluczy platformy Azure. Utwórz te klucze w dwóch osobnych regionach platformy Azure, aby zapewnić nadmiarowość geograficzną.

Aby utworzyć konto usługi DEP do używania ze skrzynką pocztową, wykonaj następujące czynności:
  
1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora programu Exchange Online w organizacji, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w Windows PowerShell okna.

2. Aby utworzyć polecenie DEP, użyj New-DataEncryptionPolicy cmdlet, wpisując następujące polecenie.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Gdzie:

   - *PolicyName* to nazwa, której chcesz użyć dla zasad. Nazwy nie mogą zawierać spacji. Na przykład: USA_mailboxes.

   - *Opis zasad* to przyjazny dla użytkownika opis zasad, ułatwiający zapamiętanie, do czego są one służące. Opis może zawierać spacje. Na przykład "Klucz główny dla skrzynek pocztowych w USA i na jego terytorium".

   - *KeyVaultURI1* to URI pierwszego klucza zasad. Na przykład <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* to drugi klucz zasad, który jest URI. Na przykład <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Dwie  URI należy oddzielić przecinkiem i spacją.

   Przykład:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Przypisywanie funkcji DEP do skrzynki pocztowej

Przypisz usługę DEP do skrzynki pocztowej za pomocą Set-Mailbox cmdlet. Po przypisaniu zasad możesz Microsoft 365 skrzynkę pocztową przy użyciu klucza wskazanego w funkcji DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Gdzie *MailboxIdParameters* określa skrzynkę pocztową użytkownika. Aby uzyskać więcej informacji na temat Set-Mailbox cmdlet, zobacz [Set-Mailbox](/powershell/module/exchange/set-mailbox).

W środowiskach hybrydowych możesz przypisać funkcji DEP do danych lokalnej skrzynki pocztowej synchronizowanych z Twoją Exchange Online dzierżawy. Aby przypisać dep do tych synchronizowanych danych skrzynki pocztowej, użyj polecenia cmdlet Set-MailUser cmdlet. Aby uzyskać więcej informacji na temat danych skrzynek pocztowych w środowisku hybrydowym, zobacz Lokalne skrzynki pocztowe używające aplikacji [Outlook dla systemów iOS i Android z nowoczesnym uwierzytelnianiem hybrydowym](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Gdzie *MailUserIdParameters* określa użytkownika poczty (nazywanego również użytkownikiem z włączoną obsługą poczty). Aby uzyskać więcej informacji na temat Set-MailUser cmdlet, zobacz [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>Tworzenie funkcji DEP do używania z SharePoint Online, OneDrive dla Firm i Teams plikach

Przed rozpoczęciem upewnij się, że ukończono zadania wymagane do skonfigurowania magazynu kluczy platformy Azure. Aby uzyskać informacje, [zobacz Konfigurowanie klucza klienta](customer-key-set-up.md).
  
Aby skonfigurować klucz klienta dla plików SharePoint Online, OneDrive dla Firm i Teams, wykonaj te czynności, zdalnie łącząc się z usługą SharePoint Online za pomocą Windows PowerShell.
  
Skojarz usługę DEP z zestawem kluczy przechowywanych w magazynie kluczy platformy Azure. Funkcja DEP jest stosowane do wszystkich danych w jednej lokalizacji geograficznej, nazywanej również geolokalizacji. W przypadku korzystania z funkcji wielolokalizacji firmy Office 365 można utworzyć jedną funkcję dep na lokalizację geograficzną z możliwością używania różnych kluczy dla każdego geolokalizacji. Jeśli nie korzystasz z wielu lokalizacji geograficznych, możesz utworzyć w organizacji jeden dep do użytku z plikami usługi SharePoint Online, OneDrive dla Firm i Teams danych. Microsoft 365 używa kluczy wskazanych w funkcji DEP do szyfrowania danych w tej lokalizacji geograficznej. Do utworzenia funkcji DEP są potrzebne  URS magazynu kluczy uzyskane podczas instalacji. Aby uzyskać informacje, [zobacz Uzyskiwanie URI dla każdego klucza magazynu kluczy platformy Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
Pamiętaj! Podczas tworzenia funkcji DEP należy określić dwa klucze w dwóch różnych magazynach kluczy platformy Azure. Utwórz te klucze w dwóch osobnych regionach platformy Azure, aby zapewnić nadmiarowość geograficzną.
  
Aby utworzyć usługę DEP, musisz zdalnie połączyć się z usługą SharePoint Online przy użyciu usługi Windows PowerShell.
  
1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego w organizacji możesz Połączenie do programu [SharePoint PowerShell w trybie online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. W Microsoft Office SharePoint Online zarządzania uruchom następujące polecenie cmdlet Register-SPODataEncryptionPolicy polecenie cmdlet:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Przykład:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a’
   ```

   Po zarejestrowaniu funkcji DEP szyfrowanie rozpoczyna się na danych w lokalizacji geograficznej. Szyfrowanie może trochę potrwać. Aby uzyskać więcej informacji na temat używania tego parametru, [zobacz Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Wyświetlanie utworzonych dezspektw dla skrzynek Exchange Online pocztowych

Aby wyświetlić listę wszystkich adresów IP utworzonych dla skrzynek pocztowych, użyj polecenia cmdlet programu Get-DataEncryptionPolicy PowerShell.

1. Używając konta służbowego z uprawnieniami administratora globalnego w twojej organizacji, połącz się z [programem Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aby zwrócić wszystkie ustawienia DEP w organizacji, uruchom polecenie cmdlet Get-DataEncryptionPolicy bez żadnych parametrów.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Aby uzyskać więcej informacji na Get-DataEncryptionPolicy cmdlet, zobacz [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Przypisywanie funkcji DEP przed przeprowadzeniem migracji skrzynki pocztowej do chmury

Podczas przypisywania funkcji DEP Microsoft 365 szyfruje zawartość skrzynki pocztowej przy użyciu przypisanego funkcji DEP podczas migracji. Ten proces jest bardziej efektywny niż migrowanie skrzynki pocztowej, przypisywanie funkcji DEP, a następnie oczekiwanie na proces szyfrowania, co może potrwać kilka godzin lub nawet dni.

Aby przypisać dep do skrzynki pocztowej przed przeprowadzeniem migracji do programu Office 365, uruchom polecenie cmdlet programu Set-MailUser w programie Exchange Online PowerShell:

1. Używając konta służbowego z uprawnieniami administratora globalnego w twojej organizacji, połącz się z [programem Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom Set-MailUser cmdlet.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Gdzie *funkcja GeneralMailboxOrMailUserIdParameters* określa skrzynkę pocztową, a wartość *DataEncryptionPolicyIdParameters* jest identyfikatorem funkcji DEP. Aby uzyskać więcej informacji na temat Set-MailUser cmdlet, zobacz [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Określanie funkcji DEP przypisanej do skrzynki pocztowej

Aby określić funkcja DEP przypisana do skrzynki pocztowej, użyj Get-MailboxStatistics cmdlet. Polecenie cmdlet zwraca wartość identyfikator unikatowy (GUID).
  
1. Używając konta służbowego z uprawnieniami administratora globalnego w twojej organizacji, połącz się z [programem Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Gdzie *funkcja GeneralMailboxOrMailUserIdParameters* określa skrzynkę pocztową, a funkcja DataEncryptionPolicyID zwraca identyfikator GUID funkcji DEP. Aby uzyskać więcej informacji na Get-MailboxStatistics cmdlet, zobacz [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. Uruchom Get-DataEncryptionPolicy cmdlet, aby znaleźć przyjazną nazwę funkcji DEP, do której jest przypisana skrzynka pocztowa.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Gdzie *identyfikator GUID* to identyfikator GUID zwracany przez Get-MailboxStatistics cmdlet w poprzednim kroku.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Sprawdzanie, czy klucz klienta zakończył szyfrowanie

Niezależnie od tego, czy masz klucz klienta, przypisano nowy element DEP, czy zmigrowałeś skrzynkę pocztową, wykonaj czynności opisane w tej sekcji, aby upewnić się, że szyfrowanie się zakończy.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Sprawdzanie, czy ukończono szyfrowanie skrzynek Exchange Online pocztowych

Zaszyfrowanie skrzynki pocztowej może zająć trochę czasu. Aby usługa szyfrować skrzynkę pocztową po raz pierwszy, należy również całkowicie przenieść ją z jednej bazy danych do drugiej.
  
Użyj Get-MailboxStatistics cmdlet, aby określić, czy skrzynka pocztowa jest zaszyfrowana.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

Właściwość IsEncrypted zwraca wartość true, jeśli  skrzynka pocztowa jest zaszyfrowana, lub wartość  fałsz, jeśli skrzynka pocztowa nie jest zaszyfrowana. Czas ukończenia przenoszenia skrzynek pocztowych zależy od liczby skrzynek pocztowych, do których po raz pierwszy przypisuje się funkcji DEP, oraz rozmiaru skrzynek pocztowych. Jeśli skrzynki pocztowe nie zostały zaszyfrowane po tygodniu od czasu przydzielenia funkcji DEP, skontaktuj się z firmą Microsoft.

Polecenie cmdlet New-MoveRequest nie jest już dostępne w przypadku przenoszenia lokalnych skrzynek pocztowych. Dodatkowe informacje [można znaleźć w](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) tym komunikacie.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Sprawdzanie, czy ukończono szyfrowanie SharePoint plików online, OneDrive dla Firm i Teams internetowych

Sprawdź stan szyfrowania, uruchamiając polecenie cmdlet Get-SPODataEncryptionPolicy w następujący sposób:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Dane wyjściowe tego polecenia cmdlet obejmują:
  
- URI klucza podstawowego.

- URI klucza pomocniczego.

- Stan szyfrowania dla lokalizacji geograficznej. Możliwe stany:

  - **Wyrejestrowane:** Szyfrowanie przy pomocy klucza klienta nie zostało jeszcze zastosowane.

  - **Rejestrowanie:** Zastosowano szyfrowanie przy użyciu klucza klienta i pliki są w trakcie procesu szyfrowania. Jeśli kluczem geolokalizacji jest rejestrowanie, zostaną również wyświetlone informacje o tym, jaki procent witryn w lokalizacji geograficznej został ukończony, aby można było monitorować postęp szyfrowania.

  - **Zarejestrowane:** Zastosowano szyfrowanie przy użyciu klucza klienta i wszystkie pliki we wszystkich witrynach zostały zaszyfrowane.

  - **Przewczasanie:** Trwa wycofywanie klucza. Jeśli klucz geolokalizacji jest przewczasowy, wyświetlane są również informacje o tym, jaki procent witryn wykonał operację rzutowania kluczy, aby można było monitorować postęp.

- Zostanie również wyprowadzona procentowa wartość procentowa witryn, które do niego wnoszą.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Uzyskaj szczegółowe informacje na temat dezspektów, których używasz z wieloma obciążeniami pracą

Aby uzyskać szczegółowe informacje o wszystkich kontach DEP utworzonych do użycia z wieloma obciążeniami pracą, wykonaj następujące czynności:

1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

   - Aby zwrócić listę wszystkich adresów DEP z wieloma obciążeniami w organizacji, uruchom to polecenie.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Aby zwrócić szczegóły dotyczące określonego funkcji DEP, uruchom to polecenie. W tym przykładzie funkcja DEP zwraca szczegółowe informacje o nazwie "Contoso_Global".

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Uzyskiwanie informacji o zadaniach funkcji DEP z wieloma obciążeniami pracą

Aby dowiedzieć się, która funkcja DEP jest obecnie przypisana do Twojej dzierżawy, wykonaj poniższe czynności. 

1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Wpisz to polecenie.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Wyłączanie funkcji DEP z wieloma obciążeniami pracą

Zanim wyłączysz funkcję DEP z wieloma obciążeniami, cofniesz przypisanie funkcji DEP z obciążeń w dzierżawie. Aby wyłączyć funkcję DEP używaną z wieloma obciążeniami pracą, wykonaj następujące czynności:

1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Uruchom Set-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Gdzie *nazwa_* zasad to nazwa lub unikatowy identyfikator zasad. Na przykład: Contoso_Global.

Przykład:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Przywracanie kluczy magazynu kluczy platformy Azure

Przed wykonaniem przywracania użyj funkcji odzyskiwania zapewnianych przez "miękkie usunięcie". Wszystkie klucze używane z kluczem klienta muszą mieć włączoną funkcję "miękkiego usunięcia". Niechętne usuwanie działa jak kosz i pozwala na odzyskanie do 90 dni bez potrzeby przywracania. Przywracanie powinno być wymagane tylko w skrajnych lub nietypowych okolicznościach, na przykład w przypadku zgubionego klucza lub magazynu kluczy. Jeśli musisz przywrócić klucz do użycia z kluczem klienta, w programie Azure PowerShell uruchom polecenie cmdlet Restore-AzureKeyVaultKey w następujący sposób:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Przykład:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Jeśli magazyn kluczy już zawiera klucz o tej samej nazwie, operacja przywracania kończy się niepowodzeniem. Restore-AzKeyVaultKey wszystkie wersje klucza i wszystkie metadane klucza, w tym nazwę klucza.
  
## <a name="manage-key-vault-permissions"></a>Zarządzanie uprawnieniami magazynu kluczy

Dostępnych jest kilka cmdlet umożliwiających wyświetlanie i, w razie potrzeby, usuwanie uprawnień do magazynu kluczy. Może być konieczne usunięcie uprawnień, na przykład gdy pracownik odchodzi z zespołu. W przypadku każdego z tych zadań należy użyć Azure PowerShell. Aby uzyskać informacje Azure PowerShell, zobacz [Omówienie Azure PowerShell](/powershell/azure/).

Aby wyświetlić uprawnienia magazynu kluczy, uruchom Get-AzKeyVault cmdlet.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Przykład:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Aby usunąć uprawnienia administratora, uruchom polecenie cmdlet Remove-AzKeyVaultAccessPolicy cmdlet:
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Przykład:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Wycofywanie z klucza klienta do kluczy zarządzanych przez firmę Microsoft

Jeśli chcesz przywrócić klucze zarządzane przez firmę Microsoft, możesz to zrobić. Po wy pracowaniu dane są ponownie szyfrowane przy użyciu domyślnego szyfrowania obsługiwanego przez poszczególne obciążenia pracą. Na przykład Exchange Online domyślne szyfrowanie przy użyciu kluczy zarządzanych przez firmę Microsoft.

> [!IMPORTANT]
> Wyniesienie to nie to samo co przeczyszczanie danych. Usunięcie danych trwale szyfruje dane organizacji z Microsoft 365, wye dołączanie nie. Nie można przeprowadzić przeczyszczania danych w przypadku zasad obciążenia pracą o wielu obciążeniach.

Jeśli nie chcesz już używać klucza klienta do przypisywania wielu obciążeń pracą, musisz kontaktować się z pomocą techniczną firmy Microsoft z prośbą o "odłogowanie" z klucza klienta. Poproś zespół pomocy technicznej o zgłoszenie żądania usługi do zespołu Microsoft 365 klienta. Jeśli masz jakieś pytania, m365-ck@service.microsoft.com się z tomem.

Jeśli nie chcesz już szyfrować poszczególnych skrzynek pocztowych przy użyciu dezp. na poziomie skrzynki pocztowej, możesz usunąć dezsignowanie wiadomości DEPs poziomu skrzynki pocztowej ze wszystkich skrzynek pocztowych.

Aby nieprzypisać dezpopsy skrzynek pocztowych, użyj Set-Mailbox cmdlet programu PowerShell.

1. Używając konta służbowego z uprawnieniami administratora globalnego w twojej organizacji, połącz się z [programem Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom Set-Mailbox cmdlet.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

Uruchomienie tego polecenia cmdlet oznacza aktualnie przypisany tryb DEP i ponownie szyfruje skrzynkę pocztową przy użyciu funkcji DEP skojarzonej z domyślnymi kluczami zarządzanymi przez firmę Microsoft. Nie można nieprzypisać funkcji DEP używanych przez klucze zarządzane przez firmę Microsoft. Jeśli nie chcesz używać kluczy zarządzanych przez firmę Microsoft, możesz przypisać do skrzynki pocztowej inny klucz klienta dep.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Odwoływanie klawiszy i rozpoczynanie procesu przeczyszczania danych

Można sterować odwołaniami wszystkich kluczy głównych, łącznie z kluczem dostępności. Klucz klienta zapewnia kontrolę nad aspektem planowania wyjścia z wymogów prawnych. Jeśli zdecydujesz się odwołać klucze w celu przeczyszczenia danych i opuszczenia usługi, usługa usuwa klucz dostępności po zakończeniu procesu przeczyszczania danych. Ta obsługa jest obsługiwana przez dezpozytywów kluczy klienta przypisanych do poszczególnych skrzynek pocztowych.

Microsoft 365 inspekcji danych i weryfikacji ścieżki przeczyszczania danych. Aby uzyskać więcej informacji, zobacz Raport SOC 2 SSAE 18 dostępny w Portalu [zaufania usług](https://servicetrust.microsoft.com/). Ponadto firma Microsoft zaleca korzystanie z następujących dokumentów:

- [Przewodnik po ocenach ryzyka i zgodności dla instytucji finansowych w chmurze firmy Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [O365 Exit Planning Considerations](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Usuwanie funkcji DEP z wieloma obciążeniami nie jest obsługiwane w przypadku Microsoft 365 klienta. Funkcja DEP z wieloma obciążeniami jest używana do szyfrowania danych w wielu obciążeniach pracą u wszystkich użytkowników dzierżawy. Przeczyszczenie takiego funkcji DEP spowoduje, że dane z wielu obciążeń staną się niedostępne. Jeśli zdecydujesz się na Microsoft 365 usług, możesz podążać za ścieżką usuwania dzierżawy w trakcie udokumentowanych procesów. Zobacz[, jak usunąć dzierżawę w Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Odwoływanie kluczy klienta i klucza dostępności dla Exchange Online i Skype dla firm

Inicjacja ścieżki przeczyszczania danych dla funkcji Exchange Online i Skype dla firm powoduje ustawienie trwałego żądania przeczyszczania danych w funkcji DEP. Spowoduje to trwałe usunięcie zaszyfrowanych danych ze skrzynek pocztowych, do których przypisano ten element DEP.

Ponieważ polecenie cmdlet programu PowerShell można uruchamiać tylko dla jednego funkcji DEP na raz, przed zainicjowaniem ścieżki przeczyszczania danych rozważ ponowne przypisanie jednego funkcji DEP do wszystkich skrzynek pocztowych.

> [!WARNING]
> Nie usuwaj podzbioru skrzynek pocztowych za pomocą ścieżki przeczyszczania danych. Ten proces jest przeznaczony tylko dla klientów opuszczających usługę.

Aby zainicjować ścieżkę przeczyszczania danych, wykonaj następujące czynności:

1. Usuń uprawnienia zawijania i cofania zawijania dla usługi "Usługa O365 Exchange Online" z magazynów kluczy platformy Azure.

2. Używając konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z [programem Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. Dla każdego polecenia cmdlet Set-DataEncryptionPolicy zawierającego skrzynki pocztowe, które chcesz usunąć, uruchom następujące polecenie cmdlet [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) .

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Jeśli to polecenie nie powiedzie się, upewnij się, że usunięto uprawnienia dostępu do obu Exchange Online w magazynie kluczy platformy Azure, jak określono wcześniej w tym zadaniu.Po skonfigurowaniu przełącznika PermanentDataPurgeRequested za pomocą polecenia cmdlet programu Set-DataEncryptionPolicy nie będzie już można przypisywać tego funkcji DEP do skrzynek pocztowych.

4. Skontaktuj się z pomocą techniczną firmy Microsoft i poproś o dokument eDocument do przeczyszczania danych.

    Na Twoje żądanie firma Microsoft wysyła do Ciebie dokument prawny w celu potwierdzenia i autoryzacji usunięcia danych. Osoba w Twojej organizacji, która podczas dołączania do programu FastTrack jako osoba zatwierdzająca musi podpisać ten dokument. Zazwyczaj jest to kierownik lub inna osoba wyznaczona w Twojej firmie, która jest prawnie upoważniona do podpisania dokumentów w imieniu Twojej organizacji.

5. Po podpisaniu dokumentu prawnego przez przedstawiciela zwróć go do firmy Microsoft (zwykle za pomocą podpisu eDoc).

    Po otrzymaniu dokumentu prawnego firma Microsoft uruchamia polecenia cmdlet w celu uruchomienia oczyszczania danych, co najpierw powoduje usunięcie zasad, oznacza skrzynki pocztowe do trwałego usunięcia, a następnie usuwa klucz dostępności. Po zakończeniu procesu przeczyszczania danych dane są wyczyszalne, są niedostępne Exchange Online i nie można ich odzyskać.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Odwoływanie kluczy klienta i klucza dostępności dla plików SharePoint Online, OneDrive dla Firm i Teams klientów

Aby zainicjować ścieżkę przeczyszczania danych dla plików SharePoint Online, OneDrive dla Firm i Teams, wykonaj następujące czynności:

1. Odwołaj dostęp do magazynu kluczy platformy Azure. Wszyscy administratorzy magazynu kluczy muszą zgodzić się na cofnięcie dostępu.

   Nie usuwasz magazynu kluczy platformy Azure dla usługi SharePoint Online. Magazyny kluczy mogą być udostępniane między kilkoma SharePoint dzierżawami usługi Online i dezp.

2. Skontaktuj się z firmą Microsoft, aby usunąć klucz dostępności.

    Gdy skontaktujesz się z firmą Microsoft w celu usunięcia klucza dostępności, wyślemy Ci dokument prawny. Osoba w Twojej organizacji, która podczas dołączania do programu FastTrack jako osoba zatwierdzająca musi podpisać ten dokument. Zazwyczaj jest to kierownik lub inna osoba wyznaczona w Twojej firmie, która jest prawnie upoważniona do podpisywania dokumentów w imieniu Twojej organizacji.

3. Gdy przedstawiciel podpisze dokument prawny, zwróć go do firmy Microsoft (zwykle za pomocą podpisu eDoc).

   Po otrzymaniu dokumentu prawnego przez firmę Microsoft uruchamiamy polecenia cmdlet w celu uruchomienia oczyszczania danych, które wykonuje usuwanie szyfrowania klucza dzierżawy, klucza witryny i wszystkich poszczególnych kluczy poszczególnych dokumentów, co nieodwołalnie przerywa hierarchię kluczy. Po zakończeniu oczyszczania danych polecenia cmdlet dane zostały wyczyszone.

## <a name="related-articles"></a>Artykuły pokrewne

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Informacje o kluczu dostępności](customer-key-availability-key-understand.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Obracanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md)

- [Skrytka klienta](customer-lockbox-requests.md)

- [Szyfrowanie usługi](office-365-service-encryption.md)
