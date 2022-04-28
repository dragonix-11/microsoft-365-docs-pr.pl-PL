---
title: Wprowadzenie do dostrajania wydajności dla usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: W tym artykule wyjaśniono, jakie konkretne aspekty należy wziąć pod uwagę podczas projektowania stron, aby uzyskać najlepszą wydajność w usłudze SharePoint Online.
ms.openlocfilehash: b31696766d3201b6677bf0c63108fad72c3ed49d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100748"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Wprowadzenie do dostrajania wydajności dla usługi SharePoint Online

W tym artykule wyjaśniono, jakie konkretne aspekty należy wziąć pod uwagę podczas projektowania stron, aby uzyskać najlepszą wydajność w usłudze SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>metryki usługi SharePoint Online

Następujące ogólne metryki dla usługi SharePoint Online zapewniają rzeczywiste dane dotyczące wydajności:
  
- Jak szybko ładują się strony
    
- Ile rund jest wymaganych na stronę
    
- Problemy z usługą
    
- Inne rzeczy, które powodują obniżenie wydajności
    
### <a name="conclusions-reached-because-of-the-data"></a>Wnioski osiągnięte z powodu danych

Dane mówią nam:
  
- Większość stron działa dobrze w usłudze SharePoint Online.
    
- Strony, które nie są dostosowane, ładują się szybko.
    
- OneDrive dla Firm, witryny zespołu i strony systemowe, takie jak _layouts itp., są szybkie do załadowania.
    
- Najwolniejsze 1% stron SharePoint Online zajmuje ponad 5000 milisekund.
    
Jednym z prostych testów porównawczych, których można użyć, jest pomiar wydajności przez porównanie czasu ładowania własnego portalu z czasem ładowania strony głównej OneDrive dla Firm, ponieważ używa ona kilku dostosowanych funkcji. Często jest to pierwszy krok, który pomoc techniczna poprosi o ukończenie rozwiązywania problemów z wydajnością sieci.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Używanie standardowego konta użytkownika podczas sprawdzania wydajności

Administrator zbioru witryn, właściciel witryny, edytor lub współautor należą do innych grup zabezpieczeń, mają więcej uprawnień i w związku z tym mają dodatkowe elementy, które SharePoint ładowane na stronie.
  
Ma to zastosowanie do SharePoint lokalnych i SharePoint Online, ale w scenariuszu lokalnym różnice nie będą tak łatwo widoczne, jak w SharePoint Online.
  
Aby poprawnie ocenić sposób działania strony dla użytkowników, należy użyć standardowego konta użytkownika, aby uniknąć ładowania kontrolek tworzenia i dodatkowego ruchu związanego z grupami zabezpieczeń.
  
## <a name="connection-categories-for-performance-tuning"></a>Kategorie połączeń na potrzeby dostrajania wydajności

Połączenia między serwerem a użytkownikiem można podzielić na trzy główne składniki. Należy wziąć pod uwagę te kwestie podczas projektowania stron SharePoint Online, aby uzyskać wgląd w czas ładowania.
  
- **Serwera** Serwery hostujące przez firmę Microsoft w centrach danych.
    
- **Sieci** Sieć firmy Microsoft, Internet i sieć lokalna między centrum danych a użytkownikami.
    
- **Przeglądarka** Miejsce załadowania strony.
    
W ramach tych trzech połączeń zwykle istnieje pięć przyczyn, które powodują 95% wolnych stron. Każdy z tych powodów został omówiony w tym artykule:
  
- Problemy z nawigacją
    
- Zestawienie zawartości
    
- Duże pliki
    
- Wiele żądań do serwera
    
- Przetwarzanie składników Web Part
    
### <a name="server-connection"></a>Połączenie z serwerem

Wiele problemów wpływających na wydajność SharePoint lokalnie dotyczy również usługi SharePoint Online.
  
Jak można się spodziewać, masz znacznie większą kontrolę nad tym, jak serwery działają przy użyciu lokalnego SharePoint. W przypadku SharePoint Online sytuacja jest nieco inna. Tym więcej pracy wykonujesz na serwerze, tym dłużej trwa renderowanie strony. W przypadku SharePoint największymi winowajcami w tym zakresie są złożone strony z wieloma składnikami Web Part.
  
lokalny serwer SharePoint
  
