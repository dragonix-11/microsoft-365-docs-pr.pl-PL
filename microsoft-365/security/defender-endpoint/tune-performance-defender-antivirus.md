---
title: Analizator wydajności dla Program antywirusowy Microsoft Defender
description: Opisuje procedurę dostosowywania wydajności Program antywirusowy Microsoft Defender.
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
ms.openlocfilehash: 43b39cac260f5bda773af6a428304dc898444771
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419599"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Analizator wydajności dla Program antywirusowy Microsoft Defender

**Dotyczy**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

## <a name="what-is-microsoft-defender-antivirus-performance-analyzer"></a>Co to jest Program antywirusowy Microsoft Defender analizator wydajności?

W niektórych przypadkach może być konieczne dostrojenie wydajności Program antywirusowy Microsoft Defender podczas skanowania określonych plików i folderów. Analizator wydajności to narzędzie wiersza polecenia programu PowerShell, które pomaga określić, które pliki, rozszerzenia plików i procesy mogą powodować problemy z wydajnością poszczególnych punktów końcowych. Te informacje mogą służyć do lepszej oceny problemów z wydajnością i stosowania akcji korygowania.

Niektóre opcje analizy obejmują:

- Najważniejsze pliki, które mają wpływ na czas skanowania
- Najważniejsze procesy wpływające na czas skanowania
- Najważniejsze rozszerzenia plików, które mają wpływ na czas skanowania
- Kombinacje — na przykład najważniejsze pliki na rozszerzenie, najczęściej skanowane na plik, najczęściej skanowane na plik na proces

## <a name="running-performance-analyzer"></a>Uruchamianie analizatora wydajności

Proces wysokiego poziomu dotyczący uruchamiania analizatora wydajności obejmuje następujące kroki:

1. Uruchom analizator wydajności, aby zebrać rejestrowanie wydajności Program antywirusowy Microsoft Defender zdarzeń w punkcie końcowym.

   > [!NOTE]
   > Wydajność zdarzeń Program antywirusowy Microsoft Defender typu **Microsoft-Antimalware-Engine** jest rejestrowana za pośrednictwem analizatora wydajności.

2. Przeanalizuj wyniki skanowania przy użyciu różnych raportów nagrywania.

## <a name="using-performance-analyzer"></a>Korzystanie z analizatora wydajności

Aby rozpocząć rejestrowanie zdarzeń systemowych, otwórz program PowerShell w trybie administracyjnym i wykonaj następujące kroki:

