---
title: Wysoka dostępność uwierzytelniania federegonowego (etap 1) Konfigurowanie platformy Azure
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Podsumowanie: skonfiguruj infrastrukturę Microsoft Azure, aby hostować uwierzytelnianie federowane o wysokiej dostępności dla Microsoft 365.'
ms.openlocfilehash: 35666baf98b45419f41a0078729ac5a5a6fab995
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013877"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Wysoka dostępność uwierzytelniania federeracyjna Etap 1. Konfigurowanie platformy Azure

W tej fazie utworzysz grupy zasobów, sieć wirtualną (VNet) i zestawy dostępności na platformie Azure, które będą hostować maszyny wirtualne w fazach 2, 3 i 4. Należy zakończyć ten etap przed przejściem do [fazy 2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Zobacz [Wdrażanie uwierzytelniania feder](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) służącego do wysokiej dostępności Microsoft 365 na platformie Azure, aby uzyskać informacje o wszystkich fazach.
  
Platforma Azure musi być aprowowana przy użyciu tych podstawowych składników:
  
- Grupy zasobów
    
- Sieć wirtualna platformy Azure (VNet) z podsieciami do hostowania maszyn wirtualnych platformy Azure
    
- Grupy zabezpieczeń sieci w celu wykonania izolacji podsieci
    
- Zestawy dostępności
    
## <a name="configure-azure-components"></a>Konfigurowanie składników platformy Azure

Przed rozpoczęciem konfigurowania składników platformy Azure wypełnij poniższe tabele. Aby pomóc w procedurach konfigurowania platformy Azure, wydrukuj tę sekcję i zanotuj wymagane informacje lub skopiuj tę sekcję do dokumentu i wypełnij ją. Aby uzyskać ustawienia sieci VNet, wpisz tabela V.
  
|**Element**|**Ustawienie konfiguracji**|**Opis**|**Wartość**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nazwa sieci VNet  <br/> |Nazwa do przypisania do sieci VNet (na przykład FedAuthNet).  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Lokalizacja sieci VNet  <br/> |Regionalne centrum danych platformy Azure, które będzie zawierać sieć wirtualną.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Adres IP urządzenia SIECI VPN  <br/> |Publiczny adres IPv4 interfejsu urządzenia VPN w Internecie.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |VNet address space  <br/> |Przestrzeń adresów dla sieci wirtualnej. We współpracy z działem IT ustal tę przestrzeń adresową.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Klucz udostępniony IPsec  <br/> |32-znakowy losowy ciąg alfanumeryczny używany do uwierzytelniania obu stron połączenia VPN między witrynami. We współpracy z działem IT lub działem zabezpieczeń ustalisz tę wartość klucza. Ewentualnie zobacz [Tworzenie ciągu losowego dla wstępnie](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx) współużytego klucza IPsec.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela V: Konfiguracja między lokalną siecią wirtualną**
  
Następnie wypełnij tabelę S, aby uzyskać informacje o podsieci tego rozwiązania. Wszystkie spacje adresów powinny mieć format Routing międzydomenami (CIDR, Classless Interdomain Routing), nazywany także formatem prefiksu sieciowego. Przykład: 10.24.64.0/20.
  
W przypadku pierwszych trzech podsieci określ nazwę i pojedynczą przestrzeń adresów IP na podstawie wirtualnej przestrzeni adresów sieciowych. Dla podsieci bramy określ 27-bitową przestrzeń adresową (o długości prefiksu /27) dla podsieci bramy platformy Azure z następującymi:
  
1. Ustaw bity zmiennych w przestrzeni adresów w net. VNet na 1 ( do bitów używanych przez podsieci bramy), a następnie dla pozostałych bitów ustaw wartość 0.
    
2. Przekonwertuj bity wynikowe na dziesiętne i wyraś je jako spację adresową o długości prefiksu ustawionej na rozmiar podsieci bramy.
    
Zobacz [Kalkulator przestrzeni adresów dla podsieci bramy platformy Azure](address-space-calculator-for-azure-gateway-subnets.md) dla bloku poleceń programu PowerShell i aplikacji konsoli języka C# lub Python, która wykonuje to obliczenie za Ciebie.
  
We współpracy z działem IT ustal te odstępy między adresami od wirtualnej przestrzeni adresów sieciowych.
  
|**Element**|**Nazwa podsieci**|**Obszar adresu podsieci**|**Cel**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Podsieć używana przez Usługi domenowe w usłudze Active Directory domeny (AD DS) i maszyn wirtualnych serwera synchronizacji katalogów.  <br/> |
|2.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Podsieci używane przez maszyny wirtualne usług AD FS.  <br/> |
|3.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Podsieci używane przez maszyny wirtualne proxy aplikacji sieci Web.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Podsieci używane przez maszyny wirtualne bramy Azure.  <br/> |
   
 **Tabela S: podsieci w sieci wirtualnej**
  
Następnie wypełnij pole Tabela I w przypadku statycznych adresów IP przypisanych do maszyn wirtualnych i wystąpień równoważenia obciążenia.
  
|**Element**|**Cel**|**Adres IP w podsieci**|**Wartość**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Statyczny adres IP pierwszego kontrolera domeny  <br/> |Czwarty możliwy adres IP dla przestrzeni adresów w podsieci zdefiniowanej w pozycji 1 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Statyczny adres IP drugiego kontrolera domeny  <br/> |Piąty możliwy adres IP dla przestrzeni adresów podsieci zdefiniowanej w pozycji 1 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Statyczny adres IP serwera synchronizacji katalogów  <br/> |Szósty możliwy adres IP dla przestrzeni adresów podsieci zdefiniowanej w pozycji 1 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Statyczny adres IP wewnętrznego równoważenia obciążenia dla serwerów usług AD FS  <br/> |Czwarty możliwy adres IP dla przestrzeni adresów w podsieci zdefiniowanej w pozycji 2 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Statyczny adres IP pierwszego serwera usług AD FS  <br/> |Piąty możliwy adres IP dla przestrzeni adresów podsieci zdefiniowanej w pozycji 2 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |Statyczny adres IP drugiego serwera usług AD FS  <br/> |Szósty możliwy adres IP dla przestrzeni adresów podsieci zdefiniowanej w pozycji 2 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |Statyczny adres IP serwera proxy pierwszej aplikacji sieci Web  <br/> |Czwarty możliwy adres IP dla przestrzeni adresów w podsieci zdefiniowanej w pozycji 3 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |Statyczny adres IP serwera proxy drugiej aplikacji sieci Web  <br/> |Piąty możliwy adres IP dla przestrzeni adresów podsieci zdefiniowanej w pozycji 3 tabeli S.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela I: Statyczne adresy IP w sieci wirtualnej**
  
W przypadku dwóch serwerów dns (Domain Name System) w Twojej sieci lokalnej, których chcesz używać podczas wstępnego konfigurowania kontrolerów domeny w Twojej sieci wirtualnej, wypełnij tabelę D. Aby określić tę listę, we współpracy z działem IT.
  
|**Element**|**Przyjazna nazwa serwera DNS**|**Adres IP serwera DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela D: Lokalne serwery DNS**
  
Aby rozsyłać pakiety z sieci lokalnej do sieci Twojej organizacji przez połączenie VPN między witrynami, musisz skonfigurować sieć wirtualną z siecią lokalną z listą spacji adresów (w notacji CIDR) dla wszystkich dostępnych lokalizacji w sieci lokalnej organizacji. Lista spacji adresów definiująca sieć lokalną musi być unikatowa i nie może zachodzić na przestrzeń adresów używaną w innych sieciach wirtualnych lub innych sieciach lokalnych.
  
W przypadku zestawu lokalnych spacji adresów sieciowych wypełnij pole Tabela L. Pamiętaj, że na liście znajdują się trzy puste wpisy, ale zazwyczaj potrzebujesz więcej. We współpracy z działem IT ustal tę listę spacji adresowych.
  
|**Element**|**Lokalna przestrzeń adresów sieciowych**|
|:-----|:-----|
|1.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela L: Prefiksy adresów dla sieci lokalnej**
  
Teraz zacznij budować infrastrukturę platformy Azure, aby hostować uwierzytelnianie federowane na Microsoft 365.
  
> [!NOTE]
> W poniższych zestawach poleceń jest dostępna najnowsza wersja Azure PowerShell. Zobacz [Wprowadzenie do Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Najpierw uruchom monit Azure PowerShell i zaloguj się do swojego konta.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Aby wygenerować gotowe bloki poleceń programu PowerShell na podstawie ustawień niestandardowych, użyj tego Microsoft Excel [konfiguracji programu PowerShell](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

Uzyskaj nazwę subskrypcji za pomocą następującego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

W przypadku starszych wersji Azure PowerShell użyj tego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Ustaw subskrypcję platformy Azure. Zamień wszystkie cudzysłowy, łącznie ze \< and > znakami, na poprawną nazwę.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Następnie utwórz nowe grupy zasobów. Aby określić unikatowy zestaw nazw grup zasobów, użyj tego polecenia, aby wyświetlić listę istniejących grup zasobów.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Wypełnij następującą tabelę, aby uzyskać zestaw unikatowych nazw grup zasobów.
  
|**Element**|**Nazwa grupy zasobów**|**Cel**|
|:-----|:-----|:-----|
|1.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Kontrolery domeny  <br/> |
|2.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Serwery usług AD FS  <br/> |
|3.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Serwery proxy aplikacji sieci Web  <br/> |
|4.  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |Elementy infrastruktury  <br/> |
   
 **Tabela R: grupy zasobów**
  
Za pomocą tych poleceń utwórz nowe grupy zasobów.
  
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

Następnie należy utworzyć sieć wirtualną platformy Azure i jej podsieci.
  
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

Następnie należy utworzyć grupy zabezpieczeń sieciowych dla każdej podsieci z maszynami wirtualnymi. Aby wykonać izolacji podsieci, możesz dodać reguły dla określonych typów ruchu dozwolonych lub odrzuconych do grupy zabezpieczeń sieciowych w podsieci.
  
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

Następnie użyj tych poleceń, aby utworzyć bramy dla połączenia VPN między witrynami.
  
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
> Uwierzytelnianie federowane pojedynczych użytkowników nie polega na żadnym zasobie lokalnym. Jednak jeśli to połączenie VPN między witrynami stanie się niedostępne, kontrolery domen w witrynie VNet nie będą otrzymywać aktualizacji kont użytkowników ani grup w lokalnym środowisku Usługi domenowe w usłudze Active Directory. Aby tego nie zrobić, możesz skonfigurować wysoką dostępność połączenia VPN między witrynami. Aby uzyskać więcej informacji, zobacz [Wysoce dostępna łączność między siedzibą firmy i między siecią VNet.](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Następnie zanotuj publiczny adres IPv4 bramy Azure VPN dla swojej sieci wirtualnej, wyświetlaąc to polecenie:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Następnie skonfiguruj lokalne urządzenie VPN, aby łączyło się z bramą azure VPN. Aby uzyskać więcej informacji, [zobacz Konfigurowanie urządzenia VPN](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Aby skonfigurować lokalne urządzenie VPN, potrzebne są następujące elementy:
  
- Publiczny adres IPv4 bramy Azure VPN.
    
- Wstępnie udostępniony klucz IPsec dla połączenia VPN między witrynami (tabela V — element 5 — kolumna Wartość).
    
Następnie upewnij się, że obszar adresów sieci wirtualnej jest osiągalny z Twojej sieci lokalnej. Zazwyczaj odbywa się to przez dodanie trasy odpowiadającej wirtualnej przestrzeni adresów sieciowej do urządzenia VPN, a następnie reklamowanie tej trasy do pozostałej infrastruktury routingu w sieci Twojej organizacji. We współpracy z działem IT ustal, jak to zrobić.
  
Następnie zdefiniuj nazwy trzech zestawów dostępności. Wypełnij tabelę A. 
  
|**Element**|**Cel**|**Nazwa zestawu dostępności**|
|:-----|:-----|:-----|
|1.  <br/> |Kontrolery domeny  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Serwery usług AD FS  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Serwery proxy aplikacji sieci Web  <br/> |![wiersz.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabela A: zestawy dostępności**
  
Te nazwy będą potrzebne podczas tworzenia maszyn wirtualnych w fazach 2, 3 i 4.
  
Utwórz nowe zestawy dostępności za pomocą tych Azure PowerShell poleceń.
  
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

Jest to konfiguracja wynikowa pomyślnego ukończenia tego etapu.
  
**Etap 1. Infrastruktura platformy Azure na poziomie wysokiej dostępności uwierzytelniania feder sądowego Microsoft 365**

![Etap 1. wysokiej dostępności uwierzytelniania Microsoft 365 federacji na platformie Azure z infrastrukturą platformy Azure.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Następny krok

Etap [2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) do kontynuowania konfiguracji tego obciążenia pracą.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federeracyjnie o wysokiej dostępności Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla Twojego Microsoft 365 deweloper/środowisko testowania](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 rozwiązania i architektury](../solutions/index.yml)

[Opis Microsoft 365 modeli tożsamości](deploy-identity-solution-identity-model.md)