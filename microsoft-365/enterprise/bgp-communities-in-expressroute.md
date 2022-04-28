---
title: Używanie społeczności protokołu BGP w usłudze ExpressRoute na potrzeby scenariuszy Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: Dowiedz się, jak używać społeczności protokołu BGP w usłudze Azure ExpressRoute do zarządzania liczbą prefiksów adresów IP i wymaganą przepustowością w scenariuszach Office 365.
ms.openlocfilehash: 3e7ec6373299741cc1d34c18cc6be5b9366f3de6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095779"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Używanie społeczności protokołu BGP w usłudze ExpressRoute na potrzeby scenariuszy Office 365

Nawiązywanie połączenia z Office 365 przy użyciu usługi Azure ExpressRoute jest oparte na anonsach protokołu BGP określonych podsieci IP reprezentujących sieci, w których są wdrażane punkty końcowe Office 365. Ze względu na globalny charakter Office 365 i liczbę usług, które stanowią Office 365, klienci często muszą zarządzać reklamami, które akceptują w swojej sieci. Zmniejszenie liczby podsieci IP; Określane jako prefiksy IP w pozostałej części tego artykułu, aby dostosować się do terminologii zarządzania siecią BGP, służy następującym celom końcowym dla klientów:
  
- **Zarządzaj liczbą zaakceptowanych prefiksów anonsowanych adresów IP** — klienci, którzy mają infrastrukturę sieci wewnętrznej lub operatora sieci, który obsługuje tylko ograniczoną liczbę prefiksów adresów IP, oraz klienci, którzy mają operatora sieci, który pobiera opłaty za akceptowanie prefiksów powyżej ograniczonej liczby, będą chcieli ocenić całkowitą liczbę prefiksów już anonsowanych w sieci i wybrać, które aplikacje Office 365 są najlepiej odpowiednie dla usługi ExpressRoute.

- **Zarządzanie ilością przepustowości wymaganą w obwodzie usługi Azure ExpressRoute** — klienci mogą chcieć kontrolować kopertę przepustowości usług Office 365 za pośrednictwem ścieżki usługi ExpressRoute a ścieżki internetowej. Dzięki temu klienci mogą rezerwować przepustowość usługi ExpressRoute dla określonych aplikacji, takich jak Skype dla firm, i kierować pozostałe aplikacje Office 365 przez ścieżkę internetową.

Aby pomóc klientom w realizacji tych celów, Office 365 prefiksy adresów IP, które są anonsowane za pośrednictwem usługi ExpressRoute, są oznaczane wartościami społeczności protokołu BGP specyficznymi dla usługi, jak pokazano w poniższym przykładzie.
  
> [!NOTE]
> Należy oczekiwać, że część ruchu sieciowego skojarzonego z innymi aplikacjami zostanie uwzględniona w wartości społeczności. Jest to oczekiwane zachowanie globalnej oferty oprogramowania jako usługi z usługami udostępnionymi i centrami danych. Zostało to zminimalizowane tam, gdzie to możliwe, przy użyciu powyższych dwóch celów, z myślą o zarządzaniu liczbą prefiksów i/lub przepustowością.

