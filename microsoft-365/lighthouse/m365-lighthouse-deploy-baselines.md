---
title: Wdrażanie Microsoft 365 Lighthouse bazowych
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse dowiedz się, jak wdrożyć Microsoft 365 Lighthouse bazowe.
ms.openlocfilehash: fa443fa025f0a1ffba6a230427797755611328a3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324632"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Wdrażanie Microsoft 365 Lighthouse bazowych 

Microsoft 365 Lighthouse bazowe umożliwiają wdrażanie standardowych konfiguracji dzierżaw zarządzanych w celu zabezpieczania użytkowników, urządzeń i danych w dzierżawach klientów. Istnieje siedem domyślnych konfiguracji bazowych, standardowo z usługą Lighthouse:

- Wymaganie uwierzytelniania wieloskładnikowego dla administratorów
- Wymaganie uwierzytelniania wieloskładnikowego dla użytkowników końcowych
- Blokuj starsze uwierzytelnianie
- Konfigurowanie rejestracji urządzeń w usłudze Microsoft Endpoint Manager — Dołączanie do usługi Azure AD
- Konfigurowanie zasad programu antywirusowego Defender Windows 10 i nowszych
- Konfigurowanie Zapory programu Microsoft Defender do Windows 10 i nowszych
- Konfigurowanie zasad zgodności dla Windows 10 i nowszych

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że Twoja dzierżawa Twoich klientów spełnia wymagania wymienione w te sposób[: Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="learn-more-about-the-default-baseline"></a>Dowiedz się więcej o domyślnym planie bazowym

Wybierz **pozycję Linie bazowe** w okienku nawigacji po lewej stronie w aplikacji Latarnia morska, aby otworzyć stronę Linie bazowe. Zobaczysz, że domyślny plan bazowy został już dodany do grupy Dzierżawa domyślna (wszyscy dzierżawcy). Aby wyświetlić domyślne konfiguracje planu bazowego, wybierz pozycję **Wyświetl plan bazowy** , aby otworzyć stronę Domyślny plan bazowy. Konfiguracje są wymienione jako kroki wdrożenia. Wybierz dowolny z kroków wdrażania, aby wyświetlić szczegóły wdrożenia i wpływ na użytkowników.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Zrzut ekranu przedstawiający stronę Domyślny plan bazowy.":::

## <a name="deploy-a-baseline-configuration"></a>Wdrażanie konfiguracji bazowej  

1. W lewym okienku nawigacji w latarni morskiej wybierz  pozycję Dzierżawy, aby wyświetlić listę dzierżaw wnoszone.

2. Wybierz dzierżawę, w której chcesz wdrożyć konfigurację podstawową.

3. Wybierz **kartę Plany** wdrażania, aby wyświetlić wszystkie kroki wdrożenia z planu bazowego, które zostały dodane do planu wdrażania dzierżawy.

4. Wybierz krok wdrożenia, aby otworzyć stronę kroku wdrażania.

5. Wybierz **pozycję Recenzja i Zastosuj** , aby zastosować wybrany krok wdrożenia do dzierżawy. Jeśli krok wdrażania wskazuje "Ta akcja wymaga czynności ręcznej", wykonaj tę czynność ręcznie, aby krok wdrażania został poprawnie zastosowany.

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie wdrażania standardowych konfiguracji dzierżawy](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) przy użyciu planu bazowego (artykuł)\
[Omówienie Microsoft 365 dzierżaw w latarni morskiej](m365-lighthouse-tenants-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse faq](m365-lighthouse-faq.yml) (artykuł)\
[Konfigurowanie Microsoft 365 Lighthouse zabezpieczeń portalu](m365-lighthouse-configure-portal-security.md) (artykuł) 