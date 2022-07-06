---
title: Tworzenie, raportowanie i usuwanie wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 1d463dda-a3b5-4675-95d4-83db19c9c4a3
description: Dowiedz się, jak zautomatyzować zadania wyszukiwania zawartości, takie jak tworzenie wyszukiwań i uruchamianie raportów przy użyciu programu PowerShell & zgodności z zabezpieczeniami.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: be456c737188f02cfad245d4a1dc4661f2c611a5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638593"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>Tworzenie, raportowanie i usuwanie wielu wyszukiwań zawartości

 Szybkie tworzenie i raportowanie wyszukiwań odnajdywania jest często ważnym krokiem w procesie zbierania elektronicznych materiałów dowodowych i badań, gdy próbujesz dowiedzieć się więcej o danych bazowych oraz o bogactwie i jakości wyszukiwań. Aby to zrobić, program PowerShell security & Compliance oferuje zestaw poleceń cmdlet do automatyzacji czasochłonnych zadań wyszukiwania zawartości. Te skrypty umożliwiają szybkie i łatwe tworzenie wielu wyszukiwań, a następnie uruchamianie raportów o szacowanych wynikach wyszukiwania, które mogą pomóc w określeniu danej ilości danych. Możesz również użyć skryptów, aby utworzyć różne wersje wyszukiwań, aby porównać wyniki, które każdy z nich generuje. Te skrypty mogą pomóc w szybkim i wydajnym identyfikowaniu i usuwaniu danych.

## <a name="before-you-create-a-content-search"></a>Przed utworzeniem wyszukiwania zawartości

- Aby uruchomić skrypty opisane w tym temacie, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych w portal zgodności Microsoft Purview.

- Aby zebrać listę adresów URL witryn OneDrive dla Firm w organizacji, które można dodać do pliku CSV w kroku 1, zobacz [Tworzenie listy wszystkich lokalizacji usługi OneDrive w organizacji](/onedrive/list-onedrive-urls).

- Pamiętaj, aby zapisać wszystkie pliki utworzone w tym temacie w tym samym folderze. Ułatwi to uruchamianie skryptów.

- Skrypty obejmują minimalną obsługę błędów. Ich głównym celem jest szybkie tworzenie, raportowanie i usuwanie wielu wyszukiwań zawartości.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowe skrypty są dostarczane jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowych skryptów i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>Krok 1. Tworzenie pliku CSV zawierającego informacje o wyszukiwaniach, które chcesz uruchomić

Plik wartości rozdzielanej przecinkami (CSV) utworzony w tym kroku zawiera wiersz dla każdego użytkownika, który chce wyszukać. Możesz przeszukać Exchange Online skrzynkę pocztową użytkownika (w tym skrzynkę pocztową archiwum, jeśli jest włączona) i jego OneDrive dla Firm witrynę. Możesz też wyszukać tylko skrzynkę pocztową lub witrynę OneDrive dla Firm. Możesz również wyszukać dowolną witrynę w organizacji usługi SharePoint Online. Skrypt uruchamiany w kroku 3 utworzy oddzielne wyszukiwanie każdego wiersza w pliku CSV.

1. Skopiuj i wklej następujący tekst do pliku .txt przy użyciu Notatnika. Zapisz ten plik w folderze na komputerze lokalnym. Zapiszesz również inne skrypty w tym folderze.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   Pierwszy wiersz pliku lub wiersz nagłówka zawiera listę parametrów, które będą używane przez polecenie cmdlet **New-ComplianceSearch** (w skrypcie w kroku 3) w celu utworzenia nowego wyszukiwania zawartości. Każda nazwa parametru jest oddzielona przecinkiem. Upewnij się, że w wierszu nagłówka nie ma żadnych spacji. Każdy wiersz w wierszu nagłówka reprezentuje wartości parametrów dla każdego wyszukiwania. Pamiętaj, aby zastąpić dane zastępcze w pliku CSV rzeczywistymi danymi.

