---
title: Używanie składników Web Part przeszukiwania zawartości zamiast składników Web Part zapytania zawartości w celu zwiększenia wydajności w SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak zwiększyć wydajność, zastępując część Web Part zapytania dotyczącej zawartości składników Web Part przeszukiwania zawartości w programie SharePoint Server 2013 i w SharePoint Online.
ms.openlocfilehash: d41983a5771e42d357ae4d2adb5864e2a74fdd57
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988410"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Używanie składników Web Part przeszukiwania zawartości zamiast składników Web Part zapytania zawartości w celu zwiększenia wydajności w SharePoint Online

W tym artykule opisano sposób zwiększania wydajności przez zastąpienie składników Web Part zapytania zawartości składników Web Part przeszukiwania zawartości w programach SharePoint Server 2013 i SharePoint Online.
  
Jedną z najbardziej zaawansowanych nowych funkcji programu SharePoint Server 2013 i usługi SharePoint Online jest składników Web Part przeszukiwania zawartości. Ten składników Web Part używa indeksu wyszukiwania do szybkiego pobierania wyników wyświetlanych użytkownikowi. Użycie na stronach składników Web Part przeszukiwania zawartości zamiast składników Web Part zapytania zawartości (CQWP) zwiększa wydajność użytkowników.
  
Użycie składników Web Part przeszukiwania zawartości w witrynie Web Part zapytania o zawartość niemal zawsze spowoduje znacznie lepszą wydajność ładowania stron w SharePoint Online. Wykonanie odpowiedniego zapytania wymaga nieco dodatkowych konfiguracji, ale korzyścią jest większa wydajność i większe zadowolenie użytkowników.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Porównanie wydajności używania składników Web Part przeszukiwania zawartości zamiast składników Web Part kwerendy zawartości

Poniższe przykłady pokazują względny wzrost wydajności, który można uzyskać dzięki użyciu składników Web Part przeszukiwania zawartości zamiast składników Web Part zapytania zawartości. Efekty są tym bardziej oczywiste, im bardziej złożona jest struktura witryny i im szersze zapytania dotyczące zawartości są dostępne, tym lepiej.
  
Ta przykładowa witryna ma następujące cechy:
  
- 8 poziomów podwitryn.
    
- Listy z niestandardowym typem zawartości "owoc".
    
- W tym składników Web Part zapytanie dotyczące zawartości jest szerokie i zwraca wszystkie elementy z typem zawartości "owoc".
    
- W tym przykładzie użyto tylko 50 elementów we wszystkich 8 witrynach. Efekty będą jeszcze bardziej widoczne w przypadku witryn z większą zawartością.
    
Poniżej znajduje się zrzut ekranu z wynikami składników Web Part zapytania zawartości.
  
![Grafika przedstawiająca zapytanie dotyczące zawartości dla składników Web Part.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
W programie Internet **Explorer użyj karty** Sieć w narzędziach deweloperskiej (F12), aby sprawdzić szczegóły nagłówka odpowiedzi. Na poniższym zarchiwizacji wartość ustawienia **SPRequestDuration** dla tego ładowania strony wynosi 924 milisekundy. 
  
![Zrzut ekranu przedstawiający czas trwania żądania: 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **Wartość SPRequestDuration** wskazuje ilość pracy wykonanej na serwerze w celu przygotowania strony. Zamiana zawartości przez zapytanie składniki Web Part na zawartość przez wyszukiwanie składniki Web Part znacznie skraca czas renderowania strony. Natomiast strona z równoważnym składnikówem Web Part przeszukiwania zawartości, zwracający tę samą liczbę wyników, ma wartość **SPRequestDuration** równą 106 milisekundom, jak pokazano na tym zarchiwizacji: 
  
![Zrzut ekranu przedstawiający czas trwania żądania: 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Dodawanie składników Web Part przeszukiwania zawartości w aplikacji SharePoint Online

Dodawanie składników Web Part przeszukiwania zawartości jest bardzo podobne do dodawania zwykłego składników Web Part zapytania o zawartość. Zobacz sekcję *"Dodawanie składników Web Part przeszukiwania zawartości"* w tece Konfigurowanie składników [Web Part przeszukiwania zawartości w programie SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Tworzenie właściwego zapytania wyszukiwania dla składników Web Part przeszukiwania zawartości

Po dodaniu składników Web Part przeszukiwania zawartości możesz uściślić wyszukiwanie i zwrócić szukane elementy. Aby uzyskać szczegółowe instrukcje, zobacz sekcję "Wyświetlanie zawartości przez skonfigurowanie zaawansowanego zapytania w składników Web Part przeszukiwania zawartości" w tece Konfigurowanie składników *Web Part* przeszukiwania zawartości w [programie SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Narzędzie do tworzenia i testowania zapytań

Aby uzyskać narzędzie do tworzenia i testowania złożonych zapytań, zobacz [narzędzie Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex. 
  

