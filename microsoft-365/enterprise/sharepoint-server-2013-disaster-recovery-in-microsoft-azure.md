---
title: Odzyskiwanie po awarii programu SharePoint Server 2013 na platformie Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Deployment
- seo-marvel-apr2020
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: W tym artykule opisano, jak za pomocą platformy Azure utworzyć środowisko odzyskiwania po awarii dla lokalnej farmy SharePoint farmy.
ms.openlocfilehash: 873d0c9ccfdc8c6a978b89416a7492a2141c825d
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569141"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Odzyskiwanie po awarii programu SharePoint Server 2013 na platformie Microsoft Azure

 Za pomocą platformy Azure możesz utworzyć środowisko odzyskiwania po awarii dla lokalnej farmy SharePoint farmie. W tym artykule opisano, jak zaprojektować i zaimplementować to rozwiązanie.

 **Obejrzyj klip wideo z SharePoint odzyskiwania po awarii programu SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]

 W sytuacji, gdy awaria SharePoint w środowisku lokalnym, najważniejsze jest szybkie uruchomienie systemu. Odzyskiwanie po awarii SharePoint jest szybsze i łatwiejsze, gdy w sieci jest już uruchomione Microsoft Azure środowisko kopii zapasowej. W tym klipie wideo wyjaśniono główne pojęcia dotyczące środowiska SharePoint trybu failover, a także uzupełniono wszystkie szczegółowe informacje dostępne w tym artykule.

Skorzystaj z tego artykułu w następującym modelu rozwiązań: odzyskiwanie po awarii SharePoint **w programie Microsoft Azure**.

[![SharePoint odzyskiwania po awarii na platformę Azure.](../media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)

 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) | [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)

## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Korzystanie z usług infrastruktury platformy Azure do odzyskiwania po awarii

Wiele organizacji nie ma środowiska odzyskiwania po awarii dla SharePoint, co może być kosztowne w przypadku kompilacji i konserwacji lokalnej. Usługi infrastruktury platformy Azure zapewniają atrakcyjne opcje dla środowisk odzyskiwania po awarii, które są bardziej elastyczne i tańsze niż lokalne alternatywy.

Zalety korzystania z usług infrastruktury platformy Azure obejmują:

- **Mniej kosztownych zasobów** Obsługa i opłacanie mniejszej liczby zasobów niż lokalne środowiska odzyskiwania po awarii. Liczba zasobów zależy od wybranego środowiska odzyskiwania po awarii: gotowości w niskiej stanie, wstrzymania w wysokiej jakości lub wstrzymania w trybie gotowości.

- **Większa elastyczność zasobów** W razie awarii łatwo skaluj swoją farmę odzyskiwania SharePoint, aby spełnić wymagania dotyczące ładowania. Skaluj w sposób, w którym nie potrzebujesz już zasobów.

- **Niższe zobowiązanie centrum danych** Zamiast inwestycji w pomocnicze centrum danych w innym regionie skorzystaj z usług infrastruktury platformy Azure.

Dostępne są mniej złożone opcje dla organizacji, które dopiero zaczynają pracę z odzyskiwaniem po awarii i zaawansowane opcje dla organizacji o wysokim poziomie odporności. Definicje dotyczące niskiej, ciepłej i hot standby środowiska różnią się nieco, gdy środowisko jest hostowane na platformie w chmurze. W poniższej tabeli opisano te środowiska do tworzenia farmy SharePoint odzyskiwania na platformie Azure.

**Tabela: Środowiska odzyskiwania**

|Typ środowiska odzyskiwania|Opis|
|---|---|
|Hot|Aprowizowana, aktualizowana i uruchamiana w trybie gotowości farma o pełnym rozmiarze.|
|Warm (Warm)|Jest ona budowaną farmą, a maszyny wirtualne są uruchomione i aktualizowane. <br/> Odzyskiwanie obejmuje dołączanie baz danych zawartości, inicjowanie obsługi aplikacji usług i przeszukiwanie zawartości. <br/> Farma może być mniejszą wersją farmy produkcyjnej, a następnie skalowana w celu obsługi pełnej bazy użytkowników.|
|Cold|Farma jest w pełni zbudowana, ale maszyny wirtualne są zatrzymywane. <br/> Konserwacja środowiska obejmuje od czasu do czasu uruchamianie maszyn wirtualnych, poprawianie, aktualizowanie i weryfikowanie środowiska. <br/> Uruchom pełne środowisko w razie awarii.|

Ważne jest, aby oceniać cele organizacji w zakresie czasu odzyskiwania (RTOS) i cele punktów odzyskiwania (RESEARCHOS). Te wymagania określają, które środowisko jest najbardziej odpowiednią inwestycją w organizacji.

W wskazówki w tym artykule opisano implementowanie środowiska wstrzymania w sposób bardzo wstrzymania. Możesz również dostosować go do trybu gotowości w niskiej jakości, chociaż musisz wykonać dodatkowe procedury w celu obsługi tego rodzaju środowiska. W tym artykule nie opisano sposobu zaimplementowania środowiska wstrzymania w trybie gotowości w trybie gotowości.

Aby uzyskać więcej informacji na temat rozwiązań do odzyskiwania po awarii, zobacz Koncepcje wysokiej dostępności i odzyskiwania po awarii w programie [SharePoint 2013](/SharePoint/administration/high-availability-and-disaster-recovery-concepts) i Wybieranie strategii odzyskiwania po awarii dla systemu [SharePoint 2013](/SharePoint/administration/plan-for-disaster-recovery).

## <a name="solution-description"></a>Opis rozwiązania

Najlepsze rozwiązanie do odzyskiwania po awarii przy zachowaniu gotowości wymaga następującego środowiska:

- Lokalna farma SharePoint produkcyjnej

- Farma SharePoint odzyskiwania na platformie Azure

- Połączenie VPN między dwoma środowiskami między witrynami

Na poniższej ilustracji przedstawiono te trzy elementy.

**Rysunek: Elementy ciepłego rozwiązania gotowości na platformie Azure**

![Elementy najlepszego rozwiązania SharePoint gotowości na platformie Azure.](../media/AZarch-AZWarmStndby.png)

SQL Server wysyłki dziennika z replikacją systemu plików rozłożonych (DFSR, Distributed File System Replication) służy do kopiowania kopii zapasowych baz danych i dzienników transakcji do farmy odzyskiwania na platformie Azure:

- DFSR przesyła dzienniki ze środowiska produkcyjnego do środowiska odzyskiwania. W scenariuszu sieci WAN usługa DFSR jest bardziej wydajna niż wysyłanie dzienników bezpośrednio do serwera pomocniczego na platformie Azure.

- Dzienniki są odtwarzane do centrum SQL Server w środowisku odzyskiwania na platformie Azure.

- Do czasu wykonania ćwiczenia z odzyskiwaniem nie dołączaj wysyłanych SharePoint bazy danych zawartości w środowisku odzyskiwania.

Aby odzyskać farmę, wykonaj następujące czynności:

1. Zatrzymaj wysyłkę dziennika.

2. Zatrzymywanie akceptowania ruchu do farmy podstawowej.

3. Ponowne odtwarzanie ostatecznych dzienników transakcji.

4. Dołączanie baz danych zawartości do farmy.

