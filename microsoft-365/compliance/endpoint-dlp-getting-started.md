---
title: Wprowadzenie do ochrony przed Microsoft 365 punktu końcowego
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
ms.custom: admindeeplinkCOMPLIANCE
description: Skonfiguruj ochronę Microsoft 365 danych w punktach końcowych, aby monitorować działania związane z plikami i wdrażać akcje zabezpieczające dla tych plików do punktów końcowych.
ms.openlocfilehash: e29db57c42081349064fd690c5c9fcebee0f8045
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2021
ms.locfileid: "62999369"
---
# <a name="get-started-with-endpoint-data-loss-prevention"></a>Wprowadzenie do ochrony przed utratą danych w punkcie końcowym

Ochrona przed utratą danych w punktach końcowych firmy Microsoft (Endpoint DLP) jest częścią pakietu funkcji ochrony przed utratą danych (DLP, Data Loss Prevention) usługi Microsoft 365, który umożliwia odnajdowanie i chronianie poufnych elementów w Microsoft 365 usługach internetowych. Aby uzyskać więcej informacji na temat wszystkich usług firmy Microsoft w zakresie ochrony przed utratą danych, zobacz [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md). Aby dowiedzieć się więcej o ochronie przed utratą danych w punktach końcowych, zobacz [Informacje na temat ochrony przed utratą danych w punktach końcowych.](endpoint-dlp-learn-about.md)

