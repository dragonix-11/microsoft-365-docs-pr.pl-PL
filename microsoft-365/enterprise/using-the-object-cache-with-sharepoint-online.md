---
title: Korzystanie z pamięci podręcznej obiektów z usługą SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: W tym artykule wyjaśniono różnicę między używaniem pamięci podręcznej obiektów w lokalnej SharePoint Server 2013 a SharePoint Online.
ms.openlocfilehash: db0a150927bc3a2078d4dc0ca7491471b7973f2d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077787"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Korzystanie z pamięci podręcznej obiektów z usługą SharePoint Online

W tym artykule wyjaśniono różnicę między używaniem pamięci podręcznej obiektów w lokalnej SharePoint Server 2013 a SharePoint Online.
  
Istnieje znaczący negatywny wpływ polegania na pamięci podręcznej obiektów we wdrożeniu usługi SharePoint Online. Każda zależność od pamięci podręcznej obiektów w usłudze SharePoint Online zmniejszy niezawodność strony. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Jak działa pamięć podręczna obiektów SharePoint Online i SharePoint Server 2013

Gdy serwer SharePoint Server 2013 jest hostowany lokalnie, klient ma prywatne serwery internetowe frontonu hostujące pamięć podręczną obiektów. Oznacza to, że pamięć podręczna jest przeznaczona dla jednego klienta i jest ograniczona tylko tym, ile pamięci jest dostępne i przydzielone do pamięci podręcznej obiektów. Ponieważ w scenariuszu lokalnym jest obsługiwany tylko jeden klient, serwery internetowe frontonu zwykle mają użytkowników wysyłających żądania do tych samych witryn w kółko. Oznacza to, że pamięć podręczna szybko się zapełnia i pozostaje pełna wyników zapytania listy i SharePoint obiektów, których użytkownicy regularnie żądają.
  
![Pokazuje ruch i obciążenie lokalnych serwerów sieci Web frontonu.](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
W związku z tym po raz drugi użytkownik odwiedzi stronę, czas ładowania strony się poprawia. Po co najmniej czterech obciążeniach tej samej strony strona jest buforowana na wszystkich serwerach sieci Web frontonu.
  
Natomiast w usłudze SharePoint Online jest o wiele więcej serwerów, ale także wiele innych witryn. Każdy użytkownik może nawiązać połączenie z innym serwerem sieci Web frontonu, który nie ma wypełnionej pamięci podręcznej. Być może pamięć podręczna jest wypełniana dla serwera, ale następny użytkownik tego serwera internetowego frontonu żąda strony z innej witryny. Lub nawet jeśli następny użytkownik zażąda tej samej strony, co podczas poprzedniej wizyty, jest zrównoważony pod względem obciążenia na innym serwerze internetowym frontonu, który nie ma tej strony w pamięci podręcznej. W tym ostatnim przypadku buforowanie w ogóle nie pomaga użytkownikom.
  
Na poniższej ilustracji każda kropka reprezentuje stronę, której żąda użytkownik, oraz miejsce, w którym jest buforowane. Różne kolory reprezentują różnych klientów korzystających z infrastruktury SaaS.
  
![Pokazuje wyniki buforowania obiektów w usłudze SharePoint Online.](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Jak widać na diagramie, prawdopodobieństwo, że dany użytkownik trafi na serwer z buforowaną wersją swojej strony, jest niewielkie. Ponadto ze względu na dużą przepływność i fakt, że serwery są współużytkowane między wieloma lokacjami, pamięć podręczna nie trwa długo, ponieważ dostępna jest tylko tyle miejsca na buforowanie.
  
Z tych wszystkich powodów poleganie na tym, że użytkownicy uzyskują buforowane obiekty, nie jest skutecznym sposobem zapewnienia jakości środowiska użytkownika i czasu ładowania stron w usłudze SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Jeśli nie możemy polegać na pamięci podręcznej obiektów w celu zwiększenia wydajności w usłudze SharePoint Online, czego zamiast tego używamy?

Ponieważ nie należy polegać na buforowaniu w usłudze SharePoint Online, należy ocenić alternatywne metody projektowania dla SharePoint dostosowań korzystających z pamięci podręcznej obiektów. Oznacza to użycie metod w przypadku problemów z wydajnością, które nie polegają na buforowaniu obiektów w celu uzyskania dobrych wyników dla użytkowników. Jest to opisane w niektórych innych artykułach z tej serii i obejmuje:
  
- [Opcje nawigacji dla SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minification and bundling in SharePoint Online (Minification and bundling in SharePoint Online )Minification and bundling in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Opóźnienie ładowania obrazów i języka JavaScript w usłudze SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    