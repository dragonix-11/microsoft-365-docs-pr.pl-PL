---
title: Wysoka dostępność uwierzytelniania federegonowego (etap 4) Konfigurowanie serwerów proxy aplikacji sieci Web
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Podsumowanie: Skonfiguruj serwery proxy aplikacji sieci Web pod celu skonfigurowania wysokiej dostępności federacji uwierzytelniania Microsoft 365 serwera Microsoft Azure.'
ms.openlocfilehash: ea50a48fe4bebd997ecf6b472a60e57772bf2b0f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986591"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Wysoka dostępność uwierzytelniania federegonowego Etap 4. Konfigurowanie serwerów proxy aplikacji sieci Web

W tym etapie wdrażania wysokiej dostępności na Microsoft 365 w usługach infrastruktury federacji platformy Azure należy utworzyć wewnętrzny równoważenie obciążenia i dwa serwery usług AD FS.
  
Należy wykonać tę fazę przed przejściem do fazy [5. Konfigurowanie uwierzytelniania federeracyjną dla Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Zobacz [Wdrażanie uwierzytelniania feder](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) służącego do wysokiej dostępności Microsoft 365 na platformie Azure, aby uzyskać informacje o wszystkich fazach.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Tworzenie narzędzia do równoważenia obciążenia skierowanego do Internetu na platformie Azure

Należy utworzyć narzędzie do równoważenia obciążenia skierowane do Internetu, aby usługa Azure równomiernie rozsyłała ruch uwierzytelniania klienta przychodzącego z Internetu między dwoma serwerami proxy aplikacji sieci Web.
  
> [!NOTE]
> W poniższych zestawach poleceń jest dostępna najnowsza wersja Azure PowerShell. Zobacz [Wprowadzenie do Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Po po w źródłach wartości lokalizacji i grupy zasobów uruchom blok wynikowy w wierszu polecenia programu Azure PowerShell lub w programie PowerShell ISE.
  
> [!TIP]
> Aby wygenerować gotowe bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego Microsoft Excel [konfiguracji programu PowerShell](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

Aby wyświetlić publiczny adres IP przypisany do urządzenia do równoważenia obciążenia dostępnego w Internecie, uruchom następujące polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Określanie nazwy FQDN usługi federowej i tworzenie rekordów DNS

Należy określić nazwę DNS do identyfikowania nazwy usługi federejnej w Internecie. Usługa Azure AD Połączenie skonfiguruje aplikację Microsoft 365 o tej nazwie w fazie 5, która stanie się częścią adresu URL wysyłanego przez usługę Microsoft 365 do łączenia klientów w celu uzyskania tokenu zabezpieczającego. Przykładem jest fs.contoso.com (fs to usługa federska).
  
Po utworzeniu nazwy FDQN usługi federskiej utwórz publiczną domenę DNS Rekord FDQN usługi federskiej, który będzie rozpoznawczy publiczny adres IP narzędzia do równoważenia obciążenia skierowanego do Internetu platformy Azure.
  
|**Name (Nazwa)**|**Type (Typ)**|**TTL (Czas wygaśnięcia)**|**Wartość**|
|:-----|:-----|:-----|:-----|
|FDQN usługi federskiej  <br/> |A  <br/> |3600  <br/> |publiczny adres IP narzędzia do równoważenia obciążenia skierowanego do Internetu platformy Azure (wyświetlany za pomocą polecenia **Write-Host** w poprzedniej sekcji) <br/> |
   
Oto przykład:
  
|**Name (Nazwa)**|**Type (Typ)**|**TTL (Czas wygaśnięcia)**|**Wartość**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Następnie dodaj rekord adresu DNS do prywatnej przestrzeni nazw DNS Twojej organizacji, rozpoznawczy nazwę FQDN Twojej usługi federrskiej do prywatnego adresu IP przypisanego do wewnętrznego równoważenia obciążenia serwerów usług AD FS (tabela I, element 4, kolumna wartości).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Tworzenie maszyn wirtualnych serwera proxy aplikacji sieci Web na platformie Azure

Użyj następującego bloku poleceń Azure PowerShell, aby utworzyć maszyny wirtualne dla dwóch serwerów proxy aplikacji sieci Web. 
  
Należy zauważyć, że w Azure PowerShell zestawów poleceń są używać wartości z następujących tabel:
  
- Tabela M dla Twoich maszyn wirtualnych
    
- Tabela R dla grup zasobów
    
- Tabela V dla ustawień sieci wirtualnej
    
- Tabela S dla podsieci
    
- Tabela I dla statycznych adresów IP
    
- Tabela A dla Twoich zestawów dostępności
    
Przypomnijmy, że zdefiniowano tabelę M w fazie [2.](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) Konfigurowanie kontrolerów domeny oraz tabel R, V, S, I i A w etapie [1. Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Po pojęniu wszystkich odpowiednich wartości uruchom blok wynikowy w wierszu polecenia programu Azure PowerShell lub w programie PowerShell ISE.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Ponieważ te maszyny wirtualne są przeznaczone do aplikacji intranetowej, nie mają przypisanego publicznego adresu IP ani etykiety nazwy domeny DNS i są dostępne w Internecie. Oznacza to jednak również, że nie można się z nimi połączyć z portalu Azure Portal. Ta **Połączenie** jest niedostępna podczas wyświetlania właściwości maszyny wirtualnej. Użyj akcesorium podłączania pulpitu zdalnego lub innego narzędzia Pulpit zdalny, aby połączyć się z maszyną wirtualną przy użyciu jej prywatnego adresu IP lub intranetowej nazwy DNS i poświadczeń konta administratora lokalnego.
  
Oto konfiguracja wynikowa pomyślnego ukończenia tego etapu z symbolami zastępczymi nazw komputerów.
  
**Etap 4. Skierowane do Internetu serwery proxy aplikacji sieci Web i równoważenia obciążenia dla infrastruktury uwierzytelniania federacji o wysokiej dostępności na platformie Azure**

![Etap 4. wysokiej dostępności infrastruktury Microsoft 365 uwierzytelniania feder służącego do uwierzytelniania na platformie Azure z serwerami proxy aplikacji sieci Web.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Następny krok

Etap [5. Konfigurowanie uwierzytelniania federatora Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) kontynuowania konfigurowania tego obciążenia pracą.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federeracyjnie o wysokiej dostępności Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla Twojego Microsoft 365 deweloper/środowisko testowania](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 rozwiązania i architektury](../solutions/index.yml)