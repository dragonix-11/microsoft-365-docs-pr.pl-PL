---
title: architektury Microsoft Azure dla SharePoint 2013 r.
ms.author: bcarter
author: brendacarter
manager: scotv
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
description: Dowiedz się, które typy rozwiązań SharePoint 2013 mogą być hostowane na maszynach wirtualnych Microsoft Azure i jak skonfigurować platformę Azure do hostowania.
ms.openlocfilehash: 7761eb9b62000c03b2983bc5ed56a62e20981db7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097409"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>architektury Microsoft Azure dla SharePoint 2013 r.

Platforma Azure to dobre środowisko do hostowania rozwiązania SharePoint Server 2013. W większości przypadków zalecamy Microsoft 365, ale farma serwerów SharePoint hostowana na platformie Azure może być dobrym rozwiązaniem dla konkretnych rozwiązań. W tym artykule opisano sposób tworzenia architektury rozwiązań SharePoint, aby dobrze pasowały do platformy Azure. Następujące dwa konkretne rozwiązania są używane jako przykłady:
  
- [Odzyskiwanie po awarii programu SharePoint Server 2013 na platformie Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Witryny internetowe w Microsoft Azure przy użyciu programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Zalecane rozwiązania SharePoint dla usług Azure Infrastructure Services

Usługi infrastruktury platformy Azure to atrakcyjna opcja hostingu rozwiązań SharePoint. Niektóre rozwiązania lepiej pasują do tej platformy niż inne. W poniższej tabeli przedstawiono zalecane rozwiązania.
  
|**Rozwiązanie**|**Dlaczego to rozwiązanie jest zalecane dla platformy Azure**|
|:-----|:-----|
|Środowiska programistyczne i testowe  <br/> |Tworzenie tych środowisk i zarządzanie nimi jest łatwe.  <br/> |
|Odzyskiwanie po awarii lokalnych farm SharePoint na platformę Azure  <br/> |**Hostowane pomocnicze centrum danych** Użyj platformy Azure zamiast inwestować w pomocnicze centrum danych w innym regionie. <br/> **Środowiska odzyskiwania po awarii o niższych kosztach** Obsługa i płacenie za mniejszą liczbę zasobów niż lokalne środowisko odzyskiwania po awarii. Liczba zasobów zależy od wybranego środowiska odzyskiwania po awarii: rezerwy zimnej, rezerwy ciepłej lub rezerwy gorącej. <br/> **Bardziej elastyczna platforma** W przypadku awarii można łatwo skalować w poziomie farmę SharePoint odzyskiwania w celu spełnienia wymagań dotyczących obciążenia. Skaluj w poziomie, gdy zasoby nie są już potrzebne. <br/> Zobacz [SharePoint Server 2013 Disaster Recovery in Microsoft Azure (Odzyskiwanie po awarii serwera SharePoint Server 2013 w Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)).  <br/> |
|Witryny internetowe korzystające z funkcji i skalowania nie są dostępne w Microsoft 365  <br/> |**Skoncentruj swoje wysiłki** Skoncentruj się na budowaniu wspaniałego obiektu, a nie na budowaniu infrastruktury. <br/> **Korzystanie z elastyczności na platformie Azure** Rozmiar farmy dla zapotrzebowania przez dodanie nowych serwerów i płacenie tylko za potrzebne zasoby. Dynamiczna alokacja maszyny nie jest obsługiwana (skalowanie automatyczne). <br/> **Użyj Azure Active Directory (AD)** Skorzystaj z usługi Azure AD dla kont klientów. <br/> **Dodaj funkcje SharePoint niedostępne w Microsoft 365** Dodaj szczegółowe raportowanie i analizę internetową. <br/> Zobacz [Witryny internetowe w Microsoft Azure przy użyciu programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Farmy aplikacji do obsługi środowisk Microsoft 365 lub lokalnych  <br/> |**Twórz, testuj i hostuj aplikacje** na platformie Azure, aby obsługiwać środowiska lokalne i w chmurze. <br/> **Hostuj tę rolę** na platformie Azure zamiast kupować nowy sprzęt dla środowisk lokalnych. <br/> |
   
W przypadku rozwiązań intranetowych i współpracy oraz obciążeń rozważ następujące opcje:
  
- Ustal, czy Microsoft 365 spełnia wymagania biznesowe, czy może być częścią rozwiązania. Microsoft 365 udostępnia bogaty zestaw funkcji, który jest zawsze aktualny.
    
- Jeśli Microsoft 365 nie spełnia wszystkich wymagań biznesowych, rozważ standardową implementację SharePoint 2013 lokalnie z usług Microsoft Consulting Services (MCS). Standardowa architektura może być szybszym, tańszym i łatwiejszym rozwiązaniem do obsługi niż niestandardowa. 
    
- Jeśli standardowa implementacja nie spełnia wymagań biznesowych, rozważ dostosowane rozwiązanie lokalne.
    
- Jeśli korzystanie z platformy w chmurze jest ważne dla wymagań biznesowych, rozważ standardową lub dostosowaną implementację SharePoint 2013 r. hostowaną w usługach infrastruktury platformy Azure. SharePoint rozwiązania są znacznie łatwiejsze do obsługi na platformie Azure niż inne nienatywne platformy chmury publicznej firmy Microsoft.
    
## <a name="before-you-design-the-azure-environment"></a>Przed zaprojektowaniem środowiska platformy Azure

Chociaż w tym artykule użyto przykładowych topologii SharePoint, można użyć tych pojęć projektowych z dowolną topologią farmy SharePoint. Przed zaprojektowaniem środowiska platformy Azure użyj następującej topologii, architektury, pojemności i wskazówek dotyczących wydajności, aby zaprojektować farmę SharePoint:
  
- [Projekt architektury dla specjalistów IT SharePoint 2013](/SharePoint/technical-reference/technical-diagrams)
    
- [Planowanie zarządzania wydajnością i pojemnością w programie SharePoint Server 2013](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a>Określanie typu domeny usługi Active Directory

Każda farma serwerów SharePoint korzysta z usługi Active Directory w celu zapewnienia kont administracyjnych dla konfiguracji farmy. Obecnie istnieją dwie opcje SharePoint rozwiązań na platformie Azure. Zostały one opisane w poniższej tabeli.
  
|**Opcja**|**Opis**|
|:-----|:-----|
|Domena dedykowana  <br/> |Dedykowaną i izolowaną domenę usługi Active Directory można wdrożyć na platformie Azure, aby obsługiwać farmę SharePoint. Jest to dobry wybór dla publicznych witryn internetowych.  <br/> |
|Rozszerzanie domeny lokalnej za pomocą połączenia między środowiskiem lokalnym  <br/> |Po rozszerzeniu domeny lokalnej za pośrednictwem połączenia między środowiskiem lokalnym użytkownicy uzyskują dostęp do farmy SharePoint za pośrednictwem intranetu tak, jakby była hostowana lokalnie. Możesz skorzystać z implementacji lokalna usługa Active Directory i DNS.  <br/> Do utworzenia środowiska odzyskiwania po awarii na platformie Azure wymagane jest połączenie między środowiskami lokalnymi w celu przejścia w tryb failover z farmy lokalnej.  <br/> |
   
Ten artykuł zawiera koncepcje projektowe dotyczące rozszerzania domeny lokalnej za pośrednictwem połączenia między środowiskiem lokalnym. Jeśli rozwiązanie korzysta z dedykowanej domeny, nie potrzebujesz połączenia między środowiskiem lokalnym.
  
## <a name="design-the-virtual-network"></a>Projektowanie sieci wirtualnej

Najpierw potrzebujesz sieci wirtualnej na platformie Azure, która obejmuje podsieci, w których zostaną umieszczane maszyny wirtualne. Sieć wirtualna wymaga prywatnej przestrzeni adresowej IP, której część jest przypisywana do podsieci.
  
Jeśli rozszerzasz sieć lokalną na platformę Azure za pośrednictwem połączenia między lokalizacjami (wymaganego dla środowiska odzyskiwania po awarii), musisz wybrać prywatną przestrzeń adresową, która nie jest jeszcze używana w innym miejscu w sieci organizacji, która może obejmować środowisko lokalne i inne sieci wirtualne platformy Azure. 
  
**Rysunek 1. Środowisko lokalne z siecią wirtualną na platformie Azure**

![Microsoft Azure projekt sieci wirtualnej dla rozwiązania SharePoint. Jedna podsieć bramy platformy Azure. Jedna podsieć maszyn wirtualnych.](../media/OPrrasconWA-AZarch.png)
  
Na tym diagramie:
  
- Sieć wirtualna na platformie Azure jest zilustrowana obok środowiska lokalnego. Te dwa środowiska nie są jeszcze połączone za pomocą połączenia międzylokacyjnej, które może być połączeniem sieci VPN typu lokacja-lokacja lub usługą ExpressRoute.
    
- W tym momencie sieć wirtualna obejmuje tylko podsieci i żadne inne elementy architektury. Jedna podsieć będzie hostem bramy platformy Azure, a inne podsieci hostują warstwy farmy SharePoint, a dodatkowa dla usług Active Directory i DNS.
    
## <a name="add-cross-premises-connectivity"></a>Dodawanie łączności między lokalizacjami

Następnym krokiem wdrożenia jest utworzenie połączenia między środowiskiem lokalnym (jeśli dotyczy to rozwiązania). W przypadku połączeń obejmujących wiele lokalizacji brama platformy Azure znajduje się w oddzielnej podsieci bramy, którą należy utworzyć i przypisać przestrzeń adresową. 
  
Podczas planowania połączenia między środowiskiem lokalnym definiujesz i tworzysz bramę platformy Azure oraz połączenie z lokalnym urządzeniem bramy.
  
**Rysunek 2. Używanie bramy platformy Azure i urządzenia bramy lokalnej w celu zapewnienia łączności typu lokacja-lokacja między środowiskiem lokalnym a platformą Azure**

![Środowisko lokalne połączone z siecią wirtualną platformy Azure za pomocą połączenia międzylokacyjnej, które może być połączeniem sieci VPN typu lokacja-lokacja lub usługą ExpressRoute.](../media/AZarch-VPNgtwyconnct.png)
  
Na tym diagramie:
  
- Dodając do poprzedniego diagramu, środowisko lokalne jest połączone z siecią wirtualną platformy Azure za pomocą połączenia międzylokacyjnej, które może być połączeniem sieci VPN typu lokacja-lokacja lub usługą ExpressRoute.
    
- Brama platformy Azure znajduje się w podsieci bramy.
    
- Środowisko lokalne obejmuje urządzenie bramy, takie jak router lub serwer sieci VPN.
    
Aby uzyskać dodatkowe informacje dotyczące planowania i tworzenia międzymiejskiej sieci wirtualnej, zobacz [Połączenie sieci lokalnej do Microsoft Azure sieci wirtualnej](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Dodawanie Active Directory Domain Services (AD DS) i DNS

W przypadku odzyskiwania po awarii na platformie Azure wdrażasz Windows Server AD i system DNS w scenariuszu hybrydowym, w którym Windows Server AD jest wdrażany zarówno lokalnie, jak i na maszynach wirtualnych platformy Azure.
  
**Rysunek 3. Konfiguracja domeny hybrydowej usługi Active Directory**

![Maszyny wirtualne STwo wdrożone w sieci wirtualnej platformy Azure i podsieci farmy SharePoint są replikami kontrolerów domeny i serwerów DNS.](../media/AZarch-HyADdomainConfig.png)
  
Ten diagram opiera się na poprzednich diagramach przez dodanie dwóch maszyn wirtualnych do podsieci Windows Server AD i DNS. Te maszyny wirtualne są replikami kontrolerów domeny i serwerów DNS. Są one rozszerzeniem lokalnego środowiska Windows Server AD. 
  
Poniższa tabela zawiera zalecenia dotyczące konfiguracji tych maszyn wirtualnych na platformie Azure. Użyj ich jako punktu początkowego do projektowania własnego środowiska — nawet w przypadku dedykowanej domeny, w której środowisko platformy Azure nie komunikuje się ze środowiskiem lokalnym.
  
|**Element**|**Konfiguracja**|
|:-----|:-----|
|Rozmiar maszyny wirtualnej na platformie Azure  <br/> |Rozmiar A1 lub A2 w warstwie Standardowa  <br/> |
|System operacyjny  <br/> |Windows Server 2012 R2  <br/> |
|Rola usługi Active Directory  <br/> |Kontroler domeny usług AD DS wyznaczony jako serwer wykazu globalnego. Ta konfiguracja zmniejsza ruch wychodzący między połączeniami lokalnymi.  <br/> W środowisku wielodomenowym z wysokimi szybkościami zmian (nie jest to typowe) skonfiguruj kontrolery domeny lokalnie, aby nie były synchronizowane z serwerami wykazu globalnego na platformie Azure, aby zmniejszyć ruch związany z replikacją.  <br/> |
|Rola DNS  <br/> |Zainstaluj i skonfiguruj usługę serwera DNS na kontrolerach domeny.  <br/> |
|Dyski danych  <br/> |Umieść bazę danych, dzienniki i SYSVOL usługi Active Directory na dodatkowych dyskach danych platformy Azure. Nie umieszczaj ich na dysku systemu operacyjnego ani na dyskach tymczasowych udostępnianych przez platformę Azure.  <br/> |
|Adresy IP  <br/> |Użyj statycznych adresów IP i skonfiguruj sieć wirtualną, aby przypisywać te adresy do maszyn wirtualnych w sieci wirtualnej po skonfigurowaniu kontrolerów domeny.  <br/> |
   
> [!IMPORTANT]
> Przed wdrożeniem usługi Active Directory na platformie Azure przeczytaj [wytyczne dotyczące wdrażania Windows Server Active Directory na platformie Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Ułatwiają one określenie, czy rozwiązanie wymaga innej architektury lub różnych ustawień konfiguracji. 
  
## <a name="add-the-sharepoint-farm"></a>Dodawanie farmy SharePoint

Umieść maszyny wirtualne farmy SharePoint w warstwach w odpowiednich podsieciach.
  
**Rysunek 4. Umieszczanie maszyn wirtualnych SharePoint**

![Serwery baz danych i role serwera SharePoint dodane do sieci wirtualnej platformy Azure w podsieci farmy SharePoint.](../media/AZarch-SPVMsinCloudSer.png)
  
Ten diagram opiera się na poprzednich diagramach przez dodanie SharePoint ról serwera farmy w odpowiednich warstwach.
  
- Dwie maszyny wirtualne bazy danych z systemem SQL Server utworzyć warstwę bazy danych.
    
- Dwie maszyny wirtualne z systemem SharePoint Server 2013 dla każdej z następujących warstw: serwery frontonu, rozproszone serwery pamięci podręcznej i serwery zaplecza.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Projektowanie i dostosowywanie ról serwera dla zestawów dostępności i domen błędów

Domena błędów to grupa sprzętu, w którym działają wystąpienia ról. Maszyny wirtualne w tej samej domenie błędów mogą być aktualizowane przez infrastrukturę platformy Azure w tym samym czasie. Mogą też zakończyć się niepowodzeniem w tym samym czasie, ponieważ mają ten sam stojak. Aby uniknąć ryzyka posiadania dwóch maszyn wirtualnych w tej samej domenie błędów, można skonfigurować maszyny wirtualne jako zestaw dostępności, co gwarantuje, że każda maszyna wirtualna znajduje się w innej domenie błędów. Jeśli trzy maszyny wirtualne są skonfigurowane jako zestaw dostępności, platforma Azure gwarantuje, że nie więcej niż dwie maszyny wirtualne znajdują się w tej samej domenie błędów.
  
Podczas projektowania architektury platformy Azure dla farmy SharePoint skonfiguruj identyczne role serwera jako część zestawu dostępności. Dzięki temu maszyny wirtualne są rozmieszczone w wielu domenach błędów.
  
**Rysunek 5. Używanie zestawów dostępności platformy Azure w celu zapewnienia wysokiej dostępności dla warstw farmy SharePoint**

![Konfiguracja zestawów dostępności w infrastrukturze platformy Azure dla rozwiązania SharePoint 2013.](../media/AZenv-WinAzureAvailSetsHA.png)
  
Na tym diagramie przedstawiono konfigurację zestawów dostępności w infrastrukturze platformy Azure. Każda z następujących ról współużytkuje oddzielny zestaw dostępności:
  
- Usługi Active Directory i DNS
    
- Database
    
- Zaplecze
    
- Dystrybucja pamięci podręcznej
    
- Frontonu
    
Farma SharePoint może wymagać dostosowania na platformie Azure. Aby zapewnić wysoką dostępność wszystkich składników, upewnij się, że wszystkie role serwera są skonfigurowane identycznie.
  
Oto przykład przedstawiający standardową architekturę witryn internetowych, która spełnia określone cele dotyczące pojemności i wydajności. Ten przykład jest przedstawiony w następującym modelu architektury: [Architektury wyszukiwania witryn internetowych dla SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Rysunek 6. Przykład planowania wydajności i celów wydajności w farmie trójwarstwowej**

![Standardowa architektura witryn internetowych SharePoint 2013 z alokacjami składników, które spełniają określone cele dotyczące pojemności i wydajności.](../media/AZarch-CapPerfexmpArch.png)
  
Na tym diagramie:
  
- Reprezentowana jest trzywarstwowa farma: serwery internetowe, serwery aplikacji i serwery baz danych.
    
- Trzy serwery internetowe są skonfigurowane identycznie z wieloma składnikami.
    
- Dwa serwery bazy danych są skonfigurowane identycznie.
    
- Trzy serwery aplikacji nie są skonfigurowane identycznie. Te role serwera wymagają dostrajania zestawów dostępności na platformie Azure.
    
Przyjrzyjmy się bliżej warstwie serwera aplikacji.
  
**Rysunek 7. Warstwa serwera aplikacji przed dostrojeniem**

![Przykładowa warstwa serwera aplikacji SharePoint Server 2013 przed dostrojeniem zestawów dostępności Microsoft Azure.](../media/AZarch-AppServtierBefore.png)
  
Na tym diagramie:
  
- W warstwie aplikacji znajdują się trzy serwery.
    
- Pierwszy serwer zawiera cztery składniki.
    
- Drugi serwer zawiera trzy składniki.
    
- Trzeci serwer zawiera dwa składniki.
    
Liczbę składników można określić według wartości docelowych wydajności i pojemności farmy. Aby dostosować tę architekturę dla platformy Azure, zreplikujemy cztery składniki na wszystkich trzech serwerach. Zwiększa to liczbę składników poza to, co jest niezbędne do zapewnienia wydajności i pojemności. Kompromis polega na tym, że ten projekt zapewnia wysoką dostępność wszystkich czterech składników na platformie Azure, gdy te trzy maszyny wirtualne są przypisane do zestawu dostępności.
  
**Rysunek 8. Warstwa serwera aplikacji po dostrojeniu**

![Przykładowa warstwa serwera aplikacji SharePoint Server 2013 po dostrajaniu zestawów dostępności Microsoft Azure.](../media/AZarch-AppServtierAfter.png)
  
Na tym diagramie przedstawiono wszystkie trzy serwery aplikacji skonfigurowane identycznie z tymi samymi czterema składnikami.
  
Po dodaniu zestawów dostępności do warstw farmy SharePoint implementacja zostanie ukończona.
  
**Rysunek 9. Ukończona farma SharePoint w usługach infrastruktury platformy Azure**

![Przykład SharePoint farmy 2013 w usługach infrastruktury platformy Azure z siecią wirtualną, łącznością między lokalizacjami, podsieciami, maszynami wirtualnymi i zestawami dostępności.](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Na tym diagramie przedstawiono farmę SharePoint wdrożoną w usługach infrastruktury platformy Azure z zestawami dostępności w celu zapewnienia domen błędów dla serwerów w każdej warstwie.
  
## <a name="see-also"></a>Zobacz też

[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)
  
[Witryny internetowe w Microsoft Azure przy użyciu programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Odzyskiwanie po awarii programu SharePoint Server 2013 na platformie Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)