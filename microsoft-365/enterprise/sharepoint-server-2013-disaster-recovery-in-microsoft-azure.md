---
title: Odzyskiwanie po awarii programu SharePoint Server 2013 na platformie Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: scotv
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
description: W tym artykule opisano sposób używania platformy Azure do tworzenia środowiska odzyskiwania po awarii dla lokalnej farmy SharePoint.
ms.openlocfilehash: 1b1951e70cfbecc0f6586e68d7142bc26fb6252f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077413"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Odzyskiwanie po awarii programu SharePoint Server 2013 na platformie Microsoft Azure

 Za pomocą platformy Azure można utworzyć środowisko odzyskiwania po awarii dla lokalnej farmy SharePoint. W tym artykule opisano sposób projektowania i implementowania tego rozwiązania.

 **Obejrzyj wideo z omówieniem odzyskiwania po awarii serwera SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]

 W przypadku wystąpienia awarii SharePoint środowisku lokalnym priorytetem jest szybkie ponowne uruchomienie systemu. Odzyskiwanie po awarii przy użyciu SharePoint jest szybsze i łatwiejsze, gdy środowisko kopii zapasowej jest już uruchomione w Microsoft Azure. W tym filmie wideo wyjaśniono główne pojęcia związane z SharePoint ciepłym środowiskiem trybu failover i uzupełnimy wszystkie szczegóły dostępne w tym artykule.

Skorzystaj z tego artykułu z następującym modelem rozwiązania: **SharePoint odzyskiwanie po awarii w Microsoft Azure**.

[![SharePoint proces odzyskiwania po awarii na platformie Azure.](../media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)

 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) | [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)

## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Korzystanie z usług Azure Infrastructure Services na potrzeby odzyskiwania po awarii

Wiele organizacji nie ma środowiska odzyskiwania po awarii dla SharePoint, co może być kosztowne w przypadku tworzenia i utrzymywania środowiska lokalnego. Usługi Azure Infrastructure Services udostępniają atrakcyjne opcje dla środowisk odzyskiwania po awarii, które są bardziej elastyczne i tańsze niż lokalne alternatywy.

Zalety korzystania z usług Azure Infrastructure Services obejmują:

- **Mniej kosztownych zasobów** Obsługa i płacenie za mniejszą liczbę zasobów niż lokalne środowiska odzyskiwania po awarii. Liczba zasobów zależy od wybranego środowiska odzyskiwania po awarii: rezerwy zimnej, rezerwy ciepłej lub rezerwy gorącej.

- **Większa elastyczność zasobów** W przypadku awarii możesz łatwo skalować w poziomie farmę SharePoint odzyskiwania, aby spełnić wymagania dotyczące obciążenia. Skaluj w poziomie, gdy zasoby nie są już potrzebne.

- **Mniejsze zobowiązanie centrum danych** Użyj usług Azure Infrastructure Services zamiast inwestować w pomocnicze centrum danych w innym regionie.

Istnieją mniej złożone opcje dla organizacji, które dopiero zaczynają korzystać z odzyskiwania po awarii, oraz zaawansowane opcje dla organizacji z wymaganiami o wysokiej odporności. Definicje środowisk chłodnych, ciepłych i rezerwowych na gorąco są nieco inne, gdy środowisko jest hostowane na platformie w chmurze. W poniższej tabeli opisano te środowiska do tworzenia farmy odzyskiwania SharePoint na platformie Azure.

**Tabela: Środowiska odzyskiwania**

|Typ środowiska odzyskiwania|Opis|
|---|---|
|Gorące|Farma o pełnym rozmiarze jest aprowizowana, aktualizowana i uruchomiona w trybie wstrzymania.|
|Ciepłe|Farma jest kompilowana, a maszyny wirtualne są uruchomione i aktualizowane. <br/> Odzyskiwanie obejmuje dołączanie baz danych zawartości, aprowizowanie aplikacji usług i przeszukiwanie zawartości. <br/> Farma może być mniejszą wersją farmy produkcyjnej, a następnie skalowana w poziomie, aby obsługiwać pełną bazę użytkowników.|
|Zimno|Farma jest w pełni skompilowana, ale maszyny wirtualne są zatrzymane. <br/> Obsługa środowiska obejmuje uruchamianie maszyn wirtualnych od czasu do czasu, stosowanie poprawek, aktualizowanie i weryfikowanie środowiska. <br/> Uruchom pełne środowisko w przypadku awarii.|

Ważne jest, aby ocenić cele czasu odzyskiwania (RTO) organizacji i cele punktu odzyskiwania (RPO). Te wymagania określają, które środowisko jest najbardziej odpowiednią inwestycją dla Twojej organizacji.

Wskazówki zawarte w tym artykule opisują sposób implementowania środowiska rezerwy ciepłej. Można również dostosować go do zimnego środowiska rezerwowego, chociaż należy wykonać dodatkowe procedury w celu obsługi tego rodzaju środowiska. W tym artykule nie opisano sposobu implementowania środowiska rezerwy gorącej.

Aby uzyskać więcej informacji na temat rozwiązań odzyskiwania po awarii, zobacz [Pojęcia dotyczące wysokiej dostępności i odzyskiwania po awarii w SharePoint 2013](/SharePoint/administration/high-availability-and-disaster-recovery-concepts) r. i [Wybierz strategię odzyskiwania po awarii dla SharePoint 2013](/SharePoint/administration/plan-for-disaster-recovery) r.

## <a name="solution-description"></a>Opis rozwiązania

Rozwiązanie do odzyskiwania po awarii w trybie rezerwy ciepłej wymaga następującego środowiska:

- Lokalna farma SharePoint produkcyjna

- Farma SharePoint odzyskiwania na platformie Azure

- Połączenie sieci VPN typu lokacja-lokacja między dwoma środowiskami

Na poniższej ilustracji przedstawiono te trzy elementy.

**Rysunek: Elementy rozwiązania rezerwy ciepłej na platformie Azure**

![Elementy SharePoint rozwiązania do rezerwy ciepłej na platformie Azure.](../media/AZarch-AZWarmStndby.png)

SQL Server wysyłania dzienników z rozproszoną replikacją systemu plików (DFSR) służy do kopiowania kopii zapasowych bazy danych i dzienników transakcji do farmy odzyskiwania na platformie Azure:

- Usługa DFSR przesyła dzienniki ze środowiska produkcyjnego do środowiska odzyskiwania. W scenariuszu sieci WAN usługa DFSR jest wydajniejsza niż wysyłanie dzienników bezpośrednio do serwera pomocniczego na platformie Azure.

- Dzienniki są odtwarzane do SQL Server w środowisku odzyskiwania na platformie Azure.

- Nie dołączasz baz danych zawartości przesyłanych z dziennika SharePoint w środowisku odzyskiwania do momentu wykonania ćwiczenia odzyskiwania.

Wykonaj następujące kroki, aby odzyskać farmę:

1. Zatrzymaj wysyłkę dziennika.

2. Zatrzymaj akceptowanie ruchu do farmy podstawowej.

3. Odtwórz końcowe dzienniki transakcji.

4. Dołącz bazy danych zawartości do farmy.

5. Przywracanie aplikacji usług z baz danych usług replikowanych.

6. Zaktualizuj rekordy systemu nazw domen (DNS), aby wskazywały farmę odzyskiwania.

