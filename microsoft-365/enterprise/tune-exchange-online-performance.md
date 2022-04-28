---
title: Dostosowywanie wydajności usługi Exchange Online
ms.author: krowley
author: tracyp
manager: scotv
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Ten artykuł zawiera ogólne porady i linki do innych zasobów, które informują o tym, jak zwiększyć wydajność Exchange Online.
ms.openlocfilehash: 3b048db5e3ea5090ce5ed2391269f8167c459538
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092034"
---
# <a name="tune-exchange-online-performance"></a>Dostosowywanie wydajności usługi Exchange Online

Ten artykuł zawiera ogólne porady i linki do innych zasobów, które informują o tym, jak zwiększyć wydajność Exchange Online, szczególnie przed migracją. Ten artykuł jest częścią [planowania sieci i dostrajania wydajności dla projektu Office 365](./network-planning-and-performance.md).
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Kwestie, które należy wziąć pod uwagę w celu poprawy wydajności Exchange Online

Aby zwiększyć szybkość migracji i zmniejszyć ograniczenia przepustowości organizacji dla Exchange Online, należy wziąć pod uwagę następujące kwestie:
  
- **Zmniejsz rozmiary skrzynek pocztowych.** Mniejszy rozmiar skrzynki pocztowej zwiększa szybkość migracji. 
    
- **Użyj możliwości przenoszenia skrzynki pocztowej z wdrożeniem hybrydowym Exchange.** W przypadku wdrożenia hybrydowego Exchange poczta offline (w postaci . Pliki OST) nie wymagają ponownego pobrania podczas migracji do Exchange Online. Znacznie zmniejsza to wymagania dotyczące przepustowości pobierania. 
    
- **Planowanie przenoszenia skrzynki pocztowej w okresach niskiego ruchu internetowego i niskiego użycia lokalnego Exchange.** W przypadku przenoszenia harmonogramu żądania migracji są przesyłane do serwera proxy replikacji skrzynki pocztowej i mogą nie być wykonywane natychmiast. 
    
- **Użyj wyskakujące okienka lean dla Outlook w sieci Web.** Wyskakujące okienka lean zapewniają mniejsze, mniej intensywnie korzystające z pamięci wersje niektórych wiadomości e-mail w programie Microsoft Edge lub Internet Explorer przez renderowanie niektórych składników na serwerze. Aby uzyskać więcej informacji, zobacz [Use lean popouts to reduce memory used when reading mail messages (Używanie wyskakujące okienka lean w celu zmniejszenia ilości pamięci używanej podczas odczytywania wiadomości e-mail](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)).


## <a name="general-advice"></a>Porady ogólne

- Upewnij się, że wyszukiwanie dns dla outlook.office.com wprowadza centrum danych MS w lokalizacji wpisu logicznego dla lokalizacji.

- Zbadaj buforowanie skrzynki pocztowej i wybierz odpowiednie opcje (ponownie. okres buforowania, buforowanie udostępnionej skrzynki pocztowej, et cetera).

- Zachowaj Outlook danych przed przekazywaniem połączeń sieci VPN (do centralnego biura), zanim przejdzie przez Internet.

- Upewnij się, że dane skrzynki pocztowej są zgodne z ograniczeniami dotyczącymi ilości folderów i elementów.
    
Aby uzyskać więcej informacji na temat wydajności migracji Exchange, zobacz [Office 365 wydajność migracji i najlepsze rozwiązania](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
