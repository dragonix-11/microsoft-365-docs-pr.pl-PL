---
title: plan zakończenia wsparcia dla serwera SharePoint Server 2007
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
description: Obsługa serwera SharePoint Server 2007 zakończyła się w październiku 2017 r. W tym artykule przedstawiono opcje uaktualniania, migracji i pomocy technicznej.
ms.openlocfilehash: 260949f73fbb4530436484e70ca39d4e2f99bbcf
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098235"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>plan zakończenia wsparcia dla serwera SharePoint Server 2007

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

**10 października 2017** r. serwer Microsoft Office SharePoint Server 2007 osiągnął koniec wsparcia. Jeśli nie przeprowadzono migracji z programu SharePoint Server 2007 do Microsoft 365 lub nowszej wersji lokalnego serwera SharePoint Server, nadszedł czas, aby rozpocząć planowanie. Ten artykuł zawiera zasoby ułatwiające migrowanie danych do usługi SharePoint Online lub uaktualnianie lokalnego serwera SharePoint.
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *koniec wsparcia* ?

SharePoint Server, podobnie jak większość produktów firmy Microsoft, ma cykl życia pomocy technicznej, podczas którego firma Microsoft udostępnia nowe funkcje, poprawki usterek, poprawki zabezpieczeń itd. Ten cykl życia zazwyczaj trwa 10 lat od początkowej wersji produktu. Koniec tego cyklu życia jest określany jako koniec wsparcia technicznego produktu. Po zakończeniu pomocy technicznej firma Microsoft nie zapewnia już następujących elementów:
  
- Pomoc techniczna dotycząca problemów, które mogą wystąpić.
    
- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
    
- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.
    
- Aktualizacje stref czasowych.
    
Farma SharePoint Server 2007 będzie nadal działać po 10 października 2017 r., ale żadne dalsze aktualizacje, poprawki lub poprawki nie zostaną wydane dla produktu, w tym poprawki/poprawki zabezpieczeń. pomoc techniczna firmy Microsoft w pełni przesunęło swoje wysiłki na rzecz pomocy technicznej na nowsze wersje produktu. Ponieważ instalacja nie jest już obsługiwana ani poprawiana, należy uaktualnić produkt lub przeprowadzić migrację ważnych danych.
  
> [!TIP]
> Jeśli nie zaplanowano jeszcze uaktualnienia lub migracji, zobacz: [SharePoint opcje migracji 2007, aby wziąć pod uwagę](sharepoint-2007-migration-options.md) niektóre przykłady rozpoczęcia. Możesz również wyszukać [partnerów firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249), którzy mogą pomóc w uaktualnieniu lub migracji Microsoft 365 (lub obu).
  
