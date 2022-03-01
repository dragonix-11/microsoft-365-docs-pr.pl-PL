---
title: Implementowanie expressroute dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Dowiedz się, jak wdrożyć usługę ExpressRoute Office 365, która zapewnia alternatywną ścieżkę routingu do wielu internetowych Office 365 usług.
ms.openlocfilehash: 9fbfaec8304c0ad5273aed3f07cb3d32c590c638
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014690"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementowanie expressroute dla Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Usługa ExpressRoute dla Office 365 udostępnia alternatywną ścieżkę routingu do wielu internetowych Office 365 internetowych. Architektura usługi ExpressRoute dla usługi Office 365 jest oparta na reklamie publicznych prefiksów IP usług Office 365, które są już dostępne przez Internet dla Twoich aprowizowanych obwodów usługi ExpressRoute w celu ponownej redystrybucji tych prefiksów IP w Twojej sieci. Usługa ExpressRoute umożliwia efektywne włączenie kilku różnych ścieżek routingu dla wielu usług internetowych i za pośrednictwem Office 365 ExpressRoute. Ten stan routingu w Twojej sieci może oznaczać istotną zmianę sposobu zaprojektowania topologii sieci wewnętrznej.
  
 **Stan:** Pełny przewodnik w wersji 2
  
Implementację usługi ExpressRoute dla usługi Office 365 musisz starannie zaplanować, aby uwzględnić specyfikę sieci w zakresie dostępnego routingu za pośrednictwem zarówno obwodu dedykowanego z trasami wproszeń do sieci podstawowej, jak i Internetu. Jeśli nie przeprowadzasz ze swoim zespołem szczegółowego planowania i testowania w tym przewodniku, istnieje duże ryzyko, że po włączeniu obwodu usługi ExpressRoute przejściowo lub całkowita utrata łączności z usługami Office 365.
  
Aby mieć pomyślne wdrożenie, musisz przeanalizować wymagania swojej infrastruktury, przejść przez proces szczegółowej oceny i projektowania sieci, starannie zaplanować etapowe wdrożenie w kontrolowany sposób oraz utworzyć szczegółowy plan sprawdzania poprawności i testowania. W przypadku dużych, rozproszonych środowisk nie jest rzadkością wdrożenie obejmujące kilka miesięcy. Ten przewodnik ma na celu pomóc Ci w planowaniu z wyprzedzeniem.
  
Zaplanowanie dużego pomyślnego wdrożenia może potrwać sześć miesięcy. Często są to członkowie zespołu z wielu obszarów organizacji, w tym administratorzy sieci, zapory i serwera proxy, administratorzy Office 365, zabezpieczenia, wsparcie użytkownika końcowego, zarządzanie projektami i sponsorowanie kierownictwa. Inwestycja w proces planowania zmniejszy prawdopodobieństwo wystąpienia niepowodzeń wdrożenia wynikających z przestojów lub złożonych i kosztownych rozwiązywania problemów.
  
Oczekujemy, że przed rozpoczęciem tego przewodnika implementacji zostaną ukończone następujące wymagania wstępne.
  
1. Ukończono ocenę sieci w celu ustalenia, czy expressRoute jest zalecane i zatwierdzone.

2. Wybrano usługę sieciową usługi ExpressRoute, usługodawca. Znajdź szczegóły dotyczące [partnerów i lokalizacji komunikacji równorzędnej usługi ExpressRoute](/azure/expressroute/expressroute-locations).

3. Została już przeczytana i zrozumiana dokumentacja usługi [ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) , a Twoja sieć wewnętrzna może spełniać wszystkie wymagania wstępne usługi ExpressRoute.

