---
title: Obsługa translatora NAT za pomocą usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: Ten artykuł zawiera szczegółowe informacje o tym, jak przybliżyć liczbę klientów, których można użyć na adres IP w organizacji przy użyciu translatora adresów sieciowych.
ms.openlocfilehash: 71c9d54ddf88d9b69c890609fea7ece8cac0de33
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097387"
---
# <a name="nat-support-with-office-365"></a>Obsługa translatora NAT za pomocą usługi Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Wcześniej wskazówki sugerowały, że maksymalna liczba klientów Exchange, których należy użyć na adres IP w celu nawiązania połączenia z Office 365, wynosiła około 2000 klientów na port sieci.
  
## <a name="why-use-nat"></a>Dlaczego warto używać translatora adresów adresowych?

Korzystając z translatora adresów sieciowych, tysiące osób w sieci firmowej może "udostępnić" kilka publicznie routingowych adresów IP.
  
Większość sieci firmowych korzysta z przestrzeni adresów IP prywatnych (RFC1918). Prywatna przestrzeń adresowa jest przydzielana przez urząd IANA (Internet Assigned Numbers Authority) i przeznaczona wyłącznie dla sieci, które nie są kierowane bezpośrednio do i z globalnego Internetu.
  
Aby zapewnić dostęp do Internetu do urządzeń w prywatnej przestrzeni adresów IP, organizacje używają technologii bramy, takich jak zapory i serwery proxy, które zapewniają usługi tłumaczenia adresów sieciowych (NAT) lub translacji adresów portów (PAT). Te bramy sprawiają, że ruch z urządzeń wewnętrznych do Internetu (w tym Office 365) wydaje się pochodzić z co najmniej jednego publicznie routingu adresów IP. Każde połączenie wychodzące z urządzenia wewnętrznego przekłada się na inny źródłowy port TCP na publicznym adresie IP. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Dlaczego musisz mieć tak wiele połączeń otwartych dla Office 365 w tym samym czasie?

Outlook może otworzyć co najmniej osiem połączeń (w sytuacjach, gdy istnieją dodatki, kalendarze udostępnione, skrzynki pocztowe itp.). Ponieważ na urządzeniu NAT opartym na Windows dostępnych jest maksymalnie 64 000 portów, adres IP może być maksymalnie 8000 użytkowników, zanim porty zostaną wyczerpane. Należy pamiętać, że jeśli klienci używają urządzeń opartych na systemie operacyjnym Windows na potrzeby translatora adresów sieciowych, łączna liczba dostępnych portów zależy od używanego urządzenia LUB oprogramowania NAT. W tym scenariuszu maksymalna liczba portów może być mniejsza niż 64 000. Na dostępność portów wpływają również inne czynniki, takie jak Windows ograniczenie 4000 portów do własnego użytku, co zmniejsza całkowitą liczbę dostępnych portów do 60 000. Mogą istnieć inne aplikacje, takie jak Internet Explorer, które mogą łączyć się w tym samym czasie, co wymaga dodatkowych portów.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Obliczanie maksymalnej obsługiwanej ochrony urządzeń za pojedynczym publicznym adresem IP z Office 365

Aby określić maksymalną liczbę urządzeń za jednym publicznym adresem IP, należy monitorować ruch sieciowy w celu określenia szczytowego użycia portów na klienta. Ponadto należy użyć współczynnika szczytowego dla użycia portu (minimum 4). 
  
 **Użyj następującej formuły, aby obliczyć liczbę obsługiwanych urządzeń na adres IP:**
  
Maksymalna liczba obsługiwanych urządzeń za pojedynczym publicznym adresem IP = (64 000 — porty z ograniczeniami)/(Szczytowe użycie portów i współczynnik szczytowy)
  
 **Jeśli na przykład spełniono następujące warunki:**
  
- **Porty z ograniczeniami:** 4000 dla systemu operacyjnego

- **Szczytowe zużycie portów:** 6 na urządzenie

- **Współczynnik szczytu:** 4

Następnie maksymalna liczba obsługiwanych urządzeń za pojedynczym publicznym adresem IP = (64 000 – 4000)/(6 + 4) = 6000
  
Wraz z wydaniem pakietu hostingowego Office 365 dołączonego do aktualizacji z września 2011 r. dla Microsoft Office Outlook 2007 r. lub listopada 2011 r. dla Microsoft Outlook 2010 lub nowszej aktualizacji liczba połączeń z Outlook (oba Office Outlook 2007 z dodatkiem Service Pack 2 i Outlook 2010) do Exchange może wynosić nawet 2. Należy uwzględnić różne systemy operacyjne, zachowania użytkowników itd., aby określić minimalną i maksymalną liczbę portów wymaganych przez sieć w szczytowym momencie.
  
Jeśli chcesz obsługiwać więcej urządzeń za jednym publicznym adresem IP, wykonaj kroki opisane w celu oceny maksymalnej liczby urządzeń, które mogą być obsługiwane:
  
Monitorowanie ruchu sieciowego w celu określenia szczytowego zużycia portów na klienta. Należy zebrać następujące dane:
  
- Z wielu lokalizacji
    
- Z wielu urządzeń
    
- Wielokrotnie
    
Użyj powyższej formuły, aby obliczyć maksymalną liczbę użytkowników na adres IP, który może być obsługiwany w ich środowisku.
  
Istnieją różne metody dystrybucji obciążenia klienta między dodatkowymi publicznymi adresami IP. Dostępne strategie zależą od możliwości rozwiązania bramy firmowej. Najprostszym rozwiązaniem jest segmentowanie przestrzeni adresowej użytkownika i statyczne "przypisanie" wielu adresów IP do każdej bramy. Inną alternatywą oferowaną przez wiele urządzeń bramy jest możliwość korzystania z puli adresów IP. Zaletą puli adresów jest to, że jest ona znacznie bardziej dynamiczna i rzadziej wymaga korekty w miarę wzrostu bazy użytkowników.
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie punktami końcowymi usługi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 punktów końcowych — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
