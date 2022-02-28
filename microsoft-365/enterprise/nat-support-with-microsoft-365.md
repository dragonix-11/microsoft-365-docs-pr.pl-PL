---
title: Obsługa NAT z Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Ten artykuł zawiera szczegółowe informacje o tym, jak  przybliżeniu liczby klientów, których można używać na jednym adresie IP w organizacji przy użyciu nat.
ms.openlocfilehash: 5335ac87bb579b6cb00e1387da97dd5a1d4f6c7f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984380"
---
# <a name="nat-support-with-office-365"></a>Obsługa NAT z Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Wcześniej wskazówki sugerowały, że maksymalna liczba klientów usługi Exchange, których należy używać na jednym adresie IP do łączenia się z usługą Office 365, wynosi około 2000 klientów na port sieciowy.
  
## <a name="why-use-nat"></a>Dlaczego warto używać nat?

Korzystając z naT, tysiące osób w sieci firmowej mogą "współużytczać" kilka publicznie routowalnych adresów IP.
  
Większość sieci firmowych korzysta z prywatnej (RFC1918) przestrzeni adresów IP. Prywatna przestrzeń adresów jest przydzielana przez urząd IANA (Internet Assigned Numbers Authority) i przeznaczona wyłącznie dla sieci, które nie mają bezpośredniego połączenia z i do globalnej sieci Internet.
  
Aby zapewnić dostęp do Internetu dla urządzeń w prywatnej przestrzeni adresów IP, organizacje używają technologii bramy, takich jak zapory i serwery proxy, które zapewniają usługi translacji adresów sieciowych (NAT) lub translacji adresów portów (PAT). Te bramy sprawiają, że ruch z urządzeń wewnętrznych do Internetu (w tym Office 365) wydaje się pochodzić z co najmniej jednego publicznie routowalnego adresu IP. Każde połączenie wychodzące z urządzenia wewnętrznego jest tłumaczone na inny port źródłowy TCP w publicznym adresie IP. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Dlaczego potrzebujesz tak wielu połączeń otwartych do Office 365 tym samym czasie?

Outlook otworzyć osiem lub więcej połączeń (w sytuacjach, gdy istnieją dodatki, kalendarze udostępnione, skrzynki pocztowe itp.). Ponieważ na opartym na programie Windows urządzeniu NAT dostępnych jest maksymalnie 64 000 portów, za adresem IP może być maksymalnie 8000 użytkowników, zanim porty zostaną wyczerpane. Należy zauważyć, że jeśli klienci Windows urządzeń opartych na systemie OS dla nat, całkowita liczba dostępnych portów zależy od tego, jakie urządzenie lub oprogramowanie NAT jest używane. W tym scenariuszu maksymalna liczba portów może być mniejsza niż 64 000. Dostępność portów wpływa również na inne czynniki, takie jak ograniczenie liczby Windows do własnego użytku, co pozwala zmniejszyć całkowitą liczbę dostępnych portów do 60 000. Mogą być też inne aplikacje, takie jak program Internet Explorer, które mogą nawiązać połączenie jednocześnie, wymagające dodatkowych portów.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Obliczanie maksymalnej liczby urządzeń obsługiwanych na jednym publicznym adresie IP za pomocą Office 365

Aby określić maksymalną liczbę urządzeń na jednym publicznym adresie IP, należy monitorować ruch sieciowy w celu określenia szczytowego zużycia portów dla każdego klienta. Ponadto do użycia portów powinien być stosowany współczynnik wartości szczytowej (co najmniej 4). 
  
 **Użyj następującej formuły, aby obliczyć liczbę obsługiwanych urządzeń na adres IP:**
  
Maksymalna liczba urządzeń obsługiwanych na jednym publicznym adresie IP = (64 000 — porty ograniczone)/(Szczytowe zużycie portów + współczynnik wartości szczytowej)
  
 **Na przykład:**
  
- **Porty ograniczone:** 4000 dla systemu operacyjnego

- **Szczytowe zużycie portów:** 6 na urządzenie

- **Współczynnik szczytowy:** 4

Następnie maksymalna liczba urządzeń obsługiwanych na jednym publicznym adresie IP = (64 000 - 4000)/(6 + 4) = 6000
  
Wraz z wydaniem pakietu hostingowego pakietu Office 365 dołączonego do aktualizacji z września 2011 r. dla pakietu Microsoft Office Outlook 2007 lub listopada 2011 r. dla systemu Microsoft Outlook 2010 lub nowszej aktualizacji liczba połączeń z programu Outlook (oba te Office Outlook 2007 z dodatkiem Service Pack 2 i Outlook 2010), aby Exchange mieć zaledwie 2. Aby określić minimalną i maksymalną liczbę portów, które sieć będzie wymagana w szczytowym stanie, należy w tym celu wyliczyć różne systemy operacyjne, zachowania użytkowników itp.
  
Jeśli chcesz obsługiwać więcej urządzeń na jednym publicznym adresie IP, wykonaj opisane czynności, aby ocenić maksymalną liczbę urządzeń, które mogą być obsługiwane:
  
Monitoruj ruch sieciowy, aby określić szczytowe zużycie portów na każdego klienta. Należy zebrać te dane:
  
- Z wielu lokalizacji
    
- Z wielu urządzeń
    
- W różnych momentach
    
Za pomocą powyższej formuły można obliczyć maksymalną liczbę użytkowników na każdy adres IP, którzy mogą być obsługiwani w swoim środowisku.
  
Istnieją różne metody dystrybucji obciążenia klientów między dodatkowe publiczne adresy IP. Dostępne strategie zależą od możliwości firmowego rozwiązania bramy. Najprostszym rozwiązaniem jest segmentowanie przestrzeni adresów użytkowników i statyczne "przypisywanie" liczby adresów IP do każdej bramy. Innym rozwiązaniem, które oferuje wiele urządzeń bramy, jest możliwość użycia puli adresów IP. Zaletą puli adresów jest to, że jest ona znacznie bardziej dynamiczna i mniej prawdopodobna w miarę wzrostu liczby użytkowników.
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie Office 365 punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 punkty końcowe — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
