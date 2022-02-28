---
title: 'Omówienie: rozdzielanie sieci VPN z siecią Office 365'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/22/2020
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
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Wskazówki dotyczące korzystania z rozdzielania sieci VPN z siecią Office 365 w celu zoptymalizowania Office 365 dla użytkowników zdalnych.
ms.openlocfilehash: 09900e1650ee1221d9b9877903a08e18af7154b3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986500"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunneling"></a>Optymalizowanie Office 365 dla użytkowników zdalnych przy użyciu rozdzielania sieci VPN
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunneling for Office 365](microsoft-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](microsoft-365-networking-china.md).
-->

W przypadku klientów łączących urządzenia pracowników zdalnych z siecią firmową lub infrastrukturą chmury przez sieć VPN firma Microsoft zaleca, aby kluczowe scenariusze sieci **Office 365 Microsoft Teams**, **usługi SharePoint Online** i **sieci Exchange Online** są kierowane za pośrednictwem konfiguracji podziału sieci _VPN_. Staje się to szczególnie ważne jako pierwsza strategia mająca na celu zwiększenie produktywności pracowników podczas dużych wydarzeń typu praca od domu, takich jak kryzys współautorów-19.

![Podziel Tunnel konfigurację sieci VPN.](../media/vpn-split-tunneling/vpn-model-2.png)

_Rysunek 1: Rozwiązanie rozdzielane rozdzielane vpn ze zdefiniowanymi Office 365 wysłanymi bezpośrednio do usługi wyjątkami. Cały inny ruch przechodzi przez klienta sieci VPN niezależnie od miejsca docelowego._

Istotą tego podejścia jest zapewnienie prostej metody dla przedsiębiorstw na ograniczenie ryzyka nasycenia infrastruktury sieci VPN oraz znacznie Office 365 wydajności w jak najkrótszym czasie. Skonfigurowanie klientów SIECI VPN w celu umożliwienia największego, największego Office 365 ruchu w celu obejścia obwodu VPN przynosi następujące korzyści:

