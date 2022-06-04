---
title: Zabezpieczanie urządzeń z systemem Windows
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
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
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: 21e5551f-fa35-4f13-9418-f80d668b6a2b
description: Dowiedz się więcej na temat konfigurowania ustawień domyślnych zasad urządzeń, które każde urządzenie z systemem Windows otrzyma po zalogowaniu się do konta służbowego.
ms.openlocfilehash: 5ac09788d609752d12a6ae6efadfa8739c5a4f9a
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893088"
---
# <a name="secure-windows-devices"></a>Zabezpieczanie urządzeń z systemem Windows

Celem jest skonfigurowanie ustawień, które są częścią domyślnych zasad urządzenia dla systemu Windows 10 lub 11. Wszyscy użytkownicy, którzy łączą urządzenie z systemem Windows, w tym urządzenia przenośne i komputery, logując się przy użyciu konta służbowego, otrzymają te ustawienia automatycznie. Zalecane jest zaakceptowanie domyślnych zasad podczas instalacji i dodanie w późniejszym terminie zasad dotyczących konkretnych grup użytkowników.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed skonfigurowaniem urządzeń z systemem Windows dla użytkowników platformy Microsoft 365 Business Premium upewnij się, że na wszystkich urządzeniach z systemem Windows 10 Pro w wersji 1703 (Aktualizacja dla twórców) lub Windows 11 Pro.

Windows 10 Pro (lub Windows 11 Pro) to warunek wstępny wdrażania systemu Windows 10 Business, który jest zestawem usług w chmurze i funkcji zarządzania urządzeniami, które uzupełniają systemy Windows 10 Pro i Windows 11 Pro oraz umożliwiają scentralizowane zarządzanie i mechanizmy kontroli zabezpieczeń platformy Microsoft 365 Business Premium.

[Dowiedz się więcej o wymaganiach dotyczących platformy Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro i Windows 11 Pro

Jeśli masz urządzenia z systemem Windows z poprzednimi wersjami systemu Windows, takimi jak Windows 7 Pro, Windows 8 Pro lub Windows 8.1 Pro, Subskrypcja platformy Microsoft 365 Business Premium uprawnia do uaktualnienia tych urządzeń do systemu Windows 10 Pro lub Windows 11 Pro.
  
Aby uzyskać więcej informacji na temat uaktualniania urządzeń z systemem Windows, zobacz następujące artykuły:

- [Uaktualnianie systemu Windows Home do systemu Windows 10 lub Windows 11 Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Uaktualnianie do systemu Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)

<!---
Could not find the Win11 equivalent upgrade link.
---> 
  
## <a name="secure-your-windows-10-and-11-devices"></a>Zabezpieczanie urządzeń z systemem Windows 10 i 11

Domyślnie wszystkie ustawienia są **Włączone**. Dostępne są następujące ustawienia:<br/><br/>

|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Ochrona komputerów przed wirusami i innymi zagrożeniami przy użyciu programu antywirusowego Microsoft Defender  <br/> |Wymaga włączenia programu antywirusowego Microsoft Defender w celu ochrony komputerów przed zagrożeniami związanymi z połączeniem z Internetem.  <br/> |
|Chroń komputery przed zagrożeniami internetowymi w programie Microsoft Edge  <br/> |Włącza w programie Microsoft Edge ustawienia ułatwiające ochronę użytkowników przed złośliwymi witrynami i złośliwą zawartością do pobrania.  <br/> |
|Pomóż chronić pliki i foldery na komputerach przed nieautoryzowanym dostępem za pomocą funkcji BitLocker  <br/> |Funkcja BitLocker chroni dane przez szyfrowanie dysków twardych komputera i ochronę przed ujawnieniem danych w przypadku utraty lub kradzieży komputera. Aby uzyskać więcej informacji, zobacz [Funkcja BitLocker — często zadawane pytania](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Wyłącz ekran urządzenia po takim czasie bezczynności  <br/> |Zapewnia bezpieczeństwo danych firmowych podczas bezczynności użytkownika. Jeśli użytkownik pracuje w miejscu publicznym, na przykład kawiarni, i odejdzie na chwilę od urządzenia lub skupi uwagę na czymś innym, przypadkowe osoby mogą obejrzeć zawartość ekranu. To ustawienie pozwala kontrolować czas bezczynności użytkownika, po którym ekran zostanie wyłączony.  <br/> |

## <a name="next-objective"></a>Następny cel

[Zarządzanie urządzeniami z systemem Windows](m365bp-manage-windows-devices.md)
