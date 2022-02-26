---
title: Wysoka dostępność uwierzytelniania federatora (etap 2) Konfigurowanie kontrolerów domeny
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Podsumowanie: Skonfiguruj kontrolery domeny i serwer synchronizacji katalogów na poziomie wysokiej dostępności federacji uwierzytelniania Microsoft 365 w Microsoft Azure.'
ms.openlocfilehash: 82199d6782e9c2497214d501da9e27ac0956edcd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973665"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Wysoka dostępność uwierzytelniania federegonowego Etap 2. Konfigurowanie kontrolerów domeny

W tym etapie wdrażania wysokiej dostępności na Microsoft 365 w usługach infrastruktury federniczej w usługach infrastruktury platformy Azure należy skonfigurować dwa kontrolery domeny i serwer synchronizacji katalogów w sieci wirtualnej azure. Żądania uwierzytelnienia klientów w sieci Web mogą być następnie uwierzytelniane w sieci wirtualnej azure zamiast wysyłać ruch uwierzytelniania przez połączenie vpn między witrynami do Twojej sieci lokalnej.
  
> [!NOTE]
> Usługi federatorów Active Directory (AD FS) nie mogą używać Azure Active Directory (Azure AD) jako zamiennika kontrolerów domeny Usługi domenowe w usłudze Active Directory (AD DS). 
  
