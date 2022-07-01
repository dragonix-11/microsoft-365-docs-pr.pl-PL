---
title: Zarządzaj ustawieniami konfiguracji usługi ochrony punktu końcowego w usłudze Microsoft Defender na urządzeniach z programem Microsoft Endpoint Manager
description: Dowiedz się, jak włączyć ustawienia zabezpieczeń w usłudze Microsoft Endpoint Manager za pośrednictwem Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: zarządzanie urządzeniami, konfigurowanie urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender, microsoft Endpoint Manager
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2c19352d584bedc5acd94f9984242a2c50d2fcf3
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573926"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Zarządzaj ustawieniami konfiguracji usługi ochrony punktu końcowego w usłudze Microsoft Defender na urządzeniach z programem Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach przy użyciu usługi Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Zarządzanie zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender jest funkcją dla urządzeń, które nie są zarządzane przez Endpoint Manager firmy Microsoft w celu odbierania konfiguracji zabezpieczeń usługi Microsoft Defender bezpośrednio z Endpoint Manager.


Aby uzyskać więcej informacji na temat zarządzania konfiguracją zabezpieczeń, w tym wymagań wstępnych, obsługiwanych platform i nie tylko, zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach z usługą Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Obejrzyj ten film wideo, aby dowiedzieć się, jak zarządzać konfiguracją zabezpieczeń dla Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą usługi Microsoft Endpoint Manager.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVq]

[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Ta funkcja jest wdrażana stopniowo. 

Aby uzyskać więcej informacji na temat zarządzania konfiguracją zabezpieczeń, zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach za pomocą usługi Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Jeśli wystąpią problemy z rejestracją, zobacz [Rozwiązywanie problemów z dołączaniem do usługi Security Configuration Management](troubleshoot-security-config-mgt.md).

> [!NOTE]
> Ta funkcja nie ma zastosowania do urządzeń, które zostały już zarejestrowane w usłudze Microsoft Endpoint Manager (Intune lub Configuration Manager). Urządzenia zarejestrowane w Intune będą nadal otrzymywać zasady za pośrednictwem ustalonego kanału zarządzania.

## <a name="identify-onboarded-devices"></a>Identyfikowanie dołączonych urządzeń

Wykonaj poniższe kroki, aby sprawdzić, czy punkty końcowe pomyślnie ukończyły proces dołączania usługi Security Management for Ochrona punktu końcowego w usłudze Microsoft Defender.

1.  Sprawdź, czy urządzenie jest wyświetlane w sekcji Spis urządzeń [w Microsoft 365 Defender](https://security.microsoft.com/).

2.  W [portalu usługi Azure Active Directory](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/) sprawdź, czy urządzenie zostało pomyślnie zarejestrowane.

3.  W [centrum microsoft Endpoint Manager Administracja](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview) sprawdź, czy urządzenie zostało pomyślnie zarejestrowane, przeglądając je w sekcji **Urządzenia > Wszystkie urządzenia**.


## <a name="offboard-devices"></a>Odłączanie urządzeń
Aby odłączyć urządzenia, które zostały dołączone za pośrednictwem usługi Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Odłącz urządzenia z usługi Ochrona punktu końcowego w usłudze Microsoft Defender](offboard-machines.md).

>[!NOTE]
>Odłączanie [spowoduje wyłączenie ochrony przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) , jeśli jest włączona.

## <a name="troubleshooting-security-management"></a>Rozwiązywanie problemów z zarządzaniem zabezpieczeniami 
Aby rozwiązać problemy z zarządzaniem zabezpieczeniami w Ochrona punktu końcowego w usłudze Microsoft Defender rejestracji, zobacz [Rozwiązywanie problemów z dołączaniem związanych z usługą Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>Temat pokrewny
- [Rozwiązywanie problemów z dołączaniem związanych z usługą Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-security-config-mgt.md)
- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach przy użyciu usługi Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
