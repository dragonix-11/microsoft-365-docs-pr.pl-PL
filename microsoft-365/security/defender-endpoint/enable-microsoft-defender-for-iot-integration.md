---
title: Włączanie integracji usługi Microsoft Defender for IoT w programie Microsoft Defender for Endpoint
description: Włączanie integracji usługi Microsoft Defender dla IoT w celu uzyskania widoczności w skoncentrowaniu się na urządzeniach IoT/OT w obszarach sieci, w których nie wdrożono funkcji MDE
keywords: Enable siem connector, siem, connector, security information and events
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 70d8586cb8f8babcdc709a67632f32103e9420ce
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996406"
---
# <a name="enable-microsoft-defender-for-iot-integration"></a>Włączanie integracji z usługą Microsoft Defender dla IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Program Microsoft Defender for Endpoint może teraz zintegrować się z usługą Microsoft Defender dla IoT. Ta integracja rozszerza możliwości odnajdowania urządzeń o funkcje monitorowania bez agenta udostępniane przez program Microsoft Defender dla IoT. Pomoże to zabezpieczyć urządzenia IoT przedsiębiorstwa połączone z sieciami IT, takimi jak urządzenia VoIP (Voice over Internet Protocol), drukarki i kamery. Umożliwia organizacjom korzystanie z jednego zintegrowanego rozwiązania, które zabezpiecza całą swoją infrastrukturę IoT i technologii operacyjnej (OT). Aby uzyskać więcej informacji, zobacz [Enterprise ochrony sieci IoT](/azure/defender-for-iot/organizations/overview-eiot).

Dzięki włączeniu tej integracji usługa Microsoft Defender for Endpoint zwiększa widoczność, ułatwiając znajdowanie, identyfikowanie i zabezpieczanie urządzeń IoT w Twojej sieci. Urządzenia IoT odkryte przez program Microsoft Defender dla IoT lub Program Microsoft Defender for Endpoint zostaną automatycznie zsynchronizowane w obu portalach. Zapewni to pojedynczy ujednolicony widok Twojego pełnego spisu usług OT/IoT wraz z pozostałymi urządzeniami IT (stacjami roboczymi, serwerami i urządzeniami przenośnymi).

Usługa Microsoft Defender dla IoT zawiera również wdrażalny czujnik sieci, który zapewnia dodatkowe źródło danych. Skonfigurowanie czujnika sieci w ramach integracji zapewnia najbardziej pełny widok urządzeń IoT i OT, w szczególności segmentów sieci, w których czujników programu Microsoft Defender for Endpoint nie ma i gdy pracownicy zdalnie uzyskają dostęp do informacji.

## <a name="prerequisites"></a>Wymagania wstępne

Aby włączyć usługę Microsoft Defender dla IoT, użytkownik musi mieć następujące role:

- Administrator globalny dzierżawy w Azure Active Directory
- Administrator zabezpieczeń dla subskrypcji platformy Azure, która będzie używana na rzecz integracji usługi Microsoft Defender dla IoT

## <a name="enabling-the-microsoft-defender-for-iot-integration"></a>Włączanie integracji z usługą Microsoft Defender dla IoT

1. W okienku nawigacji portalu wybierz [https://security.microsoft.com](https://security.microsoft.com/) pozycję Ustawienia  \> **Odnajdowanie urządzeń** \> **Program Microsoft Defender dla systemu IoT**.

    ![Obraz konfiguracji integracji z usługą IoT.](images/enable-defender-for-iot.png)

2. **Wybierz subskrypcję platformy Azure** z listy rozwijanej dostępnych subskrypcji w Twojej Azure Active Directory dzierżawie i wybierz pozycję **Zapisz**.

## <a name="set-up-a-network-sensor"></a>Konfigurowanie czujnika sieci

Po wybraniu subskrypcji platformy Azure możesz dodać czujnik sieci.

Aby dodać czujnik sieci, w obszarze **Skonfiguruj czujniki sieci** wybierz link **Microsoft Defender for IoT** . To prowadzi do procesu konfiguracji czujnika w aplikacji Azure Portal. Aby uzyskać więcej informacji, zobacz [Zarządzanie czujnikiami za pomocą usługi Defender dla IoT w portalu Azure Portal](/azure/defender-for-iot/organizations/how-to-manage-sensors-on-the-cloud).

## <a name="turn-off-subscription-integration"></a>Wyłączanie integracji subskrypcji

Integrację subskrypcji platformy Azure możesz wyłączyć z usługi Microsoft Defender dla ustawień IoT w [https://security.microsoft.com](https://security.microsoft.com/) portalu. Po wyłączenie subskrypcji nie zobaczysz już urządzeń IoT wykrytych przez usługę Microsoft Defender dla IoT w spisie urządzeń programu Microsoft Defender for Endpoint.

## <a name="see-also"></a>Zobacz też

- [Omówienie odnajdowania urządzeń](configure-device-discovery.md)
- [Odnajdowanie urządzeń — często zadawane pytania](device-discovery-faq.md)
