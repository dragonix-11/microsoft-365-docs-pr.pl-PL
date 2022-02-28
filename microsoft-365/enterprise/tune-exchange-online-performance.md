---
title: Dostosowywanie Exchange Online wydajności
ms.author: krowley
author: tracyp
manager: laurawi
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
ms.openlocfilehash: 5feb704a1da83ef93ebc3bbe72fb12c7f0c54574
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987798"
---
# <a name="tune-exchange-online-performance"></a>Dostosowywanie Exchange Online wydajności

Ten artykuł zawiera ogólne porady i linki do innych zasobów, które informują o tym, jak zwiększyć wydajność Exchange Online, szczególnie przed migracją. Ten artykuł jest częścią planowania [sieci i dostosowywania wydajności dla Office 365](./network-planning-and-performance.md) projektu.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Co należy wziąć pod uwagę w celu zwiększenia Exchange Online danych

Aby zwiększyć szybkość migracji i zmniejszyć ograniczenia przepustowości Twojej organizacji na Exchange Online, rozważ następujące kwestie:
  
- **Zmniejszanie rozmiarów skrzynek pocztowych.** Mniejszy rozmiar skrzynki pocztowej zwiększa szybkość migracji. 
    
- **Używanie funkcji przenoszenia skrzynki pocztowej we wdrożeniu Exchange hybrydowym.** W przypadku Exchange hybrydowego poczta w trybie offline (w postaci . Pliki OST) nie wymagają ponownego pobrania podczas migracji do programu Exchange Online. Znacznie zmniejsza to wymagania w zakresie przepustowości pobierania. 
    
- **Zaplanowanie przenoszenia skrzynek pocztowych na okresy niskiego ruchu internetowego i niskiego wykorzystania Exchange lokalnych.** Podczas planowania przesuńeń żądania migracji są przesyłane do serwera proxy replikacji skrzynki pocztowej i mogą nie zostać złożone natychmiast. 
    
- **Korzystanie z wysuwu bez Outlook w sieci Web.** Dzięki renderowaniu niektórych składników na serwerze w programie Microsoft Edge lub Internet Explorer mniejsze i wymaga mniej pamięci wersje niektórych wiadomości e-mail. Aby uzyskać więcej informacji, zobacz Używanie wysuwu niechcących okienek w celu zmniejszenia użycia [pamięci podczas czytania wiadomości e-mail](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Porady ogólne

- Upewnij się, że odnośnik DNS outlook.office.com wprowadza do centrum danych MS w logicznej lokalizacji wpisu dla Twojej lokalizacji.

- Buforowanie skrzynki pocztowej poszukiwania i wybieranie odpowiednich opcji (np. okres buforowania, buforowanie udostępnionej skrzynki pocztowej, et cetera).

- Nie Outlook danych sieciowych przez połączenia VPN (do biura centralnego), zanim trafią przez Internet.

- Upewnij się, że dane skrzynki pocztowej są zgodne z ograniczeniami folderów i elementów oraz kwot.
    
Aby uzyskać więcej informacji na Exchange migracji, zobacz Office 365 [wydajność migracji i najlepsze rozwiązania](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
