---
title: Sieci dostarczania zawartości
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Skorzystaj z tych informacji, aby dowiedzieć się, jak Office 365 używa sieci dostarczania zawartości (CDN) w celu zwiększenia wydajności.
ms.openlocfilehash: a2ed395ba400e09b87777c381e140a38e32d9210
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754803"
---
# <a name="content-delivery-networks-cdns"></a>Sieci dostarczania zawartości (CDN)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Sieci CDN pomagają zachować Office 365 szybkie i niezawodne dla użytkowników końcowych. Usługi w chmurze, takie jak Office 365 używają sieci CDN do buforowania statycznych zasobów bliżej przeglądarek żądających ich w celu przyspieszenia pobierania i zmniejszenia postrzeganego opóźnienia użytkowników końcowych. Informacje zawarte w tym temacie pomogą Ci dowiedzieć się więcej na temat sieci dostarczania zawartości (CDN) i sposobu ich użycia przez Office 365.

## <a name="what-exactly-is-a-cdn"></a>Co dokładnie jest CDN?

CDN to geograficznie rozproszona sieć składająca się z serwerów proxy i serwerów plików w centrach danych połączonych przez szybkie sieci szkieletowe. Sieci CDN służą do skrócenia czasu opóźnienia i ładowania określonego zestawu plików i obiektów w witrynie internetowej lub usłudze. CDN może mieć wiele tysięcy punktów końcowych do optymalnego obsługi żądań przychodzących z dowolnej lokalizacji.

Sieci CDN są często używane w celu zapewnienia szybszego pobierania zawartości ogólnej dla witryny internetowej lub usługi, takiej jak pliki Javascript, ikony i obrazy, a także mogą zapewnić prywatny dostęp do zawartości użytkownika, takiej jak pliki w bibliotekach dokumentów usługi SharePoint Online, plikach multimedialnych przesyłania strumieniowego i kodzie niestandardowym.

Sieci CDN są używane przez większość usług w chmurze dla przedsiębiorstw. Usługi w chmurze, takie jak Office 365, mają miliony klientów pobierających jednocześnie mieszankę zastrzeżonych treści (takich jak wiadomości e-mail) i zawartości ogólnej (takiej jak ikony). Bardziej wydajne jest umieszczanie obrazów używanych przez wszystkich użytkowników, takich jak ikony, tak blisko komputera użytkownika, jak to możliwe. Tworzenie CDN centrów danych, które przechowują tę ogólną zawartość w każdym obszarze metropolitalnym, a nawet w każdym głównym centrum internetowym na całym świecie, nie jest praktyczne, dlatego niektóre z tych sieci CDN są współużytkowane.

## <a name="how-do-cdns-make-services-work-faster"></a>Jak sieci CDN sprawiają, że usługi działają szybciej?

Pobieranie typowych obiektów, takich jak obrazy witryny i ikony w kółko, może zająć przepustowość sieci, która może być lepiej używana do pobierania ważnych treści osobistych, takich jak poczta e-mail lub dokumenty. Ponieważ Office 365 korzysta z architektury obejmującej sieci CDN, ikony, skrypty i inną ogólną zawartość można pobrać z serwerów bliżej komputerów klienckich, co przyspiesza pobieranie. Oznacza to szybszy dostęp do zawartości osobistej, która jest bezpiecznie przechowywana w Office 365 centrach danych.

Sieci CDN pomagają zwiększyć wydajność usługi w chmurze na kilka sposobów:

- Sieci CDN przenoszą część obciążenia związanego z pobieraniem plików i sieci od usługi w chmurze, zwalniając zasoby usługi w chmurze na potrzeby obsługi zawartości użytkowników i innych usług, zmniejszając potrzebę obsługi żądań dotyczących zasobów statycznych.
- Sieci CDN są przeznaczone do zapewniania dostępu do plików o małych opóźnieniach przez implementowanie sieci o wysokiej wydajności i serwerów plików oraz wykorzystanie zaktualizowanych protokołów sieciowych, takich jak [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) , z wysoce wydajną kompresją i multipleksowaniem żądań.
- CDN sieci używają wielu globalnie rozproszonych punktów końcowych, aby udostępnić zawartość jak najbliżej użytkowników.

## <a name="the-office-365-cdn"></a>Office 365 CDN

