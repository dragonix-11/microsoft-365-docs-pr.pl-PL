---
title: Microsoft 365 Enterprise zasobów — architektura owości
description: Dowiedz się, jak przezwyciężać wyzwania związane z zabezpieczeniami w architekturze Enterprise firmy Microsoft, Kozeta Tomasz, architectity w firmie Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: c580b6529a3467a08befdb07c1b0b8d516208183
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005239"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>Bez przeszkód na bezpieczeństwo można wypłynąć — widok jednego z architektów

W tym artykule [Kozeta Kaleta, Architectity](https://www.linkedin.com/in/kozeta-garrett-53013a6/) Architect w firmie Microsoft, opisuje najważniejsze wyzwania związane z zabezpieczeniami, jakie napotkała w przedsiębiorstwach, i zaleca metody wytyczania tych przeszkody.

## <a name="about-the-author"></a>Informacje o autorze

![Fotografia Kozeta Kosmachta.](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

Jako architekt zabezpieczeń w chmurze pracowałem z wieloma organizacjami nad zapewnieniem wskazówek strategicznych i technicznych, skupiając się na projektowaniu i wdrażaniu architektury zabezpieczeń dla klientów migrowania do usług Microsoft 365 i Azure, opracowywania rozwiązań zabezpieczeń przedsiębiorstwa i pomaganiu w przekształcaniu architektury i kultury zabezpieczeń na potrzeby odporności firmy. Moje środowisko obejmuje wykrywanie zdarzeń i reagowanie, analizę złośliwego oprogramowania, testy pensji i zalecanie ulepszeń w zakresie zabezpieczeń i obrony IT. Bardzo pasjonują mnie wiodące przekształcenia, których efektem jest włączenie zabezpieczeń w biznesie, w tym przez działania na rzecz unowocześnienia.

Organizacja, która przyjęły pomysł unowocześnienia zabezpieczeń w ciągu kilku ostatnich lat, była dla nich najbardziej satysfakcjonującą sytuacją, umożliwiającą kontynuowanie bezpiecznej pracy zdalnej, mimo niedawnej sytuacji w zakresie współużytkowania-19. Niestety, w tych okolicznościach niektórzy klienci nie byli na bieżąco z tą natychmiastową potrzebą. Wiele organizacji wie, że muszą błyskawicznie unowocześnić swoje zakumulowane zabezpieczenia IT i ulepszyć swoje zabezpieczenia w nocy, aby działały w tych niezwykle nietypowych okolicznościach.

Dobra wiadomość jest taka, że firma Microsoft przekazała pewne doskonałe zasoby, aby pomóc organizacjom w szybkiej organizacji w pielęgnacji zabezpieczeń. Oprócz tych zasobów chcę podzielić się z klientami swoimi codziennymi wyzwaniami w nadzieję, że będzie można popłynąć przez te przeszkody.

Obecnie mieszkam w Virginii Północnej, blisko stolicy naszego kraju, Waszyngton DC. Lubię niemal wszystkie formy aktywności na zewnątrz i ćwiczeń, takie jak bieganie, wędrować, wędrować i popływać. Aby licznik tych produktów mi się podobał, takich jak gotowanie, wykwintne jedzenie i podróże.

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>Współpraca z zespołem zabezpieczeń od początku wdrożenia w chmurze

Nie mogę na początku podkreślić, jak ważne jest, aby zespoły w Twojej organizacji koordynowały od początku. Zespoły zabezpieczeń muszą być na wczesnych etapach wdrożenia i projektowania chmury jako krytycznych partnerów. Oznacza to wprowadzenie zespołów ds. zabezpieczeń, aby zwiększyć wykorzystanie chmury, nie tylko w celu zapewnienia dodatkowych możliwości biznesowych (na przykład doskonałego środowiska użytkownika z bezpiecznych urządzeń przenośnych, aplikacji w pełni funkcjonalnych lub tworzenia wartości na danych firmowych poza ograniczoną funkcjonalnością poczty e-mail i aplikacji zwiększających produktywność), ale także wykorzystanie możliwości przechowywania danych, AI i analizy informatycznej, które pomagają rozwiązywać nowe i stare wyzwania związane z zabezpieczeniami. Aby można było skutecznie zarządzać wszystkimi aspektami tej zmiany, łącznie z osobami (kultura), procesami (szkoleniami) i technologiami, należy je uwzględniać w zarządzaniu wszystkimi aspektami tej zmiany. Oznacza to również inwestycje w unowocześnienie i ciągłe ulepszanie Centrum operacji zabezpieczeń (SOC). Współpracując ze sobą, dopasuj strategię zabezpieczeń do strategii biznesowej i trendów środowiska, aby zapewnić bezpieczne przekształcanie cyfrowe. Gdy to się nie stanie, organizacje mogą szybciej dostosowywać się do zmian, w tym do zmian w firmie, it i zabezpieczeniach.

Widzę, że klienci podróżują przez przeszkody, najczęściej w sytuacji, gdy nie istnieje rzeczywiste partnerstwo między operacjami a zespołami SOC. W związku z natłoku nacisków i planowania przez zespół operacyjny wąskich terminów przyjęcia chmury zespoły bezpieczeństwa nie zawsze są wcześnie uwzględniane w procesie w celu przeglądu i zaplanowania kompleksowej strategii zabezpieczeń. Obejmuje to integrowanie różnych składników chmury i składników w pre-prem. Ten brak współpracy dodatkowo prowadzi do tego, że różne zespoły wydają się działać w silosach w celu wdrożenia kontroli nad ich określonymi składnikami, co prowadzi do złożoności wdrożenia, rozwiązywania problemów i integracji.

Klienci, którzy wypłyną przez te przeszkody, mają dobre powiązywki między zespołami Operacje i zarządzanie a zespołami ds. bezpieczeństwa i zarządzania ryzykiem w celu przeoowania strategii zabezpieczeń i wymagań dotyczących ochrony hybrydowych obciążeń chmury. Koncentrują się laserowo na ostatecznych celach i wynikach w zakresie zabezpieczeń — dostępności systemów i systemów danych zgodnie z wymogami bezpieczeństwa bezpieczeństwa, ryzyka i zgodności. Te organizacje opracują relacje na wczesnym etapie między zespołem operacji i zarządzania a SOC, które mają kluczowe znaczenie dla projektu zabezpieczeń i maksymalizują wartość inwestycji.

## <a name="build-a-modern-identity-based-security-perimeter"></a>Tworzenie nowoczesnego obwodu zabezpieczeń (opartego na tożsamości)

Następnie zastosuj podejście do architektury zerowego zaufania. Na początek jest budowania nowoczesnego obwodu zabezpieczeń opartego na tożsamości. Zaprojektuj architekturę zabezpieczeń, w której każda próba dostępu, zarówno w stanie prem, jak i w chmurze, będzie traktowana jako niezaufana do czasu jej zweryfikowania — "nigdy nie ufaj, zawsze to weryfikowaj". Takie podejście projektowe nie tylko zwiększa bezpieczeństwo i produktywność, ale także umożliwia użytkownikom pracę z dowolnego miejsca przy użyciu dowolnego typu urządzenia. Zaawansowane kontrolki chmury Microsoft 365 chronią tożsamości użytkowników, a jednocześnie ułatwiają kontrolowanie dostępu do cennych zasobów w oparciu o poziom ryzyka użytkownika.

Aby uzyskać informacje o zalecanej konfiguracji, zobacz [Konfiguracje tożsamości i dostępu do urządzenia](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="transition-security-controls-to-the-cloud"></a>Przejście kontroli zabezpieczeń do chmury

Wiele zespołów ds. zabezpieczeń nadal korzysta z tradycyjnych najlepszych rozwiązań bezpieczeństwa, które zostały stworzone dla wszystkich rozwiązań lokalnych, takich jak utrzymywanie "zabezpieczeń obwodu sieci" i "wymuszanie" lokalnych narzędzi zabezpieczeń i kontrolek na rozwiązaniach w chmurze. Takie mechanizmy kontroli nie zaprojektowano dla chmury, są nieefektywne i utrudniają wdrożenie nowoczesnych możliwości chmury. Procesy i narzędzia, które działają w przypadku podejścia do zabezpieczeń obwodu sieci, okazało się nieefektywne, zasłaniające możliwości chmury i nie umożliwiają korzystania z nowoczesnych i automatycznych funkcji zabezpieczeń.

Możesz wypłynąć przez tę przeszkodę, przesuwając strategie obrony na ochronę zarządzaną w chmurze, automatyczne badania i rozwiązywanie problemów, automatyczne testowanie pióra, usługę Defender dla Office 365 i analizę zdarzeń. Klienci korzystający z nowoczesnych rozwiązań do zarządzania urządzeniami zaimplementowali automatyczne zarządzanie, ustowalizowane poprawki, oprogramowanie antywirusowe, wymuszanie zasad i ochronę aplikacji na wszystkich urządzeniach (smartfonie, komputerze osobistym, laptopie lub tablecie). Eliminuje to konieczność obsługi zasad grupy VPN, microsoft System Center Configuration Manager (SCCM) i usługi Active Directory. W połączeniu z zasadami dostępu warunkowego zapewnia to zaawansowaną kontrolę i widoczność, a także usprawniony dostęp do zasobów niezależnie od miejsca działania użytkowników.

## <a name="strive-for-best-together-security-tools"></a>Staraj się starać o "najlepsze razem" narzędzia zabezpieczające

Kolejną przeszkodyą widzę, że klienci natknęli się na "najlepszego rodzaju" podejście do narzędzi zabezpieczeń. Ciągłe nakładanie rozwiązań "najlepszych na rasę" na potrzeby wyłaniających się potrzeb w zakresie zabezpieczeń powoduje przerwy w zabezpieczeniach przedsiębiorstwa. Nawet mając najlepsze zamiary, narzędzia w większości środowisk nie są zintegrowane, ponieważ stają się zbyt kosztowne i złożone. Z kolei to powoduje przerwy w widoczności, ponieważ istnieje więcej alertów do przechyłki, niż zespół może obsłużyć. Ponowne przeszkolenie zespołu secops w nowych narzędziach również staje się stałym wyzwaniem.

Metoda "prostsza jest lepsza" działa również w przypadku zabezpieczeń. Zamiast pojechać po "najlepszych w użyciu" narzędzi, wypłyń po tej przeszkody, przyjętej strategię "najlepiej razem" z narzędziami, które domyślnie współpracują ze sobą. Funkcje zabezpieczeń firmy Microsoft chronią całą organizację za pomocą zintegrowanej ochrony przed zagrożeniami obejmującej aplikacje, użytkowników i chmury. Integracja umożliwia organizacji bardziej odporne na ataki i zmniejszanie ryzyka przez tworzenie atakujących w przypadku ejściu i szybkimi atakami naprawczymi.

## <a name="balance-security-with-functionality"></a>Równoważenie zabezpieczeń z funkcjonalnością

Ponieważ mam długie doświadczenie i doświadczenie, zwykle preferuję rozpoczynając od najbezpieczniejszej konfiguracji, która pozwala organizacjom na relaksunie się konfiguracji zabezpieczeń w zależności od potrzeb operacyjnych i potrzeb w zakresie zabezpieczeń. Może to jednak być za dużo utraconej funkcjonalności i słabego działania użytkownika. Wiele organizacji wie już, że jeśli użytkownicy nie mają zbyt trudnych zabezpieczeń, mogą znaleźć sposób na pracę w pobliżu, w tym korzystanie z nieza zarządzania usługami w chmurze. Tak trudno mi zaakceptować, że muszę zdawać sobie sprawę z tego, że należy równowagi między funkcjami i zabezpieczeniami.

Organizacje, które uznają, że użytkownicy będą robić wszystko, co trzeba, aby wykonać swoje zadania, potwierdzają, że nie warto pochylić się nad "cieniem IT" . Zdajemy sobie sprawę, że pracownicy IT są największymi pozawątkami, jeśli chodzi o aplikację Shadow IT i korzystanie z niezatwierdznych aplikacji SaaS na ich stanowiska. Przeszli oni swoją strategię, aby zachęcić do jej używania (zamiast pomijać) i skupiali się na ograniczanie ryzyka związanego z naświetldaniem. Te zespoły zabezpieczeń organizacji nie wychodziły, że wszystko jest blokowane, rejestrowane i wysyłane za pośrednictwem zwrotnego serwera proxy lub połączenia VPN. Zamiast tego te zespoły bezpieczeństwa podwoiły swoje wysiłki, aby chronić cenne i poufne dane przed narażeniem innych osób lub złośliwych aplikacji. Działają one w celu ochrony integralności danych. Korzystają oni w pełni z bardziej zaawansowanych funkcji ochrony informacji w chmurze, w tym szyfrowania, bezpiecznego uwierzytelniania wieloskładnikowego, automatycznego uwierzytelniania ryzyka i zgodności oraz funkcji CASB (Cloud Access Security Broker), umożliwiając, a nawet zachęcając do udostępniania chronionych informacji na wielu platformach. Przeoczają oni cień IT w inspirujące kreatywność, produktywność i współpracę, co pozwala ich firmie na pozostanie na tle konkurencyjności.

## <a name="adopt-a-methodical-approach"></a>Przyjęcie metodyki

Większość problemów związanych z implementacją zabezpieczeń chmury w różnych organizacjach, niezależnie od branży, są bardzo podobne. Po pierwsze, chociaż istnieje wiele doskonałych dokumentów dotyczących określonych funkcji i możliwości, na poziomie organizacji występują pewne wątpliwości co do ich związku, gdzie funkcje zabezpieczeń nakładają się i jak powinny zostać zintegrowane. Istnieje również poziom niepewność, które funkcje zabezpieczeń są wstępnie skonfigurowane, a które wymagają konfiguracji przez organizację. Ponadto zespoły SOC niestety nie miały pełnej ekspozycji, szkoleń ani alokacji budżetowej wymaganej do przygotowania się do szybkiego wdrożenia chmury i transformacji cyfrowej ich organizacje już przechodzą.

Aby ułatwić Ci rozwiązanie tych przeszkody, firma Microsoft zaprojektowała kilka zasobów, które ułatwiają metodyczne podejście do strategii i implementacji zabezpieczeń.

|Zasób   |Więcej informacji  |
|---------|---------|
|[Najważniejsze zadania dla zespołów ds. zabezpieczeń na rzecz obsługi pracy w domu](../security/top-security-tasks-for-remote-work.md)      | Jeśli nagle okazało się, że obsługujesz głównie pracowników domowych, ten artykuł ułatwia szybkie zwiększyć bezpieczeństwo. Zawiera on najważniejsze zalecane zadania w zależności od planu licencjonowania.    |
|[Microsoft 365 do podejmowania decyzji biznesowych](../security/Microsoft-365-security-for-bdm.md)    | Gdy dysponujesz czasem na bardziej kompleksowy plan, ten artykuł zawiera zalecenia obejmujące Microsoft 365 priorytety według powierzchni ataków. Jest on dostępny również w arkuszu kalkulacyjnym, który umożliwia sortowanie informacji o licencjonowaniu i obszarze (na przykład tożsamości, ochrony przed zagrożeniami i monitorowanie).  |
|[Zalecenia dotyczące architektury zabezpieczeń firmy Microsoft](/security/compass/compass)    | Jeśli jesteś architektem zabezpieczeń, pamiętaj o tym, aby wyświetlić zalecenia dotyczące zabezpieczeń zorganizowane według dyscypliny, w tym tożsamości, sieci i operacji zabezpieczeń.   |
|[Zalecenia dotyczące operacji zabezpieczeń firmy Microsoft](/security/compass/security-operations-videos-and-decks)|Zapoznaj się z zaleceniami firmy Microsoft w zakresie konfigurowania i uruchamiania Centrum operacji zabezpieczeń (SOC, Security Operations Center) |
|[Szkolenie Dla dyrektor ds. bezpieczeństwa informacji (CISO) Workshop](/security/ciso-workshop/ciso-workshop)   | Jeśli nie masz jeszcze żadnych zabezpieczeń w chmurze, nie przegap tej serii klipów wideo.        |
|[docs.security.com/security](/security/)    | Wskazówki techniczne firmy Microsoft dotyczące strategii i architektury zabezpieczeń.        |
| | |

Wszystkie te zasoby zaprojektowano, aby służyć jako punkt wyjścia i być dostosowane do potrzeb organizacji.