5. Przywracanie aplikacji usługi z replikowanych baz danych usług.

6. Zaktualizuj rekordy systemu nazw domen (DNS) tak, aby wskazują farmę odzyskiwania.

7. Rozpoczynanie przeszukiwania pełnego.

Zalecane jest regularne przećwiczenie tych kroków i udokumentować je, aby zapewnić płynne działanie odzyskiwania na żywo. Dołączanie baz danych zawartości i przywracanie aplikacji usługi może zająć trochę czasu i zazwyczaj obejmuje konfigurację ręczną.

Po wykonaniu odzyskiwania to rozwiązanie udostępnia elementy wymienione w poniższej tabeli.

**Tabela: Cele odzyskiwania rozwiązań**

|Element|Opis|
|---|---|
|Witryny i zawartość|Witryny i zawartość są dostępne w środowisku odzyskiwania.|
|Nowe wystąpienie wyszukiwania|W tym gotowym rozwiązaniu do wstrzymania wyszukiwanie nie jest przywracane z baz danych wyszukiwania. Składniki wyszukiwania w farmie odzyskiwania są konfigurowane tak samo, jak to możliwe w farmie produkcyjnej. Po przywróceniu witryn i zawartości jest rozpoczynane przeszukiwanie pełne w celu odbudowania indeksu wyszukiwania. Nie musisz czekać na ukończenie przeszukiwania, aby witryny i zawartość były dostępne.|
|Usługi|Usługi przechowujące dane w bazach danych są przywracane z wysyłanych w dzienniku baz danych. Usługi, które nie przechowują danych w bazach danych, są po prostu uruchomione. <br/> Nie wszystkie usługi z bazami danych muszą zostać przywrócone. Nie trzeba przywracać następujących usług z baz danych i można je po prostu rozpocząć po zakończeniu trybu failover: <br/> Zbieranie danych dotyczących użycia i kondycji <br/> Usługa województwa <br/> Automatyzacja programu Word <br/> Każda inna usługa, która nie korzysta z bazy danych|

Możesz współpracować z usługami Microsoft Consulting Services (MCS) lub partnerem, aby rozwiązać bardziej złożone cele dotyczące odzyskiwania danych. Podsumowywane są w poniższej tabeli.

**Tabela: Inne elementy, na które może odechcieć firma MCS lub partner**

|Element|Opis|
|---|---|
|Synchronizowanie niestandardowych rozwiązań farm|Najlepiej, jeśli konfiguracja farmy odzyskiwania jest identyczna z konfiguracją farmy produkcyjnej. Możesz współpracować z konsultantem lub partnerem, aby ocenić, czy niestandardowe rozwiązania farmy są replikowane, i czy istnieje proces synchronizowania tych dwóch środowisk.|
|Połączenia ze źródłami danych w środowisku lokalnym|Replikowanie połączeń do systemów danych back-end, takich jak połączenia zapasowego kontrolera domeny (BDC) i wyszukiwanie źródeł zawartości, może być niepraktyczne.|
|Scenariusze przywracania wyszukiwania|Ponieważ wdrożenia wyszukiwania w przedsiębiorstwie zwykle są dość unikatowe i złożone, przywracanie wyszukiwania z baz danych wymaga większych inwestycji. Możesz współpracować z konsultantem lub partnerem w celu ustalenia i wdrożenia scenariuszy przywracania wyszukiwania, które mogą być wymagane przez Twoją organizację.|

W wskazówkach podanych w tym artykule założono, że farma lokalna jest już zaprojektowana i wdrożona.

## <a name="detailed-architecture"></a>Architektura szczegółowa

Najlepiej, jeśli konfiguracja farmy odzyskiwania na platformie Azure jest identyczna z konfiguracją lokalną farmy produkcyjnej, na przykład z następującymi:

- Ta sama reprezentacja ról serwera

- Ta sama konfiguracja dostosowań

- Ta sama konfiguracja składników wyszukiwania

Środowisko na platformie Azure może być mniejszą wersją farmy produkcyjnej. Jeśli planujesz przeskalować farmę odzyskiwania po trybie failover, ważne jest, aby każdy typ roli serwera był początkowo reprezentowany.

Niektóre konfiguracje replikowania w środowisku trybu failover mogą być niepraktyczne. Pamiętaj, aby przetestować procedury i środowisko trybu failover, aby upewnić się, że farma trybu failover zapewnia oczekiwany poziom usługi.

To rozwiązanie nie oznacza określonej topologii dla farmy SharePoint farmy. Celem tego rozwiązania jest użycie platformy Azure na farmie trybu failover oraz zaimplementowanie wysyłki dziennika i funkcji DFSR między dwoma środowiskami.

### <a name="warm-standby-environments"></a>Warm standby environments

W środowisku gotowości (warm standby) wszystkie maszyny wirtualne w środowisku platformy Azure są uruchomione. Środowisko jest gotowe do ćwiczeń lub zdarzenia trybu failover.

Na poniższej ilustracji przedstawiono rozwiązanie do odzyskiwania po awarii z farmy lokalnej usługi SharePoint do farmy programu SharePoint opartej na platformie Azure skonfigurowanej jako ciepłe środowisko gotowości.

**Rysunek: Topologia i kluczowe elementy farmy produkcyjnej oraz farma odzyskiwania gotowości (warm standby)**

![Topologia farmy SharePoint i farmy odzyskiwania gotowości (warm standby).](../media/AZarch-AZWarmStndby.png)

Na tym diagramie:

- Dwa środowiska są ilustrowane obok siebie: lokalna farma SharePoint oraz farma ciepłego wstrzymania na platformie Azure.

- Każde środowisko obejmuje udział plików.

- Każda farma zawiera cztery warstwy. Aby osiągnąć wysoką dostępność, każda warstwa zawiera dwa serwery lub maszyny wirtualne, które są skonfigurowane identycznie dla określonej roli, takiej jak usługi front end, rozłożona pamięć podręczna, usługi back-end i bazy danych. Na tej ilustracji nie ma znaczenia, aby nazywać określone składniki. Te dwie farmy są skonfigurowane identycznie.

- Czwarta warstwa to warstwa bazy danych. Wysyłka dziennika służy do kopiowania dzienników z pomocniczego serwera bazy danych w środowisku lokalnym do udziału plików w tym samym środowisku.

- Narzędzie DFSR kopiuje pliki z udziału plików w środowisku lokalnym do udziału plików w środowisku platformy Azure.

- Wysyłka dziennika odtwarza dzienniki z udziału plików w środowisku platformy Azure do repliki podstawowej w grupie SQL Server Dostępność AlwaysOn w środowisku odzyskiwania.

### <a name="cold-standby-environments"></a>Środowiska pracy w trybie gotowości w niskiej gotowości

W środowisku gotowości w niskiej gotowości większość maszyn SharePoint maszyn wirtualnych farmy można zamknąć. (Czasem zalecamy uruchamianie maszyn wirtualnych, na przykład co dwa tygodnie lub raz w miesiącu, aby każda maszynę wirtualną można było zsynchronizować z domeną). Następujące maszyny wirtualne w środowisku odzyskiwania platformy Azure muszą pozostać uruchomione, aby zapewnić ciągłe operacje wysyłki dziennika i funkcji DFSR:

- Udział plików

- Podstawowy serwer bazy danych

