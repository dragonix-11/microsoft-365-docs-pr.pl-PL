---
title: Używanie wyszukiwania zawartości dla kolekcji docelowych
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
description: Użyj wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview, aby wykonać docelową kolekcję, która wyszukuje elementy w określonej skrzynce pocztowej lub folderze witryny.
ms.openlocfilehash: 9638a0870f1d97d2bcea73215509d269576c4ecd
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64991781"
---
# <a name="use-content-search-for-targeted-collections"></a>Używanie wyszukiwania zawartości dla kolekcji docelowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Narzędzie do wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview nie zapewnia bezpośredniego sposobu wyszukiwania określonych folderów w Exchange skrzynkach pocztowych lub SharePoint i witrynach OneDrive dla Firm. Można jednak przeszukać określone foldery (nazywane *kolekcją docelową*), określając właściwość identyfikatora folderu dla właściwości poczty e-mail lub ścieżki (DocumentLink) dla witryn w rzeczywistej składni zapytania wyszukiwania. Używanie wyszukiwania zawartości do wykonywania docelowej kolekcji jest przydatne, gdy masz pewność, że elementy reagujące na przypadek lub uprzywilejowane elementy znajdują się w określonej skrzynce pocztowej lub folderze witryny. Skrypt w tym artykule umożliwia uzyskanie identyfikatora folderu dla folderów skrzynki pocztowej lub ścieżki (DocumentLink) dla folderów w witrynie SharePoint i OneDrive dla Firm. Następnie możesz użyć identyfikatora folderu lub ścieżki w zapytaniu wyszukiwania, aby zwrócić elementy znajdujące się w folderze.

> [!NOTE]
> Aby zwrócić zawartość znajdującą się w folderze w witrynie SharePoint lub OneDrive dla Firm, skrypt w tym temacie używa właściwości zarządzanej DocumentLink zamiast właściwości Ścieżka. Właściwość DocumentLink jest bardziej niezawodna niż właściwość Path, ponieważ zwróci całą zawartość w folderze, natomiast właściwość Path nie zwróci niektórych plików multimedialnych.

## <a name="before-you-run-a-targeted-collection"></a>Przed uruchomieniem docelowej kolekcji

- Aby uruchomić skrypt w kroku 1, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Musisz również mieć przypisaną rolę Adresaci poczty w organizacji Exchange Online. Jest to wymagane do uruchomienia polecenia cmdlet **Get-MailboxFolderStatistics** , które jest zawarte w skryptze. Domyślnie rola Adresaci poczty jest przypisywana do grup ról Zarządzanie organizacjami i zarządzanie adresatami w Exchange Online. Aby uzyskać więcej informacji na temat przypisywania uprawnień w Exchange Online, zobacz [Zarządzanie członkami grupy ról](/exchange/manage-role-group-members-exchange-2013-help). Można również utworzyć niestandardową grupę ról, przypisać do niej rolę Adresaci poczty, a następnie dodać członków, którzy muszą uruchomić skrypt w kroku 1. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami ról](/Exchange/permissions-exo/role-groups).

