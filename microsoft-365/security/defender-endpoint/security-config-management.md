---
title: Zarządzaj ustawieniami konfiguracji programu Microsoft Defender for Endpoint na urządzeniach za pomocą programu Microsoft Endpoint Manager
description: Dowiedz się, jak włączyć ustawienia zabezpieczeń w u Microsoft Endpoint Manager programie Microsoft Defender for Endpoint.
keywords: zarządzanie urządzeniami, konfigurowanie programu Microsoft Defender dla urządzeń końcowych, Microsoft Endpoint Manager
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a8a57b14480c45ddbc154d71bc4f2ded315c83ae
ms.sourcegitcommit: 0251d5c6cb141055c93c83a402c3dc52c7a70dcc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2021
ms.locfileid: "62996855"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Zarządzaj ustawieniami konfiguracji programu Microsoft Defender for Endpoint na urządzeniach za pomocą programu Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Zarządzanie programem Microsoft Defender for Endpoint na urządzeniach za pomocą Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



[!include[Prerelease information](../../includes/prerelease.md)]


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Zarządzanie zabezpieczeniami dla programu Microsoft Defender for Endpoint to funkcja dla urządzeń, które nie są zarządzane przez Microsoft Endpoint Manager, Microsoft Intune lub Microsoft Endpoint Configuration Manager, do odbierania konfiguracji zabezpieczeń dla programu Microsoft Defender bezpośrednio z Endpoint Manager.


Aby uzyskać więcej informacji na temat zarządzania konfiguracją zabezpieczeń, w tym wymagań wstępnych, obsługiwanych platform i nie tylko, zobacz Zarządzanie programem [Microsoft Defender for Endpoint na](/mem/intune/protect/mde-security-integration) urządzeniach z systemem Microsoft Endpoint Manager.



[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Ta funkcja jest wprowadzana stopniowo. 

Aby uzyskać więcej informacji na temat zarządzania konfiguracją zabezpieczeń, zobacz [Zarządzanie programem Microsoft Defender dla punktu końcowego na urządzeniach z systemem Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Jeśli wystąpią problemy z rejestracją, zobacz [Rozwiązywanie problemów z konfiguracją zabezpieczeń podczas dołączania](troubleshoot-security-config-mgt.md).

> [!NOTE]
> Ta funkcja nie dotyczy urządzeń, które zostały już zarejestrowane w usłudze Microsoft Endpoint Manager (Intune lub Menedżer konfiguracji). Urządzenia zarejestrowane w usłudze Intune nadal będą otrzymywać zasady za pośrednictwem ustanowionego kanału zarządzania.

## <a name="identify-onboarded-devices"></a>Identyfikowanie urządzeń podłączonych do urządzenia

Skorzystaj z poniższych kroków, aby sprawdzić, czy punkty końcowe pomyślnie ukończyły proces dołączania do usługi Zarządzanie zabezpieczeniami programu Microsoft Defender for Endpoint.

1.  Sprawdź, czy urządzenie jest wyświetlane w sekcji Spis urządzeń [w](https://security.microsoft.com/) Microsoft 365 Defender.

2.  W portalu [Azure Active Directory upewnij](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/) się, że urządzenie zostało pomyślnie zarejestrowane.

3.  W centrum [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview) administracyjnego sprawdź, czy urządzenie zostało pomyślnie zarejestrowane, szukając go w sekcji Urządzenia **> Wszystkie** urządzenia.


## <a name="offboard-devices"></a>Urządzenia przenośne
Aby uzyskać informacje o urządzeniach wynoszowanych za pośrednictwem zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint, zobacz Urządzenia wynoszone z usługi [Microsoft Defender for Endpoint](offboard-machines.md).

>[!NOTE]
>Wyniesienie [spowoduje wyłączenie ochrony przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) , jeśli jest włączona.

## <a name="troubleshooting-security-management"></a>Rozwiązywanie problemów z zarządzaniem zabezpieczeniami 
Aby rozwiązać problemy z zarządzaniem zabezpieczeniami dla programu Microsoft Defender dla rejestrowania punktu końcowego, zobacz Rozwiązywanie problemów dotyczących dołączania związanych z zarządzaniem zabezpieczeniami programu [Microsoft Defender dla punktu końcowego](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>Temat pokrewny
- [Rozwiązywanie problemów z dołączaniem związanych z zarządzaniem zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego](troubleshoot-security-config-mgt.md)
- [Zarządzanie programem Microsoft Defender for Endpoint na urządzeniach za pomocą Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
