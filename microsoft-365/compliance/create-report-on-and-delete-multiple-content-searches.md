---
title: Tworzenie, tworzenie raportów i usuwanie wielu przeszukiwań zawartości
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
- SPO160
- MOE150
- MET150
ms.assetid: 1d463dda-a3b5-4675-95d4-83db19c9c4a3
description: Dowiedz się, jak zautomatyzować zadania związane z wyszukiwaniem zawartości, takie jak tworzenie wyszukiwań i uruchamianie raportów za pomocą programu PowerShell & Centrum zabezpieczeń i zgodności.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 602997114c46a68be13182a504d0b123e98d2be2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985470"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>Tworzenie, tworzenie raportów i usuwanie wielu przeszukiwań zawartości

 Szybkie tworzenie i zgłaszanie wyszukiwań odnajdowania często jest ważnym krokiem podczas zbierania elektronicznych materiałów dowodowych i badań, gdy próbujesz uzyskać informacje na temat danych źródłowych oraz bogatych i wysokiej jakości wyszukiwań. Aby to ułatwić, program PowerShell & zabezpieczeń i zgodności oferuje zestaw poleceń cmdlet do automatyzowania czasochłonnych zadań przeszukiwania zawartości. Te skrypty zapewniają szybki i łatwy sposób tworzenia wielu wyszukiwań, a następnie uruchamiania raportów dotyczących szacowanych wyników wyszukiwania, które mogą pomóc w ustaleniu ilości danych, o których mowa. Możesz również użyć skryptów, aby utworzyć różne wersje wyszukiwań w celu porównania wyników, które daje każda z nich. Te skrypty mogą ułatwić szybkie i wydajne identyfikowanie i poprawianie danych.

## <a name="before-you-create-a-content-search"></a>Przed utworzeniem przeszukiwania zawartości

- Aby uruchamiać skrypty opisane w tym temacie, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w grupie Centrum zgodności platformy Microsoft 365.

- Aby zebrać listę adresów URL witryn usługi OneDrive dla Firm w organizacji, które można dodać do pliku CSV w kroku 1, zobacz Tworzenie listy wszystkich OneDrive lokalizacji w [organizacji](/onedrive/list-onedrive-urls).

- Pamiętaj o zapisaniu wszystkich plików tworzyć w tym temacie w tym samym folderze. Ułatwi to uruchamianie skryptów.

- Skrypty zawierają minimalną obsługę błędów. Ich głównym celem jest szybkie tworzenie, tworzenie raportów i usuwanie wielu przeszukiwań zawartości.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu lub usługi pomocy technicznej firmy Microsoft. Przykładowe skrypty są dostarczane W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowych skryptów i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>Krok 1. Tworzenie pliku CSV zawierającego informacje o wyszukiwaniach, które mają zostać uruchomione

Plik wartości rozdzielanych przecinkami (CSV) dzielony w tym kroku zawiera wiersz dla każdego użytkownika, którego chcesz wyszukać. Możesz przeszukać skrzynkę pocztową Exchange Online (która zawiera archiwalne skrzynki pocztowe, jeśli jest włączona) i witrynę OneDrive dla Firm pocztowej. Możesz również przeszukać tylko skrzynkę pocztową lub witrynę OneDrive dla Firm. Możesz również przeszukać dowolną witrynę w organizacji usługi SharePoint online. Skrypt uruchomiony w kroku 3 spowoduje utworzenie oddzielnego wyszukiwania dla każdego wiersza w pliku CSV.

1. Skopiuj poniższy tekst i wklej go do pliku .txt notatnika. Zapisz ten plik w folderze na komputerze lokalnym. Zapiszesz również pozostałe skrypty w tym folderze.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   Pierwszy wiersz w pliku, czyli wiersz nagłówka, zawiera parametry używane przez polecenie cmdlet **New-ComplianceSearch** (w skrypcie w kroku 3) do tworzenia nowych wyszukiwań zawartości. Poszczególne nazwy parametrów są rozdzielone przecinkami. Upewnij się, że w wierszu nagłówka nie ma spacji. Każdy wiersz poniżej wiersza nagłówka reprezentuje wartości parametrów dla każdego wyszukiwania. Pamiętaj, aby zamienić dane zastępcze w pliku CSV na rzeczywiste dane.

