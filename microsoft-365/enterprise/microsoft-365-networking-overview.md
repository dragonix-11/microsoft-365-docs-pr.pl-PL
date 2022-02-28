---
title: Microsoft 365 na temat łączności sieciowej
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 08/27/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: W tym artykule omówiono, dlaczego optymalizacja sieci jest ważna dla usług SaaS, celem tworzenia sieci Microsoft 365 sieci i w jaki sposób oprogramowanie SaaS wymaga sieci innych niż inne obciążenia pracą.
ms.openlocfilehash: e5dcbae5a1fbac3b0b4fd4472fdcac2380b84382
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988402"
---
# <a name="microsoft-365-network-connectivity-overview"></a>Microsoft 365 na temat łączności sieciowej

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 to rozłożona chmura typu Oprogramowanie jako usługa (Software-as-a-Service, SaaS), która zapewnia scenariusze zwiększające produktywność i współpracę za pośrednictwem zróżnicowanego zestawu mikro-usług i aplikacji. Składniki klienta pakietu Microsoft 365, takie Outlook, Word i PowerPoint, działają na komputerach użytkowników i łączą się z innymi składnikami programu Microsoft 365, które działają w centrach danych firmy Microsoft. Najbardziej znaczącym czynnikiem, który określa jakość środowiska użytkownika końcowego Microsoft 365 jest niezawodność sieci i niskie opóźnienie między klientami Microsoft 365 a Microsoft 365 frontem usługi.

W tym artykule dowiesz się więcej o celach Microsoft 365 sieci i dlaczego tworzenie sieci Microsoft 365 wymaga innego podejścia do optymalizacji niż ogólny ruch internetowy.

## <a name="microsoft-365-networking-goals"></a>Microsoft 365 celów sieciowych

Najlepszym celem sieci Microsoft 365 jest zoptymalizowanie działania użytkownika końcowego przez włączenie najmniej restrykcyjnego dostępu między klientami a najbliższymi Microsoft 365 końcowymi. Jakość działania użytkownika końcowego jest bezpośrednio związana z wydajnością i szybkością działania aplikacji, z których korzysta użytkownik. Na przykład funkcja Microsoft Teams korzysta z małych opóźnień, dzięki czemu połączenia telefoniczne użytkowników, konferencje i współużytkowane funkcje współpracy ekranu są bez problemów, Outlook korzysta z wysokiej łączności sieciowej w celu obsługi funkcji wyszukiwania błyskawicznego, które stosują indeksowanie po stronie serwera i funkcje AI.

