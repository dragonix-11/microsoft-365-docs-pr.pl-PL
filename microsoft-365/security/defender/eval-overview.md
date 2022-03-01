---
title: Szacowanie i Microsoft 365 Defender pilotażowe, XDR
description: Zaplanuj laboratorium Microsoft 365 Defender testowe lub środowisko pilotażowe, aby przetestować i przetestować rozwiązanie zabezpieczające zaprojektowane do ochrony urządzeń, tożsamości, danych i aplikacji.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 06/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 442ac9859f259479da556a9611880a61ab0413e0
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013906"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Ocenianie i pilotaż Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender

Microsoft 365 Defender to rozwiązanie do rozszerzonego wykrywania i odpowiedzi (XDR, extended detection and response), które automatycznie zbiera, koreluje i analizuje sygnał, zagrożenia i dane alertów w środowisku usługi Microsoft 365, w tym punkt końcowy, adres e-mail, aplikacje i tożsamości. Wykorzystuje on rozbudowaną AI i automatyzację, aby automatycznie zatrzymywać ataki i korygować zasoby, których to dotyczy, do bezpiecznego stanu. W poniższych artykułach o krok po kroku proces konfigurowania środowiska próbnego, który umożliwia ocenę funkcji i możliwości programu Microsoft 365 Defender. 

W tych artykułach pokazano, jak włączać poszczególne składniki, konfigurować ustawienia i rozpoczynać monitorowanie w grupie pilotażowej. Gdy wszystko będzie gotowe, możesz zakończyć poprzez promocję środowiska oceny bezpośrednio do produkcji.

Firma Microsoft zaleca utworzenie oceny w istniejącej subskrypcji produkcyjnej usługi Office 365. Dzięki temu natychmiast uzyskasz szczegółowe informacje w świecie rzeczywistym i będziesz mieć możliwość dostosowania ustawień w celu ochrony przed bieżącymi zagrożeniami w Twoim środowisku. Po tym, jak uzyskasz doświadczenie i będziesz mieć doświadczenie w pracy z platformą, wystarczy po prostu promować każdy składnik, jeden na raz, do produkcji.

## <a name="the-anatomy-of-an-attack"></a>Anatomia ataków

Microsoft 365 Defender to oparty na chmurze, ujednolicony, przed naruszeniem i po naruszeniu ochrony przedsiębiorstwa. Koordynowanie działań *zapobiegania*, *wykrywania**, badania* i  odpowiedzi w różnych punktach końcowych, tożsamościach, aplikacjach, wiadomościach e-mail, aplikacjach do współpracy i wszystkich ich danych.

Na poniższej ilustracji trwa atak. Wiadomości e-mail wyłudzujące informacje są trafiane do skrzynki odbiorczej pracownika w Twojej organizacji, który nieuznajomie otwiera załącznik wiadomości e-mail. Powoduje to zainstalowanie złośliwego oprogramowania, które prowadzi do łańcucha zdarzeń, które może zakończyć się kradzieżą poufnych danych. Jednak w tym przypadku program Defender for Office 365 jest w działaniu.

![Jak Microsoft 365 Defender łańcuch zagrożeń.](../../media/defender/m365-defender-eval-threat-chain.png)

Na ilustracji:

- **Exchange Online Protection**, część programu Microsoft Defender for Office 365, może wykryć wiadomość e-mail wyłudzającą informacje i użyć reguł przepływu poczty, aby upewnić się, że nigdy nie dotrze ona do Skrzynki odbiorczej.
- Program **Defender for Office 365** bezpieczne załączniki testuje załącznik i ustala, że jest on niebezpieczny, więc o nadsyłanej wiadomości nie można zlecić działania przez użytkownika, albo zasady uniemożliwiają dojeżdżenie do poczty.
- **Program Defender for Endpoint** zarządza urządzeniami, które łączą się z siecią firmową, oraz wykrywają luki w zabezpieczeniach urządzeń i sieci, które mogą zostać w inny sposób wykorzystane.
- **Defender for Identity przyjmuje** do wiadomości niespodziewanie zmiany konta, takie jak eskalacji uprawnień lub ruchy boczne o wysokim poziomie ryzyka. Raportuje również problemy dotyczące łatwego wykorzystania tożsamości, takie jak niedoszkolone delegowanie Kerberos, w celu poprawienia ich przez zespół zabezpieczeń.
- **Usługa Microsoft Defender for Cloud Apps** zauważy nietypowe zachowanie, takie jak niemożliwy podróż, dostęp poświadczeń i nietypowe działania w zakresie pobierania, udostępniania plików lub przesyłania poczty dalej i zgłasza je zespołowi zabezpieczeń.

