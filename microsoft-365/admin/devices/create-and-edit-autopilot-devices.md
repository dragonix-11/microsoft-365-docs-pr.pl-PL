---
title: Tworzenie i edytowanie urządzeń rozwiązania AutoPilot
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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Dowiedz się, jak przekazywać urządzenia za pomocą rozwiązania AutoPilot w programie Microsoft 365 Business Premium. Profil można przypisać do urządzenia lub grupy urządzeń.
ms.openlocfilehash: 96034ca50da114adca60169ae29da5948793b498
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984090"
---
# <a name="create-and-edit-autopilot-devices"></a>Tworzenie i edytowanie urządzeń rozwiązania AutoPilot

## <a name="upload-a-list-of-devices"></a>Przekazywanie listy urządzeń

Do [przekazywania urządzeń](add-autopilot-devices-and-profile.md) możesz użyć przewodnika krok po kroku, ale możesz również przekazać urządzenia na **karcie** Urządzenia. 
  
Urządzenia muszą spełniać następujące wymagania:
  
- Windows 10, wersja 1703 lub nowsza
    
- Nowe urządzenia, które nie zostały Windows w nowym stanie obsługi

1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Devices** **AutoPilot (Rozwiązania rozwiązania Devices**\> AutoPilot).
  
2. Na stronie **AutoPilot** wybierz kartę **Urządzenia** Dodaj \> **urządzenia**.
    
    ![In the Devices tab, choose Add devices.](../../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. W **panelu Dodaj urządzenia** przejdź do pliku [CSV z listą urządzeń](../misc/device-list.md), który został przygotowany, **zapisz** \> \> **zamknij**.
    
    Możesz uzyskać te informacje od producenta sprzętu lub wygenerować plik CSV za pomocą skryptu programu [PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) . 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Przypisywanie profilu do urządzenia lub grupy urządzeń

1. Na **stronie Przygotowywanie Windows** **wybierz kartę** Urządzenia, a następnie zaznacz pole wyboru obok jednego lub większej liczby urządzeń. 
    
2. W panelu **Urządzenie** wybierz profil z listy rozwijanej **Przypisany profil**. 
    
    Jeśli nie masz jeszcze żadnych profilów, odpowiednie instrukcje znajdziesz w temacie [Tworzenie i edytowanie profilów rozwiązania AutoPilot](create-and-edit-autopilot-profiles.md). 