- Co najmniej jedna maszyna wirtualna z Windows Server Active Directory domenami i systemem DNS

Na poniższej ilustracji przedstawiono środowisko trybu failover platformy Azure, w którym jest udostępniana maszyna wirtualna współużytkowania plików i podstawowa SharePoint bazy danych jest uruchomiona. Wszystkie inne SharePoint zostaną zatrzymane. Maszynę wirtualną, z Windows Server Active Directory i systemem DNS, nie jest wyświetlana.

**Rysunek: Farma odzyskiwania w trybie gotowości z uruchomionymi maszynami wirtualnymi**

![Elementy rozwiązania w trybie SharePoint w trybie gotowości na platformie Azure.](../media/AZarch-AZColdStndby.png)

Po trybie failover w środowisku gotowości w niskiej dostępności wszystkie maszyny wirtualne są uruchomione i musi zostać skonfigurowana metoda osiągnięcia wysokiej dostępności serwerów bazy danych, na przykład grupa dostępności SQL Server AlwaysOn.

Jeśli zaimplementowano wiele grup magazynu (bazy danych znajdują się na więcej niż jednym SQL Server zestawu o wysokiej dostępności), podstawowa baza danych dla każdej grupy magazynu musi być uruchomiona, aby zaakceptować dzienniki skojarzone z jej grupą magazynu.

### <a name="skills-and-experience"></a>Umiejętności i doświadczenie

To rozwiązanie do odzyskiwania po awarii używa wielu technologii. Aby zapewnić interakcję tych technologii zgodnie z oczekiwaniami, każdy składnik w środowisku lokalnym i na platformie Azure musi zostać zainstalowany i prawidłowo skonfigurowany. Zalecamy, aby osoba lub zespół, który konfiguruje to rozwiązanie, miał silną wiedzę roboczą i umiejętności praktyczne z technologiami opisanymi w następujących artykułach:

- [Usługi replikacji systemu plików (DFS, Distributed File System)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))

- [Windows klastrów trybu failover serwera (WSFC) z SQL Server](/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)

- [AlwaysOn Availability Groups (SQL Server)](/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)

- [Jak tworzyć kopię zapasową i przywracać SQL Server danych](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)

- [SharePoint wdrożenie farmy i instalacji programu SharePoint Server 2013](/SharePoint/install/installation-and-configuration-overview)

- [Microsoft Azure](/azure/)

Ponadto zalecamy używanie umiejętności skryptów, które pozwalają zautomatyzować zadania skojarzone z tymi technologiami. Możliwe jest wykonywanie wszystkich zadań opisanych w tym rozwiązaniu za pomocą dostępnych interfejsów użytkownika. Jednak ręczne podejście może być czasochłonne i podatne na błędy oraz dostarcza niespójnych wyników.

Oprócz bibliotek Windows PowerShell dostępne są również Windows PowerShell biblioteki usług SQL Server, SharePoint Server i Azure. Nie zapomnij O-SQL, co może także skrócić czas konfigurowania i konserwacji środowiska odzyskiwania po awarii.

## <a name="disaster-recovery-roadmap"></a>Plan odzyskiwania po awarii

![Wizualna reprezentacja planu SharePoint odzyskiwania po awarii.](../media/Azure-DRroadmap.png)

W tym przewodniku założono, że masz już farmę programu SharePoint Server 2013 wdrożoną w środowisku produkcyjnym.

**Tabela: plan odzyskiwania po awarii**

|Faza|Opis|
|---|---|
|Etap 1|Zaprojektuj środowisko odzyskiwania po awarii.|
|Etap 2|Utwórz połączenie sieci wirtualnej i vpn platformy Azure.|
|Etap 3|Wd Windows usługi Active Directory i nazwy domeny w sieci wirtualnej platformy Azure.|
|Etap 4|Wdeksuj farmę odzyskiwania SharePoint na platformie Azure.|
|Etap 5|Skonfiguruj DFSR między farmami.|
|Etap 6|Skonfiguruj wysyłkę dziennika do farmy odzyskiwania.|
|Etap 7|Sprawdź poprawność rozwiązań do trybu failover i odzyskiwania. Obejmuje to następujące procedury i technologie: <br/> Zatrzymaj wysyłkę dziennika. <br/> Przywracanie kopii zapasowych. <br/> Przeszukiwanie zawartości. <br/> Odzyskiwanie usług. <br/> Zarządzanie rekordami DNS.|

## <a name="phase-1-design-the-disaster-recovery-environment"></a>Etap 1. Projektowanie środowiska odzyskiwania po awarii

Skorzystaj z wskazówek w Microsoft Azure architektury awarii systemu [SharePoint 2013,](microsoft-azure-architectures-for-sharepoint-2013.md) aby zaprojektować środowisko odzyskiwania po awarii, w tym farmę SharePoint odzyskiwania. Możesz użyć grafiki w pliku odzyskiwania po awarii [SharePoint Na Visio Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554), aby rozpocząć proces projektowania. Zalecamy zaprojektowanie całego środowiska przed rozpoczęciem pracy w środowisku platformy Azure.

Oprócz wskazówek w architekturze Microsoft Azure dla programu [SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) dotyczących projektowania sieci wirtualnej, połączenia VPN, farmy usługi Active Directory i farmy usługi SharePoint pamiętaj o dodaniu roli udziału plików w środowisku platformy Azure.

Aby obsługiwać wysyłkę dziennika w rozwiązaniu odzyskiwania po awarii, do podsieci, w której znajdują się role bazy danych, jest dodawana maszynowa współużytk plików. Udział plików służy również jako trzeci węzeł większości węźle dla grupy dostępności SQL Server AlwaysOn. Jest to zalecana konfiguracja standardowej farmy SharePoint, która używa grup SQL Server dostępność AlwaysOn.

> [!NOTE]
> Ważne jest sprawdzenie wymagań wstępnych bazy danych, aby uczestniczyć w grupie dostępności usługi SQL Server AlwaysOn. Aby uzyskać więcej informacji, zobacz [Wymagania wstępne, ograniczenia i Rekomendacje grupy dostępności AlwaysOn](/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability).

**Rysunek: Położenie serwera plików używanego do odzyskiwania po awarii**

![Pokazuje pozycję maszyny wirtualnej udziału plików dodaną do tej samej usługi w chmurze, która zawiera SharePoint serwera bazy danych.](../media/AZenv-FSforDFSRandWSFC.png)

Na tym diagramie wirtualna współużytk plików jest dodawana do tej samej podsieci na platformie Azure, która zawiera role serwera bazy danych. Nie dodawaj maszyny wirtualnej współużytkowania plików do zestawu dostępności z innymi rolami serwera, takimi jak SQL Server ról.

Jeśli martwi Cię wysoka dostępność dzienników, rozważ inne podejście, korzystając z kopii zapasowej i SQL Server kopii zapasowej i przywracania za pomocą [usługi Azure Blob Storage.](/sql/relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service) Jest to nowa funkcja na platformie Azure, która zapisuje dzienniki bezpośrednio w adresie URL magazynu obiektów blob. To rozwiązanie nie zawiera wskazówek dotyczących korzystania z tej funkcji.

