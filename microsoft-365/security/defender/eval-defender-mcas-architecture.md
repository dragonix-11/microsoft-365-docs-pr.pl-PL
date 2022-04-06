---
title: Przejrzyj wymagania dotyczące architektury i struktury Microsoft Defender for Cloud Apps
description: Microsoft Defender for Cloud Apps diagramy techniczne wyjaśniają architekturę w programie Microsoft 365 Defender, co pomoże w budowaniu środowiska pilotażowego.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6547c1b269ede9385b384ca18fe6f2ca34d35109
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500326"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Przegląd wymagań dotyczących architektury i kluczowych pojęć związanych z Microsoft Defender for Cloud Apps


**Dotyczy:**

- Microsoft 365 Defender

Ten artykuł to [krok 1 z 3](eval-defender-mcas-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender for Cloud Apps wraz z Microsoft 365 Defender. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-identity-overview.md).

Przed włączeniem Microsoft Defender for Cloud Apps upewnij się, że rozumiesz architekturę i może spełniać wymagania. 

## <a name="understand-the-architecture"></a>Opis architektury

Microsoft Defender for Cloud Apps to broker zabezpieczeń dostępu w chmurze (CASB). Zabezpieczenia CASB pełnią funkcje strażnika dostępu do usług brokera w czasie rzeczywistym między użytkownikami przedsiębiorstwa i zasobami w chmurze, z których korzystają, niezależnie od miejsca, w którym znajdują się Twoi użytkownicy, i niezależnie od urządzenia, z którego korzystają. Microsoft Defender for Cloud Apps natywnie integruje się z możliwościami zabezpieczeń firmy Microsoft, w tym z Microsoft 365 Defender.

Bez Defender dla Chmury aplikacje w chmurze używane przez Twoją organizację są niezabezpieczone i nie są chronione, jak pokazano na ilustracji.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="Architektura oprogramowania Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

Na ilustracji:
- Korzystanie z aplikacji w chmurze przez organizację nie jestmonitorowane i nie jest chronione. 
- To zastosowanie nie wchodzi w zakres ochrony zapewnianych przez organizację zarządzaną. 

#### <a name="discovering-cloud-apps"></a>Odnajdowanie aplikacji w chmurze

Pierwszym krokiem do zarządzania korzystaniem z aplikacji w chmurze jest odkrycie, które aplikacje w chmurze są używane przez Twoją organizację. Na tym następnym diagramie pokazano, jak odnajdowanie chmury działa Defender dla Chmury aplikacji.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="Architektura odnajdowania Microsoft Defender for Cloud Apps w chmurze" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


Na poniższej ilustracji istnieją dwie metody, za pomocą których można monitorować ruch sieciowy i odnajdować aplikacje w chmurze używane przez Twoją organizację.
- Odp. Odnajdowanie aplikacji w chmurze integruje się Ochrona punktu końcowego w usłudze Microsoft Defender natywnie. Usługa Defender for Endpoint zgłasza, że aplikacje i usługi w chmurze są dostępne z zarządzanych przez Windows 10 i Windows 11 urządzenia. 
- B. W przypadku zasięgu wszystkich urządzeń połączonych z siecią dziennik usługi Defender dla Chmury jest instalowany na zaporach i innych serwerach proxy w celu zbierania danych z punktów końcowych. Te dane są wysyłane do usługi Defender dla Chmury w celu analizy.

#### <a name="managing-cloud-apps"></a>Zarządzanie aplikacjami w chmurze

Po odnajdywaniu aplikacji w chmurze i analizowaniu ich sposobu, w jaki są używane przez Twoją organizację, możesz zacząć zarządzać aplikacjami w chmurze, które chcesz wybrać. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="Architektura oprogramowania Microsoft Defender for Cloud Apps trakcie zarządzania aplikacjami w chmurze" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

Na poniższej ilustracji:
- Niektóre aplikacje są schowane do użytku. Takie wytchnienie jest prostym sposobem na rozpoczęcie zarządzania aplikacjami.
- Możesz włączyć większą widoczność i kontrolę, łącząc aplikacje za pomocą łączników aplikacji. Łączniki aplikacji używają interfejsów API dostawców aplikacji.


#### <a name="applying-session-controls-to-cloud-apps"></a>Stosowanie kontrolek sesji do aplikacji w chmurze

Microsoft Defender for Cloud Apps pełni funkcję zwrotnego serwera proxy, zapewniając dostęp tego serwera do aplikacji w chmurze. To ustawienie umożliwia Defender dla Chmury aplikacji na stosowanie skonfigurowanych kontrolek sesji. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="Architektura dla programu Microsoft Defender for Cloud Apps — kontrola sesji dostępu serwera proxy" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

