---
title: Porównanie ustawień zasad zgodności urządzeń w Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak porównać ustawienia zasad zgodności urządzeń.
ms.openlocfilehash: 1ea7a278a58cd6d864c32ab7b25569ae463658f9
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022775"
---
# <a name="compare-device-compliance-policy-settings-in-microsoft-365-lighthouse"></a>Porównanie ustawień zasad zgodności urządzeń w Microsoft 365 Lighthouse

Microsoft 365 Lighthouse umożliwia wyświetlanie zasad zgodności w dzierżawach w jednym widoku. Możesz zwiększyć bezpieczeństwo i standaryzację w dzierżawach, porównując zasady. Widoki można filtrować, aby wyświetlić ustawienia, które zostały skonfigurowane (w porównaniu z ustawieniami, które pozostały nie skonfigurowane), ustawienia różniące się konfiguracjami lub ustawieniami zgodnymi. Możesz również wyszukać określone ustawienia, aby zobaczyć, jak są one porównywane między zasadami.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że urządzenia mają licencję Microsoft Intune i są zarejestrowane w Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Porównanie ustawień zasad

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Urządzenia**.

2. Wybierz kartę **Zasady** .

3. Z listy rozwijanej **Filtry** wybierz system operacyjny lub platformę.

   > [!NOTE]
   > Zasady można porównać tylko z tym samym systemem operacyjnym lub platformą.

4. Z filtrowanej listy wybierz maksymalnie trzy zasady, które chcesz porównać.

5. Wybierz pozycję **Porównaj**.

Możesz filtrować wyniki, aby wyświetlić **Ustawienia, które różnią się**, **Ustawienia zgodne** lub **Skonfigurowane ustawienia**.

## <a name="configure-a-policy-setting"></a>Konfigurowanie ustawienia zasad

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Urządzenia**.

2. Wybierz kartę **Zasady** .

3. Z listy wybierz nazwę zasad.

4. W okienku Szczegóły zasad wybierz pozycję **Wyświetl te zasady w Microsoft Endpoint Manager**.

5. W programie MEM edytuj ustawienia zasad zgodnie z potrzebami.

## <a name="next-steps"></a>Następne kroki

Podczas wprowadzania korekt zasad upewnij się, że oceniasz zmiany względem bieżących ustawień punktu odniesienia. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu punktów odniesienia](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>Zawartość pokrewna

[Co to jest rejestracja urządzeń w Intune?](/mem/intune/enrollment/device-enrollment) (artykuł)  
[Używanie zasad zgodności do ustawiania reguł dla urządzeń zarządzanych za pomocą Intune](/mem/intune/protect/device-compliance-get-started) (artykuł)  
[Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu Microsoft 365 Lighthouse planów bazowych](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artykuł)
