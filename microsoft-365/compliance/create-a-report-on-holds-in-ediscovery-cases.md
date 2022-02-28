---
title: Tworzenie raportu na temat zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 9/11/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: cca08d26-6fbf-4b2c-b102-b226e4cd7381
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak wygenerować raport zawierający informacje o wszystkich rekordach, które są skojarzone ze sprawami zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: 953b2aaa1b133d79b82f17e5f75603947cc5d6d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987783"
---
# <a name="create-a-report-on-holds-in-ediscovery-cases"></a>Tworzenie raportu na temat zbierania elektronicznych materiałów dowodowych

Skrypt w tym artykule pozwala administratorom zbierania elektronicznych materiałów dowodowych i menedżerom zbierania elektronicznych materiałów dowodowych wygenerować raport zawierający informacje o wszystkich rekordach, które są skojarzone ze sprawami zbierania elektronicznych materiałów dowodowych w centrum zgodności w programie Office 365 lub Microsoft 365. Raport zawiera informacje, takie jak nazwa sprawy, z którym jest skojarzona sprawa, lokalizacje zawartości umieszczone w hold czy też są oparte na kwerendach. Jeśli istnieją przypadki, w których nie ma żadnych blokady, skrypt utworzy dodatkowy raport z listą spraw bez blokady.

