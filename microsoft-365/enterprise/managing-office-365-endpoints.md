---
title: Zarządzanie punktami końcowymi usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak zarządzać punktami końcowymi Office 365, aby działały z architekturą sieci organizacji przedsiębiorstwa.
ms.openlocfilehash: 6743ab1c3241b84b0eb1dd3e9f5e67e100e18b40
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090346"
---
# <a name="managing-office-365-endpoints"></a>Zarządzanie punktami końcowymi usługi Office 365

Większość organizacji przedsiębiorstwa, które mają wiele lokalizacji biurowych i łączącą się sieć WAN, będzie potrzebować konfiguracji Office 365 łączności sieciowej. Sieć można zoptymalizować, wysyłając wszystkie zaufane żądania sieciowe Office 365 bezpośrednio za pośrednictwem zapory, pomijając wszystkie dodatkowe inspekcje lub przetwarzanie na poziomie pakietów. Zmniejsza to opóźnienia i wymagania dotyczące pojemności obwodowej. Identyfikowanie ruchu sieciowego Office 365 jest pierwszym krokiem zapewniania optymalnej wydajności dla użytkowników. Aby uzyskać więcej informacji, zobacz [Office 365 Zasady łączności sieciowej](microsoft-365-network-connectivity-principles.md).

Firma Microsoft zaleca dostęp do punktów końcowych sieci Office 365 i bieżących zmian w nich przy użyciu [Office 365 adresu IP i usługi sieci Web adresu URL](microsoft-365-ip-web-service.md).

Niezależnie od sposobu zarządzania istotnym ruchem sieciowym Office 365, Office 365 wymaga łączności z Internetem. Inne punkty końcowe sieci, w których wymagana jest łączność, są wymienione w [temacie Dodatkowe punkty końcowe, które nie są uwzględnione w usłudze sieci Web Office 365 adresów IP i adresów URL](additional-office365-ip-addresses-and-urls.md).

Sposób korzystania z punktów końcowych sieci Office 365 będzie zależeć od architektury sieci organizacji przedsiębiorstwa. W tym artykule opisano kilka sposobów integracji architektur sieci przedsiębiorstwa z Office 365 adresami IP i adresami URL. Najprostszym sposobem wybrania zaufanych żądań sieciowych jest użycie urządzeń SD-WAN, które obsługują zautomatyzowaną konfigurację Office 365 w każdej lokalizacji biura.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SD-WAN dla lokalnego ruchu wychodzącego gałęzi o istotnych Office 365 ruchu sieciowego

W każdej lokalizacji oddziału można podać urządzenie SD-WAN skonfigurowane do kierowania ruchu dla Office 365 Optymalizowanie kategorii punktów końcowych lub Optymalizowanie i zezwalanie na kategorie bezpośrednio do sieci firmy Microsoft. Inny ruch sieciowy, w tym ruch w lokalnym centrum danych, ogólny ruch witryn internetowych i ruch do Office 365 domyślnych punktów końcowych kategorii jest wysyłany do innej lokalizacji, w której masz bardziej znaczący obwód sieci.

