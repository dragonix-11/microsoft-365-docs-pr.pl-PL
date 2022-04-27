---
title: Przeszukaj dziennik inspekcji za pomocą skryptu programu PowerShell
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Użyj skryptu programu PowerShell, który uruchamia polecenie cmdlet Search-UnifiedAuditLog w Exchange Online, aby przeszukać dziennik inspekcji. Ten skrypt jest zoptymalizowany pod kątem zwracania dużego zestawu rekordów inspekcji przy każdym uruchomieniu. Skrypt eksportuje te rekordy do pliku CSV, który można wyświetlić lub przekształcić przy użyciu Power Query w Excel.
ms.openlocfilehash: 8799f1a4ddf2ef7dd536ccb3e6e70a4b731b4cd6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100858"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Przeszukaj dziennik inspekcji za pomocą skryptu programu PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bezpieczeństwo, zgodność i inspekcja stały się priorytetem dla administratorów IT w dzisiejszym świecie. Microsoft 365 ma kilka wbudowanych funkcji ułatwiających organizacjom zarządzanie zabezpieczeniami, zgodnością i inspekcją. W szczególności ujednolicone rejestrowanie inspekcji może pomóc w badaniu zdarzeń zabezpieczeń i problemów ze zgodnością. Dzienniki inspekcji można pobrać przy użyciu następujących metod:

- [Interfejs API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)

- [Narzędzie do wyszukiwania dzienników inspekcji](search-the-audit-log-in-security-and-compliance.md) w portalu zgodności usługi Microsoft Purview

- Polecenie cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online programu PowerShell

Jeśli musisz regularnie pobierać dzienniki inspekcji, rozważ rozwiązanie, które korzysta z interfejsu API działania zarządzania Office 365, ponieważ może zapewnić dużym organizacjom skalowalność i wydajność w celu ciągłego pobierania milionów rekordów inspekcji. Użycie narzędzia do wyszukiwania dzienników inspekcji w portalu zgodności to dobry sposób na szybkie znalezienie rekordów inspekcji dla określonych operacji występujących w krótszym zakresie czasu. Używanie dłuższych zakresów czasu w narzędziu do wyszukiwania dzienników inspekcji, szczególnie w przypadku dużych organizacji, może zwrócić zbyt wiele rekordów, aby łatwo zarządzać nimi lub eksportować.

W sytuacjach, w których konieczne jest ręczne pobranie danych inspekcji dla określonego badania lub zdarzenia, szczególnie w przypadku dłuższych zakresów dat w większych organizacjach, najlepszym rozwiązaniem może być użycie polecenia cmdlet **Search-UnifiedAuditLog** . Ten artykuł zawiera skrypt programu PowerShell, który używa polecenia cmdlet, które może pobrać 50 000 rekordów inspekcji (za każdym razem, gdy uruchamiasz polecenie cmdlet), a następnie eksportować je do pliku CSV, który można sformatować przy użyciu Power Query w Excel, aby ułatwić przegląd. Użycie skryptu w tym artykule minimalizuje również prawdopodobieństwo przekroczenia limitu czasu przeszukiwania dużych dzienników inspekcji w usłudze.

## <a name="before-you-run-the-script"></a>Przed uruchomieniem skryptu

- Rejestrowanie inspekcji musi być włączone, aby organizacja pomyślnie używała skryptu do zwracania rekordów inspekcji. Rejestrowanie inspekcji jest domyślnie włączone dla organizacji Microsoft 365 i Office 365 przedsiębiorstw. Aby sprawdzić, czy wyszukiwanie dzienników inspekcji jest włączone dla Twojej organizacji, możesz uruchomić następujące polecenie w programie Exchange Online programie PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Wartość `True` właściwości **UnifiedAuditLogIngestionEnabled** wskazuje, że wyszukiwanie dziennika inspekcji jest włączone.

