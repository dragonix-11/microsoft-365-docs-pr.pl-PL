---
title: Przeszukiwanie dziennika inspekcji za pomocą skryptu programu PowerShell
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Użyj skryptu programu PowerShell, który uruchamia Search-UnifiedAuditLog cmdlet w Exchange Online, aby przeszukać dziennik inspekcji. Ten skrypt jest zoptymalizowany pod kątem zwracania dużego zestawu rekordów inspekcji za każdym razem, gdy jest uruchamiany. Skrypt eksportuje te rekordy do pliku CSV, który można wyświetlać i przekształcać przy użyciu dodatku Power Query w programie Excel.
ms.openlocfilehash: 60f78f5a5eebeaa90f01b4b251d917f178c06ae9
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012524"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Przeszukiwanie dziennika inspekcji za pomocą skryptu programu PowerShell

Zabezpieczenia, zgodność z przepisami i inspekcja stały się dla administratorów it najważniejsze w dzisiejszych czasach. Microsoft 365 kilka wbudowanych funkcji, które ułatwiają organizacjom zarządzanie zabezpieczeniami, zgodnością i inspekcją. W szczególności ujednolicone rejestrowanie inspekcji może ułatwić badanie zdarzeń dotyczących zabezpieczeń i problemów ze zgodnością. Dzienniki inspekcji można pobierać przy użyciu następujących metod:

- [Interfejs API Office 365 zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference)

- Narzędzie [do przeszukiwania dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md) w Centrum zgodności platformy Microsoft 365

