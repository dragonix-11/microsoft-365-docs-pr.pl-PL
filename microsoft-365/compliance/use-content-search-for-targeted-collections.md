---
title: Używanie wyszukiwania zawartości dla kolekcji docelowej
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
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: Przeszukiwanie zawartości w Centrum zgodności platformy Microsoft 365 celu wykonania docelowej kolekcji, która wyszukuje elementy w określonej skrzynce pocztowej lub folderze witryny.
ms.openlocfilehash: 9de0c562f570a3028c7a96698241ac1be06b8ec1
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63013759"
---
# <a name="use-content-search-for-targeted-collections"></a>Używanie wyszukiwania zawartości dla kolekcji docelowej

Narzędzie Przeszukiwanie zawartości w aplikacji Centrum zgodności platformy Microsoft 365 nie umożliwia wyszukiwania bezpośrednio w interfejsie użytkownika określonych folderów w skrzynkach pocztowych usługi Exchange lub SharePoint i OneDrive dla Firm witrynach. Można jednak przeszukiwać określone foldery (nazywane kolekcją docelową *) przez* określenie właściwości identyfikator folderu dla poczty e-mail lub właściwości ścieżka (DocumentLink) dla witryn w rzeczywistej składni zapytania wyszukiwania. Korzystanie z wyszukiwania zawartości w celu wykonania docelowej kolekcji jest przydatne, gdy masz pewność, że elementy reagujące na konkretną sprawę lub elementy uprzywilejowany znajdują się w określonej skrzynce pocztowej lub folderze witryny. Za pomocą skryptu w tym artykule można uzyskać identyfikator folderu dla folderów skrzynki pocztowej lub ścieżkę (DocumentLink) dla folderów w witrynie sieci SharePoint i OneDrive dla Firm pocztowej. Następnie możesz użyć identyfikatora folderu lub ścieżki w zapytaniu wyszukiwania, aby zwrócić elementy znajdujące się w tym folderze.

> [!NOTE]
> Aby zwrócić zawartość znajdującą się w folderze w witrynie programu SharePoint lub OneDrive dla Firm, skrypt w tym temacie używa właściwości zarządzanej DocumentLink, a nie właściwości Path. Właściwość DocumentLink jest bardziej niezawodna niż właściwość Path, ponieważ zwraca całą zawartość w folderze, natomiast właściwość Path nie zwraca niektórych plików multimedialnych.

## <a name="before-you-run-a-targeted-collection"></a>Przed uruchomieniem kolekcji docelowej

- Aby uruchomić skrypt w kroku 1, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w grupie Centrum zgodności platformy Microsoft 365. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Musisz także mieć przypisaną rolę adresatów poczty w twojej Exchange Online organizacji. Jest to wymagane do uruchomienia polecenia **cmdlet Get-MailboxFolderStatistics** dołączonego do skryptu. Domyślnie rola Adresaci poczty jest przypisana do grup ról Zarządzanie organizacją i Zarządzanie adresatami w programie Exchange Online. Aby uzyskać więcej informacji na temat przypisywania uprawnień w Exchange Online, zobacz [Zarządzanie członkami grupy ról](/exchange/manage-role-group-members-exchange-2013-help). Możesz również utworzyć niestandardową grupę ról, przypisać do tej roli adresatów poczty, a następnie dodać członków, którzy muszą uruchomić skrypt w kroku 1. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami ról](/Exchange/permissions-exo/role-groups).

