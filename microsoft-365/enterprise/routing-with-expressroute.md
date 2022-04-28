---
title: Routing przy użyciu usługi ExpressRoute dla usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule przedstawiono wymagania dotyczące routingu usługi Azure ExpressRoute, obwody i domeny routingu do użycia z Office 365.
ms.openlocfilehash: c63e3ae14c9b369265622f17c2e542818620aa3e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092916"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing przy użyciu usługi ExpressRoute dla usługi Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Aby prawidłowo zrozumieć ruch routingu do Office 365 przy użyciu usługi Azure ExpressRoute, musisz dokładnie zapoznać się z podstawowymi [wymaganiami dotyczącymi routingu usługi ExpressRoute](/azure/expressroute/expressroute-routing) oraz [obwodami i domenami routingu usługi ExpressRoute](/azure/expressroute/expressroute-circuit-peerings). Określają one podstawy korzystania z usługi ExpressRoute, na których będą polegać Office 365 klienci.
  
Niektóre z kluczowych elementów w powyższych artykułach, które należy zrozumieć, obejmują:
  
- Obwody usługi ExpressRoute nie są mapowane na określoną infrastrukturę fizyczną, ale są połączeniem logicznym nawiązywanym w jednej lokalizacji komunikacji równorzędnej przez firmę Microsoft i dostawcę komunikacji równorzędnej w Twoim imieniu.

- Istnieje mapowanie 1:1 między obwodem usługi ExpressRoute a kluczem s-key klienta.

- Każdy obwód może obsługiwać dwie niezależne relacje komunikacji równorzędnej (prywatna komunikacja równorzędna platformy Azure i komunikacja równorzędna firmy Microsoft); Office 365 wymaga komunikacji równorzędnej firmy Microsoft.

- Każdy obwód ma stałą przepustowość, która jest współużytkowana we wszystkich relacjach komunikacji równorzędnej.

- Wszystkie publiczne adresy IPv4 i publiczne numery AS, które będą używane dla obwodu usługi ExpressRoute, muszą zostać zweryfikowane jako należące do Użytkownika lub przypisane wyłącznie do Ciebie przez właściciela zakresu adresów.

- Wirtualne obwody usługi ExpressRoute są nadmiarowe globalnie i będą zgodne ze standardowymi praktykami routingu BGP. Dlatego zalecamy dwa obwody fizyczne na ruch wychodzący do dostawcy w konfiguracji aktywnej/aktywnej.

Aby uzyskać więcej informacji na temat obsługiwanych usług, kosztów i szczegółów konfiguracji, zobacz [stronę Często zadawane](/azure/expressroute/expressroute-faqs) pytania. Aby uzyskać informacje na temat dostawców łączności oferujących pomoc dotyczącą komunikacji równorzędnej firmy Microsoft, zobacz [artykuł lokalizacji usługi ExpressRoute](/azure/expressroute/expressroute-locations) . Nagraliśmy również 10-częściową serię [usługi Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) w kanale Channel 9, aby dokładniej wyjaśnić pojęcia.
  
## <a name="ensuring-route-symmetry"></a>Zapewnianie symetrii tras

Serwery frontonu Office 365 są dostępne zarówno w Internecie, jak i w usłudze ExpressRoute. Te serwery wolą kierować z powrotem do środowiska lokalnego za pośrednictwem obwodów usługi ExpressRoute, gdy oba są dostępne. W związku z tym istnieje możliwość asymetrii tras, jeśli ruch z sieci woli kierować przez obwody internetowe. Trasy asymetryczne stanowią problem, ponieważ urządzenia, które przeprowadzają inspekcję pakietów stanowych, mogą blokować ruch powrotny podążający inną ścieżką niż obserwowane pakiety wychodzące.
  
Niezależnie od tego, czy inicjujesz połączenie z Office 365 za pośrednictwem Internetu, czy usługi ExpressRoute, źródłem musi być adres routingu publicznego. W przypadku wielu klientów komunikacji równorzędnej bezpośrednio z firmą Microsoft posiadanie prywatnych adresów, w których możliwe jest duplikowanie między klientami, nie jest możliwe.
  
