---
title: Routing za pomocą usługi ExpressRoute dla usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: W tym artykule zapoznaj się z wymaganiami routingu usługi Azure ExpressRoute, obwodami i domenami routingu do używania z usługą Office 365.
ms.openlocfilehash: d6fab2dd9a7e7519eb1f56cebccaf345685cc0cd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019388"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing za pomocą usługi ExpressRoute dla usługi Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Aby właściwie zrozumieć routing ruchu do usługi Office 365 za pomocą usługi Azure ExpressRoute, musisz dobrze poznać podstawowe wymagania dotyczące routingu usługi [ExpressRoute](/azure/expressroute/expressroute-routing) oraz obwody i domeny routingu usługi [ExpressRoute](/azure/expressroute/expressroute-circuit-peerings). Stanowi to podstawy korzystania z usługi ExpressRoute, na Office 365 będą opierać się klienci.
  
Niektóre kluczowe elementy w powyższych artykułach, które należy zrozumieć, to:
  
- Obwody usługi ExpressRoute nie są mapowane na określoną infrastrukturę fizyczną, ale są logicznym połączeniem wykonanym w pojedynczej lokalizacji komunikacji równorzędnej przez firmę Microsoft i dostawcę komunikacji równorzędnej w Twoim imieniu.

- Między obwodem usługi ExpressRoute a kluczem s klienta jest mapowanie 1:1.

- Każdy obwód może obsługiwać dwie niezależne relacje komunikacji równorzędnej (prywatną komunikacji równorzędną na platformie Azure i usługę komunikacji równorzędnej firmy Microsoft). Office 365 komunikacji równorzędnej firmy Microsoft.

- Każdy obwód ma stałą przepustowość, która jest współużytkowania przez wszystkie relacje komunikacji równorzędnej.

- Wszystkie publiczne adresy IPv4 i publiczne numery AS, które będą używane w obwodzie usługi ExpressRoute, muszą być zatwierdzone jako należące do Ciebie lub przypisane wyłącznie do Ciebie przez właściciela zakresu adresów.

- Wirtualne obwody usługi ExpressRoute są globalnie nadmiarowe i będą postępować zgodnie ze standardowymi praktykami routingu BGP. Dlatego w konfiguracji aktywnej/aktywnej zalecamy dwa obwody fizyczne na ruch wychodzący do Twojego dostawcy.