7. Rozpocznij pełne przeszukiwanie.

Zalecamy regularne próby tych kroków i udokumentowanie ich w celu zapewnienia bezproblemowego działania odzyskiwania na żywo. Dołączanie baz danych zawartości i przywracanie aplikacji usług może zająć trochę czasu i zwykle wiąże się z pewną ręczną konfiguracją.

Po wykonaniu odzyskiwania to rozwiązanie udostępnia elementy wymienione w poniższej tabeli.

**Tabela: Cele odzyskiwania rozwiązań**

|Element|Opis|
|---|---|
|Witryny i zawartość|Witryny i zawartość są dostępne w środowisku odzyskiwania.|
|Nowe wystąpienie wyszukiwania|W tym ciepłym rozwiązaniu rezerwy wyszukiwanie nie jest przywracane z baz danych wyszukiwania. Składniki wyszukiwania w farmie odzyskiwania są skonfigurowane tak podobnie jak to możliwe do farmy produkcyjnej. Po przywróceniu witryn i zawartości rozpocznie się pełne przeszukiwanie w celu ponownego skompilowania indeksu wyszukiwania. Nie musisz czekać na ukończenie przeszukiwania, aby udostępnić witryny i zawartość.|
|Usług|Usługi, które przechowują dane w bazach danych, są przywracane z baz danych wysyłanych przez dzienniki. Usługi, które nie przechowują danych w bazach danych, są po prostu uruchamiane. <br/> Nie wszystkie usługi z bazami danych muszą zostać przywrócone. Następujące usługi nie muszą być przywracane z baz danych i można je po prostu uruchomić po przejściu w tryb failover: <br/> Zbieranie danych użycia i kondycji <br/> Usługa stanu <br/> Automatyzacja programu Word <br/> Dowolna inna usługa, która nie korzysta z bazy danych|

Możesz współpracować z usługami Microsoft Consulting Services (MCS) lub partnerem w celu osiągnięcia bardziej złożonych celów odzyskiwania. Są one podsumowane w poniższej tabeli.

**Tabela: Inne elementy, które mogą być adresowane przez usługę MCS lub partnera**

|Element|Opis|
|---|---|
|Synchronizowanie niestandardowych rozwiązań farmy|W idealnym przypadku konfiguracja farmy odzyskiwania jest identyczna z farmą produkcyjną. Możesz współpracować z konsultantem lub partnerem w celu oceny, czy niestandardowe rozwiązania farmy są replikowane i czy proces jest wykonywany w celu utrzymania synchronizacji dwóch środowisk.|
|Połączenia ze źródłami danych w środowisku lokalnym|Replikowanie połączeń z systemami danych zaplecza, takich jak połączenia kontrolera domeny kopii zapasowej (BDC) i wyszukiwanie źródeł zawartości, może nie być praktyczne.|
|Scenariusze przywracania wyszukiwania|Ponieważ wdrożenia wyszukiwania w przedsiębiorstwie wydają się być dość unikatowe i złożone, przywracanie wyszukiwania z baz danych wymaga większych inwestycji. Możesz współpracować z konsultantem lub partnerem, aby zidentyfikować i zaimplementować scenariusze przywracania wyszukiwania, których organizacja może wymagać.|

W wytycznych podanych w tym artykule przyjęto założenie, że farma lokalna jest już zaprojektowana i wdrożona.

## <a name="detailed-architecture"></a>Szczegółowa architektura

W idealnym przypadku konfiguracja farmy odzyskiwania na platformie Azure jest taka sama jak lokalna farma produkcyjna, w tym następujące:

- Taka sama reprezentacja ról serwera

- Ta sama konfiguracja dostosowań

- Ta sama konfiguracja składników wyszukiwania

Środowisko na platformie Azure może być mniejszą wersją farmy produkcyjnej. Jeśli planujesz skalowanie farmy odzyskiwania w poziomie po przejściu w tryb failover, ważne jest, aby każdy typ roli serwera był początkowo reprezentowany.

Niektóre konfiguracje mogą nie być praktyczne do replikacji w środowisku trybu failover. Pamiętaj, aby przetestować procedury i środowisko pracy w trybie failover, aby upewnić się, że farma trybu failover zapewnia oczekiwany poziom usługi.

To rozwiązanie nie określa konkretnej topologii dla farmy SharePoint. Celem tego rozwiązania jest użycie platformy Azure dla farmy trybu failover oraz zaimplementowanie wysyłania dzienników i funkcji DFSR między dwoma środowiskami.

### <a name="warm-standby-environments"></a>Ciepłe środowiska rezerwowe

W środowisku rezerwy ciepłej wszystkie maszyny wirtualne w środowisku platformy Azure są uruchomione. Środowisko jest gotowe do ćwiczenia lub zdarzenia trybu failover.

Na poniższej ilustracji przedstawiono rozwiązanie odzyskiwania po awarii z lokalnej farmy SharePoint do farmy SharePoint opartej na platformie Azure, która jest skonfigurowana jako środowisko rezerwy ciepłej.

**Rysunek: Topologia i kluczowe elementy farmy produkcyjnej oraz farma odzyskiwania w stanie wstrzymania ciepłego**

![Topologia farmy SharePoint i farmy odzyskiwania w trybie rezerwy ciepłej.](../media/AZarch-AZWarmStndby.png)

Na tym diagramie:

- Dwa środowiska są zilustrowane obok siebie: lokalna farma SharePoint i farma rezerwy ciepłej na platformie Azure.

- Każde środowisko zawiera udział plików.

- Każda farma zawiera cztery warstwy. Aby osiągnąć wysoką dostępność, każda warstwa obejmuje dwa serwery lub maszyny wirtualne skonfigurowane identycznie dla określonej roli, takie jak usługi frontonu, rozproszona pamięć podręczna, usługi zaplecza i bazy danych. Na tej ilustracji nie jest ważne wywoływanie określonych składników. Te dwie farmy są skonfigurowane identycznie.

- Czwarta warstwa to warstwa bazy danych. Wysyłanie dzienników służy do kopiowania dzienników z pomocniczego serwera bazy danych w środowisku lokalnym do udziału plików w tym samym środowisku.

- Usługa DFSR kopiuje pliki z udziału plików w środowisku lokalnym do udziału plików w środowisku platformy Azure.

- Wysyłanie dzienników odtwarza dzienniki z udziału plików w środowisku platformy Azure do repliki podstawowej w grupie dostępności SQL Server AlwaysOn w środowisku odzyskiwania.

### <a name="cold-standby-environments"></a>Zimne środowiska rezerwowe

W zimnym środowisku rezerwowym większość maszyn wirtualnych farmy SharePoint można zamknąć. (Zalecamy czasami uruchamianie maszyn wirtualnych, na przykład co dwa tygodnie lub raz w miesiącu, aby każda maszyna wirtualna mogła zsynchronizować z domeną). Następujące maszyny wirtualne w środowisku odzyskiwania platformy Azure muszą pozostać uruchomione, aby zapewnić ciągłą operację wysyłania dzienników i usługi DFSR:

- Udział plików

- Podstawowy serwer bazy danych

- Co najmniej jedna maszyna wirtualna z uruchomionymi usługami Windows Server Active Directory Domain Services i DNS