- Polecenie [cmdlet Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online PowerShell

Jeśli chcesz regularnie pobierać dzienniki inspekcji, rozważ rozwiązanie, które korzysta z interfejsu API działań zarządzania usługi Office 365, ponieważ pozwala dużym organizacjom na skalowanie i wydajność w celu ciągłego pobierania milionów rekordów inspekcji. Korzystanie z narzędzia do przeszukiwania dziennika inspekcji w programie Centrum zgodności platformy Microsoft 365 to dobry sposób na szybkie znajdowanie rekordów inspekcji dla określonych operacji wykonywanych w krótszym przedziale czasowym. Używanie dłuższych zakresów czasu w narzędziu do przeszukiwania dziennika inspekcji, szczególnie w dużych organizacjach, może spowodować zwrócenie zbyt wielu rekordów, aby można było łatwo zarządzać nimi i je eksportować.

Gdy trzeba ręcznie pobrać dane inspekcji dla określonego badania lub zdarzenia, zwłaszcza w przypadku dłuższych zakresów dat w większych organizacjach, najlepszą opcją może być polecenie cmdlet **Search-UnifiedAuditLog** . Ten artykuł zawiera skrypt programu PowerShell, który używa polecenia cmdlet, które umożliwia pobieranie 50 000 rekordów inspekcji (za każdym razem, gdy uruchamiasz polecenie cmdlet), a następnie eksportowanie ich do pliku CSV, który można sformatować przy użyciu dodatku Power Query w programie Excel w celu pomocy podczas przeglądania. Użycie skryptu w tym artykule minimalizuje również szanse na przeoczycie w usłudze dużych przeszukiwań dziennika inspekcji.

## <a name="before-you-run-the-script"></a>Przed uruchomieniem skryptu

- Aby pomyślnie zwracać rekordy inspekcji, rejestrowanie inspekcji musi być włączone dla organizacji. Rejestrowanie inspekcji jest domyślnie włączone dla Microsoft 365 i Office 365 przedsiębiorstw. Aby sprawdzić, czy w organizacji włączona jest przeszukiwanie dziennika inspekcji, w programie Exchange Online PowerShell można uruchomić następujące polecenie:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Wartość właściwości `True` **UnifiedAuditLogIngestionEnabled** wskazuje, że jest włączone przeszukiwanie dziennika inspekcji.

- Aby pomyślnie uruchomić skrypt, View-Only rolę Dzienniki inspekcji lub Dzienniki inspekcji Exchange Online. Domyślnie te role są przypisane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie Uprawnienia Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">administracyjnego</a>. Aby uzyskać więcej informacji, zobacz sekcję "Wymagania dotyczące przeszukiwania dziennika inspekcji" w sekcji Przeszukiwanie dziennika inspekcji [w centrum zgodności](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- Ukończenie skryptu może zająć dużo czasu. Czas wykonywania zależy od zakresu dat i rozmiaru interwału, dla których skrypt konfiguruje pobieranie rekordów inspekcji. Większe zakresy dat i mniejsze interwały będą skutkować długim czasem działania. Aby uzyskać więcej informacji na temat zakresu dat i interwałów, zobacz tabelę w kroku 2.

- Przykładowy skrypt podany w tym artykule nie jest obsługiwany w ramach żadnego standardowego programu lub usługi pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. W żadnym wypadku firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptu nie będą odpowiadać za żadne szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowego skryptu lub dokumentacji lub nieumiejętnego używania tego skryptu lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-connect-to-exchange-online-powershell"></a>Krok 1. Połączenie do Exchange Online PowerShell

Pierwszym krokiem jest połączenie się z programem Exchange Online PowerShell. Możesz połączyć się przy użyciu nowoczesnego uwierzytelniania lub uwierzytelniania wieloskładnikowego (MFA). Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>Krok 2. Modyfikowanie i uruchamianie skryptu w celu pobrania rekordów inspekcji

Po na połączeniu z programem Exchange Online PowerShell następnym krokiem jest utworzenie, zmodyfikowanie i uruchomienie skryptu w celu pobrania danych inspekcji. Pierwszych siedem wierszy skryptu przeszukiwania dziennika inspekcji zawiera następujące zmienne, które można modyfikować w celu skonfigurowania wyszukiwania. Opis tych zmiennych został wyświetlony w tabeli w kroku 2.

1. Zapisz poniższy tekst w skrypcie Windows PowerShell, używając sufiksu nazwy pliku .ps1. Na przykład: SearchAuditLog.ps1.

   ```powershell
   #Modify the values for the following variables to configure the audit log search.
   $logFile = "d:\AuditLogSearch\AuditLogSearchLog.txt"
   $outputFile = "d:\AuditLogSearch\AuditLogRecords.csv"
   [DateTime]$start = [DateTime]::UtcNow.AddDays(-1)
   [DateTime]$end = [DateTime]::UtcNow
   $record = "AzureActiveDirectory"
   $resultSize = 5000
   $intervalMinutes = 60
   
   #Start script
   [DateTime]$currentStart = $start
   [DateTime]$currentEnd = $start
   
   Function Write-LogFile ([String]$Message)
   {
       $final = [DateTime]::Now.ToUniversalTime().ToString("s") + ":" + $Message
       $final | Out-File $logFile -Append
   }
   
   Write-LogFile "BEGIN: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize."
   Write-Host "Retrieving audit records for the date range between $($start) and $($end), RecordType=$record, ResultsSize=$resultSize"
   
   $totalCount = 0
   while ($true)
   {
       $currentEnd = $currentStart.AddMinutes($intervalMinutes)
       if ($currentEnd -gt $end)
       {
           $currentEnd = $end
       }
   
       if ($currentStart -eq $currentEnd)
       {
           break
       }
   
       $sessionID = [Guid]::NewGuid().ToString() + "_" +  "ExtractLogs" + (Get-Date).ToString("yyyyMMddHHmmssfff")
       Write-LogFile "INFO: Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       Write-Host "Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       $currentCount = 0
   
       $sw = [Diagnostics.StopWatch]::StartNew()
       do
       {
           $results = Search-UnifiedAuditLog -StartDate $currentStart -EndDate $currentEnd -RecordType $record -SessionId $sessionID -SessionCommand ReturnLargeSet -ResultSize $resultSize
   
           if (($results | Measure-Object).Count -ne 0)
           {
               $results | export-csv -Path $outputFile -Append -NoTypeInformation
   
               $currentTotal = $results[0].ResultCount
               $totalCount += $results.Count
               $currentCount += $results.Count
               Write-LogFile "INFO: Retrieved $($currentCount) audit records out of the total $($currentTotal)"
   
               if ($currentTotal -eq $results[$results.Count - 1].ResultIndex)
               {
                   $message = "INFO: Successfully retrieved $($currentTotal) audit records for the current time range. Moving on!"
                   Write-LogFile $message
                   Write-Host "Successfully retrieved $($currentTotal) audit records for the current time range. Moving on to the next interval." -foregroundColor Yellow
                   ""
                   break
               }
           }
       }
       while (($results | Measure-Object).Count -ne 0)
   
       $currentStart = $currentEnd
   }
   
   Write-LogFile "END: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize, total count: $totalCount."
   Write-Host "Script complete! Finished retrieving audit records for the date range between $($start) and $($end). Total count: $totalCount" -foregroundColor Green
   ```

2. Zmodyfikuj zmienne wymienione w poniższej tabeli, aby skonfigurować kryteria wyszukiwania. Skrypt zawiera przykładowe wartości tych zmiennych, ale należy je zmienić (o ile nie określono inaczej) w celu spełnienia określonych wymagań.

   <br>

   ****

   |Zmienna|Wartość przykładowa|Opis|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Określa nazwę i lokalizację pliku dziennika zawierającego informacje o postępie przeszukiwania dziennika inspekcji wykonywanego przez skrypt. Skrypt zapisuje sygnatury czasowe UTC w pliku dziennika.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Określa nazwę i lokalizację pliku CSV zawierającego rekordy inspekcji zwrócone przez skrypt.|
   |`[DateTime]$start` i `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Określa zakres dat przeszukiwania dziennika inspekcji. Skrypt zwróci rekordy działań inspekcji, które miały miejsce w określonym zakresie dat. Aby na przykład zwrócić działania wykonane w styczniu 2021, `"2021-01-01"` `"2021-01-31"` można użyć daty rozpoczęcia i daty zakończenia (pamiętaj, aby otoczyć wartości znakami podwójnego cudzysłowu) Wartość przykładowa w skryptze zwraca rekordy działań wykonanych w poprzednich 24 godzinach. Jeśli nie uwzględnisz w tej wartości sygnatury czasowej, domyślną sygnaturą czasową jest godzina 12:00 (północ) w określonym dniu.|
   |`$record`|"AzureActiveDirectory"|Określa typ rekordu działań inspekcji (nazywanych *również* operacjami), które mają być wyszukiwane. Ta właściwość wskazuje usługę lub funkcję, w przypadku których działanie zostało wyzwolone. Aby uzyskać listę typów rekordów, których można użyć dla tej zmiennej, zobacz Typ rekordu [dziennika inspekcji](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). Możesz użyć nazwy typu rekordu lub wartości wyliszowej. <br/><br/>**Porada:** Aby zwrócić rekordy inspekcji dla wszystkich typów rekordów, użyj wartości `$null` (bez cudzysłowów podwójnych).|
   |`$resultSize`|5000|Określa liczbę wyników zwracanych za każdym razem, gdy polecenie cmdlet **Search-UnifiedAuditLog** jest wywoływane przez skrypt (nazywany *zestawem wyników*). Wartość 5000 jest maksymalną wartością obsługiwaną przez polecenie cmdlet. Pozostaw tę wartość bez mian.|
   |`$intervalMinutes`|60|Aby pomóc pokonać ograniczenie 5000 rekordów zwracanych, ta zmienna pobiera określony zakres danych i wycinkuje go w mniejsze przedziały czasu. Teraz każdy interwał, a nie cały zakres dat, podlega limitowi wyjściowemu 5000 rekordów polecenia. Domyślna wartość 5000 rekordów w 60-minutowym interwale w zakresie dat powinna być wystarczająca dla większości organizacji. Jeśli jednak skrypt zwróci `maximum results limitation reached`błąd , zmniejsz interwał (na przykład do 30 minut lub nawet 15 minut) i ponownie uruchomić skrypt.|
   ||||

   Większość zmiennych wymienionych w poprzedniej tabeli odpowiada parametrom polecenia cmdlet **Search-UnifiedAuditLog** . Aby uzyskać więcej informacji na temat tych parametrów, [zobacz Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Na komputerze lokalnym otwórz program Windows PowerShell i przejdź do folderu, w którym został zapisany zmodyfikowany skrypt.

4. Uruchom skrypt w programie Exchange Online PowerShell, na przykład:

   ```powershell
   .\SearchAuditLog.ps1
   ```

W trakcie wykonywania skryptu są wyświetlane komunikaty o postępie. Po zakończeniu wykonywania skryptu zostanie on utworzenie pliku dziennika i pliku CSV `$logFile` zawierającego rekordy inspekcji oraz zapisanie ich w folderach zdefiniowanych przez zmienne i `$outputFile` .

> [!IMPORTANT]
> Maksymalna liczba rekordów inspekcji zwróconych po każdym uruchomieniu polecenia cmdlet w skrypcie jest ograniczenie do 50 000. Jeśli skrypt zostanie uruchomiony i zwróci 50 000 wyników, prawdopodobnie rekordy inspekcji działań, które wystąpiły w zakresie dat, nie zostaną uwzględnione. W takim przypadku zalecamy podzielenie zakresu dat na mniejsze czasy trwania, a następnie ponowne uruchomić skrypt dla każdego zakresu dat. Jeśli na przykład zakres dat to 90 dni zwraca 50 000 wyników, można uruchomić ponownie skrypt dwa razy — raz dla pierwszych 45 dni w zakresie dat, a następnie ponownie przez następne 45 dni.

## <a name="step-3-format-and-view-the-audit-records"></a>Krok 3. Formatowanie i wyświetlanie rekordów inspekcji

Po uruchomieniu skryptu i wyeksportowaniu rekordów inspekcji do pliku CSV możesz sformatować ten plik w celu ułatwienia przeglądania i analizowania rekordów inspekcji. Można to zrobić za pomocą funkcji przekształcania JSON dodatku Power Query w programie Excel w celu podzielenia każdej właściwości obiektu JSON w kolumnie **Dane** inspekcji na własną kolumnę. Aby uzyskać instrukcje krok po kroku, zobacz "Krok 2. Formatowanie wyeksportowanego dziennika inspekcji przy użyciu Edytora dodatku Power Query" w temacie Eksportowanie, konfigurowanie i [wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
