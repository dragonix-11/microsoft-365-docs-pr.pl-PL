---
title: Implementowanie usługi ExpressRoute dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak zaimplementować usługę ExpressRoute dla Office 365, która zapewnia alternatywną ścieżkę routingu do wielu usług Office 365 dostępnych z Internetu.
ms.openlocfilehash: d577a30d97630b32fa080c9d17620b429562c5df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090368"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementowanie usługi ExpressRoute dla Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Usługa ExpressRoute dla Office 365 zapewnia alternatywną ścieżkę routingu do wielu usług Office 365 dostępnych z Internetu. Architektura usługi ExpressRoute dla Office 365 jest oparta na anonsowaniu publicznych prefiksów adresów IP usług Office 365, które są już dostępne przez Internet w aprowizowanych obwodach usługi ExpressRoute w celu późniejszej redystrybucji tych prefiksów IP do sieci. Usługa ExpressRoute umożliwia efektywne włączanie kilku różnych ścieżek routingu za pośrednictwem Internetu i usługi ExpressRoute dla wielu usług Office 365. Ten stan routingu w sieci może znacząco zmienić sposób projektowania topologii sieci wewnętrznej.
  
 **Stan:** Kompletny przewodnik w wersji 2
  
Musisz dokładnie zaplanować usługę ExpressRoute na potrzeby implementacji Office 365, aby uwzględnić złożoność sieci, ponieważ routing jest dostępny zarówno za pośrednictwem dedykowanego obwodu z trasami wprowadzonymi do sieci podstawowej, jak i Internetu. Jeśli Ty i Twój zespół nie wykonacie szczegółowego planowania i testowania w tym przewodniku, istnieje wysokie ryzyko sporadycznej lub całkowitej utraty łączności z usługami Office 365 po włączeniu obwodu usługi ExpressRoute.
  
Aby pomyślnie przeprowadzić implementację, należy przeanalizować wymagania dotyczące infrastruktury, przejść przez szczegółową ocenę i projektowanie sieci, dokładnie zaplanować wdrożenie w sposób etapowy i kontrolowany oraz utworzyć szczegółowy plan weryfikacji i testowania. W przypadku dużego, rozproszonego środowiska nie jest niczym niezwykłym, że implementacje obejmują kilka miesięcy. Ten przewodnik ma na celu ułatwienie planowania z wyprzedzeniem.
  
Planowanie dużych pomyślnych wdrożeń może potrwać sześć miesięcy i często obejmuje członków zespołu z wielu obszarów w organizacji, w tym administratorów sieci, zapory i serwera proxy, administratorów Office 365, zabezpieczeń, obsługi użytkowników końcowych, zarządzania projektami i sponsorowania kadry kierowniczej. Inwestycja w proces planowania zmniejszy prawdopodobieństwo wystąpienia błędów wdrażania powodujących przestój lub złożone i kosztowne rozwiązywanie problemów.
  
Oczekujemy, że następujące wymagania wstępne zostaną spełnione przed rozpoczęciem tego przewodnika implementacji.
  
1. Przeprowadzono ocenę sieci, aby ustalić, czy usługa ExpressRoute jest zalecana i zatwierdzona.

2. Wybrano dostawcę usług sieciowych usługi ExpressRoute. Znajdź szczegółowe informacje o [partnerach usługi ExpressRoute i lokalizacjach komunikacji równorzędnej](/azure/expressroute/expressroute-locations).

3. Znasz już [dokumentację usługi ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) i rozumiesz, że Twoja sieć wewnętrzna jest w stanie spełnić wymagania wstępne usługi ExpressRoute.

