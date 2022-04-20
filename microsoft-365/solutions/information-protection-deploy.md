---
title: Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
ms.custom: admindeeplinkCOMPLIANCE
description: Skonfiguruj ochronę informacji w Microsoft 365 dla przepisów dotyczących prywatności danych, takich jak RODO i California Consumer Privacy Act (CCPA), w tym Microsoft Teams, SharePoint i poczty e-mail.
ms.openlocfilehash: ece8483773d3e2f5cdafe90bd93e11c52e2ba838
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939021"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365

Twoja organizacja może podlegać regionalnym przepisom dotyczącym prywatności danych, które wymagają ochrony, zarządzania i zapewniania praw i kontroli nad danymi osobowymi przechowywanymi w infrastrukturze IT, w tym zarówno lokalnie, jak i w chmurze. Najlepszym przykładem regulacji prywatności danych jest ogólne rozporządzenie o ochronie danych (RODO). Nieprzestrzeganie przepisów dotyczących ochrony prywatności danych może skutkować znacznymi grzywnami.

Przykłady typów danych w Microsoft 365 obejmują sesje czatów w Microsoft Teams, wiadomości e-mail w Exchange i pliki w SharePoint i OneDrive. To rozwiązanie zawiera wskazówki dotyczące oceny ryzyka i podjęcia odpowiednich działań w celu ochrony danych osobowych w Microsoft 365. Obejmuje to identyfikowanie danych osobowych, dzięki czemu można chronić, zarządzać zdarzeniami dotyczącymi prywatności danych i reagować na nie.

