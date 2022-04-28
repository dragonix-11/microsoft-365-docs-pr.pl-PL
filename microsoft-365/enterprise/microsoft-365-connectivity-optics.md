---
title: optyka łączności Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Ten artykuł zawiera informacje o Microsoft 365 Connectivity Optics.
ms.openlocfilehash: cda5fa074aa04be5fbbaff9b98360a3a2f927fc2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090324"
---
# <a name="microsoft-365-connectivity-optics"></a>optyka łączności Microsoft 365

W tym dokumencie opisano niektóre optyki łączności, które firma Microsoft zwykle zbiera z urządzeń klientów, oraz opisano niektóre sposoby, w jakie firma Microsoft używa takich danych do analizowania i optymalizowania dostarczania usług oraz do oceny i zapewnienia najlepszego możliwego środowiska użytkownika końcowego.

Optyka łączności jest zwykle zbierana z aplikacji firmy Microsoft, które mogą być instalowane na urządzeniach użytkowników końcowych lub uzyskiwane z przeglądarek. W przeciwieństwie do opcjonalnego zbierania danych w ramach usług Microsoft 365, wiele optyki łączności opisanych w tym miejscu jest integralną częścią zapewniania, że firma Microsoft spełnia nasze zobowiązanie w zakresie dostępności i wydajności wobec klientów. Ta optyka umożliwia firmie Microsoft szybkie wykrywanie i reagowanie na wszelkie problemy w ścieżce łączności między użytkownikami końcowymi a punktami końcowymi usługi firmy Microsoft. Niektóre z tych optyk są również używane do włączania funkcji, takich jak [łączność sieciowa w centrum Administracja Microsoft 365](office-365-network-mac-perf-overview.md).

## <a name="optics-collected-from-microsoft-365-applications"></a>Optyka zebrana z aplikacji Microsoft 365

Optyka jest obecnie zbierana przy użyciu rzadkiego próbkowania na wszystkich urządzeniach. Ogólnie rzecz biorąc, określony zestaw optyk i miejsc docelowych (punktów końcowych usługi), które mają być mierzone w określonej iteracji, jest konfigurowany przez firmę Microsoft na podstawie wymagań dotyczących usługi i losowy do celów próbkowania.
W każdym interwale zbierania danych optycznych co najmniej jeden z następujących pomiarów może być zbierany przy użyciu urządzenia użytkownika końcowego jako źródła pomiaru i punktu końcowego usługi Microsoft 365 jako miejsca docelowego pomiaru:

| Pomiaru | Opis |
| --- | --- |
| Opóźnienie | Czas potrzebny na pobranie małego pliku za pośrednictwem protokołu HTTP |
| Przepustowość | Czas potrzebny na pobranie większego pliku za pośrednictwem protokołu HTTP, mierzony rzadko w celu uniknięcia nadmiernego użycia przepustowości |
| Czas rundy (RTT) | Polecenie ping protokołu ICMP |
| Traceroute | ICMP traceroute |

Każdy pomiar jest zwykle skojarzony z dodatkowymi informacjami, które mogą obejmować następujące elementy:

| Element | Opis |
| --- | --- |
| Identyfikator dzierżawy | Unikatowy identyfikator dzierżawy Azure Active Directory klienta skojarzonej z urządzeniem użytkownika końcowego. |
| Identyfikator monitora | Identyfikator aplikacji generującej żądanie (na przykład Outlook, OneDrive itp.), dostarczony przez aplikację kliencką, która wykonuje pomiar. |
| Identyfikator żądania | Identyfikator żądania pomiaru określony w konfiguracji miary dostarczonej przez firmę Microsoft. |
| Zdalny adres IP | Zamaskowany źródłowy adres IP skojarzony z żądaniem od klienta do punktu końcowego usługi dostarczonym przez serwer, który odebrał żądanie pomiaru i został obliczony na podstawie źródłowego adresu IP klienta, który jest widoczny dla firmy Microsoft. Adresy IP są maskowane w podsieci /24 dla adresów IPv4 lub /48 podsieci adresów IPv6, aby upewnić się, że firma Microsoft nie może zidentyfikować poszczególnych urządzeń lub użytkowników. |
| Frontonu | Microsoft 365 identyfikator frontonu usługi dostarczony przez serwer, który otrzymał żądanie pomiaru. |
| Punkt końcowy | Microsoft 365 lokalizacji punktu końcowego usługi udostępnianej przez serwer, który otrzymał żądanie pomiaru. |
| Certyfikat wystawiony przez | Właściwość "certyfikat wystawiony przez" certyfikatu SSL przedstawiona podczas nawiązywania połączenia z punktem końcowym usługi, która wskazuje urząd certyfikacji, który wystawił certyfikat dla punktu końcowego usługi. |
| Odcisk palca certyfikatu | Właściwość "odcisk palca certyfikatu" certyfikatu SSL przedstawiona podczas nawiązywania połączenia z punktem końcowym usługi, który jest publicznie dostępnym unikatowym identyfikatorem certyfikatu. |
| Szerokość geograficzna/długość geograficzna | Abstrakcyjna szerokość i długość geograficzna urządzenia użytkownika końcowego. Jest to zbierane tylko dla dzierżawców, którzy włączyli usługę lokalizacji Windows na urządzeniach użytkowników końcowych, a także [włączyli zbieranie tych informacji w portalu administracyjnym Microsoft 365](office-365-network-mac-perf-overview.md#1-enable-windows-location-services). |

## <a name="measurement-process"></a>Proces pomiaru

Każde urządzenie użytkownika końcowego zazwyczaj wykonuje pomiar zgodnie z harmonogramem (dla zainstalowanych aplikacji) lub na podstawie akcji ładowania stron przeglądarki (dla aplikacji internetowych). Działania pomiarowe są wykonywane jako operacje w tle i nie mają wpływu na środowisko aplikacji dla użytkowników. Ponieważ typy pomiarów i miejsca docelowe, które będą używane do określonej iteracji tego procesu, są losowe, klienci mogą zauważyć żądania do punktów końcowych usługi firmy Microsoft w ich regionie, które są podobne do typowych żądań złożonych przez urządzenia użytkowników końcowych w celu zapewnienia normalnej łączności z aplikacjami. Ponadto klienci mogą zauważyć żądania do punktów końcowych usługi firmy Microsoft, które znajdują się poza ich regionem lokalnym. Te pomiary są często używane w celu zapewnienia optymalnego routingu żądań klientów do najlepszego punktu końcowego usługi, ponieważ zmiany w infrastrukturze klientów i usługodawców sieciowych mogą wymagać od firmy Microsoft ciągłej zmiany zasad routingu żądań. Dowiedz się więcej o tym, jak firma Microsoft kieruje ruch do najlepszego punktu końcowego usługi i jak zoptymalizować łączność z usługami Microsoft 365 w [omówieniu łączności sieciowej Microsoft 365](microsoft-365-networking-overview.md).

## <a name="service-endpoints"></a>Punkty końcowe usługi

Punkty końcowe usługi firmy Microsoft używane jako miejsca docelowe tych pomiarów znajdują się w opublikowanych [Office 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md). Dostęp do dodatkowych punktów końcowych usługi nie jest niezbędny do zbierania tych optycznych połączeń.
