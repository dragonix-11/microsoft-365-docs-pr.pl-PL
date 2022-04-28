---
title: Konfigurowanie urządzeń Windows dla użytkowników Microsoft 365 Business Premium
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
description: Skonfiguruj urządzenia Windows z systemem Windows 10 Pro dla użytkowników Microsoft 365 Business Premium, umożliwiając scentralizowane zarządzanie i mechanizmy kontroli zabezpieczeń.
ms.openlocfilehash: 57db37f73d2b9145f7c4fb9c1ee1005318c629d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096231"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Konfigurowanie urządzeń Windows dla użytkowników Microsoft 365 Business Premium

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed skonfigurowaniem urządzeń Windows dla użytkowników Microsoft 365 Business Premium upewnij się, że wszystkie urządzenia Windows działają Windows 10 Pro, wersja 1703 (aktualizacja dla twórców) lub Windows 11 Pro. 

Windows 10 Pro (lub Windows 11 Pro) to warunek wstępny wdrażania Windows 10 Business, który jest zestawem usług w chmurze i funkcji zarządzania urządzeniami, które uzupełniają Windows 10 Pro i Windows 11 Pro i włącza scentralizowane mechanizmy zarządzania i kontroli zabezpieczeń Microsoft 365 Business Premium.

[Dowiedz się więcej o wymaganiach dotyczących Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro i Windows 11 Pro

Jeśli masz Windows urządzenia z poprzednimi wersjami Windows, takimi jak Windows 7 Pro, Windows 8 Pro lub Windows 8.1 Pro, twoja subskrypcja Microsoft 365 Business Premium uprawnia Cię do uaktualnić te urządzenia do Windows 10 Pro lub Windows 11 Pro.
  
Aby uzyskać więcej informacji na temat uaktualniania urządzeń Windows, zobacz następujące artykuły:

- [Uaktualnij Windows Home do Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Uaktualnianie do Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
Po uaktualnieniu zobacz [Sprawdzanie, czy urządzenie jest połączone z usługą Azure AD](#verify-the-device-is-connected-to-azure-ad) , aby sprawdzić, czy uaktualnienie zostało uaktualnione, lub aby upewnić się, że uaktualnienie zadziałało.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>Dołączanie urządzeń Windows do usługi Azure AD organizacji

Gdy wszystkie urządzenia Windows firmy działają Windows 10 Pro lub Windows 11 Pro, możesz dołączyć te urządzenia do Azure Active Directory organizacji (Azure AD). 

1. Na urządzeniu Windows wybierz logo Windows, a następnie ikonę Ustawienia.
  
2. W **Ustawienia** przejdź do pozycji **KontaAdeks**  >  służbowe lub szkolne \> **Połączenie**.
  
3. Wpisz swój adres e-mail, a następnie wybierz pozycję **Dalej**.

4. Postępuj zgodnie z monitami, aby ukończyć proces.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>Sprawdzanie, czy urządzenie zostało połączone z usługą Azure AD

Aby sprawdzić stan synchronizacji, na stronie **Dostęp do pracy lub szkoły** w **Ustawienia** wybierz obszar **Połączono** z _ _ \<organization name\> , aby uwidoczniać przyciski **Informacje** i **Rozłącz**. Wybierz pozycję **Informacje,** aby uzyskać stan synchronizacji. 
  
Na stronie **Stan synchronizacji** wybierz pozycję **Synchronizuj** , aby pobrać najnowsze zasady zarządzania urządzeniami przenośnymi na komputer.  
  
## <a name="next-steps"></a>Następne kroki

Aby skonfigurować urządzenia przenośne, zobacz [Konfigurowanie urządzeń przenośnych dla użytkowników Microsoft 365 Business Premium](set-up-mobile-devices.md), 

Aby zwiększyć ochronę, zobacz [Top 10 ways to secure Microsoft 365 for business plans (10 najlepszych sposobów zabezpieczania Microsoft 365 dla planów biznesowych](../security-and-compliance/secure-your-business-data.md)).
  