- Skrypt w tym artykule obsługuje nowoczesne uwierzytelnianie. Skryptu można używać w stanie, w jaki jest, jeśli jesteś Microsoft 365 lub Microsoft 365 GCC organizacją. W przypadku organizacji Office 365 Germany, Microsoft 365 GCC High Organization lub organizacji doD Microsoft 365 DoD należy edytować skrypt, aby pomyślnie go uruchomić. W szczególności należy edytować `Connect-ExchangeOnline` wiersz i użyć parametru *ExchangeEnvironmentName* (oraz odpowiedniej wartości dla typu organizacji), aby połączyć się z programem Exchange Online PowerShell.  `Connect-IPPSSession` Ponadto musisz edytować linię i użyć parametrów *ConnectionUri* oraz *AzureADAuthorizationEndpointUri* (oraz odpowiednich wartości dla typu organizacji), aby połączyć się z programem PowerShell centrum zabezpieczeń & zgodności. Aby uzyskać więcej informacji, zobacz przykłady w te Połączenie do Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) i Połączenie do programu [PowerShell & Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Przy każdym uruchomieniu skryptu jest tworzona nowa zdalna sesja programu PowerShell. Oznacza to, że możesz korzystać ze wszystkich dostępnych zdalnych sesji programu PowerShell. Aby temu zapobiec, uruchom następujące polecenie w celu odłączenia aktywnych zdalnych sesji programu PowerShell.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    Aby uzyskać więcej informacji, zobacz [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Skrypt zawiera minimalną obsługę błędów. Głównym celem skryptu jest szybkie wyświetlenie listy identyfikatorów folderów skrzynek pocztowych lub ścieżek witryn, których można użyć w składni zapytania wyszukiwania przeszukiwania w celu wykonania docelowej kolekcji.

- Przykładowy skrypt podany w tym temacie nie jest obsługiwany w żadnym standardowym programie lub usłudze pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>Krok 1. Uruchamianie skryptu w celu uzyskania listy folderów skrzynki pocztowej lub witryny

Skrypt uruchomiony w tym pierwszym kroku zwróci listę folderów skrzynek pocztowych lub folderów SharePoint i OneDrive dla Firm oraz identyfikator lub ścieżkę odpowiedniego folderu dla każdego folderu. Po uruchomieniu tego skryptu zostanie wyświetlony monit o następujące informacje.

- **Adres e-mail lub adres URL** witryny: Wpisz adres e-mail osoby- adresata, aby Exchange foldery skrzynek pocztowych i identyfikatory folderów. Albo wpisz adres URL witryny SharePoint lub witryny sieci OneDrive dla Firm, aby zwrócić listę ścieżek dla określonej witryny. Oto kilka przykładów:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive dla Firm**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Poświadczenia użytkownika: Skrypt użyje** Twoich poświadczeń, aby połączyć się z programem PowerShell Exchange Online lub Centrum zgodności & Security & PowerShell przy użyciu nowoczesnego uwierzytelniania. Jak wyjaśniono wcześniej, musisz mieć odpowiednie uprawnienia, aby pomyślnie uruchomić ten skrypt.

Aby wyświetlić listę folderów skrzynki pocztowej lub nazwy ścieżki łącza do dokumentu witryny:

1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `GetFolderSearchParameters.ps1`na przykład .

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the Microsoft 365 compliance center.            #
   # The script will then:                                            #
   #    * If an email address is supplied: list the folders for the target mailbox.            #
   #    * If a SharePoint or OneDrive for Business site is supplied: list the documentlinks (folder paths) #
   #    * for the site.                                                                                    #
   #    * In both cases, the script supplies the correct search properties (folderid: or documentlink:)    #
   #      appended to the folder ID or documentlink to use in a Content Search.                #
   # Notes:                                                #
   #    * For SharePoint and OneDrive for Business, the paths are searched recursively; this means the     #
   #      the current folder and all sub-folders are searched.                        #
   #    * For Exchange, only the specified folder will be searched; this means sub-folders in the folder    #
   #      will not be searched.  To search sub-folders, you need to use the specify the folder ID for    #
   #      each sub-folder that you want to search.                                #
   #    * For Exchange, only folders in the user's primary mailbox will be returned by the script.        #
   #########################################################################################################
   # Collect the target email address or SharePoint Url
   $addressOrSite = Read-Host "Enter an email address or a URL for a SharePoint or OneDrive for Business site"
   # Authenticate with Exchange Online and the Microsoft 365 compliance center (Exchange Online Protection - EOP)
   if ($addressOrSite.IndexOf("@") -ige 0)
   {
      # List the folder Ids for the target mailbox
      $emailAddress = $addressOrSite
      # Connect to Exchange Online PowerShell
      if (!$ExoSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-ExchangeOnline -ShowBanner:$false -CommandName Get-MailboxFolderStatistics
      }
      $folderQueries = @()
      $folderStatistics = Get-MailboxFolderStatistics $emailAddress
      foreach ($folderStatistic in $folderStatistics)
      {
          $folderId = $folderStatistic.FolderId;
          $folderPath = $folderStatistic.FolderPath;
          $encoding= [System.Text.Encoding]::GetEncoding("us-ascii")
          $nibbler= $encoding.GetBytes("0123456789ABCDEF");
          $folderIdBytes = [Convert]::FromBase64String($folderId);
          $indexIdBytes = New-Object byte[] 48;
          $indexIdIdx=0;
          $folderIdBytes | select -skip 23 -First 24 | %{$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -shr 4];$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -band 0xF]}
          $folderQuery = "folderid:$($encoding.GetString($indexIdBytes))";
          $folderStat = New-Object PSObject
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderPath -Value $folderPath
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderQuery -Value $folderQuery
          $folderQueries += $folderStat
      }
      Write-Host "-----Exchange Folders-----"
      $folderQueries |ft
   }
   elseif ($addressOrSite.IndexOf("http") -ige 0)
   {
      $searchName = "SPFoldersSearch"
      $searchActionName = "SPFoldersSearch_Preview"
      # List the folders for the SharePoint or OneDrive for Business Site
      $siteUrl = $addressOrSite
      # Connect to Security & Compliance Center PowerShell
      if (!$SccSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-IPPSSession
      }
      # Clean-up, if the script was aborted, the search we created might not have been deleted.  Try to do so now.
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
      # Create a Content Search against the SharePoint Site or OneDrive for Business site and only search for folders; wait for the search to complete
      $complianceSearch = New-ComplianceSearch -Name $searchName -ContentMatchQuery "contenttype:folder" -SharePointLocation $siteUrl
      Start-ComplianceSearch $searchName
      do{
          Write-host "Waiting for search to complete..."
          Start-Sleep -s 5
          $complianceSearch = Get-ComplianceSearch $searchName
      }while ($complianceSearch.Status -ne 'Completed')
      if ($complianceSearch.Items -gt 0)
      {
          # Create a Compliance Search Action and wait for it to complete. The folders will be listed in the .Results parameter
          $complianceSearchAction = New-ComplianceSearchAction -SearchName $searchName -Preview
          do
          {
              Write-host "Waiting for search action to complete..."
              Start-Sleep -s 5
              $complianceSearchAction = Get-ComplianceSearchAction $searchActionName
          }while ($complianceSearchAction.Status -ne 'Completed')
          # Get the results and print out the folders
          $results = $complianceSearchAction.Results
          $matches = Select-String "Data Link:.+[,}]" -Input $results -AllMatches
          foreach ($match in $matches.Matches)
          {
              $rawUrl = $match.Value
              $rawUrl = $rawUrl -replace "Data Link: " -replace "," -replace "}"
              Write-Host "DocumentLink:""$rawUrl"""
          }
      }
      else
      {
          Write-Host "No folders were found for $siteUrl"
      }
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
   }
   else
   {
      Write-Error "Couldn't recognize $addressOrSite as an email address or a site URL"
   }
   ```

2. Na komputerze lokalnym otwórz program Windows PowerShell i przejdź do folderu, w którym został zapisany skrypt.

3. Uruchom skrypt. na przykład:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Wprowadź informacje, o które zostanie wyświetlony monit skryptu.

    Skrypt wyświetli listę folderów skrzynki pocztowej lub folderów witryny dla określonego użytkownika. Pozostaw to okno otwarte, aby skopiować identyfikator folderu lub nazwę linku do dokumentu i wkleić go do zapytania wyszukiwania w kroku 2.

    > [!TIP]
    > Zamiast wyświetlania listy folderów na ekranie komputera możesz ponownie skierować dane wyjściowe skryptu do pliku tekstowego. Ten plik zostanie zapisany w folderze, w którym znajduje się skrypt. Aby na przykład przekierować dane wyjściowe skryptu do pliku tekstowego, uruchom następujące polecenie w kroku 3:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` Następnie możesz skopiować identyfikator folderu lub link do dokumentu z pliku, aby użyć go w zapytaniu wyszukiwania.