- Skrypt w tym artykule obsługuje nowoczesne uwierzytelnianie. Możesz użyć skryptu w taki sam jak jest, jeśli jesteś Microsoft 365 lub organizacją Microsoft 365 GCC. Jeśli jesteś organizacją Office 365 Niemczech, organizacją Microsoft 365 GCC High lub organizacją Microsoft 365 DoD, musisz edytować skrypt, aby pomyślnie go uruchomić. W szczególności musisz edytować wiersz `Connect-ExchangeOnline` i użyć parametru *ExchangeEnvironmentName* (i odpowiedniej wartości dla typu organizacji), aby nawiązać połączenie z programem Exchange Online programu PowerShell.  Ponadto musisz edytować wiersz `Connect-IPPSSession` i użyć parametrów *ConnectionUri* i *AzureADAuthorizationEndpointUri* (i odpowiednich wartości dla typu organizacji), aby nawiązać połączenie z programem PowerShell Centrum zgodności usługi Security &. Aby uzyskać więcej informacji, zobacz przykłady w [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) i [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Za każdym razem, gdy uruchamiasz skrypt, tworzona jest nowa zdalna sesja programu PowerShell. Oznacza to, że możesz użyć wszystkich dostępnych zdalnych sesji programu PowerShell. Aby temu zapobiec, uruchom następujące polecenie, aby rozłączyć aktywne zdalne sesje programu PowerShell.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    Aby uzyskać więcej informacji, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Skrypt zawiera minimalną obsługę błędów. Podstawowym celem skryptu jest szybkie wyświetlenie listy identyfikatorów folderów skrzynki pocztowej lub ścieżek lokacji, których można użyć w składni zapytania wyszukiwania wyszukiwania zawartości w celu wykonania docelowej kolekcji.

- Przykładowy skrypt podany w tym temacie nie jest obsługiwany w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowy skrypt jest dostarczany jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowego skryptu i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>Krok 1. Uruchamianie skryptu w celu pobrania listy folderów dla skrzynki pocztowej lub witryny

Skrypt uruchomiony w tym pierwszym kroku zwróci listę folderów skrzynki pocztowej lub folderów SharePoint i OneDrive dla Firm oraz odpowiedni identyfikator folderu lub ścieżkę dla każdego folderu. Po uruchomieniu tego skryptu zostanie wyświetlony monit o podanie następujących informacji.

- **Adres e-mail lub adres URL witryny**: wpisz adres e-mail opiekuna, aby zwrócić listę Exchange folderów skrzynki pocztowej i identyfikatorów folderów. Możesz też wpisać adres URL witryny SharePoint lub witryny OneDrive dla Firm, aby zwrócić listę ścieżek dla określonej witryny. Oto kilka przykładów:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive dla Firm**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Poświadczenia użytkownika**: skrypt będzie używać poświadczeń w celu nawiązania połączenia z programem Exchange Online programu PowerShell lub programu PowerShell & Security & Compliance Center przy użyciu nowoczesnego uwierzytelniania. Jak wyjaśniono wcześniej, musisz mieć przypisane odpowiednie uprawnienia, aby pomyślnie uruchomić ten skrypt.

Aby wyświetlić listę folderów skrzynki pocztowej lub nazw linku dokumentu witryny (ścieżki):

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, `GetFolderSearchParameters.ps1`na przykład .

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the compliance portal.            #
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
   # Authenticate with Exchange Online and the compliance portal (Exchange Online Protection - EOP)
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

2. Na komputerze lokalnym otwórz Windows PowerShell i przejdź do folderu, w którym zapisano skrypt.

3. Uruchom skrypt; na przykład:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Wprowadź informacje, o które monituje skrypt.

    Skrypt wyświetla listę folderów skrzynki pocztowej lub folderów lokacji dla określonego użytkownika. Pozostaw to okno otwarte, aby można było skopiować identyfikator folderu lub nazwę łącza dokumentu i wkleić go do zapytania wyszukiwania w kroku 2.

    > [!TIP]
    > Zamiast wyświetlać listę folderów na ekranie komputera, można ponownie skierować dane wyjściowe skryptu do pliku tekstowego. Ten plik zostanie zapisany w folderze, w którym znajduje się skrypt. Aby na przykład przekierować dane wyjściowe skryptu do pliku tekstowego, uruchom następujące polecenie w kroku 3.  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` Następnie możesz skopiować identyfikator folderu lub link dokumentu z pliku, aby użyć go w zapytaniu wyszukiwania.

### <a name="script-output-for-mailbox-folders"></a>Dane wyjściowe skryptu dla folderów skrzynki pocztowej

Jeśli otrzymujesz identyfikatory folderów skrzynki pocztowej, skrypt nawiązuje połączenie z programem Exchange Online programu PowerShell, uruchamia polecenie cmdlet **Get-MailboxFolderStatisics**, a następnie wyświetla listę folderów z określonej skrzynki pocztowej. Dla każdego folderu w skrzynce pocztowej skrypt wyświetla nazwę folderu w kolumnie **FolderPath** i identyfikator folderu w kolumnie **FolderQuery** . Ponadto skrypt dodaje prefiks **folderId** (czyli nazwę właściwości skrzynki pocztowej) do identyfikatora folderu. Ponieważ **właściwość folderid** jest właściwością z możliwością wyszukiwania, użyjesz  `folderid:<folderid>` w zapytaniu wyszukiwania w kroku 2, aby przeszukać ten folder. 

> [!IMPORTANT]
> Skrypt w tym artykule zawiera logikę kodowania, która konwertuje 64-znakowe wartości identyfikatora folderu zwracane przez **funkcję Get-MailboxFolderStatistics** na ten sam format 48 znaków, który jest indeksowany do wyszukiwania. Jeśli po prostu uruchomisz polecenie cmdlet **Get-MailboxFolderStatistics** w programie PowerShell, aby uzyskać identyfikator folderu (zamiast uruchamiać skrypt w tym artykule), zapytanie wyszukiwania używające tej wartości identyfikatora folderu zakończy się niepowodzeniem. Musisz uruchomić skrypt, aby uzyskać poprawnie sformatowane identyfikatory folderów, które mogą być używane w wyszukiwaniu zawartości.

Oto przykład danych wyjściowych zwracanych przez skrypt dla folderów skrzynki pocztowej.

![Przykład listy folderów skrzynki pocztowej i identyfikatorów folderów zwróconych przez skrypt.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

W przykładzie w kroku 2 przedstawiono zapytanie używane do przeszukiwania podfolderu Przeczyszczanie w folderze Elementy możliwe do odzyskania użytkownika.

### <a name="script-output-for-site-folders"></a>Dane wyjściowe skryptu dla folderów lokacji

Jeśli otrzymujesz ścieżkę właściwości **documentlink** z witryn SharePoint lub OneDrive dla Firm, skrypt łączy się z programem PowerShell security & Compliance, tworzy nowe wyszukiwanie zawartości, które wyszukuje foldery w witrynie, a następnie wyświetla listę folderów znajdujących się w określonej lokacji. Skrypt wyświetla nazwę każdego folderu i dodaje prefiks **linku documentlink** do adresu URL folderu. Ponieważ właściwość **documentlink** jest właściwością z możliwością wyszukiwania, użyjesz `documentlink:<path>` pary property:value w zapytaniu wyszukiwania w kroku 2, aby przeszukać ten folder. Skrypt wyświetla maksymalnie 100 folderów lokacji. Jeśli istnieje więcej niż 100 folderów lokacji, zostaną wyświetlone najnowsze foldery.

Oto przykład danych wyjściowych zwracanych przez skrypt dla folderów lokacji.

![Przykład listy nazw linków dokumentów dla folderów lokacji zwróconych przez skrypt.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>Krok 2. Używanie identyfikatora folderu lub łącza dokumentu do wykonywania docelowej kolekcji

Po uruchomieniu skryptu w celu zebrania listy identyfikatorów folderów lub linków dokumentów dla określonego użytkownika następnym krokiem jest przejście do portalu zgodności i utworzenie nowego wyszukiwania zawartości w celu wyszukania określonego folderu. Użyjesz  `folderid:<folderid>` pary lub  `documentlink:<path>` property:value w zapytaniu wyszukiwania skonfigurowanym w polu słowa kluczowego Wyszukiwania zawartości (lub jako wartości parametru  *ContentMatchQuery*  , jeśli używasz polecenia cmdlet **New-ComplianceSearch** ). Możesz połączyć  `folderid` właściwość lub  `documentlink` z innymi parametrami wyszukiwania lub warunkami wyszukiwania. Jeśli do zapytania dołączysz  `folderid` tylko właściwość lub  `documentlink` , wyszukiwanie zwróci wszystkie elementy znajdujące się w określonym folderze.

1. Przejdź do strony <https://compliance.microsoft.com> i zaloguj się przy użyciu konta i poświadczeń użytych do uruchomienia skryptu w kroku 1.

2. W lewym okienku centrum zgodności kliknij pozycję **Pokaż** **wszystkieKontenerowanie** > , a następnie kliknij pozycję **Nowe wyszukiwanie**.

3. W polu **Słowa kluczowe** wklej `folderid:<folderid>` wartość lub  `documentlink:<path>/*` zwróconą przez skrypt w kroku 1.

    Na przykład zapytanie na poniższym zrzucie ekranu wyszuka dowolny element w podfoldecie Przeczyszczanie w folderze Elementy możliwe do odzyskania użytkownika (wartość `folderid` właściwości podfolderu Przeczyszczanie jest wyświetlana na zrzucie ekranu w kroku 1):

    ![Wklej folderid lub documentlink w polu słowa kluczowego zapytania wyszukiwania.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > Wyszukiwanie linku documentlink wymaga użycia końcowego  `asterisk '/*'`elementu .  

4. W obszarze **Lokalizacje** wybierz pozycję **Określone lokalizacje** , a następnie kliknij przycisk **Modyfikuj**.

5. Wykonaj jedną z następujących czynności w zależności od tego, czy wyszukujesz folder skrzynki pocztowej, czy folder witryny:

    - Obok **Exchange wiadomości e-mail** kliknij pozycję **Wybierz użytkowników, grupy lub zespoły,** a następnie dodaj tę samą skrzynkę pocztową, którą określono podczas uruchamiania skryptu w kroku 1.

      Lub

    - Obok **SharePoint witryn** kliknij pozycję **Wybierz witryny**, a następnie dodaj ten sam adres URL witryny określony podczas uruchamiania skryptu w kroku 1.

6. Po zapisaniu lokalizacji zawartości do wyszukiwania kliknij pozycję **Zapisz & uruchomienia**, wpisz nazwę wyszukiwania zawartości, a następnie kliknij przycisk **Zapisz** , aby rozpocząć wyszukiwanie docelowej kolekcji.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Przykłady zapytań wyszukiwania dla kolekcji docelowych

Oto kilka przykładów użycia  `folderid` właściwości i  `documentlink` w zapytaniu wyszukiwania do wykonania docelowej kolekcji. Symbole zastępcze są używane do  `folderid:<folderid>` i  `documentlink:<path>` do oszczędzania miejsca.

- Ten przykład wyszukuje trzy różne foldery skrzynki pocztowej. Podobnej składni zapytania można użyć do przeszukiwania ukrytych folderów w folderze elementów możliwych do odzyskania użytkownika.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- Ten przykład wyszukuje w folderze skrzynki pocztowej elementy zawierające dokładną frazę.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- Ten przykład wyszukuje folder witryny (i wszystkie podfoldery) w poszukiwaniu dokumentów zawierających litery "NDA" w tytule.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- Ten przykład wyszukuje folder witryny (i dowolny podfolder) w poszukiwaniu dokumentów, które zostały zmienione w zakresie dat.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Więcej informacji

Podczas używania skryptu w tym artykule do wykonywania kolekcji docelowych należy pamiętać o następujących kwestiach.

- Skrypt nie usuwa żadnych folderów z wyników. Dlatego niektóre foldery wymienione w wynikach mogą być nie do zarchiwizowane (lub zwracać zero elementów), ponieważ zawierają zawartość wygenerowaną przez system lub zawierają tylko podfoldery, a nie elementy skrzynki pocztowej.

- Ten skrypt zwraca tylko informacje o folderze dla podstawowej skrzynki pocztowej użytkownika. Nie zwraca informacji o folderach w archiwum skrzynki pocztowej użytkownika. Aby zwrócić informacje o folderach w archiwum skrzynki pocztowej użytkownika, możesz edytować skrypt. W tym celu zmień wiersz `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` na `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` , a następnie zapisz i uruchom edytowany skrypt. Ta zmiana spowoduje zwrócenie identyfikatorów folderów dla folderów i podfolderów w skrzynce pocztowej archiwum użytkownika. Aby przeszukać całą skrzynkę pocztową archiwum, możesz połączyć wszystkie pary identyfikatora folderu:wartość z operatorem `OR` w zapytaniu wyszukiwania.

- Podczas przeszukiwania folderów skrzynki pocztowej przeszukiwany będzie tylko określony folder (zidentyfikowany przez jego `folderid` właściwość). Podfoldery nie będą przeszukiwane. Aby wyszukać podfoldery, należy użyć identyfikatora folderu dla podfolderu, który chcesz wyszukać.

- Podczas przeszukiwania folderów lokacji zostanie przeszukany folder (zidentyfikowany przez jego `documentlink` właściwość) i wszystkie podfoldery.

- Podczas eksportowania wyników wyszukiwania, w którym określono `folderid` tylko właściwość w zapytaniu wyszukiwania, można wybrać pierwszą opcję eksportu "Wszystkie elementy, z wyłączeniem tych, które mają nierozpoznany format, są szyfrowane lub nie zostały z innych powodów indeksowane". Wszystkie elementy w folderze będą zawsze eksportowane niezależnie od ich stanu indeksowania, ponieważ identyfikator folderu jest zawsze indeksowany.
