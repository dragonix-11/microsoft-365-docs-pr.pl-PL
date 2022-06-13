---
title: narzędzie do testowania łączności sieciowej Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: narzędzie do testowania łączności sieciowej Microsoft 365
ms.openlocfilehash: ac2ec12ac0da2309e1d5ac0c35bbd0462cc68a62
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043714"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>narzędzie do testowania łączności sieciowej Microsoft 365

Narzędzie do testowania łączności sieciowej Microsoft 365 znajduje się pod adresem <https://connectivity.office.com>. Jest to dodatkowe narzędzie do oceny sieci i szczegółowych informacji o sieci dostępnych w Centrum administracyjne platformy Microsoft 365 w obszarze **| kondycji Menu Łączność**.

> [!IMPORTANT]
> Ważne jest, aby zalogować się do dzierżawy Microsoft 365, ponieważ wszystkie raporty testowe są udostępniane administratorowi i przekazywane do dzierżawy podczas logowania.

> [!div class="mx-imgBorder"]
> ![Narzędzie do testowania łączności.](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>Narzędzie do testowania łączności sieciowej obsługuje dzierżawy WW Commercial, ale nie GCC Moderate, GCC High, DoD lub China.

Szczegółowe informacje o sieci w centrum Administracja Microsoft 365 są oparte na regularnych pomiarach w produkcie dla dzierżawy Microsoft 365, agregowanych każdego dnia. Dla porównania szczegółowe informacje o sieci z testu łączności sieciowej Microsoft 365 są uruchamiane lokalnie w narzędziu.

Testowanie w produkcie jest ograniczone, a uruchamianie testów lokalnych dla użytkownika zbiera więcej danych, co prowadzi do dokładniejszego wglądu. Szczegółowe informacje o sieci w centrum Administracja Microsoft 365 pokazują, że w określonej lokalizacji biura występuje problem z siecią. Test łączności Microsoft 365 może pomóc w zidentyfikowaniu głównej przyczyny tego problemu i zapewnieniu ukierunkowanej akcji poprawy wydajności.

Zalecamy, aby te szczegółowe informacje były używane razem, gdy można ocenić stan jakości sieci dla każdej lokalizacji biura w centrum Administracja Microsoft 365, a bardziej szczegółowe informacje można znaleźć po wdrożeniu testów na podstawie testu łączności Microsoft 365.

## <a name="what-happens-at-each-test-step"></a>Co się dzieje na każdym etapie testu

### <a name="office-location-identification"></a>Office identyfikacji lokalizacji

Po kliknięciu przycisku *Uruchom test* pokażemy uruchomioną stronę testów i zidentyfikujemy lokalizację biura. Możesz wpisać lokalizację według miasta, stanu i kraju lub wybrać, czy została wykryta. Jeśli wykryjesz lokalizację biura, narzędzie zażąda szerokości i długości geograficznej z przeglądarki internetowej i ograniczy dokładność do 300 metrów na 300 metrów przed użyciem. Nie trzeba dokładniej identyfikować lokalizacji niż budynek w celu mierzenia wydajności sieci.

### <a name="javascript-tests"></a>Testy języka JavaScript

Po identyfikacji lokalizacji biura uruchamiamy test opóźnienia protokołu TCP w języku JavaScript i żądamy od usługi danych dotyczących używanych i zalecanych serwerów Microsoft 365 usług front door. Po zakończeniu tych testów są one wyświetlane na mapie i na karcie szczegółów, gdzie można je wyświetlić przed następnym krokiem.

### <a name="download-the-advanced-tests-client-application"></a>Pobieranie aplikacji klienckiej testów zaawansowanych

Następnie rozpoczniemy pobieranie aplikacji klienckiej testów zaawansowanych. Polegamy na użytkowniku, aby uruchomić aplikację kliencką i musi mieć zainstalowane środowisko uruchomieniowe platformy .NET 6.0.

Test łączności sieciowej Microsoft 365 obejmuje dwie części: witrynę <https://connectivity.office.com> internetową i aplikację kliencką do pobrania Windows, która uruchamia zaawansowane testy łączności sieciowej. Większość testów wymaga uruchomienia aplikacji. Wyniki zostaną wypełnione z powrotem na stronie internetowej w miarę jej uruchamiania.

Po zakończeniu testów przeglądarki internetowej zostanie wyświetlony monit o pobranie zaawansowanej aplikacji testowej klienta z witryny sieci Web. Otwórz i uruchom plik po wyświetleniu monitu.

> [!div class="mx-imgBorder"]
> ![Aplikacja kliencka testów zaawansowanych.](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Uruchamianie aplikacji klienckiej testów zaawansowanych

Po uruchomieniu aplikacji klienckiej strona internetowa zostanie zaktualizowana w celu wyświetlenia tego wyniku. Dane testowe zaczną być odbierane na stronie internetowej. Strona jest aktualizowana za każdym razem, gdy są odbierane nowe dane, a dane można przeglądać w miarę ich pojawiania się.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Ukończone testy zaawansowane i przekazywanie raportu testowego

Po zakończeniu testów zarówno strona internetowa, jak i klient testów zaawansowanych będą to pokazywać. Jeśli użytkownik jest zalogowany, raport testowy zostanie przekazany do dzierżawy klienta.

## <a name="sharing-your-test-report"></a>Udostępnianie raportu testowego

Raport testowy wymaga uwierzytelniania na koncie Microsoft 365. Administrator wybiera sposób udostępniania raportu testowego. Ustawienia domyślne umożliwiają udostępnianie raportów innym użytkownikom w organizacji, a link ReportID jest niedostępny. Raporty wygasają domyślnie po 90 dniach.

### <a name="sharing-your-report-with-your-administrator"></a>Udostępnianie raportu administratorowi

Jeśli logujesz się po wystąpieniu raportu testowego, raport zostanie udostępniony administratorowi.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Udostępnianie z zespołem konta Microsoft, pomocą techniczną lub innym pracownikom

Raporty testowe (z wyłączeniem identyfikacji osobistej) są udostępniane pracownikom firmy Microsoft. To udostępnianie jest domyślnie włączone i może zostać wyłączone przez administratora w **| kondycji Strona Łączność sieciowa** w centrum Administracja Microsoft 365.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-microsoft-365-tenant"></a>Udostępnianie innym użytkownikom, którzy logują się do tej samej dzierżawy Microsoft 365

Możesz wybrać użytkowników do udostępnienia raportu. Możliwość wyboru jest domyślnie włączona, ale może zostać wyłączona przez administratora.

> [!div class="mx-imgBorder"]
> ![Udostępnianie użytkownikowi linku do wyników testu.](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>Udostępnianie wszystkim osobom korzystającym z linku ReportID

Raport testowy można udostępnić dowolnej osobie, zapewniając dostęp do linku ReportID. Ten link generuje adres URL, który można wysłać do kogoś, aby mógł on wyświetlić raport testowy bez logowania. To udostępnianie jest domyślnie wyłączone i musi być włączone przez administratora.

> [!div class="mx-imgBorder"]
> ![Udostępnianie linku do wyników testu.](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Wyniki testu łączności sieciowej

Wyniki są wyświetlane na kartach **Podsumowanie** i **Szczegóły** . Karta podsumowanie przedstawia mapę wykrytego obwodu sieci i porównanie oceny sieci z innymi Microsoft 365 klientów znajdujących się w pobliżu. Umożliwia również udostępnianie raportu testowego. Oto jak wygląda widok wyników podsumowania:

> [!div class="mx-imgBorder"]
> ![Wyniki podsumowania narzędzia do testowania łączności sieciowej.](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Oto przykład danych wyjściowych karty szczegółów. Na karcie szczegółów jest wyświetlany zielony znacznik wyboru koła, jeśli wynik został porównany pozytywnie. Jeśli wynik przekroczył próg wskazujący wgląd w sieć, zostanie wyświetlony czerwony trójkąt wykrzyknik. W poniższych sekcjach opisano poszczególne wiersze wyników karty szczegółów i objaśniają progi używane do analizy sieci.

> [!div class="mx-imgBorder"]
> ![Przykładowe wyniki testu narzędzia do testowania łączności sieciowej.](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Informacje o lokalizacji

W tej sekcji przedstawiono wyniki testów związane z Twoją lokalizacją.

#### <a name="your-location"></a>Twoja lokalizacja

Lokalizacja użytkownika jest wykrywana w przeglądarce internetowej użytkowników. Można go również wpisać w wybranym przez użytkownika miejscu. Służy do identyfikowania odległości sieciowych do określonych części obwodu sieci przedsiębiorstwa. W raporcie są zapisywane tylko miasto z tego wykrywania lokalizacji i odległość do innych punktów sieciowych.

Lokalizacja biura użytkownika jest wyświetlana w widoku mapy.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Lokalizacja ruchu wychodzącego sieci (lokalizacja, w której sieć łączy się z usługodawcą sieciowym)

Identyfikujemy adres IP ruchu wychodzącego sieci po stronie serwera. Bazy danych lokalizacji służą do wyszukiwania przybliżanych lokalizacji dla ruchu wychodzącego sieci. Te bazy danych zwykle mają dokładność około 90% adresów IP. Jeśli lokalizacja wyszukana z adresu IP ruchu wychodzącego sieci jest nieprawidłowa, może to prowadzić do fałszywego wyniku. Aby sprawdzić, czy ten błąd występuje dla określonego adresu IP, możesz użyć publicznie dostępnych sieciowych witryn sieciowych adresów IP do porównania z rzeczywistą lokalizacją.

#### <a name="your-distance-from-the-network-egress-location"></a>Odległość od lokalizacji ruchu wychodzącego sieci

Określamy odległość od tej lokalizacji do lokalizacji biura. Jest to wyświetlane jako wgląd w sieć, jeśli odległość jest większa niż **800** kilometrów, ponieważ może to zwiększyć opóźnienie TCP o ponad 25 ms i może mieć wpływ na środowisko użytkownika.

Mapa przedstawia lokalizację ruchu wychodzącego sieci w stosunku do lokalizacji biura użytkownika wskazującą zaplecze sieci wewnątrz sieci WAN przedsiębiorstwa.

Zaimplementuj ruch wychodzący sieci lokalnej i bezpośredniej z lokalizacji biura użytkownika do Internetu w celu uzyskania optymalnej Microsoft 365 łączności sieciowej. Ulepszenia lokalnego i bezpośredniego ruchu wychodzącego to najlepszy sposób na rozwiązanie tego problemu.

#### <a name="proxy-server-information"></a>Informacje o serwerze proxy

Określamy, czy serwery proxy są skonfigurowane na maszynie lokalnej w celu przekazywania ruchu sieciowego Microsoft 365 w kategorii **Optymalizacja**. Identyfikujemy odległość od lokalizacji biura użytkownika do serwerów proxy.

Odległość jest najpierw testowana za pomocą polecenia ping protokołu ICMP. Jeśli to się nie powiedzie, przetestujemy polecenie ping protokołu TCP i na koniec wyszukamy adres IP serwera proxy w bazie danych lokalizacji adresów IP. Pokazujemy szczegółowe informacje o sieci, jeśli serwer proxy znajduje się dalej niż **800** kilometrów od lokalizacji biura użytkownika.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Wirtualna sieć prywatna (VPN) używana do nawiązywania połączenia z organizacją

Ten test wykrywa, czy używasz sieci VPN do nawiązywania połączenia z Microsoft 365. Wynik przekazywania będzie wyświetlany, jeśli nie masz sieci VPN lub jeśli masz sieć VPN z zalecaną konfiguracją tunelu podzielonego dla Microsoft 365.

#### <a name="vpn-split-tunnel"></a>Tunnel podziału sieci VPN

Każda trasa kategorii **Optymalizacja** dla Exchange Online, SharePoint Online i Microsoft Teams jest testowana, aby sprawdzić, czy jest ona tunelowana w sieci VPN. Podzielone obciążenie całkowicie unika sieci VPN. Obciążenie tunelowane jest wysyłane za pośrednictwem sieci VPN. Selektywne obciążenie tunelowane ma niektóre trasy wysyłane przez sieć VPN, a niektóre są podzielone. Wynik przekazywania będzie pokazywać, czy wszystkie obciążenia są podzielone lub selektywnie tunelowane.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Klienci w obszarze metropolitalnym z lepszą wydajnością

Opóźnienie sieci między lokalizacją biura użytkownika a usługą Exchange Online jest porównywane z innymi Microsoft 365 klientów w tym samym obszarze metra. Analiza sieci jest wyświetlana, jeśli 10% lub więcej klientów w tym samym obszarze metra ma lepszą wydajność. Oznacza to, że ich użytkownicy będą mieli lepszą wydajność w Microsoft 365 interfejsie użytkownika.

Ten wgląd w sieć jest generowany na podstawie tego, że wszyscy użytkownicy w mieście mają dostęp do tej samej infrastruktury telekomunikacyjnej i tej samej bliskości obwodów internetowych i sieci firmy Microsoft.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Czas na żądanie DNS w sieci

Spowoduje to wyświetlenie serwera DNS skonfigurowanego na maszynie klienckiej, na których uruchomiono testy. Może to być serwer rekursywnego rozpoznawania nazw DNS, jednak jest to nietypowe. Jest bardziej prawdopodobne, że jest to serwer usługi przesyłania dalej DNS, który buforuje wyniki DNS i przekazuje wszystkie nienadłużone żądania DNS do innego serwera DNS.

Jest to dostępne tylko dla informacji i nie przyczynia się do analizy sieci.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>Odległość od i/lub czasu nawiązywania połączenia z cyklicznym programem rozpoznawania nazw DNS

Program rekursywnego rozpoznawania nazw DNS w użyciu jest identyfikowany przez wykonanie określonego żądania DNS, a następnie zwrócenie się do serwera nazw DNS o adres IP, z którego otrzymał to samo żądanie. Ten adres IP jest rekursywnym programem rozpoznawania nazw DNS i będzie wyszukiwany w bazach danych lokalizacji adresów IP w celu znalezienia lokalizacji. Następnie obliczana jest odległość od lokalizacji biura użytkownika do lokalizacji serwera rekursywnego rozpoznawania nazw DNS. Jest to wyświetlane jako wgląd w sieć, jeśli odległość jest większa niż **500 mil** (800 kilometrów).

Lokalizacja wyszukana z adresu IP ruchu wychodzącego sieci może nie być dokładna i może to prowadzić do fałszywego wyniku z tego testu. Aby sprawdzić, czy ten błąd występuje dla określonego adresu IP, możesz użyć publicznie dostępnych sieciowych witryn sieciowych adresów IP.

Ten wgląd w sieć będzie miał szczególny wpływ na wybór bramy głównej usługi Exchange Online. Aby rozwiązać ten problem, lokalny i bezpośredni ruch wychodzący sieci powinien być wstępnie wymagany, a następnie rekursywny program rozpoznawania nazw DNS powinien znajdować się w pobliżu tego ruchu wychodzącego sieci.

### <a name="exchange-online"></a>Exchange Online

W tej sekcji przedstawiono wyniki testów związane z Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Exchange lokalizacji drzwi wejściowych usługi

Brama frontowa usługi Exchange w użyciu jest identyfikowana w taki sam sposób, jak Outlook to robi, a my mierzymy opóźnienie TCP sieci od lokalizacji użytkownika do niej. Opóźnienie TCP jest wyświetlane, a używana brama frontowa usługi Exchange jest porównywana z listą najlepszych drzwi wejściowych usługi dla bieżącej lokalizacji. Jest to wyświetlane jako wgląd w sieć, jeśli jedna z najlepszych bram Exchange usługi nie jest używana.

Użycie jednej z najlepszych bram Exchange usług może być spowodowane przez ruch przychodzący sieci przed ruchem wychodzącym sieci firmowej, w którym to przypadku zalecamy ruch wychodzący sieci lokalnej i bezpośredniej. Może to być również spowodowane przez użycie zdalnego serwera rekursywnego rozpoznawania nazw DNS, w którym to przypadku zalecamy wyrównanie cyklicznego serwera rozpoznawania nazw DNS z ruchem wychodzącym sieci.

Obliczamy potencjalne zwiększenie opóźnienia TCP (ms) w bramie głównej usługi Exchange. W tym celu należy przyjrzeć się przetestowanym opóźnieniu sieci lokalizacji biura użytkownika i odjąć opóźnienie sieci od bieżącej lokalizacji do szaf Exchange front door usługi. Różnica reprezentuje potencjalną możliwość poprawy.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Najlepsze Exchange usług dla twojej lokalizacji

Spowoduje to wyświetlenie najlepszych Exchange lokalizacji bramy głównej usługi według miasta dla Twojej lokalizacji.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Usługa Front Door zarejestrowana w systemie DNS klienta

Spowoduje to wyświetlenie nazwy DNS i adresu IP serwera front door usługi Exchange, do którego został przekierowany. Jest ona udostępniana tylko do celów informacyjnych i nie ma skojarzonego wglądu w sieć.

### <a name="sharepoint-online"></a>SharePoint Online

W tej sekcji przedstawiono wyniki testów związane z usługami SharePoint Online i OneDrive.

#### <a name="the-service-front-door-location"></a>Lokalizacja drzwi wejściowych usługi

Brama frontowa usługi SharePoint w użyciu jest identyfikowana w taki sam sposób, jak OneDrive klient, a my mierzymy opóźnienie TCP sieci z lokalizacji biura użytkownika do niej.

#### <a name="download-speed"></a>Szybkość pobierania

Mierzymy szybkość pobierania pliku o rozmiarze 15 Mb z bramy głównej usługi SharePoint. Wynik jest wyświetlany w megabajtach na sekundę, aby wskazać, jaki plik rozmiaru w megabajtach można pobrać z SharePoint lub OneDrive w **ciągu jednej sekundy**. Liczba ta powinna być podobna do jednej dziesiątej minimalnej przepustowości obwodu w megabitach na sekundę. Jeśli na przykład masz połączenie internetowe o wartości 100 mb/s, możesz spodziewać się 10 megabajtów na sekundę (10 MB/s).

#### <a name="buffer-bloat"></a>Buforowanie obiektu bloat

Podczas pobierania 15 Mb mierzymy opóźnienie TCP w bramie frontowej usługi SharePoint. Jest to opóźnienie w obciążeniu i jest porównywane z opóźnieniem, gdy nie jest pod obciążeniem. Wzrost opóźnienia w przypadku obciążenia jest często przypisywany do ładowanych buforów urządzeń sieciowych konsumentów (lub nadętych). Szczegółowe informacje o sieci są wyświetlane dla każdego obiektu bloat wynoszącego co najmniej 1000.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Usługa Front Door zarejestrowana w systemie DNS klienta

Spowoduje to wyświetlenie nazwy DNS i adresu IP serwera front door usługi SharePoint, do którego została przekierowana. Jest ona udostępniana tylko do celów informacyjnych i nie ma skojarzonego wglądu w sieć.

### <a name="microsoft-teams"></a>Microsoft Teams

W tej sekcji przedstawiono wyniki testów związane z Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Łączność z nośnikami (audio, wideo i udostępnianie aplikacji)

Spowoduje to przetestowanie łączności UDP z bramą frontową usługi Microsoft Teams. Jeśli jest to zablokowane, Microsoft Teams nadal może działać przy użyciu protokołu TCP, ale dźwięk i wideo będą osłabione. Przeczytaj więcej na temat tych pomiarów sieci UDP, które mają również zastosowanie do Microsoft Teams w sekcji [Jakość multimediów i Wydajność łączności sieciowej w usłudze Skype dla firm Online](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

#### <a name="packet-loss"></a>Utrata pakietu

Pokazuje utratę pakietów UDP mierzoną w 10-sekundowym testowym wywołaniu audio od klienta do bramy głównej usługi Microsoft Teams. Dla przebiegu wartość ta powinna być niższa niż **1,00%.**

#### <a name="latency"></a>Opóźnienie

Pokazuje zmierzone opóźnienie UDP, które powinno być mniejsze niż **100 ms**.

#### <a name="jitter"></a>Jitter

Pokazuje zmierzone jitter UDP, które powinny być niższe niż **30ms**.

#### <a name="connectivity"></a>Łączność

Testujemy łączność HTTP z lokalizacji biura użytkownika do wszystkich wymaganych Microsoft 365 punktów końcowych sieci. Są one publikowane pod adresem [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Wgląd w sieć jest wyświetlany dla wszystkich wymaganych punktów końcowych sieci, z którymi nie można nawiązać połączenia.

Łączność może zostać zablokowana przez serwer proxy, zaporę lub inne urządzenie zabezpieczeń sieci na obwodzie sieci przedsiębiorstwa. Łączność z portem TCP 80 jest testowana przy użyciu żądania HTTP, a łączność z portem TCP 443 jest testowana za pomocą żądania HTTPS. Jeśli nie ma odpowiedzi, nazwa FQDN jest oznaczona jako awaria. Jeśli istnieje kod odpowiedzi HTTP 407, nazwa FQDN jest oznaczona jako błąd. Jeśli istnieje kod odpowiedzi HTTP 403, sprawdzamy atrybut Serwera odpowiedzi i jeśli wydaje się, że jest to serwer proxy, oznaczamy to jako błąd. Testy, które wykonujemy, można symulować za pomocą narzędzia wiersza polecenia Windows curl.exe.

Testujemy certyfikat SSL w każdym wymaganym punkcie końcowym Microsoft 365 sieci, który znajduje się w kategorii optymalizacji lub zezwalaj zgodnie z definicją w [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md)temacie . Jeśli jakiekolwiek testy nie znajdą certyfikatu SSL firmy Microsoft, zaszyfrowana sieć połączona musi zostać przechwycona przez pośredniczące urządzenie sieciowe. Szczegółowe informacje o sieci są wyświetlane na wszystkich przechwyconych zaszyfrowanych punktach końcowych sieci.

W przypadku znalezienia certyfikatu SSL, który nie jest dostarczany przez firmę Microsoft, wyświetlamy nazwę FQDN dla testu i właściciela certyfikatu SSL w użyciu. Ten właściciel certyfikatu SSL może być dostawcą serwera proxy lub certyfikatem z podpisem własnym przedsiębiorstwa.

#### <a name="network-path"></a>Ścieżka sieciowa

W tej sekcji przedstawiono wyniki śledzenia protokołu ICMP do bramy głównej usługi Exchange Online, bramy głównej usługi SharePoint Online oraz bramy głównej usługi Microsoft Teams. Jest ona udostępniana tylko do celów informacyjnych i nie ma skojarzonego wglądu w sieć. Dostępne są trzy trasy śledzenia. Traceroute to _outlook.office365.com_, traceroute to the customers SharePoint fronton or _to microsoft.sharepoint.com_ if one was not provided, and a traceroute to _world.tr.teams.microsoft.com_.

## <a name="connectivity-reports"></a>Raporty dotyczące łączności

Po zalogowaniu możesz przejrzeć poprzednie raporty, które zostały uruchomione. Możesz je również udostępnić lub usunąć z listy.

> [!div class="mx-imgBorder"]
> ![Raporty.](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>Stan kondycji sieci

Pokazuje to wszelkie istotne problemy zdrowotne związane z globalną siecią firmy Microsoft, które mogą mieć wpływ na Microsoft 365 klientów.

> [!div class="mx-imgBorder"]
> ![Stan kondycji sieci.](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="testing-from-the-command-line"></a>Testowanie z poziomu wiersza polecenia

Udostępniamy plik wykonywalny wiersza polecenia, który może być używany przez narzędzia zdalnego wdrażania i wykonywania i uruchamiać te same testy, które są dostępne w witrynie internetowej narzędzia do testowania łączności sieciowej Microsoft 365.

Narzędzie do testowania wiersza polecenia można pobrać tutaj: [Narzędzie wiersza polecenia](https://connectivity.office.com/api/AnonymousConnectivityTest/DownloadStandAloneRichClient)

Można go uruchomić, klikając dwukrotnie plik wykonywalny w Windows Eksplorator plików, możesz uruchomić go z poziomu wiersza polecenia lub zaplanować go za pomocą harmonogramu zadań.

Po pierwszym uruchomieniu pliku wykonywalnego zostanie wyświetlony monit o zaakceptowanie umowy licencyjnej użytkownika końcowego (EULA) przed przeprowadzeniem testowania. Jeśli umowa EULA została już przeczytana i zaakceptowana, możesz utworzyć pusty plik o nazwie Microsoft-365-Network-Connectivity-Test-EULA-accepted.txt w bieżącym katalogu roboczym dla procesu wykonywalnego po jego uruchomieniu. Aby zaakceptować umowę EULA, możesz wpisać ciąg "y" i nacisnąć klawisz Enter w oknie wiersza polecenia po wyświetleniu monitu.

Plik wykonywalny akceptuje następujące parametry wiersza polecenia:
- -h, aby wyświetlić link do tej dokumentacji pomocy
- -testlist &lt;test&gt; określa testy do uruchomienia. Domyślnie uruchamiane są tylko testy podstawowe. Prawidłowe nazwy testów obejmują: wszystkie, dnsConnectivityPerf, dnsResolverIdentification, bufferBloat, traceroute, proxy, vpn, skype, connectivity, networkInterface
- -filepath &lt;filedir&gt; ścieżka katalogu plików wyników testu. Dozwolona wartość to ścieżka bezwzględna lub względna dostępnego katalogu
- -city &lt;city&gt; Dla pola miasta, stanu i kraju określona wartość będzie używana, jeśli zostanie podana. Jeśli nie zostanie podany, zostanie wyświetlone zapytanie Windows Usługi lokalizacyjne (WLS). Jeśli zabezpieczenia na poziomie WLS nie powiedzie się, lokalizacja zostanie wykryta z ruchu wychodzącego sieci maszyn 
- -state, &lt;stan&gt;
- -country country &lt;&gt; 
- -proxy &lt;account&gt; &lt;password&gt; Nazwa konta serwera proxy i hasło można podać, jeśli potrzebujesz serwera proxy, aby uzyskać dostęp do Internetu

### <a name="results"></a>Wyniki
Dane wyjściowe wyników są zapisywane w pliku JSON w folderze o nazwie TestResults, który jest tworzony w bieżącym katalogu roboczym procesu, chyba że już istnieje. Format nazwy pliku dla danych wyjściowych to connectivity_test_result_YYYY-MM-DD-HH-MM-SS.json. Wyniki są w węzłach JSON, które są zgodne z danymi wyjściowymi wyświetlanymi na stronie internetowej witryny internetowej narzędzia do testowania łączności sieciowej Microsoft 365. Przy każdym uruchomieniu jest tworzony nowy plik wyników, a autonomiczny plik wykonywalny nie przekazuje wyników do dzierżawy firmy Microsoft na potrzeby wyświetlania na stronach Łączność sieciowa centrum administracyjnego. Kody drzwi wejściowych, długości geograficzne i szerokości geograficzne nie są uwzględniane w pliku wyników.

### <a name="launching-from-windows-file-explorer"></a>Uruchamianie z Windows Eksplorator plików
Możesz po prostu kliknąć dwukrotnie plik wykonywalny, aby rozpocząć testowanie i zostanie wyświetlone okno wiersza polecenia.

### <a name="launching-from-the-command-prompt"></a>Uruchamianie z wiersza polecenia
W oknie wiersza polecenia CMD.EXE można wpisać ścieżkę i nazwę pliku wykonywalnego, aby go uruchomić. Nazwa pliku jest Microsoft.Connectivity.Test.exe

### <a name="launching-from-windows-task-scheduler"></a>Uruchamianie z harmonogramu zadań Windows
W Windows Harmonogram zadań możesz dodać zadanie uruchamiania autonomicznego pliku wykonywalnego testu. Należy określić bieżący katalog roboczy zadania, w którym został utworzony plik zaakceptowany przez umowę EULA, ponieważ plik wykonywalny będzie blokowany do momentu zaakceptowania umowy EULA. Nie można interaktywnie zaakceptować umowy EULA, jeśli proces jest uruchamiany w tle bez konsoli.

### <a name="more-details-on-the-standalone-executable"></a>Więcej szczegółów na temat autonomicznego pliku wykonywalnego
Narzędzie wiersza polecenia używa usług Windows Location Services do znajdowania użytkowników informacji o kraju stanu miasta na potrzeby określania pewnych odległości. Jeśli Windows usługi lokalizacyjne są wyłączone w panelu sterowania, oceny oparte na lokalizacji użytkownika będą puste. W Windows Ustawienia "Usługi lokalizacyjne" muszą być włączone, a "Zezwalaj aplikacjom klasycznym na dostęp do Twojej lokalizacji" również musi być włączony.

Narzędzie wiersza polecenia podejmie próbę zainstalowania .NET Framework, jeśli nie jest jeszcze zainstalowana. Spowoduje to również pobranie głównego pliku wykonywalnego testowania z narzędzia do testowania łączności sieciowej Microsoft 365 i uruchomienie go.

## <a name="faq"></a>Często zadawane pytania

Poniżej przedstawiono odpowiedzi na niektóre z naszych często zadawanych pytań.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Co jest wymagane do uruchomienia klienta testów zaawansowanych?

Klient testów zaawansowanych wymaga środowiska uruchomieniowego platformy .NET 6.0. Jeśli uruchomisz zaawansowanego klienta testowego bez zainstalowanego programu, nastąpi przekierowanie do [strony instalatora platformy .NET 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0/runtime?utm_source=getdotnetcore). Pamiętaj, aby zainstalować aplikację z kolumny Uruchamianie aplikacji klasycznych dla Windows. Uprawnienia administratora na komputerze są wymagane do zainstalowania środowiska uruchomieniowego platformy .NET 6.0.

Klient testów zaawansowanych używa usługi SignalR do komunikowania się ze stroną internetową. W tym celu należy upewnić się, że połączenie portu TCP 443 z **connectivity.service.signalr.net** jest otwarte. Ten adres URL nie jest publikowany w pliku, <https://aka.ms/o365ip> ponieważ łączność nie jest wymagana dla Microsoft 365 użytkownika aplikacji klienckiej.

### <a name="what-is-microsoft-365-service-front-door"></a>Co to jest Microsoft 365 usługi front door?

Brama frontowa usługi Microsoft 365 jest punktem wejścia w globalnej sieci firmy Microsoft, gdzie Office klienci i usługi przerywają połączenie sieciowe. Aby uzyskać optymalne połączenie sieciowe z Microsoft 365, zaleca się, aby połączenie sieciowe zostało przerwane w najbliższej Microsoft 365 drzwiach wejściowych w twoim mieście lub metrze.

> [!NOTE]
> Microsoft 365 usługa front door nie ma bezpośredniej relacji z produktem **usługi Azure Front Door Service** dostępnym na platformie Azure Marketplace.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Jaka jest najlepsza Microsoft 365 usługi front door?

Najlepszym Microsoft 365 usługi front door (dawniej znany jako optymalne usługi front door) jest taki, który jest najbliżej ruchu sieciowego, ogólnie w mieście lub dzielnicy metra. Użyj narzędzia do wydajności sieci Microsoft 365, aby określić lokalizację używanej bramy frontowej usługi Microsoft 365 i najlepszych drzwi wejściowych usługi. Jeśli narzędzie określi, że używana brama frontowa jest jedną z najlepszych, należy oczekiwać doskonałej łączności z globalną siecią firmy Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Co to jest internetowa lokalizacja ruchu wychodzącego?

Lokalizacja ruchu wychodzącego z Internetu to lokalizacja, w której ruch sieciowy zamyka sieć przedsiębiorstwa i łączy się z Internetem. Jest to również identyfikowane jako lokalizacja, w której masz urządzenie translatora adresów sieciowych (NAT) i zwykle w którym łączysz się z dostawcą usług internetowych. Jeśli widzisz dużą odległość między lokalizacją i lokalizacją ruchu wychodzącego z Internetu, może to zidentyfikować znaczący backhaul sieci WAN.

## <a name="related-topics"></a>Tematy pokrewne

[Łączność sieciowa w centrum Administracja Microsoft 365](office-365-network-mac-perf-overview.md)

[Microsoft 365 szczegółowych informacji o wydajności sieci](office-365-network-mac-perf-insights.md)

[ocena sieci Microsoft 365](office-365-network-mac-perf-score.md)

[usługi lokalizacji łączności sieciowej Microsoft 365](office-365-network-mac-location-services.md)
