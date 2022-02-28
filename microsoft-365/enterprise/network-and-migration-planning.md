---
title: Planowanie sieci i migracji dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Ten artykuł zawiera linki do informacji na temat planowania, testowania i migracji sieci do Office 365.
ms.openlocfilehash: 21bd36395f6ceb6a13b3180a26f8dbf7f197f134
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984378"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planowanie sieci i migracji dla Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Ten artykuł zawiera linki do informacji na temat planowania i testowania sieci oraz migracji do Office 365.
  
Przed wdrożeniem usługi Office 365 po raz pierwszy lub migracją do usługi Office 365 możesz użyć informacji owanych w tych tematach, aby oszacować potrzebną przepustowość, a następnie przetestować i sprawdzić, czy masz wystarczającą przepustowość do wdrożenia lub migracji do usługi Office 365.

Ten artykuł jest częścią [artykułu Planowanie sieci i dostosowywanie wydajności pod Office 365](./network-planning-and-performance.md).

Aby uzyskać instrukcje dotyczące optymalizowania sieci pod kątem usług Microsoft 365 oraz innych platform i usług w chmurze firmy Microsoft, zobacz plakat Sieci oparte na chmurze firmy Microsoft dla Enterprise [architektów architektury](../solutions/cloud-architecture-models.md).
   
## <a name="estimate-network-bandwidth-requirements"></a>Szacowanie wymagań w zakresie przepustowości sieci
<a name="EstimateBandwidthRequirements"> </a>

Używanie Office 365 może spowodować wzrost użycia obwodu internetowego w organizacji. Należy określić, czy aktualnie dostępna przepustowość wystarczy do obsługi szacowanego wzrostu przepustowości po pełnym wdrożeniu usługi Office 365 przy pozostawienia co najmniej 20% przepustowości w przypadku obsługi wiaszych dni w autobusie.
  
Aby oszacować przepustowość, należy wykonać następujące czynności:
  
1. Oceń liczbę klientów, którzy będą korzystać z każdego internetowego numeru wychodzącego. Pozwól, aby nasza wieloterabitowa sieć obsługiła możliwie najwięcej połączeń. 
    
2. Określ, Office 365 usługi i funkcje będą dostępne dla klientów. Prawdopodobnie będą to grupy osób z różnymi usługami lub profilami użycia.
    
3. Zmierz użycie sieci w pilotażowej grupie klientów. Upewnij się, że klienci pilotażowi są reprezentatywni dla różnych profilów osób w organizacji, a także różnych lokalizacji geograficznych. Możesz krzyżowo sprawdzić wyniki w starych kalkulatorach Exchange i [Microsoft Teams](/microsoftteams/prepare-network) lub [](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) na analizie przypadku wykonanej w naszej sieci.[](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) 
    
4. Użyj pomiarów z grupy pilotażowej, aby oszacować potrzeby całej organizacji, i przetestuj je ponownie, aby zweryfikować szacunki przed wprowadzeniem jakichkolwiek zmian w sieci.
    
## <a name="test-your-existing-network"></a>Testowanie istniejącej sieci
<a name="calculators"> </a>

 **Narzędzia sieciowe.** Przetestuj i zweryfikuj przepustowość swojego połączenia internetowego, aby określić ograniczenia pobierania, przekazywania i opóźnień. Te narzędzia pomogą w określeniu możliwości sieci na temat migracji oraz działania po pełnym wdrożeniu. 
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Sprawdza łączność w twoim Exchange Online sieciowym.
    