Na poniższej ilustracji:
- Dostęp do schowanych aplikacji w chmurze z użytkowników i urządzeń w organizacji jest przekierowywowyny za pośrednictwem Defender dla Chmury Aplikacje.
- Ten dostęp do serwera proxy umożliwia zastosowanie kontrolek sesji.
- Nie wpływa to na aplikacje w chmurze, które nie zostały wyparte lub jawnie niezamówione.

Kontrolki sesji umożliwiają stosowanie parametrów do sposobu, w jaki aplikacje w chmurze są używane przez Twoją organizację. Jeśli na przykład Twoja organizacja korzysta z usługi Salesforce, możesz skonfigurować zasady sesji, które zezwalają tylko zarządzanym urządzeniu na uzyskiwanie dostępu do danych organizacji w u usługi Salesforce. Prostszy przykład może dotyczyć konfigurowania zasad monitorowania ruchu z urządzeń nieza zarządzaniem, co pozwala przeanalizować ryzyko związane z tym ruchem przed zastosowaniem bardziej rygorystycznych zasad.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Integracja z usługą Azure AD i kontrolką aplikacji dostępu warunkowego

Być może do dzierżawy usługi Azure AD zostały już dodane aplikacje SaaS, aby wymuszać uwierzytelnianie wieloskładnikowe i inne zasady dostępu warunkowego. Microsoft Defender for Cloud Apps natywnie integruje się z usługą Azure AD. Wystarczy skonfigurować zasady w usłudze Azure AD w celu używania kontrolki aplikacji dostępu warunkowego w Defender dla Chmury aplikacji. Ruch sieciowy dla tych zarządzanych aplikacji SaaS jest przekierowywał przez serwer Defender dla Chmury Apps jako serwer proxy, co pozwala aplikacji Defender dla Chmury na monitorowanie tego ruchu i stosowanie kontrolek sesji. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="Architektura oprogramowania do Microsoft Defender for Cloud Apps - aplikacje SaaS" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

Na poniższej ilustracji:
- Aplikacje SaaS są zintegrowane z dzierżawą usługi Azure AD. Ta integracja umożliwia usłudze Azure AD wymuszanie zasad dostępu warunkowego, w tym uwierzytelniania wieloskładnikowego.
- Dodano politykę do Azure Active Directory kierowania ruchu aplikacji SaaS do Defender dla Chmury Oprogramowania. Zasady określają, do jakich aplikacji SaaS mają być stosowane te zasady. Dlatego po wymuszenia przez usługę Azure AD wszelkich zasad dostępu warunkowego, które mają zastosowanie do tych aplikacji SaaS, usługa Azure AD kieruje ruchem sesji przez usługę Defender dla Chmury Apps.
- Defender dla Chmury aplikacje monitoruje ten ruch i stosuje wszelkie zasady kontroli sesji skonfigurowane przez administratorów. 

Być może odkryto i schowałasz aplikacje w chmurze przy Defender dla Chmury, które nie zostały dodane do usługi Azure AD. Z funkcji kontroli aplikacji dostępu warunkowego możesz skorzystać, dodając te aplikacje w chmurze do dzierżawy usługi Azure AD oraz zakres reguł dostępu warunkowego.

#### <a name="protecting-your-organization-from-hackers"></a>Ochrona organizacji przed hakerami

Defender dla Chmury aplikacje samodzielnie zapewniają zaawansowaną ochronę. Jednak w połączeniu z innymi możliwościami aplikacji Microsoft 365 Defender aplikacje Defender dla Chmury podają dane do udostępnionych sygnałów, które (razem) pomagają zatrzymywać ataki.

Warto powtórzyć tę ilustrację od przeglądu do tego przewodnika Microsoft 365 Defender oceny i pilotażu. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Jak Microsoft 365 Defender łańcuch zagrożeń" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

Skupiając się po prawej stronie tej ilustracji, program Microsoft Defender for Cloud Apps zauważy nietypowe zachowanie, takie jak niemożliwa podróż, dostęp poświadczeń oraz nietypowe działania w zakresie pobierania, udostępniania plików lub przesyłania dalej poczty oraz zgłasza te zachowania zespołowi zabezpieczeń. Dlatego te Defender dla Chmury pomagają zapobiegać ruchu lateralnemu przez hakerów i ekscytację poufnych danych. System Microsoft 356 Defender dla Chmury skoreluje sygnały ze wszystkich składników, aby zapewnić pełną historię ataków.

## <a name="understand-key-concepts"></a>Opis kluczowych pojęć

W poniższej tabeli przedstawiono kluczowe pojęcia, które należy zrozumieć podczas oceniania, konfigurowania i wdrażania Microsoft Defender for Cloud Apps.


