---
title: Sklonowanie wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 4/26/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 7b40eeaa-544c-4534-b89b-9f79998e374c
ms.custom:
- seo-marvel-apr2020
description: Użyj skryptu programu PowerShell w tym artykule, aby szybko sklonować istniejące wyszukiwanie zawartości w Centrum zgodności w programie Office 365 lub Microsoft 365.
ms.openlocfilehash: 763bd6ac49841e5b55bbbc187631ef74426d9d0a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983175"
---
# <a name="clone-a-content-search"></a>Sklonowanie wyszukiwania zawartości

Tworzenie wyszukiwania zawartości w centrum zgodności w programie Office 365 lub Microsoft 365, które przeszukuje wiele skrzynek pocztowych lub witryn SharePoint i OneDrive dla Firm może trochę potrwać. Określenie witryn do wyszukiwania może być również podatne na błędy w przypadku błędnego wpisywania adresu URL. Aby uniknąć tych problemów, możesz użyć skryptu Windows PowerShell w tym artykule, aby szybko sklonować istniejące wyszukiwanie zawartości. W przypadku sklonowania wyszukiwania jest tworzone nowe wyszukiwanie (o innej nazwie), które zawiera te same właściwości (takie jak lokalizacje zawartości i zapytanie wyszukiwania) co oryginalne wyszukiwanie. Następnie możesz edytować nowe wyszukiwanie, zmieniając zapytanie słów kluczowych lub zakres dat i uruchamiać je.
  
Dlaczego warto sklonować wyszukiwania zawartości?
  
- Aby porównać wyniki różnych zapytań wyszukiwania słów kluczowych, działają w tych samych lokalizacjach zawartości.
    
- Aby nie trzeba było ponownie tworzyć wielu lokalizacji zawartości podczas tworzenia nowego wyszukiwania.
    
- Aby zmniejszyć rozmiar wyników wyszukiwania. Jeśli na przykład wyszukiwanie zwraca zbyt wiele wyników do wyeksportowania, można sklonować wyszukiwanie, a następnie dodać warunek wyszukiwania oparty na zakresie dat w celu zmniejszenia liczby wyników wyszukiwania.
  
## <a name="script-information"></a>Informacje o skrypcie

- Aby uruchomić skrypt opisany w tym temacie, musisz być członkiem grupy ról Menedżera zbierania elektronicznych materiałów dowodowych w grupie Centrum zgodności platformy Microsoft 365.
    
- Skrypt zawiera minimalną obsługę błędów. Głównym celem skryptu jest szybkie sklonowanie wyszukiwania zawartości.
    
- Skrypt utworzy nowe wyszukiwanie zawartości, ale nie rozpocznie się.
    
- Ten skrypt uwzględnia, czy przeszukiwanie zawartości jest klonowanie skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych. Jeśli wyszukiwanie jest skojarzone ze sprawą, nowe wyszukiwanie również zostanie skojarzone z tą samą sprawą. Jeśli istniejące wyszukiwanie nie jest skojarzone ze sprawą, nowe wyszukiwanie zostanie wyświetlone na stronie Przeszukiwanie zawartości w Centrum  zgodności. 
    
- Przykładowy skrypt podany w tym temacie nie jest obsługiwany w żadnym standardowym programie lub usłudze pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.
  
## <a name="step-1-run-the-script-to-clone-a-search"></a>Krok 1. Uruchomienie skryptu w celu sklonowania wyszukiwania

Skrypt w tym kroku utworzy nowe wyszukiwanie zawartości przez klonowanie istniejącej. Po uruchomieniu tego skryptu zostanie wyświetlony monit o następujące informacje:
  
- **Poświadczenia użytkownika —** skrypt użyje Twoich poświadczeń do nawiązania połączenia z programem PowerShell w & Centrum zgodności. Jak wspomniano wcześniej, aby uruchomić skrypt, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w Centrum & zabezpieczeń. 
    
- **Nazwa istniejącego wyszukiwania —** jest to wyszukiwanie zawartości, które chcesz sklonować. 
    
-  Nazwa nowego wyszukiwania, które zostanie utworzone — jeśli pozostawisz tę wartość pustą, skrypt utworzy nazwę nowego wyszukiwania na podstawie nazwy tego wyszukiwania, które zostanie klonowanie. 
    
Aby sklonować wyszukiwanie:
  
