---
title: Planowanie sieci z usługą ExpressRoute dla sieci Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule dowiesz się więcej o usłudze Azure ExpressRoute dla systemu Office 365 o tym, jak używać jej do planowania sieci.
ms.openlocfilehash: d411d44ffe08da684b3cbca9a9449c4d04126a39
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019368"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planowanie sieci z usługą ExpressRoute dla sieci Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Usługa ExpressRoute dla Office 365 zapewnia łączność w warstwie 3 między Twoją siecią a centrami danych firmy Microsoft. Obwody korzystają z anonsów tras protokołu BGP (Border Gateway Protocol) Office 365 front front-end serwerów firmy Microsoft. Z perspektywy urządzeń lokalnych, gdy muszą wybrać prawidłową ścieżkę TCP/IP do usługi Office 365, usługa Azure ExpressRoute jest postrzegana jako alternatywa dla Internetu.
  
Usługa Azure ExpressRoute dodaje ścieżkę bezpośrednią do określonego zestawu obsługiwanych funkcji i usług oferowanych przez Office 365 w centrach danych firmy Microsoft. Usługa Azure ExpressRoute nie zastępuje łączności internetowej z centrami danych firmy Microsoft ani z podstawowymi usługami internetowymi, takimi jak rozpoznawania nazw domen. Usługa Azure ExpressRoute i obwody internetowe powinny być zabezpieczone i nadmiarowe.
  
W poniższej tabeli przedstawiono kilka różnic między połączeniami internetowymi i połączeniami usługi Azure ExpressRoute w kontekście usług Office 365.

|**Różnice w planowaniu sieci**|**Internetowe połączenie sieciowe**|**Połączenie sieciowe usługi ExpressRoute**|
|:-----|:-----|:-----|
| Dostęp do wymaganych usług internetowych, w tym:  <br/>  Rozpoznawanie nazw DNS  <br/>  Weryfikacja odwołań certyfikatów  <br/>  Sieci dostarczania zawartości (CDN)  <br/> |Tak  <br/> |Żądania do infrastruktury dns i/lub CDN DNS należącej do firmy Microsoft mogą korzystać z sieci usługi ExpressRoute.  <br/> |
| Dostęp do Office 365 usług internetowych, w tym:  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype dla firm Online  <br/>  Office w przeglądarce  <br/>  Office 365 portalu i uwierzytelniania  <br/> |Tak, wszystkie aplikacje i funkcje  <br/> |Tak, [konkretne aplikacje i funkcje](./urls-and-ip-address-ranges.md) <br/> |
|Zabezpieczenia lokalne w obwodzie.  <br/> |Tak  <br/> |Tak  <br/> |
|Planowanie wysokiej dostępności.  <br/> |Fail over to an alternate Internet network connection  <br/> |Fail over to an alternate ExpressRoute connection  <br/> |
|Połączenie bezpośrednie z przewidywalnym profilem sieciowym.  <br/> |Nie  <br/> |Tak  <br/> |
|Łączność IPv6.  <br/> |Tak  <br/> |Tak  <br/> |