Funkcja DLP punktu końcowego firmy Microsoft pozwala monitorować Windows 10 i Windows [11](device-onboarding-overview.md) oraz urządzenia [z systemem macOS *(wersja preview)*](device-onboarding-macos-overview.md) z systemem Catalina w wersji 10.15 lub wyższej. Po dojechi na urządzenie stosowane będzie DLP, które wykrywa, kiedy są używane i udostępniane poufne elementy. Zapewnia to widoczność i kontrolę potrzebną do prawidłowego ich działania i ochrony oraz zapobiegania ryzykownych zachowaniom, które mogłoby je naruszyć.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Przed rozpoczęciem pracy z zasadą DLP punktu końcowego należy potwierdzić Microsoft 365 [subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i wszystkich dodatków. Aby uzyskać dostęp do funkcji DLP punktu końcowego i korzystać z nich, musisz mieć jedną z tych subskrypcji lub dodatków.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 zgodności
- Microsoft 365 A5 zgodności
- Microsoft 365 E5 i zarządzanie informacjami
- Microsoft 365 A5 i zarządzanie informacjami

aby uzyskać szczegółowe informacje na temat [licencjonowania, zobacz Microsoft 365 licencjonowania w celu ochrony informacji.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business)

### <a name="configure-proxy-on-the-windows-10-or-windows-11-device"></a>Konfigurowanie serwera proxy na Windows 10 lub Windows 11

Jeśli dołączasz do Windows 10 lub Windows 11 urządzeń, upewnij się, że urządzenie może komunikować się z usługą DLP w chmurze. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego na stronie Ochrona informacji](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="windows-10-and-windows-11-onboarding-procedures"></a>Windows 10 i Windows 11 Procedury dołączania

Aby uzyskać ogólne wprowadzenie do dołączania Windows urządzeniach, zobacz:

- [Omówienie dołączania Windows 10 i Windows 11 Microsoft 365 urządzeniach](device-onboarding-overview.md#onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview)

Aby uzyskać szczegółowe wskazówki dotyczące dołączania Windows urządzeń, zobacz:

Temat | Opis
:---|:---
[Na urządzeniach Windows 10 lub 11 urządzeń przy użyciu zasady grupy](device-onboarding-gp.md) | Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na urządzeniach.
[Urządzenia Windows 10 lub 11 urządzeń przy użyciu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Aby wdrożyć pakiet konfiguracji na urządzeniach, możesz użyć wersji Microsoft Endpoint Configuration Manager (bieżąca gałąź) w wersji 1606 lub Microsoft Endpoint Configuration Manager (bieżąca gałąź) w wersji 1602 lub wcześniejszej.
[Na urządzeniach Windows 10 lub 11 urządzeń za pomocą narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md) | Skorzystaj z narzędzi do zarządzania urządzeniami przenośnymi Microsoft Intune, aby wdrożyć pakiet konfiguracyjnych na urządzeniu.
[Dołączanie Windows 10 lub 11 urządzeń przy użyciu skryptu lokalnego](device-onboarding-script.md) | Dowiedz się, jak wdrożyć pakiet konfiguracji na punktach końcowych za pomocą skryptu lokalnego.
[Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)](device-onboarding-vdi.md) | Dowiedz się, jak za pomocą pakietu konfiguracji skonfigurować urządzenia VDI.

## <a name="macos-onboarding-procedures"></a>Procedury dołączania do systemu macOS

Aby uzyskać ogólne wprowadzenie do dołączania urządzeń z systemem macOS, zobacz:
 
- [Dołączanie urządzeń z systemem macOS do Microsoft 365 przegląd (wersja zapoznawcza)](device-onboarding-macos-overview.md#onboard-macos-devices-into-microsoft-365-overview-preview)

Aby uzyskać szczegółowe wskazówki dotyczące dołączania do urządzeń z systemem macOS, zobacz:

Temat | Opis
:---|:---
|[Wdychaj i wydojaj urządzenia z systemem macOS Microsoft 365 rozwiązania zgodności przy użyciu usługi Intune (wersja preview)](device-onboarding-offboarding-macos-intune.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview)|W przypadku urządzeń z systemem macOS zarządzanych za pomocą usługi Intune
|[Dołączanie i wydojażanie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi Intune dla klientów programu Microsoft Defender for Endpoint (wersja preview)](device-onboarding-offboarding-macos-intune-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview) |W przypadku urządzeń z systemem macOS zarządzanych za pomocą usługi Intune, na których wdrożono program Microsoft Defender for Endpoint (MDE)
|[Urządzenia z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview) | W przypadku urządzeń macOS zarządzanych za pośrednictwem usługi JAMF Pro
|[Dołączanie i wydoszczenie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi JAMF Pro dla klientów programu Microsoft Defender for Endpoint (wersja preview)](device-onboarding-offboarding-macos-jamfpro-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview)|W przypadku urządzeń macOS zarządzanych za pośrednictwem usługi JAMF Pro, na których wdrożono program Microsoft Defender for Endpoint (MDE)

Po dojechiniu urządzenia powinno ono być widoczne na liście urządzeń i rozpocząć raportowanie działań inspekcji w Eksploratorze aktywności.

<!--### Permissions

To enable device management, the account you use must be a member of any one of these roles:

- Global admin
- Security admin
- Compliance admin

If you want to use a custom account to view the device management settings, it must be in one of these roles:

- Global admin
- Compliance admin
- Compliance data admin
- Global reader

If you want to use a custom account to access the onboarding/offboarding page, it must be in one of these roles:

- Global admin
- Compliance admin

If you want to use a custom account to turn on/off device monitoring, it must be in one of these roles:

- Global admin
- Compliance admin

Data from Endpoint DLP can be viewed in [Activity explorer](data-classification-activity-explorer.md). There are four roles that grant permission to activity explorer, the account you use for accessing the data must be a member of any one of them.

- Global admin
- Compliance admin
- Security admin
- Compliance data admin -->

<!-- ### Prepare your Windows 10/11 endpoints

Make sure that the Windows devices that you plan on deploying Endpoint DLP to meet these requirements.

1. Must be running Windows 10 x64 build 1809, Windows 11, or later.

1. Antimalware Client Version is 4.18.2009.7 or newer. Check your current version by opening Windows Security app, select the Settings icon, and then select About. The version number is listed under Antimalware Client Version. Update to the latest Antimalware Client Version by installing Windows Update KB4052623.

   > [!NOTE]
   > None of Windows Security components need to be active, you can run Endpoint DLP independent of Windows Security status, but the [Real-time protection and Behavior monitor](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)) must be enabled.

1. The following Updates are installed on Windows 10 devices

   > [!NOTE]
   > These updates are not a pre-requisite to onboard a device to Endpoint DLP, but contain fixes for important issues thus must be installed before using the product.

   - For Windows 10 1809 - KB4559003, KB4577069, KB4580390
   - For Windows 10 1903 or 1909 - KB4559004, KB4577062, KB4580386
   - For Windows 10 2004 - KB4568831, KB4577063
   - For devices running Office 2016 (and not any other Office version) - KB4577063

1. All devices must be one of these:

   - [Azure Active Directory (Azure AD) joined](/azure/active-directory/devices/concept-azure-ad-join)
   - [Hybrid Azure AD joined](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD registered](/azure/active-directory/user-help/user-help-register-device-on-network)

1. Install Microsoft Chromium Edge browser on the endpoint device to enforce policy actions for the upload to cloud activity. See, [Download the new Microsoft Edge based on Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium). If your devices use the Chrome browser, you can install the [Microsoft Compliance Extension](dlp-chrome-learn-about.md#learn-about-the-microsoft-compliance-extension) to enforce policy actions for the upload to cloud activity.

1. If you are on Monthly Enterprise Channel of Microsoft 365 Apps versions 2004-2008, there is a known issue with Endpoint DLP classifying Office content and you need to update to version 2009 or later. See [Update history for Microsoft 365 Apps (listed by date)](/officeupdates/update-history-microsoft365-apps-by-date) for current versions. To learn more about this issue, see the Office Suite section of [Release notes for Current Channel releases in 2020](/officeupdates/current-channel#version-2010-october-27).

1. If you have endpoints that use a device proxy to connect to the internet, follow the procedures in [Configure device proxy and internet connection settings for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## Prepare your macOS devices (preview)

See, [Onboard macOS devices into Microsoft 365 overview (preview)](device-onboarding-macos-overview.md#onboard-macos-devices-into-microsoft-365-overview-preview)-->

<!--## Onboarding Windows 10 and Windows 11 devices into device management

You must enable device monitoring and onboard your endpoints before you can monitor and protect sensitive items on a device. Both of these actions are done in the Microsoft 365 Compliance portal.

When you want to onboard devices that haven't been onboarded yet, you'll download the appropriate script and deploy it to those devices. Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).

If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list. Follow the [With devices onboarded into Microsoft Defender for Endpoint procedure](?source=docs&view=o365-worldwide#with-devices-onboarded-into-microsoft-defender-for-endpoint).

### Onboarding devices

In this deployment scenario, you'll onboard devices that have not been onboarded yet, and you just want to monitor and protect sensitive items from unintentional sharing on Windows 10 or Windows 11 devices.

1. Open the <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 compliance center</a>.

2. Choose **Settings** > **Device onboarding**.

   > [!NOTE]
   > While it usually takes about 60 seconds for device onboarding to be enabled, please allow up to 30 minutes before engaging with Microsoft support.

3. Choose **Devices** to open the **Devices** list. The list will be empty until you onboard devices.

4. Choose **Onboarding** to begin the onboarding process.

5. Choose the way you want to deploy to these additional devices from the **Deployment method** list and then **download package**.

   > [!div class="mx-imgBorder"]
   > ![deployment method.](../media/endpoint-dlp-getting-started-3-deployment-method.png)

6. Follow the appropriate procedures in [Onboarding tools and methods for Windows machines](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). This link takes you to a landing page where you can access Microsoft Defender for Endpoint procedures that match the deployment package you selected in step 5:

    - Onboard Windows machines using Group Policy
    - Onboard Windows machines using Microsoft Endpoint Configuration Manager
    - Onboard Windows machines using Mobile Device Management tools
    - Onboard Windows machines using a local script
    - Onboard non-persistent virtual desktop infrastructure (VDI) machines in single-session scenarios

Once done and endpoint is onboarded, it should be visible in the devices list and also start reporting audit activity logs to Activity explorer.

> [!NOTE]
> This experience is under license enforcement. Without the required license, data will not be visible or accessible.

### With devices onboarded into Microsoft Defender for Endpoint

In this scenario, Microsoft Defender for Endpoint is already deployed and there are endpoints reporting in. All these endpoints will appear in the managed devices list. You can continue to onboard new devices into Endpoint DLP to expand coverage by using the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).

1. Open the <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 compliance center</a>.

2. Open the Compliance Center settings page and choose **Enable device monitoring**.

3. Choose **Device management** to open the **Devices** list. You should see the list of devices that are already reporting in to Microsoft Defender for Endpoint.

   > [!div class="mx-imgBorder"]
   > ![device management.](../media/endpoint-dlp-getting-started-2-device-management.png)

4. Choose **Onboarding** if you need to onboard additional devices.

5. Choose the way you want to deploy to these additional devices from the **Deployment method** list and then **Download package**.

6. Follow the appropriate procedures in [Onboarding tools and methods for Windows machines](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). This link takes you to a landing page where you can access Microsoft Defender for Endpoint procedures that match the deployment package you selected in step 5:
    - Onboard Windows machines using Group Policy
    - Onboard Windows machines using Microsoft Endpoint Configuration Manager
    - Onboard Windows machines using Mobile Device Management tools
    - Onboard Windows machines using a local script
    - Onboard non-persistent virtual desktop infrastructure (VDI) machines.

Once done and endpoint is onboarded, it should be visible under the **Devices** table and also start reporting audit logs to the **Activity Explorer**.

> [!NOTE]
>This experience is under license enforcement. Without the required license, data will not be visible or accessible.


### Viewing Endpoint DLP alerts in DLP Alerts Management dashboard

1. Open the Data loss prevention page in the <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 compliance center</a> and choose Alerts.

2. Refer to the procedures in [How to configure and view alerts for your DLP policies](dlp-configure-view-alerts-policies.md) to view alerts for your Endpoint DLP policies.

### Viewing Endpoint DLP data in activity explorer

1. Open the [Data classification page](https://compliance.microsoft.com/dataclassification?viewid=overview) for your domain in the Microsoft 365 Compliance center and choose Activity explorer.

2. Refer to the procedures in [Get started with Activity explorer](data-classification-activity-explorer.md) to access and filter all the data for your Endpoint devices.

   > [!div class="mx-imgBorder"]
   > ![activity explorer filter for endpoint devices.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

## Next steps

Now that you have onboarded devices and can view the activity data in Activity explorer, you are ready to move on to your next step where you create DLP policies that protect your sensitive items.

- [Using Endpoint data loss prevention](endpoint-dlp-using.md)

## See also

- [Learn about Endpoint data loss prevention](endpoint-dlp-learn-about.md)
- [Using Endpoint data loss prevention](endpoint-dlp-using.md)
- [Learn about data loss prevention](dlp-learn-about-dlp.md)
- [Create, test, and tune a DLP policy](create-test-tune-dlp-policy.md)
- [Get started with Activity explorer](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Onboarding tools and methods for Windows machines](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 subscription](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD joined devices](/azure/active-directory/devices/concept-azure-ad-join)
- [Download the new Microsoft Edge based on Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
-->
