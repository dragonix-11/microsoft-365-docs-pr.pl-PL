---
title: Sieci dostarczania zawartości
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/15/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Skorzystaj z tych informacji, aby dowiedzieć się, Office 365 sieci dostarczania zawartości (CDN, Content Delivery Networks) w celu zwiększenia wydajności.
ms.openlocfilehash: 1aecd8b23502ed8626979d258f7d26a90b4d3d51
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985299"
---
# <a name="content-delivery-networks-cdns"></a>Sieci dostarczania zawartości (CDN)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Sieci CDN pomagają zapewnić Office 365 i niezawodność dla użytkowników końcowych. Usługi w chmurze Office 365 korzystają z sieci CDN do buforowania statycznych zasobów bliżej przeglądarek żądających ich do przyspieszenia pobierania i zmniejszenia odbieranych opóźnień użytkownika końcowego. Informacje zawarte w tym temacie pomogą Ci dowiedzieć się więcej na temat sieci dostarczania zawartości (CDN, Content Delivery Networks) i sposobu ich Office 365.

## <a name="what-exactly-is-a-cdn"></a>Czym dokładnie jest CDN?

Centrum CDN to geograficznie rozmieszczone sieci składające się z serwerów proxy i serwerów plików w centrach danych połączonych za pomocą szybkich sieci szkieletowych. Sieci CDN służą do skracania opóźnień i czasów ładowania określonego zestawu plików i obiektów w witrynie lub usłudze sieci Web. Centrum CDN może mieć wiele tysięcy punktów końcowych w celu zapewnienia optymalnej obsługi żądań przychodzących z dowolnej lokalizacji.

Sieci CDN są często używane do szybszego pobierania zawartości ogólnej dla witryny sieci Web lub usługi, takiej jak pliki JavaScript, ikony i obrazy, oraz mogą zapewniać prywatny dostęp do zawartości użytkownika, takiej jak pliki w bibliotekach dokumentów usługi SharePoint Online, przesyłanie strumieniowe plików multimedialnych i kod niestandardowy.

Sieci CDN są używane przez większość usług w chmurze przedsiębiorstwa. Usługi w chmurze Office 365 mają miliony klientów pobierających jednocześnie zawartość zastrzeżoną (na przykład wiadomości e-mail) i ogólną zawartość (na przykład ikony). Skuteczniej jest umieszczać obrazy używane przez wszystkich, na przykład ikony, tak blisko komputera użytkownika, jak to tylko możliwe. W przypadku każdej usługi w chmurze tworzenie centrów danych usługi CDN przechowujące tę ogólną zawartość w każdym obszarze wielkomiejskim, a nawet we wszystkich głównych centrach internetowych na świecie, CDN więc niektóre z tych sieci CDN są udostępniane.

## <a name="how-do-cdns-make-services-work-faster"></a>Jak sieci CDN przyspieszyją pracę usług?

Częste pobieranie często używanych obiektów, takich jak obrazy i ikony witryn, może zająć przepustowość sieci, która może być lepiej używana do pobierania ważnej zawartości osobistej, na przykład wiadomości e-mail lub dokumentów. Ponieważ Office 365 korzysta z architektury, która obejmuje sieci CDN, ikony, skrypty i inna ogólna zawartość mogą być pobierane z serwerów bliżej komputerów klienckich, co przyspiesza pobieranie plików. Oznacza to szybszy dostęp do zawartości osobistej, która jest bezpiecznie przechowywana w Office 365 centrach danych.

Sieci CDN pomagają zwiększyć wydajność usługi w chmurze na kilka sposobów:

- Sieci CDN odsuwają część sieci i pobierania plików od usługi w chmurze, co ogranicza konieczność obsługi żądań zasobów statycznych, co ogranicza konieczność obsługi żądań zasobów statycznych.
- Sieci CDN są celem zapewnienia dostępu do plików o małych opóźnieniach, ponieważ dzięki zaimplementowaniu sieci o wysokiej wydajności i serwerów plików oraz przez wykorzystanie zaktualizowanych protokołów sieciowych, takich jak [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) , za pomocą bardzo wydajnej kompresji i żądania multipleksowania.
- CDN korzystają z wielu punktów końcowych rozpowszechnianych globalnie, aby udostępnić zawartość jak najbardziej użytkownikom.

## <a name="the-office-365-cdn"></a>The Office 365 CDN

