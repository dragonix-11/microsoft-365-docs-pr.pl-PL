---
title: Wprowadzenie do dostosowywania wydajności dla usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule wyjaśniono, jakie konkretne aspekty należy uwzględnić podczas projektowania stron w celu jak najlepszej wydajności w SharePoint Online.
ms.openlocfilehash: deabb059e2121743b35d5519e4b8684a08dd28b4
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014693"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Wprowadzenie do dostosowywania wydajności dla usługi SharePoint Online

W tym artykule wyjaśniono, jakie konkretne aspekty należy uwzględnić podczas projektowania stron w celu jak najlepszej wydajności w SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>SharePoint metryk online

Następujące ogólne metryki wydajności dla usługi SharePoint Online dostarczają rzeczywistych danych dotyczących wydajności:
  
- Szybkość ładowania stron
    
- Ile odsyłek na stronę jest wymaganych odjęć
    
- Problemy z usługą
    
- Inne rzeczy, które powodują obniżenie wydajności
    
### <a name="conclusions-reached-because-of-the-data"></a>Wnioski z danych

Z danych do nas:
  
- Większość stron w trybie online SharePoint.
    
- Strony, które nie są dostosowane, szybko się ładują.
    
- OneDrive dla Firm, witryny zespołu i strony systemowe, takie _layouts itp., można szybko załadować.
    
- Ładowanie najwolniejszych 1% SharePoint w trybie online trwa ponad 5000 milisekund.
    
Jednym z prostych testów porównawczych, który można stosować, jest mierzenie wydajności przez porównanie czasu ładowania własnego portalu z czasem ładowania strony głównej usługi OneDrive dla Firm, ponieważ korzysta on z kilku dostosowanych funkcji. Często będzie to pierwszy krok, który zostanie przez pomoc techniczną ukończony podczas rozwiązywania problemów z wydajnością sieci.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Używanie standardowego konta użytkownika podczas sprawdzania wydajności

Administrator zbioru witryn, właściciel witryny, redaktor lub współautor należą do innych grup zabezpieczeń, mają więcej uprawnień i dlatego mają dodatkowe elementy SharePoint które można ładować na stronie.
  
Dotyczy to usługi SharePoint i usługi SharePoint Online, ale w scenariuszu lokalnym różnice nie będą tak łatwo zauważyć, jak w SharePoint Online.
  
Aby poprawnie ocenić sposób działania strony dla użytkowników, należy użyć standardowego konta użytkownika w celu uniknięcia ładowania kontrolek tworzenia i dodatkowego ruchu związanego z grupami zabezpieczeń.
  
## <a name="connection-categories-for-performance-tuning"></a>Kategorie połączeń w celu dostosowywania wydajności

Połączenia między serwerem a użytkownikiem można podzielić na trzy główne składniki. Przejmij je podczas projektowania SharePoint w trybie online, aby uzyskać wgląd w czasy ładowania.
  
- **Serwer** Serwery host przez firmę Microsoft w centrach danych.
    
- **Sieć** Sieć firmy Microsoft, Internet i sieć lokalna między centrum danych a użytkownikami.
    
- **Przeglądarka** Miejsce ładowania strony.
    
W tych trzech połączeniach jest zazwyczaj pięć powodów, które powodują 95% wolnych stron. Każda z tych przyczyn jest omówiona w tym artykule:
  
- Problemy z nawigacją
    
- Rzutowania zawartości
    
- Duże pliki
    
- Wiele żądań do serwera
    
- Przetwarzanie składników Web Part
    
### <a name="server-connection"></a>Połączenie z serwerem

Wiele problemów, które wpływają na wydajność SharePoint w środowisku lokalnym, dotyczy również SharePoint online.
  
Zgodnie z oczekiwaniami masz znacznie większą kontrolę nad tym, jak serwery wykonują zadania z lokalnymi SharePoint. W SharePoint online sprawy są nieco inne. Im więcej pracy należy wykonać na serwerze, tym dłużej trwa renderowanie strony. W SharePoint najbardziej mnogiej winy pod tym względem są złożone strony z wieloma składników Web Part.
  
SharePoint serwera lokalnego
  
