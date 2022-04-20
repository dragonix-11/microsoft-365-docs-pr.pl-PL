---
title: Krok 3. Wdrażanie zabezpieczeń i zgodności dla hybrydowych procesów roboczych
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Użyj Microsoft 365 usług zabezpieczeń i zgodności, aby chronić aplikacje, dane i urządzenia dla hybrydowych procesów roboczych.
ms.openlocfilehash: 08771de0f9e833405da308fb645b5fb5c906c543
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937790"
---
# <a name="step-3-deploy-security-and-compliance-for-hybrid-workers"></a>Krok 3. Wdrażanie zabezpieczeń i zgodności dla hybrydowych procesów roboczych

W przypadku hybrydowych pracowników, z których niektórzy nigdy nie wchodzą do biura lub rzadko przechodzą, bezpieczeństwo i zgodność są ważną częścią ogólnego rozwiązania. Cała ich komunikacja odbywa się przez Internet, a nie ogranicza się do intranetu organizacyjnego.

Istnieją rzeczy, które Ty i Twoi pracownicy możecie zrobić, aby zachować produktywność przy jednoczesnym zmniejszeniu ryzyka cyberbezpieczeństwa i zachowaniu zgodności z wewnętrznymi zasadami i przepisami dotyczącymi danych.

Praca zdalna wymaga następujących elementów zabezpieczeń i zgodności:

- Kontrolowany dostęp do aplikacji zwiększających produktywność używanych przez hybrydowych pracowników, takich jak Microsoft Teams
- Kontrolowany dostęp do danych i ochrona danych, które tworzą i używają hybrydowi pracownicy, takich jak konwersacje na czacie lub pliki udostępnione
- Ochrona Windows 11 lub 10 urządzeń przed złośliwym oprogramowaniem i innymi rodzajami cyberataków
- Ochrona poczty e-mail, plików i witryny przy spójnym etykietowaniu poziomów poufności i ochrony
- Zapobieganie wyciekom informacji
- Przestrzeganie regionalnych przepisów dotyczących danych

Poniżej przedstawiono funkcje Microsoft 365, które zapewniają usługi zabezpieczeń i zgodności dla hybrydowych procesów roboczych.

:::image type="content" source="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png" alt-text="Użyj tych usług Microsoft 365, aby zachować bezpieczeństwo i zgodność" lightbox="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png":::

## <a name="security"></a>Bezpieczeństwo

Ochrona aplikacji i danych za pomocą tych funkcji zabezpieczeń Microsoft 365.

|Możliwość lub funkcja|Dlaczego tego potrzebuję|Licencjonowanie|
|---|---|---|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|Ochrona Microsoft 365 aplikacji i danych — takich jak wiadomości e-mail, Office dokumenty i narzędzia do współpracy — przed atakiem. <p> Ochrona usługi Office 365 w usłudze Microsoft Defender zbiera i analizuje sygnały z aplikacji w celu wykrywania, badania i korygowania zagrożeń bezpieczeństwa oraz zabezpiecza organizację przed złośliwymi zagrożeniami stwarzaowymi przez wiadomości e-mail, linki (adresy URL) i narzędzia do współpracy. Zapewnia również zautomatyzowane narzędzie do oceny konfiguracji dzierżawy i konfiguracji dla standardowych i ścisłych postaw zabezpieczeń.|Microsoft 365 E3 lub E5|
|Ochrona przed złośliwym oprogramowaniem|Program antywirusowy Microsoft Defender i Device Guard zapewniają ochronę przed złośliwym oprogramowaniem opartym na urządzeniach. <p> SharePoint Online automatycznie skanuje przekazywanie plików pod kątem znanego złośliwego oprogramowania. <p> Exchange Online Protection (EOP) zabezpiecza skrzynki pocztowe w chmurze.|Microsoft 365 E3 lub E5|
|Ochrona punktu końcowego w usłudze Microsoft Defender|Ochrona urządzeń organizacji przed zagrożeniami cybernetycznymi i naruszeniami danych oraz wykrywanie, badanie i reagowanie na zaawansowane zagrożenia.|Microsoft 365 E5|
|Defender for Cloud Apps|Ochrona usług opartych na chmurze — zarówno Microsoft 365, jak i innych aplikacji SaaS — przed atakiem.|licencje Microsoft 365 E5 lub indywidualne aplikacje Defender dla Chmury|
|Ochrona tożsamości w usłudze Azure AD|Automatyzowanie wykrywania i korygowania zagrożeń opartych na tożsamościach. <p>Tworzenie zasad dostępu warunkowego opartego na ryzyku w celu wymagania uwierzytelniania wieloskładnikowego (MFA) w przypadku ryzykownych logowań.|Microsoft 365 E5 lub E3 z licencjami Azure AD — wersja Premium P2|
||||

