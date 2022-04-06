---
title: Szacowanie i Microsoft 365 Defender pilotażowe, rozwiązanie XDR
description: Co to są zabezpieczenia XDR? Jak można ocenić xdr firmy Microsoft w programie Microsoft 365 Defender? W tej serii blogu możesz zaplanować laboratorium Microsoft 365 Defender próbne lub środowisko pilotażowe, aby przetestować i pilotaż rozwiązania zabezpieczającego zaprojektowanego do ochrony urządzeń, tożsamości, danych i aplikacji. Rozpocznij tutaj podróż z zabezpieczeniami cyberzagrożenia XDR i przetestuj to do produkcji.
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
ms.openlocfilehash: f7830bb25f2572c43d665d059e0a36bc1fdaa172
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500788"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Ocena i pilotaż usługi Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>Jak działa seria artykułów

Ta seria artykułów ma na celu krok po kroku przez cały proces konfigurowania środowiska XDR w wersji próbnej— *end-to-end*, dzięki czemu możesz ocenić funkcje i możliwości programu Microsoft 365 Defender a nawet promować środowisko oceny bezpośrednio do produkcji, gdy i jeśli wszystko będzie gotowe.

Jeśli nie masz pomysłu na kod XDR, możesz przeskanować te 7 artykułów połączonych, aby dowiedzieć się, jak rozbudowane jest rozwiązanie.

- [Jak utworzyć środowisko](eval-create-eval-environment.md)
- Konfigurowanie i poznanie poszczególnych technologii tego xdr firmy Microsoft
  - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
  - [Program Microsoft Defender dla Office](eval-defender-office-365-overview.md)
  - [Ochrona punktu końcowego w usłudze Microsoft Defender](eval-defender-endpoint-overview.md)
  - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Jak zbadać i odpowiedzieć przy użyciu tego xdr](eval-defender-investigate-respond.md)
