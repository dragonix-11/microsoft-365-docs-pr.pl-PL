---
title: 'Omówienie: rozdzielanie sieci VPN na Microsoft 365'
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
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Omówienie rozdzielania sieci VPN z siecią Microsoft 365 w celu zoptymalizowania łączności dla użytkowników zdalnych.
ms.openlocfilehash: 67ce8a38b536dab12af679ba860aac6d974db60e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329075"
---
# <a name="overview-vpn-split-tunneling-for-microsoft-365"></a>Omówienie: rozdzielanie sieci VPN na Microsoft 365

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji Microsoft 365 zdalnych.

>- Aby uzyskać szczegółowe wskazówki dotyczące implementowania rozdzielania sieci VPN, zobacz [Implementowanie](microsoft-365-vpn-implement-split-tunnel.md) rozdzielania sieci VPN na Microsoft 365.
>- Aby uzyskać szczegółową listę scenariuszy rozdzielania rozdzielania sieci VPN, zobacz Typowe scenariusze rozdzielania sieci [VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać wskazówki dotyczące zabezpieczania Teams ruchu multimedialnego w środowiskach rozdzielanych sieci VPN, zobacz Zabezpieczanie sieci Teams sieci multimedialnej na Teams [sieci VPN](microsoft-365-vpn-securing-teams.md).
>- Aby uzyskać informacje na temat konfigurowania usługi Stream i zdarzeń na żywo w środowiskach VPN, zobacz Szczególne zagadnienia dotyczące przesyłania strumieniowego i wydarzeń na żywo w [środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Aby uzyskać informacje na temat optymalizowania Microsoft 365 wydajności dzierżawy na całym świecie dla użytkowników w Chinach, zobacz Microsoft 365 [optymalizację wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

Przedsiębiorstwa zazwyczaj używały sieci VPN do obsługi bezpiecznego środowisk zdalnych dla swoich użytkowników. Podczas gdy podstawowe obciążenia pracą pozostaną lokalne, sieć VPN z klienta zdalnego przekierowyowana przez centrum danych w sieci firmowej była podstawową metodą uzyskiwania dostępu do zasobów firmowych przez użytkowników zdalnych. Aby chronić te połączenia, przedsiębiorstwa tworzy warstwy rozwiązań zabezpieczeń sieciowych wzdłuż ścieżek sieci VPN. Te zabezpieczenia zostały stworzone do ochrony infrastruktury wewnętrznej i ochrony przeglądania zewnętrznych witryn sieci Web w trybie przenośnym przez przekierowanie ruchu do sieci VPN, a następnie za pośrednictwem lokalnego obwodu Internetu. Sieci VPN, obwody sieci i skojarzona infrastruktura zabezpieczeń były często celowe i skalowane dla określonego woluminu ruchu — zwykle większość łączności jest inicjowana z sieci firmowej, a większość z nich znajduje się w granicach sieci wewnętrznej.

Przez dość długi czas modele sieci VPN, w których wszystkie połączenia z urządzeń użytkowników zdalnych są kierowane z powrotem do sieci lokalnej (nazywanej wymuszanym redukowaniem _), były_ w dużym stopniu uatywniane, o ile równoczesna skala użytkowników zdalnych była niewielka, a ruch sieci VPN był niewielka.  Niektórzy klienci nadal korzystają z wymuszania sieci VPN na wytyczyniu statusu quo nawet po tym, gdy ich aplikacje przeniesiono z obwodu firmy do publicznych chmur SaaS.

Korzystanie z wymuszonych sieci VPN w celu nawiązywania połączeń z aplikacjami chmurowymi o równomiernej wydajności jest suboptimalnie, ale w niektórych przedsiębiorstwach ich negatywne skutki zostały zaakceptowane w celu zachowania quo stanu zabezpieczeń. Poniżej przedstawiono przykładowy diagram tego scenariusza:

![Wymuszanie Tunnel sieci VPN.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

_Rysunek 1. Tradycyjny system wymuszany Tunnel VPN._

Ten problem rozrastał się od wielu lat, a wielu klientów zgłasza znaczną zmianę wzorców ruchu sieciowego. Ruch, który był używany do pracy w środowisku lokalnym, teraz łączy się z zewnętrznymi punktami końcowymi chmury. Wielu klientów firmy Microsoft zgłaszało wcześniej, że około 80% ich ruchu sieciowego było źródłem wewnętrznym (reprezentowanym przez linię kropkową na powyższym diagramie). W 2020 roku liczba ta zmniejszona o około 20% lub niższa w przypadku zmiany głównych obciążeń do chmury. Te trendy nie są rzadkością w przypadku innych przedsiębiorstw. Z czasem, w związku z postępem podróży w chmurze, powyższy model staje się coraz bardziej uciążliwy i nieusuwalny, uniemożliwiając organizacji adaptacyjną się w momencie przechodzenia do pierwszego świata w chmurze.

Sytuację, w związku z która pojawiła się globalna kryzysowa wer. WSPÓŁDZIEL-19, eskalował ten problem, aby wymagać natychmiastowego rozwiązania naprawczego. Konieczność zapewnienia bezpieczeństwa pracowników wygenerowała wyjątkowe wymagania dotyczące it przedsiębiorstwa w celu zapewnienia wysokiej produktywności w domu na ogromną skalę. Microsoft 365 ma dobre położenie, aby pomóc klientom w realizacji tego wymagania, ale wysoki współbieżność użytkowników pracujących z domu generuje dużą ilość ruchu Microsoft 365, który, jeśli jest przekierowyny przez wymuszone sieci VPN i obwody sieci lokalnej, powoduje szybkie nasycenie i dużą pojemność infrastruktury sieci VPN. W nowej rzeczywistości dostęp przez sieć VPN do sieci Microsoft 365 nie jest już tylko utrudnieniami w wydajności, ale trudnym ścianą, która nie tylko wpływa na usługę Microsoft 365 ale także na krytyczne operacje biznesowe, które nadal muszą polegać na sieci VPN do obsługi.

Firma Microsoft ściśle współpracuje z klientami i szerszą branżą, aby dostarczać skuteczne, nowoczesne rozwiązania tych problemów z poziomu naszych własnych usług i być zgodne z najlepszymi rozwiązaniami branżowymi. [Zasady łączności](./microsoft-365-network-connectivity-principles.md) w usłudze Microsoft 365 zaprojektowano tak, aby wydajnie pracować dla użytkowników zdalnych, jednocześnie pozwalając organizacji na zachowanie zabezpieczeń i kontroli nad ich łącznością. Te rozwiązania można również szybko wdrożyć, mając ograniczoną pracę, ale jednocześnie uzyskać istotne, dodatni wpływ na opisane powyżej problemy.

W przypadku klientów łączących urządzenia pracowników zdalnych z siecią firmową lub infrastrukturą chmury przez sieć VPN firma Microsoft zaleca, aby kluczowe scenariusze sieci **Microsoft Teams Microsoft 365**, usług **SharePoint Online** i **Exchange Online** zostały rozsyłane za pośrednictwem konfiguracji rozdzielanej sieci _VPN_. Staje się to szczególnie ważne jako pierwsza strategia mająca na celu zwiększenie produktywności pracowników podczas dużych wydarzeń typu praca od domu, takich jak kryzys współautorów-19.

![Podziel Tunnel konfigurację sieci VPN.](../media/vpn-split-tunneling/vpn-model-2.png)

_Rysunek 2. Rozwiązanie rozdzielane rozdzielane vpn ze zdefiniowanymi Microsoft 365 wysłanymi bezpośrednio do usługi wyjątkami. Cały inny ruch przechodzi przez klienta sieci VPN niezależnie od miejsca docelowego._

Istotą tego podejścia jest dostarczenie prostej metody dla przedsiębiorstw w celu zmniejszenia ryzyka nasycenia infrastruktury sieci VPN oraz znacznie Microsoft 365 wydajności w jak najmniejszym czasie. Skonfigurowanie klientów SIECI VPN w celu umożliwienia największego, największego Microsoft 365 ruchu w celu obejścia obwodu VPN przynosi następujące korzyści:

- Natychmiast ogranicza główną przyczynę większości zgłoszonych przez klientów problemów z wydajnością i wydajnością sieci w architekturach VPN przedsiębiorstwa wpływających Microsoft 365 użytkowników
  
  Zalecane rozwiązanie jest przeznaczone konkretnie do Microsoft 365 punktów końcowych usługi kategoryzowanych **jako Optymalizuj** w temacie Microsoft 365 [URL i zakresów adresów IP](./urls-and-ip-address-ranges.md). Ruch do tych punktów końcowych jest bardzo poufny na ograniczanie opóźnień i przepustowości, a włączenie go w celu obejścia obwodu sieci VPN może znacznie poprawić środowisko użytkownika końcowego oraz zmniejszyć firmowe obciążenie sieci. Microsoft 365 sieci VPN, które nie stanowią większości przepustowości lub miejsca zajmowanego przez użytkownika, mogą być kierowane przez klienta sieci VPN razem z resztą ruchu związanego z Internetem. Aby uzyskać więcej informacji, zobacz [Strategię podziału na vpn](#the-vpn-split-tunnel-strategy).

- Mogą być szybko konfigurowane, testowane i implementowane przez klientów bez dodatkowych wymagań dotyczących infrastruktury i aplikacji

  W zależności od platformy VPN i architektury sieci implementacja może potrwać nawet kilka godzin. Aby uzyskać więcej informacji, zobacz [Implementowanie podziału sieci VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Zachowuje bezpieczeństwo implementacji klienta VPN, nie zmieniając sposobu rozsyłania innych połączeń, w tym ruchu do Internetu.

  Zalecana konfiguracja jest zgodna  z zasadą jak najmniejszych uprawnień dla wyjątków związanych z ruchem VPN i pozwala klientom zaimplementować rozdzielony vpn bez narażenia użytkowników lub infrastruktury na dodatkowe zagrożenia bezpieczeństwa. Ruch sieciowy przekierowywowany bezpośrednio do punktów końcowych programu Microsoft 365 jest szyfrowany, weryfikowany pod względem integralności przez stos Office y aplikacji klienckich i ograniczony do adresów IP dedykowanych usługom Microsoft 365, które są odwłaszczane zarówno na poziomie aplikacji, jak i sieci. Aby uzyskać więcej informacji, zobacz Alternatywne metody dla informatyków dotyczące zabezpieczeń, aby zapewnić nowoczesne mechanizmy kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy [Microsoft).](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

- Jest natywnie obsługiwany przez większość platform VPN przedsiębiorstwa

  Firma Microsoft nadal współpracuje z partnerami branżowymi, którzy współpracują z komercyjnymi rozwiązaniami VPN, aby pomóc partnerom w zakresie opracowywania ukierunkowanych wskazówek i szablonów konfiguracji na ich rozwiązaniach zgodnie z powyższymi zaleceniami. Aby uzyskać więcej informacji, zobacz [Przewodniki HOWTO dotyczące popularnych platform VPN](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Firma Microsoft zaleca skoncentrowanie się na konfiguracji sieci VPN z rozdzielanym przedziałem w dokumencie dedykowanych zakresów adresów IP dla Microsoft 365 sieci. Konfiguracje rozdzielone na podstawie FQDN lub oparte na appID (możliwe jednak na niektórych platformach klienckich VPN) mogą nie obejmować w pełni kluczowych scenariuszy Microsoft 365 i mogą powodować konflikty z regułami routingu VPN opartymi na protokółach IP. Z tego powodu firma Microsoft nie zaleca używania tych Microsoft 365 FQNS w celu skonfigurowania sieci VPN z rozdzielanym szyfrowaniem. Używanie konfiguracji FQDN może być przydatne w innych powiązanych scenariuszach, takich jak dostosowania pliku pac lub zaimplementowanie obejścia serwera proxy.

Aby uzyskać pełne wskazówki dotyczące implementacji, [zobacz Implementowanie rozdzielania sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania usługi Microsoft 365 pracowników zdalnych, zobacz Konfigurowanie infrastruktury [do pracy zdalnej.](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>Strategia podziału na ekranie sieci VPN

Tradycyjne sieci firmowe są często zaprojektowane tak, aby pracować bezpiecznie w świecie przed chmurą, w którym najważniejsze dane, usługi i aplikacje są hostowane lokalnie i są bezpośrednio połączone z wewnętrzną siecią firmową, w której większość użytkowników jest ich większość. Dzięki temu infrastruktura sieciowa została zbudowana wokół tych elementów w tych oddziałach firmy i jest połączona z oddziałami firmy za pośrednictwem sieci _MPLS (Multiprotocol Label Switching_ ), a użytkownicy zdalni muszą łączyć się z siecią firmową przez sieć VPN, aby mieć dostęp zarówno do lokalnych punktów końcowych, jak i Do Internetu. W tym modelu cały ruch od użytkowników zdalnych przechodzi przez sieć firmową i jest przekierowyny do usługi w chmurze przez wspólny punkt ruchu wychodzącego.

![Wymuszona konfiguracja sieci VPN.](../media/vpn-split-tunneling/vpn-model-1.png)

_Rysunek 2. Typowe rozwiązanie sieci VPN dla użytkowników zdalnych, w przypadku których cały ruch jest wymuszany z powrotem w sieci firmowej niezależnie od miejsca docelowego_

W związku z przenoszeniem danych i aplikacji do chmury w organizacjach ten model stał się coraz mniej efektywny, ponieważ szybko staje się on kłopotliwy, kosztowny i nieocalalny, znacząco wpływa na wydajność sieci i wydajność użytkowników oraz ogranicza możliwości organizacji w zakresie dostosowywania się do zmieniających się potrzeb. Wielu klientów firmy Microsoft zgłosiło, że kilka lat temu 80% ruchu sieciowego było do lokalizacji wewnętrznej, ale w 2020 roku 80% więcej ruchu łączy się z zewnętrznym zasobem opartym na chmurze.

W przypadku kryzysu w zakresie współużytkowania 19 ten problem został zaostrzony w celu wymagania natychmiastowych rozwiązań dla zdecydowanej większości organizacji. Wielu klientów uznało, że model wymuszonego połączenia VPN nie jest skalowalny ani wystarczająco elastyczny w przypadku 100% scenariuszy pracy zdalnej, takich jak sytuacje, których wymaga ten kryzys. Aby te organizacje nadal działały wydajnie, wymagane są szybkie rozwiązania.

W przypadku usługi Microsoft 365 firma Microsoft zaprojektowała wymagania dotyczące łączności dla usługi, mając na uwadze ten problem, gdzie skoncentrowany, ściśle kontrolowany i stosunkowo statyczny zestaw punktów końcowych usługi można zoptymalizować bardzo prosto i szybko, aby zapewnić użytkownikom dostęp do usługi o wysokiej wydajności i zmniejszyć obciążenie związane z infrastrukturą VPN, aby można było używać jej przez ruch, który nadal jej wymaga.

Microsoft 365 punkty końcowe wymagane do Microsoft 365 w trzech kategoriach: **Optimize** (Optymalizuj), **Allow** (Zezwalaj) i **Default (Domyślne**). **W** tym miejscu koncentrują się na nas punkty końcowe optymalizowania, które mają następujące cechy:

- Czy punkty końcowe będące własnością firmy Microsoft i zarządzane są hostowane w infrastrukturze firmy Microsoft
- Są przeznaczone do obsługi podstawowych Microsoft 365, takich jak Exchange Online, SharePoint Online, Skype dla firm Online i Microsoft Teams
- Czy zostały podane ip
- Niskie tempo zmiany i powinny pozostać małe (obecnie jest to 20 podsieci IP)
- Są wrażliwe na duże wolumeny i (lub) opóźnienia
- Mogą mieć wymagane elementy zabezpieczeń udostępniane w usłudze, a nie w tekście w sieci.
- Uwzględnianie około 70–80% ruchu do usługi Microsoft 365 sieci

Ten ściśle ograniczony zestaw punktów końcowych można podzielić z wymuszanym szyfrowaniem VPN i przesyłać je bezpiecznie i bezpośrednio do usługi Microsoft 365 za pośrednictwem interfejsu lokalnego użytkownika. Takie podziały **są nazywane rozdzielaniem**.

Elementy zabezpieczeń, takie jak DLP, ochrona audio/wideo, uwierzytelnianie i kontrola dostępu, mogą być dostarczane o wiele wydajniej na tych punktach końcowych na różnych warstwach w ramach usługi. W związku z tym, że od przekierowywają one również ruch zbiorczy z rozwiązania VPN, pozwala to uwolnić pojemność sieci VPN dla krytycznego ruchu biznesowego, który nadal od niego korzysta. To powinno również w wielu przypadkach usunąć konieczność obsługi długiego i kosztownych programów uaktualniania w celu obsługi tego nowego sposobu działania.

![Podziel Tunnel szczegółów konfiguracji sieci VPN.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Rysunek 3. Rozwiązanie rozdzielane rozdzielane vpn ze zdefiniowanymi Microsoft 365 i wyjątkami wysyłanymi bezpośrednio do usługi. Każdy inny ruch jest wymuszany z powrotem do sieci firmowej, niezależnie od miejsca docelowego._

Z perspektywy zabezpieczeń firma Microsoft oferuje szereg funkcji zabezpieczeń, których można używać w celu zapewnienia podobnych lub nawet ulepszonych zabezpieczeń niż te dostarczane przez inspekcję w tekście przy pomocy lokalnych stosów zabezpieczeń. Wpis w blogu Zespół zabezpieczeń firmy Microsoft w blogu Alternatywne metody dla specjalistów bezpieczeństwa i [informatyków](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) dotyczące nowoczesnego sterowania zabezpieczeniami w dzisiejszych unikatowych scenariuszach pracy zdalnej mają jasne podsumowanie dostępnych funkcji, a bardziej szczegółowe wskazówki znajdziesz w tym artykule. Możesz również przeczytać o wdrożeniu sieci VPN przez firmę Microsoft w te sposób: Uruchamianie w sieci VPN: W jaki sposób firma Microsoft łączy się ze swoimi pracownikami [zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

W wielu przypadkach można zrealizować tę implementację w ciągu kilku godzin, dzięki czemu możliwe jest szybkie rozwiązanie jednego z najbardziej pilnych problemów, z którymi muszą się zmierzyć organizacje w przypadku szybkiego przejścia na pełną skalę pracy zdalnej. Aby uzyskać wskazówki dotyczące implementacji podziału sieci VPN, zobacz [Implementowanie podziału sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="faq"></a>Często zadawane pytania

Zespół zabezpieczeń firmy Microsoft opublikował alternatywne sposoby dla specjalistów bezpieczeństwa i [it](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) na uzyskanie nowoczesnych kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej ( wpis w blogu, w który przedstawiono kluczowe sposoby dla specjalistów bezpieczeństwa i it może zapewnić nowoczesne mechanizmy kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej). Ponadto poniżej przedstawiono niektóre często zadawane przez klientów pytania i odpowiedzi na ten temat.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Jak zatrzymać użytkownikom dostęp do innych dzierżaw, którym nie ufam, gdzie mogą oni eksfiltrować dane?

Odpowiedzią jest funkcja [o nazwie ograniczenia dzierżawy](/azure/active-directory/manage-apps/tenant-restrictions). Ruch uwierzytelniania nie jest duży ani nie jest szczególnie poufny dla opóźnień, więc może być przesyłany za pośrednictwem rozwiązania VPN do lokalnego serwera proxy, do którego ta funkcja została zastosowana. W tym miejscu jest zachowywana lista zaufanych dzierżaw i jeśli klient próbuje uzyskać token do dzierżawy, która nie jest zaufana, serwer proxy po prostu odrzuca żądanie. Jeśli dzierżawa jest zaufana, token jest dostępny, jeśli użytkownik ma odpowiednie poświadczenia i prawa.

Dlatego mimo że użytkownik może nawiązaniu połączenia TCP/UDP z powyższymi oznaczonymi punktami końcowymi optymalizowania, bez prawidłowego tokenu na potrzeby uzyskiwania dostępu do danych dzierżawy, po prostu nie może się zalogować ani uzyskać dostępu do żadnych danych ani ich przenosić.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Czy ten model umożliwia dostęp do usług dla klientów osobistych, takich jak osobiste OneDrive konta?

Nie, punkty końcowe usługi Microsoft 365 nie są takie same jak usługi dla klientów konsumenckich (na przykład Onedrive.live.com), więc rozdzielany nie zezwala użytkownikowi na bezpośredni dostęp do usług dla klientów konsumenckich. Ruch do punktów końcowych klientów będzie nadal korzystać z ruchu VPN i istniejące zasady będą nadal obowiązywać.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Jak stosować zasady DLP i chronić poufne dane, gdy ruch nie przepływa już za pośrednictwem rozwiązania lokalnego?

Aby zapobiec przypadkowemu ujawnianiu informacji poufnych, Microsoft 365 ma bogaty zestaw wbudowanych [narzędzi](../compliance/information-protection.md). Możesz użyć wbudowanych funkcji [DLP aplikacji Teams](../compliance/dlp-learn-about-dlp.md) i SharePoint w celu wykrywania niestosownie przechowywanych lub udostępnionych informacji poufnych. Jeśli część strategii dotyczącej pracy zdalnej obejmuje zasady bring-your-own-device (BYOD), możesz użyć opartego [](/azure/active-directory/conditional-access/app-based-conditional-access) na aplikacji dostępu warunkowego, aby zapobiec pobieraniu poufnych danych na osobiste urządzenia użytkowników.

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Jak oceniać uwierzytelnianie użytkownika i utrzymywać kontrolę nad jego uwierzytelnianiem podczas bezpośredniego nawiązywania połączenia?

Oprócz funkcji ograniczeń dzierżawy zanotowane w K1 [, można](/azure/active-directory/conditional-access/overview) zastosować zasady dostępu warunkowego w celu dynamicznej oceny ryzyka związanego z żądaniem uwierzytelniania i odpowiedniego reagowania. Firma Microsoft zaleca, aby [model Zero](https://www.microsoft.com/security/zero-trust?rtc=1) zaufania był implementowany z czasem i można używać zasad dostępu warunkowego usługi Azure AD w celu utrzymania kontroli w świecie przenośnym i w chmurze. Za pomocą zasad dostępu warunkowego można podjąć decyzję o pomyślnym uwierzytelnieniu w czasie rzeczywistym na podstawie wielu czynników, takich jak:

- Czy urządzenie jest przyłączone do nazwy/zaufanej/domeny?
- IP — czy żądanie uwierzytelnienia pochodzi ze znanego firmowego adresu IP? A może w kraju, do którym nie ufamy?
- Aplikacja — czy użytkownik jest autoryzowany do korzystania z tej aplikacji?

Następnie możemy uruchomić zasady, takie jak zatwierdzanie, wyzwalanie uwierzytelniania MFA lub blokowanie uwierzytelniania na podstawie tych zasad.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Jak chronić się przed wirusami i złośliwym oprogramowaniem?

Również ten Microsoft 365 zapewnia ochronę oznaczonych punktów końcowych Optymalizowanie na różnych warstwach samej usługi, opisanych [w tym dokumencie](/office365/Enterprise/office-365-malware-and-ransomware-protection). Jak wspomniano, znacznie skuteczniej jest dostarczać te elementy zabezpieczeń w samej usłudze, niż próbować robić to zgodnie z urządzeniami, które mogą nie w pełni rozumiać protokołów/ruchu. Domyślnie aplikacja SharePoint Online automatycznie [skanuje przekazywanie](../security/office-365-security/virus-detection-in-spo.md) plików w poszukiwaniu znanego złośliwego oprogramowania

W przypadku Exchange punktów końcowych wymienionych powyżej program [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) i [program Microsoft Defender dla systemu Microsoft 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) to doskonałe rozwiązanie do zapewniania bezpieczeństwa ruchu do usługi.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Czy mogę wysyłać nie tylko bezpośrednią optymalizację ruchu?

Priorytet powinien być nadany punktom końcowym oznaczonym jako **Optymalizuj** , ponieważ zapewni to maksymalną korzyść w przypadku niskiego poziomu pracy. Jednak w razie potrzeby do działania usługi wymagane są oznaczone punkty końcowe ze oznaczonymi adresami IP, które mogą być używane w razie potrzeby.

Istnieją również różni dostawcy, którzy oferują oparte na chmurze rozwiązania proxy/zabezpieczeń nazywane bezpiecznymi bramami sieci _Web_ , które zapewniają centralne zabezpieczenia, kontrolki i aplikację zasad firmy do ogólnego przeglądania Internetu. Te rozwiązania mogą działać dobrze w pierwszym świecie chmury, jeśli są wysoce dostępne, performantowe i zapewniane w pobliżu użytkowników, pozwalając na bezpieczny dostęp do Internetu z lokalizacji opartej na chmurze, blisko użytkownika. Dzięki temu nie będzie konieczne korzystanie ze spinki sieci VPN/firmowej do ogólnego ruchu przeglądania, a jednocześnie pozwoli na centralne sterowanie zabezpieczeniami.

Jednak nawet w przypadku tych rozwiązań firma Microsoft nadal zdecydowanie zaleca, aby optymalizować oznaczony Microsoft 365 jest wysyłany bezpośrednio do usługi.

Aby uzyskać wskazówki dotyczące zezwalania na bezpośredni dostęp do wirtualnej sieci Azure, zobacz Praca zdalna przy użyciu bezpośredniej witryny bramy [Azure VPN](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Dlaczego jest wymagany port 80? Czy ruch jest wysyłany w czytelny sposób?

Port 80 jest używany tylko do takich czynności, jak przekierowanie do sesji portu 443, żadne dane klienta nie są wysyłane ani nie są dostępne za pośrednictwem portu 80. [Szyfrowanie](../compliance/encryption.md) określa szyfrowanie danych podczas przesyłania i przechowywania danych dla sieci Microsoft 365, a typy ruchu są [](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) konspektami sposobu, w jaki używamy portali SRTP do Teams ruchu multimedialnego.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Czy ta porada dotyczy użytkowników w Chinach korzystających z globalnego wystąpienia Microsoft 365?

**Nie**, nie musi. Jedną z zastrzeżeniem powyższych porad są użytkownicy w ChRL, którzy naają połączenie z całym wystąpieniem Microsoft 365. Ze względu na typowe występowanie przeciążenia sieci przygranej w regionie wydajność bezpośredniego ruchu wychodzącego do Internetu może być zmienna. Większość klientów w regionie korzysta z połączenia VPN w celu przybliżania ruchu do sieci firmowej i korzysta z autoryzowanego obwodu MPLS lub podobnego do ruchu wychodzącego poza kraj za pośrednictwem zoptymalizowanej ścieżki. Opisano to dalej w artykule [Microsoft 365 optymalizacji wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>Czy konfiguracja z podziałem na Teams działa w przeglądarce?

Tak, z zastrzeżeniem. Większość Teams jest obsługiwana w przeglądarkach wymienionych w te [sposób: Pobierz klientów dla Microsoft Teams](/microsoftteams/get-clients#web-client).

Ponadto sieć Microsoft Edge **96** i więcej obsługuje rozdzielanie sieci VPN na ruch w komunikacji równorzędnej, włączając zasady [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled). Obecnie inne przeglądarki mogą nie obsługiwać rozdzielania sieci VPN dla ruchu równorzędnego.

## <a name="related-articles"></a>Artykuły pokrewne

[Implementowanie rozdzielania sieci VPN na Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Typowe scenariusze rozdzielania sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN](microsoft-365-vpn-securing-teams.md)

[Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md)

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
