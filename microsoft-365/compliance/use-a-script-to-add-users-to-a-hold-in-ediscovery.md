---
title: Dodawanie użytkowników do sprawy zbierania elektronicznych materiałów dowodowych przy użyciu skryptu
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
description: Dowiedz się, jak uruchomić skrypt dodawania skrzynek pocztowych & OneDrive dla Firm witryn do nowego miejsca przechowywania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.
ms.openlocfilehash: fd11ccb6c262cd0e31a65d2a1f95d5dbcd92869c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314563"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>Dodawanie użytkowników do sprawy zbierania elektronicznych materiałów dowodowych przy użyciu skryptu

Centrum & zabezpieczeń program PowerShell udostępnia polecenia cmdlet, które umożliwiają automatyzowanie czasochłonnych zadań związanych z tworzeniem spraw zbierania elektronicznych materiałów dowodowych i zarządzaniem nimi. Obecnie zastosowanie podstawowej sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 umieszczenie dużej liczby lokalizacji zawartości przechwytowej w chmurze wymaga czasu i przygotowania. Na przykład przed utworzeniem wstrzymywania musisz zebrać adres URL każdej OneDrive dla Firm witryny sieci Web, którą chcesz umieścić w a holdie. Następnie dla każdego użytkownika, którego chcesz umieścić w a holdie, musisz dodać jego skrzynkę pocztową i jego OneDrive dla Firm do tej witryny. Za pomocą skryptu w tym artykule możesz zautomatyzować ten proces.
  
