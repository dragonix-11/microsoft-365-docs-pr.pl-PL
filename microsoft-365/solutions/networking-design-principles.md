---
title: Sieć w górę (do chmury) — punkt widzenia jednego architekta
description: Dowiedz się, jak zoptymalizować sieć pod kątem łączności w chmurze, unikając najczęstszych pułapek.
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
ms.openlocfilehash: 5f90e4616edd3534baefd64bba5a2eec640f6366
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823943"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Sieć w górę (do chmury) — punkt widzenia jednego architekta

W tym artykule [Ed Fisher](https://www.linkedin.com/in/edfisher/), architekt zgodności & zabezpieczeń w firmie Microsoft, opisuje sposób optymalizowania sieci pod kątem łączności w chmurze, unikając najczęstszych pułapek.

## <a name="about-the-author"></a>Informacje o autorze

![Ed Fisher zdjęcie.](../media/solutions-architecture-center/ed-fisher-networking.jpg)

Obecnie jestem głównym specjalistą technicznym w naszym zespole ds. handlu detalicznego i dóbr konsumpcyjnych, koncentrując się na zgodności & zabezpieczeń. Przez ostatnie dziesięć lat pracowałem z klientami przenoszącymi się do Office 365. Pracowałem z mniejszymi sklepami z kilkoma lokalizacjami dla agencji rządowych i przedsiębiorstw z milionami użytkowników rozproszonych na całym świecie, a wielu innych klientów pomiędzy nimi, z większością mającą dziesiątki tysięcy użytkowników, wiele lokalizacji w różnych częściach świata, potrzebę wyższego stopnia bezpieczeństwa i wiele wymagań dotyczących zgodności. Pomogłem setkom przedsiębiorstw i milionom użytkowników bezpiecznie i bezpiecznie przenieść się do chmury.

Mając doświadczenie w ciągu ostatnich 25 lat, które obejmuje bezpieczeństwo, infrastrukturę i inżynierię sieci, i po przeniesieniu dwóch moich poprzednich pracodawców do Office 365 przed dołączeniem do firmy Microsoft, byłem po twojej stronie tabeli wiele razy i pamiętam, jak to jest. Chociaż żaden z dwóch klientów nie jest taki sam, większość z nich ma podobne potrzeby, a w przypadku korzystania ze standardowej usługi, takiej jak każda platforma SaaS lub PaaS, najlepsze podejścia wydają się być takie same.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>To nie jest sieć — w ten sposób (mis) używasz jej!

Bez względu na to, ile razy tak się dzieje, nigdy nie zadziwia mnie, jak *kreatywne* zespoły ds. zabezpieczeń i zespoły sieciowe próbują uzyskać informacje o tym, jak ich zdaniem powinny łączyć się z usługami w chmurze firmy Microsoft. Zawsze istnieją pewne zasady zabezpieczeń, standard zgodności lub lepszy sposób, w jaki nalegają, bez chęci angażowania się w rozmowę na temat tego, co próbują osiągnąć, lub *jak* istnieją lepsze, łatwiejsze, bardziej ekonomiczne i bardziej wydajne sposoby tego działania.

Kiedy tego rodzaju rzeczy są eskalowane do mnie, zwykle jestem gotów podjąć wyzwanie i przejść je przez hows i whys i dostać je tam, gdzie muszą być. Ale jeśli jestem całkowicie szczery, muszę podzielić się tym, że czasami chcę po prostu pozwolić im robić to, co będą, i wrócić, aby powiedzieć, że powiedziałem ci tak, kiedy w końcu przyznać, że nie działa. Może chcę to zrobić czasami, ale *nie*. To, co robię, to spróbować wyjaśnić wszystko, co mam zamiar uwzględnić w tym poście. Niezależnie od twojej roli, jeśli organizacja chce korzystać z usług firmy Microsoft w chmurze, prawdopodobnie istnieje pewna mądrość w następujących kwestiach, które mogą Ci pomóc.

## <a name="guiding-principles"></a>Przewodnie

Zacznijmy od pewnych zasad dotyczących tego, co robimy tutaj. Omawiamy sposób bezpiecznego łączenia się z usługami w chmurze w celu zapewnienia minimalnej złożoności i maksymalnej wydajności przy zachowaniu rzeczywistych zabezpieczeń. Żaden z poniższych elementów nie jest sprzeczny z żadnym z tych warunków, nawet jeśli ty lub twój klient nie będziesz używać ulubionego serwera proxy do wszystkiego.

- **Tylko dlatego, że można, nie oznacza, że należy**: Lub parafrazując dr Ian Malcolm z filmu Jurassic Park "... Yeah, yeah, ale twój zespół bezpieczeństwa był tak zajęty, czy mogą, że nie przestali myśleć, czy powinni."
- **Bezpieczeństwo nie oznacza złożoności**: nie jesteś bardziej bezpieczny tylko dlatego, że wydajesz więcej pieniędzy, kierujesz się przez więcej urządzeń lub klikasz więcej przycisków.
- **Office 365 jest dostępny przez Internet**: Ale to nie to samo, co Office 365 jest Internetem. Jest to usługa SaaS zarządzana przez firmę Microsoft i administrowana przez Ciebie. W przeciwieństwie do witryn internetowych, które odwiedzasz w Internecie, rzeczywiście możesz zajrzeć za zasłonę i możesz zastosować mechanizmy kontroli potrzebne do spełnienia swoich zasad i standardów zgodności, o ile rozumiesz, że chociaż możesz osiągnąć swoje cele, możesz po prostu zrobić to w inny sposób.
- **Chokepoints są złe, zlokalizowane wyprysków są dobre**: Każdy zawsze chce backhaul cały swój ruch internetowy dla wszystkich swoich użytkowników do pewnego centralnego punktu, zwykle tak, aby mogli go monitorować i wymuszać zasady, ale często dlatego, że jest to albo tańsze niż aprowizowanie dostępu do Internetu we wszystkich swoich lokalizacjach, lub to tylko jak to robią. Ale te chokepoints są dokładnie, że ... punktów, w których ruch jest zadławiony. Nie ma nic złego w uniemożliwianiu użytkownikom przeglądania na Instagramie lub przesyłania strumieniowego filmów z kotami, ale nie traktuj ruchu aplikacji biznesowych o znaczeniu krytycznym w ten sam sposób.
- **Jeśli system DNS nie jest zadowolony, nie jest to nic szczęśliwego**: Najlepiej zaprojektowana sieć może być hamowana przez słabą usługę DNS, niezależnie od tego, czy jest to poprzez ponowne uruchamianie żądań do serwerów w innych obszarach świata, czy przy użyciu serwerów DNS usługodawcy sieciowego lub innych publicznych serwerów DNS, które buforują informacje o rozpoznawaniu nazw DNS.
- **Tylko dlatego, że tak było kiedyś, nie oznacza to, że tak powinno być teraz**: Technologia ciągle się zmienia, a Office 365 nie jest wyjątkiem. Stosowanie środków bezpieczeństwa, które zostały opracowane i wdrożone dla usług lokalnych lub do kontrolowania przeglądania internetu, nie zapewni takiego samego poziomu bezpieczeństwa i może mieć znaczący negatywny wpływ na wydajność.
- **Office 365 został zbudowany, aby uzyskać dostęp przez Internet**: To jest to w skrócie. Niezależnie od tego, co chcesz zrobić między użytkownikami a twoją krawędzią, ruch nadal przechodzi przez Internet po opuszczeniu sieci i zanim trafi do naszej sieci. Nawet jeśli używasz usługi Azure ExpressRoute do kierowania pewnego ruchu wrażliwego na opóźnienia z sieci bezpośrednio do naszej sieci, łączność z Internetem jest absolutnie wymagana. Zaakceptuj to. Nie przesadzaj.

## <a name="where-bad-choices-are-often-made"></a>Gdzie często dokonuje się złych wyborów

Chociaż istnieje wiele miejsc, gdzie złe decyzje są podejmowane w imię bezpieczeństwa, są to te, które spotykam najczęściej z klientami. Wiele konwersacji z klientami obejmuje wszystkie te czynności jednocześnie.

### <a name="insufficient-resources-at-the-edge"></a>Niewystarczające zasoby na brzegu

Bardzo niewielu klientów wdraża środowiska greenfield i ma wieloletnie doświadczenie z tym, jak działają ich użytkownicy i jak wygląda ich ruch wychodzący z Internetu. Niezależnie od tego, czy klienci mają serwery proxy, czy zezwalają na bezpośredni dostęp i po prostu ruch wychodzący NAT, robią to od lat i nie zastanawiają się, o ile więcej zaczną pompować przez swoją krawędź, gdy przenoszą tradycyjnie aplikacje wewnętrzne do chmury.

Przepustowość jest zawsze problemem, ale urządzenia NAT mogą nie mieć wystarczającej mocy do obsługi zwiększonego obciążenia i mogą rozpocząć przedwczesne zamykanie połączeń w celu zwolnienia zasobów. Większość oprogramowania klienckiego łączącego się z Office 365 oczekuje trwałych połączeń, a użytkownik w pełni korzystający z Office 365 może mieć co najmniej 32 połączenia współbieżne. Jeśli urządzenie NAT porzuca je przedwcześnie, te aplikacje mogą przestać odpowiadać, ponieważ próbują korzystać z połączeń, których już nie ma. Kiedy rezydują i próbują nawiązać nowe połączenia, jeszcze bardziej obciążają twój sprzęt sieciowy.

### <a name="localized-breakout"></a>Zlokalizowany wyprysk

Wszystko inne na tej liście sprowadza się do jednej rzeczy — wysiadania z sieci i do naszej tak szybko, jak to możliwe. Zawrócenie ruchu użytkowników do centralnego punktu ruchu wychodzącego, zwłaszcza gdy ten punkt ruchu wychodzącego znajduje się w innym regionie niż użytkownicy, wprowadza niepotrzebne opóźnienia i wpływa zarówno na środowisko klienta, jak i szybkość pobierania. Firma Microsoft ma punkty obecności na całym świecie z frontonami dla wszystkich naszych usług i komunikacji równorzędnej ustanowionej z praktycznie każdym głównym usługodawcą isp, więc routing ruchu użytkowników *lokalnie* zapewnia szybkie dostanie się do naszej sieci z minimalnym opóźnieniem.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>Ruch rozpoznawania nazw DNS powinien być zgodny ze ścieżką internetowego ruchu wychodzącego

Oczywiście, aby klient znalazł dowolny punkt końcowy, musi użyć systemu DNS. Serwery DNS firmy Microsoft oceniają źródło żądań DNS, aby upewnić się, że zwracamy odpowiedź, która w kategoriach internetowych jest najbliższa źródle żądania. Upewnij się, że system DNS jest skonfigurowany tak, aby żądania rozpoznawania nazw wychodziły tą samą ścieżką co ruch użytkowników, aby nie przekazywać im lokalnego ruchu wychodzącego, ale do punktu końcowego w innym regionie. Oznacza to, że lokalne serwery DNS "przechodzą do katalogu głównego", zamiast przekazywać je do serwerów DNS w zdalnych centrach danych. I uważaj na publiczne i prywatne usługi DNS, które mogą buforować wyniki z jednej części świata i służyć im do żądań z innych części świata.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Do serwera proxy lub nie do serwera proxy, to jest pytanie

Jedną z pierwszych kwestii, które należy wziąć pod uwagę, jest to, czy połączenia użytkowników proxy z Office 365. To proste; nie serwer proxy. Office 365 jest uzyskiwany przez Internet, ale nie jest to Internet. Jest to rozszerzenie podstawowych usług i powinno być traktowane jako takie. Wszystko, co chcesz zrobić serwer proxy, taki jak DLP, oprogramowanie chroniące przed złośliwym kodem lub inspekcja zawartości, jest już dostępne w usłudze i może być używane na dużą skalę i bez konieczności trząsania połączeń zaszyfrowanych za pomocą protokołu TLS. Ale jeśli naprawdę chcesz, aby ruch proxy, który nie może inaczej kontrolować, zwróć uwagę na nasze wskazówki i [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) kategorie ruchu w .[https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) Mamy trzy kategorie ruchu dla Office 365. Optymalizuj i zezwalaj naprawdę powinien przejść bezpośrednio i pominąć serwer proxy. Wartość domyślna może być zbliżona. Szczegóły znajdują się w tych dokumentach... odczytać je.

Większość klientów, którzy nalegają na korzystanie z serwera proxy, gdy faktycznie patrzą na to, co robią, zdaje sobie sprawę, że gdy klient wysyła żądanie HTTP CONNECT do serwera proxy, serwer proxy jest teraz po prostu kosztownym dodatkowym routerem. Używane protokoły, takie jak MAPI i RTC, nie są nawet protokołami zrozumiałymi dla serwerów proxy sieci Web, więc nawet w przypadku łamania protokołu TLS nie otrzymujesz żadnych dodatkowych zabezpieczeń. *Otrzymujesz* dodatkowe opóźnienie. Zobacz, aby uzyskać [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) więcej informacji na ten temat, w tym kategorie Optymalizacja, Zezwalaj i Domyślne dla ruchu Microsoft 365.

Na koniec należy wziąć pod uwagę ogólny wpływ na serwer proxy i odpowiadającą mu odpowiedź, aby poradzić sobie z tym wpływem. W miarę jak coraz więcej połączeń jest nawiązywanych za pośrednictwem serwera proxy, może zmniejszyć współczynnik skalowania TCP, aby nie musiał buforować tak dużego ruchu. Widziałem klientów, w których ich serwery proxy były tak przeciążone, że korzystali ze współczynnika skalowania 0. Ponieważ współczynnik skalowania jest wartością wykładniczą i chcemy użyć wartości 8, każde zmniejszenie wartości współczynnika skalowania ma ogromny negatywny wpływ na przepływność.

Inspekcja protokołu TLS oznacza ZABEZPIECZENIA! Ale nie do końca! Wielu klientów z serwerami proxy chce ich używać do sprawdzania całego ruchu, a to oznacza, że protokół TLS "przerywa i sprawdza". W przypadku witryny internetowej dostępnej za pośrednictwem protokołu HTTPS (niezależnie od kwestii prywatności) serwer proxy może wymagać wykonania tej operacji dla 10 lub nawet 20 równoczesnych strumieni przez kilkaset milisekund. Jeśli jest duży plik do pobrania, a może film wideo, co najmniej jedno z tych połączeń może trwać znacznie dłużej, ale ogólnie rzecz biorąc, większość z tych połączeń nawiązuje, przesyła i zamyka bardzo szybko. Wykonanie przerwy i inspekcji oznacza, że serwer proxy musi wykonać podwójną pracę. Dla każdego połączenia klienta z serwerem proxy serwer proxy musi również nawiązać oddzielne połączenie z punktem końcowym. Tak więc, 1 staje się 2, 2 staje się 4, 32 staje się 64...zobacz, dokąd idę? Prawdopodobnie rozmiar rozwiązania serwera proxy dobrze dla typowych web surfing, ale gdy próbujesz zrobić to samo dla połączeń klienta z Office 365, liczba równoczesnych, długotrwałych połączeń może być rzędy wielkości większe niż rozmiar.

### <a name="streaming-isnt-important-except-that-it-is"></a>Przesyłanie strumieniowe nie jest ważne, z tą różnicą, że *jest*

Jedyne usługi w Office 365 korzystające z protokołu UDP są Skype (wkrótce zostaną wycofane) i Microsoft Teams. Teams używa protokołu UDP do przesyłania strumieniowego ruchu, w tym udostępniania dźwięku, wideo i prezentacji. Ruch przesyłany strumieniowo jest na żywo, na przykład podczas spotkania online z głosem, wideo i prezentacją decków lub pokazami. Używają one protokołu UDP, ponieważ jeśli pakiety zostaną porzucone lub zostaną usunięte z porządku, użytkownik praktycznie nie będzie mógł tego zrobić, a strumień może po prostu kontynuować.

Jeśli nie zezwolisz na wychodzący ruch UDP z klientów do usługi, mogą one wrócić do korzystania z protokołu TCP. Jeśli jednak pakiet TCP zostanie porzucony, *wszystko zostanie zatrzymane* do momentu wygaśnięcia limitu czasu retransmisji (RTO) i ponownego przetranstransmisji brakującego pakietu. Jeśli pakiet jest w porządku, wszystko zatrzymuje się do momentu odebrania innych pakietów i może zostać ponownie zmontowane w kolejności. Oba prowadzą do zauważalnych usterek w dźwięku (pamiętasz Max Headroom?) i wideo (czy coś kliknąłeś... oh, tam jest) i prowadzić do niskiej wydajności i złe środowisko użytkownika. I pamiętaj, co postawiłem powyżej o proxy? Gdy wymusisz użycie serwera proxy przez klienta Teams, wymusisz użycie protokołu TCP. Teraz więc dwukrotnie powodujesz negatywny wpływ na wydajność.

### <a name="split-tunneling-may-seem-scary"></a>Tunelowanie podzielone może wydawać się przerażające

Ale tak nie jest. Wszystkie połączenia z Office 365 są za pośrednictwem protokołu TLS. Od dłuższego czasu oferujemy protokół TLS 1.2 i wkrótce wyłączymy starsze wersje, ponieważ starsi klienci nadal z nich korzystają i jest to ryzyko.

Wymuszanie połączenia TLS lub 32 z nich do przejścia przez sieć VPN przed przejściem do usługi nie dodaje zabezpieczeń. Powoduje to dodanie opóźnienia i zmniejszenie ogólnej przepływności. W niektórych rozwiązaniach sieci VPN wymusza nawet tunelowanie przez protokół TCP przez protokół UDP, co ponownie będzie miało bardzo negatywny wpływ na ruch przesyłany strumieniowo. I, chyba że robisz inspekcji TLS, nie ma do góry nogami, wszystkie minusy. Bardzo typowym tematem wśród klientów, teraz, gdy większość pracowników jest zdalna, jest to, że widzą znaczny wpływ na przepustowość i wydajność poprzez łączenie wszystkich użytkowników przy użyciu sieci VPN, zamiast konfigurować tunelowanie podzielone pod kątem dostępu do [optymalizowania kategorii Office 365 punktów końcowych](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

Jest to łatwa poprawka do rozdzielania tunelowania i należy to zrobić. Aby uzyskać więcej informacji, zapoznaj się [z tematem Optymalizowanie łączności Office 365 dla użytkowników zdalnych przy użyciu tunelowania podzielonego sieci VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="the-sins-of-the-past"></a>Grzechy przeszłości

Wiele razy przyczyną złych wyborów jest kombinacja (1) nie wiedząc, jak działa usługa, (2) próbuje przestrzegać zasad firmy, które zostały napisane przed wdrożeniem chmury, i (3) zespoły zabezpieczeń, które mogą nie być łatwo przekonany, że istnieje więcej niż jeden sposób, aby osiągnąć swoje cele. Mam nadzieję, że powyższe i poniższe linki pomogą w pierwszym. Sponsorowanie kadry kierowniczej może być wymagane, aby ominąć drugi. Zajęcie się celami zasad zabezpieczeń, a nie ich metodami, pomaga w realizacji trzeciego. Od dostępu warunkowego do moderowania zawartości, DLP do ochrony informacji, weryfikacji punktu końcowego do zagrożeń zero-day — każdy cel końcowy rozsądnych zasad zabezpieczeń może być osiągnięty z tym, co jest dostępne w Office 365 i bez zależności od lokalnego sprzętu sieciowego, wymuszone tunele VPN i TLS przerwać i sprawdzić.

Innym razem sprzęt o rozmiarze i zakupie przed rozpoczęciem przenoszenia do chmury przez organizację po prostu nie może być skalowany w górę w celu obsługi nowych wzorców ruchu i obciążeń. Jeśli naprawdę musisz kierować cały ruch przez pojedynczy punkt ruchu wychodzącego i/lub serwer proxy, przygotuj się do odpowiedniego uaktualnienia sprzętu sieciowego i przepustowości. Uważnie monitoruj wykorzystanie obu tych elementów, ponieważ środowisko nie będzie się zmniejszać powoli w miarę dołączania większej liczby użytkowników. Wszystko będzie dobrze, dopóki punkt zwrotny nie zostanie osiągnięty, a następnie wszyscy cierpią.

## <a name="exceptions-to-the-rules"></a>Wyjątki od reguł

Jeśli Organizacja wymaga [ograniczeń dzierżawy](/azure/active-directory/manage-apps/tenant-restrictions), należy użyć serwera proxy z podziałem protokołu TLS i sprawdzić, aby wymusić pewien ruch przez serwer proxy, ale nie musisz wymuszać całego ruchu przez niego.  Nie jest to propozycja typu wszystko lub nic, więc zwróć uwagę na to, co musi zostać zmodyfikowane przez serwer proxy.

Jeśli zamierzasz zezwolić na tunelowanie podzielone, ale także użyć serwera proxy dla ogólnego ruchu internetowego, upewnij się, że plik PAC definiuje, co musi iść bezpośrednio, a także jak zdefiniować interesujący ruch dla tego, co przechodzi przez tunel VPN. Oferujemy przykładowe pliki PAC, [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) które ułatwiają zarządzanie nimi.

## <a name="conclusion"></a>Wniosku

Dziesiątki tysięcy organizacji, w tym prawie wszystkie listy Fortune 500, codziennie używają Office 365 do swoich funkcji krytycznych dla misji. Robią to bezpiecznie i robią to przez Internet.

Bez względu na to, jakie cele w zakresie bezpieczeństwa masz w grze, istnieją sposoby, aby je osiągnąć, które nie wymagają połączeń sieci VPN, serwerów proxy, TLS przerwać i sprawdzić, lub scentralizowany ruch internetowy, aby uzyskać ruch użytkowników z sieci i na nasze tak szybko, jak to możliwe, co zapewnia najlepszą wydajność, czy sieć jest siedzibą firmy,  zdalnego biura lub tego użytkownika pracującego w domu. Nasze wskazówki są oparte na sposobie tworzenia usług Office 365 oraz zapewnianiu bezpiecznego i wydajnego środowiska użytkownika.

## <a name="further-reading"></a>Linki zewnętrzne

[Zasady łączności sieciowej Office 365](../enterprise/microsoft-365-network-connectivity-principles.md)

[Adresy URL i zakresy adresów IP usługi Office 365](../enterprise/urls-and-ip-address-ranges.md)

[Zarządzanie punktami końcowymi usługi Office 365](../enterprise/managing-office-365-endpoints.md)

[Usługa Office 365 — usługa sieci Web adresów IP i adresów URL](../enterprise/microsoft-365-ip-web-service.md)

[Ocena łączności sieciowej Office 365](../enterprise/assessing-network-connectivity.md)

[Office 365 dostrajanie sieci i wydajności](../enterprise/network-planning-and-performance.md)

[Ocena łączności sieciowej Office 365](../enterprise/assessing-network-connectivity.md)

[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](../enterprise/performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością dla Office 365](../enterprise/performance-troubleshooting-plan.md)

[Sieci dostarczania zawartości](../enterprise/content-delivery-networks.md)

[test łączności Microsoft 365](https://connectivity.office.com/)

[Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[blog sieci Office 365](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 łączności dla użytkowników zdalnych za pomocą tunelowania podzielonego sieci VPN](../enterprise/microsoft-365-vpn-split-tunnel.md)