Aby uzyskać więcej informacji na temat serwerów Office 2007 i zakończenia wsparcia technicznego, zobacz [Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Pierwszym przystankiem powinna być [witryna cyklu życia produktu](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). Jeśli masz lokalny produkt firmy Microsoft, który się starzeje, sprawdź datę zakończenia pomocy technicznej, aby zaplanować uaktualnienie lub migrację za rok. Po wybraniu następnego kroku zastanów się, jakie funkcje produktu byłyby wystarczająco dobre, lepsze i najlepsze. Oto przykład: 
  
|**Dobry**|**Lepsze**|**Najlepszych**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint hybrydowe  <br/> |SharePoint Server 2016  <br/> |
| | |SharePoint hybrydowe  <br/> |
   
Jeśli wybierzesz opcję "wystarczająco dobra", wkrótce musisz rozpocząć planowanie kolejnego uaktualnienia po zakończeniu migracji z programu SharePoint Server 2007. 

>[!NOTE] 
>Daty zakończenia wsparcia technicznego mogą ulec zmianie. Sprawdź [witrynę cyklu życia produktu](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>Gdzie mogę iść dalej?

SharePoint Server można zainstalować lokalnie na własnych serwerach. Możesz też użyć usługi SharePoint Online, która jest usługą online, która jest częścią Microsoft 365. Dostępne są następujące opcje:
  
- Migrowanie do usługi SharePoint Online.
    
- Uaktualnij serwer SharePoint lokalnie.
    
- Wykonaj oba powyższe czynności.
    
- Zaimplementuj [rozwiązanie hybrydowe SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
    
Należy pamiętać o ukrytych kosztach związanych z utrzymywaniem farmy serwerów, utrzymywaniem lub migrowaniem dostosowań oraz uaktualnianiem sprzętu, który SharePoint serwera. Posiadanie lokalnej farmy serwerów SharePoint jest satysfakcjonujące, jeśli jest to konieczne. Jeśli jednak uruchamiasz farmę na starszych serwerach SharePoint bez dużych dostosowań, możesz skorzystać z migracji do usługi SharePoint Online.
  
> [!IMPORTANT]
> Istnieje inna opcja, jeśli zawartość w SharePoint 2007 r. jest rzadko używana. Niektórzy administratorzy SharePoint decydują się na utworzenie subskrypcji Microsoft 365, skonfigurowanie nowej witryny SharePoint Online, a następnie odcięcie od SharePoint 2007 r., pobierając tylko podstawowe dokumenty do nowych witryn SharePoint Online. Dane można następnie opróżnić z witryny SharePoint 2007 r. do archiwów. Zastanów się, jak użytkownicy pracują z danymi z instalacji SharePoint 2007. Mogą istnieć kreatywne sposoby zarządzania twoimi potrzebami.
  
|**SharePoint Online (SPO)**|**lokalny serwer SharePoint**|
|:-----|:-----|
|Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)  <br/> |Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)  <br/> |
|Niższy koszt w funduszach (bez zakupów sprzętu)  <br/> |Wyższy koszt w funduszach (sprzęt + devs/admins)  <br/> |
|Jednorazowy koszt migracji  <br/> |Jednorazowy koszt powtórzony na przyszłą migrację  <br/> |
|Niski całkowity koszt posiadania/konserwacji  <br/> |Wysoki całkowity koszt posiadania/konserwacji  <br/> |
   
Podczas migracji do Microsoft 365 jednorazowe przeniesienie będzie miało większy koszt z góry podczas organizowania danych i podejmowania decyzji o tym, co należy zabrać do chmury i co pozostawić. Jednak przyszłe uaktualnienia będą automatyczne i nie będziesz już musiał zarządzać aktualizacjami sprzętu i oprogramowania. Ponadto czas dostępności farmy będzie wspierany przez umowę dotyczącą poziomu usług firmy Microsoft ([SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)).
  
### <a name="migrate-to-sharepoint-online"></a>Migrowanie do usługi SharePoint Online

Upewnij się, że usługa SharePoint Online ma wszystkie potrzebne funkcje. Zobacz [opisy usług Microsoft 365 i Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Nie można migrować bezpośrednio z SharePoint 2007 r. do usługi SharePoint Online. Przejście do usługi SharePoint Online zostałoby wykonane ręcznie. W przypadku uaktualnienia do wersji SharePoint Server 2013 lub SharePoint Server 2016 możesz użyć interfejsu API migracji SharePoint (na przykład do migracji informacji do OneDrive dla Firm).
  
|**Online pro**|**Konfiguracja online**|
|:-----|:-----|
|Firma Microsoft dostarcza sprzęt SPO i całą administrację sprzętem.  <br/> |Dostępne funkcje mogą się różnić w zależności od lokalnego serwera SharePoint i spo.  <br/> |
|Jesteś administratorem programu Sharepoint lub administratorem globalnym subskrypcji i możesz przypisywać administratorów do witryn SPO.  <br/> |Niektóre akcje dostępne dla administratora farmy w środowisku lokalnym SharePoint Server nie istnieją lub nie muszą być uwzględnione w roli administratora SharePoint w Microsoft 365.  <br/> |
|Firma Microsoft stosuje poprawki, poprawki i aktualizacje bazowego sprzętu i oprogramowania. <br/> |Ponieważ nie ma dostępu do podstawowego systemu plików w usłudze, dostosowywanie jest ograniczone.  <br/> |
|Firma Microsoft publikuje [umowy dotyczące poziomu usług](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) i szybko przechodzi do rozwiązywania zdarzeń na poziomie usługi. <br/> |Kopie zapasowe i przywracanie oraz inne opcje odzyskiwania są zautomatyzowane przez usługę w usłudze SharePoint Online. Kopie zapasowe są zastępowane, jeśli nie są używane. <br/> |
|Testy zabezpieczeń i dostrajanie wydajności serwera są przeprowadzane na bieżąco w usłudze przez firmę Microsoft. <br/> |Zmiany interfejsu użytkownika i innych funkcji SharePoint są instalowane przez usługę i mogą wymagać włączania lub wyłączania. <br/> |
|Microsoft 365 spełnia wiele standardów branżowych: [oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home).  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pomoc dotycząca migracji jest ograniczona.  <br/> Znaczna część uaktualnienia będzie wykonywana ręcznie lub za pośrednictwem interfejsu API migracji spo opisanego w [planie migracji zawartości SharePoint Online i OneDrive Migration](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|pomoc techniczna firmy Microsoft inżynierowie i pracownicy centrum danych nie będą mieli nieograniczonego dostępu administratora do Twojej subskrypcji. <br/> |Jeśli sprzęt musi zostać uaktualniony w celu obsługi nowszej wersji SharePoint, mogą wystąpić dodatkowe koszty lub jeśli do uaktualnienia jest wymagana farma pomocnicza.  <br/> |
|Partnerzy mogą pomóc w jednorazowym zadaniu migrowania danych do SharePoint Online.  <br/> ||
|Produkty online są aktualizowane automatycznie. Chociaż funkcje mogą być przestarzałe, nie ma prawdziwego końca obsługi. <br/> ||
   
Jeśli zdecydujesz się utworzyć nową witrynę Microsoft 365 i ręcznie zmigrujesz do niej dane zgodnie z potrzebami, sprawdź [opcje Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie lokalnego serwera SharePoint

Nie ma możliwości pominięcia wersji w SharePoint uaktualnień. Uaktualnienia są uaktualnione szeregowo:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Przejście od SharePoint 2007 r. do SharePoint Server 2016 oznacza znaczną inwestycję w czas i będzie wiązać się z kosztami sprzętu (serwery SQL również muszą zostać uaktualnione), oprogramowanie i administracja. Dostosowania muszą zostać uaktualnione lub porzucone.
  
> [!NOTE]
> Istnieje możliwość utrzymania farmy SharePoint 2007 r., zainstalowania farmy SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i wykonać ręczną migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Ale uważaj na niektóre pułapki ruchów ręcznych, takie jak ruchy dokumentów zastępujących konto ostatnio zmodyfikowane aliasem konta wykonującego ręczne przenoszenie. Należy również wziąć pod uwagę prace, które należy wykonać z wyprzedzeniem, takie jak ponowne tworzenie witryn, podwitryn, uprawnień i struktur listy. Z wyprzedzeniem zastanów się, jakie dane można przenieść do magazynu lub usunąć, aby zmniejszyć wpływ migracji.
  
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
|Pełna kontrola nad wszystkimi aspektami farmy SharePoint od sprzętu serwera do góry.  <br/> |Wszystkie przerwy i poprawki są obowiązkiem firmy (możesz zaangażować płatne pomoc techniczna firmy Microsoft jeśli produkt nie jest po zakończeniu wsparcia).  <br/> |
|Pełny zestaw funkcji lokalnego serwera SharePoint z opcją połączenia farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem hybrydowej.  <br/> |Uaktualnianie, poprawki, poprawki zabezpieczeń i cała konserwacja lokalnie zarządzanego serwera SharePoint Server.  <br/> |
|Pełny dostęp w celu większego dostosowania.  <br/> |[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home) muszą być ręcznie skonfigurowane lokalnie.  <br/> |
|Testowanie zabezpieczeń i dostrajanie wydajności serwera odbywa się w środowisku lokalnym (pod kontrolą użytkownika).  <br/> |Microsoft 365 mogą udostępniać funkcje SharePoint Online, które nie współdziałają z lokalnym serwerem SharePoint.  <br/> |
|Partnerzy mogą pomóc w migracji danych do następnej wersji serwera SharePoint Server (i nie tylko).  <br/> |Lokacje serwera SharePoint nie będą automatycznie używać certyfikatów [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), jak pokazano w SharePoint Online.  <br/> |
|Pełna kontrola nad konwencjami nazewnictwa, tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w lokalnej usłudze SharePoint Server.  <br/> |SharePoint Serwer lokalny jest wrażliwy na cykle życia produktów.  <br/> |
   
### <a name="upgrade-resources"></a>Uaktualnianie zasobów

Upewnij się, że środowisko spełnia wymagania sprzętowe i programowe, a następnie postępuj zgodnie z obsługiwanymi metodami uaktualniania.
  
- **Wymagania dotyczące sprzętu/oprogramowania dla**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Granice i limity oprogramowania dla**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Omówienie procesu uaktualniania dla**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Tworzenie rozwiązania hybrydowego SharePoint między usługą SharePoint Online a środowiskiem lokalnym

Jeśli odpowiedź na potrzeby migracji znajduje się gdzieś pomiędzy samokontrolą oferowaną przez środowisko lokalne a niższym kosztem posiadania oferowanym przez usługę SharePoint Online, możesz połączyć farmy SharePoint Server 2013 lub 2016 z usługą SharePoint Online za pośrednictwem hybrydowych. [Dowiedz się więcej o SharePoint rozwiązaniach hybrydowych](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Jeśli zdecydujesz, że hybrydowa farma SharePoint Server przyniesie korzyści Twojej firmie, zapoznaj się z istniejącymi typami hybryd i sposobem konfigurowania połączenia między lokalną farmą SharePoint a subskrypcją Microsoft 365.
  
| Opcja | Opis |
|:-----|:-----|
[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home)  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pomoc dotycząca migracji jest ograniczona.  <br/> Znaczna część uaktualnienia będzie wykonywana ręcznie lub za pośrednictwem interfejsu API migracji spo opisanego w [planie migracji zawartości SharePoint Online i OneDrive Migration](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|pomoc techniczna firmy Microsoft inżynierowie i pracownicy centrum danych nie mają nieograniczonego dostępu administratora do Twojej subskrypcji.<br/> |Mogą wystąpić dodatkowe koszty, jeśli infrastruktura sprzętowa musi zostać uaktualniona w celu obsługi nowszej wersji SharePoint lub jeśli do uaktualnienia jest wymagana farma pomocnicza.  <br/> |
|Partnerzy mogą pomóc w jednorazowym zadaniu migrowania danych do SharePoint Online.  <br/> ||
|Produkty online są automatycznie aktualizowane w całej usłudze. Chociaż funkcje mogą być przestarzałe, nie ma prawdziwego końca obsługi.<br/> ||
   
Jeśli zdecydujesz się utworzyć nową witrynę Microsoft 365 i ręcznie zmigrujesz do niej dane zgodnie z potrzebami, sprawdź [opcje Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie lokalnego serwera SharePoint

Nie ma możliwości pominięcia wersji w SharePoint uaktualnień. Uaktualnienia są uaktualnione szeregowo:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Przejście od SharePoint 2007 r. do SharePoint Server 2016 będzie oznaczać znaczną inwestycję czasu i będzie wiązać się z kosztami sprzętu (serwery SQL również muszą zostać uaktualnione), oprogramowania i administracji. Dostosowania muszą zostać uaktualnione lub porzucone.
  
> [!NOTE]
> Istnieje możliwość utrzymania farmy SharePoint 2007 r., zainstalowania farmy SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i wykonać ręczną migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Uważaj jednak na potencjalne pułapki ruchów ręcznych, takie jak przenoszenie dokumentów zastępujących ostatnio zmodyfikowane konto aliasem konta wykonującego ręczne przenoszenie, oraz pracę, którą należy wykonać z wyprzedzeniem, taką jak ponowne tworzenie witryn, podwitryn, uprawnień i struktur list. Zastanów się, jakie dane można przenieść do magazynu lub usunąć, aby zmniejszyć wpływ migracji.
  
Wyczyść środowisko przed uaktualnieniem. Upewnij się, że istniejąca farma działa przed uaktualnieniem i na pewno przed likwidacją! 
  
Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Jeśli masz *dostosowania*, ważne jest, aby zaplanować uaktualnienie dla każdego kroku w ścieżce migracji: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Lokalne Pro**|**Lokalna konfiguracja**|
|:-----|:-----|
|Pełna kontrola nad wszystkimi aspektami farmy SharePoint od sprzętu serwera do góry.  <br/> |Wszystkie przerwy i poprawki są odpowiedzialne za firmę. (Możesz skorzystać z płatnych pomoc techniczna firmy Microsoft, jeśli twój produkt nie jest po zakończeniu wsparcia).  <br/> |
|Pełny zestaw funkcji lokalnego serwera SharePoint z opcją połączenia farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem hybrydowej.  <br/> |Uaktualnianie, poprawki, poprawki zabezpieczeń i cała konserwacja lokalnie zarządzanego serwera SharePoint Server.  <br/> |
|Pełny dostęp w celu większego dostosowania.  <br/> |[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home) muszą być ręcznie skonfigurowane lokalnie.  <br/> |
|Testowanie zabezpieczeń i dostrajanie wydajności serwera odbywa się w środowisku lokalnym pod kontrolą użytkownika.  <br/> |Microsoft 365 mogą udostępniać funkcje SharePoint Online, które nie współdziałają z lokalnym serwerem SharePoint  <br/> |
|Partnerzy mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).  <br/> |Lokacje serwera SharePoint nie będą automatycznie używać certyfikatów [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), jak pokazano w SharePoint Online.  <br/> |
|Pełna kontrola nad konwencjami nazewnictwa, tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w lokalnej usłudze SharePoint Server.  <br/> |SharePoint Serwer lokalny jest wrażliwy na cykle życia produktów.  <br/> |
   
### <a name="upgrade-resources"></a>Uaktualnianie zasobów

Upewnij się, że środowisko spełnia wymagania sprzętowe i programowe. Następnie postępuj zgodnie z obsługiwanymi metodami uaktualniania.
  
- **Wymagania dotyczące sprzętu/oprogramowania dla:** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Granice i limity oprogramowania dla:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Omówienie procesu uaktualniania dla:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Tworzenie rozwiązania hybrydowego SharePoint między usługą SharePoint Online a środowiskiem lokalnym

Jeśli odpowiedź na potrzeby migracji znajduje się gdzieś pomiędzy samokontrolą oferowaną przez środowisko lokalne a niższym kosztem posiadania oferowanym przez usługę SharePoint Online, możesz połączyć farmy SharePoint Server 2013 lub 2016 z usługą SharePoint Online za pośrednictwem hybrydowych. [Dowiedz się więcej o rozwiązaniach hybrydowych SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Jeśli zdecydujesz, że hybrydowa farma SharePoint Server przyniesie korzyści Twojej firmie, zapoznaj się z istniejącymi typami hybryd i sposobem konfigurowania połączenia między lokalną farmą SharePoint a subskrypcją Microsoft 365.
  
Dobrym sposobem, aby zobaczyć, jak to działa, jest utworzenie Microsoft 365 środowiska deweloperskiego/testowego, które można skonfigurować za pomocą [przewodników laboratorium testowego](m365-enterprise-test-lab-guides.md). Po uzyskaniu wersji próbnej lub zakupie subskrypcji Microsoft 365 można utworzyć zbiory witryn, sieci Web i biblioteki dokumentów w usłudze SharePoint Online, do której można migrować dane. Możesz przeprowadzić migrację ręcznie, za pomocą interfejsu API migracji lub, jeśli chcesz przeprowadzić migrację zawartości witryny Moja witryna do OneDrive dla Firm, za pomocą kreatora hybrydowego.
  
> [!NOTE]
> Pamiętaj, że aby użyć opcji hybrydowej, farma SharePoint 2007 musi zostać uaktualniona lokalnie do SharePoint Server 2013 lub SharePoint Server 2016.
  
## <a name="related-topics"></a>Tematy pokrewne

[Rozwiązywanie problemów i wznawianie uaktualniania (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[Rozwiązywanie problemów z uaktualnianiem (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[Rozwiązywanie problemów z uaktualnianiem bazy danych w SharePoint 2013 r.](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[Wyszukaj partnerów firmy Microsoft, aby uzyskać pomoc dotyczącą uaktualniania](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md)
