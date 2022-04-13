---
title: Dodawanie użytkowników do blokady w przypadku zbierania elektronicznych materiałów dowodowych za pomocą skryptu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: bad352ff-d5d2-45d8-ac2a-6cb832f10e73
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: Dowiedz się, jak uruchomić skrypt w celu dodania skrzynek pocztowych & OneDrive dla Firm witryn do nowego archiwum skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.
ms.openlocfilehash: 10a605b422178e5006d8a027a697ca6745f82b98
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824493"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>Dodawanie użytkowników do blokady w przypadku zbierania elektronicznych materiałów dowodowych za pomocą skryptu

Program PowerShell & Compliance Center zapewnia polecenia cmdlet, które umożliwiają automatyzowanie czasochłonnych zadań związanych z tworzeniem przypadków zbierania elektronicznych materiałów dowodowych i zarządzaniem nimi. Obecnie użycie przypadku core eDiscovery w Centrum zgodności platformy Microsoft 365 do umieszczenia dużej liczby lokalizacji zawartości opiekuna w zawieszeniu wymaga czasu i przygotowania. Na przykład przed utworzeniem blokady musisz zebrać adres URL dla każdej witryny OneDrive dla Firm, która ma zostać wstrzymana. Następnie dla każdego użytkownika, który chcesz umieścić w zawieszeniu, musisz dodać jego skrzynkę pocztową i witrynę OneDrive dla Firm do blokady. Aby zautomatyzować ten proces, możesz użyć skryptu w tym artykule.
  
