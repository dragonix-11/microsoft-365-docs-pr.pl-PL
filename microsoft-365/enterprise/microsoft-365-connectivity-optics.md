---
title: Microsoft 365 łączności
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Ten artykuł zawiera informacje na temat Microsoft 365 łączności.
ms.openlocfilehash: c1ee14966f13ff50ff809ebbdf4c578bf949e956
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959563"
---
# <a name="microsoft-365-connectivity-optics"></a>Microsoft 365 łączności

W tym dokumencie opisano niektóre narzędzia łączności, które firma Microsoft zwykle zbiera z urządzeń klientów, oraz sposoby, w jakie firma Microsoft używa tych danych do analizowania i optymalizowania dostarczania usług, a także oceniania i zapewnienia jak najlepszego doświadczenia użytkownika końcowego.

Kable łączności są zwykle zbierane z aplikacji firmy Microsoft, które mogą być instalowane na urządzeniach użytkowników końcowych lub dostępne z przeglądarek. W przeciwieństwie do opcjonalnego zbierania danych Microsoft 365, wiele opisanych tutaj tutaj elementów łączności jest integralną częścią zapewniania zgodności firmy Microsoft z naszymi zobowiązaniami w zakresie dostępności i wydajności dla klientów. Dzięki tym czujnikom firma Microsoft może szybko wykrywać problemy na ścieżce łączności między użytkownikami końcowymi a punktami końcowymi usługi firmy Microsoft oraz reagować na nie. Niektóre z tych urządzeń są również używane do włączania funkcji, takich jak [łączność sieciowa w centrum Administracja Microsoft 365 sieci.](office-365-network-mac-perf-overview.md)

## <a name="optics-collected-from-microsoft-365-applications"></a>Kable zebrane z Microsoft 365 aplikacji

Kable są obecnie zbierane przy próbkowaniu rzadko ze wszystkich urządzeń. Ogólnie rzecz biorąc, konkretny zestaw kable i miejsca docelowe (punkty końcowe usługi), które mają być mierzone w określonej iteracji, jest konfigurowany przez firmę Microsoft na podstawie wymagań usługi i losowo do celów próbkowania.
Dla każdego interwału kolekcji sterowników może zostać zebrany co najmniej jeden z poniższych pomiarów, używając urządzenia użytkownika końcowego jako źródła miary i punktu końcowego usługi Microsoft 365 jako miejsca docelowego miary:

| Miary | Opis |
| --- | --- |
| Opóźnienie | Czas pobierania małego pliku za pośrednictwem protokołu HTTP |
| Przepływność | Czas pobierania większego pliku za pośrednictwem protokołu HTTP mierzony rzadko w celu uniknięcia nadmiarowego zużycia przepustowości |
| Czas rundy (RTT) | Polecenie ping ICMP |
| Traceroute | Śledzenie ICMP |

Każdy miara jest zazwyczaj skojarzony z dodatkowymi informacjami, które mogą obejmować następujące elementy:

| Element | Opis |
| --- | --- |
| Identyfikator dzierżawy | Unikatowy identyfikator dzierżawy klienta Azure Active Directory skojarzonej z urządzeniem użytkownika końcowego. |
| Identyfikator monitora | Identyfikator aplikacji generującej żądanie (taki jak Outlook, OneDrive itp.), podany przez aplikację kliencową wykonującą miarę. |
| Identyfikator żądania | Identyfikator żądania miary określonego w konfiguracji miary udostępnianej przez firmę Microsoft. |
| Zdalny adres IP | Maskowany adres IP źródła skojarzony z żądaniem od punktu końcowego klienta do usługi dostarczony przez serwer, który otrzymał żądanie miary, i obliczany na podstawie adresu IP źródła klienta widocznego dla firmy Microsoft. Adresy IP są maskowane do podsieci /24 dla adresów IPv4 lub do podsieci /48 dla adresów IPv6, aby zapewnić, że firma Microsoft nie będzie w stanie zidentyfikować poszczególnych urządzeń lub użytkowników. |
| Front-end | Microsoft 365 identyfikatora frontoronu usługi podanego przez serwer, który otrzymał żądanie miary. |
| Punkt końcowy | Microsoft 365 punktu końcowego usługi, podanej przez serwer, który otrzymał żądanie miary. |
| Certyfikat wystawiony przez | Właściwość "Certyfikat wystawiony przez" certyfikatu SSL przedstawiona podczas nawiązywania połączenia z punktem końcowym usługi, która wskazuje urząd certyfikacji, który wystawił certyfikat dla punktu końcowego usługi. |
| Certificate Thumbprint | Właściwość "certificate thumbprint" certyfikatu SSL przedstawiona podczas nawiązywania połączenia z punktem końcowym usługi, który jest publicznie dostępnym identyfikator unikatowy certyfikatu. |
| Szerokość/długość geograficzna | A abstrakcyjna szerokość i długość geograficzna urządzenia użytkownika końcowego. Ta usługa jest zbierana tylko dla dzierżaw, którzy włączyli usługę Windows lokalizacji na urządzeniach użytkowników końcowych i włączyli także zbieranie tych informacji w portalu administracyjnym usługi [Microsoft 365](office-365-network-mac-perf-overview.md#1-enable-windows-location-services). |

## <a name="measurement-process"></a>Proces mierzenia

Każde urządzenie użytkownika końcowego zwykle wykonuje pomiary według harmonogramu (w przypadku zainstalowanych aplikacji) lub na podstawie akcji ładowania stron przeglądarki (w przypadku aplikacji internetowych). Działania pomiarowe są wykonywane jako operacje w tle i nie mają wpływu na działanie aplikacji dla użytkowników. Ponieważ typy miar i miejsca docelowe używane dla określonej iteracji tego procesu są losowo, klienci mogą zauważyć żądania do punktów końcowych usługi firmy Microsoft w swoim regionie, które są podobne do typowych żądań składanych przez urządzenia użytkowników końcowych na potrzeby normalnej łączności aplikacji. Ponadto klienci mogą zauważyć żądania do punktów końcowych usługi firmy Microsoft, które znajdują się na zewnątrz ich regionu lokalnego. Te miary często są używane w celu zapewnienia optymalnego routingu żądań klientów do najlepszego punktu końcowego usługi, ponieważ zmiany w infrastrukturze klienta i usługodawcy internetowego mogą na bieżąco wymagać od firmy Microsoft zmiany zasad routingu żądań. Dowiedz się więcej o tym, jak firma Microsoft kieruje ruch do najlepszego punktu końcowego usługi i jak zoptymalizować łączność z Microsoft 365 usługami w Microsoft 365 [sieciowym](microsoft-365-networking-overview.md).

## <a name="service-endpoints"></a>Punkty końcowe usługi

Punkty końcowe usługi firmy Microsoft używane jako miejsca docelowe tych miar znajdują się w opublikowanych adresach URL Office 365 [i zakresach adresów IP](urls-and-ip-address-ranges.md). Dostęp do dodatkowych punktów końcowych usługi nie jest konieczny dla kolekcji tych elementów łączności.