### <a name="script-output-for-mailbox-folders"></a>Dane wyjściowe skryptu dla folderów skrzynki pocztowej

Jeśli otrzymasz identyfikatory folderów skrzynek pocztowych, skrypt połączy się z programem Exchange Online PowerShell, uruchomi polecenie cmdlet **Get-MailboxFolderStatisics**, a następnie wyświetli listę folderów z określonej skrzynki pocztowej. W przypadku każdego folderu w skrzynce pocztowej skrypt wyświetla nazwę folderu w kolumnie **FolderPath** i identyfikator folderu w kolumnie **FolderQuery** . Ponadto skrypt dodaje do identyfikatora folderu prefiks **folderId** (czyli nazwę właściwości skrzynki pocztowej). Ponieważ właściwość **folderid** jest właściwością, która można przeszukiwać,  `folderid:<folderid>` użyjesz jej w zapytaniu wyszukiwania w kroku 2, aby przeszukać ten folder. Skrypt wyświetla maksymalnie 100 folderów skrzynki pocztowej.

> [!IMPORTANT]
> Skrypt w tym artykule zawiera logikę kodowania, która konwertuje 64-znakowe wartości identyfikatorów folderów zwracanych przez **get-MailboxFolderStatistics** na ten sam 48-znakowy format, który jest indeksowany w celu wyszukiwania. Jeśli po prostu uruchomysz polecenie cmdlet **Get-MailboxFolderStatistics** w programie PowerShell w celu uzyskania identyfikatora folderu (zamiast uruchamiania skryptu w tym artykule), zapytanie wyszukiwania, które używa tej wartości identyfikatora folderu, nie powiedzie się. Aby uzyskać prawidłowo sformatowane identyfikatory folderów, których można używać podczas przeszukiwania zawartości, należy uruchomić skrypt.