Należy wykonać tę fazę przed przejściem do [fazy 3. Konfigurowanie serwerów usług AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Zobacz [Wdrażanie uwierzytelniania federacji o wysokiej dostępności Microsoft 365 na](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) platformie Azure, aby uzyskać informacje o wszystkich fazach.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Tworzenie maszyn wirtualnych kontrolera domeny na platformie Azure

Najpierw wypełnij kolumnę Nazwa maszyny wirtualnej  w tabeli M i zmodyfikuj rozmiary maszyn wirtualnych zgodnie z potrzebami w **kolumnie Minimalny rozmiar**.
  
|**Element**|**Nazwa maszyny wirtualnej**|**Obraz galerii**|**Storage typ**|**Minimalny rozmiar**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (pierwszy kontroler domeny, przykład DC1)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (drugi kontroler domeny, przykład DC2)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (serwer synchronizacji katalogów, przykład DS1)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (pierwszy serwer usług AD FS, przykład ADFS1)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (drugi serwer usług AD FS, przykład ADFS2)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (pierwszy serwer proxy aplikacji sieci Web, przykład WEB1)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![wiersz.](../media/Common-Images/TableLine.png) (drugi serwer proxy aplikacji sieci Web, przykład WEB2)  <br/> |Windows Server 2016 Centrum danych  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tabela M — maszyny wirtualne w celu uwierzytelniania feder sądowego o wysokiej dostępności Microsoft 365 na platformie Azure**
  
Aby uzyskać pełną listę rozmiarów maszyn wirtualnych, zobacz [Rozmiary maszyn wirtualnych](/azure/virtual-machines/virtual-machines-windows-sizes).
  
Poniższy Azure PowerShell tworzy maszyny wirtualne dla dwóch kontrolerów domeny. Określ wartości zmiennych, usuwając \< and > znaki. Zwróć uwagę, że Azure PowerShell blok poleceń używa wartości z następujących tabel:
  
- Tabela M dla Twoich maszyn wirtualnych
    
- Tabela R dla grup zasobów
    
- Tabela V dla ustawień sieci wirtualnej
    
- Tabela S dla podsieci
    
- Tabela I dla statycznych adresów IP
    
- Tabela A dla Twoich zestawów dostępności
    
Przypomnijmy, że tabele R, V, S, I i A zostały zdefiniowane w [fazie 1. Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> W poniższych zestawach poleceń jest dostępna najnowsza wersja Azure PowerShell. Zobacz [Wprowadzenie do Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Po poprawność podanych wartości uruchom blok wynikowy w wierszu polecenia programu Azure PowerShell lub w środowisku PowerShell Integrated Script Environment (ISE) na komputerze lokalnym.
  
> [!TIP]
> Aby wygenerować gotowe bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego skoroszytu [Microsoft Excel konfiguracji](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Ponieważ te maszyny wirtualne są przeznaczone do aplikacji intranetowej, nie mają przypisanego publicznego adresu IP ani etykiety nazwy domeny DNS i są dostępne w Internecie. Oznacza to jednak również, że nie można się z nimi połączyć z portalu Azure Portal. Ta **Połączenie** niedostępna podczas wyświetlania właściwości maszyny wirtualnej. Użyj akcesorium podłączania pulpitu zdalnego lub innego narzędzia pulpitu zdalnego, aby połączyć się z maszyną wirtualną przy użyciu jej prywatnego adresu IP lub intranetowej nazwy DNS.
  
## <a name="configure-the-first-domain-controller"></a>Konfigurowanie pierwszego kontrolera domeny

Użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego z pierwszą maszyną wirtualną kontrolera domeny. Użyj intranetowego systemu DNS lub nazwy komputera i poświadczeń konta administratora lokalnego.
  
Następnie dodaj dodatkowy dysk danych do pierwszego kontrolera domeny za pomocą tego polecenia z wiersza polecenia Windows PowerShell **na pierwszej maszynie wirtualnej kontrolera domeny**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Następnie przetestuj łączność pierwszego kontrolera domeny z lokalizacjami w sieci Twojej organizacji, używając polecenia **ping** w celu żądania ping nazw i adresów IP zasobów w sieci Twojej organizacji.
  
Ta procedura gwarantuje, że rozpoznawanie nazw DNS działa prawidłowo (że maszynę wirtualną poprawnie skonfigurowano z lokalnymi serwerami DNS) oraz że pakiety mogą być wysyłane do i z lokalnej sieci wirtualnej. Jeśli ten podstawowy test zakończy się niepowodzeniem, skontaktuj się ze swoim działem IT, aby rozwiązać problemy z rozpoznawaniem nazw DNS i dostarczaniem pakietów.
  
Następnie z poziomu wiersza Windows PowerShell na pierwszym kontrolerze domeny uruchom następujące polecenia:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

Zostanie wyświetlony monit o podaniem poświadczeń konta administratora domeny. Komputer zostanie uruchomiony ponownie.
  
## <a name="configure-the-second-domain-controller"></a>Konfigurowanie drugiego kontrolera domeny

Użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego z drugą maszyną wirtualną kontrolera domeny. Użyj intranetowego systemu DNS lub nazwy komputera i poświadczeń konta administratora lokalnego.
  
Następnie musisz dodać dodatkowy dysk danych do drugiego kontrolera domeny za pomocą tego polecenia z wiersza polecenia Windows PowerShell **na drugiej maszyny wirtualnej kontrolera domeny**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Następnie uruchom następujące polecenia:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

Zostanie wyświetlony monit o podaniem poświadczeń konta administratora domeny. Komputer zostanie uruchomiony ponownie.
  
Następnie musisz zaktualizować serwery DNS dla swojej sieci wirtualnej, tak aby platforma Azure przypisała maszyn wirtualnych adresy IP dwóch nowych kontrolerów domeny do używania jako ich serwerów DNS. Wypełnij zmienne, a następnie uruchom następujące polecenia z wiersza Windows PowerShell polecenia na komputerze lokalnym:
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

Pamiętaj, że uruchamiamy ponownie dwa kontrolery domeny, aby nie były skonfigurowane z lokalnymi serwerami DNS jako serwerami DNS. Oba serwery DNS zostały automatycznie skonfigurowane jako lokalne serwery DNS jako serwery przesyłania dalej DNS, gdy zostały promowane do kontrolerów domeny.
  
Następnie musimy utworzyć witrynę replikacji usługi Active Directory, aby zapewnić, że serwery w sieci wirtualnej Azure używają lokalnych kontrolerów domeny. Połączenie kontrolerze domeny przy użyciu konta administratora domeny i uruchom następujące polecenia z poziomu administratora w Windows PowerShell monitu:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Konfigurowanie serwera synchronizacji katalogów

Użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego z maszyną wirtualną serwera synchronizacji katalogów. Użyj intranetowego systemu DNS lub nazwy komputera i poświadczeń konta administratora lokalnego.
  
Następnie dołącz go do odpowiedniej domeny AD DS za pomocą tych poleceń w wierszu Windows PowerShell wiersza polecenia.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Oto konfiguracja wynikowa pomyślnego ukończenia tego etapu z symbolami zastępczymi nazw komputerów.
  
**Etap 2. Kontrolery domeny i serwer synchronizacji katalogów dla infrastruktury uwierzytelniania federacji o wysokiej dostępności na platformie Azure**

![Etap 2. wysokiej dostępności infrastruktury Microsoft 365 uwierzytelniania feder sądowego na platformie Azure z kontrolerami domen.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Następny krok

Etap [3. Konfigurowanie serwerów usług AD FS w](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) celu kontynuowania konfigurowania tego obciążenia pracą.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federacji o wysokiej dostępności Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla Twojego Microsoft 365 deweloper/środowisko testowe](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 rozwiązania i architektury](../solutions/index.yml)