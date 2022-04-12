---
title: Włączanie oceny Ochrona punktu końcowego w usłudze Microsoft Defender
description: Włączanie Microsoft 365 Defender laboratorium próbnego lub środowiska pilotażowego, w tym sprawdzanie stanu licencji i dołączanie punktów końcowych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
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
ms.openlocfilehash: 2acde87daaff88ec9ce7458218919342a9f1edd8
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782506"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Włączanie środowiska oceny Ochrona punktu końcowego w usłudze Microsoft Defender


Ten artykuł przeprowadzi Cię przez kroki konfigurowania środowiska ewaluacji dla Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu urządzeń produkcyjnych. 


> [!TIP]
> Ochrona punktu końcowego w usłudze Microsoft Defender jest również wyposażony w laboratorium ewaluacyjne w produkcie, w którym można dodawać wstępnie skonfigurowane urządzenia i uruchamiać symulacje w celu oceny możliwości platformy. Laboratorium oferuje uproszczone środowisko konfiguracji, które może pomóc szybko zademonstrować wartość Ochrona punktu końcowego w usłudze Microsoft Defender w tym wskazówki dotyczące wielu funkcji, takich jak zaawansowane wyszukiwanie zagrożeń i analiza zagrożeń. Aby uzyskać więcej informacji, zobacz [Evaluate capabilities (Ocena możliwości](../defender-endpoint/evaluation-lab.md)). <br> Główną różnicą między wskazówkami podanymi w tym artykule a laboratorium ewaluacyjnym jest to, że środowisko ewaluacji używa urządzeń produkcyjnych, podczas gdy laboratorium ewaluacji używa urządzeń nieprodukcyjnych. 

Aby włączyć ocenę dla Ochrona punktu końcowego w usłudze Microsoft Defender, wykonaj następujące kroki.

:::image type="content" source="../../media/defender/m365-defender-endpoint-eval-enable-steps.png" alt-text="Kroki włączania Ochrona punktu końcowego w usłudze Microsoft Defender w środowisku ewaluacji usługi Microsoft Defender" lightbox="../../media/defender/m365-defender-endpoint-eval-enable-steps.png":::

- [Krok 1. Sprawdzanie stanu licencji](#step-1-check-license-state)
- [Krok 2. Dołączanie punktów końcowych](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Krok nr 1. Sprawdzanie stanu licencji

Najpierw należy sprawdzić stan licencji, aby sprawdzić, czy została ona prawidłowo aprowizowana. Można to zrobić za pośrednictwem centrum administracyjnego lub portalu **Microsoft Azure**.


1. Aby wyświetlić licencje, przejdź do **portalu Microsoft Azure** i przejdź do [sekcji licencji portalu Microsoft Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="../../media/defender/atp-licensing-azure-portal.png" alt-text="Strona Licencjonowanie platformy Azure w portalu Microsoft 365 Defender" lightbox="../../media/defender/atp-licensing-azure-portal.png":::

1. Alternatywnie w centrum administracyjnym przejdź do pozycji **RozliczeniaSubskrypcje** > .

    Na ekranie zostaną wyświetlone wszystkie aprowizowane licencje i ich bieżący **stan**.

    :::image type="content" source="../../media/defender/atp-billing-subscriptions.png" alt-text="Strona Licencje rozliczeniowe w portalu Microsoft Azure" lightbox="../../media/defender/atp-billing-subscriptions.png":::
    

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Krok nr 2. Dołączanie punktów końcowych przy użyciu dowolnego z obsługiwanych narzędzi do zarządzania

Po sprawdzeniu, czy stan licencji został prawidłowo zainicjowany, możesz rozpocząć dołączanie urządzeń do usługi. 

W celu oceny Ochrona punktu końcowego w usłudze Microsoft Defender zalecamy wybranie kilku Windows urządzeń do przeprowadzenia oceny.

Możesz użyć dowolnego z obsługiwanych narzędzi do zarządzania, ale Intune zapewnia optymalną integrację. Aby uzyskać więcej informacji, zobacz [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

W temacie [Planowanie wdrożenia](../defender-endpoint/deployment-strategy.md) opisano ogólne kroki, które należy wykonać w celu wdrożenia usługi Defender for Endpoint.  

Obejrzyj to wideo, aby zapoznać się z szybkim omówieniem procesu dołączania i poznać dostępne narzędzia i metody.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Opcje narzędzia dołączania

W poniższej tabeli wymieniono dostępne narzędzia oparte na punkcie końcowym, który należy dołączyć.

Punkt końcowy | Opcje narzędzi
:---|:---
**Windows** | [Skrypt lokalny (maksymalnie 10 urządzeń),](../defender-endpoint/configure-endpoints-script.md) [zasady grupy](../defender-endpoint/configure-endpoints-gp.md), [Microsoft Endpoint Manager/ Mobile Menedżer urządzeń](../defender-endpoint/configure-endpoints-mdm.md), [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md), [skrypty VDI](../defender-endpoint/configure-endpoints-vdi.md), [ Integracja z Microsoft Defender dla Chmury](../defender-endpoint/configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)
**macOS** | [Skrypty lokalne](../defender-endpoint/mac-install-manually.md), [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [Mobile Zarządzanie urządzeniami](../defender-endpoint/mac-install-with-other-mdm.md)
**Serwer z systemem Linux** | [Skrypt lokalny](../defender-endpoint/linux-install-manually.md),  [Puppet](../defender-endpoint/linux-install-with-puppet.md),  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [Oparte na aplikacji](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Następny krok
[Konfigurowanie pilotażu dla Ochrona punktu końcowego w usłudze Microsoft Defender](eval-defender-endpoint-pilot.md)
 
Wróć do przeglądu Ochrona punktu końcowego w usłudze Microsoft Defender [oceny](eval-defender-endpoint-overview.md)

Wróć do przeglądu [oceny i pilotażowego Microsoft 365 Defender](eval-overview.md)
