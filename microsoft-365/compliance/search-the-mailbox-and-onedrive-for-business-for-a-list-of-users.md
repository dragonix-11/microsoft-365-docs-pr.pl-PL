---
title: Wyszukiwanie w skrzynce & OneDrive dla Firm w celu wyszukania listy użytkowników z wyszukiwaniem zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 1/3/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 5f4f8206-2d6a-4cb2-bbc6-7a0698703cc0
description: Przeszukiwanie zawartości oraz skrypty w tym artykule wyszukuje skrzynki pocztowe i witryny OneDrive dla Firm w poszukiwaniu grupy użytkowników.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2fdf749511cc859c0aec2ea947c3a53cb800cf8c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996745"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Wyszukiwanie zawartości w skrzynce pocztowej i OneDrive dla Firm witryny w celu wyszukania listy użytkowników

Program PowerShell & zabezpieczeń i zgodności udostępnia wiele poleceń cmdlet, które umożliwiają automatyzowanie czasochłonnych zadań związanych z zbierania elektronicznych materiałów dowodowych. Obecnie utworzenie pola Przeszukiwanie zawartości w Centrum zgodności platformy Microsoft 365 przeszukiwania dużej liczby lokalizacji zawartości przejmuje czas i przygotowanie. Zanim utworzysz wyszukiwanie, musisz zebrać adresy URL poszczególnych OneDrive dla Firm, a następnie dodać poszczególne skrzynki pocztowe i witryny OneDrive dla Firm do wyszukiwania. W przyszłych wersjach będzie to łatwiejsze do Centrum zgodności platformy Microsoft 365. Do tego czasu możesz zautomatyzować ten proces za pomocą skryptu z tego artykułu. W tym skrypcie jest wyświetlany monit o nazwę domeny Mojej witryny organizacji (na przykład **contoso** w adresie URL `https://contoso-my.sharepoint.com`), listę adresów e-mail użytkowników, nazwę nowego wyszukiwania zawartości i zapytanie wyszukiwania, które ma być wyszukiwane. Skrypt pobiera adres URL programu OneDrive dla Firm dla każdego użytkownika na liście, a następnie tworzy i uruchamia wyszukiwanie zawartości, które przeszukuje skrzynkę pocztową i witrynę programu OneDrive dla Firm dla każdego użytkownika na liście za pomocą zapytania wyszukiwania, które po zapewniają.
  
## <a name="permissions-and-script-information"></a>Uprawnienia i informacje o skryptach

- Aby uruchomić skrypt w kroku 3, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w u administratora Centrum zgodności platformy Microsoft 365 SharePoint Online.

- Pamiętaj o zapisaniu listy użytkowników tworzyć w kroku 2 i skryptu w kroku 3 w tym samym folderze. Ułatwi to uruchomienie skryptu.

- Skrypt zawiera minimalną obsługę błędów. Jego głównym celem jest szybkie i łatwe przeszukiwanie skrzynki pocztowej i OneDrive dla Firm poszczególnych użytkowników.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu lub usługi pomocy technicznej firmy Microsoft. Przykładowe skrypty są dostarczane W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowych skryptów i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Krok 1. Instalowanie powłoki SharePoint zarządzania online

Pierwszym krokiem jest zainstalowanie powłoki SharePoint zarządzania online. Nie musisz korzystać z powłoki w tej procedurze, ale musisz ją zainstalować, ponieważ zawiera ona wymagania wstępne wymagane przez skrypt uruchamiany w kroku 3. Te wymagania wstępne umożliwiają skryptowi komunikowanie się z usługą SharePoint Online w celu uzyskania adresów URL witryn OneDrive dla Firm internetowych.
  
Przejdź do tematu Konfigurowanie środowiska usługi [SharePoint Online Management Shell Windows PowerShell i](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) wykonaj kroki 1 i 2, aby zainstalować powłokę zarządzania SharePoint online.
  
## <a name="step-2-generate-a-list-of-users"></a>Krok 2. Generowanie listy użytkowników

Skrypt w kroku 3 utworzy wyszukiwanie zawartości w celu przeszukiwania skrzynek OneDrive kont w poszukiwaniu listy użytkowników. Możesz po prostu wpisać adresy e-mail w pliku tekstowym lub uruchomić polecenie w programie Windows PowerShell, aby uzyskać listę adresów e-mail i zapisać je w pliku (znajduje się w tym samym folderze, w którym zapiszesz skrypt w kroku 3).
  
