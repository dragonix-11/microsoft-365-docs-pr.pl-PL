---
title: Dzienniki diagnostyczne
description: Dzienniki, które mogą być zbierane z urządzeń podczas rozwiązywania problemów i sposób ich przechowywania
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 808ce2e426a0540c95195f26c9872f569e595715
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014791"
---
# <a name="diagnostic-logs"></a>Dzienniki diagnostyczne

Niezależnie od tego, czy zgłoszono problem, czy został zidentyfikowany przez naszą usługę, może być konieczne zbieranie określonych dzienników diagnostycznych z urządzenia bez interwencji użytkownika.

Nie są zbierane żadne informacje ani zawartość wygenerowana przez użytkownika z katalogów użytkowników. Gromadzimy tylko dane diagnostyczne i dane dziennika, które dotyczą kondycji i stanu urządzenia.

Wszelkie zebrane dzienniki przechowujemy przez 28 dni, a następnie usuwamy je. Wszystkie dzienniki zebrane z urządzenia są przetwarzane zgodnie ze standardami [obsługi danych](privacy-personal-data.md).

## <a name="data-collected"></a>Dane zbierane

Ta lista poniżej zawiera wszystkie foldery, dzienniki zdarzeń, pliki wykonywalne lub lokalizacje rejestru, z Microsoft Managed Desktop z których mogą być zbierane dzienniki diagnostyczne. Rzeczywiste zbierane dane będą podzestawem tej listy i zależą od zidentyfikowanego problemu.

### <a name="registry-keys"></a>Klucze rejestru

- HKLMSYSTEMCurrentControlSetServices\\\\\\
- HKLMSOFTWAREMicrosoftSurface\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows\\ WindowsUpdate
- HKLMSYSTEMCurrentControlSetControlMUIUILanguages\\\\\\\\\\
- HKLMSoftwarePoliciesMicrosoftWindowsStore\\\\\\\\
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionWindowsStoreWindowsUpdate\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppModel\\
- HKLMSYSTEMCurrentControlSetControlFirmwareResources\\\\\\\\
- HKLMSOFTWAREMicrosoftWindowsSelfhost\\\\\\
- HKLMSOFTWAREMicrosoftWindowsUpdate\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppx\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersionSuperrolch\\\\
- HKLMSYSTEMSetup\\\\
- HKLMSoftwareMicrosoftIntuneManagementExtension\\\\\\
- HKLMSOFTWAREMicrosoftSystemCertificatesAuthRoot\\\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows Zaawansowana ochrona przed zagrożeniami
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAuthenticationLogonUI\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionInternet\\ Ustawienia
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSoftwarePolicies\\\\
- HKLMSOFTWAREPoliciesMicrosoftCryptographyConfigurationSSL\\\\\\\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows Advanced Threat Protection
- HKLMSOFTWAREWOW6432NodeMicrosoft\\\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSYSTEMCurrentControlSetControlSecurityProvidersSCHANNEL\\\\\\\\\\

### <a name="commands"></a>Polecenia

- %programfiles%\\windows defender\\mpcmdrun.exe -GetFiles
- %windir%\\system32\\certutil.exe -store
- %windir%\\system32\\certutil.exe -store -user my
- %windir%\\system32\\Dsregcmd.exe /status
- %windir%\\system32\\ipconfig.exe /all
- %windir%\\system32\\ipconfig.exe /displaydns
- %windir%\\system32\\mdmdiagnosticstool.exe
- %windir%\\system32\\msinfo32.exe /report %temp%\\MDMDiagnosticsmsinfo32.log\\
- %windir%\\system32\\netsh.exe advfirewall show allprofiles
- %windir%\\system32\\netsh.exe advfirewall show global
- %windir%\\system32netsh.exe\\ profilów pokazu sieci lan
- %windir%\\system32\\netsh.exe winhttp show proxy
- %windir%\\system32\\netsh.exe wlan show profiles
- %windir%\\system32\\netsh.exe wlan show wlanreport
- %windir%\\system32\\ping.exe -n 50 localhost
- %windir%\\system32\\powercfg.exe /batteryreport /output %temp%\\MDMDiagnostics\\battery-report.html
- %windir%\\system32\\powercfg.exe /energy /output %temp%\\MDMDiagnostics\\energy-report.html
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -nas -get
- Windows PowerShell polecenia:
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype bundle
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32product\_
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32PnPSignedDriver\_

### <a name="event-logs"></a>Dzienniki zdarzeń

- Aplikacja
- Microsoft-Windows-AppLocker/EXE i DLL
- Microsoft-Windows-AppLocker/MSI i skrypt
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Microsoft-Windows-BitLocker/Zarządzanie funkcją BitLocker
- Microsoft-Windows-SENSE/Operational
- Microsoft-Windows-SenseIR/Operational
- Konfigurowanie
- System

### <a name="files"></a>Pliki

- %ProgramData%\\MicrosoftDiagnosticLogCSPCollectors.etl\\\\\\\*
- %ProgramData%\\MicrosoftIntuneManagementExtensionLogs\\\\\\\*.\*
- %ProgramData%\\Microsoft\\ Windows Defender\\ Support\\MpSupportFiles.cab
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport\\wlan-report-latest.html
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport -SourceFileName wlan-report-latest.html
- %windir%\\ccmlogs.log\\\*
- %windir%\\ccmsetuplogs.log\\\*
- %windir%\\logsCBScbs.log\\\\
- %windir%\\logsmeaboot\\.\*\*
- %windir%\\LogsWindowsUpdate.etl\\\*
- %windir%\\inf.log\\\*
- %windir%\\servicingsessions\\\\ActionList.xml
- %windir%\\servicingsessions\\\\Sessions.xml
- %windir%\\SoftwareDistributionDataStoreLogsedb.log\\\\\\
- %windir%\\SoftwareDistributionDataStoreDataStore.edb\\\\
- %windir%\\logsdismdism.log\\\\
- %SystemRoot%\\System32WinevtLogs\\\\\\
- %appdata%\\Microsoft\\ Teams\\ media-stack.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ skylib.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ media-stack.etl\\\*
- %appdata%\\Microsoft\\ Teams\\logs.txt
- %windir%\\Windows System32winevt\\\\\*.\\\*