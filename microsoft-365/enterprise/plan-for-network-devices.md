---
title: Planowanie urządzeń sieciowych, które łączą się z Office 365 sieci
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: W tym artykule opisano zagadnienia związane z pojemnością sieci, akceleratorów WAN i urządzeń do równoważenia obciążenia używanych do łączenia się z siecią Office 365.'
ms.openlocfilehash: 38df9a64610c4b4d44014a142bf7d255aa0a0f46
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973655"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planowanie urządzeń sieciowych, które łączą się z Office 365 sieci

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*
  
Niektóre urządzenia sieciowe mogą mieć ograniczenia dotyczące obsługiwanej liczby jednoczesnych sesji. W przypadku organizacji mających więcej niż 2000 użytkowników zalecamy, aby monitorowały one swoje urządzenia sieciowe w celu upewnienia się, że są one w stanie obsługi dodatkowego ruchu Office 365 usług. Może to ułatwić oprogramowanie do monitorowania protokołu SNMP (Simple Network Management Protocol).

Ten artykuł jest częścią [artykułu Planowanie sieci i dostosowywanie wydajności pod Office 365](./network-planning-and-performance.md).

Ustawienia lokalnego wychodzącego internetowego serwera proxy mają również wpływ na łączność Office 365 usługami dla aplikacji klienckich. Musisz również skonfigurować swoje sieciowe urządzenia proxy, aby zezwalały na połączenia z adresami URL i aplikacjami usług firmy Microsoft w chmurze. Każda organizacja jest inna. Aby dowiedzieć się, jak firma Microsoft zarządza tym procesem i jaką przepustowość zapewnia, przeczytaj [analizę przypadku](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
W następujących Skype dla firm Pomocy podano więcej informacji o Skype dla firm ustawieniach:
  
- [Rozwiązywanie problemów Skype dla firm błędami podczas logowania się do usługi Online dla administratorów](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Nie można nawiązać połączenia Skype dla firm lub niektóre funkcje nie działają, ponieważ zapora lokalna blokuje połączenie](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Wiele z tych ustawień jest Skype dla firm, jednak ogólne wskazówki dotyczące konfiguracji sieci są przydatne dla wszystkich Office 365 sieci.
  
## <a name="determining-network-capacity"></a>Określanie pojemności sieci

Każde urządzenie sieciowe, które istnieje w połączeniu, ma swój limit pojemności. Do tych urządzeń należą karty sieciowe, routery, przełączniki i koncentratory, które je wzajemnie ze sobą połączone. Odpowiednia pojemność sieci oznacza, że żadne z tych urządzeń nie jest w nasyceniu. Monitorowanie aktywności sieciowej ma kluczowe znaczenie dla zapewnienia rzeczywistego obciążenia wszystkich urządzeń sieciowych poniżej ich maksymalnej pojemności. Pojemność sieci wpływa na wydajność urządzenia proxy.
  
W większości przypadków przepustowość połączenia internetowego określa limit ilości ruchu. Niska wydajność w godzinach szczytu ruchu jest prawdopodobnie spowodowana nadmiarowym korzystaniem z linku internetowego. Ta sytuacja dotyczy również scenariusza, w którym komputery serwera proxy oddziału firmy są połączone z urządzeniem proxy w siedzibie głównej za pośrednictwem wolnego łącza sieci wide area network (WAN).
  
Aby przetestować pojemność sieci, należy monitorować aktywność sieciową na interfejsie sieciowym serwera proxy. Jeśli jest to więcej niż 75 procent maksymalnej przepustowości dowolnego interfejsu sieciowego, należy rozważyć zwiększenie przepustowości infrastruktury sieciowej, która jest nieodpowiednia. Rozważ też korzystanie z zaawansowanych funkcji, takich jak kompresja HTTP.
  
## <a name="wan-accelerators"></a>Akceleratory WAN

Jeśli organizacja korzysta z urządzeń proxy przyspieszania sieci lokalnej (WAN), podczas uzyskiwania dostępu do usług internetowych mogą wystąpić Office 365 sieci. Może być konieczne zoptymalizowanie urządzeń sieciowych w celu zapewnienia, że użytkownicy mają spójne środowisko podczas uzyskiwania dostępu do Office 365. Na przykład usługi Office 365 szyfrują część Office 365 zawartości i nagłówka TCP. Urządzenie może nie być w stanie obsłużyć ruchu tego rodzaju.
  
Przeczytaj nasze oświadczenie o pomocy technicznej dotyczące [używania kontrolera optymalizacji sieci WAN lub urządzeń do obsługi ruchu/inspekcji z Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Urządzenia do równoważenia obciążenia sprzętu i oprogramowania

Twoja organizacja musi używać narzędzia do równoważenia obciążenia sprzętu (HLB, Hardware Load Balancing) lub rozwiązania do równoważenia obciążenia sieciowego (NLB, Network Load Balancing) w celu rozpowszechniania żądań do serwerów usług Federatorów Active Directory (AD FS) i/lub twoich Exchange hybrydowych. Urządzenia do równoważenia obciążenia sterują ruchem sieciowym na serwerach lokalnych. Serwery te mają kluczowe znaczenie przy zapewnianiu dostępności logowania pojedynczego i Exchange hybrydowego.
  
Zapewniamy programowe rozwiązanie NLB wbudowane w program Windows Server. Office 365 obsługuje to rozwiązanie w celu równoważenia obciążenia.
  
## <a name="firewalls-and-proxies"></a>Zapory i proxy

Aby uzyskać więcej szczegółowych informacji na temat konfigurowania zapór i serwerów proxy do łączenia się z usługą Office 365, zobacz Zarządzanie punktami końcowymi programu [Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), Ocena łączności sieciowej i punkty końcowe [](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) programu [Office 365 Office 365](assessing-network-connectivity.md) — często zadawane pytania, aby dowiedzieć się więcej o urządzeniach i wyborze obwodu.
  
## <a name="see-also"></a>Zobacz też

[Przewodniki konfiguracji dla usług Office 365 internetowych](setup-guides-for-microsoft-365.md)

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)