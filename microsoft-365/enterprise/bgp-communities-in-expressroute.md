---
title: Używanie społeczności BGP w u usługi ExpressRoute na Office 365 scenariuszy
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak używać społeczności BGP w usłudze Azure ExpressRoute do zarządzania liczbą prefiksów IP i wymaganą przepustowością dla Office 365 scenariuszy.
ms.openlocfilehash: afcbbbebda8dcc7c9425831b44f0d95f0eca5a18
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986592"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Używanie społeczności BGP w u usługi ExpressRoute na Office 365 scenariuszy

Nawiązywanie połączenia Office 365 przy użyciu usługi Azure ExpressRoute jest oparte na anonsach BGP określonych podsieci IP reprezentujących sieci, w których Office 365 punkty końcowe są wdrażane. Ze względu na globalny charakter usług Office 365 i liczbę usług, które stanowią Office 365, klienci często muszą zarządzać anonsami, które akceptują w swoich sieciach. Zmniejszenie liczby podsieci IP; W celu dostosowania do terminologii zarządzania siecią BGP, określanej jako prefiksy IP w pozostałej części tego artykułu, klienci mają następujące cele końcowe:
  
- Zarządzanie liczbą zaakceptowanych anonsowanych prefiksów **IP** — klienci, którzy posiadają wewnętrzną infrastrukturę sieciową lub operatora sieci obsługującego ograniczoną liczbę prefiksów IP, oraz klienci, których operator nalicza opłaty za zaakceptowanie prefiksów powyżej ograniczonej liczby, będą chcieli oszacować całkowitą liczbę prefiksów już ogłaszanych w ich sieci i wybrać aplikacje usługi Office 365, które najlepiej nadają się do usługi ExpressRoute.

- Zarządzanie przepustowością wymaganą w obwodzie usługi **Azure ExpressRoute** — klienci mogą chcieć kontrolować kopertę przepustowości usług Office 365 przez ścieżkę usługi ExpressRoute a ścieżkę internetową. Dzięki temu klienci mogą zarezerwować przepustowość usługi ExpressRoute dla określonych aplikacji, takich jak Skype dla firm, i rozsyłać pozostałe Office 365 przez ścieżkę internetową.

Aby pomóc klientom z tymi celami, Office 365 PREFIKSY IP, które są ogłaszane za pośrednictwem usługi ExpressRoute, są otagowane specyficznymi dla usługi wartościami społeczności BGP, jak pokazano w poniższym przykładzie.
  
> [!NOTE]
> Należy oczekiwać, że część ruchu sieciowego związanego z innymi aplikacjami zostanie uwzględniona w wartości społeczności. Jest to oczekiwane zachowanie w przypadku globalnej oferty usługi Software as a Service z udostępnionymi usługami i centrami danych. W miarę możliwości zminimalizowano ten proces, mając na uwadze powyższe dwa cele, mając na uwadze zarządzanie licznikiem prefiksów i (lub) przepustowością.

