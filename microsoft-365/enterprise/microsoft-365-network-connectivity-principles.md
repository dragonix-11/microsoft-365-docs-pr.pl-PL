---
title: Zasady dotyczące łączności sieciowej na platformie Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Ten artykuł zawiera najnowsze wskazówki dotyczące bezpiecznej optymalizacji Microsoft 365 łączności sieciowej.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e92f30c356ae782ba7d4d3bb779b744bccebf320
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944486"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Zasady dotyczące łączności sieciowej na platformie Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Przed rozpoczęciem planowania sieci na potrzeby Microsoft 365 łączności sieciowej ważne jest zrozumienie zasad łączności w celu bezpiecznego zarządzania ruchem Microsoft 365 i uzyskania najlepszej możliwej wydajności. Ten artykuł pomoże Ci zrozumieć najnowsze wskazówki dotyczące bezpiecznej optymalizacji Microsoft 365 łączności sieciowej.
  
Tradycyjne sieci przedsiębiorstwa są przeznaczone przede wszystkim w celu zapewnienia użytkownikom dostępu do aplikacji i danych hostowanych w obsługiwanych przez firmę centrach danych z silnymi zabezpieczeniami obwodowymi. Tradycyjny model zakłada, że użytkownicy będą uzyskiwać dostęp do aplikacji i danych z wewnątrz obwodu sieci firmowej, za pośrednictwem linków sieci WAN z oddziałów lub zdalnie za pośrednictwem połączeń sieci VPN.
  
Wdrożenie aplikacji SaaS, takich jak Microsoft 365, przenosi pewną kombinację usług i danych poza obwód sieci. Bez optymalizacji ruch między użytkownikami a aplikacjami SaaS podlega opóźnieniom wprowadzonym przez inspekcję pakietów, spinki do włosów sieci, przypadkowe połączenia z geograficznie odległymi punktami końcowymi i inne czynniki. Aby zapewnić najlepszą Microsoft 365 wydajność i niezawodność, możesz zrozumieć i zaimplementować wytyczne dotyczące optymalizacji kluczy.
  
W tym artykule dowiesz się więcej na temat:
  
