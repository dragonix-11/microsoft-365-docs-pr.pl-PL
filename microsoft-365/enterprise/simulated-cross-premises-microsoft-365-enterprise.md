---
title: Symulowana krzyżowa sieć wirtualna w Microsoft 365 testowym
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: seo-marvel-apr2020
description: 'Podsumowanie: Utwórz symulowaną między siedzibą sieci wirtualnej w Microsoft Azure jako Microsoft 365 testowego.'
ms.openlocfilehash: 0d0e22b5c9a12f4757a6dff5892ef72a757d2bda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988011"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Symulowana krzyżowa sieć wirtualna w Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

Ten artykuł zawiera kroki tworzenia symulowanego hybrydowego środowiska chmury z Microsoft Azure przy użyciu dwóch sieci wirtualnych platformy Azure. Oto wynikowa konfiguracja. 
  
![Etap 3 symulowanego środowiska testowego wirtualnej sieci wirtualnej z maszyną wirtualną DC2 w XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Umożliwia to symulowanie hybrydowego środowiska produkcyjnego chmury usługi Azure IaaS i składa się z:
  
- Symulowana i uproszczona sieć lokalna hostowana w sieci wirtualnej platformy Azure (sieć wirtualna TestLab).
    
- Symulowana sieć wirtualna między siedzibą hostowana na platformie Azure (XPrem).
    
- Relacja komunikacji równorzędnej VNet między obiema sieciami wirtualnymi.
    
- Pomocniczy kontroler domeny w sieci wirtualnej XPrem.
    
Stanowi to podstawę i wspólny punkt wyjścia, od którego można: 
  
- Opracuj i testuj aplikacje w symulowanym środowisku hybrydowym usługi Azure IaaS w chmurze.
    
- Utwórz konfiguracje testowe komputerów, niektóre z sieci wirtualnej TestLab, a inne w sieci wirtualnej XPrem, aby symulować hybrydowe obciążenia it oparte na chmurze.
    
Istnieją trzy główne fazy konfigurowania tego środowiska testowego:
  
1. Skonfiguruj sieć wirtualną TestLab.
    
2. Utwórz lokalną sieć wirtualną.
    
3. Konfigurowanie dc2.
    
> [!NOTE]
> Ta konfiguracja wymaga płatnej subskrypcji platformy Azure. 

Za pomocą środowiska wynikowego można przetestować funkcje programu Microsoft 365 [przedsiębiorstwa](https://www.microsoft.com/microsoft-365/enterprise) za pomocą dodatkowych przewodników laboratorium testowego [](m365-enterprise-test-lab-guides.md) lub samodzielnie.

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Przejdź do [Microsoft 365 stos](../downloads/Microsoft365EnterpriseTLGStack.pdf) przewodników laboratorium testowego dla przedsiębiorstw, aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium Microsoft 365 dla przedsiębiorstw testowych.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>Etap 1. Konfigurowanie sieci wirtualnej TestLab

Skorzystaj z instrukcji z fazy **1** symulowanej konfiguracji [](simulated-ent-base-configuration-microsoft-365-enterprise.md) bazy przedsiębiorstwa, aby skonfigurować komputery DC1, APP1 i CLIENT1 w sieci wirtualnej platformy Azure o nazwie TestLab.
  
Jest to Twoja bieżąca konfiguracja. 
  
![Symulowana konfiguracja bazy przedsiębiorstwa na platformie Azure.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Etap 2. Tworzenie sieci wirtualnej XPrem

W tej fazie utworzysz i skonfigurujesz nową sieć wirtualną XPrem, a następnie połączysz ją z siecią wirtualną TestLab za pomocą komunikacji równorzędnej VNet.
  
Najpierw uruchom monit Azure PowerShell na komputerze lokalnym.
  
> [!NOTE]
> W poniższych zestawach poleceń jest dostępna najnowsza wersja Azure PowerShell. Zobacz [Wprowadzenie do Azure PowerShell cmdlet](/powershell/azureps-cmdlets-docs/). 
  
Zaloguj się do swojego konta Azure za pomocą tego polecenia.
  
```powershell
Connect-AzAccount
```

Uzyskaj nazwę subskrypcji za pomocą tego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Ustaw subskrypcję platformy Azure. Zamień wszystkie cudzysłowy, łącznie ze znakami \< and > , na poprawne nazwy.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Następnie utwórz sieć wirtualną XPrem i chroń ją za pomocą grupy zabezpieczeń sieciowych za pomocą tych poleceń.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Następnie należy utworzyć relację komunikacji równorzędnej VNet między programem TestLab i sieciami VNet XPrem za pomocą tych poleceń.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Jest to Twoja bieżąca konfiguracja. 
  
![Etap 2 symulowanego środowiska wirtualnego testowania sieci wirtualnej z siecią VNet XPrem i relacją komunikacji równorzędnej VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Etap 3. Konfigurowanie dc2

W tej fazie należy utworzyć maszynę wirtualną DC2 w sieci wirtualnej XPrem, a następnie skonfigurować ją jako replikę kontrolera domeny.
  
Najpierw utwórz maszynę wirtualną dla dc2. Uruchom te polecenia w wierszu Azure PowerShell polecenia na komputerze lokalnym.
  
```powershell
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Następnie połącz się z nową maszyną wirtualną DC2 z portalu [Azure,](https://portal.azure.com) używając jego nazwy konta administratora lokalnego i hasła.
  
Następnie skonfiguruj regułę zapory Windows sieciowej, aby zezwolić na ruch na testy łączności podstawowej. Uruchom te polecenia w wierszu Windows PowerShell wiersza polecenia na poziomie administratora w dniu DC2. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Polecenie ping powinno spowodować cztery udane odpowiedzi z adresu IP 10.0.0.4. Jest to test ruchu w relacji komunikacji równorzędnej VNet. 
  
Następnie dodaj dodatkowy dysk danych jako nowy wolumin z literą dysku F: przy użyciu tego polecenia z wiersza polecenia Windows PowerShell w dc2.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Następnie skonfiguruj dc2 jako replikę kontrolera domeny dla corp.contoso.com domeny. Uruchom te polecenia z wiersza Windows PowerShell wiersza polecenia w dc2.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Zwróć uwagę, że zostanie wyświetlony monit o podaniem hasła CORPUser1\\ i hasła trybu przywracania usług katalogowych (DSRM, Directory Restore Mode) oraz ponownego uruchomienia systemu DC2. 
  
Teraz, gdy sieć wirtualna XPrem ma własny serwer DNS (DC2), musisz skonfigurować sieć wirtualną XPrem, aby korzystać z tego serwera DNS. Uruchom te polecenia z Azure PowerShell wiersza polecenia na komputerze lokalnym.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Z portalu Azure na komputerze lokalnym połącz się z dc1 za pomocą poświadczeń CORPUser1\\. Aby skonfigurować domenę CORP tak, aby komputery i użytkownicy korzystali z lokalnego kontrolera domeny na Windows PowerShell uwierzytelniania, uruchom te polecenia z wiersza polecenia na poziomie administratora Windows PowerShell dc1.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Jest to Twoja bieżąca konfiguracja. 
  
![Etap 3 symulowanego środowiska testowego wirtualnej sieci wirtualnej z maszyną wirtualną DC2 w XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Symulowane środowisko hybrydowe platformy Azure w chmurze jest teraz gotowe do testowania.
  
Możesz teraz poeksperymentować z dodatkowymi funkcjami usługi [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tymi dodatkowymi zestawami przewodników laboratorium testowego:
  
- [Tożsamości](m365-enterprise-test-lab-guides.md#identity)
- [Zarządzanie urządzeniami przenośnymi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Ochrona informacji](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)