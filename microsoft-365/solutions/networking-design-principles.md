---
title: Tworzenie sieci (do chmury) — widok jednego z architektów
description: Dowiedz się, jak zoptymalizować sieć pod kątem łączności z chmurą, unikając najbardziej typowych problemów.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 519f3035040f563a6f3663198be3952830cb21cb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983568"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Tworzenie sieci (do chmury) — widok jednego z architektów

W tym artykule [Ed Fisher](https://www.linkedin.com/in/edfisher/), security & Compliance Architect w firmie Microsoft, opisano sposób optymalizowania sieci pod kątem łączności z chmurą przez unikanie najbardziej typowych problemów. 

## <a name="about-the-author"></a>Informacje o autorze

![Zdjęcie Eda Fishera.](../media/solutions-architecture-center/ed-fisher-networking.jpg) 

Obecnie jestem głównym specjalistą ds. technicznych w naszym zespole ds. sprzedaży detalicznej i produktów konsumenckich i skupiam się na zabezpieczeniach & zgodności. Przez ostatnich dziesięć lat pracowałem z Office 365 do firmy. Pracowałem w mniejszych sklepach z wieloma lokalizacjami dla instytucji rządowych i przedsiębiorstw, w których są miliony użytkowników na całym świecie, a także wielu innych klientów między nimi. Większość ma dziesiątki tysięcy użytkowników, wiele lokalizacji w różnych częściach świata, potrzebę wyższego poziomu zabezpieczeń i różnorodne wymagania dotyczące zgodności z przepisami. Pomogły mi setki przedsiębiorstw i miliony użytkowników bezpiecznie przeszły do chmury.

W tle z ostatnich 25 lat, które obejmuje zabezpieczenia, infrastrukturę i inżynierię sieci, i po przenieść dwóch moich poprzednich pracodawców do firmy Office 365 przed dołączeniem do firmy Microsoft, jestem po twojej stronie dużo czasu i pamiętam, jak to wygląda. Chociaż żaden z dwóch klientów nie jest zawsze taki sam, większość ma podobne potrzeby, a podczas korzystania ze standardowej usługi, takiej jak dowolna platforma SaaS lub PaaS, najlepsze metody zwykle są takie same.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>To nie jest sieć — tak właśnie (źle)korzystasz z tej sieci!

Niezależnie od tego, ile razy tak się dzieje, nigdy nie przeodziło mnie, jak kreatywne zespoły zabezpieczeń i zespoły sieciowe próbują uzyskać informacje o tym, jak powinny łączyć się z usługami firmy Microsoft w chmurze. Zawsze istnieją pewne zasady zabezpieczeń, standardy zgodności lub lepszy sposób ich wykorzystania, bez konieczności angażowania się w konwersację na temat tego, co chcą osiągnąć, oraz o tym, jak są  lepsze, łatwiejsze, bardziej ekonomiczne i bardziej wydajne sposoby wykonywania tych czynności. 

Gdy ten rodzaj rzeczy zostanie eskalowany do mnie, zwykle chętnie zechcę zmierzyć się z wyzwaniem i przejść przez te eskalację i przyczyny, a następnie przejść do miejsca, w którym muszą się znaleźć. Ale jeśli mam dosyć wyzrównywny zamiar, muszę się dzielić, że czasami po prostu zechcę, żeby zrobili to, co będą, i odwrócę to, co ci mówię, gdy w końcu zostaną zwęsieni, że to nie zadziała. Czasami może mi się to podobać, ale *nie muszę robić tego chętnie*. Spróbuję wyjaśnić wszystkie te informacje, które dołączę w tym wpisie. Niezależnie od Twojej roli, jeśli Twoja organizacja chce korzystać z usług firmy Microsoft w chmurze, prawdopodobnie jest pewien sedno, co może w tym pomóc.

## <a name="guiding-principles"></a>Zasady wytycznych

Zacznijmy od kilku reguł lądowych dotyczących tego, co tutaj robisz. Omawiamy sposób bezpiecznego łączenia się z usługami w chmurze w celu zapewnienia minimalnej złożoności i maksymalnej wydajności przy zachowaniu rzeczywistych zabezpieczeń. Żadna z tych czynności nie jest przeciwna do żadnego z tych, nawet jeśli Ani Ty, ani Twój klient, nie będziecie w ogóle korzystać z ulubionego serwera proxy.

- **To, że możesz,** nie oznacza, że należy: Lub o parafrazę Dr. Ian Malcolm z filmu Park Jurassic "... Tak, tak, ale zespół zabezpieczeń był tak często zajęty tym, czy nie, czy mógłby, że nie są już na myśli, czy powinien".
- **Bezpieczeństwo nie oznacza złożoności**: nie jest bezpieczniejsze tylko dlatego, że wydajesz więcej pieniędzy, przekieruj się przez więcej urządzeń lub klikaj więcej przycisków.
- **Office 365 jest dostępne przez Internet**: Ale to nie to samo, co Office 365 to Internet. Jest to usługa SaaS zarządzana przez firmę Microsoft i zarządzana przez Ciebie. W przeciwieństwie do witryn internetowych odwiedzanych w Internecie, faktycznie można zaglądać za zasłony i stosować kontrolki potrzebne do spełnienia określonych zasad i standardów zgodności, o ile tylko rozumiesz, że chociaż możesz zdącić z realizacji swoich celów, może być konieczne po prostu wykonać je w inny sposób.
- **Chokepoints are bad, localized breakouts are good**: Everybody always wants to backhaul all their Internet traffic for all their users to some central point, usually so they can monitor it and enforce policy, but often because it's taniej niż inicjowanie dostępu do Internetu we wszystkich swoich lokalizacjach lub po prostu jak to zrobić. Ale te chokepoints są dokładnie takie... punkty, w których ruch drogowy się zatłacza. Nie ma nic złego w uniemożliwienia użytkownikom przeglądania internetu do witryny Sieci Web lub przesyłania strumieniowego filmów o kotach, ale ruch aplikacji biznesowych o krytycznym znaczeniu nie jest tak samo traktujący.
- Jeśli system DNS nie jest zadowolone **,** nie ma nic szczęśliwego: najlepiej zaprojektowana sieć może być bez problemu ze strony słabego systemu DNS, na przykład przez rekurencję żądań do serwerów w innych obszarach na świecie lub korzystanie z serwerów DNS Twojego dostawcy usług internetowych lub innych publicznych serwerów DNS, które buforuje informacje o rozdzielczości DNS.
- **Nie oznacza** to, że właśnie tak właśnie było, ale nie oznacza to, że należy zrobić to teraz: Technologia stale się zmienia i Office 365 nie jest wyjątkiem. Stosowanie zabezpieczeń, które zostały opracowane i wdrożone dla usług lokalnych lub do sterowania przeglądaniem w sieci Web, nie zapewni tego samego poziomu ochrony zabezpieczeń i może mieć istotny negatywny wpływ na wydajność.
- **Office 365 można uzyskać do niego dostęp przez Internet**. To wszystko w skrócie. Niezależnie od tego, co chcesz zrobić między użytkownikami a twoją krawędzią, ruch nadal przechodzi przez Internet, gdy opuści sieć i zanim trafi do naszego. Nawet jeśli używasz usługi Azure ExpressRoute do rozsyłania ruchu z sieci, w przypadku których są one poufne dla niektórych opóźnień, bezpośrednio do naszej sieci, wymagana jest łączność internetowa. Zaakceptuj go. Nie domyśl się, jak to działa.

## <a name="where-bad-choices-are-often-made"></a>Gdzie często dokonywane są złe wybory

Istnieje wiele miejsc, w których w nazwie zabezpieczeń są podejmowane złe decyzje, jednak najczęściej spotykam się z klientami. Wiele konwersacji z klientami obejmuje wszystkie te konwersacje jednocześnie.

### <a name="insufficient-resources-at-the-edge"></a>Za mało zasobów na krawędzi

Bardzo mało klientów wdraża środowiska w środowisku zielonym i mają wiele lat doświadczenia w niczym, jak działają ich użytkownicy i jak wygląda ich internetowy ruch wychodzący. Niezależnie od tego, czy klienci mają serwery proxy, czy zezwalają na bezpośredni dostęp i po prostu ruch wychodzący przy użyciu NAT, od wielu lat robią to i nie zastanawiają się nad tym, o ile więcej będą rozpoczynać przechodzenie przez ich granice podczas przenoszenia tradycyjnych aplikacji wewnętrznych do chmury.

Przepustowość jest zawsze problemem, ale urządzenia NAT mogą nie mieć wystarczającej mocy konia, aby obsłużyć zwiększone obciążenie, i mogą zacząć bezuchocznie zamykać połączenia w celu wolnych zasobów. Większość oprogramowania klienckiego, które łączy się z usługą Office 365 oczekuje połączeń trwałych, a użytkownik w pełni Office 365 może mieć co najmniej 32 jednoczesne połączenia. Jeśli urządzenie NAT je upuściło, te aplikacje mogą przestać odpowiadać w razie próby użycia połączeń, których już tam nie ma. Gdy poddają się oni i próbują nawiązać nowe połączenia, nałożyli jeszcze więcej obciążenia na Twój sprzęt sieciowy.

### <a name="localized-breakout"></a>Zlokalizowany podział

Wszystko inne na tej liście sprowadza się do jednej rzeczy — jak najszybciej wymykasz się z sieci do naszej. Powrót ruchu użytkowników do centralnego punktu ruchu wychodzącego, zwłaszcza gdy ten punkt ruchu wychodzącego znajduje się w innym regionie niż ten, w którym znajdują się użytkownicy, wprowadza niepotrzebne opóźnienia i wpływa zarówno na środowisko klienta, jak i szybkości pobierania. Firma Microsoft ma punkty obecności na całym świecie z przodu dla wszystkich naszych usług i komunikacji równorzędnej ustanowionej z niemal wszystkimi głównymi usługami sieciowym, dlatego rozsyłanie ruchu użytkowników lokalnie zapewnia szybki dostęp do naszej sieci z minimalnymi opóźnieniami.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>Ruch rozpoznawania nazw DNS powinien podążać ścieżką internetowego ruchu wychodzącego

Oczywiście aby klient znalazł dowolny punkt końcowy, musi użyć systemu DNS. Serwery DNS firmy Microsoft oceniają źródło żądań DNS, aby upewnić się, że zwracamy odpowiedź, która w terminach internetowych jest najbliżej źródła żądania. Upewnij się, że system DNS jest skonfigurowany tak, aby żądania rozpoznawania nazw wychodzące w ten sam sposób co ruch użytkowników, aby nie zapewniały ich lokalnego punktu wychodzącego, ale do punktu końcowego w innym regionie. Oznacza to możliwość "zmieściania się lokalnych serwerów DNS do katalogu głównego" zamiast przesyłania dalej na serwery DNS w zdalnych centrach danych. Zwracaj uwagę na publiczne i prywatne usługi DNS, które mogą buforować wyniki z jednej części świata i obsługiwać je do żądań z innych części świata.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Do serwera proxy lub nie do serwera proxy, czyli pytanie

Jedną z pierwszych rzeczy do rozważenia jest to, czy połączenia użytkowników serwera proxy z siecią Office 365. To proste. nie serwera proxy. Office 365 jest dostępna za pośrednictwem Internetu, ale nie jest to Internet. Jest to rozszerzenie Twoich podstawowych usług i należy je traktować jako takie. Wszystko, co może chcieć zrobić serwer proxy, na przykład ochrona przed złośliwym kodem lub inspekcją zawartości, jest już dostępne w usłudze i można z niego korzystać w skali bez konieczności pękania połączeń zaszyfrowanych przez szyfrowanie TLS. Jeśli jednak naprawdę chcesz używać ruchu serwera proxy, którego nie możesz kontrolować w inny sposób, [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) zwróć uwagę na nasze wskazówki podpowiedni i kategorie ruchu na stronie [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md). Dostępne są trzy kategorie ruchu dla Office 365. Oprogramowanie Optimize (Optymalizuj) i Allow (Zezwalaj) powinno naprawdę kierować i pomijać serwer proxy. Domyślny może być proxied. Szczegóły znajdują się w tych edycie... można je przeczytać.

Większość klientów, którzy skonfiskują się przy użyciu serwera proxy, kiedy faktycznie przyjrzyją się temu, co robią, uświadomią sobie, że gdy klient wysyła żądanie HTTP CONNECT do serwera proxy, ten serwer proxy jest teraz po prostu kosztownym dodatkowym routerem. Używane protokoły, takie jak MAPI i RTC, nie są nawet protokołami zrozumiałymi dla serwerów proxy sieci Web, więc nawet w przypadku pękania protokołu TLS nie masz żadnych dodatkowych zabezpieczeń. Masz *dodatkowe* opóźnienie. Zobacz [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) więcej na ten temat, w tym kategorie Optymalizuj, Zezwalaj i Domyślne dla Microsoft 365 ruchu.

Na koniec przejmij ogólny wpływ na serwer proxy i odpowiadającą mu odpowiedź na jego ocenę. W związku z tym, że za pośrednictwem serwera proxy jest większej liczby połączeń, współczynnik skali protokołu TCP może się zmniejszyć, dzięki czemu nie trzeba buforować tak dużej liczby ruchu. Znam klientów, którzy byli tak przeciążeni, że używali współczynnika skali 0. Ponieważ scale Factor jest wartością wykładniczą i chcemy użyć liczby 8, każda zmniejszenie wartości scale Factor ma ogromny negatywny wpływ na przepływność.

Inspekcja TLS oznacza zabezpieczenia! Ale nie naprawdę! Wielu klientów korzystających z serwerów proxy chce przeprowadzać inspekcje całego ruchu, co oznacza "przerwę i inspekcję". W przypadku witryny internetowej dostępnej za pośrednictwem protokołu HTTPS (bez względu na ochronę prywatności) serwer proxy może musi to zrobić przez 10 lub nawet 20 jednoczesnych strumieni przez kilkaset milisekund. W przypadku dużego pobierania pliku wideo lub połączenia wideo co najmniej jedno z tych połączeń może trwać znacznie dłużej, ale w większości z tych połączeń można nawiązywać, przenosić i zamykać bardzo szybko. Wykonanie przerwy i inspekcji oznacza, że serwer proxy musi wykonać dwukrotnie pracę. Dla każdego połączenia z klienta do serwera proxy musi również nawiązaniu oddzielnego połączenia z punktem końcowym. Więc 1 staje się 2, 2 staje się 4, 32 staje się 64...see where I'm going? Prawdopodobnie rozmiar rozwiązania serwera proxy jest drobnym rozwiązaniem do typowego przeglądania w sieci Web, ale gdy próbujesz wykonać tę samą wartość dla połączeń klienta z programem Office 365, liczba jednoczesnych, długotrwałych połączeń może być o wielkość większa niż wielkość.

### <a name="streaming-isnt-important-except-that-it-is"></a>Przesyłanie strumieniowe jest nie ważne, z *tym że jest*

Jedyne usługi w p Office 365 udp są Skype (wkrótce zostaną wycofane) i Microsoft Teams. Teams UDP jest używany do przesyłania strumieniowego ruchu, w tym do udostępniania dźwięku, wideo i prezentacji. Przesyłanie strumieniowe ruchu jest dostępne na żywo, na przykład podczas spotkania online za pomocą głosu, wideo i prezentacji albo pokazów. Korzystają one z protokołu UDP, ponieważ w przypadku upuszczenia pakietów lub rozsyłania ich poza kolejność jest on niewygodny dla użytkownika i może po prostu przejść dalej.

Jeśli nie zezwalasz na ruch wychodzący UDP z klientów do usługi, mogą oni wrócić do korzystania z protokołu TCP. Jednak w przypadku upuszczenia pakietu TCP  wszystko zatrzymuje się do momentu wygaśnięcia limitu czasu ponownej transmisji (RTO) i można ponownie przetłumaczyć brakujący pakiet. Jeśli pakiety pojawią się poza kolejnością, wszystko zatrzymuje się do momentu natrętnych innych pakietów i może zostać ponownie zszeparowany. Oba prowadzą do percepcji w dźwięku (pamiętasz Max Headroom?) i wideo (czy kliknięto coś... Niestety, nie jest to możliwe) i prowadzi do niskiej wydajności i słabego działania użytkownika. I pamiętasz, co umieścić powyżej na temat serwerów proxy? Wymuszanie używania Teams proxy przez klienta sieciOwego wymusza użycie protokołu TCP. Teraz dwa razy powodujesz negatywny wpływ na wydajność.

### <a name="split-tunneling-may-seem-scary"></a>Podziały na wcłęcie mogą wydawać się groźne

Ale nie jest. Wszystkie połączenia z siecią Office 365 są za pośrednictwem TLS. Od dłuższego czasu oferowaliśmy usługę TLS 1.2 i wkrótce wyłączymy starsze wersje, ponieważ starsi klienci nadal z nich korzystają, co stanowi ryzyko.

Wymuś połączenie TLS lub 32 z nich, aby korzystać z połączenia VPN, zanim przejdą do usługi, nie dodają zabezpieczeń. Powoduje dodawanie opóźnień i zmniejsza ogólną przepływność. W niektórych rozwiązaniach VPN wymusza to nawet na wyekspowywowanie protokołu TCP przez protokół UDP, co znowu będzie miało bardzo negatywny wpływ na przesyłanie strumieniowe ruchu. Poza tym, o ile nie jest to inspekcja TLS, nie ma żadnych rzeczy do góry nogami. Często spotykanym wśród klientów motywem, ponieważ większość ich pracowników korzysta zdalnie, jest to, że widzą istotne problemy z przepustowością i wydajnością w nawiązywaniu połączeń przez wszystkich użytkowników za pomocą sieci VPN, zamiast konfigurowania rozdzielania na potrzeby dostępu do optymalizowania kategorii [Office 365](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) punktów końcowych.

To łatwe rozwiązanie do podziału na rozdzielanie i takie, które należy zrobić. Aby uzyskać więcej informacji, zapoznaj się z tematem [Optymalizowanie Office 365 dla użytkowników zdalnych korzystających z rozdzielania sieci VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="the-sins-of-the-past"></a>Sins przeszłości

Często przyczyną złych wyborów są połączenia (1) nieuwienia, jak działa usługa, (2) próby spełnienia firmowych zasad, które zostały napisane przed zaadoptowanie chmury, oraz (3) zespołów zabezpieczeń, które mogą nie zostać łatwo przekonane, że istnieje więcej niż jeden sposób realizacji ich celów. Mamy nadzieję, że powyższe linki i poniższe linki pomogą w pierwszym. Sponsorowanie kierownictwa może być wymagane, aby zaszły drugie. Adresowanie celów zasad zabezpieczeń, a nie ich metod, pomaga w trzeciej. Od dostępu warunkowego do moderowania zawartości, ochrony przed zasadami dotyczącymi zawartości, przez ochronę informacji, sprawdzanie poprawności punktu końcowego do zagrożeń 0-dniowych — każdy cel końcowy może być zrealizowany przy użyciu tego, co jest dostępne w programie Office 365, i bez żadnej zależności od lokalnego koła zębatego sieciowego, wymuszonych samolotów sieci VPN oraz przerwy i inspekcji usługi TLS.

W innych czasach sprzęt, który był do rozmiarem i zakupiony przed rozpoczęciem przenoszenia się organizacji do chmury, po prostu nie można skalować do obsługi nowych wzorców ruchu i ładowania. Jeśli naprawdę musisz rozsyłać cały ruch przez pojedynczy punkt ruchu wychodzącego i/lub serwer proxy, przygotuj się do odpowiedniego uaktualnienia wyposażenia sieciowego i przepustowości. Starannie monitoruj użycie obu tych narzędzi, ponieważ środowisko nie będzie się stopniowo zmniejszać w przypadku dosyć większej liczby użytkowników. Wszystko będzie w porządku do momentu, aż punkt napięcie zostanie osiągnięty, co spowoduje, że wszyscy zostaną ponisku.

## <a name="exceptions-to-the-rules"></a>Wyjątki od reguł

Jeśli Twoja organizacja wymaga ograniczeń [dzierżawy,](/azure/active-directory/manage-apps/tenant-restrictions) musisz użyć serwera proxy z przerwą I inspekcją usługi TLS, aby wymusić część ruchu przez serwer proxy, ale nie musisz wymuszać całego ruchu przez ten serwer.  To nie wszystko lub nic, więc zwróć uwagę na to, co musi zostać zmodyfikowane przez serwer proxy.

Jeśli zamierzasz zezwolić na rozdzielanie połączeń rozdzielanych, ale używać serwera proxy do ogólnego ruchu internetowego, upewnij się, że plik PAC definiuje, co ma być bezpośrednie, oraz sposób zdefiniowania interesującego ruchu dla ruchu przechodzącego przez sieć VPN. Oferujemy przykładowe pliki [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) PAC, które ułatwią zarządzanie nimi.

## <a name="conclusion"></a>Wnioski

Dziesiątki tysięcy organizacji, w tym prawie wszystkie listy Fortune 500, używają codziennie Office 365 do kluczowych funkcji. Robi to bezpiecznie przez Internet.

Niezależnie od posiadanych celów zabezpieczeń można je osiągnąć tak szybko, jak to możliwe, aby nie wymagać połączeń VPN, serwerów proxy, przerw i inspekcji usługi TLS ani scentralizowanego ruchu wychodzącego do Internetu w celu jak najszybciej wyłączenia ruchu twoich użytkowników z sieci i do naszego, co zapewnia najlepszą wydajność, niezależnie od tego, czy Sieć jest siedzibą główną firmy.  w biurze zdalnym lub u tego użytkownika pracującego w domu. Nasze wskazówki są oparte na tym, jak są Office 365 usługi oraz zapewniają bezpieczne i performantowe środowisko użytkownika.

## <a name="further-reading"></a>Dalsze czytanie

[Zasady Office 365 łączności sieciowej](../enterprise/microsoft-365-network-connectivity-principles.md)

[Adresy URL i zakresy adresów IP usługi Office 365](../enterprise/urls-and-ip-address-ranges.md)

[Zarządzanie Office 365 punktami końcowymi](../enterprise/managing-office-365-endpoints.md)

[Office 365 adresu IP i usługi sieci Web adresu URL](../enterprise/microsoft-365-ip-web-service.md)

[Ocena Office 365 sieci](../enterprise/assessing-network-connectivity.md)

[Office 365 sieci i dostosowywania wydajności](../enterprise/network-planning-and-performance.md)

[Ocena Office 365 sieci](../enterprise/assessing-network-connectivity.md)

[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](../enterprise/performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością Office 365](../enterprise/performance-troubleshooting-plan.md)

[Sieci dostarczania zawartości](../enterprise/content-delivery-networks.md)

[Microsoft 365 test łączności](https://connectivity.office.com/)

[Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 blog sieciowy](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 dla użytkowników zdalnych korzystających z rozdzielania sieci VPN](../enterprise/microsoft-365-vpn-split-tunnel.md)
