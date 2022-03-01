---
title: Odświeżanie dokładnego pliku tabeli źródła informacji dopasowanego do twoich potrzeb
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Odświeżanie pliku tabeli źródłowej informacji poufnych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 14ef2997da92e0f902fd757a3cbff2735fdeada5
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015425"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Odświeżanie dokładnie tych danych, które są zgodne z plikiem tabeli źródłowej informacji poufnych 

Bazę danych z informacjami poufnymi można odświeżać nawet 5 razy w okresie 24 godzin. Będzie trzeba ponownie przechować i przekazać tabelę źródła informacji poufnych.

1. Ponownie wyeksportuj poufne dane do aplikacji, na przykład Microsoft Excel, i zapisz plik w formacie rozdzielanym .csv, formacie tsv lub rozdzielanym pipetą (|). Zachowaj tę samą nazwę i lokalizację pliku, które były używane podczas uprzednio zhakowanych i przekazanych plików. Aby uzyskać [szczegółowe informacje na temat eksportowania](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) poufnych danych i uzyskiwania odpowiedniego formatu, zobacz Eksportowanie danych źródłowych w celu uzyskania dokładnego dopasowania danych na podstawie typu informacji poufnych.

      > [!NOTE]
      > Jeśli nie ma żadnych zmian w strukturze (nazwach pól) pliku tabeli źródłowej informacji poufnych, nie musisz wprowadzać żadnych zmian w pliku schematu bazy danych podczas odświeżania danych. Jeśli jednak musisz wprowadzić zmiany, odpowiednio edytuj schemat bazy danych i pakiet reguł. Zobacz [Zarządzanie schematem dokładnego dopasowania danych](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) , aby uzyskać instrukcje edytowania lub usuwania schematu. Zobacz Tworzenie [dokładnego dopasowania danych do typów informacji poufnych/pakietu reguł,](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) aby uzyskać instrukcje edytowania lub usuwania pakietu EDM SIT/pakietu reguł.

2. Użyj procedur z [skrótu i przekaż](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) tabelę źródła informacji poufnych, aby dokładnie dopasować dane do typów informacji poufnych, aby przekazać plik źródłowy tabeli z informacjami poufnymi.

2. Za pomocą harmonogramu [zadań można](/windows/desktop/TaskSchd/task-scheduler-start-page) zautomatyzować tabelę Skrót i przekazać tabelę źródła informacji poufnych, aby dokładnie dopasować dane do [procedury typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . Zadania można planować przy użyciu kilku metod:

   |Metoda|Co należy zrobić|
   |---|---|
   |Windows PowerShell|Zapoznaj się z [dokumentacją programu ScheduledTasks](/powershell/module/scheduledtasks/) i [przykładem skryptu programu PowerShell](#example-powershell-script-for-task-scheduler) w tym artykule|
   |Interfejs API harmonogramu zadań|Zapoznaj się [z dokumentacją harmonogramu](/windows/desktop/TaskSchd/using-the-task-scheduler) zadań|
   |Windows interfejsu użytkownika|W Windows kliknij przycisk **Start** i wpisz tekst Harmonogram zadań. Następnie na liście wyników kliknij prawym przyciskiem myszy pozycję **Harmonogram** zadań i wybierz pozycję **Uruchom jako administrator**.|

### <a name="example-powershell-script-for-task-scheduler"></a>Przykładowy skrypt programu PowerShell dla harmonogramu zadań 

W tej sekcji znajduje się przykładowy skrypt programu PowerShell, za pomocą których można zaplanować zadania związane z przekazywaniem skrótów danych i przekazywaniem mieszanych danych:

#### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Planowanie skrótów i przekazywanie w połączonym kroku

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Planowanie skrótów i przekazywanie ich jako oddzielnych kroków

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