Rozwiń poniższe tytuły, aby uzyskać więcej wskazówek dotyczących planowania sieci. Nagraliśmy również 10-częściową serię szkolenia Office 365 [Azure ExpressRoute](https://channel9.msdn.com/series/aer) dla klientów.

## <a name="existing-azure-expressroute-customers"></a>Obecni klienci usługi Azure ExpressRoute

Jeśli korzystasz z istniejącego obwodu usługi Azure ExpressRoute i chcesz dodać łączność usługi Office 365 za pośrednictwem tego obwodu, sprawdź liczbę obwodów, lokalizacji wychodzącej i rozmiaru obwodów, aby upewnić się, że spełnią one wymagania Twojego Office 365. Większość klientów wymaga dodatkowej przepustowości, a wielu klientów wymaga więcej obwodów.
  
Aby umożliwić dostęp do Office 365 za pośrednictwem istniejących obwodów usługi Azure ExpressRoute[, skonfiguruj](/azure/expressroute/how-to-routefilter-portal) filtry tras w celu zapewnienia dostępności Office 365 usług.
  
Subskrypcja usługi Azure ExpressRoute jest zorientowana na klienta, co oznacza, że subskrypcje są powiązane z klientami. Jako klient, możesz mieć wiele obwodów usługi Azure ExpressRoute i korzystać z wielu zasobów firmy Microsoft w chmurze za pośrednictwem tych obwodów. Na przykład możesz wybrać dostęp do hostowanej maszyny wirtualnej platformy Azure, dzierżawy testowej usługi Office 365 i dzierżawy produkcyjnej usługi Office 365 za pośrednictwem pary nadmiarowych obwodów usługi Azure ExpressRoute.
  
W poniższej tabeli przedstawiono dwa typy relacji komunikacji równorzędnej, które można zaimplementować za pośrednictwem obwodów.

|**Relacja komunikacji równorzędnej**|**Prywatna na platformie Azure**|**Microsoft**|
|:-----|:-----|:-----|
|**Usługi** <br/> |IaaS: Azure Virtual Machines  <br/> |PaaS: usługi publiczne platformy Azure  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Inicjowanie połączenia**** <br/> |U klienta do firmy Microsoft  <br/> Microsoft-to-Customer  <br/> |U klienta do firmy Microsoft  <br/> Microsoft-to-Customer  <br/> |
|**Obsługa QoS** <br/> |Brak QoS  <br/> |<sup>QoS1</sup> <br/> |

<sup>1 </sup> QoS obsługuje Skype dla firm w tej chwili tylko do odczytu.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planowanie przepustowości dla usługi Azure ExpressRoute

Każdy Office 365 ma unikatowe potrzeby w zakresie przepustowości w zależności od liczby osób w poszczególnych lokalizacjach, tego, jak aktywni są z każdą aplikacją Office 365 i innych czynników, takich jak użycie sprzętu lokalnego lub hybrydowego i konfiguracji zabezpieczeń sieciowych.
  
Zbyt mała przepustowość będzie skutkować przeciążeniem sieci, ponowną transmisji danych i nieprzewidywalnymi opóźnieniami. Zbyt duża przepustowość będzie skutkować niepotrzebnymi kosztami. W istniejącej sieci przepustowość jest często określana jako ilość dostępnej ilości miejsca w obwodzie jako wartość procentowa. 10% chętnych prawdopodobnie będzie skutkować przeciążeniem, a 80% może z reguły oznaczać niepotrzebne koszty. Typowe docelowy przydziały dla chętnych to od 20% do 50%.
  
Najlepszym mechanizmem znalezienia odpowiedniego poziomu przepustowości jest przetestowanie użycia istniejącej sieci. Jest to jedyny sposób uzyskania prawdziwej miary użycia i potrzeby, ponieważ każda konfiguracja sieci i aplikacje są pod pewnymi względami unikatowe. Podczas mierzenia należy zwrócić szczególną uwagę na całkowite wykorzystanie przepustowości, opóźnienia i obciążenie tcp, aby zrozumieć potrzeby sieci.
  
Po szacowanym planie bazowym, który obejmuje wszystkie aplikacje sieciowe, przekieruj program Office 365 do małej grupy osób, która składa się z różnych profilów osób w Twojej organizacji, aby ustalić rzeczywiste użycie, i użyj tych dwóch pomiarów, aby oszacować przepustowość, która będzie wymagana dla każdej lokalizacji biura. Jeśli podczas testowania występują jakiekolwiek opóźnienia lub problemy z przeciążeniem protokołu TCP, może być konieczne przeniesienie ruchu wychodzącego bliżej osób korzystających z programu Office 365 lub usunięcie intensywnego skanowania sieci, takiego jak odszyfrowywanie/inspekcja SSL.
  
Wszystkie nasze zalecenia dotyczące zalecanego typu przetwarzania sieci dotyczą zarówno obwodów usługi ExpressRoute, jak i obwodów internetowych. To samo dotyczy pozostałych wskazówek w [witrynie dostosowywania wydajności](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Stosowanie kontroli zabezpieczeń do usługi Azure ExpressRoute na Office 365 scenariuszy

W ramach zabezpieczania łączności usługi Azure ExpressRoute należy się ująć w te same zasady, co w przypadku zabezpieczania łączności internetowej. Wielu klientów decyduje się na wdrożenie kontrolek sieci i obwodu wzdłuż ścieżki usługi ExpressRoute łączącej ich sieć lokalną z Office 365 innymi chmurami firmy Microsoft. Takie mechanizmy kontroli mogą obejmować zapory, proxy aplikacji, zapobieganie wyciekom danych, systemy wykrywania intruzów, zapobiegania dostępowi itp. W wielu przypadkach klienci stosują różne poziomy kontroli do ruchu inicjowanego lokalnie, który trafia do firmy Microsoft, a nie do ruchu inicjowanego przez firmę Microsoft i trafia do sieci lokalnej klienta, a ruch inicjowany lokalnie, trafia do ogólnego miejsca docelowego Internetu.
  
Oto kilka przykładów integrowania zabezpieczeń z modelem łączności usługi [ExpressRoute,](/azure/expressroute/expressroute-connectivity-models) który wybierzesz do wdrożenia.

|**Opcja integracji z usługą ExpressRoute**|**Model obwodu zabezpieczeń sieci**|
|:-----|:-----|
|Współlokowana na giełdzie w chmurze  <br/> |Zainstaluj nową lub użyj istniejącej infrastruktury zabezpieczeń/obwodu w infrastrukturze kolokacji, w której jest ustanowione połączenie z usługą ExpressRoute.  <br/> Używaj infrastruktury kolokacji tylko do celów routingu/wzajemnych połączeń i połączeń powrotnych z infrastruktury kolokacji do lokalnej infrastruktury zabezpieczeń/obwodu.  <br/> |
|Punkt-punkt w sieci Ethernet  <br/> |Zakończ połączenie typu punkt-punkt z usługą ExpressRoute w istniejącej lokalnej lokalizacji infrastruktury zabezpieczeń/obwodu.  <br/> Zainstaluj nową infrastrukturę zabezpieczeń/obwodu specyficzną dla ścieżki expressRoute i zakończ tam połączenie typu punkt-punkt.  <br/> |
|Każdy z każdym (IPVPN)  <br/> |Użyj istniejącej lokalnej infrastruktury zabezpieczeń/obwodu we wszystkich lokalizacjach wychodzącej do połączenia IPVPN używanego dla usługi ExpressRoute na Office 365 sieciowej.  <br/> Przypinaj protokół IPVPN używany dla usługi ExpressRoute do Office 365 konkretnych lokalizacji lokalnych, które mają pełnić funkcje zabezpieczeń/obwodu.  <br/> |

Niektórzy dostawcy usług oferują również funkcje zarządzanych zabezpieczeń/obwodu w ramach swoich rozwiązań integracji z usługą Azure ExpressRoute.
  
Rozważając położenie topologii opcji obwodu sieci/zabezpieczeń używanych dla usługi ExpressRoute na Office 365 sieci, poniżej przedstawiono dodatkowe kwestie.
  
- Głębokość i typ kontrolek sieci/zabezpieczeń mogą mieć wpływ na wydajność i skalowalność Office 365 użytkownika.

- Przepływy wychodzące (lokalnie firmy\> Microsoft) i przychodzące (\>lokalne) [jeśli są włączone] mogą mieć inne wymagania. Te połączenia prawdopodobnie różnią się od połączeń wychodzących do ogólnych miejsc internetowych.

- Office 365 wymagań dotyczących portów/protokołów i niezbędnych podsieci IP są takie same niezależnie od tego, czy ruch jest przekierowywowyny przez usługę ExpressRoute dla sieci Office 365 czy za pośrednictwem Internetu.

- Topologii położenie kontroli sieci/zabezpieczeń klienta określa ostateczną sieć między użytkownikiem a usługą Office 365 i może mieć znaczny wpływ na opóźnienia i przeciążenia sieci.

- Zachęcamy klientów do projektowania topologii zabezpieczeń/obwodu do użytku z usługą ExpressRoute dla sieci Office 365 zgodnie z najlepszymi rozwiązaniami w zakresie nadmiarowości, wysokiej dostępności i odzyskiwania po awarii.

Oto przykład banku Woodgrove, który porównuje różne opcje łączności usługi Azure ExpressRoute z omówione powyżej modelami zabezpieczeń obwodu.
  
### <a name="example-1-securing-azure-expressroute"></a>Przykład 1. Zabezpieczanie usługi Azure ExpressRoute
  
Bank Woodgrove rozważa zaimplementowanie usługi Azure ExpressRoute i po zaplanowaniu optymalnej architektury na potrzeby routingu za pomocą usługi [ExpressRoute](routing-with-expressroute.md) dla usługi Office 365 i po zastosowaniu powyższych wskazówek do zrozumienia wymagań dotyczących przepustowości określa najlepszą metodę zabezpieczenia obwodu.
  
W przypadku bank Woodgrove, wielonarodowej organizacji z lokalizacjami na kilku kontynentach, zabezpieczenia muszą obejmować wszystkie obwody. Optymalna opcja łączności dla serwisu Woodgrove to połączenie wielopunktowe z wieloma lokalizacjami komunikacji równorzędnej na świecie do obsługi potrzeb pracowników na każdym kontynencie. Każdy kontynent zawiera nadmiarowe obwody usługi Azure ExpressRoute i zabezpieczenia muszą obejmować wszystkie te obwody.
  
Istniejąca infrastruktura banku Woodgrove jest niezawodna i może obsługiwać dodatkową pracę, dzięki temu bank Woodgrove może korzystać z tej infrastruktury na użytek zabezpieczeń swoich obwodów usługi Azure ExpressRoute i Internetu. Gdyby było inaczej, woodgrove może zakupić więcej sprzętu w celu uzupełnienia istniejącego sprzętu lub zdecydować się na obsługę innego typu połączenia.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Wysoka dostępność i trybu failover dzięki usłudze Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Zalecamy inicjowanie obsługi co najmniej dwóch aktywnych obwodów z każdego obwodu wychodzącego za pomocą usługi ExpressRoute do dostawcy usługi ExpressRoute. Jest to najczęściej spotykane u klientów błędy i można łatwo tego uniknąć, aprowując parę aktywnych/aktywnych obwodów usługi ExpressRoute. Zalecamy również co najmniej dwa aktywne/aktywne obwody internetowe, ponieważ wiele Office 365 internetowych jest dostępnych tylko przez Internet.
  
Wewnątrz punktu ruchu wychodzącego Twojej sieci znajduje się wiele innych urządzeń i obwodów, które odgrywają krytyczną rolę w odbieraniu dostępności przez osoby. Te fragmenty scenariuszy dotyczące łączności nie są objęte umowy sla slas usługi ExpressRoute ani usługi Office 365, ale odgrywają one krytyczną rolę w dostępności usługi postrzeganej przez osoby w organizacji.
  
Skoncentruj się na osobach korzystających z usługi i Office 365, jeśli awaria dowolnego jednego składnika wpłynęłaby na środowisko użytkowników usługi, poszukaj sposobów ograniczenia całkowitego procentu osób, których to dotyczy. Jeśli tryb failover jest operacyjnie złożony, weź pod uwagę czas długiego czasu odzyskiwania przez użytkowników na odzyskiwanie po awarii i poszukaj operacyjnie prostych i automatycznych trybów failover.
  
Poza siecią dostępność Office 365, usługi ExpressRoute i Twojego dostawcy usługi ExpressRoute.
  
### <a name="service-availability"></a>Dostępność usługi
  
- Office 365 usługi są objęte dobrze zdefiniowanymi umowami na poziomie [usług, które](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) obejmują metryki czasu bezaatywności i dostępności dla poszczególnych usług. Jednym z Office 365 utrzymania tak wysokiego poziomu dostępności usług jest możliwość płynnego przechodzenia między poszczególnymi składnikami między wieloma centrami danych firmy Microsoft przy użyciu globalnej sieci firmy Microsoft. Ta funkcja trybu failover rozciąga się od centrum danych i sieci do wielu internetowych punktów ruchu wychodzącego i umożliwia płynne przechodzenie do trybu failover z perspektywy użytkowników usługi.

- Usługa ExpressRoute zapewnia [na poziomie 99,9%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) umowy dotyczącej dostępności na podstawie umowy dotyczącej umowy dotyczącej dostępności dla pojedynczych dedykowanych obwodów między siecią Microsoft Edge a infrastrukturą dostawcy lub partnera usługi ExpressRoute. Te poziomy usług są stosowane na poziomie obwodu usługi ExpressRoute, który składa [](/azure/expressroute/expressroute-introduction) się z dwóch niezależnych połączeń między nadmiarowym sprzętem firmy Microsoft i sprzętem dostawcy sieci w każdej lokalizacji komunikacji równorzędnej.

### <a name="provider-availability"></a>Dostępność dostawcy
  
- Ustalenia dotyczące poziomu usług firmy Microsoft przestają być stosowane u dostawcy lub partnera usługi ExpressRoute. Jest to również pierwsze miejsce, w którym możesz wybrać opcje, które wpłyną na poziom dostępności. Należy dokładnie ocenić cechy architektury, dostępności i odporności, które oferuje Twój dostawca usługi ExpressRoute między obwodem Twojej sieci a połączeniem Twoich dostawców w każdej lokalizacji komunikacji równorzędnej firmy Microsoft. Zwróć szczególną uwagę zarówno na logiczne, jak i fizyczne aspekty nadmiarowości, sprzęt komunikacji równorzędnej, obwody sieci WAN dostarczane przez operatora oraz wszelkie usługi dodatkowe o wartościach dodane, takie jak usługi NAT lub zarządzane zapory.

### <a name="designing-your-availability-plan"></a>Projektowanie planu dostępności
  
W scenariuszach end-to-connectivity dla użytkowników zdecydowanie zalecamy zaplanowanie i zaprojektowanie wysokiej dostępności i odporności na Office 365. Projekt powinien zawierać następujące informacje:
  
- Brak pojedynczych punktów awarii, w tym obwodów internetowych i obwodów usługi ExpressRoute.

- Minimalizowanie liczby osób, których dotyczy problem i czasu trwania tego wpływu w przypadku większości przewidywanych trybów awarii.

- Optymalizacja procesu odzyskiwania po awarii z większości przewidywanych trybów awarii pod celu optymalizacji procesu odzyskiwania po awarii, który może być powtarzalny i automatyczny.

- Obsługa pełnych wymagań ruchu i funkcji sieciowych za pośrednictwem nadmiarowych ścieżek bez znacznego pogorszenia.

Scenariusze dotyczące łączności powinny uwzględniać topologię sieci zoptymalizowaną pod kątem wielu niezależnych i aktywnych ścieżek sieciowych do Office 365. Pozwoli to uzyskać lepszą dostępność w pełni niż w przypadku topologii zoptymalizowanej tylko pod kątem nadmiarowości na poziomie pojedynczego urządzenia lub sprzętu.
  
> [!TIP]
> Jeśli Twoi użytkownicy są dystrybuowani na wielu kontynentach lub w wielu regionach geograficznych, a każda z tych lokalizacji łączy się za pośrednictwem nadmiarowych obwodów sieci WAN z pojedynczą lokalizacją lokalną, w której znajduje się pojedynczy obwód usługi ExpressRoute, u tych użytkowników będzie mniejsza niż w przypadku projektu topologii sieci, który zawiera niezależne obwody usługi ExpressRoute łączące poszczególne regiony z najbliższą lokalizacją komunikacji równorzędnej.
  
Zalecamy inicjowanie obsługi co najmniej dwóch obwodów usługi ExpressRoute z każdym obwodem łączącym się z inną lokalizacją geograficznej komunikacji równorzędnej. Należy aprowizować tę aktywną parę obwodów dla każdego regionu, w którym ludzie będą korzystać z łączności usługi ExpressRoute Office 365 usługach. Dzięki temu każdy region pozostaje w kontakcie podczas awarii, która wpływa na główną lokalizację, taką jak centrum danych lub lokalizacja komunikacji równorzędnej. Ich skonfigurowanie jako aktywne/aktywne umożliwia rozmieszczenie ruchu użytkownika końcowego między wiele ścieżek sieciowych. Ogranicza to zakres osób, które mają wpływ na możliwość  sieciowych  usterek urządzeń lub urządzeń sieciowych.
  
Nie zalecamy używania pojedynczego obwodu usługi ExpressRoute z Internetem jako kopii zapasowej.
  
### <a name="example-2-failover-and-high-availability"></a>Przykład 2. Failover and High Availability
  
Projekt wielogeografiowy banku Woodgrove przeszedł przegląd w zakresie routingu, przepustowości i zabezpieczeń, a teraz musi przejść przegląd w zakresie wysokiej dostępności. Zdaniem woodgrove wysoką dostępność w przypadku trzech kategorii: odporność, niezawodność i nadmiarowość.
  
Odporność umożliwia bankowi Woodgrove szybkie odzyskiwanie po awarii. Niezawodność umożliwia woodgrove oferuje spójne wyniki w ramach systemu. Nadmiarowość umożliwia aplikacji Woodgrove przechodzenie między jednym lub większą liczby dublowanych wystąpień infrastruktury.
  
W obrębie każdej konfiguracji brzegowej woodgrove ma nadmiarowe zapory, proxy i identyfikatory. Dla Ameryki Północnej woodgrove ma jedną konfigurację brzegową w centrum danych w Dallas i drugą konfigurację brzegową w centrum danych w Virginii. Nadmiarowy sprzęt w poszczególnych lokalizacjach zapewnia odporność w tej lokalizacji.
  
Konfiguracja sieci w banku Woodgrove została zbudowana na kilku kluczowych zasadach:
  
- W każdym regionie geograficznym istnieje wiele obwodów usługi Azure ExpressRoute.

- Każdy obwód w regionie może obsługiwać cały ruch sieciowy w tym regionie.

- Routing wyraźnie preferuje jedną lub inną ścieżkę w zależności od dostępności, lokalizacji i tak dalej.

- Failover between Azure ExpressRoute circuits happens automatically without additional configuration or action required by Woodgrove.

- Failover between Internet circuits happens automatically without additional configuration or action required by Woodgrove.

W tej konfiguracji z nadmiarowością na poziomie fizycznym i wirtualnym bank Woodgrove może niezawodnie zapewnić odporność lokalną, regionalną i globalną. Bank Woodgrove wybrał tę konfigurację po dokonaniu oceny pojedynczego obwodu usługi Azure ExpressRoute na region oraz oceny możliwości pracy w trybie failing over to the Internet.
  
Jeśli usługa Woodgrove nie mogła mieć wielu obwodów usługi Azure ExpressRoute na region, ruch routingu pochodzący z Ameryki Północnej do obwodu usługi Azure ExpressRoute w regionie Azji i Pacyfiku dodałaby nieakceptowalny poziom opóźnień, a wymagana konfiguracja usługi przesyłania dalej DNS byłaby bardziej skomplikowana.
  
Używanie Internetu jako konfiguracji zapasowej nie jest zalecane. Stanowi to złamanie zasady niezawodności firmy Woodgrove, czego wynikiem jest niespójne korzystanie z połączenia. Ponadto wymagana byłaby ręczna konfiguracja, aby uwzględnić skonfigurowane anonse BGP, konfigurację NAT, konfigurację DNS i konfigurację serwera proxy. Dodana złożoność trybu failover wydłuża czas odzyskiwania i zmniejsza ich możliwości diagnozowania i rozwiązywania związanych z tym kroków.
  
Nadal masz pytania dotyczące sposobu zaplanowania i wdrożenia zarządzania ruchem lub usługi Azure ExpressRoute? Przeczytaj pozostałe nasze wskazówki dotyczące [sieci i wydajności](./network-planning-and-performance.md) lub Często zadawane [pytania dotyczące usługi Azure ExpressRoute](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Praca z dostawcami usługi Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Wybierz lokalizacje obwodów na podstawie przepustowości, opóźnień, zabezpieczeń i planowania wysokiej dostępności. Gdy znasz optymalne lokalizacje, chcesz umieścić obwody, przeglądać [bieżącą listę dostawców według regionów](/azure/expressroute/expressroute-locations).
  
We współpracy z dostawcą lub dostawcami wybierz najlepsze opcje łączności: typu punkt-punkt, wielopunktowe lub hostowane. Pamiętaj, że możesz mieszać i do pasować opcje łączności, o ile przepustowość i inne nadmiarowe składniki obsługują Twój projekt routingu i wysokiej dostępności.
  
Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>Tematy pokrewne
<a name="BKMK_high-availability"> </a>

[Ocena Office 365 sieci](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie łącznością sieciową za Office 365 ExpressRoute](managing-expressroute-for-connectivity.md)
  
[Routing za pomocą usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
  
[Implementowanie expressroute dla Office 365](implementing-expressroute.md)
  
[Używanie społeczności BGP w u usługi ExpressRoute na Office 365 scenariuszy](bgp-communities-in-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Usługi ExpressRoute i QoS w Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ połączeń przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)
  
[Office 365 punkty końcowe — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)