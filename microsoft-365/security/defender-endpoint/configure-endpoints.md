---
title: Narzędzia i metody dołączania dla urządzeń Windows
description: Dołącz urządzenia Windows, aby mogły wysyłać dane czujnika do czujnika Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: Dołączanie urządzeń Windows, zasad grupy, menedżera konfiguracji punktu końcowego, zarządzania urządzeniami przenośnymi, skryptu lokalnego, gp, sccm, mdm, intune
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
ms.openlocfilehash: fbc5a0981a6318d767252e968e45874d889aee85
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949106"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Narzędzia i metody dołączania dla urządzeń Windows w usłudze Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona przed utratą danych punktu końcowego (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Zarządzanie ryzykiem wewnętrznym](/microsoft-365/compliance/insider-risk-management)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Urządzenia w organizacji muszą być skonfigurowane tak, aby usługa Defender for Endpoint mogła pobierać z nich dane czujników. Istnieją różne metody i narzędzia wdrażania, których można użyć do konfigurowania urządzeń w organizacji.

Ogólnie rzecz biorąc, zidentyfikujesz urządzenie Windows, które dołączasz, a następnie zastosujesz odpowiednie narzędzie do urządzenia lub środowiska.

:::image type="content" source="images/onboarding-config-tools.png" alt-text="Narzędzia i metody dołączania" lightbox="images/onboarding-config-tools.png":::

## <a name="endpoint-onboarding-tools"></a>Narzędzia dołączania punktów końcowych

W zależności od punktu końcowego Windows, który chcesz dołączyć, użyj odpowiedniego narzędzia lub metody opisanej w poniższej tabeli.

urządzenie Windows | Narzędzie lub metoda dołączania
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 i 2019 oraz 2022</li> <li>Windows Server 2012 R2 i 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Skrypt lokalny (maksymalnie 10 urządzeń)](configure-endpoints-script.md)<br>   [Zasady grupy](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/ Mobile Zarządzanie urządzeniami (Intune)](configure-endpoints-mdm.md)<br>    [Skrypty VDI](configure-endpoints-vdi.md) <br><br> **UWAGA**: Skrypt lokalny jest odpowiedni do weryfikacji koncepcji, ale nie powinien być używany do wdrożenia produkcyjnego. W przypadku wdrożenia produkcyjnego zalecamy używanie zasady grupy, Microsoft Endpoint Configuration Manager lub Intune.
|<ul><li> Windows Server 2008 R2 z dodatkiem SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[Dołączanie poprzednich wersji Windows](onboard-downlevel.md) lub [Microsoft Defender dla Chmury](/azure/security-center/security-center-wdatp) <br><br> **UWAGA**: Microsoft Monitoring Agent jest teraz agentem usługi Azure Log Analytics. Aby dowiedzieć się więcej, zobacz [Omówienie agenta usługi Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 z dodatkiem SP1 </li> <li>  Windows 7 Pro SP1 </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **UWAGA**: Microsoft Monitoring Agent jest teraz agentem usługi Azure Log Analytics. Aby dowiedzieć się więcej, zobacz [Omówienie agenta usługi Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) należy dołączyć Windows Server 2016 i Windows Server 2012 R2, korzystając z instrukcji zawartych w temacie [Dołączanie serwerów Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>Aby kwalifikować się do zakupu jednostki SKU serwera Ochrona punktu końcowego w usłudze Microsoft Defender, musisz już kupić łączne minimum spośród następujących, Windows E5/A5, Microsoft 365 E5/A5 lub Zabezpieczenia platformy Microsoft 365 E5 licencji subskrypcji.  Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Warunki produktu](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Temat|Opis
:---|:---
[Dołączanie urządzeń przy użyciu zasady grupy](configure-endpoints-gp.md)|Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na urządzeniach.
[Dołączanie urządzeń przy użyciu Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Do wdrożenia pakietu konfiguracji na urządzeniach można użyć Microsoft Endpoint Manager (current branch) w wersji 1606 lub Microsoft Endpoint Manager (current branch) w wersji 1602 lub starszej.
[Dołączanie urządzeń przy użyciu narzędzi mobile Zarządzanie urządzeniami](configure-endpoints-mdm.md)|Użyj narzędzi Zarządzanie urządzeniami mobile lub Microsoft Intune, aby wdrożyć pakiet konfiguracji na urządzeniu.
[Dołączanie urządzeń przy użyciu skryptu lokalnego](configure-endpoints-script.md)|Dowiedz się, jak używać skryptu lokalnego do wdrażania pakietu konfiguracji w punktach końcowych.
[Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](configure-endpoints-vdi.md)|Dowiedz się, jak skonfigurować urządzenia VDI przy użyciu pakietu konfiguracji.

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy urządzenie jest prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md).
