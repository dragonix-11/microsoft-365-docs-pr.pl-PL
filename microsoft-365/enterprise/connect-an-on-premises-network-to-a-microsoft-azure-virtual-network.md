---
title: Połączenie sieci lokalnej do sieci wirtualnej Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 'Podsumowanie: Dowiedz się, jak skonfigurować międzylokalizową sieć wirtualną platformy Azure dla obciążeń serwera Office przy użyciu połączenia sieci VPN typu lokacja-lokacja.'
ms.openlocfilehash: 8f9d8336bb50821374ada700613d2ae6142baf6d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094863"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>Połączenie sieci lokalnej do sieci wirtualnej Microsoft Azure

Sieć wirtualna platformy Azure między środowiskami lokalnymi jest połączona z siecią lokalną, rozszerzając sieć o podsieci i maszyny wirtualne hostowane w usługach infrastruktury platformy Azure. To połączenie umożliwia komputerom w sieci lokalnej bezpośredni dostęp do maszyn wirtualnych na platformie Azure i na odwrót. 

Na przykład serwer synchronizacji katalogów działający na maszynie wirtualnej platformy Azure musi wykonywać zapytania dotyczące lokalnych kontrolerów domeny w celu wprowadzenia zmian w kontach i zsynchronizować te zmiany z subskrypcją Microsoft 365. W tym artykule przedstawiono sposób konfigurowania międzylokacyjnej sieci wirtualnej platformy Azure przy użyciu połączenia wirtualnej sieci prywatnej (VPN) typu lokacja-lokacja, które jest gotowe do hostowania maszyn wirtualnych platformy Azure.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>Konfigurowanie sieci wirtualnej platformy Azure między środowiskami lokalnymi

Maszyny wirtualne na platformie Azure nie muszą być odizolowane od środowiska lokalnego. Aby połączyć maszyny wirtualne platformy Azure z lokalnymi zasobami sieciowymi, należy skonfigurować sieć wirtualną platformy Azure między środowiskami lokalnymi. Na poniższym diagramie przedstawiono składniki wymagane do wdrożenia międzylokalizowej sieci wirtualnej platformy Azure z maszyną wirtualną na platformie Azure.
  