2. Otwórz plik .txt w programie Excel, a następnie użyj informacji w poniższej tabeli, aby edytować plik z informacjami dla każdego wyszukiwania.

   ****

   |Parametr|Opis|
   |---|---|
   |`ExchangeLocation`|Adres SMTP skrzynki pocztowej użytkownika.|
   |`SharePointLocation`|Adres URL witryny OneDrive dla Firm użytkownika lub adres URL dowolnej witryny w organizacji. Aby uzyskać adres URL witryny OneDrive dla Firm, użyj następującego formatu: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. Na przykład  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|Zapytanie wyszukiwania dla wyszukiwania. Aby uzyskać więcej informacji na temat tworzenia zapytania wyszukiwania, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md).|
   |`StartDate`|W przypadku wiadomości e-mail data odebrania wiadomości lub po jej odebraniu przez adresata lub wysłaniu przez nadawcę. W przypadku dokumentów w witrynach programu SharePoint lub OneDrive dla Firm data ostatniej modyfikacji dokumentu lub po tej dacie.|
   |`EndDate`|W przypadku wiadomości e-mail data wysłania wiadomości lub przed jej wysłaniem przez użytkownika. W przypadku dokumentów w witrynach programu SharePoint lub OneDrive dla Firm data ostatniej modyfikacji dokumentu lub przed nimi.|
   |

3. Zapisz plik programu Excel jako plik CSV w folderze na komputerze lokalnym. Skrypt utworzony w kroku 3 użyje informacji zawartych w tym pliku CSV do utworzenia wyszukiwań.

## <a name="step-2-connect-to-security--compliance-powershell"></a>Krok 2. Nawiązywanie połączenia z programem PowerShell & zabezpieczeń

Następnym krokiem jest nawiązanie połączenia z programem PowerShell security & Compliance dla organizacji. Aby uzyskać instrukcje krok po kroku, zobacz [Connect to Security & Compliance PowerShell (Łączenie z programem PowerShell & zgodności z zabezpieczeniami](/powershell/exchange/connect-to-scc-powershell)).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>Krok 3. Uruchamianie skryptu w celu utworzenia i rozpoczęcia wyszukiwania

Skrypt w tym kroku utworzy oddzielne wyszukiwanie zawartości dla każdego wiersza w pliku CSV utworzonym w kroku 1. Po uruchomieniu tego skryptu zostanie wyświetlony monit o podanie dwóch wartości:

- **Identyfikator grupy wyszukiwania** — ta nazwa umożliwia łatwe organizowanie wyszukiwań utworzonych na podstawie pliku CSV. Każde utworzone wyszukiwanie ma nazwę z identyfikatorem grupy wyszukiwania, a następnie do nazwy wyszukiwania jest dołączana liczba. Jeśli na przykład wprowadzisz ciąg **ContosoCase** dla identyfikatora grupy wyszukiwania, wyszukiwania będą nazywane **ContosoCase_1**, **ContosoCase_2**, **ContosoCase_3** itd. Należy pamiętać, że wpisana nazwa uwzględnia wielkość liter. Jeśli używasz identyfikatora grupy wyszukiwania w krokach 4 i 5, musisz użyć tego samego przypadku, co podczas jego tworzenia.

- **Plik CSV** — nazwa pliku CSV utworzonego w kroku 1. Pamiętaj, aby uwzględnić użycie pełnej nazwy pliku, dołącz rozszerzenie .csv pliku; na przykład  `ContosoCase.csv`.

