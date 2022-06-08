---
title: Uwierzytelnianie federacyjne o wysokiej dostępności — faza 2. Konfigurowanie kontrolerów domeny
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Skonfiguruj kontrolery domeny i serwer synchronizacji katalogów pod kątem uwierzytelniania federacyjnego o wysokiej dostępności dla platformy Microsoft 365 na platformie Microsoft Azure.'
ms.openlocfilehash: 765ccb0aaf2611947f505b53b5689009dadd5148
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940695"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Uwierzytelnianie federacyjne o wysokiej dostępności — faza 2: konfigurowanie kontrolerów domeny

W tej fazie wdrażania wysokiej dostępności uwierzytelniania federacyjnego platformy Microsoft 365 w usługach infrastruktury platformy Azure skonfigurujesz dwa kontrolery domeny i serwer synchronizacji katalogów w sieci wirtualnej platformy Azure. Żądania sieci Web klienta dotyczące uwierzytelniania można następnie uwierzytelniać w sieci wirtualnej platformy Azure, zamiast wysyłać ten ruch uwierzytelniania przez połączenie sieci VPN typu lokacja-lokacja do sieci lokalnej.
  
> [!NOTE]
> Usługi Active Directory Federation Services (AD FS) nie mogą używać usługi Azure Active Directory (Azure AD) jako substytutu kontrolerów domeny usług Active Directory Domain Services (AD DS). 
  
