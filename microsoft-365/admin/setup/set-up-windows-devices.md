---
title: Konfigurowanie Windows dla Microsoft 365 Business Premium użytkowników
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
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
ms.openlocfilehash: 40577f2130c185f8a98a3c8f873da80233e56cf0
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998945"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Konfigurowanie Windows dla Microsoft 365 Business Premium użytkowników

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zanim będzie można skonfigurować Windows dla użytkowników Microsoft 365 Business Premium, upewnij się, że na Windows działają Windows 10 Pro w wersji 1703 (aktualizacja dla twórców). Windows 10 Pro stanowi wymaganie wstępne w przypadku wdrażania usługi Windows 10 Business, która jest zestawem usług w chmurze i funkcji zarządzania urządzeniami, który uzupełnia program Windows 10 Pro i umożliwia mechanizmy scentralizowanego zarządzania i zabezpieczeń Microsoft 365 Business Premium.
  
Jeśli masz Windows z systemem Windows 7 Pro, Windows 8 Pro lub Windows 8.1 Pro, subskrypcja Microsoft 365 Business Premium uprawnia do uaktualnienia Windows 10 wersji.
  
Aby uzyskać więcej informacji na temat uaktualniania urządzeń z systemem Windows do systemu Windows 10 Pro (aktualizacja dla twórców), wykonaj czynności opisane w tym temacie: [Uaktualnianie urządzeń z systemem Windows do systemu Windows Pro (aktualizacja dla twórców)](../../business-video/upgrade.md).
  
Zobacz [Sprawdzanie, czy urządzenie zostało połączone z usługą Azure AD](#verify-the-device-is-connected-to-azure-ad) , aby sprawdzić, czy masz uaktualnienie, lub aby się upewnić, że uaktualnienie się nie posunie.

## <a name="watch-connect-your-pc-to-microsoft-365-business"></a>Obejrzyj: Połączenie komputera w celu Microsoft 365 Firm

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3yXh3] 

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).
  
## <a name="join-windows-10-devices-to-your-organizations-azure-ad"></a>Dołączanie urządzeń z systemem Windows 10 do usługi Azure AD organizacji

Jeśli wszystkie Windows w organizacji zostały uaktualnione do usługi Windows 10 Pro Creators Update lub są już uruchomione w aktualizacji dla twórców programu Windows 10 Pro, możesz dołączyć te urządzenia do aplikacji Azure Active Directory organizacji. Po dołączeniu urządzenia zostaną automatycznie uaktualnione do wersji Windows 10 Business, która jest częścią Microsoft 365 Business Premium subskrypcji.
  
### <a name="for-a-brand-new-or-newly-upgraded-windows-10-pro-device"></a>Całkowicie nowe lub nowo uaktualnione urządzenie z systemem Windows 10 Pro

W przypadku całkowicie nowego urządzenia z systemem Windows 10 Pro (aktualizacja dla twórców) lub w przypadku urządzenia, które zostało uaktualnione do systemu Windows 10 Pro (aktualizacja dla twórców), ale nie przeszło konfiguracji urządzenia z systemem Windows 10, wykonaj poniższe czynności.
  
1. Postępuj zgodnie z instrukcjami konfiguracji urządzenia z systemem Windows 10 do momentu przejścia do strony **Jak chcesz skonfigurować?**. 
    
    ![Na stronie Jak chcesz skonfigurować wybierz pozycję Skonfiguruj dla organizacji.](../../media/1b0b2dba-00bb-4a99-a729-441479220cb7.png)
  
2. W tym miejscu **wybierz pozycję Skonfiguruj dla organizacji, a** następnie wprowadź nazwę użytkownika i hasło dla Microsoft 365 Business Premium. 
    
