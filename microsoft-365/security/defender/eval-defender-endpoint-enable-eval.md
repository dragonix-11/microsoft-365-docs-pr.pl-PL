---
title: Włączanie usługi Microsoft Defender do oceny punktu końcowego
description: Włączanie środowiska Microsoft 365 Defender próbnego lub pilotażowego, w tym sprawdzanie stanu licencji i punktów końcowych dołączania
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
ms.openlocfilehash: 846fd6854b8e2dcb408aaa55348380bb91c6b907
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013683"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Włączanie programu Microsoft Defender dla środowiska oceny punktu końcowego


Ten artykuł zawiera instrukcje konfigurowania środowiska oceny dla programu Microsoft Defender dla punktu końcowego przy użyciu urządzeń produkcyjnych. 


> [!TIP]
> Program Microsoft Defender for Endpoint oferuje również laboratorium oceny w produkcie, w którym można dodawać wstępnie skonfigurowane urządzenia i uruchamiać symeony w celu oceny możliwości platformy. Laboratorium oferuje uproszczone środowisko ustawień, które może szybko zademonstrować wartość programu Microsoft Defender for Endpoint, w tym wskazówki dotyczące wielu funkcji, takich jak zaawansowana analiza wyszukiwania i analizy zagrożeń. Aby uzyskać więcej informacji, zobacz [Ocenianie możliwości](../defender-endpoint/evaluation-lab.md). <br> Główna różnica między wskazówkami w tym artykule a laboratorium oceny jest taka, że w środowisku oceny są używane urządzenia produkcyjne, natomiast w laboratorium oceny są używane urządzenia nieprodukcji. 

Aby włączyć ocenę dla programu Microsoft Defender dla punktu końcowego, należy wykonać poniższe czynności.

![Kroki włączania programu Microsoft Defender dla punktu końcowego w środowisku oceny programu Microsoft Defender.](../../media/defender/m365-defender-endpoint-eval-enable-steps.png)

- [Krok 1. Sprawdź stan licencji](#step-1-check-license-state)
- [Krok 2. Onboard endpoints](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Krok nr 1. Sprawdź stan licencji

Najpierw musisz sprawdzić stan licencji, aby sprawdzić, czy została ona poprawnie aprowizowana. Możesz to zrobić za pośrednictwem centrum administracyjnego lub portalu **Microsoft Azure administracyjnego**.


1. Aby wyświetlić licencje, przejdź do portalu **Microsoft Azure i** przejdź do sekcji Microsoft Azure [licencji portalu](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products) internetowego.

   ![Obraz strony Licencjonowanie platformy Azure.](../../media/defender/atp-licensing-azure-portal.png)

1. Ewentualnie w centrum administracyjnym przejdź do **strony** **RozliczeniaSubskrypcje** > .

    Na ekranie zobaczysz wszystkie licencje z inicjowaniem obsługi administracyjnej i ich bieżący **stan**.

    ![Obraz licencji rozliczeniowych.](../../media/defender/atp-billing-subscriptions.png)

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Krok nr 2. Onboard endpoints using any of the supported management tools

Po sprawdzeniu, czy stan licencji został poprawnie aprowowany, możesz uruchomić urządzenia wnoszące do usługi. 

Na potrzeby oceny programu Microsoft Defender dla punktu końcowego zalecamy wybranie kilku urządzeń Windows w celu przeprowadzenia oceny.

Możesz korzystać z dowolnego z obsługiwanych narzędzi do zarządzania, ale usługa Intune zapewnia optymalną integrację. Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu Microsoft Defender dla punktu końcowego w programie Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

W [temacie Planowanie wdrożenia](../defender-endpoint/deployment-strategy.md) przedstawiono ogólne czynności, które należy wykonać, aby wdrożyć usługę Defender dla punktu końcowego.  

Obejrzyj ten klip wideo, aby szybko poznać proces dołączania i poznać dostępne narzędzia i metody.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Opcje narzędzia dołączania

W poniższej tabeli wymieniono dostępne narzędzia na podstawie punktu końcowego, który trzeba do dyspozycji.

Punkt końcowy | Opcje narzędzia
:---|:---
**Windows** | [Skrypt lokalny (do 10 urządzeń)](../defender-endpoint/configure-endpoints-script.md)[, zasady grupy](../defender-endpoint/configure-endpoints-gp.md), [Microsoft Endpoint Manager/ Menedżer](../defender-endpoint/configure-endpoints-mdm.md) urządzeń przenośnych, [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md) skrypty [VDI](../defender-endpoint/configure-endpoints-vdi.md), Integracja z programem [Microsoft Defender dla chmury](../defender-endpoint/configure-server-endpoints.md#integration-with-azure-defender)
**macOS** | [Lokalne skrypty](../defender-endpoint/mac-install-manually.md), [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [usługi JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [Zarządzanie urządzeniami przenośnymi](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [Skrypt lokalny](../defender-endpoint/linux-install-manually.md),  [Szamit](../defender-endpoint/linux-install-with-puppet.md),  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [Oparte na aplikacji](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Następny krok
[Konfigurowanie programu pilotażowego programu Microsoft Defender dla punktu końcowego](eval-defender-endpoint-pilot.md)
 
Powrót do omówieniem [Szacowanie programu Microsoft Defender dla punktu końcowego](eval-defender-endpoint-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