Zobacz stronę [często zadawanych pytań,](/azure/expressroute/expressroute-faqs) aby uzyskać więcej informacji na temat obsługiwanych usług, kosztów i szczegółów konfiguracji. Zobacz artykuł [o lokalizacjach usługi ExpressRoute](/azure/expressroute/expressroute-locations) , aby uzyskać informacje na temat listy dostawców łączności oferujących obsługę komunikacji równorzędnej firmy Microsoft. Nagraliśmy również 10-częściową serię szkoleń dotyczących usługi [Azure ExpressRoute](https://channel9.msdn.com/series/aer) dla usługi Office 365 w ramach kanału 9, aby ułatwić dogłębne wyjaśnienie tych pojęć.
  
## <a name="ensuring-route-symmetry"></a>Zapewnianie symetrii tras

Serwery Office 365 są dostępne zarówno w Internecie, jak i w u usługi ExpressRoute. Te serwery będą preferować przekierowyw ich z powrotem do instalacji lokalnych za pośrednictwem obwodów expressRoute, gdy oba te obwody będą dostępne. Z tego powodu istnieje możliwość wystąpienia asymetrii tras, jeśli ruch z Twojej sieci preferuje trasę przez obwody internetowe. Trasy asymetryczne są problemem, ponieważ urządzenia, które wykonują inspekcję pakietów o stanie, mogą blokować ruch powrotny, który podąża inną ścieżką niż pakiety wychodzące.
  
Niezależnie od tego, czy inicjujesz połączenie z usługą Office 365 Przez Internet, czy przez usługę ExpressRoute, źródło musi być adresem publicznie owalnym. W przypadku wielu klientów korzystających z bezpośredniej komunikacji równorzędnej klienci nie mogą mieć adresów prywatnych, gdzie istnieje możliwość duplikowania ich u innych klientów.
  
Poniżej przedstawiono scenariusze, w których zostanie zainicjowana Office 365 z sieci lokalnej do Twojej sieci lokalnej. Aby uprościć projekt sieci, zalecamy routing następujący po ścieżce internetowej.
  
- Usługi SMTP, takie jak poczta z dzierżawy usługi Exchange Online do hosta lokalnego lub usługi Poczta SharePoint Online wysyłane z usługi SharePoint Online do hosta lokalnego. Protokół SMTP jest używany w szerszym zakresie w obrębie sieci firmy Microsoft niż prefiksy tras udostępniane za pośrednictwem obwodów usługi ExpressRoute, a reklamy lokalnych serwerów SMTP przez usługę ExpressRoute będą powodować błędy w połączeniach z tymi innymi usługami.

- Usługi ADFS podczas sprawdzania poprawności hasła do logowania.

- [Exchange Server wdrożeń hybrydowych](/exchange/exchange-hybrid).

- [SharePoint wyszukiwania hybrydowego feder służącego do wyszukiwania hybrydowego](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint usług łączności biznesowej.](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution)

- [Skype dla firm hybrydowe](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) i/[lub Skype dla firm federacyjną](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype dla firm Łącznik chmury](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Aby firma Microsoft przekierowyła te dwukierunkowe przepływy ruchu z powrotem do Twojej sieci, trasy BGP do Twoich urządzeń lokalnych muszą być udostępnione firmie Microsoft. Podczas anonsowania prefiksów tras do firmy Microsoft przez usługę ExpressRoute należy postępować zgodnie z tymi najlepszymi rozwiązaniami:

1) Nie anonsuj tego samego prefiksu publicznej trasy adresu IP do publicznego Internetu i za pośrednictwem usługi ExpressRoute. Zalecane jest, aby anonsy prefiksu trasy IP BGP do firmy Microsoft przez usługę ExpressRoute pochodziły z zakresu, który w ogóle nie jest ogłaszany w Internecie. Jeśli nie jest to możliwe ze względu na dostępną przestrzeń adresów IP, należy zadbać o to, aby ogłaszać bardziej konkretny zakres przez usługę ExpressRoute niż jakiekolwiek obwody internetowe.

2) Użyj osobnych pul IP NAT na obwód usługi ExpressRoute oddzielonych od obwodów internetowych.

3) Każda trasa ogłaszana do firmy Microsoft będzie przyciągać ruch sieciowy z dowolnego serwera w sieci firmy Microsoft, a nie tylko z tych, dla których trasy są ogłaszane do Twojej sieci przez usługę ExpressRoute. Ogłaszaj trasy tylko na serwerach, na których scenariusze routingu są zdefiniowane i dobrze zrozumiałe dla Twojego zespołu. Ogłaszaj oddzielne prefiksy tras adresów IP w każdym z wielu obwodów usługi ExpressRoute z Twojej sieci.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Wybór aplikacji i funkcji przekierowywu przez expressRoute

Po skonfigurowaniu relacji komunikacji równorzędnej przy użyciu domeny routingu komunikacji równorzędnej firmy Microsoft i zatwierdzeniu jej do uzyskania odpowiedniego dostępu zobaczysz wszystkie usługi PaaS i SaaS dostępne za pośrednictwem usługi ExpressRoute. Usługami Office 365 usługi ExpressRoute można zarządzać za pomocą [społeczności BGP](./bgp-communities-in-expressroute.md) lub filtrów [trasy](/azure/expressroute/how-to-routefilter-portal).
  
Wszystkie funkcje komunikacji Office 365 dostępne przy użyciu komunikacji równorzędnej firmy Microsoft są wymienione w artykule Office 365 [punktów](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) końcowych aplikacji według typu aplikacji i FQDN. Przyczyną używania domeny FQDN w tabelach jest umożliwienie klientom zarządzania ruchem przy użyciu plików PAC lub innych konfiguracji serwera proxy. Zobacz nasz przewodnik dotyczący zarządzania [](./managing-office-365-endpoints.md) punktami Office 365 końcowymi, na przykład plikami PAC.
  