Poniżej przedstawiono scenariusze, w których będzie inicjowana komunikacja z Office 365 do sieci lokalnej. Aby uprościć projekt sieci, zalecamy kierowanie następujących elementów za pośrednictwem ścieżki internetowej.
  
- Usługi SMTP, takie jak poczta z dzierżawy Exchange Online do hosta lokalnego lub SharePoint Poczta online wysłana z usługi SharePoint Online do hosta lokalnego. Protokół SMTP jest używany szerzej w sieci firmy Microsoft niż prefiksy tras udostępnione przez obwody usługi ExpressRoute i anonsowanie lokalnych serwerów SMTP za pośrednictwem usługi ExpressRoute spowoduje błędy z tymi innymi usługami.

- Usługi ADFS podczas walidacji haseł na potrzeby logowania.

- [Exchange Server wdrożenia hybrydowe](/exchange/exchange-hybrid).

- [SharePoint federacyjnego wyszukiwania hybrydowego](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint hybrydowy bcs](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype dla firm federacji hybrydowej](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) i/lub [Skype dla firm](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype dla firm łącznik chmury](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Aby firma Microsoft przekierowała z powrotem do sieci dla tych dwukierunkowych przepływów ruchu, trasy protokołu BGP do urządzeń lokalnych muszą być współużytkowane z firmą Microsoft. W przypadku anonsowania prefiksów tras do firmy Microsoft za pośrednictwem usługi ExpressRoute należy postępować zgodnie z następującymi najlepszymi rozwiązaniami:

1) Nie anonsuj tego samego prefiksu trasy publicznego adresu IP do publicznego Internetu i za pośrednictwem usługi ExpressRoute. Zaleca się, aby anonsy prefiksu tras protokołu IP BGP do firmy Microsoft za pośrednictwem usługi ExpressRoute pochodziły z zakresu, który nie jest w ogóle anonsowany w Internecie. Jeśli nie jest to możliwe ze względu na dostępną przestrzeń adresów IP, należy upewnić się, że anonsujesz bardziej szczegółowy zakres za pośrednictwem usługi ExpressRoute niż jakiekolwiek obwody internetowe.

2) Użyj oddzielnych pul adresów IP translatora adresów sieciowych na obwód usługi ExpressRoute i oddziel je od obwodów internetowych.

3) Każda trasa anonsowana do firmy Microsoft przyciągnie ruch sieciowy z dowolnego serwera w sieci firmy Microsoft, a nie tylko tych, dla których trasy są anonsowane do sieci za pośrednictwem usługi ExpressRoute. Anonsuj trasy tylko do serwerów, na których scenariusze routingu są zdefiniowane i dobrze zrozumiałe dla twojego zespołu. Anonsuj oddzielne prefiksy tras adresów IP w każdym z wielu obwodów usługi ExpressRoute z sieci.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Wybieranie, które aplikacje i funkcje są kierowane przez usługę ExpressRoute

Po skonfigurowaniu relacji komunikacji równorzędnej przy użyciu domeny routingu komunikacji równorzędnej firmy Microsoft i zatwierdzeniu odpowiedniego dostępu będzie można zobaczyć wszystkie usługi PaaS i SaaS dostępne za pośrednictwem usługi ExpressRoute. Usługami Office 365 przeznaczonymi dla usługi ExpressRoute można zarządzać za pomocą [społeczności protokołu BGP](./bgp-communities-in-expressroute.md) lub [filtrów tras](/azure/expressroute/how-to-routefilter-portal).
  