Pierwszym krokiem powinno być zapoznanie się z usługą [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score) i korzystanie z niej.

Aby uzyskać więcej informacji, zobacz [Top 12 tasks for security teams to support working from home (12 najważniejszych zadań zespołów zabezpieczeń do obsługi pracy z domu](../security/top-security-tasks-for-remote-work.md) ).

Aby uzyskać informacje o zabezpieczeniach w Microsoft 365, zobacz [Microsoft 365 dokumentację zabezpieczeń](/microsoft-365/security).

## <a name="compliance"></a>Zgodność

Zgodność z zasadami wewnętrznymi lub wymaganiami prawnymi z tymi funkcjami zgodności Microsoft 365.

|Możliwość lub funkcja|Dlaczego tego potrzebuję|Licencjonowanie|
|---|---|---|
|Etykiety wrażliwości|Klasyfikowanie i ochrona danych organizacji bez ograniczania produktywności użytkowników i możliwości współpracy przez umieszczanie etykiet z różnymi poziomami ochrony w wiadomościach e-mail, plikach lub witrynach.|Microsoft 365 E3 lub E5|
|Ochrona przed utratą danych (DLP)|Wykrywanie, ostrzeganie i blokowanie ryzykownych, niezamierzonych lub niewłaściwych udostępniania, takich jak udostępnianie danych zawierających dane osobowe, zarówno wewnętrznie, jak i zewnętrznie.|Microsoft 365 E3 lub E5|
|Kontrola dostępu warunkowego aplikacji|Zapobiegaj pobieraniu poufnych danych na urządzenia osobiste użytkowników.|Microsoft 365 E3 lub E5|
|Etykiety i zasady przechowywania danych|Zaimplementuj mechanizmy nadzoru informacji, takie jak czas przechowywania danych i wymagań dotyczących przechowywania danych osobowych na klientach, w celu zachowania zgodności z zasadami organizacji lub przepisami dotyczącymi danych.|Microsoft 365 E3 lub E5|
|Szyfrowanie komunikatów usługi Microsoft Purview|Wysyłaj i odbieraj zaszyfrowane wiadomości e-mail między osobami w organizacji i poza nią, które zawierają dane regulowane, takie jak dane osobowe klientów.|Microsoft 365 E3 lub E5|
|Menedżer zgodności|Zarządzanie działaniami zgodności z przepisami związanymi z usługami firmy Microsoft w chmurze za pomocą tego narzędzia do oceny ryzyka opartego na przepływie pracy w portalu zaufania usług firmy Microsoft.|Microsoft 365 E3 lub E5|
|Menedżer zgodności|Zapoznaj się z ogólnym wynikiem bieżącej konfiguracji zgodności i zaleceniami dotyczącymi jej ulepszania w portalu zgodności usługi Microsoft Purview.|Microsoft 365 E3 lub E5|
|Zgodność z komunikacją|Wykrywanie, przechwytywanie i akcje korygowania w przypadku nieodpowiednich komunikatów w organizacji.|Microsoft 365 E5 lub Microsoft 365 E3 z dodatkami Compliance lub Insider Risk Management|
|Zarządzanie ryzykiem wewnętrznym|Wykrywanie, badanie i działanie na złośliwym i niezamierzonym ryzyku w organizacji. Microsoft 365 może wykrywać tego rodzaju zagrożenia nawet wtedy, gdy proces roboczy korzysta z urządzenia niezarządzanego.|Microsoft 365 E5 lub Microsoft 365 E3 z dodatkami Compliance lub Insider Risk Management|
||||

Aby uzyskać więcej informacji [, zobacz Szybkie zadania umożliwiające rozpoczęcie pracy z usługą Microsoft Purview](../compliance/compliance-quick-tasks.md) .

## <a name="results-of-step-3"></a>Wyniki kroku 3

W przypadku hybrydowych procesów roboczych zaimplementowane zostały:

- Bezpieczeństwo
  - Kontrolowany dostęp do aplikacji i danych używanych przez hybrydowe procesy robocze do komunikowania się i współpracy
  - Ochrona przed złośliwym oprogramowaniem dla danych usługi w chmurze, poczty e-mail i urządzeń Windows 11 lub 10
- Zgodność
  - Spójne etykietowanie poziomów poufności i ochrony
  - Zasady zapobiegania wyciekom informacji
  - Przestrzeganie regionalnych przepisów dotyczących danych

## <a name="next-step"></a>Następny krok

[![Krok 4. Zarządzanie urządzeniami, komputerami i innymi punktami końcowymi.](../media/empower-people-to-work-remotely/remote-workers-step-grid-4.png)](empower-people-to-work-remotely-manage-endpoints.md)

Przejdź do [kroku 4](empower-people-to-work-remotely-manage-endpoints.md) , aby zarządzać urządzeniami, komputerami i innymi punktami końcowymi.
