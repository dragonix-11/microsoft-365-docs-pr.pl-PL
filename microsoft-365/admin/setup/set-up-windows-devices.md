---
title: Konfigurowanie Windows dla Microsoft 365 Business Premium użytkowników
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: Skonfiguruj Windows z systemem Windows 10 Pro dla Microsoft 365 Business Premium użytkowników, umożliwiając scentralizowane zarządzanie i mechanizmy kontroli zabezpieczeń.
ms.openlocfilehash: f64114ac6a117ac3eacc9b6aa9de31366e847f33
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403594"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Konfigurowanie Windows dla Microsoft 365 Business Premium użytkowników

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zanim będzie można skonfigurować urządzenia Windows dla użytkowników usługi Microsoft 365 Business Premium upewnij się, że na wszystkich urządzeniach z systemem Windows jest uruchomiona wersja Windows 10 Pro, wersja 1703 (aktualizacja dla twórców) Windows 11 Pro. 

Windows 10 Pro (lub Windows 11 Pro) jest wymaganie wstępne w przypadku wdrażania usługi Windows 10 Business, czyli zestawu usług w chmurze i funkcji zarządzania urządzeniami, który uzupełnia Windows 10 Pro i Windows 11 Pro i włącz mechanizmy scentralizowanego zarządzania i zabezpieczeń Microsoft 365 Business Premium.

[Dowiedz się więcej o wymaganiach Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro i Windows 11 Pro

Jeśli masz Windows z poprzednimi wersjami programu Windows, takimi jak Windows 7 Pro, Windows 8 Pro lub Windows 8.1 Pro, subskrypcja Microsoft 365 Business Premium uprawnia do uaktualnić te urządzenia do Windows 10 Pro lub Windows 11 Pro.
  
Aby uzyskać więcej informacji na temat uaktualniania Windows, zobacz następujące artykuły:

- [Uaktualnij Windows home do Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Uaktualnij do Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
Po uaktualnieniu zobacz Sprawdzanie, czy urządzenie jest połączone z usługą [Azure AD](#verify-the-device-is-connected-to-azure-ad) , aby sprawdzić, czy masz uaktualnienie, lub aby upewnić się, że uaktualnienie się udało.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>Dołączanie Windows do usługi Azure AD organizacji

Gdy wszystkie urządzenia Windows firmy mają Windows 10 Pro lub Windows 11 Pro, możesz dołączyć te urządzenia do usługi Azure Active Directory (Azure AD) Twojej organizacji. 

1. Na Windows wybierz logo Windows, a następnie Ustawienia logo.
  
2. W **Ustawienia** przejdź do **accountsaccess** >  **work or school** \> **Połączenie**.
  
3. Wpisz swój adres e-mail, a następnie wybierz przycisk **Dalej**.

4. Postępuj zgodnie z monitami, aby ukończyć proces.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>Sprawdzanie, czy urządzenie zostało połączone z usługą Azure AD

Aby sprawdzić stan synchronizacji, na stronie Uzyskaj  dostęp do konta służbowego w programie **Ustawienia** wybierz obszar Połączono **z _** \<organization name\> w celu udostępnienia przycisków **Informacje** i **Rozłącz**. Wybierz **pozycję Informacje** , aby uzyskać stan synchronizacji. 
  
Na stronie **Stan synchronizacji** wybierz **pozycję Synchronizuj** , aby pobrać na komputer PC najnowsze zasady zarządzania urządzeniami przenośnymi.  
  
## <a name="next-steps"></a>Następne kroki

Aby skonfigurować urządzenia przenośne, zobacz Konfigurowanie urządzeń przenośnych [dla Microsoft 365 Business Premium użytkowników](set-up-mobile-devices.md). 

Aby zwiększyć ochronę, zobacz [10 najlepszych sposobów zabezpieczania Microsoft 365 dla firm](../security-and-compliance/secure-your-business-data.md).
  
