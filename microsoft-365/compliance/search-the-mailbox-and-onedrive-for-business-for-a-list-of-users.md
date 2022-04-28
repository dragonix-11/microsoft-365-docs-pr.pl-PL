---
title: Użyj wyszukiwania zawartości dla listy użytkowników w & OneDrive dla Firm witrynie skrzynki pocztowej
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Użyj funkcji wyszukiwania zawartości i skryptu w tym artykule, aby wyszukać w skrzynkach pocztowych i witrynach OneDrive dla Firm grupę użytkowników.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a75296bd17a1f4b77c22298f6c9a294ec06bd182
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098455"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Wyszukiwanie zawartości umożliwia wyszukanie listy użytkowników w skrzynce pocztowej i witrynie OneDrive dla Firm

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Program PowerShell & Compliance Center zapewnia szereg poleceń cmdlet, które umożliwiają automatyzację czasochłonnych zadań związanych zbierania elektronicznych materiałów dowodowych. Obecnie tworzenie wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview w celu wyszukiwania dużej liczby lokalizacji zawartości opiekuna wymaga czasu i przygotowania. Przed utworzeniem wyszukiwania należy zebrać adres URL dla każdej OneDrive dla Firm witryny, a następnie dodać każdą skrzynkę pocztową i witrynę OneDrive dla Firm do wyszukiwania. W przyszłych wersjach będzie to łatwiejsze do wykonania w portalu zgodności. Do tego czasu możesz użyć skryptu w tym artykule, aby zautomatyzować ten proces. Ten skrypt wyświetla monit o podanie nazwy domeny witryny MySite organizacji (na przykład **contoso** w adresie URL `https://contoso-my.sharepoint.com`), listy adresów e-mail użytkownika, nazwy nowego wyszukiwania zawartości i zapytania wyszukiwania do użycia. Skrypt pobiera adres URL OneDrive dla Firm dla każdego użytkownika na liście, a następnie tworzy i uruchamia wyszukiwanie zawartości, które wyszukuje skrzynkę pocztową i witrynę OneDrive dla Firm dla każdego użytkownika na liście przy użyciu podanej kwerendy wyszukiwania.
  
## <a name="permissions-and-script-information"></a>Informacje o uprawnieniach i skryptach

- Aby uruchomić skrypt w kroku 3, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności i administratorem globalnym usługi SharePoint Online.

- Pamiętaj, aby zapisać listę użytkowników utworzonych w kroku 2 i skrypt w kroku 3 w tym samym folderze. Ułatwi to uruchamianie skryptu.

- Skrypt zawiera minimalną obsługę błędów. Jego głównym celem jest szybkie i łatwe przeszukiwanie skrzynki pocztowej i OneDrive dla Firm lokacji każdego użytkownika.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowe skrypty są dostarczane jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowych skryptów i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Krok 1. Instalowanie powłoki zarządzania SharePoint Online

Pierwszym krokiem jest zainstalowanie powłoki zarządzania SharePoint Online. Nie musisz używać powłoki w tej procedurze, ale musisz ją zainstalować, ponieważ zawiera wymagania wstępne wymagane przez skrypt uruchomiony w kroku 3. Te wymagania wstępne umożliwiają skryptowi komunikowanie się z usługą SharePoint Online w celu pobrania adresów URL witryn OneDrive dla Firm.
  
Przejdź do [obszaru Konfigurowanie środowiska Windows PowerShell powłoki zarządzania SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) i wykonaj kroki 1 i 2, aby zainstalować powłokę zarządzania SharePoint Online.
  
## <a name="step-2-generate-a-list-of-users"></a>Krok 2. Generowanie listy użytkowników

