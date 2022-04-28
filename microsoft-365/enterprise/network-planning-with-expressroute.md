---
title: Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: W tym artykule dowiesz się więcej na temat usługi Azure ExpressRoute dla Office 365 i sposobu wykorzystania jej do planowania sieci.
ms.openlocfilehash: a284472ad84139a5e76eeab38121d62cf3757829
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095647"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Usługa ExpressRoute dla Office 365 zapewnia łączność w warstwie 3 między siecią a centrami danych firmy Microsoft. Obwody używają anonsów tras protokołu BGP (Border Gateway Protocol) serwerów frontonu Office 365. Z perspektywy urządzeń lokalnych, gdy trzeba wybrać właściwą ścieżkę TCP/IP do Office 365, usługa Azure ExpressRoute jest postrzegana jako alternatywa dla Internetu.
  
Usługa Azure ExpressRoute dodaje bezpośrednią ścieżkę do określonego zestawu obsługiwanych funkcji i usług oferowanych przez serwery Office 365 w centrach danych firmy Microsoft. Usługa Azure ExpressRoute nie zastępuje łączności internetowej z centrami danych firmy Microsoft ani podstawowymi usługami internetowymi, takimi jak rozpoznawanie nazw domen. Usługa Azure ExpressRoute i obwody internetowe powinny być zabezpieczone i nadmiarowe.
  
W poniższej tabeli przedstawiono kilka różnic między połączeniem internetowym i usługą Azure ExpressRoute w kontekście Office 365.

|**Różnice w planowaniu sieci**|**Połączenie sieciowe z Internetem**|**Połączenie sieciowe usługi ExpressRoute**|
|:-----|:-----|:-----|
| Dostęp do wymaganych usług internetowych, w tym;  <br/>  Rozpoznawanie nazw DNS  <br/>  Weryfikacja odwołania certyfikatu  <br/>  Sieci dostarczania zawartości (CDN)  <br/> |Tak  <br/> |Żądania do infrastruktury DNS należącej do firmy Microsoft i/lub infrastruktury CDN mogą korzystać z sieci ExpressRoute.  <br/> |
| Dostęp do usług Office 365, w tym;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype dla firm Online  <br/>  Office w przeglądarce  <br/>  Office 365 portalu i uwierzytelniania  <br/> |Tak, wszystkie aplikacje i funkcje  <br/> |Tak, [określone aplikacje i funkcje](./urls-and-ip-address-ranges.md) <br/> |
|Zabezpieczenia lokalne na obwodzie.  <br/> |Tak  <br/> |Tak  <br/> |
|Planowanie wysokiej dostępności.  <br/> |Przełączenie w tryb failover do alternatywnego połączenia sieciowego z Internetem  <br/> |Przełączenie w tryb failover do alternatywnego połączenia usługi ExpressRoute  <br/> |
|Bezpośrednie połączenie z przewidywalnym profilem sieciowym.  <br/> |Nie  <br/> |Tak  <br/> |
|Łączność IPv6.  <br/> |Tak  <br/> |Tak  <br/> |

Rozwiń poniższe tytuły, aby uzyskać więcej wskazówek dotyczących planowania sieci. Zarejestrowaliśmy również 10-częściową serię [usługi Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer), która bardziej szczegółowo się zagłębia.

## <a name="existing-azure-expressroute-customers"></a>Istniejący klienci usługi Azure ExpressRoute

Jeśli używasz istniejącego obwodu usługi Azure ExpressRoute i chcesz dodać łączność Office 365 za pośrednictwem tego obwodu, przyjrzyj się liczbie obwodów, lokalizacjom ruchu wychodzącego i rozmiarowi obwodów, aby upewnić się, że spełnią one potrzeby Office 365 użycia. Większość klientów wymaga dodatkowej przepustowości, a wielu wymaga większej liczby obwodów.
  
Aby włączyć dostęp do Office 365 za pośrednictwem istniejących obwodów usługi Azure ExpressRoute, [skonfiguruj filtry tras](/azure/expressroute/how-to-routefilter-portal), aby zapewnić dostępność usług Office 365.
  
