---
title: Urządzenia na urządzeniach bez dostępu do Internetu do programu Microsoft Defender dla punktu końcowego
ms.reviewer: ''
description: Urządzenia w urządzeniach bez dostępu do Internetu, dzięki czemu mogą przesyłać dane czujnika do czujnika programu Microsoft Defender for Endpoint
keywords: onboard, servers, vm, on-premises, oms gateway, log analytics, azure log analytics, mma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 83f0f53e2d2376975f853d826531e749732416b7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754314"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Urządzenia na urządzeniach bez dostępu do Internetu do programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Aby wboardować urządzenia bez dostępu do Internetu, musisz wykonać następujące ogólne czynności:

> [!IMPORTANT] 
> Poniższe kroki mają zastosowanie tylko do urządzeń z poprzednimi wersjami programu Windows z użyciem rozwiązania opartego na mma. Aby uzyskać więcej informacji, [zobacz Windows serwerach końcowych programu Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

> [!NOTE]
> - Serwera bramy OMS nie można używać jako serwera proxy dla odłączonych Windows lub Windows Server po skonfigurowaniu za pośrednictwem rejestru "TelemetryProxyServer" lub obiektu zasad grupy.
> - W Windows lub Windows — podczas gdy możesz użyć telemetrycznego serwera proxy, musi on wskazać standardowe urządzenie proxy lub urządzenie.
> - Ponadto program Windows lub Windows w odłączonych środowiskach musi mieć możliwość aktualizowania list zaufania certyfikatów w trybie offline za pośrednictwem wewnętrznego pliku lub serwera sieci Web.
> - Aby uzyskać więcej informacji na temat aktualizowania CRL w trybie offline, zobacz Konfigurowanie pliku lub serwera [sieci Web do pobierania plików CTL](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

Aby uzyskać więcej informacji na temat metod dołączania, zobacz następujące artykuły:
- [Wniesienie poprzednich wersji Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Onboard servers to the Microsoft Defender for Endpoint service](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)
- [Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](/microsoft-365/security/defender-endpoint/configure-proxy-internet#configure-the-proxy-server-manually-using-a-registry-based-static-proxy)

## <a name="devices-running-the-previous-mma-based-solution"></a>Urządzenia z poprzednim rozwiązaniem opartym na programie MMA

- Skonfiguruj usługę Azure Log Analytics (wcześniej znaną jako brama OMS) tak, aby działała jako serwer proxy lub centrum:
  - [Azure Log Analytics Agent](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Instalowanie i konfigurowanie programu Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) wskaż program Defender for Endpoint Workspace key & ID

[Wniesienie poprzednich wersji Windows](onboard-downlevel.md)

- Urządzenia w trybie offline w tej samej sieci usługi Azure Log Analytics
  - Skonfiguruj program MMA tak, aby wskazał:
    - Adres IP usługi Azure Log Analytics jako serwer proxy
    - Defender for Endpoint workspace key & ID

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

- W przypadku urządzeń, na których działa poprzednie rozwiązanie oparte na programie MMA, skonfiguruj bramę Azure Log Analytics Gateway (wcześniej znaną jako brama OMS) jako serwer proxy lub centrum:
    - [Brama usługi Azure Log Analytics](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [Instalowanie i konfigurowanie programu Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) wskaż program Defender for Endpoint Workspace key & ID
- Maszyny wirtualne platformy Azure w trybie offline w tej samej sieci bramy OMS
    - Konfigurowanie adresu IP usługi Azure Log Analytics jako serwera proxy
    - Identyfikator klucza obszaru roboczego usługi Azure Log Analytics & workspace
- Microsoft Defender for Cloud
    - [Obszar roboczy analizy \> dziennika zasad zabezpieczeń](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [Wykrywanie zagrożeń Zezwalaj \> u programowi Defender na dostęp do moich danych](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    Aby uzyskać więcej informacji, zobacz [Praca z zasadami zabezpieczeń](/azure/security-center/tutorial-security-policy).