Wbudowany program Office 365 Content Delivery Network (CDN) pozwala administratorom programu Office 365 zapewnić lepszą wydajność stron usługi SharePoint Online organizacji przez buforowanie statycznych zasobów bliżej przeglądarek żądających ich, co pomaga przyspieszyć pobieranie i zmniejszyć opóźnienie. Ten Office 365 CDN korzysta z [protokołu HTTP/2 w](https://en.wikipedia.org/wiki/HTTP/2) celu poprawy kompresji i szybkości pobierania.

> [!NOTE]
> Ta Office 365 CDN jest dostępna tylko dla dzierżawców w **chmurze produkcyjnej** (na całym świecie). Dzierżawcy chmury rządów Stanów Zjednoczonych, Chin i Niemiec obecnie nie obsługują Office 365 CDN.

Ten Office 365 CDN składa się z wielu sieci CDN, które umożliwiają hostowanie statycznych zasobów w wielu lokalizacjach lub pochodzeniech i obsługują je z globalnych sieci o wysokiej szybkości. W zależności od rodzaju zawartości, którą chcesz hostować w Office 365 CDN, możesz dodać pochodzenie **publiczne, pochodzenie** prywatne lub oba te źródła.

![Office 365 CDN diagram koncepcyjny.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN diagram koncepcyjny")

Zawartość pochodzenia **publicznego** w obrębie Office 365 CDN jest dostępna anonimowo i może być dostępna dla każdego, kto ma adresy URL do hostowanych zasobów. Ponieważ dostęp do zawartości w pochodzenia publicznego jest anonimowy, należy ich używać tylko do buforowania nie poufnych treści ogólnych, takich jak pliki JavaScript, skrypty, ikony i obrazy. Typ Office 365 CDN jest domyślnie używany do pobierania ogólnych zasobów zasobów, takich Office 365 aplikacji klienckich z publicznego pochodzenia.

**Pochodzenie** prywatne w obrębie Office 365 CDN prywatnego dostępu do zawartości użytkownika, takiej jak biblioteki SharePoint dokumentów online, witryny i własne obrazy. Dostęp do zawartości w pochodzenie prywatnej jest zabezpieczony dynamicznie generowanymi tokenami, dzięki czemu dostęp do niej mogą uzyskiwać tylko użytkownicy z uprawnieniami do oryginalnej biblioteki dokumentów lub lokalizacji przechowywania. Pochodzenie prywatne w sieci Office 365 CDN może być używane tylko do zawartości online usługi SharePoint, a dostęp do zasobów możesz uzyskać tylko za pośrednictwem przekierowania z dzierżawy usługi SharePoint Online.

Usługa Office 365 CDN jest zawarta w ramach subskrypcji usługi SharePoint Online.

Aby uzyskać więcej informacji na temat korzystania z Office 365 CDN, zobacz Używanie sieci dostarczania zawartości Office 365 z usługą [SharePoint Online](use-microsoft-365-cdn-with-spo.md).

Aby obejrzeć serię krótkich klipów wideo, które zawierają pojęciowe informacje i INFORMACJE NA temat korzystania z Office 365 CDN, odwiedź kanał SharePoint [Developer Patterns and Practices w serwisie YouTube](https://aka.ms/sppnp-videos).

## <a name="other-microsoft-cdns"></a>Inne sieci CDN firmy Microsoft

Mimo że nie jest to część sieci Office 365 CDN, możesz używać tych sieci CDN w dzierżawie usługi Office 365 na potrzeby uzyskiwania dostępu do bibliotek programistów programu SharePoint, kodu niestandardowego i innych celów, które nie są objęte zakresem Office 365 CDN.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>Począwszy od 3 kwartału 2020 SharePoint online rozpocznie się buforowanie klipów wideo na Azure CDN w celu obsługi ulepszonego odtwarzania wideo i lepszej niezawodności. Popularne klipy wideo będą przesyłane strumieniowo z CDN punkt końcowy najbliższy użytkownikowi. Te dane pozostaną w granicach Microsoft 365 zgodności. Jest to bezpłatna usługa dla wszystkich dzierżaw i konfiguracja nie wymaga żadnych działań ze strony klienta.

Za pomocą programu **Azure CDN** można wdrożyć własne wystąpienie programu CDN na temat hostowania niestandardowych składników Web Part, bibliotek i innych zasobów zasobów, co pozwala na stosowanie kluczy dostępu do magazynu programu CDN i większą kontrolę nad konfiguracją CDN. Korzystanie z Azure CDN jest bezpłatne i wymaga subskrypcji platformy Azure.

Aby uzyskać więcej informacji na temat konfigurowania wystąpienia Azure CDN, zobacz Szybki [start:](/azure/cdn/cdn-create-a-storage-account-with-cdn) integrowanie konta magazynu platformy Azure z usługą Azure CDN.

Aby uzyskać przykład sposobu host Azure CDN SharePoint składników Web Part po stronie klienta, zobacz SharePoint składników [Web Part](/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn) po stronie klienta w Azure CDN.

Aby uzyskać informacje na temat Azure CDN PowerShell, zobacz [Zarządzanie Azure CDN za pomocą programu PowerShell](/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Program Microsoft Ajax CDN

Ajax **CDN** firmy Microsoft to CDN tylko do odczytu, który oferuje wiele popularnych bibliotek programistów, w tym jQuery (i wszystkie inne biblioteki), ASP.NET Ajax, Bootstrap, Knockout.js i inne.
  
Aby uwzględnić te skrypty w projekcie, zamień wszelkie odwołania do tych publicznie dostępnych bibliotek na odwołania do adresu CDN, zamiast uwzględniać go w samym projekcie. Aby na przykład utworzyć link do jQuery, użyj następującego kodu:

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Aby uzyskać więcej informacji na temat używania programu Microsoft Ajax CDN, zobacz [Program Microsoft Ajax CDN](/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Jak Office 365 zawartości z witryny CDN?

Niezależnie od CDN konfigurowane dla dzierżawy usługi Office 365 podstawowy proces pobierania danych jest taki sam.

1. Klient (przeglądarka lub aplikacja Office) żąda danych z Office 365.

2. Office 365 zwraca dane bezpośrednio do klienta lub, jeśli dane są częścią zestawu zawartości hostowanej przez usługę CDN, przekierowuje klienta do adresu URL CDN URL.

    a. Jeśli dane są już zapisane w pamięci podręcznej  na publicznym pochodzenia, klient pobiera dane bezpośrednio z najbliższej CDN lokalizacji klienta.

    b. Jeśli dane są już zapisane w pamięci podręcznej  na podstawie pochodzenia prywatnego, usługa CDN sprawdza Office 365 uprawnień konta użytkownika dla tego pochodzenia. Jeśli masz uprawnienia, aplikacja SharePoint Online dynamicznie generuje niestandardowy adres URL składający się ze ścieżki do zasobu w skoroszycie CDN i dwóch tokenów dostępu, a następnie zwraca niestandardowy adres URL do klienta. Klient następnie pobiera dane bezpośrednio z najbliższej CDN lokalizacji klienta przy użyciu niestandardowego adresu URL.

3. Jeśli dane nie są buforowane w CDN, węzeł CDN żąda danych z programu Office 365, Office 365 następnie buforuje dane przez okres, po którym klient pobiera dane.

Centrum CDN znajduje się najbliżej przeglądarki użytkownika i korzystając z przekierowania, pobiera z tego miejsca żądane dane. CDN przekierowywanie jest szybkie i pozwala zaoszczędzić czas pobierania dla użytkowników.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Jak skonfigurować sieć, aby cdns działały najlepiej z siecią Office 365?

Zminimalizowanie opóźnień między klientami w sieci i CDN jest kluczowym czynnikiem zapewniającym optymalną wydajność. Za pomocą najlepszych rozwiązań opisanych w tece Zarządzanie punktami końcowymi programu [Office 365](managing-office-365-endpoints.md) można upewnić się, że konfiguracja sieci zezwala przeglądarkom klienckim na bezpośredni dostęp do serwera CDN zamiast routingu ruchu programu CDN za pośrednictwem centralnych serwerów proxy w celu uniknięcia wprowadzania niepotrzebnych opóźnień.

Ponadto można przeczytać zasady [Office 365 łączności](./microsoft-365-network-connectivity-principles.md) sieciowej, aby zrozumieć koncepcje optymalizacji Office 365 sieci.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Czy istnieje lista wszystkich sieci CDN, które Office 365 używane?

Sieci CDN, z których korzystasz Office 365, zawsze mogą ulec zmianie i w wielu CDN w przypadku niedostępności jest skonfigurowanych wielu partnerów. Główne sieci CDN używane przez Office 365 to:

|CDN  |Company  |Użycie  |Link  |
|---------|---------|---------|---------|
|Office 365 CDN     |Microsoft Azure         |Ogólne zasoby dla osób publicznie SharePoint zawartości użytkownika  pochodzenia prywatnego         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Azure CDN     |Microsoft         |Kod niestandardowy, SharePoint Framework rozwiązania         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Program Microsoft Ajax CDN (tylko do odczytu)     |Microsoft         |Popularne biblioteki dla Ajax, jQuery, ASP.NET, Bootstrap, Knockout.js itp.         |[Program Microsoft Ajax CDN](/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Jaki wzrost wydajności daje CDN?

Istnieje wiele czynników związanych z mierzenie konkretnych różnic w wydajności między danymi pobranymi bezpośrednio z usługi Office 365 a danymi pobranymi z określonego serwera CDN, takimi jak lokalizacja względem dzierżawy i najbliższego punktu końcowego programu CDN, liczba zasobów na stronie, które są obsługiwane przez CDN, oraz zmiany chwilowe w opóźnieniu i przepustowości sieci. Jednak prosty test A/B może pomóc pokazać różnicę w czasie pobierania konkretnego pliku.

Na poniższych zrzutach ekranu pokazano różnice w szybkości pobierania między natywnym plikiem w programie Office 365 a tym samym plikiem hostowany w programie [Microsoft Ajax Content Delivery Network](/aspnet/ajax/cdn/overview). Te zrzuty ekranu znajdują się na **karcie Sieć** w narzędziach dewelopernych programu Internet Explorer 11. Te zrzuty ekranu pokazują opóźnienie popularnej biblioteki jQuery. Aby w programie Internet Explorer był wyświetlana ta karta, naciśnij klawisz **F12** i wybierz kartę Sieć symbolizną za pomocą Wi-Fi sieci.
  
![Zrzut ekranu przedstawiający sieć F12.](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Ten zrzut ekranu przedstawia bibliotekę przekazanych do galerii stron wzorcowych w samej SharePoint Online. Czas przekazywania biblioteki: 1,51 sekundy.
  
![Zrzut ekranu przedstawiający czas ładowania 1,51s.](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Drugi zrzut ekranu przedstawia ten sam plik dostarczony przez firmę Microsoft w CDN. Tym razem opóźnienie wynosi około 496 milisekund. Jest to duże ulepszenie i pokazuje, że łączny czas pobierania obiektu został o łączną sekundę o kilka sekund zaniżany.
  
![Zrzut ekranu przedstawiający czasy ładowania w 469 ms.](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Czy moje dane są bezpieczne?

Dbamy o ochronę danych, na których działa Twoja firma. Dane przechowywane w Office 365 CDN są szyfrowane zarówno podczas przesyłania, jak i podczas przechowywania, a dostęp do danych w Office 365 SharePoint CDN Office 365 jest zabezpieczony uprawnieniami użytkownika i autoryzacją tokenu. Żądania danych w tym Office 365 SharePoint CDN muszą być określane (przekierowywany) z dzierżawy usługi Office 365 lub token autoryzacji nie zostaną wygenerowane.

Aby zapewnić bezpieczeństwo danych, zalecamy, aby nigdy nie przechowywać zawartości użytkownika ani innych poufnych danych w publicznym CDN. Ponieważ dostęp do danych w publicznym CDN jest anonimowy, publiczne sieci CDN powinny być używane tylko do hostować ogólną zawartość, taką jak pliki skryptów sieci Web, ikony, obrazy i inne zasoby, które nie są poufne.

> [!NOTE]
> 3. Dostawcy usług CDN mogą spełniać standardy prywatności i zgodności, które różnią się od zobowiązań opisanych w Centrum Office 365 zaufania. Dane z pamięci podręcznej za pośrednictwem usługi CDN mogą być niezgodne z Warunkami przetwarzania danych (DPT, Data Processing Terms) firmy Microsoft i mogą być spoza granic zgodności Centrum Office 365 zaufania.

Aby uzyskać szczegółowe informacje na temat ochrony prywatności i ochrony danych Office 365 CDN, odwiedź następujące strony:  

- Dowiedz się więcej o Office 365 prywatności i ochrony danych w Centrum [zaufania firmy Microsoft](https://www.microsoft.com/trustcenter)
- Dowiedz się więcej o ochronie prywatności i ochronie danych firmy [Akamai w Centrum zaufania prywatności firmy Akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp).
- Dowiedz się więcej o ochronie prywatności i ochronie danych na platformie [Azure w Centrum zaufania platformy Azure.](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Jak mogę zabezpieczyć sieć za pomocą tych wszystkich usług innych firm?

Korzystanie z rozbudowanej zestawu usług partnerskich umożliwia skalowanie Office 365 spełnianie wymagań dotyczących dostępności, a także usprawnianie korzystania z usług Office 365. Usługi innych firm, Office 365 zawierają zarówno listy odwołań certyfikatów, takie jak crl.microsoft.com lub sa.symcb.com, i sieci CDN, takie jak r3.res.outlook.com. Każda CDN FQDN wygenerowana przez Office 365 jest niestandardową dn FQDN dla Office 365. Jeśli na żądanie usługi Office 365 trafisz do domeny FQDN, możesz mieć pewność, że dostawca usługi CDN kontroluje fQDN i zawartość bazowa w tej lokalizacji.
  
Dla klientów, którzy chcą oddzielić żądania przeznaczone dla centrum danych firmy Microsoft lub programu Office 365 od żądań przeznaczonych dla innych firm, napisaliśmy wskazówki dotyczące zarządzania punktami końcowymi usługi [Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Czy istnieje lista wszystkich sieci FQDN  wykorzystaj sieci CDN?

Lista sieci FQNS i sposób, w jaki wykorzystują one sieci CDN, zmieniają się w czasie. Skorzystaj z opublikowanej [przez nas](./urls-and-ip-address-ranges.md) strony Office 365 URL i zakresów adresów IP, aby uzyskać aktualne informacje na temat najnowszych sieci FQN wykorzystaj sieci CDN.

Za pomocą usługi sieci [Web Office 365](microsoft-365-ip-web-service.md) i adresu URL możesz również zażądać bieżących adresów URL Office 365 i zakresów adresów IP w formacie CSV lub JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Czy mogę używać własnej sieci CDN i buforować zawartość w mojej sieci lokalnej?

Stale szukamy nowych sposobów obsługi potrzeb naszych klientów i obecnie badamy użycie rozwiązań serwera proxy buforowania i innych lokalnych rozwiązań CDN biznesowych.

Chociaż nie jest on częścią programu Office 365 CDN **Azure CDN**, można go też używać do hostowania niestandardowych składników Web Part, bibliotek i innych zasobów zasobów, co pozwala na stosowanie klawiszy dostępu do magazynu programu CDN i stosowanie większej kontroli nad konfiguracją CDN. Korzystanie z Azure CDN jest bezpłatne i wymaga subskrypcji platformy Azure. Aby uzyskać więcej informacji na temat konfigurowania wystąpienia Azure CDN, zobacz Szybki [start:](/azure/cdn/cdn-create-a-storage-account-with-cdn) integrowanie konta magazynu platformy Azure z usługą Azure CDN.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Korzystam z usługi Azure ExpressRoute do Office 365, czy to coś zmienia?

[Usługa Azure ExpressRoute dla usługi Office 365](azure-expressroute.md) udostępnia dedykowane połączenie Office 365 danych oddzielone od publicznego Internetu. Oznacza to, że klienci nadal będą musieli łączyć się za pośrednictwem połączeń innych niż usługa ExpressRoute, aby łączyć się z sieciami CDN i inną infrastrukturą firmy Microsoft, która nie jest jawnie uwzględniona na liście usług obsługiwanych przez usługę ExpressRoute. Aby uzyskać więcej informacji na temat sposobu skierowania określonego ruchu, na przykład żądań przeznaczonych dla sieci CDN, zobacz Office 365 [zarządzania ruchem sieciowym](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Czy mogę używać sieci CDN SharePoint lokalnym serwerze?

Używanie sieci CDN ma sens tylko w kontekście SharePoint online i należy unikać go w przypadku SharePoint serwera. Wynika to z tego, że wszystkie zalety korzystania z lokalizacji geograficznej nie mają miejsca, jeśli serwer znajduje się lokalnie lub znajduje się w pobliżu. Ponadto, jeśli istnieje połączenie sieciowe z serwerami, na których jest hostowana, witryna może być używana bez połączenia internetowego i dlatego nie może pobierać CDN plików. W przeciwnym razie należy używać CDN, jeśli jest dostępna i stabilna dla biblioteki i plików potrzebnych dla witryny.
  
Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/o365cdns]()
  
## <a name="see-also"></a>Zobacz też

[Office 365 zasad łączności sieciowej](./microsoft-365-network-connectivity-principles.md)

[Ocena Office 365 sieci](assessing-network-connectivity.md)

[Zarządzanie Office 365 punktami końcowymi](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](./urls-and-ip-address-ranges.md)

[Używanie sieci Office 365 dostarczania zawartości z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Centrum zaufania firmy Microsoft](https://www.microsoft.com/trustcenter)

[Dostosowywanie Office 365 wydajności](tune-microsoft-365-performance.md)
