---
title: Przykłady poleceń reagowania w czasie rzeczywistym
description: Dowiedz się, jak uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo dla Ochrona punktu końcowego w usłudze Microsoft Defender i zobacz przykłady sposobu ich użycia.
keywords: przykład, polecenie, interfejs wiersza polecenia, zdalny, powłoka, połączenie, na żywo, odpowiedź, w czasie rzeczywistym, polecenie, skrypt, korygowanie, wyszukiwanie, eksport, dziennik, upuszczanie, pobieranie, plik
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 77a1bd5c9234b7a38266be55825726e683557eb4
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872392"
---
# <a name="live-response-command-examples"></a>Przykłady poleceń reagowania w czasie rzeczywistym

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Dowiedz się więcej o typowych poleceniach używanych w odpowiedzi na żywo i zobacz przykłady dotyczące ich typów.

W zależności od posiadanych ról można uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo. Aby uzyskać więcej informacji na temat podstawowych i zaawansowanych poleceń, zobacz [Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo](live-response.md).

## `analyze`

```console
# Analyze the file malware.txt
analyze file c:\Users\user\Desktop\malware.txt
```

```console
# Analyze the process by PID
analyze process 1234
```

## `connections`

```console
# List active connections in json format using parameter name
connections -output json
```

```console
# List active connections in json format without parameter name
connections json
```

## `dir`

```console
# List files and sub-folders in the current folder (by default it will show relative paths [-relative_path])
dir
```

```console
# List files and sub-folders in the current folder, with their full path
dir -full_path
```

```console
# List files and sub-folders in a specific folder
dir C:\Users\user\Desktop\
```

```console
# List files and subfolders in the current folder in json format
dir -output json
```

## `fileinfo`

```console
# Display information about a file
fileinfo C:\Windows\notepad.exe
```

## `findfile`

```console
# Find file by name
findfile test.txt
```

## `getfile`

```console
# Download a file from a machine
getfile c:\Users\user\Desktop\work.txt
```

```console
# Download a file from a machine, automatically run prerequisite commands
getfile c:\Users\user\Desktop\work.txt -auto
```

> [!NOTE]
>
> Nie *można* pobrać następujących typów plików przy użyciu tego polecenia z poziomu odpowiedzi na żywo:
>
> - [Ponowna analiza plików punktów](/windows-hardware/drivers/ifs/reparse-points)
> - [Rozrzedzone pliki](/windows-server/administration/windows-commands/fsutil-sparse)
> - Puste pliki
> - Pliki wirtualne lub pliki, które nie są w pełni obecne lokalnie
>
> Te typy plików *są* obsługiwane przez [program PowerShell](/powershell/scripting/overview).
>
> Alternatywnie użyj programu PowerShell, jeśli masz problemy z użyciem tego polecenia z poziomu odpowiedzi na żywo.

## `library`

```console
# List files in the library
library
```

```console
# Delete a file from the library
library delete script.ps1
```

## `processes`

```console
# Show all processes
processes
```

```console
# Get process by pid
processes 123
```

```console
# Get process by pid with argument name
processes -pid 123
```

```console
# Get process by name
processes -name notepad.exe
```

## `putfile`

```console
# Upload file from library
putfile get-process-by-name.ps1
```

```console
# Upload file from library, overwrite file if it exists
putfile get-process-by-name.ps1 -overwrite
```

```console
# Upload file from library, keep it on the machine after a restart
putfile get-process-by-name.ps1 -keep
```

## `registry`

```console
# Show information about the values in a registry key
registry HKEY_CURRENT_USER\Console
```

```console
# Show information about a specific registry value (the double backslash \\ indicates a registry value versus key)
registry HKEY_CURRENT_USER\Console\\ScreenBufferSize
```


## `remediate`

```console
# Remediate file in specific path
remediate file c:\Users\user\Desktop\malware.exe
```

```console
# Remediate process with specific PID
remediate process 7960
```

```console
# Remediate a registry value (the double backslash \\ indicates a registry value versus key)
remediate registry HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run\\SPStartup
```

```console
# See list of all remediated entities
remediate list
```

## `run`

```console
# Run PowerShell script from the library without arguments
run script.ps1
```

```console
# Run PowerShell script from the library with arguments
run get-process-by-name.ps1 -parameters "-processName Registry"
```

> [!NOTE]
>
> W przypadku długotrwałych poleceń, takich jak "**run**" lub "**getfile**", możesz użyć symbolu "**&**" na końcu polecenia, aby wykonać tę akcję w tle.
> Umożliwi to kontynuowanie badania maszyny i powrót do polecenia w tle po wykonaniu polecenia "**fg**" [podstawowego](live-response.md#basic-commands).

## `scheduledtask`

```console
# Get all scheduled tasks
scheduledtasks
```

```console
# Get specific scheduled task by location and name
scheduledtasks Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Get specific scheduled task by location and name with spacing
scheduledtasks "Microsoft\Configuration Manager\Configuration Manager Health Evaluation"
```

## `undo`

```console
# Restore remediated registry
undo registry HKEY_CURRENT_USER\Console\ScreenBufferSize
```

```console
# Restore remediated scheduledtask
undo scheduledtask Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Restore remediated file
undo file c:\Users\user\Desktop\malware.exe
```