4. Twój zespół przeczytał wszystkie publiczne wskazówki i dokumentację pod adresem [https://aka.ms/expressrouteoffice365](./azure-expressroute.md), [https://aka.ms/ert](https://aka.ms/ert)i obejrzał serię [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) w kanale Channel 9, aby zrozumieć krytyczne szczegóły techniczne, w tym:

      - Zależności internetowe usług SaaS.

      - Jak unikać tras asymetrycznych i obsługiwać złożony routing.

      - Jak uwzględnić zabezpieczenia obwodowe, dostępność i mechanizmy kontroli na poziomie aplikacji.

## <a name="begin-by-gathering-requirements"></a>Rozpocznij od zebrania wymagań
<a name="requirements"> </a>

Zacznij od określenia, które funkcje i usługi mają zostać wdrożone w organizacji. Należy określić, które funkcje różnych usług Office 365 będą używane i które lokalizacje w sieci będą hostować osoby korzystające z tych funkcji. W przypadku wykazu scenariuszy należy dodać atrybuty sieci, których wymaga każdy z tych scenariuszy; takich jak przychodzące i wychodzące przepływy ruchu sieciowego oraz czy punkty końcowe Office 365 są dostępne za pośrednictwem usługi ExpressRoute, czy nie.
  
Aby zebrać wymagania organizacji:
  
- Katalog ruchu przychodzącego i wychodzącego sieciowego dla usług Office 365 używanych przez organizację. Zapoznaj się Office 365 stroną adresów URL i zakresów adresów IP, aby uzyskać opis przepływów, których wymagają różne scenariusze Office 365.

- Zbierz dokumentację istniejącej topologii sieci zawierającej szczegóły wewnętrznej sieci szkieletowej sieci WAN i topologii, łączności lokacji satelitarnych, łączności użytkownika z ostatniej mili, routingu do punktów ruchu wychodzącego obwodu sieciowego i usług proxy.

  - Zidentyfikuj punkty końcowe usługi dla ruchu przychodzącego na diagramach sieciowych, z którymi będą łączyć się Office 365 i inne usługi firmy Microsoft, pokazując zarówno internet, jak i proponowane ścieżki połączenia usługi ExpressRoute.

  - Zidentyfikuj wszystkie lokalizacje użytkowników geograficznych i łączność sieci WAN między lokalizacjami wraz z lokalizacjami, które obecnie mają ruch wychodzący do Internetu i które lokalizacje są proponowane, aby miały ruch wychodzący do lokalizacji komunikacji równorzędnej usługi ExpressRoute.

  - Zidentyfikuj wszystkie urządzenia brzegowe, takie jak serwery proxy, zapory itd., i skataloguj ich relacje z przepływami przechodzącymi przez Internet i usługę ExpressRoute.

  - Określ, czy użytkownicy końcowi będą uzyskiwać dostęp do usług Office 365 za pośrednictwem routingu bezpośredniego lub pośredniego serwera proxy aplikacji dla przepływów Internetu i usługi ExpressRoute.

- Dodaj lokalizację dzierżawy i lokalizacje meet-me do diagramu sieciowego.

- Oszacuj oczekiwaną i obserwowaną wydajność sieci oraz charakterystykę opóźnienia z głównych lokalizacji użytkowników do Office 365. Należy pamiętać, że Office 365 jest globalnym i rozproszonym zestawem usług, a użytkownicy będą łączyć się z lokalizacjami, które mogą różnić się od lokalizacji dzierżawy. Z tego powodu zaleca się mierzenie i optymalizowanie pod kątem opóźnienia między użytkownikiem a najbliższą krawędzią globalnej sieci firmy Microsoft za pośrednictwem usługi ExpressRoute i połączeń internetowych. Możesz użyć wyników z oceny sieci, aby ułatwić wykonanie tego zadania.

- Wyświetl listę wymagań dotyczących zabezpieczeń sieci firmowych i wysokiej dostępności, które należy spełnić w przypadku nowego połączenia usługi ExpressRoute. Na przykład w jaki sposób użytkownicy nadal uzyskują dostęp do Office 365 w przypadku wystąpienia awarii ruchu wychodzącego z Internetu lub obwodu usługi ExpressRoute.

- Dokument, który przepływy przychodzące i wychodzące Office 365 sieci będą używać ścieżki internetowej i która będzie używać usługi ExpressRoute. Specyfika lokalizacji geograficznych użytkowników i szczegóły topologii sieci lokalnej mogą wymagać, aby plan różnił się od jednej lokalizacji użytkownika do innej.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Katalog ruchu wychodzącego i przychodzącego sieci
<a name="trafficCatalog"> </a>

Aby zminimalizować routing i inne złożoność sieci, zalecamy używanie usługi ExpressRoute tylko dla Office 365 dla przepływów ruchu sieciowego wymaganych do przejścia przez dedykowane połączenie ze względu na wymagania prawne lub w wyniku oceny sieci. Ponadto zalecamy przygotowanie zakresu routingu usługi ExpressRoute i podejścia wychodzącego i przychodzącego ruchu sieciowego jako różnych etapów projektu implementacji. Wdrażanie usługi ExpressRoute dla Office 365 tylko dla przepływów ruchu wychodzącego zainicjowanego przez użytkownika i pozostawienie przepływów ruchu sieciowego ruchu przychodzącego przez Internet może pomóc w kontrolowaniu wzrostu złożoności topologicznej i ryzyka związanego z wprowadzeniem dodatkowych możliwości routingu asymetrycznego.
  
Katalog ruchu sieciowego powinien zawierać listę wszystkich połączeń sieciowych dla ruchu przychodzącego i wychodzącego, które będą nawiązywane między siecią lokalną a firmą Microsoft.
  
- Wychodzące przepływy ruchu sieciowego to dowolne scenariusze, w których połączenie jest inicjowane ze środowiska lokalnego, na przykład z wewnętrznych klientów lub serwerów, z miejscem docelowym usługi firmy Microsoft. Te połączenia mogą być bezpośrednie dla Office 365 lub pośrednich, na przykład wtedy, gdy połączenie przechodzi przez serwery proxy, zapory lub inne urządzenia sieciowe na ścieżce do Office 365.

- Przychodzące przepływy ruchu sieciowego to dowolne scenariusze, w których połączenie jest inicjowane z chmury firmy Microsoft do hosta lokalnego. Te połączenia zazwyczaj muszą przechodzić przez zaporę i inną infrastrukturę zabezpieczeń, której wymagają zasady zabezpieczeń klienta dla przepływów pochodzących z zewnątrz.

Przeczytaj sekcję **Zapewnianie symetrii trasy** w artykule Routing with ExpressRoute for Office 365 to determine which services will send inbound traffic and look for the column marked **ExpressRoute for Office 365** in the [Office 365 endpoints](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) reference article to determine the rest of the connectivity information (Zapewnianie symetrii trasy) artykułu [Routing with ExpressRoute for Office 365 for Office 365 endpoints reference (Routing with ExpressRoute for Office 365 endpoints reference( Routing with ExpressRoute for Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)), aby określić pozostałe informacje o łączności.
  
Dla każdej usługi, która wymaga połączenia wychodzącego, należy opisać planowaną łączność dla usługi, w tym routing sieciowy, konfigurację serwera proxy, inspekcję pakietów i wymagania dotyczące przepustowości.
  
Dla każdej usługi, która wymaga połączenia przychodzącego, potrzebne będą dodatkowe informacje. Serwery w chmurze firmy Microsoft będą nawiązywać połączenia z siecią lokalną. Aby upewnić się, że połączenia są prawidłowo nawiązywane, należy opisać wszystkie aspekty tej łączności, w tym; publiczne wpisy DNS dla usług, które zaakceptują te połączenia przychodzące, adresy IP IPv4 sformatowane przez cidr, który jest zaangażowany w sprzęt usługodawcy sieciowego oraz sposób obsługi przychodzącego translatora adresów sieciowych lub źródłowego translatora adresów sieciowych dla tych połączeń.
  
Połączenia przychodzące powinny być sprawdzane niezależnie od tego, czy nawiązują połączenie za pośrednictwem Internetu, czy usługi ExpressRoute, aby upewnić się, że routing asymetryczny nie został wprowadzony. W niektórych przypadkach lokalne punkty końcowe, do których usługi Office 365 inicjują połączenia przychodzące, mogą również wymagać dostępu do innych firm Microsoft i innych niż usługi firmy Microsoft. Najważniejsze jest, aby włączenie routingu usługi ExpressRoute do tych usług na potrzeby Office 365 nie przerywało innych scenariuszy. W wielu przypadkach klienci mogą wymagać zaimplementowania określonych zmian w sieci wewnętrznej, takich jak źródłowy translator adresów sieciowych, aby zapewnić, że przepływy przychodzące od firmy Microsoft pozostaną symetryczne po włączeniu usługi ExpressRoute.
  
Oto przykład wymaganego poziomu szczegółów. W tym przypadku Exchange hybrydowe będą kierowane do systemu lokalnego za pośrednictwem usługi ExpressRoute. 

|Właściwość połączenia   |Value  |
|----------|-----------|
|**Kierunek ruchu sieci** <br/> |Przychodzących  <br/> |
|**Usługa** <br/> |Wdrożenie hybrydowe programu Exchange  <br/> |
|**Publiczny punkt końcowy Office 365 (źródło)** <br/> |Exchange Online (adresy IP)  <br/> |
|**Publiczny lokalny punkt końcowy (miejsce docelowe)** <br/> |5.5.5.5  <br/> |
|**Publiczny wpis DNS (Internet)** <br/> |Autodiscover.contoso.com  <br/> |
|**Czy ten lokalny punkt końcowy będzie używany przez inne (nie Office 365) usługi firmy Microsoft** <br/> |Nie  <br/> |
|**Czy ten lokalny punkt końcowy będzie używany przez użytkowników/systemy w Internecie** <br/> |Tak  <br/> |
|**Systemy wewnętrzne publikowane za pośrednictwem publicznych punktów końcowych** <br/> |Exchange Server roli dostępu klienta (lokalnie) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Anons ip publicznego punktu końcowego** <br/> |**Do Internetu**: 5.5.0.0/16 **do usługi ExpressRoute**: 5.5.5.0/24  <br/> |
|**Zabezpieczenia/kontrolki obwodowe** <br/> |**Ścieżka internetowa**: DeviceID_002  **ścieżki usługi ExpressRoute**: DeviceID_003  <br/> |
|**Wysoka dostępność** <br/> |Aktywne/aktywne w 2 obwodach geograficznie nadmiarowych / ExpressRoute — Chicago i Dallas  <br/> |
|**Kontrolka symetrii ścieżki** <br/> |**Metoda**: **Źródłowa ścieżka internetowa** NAT: źródłowe połączenia przychodzące NAT do **ścieżki usługi ExpressRoute** 192.168.5.5: źródłowe połączenia NAT z 192.168.1.0 (Chicago) i 192.168.2.0 (Dallas)  <br/> |

Oto przykład usługi, która jest tylko wychodząca:

|**Właściwość połączenia**|**Wartość**|
|----------|-----------|
|**Kierunek ruchu sieci** <br/> |Wychodzące  <br/> |
|**Usługa** <br/> |SharePoint Online  <br/> |
|**Lokalny punkt końcowy (źródło)** <br/> |Stacja robocza użytkownika  <br/> |
|**Publiczny punkt końcowy Office 365 (miejsce docelowe)** <br/> |SharePoint Online (adresy IP)  <br/> |
|**Publiczny wpis DNS (Internet)** <br/> |\*.sharepoint.com (i więcej nazw FQDN)  <br/> |
|**CDN odwołania** <br/> |cdn.sharepointonline.com (i więcej nazw FQDN) — adresy IP obsługiwane przez dostawców CDN)  <br/> |
|**Anonsowanie adresów IP i translator adresów sieciowych w użyciu** <br/> |**Ścieżka internetowa/źródłowy translator adresów sieciowych**: 1.1.1.0/24  <br/> **Ścieżka usługi ExpressRoute/źródłowy translator adresów sieciowych**: 1.1.2.0/24 (Chicago) i 1.1.3.0/24 (Dallas)  <br/> |
|**Metoda łączności** <br/> |**Internet**: za pośrednictwem serwera proxy warstwy 7 (plik pac)  <br/> **ExpressRoute**: routing bezpośredni (bez serwera proxy)  <br/> |
|**Zabezpieczenia/kontrolki obwodowe** <br/> |**Ścieżka internetowa**: DeviceID_002  <br/> **Ścieżka usługi ExpressRoute**: DeviceID_003  <br/> |
|**Wysoka dostępność** <br/> |**Ścieżka internetowa**: Nadmiarowy ruch wychodzący z Internetu  <br/> **Ścieżka usługi ExpressRoute**: Routing aktywnych/aktywnych "gorących ziemniaków" na 2 geograficznie nadmiarowych obwodach usługi ExpressRoute — Chicago i Dallas  <br/> |
|**Kontrolka symetrii ścieżki** <br/> |**Metoda**: Źródłowy translator adresów sieciowych dla wszystkich połączeń  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Projekt topologii sieci z łącznością regionalną
<a name="topology"> </a>

Po zapoznaniu się z usługami i skojarzonymi z nimi przepływami ruchu sieciowego możesz utworzyć diagram sieciowy, który zawiera te nowe wymagania dotyczące łączności i ilustruje zmiany wprowadzone w celu używania usługi ExpressRoute dla Office 365. Diagram powinien zawierać następujące elementy:
  
1. Wszystkie lokalizacje użytkowników, z których będą uzyskiwane dostęp Office 365 i inne usługi.

2. Wszystkie punkty ruchu wychodzącego z Internetu i usługi ExpressRoute.

3. Wszystkie urządzenia wychodzące i przychodzące, które zarządzają łącznością w sieci i poza nią, w tym routery, zapory, serwery proxy aplikacji oraz wykrywanie/zapobieganie włamaniom.

4. Wewnętrzne miejsca docelowe dla całego ruchu przychodzącego, takie jak wewnętrzne serwery usług AD FS, które akceptują połączenia z serwerów proxy aplikacji internetowych usług AD FS.

5. Wykaz wszystkich podsieci IP, które będą anonsowane

6. Zidentyfikuj każdą lokalizację, z której użytkownicy będą uzyskiwać dostęp do Office 365, i wyświetl listę lokalizacji spotkania, które będą używane w usłudze ExpressRoute.

7. Lokalizacje i fragmenty topologii sieci wewnętrznej, w których prefiksy adresów IP firmy Microsoft poznane w usłudze ExpressRoute będą akceptowane, filtrowane i propagowane.

8. Topologia sieci powinna przedstawiać lokalizację geograficzną każdego segmentu sieci oraz sposób nawiązywania połączenia z siecią firmy Microsoft za pośrednictwem usługi ExpressRoute i/lub Internetu.

Na poniższym diagramie przedstawiono każdą lokalizację, w której użytkownicy będą używać Office 365 wraz z anonsami routingu przychodzącego i wychodzącego do Office 365.
  
![ExpressRoute regional geographic meet-me.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
W przypadku ruchu wychodzącego użytkownicy uzyskują dostęp Office 365 na jeden z trzech sposobów:
  
1. Dzięki lokalizacji meet-me w Ameryka Północna dla ludzi w Kalifornii.

2. Dzięki lokalizacji meet-me w Hong Kongu dla ludzi w Hong Kongu.

3. Za pośrednictwem Internetu w Bangladeszu, gdzie jest mniej osób i nie aprowizowano obwodu usługi ExpressRoute.

![Połączenia wychodzące dla diagramu regionalnego.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Podobnie przychodzący ruch sieciowy z Office 365 zwraca się na jeden z trzech sposobów:
  
1. Dzięki lokalizacji meet-me w Ameryka Północna dla ludzi w Kalifornii.

2. Dzięki lokalizacji meet-me w Hong Kongu dla ludzi w Hong Kongu.

3. Za pośrednictwem Internetu w Bangladeszu, gdzie jest mniej osób i nie aprowizowano obwodu usługi ExpressRoute.

![Połączenia przychodzące dla diagramu regionalnego.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Określanie odpowiedniej lokalizacji spotkania

Wybór lokalizacji meet-me, czyli lokalizacji fizycznej, w której obwód usługi ExpressRoute łączy sieć z siecią firmy Microsoft, zależy od lokalizacji, z których użytkownicy będą uzyskiwać dostęp do Office 365. Jako oferta SaaS Office 365 nie działa w ramach modelu regionalnego IaaS lub PaaS w taki sam sposób jak platforma Azure. Zamiast tego Office 365 to rozproszony zestaw usług współpracy, w którym użytkownicy mogą potrzebować połączenia z punktami końcowymi w wielu centrach danych i regionach, które niekoniecznie muszą znajdować się w tej samej lokalizacji lub regionie, w którym hostowana jest dzierżawa użytkownika.
  
Oznacza to, że najważniejszą kwestią, którą należy wziąć pod uwagę podczas wybierania lokalizacji meet-me dla usługi ExpressRoute dla Office 365, jest miejsce, z którego będą nawiązywać połączenia osoby w organizacji. Ogólną rekomendacją optymalnej łączności Office 365 jest implementowanie routingu, dzięki czemu żądania użytkowników dotyczące usług Office 365 są przekazywane do sieci firmy Microsoft za pośrednictwem najkrótszej ścieżki sieciowej, jest to również często nazywane routingiem "gorących ziemniaków". Jeśli na przykład większość użytkowników Office 365 znajduje się w jednej lub dwóch lokalizacjach, wybranie lokalizacji meet-me znajdujących się w najbliższej odległości od lokalizacji tych użytkowników spowoduje utworzenie optymalnego projektu. Jeśli Twoja firma ma duże populacje użytkowników w wielu różnych regionach, warto rozważyć posiadanie wielu obwodów usługi ExpressRoute i lokalizacji meet-me. W przypadku niektórych lokalizacji użytkowników najkrótsza/najbardziej optymalna ścieżka do sieci firmy Microsoft i Office 365 może nie dotyczyć wewnętrznych punktów połączenia sieci WAN i usługi ExpressRoute, ale za pośrednictwem Internetu.
  
Często istnieje wiele lokalizacji meet-me, które można wybrać w regionie ze względną bliskością użytkowników. Wypełnij poniższą tabelę, aby kierować swoimi decyzjami.

**Planowane lokalizacje usługi ExpressRoute w Kalifornii i Nowym Jorku**

|Lokalizacja  <br/> |Liczba osób  <br/> |Oczekiwane opóźnienie dla sieci firmy Microsoft za pośrednictwem ruchu wychodzącego z Internetu  <br/> |Oczekiwane opóźnienie w sieci firmy Microsoft za pośrednictwem usługi ExpressRoute  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10,000  <br/> |~15ms  <br/> |~10ms (przez Dolinę Krzemową)  <br/> |
|Waszyngtonie  <br/> |15,000  <br/> |~20ms  <br/> |~10ms (przez Nowy Jork)  <br/> |
|Dallas  <br/> |5,000  <br/> |~15ms  <br/> |~40ms (przez Nowy Jork)  <br/> |

Po utworzeniu architektury sieci globalnej przedstawiającej region Office 365, lokalizacje typu meet-me dostawcy usług sieciowych usługi ExpressRoute oraz liczbę osób według lokalizacji można użyć do określenia, czy można dokonać optymalizacji. Może również pokazać globalne połączenia sieciowe spinki do włosów, gdzie ruch kieruje się do odległej lokalizacji w celu uzyskania lokalizacji meet-me. Jeśli odnaleziono spinkę do włosów w sieci globalnej, należy ją skorygować przed kontynuowaniem. Znajdź inną lokalizację meet-me lub użyj selektywnych punktów wyjścia internet breakout, aby uniknąć spinki do włosów.
  
Pierwszy diagram przedstawia przykład klienta z dwoma lokalizacjami fizycznymi w Ameryka Północna. Możesz wyświetlić informacje o lokalizacjach biura, Office 365 lokalizacjach dzierżawy i kilku opcjach dla lokalizacji usługi ExpressRoute meet-me. W tym przykładzie klient wybrał lokalizację meet-me na podstawie dwóch zasad w kolejności:
  
1. Najbliższa bliskość osób w organizacji.

2. Najbliżej centrum danych firmy Microsoft, w którym jest hostowana Office 365.

![ExpressRoute US geographic meet-me.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Rozszerzając tę koncepcję nieco dalej, drugi diagram przedstawia przykładowego klienta z wieloma państwami, który ma do czynienia z podobnymi informacjami i podejmowaniem decyzji. Ten klient ma małe biuro w Bangladeszu z zaledwie małym zespołem dziesięciu osób koncentruje się na zwiększaniu ich śladu w regionie. Jest lokalizacja meet-me w Chennai i centrum danych firmy Microsoft z Office 365 hostowanym w Chennai, więc lokalizacja meet-me miałaby sens; jednak dla dziesięciu osób koszt dodatkowego obwodu jest uciążliwy. Patrząc na sieć, musisz określić, czy opóźnienie związane z wysyłaniem ruchu sieciowego przez sieć jest bardziej efektywne niż wydawanie kapitału w celu uzyskania innego obwodu usługi ExpressRoute.
  
Alternatywnie, dziesięć osób w Bangladeszu może doświadczyć lepszej wydajności z ruchu sieciowego wysyłane przez Internet do sieci Firmy Microsoft niż oni routingu w sieci wewnętrznej, jak pokazaliśmy na diagramach wprowadzających i odtworzone poniżej.
  
![Połączenia wychodzące dla diagramu regionalnego.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Tworzenie usługi ExpressRoute na potrzeby planu implementacji Office 365
<a name="implementation"> </a>

Plan implementacji powinien obejmować zarówno szczegóły techniczne konfigurowania usługi ExpressRoute, jak i szczegóły konfigurowania całej innej infrastruktury w sieci, takie jak poniżej.
  
- Planowanie usług podzielonych między usługę ExpressRoute i Internet.

- Zaplanuj przepustowość, zabezpieczenia, wysoką dostępność i tryb failover.

- Projektowanie routingu przychodzącego i wychodzącego, w tym odpowiednich optymalizacji ścieżki routingu dla różnych lokalizacji

- Zdecyduj, jak daleko trasy usługi ExpressRoute będą anonsowane do sieci i jaki jest mechanizm wybierania przez klientów ścieżki do Internetu lub usługi ExpressRoute; na przykład routing bezpośredni lub serwer proxy aplikacji.

- Planowanie zmian rekordów DNS, w tym wpisów struktury [zasad nadawcy](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) .

- Planowanie strategii translatora adresów sieciowych, w tym wychodzącego i przychodzącego źródłowego translatora adresów sieciowych.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planowanie routingu przy użyciu ścieżek sieciowych Internetu i usługi ExpressRoute
<a name="paths"> </a>

- W przypadku początkowego wdrożenia zaleca się korzystanie z Internetu we wszystkich usługach przychodzących, takich jak przychodzące wiadomości e-mail lub łączność hybrydowa.

- Planowanie routingu sieci LAN klienta użytkownika końcowego, [takiego jak konfigurowanie pliku PAC/WPAD](./managing-office-365-endpoints.md), trasy domyślnej, serwerów proxy i anonsów tras protokołu BGP.

- Planowanie routingu obwodu, w tym serwerów proxy, zapór i serwerów proxy w chmurze.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planowanie przepustowości, zabezpieczeń, wysokiej dostępności i trybu failover
<a name="availability"> </a>

Utwórz plan przepustowości wymagany dla każdego dużego obciążenia Office 365. Oddzielnie oszacuj wymagania dotyczące przepustowości Exchange Online, SharePoint Online i Skype dla firm Online. Możesz użyć kalkulatorów szacowania dostępnych dla Exchange Online i Skype dla firm jako miejsca początkowego. Jednak test pilotażowy z reprezentatywną próbą profilów i lokalizacji użytkowników jest wymagany, aby w pełni zrozumieć potrzeby dotyczące przepustowości organizacji.
  
Dodaj sposób obsługi zabezpieczeń w poszczególnych lokalizacjach internetu i ruchu wychodzącego usługi ExpressRoute do planu, pamiętaj, że wszystkie połączenia usługi ExpressRoute z Office 365 korzystają z publicznej komunikacji równorzędnej i nadal muszą być zabezpieczone zgodnie z zasadami zabezpieczeń firmy dotyczącymi łączenia się z sieciami zewnętrznymi.
  
Dodaj szczegóły do swojego planu, na które osoby będą miały wpływ awarie i jak te osoby będą mogły wykonywać swoją pracę na pełnych obrotach w najprostszy sposób.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planowanie wymagań dotyczących przepustowości, w tym wymagań Skype dla firm dotyczących jitteru, opóźnienia, przeciążenia i przestrzeni headroom
  
Skype dla firm Online ma również określone dodatkowe wymagania dotyczące sieci, które zostały szczegółowo opisane w artykule [Jakość multimediów i wydajność łączności sieciowej w usłudze Skype dla firm Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Przeczytaj sekcję **Planowanie przepustowości dla usługi Azure ExpressRoute** w [temacie Planowanie sieci za pomocą usługi ExpressRoute dla Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Podczas przeprowadzania oceny przepustowości z użytkownikami pilotażowymi możesz skorzystać z naszego przewodnika; [Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planowanie wymagań dotyczących wysokiej dostępności
  
Utwórz plan wysokiej dostępności w celu spełnienia twoich potrzeb i uwzględnij go w zaktualizowanym diagramie topologii sieci. Przeczytaj sekcję **Wysoka dostępność i tryb failover w usłudze Azure ExpressRoute** w [temacie Planowanie sieci za pomocą usługi ExpressRoute dla Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planowanie wymagań dotyczących zabezpieczeń sieci
  
Utwórz plan spełniający wymagania dotyczące zabezpieczeń sieci i uwzględnij go w zaktualizowanym diagramie topologii sieci. Przeczytaj sekcję **Stosowanie mechanizmów kontroli zabezpieczeń do usługi Azure ExpressRoute dla scenariuszy Office 365** w [temacie Planowanie sieci za pomocą usługi ExpressRoute dla Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Projektowanie łączności usługi wychodzącej
<a name="outbound"> </a>

Usługa ExpressRoute dla Office 365 ma wymagania dotyczące sieci *wychodzącej*, które mogą być nieznane. W szczególności adresy IP reprezentujące użytkowników i sieci do Office 365 i pełniące rolę źródłowych punktów końcowych dla wychodzących połączeń sieciowych z firmą Microsoft muszą spełniać określone wymagania opisane poniżej.
  
1. Punkty końcowe muszą być publicznymi adresami IP, które są zarejestrowane w firmie lub u operatora zapewniającego łączność usługi ExpressRoute z Tobą.

2. Punkty końcowe muszą być anonsowane do firmy Microsoft i weryfikowane/akceptowane przez usługę ExpressRoute.

3. Punkty końcowe nie mogą być anonsowane w Internecie przy użyciu tej samej lub bardziej preferowanej metryki routingu.

4. Punktów końcowych nie można używać do łączności z usługi firmy Microsoft, które nie są skonfigurowane za pośrednictwem usługi ExpressRoute.

Jeśli projekt sieci nie spełnia tych wymagań, istnieje duże ryzyko, że użytkownicy będą doświadczać błędów łączności Office 365 i innych usługi firmy Microsoft z powodu trasy czarnego holowania lub routingu asymetrycznego. Dzieje się tak, gdy żądania do usługi firmy Microsoft są kierowane przez usługę ExpressRoute, ale odpowiedzi są kierowane z powrotem przez Internet lub odwrotnie, a odpowiedzi są porzucane przez stanowe urządzenia sieciowe, takie jak zapory.
  
Najczęściej używaną metodą do spełnienia powyższych wymagań jest użycie źródłowego translatora adresów sieciowych zaimplementowanego jako część sieci lub dostarczonego przez operatora usługi ExpressRoute. Źródłowy translator adresów sieciowych umożliwia abstrakcję szczegółów i prywatnych adresów IP sieci internetowej z usługi ExpressRoute i; w połączeniu z odpowiednimi anonsami tras ip, zapewniają łatwy mechanizm zapewniający symetrię ścieżki. Jeśli używasz stanowych urządzeń sieciowych specyficznych dla lokalizacji komunikacji równorzędnej usługi ExpressRoute, musisz zaimplementować oddzielne pule NAT dla każdej komunikacji równorzędnej usługi ExpressRoute, aby zapewnić symetrię ścieżki.
  
Dowiedz się więcej o [wymaganiach dotyczących translatora adresów sieciowych usługi ExpressRoute](/azure/expressroute/expressroute-nat).
  
Dodaj zmiany dotyczące łączności wychodzącej do diagramu topologii sieci.
  
### <a name="design-inbound-service-connectivity"></a>Projektowanie łączności usługi przychodzącej
<a name="inbound"> </a>

Większość wdrożeń Office 365 przedsiębiorstwa przyjmuje pewną formę łączności przychodzącej z Office 365 do usług lokalnych, takich jak Exchange, SharePoint i Skype dla firm scenariuszy hybrydowych, migracji skrzynek pocztowych i uwierzytelniania przy użyciu infrastruktury usług ADFS. Gdy usługa ExpressRoute włączy dodatkową ścieżkę routingu między siecią lokalną a firmą Microsoft na potrzeby łączności wychodzącej, na te połączenia przychodzące może przypadkowo mieć wpływ routing asymetryczny, nawet jeśli zamierzasz, aby te przepływy nadal korzystały z Internetu. Kilka opisanych poniżej środków ostrożności zaleca się, aby upewnić się, że nie ma to wpływu na przepływy przychodzące oparte na Internecie z Office 365 do systemów lokalnych.
  
Aby zminimalizować ryzyko związane z routingiem asymetrycznym dla przepływów ruchu sieciowego ruchu przychodzącego, wszystkie połączenia przychodzące powinny używać źródłowego translatora adresów sieciowych, zanim zostaną przekierowane do segmentów sieci, które mają wgląd w routing w usłudze ExpressRoute. Jeśli połączenia przychodzące są dozwolone w segmencie sieci z widocznością routingu do usługi ExpressRoute bez źródłowego translatora adresów sieciowych, żądania pochodzące z Office 365 będą wprowadzane z Internetu, ale odpowiedź wracająca do Office 365 będzie preferować ścieżkę sieciową usługi ExpressRoute z powrotem do sieci firmy Microsoft, powodując routing asymetryczny.
  
Aby spełnić to wymaganie, możesz rozważyć jeden z następujących wzorców implementacji:
  
1. Przed skierowaniem żądań do sieci wewnętrznej przy użyciu sprzętu sieciowego, takiego jak zapory lub moduły równoważenia obciążenia na ścieżce z Internetu do systemów lokalnych, wykonaj źródłowy translator adresów sieciowych.

2. Upewnij się, że trasy usługi ExpressRoute nie są propagowane do segmentów sieci, w których znajdują się usługi przychodzące, takie jak serwery frontonu lub odwrotne systemy proxy, obsługujące połączenia internetowe.

Jawne uwzględnianie tych scenariuszy w sieci i utrzymywanie wszystkich przepływów ruchu przychodzącego przez Internet pomaga zminimalizować wdrożenie i ryzyko operacyjne routingu asymetrycznego.
  
Mogą wystąpić sytuacje, w których można skierować niektóre przepływy przychodzące za pośrednictwem połączeń usługi ExpressRoute. W przypadku tych scenariuszy należy wziąć pod uwagę następujące dodatkowe zagadnienia.
  
1. Office 365 mogą dotyczyć tylko lokalnych punktów końcowych korzystających z publicznych adresów IP. Oznacza to, że nawet jeśli lokalny punkt końcowy ruchu przychodzącego jest widoczny tylko dla Office 365 za pośrednictwem usługi ExpressRoute, nadal musi mieć skojarzony publiczny adres IP.

2. Wszystkie rozpoznawanie nazw DNS wykonywane przez usługi Office 365 w celu rozpoznawania lokalnych punktów końcowych odbywa się przy użyciu publicznego systemu DNS. Oznacza to, że musisz zarejestrować nazwę FQDN punktów końcowych usługi dla ruchu przychodzącego w mapowaniach adresów IP w Internecie.

3. Aby odbierać przychodzące połączenia sieciowe za pośrednictwem usługi ExpressRoute, publiczne podsieci IP dla tych punktów końcowych muszą być anonsowane do firmy Microsoft za pośrednictwem usługi ExpressRoute.

4. Dokładnie oceń te przychodzące przepływy ruchu sieciowego, aby upewnić się, że odpowiednie zabezpieczenia i mechanizmy kontroli sieci są stosowane zgodnie z zasadami zabezpieczeń i sieci firmy.

5. Po anonsowaniu lokalnych punktów końcowych przychodzących do firmy Microsoft za pośrednictwem usługi ExpressRoute usługa ExpressRoute stanie się preferowaną ścieżką routingu do tych punktów końcowych dla wszystkich usługi firmy Microsoft, w tym Office 365. Oznacza to, że te podsieci punktów końcowych muszą być używane tylko do komunikacji z usługami Office 365 i żadnymi innymi usługami w sieci firmy Microsoft. W przeciwnym razie twój projekt spowoduje routing asymetryczny, w którym połączenia przychodzące z innych usługi firmy Microsoft wolą kierować ruch przychodzący za pośrednictwem usługi ExpressRoute, podczas gdy ścieżka powrotna będzie korzystać z Internetu.

6. W przypadku wyłączenia obwodu usługi ExpressRoute lub lokalizacji meet-me należy upewnić się, że lokalne punkty końcowe ruchu przychodzącego są nadal dostępne do akceptowania żądań za pośrednictwem oddzielnej ścieżki sieciowej. Może to oznaczać anonsowanie podsieci dla tych punktów końcowych za pośrednictwem wielu obwodów usługi ExpressRoute.

7. Zalecamy zastosowanie źródłowego translatora adresów sieciowych dla wszystkich przepływów ruchu sieciowego ruchu przychodzącego do sieci za pośrednictwem usługi ExpressRoute, zwłaszcza gdy te przepływy są między stanowymi urządzeniami sieciowymi, takimi jak zapory.

8. Niektóre usługi lokalne, takie jak serwer proxy usług ADFS lub automatyczne wykrywanie Exchange, mogą odbierać żądania przychodzące zarówno od usług Office 365, jak i użytkowników z Internetu. W przypadku tych żądań Office 365 będzie dotyczyć tej samej nazwy FQDN co żądania użytkowników przez Internet. Zezwolenie na przychodzące połączenia użytkowników z Internetu do tych lokalnych punktów końcowych przy jednoczesnym wymuszaniu Office 365 połączeń do korzystania z usługi ExpressRoute oznacza znaczną złożoność routingu. W przypadku zdecydowanej większości klientów implementujących tak złożone scenariusze w usłudze ExpressRoute nie jest zalecane ze względu na kwestie operacyjne. To dodatkowe obciążenie obejmuje zarządzanie ryzykiem routingu asymetrycznego i wymaga starannego zarządzania anonsami i zasadami routingu w wielu wymiarach.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Zaktualizuj plan topologii sieci, aby pokazać, jak można uniknąć tras asymetrycznych
<a name="asymmetric"> </a>

Chcesz uniknąć routingu asymetrycznego, aby zapewnić osobom w organizacji bezproblemowe korzystanie z Office 365, a także innych ważnych usług w Internecie. Istnieją dwie typowe konfiguracje, które klienci mają, które powodują routing asymetryczny. Teraz warto zapoznać się z konfiguracją sieci, której planujesz użyć, i sprawdzić, czy może istnieć jeden z tych scenariuszy routingu asymetrycznego.
  
Na początek przeanalizujemy kilka różnych sytuacji związanych z poniższym diagramem sieciowym. Na tym diagramie wszystkie serwery, które odbierają żądania przychodzące, takie jak usługi ADFS lub lokalne serwery hybrydowe, znajdują się w centrum danych New Jersey i są anonsowane w Internecie.
  
1. Sieć obwodowa jest bezpieczna, ale nie ma dostępnego źródłowego translatora adresów sieciowych dla żądań przychodzących.

2. Serwery w centrum danych New Jersey mogą wyświetlać zarówno trasy internetowe, jak i expressroute.

![Omówienie łączności usługi ExpressRoute.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Mamy również sugestie dotyczące sposobu ich naprawy.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problem 1. Połączenie z chmurą do połączenia lokalnego przez Internet
  
Na poniższym diagramie przedstawiono asymetryczną ścieżkę sieciową podjętą, gdy konfiguracja sieci nie zapewnia translatora adresów sieciowych dla żądań przychodzących z chmury firmy Microsoft przez Internet.
  
1. Żądanie przychodzące z Office 365 pobiera adres IP lokalnego punktu końcowego z publicznego systemu DNS i wysyła żądanie do sieci obwodowej.

2. W tej wadliwej konfiguracji w sieci obwodowej, w której jest wysyłany ruch, nie skonfigurowano ani nie skonfigurowano źródłowego translatora adresów sieciowych, co powoduje użycie rzeczywistego źródłowego adresu IP jako zwracanego miejsca docelowego.

  - Serwer w sieci kieruje ruch powrotny do Office 365 za pośrednictwem dowolnego dostępnego połączenia sieciowego usługi ExpressRoute.

  - Wynikiem jest ścieżka asymetryczna dla tego przepływu do Office 365, co powoduje przerwanie połączenia.

![Problem z routingiem asymetrycznym usługi ExpressRoute 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Rozwiązanie 1a: źródłowy translator adresów adresów domeny
  
Po prostu dodanie źródłowego translatora adresów sieciowych do żądania przychodzącego rozwiązuje problem z nieprawidłowo skonfigurowaną siecią. Na tym diagramie:
  
1. Żądanie przychodzące nadal jest wprowadzane za pośrednictwem sieci obwodowej centrum danych New Jersey. Tym razem dostępna jest źródłowa translator adresów sieciowych.

2. Odpowiedź z serwera kieruje się z powrotem do adresu IP skojarzonego ze źródłowym translatorem adresów sieciowych zamiast oryginalnego adresu IP, co powoduje zwrócenie odpowiedzi w tej samej ścieżce sieciowej.

![Rozwiązanie routingu asymetrycznego usługi ExpressRoute 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Rozwiązanie 1b: określanie zakresu tras
  
Alternatywnie możesz nie zezwalać na anonsowanie prefiksów protokołu BGP usługi ExpressRoute, usuwając alternatywną ścieżkę sieci dla tych komputerów. Na tym diagramie:
  
1. Żądanie przychodzące nadal jest wprowadzane za pośrednictwem sieci obwodowej centrum danych New Jersey. Tym razem prefiksy anonsowane przez firmę Microsoft za pośrednictwem obwodu usługi ExpressRoute nie są dostępne w centrum danych New Jersey.

2. Odpowiedź z serwera kieruje się z powrotem do adresu IP skojarzonego z oryginalnym adresem IP za pośrednictwem jedynej dostępnej trasy, co powoduje zwrócenie odpowiedzi w tej samej ścieżce sieciowej.

![Rozwiązanie routingu asymetrycznego usługi ExpressRoute 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problem 2. Połączenie z chmurą do środowiska lokalnego za pośrednictwem usługi ExpressRoute
  
Na poniższym diagramie przedstawiono asymetryczną ścieżkę sieciową podjętą, gdy konfiguracja sieci nie zapewnia translatora adresów sieciowych dla żądań przychodzących z chmury firmy Microsoft za pośrednictwem usługi ExpressRoute.
  
1. Żądanie przychodzące z Office 365 pobiera adres IP z usługi DNS i wysyła żądanie do sieci obwodowej.

2. W tej wadliwej konfiguracji w sieci obwodowej, w której jest wysyłany ruch, nie skonfigurowano ani nie skonfigurowano źródłowego translatora adresów sieciowych, co powoduje użycie rzeczywistego źródłowego adresu IP jako zwracanego miejsca docelowego.

  - Komputer w sieci kieruje ruch powrotny do Office 365 za pośrednictwem dowolnego dostępnego połączenia sieciowego usługi ExpressRoute.

  - Rezultatem jest połączenie asymetryczne z Office 365.

![Problem z routingiem asymetrycznym usługi ExpressRoute 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Rozwiązanie 2: źródłowy translator adresów adresów adresów
  
Po prostu dodanie źródłowego translatora adresów sieciowych do żądania przychodzącego rozwiązuje problem z nieprawidłowo skonfigurowaną siecią. Na tym diagramie:
  
1. Przychodzące żądanie będzie nadal wprowadzane za pośrednictwem sieci obwodowej centrum danych w Nowym Jorku. Tym razem dostępna jest źródłowa translator adresów sieciowych.

2. Odpowiedź z serwera kieruje się z powrotem do adresu IP skojarzonego ze źródłowym translatorem adresów sieciowych zamiast oryginalnego adresu IP, co powoduje zwrócenie odpowiedzi w tej samej ścieżce sieciowej.

![Rozwiązanie routingu asymetrycznego usługi ExpressRoute 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papierowe sprawdzanie, czy projekt sieci ma symetrię ścieżki

Na tym etapie należy sprawdzić na papierze, czy plan implementacji oferuje symetrię tras dla różnych scenariuszy, w których będziesz używać Office 365. Zidentyfikujesz określoną trasę sieciową, która ma zostać podjęta, gdy dana osoba korzysta z różnych funkcji usługi. Od sieci lokalnej i routingu sieci WAN do urządzeń obwodowych do ścieżki łączności; Usługa ExpressRoute lub Internet oraz połączenie z punktem końcowym online.
  
Należy to zrobić dla wszystkich Office 365 usług sieciowych, które zostały wcześniej zidentyfikowane jako usługi, które organizacja wdroży.
  
Pomaga to zrobić ten papierowy przewodnik po trasach z drugą osobą. Wyjaśnij im, skąd oczekuje się, że każdy przeskok sieciowy uzyska następną trasę, i upewnij się, że znasz ścieżki routingu. Pamiętaj, że usługa ExpressRoute zawsze zapewnia trasę o większym zakresie do adresów IP serwera firmy Microsoft, co zapewnia niższy koszt trasy niż domyślna trasa internetowa.
  
### <a name="design-client-connectivity-configuration"></a>Projektowanie konfiguracji łączności klienta
<a name="asymmetric"> </a>

![Używanie plików PAC z usługą ExpressRoute.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Jeśli używasz serwera proxy dla ruchu związanego z Internetem, musisz dostosować wszystkie pliki konfiguracji pac lub klienta, aby upewnić się, że komputery klienckie w sieci są prawidłowo skonfigurowane do wysyłania ruchu usługi ExpressRoute, który chcesz Office 365 bez przesyłania serwera proxy, a pozostały ruch, w tym część ruchu Office 365, jest wysyłany do odpowiedniego serwera proxy. Przeczytaj nasz przewodnik [dotyczący zarządzania punktami końcowymi Office 365](./managing-office-365-endpoints.md), na przykład plikami PAC.
  
> [!NOTE]
> Punkty końcowe zmieniają się często, tak często jak co tydzień. Zmiany należy wprowadzać tylko w oparciu o usługi i funkcje, które organizacja przyjęła, aby zmniejszyć liczbę zmian, które należy wprowadzić, aby zachować aktualność. Zwróć szczególną uwagę na **datę wejścia w życie** w kanale informacyjnym RSS, w którym zmiany są ogłaszane, a do momentu osiągnięcia daty wejścia w życie nie można anonsować ani usuwać z reklamy wszystkie wcześniejsze zmiany, adresy IP, które są ogłaszane.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Tworzenie procedur wdrażania i testowania
<a name="testing"> </a>

Plan implementacji powinien obejmować zarówno testowanie, jak i planowanie wycofywania. Jeśli implementacja nie działa zgodnie z oczekiwaniami, plan powinien mieć wpływ na najmniejszą liczbę osób przed wykryciem problemów. Poniżej przedstawiono niektóre zasady wysokiego poziomu, które należy wziąć pod uwagę w planie.
  
1. Przygotowanie segmentu sieci i dołączania usługi użytkownika w celu zminimalizowania zakłóceń.

2. Zaplanuj testowanie tras za pomocą funkcji traceroute i połączenia TCP z oddzielnego hosta połączonego z Internetem.

3. Najlepiej, aby testowanie usług przychodzących i wychodzących odbywało się w izolowanej sieci testowej przy użyciu dzierżawy Office 365 testowej.

      - Alternatywnie testowanie można przeprowadzić w sieci produkcyjnej, jeśli klient nie korzysta jeszcze z Office 365 lub jest w trybie pilotażowym.

      - Alternatywnie testowanie można przeprowadzić podczas awarii produkcyjnej, która jest odkładana tylko do testowania i monitorowania.

      - Możesz też przeprowadzić testowanie, sprawdzając trasy dla każdej usługi w każdym węźle routera warstwy 3. Ta rezerwa powinna być używana tylko wtedy, gdy żadne inne testy nie są możliwe, ponieważ brak testów fizycznych wprowadza ryzyko.

### <a name="build-your-deployment-procedures"></a>Tworzenie procedur wdrażania

Procedury wdrażania powinny być wdrażane w małych grupach osób etapami, aby umożliwić testowanie przed wdrożeniem w większych grupach osób. Poniżej przedstawiono kilka sposobów wdrażania usługi ExpressRoute.
  
1. Skonfiguruj usługę ExpressRoute za pomocą komunikacji równorzędnej firmy Microsoft i przekaż anonsy tras do jednego hosta tylko na potrzeby testowania etapowego.

2. Najpierw anonsuj trasy do sieci ExpressRoute do pojedynczego segmentu sieci i rozwiń anonsy tras według segmentu sieci lub regionu.

3. Jeśli wdrożenie Office 365 po raz pierwszy, użyj wdrożenia sieci usługi ExpressRoute jako pilotażu dla kilku osób.

4. Jeśli używasz serwerów proxy, możesz też skonfigurować testowy plik PAC, aby skierować kilka osób do usługi ExpressRoute z testowaniem i opinią przed dodaniem kolejnych.

Plan implementacji powinien zawierać listę wszystkich procedur wdrażania, które należy wykonać, lub poleceń, które należy użyć do wdrożenia konfiguracji sieci. Gdy nadejdzie czas awarii sieci, wszystkie wprowadzone zmiany powinny pochodzić z pisemnego planu wdrożenia, który został napisany z wyprzedzeniem, a element równorzędny powinien zostać przejrzany. Zapoznaj się z naszymi wskazówkami dotyczącymi konfiguracji technicznej usługi ExpressRoute.
  
- Aktualizowanie rekordów SPF TXT w przypadku zmiany adresów IP dla wszystkich serwerów lokalnych, które będą nadal wysyłać wiadomości e-mail.

- Aktualizowanie wszystkich wpisów DNS dla serwerów lokalnych, jeśli zmieniono adresy IP w celu uwzględnienia nowej konfiguracji translatora adresów sieciowych.

- Upewnij się, że subskrybowaliśmy kanał informacyjny RSS w celu Office 365 powiadomień punktu końcowego w celu obsługi wszelkich konfiguracji routingu lub serwera proxy.

Po zakończeniu wdrażania usługi ExpressRoute należy wykonać procedury w planie testu. Wyniki dla każdej procedury powinny być rejestrowane. Należy uwzględnić procedury wycofywania do oryginalnego środowiska produkcyjnego w przypadku, gdy wyniki planu testu wskazują, że implementacja nie powiodła się.
  
### <a name="build-your-test-procedures"></a>Tworzenie procedur testowych

Procedury testowania powinny obejmować testy dla każdej wychodzącej i przychodzącej usługi sieciowej dla Office 365 zarówno korzystających z usługi ExpressRoute, jak i tych, które nie będą. Procedury te powinny obejmować testowanie z każdej unikatowej lokalizacji sieciowej, w tym użytkowników, którzy nie są lokalni w firmowej sieci LAN.
  
Poniżej przedstawiono przykłady działań testowych.
  
1. Polecenie ping z routera lokalnego do routera operatora sieciowego.

2. Sprawdź, czy reklamy adresów IP 500+ Office 365 i CRM Online są odbierane przez router lokalny.

3. Sprawdź, czy przychodzący i wychodzący translator adresów sieciowych działa między usługą ExpressRoute a siecią wewnętrzną.

4. Sprawdź, czy trasy do translatora adresów sieciowych są anonsowane z routera.

5. Sprawdź, czy usługa ExpressRoute zaakceptowała twoje anonsowane prefiksy.

      - Użyj następującego polecenia cmdlet, aby zweryfikować anonsy komunikacji równorzędnej:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Sprawdź, czy publiczny zakres adresów IP translatora adresów sieciowych nie jest anonsowany do firmy Microsoft za pośrednictwem żadnego innego obwodu usługi ExpressRoute lub publicznej sieci internetowej, chyba że jest to określony podzbiór większego zakresu, jak w poprzednim przykładzie.

7. Obwody usługi ExpressRoute są sparowane. Sprawdź, czy obie sesje protokołu BGP są uruchomione.

8. Skonfiguruj pojedynczego hosta wewnątrz translatora adresów sieciowych i użyj poleceń ping, tracert i tcpping, aby przetestować łączność między nowym obwodem a outlook.office365.com hosta. Alternatywnie można użyć narzędzia, takiego jak Wireshark lub Microsoft Network Monitor 3.4 na dublowanym porcie do programu MSEE, aby sprawdzić, czy możesz nawiązać połączenie z adresem IP skojarzonym z outlook.office365.com.

9. Testowanie funkcji na poziomie aplikacji dla Exchange Online.

  - Test Outlook jest w stanie nawiązać połączenie z Exchange Online i wysłać/odebrać wiadomość e-mail.

  - Test Outlook jest w stanie korzystać z trybu online.

  - Przetestuj łączność ze smartfonem i możliwość wysyłania/odbierania.

10. Testowanie funkcjonalności na poziomie aplikacji dla usługi SharePoint Online

  - Testowanie klienta synchronizacji OneDrive dla Firm.

  - Testowanie dostępu do internetu SharePoint Online.

11. Testowanie funkcji na poziomie aplikacji dla scenariuszy wywoływania Skype dla firm:

  - Dołącz do połączenia konferencyjnego jako uwierzytelniony użytkownik [zaproszenie zainicjowane przez użytkownika końcowego].

  - Zaproś użytkownika do połączenia konferencyjnego [zaproszenie wysłane z mcu].

  - Dołącz do konferencji jako użytkownik anonimowy przy użyciu aplikacji internetowej Skype dla firm.

  - Połącz połączenie z połączenia z komputerem przewodowym, telefonem IP i urządzeniem przenośnym.

  - Wywołanie użytkownika federacyjnego o Wywołanie weryfikacji PSTN: wywołanie zostało zakończone, jakość wywołań jest akceptowalna, czas połączenia jest akceptowalny.

  - Sprawdź, czy stan obecności kontaktów jest aktualizowany zarówno dla członków dzierżawy, jak i użytkowników federacyjnych.

### <a name="common-problems"></a>Typowe problemy

Routing asymetryczny jest najczęstszym problemem z implementacją. Oto kilka typowych źródeł, których należy szukać:
  
- Korzystanie z topologii routingu sieci otwartej lub płaskiej bez źródłowego translatora adresów sieciowych.

- Nie używasz SNAT do kierowania do usług przychodzących zarówno za pośrednictwem Internetu, jak i połączeń usługi ExpressRoute.

- Nie testowanie usług przychodzących w usłudze ExpressRoute w sieci testowej przed szerokim wdrożeniem.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Wdrażanie łączności usługi ExpressRoute za pośrednictwem sieci
<a name="testing"> </a>

Etap wdrożenia do jednego segmentu sieci naraz, stopniowo wdrażając łączność z różnymi częściami sieci z planem wycofania dla każdego nowego segmentu sieci. Jeśli wdrożenie jest zgodne z wdrożeniem Office 365, najpierw wdróż na Office 365 użytkowników pilotażowych i rozszerz je stamtąd.
  
Najpierw na potrzeby testu, a następnie w środowisku produkcyjnym:
  
- Uruchom kroki wdrażania, aby włączyć usługę ExpressRoute.

- Sprawdź, czy widzisz, że trasy sieciowe są zgodnie z oczekiwaniami.

- Wykonaj testy dla każdej usługi przychodzącej i wychodzącej.

- Wycofywanie w przypadku wykrycia jakichkolwiek problemów.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Konfigurowanie połączenia testowego z usługą ExpressRoute przy użyciu segmentu sieci testowej

Teraz, gdy masz ukończony plan na papierze, nadszedł czas, aby przetestować go na małą skalę. W tym teście ustanowisz jedno połączenie usługi ExpressRoute z komunikacją równorzędną firmy Microsoft z podsiecią testową w sieci lokalnej. Możesz skonfigurować [dzierżawę Office 365 próbną](https://go.microsoft.com/fwlink/p/?LinkID=403802) z łącznością z i z podsieci testowej oraz uwzględnić wszystkie usługi wychodzące i przychodzące, których będziesz używać w środowisku produkcyjnym w podsieci testowej. Skonfiguruj usługę DNS dla segmentu sieci testowej i ustal wszystkie usługi przychodzące i wychodzące. Wykonaj plan testu i upewnij się, że znasz routing dla każdej usługi i propagację trasy.
  
### <a name="execute-the-deployment-and-test-plans"></a>Wykonywanie planów wdrażania i testowania

Po ukończeniu opisanych powyżej elementów sprawdź ukończone obszary i upewnij się, że Ty i Twój zespół przejrzeliście je przed wykonaniem planów wdrażania i testowania.
  
- Lista usług wychodzących i przychodzących, które są zaangażowane w zmianę sieci.

- Diagram architektury sieci globalnej przedstawiający zarówno ruch wychodzący z Internetu, jak i lokalizacje spotkania usługi ExpressRoute.

- Diagram routingu sieciowego przedstawiający różne ścieżki sieciowe używane dla każdej wdrożonej usługi.

- Plan wdrożenia z krokami implementowania zmian i wycofywania w razie potrzeby.

- Plan testowy testowania każdego Office 365 i usługi sieciowej.

- Ukończono weryfikację papieru tras produkcyjnych dla usług przychodzących i wychodzących.

- Ukończony test w segmencie sieci testowej, w tym testowanie dostępności.

Wybierz okno awarii, które jest wystarczająco długie, aby przejść przez cały plan wdrożenia i plan testu, ma trochę czasu na rozwiązywanie problemów i czas na wycofanie w razie potrzeby.
  
> [!CAUTION]
> Ze względu na złożony charakter routingu przez Internet i usługę ExpressRoute zaleca się dodanie dodatkowego czasu buforu do tego okna w celu obsługi rozwiązywania problemów ze złożonym routingiem.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Konfigurowanie usługi QoS dla usługi Skype dla firm Online

Usługa QoS jest niezbędna do uzyskania korzyści związanych z obsługą głosu i spełniania Skype dla firm Online. Usługę QoS można skonfigurować po upewnieniu się, że połączenie sieciowe usługi ExpressRoute nie blokuje dostępu innych usług Office 365. Konfiguracja usługi QoS została opisana w artykule [ExpressRoute and QoS in Skype dla firm Online ( Usługa ExpressRoute i QoS w usłudze Skype dla firm Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)).
  
## <a name="troubleshooting-your-implementation"></a>Rozwiązywanie problemów z implementacją
<a name="troubleshooting"> </a>

Najpierw należy zapoznać się z krokami opisanymi w tym przewodniku implementacji, czy zostały pominięte w planie implementacji? Wstecz i uruchom dalsze małe testy sieciowe, jeśli to możliwe, aby zreplikować błąd i debugować go tam.
  
Określ, które usługi przychodzące lub wychodzące nie powiodły się podczas testowania. Pobierz w szczególności adresy IP i podsieci dla każdej usługi, która uległa awarii. Przejdź do diagramu topologii sieci na papierze i zweryfikuj routing. Sprawdź, gdzie jest anonsowany routing usługi ExpressRoute, przetestuj ten routing podczas awarii, jeśli jest to możliwe ze śladami.
  
Uruchom narzędzie PSPing ze śledzeniem sieci dla każdego punktu końcowego klienta i oceń źródłowe i docelowe adresy IP, aby sprawdzić, czy są one zgodnie z oczekiwaniami. Uruchom polecenie telnet na dowolnym hoście poczty uwidacznianym na porcie 25 i sprawdź, czy usługa SNAT ukrywa oryginalny źródłowy adres IP, jeśli jest to oczekiwane.
  
Należy pamiętać, że podczas wdrażania Office 365 z połączeniem usługi ExpressRoute należy upewnić się, że konfiguracja sieci dla usługi ExpressRoute jest optymalnie zaprojektowana, a także zoptymalizowano inne składniki w sieci, takie jak komputery klienckie. Oprócz użycia tego przewodnika planowania do rozwiązywania problemów z krokami, które mogły zostać pominięte, napisaliśmy również [plan rozwiązywania problemów z wydajnością dla Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365](managing-expressroute-for-connectivity.md)
  
[Routing przy użyciu usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
  
[Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365](network-planning-with-expressroute.md)
  
[Używanie społeczności protokołu BGP w usłudze ExpressRoute na potrzeby scenariuszy Office 365](bgp-communities-in-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod kątem Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Usługi ExpressRoute i QoS w usłudze Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ wywołań przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)
