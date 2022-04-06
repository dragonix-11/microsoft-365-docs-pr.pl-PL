---
title: Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN
ms.openlocfilehash: 0f16ed8f7f9721a79375f05f7b889bc8aab2d824
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704940"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji Microsoft 365 zdalnych.

>- Aby uzyskać omówienie korzystania z rozdzielania dzielonego sieci VPN w celu zoptymalizowania Microsoft 365 dla użytkowników zdalnych, zobacz Omówienie: rozdzielanie sieci VPN dla sieci [Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółowe wskazówki dotyczące implementowania rozdzielania sieci VPN, zobacz [Implementowanie](microsoft-365-vpn-implement-split-tunnel.md) rozdzielania sieci VPN na Microsoft 365.
>- Aby uzyskać szczegółową listę scenariuszy rozdzielania rozdzielania sieci VPN, zobacz Typowe scenariusze rozdzielania sieci [VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać informacje na temat konfigurowania usługi Stream i zdarzeń na żywo w środowiskach VPN, zobacz Szczególne zagadnienia dotyczące przesyłania strumieniowego i wydarzeń na żywo w [środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Aby uzyskać informacje na temat optymalizowania Microsoft 365 wydajności dzierżawy na całym świecie dla użytkowników w Chinach, zobacz Microsoft 365 [optymalizację wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

Niektórzy Microsoft Teams mogą wymagać szczegółowych informacji na temat sposobu przepływów połączeń w programie Teams korzystania z modelu rozdzielania rozdzielaowego i sposobu zabezpieczania połączeń.

## <a name="configuration"></a>Konfiguracja

Zarówno w przypadku połączeń, jak i spotkań, o ile wymagane podsieci IP Optymalizowanie podsieci IP dla multimediów Teams są poprawnie na miejscu w tabeli trasy, Teams wywołuje funkcję [Get Przełęczy](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) w celu określenia, który interfejs lokalny powinien odpowiadać trasom, które ma być kierowane do określonego miejsca docelowego, interfejs lokalny zostanie zwrócony dla miejsc docelowych firmy Microsoft w podanych powyżej blokach ADRESÓW IP firmy Microsoft.

Niektóre oprogramowanie klienckie VPN zezwala na manipulowanie routingiem na podstawie adresu URL. Jednak ruch Teams nie jest skojarzony z adresem URL, więc kontrolę nad routingiem dla tego ruchu należy wykonać przy użyciu podsieci IP.

W niektórych scenariuszach, często niezwiązanych z konfiguracją Teams klienta, ruch multimedialny nadal przechodzi przez katalog VPN, nawet gdy są prawidłowe trasy. Jeśli wystąpi ten scenariusz, należy użyć reguły zapory w celu zablokowania Teams IP lub portów z używania sieci VPN.

>[!IMPORTANT]
>Aby zapewnić, Teams ruch multimedialny jest kierowane przy użyciu odpowiedniej metody we wszystkich scenariuszach sieci VPN, upewnij się, że użytkownicy Microsoft Teams mają wersję klienta **1.3.00.13565** lub nowszą. Ta wersja zawiera ulepszenia dotyczące wykrywania dostępnych ścieżek sieciowych przez klienta.

Ruch sygnałowy jest wykonywany przez protokół HTTPS i nie jest tak opóźniony, jak ruch multimedialny, i jest oznaczony  jako Zezwalaj w danych adresu URL/IP, przez co w razie potrzeby można bezpiecznie przekierować ruch przez klienta VPN.

>[!NOTE]
>Microsoft Edge **96 i więcej** obsługuje również podzielenie sieci VPN na ruch w komunikacji równorzędnej. Oznacza to, że klienci mogą zyskać korzyści z rozdzielania sieci VPN na Teams klientów sieci Web w przeglądarce Edge. Klienci, którzy chcą skonfigurować go dla witryn internetowych uruchomionych w przeglądarce Edge, mogą osiągnąć ten cel, umożliwiając włączenie zasad [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Bezpieczeństwo

Jednym z typowych argumentów na unikanie podziałów na rozdzielanie jest to, że jest mniej bezpieczny, np. Żaden ruch, który nie przechodzi przez klienta VPN, nie będzie korzystać z jakiegokolwiek schematu szyfrowania stosowanego do szyfrowania vpn, przez co będzie mniej bezpieczny.

Głównym argumentem licznika jest to, że ruch multimedialny jest już zaszyfrowany za pośrednictwem protokołu _Secure Real-Time Transport Protocol (SRTP_) — profilu protokołu Real-Time Transport Protocol (RTP), który zapewnia poufność, uwierzytelnianie i ponowne odtwarzanie ochrony przed atakami do ruchu WTP. Sam SRTP korzysta z losowo wygenerowanego klucza sesji, który jest wymieniany za pośrednictwem zabezpieczonego kanału sygnałowego TLS. Ten temat szczegółowo opisano w tym [przewodniku zabezpieczeń](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), ale podstawową sekcją zainteresowań jest szyfrowanie multimediów.

Ruch multimedialny jest szyfrowany przy użyciu srTP, który korzysta z klucza sesji wygenerowanego przez bezpieczny generator liczb losowych i wymieniany przy użyciu kanału sygnałowego TLS. Ponadto multimedia przepływujące w obu kierunkach między serwerem pośrednicowym i jego wewnętrznym następnym przeskokiem są również szyfrowane przy użyciu SRTP.

Skype dla firm Online generuje nazwę użytkownika/hasła w celu zapewnienia bezpiecznego dostępu do przekazywania multimediów przez _portal Traversal przy użyciu przekazywania dookoła NAT (TURN)._ Przekazywanie multimediów wymienia nazwę użytkownika/hasło za pośrednictwem kanału SIP zabezpieczonego za pomocą protokołu TLS. Warto zauważyć, że nawet jeśli w celu połączenia klienta z siecią firmową może zostać użyty vpn, ruch nadal musi przepływać w formularzu SRTP, gdy opuszcza sieć firmową, aby połączyć się z usługą.

Informacje o tym, Teams ogranicza typowe zagrożenia związane z zabezpieczeniami, takie jak ataki funkcji komunikacji głosowej lub przechodzenia przez narzędzia do przechodzenia przez sesję _nat (STUN),_ można znaleźć w tece [5.1](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c) Zagadnienia związane z zabezpieczeniami dotyczące implementerów.

O nowoczesnych mechanizmach kontroli zabezpieczeń w scenariuszach pracy zdalnej można również przeczytać w artykule Alternatywne sposoby dla informatyków i informatyków dotyczące osiągnięcia nowoczesnych kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy [Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Testowanie

Gdy zasady będą działać, upewnij się, że działają zgodnie z oczekiwaniami. Istnieje wiele sposobów testowania ścieżki, która jest poprawnie ustawiona do korzystania z lokalnego połączenia internetowego:

- Uruchom test [Microsoft 365,](https://aka.ms/netonboard) który spowoduje uruchomienie testów łączności, w tym śledzenia tras, jak powspomniano powyżej. Dodaliśmy także do tego narzędzia testy sieci VPN, które powinno również dostarczyć dodatkowych informacji.

- Prosta ścieżka **śledzenia do** punktu końcowego, który znajduje się w zakresie podziału, powinna pokazywać ścieżkę przebytą, na przykład:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Następnie powinna być zobaczysz ścieżkę tego punktu końcowego za pośrednictwem lokalnego internetowego punktu końcowego, która powinna rozpoznać adres IP z zakresów Teams, które skonfigurowaliśmy do rozdzielania rozdzielania.

- Przechwyć sieć za pomocą narzędzia takiego jak Wireshark. Filtruj według protokołu UDP podczas połączenia. W zakresie optymalizowania powinien być wyświetlony ruch o przepływie do **Teams IP.** Jeśli dla tego ruchu jest używany szyfrowanie sieci VPN, ruch multimedialny nie będzie widoczny w wynikach śledzenia.

## <a name="additional-support-logs"></a>Dodatkowe dzienniki pomocy technicznej

Jeśli potrzebujesz dodatkowych danych do rozwiązania lub jeśli potrzebujesz pomocy technicznej firmy Microsoft, uzyskanie poniższych informacji powinno przyspieszyć znalezienie rozwiązania. Uniwersalny zestaw narzędzi Do rozwiązywania problemów opartych na **Windows CMD** pomocy technicznej firmy Microsoft może ułatwić zbieranie odpowiednich dzienników w prosty sposób. Narzędzie i instrukcje dotyczące używania można znaleźć na stronie <https://aka.ms/TssTools>.

## <a name="related-articles"></a>Artykuły pokrewne

[Omówienie: rozdzielanie sieci VPN na Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementowanie rozdzielania sieci VPN na Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Typowe scenariusze rozdzielania sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md)

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