Skrypt wyświetla monit o podanie nazwy domeny Moja witryna organizacji (na przykład `contoso` w adresie URL https://contoso-my.sharepoint.com)nazwa istniejącego przypadku zbierania elektronicznych materiałów dowodowych, nazwa nowego archiwum skojarzonego ze sprawą, lista adresów e-mail użytkowników, których chcesz wstrzymać, oraz zapytanie wyszukiwania do użycia, jeśli chcesz utworzyć blokadę opartą na zapytaniach. Następnie skrypt pobiera adres URL witryny OneDrive dla Firm dla każdego użytkownika na liście, tworzy nowe blokady, a następnie dodaje skrzynkę pocztową i witrynę OneDrive dla Firm dla każdego użytkownika na liście do blokady. Skrypt generuje również pliki dziennika zawierające informacje o nowym blokadzie.
  
Poniżej przedstawiono kroki, które należy wykonać:
  
[Krok 1. Instalowanie powłoki zarządzania SharePoint Online](#step-1-install-the-sharepoint-online-management-shell)
  
[Krok 2. Generowanie listy użytkowników](#step-2-generate-a-list-of-users)
  
[Krok 3. Uruchamianie skryptu w celu utworzenia blokady i dodania użytkowników](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>Przed dodaniem użytkowników do blokady

- Aby uruchomić skrypt w kroku 3, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 i administratorem usługi SharePoint Online. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w centrum Office 365 Security & Compliance Center](assign-ediscovery-permissions.md).

- Maksymalnie 1000 skrzynek pocztowych i 100 witryn można dodać do blokady skojarzonej ze sprawą zbierania elektronicznych elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Zakładając, że każdy użytkownik, który ma zostać wstrzymany, ma witrynę OneDrive dla Firm, możesz dodać maksymalnie 100 użytkowników do blokady przy użyciu skryptu w tym artykule.

- Pamiętaj, aby zapisać listę użytkowników utworzonych w kroku 2 i skrypt w kroku 3 w tym samym folderze. Ułatwi to uruchamianie skryptu.

- Skrypt dodaje listę użytkowników do nowego archiwum skojarzonego z istniejącym przypadkiem. Przed uruchomieniem skryptu upewnij się, że przypadek, z którą chcesz skojarzyć blokadę, został utworzony.

- Skrypt w tym artykule obsługuje nowoczesne uwierzytelnianie podczas nawiązywania połączenia z programem PowerShell & Compliance Center i powłoką zarządzania usługi SharePoint Online. Możesz użyć skryptu w taki sam jak jest, jeśli jesteś Microsoft 365 lub organizacją Microsoft 365 GCC. Jeśli jesteś organizacją Office 365 Niemczech, organizacją Microsoft 365 GCC High lub organizacją Microsoft 365 DoD, musisz edytować skrypt, aby pomyślnie go uruchomić. W szczególności musisz edytować wiersz `Connect-IPPSSession` i użyć parametrów *ConnectionUri* i *AzureADAuthorizationEndpointUri* (i odpowiednich wartości dla typu organizacji), aby nawiązać połączenie z programem PowerShell Security & Compliance Center. Aby uzyskać więcej informacji, zobacz przykłady w [programie PowerShell Połączenie to Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Skrypt automatycznie odłącza się od programu PowerShell Centrum zgodności & zabezpieczeń i powłoki zarządzania SharePoint Online.

- Skrypt zawiera minimalną obsługę błędów. Jego głównym celem jest szybkie i łatwe umieszczenie skrzynki pocztowej i OneDrive dla Firm lokacji każdego użytkownika.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowe skrypty są dostarczane jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowych skryptów i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Krok 1. Instalowanie powłoki zarządzania SharePoint Online

Pierwszym krokiem jest zainstalowanie powłoki zarządzania SharePoint Online, jeśli nie jest jeszcze zainstalowana na komputerze lokalnym. Nie musisz używać powłoki w tej procedurze, ale musisz ją zainstalować, ponieważ zawiera wymagania wstępne wymagane przez skrypt uruchomiony w kroku 3. Te wymagania wstępne umożliwiają skryptowi komunikowanie się z usługą SharePoint Online w celu pobrania adresów URL witryn OneDrive dla Firm.
  
Przejdź do [obszaru Konfigurowanie środowiska Windows PowerShell powłoki zarządzania SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) i wykonaj kroki 1 i 2, aby zainstalować powłokę zarządzania SharePoint Online na komputerze lokalnym.

## <a name="step-2-generate-a-list-of-users"></a>Krok 2. Generowanie listy użytkowników

Skrypt w kroku 3 utworzy blokadę skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych oraz dodasz skrzynki pocztowe i witryny OneDrive dla Firm listy użytkowników do blokady. Możesz po prostu wpisać adresy e-mail w pliku tekstowym lub uruchomić polecenie w Windows PowerShell, aby uzyskać listę adresów e-mail i zapisać je w pliku (znajdującym się w tym samym folderze, w jakim zapiszesz skrypt w kroku 3).
  
Oto polecenie programu PowerShell (uruchamiane przy użyciu zdalnego programu PowerShell połączonego z organizacją Exchange Online), aby uzyskać listę adresów e-mail dla wszystkich użytkowników w organizacji i zapisać je w pliku tekstowym o nazwie HoldUsers.txt.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

Po uruchomieniu tego polecenia otwórz plik tekstowy i usuń nagłówek zawierający nazwę  `PrimarySmtpAddress`właściwości . Następnie usuń wszystkie adresy e-mail z wyjątkiem tych dla użytkowników, których chcesz dodać do blokady utworzonej w kroku 3. Upewnij się, że nie ma pustych wierszy przed lub po liście adresów e-mail.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>Krok 3. Uruchamianie skryptu w celu utworzenia blokady i dodania użytkowników

Po uruchomieniu skryptu w tym kroku zostanie wyświetlony monit o podanie następujących informacji. Pamiętaj, aby te informacje były gotowe przed uruchomieniem skryptu.
  
- **Poświadczenia użytkownika:** Skrypt użyje twoich poświadczeń do nawiązania połączenia z Centrum zgodności & zabezpieczeń za pomocą programu PowerShell. Te poświadczenia będą również używane do uzyskiwania dostępu do SharePoint Online w celu uzyskania adresów URL OneDrive dla Firm dla listy użytkowników.

- **Nazwa domeny SharePoint:** skrypt monituje o wprowadzenie tej nazwy, aby można było nawiązać połączenie z <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnym SharePoint</a>. Używa ona również nazwy domeny dla adresów URL OneDrive w organizacji. Jeśli na przykład adres URL centrum administracyjnego to `https://contoso-admin.sharepoint.com` , a adres URL OneDrive to `https://contoso-my.sharepoint.com`, należy wprowadzić`contoso`, gdy skrypt wyświetli monit o podanie nazwy domeny.

- **Nazwa sprawy:** Nazwa istniejącego przypadku. Skrypt utworzy nowe blokady skojarzone z tym przypadkiem.

- **Nazwa blokady:** Nazwa blokady skryptu zostanie utworzona i skojarzona z określonym przypadkiem.

- **Wyszukaj zapytanie dotyczące blokady opartej na zapytaniach:** Można utworzyć blokadę opartą na zapytaniach, aby tylko zawartość spełniająca określone kryteria wyszukiwania została wstrzymana. Aby wstrzymać całą zawartość, naciśnij klawisz **Enter** po wyświetleniu monitu o zapytanie wyszukiwania.

- **Włączanie blokady lub nie:** Po jego utworzeniu skrypt może włączyć blokadę lub utworzyć blokadę bez włączania go. Jeśli skrypt nie jest włączony, możesz go włączyć w dalszej części Centrum zgodności platformy Microsoft 365 lub uruchamiając następujące polecenia programu PowerShell:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **Nazwa pliku tekstowego z listą użytkowników** — nazwa pliku tekstowego z kroku 2 zawierającego listę użytkowników do dodania do blokady. Jeśli ten plik znajduje się w tym samym folderze co skrypt, wystarczy wpisać nazwę pliku (na przykład HoldUsers.txt). Jeśli plik tekstowy znajduje się w innym folderze, wpisz pełną nazwę ścieżki pliku.

Po zebraniu informacji, o które zostanie wyświetlony monit skrypt, ostatnim krokiem jest uruchomienie skryptu w celu utworzenia nowego blokady i dodania do niego użytkowników.
  
1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy `.ps1`pliku . Na przykład `AddUsersToHold.ps1`.

```powershell
#script begin
" "
write-host "***********************************************"
write-host "   Security & Compliance Center PowerShell  " -foregroundColor yellow -backgroundcolor darkgreen
write-host "   Core eDiscovery cases - Add users to a hold   " -foregroundColor yellow -backgroundcolor darkgreen 
write-host "***********************************************"
" "
# Connect to SCC PowerShell using modern authentication
if (!$SccSession)
{
  Import-Module ExchangeOnlineManagement
  Connect-IPPSSession
}

# Get the organization's domain name. We use this to create the SharePoint admin URL and root URL for OneDrive for Business.
""
$mySiteDomain = Read-Host "Enter the domain name for your SharePoint organization. We use this name to connect to SharePoint admin center and for the OneDrive URLs in your organization. For example, 'contoso' in 'https://contoso-admin.sharepoint.com' and 'https://contoso-my.sharepoint.com'"
""

# Connect to PnP Online using modern authentication
Import-Module PnP.PowerShell
Connect-PnPOnline -Url https://$mySiteDomain-admin.sharepoint.com -UseWebLogin

# Load the SharePoint assemblies from the SharePoint Online Management Shell
# To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
{
    $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
    $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
    $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
    if (!$SharePointClient)
    {
        Write-Error "The SharePoint Online Management Shell isn't installed. Please install it from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then re-run this script."
        return;
    }
}

# Get other required information
do{
$casename = Read-Host "Enter the name of the case"
$caseexists = (get-compliancecase -identity "$casename" -erroraction SilentlyContinue).isvalid
if($caseexists -ne 'True')
{""
write-host "A case named '$casename' doesn't exist. Please specify the name of an existing case, or create a new case and then re-run the script." -foregroundColor Yellow
""}
}While($caseexists -ne 'True')
""
do{
$holdName = Read-Host "Enter the name of the new hold"
$holdexists=(get-caseholdpolicy -identity "$holdname" -case "$casename" -erroraction SilentlyContinue).isvalid
if($holdexists -eq 'True')
{""
write-host "A hold named '$holdname' already exists. Please specify a new hold name." -foregroundColor Yellow
""}
}While($holdexists -eq 'True')
""
$holdQuery = Read-Host "Enter a search query to create a query-based hold, or press Enter to hold all content"
""
$holdstatus = read-host "Do you want the hold enabled after it's created? (Yes/No)"
do{
""
$inputfile = read-host "Enter the name of the text file that contains the email addresses of the users to add to the hold"
""
$fileexists = test-path -path $inputfile
if($fileexists -ne 'True'){write-host "$inputfile doesn't exist. Please enter a valid file name." -foregroundcolor Yellow}
}while($fileexists -ne 'True')
#Import the list of addresses from the txt file.  Trim any excess spaces and make sure all addresses 
    #in the list are unique.
  [array]$emailAddresses = Get-Content $inputfile -ErrorAction SilentlyContinue | where {$_.trim() -ne ""}  | foreach{ $_.Trim() }
  [int]$dupl = $emailAddresses.count
  [array]$emailAddresses = $emailAddresses | select-object -unique
  $dupl -= $emailAddresses.count
#Validate email addresses so the hold creation does not run in to an error.
if($emailaddresses.count -gt 0){
write-host ($emailAddresses).count "addresses were found in the text file. There were $dupl duplicate entries in the file." -foregroundColor Yellow
""
Write-host "Validating the email addresses. Please wait..." -foregroundColor Yellow
""
$finallist =@()
foreach($emailAddress in $emailAddresses)
{
if((get-recipient $emailaddress -erroraction SilentlyContinue).isvalid -eq 'True')
{$finallist += $emailaddress}
else {"Unable to find the user $emailaddress"
[array]$excludedlist += $emailaddress}
}
""
#Find user's OneDrive account URL using email address
Write-Host "Getting the URL for each user's OneDrive for Business site." -foregroundColor Yellow 
""
$AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
$mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
$urls = @()
foreach($emailAddress in $finallist)
{
try
{
$url=Get-PnPUserProfileProperty -Account $emailAddress | Select PersonalUrl
$urls += $url.PersonalUrl
       Write-Host "- $emailAddress => $url"
       [array]$ODadded += $url.PersonalUrl
       }catch { 
 Write-Warning "Could not locate OneDrive for $emailAddress"
 [array]$ODExluded += $emailAddress
 Continue }
}
$urls | FL
if(($finallist.count -gt 0) -or ($urls.count -gt 0)){
""
Write-Host "Creating the hold named $holdname. Please wait..." -foregroundColor Yellow
if(($holdstatus -eq "Y") -or ($holdstatus -eq  "y") -or ($holdstatus -eq "yes") -or ($holdstatus -eq "YES")){
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $True | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery | out-null
}
else{
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $false | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery -disabled $false | out-null
}
""
}
else {"No valid locations were identified. Therefore, the hold wasn't created."}
#write log files (if needed)
$newhold=Get-CaseHoldPolicy -Identity "$holdname" -Case "$casename" -erroraction SilentlyContinue
$newholdrule=Get-CaseHoldRule -Identity "$holdName" -erroraction SilentlyContinue
if(($ODAdded.count -gt 0) -or ($ODExluded.count -gt 0) -or ($finallist.count -gt 0) -or ($excludedlist.count -gt 0) -or ($newhold.isvalid -eq 'True') -or ($newholdrule.isvalid -eq 'True'))
{
Write-Host "Generating output files..." -foregroundColor Yellow
if($ODAdded.count -gt 0){
"OneDrive Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.SharePointLocation.name | add-content .\LocationsOnHold.txt}
if($ODExluded.count -gt 0){ 
"Users without OneDrive locations" | add-content .\LocationsNotOnHold.txt
"================================" | add-content .\LocationsNotOnHold.txt
$ODExluded | add-content .\LocationsNotOnHold.txt}
if($finallist.count -gt 0){
" " | add-content .\LocationsOnHold.txt
"Exchange Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.ExchangeLocation.name | add-content .\LocationsOnHold.txt}
if($excludedlist.count -gt 0){
" "| add-content .\LocationsNotOnHold.txt
"Mailboxes not added to the hold" | add-content .\LocationsNotOnHold.txt
"===============================" | add-content .\LocationsNotOnHold.txt
$excludedlist | add-content .\LocationsNotOnHold.txt}
$FormatEnumerationLimit=-1
if($newhold.isvalid -eq 'True'){$newhold|fl >.\GetCaseHoldPolicy.txt}
if($newholdrule.isvalid -eq 'True'){$newholdrule|Fl >.\GetCaseHoldRule.txt}
}
}
else {"The hold wasn't created because no valid entries were found in the text file."}
""
#Disconnect from SCC PowerShell and PnPOnline

Write-host "Disconnecting from SCC PowerShell and PnP Online" -foregroundColor Yellow
Get-PSSession | Remove-PSSession
Disconnect-PnPOnline

Write-host "Script complete!" -foregroundColor Yellow
""
#script end
```

2. Na komputerze lokalnym otwórz Windows PowerShell i przejdź do folderu, w którym zapisano skrypt.

3. Uruchom skrypt; na przykład:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. Wprowadź informacje, o które monituje skrypt.

   Skrypt łączy się z programem PowerShell Security & Compliance Center, a następnie tworzy nowe blokady w przypadku zbierania elektronicznych materiałów dowodowych i dodaje skrzynki pocztowe i OneDrive dla Firm dla użytkowników na liście. Możesz przejść do sprawy na stronie **zbierania elektronicznych materiałów dowodowych** w Centrum zgodności platformy Microsoft 365, aby wyświetlić nową blokadę.

Po zakończeniu działania skryptu tworzy następujące pliki dziennika i zapisuje je w folderze, w którym znajduje się skrypt.
  
- **LocationsOnHold.txt:** Zawiera listę skrzynek pocztowych i witryn OneDrive dla Firm, które skrypt został pomyślnie wstrzymany.

- **LocationsNotOnHold.txt:** Zawiera listę skrzynek pocztowych i witryn OneDrive dla Firm, których skrypt nie został wstrzymany. Jeśli użytkownik ma skrzynkę pocztową, ale nie witrynę OneDrive dla Firm, użytkownik zostanie umieszczony na liście witryn OneDrive dla Firm, które nie zostały wstrzymane.

- **GetCaseHoldPolicy.txt:** Zawiera dane wyjściowe polecenia cmdlet **Get-CaseHoldPolicy** dla nowego blokady, które skrypt uruchomił po utworzeniu nowego blokady. Informacje zwrócone przez to polecenie cmdlet zawierają listę użytkowników, których skrzynki pocztowe i witryny OneDrive dla Firm zostały wstrzymane oraz czy blokada jest włączona, czy wyłączona. 

- **GetCaseHoldRule.txt:** Zawiera dane wyjściowe polecenia cmdlet **Get-CaseHoldRule** dla nowego blokady, które skrypt uruchomił po utworzeniu nowego blokady. Informacje zwrócone przez to polecenie cmdlet zawierają zapytanie wyszukiwania, jeśli skrypt został użyty do utworzenia blokady opartej na zapytaniach.
