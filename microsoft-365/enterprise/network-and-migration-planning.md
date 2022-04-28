---
title: Planowanie sieci i migracji dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Ten artykuł zawiera linki do informacji o planowaniu sieci, testowaniu i migracji do Office 365.
ms.openlocfilehash: 6288c9afae66206b7284f751f8a63381ab8451e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077461"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planowanie sieci i migracji dla Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Ten artykuł zawiera linki do informacji o planowaniu i testowaniu sieci oraz migracji do Office 365.
  
Przed pierwszym wdrożeniem lub migracją do Office 365 można użyć informacji w tych tematach, aby oszacować potrzebną przepustowość, a następnie przetestować i sprawdzić, czy masz wystarczającą przepustowość do wdrożenia lub migracji do Office 365.

Ten artykuł jest częścią [planowania sieci i dostrajania wydajności dla Office 365](./network-planning-and-performance.md).

Aby zapoznać się z krokami optymalizacji sieci pod kątem Microsoft 365 i innych platform i usług firmy Microsoft w chmurze, zobacz plakat [Microsoft Cloud Networking for Enterprise Architects (Sieć w chmurze firmy Microsoft dla architektów Enterprise](../solutions/cloud-architecture-models.md)).
   
## <a name="estimate-network-bandwidth-requirements"></a>Szacowanie wymagań dotyczących przepustowości sieci
<a name="EstimateBandwidthRequirements"> </a>

Użycie Office 365 może zwiększyć wykorzystanie obwodu internetowego organizacji. Ważne jest, aby określić, czy obecnie dostępna przepustowość jest wystarczająca do obsługi szacowanego wzrostu po pełnym wdrożeniu Office 365, pozostawiając co najmniej 20% pojemności, aby obsłużyć najbardziej ruchliwe dni.
  
Aby oszacować przepustowość, wykonaj następujące kroki:
  
1. Oceń liczbę klientów, którzy będą używać każdego ruchu wychodzącego z Internetu. Pozwól naszej sieci z wieloma terabitami obsłużyć jak największą część połączenia. 
    
2. Określ, które usługi i funkcje Office 365 będą dostępne dla klientów. Prawdopodobnie będziesz mieć grupy osób z różnymi usługami lub profilami użycia.
    
3. Zmierz użycie sieci dla pilotażowej grupy klientów. Upewnij się, że klienci pilotażowi są reprezentatywni dla różnych profilów osób w organizacji, a także różnych lokalizacji geograficznych. Możesz krzyżowo sprawdzić wyniki względem naszych starych kalkulatorów [dla Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) i [Microsoft Teams](/microsoftteams/prepare-network) lub [analizy przypadku](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365), którą przeprowadziliśmy we własnej sieci. 
    
4. Użyj pomiarów z grupy pilotażowej, aby ekstrapolować potrzeby całej organizacji i ponownie przetestować w celu zweryfikowania oszacowań przed wprowadzeniem jakichkolwiek zmian w sieci.
    
## <a name="test-your-existing-network"></a>Testowanie istniejącej sieci
<a name="calculators"> </a>

 **Narzędzia sieciowe.** Przetestuj i zweryfikuj przepustowość Internetu, aby określić ograniczenia pobierania, przekazywania i opóźnienia. Te narzędzia pomogą Ci określić możliwości sieci na potrzeby migracji, a także po pełnym wdrożeniu. 
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): testuje łączność w środowisku Exchange Online.
    
