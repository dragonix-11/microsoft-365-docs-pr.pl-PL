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
ms.openlocfilehash: c4cef0b966e1c35d5b8d4f282e5eeee4cb76a998
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2022
ms.locfileid: "63014806"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Wdrażanie Microsoft 365 Lighthouse bazowych 

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse bazowe umożliwiają wdrażanie standardowych konfiguracji dzierżaw zarządzanych w celu zabezpieczania użytkowników, urządzeń i danych w dzierżawach klientów. Istnieje sześć domyślnych konfiguracji planu bazowego standardowo z usługą Lighthouse:

- Wymaganie uwierzytelniania wieloskładnikowego dla administratorów
- Wymaganie uwierzytelniania wieloskładnikowego dla użytkowników końcowych
- Blokuj starsze uwierzytelnianie
- Konfigurowanie rejestracji urządzeń w usłudze Microsoft Endpoint Manager — Dołączanie do usługi Azure AD
- Konfigurowanie zasad programu antywirusowego Defender Windows urządzeniach
- Konfigurowanie zasad zgodności na Windows urządzeniach

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że Twoja dzierżawa Twoich klientów spełnia wymagania wymienione w te sposób[: Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="learn-more-about-the-default-baseline"></a>Dowiedz się więcej o domyślnym planie bazowym

Wybierz **pozycję Linie bazowe** w lewym okienku nawigacji, aby otworzyć stronę Linie bazowe. Zobaczysz, że domyślny plan bazowy został już dodany do grupy Dzierżawa domyślna (wszyscy dzierżawcy). Aby wyświetlić domyślne konfiguracje planu bazowego, wybierz pozycję **Wyświetl plan bazowy** , aby otworzyć stronę Domyślny plan bazowy. Konfiguracje są wymienione jako kroki wdrożenia. Wybierz dowolny z kroków wdrażania, aby wyświetlić szczegóły wdrożenia i wpływ na użytkowników.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Zrzut ekranu przedstawiający stronę Domyślny plan bazowy.>.":::

## <a name="deploy-a-baseline-configuration"></a>Wdrażanie konfiguracji bazowej  

1. W lewym okienku nawigacji w latarni morskiej wybierz  pozycję Dzierżawy, aby wyświetlić listę dzierżaw wnoszone.

2. Wybierz dzierżawę, w której chcesz wdrożyć konfigurację podstawową.

3. Wybierz **kartę Plany** wdrażania, aby wyświetlić wszystkie kroki wdrożenia z planu bazowego, które zostały dodane do planu wdrażania dzierżawy.

4. Wybierz krok wdrożenia, aby otworzyć stronę kroku wdrażania.

5. Wybierz **pozycję Zastosuj** , aby zastosować wybrany krok wdrożenia do dzierżawy. Jeśli krok wdrażania wskazuje "Ta akcja wymaga czynności ręcznej", wykonaj tę czynność ręcznie, aby krok wdrażania został poprawnie zastosowany.

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie wdrażania standardowych konfiguracji dzierżawy](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) przy użyciu planu bazowego (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