3. Dokończ konfigurację urządzenia z systemem Windows 10.
    
   Gdy to zrobisz, użytkownik będzie połączony z usługą Azure AD organizacji. Zobacz [Sprawdzanie, czy urządzenie zostało połączone z usługą Azure AD](#verify-the-device-is-connected-to-azure-ad), aby się upewnić. 
  
### <a name="for-a-device-already-set-up-and-running-windows-10-pro"></a>Urządzenie już skonfigurowane z uruchomionym systemem Windows 10 Pro

 **Połącz użytkowników z usługą Azure AD:**
  
1. Na komputerze Windows użytkownika z systemem Windows 10 Pro wersja 1703 (aktualizacja dla twórców) (zobacz wymagania [wstępne, kliknij](../security-and-compliance/pre-requisites-for-data-protection.md) logo Windows, Ustawienia ikonę.
  
   ![W menu Start kliknij ikonę Windows Ustawienia.](../../media/74e1ce9a-1554-4761-beb9-330b176e9b9d.png)
  
2. W oknie **Ustawienia** wybierz opcję **Konta**.
  
   ![W Windows Ustawienia przejdź do konta.](../../media/472fd688-d111-4788-9fbb-56a00fbdc24d.png)
  
3. Na stronie **Twoje informacje** kliknij pozycję **Uzyskaj dostęp do miejsca pracy lub nauki** \> **Połącz**.
  
   ![Wybierz Połączenie w obszarze Uzyskaj dostęp do pracy lub nauki.](../../media/af3a4e3f-f9b9-4969-b3e2-4ef99308090c.png)
  
4. W oknie dialogowym **Konfigurowanie konta służbowego** w sekcji **Alternatywne działania** wybierz pozycję **Dołącz to urządzenie do usługi Azure Active Directory**.
  
   ![Kliknij pozycję Dołącz to urządzenie, aby Azure Active Directory.](../../media/fb709a1b-05a9-4750-9cb9-e097f4412cba.png)
  
5. On the **Let's get you signed in** page, enter your work or school account \> **Next**.
  
   On the **Enter password** page, enter your password \> **Sign in**.
  
   ![Wprowadź służbowy lub szkolny adres e-mail na stronie Czas się zalogować.](../../media/f70eb148-b1d2-4ba3-be38-7317eaf0321a.png)
  
6. Na stronie **Upewnij się, że to Twoja organizacja** sprawdź, czy informacje są poprawne, a następnie wybierz pozycję **Dołącz**.
  
   Na **ekranie Wszystko jest już ustawione!** wybierz pozycję **Gotowe**.
  
   ![Na ekranie Upewnij się, że to Twoja organizacja wybierz pozycję Dołącz.](../../media/c749c0a2-5191-4347-a451-c062682aa1fb.png)
  
Jeśli masz pliki przesłane do usługi OneDrive dla Firm, zsynchronizuj je z powrotem. Jeśli profil i pliki zostały przeniesione za pomocą narzędzia innej firmy, zsynchronizuj też te dane z nowym profilem.
  
## <a name="verify-the-device-is-connected-to-azure-ad"></a>Sprawdzanie, czy urządzenie zostało połączone z usługą Azure AD

Aby sprawdzić stan synchronizacji, na stronie Uzyskaj  dostęp do konta służbowego w programie **Ustawienia** wybierz obszar Połączono **z _** \<organization name\> w celu udostępnienia przycisków **Informacje** i **Rozłącz**. Wybierz **pozycję Informacje** , aby uzyskać stan synchronizacji. 
  
Na stronie **Stan synchronizacji** wybierz **pozycję Synchronizuj** , aby pobrać na komputer PC najnowsze zasady zarządzania urządzeniami przenośnymi.
  
Aby rozpocząć korzystanie z Microsoft 365 Business Premium konta, przejdź do Windows **Start**, kliknij prawym przyciskiem myszy bieżący obraz konta, a następnie wybierz **pozycję Przełącz konto**. Zaloguj się przy użyciu adresu e-mail i hasła organizacji.
  
![Kliknij przycisk Informacje, aby wyświetlić stan synchronizacji.](../../media/818f7043-adbf-402a-844a-59d50034911d.png)
  
## <a name="verify-the-pc-is-upgraded-to-windows-10-business"></a>Sprawdzanie, czy komputer został uaktualniony do Windows 10 Business

Sprawdź, czy urządzenia dołączane do Windows 10 Azure AD zostały uaktualnione do Windows 10 Business w ramach twojej Microsoft 365 Business Premium subskrypcji.
  
1. Wybierz pozycję **Ustawienia** \> **System** \> **Informacje**.
    
2. Potwierdź, że w polu **Wersja** jest wskazywany system **Windows 10 Business**.
    
    ![Verify that Windows edition is Windows 10 Business.](../../media/ff660fc8-d3ba-431b-89a5-f5abded96c4d.png)
  
## <a name="next-steps"></a>Następne kroki

Aby skonfigurować urządzenia przenośne, zobacz Konfigurowanie urządzeń przenośnych dla użytkowników usługi [Microsoft 365 Business Premium](set-up-mobile-devices.md). Aby skonfigurować zasady ochrony urządzeń lub ochrony aplikacji, zobacz Zarządzanie usługą [Microsoft 365 dla firm](/admin/index.yml).
  
## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 szkoleniowe klipy wideo dla firm](../../business-video/index.yml) (strona linku)