Wszystkie funkcje Office 365, które są dostępne przy użyciu komunikacji równorzędnej firmy Microsoft, są wymienione w [artykule Office 365 punktów końcowych](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) według typu aplikacji i nazwy FQDN. Powodem używania nazwy FQDN w tabelach jest umożliwienie klientom zarządzania ruchem przy użyciu plików PAC lub innych konfiguracji serwera proxy. Zobacz nasz przewodnik [dotyczący zarządzania punktami końcowymi Office 365](./managing-office-365-endpoints.md), na przykład plikami PAC.
  
W niektórych sytuacjach użyliśmy domeny z symbolami wieloznacznymi, w której co najmniej jedna nazwa FQDN jest anonsowana inaczej niż domena wieloznaczna wyższego poziomu. Zwykle dzieje się tak, gdy symbol wieloznaczny reprezentuje długą listę serwerów, które są anonsowane w usłudze ExpressRoute i Internecie, podczas gdy mały podzbiór miejsc docelowych jest anonsowany tylko do Internetu lub odwrotnie. Zapoznaj się z poniższymi tabelami, aby zrozumieć, gdzie są różnice.
  
W tej tabeli są wyświetlane wieloznaczne nazwy FQDN, które są anonsowane zarówno w Internecie, jak i w usłudze Azure ExpressRoute wraz z nazwami FQDN, które są anonsowane tylko w Internecie.

|**Domena z symbolami wieloznacznymi anonsowana do obwodów usługi ExpressRoute i Internetu**|**Sub-FQDN anonsowane tylko do obwodów internetowych**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

Zazwyczaj pliki PAC są przeznaczone do wysyłania żądań sieciowych do anonsowanych punktów końcowych usługi ExpressRoute bezpośrednio do obwodu i wszystkich innych żądań sieciowych do serwera proxy. Jeśli konfigurujesz plik PAC w następujący sposób, skomponuj plik PAC w następującej kolejności:
  
1. Uwzględnij nazwy podrzędne FQDN z kolumny drugiej w powyższej tabeli w górnej części pliku PAC, wysyłając ruch do serwera proxy. W naszym artykule dotyczącym [zarządzania punktami końcowymi Office 365](./managing-office-365-endpoints.md) skompilowaliśmy przykładowy plik PAC.

2. Uwzględnij wszystkie nazwy FQDN oznaczone jako anonsowane w usłudze ExpressRoute w [tym artykule](./urls-and-ip-address-ranges.md) poniżej pierwszej sekcji, wysyłając ruch bezpośrednio do obwodu usługi ExpressRoute.

3. Dołącz inne punkty końcowe sieci lub reguły poniżej tych dwóch wpisów, wysyłając ruch do serwera proxy.

W tej tabeli są wyświetlane domeny z symbolami wieloznacznymi, które są anonsowane do obwodów internetowych tylko razem z pod-FQDN, które są anonsowane w usłudze Azure ExpressRoute i obwodach internetowych. W przypadku powyższego pliku PAC nazwy FQDN w kolumnie 2 w poniższej tabeli są wyświetlane jako anonsowane do usługi ExpressRoute w odwołanym linku, co oznacza, że zostaną uwzględnione w drugiej grupie wpisów w pliku.

|**Domena z symbolami wieloznacznymi anonsowana tylko do obwodów internetowych**|**Sub-FQDN anonsowane do obwodów usługi ExpressRoute i Internetu**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing ruchu Office 365 przez Internet i usługę ExpressRoute

Aby skierować do wybranego Office 365 aplikacji, należy określić szereg kluczowych czynników.
  
1. Ile przepustowości będzie wymagać aplikacja. Próbkowanie istniejącego użycia jest jedyną niezawodną metodą określania tego w organizacji.

2. Z jakich lokalizacji ruchu wychodzącego chcesz opuścić sieć. Należy zaplanować zminimalizowanie opóźnienia sieci dla łączności z Office 365, ponieważ będzie to miało wpływ na wydajność. Ponieważ Skype dla firm używa głosu i wideo w czasie rzeczywistym, jest podatny na małe opóźnienia sieci.

