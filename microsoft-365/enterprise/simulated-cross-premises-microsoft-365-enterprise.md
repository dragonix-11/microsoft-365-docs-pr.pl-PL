---
title: Symulowana sieć wirtualna między lokalami w środowisku testowym Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Tworzenie symulowanej sieci wirtualnej między środowiskami lokalnymi w Microsoft Azure jako środowisko testowe Microsoft 365.'
ms.openlocfilehash: a3bc5c130ad03d1896abcf98ba9fc26d9ff2f422
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099174"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Symulowana sieć wirtualna między lokalami w środowisku testowym Microsoft 365

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

W tym artykule opisano proces tworzenia symulowanego środowiska chmury hybrydowej z Microsoft Azure przy użyciu dwóch sieci wirtualnych platformy Azure. Oto wynikowej konfiguracji. 
  
![Faza 3 symulowanego środowiska testowego między lokalnymi sieciami wirtualnymi z maszyną wirtualną DC2 w sieci wirtualnej XPrem.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Symuluje to środowisko produkcyjne chmury hybrydowej IaaS platformy Azure i składa się z następujących elementów:
  
- Symulowana i uproszczona sieć lokalna hostowana w sieci wirtualnej platformy Azure (sieci wirtualnej TestLab).
    
- Symulowana sieć wirtualna między lokalami hostowana na platformie Azure (XPrem).
    
- Relacja komunikacji równorzędnej między dwiema sieciami wirtualnymi.
    
- Pomocniczy kontroler domeny w sieci wirtualnej XPrem.
    
Stanowi to podstawę i wspólny punkt początkowy, z którego można: 
  
- Tworzenie i testowanie aplikacji w symulowanym środowisku chmury hybrydowej IaaS platformy Azure.
    
- Utwórz konfiguracje testowe komputerów, niektóre w sieci wirtualnej TestLab, a niektóre w sieci wirtualnej XPrem, aby symulować hybrydowe obciążenia IT oparte na chmurze.
    
Istnieją trzy główne fazy konfigurowania tego środowiska testowego:
  
1. Skonfiguruj sieć wirtualną TestLab.
    
2. Utwórz sieć wirtualną między środowiskami.
    
3. Skonfiguruj kontroler DC2.
    
> [!NOTE]
> Ta konfiguracja wymaga płatnej subskrypcji platformy Azure. 

Środowisko wynikowe umożliwia testowanie funkcji i funkcji [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/enterprise) przy użyciu dodatkowych [przewodników laboratorium testowego](m365-enterprise-test-lab-guides.md) lub samodzielnie.

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Przejdź do [Microsoft 365 dla stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf), aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 for enterprise Test Lab.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>Faza 1. Konfigurowanie sieci wirtualnej TestLab

Skorzystaj z instrukcji w **fazie 1** [symulowanej konfiguracji podstawowej przedsiębiorstwa](simulated-ent-base-configuration-microsoft-365-enterprise.md) , aby skonfigurować komputery DC1, APP1 i CLIENT1 w sieci wirtualnej platformy Azure o nazwie TestLab.
  
Jest to bieżąca konfiguracja. 
  
![Symulowana konfiguracja podstawowa przedsiębiorstwa na platformie Azure.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Faza 2. Tworzenie sieci wirtualnej XPrem

W tej fazie utworzysz i skonfigurujesz nową sieć wirtualną XPrem, a następnie połączysz ją z siecią wirtualną TestLab za pomocą komunikacji równorzędnej sieci wirtualnych.
  
Najpierw uruchom monit Azure PowerShell na komputerze lokalnym.
  
> [!NOTE]
> Poniższe zestawy poleceń używają najnowszej wersji Azure PowerShell. Zobacz [Wprowadzenie z poleceniami cmdlet Azure PowerShell](/powershell/azureps-cmdlets-docs/). 
  
Zaloguj się do konta platformy Azure za pomocą tego polecenia.
  
```powershell
Connect-AzAccount
```

Pobierz nazwę subskrypcji przy użyciu tego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Ustaw subskrypcję platformy Azure. Zastąp wszystkie elementy w cudzysłowie, w tym \< and > znaki, prawidłowymi nazwami.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Następnie utwórz sieć wirtualną XPrem i chroń ją za pomocą sieciowej grupy zabezpieczeń za pomocą tych poleceń.
  
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

Następnie utworzysz relację komunikacji równorzędnej sieci wirtualnych między sieciami wirtualnymi TestLab i XPrem za pomocą tych poleceń.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Jest to bieżąca konfiguracja. 
  
![Faza 2 symulowanego środowiska testowego między lokalnymi sieciami wirtualnymi z siecią wirtualną XPrem i relacją komunikacji równorzędnej sieci wirtualnej.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Faza 3. Konfigurowanie kontrolera DC2

W tej fazie utworzysz maszynę wirtualną DC2 w sieci wirtualnej XPrem, a następnie skonfigurujesz ją jako kontroler domeny repliki.
  
Najpierw utwórz maszynę wirtualną dla kontrolera DC2. Uruchom te polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym.
  
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

Następnie połącz się z nową maszyną wirtualną DC2 z [Azure Portal](https://portal.azure.com) przy użyciu nazwy konta administratora lokalnego i hasła.
  
Następnie skonfiguruj regułę zapory Windows, aby zezwolić na ruch na potrzeby podstawowego testowania łączności. W wierszu polecenia Windows PowerShell na poziomie administratora na kontrolerze DOMENY2 uruchom te polecenia. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Polecenie ping powinno spowodować cztery pomyślne odpowiedzi z adresu IP 10.0.0.4. Jest to test ruchu w relacji komunikacji równorzędnej sieci wirtualnych. 
  
Następnie dodaj dodatkowy dysk danych jako nowy wolumin z literą dysku F: za pomocą tego polecenia z wiersza polecenia Windows PowerShell w kontrolerze DC2.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Następnie skonfiguruj kontroler DOMENY DC2 jako kontroler domeny repliki dla domeny corp.contoso.com. Uruchom te polecenia w wierszu polecenia Windows PowerShell na kontrolerze DC2.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Należy pamiętać, że zostanie wyświetlony monit o podanie hasła CORPUser1\\ i hasła trybu przywracania usług katalogowych (DSRM) oraz ponowne uruchomienie kontrolera DC2. 
  
Teraz, gdy sieć wirtualna XPrem ma własny serwer DNS (DC2), należy skonfigurować sieć wirtualną XPrem do korzystania z tego serwera DNS. Uruchom te polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Z Azure Portal na komputerze lokalnym połącz się z kontrolerem DC1 przy użyciu poświadczeń CORPUser1\\. Aby skonfigurować domenę CORP tak, aby komputery i użytkownicy korzystali z lokalnego kontrolera domeny na potrzeby uwierzytelniania, uruchom te polecenia z poziomu administratora Windows PowerShell wiersza polecenia na kontrolerze DC1.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Jest to bieżąca konfiguracja. 
  
![Faza 3 symulowanego środowiska testowego między lokalnymi sieciami wirtualnymi z maszyną wirtualną DC2 w sieci wirtualnej XPrem.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Symulowane środowisko chmury hybrydowej platformy Azure jest teraz gotowe do testowania.
  
Teraz możesz eksperymentować z dodatkowymi funkcjami [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tymi dodatkowymi zestawami przewodników laboratorium testowego:
  
- [Tożsamości](m365-enterprise-test-lab-guides.md#identity)
- [Zarządzanie urządzeniami przenośnymi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Ochrona informacji](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)