---
title: Implementowanie rozdzielania sieci VPN na Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
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
ms.openlocfilehash: ee8c0929682370d581c9d1b5c738d682d3f91a01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320441"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implementowanie rozdzielania sieci VPN na Microsoft 365

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji Microsoft 365 zdalnych.

>- Aby uzyskać omówienie korzystania z rozdzielania dzielonego sieci VPN w celu zoptymalizowania Microsoft 365 dla użytkowników zdalnych, zobacz Omówienie: rozdzielanie sieci VPN dla sieci [Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółową listę scenariuszy rozdzielania rozdzielania sieci VPN, zobacz Typowe scenariusze rozdzielania sieci [VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać wskazówki dotyczące zabezpieczania Teams ruchu multimedialnego w środowiskach rozdzielanych sieci VPN, zobacz Zabezpieczanie sieci Teams sieci multimedialnej na Teams [sieci VPN](microsoft-365-vpn-securing-teams.md).
>- Aby uzyskać informacje na temat konfigurowania usługi Stream i zdarzeń na żywo w środowiskach VPN, zobacz Szczególne zagadnienia dotyczące przesyłania strumieniowego i wydarzeń na żywo w [środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Aby uzyskać informacje na temat optymalizowania Microsoft 365 wydajności dzierżawy na całym świecie dla użytkowników w Chinach, zobacz Microsoft 365 [optymalizację wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

Zalecana przez firmę Microsoft strategia optymalizacji łączności pracowników zdalnych skupia się na szybkim ograniczaniem problemów i zapewnieniu wysokiej wydajności, przy użyciu kilku prostych kroków. Te kroki obejmują dostosowanie starszego podejścia sieci VPN dla kilku zdefiniowanych punktów końcowych, które pomijają wąskie gardła serwerów VPN. Równoważny lub nawet doskonały model zabezpieczeń można stosować na różnych warstwach w celu usunięcia konieczności zabezpieczenia całego ruchu na ruchu wychodzącym z sieci firmowej. W większości przypadków można to efektywnie zrealizować w ciągu godzin, a następnie można to skalować do innych obciążeń tak, jak pozwala na to wymaganie i czas.

## <a name="implement-vpn-split-tunneling"></a>Implementowanie rozdzielania sieci VPN

W tym artykule znajdziesz proste czynności wymagane do przeprowadzenia migracji architektury klienta VPN z wymuszonego połączenia VPN do wymuszonego klienta sieci _VPN_ z kilkoma zaufanymi wyjątkami, model rozdzielany [vpn #2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) w typowych scenariuszach rozdzielania sieci _VPN_ dla sieci [Microsoft 365](microsoft-365-vpn-common-scenarios.md).

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
| Teams i/lub adresy IP plików multimedialnych (bez adresu URL) | UDP 3478, 3479, 3480 i 3481 | Alokacja odnajdowania przekazywania i ruch w czasie rzeczywistym. Są to punkty końcowe używane do przesyłania Skype dla firm sieci Microsoft Teams multimediów (połączeń, spotkań itp.). Większość punktów końcowych jest dostarczana, gdy Microsoft Teams nawiązuje połączenie (i są zawarte w wymaganych dla usługi punktach IP). Użycie protokołu UDP jest wymagane do zapewnienia optymalnej jakości multimediów.   |

W powyższych przykładach **dzierżawę** należy zastąpić nazwą Microsoft 365 dzierżawy. Na przykład **contoso.onmicrosoft.com** użyć funkcji _contoso.sharepoint.com_ i _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optymalizowanie zakresów adresów IP

W chwili pisania zakresów adresów IP, z których odpowiadają te punkty końcowe, są następujące. Zdecydowanie zaleca się  używanie skryptu, takiego jak ten [](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) przykład, usługi sieci Web [adresów IP i URL usługi Microsoft 365](microsoft-365-ip-web-service.md) lub strony adres [URL/IP](urls-and-ip-address-ranges.md) w celu sprawdzenia, czy są dostępne aktualizacje podczas stosowania konfiguracji, i regularne stosowanie zasad.

```markdown
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

## <a name="howto-guides-for-common-vpn-platforms"></a>Przewodniki HOWTO dotyczące typowych platform VPN

Ta sekcja zawiera linki do szczegółowych przewodników implementowania rozdzielania Microsoft 365 sieciowego od najbardziej typowych partnerów w tym miejscu. Po ich dodaniu dodamy kolejne przewodniki.

- **Windows 10 VPN**: Optymalizowanie ruchu sieci Microsoft 365 pracowników zdalnych przy użyciu [natywnego Windows 10 VPN](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [Optymalizowanie podziału usługi Anyconnect Tunnel pod kątem usługi Office365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **GlobalProtect, Palo Alto**: [Optymalizowanie ruchu Microsoft 365 przez sieć VPN Tunnel wykluczanie trasy dostępu](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: Optymalizowanie ruchu w Microsoft 365 dostępu zdalnego za pośrednictwem [sieci VPN w przypadku używania usługi BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Brama Citrix**: [Optymalizowanie klienta VPN bramy Citrix dla usługi Office365](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: Szyfrowanie [sieci VPN: jak skonfigurować rozdzielanie w celu wykluczenia Microsoft 365 aplikacji](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Check Point VPN**: [How to configure Split Tunnel for Microsoft 365 and other SaaS Applications](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>Artykuły pokrewne

[Omówienie: rozdzielanie sieci VPN na Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Typowe scenariusze rozdzielania sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN](microsoft-365-vpn-securing-teams.md)

[Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md)

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
