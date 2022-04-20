---
title: Tworzenie raportu zbierania elektronicznych materiałów dowodowych przy użyciu skryptu
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
description: Dowiedz się, jak wygenerować raport zawierający informacje o wszystkich blokadach skojarzonych z przypadkami zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: 98cdad3d125fbeab9afd9d7d99b572e5f0bf7386
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993211"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>Tworzenie raportu dotyczącego blokad w przypadkach zbierania elektronicznych materiałów dowodowych przy użyciu skryptu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Skrypt w tym artykule umożliwia administratorom zbierania elektronicznych materiałów dowodowych i menedżerom zbierania elektronicznych materiałów dowodowych generowanie raportu zawierającego informacje o wszystkich blokadach skojarzonych z przypadkami core i eDiscovery (Premium) w portalu zgodności usługi Microsoft Purview. Raport zawiera informacje, takie jak nazwa przypadku, z którym jest skojarzona blokada, lokalizacje zawartości, które są wstrzymane, oraz to, czy blokada jest oparta na zapytaniach. Jeśli istnieją przypadki, które nie mają żadnych blokad, skrypt utworzy dodatkowy raport z listą spraw bez blokady.

Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać szczegółowy opis informacji zawartych w raporcie.

## <a name="admin-requirements-and-script-information"></a>Wymagania administratora i informacje o skryptach

- Aby wygenerować raport dotyczący wszystkich przypadków zbierania elektronicznych materiałów dowodowych w organizacji, musisz być administratorem zbierania elektronicznych materiałów dowodowych w organizacji. Jeśli jesteś menedżerem zbierania elektronicznych materiałów dowodowych, raport będzie zawierać tylko informacje o przypadkach, do których można uzyskać dostęp. Aby uzyskać więcej informacji na temat uprawnień zbierania elektronicznych materiałów dowodowych, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Skrypt w tym artykule ma minimalną obsługę błędów. Podstawowym celem jest szybkie utworzenie raportu dotyczącego blokad skojarzonych z przypadkami zbierania elektronicznych materiałów dowodowych w organizacji.

- Przykładowe skrypty podane w tym temacie nie są obsługiwane w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowe skrypty są dostarczane jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowych skryptów i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Krok 1. Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń

Pierwszym krokiem jest nawiązanie połączenia z programem PowerShell Centrum zgodności usługi Security & dla Twojej organizacji. Aby uzyskać instrukcje krok po kroku, zobacz [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>Krok 2. Uruchamianie skryptu w celu raportowania blokad skojarzonych z przypadkami zbierania elektronicznych materiałów dowodowych

Po nawiązaniu połączenia z programem PowerShell Security & Compliance Center następnym krokiem jest utworzenie i uruchomienie skryptu zbierającego informacje o przypadkach zbierania elektronicznych materiałów dowodowych w organizacji.

1. Zapisz następujący tekst w pliku skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, na przykład CaseHoldsReport.ps1.

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
   $Path = Read-Host 'Enter a folder path to save the report to a .csv file (filename is created automatically)'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casetype,
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
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case type" -Value $casetype
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
   $allholdreport = $addRow | Select-Object "Case name","Case type","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Standard) cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Premium) cases and holds..."
   " "
   $edc =Get-ComplianceCase -CaseType Advanced -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus -casetype $cc.casetype $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
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

2. W sesji Windows PowerShell otwartej w kroku 1 przejdź do folderu, w którym zapisano skrypt.

3. Uruchom skrypt; na przykład:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Skrypt wyświetli monit o zapisanie raportu w folderze docelowym.

4. Wpisz pełną nazwę ścieżki folderu, w celu zapisania raportu, a następnie naciśnij **klawisz Enter**.

   > [!TIP]
   > Aby zapisać raport w tym samym folderze, w jakim znajduje się skrypt, wpisz kropkę (".") po wyświetleniu monitu o folder docelowy. Aby zapisać raport w podfoldecie w folderze, w którym znajduje się skrypt, wystarczy wpisać nazwę podfolderu.

   Skrypt rozpoczyna zbieranie informacji o wszystkich przypadkach zbierania elektronicznych materiałów dowodowych w organizacji. Nie uzyskiwać dostępu do pliku raportu, gdy skrypt jest uruchomiony. Po ukończeniu skryptu w sesji Windows PowerShell zostanie wyświetlony komunikat z potwierdzeniem. Po wyświetleniu tej wiadomości możesz uzyskać dostęp do raportu w folderze określonym w kroku 4. Nazwa pliku raportu to `CaseHoldsReport<DateTimeStamp>.csv`.

   Ponadto skrypt tworzy również raport z listą przypadków, które nie mają żadnych blokad. Nazwa pliku dla tego raportu to `CaseswithNoHolds<DateTimeStamp>.csv`.

   Oto przykład uruchamiania skryptu CaseHoldsReport.ps1.

   ![Dane wyjściowe po uruchomieniu skryptu CaseHoldsReport.ps1.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Więcej informacji

Sprawa zawiera raport utworzony podczas uruchamiania skryptu w tym artykule zawiera następujące informacje o każdym blokadzie. Jak wyjaśniono wcześniej, musisz być administratorem zbierania elektronicznych materiałów dowodowych, aby zwracać informacje o wszystkich blokadach w organizacji. Aby uzyskać więcej informacji na temat spraw dotyczących blokad, zobacz [Przypadki zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md).

- Nazwa blokady i nazwa sprawy zbierania elektronicznych materiałów dowodowych, z którą jest skojarzona blokada.

- Czy blokada jest skojarzona z przypadkiem Core, czy eDiscovery (Premium).

- Czy przypadek zbierania elektronicznych materiałów dowodowych jest aktywny, czy zamknięty.

- Czy blokada jest włączona, czy wyłączona.

- Członkowie sprawy zbierania elektronicznych materiałów dowodowych, z którą jest skojarzona blokada. Członkowie sprawy mogą wyświetlać przypadek lub zarządzać nimi w zależności od przypisanych im uprawnień do zbierania elektronicznych materiałów dowodowych.

- Godzina i data utworzenia sprawy.

- Jeśli sprawa zostanie zamknięta, osoba, która ją zamknęła, oraz godzina i data jej zamknięcia.

- Skrzynki pocztowe Exchange i SharePoint lokalizacje witryn, które są wstrzymane.

- Jeśli blokada jest oparta na zapytaniach, składnia zapytania.

- Godzina i data utworzenia blokady oraz osoba, która ją utworzyła.

- Godzina i data ostatniej zmiany blokady oraz osoba, która ją zmieniła.
