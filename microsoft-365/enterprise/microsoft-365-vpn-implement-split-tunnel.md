---
title: Implementowanie rozdzielania sieci VPN na Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/28/2022
audience: Admin
ms.article: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Jak zaimplementować rozdzielanie sieci VPN dla sieci Microsoft 365
ms.openlocfilehash: 59414e32f187dc4e8354dc0c20228a4222fa2754
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2022
ms.locfileid: "63009727"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implementowanie rozdzielania sieci VPN na Microsoft 365

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji Microsoft 365 zdalnych.

>- Aby uzyskać omówienie korzystania z rozdzielania dzielonego sieci VPN w celu zoptymalizowania Microsoft 365 dla użytkowników zdalnych, zobacz Omówienie: rozdzielanie sieci VPN dla sieci [Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać informacje na temat optymalizowania Microsoft 365 wydajności dzierżawy na całym świecie dla użytkowników w Chinach, zobacz Microsoft 365 [optymalizację wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

Od wielu lat przedsiębiorstwa obsługują środowisko zdalne za pomocą sieci VPN. Podczas gdy podstawowe obciążenia pracą pozostaną lokalne, sieć VPN z klienta zdalnego przekierowyowana przez centrum danych w sieci firmowej była podstawową metodą uzyskiwania dostępu do zasobów firmowych przez użytkowników zdalnych. Aby chronić te połączenia, przedsiębiorstwa tworzy warstwy rozwiązań zabezpieczeń sieciowych wzdłuż ścieżek sieci VPN. Te zabezpieczenia zostały stworzone do ochrony infrastruktury wewnętrznej i ochrony przeglądania zewnętrznych witryn sieci Web w trybie przenośnym przez przekierowanie ruchu do sieci VPN, a następnie za pośrednictwem lokalnego obwodu Internetu. Sieci VPN, obwody sieci i skojarzona infrastruktura zabezpieczeń były często celowe i skalowane dla określonego woluminu ruchu — zwykle większość łączności jest inicjowana z sieci firmowej, a większość z nich znajduje się w granicach sieci wewnętrznej.

Przez dość długi czas modele sieci VPN, w których wszystkie połączenia z urządzeń użytkowników zdalnych są kierowane z powrotem do sieci lokalnej (nazywanej wymuszanym redukowaniem _), były_ w dużym stopniu uatywniane, o ile równoczesna skala użytkowników zdalnych była niewielka, a ruch sieci VPN był niewielka.  Niektórzy klienci nadal korzystają z wymuszania sieci VPN na wytyczyniu statusu quo nawet po tym, gdy ich aplikacje przeniesiono z obwodu firmy do publicznych chmur SaaS.

Korzystanie z wymuszonych sieci VPN w celu nawiązywania połączeń z aplikacjami chmurowymi o równomiernej wydajności jest suboptimalnie, ale w niektórych przedsiębiorstwach ich negatywne skutki zostały zaakceptowane w celu zachowania quo stanu zabezpieczeń. Poniżej przedstawiono przykładowy diagram tego scenariusza:

![Podziel Tunnel konfigurację sieci VPN.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

Ten problem rozrastał się od wielu lat, a wielu klientów zgłasza znaczną zmianę wzorców ruchu sieciowego. Ruch, który był używany do pracy w środowisku lokalnym, teraz łączy się z zewnętrznymi punktami końcowymi chmury. Wielu klientów firmy Microsoft zgłaszało wcześniej, że około 80% ich ruchu sieciowego było źródłem wewnętrznym (reprezentowanym przez linię kropkową na powyższym diagramie). W 2020 roku liczba ta wynosi około 20% lub mniej w związku z przeniesieniem głównych obciążeń do chmury, trendy te nie są rzadkością w przypadku innych przedsiębiorstw. Z czasem, w związku z postępem podróży w chmurze, powyższy model staje się coraz bardziej uciążliwy i nieusuwalny, uniemożliwiając organizacji adaptacyjną się w momencie przechodzenia do pierwszego świata w chmurze.

Podczas globalnej sytuacji kryzysowej w współpracy z siecią COVID-19 ten problem eskalował, aby wymagać natychmiastowego rozwiązywania problemów. Konieczność zapewnienia bezpieczeństwa pracowników wygenerowała wyjątkowe wymagania dotyczące it przedsiębiorstwa w celu zapewnienia wysokiej produktywności w domu na ogromną skalę. Microsoft 365 ma dobre położenie, aby pomóc klientom w realizacji tego wymagania, ale wysoki współbieżność użytkowników pracujących z domu generuje dużą ilość ruchu Microsoft 365, który, jeśli jest przekierowyny przez wymuszone sieci VPN i obwody sieci lokalnej, powoduje szybkie nasycenie i dużą pojemność infrastruktury sieci VPN. W nowej rzeczywistości dostęp przez sieć VPN do sieci Microsoft 365 nie jest już tylko utrudnieniami w wydajności, ale trudnym ścianą, która nie tylko wpływa na usługę Microsoft 365 ale także na krytyczne operacje biznesowe, które nadal muszą polegać na sieci VPN do obsługi.

Firma Microsoft ściśle współpracuje z klientami i szerszą branżą od wielu lat, aby dostarczać efektywne, nowoczesne rozwiązania tych problemów z poziomu naszych własnych usług i być zgodne z najlepszymi rozwiązaniami branżowymi. [Zasady łączności](./microsoft-365-network-connectivity-principles.md) w usłudze Microsoft 365 zaprojektowano tak, aby wydajnie pracować dla użytkowników zdalnych, jednocześnie pozwalając organizacji na zachowanie zabezpieczeń i kontroli nad ich łącznością. Te rozwiązania można również szybko wdrożyć, mając ograniczoną pracę, ale jednocześnie uzyskać istotne, dodatni wpływ na opisane powyżej problemy.

Zalecana przez firmę Microsoft strategia optymalizacji łączności pracowników zdalnych skupia się na szybkim ograniczaniem problemów i zapewnieniu wysokiej wydajności, przy użyciu kilku prostych kroków. Te kroki obejmują dostosowanie starszego podejścia sieci VPN dla kilku zdefiniowanych punktów końcowych, które pomijają wąskie gardła serwerów VPN. Równoważny lub nawet doskonały model zabezpieczeń można stosować na różnych warstwach w celu usunięcia konieczności zabezpieczenia całego ruchu na ruchu wychodzącym z sieci firmowej. W większości przypadków można to efektywnie zrealizować w ciągu godzin, a następnie można to skalować do innych obciążeń tak, jak pozwala na to wymaganie i czas.

## <a name="common-vpn-scenarios"></a>Typowe scenariusze sieci VPN

Na poniższej liście przedstawiono najbardziej typowe scenariusze sieci VPN w środowiskach przedsiębiorstwa. Większość klientów w tradycyjnej obsłudze modelu 1 (połączenia VPN z Tunnel). Ta sekcja pomoże w krótkim i bezpiecznym przejściu do modelu **2**, który można uzyskać przy stosunkowo niewielkim nałocie pracy i ma niezwykle duże korzyści z wydajnością sieci i środowiskiem użytkownika.

| Model | Opis |
| --- | --- |
| [1. Wymuszone połączenia VPN Tunnel](#1-vpn-forced-tunnel) | 100% ruchu przechodzi do klienta VPN, łącznie z lokalnym, Internetem i wszystkimi usługami O365/M365 |
| [2. VPN Wymuszane Tunnel z kilkoma wyjątkami](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | Vpn jest domyślnie używany (domyślnie prowadzi do sieci VPN), a w przypadku kilku najważniejszych wyklucznych scenariuszy można kierować |
| [3. Vpn wymuszane Tunnel z szerokimi wyjątkami](#3-vpn-forced-tunnel-with-broad-exceptions) | Vpn jest domyślnie używany (domyślnie prowadzi trasę do sieci VPN), z szerokimi wyjątkami, które mogą kierować (na przykład wszystkie połączenia Microsoft 365, Wszystkie usługi Salesforce, Wszystkie powiększenie) |
| [4. Selektywny Tunnel VPN](#4-vpn-selective-tunnel) | Vpn jest używany tylko w przypadku usług opartych na corpnet. Trasa domyślna (Internet i wszystkie usługi internetowe) działa bezpośrednio. |
| [5. Brak połączenia VPN](#5-no-vpn) | Odmiana ciągu #2. Zamiast starszego połączenia VPN wszystkie usługi Corpnet są publikowane przy użyciu nowoczesnych metod zabezpieczeń (takich jak Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS itp.). |

### <a name="1-vpn-forced-tunnel"></a>1. Wymuszone połączenia VPN Tunnel

Najczęstszy scenariusz początkowy dla większości klientów korporacyjnych. Używany jest wymuszony interfejs VPN, co oznacza, że 100% ruchu jest przekierowywowywowy do sieci firmowej niezależnie od tego, czy punkt końcowy znajduje się w sieci firmowej. Każdy ruch zewnętrzny (internetowy), taki jak Microsoft 365 lub przeglądanie Internetu, jest następnie przypięty z powrotem z lokalnego sprzętu zabezpieczającego, takiego jak proxy. W bieżącej sytuacji z prawie 100% użytkowników pracujących zdalnie ten model obciąża infrastrukturę sieci VPN, co może znacznie utrudnić wydajność całego ruchu firmowego, przez co przedsiębiorstwa mogą pracować wydajnie w czasie kryzysowej sytuacji.

![VPN Wymuszanie Tunnel modelu 1.](../media/vpn-split-tunneling/vpn-model-1.png)

### <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. Vpn Wymuszane Tunnel z niewielką liczbą zaufanych wyjątków

Znacznie bardziej efektywne działanie w przedsiębiorstwie. Ten model pozwala na obejście obwodu sieci VPN i bezpośrednie kierowanie się do usługi sieci Microsoft 365 punktów końcowych o wysokim obciążeniach i opóźnieniach. W ten sposób znacznie zwiększa się wydajność usług ładowanych oraz zmniejsza się obciążenie infrastruktury sieci VPN, dzięki czemu elementy, które wciąż wymagają jej działania, wymagają niższej zawartości zasobów. Jest to model, w którym skupimy się na udzielaniu pomocy przy przejściu do tego modelu, ponieważ umożliwia szybkie szybkie działanie z wieloma wynikami dodatnimi.

![Podziel Tunnel vpn model 2.](../media/vpn-split-tunneling/vpn-model-2.png)

### <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. Vpn wymuszane Tunnel z szerokimi wyjątkami

Rozszerza zakres modelu 2. Zamiast wysyłać bezpośrednio małą grupę zdefiniowanych punktów końcowych, cały ruch jest przesyłany bezpośrednio do zaufanych usług, takich jak Microsoft 365 i SalesForce. To dodatkowo zmniejsza obciążenie firmowej infrastruktury VPN i poprawia wydajność zdefiniowanych usług. Ponieważ ten model może zająć więcej czasu na ocenę chłoniania i zaimplementowanie go, prawdopodobnie będzie to etap, który można podjąć iteratywnie w późniejszym terminie, gdy model drugi zostanie pomyślnie wdrożyny.

![Dzielenie Tunnel VPN model 3.](../media/vpn-split-tunneling/vpn-model-3.png)

### <a name="4-vpn-selective-tunnel"></a>4. Połączenia selektywne VPN Tunnel

Odwraca trzeci model w tym, że tylko ruch oznaczony jako ma firmowy adres IP jest wysyłany w dół ścieżki vpn, przez co ścieżka internetowa jest trasą domyślną dla wszystkich innych. Ten model wymaga, aby organizacja była dobrze na ścieżce do [](https://www.microsoft.com/security/zero-trust?rtc=1) zerowego zaufania w celu bezpiecznego wdrożenia tego modelu. Należy zauważyć, że ten model lub jego zmiana prawdopodobnie stanie się z czasem niezbędnym domyślnym ustawieniem w miarę przechodzenia większej liczby usług z sieci firmowej do chmury.

Firma Microsoft używa tego modelu wewnętrznie. Aby uzyskać więcej informacji na temat implementacji sieci VPN przez firmę Microsoft, zobacz Uruchamianie w sieci VPN: W jaki sposób firma Microsoft łączy się ze swoimi [pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Podziel Tunnel VPN model 4.](../media/vpn-split-tunneling/vpn-model-4.png)

### <a name="5-no-vpn"></a>5. Brak połączenia VPN

Bardziej zaawansowana wersja modelu numer 2, w której wszelkie usługi wewnętrzne są publikowane za pomocą nowoczesnego podejścia zabezpieczeń lub rozwiązania SDWAN, takiego jak serwer proxy usługi Azure AD, usługa Defender dla aplikacji w chmurze, skalr ZPA itp.

![Podziel Tunnel VPN model 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="implement-vpn-split-tunneling"></a>Implementowanie rozdzielania sieci VPN

W tej sekcji znajdziesz proste czynności wymagane do przeprowadzenia migracji architektury klienta VPN z wymuszonego połączenia VPN do wymuszonego klienta sieci _VPN_ z kilkoma zaufanymi wyjątkami, modelem rozdzielanym vpn [#2](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) w typowych scenariuszach sieci _VPN_[.](#common-vpn-scenarios)

Na poniższym diagramie pokazano, jak działa zalecane rozwiązanie do rozdzielania rozdzielaowego VPN:

![Podziel szczegóły rozwiązania sieci VPN z rozdzielanym vpn.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. Identyfikowanie punktów końcowych do optymalizowania

W artykule [Microsoft 365](urls-and-ip-address-ranges.md) URL i zakresów adresów IP firma Microsoft wyraźnie identyfikuje kluczowe punkty końcowe potrzebne do ich optymalizowania i kategoryzowania **ich jako Optymalizuj**. Obecnie są tylko cztery adresy URL i 20 podsieci IP, które wymagają optymalizacji. Ta mała grupa kont punktów końcowych dla około 70% – 80% ruchu do usługi Microsoft 365, w tym punktów końcowych, które są poufne dla opóźnień, takich jak punkty Teams multimediów. Zasadniczo jest to ruch, o który należy szczególnie zadbać, a także ruch, który słynie z natłokania tradycyjnych ścieżek sieciowych i infrastruktury VPN.

Adresy URL w tej kategorii mają następujące cechy:

- Czy punkty końcowe będące własnością firmy Microsoft i zarządzane są hostowane w infrastrukturze firmy Microsoft
- Czy zostały podane ip
- Niskie tempo zmiany i powinny pozostać małe (obecnie jest to 20 podsieci IP)
- Czy przepustowość i/lub opóźnienie są poufne
- Mogą mieć wymagane elementy zabezpieczeń udostępniane w usłudze, a nie w tekście w sieci.
- Uwzględnianie około 70–80% ruchu do usługi Microsoft 365 sieci

Aby uzyskać więcej informacji Microsoft 365 oraz sposobu kategoryzowania i zarządzania nimi, zobacz Zarządzanie Microsoft 365 [punktami końcowymi](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>Optymalizowanie adresów URL

Bieżącą tabelę adresy URL optymalizowania można znaleźć w poniższej tabeli. W większości przypadków używaj tylko punktów końcowych adresu URL w pliku [PAC](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) przeglądarki, w którym te punkty końcowe są skonfigurowane jako wysyłane bezpośrednio, a nie do serwera proxy.

| Optymalizowanie adresów URL | Port/protokół | Cel |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Jest to jeden z podstawowych adresów URL, Outlook jest używany do łączenia się z serwerem Exchange Online i ma dużą ilość użycia przepustowości oraz liczbę połączeń. Funkcje online są wymagane do obsługi małych opóźnień sieci, takich jak wyszukiwanie błyskawiczne, inne kalendarze skrzynek pocztowych, wyszukiwanie informacji wolny/zajęty, zarządzanie regułami i alertami, Exchange archiwum online, wiadomości e-mail wychodzące ze skrzynki nadawczej. |
| <https://outlook.office.com> | TCP 443 | Ten adres URL jest używany do nawiązywania Outlook sieci Web w trybie online na Exchange Online sieci Web i jest poufny dla opóźnień sieciowych. Łączność jest szczególnie wymagana w przypadku dużych plików do przekazywania i pobierania za pośrednictwem usługi SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Jest to podstawowy adres URL dla usługi SharePoint Online i ma zastosowanie wysokiej przepustowości. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Jest to podstawowy adres URL usługi OneDrive dla Firm ma wysokie użycie przepustowości i prawdopodobnie wysoką liczbę połączeń z narzędzia OneDrive dla Firm synchronizacji połączeń. |
| Teams i/lub adresy IP plików multimedialnych (bez adresu URL) | UDP 3478, 3479, 3480 i 3481 | Alokacja odnajdowania przekazywania i ruch w czasie rzeczywistym (3478), Dźwięk (3479), Wideo (3480) i Udostępnianie ekranu wideo (3481). Są to punkty końcowe używane do przesyłania Skype dla firm sieci Microsoft Teams multimediów (połączeń, spotkań itp.). Większość punktów końcowych jest dostarczana, gdy Microsoft Teams nawiązuje połączenie (i są zawarte w wymaganych dla usługi punktach IP). Użycie protokołu UDP jest wymagane do zapewnienia optymalnej jakości multimediów.   |

W powyższych przykładach **dzierżawę** należy zastąpić nazwą Microsoft 365 dzierżawy. Na przykład **contoso.onmicrosoft.com** użyć funkcji _contoso.sharepoint.com_ i _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optymalizowanie zakresów adresów IP

W chwili pisania zakresów adresów IP, z których odpowiadają te punkty końcowe, są następujące. Zdecydowanie zaleca się  używanie skryptu, takiego jak ten [](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) przykład, usługi sieci Web [adresów IP i URL usługi Microsoft 365](microsoft-365-ip-web-service.md) lub strony adres [URL/IP](urls-and-ip-address-ranges.md) w celu sprawdzenia, czy są dostępne aktualizacje podczas stosowania konfiguracji, i regularne stosowanie zasad.

```
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. Optymalizowanie dostępu do tych punktów końcowych za pośrednictwem sieci VPN

Po zidentyfikowaniu tych krytycznych punktów końcowych musimy od przekierować je z drogi vpn i umożliwić mu bezpośrednie połączenie z usługą przy użyciu lokalnego połączenia internetowego użytkownika. Sposób realizacji tego zadania będzie się różnić w zależności od używanej platformy maszynowej i produktu VPN, ale większość rozwiązań VPN pozwala na stosowanie tej logiki przez prostą konfigurację zasad. Aby uzyskać informacje na temat platformy VPN dotyczącej podziału na rozdzielanie, zobacz [Przewodniki HOWTO dotyczące typowych platform VPN](#howto-guides-for-common-vpn-platforms).

Jeśli chcesz przetestować rozwiązanie ręcznie, możesz wykonać poniższy przykład programu PowerShell, aby emulować rozwiązanie na poziomie tabeli trasy. W tym przykładzie do tabeli trasy dodaje się Teams IP mediów multimedialnych. Możesz przetestować wydajność Teams multimediów przed i po oraz obserwować różnicę w trasach dla określonych punktów końcowych.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Przykład: Dodawanie Teams IP multimediów do tabeli tras

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

W powyższym skrypcie _$intIndex jest_ indeksem interfejsu połączonego z Internetem (można go znaleźć, uruchamiając polecenie **get-netadapter** w programie PowerShell; poszukaj wartości _ifIndex_), _$gateway jest_ domyślną bramą tego interfejsu (można to znaleźć, uruchamiając konfigurację **ipconfig** w wierszu polecenia lub **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** in PowerShell).

Po dodaniu tras możesz potwierdzić, że tabela tras jest poprawna, uruchamiając drukowanie  trasy w wierszu polecenia lub programie PowerShell. Dane wyjściowe powinny zawierać dodane trasy, pokazując indeks interfejsu (_22_ w tym przykładzie) i bramę dla tego interfejsu (w tym przykładzie _192.168.1.1_ ):

![Trasuj dane wyjściowe wydruku.](../media/vpn-split-tunneling/vpn-route-print.png)

Aby dodać trasy dla  wszystkich bieżących zakresów adresów IP w kategorii Optymalizowanie, możesz użyć następującej odmiany skryptu w celu zapytania usługi sieci Web adresów [IP i URL usługi Microsoft 365](microsoft-365-ip-web-service.md) dla bieżącego zestawu podsieci Optymalizowanie adresów IP i dodawania ich do tabeli trasy.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Przykład: Dodawanie wszystkich podsieci Optymalizowanie do tabeli tras

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Jeśli przypadkowo dodano trasy z niepoprawnymi parametrami lub po prostu chcesz przywrócić zmiany, możesz usunąć właśnie dodane trasy za pomocą następującego polecenia:

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

Klient VPN powinien zostać skonfigurowany tak, aby ruch do **dostawcy IP** optymalizowania był tak przekierowywowyny. Dzięki temu ruch może korzystać z lokalnych zasobów firmy Microsoft, takich jak Microsoft 365 Front Door usługi, takich jak front drzwi platformy [Azure Front Door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/), które dostarczają usługi Microsoft 365 i punkty końcowe łączności tak blisko twoich użytkowników, jak to tylko możliwe. Umożliwia to nam dostarczanie użytkownikom wysokiego poziomu wydajności niezależnie od tego, gdzie znajdują się na świecie, i pełne korzystanie z globalnej sieci firmy [Microsoft](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), która prawdopodobnie zajmuje kilka milisekund od ich bezpośredniego ruchu wychodzącego.

## <a name="configuring-and-securing-teams-media-traffic"></a>Konfigurowanie i zabezpieczanie ruchu Teams multimediów

Niektórzy administratorzy mogą wymagać bardziej szczegółowych informacji na temat sposobu, w jaki przepływy połączeń działają Teams w modelu rozdzielania rozdzielania i jak połączenia są zabezpieczone.

### <a name="configuration"></a>Konfiguracja

Zarówno w przypadku połączeń, jak i spotkań, o ile wymagane podsieci IP Optymalizowanie podsieci IP dla multimediów Teams są poprawnie na miejscu w tabeli trasy, Teams wywołuje funkcję [Get Przełęczy](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) w celu określenia, który interfejs lokalny powinien odpowiadać trasom, które ma być kierowane do określonego miejsca docelowego, interfejs lokalny zostanie zwrócony dla miejsc docelowych firmy Microsoft w podanych powyżej blokach ADRESÓW IP firmy Microsoft.

Niektóre oprogramowanie klienckie VPN zezwala na manipulowanie routingiem na podstawie adresu URL. Jednak ruch Teams nie jest skojarzony z adresem URL, więc kontrolę nad routingiem dla tego ruchu należy wykonać przy użyciu podsieci IP.

W niektórych scenariuszach, często niezwiązanych z konfiguracją Teams klienta, ruch multimedialny nadal przechodzi przez katalog VPN, nawet gdy są prawidłowe trasy. Jeśli wystąpi ten scenariusz, należy użyć reguły zapory w celu zablokowania Teams IP lub portów z używania sieci VPN.

>[!IMPORTANT]
>Aby zapewnić, Teams ruch multimedialny jest kierowane przy użyciu odpowiedniej metody we wszystkich scenariuszach sieci VPN, upewnij się, że użytkownicy Microsoft Teams mają wersję klienta **1.3.00.13565** lub nowszą. Ta wersja zawiera ulepszenia dotyczące wykrywania dostępnych ścieżek sieciowych przez klienta.

Ruch sygnałowy jest wykonywany przez protokół HTTPS i nie jest tak opóźniony, jak ruch multimedialny, i jest oznaczony  jako Zezwalaj w danych adresu URL/IP, przez co w razie potrzeby można bezpiecznie przekierować ruch przez klienta VPN.

>[!NOTE]
>Microsoft Edge **96 i więcej** obsługuje również podzielenie sieci VPN na ruch w komunikacji równorzędnej. Oznacza to, że klienci mogą zyskać korzyści z rozdzielania sieci VPN na Teams klientów sieci Web w przeglądarce Edge. Klienci, którzy chcą skonfigurować go dla witryn internetowych uruchomionych w przeglądarce Edge, mogą osiągnąć ten cel, umożliwiając włączenie zasad [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Bezpieczeństwo

Jednym z typowych argumentów na unikanie podziałów na rozdzielanie jest to, że jest mniej bezpieczny, np. Żaden ruch, który nie przechodzi przez klienta VPN, nie będzie korzystać z jakiegokolwiek schematu szyfrowania stosowanego do szyfrowania vpn, przez co będzie mniej bezpieczny.

Głównym argumentem licznika jest to, że ruch multimedialny jest już zaszyfrowany za pośrednictwem protokołu _Secure Real-Time Transport Protocol (SRTP_) — profilu protokołu Real-Time Transport Protocol (RTP), który zapewnia poufność, uwierzytelnianie i ponowne odtwarzanie ochrony przed atakami do ruchu WTP. Sam SRTP korzysta z losowo wygenerowanego klucza sesji, który jest wymieniany za pośrednictwem zabezpieczonego kanału sygnałowego TLS. Ten temat szczegółowo opisano w tym [przewodniku zabezpieczeń](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), ale podstawową sekcją zainteresowań jest szyfrowanie multimediów.

Ruch multimedialny jest szyfrowany przy użyciu srTP, który korzysta z klucza sesji wygenerowanego przez bezpieczny generator liczb losowych i wymieniany przy użyciu kanału sygnałowego TLS. Ponadto multimedia przepływujące w obu kierunkach między serwerem pośrednicowym i jego wewnętrznym następnym przeskokiem są również szyfrowane przy użyciu SRTP.

Skype dla firm Online generuje nazwę użytkownika/hasła w celu zapewnienia bezpiecznego dostępu do przekazywania multimediów przez _portal Traversal przy użyciu przekazywania dookoła NAT (TURN)._ Przekazywanie multimediów wymienia nazwę użytkownika/hasło za pośrednictwem kanału SIP zabezpieczonego za pomocą protokołu TLS. Warto zauważyć, że nawet jeśli w celu połączenia klienta z siecią firmową może zostać użyty vpn, ruch nadal musi przepływać w formularzu SRTP, gdy opuszcza sieć firmową, aby połączyć się z usługą.

Informacje o tym, Teams ogranicza typowe zagrożenia związane z zabezpieczeniami, takie jak ataki funkcji komunikacji głosowej lub przechodzenia przez narzędzia do przechodzenia przez sesję _nat (STUN),_ można znaleźć w tece [5.1](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c) Zagadnienia związane z zabezpieczeniami dotyczące implementerów.

O nowoczesnych mechanizmach kontroli zabezpieczeń w scenariuszach pracy zdalnej można również przeczytać w artykule Alternatywne sposoby dla informatyków i informatyków dotyczące osiągnięcia nowoczesnych kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy [Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Testowanie

Gdy zasady będą działać, upewnij się, że działają zgodnie z oczekiwaniami. Istnieje wiele sposobów testowania ścieżki, która jest poprawnie ustawiona do korzystania z lokalnego połączenia internetowego:

- Uruchom test [Microsoft 365,](https://aka.ms/netonboard) który spowoduje uruchomienie testów łączności, w tym śledzenia tras, jak powspomniano powyżej. Dodaliśmy także do tego narzędzia testy sieci VPN, które powinno również dostarczyć dodatkowych informacji.

- Prosta ścieżka **śledzenia do** punktu końcowego, który znajduje się w zakresie podziału, powinna pokazywać ścieżkę przebytą, na przykład:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Następnie powinna być zobaczysz ścieżkę tego punktu końcowego za pośrednictwem lokalnego internetowego punktu końcowego, która powinna rozpoznać adres IP z zakresów Teams, które skonfigurowaliśmy do rozdzielania rozdzielania.

- Przechwyć sieć za pomocą narzędzia takiego jak Wireshark. Filtruj według protokołu UDP podczas połączenia. W zakresie optymalizowania powinien być wyświetlony ruch o przepływie do **Teams IP.** Jeśli dla tego ruchu jest używany szyfrowanie sieci VPN, ruch multimedialny nie będzie widoczny w wynikach śledzenia.

### <a name="additional-support-logs"></a>Dodatkowe dzienniki pomocy technicznej

Jeśli potrzebujesz dodatkowych danych do rozwiązania lub jeśli potrzebujesz pomocy technicznej firmy Microsoft, uzyskanie poniższych informacji powinno przyspieszyć znalezienie rozwiązania. Uniwersalny zestaw narzędzi Do rozwiązywania problemów opartych na **Windows CMD** pomocy technicznej firmy Microsoft może ułatwić zbieranie odpowiednich dzienników w prosty sposób. Narzędzie i instrukcje dotyczące używania można znaleźć na stronie <https://aka.ms/TssTools>.

## <a name="how-to-optimize-stream--live-events"></a>Jak zoptymalizować strumień & wydarzeń na żywo

Microsoft 365 w wydarzeniach na żywo (dotyczy Teams wydarzeń na żywo owanych przez uczestników, Teams także wydarzenia z zewnętrznym koderem za pośrednictwem usługi Teams, Stream lub Yammer), a ruch usługi Stream na żądanie jest obecnie kategoryzowany jako domyślny a optymalizowany na liście  adresów [URL/IP](urls-and-ip-address-ranges.md) usługi. Te punkty końcowe są kategoryzowane **jako** domyślne, ponieważ są hostowane w sieciach CDN, które mogą być również używane przez inne usługi. Klienci zazwyczaj preferują serwer proxy dla tego typu ruchu i stosują wszystkie elementy zabezpieczeń zwykle wykonywane w punktach końcowych, takich jak te.

Wielu klientów prosiło o dane adresów URL/IP potrzebne do połączenia ich użytkowników z usługą Stream/Live Events bezpośrednio z ich lokalnego połączenia internetowego, zamiast przekierowywał ruch o dużej pojemności i opóźnień za pośrednictwem infrastruktury VPN. Zazwyczaj nie jest to możliwe bez zarówno dedykowanych przestrzeni nazw, jak i dokładnych informacji o adresach IP dla punktów końcowych, które nie są dostępne dla punktów końcowych Microsoft 365 jako **domyślne**.

Aby włączyć łączność bezpośrednią usługi Stream/Live Events z klientami korzystającymi z wymuszonego połączenia VPN, należy wykonać poniższe czynności. To rozwiązanie ma na celu zapewnienie klientom opcji unikania routingu ruchu w zdarzeniach na żywo przez sieć VPN, gdy istnieje duży ruch sieciowy ze względu na scenariusze z pracy z domu. Jeśli to możliwe, zaleca się uzyskanie dostępu do usługi przez serwer proxy przeprowadzający inspekcję.

>[!NOTE]
>W przypadku użycia tego rozwiązania mogą wystąpić elementy usługi, które nie rozwiązują podanego adresu IP, przez co przechodzi przez sieć VPN, ale zbiorczy ruch o dużej pojemności, taki jak przesyłanie strumieniowe danych, powinien być przesyłany. Poza zakresem zdarzeń na żywo/strumienia mogą znajdować się inne elementy, które napawają uwagę podczas tego ładowania, ale powinny one być ograniczone, ponieważ muszą spełniać zarówno usługę _FQDN,_ jak i dopasowanie adresu IP, zanim trafią bezpośrednio.

>[!IMPORTANT]
>Zaleca się, aby klienci zważyli na ryzyko wysyłania większej liczby ruchu ominięcia sieci VPN w większej wydajności niż w przypadku wydarzeń na żywo.

Aby zaimplementować wyjątek wymuszany wyekspowania Teams wydarzeń na żywo i usługi Stream, należy zastosować następujące kroki:

### <a name="1-configure-external-dns-resolution"></a>1. Konfigurowanie rozpoznawania zewnętrznego systemu DNS

Klienci muszą mieć dostęp do zewnętrznej, rekurentywnej rozdzielczości DNS, aby można było rozpoznać następujące nazwy hostów jako adresy IP.

- \*azureedge.net
- \*media.azure.net
- \*bmc.cdn.office.net

**\*.azureedge.net** jest używana do zdarzeń usługi Stream (Konfigurowanie koderów dla przesyłania strumieniowego na żywo w [umacie Microsoft Stream — Usługa Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** **\*i bmc.cdn.office.net** są używane do tworzenia wydarzeń na żywo Teams (wydarzeń szybkich start, wydarzeń RTMP-In obsługiwanych [Identyfikator planu 84960]) zaplanowanych w kliencie Teams klienta.

 Niektóre z tych punktów końcowych są udostępniane innym elementom poza usługą Stream/Wydarzenia na żywo. Zaleca się używanie tych FQDN do konfigurowania ładowania SIECI VPN, nawet jeśli to możliwe technicznie w rozwiązaniu VPN (np. jeśli działa ono w witrynie FQDN, a nie w adresie IP).

W konfiguracji SIECI VPN nie są wymagane sieci FQDN, mają tylko zastosowanie w plikach PAC w połączeniu z adresami IP w celu bezpośredniego wysyłania ruchu.

### <a name="2-implement-pac-file-changes-where-required"></a>2. Implementowanie zmian w plikach PAC (jeśli jest to wymagane)

W przypadku organizacji korzystających z pliku PAC w celu trasy ruchu przez serwer proxy w sieci VPN zwykle uzyskuje się to za pomocą FQDN. Jednak w przypadku wydarzeń na żywo/**\*** streamu podane nazwy hostów zawierają symbole wieloznaczne, takie jak azureedge.net, które również obejmują inne elementy, dla których nie można podać pełnych list adresów IP. Dlatego, jeśli żądanie jest wysyłane bezpośrednio na podstawie samego dopasowania z symbolami wieloznacznych DNS, ruch do tych punktów końcowych zostanie zablokowany, ponieważ w kroku 3 nie ma trasy przez ścieżkę [bezpośrednią](#3-configure-routing-on-the-vpn-to-enable-direct-egress).

Aby rozwiązać ten problem, możemy udostępnić następujące adresy IP i używać ich w połączeniu z nazwami hostów w kroku [1](#1-configure-external-dns-resolution) w przykładowym pliku PAC. Plik PAC sprawdza, czy adres URL jest ten sam, jak używany dla zdarzeń Stream/Live, a następnie, jeśli tak, sprawdza również, czy adres IP zwrócony z odnośnika DNS jest ten sam, jak adres podany dla usługi. Jeśli _oba_ są zgodne, ruch jest kierowany bezpośrednio. Jeśli którykolwiek z elementów (FQDN/IP) nie jest zgodne, ruch jest wysyłany do serwera proxy. Dzięki temu konfiguracja zapewnia, że wszystko, co znajdzie się poza zakresem adresów IP i zdefiniowanych przestrzeni nazw, będzie przechodzić przez serwer proxy przez sieć VPN tak jak zwykle.

#### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Zbieranie bieżących list punktów CDN końcowych

Wydarzenia na żywo używa wielu CDN do przesyłania strumieniowego do klientów, aby zapewnić najlepszą wydajność, jakość i odporność. Obecnie używane są Azure CDN firmy Microsoft i Verizon. Z czasem może to zostać zmienione ze względu na sytuacje, takie jak dostępność regionalna. Ten artykuł jest źródłem, dzięki którym możesz na bieżąco śledzić zakresy adresów IP.

W przypadku Azure CDN firmy Microsoft możesz pobrać listę z witryny Pobieranie zakresów [adresów IP](https://www.microsoft.com/download/details.aspx?id=56519) i tagów usług platformy Azure — chmury publicznej z oficjalnego Centrum pobierania Microsoft — musisz poszukać w szczególności tagu usługi *AzureFrontdoor.Frontend* w usłudze JSON. *AddressPrefixs* will show the IPv4/IPv6 subnets. Z czasem adresów IP mogą się zmieniać, ale lista tagów usługi jest zawsze aktualizowana przed ich użyciem.

Na Azure CDN firmy Verizon (Edgecast) [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) możesz znaleźć pełną listę, używając (kliknij pozycję **Wypróbuj) —** musisz szukać w szczególności sekcji **Premium\_ Verizon**. Pamiętaj, że ten interfejs API pokazuje wszystkie ip usługi Edgecast (pochodzenie i Anycast). Obecnie nie istnieje mechanizm interfejsu API rozróżniania pochodzenia od funkcji Anycast.

Aby zaimplementować to w pliku PAC, możesz użyć poniższego przykładu, który wysyła nazwę Microsoft 365 Optimize traffic direct (co jest zalecane najlepszym rozwiązaniem) za pośrednictwem nazwy FQDN, a krytyczny ruch Stream/Live Events bezpośrednio za pośrednictwem kombinacji nazwy FQDN i zwróconego adresu IP. Nazwa zastępczą _Contoso_ należy edytować pod nazwą konkretnej dzierżawy, gdzie _contoso_ pochodzi z contoso.onmicrosoft.com

##### <a name="example-pac-file"></a>Przykładowy plik PAC

Oto przykład wygenerowania plików PAC:

1. Zapisz poniższy skrypt na lokalnym dysku twardym jako _Get-TLEPacFile.ps1_.
1. Przejdź do adresu [URL sieci Verizon](/rest/api/cdn/edge-nodes/list#code-try-0) i pobierz wynikowy kod JSON (skopiuj go do pliku, takiego jak cdnedgenodes.json)
1. Umieść plik w tym samym folderze, w którym znajduje się skrypt.
1. W oknie programu PowerShell uruchom następujące polecenie. Zmień nazwę dzierżawy na coś innego, jeśli chcesz uzyskać adresy URL usługi SPO. Jest to typ 2, więc optymalizuj **i** **zezwalaj** (typ 1 to tylko optymalizowanie).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. Plik TLE.pac będzie zawierać wszystkie przestrzenie nazw i adresów IP (IPv4/IPv6).

###### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Skrypt automatycznie analizuje listę platformy Azure na podstawie adresu [URL](https://www.microsoft.com/download/details.aspx?id=56519) i kluczy pobierania z usługi **AzureFrontDoor.Frontend**, więc nie trzeba pobierać tego ręcznie.

Zaleca się także, aby połączenia VPN można było ładować tylko za pomocą FQDN. korzystanie **zarówno z** sieci FQDN, jak i adresów IP w funkcji pomaga ograniczyć wykorzystanie tego obciążenia do ograniczonego zestawu punktów końcowych, w tym do usługi Live Events/Stream. Struktura funkcji spowoduje, że wykonywana będzie odnośnik DNS dla nazwy FQDN, która będzie odpowiadać tym, które są wymienione bezpośrednio przez klienta, na przykład rozpoznawanie nazw DNS pozostałych przestrzeni nazw pozostaje bez zmian.

Jeśli chcesz ograniczyć ryzyko związanego z ładowaniem punktów końcowych nie związanych z wydarzeniami na żywo i usługą Stream, **\*** możesz usunąć domenę .azureedge.net z konfiguracji, gdzie większość tego ryzyka leży, ponieważ jest to domena udostępniona używana dla wszystkich klientów usługi Azure CDN. Minusem tej funkcji jest to, że żadne zdarzenie korzystające z zewnętrznego kodera nie zostanie zoptymalizowane, ale wydarzenia są organizowane/zorganizowane w ramach Teams będą.

### <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Konfigurowanie routingu w sieci VPN w celu włączenia bezpośredniego ruchu wychodzącego

Ostatnim krokiem jest dodanie trasy bezpośredniej do adresu IP zdarzeń na żywo opisanego w artykule Zbieranie bieżących list punktów końcowych usługi **CDN** do konfiguracji sieci VPN w celu zapewnienia, że ruch nie będzie wysyłany przez wymuszony parametr sieci VPN. Szczegółowe informacje o tym, jak to zrobić dla punktów końcowych usługi Microsoft 365 Optimize, można znaleźć w sekcji Implementowanie rozdzielania sieci [VPN](#implement-vpn-split-tunneling), a proces jest dokładnie taki sam dla dostawcy IP usługi Stream/Wydarzeń na żywo wymienionego w tym dokumencie.

Pamiętaj, że do konfiguracji sieci VPN powinny być używane tylko protokoły IP (a nie FQDN) z bieżącej listy CDN punktów końcowych sieci VPN.[](#gathering-the-current-lists-of-cdn-endpoints)

### <a name="stream--live-events-optimization-faq"></a>Przesyłanie strumieniowe & optymalizacji wydarzeń na żywo — często zadawane pytania

#### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Czy spowoduje to kierowanie całego ruchu do usługi?

Nie, spowoduje to wysłanie ruchu strumieniowego, w przypadku których ruch strumieniowy z opóźnieniem jest przesyłany bezpośrednio w przypadku zdarzenia na żywo lub przesyłania strumieniowego, każdy inny ruch będzie nadal korzystać z serwera vpn, jeśli nie rozpozna opublikowanych ip.

#### <a name="do-i-need-to-use-the-ipv6-addresses"></a>Czy muszę używać adresów IPv6?

Nie, łączność może mieć protokół IPv4 tylko wtedy, gdy jest to wymagane.

#### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Dlaczego te adresy IP nie są publikowane w usłudze Microsoft 365 URL/IP?

Firma Microsoft dysponuje rygorystycznymi mechanizmami kontroli nad formatem i typem informacji w usłudze, aby zapewnić klientom możliwość niezawodnego używania tych informacji w celu wdrożenia bezpiecznego i optymalnego routingu na podstawie kategorii punktów końcowych.

W **kategorii** Domyślny punkt końcowy nie podano informacji o adresie IP z wielu powodów (Domyślne punkty końcowe mogą być poza kontrolą firmy Microsoft, mogą zmieniać się zbyt często lub mogą być zawarte w blokach udostępnionych innym elementom). Z tego powodu domyślne punkty końcowe są przeznaczone do przesyłania za pośrednictwem usługi FQDN do serwera proxy inspekcji, takiego jak normalny ruch sieci Web.

W tym przypadku powyższe punkty końcowe to sieci CDN, które mogą być używane przez elementy inne niż zdarzenia na żywo lub strumień inne niż zdarzenia na żywo firmy Microsoft, a zatem wysyłanie bezpośredniego ruchu będzie również oznaczać wszystko, co zmieni się w tych adresach IP, zostanie również wysłane bezpośrednio z klienta. Ze względu na unikatowy charakter bieżącej globalnej kryzysowej sytuacji i w celu zaspokojenia krótkich potrzeb naszych klientów firma Microsoft dostarczyła klientom powyższe informacje do użycia zgodnie z ich potrzebami.

Firma Microsoft pracuje nad ponowne skonfigurowaniem punktów końcowych zdarzeń na żywo, aby w przyszłości umożliwić ich uwzględnianie w kategoriach punktów końcowych Zezwalaj/Optymalizuj.

#### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Czy muszę zezwolić na dostęp tylko do tych ip?

Nie, dostęp do wszystkich oznaczonych  punktów końcowych wymaganych w [usłudze adresów URL/IP](urls-and-ip-address-ranges.md) jest niezbędny do działania usługi. Ponadto jest wymagany dowolny opcjonalny punkt końcowy oznaczony dla usługi Stream (IDENTYFIKATOR 41-45).

#### <a name="what-scenarios-will-this-advice-cover"></a>Jakie scenariusze będą dotyczyć tych porad?

1. Wydarzenia na żywo w aplikacji Teams App
2. Wyświetlanie hostowanej zawartości usługi Stream
3. Wydarzenia są wykonywane na urządzeniach zewnętrznych (encoder)

#### <a name="does-this-advice-cover-presenter-traffic"></a>Czy ta porada dotyczy ruchu osób prezentera?

Nie, powyższe porady mają tylko charakter tylko dla osób, które chłoną usługę. Prezentujejąc z poziomu programu Teams, zobaczymy ruch prezentera trafiający do oznaczonych punktów końcowych UDP wymienionych w wierszu 11 adresu URL/usługi IP ze szczegółowymi poradami o ładowaniu VPN opisanymi [](#implement-vpn-split-tunneling) w sekcji Implementowanie rozdzielania vpn.

#### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Czy ta konfiguracja powoduje ryzyko kierowania ruchu innego niż strumień &amp; wydarzeń na żywo?

Tak, ze względu na udostępnione usługi FQNS używane dla niektórych elementów usługi jest to nie da się uniknąć. Ten ruch jest zazwyczaj wysyłany za pośrednictwem firmowego serwera proxy, który może zastosować inspekcję. W scenariuszu z podziałem na scenariusz z podziałem sieci VPN użycie zarówno sieci FQDN, jak i ip spowoduje minimalne wykorzystanie tego ryzyka, ale nadal będzie istnieć. **\*** Klienci mogą usunąć domenę azureedge.net z konfiguracji ładowania i zmniejszyć to ryzyko do minimalnego poziomu, ale spowoduje Teams usunięcie ładowania zdarzeń na żywo obsługiwanych przez usługę Stream (zaplanowanych przez usługę Teams, zdarzeń kodera zewnętrznego, wydarzeń Yammer owanych w programie Teams, zdarzeń zewnętrznego kodera Yammer zaplanowanego przez usługę Yammer oraz wydarzeń planowanych przez usługę Stream lub wyświetlania ich na żądanie z poziomu usługi Stream). Wydarzenia zaplanowane i produkcji Teams pozostają nienaruszone.

## <a name="howto-guides-for-common-vpn-platforms"></a>Przewodniki HOWTO dotyczące typowych platform VPN

Ta sekcja zawiera linki do szczegółowych przewodników implementowania rozdzielania Microsoft 365 sieciowego od najbardziej typowych partnerów w tym miejscu. Po ich dodaniu dodamy kolejne przewodniki.

- **Windows 10 VPN**: Optymalizowanie ruchu sieci Microsoft 365 pracowników zdalnych przy użyciu [natywnego Windows 10 VPN](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [Optymalizowanie podziału usługi Anyconnect Tunnel pod kątem usługi Office365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **GlobalProtect, Palo Alto**: [Optymalizowanie ruchu Microsoft 365 przez sieć VPN Tunnel wykluczanie trasy dostępu](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: Optymalizowanie ruchu w Microsoft 365 dostępu zdalnego za pośrednictwem [sieci VPN w przypadku używania usługi BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Brama Citrix**: [Optymalizowanie klienta VPN bramy Citrix dla usługi Office365](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: Szyfrowanie [sieci VPN: jak skonfigurować rozdzielanie w celu wykluczenia Microsoft 365 aplikacji](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Check Point VPN**: [How to configure Split Tunnel for Microsoft 365 and other SaaS Applications](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="vpn-split-tunneling-faq"></a>Rozdzielanie sieci VPN — często zadawane pytania

Zespół zabezpieczeń firmy Microsoft opublikował alternatywne sposoby dla specjalistów bezpieczeństwa i [it](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) na uzyskanie nowoczesnych kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej ( wpis w blogu, w który przedstawiono kluczowe sposoby dla specjalistów bezpieczeństwa i it może zapewnić nowoczesne mechanizmy kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej). Ponadto poniżej przedstawiono niektóre często zadawane przez klientów pytania i odpowiedzi na ten temat.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Jak zatrzymać użytkownikom dostęp do innych dzierżaw, którym nie ufam, gdzie mogą oni eksfiltrować dane?

Odpowiedzią jest funkcja [o nazwie ograniczenia dzierżawy](/azure/active-directory/manage-apps/tenant-restrictions). Ruch uwierzytelniania nie jest duży ani nie jest szczególnie poufny dla opóźnień, więc może być przesyłany za pośrednictwem rozwiązania VPN do lokalnego serwera proxy, do którego ta funkcja została zastosowana. W tym miejscu jest zachowywana lista zaufanych dzierżaw i jeśli klient próbuje uzyskać token do dzierżawy, która nie jest zaufana, serwer proxy po prostu odrzuca żądanie. Jeśli dzierżawa jest zaufana, token jest dostępny, jeśli użytkownik ma odpowiednie poświadczenia i prawa.

Dlatego mimo że użytkownik może nawiązaniu połączenia TCP/UDP z powyższymi oznaczonymi punktami końcowymi optymalizowania, bez prawidłowego tokenu na potrzeby uzyskiwania dostępu do danych dzierżawy, po prostu nie może się zalogować ani uzyskać dostępu do żadnych danych ani ich przenosić.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Czy ten model umożliwia dostęp do usług dla klientów osobistych, takich jak osobiste OneDrive konta?

Nie, punkty końcowe usługi Microsoft 365 nie są takie same jak usługi dla klientów konsumenckich (na przykład Onedrive.live.com), więc rozdzielany nie zezwala użytkownikowi na bezpośredni dostęp do usług dla klientów konsumenckich. Ruch do punktów końcowych klientów będzie nadal korzystać z ruchu VPN i istniejące zasady będą nadal obowiązywać.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Jak stosować zasady DLP i chronić poufne dane, gdy ruch nie przepływa już za pośrednictwem rozwiązania lokalnego?

Aby zapobiec przypadkowemu ujawnianiu informacji poufnych, Microsoft 365 ma bogaty zestaw wbudowanych [narzędzi](../compliance/information-protection.md). Możesz użyć wbudowanych funkcji [DLP aplikacji Teams](../compliance/dlp-learn-about-dlp.md) i SharePoint w celu wykrywania niestosownie przechowywanych lub udostępnionych informacji poufnych. Jeśli część strategii dotyczącej pracy zdalnej obejmuje zasady bring-your-own-device (BYOD), możesz użyć opartego [](/azure/active-directory/conditional-access/app-based-conditional-access) na aplikacji dostępu warunkowego, aby zapobiec pobieraniu poufnych danych na osobiste urządzenia użytkowników.

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Jak oceniać uwierzytelnianie użytkownika i utrzymywać kontrolę nad jego uwierzytelnianiem podczas bezpośredniego nawiązywania połączenia?

Oprócz funkcji ograniczeń dzierżawy zanotowane w K1 [, można](/azure/active-directory/conditional-access/overview) zastosować zasady dostępu warunkowego w celu dynamicznej oceny ryzyka związanego z żądaniem uwierzytelniania i odpowiedniego reagowania. Firma Microsoft zaleca, aby [model Zero](https://www.microsoft.com/security/zero-trust?rtc=1) zaufania był implementowany z czasem i można używać zasad dostępu warunkowego usługi Azure AD w celu utrzymania kontroli w świecie przenośnym i w chmurze. Za pomocą zasad dostępu warunkowego można podjąć decyzję o pomyślnym uwierzytelnieniu w czasie rzeczywistym na podstawie wielu czynników, takich jak:

- Czy urządzenie jest przyłączone do nazwy/zaufanej/domeny?
- IP — czy żądanie uwierzytelnienia pochodzi ze znanego firmowego adresu IP? A może w kraju, do którym nie ufamy?
- Aplikacja — czy użytkownik jest autoryzowany do korzystania z tej aplikacji?

Następnie możemy uruchomić zasady, takie jak zatwierdzanie, wyzwalanie uwierzytelniania MFA lub blokowanie uwierzytelniania na podstawie tych zasad.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Jak chronić się przed wirusami i złośliwym oprogramowaniem?

Również ten Microsoft 365 zapewnia ochronę oznaczonych punktów końcowych Optymalizowanie na różnych warstwach samej usługi, opisanych [w tym dokumencie](/office365/Enterprise/office-365-malware-and-ransomware-protection). Jak wspomniano, znacznie skuteczniej jest dostarczać te elementy zabezpieczeń w samej usłudze, niż próbować robić to zgodnie z urządzeniami, które mogą nie w pełni rozumiać protokołów/ruchu. Domyślnie aplikacja SharePoint Online automatycznie [skanuje przekazywanie](../security/office-365-security/virus-detection-in-spo.md) plików w poszukiwaniu znanego złośliwego oprogramowania

W przypadku Exchange punktów końcowych wymienionych powyżej program [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) i [program Microsoft Defender dla systemu Microsoft 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) to doskonałe rozwiązanie do zapewniania bezpieczeństwa ruchu do usługi.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Czy mogę wysyłać nie tylko bezpośrednią optymalizację ruchu?

Priorytet powinien być nadany punktom końcowym oznaczonym jako **Optymalizuj** , ponieważ zapewni to maksymalną korzyść w przypadku niskiego poziomu pracy. Jednak w razie potrzeby do działania usługi wymagane są oznaczone punkty końcowe ze oznaczonymi adresami IP, które mogą być używane w razie potrzeby.

Istnieją również różni dostawcy, którzy oferują oparte na chmurze rozwiązania proxy/zabezpieczeń nazywane bezpiecznymi bramami sieci _Web_ , które zapewniają centralne zabezpieczenia, kontrolki i aplikację zasad firmy do ogólnego przeglądania Internetu. Te rozwiązania mogą działać dobrze w pierwszym świecie chmury, jeśli są wysoce dostępne, performantowe i zapewniane w pobliżu użytkowników, pozwalając na bezpieczny dostęp do Internetu z lokalizacji opartej na chmurze, blisko użytkownika. Dzięki temu nie będzie konieczne korzystanie ze spinki sieci VPN/firmowej do ogólnego ruchu przeglądania, a jednocześnie pozwoli na centralne sterowanie zabezpieczeniami.

Jednak nawet w przypadku tych rozwiązań firma Microsoft nadal zdecydowanie zaleca, aby optymalizować oznaczony Microsoft 365 jest wysyłany bezpośrednio do usługi.

Aby uzyskać wskazówki dotyczące zezwalania na bezpośredni dostęp do wirtualnej sieci Azure, zobacz Praca zdalna przy użyciu bezpośredniej witryny bramy [Azure VPN](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Dlaczego jest wymagany port 80? Czy ruch jest wysyłany w czytelny sposób?

Port 80 jest używany tylko do takich czynności, jak przekierowanie do sesji portu 443, żadne dane klienta nie są wysyłane ani nie są dostępne za pośrednictwem portu 80. [Szyfrowanie](../compliance/encryption.md) określa szyfrowanie danych podczas przesyłania i przechowywania danych dla sieci Microsoft 365, a typy ruchu są [](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) konspektami sposobu, w jaki używamy portali SRTP do Teams ruchu multimedialnego.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Czy ta porada dotyczy użytkowników w Chinach korzystających z globalnego wystąpienia Microsoft 365?

**Nie**, nie musi. Jedną z zastrzeżeniem powyższych porad są użytkownicy w ChRL, którzy naają połączenie z całym wystąpieniem Microsoft 365. Ze względu na typowe występowanie przeciążenia sieci przygranej w regionie wydajność bezpośredniego ruchu wychodzącego do Internetu może być zmienna. Większość klientów w regionie korzysta z połączenia VPN w celu przybliżania ruchu do sieci firmowej i korzysta z autoryzowanego obwodu MPLS lub podobnego do ruchu wychodzącego poza kraj za pośrednictwem zoptymalizowanej ścieżki. Opisano to dalej w artykule [Microsoft 365 optymalizacji wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>Czy konfiguracja z podziałem na Teams działa w przeglądarce?

Tak, z zastrzeżeniem. Większość Teams jest obsługiwana w przeglądarkach wymienionych w te [sposób: Pobierz klientów dla Microsoft Teams](/microsoftteams/get-clients#web-client).

Ponadto sieć Microsoft Edge **96** i więcej obsługuje rozdzielanie sieci VPN na ruch w komunikacji równorzędnej, włączając zasady [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled). Obecnie inne przeglądarki mogą nie obsługiwać rozdzielania sieci VPN dla ruchu równorzędnego.

## <a name="related-articles"></a>Artykuły pokrewne

[Omówienie: rozdzielanie sieci VPN na Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Microsoft 365 wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)