W niektórych sytuacjach u używano domeny z symbolami wieloznacznymi, w której co najmniej jedna podrzędna nazwa FQDN jest ogłaszana inaczej niż domena z symbolami wieloznacznymi wyższego poziomu. Zazwyczaj dzieje się tak, gdy symbol wieloznaczny reprezentuje długą listę serwerów, które są ogłaszane w u usługi ExpressRoute i w Internecie, natomiast niewielki podzbiór miejsc docelowych jest ogłaszany tylko w Internecie lub odwrotnie. W poniższych tabelach porozumiew się, gdzie występują różnice.
  
W poniższej tabeli znajdują się symbole wieloznaczne FQDN, które są ogłaszane zarówno w Internecie, jak i w usłudze Azure ExpressRoute, oraz podrzędne usługi FQDN, które są ogłaszane tylko w Internecie.

|**Domena z symbolami wieloznacznymi ogłaszana w obwodach internetowych i obwodach usługi ExpressRoute**|**Podrzędna fqdn ogłaszana tylko w obwodach internetowych**|
|:-----|:-----|
|\*microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

Zazwyczaj pliki PAC są przeznaczone do wysyłania żądań sieciowych do ogłaszanych punktów końcowych usługi ExpressRoute bezpośrednio do obwodu, a wszystkich innych żądań sieciowych do serwera proxy. Jeśli konfigurujesz taki plik PAC, utwórz go w następującej kolejności:
  
1. Dołącz podrzędne nazwy FQDN z drugiej kolumny powyższej tabeli u góry pliku PAC, wysyłając ruch w kierunku serwera proxy. W artykule na temat zarządzania punktami końcowymi usług sieci Web dla klientów zbudowaliśmy przykładowy plik PAC, [z Office 365 punktami końcowymi](./managing-office-365-endpoints.md).

2. W poniższej sekcji poniżej pierwszej sekcji uwzględnij wszystkie usługi FQQN oznaczone w tym artykule jako ogłaszane w układzie ExpressRoute, wysyłając ruch bezpośrednio do obwodu usługi ExpressRoute.[](./urls-and-ip-address-ranges.md)

3. Uwzględnij wszystkie inne punkty końcowe sieci lub reguły poniżej tych dwóch wpisów, wysyłając ruch w kierunku serwera proxy.

W poniższej tabeli są wyświetlane domeny z symbolami wieloznacznymi, które są ogłaszane tylko w obwodach internetowych, oraz podrzędne domeny FQNS, które są ogłaszane w obwodach internetowych i obwodach usługi Azure ExpressRoute. W przypadku powyższego pliku PAC nazwy FQDN w kolumnie 2 w poniższej tabeli wymieniono jako ogłaszane w u usługi ExpressRoute w linku, do którego się odwołujesz, co oznacza, że powinny one zostać uwzględnione w drugiej grupie wpisów w pliku.

|**Domena z symbolami wieloznacznymi ogłaszana tylko w obwodach internetowych**|**Podrzędna fqdn ogłaszana w obwodach internetowych i obwodach usługi ExpressRoute**|
|:-----|:-----|
|\*office.com  <br/> |\*outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*office.net  <br/> |agent.office.net  <br/> |
|\*office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*outlook.com  <br/> |\*protection.outlook.com  <br/> \*mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing Office 365 przez Internet i usługę ExpressRoute

Aby przekierować Office 365 do aplikacji wybierającej, musisz określić kilka kluczowych czynników.
  
1. Ile przepustowości będzie wymagała aplikacja. Jedyną niezawodną metodą określenia tego czynnika w Twojej organizacji jest próbkowanie istniejącego użycia.

2. W jakich lokalizacjach ruchu wychodzącego ma opuszczać Twoją sieć ruch sieciowy. Należy zaplanować zminimalizowanie opóźnień sieci w przypadku łączności z siecią Office 365, ponieważ będzie to miało wpływ na wydajność. Ponieważ Skype dla firm wideo i głosowe w czasie rzeczywistym, są one narażone na duże opóźnienia w sieci.

