---
title: Omówienie łączności sieciowej Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Omówiono, dlaczego optymalizacja sieci jest ważna dla usług SaaS, cel Microsoft 365 sieci oraz jak usługa SaaS wymaga innej sieci niż inne obciążenia.
ms.openlocfilehash: 64af558653ff57e91068d2e028235b73c165376b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096771"
---
# <a name="microsoft-365-network-connectivity-overview"></a>omówienie łączności sieciowej Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 to rozproszona chmura typu oprogramowanie jako usługa (SaaS), która zapewnia scenariusze produktywności i współpracy za pośrednictwem zróżnicowanego zestawu mikrousługow i aplikacji. Składniki klienckie Microsoft 365, takie jak Outlook, Word i PowerPoint działają na komputerach użytkowników i łączą się z innymi składnikami Microsoft 365 uruchomionymi w centrach danych firmy Microsoft. Najważniejszym czynnikiem, który określa jakość środowiska Microsoft 365 użytkownika końcowego, jest niezawodność sieci i małe opóźnienia między klientami Microsoft 365 i Microsoft 365 drzwiami frontowymi usługi.

W tym artykule dowiesz się więcej na temat celów sieci Microsoft 365 i tego, dlaczego sieć Microsoft 365 wymaga innego podejścia do optymalizacji niż ogólny ruch internetowy.

## <a name="microsoft-365-networking-goals"></a>cele sieciowe Microsoft 365

Ostatecznym celem Microsoft 365 sieci jest zoptymalizowanie środowiska użytkownika końcowego przez włączenie najmniej restrykcyjnego dostępu między klientami a najbliższymi punktami końcowymi Microsoft 365. Jakość środowiska użytkownika końcowego jest bezpośrednio związana z wydajnością i czasem odpowiedzi aplikacji, z których korzysta użytkownik. Na przykład Microsoft Teams opiera się na małych opóźnieniach, dzięki czemu połączenia telefoniczne użytkownika, konferencje i współpraca na ekranie udostępnionym są wolne od błędów, a Outlook opiera się na doskonałej łączności sieciowej dla funkcji wyszukiwania błyskawicznego, które stosują indeksowanie po stronie serwera i możliwości sztucznej inteligencji.

Głównym celem projektu sieci powinno być zminimalizowanie opóźnienia przez skrócenie czasu rundy (RTT) z maszyn klienckich do sieci globalnej firmy Microsoft, sieci publicznej sieci szkieletowej firmy Microsoft, która łączy wszystkie centra danych firmy Microsoft z małymi opóźnieniami i punktami wejścia aplikacji w chmurze o wysokiej dostępności rozsianymi po całym świecie. Więcej informacji na temat globalnej sieci firmy Microsoft można znaleźć w artykułach [How Microsoft builds its fast and reliable global network (Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)).

Optymalizacja Microsoft 365 wydajności sieci nie musi być skomplikowana. Możesz uzyskać najlepszą możliwą wydajność, postępjąc zgodnie z kilkoma kluczowymi zasadami:

- Identyfikowanie ruchu sieci Microsoft 365
- Zezwalaj na ruch lokalny gałęzi Microsoft 365 ruchu sieciowego do Internetu z każdej lokalizacji, w której użytkownicy łączą się z Microsoft 365
- Zezwalanie ruchowi Microsoft 365 na pomijanie serwerów proxy i urządzeń inspekcji pakietów

