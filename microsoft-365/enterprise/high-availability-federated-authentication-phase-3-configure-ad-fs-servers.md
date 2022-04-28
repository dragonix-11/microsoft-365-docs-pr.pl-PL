---
title: Uwierzytelnianie federacyjne o wysokiej dostępności — faza 3— konfigurowanie serwerów usług AD FS
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: Dowiedz się, jak tworzyć i konfigurować serwery usług AD FS na potrzeby uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 w Microsoft Azure.
ms.openlocfilehash: ed0974c8286a5bbad083152d2e2f9aeb01f659df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101254"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>Uwierzytelnianie federacyjne o wysokiej dostępności — faza 3: konfigurowanie serwerów usług AD FS

W tej fazie wdrażania wysokiej dostępności Microsoft 365 uwierzytelniania federacyjnego w usługach infrastruktury platformy Azure utworzysz wewnętrzny moduł równoważenia obciążenia i dwa serwery usług AD FS.
  
Musisz ukończyć tę fazę przed przejściem do [fazy 4: Konfigurowanie serwerów proxy aplikacji internetowej](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Zobacz [Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) dla wszystkich faz.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>Tworzenie maszyn wirtualnych serwera usług AD FS na platformie Azure

Użyj następującego bloku poleceń programu PowerShell, aby utworzyć maszyny wirtualne dla dwóch serwerów usług AD FS. Ten zestaw poleceń programu PowerShell używa wartości z następujących tabel:
  
- Tabela M dla maszyn wirtualnych
    
- Tabela R dla grup zasobów
    
- Tabela V dla ustawień sieci wirtualnej
    
- Tabela S dla podsieci
    
- Tabela I dla statycznych adresów IP
    
- Tabela A dla zestawów dostępności
    
Pamiętaj, że tabela M została zdefiniowana w [fazie 2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) i tabel R, V, S, I i A w [fazie 1: konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Poniższe zestawy poleceń używają najnowszej wersji Azure PowerShell. Zobacz [Wprowadzenie z Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Najpierw należy utworzyć wewnętrzny moduł równoważenia obciążenia platformy Azure dla dwóch serwerów usług AD FS. Określ wartości zmiennych, usuwając \< and > znaki. Po podaniu wszystkich odpowiednich wartości uruchom wynikowe bloki w wierszu polecenia Azure PowerShell lub w programie PowerShell ISE.
  
> [!TIP]
> Aby wygenerować gotowe do uruchomienia bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego [Microsoft Excel skoroszytu konfiguracji](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

Następnie utwórz maszyny wirtualne serwera usług AD FS.
  
Po podaniu wszystkich odpowiednich wartości uruchom wynikowe bloki w wierszu polecenia Azure PowerShell lub w programie PowerShell ISE.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> Ponieważ te maszyny wirtualne są przeznaczone dla aplikacji intranetowej, nie mają przypisanego publicznego adresu IP ani etykiety nazwy domeny DNS i nie są uwidocznione w Internecie. Jednak oznacza to również, że nie można nawiązać z nimi połączenia z Azure Portal. Opcja **Połączenie** jest niedostępna podczas wyświetlania właściwości maszyny wirtualnej. Użyj akcesorium Podłączanie pulpitu zdalnego lub innego narzędzia pulpitu zdalnego, aby nawiązać połączenie z maszyną wirtualną przy użyciu jej prywatnego adresu IP lub intranetowej nazwy DNS.
  
Dla każdej maszyny wirtualnej użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego. Użyj intranetowej nazwy DNS lub komputera oraz poświadczeń konta administratora lokalnego.
  
Dla każdej maszyny wirtualnej dołącz je do odpowiedniej domeny Active Directory Domain Services (AD DS) za pomocą tych poleceń w wierszu Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Oto konfiguracja wynikająca z pomyślnego zakończenia tej fazy z nazwami komputerów zastępczych.
  
**Faza 3. Serwery usług AD FS i wewnętrzny moduł równoważenia obciążenia dla infrastruktury uwierzytelniania federacyjnego o wysokiej dostępności na platformie Azure**

![Faza 3 wysokiej dostępności Microsoft 365 infrastruktury uwierzytelniania federacyjnego na platformie Azure z serwerami usług AD FS.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>Następny krok

Użyj [fazy 4. Konfigurowanie serwerów proxy aplikacji internetowej](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) w celu kontynuowania konfigurowania tego obciążenia.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla środowiska deweloperskiego/testowego Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)