Oto przykład wyniku zwróconego przez skrypt dla folderów skrzynki pocztowej.

![Przykład listy folderów skrzynek pocztowych i identyfikatorów folderów zwróconych przez skrypt.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

W przykładzie w kroku 2 przedstawiono kwerendę używaną do przeszukiwania podfolderu Oczyszczanie w folderze Elementy do odzyskania użytkownika.

### <a name="script-output-for-site-folders"></a>Dane wyjściowe skryptów dla folderów witryny

Jeśli ścieżka właściwości **documentlinku** jest wyświetlana z witryn programu SharePoint lub OneDrive dla Firm, skrypt nawiązuje połączenie z programem PowerShell zabezpieczeń & zgodności, tworzy nowe wyszukiwanie zawartości w witrynie w poszukiwaniu folderów, a następnie wyświetla listę folderów znajdujących się w określonej witrynie. Skrypt wyświetli nazwę każdego folderu i doda prefiks **linku do dokumentu** do adresu URL folderu. Ponieważ właściwość **linku do dokumentu** jest właściwością, która można przeszukiwać, `documentlink:<path>` w zapytaniu wyszukiwania w kroku 2 użyjesz pary właściwość:wartość do przeszukiwania tego folderu. Skrypt wyświetla maksymalnie 200 folderów witryny. Jeśli istnieje więcej niż 200 folderów witryny, są wyświetlane najnowsze z nich.

Oto przykład wyniku zwróconego przez skrypt dla folderów witryny.

![Przykład listy nazw linków do dokumentów dla folderów witryny zwróconych przez skrypt.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>Krok 2. Wykonywanie docelowej kolekcji za pomocą identyfikatora folderu lub łącza do dokumentu

Po uruchomieniu skryptu w celu zebrania listy identyfikatorów folderów lub linków do dokumentów dla określonego użytkownika należy przejść do witryny Centrum zgodności platformy Microsoft 365 i utworzyć nowe wyszukiwanie zawartości w celu przeszukania określonego folderu. W zapytaniu `folderid:<folderid>` wyszukiwania skonfigurowanym w polu słowa kluczowego Przeszukiwanie zawartości (lub jako wartości parametru *ContentMatchQuery*, jeśli używasz polecenia cmdlet **New-ComplianceSearch**) użyjesz pary or `documentlink:<path>` property:value. Możesz połączyć właściwość lub  `folderid` z  `documentlink` innymi parametrami wyszukiwania lub warunkami wyszukiwania. Jeśli uwzględnisz tylko właściwość  `folderid` lub w  `documentlink` zapytaniu, wyszukiwanie zwróci wszystkie elementy znajdujące się w określonym folderze.

1. Przejdź do <https://compliance.microsoft.com> konta i poświadczeń użytych do uruchomienia skryptu w kroku 1 i zaloguj się.

2. W lewym okienku Centrum zgodności kliknij pozycję **Pokaż wszystkieWyszukiwanie** >  **treści**, a następnie kliknij pozycję **Nowe wyszukiwanie**.

3. W polu **Słowa kluczowe** wklej wartości `folderid:<folderid>`  `documentlink:<path>/*` zwrócone przez skrypt w kroku 1.

    Na przykład zapytanie na poniższym zrzucie ekranu spowoduje wyszukanie dowolnego elementu w podfolderze przeczyszczania w folderze Elementy do odzyskania użytkownika ( `folderid` wartość właściwości podfolderu Przeczyszczania jest wyświetlana na zrzucie ekranu w kroku 1):

    ![Wklej folderid lub link do dokumentu w polu słowa kluczowego zapytania wyszukiwania.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > Przeszukiwanie linków do dokumentów wymaga użycia nasyłki końcowej  `asterisk '/*'`.  

4. W **obszarze Lokalizacje** wybierz pozycję **Określone lokalizacje** , a następnie kliknij pozycję **Modyfikuj**.

5. Wykonaj jedną z następujących czynności w zależności od tego, czy przeszukujesz folder skrzynki pocztowej, czy folder witryny:

    - Obok **Exchange** e-mail kliknij pozycję Wybierz użytkowników **,** grupy lub zespoły, a następnie dodaj tę samą skrzynkę pocztową określoną podczas uruchamiania skryptu w kroku 1.

      Lub

    - Obok SharePoint **kliknij** pozycję Wybierz witryny, a następnie  dodaj ten sam adres URL witryny, który został określony podczas uruchamiania skryptu w kroku 1.

6. Po zapisaniu lokalizacji zawartości do wyszukiwania kliknij pozycję Zapisz & **uruchom**, wpisz nazwę przeszukiwania zawartości, a następnie kliknij przycisk Zapisz, aby uruchomić wyszukiwanie  kierowanej kolekcji.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Przykłady zapytań wyszukiwania dla kolekcji docelowej

Oto kilka przykładów użycia właściwości  `folderid` i  `documentlink` w zapytaniu wyszukiwania w celu wykonania docelowej kolekcji. Symbole zastępcze służą do oszczędzania  `folderid:<folderid>`  `documentlink:<path>` miejsca i oszczędzania miejsca.

- W tym przykładzie przeszukane są trzy różne foldery skrzynek pocztowych. Za pomocą podobnej składni zapytania można przeszukiwać foldery ukryte w folderze Elementy do odzyskania użytkownika.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- W tym przykładzie elementy zawierające dokładną frazę są przeszukiwane w folderze skrzynki pocztowej.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- W tym przykładzie folder witryny (i wszystkie podfoldery) zawiera dokumenty zawierające w tytule litery "NDA".

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- Ten przykład wyszukuje w folderze witryny (i dowolnym podfolderze) dokumenty, które w tym folderze zostały zmienione w zakresie dat.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Więcej informacji

Używając skryptu z tego artykułu do wykonywania kolekcji ukierunkowanych, należy pamiętać o następujących kwestiach.

- Skrypt nie usuwa żadnych folderów z wyników. Dlatego niektórych folderów wymienionych w wynikach może nie być można wyszukiwać (lub zwracać elementów zerowych), ponieważ zawierają one zawartość wygenerowaną przez system lub zawierają tylko podfoldery, a nie elementy skrzynki pocztowej.

- Ten skrypt zwraca informacje o folderach tylko dla podstawowej skrzynki pocztowej użytkownika. Nie zwraca informacji o folderach w archiwaowej skrzynce pocztowej użytkownika. Aby zwrócić informacje o folderach w archiwaowej skrzynce pocztowej użytkownika, możesz edytować skrypt. W tym celu zmień wiersz na `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` , a następnie zapisz i uruchom edytowany skrypt. Ta zmiana zwróci identyfikatory folderów i podfolderów w archiwaowej skrzynce pocztowej użytkownika. Aby przeszukać całą archiwacyjną skrzynkę pocztową, możesz połączyć wszystkie pary identyfikatorów folderów:wartość `OR` z operatorem w zapytaniu wyszukiwania.

- Podczas wyszukiwania folderów skrzynki pocztowej jest przeszukiwany tylko określony folder ( `folderid` określony przez jego właściwość), a podfoldery nie są przeszukiwane. Aby wyszukać podfoldery, należy użyć identyfikatora folderu dla podfolderu, który ma zostać przeszukany.

- Podczas wyszukiwania w folderach witryny przeszukiwany jest folder (oznaczony jego `documentlink` właściwością) i wszystkie podfoldery.

- `folderid` Podczas eksportowania wyników wyszukiwania, w którym określono właściwość tylko w zapytaniu wyszukiwania, można wybrać pierwszą opcję eksportowania: "Wszystkie elementy z wyjątkiem elementów, które mają nierozpoznany format, są szyfrowane lub nie zostały zindeksowane z innych powodów". Wszystkie elementy w folderze będą zawsze eksportowane bez względu na ich stan indeksowania, ponieważ identyfikator folderu jest zawsze indeksowany.
