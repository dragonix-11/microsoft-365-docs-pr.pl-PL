---
title: Uwierzytelnianie federacyjne o wysokiej dostępności — faza 1 Konfigurowanie platformy Azure
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Podsumowanie: Skonfiguruj infrastrukturę Microsoft Azure do hostowania uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365.'
ms.openlocfilehash: f83aa494fcdead8f29810dea06193934b8ef26b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098389"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Uwierzytelnianie federacyjne o wysokiej dostępności — faza 1: konfigurowanie platformy Azure

W tej fazie utworzysz grupy zasobów, sieć wirtualną (VNet) i zestawy dostępności na platformie Azure, które będą hostem maszyn wirtualnych w fazach 2, 3 i 4. Należy ukończyć tę fazę przed przejściem do [fazy 2: Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Zobacz [Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) dla wszystkich faz.
  
Platforma Azure musi być aprowizowana przy użyciu następujących podstawowych składników:
  
- Grupy zasobów
    
- Sieć wirtualna platformy Azure z podsieciami obejmującymi maszyny wirtualne platformy Azure
    
- Sieciowe grupy zabezpieczeń do przeprowadzania izolacji podsieci
    
- Zestawy dostępności
    
## <a name="configure-azure-components"></a>Konfigurowanie składników platformy Azure

Przed rozpoczęciem konfigurowania składników platformy Azure wypełnij poniższe tabele. Aby ułatwić procedurę konfigurowania platformy Azure, wydrukuj tę sekcję i zapisz potrzebne informacje lub skopiuj tę sekcję do dokumentu i wypełnij ją. Aby uzyskać informacje o ustawieniach sieci wirtualnej, wypełnij tabelę V.
  
|**Element**|**Ustawienie konfiguracji**|**Opis**|**Wartość**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nazwa sieci wirtualnej  <br/> |Nazwa do przypisania do sieci wirtualnej (przykład FedAuthNet).  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Lokalizacja sieci wirtualnej  <br/> |Regionalne centrum danych platformy Azure, które będzie zawierać sieć wirtualną.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Adres IP urządzenia sieci VPN  <br/> |Publiczny adres IPv4 interfejsu urządzenia sieci VPN w Internecie.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Przestrzeń adresowa sieci wirtualnej  <br/> |Przestrzeń adresowa sieci wirtualnej. Skontaktuj się z działem IT, aby określić tę przestrzeń adresów.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Klucz udostępniony protokołu IPsec  <br/> |32-znakowy, alfanumeryczny ciąg, który będzie używany do uwierzytelniania obu stron połączenia sieci VPN typu lokacja-lokacja. Skontaktuj się z działem IT lub działu zabezpieczeń, aby określić tę wartość klucza. Alternatywnie zobacz [Create a random string for an IPsec preshared key (Tworzenie losowego ciągu dla klucza wstępnego udostępniania protokołu IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)).  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela V: konfiguracja między lokalnymi sieciami wirtualnymi**
  
Następnie wypełnij tabelę S dla podsieci tego rozwiązania. Wszystkie przestrzenie adresowe powinny być w formacie CIDR (Classless Interdomain Routing), znanym również jako format prefiksu sieci. Przykładem jest 10.24.64.0/20.
  
W przypadku pierwszych trzech podsieci określ nazwę i pojedynczą przestrzeń adresową IP na podstawie przestrzeni adresowej sieci wirtualnej. W podsieci bramy określ 27-bitową przestrzeń adresową (o długości prefiksu /27) dla podsieci bramy platformy Azure z następującymi elementami:
  
1. Ustaw zmienne bity w przestrzeni adresowej sieci wirtualnej na 1, do bitów używanych przez podsieć bramy, a następnie ustaw pozostałe bity na 0.
    
2. Przekonwertuj wynikowe bity na dziesiętne i wyświęć je jako przestrzeń adresową z długością prefiksu ustawioną na rozmiar podsieci bramy.
    
Zobacz [Kalkulator przestrzeni adresowej dla podsieci bramy platformy Azure](address-space-calculator-for-azure-gateway-subnets.md) dla bloku poleceń programu PowerShell oraz aplikacji konsolowej języka C# lub Python, która wykonuje to obliczenie za Ciebie.
  
Skontaktuj się z działem IT, aby określić te przestrzenie adresowe z przestrzeni adresowej sieci wirtualnej.
  
|**Element**|**Nazwa podsieci**|**Przestrzeń adresowa podsieci**|**Celu**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Podsieć używana przez kontroler domeny Active Directory Domain Services (AD DS) i maszyny wirtualne serwera synchronizacji katalogów.  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Podsieć używana przez maszyny wirtualne usług AD FS.  <br/> |
|3.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Podsieć używana przez maszyny wirtualne serwera proxy aplikacji internetowej.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Podsieć używana przez maszyny wirtualne bramy platformy Azure.  <br/> |
   
 **Tabela S: podsieci w sieci wirtualnej**
  
Następnie wypełnij tabelę I dla statycznych adresów IP przypisanych do maszyn wirtualnych i wystąpień modułu równoważenia obciążenia.
  
|**Element**|**Celu**|**Adres IP w podsieci**|**Wartość**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Statyczny adres IP pierwszego kontrolera domeny  <br/> |Czwarty możliwy adres IP dla przestrzeni adresowej podsieci zdefiniowanej w elemencie 1 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Statyczny adres IP drugiego kontrolera domeny  <br/> |Piąty możliwy adres IP dla przestrzeni adresowej podsieci zdefiniowanej w elemencie 1 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Statyczny adres IP serwera synchronizacji katalogów  <br/> |Szósty możliwy adres IP przestrzeni adresowej podsieci zdefiniowanej w elemencie 1 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Statyczny adres IP wewnętrznego modułu równoważenia obciążenia dla serwerów usług AD FS  <br/> |Czwarty możliwy adres IP dla przestrzeni adresowej podsieci zdefiniowanej w elemencie 2 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Statyczny adres IP pierwszego serwera usług AD FS  <br/> |Piąty możliwy adres IP przestrzeni adresowej podsieci zdefiniowanej w elemencie 2 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |Statyczny adres IP drugiego serwera usług AD FS  <br/> |Szósty możliwy adres IP przestrzeni adresowej podsieci zdefiniowanej w elemencie 2 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |Statyczny adres IP pierwszego serwera proxy aplikacji internetowej  <br/> |Czwarty możliwy adres IP dla przestrzeni adresowej podsieci zdefiniowanej w elemencie 3 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |Statyczny adres IP drugiego serwera proxy aplikacji internetowej  <br/> |Piąty możliwy adres IP przestrzeni adresowej podsieci zdefiniowanej w elemencie 3 tabeli S.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela I: statyczne adresy IP w sieci wirtualnej**
  
W przypadku dwóch serwerów systemu nazw domen (DNS) w sieci lokalnej, których chcesz użyć podczas początkowego konfigurowania kontrolerów domeny w sieci wirtualnej, wypełnij tabelę D. Skontaktuj się z działem IT, aby określić tę listę.
  
|**Element**|**Przyjazna nazwa serwera DNS**|**Adres IP serwera DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela D: Lokalne serwery DNS**
  
Aby kierować pakiety z sieci międzylokacyjnej do sieci organizacji przez połączenie sieci VPN typu lokacja-lokacja, należy skonfigurować sieć wirtualną z siecią lokalną zawierającą listę przestrzeni adresowych (w notacji CIDR) dla wszystkich dostępnych lokalizacji w sieci lokalnej organizacji. Lista przestrzeni adresowych definiujących sieć lokalną musi być unikatowa i nie może pokrywać się z przestrzenią adresową używaną w innych sieciach wirtualnych lub innych sieciach lokalnych.
  
W przypadku zestawu przestrzeni adresowych sieci lokalnej wypełnij tabelę L. Pamiętaj, że na liście znajdują się trzy puste wpisy, ale zazwyczaj potrzebujesz więcej. Skontaktuj się z działem IT, aby określić tę listę przestrzeni adresowych.
  
|**Element**|**Przestrzeń adresowa sieci lokalnej**|
|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela L: Prefiksy adresów dla sieci lokalnej**
  
Teraz zacznijmy tworzyć infrastrukturę platformy Azure do hostowania uwierzytelniania federacyjnego na potrzeby Microsoft 365.
  
> [!NOTE]
> Poniższe zestawy poleceń używają najnowszej wersji Azure PowerShell. Zobacz [Wprowadzenie z Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Najpierw uruchom Azure PowerShell monit i zaloguj się do swojego konta.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Aby wygenerować gotowe do uruchomienia bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego [Microsoft Excel skoroszytu konfiguracji](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

Pobierz nazwę subskrypcji przy użyciu następującego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

W przypadku starszych wersji Azure PowerShell użyj tego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Ustaw subskrypcję platformy Azure. Zastąp wszystkie elementy w cudzysłowie, w tym \< and > znaki, poprawną nazwą.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Następnie utwórz nowe grupy zasobów. Aby określić unikatowy zestaw nazw grup zasobów, użyj tego polecenia, aby wyświetlić listę istniejących grup zasobów.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

W poniższej tabeli podaj zestaw unikatowych nazw grup zasobów.
  
|**Element**|**Nazwa grupy zasobów**|**Celu**|
|:-----|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Kontrolery domeny  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Serwery usług AD FS  <br/> |
|3.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Serwery proxy aplikacji internetowej  <br/> |
|4.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Elementy infrastruktury  <br/> |
   
 **Tabela R: grupy zasobów**
  
Utwórz nowe grupy zasobów przy użyciu tych poleceń.
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Następnie utworzysz sieć wirtualną platformy Azure i jej podsieci.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Następnie utworzysz sieciowe grupy zabezpieczeń dla każdej podsieci, która ma maszyny wirtualne. Aby przeprowadzić izolację podsieci, można dodać reguły dla określonych typów ruchu dozwolonego lub niedozwolonego do sieciowej grupy zabezpieczeń podsieci.
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Następnie użyj tych poleceń, aby utworzyć bramy dla połączenia sieci VPN typu lokacja-lokacja.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Uwierzytelnianie federacyjne poszczególnych użytkowników nie opiera się na żadnych zasobach lokalnych. Jeśli jednak to połączenie sieci VPN typu lokacja-lokacja stanie się niedostępne, kontrolery domeny w sieci wirtualnej nie będą otrzymywać aktualizacji kont użytkowników i grup w usługach lokalna usługa Active Directory Domain Services. Aby upewnić się, że tak się nie stanie, można skonfigurować wysoką dostępność dla połączenia sieci VPN typu lokacja-lokacja. Aby uzyskać więcej informacji, zobacz [Highly Available Cross-Premises and VNet-to-VNet Connectivity (Łączność między sieciami wirtualnymi i między sieciami wirtualnymi](/azure/vpn-gateway/vpn-gateway-highlyavailable))
  
Następnie zapisz publiczny adres IPv4 bramy sieci VPN platformy Azure dla sieci wirtualnej z poziomu wyświetlania tego polecenia:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Następnie skonfiguruj lokalne urządzenie sieci VPN w celu nawiązania połączenia z bramą sieci VPN platformy Azure. Aby uzyskać więcej informacji, zobacz [Konfigurowanie urządzenia sieci VPN](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Do skonfigurowania lokalnego urządzenia sieci VPN potrzebne są następujące elementy:
  
- Publiczny adres IPv4 bramy sieci VPN platformy Azure.
    
- Klucz wstępny protokołu IPsec dla połączenia sieci VPN typu lokacja-lokacja (tabela V — element 5 — kolumna wartość).
    
Następnie upewnij się, że przestrzeń adresowa sieci wirtualnej jest osiągalna z sieci lokalnej. Zwykle odbywa się to przez dodanie trasy odpowiadającej przestrzeni adresowej sieci wirtualnej do urządzenia sieci VPN, a następnie reklamowanie tej trasy do pozostałej części infrastruktury routingu sieci organizacji. Skontaktuj się z działem IT, aby ustalić, jak to zrobić.
  
Następnie zdefiniuj nazwy trzech zestawów dostępności. Wypełnij tabelę A. 
  
|**Element**|**Celu**|**Nazwa zestawu dostępności**|
|:-----|:-----|:-----|
|1.  <br/> |Kontrolery domeny  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Serwery usług AD FS  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Serwery proxy aplikacji internetowej  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela A: zestawy dostępności**
  
Te nazwy będą potrzebne podczas tworzenia maszyn wirtualnych w fazach 2, 3 i 4.
  
Utwórz nowe zestawy dostępności przy użyciu tych poleceń Azure PowerShell.
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

Jest to konfiguracja wynikająca z pomyślnego ukończenia tej fazy.
  
**Faza 1. Infrastruktura platformy Azure na potrzeby uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365**

![Faza 1 wysokiej dostępności Microsoft 365 uwierzytelniania federacyjnego na platformie Azure z infrastrukturą platformy Azure.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Następny krok

Użyj [fazy 2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) w celu kontynuowania konfiguracji tego obciążenia.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla środowiska deweloperskiego/testowego Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)

[Omówienie modeli tożsamości Microsoft 365](deploy-identity-solution-identity-model.md)