![Zrzut ekranu przedstawiający serwer lokalny.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Zrzut ekranu przedstawiający serwer w trybie online.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
W przypadku SharePoint Online niektóre żądania stron mogą w rzeczywistości wywoływać wiele serwerów. Może skończyć się macierz żądań między serwerami dla pojedynczego żądania. Te interakcje są kosztowne z perspektywy ładowania strony i spowalniają działanie.
  
Przykłady tych interakcji między serwerami to:
  
- Serwery z sieci Web do SQL
    
- Serwery sieci Web do aplikacji
    
Inną rzeczą, która może spowolnić interakcje z serwerem, są chybienia pamięci podręcznej. W przeciwieństwie do lokalnego SharePoint istnieje niewielkie prawdopodobieństwo, że trafisz na ten sam serwer dla strony, która była wcześniej odwiedzana. Dzięki temu buforowanie obiektów staje się przestarzałe.
  
### <a name="network-connection"></a>Połączenie sieciowe

W przypadku lokalnego SharePoint, który nie korzysta z sieci WAN, możesz użyć szybkiego połączenia między centrum danych a użytkownikami końcowymi. Ogólnie rzecz biorąc, rzeczy są łatwe do zarządzania z perspektywy sieci.
  
W przypadku usługi SharePoint Online należy wziąć pod uwagę jeszcze kilka czynników, na przykład:
  
- Sieć firmy Microsoft
    
- The Internet
    
- Usługodawca sieciowy
    
Niezależnie od używanej wersji SharePoint (i używanej sieci) są to następujące elementy, które zazwyczaj spowodują zajętość sieci:
  
- Duży ładunek
    
- Wiele plików
    
- Duża fizyczna odległość do serwera
    
Jedną z funkcji, której można użyć w usłudze SharePoint Online, jest microsoft CDN (Content Delivery Network). CDN jest zasadniczo rozproszoną kolekcją serwerów wdrożonych w wielu centrach danych. Za pomocą CDN zawartość na stronach może być hostowana na serwerze znajdującym się blisko klienta, nawet jeśli klient znajduje się daleko od źródłowego serwera SharePoint Server. Firma Microsoft będzie używać tego więcej w przyszłości do przechowywania lokalnych wystąpień stron, których nie można dostosować, na przykład strony głównej administratora usługi SharePoint Online. Aby uzyskać więcej informacji na temat sieci CDN, zobacz [Sieci dostarczania zawartości](content-delivery-networks.md).
  
Coś, o czym musisz wiedzieć, ale może nie być w stanie zrobić wiele, to szybkość połączenia usługodawcy sieciowego. Proste narzędzie do testowania prędkości informuje o szybkości połączenia.
  
### <a name="browser-connection"></a>Połączenie przeglądarki

Istnieje kilka czynników, które należy wziąć pod uwagę w przypadku przeglądarek internetowych z perspektywy wydajności.
  
Odwiedzanie złożonych stron wpłynie na wydajność. Większość przeglądarek ma tylko niewielką pamięć podręczną (około 90 MB), podczas gdy średnia strona internetowa zwykle wynosi około 1,6 MB. To nie trwa długo, aby się przyzwyczaić.
  
Problemem może być również przepustowość. Jeśli na przykład użytkownik ogląda filmy wideo w innej sesji, wpłynie to na wydajność strony SharePoint. Chociaż nie możesz uniemożliwić użytkownikom przesyłania strumieniowego multimediów, możesz kontrolować sposób ładowania strony dla użytkowników.
  
Zapoznaj się z następującymi artykułami dotyczącymi różnych technik dostosowywania stron SharePoint Online i innych najlepszych rozwiązań, które pomogą Ci osiągnąć optymalną wydajność.
  
- [Opcje nawigacji dla SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Korzystanie z narzędzia diagnostyki strony dla usługi SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optymalizacja obrazów dla usługi SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Opóźnienie ładowania obrazów i języka JavaScript w usłudze SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minification and bundling in SharePoint Online (Minification and bundling in SharePoint Online )Minification and bundling in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Używanie składnika Web Part wyszukiwania zawartości zamiast składnika Web Part zapytania o zawartość w celu zwiększenia wydajności w SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Planowanie wydajności i testowanie obciążenia usługi SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnozowanie problemów z wydajnością w usłudze SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Korzystanie z pamięci podręcznej obiektów z usługą SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Instrukcje: unikanie ograniczania lub blokowania w SharePoint Online](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
