---
title: Implementowanie tunelowania podzielonego sieci VPN dla platformy Microsoft 365
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
description: Jak zaimplementować tunelowanie podzielone sieci VPN dla platformy Microsoft 365
ms.openlocfilehash: 6b578b9b1801921644c6982c15c160bce5fbb4dd
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941091"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implementowanie tunelowania podzielonego sieci VPN dla platformy Microsoft 365

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji platformy Microsoft 365 dla użytkowników zdalnych.

>- Aby zapoznać się z omówieniem korzystania z tunelowania podzielonego sieci VPN w celu optymalizacji łączności platformy Microsoft 365 dla użytkowników zdalnych, zobacz [Omówienie: tunelowanie podzielone sieci VPN dla platformy Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółową listę scenariuszy tunelowania podzielonego sieci VPN, zobacz [Typowe scenariusze tunelowania podzielonego sieci VPN dla platformy Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać wskazówki dotyczące zabezpieczania ruchu multimedialnego usługi Teams w środowiskach tunelowania podzielonego sieci VPN, zobacz [Zabezpieczanie ruchu multimedialnego usługi Teams na potrzeby tunelowania podzielonego sieci VPN](microsoft-365-vpn-securing-teams.md).
>- Aby uzyskać informacje o sposobie konfigurowania strumienia i zdarzeń na żywo w środowiskach sieci VPN, zobacz [Specjalne zagadnienia dotyczące strumienia i zdarzeń na żywo w środowiskach sieci VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Aby uzyskać informacje na temat optymalizacji wydajności dzierżawy platformy Microsoft 365 na całym świecie dla użytkowników w Chinach, zobacz [Optymalizacja wydajności platformy Microsoft 365 dla chińskich użytkowników](microsoft-365-networking-china.md).

Zalecana przez firmę Microsoft strategia optymalizacji łączności zdalnego procesu roboczego koncentruje się na szybkim ograniczaniu problemów i zapewnianiu wysokiej wydajności przy użyciu kilku prostych kroków. Te kroki umożliwiają dostosowanie starszego podejścia do sieci VPN dla kilku zdefiniowanych punktów końcowych, które pomijają wąskie gardła serwerów sieci VPN. Równoważny lub nawet lepszy model zabezpieczeń można zastosować w różnych warstwach, aby usunąć konieczność zabezpieczania całego ruchu w ruchu wychodzącym sieci firmowej. W większości przypadków można to skutecznie osiągnąć w ciągu kilku godzin, a następnie jest skalowalne do innych obciążeń, zgodnie z zapotrzebowaniem na wymagania i czasem.

## <a name="implement-vpn-split-tunneling"></a>Implementowanie tunelowania podzielonego sieci VPN

W tym artykule znajdziesz proste kroki wymagane do migracji architektury klienta sieci VPN z _wymuszonego tunelu vpn_ do _wymuszonego tunelu vpn z kilkoma zaufanymi wyjątkami_, [model tunelu podzielonego sieci VPN nr 2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) w [typowych scenariuszach tunelowania podzielonego sieci VPN dla platformy Microsoft 365](microsoft-365-vpn-common-scenarios.md).

Na poniższym diagramie pokazano, jak działa zalecane rozwiązanie tunelu podzielonego sieci VPN:

![Szczegóły rozwiązania sieci VPN z tunelem podzielonym.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. Identyfikowanie punktów końcowych do optymalizacji

W artykule Dotyczącym [adresów URL i zakresów adresów IP platformy Microsoft 365](urls-and-ip-address-ranges.md) firma Microsoft jasno identyfikuje kluczowe punkty końcowe potrzebne do optymalizacji i kategoryzowania ich jako **optymalizowania**. Obecnie istnieją tylko cztery adresy URL i 20 podsieci IP, które należy zoptymalizować. Ta niewielka grupa punktów końcowych stanowi około 70% — 80% ruchu do usługi Microsoft 365, w tym punkty końcowe z uwzględnieniem opóźnień, takie jak te dla nośników usługi Teams. Zasadniczo jest to ruch, który musimy szczególnie zadbać, a także ruch, który wywrze niesamowitą presję na tradycyjne ścieżki sieciowe i infrastrukturę sieci VPN.

Adresy URL w tej kategorii mają następujące cechy:

- Czy punkty końcowe należące do firmy Microsoft i zarządzane są hostowane w infrastrukturze firmy Microsoft
- Podano adresy IP
- Niska szybkość zmian i oczekuje się, że pozostanie niewielka liczba (obecnie 20 podsieci IP)
- Czy przepustowość i/lub opóźnienie są wrażliwe
- Mogą mieć wymagane elementy zabezpieczeń udostępniane w usłudze, a nie wbudowane w sieci
- Stanowią około 70–80% ruchu do usługi Microsoft 365

Aby uzyskać więcej informacji na temat punktów końcowych platformy Microsoft 365 oraz sposobu ich kategoryzowania i zarządzania, zobacz [Zarządzanie punktami końcowymi platformy Microsoft 365](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>Optymalizowanie adresów URL

Bieżące adresy URL optymalizacji można znaleźć w poniższej tabeli. W większości przypadków należy używać tylko punktów końcowych adresu URL w [pliku PAC przeglądarki](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) , w którym punkty końcowe są skonfigurowane do wysyłania bezpośrednio, a nie do serwera proxy.

| Optymalizowanie adresów URL | Port/protokół | Celu |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Jest to jeden z podstawowych adresów URL używanych przez program Outlook do nawiązywania połączenia z serwerem usługi Exchange Online i ma duże użycie przepustowości i liczbę połączeń. Małe opóźnienie sieci jest wymagane w przypadku funkcji online, takich jak: wyszukiwanie błyskawiczne, inne kalendarze skrzynki pocztowej, bezpłatne/zajęte wyszukiwanie, zarządzanie regułami i alertami, archiwum online programu Exchange, wiadomości e-mail wychodzące ze skrzynki wychodzącej. |
| <https://outlook.office.com> | TCP 443 | Ten adres URL jest używany w przypadku programu Outlook Online Web Access do nawiązywania połączenia z serwerem usługi Exchange Online i jest wrażliwy na opóźnienie sieci. Łączność jest szczególnie wymagana w przypadku przekazywania i pobierania dużych plików za pomocą usługi SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Jest to podstawowy adres URL usługi SharePoint Online z użyciem wysokiej przepustowości. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Jest to podstawowy adres URL usługi OneDrive dla Firm, który ma wysokie użycie przepustowości i prawdopodobnie dużą liczbę połączeń z narzędzia synchronizacji usługi OneDrive dla Firm. |
| Adresy IP usługi Teams Media (bez adresu URL) | UDP 3478, 3479, 3480 i 3481 | Alokacja odnajdywania przekaźnika i ruch w czasie rzeczywistym. Są to punkty końcowe używane dla ruchu skype dla firm i usługi Microsoft Teams Media (wywołania, spotkania itp.). Większość punktów końcowych jest dostarczana, gdy klient usługi Microsoft Teams nawiązuje wywołanie (i znajduje się w wymaganych adresach IP wymienionych dla usługi). Korzystanie z protokołu UDP jest wymagane w celu uzyskania optymalnej jakości multimediów.   |

W powyższych przykładach **dzierżawa** powinna zostać zastąpiona nazwą dzierżawy platformy Microsoft 365. Na przykład **contoso.onmicrosoft.com** będzie używać _contoso.sharepoint.com_ i _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optymalizowanie zakresów adresów IP

W momencie pisania zakresów adresów IP, które odpowiadają tym punktom końcowym, są następujące. Bardzo **dobrze** zaleca się użycie [skryptu takiego jak ten](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) przykład, [usługa internetowa microsoft 365 ip i adres URL](microsoft-365-ip-web-service.md) lub [strona adresu URL/IP](urls-and-ip-address-ranges.md) w celu sprawdzenia dostępności aktualizacji podczas stosowania konfiguracji i wprowadzenia zasad w celu regularnego wykonywania tych czynności.

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

Teraz, po zidentyfikowaniu tych krytycznych punktów końcowych, musimy odwrócić je od tunelu sieci VPN i umożliwić mu użycie lokalnego połączenia internetowego użytkownika w celu nawiązania bezpośredniego połączenia z usługą. Sposób, w jaki jest to realizowane, będzie się różnić w zależności od używanego produktu sieci VPN i platformy maszynowej, ale większość rozwiązań sieci VPN pozwoli na zastosowanie tej logiki przy użyciu prostej konfiguracji zasad. Aby uzyskać informacje na temat wskazówek dotyczących tunelu podzielonego specyficznego dla platformy VPN, zobacz [przewodniki HOWTO dotyczące typowych platform sieci VPN](#howto-guides-for-common-vpn-platforms).

Jeśli chcesz przetestować rozwiązanie ręcznie, możesz wykonać następujący przykład programu PowerShell, aby emulować rozwiązanie na poziomie tabeli tras. W tym przykładzie do tabeli tras zostanie dodana trasa dla każdej podsieci adresu IP usługi Teams Media. Wydajność multimediów w usłudze Teams można testować przed i po oraz obserwować różnice w trasach dla określonych punktów końcowych.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Przykład: dodawanie podsieci adresów IP multimediów usługi Teams do tabeli tras

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

W powyższym skrypcie _$intIndex_ jest indeksem interfejsu połączonego z Internetem (znajdź, uruchamiając **polecenie get-netadapter** w programie PowerShell; poszukaj wartości _ifIndex_), a _$gateway_ jest bramą domyślną tego interfejsu (znajdź, uruchamiając **polecenie ipconfig** w wierszu polecenia lub **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** w programie PowerShell).

Po dodaniu tras można potwierdzić, że tabela tras jest poprawna, uruchamiając **drukowanie tras** w wierszu polecenia lub programie PowerShell. Dane wyjściowe powinny zawierać dodane trasy z indeksem interfejsu (_22_ w tym przykładzie) i bramą dla tego interfejsu (_192.168.1.1_ w tym przykładzie):

![Dane wyjściowe wydruku trasy.](../media/vpn-split-tunneling/vpn-route-print.png)

Aby dodać trasy dla _wszystkich_ bieżących zakresów adresów IP w kategorii Optymalizuj, możesz użyć następującej odmiany skryptu, aby wykonać zapytanie dotyczące [usługi internetowej adresów IP i adresów URL platformy Microsoft 365](microsoft-365-ip-web-service.md) dla bieżącego zestawu podsieci Optymalizuj adres IP i dodać je do tabeli tras.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Przykład: dodaj wszystkie podsieci Optymalizuj do tabeli tras

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

Jeśli przypadkowo dodano trasy z nieprawidłowymi parametrami lub po prostu chcesz przywrócić zmiany, możesz usunąć właśnie dodane trasy za pomocą następującego polecenia:

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

Klient sieci VPN powinien być skonfigurowany tak, aby ruch do **optymalizowanych** adresów IP był kierowany w ten sposób. Dzięki temu ruch może korzystać z lokalnych zasobów firmy Microsoft, takich jak microsoft 365 Service Front Door, [takich jak usługa Azure Front Door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/) , która dostarcza usługi Platformy Microsoft 365 i punkty końcowe łączności tak blisko użytkowników, jak to możliwe. Dzięki temu możemy zapewnić użytkownikom wysoki poziom wydajności wszędzie tam, gdzie są na świecie, i w pełni wykorzystać [światowej klasy globalną sieć firmy Microsoft](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), która prawdopodobnie znajduje się w ciągu kilku milisekund od bezpośredniego ruchu wychodzącego użytkowników.

## <a name="howto-guides-for-common-vpn-platforms"></a>Przewodniki HOWTO dla typowych platform sieci VPN

Ta sekcja zawiera linki do szczegółowych przewodników implementowania tunelowania podzielonego dla ruchu platformy Microsoft 365 od najpopularniejszych partnerów w tej przestrzeni. Dodamy dodatkowe przewodniki w miarę ich udostępniania.

- **Klient sieci VPN systemu Windows 10**: [optymalizowanie ruchu platformy Microsoft 365 dla pracowników zdalnych przy użyciu natywnego klienta sieci VPN systemu Windows 10](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [Optymalizowanie tunelu podziału połączeń dla usługi Office 365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [Optymalizowanie ruchu na platformie Microsoft 365 za pośrednictwem połączenia VPN Split Tunnel Exclude Access Route](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: [Optymalizowanie ruchu platformy Microsoft 365 w przypadku dostępu zdalnego za pośrednictwem sieci VPN podczas korzystania z modułu APM BIG-IP](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix Gateway**: [Optymalizowanie tunelu podziału sieci VPN usługi Citrix Gateway dla usługi Office365](https://docs.citrix.com/en-us/citrix-gateway/current-release/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [Tunelowanie vpn: jak skonfigurować tunelowanie podzielone w celu wykluczenia aplikacji platformy Microsoft 365](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Sieć VPN punktu kontrolnego**: [jak skonfigurować split tunnel dla platformy Microsoft 365 i innych aplikacji SaaS](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>Powiązane artykuły:

[Omówienie: tunelowanie podzielone sieci VPN dla platformy Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Typowe scenariusze tunelowania podzielonego sieci VPN dla platformy Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Zabezpieczanie ruchu multimediów aplikacji Teams na potrzeby tunelowania podziału sieci VPN](microsoft-365-vpn-securing-teams.md)

[Specjalne zagadnienia dotyczące strumienia i wydarzeń na żywo w środowiskach sieci VPN](microsoft-365-vpn-stream-and-live-events.md)

[Optymalizacja wydajności platformy Microsoft 365 dla chińskich użytkowników](microsoft-365-networking-china.md)

[Zasady łączności sieciowej platformy Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Ocena łączności sieciowej na platformie Microsoft 365](assessing-network-connectivity.md)

[Dostrajanie sieci i wydajności platformy Microsoft 365](network-planning-and-performance.md)

[Alternatywne sposoby zapewniania przez specjalistów ds. zabezpieczeń i działów IT nowoczesnych mechanizmów kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu ds. zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: używanie profilów sieci VPN systemu Windows 10 w celu umożliwienia połączeń automatycznych](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Uruchamianie w sieci VPN: jak firma Microsoft utrzymuje połączenie ze swoimi zdalnymi pracownikami](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
