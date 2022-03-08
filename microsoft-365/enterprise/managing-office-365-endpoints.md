---
title: Zarządzanie Office 365 punktami końcowymi
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Dowiedz się, jak zarządzać punktami Office 365 końcowymi, aby działały one z architekturą sieci organizacji przedsiębiorstwa.
ms.openlocfilehash: 5d5e51b789ef0336a2e7aaa6a923ca2957ea6edf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314535"
---
# <a name="managing-office-365-endpoints"></a>Zarządzanie Office 365 punktami końcowymi

Większość przedsiębiorstw z wieloma lokalizacjami biur i siecią WAN łączącą się z siecią WAN będzie potrzebować konfiguracji na potrzeby Office 365 sieciowej. Sieć można zoptymalizować, wysyłając wszystkie zaufane żądania Office 365 sieciowych bezpośrednio przez zaporę z pominięciem wszelkiego dodatkowego przetwarzania i inspekcji na poziomie pakietów. Zmniejsza to opóźnienia i wymagania dotyczące pojemności sieci obwodowej. Identyfikowanie Office 365 sieciowego jest pierwszym krokiem w celu zapewnienia użytkownikom optymalnej wydajności. Aby uzyskać więcej informacji, [Office 365 zasady łączności sieciowej](microsoft-365-network-connectivity-principles.md).

Firma Microsoft zaleca uzyskiwanie dostępu do punktów końcowych Office 365 sieci i bieżących zmian w nich przy użyciu usługi sieci Web Office 365 adresów [IP i adresów URL](microsoft-365-ip-web-service.md).

Niezależnie od tego, jak zarządzasz ważnymi Office 365 sieciowym, Office 365 wymagana jest łączność internetowa. Inne punkty końcowe sieci, w których wymagana jest łączność, znajdują się w polu Dodatkowe punkty końcowe nieujętne w usłudze sieci [Office 365 ip i adresie URL usługi sieci Web](additional-office365-ip-addresses-and-urls.md).

Sposób korzystania z Office 365 sieciowych będzie zależny od architektury sieci organizacji przedsiębiorstwa. W tym artykule przedstawiono kilka sposobów integracji architektury sieci przedsiębiorstwa z adresami IP Office 365 ADRESAMI URL i adresami URL. Najprostszym sposobem wybrania zaufanych żądań sieciowych jest użycie urządzeń SD-WAN, które obsługują automatyczną Office 365 konfiguracji w każdej z lokalizacji biura.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SD-WAN do lokalnego ruchu wychodzącego gałęzi kluczowego Office 365 ruchu sieciowego

W każdej lokalizacji oddziału możesz udostępnić urządzenie SD-WAN skonfigurowane do rozsyłania ruchu dla punktów końcowych w kategorii Office 365 Optymalizuj kategorię punktów końcowych lub Optymalizuj i zezwalaj na kategorie bezpośrednio do sieci firmy Microsoft. Inny ruch sieciowy, w tym ruch lokalnego centrum danych, ogólny ruch witryn internetowych oraz ruch do Office 365 Domyślne punkty końcowe kategorii są wysyłane do innej lokalizacji, w której masz bardziej znaczące obwody sieci.