Należy ukończyć tę fazę przed przejściem do [fazy 3: Konfigurowanie serwerów usług AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Zobacz [Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla platformy Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) , aby zapoznać się ze wszystkimi fazami.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Tworzenie maszyn wirtualnych kontrolera domeny na platformie Azure

Najpierw należy wypełnić kolumnę **Nazwa maszyny wirtualnej** tabeli M i zmodyfikować rozmiary maszyn wirtualnych zgodnie z potrzebami w kolumnie **Minimalny rozmiar** .
  
|**Element**|**Nazwa maszyny wirtualnej**|**Obraz galerii**|**Typ magazynu**|**Minimalny rozmiar**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (pierwszy kontroler domeny, przykład DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (drugi kontroler domeny, przykład DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (serwer synchronizacji katalogów, przykład DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (pierwszy serwer usług AD FS, przykład ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (drugi serwer usług AD FS, przykład ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (pierwszy serwer proxy aplikacji internetowej, przykład WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![Linii.](../media/Common-Images/TableLine.png) (drugi serwer proxy aplikacji internetowej, przykład WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tabela M — maszyny wirtualne do uwierzytelniania federacyjnego o wysokiej dostępności dla platformy Microsoft 365 na platformie Azure**
  
Aby uzyskać pełną listę rozmiarów maszyn wirtualnych, zobacz [Rozmiary maszyn wirtualnych](/azure/virtual-machines/sizes).
  
Poniższy blok poleceń programu Azure PowerShell tworzy maszyny wirtualne dla dwóch kontrolerów domeny. Określ wartości zmiennych, usuwając \< and > znaki. Należy pamiętać, że ten blok poleceń programu Azure PowerShell używa wartości z następujących tabel:
  
- Tabela M dla maszyn wirtualnych
    
- Tabela R dla grup zasobów
    
- Tabela V dla ustawień sieci wirtualnej
    
- Tabela S dla podsieci
    
- Tabela I dla statycznych adresów IP
    
- Tabela A dla zestawów dostępności
    
Pamiętaj, że w [fazie 1: Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md) zdefiniowano tabele R, V, S, I i A.
  
> [!NOTE]
> Poniższe zestawy poleceń używają najnowszej wersji programu Azure PowerShell. Zobacz [Wprowadzenie do programu Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Po podaniu wszystkich prawidłowych wartości uruchom wynikowy blok w wierszu polecenia programu Azure PowerShell lub w zintegrowanym środowisku skryptów programu PowerShell (ISE) na komputerze lokalnym.
  
> [!TIP]
> Aby wygenerować gotowe do uruchomienia bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego [skoroszytu konfiguracji programu Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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
> Ponieważ te maszyny wirtualne są przeznaczone dla aplikacji intranetowej, nie mają przypisanego publicznego adresu IP ani etykiety nazwy domeny DNS i nie są uwidocznione w Internecie. Oznacza to jednak również, że nie można nawiązać z nimi połączenia z poziomu witryny Azure Portal. Opcja **Połącz** jest niedostępna w przypadku wyświetlania właściwości maszyny wirtualnej. Użyj akcesorium Podłączanie pulpitu zdalnego lub innego narzędzia pulpitu zdalnego, aby nawiązać połączenie z maszyną wirtualną przy użyciu jej prywatnego adresu IP lub intranetowej nazwy DNS.
  
## <a name="configure-the-first-domain-controller"></a>Konfigurowanie pierwszego kontrolera domeny

Użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego z pierwszą maszyną wirtualną kontrolera domeny. Użyj intranetowej nazwy DNS lub komputera oraz poświadczeń konta administratora lokalnego.
  
Następnie dodaj dodatkowy dysk danych do pierwszego kontrolera domeny za pomocą tego polecenia z wiersza polecenia programu Windows PowerShell **na pierwszej maszynie wirtualnej kontrolera domeny**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Następnie przetestuj łączność pierwszego kontrolera domeny z lokalizacjami w sieci organizacji przy użyciu polecenia **ping** do pingowania nazw i adresów IP zasobów w sieci organizacji.
  
Ta procedura gwarantuje, że rozpoznawanie nazw DNS działa poprawnie (że maszyna wirtualna jest poprawnie skonfigurowana z lokalnymi serwerami DNS) oraz że pakiety mogą być wysyłane do i z sieci wirtualnej między środowiskami. Jeśli ten podstawowy test zakończy się niepowodzeniem, skontaktuj się z działem IT, aby rozwiązać problemy z rozpoznawaniem nazw DNS i dostarczaniem pakietów.
  
Następnie w wierszu polecenia programu Windows PowerShell na pierwszym kontrolerze domeny uruchom następujące polecenia:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

Zostanie wyświetlony monit o podanie poświadczeń konta administratora domeny. Komputer zostanie ponownie uruchomiony.
  
## <a name="configure-the-second-domain-controller"></a>Konfigurowanie drugiego kontrolera domeny

Użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego z drugą maszyną wirtualną kontrolera domeny. Użyj intranetowej nazwy DNS lub komputera oraz poświadczeń konta administratora lokalnego.
  
Następnie należy dodać dodatkowy dysk danych do drugiego kontrolera domeny za pomocą tego polecenia z wiersza polecenia programu Windows PowerShell **na drugiej maszynie wirtualnej kontrolera domeny**:
  
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

Zostanie wyświetlony monit o podanie poświadczeń konta administratora domeny. Komputer zostanie ponownie uruchomiony.
  
Następnie należy zaktualizować serwery DNS dla sieci wirtualnej, aby platforma Azure przypisywać maszynom wirtualnym adresy IP dwóch nowych kontrolerów domeny do użycia jako serwery DNS. Wypełnij zmienne, a następnie uruchom następujące polecenia z poziomu wiersza polecenia programu Windows PowerShell na komputerze lokalnym:
  
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

Należy pamiętać, że uruchamiamy ponownie dwa kontrolery domeny, aby nie były skonfigurowane z lokalnymi serwerami DNS jako serwerami DNS. Ponieważ oba są serwerami DNS, zostały one automatycznie skonfigurowane przy użyciu lokalnych serwerów DNS jako usługi przesyłania dalej DNS, gdy zostały one awansowane do kontrolerów domeny.
  
Następnie musimy utworzyć lokację replikacji usługi Active Directory, aby upewnić się, że serwery w sieci wirtualnej platformy Azure korzystają z lokalnych kontrolerów domeny. Połącz się z kontrolerem domeny przy użyciu konta administratora domeny i uruchom następujące polecenia z poziomu administratora wiersza polecenia programu Windows PowerShell:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Konfigurowanie serwera synchronizacji katalogów

Użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego z maszyną wirtualną serwera synchronizacji katalogów. Użyj intranetowej nazwy DNS lub komputera oraz poświadczeń konta administratora lokalnego.
  
Następnie dołącz go do odpowiedniej domeny usług AD DS za pomocą tych poleceń w wierszu polecenia programu Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Oto konfiguracja wynikająca z pomyślnego zakończenia tej fazy z nazwami komputerów zastępczych.
  
**Faza 2. Kontrolery domeny i serwer synchronizacji katalogów dla infrastruktury uwierzytelniania federacyjnego o wysokiej dostępności na platformie Azure**

![Faza 2 infrastruktury uwierzytelniania federacyjnego platformy Microsoft 365 o wysokiej dostępności na platformie Azure z kontrolerami domeny.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Następny krok

Użyj [fazy 3: skonfiguruj serwery usług AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) , aby kontynuować konfigurowanie tego obciążenia.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla platformy Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla środowiska deweloperskiego/testowego platformy Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)