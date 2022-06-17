---
title: Używanie składnika Web Part wyszukiwania zawartości zamiast składnika Web Part zapytania o zawartość w celu zwiększenia wydajności w SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/20/2015
audience: Admin
ms.topic: article
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
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Dowiedz się, jak zwiększyć wydajność, zastępując składnik Web Part kwerendy zawartości składnikiem Web Part wyszukiwania zawartości w SharePoint Server 2013 i SharePoint Online.
ms.openlocfilehash: 4c8a97d24320d5380eccc089737947df9b1a0d0b
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139502"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Używanie składnika Web Part wyszukiwania zawartości zamiast składnika Web Part zapytania o zawartość w celu zwiększenia wydajności w SharePoint Online

W tym artykule opisano sposób zwiększania wydajności przez zastąpienie składnika Web Part kwerendy zawartości składnikiem Web Part wyszukiwania zawartości w SharePoint Server 2013 i SharePoint Online.
  
Jedną z najbardziej zaawansowanych nowych funkcji SharePoint Server 2013 i SharePoint Online jest składnik Web Part wyszukiwania zawartości (CSWP). Ten składnik Web Part używa indeksu wyszukiwania do szybkiego pobierania wyników, które są wyświetlane użytkownikowi. Użyj składnika Web Part wyszukiwania zawartości zamiast składnika Web Part zapytania o zawartość (CQWP) na stronach, aby zwiększyć wydajność użytkowników.
  
Użycie składnika Web Part wyszukiwania zawartości za pośrednictwem składnika Web Part zapytania o zawartość prawie zawsze spowoduje lepszą wydajność ładowania stron w SharePoint Online. Istnieje nieco dodatkowa konfiguracja umożliwiająca uzyskanie odpowiedniego zapytania, ale nagrody to lepsza wydajność i szczęśliwsi użytkownicy.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Porównanie korzyści wydajności uzyskiwanych z używania składnika Web Part wyszukiwania zawartości zamiast składnika Web Part zapytania o zawartość

W poniższych przykładach przedstawiono względny wzrost wydajności, który może zostać wyświetlony podczas korzystania ze składnika Web Part wyszukiwania zawartości zamiast składnika Web Part zapytania o zawartość. Efekty są bardziej oczywiste w przypadku złożonej struktury witryny i zapytań o szeroką zawartość.
  
Ta przykładowa witryna ma następujące cechy:
  
- 8 poziomów podwitryn.
    
- Wyświetla listę przy użyciu niestandardowego typu zawartości "owocowej".
    
- W składniku Web Part zapytanie o zawartość jest szerokie i zwraca wszystkie elementy o typie zawartości "fruit".
    
- W przykładzie użyto tylko 50 elementów w 8 witrynach. Efekty będą jeszcze bardziej widoczne dla witryn z większą ilością zawartości.
    
Oto zrzut ekranu przedstawiający wyniki składnika Web Part zapytania o zawartość.
  
![Grafika przedstawiająca zapytanie o zawartość składnika Web Part.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
W programie Internet Explorer użyj karty **Sieć** narzędzi deweloperskich F12, aby zapoznać się ze szczegółami nagłówka odpowiedzi. Na poniższym zrzucie ekranu wartość **parametru SPRequestDuration** dla tego obciążenia strony wynosi 924 milisekundy. 
  
![Zrzut ekranu przedstawiający czas trwania żądania 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SpRequestDuration** wskazuje ilość pracy wykonanej na serwerze w celu przygotowania strony. Przełączanie zawartości według składników Web Part zapytań z zawartością według składników Web Part wyszukiwania znacznie skraca czas renderowania strony. Natomiast strona z równoważnym składnikiem Web Part wyszukiwania zawartości zwracająca taką samą liczbę wyników ma wartość **SPRequestDuration** wynoszącą 106 milisekund, jak pokazano na tym zrzucie ekranu: 
  
![Zrzut ekranu przedstawiający czas trwania żądania 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Dodawanie składnika Web Part wyszukiwania zawartości w usłudze SharePoint Online

Dodawanie składnika Web Part wyszukiwania zawartości jest podobne do zwykłego składnika Web Part zapytania o zawartość. Zobacz *sekcję "Dodawanie składnika Web Part wyszukiwania zawartości"* w artykule [Konfigurowanie składnika Web Part wyszukiwania zawartości w SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Tworzenie odpowiedniego zapytania wyszukiwania dla składnika Web Part wyszukiwania zawartości

Po dodaniu składnika Web Part wyszukiwania zawartości możesz uściślić wyszukiwanie i zwrócić żądane elementy. Aby uzyskać szczegółowe instrukcje dotyczące tego sposobu, zobacz sekcję *"Wyświetlanie zawartości przez skonfigurowanie zaawansowanego zapytania w składniku Web Part wyszukiwania zawartości"* w [temacie Konfigurowanie składnika Web Part wyszukiwania zawartości w SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Narzędzie do tworzenia i testowania zapytań

Aby uzyskać narzędzie do tworzenia i testowania złożonych zapytań, zobacz [Narzędzie do wyszukiwania zapytań](https://github.com/pnp/PnP-Tools/tree/master/Solutions/SharePoint.Search.QueryTool#download-the-tool).
  