Aby uruchomić skrypt:

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, `CreateSearches.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zostały zapisane inne pliki.

   ```Powershell
   # Get the Search Group ID and the location of the CSV input file
   $searchGroup = Read-Host 'Search Group ID'
   $csvFile = Read-Host 'Source CSV file'

   # Do a quick check to make sure our group name will not collide with other searches
   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    $searchName = $searchGroup +'_' + $searchCounter
    $search = Get-ComplianceSearch $searchName -EA SilentlyContinue
    if ($search)
    {
       Write-Error "The Search Group ID conflicts with existing searches.  Please choose a search group name and restart the script."
       return
    }
    $searchCounter++
   }

   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    # Create the query
    $query = $_.ContentMatchQuery
    if(($_.StartDate -or $_.EndDate))
    {
          # Add the appropriate date restrictions.  NOTE: Using the Date condition property here because it works across Exchange, SharePoint, and OneDrive for Business.
          # For Exchange, the Date condition property maps to the Sent and Received dates; for SharePoint and OneDrive for Business, it maps to Created and Modified dates.
          if($query)
          {
              $query += " AND"
          }
          $query += " ("
          if($_.StartDate)
          {
              $query += "Date >= " + $_.StartDate
          }
          if($_.EndDate)
          {
              if($_.StartDate)
              {
                  $query += " AND "
              }
              $query += "Date <= " + $_.EndDate
          }
          $query += ")"
    }

     # -ExchangeLocation can't be set to an empty string, set to null if there's no location.
     $exchangeLocation = $null
     if ( $_.ExchangeLocation)
     {
           $exchangeLocation = $_.ExchangeLocation
     }

    # Create and run the search
    $searchName = $searchGroup +'_' + $searchCounter
    Write-Host "Creating and running search: " $searchName -NoNewline
    $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $exchangeLocation -SharePointLocation $_.SharePointLocation -ContentMatchQuery $query

    # Start and wait for each search to complete
    Start-ComplianceSearch $search.Name
    while ((Get-ComplianceSearch $search.Name).Status -ne "Completed")
    {
       Write-Host " ." -NoNewline
       Start-Sleep -s 3
    }
    Write-Host ""

    $searchCounter++
   }
   ```

2. W Windows PowerShell przejdź do folderu, w którym zapisano skrypt w poprzednim kroku, a następnie uruchom skrypt, na przykład:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. W wierszu polecenia **Identyfikator grupy wyszukiwania** wpisz nazwę grupy wyszukiwania, a następnie naciśnij **klawisz Enter**; na przykład  `ContosoCase`. Należy pamiętać, że ta nazwa uwzględnia wielkość liter, więc w kolejnych krokach należy wpisać ją w taki sam sposób.

4. W wierszu polecenia **źródłowego pliku CSV** wpisz nazwę pliku CSV, w tym rozszerzenie pliku .csv; na przykład  `ContosoCase.csv`.

5. Naciśnij **klawisz Enter** , aby kontynuować uruchamianie skryptu.

   Skrypt wyświetla postęp tworzenia i uruchamiania wyszukiwań. Po ukończeniu skryptu wraca do wiersza polecenia.

   ![Przykładowe dane wyjściowe uruchamiania skryptu w celu utworzenia wielu wyszukiwań zgodności.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>Krok 4. Uruchamianie skryptu w celu raportowania szacunków wyszukiwania

Po utworzeniu wyszukiwań następnym krokiem jest uruchomienie skryptu, który wyświetla prosty raport o liczbie trafień wyszukiwania dla każdego wyszukiwania utworzonego w kroku 3. Raport zawiera również rozmiar wyników dla każdego wyszukiwania oraz łączną liczbę trafień i całkowity rozmiar wszystkich wyszukiwań. Po uruchomieniu skryptu raportowania zostanie wyświetlony monit o identyfikator grupy wyszukiwania i nazwę pliku CSV, jeśli chcesz zapisać raport w pliku CSV.

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, `SearchReport.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zostały zapisane inne pliki.

   ```Powershell
   $searchGroup = Read-Host 'Search Group ID'
   $outputFile = Read-Host 'Enter a file name or file path to save the report to a .csv file. Leave blank to only display the report'
   $searches = Get-ComplianceSearch | ?{$_.Name -clike $searchGroup + "_*"}
   $allSearchStats = @()
   foreach ($partialObj in $searches)
   {
      $search = Get-ComplianceSearch $partialObj.Name
      $sizeMB = [System.Math]::Round($search.Size / 1MB, 2)
      $searchStatus = $search.Status
      if($search.Errors)
      {
          $searchStatus = "Failed"
      }elseif($search.NumFailedSources -gt 0)
      {
          $searchStatus = "Failed Sources"
      }
      $searchStats = New-Object PSObject
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Name -Value $search.Name
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name ContentMatchQuery -Value $search.ContentMatchQuery
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Status -Value $searchStatus
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Items -Value $search.Items
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size" -Value $search.Size
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size(MB)" -Value $sizeMB
      $allSearchStats += $searchStats
   }
   # Calculate the totals
   $allItems = ($allSearchStats | Measure-Object Items -Sum).Sum
   # Convert the total size to MB and round to the nearst 100th
   $allSize = ($allSearchStats | Measure-Object 'Size' -Sum).Sum
   $allSizeMB = [System.Math]::Round($allSize  / 1MB, 2)
   # Get the total successful searches and total of all searches
   $allSuccessCount = ($allSearchStats |?{$_.Status -eq "Completed"}).Count
   $allCount = $allSearchStats.Count
   $allStatus = [string]$allSuccessCount + " of " + [string]$allCount
   # Totals Row
   $totalSearchStats = New-Object PSObject
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Name -Value "Total"
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Status -Value $allStatus
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Items -Value $allItems
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name "Size(MB)" -Value $allSizeMB
   $allSearchStats += $totalSearchStats
   # Just get the columns we're interested in showing
   $allSearchStatsPrime = $allSearchStats | Select-Object Name, Status, Items, "Size(MB)", ContentMatchQuery
   # Print the results to the screen
   $allSearchStatsPrime |ft -AutoSize -Wrap
   # Save the results to a CSV file
   if ($outputFile)
   {
      $allSearchStatsPrime | Export-Csv -Path $outputFile -NoTypeInformation
   }
   ```