|Pojęcie  |Opis |Więcej informacji  |
|---------|---------|---------|
| Defender dla Chmury pulpit nawigacyjny aplikacji | Zawiera omówienie najważniejszych informacji na temat organizacji oraz linki do bardziej szczegółowego badania.        | [Praca z pulpitem nawigacyjnym ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Kontrolka aplikacji dostępu warunkowego    | Odwróć architekturę serwera proxy, która jest zintegrowana z Twoim dostawcą tożsamości( IdP), aby nadać zasadom dostępu warunkowego usługi Azure AD i selektywnie wymusić kontrolki sesji.        |  [Ochrona aplikacji za pomocą kontrolki Microsoft Defender for Cloud Apps dostępu warunkowego](/cloud-app-security/proxy-intro-aad)       |
|  Wykaz aplikacji w chmurze   | Wykaz aplikacji w chmurze udostępnia pełny obraz w wykazie firmy Microsoft z ponad 16 000 aplikacji w chmurze, które są klasyfikowane i klasyfikowane na podstawie ponad 80 czynników ryzyka.    |  [Praca z wynikami ryzyka aplikacji](/cloud-app-security/risk-score)       |
| Pulpit nawigacyjny odnajdowania w chmurze    | Odnajdowanie w chmurze analizuje dzienniki ruchu i ma na celu dać więcej informacji na temat sposobu, w jaki aplikacje w chmurze są używane w Twojej organizacji, a także alerty i poziomy ryzyka.     |  [Praca z wykrytymi aplikacjami   ](/cloud-app-security/discovered-apps)    |
|Połączone aplikacje |Defender dla Chmury aplikacje zapewniają end-to-end protection dla połączonych aplikacji przy użyciu integracji z chmurą i chmury, łączników interfejsu API oraz kontrolek dostępu i sesji w czasie rzeczywistym przy użyciu naszych warunkowych kontrolek dostępu do aplikacji. |[Ochrona połączonych aplikacji](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Przegląd wymagań dotyczących architektury

### <a name="discovering-cloud-apps"></a>Odnajdowanie aplikacji w chmurze

Aby odkryć aplikacje w chmurze używane w Twoim środowisku, możesz wdrożyć jedną lub obie z następujących metod:

- Szybko przygotuj się do pracy dzięki odnajdowi w chmurze, integrując się z usługą Ochrona punktu końcowego w usłudze Microsoft Defender. Ta natywna integracja umożliwia natychmiastowe rozpoczęcie zbierania danych dotyczących ruchu w chmurze na Windows 11 i Windows 10 urządzeniach sieciowych oraz poza siecią.
- Aby odkryć wszystkie aplikacje w chmurze dostępne dla wszystkich urządzeń połączonych z Siecią, wdaj dziennik aplikacji usługi Defender dla Chmury na zaporach i innych serwerach proxy. To wdrożenie ułatwia zbieranie danych z punktów końcowych i wysyłanie ich do usługi Defender dla Chmury do analizy. Defender dla Chmury aplikacje natywnie integrują się z niektórymi serwerów proxy innych firm, aby uzyskać jeszcze więcej możliwości.

Te opcje są zawarte w [kroku 2. Włącz środowisko oceny](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Stosowanie zasad dostępu warunkowego usługi Azure AD do aplikacji w chmurze

Warunkowe sterowanie aplikacjami dostępu (możliwość stosowania zasad dostępu warunkowego do aplikacji w chmurze) wymaga integracji z usługą Azure AD. Taka integracja nie jest wymaganiem rozpoczynania pracy z aplikacją Defender dla Chmury Apps. Jest to krok, który zachęcamy do wypróbowania w fazie pilotażowej — [krok 3. Pilot Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>Integracja zarządzania informacjami i zdarzeniami zabezpieczeń

Możesz zintegrować Microsoft Defender for Cloud Apps z ogólnym serwerem SIEM lub microsoft Sentinel, aby włączyć scentralizowane monitorowanie alertów i działań z połączonych aplikacji. 

Ponadto program Microsoft Sentinel zawiera łącznik Microsoft Defender for Cloud Apps w celu zapewnienia bardziej dogłębnej integracji z programem Microsoft Sentinel. Takie rozmieszczenie pozwala nie tylko uzyskać wgląd w aplikacje w chmurze, ale również uzyskać zaawansowane analizy w celu identyfikowania i zwalczania cyberataków oraz kontrolowania ruchu danych.

- [Integracja ogólnego SIEM](/cloud-app-security/siem)
- [Alerty przesyłania strumieniowego i dzienniki odnajdowania w chmurze Defender dla Chmury aplikacji do programu Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Następne kroki

Krok 2 z 3. [Włączanie środowiska oceny dla Microsoft Defender for Cloud Apps](eval-defender-mcas-enable-eval.md)

Powrót do omówieniem [funkcji Szacowanie Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
