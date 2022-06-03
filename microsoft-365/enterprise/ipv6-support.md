---
title: Obsługa protokołu IPv6 w usługach Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Podsumowanie: Opisuje obsługę protokołu IPv6 w składnikach Microsoft 365 i w ofertach Microsoft 365 dla instytucji rządowych.'
ms.openlocfilehash: 2619567e8dac6f4b87cba0108bcf105011c4a87c
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872747"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Obsługa protokołu IPv6 w usługach Microsoft 365

Wraz z rosnącym wdrażaniem i obsługą protokołu IPv6 w sieciach przedsiębiorstwa, dostawcach usług i urządzeniach wielu klientów zastanawia się, czy ich użytkownicy mogą nadal uzyskiwać dostęp do usług Microsoft 365 z klientów IPv6 i sieci IPv6. Microsoft 365 usługi mogą być pomyślnie używane zarówno z urządzeń z podwójnym stosem IPv6, jak i urządzeń tylko dla protokołu IPv6. W rzeczywistości mamy coraz większą liczbę klientów, od konsumentów po duże przedsiębiorstwa, którzy zmierzają w kierunku większego wdrożenia protokołu IPv6. W przypadku większości klientów protokół IPv4 nie zniknie całkowicie z ich cyfrowego krajobrazu, dlatego nie planujemy wymagać protokołu IPv6 ani anulować priorytetów protokołu IPv4 w żadnych Microsoft 365 funkcji lub usług.

Jednym z naszych kluczowych priorytetów w Microsoft 365 jest zapewnienie bezproblemowego środowiska klienta i użytkownika przez Internet z dowolnej lokalizacji z dowolnego urządzenia. Obejmuje to dostęp do Microsoft 365 z urządzeń klientów korzystających z protokołu IPv6 w konfiguracji podwójnego stosu, a także przejście do wdrożeń klientów tylko dla protokołu IPv6. W większości przypadków, gdy stosujesz standardowy internetowy model nawiązywania połączenia z Microsoft 365 zgodnie z opisem w [temacie Microsoft 365 zasad łączności sieciowej](microsoft-365-network-connectivity-principles.md), [Microsoft 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md) oraz [Microsoft 365 najlepszych rozwiązań dotyczących planowania sieci](network-and-migration-planning.md#best-practices-for-network-planning-and-improving-migration-performance-for-office-365) , przejścia protokołu IPv6 nie będą zakłócać środowiska użytkownika.

Wiele usług Microsoft 365 już obecnie zapewnia natywną obsługę protokołu IPv6 i można uzyskać do niej dostęp bezpośrednio z poziomu podwójnego stosu IPv6 i klientów tylko dla protokołu IPv6. Microsoft 365 umożliwia również dostęp za pośrednictwem konwencjonalnych technologii tłumaczenia IPv6 do protokołu IPv4 (takich jak podstawowe serwery proxy 64 lub DNS64/NAT64) często używanych przez klientów i dostawców rozwiązań sieciowych do łączenia się z zasobami internetowymi IPv4.

Podobnie jak w przypadku wszystkich usług SaaS i Internetu, zakres natywnych interfejsów Microsoft 365, funkcji i interfejsów API z obsługą protokołu IPv6 rozszerza się w sposób ciągły i bez bezpośredniego działania i kontroli klienta. Jeśli używasz usług IPv6 lub IPv6 tylko w sieciach, które wymagają dostępu do Microsoft 365 i Internetu, zaleca się uwzględnienie dynamicznych mechanizmów przejściowych IPv6/IPv4, takich jak DNS64/NAT64, aby zapewnić kompleksową łączność IPv6 z Microsoft 365 bez żadnych dalszych ponownych konfiguracji sieci.

Większość usług Microsoft 365 została lub zostanie całkowicie włączona z funkcjami IPv6 dla użytkowników końcowych i administratorów IT. Niektóre scenariusze Microsoft 365 (takie jak anonimowe przychodzące wiadomości e-mail) mają specjalne wymagania i zagadnienia dotyczące użycia w połączeniu z IPv6. Aby uzyskać więcej informacji na temat wymagań i zagadnień związanych ze scenariuszem IPv6, skontaktuj się z zespołem ds. konta Microsoft lub pomocą techniczną firmy Microsoft.

Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)

## <a name="see-also"></a>Zobacz też

[Omówienie łączności sieciowej Microsoft 365](microsoft-365-networking-overview.md)

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Usługa Office 365 — usługa sieci Web adresów IP i adresów URL](microsoft-365-ip-web-service.md)

[Ocena łączności sieciowej na platformie Microsoft 365](assessing-network-connectivity.md)

[Planowanie sieci i dostrajanie wydajności dla Microsoft 365](network-planning-and-performance.md)

[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)

[Sieci dostarczania zawartości](content-delivery-networks.md)

[test łączności Microsoft 365](https://aka.ms/netonboard)

[Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[blog sieci Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