2. W Windows PowerShell przejdź do folderu, w którym zapisano skrypt w poprzednim kroku, a następnie uruchom skrypt, na przykład:

   ```Powershell
   .\SearchReport.ps1
   ```

3. W wierszu polecenia **Identyfikator grupy wyszukiwania** wpisz nazwę grupy wyszukiwania, a następnie naciśnij **klawisz Enter**; na przykład  `ContosoCase`. Pamiętaj, że ta nazwa uwzględnia wielkość liter, więc musisz wpisać ją w taki sam sposób, jak podczas uruchamiania skryptu w kroku 3.

4. W **ścieżce Plik, aby zapisać raport w pliku CSV (pozostaw pusty, aby po prostu wyświetlić raport)** wpisz nazwę pliku o pełnej ścieżce nazwy pliku (w tym rozszerzenie pliku .csv), jeśli chcesz zapisać raport w pliku CSV. nazwa pliku CSV, w tym rozszerzenie pliku .csv. Na przykład można wpisać  `ContosoCaseReport.csv` , aby zapisać go w bieżącym katalogu lub wpisać  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` , aby zapisać go w innym folderze. Możesz również pozostawić monit pusty, aby wyświetlić raport, ale nie zapisać go w pliku.

5. Naciśnij **klawisz Enter**.

   Skrypt wyświetla postęp tworzenia i uruchamiania wyszukiwań. Po zakończeniu działania skryptu zostanie wyświetlony raport.

   ![Uruchom raport wyszukiwania, aby wyświetlić oszacowania dla grupy wyszukiwania.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> Jeśli ta sama skrzynka pocztowa lub witryna jest określona jako lokalizacja zawartości w więcej niż jednym wyszukiwaniu w grupie wyszukiwania, łączne oszacowanie wyników w raporcie (zarówno dla liczby elementów, jak i całkowitego rozmiaru) może zawierać wyniki dla tych samych elementów. Dzieje się tak, ponieważ ta sama wiadomość e-mail lub dokument będzie liczona więcej niż raz, jeśli jest zgodna z zapytaniem dla różnych wyszukiwań w grupie wyszukiwania.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>Krok 5. Uruchamianie skryptu w celu usunięcia wyszukiwań

Ponieważ możesz tworzyć wiele wyszukiwań, ten ostatni skrypt ułatwia szybkie usuwanie wyszukiwań utworzonych w kroku 3. Podobnie jak w przypadku innych skryptów, ten wyświetla również monit o identyfikator grupy wyszukiwania. Wszystkie wyszukiwania z identyfikatorem grupy wyszukiwania w nazwie wyszukiwania zostaną usunięte po uruchomieniu tego skryptu.

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, `DeleteSearches.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zostały zapisane inne pliki.

   ```Powershell
   # Delete all searches in a search group
   $searchGroup = Read-Host 'Search Group ID'
   Get-ComplianceSearch |
      ForEach-Object{
      # If the name matches the search group name pattern (case sensitive), delete the search
      if ($_.Name -cmatch $searchGroup + "_\d+")
      {
          Write-Host "Deleting search: " $_.Name
          Remove-ComplianceSearch $_.Name -Confirm:$false
      }
   }
   ```

2. W Windows PowerShell przejdź do folderu, w którym zapisano skrypt w poprzednim kroku, a następnie uruchom skrypt, na przykład:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. W wierszu polecenia **Identyfikator grupy wyszukiwania** wpisz nazwę grupy wyszukiwania dla wyszukiwań, które chcesz usunąć, a następnie naciśnij **klawisz Enter**; na przykład  `ContosoCase`. Pamiętaj, że ta nazwa uwzględnia wielkość liter, więc musisz wpisać ją w taki sam sposób, jak podczas uruchamiania skryptu w kroku 3.

   Skrypt wyświetla nazwę każdego usuniętego wyszukiwania.

   ![Uruchom skrypt, aby usunąć wyszukiwania w grupie wyszukiwania.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