- Aby pomyślnie uruchomić skrypt, musisz mieć przypisaną rolę dzienników inspekcji lub dzienników inspekcji View-Only w Exchange Online. Domyślnie te role są przypisywane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie Uprawnienia w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. Aby uzyskać więcej informacji, zobacz sekcję "Wymagania dotyczące przeszukiwania dziennika inspekcji" w [temacie Wyszukaj dziennik inspekcji w centrum zgodności](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- Wykonanie skryptu może zająć dużo czasu. Czas trwania zależy od zakresu dat i rozmiaru interwału konfigurowanego przez skrypt do pobierania rekordów inspekcji. Większe zakresy dat i mniejsze interwały spowodują długi czas trwania. Zobacz tabelę w kroku 2, aby uzyskać więcej informacji na temat zakresu dat i interwałów.

- Przykładowy skrypt podany w tym artykule nie jest obsługiwany w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowy skrypt jest dostarczany jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowego skryptu i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptu nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowego skryptu lub dokumentacji lub niemożności korzystania z niego,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-connect-to-exchange-online-powershell"></a>Krok 1. Połączenie do Exchange Online programu PowerShell

Pierwszym krokiem jest nawiązanie połączenia z programem Exchange Online programu PowerShell. Możesz nawiązać połączenie przy użyciu nowoczesnego uwierzytelniania lub uwierzytelniania wieloskładnikowego (MFA). Aby uzyskać instrukcje krok po kroku, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>Krok 2. Modyfikowanie i uruchamianie skryptu w celu pobrania rekordów inspekcji

Po nawiązaniu połączenia z programem Exchange Online programu PowerShell następnym krokiem jest utworzenie, zmodyfikowanie i uruchomienie skryptu w celu pobrania danych inspekcji. Pierwsze siedem wierszy w skryptze wyszukiwania dziennika inspekcji zawiera następujące zmienne, które można zmodyfikować w celu skonfigurowania wyszukiwania. Zapoznaj się z tabelą w kroku 2, aby uzyskać opis tych zmiennych.

1. Zapisz następujący tekst w skryptze Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1. Na przykład SearchAuditLog.ps1.

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

2. Zmodyfikuj zmienne wymienione w poniższej tabeli, aby skonfigurować kryteria wyszukiwania. Skrypt zawiera przykładowe wartości dla tych zmiennych, ale należy je zmienić (o ile nie określono inaczej), aby spełnić określone wymagania.

   <br>

   ****

   |Zmienna|Przykładowa wartość|Opis|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Określa nazwę i lokalizację pliku dziennika, który zawiera informacje o postępie przeszukiwania dziennika inspekcji wykonywanego przez skrypt. Skrypt zapisuje znaczniki czasu UTC w pliku dziennika.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Określa nazwę i lokalizację pliku CSV zawierającego rekordy inspekcji zwrócone przez skrypt.|
   |`[DateTime]$start` I `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Określa zakres dat wyszukiwania dziennika inspekcji. Skrypt zwróci rekordy dla działań inspekcji, które wystąpiły w określonym zakresie dat. Na przykład w celu zwrócenia działań wykonanych w styczniu 2021 r. można użyć daty `"2021-01-01"` rozpoczęcia i daty `"2021-01-31"` zakończenia (pamiętaj, aby otoczyć wartości w cudzysłowie) Przykładowa wartość w skrypcie zwraca rekordy dla działań wykonywanych w ciągu poprzednich 24 godzin. Jeśli nie uwzględnisz sygnatury czasowej w wartości, domyślny znacznik czasu to 12:00 (północ) w określonej dacie.|
   |`$record`|"AzureActiveDirectory"|Określa typ rekordu działań inspekcji (nazywanych również *operacjami*), które mają być wyszukiwane. Ta właściwość wskazuje usługę lub funkcję, w której zostało wyzwolone działanie. Aby uzyskać listę typów rekordów, których można użyć dla tej zmiennej, zobacz [Audit log record type (Typ rekordu dziennika inspekcji](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype)). Możesz użyć nazwy typu rekordu lub wartości ENUM. <br/><br/>**Wskazówka:** Aby zwrócić rekordy inspekcji dla wszystkich typów rekordów, użyj wartości `$null` (bez znaków podwójnego cudzysłowu).|
   |`$resultSize`|5000|Określa liczbę zwracanych wyników za każdym razem, gdy polecenie cmdlet **Search-UnifiedAuditLog jest wywoływane** przez skrypt (nazywany *zestawem wyników*). Wartość 5000 jest wartością maksymalną obsługiwaną przez polecenie cmdlet. Pozostaw tę wartość w takiej postaci, jaka jest.|
   |`$intervalMinutes`|60|Aby pomóc w pokonaniu limitu 5000 zwróconych rekordów, ta zmienna przyjmuje określony zakres danych i dzieli go na mniejsze interwały czasu. Teraz każdy interwał, a nie cały zakres dat, podlega limitowi danych wyjściowych rekordu 5000 polecenia. Domyślna wartość 5000 rekordów na interwał 60 minut w zakresie dat powinna być wystarczająca dla większości organizacji. Jeśli jednak skrypt zwróci błąd z `maximum results limitation reached`komunikatem , zmniejsz interwał czasu (na przykład do 30 minut lub nawet 15 minut) i uruchom ponownie skrypt.|
   ||||

   Większość zmiennych wymienionych w poprzedniej tabeli odpowiada parametrom polecenia cmdlet **Search-UnifiedAuditLog** . Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Na komputerze lokalnym otwórz Windows PowerShell i przejdź do folderu, w którym zapisano zmodyfikowany skrypt.

4. Uruchom skrypt w programie Exchange Online programu PowerShell, na przykład:

   ```powershell
   .\SearchAuditLog.ps1
   ```

Skrypt wyświetla komunikaty postępu podczas jego działania. Po zakończeniu działania skryptu tworzy plik dziennika i plik CSV zawierający rekordy inspekcji i zapisuje je w folderach zdefiniowanych przez `$logFile` zmienne i `$outputFile` .

> [!IMPORTANT]
> Istnieje limit 50 000 dla maksymalnej liczby rekordów inspekcji zwracanych przy każdym uruchomieniu polecenia cmdlet w skryptze. Jeśli uruchomisz ten skrypt i zwróci on 50 000 wyników, prawdopodobnie rekordy inspekcji dla działań, które wystąpiły w zakresie dat, nie zostały uwzględnione. W takim przypadku zalecamy podzielenie zakresu dat na mniejsze czasy trwania, a następnie ponowne uruchomienie skryptu dla każdego zakresu dat. Jeśli na przykład zakres dat wynoszący 90 dni zwraca 50 000 wyników, możesz ponownie uruchomić skrypt dwa razy, raz przez pierwsze 45 dni w zakresie dat, a następnie ponownie przez następne 45 dni.

## <a name="step-3-format-and-view-the-audit-records"></a>Krok 3. Formatowanie i wyświetlanie rekordów inspekcji

Po uruchomieniu skryptu i wyeksportowaniu rekordów inspekcji do pliku CSV możesz sformatować plik CSV, aby ułatwić przeglądanie i analizowanie rekordów inspekcji. Jednym ze sposobów jest Power Query funkcji przekształcania JSON w Excel, aby podzielić każdą właściwość w obiekcie JSON w kolumnie **AuditData** na własną kolumnę. Aby uzyskać instrukcje krok po kroku, zobacz "Krok 2: Formatowanie wyeksportowanego dziennika inspekcji przy użyciu Edytor Power Query" w temacie [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
