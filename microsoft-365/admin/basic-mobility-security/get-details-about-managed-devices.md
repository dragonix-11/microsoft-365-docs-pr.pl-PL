---
title: Uzyskaj szczegółowe informacje na temat urządzeń zarządzanych podstawową mobilnością i zabezpieczeń
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Skorzystaj Windows PowerShell, aby uzyskać szczegółowe informacje na temat urządzeń z pakietem Basic Mobility i Zabezpieczeń w Twojej organizacji.
ms.openlocfilehash: 25c7f89dda32121306bfe2434620d17396f2e870
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973643"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Uzyskaj szczegółowe informacje na temat urządzeń zarządzanych podstawową mobilnością i zabezpieczeń

W tym artykule pokazano, jak za pomocą pakietu Windows PowerShell uzyskać szczegółowe informacje o urządzeniach w Twojej organizacji, na których ustawiono mobilność podstawową i zabezpieczenia.

Oto zestawienie dostępnych szczegółów urządzenia.

|**Szczegóły**|**Czego szukać w programie PowerShell**|
|:----------------|:------------------------------------------------------------------------------|
|Urządzenie jest zarejestrowane na stronie Podstawowa mobilność i zabezpieczenia. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego za pomocą platformy Basic Mobility and Security.](enroll-your-mobile-device.md)|Wartość właściwości  *theisManagedparameters*  to:<br/>**True**= urządzenie jest zarejestrowane.<br/>**False** = urządzenie nie jest zarejestrowane. |
|Urządzenie jest zgodne z zasadami zabezpieczeń twoich urządzeń. Aby uzyskać więcej informacji, zobacz [Tworzenie zasad zabezpieczeń urządzeń](create-device-security-policies.md)|Wartość  *właściwościisCompliantparameters*  wynosi:<br/>**True (Prawda)**  = urządzenie jest zgodne z zasadami.<br/>**False (Fałsz**  = urządzenie jest niezgodne z zasadami.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Parametry programu PowerShell w zakresie mobilności podstawowej i zabezpieczeń.":::

> [!NOTE]
> Polecenia i skrypty w tym artykule zwracają również szczegółowe informacje o wszystkich urządzeniach zarządzanych przez  [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby uruchomić polecenia i skrypty opisane w tym artykule, należy skonfigurować kilka czynności.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Krok 1. Pobieranie i instalowanie modułu Azure Active Directory dla Windows PowerShell

Aby uzyskać więcej informacji na temat tych kroków,  [Połączenie aby Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. Przejdź do  [strony Asystent logowania w witrynie Microsoft Online Services Sign-In dla informatyków RTWli](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi)  wybierz pozycję Pobierz dla Asystenta logowania w witrynie  **Microsoft Online Services**.

2. Zainstaluj moduł Microsoft Azure Active Directory dla Windows PowerShell, wykonać następujące czynności:

    1. Otwórz wiersz polecenia programu PowerShell na poziomie administratora.

    2. `Install-Module MSOnline` Uruchom polecenie.

    3. Jeśli zostanie wyświetlony monit o zainstalowanie NuGet, wpisz Y i naciśnij klawisz ENTER.

    4. Jeśli zostanie wyświetlony monit o zainstalowanie modułu od firmy PSGallery, wpisz Y i naciśnij klawisz ENTER.

    5. Po zakończeniu instalacji zamknij okno polecenia programu PowerShell.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Krok 2. Połączenie do subskrypcji Microsoft 365 usługi

1. W Windows Azure Active Directory modułu Windows PowerShell uruchom następujące polecenie.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. W oknie Windows PowerShell żądanie poświadczeń wpisz nazwę użytkownika i hasło dla konta administratora Microsoft 365 globalnego, a następnie wybierz przycisk **OK**.

3. Uruchom następujące polecenie:

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Krok 3. Upewnij się, że możesz uruchamiać skrypty programu PowerShell

> [!NOTE]
> Możesz pominąć ten krok, jeśli masz już ustawione uruchamianie skryptów programu PowerShell.

Aby uruchomić skrypt Get-MsolUserDeviceComplianceStatus.ps1, musisz włączyć uruchamianie skryptów programu PowerShell.

1. Na komputerze Windows wybierz  **pozycjęStart**, a następnie wpisz Windows PowerShell. Kliknij prawym przyciskiem myszy Windows PowerShell, a następnie wybierz  **pozycjęRun jako administrator**.

2. Uruchom następujące polecenie:

   ```powershell
   Set-ExecutionPolicy  RemoteSigned
   ```

3. Po wyświetleniu monitu wpisz Y, a następnie naciśnij klawisz Enter.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Uruchamianie Get-MsolDevice cmdlet w celu wyświetlenia szczegółów dotyczących wszystkich urządzeń w organizacji

1. Otwórz moduł Microsoft Azure Active Directory dla Windows PowerShell.

2. Uruchom następujące polecenie:

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Aby uzyskać więcej przykładów,  [zobacz Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

## <a name="run-a-script-to-get-device-details"></a>Uruchamianie skryptu w celu uzyskania szczegółów urządzenia

Najpierw zapisz skrypt na komputerze.

1. Skopiuj i wklej następujący tekst do Notatnik.

   ```powershell
   param (
   [PSObject[]]$users = @(),
   [Switch]$export,
   [String]$exportFileName = "UserDeviceComplianceStatus_" + (Get-Date -Format "yyMMdd_HHMMss") + ".csv",
   [String]$exportPath = [Environment]::GetFolderPath("Desktop")
   )
   [System.Collections.IDictionary]$script:schema = @{
   DeviceId = ''
   DeviceOSType = ''
   DeviceOSVersion = ''
   DeviceTrustLevel = ''
   DisplayName = ''
   IsCompliant = ''
   IsManaged = ''
   ApproximateLastLogonTimestamp = ''
   DeviceObjectId = ''
   RegisteredOwnerUpn = ''
   RegisteredOwnerObjectId = ''
   RegisteredOwnerDisplayName = ''
   }
   function createResultObject
   {
   [PSObject]$resultObject = New-Object -TypeName PSObject -Property $script:schema
   return $resultObject
   }
   If ($users.Count -eq 0)
   {
   $users = Get-MsolUser
   }
   [PSObject[]]$result = foreach ($u in $users)
   {
   [PSObject]$devices = get-msoldevice -RegisteredOwnerUpn $u.UserPrincipalName
   foreach ($d in $devices)
   {
   [PSObject]$deviceResult = createResultObject
   $deviceResult.DeviceId = $d.DeviceId
   $deviceResult.DeviceOSType = $d.DeviceOSType
   $deviceResult.DeviceOSVersion = $d.DeviceOSVersion
   $deviceResult.DeviceTrustLevel = $d.DeviceTrustLevel
   $deviceResult.DisplayName = $d.DisplayName
   $deviceResult.IsCompliant = $d.GraphDeviceObject.IsCompliant
   $deviceResult.IsManaged = $d.GraphDeviceObject.IsManaged
   $deviceResult.DeviceObjectId = $d.ObjectId
   $deviceResult.RegisteredOwnerUpn = $u.UserPrincipalName
   $deviceResult.RegisteredOwnerObjectId = $u.ObjectId
   $deviceResult.RegisteredOwnerDisplayName = $u.DisplayName
   $deviceResult.ApproximateLastLogonTimestamp = $d.ApproximateLastLogonTimestamp
   $deviceResult
   }
   }
   If ($export)
   {
   $result | Export-Csv -path ($exportPath + "\" + $exportFileName) -NoTypeInformation
   }
   Else
   {
   $result
   }
   ```

2. Zapisz plik jako plik Windows PowerShell, używając nazwy .ps1 pliku, na przykład Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Uruchamianie skryptu w celu uzyskania informacji o urządzeniu dla jednego konta użytkownika

1. Otwórz moduł Microsoft Azure Active Directory dla Windows PowerShell.

2. Przejdź do folderu, w którym został zapisany skrypt. Jeśli na przykład plik został zapisany w folderze C:\PS-Scripts, uruchom następujące polecenie.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Uruchom następujące polecenie w celu zidentyfikowania użytkownika, dla którego chcesz uzyskać szczegółowe informacje o urządzeniu. Ten przykład pobiera szczegółowe informacje dotyczące bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Uruchom następujące polecenie, aby zainicjować skrypt.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Informacje są eksportowane do twojego pulpitu Windows jako plik CSV. Możesz użyć dodatkowych parametrów, aby określić nazwę pliku i ścieżkę pliku CSV.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Uruchamianie skryptu w celu uzyskania informacji o urządzeniu dla grupy użytkowników

1. Otwórz moduł Microsoft Azure Active Directory dla Windows PowerShell.

2. Przejdź do folderu, w którym został zapisany skrypt. Jeśli na przykład plik został zapisany w folderze C:\PS-Scripts, uruchom następujące polecenie.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Uruchom następujące polecenie w celu zidentyfikowania grupy, dla której chcesz uzyskać szczegółowe informacje o urządzeniu. Ten przykład dotyczy użytkowników z grupy FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Uruchom następujące polecenie, aby zainicjować skrypt.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Informacje są eksportowane do twojego pulpitu Windows jako plik CSV. Możesz użyć dodatkowych parametrów, aby określić nazwę pliku i ścieżkę pliku CSV.

## <a name="related-topics"></a>Tematy pokrewne

[Aplikacja Microsoft Połączenie została wycofana](/collaborate/connect-redirect)

[Omówienie mobilności podstawowej i zabezpieczeń](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