4. Twój zespół [https://aka.ms/expressrouteoffice365](./azure-expressroute.md)przeczytał wszystkie publiczne wytyczne i dokumentację pod nr . [https://aka.ms/ert](https://aka.ms/ert)oraz obserwował serię szkoleń usługi [Azure ExpressRoute](https://channel9.msdn.com/series/aer) dla usługi Office 365 w kanale 9, aby zapoznać się z ważnymi szczegółami technicznymi, w tym:

      - Zależności internetowe usług SaaS.

      - Sposób unikania tras asymetrycznych oraz obsługi złożonego routingu.

      - Jak włączyć zabezpieczenia obwodu, dostępność i kontrolki na poziomie aplikacji.

## <a name="begin-by-gathering-requirements"></a>Rozpocznij od zbierania wymagań
<a name="requirements"> </a>

Zacznij od określenia funkcji i usług, które zamierzasz przyjąć w Twojej organizacji. Musisz określić, które funkcje różnych usług Office 365 będą używane i w których lokalizacjach w Twojej sieci będą hostować osoby korzystające z tych funkcji. Katalog scenariuszy wymaga dodawania atrybutów sieci wymaganych w każdym z tych scenariuszy. na przykład przychodzące i wychodzące przepływy ruchu sieciowego i jeśli Office 365 końcowe są dostępne za pośrednictwem usługi ExpressRoute.
  
Aby zebrać wymagania Twojej organizacji:
  
- Skataloguj przychodzący i wychodzący ruch sieciowy dla usług Office 365, z których korzysta Twoja organizacja. Aby uzyskać Office 365 wymaganych przez różne scenariusze, należy Office 365 adresy URL i zakresy adresów Office 365 IP.

- Zbierz dokumentację istniejącej topologii sieci przedstawiającą szczegóły wewnętrznej sieci szkieletowej i topologii sieci WAN, łączności witryn satelitarnych, łączności użytkownika ostatniej mili, routingu do punktów ruchu wychodzącego sieci obwodowej i usług serwera proxy.

  - Zidentyfikuj punkty końcowe usług przychodzących na diagramach sieci Office 365 z usługi firmy Microsoft będzie nawiązywane połączenie, pokazując zarówno ścieżki połączeń internetowych, jak i proponowane ścieżki połączeń usługi ExpressRoute.

  - Określ wszystkie lokalizacje geograficzne użytkowników i łączność WAN między lokalizacjami wraz z lokalizacjami, które obecnie mają ruch wychodzący do Internetu i które lokalizacje mają mieć ruch wychodzący do lokalizacji równorzędnej usługi ExpressRoute.

  - Zidentyfikuj wszystkie urządzenia brzegowe, takie jak proxy, zapory itp., i skataloguj ich relację z przepływami przechodzącymi przez Internet i usługę ExpressRoute.

  - Udokumentuj, czy użytkownicy końcowi będą Office 365 za pośrednictwem routingu bezpośredniego lub pośredniego serwera proxy aplikacji zarówno dla przepływów internetowych, jak i przepływów usługi ExpressRoute.

- Dodaj lokalizację dzierżawy i lokalizacje meet-me do diagramu sieciowego.

- Os szacuj oczekiwaną i obserwowaną wydajność sieci oraz charakterystyki opóźnień z lokalizacji głównych użytkowników do Office 365. Pamiętaj, że Office 365 jest globalnym i rozproszonym zestawem usług, a użytkownicy będą nawiązywać połączenia z lokalizacjami, które mogą różnić się od lokalizacji dzierżawy. Z tego powodu zaleca się mierzenie i optymalizowanie opóźnień między użytkownikiem a najbliższą krawędzią globalnej sieci firmy Microsoft przez połączenia usługi ExpressRoute i Internetu. Aby pomóc w tym zadaniu, możesz skorzystać z wniosków z oceny sieci.

- Wymień wymagania związane z zabezpieczeniami i wysoką dostępnością sieci firmowej, które muszą być spełnione w przypadku nowego połączenia usługi ExpressRoute. Na przykład sposób kontynuacji dostępu użytkowników do usługi Office 365 w przypadku ruchu wychodzącego do Internetu lub awarii obwodu usługi ExpressRoute.

- Udokumentuj, które przepływy Office 365 wychodzącej będą używać ścieżki internetowej, a które usługi ExpressRoute. Specyfika lokalizacji geograficznych użytkowników i szczegóły topologii Twojej sieci lokalnej mogą wymagać, aby plan różnił się od jednej lokalizacji użytkownika.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Skatalogowanie przychodzącego i wychodzącego ruchu sieciowego
<a name="trafficCatalog"> </a>

W celu zminimalizowania routingu i innych złożonych kwestii sieci zalecamy używanie usługi ExpressRoute tylko dla usługi Office 365 w przypadku przepływów ruchu sieciowego, które są wymagane do przekierowania przez połączenie dedykowane ze względu na wymagania prawne lub jako wynik oceny sieci. Ponadto zalecamy, aby etapować zakres routingu usługi ExpressRoute oraz podejście do wychodzących i przychodzących przepływów ruchu sieciowego jako różnych i odrębnych etapów projektu implementacji. Wdrażanie usługi ExpressRoute dla usługi Office 365 tylko dla wychodzących przepływów ruchu sieciowego inicjowanych przez użytkowników i pozostawienie przychodzących przepływów ruchu sieciowego w Internecie może ułatwić kontrolowanie wzrostu złożoności topologii i ryzyka związanego z wprowadzeniem dodatkowych możliwości routingu asymetrycznego.
  
Katalog ruchu sieciowego powinien zawierać listy wszystkich przychodzących i wychodzących połączeń sieciowych, które będą mieć połączenia między Twoją siecią lokalną a firmą Microsoft.
  
- Wychodzące przepływy ruchu sieciowego to wszystkie scenariusze, w których połączenie jest inicjowane z Twojego środowiska lokalnego, na przykład z klientów lub serwerów wewnętrznych, a miejscem docelowym jest usługi firmy Microsoft. Te połączenia mogą być skierowane bezpośrednio Office 365 lub pośrednie, na przykład gdy na ścieżce do serwera proxy, zapór lub innych urządzeń sieciowych przechodzi połączenie Office 365.

- Przychodzące przepływy ruchu sieciowego to wszystkie scenariusze, w których połączenie jest inicjowane z chmury firmy Microsoft do hosta lokalnego. Te połączenia zazwyczaj muszą przejść przez zaporę i inną infrastrukturę zabezpieczeń, której wymagają zasady zabezpieczeń klienta w przypadku przepływów pochodzących zewnętrznie.

Przeczytaj sekcję Zapewnianie **symetrii** tras w artykule Routing za pomocą usługi [ExpressRoute](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) dla usługi Office 365, aby określić, które usługi będą wysyłać ruch przychodzący, i odszukaj kolumnę oznaczoną jako **ExpressRoute** dla usługi Office 365 w artykule z informacją na temat punktów końcowych usługi [Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2), aby ustalić pozostałe informacje o łączności.
  
W przypadku każdej usługi, która wymaga połączenia wychodzącego, możesz opisać planowaną łączność usługi, w tym routing sieciowy, konfigurację serwera proxy, inspekcję pakietów i potrzeby w zakresie przepustowości.
  
Dla każdej usługi, która wymaga połączenia przychodzącego, będą potrzebne pewne dodatkowe informacje. Serwery w chmurze firmy Microsoft będą nawiązywać połączenia z Twoją siecią lokalną. Aby zapewnić poprawne połączenia, możesz opisać wszystkie aspekty tej łączności, w tym: wpisy publicznych serwerów DNS dla usług, które będą akceptowały te połączenia przychodzące, adresy IP IPv4 w formacie CIDR, używany sprzęt obsługiwanego przez isp oraz sposób obsługi źródłowego nat lub nat ruchu przychodzącego dla tych połączeń.
  
Połączenia przychodzące należy przejrzeć niezależnie od tego, czy nawiązały połączenie przez Internet, czy za pośrednictwem usługi ExpressRoute, aby upewnić się, że nie został wprowadzony routing asymetryczny. W niektórych przypadkach lokalne punkty końcowe, z Office 365 inicjują połączenia przychodzące, także muszą być używane przez inną firmę Microsoft i inną firmę usługi firmy Microsoft. Najważniejsze, aby włączenie routingu usługi ExpressRoute do tych usług na Office 365 nie awarii innych scenariuszy. W wielu przypadkach klienci muszą zaimplementować określone zmiany w swojej sieci wewnętrznej, takie jak źródłowy nat, aby zapewnić, że przepływy przychodzące od firmy Microsoft pozostaną symetryczne po włączeniu usługi ExpressRoute.
  
Oto przykładowy poziom wymaganych szczegółów. W tym przypadku Exchange hybrydowe będzie kierowane do systemu lokalnego przez usługę ExpressRoute. 

|Właściwość połączenia   |Value  |
|----------|-----------|
|**Kierunek ruchu sieciowego** <br/> |Przychodzący  <br/> |
|**Usługa** <br/> |Wdrożenie hybrydowe programu Exchange  <br/> |
|**Publiczny Office 365 końcowy (źródło)** <br/> |Exchange Online (adresy IP)  <br/> |
|**Publiczny lokalny punkt końcowy (miejsce docelowe)** <br/> |5.5.5.5  <br/> |
|**Publiczny (internetowy) wpis DNS** <br/> |Autodiscover.contoso.com  <br/> |
|**Czy ten lokalny punkt końcowy będzie używany przez inne (inne niż Office 365) usługi firmy Microsoft** <br/> |Nie  <br/> |
|**Czy ten lokalny punkt końcowy będzie używany przez użytkowników/systemy w Internecie** <br/> |Tak  <br/> |
|**Systemy wewnętrzne publikowane za pośrednictwem publicznych punktów końcowych** <br/> |Exchange Server dostępu klienta (lokalnie) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Ogłoszenie IP dla publicznego punktu końcowego** <br/> |**Do Internetu**: 5.5.0.0/16 **do usługi ExpressRoute**: 5.5.5.0/24  <br/> |
|**Kontrolki zabezpieczeń/obwodu** <br/> |**Ścieżka internetowa**: DeviceID_002  **usługi ExpressRoute**: DeviceID_003  <br/> |
|**Wysoka dostępność** <br/> |Aktywna/aktywna przez 2 nadmiarowe lokalizacje geograficzne / obwody usługi ExpressRoute — Chicago i Dallas  <br/> |
|**Kontrola symetrii ścieżki** <br/> |Metoda **: Source** NAT **Internet path**: Source NAT inbound connections to 192.168.5.5 **ExpressRoute path**: Source NAT connections to 192.168.1.0 (Chicago) and 192.168.2.0 (Dallas)  <br/> |

Oto przykładowa usługa, która jest tylko usługą wychodzącą:

|**Właściwość połączenia**|**Wartość**|
|----------|-----------|
|**Kierunek ruchu sieciowego** <br/> |Wychodzące  <br/> |
|**Usługa** <br/> |SharePoint Online  <br/> |
|**Lokalny punkt końcowy (źródło)** <br/> |Stacja robocza użytkownika  <br/> |
|**Publiczny Office 365 końcowy (miejsce docelowe)** <br/> |SharePoint online (adresy IP)  <br/> |
|**Publiczny (internetowy) wpis DNS** <br/> |\*sharepoint.com (i nie tylko)  <br/> |
|**CDN polecane** <br/> |cdn.sharepointonline.com (i nie tylko) — adresy IP utrzymywane przez CDN internetowych)  <br/> |
|**Ogłoszenia IP i nat w użyciu** <br/> |**Ścieżka internetowa/źródłowy nat**: 1.1.1.0/24  <br/> **Ścieżka expressRoute/źródłowy nat**: 1.1.2.0/24 (Chicago) i 1.1.3.0/24 (Dallas)  <br/> |
|**Metoda łączności** <br/> |**Internet**: za pośrednictwem serwera proxy warstwy 7 (plik pac)  <br/> **ExpressRoute**: routing bezpośredni (bez serwera proxy)  <br/> |
|**Kontrolki zabezpieczeń/obwodu** <br/> |**Ścieżka internetowa**: DeviceID_002  <br/> **Ścieżka expressRoute**: DeviceID_003  <br/> |
|**Wysoka dostępność** <br/> |**Ścieżka internetowa**: Nadmiarowy internetowy ruch wychodzący  <br/> **Ścieżka usługi ExpressRoute**: Aktywny/aktywny routing typu "gorący kartofel" przez 2 nadmiarowe obwody geograficzne usługi ExpressRoute — Chicago i Dallas  <br/> |
|**Kontrola symetrii ścieżki** <br/> |**Metoda**: źródłowy nat dla wszystkich połączeń  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Projekt topologii sieci z łącznością regionalną
<a name="topology"> </a>

