---
title: Porównanie ustawień zasad zgodności urządzeń
f1.keywords: NOCSH
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych używających Microsoft 365 Lighthouse, dowiedz się, jak porównać ustawienia zasad zgodności urządzeń.
ms.openlocfilehash: 5e4fc396e2ea1e1cce576f6064f4239179db33cc
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2022
ms.locfileid: "63014804"
---
# <a name="compare-device-compliance-policy-settings"></a>Porównanie ustawień zasad zgodności urządzeń

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse umożliwia wyświetlanie zasad zgodności dla całej dzierżawy w jednym widoku. Możesz zapewnić bezpieczeństwo i standaryzację w całej dzierżawie, porównując zasady. Możesz filtrować widoki, aby wyświetlić skonfigurowane ustawienia (a nie skonfigurowane ustawienia), ustawienia inne niż w ich konfiguracjach lub zgodne ustawienia. Możesz również wyszukać określone ustawienia, aby sprawdzić, jak są one porównywane przez zasady.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że urządzenia mają licencję Microsoft Intune i są zarejestrowane w programie Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Porównanie ustawień zasad

1. W lewym okienku nawigacji w aplikacji Lighthouse wybierz pozycję **Urządzenia**.

2. Wybierz **kartę** Zasady.

3. Z **listy rozwijanej** Filtry wybierz system operacyjny lub platformę.

   > [!NOTE]
   > Zasady można porównywać tylko z tym samym systemem operacyjnym lub platformą.

4. Z listy filtrowanych wybierz maksymalnie trzy zasady, które chcesz porównać.

5. Wybierz **pozycję Porównaj**.

Możesz filtrować wyniki, aby Ustawienia **inne**, Ustawienia **lub** **Skonfigurowane ustawienia**.

## <a name="configure-a-policy-setting"></a>Konfigurowanie ustawienia zasad

1. W lewym okienku nawigacji w aplikacji Lighthouse wybierz pozycję **Urządzenia**.

2. Wybierz **kartę** Zasady.

3. Wybierz nazwę zasad z listy.

4. W okienku Szczegóły zasad wybierz pozycję **Wyświetl te zasady w Microsoft Endpoint Manager**.

5. W programie MEM edytuj ustawienia zasad zgodnie z potrzebami.

## <a name="next-steps"></a>Następne kroki

W czasie dostosowań zasad należy ocenić zmiany pod względem bieżących ustawień planu bazowego. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania standardowych konfiguracji dzierżawy za pomocą planu bazowego](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>Zawartość pokrewna

[Co to jest rejestracja urządzeń w usłudze Intune?](/mem/intune/enrollment/device-enrollment) (article)  
[Ustawianie reguł dla urządzeń, które zarządzasz](/mem/intune/protect/device-compliance-get-started) za pomocą usługi Intune, przy użyciu zasad zgodności (artykuł)  
[Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) planu bazowego (artykuł)
