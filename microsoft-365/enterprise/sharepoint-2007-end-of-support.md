---
title: Plan zakończenia pomocy technicznej programu SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1.keywords:
- CSH
ms.custom:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
- seo-marvel-apr2020
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: Obsługa programu SharePoint Server 2007 zakończyła się w październiku 2017 r. W tym artykule przedstawiono opcje uaktualniania, migracji i pomocy technicznej.
ms.openlocfilehash: 4678af709c498366c74802e70d17b1380b871143
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941157"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Plan zakończenia pomocy technicznej programu SharePoint Server 2007

*Ten artykuł dotyczy zarówno platformy Microsoft 365 Enterprise, jak i usługi Office 365 Enterprise.*

**10 października 2017** r. program Microsoft Office SharePoint Server 2007 osiągnął koniec wsparcia. Jeśli nie przeprowadzono migracji z programu SharePoint Server 2007 do platformy Microsoft 365 lub nowszej wersji lokalnego programu SharePoint Server, nadszedł czas na rozpoczęcie planowania. Ten artykuł zawiera zasoby ułatwiające migrowanie danych do usługi SharePoint Online lub uaktualnianie lokalnego programu SharePoint Server.
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *koniec wsparcia* ?

Program SharePoint Server, podobnie jak większość produktów firmy Microsoft, ma cykl życia pomocy technicznej, podczas którego firma Microsoft udostępnia nowe funkcje, poprawki usterek, poprawki zabezpieczeń itd. Ten cykl życia zazwyczaj trwa 10 lat od początkowej wersji produktu. Koniec tego cyklu życia jest określany jako koniec wsparcia technicznego produktu. Po zakończeniu pomocy technicznej firma Microsoft nie zapewnia już następujących elementów:
  
- Pomoc techniczna dotycząca problemów, które mogą wystąpić.
    
- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
    
- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.
    
- Aktualizacje stref czasowych.
    
Farma programu SharePoint Server 2007 będzie nadal działać po 10 października 2017 r., ale żadne dalsze aktualizacje, poprawki lub poprawki nie zostaną wydane dla produktu, w tym poprawki/poprawki zabezpieczeń. Pomoc techniczna firmy Microsoft w pełni przeniosła swoje wysiłki na rzecz pomocy technicznej na nowsze wersje produktu. Ponieważ instalacja nie jest już obsługiwana ani poprawiana, należy uaktualnić produkt lub przeprowadzić migrację ważnych danych.
  
> [!TIP]
> Jeśli nie zaplanowano jeszcze uaktualnienia lub migracji, zobacz: [Opcje migracji programu SharePoint 2007, które należy wziąć pod uwagę, aby zapoznać](sharepoint-2007-migration-options.md) się z przykładami rozpoczęcia. Możesz również wyszukać [partnerów firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) , którzy mogą pomóc w uaktualnianiu lub migracji platformy Microsoft 365 (lub obu).
  