|**Usługa**|**Wartość Community protokołu BGP**|**Uwagi**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Obejmuje usługi Exchange i EOP\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype dla firm\*  <br/> |12076:5030  <br/> |usługi & Microsoft Teams online Skype dla firm  <br/> |
|Inne usługi Office 365\*  <br/> |12076:5100  <br/> |Obejmuje Azure Active Directory (scenariusze uwierzytelniania i synchronizacji katalogów), a także usługi portalu Office 365  <br/> |
|\*Zakres scenariuszy usług zawartych w usłudze ExpressRoute jest udokumentowany w artykule [Office 365 punktów końcowych](./urls-and-ip-address-ranges.md).  <br/> \*\*Dodatkowe usługi i wartości społeczności protokołu BGP mogą zostać dodane w przyszłości. [Zobacz bieżącą listę społeczności protokołu BGP](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Jakie są najczęstsze scenariusze korzystania ze społeczności protokołu BGP?

Klienci mogą używać społeczności protokołu BGP do regulowania grup prefiksów adresów IP akceptowanych przez ich sieć za pośrednictwem usługi Azure ExpressRoute, co ma wpływ na łączną liczbę prefiksów ip i oczekiwaną kopertę przepustowości niektórych usług Office 365. Należy pamiętać, że wszystkie Office 365 będą wymagały ruchu związanego z Internetem niezależnie od korzystania ze społeczności usługi Azure ExpressRoute lub BGP. Poniższe trzy scenariusze to najczęstsze zastosowania tej funkcji.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scenariusz 1. Minimalizowanie liczby prefiksów Office 365 adresów IP

Contoso Corporation to firma z 50 000 osób, która obecnie używa Office 365 dla Exchange Online i SharePoint Online. Podczas przeglądania wymagań usługi ExpressRoute firma Contoso określa, że urządzenia sieciowe w wielu lokalizacjach regionalnych nie mogą obsługiwać tabel routingu o rozmiarach powyżej 100 dodatkowych wpisów tras. Firma Contoso przejrzała całkowitą liczbę prefiksów adresów IP anonsowanych przez usługę ExpressRoute dla pełnego zestawu usług Office 365 i stwierdziła, że przekracza ona 100. Aby pozostać poniżej 100 dodatkowych wpisów trasy, firma Contoso ogranicza użycie usługi ExpressRoute dla Office 365 tylko do wartości społeczności protokołu BGP usługi SharePoint Online, 12076:5020, odebranej za pośrednictwem komunikacji równorzędnej firmy Microsoft usługi ExpressRoute.

|**Używany tag społeczności protokołu BGP**|**Routing funkcji za pośrednictwem usługi Azure ExpressRoute**|**Wymagane trasy internetowe**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint online &amp; OneDrive dla Firm  <br/> | Żądania DNS, CRL, &amp; CDN  <br/>  Wszystkie inne usługi Office 365 nie są specjalnie obsługiwane przez usługę Azure ExpressRoute  <br/>  Wszystkie inne usługi firmy Microsoft w chmurze  <br/>  Office 365 portal, uwierzytelnianie Office 365, &amp; Office w przeglądarce  <br/>  Exchange Online, Exchange Online Protection i Skype dla firm Online  <br/> |

> [!NOTE]
> Aby osiągnąć mniejszą liczbę prefiksów dla każdej usługi, będzie się powtarzać minimalna ilość nakładania się między usługami. Takie zachowanie jest oczekiwane.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scenariusz 2. Określanie zakresu użycia usługi ExpressRoute i przepustowości wewnętrznej dla niektórych usług Office 365

Fabrikam Inc, duże przedsiębiorstwo wielonarodowe z rozproszoną siecią heterogeniczną, jest subskrybentem wielu usług Office 365, w tym; Exchange Online, SharePoint Online i Skype dla firm Online. Wewnętrzna infrastruktura routingu firmy Fabrikam może obsługiwać tysiące prefiksów IP w tabelach routingu; Firma Fabrikam chce jednak aprowizować tylko usługę ExpressRoute i przepustowość wewnętrzną dla aplikacji Office 365, które są najbardziej wrażliwe na wydajność sieci i korzystają z istniejącej przepustowości Internetu dla wszystkich innych aplikacji Office 365.
  
Z tego powodu firma Fabrikam ogranicza przepustowość usługi Azure ExpressRoute do Skype dla firm wartość Community protokołu BGP online o wartości 12076:5030 odebranej za pośrednictwem komunikacji równorzędnej firmy Microsoft usługi ExpressRoute. Pozostały ruch sieciowy skojarzony z Office 365 nadal korzysta z internetowych punktów ruchu wychodzącego.

|**Używany tag społeczności protokołu BGP**|**Routing funkcji za pośrednictwem usługi Azure ExpressRoute**|**Wymagane trasy internetowe**|
|:-----|:-----|:-----|
|Skype dla firm  <br/> (12076:5030)  <br/> |Skype SIP signaling, downloads, voice, video, and desktop sharing (SIP signaling, downloads, voice, video, and desktop sharing)  <br/> | Żądania DNS, CRL, &amp; CDN  <br/>  Wszystkie inne usługi Office 365 nie są specjalnie obsługiwane przez usługę Azure ExpressRoute  <br/>  Wszystkie inne usługi firmy Microsoft w chmurze  <br/>  Office 365 portal, uwierzytelnianie Office 365, &amp; Office w przeglądarce  <br/>  Skype dla firm telemetria, szybkie wskazówki dotyczące klienta Skype, publiczna łączność z wiadomościami błyskawicznymi  <br/>  Exchange Online, Exchange Online Protection i SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scenariusz 3. Określanie zakresu usługi Azure ExpressRoute tylko dla usług Office 365

Woodgrove Bank jest klientem kilku usług w chmurze firmy Microsoft, w tym Office 365. Po dokonaniu oceny pojemności sieci i zużycia firma Woodgrove Bank decyduje się wdrożyć usługę Azure ExpressRoute jako preferowaną ścieżkę dla obsługiwanych usług Office 365. Tabele routingu mogą obsługiwać pełny zestaw prefiksów Office 365 adresów IP, a aprowizowane obwody usługi Azure ExpressRoute obsługują wszystkie przewidywane wymagania dotyczące przepustowości i opóźnienia.
  
Aby zapewnić ruch sieciowy skojarzony z usługami w chmurze firmy Microsoft innymi niż Office 365, woodgrove Bank ogranicza użycie usługi ExpressRoute dla Office 365 do wszystkich prefiksów IP oznaczonych Office 365 określonych wartości społeczności protokołu BGP, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Używany tag społeczności protokołu BGP**|**Routing funkcji za pośrednictwem usługi Azure ExpressRoute**|**Wymagane trasy internetowe**|
|:-----|:-----|:-----|
|Exchange, Skype dla firm & Microsoft Teams, SharePoint, &amp; inne usługi  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> SharePoint online &amp; OneDrive dla Firm  <br/> Skype SIP signaling, downloads, voice, video, and desktop sharing (SIP signaling, downloads, voice, video, and desktop sharing)  <br/> Office 365 portal, uwierzytelnianie Office 365, &amp; Office w przeglądarce  <br/> | Żądania DNS, CRL, &amp; CDN  <br/>  Wszystkie inne usługi Office 365 nie są specjalnie obsługiwane przez usługę Azure ExpressRoute  <br/>  Wszystkie inne usługi firmy Microsoft w chmurze  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Kluczowe zagadnienia dotyczące planowania korzystania ze społeczności protokołu BGP

Klienci, którzy zdecydują się skorzystać ze społeczności protokołu BGP, aby wpłynąć na sposób anonsowania i propagowania usługi ExpressRoute za pośrednictwem sieci klientów, powinni wziąć pod uwagę następujące kwestie:
  
- W przypadku korzystania ze społeczności protokołu BGP w projekcie sieci ważne jest, aby zapewnić zachowanie symetrii tras. W niektórych przypadkach dodanie lub usunięcie społeczności protokołu BGP może spowodować przerwanie routingu symetrycznego i zaktualizowanie konfiguracji routingu w celu przywrócenia routingu symetrycznego.

- Określanie zakresu usługi Azure ExpressRoute przy użyciu wartości społeczności protokołu BGP to akcja klienta. Firma Microsoft anonsuje wszystkie prefiksy adresów IP skojarzone z relacją komunikacji równorzędnej niezależnie od zakresu skonfigurowanego przez klienta.

- Usługa Azure ExpressRoute nie obsługuje żadnych akcji w sieci firmy Microsoft opartych na społecznościach protokołu BGP przypisanych przez klienta.

- Prefiksy adresów IP używane przez Office 365 są oznaczone tylko wartościami społeczności protokołu BGP specyficznymi dla usługi, a specyficzne dla lokalizacji społeczności protokołu BGP nie są obsługiwane. Office 365 usługi mają charakter globalny, filtrowanie prefiksów na podstawie lokalizacji dzierżawy lub danych w chmurze Office 365 nie jest obsługiwane. Zaleca się skonfigurowanie sieci w celu koordynowania najkrótszej lub najbardziej preferowanej ścieżki sieciowej z lokalizacji sieciowej użytkownika do sieci globalnej firmy Microsoft, niezależnie od fizycznej lokalizacji adresu IP żądanej usługi Office 365.

- Prefiksy ip zawarte w każdej wartości społeczności protokołu BGP reprezentują podsieć zawierającą adresy IP dla aplikacji Office 365 skojarzonej z wartością. W niektórych przypadkach więcej niż jedna aplikacja Office 365 ma adresy IP w podsieci, co powoduje powstanie prefiksu IP istniejącego w więcej niż jednej wartości społeczności. Jest to oczekiwane, choć rzadko, zachowanie spowodowane fragmentacją alokacji i nie ma wpływu na liczbę prefiksów ani cele zarządzania przepustowością. Klienci są zachęcani do korzystania z podejścia "zezwalaj na to, co jest potrzebne", w przeciwieństwie do "odmowy tego, co nie jest potrzebne" podczas korzystania ze społeczności BGP dla Office 365, aby zminimalizować efekt.

- Używanie społeczności protokołu BGP nie zmienia podstawowych wymagań dotyczących łączności sieciowej ani konfiguracji wymaganych do używania Office 365. Klienci, którzy chcą uzyskać dostęp do Office 365, nadal muszą mieć dostęp do Internetu.

- Określenie zakresu usługi Azure ExpressRoute ze społecznościami protokołu BGP ma wpływ tylko na trasy, które sieć wewnętrzna może zobaczyć za pośrednictwem relacji komunikacji równorzędnej firmy Microsoft. Może być konieczne utworzenie dodatkowych konfiguracji na poziomie aplikacji, takich jak użycie konfiguracji PAC lub WPAD w połączeniu z routingiem o określonym zakresie.

- Oprócz korzystania ze społeczności protokołu BGP przypisanych przez firmę Microsoft klienci mogą zdecydować się na przypisanie własnych społeczności protokołu BGP do Office 365 prefiksów adresów IP poznanych za pośrednictwem usługi Azure ExpressRoute w celu wpływania na routing wewnętrzny. Popularnym przypadkiem użycia jest przypisanie społeczności protokołu BGP opartej na lokalizacji do wszystkich tras poznanych za pośrednictwem każdej lokalizacji komunikacji równorzędnej usługi ExpressRoute, a następnie użycie tych informacji podrzędnych w sieci klienta w celu koordynowania najkrótszej lub najbardziej preferowanej ścieżki sieciowej do sieci firmy Microsoft. Korzystanie z społeczności protokołu BGP przypisanych przez klienta w usłudze ExpressRoute w przypadku scenariuszy Office 365 wykracza poza zakres kontroli lub widoczności firmy Microsoft.

Oto krótki link, którego można użyć do powrotu: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>Tematy pokrewne

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365](managing-expressroute-for-connectivity.md)
  
[Routing przy użyciu usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
  
[Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365](network-planning-with-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Usługi ExpressRoute i QoS w usłudze Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ wywołań przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementowanie usługi ExpressRoute dla Office 365](implementing-expressroute.md)
  
[Obsługa społeczności protokołu BGP](/azure/expressroute/expressroute-routing)
  
[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)