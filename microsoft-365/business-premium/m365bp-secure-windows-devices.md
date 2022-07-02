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
ms.openlocfilehash: a9fd78ef37aed3663572b7049ae150e85916e41b
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607416"
---
# <a name="secure-windows-devices"></a>Zabezpieczanie urządzeń z systemem Windows

Celem jest skonfigurowanie ustawień, które są częścią domyślnych zasad urządzenia dla Windows 10 lub 11. Wszyscy użytkownicy, którzy łączą urządzenie z systemem Windows, w tym urządzenia przenośne i komputery, logując się przy użyciu konta służbowego, otrzymają te ustawienia automatycznie. Zalecane jest zaakceptowanie domyślnych zasad podczas instalacji i dodanie w późniejszym terminie zasad dotyczących konkretnych grup użytkowników.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed skonfigurowaniem urządzeń z systemem Windows dla użytkowników Microsoft 365 Business Premium upewnij się, że wszystkie urządzenia z systemem Windows działają Windows 10 Pro.

Windows 10 Pro jest wymaganiem wstępnym wdrażania Windows 10 Business, który jest zestawem usług w chmurze i funkcji zarządzania urządzeniami, które uzupełniają Windows 10 Pro i Windows 11 Pro oraz umożliwiają scentralizowane zarządzanie i mechanizmy kontroli zabezpieczeń Microsoft 365 Business Premium.

[Dowiedz się więcej o wymaganiach dotyczących Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro"></a>Windows 10 Pro

Jeśli masz urządzenia z systemem Windows z poprzednimi wersjami systemu Windows, takimi jak Windows 7 Pro, Windows 8 Pro lub Windows 8.1 Pro, Subskrypcja Microsoft 365 Business Premium uprawnia Do uaktualnienia tych urządzeń do Windows 10 Pro lub Windows 11 Pro.
  
Aby uzyskać więcej informacji na temat uaktualniania urządzeń z systemem Windows, zobacz [Uaktualnianie urządzeń z systemem Windows do Windows 10 Pro](m365bp-upgrade-windows-10-pro.md).

## <a name="secure-your-windows-10-and-11-devices"></a>Zabezpieczanie urządzeń Windows 10 i 11

Domyślnie wszystkie ustawienia są **Włączone**. Dostępne są następujące ustawienia:<br/><br/>

|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Ochrona komputerów przed wirusami i innymi zagrożeniami przy użyciu programu antywirusowego Microsoft Defender  <br/> |Wymaga włączenia programu antywirusowego Microsoft Defender w celu ochrony komputerów przed zagrożeniami związanymi z połączeniem z Internetem.  <br/> |
|Chroń komputery przed zagrożeniami internetowymi w programie Microsoft Edge  <br/> |Włącza w programie Microsoft Edge ustawienia ułatwiające ochronę użytkowników przed złośliwymi witrynami i złośliwą zawartością do pobrania.  <br/> |
|Pomóż chronić pliki i foldery na komputerach przed nieautoryzowanym dostępem za pomocą funkcji BitLocker  <br/> |BitLocker chroni dane przez szyfrowanie dysków twardych komputera i ochronę przed ujawnieniem danych w przypadku utraty lub kradzieży komputera. Aby uzyskać więcej informacji, zobacz [BitLocker często zadawane pytania](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Wyłącz ekran urządzenia po takim czasie bezczynności  <br/> |Zapewnia bezpieczeństwo danych firmowych podczas bezczynności użytkownika. Jeśli użytkownik pracuje w miejscu publicznym, na przykład kawiarni, i odejdzie na chwilę od urządzenia lub skupi uwagę na czymś innym, przypadkowe osoby mogą obejrzeć zawartość ekranu. To ustawienie pozwala kontrolować czas bezczynności użytkownika, po którym ekran zostanie wyłączony.  <br/> |

## <a name="next-objective"></a>Następny cel

[Zarządzanie urządzeniami z systemem Windows](m365bp-manage-windows-devices.md)
