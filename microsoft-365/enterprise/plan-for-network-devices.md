---
title: Planowanie urządzeń sieciowych łączących się z usługami Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Podsumowanie: Opisuje zagadnienia dotyczące pojemności sieci, akceleratorów sieci WAN i urządzeń równoważenia obciążenia, które są używane do nawiązywania połączenia z Office 365.'
ms.openlocfilehash: 3b79e73f292ecf1db38a90364db3d2e475723158
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622817"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planowanie urządzeń sieciowych łączących się z usługami Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*
  
Niektóre sprzęty sieciowe mogą mieć ograniczenia dotyczące liczby obsługiwanych sesji współbieżnych. W przypadku organizacji mających ponad 2000 użytkowników zalecamy monitorowanie urządzeń sieciowych w celu upewnienia się, że są w stanie obsługiwać dodatkowy ruch Office 365 usług. Proste oprogramowanie do monitorowania protokołu SNMP (Network Management Protocol) może ci w tym pomóc.

Ten artykuł jest częścią [planowania sieci i dostrajania wydajności dla Office 365](./network-planning-and-performance.md).

Ustawienia lokalnego wychodzącego internetowego serwera proxy mają również wpływ na łączność z usługami Office 365 dla aplikacji klienckich. Należy również skonfigurować sieciowe urządzenia proxy, aby zezwalać na połączenia dla adresów URL i aplikacji usług w chmurze firmy Microsoft. Każda organizacja jest inna. Aby dowiedzieć się, jak firma Microsoft zarządza tym procesem i jaka jest przepustowość, którą aprowizujemy, [przeczytaj analizę przypadku](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Poniższe artykuły Skype dla firm Pomoc zawierają więcej informacji na temat ustawień Skype dla firm:
  
- [Rozwiązywanie problemów z błędami logowania Skype dla firm Online dla administratorów](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Nie można nawiązać połączenia z Skype dla firm lub niektóre funkcje nie działają, ponieważ zapora lokalna blokuje połączenie](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Chociaż wiele z tych ustawień jest specyficznych dla Skype dla firm, ogólne wskazówki dotyczące konfiguracji sieci są przydatne dla wszystkich usług Office 365.
  
## <a name="determining-network-capacity"></a>Określanie pojemności sieci

Każde urządzenie sieciowe, które istnieje w połączeniu, ma limit pojemności. Urządzenia te obejmują karty sieciowe klienta i serwera, routery, przełączniki i koncentratory, które je łączą. Odpowiednia pojemność sieci oznacza, że żadna z nich nie jest nasycona. Monitorowanie aktywności sieciowej ma zasadnicze znaczenie dla zapewnienia, że rzeczywiste obciążenia na wszystkich urządzeniach sieciowych są mniejsze niż ich maksymalna pojemność. Pojemność sieci wpływa na wydajność urządzenia proxy.
  
W większości sytuacji przepustowość połączenia internetowego określa limit ilości ruchu. Słaba wydajność w godzinach szczytu ruchu jest prawdopodobnie spowodowana nadmiernym użyciem łącza internetowego. Ta sytuacja ma również zastosowanie do scenariusza biura oddziału, w którym komputery serwera proxy biura oddziału są połączone z urządzeniem proxy w siedzibie oddziału za pośrednictwem powolnego łącza sieci rozległej (WAN).
  
Aby przetestować pojemność sieci, monitoruj aktywność sieci w interfejsie sieciowym serwera proxy. Jeśli jest to ponad 75 procent maksymalnej przepustowości dowolnego interfejsu sieciowego, rozważ zwiększenie przepustowości infrastruktury sieciowej, która jest niewystarczająca. Możesz też rozważyć użycie zaawansowanych funkcji, takich jak kompresja HTTP.
  
## <a name="wan-accelerators"></a>Akceleratory sieci WAN

Jeśli Organizacja korzysta z urządzeń serwera proxy przyspieszania sieci rozległej (WAN), podczas uzyskiwania dostępu do usług Office 365 mogą wystąpić problemy. Może być konieczne zoptymalizowanie urządzenia lub urządzeń sieciowych w celu zapewnienia, że użytkownicy mają spójne środowisko podczas uzyskiwania dostępu do Office 365. Na przykład usługi Office 365 szyfrować część zawartości Office 365 i nagłówek TCP. Urządzenie może nie być w stanie obsłużyć tego rodzaju ruchu.
  
Przeczytaj naszą instrukcję pomocy technicznej dotyczącą [używania kontrolera optymalizacji sieci WAN lub urządzeń ruchu/inspekcji z Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Sprzętowe i programowe urządzenia równoważenia obciążenia

Twoja organizacja musi używać sprzętowego modułu równoważenia obciążenia (HLB) lub rozwiązania równoważenia obciążenia sieciowego (NLB) do dystrybucji żądań na serwerach Active Directory Federation Services (AD FS) i/lub serwerach hybrydowych Exchange. Urządzenia równoważenia obciążenia kontrolują ruch sieciowy do serwerów lokalnych. Te serwery mają kluczowe znaczenie dla zapewnienia dostępności logowania jednokrotnego i Exchange wdrożenia hybrydowego.
  
Udostępniamy oparte na oprogramowaniu rozwiązanie równoważenia obciążenia sieciowego wbudowane w Windows Server. Office 365 obsługuje to rozwiązanie w celu zapewnienia równoważenia obciążenia.
  
## <a name="firewalls-and-proxies"></a>Zapory i serwery proxy

Aby uzyskać więcej informacji na temat konfigurowania zapór i serwerów proxy w celu nawiązywania połączenia z Office 365, zobacz [Zarządzanie punktami końcowymi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Ocenianie łączności sieciowej Office 365](assessing-network-connectivity.md) i [Office 365 punktów końcowych — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d), aby dowiedzieć się więcej o urządzeniach i wyborze obwodów.
  
## <a name="see-also"></a>Zobacz też

[Przewodniki konfiguracji dla usług Office 365](setup-guides-for-microsoft-365.md)

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)