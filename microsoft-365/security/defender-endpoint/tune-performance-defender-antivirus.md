---
title: Analizator wydajności dla Program antywirusowy Microsoft Defender
description: W tym artykule opisano procedurę dostosowania wydajności Program antywirusowy Microsoft Defender.
keywords: tune, performance, microsoft defender for endpoint, defender antivirus
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 91dd3dc8563e7bd443362c47190139101a5ede61
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016578"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Analizator wydajności dla Program antywirusowy Microsoft Defender

**Dotyczy**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Co to Program antywirusowy Microsoft Defender analizatora wydajności?**

W niektórych przypadkach może być konieczne dostosowanie wydajności programu Program antywirusowy Microsoft Defender skanuje określone pliki i foldery. Analizator wydajności to narzędzie wiersza polecenia programu PowerShell, które pomaga określić, które pliki, rozszerzenia plików i procesy mogą powodować problemy z wydajnością w poszczególnych punktach końcowych. Te informacje mogą być używane do lepszego oceniania problemów z wydajnością i stosowania działań naprawczych.

Dostępne są między innymi następujące opcje do przeanalizowania:

- Najważniejsze pliki wpływające na czas skanowania
- Najważniejsze procesy wpływające na czas skanowania
- Najważniejsze rozszerzenia plików, które wpływają na czas skanowania
- Kombinacje — na przykład najważniejsze pliki na rozszerzenie, najlepsze skany w trakcie każdego pliku, najlepsze skany na plik w trakcie procesu

## <a name="running-performance-analyzer"></a>Uruchamianie Analizatora wydajności

Proces wysokiego poziomu dla uruchomionego analizatora wydajności obejmuje następujące kroki:

1. Uruchom Analizatora wydajności, aby zebrać nagranie wydajności Program antywirusowy Microsoft Defender zdarzeń w punkcie końcowym.

   > [!NOTE]
   > Wydajność Program antywirusowy Microsoft Defender zdarzeń typu **Microsoft-Antimalware-Engine** jest rejestrowana za pośrednictwem analizatora wydajności.

2. Przeanalizuj wyniki skanowania przy użyciu różnych raportów nagrań.

## <a name="using-performance-analyzer"></a>Używanie Analizatora wydajności

Aby rozpocząć nagrywanie zdarzeń systemowych, otwórz program PowerShell w trybie administracyjnym i wykonaj następujące czynności:

1. Uruchom następujące polecenie, aby rozpocząć nagrywanie:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`
 
    gdzie `-RecordTo` parametr określa pełną lokalizację ścieżki, w której zapisano plik śledzenia. Aby uzyskać więcej informacji o poleceniach cmdlet, [Program antywirusowy Microsoft Defender polecenia cmdlet](/powershell/module/defender).

2. Jeśli istnieją procesy lub usługi, które powinny mieć wpływ na wydajność, odtąd wykonywać odpowiednie zadania.

3. Naciśnij **klawisz ENTER** , aby zatrzymać i zapisać nagranie, lub **klawisze Ctrl+C** , aby anulować nagrywanie.

4. Analizowanie wyników przy użyciu parametru analizatora `Get-MpPerformanceReport`wydajności. Na przykład podczas wykonywania `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`polecenia użytkownik ma dostęp do listy dziesięciu najlepszych skanów w poszukiwaniu 3 najwyższych plików wpływających na wydajność. 

Aby uzyskać więcej informacji na temat parametrów i opcji wiersza polecenia, zobacz [New-MpPerformanceRecording](#new-mpperformancerecording) i [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> Jeśli podczas uruchamiania nagrywania zostanie wyświetlany komunikat o błędzie "Nie można uruchomić rejestrowania wydajności, ponieważ rejestrator wydajności Windows już nagrywa", uruchom następujące polecenie, aby zatrzymać istniejące śledzenia za pomocą nowego polecenia: **wpr -cancel -instancename MSFT_MpPerformanceRecording**

### <a name="performance-tuning-data-and-information"></a>Dostosowywanie wydajności danych i informacji

Na podstawie zapytania użytkownik będzie mógł wyświetlać dane dotyczące liczby skanów, czasu trwania (suma/min/średnia/maks/mediana), ścieżki, procesu i przyczyny skanowania. Na poniższej ilustracji przedstawiono przykładowe dane wyjściowe dla prostego zapytania z 10 najwyższych plików w celu oceny wyników skanowania. 

:::image type="content" source="images/example-output.png" alt-text="Przykład danych wyjściowych dla podstawowego zapytania TopFiles":::

### <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Dodatkowe funkcje: eksportowanie i konwertowanie na pliki CSV i JSON

Wyniki analizatora wydajności można również wyeksportować i przekonwertować na plik CSV lub JSON.
Przykłady opisujące proces eksportowania i konwertowania za pomocą przykładowych kodów przedstawiono poniżej.

#### <a name="for-csv"></a>W przypadku pliku CSV

- **Aby wyeksportować**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Aby przekonwertować**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

#### <a name="for-json"></a>W przypadku JSON

- **Aby przekonwertować**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

### <a name="requirements"></a>Wymagania
Program antywirusowy Microsoft Defender wydajności ma następujące wymagania wstępne:

- Obsługiwane Windows wersji: Windows 10, Windows 11 i Windows Server 2016 i wyżej
- Wersja platformy: 4.18.2108.7+
- Wersja programu PowerShell: PowerShell w wersji 5.1, PowerShell ISE, zdalny program PowerShell (4.18.2201.10+), PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>Informacje o programie PowerShell
Istnieją dwa nowe polecenia cmdlet programu PowerShell używane do dostosowania wydajności Program antywirusowy Microsoft Defender: 

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)


### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

W poniższej sekcji opisano informacje dotyczące nowego polecenia cmdlet programu PowerShell New-MpPerformanceRecording. To polecenie cmdlet zbiera nagranie wydajności Program antywirusowy Microsoft Defender skanów.

#### <a name="syntax-new-mpperformancerecording"></a>Składnia: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Opis: New-MpPerformanceRecording
Polecenie `New-MpPerformanceRecording` cmdlet zbiera nagranie wydajności Program antywirusowy Microsoft Defender skanów. Te nagrania wydajności zawierają zdarzenia procesu procesu kernelu MICROSOFT-Antimalware Engine i NT i można je analizować po zbiorze za pomocą polecenia cmdlet [Get-MpPerformanceReport](#get-mpperformancereport) .

To `New-MpPerformanceRecording` polecenie cmdlet dostarcza szczegółowych informacji o problematycznych plikach, które mogą powodować pogorszenie wydajności Program antywirusowy Microsoft Defender. To narzędzie jest udostępniane w stanie takim, w ile jest, i nie ma na celu dosyć sugestii dotyczących wykluczeń. Wykluczenia mogą zmniejszać poziom ochrony punktów końcowych. O ile takie wyjątki są w nim zdefiniowane, należy zachować ostrożność.

Aby uzyskać więcej informacji na temat Analizatora wydajności, zobacz [Dokumenty Analizatora](/windows-hardware/test/wpt/windows-performance-analyzer) wydajności.

> [!IMPORTANT]
> To polecenie cmdlet wymaga podwyższonych uprawnień administratora.

**Obsługiwane wersje systemu operacyjnego**

Windows wersji 10 lub nowszej.

> [!NOTE]
> Ta funkcja jest dostępna od wersji platformy 4.18.2108.X i nowszych.

#### <a name="examples-new-mpperformancerecording"></a>Przykłady: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Przykład 1. Zbieranie nagrania z wydajności i zapisywanie go

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

Powyższe polecenie zbiera nagranie wydajności i zapisuje je w określonej ścieżce: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>Przykład 2. Zbieranie nagrania wydajności dla zdalnej sesji programu PowerShell

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

Powyższe polecenie zbiera nagranie wydajności z serwera Server02 (określone przez argument $s sesji parametru) i zapisuje je w określonej ścieżce: **C:\LocalPathOnServer02\trace.etl** w programie Server02.

#### <a name="parameters-new-mpperformancerecording"></a>Parametry: New-MpPerformanceRecording

##### <a name="-recordto"></a>— RecordTo
Określa lokalizację zapisywania nagrania wydajności programu Microsoft Defender Antimalware.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-session"></a>— Sesja 
Określa obiekt PSSession, w którym ma być tworzyć i zapisywać Program antywirusowy Microsoft Defender wydajności. W przypadku użycia tego parametru parametr RecordTo odwołuje się do ścieżki lokalnej na komputerze zdalnym. Dostępny na platformie Defender w wersji 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

W poniższej sekcji opisano Get-MpPerformanceReport cmdlet programu PowerShell. Analizuje i raporty dotyczące Program antywirusowy Microsoft Defender wydajności MDAV.

#### <a name="syntax-get-mpperformancereport"></a>Składnia: Get-MpPerformanceReport

```powershell
Get-MpPerformanceReport    [-Path] <String>
[-TopScans <Int32>]
[-TopFiles  <Int32>
    [-TopScansPerFile <Int32>]
    [-TopProcessesPerFile  <Int32>  
        [-TopScansPerProcessPerFile <Int32>]
    ]
] 
[-TopExtensions  <Int32>
    [-TopScansPerExtension <Int32>]
    [-TopProcessesPerExtension <Int32>
        [-TopScansPerProcessPerExtension <Int32>]
        ]
    [-TopFilesPerExtension  <Int32>
        [-TopScansPerFilePerExtension <Int32>]
        ]
    ] 
]
[-TopProcesses  <Int32>
    [-TopScansPerProcess <Int32>]
    [-TopExtensionsPerProcess <Int32>
        [-TopScansPerExtensionPerProcess <Int32>]
    ]
]
[-TopFilesPerProcess  <Int32>
    [-TopScansPerFilePerProcess <Int32>]
]
[-MinDuration <String>]
```

#### <a name="description-get-mpperformancereport"></a>Opis: Get-MpPerformanceReport
`Get-MpPerformanceReport` Polecenie cmdlet analizuje poprzednio zebrane nagranie wydajności programu Program antywirusowy Microsoft Defender ([New-MpPerformanceRecording](#new-mpperformancerecording)) i raportuje ścieżki plików, rozszerzenia plików oraz procesy, które powodują największe Program antywirusowy Microsoft Defender skanów.

Analizator wydajności dostarcza szczegółowych informacji o problematycznych plikach, które mogą powodować pogorszenie wydajności Program antywirusowy Microsoft Defender. To narzędzie jest udostępniane w stanie takim, w ile jest, i nie ma na celu dosyć sugestii dotyczących wykluczeń. Wykluczenia mogą zmniejszać poziom ochrony punktów końcowych. O ile takie wyjątki są w nim zdefiniowane, należy zachować ostrożność.

Aby uzyskać więcej informacji na temat Analizatora wydajności, zobacz [Dokumenty Analizatora](/windows-hardware/test/wpt/windows-performance-analyzer) wydajności.

**Obsługiwane wersje systemu operacyjnego**

Windows wersji 10 lub nowszej.

> [!NOTE]
> Ta funkcja jest dostępna od wersji platformy 4.18.2108.X i nowszych.

#### <a name="examples-get-mpperformancereport"></a>Przykłady: Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>Przykład 1. Jedno zapytanie 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>Przykład 2. Wiele zapytań 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>Przykład 3. Zapytania zagnieżdżone 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>Przykład 4. Użycie parametru -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```