Podczas projektowania farmy odzyskiwania należy pamiętać, że pomyślne środowisko odzyskiwania po awarii dokładnie odzwierciedla farmę produkcyjną, którą chcesz odzyskać. Rozmiar farmy odzyskiwania nie jest najważniejszym elementem w projekcie, wdrożeniu i testowaniu farmy odzyskiwania. Skala farmy różni się w zależności od wymagań biznesowych organizacji. Może być możliwe użycie farmy skalowanej przez krótką pustą pracę lub do czasu, gdy wymaga się skalowania farmy przez wymagania dotyczące wydajności i wydajności.

Skonfiguruj farmę odzyskiwania tak identycznie, jak to tylko możliwe, w farmie produkcyjnej, aby spełniała wymagania umowy dotyczącej poziomu usług i udostępniała funkcje potrzebne do obsługi Twojej firmy. Podczas projektowania środowiska odzyskiwania po awarii przyjrzyj się także procesowi zarządzania zmianą w środowisku produkcyjnym. Zalecamy rozszerzenie procesu zarządzania zmianą na środowisko odzyskiwania przez zaktualizowanie środowiska odzyskiwania w tym samym interwale czasu co w środowisku produkcyjnym. W ramach procesu zarządzania zmianami zalecamy prowadzenie szczegółowego spisu konfiguracji farmy, aplikacji i użytkowników.

## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Etap 2. Tworzenie wirtualnej sieci platformy Azure i połączenia VPN

Połączenie sieci lokalnej do sieci [Microsoft Azure wirtualnej](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) pokazano, jak zaplanować i wdrożyć sieć wirtualną na platformie Azure oraz jak utworzyć połączenie VPN. Postępuj zgodnie ze wskazówkami w tym temacie, aby wykonać następujące procedury:

- Zaplanuj prywatną przestrzeń adresów IP Virtual Network.

- Planowanie zmian infrastruktury routingu w Virtual Network.

- Zaplanuj reguły zapory dla ruchu z i do lokalnego urządzenia VPN.

- Utwórz lokalną sieć wirtualną na platformie Azure.

- Skonfiguruj routing między siecią lokalną a siecią Virtual Network.

## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Etap 3. Wdrażanie usług Active Directory i domain Name Services w sieci wirtualnej platformy Azure

Ten etap obejmuje wdrożenie usług Windows Server Active Directory i DNS w uwitrynie Virtual Network w scenariuszu hybrydowym zgodnie z opisem w architekturze Microsoft Azure dla systemu [SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) oraz jak pokazano na poniższym rysunku.

**Rysunek: hybrydowa konfiguracja domeny usługi Active Directory**

![Dwie maszyny wirtualne wdrożone w sieci wirtualnej platformy Azure i SharePoint Farma jest repliką kontrolerów domeny i serwerów DNS.](../media/AZarch-HyADdomainConfig.png)

Na ilustracji w tej samej podsieci są wdrożone dwie maszyny wirtualne. Te maszyny wirtualne obsługują dwie role: usługę Active Directory i system DNS.

