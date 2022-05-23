---
title: Microsoft 365 globalnej optymalizacji wydajności dzierżawy dla użytkowników z Chin
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: Ten artykuł zawiera wskazówki dotyczące optymalizacji wydajności sieci dla chińskich użytkowników globalnych dzierżaw Microsoft 365.
ms.openlocfilehash: f7e4e69277a252fd1af52559d3bc4360fd3cfd51
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637874"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 globalnej optymalizacji wydajności dzierżawy dla użytkowników z Chin

> [!IMPORTANT]
> Te wskazówki są specyficzne dla scenariuszy użycia, w których **użytkownicy Microsoft 365 przedsiębiorstwa znajdujący się w Chinach** łączą się z **globalną dzierżawą Microsoft 365**. Te wskazówki **nie** mają zastosowania do dzierżaw w Office 365 obsługiwanych przez firmę 21Vianet.

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów, które dotyczą optymalizacji Microsoft 365 dla użytkowników zdalnych.

>- Aby zapoznać się z omówieniem korzystania z tunelowania podzielonego sieci VPN w celu optymalizacji łączności Microsoft 365 dla użytkowników zdalnych, zobacz [Omówienie tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółowe wskazówki dotyczące implementowania tunelowania podzielonego sieci VPN, zobacz [Implementowanie tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Aby uzyskać szczegółową listę scenariuszy tunelowania podzielonego sieci VPN, zobacz [Typowe scenariusze tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać wskazówki dotyczące zabezpieczania ruchu Teams multimediów w środowiskach tunelowania podzielonego sieci VPN, zobacz [Zabezpieczanie ruchu Teams multimediów na potrzeby tunelowania podzielonego sieci VPN](microsoft-365-vpn-securing-teams.md).
>- Aby uzyskać informacje o sposobie konfigurowania strumienia i zdarzeń na żywo w środowiskach sieci VPN, zobacz [Specjalne zagadnienia dotyczące strumienia i zdarzeń na żywo w środowiskach sieci VPN](microsoft-365-vpn-stream-and-live-events.md).

W przypadku przedsiębiorstw z globalnymi dzierżawami Microsoft 365 i obecnością firmy w Chinach Microsoft 365 wydajność klientów dla użytkowników z Chin może być skomplikowana przez czynniki unikatowe dla architektury internetowej Firmy China Telco.

Dostawcy usług internetowych z Chin regulowali połączenia offshore z globalnym publicznym Internetem, które przechodzą przez urządzenia obwodowe, które są podatne na wysoki poziom transgranicznych zatorów sieciowych. To przeciążenie powoduje utratę pakietów i opóźnienie dla całego ruchu internetowego do i z Chin.

![Microsoft 365 ruch — niezoptymalizowany.](../media/O365-networking/China-O365-unoptimized.png)

Utrata pakietów i opóźnienie są szkodliwe dla wydajności usług sieciowych, zwłaszcza usług, które wymagają dużych wymian danych (takich jak duże transfery plików) lub wymagają wydajności niemal w czasie rzeczywistym (aplikacje audio i wideo).

Celem tego tematu jest zapewnienie najlepszych rozwiązań w zakresie łagodzenia wpływu przeciążenia sieci transgranicznej w Chinach na usługi Microsoft 365. W tym temacie nie rozwiązano innych typowych problemów z wydajnością ostatniej mili, takich jak problemy z dużym opóźnieniem pakietów z powodu złożonego routingu w chińskich przewoźnikach.

## <a name="corporate-network-best-practices"></a>Najlepsze rozwiązania dotyczące sieci firmowej

Wiele przedsiębiorstw z globalnymi dzierżawami Microsoft 365 i użytkownikami w Chinach wdrożyło sieci prywatne, które obsługują ruch sieciowy firmowy między lokalizacjami biur w Chinach a lokalizacjami na morzu na całym świecie. Przedsiębiorstwa te mogą korzystać z tej infrastruktury sieciowej, aby uniknąć przeciążenia sieci transgranicznej i zoptymalizować wydajność usług Microsoft 365 w Chinach.

> [!IMPORTANT]
> Podobnie jak w przypadku wszystkich prywatnych implementacji sieci WAN, zawsze należy zapoznać się z wymaganiami prawnymi dotyczącymi kraju i/lub regionu, aby upewnić się, że konfiguracja sieci jest zgodna.

W pierwszym kroku ważne jest, aby postępować zgodnie z naszymi wytycznymi dotyczącymi sieci testów porównawczych w sekcji [Planowanie sieci i dostrajanie wydajności dla Microsoft 365](./network-planning-and-performance.md). Głównym celem powinno być uniknięcie dostępu do globalnych usług Microsoft 365 z Internetu w Chinach, jeśli to możliwe.

- Wykorzystaj istniejącą sieć prywatną do przenoszenia ruchu sieciowego Microsoft 365 między chińskimi sieciami biurowymi a lokalizacjami offshore wychodzącymi w publicznym Internecie poza Chinami. Prawie każda lokalizacja poza Chinami zapewni wyraźną korzyść. Administratorzy sieci mogą jeszcze bardziej zoptymalizować ruch wychodzący w obszarach o małych opóźnieniach łączących się z [siecią globalną firmy Microsoft](/azure/networking/microsoft-global-network). Przykładem są Hongkong, Singapur, Japonia i Korea Południowa.
- Skonfiguruj urządzenia użytkowników, aby uzyskiwać dostęp do sieci firmowej za pośrednictwem połączenia sieci VPN, aby umożliwić Microsoft 365 ruchu do przesyłania prywatnego połączenia offshore sieci firmowej. Upewnij się, że klienci sieci VPN nie są skonfigurowani do używania tunelowania podzielonego lub że urządzenia użytkowników są skonfigurowane do ignorowania tunelowania podzielonego dla ruchu Microsoft 365. Aby uzyskać dodatkowe informacje na temat optymalizowania łączności sieci VPN pod kątem Teams i ruchu multimediów w czasie rzeczywistym, zobacz [tę sekcję](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Skonfiguruj sieć tak, aby kierowała cały ruch Microsoft 365 przez prywatne połączenie offshore. Jeśli musisz zminimalizować ilość ruchu w linku prywatnym, możesz wybrać tylko kierowanie punktów końcowych w kategorii **Optymalizuj** i zezwolić na przesyłanie przez Internet żądań **zezwalania** na przesyłanie przez Internet domyślnych punktów końcowych i **domyślnych** . Zwiększy to wydajność i zminimalizuje zużycie przepustowości przez ograniczenie zoptymalizowanego ruchu do usług krytycznych, które są najbardziej wrażliwe na duże opóźnienia i utratę pakietów.
- Jeśli to możliwe, użyj protokołu UDP zamiast protokołu TCP dla ruchu strumieniowego multimediów na żywo, na przykład w przypadku Teams. Protokół UDP oferuje lepszą wydajność transmisji strumieniowej multimediów na żywo niż TCP.

Aby uzyskać informacje o tym, jak selektywnie kierować ruch Microsoft 365, zobacz [Zarządzanie punktami końcowymi Office 365](managing-office-365-endpoints.md). Aby uzyskać listę wszystkich adresów URL i IP Office 365 na całym świecie, zobacz [Office 365 adresy URL i zakresy adresów IP](urls-and-ip-address-ranges.md).

![Microsoft 365 ruch — zoptymalizowany.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Najlepsze rozwiązania dotyczące użytkowników

Użytkownicy w Chinach, którzy łączą się z globalnymi dzierżawami Microsoft 365 z odległych lokalizacji, takich jak domy, kawiarnie, hotele i oddziały bez połączenia z sieciami przedsiębiorstw, mogą doświadczyć niskiej wydajności sieci, ponieważ ruch między ich urządzeniami a Microsoft 365 musi przechodzić przez zatłoczone obwody sieciowe w Chinach.

Jeśli transgraniczne sieci prywatne i/lub dostęp sieci VPN do sieci firmowej nie są dostępne, problemy z wydajnością poszczególnych użytkowników nadal można rozwiązać, szkoląc użytkowników z Chin, aby postępowali zgodnie z tymi najlepszymi rozwiązaniami.

- Korzystaj z bogatych klientów Office obsługujących buforowanie (np. Outlook, Teams, OneDrive itp.) i unikaj klientów internetowych. Office funkcje buforowania klientów i dostępu w trybie offline mogą znacznie zmniejszyć wpływ przeciążenia i opóźnienia sieci.
- Jeśli dzierżawa Microsoft 365 została skonfigurowana przy użyciu funkcji _Konferencje głosowe_, użytkownicy Teams mogą dołączać do spotkań za pośrednictwem publicznej przełączanej sieci telefonicznej (PSTN). Aby uzyskać więcej informacji, zobacz [Konferencje głosowe w Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Jeśli użytkownicy mają problemy z wydajnością sieci, powinni zgłosić się do swojego działu IT w celu rozwiązywania problemów i eskalować do pomocy technicznej firmy Microsoft, jeśli podejrzewa się problemy z usługami Microsoft 365. Nie wszystkie problemy są spowodowane przez wydajność sieci transgranicznej.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Optymalizowanie wydajności sieci spotkań Microsoft Teams dla użytkowników w Chinach

W przypadku organizacji z globalną dzierżawą Microsoft 365 i obecnością w Chinach wydajność klienta Microsoft 365 dla użytkowników z Chin może być skomplikowana przez czynniki unikatowe dla chińskiej architektury internetowej. Wiele firm i szkół zgłosiło dobre wyniki, postępjąc zgodnie z tymi wskazówkami. Zakres ten jest jednak ograniczony do lokalizacji sieci użytkowników, które są pod kontrolą konfiguracji sieci IT, na przykład lokalizacji biurowych lub domowych/mobilnych punktów końcowych z łącznością sieci VPN. Microsoft Teams połączenia i spotkania są często używane z zewnętrznych lokalizacji, takich jak biura domowe, lokalizacje mobilne, w drodze i kawiarnie. Ponieważ połączenia i spotkania opierają się na ruchu multimedialnym w czasie rzeczywistym, te środowiska Teams są szczególnie wrażliwe na przeciążenie sieci.

W związku z tym firma Microsoft nawiązała współpracę z dostawcami usług telekomunikacyjnych w celu przenoszenia ruchu multimedialnego Teams i Skype dla firm Online w czasie rzeczywistym przy użyciu wyższej jakości, preferencyjnej ścieżki sieciowej między krajowymi i publicznymi połączeniami internetowymi w Chinach oraz usługami Teams i Skype w chmurze globalnej Microsoft 365. Ta funkcja doprowadziła do ponad dziesięciokrotnej poprawy utraty pakietów i innych kluczowych metryk wpływających na środowisko użytkownika.

>[!IMPORTANT]
>Obecnie te ulepszenia nie dotyczą uczestniczenia w spotkaniach z wydarzeniami na żywo firmy Microsoft, takich jak spotkania w stylu dużych transmisji lub ratusza przy użyciu Teams lub Microsoft Stream. Ulepszenia sieci będą korzystne dla użytkowników prezentujących lub tworzących spotkania zdarzeń na żywo, ponieważ to środowisko działa jako regularne spotkanie Teams dla producenta lub prezentera.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Najlepsze rozwiązania dotyczące sieci organizacji dotyczące spotkań Teams

Należy rozważyć sposób wykorzystania tych ulepszeń sieci, biorąc pod uwagę, że w poprzednich wskazówkach rozważysz rozszerzenie sieci prywatnej, aby uniknąć przeciążenia sieci transgranicznej. Istnieją dwie ogólne opcje sieci biurowych organizacji:

1. Nie rób nic nowego. Postępuj zgodnie z wcześniejszymi wskazówkami dotyczącymi obejścia sieci prywatnej, aby uniknąć zatorów transgranicznych. Teams ruch multimedialny w czasie rzeczywistym będzie korzystać z tej konfiguracji, jak poprzednio.
2. Zaimplementuj wzorzec podziału/hybrydowego.
   - Skorzystaj z poprzednich wskazówek dotyczących całego ruchu oflagowanego w celu optymalizacji, z wyjątkiem spotkań Teams i wywoływania ruchu multimedialnego w czasie rzeczywistym.
   - Kierowanie Teams spotkania i wywoływanie ruchu medialnego w czasie rzeczywistym przez publiczny Internet. Zapoznaj się z poniższymi informacjami, aby uzyskać szczegółowe informacje na temat identyfikowania ruchu sieciowego multimediów w czasie rzeczywistym.

Wysyłanie Teams ruchu audio i wideo w czasie rzeczywistym za pośrednictwem publicznego Internetu, który korzysta z łączności wyższej jakości, może spowodować znaczne oszczędności, ponieważ wysyłanie tego ruchu przez sieć prywatną jest bezpłatne, a nie płatne. Mogą istnieć podobne dodatkowe korzyści, jeśli użytkownicy korzystają również z sieci SDWAN lub klientów sieci VPN. Niektóre organizacje mogą również preferować, aby więcej danych przechodziło przez publiczne połączenia internetowe jako ogólną praktykę.

Te same opcje mogą dotyczyć konfiguracji SDWAN lub VPN. Na przykład użytkownik używa sieci SDWAN lub VPN do kierowania ruchu Microsoft 365 do sieci firmowej, a następnie korzysta z prywatnego rozszerzenia tej sieci, aby uniknąć przeciążenia transgranicznego. Sieć SDWAN lub SIEĆ VPN użytkownika można teraz skonfigurować tak, aby wykluczała Teams spotkania i wywoływania ruchu w czasie rzeczywistym z routingu sieci VPN. Ta konfiguracja sieci VPN jest określana jako tunelowanie podzielone. Aby uzyskać więcej informacji, zobacz [Tunelowanie podzielone sieci VPN, aby uzyskać Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel).

Możesz również nadal używać sieci SDWAN lub VPN dla całego ruchu Microsoft 365, w tym dla ruchu Microsoft Teams w czasie rzeczywistym. Firma Microsoft nie ma żadnych zaleceń dotyczących korzystania z rozwiązań SDWAN lub VPN.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Najlepsze rozwiązania dotyczące sieci domowej, mobilnej i użytkownika dotyczące spotkań Teams

Użytkownicy w Chinach mogą korzystać z tych ulepszeń po prostu łącząc się z publiczną usługą internetową w Chinach za pomocą połączenia stacjonarnego lub mobilnego. Teams ruch audio i wideo w czasie rzeczywistym w publicznym Internecie bezpośrednio korzysta z ulepszonej łączności i jakości.

Jednak dane z innych usług Microsoft 365 i innego ruchu w Teams, takich jak czat lub pliki, nie będą bezpośrednio korzystać z tych ulepszeń. Użytkownicy spoza sieci organizacji mogą nadal doświadczać niskiej wydajności sieci dla tego ruchu. Jak opisano w tym artykule, można wyeliminować te skutki przy użyciu sieci VPN lub SDWAN. Użytkownicy mogą również używać bogatych klientów klasycznych za pośrednictwem klientów internetowych, którzy obsługują buforowanie w aplikacji w celu rozwiązania problemów z siecią.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Identyfikowanie Teams ruchu sieciowego multimediów w czasie rzeczywistym

Aby skonfigurować urządzenie sieciowe lub konfigurację sieci VPN/SDWAN, należy wykluczyć tylko Teams ruchu audio i wideo multimediów w czasie rzeczywistym. Szczegóły ruchu można znaleźć dla identyfikatora 11 na oficjalnej liście [adresów URL Office 365 i zakresów adresów IP](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Wszystkie inne konfiguracje sieci powinny pozostać w niezmienionej postaci.

Firma Microsoft nieustannie pracuje nad poprawą Microsoft 365 środowiska użytkownika i wydajności klientów w zakresie możliwie najszerszego zakresu architektur i cech sieciowych. Odwiedź [Office 365 Networking Tech Community](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking), aby rozpocząć lub dołączyć do konwersacji, znaleźć zasoby oraz przesłać żądania i sugestie dotyczące funkcji

## <a name="related-articles"></a>Powiązane artykuły:

[Omówienie: tunelowanie podzielone sieci VPN dla Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementowanie tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Typowe scenariusze tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Zabezpieczanie ruchu multimediów aplikacji Teams na potrzeby tunelowania podziału sieci VPN](microsoft-365-vpn-securing-teams.md)

[Specjalne zagadnienia dotyczące strumienia i wydarzeń na żywo w środowiskach sieci VPN](microsoft-365-vpn-stream-and-live-events.md)

[zasady łączności sieciowej Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Ocena łączności sieciowej na platformie Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)

[Alternatywne sposoby zapewniania przez specjalistów ds. zabezpieczeń i działów IT nowoczesnych mechanizmów kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu ds. zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: używanie Windows 10 profilów sieci VPN do zezwalania na połączenia automatyczne](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Uruchamianie w sieci VPN: jak firma Microsoft utrzymuje połączenie ze swoimi zdalnymi pracownikami](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