Firma Microsoft współpracuje z dostawcami usług SD-WAN w celu włączenia zautomatyzowanej konfiguracji. Aby uzyskać więcej informacji, zobacz [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Używanie pliku PAC do bezpośredniego routingu istotnego ruchu Office 365

Użyj plików PAC lub WPAD, aby zarządzać żądaniami sieciowymi skojarzonymi z Office 365 ale nie mają adresu IP. Typowe żądania sieciowe wysyłane za pośrednictwem serwera proxy lub urządzenia obwodowego zwiększają opóźnienie. Podczas gdy funkcja SSL Break and Inspect tworzy największe opóźnienie, inne usługi, takie jak uwierzytelnianie serwera proxy i wyszukiwanie reputacji, mogą powodować niską wydajność i złe środowisko użytkownika. Ponadto te urządzenia sieci obwodowej potrzebują wystarczającej pojemności, aby przetworzyć wszystkie żądania połączenia sieciowego. Zalecamy pomijanie serwera proxy lub urządzeń inspekcji w przypadku żądań sieciowych Office 365 bezpośrednich.
  
[Galeria programu PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) to skrypt programu PowerShell, który odczytuje najnowsze punkty końcowe sieci z usługi sieci Web Office 365 adresów IP i adresów URL oraz tworzy przykładowy plik PAC. Skrypt można zmodyfikować tak, aby był integrowany z istniejącym zarządzaniem plikami PAC.

![Nawiązywanie połączenia z Office 365 za pośrednictwem zapór i serwerów proxy.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Rysunek 1 . Prosty obwód sieci przedsiębiorstwa**

Plik PAC jest wdrażany w przeglądarkach internetowych w punkcie 1 na rysunku 1. W przypadku korzystania z pliku PAC do bezpośredniego ruchu wychodzącego o istotnych Office 365 ruchu sieciowego należy również zezwolić na łączność z adresami IP znajdującymi się za tymi adresami URL w zaporze obwodowej sieci. Odbywa się to przez pobranie adresów IP dla tych samych Office 365 kategorii punktów końcowych, jak określono w pliku PAC i utworzenie list ACL zapory na podstawie tych adresów. Zapora jest punktem 3 na rysunku 1.

Osobno, jeśli wybierzesz tylko routing bezpośredni dla punktów końcowych kategorii Optymalizacja, wszystkie wymagane punkty końcowe kategorii Zezwalaj wysyłane do serwera proxy będą musiały być wymienione na serwerze proxy w celu obejścia dalszego przetwarzania. Na przykład podział protokołu SSL oraz inspekcja i uwierzytelnianie serwera proxy są niezgodne zarówno z punktami końcowymi Optymalizacja, jak i Zezwalaj na kategorię. Serwer proxy jest punktem 2 na rysunku 1.

Typową konfiguracją jest zezwolenie bez przetwarzania całego ruchu wychodzącego z serwera proxy dla docelowych adresów IP dla ruchu sieciowego Office 365, który dociera do serwera proxy. Aby uzyskać informacje o problemach z podziałem i inspekcją protokołu SSL, zobacz [Korzystanie z urządzeń sieciowych innych firm lub rozwiązań dotyczących ruchu Office 365](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Istnieją dwa typy plików PAC, które wygeneruje skrypt Get-PacFile.

| Wpisać | Opis |
|:-----|:-----|
|**1** <br/> |Wyślij bezpośredni ruch do punktu końcowego optymalizuj i wszystkie inne elementy do serwera proxy. <br/> |
|**2** <br/> |Wyślij opcję Optymalizuj i zezwalaj na bezpośredni ruch punktu końcowego oraz wszystkie inne elementy do serwera proxy. Tego typu można również użyć do wysyłania wszystkich obsługiwanych usług ExpressRoute dla ruchu Office 365 do segmentów sieci usługi ExpressRoute i wszystkich innych do serwera proxy. <br/> |

Oto prosty przykład wywoływania skryptu programu PowerShell:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Istnieje wiele parametrów, które można przekazać do skryptu:

| Parametr | Opis |
|:-----|:-----|
|**ClientRequestId** <br/> |Jest to wymagane i jest identyfikatorEM GUID przekazanym do usługi internetowej, która reprezentuje maszynę kliencką wykonującą wywołanie. <br/> |
|**Wystąpienie** <br/> |Wystąpienie usługi Office 365, które domyślnie ma wartość Na całym świecie. Jest to również przekazywane do usługi internetowej. <br/> |
|**TenantName** <br/> |Nazwa dzierżawy Office 365. Przekazany do usługi internetowej i używany jako parametr wymienny w niektórych adresach URL Office 365. <br/> |
|**Type** <br/> |Typ pliku PAC serwera proxy, który chcesz wygenerować. <br/> |

Oto kolejny przykład wywoływania skryptu programu PowerShell z dodatkowymi parametrami:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Serwer proxy pomija przetwarzanie ruchu sieciowego Office 365

Jeśli pliki PAC nie są używane do bezpośredniego ruchu wychodzącego, nadal chcesz pominąć przetwarzanie na obwodzie sieci, konfigurując serwer proxy. Niektórzy dostawcy serwera proxy włączyli automatyczną konfigurację tego rozwiązania zgodnie z opisem w [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md).

Jeśli robisz to ręcznie, musisz pobrać dane kategorii Optymalizuj i Zezwalaj na punkty końcowe z usługi sieci Web Office 365 adresów IP i adresów URL oraz skonfigurować serwer proxy do obejścia przetwarzania tych danych. Ważne jest, aby uniknąć podziału protokołu SSL oraz inspekcji i uwierzytelniania serwera proxy dla punktów końcowych optymalizacji i zezwalania na kategorię.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Zarządzanie zmianami adresów IP i adresów URL Office 365

Oprócz wybrania odpowiedniej konfiguracji dla obwodu sieci ważne jest wdrożenie procesu zarządzania zmianami dla Office 365 punktów końcowych. Te punkty końcowe zmieniają się regularnie, a jeśli nie zarządzasz zmianami, po dodaniu nowego adresu IP lub adresu URL mogą wystąpić problemy z blokowaniem użytkowników lub niską wydajnością.

Zmiany Office 365 adresów IP i adresów URL są zwykle publikowane w ostatnim dniu każdego miesiąca. Czasami zmiana zostanie opublikowana poza tym harmonogramem z powodu wymagań operacyjnych, pomocy technicznej lub zabezpieczeń.

Po opublikowaniu zmiany, która wymaga działania z powodu dodania adresu IP lub adresu URL, należy oczekiwać 30-dniowego powiadomienia od momentu opublikowania zmiany do momentu utworzenia usługi Office 365 w tym punkcie końcowym. Jest to odzwierciedlone jako data wejścia w życie. Mimo że dążymy do tego okresu powiadomień, nie zawsze jest to możliwe ze względu na wymagania dotyczące działania, pomocy technicznej lub zabezpieczeń. Zmiany, które nie wymagają natychmiastowej akcji w celu utrzymania łączności, takie jak usunięte adresy IP lub adresy URL lub mniej znaczące zmiany, nie obejmują powiadomienia z wyprzedzeniem. W tych przypadkach nie zostanie podana żadna data wejścia w życie. Niezależnie od tego, jakie powiadomienie jest dostarczane, wyświetlamy listę oczekiwanej aktywnej daty usługi dla każdej zmiany.

### <a name="change-notification-using-the-web-service"></a>Zmienianie powiadomienia przy użyciu usługi sieci Web

Aby uzyskać powiadomienie o zmianie, możesz użyć Office 365 adresu IP i usługi sieci Web adresu URL. Zalecamy wywołanie metody **internetowej /version** raz na godzinę, aby sprawdzić wersję punktów końcowych używanych do nawiązywania połączenia z Office 365. Jeśli ta wersja zmieni się w porównaniu z używaną wersją, należy pobrać najnowsze dane punktu końcowego z metody internetowej **/endpoints** i opcjonalnie uzyskać różnice z metody internetowej **/changes** . Nie trzeba wywoływać **/endpoints** lub **/changes** metod internetowych, jeśli nie nastąpiła żadna zmiana w znalezionej wersji.

Aby uzyskać więcej informacji, zobacz [Office 365 adres IP i adres URL usługi sieci Web](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Zmienianie powiadomień przy użyciu kanałów informacyjnych RSS

Usługa sieci Web adresów IP i adresów URL Office 365 udostępnia kanał informacyjny RSS, który można subskrybować w Outlook. Istnieją linki do adresów URL usług RSS na każdej ze stron specyficznych dla wystąpienia usługi Office 365 adresów IP i adresów URL. Aby uzyskać więcej informacji, zobacz [Office 365 adres IP i adres URL usługi sieci Web](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Zmienianie przeglądu powiadomień i zatwierdzania przy użyciu Power Automate

Rozumiemy, że nadal może być wymagane ręczne przetwarzanie zmian w punktach końcowych sieci, które pojawiają się w każdym miesiącu. Możesz użyć Power Automate, aby utworzyć przepływ, który powiadamia cię pocztą e-mail i opcjonalnie uruchamia proces zatwierdzania zmian, gdy Office 365 punkty końcowe sieci mają zmiany. Po zakończeniu przeglądu możesz automatycznie wysłać zmiany do zespołu zarządzania zaporą i serwerem proxy.

Aby uzyskać informacje o przykładzie i szablonie Power Automate, zobacz [Używanie Power Automate do odbierania wiadomości e-mail w celu wprowadzenia zmian w adresach IP i adresach URL Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 punkty końcowe sieci — często zadawane pytania

Zobacz te często zadawane pytania dotyczące Office 365 łączności sieciowej.
  
### <a name="how-do-i-submit-a-question"></a>Jak mogę przesłać pytanie?

Kliknij link u dołu, aby wskazać, czy artykuł był pomocny, czy nie, i prześlij dodatkowe pytania. Monitorujemy opinię i aktualizujemy tutaj pytania, korzystając z najczęściej zadawanych pytań.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Jak mogę określić lokalizację mojej dzierżawy?

 **Lokalizacja dzierżawy** jest najlepiej określana przy użyciu [mapy centrum danych](./o365-data-locations.md).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Czy komunikacja równorzędna jest odpowiednia z firmą Microsoft?

 **Lokalizacje komunikacji równorzędnej** opisano bardziej szczegółowo w [komunikacji równorzędnej z firmą Microsoft](https://www.microsoft.com/peering).
  
Dzięki ponad 2500 relacjom komunikacji równorzędnej usługodawców sieciowych na całym świecie i 70 punktom obecności, dotarcie z sieci do naszej powinno być bezproblemowe. Nie zaszkodzi spędzić kilka minut, upewniając się, że relacja komunikacji równorzędnej usługodawcy isp jest najbardziej optymalna, [oto kilka przykładów dobrych](/archive/blogs/onthewire/__guidance) i nie tak dobrych komunikacji równorzędnej hand-off do naszej sieci.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Widzę żądania sieciowe do adresów IP, które nie znajdują się na opublikowanej liście, czy muszę zapewnić im dostęp?

Podajemy tylko adresy IP dla serwerów Office 365, do których należy kierować się bezpośrednio. Nie jest to pełna lista wszystkich adresów IP, dla których będą wyświetlane żądania sieciowe. Zobaczysz żądania sieciowe do firmy Microsoft i adresów IP należących do innych firm, nieopublikowanych. Te adresy IP są generowane dynamicznie lub zarządzane w sposób uniemożliwiający szybkie powiadomienie o zmianie. Jeśli zapora nie może zezwolić na dostęp na podstawie nazw FQDN dla tych żądań sieciowych, użyj pliku PAC lub WPAD do zarządzania żądaniami.
  
Czy widzisz adres IP skojarzony z Office 365, o których chcesz uzyskać więcej informacji?
  
1. Sprawdź, czy adres IP jest uwzględniony w większym opublikowanym zakresie przy użyciu kalkulatora CIDR, takiego jak dla [protokołu IPv4](https://www.ipaddressguide.com/cidr) lub [IPv6](https://www.ipaddressguide.com/ipv6-cidr). Na przykład 40.96.0.0/13 zawiera adres IP 40.103.0.1, mimo że 40.96 nie pasuje do 40.103.
2. Sprawdź, czy partner jest właścicielem adresu IP z [zapytaniem whois](https://dnsquery.org/). Jeśli jest własnością firmy Microsoft, może to być partner wewnętrzny. Wiele punktów końcowych sieci partnerskiej jest wymienionych jako należące do kategorii _domyślnej_ , dla których adresy IP nie są publikowane.
3. Adres IP może nie być częścią Office 365 lub zależności. Office 365 publikowanie punktów końcowych sieci nie obejmuje wszystkich punktów końcowych sieci firmy Microsoft.
4. Sprawdź certyfikat. W przeglądarce połącz się z adresem IP przy użyciu  *HTTPS://\<IP_ADDRESS\>* i sprawdź domeny wymienione w certyfikacie, aby dowiedzieć się, jakie domeny są skojarzone z adresem IP. Jeśli jest to adres IP należący do firmy Microsoft, a nie na liście Office 365 adresów IP, prawdopodobnie adres IP jest skojarzony z CDN firmy Microsoft, na przykład *MSOCDN.NET* lub inną domeną firmy Microsoft bez opublikowanych informacji IP. Jeśli domena certyfikatu jest domeną, w której żądamy wyświetlenia adresu IP, poinformuj nas o tym.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Niektóre adresy URL Office 365 wskazują rekordy CNAME zamiast rekordów A w systemie DNS. Co mam zrobić z rekordami CNAME?

Komputery klienckie potrzebują rekordu DNS A lub AAAA, który zawiera co najmniej jeden adres IP w celu nawiązania połączenia z usługą w chmurze. Niektóre adresy URL zawarte w Office 365 pokazują rekordy CNAME zamiast rekordów A lub AAAA. Te rekordy CNAME są pośredniczące i może istnieć kilka w łańcuchu. Zawsze będą one ostatecznie rozpoznawać rekord A lub AAAA dla adresu IP. Rozważmy na przykład następującą serię rekordów DNS, które ostatecznie rozpoznają adres IP _IP_1_:

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Te przekierowania CNAME są normalną częścią systemu DNS i są niewidoczne dla komputera klienckiego i niewidoczne dla serwerów proxy. Są one używane do równoważenia obciążenia, sieci dostarczania zawartości, wysokiej dostępności i ograniczania zdarzeń usługi. Firma Microsoft nie publikuje pośredniczących rekordów CNAME, mogą one ulec zmianie w dowolnym momencie i nie należy ich konfigurować zgodnie z wymaganiami na serwerze proxy.

Serwer proxy weryfikuje początkowy adres URL, który w powyższym przykładzie jest serviceA.office.com, a ten adres URL zostanie uwzględniony w Office 365 publikowania. Serwer proxy żąda rozpoznawania dns tego adresu URL do adresu IP i otrzyma z powrotem IP_1. Nie weryfikuje on pośredniczących rekordów przekierowania CNAME.

Konfiguracje zakodowane na stałe lub korzystające z listy dozwolonych opartej na pośrednich Office 365 nazw FQDN nie są zalecane, nie są obsługiwane przez firmę Microsoft i wiadomo, że powodują problemy z łącznością z klientem. Rozwiązania DNS, które blokują przekierowanie CNAME lub które w inny sposób niepoprawnie rozpoznają Office 365 wpisy DNS, można rozwiązać za pośrednictwem usług przesyłania dalej DNS z włączoną rekursją DNS lub za pomocą wskazówek głównych DNS. Wiele produktów obwodowych sieci innych firm natywnie integruje zalecany punkt końcowy Office 365, aby uwzględnić listę dozwolonych w konfiguracji przy użyciu [usługi sieci Web Office 365 adresów IP i adresów URL](microsoft-365-ip-web-service.md).

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Dlaczego w nazwach domen firmy Microsoft są wyświetlane nazwy takie jak nsatc.net lub akadns.net?

Office 365 i inne usługi firmy Microsoft korzystać z kilku usług innych firm, takich jak Akamai i MarkMonitor, aby ulepszyć środowisko Office 365. Aby zapewnić ci jak najlepsze środowisko, możemy zmienić te usługi w przyszłości. Domeny innych firm mogą hostowanie zawartości, takiej jak CDN, lub mogą hostowanie usługi, takiej jak usługa zarządzania ruchem geograficznym. Niektóre z obecnie używanych usług to:
  
[MarkMonitor](https://www.markmonitor.com/) jest używany, gdy zobaczysz żądania obejmujące  *\*nsatc.net*. Ta usługa zapewnia ochronę nazw domen i monitorowanie w celu ochrony przed złośliwym zachowaniem.
  
[Funkcja ExactTarget](https://www.marketingcloud.com/) jest używana w przypadku wyświetlenia żądań do  *\*exacttarget.com*. Ta usługa zapewnia zarządzanie linkami poczty e-mail i monitorowanie przed złośliwym zachowaniem.
  
[Usługa Akamai](https://www.akamai.com/) jest używana w przypadku wyświetleń żądań zawierających jedną z następujących nazw FQDN. Ta usługa oferuje usługi sieciowe geo-DNS i dostarczania zawartości.
  
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

Ponieważ Office 365 jest pakietem usług utworzonych do działania przez Internet, obietnice dotyczące niezawodności i dostępności są oparte na wielu dostępnych standardowych usługach internetowych. Na przykład standardowe usługi internetowe, takie jak DNS, CRL i CDN, muszą być osiągalne do używania Office 365, tak jak muszą być osiągalne do korzystania z większości nowoczesnych usług internetowych.

Pakiet Office 365 jest podzielony na główne obszary usług. Można je selektywnie włączyć dla łączności i istnieje wspólny obszar, który jest zależnością dla wszystkich i jest zawsze wymagany.

| Obszar usługi | Opis |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online i Exchange Online Protection <br/> |
|**SharePoint** <br/> |Usługi SharePoint Online i OneDrive dla Firm <br/> |
|**Skype dla firm Online i Microsoft Teams** <br/> |Skype dla firm i Microsoft Teams <br/> |
|**Wspólne** <br/> |Office 365 Pro Plus, Office w przeglądarce, usłudze Azure AD i innych typowych punktach końcowych sieci <br/> |

Oprócz podstawowych usług internetowych istnieją usługi innych firm, które są używane tylko do integracji funkcji. Chociaż są one potrzebne do integracji, są one oznaczone jako opcjonalne w artykule Office 365 punktów końcowych, co oznacza, że podstawowe funkcje usługi będą nadal działać, jeśli punkt końcowy nie jest dostępny. Każdy wymagany punkt końcowy sieci będzie mieć wymagany atrybut ustawiony na wartość true. Każdy opcjonalny punkt końcowy sieci będzie miał wymagany atrybut ustawiony na wartość false, a atrybut notesu szczegółowo określi brakujące funkcje, których należy oczekiwać, jeśli łączność zostanie zablokowana.
  
Jeśli próbujesz użyć Office 365 i stwierdzasz, że usługi innych firm są niedostępne, upewnij się, [że wszystkie nazwy FQDN oznaczone jako wymagane lub opcjonalne w tym artykule są dozwolone za pośrednictwem serwera proxy i zapory](urls-and-ip-address-ranges.md).
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Jak mogę zablokować dostęp do usług konsumenckich firmy Microsoft?

Funkcja ograniczeń dzierżawy obsługuje teraz blokowanie korzystania ze wszystkich aplikacji konsumenckich firmy Microsoft (aplikacji MSA), takich jak OneDrive, Hotmail i Xbox.com. Używa to oddzielnego nagłówka do punktu końcowego login.live.com. Aby uzyskać więcej informacji, zobacz [Używanie ograniczeń dzierżawy do zarządzania dostępem do aplikacji W chmurze SaaS](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Moja zapora wymaga adresów IP i nie może przetwarzać adresów URL. Jak mogę skonfigurować go dla Office 365?

Office 365 nie zawiera adresów IP wszystkich wymaganych punktów końcowych sieci. Niektóre z nich są udostępniane tylko jako adresy URL i są kategoryzowane jako domyślne. Adresy URL w kategorii domyślnej, które są wymagane, powinny być dozwolone za pośrednictwem serwera proxy. Jeśli nie masz serwera proxy, sprawdź, jak skonfigurowano żądania internetowe dla adresów URL, które użytkownicy wpisują na pasku adresu przeglądarki internetowej; użytkownik nie podaje również adresu IP. Domyślne adresy URL kategorii Office 365, które nie zawierają adresów IP, powinny być skonfigurowane w taki sam sposób.

## <a name="related-topics"></a>Tematy pokrewne

[Usługa Office 365 — usługa sieci Web adresów IP i adresów URL](microsoft-365-ip-web-service.md)

[zakresy adresów IP centrum danych Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Przestrzeń publicznych adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Wymagania dotyczące infrastruktury sieci dla Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Usługi ExpressRoute i Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)
  
[Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365](managing-expressroute-for-connectivity.md)
  
[zasady łączności sieciowej Office 365](microsoft-365-network-connectivity-principles.md)