Zobacz [sekcję Więcej](#more-information) informacji, aby uzyskać szczegółowy opis informacji zawartych w raporcie.

## <a name="admin-requirements-and-script-information"></a>Wymagania administratora i informacje o skryptach

- Aby wygenerować raport na temat wszystkich spraw zbierania elektronicznych materiałów dowodowych w organizacji, musisz być administratorem zbierania elektronicznych materiałów dowodowych w organizacji. Jeśli jesteś menedżerem zbierania elektronicznych materiałów dowodowych, raport będzie zawierał tylko informacje o przypadkach, do których masz dostęp. Aby uzyskać więcej informacji o uprawnieniach zbierania elektronicznych materiałów dowodowych, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Skrypt w tym artykule ma minimalną obsługę błędów. Podstawowym celem jest szybkie utworzenie raportu o rekordach, które są skojarzone ze sprawami zbierania elektronicznych materiałów dowodowych w organizacji.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu lub usługi pomocy technicznej firmy Microsoft. Przykładowe skrypty są dostarczane W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowych skryptów i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Krok 1. Połączenie do centrum zabezpieczeń & w programie PowerShell

Pierwszym krokiem jest połączenie się z programem PowerShell & zabezpieczeń w organizacji. Aby uzyskać instrukcje krok po kroku, zobacz [Połączenie do programu PowerShell & centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>Krok 2. Uruchamianie skryptu w celu zgłoszenia raportów o zarchiwniach skojarzonych ze sprawami zbierania elektronicznych materiałów dowodowych

Po na połączeniu z programem PowerShell w Centrum zabezpieczeń & zgodności następnym krokiem jest utworzenie i uruchomienie skryptu zbieracego informacje o sprawach zbierania elektronicznych materiałów dowodowych w organizacji.

1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, na przykład CaseHoldsReport.ps1.

   ```powershell
   #script begin
   " "
   write-host "***********************************************"
   write-host "   Security & Compliance Center   " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "        eDiscovery cases - Holds report         " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "***********************************************"
   " "
   #prompt users to specify a path to store the output files
   $time=get-date
   $Path = Read-Host 'Enter a file path to save the report to a .csv file'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casestatus,
   [datetime]$casecreatedtime,
   [string]$casemembers,
   [datetime]$caseClosedDateTime,
   [string]$caseclosedby,
   [string]$holdname,
   [String]$Holdenabled,
   [string]$holdcreatedby,
   [string]$holdlastmodifiedby,
   [string]$ExchangeLocation,
   [string]$sharePointlocation,
   [string]$ContentMatchQuery,
   [datetime]$holdcreatedtime,
   [datetime]$holdchangedtime
   )
   $addRow = New-Object PSObject
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case name" -Value $casename
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case status" -Value $casestatus
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case members" -Value $casemembers
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case created time" -Value $casecreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed time" -Value $caseClosedDateTime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed by" -Value $caseclosedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold name" -Value $holdname
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold enabled" -Value $Holdenabled
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created by" -Value $holdcreatedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold last changed by" -Value $holdlastmodifiedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Exchange locations" -Value  $ExchangeLocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "SharePoint locations" -Value $sharePointlocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold query" -Value $ContentMatchQuery
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created time (UTC)" -Value $holdcreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold changed time (UTC)" -Value $holdchangedtime
   $allholdreport = $addRow | Select-Object "Case name","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }

   " "
   Write-host "Script complete! Report files saved to this folder: '$Path'"
   " "
   #script end
   ```

2. W Windows PowerShell otwartej w kroku 1 przejdź do folderu, w którym został zapisany skrypt.

3. Uruchom skrypt. na przykład:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Skrypt wyświetli monit o zapisanie raportu w folderze docelowym.

4. Wpisz pełną nazwę folderu, w którym chcesz zapisać raport, a następnie naciśnij klawisz **Enter**.

   > [!TIP]
   > Aby zapisać raport w tym samym folderze, w którym znajduje się skrypt, po wyświetleniu monitu o folder docelowy wpisz okres ("."). Aby zapisać raport w podfolderze w folderze, w którym znajduje się skrypt, wystarczy wpisać jego nazwę.

   Skrypt zacznie zbierać informacje o wszystkich przypadkach zbierania elektronicznych materiałów dowodowych w organizacji. Nie uzyskaj dostępu do pliku raportu, gdy skrypt jest uruchomiony. Po zakończeniu skryptu w sesji wiadomości jest wyświetlany Windows PowerShell potwierdzenia. Po wyświetlaniu tego komunikatu możesz uzyskać dostęp do raportu w folderze określonym w kroku 4. Nazwa pliku raportu to `CaseHoldsReport<DateTimeStamp>.csv`.

   Ponadto skrypt tworzy również raport z listą spraw, które nie mają żadnych blokady. Nazwa pliku tego raportu to `CaseswithNoHolds<DateTimeStamp>.csv`.

   Oto przykład uruchamiania skryptu CaseHoldsReport.ps1 skryptu.

   ![Wynik po uruchomieniu skryptu CaseHoldsReport.ps1 skryptu.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Więcej informacji

Raport o przypadku utworzony po uruchomieniu skryptu w tym artykule zawiera następujące informacje o poszczególnych blokadych. Jak już wyjaśniono, musisz być administratorem zbierania elektronicznych materiałów dowodowych, aby zwracać informacje o wszystkich blokadych w organizacji. Aby uzyskać więcej informacji na temat zbierania spraw, zobacz [Sprawy zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md).

- Nazwa przechowywania i nazwa sprawy zbierania elektronicznych materiałów dowodowych, z tą sprawą jest skojarzona.

- Czy sprawa zbierania elektronicznych materiałów dowodowych jest aktywna, czy zamknięta.

- Określa, czy to hold jest włączone, czy wyłączone.

- Członkowie sprawy zbierania elektronicznych materiałów dowodowych, z tą sprawą jest skojarzona ta sprawa. Członkowie sprawy mogą wyświetlać i zarządzać sprawą, zależnie od przypisanych im uprawnień zbierania elektronicznych materiałów dowodowych.

- Godzina i data utworzenia sprawy.

- W przypadku zamknięcia sprawy osoba, która ją zamknęła, oraz godzina i data zamknięcia.

- Skrzynki Exchange pocztowe i SharePoint witryn, które znajdują się w wstrzymaniu.

- Jeśli hold jest oparty na kwerendzie, składnia zapytania.

- Godzina i data utworzenia hold'a oraz osoba, która go utworzyła.

- Godzina i data ostatniej zmiany trzymania oraz osoba, która go zmieniła.