Przed wdrożeniem usługi Active Directory na platformie Azure przeczytaj Wskazówki [dotyczące wdrażania usługi Windows Server Active Directory na platformie Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Te wskazówki pomogą Ci w określeniu, czy potrzebujesz innej architektury, czy różnych ustawień konfiguracji dla swojego rozwiązania.

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania kontrolera domeny na platformie Azure, zobacz Instalowanie repliki domena usługi Active Directory [w azure virtual networks](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).

Przed tą fazą nie wdrożono maszyn wirtualnych na Virtual Network. Maszyny wirtualne hostowania usługi Active Directory i systemu DNS prawdopodobnie nie są największymi maszynami wirtualnymi potrzebnymi do rozwiązania. Przed wdrożeniem tych maszyn wirtualnych należy utworzyć największą maszynę wirtualną, która ma być Virtual Network. Dzięki temu rozwiązanie może znaleźć się na tagu na platformie Azure, który zapewnia największy potrzebny rozmiar. Obecnie nie musisz konfigurować tej maszyny wirtualnej. Po prostu utwórz go i odłóż na bok. Jeśli tego nie zrobisz, podczas późniejszej próby utworzenia większych maszyn wirtualnych może wystąpić ograniczenie, co było problemem podczas pisano w tym artykule.

## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Etap 4. Wdrażanie farmy SharePoint odzyskiwania na platformie Azure

Wdychuj SharePoint farmę w Virtual Network zgodnie z planami projektu. Warto przejrzeć planowanie programu [SharePoint 2013](/previous-versions/azure/dn275958(v=azure.100)) w usługach infrastruktury platformy Azure przed wdrożeniem ról SharePoint na platformie Azure.

Rozważmy następujące praktyki, które poznaliśmy, konując nasze środowisko dowodu koncepcji:

- Tworzenie maszyn wirtualnych przy użyciu programu Azure Portal lub PowerShell.

- Platforma Azure i technologia Hyper-V nie obsługują pamięci dynamicznej. Należy się upewnić, że wpływa to na wydajność i wydajność twoich planów.

- Uruchom ponownie maszyny wirtualne za pośrednictwem interfejsu platformy Azure, a nie samego logowania maszyn wirtualnych. Korzystanie z interfejsu platformy Azure działa lepiej i jest bardziej przewidywalne.

- Jeśli chcesz zamknąć maszynę wirtualną, aby zaoszczędzić koszty, skorzystaj z interfejsu platformy Azure. Po zamknięciu logowania maszyny wirtualnej opłaty będą nadal naliczane.

- Korzystanie z konwencji nazewnictwa dla maszyn wirtualnych.

- Zwróć uwagę na lokalizację centrum danych, w którym są wdrażane maszyny wirtualne.

- Funkcja skalowania automatycznego na platformie Azure nie jest obsługiwana w SharePoint ról.

- Nie konfiguruj elementów w farmie, które zostaną przywrócone, takich jak zbiory witryn.

## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Etap 5. Konfigurowanie usługi DFSR między farmami

Aby skonfigurować replikację plików przy użyciu funkcji DFSR, użyj przystawki zarządzanie systemem DNS. Jednak przed rozpoczęciem konfiguracji funkcji DFSR zaloguj się na lokalnym serwerze plików i serwerze plików Azure, a następnie włącz usługę w Windows.

W Menedżer serwera pulpitu nawigacyjnego wykonaj następujące czynności:

- Skonfiguruj serwer lokalny.

- Uruchom Kreatora **dodawania ról i funkcji**.

- Otwórz węzeł **Plik i Storage Services**.

- Wybierz **pozycję Przestrzenie nazw DFS i** **replikacja usług DFS**.

- Kliknij **przycisk Dalej** , aby zakończyć kroki kreatora.

W poniższej tabeli znajdują się linki do artykułów referencyjnych dotyczących usługi DFSR i wpisów w blogach.

**Tabela: Artykuły referencyjne dotyczące usługi DFSR**

|Tytuł|Opis|
|---|---|
|[Replikacja](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11))|Temat w witrynie TechNet Zarządzanie usługami DFS z łączami replikacji|
|[Replikacja systemu DFS: przewodnik po procesach posunietowych](https://go.microsoft.com/fwlink/p/?LinkId=392737)|Strona typu wiki z linkami do informacji usługi DFS|
|[Replikacja systemu DFS: często zadawane pytania](/previous-versions/windows/it-pro/windows-server-2003/cc773238(v=ws.10))|Temat usługi replikacji systemu DFS w witrynie TechNet|
|[Blog Użytkownika Ciesiego Barreto](/archive/blogs/josebda/)|Blog napisany przez głównego menedżera programów w zespole file server w firmie Microsoft|
|[The Storage Team at Microsoft - File Cabinet Blog](https://go.microsoft.com/fwlink/p/?LinkId=392740)|Blog o usługach plików i funkcjach przechowywania w programie Windows Server|

## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Etap 6. Konfigurowanie wysyłki dziennika do farmy odzyskiwania

Wysyłka dziennika jest krytycznym składnikiem do konfigurowania odzyskiwania po awarii w tym środowisku. Wysyłka dziennika umożliwia automatyczne wysyłanie plików dziennika transakcji dla baz danych z podstawowego wystąpienia serwera bazy danych do pomocniczego wystąpienia serwera bazy danych. Aby skonfigurować wysyłkę dziennika, zobacz Konfigurowanie wysyłki [dziennika w programie SharePoint 2013](/sharepoint/administration/configure-log-shipping).

> [!IMPORTANT]
> Obsługa wysyłki dziennika w programie SharePoint Server jest ograniczona do niektórych baz danych. Aby uzyskać więcej informacji, zobacz Obsługiwane opcje wysokiej dostępności i odzyskiwania po awarii dla baz danych programu [SharePoint (SharePoint 2013)](/SharePoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas).

## <a name="phase-7-validate-failover-and-recovery"></a>Etap 7. Sprawdzanie poprawności trybu failover i odzyskiwania

Celem tego końcowego etapu jest sprawdzenie, czy rozwiązanie do odzyskiwania po awarii działa zgodnie z planem. W tym celu utwórz zdarzenie trybu failover, które w zamian wyłącza farmę produkcyjną i uruchamia farmę odzyskiwania. Scenariusz trybu failover można uruchomić ręcznie lub przy użyciu skryptów.

Pierwszym krokiem jest zatrzymanie przychodzących żądań użytkowników na usługi lub zawartość farmy. Możesz to zrobić, wyłączając wpisy DNS lub wyłączając serwery front-end web servers. Gdy farma zostanie "w dół", możesz przejść w tryb fail over do farmy odzyskiwania.

### <a name="stop-log-shipping"></a>Zatrzymaj wysyłkę dziennika

Przed odzyskaniem farmy musisz zatrzymać wysyłkę dziennika. Najpierw zatrzymaj wysyłkę dziennika na serwerze pomocniczym na platformie Azure, a następnie zatrzymaj ją na lokalnym serwerze podstawowym. Aby najpierw zatrzymać wysyłkę dziennika na serwerze pomocniczym, a następnie na serwerze podstawowym, należy użyć poniższego skryptu. Nazwy baz danych w skrypcie mogą się różnić w zależności od środowiska.

```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')
```

### <a name="restore-the-backups"></a>Przywracanie kopii zapasowych

Kopie zapasowe należy przywrócić w kolejności, w jakiej zostały utworzone. Aby można było przywrócić określoną kopię zapasową dziennika transakcji, należy najpierw przywrócić poniższe poprzednie kopie zapasowe bez wycofywania niezatwierdzeń transakcji (czyli przy użyciu):`WITH NORECOVERY`

- Pełna kopia zapasowa bazy danych i ostatnia zapasowa kopia zapasowa — przywróć te kopie zapasowe, jeśli istnieją, wykonane przed określoną kopią zapasową dziennika transakcji. Przed utworzeniem najnowszej pełnej lub zróżnicowanej kopii zapasowej bazy danych używano pełnego modelu odzyskiwania lub modelu odzyskiwania rejestrowanego zbiorczo.

- Wszystkie kopie zapasowe dziennika transakcji — przywróć wszelkie kopie zapasowe dziennika transakcji wykonane po pełnej kopii zapasowej bazy danych lub dopiero potem (jeśli przywrócisz kopię zapasową) przed określoną kopią zapasową dziennika transakcji. Kopie zapasowe dzienników należy stosować w kolejności, w jakiej zostały utworzone, bez przerw w łańcuchu dzienników.

Aby odzyskać bazę danych zawartości na serwerze pomocniczym w celu renderowania witryn, usuń wszystkie połączenia bazy danych przed ich odzyskaniem. Aby przywrócić bazę danych, uruchom następujące SQL danych.

```SQL
restore database WSS_Content with recovery
```

> [!IMPORTANT]
> Podczas jawnego korzystania z funkcji T-SQL określ w każdej instrukcji RESTORE wartość **WITH NORECOVERY** lub **WITH RECOVERY**, aby wyeliminować niejednoznaczność— jest to bardzo ważne podczas pisania skryptów. Po przywróceniu pełnych i przyrostowych kopii zapasowych dzienniki transakcji można przywrócić w SQL Server Management Studio. Ponadto ponieważ wysyłka dziennika jest już zatrzymana, baza danych zawartości znajduje się w stanie gotowości, więc musisz zmienić stan na pełny dostęp.

W SQL Server Management Studio kliknij prawym przyciskiem myszy bazę danych programu **WSS_Content**, wskaż pozycję **TasksRestore** > , a następnie kliknij pozycję Dziennik **transakcji (jeśli** nie została przywrócona pełna kopia zapasowa, ta wartość jest niedostępne). Aby uzyskać więcej informacji, [zobaczRestore kopii zapasowej dziennika transakcji (SQL Server)](/sql/relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server).

### <a name="crawl-the-content-source"></a>Przeszukiwanie źródła zawartości

Aby przywrócić usługę wyszukiwania, należy uruchomić przeszukiwanie pełne dla każdego źródła zawartości. Zwróć uwagę, że utracisz część informacji analitycznych z farmy lokalnej, takich jak zalecenia dotyczące wyszukiwania. Przed rozpoczęciem przeszukiwania pełnego należy użyć polecenia cmdlet **Restore-SPEnterpriseSearchServiceApplication** programu Windows PowerShell oraz określić bazę danych z wysyłką dziennika i zreplikowanej administracji **Search_Service__DB_.\<GUID\>** To polecenie cmdlet udostępnia konfigurację wyszukiwania, schemat, właściwości zarządzane, reguły i źródła oraz tworzy domyślny zestaw pozostałych składników.

Aby rozpocząć przeszukiwanie pełne, wykonaj następujące czynności:

1. W administracji centralnej programu SharePoint 2013 przejdź do strony Application **ManagementService** >  **ApplicationsZa** >  zarządzanie aplikacjami usług, a następnie kliknij aplikację usługi wyszukiwania, którą chcesz przeszukać.

2. Na stronie **Administracja wyszukiwania** kliknij pozycję **Źródła** zawartości, wskaż szukane źródło zawartości, kliknij strzałkę, a następnie kliknij pozycję **Rozpocznij przeszukiwanie pełne**.

### <a name="recover-farm-services"></a>Odzyskiwanie usług farmy

W poniższej tabeli pokazano, jak odzyskać usługi, które mają bazy danych z wysyłką dziennika, usługi, które zawierają bazy danych, ale nie są zalecane do przywrócenia przy użyciu wysyłki dziennika, oraz usługi, które nie mają baz danych.

> [!IMPORTANT]
> Przywracanie lokalnej bazy danych programu SharePoint do środowiska platformy Azure nie spowoduje odzyskania żadnych SharePoint danych, które nie zostały jeszcze ręcznie zainstalowane na platformie Azure.

**Tabela: Informacje o bazie danych aplikacji usługi**

|Przywracanie tych usług z bazy danych wysyłanych w dzienniku|Te usługi zawierają bazy danych, ale zalecamy uruchomienie tych usług bez przywracania ich baz danych.|Te usługi nie przechowują danych w bazach danych. uruchom te usługi po uruchomieniu trybu failover|
|---|---|---|
|Usługa tłumaczenia maszynowego <br/> Zarządzane Usługa przesyłania metadanych <br/> Usługa bezpiecznego magazynu <br/> Profil użytkownika. (Obsługiwane są tylko bazy danych profilów i otagów społecznościowych. Baza danych synchronizacji nie jest obsługiwana). <br/> Subskrypcja SharePoint Microsoft Ustawienia Foundation|Zbieranie danych dotyczących użycia i kondycji <br/> Usługa województwa <br/> Automatyzacja programu Word|Usługi programu Excel <br/> Usługi programu PerformancePoint <br/> PowerPoint konwersji <br/> usługa grafiki programu Visio <br/> Zarządzanie pracą|

W poniższym przykładzie pokazano, jak przywrócić usługę zarządzanych metadanych z bazy danych.

W ten sposób zostanie używana istniejąca Managed_Metadata_DB danych. Ta baza danych jest dostarczana, ale na farmie pomocniczej nie ma aktywnej aplikacji usługi, więc musi być połączona, gdy aplikacja usługi będzie w miejscu.

Najpierw użyj przycisku  `New-SPMetadataServiceApplication`, a następnie  `DatabaseName` określ przełącznik z nazwą przywróconej bazy danych.

Następnie skonfiguruj nową aplikację zarządzaną usługi Usługa przesyłania metadanych na serwerze pomocniczym w następujący sposób:

- Nazwa: Zarządzane Usługa przesyłania metadanych

- Serwer bazy danych: nazwa bazy danych z dziennika transakcji wysłanych

- Nazwa bazy danych: Managed_Metadata_DB

- Pula aplikacji: aplikacje SharePoint usług

### <a name="manage-dns-records"></a>Zarządzanie rekordami DNS

Musisz ręcznie utworzyć rekordy DNS, aby wskazać Farmę SharePoint danych.

W większości przypadków, gdy masz wiele serwerów frontoronu sieci Web, warto skorzystać z funkcji równoważenia obciążenia sieci w programie Windows Server 2012 lub narzędzia do równoważenia obciążenia sprzętu do rozpowszechniania żądań między serwerami front frontu sieci Web w farmie. Równoważenie obciążenia sieci może również zmniejszyć ryzyko dzięki rozpowszechnianiu żądań na innych serwerach w przypadku awarii jednego z serwerów front frontu sieci Web.

Zazwyczaj podczas konfiguracji równoważenia obciążenia sieciowego do klastrów jest przypisywany jeden adres IP. Następnie należy utworzyć rekord hosta DNS u dostawcy DNS dla swojej sieci, który wskazuje klaster. W przypadku tego projektu umieściliśmy serwer DNS na platformie Azure w celu zapewnienia odporności na wypadek awarii lokalnego centrum danych. Na przykład możesz utworzyć rekord DNS w Menedżerze DNS w usłudze Active Directory,  `https://sharepoint.contoso.com`na przykład o nazwie , który wskazuje adres IP Twojego klastru z obciążeniem zrównoważonym.

Aby uzyskać dostęp zewnętrzny do farmy SharePoint, możesz utworzyć rekord hosta na zewnętrznym serwerze DNS, który będzie zawierał ten sam adres URL, który będzie przez klientów używać w Intranecie (`https://sharepoint.contoso.com`na przykład), który wskazuje zewnętrzny adres IP w zaporze. (Najlepszym rozwiązaniem w tym przykładzie jest skonfigurowanie podzielonego systemu DNS tak, aby wewnętrzny serwer DNS był autorytatywny `contoso.com` dla żądań i rozsyłał żądania bezpośrednio do klastrów farmy usługi SharePoint, a nie do zewnętrznego serwera DNS). Następnie możesz zamapować zewnętrzny adres IP na wewnętrzny adres IP Twojego klastru lokalnego, aby klienci szukali zasobów.

W tym miejscu możesz mieć kilka różnych scenariuszy odzyskiwania po awarii:

 **Przykładowy scenariusz: Lokalna farma SharePoint jest niedostępna z powodu awarii sprzętu w lokalnej SharePoint farmie.** W takim przypadku po zakończeniu procedury trybu failover na farmie usługi Azure SharePoint możesz skonfigurować równoważenie obciążenia sieci na serwerach frontu sieci Web farmy odzyskiwania usługi SharePoint, tak jak w przypadku farmy lokalnej. Następnie możesz przekierować rekord hosta u wewnętrznego dostawcy DNS, aby wskazać adres IP farmy odzyskiwania dla farmy odzyskiwania. Pamiętaj, że odświeżenie rekordów DNS w pamięci podręcznej klientów i wskazanie farmy odzyskiwania może zająć trochę czasu.

 **Przykładowy scenariusz: Lokalne centrum danych zostanie całkowicie utracone.** Ten scenariusz może wystąpić ze względu na klęskę żywiołową, taką jak powódź lub powódź. W takim przypadku w przypadku przedsiębiorstwa pomocnicze centrum danych jest prawdopodobnie hostowane w innym regionie, a także podsieci platformy Azure, która ma własne usługi katalogowe i system DNS. Tak jak w poprzednim scenariuszu awarii, możesz przekierować wewnętrzne i zewnętrzne rekordy DNS, aby wskazać farmę usług Azure SharePoint farmy. Warto również zauważyć, że propagacja rekordów DNS może trochę potrwać.

Jeśli używasz zbiorów witryn nazwanych przez hosta zgodnie z zaleceniami w architekturze i wdrożeniu zbioru witryn nazwanego przez hosta [(SharePoint 2013),](/SharePoint/administration/host-named-site-collection-architecture-and-deployment) w farmie usługi SharePoint może być hostowanych kilka zbiorów witryn z unikatowymi nazwami DNS ( `https://sales.contoso.com` `https://marketing.contoso.com`na przykład ). W takim przypadku możesz utworzyć rekordy DNS dla każdego zbioru witryn, które wskazują twój adres IP klastrów. Gdy żądanie dotrze do Twojego SharePoint frontoronu sieci Web, przekieruje je do odpowiedniego zbioru witryn.

## <a name="microsoft-proof-of-concept-environment"></a>Środowisko weryfikacji koncepcji firmy Microsoft

Zaprojektowaliśmy i przetestowaliśmy środowisko weryfikacji koncepcji dla tego rozwiązania. Celem projektu w naszym środowisku testowym było wdrożenie i odzyskanie farmy SharePoint, która może zostać znajdzie w środowisku klienta. Wyczyszczyliśmy kilka założeń, ale wiedzieliśmy, że farma jest potrzebna do zapewnienia wszystkich funkcji, które są dostępne, bez żadnych dostosowań. Topologia została zaprojektowana pod kątem wysokiej dostępności przy użyciu wskazówek najlepszego rozwiązania dostępnych w polu i grupie produktów.

W poniższej tabeli opisano maszyny wirtualne hyper-V, które zostały utworzone i skonfigurowane dla lokalnego środowiska testowego.

**Tabela: Maszyny wirtualne do testowania lokalnego**

|Nazwa serwera|Rola|Konfiguracja|
|---|---|---|
|DC1|Kontroler domeny z usługą Active Directory.|Dwa procesory <br/> Od 512 MB do 4 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|
|RRAS|Serwer skonfigurowany z rolą Routing i usługa dostępu zdalnego (RRAS).|Dwa procesory <br/> 2-8 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|
|FS1|Serwer plików z udziałami dla kopii zapasowych i punktem końcowy usługi DFSR.|Cztery procesory <br/> 2-12 GB pamięci RAM <br/> 1 x 127 GB dysku twardego <br/> 1 x 1 TB dysku twardego (SAN) <br/> Dysk twardy 1 x 750 GB|
|SP-WFE1, SP-WFE2|Front-end web servers (Front-end web servers).|Cztery procesory <br/> 16 GB pamięci RAM|
|SP-APP1, SP-APP2, SP-APP3|Serwery aplikacji.|Cztery procesory <br/> 2–16 GB pamięci RAM|
|SP-SQL-HA1, SP-SQL-HA2|Serwery baz danych skonfigurowane z grupami SQL Server 2012 AlwaysOn w celu zapewnienia wysokiej dostępności. W tej konfiguracji jako repliki podstawowej i pomocniczej SQL SP-SQL-HA2 używane są sp-SQL-HA1 i SP-ha2.|Cztery procesory <br/> 2–16 GB pamięci RAM|

W poniższej tabeli opisano konfiguracje dysków dla maszyn wirtualnych funkcji Hyper-V, które zostały przez nas utworzone i skonfigurowane dla frontologu serwerów sieci Web i aplikacji dla lokalnego środowiska testowego.

**Tabela: Wymagania dotyczące dysków maszyn wirtualnych dla serwerów front end w sieci Web i aplikacji w teście lokalnym**

|Litera dysku|Rozmiar|Nazwa katalogu|Ścieżka|
|---|---|---|---|
|C|80|Dysk systemowy|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\|
|E|80|Dysk dziennika (40 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|80|Strona (36 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQLDATA\\|

W poniższej tabeli opisano konfiguracje dysków dla maszyn wirtualnych funkcji Hyper-V, które zostały utworzone i skonfigurowane jako serwery lokalnych baz danych. Na stronie **Konfiguracja aparatu bazy** danych dostęp do **karty Katalogi** danych umożliwia ustawienie i potwierdzenie ustawień pokazanych w poniższej tabeli.

**Tabela: Wymagania dotyczące dysków maszyn wirtualnych dla serwera bazy danych w celu przetestowania lokalnego**

|Litera dysku|Rozmiar|Nazwa katalogu|Ścieżka|
|---|---|---|---|
|C|80|Katalog główny danych|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\|
|E|500|Katalog bazy danych użytkowników|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|500|Katalog dziennika bazy danych użytkowników|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|G|500|Katalog temp db|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|H|500|Katalog dziennika temp db|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|

### <a name="setting-up-the-test-environment"></a>Konfigurowanie środowiska testowego

W różnych fazach wdrażania zespół testowy zazwyczaj najpierw pracował nad architekturą lokalną, a następnie w odpowiednim środowisku platformy Azure. Odzwierciedla to ogólne przypadki, w których farmy produkcyjne w domu są już uruchomione. Co jeszcze ważniejsze, należy znać bieżące obciążenie produkcyjne, wydajność i typową wydajność. Oprócz modelu odzyskiwania po awarii, który może spełniać wymagania biznesowe, należy określić rozmiar serwerów farmy odzyskiwania, aby zapewnić minimalny poziom usługi. W cold or warm standby environment, a recovery farma jest zazwyczaj mniejsza niż farma produkcyjna. Gdy farma odzyskiwania jest stabilna i jest w produkcji, można ją skalować w celu spełnienia wymagań dotyczących obciążenia pracą.

Nasze środowisko testowe wdrożono w następujących trzech fazach:

- Konfigurowanie infrastruktury hybrydowej

- Inicjowanie obsługi administracyjnej serwerów

- Wdrażanie farm SharePoint farm

#### <a name="set-up-the-hybrid-infrastructure"></a>Konfigurowanie infrastruktury hybrydowej

Ten etap oznaczał skonfigurowanie środowiska domeny dla farmy lokalnej i farmy odzyskiwania na platformie Azure. Poza normalnymi zadaniami skojarzonymi z konfigurowaniem usługi Active Directory zespół testowy zaimplementował rozwiązanie routingu i połączenie VPN między tymi dwoma środowiskami.

#### <a name="provision-the-servers"></a>Inicjowanie obsługi administracyjnej serwerów

Oprócz serwerów farmy konieczne było inicjowanie obsługi serwerów dla kontrolerów domeny i konfigurowanie serwera do obsługi RRAS, a także sieci VPN dla witrynie. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.

#### <a name="deploy-the-sharepoint-farms"></a>Wdrażanie farm SharePoint farm

Farmy SharePoint wdrożono w dwóch etapach w celu uproszczenia stabilizacji środowiska i rozwiązania w razie potrzeby. Podczas pierwszego etapu wdrożono każdą farmę na minimalnej liczbie serwerów dla każdej warstwy topologii w celu obsługi wymaganej funkcji.

Serwery baz danych z zainstalowanymi SQL Server przed utworzeniem serwerów w SharePoint 2013. Ponieważ było to nowe wdrożenie, grupy dostępności utworzono przed wdrożeniem nowego SharePoint. Utworzono trzy grupy na podstawie wskazówek najlepszego rozwiązania firmy MCS.

> [!NOTE]
> Utwórz zastępcze bazy danych, aby można było utworzyć grupy dostępności przed SharePoint instalacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](/SharePoint/administration/configure-an-alwayson-availability-group)

Utworzono farmę i dodano kolejne serwery w następującej kolejności:

- Inicjowanie obsługi SQL-HA1 i SP-SQL-HA2.

- Skonfiguruj usługę AlwaysOn i utwórz trzy grupy dostępności dla farmy.

- Provision SP-APP1 to host Central Administration.

- Provision SP-WFE1 and SP-WFE2 to host the distributed cache.

U używaliśmy  _parametru skipRegisterAsDistributedCachehost_ , gdy **psconfig.exew** wierszu polecenia. Aby uzyskać więcej informacji, zobacz [Planowanie kanałów informacyjnych i usługi distributed cache w programie SharePoint Server 2013](/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service).

W środowisku odzyskiwania powtarzaliśmy następujące czynności:

- Inicjowanie obsługi administracyjnej SQL-HA1 i AZ-SQL-HA2.

- Skonfiguruj usługę AlwaysOn i utwórz trzy grupy dostępności dla farmy.

- Provision AZ-APP1 to host Central Administration.

- Provision AZ-WFE1 and AZ-WFE2 to host the distributed cache.

Po skonfigurowaniu rozproszonej pamięci podręcznej, dodaniu testowych użytkowników i zawartości testowej rozpoczęliśmy etap drugi wdrożenia. Wymaga to skalowania warstw i konfigurowania serwerów farm w celu obsługi topologii wysokiej dostępności opisanej w architekturze farmy.

W poniższej tabeli opisano maszyny wirtualne, podsieci i zestawy dostępności, które skonfigurujemy dla naszej farmy odzyskiwania.

**Tabela: Infrastruktura farm odzyskiwania**

|Nazwa serwera|Rola|Konfiguracja|Podsieci|Zestaw dostępności|
|---|---|---|---|---|
|spDRAD|Kontroler domeny z usługą Active Directory|Dwa procesory <br/> Od 512 MB do 4 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|sp-ADservers||
|AZ-SP-FS|Serwer plików z udziałami kopii zapasowych i punktem końcowym dla usługi DFSR|Konfiguracja A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM <br/> 1 x 127 GB dysku twardego <br/> 1 x 135 GB dysku twardego <br/> 1 x 127 GB dysku twardego <br/> 1 x 150 GB dysku twardego|sp-databaseservers|DATA_SET|
|AZ-WFE1, AZ -WFE2|Front End Web Servers (Front End Web Servers)|Konfiguracja A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|sp-webservers|WFE_SET|
|AZ -APP1, AZ -APP2, AZ -APP3|Serwery aplikacji|Konfiguracja A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|sp-applicationservers|APP_SET|
|AZ -SQL-HA1, AZ -SQL-HA2|Serwery baz danych oraz repliki podstawowe i pomocnicze dla grup dostępności AlwaysOn|Konfiguracja A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM|sp-databaseservers|DATA_SET|

### <a name="operations"></a>Operacje

Po stabilizacji środowisk farmy i ukończeniu testów funkcjonalności zespół testowy uruchomił następujące zadania operacyjne wymagane do skonfigurowania lokalnego środowiska odzyskiwania:

- Skonfiguruj pełne i zróżnicowane kopie zapasowe.

- Skonfiguruj usługę DFSR na serwerach plików, aby transferowały dzienniki transakcji między środowiskiem lokalnym a środowiskiem platformy Azure.

- Skonfiguruj wysyłkę dziennika na podstawowym serwerze bazy danych.

- Stabilizacja, weryfikacja i rozwiązywanie problemów związanych z wysyłką dziennika zgodnie z wymaganiami. Obejmuje to identyfikowanie i dokumentowanie wszelkich zachowań, które mogą powodować problemy, takie jak opóźnienie sieciowe, które mogło powodować wysyłkę dziennika lub błędy synchronizacji plików DFSR.

### <a name="databases"></a>Bazy danych

W testach trybu failover biorą udział następujące bazy danych:

- WSS_Content

- ManagedMetadata

- Baza danych profilu

- Synchronizowanie bazy danych

- Social DB

- Centrum typów zawartości (baza danych dla dedykowanego centrum zes jakiekolwiekgo typu zawartości)

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

W tej sekcji wyjaśniono problemy, które wystąpiły podczas testów i ich rozwiązań.

### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Użycie narzędzia do zarządzania magazynami okresów powodowało błąd "Magazyn zarządzanych metadanych lub połączenie nie jest obecnie dostępne".

Upewnij się, że konto puli aplikacji używane przez aplikację sieci Web ma uprawnienie Odczyt dostępu do magazynu terminów.

### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Niestandardowe zestawy terminów nie są dostępne w zbiorze witryn

Sprawdź, czy nie ma brakującego skojarzenia aplikacji usługi między zbiorem witryn zawartości a centrum typów zawartości. Ponadto na ekranie **Zarządzane metadane — \<site collection name\>** właściwości połączenia upewnij się, że ta opcja jest włączona: Ta aplikacja usługi jest domyślną lokalizacją przechowywania dla zestawów terminów **dla określonej kolumny.**

### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Polecenie Get-ADForest Windows PowerShell generuje błąd "Termin "Get-ADForest" nie jest rozpoznawany jako nazwa polecenia cmdlet, funkcji, pliku skryptu lub programu nie można go rozpoznać".

Podczas konfigurowania profilów użytkowników potrzebna jest nazwa lasu usługi Active Directory. W Kreatorze dodawania ról i funkcji upewnij się, że włączono moduł usługi Active Directory dla programu Windows PowerShell (w sekcji Narzędzia administracji zdalnej serwera>Narzędzia administracji rolami **>AD DS i Narzędzia usług AD LDS**). Ponadto uruchom następujące polecenia przed użyciem polecenia **Get-ADForest** , aby upewnić się, że są załadowane zależności oprogramowania.

```powershell
Import-Module ServerManager
Import-Module ActiveDirectory
```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Tworzenie grupy dostępności kończy się niepowodzeniem przy uruchamianiu sesji XEvent\<server name\> AlwaysOn_health ''

Upewnij się, że oba węzły twojego klastra trybu failover znajdują się w stanie "W górę", a nie "Wstrzymano" ani "Zatrzymano".

### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server wysyłki dziennika kończy się niepowodzeniem i błąd o odmowie dostępu podczas próby nawiązania połączenia z udziałem plików

Upewnij się, SQL Server działa w obszarze poświadczeń sieciowych, a nie poświadczeń domyślnych.

### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server wysyłki dziennika oznacza sukces, ale nie są kopiowane żadne pliki

Dzieje się tak, ponieważ domyślną preferencją kopii zapasowej grupy dostępności jest **Preferuj pomocniczo**. Upewnij się, że zamiast podstawowego uruchamiasz zadanie wysyłki dziennika z serwera pomocniczego dla grupy dostępności. w przeciwnym razie zadanie nie powiedzie się bezgłośnie.

### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Automatyczne uruchomienie usługi zarządzanych metadanych (SharePoint lub innej usługi zarządzania metadanymi) nie powiedzie się po zakończeniu instalacji

Uruchamianie usług może potrwać kilka minut w zależności od wydajności i bieżącego ładowania serwera SharePoint sieci. Kliknij ręcznie pozycję **Uruchom dla** usługi i podaj odpowiedni czas uruchamiania podczas sporadycznego odświeżania ekranu Usługi na serwerze w celu monitorowania jej stanu. Jeśli usługa pozostanie zatrzymana, włącz SharePoint diagnostyczne, spróbuj ponownie uruchomić usługę, a następnie sprawdź w dzienniku, czy nie występują błędy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie rejestrowania diagnostycznego w programie SharePoint 2013](/sharepoint/administration/configure-diagnostic-logging).

### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Po zmianie systemu DNS na środowisko trybu failover platformy Azure przeglądarki klienckie nadal używają starego adresu IP SharePoint sieci Web

Zmiana systemu DNS może nie być natychmiast widoczna dla wszystkich klientów. W kliencie testowym wykonaj następujące polecenie z poziomu wiersza polecenia z podwyższonym poziomem uprawnień i ponownie spróbuj uzyskać dostęp do witryny.

```DOS
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Dodatkowe materiały

[Obsługiwane opcje wysokiej dostępności i odzyskiwania po awarii dla SharePoint danych](/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)

[Konfigurowanie SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](/SharePoint/administration/configure-an-alwayson-availability-group)

## <a name="see-also"></a>Zobacz też

[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)