![Co to jest ochrona informacji dla przepisów dotyczących prywatności danych.](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Dostępne są również dodatkowe informacje na temat korzystania z mechanizmów kontroli tożsamości Microsoft 365, urządzeń i ochrony przed zagrożeniami w celu zapewnienia prywatności danych.

Obejrzyj to wideo, aby zapoznać się z omówieniem procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Te Microsoft 365 możliwości i funkcje ułatwiają spełnienie kryteriów ochrony informacji.

| Możliwość lub funkcja | Opis | Licencjonowanie |
|:-------|:-----|:-------|
| Menedżer zgodności | Zarządzanie działaniami zgodności z przepisami, uzyskiwanie ogólnego wyniku bieżącej konfiguracji zgodności i znajdowanie zaleceń dotyczących ulepszeń. Jest to narzędzie do oceny ryzyka opartego na przepływie pracy w portalu zgodności usługi Microsoft Purview. | Microsoft 365 E3 i E5 |
| Ochrona usługi Office 365 w usłudze Microsoft Defender | Ochrona Microsoft 365 aplikacji i danych — takich jak wiadomości e-mail, Office dokumenty i narzędzia do współpracy — przed atakiem. | Microsoft 365 E3 i E5 |
| Etykiety wrażliwości | Klasyfikowanie i ochrona danych organizacji bez ograniczania produktywności użytkowników i możliwości współpracy. Umieść etykiety z różnymi poziomami ochrony w wiadomościach e-mail, plikach lub witrynach. | Microsoft 365 E3 i E5 |
| Ochrona przed utratą danych (DLP) | Wykrywanie, ostrzeganie i blokowanie ryzykownych, niezamierzonych lub nieodpowiednich danych zawierających dane osobowe, zarówno wewnętrznie, jak i zewnętrznie. | Microsoft 365 E3 i E5 |
| Etykiety i zasady przechowywania danych | Zaimplementuj mechanizmy kontroli ładu informacji. Mogą one obejmować określenie czasu przechowywania danych (takich jak dane osobowe powiązane z klientami) w celu zachowania zgodności z zasadami organizacji lub przepisami dotyczącymi danych. | Microsoft 365 E3 i E5 |
| Szyfrowanie wiadomości e-mail | Ochrona danych osobowych przez wysyłanie i odbieranie zaszyfrowanych wiadomości e-mail między osobami w organizacji i poza nią. | Microsoft 365 E3 i E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organizacja wskazówek w tym rozwiązaniu

Aby ułatwić zrozumienie dostępnych narzędzi Microsoft 365, które ułatwiają spełnienie co najmniej jednego przepisu dotyczącego prywatności, te wskazówki są zorganizowane w sekcje.

![Kroki implementowania ochrony informacji dla przepisów dotyczących prywatności danych.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Każda z tych sekcji odpowiada oddzielnemu artykułowi w tym rozwiązaniu.

> [!NOTE]
> Jeśli znasz już swoje obowiązki w zakresie ochrony prywatności danych i wykonujesz działania względem istniejącego planu, możesz skupić się na wskazówkach dotyczących zapobiegania, ochrony, zachowywania i badania.

> [!IMPORTANT]
> Wykonanie tych wskazówek niekoniecznie zapewni zgodność z żadnymi przepisami dotyczącymi prywatności danych, zwłaszcza biorąc pod uwagę liczbę wymaganych kroków spoza kontekstu funkcji. Użytkownik jest odpowiedzialny za zapewnienie zgodności i zasięgnięcie opinii zespołów prawnych i zespołów ds. zgodności lub zasięgnięcie wskazówek i porad od osób trzecich, które specjalizują się w zgodności.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan: Ocena ryzyka związanego z prywatnością danych i identyfikowanie poufnych elementów

Ocena przepisów dotyczących prywatności danych i zagrożeń, na które podlega organizacja, jest kluczowym pierwszym krokiem do wykonania przed rozpoczęciem wdrażania ulepszeń, w tym konfigurowania możliwości w Microsoft 365. Ta praca może obejmować ogólną ocenę gotowości lub identyfikację określonych typów informacji poufnych, które podlegają kontrolom regulacyjnym, które organizacja musi przestrzegać.

Aby uzyskać więcej informacji, zobacz [Ocena ryzyka związanego z prywatnością danych i identyfikowanie elementów poufnych](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Śledzenie: przeprowadzanie ocen ryzyka i sprawdzanie oceny zgodności

Menedżer zgodności, dostępny w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności usługi Microsoft Purview</a>, zapewnia wbudowaną możliwość śledzenia ogólnych akcji poprawy i zarządzania nimi, jak również tych związanych z wieloma przepisami dotyczącymi prywatności danych, które mają zastosowanie do Ciebie.

Możesz użyć wbudowanych szablonów oceny specyficznych dla poszczególnych regulacji, w których można śledzić elementy akcji dla każdego wybranego szablonu oceny, a także wyświetlać określone mechanizmy kontroli prawnych i powiązać je z określonymi akcjami.

Aby uzyskać więcej informacji, zobacz [Używanie Menedżera zgodności do zarządzania akcjami poprawy](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Zapobieganie: Ochrona danych osobowych

Microsoft 365 zapewnia funkcje ochrony przed tożsamościami, urządzeniami i zagrożeniami, których można użyć w celu zapewnienia zgodności z przepisami dotyczącymi prywatności danych.

Aby uzyskać więcej informacji, zobacz [Używanie tożsamości, urządzenia i ochrony przed zagrożeniami w celu zapewnienia ochrony prywatności danych](information-protection-deploy-identity-device-threat.md).

W tym artykule krótko opisano, czego zwykle wymagają przepisy dotyczące prywatności danych w tych obszarach, i przedstawiono listę powiązanych rozwiązań Microsoft 365 z linkami do dodatkowych informacji ułatwiających spełnienie wymagań dotyczących implementacji.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Ochrona informacji podlegających przepisom dotyczącym prywatności danych

Przepisy dotyczące prywatności danych określają szereg mechanizmów kontroli ochrony danych osobowych, które mogą być stosowane w Twoim środowisku, w tym ponad 40 mechanizmów kontroli ochrony informacji w ramach zaledwie czterech przepisów dotyczących ochrony prywatności danych w naszym przykładowym zestawie RODO, California Consumer Protection Act (CCPA), HIPAA-HITECH (Stany Zjednoczone ustawy o ochronie prywatności w służbie zdrowia) i Brazylijskiej ustawy o ochronie danych (LGPD).

Aby uzyskać więcej informacji, zobacz [Ochrona informacji podlegających regulacjom dotyczącym prywatności danych w organizacji](information-protection-deploy-protect-information.md).

W tym artykule opisano główne schematy kontroli, które mogą być używane w celu zaspokojenia potrzeb w zakresie ochrony informacji dotyczących prywatności danych w organizacji.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Zachowaj: Zarządzanie informacjami podlegającymi przepisom dotyczącym prywatności danych

Przepisy dotyczące ochrony prywatności danych wymagają kontroli ładu informacji osobowych, które mogą być stosowane w Twoim środowisku, w tym ponad 24 mechanizmów kontroli w ramach czterech przepisów dotyczących prywatności danych w naszym przykładowym zestawie RODO, CCPA, HIPAA-HITECH i LGPD.

Aby uzyskać więcej informacji, zobacz [Zarządzanie informacjami podlegającymi przepisom dotyczącym prywatności danych w organizacji](information-protection-deploy-govern.md).

Chociaż przepisy dotyczące prywatności danych mogą być niejasne w odniesieniu do ładu&mdash; informacyjnego jako celowego przechowywania, usuwania i archiwizacji&mdash;, artykuł określa podstawowe schematy kontroli, których można użyć w celu zapewnienia ochrony prywatności danych w organizacji.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Badanie: Monitorowanie, badanie i reagowanie na zdarzenia dotyczące prywatności danych

Dostępne są Microsoft 365 funkcje ułatwiające monitorowanie, badanie i reagowanie na zdarzenia związane z prywatnością danych w organizacji podczas operacji związanych z nimi możliwości.

Posiadanie procesów, procedur i innej dokumentacji dotyczącej korzystania z tych funkcji może być ważne, aby zademonstrować zgodność z organami regulacyjnymi.

Aby uzyskać więcej informacji, zobacz [Monitorowanie zdarzeń związanych z prywatnością danych i reagowanie na nie w organizacji](information-protection-deploy-monitor-respond.md).

## <a name="training-for-administrators"></a>Szkolenie dla administratorów

Te moduły szkoleniowe z usługi Microsoft Learn mogą pomóc w poznaniu możliwości ważnych dla ochrony informacji.


#### <a name="information-protection"></a>Ochrona informacji

|Szkolenia:|Ochrona informacji o przedsiębiorstwie za pomocą Microsoft 365|
|:---|:---|
|![Teams ikona trenowania ochrony informacji.](../media/protect-enterprise-information-microsoft-365.svg)|Ochrona i zabezpieczanie informacji organizacji jest trudniejsze niż kiedykolwiek wcześniej. W ścieżce szkoleniowej Ochrona informacji o przedsiębiorstwie za pomocą Microsoft 365 omówiono sposób ochrony poufnych informacji przed przypadkowym nadmiernym udostępnianiem lub niewłaściwym użyciem, sposobu odnajdywania i klasyfikowania danych, sposobu ich ochrony za pomocą etykiet poufności oraz sposobu monitorowania i analizowania poufnych informacji w celu ochrony przed ich utratą. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Security Administrator Associate i Microsoft 365 Certified: Enterprise Administration Expert..<br><br>1 godz. ścieżka Edukacja — 5 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Tożsamość i dostęp

|Szkolenia:|Ochrona tożsamości i dostępu za pomocą Azure Active Directory|
|:---|:---|
|![Ikona trenowania tożsamości i dostępu.](../media/protect-identity-and-access-with-microsoft-365.svg)|Ścieżka szkoleniowa Dotycząca tożsamości i dostępu obejmuje najnowsze technologie tożsamości i dostępu, narzędzia do wzmacniania uwierzytelniania oraz wskazówki dotyczące ochrony tożsamości w organizacji. Technologie dostępu i tożsamości firmy Microsoft umożliwiają zabezpieczanie tożsamości organizacji, niezależnie od tego, czy jest ona lokalna, czy w chmurze, oraz umożliwianie użytkownikom bezpiecznej pracy z dowolnej lokalizacji. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Security Administrator Associate i Microsoft 365 Certified: Enterprise Administration Expert.<br><br>2 godz. 52 min — ścieżka Edukacja — 6 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-identity-overview/introduction/)