Subskrypcja usługi Azure ExpressRoute jest zorientowana na klienta, co oznacza, że subskrypcje są powiązane z klientami. Jako klient możesz mieć wiele obwodów usługi Azure ExpressRoute i uzyskiwać dostęp do wielu zasobów w chmurze firmy Microsoft za pośrednictwem tych obwodów. Możesz na przykład uzyskać dostęp do hostowanej maszyny wirtualnej platformy Azure, dzierżawy testowej Office 365 i dzierżawy Office 365 produkcyjnej za pośrednictwem pary nadmiarowych obwodów usługi Azure ExpressRoute.
  
W tej tabeli przedstawiono dwa typy relacji komunikacji równorzędnej, które można zaimplementować za pośrednictwem obwodów.

|**Relacja komunikacji równorzędnej**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**Usług** <br/> |IaaS: Azure Virtual Machines  <br/> |PaaS: usługi publiczne platformy Azure  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Inicjowanie połączenia**** <br/> |Klient-firma Microsoft  <br/> Microsoft-to-Customer  <br/> |Klient-firma Microsoft  <br/> Microsoft-to-Customer  <br/> |
|**Obsługa QoS** <br/> |Brak QoS  <br/> |<sup>QoS1</sup> <br/> |

<sup>1 </sup> Usługa QoS obsługuje Skype dla firm tylko w tej chwili.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planowanie przepustowości dla usługi Azure ExpressRoute

Każdy Office 365 klient ma unikatowe wymagania dotyczące przepustowości w zależności od liczby osób w każdej lokalizacji, aktywności każdej aplikacji Office 365 oraz innych czynników, takich jak użycie sprzętu lokalnego lub hybrydowego oraz konfiguracje zabezpieczeń sieci.
  
Zbyt mała przepustowość spowoduje przeciążenie, ponowne przekazywanie danych i nieprzewidywalne opóźnienia. Zbyt duża przepustowość spowoduje niepotrzebne koszty. W istniejącej sieci przepustowość jest często określana jako wartość procentowa dostępnego miejsca na pokładzie obwodu. Posiadanie 10% miejsca na głowę prawdopodobnie spowoduje przeciążenie, a posiadanie 80% miejsca na głowę zwykle oznacza niepotrzebne koszty. Typowe przydziały docelowe pomieszczeń docelowych to od 20% do 50%.
  
Aby znaleźć odpowiedni poziom przepustowości, najlepszym mechanizmem jest przetestowanie istniejącego użycia sieci. Jest to jedyny sposób uzyskania rzeczywistej miary użycia i potrzeb, ponieważ każda konfiguracja sieci i aplikacje są w pewnym sensie unikatowe. Podczas pomiaru należy zwrócić szczególną uwagę na całkowite zużycie przepustowości, opóźnienia i przeciążenie TCP, aby zrozumieć potrzeby sieci.
  
Gdy masz szacowany plan bazowy obejmujący wszystkie aplikacje sieciowe, pilotaż Office 365 z niewielką grupą, która składa się z różnych profilów osób w organizacji, aby określić rzeczywiste użycie, i użyj dwóch pomiarów, aby oszacować przepustowość wymaganą dla każdej lokalizacji biura. Jeśli podczas testowania występują problemy z opóźnieniami lub przeciążeniem TCP, może być konieczne przeniesienie ruchu wychodzącego bliżej osób korzystających z Office 365 lub usunięcie intensywnego skanowania sieci, takiego jak odszyfrowywanie/inspekcja protokołu SSL.
  