2. Otwórz .txt pliku w programie Excel, a następnie użyj informacji z poniższej tabeli, aby edytować plik z informacjami dla każdego wyszukiwania.

   ****

   |Parametr|Opis|
   |---|---|
   |`ExchangeLocation`|Adres SMTP skrzynki pocztowej użytkownika.|
   |`SharePointLocation`|Adres URL witryny OneDrive dla Firm lub adres URL dowolnej witryny w organizacji. Aby uzyskać adres URL OneDrive dla Firm witryn, użyj tego formatu: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. Na przykład . `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`|
   |`ContentMatchQuery`|Zapytanie wyszukiwania dla tego wyszukiwania. Aby uzyskać więcej informacji na temat tworzenia zapytania wyszukiwania, zobacz Zapytania słów kluczowych [i warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md).|
   |`StartDate`|W przypadku wiadomości e-mail jest to data, kiedy wiadomość została odebrana przez adresata lub wysłana przez nadawcę. W przypadku dokumentów SharePoint lub OneDrive dla Firm internetowych data ostatniej modyfikacji dokumentu lub późniejsza.|
   |`EndDate`|W przypadku wiadomości e-mail jest to data, do dnia lub przed wysłaniem wiadomości przez użytkownika. W przypadku dokumentów SharePoint lub OneDrive dla Firm internetowych data ostatniej modyfikacji dokumentu lub przed nim.|
   |

3. Zapisz Excel jako plik CSV w folderze na komputerze lokalnym. Skrypt, który utworzysz w kroku 3, użyje informacji z tego pliku CSV do utworzenia wyszukiwań.

## <a name="step-2-connect-to-security--compliance-center-powershell"></a>Krok 2. Połączenie do programu PowerShell w & zabezpieczeń i zgodności