Skrypt wyświetli monit o nazwę domeny witryny Moja witryna organizacji ( `contoso` na przykład w adresie URL https://contoso-my.sharepoint.com), nazwie istniejącej sprawy zbierania elektronicznych materiałów dowodowych, nazwie nowego miejsca przechowywania skojarzonego ze sprawą, liście adresów e-mail użytkowników, których chcesz umieścić w a hold, oraz kwerendy wyszukiwania do użycia w przypadku tworzenia blokowania opartego na kwerendach. Skrypt pobiera następnie adres URL witryny programu OneDrive dla Firm dla każdego użytkownika z listy, tworzy nowe wstrzymanie, a następnie dodaje skrzynkę pocztową i witrynę OneDrive dla Firm każdego użytkownika na liście do tej listy. Skrypt generuje również pliki dziennika, które zawierają informacje o nowym wstrzymaniu.
  
W tym celu należy wykonać następujące czynności:
  
[Krok 1. Instalowanie powłoki SharePoint zarządzania online](#step-1-install-the-sharepoint-online-management-shell)
  
[Krok 2. Generowanie listy użytkowników](#step-2-generate-a-list-of-users)
  
[Krok 3. Uruchamianie skryptu w celu utworzenia skryptu i dodania użytkowników](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>Przed dodaniem użytkowników do trzymania

- Aby uruchomić skrypt w kroku 3, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 i administratorem usługi SharePoint Online. Aby uzyskać więcej informacji, zobacz Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń Office [365 & zgodności](assign-ediscovery-permissions.md).

- Do holdu skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 można dodać maksymalnie 1000 skrzynek pocztowych i 100 witryn. Zakładając, że każdy użytkownik, który ma zostać umieścić w a hold, ma witrynę sieci OneDrive dla Firm, można dodać maksymalnie 100 użytkowników do trzymania przy użyciu skryptu z tego artykułu.

- Pamiętaj o zapisaniu listy użytkowników tworzyć w kroku 2 i skryptu w kroku 3 w tym samym folderze. Ułatwi to uruchomienie skryptu.

- Skrypt dodaje listę użytkowników do nowego hold'a, który jest skojarzony z istniejącą sprawą. Przed uruchomieniem skryptu upewnij się, że utworzono sprawę, z którą chcesz skojarzyć wstrzymanie.

- Skrypt w tym artykule obsługuje nowoczesne uwierzytelnianie podczas nawiązywania połączenia z Centrum zgodności & w programie PowerShell i SharePoint powłoki zarządzania online. Skryptu można używać w stanie, w jaki jest, jeśli jesteś Microsoft 365 lub Microsoft 365 GCC organizacją. W przypadku organizacji Office 365 Germany, Microsoft 365 GCC High Organization lub organizacji doD Microsoft 365 DoD należy edytować skrypt, aby pomyślnie go uruchomić. `Connect-IPPSSession` W szczególności należy edytować linię i użyć parametrów *ConnectionUri* oraz *AzureADAuthorizationEndpointUri* (oraz odpowiednich wartości dla typu organizacji), aby połączyć się z programem PowerShell centrum zabezpieczeń & zgodności. Aby uzyskać więcej informacji, zobacz przykłady w te [Połączenie do programu PowerShell & Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Skrypt automatycznie rozłącza się z programem PowerShell & Centrum zgodności i SharePoint powłoki zarządzania online.

- Skrypt zawiera minimalną obsługę błędów. Jego głównym celem jest szybkie i łatwe umieść skrzynkę pocztową i OneDrive dla Firm witryny poszczególnych użytkowników w miejscu przechowywania.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu lub usługi pomocy technicznej firmy Microsoft. Przykładowe skrypty są dostarczane W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowych skryptów i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Krok 1. Instalowanie powłoki SharePoint zarządzania online

Pierwszym krokiem jest zainstalowanie powłoki SharePoint zarządzania online, jeśli nie jest ona jeszcze zainstalowana na komputerze lokalnym. Nie musisz korzystać z powłoki w tej procedurze, ale musisz ją zainstalować, ponieważ zawiera ona wymagania wstępne wymagane przez skrypt uruchamiany w kroku 3. Te wymagania wstępne umożliwiają skryptowi komunikowanie się z usługą SharePoint Online w celu uzyskania adresów URL witryn OneDrive dla Firm internetowych.
  
Przejdź do tematu Konfigurowanie środowiska usługi [SharePoint Online Management Shell Windows PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) i wykonaj kroki 1 i 2, aby zainstalować powłokę zarządzania usługi SharePoint Online na komputerze lokalnym.

## <a name="step-2-generate-a-list-of-users"></a>Krok 2. Generowanie listy użytkowników

Skrypt w kroku 3 utworzy hold, który jest skojarzony ze sprawą zbierania elektronicznych materiałów dowodowych, oraz dodanie skrzynek pocztowych i witryn OneDrive dla Firm z listy użytkowników do hold. Możesz po prostu wpisać adresy e-mail w pliku tekstowym lub uruchomić polecenie w programie Windows PowerShell, aby uzyskać listę adresów e-mail i zapisać je w pliku (znajduje się w tym samym folderze, w którym zapiszesz skrypt w kroku 3).
  
Oto polecenie programu PowerShell (uruchamiane przy użyciu zdalnej obsługi programu PowerShell połączonego z Twoją organizacją programu Exchange Online), które pozwala uzyskać listę adresów e-mail wszystkich użytkowników w organizacji i zapisać je w pliku tekstowym o nazwie HoldUsers.txt.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

Po uruchomieniu tego polecenia otwórz plik tekstowy i usuń nagłówek zawierający nazwę właściwości . `PrimarySmtpAddress` Następnie usuń wszystkie adresy e-mail oprócz adresów użytkowników, których chcesz dodać do hold, który utworzysz w kroku 3. Upewnij się, że przed listą adresów e-mail lub po tej liście nie ma pustych wierszy.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>Krok 3. Uruchamianie skryptu w celu utworzenia skryptu i dodania użytkowników

Po uruchomieniu skryptu w tym kroku zostanie wyświetlony monit o następujące informacje. Przed uruchomieniem skryptu należy przygotować te informacje.
  
- **Poświadczenia użytkownika:** Skrypt użyje Twoich poświadczeń do nawiązania połączenia z Centrum zabezpieczeń & zgodności za pomocą programu PowerShell. Ponadto użyje tych poświadczeń w celu uzyskania dostępu SharePoint Online w celu uzyskania dostępu do OneDrive dla Firm URL listy użytkowników.

- **Nazwa domeny SharePoint:** Skrypt wyświetli monit o wprowadzenie tej nazwy, aby można było połączyć się z centrum SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">administracyjnego</a>. Ponadto używa nazwy domeny dla OneDrive URL w organizacji. Jeśli na przykład adres URL `https://contoso-admin.sharepoint.com` Twojego centrum administracyjnego to , a adres URL `https://contoso-my.sharepoint.com`OneDrive to , `contoso` wprowadź go, gdy skrypt wyświetli monit o podanie nazwy domeny.

- **Nazwa sprawy:** Nazwa istniejącej sprawy. Skrypt utworzy nowe hold, które jest skojarzone z tą sprawą.

- **Nazwa wstrzymywania:** Nazwa skryptu spowoduje utworzenie i skojarzenie określonej sprawy.

- **Zapytanie wyszukiwania dla trzymania opartego na kwerendzie:** Wstrzymywanie oparte na kwerendach można utworzyć w taki sposób, aby wstrzymywać będzie tylko zawartość spełniająca określone kryteria wyszukiwania. Aby umieścić całą zawartość w a hold, po prostu naciśnij klawisz **Enter** , gdy zostanie wyświetlony monit o zapytanie wyszukiwania.

- **Włączanie lub wyłączanie wstrzymywania:** Skrypt można włączyć wstrzymywanie po jego utworzeniu lub można utworzyć skrypt bez włączania go. Jeśli skrypt nie został uruchomiony, możesz włączyć go później w Centrum zgodności platformy Microsoft 365 lub uruchamiając następujące polecenia programu PowerShell:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **Nazwa pliku tekstowego z** listą użytkowników — nazwa pliku tekstowego z kroku 2, który zawiera listę użytkowników do dodania do zawieszonego systemu. Jeśli ten plik znajduje się w tym samym folderze co skrypt, po prostu wpisz nazwę pliku (na przykład HoldUsers.txt). Jeśli plik tekstowy znajduje się w innym folderze, wpisz pełną nazwę i ścieżkę pliku.

Po zebraniu informacji, o które zostanie wyświetlony monit skryptu, ostatnim krokiem jest uruchomienie skryptu w celu utworzenia nowego blokowania i dodania do niego użytkowników.
  
1. Zapisz poniższy tekst w pliku Windows PowerShell pliku skryptu, używając sufiksu nazwy pliku `.ps1`. Na przykład `AddUsersToHold.ps1`.

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

2. Na komputerze lokalnym otwórz program Windows PowerShell i przejdź do folderu, w którym został zapisany skrypt.

3. Uruchom skrypt. na przykład:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. Wprowadź informacje, o które zostanie wyświetlony monit skryptu.

   Skrypt łączy się z programem PowerShell centrum zabezpieczeń & zgodności, a następnie tworzy nowe hold w przypadku zbierania elektronicznych materiałów dowodowych oraz dodaje skrzynki pocztowe i OneDrive dla Firm użytkowników do listy. Możesz przejść do sprawy na stronie **zbierania** elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365, aby wyświetlić nowe wstrzymanie.

Po zakończeniu wykonywania skryptu tworzy następujące pliki dziennika i zapisuje je w folderze, w którym znajduje się skrypt.
  
- **LocationsOnHold.txt:** Zawiera listę skrzynek pocztowych i witryn OneDrive dla Firm, które skrypt pomyślnie umieścił w a hold.

- **LocationsNotOnHold.txt:** Zawiera listę skrzynek pocztowych i witryn OneDrive dla Firm, których skrypt nie umieścić w a hold. Jeśli użytkownik ma skrzynkę pocztową, ale nie witrynę OneDrive dla Firm, zostałby uwzględniony na liście witryn programu OneDrive dla Firm, które nie zostały umieszczone w a hold.

- **GetCaseHoldPolicy.txt:** Zawiera wynik polecenia **cmdlet Get-CaseHoldPolicy** dla nowego blokowania, którego skrypt uruchomił po utworzeniu nowego blokowania. Informacje zwrócone przez to polecenie cmdlet obejmują listę użytkowników, których skrzynki pocztowe i witryny OneDrive dla Firm zostały umieszczone w a hold i czy to hold jest włączone, czy wyłączone. 

- **GetCaseHoldRule.txt:** Zawiera wynik polecenia **cmdlet Get-CaseHoldRule** nowego hold, którego skrypt uruchomił po utworzeniu nowego blokowania. Informacje zwrócone przez to polecenie cmdlet obejmują zapytanie wyszukiwania, jeśli skrypt został użyty do utworzenia hold'a opartego na zapytaniu.