1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `CloneSearch.ps1`na przykład .
    
  ```powershell
  # This PowerShell script clones an existing content search in the Security &amp; Compliance Center.
  # Get login credentials from the user
  if(!$UserCredential)
  {
      $UserCredential = Get-Credential
      $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
      if (!$Session)
      {
          Write-Error "Couldn't create a remote PowerShell session."
          return
      }
      Import-PSSession $Session -AllowClobber -DisableNameChecking
      $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Security & Compliance Center)"
  }
  # Ask for the name of the search you want to clone
  $searchName = Read-Host 'Enter the name of the search that you want to clone'
  # Ask for the name of the new search
  $newSearchName = Read-Host 'Enter a name for the new search [leave blank to automatically generate a name]'
  $originalSearch = Get-ComplianceSearch $searchName -EA SilentlyContinue
  # Make sure we have a valid search before continuing
  if(!$originalSearch)
  {
      Write-Error "Couldn't find search: $searchName"
      return
  }
  $searchNameCounter = 1
  # Find a suitable name for the new search
  while(!$newSearchName)
  {
      $newSearchName = $originalSearch.Name + "_" + $searchNameCounter
      $tempSearch = Get-ComplianceSearch $newSearchName -EA SilentlyContinue
      if ($tempSearch)
      {
          $newSearchName = $null
          $searchNameCounter++
      }
  }
  $caseName
  # Determine if the search is part of a case; if so get the case name
  if ($originalSearch.CaseId)
  {
      $searchCase = Get-ComplianceCase $originalSearch.CaseId
      $caseName = $searchCase.Name
  }
  # Need to cast this value as a Boolean the old fashion way
  $allowNotFoundExchangeLocationsEnabled = $false
  if ($originalSearch.AllowNotFoundExchangeLocationsEnabled)
  {
      $allowNotFoundExchangeLocationsEnabled = $true
  }
  $newSearch = New-ComplianceSearch -Name $newSearchName -AllowNotFoundExchangeLocationsEnabled $allowNotFoundExchangeLocationsEnabled -Case $caseName -ContentMatchQuery $originalSearch.ContentMatchQuery -Description $originalSearch.Description -ExchangeLocation $originalSearch.ExchangeLocation -ExchangeLocationExclusion $originalSearch.ExchangeLocationExclusion -Language $originalSearch.Language -SharePointLocation $originalSearch.SharePointLocation -SharePointLocationExclusion $originalSearch.SharePointLocationExclusion -PublicFolderLocation $originalSearch.PublicFolderLocation
  if ($newSearch)
  {
      Write-Host $newSearch.Name "was successfully created" -ForegroundColor Yellow
  }
  ```

2. Otwórz Windows PowerShell i przejdź do folderu, w którym został zapisany skrypt.
    
3. Uruchom skrypt. na przykład:
    
    ```powershell
    .\CloneSearch.ps1
    ```

4. Po wyświetleniu monitu o podanie poświadczeń wprowadź swój adres e-mail i hasło, a następnie kliknij przycisk **OK**.
    
5. Po wyświetleniu monitu przez skrypt wprowadź następujące informacje. Wpisz poszczególne informacje, a następnie naciśnij klawisz **Enter**.
    
    - Nazwa istniejącego wyszukiwania.
    
    - Nazwa nowego wyszukiwania.
    
    Skrypt utworzy nowe wyszukiwanie zawartości, ale nie rozpocznie się. Umożliwia to edytowanie i uruchamianie wyszukiwania w następnym kroku. Właściwości nowego wyszukiwania można wyświetlić, uruchamiając polecenie cmdlet **Get-ComplianceSearch** lub przechodząc do strony Przeszukiwanie zawartości lub  **zbierania** elektronicznych materiałów dowodowych w centrum zgodności w zależności od tego, czy nowe wyszukiwanie jest skojarzone ze sprawą. 
  
## <a name="step-2-edit-and-run-the-cloned-search-in-the-compliance-center"></a>Krok 2. Edytowanie i uruchamianie sklonowanego wyszukiwania w centrum zgodności

Po uruchomieniu skryptu w celu sklonowania istniejącego przeszukiwania zawartości następnym krokiem jest przejść do Centrum zgodności w celu edytowania i uruchomienia nowego wyszukiwania. Jak wspomniano wcześniej, możesz edytować wyszukiwanie, zmieniając zapytanie wyszukiwania słów kluczowych i dodając lub usuwając warunki wyszukiwania. Więcej informacji można znaleźć w następujących artykułach:
  
- [Wyszukiwanie zawartości w programie Office 365](content-search.md)
    
- [Zapytania słów kluczowych i warunki wyszukiwania dla przeszukiwania zawartości](keyword-queries-and-search-conditions.md)
    
- [Sprawy zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md)