![Sieć lokalna połączona z Microsoft Azure przez połączenie sieci VPN typu lokacja-lokacja.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
Na diagramie istnieją dwie sieci połączone przez połączenie sieci VPN typu lokacja-lokacja: sieć lokalna i sieć wirtualna platformy Azure. Połączenie sieci VPN typu lokacja-lokacja to:

- Między dwoma punktami końcowymi, które są adresowalne i znajdują się w publicznym Internecie.
- Zakończone przez urządzenie sieci VPN w sieci lokalnej i bramę sieci VPN platformy Azure w sieci wirtualnej platformy Azure.

Sieć wirtualna platformy Azure hostuje maszyny wirtualne. Ruch sieciowy pochodzący z maszyn wirtualnych w sieci wirtualnej platformy Azure jest przekazywany do bramy sieci VPN, która następnie przekazuje ruch przez połączenie sieci VPN typu lokacja-lokacja do urządzenia sieci VPN w sieci lokalnej. Infrastruktura routingu sieci lokalnej przekazuje ruch do miejsca docelowego.

>[!Note]
>Możesz również użyć usługi [ExpressRoute](https://azure.microsoft.com/services/expressroute/), która jest bezpośrednim połączeniem między organizacją a siecią firmy Microsoft. Ruch przez usługę ExpressRoute nie odbywa się za pośrednictwem publicznego Internetu. W tym artykule nie opisano korzystania z usługi ExpressRoute.
>
  
Aby skonfigurować połączenie sieci VPN między siecią wirtualną platformy Azure a siecią lokalną, wykonaj następujące kroki: 
  
1. **Lokalnie:** Zdefiniuj i utwórz trasę sieci lokalnej dla przestrzeni adresowej sieci wirtualnej platformy Azure, która wskazuje lokalne urządzenie sieci VPN.
    
2. **Microsoft Azure:** tworzenie sieci wirtualnej platformy Azure z połączeniem sieci VPN typu lokacja-lokacja. 
    
3. **Lokalnie:** Skonfiguruj lokalny sprzęt lub oprogramowanie urządzenia sieci VPN, aby zakończyć połączenie sieci VPN, które korzysta z zabezpieczeń protokołu internetowego (IPsec).
    
Po ustanowieniu połączenia sieci VPN typu lokacja-lokacja należy dodać maszyny wirtualne platformy Azure do podsieci sieci wirtualnej.
  
## <a name="plan-your-azure-virtual-network"></a>Planowanie sieci wirtualnej platformy Azure
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>Wymagania wstępne
<a name="Prerequisites"></a>

- Subskrypcja platformy Azure. Aby uzyskać informacje o subskrypcjach platformy Azure, przejdź do [strony Jak kupić platformę Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- Dostępna prywatna przestrzeń adresowa IPv4 do przypisania do sieci wirtualnej i jej podsieci z wystarczającą przestrzenią do wzrostu, aby pomieścić liczbę maszyn wirtualnych potrzebnych teraz i w przyszłości.
    
- Dostępne urządzenie sieci VPN w sieci lokalnej w celu zakończenia połączenia sieci VPN typu lokacja-lokacja, które obsługuje wymagania dotyczące protokołu IPsec. Aby uzyskać więcej informacji, zobacz [Informacje o urządzeniach sieci VPN dla połączeń sieci wirtualnej typu lokacja-lokacja](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- Zmiany w infrastrukturze routingu, dzięki czemu ruch kierowany do przestrzeni adresowej sieci wirtualnej platformy Azure zostanie przekazany do urządzenia sieci VPN hostującego połączenie sieci VPN typu lokacja-lokacja.
    
- Internetowy serwer proxy, który zapewnia komputerom połączonym z siecią lokalną i sieci wirtualnej platformy Azure dostęp do Internetu.
    
### <a name="solution-architecture-design-assumptions"></a>Założenia dotyczące projektowania architektury rozwiązania

Poniższa lista przedstawia opcje projektowe, które zostały dokonane dla tej architektury rozwiązania. 
  
- To rozwiązanie używa pojedynczej sieci wirtualnej platformy Azure z połączeniem sieci VPN typu lokacja-lokacja. Sieć wirtualna platformy Azure hostuje jedną podsieć, która może zawierać wiele maszyn wirtualnych. 
    
- Usługi routingu i dostępu zdalnego (RRAS) w Windows Server 2016 lub Windows Server 2012 można użyć do ustanowienia połączenia sieci VPN typu lokacja-lokacja protokołu IPsec między siecią lokalną a siecią wirtualną platformy Azure. Możesz również użyć innych opcji, takich jak urządzenia sieci VPN Cisco lub Juniper Networks.
    
- Sieć lokalna może nadal mieć usługi sieciowe, takie jak Active Directory Domain Services (AD DS), system nazw domen (DNS) i serwery proxy. W zależności od wymagań może być korzystne umieszczenie niektórych z tych zasobów sieciowych w sieci wirtualnej platformy Azure.
    
W przypadku istniejącej sieci wirtualnej platformy Azure z co najmniej jedną podsiecią określ, czy pozostała przestrzeń adresowa dla dodatkowej podsieci do hostowania potrzebnych maszyn wirtualnych na podstawie wymagań. Jeśli nie masz pozostałej przestrzeni adresowej dla dodatkowej podsieci, utwórz dodatkową sieć wirtualną, która ma własne połączenie sieci VPN typu lokacja-lokacja.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Planowanie zmian infrastruktury routingu dla sieci wirtualnej platformy Azure

Należy skonfigurować lokalną infrastrukturę routingu w celu przekazywania ruchu przeznaczonego dla przestrzeni adresowej sieci wirtualnej platformy Azure do lokalnego urządzenia sieci VPN hostującego połączenie sieci VPN typu lokacja-lokacja.
  
Dokładna metoda aktualizowania infrastruktury routingu zależy od sposobu zarządzania informacjami o routingu, które mogą być następujące:
  
- Aktualizacje tabeli routingu na podstawie konfiguracji ręcznej.
    
- Aktualizacje tabeli routingu oparte na protokołach routingu, takich jak routing Information Protocol (RIP) lub Open Shortest Path First (OSPF).
    
Skontaktuj się ze specjalistą ds. routingu, aby upewnić się, że ruch kierowany do sieci wirtualnej platformy Azure jest przekazywany do lokalnego urządzenia sieci VPN.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Planowanie reguł zapory dla ruchu do i z lokalnego urządzenia sieci VPN

Jeśli urządzenie sieci VPN znajduje się w sieci obwodowej, która ma zaporę między siecią obwodową a Internetem, może być konieczne skonfigurowanie zapory dla następujących reguł, aby zezwolić na połączenie sieci VPN typu lokacja-lokacja.
  
- Ruch do urządzenia sieci VPN (przychodzącego z Internetu):
    
  - Docelowy adres IP urządzenia sieci VPN i protokołu IP 50
    
  - Docelowy adres IP urządzenia sieci VPN i portu docelowego UDP 500
    
  - Docelowy adres IP urządzenia sieci VPN i portu docelowego UDP 4500
    
- Ruch z urządzenia sieci VPN (wychodzący do Internetu):
    
  - Źródłowy adres IP urządzenia sieci VPN i protokołu IP 50
    
  - Źródłowy adres IP urządzenia sieci VPN i portu źródłowego UDP 500
    
  - Źródłowy adres IP urządzenia sieci VPN i portu źródłowego UDP 4500
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Planowanie prywatnej przestrzeni adresów IP sieci wirtualnej platformy Azure

Prywatna przestrzeń adresów IP sieci wirtualnej platformy Azure musi być w stanie pomieścić adresy używane przez platformę Azure do hostowania sieci wirtualnej i co najmniej jedną podsieć, która ma wystarczającą liczbę adresów dla maszyn wirtualnych platformy Azure.
  
Aby określić liczbę adresów potrzebnych dla podsieci, zlicz potrzebną teraz liczbę maszyn wirtualnych, oszacuj przyszły wzrost, a następnie użyj poniższej tabeli, aby określić rozmiar podsieci.
  
|**Wymagana liczba maszyn wirtualnych**|**Liczba potrzebnych bitów hosta**|**Rozmiar podsieci**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Planowanie arkusza na potrzeby konfigurowania sieci wirtualnej platformy Azure
<a name="worksheet"> </a>

Przed utworzeniem sieci wirtualnej platformy Azure do hostowania maszyn wirtualnych należy określić ustawienia wymagane w poniższych tabelach.
  
Aby uzyskać informacje o ustawieniach sieci wirtualnej, wypełnij tabelę V.
  
 **Tabela V: konfiguracja między lokalnymi sieciami wirtualnymi**
  
|**Element**|**Element konfiguracji**|**Opis**|**Wartość**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nazwa sieci wirtualnej  <br/> |Nazwa do przypisania do sieci wirtualnej platformy Azure (przykład DirSyncNet).  <br/> |![Linii.](../media/Common-Images/TableLine.png) |
|2.  <br/> |Lokalizacja sieci wirtualnej  <br/> |Centrum danych platformy Azure, które będzie zawierać sieć wirtualną (na przykład Zachodnie stany USA).  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Adres IP urządzenia sieci VPN  <br/> |Publiczny adres IPv4 interfejsu urządzenia sieci VPN w Internecie. Skontaktuj się z działem IT, aby określić ten adres.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Przestrzeń adresowa sieci wirtualnej  <br/> |Przestrzeń adresowa (zdefiniowana w pojedynczym prefiksie adresu prywatnego) dla sieci wirtualnej. Skontaktuj się z działem IT, aby określić tę przestrzeń adresów. Przestrzeń adresowa powinna być w formacie CIDR (Classless Interdomain Routing), znanym również jako format prefiksu sieci. Przykładem jest 10.24.64.0/20.  <br/> |![Linii.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |Klucz udostępniony protokołu IPsec  <br/> |32-znakowy, alfanumeryczny ciąg, który będzie używany do uwierzytelniania obu stron połączenia sieci VPN typu lokacja-lokacja. Skontaktuj się z działem IT lub działu zabezpieczeń, aby określić tę wartość klucza, a następnie zapisać ją w bezpiecznej lokalizacji. Alternatywnie zobacz [Create a random string for an IPsec preshared key (Tworzenie losowego ciągu dla klucza wstępnego udostępniania protokołu IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)).  <br/> |![Linii.](../media/Common-Images/TableLine.png) <br/> |
   
Wypełnij tabelę S dla podsieci tego rozwiązania.
  
- W pierwszej podsieci określ 28-bitową przestrzeń adresową (o długości prefiksu /28) dla podsieci bramy platformy Azure. Zobacz [Obliczanie przestrzeni adresowej podsieci bramy dla sieci wirtualnych platformy Azure](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) , aby uzyskać informacje o sposobie określania tej przestrzeni adresowej.
    
- W drugiej podsieci określ przyjazną nazwę, pojedynczą przestrzeń adresów IP opartą na przestrzeni adresowej sieci wirtualnej i opisowy cel.
    
Skontaktuj się z działem IT, aby określić te przestrzenie adresowe z przestrzeni adresowej sieci wirtualnej. Obie przestrzenie adresowe powinny mieć format CIDR.
  
 **Tabela S: podsieci w sieci wirtualnej**
  
|**Element**|**Nazwa podsieci**|**Przestrzeń adresowa podsieci**|**Celu**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |Podsieć używana przez bramę platformy Azure.  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
W przypadku lokalnych serwerów DNS, których mają używać maszyny wirtualne w sieci wirtualnej, wypełnij tabelę D. Nadaj każdemu serwerowi DNS przyjazną nazwę i pojedynczy adres IP. Ta przyjazna nazwa nie musi być zgodna z nazwą hosta lub nazwą komputera serwera DNS. Pamiętaj, że na liście znajdują się dwa puste wpisy, ale możesz dodać więcej. Skontaktuj się z działem IT, aby określić tę listę.
  
 **Tabela D: Lokalne serwery DNS**
  
|**Element**|**Przyjazna nazwa serwera DNS**|**Adres IP serwera DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
   
Aby kierować pakiety z sieci wirtualnej platformy Azure do sieci organizacji przez połączenie sieci VPN typu lokacja-lokacja, należy skonfigurować sieć wirtualną za pomocą sieci lokalnej. Ta sieć lokalna zawiera listę przestrzeni adresowych (w formacie CIDR) dla wszystkich lokalizacji w sieci lokalnej organizacji, do których muszą dotrzeć maszyny wirtualne w sieci wirtualnej. Mogą to być wszystkie lokalizacje w sieci lokalnej lub podzestawie. Lista przestrzeni adresowych definiujących sieć lokalną musi być unikatowa i nie może nakładać się na przestrzenie adresowe używane dla tej sieci wirtualnej lub innych sieci wirtualnych obejmujących wiele lokalizacji.
  
W przypadku zestawu przestrzeni adresowych sieci lokalnej wypełnij tabelę L. Pamiętaj, że na liście znajdują się trzy puste wpisy, ale zazwyczaj potrzebujesz więcej. Skontaktuj się z działem IT, aby określić tę listę.
  
 **Tabela L: Prefiksy adresów dla sieci lokalnej**
  
|**Element**|**Przestrzeń adresowa sieci lokalnej**|
|:-----|:-----|
|1.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linii.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![Linii](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>Plan wdrożenia
<a name="DeploymentRoadmap"> </a>

Tworzenie lokalnej sieci wirtualnej i dodawanie maszyn wirtualnych na platformie Azure składa się z trzech faz:
  
- Faza 1. Przygotowywanie sieci lokalnej.
    
- Faza 2. Tworzenie lokalnej sieci wirtualnej na platformie Azure.
    
- Faza 3 (opcjonalnie): dodawanie maszyn wirtualnych.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>Faza 1. Przygotowywanie sieci lokalnej
<a name="Phase1"></a>

Sieć lokalną należy skonfigurować przy użyciu trasy, która wskazuje i ostatecznie dostarcza ruch przeznaczony dla przestrzeni adresowej sieci wirtualnej do routera na krawędzi sieci lokalnej. Skontaktuj się z administratorem sieci, aby ustalić, jak dodać trasę do infrastruktury routingu sieci lokalnej.
  
Oto konfiguracja wyniku.
  
![Sieć lokalna musi mieć trasę dla przestrzeni adresowej sieci wirtualnej, która wskazuje urządzenie sieci VPN.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>Faza 2. Tworzenie lokalnej sieci wirtualnej na platformie Azure
<a name="Phase2"></a>

Najpierw otwórz Azure PowerShell monit. Jeśli nie zainstalowano Azure PowerShell, zobacz [Wprowadzenie z Azure PowerShell](/powershell/azure/get-started-azureps).

 
Następnie zaloguj się do konta platformy Azure za pomocą tego polecenia.
  
```powershell
Connect-AzAccount
```

Pobierz nazwę subskrypcji przy użyciu następującego polecenia.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

Ustaw subskrypcję platformy Azure za pomocą tych poleceń. Zastąp wszystkie elementy w cudzysłowie, w tym znaki < i >, poprawną nazwą subskrypcji.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Następnie utwórz nową grupę zasobów dla sieci wirtualnej. Aby określić unikatową nazwę grupy zasobów, użyj tego polecenia, aby wyświetlić listę istniejących grup zasobów.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Utwórz nową grupę zasobów przy użyciu tych poleceń.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Następnie utworzysz sieć wirtualną platformy Azure.
  
```powershell
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Oto konfiguracja wyniku.
  
![Sieć wirtualna nie jest jeszcze połączona z siecią lokalną.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Następnie użyj tych poleceń, aby utworzyć bramy dla połączenia sieci VPN typu lokacja-lokacja.
  
```powershell
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Oto konfiguracja wyniku.
  
![Sieć wirtualna ma teraz bramę.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Następnie skonfiguruj lokalne urządzenie sieci VPN w celu nawiązania połączenia z bramą sieci VPN platformy Azure. Aby uzyskać więcej informacji, zobacz [About VPN Devices for site-to-site Azure Virtual Network connections (Informacje o urządzeniach sieci VPN dla połączeń Virtual Network platformy Azure typu lokacja-lokacja](/azure/vpn-gateway/vpn-gateway-about-vpn-devices)).
  
Aby skonfigurować urządzenie sieci VPN, potrzebne są następujące elementy:
  
- Publiczny adres IPv4 bramy sieci VPN platformy Azure dla sieci wirtualnej. Użyj polecenia **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** , aby wyświetlić ten adres.
    
- Klucz wstępny protokołu IPsec dla połączenia sieci VPN typu lokacja-lokacja (tabela V— element 5 — kolumna wartość).
    
Oto konfiguracja wyniku.
  
![Sieć wirtualna jest teraz połączona z siecią lokalną.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>Faza 3 (opcjonalnie): dodawanie maszyn wirtualnych

Utwórz maszyny wirtualne potrzebne na platformie Azure. Aby uzyskać więcej informacji, zobacz [Tworzenie maszyny wirtualnej Windows przy użyciu Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Użyj następujących ustawień:
  
- Na **karcie Podstawy** wybierz tę samą subskrypcję i grupę zasobów co sieć wirtualna. Będą one potrzebne później, aby zalogować się do maszyny wirtualnej. W sekcji **Szczegóły wystąpienia** wybierz odpowiedni rozmiar maszyny wirtualnej. Zarejestruj nazwę użytkownika i hasło konta administratora w bezpiecznej lokalizacji. 
    
- Na karcie Sieć wybierz nazwę sieci wirtualnej i podsieci do **hostowania** maszyn wirtualnych (a nie podsieć GatewaySubnet). Pozostaw wszystkie inne ustawienia na wartościach domyślnych.
    
Sprawdź, czy maszyna wirtualna prawidłowo używa systemu DNS, sprawdzając wewnętrzny system DNS, aby upewnić się, że dodano rekordy adresu (A) dla nowej maszyny wirtualnej. Aby uzyskać dostęp do Internetu, maszyny wirtualne platformy Azure muszą być skonfigurowane do korzystania z serwera proxy sieci lokalnej. Skontaktuj się z administratorem sieci, aby uzyskać dodatkowe kroki konfiguracji do wykonania na serwerze.
  
Oto konfiguracja wyniku.
  
![Sieć wirtualna hostuje teraz maszyny wirtualne, które są dostępne z sieci lokalnej.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>Następny krok
  
[Wdrażanie synchronizacji katalogów Microsoft 365 w Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)