Aby uzyskać więcej informacji na temat serwerów pakietu Office 2007 i zakończenia pomocy technicznej, zobacz [Zasoby ułatwiające uaktualnienie z serwerów i klientów pakietu Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Pierwszym przystankiem powinna być [witryna cyklu życia produktu](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). Jeśli masz lokalny produkt firmy Microsoft, który się starzeje, sprawdź datę zakończenia pomocy technicznej, aby zaplanować uaktualnienie lub migrację za rok. Po wybraniu następnego kroku zastanów się, jakie funkcje produktu byłyby wystarczająco dobre, lepsze i najlepsze. Oto przykład: 
  
|**Dobry**|**Lepsze**|**Najlepszych**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint Hybrid  <br/> |SharePoint Server 2016  <br/> |
| | |SharePoint Hybrid  <br/> |
   
Jeśli wybierzesz opcję "wystarczająco dobra", wkrótce musisz rozpocząć planowanie kolejnego uaktualnienia po zakończeniu migracji z programu SharePoint Server 2007. 

>[!NOTE] 
>Daty zakończenia wsparcia technicznego mogą ulec zmianie. Sprawdź [witrynę cyklu życia produktu](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>Gdzie mogę iść dalej?

Program SharePoint Server można zainstalować lokalnie na własnych serwerach. Możesz też użyć usługi SharePoint Online, która jest usługą online, która jest częścią platformy Microsoft 365. Dostępne są następujące opcje:
  
- Migrowanie do usługi SharePoint Online.
    
- Uaktualnij program SharePoint Server lokalnie.
    
- Wykonaj oba powyższe czynności.
    
- Implementowanie rozwiązania [hybrydowego programu SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) .
    
Należy pamiętać o ukrytych kosztach związanych z utrzymywaniem farmy serwerów, utrzymywaniem lub migrowaniem dostosowań oraz uaktualnianiem sprzętu, który jest potrzebny programowi SharePoint Server. Posiadanie lokalnej farmy programu SharePoint Server jest satysfakcjonujące, jeśli jest to konieczne. Jeśli jednak uruchamiasz farmę na starszych serwerach programu SharePoint bez dużych dostosowań, możesz skorzystać z migracji do usługi SharePoint Online.
  
> [!IMPORTANT]
> Istnieje inna opcja, jeśli zawartość programu SharePoint 2007 jest rzadko używana. Niektórzy administratorzy programu SharePoint decydują się na utworzenie subskrypcji platformy Microsoft 365, skonfigurowanie nowej witryny usługi SharePoint Online, a następnie odcięcie od programu SharePoint 2007 w sposób czysty, pobierając tylko podstawowe dokumenty do nowych witryn usługi SharePoint Online. Dane można następnie opróżnić z witryny programu SharePoint 2007 do archiwów. Zastanów się, jak użytkownicy pracują z danymi z instalacji programu SharePoint 2007. Mogą istnieć kreatywne sposoby zarządzania twoimi potrzebami.
  
|**SharePoint Online (SPO)**|**Lokalny program SharePoint Server**|
|:-----|:-----|
|Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)  <br/> |Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)  <br/> |
|Niższy koszt w funduszach (bez zakupów sprzętu)  <br/> |Wyższy koszt w funduszach (sprzęt + devs/admins)  <br/> |
|Jednorazowy koszt migracji  <br/> |Jednorazowy koszt powtórzony na przyszłą migrację  <br/> |
|Niski całkowity koszt posiadania/konserwacji  <br/> |Wysoki całkowity koszt posiadania/konserwacji  <br/> |
   
Podczas migracji na platformę Microsoft 365 jednorazowe przeniesienie będzie miało większy koszt z góry, podczas gdy organizujesz dane i decydujesz, co należy zabrać do chmury i co pozostawić. Jednak przyszłe uaktualnienia będą automatyczne i nie będziesz już musiał zarządzać aktualizacjami sprzętu i oprogramowania. Ponadto czas dostępności farmy będzie wspierany przez umowę dotyczącą poziomu usług firmy Microsoft ([SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)).
  
### <a name="migrate-to-sharepoint-online"></a>Migrowanie do usługi SharePoint Online

