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
description: Po skonfigurowaniu klucza klienta dowiedz się, jak nim zarządzać, przywracając klucze akv oraz zarządzając uprawnieniami oraz tworząc i przypisując zasady szyfrowania danych.
ms.openlocfilehash: a1fab2694be866acd6035af90929b5ab690da031
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663475"
---
# <a name="manage-customer-key"></a>Zarządzanie kluczem klienta

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po skonfigurowaniu klucza klienta należy utworzyć i przypisać co najmniej jedną zasadę szyfrowania danych (DEP). Po przypisaniu adresów IP możesz zarządzać kluczami zgodnie z opisem w tym artykule. Dowiedz się więcej o kluczu klienta w powiązanych tematach.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Tworzenie programu DEP do użycia z wieloma obciążeniami dla wszystkich użytkowników dzierżawy

Przed rozpoczęciem upewnij się, że wykonano zadania wymagane do skonfigurowania klucza klienta. Aby uzyskać informacje, zobacz [Konfigurowanie klucza klienta](customer-key-set-up.md). Aby utworzyć program DEP, potrzebne są identyfikatory URI Key Vault uzyskane podczas instalacji. Aby uzyskać informacje, zobacz [Uzyskiwanie identyfikatora URI dla każdego klucza Key Vault platformy Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Aby utworzyć wielozadaniowy program DEP, wykonaj następujące kroki:
  
1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Aby utworzyć program DEP, użyj polecenia cmdlet New-M365DataAtRestEncryptionPolicy.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Gdzie:

   - *PolicyName* to nazwa, która ma być używana dla zasad. Nazwy nie mogą zawierać spacji. Na przykład Contoso_Global.

   - *KeyVaultURI1* to identyfikator URI pierwszego klucza w zasadach. Na przykład <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* to identyfikator URI drugiego klucza w zasadach. Na przykład <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. Rozdziel dwa identyfikatory URI przecinkiem i spacji.

   - *Opis zasad* to przyjazny dla użytkownika opis zasad, który pomoże Ci zapamiętać, do czego służy zasada. W opisie można dołączyć spacje. Na przykład "Zasady główne dla wielu obciążeń dla wszystkich użytkowników w dzierżawie".

Przykład:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Przypisywanie zasad obejmujących wiele obciążeń

Przypisz program DEP przy użyciu polecenia cmdlet Set-M365DataAtRestEncryptionPolicyAssignment. Po przypisaniu zasad Microsoft 365 szyfruje dane przy użyciu klucza zidentyfikowanego w programie DEP.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Where *PolicyName* to nazwa zasad. Na przykład Contoso_Global.

Przykład:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Tworzenie programu DEP do użycia ze skrzynkami pocztowymi Exchange Online

Przed rozpoczęciem upewnij się, że wykonano zadania wymagane do skonfigurowania usługi Azure Key Vault. Aby uzyskać informacje, zobacz [Konfigurowanie klucza klienta](customer-key-set-up.md). Wykonaj te kroki, zdalnie nawiązując połączenie z Exchange Online za pomocą Windows PowerShell.

Program DEP jest skojarzony z zestawem kluczy przechowywanych w usłudze Azure Key Vault. Program DEP jest przypisywany do skrzynki pocztowej w Microsoft 365. Microsoft 365 będzie następnie używać kluczy zidentyfikowanych w zasadach do szyfrowania skrzynki pocztowej. Aby utworzyć program DEP, potrzebne są identyfikatory URI Key Vault uzyskane podczas instalacji. Aby uzyskać informacje, zobacz [Uzyskiwanie identyfikatora URI dla każdego klucza Key Vault platformy Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Pamiętaj! Podczas tworzenia programu DEP należy określić dwa klucze w dwóch różnych usługach Azure Key Vault. Utwórz te klucze w dwóch oddzielnych regionach platformy Azure, aby zapewnić nadmiarowość geograficzną.

Aby utworzyć program DEP do użycia ze skrzynką pocztową, wykonaj następujące kroki:
  
1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego lub administratora Exchange Online w organizacji [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Aby utworzyć program DEP, użyj polecenia cmdlet New-DataEncryptionPolicy, wpisując następujące polecenie.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Gdzie:

   - *PolicyName* to nazwa, która ma być używana dla zasad. Nazwy nie mogą zawierać spacji. Na przykład USA_mailboxes.

   - *Opis zasad* to przyjazny dla użytkownika opis zasad, który pomoże Ci zapamiętać, do czego służy zasada. W opisie można dołączyć spacje. Na przykład "Klucz główny dla skrzynek pocztowych w Stanach Zjednoczonych i ich terytoriach".

   - *KeyVaultURI1* to identyfikator URI pierwszego klucza w zasadach. Na przykład <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* to identyfikator URI drugiego klucza w zasadach. Na przykład <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Rozdziel dwa identyfikatory URI przecinkiem i spacji.

   Przykład:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-DataEncryptionPolicy](/powershell/module/exchange/new-dataencryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Przypisywanie programu DEP do skrzynki pocztowej

Przypisz program DEP do skrzynki pocztowej przy użyciu polecenia cmdlet Set-Mailbox. Po przypisaniu zasad Microsoft 365 może zaszyfrować skrzynkę pocztową przy użyciu klucza zidentyfikowanego w programie DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Gdzie *MailboxIdParameter* określa skrzynkę pocztową użytkownika. Aby uzyskać więcej informacji na temat polecenia cmdlet Set-Mailbox, zobacz [Set-Mailbox (Set-Mailbox](/powershell/module/exchange/set-mailbox)).

W środowiskach hybrydowych można przypisać program DEP do lokalnych danych skrzynki pocztowej, które są synchronizowane z dzierżawą Exchange Online. Aby przypisać program DEP do tych zsynchronizowanych danych skrzynki pocztowej, użyjesz polecenia cmdlet Set-MailUser. Aby uzyskać więcej informacji na temat danych skrzynki pocztowej w środowisku [hybrydowym, zobacz lokalne skrzynki pocztowe korzystające z Outlook dla iOS i Android z nowoczesnym uwierzytelnianiem hybrydowym](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Gdzie *MailUserIdParameter* określa użytkownika poczty (znanego również jako użytkownik obsługujący pocztę). Aby uzyskać więcej informacji na temat polecenia cmdlet Set-MailUser, zobacz [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>Tworzenie programu DEP do użycia z plikami SharePoint Online, OneDrive dla Firm i Teams

Przed rozpoczęciem upewnij się, że wykonano zadania wymagane do skonfigurowania usługi Azure Key Vault. Aby uzyskać informacje, zobacz [Konfigurowanie klucza klienta](customer-key-set-up.md).
  
Aby skonfigurować klucz klienta dla plików SharePoint Online, OneDrive dla Firm i Teams, wykonaj te kroki, zdalnie nawiązując połączenie z usługą SharePoint Online za pomocą usługi Windows PowerShell.
  
Program DEP można skojarzyć z zestawem kluczy przechowywanych w usłudze Azure Key Vault. Program DEP jest stosowany do wszystkich danych w jednej lokalizacji geograficznej, nazywanej również obszarem geograficznym. Jeśli używasz funkcji wielu obszarów geograficznych Office 365, możesz utworzyć jeden program DEP na obszar geograficzny z możliwością używania różnych kluczy na dane geograficzne. Jeśli nie używasz wielu obszarów geograficznych, możesz utworzyć jeden program DEP w organizacji do użycia z plikami SharePoint Online, OneDrive dla Firm i Teams. Microsoft 365 używa kluczy zidentyfikowanych w programie DEP do szyfrowania danych w tym obszarze geograficznym. Aby utworzyć program DEP, potrzebne są identyfikatory URI Key Vault uzyskane podczas instalacji. Aby uzyskać informacje, zobacz [Uzyskiwanie identyfikatora URI dla każdego klucza Key Vault platformy Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
Pamiętaj! Podczas tworzenia programu DEP należy określić dwa klucze w dwóch różnych usługach Azure Key Vault. Utwórz te klucze w dwóch oddzielnych regionach platformy Azure, aby zapewnić nadmiarowość geograficzną.
  
Aby utworzyć program DEP, musisz zdalnie nawiązać połączenie z usługą SharePoint Online przy użyciu Windows PowerShell.
  
1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego w organizacji [Połączenie SharePoint programu PowerShell online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. W powłoce zarządzania Microsoft Office SharePoint Online uruchom polecenie cmdlet Register-SPODataEncryptionPolicy w następujący sposób:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Przykład:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a'
   ```

   Podczas rejestrowania programu DEP rozpoczyna się szyfrowanie danych w obszarze geograficznym. Szyfrowanie może zająć trochę czasu. Aby uzyskać więcej informacji na temat korzystania z tego parametru, zobacz [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Wyświetlanie utworzonych adresów DEP dla Exchange Online skrzynek pocztowych

Aby wyświetlić listę wszystkich adresów IP utworzonych dla skrzynek pocztowych, użyj polecenia cmdlet Get-DataEncryptionPolicy programu PowerShell.

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aby zwrócić wszystkie adresy DEPs w organizacji, uruchom polecenie cmdlet Get-DataEncryptionPolicy bez żadnych parametrów.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Aby uzyskać więcej informacji na temat polecenia cmdlet Get-DataEncryptionPolicy, zobacz [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Przypisywanie programu DEP przed migracją skrzynki pocztowej do chmury

Podczas przypisywania programu DEP Microsoft 365 szyfruje zawartość skrzynki pocztowej przy użyciu przypisanego programu DEP podczas migracji. Ten proces jest bardziej wydajny niż migrowanie skrzynki pocztowej, przypisywanie programu DEP, a następnie oczekiwanie na przeprowadzenie szyfrowania, co może potrwać wiele godzin lub ewentualnie dni.

Aby przypisać program DEP do skrzynki pocztowej przed migracją do Office 365, uruchom polecenie cmdlet Set-MailUser w programie Exchange Online programu PowerShell:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-MailUser.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Gdzie *GeneralMailboxOrMailUserIdParameter* określa skrzynkę pocztową, a *DataEncryptionPolicyIdParameter* jest identyfikatorem programu DEP. Aby uzyskać więcej informacji na temat polecenia cmdlet Set-MailUser, zobacz [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Określanie programu DEP przypisanego do skrzynki pocztowej

Aby określić program DEP przypisany do skrzynki pocztowej, użyj polecenia cmdlet Get-MailboxStatistics. Polecenie cmdlet zwraca unikatowy identyfikator (GUID).
  
1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Gdzie *GeneralMailboxOrMailUserIdParameter* określa skrzynkę pocztową i DataEncryptionPolicyID zwraca identyfikator GUID programu DEP. Aby uzyskać więcej informacji na temat polecenia cmdlet Get-MailboxStatistics, zobacz [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. Uruchom polecenie cmdlet Get-DataEncryptionPolicy, aby dowiedzieć się przyjaznej nazwy programu DEP, do której jest przypisana skrzynka pocztowa.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Gdzie *identyfikator GUID* to identyfikator GUID zwrócony przez polecenie cmdlet Get-MailboxStatistics w poprzednim kroku.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Sprawdź, czy klucz klienta zakończył szyfrowanie

Niezależnie od tego, czy masz wdrożony klucz klienta, przypisano nowy program DEP, czy zmigrowaliśmy skrzynkę pocztową, wykonaj kroki opisane w tej sekcji, aby upewnić się, że szyfrowanie zostanie zakończone.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Weryfikowanie zakończenia szyfrowania dla skrzynek pocztowych Exchange Online

Szyfrowanie skrzynki pocztowej może zająć trochę czasu. W przypadku szyfrowania po raz pierwszy skrzynka pocztowa musi również całkowicie przenieść się z jednej bazy danych do innej, aby usługa mogła zaszyfrować skrzynkę pocztową.
  
Użyj polecenia cmdlet Get-MailboxStatistics, aby określić, czy skrzynka pocztowa jest szyfrowana.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

Właściwość IsEncrypted zwraca wartość **true** , jeśli skrzynka pocztowa jest zaszyfrowana, oraz wartość **false** , jeśli skrzynka pocztowa nie jest zaszyfrowana. Czas zakończenia przenoszenia skrzynki pocztowej zależy od liczby skrzynek pocztowych, do których po raz pierwszy przypisano program DEP, oraz od rozmiaru skrzynek pocztowych. Jeśli skrzynki pocztowe nie zostały zaszyfrowane po tygodniu od momentu przypisania programu DEP, skontaktuj się z firmą Microsoft.

Polecenie cmdlet New-MoveRequest nie jest już dostępne dla lokalnych ruchów skrzynki pocztowej. Aby uzyskać dodatkowe informacje, zapoznaj się z [tym ogłoszeniem](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) .

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Weryfikowanie zakończenia szyfrowania plików SharePoint Online, OneDrive dla Firm i Teams

Sprawdź stan szyfrowania, uruchamiając polecenie cmdlet Get-SPODataEncryptionPolicy w następujący sposób:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Dane wyjściowe z tego polecenia cmdlet obejmują:
  
- Identyfikator URI klucza podstawowego.

- Identyfikator URI klucza pomocniczego.

- Stan szyfrowania dla obszaru geograficznego. Możliwe stany obejmują:

  - **Niezarejestrowanych:** Szyfrowanie klucza klienta nie zostało jeszcze zastosowane.

  - **Rejestrowanie:** Zastosowano szyfrowanie klucza klienta, a pliki są w trakcie szyfrowania. Jeśli klucz dla obszaru geograficznego jest rejestrowany, zostaną również wyświetlone informacje o tym, jaki procent lokacji w obszarze geograficznym został ukończony, aby można było monitorować postęp szyfrowania.

  - **Zarejestrowany:** Zastosowano szyfrowanie klucza klienta, a wszystkie pliki we wszystkich witrynach zostały zaszyfrowane.

  - **Toczenia:** Trwa przerzucanie kluczy. Jeśli klucz dla obszaru geograficznego jest stopniowany, zostaną również wyświetlone informacje o tym, jaki procent lokacji zakończył operację rzutowania kluczy, aby można było monitorować postęp.

- Spowoduje to również wygenerowanie procentu dołączonych witryn.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Uzyskiwanie szczegółowych informacji o adresach IP używanych z wieloma obciążeniami

Aby uzyskać szczegółowe informacje na temat wszystkich adresów IP utworzonych do użycia z wieloma obciążeniami, wykonaj następujące kroki:

1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

   - Aby zwrócić listę wszystkich adresów IP z wieloma obciążeniami w organizacji, uruchom to polecenie.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Aby zwrócić szczegółowe informacje o określonym programie DEP, uruchom to polecenie. Ten przykład zwraca szczegółowe informacje dotyczące programu DEP o nazwie "Contoso_Global".

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Uzyskiwanie informacji o przypisywaniu programu DEP dla wielu obciążeń

Aby dowiedzieć się, który program DEP jest obecnie przypisany do dzierżawy, wykonaj następujące kroki. 

1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Wpisz to polecenie.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Wyłączanie programu DEP z wieloma obciążeniami

Przed wyłączeniem programu DEP z wieloma obciążeniami usuń przypisanie programu DEP z obciążeń w dzierżawie. Aby wyłączyć program DEP używany z wieloma obciążeniami, wykonaj następujące kroki:

1. Na komputerze lokalnym przy użyciu konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Uruchom polecenie cmdlet Set-M365DataAtRestEncryptionPolicy.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Gdzie *PolicyName* jest nazwą lub unikatowym identyfikatorem zasad. Na przykład Contoso_Global.

Przykład:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Przywracanie kluczy Key Vault platformy Azure

Przed wykonaniem przywracania użyj funkcji odzyskiwania udostępnianych przez usuwanie nietrwałe. Wszystkie klucze używane z kluczem klienta muszą mieć włączone usuwanie nietrwałe. Usuwanie nietrwałe działa jak kosz i umożliwia odzyskiwanie przez maksymalnie 90 dni bez konieczności przywracania. Przywracanie powinno być wymagane tylko w ekstremalnych lub nietypowych okolicznościach, na przykład w przypadku utraty klucza lub magazynu kluczy. Jeśli musisz przywrócić klucz do użycia z kluczem klienta, w Azure PowerShell uruchom polecenie cmdlet Restore-AzureKeyVaultKey w następujący sposób:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Przykład:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Jeśli magazyn kluczy zawiera już klucz o tej samej nazwie, operacja przywracania kończy się niepowodzeniem. Restore-AzKeyVaultKey przywraca wszystkie wersje klucza i wszystkie metadane klucza, w tym nazwę klucza.
  
## <a name="manage-key-vault-permissions"></a>Zarządzanie uprawnieniami magazynu kluczy

Dostępnych jest kilka poleceń cmdlet, które umożliwiają wyświetlanie i, w razie potrzeby, usuwanie uprawnień magazynu kluczy. Może być konieczne usunięcie uprawnień, na przykład po opuszczeniu zespołu przez pracownika. W przypadku każdego z tych zadań użyjesz Azure PowerShell. Aby uzyskać informacje o Azure PowerShell, zobacz [Omówienie Azure PowerShell](/powershell/azure/).

Aby wyświetlić uprawnienia magazynu kluczy, uruchom polecenie cmdlet Get-AzKeyVault.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Przykład:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Aby usunąć uprawnienia administratora, uruchom polecenie cmdlet Remove-AzKeyVaultAccessPolicy:
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Przykład:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Wycofywanie klucza klienta z klucza do kluczy zarządzanych przez firmę Microsoft

Jeśli musisz wrócić do kluczy zarządzanych przez firmę Microsoft, możesz to zrobić. Po odłączeniu dane są ponownie szyfrowane przy użyciu domyślnego szyfrowania obsługiwanego przez poszczególne obciążenia. Na przykład Exchange Online obsługuje domyślne szyfrowanie przy użyciu kluczy zarządzanych przez firmę Microsoft.

> [!IMPORTANT]
> Odłączanie nie jest tym samym, co przeczyszczanie danych. Przeczyszczanie danych trwale usuwa dane organizacji z Microsoft 365, a odłączanie nie. Nie można przeprowadzić przeczyszczania danych dla zasad wielu obciążeń.

Jeśli zdecydujesz się już nie używać klucza klienta do przypisywania adresów DEPs z wieloma obciążeniami, musisz skontaktować się z pomocą techniczną firmy Microsoft z prośbą o "odłączenie" od klucza klienta. Poproś zespół pomocy technicznej o zgłoszenie żądania obsługi do zespołu Microsoft Purview Customer Key. Jeśli masz jakiekolwiek pytania, skontaktuj się z m365-ck@service.microsoft.com.

Jeśli nie chcesz już szyfrować poszczególnych skrzynek pocztowych przy użyciu adresów DEPs na poziomie skrzynki pocztowej, możesz anulować przypisanie adresów DEPs na poziomie skrzynki pocztowej ze wszystkich skrzynek pocztowych.

Aby anulować przypisanie adresów DEPs skrzynki pocztowej, użyj polecenia cmdlet programu PowerShell Set-Mailbox.

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-Mailbox.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

Uruchomienie tego polecenia cmdlet powoduje anulowanie przypisania aktualnie przypisanego programu DEP i ponowne odszyfrowanie skrzynki pocztowej przy użyciu programu DEP skojarzonego z domyślnymi kluczami zarządzanymi przez firmę Microsoft. Nie można cofnąć przypisania programu DEP używanego przez klucze zarządzane firmy Microsoft. Jeśli nie chcesz używać kluczy zarządzanych przez firmę Microsoft, możesz przypisać do skrzynki pocztowej inny program DEP klucza klienta.

> [!IMPORTANT]
> Wycofywanie klucza klienta do kluczy zarządzanych przez firmę Microsoft nie jest obsługiwane w przypadku plików SharePoint Online, OneDrive dla Firm i Teams. 

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Odwoływanie kluczy i uruchamianie procesu ścieżki przeczyszczania danych

Kontrolujesz odwoływanie wszystkich kluczy głównych, w tym klucza dostępności. Klucz klienta zapewnia kontrolę nad aspektem planowania zakończenia wymagań regulacyjnych. Jeśli zdecydujesz się odwołać klucze w celu oczyszczenia danych i zakończenia usługi, usługa usunie klucz dostępności po zakończeniu procesu przeczyszczania danych. Jest to obsługiwane w przypadku adresów DEPs klucza klienta przypisanych do poszczególnych skrzynek pocztowych.

Microsoft 365 przeprowadza inspekcję i weryfikuje ścieżkę przeczyszczania danych. Aby uzyskać więcej informacji, zobacz raport SSAE 18 SOC 2 dostępny w [portalu zaufania usługi](https://servicetrust.microsoft.com/). Ponadto firma Microsoft zaleca następujące dokumenty:

- [Przewodnik dotyczący oceny ryzyka i zgodności dla instytucji finansowych w chmurze firmy Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Zagadnienia dotyczące planowania zakończenia usługi O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Przeczyszczanie wielozadaniowego programu DEP nie jest obsługiwane w przypadku klucza klienta. Wielozadaniowy program DEP służy do szyfrowania danych w wielu obciążeniach dla wszystkich użytkowników dzierżawy. Przeczyszczanie takiego programu DEP spowodowałoby, że dane z wielu obciążeń staną się niedostępne. Jeśli zdecydujesz się całkowicie zakończyć Microsoft 365 usług, możesz kontynuować ścieżkę usuwania dzierżawy zgodnie z udokumentowanym procesem. Zobacz[, jak usunąć dzierżawę w Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Odwoływanie kluczy klienta i klucza dostępności dla Exchange Online i Skype dla firm

Podczas inicjowania ścieżki przeczyszczania danych dla Exchange Online i Skype dla firm należy ustawić stałe żądanie przeczyszczania danych w programie DEP. Spowoduje to trwałe usunięcie zaszyfrowanych danych w skrzynkach pocztowych, do których przypisano ten program DEP.

Ponieważ polecenie cmdlet programu PowerShell można uruchamiać tylko w jednym programie DEP jednocześnie, rozważ ponowne przypisanie pojedynczego programu DEP do wszystkich skrzynek pocztowych przed zainicjowaniem ścieżki przeczyszczania danych.

> [!WARNING]
> Nie używaj ścieżki przeczyszczania danych, aby usunąć podzbiór skrzynek pocztowych. Ten proces jest przeznaczony tylko dla klientów, którzy opuszczają usługę.

Aby zainicjować ścieżkę przeczyszczania danych, wykonaj następujące kroki:

1. Usuń uprawnienia zawijania i rozpakowywanie dla usługi "O365 Exchange Online" z usługi Azure Key Vault.

2. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. Dla każdego programu DEP zawierającego skrzynki pocztowe, które chcesz usunąć, uruchom polecenie cmdlet [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) w następujący sposób.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Jeśli polecenie nie powiedzie się, upewnij się, że usunięto uprawnienia Exchange Online z obu kluczy w usłudze Azure Key Vault zgodnie z wcześniejszym opisem w tym zadaniu. Po ustawieniu przełącznika PermanentDataPurgeRequested przy użyciu polecenia cmdlet Set-DataEncryptionPolicy nie będzie można przypisywać tego programu DEP do skrzynek pocztowych.

4. Skontaktuj się z pomocą techniczną firmy Microsoft i poproś o dokument eDocument przeczyszczania danych.

    Na Twoje żądanie firma Microsoft wysyła do Ciebie dokument prawny w celu potwierdzenia i autoryzacji usunięcia danych. Osoba w organizacji, która zarejestrowała się jako osoba zatwierdzająca w ofercie FastTrack podczas dołączania, musi podpisać ten dokument. Zwykle jest to osoba wykonawcza lub inna wyznaczona osoba w Firmie, która jest prawnie upoważniona do podpisywania dokumentów w imieniu organizacji.

5. Gdy przedstawiciel podpisze dokument prawny, zwróć go do firmy Microsoft (zwykle za pośrednictwem podpisu eDoc).

    Gdy firma Microsoft otrzyma dokument prawny, firma Microsoft uruchamia polecenia cmdlet w celu wyzwolenia przeczyszczania danych, które najpierw usuwa zasady, oznacza skrzynki pocztowe do trwałego usunięcia, a następnie usuwa klucz dostępności. Po zakończeniu procesu przeczyszczania danych dane zostały wyczyszczone, są niedostępne do Exchange Online i nie można ich odzyskać.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Odwoływanie kluczy klienta i klucza dostępności dla plików SharePoint Online, OneDrive dla Firm i Teams

Przeczyszczanie SharePoint, OneDrive do celów służbowych i Teams plików DEPs nie jest obsługiwane w kluczu klienta. Te wielozadaniowe adresy IP są używane do szyfrowania danych w wielu obciążeniach dla wszystkich użytkowników dzierżawy. Przeczyszczanie takiego programu DEP spowodowałoby, że dane z wielu obciążeń staną się niedostępne. Jeśli zdecydujesz się całkowicie zakończyć Microsoft 365 usług, możesz kontynuować ścieżkę usuwania dzierżawy zgodnie z udokumentowanym procesem. Zobacz, jak [usunąć dzierżawę w Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).  

## <a name="related-articles"></a>Powiązane artykuły:

- [Szyfrowanie usługi przy użyciu klucza klienta usługi Microsoft Purview](customer-key-overview.md)

- [Dowiedz się więcej o kluczu dostępności](customer-key-availability-key-understand.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Tocz lub obracaj klucz klienta lub klucz dostępności](customer-key-availability-key-roll.md)

- [Skrytka klienta](customer-lockbox-requests.md)

- [Szyfrowanie usługi](office-365-service-encryption.md)
