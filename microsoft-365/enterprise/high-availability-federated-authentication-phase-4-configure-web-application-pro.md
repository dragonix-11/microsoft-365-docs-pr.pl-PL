---
title: Uwierzytelnianie federacyjne o wysokiej dostępności — faza 4. Konfigurowanie serwerów proxy aplikacji internetowych
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Podsumowanie: Skonfiguruj serwery proxy aplikacji internetowej pod kątem uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 w Microsoft Azure.'
ms.openlocfilehash: 2200d4f7c0aafbaff11dd5d9b5b5b414fae06b5f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091286"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Uwierzytelnianie federacyjne o wysokiej dostępności — faza 4: konfigurowanie serwerów proxy aplikacji internetowych

W tej fazie wdrażania wysokiej dostępności Microsoft 365 uwierzytelniania federacyjnego w usługach infrastruktury platformy Azure utworzysz wewnętrzny moduł równoważenia obciążenia i dwa serwery usług AD FS.
  
Należy ukończyć tę fazę przed przejściem do [fazy 5. Konfigurowanie uwierzytelniania federacyjnego dla Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Zobacz [Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) dla wszystkich faz.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Tworzenie modułu równoważenia obciążenia dostępnego z Internetu na platformie Azure

Musisz utworzyć moduł równoważenia obciążenia dostępny z Internetu, aby platforma Azure równomiernie rozdzielała przychodzący ruch uwierzytelniania klienta z Internetu między dwa serwery proxy aplikacji internetowej.
  
> [!NOTE]
> Poniższe zestawy poleceń używają najnowszej wersji Azure PowerShell. Zobacz [Wprowadzenie z Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Po podaniu wartości lokalizacji i grupy zasobów uruchom wynikowe bloki w wierszu polecenia Azure PowerShell lub w programie PowerShell ISE.
  
> [!TIP]
> Aby wygenerować gotowe do uruchomienia bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego [Microsoft Excel skoroszytu konfiguracji](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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

Aby wyświetlić publiczny adres IP przypisany do modułu równoważenia obciążenia dostępnego z Internetu, uruchom następujące polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Określanie nazwy FQDN usługi federacyjnej i tworzenie rekordów DNS

Musisz określić nazwę DNS, aby zidentyfikować nazwę usługi federacyjnej w Internecie. Usługa Azure AD Połączenie skonfiguruje Microsoft 365 o tej nazwie w fazie 5, która stanie się częścią adresu URL, który Microsoft 365 wysyła do klientów łączących się w celu uzyskania tokenu zabezpieczającego. Przykładem jest fs.contoso.com (fs oznacza usługę federacyjną).
  
Po utworzeniu nazwy FDQN usługi federacyjnej utwórz publiczną domenę DNS rekord A dla nazwy FDQN usługi federacyjnej, która jest rozpoznawana jako publiczny adres IP modułu równoważenia obciążenia dostępnego z Internetu na platformie Azure.
  
|**Name (Nazwa)**|**Type (Typ)**|**TTL (Czas wygaśnięcia)**|**Wartość**|
|:-----|:-----|:-----|:-----|
|nazwa FDQN usługi federacyjnej  <br/> |A  <br/> |3600  <br/> |publiczny adres IP modułu równoważenia obciążenia dostępnego z Internetu na platformie Azure (wyświetlany przez polecenie **Write-Host** w poprzedniej sekcji) <br/> |
   
Oto przykład:
  
|**Name (Nazwa)**|**Type (Typ)**|**TTL (Czas wygaśnięcia)**|**Wartość**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Następnie dodaj rekord adresu DNS do prywatnej przestrzeni nazw DNS organizacji, który rozpoznaje nazwę FQDN usługi federacyjnej jako prywatny adres IP przypisany do wewnętrznego modułu równoważenia obciążenia dla serwerów usług AD FS (tabela I, element 4, kolumna Wartość).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Tworzenie maszyn wirtualnych serwera proxy aplikacji internetowej na platformie Azure

Użyj następującego bloku poleceń Azure PowerShell, aby utworzyć maszyny wirtualne dla dwóch serwerów proxy aplikacji internetowej. 
  
Należy pamiętać, że następujące zestawy poleceń Azure PowerShell używają wartości z następujących tabel:
  
- Tabela M dla maszyn wirtualnych
    
- Tabela R dla grup zasobów
    
- Tabela V dla ustawień sieci wirtualnej
    
- Tabela S dla podsieci
    
- Tabela I dla statycznych adresów IP
    
- Tabela A dla zestawów dostępności
    
Pamiętaj, że tabela M została zdefiniowana w [fazie 2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) i tabel R, V, S, I i A w [fazie 1: konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Po podaniu wszystkich odpowiednich wartości uruchom wynikowe bloki w wierszu polecenia Azure PowerShell lub w programie PowerShell ISE.
  
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
> Ponieważ te maszyny wirtualne są przeznaczone dla aplikacji intranetowej, nie mają przypisanego publicznego adresu IP ani etykiety nazwy domeny DNS i nie są uwidocznione w Internecie. Jednak oznacza to również, że nie można nawiązać z nimi połączenia z Azure Portal. Opcja **Połączenie** jest niedostępna podczas wyświetlania właściwości maszyny wirtualnej. Użyj akcesorium Podłączanie pulpitu zdalnego lub innego narzędzia pulpitu zdalnego, aby nawiązać połączenie z maszyną wirtualną przy użyciu jej prywatnego adresu IP lub intranetowej nazwy DNS i poświadczeń konta administratora lokalnego.
  
Oto konfiguracja wynikająca z pomyślnego zakończenia tej fazy z nazwami komputerów zastępczych.
  
**Faza 4. Internetowy moduł równoważenia obciążenia i serwery proxy aplikacji internetowej dla infrastruktury uwierzytelniania federacyjnego o wysokiej dostępności na platformie Azure**

![Faza 4 wysokiej dostępności Microsoft 365 infrastruktury uwierzytelniania federacyjnego na platformie Azure z serwerami proxy aplikacji internetowej.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Następny krok

Użyj [fazy 5. Skonfiguruj uwierzytelnianie federacyjne dla Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md), aby kontynuować konfigurowanie tego obciążenia.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla środowiska deweloperskiego/testowego Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)