---
title: Dodawanie urządzeń i profilu rozwiązania Autopilot przy użyciu przewodnika krok po kroku
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.localizationpriority: medium
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Dowiedz się, jak za pomocą rozwiązania Windows AutoPilot skonfigurować nowe Windows 10 firmowe urządzenia gotowe do użytku przez pracowników.
ms.openlocfilehash: 12e86102633ddfc19960fb561b2a626da29f0560
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314017"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>Dodawanie urządzeń i profilu rozwiązania Autopilot przy użyciu przewodnika krok po kroku

> [!NOTE]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Ta oferta oferuje dodatkowe funkcje zabezpieczeń dla urządzeń. [Dowiedz się więcej o uchcie programu Defender dla firm](../../security/defender-business/mdb-overview.md).

Korzystając z rozwiązania Windows AutoPilot, możesz skonfigurować nowe **urządzenia Windows 10 dla** swojej firmy, aby były gotowe do użycia po przysyłaniu ich pracownikom.
  
## <a name="device-requirements"></a>Wymagania dotyczące urządzeń

Urządzenia muszą spełniać następujące wymagania:
  
- Windows 10, wersja 1703 lub nowsza
    
- Nowe urządzenia, które nie zostały Windows w nowym stanie obsługi
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>Tworzenie urządzeń i profilów za pomocą przewodnika konfiguracji

Jeśli jeszcze nie utworzono grup urządzeń ani profilów, najlepiej rozpocząć pracę, korzystając z przewodnika krok po kroku. Możesz również dodawać [urządzenia i przypisywać](create-and-edit-autopilot-devices.md) [do](create-and-edit-autopilot-profiles.md) nich profile bez korzystania z przewodnika. 
  
1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. W lewym okienku nawigacji wybierz pozycję **Devices** **AutoPilot (Rozwiązania rozwiązania Devices**\> AutoPilot).

    ![W centrum administracyjnym wybierz pozycję urządzenia, a następnie pozycję AutoPilot.](../../media/AutoPilot.png)
  
2. Na stronie **AutoPilot (AutoPilot** ) kliknij lub naciśnij pozycję **Uruchom przewodnik**.
    
    ![Click Start guide for step-by-step instructions for Autopilot.](../../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. Na stronie **Upload .csv z** listą urządzeń przejdź do lokalizacji, w której znajduje się przygotowany plik .CSV, a następnie **otwórz przycisk** \> **Dalej**. Plik musi zawierać trzy nagłówki:
    
    - Kolumna A: Numer seryjny urządzenia
    
    - Kolumna B: Identyfikator produktu systemu Windows
    
    - Kolumna C: Skrót sprzętowy
    
    Możesz uzyskać te informacje od producenta sprzętu lub wygenerować plik CSV za pomocą skryptu programu [PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) . 
    
    Aby uzyskać więcej informacji, zobacz [Lista urządzeń w pliku CSV](../misc/device-list.md). Możesz również pobrać przykładowy plik na stronie **Przekazywanie pliku csv z listą urządzeń**. 
    
> [!NOTE]
> Ten skrypt używa usługi WMI do pobierania właściwości potrzebnych klientowi do zarejestrowania urządzenia w Windows Autopilot. Zwróć uwagę, że w wynikowym pliku CSV normalne jest nieuzyskanie wartości Windows IDENTYFIKATORA produktu (PKID), ponieważ nie jest to wymagane do zarejestrowania urządzenia, a wartość PKID w wyjściowym pliku CSV jest całkowicie prawidłowa. Zostanie wypełniony tylko numer seryjny i skrót sprzętowy.
    
4. Na **stronie Przypisywanie profilu** możesz wybrać istniejący profil lub utworzyć nowy. Jeśli nie masz jeszcze konta, zostanie wyświetlony monit o jego utworzenie. 
    
    Profil to kolekcja ustawień, które można zastosować do jednego urządzenia lub do grupy urządzeń.
    
    Funkcje domyślne są wymagane i ustawiane automatycznie. Funkcje domyślne to:
    
    - Pomiń Cortana, OneDrive i OEM.
    
    - Tworzenie środowiska logowania z marką Twojej firmy.
    
    - Połączenie urządzeniach, aby Azure Active Directory konta i automatycznie je zarejestrować do zarządzania przez Microsoft 365 Business Premium.
    
    Aby uzyskać więcej informacji, zobacz [Ustawienia profilu rozwiązania AutoPilot — informacje](autopilot-profile-settings.md). 
    
5. Pozostałe ustawienia to **Pomiń ustawienia prywatności** i **Nie zezwalaj użytkownikowi na zostanie administratorem lokalnym**. Oba są domyślnie **wyłączone**. 
    
    Wybierz przycisk **Dalej**.
    
6. **Wszystko gotowe oznacza** , że utworzony (lub wybrany) profil zostanie zastosowany do grupy urządzeń utworzonej po przesłaniu listy urządzeń. Ustawienia zostaną wprowadzone, gdy użytkownicy urządzenia zalogują się dalej. Wybierz pozycję **Zamknij**.

## <a name="related-content"></a>Zawartość pokrewna

[Ustawienia profilu rozwiązania AutoPilot —](autopilot-profile-settings.md) informacje (artykuł)\
[Opcje ochrony urządzeń i danych aplikacji](../devices/choose-device-security.md) (artykuł) 10 najlepszych sposobów zabezpieczania Microsoft 365 [dla firm](../security-and-compliance/secure-your-business-data.md)