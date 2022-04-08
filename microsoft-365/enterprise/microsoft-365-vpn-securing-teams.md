---
title: Zabezpieczanie ruchu multimediów aplikacji Teams na potrzeby tunelowania podziału sieci VPN
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
description: Zabezpieczanie ruchu multimediów aplikacji Teams na potrzeby tunelowania podziału sieci VPN
ms.openlocfilehash: 715d5e02ef01db9ef1c75a063ef5a2771d425f5c
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715390"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>Zabezpieczanie ruchu multimediów aplikacji Teams na potrzeby tunelowania podziału sieci VPN

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów, które dotyczą optymalizacji Microsoft 365 dla użytkowników zdalnych.

>- Aby zapoznać się z omówieniem korzystania z tunelowania podzielonego sieci VPN w celu optymalizacji łączności Microsoft 365 dla użytkowników zdalnych, zobacz [Omówienie tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółowe wskazówki dotyczące implementowania tunelowania podzielonego sieci VPN, zobacz [Implementowanie tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Aby uzyskać szczegółową listę scenariuszy tunelowania podzielonego sieci VPN, zobacz [Typowe scenariusze tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać informacje o sposobie konfigurowania strumienia i zdarzeń na żywo w środowiskach sieci VPN, zobacz [Specjalne zagadnienia dotyczące strumienia i zdarzeń na żywo w środowiskach sieci VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Aby uzyskać informacje na temat optymalizacji Microsoft 365 ogólnoświatowych wydajności dzierżaw dla użytkowników w Chinach, zobacz [optymalizację wydajności Microsoft 365 dla chińskich użytkowników](microsoft-365-networking-china.md).

Niektórzy administratorzy Microsoft Teams mogą wymagać szczegółowych informacji na temat sposobu działania przepływów wywołań w Teams przy użyciu modelu tunelowania podzielonego i sposobu zabezpieczania połączeń.

## <a name="configuration"></a>Konfiguracja

W przypadku wywołań i spotkań, o ile wymagane podsieci IP optymalizacji dla nośników Teams są poprawnie w miejscu w tabeli tras, gdy Teams wywołuje funkcję [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) w celu określenia, który interfejs lokalny odpowiada trasie, której powinien używać dla określonego miejsca docelowego, interfejs lokalny zostanie zwrócony dla miejsc docelowych firmy Microsoft w blokach adresów IP firmy Microsoft wymienionych powyżej.

Niektóre oprogramowanie klienckie sieci VPN umożliwia manipulowanie routingiem na podstawie adresu URL. Jednak Teams ruch multimediów nie ma z nim skojarzonego adresu URL, dlatego należy kontrolować routing dla tego ruchu przy użyciu podsieci IP.

W niektórych scenariuszach, często niezwiązanych z konfiguracją klienta Teams, ruch multimediów nadal przechodzi przez tunel VPN nawet z odpowiednimi trasami. Jeśli wystąpi ten scenariusz, użycie reguły zapory w celu zablokowania Teams podsieci IP lub portów przy użyciu sieci VPN powinno wystarczyć.

>[!IMPORTANT]
>Aby upewnić się, Teams ruch multimediów jest kierowany za pomocą żądanej metody we wszystkich scenariuszach sieci VPN, upewnij się, że użytkownicy korzystają Microsoft Teams klienta **w wersji 1.3.00.13565 lub nowszej**. Ta wersja obejmuje ulepszenia sposobu wykrywania dostępnych ścieżek sieciowych przez klienta.

Ruch sygnałowy jest wykonywany za pośrednictwem protokołu HTTPS i nie jest tak wrażliwy na opóźnienie jak ruch multimedialny i jest oznaczony jako **Zezwalaj** w danych adresu URL/IP, a tym samym może być bezpiecznie kierowany przez klienta sieci VPN w razie potrzeby.

>[!NOTE]
>Microsoft Edge **96 i nowsze** obsługują również tunelowanie podzielone sieci VPN dla ruchu równorzędnego. Oznacza to, że klienci mogą na przykład uzyskać korzyści z tunelowania podzielonego sieci VPN dla Teams klientów internetowych w przeglądarce Edge. Klienci, którzy chcą skonfigurować ją dla witryn internetowych działających w przeglądarce Edge, mogą to osiągnąć, wykonując dodatkowy krok wyłączania zasad [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) przeglądarki Edge.

### <a name="security"></a>Bezpieczeństwo

Jednym z typowych argumentów unikania dzielenia tuneli jest to, że jest to mniej bezpieczne, tj. Żaden ruch, który nie przechodzi przez tunel VPN, nie będzie korzystać z jakiegokolwiek schematu szyfrowania stosowanego do tunelu SIECI VPN i dlatego jest mniej bezpieczny.

Głównym kontrargumentem jest to, że ruch multimedialny jest już szyfrowany za pośrednictwem _protokołu SRTP (Secure Real-Time Transport Protocol),_ profilu protokołu Real-Time Transport Protocol (RTP), który zapewnia poufność, uwierzytelnianie i ochronę przed atakami odtwarzania dla ruchu RTP. Sam protokół SRTP opiera się na losowo wygenerowanym kluczu sesji, który jest wymieniany za pośrednictwem kanału sygnałowego zabezpieczonego przez protokół TLS. Jest to szczegółowo omówione w [tym przewodniku po zabezpieczeniach](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), ale podstawową interesującą częścią jest szyfrowanie multimediów.

Ruch multimediów jest szyfrowany przy użyciu protokołu SRTP, który używa klucza sesji wygenerowanego przez bezpieczny generator liczb losowych i wymienianego przy użyciu kanału TLS sygnalizacji. Ponadto nośnik przepływający w obu kierunkach między serwerem mediacji a jego wewnętrznym następnym przeskokem jest również szyfrowany przy użyciu protokołu SRTP.

Skype dla firm Online generuje nazwy użytkownika/hasła w celu bezpiecznego dostępu do przekaźników multimediów za _pośrednictwem przekaźników przy użyciu przekaźników wokół translatora adresów sieciowych (TURN)._ Przekaźniki multimediów wymieniają nazwę użytkownika/hasło za pośrednictwem kanału SIP zabezpieczonego przez protokół TLS. Warto zauważyć, że nawet jeśli tunel VPN może być używany do łączenia klienta z siecią firmową, ruch musi nadal przepływać w formularzu SRTP, gdy opuszcza sieć firmową, aby dotrzeć do usługi.

Informacje na temat sposobu, w jaki Teams eliminują typowe problemy z zabezpieczeniami, takie jak ataki wzmacniania połączeń głosowych lub narzędzi przechodzenia sesji na potrzeby ataków wzmacniania translatora adresów sieciowych _(STUN),_ można znaleźć w [artykule 5.1 Zagadnienia dotyczące zabezpieczeń dla implementatorów](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

Możesz również przeczytać o nowoczesnych mechanizmach kontroli zabezpieczeń w scenariuszach pracy zdalnej w artykule [Alternatywne sposoby dla specjalistów ds. zabezpieczeń i działu IT w celu uzyskania nowoczesnych mechanizmów kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu ds. zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Testowania

Po wprowadzeniu zasad należy potwierdzić, że działa zgodnie z oczekiwaniami. Istnieje wiele sposobów testowania ścieżki jest poprawnie ustawiona do korzystania z lokalnego połączenia internetowego:

- Uruchom [test łączności Microsoft 365](https://aka.ms/netonboard), który będzie uruchamiał testy łączności, w tym trasy śledzenia, jak powyżej. Dodajemy również testy sieci VPN do tego narzędzia, które powinno również dostarczyć dodatkowych szczegółowych informacji.

- Prosta **kontrolka tracert** do punktu końcowego w zakresie tunelu podzielonego powinna zawierać pobraną ścieżkę, na przykład:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Następnie powinna zostać wyświetlona ścieżka za pośrednictwem lokalnego usługodawcy sieciowego do tego punktu końcowego, która powinna zostać rozpoznana jako adres IP w zakresach Teams skonfigurowanych do tunelowania podzielonego.

- Wykonaj przechwytywanie sieci przy użyciu narzędzia takiego jak Wireshark. Filtruj według protokołu UDP podczas wywołania i powinien zostać wyświetlony ruch przepływający do adresu IP w zakresie Teams **Optymalizuj**. Jeśli tunel VPN jest używany dla tego ruchu, ruch multimedialny nie będzie widoczny w śladzie.

## <a name="additional-support-logs"></a>Dodatkowe dzienniki pomocy technicznej

Jeśli potrzebujesz dalszych danych do rozwiązywania problemów lub żądasz pomocy od pomocy technicznej firmy Microsoft, uzyskanie poniższych informacji powinno umożliwić przyspieszenie znajdowania rozwiązania. Zestaw **narzędzi TSS Windows oparty na** uniwersalnym zestawie narzędzi Skrypt rozwiązywania problemów firmy Microsoft może pomóc w prosty sposób zebrać odpowiednie dzienniki. Narzędzie i instrukcje dotyczące używania można znaleźć pod adresem <https://aka.ms/TssTools>.

## <a name="related-articles"></a>Artykuły pokrewne

[Omówienie: tunelowanie podzielone sieci VPN dla Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementowanie tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Typowe scenariusze tunelowania podzielonego sieci VPN dla Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Specjalne zagadnienia dotyczące strumienia i wydarzeń na żywo w środowiskach sieci VPN](microsoft-365-vpn-stream-and-live-events.md)

[optymalizacja wydajności Microsoft 365 dla użytkowników z Chin](microsoft-365-networking-china.md)

[zasady łączności sieciowej Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Ocena łączności sieciowej na platformie Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)

[Alternatywne sposoby zapewniania przez specjalistów ds. zabezpieczeń i działów IT nowoczesnych mechanizmów kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu ds. zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: używanie Windows 10 profilów sieci VPN do zezwalania na połączenia automatyczne](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Uruchamianie w sieci VPN: jak firma Microsoft utrzymuje połączenie ze swoimi zdalnymi pracownikami](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