Oto polecenie programu [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), które można uruchomić w celu uzyskania listy adresów e-mail dla wszystkich użytkowników w organizacji i zapisania go w pliku tekstowym o nazwie `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Po uruchomieniu tego polecenia otwórz plik i usuń nagłówek zawierający nazwę właściwości . `PrimarySmtpAddress` Plik tekstowy powinien po prostu zawierać listę adresów e-mail i nie powinno zawierać nic więcej. Upewnij się, że przed listą adresów e-mail lub po tej liście nie ma pustych wierszy.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>Krok 3. Uruchomienie skryptu w celu utworzenia i rozpoczęcia wyszukiwania

Po uruchomieniu skryptu w tym kroku zostanie wyświetlony monit o następujące informacje. Przed uruchomieniem skryptu należy przygotować te informacje.
  
- **Poświadczenia** użytkownika — skrypt użyje Twoich poświadczeń w celu uzyskania dostępu do usługi SharePoint Online w celu uzyskania dostępu do adresów URL usługi OneDrive dla Firm i połączenia się z programem PowerShell centrum zabezpieczeń & zgodności. 
    
- **Nazwa domeny mojej witryny —** domena witryny Moja witryna to domena zawierająca wszystkie witryny OneDrive dla Firm w organizacji. Jeśli na przykład adres URL **https://contoso-my.sharepoint.com** domeny Mojej witryny to ,  `contoso` wprowadź go, gdy skrypt wyświetli monit o nazwę domeny Mojej witryny. 
    
- **Nazwa ścieżki pliku tekstowego z kroku 2** — nazwa ścieżki pliku tekstowego utworzonego w kroku 2. Jeśli plik tekstowy i skrypt znajdują się w tym samym folderze, wprowadź nazwę pliku tekstowego. W przeciwnym razie wprowadź pełną nazwę ścieżki pliku tekstowego. 
    
- **Nazwa wyszukiwania zawartości —** nazwa wyszukiwania zawartości, które zostanie utworzone przez skrypt. 
    
- **Zapytanie wyszukiwania** — zapytanie wyszukiwania, które będzie używane wraz z wyszukiwaniem zawartości, zostanie utworzone i uruchomione. Aby uzyskać więcej informacji na temat zapytań wyszukiwania, zobacz Zapytania słów kluczowych [i warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).


**Aby uruchomić skrypt:**
    
1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `SearchEXOOD4B.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zapisano listę użytkowników w kroku 2.
    
  ```powershell
  # This PowerShell script will prompt you for the following information:
  #    * Your user credentials 
  #    * The name of your organization's MySite domain                                              
  #    * The pathname for the text file that contains a list of user email addresses
  #    * The name of the Content Search that will be created
  #    * The search query string
  # The script will then:
  #    * Find the OneDrive for Business site for each user in the text file
  #    * Create and start a Content Search using the above information
  # Get user credentials
  if (!$credentials)
  {
      $credentials = Get-Credential
  }
  # Get the user's MySite domain name.  We use this to create the admin URL and root URL for OneDrive for Business
  $mySiteDomain = Read-Host "What is your organization's MySite domain?  For example,  'contoso' for 'https://contoso-my.sharepoint.com'"
  $AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
  $mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
  # Get other required information
  $inputfile = read-host "Enter the file name of the text file that contains the email addresses for the users you want to search"
  $searchName = Read-Host "Enter the name for the new search"
  $searchQuery = Read-Host "Enter the search query you want to use"
  $emailAddresses = Get-Content $inputfile | where {$_ -ne ""}  | foreach{ $_.Trim() }
  # Connect to Security & Compliance Center PowerShell
  if (!$s -or !$a)
  {
      Import-Module ExchangeOnlineManagement
      Connect-IPPSSession
  }
  
  # Load the SharePoint assemblies from the SharePoint Online Management Shell
  # To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
  if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
  {
      $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
      $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
      $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
      if (!$SharePointClient)
      {
          Write-Error "SharePoint Online Management Shell isn't installed, please install from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then run this script again"
          return;
      }
  }
  if (!$spCreds)
  {
      $spCreds = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($credentials.UserName, $credentials.Password)
  }
  # Add the path of the User Profile Service to the SPO admin URL, then create a new webservice proxy to access it
  $proxyaddr = "$AdminUrl/_vti_bin/UserProfileService.asmx?wsdl"
  $UserProfileService= New-WebServiceProxy -Uri $proxyaddr -UseDefaultCredential False
  $UserProfileService.Credentials = $credentials
  # Take care of auth cookies
  $strAuthCookie = $spCreds.GetAuthenticationCookie($AdminUrl)
  $uri = New-Object System.Uri($AdminUrl)
  $container = New-Object System.Net.CookieContainer
  $container.SetCookies($uri, $strAuthCookie)
  $UserProfileService.CookieContainer = $container
  Write-Host "Getting each user's OneDrive for Business URL"
  $urls = @()
  foreach($emailAddress in $emailAddresses)
  {
      try
      {
          $prop = $UserProfileService.GetUserProfileByName("i:0#.f|membership|$emailAddress") | Where-Object { $_.Name -eq "PersonalSpace" } 
          $url = $prop.values[0].value
          $furl = $mySiteUrlRoot + $url
          $urls += $furl
          Write-Host "-$emailAddress => $furl"
      }
      catch
      {
          Write-Warning "Could not locate OneDrive for $emailAddress"
      }
  }
  Write-Host "Creating and starting the search"
  $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $emailAddresses -SharePointLocation $urls -ContentMatchQuery $searchQuery
  # Finally, start the search and then display the status
  if($search)
  {
      Start-ComplianceSearch $search.Name
      Get-ComplianceSearch $search.Name
  }
  
  ```

2. Otwórz Windows PowerShell i przejdź do folderu, w którym został zapisany skrypt, oraz do listy użytkowników z kroku 2.
    
3. Uruchom skrypt. na przykład:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Po wyświetleniu monitu o podanie poświadczeń wprowadź swój adres e-mail i hasło, a następnie kliknij przycisk **OK**. 
    
5. Po wyświetleniu monitu przez skrypt wprowadź następujące informacje. Wpisz poszczególne informacje, a następnie naciśnij klawisz **Enter**.
    
    - Nazwa domeny Mojej domeny. 
    
    - Nazwa ścieżki pliku tekstowego zawierającego listę użytkowników.
    
    - Nazwa wyszukiwania zawartości.
    
    - Zapytanie wyszukiwania (pozostaw to pole puste, aby zwrócić wszystkie elementy w lokalizacjach zawartości).
    
    Skrypt pobiera adresy URL każdej witryny OneDrive dla Firm, a następnie tworzy i rozpoczyna wyszukiwanie. Aby wyświetlić statystyki wyszukiwania i wyniki, możesz uruchomić polecenie cmdlet **Get-ComplianceSearch** w centrum zabezpieczeń & Compliance Center lub przejść do strony Przeszukiwanie zawartości w Centrum zgodności platformy Microsoft 365, aby wyświetlić informacje  o wyszukiwaniu.
