---
title: Sprawdzanie poprawności ustawień ochrony aplikacji na Windows 10 PC
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
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
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Dowiedz się, jak sprawdzić Microsoft 365 ustawienia ochrony aplikacji dla firm miały wpływ na ustawienia ochrony aplikacji Windows 10 urządzeniach.
ms.openlocfilehash: 311da3efec8cd3ad57e722aea5a8c3888d1af7b0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983804"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Sprawdzanie poprawności ustawień ochrony urządzeń dla Windows 10 PC

## <a name="verify-that-windows-10-device-policies-are-set"></a>Sprawdzanie, Windows 10 urządzenia są ustawione

Po [skonfigurowaniu zasad urządzeń](protection-settings-for-windows-10-pcs.md) może upłynieć kilka godzin, aż te zasady zajdą w życie na urządzeniach użytkowników. Aby potwierdzić, że zasady te obowiązywały, możesz Windows Ustawienia ekranów na urządzeniach użytkowników. Ponieważ użytkownicy nie będą mogli modyfikować ustawień aktualizacji Windows i Program antywirusowy Windows Defender na swoich urządzeniach Windows 10, wiele opcji zostanie wyszarowanych.
  
1. Przejdź do **Ustawienia** \> **Opcje &amp; ponownego** \> **uruchamiania Windows** \> aktualizacji i upewnij się, że wszystkie ustawienia są wyszarowane. 
    
    ![Wszystkie opcje Uruchom ponownie są wyszarowane.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Przejdź do **Ustawienia** \> **Opcje &amp;** **aktualizacji Windows** \> \> Zaawansowane i upewnij się, że wszystkie ustawienia są wyszarowane. 
    
    ![Windows opcje aktualizacji zaawansowanych są wyszarowane.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Przejdź do **Ustawienia** \> **Opcje &amp;** **zaawansowane aktualizacji Windows** \> \> Opcje **aktualizacji** \> Wybierz **sposób dostarczenia aktualizacji**.
    
    Upewnij się, że widzisz komunikat (kolor czerwony), że niektóre ustawienia są ukryte lub zarządzane przez Twoją organizację, a wszystkie opcje są wyszarowane.
    
    ![Strona Wybieranie sposobu dostarczenia aktualizacji wskazuje, że ustawienia są ukryte lub zarządzane przez Organizację.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Aby otworzyć Centrum zabezpieczeń Windows Defender, przejdź do Ustawienia aktualizacji zabezpieczeń i  \> **&amp;** \> **Windows Defender** \> pozycję Otwórz Windows Defender **Ochronę** \> **&amp;** \> **&amp; wątku wirusów ustawieniami ochrony przed zagrożeniami antywirusowymi**. 
    
5. Sprawdź, czy wszystkie opcje są wyszarowane. 
    
    ![Ustawienia ochrony przed wirusami i zagrożeniami są wyszarowane.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 i zasoby dla firm](/admin)\
[Konfigurowanie komputerów PC z systemem Windows 10](protection-settings-for-windows-10-pcs.md)
