---
title: Wysoka dostępność uwierzytelniania federegonowego (etap 3) Konfigurowanie serwerów usług AD FS
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: Dowiedz się, jak tworzyć i konfigurować serwery usług AD FS na poziomie wysokiej dostępności uwierzytelniania feder służącego do Microsoft 365 usług Microsoft Azure.
ms.openlocfilehash: c26fc68aa382ce93c62b6edbce4040b7e0813474
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988405"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>Wysoka dostępność uwierzytelniania federacji Etap 3. Konfigurowanie serwerów usług AD FS

W tym etapie wdrażania wysokiej dostępności na Microsoft 365 w usługach infrastruktury federacji platformy Azure należy utworzyć wewnętrzny równoważenie obciążenia i dwa serwery usług AD FS.
  
Należy wykonać tę fazę przed przejściem do [fazy 4. Konfigurowanie serwerów proxy aplikacji sieci Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Zobacz [Wdrażanie uwierzytelniania feder](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) służącego do wysokiej dostępności Microsoft 365 na platformie Azure, aby uzyskać informacje o wszystkich fazach.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>Tworzenie maszyn wirtualnych serwera usług AD FS na platformie Azure

Użyj następującego bloku poleceń programu PowerShell, aby utworzyć maszyny wirtualne dla dwóch serwerów usług AD FS. W tym zestawie poleceń programu PowerShell są używane wartości z następujących tabel:
  
- Tabela M dla Twoich maszyn wirtualnych
    
- Tabela R dla grup zasobów
    
- Tabela V dla ustawień sieci wirtualnej
    
- Tabela S dla podsieci
    
- Tabela I dla statycznych adresów IP
    
- Tabela A dla Twoich zestawów dostępności
    
Przypomnijmy, że zdefiniowano tabelę M w fazie [2.](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) Konfigurowanie kontrolerów domeny oraz tabel R, V, S, I i A w etapie [1. Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> W poniższych zestawach poleceń jest dostępna najnowsza wersja Azure PowerShell. Zobacz [Wprowadzenie do Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Najpierw należy utworzyć wewnętrzny równoważenie obciążenia platformy Azure dla dwóch serwerów usług AD FS. Określ wartości zmiennych, usuwając \< and > znaki. Po pojęniu wszystkich odpowiednich wartości uruchom blok wynikowy w wierszu polecenia programu Azure PowerShell lub w programie PowerShell ISE.
  
> [!TIP]
> Aby wygenerować gotowe bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego Microsoft Excel [konfiguracji programu PowerShell](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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
  
Po pojęniu wszystkich odpowiednich wartości uruchom blok wynikowy w wierszu polecenia programu Azure PowerShell lub w programie PowerShell ISE.
  
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
> Ponieważ te maszyny wirtualne są przeznaczone do aplikacji intranetowej, nie mają przypisanego publicznego adresu IP ani etykiety nazwy domeny DNS i są dostępne w Internecie. Oznacza to jednak również, że nie można się z nimi połączyć z portalu Azure Portal. Ta **Połączenie** jest niedostępna podczas wyświetlania właściwości maszyny wirtualnej. Użyj akcesorium podłączania pulpitu zdalnego lub innego narzędzia pulpitu zdalnego, aby połączyć się z maszyną wirtualną przy użyciu jej prywatnego adresu IP lub intranetowej nazwy DNS.
  
Dla każdej maszyny wirtualnej użyj wybranego klienta pulpitu zdalnego i utwórz połączenie pulpitu zdalnego. Użyj intranetowego systemu DNS lub nazwy komputera i poświadczeń konta administratora lokalnego.
  
Dla każdej maszyny wirtualnej dołącz je do odpowiedniej domeny Usługi domenowe w usłudze Active Directory (AD DS) za pomocą tych poleceń w wierszu Windows PowerShell wiersza polecenia.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Oto konfiguracja wynikowa pomyślnego ukończenia tego etapu z symbolami zastępczymi nazw komputerów.
  
**Etap 3. Serwery usług AD FS i wewnętrzny mechanizm równoważenia obciążenia dla twojej wysokiej dostępności infrastruktury uwierzytelniania federatora na platformie Azure**

![Etap 3 etapu wysokiej dostępności usługi Microsoft 365 federacji uwierzytelniania na platformie Azure z serwerami usług AD FS.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>Następny krok

Etap [4. Konfigurowanie serwerów proxy aplikacji sieci Web w](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) celu kontynuowania konfigurowania tego obciążenia pracą.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federeracyjnie o wysokiej dostępności Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla Twojego Microsoft 365 deweloper/środowisko testowania](federated-identity-for-your-microsoft-365-dev-test-environment.md)