Gdy zrozumiesz usługi i skojarzone z nimi przepływy ruchu sieciowego, możesz utworzyć diagram sieciowy, który uwzględnia te nowe wymagania dotyczące łączności i ilustruje zmiany, które zostaną wprowadzone w celu używania usługi ExpressRoute do Office 365. Diagram powinien zawierać:
  
1. Wszystkie lokalizacje użytkowników, z Office 365 i innych usług, będą dostępne.

2. Wszystkie punkty wychodzące za pośrednictwem Internetu i usługi ExpressRoute.

3. Wszystkie urządzenia wychodzące i przychodzące, które zarządzają łącznością do i z sieci, w tym routery, zapory, serwery proxy aplikacji oraz urządzenia do wykrywania i zapobiegania dostępowi.

4. Wewnętrzne miejsca docelowe dla całego ruchu przychodzącego, takie jak wewnętrzne serwery usług ADFS akceptujące połączenia z serwerów proxy aplikacji sieci Web usług ADFS.

5. Katalog wszystkich podsieci IP, które będą ogłaszane

6. Określ każdą lokalizację, do której inne osoby będą Office 365, i określ lokalizacje meet-me, które będą używane dla usługi ExpressRoute.

7. Lokalizacje i fragmenty topologii sieci wewnętrznej, w których prefiksy IP firmy Microsoft poznane z usługi ExpressRoute będą akceptowane, filtrowane i propagowane.

8. Topologia sieci powinna przedstawiać lokalizację geograficzną każdego segmentu sieci i sposób jej połączenia z siecią firmy Microsoft za pośrednictwem usługi ExpressRoute i/lub Internetu.

Na poniższym diagramie przedstawiono każdą lokalizację, z której będą Office 365 inne osoby, wraz z ogłoszeniami routingu przychodzącego i wychodzącego do połączeń Office 365.
  