Następnym krokiem jest połączenie się z programem PowerShell & zabezpieczeń w organizacji. Aby uzyskać instrukcje krok po kroku, zobacz [Połączenie do programu PowerShell & centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>Krok 3. Uruchamianie skryptu w celu utworzenia i rozpoczęcia wyszukiwań

Skrypt w tym kroku utworzy osobne wyszukiwanie zawartości dla każdego wiersza w pliku CSV utworzonym w kroku 1. Po uruchomieniu tego skryptu zostanie wyświetlony monit o wartości:

- **Identyfikator grupy wyszukiwania** — ta nazwa zapewnia łatwy sposób organizowania wyszukiwań utworzonych na podstawie pliku CSV. Każde utworzone wyszukiwanie ma nazwę z identyfikatorem grupy wyszukiwania, a następnie do nazwy wyszukiwania jest dołączany numer. Jeśli na przykład dla identyfikatora grupy wyszukiwania zostanie w wprowadzeniu nazwy **ContosoCase** , wyszukiwania będą nosiły nazwy **ContosoCase_1**, **ContosoCase_2**, **ContosoCase_3** i tak dalej. Pamiętaj, że w wpisanych nazwach jest wana wielkość liter. Jeśli używasz identyfikatora grupy wyszukiwania w krokach 4 i 5, musisz użyć tej samej sprawy, co podczas tworzenia.

- **Plik CSV** — nazwa pliku CSV utworzonego w kroku 1. Pamiętaj, aby dołączyć pełną nazwę pliku, dołączyć rozszerzenie .csv pliku; na przykład  `ContosoCase.csv`.

Aby uruchomić skrypt:

1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `CreateSearches.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zapisano inne pliki.

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

2. W Windows PowerShell przejdź do folderu, w którym został zapisany skrypt w poprzednim kroku, a następnie uruchom skrypt, na przykład:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. W **wierszu monitu Identyfikator** grupy wyszukiwania wpisz nazwę grupy wyszukiwania, a następnie naciśnij klawisz **Enter**. na przykład  `ContosoCase`. Pamiętaj, że w tej nazwie jest wróżniana wielkość liter, więc w kolejnych krokach będzie konieczne wpisanie jej w taki sam sposób.

4. W **wierszu monitu** o źródłowy plik CSV wpisz nazwę pliku CSV wraz z rozszerzeniem pliku .csv pliku. na przykład  `ContosoCase.csv`.

5. Naciśnij **klawisz Enter** , aby kontynuować uruchamianie skryptu.

   Skrypt wyświetla postęp tworzenia i uruchamiania wyszukiwań. Po ukończeniu skryptu powróci on do wiersza polecenia.

   ![Przykładowe dane wyjściowe z uruchamiania skryptu w celu utworzenia wielu wyszukiwań zgodności.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>Krok 4. Uruchamianie skryptu w celu zgłoszenia oszacowania wyszukiwania

Kolejnym krokiem po utworzeniu wyszukiwań jest uruchomienie skryptu wyświetlacego prosty raport o liczbie trafień dla każdego wyszukiwania utworzonego w kroku 3. Raport zawiera również rozmiar wyników każdego wyszukiwania oraz łączną liczbę trafień i całkowity rozmiar wszystkich wyszukiwań. Po uruchomieniu skryptu raportowania zostanie wyświetlony monit o identyfikator grupy wyszukiwania i nazwę pliku CSV, jeśli chcesz zapisać raport w pliku CSV.

1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `SearchReport.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zapisano inne pliki.

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

2. W Windows PowerShell przejdź do folderu, w którym został zapisany skrypt w poprzednim kroku, a następnie uruchom skrypt, na przykład:

   ```Powershell
   .\SearchReport.ps1
   ```

3. W **wierszu monitu Identyfikator** grupy wyszukiwania wpisz nazwę grupy wyszukiwania, a następnie naciśnij klawisz **Enter**. na przykład  `ContosoCase`. Pamiętaj, że w tej nazwie jest wróżniana wielkość liter, więc będzie trzeba ją wpisać tak samo, jak w przypadku uruchamiania skryptu w kroku 3.

4. W wierszu Ścieżka pliku, aby zapisać raport w pliku **CSV (** pozostaw puste miejsce, aby tylko wyświetlić raport) wpisz nazwę pliku pełnej ścieżki nazwy pliku (wraz z rozszerzeniem pliku .csv), jeśli chcesz zapisać raport w pliku CSV. nazwę pliku CSV wraz z .csv pliku. Możesz na przykład wpisać tekst,  `ContosoCaseReport.csv` aby zapisać go w bieżącym katalogu  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` lub zapisać go w innym folderze. Możesz również pozostawić monit pusty, aby wyświetlić raport, ale nie zapisać go w pliku.

5. Naciśnij **klawisz Enter**.

   Skrypt wyświetla postęp tworzenia i uruchamiania wyszukiwań. Po ukończeniu skryptu zostanie wyświetlony raport.

   ![Uruchom raport wyszukiwania, aby wyświetlić oszacowania dla grupy wyszukiwania.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> Jeśli ta sama skrzynka pocztowa lub witryna jest określona jako lokalizacja zawartości w więcej niż jednym wyszukiwaniu w grupie wyszukiwania, szacowana suma wyników w raporcie (zarówno dla liczby elementów, jak i całkowitego rozmiaru) może obejmować wyniki dla tych samych elementów. Jest tak dlatego, że ta sama wiadomość e-mail lub dokument będzie liczony więcej niż raz, jeśli będzie odpowiadać zapytaniu dotyczącem różnych wyszukiwań w grupie wyszukiwania.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>Krok 5. Uruchamianie skryptu w celu usunięcia wyszukiwań

Ponieważ możesz tworzyć wiele wyszukiwań, ten ostatni skrypt po prostu ułatwia szybkie usuwanie wyszukiwań utworzonych w kroku 3. Podobnie jak w przypadku innych skryptów, ten również wyświetla monit o identyfikator grupy wyszukiwania. Wszystkie wyszukiwania z identyfikatorem grupy wyszukiwania w nazwie wyszukiwania zostaną usunięte po uruchomieniu tego skryptu.

1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `DeleteSearches.ps1`na przykład . Zapisz plik w tym samym folderze, w którym zapisano inne pliki.

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

2. W Windows PowerShell przejdź do folderu, w którym został zapisany skrypt w poprzednim kroku, a następnie uruchom skrypt, na przykład:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. W **wierszu monitu** Identyfikator grupy wyszukiwania wpisz nazwę grupy wyszukiwania dla wyszukiwań, które chcesz usunąć, a następnie naciśnij klawisz **Enter**. na przykład  `ContosoCase`. Pamiętaj, że w tej nazwie jest wróżniana wielkość liter, więc będzie trzeba ją wpisać tak samo, jak w przypadku uruchamiania skryptu w kroku 3.

   Skrypt wyświetli nazwę każdego usuniętego wyszukiwania.

   ![Uruchom skrypt, aby usunąć wyszukiwania z grupy wyszukiwania.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