Na poniższej ilustracji przedstawiono środowisko trybu failover platformy Azure, w którym maszyna wirtualna udziału plików i podstawowa maszyna wirtualna bazy danych SharePoint są uruchomione. Wszystkie inne maszyny wirtualne SharePoint są zatrzymane. Nie jest wyświetlana maszyna wirtualna z systemem Windows Server Active Directory i systemem DNS.

**Rysunek: Farma odzyskiwania rezerwy zimnej z uruchomionymi maszynami wirtualnymi**

![Elementy SharePoint zimnego rozwiązania rezerwowego na platformie Azure.](../media/AZarch-AZColdStndby.png)

Po przejściu w tryb failover do zimnego środowiska rezerwowego wszystkie maszyny wirtualne są uruchamiane, a metoda osiągnięcia wysokiej dostępności serwerów baz danych musi zostać skonfigurowana, na przykład SQL Server zawsze włączonych grup dostępności.

Jeśli zaimplementowano wiele grup magazynu (bazy danych są rozłożone na więcej niż jedną SQL Server zestawu wysokiej dostępności), podstawowa baza danych dla każdej grupy magazynu musi być uruchomiona, aby akceptować dzienniki skojarzone z jej grupą magazynów.

### <a name="skills-and-experience"></a>Umiejętności i doświadczenie

W tym rozwiązaniu odzyskiwania po awarii jest używanych wiele technologii. Aby zapewnić, że te technologie współdziałają zgodnie z oczekiwaniami, każdy składnik w środowisku lokalnym i środowisku platformy Azure musi być poprawnie zainstalowany i skonfigurowany. Zalecamy, aby osoba lub zespół, który konfiguruje to rozwiązanie, dysponował silną praktyczną wiedzą i praktycznymi umiejętnościami w zakresie technologii opisanych w następujących artykułach:

- [Rozproszone usługi replikacji systemu plików (DFS)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))

- [Windows Server Failover Clustering (WSFC) z SQL Server](/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)

- [Zawsze włączone grupy dostępności (SQL Server)](/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)

- [Tworzenie kopii zapasowej i przywracanie baz danych SQL Server](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)

- [instalacja i wdrażanie farmy programu SharePoint Server 2013](/SharePoint/install/installation-and-configuration-overview)

- [Microsoft Azure](/azure/)

Na koniec zalecamy wykonywanie skryptów, których można użyć do automatyzacji zadań skojarzonych z tymi technologiami. Dostępne interfejsy użytkownika umożliwiają wykonywanie wszystkich zadań opisanych w tym rozwiązaniu. Jednak ręczne podejście może być czasochłonne i podatne na błędy i zapewnia niespójne wyniki.

Oprócz Windows PowerShell istnieją również biblioteki Windows PowerShell dla SQL Server, SharePoint Server i Platformy Azure. Nie zapomnij o SQL T, co może również pomóc skrócić czas konfigurowania i utrzymywania środowiska odzyskiwania po awarii.

## <a name="disaster-recovery-roadmap"></a>Plan odzyskiwania po awarii

![Wizualna reprezentacja planu odzyskiwania po awarii SharePoint.](../media/Azure-DRroadmap.png)

W tym planie przyjęto założenie, że masz już farmę SharePoint Server 2013 wdrożoną w środowisku produkcyjnym.

**Tabela: Plan odzyskiwania po awarii**

|Fazy|Opis|
|---|---|
|Faza 1|Projektowanie środowiska odzyskiwania po awarii.|
|Faza 2|Utwórz sieć wirtualną platformy Azure i połączenie sieci VPN.|
|Faza 3|Wdróż usługi Windows Active Directory i Domain Name Services w sieci wirtualnej platformy Azure.|
|Faza 4|Wdrażanie farmy odzyskiwania SharePoint na platformie Azure.|
|Faza 5|Skonfiguruj funkcję DFSR między farmami.|
|Faza 6|Skonfiguruj wysyłanie dzienników do farmy odzyskiwania.|
|Faza 7|Weryfikowanie rozwiązań trybu failover i odzyskiwania. Obejmuje to następujące procedury i technologie: <br/> Zatrzymaj wysyłkę dziennika. <br/> Przywróć kopie zapasowe. <br/> Przeszukiwanie zawartości. <br/> Odzyskiwanie usług. <br/> Zarządzanie rekordami DNS.|

## <a name="phase-1-design-the-disaster-recovery-environment"></a>Faza 1. Projektowanie środowiska odzyskiwania po awarii