1. Uruchom następujące polecenie, aby rozpocząć nagrywanie:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`

    gdzie `-RecordTo` parametr określa pełną lokalizację ścieżki, w której jest zapisywany plik śledzenia. Aby uzyskać więcej informacji na temat poleceń cmdlet, zobacz [Program antywirusowy Microsoft Defender poleceń cmdlet](/powershell/module/defender).

2. Jeśli istnieją procesy lub usługi, które mają wpływ na wydajność, odtwórz sytuację, wykonując odpowiednie zadania.

3. Naciśnij **klawisz ENTER** , aby zatrzymać i zapisać nagrywanie, lub **klawisze Ctrl+C** , aby anulować nagrywanie.

4. Przeanalizuj wyniki przy użyciu parametru analizatora `Get-MpPerformanceReport`wydajności. Na przykład podczas wykonywania polecenia `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`użytkownik otrzymuje listę dziesięciu pierwszych skanów dla 3 pierwszych plików wpływających na wydajność.

Aby uzyskać więcej informacji na temat parametrów i opcji wiersza polecenia, zobacz [New-MpPerformanceRecording](#new-mpperformancerecording) i [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> Jeśli podczas uruchamiania nagrania zostanie wyświetlony błąd "Nie można rozpocząć rejestrowania wydajności, ponieważ Windows rejestrator wydajności jest już nagrywany", uruchom następujące polecenie, aby zatrzymać istniejący ślad za pomocą nowego polecenia: **wpr -cancel -instancename MSFT_MpPerformanceRecording**

## <a name="performance-tuning-data-and-information"></a>Dane i informacje dotyczące dostrajania wydajności

Na podstawie zapytania użytkownik będzie mógł wyświetlać dane pod kątem liczby skanów, czasu trwania (łączna/minimalna/średnia/maksymalna/mediana), ścieżki, procesu i przyczyny skanowania. Na poniższej ilustracji przedstawiono przykładowe dane wyjściowe dla prostego zapytania 10 pierwszych plików pod kątem wpływu skanowania.

:::image type="content" source="images/example-output.png" alt-text="Przykładowe dane wyjściowe podstawowego zapytania TopFiles" lightbox="images/example-output.png":::

## <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Dodatkowe funkcje: eksportowanie i konwertowanie do plików CSV i JSON

Wyniki analizatora wydajności można również wyeksportować i przekonwertować na plik CSV lub JSON.
Przykłady opisujące proces "eksportowania" i "konwertowania" za pomocą przykładowych kodów można znaleźć poniżej.

### <a name="for-csv"></a>Dla pliku CSV

- **Aby wyeksportować**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Aby przekonwertować**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

### <a name="for-json"></a>W przypadku formatu JSON

- **Aby przekonwertować**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

Aby zapewnić możliwość odczytu maszynowego danych wyjściowych na potrzeby eksportowania z innymi systemami przetwarzania danych, zaleca się użycie parametru -Raw dla polecenia Get-MpPerformanceReport. Aby uzyskać szczegółowe informacje, zobacz poniżej

## <a name="requirements"></a>Wymagania

Program antywirusowy Microsoft Defender analizator wydajności ma następujące wymagania wstępne:

- Obsługiwane wersje Windows: Windows 10, Windows 11 i Windows Server 2016 i nowsze
- Wersja platformy: 4.18.2108.7+
- Wersja programu PowerShell: PowerShell w wersji 5.1, PowerShell ISE, zdalny program PowerShell (4.18.2201.10+), PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>Dokumentacja programu PowerShell

Istnieją dwa nowe polecenia cmdlet programu PowerShell służące do dostosowywania wydajności Program antywirusowy Microsoft Defender:

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)

### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

W poniższej sekcji opisano odwołanie do nowego polecenia cmdlet programu PowerShell New-MpPerformanceRecording. To polecenie cmdlet zbiera nagranie wydajności skanowania Program antywirusowy Microsoft Defender.

#### <a name="syntax-new-mpperformancerecording"></a>Składnia: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Opis: New-MpPerformanceRecording

Polecenie `New-MpPerformanceRecording` cmdlet zbiera nagranie wydajności skanowania Program antywirusowy Microsoft Defender. Te nagrania wydajności zawierają zdarzenia procesu jądra Microsoft-Antimalware-Engine i NT i mogą być analizowane po zebraniu za pomocą polecenia cmdlet [Get-MpPerformanceReport](#get-mpperformancereport) .

To `New-MpPerformanceRecording` polecenie cmdlet zapewnia wgląd w problematyczne pliki, które mogą powodować obniżenie wydajności Program antywirusowy Microsoft Defender. To narzędzie jest dostarczane jako "AS IS" i nie ma na celu przedstawienia sugestii dotyczących wykluczeń. Wykluczenia mogą zmniejszyć poziom ochrony punktów końcowych. Wykluczenia, jeśli istnieją, powinny być definiowane z ostrożnością.

Aby uzyskać więcej informacji na temat analizatora wydajności, zobacz [Analizator wydajności](/windows-hardware/test/wpt/windows-performance-analyzer) dokumentacji.

> [!IMPORTANT]
> To polecenie cmdlet wymaga uprawnień administratora z podwyższonym poziomem uprawnień.

**Obsługiwane wersje systemu operacyjnego**:

Windows wersji 10 lub nowszej.

> [!NOTE]
> Ta funkcja jest dostępna od wersji platformy 4.18.2108.X lub nowszej.

#### <a name="examples-new-mpperformancerecording"></a>Przykłady: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Przykład 1. Zbieranie nagrania wydajności i zapisywanie go

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

Powyższe polecenie zbiera nagranie wydajności i zapisuje je w określonej ścieżce: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>Przykład 2. Zbieranie nagrania wydajności dla sesji zdalnego programu PowerShell

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

Powyższe polecenie zbiera rejestrowanie wydajności na serwerze Server02 (zgodnie z argumentem $s sesji parametru) i zapisuje je w określonej ścieżce: **C:\LocalPathOnServer02\trace.etl** na serwerze Server02.

##### <a name="example-3-collect-a-performance-recording-in-non-interactive-mode"></a>Przykład 3. Zbieranie nagrania wydajności w trybie nieinterakcyjnym
```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl -Seconds 60 
```
Powyższe polecenie zbiera rejestrowanie wydajności dla czasu trwania w sekundach określonego przez parametr -Seconds. Jest to zalecane dla użytkowników prowadzących kolekcje wsadowe, które nie wymagają interakcji ani monitu.

#### <a name="parameters-new-mpperformancerecording"></a>Parametry: New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo

Określa lokalizację, w której ma zostać zapisane nagranie wydajności ochrony przed złośliwym kodem w usłudze Microsoft Defender.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-session"></a>-Session

Określa obiekt PSSession, w którym należy utworzyć i zapisać Program antywirusowy Microsoft Defender rejestrowania wydajności. W przypadku użycia tego parametru parametr RecordTo odwołuje się do ścieżki lokalnej na komputerze zdalnym. Dostępne z platformą Defender w wersji 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-seconds"></a>-Seconds
Określa czas trwania rejestrowania wydajności w sekundach. Jest to zalecane dla użytkowników prowadzących kolekcje wsadowe, które nie wymagają interakcji ani monitu.

```yaml
Type: Int32
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