- [Promowanie środowiska próbnego do produkcji](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender to rozwiązanie do ochrony przed cyberzagrożeniami XDR firmy Microsoft

Microsoft 365 Defender to rozwiązanie **eXtended detection and response (XDR),** które automatycznie zbiera, koreluje i analizuje dane sygnału, zagrożeń i alertów w środowisku usługi Microsoft 365,  w tym punkt końcowy, poczta e-mail *, aplikacje i tożsamości*. Wykorzystuje ona sztuczną inteligencję i automatyzację, aby automatycznie  zatrzymywać ataki i rekultywować zasoby, których to dotyczy, w stanie bezpiecznym.

Kod XDR to kolejny krok w zakresie zabezpieczeń, unifying endpoint (wykrywanie i reagowanie w punktach końcowych lub EDR), poczty e-mail, aplikacji i tożsamości w jednym miejscu.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>Zalecenia firmy Microsoft dotyczące szacowania Microsoft 365 Defender

Firma Microsoft zaleca utworzenie oceny w istniejącej subskrypcji produkcyjnej usługi Office 365. Dzięki temu natychmiast uzyskasz szczegółowe informacje w świecie rzeczywistym i będziesz mieć możliwość dostosowania ustawień w celu ochrony przed bieżącymi zagrożeniami w Twoim środowisku. Po tym, jak uzyskasz doświadczenie i będziesz mieć doświadczenie w pracy z platformą, wystarczy po prostu promować każdy składnik, jeden na raz, do produkcji.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>Anatomia ataków na bezpieczeństwo cyberprzestępczości

Microsoft 365 Defender to oparty na chmurze, ujednolicony, przed naruszeniem i po naruszeniu ochrony przedsiębiorstwa. Koordynowanie działań *zapobiegania*, *wykrywania**, badania* i  odpowiedzi w różnych punktach końcowych, tożsamościach, aplikacjach, wiadomościach e-mail, aplikacjach do współpracy i wszystkich ich danych.

Na poniższej ilustracji trwa atak. Wiadomości e-mail wyłudzujące informacje są trafiane do skrzynki odbiorczej pracownika w Twojej organizacji, który nieuznajomie otwiera załącznik wiadomości e-mail. Powoduje to zainstalowanie złośliwego oprogramowania, które prowadzi do łańcucha zdarzeń, które może zakończyć się kradzieżą poufnych danych. Jednak w tym Ochrona usługi Office 365 w usłudze Defender jest w działaniu.

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Różne próby ataków" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

Na ilustracji:

- **Exchange Online Protection**, część Ochrona usługi Office 365 w usłudze Microsoft Defender, może wykryć wiadomość e-mail wyłudzającą informacje i użyć reguł przepływu poczty, aby upewnić się, że nigdy nie dotrze ona do Skrzynki odbiorczej.
- **Ochrona usługi Office 365 w usłudze Defender** bezpieczne załączniki testują załączniki i określają, że jest on niebezpieczny, dlatego przychodząca wiadomość nie może być przez użytkownika zasypytą akcją, lub zasady uniemożliwiają, by poczta w ogóle nie trafiała.
- **Program Defender for Endpoint** zarządza urządzeniami, które łączą się z siecią firmową, oraz wykrywają luki w zabezpieczeniach urządzeń i sieci, które mogą zostać w inny sposób wykorzystane.
- **Defender for Identity przyjmuje** do wiadomości niespodziewanie zmiany konta, takie jak eskalacji uprawnień lub ruchy boczne o wysokim poziomie ryzyka. Raportuje również problemy dotyczące łatwego wykorzystania tożsamości, takie jak niedoszkolone delegowanie Kerberos, w celu poprawienia ich przez zespół zabezpieczeń.
- **Microsoft Defender for Cloud Apps** dostrzegą nietypowe zachowanie, takie jak niemożliwa podróż, dostęp poświadczeń i nietypowe działania w zakresie pobierania, udostępniania plików lub przesyłania dalej poczty i zgłasza je zespołowi zabezpieczeń.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender składników zabezpieczanie urządzeń, tożsamości, danych i aplikacji

Microsoft 365 Defender są to te technologie zabezpieczeń działające razem. Te wszystkie składniki nie są potrzebne, aby korzystać z funkcji XDR i Microsoft 365 Defender. Zrealizujesz zyski i skuteczność, używając również jednej lub dwóch funkcji.

|Składnik|Opis|Materiały referencyjne|
|---|---|---|
|Microsoft Defender for Identity|Microsoft Defender for Identity używa sygnałów usługi Active Directory do identyfikowania, wykrywania i badanie zaawansowanych zagrożeń, naruszonych tożsamości oraz złośliwych działań w ramach niejawnego programu testów skierowanych do organizacji.|[Co to jest usługa Microsoft Defender for Identity?](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection to natywna usługa przekazywania i filtrowania SMTP oparta na chmurze, która pomaga chronić organizację przed spamem i złośliwym oprogramowaniem.|[Omówienie Exchange Online Protection (EOP) — Office 365](../office-365-security/overview.md)|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|Ochrona usługi Office 365 w usłudze Microsoft Defender chroni organizację przed złośliwymi zagrożeniami ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy.|[Ochrona usługi Office 365 w usłudze Microsoft Defender — Office 365](../office-365-security/overview.md)|
|Ochrona punktu końcowego w usłudze Microsoft Defender|Ochrona punktu końcowego w usłudze Microsoft Defender to ujednolicona platforma do ochrony urządzeń, wykrywania naruszenia, automatycznego badania i zalecanej odpowiedzi.|[Ochrona punktu końcowego w usłudze Microsoft Defender — Windows zabezpieczeń](../defender-endpoint/microsoft-defender-endpoint.md)|
|Microsoft Defender for Cloud Apps|Microsoft Defender for Cloud Apps to kompleksowe rozwiązanie typu saaS, które zapewnia pełną widoczność, silne kontrolki danych i ulepszoną ochronę przed zagrożeniami w aplikacjach w chmurze.|[Co to są Defender dla Chmury aplikacji?](/cloud-app-security/what-is-cloud-app-security)|
|Ochrona tożsamości w usłudze Azure AD|Usługa Azure AD Identity Protection ocenia dane ryzyka od miliardów prób logowania i używa tych danych do oceny ryzyka każdego logowania w środowisku. Te dane są używane przez usługę Azure AD do zezwalania na dostęp do konta lub blokowania go w zależności od tego, jak skonfigurowano zasady dostępu warunkowego. Usługa Azure AD Identity Protection jest licencjonowana niezależnie od Microsoft 365 Defender. Jest on dołączony do Azure Active Directory — wersja Premium P2.|[Co to jest ochrona tożsamości?](/azure/active-directory/identity-protection/overview-identity-protection)|
||||

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender architekturze

Poniższy diagram przedstawia architekturę wysokiego poziomu dla kluczowych Microsoft 365 Defender i integracji. *W* tej serii artykułów odano szczegółową architekturę poszczególnych składników programu Defender oraz scenariusze scenariuszy użycia.

:::image type="content" source="../../media/defender/m365-defender-eval-architecture.png" alt-text="High-level architecture of the Microsoft 365 Defender portal" lightbox="../../media/defender/m365-defender-eval-architecture.png":::

Na poniższej ilustracji:

- Microsoft 365 Defender łączy sygnały ze wszystkich składników Defender w celu zapewnienia rozszerzonego wykrywania i odpowiedzi (XDR) w różnych domenach. Obejmuje to ujednoliconą kolejkę zdarzeń, zautomatyzowaną reakcję w celu zatrzymania ataków, samooceny (w przypadku naruszonych urządzeń, tożsamości użytkowników i skrzynek pocztowych), śledzenia przez zagrożenia krzyżowe i analizy zagrożeń.
- Ochrona usługi Office 365 w usłudze Microsoft Defender chroni organizację przed złośliwymi zagrożeniami ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. Udostępnia ona sygnały wynikające z tych działań innym Microsoft 365 Defender. Exchange Online Protection (EOP) jest zintegrowane, aby zapewnić przychodzącą ochronę przychodzących wiadomości e-mail i załączników.
- Microsoft Defender for Identity zbiera sygnały z serwerów z usługami federacyjną Active Directory (AD FS) i lokalna usługa Active Directory domenowych (AD DS). Używa tych sygnałów do ochrony środowiska tożsamości hybrydowej, w tym ochrony przed hakerami, którzy używają naruszonych kont, do przenoszenia się w  nowszej wersji na stanowiskach w środowisku lokalnym.
- Ochrona punktu końcowego w usłudze Microsoft Defender zbiera sygnały z urządzeń używanych przez Twoją organizację i chroni je.
- Microsoft Defender for Cloud Apps zbiera sygnały płynące z aplikacji w chmurze w Twojej organizacji i chroni dane przepływające między Twoim środowiskiem a tymi aplikacjami, w tym zarówno w aplikacjach w chmurze, jak i w aplikacjach w chmurze, które nie są unsanctioned.
- Usługa Azure AD Identity Protection ocenia dane ryzyka od miliardów prób logowania i używa tych danych do oceny ryzyka każdego logowania w środowisku. Te dane są używane przez usługę Azure AD do zezwalania na dostęp do konta lub blokowania go w zależności od tego, jak skonfigurowano zasady dostępu warunkowego. Usługa Azure AD Identity Protection jest licencjonowana niezależnie od Microsoft 365 Defender. Jest on dołączony do Azure Active Directory — wersja Premium P2.

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>Firmy Microsoft SIEM i SOAR mogą używać danych z Microsoft 365 Defender

Dodatkowe opcjonalne składniki architektury, które nie zostały uwzględnione na poniższej ilustracji:

- **Szczegółowe dane sygnału ze wszystkich Microsoft 365 Defender** mogą być zintegrowane z programem Microsoft Sentinel i łączone z innymi źródłami rejestrowania, co zapewnia pełne możliwości i wnioski funkcji SIEM i SOAR.
- Aby uzyskać więcej informacji na temat korzystania z platformy **Microsoft Sentinel, platformy Azure SIEM z** Microsoft 365 Defender jako alternatywy XDR, zobacz ten artykuł [](/azure/sentinel/microsoft-365-defender-sentinel-integration) z omówieniem oraz kroki integracji z programem Microsoft Sentinel Microsoft 365 Defender [projektu](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE).
- Aby uzyskać więcej informacji na temat programu SOAR w programie Microsoft Sentinel (w tym linki do podręczników w repozytorium programu Microsoft Sentinel GitHub), przeczytaj [ten artykuł](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>Proces oceny pod Microsoft 365 Defender ochrony przed cyberzagrożeniami

Firma Microsoft zaleca włączenie składników Microsoft 365 w kolejności przedstawionej na ilustracji:

:::image type="content" source="../../media/defender/m365-defender-eval-process.png" alt-text="Proces oceny wysokiego poziomu w portalu Microsoft 365 Defender projektu" lightbox="../../media/defender/m365-defender-eval-process.png":::

W poniższej tabeli opisano tę ilustrację.

|  Serial Number (Numer seryjny)   |Krok  |Opis  |
|------|---------|---------|
|1     | [Tworzenie środowiska oceny](eval-create-eval-environment.md)       |Ten krok gwarantuje, że masz licencję na wersję próbną Microsoft 365 Defender.         |
|2     | [Włączanie usługi Defender dla tożsamości](eval-defender-identity-overview.md)        | Przejrzyj wymagania dotyczące architektury, włącz proces oceny i zapoznaj się z samouczkami umożliwiającymi identyfikowanie i korygowanie różnych typów ataków.   |
|3     | [Włączanie Ochrona usługi Office 365 w usłudze Defender ](eval-defender-office-365-overview.md)       | Upewnij się, że spełniasz wymagania dotyczące architektury, włącz ocenę, a następnie utwórz środowisko pilotażowe. Ten składnik zawiera Exchange Online Protection, więc w rzeczywistości zarówno *tutaj, jak i tutaj oceniasz obie* te wartości.      |
|4     | [Włączanie usługi Defender dla punktu końcowego ](eval-defender-endpoint-overview.md)       | Upewnij się, że spełniasz wymagania dotyczące architektury, włącz ocenę, a następnie utwórz środowisko pilotażowe.         |
|5     | [Włącz Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)        |  Upewnij się, że spełniasz wymagania dotyczące architektury, włącz ocenę, a następnie utwórz środowisko pilotażowe.        |
|6     | [Badanie zagrożeń i odpowiadanie na nie](eval-defender-investigate-respond.md)        |   Symulowanie ataków i rozpoczynanie korzystania z możliwości reagowania na incydenty.      |
|7     | [Podwyższanie wersji próbnej do poziomu wersji produkcyjnej](eval-defender-promote-to-production.md)        | Podniesienie Microsoft 365 do produkcji jeden po jeden.        |

Jest to zazwyczaj zalecana kolejność, która pozwala szybko wykorzystać wartość funkcji w zależności od tego, ile nakładu pracy jest zazwyczaj wymagane do wdrożenia i skonfigurowania tych funkcji. Na przykład Ochrona usługi Office 365 w usłudze Defender skonfigurować w krótszym czasie, niż trwa zarejestrowanie urządzeń w programie Defender dla punktu końcowego. Oczywiście należy określić priorytety składników w celu zaspokojenia potrzeb biznesowych i włączyć je w innej kolejności.

## <a name="go-to-the-next-step"></a>Przejdź do następnego kroku

[Informacje o środowisku oceny Microsoft 365 Defender i (lub) tworzeniu](eval-create-eval-environment.md)