![Zrzut ekranu przedstawiający serwer w środowisku lokalnym.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Zrzut ekranu przedstawiający serwer w trybie online.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
W SharePoint online niektóre żądania stron mogą w rzeczywistości kończyć się na wywoływaniu wielu serwerów. Może nas na końcu zostać wyedytowana macierz żądań między serwerami dla poszczególnych żądań. Te interakcje są kosztowne z perspektywy ładowania strony i mogą spowolnić proces.
  
Przykładowe interakcje między serwerami to:
  
- Web to SQL Servers
    
- Serwery aplikacji w sieci Web do
    
Inna rzecz, która może spowolnić interakcje na serwerach, to zapisane w pamięci podręcznej błędy. W przeciwieństwie do SharePoint lokalnej istnieje prawdopodobieństwo, że nacisniesz ten sam serwer na stronie, która została odwiedzona wcześniej, co powoduje, że buforowanie obiektów jest przestarzałe.
  
### <a name="network-connection"></a>Połączenie sieciowe

W przypadku SharePoint sieci w sieci WAN, która nie korzysta z sieci WAN, możesz używać szybkiego połączenia między centrum danych i użytkownikami końcowymi. Ogólnie rzecz biorąc, zarządzanie jest łatwe z perspektywy sieci.
  
W SharePoint Online należy wziąć pod uwagę jeszcze kilka czynników, na przykład:
  
- Sieć firmy Microsoft
    
- The Internet
    
- The ISP
    
Niezależnie od używanej SharePoint sieci (i od używanej sieci) zwykle oznacza to, że sieć jest zajęta:
  
- Duży ład
    
- Wiele plików
    
- Duża odległość fizyczna od serwera
    
Jedną z funkcji, z których można korzystać w SharePoint Online, jest aplikacja Microsoft CDN (Content Delivery Network). Centrum CDN w zasadzie jest dystrybuowaną kolekcją serwerów wdrożonych w wielu centrach danych. W CDN zawartość stron może być hostowana na serwerze blisko klienta, nawet jeśli klient znajduje się daleko od pochodzących SharePoint Server. Firma Microsoft będzie używać tego więcej w przyszłości do przechowywania lokalnych wystąpień stron, których nie można dostosować, na przykład na stronie głównej administratora usługi SharePoint Online. Aby uzyskać więcej informacji na temat sieci CDN, zobacz [Sieci dostarczania zawartości](content-delivery-networks.md).
  
Czymś, o czym musisz wiedzieć, ale o których być może nie uda Ci się zrobić zbyt wiele, jest szybkość połączenia Twojego internetowego. Szybkie połączenie można sprawdzić za pomocą prostego narzędzia do testowania szybkości połączenia.
  
### <a name="browser-connection"></a>Połączenie z przeglądarką

Istnieje kilka czynników, które należy uwzględnić w przeglądarkach sieci Web z perspektywy wydajności.
  
Odwiedzanie złożonych stron ma wpływ na wydajność. Większość przeglądarek ma tylko niewielką pamięć podręczną (około 90 MB), a średnia strona sieci Web zazwyczaj wynosi około 1,6 MB. Może to zająć trochę czasu.
  
Być może również występuje problem z przepustowością. Jeśli na przykład użytkownik ogląda klipy wideo w innej sesji, ma to wpływ na wydajność SharePoint strony. Nie można uniemożliwić użytkownikom przesyłania strumieniowego multimediów, ale można kontrolować sposób ładowania strony przez użytkowników.
  
Zapoznaj się z następującymi artykułami, aby uzyskać informacje na temat SharePoint dostosowywania stron w trybie online i innych najlepszych rozwiązań, które pomogą Ci osiągnąć optymalną wydajność.
  
- [Opcje nawigacji dla aplikacji SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Korzystanie z narzędzia Diagnostyka stron dla usługi SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optymalizacja obrazu dla aplikacji SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Opóźnienie ładowania obrazów i kodu JavaScript w u SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minifikacja i tworzenie pakietów w u SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Używanie składników Web Part przeszukiwania zawartości zamiast składników Web Part zapytania zawartości w celu zwiększenia wydajności w SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Planowanie wydajności i testowanie obciążenia usługi SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnozowanie problemów z wydajnością aplikacji SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Korzystanie z pamięci podręcznej obiektów z usługą SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Jak to zrobić: unikanie ograniczania lub blokowania w u SharePoint Online](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