W poniższej sekcji opisano polecenie cmdlet programu PowerShell Get-MpPerformanceReport. Analizuje i raportuje rejestrowanie wydajności Program antywirusowy Microsoft Defender (MDAV).

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
[-Raw]
```

#### <a name="description-get-mpperformancereport"></a>Opis: Get-MpPerformanceReport

Polecenie `Get-MpPerformanceReport` cmdlet analizuje wcześniej zebrane Program antywirusowy Microsoft Defender rejestrowanie wydajności ([New-MpPerformanceRecording](#new-mpperformancerecording)) i raportuje ścieżki plików, rozszerzenia plików i procesy, które powodują największy wpływ na Program antywirusowy Microsoft Defender skanowania.

Analizator wydajności zapewnia wgląd w problematyczne pliki, które mogą powodować obniżenie wydajności Program antywirusowy Microsoft Defender. To narzędzie jest dostarczane jako "AS IS" i nie ma na celu przedstawienia sugestii dotyczących wykluczeń. Wykluczenia mogą zmniejszyć poziom ochrony punktów końcowych. Wykluczenia, jeśli istnieją, powinny być definiowane z ostrożnością.

Aby uzyskać więcej informacji na temat analizatora wydajności, zobacz [Analizator wydajności](/windows-hardware/test/wpt/windows-performance-analyzer) dokumentacji.

**Obsługiwane wersje systemu operacyjnego**:

Windows wersji 10 lub nowszej.

> [!NOTE]
> Ta funkcja jest dostępna od wersji platformy 4.18.2108.X lub nowszej.

#### <a name="examples-get-mpperformancereport"></a>Przykłady: Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>Przykład 1: pojedyncze zapytanie

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>Przykład 2: Wiele zapytań

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>Przykład 3: Zapytania zagnieżdżone

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>Przykład 4. Używanie parametru -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```
##### <a name="example-5-using--raw-parameter"></a>Przykład 5. Używanie parametru -Raw

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10 -Raw | ConvertTo-Json
```
Użycie polecenia -Raw w powyższym poleceniu określa, że dane wyjściowe powinny być czytelne dla maszyny i łatwo można je konwertować na formaty serializacji, takie jak JSON

#### <a name="parameters-get-mpperformancereport"></a>Parametry: Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration

Określa minimalny czas trwania skanowania lub łączny czas trwania skanowania plików, rozszerzeń i procesów zawartych w raporcie; akceptuje wartości takie jak  **0.1234567sec**, **0.1234ms**, **0.1us** lub prawidłowy timeSpan.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-path"></a>-Ścieżka

Określa ścieżki do co najmniej jednej lokalizacji.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```
##### <a name="-raw"></a>-Nieprzetworzone