Upewnij się, że usługa SharePoint Online ma wszystkie potrzebne funkcje. Zobacz [Opisy usług Microsoft 365 i Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Nie można migrować bezpośrednio z programu SharePoint 2007 do usługi SharePoint Online. Przejście do usługi SharePoint Online zostałoby wykonane ręcznie. W przypadku uaktualnienia do programu SharePoint Server 2013 lub SharePoint Server 2016 możesz użyć interfejsu API migracji programu SharePoint (na przykład do migracji informacji do usługi OneDrive dla Firm).
  
|**Online pro**|**Konfiguracja online**|
|:-----|:-----|
|Firma Microsoft dostarcza sprzęt SPO i całą administrację sprzętem.  <br/> |Dostępne funkcje mogą się różnić między programem SharePoint Server w środowisku lokalnym i spo.  <br/> |
|Jesteś administratorem programu SharePoint lub administratorem globalnym subskrypcji i możesz przypisywać administratorów do witryn SPO.  <br/> |Niektóre akcje dostępne dla administratora farmy w lokalnym programie SharePoint Server nie istnieją lub nie muszą być uwzględnione w roli administratora programu SharePoint w usłudze Microsoft 365.  <br/> |
|Firma Microsoft stosuje poprawki, poprawki i aktualizacje bazowego sprzętu i oprogramowania. <br/> |Ponieważ nie ma dostępu do podstawowego systemu plików w usłudze, dostosowywanie jest ograniczone.  <br/> |
|Firma Microsoft publikuje [umowy dotyczące poziomu usług](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) i szybko przechodzi do rozwiązywania zdarzeń na poziomie usługi. <br/> |Kopie zapasowe i przywracanie oraz inne opcje odzyskiwania są zautomatyzowane przez usługę w usłudze SharePoint Online. Kopie zapasowe są zastępowane, jeśli nie są używane. <br/> |
|Testy zabezpieczeń i dostrajanie wydajności serwera są przeprowadzane na bieżąco w usłudze przez firmę Microsoft. <br/> |Zmiany interfejsu użytkownika i innych funkcji programu SharePoint są instalowane przez usługę i mogą wymagać włączania lub wyłączania. <br/> |
|Platforma Microsoft 365 spełnia wiele standardów branżowych: [oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home).  <br/> |Pomoc [dotycząca rozwiązania FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) dla migracji jest ograniczona.  <br/> Znaczna część uaktualnienia będzie wykonywana ręcznie lub za pośrednictwem interfejsu API migracji spo opisanego w [planie migracji usługi SharePoint Online i oneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Inżynierowie pomocy technicznej firmy Microsoft i pracownicy centrum danych nie będą mieli nieograniczonego dostępu administratora do Twojej subskrypcji. <br/> |Jeśli sprzęt musi zostać uaktualniony w celu obsługi nowszej wersji programu SharePoint, mogą wystąpić dodatkowe koszty, jeśli do uaktualnienia jest wymagana farma pomocnicza.  <br/> |
|Partnerzy mogą pomóc w jednorazowym zadaniu migrowania danych do usługi SharePoint Online.  <br/> ||
|Produkty online są aktualizowane automatycznie. Chociaż funkcje mogą być przestarzałe, nie ma prawdziwego końca obsługi. <br/> ||
   
Jeśli zdecydujesz się utworzyć nową witrynę platformy Microsoft 365 i ręcznie zmigrujesz do niej dane w razie potrzeby, sprawdź [opcje platformy Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie lokalnego programu SharePoint Server

Nie ma możliwości pominięcia wersji w uaktualnieniach programu SharePoint. Uaktualnienia są uaktualnione szeregowo:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Przejście z programu SharePoint 2007 do programu SharePoint Server 2016 oznacza znaczną inwestycję czasu i wiąże się z kosztami sprzętu (serwery SQL również muszą zostać uaktualnione), oprogramowania i administracji. Dostosowania muszą zostać uaktualnione lub porzucone.
  
> [!NOTE]
> Istnieje możliwość utrzymania farmy programu SharePoint 2007, zainstalowania farmy programu SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i ręcznie przeprowadzić migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Ale uważaj na niektóre pułapki ruchów ręcznych, takie jak ruchy dokumentów zastępujących konto ostatnio zmodyfikowane aliasem konta wykonującego ręczne przenoszenie. Należy również wziąć pod uwagę prace, które należy wykonać z wyprzedzeniem, takie jak ponowne tworzenie witryn, podwitryn, uprawnień i struktur listy. Z wyprzedzeniem zastanów się, jakie dane można przenieść do magazynu lub usunąć, aby zmniejszyć wpływ migracji.
  
Przed uaktualnieniem należy wyczyścić środowisko. Przed uaktualnieniem upewnij się, że istniejąca farma działa, a na pewno przed likwidacją!
  
Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Jeśli masz dostosowania, niezwykle ważne jest posiadanie planu dla każdego kroku w ścieżce migracji: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Lokalny pro**|**Lokalna konfiguracja**|
|:-----|:-----|
|Pełna kontrola nad wszystkimi aspektami farmy programu SharePoint od sprzętu serwera do góry.  <br/> |Wszystkie przerwy i poprawki są odpowiedzialne za firmę (możesz skorzystać z płatnej pomocy technicznej firmy Microsoft, jeśli produkt nie jest już po zakończeniu wsparcia).  <br/> |
|Pełny zestaw funkcji lokalnego programu SharePoint Server z opcją połączenia farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem środowiska hybrydowego.  <br/> |Uaktualnianie, poprawki, poprawki zabezpieczeń i cała konserwacja lokalnie zarządzanego programu SharePoint Server.  <br/> |
|Pełny dostęp w celu większego dostosowania.  <br/> |[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home) muszą być ręcznie skonfigurowane lokalnie.  <br/> |
|Testowanie zabezpieczeń i dostrajanie wydajności serwera odbywa się w środowisku lokalnym (pod kontrolą użytkownika).  <br/> |Platforma Microsoft 365 może udostępniać funkcje usługi SharePoint Online, które nie współdziałają ze środowiskiem lokalnym programu SharePoint Server.  <br/> |
|Partnerzy mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).  <br/> |Witryny programu SharePoint Server nie będą automatycznie używać certyfikatów [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) , jak pokazano w usłudze SharePoint Online.  <br/> |
|Pełna kontrola nad konwencjami nazewnictwa, tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w lokalnym programie SharePoint Server.  <br/> |Lokalny program SharePoint Server jest wrażliwy na cykle życia produktu.  <br/> |
   
### <a name="upgrade-resources"></a>Uaktualnianie zasobów

Upewnij się, że środowisko spełnia wymagania sprzętowe i programowe, a następnie postępuj zgodnie z obsługiwanymi metodami uaktualniania.
  
- **Wymagania dotyczące sprzętu/oprogramowania dla**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Granice i limity oprogramowania dla**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)
    
- **Omówienie procesu uaktualniania dla**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Tworzenie rozwiązania hybrydowego programu SharePoint między usługą SharePoint Online i środowiskiem lokalnym

Jeśli odpowiedź na potrzeby migracji znajduje się gdzieś pomiędzy samokontrolą oferowaną przez środowisko lokalne a niższym kosztem posiadania oferowanym przez usługę SharePoint Online, możesz połączyć farmy programu SharePoint Server 2013 lub 2016 z usługą SharePoint Online za pomocą hybryd. [Dowiedz się więcej o rozwiązaniach hybrydowych programu SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Jeśli zdecydujesz, że hybrydowa farma programu SharePoint Server przyniesie korzyści Twojej firmie, zapoznaj się z istniejącymi typami hybryd i sposobem konfigurowania połączenia między lokalną farmą programu SharePoint a subskrypcją platformy Microsoft 365.
  
| Opcja | Opis |
|:-----|:-----|
[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home)  <br/> |Pomoc [dotycząca rozwiązania FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) dla migracji jest ograniczona.  <br/> Znaczna część uaktualnienia będzie wykonywana ręcznie lub za pośrednictwem interfejsu API migracji spo opisanego w [planie migracji usługi SharePoint Online i oneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Inżynierowie pomocy technicznej firmy Microsoft i pracownicy centrum danych nie mają nieograniczonego dostępu administratora do Twojej subskrypcji.<br/> |Mogą wystąpić dodatkowe koszty, jeśli infrastruktura sprzętowa musi zostać uaktualniona w celu obsługi nowszej wersji programu SharePoint lub jeśli do uaktualnienia jest wymagana farma pomocnicza.  <br/> |
|Partnerzy mogą pomóc w jednorazowym zadaniu migrowania danych do usługi SharePoint Online.  <br/> ||
|Produkty online są automatycznie aktualizowane w całej usłudze. Chociaż funkcje mogą być przestarzałe, nie ma prawdziwego końca obsługi.<br/> ||
   
Jeśli zdecydujesz się utworzyć nową witrynę platformy Microsoft 365 i ręcznie zmigrujesz do niej dane w razie potrzeby, sprawdź [opcje platformy Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie lokalnego programu SharePoint Server

Nie ma możliwości pominięcia wersji w uaktualnieniach programu SharePoint. Uaktualnienia są uaktualnione szeregowo:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Przejście z programu SharePoint 2007 do programu SharePoint Server 2016 będzie oznaczać znaczną inwestycję czasu i będzie wiązać się z kosztami sprzętu (serwery SQL również muszą zostać uaktualnione), oprogramowania i administracji. Dostosowania muszą zostać uaktualnione lub porzucone.
  
> [!NOTE]
> Istnieje możliwość utrzymania farmy programu SharePoint 2007, zainstalowania farmy programu SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i ręcznie przeprowadzić migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Uważaj jednak na potencjalne pułapki ruchów ręcznych, takie jak przenoszenie dokumentów zastępujących ostatnio zmodyfikowane konto aliasem konta wykonującego ręczne przenoszenie, oraz pracę, którą należy wykonać z wyprzedzeniem, taką jak ponowne tworzenie witryn, podwitryn, uprawnień i struktur list. Zastanów się, jakie dane można przenieść do magazynu lub usunąć, aby zmniejszyć wpływ migracji.
  
Wyczyść środowisko przed uaktualnieniem. Upewnij się, że istniejąca farma działa przed uaktualnieniem i na pewno przed likwidacją! 
  
Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Jeśli masz *dostosowania*, ważne jest, aby zaplanować uaktualnienie dla każdego kroku w ścieżce migracji: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Lokalny pro**|**Lokalna konfiguracja**|
|:-----|:-----|
|Pełna kontrola nad wszystkimi aspektami farmy programu SharePoint od sprzętu serwera do góry.  <br/> |Wszystkie przerwy i poprawki są odpowiedzialne za firmę. (Jeśli twój produkt nie został po zakończeniu pomocy technicznej, możesz skorzystać z płatnej pomocy technicznej firmy Microsoft).  <br/> |
|Pełny zestaw funkcji lokalnego programu SharePoint Server z opcją połączenia farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem środowiska hybrydowego.  <br/> |Uaktualnianie, poprawki, poprawki zabezpieczeń i cała konserwacja lokalnie zarządzanego programu SharePoint Server.  <br/> |
|Pełny dostęp w celu większego dostosowania.  <br/> |[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home) muszą być ręcznie skonfigurowane lokalnie.  <br/> |
|Testowanie zabezpieczeń i dostrajanie wydajności serwera odbywa się w środowisku lokalnym pod kontrolą użytkownika.  <br/> |Platforma Microsoft 365 może udostępniać funkcje usługi SharePoint Online, które nie współdziałają z lokalnym programem SharePoint Server  <br/> |
|Partnerzy mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).  <br/> |Witryny programu SharePoint Server nie będą automatycznie używać certyfikatów [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) , jak pokazano w usłudze SharePoint Online.  <br/> |
|Pełna kontrola nad konwencjami nazewnictwa, tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w lokalnym programie SharePoint Server.  <br/> |Lokalny program SharePoint Server jest wrażliwy na cykle życia produktu.  <br/> |
   
### <a name="upgrade-resources"></a>Uaktualnianie zasobów

Upewnij się, że środowisko spełnia wymagania sprzętowe i programowe. Następnie postępuj zgodnie z obsługiwanymi metodami uaktualniania.
  
- **Wymagania dotyczące sprzętu/oprogramowania dla:** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Granice i limity oprogramowania dla:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)
    
- **Omówienie procesu uaktualniania dla:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Tworzenie rozwiązania hybrydowego programu SharePoint między usługą SharePoint Online i środowiskiem lokalnym

Jeśli odpowiedź na potrzeby migracji znajduje się gdzieś pomiędzy samokontrolą oferowaną przez środowisko lokalne a niższym kosztem posiadania oferowanym przez usługę SharePoint Online, możesz połączyć farmy programu SharePoint Server 2013 lub 2016 z usługą SharePoint Online za pomocą hybryd. [Dowiedz się więcej o rozwiązaniach hybrydowych programu SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Jeśli zdecydujesz, że hybrydowa farma programu SharePoint Server przyniesie korzyści Twojej firmie, zapoznaj się z istniejącymi typami hybryd i sposobem konfigurowania połączenia między lokalną farmą programu SharePoint a subskrypcją platformy Microsoft 365.
  
Dobrym sposobem na sprawdzenie, jak to działa, jest utworzenie środowiska deweloperskiego/testowego platformy Microsoft 365, które można skonfigurować za pomocą [przewodników laboratorium testowego](m365-enterprise-test-lab-guides.md). Po uzyskaniu wersji próbnej lub zakupie subskrypcji platformy Microsoft 365 możesz utworzyć zbiory witryn, sieci Web i biblioteki dokumentów w usłudze SharePoint Online, do których można migrować dane. Możesz przeprowadzić migrację ręcznie, za pomocą interfejsu API migracji lub, jeśli chcesz przeprowadzić migrację zawartości witryny Moja witryna do usługi OneDrive dla Firm, za pomocą kreatora hybrydowego.
  
> [!NOTE]
> Pamiętaj, że aby użyć opcji hybrydowej, farma programu SharePoint 2007 musi zostać uaktualniona lokalnie do programu SharePoint Server 2013 lub SharePoint Server 2016.
  
## <a name="related-topics"></a>Tematy pokrewne

[Rozwiązywanie problemów i wznawianie uaktualniania (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[Rozwiązywanie problemów z uaktualnianiem (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[Rozwiązywanie problemów z uaktualnianiem bazy danych w programie SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[Wyszukaj partnerów firmy Microsoft, aby uzyskać pomoc dotyczącą uaktualniania](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Zasoby ułatwiające uaktualnienie z serwerów i klientów pakietu Office 2007](upgrade-from-office-2007-servers-and-products.md)
