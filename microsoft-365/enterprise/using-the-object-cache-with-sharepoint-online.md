---
title: Korzystanie z pamięci podręcznej obiektów z usługą SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule wyjaśniono różnice między korzystaniem z pamięci podręcznej obiektów w lokalnym SharePoint Server 2013 a w SharePoint Online.
ms.openlocfilehash: c763ebb1603ade7fdc98f7728fb03697c5e7425c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014670"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Korzystanie z pamięci podręcznej obiektów z usługą SharePoint Online

W tym artykule wyjaśniono różnice między korzystaniem z pamięci podręcznej obiektów w lokalnym SharePoint Server 2013 a w SharePoint Online.
  
Poleganie na pamięci podręcznej obiektów w przypadku wdrożenia online ma istotne SharePoint online. Każda zależność od pamięci podręcznej obiektów SharePoint online obniża niezawodność strony. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Jak działa SharePoint online i SharePoint Server 2013

Gdy SharePoint Server 2013 jest hostowany lokalnie, klient ma prywatne serwery frontoronu sieci Web, które hostuje pamięć podręczną obiektów. Oznacza to, że pamięć podręczna jest przeznaczona tylko dla jednego klienta i jest ograniczona tylko ilości dostępnej pamięci przydzielonej do pamięci podręcznej obiektów. Ponieważ w scenariuszu lokalnym jest obsługiwany tylko jeden klient, serwery front-end sieci Web zazwyczaj wymagają od użytkowników, aby wielokrotnie składali żądania do tych samych witryn. Oznacza to, że pamięć podręczna szybko się zapełnia i pozostaje pełna wyników zapytania listy oraz SharePoint obiekty regularnie żądane przez użytkowników.
  
![Pokazuje ruch i obciążenie lokalnych serwerów frontoronu sieci Web.](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
W wyniku tego czas ładowania strony jest zwiększany, gdy użytkownik odwiedza tę stronę po raz drugi. Po co najmniej czterokrotnych ładowaniach tej samej strony będzie ona buforowana na wszystkich frontonych serwerach sieci Web.
  
Z kolei w przypadku usługi SharePoint Online jest wiele innych serwerów, ale również wiele innych witryn. Każdy użytkownik może łączyć się z innym serwerem frontoronu sieci Web, dla których pamięć podręczna nie jest wypełniana. Być może pamięć podręczna jest wypełniana dla serwera, ale kolejny użytkownik tego serwera frontoronu sieci Web żąda strony z innej witryny. Nawet jeśli następny użytkownik zażąda tej samej strony, co podczas poprzedniej wizyty, jest on ładowany do innego serwera frontoronu sieci Web, który nie ma tej strony w pamięci podręcznej. W tym ostatnim przypadku buforowanie nie pomaga użytkownikom.
  
Na poniższej ilustracji każdy punkt oznacza stronę żądaną przez użytkownika i miejsce jej w pamięci podręcznej. Różne kolory reprezentują różnych klientów współużytkują infrastrukturę SaaS.
  
![Wyświetla wyniki buforowania obiektów w u SharePoint Online.](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Jak widać na diagramie, szanse na to, że użytkownik nabiernie się na serwer, który ma kopię strony w pamięci podręcznej, są bardzo wąskie. Ponadto ze względu na dużą przepustowość i współużytkowanie serwerów przez wiele witryn, pamięć podręczna nie trwa długo, ponieważ miejsce dostępne dla pamięci podręcznej jest zbyt duże.
  
Ze wszystkich tych powodów uzyskiwanie przez użytkowników obiektów z pamięci podręcznej nie jest skutecznym sposobem na zapewnienie wysokiej jakości obsługi użytkownika i czasu ładowania stron w u SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Czego używamy, jeśli nie możemy polegać na pamięci podręcznej obiektów w celu zwiększenia wydajności SharePoint online?

Ponieważ nie należy polegać na pamięci podręcznej w u SharePoint Online, należy oceniać alternatywne metody projektowania pod SharePoint dostosowaniami, które korzystają z pamięci podręcznej obiektów. Oznacza to korzystanie z metod związanych z problemami z wydajnością, które nie opierają się na buforowaniu obiektów w celu uzyskania dobrych wyników dla użytkowników. Opisano to w niektórych innych artykułach z tej serii, m.in.:
  
- [Opcje nawigacji dla aplikacji SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minifikacja i tworzenie pakietów w u SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Opóźnienie ładowania obrazów i kodu JavaScript w u SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    