Firma Microsoft współpracuje z dostawcami sd-WAN, aby włączyć automatyczną konfigurację. Aby uzyskać więcej informacji, zobacz [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Używanie pliku PAC do bezpośredniego routingu najważniejszych Office 365 ruchu

Pliki PAC lub WPAD zarządzają żądaniami sieciowym, które są skojarzone Office 365 ale nie mają adresu IP. Typowe żądania sieciowe wysyłane przez serwer proxy lub urządzenie obwodowe zwiększają opóźnienia. Natomiast podział SSL i inspekcja tworzą największe opóźnienie, natomiast inne usługi, takie jak uwierzytelnianie serwera proxy i wyszukiwania reputacji, mogą powodować niską wydajność i słabe działanie użytkownika. Ponadto te urządzenia sieci obwodowej muszą mieć pojemność wystarczającą do przetwarzania wszystkich żądań połączeń sieciowych. Zalecamy pomijanie serwera proxy lub urządzeń do inspekcji w przypadku bezpośrednich Office 365 żądań sieciowych.
  
[Galeria programu PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) to skrypt programu PowerShell, który odczytuje najnowsze punkty końcowe sieci z usługi sieci web programu Office 365 Adres IP i adres URL oraz tworzy przykładowy plik PAC. Skrypt można zmodyfikować tak, aby był zintegrowany z istniejącym zarządzaniem plikami PAC.

![Łączenie się Office 365 przez zapory i proxy.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Rysunek 1. Prosty obwód sieci przedsiębiorstwa**

Plik PAC został wdrożony w przeglądarkach sieci Web w punkcie 1 na rysunku 1. W przypadku używania pliku PAC do bezpośredniego ruchu wychodzącego kluczowego Office 365 sieciowego należy również zezwolić na łączność z adresami IP, które są za pośrednictwem tych adresów URL w zaporze obwodowej sieci. Jest to wykonywane przez pobieranie adresów IP dla tych samych kategorii punktów Office 365 określonych w pliku PAC i tworzenie na ich podstawie plików ACL zapory. Zapora to punkt 3 na rysunku 1.

Oddzielnie, jeśli wybierzesz routing bezpośredni tylko dla punktów końcowych kategorii Optymalizowanie, wszelkie wymagane punkty końcowe kategorii Zezwalaj, które wysyłasz do serwera proxy, muszą być wymienione na serwerze proxy, aby pominąć dalsze przetwarzanie. Na przykład podział SSL oraz inspekcja i uwierzytelnianie serwera proxy są niezgodne zarówno z punktami końcowymi kategorii Optymalizuj, jak i Zezwalaj. Serwer proxy ma punkt 2 na rysunku 1.

Wspólną konfiguracją jest zezwolenie bez przetwarzania całego ruchu wychodzącego z serwera proxy dla docelowych adresów IP dla Office 365 sieciowego, który trafia do serwera proxy. Aby uzyskać informacje na temat problemów z przerwą SSL i inspekcją, zobacz Używanie urządzeń sieciowych innych firm lub rozwiązań [w Office 365 ruchu.](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)

Istnieją dwa typy plików PAC, które zostanie Get-PacFile w skrypcie.

| Wpisać | Opis |
|:-----|:-----|
|**1** <br/> |Wyślij bezpośrednią optymalizację ruchu punktu końcowego i wszystkie inne informacje do serwera proxy. <br/> |
|**2** <br/> |Wyślij oprogramowanie Optimize (Optymalizuj) i Allow endpoint traffic direct (Zezwalaj na ruch bezpośredni) i wszystkie inne dane do serwera proxy. Za pomocą tego typu można również wysyłać wszystkie obsługiwane usługi ExpressRoute na Office 365 do segmentów sieci usługi ExpressRoute i wszystkich innych części do serwera proxy. <br/> |

Oto prosty przykład wywoływania skryptu programu PowerShell:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Istnieje wiele parametrów, które można przekazać do skryptu:

| Parametr | Opis |
|:-----|:-----|
|**ClientRequestId** <br/> |Jest to wymagane i jest identyfikatorEM GUID przekazywanym do usługi sieci Web reprezentującej komputer kliencki wywołujący. <br/> |
|**Wystąpienie** <br/> |To Office 365 wystąpienia usługi, które domyślnie ma wartość Worldwide. Te informacje są również przekazywane do usługi sieci Web. <br/> |
|**TenantName** <br/> |Twoja Office 365 dzierżawy. Przekazywane do usługi sieci Web i używane jako parametr wymień w niektórych Office 365 URL. <br/> |
|**Type** <br/> |Typ pliku PAC serwera proxy, który ma zostać wygenerowany. <br/> |

Oto kolejny przykład wywoływania skryptu programu PowerShell z dodatkowymi parametrami:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Przetwarzanie ruchu sieciowego na Office 365 serwera proxy

Jeśli pliki PAC nie są używane do kierowania ruchu wychodzącego, mimo to chcesz pominąć przetwarzanie w obwodzie sieci, konfigurując serwer proxy. Niektórzy dostawcy serwera proxy włączyli automatyczną konfigurację tej funkcji zgodnie z opisem [w](microsoft-365-networking-partner-program.md) Office 365 Networking Partner Program.

Jeśli wykonujesz to ręcznie, musisz pobrać dane kategorii Optymalizowanie i Zezwalaj na punkt końcowy z usługi sieci Web adresów IP i adresów URL usługi Office 365 oraz skonfigurować serwer proxy tak, aby pomijał przetwarzanie tych wartości. Należy unikać przerwy SSL i sprawdzania oraz uwierzytelniania serwera proxy dla punktów końcowych kategorii Optymalizowanie i Zezwalaj.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Zarządzanie zmianami w Office 365 IP i adresach URL

Oprócz wybrania odpowiedniej konfiguracji dla obwodu sieci bardzo ważne jest przyjęcie procesu zarządzania zmianami dla Office 365 końcowych. Te punkty końcowe zmieniają się regularnie i jeśli nie zarządzasz zmianami, możesz zakończyć się zablokowaniem użytkowników lub niską wydajnością po dodaniu nowego adresu IP lub adresu URL.

Zmiany adresów IP Office 365 URL są zwykle publikowane w pobliżu ostatniego dnia każdego miesiąca. Czasami zmiana zostanie opublikowana poza tym harmonogramem ze względu na wymagania operacyjne, techniczne lub związane z zabezpieczeniami.

Po opublikowaniu zmiany, która wymaga działania z powodu dodania adresu IP lub adresu URL, należy oczekiwać, że otrzymasz 30-dniowe powiadomienie od czasu opublikowania przez nas zmiany do momentu opublikowania usługi Office 365 dla tego punktu końcowego. Jest to odzwierciedlane jako data wejścia w życie. Chociaż celem jest dla nas okres powiadamiania, nie zawsze jest to możliwe ze względu na wymagania operacyjne, techniczne lub związane z zabezpieczeniami. Zmiany, które nie wymagają natychmiastowego działania w celu utrzymania łączności, takie jak usunięte adresy IP lub adresy URL lub mniej istotnych zmian, nie obejmują wcześniejszego powiadomienia. W takich przypadkach nie jest dostarczana data wejścia w życie. Niezależnie od tego, jakie powiadomienie zostanie dostarczone, dla każdej zmiany podano oczekiwaną datę aktywnej usługi.

### <a name="change-notification-using-the-web-service"></a>Zmienianie powiadomień przy użyciu usługi sieci Web

Aby uzyskać powiadomienie o zmianie, możesz Office 365 adres IP i usługę sieci Web adresu URL. Zalecamy, aby raz na godzinę wywołać metodę **sieci Web /version** w celu sprawdzenia wersji punktów końcowych, których używasz do łączenia się z usługą Office 365. Jeśli ta wersja zmieni się w porównaniu z używaną wersją, należy pobrać najnowsze dane punktu końcowego z metody sieci Web **/endpoints** i opcjonalnie uzyskać różnice z metody sieci Web **/changes** . Nie jest konieczne wywołanie metod sieci Web **/endpoints** **lub /changes** , jeśli nie wszły zmiany w odnalezionej wersji.

Aby uzyskać więcej informacji, zobacz [Office 365 adres IP i usługa sieci Web adresu URL](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Zmienianie powiadomień przy użyciu kanałów informacyjnych RSS

Usługa Office 365 adresu IP i adresu URL usługi sieci Web udostępnia kanał informacyjny RSS, który można zasubskrybować w Outlook. Na każdej ze stron wystąpienia usługi usługi Office 365 znajdują się linki do adresów URL i adresów URL źródeł danych RSS. Aby uzyskać więcej informacji, zobacz [Office 365 adres IP i usługa sieci Web adresu URL](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Zmienianie powiadomień i recenzji zatwierdzania przy Power Automate

Rozumiemy, że nadal możesz wymagać ręcznego przetwarzania dla zmian punktu końcowego sieci, które mogą wystąpić co miesiąc. Możesz użyć programu Power Automate utworzyć przepływ, który powiadamia Cię pocztą e-mail i opcjonalnie uruchamia proces zatwierdzania zmian, gdy Office 365 punkty końcowe sieci mają zmiany. Po zakończeniu przeglądu możesz automatycznie wysłać zmiany do zespołu zarządzającego zaporą i serwerem proxy w wiadomości e-mail.

Aby uzyskać informacje na Power Automate i szablon, zobacz Otrzymywanie wiadomości e Power Automate e-mail na temat zmian w adresach IP i Office 365 [URL](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 punktów końcowych sieci — często zadawane pytania

Zobacz te często zadawane pytania dotyczące Office 365 sieci.
  
### <a name="how-do-i-submit-a-question"></a>Jak przesłać pytanie?

Kliknij link u dołu, aby wskazać, czy artykuł był pomocny, i prześlij wszelkie dodatkowe pytania. Monitorujemy opinie i aktualizujemy tu pytania o najczęściej zadawane.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Jak ustalić lokalizację mojej dzierżawy?

 **Lokalizację dzierżawy** najlepiej ustalić przy użyciu [naszej mapy centrum danych](./o365-data-locations.md).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Czy komunikacja równorzędna z firmą Microsoft jest odpowiednia?

 **Lokalizacje komunikacji równorzędnej** opisano bardziej szczegółowo w komunikacji [równorzędnej z firmą Microsoft](https://www.microsoft.com/peering).
  
Globalne i 70 punktów obecności dzięki ponad 2500 relacjom komunikacji równorzędnej z naszymi sieciami powinno być bezproblemowe. Nie szkodzi poświęcić kilka minut na upewnienie się, że relacja komunikacji równorzędnej twojego internetowego jest najbardziej optymalna [. Oto](/archive/blogs/onthewire/__guidance) kilka przykładów dobrych i niespodziewnych komunikacji równorzędnych w naszej sieci.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Widzę żądania sieciowe dotyczące adresów IP, których nie ma na opublikowanej liście. Czy muszę zapewnić do nich dostęp?

Zapewniamy adresy IP tylko dla tych Office 365, do których należy bezpośrednio przekierowywować adresy IP. Nie jest to pełna lista wszystkich adresów IP, pod które widać żądania sieciowe. Będą na przykład żądania sieciowe do nieopublikowanego adresu IP należącego do firmy Microsoft lub innej firmy. Te adresy IP są generowane dynamicznie lub zarządzane w sposób uniemożliwiający terminowe powiadomienia o ich zmianie. Jeśli zapora nie zezwala na dostęp dla tych żądań sieciowych na podstawie nazwy FQNS, zarządzaj żądaniami przy użyciu pliku PAC lub WPAD.
  
Widzisz skojarzony z siecią adres IP Office 365 o którym chcesz uzyskać więcej informacji?
  
1. Sprawdź, czy adres IP nie znajduje się w większym opublikowanym zakresie przy użyciu kalkulatora CIDR, na przykład dla protokołu [IPv4](https://www.ipaddressguide.com/cidr) [lub IPv6](https://www.ipaddressguide.com/ipv6-cidr). Na przykład adres IP 40.10.96.0.0/13 zawiera adres IP 40.103.0.1 mimo tego, że wartości 40,96 nie są zgodne z wartością 40.103.
2. Sprawdź, czy partner nie jest właścicielem adresu IP za pomocą zapytania [whois](https://dnsquery.org/). Jeśli należy on do firmy Microsoft, być może jest partnerem wewnętrznym. Wiele punktów końcowych sieci partnerskiej jest wymienionych jako należących do kategorii _domyślnej_ , dla których adresy IP nie są publikowane.
3. Adres IP nie może być częścią Office 365 ani zależności. Office 365 punktów końcowych sieci nie zawiera wszystkich punktów końcowych sieci firmy Microsoft.
4. Sprawdź certyfikat. Za pomocą przeglądarki połącz się z adresem IP, używając programu  *HTTPS://\<IP_ADDRESS\>* i sprawdź domeny wymienione w certyfikacie, aby zrozumieć, które domeny są skojarzone z tym adresem IP. Jeśli ten adres IP należy do firmy Microsoft, Office 365 nie znajduje się na liście adresów IP, prawdopodobnie jest skojarzony z usługą Microsoft CDN, taką *jak MSOCDN.NET*, lub inną domeną firmy Microsoft, dla której nie ma opublikowanych informacji o adresie IP. Jeśli znajdziesz domenę na certyfikacie, którego używamy do wywłasniania adresu IP, pomów nas o tym.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Niektóre Office 365 URL wskazują rekordy CNAME zamiast rekordów A w systemie DNS. Co muszę zrobić z rekordami CNAME?

Komputery klienckie potrzebują rekordu DNS A lub AAAA, który zawiera co najmniej jeden adres IP, aby połączyć się z usługą w chmurze. Niektóre adresy URL zawarte w Office 365 zamiast rekordów A lub AAAA są wyświetlane w rekordach CNAME. Te rekordy CNAME są pośrednie i może być ich wiele w łańcuchu. Zawsze będą one zawsze rozpoznają rekord A lub AAAA dla adresu IP. Rozważ na przykład następującą serię rekordów DNS, która ostatecznie rozwiązuje problem z adresem IP _IP_1_:

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Te przekierowywania CNAME są normalną częścią systemu DNS i są przezroczyste dla klienta oraz przezroczyste dla serwerów proxy. Są one używane do równoważenia obciążenia, sieci dostarczania zawartości, wysokiej dostępności i zaradczego wpływu zdarzeń usługi. Firma Microsoft nie publikuje pośrednich rekordów CNAME, które mogą ulec zmianie w dowolnym momencie i nie trzeba ich konfigurować jako dozwolonych na serwerze proxy.

Serwer proxy sprawdza początkowy adres URL( w powyższym przykładzie jest serviceA.office.com adres URL, który zostałby uwzględniony w Office 365 publikowania. Serwer proxy żąda rozwiązania DNS dla tego adresu URL dla adresu IP i otrzyma IP_1. Nie są sprawdzane pośrednie rekordy przekierowywania CNAME.

Konfiguracje zakodowane lub używanie listy zezwalania opartej na pośrednich Office 365 nie jest zalecane (nie jest obsługiwane przez firmę Microsoft) i wiadomo, że powodują problemy z łącznością z klientami. Rozwiązania DNS, które blokują przekierowywanie CNAME lub które w inny sposób niepoprawnie rozpoznają wpisy DNS Office 365, można rozwiązać za pośrednictwem usługi przesyłania dalej DNS z włączoną powtarzaniem dns lub za pomocą wskazówek głównych systemu DNS. Wiele produktów obwodu sieci innych firm natywnie integruje zalecane Office 365 sieci Web, aby uwzględnić listę zezwalań w swojej konfiguracji przy użyciu usługi sieci Web adresów IP i adresów [URL](microsoft-365-ip-web-service.md) firmy Office 365.

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Dlaczego w nazwach domen firmy Microsoft są nsatc.net lub akadns.net, takie jak nazwa domeny firmy Microsoft?

Office 365 usługi usługi firmy Microsoft usługi innych firm, takie jak Akamai i MarkMonitor, aby ulepszyć Twoje Office 365 usługi. Aby nadal zapewniać Ci jak najlepsze możliwości, możemy zmieniać te usługi w przyszłości. W domenach innych firm może być hostna zawartość, taka CDN, lub usługi, takie jak usługa zarządzania ruchem geograficznym. Niektóre usługi, które są obecnie używani, to:
  
[MarkMonitor](https://www.markmonitor.com/) jest w użyciu, gdy widzisz żądania, które zawierają  *\*nsatc.net*. Ta usługa udostępnia funkcje ochrony i monitorowania nazw domen w celu ich zabezpieczenia przed złośliwym zachowaniem.
  
[ExactTarget](https://www.marketingcloud.com/) jest w użyciu, gdy widzisz *żądania dotyczące exacttarget.com\**. Ta usługa udostępnia funkcje zarządzania linkami w wiadomościach e-mail i monitorowania ich w celu ochrony przed złośliwym zachowaniem.
  
[Firma Akamai](https://www.akamai.com/) jest w użyciu, gdy widzisz żądania, które zawierają jedną z następujących FQDN. Ta usługa oferuje usługi DNS geolokalizacji oraz usługi sieci dostarczania zawartości.
  
```console
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Muszę mieć minimalną możliwą łączność dla Office 365

Ponieważ Office 365 to pakiet usług stworzonych do działania za pośrednictwem Internetu, zapewnianie niezawodności i dostępności opiera się na wielu dostępnych standardowych usługach internetowych. Na przykład standardowe usługi internetowe, takie jak DNS, CRL i sieci CDN, muszą być osiągalne, aby można było używać sieci Office 365, tak jak muszą być osiągalne, aby można było korzystać z większości nowoczesnych usług internetowych.

Pakiet Office 365 jest podzielone na główne obszary usługi. Można je selektywnie włączyć dla łączności, a istnieje obszar Wspólny, który jest współzależnością dla wszystkich i jest zawsze wymagany.

| Obszar usługi | Opis |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online i Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online i OneDrive dla Firm <br/> |
|**Skype dla firm Online i Microsoft Teams** <br/> |Skype dla firm i Microsoft Teams <br/> |
|**Typowe** <br/> |Office 365 Pro Plus, Office w przeglądarce, usłudze Azure AD i innych typowych punktach końcowych sieci. <br/> |

Oprócz podstawowych usług internetowych istnieją usługi innych firm, które służą tylko do integracji funkcji. Ponieważ są one wymagane na potrzeby integracji, są one oznaczone jako opcjonalne w artykule z punktami końcowymi usługi Office 365, co oznacza, że podstawowa funkcjonalność usługi będzie nadal działać, jeśli punkt końcowy nie będzie dostępny. Każdy wymagany punkt końcowy sieci będzie miał wymagany atrybut ustawiony na wartość true. Każdy opcjonalny punkt końcowy sieci będzie miał wymagany atrybut ustawiony na wartość false, a atrybut notatek będzie wyszczególnić brakujące funkcje, których należy oczekiwać w przypadku zablokowania łączności.
  
Jeśli próbujesz używać programu Office 365 i znajdują się usługi innych firm są niedostępne, upewnij się, że wszystkie usługi [FQDN](urls-and-ip-address-ranges.md) oznaczone w tym artykule jako wymagane lub opcjonalne są dozwolone przez serwer proxy i zaporę.
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Jak zablokować dostęp do usług firmy Microsoft dla klientów konsumenckich?

Funkcja ograniczeń dzierżawy obsługuje teraz blokowanie używania wszystkich aplikacji firmy Microsoft dla klientów konsumenckich (aplikacji MSA), takich jak OneDrive, Hotmail i Xbox.com. W ten sposób jest używany osobny nagłówek do login.live.com końcowego. Aby uzyskać więcej szczegółowych informacji, [zobacz Używanie ograniczeń dzierżawy do zarządzania dostępem do aplikacji w chmurze SaaS](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Moja zapora wymaga adresów IP i nie może przetwarzać adresów URL. Jak skonfigurować go do Office 365?

Office 365 nie zawiera adresów IP wszystkich wymaganych punktów końcowych sieci. Niektóre z nich są dostarczane tylko jako adresy URL i są domyślnie skategoryzowane. Adresy URL w kategorii domyślnej, które są wymagane, powinny być dozwolone za pośrednictwem serwera proxy. Jeśli nie masz serwera proxy, sprawdź, jak skonfigurowano żądania sieci Web adresów URL wpisywanych przez użytkowników na pasku adresu w przeglądarce sieci Web. użytkownik również nie poda adresu IP. Domyślne Office 365 URL kategorii, które nie zapewniają adresów IP, należy skonfigurować w taki sam sposób.

## <a name="related-topics"></a>Tematy pokrewne

[Office 365 adresu IP i usługi sieci Web adresu URL](microsoft-365-ip-web-service.md)

[Microsoft Azure IP centrum danych](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Publiczny obszar adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Wymagania dotyczące infrastruktury sieci Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute i Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)
  
[Zarządzanie łącznością sieciową za Office 365 ExpressRoute](managing-expressroute-for-connectivity.md)
  
[Office 365 zasad łączności sieciowej](microsoft-365-network-connectivity-principles.md)