- Natychmiast ogranicza główną przyczynę większości zgłoszonych przez klientów problemów z wydajnością i wydajnością sieci w architekturach VPN w przedsiębiorstwie, które wpływają Office 365 użytkowników
  
  Zalecane rozwiązanie jest przeznaczone konkretnie do Office 365 punktów końcowych usługi kategoryzowanych **jako Optymalizuj** w temacie Office 365 [URL i zakresów adresów IP](./urls-and-ip-address-ranges.md). Ruch do tych punktów końcowych jest bardzo poufny na ograniczanie opóźnień i przepustowości, a włączenie go w celu obejścia obwodu sieci VPN może znacznie poprawić środowisko użytkownika końcowego oraz zmniejszyć firmowe obciążenie sieci. Office 365 połączeń, które nie stanowią większości przepustowości lub miejsca zajmowanego przez użytkownika, mogą być nadal kierowane przez klienta sieci VPN wraz z resztą ruchu związanego z Internetem. Aby uzyskać więcej informacji, zobacz [Strategię podziału na vpn](#the-vpn-split-tunnel-strategy).

- Mogą być szybko konfigurowane, testowane i implementowane przez klientów bez dodatkowych wymagań dotyczących infrastruktury i aplikacji

  W zależności od platformy VPN i architektury sieci implementacja może potrwać nawet kilka godzin. Aby uzyskać więcej informacji, zobacz [Implementowanie podziału sieci VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Zachowuje bezpieczeństwo implementacji klienta VPN, nie zmieniając sposobu rozsyłania innych połączeń, w tym ruchu do Internetu.

  Zalecana konfiguracja jest zgodna  z zasadą jak najmniejszych uprawnień dla wyjątków związanych z ruchem VPN i pozwala klientom zaimplementować rozdzielony vpn bez narażenia użytkowników lub infrastruktury na dodatkowe zagrożenia bezpieczeństwa. Ruch sieciowy przekierowywowany bezpośrednio do punktów końcowych usługi Office 365 jest szyfrowany, sprawdzany pod względem integralności przez stos Office y aplikacji klienckich i ograniczony do adresów IP dedykowanych usługom Office 365, które są odwłaszczane zarówno na poziomie aplikacji, jak i sieci. Aby uzyskać więcej informacji, zobacz Alternatywne metody dla informatyków dotyczące zabezpieczeń, aby zapewnić nowoczesne mechanizmy kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy [Microsoft).](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

- Jest natywnie obsługiwany przez większość platform VPN przedsiębiorstwa

  Firma Microsoft nadal współpracuje z partnerami branżowymi, którzy współpracują z komercyjnymi rozwiązaniami VPN, aby pomóc partnerom w zakresie opracowywania ukierunkowanych wskazówek i szablonów konfiguracji na ich rozwiązaniach zgodnie z powyższymi zaleceniami. Aby uzyskać więcej informacji, zobacz [Przewodniki HOWTO dotyczące popularnych platform VPN](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Firma Microsoft zaleca skoncentrowanie się na konfiguracji sieci VPN z rozdzielanym rozdzielanym połączeniami w celu obsługi udokumentowanych zakresów adresów IP dla Office 365 sieci. Konfiguracje podziałów poczty oparte na witrynie FQDN lub na podstawie appID (możliwe jednak na niektórych platformach klienckich VPN) mogą nie obejmować w pełni kluczowych scenariuszy Office 365 i mogą powodować konflikty z regułami routingu VPN opartymi na protokółach IP. Z tego powodu firma Microsoft nie zaleca używania tych Office 365 FQNS do konfigurowania sieci VPN z podzielonymi połączeniami sieci vpn. Używanie konfiguracji FQDN może być przydatne w innych powiązanych scenariuszach, takich jak dostosowania pliku pac lub zaimplementowanie obejścia serwera proxy.

Aby uzyskać pełne wskazówki dotyczące implementacji, [zobacz Implementowanie rozdzielania sieci VPN dla sieci Office 365](microsoft-365-vpn-implement-split-tunnel.md).

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania usługi Microsoft 365 pracowników zdalnych, zobacz Konfigurowanie infrastruktury [do pracy zdalnej.](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>Strategia podziału na ekranie sieci VPN

Tradycyjne sieci firmowe są często zaprojektowane tak, aby pracować bezpiecznie w świecie przed chmurą, w którym najważniejsze dane, usługi i aplikacje są hostowane lokalnie i są bezpośrednio połączone z wewnętrzną siecią firmową, w której większość użytkowników jest ich większość. Dzięki temu infrastruktura sieciowa została zbudowana wokół tych elementów w tych oddziałach firmy i jest połączona z oddziałami firmy za pośrednictwem sieci _MPLS (Multiprotocol Label Switching_ ), a użytkownicy zdalni muszą łączyć się z siecią firmową przez sieć VPN, aby mieć dostęp zarówno do lokalnych punktów końcowych, jak i Do Internetu. W tym modelu cały ruch od użytkowników zdalnych przechodzi przez sieć firmową i jest przekierowyny do usługi w chmurze przez wspólny punkt ruchu wychodzącego.

![Wymuszona konfiguracja sieci VPN.](../media/vpn-split-tunneling/vpn-model-1.png)

_Rysunek 2. Typowe rozwiązanie sieci VPN dla użytkowników zdalnych, w przypadku których cały ruch jest wymuszany z powrotem w sieci firmowej niezależnie od miejsca docelowego_

W związku z przenoszeniem danych i aplikacji do chmury w organizacjach ten model stał się coraz mniej efektywny, ponieważ szybko staje się on kłopotliwy, kosztowny i nieocalalny, znacząco wpływa na wydajność sieci i wydajność użytkowników oraz ogranicza możliwości organizacji w zakresie dostosowywania się do zmieniających się potrzeb. Wielu klientów firmy Microsoft zgłosiło, że kilka lat temu 80% ruchu sieciowego było do lokalizacji wewnętrznej, ale w 2020 roku 80% więcej ruchu łączy się z zewnętrznym zasobem opartym na chmurze.

W przypadku kryzysu w zakresie współużytkowania 19 ten problem został zaostrzony w celu wymagania natychmiastowych rozwiązań dla zdecydowanej większości organizacji. Wielu klientów uznało, że model wymuszonego połączenia VPN nie jest skalowalny ani wystarczająco elastyczny w przypadku 100% scenariuszy pracy zdalnej, takich jak sytuacje, których wymaga ten kryzys. Aby te organizacje nadal działały wydajnie, wymagane są szybkie rozwiązania.

W przypadku usługi Office 365 firma Microsoft zaprojektowała wymagania dotyczące łączności dla usługi, mając na uwadze ten problem, gdzie skoncentrowany, ściśle kontrolowany i stosunkowo statyczny zestaw punktów końcowych usługi można zoptymalizować bardzo prosto i szybko, aby zapewnić użytkownikom dostęp do usługi o wysokiej wydajności i zmniejszyć obciążenie związane z infrastrukturą sieci VPN, aby można było z niego korzystać przez ruch, który nadal jej wymaga.

Office 365 punkty końcowe wymagane do Office 365 w trzech kategoriach: **Optimize** (Optymalizuj), **Allow** (Zezwalaj) i **Default (Domyślne**). **W** tym miejscu koncentrują się na nas punkty końcowe optymalizowania, które mają następujące cechy:

- Czy punkty końcowe będące własnością firmy Microsoft i zarządzane są hostowane w infrastrukturze firmy Microsoft
- Są przeznaczone do obsługi podstawowych Office 365, takich jak Exchange Online, SharePoint Online, Skype dla firm Online i Microsoft Teams
- Czy zostały podane ip
- Niskie tempo zmiany i powinny pozostać małe (obecnie jest to 20 podsieci IP)
- Są wrażliwe na duże wolumeny i (lub) opóźnienia
- Mogą mieć wymagane elementy zabezpieczeń udostępniane w usłudze, a nie w tekście w sieci.
- Uwzględnianie około 70–80% ruchu do usługi Office 365 sieci

Ten ściśle ograniczony zestaw punktów końcowych można podzielić z wymuszanym szyfrowaniem VPN oraz bezpiecznie i bezpośrednio do usługi Office 365 za pośrednictwem interfejsu lokalnego użytkownika. Takie podziały **są nazywane rozdzielaniem**.

Elementy zabezpieczeń, takie jak DLP, ochrona audio/wideo, uwierzytelnianie i kontrola dostępu, mogą być dostarczane o wiele wydajniej na tych punktach końcowych na różnych warstwach w ramach usługi. W związku z tym, że od przekierowywają one również ruch zbiorczy z rozwiązania VPN, pozwala to uwolnić pojemność sieci VPN dla krytycznego ruchu biznesowego, który nadal od niego korzysta. To powinno również w wielu przypadkach usunąć konieczność obsługi długiego i kosztownych programów uaktualniania w celu obsługi tego nowego sposobu działania.

![Podziel Tunnel szczegółów konfiguracji sieci VPN.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Rysunek 3: Rozwiązanie rozdzielane rozdzielane vpn ze zdefiniowanymi Office 365 wysłanymi bezpośrednio do usługi wyjątkami. Każdy inny ruch jest wymuszany z powrotem do sieci firmowej, niezależnie od miejsca docelowego._

Z perspektywy zabezpieczeń firma Microsoft oferuje szereg funkcji zabezpieczeń, których można używać w celu zapewnienia podobnych lub nawet ulepszonych zabezpieczeń niż te dostarczane przez inspekcję w tekście przy pomocy lokalnych stosów zabezpieczeń. Wpis w blogu Zespół zabezpieczeń firmy Microsoft w blogu Alternatywne metody dla specjalistów bezpieczeństwa i [informatyków](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) dotyczące nowoczesnego sterowania zabezpieczeniami w dzisiejszych unikatowych scenariuszach pracy zdalnej mają jasne podsumowanie dostępnych funkcji, a bardziej szczegółowe wskazówki znajdziesz w tym artykule. Możesz również przeczytać o wdrożeniu sieci VPN przez firmę Microsoft w te sposób: Uruchamianie w sieci VPN: W jaki sposób firma Microsoft łączy się ze swoimi pracownikami [zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

W wielu przypadkach można zrealizować tę implementację w ciągu kilku godzin, dzięki czemu możliwe jest szybkie rozwiązanie jednego z najbardziej pilnych problemów, z którymi muszą się zmierzyć organizacje w przypadku szybkiego przejścia na pełną skalę pracy zdalnej. Aby uzyskać wskazówki dotyczące implementacji podziału sieci VPN, zobacz [Implementowanie rozdzielania sieci VPN dla sieci Office 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="related-topics"></a>Tematy pokrewne

[Implementowanie rozdzielania sieci VPN na Office 365](microsoft-365-vpn-implement-split-tunnel.md)

[Office 365 wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Office 365 zasad łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocena Office 365 sieci](assessing-network-connectivity.md)

[Microsoft 365 test łączności](https://aka.ms/netonboard)