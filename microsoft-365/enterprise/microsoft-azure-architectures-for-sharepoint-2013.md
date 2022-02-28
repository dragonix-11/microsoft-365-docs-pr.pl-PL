---
title: Microsoft Azure architektury SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
- seo-marvel-apr2020
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: Dowiedz się, jakie typy rozwiązań SharePoint 2013 można hostować w Microsoft Azure maszyn wirtualnych, i jak skonfigurować platformę Azure, aby hostować jeden z nich.
ms.openlocfilehash: 8bbaeb7a20b467625d57800cdf95f42e5b11f434
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983949"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Microsoft Azure architektury SharePoint 2013

Platforma Azure to dobre środowisko do hostowania rozwiązania SharePoint Server 2013. W większości przypadków zalecamy używanie programu Microsoft 365, ale farma programu SharePoint Server hostowana na platformie Azure może być dobrą opcją dla określonych rozwiązań. W tym artykule opisano, jak SharePoint rozwiązania, aby dobrze pasowały do platformy Azure. Jako przykładu są używane następujące dwa rozwiązania szczegółowe:
  
- [SharePoint Server 2013 Odzyskiwanie po awarii w Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Witryny internetowe w programie Microsoft Azure za pomocą programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Zalecane SharePoint dla usług infrastruktury platformy Azure

Usługi infrastruktury platformy Azure to atrakcyjna opcja hostingu SharePoint rozwiązania. Niektóre rozwiązania są lepiej dopasowane do tej platformy niż inne. W poniższej tabeli przedstawiono zalecane rozwiązania.
  
|**Rozwiązanie**|**Dlaczego to rozwiązanie jest zalecane dla platformy Azure**|
|:-----|:-----|
|Środowiska deweloperskich i testowych  <br/> |Tworzenie tych środowisk i zarządzanie nimi jest łatwe.  <br/> |
|Odzyskiwanie po awarii lokalnych farm SharePoint do platformy Azure  <br/> |**Hostowane pomocnicze centrum danych** Zamiast inwestycji w pomocnicze centrum danych w innym regionie użyj platformy Azure. <br/> **Środowiska odzyskiwania po awarii po niższej cenie** Konserwacja i opłacanie mniejszej liczby zasobów niż lokalne środowisko odzyskiwania po awarii. Liczba zasobów zależy od wybranego środowiska odzyskiwania po awarii: gotowości w niskiej gotowości, gotowości w ciepłej sytuacji lub gotowości w trybie gotowości. <br/> **Bardziej elastyczna platforma** W razie awarii łatwo skaluj swoją farmę odzyskiwania SharePoint, aby spełnić wymagania dotyczące ładowania. Skaluj w sposób, w którym nie potrzebujesz już zasobów. <br/> Zobacz [SharePoint odzyskiwania po awarii serwera 2013 w Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Witryny internetowe z funkcjami i skalą, które nie są dostępne w Microsoft 365  <br/> |**Skoncentruj się na swoich działaniach** Skoncentruj się na budowaniu wspaniałej witryny, a nie na infrastrukturze. <br/> **Korzystanie z elastyczności na platformie Azure** Rozmiar farmy na potrzeby potrzeb przez dodanie nowych serwerów i płać tylko za potrzebne zasoby. Dynamiczna alokacja maszynowa nie jest obsługiwana (skala automatyczna). <br/> **Użyj Azure Active Directory (AD) Skorzystaj** z usługi Azure AD do obsługi kont klientów. <br/> **Dodaj SharePoint funkcje, które nie są dostępne w programie Microsoft 365** Dodawanie funkcji raportowania zaawansowanego i analizy sieci Web. <br/> Zobacz [Witryny internetowe w programie Microsoft Azure użyciu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Farmy aplikacji do obsługi Microsoft 365 lub lokalnych  <br/> |**Twórz, testuj i hostuj aplikacje na** platformie Azure, aby obsługiwać zarówno środowiska lokalne, jak i w chmurze. <br/> **Hostuj tę rolę** na platformie Azure zamiast kupowania nowego sprzętu dla środowisk lokalnych. <br/> |
   
W przypadku rozwiązań intranetowych i współpracy oraz obciążeń rozważ następujące opcje:
  
- Określ Microsoft 365 spełnia wymagania biznesowe firmy lub może być częścią rozwiązania. Microsoft 365 udostępnia bogaty zestaw funkcji, który jest zawsze aktualny.
    
- Jeśli Microsoft 365 spełnia ona wszystkich wymagań biznesowych twojej firmy, rozważ wdrożenie standardowego programu SharePoint 2013 lokalnie przez firmę Microsoft Consulting Services (MCS). Architektura standardowa może być szybsza, tańsza i prostsza w przypadku obsługi przez Ciebie niż dostosowane rozwiązanie. 
    
- Jeśli implementacja standardowa nie spełnia wymagań biznesowych Twojej firmy, rozważ dostosowane rozwiązanie lokalne.
    
- Jeśli korzystanie z platformy w chmurze jest ważne dla Twoich wymagań biznesowych, rozważ standardową lub niestandardową implementację programu SharePoint 2013 hostowaną w usługach infrastruktury platformy Azure. SharePoint rozwiązania są znacznie łatwiejsze w obsługi na platformie Azure niż inne platformy chmur publicznych firmy Microsoft, które nie są natywne.
    
## <a name="before-you-design-the-azure-environment"></a>Przed rozpoczęciem projektowania środowiska platformy Azure

W tym artykule użyto przykładowych SharePoint topologii, ale tych pojęć związanych z projektem można używać w SharePoint topologii farmy. Przed rozpoczęciem projektowania środowiska platformy Azure zaprojektuj farmę danych przy użyciu następujących wskazówek dotyczących topologii, architektury, pojemności i SharePoint wydajności:
  
- [Projekt Architektura dla informatyków SharePoint 2013](/SharePoint/technical-reference/technical-diagrams)
    
- [Planowanie wydajności i zarządzania wydajnością w programie SharePoint Server 2013](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a>Określanie typu domeny usługi Active Directory

Każda SharePoint serwera korzysta z usługi Active Directory w celu zapewnienia kont administracyjnych do konfiguracji farmy. Obecnie dostępne są dwie opcje SharePoint na platformie Azure. Są one opisane w poniższej tabeli.
  
|**Opcja**|**Opis**|
|:-----|:-----|
|Domena dedykowana  <br/> |W celu obsługi Twojej farmy danych możesz wdrożyć na platformie Azure dedykowaną i odizolowaną domenę SharePoint usługi Active Directory. Ta możliwość jest dobrym wyborem w przypadku publicznych witryn internetowych.  <br/> |
|Rozszerzanie domeny lokalnej za pośrednictwem połączenia lokalnego  <br/> |Gdy rozszerzysz domenę lokalną za pośrednictwem połączenia lokalnego, użytkownicy uzyskają dostęp do farmy usługi SharePoint za pośrednictwem intranetu, tak jakby była hostowana lokalnie. Możesz skorzystać z lokalnej implementacji usługi Active Directory i systemu DNS.  <br/> Do tworzenia środowiska odzyskiwania po awarii na platformie Azure wymagane jest połączenie między siedzibą firmy.  <br/> |
   
Ten artykuł zawiera pojęcia projektowe dotyczące rozszerzania domeny lokalnej za pośrednictwem połączenia między siedzibą firmy. Jeśli w rozwiązaniu jest używana domena dedykowana, nie jest potrzebne połączenie lokalne.
  
## <a name="design-the-virtual-network"></a>Projektowanie sieci wirtualnej

Najpierw potrzebujesz sieci wirtualnej na platformie Azure, która obejmuje podsieci, w których będą umieszczane Twoje maszyny wirtualne. Sieć wirtualna wymaga prywatnej przestrzeni adresów IP, której część jest przypisywana do podsieci.
  
Jeśli rozszerzasz swoją sieć lokalną na platformę Azure za pośrednictwem połączenia między siedzibą firmy (wymaganego w przypadku środowiska odzyskiwania po awarii), musisz wybrać prywatną przestrzeń adresów, która nie jest jeszcze potrzebna w innej sieci organizacji, która może obejmować Twoje środowisko lokalne i inne sieci wirtualne Platformy Azure. 
  
**Rysunek 1. Środowisko lokalne z siecią wirtualną na platformie Azure**

![Microsoft Azure projektu sieci wirtualnej dla SharePoint rozwiązania. Jedna podsieci dla bramy Azure. Jedna podsieci dla maszyn wirtualnych.](../media/OPrrasconWA-AZarch.png)
  
Na tym diagramie:
  
- Sieć wirtualna na platformie Azure jest ilustrowana obok środowiska lokalnego. Oba środowiska nie są jeszcze połączone za pomocą połączenia lokalnego, które może być połączeniem VPN między witrynami lub usługą ExpressRoute.
    
- W tym momencie sieć wirtualna zawiera jedynie podsieci i nie ma żadnych innych elementów architektonicznych. Jedna podsieci hostuje bramę platformy Azure, a inne podsieci hostuje warstwy farmy SharePoint, a inna dla usługi Active Directory i systemu DNS.
    
## <a name="add-cross-premises-connectivity"></a>Dodawanie łączności między siedzibą

Następnym krokiem wdrożenia jest utworzenie połączenia między siedzibą firmy (jeśli dotyczy to Twojego rozwiązania). W przypadku połączeń między siedzibą firmy Azure brama platformy Azure znajduje się w osobnej podsieci bramy, w której należy utworzyć i przypisać miejsce adresu. 
  
Podczas planowania połączenia między siedzibą firmy definiujesz i tworzysz bramę Azure oraz połączenie z lokalnym urządzeniem bramy.
  
**Rysunek 2. Korzystanie z bramy Azure i lokalnego urządzenia bramy w celu zapewnienia łączności między witryną a platformą Azure**

![Środowisko lokalne połączone z siecią wirtualną platformy Azure za pośrednictwem połączenia lokalnego, które może być połączeniem vpn między witrynami lub usługą ExpressRoute.](../media/AZarch-VPNgtwyconnct.png)
  
Na tym diagramie:
  
- Dodając do poprzedniego diagramu, środowisko lokalne jest połączone z siecią wirtualną platformy Azure za pomocą połączenia między premiowego, które może być połączeniem VPN między witrynami lub usługą ExpressRoute.
    
- Brama platformy Azure znajduje się w podsieci bramy.
    
- Środowisko lokalne zawiera urządzenie bramy, takie jak router lub serwer VPN.
    
Aby uzyskać dodatkowe informacje na temat planowania i tworzenia między siedzibą sieci wirtualnej, zobacz Połączenie do sieci lokalnej z siecią Microsoft Azure [wirtualną](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Dodawanie Usługi domenowe w usłudze Active Directory DNS (AD DS)

Na przykład w celu odzyskiwania po awarii na platformie Azure wdrażasz usługę Windows Server AD i system DNS w scenariuszu hybrydowym, w którym usługa Windows Server AD jest wdrożona zarówno lokalnie, jak i na komputerach wirtualnych platformy Azure.
  
**Rysunek 3. Hybrydowa konfiguracja domeny usługi Active Directory**

![STwo maszyny wirtualne wdrożone w sieci wirtualnej platformy Azure, a podsieć farmy SharePoint jest repliką kontrolerów domeny i serwerów DNS.](../media/AZarch-HyADdomainConfig.png)
  
Ten diagram opiera się na poprzednich diagramach przez dodanie dwóch maszyn wirtualnych do Windows Server AD i podsieci DNS. Te maszyny wirtualne są replikami kontrolerów domen i serwerów DNS. Są one rozszerzeniem lokalnego środowiska Windows Server AD sieci. 
  
W poniższej tabeli przedstawiono zalecenia dotyczące konfiguracji dla tych maszyn wirtualnych na platformie Azure. Skorzystaj z nich jako punktu wyjścia do projektowania własnego środowiska — nawet w przypadku domeny dedykowanej, w której Twoje środowisko platformy Azure nie komunikuje się ze środowiskiem lokalnym.
  
|**Element**|**Konfiguracja**|
|:-----|:-----|
|Rozmiar maszyny wirtualnej na platformie Azure  <br/> |Rozmiar A1 lub A2 w warstwie Standardowe  <br/> |
|System operacyjny  <br/> |Windows Server 2012 R2  <br/> |
|Rola usługi Active Directory  <br/> |AD DS domeny wyznaczony jako globalny serwer wykazu. Ta konfiguracja zmniejsza ruch wychodzący przez połączenie między siedzibą firmy.  <br/> W środowisku wielodomen z wysokimi zmianami (jest to częste) skonfiguruj kontrolery domen w środowisku lokalnym, aby nie były synchronizowane z serwerami wykazu globalnego na platformie Azure w celu zmniejszenia ruchu replikacji.  <br/> |
|Rola DNS  <br/> |Zainstaluj i skonfiguruj usługę serwera DNS w kontrolerach domeny.  <br/> |
|Dyskietki z danymi  <br/> |Umieść bazę danych usługi Active Directory, dzienniki i narzędzie SYSVOL na dodatkowych dyskach z danymi w usłudze Azure. Nie należy umieszczać tych dysków na dysku systemu operacyjnego ani dysków tymczasowych dostarczonych przez platformę Azure.  <br/> |
|Adresy IP  <br/> |Użyj statycznych adresów IP i skonfiguruj sieć wirtualną do przypisywania tych adresów do maszyn wirtualnych w sieci wirtualnej po skonfigurowaniu kontrolerów domeny.  <br/> |
   
> [!IMPORTANT]
> Przed wdrożeniem usługi Active Directory na platformie Azure przeczytaj Wskazówki dotyczące [wdrażania usługi Windows Server Active Directory maszyn wirtualnych platformy Azure](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Pomoże to w określeniu, czy dla Twojego rozwiązania jest potrzebna inna architektura lub inne ustawienia konfiguracji. 
  
## <a name="add-the-sharepoint-farm"></a>Dodawanie farmy SharePoint farmy

Umieść maszyny wirtualne farmy SharePoint w warstwach w odpowiednich podsieciach.
  
**Rysunek 4. Położenie SharePoint maszyn wirtualnych**

![Serwery baz danych i SharePoint serwera dodane do sieci wirtualnej platformy Azure w SharePoint farmie.](../media/AZarch-SPVMsinCloudSer.png)
  
Ten diagram opiera się na poprzednich diagramach przez dodanie SharePoint serwera farmy w odpowiednich warstwach.
  
- Two database virtual machines running SQL Server create the database tier.
    
- Dwie maszyny wirtualne z SharePoint Server 2013 dla każdej z następujących warstw: serwery front end, rozproszone serwery pamięci podręcznej i serwery back end.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Projektowanie i dostosowywanie ról serwera dla zestawów dostępności i domen błędów

Domena błędu to zgrupowanie sprzętu, w którym są uruchamiane wystąpienia ról. Maszyny wirtualne w tej samej domenie błędu mogą być jednocześnie aktualizowane przez infrastrukturę platformy Azure. Mogą też jednocześnie awarii, ponieważ współużytkują ten sam stojak. Aby uniknąć ryzyka związanego z posiadaniem dwóch maszyn wirtualnych w tej samej domenie błędu, możesz skonfigurować swoje maszyny wirtualne jako zestaw dostępności, co gwarantuje, że każda maszyny wirtualnej znajduje się w innej domenie błędu. Jeśli jako zestaw dostępności skonfigurowano trzy maszyny wirtualne, platforma Azure gwarantuje, że nie więcej niż dwa maszyny wirtualne znajdują się w tej samej domenie błędu.
  
Podczas projektowania architektury platformy Azure dla farmy SharePoint skonfiguruj identyczne role serwerów, aby stanowić część zestawu dostępności. Dzięki temu maszyny wirtualne znajdują się w wielu domenach błędów.
  
**Rysunek 5. Korzystanie z zestawów dostępności platformy Azure w celu zapewnienia wysokiej dostępności dla SharePoint farm**

![Konfiguracja zestawów dostępności w infrastrukturze platformy Azure dla rozwiązania w wersji SharePoint 2013.](../media/AZenv-WinAzureAvailSetsHA.png)
  
Ten diagram zawiera informacje o konfiguracji zestawów dostępności w obrębie infrastruktury platformy Azure. Każda z poniższych ról ma oddzielny zestaw dostępności:
  
- Usługa Active Directory i system DNS
    
- Database
    
- Koniec
    
- Rozpowszechnianie pamięci podręcznej
    
- Front end
    
Farma SharePoint może wymagać dopracowania na platformie Azure. Aby zapewnić wysoką dostępność wszystkich składników, upewnij się, że wszystkie role serwera są skonfigurowane identycznie.
  
Oto przykład, który przedstawia standardową architekturę witryn internetowych spełniania określonych celów w zakresie wydajności i wydajności. Ten przykład znajduje się w następującym modelu architektury: Architektura wyszukiwania witryn internetowych dla programu [SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Rysunek 6. Planowanie przykładu celów wydajności i wydajności w farmie trzypoziomowej**

![Standardowa SharePoint witryn internetowych w wersji 2013 z alokacjami składników spełniającymi określone cele w zakresie wydajności i wydajności.](../media/AZarch-CapPerfexmpArch.png)
  
Na tym diagramie:
  
- Przedstawia farmę trójpoziomową: serwery sieci Web, serwery aplikacji i serwery baz danych.
    
- Trzy serwery sieci Web są skonfigurowane identycznie z wieloma składnikami.
    
- Te dwa serwery bazy danych są skonfigurowane identycznie.
    
- Trzy serwery aplikacji nie są skonfigurowane identycznie. Te role serwera wymagają precyzyjnego dostosowywania zestawów dostępności na platformie Azure.
    
Przyjrzyjmy się bliżej warstwie serwera aplikacji.
  
**Rysunek 7. Warstwa serwera aplikacji przed dostosowaniem**

![Przykład SharePoint warstwy serwera aplikacji programu Server 2013 przed dostosowaniem pod Microsoft Azure zestawy dostępności.](../media/AZarch-AppServtierBefore.png)
  
Na tym diagramie:
  
- W warstwie aplikacji są dostępne trzy serwery.
    
- Pierwszy serwer zawiera cztery składniki.
    
- Drugi serwer składa się z trzech składników.
    
- Trzeci serwer zawiera dwa składniki.
    
Liczbę składników określa się na podstawie celów wydajności i wydajności farmy. Aby dostosować tę architekturę dla platformy Azure, zreplikowane będą cztery składniki na wszystkich trzech serwerach. Powoduje to zwiększenie liczby składników poza to, co jest konieczne dla wydajności i wydajności. Kompromis jest taki, że ten projekt gwarantuje wysoką dostępność wszystkich czterech składników na platformie Azure, gdy te trzy maszyny wirtualne zostaną przypisane do zestawu dostępności.
  
**Rysunek 8. Warstwa serwera aplikacji po zakończeniu dostosowywania**

![Przykład SharePoint warstwy serwera aplikacji programu Server 2013 po dostrajeniu pod Microsoft Azure zestawy dostępności.](../media/AZarch-AppServtierAfter.png)
  
Na tym diagramie przedstawiono wszystkie trzy serwery aplikacji skonfigurowane identycznie z czterema identycznymi składnikami.
  
Po dodaniu zestawów dostępności do warstw farmy SharePoint implementacja jest ukończona.
  
**Rysunek 9. Ukończona farma SharePoint w usługach infrastruktury platformy Azure**

![Przykład SharePoint 2013 farmy w usługach infrastruktury platformy Azure z siecią wirtualną, łącznością między siedzibą firmy, podsiecimi, maszynami wirtualnymi i zestawami dostępności.](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Ten diagram przedstawia farmę SharePoint zaimplementowaną w usługach infrastruktury platformy Azure z zestawami dostępności w celu zapewnienia domen błędów dla serwerów w każdej warstwie.
  
## <a name="see-also"></a>Zobacz też

[Microsoft 365 rozwiązania i architektury](../solutions/index.yml)
  
[Witryny internetowe w programie Microsoft Azure za pomocą programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[SharePoint Server 2013 Odzyskiwanie po awarii w Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)