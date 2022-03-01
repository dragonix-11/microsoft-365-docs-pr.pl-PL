---
title: Przykłady poleceń odpowiedzi na żywo
description: Dowiedz się, jak uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo dla programu Microsoft Defender dla punktu końcowego, oraz zobacz przykłady dotyczące sposobu ich działania.
keywords: example, command, cli, remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file
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
ms.openlocfilehash: c91c0c5afc449d2e8fdfc415fae83fcc2c913c6a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010378"
---
# <a name="live-response-command-examples"></a>Przykłady poleceń odpowiedzi na żywo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Dowiedz się więcej o typowych poleceniach używanych w odpowiedzi na żywo i poznaj przykłady ich zwykle używanych poleceń.

W zależności od posiadanych ról możesz uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo. Aby uzyskać więcej informacji na temat poleceń podstawowych i zaawansowanych, zobacz [Badanie jednostek na urządzeniach przy użyciu funkcji odpowiedzi na żywo](live-response.md).

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
> Za pomocą tego polecenia z *poziomu funkcji Live* Response nie można pobrać następujących typów plików:
>
> - [Ponowne rozdęcie plików punktowych](/windows/desktop/fileio/reparse-points/)
> - [Zarzekasz pliki](/windows/desktop/fileio/sparse-files/)
> - Puste pliki
> - Pliki wirtualne lub pliki, które nie są w pełni obecne lokalnie
>
> Te typy *plików są obsługiwane* przez [program PowerShell](/powershell/scripting/overview).
>
> Jeśli masz problemy z używaniem tego polecenia z poziomu funkcji Live Response, użyj programu PowerShell jako alternatywy.

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
# Show information about a specific registry value
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
> W przypadku długich poleceń, takich jak "**run**" lub **"getfile**", możesz użyć symbolu "**&**" na końcu polecenia, aby wykonać tę akcję w tle.
> Umożliwi to kontynuowanie badania komputera i powrót do polecenia w tle po użyciu polecenia "**fg**["](live-response.md#basic-commands).

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