### <a name="microsoft-365-defender-components"></a>Microsoft 365 Defender składników

Microsoft 365 Defender są to te technologie zabezpieczeń działające razem. Te wszystkie składniki nie są potrzebne, aby korzystać z funkcji XDR i Microsoft 365 Defender. Zrealizujesz zyski i skuteczność, używając również jednej lub dwóch funkcji. 

|Składnik  |Opis  |Materiały referencyjne  |
|---------|---------|---------|
|Microsoft Defender for Identity     |      Usługa Microsoft Defender for Identity używa sygnałów usługi Active Directory do identyfikowania, wykrywania i badanie zaawansowanych zagrożeń, naruszonych tożsamości oraz złośliwych działań w ramach niejawnego programu testów skierowanych do organizacji.     |     [Co to jest program Microsoft Defender for Identity?](/defender-for-identity/what-is)   |
|Exchange Online Protection     |      Exchange Online Protection to natywna usługa przekazywania i filtrowania SMTP oparta na chmurze, która pomaga chronić organizację przed spamem i złośliwym oprogramowaniem.      |   [Omówienie Exchange Online Protection (EOP) — Office 365](../office-365-security/overview.md)     |
|Usługa Microsoft Defender dla Office 365     |     Program Microsoft Defender for Office 365 chroni organizację przed złośliwymi zagrożeniami, które mogą być ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy.      |    [Usługa Microsoft Defender dla Office 365 — Office 365](../office-365-security/overview.md)    |
|Ochrona punktu końcowego w usłudze Microsoft Defender     |     Program Microsoft Defender for Endpoint to ujednolicona platforma do ochrony urządzeń, wykrywania po naruszeniu, automatycznego badania i zalecanej odpowiedzi.      |   [Program Microsoft Defender dla punktu końcowego — Windows zabezpieczeń](../defender-endpoint/microsoft-defender-endpoint.md)    |
|Usługa Microsoft Defender dla aplikacji w chmurze     |      Usługa Microsoft Defender for Cloud Apps to kompleksowe rozwiązanie typu "cross-SaaS", które zapewnia pełną widoczność, silne kontrolki danych i ulepszoną ochronę przed zagrożeniami w aplikacjach w chmurze.       |    [Co to jest usługa Defender dla aplikacji w chmurze?](/cloud-app-security/what-is-cloud-app-security)    |
|Azure AD Identity Protection|Usługa Azure AD Identity Protection ocenia dane ryzyka od miliardów prób logowania i używa tych danych do oceny ryzyka każdego logowania w środowisku. Te dane są używane przez usługę Azure AD do zezwalania na dostęp do konta lub blokowania go w zależności od tego, jak skonfigurowano zasady dostępu warunkowego. Usługa Azure AD Identity Protection jest licencjonowana niezależnie od Microsoft 365 Defender. Jest on dołączony do Azure Active Directory — wersja Premium P2.|[Co to jest ochrona tożsamości?](/azure/active-directory/identity-protection/overview-identity-protection)|
| | | |

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender architekturze

Poniższy diagram przedstawia architekturę wysokiego poziomu dla kluczowych Microsoft 365 Defender i integracji. *W* tej serii artykułów odano szczegółową architekturę poszczególnych składników programu Defender oraz scenariusze scenariuszy użycia.

![Microsoft 365 Defender architekturze wysokiego poziomu.](../../media/defender/m365-defender-eval-architecture.png)

Na poniższej ilustracji:

- Microsoft 365 Defender łączy sygnały ze wszystkich składników Defender w celu zapewnienia rozszerzonego wykrywania i odpowiedzi (XDR) w różnych domenach. Obejmuje to ujednoliconą kolejkę zdarzeń, zautomatyzowaną reakcję w celu zatrzymania ataków, samooceny (w przypadku naruszonych urządzeń, tożsamości użytkowników i skrzynek pocztowych), śledzenia przez zagrożenia krzyżowe i analizy zagrożeń.
- Program Microsoft Defender for Office 365 chroni organizację przed złośliwymi zagrożeniami, które mogą być ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. Udostępnia ona sygnały wynikające z tych działań innym Microsoft 365 Defender. Exchange Online Protection (EOP) jest zintegrowane, aby zapewnić przychodzącą ochronę przychodzących wiadomości e-mail i załączników.
- Program Microsoft Defender for Identity zbiera sygnały z serwerów z usługami federacyjną Active Directory (AD FS) i usługami lokalnymi (Usługi domenowe w usłudze Active Directory (AD DS). Używa tych sygnałów do ochrony środowiska tożsamości hybrydowej, w tym ochrony przed hakerami, którzy używają naruszonych kont, do przenoszenia się w  nowszej wersji na stanowiskach w środowisku lokalnym.
- Program Microsoft Defender for Endpoint zbiera sygnały z urządzeń używanych przez Twoją organizację i chroni je.
- Usługa Microsoft Defender for Cloud Apps zbiera sygnały płynące z aplikacji w chmurze w Twojej organizacji i chroni dane przepływające między Twoim środowiskiem i tymi aplikacjami, w tym zarówno w aplikacjach w chmurze, które nie są w nich wykorzystywane, jak i nienawiązane.
- Usługa Azure AD Identity Protection ocenia dane ryzyka od miliardów prób logowania i używa tych danych do oceny ryzyka każdego logowania w środowisku. Te dane są używane przez usługę Azure AD do zezwalania na dostęp do konta lub blokowania go w zależności od tego, jak skonfigurowano zasady dostępu warunkowego. Usługa Azure AD Identity Protection jest licencjonowana niezależnie od Microsoft 365 Defender. Jest on dołączony do Azure Active Directory — wersja Premium P2.  

Dodatkowe opcjonalne składniki architektury, które nie zostały uwzględnione na poniższej ilustracji:

- Szczegółowe dane sygnału ze wszystkich Microsoft 365 Defender mogą być zintegrowane z programem Microsoft Sentinel i łączone z innymi źródłami rejestrowania, co zapewnia pełne możliwości i wnioski funkcji SIEM i SOAR.

## <a name="the-evaluation-process"></a>Proces oceny

Firma Microsoft zaleca włączenie składników Microsoft 365 w kolejności przedstawionej na ilustracji:

![Microsoft 365 Defender proces oceny wysokiego poziomu.](../../media/defender/m365-defender-eval-process.png)

W poniższej tabeli opisano tę ilustrację.

|      |Krok  |Opis  |
|------|---------|---------|
|1     | [Tworzenie środowiska oceny](eval-create-eval-environment.md)       |Ten krok gwarantuje, że masz licencję na wersję próbną Microsoft 365 Defender.         |
|2     | [Włączanie usługi Defender dla tożsamości](eval-defender-identity-overview.md)        | Przejrzyj wymagania dotyczące architektury, włącz proces oceny i zapoznaj się z samouczkami umożliwiającymi identyfikowanie i korygowanie różnych typów ataków.   |
|3     | [Włączanie usługi Defender dla Office 365 ](eval-defender-office-365-overview.md)       | Upewnij się, że spełniasz wymagania dotyczące architektury, włącz ocenę, a następnie utwórz środowisko pilotażowe. Ten składnik zawiera Exchange Online Protection, więc w rzeczywistości zarówno *tutaj, jak i tutaj oceniasz obie* te wartości.      |
|4     | [Włączanie usługi Defender dla punktu końcowego ](eval-defender-endpoint-overview.md)       | Upewnij się, że spełniasz wymagania dotyczące architektury, włącz ocenę, a następnie utwórz środowisko pilotażowe.         |
|5     | [Włączanie usługi Microsoft Defender dla aplikacji w chmurze](eval-defender-mcas-overview.md)        |  Upewnij się, że spełniasz wymagania dotyczące architektury, włącz ocenę, a następnie utwórz środowisko pilotażowe.        |
|6     | [Badanie zagrożeń i reagowanie na nie](eval-defender-investigate-respond.md)        |   Symulowanie ataków i rozpoczynanie korzystania z możliwości reagowania na incydenty.      |
|7     | [Promowanie wersji próbnej do wersji produkcyjnej](eval-defender-promote-to-production.md)        | Podniesienie Microsoft 365 do produkcji jeden po jeden.        |
| | | |

Jest to zazwyczaj zalecana kolejność, która pozwala szybko uzyskać wartość funkcji w zależności od tego, ile zazwyczaj jest wymagane do wdrożenia i skonfigurowania tych funkcji. Na przykład usługę Defender for Office 365 skonfigurować w krótszym czasie, niż zajmuje zarejestrowanie urządzeń w programie Defender dla punktu końcowego. Oczywiście możesz określić priorytety składników w celu zaspokojenia potrzeb biznesowych i włączyć je w innej kolejności.

## <a name="next-steps"></a>Następne kroki

[Tworzenie środowiska Microsoft 365 Defender oceny](eval-create-eval-environment.md)