Wbudowana Office 365 Content Delivery Network (CDN) umożliwia administratorom Office 365 zapewnienie lepszej wydajności stron SharePoint Online organizacji przez buforowanie zasobów statycznych bliżej przeglądarek żądających ich, co pomaga przyspieszyć pobieranie i zmniejszyć opóźnienia. Office 365 CDN używa [protokołu HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) w celu zwiększenia szybkości kompresji i pobierania.

> [!NOTE]
> Office 365 CDN jest dostępna tylko dla dzierżawców w chmurze **produkcyjnej** (na całym świecie). Dzierżawy w chmurach rządowych USA, Chin i Niemiec nie obsługują obecnie Office 365 CDN.

Office 365 CDN składa się z wielu sieci CDN, które umożliwiają hostowanie zasobów statycznych w wielu lokalizacjach lub _źródłach_ oraz obsługę ich z globalnych sieci o dużej szybkości. W zależności od rodzaju zawartości, którą chcesz hostować w Office 365 CDN, możesz dodać **źródła publiczne**, **źródła prywatne** lub oba te elementy.

![Office 365 CDN diagram koncepcyjny.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN diagram koncepcyjny")

Zawartość w **źródłach publicznych** w Office 365 CDN jest dostępna anonimowo i może uzyskać do niej dostęp każdy, kto ma adresy URL hostowanych zasobów. Ponieważ dostęp do zawartości w źródłach publicznych jest anonimowy, należy ich używać tylko do buforowania niewrażliwej zawartości ogólnej, takiej jak pliki Javascript, skrypty, ikony i obrazy. Office 365 CDN jest domyślnie używana do pobierania ogólnych zasobów zasobów, takich jak Office 365 aplikacje klienckie z publicznego źródła.

**Prywatne** źródła w Office 365 CDN zapewniają prywatny dostęp do zawartości użytkownika, takiej jak biblioteki dokumentów SharePoint Online, witryny i zastrzeżone obrazy. Dostęp do zawartości w prywatnych źródłach jest zabezpieczony za pomocą dynamicznie generowanych tokenów, dzięki czemu użytkownicy mogą uzyskiwać do niej dostęp tylko z uprawnieniami do oryginalnej biblioteki dokumentów lub lokalizacji magazynu. Źródła prywatne w Office 365 CDN mogą być używane tylko do SharePoint zawartości online i można uzyskiwać dostęp tylko do zasobów za pośrednictwem przekierowania z dzierżawy usługi SharePoint Online.

Usługa Office 365 CDN jest uwzględniona w ramach subskrypcji usługi SharePoint Online.

Aby uzyskać więcej informacji na temat korzystania z Office 365 CDN, zobacz [Korzystanie z sieci dostarczania zawartości Office 365 z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).

Aby obejrzeć serię krótkich filmów wideo, które zawierają informacje koncepcyjne i HOWTO dotyczące korzystania z Office 365 CDN, odwiedź [kanał SharePoint Developer Patterns and Practices w serwisie YouTube](https://aka.ms/sppnp-videos).

## <a name="other-microsoft-cdns"></a>Inne sieci CDN firmy Microsoft

Chociaż nie jest to część Office 365 CDN, możesz użyć tych sieci CDN w dzierżawie Office 365, aby uzyskać dostęp do bibliotek programistycznych SharePoint, kodu niestandardowego i innych celów, które wykraczają poza zakres Office 365 CDN.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>Począwszy od 3. kwartału 2020 r., usługa SharePoint Online rozpocznie buforowanie filmów wideo na Azure CDN w celu obsługi ulepszonego odtwarzania wideo i niezawodności. Popularne filmy wideo będą przesyłane strumieniowo z punktu końcowego CDN najbliżej użytkownika. Te dane pozostaną w granicach Microsoft Purview. Jest to bezpłatna usługa dla wszystkich dzierżaw i nie wymaga żadnej akcji klienta do skonfigurowania.

Za pomocą **Azure CDN** można wdrożyć własne wystąpienie CDN na potrzeby hostowania niestandardowych składników Web Part, bibliotek i innych zasobów zasobów, co umożliwia stosowanie kluczy dostępu do magazynu CDN i wywieranie większej kontroli nad konfiguracją CDN. Korzystanie z Azure CDN nie jest bezpłatne i wymaga subskrypcji platformy Azure.

Aby uzyskać więcej informacji na temat konfigurowania wystąpienia Azure CDN, zobacz [Szybki start: integrowanie konta usługi Azure Storage z Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

Aby uzyskać przykład użycia Azure CDN do hostowania SharePoint składników Web Part, zobacz [Deploy your SharePoint client-side web part to Azure CDN (Wdrażanie składnika Web Part po stronie klienta SharePoint w celu Azure CDN](/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn)).

Aby uzyskać informacje na temat modułu Azure CDN programu PowerShell, zobacz [Zarządzanie Azure CDN za pomocą programu PowerShell](/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

**CDN Ajax** firmy Microsoft to CDN tylko do odczytu, która oferuje wiele popularnych bibliotek programistycznych, w tym jQuery (i wszystkie inne biblioteki), ASP.NET Ajax, Bootstrap, Knockout.js i inne.
  
Aby uwzględnić te skrypty w projekcie, po prostu zastąp wszelkie odwołania do tych publicznie dostępnych bibliotek odwołaniami do adresu CDN zamiast uwzględniać je w samym projekcie. Na przykład użyj następującego kodu, aby połączyć się z zapytaniem jQuery:

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Aby uzyskać więcej informacji na temat korzystania z CDN Microsoft Ajax, zobacz [Microsoft Ajax CDN](/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Jak Office 365 używać zawartości z CDN?

Niezależnie od tego, jakie CDN skonfigurować dla dzierżawy Office 365, podstawowy proces pobierania danych jest taki sam.

1. Klient (przeglądarka lub aplikacja kliencka Office) żąda danych z Office 365.

2. Office 365 zwraca dane bezpośrednio do klienta lub, jeśli dane są częścią zestawu zawartości hostowanej przez CDN, przekierowuje klienta do adresu URL CDN.

    a. Jeśli dane są już buforowane w _publicznym_ pochodzeniu, klient pobiera dane bezpośrednio z najbliższej CDN lokalizacji do klienta.

    b. Jeśli dane są już buforowane w _prywatnym_ pochodzeniu, usługa CDN sprawdza uprawnienia Office 365 konta użytkownika do źródła. Jeśli masz uprawnienia, usługa SharePoint Online dynamicznie generuje niestandardowy adres URL składający się ze ścieżki do zasobu w CDN i dwóch tokenów dostępu oraz zwraca niestandardowy adres URL do klienta. Następnie klient pobiera dane bezpośrednio z najbliższej lokalizacji CDN do klienta przy użyciu niestandardowego adresu URL.

3. Jeśli dane nie są buforowane w CDN, węzeł CDN żąda danych z Office 365, a następnie buforuje dane przez czas po pobraniu danych przez klienta.

CDN określa najbliższe centrum danych w przeglądarce użytkownika, a przy użyciu przekierowania pobiera stamtąd żądane dane. CDN przekierowanie jest szybkie i może zaoszczędzić użytkownikom dużo czasu pobierania.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Jak skonfigurować sieć, aby sieci CDN działały najlepiej z Office 365?

Minimalizowanie opóźnień między klientami w sieci i punktami końcowymi CDN jest kluczowym czynnikiem zapewniającym optymalną wydajność. Najlepsze rozwiązania opisane w temacie [Zarządzanie punktami końcowymi Office 365](managing-office-365-endpoints.md) umożliwiają przeglądarce klienckiej bezpośredni dostęp do CDN zamiast routingu ruchu CDN za pośrednictwem centralnych serwerów proxy w celu uniknięcia niepotrzebnych opóźnień.

Możesz również przeczytać [Office 365 Zasady łączności sieciowej](./microsoft-365-network-connectivity-principles.md), aby zrozumieć pojęcia związane z optymalizacją Office 365 wydajności sieci.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Czy istnieje lista wszystkich sieci CDN, których Office 365 używa?

Sieci CDN używane przez Office 365 zawsze mogą ulec zmianie i w wielu przypadkach istnieje wiele CDN partnerów skonfigurowanych w przypadku niedostępności jednej z nich. Podstawowe sieci CDN używane przez Office 365 to:

|CDN  |Company  |Zastosowanie  |Link  |
|---------|---------|---------|---------|
|Office 365 CDN     |Microsoft Azure         |Zasoby ogólne w źródłach publicznych, SharePoint zawartości użytkownika w źródłach prywatnych         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Azure CDN     |Microsoft         |Kod niestandardowy, rozwiązania SharePoint Framework         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (tylko do odczytu)     |Microsoft         |Typowe biblioteki ajax, jQuery, ASP.NET, Bootstrap, Knockout.js itp.         |[Microsoft Ajax CDN](/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Jakie korzyści z wydajności zapewnia CDN?

Mierzenie określonych różnic w wydajności między danymi pobranymi bezpośrednio z Office 365 i danych pobranych z określonego CDN, takich jak lokalizacja w stosunku do dzierżawy i najbliższego punktu końcowego CDN, liczba zasobów na stronie obsługiwanej przez CDN oraz przejściowe zmiany opóźnienia i przepustowości sieci. Jednak prosty test A/B może pomóc pokazać różnicę w czasie pobierania określonego pliku.

Poniższe zrzuty ekranu ilustrują różnicę w szybkości pobierania między natywną lokalizacją pliku w Office 365 a tym samym plikiem hostowanym w [Content Delivery Network Microsoft Ajax](/aspnet/ajax/cdn/overview). Te zrzuty ekranu pochodzą z karty **Sieć** w narzędziach programistycznych programu Internet Explorer 11. Te zrzuty ekranu pokazują opóźnienie w popularnej bibliotece jQuery. Aby wyświetlić ten ekran, w programie Internet Explorer naciśnij **klawisz F12** i wybierz kartę **Sieć** , która jest symbolizowana ikoną Wi-Fi.
  
![Zrzut ekranu przedstawiający sieć F12.](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Ten zrzut ekranu przedstawia bibliotekę przekazaną do galerii stron wzorcowych w samej witrynie SharePoint Online. Czas przekazania biblioteki wynosi 1,51 sekundy.
  
![Zrzut ekranu przedstawiający czas ładowania 1.51s.](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Drugi zrzut ekranu przedstawia ten sam plik dostarczony przez CDN firmy Microsoft. Tym razem opóźnienie wynosi około 496 milisekund. Jest to duża poprawa i pokazuje, że cała sekunda jest ogolona z całkowitego czasu pobierania obiektu.
  
![Zrzut ekranu przedstawiający czas ładowania w 469 ms.](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Czy moje dane są bezpieczne?

Dokładamy szczególnej wagi, aby chronić dane, które prowadzi Twoją firmę. Dane przechowywane w Office 365 CDN są szyfrowane zarówno podczas przesyłania, jak i w spoczynku, a dostęp do danych w Office 365 SharePoint CDN jest zabezpieczony za pomocą Office 365 uprawnień użytkownika i autoryzacji tokenu. Żądania dotyczące danych w Office 365 SharePoint CDN muszą być kierowane (przekierowywane) z dzierżawy Office 365 lub token autoryzacji nie zostanie wygenerowany.

Aby zapewnić bezpieczeństwo danych, zalecamy, aby nigdy nie przechowywać zawartości użytkownika ani innych poufnych danych w publicznym CDN. Ponieważ dostęp do danych w publicznym CDN jest anonimowy, publiczne sieci CDN powinny być używane tylko do hostowania zawartości ogólnej, takiej jak pliki skryptów sieci Web, ikony, obrazy i inne niewrażliwe zasoby.

> [!NOTE]
> Dostawcy CDN innych firm mogą mieć standardy prywatności i zgodności, które różnią się od zobowiązań opisanych przez centrum zaufania Office 365. Dane buforowane za pośrednictwem usługi CDN mogą nie być zgodne z warunkami przetwarzania danych firmy Microsoft (DPT) i mogą znajdować się poza granicami zgodności centrum zaufania Office 365.

Aby uzyskać szczegółowe informacje na temat prywatności i ochrony danych dla dostawców Office 365 CDN, odwiedź następujące strony:  

- Dowiedz się więcej o ochronie prywatności i danych Office 365 w [Centrum zaufania firmy Microsoft](https://www.microsoft.com/trustcenter)
- Dowiedz się więcej o ochronie prywatności i danych w usłudze [Akamai w Centrum zaufania prywatności akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- Dowiedz się więcej o ochronie prywatności i danych na platformie Azure w [Centrum zaufania platformy Azure](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Jak mogę zabezpieczyć sieć za pomocą tych wszystkich usług innych firm?

Korzystanie z rozbudowanego zestawu usług partnerskich umożliwia Office 365 skalowanie i spełnianie wymagań dotyczących dostępności oraz ulepszanie środowiska użytkownika podczas korzystania z Office 365. Usługi innych firm Office 365 wykorzystują zarówno listy odwołania certyfikatów, takie jak crl.microsoft.com lub sa.symcb.com, jak i sieci CDN, takie jak r3.res.outlook.com. Każda CDN nazwa FQDN generowana przez Office 365 jest niestandardową nazwą FQDN dla Office 365. Jeśli na żądanie Office 365 zostanie wysłana nazwa FQDN, możesz mieć pewność, że dostawca CDN kontroluje nazwę FQDN i podstawową zawartość w tej lokalizacji.
  
W przypadku klientów, którzy chcą oddzielić żądania przeznaczone dla firmy Microsoft lub Office 365 centrum danych od żądań przeznaczonych dla innych firm, napisaliśmy wskazówki dotyczące [zarządzania punktami końcowymi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Czy istnieje lista wszystkich nazw FQDN korzystających z sieci CDN?

Lista nazw FQDN i sposób ich wykorzystania zmieniają się wraz z upływem czasu. Zapoznaj się z opublikowaną stroną [adresów URL Office 365 i zakresów adresów IP](./urls-and-ip-address-ranges.md), aby uzyskać aktualne informacje o najnowszych nazwach FQDN korzystających z sieci CDN.

Możesz również użyć [Office 365 usługi sieci Web adresów IP i adresów URL](microsoft-365-ip-web-service.md), aby zażądać bieżących adresów URL Office 365 i zakresów adresów IP sformatowanych jako CSV lub JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Czy mogę używać własnych CDN i buforować zawartość w sieci lokalnej?

Nieustannie szukamy nowych sposobów obsługi potrzeb naszych klientów i obecnie badamy korzystanie z rozwiązań serwera proxy buforowania i innych lokalnych rozwiązań CDN.

Chociaż nie jest to część Office 365 CDN, możesz również użyć **Azure CDN** do hostowania niestandardowych składników Web Part, bibliotek i innych zasobów zasobów, co umożliwia stosowanie kluczy dostępu do magazynu CDN i wywieranie większej kontroli nad konfiguracją CDN. Korzystanie z Azure CDN nie jest bezpłatne i wymaga subskrypcji platformy Azure. Aby uzyskać więcej informacji na temat konfigurowania wystąpienia Azure CDN, zobacz [Szybki start: integrowanie konta usługi Azure Storage z Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Używam usługi Azure ExpressRoute dla Office 365, czy to coś zmienia?

[Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md) zapewnia dedykowane połączenie z infrastrukturą Office 365, która jest oddzielona od publicznego Internetu. Oznacza to, że klienci nadal będą musieli łączyć się za pośrednictwem połączeń innych niż ExpressRoute, aby nawiązać połączenie z sieciami CDN i inną infrastrukturą firmy Microsoft, która nie jest jawnie uwzględniona na liście usług obsługiwanych przez usługę ExpressRoute. Aby uzyskać więcej informacji o sposobie kierowania określonego ruchu, takiego jak żądania przeznaczone dla sieci CDN, zobacz [Office 365 zarządzanie ruchem sieciowym](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Czy mogę używać sieci CDN z lokalnym serwerem SharePoint?

Używanie sieci CDN ma sens tylko w kontekście usługi SharePoint Online i należy ich unikać w przypadku serwera SharePoint. Wynika to z faktu, że wszystkie zalety lokalizacji geograficznej nie są prawdziwe, jeśli serwer i tak znajduje się lokalnie lub geograficznie blisko. Ponadto jeśli istnieje połączenie sieciowe z serwerami, na których jest hostowane, lokacja może być używana bez połączenia z Internetem i w związku z tym nie może pobrać plików CDN. W przeciwnym razie należy użyć CDN, jeśli istnieje jeden dostępny i stabilny dla biblioteki i plików potrzebnych dla witryny.
  
Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/o365cdns]()
  
## <a name="see-also"></a>Zobacz też

[zasady łączności sieciowej Office 365](./microsoft-365-network-connectivity-principles.md)

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](./urls-and-ip-address-ranges.md)

[Korzystanie z sieci dostarczania zawartości Office 365 z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Centrum zaufania firmy Microsoft](https://www.microsoft.com/trustcenter)

[Dostrajanie wydajności Office 365](tune-microsoft-365-performance.md)