- [Microsoft 365 architektury](microsoft-365-network-connectivity-principles.md#BKMK_Architecture), która ma zastosowanie do łączności klienta z chmurą
- Zaktualizowano [Microsoft 365 zasad łączności](microsoft-365-network-connectivity-principles.md#BKMK_Principles) i strategii optymalizacji ruchu sieciowego i środowiska użytkownika końcowego
- [Usługa internetowa Office 365 Endpoints](microsoft-365-network-connectivity-principles.md#BKMK_WebSvc), która umożliwia administratorom sieci korzystanie ze strukturalnej listy punktów końcowych do użycia w optymalizacji sieci
- [Nowe kategorie punktów końcowych Office 365](microsoft-365-network-connectivity-principles.md#BKMK_Categories) i wskazówki dotyczące optymalizacji
- [Porównanie zabezpieczeń obwodowych sieci z zabezpieczeniami punktu końcowego](microsoft-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- [Opcje optymalizacji przyrostowej](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) dla ruchu Microsoft 365
- [Test łączności Microsoft 365](https://aka.ms/netonboard), nowe narzędzie do testowania podstawowej łączności z Microsoft 365

## <a name="microsoft-365-architecture"></a>architektura Microsoft 365
<a name="BKMK_Architecture"> </a>

Microsoft 365 jest rozproszoną chmurą typu oprogramowanie jako usługa (SaaS), która zapewnia scenariusze produktywności i współpracy za pośrednictwem zróżnicowanego zestawu mikrousługow i aplikacji, takich jak Exchange Online, SharePoint Online, Skype dla firm Online, Microsoft Teams, Exchange Online Protection, Office w przeglądarce i wielu innych. Chociaż określone aplikacje Microsoft 365 mogą mieć swoje unikatowe funkcje, ponieważ mają zastosowanie do sieci klienta i łączności z chmurą, wszystkie mają pewne kluczowe podmioty zabezpieczeń, cele i wzorce architektury. Te zasady i wzorce architektury dotyczące łączności są typowe dla wielu innych chmur SaaS, a jednocześnie różnią się od typowych modeli wdrażania chmur typu "platforma jako usługa" i "infrastruktura jako usługa", takich jak Microsoft Azure.
  
Jedną z najważniejszych cech architektury Microsoft 365 (która jest często pomijana lub błędnie interpretowana przez architektów sieci) jest to, że jest to naprawdę globalna usługa rozproszona w kontekście sposobu łączenia się z nią przez użytkowników. Lokalizacja docelowej dzierżawy Microsoft 365 jest ważna, aby zrozumieć lokalizację, w której dane klientów są przechowywane w chmurze, ale środowisko użytkownika z Microsoft 365 nie obejmuje bezpośredniego łączenia się z dyskami zawierającymi dane. Środowisko użytkownika z Microsoft 365 (w tym wydajnością, niezawodnością i innymi ważnymi cechami jakości) obejmuje łączność za pośrednictwem wysoce rozproszonych drzwi frontowych usługi, które są skalowane w poziomie w setkach lokalizacji firmy Microsoft na całym świecie. W większości przypadków najlepsze środowisko użytkownika jest osiągane przez umożliwienie sieci klienta kierowania żądań użytkowników do najbliższego punktu wejścia usługi Microsoft 365 zamiast nawiązywania połączenia z Microsoft 365 za pośrednictwem punktu ruchu wychodzącego w centralnej lokalizacji lub regionie.
  
W przypadku większości klientów Microsoft 365 użytkownicy są dystrybuowane w wielu lokalizacjach. Aby osiągnąć najlepsze wyniki, zasady opisane w tym dokumencie powinny być sprawdzane z punktu widzenia skalowania w poziomie (nie skalowania w górę), koncentrując się na optymalizacji łączności z najbliższym punktem obecności w globalnej sieci firmy Microsoft, a nie lokalizacji geograficznej dzierżawy Microsoft 365. Zasadniczo oznacza to, że nawet jeśli Microsoft 365 dane dzierżawy mogą być przechowywane w określonej lokalizacji geograficznej, środowisko Microsoft 365 dla tej dzierżawy pozostaje rozproszone i może znajdować się w bardzo bliskiej (sieci) blisko każdej lokalizacji użytkownika końcowego, którą ma dzierżawa.
  
## <a name="microsoft-365-connectivity-principles"></a>zasady łączności Microsoft 365
<a name="BKMK_Principles"> </a>

Firma Microsoft zaleca następujące zasady, aby osiągnąć optymalną Microsoft 365 łączności i wydajności. Użyj tych Microsoft 365 zasad łączności, aby zarządzać ruchem i uzyskać najlepszą wydajność podczas nawiązywania połączenia z Microsoft 365.
  
Głównym celem projektu sieci powinno być zminimalizowanie opóźnienia przez skrócenie czasu rundy (RTT) z sieci do sieci globalnej firmy Microsoft, sieci publicznej sieci szkieletowej firmy Microsoft, która łączy wszystkie centra danych firmy Microsoft z małymi opóźnieniami i punktami wejścia aplikacji w chmurze rozłożonymi na całym świecie. Więcej informacji na temat globalnej sieci firmy Microsoft można znaleźć w artykułach [How Microsoft builds its fast and reliable global network (Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identyfikowanie i rozróżnianie ruchu Microsoft 365

![Identyfikowanie ruchu Microsoft 365.](../media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identyfikowanie ruchu sieciowego Microsoft 365 jest pierwszym krokiem do odróżnienia tego ruchu od ogólnego ruchu sieciowego powiązanego z Internetem. Microsoft 365 łączność można zoptymalizować, implementując kombinację metod, takich jak optymalizacja tras sieciowych, reguły zapory, ustawienia serwera proxy przeglądarki i obejście urządzeń inspekcji sieci dla niektórych punktów końcowych.
  
Poprzednie wskazówki dotyczące optymalizacji Microsoft 365 podzieliły punkty końcowe Microsoft 365 na dwie kategorie: **Wymagane** i **Opcjonalne**. Po dodaniu punktów końcowych do obsługi nowych usług i funkcji Microsoft 365 zreorganizowaliśmy Microsoft 365 punktów końcowych na trzy **kategorie: Optymalizuj**, **Zezwalaj** i **Domyślne**. Wytyczne dla każdej kategorii dotyczą wszystkich punktów końcowych w kategorii, co ułatwia zrozumienie i zaimplementowanie optymalizacji.
  
Aby uzyskać więcej informacji na temat Microsoft 365 kategorii punktów końcowych i metod optymalizacji, zobacz sekcję [New Office 365 endpoint categories (Nowe Office 365 kategorie punktów końcowych](microsoft-365-network-connectivity-principles.md#BKMK_Categories)).
  
Firma Microsoft publikuje teraz wszystkie punkty końcowe Microsoft 365 jako usługę internetową i zawiera wskazówki dotyczące najlepszego wykorzystania tych danych. Aby uzyskać więcej informacji na temat pobierania i pracy z punktami końcowymi Microsoft 365, zobacz artykuł [Office 365 adresów URL i zakresów adresów IP](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Egress połączeń sieciowych lokalnie

![Egress połączeń sieciowych lokalnie.](../media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Lokalny ruch wychodzący DNS i Internet ma kluczowe znaczenie dla zmniejszenia opóźnienia połączenia i zapewnienia, że połączenia użytkowników są nawiązywane do najbliższego punktu wejścia do usług Microsoft 365. W złożonej topologii sieci ważne jest, aby razem zaimplementować zarówno lokalny system DNS, jak i lokalny internetowy ruch wychodzący. Aby uzyskać więcej informacji na temat sposobu, w jaki Microsoft 365 kieruje połączenia klienta do najbliższego punktu wejścia, zobacz artykuł [Łączność klienta](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Przed pojawieniem się usług w chmurze, takich jak Microsoft 365, łączność internetowa użytkownika końcowego jako czynnik projektowy architektury sieci była stosunkowo prosta. Gdy usługi internetowe i witryny internetowe są dystrybuowane na całym świecie, opóźnienie między firmowymi punktami ruchu wychodzącego i dowolnym docelowym punktem końcowym jest w dużej mierze funkcją odległości geograficznej.
  
W tradycyjnej architekturze sieci wszystkie wychodzące połączenia internetowe przechodzą przez sieć firmową i wychodzące z centralnej lokalizacji. W miarę dojrzewania ofert firmy Microsoft w chmurze rozproszona architektura sieci dostępna z Internetu stała się kluczowa dla obsługi usług w chmurze wrażliwych na opóźnienia. Globalna sieć firmy Microsoft została zaprojektowana w celu spełnienia wymagań dotyczących opóźnień dzięki infrastrukturze usługi Distributed Service Front Door, dynamicznej sieci szkieletowej globalnych punktów wejścia, która kieruje przychodzące połączenia usługi w chmurze do najbliższego punktu wejścia. Ma to na celu zmniejszenie długości "ostatniej mili" dla klientów chmury firmy Microsoft przez efektywne skrócenie trasy między klientem a chmurą.
  
Enterprise sieci WAN są często przeznaczone do obsługi ruchu sieciowego do centrali firmy w celu przeprowadzenia inspekcji przed wyjściem do Internetu, zwykle za pośrednictwem co najmniej jednego serwera proxy. Na poniższym diagramie przedstawiono taką topologię sieci.
  
![Tradycyjny model sieci przedsiębiorstwa.](../media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Ponieważ Microsoft 365 działa w globalnej sieci firmy Microsoft, która obejmuje serwery frontonu na całym świecie, serwer frontonu często znajduje się w pobliżu lokalizacji użytkownika. Dzięki zapewnieniu lokalnego ruchu wychodzącego z Internetu i skonfigurowaniu wewnętrznych serwerów DNS w celu zapewnienia lokalnego rozpoznawania nazw dla Microsoft 365 punktów końcowych ruch sieciowy przeznaczony dla Microsoft 365 może łączyć się z serwerami frontonu Microsoft 365 jak najbliżej użytkownika. Na poniższym diagramie przedstawiono przykład topologii sieci, która umożliwia użytkownikom nawiązywanie połączeń z głównego biura, oddziału i lokalizacji zdalnych na podążanie najkrótszą trasą do najbliższego punktu wejścia Microsoft 365.
  
![Model sieci WAN z regionalnymi punktami ruchu wychodzącego.](../media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Skrócenie ścieżki sieciowej do Microsoft 365 punktów wejścia w ten sposób może zwiększyć wydajność łączności i środowisko użytkownika końcowego w Microsoft 365, a także może pomóc zmniejszyć wpływ przyszłych zmian architektury sieci na wydajność i niezawodność Microsoft 365.
  
Ponadto żądania DNS mogą wprowadzać opóźnienie, jeśli odpowiadający serwer DNS jest odległy lub zajęty. Opóźnienie rozpoznawania nazw można zminimalizować, aprowizując lokalne serwery DNS w lokalizacjach gałęzi i upewniając się, że są one odpowiednio skonfigurowane do buforowania rekordów DNS.
  
Chociaż regionalny ruch wychodzący może działać dobrze dla Microsoft 365, optymalnym modelem łączności byłoby zawsze zapewnienie ruchu wychodzącego sieci w lokalizacji użytkownika, niezależnie od tego, czy jest to sieć firmowa, czy zdalne lokalizacje, takie jak domy, hotele, kawiarnie i lotniska. Ten lokalny model bezpośredniego ruchu wychodzącego jest reprezentowany na poniższym diagramie.
  
![Architektura lokalnej sieci wychodzącej.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Przedsiębiorstwa, które przyjęły Microsoft 365, mogą skorzystać z architektury usługi Front Door usługi rozproszonej firmy Microsoft, zapewniając, że połączenia użytkowników z Microsoft 365 najkrótszą możliwą trasą do najbliższego punktu wejścia do sieci globalnej firmy Microsoft. Lokalna architektura sieci wychodzącej umożliwia kierowanie ruchu Microsoft 365 przez najbliższy ruch wychodzący, niezależnie od lokalizacji użytkownika.
  
Architektura ruchu wychodzącego lokalnego zapewnia następujące korzyści w stosunku do tradycyjnego modelu:
  
- Zapewnia optymalną wydajność Microsoft 365 przez optymalizowanie długości trasy. Połączenia użytkowników końcowych są dynamicznie kierowane do najbliższego punktu wejścia Microsoft 365 przez infrastrukturę usługi Rozproszona usługa Front Door.
- Zmniejsza obciążenie infrastruktury sieci firmowej, zezwalając na ruch wychodzący lokalny.
- Zabezpiecza połączenia na obu końcach dzięki wykorzystaniu zabezpieczeń punktów końcowych klienta i funkcji zabezpieczeń w chmurze.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Unikanie sieciowych spinek do włosów

![Unikaj spinek do włosów.](../media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Ogólnie rzecz biorąc, najkrótsza, najbardziej bezpośrednia trasa między użytkownikiem a najbliższym punktem końcowym Microsoft 365 zapewni najlepszą wydajność. Spin sieciowy występuje, gdy ruch sieci WAN lub sieci VPN powiązany z określonym miejscem docelowym jest najpierw kierowany do innej lokalizacji pośredniej (takiej jak stos zabezpieczeń, broker dostępu do chmury lub brama internetowa oparta na chmurze), wprowadzając opóźnienia i potencjalne przekierowanie do geograficznie odległego punktu końcowego. Spinki do włosów sieci mogą być również spowodowane przez nieefektywność routingu/komunikacji równorzędnej lub nieoptymalne (zdalne) odnośniki DNS.
  
Aby upewnić się, że łączność Microsoft 365 nie jest objęta siecią nawet w przypadku ruchu wychodzącego lokalnego, sprawdź, czy usługodawca internetowy, który jest używany do zapewnienia ruchu wychodzącego z Internetu dla lokalizacji użytkownika, ma bezpośrednią relację komunikacji równorzędnej z globalną siecią microsoft w pobliżu tej lokalizacji. Możesz również skonfigurować routing ruchu wychodzącego w celu bezpośredniego wysyłania zaufanego ruchu Microsoft 365, w przeciwieństwie do serwera proxy lub tunelowania przez dostawcę zabezpieczeń sieci w chmurze lub w chmurze, który przetwarza ruch związany z Internetem. Lokalne rozpoznawanie nazw DNS Microsoft 365 punktów końcowych pomaga zapewnić, że oprócz routingu bezpośredniego najbliższe punkty wejścia Microsoft 365 są używane na potrzeby połączeń użytkowników.
  
Jeśli używasz sieci opartej na chmurze lub usług zabezpieczeń dla ruchu Microsoft 365, upewnij się, że wynik spinki do włosów jest oceniany, a jego wpływ na wydajność Microsoft 365 jest zrozumiały. Można to zrobić, sprawdzając liczbę i lokalizacje lokalizacji dostawców usług, za pośrednictwem których ruch jest przekazywany w związku z liczbą oddziałów i punktów komunikacji równorzędnej usługi Microsoft Global Network, jakością relacji komunikacji równorzędnej sieci dostawcy usług z usługodawcą isp i firmą Microsoft oraz wpływem na wydajność komunikacji równorzędnej w infrastrukturze dostawcy usług.
  
Ze względu na dużą liczbę rozproszonych lokalizacji z punktami wejścia Microsoft 365 i ich bliskość do użytkowników końcowych, routing ruchu Microsoft 365 do dowolnej sieci innej firmy lub dostawcy zabezpieczeń może mieć negatywny wpływ na połączenia Microsoft 365, jeśli sieć dostawcy nie jest skonfigurowana pod kątem optymalnego Microsoft 365 Wpatrując się.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Ocena pomijania serwerów proxy, urządzeń inspekcji ruchu i zduplikowanych technologii zabezpieczeń

![Pomijaj serwery proxy, urządzenia inspekcji ruchu i zduplikowane technologie zabezpieczeń.](../media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Enterprise klienci powinni zapoznać się ze swoimi metodami bezpieczeństwa sieci i ograniczania ryzyka w szczególności w przypadku ruchu powiązanego Microsoft 365 i korzystać z Microsoft 365 funkcji zabezpieczeń, aby zmniejszyć zależność od natrętnych, wpływających na wydajność i kosztownych technologii zabezpieczeń sieciowych dla ruchu sieciowego Microsoft 365.
  
Większość sieci przedsiębiorstwa wymusza zabezpieczenia sieci dla ruchu internetowego przy użyciu technologii, takich jak serwery proxy, inspekcja protokołu SSL, inspekcja pakietów i systemy zapobiegania utracie danych. Technologie te zapewniają istotne ograniczenie ryzyka dla ogólnych żądań internetowych, ale mogą znacznie zmniejszyć wydajność, skalowalność i jakość środowiska użytkownika końcowego, gdy są stosowane do Microsoft 365 punktów końcowych.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>usługa sieci Web punktów końcowych Office 365

Microsoft 365 administratorzy mogą używać skryptu lub wywołania REST, aby korzystać ze strukturalnej listy punktów końcowych z usługi sieci Web punktów końcowych Office 365 i aktualizować konfiguracje zapór obwodowych i innych urządzeń sieciowych. Zapewni to, że ruch związany z Microsoft 365 zostanie zidentyfikowany, odpowiednio potraktowany i zarządzany inaczej niż ruch sieciowy powiązany z ogólnymi i często nieznanymi internetowymi witrynami internetowymi. Aby uzyskać więcej informacji na temat korzystania z usługi internetowej Office 365 Endpoints, zobacz artykuł [Office 365 adresów URL i zakresów adresów IP](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Skrypty PAC (automatyczna konfiguracja serwera proxy)
<a name="BKMK_WebSvc"> </a>

Microsoft 365 administratorzy mogą tworzyć skrypty PAC (automatyczna konfiguracja serwera proxy), które mogą być dostarczane do komputerów użytkowników za pośrednictwem urządzenia WPAD lub obiektu zasad grupy. Skrypty PAC mogą służyć do obejścia serwerów proxy dla żądań Microsoft 365 od użytkowników sieci WAN lub sieci VPN, dzięki czemu ruch Microsoft 365 może korzystać z bezpośrednich połączeń internetowych zamiast przechodzić przez sieć firmową.
  
#### <a name="microsoft-365-security-features"></a>funkcje zabezpieczeń Microsoft 365
<a name="BKMK_WebSvc"> </a>

Firma Microsoft jest przejrzysta w zakresie zabezpieczeń centrum danych, zabezpieczeń operacyjnych i zmniejszania ryzyka związanego z serwerami Microsoft 365 i punktami końcowymi sieci, które reprezentują. Microsoft 365 dostępne są wbudowane funkcje zabezpieczeń w celu zmniejszenia ryzyka bezpieczeństwa sieci, takie jak ochrona przed utratą danych w usłudze Microsoft Purview, ochrona przed wirusami, uwierzytelnianie wieloskładnikowe, pole blokady klienta, Ochrona usługi Office 365 w usłudze Defender, Microsoft 365 analiza zagrożeń, Microsoft 365 wskaźnika bezpieczeństwa, Exchange Online Protection i zabezpieczeń DDOS sieci.
  
Aby uzyskać więcej informacji na temat zabezpieczeń centrum danych firmy Microsoft i sieci globalnej, zobacz [Centrum zaufania firmy Microsoft](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nowe kategorie punktów końcowych Office 365
<a name="BKMK_Categories"> </a>

Office 365 punkty końcowe reprezentują zróżnicowany zestaw adresów sieciowych i podsieci. Punkty końcowe mogą być adresami URL, adresami IP lub zakresami adresów IP, a niektóre punkty końcowe są wymienione z określonymi portami TCP/UDP. Adresy URL mogą być nazwą FQDN, taką jak *account.office.net*, lub adresem URL symbolu wieloznacznego, takim jak *\*.office365.com*.
  
> [!NOTE]
> Lokalizacje Office 365 punktów końcowych w sieci nie są bezpośrednio powiązane z lokalizacją danych dzierżawy Microsoft 365. Z tego powodu klienci powinni patrzeć na Microsoft 365 jako usługę rozproszoną i globalną i nie powinni próbować blokować połączeń sieciowych z punktami końcowymi Office 365 na podstawie kryteriów geograficznych.
  
W naszych poprzednich wskazówkach dotyczących zarządzania ruchem Microsoft 365 punkty końcowe zostały podzielone na dwie kategorie: **Wymagane** i **Opcjonalne**. Punkty końcowe w każdej kategorii wymagały różnych optymalizacji w zależności od krytyczności usługi, a wielu klientów napotkało wyzwania związane z uzasadnieniem zastosowania tych samych optymalizacji sieci do pełnej listy adresów URL i adresów IP Office 365.
  
W nowym modelu punkty końcowe są podzielone na trzy **kategorie: Optymalizuj**, **Zezwalaj** i **Domyślne**, zapewniając oparty na priorytecie punkt przestawny, w którym należy skoncentrować działania optymalizacji sieci w celu osiągnięcia najlepszych ulepszeń wydajności i zwrotu z inwestycji. Punkty końcowe są konsolidowane w powyższych kategoriach w oparciu o wrażliwość efektywnego środowiska użytkownika na jakość sieci, wolumin i wydajność scenariuszy oraz łatwość implementacji. Zalecane optymalizacje można zastosować w ten sam sposób do wszystkich punktów końcowych w danej kategorii.
  
- **Optymalizacja** punktów końcowych jest wymagana do łączności z każdą usługą Office 365 i stanowi ponad 75% przepustowości Office 365, połączeń i ilości danych. Te punkty końcowe reprezentują Office 365 scenariuszy, które są najbardziej wrażliwe na wydajność, opóźnienie i dostępność sieci. Wszystkie punkty końcowe są hostowane w centrach danych firmy Microsoft. Oczekuje się, że szybkość zmiany punktów końcowych w tej kategorii będzie znacznie niższa niż w przypadku punktów końcowych w dwóch pozostałych kategoriach. Ta kategoria obejmuje niewielki zestaw adresów URL kluczy (rzędu ok. 10) oraz zdefiniowany zestaw podsieci IP przeznaczonych dla podstawowych obciążeń Office 365, takich jak Exchange Online, SharePoint Online, Skype dla firm Online i Microsoft Teams.

    Skrócona lista dobrze zdefiniowanych krytycznych punktów końcowych powinna pomóc w szybszym i łatwiejszym planowaniu i implementowaniu optymalizacji sieci o wysokiej wartości dla tych miejsc docelowych.

    Przykłady punktów końcowych  *optymalizacji*  to *https://outlook.office365.com*, *https://\<tenant\>.sharepoint.com* i *https://\<tenant\>-my.sharepoint.com*.

    Metody optymalizacji obejmują:

  - *Pomiń optymalizowanie* punktów końcowych na urządzeniach sieciowych i usługach, które wykonują przechwytywanie ruchu, odszyfrowywanie SSL, głęboką inspekcję pakietów i filtrowanie zawartości.
  - Pomijaj lokalne urządzenia proxy i usługi serwera proxy oparte na chmurze, które są często używane do ogólnego przeglądania Internetu.
  - Określanie priorytetów oceny tych punktów końcowych jako w pełni zaufanych przez infrastrukturę sieci i systemy obwodowe.
  - Priorytetyzowanie redukcji lub eliminacji zaplecza sieci WAN i ułatwienie bezpośredniego rozproszonego ruchu wychodzącego opartego na Internecie dla tych punktów końcowych tak blisko lokalizacji użytkowników/oddziałów, jak to możliwe.
  - Ułatwianie bezpośredniej łączności z tymi punktami końcowymi w chmurze dla użytkowników sieci VPN przez zaimplementowanie tunelowania podzielonego.
  - Upewnij się, że adresy IP zwracane przez rozpoznawanie nazw DNS są zgodne ze ścieżką ruchu wychodzącego routingu dla tych punktów końcowych.
  - Nadaj priorytet tym punktom końcowym integracji SD-WAN w przypadku bezpośredniego, minimalnego routingu opóźnień do najbliższego internetowego punktu komunikacji równorzędnej sieci globalnej firmy Microsoft.

- **Zezwalaj na** punkty końcowe są wymagane do łączności z określonymi usługami i funkcjami Office 365, ale nie są tak wrażliwe na wydajność i opóźnienie sieci, jak w kategorii *Optymalizacja*. Ogólny ślad sieciowy tych punktów końcowych z punktu widzenia przepustowości i liczby połączeń jest również mniejszy. Te punkty końcowe są przeznaczone dla Office 365 i są hostowane w centrach danych firmy Microsoft. Reprezentują one szeroki zestaw Office 365 mikrousług i ich zależności (w kolejności ok. 100 adresów URL) i oczekuje się, że zmienią się z większą szybkością niż w kategorii *Optymalizacja*. Nie wszystkie punkty końcowe w tej kategorii są skojarzone ze zdefiniowanymi dedykowanymi podsieciami IP.

    Optymalizacje *sieci dla* zezwalających punktów końcowych mogą poprawić środowisko Office 365 użytkownika, ale niektórzy klienci mogą zdecydować się na bardziej wąski zakres tych optymalizacji, aby zminimalizować zmiany w sieci.

    Przykłady *zezwalania na* punkty końcowe obejmują *https://\*.protection.outlook.com* i *https://accounts.accesscontrol.windows.net*.

    Metody optymalizacji obejmują:

  - *Pomiń pozycję Zezwalaj* na punkty końcowe na urządzeniach sieciowych i usługach, które wykonują przechwytywanie ruchu, odszyfrowywanie SSL, głęboką inspekcję pakietów i filtrowanie zawartości.
  - Określanie priorytetów oceny tych punktów końcowych jako w pełni zaufanych przez infrastrukturę sieci i systemy obwodowe.
  - Priorytetyzowanie redukcji lub eliminacji zaplecza sieci WAN i ułatwienie bezpośredniego rozproszonego ruchu wychodzącego opartego na Internecie dla tych punktów końcowych tak blisko lokalizacji użytkowników/oddziałów, jak to możliwe.
  - Upewnij się, że adresy IP zwracane przez rozpoznawanie nazw DNS są zgodne ze ścieżką ruchu wychodzącego routingu dla tych punktów końcowych.
  - Nadaj priorytet tym punktom końcowym integracji SD-WAN w przypadku bezpośredniego, minimalnego routingu opóźnień do najbliższego internetowego punktu komunikacji równorzędnej sieci globalnej firmy Microsoft.

- **Domyślne** punkty końcowe reprezentują usługi i zależności Office 365, które nie wymagają żadnej optymalizacji i mogą być traktowane przez sieci klientów jako normalny ruch związany z Internetem. Niektóre punkty końcowe w tej kategorii mogą nie być hostowane w centrach danych firmy Microsoft. Przykłady obejmują  *https://odc.officeapps.live.com*  i  *https://appexsin.stb.s-msn.com*.

Aby uzyskać więcej informacji na temat Office 365 technik optymalizacji sieci, zobacz artykuł [Zarządzanie punktami końcowymi Office 365](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Porównanie zabezpieczeń obwodowych sieci z zabezpieczeniami punktu końcowego
<a name="BKMK_SecurityComparison"> </a>

Celem tradycyjnych zabezpieczeń sieci jest wzmocnienie obwodu sieci firmowej przed nieautoryzowanym dostępem i złośliwymi lukami w zabezpieczeniach. W miarę jak organizacje przyjmują Microsoft 365, niektóre usługi sieciowe i dane są częściowo lub całkowicie migrowane do chmury. Jeśli chodzi o wszelkie fundamentalne zmiany w architekturze sieci, ten proces wymaga ponownej ewaluacji zabezpieczeń sieci, która uwzględnia nowe czynniki:
  
- W miarę wdrażania usług w chmurze usługi sieciowe i dane są dystrybuowane między lokalnymi centrami danych i chmurą, a zabezpieczenia obwodowe nie są już odpowiednie samodzielnie.
- Użytkownicy zdalni łączą się z zasobami firmy zarówno w lokalnych centrach danych, jak i w chmurze z niekontrolowanych lokalizacji, takich jak domy, hotele i kawiarnie.
- Specjalnie utworzone funkcje zabezpieczeń są coraz bardziej wbudowane w usługi w chmurze i mogą potencjalnie uzupełniać lub zastępować istniejące systemy zabezpieczeń.

Firma Microsoft oferuje szeroką gamę funkcji zabezpieczeń Microsoft 365 i zapewnia nakazowe wskazówki dotyczące stosowania najlepszych rozwiązań w zakresie zabezpieczeń, które mogą pomóc w zapewnieniu bezpieczeństwa danych i sieci dla Microsoft 365. Zalecane najlepsze rozwiązania obejmują następujące kwestie:
  
- **Korzystanie z uwierzytelniania wieloskładnikowego (MFA)** Uwierzytelnianie wieloskładnikowe dodaje dodatkową warstwę ochrony do silnej strategii haseł, wymagając od użytkowników potwierdzenia połączenia telefonicznego, wiadomości SMS lub powiadomienia aplikacji na smartfonie po poprawnym wprowadzeniu hasła.

- **Użyj Microsoft Defender for Cloud Apps** Konfigurowanie zasad, aby śledzić nietypowe działania i działać na nich. Skonfiguruj alerty za pomocą Microsoft Defender for Cloud Apps, aby administratorzy mogli przeglądać nietypowe lub ryzykowne działania użytkowników, takie jak pobieranie dużych ilości danych, wiele nieudanych prób logowania lub połączenia z nieznanych lub niebezpiecznych adresów IP.

- **Konfigurowanie ochrony przed utratą danych (DLP)** DLP umożliwia identyfikowanie poufnych danych i tworzenie zasad, które uniemożliwiają użytkownikom przypadkowe lub celowe udostępnianie danych. DLP działa w różnych Microsoft 365, w tym Exchange Online, SharePoint Online i OneDrive, aby użytkownicy mogli zachować zgodność bez przerywania przepływu pracy.

- **Używanie skrytki klienta** Jako administrator Microsoft 365 możesz użyć skrytki klienta, aby kontrolować, w jaki sposób inżynier pomocy technicznej firmy Microsoft uzyskuje dostęp do twoich danych podczas sesji pomocy. W przypadkach, gdy inżynier wymaga dostępu do danych w celu rozwiązania i rozwiązania problemu, skrytka klienta umożliwia zatwierdzenie lub odrzucenie żądania dostępu.

- **Użyj Office 365 Wskaźnik** bezpieczeństwa Narzędzie do analizy zabezpieczeń, które zaleca, co można zrobić, aby jeszcze bardziej zmniejszyć ryzyko. Wskaźnik bezpieczeństwa analizuje ustawienia i działania Microsoft 365 i porównuje je z punktem odniesienia ustanowionym przez firmę Microsoft. Uzyskasz ocenę na podstawie tego, jak dobrze jesteś zgodny z najlepszymi rozwiązaniami w zakresie zabezpieczeń.

Całościowe podejście do zwiększonych zabezpieczeń powinno obejmować następujące kwestie:
  
- Przesuń nacisk z zabezpieczeń obwodowych na zabezpieczenia punktów końcowych, stosując funkcje zabezpieczeń klienta oparte na chmurze i Office.
  - Zmniejszanie obwodu zabezpieczeń do centrum danych
  - Włączanie równoważnego zaufania dla urządzeń użytkowników w biurze lub w lokalizacjach zdalnych
  - Skoncentruj się na zabezpieczaniu lokalizacji danych i lokalizacji użytkownika
  - Zarządzane maszyny użytkowników mają większe zaufanie do zabezpieczeń punktu końcowego
- Całościowe zarządzanie wszystkimi zabezpieczeniami informacji, nie skupiając się wyłącznie na obwodzie
  - Ponowne definiowanie sieci WAN i tworzenie zabezpieczeń sieci obwodowej dzięki umożliwieniu zaufanemu ruchowi obejścia urządzeń zabezpieczeń i oddzielenia urządzeń niezarządzanych od sieci Wi-Fi gościa
  - Zmniejszanie wymagań dotyczących zabezpieczeń sieci w korporacyjnej przeglądarce sieci WAN
  - Niektóre urządzenia zabezpieczeń obwodowych sieci, takie jak zapory, są nadal wymagane, ale obciążenie jest zmniejszane
  - Zapewnia lokalny ruch wychodzący dla ruchu Microsoft 365
- Ulepszenia można rozwiązywać przyrostowo zgodnie z opisem w sekcji [Optymalizacja przyrostowa](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) . Niektóre techniki optymalizacji mogą oferować lepsze współczynniki kosztów i korzyści w zależności od architektury sieci i należy wybrać optymalizacje, które mają największy sens w organizacji.

Aby uzyskać więcej informacji na temat Microsoft 365 zabezpieczeń i zgodności, zobacz artykuły [Microsoft 365 security](../security/index.yml) i [Microsoft Purview](../compliance/index.yml).
  
## <a name="incremental-optimization"></a>Optymalizacja przyrostowa
<a name="BKMK_IncOpt"> </a>

Przedstawiliśmy idealny model łączności sieciowej dla usługi SaaS we wcześniejszej części tego artykułu, ale w przypadku wielu dużych organizacji z historycznie złożonymi architekturami sieci nie będzie praktyczne bezpośrednie wprowadzanie wszystkich tych zmian. W tej sekcji omówimy szereg zmian przyrostowych, które mogą pomóc zwiększyć wydajność i niezawodność Microsoft 365.
  
Metody optymalizacji ruchu Microsoft 365 będą się różnić w zależności od topologii sieci i zaimplementowanych urządzeń sieciowych. Duże przedsiębiorstwa z wieloma lokalizacjami i złożonymi rozwiązaniami w zakresie zabezpieczeń sieci będą musiały opracować strategię obejmującą większość lub wszystkie zasady wymienione w sekcji [zasad łączności Microsoft 365](microsoft-365-network-connectivity-principles.md#BKMK_Principles), podczas gdy mniejsze organizacje mogą wymagać uwzględnienia tylko jednej lub dwóch.
  
Optymalizację można podejść jako proces przyrostowy, stosując każdą metodę kolejno. Poniższa tabela zawiera listę metod optymalizacji kluczy w kolejności ich wpływu na opóźnienia i niezawodność dla największej liczby użytkowników.
  
|**Metoda optymalizacji**|**Opis**|**Wpływ**|
|:-----|:-----|:-----|
|Lokalne rozpoznawanie nazw DNS i ruch wychodzący z Internetu  <br/> |Aprowizuj lokalne serwery DNS w każdej lokalizacji i upewnij się, że Microsoft 365 połączenia wychodzące do Internetu jak najbliżej lokalizacji użytkownika.  <br/> | Minimalizowanie opóźnienia  <br/>  Ulepszanie niezawodnej łączności z najbliższym punktem wejścia Microsoft 365  <br/> |
|Dodawanie regionalnych punktów ruchu wychodzącego  <br/> |Jeśli sieć firmowa ma wiele lokalizacji, ale tylko jeden punkt ruchu wychodzącego, dodaj regionalne punkty ruchu wychodzącego, aby umożliwić użytkownikom nawiązywanie połączenia z najbliższym punktem wejścia Microsoft 365.  <br/> | Minimalizowanie opóźnienia  <br/>  Ulepszanie niezawodnej łączności z najbliższym punktem wejścia Microsoft 365  <br/> |
|Pomijanie serwerów proxy i urządzeń inspekcji  <br/> |Skonfiguruj przeglądarki przy użyciu plików PAC, które wysyłają żądania Microsoft 365 bezpośrednio do punktów ruchu wychodzącego.  <br/> Skonfiguruj routery brzegowe i zapory, aby zezwalać na ruch Microsoft 365 bez inspekcji.  <br/> | Minimalizowanie opóźnienia  <br/>  Zmniejszenie obciążenia urządzeń sieciowych  <br/> |
|Włączanie bezpośredniego połączenia dla użytkowników sieci VPN  <br/> |W przypadku użytkowników sieci VPN włącz Microsoft 365 połączenia, aby nawiązywać połączenia bezpośrednio z sieci użytkownika, a nie za pośrednictwem tunelu VPN, implementując tunelowanie podzielone.  <br/> | Minimalizowanie opóźnienia  <br/>  Ulepszanie niezawodnej łączności z najbliższym punktem wejścia Microsoft 365  <br/> |
|Migrowanie z tradycyjnej sieci WAN do sieci SD-WAN  <br/> |SD-WANs (Software Defined Wide Area Networks) upraszcza zarządzanie siecią WAN i poprawia wydajność, zastępując tradycyjne routery sieci WAN urządzeniami wirtualnymi, podobnie jak wirtualizacja zasobów obliczeniowych przy użyciu maszyn wirtualnych.  <br/> | Zwiększanie wydajności i możliwości zarządzania ruchem sieci WAN  <br/>  Zmniejszenie obciążenia urządzeń sieciowych  <br/> |

## <a name="related-topics"></a>Tematy pokrewne

[Omówienie łączności sieciowej Microsoft 365](microsoft-365-networking-overview.md)

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Usługa Office 365 — usługa sieci Web adresów IP i adresów URL](microsoft-365-ip-web-service.md)

[Ocena łączności sieciowej na platformie Microsoft 365](assessing-network-connectivity.md)

[Planowanie sieci i dostrajanie wydajności dla Microsoft 365](network-planning-and-performance.md)

[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)

[Sieci dostarczania zawartości](content-delivery-networks.md)

[test łączności Microsoft 365](https://aka.ms/netonboard)

[Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[blog sieci Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