- Rozwiązywanie [problemów z Asystent odzyskiwania i pomocy technicznej Outlook i Office 365](https://diagnostics.office.com/#/Download?env=SOC) za pomocą Office 365 Microsoft Office 365 Microsoft. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Najlepsze rozwiązania dotyczące planowania sieci i poprawy wydajności migracji w przypadku Office 365
<a name="BestPractices"> </a>

Aby uzyskać więcej informacji na temat ulepszania obsługi klienta, bardziej szczegółowe informacje na temat Office 365 klientów.
  
1. Chcesz od razu rozpocząć pomaganie użytkownikom? Zobacz Najlepsze rozwiązania dotyczące korzystania z usługi [Office 365](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) w wolno współpracującej sieci, aby uzyskać porady dotyczące korzystania z usługi Office 365, w tym usług SharePoint Online, Exchange Online i Lync Online, gdy Twoja sieć po prostu nie chce współpracować. Ten artykuł zawiera linki do wielu materiałów w witrynie TechNet i programie Support.office.com w celu optymalizacji obsługi programu Office 365 i zawiera informacje o łatwych sposobach dostosowywania stron sieci Web oraz o tym, jak skonfigurować ustawienia programu Internet Explorer w celu Office 365 strony. 
    
2. Przeczytaj [Office 365 zasady łączności sieciowej](./microsoft-365-network-connectivity-principles.md), aby zrozumieć zasady łączności w celu bezpiecznego zarządzania Office 365 ruchu i uzyskiwania najlepszej możliwej wydajności. Ten artykuł pomoże Ci zrozumieć najnowsze wskazówki dotyczące bezpiecznego optymalizowania Office 365 sieci. 
    
3. Wydajność migracji poczty można zwiększyć, starannie zarządzając harmonogramem aktualizacji Windows poczty. Możesz zaktualizować komputery klienckie partiami i upewnić się, że wszystkie komputery klienckie zostały zaktualizowane przed Office 365, aby regulować wykorzystanie przepustowości sieci. Aby uzyskać więcej informacji, [zobacz Ręczne aktualizowanie i konfigurowanie komputerów pod Office 365 najnowszych aktualizacji](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 sieci działa najlepiej, gdy jest traktowany jako zaufana usługa internetowa, i może pominąć większość tradycyjnego filtrowania i skanowania, które niektóre organizacje umieszczają w ruchu sieciowym do niezaufanych usług internetowych. Obejmuje to zwykle usunięcie przetwarzania ruchu wychodzącego, takiego jak uwierzytelnianie użytkowników serwera proxy i inspekcja pakietów, a także zapewnienie lokalnego ruchu wychodzącego do Internetu za pomocą odpowiedniego translacji adresów sieciowych (NAT, Network Address Translation) i odpowiedniej przepustowości do obsługi zwiększonych żądań sieciowych. Zobacz Zarządzanie [punktami Office 365,](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) aby uzyskać dodatkowe wskazówki dotyczące konfigurowania sieci w celu obsługi Office 365 jako zaufanej usługi internetowej w Twojej sieci.
    
1. [Zapewnij zarządzanie Office 365 punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Dodatkowy ruch przychodzący do Office 365 połączeń wychodzących serwera proxy oraz wzrost bezpiecznego ruchu za pośrednictwem protokołu TLS/SSL.
    
2. Jeśli twoje proxy połączeń wychodzących wymagają uwierzytelniania użytkowników, może na przykład wystąpić spowolnienie łączności lub utrata funkcjonalności. Pominięcie wymagania uwierzytelniania dla domen Office 365 może zmniejszyć to obciążenie.
    
3. Jeśli masz dużą liczbę udostępnionych kalendarzy i skrzynek pocztowych, możesz zobaczyć wzrost liczby połączeń z Outlook do Exchange. Na przykład klient Outlook może otworzyć do dwóch dodatkowych połączeń dla każdego kalendarza udostępnionego w użyciu. W takiej sytuacji upewnij się, że serwer proxy połączeń wychodzących może obsługiwać połączenia, lub pomiń serwer proxy w przypadku połączeń z Office 365 dla Outlook.
    
4. Określ maksymalną liczbę obsługiwanych urządzeń dla publicznego adresu IP oraz sposób równoważenia obciążenia między wieloma adresami IP. Aby uzyskać więcej informacji, zobacz [Obsługa NAT z Office 365](nat-support-with-microsoft-365.md).
    
5. Jeśli przeprowadzasz inspekcję połączeń wychodzących z komputerów w sieci, pominięcie filtrowania do domen sieci Office 365 poprawi łączność i wydajność. Ponadto pominięcie inspekcji ruchu wychodzącego często usuwa konieczność jednego internetowego ruchu wychodzącego i umożliwia lokalny internetowy ruch wychodzący dla żądań sieciowych przeznaczonych Office 365.
    
6. Niektórzy klienci mogą mieć wpływ na wydajność wewnętrznych ustawień sieci. Ustawienia, takie jak maksymalny rozmiar jednostki transmisji (MTU), automatyczne wykrywanie lub negocjowanie sieci oraz nieostrostrogowe trasy transmisji do Internetu to typowe miejsca do rozglądu.
    
## <a name="network-planning-reference-for-office-365"></a>Informacje o planowaniu sieci dla Office 365
<a name="NetReference"> </a>

Te tematy zawierają szczegółowe Office 365 informacji o sieci.
  
- [Zarządzanie Office 365 punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Sieci dostarczania zawartości](content-delivery-networks.md)
    
- [Zewnętrzne rekordy systemu nazw domen dla Office 365](external-domain-name-system-records.md)
    
- [Obsługa protokołu IPv6 w Office 365 usługach internetowych](ipv6-support.md)
    
- [Office 365 zasad łączności sieciowej](./microsoft-365-network-connectivity-principles.md)
    
- [Planowanie urządzeń sieciowych, które łączą się z Office 365 sieci](plan-for-network-devices.md)
    
- [Przewodniki konfiguracji dla usług Office 365 internetowych](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Zobacz też

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)