- Użyj [pomoc techniczna firmy Microsoft i asystenta odzyskiwania dla Office 365](https://diagnostics.office.com/#/Download?env=SOC), aby rozwiązać problemy z Outlook i Office 365. 

- [narzędzie do testowania łączności sieciowej Microsoft 365](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool): testy Microsoft 365 łączności sieciowej.
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Najlepsze rozwiązania dotyczące planowania sieci i zwiększania wydajności migracji dla Office 365
<a name="BestPractices"> </a>

Zapoznaj się z tymi najlepszymi rozwiązaniami, aby uzyskać więcej informacji na temat ulepszania środowiska Office 365.
  
1. Chcesz od razu zacząć pomagać użytkownikom? Zobacz [Najlepsze rozwiązania dotyczące używania Office 365 w powolnej sieci](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166), aby uzyskać wskazówki dotyczące korzystania z Office 365, w tym SharePoint Online, Exchange Online i Lync Online, gdy sieć po prostu nie współpracuje. Ten artykuł zawiera linki do mnóstwa zawartości w witrynie TechNet i Support.office.com w celu optymalizacji środowiska Office 365 oraz zawiera informacje na temat prostych sposobów dostosowywania stron internetowych oraz sposobu ustawiania ustawień programu Internet Explorer dla najlepszego środowiska Office 365. 
    
2. Przeczytaj [Office 365 zasady łączności sieciowej](./microsoft-365-network-connectivity-principles.md), aby zrozumieć zasady łączności dotyczące bezpiecznego zarządzania ruchem Office 365 i uzyskiwania najlepszej możliwej wydajności. Ten artykuł pomoże Ci zrozumieć najnowsze wskazówki dotyczące bezpiecznej optymalizacji Office 365 łączności sieciowej. 
    
3. Zwiększ wydajność migracji poczty, starannie zarządzając harmonogramem aktualizacji Windows. Komputery klienckie można aktualizować w partiach i upewnić się, że wszystkie komputery klienckie są aktualizowane przed migracją do Office 365 w celu regulowania użycia przepustowości sieci. Aby uzyskać więcej informacji, zobacz [Ręczne aktualizowanie i konfigurowanie pulpitów dla Office 365 dla najnowszych aktualizacji](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 ruch sieciowy działa najlepiej, gdy jest traktowany jako zaufana usługa internetowa i może pominąć większość tradycyjnego filtrowania i skanowania, które niektóre organizacje umieszczają w ruchu sieciowym do niezaufanych usług internetowych. Zwykle obejmuje to usuwanie przetwarzania wychodzącego, takiego jak uwierzytelnianie użytkownika serwera proxy i inspekcja pakietów, a także zapewnienie lokalnego ruchu wychodzącego do Internetu z odpowiednim tłumaczeniem adresów sieciowych (NAT) i wystarczającą pojemnością przepustowości do obsługi zwiększonych żądań sieciowych. Zapoznaj się [z tematem Zarządzanie punktami końcowymi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), aby uzyskać dodatkowe wskazówki dotyczące konfigurowania sieci do obsługi Office 365 jako zaufanej usługi internetowej w sieci.
    
1. Upewnij się[, że zarządzasz punktami końcowymi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Dodatkowy ruch przechodzący do Office 365 powoduje wzrost liczby wychodzących połączeń serwera proxy, a także wzrost bezpiecznego ruchu za pośrednictwem protokołu TLS/SSL.
    
2. Jeśli serwery proxy ruchu wychodzącego wymagają uwierzytelniania użytkownika, może wystąpić niska łączność lub utrata funkcjonalności. Pomijanie wymagań dotyczących uwierzytelniania dla domen Office 365 może zmniejszyć to obciążenie.
    
3. Jeśli masz dużą liczbę kalendarzy udostępnionych i skrzynek pocztowych, może wystąpić wzrost liczby połączeń z Outlook do Exchange. Na przykład klient Outlook może otworzyć do dwóch dodatkowych połączeń dla każdego używanego kalendarza udostępnionego. W takiej sytuacji upewnij się, że serwer proxy ruchu wychodzącego może obsługiwać połączenia lub pominąć serwer proxy dla połączeń z Office 365 dla Outlook.
    
4. Określ maksymalną liczbę obsługiwanych urządzeń dla publicznego adresu IP i sposób równoważenia obciążenia wielu adresów IP. Aby uzyskać więcej informacji, zobacz [Obsługa translatora adresów internetowych w Office 365](nat-support-with-microsoft-365.md).
    
5. Jeśli przeprowadzasz inspekcję połączeń wychodzących z komputerów w sieci, pominięcie tego filtrowania do Office 365 domen poprawi łączność i wydajność. Ponadto pomijanie inspekcji ruchu wychodzącego często eliminuje potrzebę pojedynczego ruchu wychodzącego z Internetu i umożliwia lokalne wyjście internetowe dla Office 365 kierowanych żądań sieciowych.
    
6. Niektórzy klienci uważają, że ustawienia sieci wewnętrznej mogą mieć wpływ na wydajność. Ustawienia takie jak maksymalny rozmiar jednostki transmisji (MTU), automatyczne negocjowanie sieci lub wykrywanie automatyczne oraz nieoptymalne trasy do Internetu są typowymi miejscami do wyszukania.
    
## <a name="network-planning-reference-for-office-365"></a>Dokumentacja planowania sieci dla Office 365
<a name="NetReference"> </a>

Te tematy zawierają szczegółowe informacje Office 365 dokumentacji sieci.
  
- [Zarządzanie punktami końcowymi usługi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Sieci dostarczania zawartości](content-delivery-networks.md)
    
- [Rekordy systemu nazw domen zewnętrznych dla Office 365](external-domain-name-system-records.md)
    
- [Obsługa protokołu IPv6 w usługach Office 365](ipv6-support.md)
    
- [zasady łączności sieciowej Office 365](./microsoft-365-network-connectivity-principles.md)
    
- [Planowanie urządzeń sieciowych łączących się z usługami Office 365](plan-for-network-devices.md)
    
- [Przewodniki konfiguracji dla usług Office 365](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Zobacz też

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)