Aby uzyskać więcej informacji na temat Microsoft 365 zasad łączności sieciowej, zobacz [Microsoft 365 Zasady łączności sieciowej](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Tradycyjne architektury sieci i SaaS

Tradycyjne zasady architektury sieci dla obciążeń klientów/serwerów są zaprojektowane przy założeniu, że ruch między klientami a punktami końcowymi nie rozciąga się poza obwód sieci firmowej. Ponadto w wielu sieciach przedsiębiorstwa wszystkie wychodzące połączenia internetowe przechodzą przez sieć firmową i wychodzące z centralnej lokalizacji.

W tradycyjnych architekturach sieci większe opóźnienia dla ogólnego ruchu internetowego są niezbędnym kompromisem w celu utrzymania zabezpieczeń obwodowych sieci, a optymalizacja wydajności ruchu internetowego zwykle wiąże się z uaktualnianiem lub skalowaniem sprzętu w punktach ruchu wychodzącego sieci. Takie podejście nie spełnia jednak wymagań dotyczących optymalnej wydajności sieci usług SaaS, takich jak Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identyfikowanie ruchu sieci Microsoft 365

Ułatwiamy identyfikowanie Microsoft 365 ruchu sieciowego i ułatwiamy zarządzanie identyfikacją sieci.

- Nowe kategorie punktów końcowych sieci w celu odróżnienia bardzo krytycznego ruchu sieciowego od ruchu sieciowego, na który nie mają wpływu opóźnienia internetowe. Istnieje tylko kilka adresów URL i obsługujących adresy IP w najbardziej krytycznej kategorii "Optymalizuj".
- Usługi sieci Web na potrzeby użycia skryptów lub bezpośredniej konfiguracji urządzeń oraz zarządzania zmianami Microsoft 365 identyfikacji sieci. Zmiany są dostępne w usłudze internetowej, w formacie RSS lub w wiadomości e-mail przy użyciu szablonu Microsoft Flow.
- [Office 365 program partnerski sieci](./microsoft-365-networking-partner-program.md) z partnerami firmy Microsoft, którzy udostępniają urządzenia lub usługi zgodne Microsoft 365 zasadami łączności sieciowej i mają prostą konfigurację.

## <a name="securing-microsoft-365-connections"></a>Zabezpieczanie połączeń Microsoft 365

Celem tradycyjnych zabezpieczeń sieci jest wzmocnienie obwodu sieci firmowej przed nieautoryzowanym dostępem i złośliwymi lukami w zabezpieczeniach. Większość sieci przedsiębiorstwa wymusza zabezpieczenia sieci dla ruchu internetowego przy użyciu technologii, takich jak serwery proxy, zapory, podział I inspekcja protokołu SSL, głęboka inspekcja pakietów i systemy zapobiegania utracie danych. Technologie te zapewniają istotne ograniczenie ryzyka dla ogólnych żądań internetowych, ale mogą znacznie zmniejszyć wydajność, skalowalność i jakość środowiska użytkownika końcowego, gdy są stosowane do Microsoft 365 punktów końcowych.

Microsoft 365 pomaga spełnić wymagania organizacji dotyczące zabezpieczeń zawartości i zgodności użycia danych dzięki wbudowanym funkcjom zabezpieczeń i ładu zaprojektowanym specjalnie dla Microsoft 365 funkcji i obciążeń. Aby uzyskać więcej informacji na temat Microsoft 365 zabezpieczeń i zgodności, zobacz [plan zabezpieczeń Office 365](/office365/securitycompliance/security-roadmap). Aby uzyskać więcej informacji na temat zaleceń firmy Microsoft i stanowiska pomocy technicznej w zakresie zaawansowanych rozwiązań sieciowych, które wykonują przetwarzanie na poziomie zaawansowanym w ruchu Microsoft 365, zobacz [Korzystanie z urządzeń sieciowych innych firm lub rozwiązań w ruchu Office 365](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Dlaczego sieć Microsoft 365 jest inna?

Microsoft 365 została zaprojektowana pod kątem optymalnej wydajności przy użyciu zabezpieczeń punktów końcowych i szyfrowanych połączeń sieciowych, co zmniejsza potrzebę wymuszania zabezpieczeń obwodowych. Microsoft 365 centra danych znajdują się na całym świecie, a usługa jest przeznaczona do korzystania z różnych metod łączenia klientów z najlepszymi dostępnymi punktami końcowymi usługi. Ponieważ dane użytkownika i przetwarzanie są dystrybuowane między wieloma centrami danych firmy Microsoft, nie ma pojedynczego punktu końcowego sieci, z którym maszyny klienckie mogą się łączyć. W rzeczywistości dane i usługi w dzierżawie Microsoft 365 są dynamicznie optymalizowane przez globalną sieć firmy Microsoft w celu dostosowania ich do lokalizacji geograficznych, z których są uzyskiwane przez użytkowników końcowych.

Niektóre typowe problemy z wydajnością są tworzone, gdy ruch Microsoft 365 podlega inspekcji pakietów i scentralizowanego ruchu wychodzącego:

- Duże opóźnienie może powodować niską wydajność strumieni wideo i audio oraz powolną reakcję na pobieranie danych, wyszukiwanie, współpracę w czasie rzeczywistym, informacje o wolnych/zajętych kalendarzach, zawartość w produkcie i inne usługi
- Połączenia wychodzące z centralnej lokalizacji pokonują dynamiczne możliwości routingu Microsoft 365 sieci globalnej, dodając opóźnienie i czas rundy
- Odszyfrowywanie zabezpieczonego protokołem SSL Microsoft 365 ruchu sieciowego i ponowne szyfrowanie go może powodować błędy protokołu i stwarzać zagrożenie bezpieczeństwa

Skrócenie ścieżki sieciowej do Microsoft 365 punktów wejścia dzięki umożliwieniu ruchu klienta do ruchu wychodzącego jak najbliżej ich lokalizacji geograficznej może zwiększyć wydajność łączności i środowisko użytkownika końcowego w Microsoft 365. Może również pomóc zmniejszyć wpływ przyszłych zmian w architekturze sieci na wydajność i niezawodność Microsoft 365. Optymalnym modelem łączności jest zawsze zapewnienie ruchu wychodzącego sieci w lokalizacji użytkownika, niezależnie od tego, czy jest to sieć firmowa, czy zdalne lokalizacje, takie jak dom, hotele, kawiarnie i lotniska. Ogólny ruch internetowy i ruch sieci firmowy oparty na sieci WAN będą oddzielnie kierowane i nie będą używać lokalnego modelu bezpośredniego ruchu wychodzącego. Ten lokalny model bezpośredniego ruchu wychodzącego jest reprezentowany na poniższym diagramie.

![Architektura lokalnej sieci wychodzącej.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Architektura lokalnego ruchu wychodzącego zapewnia następujące korzyści w przypadku Microsoft 365 ruchu sieciowego w tradycyjnym modelu:
  
- Zapewnia optymalną wydajność Microsoft 365 przez optymalizowanie długości trasy. Połączenia użytkowników końcowych są dynamicznie kierowane do najbliższego punktu wejścia Microsoft 365 przez infrastrukturę usługi _Front Door usługi rozproszonej_ firmy Microsoft Global Network, a ruch jest następnie kierowany wewnętrznie do punktów końcowych danych i usług za pośrednictwem światłowodu o wysokiej dostępności firmy Microsoft o bardzo małych opóźnieniach.
- Zmniejsza obciążenie infrastruktury sieci firmowej, zezwalając lokalnemu ruchowi wychodzącemu na ruch Microsoft 365, pomijając serwery proxy i urządzenia inspekcji ruchu.
- Zabezpiecza połączenia na obu końcach, stosując zabezpieczenia punktu końcowego klienta i funkcje zabezpieczeń w chmurze, unikając stosowania nadmiarowych technologii zabezpieczeń sieci.

> [!NOTE]
> Infrastruktura _usługi Distributed Service Front Door_ to wysoce dostępna i skalowalna krawędź sieci firmy Microsoft z geograficznie rozproszonymi lokalizacjami. Przerywa ona połączenia użytkowników końcowych i efektywnie kieruje je w ramach globalnej sieci firmy Microsoft. Więcej informacji na temat globalnej sieci firmy Microsoft można znaleźć w artykułach [How Microsoft builds its fast and reliable global network (Jak firma Microsoft tworzy swoją szybką i niezawodną sieć globalną](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)).

Aby uzyskać więcej informacji na temat zrozumienia i stosowania zasad łączności sieciowej Microsoft 365, zobacz [Microsoft 365 Zasady łączności sieciowej](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Wniosku

Optymalizacja Microsoft 365 wydajności sieci naprawdę sprowadza się do usunięcia niepotrzebnych przeszkód. Traktując połączenia Microsoft 365 jako ruch zaufany, można zapobiec wprowadzeniu opóźnienia przez inspekcję pakietów i konkurencję o przepustowość serwera proxy. Zezwolenie na połączenia lokalne między maszynami klienckimi i punktami końcowymi Office 365 umożliwia dynamiczne kierowanie ruchu przez globalną sieć firmy Microsoft.

## <a name="related-topics"></a>Tematy pokrewne

[zasady łączności sieciowej Microsoft 365](microsoft-365-network-connectivity-principles.md)

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