![Regionalne geograficzne lokalizacje meet-me w utercie ExpressRoute.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
W przypadku ruchu wychodzącego dostęp osób Office 365 w jeden z trzech sposobów:
  
1. Za pośrednictwem lokalizacji meet-me w Ameryce Północnej dla osób z Kalifornii.

2. Za pośrednictwem lokalizacji meet-me w Hongkongu dla osób z Hongkongu.

3. Za pośrednictwem Internetu w Bangladeszu, w którym jest mniej osób i nie jest aprowowany obwód usługi ExpressRoute.

![Połączenia wychodzące dla diagramu regionalnego.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Podobnie przychodzący ruch sieciowy z usługi Office 365 zwraca się w jeden z trzech sposobów:
  
1. Za pośrednictwem lokalizacji meet-me w Ameryce Północnej dla osób z Kalifornii.

2. Za pośrednictwem lokalizacji meet-me w Hongkongu dla osób z Hongkongu.

3. Za pośrednictwem Internetu w Bangladeszu, w którym jest mniej osób i nie jest aprowowany obwód usługi ExpressRoute.

![Połączenia przychodzące dla diagramu regionalnego.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Określanie odpowiedniej lokalizacji meet-me

Wybór lokalizacji meet-me, czyli fizycznej lokalizacji, w której obwód usługi ExpressRoute łączy Twoją sieć z siecią firmy Microsoft, zależy od lokalizacji, z których ludzie będą mieli dostęp Office 365 sieci. Jako oferta SaaS Office 365 nie działa w ramach modelu regionalnego IaaS lub PaaS w taki sam sposób jak platforma Azure. Zamiast Office 365 to rozłożony zestaw usług współpracy, w którym użytkownicy mogą łączyć się z punktami końcowymi w wielu centrach danych i regionach, które mogą nie być w tej samej lokalizacji lub regionie, w którym jest hostowana dzierżawa użytkownika.
  
Oznacza to, że najważniejszą kwestią, która należy uwzględnić podczas wybierania lokalizacji meet-me dla usługi ExpressRoute dla usługi Office 365 jest miejsce, z którego będą się łączyć osoby w Twojej organizacji. Zaleceniem ogólnym dla optymalnej łączności Office 365 jest zaimplementowanie routingu, aby żądania użytkowników do usług Office 365 były do nich dodawana do sieci firmy Microsoft najkrótszą ścieżką sieciową, co często jest nazywane routingiem "gorącym kartofelem". Na przykład jeśli większość użytkowników usługi Office 365 znajduje się w jednej lub dwóch lokalizacjach, wybranie lokalizacji meet-me, które znajdują się w najbliższej odległości od lokalizacji tych użytkowników, spowoduje utworzenie optymalnego projektu. Jeśli Twoja firma ma duże populacje użytkowników w wielu różnych regionach, warto rozważyć posiadanie wielu obwodów usługi ExpressRoute i lokalizacji meet-me. W przypadku niektórych lokalizacji użytkowników najkrótsza/najbardziej optymalna ścieżka do sieci firmy Microsoft i usługi Office 365 może być różnić się od wewnętrznej sieci WAN i punktów meet-me usługi ExpressRoute, ale za pośrednictwem Internetu.
  
Często istnieje wiele lokalizacji meet-me, które można wybrać w regionie o względnej odległości od użytkowników. Wypełnij następującą tabelę, aby podejmować decyzje.

**Planowane lokalizacje meet-me usługi ExpressRoute w Kalifornii i Nowym Jorku**

|Lokalizacja  <br/> |Liczba osób  <br/> |Oczekiwane opóźnienie do sieci firmy Microsoft za pośrednictwem internetowego ruchu wychodzącego  <br/> |Oczekiwane opóźnienie do sieci firmy Microsoft przez usługę ExpressRoute  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10,000  <br/> |~15 min  <br/> |~10 m (przez Dolinę Krzemową)  <br/> |
|Waszyngton DC  <br/> |15,000  <br/> |~20 m  <br/> |~10 m (przez Nowy Jork)  <br/> |
|Dallas  <br/> |5,000  <br/> |~15 min  <br/> |~40 m (przez Nowy Jork)  <br/> |

Gdy globalna architektura sieciowa przedstawiająca region Office 365, lokalizacje meet-me sieci usługi ExpressRo usługodawca ute oraz liczbę osób według lokalizacji została opracowana, można jej użyć do określenia, czy można wywęsić jakiekolwiek optymalizacje. Może też pokazywać globalne połączenia sieciowe ze spinką, gdzie ruch jest przekierowywowyny do odległej lokalizacji w celu uzyskania dostępu do lokalizacji meet-me. W przypadku odkrycia spinki w sieci globalnej przed kontynuowaniem należy ją rozwiązać. Znajdź inną lokalizację meet-me lub użyj selektywnych punktów połączeń wychodzącej z Internetu, aby uniknąć spinki.
  
Na pierwszym diagramie pokazano przykładowego klienta z dwoma lokalizacjami fizycznymi w Ameryce Północnej. Możesz wyświetlić informacje o lokalizacjach biura, lokalizacjach Office 365 dzierżawy oraz kilka opcji lokalizacji meet-me usługi ExpressRoute. W tym przykładzie klient wybrał lokalizację meet-me w oparciu o dwie zasady w następującej kolejności:
  
1. Najbliższa odległość do osób w organizacji.

2. Najbliższa odległość do centrum danych firmy Microsoft, w którym Office 365 jest hostowane.

![Geograficzne lokalizacje meet-me w Usa w uchcie ExpressRoute.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Nieco bardziej rozwijając tę koncepcję, drugi diagram przedstawia przykładowego klienta wielonarodowego, który ma podobne informacje i musi podjąć podobne decyzje. Ten klient ma małe biuro w Bangladeszu z niewielkim zespołem 10 osób, skupionym na ilości miejsca w regionie. Istnieje lokalizacja meet-me w Chennai i centrum danych firmy Microsoft z usługą Office 365 hostowaną w Chennai, więc lokalizacja meet-me byłaby sensowna, jednak dla dziesięciu osób koszt dodatkowego obwodu jest uciążliwy. Podczas gdy przyjrzysz się swojej sieci, musisz określić, czy opóźnienie związane z wysyłaniem ruchu sieciowego przez Twoją sieć jest bardziej efektywne niż wydawanie pieniędzy na zakup kolejnego obwodu usługi ExpressRoute.
  
Dziesięć osób w Bangladeszu może mieć lepszą wydajność, jeśli ruch w swojej sieci jest przesyłany przez Internet do sieci firmy Microsoft, niż przekierowywają oni w swojej sieci wewnętrznej, jak pokazaliśmy na diagramach wprowadzających i  powielaliśmy poniżej.
  
![Połączenia wychodzące dla diagramu regionalnego.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Tworzenie planu implementacji Office 365 ExpressRoute
<a name="implementation"> </a>

Twój plan implementacji powinien obejmować zarówno szczegóły techniczne konfigurowania usługi ExpressRoute, jak i szczegóły konfigurowania całej pozostałej infrastruktury sieci, takie jak poniższe.
  
- Zaplanuj podział usług między usługę ExpressRoute i Internet.

- Zaplanuj przepustowość, zabezpieczenia, wysoką dostępność i trybu failover.

- Projektowanie routingu przychodzącego i wychodzącego, w tym odpowiedniej optymalizacji ścieżki routingu dla różnych lokalizacji

- Zdecyduj, jak daleko trasy usługi ExpressRoute będą ogłaszane w sieci i jaki jest mechanizm wybierania ścieżki internetowej lub ścieżki usługi ExpressRoute przez klientów. na przykład routing bezpośredni lub serwer proxy aplikacji.

- Zaplanuj zmiany rekordu DNS, uwzględniając wpisy [struktury zasad dotyczących nadawców](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) .

- Zaplanuj strategię NAT, w tym źródłowy nat ruchu wychodzącego i przychodzącego.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planowanie routingu za pomocą ścieżek sieciowych zarówno internetowych, jak i sieciowych usługi ExpressRoute
<a name="paths"> </a>

- Na wdrożenie wstępne zalecamy korzystanie z Internetu we wszystkich usługach przychodzących, takich jak ruchoma poczta e-mail lub łączność hybrydowa.

- Zaplanuj routing sieci LAN klienta użytkownika końcowego, na przykład konfigurując plik [PAC/WPAD](./managing-office-365-endpoints.md), trasę domyślną, serwery proxy i ogłoszenia trasy BGP.

- Zaplanuj routing sieci obwodowej, w tym serwery proxy, zapory i serwery proxy w chmurze.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planowanie przepustowości, zabezpieczeń, wysokiej dostępności i trybu failover
<a name="availability"> </a>

Utwórz plan na potrzeby przepustowości wymaganej dla każdego z głównych obciążeń Office 365 sieci. Oddzielnie osąduj Exchange Online, SharePoint online i Skype dla firm w zakresie przepustowości online. Jako punktu wyjścia możesz użyć kalkulatorów szacowania, które zostały przez nas dostarczone dla usług Exchange Online i Skype dla firm. Do pełnego zrozumienia potrzeb w zakresie przepustowości Twojej organizacji jest jednak wymagany test pilotażowy z reprezentatywną próbką profilów użytkowników i lokalizacji.
  
Dodaj do planu sposób obsługi zabezpieczeń w każdej lokalizacji internetowej i wychodzącej usługi ExpressRoute. Pamiętaj, że wszystkie połączenia usługi ExpressRoute z usługą Office 365 korzystają z publicznej komunikacji równorzędnej i nadal muszą być zabezpieczone zgodnie z zasadami zabezpieczeń Twojej firmy w zakresie łączenia się z sieciami zewnętrznymi.
  
Dodaj do planu szczegółowe informacje o tym, jaki typ  usterek będzie miał wpływ na jakie osoby oraz w jaki sposób te osoby będą mogły wykonywać swoją pracę z pełną wydajnością w najprostszy sposób.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planowanie wymagań w zakresie przepustowości, Skype dla firm w tym wymagań dotyczących zakłóceń, opóźnień, przeciążenia i łęk
  
Skype dla firm online mają również określone dodatkowe wymagania dotyczące sieci, o których szczegółowo o mowa w artykule Jakość multimediów i wydajność łączności sieciowej w u [Skype dla firm Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Przeczytaj sekcję **Planowanie przepustowości dla usługi Azure ExpressRoute** w tece Planowanie sieci z usługą [ExpressRoute dla sieci Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Podczas przeprowadzania oceny przepustowości z użytkownikami pilotażowymi możesz skorzystać z naszego przewodnika. [Office 365 wydajności przy użyciu planu bazowego i historii wydajności](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planowanie wymagań dotyczących wysokiej dostępności
  
Utwórz plan wysokiej dostępności spełniający Twoje potrzeby i uwzględniaj go na zaktualizowanym diagramie topologii sieci. Przeczytaj sekcję **Wysoka dostępność i trybu failover dzięki usłudze Azure ExpressRoute** w tesłudze planowania sieci z usługą [ExpressRoute dla sieci Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planowanie wymagań dotyczących zabezpieczeń sieci
  
Utwórz plan, aby spełnić wymagania dotyczące zabezpieczeń sieci i uwzględnić go na zaktualizowanym diagramie topologii sieci. Przeczytaj sekcję **Stosowanie kontrolek zabezpieczeń do usługi Azure ExpressRoute na** Office 365 scenariuszy w te dotyczące planowania sieci z usługą [ExpressRoute dla Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Projektowanie łączności usług wychodzących
<a name="outbound"> </a>

ExpressRoute dla Office 365 *ma wymagania dotyczące* sieci wychodzącej, które mogą być nieznane. W szczególności adresy IP, które reprezentują użytkowników i sieci w celu Office 365 i działają jako punkty końcowe źródła dla wychodzących połączeń sieciowych do firmy Microsoft, muszą spełniać określone wymagania opisane poniżej.
  
1. Punkty końcowe muszą być publicznymi adresami IP zarejestrowanymi dla Twojej firmy lub dla operatora dostarczającego Ci łączność z usługą ExpressRoute.

2. Punkty końcowe muszą być ogłaszane do firmy Microsoft i weryfikowane/akceptowane przez usługę ExpressRoute.

3. Punkty końcowe nie mogą być ogłaszane do Internetu z taką samą lub bardziej preferowaną metryką routingu.

4. Punkty końcowe nie mogą być używane do łączności z usługi firmy Microsoft, które nie są skonfigurowane za pośrednictwem usługi ExpressRoute.

Jeśli projekt Twojej sieci nie spełnia tych wymagań, istnieje duże ryzyko, że użytkownicy będą odczuwali awarie łączności z usługą Office 365 i innymi usługami usługi firmy Microsoft z powodu czarnych dziur w trasach lub routingu asymetrycznego. Dzieje się tak, gdy żądania do usługi usługi firmy Microsoft są kierowane przez usługę ExpressRoute, ale odpowiedzi są kierowane z powrotem przez Internet lub odwrotnie, a odpowiedzi są upuszczane przez urządzenia sieciowe o stanie, takie jak zapory.
  
Najpopularniejszą metodą spełniania powyższych wymagań jest użycie źródłowego rodzaju NAT zaimplementowanego w ramach Twojej sieci lub udostępnianego przez operatora usługi ExpressRoute. Źródłowy protokół NAT umożliwia pozyskiwanie szczegółów i prywatnych adresów IP Twojej sieci internetowej z usługi ExpressRoute oraz w połączeniu z właściwymi ogłoszeniami tras IP, zapewniają prosty mechanizm zapewniający symetrię ścieżek. Jeśli korzystasz z urządzeń sieciowych o określonym stanie, które są specyficzne dla lokalizacji komunikacji równorzędnej usługi ExpressRoute, musisz zaimplementować oddzielne pule NAT dla każdej komunikacji równorzędnej usługi ExpressRoute, aby zapewnić symetrię ścieżek.
  
Dowiedz się więcej o wymaganiach [dotyczących nat nat w uterze ExpressRoute](/azure/expressroute/expressroute-nat).
  
Dodaj zmiany dotyczące łączności wychodzącej do diagramu topologii sieci.
  
### <a name="design-inbound-service-connectivity"></a>Projektowanie łączności usług przychodzących
<a name="inbound"> </a>

Większość wdrożeń usługi Enterprise Office 365 zakłada pewien typ łączności przychodzącej z usługi Office 365 do usług lokalnych, na przykład w przypadku scenariuszy hybrydowych usług Exchange, SharePoint i Skype dla firm, migracji skrzynek pocztowych oraz uwierzytelniania przy użyciu infrastruktury usług ADFS. Gdy włączasz dodatkową ścieżkę routingu między siecią lokalną a firmą Microsoft w celu łączności wychodzącej przez usługę ExpressRoute, na te połączenia przychodzące może mieć niezamierzony wpływ routing asymetryczny, nawet jeśli te przepływy powinny nadal korzystać z Internetu. Zaleca się stosowanie kilku opisanych poniżej środków ostrożności w celu zagwarantowania, że internetowe przepływy przychodzące z Office 365 do systemów lokalnych nie mają wpływu.
  
Aby zminimalizować ryzyko routingu asymetrycznego dla przepływów przychodzącego ruchu sieciowego, wszystkie połączenia przychodzące powinny używać źródłowego nat, zanim będą kierowane do segmentów sieci, które mają widoczność routingu do usługi ExpressRoute. Jeśli połączenia przychodzące są dozwolone do segmentu sieci z widocznością routingu do usługi ExpressRoute bez źródłowego nat, żądania pochodzące z usługi Office 365 będą wchodzić z Internetu, ale odpowiedź wracająca do usługi Office 365 preferuje ścieżkę sieciową usługi ExpressRoute z powrotem do sieci firmy Microsoft, powodując routing asymetryczny.
  
Aby spełnić to wymaganie, możesz rozważyć jeden z następujących wzorców implementacji:
  
1. Przekieruj źródłowy obiekt NAT przed rozsyłaniem żądań do Twojej sieci wewnętrznej przy użyciu urządzeń sieciowych, takich jak zapory lub urządzenia do równoważenia obciążenia na ścieżce z Internetu do Twoich systemów lokalnych.

2. Upewnij się, że trasy usługi ExpressRoute nie są propagowane do segmentów sieci, w których znajdują się usługi przychodzące, takie jak serwery front end lub zwrotne systemy proxy, które obsługiją połączenia internetowe.

Jawne księgowanie tych scenariuszy w Twojej sieci i przechowywanie wszystkich przepływów przychodzącego ruchu sieciowego przez Internet pomaga zminimalizować ryzyko wdrażania i operacyjnej routingu asymetrycznego.
  
Mogą się okazać przypadki, w których zdecydujesz się skierować część przepływów przychodzących przez połączenia expressRoute. W przypadku takich scenariuszy weź pod uwagę następujące kwestie dodatkowe.
  
1. Office 365 mogą być kierowane tylko lokalne punkty końcowe, które używają publicznych punktów IP. Oznacza to, że nawet jeśli lokalnych punktów końcowych ruchu przychodzącego jest widoczne tylko dla usługi Office 365 przez usługę ExpressRoute, nadal musi z nim być skojarzony publiczny adres IP.

2. Wszystkie rozpoznawanie nazw DNS, które Office 365 w celu rozpoznania lokalnych punktów końcowych, odbywa się przy użyciu publicznego systemu DNS. Oznacza to, że musisz zarejestrować fQDN punktów końcowych ruchu przychodzącego do mapowania adresów IP w Internecie.

3. Aby można było odbierać przychodzące połączenia sieciowe przez usługę ExpressRoute, publiczne podsieci IP dla tych punktów końcowych muszą być ogłaszane do firmy Microsoft przez usługę ExpressRoute.

4. Starannie oceń te przepływy przychodzącego ruchu sieciowego, aby upewnić się, że zastosowano do nich odpowiednie mechanizmy kontroli zabezpieczeń i sieci zgodnie z firmową zasadami zabezpieczeń i sieci.

5. Gdy Twoje lokalne punkty końcowe ruchu przychodzącego są ogłaszane do firmy Microsoft przez usługę ExpressRoute, usługa ExpressRoute efektywnie staje się preferowaną ścieżką routingu do tych punktów końcowych dla wszystkich usług usługi firmy Microsoft, w tym do Office 365. Oznacza to, że te podsieci punktów końcowych mogą być używane tylko do komunikacji z Office 365 usługami firmy Microsoft i nie mogą być używane żadne inne usługi w sieci firmy Microsoft. W przeciwnym razie Twój projekt spowoduje routing asymetryczny, w którym połączenia przychodzące z innych usług usługi firmy Microsoft będą preferować routing ruchu przychodzącego przez usługę ExpressRoute, a ścieżka zwrotna będzie używać Internetu.

6. Jeśli obwód usługi ExpressRoute lub lokalizacja meet-me utkną, musisz upewnić się, że lokalne punkty końcowe ruchu przychodzącego są nadal dostępne, aby akceptować żądania za pośrednictwem oddzielnej ścieżki sieciowej. Może to oznaczać reklamowanie podsieci dla tych punktów końcowych za pośrednictwem wielu obwodów usługi ExpressRoute.

7. Zalecamy stosowanie źródłowego ustawienia NAT dla wszystkich przepływów przychodzącego ruchu sieciowego przychodzących do Twojej sieci za pośrednictwem usługi ExpressRoute, zwłaszcza w sytuacji, gdy te przepływy przecinają urządzenia sieciowe o różnych stanach, takie jak zapory.

8. Niektóre usługi lokalne, takie jak serwer proxy usług ADFS Exchange wykrywania automatycznego, mogą odbierać żądania przychodzące zarówno od Office 365, jak i od użytkowników z Internetu. Dla tych żądań Office 365 tej samej nazwy FQDN, co żądania użytkowników przez Internet. Zezwolenie na przychodzące połączenia użytkownika z Internetu do tych lokalnych punktów końcowych i Office 365 połączeń w celu używania usługi ExpressRoute oznacza znaczącą złożoność routingu. Dla zdecydowanej większości klientów implementowanie tak złożonych scenariuszy przez usługę ExpressRoute nie jest zalecane ze względów operacyjnych. To dodatkowe obciążenie obejmuje zarządzanie zagrożeniami związanych z routingiem asymetrycznym i będzie wymagać dokładnego zarządzania ogłoszeniami routingu i zasadami w wielu wymiarach.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Aktualizowanie planu topologii sieci w celu pokazania sposobu uniknięcia tras asymetrycznych
<a name="asymmetric"> </a>

Chcesz uniknąć routingu asymetrycznego, aby upewnić się, że osoby w Twojej organizacji mogą bezproblemowo Office 365 oraz innych ważnych usług w Internecie. Istnieją dwie typowe konfiguracje, które powodują routing asymetryczny u klientów. Teraz jest dobry czas na przejrzenie konfiguracji sieci, która ma być używania, i sprawdzenie, czy może występować jeden z tych scenariuszy routingu asymetrycznego.
  
Aby rozpocząć, sprawdzimy kilka różnych sytuacji skojarzonych z poniższym diagramem sieciowym. Na tym diagramie wszystkie serwery, które odbierają żądania przychodzące, takie jak usługi ADFS lub lokalne serwery hybrydowe, znajdują się w centrum danych w New Jersey i są ogłaszane w Internecie.
  
1. Sieć obwodowa jest bezpieczna, ale dla żądań przychodzących nie jest dostępny źródłowy naT.

2. Serwery w centrum danych w New Jersey mogą widzieć zarówno trasy internetowe, jak i trasy usługi ExpressRoute.

![Omówienie łączności usługi ExpressRoute.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Mamy również sugestie dotyczące sposobu ich rozwiązania.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problem 1. Połączenie z chmury do połączenia lokalnego przez Internet
  
Na poniższym diagramie przedstawiono asymetryczną ścieżkę sieciową przyjmowaną, gdy konfiguracja sieci nie zapewnia nat dla żądań przychodzących z chmury firmy Microsoft przez Internet.
  
1. Żądanie przychodzące z usługi Office 365 pobiera adres IP lokalnego punktu końcowego z publicznego serwera DNS i wysyła żądanie do Twojej sieci obwodowej.

2. W tej wadliwej konfiguracji nie skonfigurowano źródłowego serwera NAT ani nie jest on dostępny w sieci obwodowej, do której jest wysyłany ruch, co spowoduje, że jako miejsce docelowe zwracane będzie używany rzeczywisty źródłowy adres IP.

  - Serwer w Twojej sieci przekieruje ruch powrotny do usługi Office 365 za pośrednictwem dowolnego dostępnego połączenia sieciowego usługi ExpressRoute.

  - Wynikiem jest asymetryczna ścieżka dla tego przepływu do Office 365, co prowadzi do przerwanego połączenia.

![Routing asymetryczny w u usługi ExpressRoute : problem 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Rozwiązanie 1a: źródłowy nat
  
Wystarczy dodać źródłowy nat do żądania przychodzącego, aby rozwiązać ten problem z błędnie skonfigurowaną siecią. Na tym diagramie:
  
1. Żądanie przychodzące nadal wchodzi za pośrednictwem sieci obwodowej centrum danych w New Jersey. Tym razem źródłowy nat jest dostępny.

2. Odpowiedź z serwera jest przekierowywana z powrotem do adresu IP skojarzonego ze źródłowym adresem NAT, a nie do pierwotnego adresu IP, w wyniku czego odpowiedź wraca tą samą ścieżką sieciową.

![Routing asymetryczny w u usługi ExpressRoute rozwiązanie 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Rozwiązanie 1b: Określanie zakresu trasy
  
Alternatywnie możesz zdecydować, aby nie zezwalać na ogłaszanie prefiksów BGP usługi ExpressRoute, usuwając alternatywną ścieżkę sieciową dla tych komputerów. Na tym diagramie:
  
1. Żądanie przychodzące nadal wchodzi za pośrednictwem sieci obwodowej centrum danych w New Jersey. Tym razem prefiksy ogłaszane z firmy Microsoft przez obwód usługi ExpressRoute nie są dostępne dla centrum danych w New Jersey.

2. Odpowiedź z serwera jest przekierowywana z powrotem do adresu IP skojarzonego z oryginalnym adresem IP przez jedyną dostępną trasę, w wyniku czego odpowiedź wraca tą samą ścieżką sieciową.

![Routing asymetryczny w u usługi ExpressRoute rozwiązanie 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problem 2: połączenie z chmury do połączenia lokalnego za pośrednictwem usługi ExpressRoute
  
Na poniższym diagramie pokazano asymetryczną ścieżkę sieciową przyjmowaną, gdy konfiguracja sieci nie zapewnia nat dla żądań przychodzących z chmury firmy Microsoft przez usługę ExpressRoute.
  
1. Żądanie przychodzące od dostawcy Office 365 pobiera adres IP z systemu DNS i wysyła żądanie do Twojej sieci obwodowej.

2. W tej wadliwej konfiguracji nie skonfigurowano źródłowego serwera NAT ani nie jest on dostępny w sieci obwodowej, do której jest wysyłany ruch, co spowoduje, że jako miejsce docelowe zwracane będzie używany rzeczywisty źródłowy adres IP.

  - Komputer w Twojej sieci przekierowywuje ruch powrotny do usługi Office 365 za pośrednictwem dowolnego dostępnego połączenia sieciowego usługi ExpressRoute.

  - Wynikiem jest asymetryczne połączenie z Office 365.

![Routing asymetryczny w u usługi ExpressRoute : problem 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Rozwiązanie 2: źródłowy nat
  
Wystarczy dodać źródłowy nat do żądania przychodzącego, aby rozwiązać ten problem z błędnie skonfigurowaną siecią. Na tym diagramie:
  
1. Żądanie przychodzące nadal wchodzi za pośrednictwem sieci obwodowej centrum danych w Nowym Jorku. Tym razem źródłowy nat jest dostępny.

2. Odpowiedź z serwera jest przekierowywana z powrotem do adresu IP skojarzonego ze źródłowym adresem NAT, a nie do pierwotnego adresu IP, w wyniku czego odpowiedź wraca tą samą ścieżką sieciową.

![Routing asymetryczny w u usługi ExpressRoute rozwiązanie 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Sprawdzanie na papierze, czy projekt sieci ma symetrię ścieżek

W tym momencie musisz sprawdzić na papierze, czy Twój plan implementacji oferuje symetrię tras dla różnych scenariuszy, w których będziesz używać Office 365. Zidentyfikujesz określoną trasę sieciową, która powinna zostać zrobione, gdy użytkownik korzysta z różnych funkcji usługi. Od sieci lokalnej i routingu WAN do urządzeń w sieci obwodowej, do ścieżki łączności; ExpressRoute lub Internet i dalej do połączenia z punktem końcowym online.
  
Musisz to zrobić dla wszystkich usług sieciowych usługi Office 365, które zostały wcześniej zidentyfikowane jako usługi, które będą przyjęte przez Twoją organizację.
  
Warto przejść na papierze przez wszystkie trasy z drugą osobą. Wyjaśnij im, skąd każdy przeskok sieciowy powinien rozpocząć następną trasę, i upewnij się, że znasz ścieżki routingu. Pamiętaj, że usługa ExpressRoute zawsze udostępni trasę o bardziej ograniczonych zakresach do adresów IP serwera Microsoft, zapewniając niższy koszt trasy niż internetowa trasa domyślna.
  
### <a name="design-client-connectivity-configuration"></a>Projektowanie konfiguracji łączności klienta
<a name="asymmetric"> </a>

![Używanie plików PAC z usługą ExpressRoute.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Jeśli używasz serwera proxy dla ruchu powiązanego z Internetem, musisz dostosować wszystkie pliki PAC lub pliki konfiguracji klienta, aby upewnić się, że komputery klienckie w Twojej sieci są poprawnie skonfigurowane do wysyłania ruchu usługi ExpressRoute, który chcesz wysłać do usługi Office 365 bez konieczności przesyłania serwera proxy, a pozostały ruch, w tym część ruchu Office 365, jest wysyłany do odpowiedniego serwera proxy. Przeczytaj nasz przewodnik dotyczący [zarządzania Office 365 punktami końcowymi](./managing-office-365-endpoints.md), na przykład plikami PAC.
  
> [!NOTE]
> Punkty końcowe zmieniają się często, nawet co tydzień. Zmiany należy wprowadzać tylko w zależności od usług i funkcji, które zostały przyjęte przez Twoją organizację, w celu zmniejszenia liczby zmian, które trzeba wprowadzić, aby być na miejscu. Zwróć szczególną uwagę na datę wejścia w życie w kanale informacyjnym RSS, w którym są ogłaszane zmiany, a we wszystkich poprzednich zmianach jest rejestrowany rejestr, ogłaszane adresy IP mogą nie być ogłaszane lub usuwane z ogłoszenia aż do dnia wejścia w życie.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Tworzenie procedur wdrażania i testowania
<a name="testing"> </a>

Plan implementacji powinien obejmować zarówno testowanie, jak i planowanie wycofywania. Jeśli implementacja nie działa zgodnie z oczekiwaniami, plan powinien być opracowany w taki sposób, aby przed wykrytymi problemami jak najmniejsza liczba osób nie działała. Poniżej przedstawiono kilka zasad wysokiego poziomu, które powinien uwzględniać Twój plan.
  
1. Rozsuń segment sieci i dołączanie usług użytkownika, aby zminimalizować zakłócenia w pracy.

2. Zaplanuj testowanie tras za pomocą trasy śledzenia i połączenia TCP z oddzielnego hosta połączonego z Internetem.

3. Najlepiej, aby testowanie usług przychodzących i wychodzących odbywało się w odizolowanym sieci testowej z testową Office 365 dzierżawy.

      - Można również przeprowadzać testowanie w sieci produkcyjnej, jeśli klient nie używa jeszcze programu Office 365 lub jest w ramach programu pilotażowego.

      - Można również przeprowadzać testowanie podczas testowania w czasie testowania i monitorowania produkcji przeznaczonego wyłącznie do testowania i monitorowania.

      - Można również testować, sprawdzając trasy każdej usługi na każdym węźle routera warstwy 3. Tej możliwości należy używać tylko wtedy, gdy nie ma innej możliwości testowania, ponieważ brak testowania fizycznego stanowi zagrożenie.

### <a name="build-your-deployment-procedures"></a>Tworzenie procedur wdrażania

Twoje procedury wdrażania powinny być wdrażane etapami w małych grupach osób, aby umożliwić testowanie przed wdrożeniem w większych grupach osób. Poniżej przedstawiono kilka sposobów  informacje o etapach wdrażania usługi ExpressRoute.
  
1. Skonfiguruj usługę ExpressRoute z komunikacji równorzędnej firmy Microsoft i przekieruj ogłoszenia tras do pojedynczego hosta tylko na potrzeby testowania etapowego.

2. Najpierw anonsuj trasy w sieci usługi ExpressRoute do pojedynczego segmentu sieci, a następnie rozszerzaj ogłoszenia tras według segmentu lub regionu sieci.

3. Jeśli wdrażasz Office 365 po raz pierwszy, użyj wdrożenia sieciowego usługi ExpressRoute jako wdrożenia pilotażowego dla kilku osób.

4. Jeśli korzystasz z serwerów proxy, możesz też skonfigurować plik testowy PAC, aby skierować kilka osób do usługi ExpressRoute z testami i opiniami przed dodaniem kolejnych.

Twój plan implementacji powinien zawierać listę wszystkich procedur wdrażania, które należy wykonać, lub poleceń, których należy użyć do wdrożenia konfiguracji sieci. Gdy nadejdzie czas 30-godzinnego 30-godzinnego 30-godzinnego, wszystkie dokonywane zmiany powinny pochodzić z pisemnego planu wdrożenia, który został napisany wcześniej i zweryfikowany przez współpracowników. Zobacz nasze wskazówki dotyczące konfiguracji technicznej usługi ExpressRoute.
  
- Aktualizacja rekordów TXT SPF, jeśli zostały zmienione adresy IP dla jakichkolwiek serwerów lokalnych, które nadal będą wysyłać pocztę e-mail.

- Aktualizacja wszystkich wpisów DNS dla serwerów lokalnych, jeśli zostały zmienione adresy IP, aby uwzględnić nową konfigurację NAT.

- Upewnij się, że subskrybujesz kanał informacyjny RSS na Office 365 punktów końcowych, aby zachować wszelkie konfiguracje routingu lub serwera proxy.

Po zakończeniu wdrażania usługi ExpressRoute należy wykonać procedury z planu testowania. Wyniki każdej procedury powinny zostać zarejestrowane. Na wypadek, gdy wyniki planu testowania wskazują, że implementacja nie powiodła się, musisz uwzględnić procedury wycofywania do oryginalnego środowiska produkcyjnego.
  
### <a name="build-your-test-procedures"></a>Tworzenie procedur testowania

Twoje procedury testowania powinny obejmować testy dla każdej wychodzącej i przychodzącej usługi sieciowej dla tych usług Office 365 które będą używać usługi ExpressRoute, jak i te, które nie będą. Procedury powinny obejmować testowanie z każdej unikatowej lokalizacji sieciowej, łącznie z użytkownikami, którzy nie znajdują się lokalnie w firmowej sieci LAN.
  
Oto kilka przykładów działań testowych.
  
1. Wyślij polecenie ping z Twojego routera lokalnego do routera operatora sieci.

2. Sprawdź, czy Twój router Office 365 odbiera ogłoszenia adresów IP rozwiązań 500+ i CRM Online.

3. Sprawdź, czy przychodzący i wychodzący nat działa między usługą ExpressRoute a siecią wewnętrzną.

4. Sprawdź, czy Twój router anonsuje trasy do twojego nat.

5. Sprawdź, czy anonsowane prefiksy zostały zaakceptowane przez expressRoute.

      - Aby zweryfikować ogłoszenia komunikacji równorzędnej, użyj następującego polecenia cmdlet:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Sprawdź, czy zakres publicznych adresów IP NAT nie jest ogłaszany do firmy Microsoft za pośrednictwem żadnego innego obwodu sieciowego usługi ExpressRoute lub publicznego Internetu, chyba że jest określonym podzestawem większego zakresu, jak w poprzednim przykładzie.

7. Obwody usługi ExpressRoute są sparowane i sprawdź, czy są uruchomione obie sesje BGP.

8. Skonfiguruj pojedynczego hosta wewnątrz swojego serwera NAT i użyj polecenia ping, tracert i tcpping, aby przetestować łączność nowego obwodu z siecią outlook.office365.com. Możesz również użyć narzędzia, takiego jak Wireshark lub Microsoft Network Monitor 3.4, na porcie lustrzanym do MSEE, aby sprawdzić, czy można połączyć się z adresem IP skojarzonym z programem outlook.office365.com.

9. Przetestuj funkcje na poziomie Exchange Online.

  - Przetestuj Outlook może nawiązać połączenie z siecią Exchange Online i wysyłać/odbierać wiadomości e-mail.

  - Przetestuj Outlook może korzystać z trybu online.

  - Przetestuj łączność ze smartfonem oraz możliwość wysyłania/odbierania.

10. Przetestuj funkcje na poziomie aplikacji dla usługi SharePoint Online

  - Przetestuj OneDrive dla Firm klienta synchronizacji.

  - Przetestuj SharePoint dostęp do Internetu w trybie online.

11. Przetestuj funkcje na poziomie aplikacji Skype dla firm scenariuszy połączeń:

  - Dołącz do połączenia konferencyjnego jako uwierzytelniony użytkownik [zaproszenie zainicjowane przez użytkownika końcowego].

  - Zaproś użytkownika do połączenia konferencyjnego [zaproszenie wysłane z mcu].

  - Dołącz do konferencji jako użytkownik anonimowy przy użyciu Skype dla firm sieci Web.

  - Dołącz do połączenia z przewodowego połączenia komputera, telefonu IP i urządzenia przenośnego.

  - Call to federated user o Call to PSTN Validation: call is completed, call is acceptable, call is acceptable, connection time is acceptable.

  - Sprawdź, czy stan obecności kontaktów został zaktualizowany zarówno dla członków dzierżawy, jak i dla użytkowników federowanych.

### <a name="common-problems"></a>Typowe problemy

Najpopularniejszym problemem implementacji jest routing asymetryczny. Oto niektóre typowe źródła do wyszukiwania:
  
- Używanie otwartej lub płaskiej topologii routingu sieciowego bez źródłowego nat.

- Nieuzyskanie NAT do przekierowywu usług przychodzących za pośrednictwem zarówno połączeń internetowych, jak i połączeń Usługi ExpressRoute.

- Nie testowanie usług przychodzących w uciekowaniu usługi ExpressRoute w sieci testowej przed rozpoczęciem szerokiego wdrażania.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Wdrażanie łączności usługi ExpressRoute za pośrednictwem sieci
<a name="testing"> </a>

Rozmietapuj wdrażanie w jednym segmencie sieci na raz, stopniowo rozsuwając łączność z różnymi częściami sieci z planem wycofywania zmian w każdym nowym segmencie sieci. Jeśli Twoje wdrożenie jest dostosowane do wdrożenia Office 365, najpierw wdeksuj użytkowników pilotażowych Office 365 i obejmuje to miejsce.
  
Najpierw do testu, a następnie do produkcji:
  
- Uruchom kroki wdrażania, aby włączyć usługę ExpressRoute.

- Przetestuj, czy trasy sieciowe są zgodnie z oczekiwaniami.

- Prze przeprowadzenia testów dla każdej usługi przychodzącej i wychodzącej.

- Wycofywanie w przypadku odkrywania jakichkolwiek problemów.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Konfigurowanie połączenia testowego z usługą ExpressRoute za pomocą testowego segmentu sieci

Po ukończeniu planu na papierze należy sprawdzić go na małą skalę. W tym teście nawiązasz pojedyncze połączenie usługi ExpressRoute z komunikacji równorzędnej firmy Microsoft do podsieci testowej w swojej sieci lokalnej. Możesz skonfigurować dzierżawę [](https://go.microsoft.com/fwlink/p/?LinkID=403802) usługi Office 365 próbnej z łącznością z podsieci testowej i z jej strony oraz uwzględnić wszystkie usługi wychodzące i przychodzące, które będą używać w środowisku produkcyjnym, w podsieci testowej. Skonfiguruj system DNS dla testowego segmentu sieci i nawiąz połączenie ze wszystkimi usługami przychodzącymi i wychodzącymi. Wykonaj plan testowania i upewnij się, że znasz routing poszczególnych usług oraz propagację tras.
  
### <a name="execute-the-deployment-and-test-plans"></a>Wykonywanie planów wdrażania i testowania

Po wykonaniu opisanych powyżej elementów zaznacz ukończone obszary i upewnij się, że zostały one przejdą przez Ciebie i Twój zespół przed wykonaniem planu wdrażania i testowania.
  
- Lista usług wychodzących i przychodzących, które biorą udział w zmianie sieci.

- Diagram globalnej architektury sieci przedstawiający zarówno internetowy ruch wychodzący, jak i lokalizacje meet-me usługi ExpressRoute.

- Diagram routingu sieciowego przedstawiający różne ścieżki sieciowe używane dla każdej wdrożonej usługi.

- Plan wdrożenia z etapami implementacji zmian i ich wycofywania w razie potrzeby.

- Plan testowania poszczególnych Office 365 usług sieciowych.

- Ukończono papierowe sprawdzanie poprawności tras produkcyjnych dla usług przychodzących i wychodzących.

- Ukończony test w testowym segmencie sieci, w tym test dostępności.

Wybierz okno przerwy w pracy, które jest wystarczająco długie, aby przejść przez cały plan wdrażania i plan testowania, ma trochę czasu na rozwiązywanie problemów i w razie potrzeby czas na jego wycofywanie.
  
> [!CAUTION]
> Ze względu na złożony charakter routingu zarówno przez Internet, jak i przez usługę ExpressRoute zalecane jest dodanie do tego okna dodatkowego buforu czasu na potrzeby rozwiązywania problemów ze złożonym routingiem.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Konfigurowanie usługi QoS dla usługi Skype dla firm Online

Usługi QoS są niezbędne do uzyskania połączeń głosowych i spotkań w Skype dla firm Online. Usługę QoS możesz skonfigurować po upewnieniu się, że połączenie sieciowe usługi ExpressRoute nie blokuje dostępu do innych usług Office 365 Twojej sieci. Konfiguracja usługi QoS jest opisana w artykule [Usługi ExpressRoute i QoS w u Skype dla firm Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d).
  
## <a name="troubleshooting-your-implementation"></a>Rozwiązywanie problemów z implementacją
<a name="troubleshooting"> </a>

W pierwszej kolejności należy przyjrzeć się krokom w tym przewodniku implementacji, aby sprawdzić, czy w planie implementacji nie zostały pominięte? Cofniesz się i, jeśli to możliwe, uruchom dodatkowe testy w małej sieci, aby powtórzyć błąd i w tym miejscu go debugowania.
  
Określ, które usługi przychodzące lub wychodzące nie powiodły się podczas testowania. Uzyskaj konkretnie adresy IP i podsieci dla każdej usługi, która nie powiodła się. Przejdź dalej i przejdź dalej, przechodz na papierowy diagram topologii sieci i sprawdź poprawność routingu. Jeśli to możliwe, sprawdź, dokąd jest ogłaszany routing usługi ExpressRoute, przetestuj ten routing podczas śledzenia, jeśli to możliwe.
  
Uruchom program PSPing ze śledzeniem sieci do każdego punktu końcowego klienta i oceń źródłowe i docelowe adresy IP, aby sprawdzić, czy są one zgodnie z oczekiwaniami. Uruchom usługę telnet dla dowolnego hosta poczty, który jest udostępniany na porcie 25, i sprawdź, czy źródłowy nat ukrywa oryginalny adres IP źródła, jeśli jest to oczekiwane.
  
Pamiętaj, że podczas wdrażania usługi Office 365 przy użyciu połączenia usługi ExpressRoute musisz upewnić się, że konfiguracja sieci dla usługi ExpressRoute jest optymalnie zaprojektowana, a także że zostały również zoptymalizowane inne składniki w Twojej sieci, takie jak komputery klienckie. Oprócz korzystania z tego przewodnika planowania w celu rozwiązania problemów z czynnościami, które zostały pominięte, mamy również pisemny [plan rozwiązywania](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) problemów z wydajnością Office 365.
  
Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Ocena Office 365 sieci](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie łącznością sieciową za Office 365 ExpressRoute](managing-expressroute-for-connectivity.md)
  
[Routing za pomocą usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
  
[Planowanie sieci z usługą ExpressRoute dla sieci Office 365](network-planning-with-expressroute.md)
  
[Używanie społeczności BGP w u usługi ExpressRoute na Office 365 scenariuszy](bgp-communities-in-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Usługi ExpressRoute i QoS w Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ połączeń przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)
