---
title: Weryfikowanie ustawień ochrony aplikacji dla komputerów Windows 10
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
description: Dowiedz się, jak sprawdzić, czy ustawienia ochrony aplikacji Microsoft 365 dla firm weszły w życie na urządzeniach Windows 10 użytkowników.
ms.openlocfilehash: cbb26461da9fcc73f57d219c36ef04d97e7fc209
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317558"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Weryfikowanie ustawień ochrony urządzeń dla komputerów Windows 10

> [!NOTE]
> Microsoft Defender dla Firm jest wdrażana dla klientów Microsoft 365 Business Premium od 1 marca 2022 r. Ta oferta zapewnia dodatkowe funkcje zabezpieczeń dla urządzeń. [Dowiedz się więcej o usłudze Defender dla Firm](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Sprawdź, czy ustawiono zasady Windows 10 urządzeń

Po [skonfigurowaniu zasad urządzeń](../../business-premium/m365bp-protection-settings-for-windows-10-pcs.md) może upłynąć do kilku godzin, aż zasady wejdą w życie na urządzeniach użytkowników. Możesz potwierdzić, że zasady weszły w życie, przeglądając różne ekrany Windows Ustawienia na urządzeniach użytkowników. Ponieważ użytkownicy nie będą mogli modyfikować ustawień Windows Update i Program antywirusowy Microsoft Defender na swoich urządzeniach Windows 10, wiele opcji zostanie wyszarzone.
  
1. Przejdź do **obszaru** \> Ustawienia **Zaktualizuj &amp; Windows Update** \>  \> **Opcje ponownego uruchamiania** i upewnij się, że wszystkie ustawienia są wyszarzone.

    ![Wszystkie opcje ponownego uruchamiania są wyszarzone.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Przejdź do **obszaru** \> Ustawienia **Zaktualizuj &amp; zabezpieczenia** \> **Windows Update** \> **Opcje zaawansowane** i upewnij się, że wszystkie ustawienia są wyszarzone.

    ![Windows Opcje aktualizacji zaawansowanych są wyszarzone.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Przejdź do **Ustawienia** \> **Aktualizuj &amp; opcje zabezpieczeń** \> **Windows Update** \> **Opcje** \> zaawansowane **Wybierz sposób dostarczania aktualizacji**.

    Upewnij się, że widzisz komunikat (na czerwono), że niektóre ustawienia są ukryte lub zarządzane przez organizację, a wszystkie opcje są wyszarzone.

    ![Wybierz sposób dostarczania aktualizacji strona wskazuje ustawienia są ukryte lub zarządzane przez organizację.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Aby otworzyć centrum zabezpieczeń Windows Defender, przejdź do **Ustawienia** \> **Update &amp; security** \> **Windows Defender** \> kliknij pozycję **Otwórz Windows Defender** Ustawienia ochrony antywirusowej ochrona przed \> zagrożeniami wirusami **w usłudze Security Center &amp;** \> **&amp;**.

5. Sprawdź, czy wszystkie opcje są wyszarzone.

    ![Ustawienia Ochrony przed wirusami i zagrożeniami są wyszarzone.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 dokumentacji i zasobów biznesowych](/admin)

[Ustawianie konfiguracji urządzeń dla Windows 10 rozwiązań PCsBest](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 [dotyczących zabezpieczania Microsoft 365 dla planów biznesowych](../../admin/security-and-compliance/secure-your-business-data.md)