Określa, że dane wyjściowe rejestrowania wydajności powinny być czytelne dla komputera i łatwo można je konwertować na formaty serializacji, takie jak JSON (na przykład za pomocą polecenia Convert-to-JSON). Jest to zalecane dla użytkowników zainteresowanych przetwarzaniem wsadowym z innymi systemami przetwarzania danych. 

```yaml
Type: <SwitchParameter>
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensions"></a>-TopExtensions

Określa, ile górnych rozszerzeń do danych wyjściowych, posortowane według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess

Określa, ile górnych rozszerzeń do danych wyjściowych dla każdego górnego procesu, posortowane według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfiles"></a>-TopFiles

Żąda raportu z najwyższą liczbą plików i określa liczbę najważniejszych plików do danych wyjściowych posortowanych według wartości "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperextension"></a>-TopFilesPerExtension

Określa liczbę najlepszych plików do wyświetlenia dla każdego górnego rozszerzenia posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperprocess"></a>-TopFilesPerProcess

Określa liczbę najlepszych plików do wyświetlenia dla każdego najwyższego procesu posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocesses"></a>-TopProcesses

Żąda raportu top-processes i określa, ile z najważniejszych procesów do danych wyjściowych, posortowane według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension

Określa liczbę najlepszych procesów do wyświetlenia dla każdego górnego rozszerzenia posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperfile"></a>-TopProcessesPerFile

Określa liczbę najważniejszych procesów do wyświetlenia dla każdego najwyższego pliku posortowanych według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscans"></a>-TopScans

Żąda najwyższego skanowania raportu i określa, ile top skanowania do danych wyjściowych, posortowane według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextension"></a>-TopScansPerExtension

Określa liczbę najczęściej skanowanych danych wyjściowych dla każdego górnego rozszerzenia posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess

Określa liczbę najczęściej skanowanych danych wyjściowych dla każdego górnego rozszerzenia dla każdego najwyższego procesu posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfile"></a>-TopScansPerFile

Określa liczbę najczęściej skanowanych danych wyjściowych dla każdego najwyższego pliku posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension

Określa liczbę najczęściej skanowanych danych wyjściowych dla każdego najwyższego pliku dla każdego górnego rozszerzenia posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess

Określa, ile najczęściej skanuje dane wyjściowe dla każdego najwyższego pliku dla każdego najwyższego procesu, posortowane według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocess"></a>-TopScansPerProcess

Określa, ile najlepszych skanów do danych wyjściowych dla każdego najwyższego procesu w raporcie Top Processes posortowane według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension

Określa liczbę najczęściej skanowanych danych wyjściowych dla każdego najwyższego procesu dla każdego górnego rozszerzenia posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile

Określa liczbę najczęściej skanowanych danych wyjściowych dla każdego najwyższego procesu dla każdego najwyższego pliku posortowanego według "Czas trwania".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## <a name="additional-resources"></a>Dodatkowe materiały

Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:

- [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
- [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
- [Konfigurowanie usługi Defender for Endpoint w funkcjach](android-configure.md)-  Android [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender na funkcjach iOS](ios-configure-features.md)