#### <a name="parameters-get-mpperformancereport"></a>Parametry: Get-MpPerformanceReport

##### <a name="-minduration"></a>— MinDuration
Określa minimalny czas trwania każdego skanowania lub całkowitego czasu trwania skanowania plików, rozszerzeń i procesów zawartych w raporcie. przyjmuje wartości, takie jak  **0,1234567sec**, **0,1234 ms**, **0,1us** lub prawidłowy czasowy.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-path"></a>— Ścieżka
Określa ścieżki do jednej lub wielu lokalizacji.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### <a name="-topextensions"></a>-TopExtensions 
Określa liczbę najwyższych rozszerzeń do wyprowadzeń posortowanych według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess 
Określa liczbę najwyższych rozszerzeń do wyprowadzania dla każdego procesu, sortowanych według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfiles"></a>-TopFiles
Żąda raportu o najwyższej jakości plików i określa, ile najwyższych plików ma być wyprowadzanych, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperextension"></a>-TopFilesPerExtension 
Określa, ile najwyższych plików wyjściowych ma być wyprowadzanych dla każdego najwyższego rozszerzenia, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperprocess"></a>-TopFilesPerProcess
Określa liczbę najwyższych plików wyjściowych dla każdego procesu, posortowanych według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocesses"></a>-TopProcesses
Żąda raportu o najlepszych procesach i określa liczbę procesów, które mają być wyprowadzone, sortowanych według "Czasu trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension 
Określa liczbę procesów, które mają być wyprowadzone dla każdego najwyższego rozszerzenia, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topprocessesperfile"></a>-TopProcessesPerFile
Określa liczbę procesów, które mają być wyprowadzone w przypadku każdego najwyższego pliku, sortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscans"></a>-TopScans
Żąda raportu z górnym skanowaniem i określa liczbę skanów do wyprowadzowania, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextension"></a>-TopKansPerExtension
Określa liczbę skanów w górnym rogu do wyprowadzeniu dla każdego górnego rozszerzenia, sortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextensionperprocess"></a>-TopKansPerExtensionPerProcess 
Określa liczbę skanów w górnym rogu dla każdego górnego rozszerzenia dla każdego procesu, posortowane według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfile"></a>-TopFileSPerFile
Określa liczbę skanów w górnym rogu dla każdego najlepszego pliku, sortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperfileperextension"></a>-TopFilesPerFilePerExtension 
Określa liczbę skanów w górnym rogu dla każdego najlepszego pliku dla każdego najwyższego rozszerzenia, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfileperprocess"></a>-TopFilesPerFilePerProcess 
Określa liczbę skanów w górnym rogu każdego najlepszego pliku w każdym górnym procesie, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperprocess"></a>-TopKansPerProcess 
Określa liczbę najwyższych skanów do wyprowadzania dla każdego najlepszego procesu w raporcie Najważniejsze procesy, sortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperextension"></a>-TopKansPerProcessPerExtension
Określa liczbę skanów w górnym rogu każdego procesu dla każdego najwyższego rozszerzenia, sortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperfile"></a>-TopFilesPerProcessPerFile
Określa liczbę skanów w górnym rogu każdego najlepszego procesu dla każdego najlepszego pliku, posortowanych według "Czas trwania".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
