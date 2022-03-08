---
title: Tworzenie i edytowanie profilów rozwiązania AutoPilot
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: Dowiedz się, jak utworzyć profil rozwiązania AutoPilot i zastosować go do urządzenia, a także edytować lub usunąć profil albo usunąć profil z urządzenia.
ms.openlocfilehash: 91df801fb1833c9bfe5f1112e6a3cd5fc8efcf5d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313849"
---
# <a name="create-and-edit-autopilot-profiles"></a>Tworzenie i edytowanie profilów rozwiązania AutoPilot

> [!NOTE]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Ta oferta oferuje dodatkowe funkcje zabezpieczeń dla urządzeń. [Dowiedz się więcej o uchcie programu Defender dla firm](../../security/defender-business/mdb-overview.md).

## <a name="create-a-profile"></a>Tworzenie profilu

Profil dotyczy urządzenia lub grupy urządzeń.
  
1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Devices** **AutoPilot (Rozwiązania rozwiązania Devices**\> AutoPilot).
  
2. Na stronie **AutoPilot (Autopilot** ) wybierz **kartę Profile** , Utwórz \> **profil**.
    
3. Na **stronie Tworzenie profilu** wprowadź nazwę profilu, która ułatwia jej identyfikację, na przykład Marketing. Włącz to ustawienie, a następnie wybierz pozycję **Zapisz**. Aby uzyskać więcej informacji o ustawieniach profilu rozwiązania AutoPilot, zobacz [Ustawienia profilu rozwiązania AutoPilot — informacje](autopilot-profile-settings.md).
    
    ![Enter name and turn on settings in the Create profile panel.](../../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Stosowanie profilu do urządzenia

Po utworzeniu profilu możesz go zastosować do urządzenia lub grupy urządzeń. Możesz wybrać istniejący profil w przewodniku krok [](add-autopilot-devices-and-profile.md) po kroku i zastosować go do nowych urządzeń lub zamienić istniejący profil dla urządzenia lub grupy urządzeń. 
  
1. Na stronie **Przygotowywanie systemu Windows** wybierz kartę **Urządzenia**. 
    
2. Zaznacz pole wyboru obok nazwy urządzenia, a następnie **w panelu** Urządzenie wybierz profil z listy rozwijanej Przypisany **profil** Zapisz. \>
    
    ![In the Device panel, select an Assigned profile to apply it.](../../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Edytowanie, usuwanie lub czyszczenie profilu

Profil przypisany do urządzenia można zaktualizować, nawet jeśli już przekazano urządzenie użytkownikowi. Gdy urządzenie łączy się z Internetem, pobiera najnowszą wersję profilu w procesie konfiguracji. Jeśli użytkownik przywróci domyślne ustawienia fabryczne na urządzeniu, ponownie pobierze ono najnowsze aktualizacje profilu. 
  
### <a name="edit-a-profile"></a>Edytowanie profilu

1. Na stronie **Przygotowywanie systemu Windows** wybierz kartę **Profile**. 
    
2. Zaznacz pole wyboru obok nazwy urządzenia i **w panelu** Profil zaktualizuj dowolne z dostępnych **ustawień Zapisz**\>.
    
    Jeśli zrobisz to, zanim urządzenie użytkownika połączy się z Internetem, profil zostanie zastosowany w procesie konfiguracji.
    
### <a name="delete-a-profile"></a>Usuwanie profilu

1. Na stronie **Przygotowywanie systemu Windows** wybierz kartę **Profile**. 
    
2. Zaznacz pole wyboru obok nazwy urządzenia i w **panelu** Profil wybierz pozycję **Usuń profil Zapisz** \> **.**
    
    Usunięty profil zostaje odłączony od urządzenia lub grupy urządzeń, do których go przypisano.
    
### <a name="remove-a-profile"></a>Czyszczenie profilu

1. Na stronie **Przygotowywanie systemu Windows** wybierz kartę **Urządzenia**. 
    
2. Zaznacz pole wyboru obok nazwy urządzenia, a następnie **w panelu** Urządzenie wybierz pozycję **Brak** z listy rozwijanej  **Przypisany profil Zapisz**.\>
    
## <a name="see-also"></a>Zobacz też

[10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](../security-and-compliance/secure-your-business-data.md)