3. Jeśli chcesz, aby wszystkie lub niektóre z Twoich lokalizacji sieciowych korzystały z usługi ExpressRoute.

4. Z jakich lokalizacji oferuje usługę ExpressRoute wybrany dostawca sieci.

Po ustaleniu odpowiedzi na te pytania możesz utworzyć obwód usługi ExpressRoute spełniający wymagania dotyczące przepustowości i lokalizacji. Aby uzyskać więcej pomocy w zakresie planowania sieci, zobacz przewodnik Office 365 [dostosowywania](./network-planning-and-performance.md) sieci i analizę przypadku, w jaki firma [Microsoft obsługuje planowanie wydajności sieci](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Przykład 1. Pojedyncza lokalizacja geograficzna
  
Ten przykład jest scenariuszem dla fikcyjnej firmy o nazwie Trey Research, która ma jedną lokalizację geograficzną.
  
Pracownicy firmy Trey Research mogą łączyć się tylko z usługami i witrynami internetowymi, które zostały jawnie dozwolone przez dział zabezpieczeń na para serwerów proxy ruchu wychodzącego, które znajdują się między siecią firmową a jego usługą internetową.
  
Firma Trey Research planuje korzystać z usługi Azure ExpressRoute dla usługi Office 365 i uznaje, że część ruchu, na przykład ruch przeznaczony dla sieci dostarczania zawartości, nie będzie mogła przekierowywała przez usługę ExpressRoute na Office 365 sieci. Ponieważ cały ruch już jest domyślnie przekierowywowyny do urządzeń proxy, żądania te będą nadal działać jak wcześniej. Gdy firma Trey Research ustali, że może spełnić wymagania dotyczące routingu w usłudze Azure ExpressRoute, przechodzi do tworzenia obwodu, konfigurowania routingu i łączenia nowego obwodu usługi ExpressRoute z siecią wirtualną. Po zakończeniu podstawowej konfiguracji usługi Azure ExpressRoute firma Trey Research korzysta z pliku [PAC nr 2](./managing-office-365-endpoints.md), który publikujemy, do kierowania ruchu z danymi klienta za pośrednictwem bezpośredniej usługi ExpressRoute na potrzeby połączeń Office 365 sieciowych.
  
Jak pokazano na poniższym diagramie, firma Trey Office 365 Research spełnia wymóg kierowania ruchu przez Internet oraz podzestawu ruchu przez usługę ExpressRoute przy użyciu kombinacji routingu i zmian konfiguracji serwera proxy ruchu wychodzącego.
  
1. [Publikując plik PAC nr 2](./managing-office-365-endpoints.md), można rozsyłać ruch za pośrednictwem oddzielnego internetowego punktu ruchu wychodzącego dla usługi Azure ExpressRoute dla Office 365.

2. Klienci są skonfigurowani tak, że trasa domyślna prowadzi do serwerów proxy firmy Trey Research.

W tym przykładowym scenariuszu firma Trey Research używa wychodzącego urządzenia proxy. Podobnie klienci, którzy nie korzystają z usługi Azure ExpressRoute dla usługi Office 365, mogą chcieć użyć tej metody do rozsyłania ruchu w oparciu o koszty inspekcji ruchu przeznaczonego dla znanych punktów końcowych o dużej pojemności.
  
Poniżej przedstawiono następujące Exchange Online FQN o największej pojemności dla usług Exchange Online, SharePoint Online i Skype dla firm Online:
  
![Sieć brzegowa klienta usługi ExpressRoute.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>sharepoint.com, \<tenant-name\>-my.sharepoint.com,-\<tenant-name\>\<app\> sharepoint.com

- \*Lync.com wraz z zakresami adresów IP dla ruchu niezwiązywistego z protokołem TCP

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

Dowiedz się więcej [o wdrażaniu ustawień serwera proxy](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) i zarządzaniu nimi Windows 8 sieci Office 365 tym programie nie jest [ograniczany przez serwer proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Pojedynczy obwód usługi ExpressRoute nie ma wysokiej dostępności dla firmy Trey Research. W przypadku awarii nadmiarowej pary urządzeń brzegowych, które obsługują łączność z usługą ExpressRoute, firma Trey nie ma dodatkowego obwodu usługi ExpressRoute, w przypadku których należy przepaść. W ten sposób firma Trey Research jest w kłopotliwej sytuacji, ponieważ połączenie z Internetem w trybie pracy w trybie przeciwnym do wymagane jest ręczne ponowne skonfigurowanie, a w niektórych przypadkach nowe adresy IP. Jeśli firma Trey chce dodać wysoką dostępność, najprostszym rozwiązaniem jest dodanie dodatkowych obwodów usługi ExpressRoute dla każdej lokalizacji i skonfigurowanie obwodów w sposób aktywny/aktywny.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing usługi ExpressRoute dla Office 365 z wieloma lokalizacjami

Ostatni scenariusz, routing Office 365 przez usługę ExpressRoute jest podstawą dla jeszcze bardziej złożonej architektury routingu. Niezależnie od liczby lokalizacji, liczby kontynentów, na których znajdują się te lokalizacje, liczby obwodów usługi ExpressRoute i tak dalej, będzie wymagana możliwość przekierowywu części ruchu do Internetu, a część ruchu przez usługę ExpressRoute.
  
Do dodatkowych pytań, na które muszą odpowiedzieć klienci z wieloma lokalizacjami w wielu regionach geograficznych, należą:
  
1. Czy potrzebujesz obwodu usługi ExpressRoute w każdej lokalizacji? Jeśli używasz usługi Skype dla firm Online lub obawiasz się wrażliwości usługi SharePoint Online lub Exchange Online, zaleca się nadmiarową parę aktywnych/aktywnych obwodów usługi ExpressRoute w każdej lokalizacji. Aby uzyskać więcej szczegółowych Skype dla firm zobacz przewodnik dotyczący jakości multimediów i łączności sieciowej.

2. Jeśli w określonym regionie obwód aplikacji ExpressRoute nie jest dostępny, jak powinien zostać Office 365 ruchu kierowanego?

3. Jaka jest preferowana metoda konsolidowania ruchu w przypadku sieci o wielu małych lokalizacjach?

Każde z nich stanowi unikatowe wyzwanie, które wymaga oceny Twojej sieci i opcji dostępnych przez firmę Microsoft.

|**Kwestie do rozważenia**|**Składniki sieci do oceny**|
|:-----|:-----|
|Obwody w więcej niż jednej lokalizacji  <br/> |Zalecamy co najmniej dwa obwody skonfigurowane w sposób aktywny/aktywny.  <br/> Należy porównać potrzeby w zakresie kosztów, opóźnień i przepustowości.  <br/> Użyj kosztu trasy BGP, plików PAC i nat, aby zarządzać routingiem za pomocą wielu obwodów.  <br/> |
|Routing z lokalizacji bez obwodu usługi ExpressRoute  <br/> |Zalecamy ruch wychodzący i rozpoznawanie nazw DNS tak blisko osoby, która żąda Office 365.  <br/> Aby umożliwić biurom zdalnym odnajdowanie odpowiedniego punktu końcowego, można użyć funkcji przesyłania dalej DNS.  <br/> Klienci w biurze zdalnym muszą mieć dostępną trasę, która zapewnia dostęp do obwodu usługi ExpressRoute.  <br/> |
|Konsolidacja małego biura  <br/> |Należy starannie porównać dostępną przepustowość i użycie danych.  <br/> |

> [!NOTE]
> Firma Microsoft preferuje usługę ExpressRoute przez Internet, jeśli trasa jest dostępna niezależnie od lokalizacji fizycznej.
  
Każde z tych kwestii należy wziąć pod uwagę w przypadku każdej unikatowej sieci. Poniżej znajduje się przykład.
  
### <a name="example-2-multi-geographic-locations"></a>Przykład 2. Wiele lokalizacji geograficznych
  
Ten przykład jest scenariuszem dla fikcyjnej firmy o nazwie "Humongous Insurance", która ma wiele lokalizacji geograficznych.
  
Humongous Insurance ma biura rozproszone po całym świecie. Chcą zaimplementować usługę Azure ExpressRoute dla usługi Office 365, aby większość ruchu Office 365 na bezpośrednich połączeniach sieciowych. Humongous Insurance ma również biura na dwóch dodatkowych kontynentach. Pracownicy biura zdalnego, w którym usługa ExpressRoute nie jest możliwa, będą musieli przekierowywować połączenia z powrotem do jednej lub obu podstawowych obiektów, aby korzystać z połączenia ExpressRoute.
  
Podstawową zasadą jest jak Office 365 ruchu do centrum danych firmy Microsoft. W tym przykładzie firma Humongous Insurance musi zdecydować, czy jej biura zdalne powinny kierowane przez Internet, aby jak najszybciej uzyskać dostęp do centrum danych firmy Microsoft za pośrednictwem dowolnego połączenia, czy też jej biura zdalne powinny kierowane przez sieć wewnętrzną, aby jak najszybciej uzyskać dostęp do centrum danych firmy Microsoft za pośrednictwem połączenia ExpressRoute.
  
Centra danych, sieci i architektura aplikacji firmy Microsoft są zaprojektowane tak, aby przejmowały globalnie nieparzystą komunikację i obsługiwali je w najskuteczniejszy możliwy sposób. Należy do jednej z największych sieci na świecie. Żądania przeznaczone dla Office 365, które pozostają w sieciach klientów dłużej, niż to jest konieczne, nie mogą korzystać z tej architektury.
  
W sytuacji firmy Humongous Insurance powinni kontynuować w zależności od aplikacji, które będą używać przez expressRoute. Jeśli na przykład jesteś klientem usługi Skype dla firm Online lub planujesz korzystanie z łączności usługi ExpressRoute podczas nawiązywania połączenia z zewnętrznymi spotkaniami usługi Skype dla firm Online, projekt zalecany w przewodniku na temat jakości multimediów i łączności sieciowej usługi Skype dla firm Online to inicjowanie obsługi dodatkowego obwodu usługi ExpressRoute dla trzeciej lokalizacji. Z perspektywy sieci może to być kosztowne; jednak żądania routingu z jednego kontynentu do drugiego przed dostarczeniem do centrum danych firmy Microsoft mogą powodować słabe lub niezdatne do użytku środowisko podczas spotkań Skype dla firm Online i komunikacji.
  
Jeśli humongous Insurance nie używa usługi Skype dla firm Online lub nie planuje jej używania w jakikolwiek sposób, możliwe jest, że ruch sieciowy będzie przeznaczony do routingu z powrotem na kontynent, na który jest dostęp do połączenia ExpressRoute. Może Office 365 jednak powodować niepotrzebne opóźnienia lub przeciążenie protokołu TCP. W obu przypadkach zaleca się routing ruchu do Internetu do Internetu w witrynie lokalnej, aby korzystać z sieci dostarczania zawartości, na których Office 365.
  
![Wiele lokalizacji geograficznych w utercie ExpressRoute.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Podczas planowania strategii dotyczącej wielu lokalizacji geograficznych firmy Humongous Insurance należy uwzględnić wiele czynników w zakresie wielkości obwodu, liczby obwodów, trybu failover itp.
  
Mając usługę ExpressRoute w jednej lokalizacji z wieloma regionami próbujących korzystać z obwodu, humongous Insurance chce mieć pewność, że połączenia z biura zdalnego Office 365 będą wysyłane do centrum danych firmy Office 365 w najbliższej siedzibie głównej i odbierane w lokalizacji siedziby. W tym celu humongous Insurance implementuje przesyłanie dalej DNS, aby zmniejszyć liczbę rund i odnośników DNS wymaganych do nawiązania odpowiedniego połączenia ze środowiskiem usługi Office 365 najbliższym internetowym punktem wychodzącym w siedzibie firmy. Uniemożliwia to klientowi rozwiązanie problemu lokalnego serwera frontonu i zapewnia, że serwer Front-End, z którym łączy się osoba, znajduje się w pobliżu siedziby firmy Humongous Insurance, w której firma Humongous Insurance łączy się z firmą Microsoft. Możesz również nauczyć się [przypisywania warunkowej usługi przesyłania dalej dla nazwy domeny](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
W tym scenariuszu ruch z biura zdalnego rozpozna infrastrukturę frontoronu usługi Office 365 w Ameryce Północnej i będzie używać programu Office 365 do łączenia się z serwerami zaplecza, zgodnie z architekturą aplikacji Office 365. Na przykład Exchange Online połączenie w Ameryce Północnej i te serwery frontendowe połączą się z serwerem skrzynki pocztowej zaplecza, niezależnie od miejsca pobytu dzierżawcy. Wszystkie usługi mają bardzo rozproszone front doors, w skład których wchodzą unicast i anycast.
  
Jeśli firmy Humongous ma główne biura na wielu kontynentach, zalecany jest co najmniej dwa aktywne/aktywne obwody na region w celu zmniejszenia opóźnień dla wrażliwych aplikacji, takich jak Skype dla firm Online. Jeśli wszystkie biura znajdują się na jednym kontynencie lub nie są połączone ze współpracą w czasie rzeczywistym, decyzja o posiadaniu skonsolidowanego lub rozproszonego punktu wychodzącego należy do klienta. Gdy dostępnych jest wiele obwodów, routing BGP zapewni tryb failover w przypadku niedostępności dowolnego pojedynczego obwodu.
  
Dowiedz się więcej o [przykładowych konfiguracjach routingu](/azure/expressroute/expressroute-config-samples-routing) i [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>Routing selektywny przy użyciu usługi ExpressRoute

Routing selektywny przy użyciu usługi ExpressRoute może być potrzebny z różnych powodów, takich jak testowanie i uruchamianie usługi ExpressRoute dla podzestawu użytkowników. Istnieją różne narzędzia, których mogą używać klienci, aby selektywnie Office 365 ruchu sieciowego za pośrednictwem usługi ExpressRoute:
  
1. **Filtrowanie/podział** tras — pozwala na trasy BGP Office 365 przez usługę ExpressRoute do podzestawu podsieci lub routerów. To selektywny sposób przekierowywuje ruch według segmentu sieci klienta lub fizycznej lokalizacji biura. Jest to typowe w przypadku rozłożonego werego rzutowania usługi ExpressRoute dla Office 365 skonfigurowanego na Twoich urządzeniach BGP.

2. **Pliki PAC/adresy URL —** kierowanie Office 365 sieciowego do określonych FQDN do trasy na określonej ścieżce. To selektywny sposób rozsyła pliki według komputera klienckiego wskazanego we [wdrożeniu pliku PAC](./managing-office-365-endpoints.md).

3. **Filtrowanie tras** -  [Filtry trasy](/azure/expressroute/how-to-routefilter-portal) są sposobem na wykorzystanie podzestawu obsługiwanych usług za pośrednictwem komunikacji równorzędnej firmy Microsoft.

4. **Społeczności BGP —** filtrowanie oparte na tagach społeczności [BGP](./bgp-communities-in-expressroute.md) umożliwia klientowi określenie, które Office 365 będą przechodzić przez usługę ExpressRoute, a które będą przechodzić przez Internet.

Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Ocena Office 365 sieci](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie łącznością sieciową za Office 365 ExpressRoute](managing-expressroute-for-connectivity.md)
  
[Planowanie sieci z usługą ExpressRoute dla sieci Office 365](network-planning-with-expressroute.md)
  
[Implementowanie expressroute dla Office 365](implementing-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Usługi ExpressRoute i QoS w Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ połączeń przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Używanie społeczności BGP w u usługi ExpressRoute na Office 365 scenariuszy](bgp-communities-in-expressroute.md)
  
[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)