Podstawowym celem projektu sieci powinno być zminimalizowanie opóźnień przez skrócenie czasu rundy (RTT) z komputerów klienckich do globalnej sieci firmy Microsoft — podstawowej sieci publicznej firmy Microsoft, która łączy wszystkie centra danych firmy Microsoft z małymi opóźnieniami i wysoką dostępnością punktów wprowadzania aplikacji w chmurze na całym świecie. Więcej informacji o globalnej sieci firmy Microsoft można znaleźć w te sposób, w jaki firma [Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Optymalizowanie Microsoft 365 sieci nie musi być skomplikowane. Najlepszą możliwą wydajność można uzyskać, korzystając z kilku najważniejszych zasad:

- Identyfikowanie Microsoft 365 sieciowego
- Zezwalaj na ruch wychodzący z lokalnej gałęzi Microsoft 365 do Internetu z każdej lokalizacji, w której użytkownicy nawiąż połączenie z Microsoft 365
- Zezwalanie Microsoft 365 ruchu na pomijanie serwerów proxy i urządzeń do inspekcji pakietów

Aby uzyskać więcej informacji Microsoft 365 dotyczących łączności sieciowej, [zobacz zasady Microsoft 365 łączności sieciowej](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Tradycyjne architektury sieci i oprogramowanie SaaS

Tradycyjne zasady architektury sieci dla obciążeń klientów/serwerów projektuje się przy założeniu, że ruch między klientami i punktami końcowymi nie obejmuje obwodu sieci firmowej. Ponadto w wielu sieciach przedsiębiorstwa wszystkie połączenia internetowe wychodzące przechodzenie przez sieć firmową i ruch wychodzący z lokalizacji centralnej.

W tradycyjnych architekturach sieci wyższe opóźnienia dla ogólnego ruchu internetowego są niezbędne do utrzymania zabezpieczeń obwodu sieci, a optymalizacja wydajności dla ruchu internetowego zazwyczaj wymaga uaktualnienia lub skalowania sprzętu w punktach ruchu wychodzącego do sieci. Takie podejście nie spełnia jednak wymagań w celu zapewnienia optymalnej wydajności sieci usług SaaS, takich jak Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identyfikowanie Microsoft 365 sieciowego

Ułatwiamy identyfikowanie ruchu sieciowego Microsoft 365 oraz ułatwiamy zarządzanie identyfikacją sieci.

- Nowe kategorie punktów końcowych sieci odróżniają bardzo krytyczny ruch sieciowy od ruchu sieciowego, na który nie mają wpływu opóźnienia internetowe. Istnieje tylko kilka adresów URL i obsługa adresów IP w najważniejszej kategorii "Optymalizowanie".
- Usługi sieci Web do obsługi skryptów lub bezpośredniej konfiguracji urządzenia i zarządzania zmianą Microsoft 365 sieci. Zmiany są dostępne z usługi sieci Web, w formacie RSS lub w wiadomości e-mail przy użyciu Microsoft Flow szablonu.
- [Office 365 partnerów](./microsoft-365-networking-partner-program.md) sieciowych partnerom firmy Microsoft, którzy dostarczają urządzenia lub usługi zgodnie Microsoft 365 zasadami łączności sieciowej i mają prostą konfigurację.

## <a name="securing-microsoft-365-connections"></a>Zabezpieczanie Microsoft 365 sieci

Celem tradycyjnych zabezpieczeń sieci jest ochrona obwodu sieci firmowej przed dostępem osób do sieci i złośliwymi wykorzystywaniami. Większość sieci przedsiębiorstw wymusza zabezpieczenia sieci dla ruchu internetowego za pomocą technologii, takich jak serwery proxy, zapory, przerwa i inspekcja PROTOKOŁU SSL, dogłębna inspekcja pakietów i systemy ochrony przed utratą danych. Te technologie zapewniają istotne środki zaradcze dla ogólnych żądań internetowych, ale mogą znacznie zmniejszyć wydajność, skalowalność i jakość środowiska użytkownika końcowego stosowanego do Microsoft 365 końcowych.

Microsoft 365 pomaga sprostać potrzebom organizacji w zakresie zabezpieczeń zawartości i zgodności z użyciem danych dzięki wbudowanym funkcjam zabezpieczeń i zarządzania, zaprojektowanym specjalnie z myślą o Microsoft 365 funkcjach i obciążeniach pracą. Aby uzyskać więcej informacji na Microsoft 365 zabezpieczeń i zgodności, zobacz przewodnik dotyczący Office 365 [zabezpieczeń](/office365/securitycompliance/security-roadmap). Aby uzyskać więcej informacji na temat zaleceń i pomocy technicznej firmy Microsoft dotyczących zaawansowanych rozwiązań sieciowych, które wykonują zaawansowane przetwarzanie ruchu na poziomie Microsoft 365, zobacz Korzystanie z urządzeń sieciowych innych firm lub rozwiązań w Office 365 [sieci](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Dlaczego różni Microsoft 365 sieci?

Microsoft 365 celu zapewnienia optymalnej wydajności przy użyciu zabezpieczeń punktów końcowych i zaszyfrowanych połączeń sieciowych, co ogranicza konieczność wymuszania zabezpieczeń obwodowych. Microsoft 365 centra danych znajdują się na całym świecie, a usługa została zaprojektowana tak, aby używać różnych metod łączenia klientów z najlepszymi dostępnymi punktami końcowymi usługi. Dane użytkowników i ich przetwarzanie są rozpowszechniane między wieloma centrami danych firmy Microsoft, dlatego nie istnieje pojedynczy punkt końcowy sieci, z którym można nawiązać połączenie z komputerami klienckimi. Dane i usługi w dzierżawie usługi Microsoft 365 są dynamicznie optymalizowane przez sieć globalną firmy Microsoft w celu dostosowania ich do lokalizacji geograficznych, z których są dostępne dla użytkowników końcowych.

Niektóre typowe problemy z wydajnością są tworzone Microsoft 365 przypadku, gdy ruch sieciowy podlega inspekcji pakietów i scentralizowanemu ruchu wychodzącemu:

- Duże opóźnienie może powodować niską wydajność strumieni wideo i audio oraz wolne reakcje na pobieranie danych, wyszukiwania, współpracę w czasie rzeczywistym, informacje o czasie wolnym/zajętym w kalendarzu, zawartość w produktach i inne usługi
- Połączenia wychodzące z lokalizacji centralnej pokonają możliwości routingu dynamicznego sieci Microsoft 365 globalnej, dodając opóźnienie i czas rundy
- Odszyfrowywanie Microsoft 365 SSL do ruchu sieciowego i ponowne szyfrowanie może powodować błędy protokołu i powodować zagrożenia bezpieczeństwa

Skrócenie ścieżki sieciowej do punktów wejścia Microsoft 365 przez umożliwienie ruchu klienckiego jak najbardziej zbliżonego do ich lokalizacji geograficznej może poprawić wydajność łączności i środowisko użytkownika końcowego w Microsoft 365. Może również pomóc zmniejszyć wpływ przyszłych zmian architektury sieci na wydajność Microsoft 365 niezawodności. Optymalny model łączności to zawsze zapewnianie ruchu wychodzącego w lokalizacji użytkownika, niezależnie od tego, czy znajduje się on w sieci firmowej, czy w lokalizacji zdalnej, takiej jak dom, hotel, kawiarnie lub lotniska. Generic Internet traffic and WAN based corporate network traffic would be separately routed and not use the local directgress model. Ten lokalny model bezpośredniego ruchu wychodzącego przedstawiono na poniższym diagramie.

![Lokalna architektura sieci ruchu wychodzącego.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Lokalna architektura ruchu wychodzącego oferuje następujące korzyści Microsoft 365 ruchu sieciowego w tradycyjnym modelu:
  
- Zapewnia optymalną Microsoft 365 przez optymalizację długości trasy. Połączenia użytkowników końcowych są dynamicznie kierowane do najbliższego punktu wejścia sieci Microsoft 365 przez infrastrukturę frontów frontowych usługi rozproszonej sieci  globalnej firmy Microsoft, a ruch jest następnie przekierowywane wewnętrznie do punktów końcowych danych i usług przez kable o wysokiej dostępności o wysokiej dostępności przez firmę Microsoft.
- Zmniejsza obciążenie firmowej infrastruktury sieciowej, zezwalając na lokalny ruch wychodzący z Microsoft 365 z pominięciem serwerów proxy i urządzeń do inspekcji ruchu.
- Zabezpiecza połączenia po obu stronach, stosując funkcje zabezpieczeń punktów końcowych klienta i chmury, unikając stosowania nadmiarowych technologii zabezpieczeń sieciowych.

> [!NOTE]
> Infrastruktura _drzwi frontowych usług rozłożonych (Distributed Service Front Door_ ) to wysoce dostępna i skalowalna krawędź sieci microsoft globalna z lokalizacjami geograficznymi. Kończy ono połączenia użytkowników końcowych i skutecznie kieruje je w obrębie globalnej sieci firmy Microsoft. Więcej informacji o globalnej sieci firmy Microsoft można znaleźć w te sposób, w jaki firma [Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Aby uzyskać więcej informacji na temat zrozumienia i stosowania Microsoft 365 dotyczących łączności sieciowej, [Microsoft 365 zasady łączności sieciowej](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Wnioski

Optymalizacja Microsoft 365 sieci w tak naprawdę sprowadza się do usuwania niepotrzebnych przeszkód. Traktując połączenia Microsoft 365 jako zaufany ruch, można zapobiec wprowadzania opóźnień przez inspekcję pakietów i konkurencję na przepustowość serwera proxy. Zezwolenie na połączenia lokalne między Office 365 klienta i punktami końcowymi umożliwia dynamiczne rozsyłanie ruchu za pośrednictwem globalnej sieci firmy Microsoft.

## <a name="related-topics"></a>Tematy pokrewne

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Zarządzanie Office 365 punktami końcowymi](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Office 365 adresu IP i usługi sieci Web adresu URL](microsoft-365-ip-web-service.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Planowanie sieci i dostosowywanie wydajności dla Microsoft 365](network-planning-and-performance.md)

[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)

[Sieci dostarczania zawartości](content-delivery-networks.md)

[Microsoft 365 test łączności](https://aka.ms/netonboard)

[Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 blog sieciowy](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
