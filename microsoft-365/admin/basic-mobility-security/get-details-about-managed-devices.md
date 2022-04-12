---
title: Uzyskiwanie szczegółowych informacji o urządzeniach zarządzanych w usłudze Basic Mobility and Security
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
description: Użyj Windows PowerShell, aby uzyskać szczegółowe informacje o urządzeniach Usługi Basic Mobility and Security w organizacji.
ms.openlocfilehash: 4cac15e8377370e4bd2f8b359a39aaf830f13d10
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781078"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Uzyskiwanie szczegółowych informacji o urządzeniach zarządzanych w usłudze Basic Mobility and Security

W tym artykule przedstawiono sposób używania Windows PowerShell w celu uzyskania szczegółowych informacji o urządzeniach w organizacji skonfigurowanych dla usługi Basic Mobility and Security.

Poniżej przedstawiono podział szczegółów urządzenia dostępnych dla Ciebie.

|Szczegóły|Czego szukać w programie PowerShell|
|---|---|
|Urządzenie jest zarejestrowane w usłudze Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md)|Wartość parametru *isManaged* to:<br/>**True** = urządzenie jest zarejestrowane.<br/>**False** = urządzenie nie jest zarejestrowane.|
|Urządzenie jest zgodne z zasadami zabezpieczeń urządzeń. Aby uzyskać więcej informacji, zobacz [Tworzenie zasad zabezpieczeń urządzeń](create-device-security-policies.md)|Wartość parametru *isCompliant* to:<br/>**True** = urządzenie jest zgodne z zasadami.<br/>**False** = urządzenie nie jest zgodne z zasadami.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Podstawowe parametry programu PowerShell dotyczące mobilności i zabezpieczeń.":::

> [!NOTE]
> Polecenia i skrypty w tym artykule zwracają również szczegółowe informacje o wszystkich urządzeniach zarządzanych przez [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Istnieje kilka elementów, które należy skonfigurować do uruchamiania poleceń i skryptów opisanych w tym artykule.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Krok 1. Pobieranie i instalowanie modułu Azure Active Directory dla Windows PowerShell

Aby uzyskać więcej informacji na temat tych kroków, zobacz [Połączenie do Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. Przejdź do obszaru [Microsoft Online Services Sign-In Assistant for IT Professionals RTWl](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi) i wybierz pozycję **Pobierz dla Asystenta logowania usług online firmy Microsoft**.

2. Zainstaluj moduł Microsoft Azure Active Directory dla Windows PowerShell, wykonując następujące kroki:

    1. Otwórz wiersz polecenia programu PowerShell na poziomie administratora.

    2. `Install-Module MSOnline` Uruchom polecenie .

    3. Jeśli zostanie wyświetlony monit o zainstalowanie dostawcy NuGet, wpisz Y i naciśnij klawisz ENTER.

    4. Jeśli zostanie wyświetlony monit o zainstalowanie modułu z galerii PSGallery, wpisz Y i naciśnij klawisz ENTER.

    5. Po instalacji zamknij okno polecenia programu PowerShell.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Krok 2. Połączenie subskrypcji Microsoft 365

1. W module Windows Azure Active Directory dla Windows PowerShell uruchom następujące polecenie.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. W oknie dialogowym żądanie poświadczeń Windows PowerShell wpisz nazwę użytkownika i hasło dla konta administratora globalnego Microsoft 365, a następnie wybierz przycisk **OK**.

3. Uruchom następujące polecenie:

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Krok 3. Upewnij się, że możesz uruchamiać skrypty programu PowerShell

> [!NOTE]
> Możesz pominąć ten krok, jeśli masz już skonfigurowane uruchamianie skryptów programu PowerShell.

Aby uruchomić skrypt Get-MsolUserDeviceComplianceStatus.ps1, należy włączyć uruchamianie skryptów programu PowerShell.

1. W programie Windows Desktop wybierz pozycję **Start**, a następnie wpisz Windows PowerShell. Kliknij prawym przyciskiem myszy Windows PowerShell, a następnie wybierz pozycję **Uruchom jako administrator**.

2. Uruchom następujące polecenie:

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

3. Po wyświetleniu monitu wpisz Y, a następnie naciśnij klawisz Enter.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Uruchom polecenie cmdlet Get-MsolDevice, aby wyświetlić szczegóły dotyczące wszystkich urządzeń w organizacji

1. Otwórz moduł Microsoft Azure Active Directory dla Windows PowerShell.

2. Uruchom następujące polecenie:

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Aby uzyskać więcej przykładów, zobacz [Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

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

2. Zapisz go jako plik skryptu Windows PowerShell przy użyciu rozszerzenia pliku .ps1, na przykład Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Uruchom skrypt, aby uzyskać informacje o urządzeniu dla pojedynczego konta użytkownika

1. Otwórz moduł Microsoft Azure Active Directory dla Windows PowerShell.

2. Przejdź do folderu, w którym zapisano skrypt. Jeśli na przykład zapisano go w programie C:\PS-Scripts, uruchom następujące polecenie.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Uruchom następujące polecenie, aby zidentyfikować użytkownika, dla który chcesz uzyskać szczegółowe informacje o urządzeniu. W tym przykładzie są pobierane szczegółowe informacje dotyczące bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Uruchom następujące polecenie, aby zainicjować skrypt.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Informacje są eksportowane do programu Windows Desktop jako plik CSV. Możesz użyć dodatkowych parametrów, aby określić nazwę pliku i ścieżkę pliku CSV.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Uruchom skrypt, aby uzyskać informacje o urządzeniu dla grupy użytkowników

1. Otwórz moduł Microsoft Azure Active Directory dla Windows PowerShell.

2. Przejdź do folderu, w którym zapisano skrypt. Jeśli na przykład zapisano go w programie C:\PS-Scripts, uruchom następujące polecenie.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Uruchom następujące polecenie, aby zidentyfikować grupę, dla którą chcesz uzyskać szczegółowe informacje o urządzeniu. W tym przykładzie są pobierane szczegółowe informacje dla użytkowników w grupie FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Uruchom następujące polecenie, aby zainicjować skrypt.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Informacje są eksportowane do programu Windows Desktop jako plik CSV. Możesz użyć dodatkowych parametrów, aby określić nazwę pliku i ścieżkę pliku CSV.

## <a name="related-topics"></a>Tematy pokrewne

[Microsoft Połączenie został wycofany](/collaborate/connect-redirect)

[Omówienie funkcji Podstawowa mobilność i zabezpieczenia](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