Skrypt w kroku 3 utworzy wyszukiwanie zawartości, aby wyszukać listę użytkowników w skrzynkach pocztowych i kontach OneDrive. Możesz po prostu wpisać adresy e-mail w pliku tekstowym lub uruchomić polecenie w Windows PowerShell, aby uzyskać listę adresów e-mail i zapisać je w pliku (znajdującym się w tym samym folderze, w jakim zapiszesz skrypt w kroku 3).
  
Oto [polecenie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), które można uruchomić, aby uzyskać listę adresów e-mail dla wszystkich użytkowników w organizacji i zapisać je w pliku tekstowym o nazwie `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Po uruchomieniu tego polecenia otwórz plik i usuń nagłówek zawierający nazwę  `PrimarySmtpAddress`właściwości . Plik tekstowy powinien zawierać tylko listę adresów e-mail i nic więcej. Upewnij się, że nie ma pustych wierszy przed lub po liście adresów e-mail.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>Krok 3. Uruchamianie skryptu w celu utworzenia i rozpoczęcia wyszukiwania

Po uruchomieniu skryptu w tym kroku zostanie wyświetlony monit o podanie następujących informacji. Pamiętaj, aby te informacje były gotowe przed uruchomieniem skryptu.
  
- **Poświadczenia użytkownika** — skrypt użyje poświadczeń w celu uzyskania dostępu do SharePoint Online w celu uzyskania adresów URL OneDrive dla Firm i nawiązania połączenia z programem PowerShell Centrum zgodności usługi Security &. 
    
- **Nazwa domeny witryny MySite** — domena MySite to domena, która zawiera wszystkie witryny OneDrive dla Firm w organizacji. Jeśli na przykład adres URL domeny witryny MySite to **https://contoso-my.sharepoint.com**, należy wprowadzić  `contoso` , gdy skrypt wyświetli monit o podanie nazwy domeny witryny MySite. 
    
- **Nazwa ścieżki pliku tekstowego z kroku 2** — nazwa ścieżki pliku tekstowego utworzonego w kroku 2. Jeśli plik tekstowy i skrypt znajdują się w tym samym folderze, wprowadź nazwę pliku tekstowego. W przeciwnym razie wprowadź pełną nazwę ścieżki pliku tekstowego. 
    
- **Nazwa wyszukiwania zawartości** — nazwa wyszukiwania zawartości, która zostanie utworzona przez skrypt. 
    
- **Zapytanie wyszukiwania** — zapytanie wyszukiwania, które będzie używane z wyszukiwaniem zawartości, jest tworzone i uruchamiane. Aby uzyskać więcej informacji na temat zapytań wyszukiwania, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).


**Aby uruchomić skrypt:**
    
1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, `SearchEXOOD4B.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zapisano listę użytkowników w kroku 2.
    
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

2. Otwórz Windows PowerShell i przejdź do folderu, w którym zapisano skrypt i listy użytkowników z kroku 2.
    
3. Uruchom skrypt; na przykład:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Po wyświetleniu monitu o podanie poświadczeń wprowadź adres e-mail i hasło, a następnie kliknij przycisk **OK**. 
    
5. Wprowadź następujące informacje po wyświetleniu monitu przez skrypt. Wpisz każdą informację, a następnie naciśnij **klawisz Enter**.
    
    - Nazwa domeny witryny MySite. 
    
    - Nazwa ścieżki pliku tekstowego zawierającego listę użytkowników.
    
    - Nazwa wyszukiwania zawartości.
    
    - Zapytanie wyszukiwania (pozostaw to puste, aby zwrócić wszystkie elementy w lokalizacjach zawartości).
    
    Skrypt pobiera adresy URL dla każdej OneDrive dla Firm lokacji, a następnie tworzy i uruchamia wyszukiwanie. Możesz uruchomić polecenie cmdlet **Get-ComplianceSearch** w programie PowerShell Security & Compliance Center, aby wyświetlić statystyki wyszukiwania i wyniki, lub przejść do strony **wyszukiwania zawartości** w portalu zgodności, aby wyświetlić informacje o wyszukiwaniu.