Wszystkie nasze zalecenia dotyczące tego, jaki typ przetwarzania sieci jest zalecany, mają zastosowanie zarówno do obwodów usługi ExpressRoute, jak i internetu. To samo dotyczy pozostałych wskazówek dotyczących witryny [dostrajania wydajności](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Stosowanie mechanizmów kontroli zabezpieczeń do usługi Azure ExpressRoute w scenariuszach Office 365

Zabezpieczanie łączności usługi Azure ExpressRoute rozpoczyna się od tych samych zasad, co zabezpieczanie łączności z Internetem. Wielu klientów decyduje się na wdrożenie kontrolek sieciowych i obwodowych wzdłuż ścieżki usługi ExpressRoute łączącej sieć lokalną z Office 365 i innymi chmurami firmy Microsoft. Te mechanizmy kontroli mogą obejmować zapory, serwery proxy aplikacji, zapobieganie wyciekom danych, wykrywanie włamań, systemy zapobiegania włamaniom itd. W wielu przypadkach klienci stosują różne poziomy kontroli do ruchu inicjowanego ze środowiska lokalnego do firmy Microsoft w porównaniu z ruchem inicjowanym przez firmę Microsoft przechodzącym do sieci lokalnej klienta w porównaniu z ruchem inicjowanym ze środowiska lokalnego do ogólnego internetowego miejsca docelowego.
  
Oto kilka przykładów integracji zabezpieczeń z [modelem łączności usługi ExpressRoute](/azure/expressroute/expressroute-connectivity-models) , który chcesz wdrożyć.

|**Opcja integracji usługi ExpressRoute**|**Model obwodowy zabezpieczeń sieci**|
|:-----|:-----|
|Colocated at a cloud exchange (Kolokowana na giełdzie w chmurze)  <br/> |Zainstaluj nową lub użyj istniejącej infrastruktury zabezpieczeń/obwodowej w obiekcie kolokacji, w którym nawiązano połączenie usługi ExpressRoute.  <br/> Używaj obiektu kolokacji wyłącznie do celów routingu/połączenia wzajemnego i połączeń back haul z obiektu kolokacji do lokalnej infrastruktury zabezpieczeń/obwodowej.  <br/> |
|Sieć Ethernet typu punkt-punkt  <br/> |Zakończ połączenie usługi ExpressRoute typu punkt-punkt w istniejącej lokalnej lokalizacji infrastruktury zabezpieczeń/obwodowej.  <br/> Zainstaluj nową infrastrukturę zabezpieczeń/obwodową specyficzną dla ścieżki usługi ExpressRoute i zakończ tam połączenie punkt-punkt.  <br/> |
|Dowolna-dowolna nazwa IPVPN  <br/> |Użyj istniejącej lokalnej infrastruktury zabezpieczeń/obwodowej we wszystkich lokalizacjach wychodzących do sieci IPVPN używanej do obsługi usługi ExpressRoute w celu Office 365 łączności.  <br/> Zasuń nazwę IPVPN używaną w usłudze ExpressRoute w celu Office 365 do określonych lokalizacji lokalnych wyznaczonych do pełnienia funkcji zabezpieczeń/obwodu.  <br/> |

Niektórzy dostawcy usług oferują również funkcje zabezpieczeń zarządzanych/obwodowych w ramach swoich rozwiązań integracji z usługą Azure ExpressRoute.
  
Rozważając rozmieszczenie topologii opcji obwodowych sieci/zabezpieczeń używanych w usłudze ExpressRoute dla połączeń Office 365, poniżej przedstawiono dodatkowe zagadnienia
  
- Mechanizmy kontroli sieci/zabezpieczeń typu i głębokości mogą mieć wpływ na wydajność i skalowalność środowiska Office 365 użytkownika.

- Przepływy wychodzące (lokalne firmy\> Microsoft) i przychodzące (lokalne firmy Microsoft\>) [jeśli są włączone] mogą mieć inne wymagania. Prawdopodobnie różnią się one od wychodzących do ogólnych miejsc docelowych w Internecie.

- Office 365 wymagania dotyczące portów/protokołów i niezbędnych podsieci IP są takie same, niezależnie od tego, czy ruch jest kierowany przez usługę ExpressRoute dla Office 365, czy przez Internet.

- Rozmieszczenie topologiczne sieci klienta/mechanizmów kontroli zabezpieczeń określa ostateczną kompleksową sieć między użytkownikiem a usługą Office 365 i może mieć znaczący wpływ na opóźnienie sieci i przeciążenie sieci.

- Zachęcamy klientów do projektowania topologii zabezpieczeń/obwodu do użytku z usługą ExpressRoute na potrzeby Office 365 zgodnie z najlepszymi rozwiązaniami dotyczącymi nadmiarowości, wysokiej dostępności i odzyskiwania po awarii.

Oto przykład banku Woodgrove Bank, który porównuje różne opcje łączności usługi Azure ExpressRoute z modelami zabezpieczeń obwodowych omówionymi powyżej.
  
### <a name="example-1-securing-azure-expressroute"></a>Przykład 1: Zabezpieczanie usługi Azure ExpressRoute
  
Firma Woodgrove Bank rozważa wdrożenie usługi Azure ExpressRoute i po zaplanowaniu optymalnej architektury [routingu z usługą ExpressRoute dla Office 365](routing-with-expressroute.md) i po zastosowaniu powyższych wskazówek w celu zrozumienia wymagań dotyczących przepustowości określa najlepszą metodę zabezpieczania obwodu.
  
W przypadku Woodgrove, organizacji wielonarodowej z lokalizacjami na wielu kontynentach, zabezpieczenia muszą obejmować wszystkie obwody. Optymalną opcją łączności dla woodgrove jest połączenie wielopunktowe z wieloma lokalizacjami komunikacji równorzędnej na całym świecie w celu zaspokojenia potrzeb pracowników na każdym kontynencie. Każdy kontynent obejmuje nadmiarowe obwody usługi Azure ExpressRoute na kontynencie, a zabezpieczenia muszą obejmować wszystkie te elementy.
  
Istniejąca infrastruktura Woodgrove jest niezawodna i może obsłużyć dodatkową pracę, w związku z tym Woodgrove Bank może korzystać z infrastruktury na potrzeby zabezpieczeń obwodowych usługi Azure ExpressRoute i Internetu. Gdyby tak nie było, Woodgrove mógłby zdecydować się na zakup większej ilości sprzętu w celu uzupełnienia istniejącego sprzętu lub obsługi innego typu połączenia.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Wysoka dostępność i tryb failover w usłudze Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Zalecamy aprowizowanie co najmniej dwóch aktywnych obwodów z każdego ruchu wychodzącego za pomocą usługi ExpressRoute do dostawcy usługi ExpressRoute. Jest to najczęstsze miejsce, w których występują błędy dla klientów i można ich łatwo uniknąć, aprowizacja pary aktywnych/aktywnych obwodów usługi ExpressRoute. Zalecamy również co najmniej dwa aktywne/aktywne obwody internetowe, ponieważ wiele Office 365 usług jest dostępnych tylko przez Internet.
  
Wewnątrz punktu ruchu wychodzącego sieci znajduje się wiele innych urządzeń i obwodów, które odgrywają kluczową rolę w postrzeganiu dostępności przez użytkowników. Te części scenariuszy łączności nie są objęte usługą ExpressRoute ani Office 365 umów SLA, ale odgrywają one kluczową rolę w kompleksowej dostępności usług postrzeganej przez osoby w organizacji.
  
Skoncentruj się na osobach korzystających z usługi i Office 365 operacyjnych, jeśli awaria jednego składnika wpłynie na doświadczenia osób korzystających z usługi, poszukaj sposobów ograniczenia całkowitego odsetka osób, których dotyczy problem. Jeśli tryb pracy w trybie failover jest złożony pod względem operacyjnym, należy wziąć pod uwagę środowisko ludzi z długiego czasu odzyskiwania i poszukać prostych operacyjnie i zautomatyzowanych trybów pracy w trybie failover.
  
Poza siecią Office 365, expressroute i dostawca usługi ExpressRoute mają różne poziomy dostępności.
  
### <a name="service-availability"></a>Dostępność usługi
  
- usługi Office 365 są objęte dobrze zdefiniowanymi [umowami dotyczącymi poziomu usług](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement), które obejmują metryki czasu pracy i dostępności dla poszczególnych usług. Jednym z powodów, dla których Office 365 może utrzymać tak wysoki poziom dostępności usług, jest możliwość bezproblemowego przełączania poszczególnych składników w tryb failover między wieloma centrami danych firmy Microsoft przy użyciu globalnej sieci firmy Microsoft. Ta praca w trybie failover rozciąga się z centrum danych i sieci do wielu internetowych punktów ruchu wychodzącego i umożliwia bezproblemowe przejście w tryb failover z perspektywy osób korzystających z usługi.

- Usługa ExpressRoute [zapewnia 99,9% dostępności umowy SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) dla poszczególnych dedykowanych obwodów między przeglądarką Microsoft Network Edge a dostawcą usługi ExpressRoute lub infrastrukturą partnera. Te poziomy usług są stosowane na poziomie obwodu usługi ExpressRoute, który składa się z [dwóch niezależnych połączeń między](/azure/expressroute/expressroute-introduction) nadmiarowym sprzętem firmy Microsoft a sprzętem dostawcy sieci w każdej lokalizacji komunikacji równorzędnej.

### <a name="provider-availability"></a>Dostępność dostawcy
  
- Ustalenia dotyczące poziomu usług firmy Microsoft są zatrzymywane u dostawcy lub partnera usługi ExpressRoute. Jest to również pierwsze miejsce, w których można dokonywać wyborów, które będą miały wpływ na poziom dostępności. Należy dokładnie ocenić architekturę, dostępność i odporność, które dostawca usługi ExpressRoute oferuje między obwodem sieci a połączeniem dostawców w każdej lokalizacji komunikacji równorzędnej firmy Microsoft. Zwróć szczególną uwagę na logiczne i fizyczne aspekty nadmiarowości, sprzętu komunikacji równorzędnej, obwodów sieci WAN dostarczanych przez przewoźnika oraz wszelkich dodatkowych usług dodawania wartości, takich jak usługi NAT lub zarządzane zapory.

### <a name="designing-your-availability-plan"></a>Projektowanie planu dostępności
  
Zdecydowanie zalecamy planowanie i projektowanie wysokiej dostępności i odporności w kompleksowych scenariuszach łączności dla Office 365. Projekt powinien obejmować;
  
- Brak pojedynczych punktów awarii, w tym obwodów Internetowych i ExpressRoute.

- Minimalizowanie liczby osób, których to dotyczy, i czasu trwania tego wpływu w przypadku większości przewidywanych trybów awarii.

- Optymalizacja dla prostego, powtarzalnego i automatycznego procesu odzyskiwania z większości przewidywanych trybów awarii.

- Obsługa pełnych wymagań ruchu sieciowego i funkcjonalności za pośrednictwem ścieżek nadmiarowych bez znacznego pogorszenia wydajności.

Scenariusze łączności powinny obejmować topologię sieci zoptymalizowaną pod kątem wielu niezależnych i aktywnych ścieżek sieciowych do Office 365. Zapewni to lepszą kompleksową dostępność niż topologia zoptymalizowana tylko pod kątem nadmiarowości na poziomie poszczególnych urządzeń lub urządzeń.
  
> [!TIP]
> Jeśli użytkownicy są rozdzielani między wieloma kontynentami lub regionami geograficznymi, a każda z tych lokalizacji łączy się za pośrednictwem nadmiarowych obwodów sieci WAN z pojedynczą lokalizacją lokalną, w której znajduje się pojedynczy obwód usługi ExpressRoute, użytkownicy będą mieć mniejszą dostępność usługi end-to-end niż projekt topologii sieci, który obejmuje niezależne obwody usługi ExpressRoute łączące różne regiony z najbliższą lokalizacją komunikacji równorzędnej.
  
Zalecamy aprowizowanie co najmniej dwóch obwodów usługi ExpressRoute z każdym obwodem łączącym się z inną geograficzną lokalizacją komunikacji równorzędnej. Należy aprowizować tę aktywno-aktywną parę obwodów dla każdego regionu, w którym użytkownicy będą korzystać z łączności usługi ExpressRoute dla usług Office 365. Dzięki temu każdy region może pozostać połączony podczas awarii, która ma wpływ na główną lokalizację, taką jak centrum danych lub lokalizacja komunikacji równorzędnej. Skonfigurowanie ich jako aktywnych/aktywnych umożliwia dystrybucję ruchu użytkowników końcowych na wielu ścieżkach sieciowych. Zmniejsza to zakres osób dotkniętych awariami urządzeń lub urządzeń sieciowych.
  
Nie zalecamy używania jednego obwodu usługi ExpressRoute z Internetem jako kopii zapasowej.
  
### <a name="example-2-failover-and-high-availability"></a>Przykład 2: tryb failover i wysoka dostępność
  
Projekt wielo geograficzny banku Woodgrove Bank został poddany przeglądowi routingu, przepustowości, zabezpieczeń, a teraz musi przejść przez przegląd wysokiej dostępności. Woodgrove uważa wysoką dostępność za obejmującą trzy kategorie; odporność, niezawodność i nadmiarowość.
  
Odporność umożliwia firmie Woodgrove szybkie odzyskiwanie po awariach. Niezawodność umożliwia woodgrove oferowanie spójnego wyniku w systemie. Nadmiarowość umożliwia woodgrove przejście między co najmniej jednym dublowanym wystąpieniem infrastruktury.
  
W każdej konfiguracji krawędzi woodgrove ma nadmiarowe zapory, serwery proxy i identyfikatory. W przypadku Ameryka Północna woodgrove ma jedną konfigurację krawędzi w centrum danych Dallas i inną konfigurację krawędzi w centrum danych w Wirginii. Nadmiarowy sprzęt w każdej lokalizacji zapewnia odporność na tę lokalizację.
  
Konfiguracja sieci w banku Woodgrove Bank jest oparta na kilku kluczowych zasadach:
  
- W każdym regionie geograficznym istnieje wiele obwodów usługi Azure ExpressRoute.

- Każdy obwód w regionie może obsługiwać cały ruch sieciowy w tym regionie.

- Routing wyraźnie preferuje jedną lub drugą ścieżkę w zależności od dostępności, lokalizacji itd.

- Przełączanie w tryb failover między obwodami usługi Azure ExpressRoute odbywa się automatycznie bez dodatkowej konfiguracji lub akcji wymaganej przez firmę Woodgrove.

- Tryb failover między obwodami internetowymi odbywa się automatycznie bez dodatkowej konfiguracji lub akcji wymaganej przez woodgrove.

W tej konfiguracji, dzięki nadmiarowości na poziomie fizycznym i wirtualnym, Woodgrove Bank jest w stanie zapewnić lokalną odporność, odporność regionalną i globalną odporność w niezawodny sposób. Firma Woodgrove wybrała tę konfigurację po ocenie pojedynczego obwodu usługi Azure ExpressRoute na region, a także możliwości przełączenia w tryb failover do Internetu.
  
Jeśli woodgrove nie może mieć wielu obwodów usługi Azure ExpressRoute na region, routing ruchu pochodzącego z Ameryka Północna do obwodu usługi Azure ExpressRoute w regionie Azji i Pacyfiku doda niedopuszczalny poziom opóźnienia, a wymagana konfiguracja usługi przesyłania dalej DNS zwiększa złożoność.
  
Korzystanie z Internetu jako konfiguracji kopii zapasowej nie jest zalecane. Powoduje to przerwanie zasady niezawodności woodgrove, co powoduje niespójne środowisko korzystania z połączenia. Ponadto ręczna konfiguracja byłaby wymagana do przełączenia w tryb failover, biorąc pod uwagę skonfigurowane anonse protokołu BGP, konfigurację translatora adresów sieciowych, konfigurację DNS i konfigurację serwera proxy. Ta dodatkowa złożoność trybu failover wydłuża czas odzyskiwania i zmniejsza ich zdolność do diagnozowania i rozwiązywania związanych z tym kroków.
  
Nadal masz pytania dotyczące planowania i implementowania zarządzania ruchem lub usługi Azure ExpressRoute? Przeczytaj pozostałe [wskazówki dotyczące sieci i wydajności](./network-planning-and-performance.md) lub często [zadawane pytania dotyczące usługi Azure ExpressRoute](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Praca z dostawcami usługi Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Wybierz lokalizacje obwodów na podstawie przepustowości, opóźnienia, zabezpieczeń i planowania wysokiej dostępności. Gdy znasz optymalne lokalizacje, chcesz umieścić obwody [, przeglądając bieżącą listę dostawców według regionów](/azure/expressroute/expressroute-locations).
  
Skontaktuj się z dostawcą lub dostawcami, aby wybrać najlepsze opcje łączności, punkt-punkt, wiele punktów lub hostowane. Pamiętaj, że możesz mieszać i dopasowywać opcje łączności, o ile przepustowość i inne nadmiarowe składniki obsługują projekt routingu i wysokiej dostępności.
  
Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>Tematy pokrewne
<a name="BKMK_high-availability"> </a>

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365](managing-expressroute-for-connectivity.md)
  
[Routing przy użyciu usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
  
[Implementowanie usługi ExpressRoute dla Office 365](implementing-expressroute.md)
  
[Używanie społeczności protokołu BGP w usłudze ExpressRoute na potrzeby scenariuszy Office 365](bgp-communities-in-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod kątem Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Usługi ExpressRoute i QoS w usłudze Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ wywołań przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)
  
[Office 365 punktów końcowych — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)