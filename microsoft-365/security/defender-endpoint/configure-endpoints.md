---
title: Narzędzia i metody dołączania do Windows urządzeniach
description: Na urządzeniach Windows, aby wysyłać dane czujnika do czujnika programu Microsoft Defender for Endpoint
keywords: Urządzenia Windows, zasady grupy, menedżer konfiguracji punktu końcowego, zarządzanie urządzeniami przenośnymi, skrypt lokalny, gp, sccm, mdm, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c4b70bfa9875d1e8c09d21e9435d8b4200555b5c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011322"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Narzędzia i metody dołączania do Windows w programie Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 zarządzanie ryzykiem w niejawnym programie testów](/microsoft-365/compliance/insider-risk-management)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Urządzenia w Twojej organizacji należy tak skonfigurować, aby usługa Defender for Endpoint może uzyskać od nich dane czujnika. Istnieją różne metody i narzędzia wdrażania, za pomocą których możesz skonfigurować urządzenia w organizacji.

Ogólnie rzecz biorąc, określisz urządzenie, Windows dołączasz, a następnie postępuj zgodnie z odpowiednim narzędziem odpowiednim dla urządzenia lub środowiska.

![Obraz narzędzi i metod dołączania](images/onboarding-config-tools.png)

## <a name="endpoint-onboarding-tools"></a>Narzędzia do dołączania punktów końcowych

W zależności od Windows, który chcesz dodać, użyj odpowiedniego narzędzia lub metody opisanej w poniższej tabeli.

Windows urządzenia | Narzędzie lub metoda dołączania
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803, 2019 i 2022</li> <li>Windows Server 2012 R2 i 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md)<br>   [zasady grupy](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/ Zarządzanie urządzeniami przenośnymi (Intune)](configure-endpoints-mdm.md)<br>    [Skrypty VDI](configure-endpoints-vdi.md) <br><br> **UWAGA**: Skrypt lokalny nadaje się do dowodu koncepcji, ale nie powinien być używany do wdrożenia produkcyjnego. W przypadku wdrożenia produkcyjnego zalecamy używanie aplikacji zasady grupy, Microsoft Endpoint Configuration Manager lub Intune.
|<ul><li> Windows Server 2008 R2 z dodatkiem SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[Wnosz poprzednie wersje programu Windows](onboard-downlevel.md) lub [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **UWAGA**: Microsoft Monitoring Agent agentem usługi Azure Log Analytics. Aby dowiedzieć się więcej, zobacz Omówienie [agenta analizy dziennika](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 z dodatkiem SP1 </li> <li>  Windows 7 z dodatkiem SP1 Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **UWAGA**: Microsoft Monitoring Agent agentem usługi Azure Log Analytics. Aby dowiedzieć się więcej, zobacz Omówienie [agenta analizy dziennika](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone, korzystając z instrukcji podanych w te Windows[.](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016)

>[!IMPORTANT]
>Aby można było zakupić usługę Microsoft Defender for Endpoint Server SKU, musisz już zakupić co najmniej dowolną z następujących subskrypcji: Windows E5/A5, Microsoft 365 E5/A5 lub Zabezpieczenia platformy Microsoft 365 E5 subskrypcji.  Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Postanowienia dotyczące produktu](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Temat|Opis
:---|:---
[Urządzenia wyniesiene przy użyciu zasady grupy](configure-endpoints-gp.md)|Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na urządzeniach.
[Urządzenia w urządzeniach w urządzeniu Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Aby wdrożyć pakiet konfiguracji na urządzeniach, możesz użyć wersji Microsoft Endpoint Manager (bieżąca gałąź) w wersji 1606 lub Microsoft Endpoint Manager (bieżąca gałąź) w wersji 1602 lub wcześniejszej.
[Urządzenia na urządzeniach mobilnych korzystające z narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md)|Skorzystaj z narzędzi do zarządzania urządzeniami przenośnymi Microsoft Intune, aby wdrożyć pakiet konfiguracyjnych na urządzeniu.
[Urządzenia w tablicy korzystające ze skryptu lokalnego](configure-endpoints-script.md)|Dowiedz się, jak wdrożyć pakiet konfiguracji na punktach końcowych za pomocą skryptu lokalnego.
[Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)|Dowiedz się, jak za pomocą pakietu konfiguracji skonfigurować urządzenia VDI.

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, zobacz Uruchamianie testu wykrywania na nowo włodarzony [program Microsoft Defender dla urządzenia końcowego](run-detection-test.md).
