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
ms.openlocfilehash: be25acb8414705c48a8763a0530ec2a70565de83
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313597"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Sprawdzanie poprawności ustawień ochrony urządzeń dla Windows 10 PC

> [!NOTE]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Ta oferta oferuje dodatkowe funkcje zabezpieczeń dla urządzeń. [Dowiedz się więcej o uchcie programu Defender dla firm](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Sprawdzanie, Windows 10 urządzenia są ustawione

Po [skonfigurowaniu zasad urządzeń](protection-settings-for-windows-10-pcs.md) może upłynieć kilka godzin, aż te zasady zajdą w życie na urządzeniach użytkowników. Aby potwierdzić, że zasady te obowiązywały, możesz Windows Ustawienia ekranów na urządzeniach użytkowników. Ponieważ użytkownicy nie będą mogli modyfikować ustawień aktualizacji Windows i ustawień Program antywirusowy Microsoft Defender na ich Windows 10 urządzeniach, wiele opcji zostanie wyszarzeni.
  
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
[Konfigurowanie urządzeń dla komputerów Windows 10](protection-settings-for-windows-10-pcs.md)
 [Najedna 10](../security-and-compliance/secure-your-business-data.md) sposobów zabezpieczania Microsoft 365 dla firm