|**Usługa**|**Wartość Community BGP**|**Uwagi**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Obejmuje Exchange i EOP\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype dla firm\*  <br/> |12076:5030  <br/> |Skype dla firm usługi & Microsoft Teams Online  <br/> |
|Inne Office 365 usługi\*  <br/> |12076:5100  <br/> |Obejmuje Azure Active Directory (scenariusze uwierzytelniania i synchronizacji katalogów) oraz usługi Office 365 portali  <br/> |
|\*Zakres scenariuszy usług zawarty w usłudze ExpressRoute o dokumencie w artykule z Office 365 [punktów końcowych](./urls-and-ip-address-ranges.md).  <br/> \*\*W przyszłości mogą zostać dodane dodatkowe usługi i wartości społeczności BGP. [Zobacz bieżącą listę społeczności BGP](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Jakie są najbardziej typowe scenariusze używania społeczności BGP?

Klienci mogą używać społeczności BGP, aby regulować grupy prefiksów IP, które są akceptowane przez ich sieci przez usługę Azure ExpressRoute, wpływając na całkowitą liczbę prefiksów IP i oczekiwaną przepustowość niektórych Office 365 usług. Ważne jest, aby zrozumieć, że wszystkie Office 365 będzie wymagać ruchu powiązanego z Internetem niezależnie od użycia usługi Azure ExpressRoute lub społeczności BGP. Poniższe trzy scenariusze to najpopularniejsze zastosowania tej funkcji.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scenariusz 1. Minimalizowanie liczby prefiksów IP Office 365 IP

Contoso Corporation to firma zatrudniaca 50 000 osób, która obecnie Office 365 usługach Exchange Online i SharePoint Online. Podczas przeglądania wymagań usługi ExpressRoute firma Contoso ustala, że urządzenia sieciowe w wielu lokalizacjach regionalnych nie mogą obsługiwać tabel routingu powyżej 100 dodatkowych tras. Firma Contoso przejeła całkowitą liczbę prefiksów IP, które usługi ExpressRoute anonsowałaby dla pełnego zestawu usług Office 365, i podsumowała, że liczba ta przekracza 100. Aby nie było więcej niż 100 dodatkowych wpisów tras, firma Contoso zawęza użycie usługi ExpressRoute dla usługi Office 365 tylko do wartości społeczności BGP usługi SharePoint Online, 12076:5020, otrzymanej w drodze komunikacji równorzędnej przez usługę Microsoft ExpressRoute.

|**Użyty tag społeczności BGP**|**Funkcja routowalna przez usługę Azure ExpressRoute**|**Wymagane trasy internetowe**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online OneDrive dla Firm &amp;  <br/> | Żądania rekordów DNS, &amp; list CRL CDN rekordów  <br/>  Wszystkie inne usługi Office 365, które nie są specjalnie obsługiwane przez usługę Azure ExpressRoute  <br/>  Wszystkie pozostałe usługi firmy Microsoft w chmurze  <br/>  Office 365 portal, Office 365 uwierzytelnianie i &amp; Office w przeglądarce  <br/>  Exchange Online, Exchange Online Protection i Skype dla firm Online  <br/> |

> [!NOTE]
> Aby można było osiągnąć niższą liczbę prefiksów dla każdej usługi, musi być zachowywany minimalny obszar nakładania się usług. Takie zachowanie jest oczekiwane.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scenariusz 2. Określanie zakresu użycia usługi ExpressRoute i przepustowości wewnętrznej do niektórych Office 365 sieci

Fabrikam Inc, duże wielonarodowe przedsiębiorstwo z rozproszonej, niejednorodnej sieci, jest subskrybentem wielu Office 365 usług, w tym: Exchange Online, SharePoint Online i Skype dla firm Online. Wewnętrzna infrastruktura routingu firmy Fabrikam może obsługiwać tysiące prefiksów IP w swoich tabelach routingu. Jednak firma Fabrikam chce zapewniać usługę ExpressRoute i przepustowość wewnętrzną tylko dla aplikacji Office 365, które są najbardziej poufne pod uwagę pod wydajnością sieci i używają istniejącej przepustowości internetowej dla wszystkich innych aplikacji Office 365 sieci.
  
Z tego powodu firma Fabrikam ma zakres przepustowości usługi Azure ExpressRoute tylko do wartości Community BGP usługi Skype dla firm Community online, 12076:5030, otrzymanej w drodze komunikacji równorzędnej przez usługę Microsoft ExpressRoute. Pozostały ruch sieciowy skojarzony z usługą Office 365 nadal używa internetowych punktów ruchu wychodzącego.

|**Użyty tag społeczności BGP**|**Funkcja routowalna przez usługę Azure ExpressRoute**|**Wymagane trasy internetowe**|
|:-----|:-----|:-----|
|Skype dla firm  <br/> (12076:5030)  <br/> |Skype sygnału SIP, pobierania, komunikacji głosowej, wideo i udostępniania pulpitu  <br/> | Żądania rekordów DNS, &amp; list CRL CDN rekordów  <br/>  Wszystkie inne usługi Office 365, które nie są specjalnie obsługiwane przez usługę Azure ExpressRoute  <br/>  Wszystkie pozostałe usługi firmy Microsoft w chmurze  <br/>  Office 365 portal, Office 365 uwierzytelnianie i &amp; Office w przeglądarce  <br/>  Skype dla firm wiadomości błyskawicznych, szybkie Skype klientów, łączność publiczna w zakresie wiadomości błyskawicznych  <br/>  Exchange Online, Exchange Online Protection i SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scenariusz 3. Określanie zakresu usługi Azure ExpressRoute tylko Office 365 usług

Bank Woodgrove jest klientem kilku usług firmy Microsoft w chmurze, w tym klientów Office 365. Po dokonaniu oceny pojemności i zużycia swojej bank Woodgrove postanawia wdrożyć usługę Azure ExpressRoute jako preferowaną ścieżkę dla obsługiwanych Office 365 usług. Tabele routingu mogą obsługiwać pełny zestaw prefiksów IP usługi Office 365, Office 365 obwody usługi Azure ExpressRoute z obsługą obsługi administracyjnej obsługują wszystkie prognozowane potrzeby w zakresie przepustowości i opóźnień.
  
Aby zapewnić ruch sieciowy skojarzony z usługami firmy Microsoft w chmurze innymi niż Office 365, bank Woodgrove zakresy użycia usługi ExpressRoute dla usługi Office 365 do wszystkich prefiksów IP oznaczonych określonymi wartościami społeczności BGP usługi Office 365: 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Użyty tag społeczności BGP**|**Funkcja routowalna przez usługę Azure ExpressRoute**|**Wymagane trasy internetowe**|
|:-----|:-----|:-----|
|Exchange, Skype dla firm & Microsoft Teams, SharePoint, &amp; inne usługi  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> SharePoint Online OneDrive dla Firm &amp;  <br/> Skype sygnału SIP, pobierania, komunikacji głosowej, wideo i udostępniania pulpitu  <br/> Office 365 portal, Office 365 uwierzytelnianie i &amp; Office w przeglądarce  <br/> | Żądania rekordów DNS, &amp; list CRL CDN rekordów  <br/>  Wszystkie inne usługi Office 365, które nie są specjalnie obsługiwane przez usługę Azure ExpressRoute  <br/>  Wszystkie pozostałe usługi firmy Microsoft w chmurze  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Kluczowe kwestie dotyczące planowania użycia społeczności BGP

Klienci, którzy chcą wykorzystać społeczności BGP, aby wpływać na to, jak jest anonsowana i propagowana przez sieć klientów usługę ExpressRoute, powinni wziąć pod uwagę następujące kwestie:
  
- Podczas używania społeczności BGP w projekcie sieci ważne jest, aby zachować symetrię tras. W niektórych przypadkach dodanie lub usunięcie społeczności BGP może spowodować sytuację, w której symetria routingu zostanie załamana i należy zaktualizować konfigurację routingu, aby ponownie ustanowić tę symetrię.

- Określanie zakresu działania usługi Azure ExpressRoute za pomocą wartości społeczności BGP jest działaniem po stronie klienta. Firma Microsoft będzie anonsować wszystkie prefiksy IP skojarzone z relacją komunikacji równorzędnej niezależnie od wszelkich zakresów skonfigurowanych przez klienta.

- Usługa Azure ExpressRoute nie obsługuje żadnych akcji w sieci firmy Microsoft na podstawie społeczności BGP przypisanych przez klienta.

- Prefiksy IP używane przez Office 365 są oznaczone tylko wartościami społeczności BGP specyficznymi dla usługi, określone społeczności BGP lokalizacji nie są obsługiwane. Office 365 usługi mają charakter globalny, filtrowanie prefiksów na podstawie lokalizacji dzierżawy lub danych w Office 365 chmurze nie jest obsługiwane. Zalecane podejście to skonfigurowanie sieci tak, aby skoordynować najkrótszą lub najbardziej preferowaną ścieżkę sieciową z lokalizacji sieciowej użytkownika do globalnej sieci firmy Microsoft, niezależnie od fizycznej lokalizacji adresu IP usługi Office 365, o którą prosili.

- Prefiksy IP zawarte w poszczególnych wartościach społeczności BGP reprezentują podsieci, które zawierają adresy IP Office 365 skojarzonej z wartością. W niektórych przypadkach więcej niż jedna aplikacja Office 365 ma adresy IP w podsieci, co oznacza, że prefiks IP jest istniejący w więcej niż jednej wartości społeczności. To zdarza się rzadko ze względu fragmentację alokacji i nie wpływa na cele związane z zarządzaniem liczbami prefiksów i przepustowością. Zachęcamy klientów do korzystania z podejścia "zezwalaj na to, co jest potrzebne", a nie "odmawiaj tego, co nie jest potrzebne", gdy korzystają ze społeczności BGP dla usługi Office 365 w celu zminimalizowania tego efektu.

- Użycie społeczności BGP nie zmienia podstawowych wymagań dotyczących łączności sieciowej ani konfiguracji wymaganej do korzystania z Office 365. Klienci, którzy chcą uzyskać Office 365, nadal muszą mieć dostęp do Internetu.

- Określanie zakresu dostępu do usługi Azure ExpressRoute za pomocą społeczności BGP wpływa tylko na trasy, które może zobaczyć sieć wewnętrzna za pośrednictwem relacji komunikacji równorzędnej firmy Microsoft. W połączeniu z routingiem o ograniczonych zakresach może być konieczne użycie konfiguracji na poziomie aplikacji, takiej jak użycie konfiguracji PAC lub WPAD.

- Oprócz używania społeczności BGP przypisanych przez firmę Microsoft klienci mogą przypisywać własne społeczności BGP do prefiksów IP usługi Office 365 za pośrednictwem usługi Azure ExpressRoute, aby wpłynąć na routing wewnętrzny. Popularnym przypadekem jest przypisanie społeczności BGP opartej na lokalizacji do wszystkich tras poznanych za pośrednictwem poszczególnych lokalizacji komunikacji równorzędnej usługi ExpressRoute, a następnie wykorzystanie tych informacji w sieci klienta do koordynowania najkrótszej lub najbardziej preferowanej ścieżki sieciowej do sieci firmy Microsoft. Użycie przypisanych przez klienta społeczności BGP z usługą ExpressRoute na potrzeby Office 365 jest poza zakresem kontroli i widoczności firmy Microsoft.

Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>Tematy pokrewne

[Ocena Office 365 sieci](assessing-network-connectivity.md)
  
[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
  
[Zarządzanie łącznością sieciową za Office 365 ExpressRoute](managing-expressroute-for-connectivity.md)
  
[Routing za pomocą usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
  
[Planowanie sieci z usługą ExpressRoute dla sieci Office 365](network-planning-with-expressroute.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Usługi ExpressRoute i QoS w Skype dla firm Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Przepływ połączeń przy użyciu usługi ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementowanie expressroute dla Office 365](implementing-expressroute.md)
  
[Obsługa społeczności BGP](/azure/expressroute/expressroute-routing)
  
[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)
  
[Szkolenia dotyczące usługi Azure ExpressRoute Office 365 usługi Azure ExpressRoute](https://channel9.msdn.com/series/aer)