3. Jeśli chcesz, aby wszystkie lokalizacje sieciowe lub podzestaw lokalizacji sieciowych korzystały z usługi ExpressRoute.

4. Z jakich lokalizacji wybrany dostawca sieci oferuje usługę ExpressRoute.

Po określeniu odpowiedzi na te pytania można aprowizować obwód usługi ExpressRoute, który spełnia wymagania dotyczące przepustowości i lokalizacji. Aby uzyskać więcej pomocy w planowaniu sieci, zapoznaj się z [przewodnikiem dostrajania sieci Office 365](./network-planning-and-performance.md) i [analizą przypadku dotyczącą sposobu, w jaki firma Microsoft obsługuje planowanie wydajności sieci](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Przykład 1: Pojedyncza lokalizacja geograficzna
  
Ten przykład jest scenariuszem fikcyjnej firmy Trey Research, która ma jedną lokalizację geograficzną.
  
Pracownicy Trey Research mogą łączyć się tylko z usługami i stronami internetowymi w Internecie, na które dział bezpieczeństwa wyraźnie zezwala na parę wychodzących serwerów proxy, które znajdują się między siecią firmową a usługodawcą internetowym.
  
Firma Trey Research planuje używać usługi Azure ExpressRoute dla Office 365 i uznaje, że niektóre ruchy, takie jak ruch przeznaczony dla sieci dostarczania zawartości, nie będą mogły kierować się przez usługę ExpressRoute w celu Office 365 połączenia. Ponieważ cały ruch jest już domyślnie kierowany do urządzeń proxy, te żądania będą nadal działać tak jak poprzednio. Gdy firma Trey Research ustali, że może spełnić wymagania dotyczące routingu usługi Azure ExpressRoute, utworzy obwód, skonfiguruje routing i połączy nowy obwód usługi ExpressRoute z siecią wirtualną. Po wprowadzeniu podstawowej konfiguracji usługi Azure ExpressRoute firma Trey Research używa [pliku PAC nr 2, który publikujemy](./managing-office-365-endpoints.md), do kierowania ruchu z danymi specyficznymi dla klienta za pośrednictwem bezpośredniej usługi ExpressRoute na potrzeby połączeń Office 365.
  
Jak pokazano na poniższym diagramie, firma Trey Research jest w stanie spełnić wymóg kierowania ruchu Office 365 przez Internet oraz podzbioru ruchu przez usługę ExpressRoute przy użyciu kombinacji zmian konfiguracji routingu i wychodzącego serwera proxy.
  
1. Za pomocą [pliku PAC nr 2 publikujemy](./managing-office-365-endpoints.md) w celu kierowania ruchu przez oddzielny internetowy punkt ruchu wychodzącego dla usługi Azure ExpressRoute dla Office 365.

2. Klienci są konfigurowane z domyślną trasą do serwerów proxy firmy Trey Research.

W tym przykładowym scenariuszu firma Trey Research korzysta z wychodzącego urządzenia proxy. Podobnie klienci, którzy nie korzystają z usługi Azure ExpressRoute dla Office 365, mogą chcieć użyć tej techniki do kierowania ruchu na podstawie kosztów inspekcji ruchu przeznaczonego dla dobrze znanych punktów końcowych o dużej liczbie.
  
Najwięcej nazw FQDN dla Exchange Online, SharePoint Online i Skype dla firm Online są następujące:
  
![Sieć brzegowa klienta usługi ExpressRoute.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\>-my.sharepoint.com, \<tenant-name\>-\<app\>.sharepoint.com

- \*.Lync.com wraz z zakresami adresów IP dla ruchu innych niż TCP

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

Dowiedz się więcej na temat [wdrażania ustawień serwera proxy i zarządzania nimi w Windows 8](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) i [zapewniania, że serwer proxy nie ogranicza Office 365](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
W przypadku jednego obwodu usługi ExpressRoute nie ma wysokiej dostępności dla usługi Trey Research. W przypadku awarii nadmiarowej pary urządzeń brzegowych usługi Trey obsługujących łączność usługi ExpressRoute nie ma dodatkowego obwodu usługi ExpressRoute do przełączenia w tryb failover. To pozostawia Trey Research w trudnej sytuacji, ponieważ przechodzenie w tryb failover do Internetu będzie wymagało ręcznej ponownej konfiguracji, a w niektórych przypadkach nowych adresów IP. Jeśli firma Trey chce dodać wysoką dostępność, najprostszym rozwiązaniem jest dodanie dodatkowych obwodów usługi ExpressRoute dla każdej lokalizacji i skonfigurowanie obwodów w sposób aktywny/aktywny.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing usługi ExpressRoute dla Office 365 z wieloma lokalizacjami

Ostatni scenariusz, routing Office 365 ruchu przez usługę ExpressRoute jest podstawą jeszcze bardziej złożonej architektury routingu. Niezależnie od liczby lokalizacji, liczby kontynentów, na których te lokalizacje istnieją, liczby obwodów usługi ExpressRoute itd., będzie wymagane kierowanie pewnego ruchu do Internetu i pewnego ruchu przez usługę ExpressRoute.
  
Dodatkowe pytania, na które należy odpowiedzieć klientom z wieloma lokalizacjami w wielu lokalizacjach geograficznych, obejmują:
  
1. Czy w każdej lokalizacji jest wymagany obwód usługi ExpressRoute? Jeśli używasz usługi Skype dla firm Online lub potrzebujesz poufności opóźnienia dla SharePoint Online lub Exchange Online, w każdej lokalizacji zaleca się nadmiarową parę aktywnych/aktywnych obwodów usługi ExpressRoute. Aby uzyskać więcej informacji, zobacz Skype dla firm przewodnik po jakości multimediów i łączności sieciowej.

2. Jeśli obwód usługi ExpressRoute nie jest dostępny w określonym regionie, jak Office 365 kierowany ruch?

3. Jaka jest preferowana metoda konsolidowania ruchu w przypadku sieci z wieloma małymi lokalizacjami?

Każdy z nich stanowi unikatowe wyzwanie, które wymaga oceny własnej sieci i opcji dostępnych przez firmę Microsoft.

|**Kwestie do rozważenia**|**Składniki sieci do oceny**|
|:-----|:-----|
|Obwody w więcej niż jednej lokalizacji  <br/> |Zalecamy co najmniej dwa obwody skonfigurowane w sposób aktywny/aktywny.  <br/> Należy porównać wymagania dotyczące kosztów, opóźnień i przepustowości.  <br/> Aby zarządzać routingiem z wieloma obwodami, użyj kosztów tras BGP, plików PAC i translatora adresów sieciowych.  <br/> |
|Routing z lokalizacji bez obwodu usługi ExpressRoute  <br/> |Zalecamy ruch wychodzący i rozpoznawanie nazw DNS tak blisko osoby inicjującej żądanie Office 365.  <br/> Przekazywanie DNS może służyć do umożliwienia zdalnym biurom odnajdywania odpowiedniego punktu końcowego.  <br/> Klienci w zdalnym biurze muszą mieć dostępną trasę, która zapewnia dostęp do obwodu usługi ExpressRoute.  <br/> |
|Konsolidacja małych biur  <br/> |Dostępną przepustowość i użycie danych należy dokładnie porównać.  <br/> |

> [!NOTE]
> Firma Microsoft będzie preferować usługę ExpressRoute przez Internet, jeśli trasa jest dostępna niezależnie od lokalizacji fizycznej.
  
Każda z tych kwestii musi być brana pod uwagę dla każdej unikatowej sieci. Poniżej przedstawiono przykład.
  
### <a name="example-2-multi-geographic-locations"></a>Przykład 2: Lokalizacje z wieloma lokalizacjami geograficznymi
  
Ten przykład jest scenariuszem fikcyjnej firmy o nazwie "Humongous Insurance", która ma wiele lokalizacji geograficznych.
  
Humongous Insurance jest geograficznie rozproszony z biurami na całym świecie. Chcą zaimplementować usługę Azure ExpressRoute dla Office 365, aby zachować większość ruchu Office 365 w bezpośrednich połączeniach sieciowych. Humongous Insurance ma również biura na dwóch dodatkowych kontynentach. Pracownicy zdalnego biura, w którym usługa ExpressRoute nie jest możliwa, będą musieli wrócić do jednego lub obu głównych obiektów, aby korzystać z połączenia usługi ExpressRoute.
  
Przewodnią zasadą jest jak najszybsze uzyskanie ruchu Office 365 przeznaczonego do centrum danych firmy Microsoft. W tym przykładzie firma Humongous Insurance musi zdecydować, czy ich biura zdalne powinny kierować się przez Internet, aby jak najszybciej dostać się do centrum danych firmy Microsoft za pośrednictwem dowolnego połączenia lub czy ich biura zdalne powinny kierować się przez sieć wewnętrzną, aby jak najszybciej dostać się do centrum danych firmy Microsoft za pośrednictwem połączenia usługi ExpressRoute.
  
Centra danych, sieci i architektura aplikacji firmy Microsoft zostały zaprojektowane tak, aby umożliwić globalną komunikację i obsługę ich w najbardziej wydajny sposób. Jest to jedna z największych sieci na świecie. Żądania przeznaczone dla Office 365, które pozostają w sieciach klientów dłużej niż jest to konieczne, nie będą mogły korzystać z tej architektury.
  
W sytuacji Humongous Insurance powinni postępować w zależności od aplikacji, z których zamierzają korzystać za pośrednictwem usługi ExpressRoute. Jeśli na przykład jest on klientem usługi Skype dla firm Online lub planuje korzystać z łączności usługi ExpressRoute podczas nawiązywania połączenia z zewnętrznymi spotkaniami Skype dla firm Online, projekt zalecany w przewodniku Skype dla firm Jakości multimediów online i łączności sieciowej polega na aprowizowaniu dodatkowego obwodu usługi ExpressRoute dla trzeciej lokalizacji. Może to być droższe z perspektywy sieci; Jednak kierowanie żądań z jednego kontynentu do innego przed dostarczeniem do centrum danych firmy Microsoft może spowodować słabe lub bezużyteczne środowisko podczas spotkań i komunikacji Skype dla firm Online.
  
Jeśli usługa Humongous Insurance nie używa usługi Skype dla firm Online lub nie planuje jej używać w żaden sposób, kierowanie Office 365 ruchu sieciowego z powrotem do kontynentu z połączeniem usługi ExpressRoute może być wykonalne, ale może spowodować niepotrzebne opóźnienia lub przeciążenie TCP. W obu przypadkach zaleca się kierowanie ruchu internetowego do Internetu w witrynie lokalnej w celu skorzystania z sieci dostarczania zawartości, na których Office 365 polega.
  
![Wiele lokalizacji geograficznych usługi ExpressRoute.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Kiedy Humongous Insurance planuje swoją strategię wielu geografii, istnieje wiele rzeczy do rozważenia wokół wielkości obwodu, liczby obwodów, trybu failover i tak dalej.
  
Dzięki usłudze ExpressRoute w jednej lokalizacji, w których wiele regionów próbuje korzystać z obwodu, usługa Humongous Insurance chce zapewnić, że połączenia z Office 365 z zdalnego biura są wysyłane do najbliższej siedziby Office 365 centrum danych i odbierane przez lokalizację siedziby głównej. W tym celu usługa Humongous Insurance implementuje przekazywanie DNS w celu zmniejszenia liczby rund i wyszukiwań DNS wymaganych do nawiązania odpowiedniego połączenia ze środowiskiem Office 365 znajdującym się najbliżej internetowego punktu ruchu wychodzącego siedziby. Uniemożliwia to klientowi rozpoznawanie lokalnego serwera frontonu i zapewnia, że serwer Front-End, z którym osoba nawiązuje połączenie, znajduje się w pobliżu siedziby głównej, w której usługa Humongous Insurance prowadzi komunikację równorzędną z firmą Microsoft. Możesz również dowiedzieć się [, jak przypisać warunkowy usługę przesyłania dalej dla nazwy domeny](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
W tym scenariuszu ruch z zdalnego biura rozpozna infrastrukturę frontonu Office 365 w Ameryka Północna i użyje Office 365 do nawiązania połączenia z serwerami zaplecza zgodnie z architekturą aplikacji Office 365. Na przykład Exchange Online zakończy połączenie w Ameryka Północna, a te serwery frontonu będą łączyć się z serwerem skrzynki pocztowej zaplecza wszędzie tam, gdzie znajduje się dzierżawa. Wszystkie usługi mają szeroko rozproszoną usługę front door składającą się z emisji pojedynczej i dowolnych miejsc docelowych emisji.
  
Jeśli firma Humongous ma duże biura na wielu kontynentach, zaleca się co najmniej dwa obwody aktywne/aktywne na region w celu zmniejszenia opóźnienia dla poufnych aplikacji, takich jak Skype dla firm Online. Jeśli wszystkie biura znajdują się na jednym kontynencie lub nie korzystają ze współpracy w czasie rzeczywistym, skonsolidowany lub rozproszony punkt ruchu wychodzącego jest decyzją specyficzną dla klienta. Jeśli jest dostępnych wiele obwodów, routing protokołu BGP zapewni przejście w tryb failover, jeśli dowolny pojedynczy obwód stanie się niedostępny.
  
Dowiedz się więcej o [przykładowych konfiguracjach routingu](/azure/expressroute/expressroute-config-samples-routing) i [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>Routing selektywny za pomocą usługi ExpressRoute

Routing selektywny z usługą ExpressRoute może być potrzebny z różnych powodów, takich jak testowanie, wdrażanie usługi ExpressRoute dla podzbioru użytkowników. Istnieją różne narzędzia, których klienci mogą używać do selektywnego kierowania ruchu sieciowego Office 365 za pośrednictwem usługi ExpressRoute:
  
1. **Filtrowanie/podział** tras — umożliwia trasom protokołu BGP Office 365 za pośrednictwem usługi ExpressRoute do podzesieci lub routerów. Jest to selektywne kierowanie według segmentu sieci klienta lub fizycznej lokalizacji biura. Jest to typowe w przypadku zdumiewającego wdrożenia usługi ExpressRoute dla Office 365 i jest skonfigurowane na urządzeniach BGP.

2. **Pliki/adresy URL PAC** — kierowanie ruchu sieciowego Office 365 przeznaczonego dla określonych nazw FQDN w celu kierowania do określonej ścieżki. To selektywnie kieruje według komputera klienckiego zgodnie z identyfikatorem [wdrożenia pliku PAC](./managing-office-365-endpoints.md).

3. **Filtrowanie** -  tras [Filtry tras](/azure/expressroute/how-to-routefilter-portal) to sposób na korzystanie z podzestawu obsługiwanych usług za pośrednictwem komunikacji równorzędnej firmy Microsoft.

4. **Społeczności protokołu BGP** — filtrowanie na podstawie [tagów społeczności protokołu BGP](./bgp-communities-in-expressroute.md) pozwala klientowi określić, które aplikacje Office 365 będą przechodzić przez usługę ExpressRoute i które będą przechodzić przez Internet.

Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365](managing-expressroute-for-connectivity.md)
  
[Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365](network-planning-with-expressroute.md)
  
[Implementowanie usługi ExpressRoute dla Office 365](implementing-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod kątem Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Usługi ExpressRoute i QoS w usłudze Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ wywołań przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Używanie społeczności protokołu BGP w usłudze ExpressRoute na potrzeby scenariuszy Office 365](bgp-communities-in-expressroute.md)
  
[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)
