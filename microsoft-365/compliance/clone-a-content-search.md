---
title: Klonowanie wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Użyj skryptu programu PowerShell w tym artykule, aby szybko sklonować istniejące wyszukiwanie zawartości w portalu zgodności usługi Microsoft Purview w Microsoft 365.
ms.openlocfilehash: f5ec0433e445256865033b71082c92889972f827
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017449"
---
# <a name="clone-a-content-search"></a>Klonowanie wyszukiwania zawartości

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Tworzenie wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview w Microsoft 365, które wyszukuje wiele skrzynek pocztowych lub SharePoint i witryn OneDrive dla Firm, może trochę potrwać. Określanie witryn do wyszukiwania może być również podatne na błędy, jeśli błędnie określisz adres URL. Aby uniknąć tych problemów, możesz użyć skryptu Windows PowerShell w tym artykule, aby szybko sklonować istniejące wyszukiwanie zawartości. Podczas klonowania wyszukiwania jest tworzone nowe wyszukiwanie (o innej nazwie), które zawiera te same właściwości (takie jak lokalizacje zawartości i zapytanie wyszukiwania) co oryginalne wyszukiwanie. Następnie możesz edytować nowe wyszukiwanie, zmieniając zapytanie słowa kluczowego lub zakres dat i uruchamiając je.

Dlaczego warto klonować wyszukiwania zawartości?

- Aby porównać wyniki różnych zapytań wyszukiwania słów kluczowych uruchamianych w tych samych lokalizacjach zawartości.

- Aby zapisać konieczność ponownego wstawienia dużej liczby lokalizacji zawartości podczas tworzenia nowego wyszukiwania.

- Aby zmniejszyć rozmiar wyników wyszukiwania. Jeśli na przykład masz wyszukiwanie zwracające zbyt wiele wyników do wyeksportowania, możesz sklonować wyszukiwanie, a następnie dodać warunek wyszukiwania na podstawie zakresu dat, aby zmniejszyć liczbę wyników wyszukiwania.

## <a name="script-information"></a>Informacje o skryptze

- Musisz zainstalować moduł Exchange Online V2. Aby uzyskać instrukcje, zobacz [Instalowanie i obsługa modułu EXO w wersji 2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

- Aby uruchomić skrypt opisany w tym temacie, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview.

- Skrypt zawiera minimalną obsługę błędów. Podstawowym celem skryptu jest szybkie sklonowanie wyszukiwania zawartości.

- Skrypt tworzy nowe wyszukiwanie zawartości, ale nie uruchamia go.

- Ten skrypt uwzględnia, czy klonowanie wyszukiwania zawartości jest skojarzone z przypadkiem zbierania elektronicznych materiałów dowodowych. Jeśli wyszukiwanie jest skojarzone ze sprawą, nowe wyszukiwanie będzie również skojarzone z tym samym przypadkiem. Jeśli istniejące wyszukiwanie nie jest skojarzone ze sprawą, nowe wyszukiwanie zostanie wyświetlone na stronie **wyszukiwania zawartości** w portalu zgodności usługi Microsoft Purview.

- Przykładowy skrypt podany w tym temacie nie jest obsługiwany w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowy skrypt jest dostarczany jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowego skryptu i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-run-the-script-to-clone-a-search"></a>Krok 1. Uruchamianie skryptu w celu sklonowania wyszukiwania

Skrypt w tym kroku utworzy nowe wyszukiwanie zawartości przez sklonowanie istniejącego. Po uruchomieniu tego skryptu zostanie wyświetlony monit o podanie następujących informacji:

- **Poświadczenia użytkownika** — skrypt będzie używać poświadczeń w celu nawiązania połączenia z programem PowerShell security & Compliance. Jak wspomniano wcześniej, musisz być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview, aby uruchomić skrypt.

- **Nazwa istniejącego wyszukiwania** — jest to wyszukiwanie zawartości, które chcesz sklonować.

- **Nazwa nowego wyszukiwania, które zostanie utworzone** — jeśli pozostawisz tę wartość pustą, skrypt utworzy nazwę nowego wyszukiwania opartą na nazwie klonowanego wyszukiwania.

Aby sklonować wyszukiwanie:

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, `CloneSearch.ps1`na przykład .

   ```powershell
   # This PowerShell script clones an existing content search in Microsoft Purview compliance.

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

2. [Połączenie do programu PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell). W tym samym oknie programu PowerShell przejdź do folderu, w którym zapisano skrypt.

3. Uruchom skrypt; na przykład:

     ```powershell
     .\CloneSearch.ps1
     ```

4. Wprowadź następujące informacje po wyświetleniu monitu przez skrypt. Wpisz każdą informację, a następnie naciśnij **klawisz Enter**.

     - Nazwa istniejącego wyszukiwania.
     - Nazwa nowego wyszukiwania.

     Skrypt tworzy nowe wyszukiwanie zawartości, ale nie uruchamia go. Dzięki temu możesz edytować i uruchomić wyszukiwanie w następnym kroku. Właściwości nowego wyszukiwania można wyświetlić, uruchamiając polecenie cmdlet **Get-ComplianceSearch** lub przechodząc do strony **Wyszukiwanie zawartości** lub **eDiscovery** w portalu zgodności usługi Microsoft Purview, w zależności od tego, czy nowe wyszukiwanie jest skojarzone ze sprawą.

## <a name="step-2-edit-and-run-the-cloned-search-in-the-microsoft-purview-compliance-portal"></a>Krok 2. Edytowanie i uruchamianie sklonowanego wyszukiwania w portalu zgodności usługi Microsoft Purview

Po uruchomieniu skryptu w celu sklonowania istniejącego wyszukiwania zawartości następnym krokiem jest przejście do portalu zgodności usługi Microsoft Purview w celu edytowania i uruchomienia nowego wyszukiwania. Jak wspomniano wcześniej, możesz edytować wyszukiwanie, zmieniając zapytanie wyszukiwania słów kluczowych i dodając lub usuwając warunki wyszukiwania. Więcej informacji można znaleźć w następujących artykułach:

- [Wyszukiwanie zawartości w Office 365](content-search.md)

- [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md)

- [Przypadki zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md)