Skorzystaj ze wskazówek w [temacie architektury Microsoft Azure dla SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) r., aby zaprojektować środowisko odzyskiwania po awarii, w tym farmę odzyskiwania SharePoint. Aby rozpocząć proces projektowania, możesz użyć grafiki w pliku [SharePoint Disaster Recovery Solution na](https://go.microsoft.com/fwlink/p/?LinkId=392554) platformie Azure Visio. Zalecamy zaprojektowanie całego środowiska przed rozpoczęciem pracy w środowisku platformy Azure.

Oprócz wskazówek [zawartych w temacie architektury Microsoft Azure dla SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) r. dotyczące projektowania sieci wirtualnej, połączenia sieci VPN, usługi Active Directory i farmy SharePoint należy dodać rolę udziału plików do środowiska platformy Azure.

Aby obsługiwać wysyłanie dzienników w rozwiązaniu odzyskiwania po awarii, maszyna wirtualna udziału plików jest dodawana do podsieci, w której znajdują się role bazy danych. Udział plików służy również jako trzeci węzeł większości węzła dla grupy dostępności SQL Server AlwaysOn. Jest to zalecana konfiguracja dla standardowej farmy SharePoint, która używa SQL Server zawsze włączonych grup dostępności.

> [!NOTE]
> Ważne jest, aby zapoznać się z wymaganiami wstępnymi dotyczącymi udziału bazy danych w grupie dostępności SQL Server AlwaysOn. Aby uzyskać więcej informacji, zobacz [Wymagania wstępne, ograniczenia i Rekomendacje dla zawsze włączonych grup dostępności](/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability).

**Rysunek: Umieszczanie serwera plików używanego do odzyskiwania po awarii**

![Pokazuje maszynę wirtualną udziału plików dodaną do tej samej usługi w chmurze, która zawiera role serwera SharePoint bazy danych.](../media/AZenv-FSforDFSRandWSFC.png)

Na tym diagramie maszyna wirtualna udziału plików jest dodawana do tej samej podsieci na platformie Azure, która zawiera role serwera bazy danych. Nie należy dodawać maszyny wirtualnej udziału plików do zestawu dostępności z innymi rolami serwera, takimi jak role SQL Server.

Jeśli obawiasz się wysokiej dostępności dzienników, rozważ zastosowanie innego podejścia przy użyciu [SQL Server tworzenia kopii zapasowych i przywracania w usłudze Azure Blob Storage Service](/sql/relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service). Jest to nowa funkcja na platformie Azure, która zapisuje dzienniki bezpośrednio w adresie URL magazynu obiektów blob. To rozwiązanie nie zawiera wskazówek dotyczących korzystania z tej funkcji.

Podczas projektowania farmy odzyskiwania należy pamiętać, że pomyślne środowisko odzyskiwania po awarii dokładnie odzwierciedla farmę produkcyjną, którą chcesz odzyskać. Rozmiar farmy odzyskiwania nie jest najważniejszy w projekcie, wdrożeniu i testowaniu farmy odzyskiwania. Skala farmy różni się w zależności od organizacji w zależności od wymagań biznesowych. Może być możliwe użycie farmy skalowanej w dół w przypadku krótkiej awarii lub do momentu, gdy wymagania dotyczące wydajności i pojemności będą wymagały skalowania farmy.

Skonfiguruj farmę odzyskiwania tak samo, jak to możliwe z farmą produkcyjną, aby spełniała wymagania umowy dotyczącej poziomu usług (SLA) i zapewniała funkcje potrzebne do obsługi twojej firmy. Podczas projektowania środowiska odzyskiwania po awarii przyjrzyj się również procesowi zarządzania zmianami w środowisku produkcyjnym. Zalecamy rozszerzenie procesu zarządzania zmianami na środowisko odzyskiwania przez zaktualizowanie środowiska odzyskiwania w tym samym interwale co środowisko produkcyjne. W ramach procesu zarządzania zmianami zalecamy zachowanie szczegółowego spisu konfiguracji farmy, aplikacji i użytkowników.

## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Faza 2. Tworzenie sieci wirtualnej platformy Azure i połączenia sieci VPN

[Połączenie sieci lokalnej do sieci wirtualnej Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) pokazuje, jak zaplanować i wdrożyć sieć wirtualną na platformie Azure oraz jak utworzyć połączenie sieci VPN. Postępuj zgodnie ze wskazówkami w temacie, aby wykonać następujące procedury:

- Zaplanuj prywatną przestrzeń adresów IP Virtual Network.

- Planowanie zmian infrastruktury routingu dla Virtual Network.

- Planowanie reguł zapory dla ruchu do i z lokalnego urządzenia sieci VPN.

- Utwórz sieć wirtualną między środowiskami na platformie Azure.

- Skonfiguruj routing między siecią lokalną a Virtual Network.

## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Faza 3. Wdrażanie usług Active Directory i Domain Name Services w sieci wirtualnej platformy Azure

Ta faza obejmuje wdrożenie zarówno Windows Server Active Directory, jak i systemu DNS w Virtual Network w scenariuszu hybrydowym zgodnie z opisem w [temacie Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) i jak pokazano na poniższej ilustracji.

**Rysunek: Konfiguracja domeny hybrydowej usługi Active Directory**

![Dwie maszyny wirtualne wdrożone w sieci wirtualnej platformy Azure i podsieć farmy SharePoint to repliki kontrolerów domeny i serwerów DNS.](../media/AZarch-HyADdomainConfig.png)

Na ilustracji dwie maszyny wirtualne są wdrażane w tej samej podsieci. Te maszyny wirtualne obsługują dwie role: Active Directory i DNS.

Przed wdrożeniem usługi Active Directory na platformie Azure przeczytaj [wytyczne dotyczące wdrażania Windows Server Active Directory na platformie Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Te wytyczne ułatwiają określenie, czy potrzebujesz innej architektury, czy różnych ustawień konfiguracji dla rozwiązania.

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania kontrolera domeny na platformie Azure, zobacz [Instalowanie kontrolera domena usługi Active Directory repliki w usłudze Azure Virtual Networks](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).

Przed tą fazą nie wdrożono maszyn wirtualnych w Virtual Network. Maszyny wirtualne do hostowania usług Active Directory i DNS prawdopodobnie nie są największymi maszynami wirtualnymi potrzebnymi do rozwiązania. Przed wdrożeniem tych maszyn wirtualnych najpierw utwórz największą maszynę wirtualną, która ma być używana w Virtual Network. Pomaga to zapewnić, że rozwiązanie trafi na tag na platformie Azure, który pozwala na największy potrzebny rozmiar. Obecnie nie trzeba konfigurować tej maszyny wirtualnej. Po prostu utwórz go i odłóż na bok. Jeśli tego nie zrobisz, możesz napotkać ograniczenie podczas próby utworzenia większych maszyn wirtualnych później, co było problemem podczas pisania tego artykułu.

## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Faza 4. Wdrażanie farmy odzyskiwania SharePoint na platformie Azure

Wdróż farmę SharePoint w Virtual Network zgodnie z planami projektów. Przed wdrożeniem ról SharePoint na platformie Azure warto zapoznać się z tematem [Planowanie SharePoint 2013 w usługach Azure Infrastructure Services](/previous-versions/azure/dn275958(v=azure.100)).

Rozważmy następujące rozwiązania, które poznaliśmy, tworząc nasze środowisko weryfikacji koncepcji:

- Tworzenie maszyn wirtualnych przy użyciu Azure Portal lub programu PowerShell.

- Platforma Azure i funkcja Hyper-V nie obsługują pamięci dynamicznej. Upewnij się, że jest to uwzględniane w planach wydajności i pojemności.

- Uruchom ponownie maszyny wirtualne za pośrednictwem interfejsu platformy Azure, a nie z samego logowania maszyny wirtualnej. Korzystanie z interfejsu platformy Azure działa lepiej i jest bardziej przewidywalne.

- Jeśli chcesz zamknąć maszynę wirtualną w celu zaoszczędzenia kosztów, użyj interfejsu platformy Azure. Jeśli użytkownik zostanie zamknięty z poziomu logowania maszyny wirtualnej, opłaty będą nadal naliczane.

- Użyj konwencji nazewnictwa dla maszyn wirtualnych.

- Zwróć uwagę na lokalizację centrum danych, w której są wdrażane maszyny wirtualne.

- Funkcja automatycznego skalowania na platformie Azure nie jest obsługiwana w przypadku ról SharePoint.

- Nie konfiguruj elementów w farmie, które zostaną przywrócone, takich jak zbiory witryn.

## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Faza 5. Konfigurowanie usługi DFSR między farmami

Aby skonfigurować replikację plików przy użyciu usługi DFSR, użyj przystawki Zarządzanie DNS. Jednak przed konfiguracją usługi DFSR zaloguj się do lokalnego serwera plików i serwera plików platformy Azure i włącz usługę w Windows.

Na pulpicie nawigacyjnym Menedżer serwera wykonaj następujące kroki:

- Skonfiguruj serwer lokalny.

- Uruchom **Kreatora dodawania ról i funkcji**.

- Otwórz węzeł **Plik i usługi Storage**.

- Wybierz pozycję **Przestrzenie nazw systemu plików DFS** i **replikację systemu plików DFS**.

- Kliknij przycisk **Dalej** , aby zakończyć kroki kreatora.

Poniższa tabela zawiera linki do artykułów referencyjnych DFSR i wpisów w blogu.

**Tabela: artykuły referencyjne dotyczące usługi DFSR**

|Tytuł|Opis|
|---|---|
|[Replikacji](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11))|Temat technet zarządzania systemem plików DFS z linkami do replikacji|
|[Replikacja systemu plików DFS: Przewodnik przetrwania](https://go.microsoft.com/fwlink/p/?LinkId=392737)|Witryna typu wiki z linkami do informacji o usłudze DFS|
|[Replikacja systemu plików DFS: często zadawane pytania](/previous-versions/windows/it-pro/windows-server-2003/cc773238(v=ws.10))|Temat technet replikacji systemu plików DFS|
|[Blog Jose Barreto](/archive/blogs/josebda/)|Blog napisany przez głównego menedżera programu w zespole serwera plików w firmie Microsoft|
|[Blog zespołu Storage w firmie Microsoft — file cabinet](https://go.microsoft.com/fwlink/p/?LinkId=392740)|Blog dotyczący usług plików i funkcji magazynu na serwerze Windows|

## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Faza 6. Konfigurowanie wysyłania dzienników do farmy odzyskiwania

Wysyłka dziennika jest kluczowym składnikiem konfigurowania odzyskiwania po awarii w tym środowisku. Wysyłka dziennika umożliwia automatyczne wysyłanie plików dziennika transakcji dla baz danych z wystąpienia podstawowego serwera bazy danych do wystąpienia pomocniczego serwera bazy danych. Aby skonfigurować wysyłanie dzienników, zobacz [Konfigurowanie wysyłania dzienników w SharePoint 2013](/sharepoint/administration/configure-log-shipping) r.

> [!IMPORTANT]
> Obsługa wysyłania dzienników na serwerze SharePoint jest ograniczona do niektórych baz danych. Aby uzyskać więcej informacji, zobacz [Obsługiwane opcje wysokiej dostępności i odzyskiwania po awarii dla baz danych SharePoint (SharePoint 2013 r.).](/SharePoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)

## <a name="phase-7-validate-failover-and-recovery"></a>Faza 7. Weryfikowanie trybu failover i odzyskiwania

Celem tej ostatniej fazy jest sprawdzenie, czy rozwiązanie odzyskiwania po awarii działa zgodnie z planem. W tym celu utwórz zdarzenie trybu failover, które spowoduje zamknięcie farmy produkcyjnej i uruchomienie farmy odzyskiwania jako zamiennika. Scenariusz trybu failover można uruchomić ręcznie lub za pomocą skryptów.

Pierwszym krokiem jest zatrzymanie przychodzących żądań użytkowników dotyczących usług farmy lub zawartości. Można to zrobić, wyłączając wpisy DNS lub zamykając serwery internetowe frontonu. Gdy farma jest "wyłączona", możesz przełączać się w tryb failover do farmy odzyskiwania.

### <a name="stop-log-shipping"></a>Zatrzymaj wysyłkę dziennika

Przed odzyskaniem farmy należy zatrzymać wysyłanie dzienników. Najpierw zatrzymaj wysyłanie dzienników na serwerze pomocniczym na platformie Azure, a następnie zatrzymaj go na serwerze podstawowym w środowisku lokalnym. Użyj następującego skryptu, aby najpierw zatrzymać wysyłanie dzienników na serwerze pomocniczym, a następnie na serwerze podstawowym. Nazwy baz danych w skryptze mogą się różnić w zależności od środowiska.

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

Kopie zapasowe muszą zostać przywrócone w kolejności, w jakiej zostały utworzone. Przed przywróceniem określonej kopii zapasowej dziennika transakcji należy najpierw przywrócić następujące poprzednie kopie zapasowe bez wycofywania niezatwierdzone transakcje (czyli przy użyciu  `WITH NORECOVERY`):

- Pełna kopia zapasowa bazy danych i ostatnia różnicowa kopia zapasowa — przywróć te kopie zapasowe, jeśli istnieją, wykonane przed utworzeniem kopii zapasowej dziennika transakcji. Przed utworzeniem najnowszej pełnej lub różnicowej kopii zapasowej bazy danych baza danych korzystała z modelu odzyskiwania pełnego lub modelu odzyskiwania zarejestrowanego zbiorczo.

- Wszystkie kopie zapasowe dziennika transakcji — przywróć wszystkie kopie zapasowe dziennika transakcji wykonane po utworzeniu pełnej kopii zapasowej bazy danych lub różnicowej kopii zapasowej (jeśli je przywrócisz) i przed utworzeniem kopii zapasowej dziennika transakcji. Kopie zapasowe dzienników muszą być stosowane w sekwencji, w której zostały utworzone, bez żadnych luk w łańcuchu dzienników.

Aby odzyskać bazę danych zawartości na serwerze pomocniczym, tak aby lokacje były renderowane, usuń wszystkie połączenia bazy danych przed odzyskiwaniem. Aby przywrócić bazę danych, uruchom następującą instrukcję SQL.

```SQL
restore database WSS_Content with recovery
```

> [!IMPORTANT]
> W przypadku jawnego używania protokołu T-SQL należy określić opcję **WITH NORECOVERY** lub **WITH RECOVERY** w każdej instrukcji RESTORE, aby wyeliminować niejednoznaczność — jest to bardzo ważne podczas pisania skryptów. Po przywróceniu pełnych i różnicowych kopii zapasowych dzienniki transakcji można przywrócić w SQL Server Management Studio. Ponadto ze względu na to, że wysyłka dziennika jest już zatrzymana, baza danych zawartości jest w stanie wstrzymania, więc należy zmienić stan na pełny dostęp.

W SQL Server Management Studio kliknij prawym przyciskiem myszy bazę danych **WSS_Content**, wskaż pozycję **TasksRestore** > , a następnie kliknij pozycję **Dziennik transakcji** (jeśli nie przywrócono pełnej kopii zapasowej, jest to niedostępne). Aby uzyskać więcej informacji, [zobaczRestore a Transaction Log Backup (SQL Server)](/sql/relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server).

### <a name="crawl-the-content-source"></a>Przeszukiwanie źródła zawartości

Aby przywrócić usługę wyszukiwania, musisz rozpocząć pełne przeszukiwanie dla każdego źródła zawartości. Należy pamiętać, że niektóre informacje analityczne z farmy lokalnej, takie jak zalecenia dotyczące wyszukiwania, tracą pewne informacje analityczne. Przed rozpoczęciem pełnego przeszukiwania użyj polecenia cmdlet Windows PowerShell **Restore-SPEnterpriseSearchServiceApplication** i określ bazę danych administracji wyszukiwania wysyłanej w dzienniku i replikowanej, **Search_Service__DB_\<GUID\>**. To polecenie cmdlet udostępnia konfigurację wyszukiwania, schemat, właściwości zarządzane, reguły i źródła oraz tworzy domyślny zestaw innych składników.

Aby rozpocząć pełne przeszukiwanie, wykonaj następujące kroki:

1. W SharePoint 2013 Administracja centralna przejdź do pozycji **Zarządzanie aplikacjamiZasługi** >  >  **usługiZarządzanie aplikacjami usług**, a następnie kliknij aplikację usługi wyszukiwania, którą chcesz przeszukać.

2. Na stronie **Administracja wyszukiwaniem** kliknij pozycję **Źródła zawartości**, wskaż żądane źródło zawartości, kliknij strzałkę, a następnie kliknij pozycję **Rozpocznij pełne przeszukiwanie**.

### <a name="recover-farm-services"></a>Odzyskiwanie usług farmy

W poniższej tabeli przedstawiono sposób odzyskiwania usług z bazami danych wysyłanych przez dzienniki, usługami, które mają bazy danych, ale nie zaleca się przywracania przy użyciu wysyłania dzienników, oraz usługami, które nie mają baz danych.

> [!IMPORTANT]
> Przywrócenie lokalnej bazy danych SharePoint do środowiska platformy Azure nie spowoduje odzyskania żadnych usług SharePoint, które nie zostały jeszcze zainstalowane ręcznie na platformie Azure.

**Tabela: Dokumentacja bazy danych aplikacji usługi**

|Przywracanie tych usług z baz danych wysyłanych przez dzienniki|Te usługi mają bazy danych, ale zalecamy uruchomienie tych usług bez przywracania ich baz danych|Te usługi nie przechowują danych w bazach danych; uruchamianie tych usług po przejściu w tryb failover|
|---|---|---|
|Usługa tłumaczenia maszynowego <br/> Zarządzana usługa metadanych <br/> Usługa bezpiecznego magazynu <br/> Profil użytkownika. (Obsługiwane są tylko bazy danych profilów i tagów społecznościowych. Baza danych synchronizacji nie jest obsługiwana). <br/> Microsoft SharePoint Foundation Subscription Ustawienia Service|Zbieranie danych użycia i kondycji <br/> Usługa stanu <br/> Automatyzacja programu Word|Usługi programu Excel <br/> Usługi programu PerformancePoint <br/> konwersja PowerPoint <br/> usługa grafiki programu Visio <br/> Zarządzanie pracą|

W poniższym przykładzie pokazano, jak przywrócić usługę zarządzanych metadanych z bazy danych.

Używa to istniejącej bazy danych Managed_Metadata_DB. Ta baza danych jest dostarczana w dzienniku, ale nie ma aktywnej aplikacji usługi w farmie dodatkowej, dlatego musi być połączona po utworzeniu aplikacji usługi.

Najpierw użyj polecenia  `New-SPMetadataServiceApplication`i określ  `DatabaseName` przełącznik o nazwie przywróconej bazy danych.

Następnie skonfiguruj nową aplikację usługi zarządzanych metadanych na serwerze pomocniczym w następujący sposób:

- Nazwa: Zarządzana usługa metadanych

- Serwer bazy danych: nazwa bazy danych z wysłanego dziennika transakcji

- Nazwa bazy danych: Managed_Metadata_DB

- Pula aplikacji: aplikacje usługi SharePoint

### <a name="manage-dns-records"></a>Zarządzanie rekordami DNS

Musisz ręcznie utworzyć rekordy DNS, aby wskazać farmę SharePoint.

W większości przypadków, gdy masz wiele serwerów sieci Web frontonu, warto skorzystać z funkcji równoważenia obciążenia sieciowego w Windows Server 2012 lub sprzętowego modułu równoważenia obciążenia w celu dystrybucji żądań między serwerami frontonu internetowego w farmie. Równoważenie obciążenia sieciowego może również pomóc zmniejszyć ryzyko, dystrybuując żądania na inne serwery w przypadku awarii jednego z serwerów frontonu internetowego.

Zazwyczaj podczas konfigurowania równoważenia obciążenia sieciowego klaster ma przypisany pojedynczy adres IP. Następnie należy utworzyć rekord hosta DNS w dostawcy DNS dla sieci, który wskazuje klaster. (W tym projekcie umieszczamy serwer DNS na platformie Azure w celu zapewnienia odporności w przypadku awarii lokalnego centrum danych). Na przykład można utworzyć rekord DNS w Menedżerze DNS w usłudze Active Directory, na przykład o nazwie  `https://sharepoint.contoso.com`, który wskazuje adres IP klastra o zrównoważonym obciążeniu.

W przypadku dostępu zewnętrznego do farmy SharePoint można utworzyć rekord hosta na zewnętrznym serwerze DNS z tym samym adresem URL, którego klienci używają w intranecie (na przykład `https://sharepoint.contoso.com`), który wskazuje zewnętrzny adres IP w zaporze. (Najlepszym rozwiązaniem, korzystając z tego przykładu, jest skonfigurowanie podzielonego systemu DNS, tak aby wewnętrzny serwer DNS był autorytatywny dla `contoso.com` żądań i kieruje żądania bezpośrednio do klastra farmy SharePoint, zamiast kierować żądania DNS do zewnętrznego serwera DNS). Następnie możesz zamapować zewnętrzny adres IP na wewnętrzny adres IP klastra lokalnego, aby klienci znaleźli zasoby, których szukają.

W tym miejscu może wystąpić kilka różnych scenariuszy odzyskiwania po awarii:

 **Przykładowy scenariusz: lokalna farma SharePoint jest niedostępna z powodu awarii sprzętu w lokalnej farmie SharePoint.** W takim przypadku po wykonaniu kroków przechodzenia w tryb failover do farmy usługi Azure SharePoint można skonfigurować równoważenie obciążenia sieciowego na serwerach frontonu internetowego farmy SharePoint farmy, tak samo jak w przypadku farmy lokalnej. Następnie można przekierować rekord hosta w wewnętrznym dostawcy DNS, aby wskazać adres IP klastra farmy odzyskiwania. Pamiętaj, że może upłynąć trochę czasu, zanim buforowane rekordy DNS na klientach zostaną odświeżone i wskaż farmę odzyskiwania.

 **Przykładowy scenariusz: lokalne centrum danych zostało całkowicie utracone.** Ten scenariusz może wystąpić z powodu klęski żywiołowej, takiej jak pożar lub powódź. W takim przypadku w przypadku przedsiębiorstwa prawdopodobnie będziesz mieć dodatkowe centrum danych hostowane w innym regionie, a także podsieć platformy Azure, która ma własne usługi katalogowe i usługę DNS. Podobnie jak w poprzednim scenariuszu awarii, możesz przekierować wewnętrzne i zewnętrzne rekordy DNS, aby wskazywały farmę SharePoint platformy Azure. Ponownie zwróć uwagę, że propagacja rekordów DNS może zająć trochę czasu.

Jeśli używasz zbiorów witryn o nazwie hosta, zgodnie z zaleceniami w [architekturze zbioru witryn o nazwie hosta i wdrożeniu (SharePoint 2013 r.),](/SharePoint/administration/host-named-site-collection-architecture-and-deployment) w farmie SharePoint może znajdować się kilka zbiorów witryn hostowanych przez tę samą aplikację internetową z unikatowymi nazwami DNS (na przykład `https://sales.contoso.com` i `https://marketing.contoso.com`). W takim przypadku można utworzyć rekordy DNS dla każdego zbioru witryn, który wskazuje adres IP klastra. Gdy żądanie dotrze do SharePoint serwerów frontonu internetowego, obsługują one routing każdego żądania do odpowiedniego zbioru witryn.

## <a name="microsoft-proof-of-concept-environment"></a>Środowisko weryfikacji koncepcji firmy Microsoft

Zaprojektowaliśmy i przetestowaliśmy środowisko weryfikacji koncepcji dla tego rozwiązania. Celem projektu dla naszego środowiska testowego było wdrożenie i odzyskanie farmy SharePoint, którą możemy znaleźć w środowisku klienta. Wprowadziliśmy kilka założeń, ale wiedzieliśmy, że farma musi zapewnić wszystkie wbudowane funkcje bez żadnych dostosowań. Topologia została zaprojektowana pod kątem wysokiej dostępności, korzystając ze wskazówek dotyczących najlepszych rozwiązań z dziedziny i grupy produktów.

W poniższej tabeli opisano maszyny wirtualne funkcji Hyper-V utworzone i skonfigurowane dla lokalnego środowiska testowego.

**Tabela: Maszyny wirtualne do testowania lokalnego**

|Nazwa serwera|Rola|Konfiguracja|
|---|---|---|
|DC1|Kontroler domeny z usługą Active Directory.|Dwa procesory <br/> Od 512 MB do 4 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|
|RRAS|Serwer skonfigurowany z rolą routingu i dostępu zdalnego (RRAS).|Dwa procesory <br/> 2–8 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|
|FS1|Serwer plików z udziałami kopii zapasowych i punktem końcowym dla usługi DFSR.|Cztery procesory <br/> 2–12 GB pamięci RAM <br/> 1 x 127 GB dysku twardego <br/> 1 x 1 TB dysku twardego (SAN) <br/> 1 x 750 GB dysku twardego|
|SP-WFE1, SP-WFE2|Serwery internetowe frontonu.|Cztery procesory <br/> 16 GB pamięci RAM|
|SP-APP1, SP-APP2, SP-APP3|Serwery aplikacji.|Cztery procesory <br/> 2–16 GB pamięci RAM|
|SP-SQL-HA1, SP-SQL-HA2|Serwery baz danych skonfigurowane za pomocą grup dostępności AlwaysOn SQL Server 2012 w celu zapewnienia wysokiej dostępności. W tej konfiguracji używane są repliki podstawowe i pomocnicze SP-SQL-HA1 i SP-SQL-HA2.|Cztery procesory <br/> 2–16 GB pamięci RAM|

W poniższej tabeli opisano konfiguracje dysków dla maszyn wirtualnych funkcji Hyper-V, które zostały utworzone i skonfigurowane dla serwerów sieci Web frontonu i aplikacji dla lokalnego środowiska testowego.

**Tabela: Wymagania dotyczące dysków maszyn wirtualnych dla serwerów sieci Web i aplikacji frontonu na potrzeby testu lokalnego**

|Litera dysku|Rozmiar|Nazwa katalogu|Ścieżka|
|---|---|---|---|
|C|80|Dysk systemowy|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\|
|E|80|Dysk dziennika (40 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|80|Strona (36 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQLDATA\\|

W poniższej tabeli opisano konfiguracje dysków dla maszyn wirtualnych funkcji Hyper-V utworzonych i skonfigurowanych tak, aby służyły jako lokalne serwery bazy danych. Na stronie **Konfiguracja aparatu bazy danych** uzyskaj dostęp do karty **Katalogi danych** , aby ustawić i potwierdzić ustawienia przedstawione w poniższej tabeli.

**Tabela: Wymagania dotyczące dysku maszyny wirtualnej dla serwera bazy danych dla testu lokalnego**

|Litera dysku|Rozmiar|Nazwa katalogu|Ścieżka|
|---|---|---|---|
|C|80|Katalog główny danych|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\|
|E|500|Katalog bazy danych użytkownika|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|500|Katalog dziennika bazy danych użytkownika|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|G|500|Katalog temp DB|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|H|500|Katalog dziennika bazy danych temp|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|

### <a name="setting-up-the-test-environment"></a>Konfigurowanie środowiska testowego

W różnych fazach wdrażania zespół testowy zwykle najpierw pracował nad architekturą lokalną, a następnie nad odpowiednim środowiskiem platformy Azure. Odzwierciedla to ogólne rzeczywiste przypadki, w których lokalne gospodarstwa produkcyjne już działają. Jeszcze ważniejsze jest to, że należy znać bieżące obciążenie produkcyjne, pojemność i typową wydajność. Oprócz tworzenia modelu odzyskiwania po awarii, który może spełniać wymagania biznesowe, należy określić rozmiar serwerów farmy odzyskiwania, aby zapewnić minimalny poziom usługi. W zimnym lub ciepłym środowisku rezerwowym farma odzyskiwania jest zwykle mniejsza niż farma produkcyjna. Gdy farma odzyskiwania jest stabilna i w środowisku produkcyjnym, farmę można skalować w górę i w poziomie, aby spełnić wymagania dotyczące obciążenia.

Nasze środowisko testowe wdrożono w następujących trzech fazach:

- Konfigurowanie infrastruktury hybrydowej

- Aprowizowanie serwerów

- Wdrażanie farm SharePoint

#### <a name="set-up-the-hybrid-infrastructure"></a>Konfigurowanie infrastruktury hybrydowej

Ta faza polegała na skonfigurowaniu środowiska domeny dla farmy lokalnej i farmy odzyskiwania na platformie Azure. Oprócz normalnych zadań związanych z konfigurowaniem usługi Active Directory zespół testowy zaimplementował rozwiązanie routingu i połączenie sieci VPN między dwoma środowiskami.

#### <a name="provision-the-servers"></a>Aprowizowanie serwerów

Oprócz serwerów farmy konieczne było aprowizowanie serwerów dla kontrolerów domeny i skonfigurowanie serwera do obsługi usługi RRAS oraz sieci VPN typu lokacja-lokacja. Dla usługi DFSR aprowizowano dwa serwery plików, a kilka komputerów klienckich zostało aprowizowanych dla testerów.

#### <a name="deploy-the-sharepoint-farms"></a>Wdrażanie farm SharePoint

Farmy SharePoint zostały wdrożone w dwóch etapach w celu uproszczenia stabilizacji środowiska i rozwiązywania problemów, jeśli jest to wymagane. W pierwszym etapie każda farma została wdrożona na minimalnej liczbie serwerów dla każdej warstwy topologii w celu obsługi wymaganych funkcji.

Przed utworzeniem serwerów SharePoint 2013 utworzyliśmy serwery bazy danych z zainstalowanymi SQL Server. Ponieważ było to nowe wdrożenie, utworzeliśmy grupy dostępności przed wdrożeniem SharePoint. Utworzyliśmy trzy grupy na podstawie wskazówek dotyczących najlepszych rozwiązań w usłudze MCS.

> [!NOTE]
> Utwórz zastępcze bazy danych, aby można było tworzyć grupy dostępności przed instalacją SharePoint. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zawsze włączonych grup dostępności SQL Server 2012 dla SharePoint 2013 r](/SharePoint/administration/configure-an-alwayson-availability-group).

Utworzyliśmy farmę i dołączyliśmy do dodatkowych serwerów w następującej kolejności:

- Aprowizowanie usług SP-SQL-HA1 i SP-SQL-HA2.

- Skonfiguruj funkcję AlwaysOn i utwórz trzy grupy dostępności dla farmy.

- Aprowizowanie aplikacji SP-APP1 do hostowania administracji centralnej.

- Aprowizowanie usług SP-WFE1 i SP-WFE2 do hostowania rozproszonej pamięci podręcznej.

Podczas uruchamiania **psconfig.exe** w wierszu polecenia użyliśmy parametru _skipRegisterAsDistributedCachehost_. Aby uzyskać więcej informacji, zobacz [Plan for feeds and the Distributed Cache service in SharePoint Server 2013 (Planowanie kanałów informacyjnych i usługi rozproszonej pamięci podręcznej w programie SharePoint Server 2013](/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service)).

Powtórzyliśmy następujące kroki w środowisku odzyskiwania:

- Aprowizowanie usług AZ-SQL-HA1 i AZ-SQL-HA2.

- Skonfiguruj funkcję AlwaysOn i utwórz trzy grupy dostępności dla farmy.

- Aprowizuj usługę AZ-APP1 do hostowania administracji centralnej.

- Aprowizowanie usług AZ-WFE1 i AZ-WFE2 do hostowania rozproszonej pamięci podręcznej.

Po skonfigurowaniu rozproszonej pamięci podręcznej i dodaniu użytkowników testowych i zawartości testowej rozpoczęliśmy drugi etap wdrożenia. Wymaga to skalowania warstw w poziomie i konfigurowania serwerów farmy w celu obsługi topologii wysokiej dostępności opisanej w architekturze farmy.

W poniższej tabeli opisano maszyny wirtualne, podsieci i zestawy dostępności skonfigurowane dla naszej farmy odzyskiwania.

**Tabela: Infrastruktura farmy odzyskiwania**

|Nazwa serwera|Rola|Konfiguracja|Podsieci|Zestaw dostępności|
|---|---|---|---|---|
|spDRAD|Kontroler domeny z usługą Active Directory|Dwa procesory <br/> Od 512 MB do 4 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|serwery sp-ADservers||
|AZ-SP-FS|Serwer plików z udziałami kopii zapasowych i punktem końcowym dla usługi DFSR|Konfiguracja usługi A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM <br/> 1 x 127 GB dysku twardego <br/> 1 x 135 GB dysku twardego <br/> 1 x 127 GB dysku twardego <br/> 1 x 150 GB dysku twardego|serwery sp-database|DATA_SET|
|AZ-WFE1, AZ -WFE2|Serwery frontonu sieci Web|Konfiguracja usługi A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|sp-webservers|WFE_SET|
|AZ -APP1, AZ -APP2, AZ -APP3|Serwery aplikacji|Konfiguracja usługi A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM <br/> 1 x 127 GB dysku twardego|sp-applicationservers|APP_SET|
|AZ -SQL-HA1, AZ -SQL-HA2|Serwery baz danych i repliki podstawowe i pomocnicze dla zawsze włączonych grup dostępności|Konfiguracja usługi A5: <br/> Dwa procesory <br/> 14 GB pamięci RAM|serwery sp-database|DATA_SET|

### <a name="operations"></a>Operacje

Po ustabilizowaniu środowisk farmy przez zespół testowy i zakończeniu testowania funkcjonalnego uruchomili następujące zadania operacyjne wymagane do skonfigurowania lokalnego środowiska odzyskiwania:

- Konfigurowanie pełnych i różnicowych kopii zapasowych.

- Skonfiguruj usługę DFSR na serwerach plików, które przesyłają dzienniki transakcji między środowiskiem lokalnym a środowiskiem platformy Azure.

- Skonfiguruj wysyłanie dzienników na podstawowym serwerze bazy danych.

- W razie potrzeby stabilizuj, weryfikuj i rozwiąż problemy z wysyłką dziennika. Obejmowało to identyfikowanie i dokumentowanie wszelkich zachowań, które mogą powodować problemy, takie jak opóźnienie sieci, co spowodowałoby błędy wysyłania dzienników lub synchronizacji plików DFSR.

### <a name="databases"></a>Baz danych

Nasze testy trybu failover obejmowały następujące bazy danych:

- WSS_Content

- ManagedMetadata

- Baza danych profilu

- Synchronizowanie bazy danych

- Baza danych społecznościowych

- Centrum typów zawartości (baza danych dedykowanego centrum syndykacji typu zawartości)

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

W sekcji opisano problemy, które napotkaliśmy podczas testowania i ich rozwiązania.

### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Użycie narzędzia do zarządzania magazynem terminów spowodowało błąd "Zarządzany magazyn metadanych lub połączenie jest obecnie niedostępne".

Upewnij się, że konto puli aplikacji używane przez aplikację internetową ma uprawnienie Dostęp do odczytu do magazynu terminów.

### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Niestandardowe zestawy terminów nie są dostępne w zbiorze witryn

Sprawdź brak skojarzenia aplikacji usługi między zbiorem witryn zawartości a centrum typów zawartości. Ponadto na ekranie **Właściwości zarządzanych metadanych — \<site collection name\> połączenie** upewnij się, że ta opcja jest włączona: **ta aplikacja usługi jest domyślną lokalizacją magazynu dla zestawów terminów specyficznych dla kolumn.**

### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Polecenie Get-ADForest Windows PowerShell generuje błąd "Termin "Get-ADForest" nie jest rozpoznawany jako nazwa polecenia cmdlet, funkcji, pliku skryptu lub działającego programu."

Podczas konfigurowania profilów użytkowników potrzebna jest nazwa lasu usługi Active Directory. W Kreatorze dodawania ról i funkcji upewnij się, że włączono moduł usługi Active Directory dla Windows PowerShell (w sekcji **Narzędzia administracji zdalnej serwera>Narzędzia administrowania rolami>usług AD DS i AD LDS Tools**). Ponadto przed użyciem polecenia **Get-ADForest** uruchom następujące polecenia, aby upewnić się, że zależności oprogramowania są ładowane.

```powershell
Import-Module ServerManager
Import-Module ActiveDirectory
```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Tworzenie grupy dostępności kończy się niepowodzeniem podczas uruchamiania sesji XEvent "AlwaysOn_health" w dniu "\<server name\>"

Upewnij się, że oba węzły klastra trybu failover mają stan "W górę", a nie "Wstrzymano" lub "Zatrzymano".

### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server zadanie wysyłki dziennika kończy się niepowodzeniem z powodu błędu odmowy dostępu podczas próby nawiązania połączenia z udziałem plików

Upewnij się, że agent SQL Server działa w obszarze poświadczeń sieciowych zamiast poświadczeń domyślnych.

### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server zadanie wysyłki dziennika wskazuje na powodzenie, ale żadne pliki nie są kopiowane

Dzieje się tak, ponieważ domyślną preferencją tworzenia kopii zapasowej dla grupy dostępności jest **Preferuj pomocnicze**. Upewnij się, że zadanie wysyłki dziennika jest uruchamiane z serwera pomocniczego dla grupy dostępności zamiast podstawowej; W przeciwnym razie zadanie zakończy się niepowodzeniem w trybie dyskretnym.

### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Usługa zarządzanych metadanych (lub inna usługa SharePoint) nie może zostać uruchomiona automatycznie po instalacji

Uruchomienie usług może potrwać kilka minut, w zależności od wydajności i bieżącego obciążenia serwera SharePoint. Ręcznie kliknij przycisk **Uruchom** dla usługi i podaj odpowiedni czas na uruchamianie, od czasu do czasu odświeżając ekran Usługi na serwerze, aby monitorować jej stan. W przypadku zatrzymania usługi włącz SharePoint rejestrowanie diagnostyczne, spróbuj uruchomić usługę ponownie, a następnie sprawdź dziennik pod kątem błędów. Aby uzyskać więcej informacji, zobacz [Konfigurowanie rejestrowania diagnostycznego w SharePoint 2013 r](/sharepoint/administration/configure-diagnostic-logging).

### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Po zmianie systemu DNS na środowisko trybu failover platformy Azure przeglądarki klienckie nadal używają starego adresu IP dla SharePoint lokacji

Zmiana dns może nie być widoczna dla wszystkich klientów natychmiast. Na kliencie testowym wykonaj następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień i spróbuj ponownie uzyskać dostęp do lokacji.

```DOS
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Dodatkowe materiały

[Obsługiwane opcje wysokiej dostępności i odzyskiwania po awarii dla SharePoint baz danych](/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)

[Konfigurowanie zawsze włączonych grup dostępności SQL Server 2012 dla SharePoint 2013 r.](/SharePoint/administration/configure-an-alwayson-availability-group)

## <a name="see-also"></a>Zobacz też

[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)
